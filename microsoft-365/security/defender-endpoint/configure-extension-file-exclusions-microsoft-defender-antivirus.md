---
title: تكوين الاستثناءات والتحقق من صحتها استنادا إلى الملحق أو الاسم أو الموقع
description: استبعاد الملفات من عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender استنادا إلى ملحق الملف أو اسم الملف أو موقعه.
keywords: الاستثناءات، والملفات، والملحق، ونوع الملف، واسم المجلد، واسم الملف، والمسح الضوئي
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
ms.collection: M365-security-compliance
ms.openlocfilehash: 7b1614738b17d7f3cf78a6bfabb84f85196d42ff
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873237"
---
# <a name="configure-and-validate-exclusions-based-on-file-extension-and-folder-location"></a>تكوين الاستثناءات والتحقق من صحتها استنادا إلى ملحق الملف وموقع المجلد

**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يمكنك تحديد استثناءات برنامج الحماية من الفيروسات من Microsoft Defender التي تنطبق على [عمليات الفحص المجدولة](schedule-antivirus-scans.md)، [والمسح حسب الطلب](run-scan-microsoft-defender-antivirus.md)، [والحماية والمراقبة في الوقت الحقيقي دائما](configure-real-time-protection-microsoft-defender-antivirus.md). **بشكل عام، يجب ألا تحتاج إلى تطبيق الاستثناءات**. إذا كنت بحاجة إلى تطبيق الاستثناءات، يمكنك الاختيار من بين عدة أنواع مختلفة:

