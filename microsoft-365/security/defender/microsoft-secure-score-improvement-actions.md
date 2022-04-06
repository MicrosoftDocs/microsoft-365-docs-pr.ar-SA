---
title: تقييم وضعية الأمان من خلال Microsoft Secure Score
description: يصف كيفية اتخاذ إجراء لتحسين "نقاط Microsoft الآمنة" في Microsoft 365 Defender الإلكتروني.
keywords: نقاط آمنة من microsoft، نقاط آمنة، نقاط آمنة في Office 365، نقاط أمان microsoft، Microsoft 365 Defender مدخل، إجراءات التحسين
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 8991c2aca277d2a08e5f8924a5e5cb354df6dc1f
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569415"
---
# <a name="assess-your-security-posture-with-microsoft-secure-score"></a>تقييم وضع الأمان باستخدام Microsoft Secure Score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure Score هو قياس لوضعية الأمان في المؤسسة، مع رقم أعلى يشير إلى المزيد من إجراءات التحسين التي تم اتخاذها. يمكن العثور عليه في https://security.microsoft.com/securescore مدخل Microsoft 365 Defender[.](microsoft-365-defender.md)

لمساعدتك في العثور على المعلومات التي تحتاج إليها بشكل أسرع، يتم تنظيم إجراءات التحسين من Microsoft في مجموعات:

- الهوية (حسابات Azure Active Directory & الأدوار)
- الجهاز (Microsoft Defender لنقطة النهاية، المعروف باسم [Microsoft Secure Score للأجهزة](/windows/security/threat-protection/microsoft-defender-atp/tvm-microsoft-secure-score-devices))
- التطبيقات (تطبيقات البريد الإلكتروني والسحابة، بما في ذلك Office 365 Microsoft Defender for Cloud Apps)

>[!NOTE]
>في الإصدار الأخير من Microsoft Secure Score، تم إصدار نموذج تسجيل محسن مما جعل Microsoft Secure Score غير متوافق مؤقتا مع نقاط الهوية الآمنة Graph API. [عرض التفاصيل](microsoft-secure-score-whats-new.md)

في صفحة نظرة عامة على Microsoft Secure Score، يمكنك عرض كيفية تقسيم النقاط بين هذه المجموعات والنقاط المتوفرة. يمكنك أيضا الحصول على طريقة عرض مضمنة لإجمالي الدرجة، والاتجاه التاريخي لسجل نقاطك الآمنة باستخدام مقارنات المعايير، والإجراءات ذات الأولوية للتحسينات التي يمكن اتخاذها لتحسين نقاطك.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="الصفحة الرئيسية &quot;نقاط آمنة&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="check-your-current-score"></a>التحقق من نقاطك الحالية

للتحقق من نقاطك الحالية، انتقل إلى صفحة نظرة عامة على Microsoft Secure Score وابحث عن اللوحة التي تقول **نقاطك الآمنة**. سيتم عرض نقاطك كنسبة مئوية، إلى جانب عدد النقاط التي حققتها من إجمالي النقاط الممكنة.

بالإضافة إلى ذلك، إذا قمت **بتحديد الزر تضمين** بجانب نقاطك، يمكنك اختيار طرق عرض مختلفة لسجلاتك. سيتم عرض طرق عرض الدرجات المختلفة هذه في الرسم البياني على لوحة الدرجة ومخطط تصنيف النقاط.

فيما يلي النقاط التي يمكنك إضافتها إلى طريقة العرض الخاصة بالنتيجة الإجمالية لتعطيك صورة كاملة عن إجمالي نقاطك:

- **النتيجة المخطط لها**: إظهار النتيجة المتوقعة عند اكتمال الإجراءات المخطط لها
- **نقاط الترخيص الحالية**: إظهار الدرجة التي يمكن تحقيقها باستخدام ترخيص Microsoft الحالي
- **نقاط قابلة لتحقيقها**: إظهار النتيجة التي يمكن تحقيقها باستخدام تراخيص Microsoft وقبول المخاطر الحالية

ستبدو طريقة العرض هذه كما لو قمت بضم كل طرق عرض النقاط المحتملة:

:::image type="content" source="../../media/secure-score/secure-score-achievable.png" alt-text="نقاطك الآمنة بما في ذلك النتيجة المخطط لها والنتيجة الحالية للترخيص والنتيجة القابلة لتحقيقها في مدخل Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-achievable.png":::

## <a name="take-action-to-improve-your-score"></a>اتخاذ إجراء لتحسين نقاطك

**تسرد علامة التبويب** إجراءات التحسين توصيات الأمان التي تعالج أسطح الهجمات المحتملة. وتتضمن أيضا الحالة (لمعالجة المخاطر، المخطط لها، المقبولة، التي يتم حلها من خلال طرف ثالث، يتم حلها من خلال تخفيف بديل، وإكمالها). يمكنك البحث عن جميع إجراءات التحسين وتصفيتها تجميعها.  

### <a name="ranking"></a>التصنيف

يستند تحديد المرتبة إلى عدد النقاط التي تبقى لتحقيقها وصعوبة التنفيذ وتأثير المستخدم وتعقيداتها. تظل إجراءات التحسين الأعلى تصنيفا عددا كبيرا من النقاط مع صعوبة منخفضة وتأثير المستخدم وتعقيداته.

### <a name="view-improvement-action-details"></a>عرض تفاصيل إجراء التحسين

عند تحديد إجراء تحسين معين، تظهر قائمة منبئة بصفحة كاملة.  

