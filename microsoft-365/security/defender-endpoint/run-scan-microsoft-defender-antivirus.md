---
title: تشغيل عمليات الفحص حسب الطلب وتخصيصها في برنامج الحماية من الفيروسات من Microsoft Defender
description: تشغيل عمليات المسح الضوئي عند الطلب وتكوينها باستخدام PowerShell أو Windows Management Instrumentation أو بشكل فردي على نقاط النهاية باستخدام تطبيق أمن Windows
keywords: المسح الضوئي، عند الطلب، dos، intune، الفحص الفوري
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/22/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: bca0e953b759f447e8274e8766cbcada273eb614
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788865"
---
# <a name="configure-and-run-on-demand-microsoft-defender-antivirus-scans"></a>تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

يمكنك تشغيل فحص عند الطلب على نقاط النهاية الفردية. ستبدأ عمليات الفحص هذه على الفور، ويمكنك تحديد معلمات الفحص، مثل الموقع أو النوع. عند تشغيل الفحص، يمكنك الاختيار من بين ثلاثة أنواع: الفحص السريع، والفحص الكامل، والمسح الضوئي المخصص. في معظم الحالات، استخدم فحصا سريعا. يبحث الفحص السريع في جميع المواقع التي يمكن أن تكون هناك برامج ضارة مسجلة للبدء بالنظام، مثل مفاتيح التسجيل ومجلدات بدء التشغيل المعروفة Windows.

جنبا إلى جنب مع الحماية الدائمة في الوقت الحقيقي، والتي تراجع الملفات عند فتحها وإغلاقها، وكلما انتقل المستخدم إلى مجلد، يساعد الفحص السريع على توفير حماية قوية من البرامج الضارة التي تبدأ بالنظام والبرامج الضارة على مستوى النواة. في معظم الحالات، يكون الفحص السريع كافيا وهو الخيار الموصى به لإجراء عمليات الفحص المجدولة أو عند الطلب. [تعرف على المزيد حول أنواع الفحص](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan).

> [!IMPORTANT]
> يتم تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في سياق حساب [LocalSystem](/windows/win32/services/localsystem-account) عند إجراء فحص محلي. بالنسبة لمسح الشبكة، فإنه يستخدم سياق حساب الجهاز. إذا لم يكن لحساب جهاز المجال الأذونات المناسبة للوصول إلى المشاركة، فلن يعمل الفحص. تأكد من أن الجهاز لديه أذونات لمشاركة شبكة الوصول.

## <a name="use-microsoft-endpoint-manager-to-run-a-scan"></a>استخدام إدارة نقاط النهاية من Microsoft لتشغيل فحص

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. اختر برنامج **الحماية من الفيروسات** **لأمان** \> نقطة النهاية.

3. في قائمة علامات التبويب، حدد **Windows 10 نقاط النهاية غير السليمة** أو **Windows 11 نقاط النهاية غير السليمة**.

4. من قائمة الإجراءات المتوفرة، حدد **"فحص سريع** " (مستحسن) أو **"فحص كامل**".

   [![خيارات الفحص على علامة تبويب نقاط النهاية Windows 10 غير السليمة.](images/mem-antivirus-scan-on-demand.png)](images/mem-antivirus-scan-on-demand.png#lightbox)

> [!TIP]
> لمزيد من المعلومات حول استخدام إدارة نقاط النهاية من Microsoft لتشغيل الفحص، راجع [مهام مكافحة البرامج الضارة وجدار الحماية: كيفية إجراء فحص عند الطلب](/configmgr/protect/deploy-use/endpoint-antimalware-firewall#how-to-perform-an-on-demand-scan-of-computers).

## <a name="use-the-mpcmdrunexe-command-line-utility-to-run-a-scan"></a>استخدام الأداة المساعدة mpcmdrun.exe سطر الأوامر لتشغيل فحص

استخدم المعلمة التالية `-scan` :

```console
mpcmdrun.exe -scan -scantype 1
```

لمزيد من المعلومات حول كيفية استخدام الأداة والمعلمات الإضافية، بما في ذلك بدء الفحص الكامل أو تحديد المسارات، راجع [استخدام أداة سطر الأوامر mpcmdrun.exe لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender](command-line-arguments-microsoft-defender-antivirus.md).

## <a name="use-microsoft-intune-to-run-a-scan"></a>استخدام Microsoft Intune لتشغيل فحص

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) وسجل الدخول.

2. من الشريط الجانبي، حدد **الأجهزة** \> **كافة الأجهزة** واختر الجهاز الذي تريد فحصه.

3. حدد **... المزيد.** من الخيارات، حدد **"فحص سريع** " (مستحسن) أو **"فحص كامل**".

## <a name="use-the-windows-security-app-to-run-a-scan"></a>استخدام تطبيق أمن Windows لتشغيل فحص

راجع [تشغيل فحص في تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md) للحصول على إرشادات حول تشغيل فحص على نقاط النهاية الفردية.

## <a name="use-powershell-cmdlets-to-run-a-scan"></a>استخدام PowerShell cmdlets لتشغيل الفحص

استخدم cmdlet التالي:

```PowerShell
Start-MpScan
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع [استخدام PowerShell cmdlets لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus](/powershell/module/defender/).

## <a name="use-windows-management-instruction-wmi-to-run-a-scan"></a>استخدام تعليمات إدارة Windows (WMI) لتشغيل فحص

استخدم [أسلوب **البدء**](/previous-versions/windows/desktop/defender/start-msft-mpscan) للفئة **MSFT_MpScan**.

لمزيد من المعلومات حول المعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)