- الاستثناءات المستندة إلى ملحقات الملفات ومواقع المجلدات (الموضحة في هذه المقالة)
- [استثناءات الملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

> [!IMPORTANT]
> لا تنطبق استثناءات برنامج الحماية من الفيروسات من Microsoft Defender على قدرات Microsoft Defender لنقطة النهاية الأخرى، مثل [قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction) [والوصول إلى المجلدات الخاضعة للرقابة](/microsoft-365/security/defender-endpoint/controlled-folders). لا يزال بإمكان الملفات التي تستثنيها باستخدام الأساليب الموضحة في هذه المقالة تشغيل تنبيهات الكشف التلقائي والاستجابة على النقط النهائية وغيرها من عمليات الكشف.
> لاستبعاد الملفات على نطاق واسع، أضفها إلى [المؤشرات المخصصة](/microsoft-365/security/defender-endpoint/manage-indicators) Microsoft Defender لنقطة النهاية.

## <a name="before-you-begin"></a>قبل البدء

راجع [التوصيات لتعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md) قبل تعريف قوائم الاستبعاد الخاصة بك.

## <a name="exclusion-lists"></a>قوائم الاستبعاد

لاستبعاد ملفات معينة من عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender، يمكنك تعديل قوائم الاستبعاد الخاصة بك. تتضمن برنامج الحماية من الفيروسات من Microsoft Defender العديد من الاستثناءات التلقائية استنادا إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية، مثل تلك المستخدمة في إدارة المؤسسة وإدارة قاعدة البيانات وسيناريوهات المؤسسة وحالاتها الأخرى.

> [!NOTE]
> تنطبق الاستثناءات على عمليات الكشف عن التطبيقات غير المرغوب فيها (PUA) أيضا.
>
> تنطبق الاستثناءات التلقائية فقط على Windows Server 2016 والإي وقت لاحق. هذه الاستثناءات غير مرئية في تطبيق أمن Windows وفي PowerShell.

يسرد الجدول التالي بعض الأمثلة على الاستثناءات استنادا إلى ملحق الملف وموقع المجلد.

|الاستبعاد|أمثلة|قائمة الاستبعاد|
|---|---|---|
|أي ملف ذي ملحق معين|جميع الملفات ذات الملحق المحدد، في أي مكان على الجهاز. <p> بناء جملة صالح: `.test` و `test`|استثناءات الملحق|
|أي ملف ضمن مجلد معين|كافة الملفات الموجودة `c:\test\sample` ضمن المجلد|استثناءات الملفات والمجلدات|
|ملف معين في مجلد معين|الملف `c:\sample\sample.test` فقط|استثناءات الملفات والمجلدات|
|عملية معينة|الملف القابل للتنفيذ `c:\test\process.exe`|استثناءات الملفات والمجلدات|

## <a name="characteristics-of-exclusion-lists"></a>خصائص قوائم الاستبعاد

- تنطبق استثناءات المجلد على كافة الملفات والمجلدات الموجودة ضمن هذا المجلد، إلا إذا كان المجلد الفرعي نقطة إعادة توزيع. يجب استبعاد المجلدات الفرعية لإعادة توزيع النقاط بشكل منفصل.
- تنطبق ملحقات الملف على أي اسم ملف له الملحق المحدد إذا لم يتم تعريف مسار أو مجلد.

## <a name="important-notes-about-exclusions-based-on-file-extensions-and-folder-locations"></a>ملاحظات هامة حول الاستثناءات استنادا إلى ملحقات الملفات ومواقع المجلدات

- سيؤدي استخدام أحرف البدل مثل العلامة النجمية (\*) إلى تغيير كيفية تفسير قواعد الاستبعاد. راجع القسم ["استخدام أحرف البدل" في اسم الملف ومسار المجلد أو مقطع استبعاد الملحق](#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) للحصول على معلومات هامة حول كيفية عمل أحرف البدل.

- لا تستبعد محركات أقراص الشبكة المعينة. حدد مسار الشبكة الفعلي.

- لن يتم تضمين المجلدات التي يتم إعادة توزيع النقاط التي تم إنشاؤها بعد بدء تشغيل الخدمة برنامج الحماية من الفيروسات من Microsoft Defender والتي تمت إضافتها إلى قائمة الاستبعاد. أعد تشغيل الخدمة (عن طريق إعادة تشغيل Windows) ليتم التعرف على نقاط إعادة التوزيع الجديدة كهدف استبعاد صالح.

- تنطبق الاستثناءات على [عمليات الفحص المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)، [والمسح الضوئي عند الطلب](run-scan-microsoft-defender-antivirus.md)، [والحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md)، ولكن ليس عبر Defender لنقطة النهاية. لتحديد الاستثناءات عبر Defender لنقطة النهاية، استخدم [المؤشرات المخصصة](manage-indicators.md).

- بشكل افتراضي، سيتم دمج التغييرات المحلية التي تم إجراؤها على القوائم (من قبل المستخدمين الذين لديهم امتيازات المسؤول، بما في ذلك التغييرات التي تم إجراؤها باستخدام PowerShell وWMI) مع القوائم كما تم تحديدها (ونشرها) بواسطة نهج المجموعة أو Configuration Manager أو Intune. تأخذ قوائم نهج المجموعة الأسبقية عند وجود تعارضات. بالإضافة إلى ذلك، تظهر تغييرات قائمة الاستبعاد التي تم إجراؤها باستخدام نهج المجموعة في [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).

- للسماح للتغييرات المحلية بتجاوز إعدادات النشر المدارة، [قم بتكوين كيفية دمج قوائم الاستثناءات المعرفة محليا وبشكل عام](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists).

## <a name="configure-the-list-of-exclusions-based-on-folder-name-or-file-extension"></a>تكوين قائمة الاستثناءات استنادا إلى اسم المجلد أو ملحق الملف

يمكنك الاختيار من بين عدة أساليب لتعريف الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-intune-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام Intune لتكوين استثناءات اسم الملف أو المجلد أو ملحق الملف

راجع المقالات التالية:

- [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure)
- [برنامج الحماية من الفيروسات من Microsoft Defender إعدادات تقييد الجهاز Windows 10 في Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus)

### <a name="use-configuration-manager-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام Configuration Manager لتكوين استثناءات اسم الملف أو المجلد أو ملحق الملف

راجع [كيفية إنشاء نهج مكافحة البرامج الضارة ونشرها: إعدادات الاستثناء](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) للحصول على تفاصيل حول تكوين إدارة نقاط النهاية من Microsoft (الفرع الحالي).

### <a name="use-group-policy-to-configure-folder-or-file-extension-exclusions"></a>استخدام نهج المجموعة لتكوين استثناءات ملحق المجلد أو الملف

> [!NOTE]
> إذا قمت بتحديد مسار مؤهل بالكامل إلى ملف، فسيتم استبعاد هذا الملف فقط. إذا تم تعريف مجلد في الاستثناء، فسيتم استبعاد كافة الملفات والدلائل الفرعية ضمن هذا المجلد.

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات لـ Windows Defender** \> **الاستثناءات**.

4. افتح إعداد **"استثناءات المسار"** للتحرير، وأضف الاستثناءات.

    1. تعيين الخيار إلى **ممكن**.
    2. ضمن المقطع **"خيارات** "، حدد **"إظهار**".
    3. حدد كل مجلد على السطر الخاص به ضمن عمود **اسم القيمة** .
    4. إذا كنت تحدد ملفا، فتأكد من إدخال مسار مؤهل بالكامل إلى الملف، بما في ذلك حرف محرك الأقراص ومسار المجلد واسم الملف والملحق.
    5. أدخل **0** في عمود **"القيمة** ".

5. اختر **"موافق**".

6. افتح إعداد Extension **Exclusions** للتحرير وأضف الاستثناءات الخاصة بك.

    1. تعيين الخيار إلى **ممكن**.
    2. ضمن المقطع **"خيارات** "، حدد **"إظهار**".
    3. أدخل كل ملحق ملف على السطر الخاص به ضمن عمود **اسم القيمة** .
    4. أدخل **0** في عمود **"القيمة** ".

7. اختر **"موافق**".

<a id="ps"></a>

### <a name="use-powershell-cmdlets-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام أوامر cmdlets PowerShell لتكوين اسم الملف أو المجلد أو استثناءات ملحق الملف

يتطلب استخدام PowerShell لإضافة استثناءات للملفات أو إزالتها استنادا إلى اسم الملحق أو الموقع أو الملف استخدام مجموعة من ثلاثة أوامر cmdlets ومعلمة قائمة الاستبعاد المناسبة. أوامر cmdlets كلها في [وحدة Defender](/powershell/module/defender/).

تنسيق أوامر cmdlets هو كما يلي:

```PowerShell
<cmdlet> -<exclusion list> "<item>"
```

يسرد الجدول التالي أوامر cmdlets التي يمكنك استخدامها في `<cmdlet>` جزء PowerShell cmdlet:

|إجراء التكوين|PowerShell cmdlet|
|:---|:---|
|إنشاء القائمة أو الكتابة فوقها|`Set-MpPreference`|
|إضافة إلى القائمة|`Add-MpPreference`|
|إزالة عنصر من القائمة|`Remove-MpPreference`|

يسرد الجدول التالي القيم التي يمكنك استخدامها في `<exclusion list>` جزء PowerShell cmdlet:

|نوع الاستبعاد|معلمة PowerShell|
|---|---|
|كافة الملفات ذات ملحق ملف محدد|`-ExclusionExtension`|
|كافة الملفات الموجودة ضمن مجلد (بما في ذلك الملفات في الدلائل الفرعية) أو ملف معين|`-ExclusionPath`|

> [!IMPORTANT]
> إذا قمت بإنشاء قائمة، إما باستخدام `Set-MpPreference` cmdlet أو `Add-MpPreference`باستخدامه `Set-MpPreference` مرة أخرى، فسيؤدي ذلك إلى الكتابة فوق القائمة الموجودة.

على سبيل المثال، قد تتسبب القصاصة البرمجية التالية في إجراء عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender لاستبعاد أي ملف ذي `.test` ملحق الملف:

```PowerShell
Add-MpPreference -ExclusionExtension ".test"
```

> [!TIP]
> لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) [وSmdlets لبرنامج الحماية من الفيروسات من Defender](/powershell/module/defender/).

### <a name="use-windows-management-instrumentation-wmi-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدام Windows Management Instrumentation (WMI) لتكوين اسم الملف أو المجلد أو استثناءات ملحق الملف

استخدم [أساليب المجموعة والإضافة والإزالة للفئة MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ExclusionExtension
ExclusionPath
```

يعد استخدام **Set** **وإضافة** **وإزالة** مماثلا لنظيراتها في PowerShell: `Set-MpPreference`و، `Add-MpPreference`و.`Remove-MpPreference`

> [!TIP]
> لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="man-tools"></a>

### <a name="use-the-windows-security-app-to-configure-file-name-folder-or-file-extension-exclusions"></a>استخدم تطبيق أمن Windows لتكوين اسم الملف أو المجلد أو استثناءات ملحق الملف

راجع [إضافة استثناءات في تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md) للحصول على الإرشادات.

<a id="wildcards"></a>

## <a name="use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>استخدام أحرف البدل في اسم الملف ومسار المجلد أو قوائم استثناء الملحق

يمكنك استخدام العلامة النجمية `*`أو علامة الاستفهام `?`أو متغيرات البيئة (مثل `%ALLUSERSPROFILE%`) كأحرف البدل عند تعريف العناصر في اسم الملف أو قائمة استبعاد مسار المجلد. تختلف الطريقة التي يتم بها تفسير أحرف البدل هذه عن استخدامها المعتاد في التطبيقات واللغات الأخرى. تأكد من قراءة هذا القسم لفهم قيودها المحددة.

> [!IMPORTANT]
> هناك قيود رئيسية وسيناريوهات استخدام لأحرف البدل هذه:
> - يقتصر استخدام متغير البيئة على متغيرات الجهاز وتلك التي تنطبق على العمليات التي تعمل كحساب NT AUTHORITY\SYSTEM.
> - يمكنك فقط استخدام ستة أحرف بدل كحد أقصى لكل إدخال.
> - لا يمكنك استخدام حرف بدل بدلا من حرف محرك الأقراص.
> - توجد علامة نجمية `*` في استثناء مجلد في مكانها لمجلد واحد. استخدم مثيلات `\*\` متعددة للإشارة إلى مجلدات متعددة متداخلة بأسماء غير محددة.
> - حاليا، لا يعتمد Microsoft Endpoint Configuration Manager أحرف البدل (مثل `*` أو`?`).
    
يصف الجدول التالي كيفية استخدام أحرف البدل ويوفر بعض الأمثلة.

|بدل|أمثلة|
|---|---|
|`*` (علامة نجمية) <p> في **تضمينات اسم الملف وملحق الملف**، تحل العلامة النجمية محل أي عدد من الأحرف، وتنطبق فقط على الملفات الموجودة في المجلد الأخير المعرف في الوسيطة. <p> في **استثناءات المجلد**، تحل العلامة النجمية محل مجلد واحد. استخدم مضاعفا `*` مع شرطة مائلة `\` للمجلدات للإشارة إلى مجلدات متعددة متداخلة. بعد مطابقة عدد المجلدات المسماة وبطاقة البدل، يتم أيضا تضمين كافة المجلدات الفرعية.|`C:\MyData\*.txt` يتضمن `C:\MyData\notes.txt` <p> `C:\somepath\*\Data` يتضمن أي ملف في `C:\somepath\Archives\Data` ومجلداته الفرعية `C:\somepath\Authorized\Data` ومجلداته الفرعية <p> `C:\Serv\*\*\Backup` يتضمن أي ملف في `C:\Serv\Primary\Denied\Backup` ومجلداته الفرعية ومجلداته `C:\Serv\Secondary\Allowed\Backup` الفرعية|
|`?` (علامة استفهام)  <p> في **تضمينات اسم الملف وملحق الملف**، تحل علامة الاستفهام محل حرف واحد، وتنطبق فقط على الملفات الموجودة في المجلد الأخير المعرف في الوسيطة. <p> في **استثناءات المجلد**، تحل علامة الاستفهام محل حرف واحد في اسم مجلد. بعد مطابقة عدد المجلدات المسماة وبطاقة البدل، يتم أيضا تضمين كافة المجلدات الفرعية.|`C:\MyData\my?.zip` يتضمن `C:\MyData\my1.zip` <p> `C:\somepath\?\Data` يتضمن أي ملف في `C:\somepath\P\Data` ومجلداته الفرعية  <p> `C:\somepath\test0?\Data` سيتضمن أي ملف في `C:\somepath\test01\Data` ومجلداته الفرعية|
|متغيرات البيئة <p> يتم ملء المتغير المحدد كمسار عند تقييم الاستبعاد.|`%ALLUSERSPROFILE%\CustomLogFiles` ستتضمن `C:\ProgramData\CustomLogFiles\Folder1\file1.txt`|

> [!IMPORTANT]
> إذا قمت بخلط وسيطة استثناء ملف مع وسيطة استثناء مجلد، فستتوقف القواعد عند تطابق وسيطة الملف في المجلد المطابق، ولن تبحث عن تطابقات الملفات في أي مجلدات فرعية.
> على سبيل المثال، يمكنك استبعاد كافة الملفات التي تبدأ ب "التاريخ" في المجلدات `c:\data\final\marked` `c:\data\review\marked` وباستخدام وسيطة `c:\data\*\marked\date*`القاعدة.
> ومع ذلك، لن تتطابق هذه الوسيطة مع أي ملفات في المجلدات الفرعية ضمن `c:\data\final\marked` أو `c:\data\review\marked`.

<a id="review"></a>

### <a name="system-environment-variables"></a>متغيرات بيئة النظام

يسرد الجدول التالي متغيرات بيئة حساب النظام ويصفها.

|متغير بيئة النظام هذا...|إعادة التوجيه إلى هذا|
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

يمكنك استرداد العناصر الموجودة في قائمة الاستبعاد باستخدام إحدى الطرق التالية:

- [Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)
- [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies)
- [MpCmdRun](command-line-arguments-microsoft-defender-antivirus.md)
- [PowerShell](/powershell/module/defender)
- [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md)

> [!IMPORTANT]
> **ستظهر** تغييرات قائمة الاستبعاد التي تم إجراؤها باستخدام نهج المجموعة في القوائم في [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).
> **لن تظهر** التغييرات التي تم إجراؤها في تطبيق أمن Windows في قوائم نهج المجموعة.

إذا كنت تستخدم PowerShell، يمكنك استرداد القائمة بطريقتين:

- استرداد حالة كافة تفضيلات برنامج الحماية من الفيروسات من Microsoft Defender. يتم عرض كل قائمة على أسطر منفصلة، ولكن يتم دمج العناصر الموجودة داخل كل قائمة في نفس السطر.
- اكتب حالة كافة التفضيلات إلى متغير، واستخدم هذا المتغير لاستدعاء القائمة المحددة التي تهتم بها فقط. تتم كتابة كل استخدام لسطر `Add-MpPreference` جديد.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>التحقق من صحة قائمة الاستبعاد باستخدام MpCmdRun

للتحقق من الاستثناءات باستخدام [أداة سطر الأوامر المخصصة mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md)، استخدم الأمر التالي:

```console
Start, CMD (Run as admin)
cd "%programdata%\microsoft\windows defender\platform"
cd 4.18.2111-5.0 (Where 4.18.2111-5.0 is this month's Microsoft Defender Antivirus "Platform Update".)
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> يتطلب التحقق من الاستثناءات باستخدام MpCmdRun برنامج الحماية من الفيروسات من Microsoft Defender إصدار 4.18.2111-5.0 (الذي تم إصداره في ديسمبر 2021) أو إصدار أحدث.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>مراجعة قائمة الاستثناءات إلى جانب جميع تفضيلات برنامج الحماية من الفيروسات من Microsoft Defender الأخرى باستخدام PowerShell

استخدم cmdlet التالي:

```PowerShell
Get-MpPreference
```

في المثال التالي، يتم تمييز العناصر المضمنة في `ExclusionExtension` القائمة:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="إخراج PowerShell ل Get-MpPreference" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) [وSmdlets لبرنامج الحماية من الفيروسات من Defender](/powershell/module/defender/).

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>استرداد قائمة استثناءات معينة باستخدام PowerShell

استخدم القصاصة البرمجية التالية (أدخل كل سطر كأوامر منفصلة)؛ استبدل **WDAVprefs** بأي تسمية تريد تسمية المتغير بها:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionExtension
$WDAVprefs.ExclusionPath
```

في المثال التالي، يتم تقسيم القائمة إلى أسطر جديدة لكل استخدام من `Add-MpPreference` cmdlet:

:::image type="content" source="../../media/wdav-powershell-get-exclusions-variable.png" alt-text="إخراج PowerShell يعرض الإدخالات في قائمة الاستبعاد فقط" lightbox="../../media/wdav-powershell-get-exclusions-variable.png":::

لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) [وSmdlets لبرنامج الحماية من الفيروسات من Defender](/powershell/module/defender/).

<a id="validate"></a>

## <a name="validate-exclusions-lists-with-the-eicar-test-file"></a>التحقق من صحة قوائم الاستثناءات باستخدام ملف اختبار EICAR

يمكنك التحقق من أن قوائم الاستبعاد الخاصة بك تعمل باستخدام PowerShell إما `Invoke-WebRequest` مع cmdlet أو فئة .NET WebClient لتنزيل ملف اختبار.

في قصاصة PowerShell البرمجية التالية، استبدلها `test.txt` بملف يتوافق مع قواعد الاستبعاد الخاصة بك. على سبيل المثال، إذا قمت باستبعاد `.testing` الملحق، فاستبدله `test.txt` ب `test.testing`. إذا كنت تختبر مسارا، فتأكد من تشغيل cmdlet داخل هذا المسار.

```PowerShell
Invoke-WebRequest "http://www.eicar.org/download/eicar.com.txt" -OutFile "test.txt"
```

إذا برنامج الحماية من الفيروسات من Microsoft Defender الإبلاغ عن البرامج الضارة، فإن القاعدة لا تعمل. إذا لم يكن هناك أي تقرير عن البرامج الضارة وكان الملف الذي تم تنزيله موجودا، فإن الاستبعاد يعمل. يمكنك فتح الملف لتأكيد أن المحتويات هي نفسها ما هو موضح على [موقع ويب ملف اختبار EICAR](http://www.eicar.org/86-0-Intended-use.html).

يمكنك أيضا استخدام التعليمات البرمجية PowerShell التالية، التي تستدعي فئة .NET WebClient لتنزيل ملف الاختبار - كما هو الحال مع `Invoke-WebRequest` cmdlet؛ استبدال `c:\test.txt` بملف يتوافق مع القاعدة التي تقوم بالتحقق من صحتها:

```PowerShell
$client = new-object System.Net.WebClient
$client.DownloadFile("http://www.eicar.org/download/eicar.com.txt","c:\test.txt")
```

إذا لم يكن لديك اتصال بالإنترنت، يمكنك إنشاء ملف اختبار EICAR الخاص بك عن طريق كتابة سلسلة EICAR إلى ملف نصي جديد باستخدام أمر PowerShell التالي:

```PowerShell
[io.file]::WriteAllText("test.txt",'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*')
```

يمكنك أيضا نسخ السلسلة إلى ملف نصي فارغ ومحاولة حفظها باسم الملف أو في المجلد الذي تحاول استبعاده.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [تكوين الاستثناءات والتحقق من صحتها في عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات للملفات التي يتم فتحها بواسطة العمليات والتحقق من صحتها](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين استثناءات برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows](configure-server-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
