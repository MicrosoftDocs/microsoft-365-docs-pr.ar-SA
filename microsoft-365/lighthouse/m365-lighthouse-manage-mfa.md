---
title: إدارة المصادقة متعددة العوامل
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية إدارة المصادقة متعددة العوامل.
ms.openlocfilehash: 5ab430e464fb2d20f9a911818f9fd6cb077d849e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575100"
---
# <a name="manage-multifactor-authentication"></a>إدارة المصادقة متعددة العوامل

يساعد Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA) على حماية الوصول إلى البيانات والتطبيقات، وتوفير طبقة أمان أخرى باستخدام نموذج ثان من المصادقة. توفر علامة التبويب مصادقة متعددة العوامل معلومات مفصلة حول حالة تمكين المصادقة متعددة العوامل عبر المستأجرين. حدد أي مستأجر في القائمة لرؤية مزيد من التفاصيل لذلك المستأجر، بما في ذلك سياسات الوصول الشرطي التي تتطلب MFA التي تم تكوينها بالفعل والمستخدمين الذين لم يسجلوا بعد للحصول على MFA.

بالنسبة لعملاء الشركات الصغيرة والمتوسطة الحجم (SMB)، توصي Microsoft بتمكين [إعدادات](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) الأمان الافتراضية كحد أدنى. بالنسبة إلى السيناريوهات الأكثر تعقيدا، يمكنك استخدام ["الوصول الشرطي](/azure/active-directory/conditional-access/overview) " لتكوين سياسات معينة.

## <a name="before-you-begin"></a>قبل البدء

يجب أن يتم تقديم الشروط التالية قبل ظهور المستأجر في القائمة:

- يجب أن يكون لدى مستأجر العميل ترخيص Azure AD Premium لكل مستخدم. لمزيد من المعلومات حول التراخيص التي تدعم المصادقة متعددة العوامل، راجع ميزات وتراخيص [Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-licensing).

- يجب أن يكون مستأجر العميل نشطا ضمن Microsoft 365 المنارة. لمعرفة كيفية تحديد ما إذا كان المستأجر نشطا، راجع Microsoft 365 نظرة عامة حول قائمة [مستأجري المنارة](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>تمكين MFA لمستأجر

1. في جزء التنقل الأيسر في المنارة، حدد **المستخدمون**.

2. حدد علامة **التبويب مصادقة متعددة** العوامل.

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. على علامة **التبويب تمكين MFA** ، ضمن **MFA مع إعدادات الأمان الافتراضية**، حدد **تمكين إعدادات الأمان الافتراضية**.

5. حدد **حفظ التغييرات**.

لتمكين المصادقة متعددة العوامل من خلال الوصول الشرطي، راجع البرنامج التعليمي: تأمين أحداث تسجيل دخول المستخدم [باستخدام Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>إعلام المستخدمين غير المسجلين للحصول على MFA

1. في جزء التنقل الأيسر في المنارة، حدد **المستخدمون**.

2. حدد علامة **التبويب مصادقة متعددة** العوامل.

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. في علامة **التبويب مستخدم غير مسجل ل MFA** ، حدد المستخدمين الذين تريد إعلامهم.

5. حدد **إنشاء بريد إلكتروني**.

تفتح "المنارة" عميل البريد الإلكتروني الافتراضي وتنفر رسالة البريد الإلكتروني مع إرشادات للتسجيل في MFA. سيتم تضمين جميع المستخدمين المحددين في السطر "BCC". إذا كنت تفضل إرسال بريد إلكتروني فردي لمستخدمين، يمكنك تحديد أيقونة البريد الإلكتروني بجانب اسم المستخدم.

إذا كنت تريد استخدام حساب بريد إلكتروني آخر، يمكنك تصدير قائمة المستخدمين إلى ملف. يمكنك أيضا تنزيل نماذج قوالب البريد الإلكتروني التي يمكنك تخصيصها باستخدام العلامة التجارية للشركة.

## <a name="next-steps"></a>الخطوات التالية

بمجرد تمكين MFA، يمكنك تمكين Azure Active Directory (Azure AD) إعادة تعيين كلمة مرور الخدمة الذاتية. تمنح هذه الميزة المستخدمين القدرة على تغيير كلمة المرور أو إعادة تعيينها بدون مشاركة مسؤول أو مكتب مساعدة. لمزيد من المعلومات، راجع [إدارة إعادة تعيين كلمة مرور الخدمة الذاتية](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>المحتوى ذي الصلة

[تخطيط نشر مصادقة Azure Active Directory متعددة العوامل](/azure/active-directory/authentication/howto-mfa-getstarted) (مقالة)\
[ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (article)\
[ما هو الوصول الشرطي؟](/azure/active-directory/conditional-access/overview) (article)\
[تعرف على كيفية تحويل المستخدمين من MFA لكل مستخدم إلى وصول شرطي](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (مقالة)
