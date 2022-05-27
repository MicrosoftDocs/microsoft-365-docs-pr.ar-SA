---
title: التحقيق في التنبيهات في Microsoft 365 Defender
description: تحقق من التنبيهات التي تظهر عبر الأجهزة والمستخدمين وعلب البريد.
keywords: الحوادث والتنبيهات والتحقيق والتحليل والاستجابة والارتباط والهجوم والأجهزة والأجهزة والمستخدمين والهويات والهوية وعلبة البريد والبريد الإلكتروني و365 وmicrosoft وm365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 40e0285f185d112fa508d871e0ccd70c2a09120e
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739406"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>التحقيق في التنبيهات في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

>[!Note]
>تصف هذه المقالة تنبيهات الأمان في Microsoft 365 Defender. ومع ذلك، يمكنك استخدام تنبيهات النشاط لإرسال إعلامات بالبريد الإلكتروني إلى نفسك أو إلى مسؤولين آخرين عندما يقوم المستخدمون بأنشطة معينة في Microsoft 365. لمزيد من المعلومات، راجع [إنشاء تنبيهات النشاط - Microsoft Purview | Microsoft Docs](../../compliance/create-activity-alerts.md).

التنبيهات هي أساس جميع الحوادث وتشير إلى حدوث أحداث ضارة أو مريبة في بيئتك. عادة ما تكون التنبيهات جزءا من هجوم أوسع وتوفر أدلة حول حادث.

في Microsoft 365 Defender، يتم تجميع التنبيهات ذات الصلة معا لتشكيل [الحوادث](incidents-overview.md). ستوفر الحوادث دائما السياق الأوسع للهجوم، ومع ذلك، يمكن أن يكون تحليل التنبيهات ذا قيمة عند الحاجة إلى تحليل أعمق.

