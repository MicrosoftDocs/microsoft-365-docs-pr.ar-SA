---
title: استكشاف مشاكل Microsoft Defender لنقطة النهاية في الحافظة وإصلاحها
description: استكشاف المشاكل التي قد تنشأ أثناء اجهزه الالجهزه أو Microsoft Defender لنقطة النهاية الخدمة.
keywords: استكشاف الأخطاء المتعلقة باللوح وإصلاحها، ومشكلات الboard، وعارض الأحداث، وبناءات تجميع البيانات والمعاينة، وبيانات المستشعر، والت تشخيصات
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 9813857bffe62ab26d377d49b2830f55d0f38f93
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473486"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-onboarding-issues"></a>استكشاف مشاكل Microsoft Defender لنقطة النهاية في الحافظة وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows Server 2012 R2
- Windows Server 2016‏
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

قد تحتاج إلى استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية التكهين إذا واجهت مشاكل.
توفر هذه الصفحة خطوات تفصيلية لاستعلام مشاكل التكدث وإصلاحها التي قد تحدث عند النشر باستخدام إحدى أدوات النشر والأخطاء الشائعة التي قد تحدث على الأجهزة.

قبل البدء في استكشاف الأخطاء وإصلاحها باستخدام أدوات المستلزمات، من المهم التحقق مما إذا كان قد تم تحقيق الحد الأدنى من المتطلبات للأجهزة التي تريد تشغيلها في الخدمات. [تعرف على متطلبات الترخيص والأجهزة والبرامج للأجهزة المجهزة للخدمة](minimum-requirements.md).

## <a name="troubleshoot-issues-with-onboarding-tools"></a>استكشاف المشاكل وإصلاحها باستخدام أدوات الرصيد

إذا أكملت عملية الضم ولم تشاهد الأجهزة في قائمة الأجهزة بعد ساعة، فقد تشير إلى [](investigate-machines.md) مشكلة في الضم أو الاتصال.

### <a name="troubleshoot-onboarding-when-deploying-with-group-policy"></a>استكشاف الأخطاء في الحافظة وإصلاحها عند النشر باستخدام نهج المجموعة

يتم النشر باستخدام نهج المجموعة عن طريق تشغيل البرنامج النصي ل التشغيل على الأجهزة. لا نهج المجموعة وحدة التحكم هذه ما إذا نجح النشر أم لا.

