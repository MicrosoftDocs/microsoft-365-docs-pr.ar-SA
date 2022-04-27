---
title: إدارة مجموعات Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: تعرف على كيفية إدارة مجموعات Microsoft 365.
ms.openlocfilehash: 0e7cef7d1b55f695af9a33f22393172f6eee6485
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100490"
---
# <a name="manage-microsoft-365-groups"></a>إدارة مجموعات Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك إدارة مجموعات Microsoft 365 بعدة طرق مختلفة، اعتمادا على التكوين الخاص بك. يمكنك إدارة حسابات المستخدمين في [مركز مسؤولي Microsoft 365](/admin) أو PowerShell أو في خدمات مجال Active Directory (AD DS) أو في [مركز إدارة Azure Active Directory (Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>التخطيط لمكان وكيفية إدارة مجموعاتك

يعتمد مكان وكيفية إدارة حسابات المستخدمين على نموذج الهوية الذي تريد استخدامه Microsoft 365. النموذجان العامان هما السحابة فقط والمختلطة.
  
### <a name="cloud-only"></a>السحابة فقط

يمكنك إنشاء المجموعات وإدارتها باستخدام:

- [مركز مسؤولي Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [مركز إدارة Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>مختلط

تتم مزامنة مجموعات AD DS مع Microsoft 365 من AD DS، لذلك يجب استخدام أدوات AD DS المحلية لإدارة هذه المجموعات.

يمكنك أيضا إنشاء وإدارة مجموعات Azure AD المنفصلة عن مجموعات AD DS ولكن يمكن أن تحتوي على مستخدمين ومجموعات من AD DS. في هذه الحالة، يمكنك استخدام:

- [مركز مسؤولي Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [مركز إدارة Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>السماح للمستخدمين بإنشاء مجموعاتهم الخاصة وإدارتها

يسمح Azure AD بالمجموعات التي يمكن إدارتها من قبل مالكي المجموعات بدلا من مسؤولي تكنولوجيا المعلومات. تعرف هذه الميزة *بإدارة مجموعة الخدمة الذاتية*، وتسمح لمالكي المجموعات الذين لم يتم تعيين دور إداري لهم بإنشاء مجموعات الأمان وإدارتها. 

يمكن للمستخدمين طلب العضوية في مجموعة أمان وينتقل هذا الطلب إلى مالك المجموعة، بدلا من مسؤول تكنولوجيا المعلومات. يسمح هذا الأمر بتفويض التحكم اليومي في عضوية المجموعة إلى مالكي الفرق أو المشاريع أو الشركات الذين يفهمون استخدام الأعمال للمجموعة ويمكنهم إدارة عضويتها.

>[!Note]
>تتوفر إدارة مجموعة الخدمة الذاتية فقط لأمان Azure AD ومجموعات Microsoft 365. وهي غير متوفرة للمجموعات الممكنة للبريد أو قوائم التوزيع أو أي مجموعة تمت مزامنتها من AD DS.
>

لمزيد من المعلومات، راجع [الإرشادات لتكوين مجموعة Azure AD لإدارة الخدمة الذاتية](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>إعداد عضوية المجموعة الديناميكية

يدعم Azure AD تكوين سلسلة من القواعد التي تضيف تلقائيا حسابات المستخدمين أو تزيلها كأعضاء في مجموعة Azure AD. يعرف هذا باسم *عضوية المجموعة الديناميكية*. تستند القواعد إلى سمات حساب المستخدم، مثل القسم أو البلد.

إليك كيفية تطبيق القواعد:

- إذا تطابق حساب مستخدم جديد مع جميع قواعد المجموعة، فسيصبح عضوا.
- إذا لم يكن حساب المستخدم عضوا في المجموعة، ولكن تتغير سماته بحيث يطابق جميع قواعد المجموعة، فسيصبح عضوا في تلك المجموعة.
- إذا لم يتطابق حساب المستخدم مع كافة قواعد المجموعة، فلن تتم إضافته إلى المجموعة.
- إذا كان حساب المستخدم عضوا في المجموعة، ولكن تتغير سماته بحيث لا يتطابق مع كافة قواعد المجموعة، تتم إزالته كعضو في المجموعة.

لاستخدام العضوية الديناميكية، يجب أولا تحديد مجموعات المجموعات التي تحتوي على مجموعة مشتركة من سمات حساب المستخدم. على سبيل المثال، يجب أن يكون جميع أعضاء قسم المبيعات في مجموعة Sales Azure AD، استنادا إلى قسم سمة حساب المستخدم المعين إلى "المبيعات".

راجع [الإرشادات لإنشاء القواعد وتكوينها لمجموعة Azure AD ديناميكية](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>إعداد الترخيص التلقائي

يمكنك تكوين مجموعات الأمان في Azure AD لتعيين التراخيص تلقائيا من مجموعة من الاشتراكات لجميع أعضاء المجموعة. يعرف هذا باسم *الترخيص المستند إلى المجموعة*. إذا تمت إضافة حساب مستخدم إلى المجموعة أو إزالته منها، فسيتم تعيين تراخيص اشتراكات المجموعة تلقائيا أو إلغاء تعيينها من حساب المستخدم.

على سبيل Microsoft 365 Enterprise، ستقوم بتكوين مجموعات أمان Azure AD لتعيين ترخيص Microsoft 365 Enterprise المناسب.

تأكد من أن لديك تراخيص كافية لجميع أعضاء المجموعة. إذا نفدت التراخيص، فلن يتم تعيين تراخيص للمستخدمين الجدد حتى تصبح التراخيص متوفرة.

>[!Note]
>يجب عدم تكوين الترخيص المستند إلى المجموعة للمجموعات التي تحتوي على حسابات Azure business to business (B2B).
>

لمزيد من المعلومات، راجع [أساسيات الترخيص المستندة إلى المجموعة في Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

راجع [الإرشادات لتكوين الترخيص المستند إلى المجموعة لمجموعة أمان Azure](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).