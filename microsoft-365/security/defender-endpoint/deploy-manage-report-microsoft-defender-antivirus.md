---
title: نشر وإدارة والإبلاغ عن برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك نشر وإدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام Intune أو Microsoft Endpoint Configuration Manager أو نهج المجموعة أو PowerShell أو WMI
keywords: النشر والإدارة والتحديث والحماية برنامج الحماية من الفيروسات من Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 049c7a772c4c8dcf986efd310e4613423f33dcc9
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419121"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>نشر وإدارة والإبلاغ عن برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender 

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يمكنك نشر برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها وإعداد تقرير بشأنها بعدة طرق.

نظرا إلى تثبيت عميل برنامج الحماية من الفيروسات من Microsoft Defender كجزء أساسي من Windows 10 Windows 11، لا ينطبق النشر التقليدي للعميل على نقاط النهاية الخاصة بك.

ومع ذلك، في معظم الحالات، ستظل بحاجة إلى تمكين خدمة الحماية على نقاط النهاية الخاصة بك باستخدام Microsoft Intune أو Microsoft Endpoint Configuration Manager أو Microsoft Defender for Cloud أو كائنات نهج المجموعة، والتي يتم وصفها في الجدول التالي.

سترى أيضا ارتباطات إضافية ل:

- إدارة حماية برنامج الحماية من الفيروسات من Microsoft Defender، بما في ذلك إدارة تحديثات المنتجات والحماية
- الإبلاغ عن حماية برنامج الحماية من الفيروسات من Microsoft Defender

> [!IMPORTANT]
> في معظم الحالات، سيعطل Windows 10 أو Windows 11 برنامج الحماية من الفيروسات من Microsoft Defender إذا عثر على منتج آخر من منتجات مكافحة الفيروسات قيد التشغيل ومحدث. يجب تعطيل منتجات مكافحة الفيروسات لجهة خارجية أو إلغاء تثبيتها قبل أن تعمل برنامج الحماية من الفيروسات من Microsoft Defender. إذا قمت بإعادة تمكين منتجات الحماية من الفيروسات لجهة خارجية أو تثبيتها، Windows 10 أو Windows 11 تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا.

