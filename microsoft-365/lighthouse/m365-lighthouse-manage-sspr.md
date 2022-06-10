---
title: إدارة إعادة تعيين كلمة مرور الخدمة الذاتية في Microsoft 365 Lighthouse
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
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية إدارة إعادة تعيين كلمة مرور الخدمة الذاتية.
ms.openlocfilehash: 0af624e93ae9321834e147f829a87f09c36dedf7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017665"
---
# <a name="manage-self-service-password-reset-in-microsoft-365-lighthouse"></a>إدارة إعادة تعيين كلمة مرور الخدمة الذاتية في Microsoft 365 Lighthouse

يتيح Microsoft 365 Lighthouse للشركاء إدارة Azure Active Directory (Azure AD) إعادة تعيين كلمة مرور الخدمة الذاتية (SSPR). يمنح SSPR المستخدمين القدرة على تغيير كلمة المرور الخاصة بهم أو إعادة تعيينها دون مشاركة المسؤول أو مكتب المساعدة. إذا تم تأمين حساب المستخدم أو نسي كلمة المرور الخاصة به، يمكنه اتباع المطالبات لإلغاء حظر نفسه والعودة إلى العمل. تقلل هذه القدرة من مكالمات مكتب المساعدة وفقدان الإنتاجية عندما لا يتمكن المستخدم من تسجيل الدخول إلى جهازه أو تطبيق.

## <a name="before-you-begin"></a>قبل البدء

يجب استيفاء الشروط التالية قبل أن يظهر المستأجر في القائمة:

- يجب أن يكون لدى مستأجر العميل ترخيص Azure AD Premium لكل مستخدم. لمزيد من المعلومات حول التراخيص التي تدعم إعادة تعيين كلمة [مرور الخدمة الذاتية، راجع متطلبات الترخيص لإعادة تعيين كلمة مرور الخدمة الذاتية ل Azure Active Directory](/azure/active-directory/authentication/concept-sspr-licensing).

- يجب أن يكون مستأجر العميل نشطا داخل Lighthouse. لمعرفة كيفية تحديد ما إذا كان المستأجر نشطا، راجع [نظرة عامة على صفحة Windows 365 (أجهزة الكمبيوتر السحابية) في Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>عرض حالة مستأجر SSPR

1. في جزء التنقل الأيمن من Lighthouse، حدد **"Users**".

2. حدد علامة التبويب **"إعادة تعيين كلمة المرور** ".

توفر علامة التبويب "إعادة تعيين كلمة المرور" نظرة عامة على المستأجرين الذين قاموا بتمكين إعادة تعيين كلمة مرور الخدمة الذاتية من خلال الإعدادات الموصى بها، وعدد المستخدمين الذين لم يسجلوا إعادة تعيين كلمة مرور الخدمة الذاتية، وتفصيل تفصيلي حسب المستأجر لتقدم نشر إعادة تعيين كلمة مرور الخدمة الذاتية عبر المؤسسات التي تديرها.

## <a name="enable-sspr-for-a-tenant"></a>تمكين إعادة تعيين كلمة مرور الخدمة الذاتية لمستأجر

1. في جزء التنقل الأيمن في Lighthouse، حدد **"Users**".

2. حدد علامة التبويب **"إعادة تعيين كلمة المرور** ".

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. حدد **تحرير إعدادات إعادة تعيين كلمة مرور الخدمة الذاتية في Azure Active Directory** للانتقال إلى Azure Active Directory (Azure AD).

5. في Azure AD، قم بتمكين إعادة تعيين كلمة مرور الخدمة الذاتية لجميع المستخدمين أو المستخدمين المحددين. لمعرفة المزيد، راجع [البرنامج التعليمي: تمكين المستخدمين من إلغاء تأمين حساباتهم أو إعادة تعيين كلمات المرور باستخدام إعادة تعيين كلمة مرور الخدمة الذاتية ل Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>إعلام المستخدمين بالتسجيل في إعادة تعيين كلمة مرور الخدمة الذاتية

1. في جزء التنقل الأيمن في Lighthouse، حدد **"Users**".

2. حدد علامة التبويب **"إعادة تعيين كلمة المرور** ".

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. حدد المستخدمين الذين تريد إعلامهم.

5. حدد **إنشاء بريد إلكتروني**.

يفتح Lighthouse عميل البريد الإلكتروني الافتراضي الخاص بك ويملء رسالة البريد الإلكتروني مسبقا مع إرشادات للتسجيل في إعادة تعيين كلمة مرور الخدمة الذاتية. سيتم تضمين كافة المستخدمين المحددين في سطر نسخة مخفية. إذا كنت تفضل إرسال بريد إلكتروني لمستخدمي البريد الإلكتروني بشكل فردي، يمكنك تحديد أيقونة البريد الإلكتروني إلى جانب اسم المستخدم.

إذا كنت تريد استخدام حساب بريد إلكتروني آخر، يمكنك تصدير قائمة المستخدمين إلى ملف. يمكنك أيضا تنزيل نماذج قوالب البريد الإلكتروني التي يمكنك تخصيصها باستخدام العلامة التجارية للشركة.

## <a name="related-content"></a>المحتويات ذات الصلة

[تخطيط نشر إعادة تعيين كلمة مرور الخدمة الذاتية ل Azure Active Directory](/azure/active-directory/authentication/howto-sspr-deployment) (مقالة)\
[البرنامج التعليمي: تمكين المستخدمين من إلغاء تأمين حساباتهم أو إعادة تعيين كلمات المرور باستخدام إعادة تعيين كلمة مرور الخدمة الذاتية ل Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr) (المقالة)\
[كيفية تمكين SSPR وتكوينه في Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (فيديو)\
[إدارة المصادقة متعددة العوامل في Microsoft 365 Lighthouse](m365-lighthouse-manage-mfa.md) (مقالة)
