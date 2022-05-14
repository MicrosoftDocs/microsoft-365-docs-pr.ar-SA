---
title: معالجة حسابات المستخدمين المخترقة مع التحقيق التلقائي والاستجابة
keywords: AIR، autoIR، Microsoft Defender لنقطة النهاية، تلقائي، التحقيق، الاستجابة، المعالجة، التهديدات، المتقدمة، التهديد، الحماية، تم اختراقها
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection: M365-security-compliance
ms.custom: ''
ms.date: 06/10/2021
description: تعرف على كيفية تسريع عملية الكشف عن حسابات المستخدمين المخترقة ومعالجتها مع قدرات التحقيق والاستجابة التلقائية في Microsoft Defender لـ Office 365 الخطة 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 97466622a138a6604b9be51333148b472f7cd519
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418259"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>معالجة حسابات المستخدمين المخترقة مع التحقيق التلقائي والاستجابة

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[تتضمن Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) قدرات [قوية للتحقيق والاستجابة التلقائية](office-365-air.md) (AIR). يمكن أن توفر هذه القدرات لفريق عمليات الأمان لديك الكثير من الوقت والجهد للتعامل مع التهديدات. تواصل Microsoft تحسين قدرات الأمان. مؤخرا، تم تحسين قدرات AIR لتضمين دليل مبادئ أمان المستخدم الذي تم اختراقه (قيد المعاينة حاليا). اقرأ هذه المقالة لمعرفة المزيد حول دليل مبادئ أمان المستخدم الذي تم اختراقه. واطلع على وقت تسريع نشر المدونة [للكشف عن اختراق المستخدم والاستجابة له والحد من نطاق الخرق مع Microsoft Defender لـ Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) للحصول على تفاصيل إضافية.

