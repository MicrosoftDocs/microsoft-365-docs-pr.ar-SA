---
title: نشر المعلومات وإدارتها برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك نشر وإدارة برنامج الحماية من الفيروسات من Microsoft Defender Intune أو Microsoft Endpoint Configuration Manager أو نهج المجموعة أو PowerShell أو WMI
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
ms.openlocfilehash: 1ce212bf01b8c464760192a4bbd6355498d19c3c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63579556"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>نشر المعلومات وإدارتها برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك نشر المعلومات وإدارتها برنامج الحماية من الفيروسات من Microsoft Defender من خلال عدد من الطرق.

نظرا لأن برنامج الحماية من الفيروسات من Microsoft Defender العميل مثبت كجزء أساسي من Windows 10 Windows 11، لا يتم تطبيق النشر التقليدي للعميل على نقاط النهاية.

ومع ذلك، في معظم الحالات، ما زلت بحاجة إلى تمكين خدمة الحماية على نقاط النهاية باستخدام Microsoft Intune أو Microsoft Endpoint Configuration Manager أو Microsoft Defender for Cloud أو كائنات نهج المجموعة، الموضحة في الجدول التالي.

سترى أيضا ارتباطات إضافية ل:

- إدارة برنامج الحماية من الفيروسات من Microsoft Defender، بما في ذلك إدارة تحديثات المنتجات والحماية
- إعداد التقارير برنامج الحماية من الفيروسات من Microsoft Defender الحماية

> [!IMPORTANT]
> في معظم الحالات، Windows 10 أو Windows 11 تعطيل برنامج الحماية من الفيروسات من Microsoft Defender إذا تم العثور على منتج آخر من برنامج الحماية من الفيروسات قيد التشغيل ومجدد. يجب تعطيل منتجات الحماية من الفيروسات الخاصة ب جهة خارجية أو إلغاء تثبيتها قبل برنامج الحماية من الفيروسات من Microsoft Defender تعمل. إذا قمت ب إعادة تمكين منتجات الحماية من الفيروسات أو تثبيتها من جهة خارجية، Windows 10 أو Windows 11 تلقائيا برنامج الحماية من الفيروسات من Microsoft Defender.

