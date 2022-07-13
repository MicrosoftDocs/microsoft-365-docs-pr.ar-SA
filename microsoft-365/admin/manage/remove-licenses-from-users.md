---
title: أخطاء تعيين التراخيص من المستخدمين
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
description: يعتمد الأسلوب الذي تستخدمه لإلغاء تعيين تراخيص المنتجات على ما إذا كنت تقوم بإلغاء تعيين التراخيص من مستخدمين محددين أو من منتج معين.
ms.date: 07/12/2022
ms.openlocfilehash: b6459030c376bb891ea32b9cb096d26449dfa0d1
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748374"
---
# <a name="unassign-microsoft-365-licenses-from-users"></a>إلغاء تعيين تراخيص Microsoft 365 من المستخدمين

يمكنك إلغاء تعيين التراخيص من المستخدمين على صفحة **"المستخدمين النشطين** " أو على صفحة **"التراخيص** ". يعتمد الأسلوب الذي تستخدمه على ما إذا كنت تريد إلغاء تعيين تراخيص المنتجات من مستخدمين محددين أو إلغاء تعيين تراخيص المستخدمين من منتج معين.

> [!NOTE]
>
> - بصفتك مسؤولا، لا يمكنك تعيين تراخيص أو إلغاء تعيينها لاشتراك شراء الخدمة الذاتية الذي يشتريه مستخدم في مؤسستك. يمكنك [تولي اشتراك شراء الخدمة الذاتية](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription)، ثم تعيين تراخيص أو إلغاء تعيينها.
>
> - بالنسبة لبعض الاشتراكات، يمكنك إلغاء الاشتراك فقط خلال فترة زمنية محدودة بعد شراء اشتراكك أو تجديده. إذا تم تمرير نافذة الإلغاء، فقم بإيقاف تشغيل الفوترة المتكررة لإلغاء الاشتراك في نهاية مدة الاشتراك.

## <a name="before-you-begin"></a>قبل البدء

