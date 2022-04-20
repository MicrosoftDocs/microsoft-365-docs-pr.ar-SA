---
title: حماية التطبيقات Office للمسؤولين
keywords: حماية التطبيق، والحماية، والعزل، والحاوية المعزولة، وعزل الأجهزة
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
description: احصل على أحدث ما في العزل المستند إلى الأجهزة. منع الهجمات الحالية والناشئة مثل المهاجمات أو الارتباطات الضارة من تعطيل إنتاجية الموظفين وأمان المؤسسة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 98d23a814ac2af8d9dedc4f163923e67c9ca7dc2
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973234"
---
# <a name="application-guard-for-office-for-admins"></a>حماية التطبيقات Office للمسؤولين

**ينطبق على:** Word و Excel و PowerPoint لـ Microsoft 365 و Windows 10 Enterprise و Windows 11 Enterprise

تساعد حماية التطبيقات من Microsoft Defender Office (حماية التطبيقات Office) على منع الملفات غير الموثوق بها من الوصول إلى الموارد الموثوق بها، ما يحافظ على أمان مؤسستك من الهجمات الجديدة والناشئة. ترشد هذه المقالة المسؤولين من خلال إعداد الأجهزة لمعاينة حماية التطبيقات Office. يوفر معلومات حول متطلبات النظام وخطوات التثبيت لتمكين حماية التطبيقات Office على جهاز.

## <a name="prerequisites"></a>المتطلبات الأساسية

### <a name="minimum-hardware-requirements"></a>الحد الأدنى لمتطلبات الأجهزة

* **CPU**: 64 بت، 4 نواة (فعلية أو ظاهرية)، ملحقات ظاهرية (Intel VT-x OR AMD-V)، مكافئ Core i5 أو أعلى مستحسن
* **الذاكرة الفعلية**: ذاكرة وصول عشوائي 8 غيغابايت
* **القرص الثابت**: 10 غيغابايت من المساحة الحرة على محرك أقراص النظام (يوصى باستخدام SSD)

### <a name="minimum-software-requirements"></a>الحد الأدنى لمتطلبات البرامج