أداة|خيارات النشر (<a href="#fn2" id="ref2">2</a>)|خيارات الإدارة (التكوين على مستوى الشبكة والنهج أو توزيع الأساس) ([3](#fn3))|خيارات إعداد التقارير
---|---|---|---
Microsoft Intune|[إضافة إعدادات حماية نقطة النهاية في Intune](/intune/endpoint-protection-configure)|[تكوين إعدادات تقييد الجهاز في Intune](/intune/device-restrictions-configure)| [استخدام وحدة تحكم Intune لإدارة الأجهزة](/intune/device-management)
إدارة نقاط النهاية من Microsoft ([1](#fn1))|استخدم [دور نظام نقطة Endpoint Protection][] و[تمكين Endpoint Protection مع إعدادات العميل المخصصة][]|مع [نهج مكافحة البرامج الضارة الافتراضية والمخصصة][] و[إدارة العميل][]|مع مساحة عمل المراقبة الافتراضية [Configuration Manager][] و[تنبيهات البريد الإلكتروني][]
نهج المجموعة وActive Directory (مرتبط بالمجال)|استخدم عنصر نهج المجموعة لنشر تغييرات التكوين والتأكد من تمكين برنامج الحماية من الفيروسات من Microsoft Defender.|استخدم كائنات نهج المجموعة (GPOs) ل [تكوين خيارات التحديث برنامج الحماية من الفيروسات من Microsoft Defender][] و[تكوين ميزات Windows Defender][]|تقارير نقطة النهاية غير متوفرة مع نهج المجموعة. يمكنك إنشاء قائمة ب [نهج المجموعة لتحديد ما إذا لم يتم تطبيق أي إعدادات أو نهج][]
PowerShell|النشر باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو يدويا على نقاط النهاية الفردية.|استخدم أوامر cmdlets [Set-MpPreference] و[Update-MpSignature] المتوفرة في الوحدة النمطية Defender.|استخدم [Get- cmdlets المناسبة المتوفرة في الوحدة النمطية Defender][]
Windows Management Instrumentation|النشر باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو يدويا على نقاط النهاية الفردية.|استخدم الأسلوب [Set method of the MSFT_MpPreference class][] و[Update method of the MSFT_MpSignature class][]|استخدم الفئة [MSFT_MpComputerStatus][] وطريقة الحصول على الفئات المقترنة في [Windows Defender WMIv2 Provider][]
Microsoft Azure|نشر Microsoft Antimalware ل Azure في [مدخل Azure، باستخدام تكوين الجهاز الظاهري Visual Studio، أو باستخدام أوامر Cmdlets Azure PowerShell](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). يمكنك أيضا [تثبيت حماية نقطة النهاية في Microsoft Defender for Cloud*](/azure/security-center/security-center-install-endpoint-protection)|تكوين [Microsoft Antimalware للأجهزة الظاهرية والخدمات السحابية مع أوامر Cmdlets Azure PowerShell](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) أو [استخدام نماذج التعليمات البرمجية](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|استخدم [Microsoft Antimalware للأجهزة الظاهرية والخدمات السحابية مع أوامر Cmdlets Azure PowerShell](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) لتمكين المراقبة. يمكنك أيضا مراجعة تقارير الاستخدام في Azure Active Directory لتحديد النشاط المشبوه، بما في ذلك تقرير [ربما الأجهزة المصابة][] وتكوين أداة SIEM للإبلاغ عن [أحداث برنامج الحماية من الفيروسات من Microsoft Defender][] وإضافة هذه الأداة كتطبيق في AAD.

1. <span id="fn1" />يختلف توفر بعض الوظائف والميزات، خاصة المتعلقة بالحماية المقدمة من السحابة، بين إدارة نقاط النهاية من Microsoft (الفرع الحالي) ومركز النظام 2012 Configuration Manager. في هذه المكتبة، ركزنا على Windows 10 Windows 11 Windows Server 2016 و إدارة نقاط النهاية من Microsoft (الفرع الحالي). راجع [استخدام الحماية التي توفرها السحابة من Microsoft في برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) لجدول يصف الاختلافات الرئيسية. [(العودة إلى الجدول)](#ref2)

2. <span id="fn2" />في Windows 10 Windows 11، برنامج الحماية من الفيروسات من Microsoft Defender هو مكون متوفر دون تثبيت أو نشر عميل أو خدمة إضافية. سيتم تمكينه تلقائيا عندما تكون منتجات مكافحة الفيروسات التابعة لجهة خارجية إما غير مثبتة أو قديمة (باستثناء Windows Server 2016). وبالتالي، فإن النشر التقليدي غير مطلوب. يشير النشر هنا إلى ضمان توفر مكون برنامج الحماية من الفيروسات من Microsoft Defender وتمكينه على نقاط النهاية أو الخوادم. [(العودة إلى الجدول)](#ref2)

3. <span id="fn3" />يتم وصف تكوين الميزات والحماية، بما في ذلك تكوين تحديثات المنتج والحماية، في قسم [تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender](configure-notifications-microsoft-defender-antivirus.md) في هذه المكتبة. [(العودة إلى الجدول)](#ref2)

## <a name="in-this-section"></a>في هذا القسم

الموضوع | الوصف
---|---
[نشر الحماية برنامج الحماية من الفيروسات من Microsoft Defender وتمكينها](deploy-microsoft-defender-antivirus.md) | بينما يتم تثبيت العميل كجزء أساسي من Windows 10 أو Windows 11، ولا ينطبق النشر التقليدي، ستظل بحاجة إلى تمكين العميل على نقاط النهاية باستخدام Microsoft Endpoint Configuration Manager أو Microsoft Intune أو نهج المجموعة الكائنات.
[إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md) | هناك جزأان لتحديث برنامج الحماية من الفيروسات من Microsoft Defender: تحديث العميل على نقاط النهاية (تحديثات المنتج)، وتحديث معلومات الأمان (تحديثات الحماية). يمكنك تحديث معلومات الأمان بعدة طرق، باستخدام Microsoft Endpoint Configuration Manager نهج المجموعة وPowerShell وWMI.
[مراقبة الحماية برنامج الحماية من الفيروسات من Microsoft Defender وإعداد تقرير بشأنها](report-monitor-microsoft-defender-antivirus.md) | يمكنك استخدام Microsoft Intune أو Microsoft Endpoint Configuration Manager أو الوظيفة الإضافية Update Compliance لمجموعة إدارة عمليات Microsoft أو منتج SIEM تابع لجهة خارجية (عن طريق استهلاك سجلات أحداث Windows) لمراقبة حالة الحماية وإنشاء تقارير حول حماية نقطة النهاية.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
    
