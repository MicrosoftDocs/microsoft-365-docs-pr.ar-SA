---
title: معالجة حسابات المستخدمين التي تم اختراقها باستخدام الاستجابة والتحري التلقائي
keywords: AIR، autoIR، Microsoft Defender ل Endpoint، تلقائي، تحقيق، استجابة، معالجة، تهديدات، متقدم، خطر، حماية، معرض للاختراق
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
description: تعرف على كيفية تسريع عملية الكشف عن حسابات المستخدمين التي تم اختراقها ومعالجتها باستخدام قدرات الاستجابة والتحري التلقائية في Microsoft Defender Office 365 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cbc3c6c8a81d59bebbd5272e13e0f96de2257623
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63570963"
---
# <a name="address-compromised-user-accounts-with-automated-investigation-and-response"></a>معالجة حسابات المستخدمين التي تم اختراقها باستخدام الاستجابة والتحري التلقائي

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


[يتضمن Microsoft Defender Office 365 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) قدرات فعالة [للتحري والاستجابة](office-365-air.md) التلقائية (AIR). من الممكن أن توفر هذه الإمكانات لفريق عمليات الأمان الكثير من الوقت والجهد في التعامل مع التهديدات. تواصل Microsoft تحسين قدرات الأمان. مؤخرا، تم تحسين قدرات AIR لتضمين مصنف أمان مستخدم ملوث (حاليا قيد المعاينة). اقرأ هذه المقالة لمعرفة المزيد حول دفتر تشغيل أمان المستخدم الذي تم اختراقه. راجع منشور المدونة تسريع الوقت للكشف عن اختراق المستخدم والاستجابة له والحد من نطاق الانتهاك باستخدام [Microsoft Defender Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Speed-up-time-to-detect-and-respond-to-user-compromise-and-limit/ba-p/977053) للحصول على مزيد من التفاصيل.

![إجراء تحقيق تلقائي لمستخدم تم اختراقه.](/microsoft-365/media/office365atp-compduserinvestigation.jpg)

يمكن دفتر تشغيل أمان المستخدم الذي تم اختراقه فريق الأمان في مؤسستك من القيام ب:

- تسريع عملية الكشف عن حسابات المستخدمين التي تم اختراقها؛
- تحديد نطاق الانتهاك عند اختراق حساب؛ و
- الاستجابة للمستخدمين الذين تم اختراقهم بفعالية وفعالية أكبر.

## <a name="compromised-user-alerts"></a>تنبيهات المستخدمين التي تم اختراقها

عند اختراق حساب مستخدم، تحدث سلوكيات غير منطقية أو غير منطقية. على سبيل المثال، قد يتم إرسال رسائل التصيد الاحتيالي والبريد العشوائي داخليا من حساب مستخدم موثوق به. يمكن ل Office 365 الكشف عن حالات الشذوذ هذه في أنماط البريد الإلكتروني ونشاط التعاون داخل Office 365. عند حدوث ذلك، يتم تشغيل التنبيهات، وتبدأ عملية التخفيف من المخاطر.

على سبيل المثال، إليك تنبيه تم تشغيله بسبب إرسال بريد إلكتروني مريب:

![تم تشغيل التنبيه بسبب إرسال بريد إلكتروني مريب.](/microsoft-365/media/office365atp-suspiciousemailsendalert.jpg)

وفيما يلي مثال على تنبيه تم تشغيله عند الوصول إلى حد الإرسال للمستخدم:

![تم تشغيل التنبيه عن طريق الوصول إلى حد الإرسال.](/microsoft-365/media/office365atp-sendinglimitreached.jpg)

## <a name="investigate-and-respond-to-a-compromised-user"></a>التحقق من المستخدم الذي تم اختراقه والرد عليه

عند اختراق حساب مستخدم، يتم تشغيل التنبيهات. وفي بعض الحالات، يتم حظر حساب المستخدم هذا ومنعه من إرسال أي رسائل بريد إلكتروني إضافية حتى يتم حل المشكلة بواسطة فريق عمليات الأمان في مؤسستك. في حالات أخرى، يبدأ التحقيق التلقائي الذي قد يؤدي إلى الإجراءات الموصى بها التي يجب أن يتخذها فريق الأمان.