* **Windows**: إصدار Windows 10 Enterprise، إصدار 2004 (20H1) من Client Build 19041 أو إصدار أحدث. جميع إصدارات Windows 11 مدعومة.
* **Office**: Office خيار التحديث الحالي وقناة المؤسسة الشهرية، النسخة 2011 16.0.13530.10000 أو الإصدارات الأحدث. Office Semi-Annual قناة المؤسسة، الإصدار 2108 أو الإصدارات الأحدث. يتم دعم كل من الإصدارين 32 بت و64 بت من Office.
* **حزمة التحديث**: Windows 10 تحديث الأمان الشهري التراكمي [KB4571756](https://support.microsoft.com/help/4571756/windows-10-update-KB4571756)

للحصول على متطلبات النظام التفصيلية، راجع [متطلبات النظام حماية التطبيقات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-application-guard/reqs-md-app-guard). يرجى أيضا الرجوع إلى إرشادات الشركة المصنعة للكمبيوتر حول كيفية تمكين تقنية الظاهرية.
لمعرفة المزيد حول قنوات تحديث Office، راجع [نظرة عامة على قنوات التحديث Microsoft 365](/deployoffice/overview-update-channels).

### <a name="licensing-requirements"></a>متطلبات الترخيص

* Microsoft 365 E5 أو الأمان في Microsoft 365 E5

> [!NOTE]
> Microsoft 365 Apps for enterprise مع تنشيط الكمبيوتر المشترك أو الترخيص المستند إلى الجهاز ليس لديه حق الوصول إلى Application Guard Office.

## <a name="deploy-application-guard-for-office"></a>نشر حماية التطبيقات Office

### <a name="enable-application-guard-for-office"></a>تمكين حماية التطبيقات Office

1. تنزيل **وتثبيت Windows 10 تحديثات الأمان الشهرية التراكمية KB4571756**.

2. حدد **حماية التطبيقات من Microsoft Defender** ضمن "ميزات Windows" وحدد **"موافق**". سيؤدي تمكين ميزة Application Guard إلى المطالبة بإعادة تشغيل النظام. يمكنك اختيار إعادة التشغيل الآن أو بعد الخطوة 3.

   :::image type="content" source="../../media/ag03-deploy.png" alt-text="يعرض مربع الحوار &quot;ميزات Windows&quot; AG" lightbox="../../media/ag03-deploy.png":::

   يمكن أيضا تمكين الميزة عن طريق تشغيل أمر PowerShell التالي كمسؤول:

   ```powershell
   Enable-WindowsOptionalFeature -online -FeatureName Windows-Defender-ApplicationGuard
   ```

3. ابحث عن **حماية التطبيقات من Microsoft Defender في الوضع المدار**، وهو نهج مجموعة في **Computer ConfigurationAdministrative\\ Templates\\ Windows Components\\ حماية التطبيقات من Microsoft Defender**. قم بتشغيل هذا النهج عن طريق تعيين القيمة ضمن "خيارات" ك **2** أو **3**، ثم تحديد **"موافق** " أو **"تطبيق**".

   :::image type="content" source="../../media/ag04-deploy.png" alt-text="خيار تشغيل AG في الوضع المدار" lightbox="../../media/ag04-deploy.png":::

   بدلا من ذلك، يمكنك تعيين نهج CSP المقابل:

   > OMA-URI: **./Device/Vendor/MSFT/WindowsDefenderApplicationGuard/الإعدادات/AllowWindowsDefenderApplicationGuard** <br> نوع البيانات: **عدد صحيح** <br> القيمة: **2**

4. أعد تشغيل النظام.

### <a name="set-diagnostics--feedback-to-send-full-data"></a>تعيين الملاحظات & التشخيصية لإرسال بيانات كاملة

> [!NOTE]
> هذا غير مطلوب، ومع ذلك، فإن تكوين بيانات التشخيص الاختيارية سيساعد في تشخيص المشكلات المبلغ عنها.

تضمن هذه الخطوة وصول البيانات اللازمة لتحديد المشاكل وإصلاحها إلى Microsoft. اتبع هذه الخطوات لتمكين التشخيصات على جهازك Windows:

1. افتح **الإعدادات** من قائمة البدء.

   :::image type="content" source="../../media/ag05-diagnostic.png" alt-text="قائمة البدء" lightbox="../../media/ag05-diagnostic.png":::

2. **في Windows الإعدادات**، حدد **الخصوصية**.

   :::image type="content" source="../../media/ag06-diagnostic.png" alt-text="قائمة Windows الإعدادات" lightbox="../../media/ag06-diagnostic.png":::

3. ضمن الخصوصية، حدد **التشخيصات & الملاحظات** وحدد **البيانات التشخيصية الاختيارية**.

   :::image type="content" source="../../media/ag07a-diagnostic.png" alt-text="قائمة التشخيصات والملاحظات" lightbox="../../media/ag07a-diagnostic.png":::

لمزيد من التفاصيل حول تكوين إعدادات التشخيص Windows، راجع [تكوين البيانات التشخيصية Windows في مؤسستك](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enterprise-management).

### <a name="confirm-that-application-guard-for-office-is-enabled-and-working"></a>تأكد من تمكين Application Guard ل Office والعمل

قبل التأكد من تمكين "حماية التطبيقات" Office، قم بتشغيل Word أو Excel أو PowerPoint على جهاز تم نشر النهج فيه. تأكد من تنشيط Office. قد تحتاج إلى استخدام هوية العمل لتنشيط منتج Office أولا.

لتأكيد تمكين "حماية التطبيقات" Office، قم بتشغيل Word أو Excel أو PowerPoint، ثم افتح مستندا غير موثوق به. على سبيل المثال، يمكنك فتح مستند تم تنزيله من الإنترنت أو مرفق بريد إلكتروني من شخص من خارج مؤسستك.

عند فتح ملف غير موثوق به لأول مرة، قد ترى شاشة بداية Office مثل المثال التالي. قد يتم عرضه لبعض الوقت أثناء تنشيط Application Guard Office ويتم فتح الملف. يجب أن تكون عمليات الفتح اللاحقة للملفات غير الموثوق بها أسرع.

:::image type="content" source="../../media/ag08-confirm.png" alt-text="صفحة البداية تطبيق Office" lightbox="../../media/ag08-confirm.png":::

عند فتحه، يجب أن يعرض الملف بعض المؤشرات المرئية التي تفيد بأنه تم فتح الملف داخل Application Guard Office:

* وسيلة شرح في الشريط

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="ملف المستند يعرض ملاحظة &quot;حماية التطبيقات&quot; الصغيرة" lightbox="../../media/ag09-confirm.png":::

* أيقونة التطبيق مع درع في شريط المهام

  ![أيقونة في شريط المهام.](../../media/ag12-limitations.png)

## <a name="configure-application-guard-for-office"></a>تكوين حماية التطبيقات Office

يدعم Office النهج التالية لتمكينك من تكوين قدرات Application Guard Office. يمكن تكوين هذه النهج من خلال نهج المجموعة أو من خلال [خدمة نهج السحابة Office](/DeployOffice/overview-office-cloud-policy-service).

> [!NOTE]
> يمكن أن يؤدي تكوين هذه النهج إلى تعطيل بعض الوظائف للملفات المفتوحة في Application Guard Office.

|السياسات|الوصف|
|---|---|
|لا تستخدم Application Guard Office|سيؤدي تمكين هذا النهج إلى فرض استخدام حاوية عزل "طريقة عرض محمية" بدلا من "حماية التطبيقات" Office على Word و Excel PowerPoint. يمكن استخدام هذا النهج لتعطيل Application Guard مؤقتا Office عند وجود مشاكل في تركه ممكنا Microsoft Edge.|
|تكوين حماية التطبيقات لحاوية Office ما قبل الإنشاء|يحدد هذا النهج ما إذا تم إنشاء Application Guard لحاوية Office، لعزل الملفات غير الموثوق بها، مسبقا لتحسين أداء وقت التشغيل. إذا قمت بتمكين هذا الإعداد، يمكنك تحديد عدد الأيام لمتابعة إنشاء حاوية مسبقا أو السماح Office إنشاء الحاوية مسبقا.
|عدم السماح بالنسخ/اللصق لمستندات Office المفتوحة في "حماية التطبيقات" Office|سيؤدي تمكين هذا النهج إلى منع المستخدم من نسخ المحتوى ولصقه من مستند تم فتحه في "حماية التطبيقات" Office إلى مستند مفتوح خارجه.|
|تعطيل تسريع الأجهزة في حماية التطبيقات Office|يتحكم هذا النهج في ما إذا كان Application Guard ل Office يستخدم تسريع الأجهزة لعرض الرسومات. إذا قمت بتمكين هذا الإعداد، فإن Application Guard for Office يستخدم العرض المستند إلى البرامج (CPU) ولن يقوم بتحميل أي برامج تشغيل رسومات تابعة لجهة خارجية أو التفاعل مع أي أجهزة رسومات متصلة.
|تعطيل حماية أنواع الملفات غير المعتمدة في حماية التطبيقات Office|يتحكم هذا النهج في ما إذا كان "حماية التطبيقات" ل Office سيمنع فتح أنواع الملفات غير المعتمدة أو إذا كان سيؤدي إلى تمكين إعادة التوجيه إلى "طريقة عرض محمية".
|إيقاف تشغيل الوصول إلى الكاميرا والميكروفون للمستندات المفتوحة في "حماية التطبيقات" Office|سيؤدي تمكين هذا النهج إلى إزالة الوصول Office إلى الكاميرا والميكروفون داخل Application Guard Office.|
|تقييد الطباعة من المستندات المفتوحة في Application Guard Office|سيؤدي تمكين هذا النهج إلى تقييد الطابعات التي يمكن للمستخدم طباعتها من ملف تم فتحه في Application Guard Office. على سبيل المثال، يمكنك استخدام هذا النهج لتقييد المستخدمين بالطباعة إلى PDF فقط.|
|منع المستخدمين من إزالة حماية التطبيقات لحماية Office على الملفات|سيؤدي تمكين هذا النهج إلى إزالة الخيار (ضمن تجربة تطبيق Office) لتعطيل حماية التطبيق لحماية Office أو لفتح ملف خارج Application Guard Office. <p> **ملاحظه:** لا يزال بإمكان المستخدمين تجاوز هذا النهج عن طريق إزالة خاصية وضع علامة ويب من الملف يدويا أو عن طريق نقل مستند إلى موقع موثوق به.|

> [!NOTE]
> ستتطلب النهج التالية من المستخدم تسجيل الخروج وتسجيل الدخول مرة أخرى Windows لكي يدخل حيز التنفيذ:
>
> * تعطيل النسخ/اللصق للمستندات المفتوحة في "حماية التطبيقات" Office
> * تقييد طباعة المستندات المفتوحة في "حماية التطبيقات" Office
> * إيقاف تشغيل وصول الكاميرا والميكروفون إلى المستندات التي تم فتحها في "حماية التطبيقات" Office

## <a name="submit-feedback"></a>إرسال الملاحظات

### <a name="submit-feedback-via-feedback-hub"></a>إرسال الملاحظات عبر مركز تقديم الملاحظات

إذا واجهت أي مشاكل عند بدء تشغيل Application Guard Office، يتم تشجيعك على إرسال ملاحظاتك عبر مركز تقديم الملاحظات:

1. افتح **تطبيق مركز تقديم الملاحظات** وسجل الدخول.

2. إذا تلقيت مربع حوار خطأ أثناء تشغيل Application Guard، فحدد **"تقرير إلى Microsoft** " في مربع حوار الخطأ لبدء إرسال ملاحظات جديدة. بخلاف ذلك، انتقل إلى <https://aka.ms/mdagoffice-fb> تحديد الفئة الصحيحة ل Application Guard، ثم حدد **+&nbsp;إضافة ملاحظات جديدة** بالقرب من أعلى اليمين.

3. أدخل ملخصا في المربع **"تلخيص ملاحظاتك** " إذا لم يتم ملؤه بالفعل لك.

4. أدخل وصفا مفصلا للمشكلة التي واجهتك والخطوات التي اتخذتها **في المربع "شرح بمزيد من التفاصيل** "، ثم حدد **"التالي**".

5. حدد الفقاعة بجانب **المشكلة**. تأكد من أن الفئة المحددة هي **حماية التطبيقات من Microsoft Defender الأمان والخصوصية \> – Office**، ثم حدد **"التالي**".

6. حدد **ملاحظات جديدة**، ثم **"التالي**".

7. جمع التتبعات حول المشكلة:

   1. قم بتوسيع لوحة **إعادة إنشاء المشكلة** .

   2. إذا حدثت المشكلة التي تواجهها أثناء تشغيل Application Guard، فافتح مثيل Application Guard. يسمح فتح مثيل بتجميع تتبعات إضافية من داخل حاوية Application Guard.

   3. حدد **"بدء التسجيل**"، وانتظر حتى تتوقف اللوحة عن الدوران وقل *"إيقاف التسجيل*".

   4. إعادة إنتاج المشكلة بالكامل باستخدام Application Guard. قد يتضمن النسخ محاولة تشغيل مثيل Application Guard والانتظار حتى يفشل، أو إعادة إنتاج مشكلة في مثيل Application Guard قيد التشغيل.

   5. حدد لوحة **إيقاف التسجيل** .

   6. احتفظ بأي مثيل (مثيلات) حماية التطبيقات قيد التشغيل مفتوحة، حتى بعد بضع دقائق من الإرسال، بحيث يمكن أيضا جمع تشخيصات الحاوية.

8. إرفاق أي لقطات شاشة أو ملفات ذات صلة بالمشكلة.

9. حدد **"إرسال**".

### <a name="submit-feedback-via-office-customer-voice"></a>إرسال الملاحظات عبر Office Customer Voice

يمكنك أيضا إرسال ملاحظات من داخل Office إذا حدثت المشكلة عند فتح مستندات Office في Application Guard. راجع [دليل insider Office](https://insider.office.com/handbook) لإرسال الملاحظات.

## <a name="integration-with-microsoft-defender-for-endpoint-and-microsoft-defender-for-office-365"></a>التكامل مع Microsoft Defender لنقطة النهاية Microsoft Defender لـ Office 365

يتم دمج حماية التطبيقات Office مع Microsoft Defender لنقطة النهاية لتوفير المراقبة والتنبيه إلى النشاط الضار الذي يحدث في البيئة المعزولة.

[خزينة المستندات في Microsoft E365 E5](/microsoft-365/security/office-365-security/safe-docs) هي ميزة تستخدم Microsoft Defender لنقطة النهاية لمسح المستندات المفتوحة في Application Guard بحثا عن Office. للحصول على طبقة حماية إضافية، لا يمكن للمستخدمين مغادرة Application Guard Office حتى يتم تحديد نتائج الفحص.

Microsoft Defender لنقطة النهاية هو نظام أساسي للأمان مصمم لمساعدة شبكات المؤسسة على منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها. لمزيد من التفاصيل حول هذا النظام الأساسي، راجع [Microsoft Defender لنقطة النهاية](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp). لمعرفة المزيد حول إلحاق الأجهزة بهذا النظام الأساسي، راجع [إلحاق الأجهزة بخدمة Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/onboard-configure).

يمكنك أيضا تكوين Microsoft Defender لـ Office 365 للعمل مع Defender لنقطة النهاية. لمزيد من المعلومات، راجع [دمج Defender لـ Office 365 مع Microsoft Defender لنقطة النهاية](integrate-office-365-ti-with-mde.md).

## <a name="limitations-and-considerations"></a>القيود والاعتبارات

* حماية التطبيقات Office هو وضع محمي يعزل المستندات غير الموثوق بها بحيث لا يمكنهم الوصول إلى موارد الشركة الموثوق بها والإنترانت وهوية المستخدم والملفات العشوائية على الكمبيوتر. ونتيجة لذلك، إذا حاول مستخدم الوصول إلى ميزة لها تبعية على هذا الوصول، مثل إدراج صورة من ملف محلي على القرص، فسيفشل الوصول وينتج مطالبة تشبه المثال التالي. لتمكين مستند غير موثوق به للوصول إلى الموارد الموثوق بها، يجب على المستخدمين إزالة حماية Application Guard من المستند.

  :::image type="content" source="../../media/ag09-confirm.png" alt-text="مربع الحوار الذي يوضح رسالة الأمان وحالة الميزة" lightbox="../../media/ag09-confirm.png":::

  > [!NOTE]
  > ننصح المستخدمين بإزالة الحماية فقط إذا كانوا يثقون بالملف ومصدره أو من أين جاء.

* عندما يتم تخزين مستند غير موثوق به في موقع موثوق به، يتم توريث الثقة من الموقع بواسطة المستند. عادة ما يتم تعريف التخزين السحابي للمؤسسة كموقع موثوق به.

* يتم تعطيل المحتوى النشط في المستندات مثل وحدات الماكرو وعناصر تحكم ActiveX في Application Guard Office. يحتاج المستخدمون إلى إزالة حماية Application Guard لتمكين المحتوى النشط.

* يتم فتح الملفات غير الموثوق بها من مشاركات الشبكة أو الملفات المشتركة من OneDrive أو OneDrive for Business أو SharePoint Online من مؤسسة مختلفة للقراءة فقط في Application Guard. يمكن للمستخدمين حفظ نسخة محلية من هذه الملفات لمواصلة العمل في الحاوية أو إزالة الحماية للعمل مباشرة مع الملف الأصلي.

* يتم حظر الملفات المحمية بواسطة إدارة حقوق المعلومات (IRM) بشكل افتراضي. إذا أراد المستخدمون فتح مثل هذه الملفات في "طريقة عرض محمية"، فيجب على المسؤول تكوين إعدادات النهج لأنواع الملفات غير المعتمدة للمؤسسة.

* لن تستمر أي تخصيصات لتطبيقات Office في Application Guard ل Office بعد تسجيل خروج المستخدم وتسجيل الدخول مرة أخرى أو بعد إعادة تشغيل الجهاز.

* يمكن فقط لأدوات إمكانية وصول ذوي الاحتياجات الخاصة التي تستخدم إطار عمل UIA توفير تجربة يمكن الوصول إليها للملفات المفتوحة في Application Guard Office.

* الاتصال بالشبكة مطلوب للتشغيل الأول ل Application Guard بعد التثبيت. الاتصال مطلوب ل Application Guard للتحقق من صحة الترخيص.

* في قسم معلومات المستند، قد تعرض الخاصية *"التعديل الأخير بواسطة***" WDAGUtilityAccount** كمستخدم. WDAGUtilityAccount هو المستخدم المجهول الذي تم تكوينه في Application Guard. لا تتم مشاركة هوية مستخدم سطح المكتب داخل حاوية Application Guard.

## <a name="performance-optimizations-for-application-guard-for-office"></a>تحسينات الأداء ل Application Guard ل Office

يقدم هذا القسم نظرة عامة على تحسينات الأداء المستخدمة في حماية التطبيقات Office. يمكن أن تساعد هذه المعلومات المسؤولين على تشخيص التقارير من المستخدمين المتعلقة بأداء Office أو النظام العام عند تمكين Application Guard.

يستخدم Application Guard حاوية ظاهرية لعزل المستندات غير الموثوق بها بعيدا عن النظام. عملية إنشاء حاوية وإعداد حاوية Application Guard لفتح مستندات Office لها حمل أداء قد يؤثر سلبا على تجربة المستخدم عندما يفتح المستخدمون مستندا غير موثوق به.

لتزويد المستخدمين بتجربة فتح الملفات المتوقعة، يستخدم Application Guard المنطق لإنشاء حاوية مسبقا عند استيفاء الاستعداد التالي على نظام: قام مستخدم بفتح ملف إما في "طريقة عرض محمية" أو "حماية التطبيقات" في آخر 28 يوما.

عند استيفاء هذا الاستعداد، سيقوم Office بإنشاء حاوية Application Guard للمستخدم مسبقا بعد تسجيل الدخول إلى Windows. في حين أن عملية الإنشاء المسبق هذه قيد التقدم، قد يواجه النظام أداء بطيئا، ولكن سيتم حل التأثير بمجرد اكتمال العملية.

> [!NOTE]
> يتم إنشاء التلميحات اللازمة لإجراء الاستعداد لإنشاء الحاوية مسبقا بواسطة تطبيقات Office حيث يستخدمها المستخدم. إذا قام مستخدم بتثبيت Office على نظام جديد حيث تم تمكين Application Guard، فلن Office إنشاء الحاوية مسبقا إلا بعد المرة الأولى التي يفتح فيها المستخدم مستندا غير موثوق به على النظام. سيلاحظ المستخدم أن هذا الملف الأول يستغرق وقتا أطول لفتحه في Application Guard.

## <a name="known-issues"></a>المشاكل المعروفة

* لا يؤدي تحديد ارتباطات ويب (`http` أو `https`) إلى فتح المستعرض.
* الإعداد الافتراضي لنهج حماية النسخ واللصق هو تمكين وصول الحافظة إلى النص فقط.
* الإعداد الافتراضي لنهج حماية أنواع الملفات غير المعتمدة هو حظر فتح أنواع الملفات غير المعتمدة غير الموثوق بها المشفرة أو التي تم تعيين إدارة حقوق استخدام المعلومات (IRM) لها. يتضمن ذلك الملفات المشفرة باستخدام تسميات الحساسية من Microsoft Purview حماية البيانات.
* ملفات CSV و HTML غير معتمدة حاليا.
* لا يعمل Application Guard ل Office حاليا مع وحدات التخزين المضغوطة NTFS. إذا كنت ترى خطأ "ERROR_VIRTUAL_DISK_LIMITATION" يرجى محاولة إلغاء ضغط وحدة التخزين.
* قد تؤدي التحديثات إلى .NET إلى فشل فتح الملفات في Application Guard. كحل بديل، يمكن للمستخدمين إعادة تشغيل جهازهم عند حدوث هذا الفشل. تعرف على المزيد حول المشكلة في [تلقي رسالة خطأ عند محاولة فتح حماية التطبيقات لـ Windows Defender أو بيئة الاختبار المعزولة في Windows](https://support.microsoft.com/help/4575917/receiving-an-error-message-when-attempting-to-open-windows-defender-ap).
* الرجاء الاطلاع [على الأسئلة المتداولة - حماية التطبيقات من Microsoft Defender للحصول على معلومات إضافية.](/windows/security/threat-protection/microsoft-defender-application-guard/faq-md-app-guard)
