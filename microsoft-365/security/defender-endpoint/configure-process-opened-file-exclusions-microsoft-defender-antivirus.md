---
title: تكوين الاستثناءات للملفات التي يتم فتحها بواسطة عمليات معينة
description: يمكنك استبعاد الملفات من عمليات الفحص إذا تم فتحها بواسطة عملية معينة.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، معالجة، استثناء، ملفات، عمليات فحص
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
ms.openlocfilehash: 034ad1312497652554c9a59d51ba18f6bddc9d83
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63571613"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>تكوين الاستثناءات للملفات التي يتم فتحها بواسطة العمليات


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك استثناء الملفات التي تم فتحها بواسطة عمليات معينة من برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. راجع [التوصيات تعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) قبل تعريف قوائم الاستثناء.

تصف هذه المقالة كيفية تكوين قوائم الاستثناء.

## <a name="examples-of-exclusions"></a>أمثلة على الاستثناءات

<br/><br/>

|الاستثناء|مثال|
|---|---|
|أي ملف على الجهاز يتم فتحه بواسطة أي عملية باستخدام اسم ملف معين|قد يستثني `test.exe` التحديد الملفات التي يتم فتحها بواسطة: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|أي ملف على الجهاز يتم فتحه بواسطة أي عملية ضمن مجلد معين|قد يستثني `c:\test\sample\*` التحديد الملفات التي يتم فتحها بواسطة: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|أي ملف على الجهاز يتم فتحه بواسطة عملية معينة في مجلد معين|قد يستثني `c:\test\process.exe` تحديد الملفات التي يتم فتحها فقط بواسطة `c:\test\process.exe`|

