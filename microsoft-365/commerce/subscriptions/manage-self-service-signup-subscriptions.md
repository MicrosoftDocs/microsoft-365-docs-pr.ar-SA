---
title: إدارة اشتراكات التسجيل الذاتي للخدمة
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
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
description: تعرف على كيفية إدارة اشتراكات التسجيل الذاتي المجانية لمنظمتك.
ms.date: 03/17/2021
ms.openlocfilehash: be93a09ca63a4ee24945438be59b725e7d41911c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567433"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>إدارة اشتراكات التسجيل الذاتي للخدمة

## <a name="what-are-self-service-sign-up-subscriptions"></a>ما هي اشتراكات التسجيل الذاتي للخدمة؟

يتوفر عدد محدود من اشتراكات التسجيل الذاتي المجانية المتوفرة للمستخدمين في مؤسستك للاشتراك فيها. يمكن للمستخدم التسجيل فقط للحصول على اشتراك تسجيل الخدمة الذاتية واستخدامه لنفسه. يمكنك إدارة اشتراكات التسجيل ذاتية الخدمة من خلال منع المستخدمين من التسجيل، وحذف الاشتراكات المجانية التي سجل المستخدمون للحصول عليها. لمزيد من المعلومات حول التسجيل الذاتي للخدمة والاشتراكات المتوفرة، راجع [استخدام تسجيل الخدمة الذاتية في مؤسستك](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>عرض قائمة باشتراكات التسجيل الذاتي للخدمة

1. في مركز الإدارة، انتقل إلى **صفحة منتجات BillingYour** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>
2. على علامة **التبويب** المنتجات، حدد أيقونة عامل التصفية، ثم حدد **مجاني**. يتم عرض قائمة بكل اشتراكات التسجيل ذاتية الخدمة.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>كيف تختلف هذه الاشتراكات عن اشتراكات شراء الخدمة الذاتية؟

إن اشتراكات التسجيل الذاتي الخدمة مجانية ومتوفرة لقائمة أكبر من المنتجات مقارنة باشتراكات شراء الخدمة الذاتية. عندما يقوم المستخدم التسجيل للحصول على اشتراك شراء الخدمة الذاتية، يكون مسؤولا عن دفع ثمنه. لا تتوفر اشتراكات شراء الخدمة الذاتية إلا لمنتجات Power Platform (Power BI و Power Apps و Power Automate) Project و Visio. لمزيد من المعلومات، راجع [الأسئلة الشائعة حول شراء الخدمة الذاتية](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>حظر المستخدمين من التسجيل

يمكنك استخدام [**الأمر cmdlet Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) مع المعلمة **AllowAdHocSubscriptions** للتحكم في ما إذا كان يمكن للمستخدمين التسجيل للحصول على اشتراكات التسجيل الذاتي للخدمة. لمزيد من المعلومات، [راجع كيف يمكنني التحكم في إعدادات الخدمة الذاتية؟](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>حذف اشتراك تسجيل الخدمة الذاتية

> [!IMPORTANT]
> عندما تحذف اشتراك تسجيل خدمة ذاتية، ستحظر جميع المستخدمين من الوصول إلى بياناتهم ورسائل البريد الإلكتروني الخاصة بهم وحذف كل البيانات والبريد الإلكتروني.

1. في مركز الإدارة، انتقل إلى **صفحة منتجات BillingYour** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>
2. على علامة **التبويب** المنتجات، حدد أيقونة عامل التصفية، ثم حدد **مجاني**.
3. حدد اشتراك التسجيل الذاتي للخدمة الذي تريد حذفه. 
4. في صفحة تفاصيل الاشتراك، في المقطع **الاشتراكات وإعدادات الدفع** ، حدد **حذف الاشتراك**.
5. في جزء **حذف الاشتراك** ، حدد خانة الاختيار، ثم حدد **حذف الاشتراك**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>لدي اشتراك تسجيل خدمة ذاتية يمنع حذف الدليل

تقوم أيضا منتجات التسجيل الذاتي الخدمة التي يمكن للمستخدمين الفرديين التسجيل فيها بإنشاء مستخدم ضيف للمصادقة في دليل Azure AD. لتجنب فقدان البيانات، تقوم منتجات الخدمة الذاتية هذه بحظر عمليات حذف الدليل حتى يتم حذفها بالكامل من الدليل. يمكن حذفها فقط من قبل مسؤول Azure AD. لمزيد من المعلومات، راجع [حذف دليل في Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
