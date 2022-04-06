---
title: التحقق من التنبيهات في Microsoft 365 Defender
description: تحقق من التنبيهات التي يتم شاهدها عبر الأجهزة والمستخدمين علب البريد.
keywords: الأحداث والتنبيهات، التحقيق، التحليل، الاستجابة، الارتباط، الهجوم، الأجهزة، الأجهزة، المستخدمون، الهويات، الهوية، علبة البريد، البريد الإلكتروني، 365، microsoft، m365
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
ms.openlocfilehash: c09a3880a9f117d0ce5ce6e5edf3736192fc9c95
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499848"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>التحقق من التنبيهات في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

>[!Note]
>تصف هذه المقالة تنبيهات الأمان في Microsoft 365 Defender. ومع ذلك، يمكنك استخدام تنبيهات النشاط لإرسال إعلامات بالبريد الإلكتروني إلى نفسك أو إلى المسؤولين الآخرين عندما يقوم المستخدمون بتنفيذ أنشطة معينة في Microsoft 365. لمزيد من المعلومات، راجع [إنشاء تنبيهات النشاط - Microsoft 365 التوافق | Microsoft Docs](../../compliance/create-activity-alerts.md).

التنبيهات هي أساس كل الأحداث وتشير إلى حدوث أحداث ضارة أو مريبة في بيئتك. عادة ما تكون التنبيهات جزءا من هجوم أوسع وتوفر دلائل حول حادث.

في Microsoft 365 Defender، يتم تجميع التنبيهات ذات الصلة معا لحوادث [النموذج](incidents-overview.md). توفر الأحداث دائما السياق الأوسع للهجوم، ومع ذلك، يمكن أن يكون تحليل التنبيهات ذا قيمة عند الحاجة إلى إجراء تحليل أعمق.