أداة|خيارات النشر (<a href="#fn2" id="ref2">2</a>)|خيارات الإدارة (التكوين على مستوى الشبكة ونشر النهج أو الأساس) ([3](#fn3))|خيارات إعداد التقارير
---|---|---|---
Microsoft Intune|[إضافة إعدادات حماية نقطة النهاية في Intune](/intune/endpoint-protection-configure)|[تكوين إعدادات تقييد الجهاز في Intune](/intune/device-restrictions-configure)| [استخدام وحدة تحكم Intune لإدارة الأجهزة](/intune/device-management)
إدارة نقاط النهاية من Microsoft ([1](#fn1))|استخدم [Endpoint Protection دور نظام موقع النقاط][] و[تمكين Endpoint Protection إعدادات العميل المخصصة][]|مع [سياسات مكافحة البرامج الضارة الافتراضية والمخصصة][] و[إدارة العميل][]|باستخدام مساحة العمل الافتراضية [مراقبة إدارة التكوين][] و[تنبيهات البريد الإلكتروني][]
نهج المجموعة و Active Directory (المجال المنضم)|استخدم "كائن نهج المجموعة" لنشر تغييرات التكوين وضمان برنامج الحماية من الفيروسات من Microsoft Defender تمكينها.|استخدم كائنات نهج المجموعة (GPOs) ل [تكوين خيارات التحديث برنامج الحماية من الفيروسات من Microsoft Defender][] و[تكوين Windows Defender][]|لا تتوفر تقارير نقطة النهاية مع "نهج المجموعة". يمكنك إنشاء قائمة ب [سياسات المجموعة لتحديد ما إذا لم يتم تطبيق أي إعدادات أو سياسات][]
PowerShell|النشر باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو يدويا على نقاط النهاية الفردية.|استخدم الأمرين cmdlets [Set-MpPreference] و[Update-MpSignature] المتوفرين في الوحدة النمطية Defender.|استخدم [Get-cmdlets المناسبة المتوفرة في الوحدة النمطية Defender][]
Windows أدوات الإدارة|النشر باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو يدويا على نقاط النهاية الفردية.|استخدم [أسلوب المجموعة للفئة MSFT_MpPreference][] و[أسلوب التحديث للفئة MSFT_MpSignature][]|استخدم الفئة [MSFT_MpComputerStatus][] وطريقة الحصول على الفئات المقترنة في [Windows Defender WMIv2 Provider][]
Microsoft Azure|نشر Microsoft Antimalware ل Azure في مدخل Azure، باستخدام Visual Studio جهاز ظاهري، أو [باستخدام Azure PowerShell cmdlets](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). يمكنك أيضا [تثبيت حماية نقطة النهاية في Microsoft Defender for Cloud*](/azure/security-center/security-center-install-endpoint-protection)|تكوين [Microsoft Antimalware للآلات الظاهرية والخدمات السحابية باستخدام Azure PowerShell cmdlets](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) [أو استخدام نماذج التعليمات البرمجية](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|استخدم [Microsoft Antimalware للآلات الظاهرية والخدمات السحابية مع Azure PowerShell cmdlets](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) لتمكين المراقبة. يمكنك أيضا مراجعة تقارير الاستخدام في Azure Active Directory لتحديد نشاط مريب، بما في ذلك تقرير [الأجهزة التي ربما أصيبت][] وتكوين أداة SIEM للتقرير عن [أحداث برنامج الحماية من الفيروسات من Microsoft Defender][] وإضافة هذه الأداة ك تطبيق في AAD (دليل Azure النشط).

1. <span id="fn1" />يختلف توفر بعض الدالات والميزات، لا سيما المتعلقة بالحماية التي توفرها السحابة، بين إدارة نقاط النهاية من Microsoft (الفرع الحالي) System Center 2012 إدارة التكوين. في هذه المكتبة، ركزنا على Windows 10 و Windows 11 و Windows Server 2016 و إدارة نقاط النهاية من Microsoft (الفرع الحالي). راجع [استخدام الحماية التي توفرها السحابة من Microsoft برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) جدول يصف الاختلافات الرئيسية. [(العودة إلى الجدول)](#ref2)

2. <span id="fn2" />في Windows 10 Windows 11، برنامج الحماية من الفيروسات من Microsoft Defender مكون متوفر بدون تثبيت أو نشر عميل أو خدمة إضافية. سيتم تمكينها تلقائيا عندما يتم إلغاء تثبيت منتجات الحماية من الفيروسات الخاصة بأي جهة خارجية أو تكون غير م تاريخها (باستثناء Windows Server 2016). وبالتالي، فإن النشر التقليدي غير مطلوب. يشير النشر هنا إلى التأكد من برنامج الحماية من الفيروسات من Microsoft Defender المكون المتوفر والممكن على نقاط النهاية أو الخوادم. [(العودة إلى الجدول)](#ref2)

3. <span id="fn3" />يتم أيضا وصف تكوين الميزات والحماية، بما في ذلك تكوين تحديثات المنتجات والحماية، في المقطع تكوين برنامج الحماية من الفيروسات من Microsoft Defender [في](configure-notifications-microsoft-defender-antivirus.md) هذه المكتبة. [(العودة إلى الجدول)](#ref2)

## <a name="in-this-section"></a>في هذا القسم

الموضوع | الوصف
---|---
[نشر الحماية برنامج الحماية من الفيروسات من Microsoft Defender وتمكينها](deploy-microsoft-defender-antivirus.md) | بينما يكون العميل مثبتا كجزء أساسي من Windows 10 أو Windows 11، ولا ينطبق النشر التقليدي، لا يزال عليك تمكين العميل على نقاط النهاية باستخدام Microsoft Endpoint Configuration Manager أو Microsoft Intune أو كائنات نهج المجموعة.
[إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيقها](manage-updates-baselines-microsoft-defender-antivirus.md) | هناك جزءان لتحديث برنامج الحماية من الفيروسات من Microsoft Defender: تحديث العميل على نقاط النهاية (تحديثات المنتجات)، وتحديث معلومات الأمان (تحديثات الحماية). يمكنك تحديث معلومات الأمان بعدد من الطرق، Microsoft Endpoint Configuration Manager نهج المجموعة و PowerShell و WMI.
[مراقبة البيانات برنامج الحماية من الفيروسات من Microsoft Defender الحماية](report-monitor-microsoft-defender-antivirus.md) | يمكنك استخدام Microsoft Intune أو Microsoft Endpoint Configuration Manager أو تحديث التوافق ل Microsoft Operations Management Suite أو منتج SIEM من جهة خارجية (من خلال استهلاك سجلات أحداث Windows) لمراقبة حالة الحماية وإنشاء تقارير حول حماية نقطة النهاية.