تعرض **قائمة انتظار التنبيهات** مجموعة التنبيهات الحالية. يمكنك الوصول إلى قائمة انتظار التنبيهات من **التنبيهات & الحوادث > التنبيهات** على التشغيل السريع [لمدخل Microsoft 365 Defender](https://go.microsoft.com/fwlink/p/?linkid=2077139).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="قسم التنبيهات في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

تظهر هنا تنبيهات من حلول أمان Microsoft المختلفة مثل Microsoft Defender لنقطة النهاية Microsoft Defender لـ Office 365 Microsoft 365 Defender.

بشكل افتراضي، تعرض قائمة انتظار التنبيهات في مدخل Microsoft 365 Defender التنبيهات الجديدة والمتقدمة من آخر 30 يوما. يوجد التنبيه الأحدث في أعلى القائمة حتى تتمكن من رؤيته أولا. 

من قائمة انتظار التنبيهات الافتراضية، يمكنك تحديد **"تصفية** " لمشاهدة جزء **"عامل التصفية** "، الذي يمكنك من خلاله تحديد مجموعة فرعية من التنبيهات. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="قسم عوامل التصفية في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

يمكنك تصفية التنبيهات وفقا لهذه المعايير:

- شده
- حاله
- مصادر الخدمة
- الكيانات (الأصول المتأثرة)
- حالة التحقيق التلقائي

## <a name="required-roles-for-defender-for-office-365-alerts"></a>الأدوار المطلوبة لتنبيهات Defender لـ Office 365

ستحتاج إلى الحصول على أي من الأدوار التالية للوصول إلى تنبيهات Microsoft Defender لـ Office 365:

- للأدوار العمومية ل Azure Active Directory (Azure AD):

   - المسؤول العام

   - مسؤول الأمان

   - عامل تشغيل الأمان

   - القارئ العمومي

   - قارئ الأمان

- مجموعات دور التوافق Office 365 الأمان &

   - مسؤول التوافق

   - إدارة المؤسسة 

- [دور مخصص](custom-roles.md)

## <a name="analyze-an-alert"></a>تحليل تنبيه

لمشاهدة صفحة التنبيه الرئيسية، حدد اسم التنبيه. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="تفاصيل تنبيه في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

يمكنك أيضا تحديد إجراء **"فتح صفحة التنبيه الرئيسي** " من جزء **"إدارة التنبيه** ".

تتكون صفحة التنبيه من هذه المقاطع: 

- قصة التنبيه، وهي سلسلة الأحداث والتنبيهات المتعلقة بهذا التنبيه بترتيب زمني
- تفاصيل الملخص

في جميع أنحاء صفحة التنبيه، يمكنك تحديد علامات الحذف (**...**) إلى جانب أي كيان لرؤية الإجراءات المتاحة، مثل ربط التنبيه بحادث آخر. تعتمد قائمة الإجراءات المتوفرة على نوع التنبيه.

### <a name="alert-sources"></a>مصادر التنبيه

قد تأتي التنبيهات Microsoft 365 Defender من حلول مثل Microsoft Defender لنقطة النهاية، Microsoft Defender لـ Office 365، Microsoft Defender for Cloud Apps والوظيفة الإضافية لحوكمة التطبيق Microsoft Defender for Cloud Apps. قد تلاحظ تنبيهات ذات أحرف مسبقة في التنبيه. يوفر الجدول التالي إرشادات لمساعدتك على فهم تعيين مصادر التنبيه استنادا إلى الحرف الذي تم إلحاقه في التنبيه.

> [!NOTE]
> - تكون معرفات واجهة المستخدم الرسومية التي تم تشغيلها مسبقا خاصة فقط بالتجارب الموحدة مثل قائمة انتظار التنبيهات الموحدة وصفحة التنبيهات الموحدة والتحقيق الموحد والحوادث الموحدة.
> - لا يغير الحرف الذي تم تثبيته المعرف الفريد العمومي (GUID) للتنبيه. التغيير الوحيد إلى GUID هو المكون السابق.

| مصدر التنبيه | حرف مسبق |
| :---|:--- |
| Microsoft Defender لـ Office 365 | `fa{GUID}` <br> على سبيل المثال:`fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Endpoint | `da` أو `ed` لتنبيهات الكشف المخصصة <br> |
| Microsoft Defender للهوية | `aa{GUID}` <br> على سبيل المثال:`aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> على سبيل المثال:`ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>تحليل الأصول المتأثرة

يحتوي قسم **الإجراءات التي تم اتخاذها** على قائمة بالأصول المتأثرة، مثل علب البريد والأجهزة والمستخدمين المتأثرين بهذا التنبيه. 

يمكنك أيضا تحديد **"عرض" في مركز الصيانة** لعرض علامة التبويب "**محفوظات**" في **مركز الصيانة** في مدخل Microsoft 365 Defender. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>تتبع دور التنبيه في قصة التنبيه

تعرض قصة التنبيه جميع الأصول أو الكيانات المتعلقة بالتنبيه في طريقة عرض شجرة العمليات. التنبيه في العنوان هو التنبيه الذي يتم التركيز عليه عند الوصول لأول مرة إلى صفحة التنبيه المحدد. الأصول في قصة التنبيه قابلة للتوسيع والنقر. وهي توفر معلومات إضافية وتسريع استجابتك من خلال السماح لك باتخاذ إجراء صحيح في سياق صفحة التنبيه. 

> [!NOTE]
> قد يحتوي قسم قصة التنبيه على أكثر من تنبيه واحد، مع ظهور تنبيهات إضافية متعلقة بنفس شجرة التنفيذ قبل التنبيه الذي حددته أو بعده.

### <a name="view-more-alert-information-on-the-details-page"></a>عرض مزيد من معلومات التنبيه في صفحة التفاصيل

تعرض صفحة التفاصيل تفاصيل التنبيه المحدد، مع التفاصيل والإجراءات المتعلقة به. إذا قمت بتحديد أي من الأصول أو الكيانات المتأثرة في قصة التنبيه، تتغير صفحة التفاصيل لتوفير معلومات وإجراءات سياقية للكائن المحدد.

بمجرد تحديد كيان اهتمام، تتغير صفحة التفاصيل لعرض معلومات حول نوع الكيان المحدد، والمعلومات التاريخية عندما يكون متوفرا، وخيارات اتخاذ إجراء بشأن هذا الكيان مباشرة من صفحة التنبيه.

## <a name="manage-alerts"></a>إدارة التنبيهات

لإدارة تنبيه، حدد **"إدارة التنبيه** " في قسم تفاصيل الملخص في صفحة التنبيه. للحصول على تنبيه واحد، إليك مثال على جزء **إدارة التنبيه** .

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="قسم &quot;إدارة التنبيه&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

يسمح لك جزء **"إدارة التنبيه** " بعرض ما يلي أو تحديده:

- حالة التنبيه (جديد، تم الحل، قيد التقدم).
- حساب المستخدم الذي تم تعيين التنبيه له.
- تصنيف التنبيه:

   - **غير معين** (الافتراضي).

   - **إيجابية حقيقية** مع نوع من التهديد. استخدم هذا التصنيف للتنبيهات التي تشير بدقة إلى تهديد حقيقي. يساعد تحديد نوع التهديد فريق الأمان على رؤية أنماط التهديد والعمل على الدفاع عن مؤسستك منها.

   - **نشاط إعلامي متوقع** مع نوع من النشاط. استخدم الخيارات الموجودة في هذه الفئة لتصنيف التنبيهات لاختبارات الأمان ونشاط الفريق الأحمر والسلوك غير العادي المتوقع من التطبيقات والمستخدمين الموثوق بهم.

   - **إيجابية خاطئة** لأنواع التنبيهات التي تم إنشاؤها حتى عندما لا يكون هناك نشاط ضار. يساعد تصنيف التنبيهات على أنها إيجابية زائفة Microsoft 365 Defender على تحسين جودة الكشف الخاصة بها.

- تعليق على التنبيه.

> [!NOTE]
> إحدى طرق إدارة التنبيهات من خلال استخدام العلامات. يتم نشر إمكانية وضع العلامات Microsoft Defender لـ Office 365 بشكل تزايدي وهي قيد المعاينة حاليا. <br>
> حاليا، يتم تطبيق أسماء العلامات المعدلة فقط على التنبيهات التي تم إنشاؤها *بعد* التحديث. لن تعكس التنبيهات التي تم إنشاؤها قبل التعديل اسم العلامة المحدثة. 

لإدارة *مجموعة من التنبيهات المشابهة لتنبيه معين*، حدد **عرض التنبيهات المماثلة** في مربع **INSIGHT** في قسم تفاصيل الملخص في صفحة التنبيه.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="إدارة تنبيه في مدخل Microsoft 365 Defender":::

من جزء **إدارة التنبيهات** ، يمكنك بعد ذلك تصنيف جميع التنبيهات ذات الصلة في نفس الوقت. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="إدارة التنبيهات ذات الصلة في مدخل Microsoft 365 Defender":::

إذا تم تصنيف تنبيهات مماثلة بالفعل في الماضي، يمكنك توفير الوقت باستخدام توصيات Microsoft 365 Defender لمعرفة كيفية حل التنبيهات الأخرى. من قسم تفاصيل الملخص، حدد **التوصيات**.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="مثال على تحديد توصيات تنبيه":::

توفر علامة التبويب **التوصيات** إجراءات الخطوة التالية ونصائح للتحقيق والمعالجة والوقاية. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="مثال لتوصيات التنبيه":::

## <a name="resolve-an-alert"></a>حل تنبيه

بمجرد الانتهاء من تحليل تنبيه ويمكن حله، انتقل إلى جزء **"إدارة التنبيه** " للتنبيه أو التنبيهات المماثلة وضع علامة على الحالة على أنها **"تم حلها** " ثم قم بتصنيفها على أنها **إيجابية True** مع نوع من التهديد، **أو نشاط إعلامي، أو متوقع** بنوع من النشاط، أو **إيجابية خطأ**.

يساعد تصنيف التنبيهات Microsoft 365 Defender على تحسين جودة الكشف.

## <a name="use-power-automate-to-triage-alerts"></a>استخدام Power Automate لفرز التنبيهات

تحتاج فرق عمليات الأمان الحديثة (SecOps) إلى التشغيل التلقائي للعمل بفعالية. للتركيز على تتبع التهديدات الحقيقية والتحقيق فيها، تستخدم فرق SecOps Power Automate لفرز قائمة التنبيهات والقضاء على تلك التي ليست تهديدات.  

### <a name="criteria-for-resolving-alerts"></a>معايير لحل التنبيهات

- تم تشغيل رسالة "خارج المكتب" للمستخدم

- لا يتم وضع علامة على المستخدم على أنه خطر كبير

إذا كان كلاهما صحيحا، فإن SecOps يضع علامة على التنبيه على أنه سفر شرعي ويحله. يتم نشر إعلام في Microsoft Teams بعد حل التنبيه.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>الاتصال Power Automate إلى Microsoft Defender for Cloud Apps

لإنشاء التشغيل التلقائي، ستحتاج إلى رمز مميز لواجهة برمجة التطبيقات قبل أن تتمكن من توصيل Power Automate Microsoft Defender for Cloud Apps.

1. انقر فوق **الإعدادات**، وحدد **ملحقات الأمان**، ثم انقر فوق **"إضافة رمز مميز**" في علامة التبويب **"رموز API المميزة**".

2. أدخل اسما للرمز المميز، ثم انقر فوق **"إنشاء**". احفظ الرمز المميز كما ستحتاج إليه لاحقا.

### <a name="create-an-automated-flow"></a>إنشاء تدفق تلقائي

شاهد هذا الفيديو القصير لمعرفة كيفية عمل الأتمتة بكفاءة لإنشاء سير عمل سلس وكيفية توصيل Power Automate ب Defender for Cloud Apps. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn]

## <a name="next-steps"></a>الخطوات التالية

حسب الحاجة للحوادث قيد المعالجة، تابع [التحقيق](investigate-incidents.md) الخاص بك.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [إدارة الأحداث](manage-incidents.md)
- [التحقيق في الأحداث](investigate-incidents.md)
