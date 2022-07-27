---
title: التحقيق مع المستخدمين في Microsoft 365 Defender
description: التحقيق مع المستخدمين لحادث في مدخل Microsoft 365 Defender.
keywords: الأمان والبرامج الضارة وMicrosoft 365 وM365 ومركز الأمان والمراقبة والتقرير والهويات والبيانات والأجهزة والتطبيقات والحوادث والتحليل والاستجابة
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
ms.openlocfilehash: 75fa4b76017c8fcb1f0ab65b5ed88440c04f47d2
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051613"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>التحقيق مع المستخدمين في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

يمكن أن يتضمن جزء من التحقيق في الحوادث حسابات المستخدمين. يمكنك الاطلاع على تفاصيل حسابات المستخدمين المحددة في تنبيهات حدث في مدخل Microsoft 365 Defender من **Incidents & alerts** \> **_incident_*_ \> _* Users**. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="صفحة المستخدمين لحادث في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

للحصول على ملخص سريع لحساب مستخدم للحادث، حدد علامة الاختيار إلى جانب اسم حساب المستخدم. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="علامة التبويب &quot;المستخدمون&quot; لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> تعرض صفحة المستخدم مؤسسة Azure Active Directory (Azure AD) بالإضافة إلى المجموعات، مما يساعدك على فهم المجموعات والأذونات المقترنة بالمستخدم.

في هذا الجزء، يمكنك مراجعة معلومات التهديد للمستخدم، بما في ذلك أي حوادث حالية وتنبيهات نشطة ومستوى مخاطر بالإضافة إلى تعرض المستخدم والحسابات والأجهزة والمزيد.

بالإضافة إلى ذلك، يمكنك اتخاذ إجراء مباشرة في مدخل Microsoft 365 Defender لمعالجة مستخدم تم اختراقه، مثل تأكيد اختراق حساب المستخدم أو طلب تسجيل دخول جديد.

من هنا، يمكنك تحديد **"الانتقال إلى صفحة المستخدم** " للاطلاع على تفاصيل حساب المستخدم. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="تفاصيل حساب المستخدم في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

يمكنك أيضا رؤية هذه الصفحة عن طريق تحديد اسم حساب المستخدم من القائمة على صفحة **المستخدمين** .

يمكنك رؤية عضوية المجموعة للمستخدم عن طريق تحديد الرقم ضمن **المجموعات**. سيؤدي تحديد مجموعة إلى فتح جزء **المجموعات** ، الذي يتضمن معلومات إضافية مثل تاريخ الإنشاء وعضوية المجموعة.

> [!NOTE]
> تعرض عضوية المجموعة فقط أول 1000 عضو في المجموعة.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="معلومات حول عضوية المجموعة لمستخدم في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-users/user-group-membership.png":::

من خلال تحديد الأيقونة ضمن **Manager**، يمكنك معرفة مكان وجود المستخدم في شجرة المؤسسة.

تجمع صفحة مستخدم مدخل Microsoft 365 Defender المعلومات من Microsoft Defender لنقطة النهاية Microsoft Defender for Identity و Microsoft Defender for Cloud Apps (اعتمادا على التراخيص التي لديك).

تعرض هذه الصفحة معلومات خاصة بالمخاطر الأمنية لحساب المستخدم، والتي تتضمن درجة تساعد على تقييم المخاطر والأحداث والتنبيهات الأخيرة التي ساهمت في الخطر العام.

من هذه الصفحة، يمكنك القيام بهذه الإجراءات الإضافية:

- وضع علامة على حساب المستخدم كمخترق
- مطالبة المستخدم بتسجيل الدخول مرة أخرى
- إيقاف حساب المستخدم مؤقتا
- راجع إعدادات حساب المستخدم Azure AD
- عرض الملفات التي يملكها حساب المستخدم
- عرض الملفات المشتركة مع هذا المستخدم.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="القسم الذي يصف الإجراءات على حساب مستخدم لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>عرض مسارات الحركة الجانبية

من خلال تحديد علامة تبويب **مسارات الحركة الجانبية** ، يمكنك عرض خريطة ديناميكية تماما وقابلة للنقر توفر لك تمثيلا مرئيا لمسارات الحركة الجانبية من وإلى هذا المستخدم التي يمكن استخدامها للتسلل إلى شبكتك.

توفر لك الخريطة قائمة بعدد القفزات بين أجهزة الكمبيوتر أو المستخدمين الذين سيتعين على المهاجم القيام به من وإلى هذا المستخدم للمساس بحساب حساس، وإذا كان المستخدم لديه حساب حساس، يمكنك معرفة عدد الموارد والحسابات المتصلة مباشرة.

إذا لم يتم الكشف عن مسار حركة جانبية محتمل للكيان خلال اليومين الماضيين، فلن يظهر الرسم البياني. حدد تاريخا مختلفا باستخدام عرض تاريخ مختلف لعرض الرسوم البيانية السابقة لمسارات الحركة الجانبية المكتشفة لهذا الكيان. يتوفر دائما تقرير مسار الحركة الجانبية لتزويدك بمعلومات حول مسارات الحركة الجانبية المحتملة المكتشفة، ويمكن تخصيصها بحلول الوقت.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="مسار الحركة الجانبية لمستخدم في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-users/lateral-movement-path.png":::

لمزيد من المعلومات، راجع [مسارات الحركة الجانبية](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>الخطوات التالية

حسب الحاجة للحوادث قيد المعالجة، تابع [التحقيق](investigate-incidents.md) الخاص بك.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [تحديد أولوية الأحداث](incident-queue.md)
- [إدارة الأحداث](manage-incidents.md)
