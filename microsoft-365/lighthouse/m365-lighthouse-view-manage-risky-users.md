---
title: عرض المستخدمين المعرضين للمخاطر وإدارتها في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية عرض المستخدمين المعرضين للمخاطر وإدارتهم.
ms.openlocfilehash: 45c91ec0871393f69e7a166cc8582f149479ad1b
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011827"
---
# <a name="view-and-manage-risky-users-in-microsoft-365-lighthouse"></a>عرض المستخدمين المعرضين للمخاطر وإدارتها في Microsoft 365 Lighthouse

تجمع Microsoft وتحلل تريليونات من إشارات تسجيل دخول المستخدم كل يوم. يتم استخدام هذه الإشارات للمساعدة في إنشاء أنماط سلوك تسجيل دخول مستخدم جيدة وتحديد محاولات تسجيل الدخول المحتملة المحفوفة بالمخاطر. تستخدم Azure Active Directory (Azure AD) Identity Protection هذه الإشارات لمراجعة محاولات تسجيل دخول المستخدم واتخاذ إجراء إذا كان هناك نشاط مريب.

يساعد Microsoft 365 Lighthouse على إدارة المخاطر التي تم اكتشافها بواسطة Azure AD Identity Protection من خلال توفير طريقة عرض واحدة للمستخدمين المعرضين للمخاطر عبر جميع المستأجرين المدارين. يمكنك تأمين المستخدمين المعرضين للمخاطر بسرعة إما عن طريق إعادة تعيين كلمة المرور الخاصة بهم أو حظرهم من تسجيل الدخول إلى حسابهم Microsoft 365. يمكنك أيضا عرض الرؤى لفهم مخاطر المستخدم بشكل أفضل وتحديد الخطوات التالية.

تحدد Azure AD Identity Protection المخاطر من أنواع متعددة، بما في ذلك:

- بيانات الاعتماد المسربة
- استخدام IP مجهول
- السفر غير النمطي
- تسجيل الدخول من الأجهزة المصابة
- تسجيل الدخول من عناوين IP مع نشاط مريب
- تسجيل الدخول من مواقع غير مألوفة

## <a name="before-you-begin"></a>قبل البدء

يجب استيفاء الشروط التالية قبل أن يظهر المستخدمون في قائمة المستخدمين المحفوفة بالمخاطر:

- يجب أن يكون لدى مستأجر العميل ترخيص Azure AD Premium لكل مستخدم. لمزيد من المعلومات حول التراخيص التي تدعم Azure AD Identity Protection، راجع [ما هي Identity Protection؟](/azure/active-directory/identity-protection/overview-identity-protection)

- يجب أن يكون مستأجر العميل نشطا داخل Microsoft 365 Lighthouse. لتحديد ما إذا كان المستأجر نشطا، راجع [نظرة عامة على صفحة Windows 365 (أجهزة الكمبيوتر السحابية) في Microsoft 365 Lighthouse](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>مراجعة المخاطر المكتشفة واتخاذ إجراء

في Azure AD Identity Protection، تتضمن عمليات الكشف عن المخاطر أي إجراءات مشبوهة محددة تتعلق بحسابات المستخدمين في Azure AD.

1. في جزء التنقل الأيمن في Lighthouse، حدد **"Users**".

2. حدد علامة التبويب **"المستخدمون المحفوفوفة بالمخاطر** ".

3. راجع المستخدمين في القائمة مع حالة الخطر **المعرضة للخطر**.

4. حدد **عرض عمليات الكشف عن المخاطر** للحصول على معلومات مفصلة حول المخاطر المكتشفة لكل مستخدم. لمزيد من المعلومات حول أنواع المخاطر والكشف، راجع [ما هي المخاطر؟](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. لكل مستخدم، قم بتقييم عمليات الكشف عن المخاطر وحدد أحد الإجراءات التالية، حسب الاقتضاء:

    - إعادة تعيين كلمة المرور – تغيير كلمة مرور المستخدم أو إعادة تعيينها.

    - حظر تسجيل الدخول - منع أي شخص من تسجيل الدخول بصفته هذا المستخدم.

    - تأكيد تعرض المستخدم للخطر – تعيين حالة الخطر إلى ما تم تأكيده من اختراق.

    - استبعاد مخاطر المستخدم - تعيين حالة الخطر إلى تجاهلها.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>اتخاذ إجراء بشأن حسابات مستخدمين متعددة في وقت واحد

لاتخاذ إجراء على عدة مستخدمين متأثرين في وقت واحد:

1. من علامة التبويب " **المستخدمون المحفوفوفة بالمخاطر** "، حدد مجموعة المستخدمين الذين تريد اتخاذ إجراء عليهم.

2. اختر أحد الإجراءات التالية لتنفيذها:

    - إعادة تعيين كلمة المرور

    - حظر تسجيل الدخول

    - تأكيد اختراق المستخدم

    - تجاهل مخاطر المستخدم

> [!NOTE]
> إذا كان لدى المؤسسة التي تديرها ترخيص P2 Azure AD Premium، فمن المستحسن تمكين نهج الوصول المشروط المستندة إلى المخاطر من قبل المستخدم. لمزيد من المعلومات، راجع [الوصول المشروط: الوصول المشروط المستند إلى مخاطر المستخدم](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>المحتويات ذات الصلة
[البرنامج التعليمي: استخدام عمليات الكشف عن المخاطر لتسجيل دخول المستخدم لتشغيل مصادقة متعددة العوامل Azure AD أو تغييرات كلمة المرور](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) (المقالة)\
[ما المقصود بالمخاطرة؟](/azure/active-directory/identity-protection/concept-identity-protection-risks) (مقال) /
[معالجة المخاطر وإلغاء حظر المستخدمين](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (مقالة)
