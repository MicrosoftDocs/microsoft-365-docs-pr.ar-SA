---
title: إغلاق حسابك
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
- fwlink 2133922 to Delete subscription heading
- AdminTemplateSet
search.appverid: MET150
description: عند إغلاق حسابك مع Microsoft، يتم حذف كل المعلومات المتعلقة به بما في ذلك التراخيص والمستخدمين وبيانات المستخدمين.
ms.date: 04/02/2021
ms.openlocfilehash: b1ac828d047d2c2b9f39185a66ccc77976b8324b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566979"
---
# <a name="close-your-account"></a>إغلاق حسابك

عند إغلاق حسابك في Microsoft، ستُحذف كل المعلومات المتعلقة بحسابك. تتضمن هذه المعلومات الاشتراكات والتراخيص وطرق الدفع والمستخدمين وبياناتهم.

## <a name="before-you-begin"></a>قبل البدء

قبل بدء تلك العملية، تأكد من إعدادك نسخة احتياطية لأي بيانات تريد حفظها.

يجب أن تكون المسؤول العام أو مسؤول الفوترة للقيام بالمهام في هذه المقالة. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>الخطوة 1: حذف المستخدمين

احذف جميع المستخدمين باستثناء مسؤول عام واحد. يكمل المسؤول العام الخطوات اللازمة لإغلاق الحساب. قبل أن تتمكن من حذف الدليل في نهاية هذه العملية، يجب حذف جميع المستخدمين الآخرين.

إذا كانت مزامنة المستخدمين تتم من داخل الموقع، فأغلق المزامنة أولا، ثم احذف المستخدمين في دليل السحابة باستخدام مدخل Azure أو Azure PowerShell cmdlets.

لحذف المستخدمين، راجع [مسؤول إدارة المستخدمين: حذف مستخدم واحد أو أكثر](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

يمكنك أيضا استخدام [الأمر Cmdlet Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell لحذف المستخدمين بشكل مجمع.

إذا كانت مؤسستك تستخدم Active Directory الذي يتزامن مع Microsoft Azure Active Directory (Azure AD)، فاحذف حساب المستخدم من Active Directory، بدلا من ذلك. للحصول على الإرشادات، راجع [حذف المستخدمين بشكل مجمع في Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>الخطوة 2: إلغاء كل الاشتراكات النشطة

1. في مركز الإدارة، انتقل إلى **صفحة منتجات BillingYour** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>
2. على علامة **التبويب** المنتجات، ابحث عن اشتراك نشط. حدد النقاط الثلاث (المزيد من الإجراءات)، ثم حدد **إلغاء الاشتراك**.
3. في الجزء **إلغاء الاشتراك** ، اختر سببا وراء إلغاء الاشتراك. بشكل اختياري، اقدم أي ملاحظات.
4. حدد **حفظ**.
5. كرر الخطوات من 1 إلى 4 لإلغاء كل الاشتراكات النشطة.

## <a name="step-3-delete-all-disabled-subscriptions"></a>الخطوة 3: حذف كل الاشتراكات المعطلة

1. في مركز الإدارة، انتقل إلى **صفحة منتجات BillingYour** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>
2. على علامة **التبويب** المنتجات، حدد اشتراكا معطلا.
3. في صفحة تفاصيل الاشتراك، في المقطع **إعدادات الاشتراك والدفع** ، حدد **حذف الاشتراك**.
4. في جزء **حذف الاشتراك** ، حدد **حذف اشتراك**.
5. في مربع **الحوار حذف** اشتراك، حدد **نعم**.
6. لكل اشتراك معطل، كرر الخطوات من 3 إلى 5 حتى يتم حذف كل الاشتراكات.

> [!NOTE]
> إذا تعذر عليك حذف اشتراك معطل على الفور، [فاتصل بالدعم](../admin/get-help-support.md).

## <a name="step-4-disable-multi-factor-authentication"></a>الخطوة 4: تعطيل المصادقة متعددة العوامل

1. سجل الدخول إلى مركز الإدارة باستخدام حساب مسؤول عام. للتحقق من الأدوار التي لديك، راجع [التحقق من أدوار المسؤولين في مؤسستك](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. انتقل إلى صفحة <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">المستخدمونمستخدمون</a>  >  نشطون.
3. اختر **مصادقة متعددة العوامل**.
4. في صفحة المصادقة متعددة العوامل، قم بتعطيل كل الحسابات باستثناء حساب المسؤول العام الذي تستخدمه حاليا.

يمكنك أيضا استخدام [PowerShell لتعطيل المصادقة متعددة العوامل لعدة مستخدمين](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>الخطوة 5: حذف الدليل في Azure Active Directory

1. سجل الدخول إلى <a href="https://aad.portal.azure.com/" target="_blank">مركز إدارة Azure AD</a> باستخدام حساب مسؤول عام.
2. حدد **Microsoft Azure Active Directory**.
3. قم بالتبديل إلى المؤسسة التي تريد حذفها.
4. حدد **حذف المستأجر**.
5. إذا فشلت مؤسستك في إجراء فحص واحد أو أكثر، يمكنك رؤية ارتباط لمزيد من المعلومات حول كيفية اجتياز الاختبارات. بعد اجتياز كل الاختبارات، حدد **حذف** لإكمال العملية.

بعد إكمال هذه الخطوة النهائية، يتم إغلاق حسابك مع Microsoft وحذفه.

## <a name="related-content"></a>المحتوى ذي الصلة 

[فهم الفاتورة أو الفاتورة الخاصة Microsoft 365 للأعمال](./billing-and-payments/understand-your-invoice2.md) (مقالة)\
[إلغاء اشتراكك](./subscriptions/cancel-your-subscription.md) (مقالة)