تعرض **قائمة انتظار التنبيهات** مجموعة التنبيهات الحالية. يمكنك الوصول إلى قائمة انتظار التنبيهات من & **تنبيهات** > التنبيهات عند التشغيل السريع [Microsoft 365 Defender المدخل](https://go.microsoft.com/fwlink/p/?linkid=2077139).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="مقطع التنبيهات في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

تظهر التنبيهات من حلول أمان Microsoft المختلفة مثل Microsoft Defender لنقطة النهاية Microsoft Defender لـ Office 365 Microsoft 365 Defender هنا.

بشكل افتراضي، تعرض قائمة انتظار التنبيهات في Microsoft 365 Defender الجديد وتنبيهات التقدم من آخر 30 يوما. يوجد التنبيه الأخير في أعلى القائمة حتى تتمكن من رؤيته أولا. 

من قائمة انتظار التنبيهات الافتراضية، يمكنك تحديد **تصفية** لرؤية جزء عامل التصفية، الذي يمكنك تحديد مجموعة فرعية من التنبيهات منه. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="القسم عوامل التصفية في Microsoft 365 Defender المدخل." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

يمكنك تصفية التنبيهات وفقا لهذه المعايير:

- الخطورة
- الحالة
- مصادر الخدمة
- الكيانات (الأصول التي تم التأثير عليها)
- حالة التحقيق التلقائي

## <a name="required-roles-for-defender-for-office-365-alerts"></a>الأدوار المطلوبة لتنبيهات Defender لـ Office 365

ستحتاج إلى الحصول على أي من الأدوار التالية للوصول إلى Microsoft Defender لـ Office 365 التنبيهات:

- بالنسبة للأدوار العامة ل Azure Active Directory (Azure AD):

   - المسؤول العام

   - مسؤول الأمان

   - عامل تشغيل الأمان

   - القارئ العام

   - قارئ الأمان

- Office 365 مجموعات دور & الأمان والتوافق

   - مسؤول التوافق

   - إدارة المؤسسة 

- دور [مخصص](custom-roles.md)

## <a name="analyze-an-alert"></a>تحليل تنبيه

لرؤية صفحة التنبيه الرئيسية، حدد اسم التنبيه. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="تفاصيل تنبيه في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

يمكنك أيضا تحديد الإجراء **فتح صفحة التنبيه الرئيسي** من **جزء إدارة التنبيهات** .

تتألف صفحة التنبيه من هذه المقاطع: 

- قصة التنبيه، وهي سلسلة الأحداث والتنبيهات ذات الصلة بهذا التنبيه بترتيب زمني
- تفاصيل الملخص

في صفحة التنبيه، يمكنك تحديد البقصاصات (**...**) إلى جانب أي كيان لرؤية الإجراءات المتوفرة، مثل ربط التنبيه بحادث آخر. تعتمد قائمة الإجراءات المتوفرة على نوع التنبيه.

### <a name="alert-sources"></a>مصادر التنبيهات

Microsoft 365 Defender التنبيهات من حلول مثل Microsoft Defender لنقطة النهاية، Microsoft Defender لـ Office 365، Microsoft Defender for Cloud Apps، والإدارة الإضافية لإدارة التطبيق Microsoft Defender for Cloud Apps. قد تلاحظ تنبيهات ذات أحرف معببة مسبقا في التنبيه. يوفر الجدول التالي إرشادات لمساعدتك على فهم تعيين مصادر التنبيه استنادا إلى الحرف المزدخم مسبقا على التنبيه.

> [!NOTE]
> - إن GUIDs المزدخمة خاصة فقط ب التجارب الموحدة مثل قائمة انتظار التنبيهات الموحدة وصفحة التنبيهات الموحدة والتحري الموحد والحادث الموحد.
> - لا يغير الحرف المرتد مسبقا GUID الخاص بالتنبيه. التغيير الوحيد الذي يتم تغييره إلى GUID هو المكون المرتد مسبقا.

| مصدر التنبيه | حرف معبب مسبقا |
| :---|:--- |
| Microsoft Defender لـ Office 365 | `fa{GUID}` <br> على سبيل المثال:`fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender لنقطة النهاية | `da` أو `ed` لتنبيهات الكشف المخصصة <br> |
| Microsoft Defender for Identity | `aa{GUID}` <br> على سبيل المثال:`aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> على سبيل المثال:`ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>تحليل الأصول المتأثرة

تتضمن **قائمة الإجراءات** التي تم اتخاذها قائمة بالأصول المتأثرة، مثل علب البريد والأجهزة والمستخدمين المتأثرين بهذا التنبيه. 

يمكنك أيضا تحديد **عرض في مركز الإجراءات** لعرض علامة التبويب **محفوظات** لمركز الإجراءات في Microsoft 365 Defender  المدخل. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>تتبع دور تنبيه في قصة التنبيه

تعرض قصة التنبيه كل الأصول أو الكيانات المرتبطة بالتنبيه في طريقة عرض شجرة معالجة. التنبيه في العنوان هو التنبيه الذي يتم التركيز عليه عند أول مرة يتم فيها التركيز على صفحة التنبيه المحددة. الأصول في قصة التنبيه قابلة للتوسع والنقر فوقها. فهي توفر معلومات إضافية وتسرع استجابتك من خلال السماح لك لاتخاذ إجراء مباشرة في سياق صفحة التنبيه. 

> [!NOTE]
> قد يحتوي مقطع قصة التنبيه على أكثر من تنبيه واحد، مع ظهور تنبيهات إضافية ذات صلة بنفس شجرة التنفيذ قبل التنبيه الذي حددته أو بعده.

### <a name="view-more-alert-information-on-the-details-page"></a>عرض مزيد من معلومات التنبيه على صفحة التفاصيل

تعرض صفحة التفاصيل تفاصيل التنبيه المحدد، مع تفاصيل والإجراءات المتعلقة به. إذا قمت بتحديد أي من الأصول أو الوحدات المتأثرة في قصة التنبيه، تتغير صفحة التفاصيل لتوفير معلومات سياقية والإجراءات للكائن المحدد.

بعد تحديد كيان يهمك، تتغير صفحة التفاصيل لعرض معلومات حول نوع الكيان المحدد والمعلومات التاريخية عند توفرها وخيارات اتخاذ إجراء على هذا الكيان مباشرة من صفحة التنبيه.

## <a name="manage-alerts"></a>إدارة التنبيهات

لإدارة تنبيه، حدد **إدارة** التنبيه في قسم تفاصيل التلخيص في صفحة التنبيه. للحصول على تنبيه واحد، فيما يلي مثال على جزء **إدارة التنبيهات** .

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="القسم &quot;إدارة التنبيه&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

يتيح **لك جزء** "إدارة التنبيهات" عرض أو تحديد:

- حالة التنبيه (جديد، تم الحل، في تقدم).
- حساب المستخدم الذي تم تعيين التنبيه له.
- تصنيف التنبيه:

   - **غير تعيين** (الإعداد الافتراضي).

   - **إيجابية حقيقية** مع نوع من التهديدات. استخدم هذا التصنيف للتنبيهات التي تشير إلى وجود خطر حقيقي. يساعد تحديد نوع الخطر فريق الأمان على رؤية أنماط التهديدات والعمل على حماية مؤسستك منها.

   - **نشاط معلوماتي متوقع** مع نوع نشاط. استخدم الخيارات في هذه الفئة لتصنيف التنبيهات لاختبارات الأمان ونشاط الفريق الأحمر والسلوك غير المعتاد المتوقع من التطبيقات والمستخدمين الموثوق بهم.

   - **إيجابية خاطئة** لأنواع التنبيهات التي تم إنشاؤها حتى في حالة عدم وجود نشاط ضار. يساعد تصنيف التنبيهات كتنبيهات خاطئة Microsoft 365 Defender تحسين جودة الكشف الخاصة بها.

- تعليق على التنبيه.

> [!NOTE]
> إحدى الطرق لإدارة تنبيهاتها من خلال استخدام العلامات. يتم طرح إمكانية وضع العلامات Microsoft Defender لـ Office 365 تدريجيا وهي حاليا في وضع المعاينة. <br>
> حاليا، يتم تطبيق أسماء العلامات المعدلة على التنبيهات التي تم إنشاؤها *بعد* التحديث فقط. لن تعكس التنبيهات التي تم إنشاؤها قبل التعديل اسم العلامة المحدث. 

لإدارة مجموعة *تنبيهات* مماثلة لتنبيه معين، حدد عرض تنبيهات  مماثلة في المربع **INSIGHT** في مقطع تفاصيل الملخص في صفحة التنبيه.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="إدارة تنبيه في مدخل Microsoft 365 Defender":::

من **الجزء إدارة التنبيهات** ، يمكنك بعد ذلك تصنيف كل التنبيهات ذات الصلة في الوقت نفسه. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="إدارة التنبيهات ذات الصلة في مدخل Microsoft 365 Defender":::

إذا تم تصنيف تنبيهات مماثلة في الماضي، يمكنك توفير الوقت باستخدام Microsoft 365 Defender للتعرف على كيفية حل التنبيهات الأخرى. من مقطع تفاصيل التلخيص **، حدد التوصيات**.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="مثال حول تحديد توصيات تنبيه":::

توفر **التوصيات** التالية إجراءات ونصائح حول التحقيق والتحري والمنع. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="مثال لتوصيات التنبيه":::

## <a name="resolve-an-alert"></a>حل تنبيه

بمجرد أن تنجز تحليل تنبيه ويمكن حله، انتقل إلى جزء إدارة التنبيهات للتنبيه  أو التنبيهات المشابهة وضع علامة على الحالة ك تم الحل ثم قم بتصنيفها كإيجابية True مع نوع من  التهديدات أو نشاط معلوماتي متوقع مع نوع نشاط  أو إيجابية **False**.

يساعد تصنيف التنبيهات Microsoft 365 Defender تحسين جودة الكشف الخاصة بها.

## <a name="use-power-automate-to-triage-alerts"></a>استخدام Power Automate لفرز التنبيهات

تحتاج فرق عمليات الأمان الحديثة (SecOps) إلى التنفيذ التلقائي للعمل بفعالية. للتركيز على الصيد والتحري عن التهديدات الحقيقية، تستخدم فرق SecOps Power Automate للفرز عبر قائمة التنبيهات وإزالة تلك التي ليست تهديدات.  

### <a name="criteria-for-resolving-alerts"></a>معايير حل التنبيهات

- تم تشغيل رسالة "خارج المكتب" للمستخدم

- لا يتم وضع علامة على المستخدم كخطر عال

إذا كان كل منهما صحيحا، فإن SecOps يصادف التنبيه على أنه سفر شرعي ويحله. يتم نشر إعلام في Microsoft Teams بعد حل التنبيه.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>الاتصال Power Automate Microsoft Defender for Cloud Apps

لإنشاء التنفيذ التلقائي، ستحتاج إلى رمز API مميز قبل أن تتمكن من Power Automate Microsoft Defender for Cloud Apps.

1. انقر **الإعدادات**، وحدد **ملحقات الأمان**، ثم انقر فوق **إضافة** رمز مميز في علامة التبويب **رموز API المميزة**.

2. قم بتوفير اسم لرمزك المميز، ثم انقر فوق **إنشاء**. احفظ الرمز المميز كما ستحتاج إليه لاحقا.

### <a name="create-an-automated-flow"></a>إنشاء تدفق تلقائي

للحصول على العملية المفصلة خطوة بخطوة، راجع الفيديو [هنا](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn).

يصف هذا الفيديو أيضا كيفية توصيل الطاقة التلقائية ب Defender for Cloud Apps.

## <a name="next-steps"></a>الخطوات التالية

كما هو مطلوب للحوادث الجارية، تابع [التحقيق](investigate-incidents.md).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [إدارة الأحداث](manage-incidents.md)
- [التحقيق في الأحداث](investigate-incidents.md)
