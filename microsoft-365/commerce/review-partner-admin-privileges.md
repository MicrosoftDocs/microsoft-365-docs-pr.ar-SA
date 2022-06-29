---
title: مراجعة الامتيازات الإدارية للشركاء
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
description: تعرف على كيفية مراجعة قائمة موفري الحلول المعتمدين من Microsoft (الشركاء) لتحديد امتيازات المسؤول لديهم، وكيفية إزالة هذه الامتيازات.
ms.date: 12/03/2021
ms.openlocfilehash: eefbe2c8b70afee9c1e24e4335a73488906bf844
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490686"
---
# <a name="review-microsoft-certified-cloud-solution-provider-partner-administrative-privileges"></a>مراجعة الامتيازات الإدارية لشريك موفر حلول السحابة المعتمد من Microsoft

إذا كان لديك موفر حلول سحابية معتمد من Microsoft (شريك بائع)، نوصي بإجراء مراجعة ربع سنوية للامتيازات الإدارية المفوضة (DAP) المعينة لهم. تأكد من أن مؤسستك تريد أن يتمكن هذا الشريك من الوصول إلى بيانات مؤسستك وإجراء عمليات شراء بالنيابة عنك.

> [!IMPORTANT]
> قد يمثل منح DAP، الذي يتضمن أذونات المسؤول العمومي، لأي شريك خطرا أمنيا. يعد وجود عدد كبير جدا من المسؤولين العموميين أيضا خطرا أمنيا. [تعرف على المزيد حول النشاط الأخير الذي يستهدف الامتيازات المفوضة](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

بعد قبول اتفاقية DAP من شريك موزع، يمكنهم تعيين دور المسؤول العام لمؤسستك لموظفيهم. يمنح دور المسؤول العام موظفي الشريك حق الوصول إلى البيانات الشخصية لموظفيك والمعلومات الحساسة الأخرى. كما أنه يمنحهم الإذن لاتخاذ إجراءات على مستوى المستأجر، مثل الإجراءات التالية:

- تغيير كلمات مرور المستخدم
- إضافة مستخدمين باستخدام حسابات البريد الإلكتروني
- إضافة مجالات ويب المقترنة بمؤسستك وإدارتها

عند تمكين DAP، لا يكون لديك أي تحكم في عدد المسؤولين العموميين الذين يمكن لشريكك إضافتهم. يمكنك فقط منح الشريك DAP (المسؤول العام) حق الوصول إلى حسابك أو رفضه.

## <a name="review-and-remove-roles-from-partners"></a>مراجعة الأدوار وإزالتها من الشركاء

1. في مركز مسؤولي Microsoft 365، انتقل إلى الصفحة **"إعدادات** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">علاقات الشركاء</a>". لدى الشركاء الذين لديهم DAP **"مسؤول عمومي** " مدرج في عمود **"Roles** ".
2. لإزالة دور المسؤول العمومي من شريك، ابحث عن اسم الشريك الذي تريد إزالته.
3. حدد الصف الذي يحتوي **على البائع** **كنوع العلاقة**.
4. في صفحة تفاصيل الشريك، حدد **"إزالة الأدوار**"، ثم حدد **"نعم**".

> [!NOTE]
>
> - إذا قمت بإزالة DAP (دور المسؤول العام) من شريك، نوصي بالاتصال به لمناقشة تسليم الخدمة في المستقبل. على سبيل المثال، يمكنك إنشاء حساب مستخدم بامتيازات أقل ومشاركة معلومات الحساب هذه مع شريكك. تعرف على المزيد حول [إضافة المستخدمين](../admin/add-users/add-users.md) [وتعيين أدوار المسؤولين](../admin/add-users/assign-admin-roles.md).
> - حتى مع إزالة دور المسؤول العمومي، لا يزال بإمكان الشريك إجراء عمليات شراء بالنيابة عنك. نوصي بالاتصال بالشريك لمطالبته بإزالة هذه القدرة في مركز الشركاء.

## <a name="related-content"></a>المحتوى ذو الصلة

[إدارة علاقات الشركاء](manage-partners.md) (مقالة)\
[حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md) (مقالة)\
[امتيازات المسؤول المفوض في Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (مقالة)
