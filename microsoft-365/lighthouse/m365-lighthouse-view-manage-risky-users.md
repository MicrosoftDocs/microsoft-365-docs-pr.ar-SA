---
title: عرض المستخدمين الخطرين وإدارتهم
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية عرض المستخدمين الخطرين وإدارتهم.
ms.openlocfilehash: 708fc0576c85d9b8511ac6b31ed0398fae1b20d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704913"
---
# <a name="view-and-manage-risky-users"></a>عرض المستخدمين الخطرين وإدارتهم

تجمع Microsoft كل يوم الكثير من إشارات تسجيل الدخول الخاصة بمستخدم وتحللها. يتم استخدام هذه الإشارات للمساعدة في إنشاء أنماط سلوك تسجيل الدخول الجيدة للمستخدم وتحديد محاولات تسجيل الدخول المحتملة والمجازفة. يستخدم Azure Active Directory (Azure AD) Identity Protection هذه الإشارات لمراجعة محاولات تسجيل الدخول من قبل المستخدم واتخاذ إجراء إذا كان هناك نشاط مريب.

Microsoft 365 المنارة على إدارة المخاطر التي يكشف عنها Azure AD Identity Protection من خلال توفير طريقة عرض واحدة للمستخدمين الخطرين عبر جميع المستأجرين المدارين. يمكنك بسرعة تأمين المستخدمين الخطرين عن طريق إعادة تعيين كلمة المرور الخاصة بهم أو منعهم من تسجيل الدخول إلى Microsoft 365 الخاص بهم. يمكنك أيضا عرض نتائج تحليلات لفهم مخاطر المستخدم بشكل أفضل وتحديد الخطوات التالية.

تحدد Azure AD Identity Protection المخاطر لأنواع متعددة، بما في ذلك:

- بيانات الاعتماد التي تم تسريبها
- استخدام IP مجهول
- السفر غير المتنقل
- تسجيل الدخول من الأجهزة المصابة
- تسجيل الدخول من عناوين IP باستخدام نشاط مريب
- تسجيل الدخول من مواقع غير مألوفة

## <a name="before-you-begin"></a>قبل البدء

يجب أن يتم الحصول على الشروط التالية قبل ظهور المستخدمين في قائمة المستخدمين الخطرين:

- يجب أن يكون لدى مستأجر العميل ترخيص Azure AD Premium لكل مستخدم. لمزيد من المعلومات حول التراخيص التي تدعم Azure AD Identity Protection، راجع [ما هي حماية الهوية؟](/azure/active-directory/identity-protection/overview-identity-protection)

- يجب أن يكون مستأجر العميل نشطا ضمن Microsoft 365 المنارة. لتحديد ما إذا كان المستأجر نشطا، راجع Microsoft 365 نظرة عامة على صفحة [مستأجري المنارة](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>مراجعة المخاطر التي تم الكشف عنها واتخاذ إجراء

في Azure AD Identity Protection، تتضمن اكتشافات المخاطر أي إجراءات مريبة محددة ذات صلة وحسابات المستخدمين في Azure AD.

1. في جزء التنقل الأيسر في المنارة، حدد **المستخدمون**.

2. حدد علامة **التبويب المستخدمون الخطرون** .

3. راجع المستخدمين في القائمة مع حالة الخطر **المعرضة للمخاطر**.

4. حدد **عرض الكشف عن المخاطر** للحصول على معلومات مفصلة حول المخاطر التي يتم الكشف عنها لكل مستخدم. لمزيد من المعلومات حول أنواع المخاطر والكشف عنها، راجع [ما هي المخاطر؟](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. لكل مستخدم، قم بتقييم الكشف عن المخاطر وحدد أحد الإجراءات التالية، حسب الاقتضاء:

    - إعادة تعيين كلمة المرور – تغيير كلمة مرور المستخدم أو إعادة تعيينها.

    - حظر تسجيل الدخول - منع أي شخص من تسجيل الدخول بهذا المستخدم.

    - تأكيد اختراق المستخدم – تعيين حالة الخطر إلى تأكيد اختراق.

    - تجاهل مخاطر المستخدم - تعيين حالة الخطر إلى استبعاد.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>اتخاذ إجراء على حسابات مستخدمين متعددة في وقت واحد

لاتخاذ إجراء على عدة مستخدمين متأثرين في وقت واحد:

1. من علامة **التبويب المستخدمون** الخطرون، حدد مجموعة المستخدمين الذين تريد اتخاذ إجراء بشأنهم.

2. اختر أحد الإجراءات التالية لتنفيذ:

    - إعادة تعيين كلمة المرور

    - حظر تسجيل الدخول

    - تأكيد اختراق المستخدم

    - تجاهل مخاطر المستخدم

> [!NOTE]
> إذا كانت المؤسسة التي تديرها لديها ترخيص Azure AD Premium P2، فمن المستحسن تمكين سياسات الوصول الشرطي المستندة إلى مخاطر المستخدم. لمزيد من المعلومات، راجع [الوصول الشرطي: الوصول الشرطي المستند إلى مخاطر المستخدم](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>المحتوى ذي الصلة
[البرنامج التعليمي: استخدام الكشف عن المخاطر لادراج المستخدمين في تسجيل الدخول إلى تشغيل Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) أو تغييرات كلمة المرور (مقالة)\
[ما هي المخاطر؟](/azure/active-directory/identity-protection/concept-identity-protection-risks) (article) \
[إصلاح المخاطر و إلغاء حظر المستخدمين](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (مقالة)
