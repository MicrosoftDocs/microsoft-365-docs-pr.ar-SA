---
title: إدارة إعادة تعيين كلمة مرور الخدمة الذاتية
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية إدارة إعادة تعيين كلمة مرور الخدمة الذاتية.
ms.openlocfilehash: f9f8ef9a3c81281629c378fb4b55cd4c9a839c1d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572031"
---
# <a name="manage-self-service-password-reset"></a>إدارة إعادة تعيين كلمة مرور الخدمة الذاتية

Microsoft 365 Lighthouse للشركاء بإدارة Azure Active Directory (Azure AD) إعادة تعيين كلمة مرور الخدمة الذاتية (SSPR). يمنح SSPR المستخدمين القدرة على تغيير كلمة المرور أو إعادة تعيينها بدون مشاركة مسؤول أو مكتب مساعدة. إذا تم تأمين حساب مستخدم أو نسيان كلمة المرور الخاصة به، يمكنه اتباع المطالبات  إلغاء حظر نفسه ثم العودة إلى العمل. تقلل هذه القدرة من مكالمات مكتب المساعدة وفقدان الإنتاجية عندما لا يستطيع المستخدم تسجيل الدخول إلى جهازه أو تطبيق.

## <a name="before-you-begin"></a>قبل البدء

يجب أن يتم تقديم الشروط التالية قبل ظهور المستأجر في القائمة:

- يجب أن يكون لدى مستأجر العميل ترخيص Azure AD Premium لكل مستخدم. لمزيد من المعلومات حول التراخيص التي تدعم SSPR، راجع متطلبات الترخيص لإعادة تعيين كلمة مرور الخدمة الذاتية ل [Azure Active Directory](/azure/active-directory/authentication/concept-sspr-licensing).

- يجب أن يكون مستأجر العميل نشطا داخل "المنارة". لمعرفة كيفية تحديد ما إذا كان المستأجر نشطا، راجع Microsoft 365 نظرة عامة على صفحة [مستأجري المنارة](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>عرض حالة مستأجر SSPR

1. في جزء التنقل الأيسر من المنارة، حدد **المستخدمون**.

2. حدد علامة **التبويب إعادة تعيين كلمة** المرور.

توفر علامة التبويب إعادة تعيين كلمة المرور نظرة عامة حول المستأجرين الذين مكنوا SSPR من خلال الإعدادات الموصى بها، وعدد المستخدمين الذين لم يسجلوا ل SSPR، و تصنيف تفصيلي حسب نطاق تقدم نشر SSPR عبر المؤسسات التي تديرها.

## <a name="enable-sspr-for-a-tenant"></a>تمكين SSPR لمستأجر

1. في جزء التنقل الأيسر في المنارة، حدد **المستخدمون**.

2. حدد علامة **التبويب إعادة تعيين كلمة** المرور.

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. حدد **تحرير إعدادات SSPR في Azure Active Directory** الانتقال إلى Azure Active Directory (Azure AD).

5. في Azure AD، قم بتمكين SSPR لجميع المستخدمين أو المستخدمين المحددين. لمعرفة المزيد، راجع البرنامج التعليمي: تمكين المستخدمين من إلغاء تأمين حسابهم أو إعادة تعيين كلمات المرور باستخدام إعادة تعيين كلمة مرور الخدمة الذاتية ل [Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>إعلام المستخدمين بالتسجيل في SSPR

1. في جزء التنقل الأيسر في المنارة، حدد **المستخدمون**.

2. حدد علامة **التبويب إعادة تعيين كلمة** المرور.

3. من قائمة المستأجرين، حدد مستأجرا لفتح جزء التفاصيل.

4. حدد المستخدمين الذين تريد إعلامهم.

5. حدد **إنشاء بريد إلكتروني**.

تفتح "المنارة" عميل البريد الإلكتروني الافتراضي وتنفر رسالة البريد الإلكتروني بشكل مسبق مع إرشادات للتسجيل في SSPR. سيتم تضمين جميع المستخدمين المحددين في السطر "BCC". إذا كنت تفضل إرسال بريد إلكتروني فردي لمستخدمين، يمكنك تحديد أيقونة البريد الإلكتروني بجانب اسم المستخدم.

إذا كنت تريد استخدام حساب بريد إلكتروني آخر، يمكنك تصدير قائمة المستخدمين إلى ملف. يمكنك أيضا تنزيل نماذج قوالب البريد الإلكتروني التي يمكنك تخصيصها باستخدام العلامة التجارية للشركة.

## <a name="related-content"></a>المحتوى ذي الصلة

التخطيط لنشر إعادة تعيين كلمة مرور الخدمة الذاتية ل [Azure Active Directory](/azure/active-directory/authentication/howto-sspr-deployment) (مقالة)\
[البرنامج التعليمي: تمكين المستخدمين من إلغاء تأمين حسابهم أو إعادة تعيين كلمات المرور باستخدام خدمة Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr) الذاتية إعادة تعيين كلمة المرور (مقالة)\
[كيفية تمكين SSPR وتكوينه في Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (فيديو)\
[إدارة المصادقة متعددة العوامل](m365-lighthouse-manage-mfa.md) (مقالة)
