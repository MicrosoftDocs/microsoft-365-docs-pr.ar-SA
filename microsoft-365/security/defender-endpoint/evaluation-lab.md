---
title: Microsoft Defender لنقطة النهاية التقييم
description: تعرف على Microsoft Defender لنقطة النهاية، وتشغيل عمليات محاكاة الهجمات، وتعرف على كيفية منع التهديدات والكشف عنها وكيفية إصلاحها.
keywords: تقييم Microsoft Defender لنقطة النهاية والتقييم والمختبر والمحاكاة و windows 10 و windows server 2019 ومعمل التقييم
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.prod: m365-security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2b4c1cd9c37921fbb54633c0fc1bf2e42d308081
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472870"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>Microsoft Defender لنقطة النهاية التقييم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

قد يكون إجراء تقييم شامل لمنتج الأمان عملية معقدة تتطلب بيئة مرهقة وتكوين جهاز قبل إجراء محاكاة هجوم شامل. ويضاف إلى التعقيد تحدي تعقب مكان انعكاس أنشطة المحاكاة والتنبيهات والنتائج أثناء التقييم.

تم تصميم Microsoft Defender لنقطة النهاية تقييم البيانات لإزالة تعقيدات تكوين الجهاز والبيئة بحيث يمكنك التركيز على تقييم إمكانات النظام الأساسي وتشغيل عمليات المحاكاة ورؤية ميزات منع الفيروسات والكشف عنها وميزات المعالجة قيد التنفيذ.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

باستخدام تجربة الإعداد المبسطة، يمكنك التركيز على تشغيل سيناريوهات الاختبار الخاصة بك و عمليات المحاكاة التي تم إعدادها مسبقا لمعرفة كيفية أداء Defender for Endpoint.

سيكون لديك حق الوصول الكامل إلى الإمكانات القوية في النظام الأساسي مثل الاختبارات التلقائية والصيد المتقدم وتحليلات التهديدات، مما يسمح لك باختبار مكدس الحماية الشامل الذي يقدمه Defender for Endpoint.

يمكنك إضافة أجهزة Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2016 و Linux (Ubuntu) التي تم تكوينها مسبقا لكي يتم تثبيت أحدث إصدارات نظام التشغيل ومكونات الأمان الصحيحة بالإضافة إلى Office 2019 Standard.

يمكنك أيضا تثبيت محاكي التهديدات. لقد عمل Defender for Endpoint على شراكة مع الأنظمة الأساسية الرائدة لمحاكاة المخاطر في المجال لمساعدتك على اختبار قدرات Defender for Endpoint دون الحاجة إلى مغادرة المدخل.

قم بتثبيت المحاكي المفضل لديك، وسيناريوهات التشغيل داخل معمل التقييم، وشاهد على الفور كيفية أداء النظام الأساسي - كل ذلك متوفر بسهولة دون أي تكلفة إضافية بالنسبة لك. سيكون لديك أيضا وصول ملائم إلى مجموعة واسعة من عمليات المحاكاة التي يمكنك الوصول إليها وتشغيلها من كتالوج عمليات المحاكاة.

## <a name="before-you-begin"></a>قبل البدء

ستحتاج إلى تلبية [متطلبات الترخيص](minimum-requirements.md#licensing-requirements) أو الحصول على حق الوصول التجريبي Microsoft Defender لنقطة النهاية الوصول إلى معمل التقييم.

يجب أن يكون **لديك أذونات إدارة إعدادات الأمان** من أجل:

- إنشاء المعمل
- إنشاء أجهزة
- إعادة تعيين كلمة المرور
- إنشاء عمليات محاكاة

إذا قمت بتمكين التحكم بالوصول المستند إلى الدور (RBAC) وأنشئت مجموعة جهاز واحدة على الأقل، فيجب أن يكون لدى المستخدمين حق الوصول إلى كافة مجموعات الجهاز.

لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md).

هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>بدء العمل في المعمل

يمكنك الوصول إلى المعمل من القائمة. في قائمة التنقل، حدد **التقييم والبرامج التعليمية > التقييم**.

> [!NOTE]
>
> - استنادا إلى نوع بنية البيئة التي تحددها، ستتوفر الأجهزة لعدد الساعات المحدد من يوم التنشيط.
> - يتم توفير كل بيئة مع مجموعة محدودة من أجهزة الاختبار. عند استخدام الأجهزة التي تم توفيرها وحذفها، يمكنك طلب المزيد من الأجهزة.
> - يمكنك طلب موارد المعمل مرة كل شهر.

هل لديك معمل بالفعل؟ تأكد من تمكين محاكي التهديدات الجديدة وأن يكون لديك أجهزة نشطة.

## <a name="setup-the-evaluation-lab"></a>إعداد معمل التقييم

