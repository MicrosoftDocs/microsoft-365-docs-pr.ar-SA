---
title: تكوين استثناءات للملفات التي تم فتحها بواسطة عمليات معينة
description: يمكنك استبعاد الملفات من عمليات الفحص إذا تم فتحها بواسطة عملية معينة.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender والمعالجة والاستبعاد والملفات وعمليات الفحص
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 0dd59d2196ebb2c2af80fb53d43a009ff3a367d0
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102310"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>تكوين استثناءات للملفات التي يتم فتحها بواسطة العمليات


**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل 

يمكنك استبعاد الملفات التي تم فتحها بواسطة عمليات معينة من عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender. راجع [التوصيات لتعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) قبل تعريف قوائم الاستبعاد الخاصة بك.

تصف هذه المقالة كيفية تكوين قوائم الاستبعاد.

## <a name="examples-of-exclusions"></a>أمثلة على الاستثناءات

|الاستبعاد|المثال|
|---|---|
|أي ملف على الجهاز يتم فتحه بواسطة أي عملية باسم ملف معين|قد يؤدي تحديد `test.exe` الملفات التي تم فتحها إلى استبعاد ما يلي: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|أي ملف على الجهاز يتم فتحه بواسطة أي عملية ضمن مجلد معين|قد يؤدي تحديد `c:\test\sample\*` الملفات التي تم فتحها إلى استبعاد ما يلي: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|أي ملف على الجهاز يتم فتحه بواسطة عملية معينة في مجلد معين|سيؤدي تحديد `c:\test\process.exe` الملفات التي تم فتحها فقط إلى استبعاد الملفات التي تم فتحها `c:\test\process.exe`|

