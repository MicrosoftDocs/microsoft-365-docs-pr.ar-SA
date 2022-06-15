---
title: إدارة اشتراكات تسجيل الخدمة الذاتية
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid: MET150
description: تعرف على كيفية إدارة اشتراكات تسجيل الخدمة الذاتية المجانية لمؤسستك.
ms.date: 03/17/2021
ms.openlocfilehash: 58c58c849b72c170e0ccf10de54389bd1245bced
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102339"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>إدارة اشتراكات تسجيل الخدمة الذاتية

## <a name="what-are-self-service-sign-up-subscriptions"></a>ما هي اشتراكات تسجيل الخدمة الذاتية؟

هناك عدد محدود من اشتراكات التسجيل الذاتي المجانية المتوفرة للمستخدمين في مؤسستك للتسجيل فيها. يمكن للمستخدم التسجيل في اشتراك تسجيل الخدمة الذاتية واستخدامه فقط لأنفسهم. يمكنك إدارة اشتراكات تسجيل الخدمة الذاتية عن طريق حظر المستخدمين من التسجيل، ومن خلال حذف الاشتراكات المجانية التي قام المستخدمون بالتسجيل فيها. لمزيد من المعلومات حول التسجيل في الخدمة الذاتية والاشتراكات المتوفرة، راجع [استخدام تسجيل الخدمة الذاتية في مؤسستك](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>عرض قائمة باشتراكات تسجيل الخدمة الذاتية

1. في مركز الإدارة، انتقل إلى صفحة **الفاتورة** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">المنتجات والخدمات</a>.
2. في علامة التبويب **"المنتجات** "، حدد أيقونة عامل التصفية، ثم حدد **"حر**". يتم عرض قائمة بجميع اشتراكات تسجيل الخدمة الذاتية.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>كيف تختلف هذه الاشتراكات عن اشتراكات شراء الخدمة الذاتية؟

اشتراكات تسجيل الخدمة الذاتية مجانية ومتاحة لقائمة منتجات أكبر من اشتراكات شراء الخدمة الذاتية. عندما يقوم المستخدم بالتسجيل للحصول على اشتراك شراء الخدمة الذاتية، يكون مسؤولا عن الدفع مقابل ذلك. تتوفر اشتراكات شراء الخدمة الذاتية فقط لمنتجات Power Platform (Power BI وPower Apps Power Automate) Project Visio. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول شراء الخدمة الذاتية](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>حظر المستخدمين من التسجيل

يمكنك استخدام [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) cmdlet مع المعلمة **AllowAdHocSubscriptions** للتحكم في ما إذا كان يمكن للمستخدمين التسجيل للحصول على اشتراكات تسجيل الخدمة الذاتية. لمزيد من المعلومات، راجع [كيف أعمل التحكم في إعدادات الخدمة الذاتية؟](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>حذف اشتراك تسجيل الخدمة الذاتية

> [!IMPORTANT]
> عند حذف اشتراك تسجيل الخدمة الذاتية، فإنك تمنع جميع المستخدمين من الوصول إلى بياناتهم وبريدهم الإلكتروني وحذف جميع البيانات والبريد الإلكتروني.

1. في مركز الإدارة، انتقل إلى صفحة **الفاتورة** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">المنتجات والخدمات</a>.
2. في علامة التبويب **"المنتجات** "، حدد أيقونة عامل التصفية، ثم حدد **"حر**".
3. حدد اشتراك تسجيل الخدمة الذاتية الذي تريد حذفه. 
4. في صفحة تفاصيل الاشتراك، في قسم **إعدادات الاشتراكات والدفع** ، حدد **حذف الاشتراك**.
5. في جزء **«Delete subscription** »، حدد خانة الاختيار، ثم حدد **«Delete subscription**».

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>لدي اشتراك تسجيل الخدمة الذاتية الذي يمنع حذف الدليل

منتجات تسجيل الخدمة الذاتية التي يمكن للمستخدمين الفرديين التسجيل للحصول عليها أيضا إنشاء مستخدم ضيف للمصادقة في دليل Azure AD الخاص بك. لتجنب فقدان البيانات، تحظر منتجات الخدمة الذاتية هذه حذف الدليل حتى يتم حذفها بالكامل من الدليل. يمكن حذفها فقط من قبل مسؤول Azure AD. لمزيد من المعلومات، راجع [حذف دليل في Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