إذا أكملت عملية الضم ولم تتمكن من رؤية الأجهزة في قائمة الأجهزة بعد ساعة واحدة، [](investigate-machines.md) يمكنك التحقق من إخراج البرنامج النصي على الأجهزة. لمزيد من المعلومات، راجع استكشاف الأخطاء [وإصلاحها عند النشر باستخدام برنامج نصي](#troubleshoot-onboarding-when-deploying-with-a-script).

إذا اكتمل البرنامج النصي بنجاح، فشاهد استكشاف أخطاء التكدث وإصلاحها على [الأجهزة](#troubleshoot-onboarding-issues-on-the-device) للحصول على أخطاء إضافية قد تحدث.

### <a name="troubleshoot-onboarding-issues-when-deploying-with-microsoft-endpoint-configuration-manager"></a>استكشاف مشاكل الboarding وإصلاحها عند النشر باستخدام Microsoft Endpoint Configuration Manager

عند وضع الأجهزة في الحافظة باستخدام الإصدارات التالية من Configuration Manager:

- Microsoft Endpoint Configuration Manager
- إدارة تكوين System Center 2012
- System Center 2012 R2 Configuration Manager

يتم النشر باستخدام الإصدارات المذكورة أعلاه من Configuration Manager عن طريق تشغيل البرنامج النصي ل التشغيل على الأجهزة. يمكنك تعقب النشر في وحدة Configuration Manager التحكم.

إذا فشل النشر، يمكنك التحقق من إخراج البرنامج النصي على الأجهزة.

إذا اكتملت عملية الضم بنجاح ولكن الأجهزة لا تظهر في قائمة الأجهزة بعد ساعة واحدة،  فشاهد استكشاف أخطاء الضم وإصلاحها على الجهاز لمعرفة الأخطاء الإضافية التي قد تحدث.[](#troubleshoot-onboarding-issues-on-the-device)

### <a name="troubleshoot-onboarding-when-deploying-with-a-script"></a>استكشاف الأخطاء في الboarding وإصلاحها عند النشر باستخدام برنامج نصي

**تحقق من نتيجة البرنامج النصي على الجهاز:**

1. انقر **فوق** بدء، **عارض الأحداث**، ثم اضغط على **Enter**.

2. انتقل إلى **Windows Logs** \> **Application**.

3. ابحث عن حدث من **مصدر حدث WDATPOnboarding** .

إذا فشل البرنامج النصي وكان الحدث خطأ، يمكنك التحقق من "معرف الحدث" في الجدول التالي لمساعدتك على استكشاف المشكلة وإصلاحها.

> [!NOTE]
> إن "معرّفات الحدث" التالية خاصة بالنص النصي ل "التكهف" فقط.

<br>

****

|"معرّف الحدث"|نوع الخطأ|خطوات الحل|
|:---:|---|---|
|`5`|تم العثور على بيانات إلغاء الحذف ولكن لا يمكن حذفها|التحقق من الأذونات على السجل، على وجه التحديد <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.|
|`10`|لا يمكن كتابة بيانات الboarding إلى السجل|التحقق من الأذونات على السجل، على وجه التحديد <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`. <p> تحقق من تشغيل البرنامج النصي كمسؤول.|
|`15`|فشل بدء تشغيل خدمة SENSE|تحقق من صحة الخدمة (`sc query sense` الأمر). تأكد من أنها ليست في حالة وسيطة (*'* Pending_Stopped'، *'Pending_Running'*) وحاول تشغيل البرنامج النصي مرة أخرى (مع حقوق المسؤول). <p> إذا كان الجهاز قيد التشغيل Windows 10، فإن الإصدار 1607 `sc query sense` `START_PENDING`وتشغيل الأمر يرجع إعادة تشغيل الجهاز. إذا لم تعالج إعادة تشغيل الجهاز المشكلة، ف قم بالترقية إلى KB4015217 وحاول تشغيل الجهاز مرة أخرى.|
|`15`|فشل بدء تشغيل خدمة SENSE|إذا كانت رسالة الخطأ هي: حدث الخطأ 577 أو الخطأ 1058 في النظام، يجب تمكين برنامج تشغيل برنامج الحماية من الفيروسات من Microsoft Defender ELAM، راجع التأكد من أن [برنامج الحماية من الفيروسات من Microsoft Defender](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) غير معطل بواسطة نهج للحصول على الإرشادات.|
|`30`|فشل البرنامج النصي في انتظار بدء تشغيل الخدمة|قد تكون الخدمة قد اتخذت وقتا أكثر للبدء أو قد صادفت أخطاء أثناء محاولة البدء. لمزيد من المعلومات حول الأحداث والأخطاء المتعلقة ب SENSE، راجع مراجعة الأحداث والأخطاء [باستخدام عارض الأحداث](event-error-codes.md).|
|`35`|فشل البرنامج النصي في العثور على قيمة تسجيل حالة الboarding المطلوبة|عند بدء تشغيل خدمة SENSE للمرة الأولى، تكتب حالة الboarding إلى موقع التسجيل <p> `HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status`. <p> فشل البرنامج النصي في العثور عليه بعد عدة ثوان. يمكنك اختباره يدويا والتحقق مما إذا كان هناك. لمزيد من المعلومات حول الأحداث والأخطاء المتعلقة ب SENSE، راجع مراجعة الأحداث والأخطاء [باستخدام عارض الأحداث](event-error-codes.md).|
|`40`|لم يتم تعيين حالة إعداد خدمة SENSE إلى **1**|فشلت خدمة SENSE في ال متنها بشكل صحيح. لمزيد من المعلومات حول الأحداث والأخطاء المتعلقة ب SENSE، راجع مراجعة الأحداث والأخطاء [باستخدام عارض الأحداث](event-error-codes.md).|
|`65`|امتيازات غير كافية|تشغيل البرنامج النصي مرة أخرى باستخدام امتيازات المسؤول.|
|

### <a name="troubleshoot-onboarding-issues-using-microsoft-intune"></a>استكشاف مشاكل الحافظة وإصلاحها باستخدام Microsoft Intune

يمكنك استخدام Microsoft Intune للتحقق من رموز الأخطاء ومحاولة استكشاف سبب المشكلة وإصلاحها.

إذا قمت بتكوين نهج في Intune ولم يتم نشرها على الأجهزة، فقد تحتاج إلى تكوين تسجيل MDM تلقائي.

استخدم الجداول التالية لفهم الأسباب المحتملة للقضايا أثناء الإستخدام:

- Microsoft Intune رموز الخطأ OMA-URIs الجدول
- المشاكل المعروفة في جدول عدم التوافق
- جدول سجلات إدارة الجهاز الأجهزة المحمولة (MDM)

إذا لم تعمل أي من سجلات الأحداث والخطوات الخاصة استكشاف الأخطاء وإصلاحها، ف قم بتنزيل البرنامج النصي المحلي من قسم إدارة الأجهزة في المدخل، ثم قم بتشغيله في موجه أوامر غير محدث.

#### <a name="microsoft-intune-error-codes-and-oma-uris"></a>Microsoft Intune رموز الخطأ OMA-URIs

<br>

****

|رمز الخطأ Hex|رمز الخطأ ديسمبر|وصف الخطأ|OMA-URI|خطوات استكشاف الأخطاء وإصلاحها المحتملة|
|:---:|---|---|---|---|
|0x87D1FDE8|-2016281112|فشل المعالجة|الboarding <p> إيقاف التشغيل|**السبب المحتمل:** فشل التكليف أو الفقدان على أساس خطأ: توقيع غير صحيح أو حقول PreviousOrgIds مفقودة. <p> **خطوات استكشاف الأخطاء وإصلاحها:** <p> تحقق من "معرّف الحدث" في القسم "عرض أخطاء التكميل للعامل" [في المقطع "سجل أحداث](#view-agent-onboarding-errors-in-the-device-event-log) الجهاز". <p> تحقق من سجلات أحداث MDM في الجدول التالي أو اتبع الإرشادات الواردة في تشخيص حالات فشل [MDM في](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) Windows.|
||||الboarding <p> إيقاف التشغيل <p> SampleSharing|**السبب المحتمل:** Microsoft Defender لنقطة النهاية مفتاح تسجيل النهج غير موجود أو لا يكون لدى عميل OMA DM الأذونات للكتابة عليه. <p> **خطوات استكشاف الأخطاء وإصلاحها:** تأكد من وجود مفتاح التسجيل التالي: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <p> إذا لم يكن موجودا، فافتح أمر مرتفع وأضف المفتاح.|
||||SenseIsRunning <p> OnboardingState <p> OrgId|**السبب المحتمل:** محاولة المعالجة بواسطة خاصية للقراءة فقط. فشلت عملية التكهين. <p> **خطوات استكشاف الأخطاء وإصلاحها:** تحقق من خطوات استكشاف الأخطاء وإصلاحها في استكشاف مشاكل [التكدث وإصلاحها على الجهاز](#troubleshoot-onboarding-issues-on-the-device). <p> تحقق من سجلات أحداث MDM في الجدول التالي أو اتبع الإرشادات الواردة في تشخيص حالات فشل [MDM في](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10) Windows.|
||||الكل|**السبب المحتمل:** حاول نشر Microsoft Defender لنقطة النهاية SKU/النظام الأساسي غير المعتمد، لا سيما Holographic SKU. <p> الأنظمة الأساسية المدعمة حاليا: <p> Enterprise و Education و Professional.<p> الخادم غير معتمد.|
|0x87D101A9|-2016345687|SyncML(425): فشل الأمر المطلوب لأن المرسل لا لديه أذونات كافية للتحكم بالوصول (ACL) على المستلم.|الكل|**السبب المحتمل:** حاول نشر Microsoft Defender لنقطة النهاية SKU/النظام الأساسي غير المعتمد، لا سيما Holographic SKU.<p> الأنظمة الأساسية المدعمة حاليا: <p> Enterprise و Education و Professional.|
|

#### <a name="known-issues-with-non-compliance"></a>المشاكل المعروفة المتعلقة بعدم التوافق

يوفر الجدول التالي معلومات حول المشاكل المتعلقة بعدم التوافق وكيفية معالجة المشاكل.

<br>

****

|Case|الأعراض|خطوات استكشاف الأخطاء وإصلاحها المحتملة|
|:---:|---|---|
|`1`|يتوافق الجهاز مع SenseIsRunning OMA-URI. ولكنه غير متوافق مع OrgId و Onboarding و OnboardingState OMA-URIs.|**السبب المحتمل:** تحقق من اجتياز المستخدم ل OOBE بعد Windows أو ترقيته. أثناء تشغيل OOBE، لا يمكن إكماله ولكن SENSE قيد التشغيل بالفعل. <p> **خطوات استكشاف الأخطاء وإصلاحها:** انتظر حتى اكتمال OOBE.|
|`2`|يتوافق الجهاز مع OrgId و OnboardingState OMA-URI، ولكنه غير متوافق بواسطة SenseIsRunning OMA-URI.|**السبب المحتمل:** يتم تعيين نوع بدء تشغيل خدمة Sense على أنه "بدء متأخر". في بعض الأحيان يؤدي ذلك Microsoft Intune الخادم إلى الإبلاغ عن الجهاز على أنه غير متوافق بواسطة SenseIsRunning عند حدوث جلسة عمل DM عند بدء تشغيل النظام. <p> **خطوات استكشاف الأخطاء وإصلاحها:** يجب أن يتم إصلاح المشكلة تلقائيا في غضون 24 ساعة.|
|`3`|الجهاز غير متوافق|**خطوات استكشاف الأخطاء وإصلاحها:** تأكد من عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه.|
|

#### <a name="mobile-device-management-mdm-event-logs"></a>سجلات إدارة الجهاز المحمول (MDM)

عرض سجلات أحداث MDM لا استكشاف الأخطاء التي قد تحدث أثناء ال متنهار وإصلاحها:

اسم السجل: Microsoft\Windows\DeviceManagement-EnterpriseDiagnostics-Provider

اسم القناة: المسؤول

<br>

****

|الم ID|الخطورة|وصف الحدث|خطوات استكشاف الأخطاء وإصلاحها|
|---|---|---|---|
|1819|الخطأ|Microsoft Defender لنقطة النهاية CSP: فشل تعيين قيمة العقدة. NodeId: (٪1), TokenName: (٪2), Result: (٪3).|قم [بتنزيل التحديث التراكمي Windows 10 1607](https://go.microsoft.com/fwlink/?linkid=829760).|
|

## <a name="troubleshoot-onboarding-issues-on-the-device"></a>استكشاف مشاكل الboard على الجهاز وإصلاحها

إذا لم تشير أدوات النشر المستخدمة إلى وجود خطأ في عملية الضم، ولكن الأجهزة لا تزال لا تظهر في قائمة الأجهزة خلال ساعة واحدة، فاستعرض مواضيع التحقق التالية للتحقق مما إذا حدث خطأ مع وكيل Microsoft Defender لنقطة النهاية.

- [عرض أخطاء تسجيل العامل في سجل أحداث الجهاز](#view-agent-onboarding-errors-in-the-device-event-log)
- [التأكد من تمكين خدمة البيانات التشخيصية](#ensure-the-diagnostics-service-is-enabled)
- [التأكد من تعيين الخدمة للبدء](#ensure-the-service-is-set-to-start)
- [التأكد من أن الجهاز لديه اتصال بالإنترنت](#ensure-the-device-has-an-internet-connection)
- [تأكد من برنامج الحماية من الفيروسات من Microsoft Defender معطل بواسطة نهج](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

### <a name="view-agent-onboarding-errors-in-the-device-event-log"></a>عرض أخطاء تسجيل العامل في سجل أحداث الجهاز

1. انقر **فوق** بدء، **عارض الأحداث**، ثم اضغط على **Enter**.

2. في الجزء **عارض الأحداث (محلي)،** قم بتوسيع التطبيقات والخدمات **سجلات** \> **Microsoft** \>  \> Windows **SENSE**.

   > [!NOTE]
   > SENSE هو الاسم الداخلي المستخدم للإشارة إلى المستشعر السلوكي الذي Microsoft Defender لنقطة النهاية.

3. حدد **تشغيل** لتحميل السجل.

4. في جزء **الإجراءات** ، انقر فوق **تصفية السجل الحالي**.

5. على علامة **التبويب تصفية** ، ضمن **مستوى الحدث:** حدد **هام** **وتحذير** **وخطأ**، وانقر فوق **موافق**.

   :::image type="content" source="images/filter-log.png" alt-text="عامل عارض الأحداث تسجيل الدخول" lightbox="images/filter-log.png":::

6. ستظهر الأحداث التي يمكن أن تشير إلى وجود مشاكل في **جزء** التشغيل. يمكنك محاولة استكشاف الأخطاء وإصلاحها استنادا إلى الحلول في الجدول التالي:

   <br>

   ****

   |"معرّف الحدث"|رسالة|خطوات الحل|
   |:---:|---|---|
   |`5`|Microsoft Defender لنقطة النهاية خدمة الاتصال للخادم عند _المتغير_|[تأكد من أن الجهاز لديه اتصال بالإنترنت](#ensure-the-device-has-an-internet-connection).|
   |`6`|Microsoft Defender لنقطة النهاية الخدمة غير مواد كما لم يتم العثور على معلمات الboarding. رمز الفشل: _متغير_|[تشغيل البرنامج النصي للدبور مرة أخرى](configure-endpoints-script.md).|
   |`7`|Microsoft Defender لنقطة النهاية خدمة الخدمة قراءة معلمات التكهين. رمز الفشل: _متغير_|[تأكد من أن الجهاز لديه اتصال](#ensure-the-device-has-an-internet-connection) بالإنترنت، ثم قم بتشغيل عملية التكامل بالكامل مرة أخرى.|
   |`9`|Microsoft Defender لنقطة النهاية الخدمة إلى تغيير نوع البدء. رمز الفشل: متغير|إذا حدث الحدث أثناء التكهين، فحاول إعادة التشغيل ثم إعادة تشغيل البرنامج النصي للدبوس. للحصول على مزيد من المعلومات، [راجع تشغيل البرنامج النصي للدبور مرة أخرى](configure-endpoints-script.md). <br><br>إذا حدث الحدث أثناء إيقاف التشغيل، فاتصل بالدعم.|
   |`10`|Microsoft Defender لنقطة النهاية فشل الخدمة في الاستمرار في معلومات الboarding. رمز الفشل: متغير|إذا حدث الحدث أثناء التكهين، فحاول إعادة تشغيل البرنامج النصي للدبور. للحصول على مزيد من المعلومات، [راجع تشغيل البرنامج النصي للدبور مرة أخرى](configure-endpoints-script.md). <br><br>إذا استمرت المشكلة، فاتصل بالدعم.|
   |`15`|Microsoft Defender لنقطة النهاية بدء قناة الأوامر باستخدام عنوان URL: _متغير_|[تأكد من أن الجهاز لديه اتصال بالإنترنت](#ensure-the-device-has-an-internet-connection).|
   |`17`|Microsoft Defender لنقطة النهاية هذه الخدمة إلى تغيير موقع خدمة "تجارب المستخدمين المتصلين" و"بيانات الاستخدام". رمز الفشل: متغير|[تشغيل البرنامج النصي للدبور مرة أخرى](configure-endpoints-script.md). إذا استمرت المشكلة، فاتصل بالدعم.|
   |`25`|Microsoft Defender لنقطة النهاية الخدمة بإعادة تعيين حالة الصحة في السجل. رمز الفشل: _متغير_|اتصل بالدعم.|
   |`27`|فشل تمكين Microsoft Defender لنقطة النهاية في Windows Defender. فشلت عملية التكهين. رمز الفشل: متغير|اتصل بالدعم.|
   |`29`|فشل قراءة معلمات إيقاف التشغيل. نوع الخطأ: ٪1، رمز الخطأ: ٪2، الوصف: ٪3|تأكد من أن الجهاز لديه اتصال بالإنترنت، ثم قم بتشغيل عملية إيقاف التشغيل بالكامل مرة أخرى.|
   |`30`|فشل تعطيل وضع $(build.sense.productDisplayName) في Microsoft Defender لنقطة النهاية. رمز الفشل: ٪1|اتصل بالدعم.|
   |`32`|فشل طلب خدمة $(build.sense.productDisplayName) لإيقاف تشغيلها بعد عملية إيقاف التشغيل. رمز الفشل: ٪1|تحقق من أن نوع بدء الخدمة يدوي وأبدأ تشغيل الجهاز.|
   |`55`|فشل إنشاء "برنامج تأمين ETW" التلقائي. رمز الفشل: ٪1|إعادة تشغيل الجهاز.|
   |`63`|تحديث نوع بدء الخدمة الخارجية. الاسم: ٪1، نوع البدء الفعلي: ٪2، نوع البدء المتوقع: ٪3، رمز الخروج: ٪4|تحديد ما الذي يتسبب في حدوث تغييرات في نوع بدء الخدمة المذكورة. إذا لم تكن رمز الخروج 0، فصلح نوع البدء يدويا إلى نوع البدء المتوقع.|
   |`64`|بدء الخدمة الخارجية المتوقفة. الاسم: ٪1، رمز الخروج: ٪2|اتصل بالدعم إذا استمر الحدث في الظهور.|
   |`68`|نوع بدء الخدمة غير متوقع. اسم الخدمة: ٪1، نوع البدء الفعلي: ٪2، نوع البدء المتوقع: ٪3|تحديد ما الذي يتسبب في حدوث تغييرات في نوع البدء. إصلاح نوع بدء الخدمة المذكورة.|
   |`69`|تم إيقاف الخدمة. اسم الخدمة: ٪1|ابدأ تشغيل الخدمة المذكورة. اتصل بالدعم في حالة استمراره.|
   |

هناك مكونات إضافية على الجهاز يعتمد Microsoft Defender لنقطة النهاية العامل على تشغيلها بشكل صحيح. إذا لم يكن هناك أي أخطاء ذات صلة بالتهيئة في سجل أحداث Microsoft Defender لنقطة النهاية، فاتبع الخطوات التالية للتأكد من تكوين المكونات الإضافية بشكل صحيح.

<span id="ensure-the-diagnostics-service-is-enabled" />

### <a name="ensure-the-diagnostic-data-service-is-enabled"></a>التأكد من تمكين خدمة البيانات التشخيصية

إذا لم يتم الإبلاغ عن الأجهزة بشكل صحيح، فقد تحتاج إلى التحقق من تعيين Windows البيانات التشخيصية إلى بدء تشغيلها تلقائيا وتشغيلها على الجهاز. ربما تم تعطيل الخدمة بواسطة برامج أخرى أو تغييرات تكوين المستخدم.

أولا، يجب التحقق من تعيين الخدمة للبدء تلقائيا عند بدء Windows، ثم يجب التحقق من أن الخدمة قيد التشغيل حاليا (وبدء تشغيلها إذا لم تكن كذلك).

### <a name="ensure-the-service-is-set-to-start"></a>التأكد من تعيين الخدمة للبدء

**استخدم سطر الأوامر للتحقق من نوع Windows بدء تشغيل خدمة البيانات التشخيصية**:

1. افتح موجه سطر أوامر مرتفعا على الجهاز:

   أ. انقر **فوق** بدء، وا **اكتب cmd**، ثم اضغط على **Enter**.

   ب. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي، ثم اضغط على **Enter**:

   ```console
   sc qc diagtrack
   ```

   إذا تم تمكين الخدمة، يجب أن تبدو النتيجة على شكل لقطة الشاشة التالية:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="نتيجة أمر استعلام sc ل diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

   `START_TYPE` إذا لم يتم تعيين إلى `AUTO_START`، فسوف تحتاج إلى تعيين الخدمة للبدء تلقائيا.

**استخدم سطر الأوامر لتعيين Windows البيانات التشخيصية تلقائيا:**

1. افتح موجه سطر أوامر مرتفعا على الجهاز:

   أ. انقر **فوق** بدء، وا **اكتب cmd**، ثم اضغط على **Enter**.

   ب. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي، ثم اضغط على **Enter**:

   ```console
   sc config diagtrack start=auto
   ```

3. يتم عرض رسالة نجاح. تحقق من التغيير بإدخال الأمر التالي، ثم اضغط على **Enter**:

   ```console
   sc qc diagtrack
   ```

4. ابدأ الخدمة. في موجه الأوامر، اكتب الأمر التالي واضغط على **Enter**:

   ```console
   sc start diagtrack
   ```

### <a name="ensure-the-device-has-an-internet-connection"></a>التأكد من أن الجهاز لديه اتصال بالإنترنت

يتطلب Microsoft Defender لنقطة النهاية المستشعر من Microsoft Windows HTTP (WinHTTP) الإبلاغ عن بيانات المستشعر والتواصل مع Microsoft Defender لنقطة النهاية الخدمة.

إن WinHTTP مستقل عن إعدادات وكيل استعراض الإنترنت وتطبيقات سياق المستخدم الأخرى ويجب أن يكون قادرا على الكشف عن خوادم الوكيل المتوفرة في بيئتك الخاصة.

للتأكد من أن المستشعر لديه اتصال الخدمة، اتبع الخطوات الموضحة في الموضوع التحقق من اتصال العميل [Microsoft Defender لنقطة النهاية URL للخدمة](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls).

إذا فشلت عملية التحقق وكانت بيئتك تستخدم وكيلا للاتصال بالإنترنت، فاتبع الخطوات الموضحة في الموضوع تكوين الوكيل وإعدادات [اتصال الإنترنت.](configure-proxy-internet.md)

### <a name="ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy"></a>تأكد من برنامج الحماية من الفيروسات من Microsoft Defender معطل بواسطة نهج

> [!IMPORTANT]
> ينطبق ما يلي فقط على الأجهزة التي لم تتلق  تحديث أغسطس 2020 (الإصدار 4.18.2007.8) برنامج الحماية من الفيروسات من Microsoft Defender.
>
> يضمن التحديث عدم برنامج الحماية من الفيروسات من Microsoft Defender إيقاف تشغيل الأجهزة العميلة عبر نهج النظام.

**المشكلة**: لا Microsoft Defender لنقطة النهاية تشغيل خدمة البريد بعد الboarding.

**العرض**: اكتملت عملية التكهين بنجاح، ولكنك ترى الخطأ 577 أو الخطأ 1058 عند محاولة بدء الخدمة.

**الحل**: إذا كانت أجهزتك تعمل عميلا لمكافحة البرامج الضارة من جهة خارجية، فإن Microsoft Defender لنقطة النهاية يحتاج إلى تمكين برنامج تشغيل برنامج تشغيل مبكر لمكافحة البرامج الضارة (ELAM). يجب أن تضمن عدم إيقاف تشغيله بواسطة نهج النظام.

- استنادا إلى الأداة التي تستخدمها لتنفيذ سياسات، ستحتاج إلى التحقق من مسح Windows Defender التالية:

  - DisableAntiSpyware
  - DisableAntiVirus

  على سبيل المثال، في نهج المجموعة يجب عدم وجود إدخالات مثل القيم التالية:

  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiSpyware"/></Key>`
  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiVirus"/></Key>`

> [!IMPORTANT]
> تم `disableAntiSpyware` إيقاف الإعداد وسوف يتم تجاهله على جميع أجهزة Windows 10، حتى تحديث أغسطس 2020 (الإصدار 4.18.2007.8) برنامج الحماية من الفيروسات من Microsoft Defender.

- بعد مسح النهج، ادير خطوات التكهين مرة أخرى.

- يمكنك أيضا التحقق من قيم مفتاح التسجيل السابقة للتحقق من تعطيل النهج، عن طريق فتح مفتاح التسجيل `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

  :::image type="content" source="images/atp-disableantispyware-regkey.png" alt-text="مفتاح التسجيل برنامج الحماية من الفيروسات من Microsoft Defender" lightbox="images/atp-disableantispyware-regkey.png":::

   > [!NOTE]
   > يجب Windows خدمات Defender (wdboot و wdfilter و wdnisdrv و wdnissvc و windefend) في حالتها الافتراضية. إن تغيير بدء تشغيل هذه الخدمات غير معتمد وقد يجبرك على إعادة إدارة النظام.
   >
   > مثال على التكوينات الافتراضية ل WdBoot و WdFilter:
   >
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdBoot"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdFilter"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`

## <a name="troubleshoot-onboarding-issues"></a>استكشاف مشاكل الحافظة وإصلاحها 

> [!NOTE]
> لا تنطبق إرشادات استكشاف الأخطاء وإصلاحها التالية إلا على Windows Server 2016 والمستويات الأقل.

إذا واجهت مشاكل أثناء تشغيل خادم، فاستعرض خطوات التحقق التالية لمعالجة المشاكل المحتملة.


- [تأكد من تثبيت Microsoft Monitoring Agent (MMA) وتكوينه لتقارير بيانات المستشعر للخدمة](configure-server-endpoints.md)
- [تأكد من تكوين إعدادات اتصال الإنترنت ووكيل الخادم بشكل صحيح](configure-server-endpoints.md)

قد تحتاج أيضا إلى التحقق مما يلي:

- تحقق من وجود خدمة Microsoft Defender لنقطة النهاية قيد التشغيل في علامة **التبويب** عمليات في **إدارة المهام**. على سبيل المثال:

  :::image type="content" source="images/atp-task-manager.png" alt-text="طريقة عرض العملية مع Microsoft Defender لنقطة النهاية قيد التشغيل" lightbox="images/atp-task-manager.png":::

- تحقق **عارض الأحداث** \> **إدارة** \> عمليات سجلات الخدمات والتطبيقات لمعرفة ما إذا كان هناك أي أخطاء.

- في **الخدمات**، تحقق مما إذا كان **وكيل مراقبة Microsoft** قيد التشغيل على الخادم. على سبيل المثال

  :::image type="content" source="images/atp-services.png" alt-text="الخدمات" lightbox="images/atp-services.png":::

- في **Microsoft Monitoring Agent** \> **Azure Log Analytics (OMS)،** تحقق من مساحات العمل وتحقق من تشغيل الحالة.

  :::image type="content" source="images/atp-mma-properties.png" alt-text="خصائص وكيل مراقبة Microsoft" lightbox="images/atp-mma-properties.png":::

- تحقق من أن الأجهزة تنعكس في قائمة **الأجهزة** في المدخل.

## <a name="confirming-onboarding-of-newly-built-devices"></a>تأكيد الدمج في الأجهزة التي تم إنشاؤها حديثا

قد تكون هناك مثيلات عند نشر الدمج على جهاز تم إنشاؤه حديثا ولكن لم يتم إكماله.

توفر الخطوات أدناه إرشادات حول السيناريو التالي:

- تم نشر حزمة الدمج على الأجهزة التي تم إنشاؤها حديثا
- لا يبدأ المستشعر بسبب عدم اكتمال تجربة تسجيل الخروج (OOBE) أو تسجيل المستخدم الأول
- يتم إيقاف تشغيل الجهاز أو إعادة تشغيله قبل أن يقوم المستخدم بإجراء تسجيل أول
- في هذا السيناريو، لن تبدأ خدمة SENSE تلقائيا على الرغم من نشر حزمة التكهين

> [!NOTE]
> لم يعد تسجيل مرور المستخدم بعد OOBE مطلوبا لبدء تشغيل خدمة SENSE في إصدارات Windows التالية أو الأحدث: الإصدار 1809 من Windows 10 أو Windows Server 2019 أو Windows Server 2022 مع تحديث [22 أبريل 2021](https://support.microsoft.com/kb/5001384). Windows 10، الإصدار 1909 مع [تحديث شهر أبريل 2021](https://support.microsoft.com/kb/5001396). Windows 10، الإصدار 2004/20H2 مع [مجموعة تحديثات 28 أبريل 2021](https://support.microsoft.com/kb/5001391). 


> [!NOTE]
> لا تكون الخطوات التالية ذات صلة إلا عند استخدام Microsoft Endpoint Configuration Manager. للحصول على مزيد من التفاصيل حول استخدام Microsoft Endpoint Configuration Manager[، راجع Microsoft Defender لنقطة النهاية](/mem/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection).

1. إنشاء تطبيق في Microsoft Endpoint Configuration Manager.

   :::image type="content" source="images/mecm-1.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-1" lightbox="images/mecm-1.png":::

2. حدد **تحديد معلومات التطبيق يدويا**.

   :::image type="content" source="images/mecm-2.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-2" lightbox="images/mecm-2.png":::

3. حدد معلومات حول التطبيق، ثم حدد **التالي**.

   :::image type="content" source="images/mecm-3.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-3" lightbox="images/mecm-3.png":::

4. حدد معلومات حول مركز البرامج، ثم حدد **التالي**.

   :::image type="content" source="images/mecm-4.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-4" lightbox="images/mecm-4.png":::

5. في **أنواع النشر،** حدد **إضافة**.

   :::image type="content" source="images/mecm-5.png" alt-text="تكوين Microsoft Endpoint Configuration Manager-5" lightbox="images/mecm-5.png":::

6. حدد **تحديد معلومات نوع النشر يدويا**، ثم حدد **التالي**.

   :::image type="content" source="images/mecm-6.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-6" lightbox="images/mecm-6.png":::

7. حدد معلومات حول نوع النشر، ثم حدد **التالي**.

   :::image type="content" source="images/mecm-7.png" alt-text="تكوين Microsoft Endpoint Configuration Manager-7" lightbox="images/mecm-7.png":::

8. في **برنامج** \> **تثبيت المحتوى** ، حدد الأمر: `net start sense`.

   :::image type="content" source="images/mecm-8.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-8" lightbox="images/mecm-8.png":::

9. في **أسلوب الكشف**، حدد **تكوين القواعد للكشف عن** وجود نوع النشر هذا، ثم حدد **إضافة عبارة**.

   :::image type="content" source="images/mecm-9.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-9" lightbox="images/mecm-9.png":::

10. حدد تفاصيل قاعدة الكشف التالية، ثم حدد **موافق**:

    :::image type="content" source="images/mecm-10.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 10" lightbox="images/mecm-10.png":::

11. في **طريقة الكشف،** حدد **التالي**.

    :::image type="content" source="images/mecm-11.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-11" lightbox="images/mecm-11.png":::

12. في **تجربة المستخدم**، حدد المعلومات التالية، ثم حدد **التالي**:

    :::image type="content" source="images/mecm-12.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 12" lightbox="images/mecm-12.png":::

13. في **المتطلبات**، حدد **التالي**.

    :::image type="content" source="images/mecm-13.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 13" lightbox="images/mecm-13.png":::

14. في **التبعيات**، حدد **التالي**.

    :::image type="content" source="images/mecm-14.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 14" lightbox="images/mecm-14.png":::

15. في **الملخص،** حدد **التالي**.

    :::image type="content" source="images/mecm-15.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 15" lightbox="images/mecm-15.png":::

16. في **"الإكمال**"، حدد **إغلاق**.

    :::image type="content" source="images/mecm-16.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 16" lightbox="images/mecm-16.png":::

17. في **أنواع النشر**، حدد **التالي**.

    :::image type="content" source="images/mecm-17.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 17" lightbox="images/mecm-17.png":::

18. في **الملخص،** حدد **التالي**.

    :::image type="content" source="images/mecm-18.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 18" lightbox="images/mecm-18.png":::

    يتم عرض الحالة بعد ذلك: :::image type="content" source="images/mecm-19.png" alt-text="Microsoft Endpoint Configuration Manager-19" lightbox="images/mecm-19.png":::

19. في **"الإكمال**"، حدد **إغلاق**.

    :::image type="content" source="images/mecm-20.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 20" lightbox="images/mecm-20.png":::

20. يمكنك الآن نشر التطبيق بالنقر ب الماوس الأيمن فوق التطبيق وتحديد **نشر**.

    :::image type="content" source="images/mecm-21.png" alt-text="تكوين Microsoft Endpoint Configuration Manager-21" lightbox="images/mecm-21.png":::

21. بشكل **عام**، **حدد توزيع المحتوى تلقائيا للتبعيات** **واستعراض.**

    :::image type="content" source="images/mecm-22.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 22" lightbox="images/mecm-22.png":::

22. في **المحتوى** ، حدد **التالي**.

    :::image type="content" source="images/mecm-23.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 23" lightbox="images/mecm-23.png":::

23. في **إعدادات النشر،** حدد **التالي**.

    :::image type="content" source="images/mecm-24.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 24" lightbox="images/mecm-24.png":::

24. في **الجدولة****، حدد في أقرب وقت ممكن بعد الوقت المتوفر**، ثم حدد **التالي**.

    :::image type="content" source="images/mecm-25.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-25" lightbox="images/mecm-25.png":::

25. في **تجربة المستخدم،** حدد **إجراء التغييرات في الموعد النهائي أو أثناء نافذة الصيانة (يتطلب إعادة التشغيل)،** ثم حدد **التالي**.

    :::image type="content" source="images/mecm-26.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-26" lightbox="images/mecm-26.png":::

26. في **التنبيهات** ، حدد **التالي**.

    :::image type="content" source="images/mecm-27.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 27" lightbox="images/mecm-27.png":::

27. في **الملخص،** حدد **التالي**.

    :::image type="content" source="images/mecm-28.png" alt-text="تكوين Microsoft Endpoint Configuration Manager 28" lightbox="images/mecm-28.png":::
      

    يتم عرض الحالة بعد ذلك :::image type="content" source="images/mecm-29.png" alt-text="Microsoft Endpoint Configuration Manager تكوين-29" lightbox="images/mecm-29.png":::

28. في **"الإكمال**"، حدد **إغلاق**.

    :::image type="content" source="images/mecm-30.png" alt-text="الإعداد Microsoft Endpoint Configuration Manager-30" lightbox="images/mecm-30.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية](troubleshoot-mdatp.md)
- [الأجهزة المجهزة](onboard-configure.md)
- [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز](configure-proxy-internet.md)
