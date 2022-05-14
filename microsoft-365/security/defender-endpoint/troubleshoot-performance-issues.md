---
title: استكشاف مشاكل الأداء وإصلاحها
description: استكشاف أخطاء الاستخدام العالي لوحدة المعالجة المركزية المتعلقة بخدمة الحماية في الوقت الحقيقي في Microsoft Defender لنقطة النهاية وإصلاحها.
keywords: استكشاف الأخطاء وإصلاحها، والأداء، والاستخدام العالي لوحدة المعالجة المركزية، والاستخدام العالي لوحدة المعالجة المركزية، والخطأ، والإصلاح، وتحديث التوافق، وoms، والمراقبة، والإبلاغ، برنامج الحماية من الفيروسات من Microsoft Defender
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
ms.date: 10/19/2021
audience: ITPro
ms.topic: troubleshooting
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 01db84f3ddd4eae79cae2fa97400f4d3d78ba8da
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419737"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>استكشاف مشاكل الأداء المتعلقة بالحماية في الوقت الحقيقي وإصلاحها


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

إذا كان نظامك يواجه مشاكل عالية في استخدام وحدة المعالجة المركزية أو الأداء تتعلق بخدمة الحماية في الوقت الحقيقي في Microsoft Defender لنقطة النهاية، يمكنك إرسال تذكرة إلى دعم Microsoft. اتبع الخطوات الواردة في [تجميع البيانات التشخيصية برنامج الحماية من الفيروسات من Microsoft Defender](collect-diagnostic-data.md).

بصفتك مسؤولا، يمكنك أيضا استكشاف هذه المشكلات وإصلاحها بنفسك.