1. في جزء التنقل، حدد تقييم & **التعليمية** \> معمل **التقييم، ثم** حدد **إعداد المعمل**.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="صفحة الترحيب في معمل التقييم" lightbox="../../media/evaluationtutormenu.png":::

2. استنادا إلى احتياجات التقييم، يمكنك اختيار إعداد بيئة ذات أجهزة أقل لفترة أطول أو أكثر لفترة زمنية أقصر. حدد تكوين المعمل المفضل لديك ثم حدد **التالي**.

    :::image type="content" source="images/lab-creation-page.png" alt-text="خيارات تكوين المعمل" lightbox="images/lab-creation-page.png":::

3. (اختياري) يمكنك اختيار تثبيت محاكي التهديدات في المعمل.

    :::image type="content" source="images/install-agent.png" alt-text="صفحة وكيل محاكي التثبيت" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > ستحتاج أولا إلى قبول الشروط وبيانات مشاركة المعلومات وتقديم الموافقة عليها.

4. حدد وكيل محاكاة التهديدات الذي تريد استخدامه وأدخل التفاصيل الخاصة بك. يمكنك أيضا اختيار تثبيت محاكي التهديدات في وقت لاحق. إذا اخترت تثبيت وكلاء محاكاة التهديدات أثناء إعداد المعمل، فسوف تستمتع بستفيدية تثبيتهم بسهولة على الأجهزة التي تضيفها.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="صفحة الملخص" lightbox="images/lab-setup-summary.png":::

5. راجع الملخص وحدد **معمل الإعداد**.

بعد اكتمال عملية إعداد المعمل، يمكنك إضافة أجهزة وتشغيل عمليات محاكاة.

## <a name="add-devices"></a>إضافة أجهزة

عند إضافة جهاز إلى بيئتك، يعمل Defender for Endpoint على إعداد جهاز تم تكوينه بشكل جيد مع تفاصيل الاتصال. يمكنك إضافة Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2016 و Linux (Ubuntu).

سيتم تكوين الجهاز باستخدام أحدث إصدار من نظام التشغيل وsysIntenals Office 2019 بالإضافة إلى تطبيقات أخرى مثل Java وYython وSysIntenals.

إذا اخترت إضافة محاكي تهديدات أثناء إعداد المعمل، فإن كل الأجهزة ستثبت عامل محاكي التهديدات في الأجهزة التي تضيفها.

سيتم تلقائيا تشغيل الجهاز للمستأجر مع Windows الموصى بها ومكونات الأمان في وضع التدقيق - بدون أي جهد من جانبك.

تم تكوين مكونات الأمان التالية مسبقا في أجهزة الاختبار:

- [الحد من سطح الهجوم](attack-surface-reduction.md)
- [الحظر من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [الوصول إلى المجلدات الخاضعة للتحكم](controlled-folders.md)
- [الحماية من استغلال](enable-exploit-protection.md)
- [حماية الشبكة](network-protection.md)
- [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [الحماية التي يتم تسليمها من السحابة](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> برنامج الحماية من الفيروسات من Microsoft Defender تشغيل (ليس في وضع التدقيق). إذا برنامج الحماية من الفيروسات من Microsoft Defender تشغيل المحاكاة، يمكنك إيقاف تشغيل الحماية في الوقت الحقيقي على الجهاز من خلال أمن Windows. لمزيد من المعلومات، راجع [تكوين الحماية دائما](configure-real-time-protection-microsoft-defender-antivirus.md).

ستعتمد إعدادات التحقيق التلقائي على إعدادات المستأجر. سيتم تكوينها لتكون شبه تلقائية بشكل افتراضي. لمزيد من المعلومات، راجع [نظرة عامة حول عمليات البحث التلقائية](automated-investigations.md).

> [!NOTE]
> يتم الاتصال بأجهزة الاختبار باستخدام RDP. تأكد من أن إعدادات جدار الحماية تسمح باتصالات RDP.

1. من لوحة المعلومات، حدد **إضافة جهاز**.

2. اختر نوع الجهاز الذي تريد إضافته. يمكنك اختيار إضافة Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2016 و Linux (Ubuntu).

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="إعداد المعمل مع خيارات الجهاز" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > إذا حدث خطأ ما في عملية إنشاء الجهاز، سيتم إعلامك وستحتاج إلى إرسال طلب جديد. إذا فشل إنشاء الجهاز، لن يتم حسابه مقابل الحصة النسبية الإجمالية المسموح بها.

3. يتم عرض تفاصيل الاتصال. حدد **نسخ** لحفظ كلمة المرور للجهاز.

   > [!NOTE]
   > يتم عرض كلمة المرور مرة واحدة فقط. تأكد من حفظه لاستخدامه لاحقا.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="الجهاز الذي تم إضافته مع تفاصيل الاتصال" lightbox="../../media/add-machine-eval-lab-new.png":::

4. يبدأ إعداد الجهاز. قد يستغرق ذلك ما يصل إلى 30 دقيقة تقريبا.

5. راجع حالة أجهزة الاختبار، ومستويات المخاطر والتعرض للضوء، حالة عمليات تثبيت المحاكي من خلال تحديد علامة **التبويب** الأجهزة.

   :::image type="content" source="images/machines-tab.png" alt-text="علامة تبويب الأجهزة" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > في عمود **حالة المحاكي** ، يمكنك مرر فوق أيقونة المعلومات لمعرفة حالة تثبيت عامل.


## <a name="request-for-more-devices"></a>طلب المزيد من الأجهزة

عند استخدام جميع الأجهزة الموجودة وحذفها، يمكنك طلب المزيد من الأجهزة. يمكنك طلب موارد المعمل مرة كل شهر.

1. من لوحة معلومات معمل التقييم، حدد **طلب المزيد من الأجهزة**.

   :::image type="content" source="images/request-more-devices.png" alt-text="خيار طلب المزيد من الأجهزة" lightbox="images/request-more-devices.png":::

2. اختر التكوين الخاص بك.
3. أرسل الطلب.

عند إرسال الطلب بنجاح، سترى شعار تأكيد أخضر وتاريخ الإرسال الأخير.

يمكنك العثور على حالة طلبك في علامة التبويب إجراءات المستخدم، التي سيتم اعتمادها في غضون ساعات.

عند الموافقة، تضاف الأجهزة المطلوبة إلى إعداد المعمل وستتمكن من إنشاء المزيد من الأجهزة.

> [!TIP]
> للحصول على المزيد من المعمل، لا تنس الاطلاع على مكتبة عمليات المحاكاة.

## <a name="simulate-attack-scenarios"></a>محاكاة سيناريوهات الهجوم

استخدم أجهزة الاختبار لتشغيل عمليات محاكاة الهجمات الخاصة بك من خلال الاتصال بها.

يمكنك محاكاة سيناريوهات الهجمات باستخدام:

- [سيناريوهات الهجوم "القيام بذلك بنفسك"](https://security.microsoft.com/tutorials/all)
- محاكي التهديدات

يمكنك أيضا استخدام [البحث المتقدم](advanced-hunting-overview.md) للاستعلام عن البيانات وتحليلات [](threat-analytics.md) التهديدات لعرض تقارير حول التهديدات الناشئة.

### <a name="do-it-yourself-attack-scenarios"></a>سيناريوهات الهجوم بنفسك

إذا كنت تبحث عن محاكاة مسبقة الإعداد، يمكنك استخدام سيناريوهات هجوم ["القيام بذلك بنفسك](https://security.microsoft.com/tutorials/all)". هذه البرامج النصية آمنة وموثقة وسهلة الاستخدام. ستعكس هذه السيناريوهات قدرات Defender لنقطة النهاية وتحرك خلال تجربة التحقيق.

> [!NOTE]
> يتم الاتصال بأجهزة الاختبار باستخدام RDP. تأكد من أن إعدادات جدار الحماية تسمح باتصالات RDP.

1. الاتصال إلى جهازك وتشغيل محاكاة هجوم عن **طريق تحديد الاتصال**.

    :::image type="content" source="images/test-machine-table.png" alt-text="زر الاتصال للأجهزة الاختبارية" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="شاشة اتصال سطح المكتب البعيد" lightbox="images/remote-connection.png":::

    بالنسبة **إلى أجهزة Linux**: ستحتاج إلى استخدام عميل SSH محلي الأمر الذي تم توفيره. 


    > [!NOTE]
    > إذا لم يكن لديك نسخة من كلمة المرور المحفوظة أثناء الإعداد الأولي، يمكنك إعادة تعيين كلمة المرور عن طريق تحديد إعادة تعيين كلمة **المرور من القائمة** :
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="الخيار &quot;إعادة تعيين كلمة المرور&quot;" lightbox="images/reset-password-test-machine.png":::
    >
    > سيغير الجهاز الحالة إلى "تنفيذ إعادة تعيين كلمة المرور"، ثم سيتم تقديم كلمة المرور الجديدة في غضون دقائق قليلة.

3. أدخل كلمة المرور التي تم عرضها أثناء خطوة إنشاء الجهاز.

   :::image type="content" source="images/enter-password.png" alt-text="الشاشة التي تقوم بإدخال بيانات الاعتماد عليها" lightbox="images/enter-password.png":::

4. تشغيل عمليات محاكاة الهجمات بنفسك على الجهاز.

### <a name="threat-simulator-scenarios"></a>سيناريوهات محاكي التهديدات

إذا اخترت تثبيت أي من محاكي التهديدات المعتمدة أثناء إعداد المعمل، يمكنك تشغيل عمليات المحاكاة المضمنة على أجهزة معامل التقييم.

يشكل تشغيل عمليات محاكاة التهديدات باستخدام الأنظمة الأساسية الخاصة ب جهة خارجية طريقة جيدة لتقييم Microsoft Defender لنقطة النهاية داخل بيئة المعمل.

> [!NOTE]
>
> قبل أن تتمكن من تشغيل عمليات المحاكاة، تأكد من تلبية المتطلبات التالية:
>
> - يجب إضافة الأجهزة إلى معمل التقييم
> - يجب تثبيت محاكي التهديدات في معمل التقييم

1. من المدخل، حدد **إنشاء محاكاة**.

2. حدد محاكي تهديدات.

   :::image type="content" source="images/select-simulator.png" alt-text="تحديد محاكي التهديدات" lightbox="images/select-simulator.png":::

3. اختر محاكاة أو ابحث في معرض المحاكاة للاستعراض عبر عمليات المحاكاة المتوفرة.

    يمكنك الوصول إلى معرض المحاكاة من:
    - لوحة معلومات التقييم الرئيسية في لوحة **نظرة عامة على عمليات المحاكاة** أو
    - من خلال الانتقال من جزء التنقل **التقييم** \> والبرامج التعليمية محاكاة & **البرامج** التعليمية، ثم حدد **كتالوج عمليات المحاكاة**.

4. حدد الأجهزة التي تريد تشغيل المحاكاة عليها.

5. حدد **إنشاء محاكاة**.

6. عرض تقدم عملية محاكاة عن طريق تحديد علامة **التبويب عمليات المحاكاة** . عرض حالة المحاكاة والتنبيهات النشطة وتفاصيل أخرى.

   :::image type="content" source="images/simulations-tab.png" alt-text="علامة التبويب &quot;عمليات محاكاة&quot;" lightbox="images/simulations-tab.png":::

بعد تشغيل عمليات المحاكاة، نشجعك على السير عبر شريط التقدم في المعمل واستكشاف Microsoft Defender لنقطة النهاية إجراء عملية تحقيق **وبحث تلقائية**. اطلع على الإثباتات التي تم تجميعها وتحليلها بواسطة الميزة.

البحث عن أدلة الهجوم من خلال البحث المتقدم باستخدام لغة الاستعلام الغنية وفحص بيانات التعقب الخام وفحص بعض التهديدات على مستوى العالم الموثقة في تحليلات المخاطر.

## <a name="simulation-gallery"></a>معرض المحاكاة

Microsoft Defender لنقطة النهاية شراكة مع العديد من الأنظمة الأساسية لمحاكاة التهديدات من أجل منح لك إمكانية الوصول المناسبة لاختبار إمكانات النظام الأساسي مباشرة من داخل المدخل.

اشاهد كل عمليات المحاكاة المتوفرة عن طريق الذهاب إلى  **كتالوج عمليات** المحاكاة والبرامج التعليمية \> **من القائمة**  .

يتم سرد قائمة بوكلاء محاكاة التهديدات المعتمدين من جهة خارجية، كما يتم توفير أنواع معينة من عمليات المحاكاة إلى جانب أوصاف تفصيلية في الكتالوج.

يمكنك بسهولة تشغيل أي محاكاة متوفرة مباشرة من الكتالوج.

:::image type="content" source="images/simulations-catalog.png" alt-text="كتالوج عمليات المحاكاة" lightbox="images/simulations-catalog.png":::

تأتي كل محاكاة مع وصف مفصل لسيناريوهات الهجوم ومراجع مثل تقنيات هجوم MITRE المستخدمة ونموذج استعلامات البحث المتقدم التي تقوم بتشغيلها.

**أمثلة:**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="مثال على تفاصيل وصف المحاكاة لأساليب الثبات" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="تفاصيل وصف المحاكاة ل APT29" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>تقرير التقييم

تلخص تقارير المعمل نتائج عمليات المحاكاة التي أجريت على الأجهزة.

:::image type="content" source="images/eval-report.png" alt-text="تقرير التقييم" lightbox="images/eval-report.png":::

بنظرة سريعة، سوف تتمكن بسرعة من رؤية:

- الأحداث التي تم تشغيلها
- التنبيهات التي تم إنشاؤها
- التقييمات على مستوى التعرض للضوء
- فئات التهديدات التي تم ملاحظتها
- مصادر الكشف
- عمليات التحقيق التلقائية

## <a name="provide-feedback"></a>تقديم الملاحظات

تساعدنا ملاحظاتك على تحسين حماية بيئتك من الهجمات المتقدمة. شارك تجربتك وانطباعاتك من قدرات المنتجات ونتائج التقييم.

أعلمنا رأيك عن طريق تحديد **تقديم ملاحظات**.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="صفحة الملاحظات" lightbox="images/send-us-feedback-eval-lab.png":::
