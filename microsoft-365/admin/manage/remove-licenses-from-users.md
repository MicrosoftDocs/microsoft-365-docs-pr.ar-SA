---
title: اخطاء تعيين التراخيص من المستخدمين
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_smb
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: تعتمد الطريقة التي تستخدمها لترخيص منتج غير معين على ما إذا كنت تقوم بعزل التراخيص من مستخدمين محددين أو من منتج معين.
ms.date: 09/16/2021
ms.openlocfilehash: 7308888c54a30cdd11618cb07a233f8bd55f27c2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569182"
---
# <a name="unassign-licenses-from-users"></a>اخطاء تعيين التراخيص من المستخدمين

يمكنك عدم تعيين التراخيص من المستخدمين على صفحة المستخدمين النشطين أو على **صفحة التراخيص**. يعتمد الأسلوب الذي تستخدمه على ما إذا كنت تريد عدم تعيين تراخيص منتجات من مستخدمين معينين أو عدم تعيين تراخيص مستخدمين من منتج معين.

> [!NOTE]
> 
> - ب أنت مسؤول، لا يمكنك تعيين تراخيص أو إلغاء تعيينها لاشتراك شراء الخدمة الذاتية الذي يشتريه مستخدم في مؤسستك. يمكنك [الحصول على اشتراك شراء الخدمة](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) الذاتية، ثم تعيين التراخيص أو إلغاء تعيينها.
> 
> - بالنسبة لبعض الاشتراكات، يمكنك إلغاء الاشتراك فقط خلال فترة زمنية محدودة بعد شراء اشتراكك أو تجديده. إذا مرت نافذة الإلغاء، ف قم إيقاف تشغيل الفوترة المتكررة لإلغاء الاشتراك في نهاية مدة الاشتراك.

## <a name="before-you-begin"></a>قبل البدء

- يجب أن تكون "عام" و"ترخيص" و"مسؤول مستخدم" لترخيص غير تعيين. لمزيد من المعلومات، راجع [Microsoft 365 أدوار المسؤولين](../add-users/about-admin-roles.md).
- يمكنك إزالة [التراخيص من حسابات المستخدمين باستخدام Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- يمكنك أيضا [حذف حسابات المستخدمين](../add-users/delete-a-user.md) التي تم تعيين ترخيص لها لجعل ترخيصها متوفرا للمستخدمين الآخرين. عند حذف حساب مستخدم، يتوفر ترخيصه على الفور لتعيينه إلى شخص آخر.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>استخدام صفحة التراخيص لترخيص غير تعيين

عند استخدام صفحة **التراخيص** لترخيص غير معين، يمكنك إعادة تعيين التراخيص لمنتج معين لما يصل إلى 20 مستخدما.

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى **صفحة تراخيص** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">الفوترة</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى **صفحة تراخيص** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">الفوترة</a> .

::: moniker-end

2. حدد المنتج الذي تريد إعادة تعيين التراخيص له.

3. حدد المستخدمين الذين تريد إعادة تعيين تراخيصهم.

4. حدد **"غير تعيين التراخيص**".

5. في **المربع غير تعيين التراخيص** ، حدد **غير تعيين**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>استخدام صفحة المستخدمون النشطون لترخيص غير تعيين

عند استخدام صفحة **المستخدمون** النشطون لترخيص غير معين، يجب عليك إعادة تعيين تراخيص المنتجات من المستخدمين.

### <a name="unassign-licenses-from-one-user"></a>غير تعيين التراخيص من مستخدم واحد

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">النشطون</a> .

::: moniker-end

2. حدد صف المستخدم الذي تريد إعادة تعيين ترخيص له.

3. في الجزء الأيمن، حدد **التراخيص والتطبيقات**.

4. قم بتوسيع **مقطع التراخيص** ، وأمسح مربعات التراخيص التي تريد أن لا يتم تعيينها، ثم حدد **حفظ التغييرات**.

### <a name="unassign-licenses-from-multiple-users"></a>اخطاء تعيين التراخيص من عدة مستخدمين

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">النشطون</a> .

::: moniker-end

2. حدد الدوائر المجاورة لأسماء المستخدمين الذين تريد أن لا يتم تعيين تراخيصهم.

3. في الأعلى، حدد **إدارة تراخيص المنتجات**.

4. في الجزء **إدارة تراخيص** المنتجات، حدد **غير تعيين كافة** >  **التغييراتالتغييرات التي تم إدخالها**.

5. في أسفل الجزء، حدد **تم**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>ماذا يحدث لبيانات المستخدم عند إزالة ترخيصه؟

- عند إزالة ترخيص من مستخدم، يتم Exchange البيانات عبر الإنترنت المقترنة بهذا الحساب لمدة 30 يوما. بعد فترة السماح التي تستغرق 30 يوما، يتم حذف البيانات ولا يمكن استردادها.
- لا يتم حذف OneDrive for Business المحفوظة في الملف إلا إذا تم حذف المستخدم من مركز مسؤولي Microsoft 365 أو تمت إزالته من خلال مزامنة Active Directory. لمزيد من المعلومات، [راجع OneDrive الاستبقاء والحذف](/onedrive/retention-and-deletion).
- عند إزالة الترخيص، لن يعود البحث في علبة بريد المستخدم ممكنا باستخدام أداة eDiscovery مثل البحث في المحتوى أو Advanced eDiscovery. لمزيد من المعلومات، راجع "البحث في علب البريد غير المرخصة أو [غير المرخصة](../../compliance/content-search.md)" في البحث في المحتوى في Microsoft 365.
- إذا كان لديك اشتراك Enterprise، مثل Office 365 Enterprise E3، Exchange Online يمكنك من الاحتفاظ بيانات علبة البريد لحساب مستخدم محذوف باستخدام علب البريد [غير النشطة](../../compliance/inactive-mailboxes-in-office-365.md). لمزيد من المعلومات، راجع [إنشاء علب البريد غير](../../compliance/create-and-manage-inactive-mailboxes.md) النشطة وإدارتها في Exchange Online.
- لمعرفة كيفية حظر وصول مستخدم إلى Microsoft 365 بعد إزالة ترخيصه، وكيفية الوصول إلى البيانات بعد ذلك، راجع إزالة [موظف سابق](../add-users/remove-former-employee.md).
- إذا قمت بإزالة ترخيص مستخدم وكان لا يزال لديه Office مثبتة، فرؤية أخطاء التنشيط والمنتج غير المرخص في Office عند استخدام تطبيقات Office.[](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380)

## <a name="next-steps"></a>الخطوات التالية

إذا كنت لا تريد إعادة تعيين التراخيص غير المستخدمة لمستخدمين آخرين، فنظر في إزالة التراخيص من [](../../commerce/licenses/buy-licenses.md) اشتراكك بحيث لا تدفع مقابل تراخيص أكثر مما تحتاج إليه.[](../../managed-desktop/get-started/assign-licenses.md)

## <a name="related-content"></a>المحتوى ذي الصلة

[إزالة التراخيص من اشتراكك](../../commerce/licenses/buy-licenses.md) (مقالة)\
[تعيين تراخيص للمستخدمين](assign-licenses-to-users.md) (مقالة)\
[فهم الاشتراكات والتراخيص في Microsoft 365 للأعمال](../../commerce/licenses/subscriptions-and-licenses.md) (مقالة)