أولا، قد تحتاج إلى التحقق مما إذا كان سبب المشكلة هو برنامج آخر. اقرأ [التحقق مع المورد بحثا عن استثناءات الحماية من الفيروسات](#check-with-vendor-for-antivirus-exclusions).

وإلا، يمكنك تحديد البرنامج المرتبط بمشكلة الأداء المحددة باتباع الخطوات [الواردة في "تحليل سجل حماية Microsoft](#analyze-the-microsoft-protection-log)".

يمكنك أيضا توفير سجلات إضافية لإرسالك إلى دعم Microsoft باتباع الخطوات الواردة في:

- [تسجيل سجلات العمليات باستخدام "مراقبة العمليات"](#capture-process-logs-using-process-monitor)
- [تسجيل سجلات الأداء باستخدام مسجل الأداء Windows](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>التحقق مع المورد بحثا عن استثناءات برنامج الحماية من الفيروسات

إذا كان بإمكانك تحديد البرنامج الذي يؤثر على أداء النظام بسهولة، فانتقل إلى قاعدة معارف مورد البرامج أو مركز الدعم. ابحث عما إذا كانت لديهم توصيات حول استثناءات برنامج الحماية من الفيروسات. إذا لم يكن موقع ويب الخاص بالمورد متوفرا لديه، يمكنك فتح تذكرة دعم معه ومطالبته بنشر تذكرة.

نوصي بموردي البرامج باتباع الإرشادات المختلفة في [الشراكة مع الصناعة لتقليل النتائج الإيجابية الخاطئة](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). يمكن للمورد إرسال برامجه من خلال [مدخل التحليل الذكي لمخاطر الأمان من Microsoft](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

## <a name="analyze-the-microsoft-protection-log"></a>تحليل سجل حماية Microsoft

في **MPLog-xxxxxxxx-xxxxxx.log**، يمكنك العثور على معلومات تأثير الأداء المقدرة لتشغيل البرامج ك *EstimatedImpact*:

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|اسم الحقل|الوصف|
|---|---|
|ProcessImageName|معالجة اسم الصورة|
|TotalTime|المدة التراكمية بالمللي ثانية التي تم إنفاقها في عمليات مسح الملفات التي تم الوصول إليها بواسطة هذه العملية|
|عدد|عدد الملفات الممسوحة ضوئيا التي تم الوصول إليها بواسطة هذه العملية|
|الحد الأقصى للوقت|المدة بالمللي ثانية في أطول فحص فردي لملف تم الوصول إليه بواسطة هذه العملية|
|MaxTimeFile|مسار الملف الذي تم الوصول إليه بواسطة هذه العملية الذي تم تسجيل أطول فحص للمدة `MaxTime` له|
|EstimatedImpact|النسبة المئوية للوقت المستغرق في عمليات الفحص بحثا عن الملفات التي تم الوصول إليها بواسطة هذه العملية خارج الفترة التي شهدت فيها هذه العملية نشاط الفحص|
|

إذا كان تأثير الأداء مرتفعا، فحاول إضافة العملية إلى استثناءات المسار/العملية باتباع الخطوات في [تكوين الاستثناءات والتحقق من صحتها لعمليات المسح برنامج الحماية من الفيروسات من Microsoft Defender](collect-diagnostic-data.md).

إذا لم تحل الخطوة السابقة المشكلة، يمكنك جمع المزيد من المعلومات من خلال ["مراقبة العملية](#capture-process-logs-using-process-monitor)" أو [Windows "مسجل الأداء"](#capture-performance-logs-using-windows-performance-recorder) في الأقسام التالية.

## <a name="capture-process-logs-using-process-monitor"></a>تسجيل سجلات العمليات باستخدام "مراقبة العمليات"

مراقبة العملية (ProcMon) هي أداة مراقبة متقدمة يمكنها إظهار العمليات في الوقت الحقيقي. يمكنك استخدام هذا لتسجيل مشكلة الأداء أثناء حدوثها.

1. تنزيل [Process Monitor v3.60](/sysinternals/downloads/procmon) إلى مجلد مثل `C:\temp`.

2. لإزالة علامة الملف على الويب:
    1. انقر بزر الماوس الأيمن **فوقProcessMonitor.zip** وحدد **"خصائص**".
    1. ضمن علامة التبويب *"عام* "، ابحث عن *"الأمان*".
    1. حدد المربع إلى جانب **إلغاء الحظر**.
    1. حدد **Apply**.

    :::image type="content" source="images/procmon-motw.png" alt-text="صفحة إزالة MOTW" lightbox="images/procmon-motw.png":::

3. قم بإلغاء ضغط الملف `C:\temp` بحيث يكون `C:\temp\ProcessMonitor`مسار المجلد .

4. انسخ **ProcMon.exe** إلى عميل Windows أو خادم Windows الذي تقوم باستكشاف الأخطاء وإصلاحها.

5. قبل تشغيل ProcMon، تأكد من إغلاق جميع التطبيقات الأخرى غير المرتبطة بمشكلة استخدام وحدة المعالجة المركزية العالية. سيؤدي القيام بذلك إلى تقليل عدد العمليات المراد التحقق منها.

6. يمكنك تشغيل ProcMon بطريقتين.
    1. انقر بزر الماوس الأيمن **فوقProcMon.exe** وحدد **"تشغيل كمسؤول**".

        منذ بدء التسجيل تلقائيا، حدد أيقونة عدسة التكبير لإيقاف الالتقاط الحالي أو استخدم اختصار لوحة المفاتيح **Ctrl+E**.

        :::image type="content" source="images/procmon-magglass.png" alt-text="أيقونة عدسة التكبير" lightbox="images/procmon-magglass.png":::

        للتحقق من إيقاف الالتقاط، تحقق مما إذا كانت أيقونة عدسة التكبير تظهر الآن مع علامة X حمراء.

        :::image type="content" source="images/procmon-magglass-stop.png" alt-text="شرطة مائلة حمراء" lightbox="images/procmon-magglass-stop.png":::

        بعد ذلك، لمسح الالتقاط السابق، حدد أيقونة الممحاة.

        :::image type="content" source="images/procmon-eraser-clear.png" alt-text="الأيقونة &quot;مسح&quot;" lightbox="images/procmon-eraser-clear.png":::

        أو استخدم اختصار لوحة المفاتيح **Ctrl+X**.

    2. الطريقة الثانية هي تشغيل **سطر الأوامر** كمسؤول، ثم من مسار "مراقبة العملية"، قم بتشغيل:

       :::image type="content" source="images/cmd-procmon.png" alt-text="cmd procmon" lightbox="images/cmd-procmon.png":::

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > اجعل نافذة ProcMon صغيرة قدر الإمكان عند التقاط البيانات حتى تتمكن من بدء التتبع وإيقافه بسهولة.
        >
        > :::image type="content" source="images/procmon-minimize.png" alt-text="الصفحة التي تعرض تصغير Procmon" lightbox="images/procmon-minimize.png":::

7. بعد اتباع أحد الإجراءات في الخطوة 6، سترى بعد ذلك خيارا لتعيين عوامل التصفية. حدد **موافق**. يمكنك دائما تصفية النتائج بعد اكتمال الالتقاط.

   :::image type="content" source="images/procmon-filter-options.png" alt-text="الصفحة التي يتم اختيار &quot;استبعاد النظام&quot; عليها كاسم عملية التصفية" lightbox="images/procmon-filter-options.png":::

8. لبدء الالتقاط، حدد أيقونة عدسة التكبير مرة أخرى.

9. إعادة إنشاء المشكلة.

    > [!TIP]
    > انتظر حتى يتم إعادة إنتاج المشكلة بالكامل، ثم دون الطابع الزمني عند بدء التتبع.

10. بمجرد أن يكون لديك دقيقتان إلى أربع دقائق من نشاط العملية أثناء حالة استخدام وحدة المعالجة المركزية العالية، أوقف الالتقاط عن طريق تحديد أيقونة عدسة التكبير.

11. لحفظ الالتقاط باسم فريد وبتنسيق .pml، حدد **"ملف**" ثم حدد **"حفظ...**". تأكد من تحديد الأزرار التبادلية **"All events**" و"**Native Process Monitor Format" (PML).**

    :::image type="content" source="images/procmon-savesettings1.png" alt-text="صفحة إعدادات الحفظ" lightbox="images/procmon-savesettings1.png":::

12. لتعقب أفضل، قم بتغيير المسار الافتراضي من `C:\temp\ProcessMonitor\LogFile.PML` حيث `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` :
    - `%ComputerName%` هو اسم الجهاز
    - `MMDDYEAR` هو الشهر واليوم والسنة
    - `Repro_of_issue` هو اسم المشكلة التي تحاول إعادة إنتاجها

    > [!TIP]
    > إذا كان لديك نظام عمل، فقد ترغب في الحصول على نموذج سجل للمقارنة.

13. اضغط على ملف .pml وأرسله إلى دعم Microsoft.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>تسجيل سجلات الأداء باستخدام مسجل الأداء Windows

يمكنك استخدام Windows Performance Recorder (WPR) لتضمين معلومات إضافية في عمليات الإرسال إلى دعم Microsoft. WPR هي أداة تسجيل قوية تنشئ "تتبع الأحداث" لتسجيلات Windows.

WPR هو جزء من Windows Assessment and Deployment Kit (Windows ADK) ويمكن تنزيلها من [Download وتثبيت Windows ADK](/windows-hardware/get-started/adk-install). يمكنك أيضا تنزيله كجزء من Windows 10 Software Development Kit في [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

يمكنك استخدام واجهة مستخدم WPR باتباع الخطوات الواردة في [سجلات أداء الالتقاط باستخدام واجهة مستخدم WPR](#capture-performance-logs-using-the-wpr-ui).

بدلا من ذلك، يمكنك أيضا استخدام أداة سطر الأوامر *wpr.exe*، والتي تتوفر في Windows 8 والإصدارات الأحدث باتباع الخطوات في [سجلات أداء الالتقاط باستخدام WPR CLI](#capture-performance-logs-using-the-wpr-cli).

### <a name="capture-performance-logs-using-the-wpr-ui"></a>تسجيل سجلات الأداء باستخدام واجهة مستخدم WPR

> [!TIP]
> إذا كانت هناك أجهزة متعددة تواجه هذه المشكلة، فاستخدم الجهاز الذي يحتوي على ذاكرة الوصول العشوائي الأكثر.

1. تنزيل WPR وتثبيته.

2. ضمن *Windows Kits*، انقر بزر الماوس الأيمن **Windows "مسجل الأداء**".

   :::image type="content" source="images/wpr-01.png" alt-text="قائمة البدء" lightbox="images/wpr-01.png":::

    حدد **المزيد**. حدد **"تشغيل كمسؤول**".

3. عندما يظهر مربع الحوار "التحكم في حساب المستخدم"، حدد **"نعم**".

   :::image type="content" source="images/wpt-yes.png" alt-text="صفحة UAC" lightbox="images/wpt-yes.png":::

4. بعد ذلك، قم بتنزيل ملف تعريف [تحليل Microsoft Defender لنقطة النهاية](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) واحفظه `MDAV.wprp` في مجلد مثل `C:\temp`.

5. في مربع الحوار WPR، حدد **المزيد من الخيارات**.

   :::image type="content" source="images/wpr-03.png" alt-text="الصفحة التي يمكنك تحديد المزيد من الخيارات عليها" lightbox="images/wpr-03.png":::


6. حدد **"إضافة ملفات تعريف"...** واستعرض وصولا إلى مسار `MDAV.wprp` الملف.

7. بعد ذلك، يجب أن تشاهد مجموعة ملفات تعريف جديدة ضمن *قياسات مخصصة* تسمى *تحليل Microsoft Defender لنقطة النهاية* تحته.

   :::image type="content" source="images/wpr-infile.png" alt-text="داخل الملف" lightbox="images/wpr-infile.png":::

    > [!WARNING]
    > إذا كان Windows Server يحتوي على 64 غيغابايت من ذاكرة الوصول العشوائي أو أكثر، فاستخدم القياس `Microsoft Defender for Endpoint analysis for large servers` المخصص بدلا من `Microsoft Defender for Endpoint analysis`. وإلا، فقد يستهلك النظام الخاص بك كمية كبيرة من ذاكرة التجمع غير الصفحات أو المخازن المؤقتة التي يمكن أن تؤدي إلى عدم استقرار النظام. يمكنك اختيار ملفات التعريف التي تريد إضافتها عن طريق توسيع **Resource Analysis**.
    يوفر ملف التعريف المخصص هذا السياق الضروري لتحليل الأداء المتعمق.

8. لاستخدام القياس المخصص Microsoft Defender لنقطة النهاية ملف تعريف تحليل مطول في واجهة مستخدم WPR:

    1. تأكد من عدم تحديد ملفات تعريف ضمن مجموعات *الفرز من المستوى الأول* *وتحليل الموارد* *وتحليل السيناريو* .
    2. حدد **القياسات المخصصة**.
    3. حدد **تحليل Microsoft Defender لنقطة النهاية**.
    4. حدد **Verbose** ضمن مستوى *التفاصيل* .
    5. حدد **"ملف"** أو **"ذاكرة** " ضمن وضع "التسجيل".

    > [!IMPORTANT]
    > يجب تحديد *File* لاستخدام وضع تسجيل الملفات إذا كان يمكن إعادة إنتاج مشكلة الأداء مباشرة من قبل المستخدم. تندرج معظم المشاكل ضمن هذه الفئة. ومع ذلك، إذا لم يتمكن المستخدم من إعادة إنتاج المشكلة مباشرة ولكن يمكن أن يلاحظها بسهولة بمجرد حدوث المشكلة، يجب على المستخدم تحديد *Memory* لاستخدام وضع تسجيل الذاكرة. وهذا يضمن أن سجل التتبع لن ينفخ بشكل مفرط بسبب وقت المدى الطويل.

9. أنت الآن جاهز لجمع البيانات. قم بإنهاء كافة التطبيقات غير ذات الصلة بإعادة إنتاج مشكلة الأداء. يمكنك تحديد **"إخفاء الخيارات** " للحفاظ على المساحة التي تشغلها نافذة WPR صغيرة.

   :::image type="content" source="images/wpr-08.png" alt-text="خيارات &quot;إخفاء&quot;" lightbox="images/wpr-08.png":::

    > [!TIP]
    > حاول بدء التتبع في عدد صحيح من الثوان. على سبيل المثال، 01:30:00. وهذا سيجعل من السهل تحليل البيانات. حاول أيضا تعقب الطابع الزمني تماما عند إعادة إنتاج المشكلة.

10. حدد **"ابدأ**".

    :::image type="content" source="images/wpr-09.png" alt-text="صفحة معلومات نظام السجلات" lightbox="images/wpr-09.png":::

11. إعادة إنشاء المشكلة.

    > [!TIP]
    > الاحتفاظ بجمع البيانات إلى ما لا يزيد عن خمس دقائق. من دقيقتين إلى ثلاث دقائق هو نطاق جيد حيث يتم جمع الكثير من البيانات.

12. حدد **حفظ**.

    :::image type="content" source="images/wpr-10.png" alt-text="الخيار &quot;حفظ&quot;" lightbox="images/wpr-10.png":::

13. قم **بتعبئة النوع في وصف مفصل للمشكلة:** مع معلومات حول المشكلة وكيفية إعادة إنتاج المشكلة.

    :::image type="content" source="images/wpr-12.png" alt-text="الجزء الذي تقوم بتعبئة فيه" lightbox="images/wpr-12.png":::

    1. حدد **اسم الملف:** لتحديد مكان حفظ ملف التتبع. بشكل افتراضي، يتم حفظه إلى `%user%\Documents\WPR Files\`.
    1. حدد **حفظ**.

14. انتظر بينما يتم دمج التتبع.

    :::image type="content" source="images/wpr-13.png" alt-text="جمع التتبع العام ل WPR" lightbox="images/wpr-13.png":::

15. بمجرد حفظ التتبع، حدد **"فتح المجلد**".

    :::image type="content" source="images/wpr-14.png" alt-text="الصفحة التي تعرض الإعلام بحفظ تتبع WPR" lightbox="images/wpr-14.png":::

    قم بتضمين كل من الملف والمجلد في عمليات الإرسال إلى دعم Microsoft.

    :::image type="content" source="images/wpr-15.png" alt-text="تفاصيل الملف والمجلد" lightbox="images/wpr-15.png":::

### <a name="capture-performance-logs-using-the-wpr-cli"></a>تسجيل سجلات الأداء باستخدام WPR CLI

تعد أداة سطر الأوامر *wpr.exe* جزءا من نظام التشغيل بدءا من Windows 8. لتجميع تتبع WPR باستخدام أداة سطر الأوامر wpr.exe:

1. تنزيل ملف تعريف **[تحليل Microsoft Defender لنقطة النهاية](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** لتتبعات الأداء إلى ملف مسمى `MDAV.wprp` في دليل محلي مثل `C:\traces`.

2. انقر بزر الماوس الأيمن فوق أيقونة **قائمة البدء** وحدد **Windows PowerShell (المسؤول)** أو **موجه الأوامر (المسؤول)** لفتح نافذة موجه أوامر المسؤول.

3. عندما يظهر مربع الحوار "التحكم في حساب المستخدم"، حدد **"نعم**".

4. في المطالبة المرتفعة، قم بتشغيل الأمر التالي لبدء تتبع أداء Microsoft Defender لنقطة النهاية:

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > إذا كان خادم Windows يحتوي على 64 غيغابايت أو ذاكرة وصول عشوائي أو أكثر، فاستخدم ملفات التعريف `WDForLargeServers.Light` وعوضا `WDForLargeServers.Verbose` عن ملفات التعريف `WD.Light` و`WD.Verbose`، على التوالي. وإلا، فقد يستهلك النظام الخاص بك كمية كبيرة من ذاكرة التجمع غير الصفحات أو المخازن المؤقتة التي يمكن أن تؤدي إلى عدم استقرار النظام.

5. إعادة إنشاء المشكلة.

    > [!TIP]
    > احتفظ بمجموعة البيانات لا تزيد عن خمس دقائق. اعتمادا على السيناريو، من دقيقتين إلى ثلاث دقائق هو نطاق جيد حيث يتم جمع الكثير من البيانات.

6. عند المطالبة المرتفعة، قم بتشغيل الأمر التالي لإيقاف تتبع الأداء، مع التأكد من توفير معلومات حول المشكلة وكيفية إعادة إنتاج المشكلة:

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. انتظر حتى يتم دمج التتبع.

8. قم بتضمين كل من الملف والمجلد في الإرسال إلى دعم Microsoft.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [جمع البيانات التشخيصية برنامج الحماية من الفيروسات من Microsoft Defender](collect-diagnostic-data.md)
- [تكوين الاستثناءات والتحقق من صحتها لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
