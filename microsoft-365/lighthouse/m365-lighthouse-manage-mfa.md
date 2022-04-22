---
title: إدارة المصادقة متعددة العوامل في Microsoft 365 Lighthouse
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
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية إدارة المصادقة متعددة العوامل.
ms.openlocfilehash: 53f1b0fa9a477ae74b48c96f76f9b2523fe45c10
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023184"
---
# <a name="manage-multifactor-authentication-in-microsoft-365-lighthouse"></a>إدارة المصادقة متعددة العوامل في Microsoft 365 Lighthouse

تساعد Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA) على حماية الوصول إلى البيانات والتطبيقات، ما يوفر طبقة أخرى من الأمان باستخدام نموذج ثان من المصادقة. توفر علامة التبويب "مصادقة متعددة العوامل" معلومات مفصلة حول حالة تمكين المصادقة متعددة العوامل عبر المستأجرين. حدد أي مستأجر في القائمة للاطلاع على مزيد من التفاصيل لهذا المستأجر، بما في ذلك نهج الوصول المشروط التي تتطلب المصادقة متعددة العوامل التي تم تكوينها بالفعل والمستخدمين الذين لم يسجلوا بعد للحصول على المصادقة متعددة العوامل.

بالنسبة لعملاء الشركات الصغيرة والمتوسطة الحجم (SMB)، توصي Microsoft بتمكين [إعدادات الأمان الافتراضية](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) كحد أدنى. للحصول على سيناريوهات أكثر تعقيدا، يمكنك استخدام [الوصول المشروط](/azure/active-directory/conditional-access/overview) لتكوين نهج معينة.

## <a name="before-you-begin"></a>قبل البدء

يجب استيفاء الشروط التالية قبل أن يظهر المستأجر في القائمة:

- يجب أن يكون لدى مستأجر العميل ترخيص Premium Azure AD لكل مستخدم. لمزيد من المعلومات حول التراخيص التي تدعم المصادقة متعددة العوامل، راجع [الميزات والتراخيص لمصادقة Azure AD متعددة العوامل](/azure/active-directory/authentication/concept-mfa-licensing).

- يجب أن يكون مستأجر العميل نشطا داخل Microsoft 365 Lighthouse. لمعرفة كيفية تحديد ما إذا كان المستأجر نشطا، راجع [Microsoft 365 نظرة عامة على قائمة مستأجر Lighthouse](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>تمكين المصادقة متعددة العوامل لمستأجر

1. في جزء التنقل الأيمن في Lighthouse، حدد **"Users**".

2. حدد علامة التبويب **"مصادقة متعددة العوامل** ".

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. في علامة التبويب **تمكين المصادقة** متعددة العوامل، ضمن **المصادقة متعددة العوامل مع إعدادات الأمان الافتراضية**، حدد **تمكين إعدادات الأمان الافتراضية**.

5. حدد **"حفظ التغييرات**".

لتمكين المصادقة متعددة العوامل من خلال الوصول المشروط، راجع [البرنامج التعليمي: تأمين أحداث تسجيل دخول المستخدم باستخدام Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>إعلام المستخدمين غير المسجلين في المصادقة متعددة العوامل

1. في جزء التنقل الأيمن في Lighthouse، حدد **"Users**".

2. حدد علامة التبويب **"مصادقة متعددة العوامل** ".

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. في علامة التبويب **"المستخدم" غير المسجل في المصادقة متعددة** العوامل، حدد المستخدمين الذين تريد إعلامهم.

5. حدد **إنشاء بريد إلكتروني**.

يفتح Lighthouse عميل البريد الإلكتروني الافتراضي الخاص بك ويملء رسالة البريد الإلكتروني مسبقا مع إرشادات للتسجيل في المصادقة متعددة العوامل. سيتم تضمين كافة المستخدمين المحددين في سطر نسخة مخفية. إذا كنت تفضل إرسال بريد إلكتروني لمستخدمي البريد الإلكتروني بشكل فردي، يمكنك تحديد أيقونة البريد الإلكتروني إلى جانب اسم المستخدم.

إذا كنت تريد استخدام حساب بريد إلكتروني آخر، يمكنك تصدير قائمة المستخدمين إلى ملف. يمكنك أيضا تنزيل نماذج قوالب البريد الإلكتروني التي يمكنك تخصيصها باستخدام العلامة التجارية للشركة.

## <a name="next-steps"></a>الخطوات التالية

بمجرد تمكين المصادقة متعددة العوامل، يمكنك تمكين إعادة تعيين كلمة مرور الخدمة الذاتية ل Azure Active Directory (Azure AD). تمنح هذه الميزة المستخدمين القدرة على تغيير كلمة المرور الخاصة بهم أو إعادة تعيينها دون مشاركة المسؤول أو مكتب المساعدة. لمزيد من المعلومات، راجع [إدارة إعادة تعيين كلمة مرور الخدمة الذاتية في Microsoft 365 Lighthouse](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[تخطيط نشر Azure Active Directory Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-getstarted) (article)\
[ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (مقالة)\
[ما هو الوصول المشروط؟](/azure/active-directory/conditional-access/overview) (مقالة)\
[تعرف على كيفية تحويل المستخدمين من المصادقة متعددة العوامل لكل مستخدم إلى الوصول المشروط](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (مقالة)