:::image type="content" source="../../media/secure-score/secure-score-improvement-action-details.png" alt-text="منتحلة من أحد إجراءات التحسين في مدخل Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-improvement-action-details.png":::

لإكمال الإجراء، لديك بعض الخيارات:

- حدد **إدارة في Microsoft 365 Defender** الانتقال إلى شاشة التكوين ثم إجراء التغيير. بعد ذلك، ستكتسب النقاط التي يساويها الإجراء، وهي مرئية في الجزء المتحرك. يستغرق تحديث النقاط عادة حوالي 24 ساعة.

- حدد **مشاركة** لنسخ الارتباط المباشر إلى إجراء التحسين. يمكنك أيضا اختيار النظام الأساسي لمشاركة الارتباط، مثل البريد الإلكتروني أو Microsoft Teams أو Microsoft Planner.

أضف **الملاحظات** لتعقب التقدم أو أي شيء آخر تريد التعليق عليه. إذا أضفت **علاماتك إلى** إجراء التحسين، يمكنك التصفية حسب هذه العلامات.

### <a name="choose-an-improvement-action-status"></a>اختيار حالة إجراء تحسين

اختر أي حالات وسجل الملاحظات الخاصة بعمل التحسين.

- **للمعالجة** - أنت تدرك أن إجراء التحسين ضروري وتخطط لمعالجته في مرحلة ما في المستقبل. تنطبق هذه الحالة أيضا على الإجراءات التي يتم الكشف عنها جزئيا، ولكن لم يتم إكمالها بالكامل.
- **المخطط له** - هناك خطط ملموسة في مكانها لإكمال إجراء التحسين.
- **قبول المخاطر** - يجب أن يكون الأمان دائما متوازنا مع إمكانية الاستخدام، ولن تعمل كل توصية مع بيئتك. عندما يكون الأمر كذلك، يمكنك اختيار قبول الخطر، أو الخطر المتبقي، وليس اتخاذ إجراء التحسين. لن تحصل على أي نقاط، ولكن لن يعود الإجراء مرئيا في قائمة إجراءات التحسين. يمكنك عرض هذا الإجراء في المحفوظات أو التراجع عنه في أي وقت.
- **تم الحل من** خلال جهة خارجية وحلها من خلال تخفيف **بديل - تم** بالفعل معالجة إجراء التحسين بواسطة تطبيق أو برنامج من جهة خارجية أو أداة داخلية. ستكتسب النقاط التي يستحقها الإجراء، بحيث تعكس نقاطك وضع الأمان العام بشكل أفضل. إذا لم تعد هناك جهة خارجية أو أداة داخلية تغطي عنصر التحكم، يمكنك اختيار حالة أخرى. ضع في اعتبارك أن Microsoft لن تكون لها رؤية لاكمال التنفيذ إذا تم وضع علامة على إجراء التحسين على أنه أي من هذه الحالة.

#### <a name="threat--vulnerability-management-improvement-actions"></a>إجراءات & إدارة الثغرات الأمنية المخاطر

بالنسبة إلى إجراءات التحسين في الفئة "الجهاز"، لا يمكنك اختيار الحالة. بدلا من ذلك، سيتم توجيهك إلى إدارة المخاطر والثغرات الأمنية [الأمان](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) في Microsoft 365 Defender اتخاذ إجراء. سيكون الاستثناء الذي تختاره وتبريره الذي تكتبه محددا لهذا المدخل. لن يكون موجودا في مدخل Microsoft Secure Score.

#### <a name="completed-improvement-actions"></a>إجراءات التحسين المكتملة

تكون حالة إجراءات التحسين "مكتملة" بمجرد تحقيق كل النقاط المحتملة الخاصة بعمل التحسين. يتم تأكيد إجراءات التحسين المكتملة على الرغم من بيانات Microsoft، ولا يمكنك تغيير الحالة.

### <a name="assess-information-and-review-user-impact"></a>تقييم المعلومات ومراجعة تأثير المستخدم

سيخبرك القسم **المسمى** بنظرة سريعة الفئة ولهجماته التي يمكنه حمايتها والمنتج.

**تأثير المستخدم** هو ما سيختبره المستخدمون إذا تم تنفيذ إجراء التحسين، وكان المستخدمون  المتأثرون هم الأشخاص الذين سيتأثرون.

### <a name="implement-the-improvement-action"></a>تنفيذ إجراء التحسين

يعرض **قسم** التنفيذ أي متطلبات أساسية، والخطوات التالية خطوة بخطوة لإكمال إجراء التحسين، حالة التنفيذ الحالية لخطوة التحسين، وأي ارتباطات معرفة المزيد.

تتضمن المتطلبات الأساسية أي تراخيص مطلوبة أو إجراءات يجب إكمالها قبل معالجة إجراء التحسين. تأكد من أن لديك ما يكفي من المقاعد في الترخيص لإكمال إجراء التحسين ومن تطبيق هذه التراخيص على المستخدمين الضروريين.  

## <a name="we-want-to-hear-from-you"></a>نريد أن نستمع منك

إذا كانت لديك أي مشاكل، فأعلمنا بذلك من خلال النشر في مجتمع الأمان [والخصوصية & التوافق](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . نحن نراقب المجتمع وسنوفر المساعدة.

## <a name="related-resources"></a>الموارد ذات الصلة

- [نظرة عامة حول Microsoft Secure Score](microsoft-secure-score.md)
- [تعقب سجل Microsoft Secure Score و تحقيق الأهداف](microsoft-secure-score-history-metrics-trends.md)
- [ما الجديد](microsoft-secure-score-whats-coming.md)
- [أحدث الميزات](microsoft-secure-score-whats-new.md)
