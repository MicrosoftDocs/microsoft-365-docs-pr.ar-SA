---
title: تكوين الاستثناءات والتحقق من صحتها استنادا إلى الملحق أو الاسم أو الموقع
description: استبعاد الملفات من عمليات برنامج الحماية من الفيروسات من Microsoft Defender استنادا إلى ملحق الملف أو اسم الملف أو موقعه.
keywords: الاستثناءات والملفات والملحقات ونوع الملف واسم المجلد واسم الملف والفحص
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.date: 02/27/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: be22c80e51551b5de2a2aeed2f0dff0db9a8481f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575462"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>تكوين الاستثناءات والتحقق من صحتها استنادا إلى ملحق الملف وموقع المجلد

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك تحديد الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender التي تنطبق على عمليات الفحص المجدولة، [](schedule-antivirus-scans.md)والفحص عند الطلب، [](run-scan-microsoft-defender-antivirus.md)والحماية والمراقبة في الوقت الحقيقي [دائما](configure-real-time-protection-microsoft-defender-antivirus.md). **بشكل عام، يجب ألا تحتاج إلى تطبيق الاستثناءات**. إذا كنت بحاجة إلى تطبيق الاستثناءات، يمكنك الاختيار من بين عدة أنواع مختلفة:

- الاستثناءات استنادا إلى ملحقات الملفات ومواقع المجلدات (الموضحة في هذه المقالة)
- [استثناءات الملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender لا تنطبق الاستثناءات على إمكانيات نقاط النهاية الأخرى ل Microsoft Defender، بما في ذلك [الكشف عن تهديدات نقاط النهاية والرد عليها ( الكشف التلقائي والاستجابة على النقط النهائية)](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)، وقواعد تقليل مساحة الهجوم [(ASR)،](/microsoft-365/security/defender-endpoint/attack-surface-reduction) [والوصول المتحكم به إلى المجلدات](/microsoft-365/security/defender-endpoint/controlled-folders). لا تزال الملفات التي تستبعدها باستخدام الأساليب الموضحة في هذه المقالة تؤدي إلى تشغيل الكشف التلقائي والاستجابة على النقط النهائية والكشف الأخرى.
> لاستبعاد الملفات على نطاق واسع، أضفها إلى مؤشرات Microsoft Defender لنقطة [النهاية المخصصة](/microsoft-365/security/defender-endpoint/manage-indicators).

## <a name="before-you-begin"></a>قبل البدء...

راجع [التوصيات تعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md) قبل تعريف قوائم الاستثناء.

## <a name="exclusion-lists"></a>قوائم الاستثناء

لاستبعاد ملفات معينة من عمليات برنامج الحماية من الفيروسات من Microsoft Defender، يمكنك تعديل قوائم الاستثناء. برنامج الحماية من الفيروسات من Microsoft Defender العديد من الاستثناءات التلقائية استنادا إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية، مثل تلك المستخدمة في إدارة المؤسسة وإدارة قاعدة البيانات وسيناريوهات ومواد أخرى خاصة بالمؤسسة.

> [!NOTE]
> تنطبق الاستثناءات أيضا على اكتشافات التطبيقات (PUA) التي قد تكون غير مرغوب فيها.
>
> تنطبق الاستثناءات التلقائية فقط على Windows Server 2016 واللاحقة. لا تظهر هذه الاستثناءات في أمن Windows التطبيق وفي PowerShell.

يسرد الجدول التالي بعض أمثلة الاستثناءات استنادا إلى ملحق الملف وموقع المجلد. 
<br/><br/>

|الاستثناء|أمثلة|قائمة الاستثناء|
|---|---|---|
|أي ملف بملحق معين|كل الملفات ذات الملحق المحدد، في أي مكان على الجهاز. <p> بناء الجملة الصالح: `.test` و `test`|استثناءات الملحقات|
|أي ملف ضمن مجلد معين|كل الملفات الموجودة ضمن `c:\test\sample` المجلد|استثناءات الملفات والمجلدات|
|ملف معين في مجلد معين|الملف فقط `c:\sample\sample.test`|استثناءات الملفات والمجلدات|
|عملية معينة|الملف القابل للتنفيذ `c:\test\process.exe`|استثناءات الملفات والمجلدات|

## <a name="characteristics-of-exclusion-lists"></a>خصائص قوائم الاستثناء

- تنطبق استثناءات المجلدات على كل الملفات والمجلدات الموجودة ضمن ذلك المجلد، إلا إذا كان المجلد الفرعي نقطة إعادة. يجب استبعاد المكاتب الفرعية لنقطة Reparse بشكل منفصل.
- تنطبق ملحقات الملفات على أي اسم ملف مع الملحق المعرف إذا لم يتم تعريف مسار أو مجلد.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>ملاحظات مهمة حول الاستثناءات استنادا إلى ملحقات الملفات ومواقع المجلدات

- سيغير استخدام أحرف البدل مثل النجمة (\*) طريقة تفسير قواعد الاستثناء. راجع المقطع [استخدام أحرف البدل](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) في اسم الملف ومسار المجلد أو قائمة استثناءات الملحقات للحصول على معلومات مهمة حول كيفية عمل أحرف البدل.

- لا تستبعد محركات أقراص الشبكة التي تم تعيينها. حدد مسار الشبكة الفعلي.

- لن يتم تضمين المجلدات التي هي نقاط reparse التي تم إنشاؤها بعد برنامج الحماية من الفيروسات من Microsoft Defender الخدمة التي تم إضافتها إلى قائمة الاستثناء. أعد تشغيل الخدمة (عن طريق إعادة Windows التشغيل) لنقاط reparse الجديدة لكي يتم التعرف عليها كهدف استثناء صالح.

- تنطبق الاستثناءات على [عمليات الفحص](scheduled-catch-up-scans-microsoft-defender-antivirus.md) المجدولة، [](run-scan-microsoft-defender-antivirus.md)والفحص عند الطلب، والحماية [](configure-real-time-protection-microsoft-defender-antivirus.md)في الوقت الحقيقي، ولكن ليس عبر Defender for Endpoint. لتحديد الاستثناءات عبر Defender for Endpoint، استخدم [المؤشرات المخصصة](manage-indicators.md).

- بشكل افتراضي، سيتم دمج التغييرات المحلية التي يتم إدخالها على القوائم (بواسطة المستخدمين الذين لديهم امتيازات المسؤول، بما في ذلك التغييرات التي تم إدخالها على PowerShell و WMI) مع القوائم كما تم تعريفها (ونشرها) بواسطة نهج المجموعة أو إدارة التكوين أو Intune. تأخذ قوائم نهج المجموعة الأسبقية عند وجود تعارضات. بالإضافة إلى ذلك، تكون تغييرات قائمة الاستثناء التي تم إدخالها باستخدام "نهج المجموعة" مرئية في [أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md).

- للسماح بتغييرات محلية لتجاوز إعدادات النشر المدار، قم بتكوين كيفية دمج قوائم الاستثناءات المعرفة محليا [و عموميا](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>تكوين قائمة الاستثناءات استنادا إلى اسم المجلد أو ملحق الملف

يمكنك الاختيار من بين عدة أساليب لتعريف الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام Intune لتكوين اسم الملف أو المجلد أو استثناءات ملحقات الملفات

راجع المقالات التالية:

- [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure)
- [برنامج الحماية من الفيروسات من Microsoft Defender إعدادات تقييد الجهاز Windows 10 Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام "إدارة التكوين" لتكوين اسم الملف أو المجلد أو استثناءات ملحقات الملفات

راجع [كيفية إنشاء سياسات](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) مكافحة البرامج الضارة ونشرها: إعدادات الاستثناء للحصول على تفاصيل حول إدارة نقاط النهاية من Microsoft (الفرع الحالي).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>استخدام "نهج المجموعة" لتكوين استثناءات ملحقات الملفات أو المجلدات

> [!NOTE]
> إذا قمت بتحديد مسار مؤهل بالكامل لملف، يتم استبعاد هذا الملف فقط. إذا تم تعريف مجلد في الاستثناء، يتم استبعاد كل الملفات والمجلدات الفرعية ضمن هذا المجلد.

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **الاستثناءات**.

4. افتح **الإعداد استثناءات المسار** للتحرير، وأضف استثناءاتك.
    1. تعيين الخيار إلى **تمكين**.
    2. ضمن المقطع **خيارات** ، حدد **إظهار**.
    3. حدد كل مجلد على السطر الخاص به ضمن **العمود اسم** القيمة.
    4. إذا كنت تحدد ملفا، فتأكد من إدخال مسار مؤهل بالكامل إلى الملف، بما في ذلك حرف محرك الأقراص ومسار المجلد واسم الملف والملحق. 
    5. أدخل **0** في **عمود القيمة** .

5. اختر **موافق**.

6. افتح **الإعداد استثناءات الملحقات** للتحرير وأضف استثناءاتك.
    1. تعيين الخيار إلى **تمكين**.
    2. ضمن المقطع **خيارات** ، حدد **إظهار**.
    3. أدخل كل ملحق ملف على السطر الخاص به ضمن **العمود اسم** القيمة.
    4. أدخل **0** في **عمود القيمة** .

7. اختر **موافق**.

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام PowerShell cmdlets لتكوين اسم الملف أو المجلد أو استثناءات ملحقات الملفات

يتطلب استخدام PowerShell لإضافة استثناءات للملفات أو إزالتها استنادا إلى اسم الملف أو الموقع أو الملحق استخدام مجموعة من ثلاثة cmdlets ومعلمة قائمة الاستثناء المناسبة. يتم كل cmdlets في الوحدة [النمطية Defender](/powershell/module/defender/).

تنسيق cmdlets هو كما يلي:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

يسرد الجدول التالي cmdlets التي يمكنك استخدامها `<cmdlet>` في جزء cmdlet في PowerShell:

<br/><br/>

|إجراء التكوين|PowerShell cmdlet|
|:---|:---|
|إنشاء القائمة أو الكتابة فوقها|`Set-MpPreference`|
|إضافة إلى القائمة|`Add-MpPreference`|
|إزالة عنصر من القائمة|`Remove-MpPreference`|

يسرد الجدول التالي القيم التي يمكنك استخدامها `<exclusion list>` في جزء cmdlet في PowerShell:

<br/><br/>

|نوع الاستثناء|معلمة PowerShell|
|---|---|
|كل الملفات ذات ملحق ملف محدد|`-ExclusionExtension`|
|كل الملفات الموجودة ضمن مجلد (بما في ذلك الملفات الموجودة في ا لمعانات فرعية) أو ملف معين|`-ExclusionPath`|

> [!IMPORTANT]
> إذا قمت بإنشاء قائمة، `Set-MpPreference` `Add-MpPreference`إما باستخدام أو ، `Set-MpPreference` فإن استخدام الأمر cmdlet مرة أخرى سيكتم الكتابة فوق القائمة الموجودة.

على سبيل المثال، قد تتسبب قصاصة التعليمات البرمجية التالية برنامج الحماية من الفيروسات من Microsoft Defender عمليات فحص لاستبعاد أي ملف بملحق `.test` الملف:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> لمزيد من المعلومات، راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدم Windows أدوات الإدارة (WMI) لتكوين أسماء الملفات أو المجلدات أو استثناءات ملحقات الملفات

استخدم [أساليب تعيين الفئة](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) MSFT_MpPreference وإضافتها وإزالتها للخصائص التالية:

```WMI
ExclusionExtension
ExclusionPath
```

إن **استخدام "** تعيين" و"**إضافة**" و"إزالة" مماثل لنظيراتها في PowerShell: `Set-MpPreference`و `Add-MpPreference`و.`Remove-MpPreference`

> [!TIP]
> لمزيد من المعلومات، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام تطبيق أمن Windows لتكوين أسماء الملفات أو المجلدات أو استثناءات ملحقات الملفات

راجع [إضافة استثناءات في تطبيق أمن Windows للحصول](microsoft-defender-security-center-antivirus.md) على الإرشادات.

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>استخدام أحرف البدل في اسم الملف ومسار المجلد أو قوائم استثناءات الملحقات

يمكنك استخدام العلامة `*``?`النجمية أو علامة الاستفهام أو متغيرات البيئة (`%ALLUSERSPROFILE%`مثل ) مثل أحرف البدل عند تعريف العناصر في اسم الملف أو قائمة استثناء مسار المجلد. تختلف الطريقة التي يتم بها تفسير أحرف البدل هذه عن استخدامها المعتاد في التطبيقات واللغات الأخرى. تأكد من قراءة هذا المقطع لفهم القيود الخاصة بها.

> [!IMPORTANT]
> هناك قيود أساسية وسيناريوهات استخدام لأحجام البدل هذه:
>
> - يقتصر استخدام متغيرات البيئة على متغيرات الأجهزة وتلك المطبقة على العمليات التي يتم تشغيلها ك حساب NT AUTHORITY\SYSTEM.
> - يمكنك فقط استخدام ستة أحرف بدل كحد أقصى لكل إدخال.
> - لا يمكنك استخدام حرف بدل مكان حرف محرك الأقراص.
> - يتم وضع النجمة `*` في استثناء مجلد في مكان لمجلد واحد. استخدم مثيلات متعددة للإشارة `\*\` إلى مجلدات متداخلة متعددة بأسماء غير محددة.
> - حاليا، Microsoft Endpoint Configuration Manager أحرف البدل (مثل `*` أو `?`).
    
يصف الجدول التالي كيفية استخدام أحرف البدل ويوفر بعض الأمثلة.

<br/><br/>

|أحرف البدل|أمثلة|
|---|---|
|`*` (asterisk) <p> في **تضمينات ملحقات** أسماء الملفات واسم الملف، تستبدل النجمة أي عدد من الأحرف، ولا تنطبق إلا على الملفات الموجودة في المجلد الأخير المعرف في الوسيطة. <p> في **استثناءات المجلدات**، تستبدل النجمة مجلدا واحدا. استخدم المضاعف `*` مع شرط مائلة `\` للمجلدات للإشارة إلى مجلدات متداخلة متعددة. بعد مطابقة عدد المجلدات المسماة والمجلدات المسماة، يتم أيضا تضمين كل المجلدات الفرعية.|`C:\MyData\*.txt` يتضمن `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` يتضمن أي ملف في `C:\somepath\Archives\Data` والملفات الفرعية `C:\somepath\Authorized\Data` الخاصة به والملفات الفرعية الخاصة به <p> `C:\Serv\*\*\Backup` يتضمن أي ملف في `C:\Serv\Primary\Denied\Backup` والملفات الفرعية `C:\Serv\Secondary\Allowed\Backup` والملفات الفرعية الخاصة به|
|`?` (علامة استفهام)  <p> في **تضمينات ملحقات** ملحقات أسماء الملفات واسم الملف، تستبدل علامة استفهام حرفا واحدا، ولا تنطبق إلا على الملفات الموجودة في المجلد الأخير المعرف في الوسيطة. <p> في **استثناءات المجلدات**، تستبدل علامة استفهام حرفا واحدا في اسم المجلد. بعد مطابقة عدد المجلدات المسماة والمجلدات المسماة، يتم أيضا تضمين كل المجلدات الفرعية.|`C:\MyData\my?.zip` يتضمن `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` يتضمن أي ملف في `C:\somepath\P\Data` والملفات الفرعية الخاصة به  <p> `C:\somepath\test0?\Data` تضمين أي ملف في `C:\somepath\test01\Data` والملفات الفرعية الخاصة به|
|متغيرات البيئة <p> يتم ملء المتغير المعرف كمسار عند تقييم الاستثناء.|`%ALLUSERSPROFILE%\CustomLogFiles` سيتم تضمين `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> إذا قمت بخلط وسيطة استثناء ملف مع وسيطة استثناء مجلد، ستتوقف القواعد عند تطابق وسيطة الملف في المجلد المطابق، ولن تبحث عن تطابقات الملفات في أي مجلدات فرعية.
>
> على سبيل المثال، يمكنك استبعاد كل الملفات التي تبدأ ب "التاريخ" `c:\data\final\marked` `c:\data\review\marked` في المجلدات وباستخدام وسيطة القاعدة `c:\data\*\marked\date*`.
>
> ومع ذلك، لن تتطابق هذه الوسيطة مع أي ملفات في المكاتب الفرعية ضمن `c:\data\final\marked` أو `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>متغيرات بيئة النظام

يسرد الجدول التالي متغيرات بيئة حساب النظام ويصفها.

<br/><br/>

|متغير بيئة النظام هذا...|عمليات إعادة التوجيه إلى هذا|
|---|---|
|`%APPDATA%`|`C:\Users\UserName.DomainName\AppData\Roaming`|
|`%APPDATA%\Microsoft\Internet Explorer\Quick Launch`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Internet Explorer\Quick Launch`|
|`%APPDATA%\Microsoft\Windows\Start Menu`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu`|
|`%APPDATA%\Microsoft\Windows\Start Menu\Programs`|`C:\Windows\System32\config\systemprofile\AppData\Roaming\Microsoft\Windows\Start Menu\Programs`|
|`%LOCALAPPDATA%`|`C:\Windows\System32\config\systemprofile\AppData\Local`|
|`%ProgramData%`|`C:\ProgramData`|
|`%ProgramFiles%`|`C:\Program Files`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles%\Windows Sidebar\Gadgets`|`C:\Program Files\Windows Sidebar\Gadgets`|
|`%ProgramFiles%\Common Files`|`C:\Program Files\Common Files`|
|`%ProgramFiles(x86)%`|`C:\Program Files (x86)`|
|`%ProgramFiles(x86)%\Common Files`|`C:\Program Files (x86)\Common Files`|
|`%SystemDrive%`|`C:`|
|`%SystemDrive%\Program Files`|`C:\Program Files`|
|`%SystemDrive%\Program Files (x86)`|`C:\Program Files (x86)`|
|`%SystemDrive%\Users`|`C:\Users`|
|`%SystemDrive%\Users\Public`|`C:\Users\Public`|
|`%SystemRoot%`|`C:\Windows`|
|`%windir%`|`C:\Windows`|
|`%windir%\Fonts`|`C:\Windows\Fonts`|
|`%windir%\Resources`|`C:\Windows\Resources`|
|`%windir%\resources\0409`|`C:\Windows\resources\0409`|
|`%windir%\system32`|`C:\Windows\System32`|
|`%ALLUSERSPROFILE%`|`C:\ProgramData`|
|`%ALLUSERSPROFILE%\Application Data`|`C:\ProgramData\Application Data`|
|`%ALLUSERSPROFILE%\Documents`|`C:\ProgramData\Documents`|
|`%ALLUSERSPROFILE%\Documents\My Music\Sample Music`|`C:\ProgramData\Documents\My Music\Sample Music`|
|`%ALLUSERSPROFILE%\Documents\My Music`|`C:\ProgramData\Documents\My Music`|
|`%ALLUSERSPROFILE%\Documents\My Pictures`|`C:\ProgramData\Documents\My Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Pictures\Sample Pictures`|`C:\ProgramData\Documents\My Pictures\Sample Pictures`|
|`%ALLUSERSPROFILE%\Documents\My Videos`|`C:\ProgramData\Documents\My Videos`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\DeviceMetadataStore`|`C:\ProgramData\Microsoft\Windows\DeviceMetadataStore`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\GameExplorer`|`C:\ProgramData\Microsoft\Windows\GameExplorer`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Ringtones`|`C:\ProgramData\Microsoft\Windows\Ringtones`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu`|`C:\ProgramData\Microsoft\Windows\Start Menu`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\StartUp`|`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`|
|`%ALLUSERSPROFILE%\Microsoft\Windows\Templates`|`C:\ProgramData\Microsoft\Windows\Templates`|
|`%ALLUSERSPROFILE%\Start Menu`|`C:\ProgramData\Start Menu`|
|`%ALLUSERSPROFILE%\Start Menu\Programs`| `C:\ProgramData\Start Menu\Programs`|
|`%ALLUSERSPROFILE%\Start Menu\Programs\Administrative Tools`|`C:\ProgramData\Start Menu\Programs\Administrative Tools`|
|`%ALLUSERSPROFILE%\Templates`|`C:\ProgramData\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\ConnectedSearch\Templates`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\ConnectedSearch\Templates`|
|`%LOCALAPPDATA%\Microsoft\Windows\History`|`C:\Windows\System32\config\systemprofile\AppData\Local\Microsoft\Windows\History`|
|`%PUBLIC%`|`C:\Users\Public`|
|`%PUBLIC%\AccountPictures`|`C:\Users\Public\AccountPictures`|
|`%PUBLIC%\Desktop`|`C:\Users\Public\Desktop`|
|`%PUBLIC%\Documents`|`C:\Users\Public\Documents`|
|`%PUBLIC%\Downloads`|`C:\Users\Public\Downloads`|
|`%PUBLIC%\Music\Sample Music`|`C:\Users\Public\Music\Sample Music`|
|`%PUBLIC%\Music\Sample Playlists`|`C:\Users\Public\Music\Sample Playlists`|
|`%PUBLIC%\Pictures\Sample Pictures`|`C:\Users\Public\Pictures\Sample Pictures`|
|`%PUBLIC%\RecordedTV.library-ms`|`C:\Users\Public\RecordedTV.library-ms`|
|`%PUBLIC%\Videos`|`C:\Users\Public\Videos`|
|`%PUBLIC%\Videos\Sample Videos`|`C:\Users\Public\Videos\Sample Videos`|
|`%USERPROFILE%`|`C:\Users\UserName`|
|`%USERPROFILE%\AppData\Local`|`C:\Users\UserName\AppData\Local`|
|`%USERPROFILE%\AppData\LocalLow`|`C:\Users\UserName\AppData\LocalLow`|
|`%USERPROFILE%\AppData\Roaming`|`C:\Users\UserName\AppData\Roaming`|

## <a name="review-the-list-of-exclusions"></a>مراجعة قائمة الاستثناءات

يمكنك استرداد العناصر الموجودة في قائمة الاستثناء باستخدام أحد الأساليب التالية:

- [Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- MpCmdRun
- PowerShell
- [أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> سيتم عرض تغييرات قائمة الاستثناء التي تم **إدخالها** باستخدام "نهج المجموعة" في القوائم في [أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md).
>
> لن تظهر التغييرات أمن Windows التطبيق **في** قوائم نهج المجموعة.

إذا كنت تستخدم PowerShell، يمكنك استرداد القائمة باستخدام طريقتين:

- استرداد حالة كل برنامج الحماية من الفيروسات من Microsoft Defender المفضلة. يتم عرض كل قائمة على أسطر منفصلة، ولكن يتم دمج العناصر ضمن كل قائمة في السطر نفسه.
- اكتب حالة كل التفضيلات إلى متغير، ثم استخدم هذا المتغير لاستدعاء القائمة المحددة التي تريدها فقط. يتم كتابة كل `Add-MpPreference` استخدام ل إلى سطر جديد.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>التحقق من صحة قائمة الاستثناء باستخدام MpCmdRun

للتحقق من الاستثناءات باستخدام أداة [سطر ](./command-line-arguments-microsoft-defender-antivirus.md)الأوامر المخصصة mpcmdrun.exe، استخدم الأمر التالي:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> يتطلب التحقق من الاستثناءات باستخدام MpCmdRun برنامج الحماية من الفيروسات من Microsoft Defender من 4.18.2111-5.0 (تم إصداره في ديسمبر 2021) أو إصدار لاحق.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>راجع قائمة الاستثناءات إلى جانب جميع تفضيلات برنامج الحماية من الفيروسات من Microsoft Defender الأخرى باستخدام PowerShell

استخدم cmdlet التالي:

```PowerShell
Get-MpPreference
```

في المثال التالي، يتم `ExclusionExtension` تمييز العناصر المضمنة في القائمة:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="إخراج PowerShell ل Get-MpPreference.":::

لمزيد من المعلومات، راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>استرداد قائمة استثناءات معينة باستخدام PowerShell

استخدم قصاصة التعليمات البرمجية التالية (أدخل كل سطر ك أمر منفصل)؛ **استبدل WDAVprefs** بأي تسمية تريد تسمية المتغير بها:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

في المثال التالي، يتم تقسيم القائمة إلى أسطر جديدة لكل استخدام ل `Add-MpPreference` cmdlet:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="يعرض إخراج PowerShell الإدخالات فقط في قائمة الاستثناء.":::

لمزيد من المعلومات، راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>التحقق من صحة قوائم الاستثناءات باستخدام ملف اختبار EICAR

يمكنك التحقق من عمل قوائم الاستثناء باستخدام PowerShell `Invoke-WebRequest` مع cmdlet أو الفئة .NET WebClient لتنزيل ملف اختباري.

في قصاصة PowerShell `test.txt` التالية، استبدل بملف يتوافق مع قواعد الاستثناء. على سبيل المثال، إذا قمت باستبعاد `.testing` الملحق، فاستبدل `test.txt` ب `test.testing`. إذا كنت تقوم باختبار مسار، فتأكد من تشغيل الأمر cmdlet داخل هذا المسار.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

إذا برنامج الحماية من الفيروسات من Microsoft Defender عن وجود برامج ضارة، فإن القاعدة لا تعمل. إذا لم يكن هناك تقرير عن وجود برامج ضارة وكان الملف الذي تم تنزيله موجودا، فإن الاستثناء يعمل. يمكنك فتح الملف للتأكد من أن المحتويات هي نفسها التي تم وصفها في موقع ملف [اختبار EICAR على الويب](http://www.eicar.org/86-0-Intended-use.html).

يمكنك أيضا استخدام تعليمات PowerShell البرمجية التالية، التي تستدعي الفئة .NET WebClient لتنزيل ملف الاختبار - `Invoke-WebRequest` كما هو الأمر مع cmdlet `c:\test.txt` ؛ استبدال بملف يتوافق مع القاعدة التي تقوم بالتحقق من صحتها:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

إذا لم يكن لديك اتصال بالإنترنت، يمكنك إنشاء ملف اختبار EICAR الخاص بك عن طريق كتابة سلسلة EICAR إلى ملف نصي جديد باستخدام الأمر PowerShell التالي:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

يمكنك أيضا نسخ السلسلة إلى ملف نصي فارغ ومحاولة حفظها باسم الملف أو في المجلد الذي تحاول استبعاده.

## <a name="see-also"></a>راجع أيضًا

- [تكوين الاستثناءات والتحقق من صحتها في برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها للملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين برنامج الحماية من الفيروسات من Microsoft Defender استثناءات على Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