![التحقيق التلقائي لمستخدم مخترق.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

يمكن دليل مبادئ أمان المستخدم الذي تم اختراقه فريق أمان مؤسستك من:

- تسريع الكشف عن حسابات المستخدمين المخترقة؛
- تحديد نطاق الخرق عند اختراق حساب؛ و
- الاستجابة للمستخدمين المخترقين بشكل أكثر فعالية وكفاءة.

## <a name="compromised-user-alerts"></a>تنبيهات المستخدم المخترقة

عند اختراق حساب مستخدم، تحدث سلوكيات غير نمطية أو غير طبيعية. على سبيل المثال، قد يتم إرسال رسائل التصيد الاحتيالي والبريد العشوائي داخليا من حساب مستخدم موثوق به. يمكن Defender لـ Office 365 اكتشاف مثل هذه الحالات الشاذة في أنماط البريد الإلكتروني ونشاط التعاون داخل Office 365. عند حدوث ذلك، يتم تشغيل التنبيهات، وتبدأ عملية التخفيف من المخاطر.

على سبيل المثال، إليك تنبيه تم تشغيله بسبب إرسال بريد إلكتروني مريب:

![تم تشغيل التنبيه بسبب إرسال بريد إلكتروني مريب.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

وفيما يلي مثال على تنبيه تم تشغيله عند الوصول إلى حد الإرسال للمستخدم:

![تم الوصول إلى التنبيه الذي تم تشغيله عن طريق إرسال الحد.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>التحقيق في مستخدم تم اختراقه والاستجابة له

عند اختراق حساب مستخدم، يتم تشغيل التنبيهات. وفي بعض الحالات، يتم حظر حساب المستخدم هذا ومنعه من إرسال أي رسائل بريد إلكتروني أخرى حتى يتم حل المشكلة من قبل فريق عمليات الأمان في مؤسستك. في حالات أخرى، يبدأ التحقيق التلقائي الذي يمكن أن يؤدي إلى إجراءات موصى بها يجب على فريق الأمان اتخاذها.

- [عرض المستخدمين المقيدين والتحقيق فيهم](#view-and-investigate-restricted-users)

- [عرض تفاصيل حول التحقيقات التلقائية](#view-details-about-automated-investigations)

> [!IMPORTANT]
> يجب أن يكون لديك الأذونات المناسبة لتنفيذ المهام التالية. راجع [الأذونات المطلوبة لاستخدام قدرات AIR](office-365-air.md#required-permissions-to-use-air-capabilities).

شاهد هذا الفيديو القصير لمعرفة كيف يمكنك الكشف عن اختراق المستخدم والاستجابة له في Microsoft Defender لـ Office 365 باستخدام التحقيق التلقائي والاستجابة (AIR) وتنبيهات المستخدم المخترقة.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWAl83]

### <a name="view-and-investigate-restricted-users"></a>عرض المستخدمين المقيدين والتحقيق فيهم

لديك بعض الخيارات للانتقال إلى قائمة المستخدمين المقيدين. على سبيل المثال، في مدخل Microsoft 365 Defender، يمكنك الانتقال إلى  تعاون \> **البريد الإلكتروني &** مراجعة \> **المستخدمين المقيدين**. يصف الإجراء التالي التنقل باستخدام لوحة معلومات **التنبيهات** ، وهي طريقة جيدة لمشاهدة أنواع مختلفة من التنبيهات التي ربما تم تشغيلها.

1. افتح مدخل Microsoft 365 Defender في <https://security.microsoft.com> **تنبيهات الحوادث** \> & وانتقل **إليها.** أو للانتقال مباشرة إلى صفحة **التنبيهات** ، استخدم <https://security.microsoft.com/alerts>.

2. في صفحة **التنبيهات** ، قم بتصفية النتائج حسب الفترة الزمنية والنهج المسمى **المستخدم مقيد من إرسال البريد الإلكتروني**.

   :::image type="content" source="../../media/m365-sc-alerts-page-with-restricted-user.png" alt-text="تمت تصفية صفحة التنبيهات في مدخل Microsoft 365 Defender للمستخدمين المقيدين" lightbox="../../media/m365-sc-alerts-page-with-restricted-user.png":::

3. إذا قمت بتحديد الإدخال بالنقر فوق الاسم، يفتح **مستخدم مقيد من إرسال صفحة البريد الإلكتروني** مع تفاصيل إضافية لمراجعتها. إلى جانب الزر **"إدارة التنبيه** "، يمكنك النقر فوق ![أيقونة "خيارات إضافية".](../../media/m365-cc-sc-more-actions-icon.png) **مزيد من الخيارات** ثم حدد **عرض تفاصيل المستخدم المقيد** للانتقال إلى صفحة **"المستخدمون المقيدون** "، حيث يمكنك [تحرير المستخدم المقيد](removing-user-from-restricted-users-portal-after-spam.md).

  :::image type="content" source="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png" alt-text="المستخدم مقيد من إرسال صفحة البريد الإلكتروني" lightbox="../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png":::

### <a name="view-details-about-automated-investigations"></a>عرض تفاصيل حول التحقيقات التلقائية

عند بدء تحقيق تلقائي، يمكنك الاطلاع على تفاصيله ونتائجه في مركز التوافق & الأمان. انتقل إلى تحقيقات **إدارة** \> **المخاطر**، ثم حدد التحقيق لعرض تفاصيله.

لمعرفة المزيد، راجع [عرض تفاصيل التحقيق](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>ضع النقاط التالية في الاعتبار

- **ابق على اطلاع على التنبيهات.** كما تعلم، كلما طالت فترة عدم الكشف عن التسوية، زاد احتمال التأثير والتكلفة على نطاق واسع لمؤسستك وعملائك وشركائك. يعد الكشف المبكر والاستجابة في الوقت المناسب أمرا بالغ الأهمية للتخفيف من التهديدات، وخاصة عند اختراق حساب المستخدم.

- **تساعد الأتمتة فريق عمليات الأمان الخاص بك، ولكن لا تحل محله**. يمكن أن تكشف قدرات التحقيق والاستجابة التلقائية عن مستخدم تم اختراقه في وقت مبكر، ولكن من المحتمل أن يحتاج فريق عمليات الأمان إلى المشاركة وإجراء بعض التحقيق والمعالجة. هل تحتاج إلى بعض المساعدة في هذا؟ راجع [مراجعة الإجراءات والموافقة عليها](air-review-approve-pending-completed-actions.md).

- **لا تعتمد على تنبيه تسجيل الدخول المشبوه كمؤشرك الوحيد**. عند اختراق حساب مستخدم، قد يؤدي أو لا يقوم بتشغيل تنبيه تسجيل دخول مريب. في بعض الأحيان، تكون سلسلة الأنشطة التي تحدث بعد اختراق الحساب هي التي تشغل تنبيها. هل تريد معرفة المزيد حول التنبيهات؟ راجع [نهج التنبيه](../../compliance/alert-policies.md).

## <a name="next-steps"></a>الخطوات التالية

- [مراجعة الأذونات المطلوبة لاستخدام قدرات AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [البحث عن البريد الإلكتروني الضار والتحقيق فيه في Office 365](investigate-malicious-email-that-was-delivered.md)

- [تعرف على AIR في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [تفضل بزيارة Microsoft 365 Roadmap للاطلاع على ما سيتوفر قريبا والطرح](https://www.microsoft.com/microsoft-365/roadmap?filters=)