عند إضافة عملية إلى قائمة استبعاد العملية، لن يقوم برنامج الحماية من الفيروسات من Microsoft Defender بفحص الملفات التي تم فتحها بواسطة هذه العملية، بغض النظر عن مكان وجود الملفات. ومع ذلك، سيتم مسح العملية نفسها ضوئيا ما لم تتم إضافتها أيضا إلى [قائمة استبعاد الملفات](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

تنطبق الاستثناءات فقط [على الحماية والمراقبة في الوقت الحقيقي دائما](configure-real-time-protection-microsoft-defender-antivirus.md). لا تنطبق على عمليات الفحص المجدولة أو عند الطلب.

**ستظهر** التغييرات التي تم إجراؤها مع نهج المجموعة على قوائم الاستبعاد في القوائم في [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md). ومع ذلك، **لن تظهر** التغييرات التي تم إجراؤها في تطبيق أمن Windows في قوائم نهج المجموعة.

يمكنك إضافة قوائم الاستثناءات وإزالتها ومراجعتها في نهج المجموعة، Microsoft Endpoint Configuration Manager، Microsoft Intune، ومع تطبيق أمن Windows، ويمكنك استخدام أحرف البدل لتخصيص القوائم بشكل أكبر.

يمكنك أيضا استخدام PowerShell cmdlets وWMI لتكوين قوائم الاستبعاد، بما في ذلك مراجعة القوائم.

بشكل افتراضي، سيتم دمج التغييرات المحلية التي تم إجراؤها على القوائم (من قبل المستخدمين الذين لديهم امتيازات المسؤول؛ والتغييرات التي تم إجراؤها باستخدام PowerShell وWMI) مع القوائم كما تم تعريفها (ونشرها) بواسطة نهج المجموعة أو Configuration Manager أو Intune. ستكون للقوائم نهج المجموعة الأسبقية في حالة التعارضات.

يمكنك [تكوين كيفية دمج قوائم الاستثناءات المعرفة محليا وبشكل عمومي للسماح للتغييرات](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) المحلية بتجاوز إعدادات النشر المدارة.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>تكوين قائمة الاستثناءات للملفات التي تم فتحها بواسطة عمليات محددة

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام Microsoft Intune لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

راجع [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure) [وإعدادات تقييد الجهاز برنامج الحماية من الفيروسات من Microsoft Defender Windows 10 في Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) للحصول على مزيد من التفاصيل.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام إدارة نقاط النهاية من Microsoft لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

راجع [كيفية إنشاء نهج مكافحة البرامج الضارة ونشرها: إعدادات الاستثناء](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) للحصول على تفاصيل حول تكوين إدارة نقاط النهاية من Microsoft (الفرع الحالي).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام نهج المجموعة لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر** وانقر فوق **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات \> Windows برنامج الحماية من الفيروسات من Microsoft Defender \> الاستثناءات**.

4. انقر نقرا مزدوجا فوق **"استثناءات العمليات** " وأضف الاستثناءات:
    1. تعيين الخيار إلى **ممكن**.
    2. ضمن المقطع **"خيارات** "، انقر فوق **"إظهار...**".
    3. أدخل كل عملية على السطر الخاص بها ضمن عمود **اسم القيمة** . راجع الجدول المثال لأنواع مختلفة من استثناءات العمليات. أدخل **0** في عمود **"القيمة** " لكافة العمليات.

5. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام PowerShell cmdlets لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

يتطلب استخدام PowerShell لإضافة استثناءات للملفات التي تم فتحها بواسطة العمليات أو إزالتها استخدام مجموعة من ثلاثة أوامر cmdlets مع المعلمة `-ExclusionProcess` . أوامر cmdlets كلها في [وحدة Defender](/powershell/module/defender/).

تنسيق cmdlets هو:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

يسمح بما يلي ك \<cmdlet\>:

|إجراء التكوين|PowerShell cmdlet|
|---|---|
|إنشاء القائمة أو الكتابة فوقها|`Set-MpPreference`|
|إضافة إلى القائمة|`Add-MpPreference`|
|إزالة العناصر من القائمة|`Remove-MpPreference`|

> [!IMPORTANT]
> إذا قمت بإنشاء قائمة، إما باستخدام `Set-MpPreference` cmdlet أو `Add-MpPreference`باستخدامه `Set-MpPreference` مرة أخرى، فسيؤدي ذلك إلى الكتابة فوق القائمة الموجودة.

على سبيل المثال، قد تتسبب القصاصة البرمجية التالية في قيام عمليات فحص Microsoft Defender AV باستبعاد أي ملف يتم فتحه بواسطة العملية المحددة:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع إدارة الحماية من الفيروسات باستخدام PowerShell cmdlets و [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender](/powershell/module/defender).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام تعليمات إدارة Windows (WMI) لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

استخدم [أساليب **المجموعة** **والإضافة** **والإزالة** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ExclusionProcess
```

يعد استخدام **Set** و **Add** و **Remove** مماثلا لنظرائهم في PowerShell: `Set-MpPreference`و، `Add-MpPreference`و `Remove-MpPreference`.

لمزيد من المعلومات والمعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدم تطبيق أمن Windows لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

راجع [إضافة استثناءات في تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md) للحصول على الإرشادات.

## <a name="use-wildcards-in-the-process-exclusion-list"></a>استخدام أحرف البدل في قائمة استبعاد العملية

يختلف استخدام أحرف البدل في قائمة استبعاد العملية عن استخدامها في قوائم الاستبعاد الأخرى.

على وجه الخصوص، لا يمكنك استخدام حرف البدل (`?`) علامة الاستفهام، ولا يمكن استخدام حرف البدل () النجمي إلا`*` في نهاية مسار كامل. لا يزال بإمكانك استخدام متغيرات البيئة (مثل `%ALLUSERSPROFILE%`) كأحرف البدل عند تعريف العناصر في قائمة استبعاد العملية.

يصف الجدول التالي كيفية استخدام أحرف البدل في قائمة استبعاد العملية:

|بدل|مثال على الاستخدام|مثال على التطابقات|
|---|---|---|
|`*` (علامة نجمية) <p> استبدال أي عدد من الأحرف|`C:\MyData\*`|أي ملف يتم فتحه بواسطة `C:\MyData\file.exe`|
|متغيرات البيئة <p> يتم ملء المتغير المحدد كمسار عند تقييم الاستبعاد|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|أي ملف يتم فتحه بواسطة `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>مراجعة قائمة الاستثناءات

يمكنك استرداد العناصر في قائمة الاستبعاد باستخدام MpCmdRun أو PowerShell [أو Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) أو [Intune](/intune/device-restrictions-configure) أو [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).

إذا كنت تستخدم PowerShell، يمكنك استرداد القائمة بطريقتين:

- استرداد حالة كافة تفضيلات برنامج الحماية من الفيروسات من Microsoft Defender. سيتم عرض كل قائمة من القوائم على أسطر منفصلة، ولكن سيتم دمج العناصر الموجودة داخل كل قائمة في السطر نفسه.
- اكتب حالة كافة التفضيلات إلى متغير، واستخدم هذا المتغير لاستدعاء القائمة المحددة التي تهتم بها فقط. تتم كتابة كل استخدام لسطر `Add-MpPreference` جديد.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>التحقق من صحة قائمة الاستبعاد باستخدام MpCmdRun

للتحقق من الاستثناءات باستخدام [أداة سطر الأوامر المخصصة mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options)، استخدم الأمر التالي:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> يتطلب التحقق من الاستثناءات باستخدام MpCmdRun برنامج الحماية من الفيروسات من Microsoft Defender إصدار 4.18.1812.3 من برنامج المعالجة المؤقتة (الذي تم إصداره في ديسمبر 2018) أو إصدار أحدث.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>مراجعة قائمة الاستثناءات إلى جانب جميع تفضيلات برنامج الحماية من الفيروسات من Microsoft Defender الأخرى باستخدام PowerShell

استخدم cmdlet التالي:

```PowerShell
Get-MpPreference
```

راجع [استخدام أوامر cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) و [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender](/powershell/module/defender) لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>استرداد قائمة استثناءات معينة باستخدام PowerShell

استخدم القصاصة البرمجية التالية (أدخل كل سطر كأوامر منفصلة)؛ استبدل **WDAVprefs** بأي تسمية تريد تسمية المتغير بها:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

راجع [استخدام أوامر cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) و [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender](/powershell/module/defender) لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الاستثناءات والتحقق من صحتها في عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين استثناءات برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows](configure-server-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [تخصيص نتائج عمليات الفحص والمعالجة برنامج الحماية من الفيروسات من Microsoft Defender وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
