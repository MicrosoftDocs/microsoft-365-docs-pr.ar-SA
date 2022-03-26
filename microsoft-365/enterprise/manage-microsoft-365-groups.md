---
title: إدارة Microsoft 365 المجموعات
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية إدارة Microsoft 365 المجموعات.
ms.openlocfilehash: 28d8bae8aaed6d02fe082824c07afe03bdc0ce5a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575405"
---
# <a name="manage-microsoft-365-groups"></a>إدارة Microsoft 365 المجموعات

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك إدارة Microsoft 365 المجموعات بعدة طرق مختلفة، استنادا إلى التكوين. يمكنك إدارة حسابات المستخدمين في مركز مسؤولي Microsoft 365 [](/admin)أو PowerShell أو في خدمات مجال Active Directory (AD DS) أو في [مركز إدارة Azure Active Directory (Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>التخطيط لمجموعاتك وكيفية إدارتها

يعتمد مكان إدارة حسابات المستخدمين وكيفية إدارتها على نموذج الهوية الذي تريد استخدامه Microsoft 365. النموذجان الإجماليان مختلطان وسحابي فقط.
  
### <a name="cloud-only"></a>السحابة فقط

يمكنك إنشاء مجموعات وإدارتها باستخدام:

- [مركز مسؤولي Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [مركز إدارة Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>مختلط

يتم مزامنة مجموعات AD DS Microsoft 365 من AD DS، لذلك يجب استخدام أدوات AD DS المحلية لإدارة هذه المجموعات.

يمكنك أيضا إنشاء مجموعات Azure AD المنفصلة عن مجموعات AD DS وإدارتها ولكن يمكن أن تحتوي على مستخدمين ومجموعات من AD DS. في هذه الحالة، يمكنك استخدام:

- [مركز مسؤولي Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [مركز إدارة Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>السماح للمستخدمين بإنشاء مجموعاتهم الخاصة وإدارتها

يسمح Azure AD بالمجموعات التي يمكن إدارتها بواسطة مالكي المجموعة بدلا من مسؤولي تكنولوجيا المعلومات. تعرف هذه *الميزة بإدارة مجموعات* الخدمة الذاتية، وتسمح لمالكي المجموعات الذين لم يتم تعيين دور إداري لهم بإنشاء مجموعات أمان وإدارتها. 

يمكن للمستخدمين طلب العضوية في مجموعة أمان، ويذهب هذا الطلب إلى مالك المجموعة، بدلا من مسؤول تكنولوجيا المعلومات. يسمح هذا الأمر بتفويض التحكم اليومية في عضوية المجموعة إلى مالكي الفريق أو المشروع أو الأعمال الذين يفهمون استخدام الأعمال للمجموعة ويمكنهم إدارة عضويتها.

>[!Note]
>تتوفر إدارة مجموعة الخدمة الذاتية فقط لأمن Azure AD Microsoft 365 المجموعات. ولا تتوفر للمجموعات أو قوائم التوزيع أو أي مجموعة تم مزامنتها من AD DS.
>

لمزيد من المعلومات، راجع الإرشادات لتكوين [مجموعة Azure AD لإدارة الخدمة الذاتية](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>إعداد عضوية المجموعة الديناميكية

يدعم Azure AD تكوين سلسلة من القواعد التي تضيف حسابات المستخدمين أو تزيلها تلقائيا كأعضاء في مجموعة Azure AD. تعرف هذه العضوية *بعضوية المجموعة الديناميكية*. تستند القواعد إلى سمات حساب المستخدم، مثل القسم أو البلد.

فيما يلي كيفية تطبيق القواعد:

- إذا تطابق حساب مستخدم جديد مع كل قواعد المجموعة، يتحول إلى عضو.
- إذا لم يكن حساب المستخدم عضوا في المجموعة، ولكن تتغير سماته بحيث يتطابق مع كل قواعد المجموعة، فيصبح عضوا في تلك المجموعة.
- إذا لم يكن حساب المستخدم مطابقا لجميع قواعد المجموعة، فإنه لا يضاف إلى المجموعة.
- إذا كان حساب المستخدم عضوا في المجموعة، ولكن تتغير سماته بحيث لا يتطابق مع كل قواعد المجموعة، تتم إزالته كعضو في المجموعة.

لاستخدام العضوية الديناميكية، يجب أولا تحديد مجموعات المجموعات التي لديها مجموعة مشتركة من سمات حساب المستخدم. على سبيل المثال، يجب أن يكون كل أعضاء قسم المبيعات في مجموعة المبيعات Azure AD، استنادا إلى سمة حساب المستخدم التي تم تعيينها إلى "المبيعات".

راجع [الإرشادات لإنشاء القواعد وتكوينها لمجموعة Azure AD ديناميكية](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>إعداد الترخيص التلقائي

يمكنك تكوين مجموعات الأمان في Azure AD لتعيين التراخيص تلقائيا من مجموعة من الاشتراكات إلى جميع أعضاء المجموعة. يعرف ذلك *بالترخيص المستند إلى المجموعة*. إذا تمت إضافة حساب مستخدم إلى المجموعة أو إزالته منها، سيتم تعيين تراخيص لاشتراكات المجموعة تلقائيا أو إلغاء تعيينها من حساب المستخدم.

على Microsoft 365 Enterprise، ستكوين مجموعات أمان Azure AD لتعيين الترخيص Microsoft 365 Enterprise المناسب.

تأكد من أن لديك تراخيص كافية لجميع أعضاء المجموعة. إذا نفت التراخيص لديك، فلن يتم تعيين تراخيص للمستخدمين الجدد حتى تصبح التراخيص متوفرة.

>[!Note]
>يجب ألا تقوم بتكوين الترخيص المستند إلى المجموعة للمجموعات التي تحتوي على حسابات Azure للأعمال (B2B).
>

لمزيد من المعلومات، راجع [أساسيات الترخيص المستند إلى المجموعة في Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

راجع [الإرشادات لتكوين الترخيص المستند إلى المجموعة لمجموعة أمان Azure](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).