- يجب أن تكون مسؤولا عموميا، وترخيصا، ومستخدما لإلغاء تعيين التراخيص. لمزيد من المعلومات، راجع [حول أدوار مسؤولي Microsoft 365](../add-users/about-admin-roles.md).
- يمكنك [إزالة التراخيص من حسابات المستخدمين باستخدام Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- يمكنك أيضا [حذف حسابات المستخدمين](../add-users/delete-a-user.md) التي تم تعيين ترخيص لها لجعل ترخيصها متوفرا للمستخدمين الآخرين. عند حذف حساب مستخدم، يكون ترخيصه متوفرا على الفور لتعيينه إلى شخص آخر.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>استخدام صفحة "التراخيص" لإلغاء تعيين التراخيص

تتيح لك صفحة **التراخيص** تعيين تراخيص أو إلغاء تعيينها لما يصل إلى 20 مستخدما في كل مرة. تعرض الصفحة المنتجات التي تملكها وعدد التراخيص المتوفرة لكل منتج وعدد التراخيص المعينة من إجمالي التراخيص المتوفرة.

تعرض صفحة **التراخيص** إجمالي إجمالي التراخيص لكافة الاشتراكات لاسم المنتج نفسه. على سبيل المثال، قد يكون لديك اشتراك واحد Microsoft 365 Business Premium يحتوي على 5 تراخيص، واشتراك آخر يحتوي على 8 تراخيص لنفس المنتج. تظهر صفحة **"التراخيص**" أن لديك إجمالي 13 ترخيصا Microsoft 365 Business Premium عبر جميع اشتراكاتك. يختلف هذا عن ما تراه في صفحة **المنتجات،** والتي تعرض صفا لكل اشتراك تملكه، حتى لو كان للمنتج نفسه.

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">"تراخيص</a> **الفوترة**\>".

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">"تراخيص</a> **الفوترة**\>".

::: moniker-end

2. حدد منتجا.

3. حدد خانات الاختيار الخاصة بالمستخدمين الذين تريد إلغاء تعيين التراخيص لهم.

4. حدد **إلغاء تعيين التراخيص**.

5. في المربع **"إلغاء تعيين التراخيص** "، حدد **"إلغاء التعيين**".

## <a name="use-the-active-users-page-to-unassign-licenses"></a>استخدام صفحة "المستخدمون النشطون" لإلغاء تعيين التراخيص

عند استخدام صفحة **"المستخدمون النشطون** " لإلغاء تعيين التراخيص، يمكنك إلغاء تعيين تراخيص المنتجات من المستخدمين.

### <a name="unassign-licenses-from-one-user"></a>إلغاء تعيين التراخيص من مستخدم واحد

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank"></a>

::: moniker-end

2. حدد صف المستخدم الذي تريد إلغاء تعيين ترخيص له.

3. في الجزء الأيسر، حدد **"التراخيص والتطبيقات**".

4. قم بتوسيع قسم **"التراخيص** "، وقم بإلغاء تحديد المربعات الخاصة بالتراخيص التي تريد إلغاء تعيينها، ثم حدد **"حفظ التغييرات**".

### <a name="unassign-licenses-from-multiple-users"></a>إلغاء تعيين التراخيص من عدة مستخدمين

::: moniker range="o365-worldwide"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank"></a>

::: moniker-end

2. حدد الدوائر الموجودة بجانب أسماء المستخدمين الذين تريد إلغاء تعيين التراخيص لهم.

3. في الأعلى، حدد **"Manage product licenses**".

4. في الجزء **"إدارة تراخيص المنتجات** "، حدد **"إلغاء تعيين كافة** > **تغييرات الحفظ**".

5. في أسفل الجزء، حدد **«Done»**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>ماذا يحدث لبيانات المستخدم عند إزالة ترخيصه؟

- عند إزالة ترخيص من مستخدم، يتم الاحتفاظ بالبيانات Exchange Online المقترنة بهذا الحساب لمدة 30 يوما. بعد فترة السماح التي تبلغ 30 يوما، يتم حذف البيانات ولا يمكن استردادها. ومع ذلك، فإنه يرتبط بنهج الاستبقاء، ويتم الاحتفاظ بالمحتوى الذي يطابق تسميات الاستبقاء للاكتشاف.
- لا يتم حذف الملفات المحفوظة في OneDrive for Business إلا إذا تم حذف المستخدم من مركز مسؤولي Microsoft 365 أو تمت إزالته من خلال مزامنة Active Directory. لمزيد من المعلومات، راجع [استبقاء OneDrive وحذفه](/onedrive/retention-and-deletion).
- عند إزالة الترخيص، لم تعد علبة بريد المستخدم قابلة للبحث باستخدام أداة eDiscovery مثل البحث في المحتوى أو eDiscovery (Premium). لمزيد من المعلومات، راجع "البحث في علب البريد غير المتصلة أو غير المرخصة" في ["البحث في المحتوى" في Microsoft 365](../../compliance/content-search.md).
- إذا كان لديك اشتراك Enterprise، مثل Office 365 Enterprise E3، Exchange Online يسمح لك بالاحتفاظ ببيانات علبة البريد لحساب مستخدم محذوظ باستخدام [علب البريد غير النشطة](../../compliance/inactive-mailboxes-in-office-365.md). لمزيد من المعلومات، راجع [إنشاء علب بريد غير نشطة وإدارتها في Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- لمعرفة كيفية حظر وصول المستخدم إلى بيانات Microsoft 365 بعد إزالة ترخيصه، وكيفية الوصول إلى البيانات بعد ذلك، راجع [إزالة موظف سابق](../add-users/remove-former-employee.md).
- إذا قمت بإزالة ترخيص مستخدم وكان لا يزال لديه تطبيقات Office مثبتة، فسيظهر المنتج [غير المرخص وأخطاء التنشيط في Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) عند استخدام تطبيقات Office.

## <a name="next-steps"></a>الخطوات التالية

إذا كنت لن [تعيد تعيين التراخيص غير المستخدمة إلى مستخدمين آخرين](assign-licenses-to-users.md)، ففكر [في إزالة التراخيص من اشتراكك](../../commerce/licenses/buy-licenses.md) بحيث لا تدفع مقابل تراخيص أكثر مما تحتاج إليه.

## <a name="related-content"></a>المحتويات ذات الصلة

[إزالة التراخيص من اشتراكك](../../commerce/licenses/buy-licenses.md) (مقال)\
[تعيين تراخيص للمستخدمين](assign-licenses-to-users.md) (مقالة)\
[التعرّف على الاشتراكات والتراخيص في Microsoft 365 للأعمال](../../commerce/licenses/subscriptions-and-licenses.md) (مقالة)
