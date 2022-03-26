---
title: التحقق من المستخدمين في Microsoft 365 Defender
description: تحقق من وجود حادث في مدخل Microsoft 365 Defender المستخدمين.
keywords: الأمان والبرامج الضارة Microsoft 365 و M365 ومركز الأمان والشاشة والتقارير والهويات والبيانات والأجهزة والتطبيقات والحادث والتحليل والاستجابة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: d49ef6b31e6446f3452d0efdce2e918813eabcc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572234"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>التحقق من المستخدمين في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

يمكن أن يتضمن جزء من التحقيق في الحادث حسابات المستخدمين. يمكنك الاطلاع على تفاصيل حسابات المستخدمين المحددة في تنبيهات حادث في مدخل Microsoft 365 Defender من **الأحداث** \> & **_التنبيهات incident_*_ \> _* Users**. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="مثال لصفحة &quot;المستخدمون&quot; لحادث." lightbox="../../media/investigate-incidents/incident-users.png":::

للحصول على ملخص سريع لحساب مستخدم للحادث، حدد علامة الاختيار بجانب اسم حساب المستخدم. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="مثال لجزاء ملخص حساب المستخدم لحادث ما." lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> تعرض صفحة المستخدم مؤسسة Azure Active Directory (Azure AD) بالإضافة إلى المجموعات، مما يساعدك على فهم المجموعات والأذونات المقترنة بمستخدم.

في هذا الجزء، يمكنك مراجعة معلومات تهديدات المستخدم، بما في ذلك أي أحداث حالية وتنبيهات نشطة ومستوى المخاطر بالإضافة إلى التعرض للمستخدم والحسابات والأجهزة والمزيد.

بالإضافة إلى ذلك، يمكنك اتخاذ إجراء مباشرة في مدخل Microsoft 365 Defender لمعالجة مستخدم تم اختراقه، مثل تأكيد اختراق حساب المستخدم أو طلب تسجيل الدخول الجديد.

من هنا، يمكنك تحديد **الانتقال إلى صفحة المستخدم** لرؤية تفاصيل حساب مستخدم. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="مثال لصفحة حساب المستخدم لحادث." lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

يمكنك أيضا رؤية هذه الصفحة عن طريق تحديد اسم حساب المستخدم من القائمة على **صفحة** المستخدمون.

يمكنك رؤية عضوية المجموعة للمستخدم عن طريق تحديد الرقم ضمن **المجموعات**.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="مثال لعضوية المجموعة لمستخدم." lightbox="../../media/investigate-users/user-group-membership.png":::

من خلال تحديد الأيقونة ضمن **مدير**، يمكنك معرفة مكان وجود المستخدم في شجرة المؤسسة.

تجمع Microsoft 365 Defender مدخل ويب معلومات من Microsoft Defender ل Endpoint و Microsoft Defender for Identity و Microsoft Defender for Cloud Apps (استنادا إلى التراخيص التي لديك).

تعرض هذه الصفحة معلومات خاصة بخطر الأمان لحساب المستخدم، الذي يتضمن درجة تساعد على تقييم المخاطر والأحداث والتنبيهات الأخيرة التي كانت تساهم في الخطر العام.

من هذه الصفحة، يمكنك القيام بهذه الإجراءات الإضافية:

- وضع علامة على حساب المستخدم كمختر
- طلب تسجيل الدخول مرة أخرى من قبل المستخدم
- تعليق حساب المستخدم
- راجع إعدادات حساب مستخدم Azure AD
- عرض الملفات المملوكة لحساب المستخدم
- عرض الملفات المشتركة مع هذا المستخدم.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="مثال على الإجراءات على حساب مستخدم لحادث." lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>عرض مسارات الحركة العرضية

من خلال تحديد علامة  التبويب مسارات الحركة الفوقية، يمكنك عرض خريطة ديناميكية تماما ويمكن النقر فوقها توفر لك تمثيلا مرئيا لمسارات الحركة الفوقية من ونهاية هذا المستخدم الذي يمكن استخدامه للتسلل إلى شبكتك.

توفر لك الخريطة قائمة تتضمن عدد القفزات بين أجهزة الكمبيوتر أو المستخدمين الذين قد يحتاجهم مهاجم من هذا المستخدم وإخراسه من أجل اختراق حساب حساس، وإذا كان لدى المستخدم حساب حساس، يمكنك معرفة عدد الموارد والحسابات المتصلة مباشرة.

إذا لم يتم اكتشاف مسار حركة لاحقة للكيان خلال اليومين الماضيين، لن يتم عرض الرسم البياني. حدد تاريخا مختلفا باستخدام عرض تاريخ مختلف لعرض الرسوم البيانية السابقة لمسارات الحركة اللاحقة التي تم اكتشافها لهذا الكيان. يتوفر تقرير مسار الحركة اللاحقة دائما لتزويدك بمعلومات حول مسارات الحركة اللاحقة المحتملة التي تم اكتشافها، ويمكن تخصيصه حسب الوقت.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="مثال لمسار الحركة اللاحقة للمستخدم." lightbox="../../media/investigate-users/lateral-movement-path.png":::

لمزيد من المعلومات، راجع [مسارات الحركة اللاحقة](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>الخطوات التالية

كما هو مطلوب للحوادث الجارية، تابع [التحقيق](investigate-incidents.md).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [تحديد أولوية الأحداث](incident-queue.md)
- [إدارة الأحداث](manage-incidents.md)
