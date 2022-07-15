---
title: إدارة الإصدار التجريبي من Frontline في Teams
author: daisyfell
ms.author: daisyfeller
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية إعداد إصدار تجريبي من Teams لمدة 90 يوما للعاملين في الخطوط الأمامية لمؤسستك.
ms.localizationpriority: high
ms.collection:
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 311d0a5b1204f022a993bbef24ea4bc1edda324c
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823683"
---
# <a name="manage-the-frontline-trial-in-teams"></a>إدارة الإصدار التجريبي من Frontline في Teams

> [!NOTE]
> ستتوفر هذه التجربة التجريبية قريبا. يمكنك التحقق من الوقت الذي يتوفر فيه ذلك لمؤسستك من خلال البحث عن رسالة في [مركز الرسائل](https://go.microsoft.com/fwlink/p/?linkid=2070717) في مركز مسؤول Microsoft 365.

تتيح تجربة الإصدار التجريبي من Microsoft Teams Frontline للمستخدمين في مؤسستك الموجودين في Teams بدء تجربة Teams لفريق الخطوط الأمامية بأكمله، طالما أن الأعضاء الآخرين في Azure Active Directory (Azure AD). يمكنك تعطيل هذه الميزة للمستخدمين في مؤسستك باستخدام [الوحدة النمطية AllowSelfServicePurchase PowerShell](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

## <a name="what-services-are-included"></a>الخدمات المضمنة

يتضمن الإصدار التجريبي كل شيء في [ترخيص Microsoft 365 F3](https://www.microsoft.com/microsoft-365/enterprise/f3) مع الاستثناءات التالية:

- يتضمن الإصدار التجريبي من Frontline Exchange Foundation بدلا من Exchange Kiosk. قد يفتقد المستخدمون وظائف Teams الأخرى بسبب هذا التغيير.

## <a name="eligibility"></a>الاهليه

> [!NOTE]
> يمكنك التحقق مما إذا كانت مؤسستك جزءا من الإصدار التجريبي من خلال البحث عن إعلان في [مركز الرسائل](https://go.microsoft.com/fwlink/p/?linkid=2070717) في مركز مسؤول Microsoft 365. ستحتاج مؤسستك إلى أن تكون جزءا من الإصدار التجريبي للمستخدمين لبدء تجربة أو المشاركة فيها. لا يتوفر هذا العرض لعملاء GCC أو GCC High أو DoD أو EDU.

يمكن أن تستوعب الإصدار التجريبي من Frontline 300 مستخدم كحد أقصى لكل إصدار تجريبي.

يمكن للمستخدمين بدء إصدار تجريبي من الخطوط الأمامية لفريقهم إذا:

- امتلاك ترخيص نشط يمنحهم حق الوصول إلى Teams.
- لم يسبق أن بدأت تجربة عامل الخطوط الأمامية.

> [!IMPORTANT]
> إذا غادر المستخدم الذي بدأ الإصدار التجريبي مؤسستك قبل انتهاء الإصدار التجريبي، فستحتاج كمسؤول إلى مراقبة الإصدار التجريبي، وتحقق من الفريق لمعرفة من يستفيد من هذه الميزات، وحدد المستخدمين الذين ستحتاجهم للترقية إلى ترخيص مدفوع.

يمكن للمستخدمين المشاركة في إصدار تجريبي لعامل الواجهة الأمامية إذا كان لديهم عنوان بريد إلكتروني مدار لمجال Azure Active Directory.

يمكن للمستخدمين المشاركة إذا قاموا مسبقا بتشغيل إصدار تجريبي، ولكن لا يمكنهم بدء إصدار تجريبي آخر.

> [!NOTE]
> يمكن إضافة المستخدمين الذين لا يملكون إمكانية وصول موجودة إلى Teams فقط إلى الفريق التجريبي في وقت إنشاء الفريق. لا يزال من الممكن إضافة مستخدمي Teams الحاليين إلى الإصدار التجريبي بعد إنشاء الفريق.

## <a name="set-up-the-trial"></a>إعداد الإصدار التجريبي

يمكن للمستخدمين المؤهلين بدء إصدار تجريبي من Frontline عن طريق تسجيل الدخول إلى تطبيق المهام في Teams من سطح المكتب أو [تطبيق الويب](https://teams.microsoft.com/_#/apps/com.microsoft.teamspace.tab.planner/sections/mytasks). في هذا الوقت، لا يتم دعم بدء الإصدار التجريبي من Frontline من خلال الهاتف المحمول. عند بدء الإصدار التجريبي، سيتم تعيين ترخيص الإصدار التجريبي من Frontline للفريق بأكمله تلقائيا. سيتم أيضا تعيين تراخيص تجريبية للمستخدمين الذين لديهم تراخيص مدفوعة موجودة تمنحهم إمكانية الوصول إلى Teams، ولكن سيحتفظون بوظائف تراخيصهم الحالية طوال فترة الإصدار التجريبي، وسيحتفظون بتراخيصهم المدفوعة الموجودة بعد انتهاء الإصدار التجريبي. سيتلقى المستخدم الذي بدأ الإصدار التجريبي إعلامات بالبريد الإلكتروني طوال فترة الإصدار التجريبي.

## <a name="manage-the-frontline-trials-experience"></a>إدارة تجربة الإصدارات التجريبية للخطوط الأمامية

يمكن للمسؤولين منع المستخدمين النهائيين من بدء تشغيل الإصدار التجريبي من Frontline داخل مؤسستهم باستخدام الوحدة النمطية **AllowSelfServicePurchase** PowerShell. هذا فقط للتراخيص التجريبية. [تعرف على كيفية استخدام الوحدة النمطية AllowSelfServicePurchase PowerShell](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

### <a name="manage-teams-for-users-who-have-the-frontline-trial-license"></a>إدارة Teams للمستخدمين الذين لديهم ترخيص Frontline Trial

يمكنك إدارة المستخدمين الذين لديهم ترخيص Frontline Trial تماما كما تدير المستخدمين الذين لديهم ترخيص مدفوع منتظم. لمزيد من المعلومات، راجع [إدارة إعدادات Teams لمؤسستك](/microsoftteams/manage-teams-overview).

### <a name="remove-a-trial-license"></a>إزالة ترخيص تجريبي

يمكنك إزالة ترخيص Frontline Trial من خلال PowerShell أو مركز مسؤولي Microsoft 365.

[تعرف على كيفية الإزالة باستخدام PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell).

[تعرف على كيفية الإزالة في مركز الإدارة](/microsoft-365/admin/add-users/delete-a-user).

## <a name="upgrade-users-from-frontline-trial"></a>ترقية المستخدمين من الإصدار التجريبي من Frontline

قد يتصل بك المستخدمون لطلب التراخيص عند انتهاء الإصدار التجريبي. ستحتاج إلى امتيازات المسؤول لترقية المستخدمين.

### <a name="when-to-upgrade"></a>متى يتم الترقية

بالقرب من نهاية الإصدار التجريبي لمدة 90 يوما، ستحتاج إلى التحقق مع المستخدمين لمعرفة من يحتاج إلى متابعة ترخيص مدفوع. تأكد من القيام بذلك قبل انتهاء صلاحية اشتراك Frontline Trial لتجنب أي تعطيل لتجارب المستخدمين.

> [!IMPORTANT]
> إذا انتهى ترخيص Frontline التجريبي ولم يتم تعيين ترخيص يتضمن Teams لمستخدم على الفور، فسيفقد إمكانية الوصول إلى Teams. بعد 30 يوما، يتم حذف بياناتهم (الملفات والرسائل والمزيد). لا يزال المستخدم موجودا في Azure Active Directory. إذا تم تعيين ترخيص جديد للمستخدم لتمكين وظائف Teams خلال فترة 30 يوما، فسيظل كل محتوياته في Teams موجودة.

### <a name="choose-an-upgrade-path"></a>اختيار مسار ترقية

> [!TIP]
> يستند الإصدار التجريبي من Frontline إلى [ترخيص Microsoft 365 F3](https://www.microsoft.com/microsoft-365/enterprise/f3).

استنادا إلى الاشتراكات التي تمتلكها مؤسستك حاليا، هناك ثلاث طرق للترقية من الإصدار التجريبي من Frontline إلى ترخيص مدفوع:

- **ترقية اشتراك Microsoft 365 موجود.** استخدم هذا الخيار إذا كانت مؤسستك لديها اشتراكات في منتجات Office الأخرى التي لا تتضمن Teams. لمزيد من المعلومات، راجع [الترقية إلى خطة مختلفة](/microsoft-365/commerce/subscriptions/upgrade-to-different-plan). للاطلاع على المستخدمين النشطين لاشتراك موجود، انتقل إلى **المستخدمين >** [المستخدمين النشطين](https://go.microsoft.com/fwlink/p/?linkid=834822) في مركز مسؤولي Microsoft 365.

- **إضافة مستخدمين إلى اشتراك Microsoft 365 موجود.** استخدم هذا الخيار إذا لم يكن لدى مؤسستك تراخيص Teams المدفوعة كافية لتغطية فريق الخطوط الأمامية. لمزيد من المعلومات، راجع [شراء التراخيص أو إزالتها](/microsoft-365/commerce/licenses/buy-licenses). لإضافة مستخدمين إلى اشتراك موجود يحتوي بالفعل على تراخيص متوفرة كافية، راجع [نقل المستخدمين إلى اشتراك مختلف](/microsoft-365/commerce/subscriptions/move-users-different-subscription). للاطلاع على المستخدمين النشطين لاشتراك موجود، انتقل إلى **المستخدمين >** [المستخدمين النشطين](https://go.microsoft.com/fwlink/p/?linkid=834822) في مركز مسؤولي Microsoft 365.

- **شراء اشتراك Microsoft 365 جديد.** استخدم هذا الخيار إذا لم يكن لدى مؤسستك أي اشتراكات موجودة في منتجات Office، أو إذا كانت مؤسستك تريد شراء اشتراك مختلف عن اشتراكها الحالي لتغطية مستخدمي الخطوط الأمامية. لمزيد من المعلومات، راجع [Microsoft 365 للعاملين في الخطوط الأمامية](https://www.microsoft.com/microsoft-365/enterprise/frontline).

إذا لم تكن متأكدا من اشتراك Microsoft 365 الذي تريد الترقية إليه، فراجع [Microsoft 365 للعاملين في الخطوط الأمامية](https://www.microsoft.com/microsoft-365/enterprise/frontline). إذا كنت بحاجة إلى مساعدة إضافية في اختيار اشتراك، أو إذا كانت مؤسستك بحاجة إلى أكثر من 300 ترخيص، فاتصل [بشريك Microsoft](https://www.microsoft.com/solution-providers/home) أو ممثل حساب Microsoft.

### <a name="assign-paid-licenses"></a>تعيين التراخيص المدفوعة

لتعيين التراخيص التي حصلت عليها حديثا، راجع [تعيين التراخيص للمستخدمين](/microsoft-365/admin/manage/assign-licenses-to-users).  

بعد تعيين التراخيص الجديدة، قم بإلغاء تعيين تراخيص Teams الاستكشافية. راجع [إلغاء تعيين التراخيص من المستخدمين](/microsoft-365/admin/manage/remove-licenses-from-users)، للحصول على مزيد من المعلومات.

## <a name="faq"></a>الأسئلة المتداولة

**المدة التي يستغرقها الإصدار التجريبي** <br>
يستمر الإصدار التجريبي من Frontline لمدة 90 يوما.

**ما الذي يجب على المسؤولين فعله في نهاية تجربة الإصدار التجريبي من Frontline لمدة 90 يوما؟** <br>
في نهاية الإصدار التجريبي لمدة 90 يوما، ستحتاج إلى التحقق مع المستخدمين لمعرفة من يحتاج إلى متابعة ترخيص مدفوع. ثم ستحتاج إلى [ترقية المستخدمين](#upgrade-users-from-frontline-trial).

**ماذا يحدث إذا غادر المستخدم الذي بدأ الإصدار التجريبي مؤسستك؟** <br>
ستحتاج كمسؤول إلى مراقبة الإصدار التجريبي لبقية فترة ال 90 يوما، والترقية إلى التراخيص المدفوعة للمستخدمين الذين يحتاجون إليها عند انتهاء الإصدار التجريبي.

**ما هو نهج استبقاء البيانات؟** <br>
يمكنك التعرف على استبقاء البيانات من [معلومات اشتراك Microsoft 365](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?).

**ماذا لو واجه مستخدم خطأ عند بدء تشغيل الإصدار التجريبي من Frontline؟** <br>
تأكد من أن مؤسستك والمستخدم الذي يبدأ الإصدار التجريبي والمستخدمين الذين تتم إضافتهم إلى الإصدار التجريبي يستوفون [معايير الأهلية](#eligibility).