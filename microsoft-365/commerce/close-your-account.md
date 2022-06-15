---
title: إغلاق حسابك
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
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
- fwlink 2133922 to Delete subscription heading
- AdminTemplateSet
search.appverid: MET150
description: عند إغلاق حسابك باستخدام Microsoft، يتم حذف كل المعلومات المتعلقة بحسابك بما في ذلك التراخيص والمستخدمين وبيانات المستخدم.
ms.date: 04/02/2021
ms.openlocfilehash: c036a4cda929d58265a088b15a43772caacb0b94
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102449"
---
# <a name="close-your-account"></a>إغلاق حسابك

عند إغلاق حسابك في Microsoft، ستُحذف كل المعلومات المتعلقة بحسابك. تتضمن هذه المعلومات الاشتراكات والتراخيص وطرق الدفع والمستخدمين وبياناتهم.

## <a name="before-you-begin"></a>قبل البدء

قبل بدء تلك العملية، تأكد من إعدادك نسخة احتياطية لأي بيانات تريد حفظها.

يجب الحصول على صلاحيات المسؤول العمومي أو مسؤول الفوترة لتنفيذ المهام في هذه المقالة. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>الخطوة 1: حذف المستخدمين

حذف كافة المستخدمين باستثناء مسؤول عمومي واحد. يكمل المسؤول العام الخطوات لإغلاق الحساب. قبل أن تتمكن من حذف الدليل في نهاية هذه العملية، يجب حذف كافة المستخدمين الآخرين.

إذا تمت مزامنة المستخدمين من الموقع المحلي، فأوقف تشغيل المزامنة أولا، ثم احذف المستخدمين في دليل السحابة باستخدام مدخل Azure أو أوامر Cmdlets Azure PowerShell.

لحذف المستخدمين، راجع [مسؤول إدارة المستخدمين: حذف مستخدم واحد أو أكثر](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

يمكنك أيضا استخدام [Cmdlet Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell لحذف المستخدمين بشكل مجمع.

إذا كانت مؤسستك تستخدم Active Directory الذي يتزامن مع Microsoft Azure Active Directory (Azure AD)، فاحذف حساب المستخدم من Active Directory، بدلا من ذلك. للحصول على الإرشادات، راجع [حذف المستخدمين بشكل مجمع في Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>الخطوة 2: إلغاء كافة الاشتراكات النشطة

1. في مركز الإدارة، انتقل إلى صفحة **الفاتورة** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">المنتجات والخدمات</a>.
2. في علامة التبويب **"المنتجات** "، ابحث عن اشتراك نشط. حدد النقاط الثلاث (إجراءات إضافية)، ثم حدد **إلغاء الاشتراك**.
3. في جزء **إلغاء الاشتراك**، اختر سبباً لإلغاء الاشتراك. اختيارياً، قدّم أي ملاحظات.
4. حدد **حفظ**.
5. كرر الخطوات من 1 إلى 4 لإلغاء كافة الاشتراكات النشطة.

## <a name="step-3-delete-all-disabled-subscriptions"></a>الخطوة 3: حذف كافة الاشتراكات المعطلة

1. في مركز الإدارة، انتقل إلى صفحة **الفاتورة** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">المنتجات والخدمات</a>.
2. في علامة التبويب **"المنتجات** "، حدد اشتراكا معطلا.
3. في صفحة تفاصيل الاشتراك، في قسم **إعدادات الاشتراك والدفع** ، حدد **"حذف الاشتراك**".
4. في جزء **«Delete subscription** »، حدد **«Delete subscription**».
5. في مربع الحوار **"حذف الاشتراك** "، حدد **"نعم**".
6. لكل اشتراك معطل، كرر الخطوات من 3 إلى 5 حتى يتم حذف جميع الاشتراكات.

> [!NOTE]
> إذا لم تتمكن من حذف اشتراك معطل على الفور، [فاتصل بالدعم](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>الخطوة 4: تعطيل المصادقة متعددة العوامل

1. سجل الدخول إلى مركز الإدارة باستخدام حساب مسؤول عمومي. للتحقق من الأدوار التي لديك، راجع [التحقق من أدوار المسؤول في مؤسستك](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. انتقل إلى صفحة **المستخدمين النشطين للمستخدمين** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>
3. اختر **المصادقة متعددة العوامل**.
4. في صفحة المصادقة متعددة العوامل، قم بتعطيل كافة الحسابات باستثناء حساب المسؤول العمومي الذي تستخدمه حاليا.

يمكنك أيضا [استخدام PowerShell لتعطيل المصادقة متعددة العوامل لعدة مستخدمين](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>الخطوة 5: حذف الدليل في Azure Active Directory

1. سجل الدخول إلى <a href="https://aad.portal.azure.com/" target="_blank">مركز إدارة Azure AD</a> باستخدام حساب مسؤول عمومي.
2. حدد **Microsoft Azure Active Directory**.
3. قم بالتبديل إلى المؤسسة التي تريد حذفها.
4. حدد **«Delete tenant»**.
5. إذا فشلت مؤسستك في عملية تحقق واحدة أو أكثر، فسترى ارتباطا لمزيد من المعلومات حول كيفية تمرير عمليات الفحص. بعد اجتياز كافة عمليات التحقق، حدد **"حذف** " لإكمال العملية.

بعد إكمال هذه الخطوة الأخيرة، يتم إغلاق حسابك مع Microsoft وحذفه.

## <a name="related-content"></a>المحتويات ذات الصلة 

[فهم فاتورتك أو فاتورتك Microsoft 365 للأعمال](./billing-and-payments/understand-your-invoice2.md) (مقالة)\
[إلغاء اشتراكك](./subscriptions/cancel-your-subscription.md) (مقالة)

