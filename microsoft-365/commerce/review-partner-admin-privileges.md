---
title: مراجعة الامتيازات الإدارية الشريكة
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
search.appverid: MET150
description: تعرف على كيفية مراجعة قائمة موفري الحلول المعتمدين من Microsoft (الشركاء) لتحديد امتيازات المسؤول التي لديهم، وكيفية إزالة هذه الامتيازات.
ms.date: 12/03/2021
ms.openlocfilehash: 067716689bd82e67dda357d675383ef2541b1dc3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63580002"
---
# <a name="review-partner-administrative-privileges"></a>مراجعة الامتيازات الإدارية الشريكة

إذا كان لديك موفر حلول سحابية معتمد من Microsoft (شريك بائع)، نوصي بإجراء مراجعة ربعية للامتيازات الإدارية المفوضة (DAP) المعينة له. تأكد من أن مؤسستك تريد أن يكون لهذا الشريك حق الوصول إلى بيانات مؤسستك وأن يجري عمليات شراء بالنيابة عنك.

> [!IMPORTANT]
> قد يكون منح DAP، الذي يتضمن أذونات المسؤول العام، لأي شريك خطرا على الأمان. كما أن وجود عدد كبير جدا من المسؤولين العامين هو أيضا خطر على الأمان. [تعرف على المزيد حول النشاط الأخير الذي يستهدف الامتيازات المفوضة](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

بعد قبول اتفاقية DAP من أحد شركاء البائعين، يمكنهم تعيين دور المسؤول العام لمنظمتك لموظفيهم. يمنح دور المسؤول العام موظفي الشريك حق الوصول إلى البيانات الشخصية الخاصة بالموظفين والمعلومات الحساسة الأخرى. كما يمنحهم الإذن لاتخاذ إجراءات على مستوى المستأجر، مثل الإجراءات التالية:

- تغيير كلمات مرور المستخدمين
- إضافة مستخدمين باستخدام حسابات البريد الإلكتروني
- إضافة مجالات ويب المقترنة بمنظمتك وإدارتها

عند تمكين DAP، لن يكون لديك أي تحكم في عدد المسؤولين العامين الذين يمكن لشريكك إضافتهم. يمكنك فقط منح الشريك DAP (المسؤول العام) حق الوصول إلى حسابك أو رفضه.

## <a name="review-and-remove-roles-from-partners"></a>مراجعة الأدوار وإزالتها من الشركاء

1. في مركز مسؤولي Microsoft 365، انتقل **إلى صفحة** >  علاقات الإعدادات <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partner</a>. لدى الشركاء في DAP **"المسؤول العام** " مدرج **في عمود "** الأدوار".
2. لإزالة دور المسؤول العام من شريك، ابحث عن اسم الشريك الذي تريد إزالته.
3. حدد الصف الذي به **بائع كنوع** **العلاقة**.
4. في صفحة تفاصيل الشريك، حدد **إزالة الأدوار**، ثم حدد **نعم**.

> [!NOTE]
>
> - إذا قمت بإزالة DAP (دور المسؤول العام) من شريك، نوصي بالاتصال به لمناقشة تسليم الخدمة في المستقبل. على سبيل المثال، يمكنك إنشاء حساب مستخدم بامتيازات أقل ومشاركة معلومات الحساب هذه مع شريكك. تعرف على المزيد [حول إضافة مستخدمين](../admin/add-users/add-users.md) [وتعيين أدوار المسؤولين](../admin/add-users/assign-admin-roles.md).
> - حتى مع إزالة دور المسؤول العام، لا يزال با با الممكن أن يجري الشريك عمليات شراء بالنيابة عنك. نوصي بالاتصال الشريك لمطالبته بإزالة هذه القدرة في مركز الشركاء.

## <a name="related-content"></a>المحتوى ذي الصلة

[إدارة علاقات الشريك](manage-partners.md) (مقالة)\
[حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md) (مقالة)\
[امتيازات المسؤول المفوض في Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (مقالة)