عند إضافة عملية إلى قائمة استثناءات العملية، لن برنامج الحماية من الفيروسات من Microsoft Defender الملفات المفتوحة بواسطة هذه العملية، بغض النظر عن موقع الملفات. ومع ذلك، سيتم فحص العملية نفسها ما لم يتم إضافتها أيضا إلى [قائمة استثناءات الملفات](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

تنطبق الاستثناءات فقط على الحماية والمراقبة في [الوقت الحقيقي دائما](configure-real-time-protection-microsoft-defender-antivirus.md). ولا تنطبق على عمليات الفحص المجدولة أو عند الطلب.

سيتم عرض التغييرات التي تم إدخالها باستخدام "نهج **المجموعة" على** قوائم الاستثناء في القوائم أمن Windows [التطبيق](microsoft-defender-security-center-antivirus.md). ومع ذلك، لن تظهر التغييرات أمن Windows التطبيق **في** قوائم نهج المجموعة.

يمكنك إضافة القوائم وإزالتها ومراجعتها للاستبعادات في "نهج المجموعة" و"Microsoft Endpoint Configuration Manager" و"Microsoft Intune" ومع تطبيق أمن Windows، كما يمكنك استخدام أحرف البدل لتخصيص القوائم بشكل أكبر.

يمكنك أيضا استخدام PowerShell cmdlets و WMI لتكوين قوائم الاستثناء، بما في ذلك مراجعة القوائم.

بشكل افتراضي، سيتم دمج التغييرات المحلية التي يتم إدخالها على القوائم (بواسطة المستخدمين الذين لديهم امتيازات المسؤول؛ والتغييرات التي تم إدخالها على PowerShell و WMI) مع القوائم كما تم تعريفها (ونشرها) بواسطة نهج المجموعة أو إدارة التكوين أو Intune. ستتخذ قوائم نهج المجموعة الأسبقية في حالة التعارضات.

يمكنك تكوين [كيفية](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) دمج قوائم الاستثناءات المعرفة محليا و عموميا للسماح بإجراء تغييرات محلية لتجاوز إعدادات النشر المدار.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>تكوين قائمة الاستثناءات للملفات التي يتم فتحها بواسطة عمليات محددة

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام Microsoft Intune لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

راجع [تكوين إعدادات تقييد](/intune/device-restrictions-configure) الجهاز في Microsoft Intune برنامج الحماية من الفيروسات من Microsoft Defender إعدادات تقييد الجهاز Windows 10 [Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) للحصول على مزيد من التفاصيل.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام إدارة نقاط النهاية من Microsoft لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

راجع [كيفية إنشاء سياسات](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) مكافحة البرامج الضارة ونشرها: إعدادات الاستثناء للحصول على تفاصيل حول إدارة نقاط النهاية من Microsoft (الفرع الحالي).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام "نهج المجموعة" لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر** وانقر فوق **قوالب إدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender \> \> الاستثناءات**.

4. انقر نقرا مزدوجا **فوق استثناءات العملية** وأضف الاستثناءات:
    1. تعيين الخيار إلى **تمكين**.
    2. ضمن المقطع **خيارات** ، انقر فوق **إظهار...**.
    3. أدخل كل عملية على السطر الخاص بها ضمن **العمود اسم** القيمة. راجع الجدول المثال لأنواع استثناءات العمليات المختلفة. أدخل **0** في عمود **القيمة** لجميع العمليات.

5. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام PowerShell cmdlets لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

يتطلب استخدام PowerShell لإضافة استثناءات للملفات التي تم فتحها بواسطة العمليات أو إزالتها استخدام مجموعة من ثلاثة cmdlets مع `-ExclusionProcess` المعلمة. يتم كل cmdlets في الوحدة [النمطية Defender](/powershell/module/defender/).

تنسيق cmdlets هو:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

يسمح بما يلي ك :\<cmdlet\>

<br/><br/>

|إجراء التكوين|PowerShell cmdlet|
|---|---|
|إنشاء القائمة أو الكتابة فوقها|`Set-MpPreference`|
|إضافة إلى القائمة|`Add-MpPreference`|
|إزالة العناصر من القائمة|`Remove-MpPreference`|

> [!IMPORTANT]
> إذا قمت بإنشاء قائمة، `Set-MpPreference` `Add-MpPreference`إما باستخدام أو ، `Set-MpPreference` فإن استخدام الأمر cmdlet مرة أخرى سيكتم الكتابة فوق القائمة الموجودة.

على سبيل المثال، قد تتسبب قصاصة التعليمات البرمجية التالية في استبعاد أي ملف يتم فتحه بواسطة العملية المحددة ل Microsoft Defender AV:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع إدارة برنامج الحماية من الفيروسات باستخدام powerShell [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender cmdlets](/powershell/module/defender).

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام Windows إدارة الملفات (WMI) لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

استخدم [**أساليب تعيين** الفئة](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) MSFT_MpPreference وإضافتها وإزالتها للخصائص التالية:

```WMI
ExclusionProcess
```

إن استخدام **"تعيين**" و"**إضافة**" و"إزالة" مماثل لنظيراتها في PowerShell: `Set-MpPreference`و `Add-MpPreference`و.`Remove-MpPreference`

لمزيد من المعلومات والمعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>استخدام تطبيق أمن Windows لاستبعاد الملفات التي تم فتحها بواسطة عمليات محددة من عمليات الفحص

راجع [إضافة استثناءات في تطبيق أمن Windows للحصول](microsoft-defender-security-center-antivirus.md) على الإرشادات.

## <a name="use-wildcards-in-the-process-exclusion-list"></a>استخدام أحرف البدل في قائمة استثناءات العملية

يختلف استخدام أحرف البدل في قائمة استثناءات العملية عن استخدامها في قوائم الاستثناء الأخرى.

بشكل خاص، لا يمكنك استخدام علامة الاستفهام (`?`) أحرف البدل، ولا يمكن استخدام أحرف البدل العلامة النجمية (`*`) إلا في نهاية المسار الكامل. لا يزال بإمكانك استخدام متغيرات البيئة ( `%ALLUSERSPROFILE%`مثل ) مثل أحرف البدل عند تعريف العناصر في قائمة استثناءات العملية.

يصف الجدول التالي كيفية استخدام أحرف البدل في قائمة استثناءات العمليات:

<br/><br/>

|أحرف البدل|مثال على استخدام|تطابقات الأمثلة|
|---|---|---|
|`*` (asterisk) <p> استبدال أي عدد من الأحرف|`C:\MyData\*`|أي ملف يتم فتحه بواسطة `C:\MyData\file.exe`|
|متغيرات البيئة <p> يتم ملء المتغير المعرف كمسار عند تقييم الاستثناء|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|أي ملف يتم فتحه بواسطة `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>مراجعة قائمة الاستثناءات

يمكنك استرداد العناصر الموجودة في قائمة الاستثناء باستخدام MpCmdRun أو PowerShell أو Microsoft Endpoint Configuration Manager [أو Intune](/intune/device-restrictions-configure) أو [تطبيق أمن Windows.](microsoft-defender-security-center-antivirus.md)[](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings)

إذا كنت تستخدم PowerShell، يمكنك استرداد القائمة باستخدام طريقتين:

- استرداد حالة كل برنامج الحماية من الفيروسات من Microsoft Defender المفضلة. سيتم عرض كل قائمة على أسطر منفصلة، ولكن سيتم دمج العناصر ضمن كل قائمة في السطر نفسه.
- اكتب حالة كل التفضيلات إلى متغير، ثم استخدم هذا المتغير لاستدعاء القائمة المحددة التي تريدها فقط. يتم كتابة كل `Add-MpPreference` استخدام ل إلى سطر جديد.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>التحقق من صحة قائمة الاستثناء باستخدام MpCmdRun

للتحقق من الاستثناءات باستخدام أداة [سطر ](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options)الأوامر المخصصة mpcmdrun.exe، استخدم الأمر التالي:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> يتطلب التحقق من الاستثناءات باستخدام MpCmdRun برنامج الحماية من الفيروسات من Microsoft Defender من إصدار 'المكاتب' 4.18.1812.3 (الذي تم إصداره في ديسمبر 2018) أو الإصدارات الأحدث.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>راجع قائمة الاستثناءات إلى جانب جميع تفضيلات برنامج الحماية من الفيروسات من Microsoft Defender الأخرى باستخدام PowerShell

استخدم cmdlet التالي:

```PowerShell
Get-MpPreference
```

راجع [استخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets وتشغيلها برنامج الحماية من الفيروسات من Microsoft Defender PowerShell](/powershell/module/defender) للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>استرداد قائمة استثناءات معينة باستخدام PowerShell

استخدم قصاصة التعليمات البرمجية التالية (أدخل كل سطر ك أمر منفصل)؛ **استبدل WDAVprefs** بأي تسمية تريد تسمية المتغير بها:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

راجع [استخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets وتشغيلها برنامج الحماية من الفيروسات من Microsoft Defender PowerShell](/powershell/module/defender) للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="related-articles"></a>المقالات ذات الصلة

- [تكوين الاستثناءات والتحقق من صحتها في برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين برنامج الحماية من الفيروسات من Microsoft Defender استثناءات على Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [تخصيص نتائج عمليات المسح برنامج الحماية من الفيروسات من Microsoft Defender والوساطة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