- [عرض المستخدمين المقيدين والتحقق من الأمر](#view-and-investigate-restricted-users)

- [عرض تفاصيل حول عمليات التحقيق التلقائية](#view-details-about-automated-investigations)

> [!IMPORTANT]
> يجب أن يكون لديك الأذونات المناسبة لتنفيذ المهام التالية. راجع [الأذونات المطلوبة لاستخدام قدرات AIR](office-365-air.md#required-permissions-to-use-air-capabilities).

### <a name="view-and-investigate-restricted-users"></a>عرض المستخدمين المقيدين والتحقق من الأمر

لديك بعض الخيارات للتنقل إلى قائمة المستخدمين المقيدين. على سبيل المثال، في مدخل Microsoft 365 Defender، يمكنك الانتقال إلى **البريد** الإلكتروني & **مراجعة** \> \> **المستخدمين المقيدين**. يصف الإجراء التالي التنقل باستخدام لوحة معلومات التنبيهات، وهي طريقة جيدة لرؤية أنواع مختلفة من التنبيهات التي قد تكون تم تشغيلها.

1. افتح Microsoft 365 Defender في <https://security.microsoft.com> واذهب إلى **تنبيهات** \> & **تنبيهات الأحداث**. أو، انتقل مباشرة إلى صفحة **التنبيهات** ، استخدم <https://security.microsoft.com/alerts>.

2. في صفحة **التنبيهات** ، يمكنك تصفية النتائج حسب الفترة الزمنية النهج المسمى **المستخدم مقيد من إرسال البريد الإلكتروني**.

   ![صفحة التنبيهات في Microsoft 365 Defender تمت تصفيتها للمستخدمين المقيدين.](../../media/m365-sc-alerts-page-with-restricted-user.png)

3. إذا قمت بتحديد الإدخال بالنقر فوق الاسم، يتم فتح مستخدم مقيد من  إرسال صفحة البريد الإلكتروني بتفاصيل إضافية لمراجعتها. بجانب الزر **إدارة التنبيه** ، يمكنك النقر فوق أيقونة ![خيارات إضافية.](../../media/m365-cc-sc-more-actions-icon.png) **المزيد من** الخيارات، ثم حدد **عرض تفاصيل** المستخدم المقيدة للذهاب إلى صفحة المستخدمون المقيدون، حيث يمكنك تحرير [المستخدم المقيد](removing-user-from-restricted-users-portal-after-spam.md).

   ![تم تقييد المستخدم من إرسال صفحة البريد الإلكتروني من مركز التنبيهات.](../../media/m365-sc-alerts-user-restricted-from-sending-email-page.png)

### <a name="view-details-about-automated-investigations"></a>عرض تفاصيل حول عمليات التحقيق التلقائية

عندما يبدأ التحقيق التلقائي، يمكنك الاطلاع على تفاصيله ونتائجه في مركز التوافق & الأمان. انتقل إلى **"التحقيق في إدارة** \> **المخاطر**"، ثم حدد التحقيق لعرض تفاصيله.

لمعرفة المزيد، راجع [عرض تفاصيل التحقيق](air-view-investigation-results.md).

## <a name="keep-the-following-points-in-mind"></a>ضع النقاط التالية في الاعتبار

- **ابق على أهبة الاستعدادات.** كما تعلم، كلما لم يتم اكتشاف أي اختراق، زاد احتمال التأثير والتكلفة على نطاق واسع على مؤسستك والعملاء والشركاء. إن الكشف المبكر والاستجابة في الوقت المناسب أمران بالغا الأهمية للحد من التهديدات، ولا سيما عندما يتم اختراق حساب المستخدم.

- **يساعد التنفيذ التلقائي فريق** عمليات الأمان، ولكنه لا يحل محله. يمكن أن تكشف قدرات الاستجابة والتحري التلقائية عن مستخدم م اختراق في وقت مبكر، ولكن من المرجح أن يحتاج فريق عمليات الأمان إلى التفاعل مع بعض عمليات البحث والاستجابة. هل تحتاج إلى بعض المساعدة في هذا الأمر؟ راجع [مراجعة الإجراءات والموافقة عليها](air-review-approve-pending-completed-actions.md).

- **لا تعتمد على تنبيه تسجيل الدخول المريب كمؤشرك الوحيد**. عند اختراق حساب مستخدم، قد يقوم بتشغيل تنبيه تسجيل دخول مريب أو قد لا يقوم بتشغيله. في بعض الأحيان تكون سلسلة الأنشطة التي تحدث بعد اختراق الحساب هي التي تؤدي إلى تشغيل تنبيه. هل تريد معرفة المزيد حول التنبيهات؟ راجع [سياسات التنبيه](../../compliance/alert-policies.md).

## <a name="next-steps"></a>الخطوات التالية

- [مراجعة الأذونات المطلوبة لاستخدام قدرات AIR](office-365-air.md#required-permissions-to-use-air-capabilities)

- [البحث عن البريد الإلكتروني الضار في Office 365](investigate-malicious-email-that-was-delivered.md)

- [التعرف على AIR في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)

- [تفضل بزيارة Microsoft 365 خريطة الطريق لمعرفة ما سيكتشف قريبا ويخرج](https://www.microsoft.com/microsoft-365/roadmap?filters=)