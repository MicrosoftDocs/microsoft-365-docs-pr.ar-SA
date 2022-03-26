---
title: تعيين Microsoft 365 جديدة إلى حسابات المستخدمين
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: يصف كيفية تعيين تراخيص Microsoft 365 إلى حسابات المستخدمين، سواء بشكل فردي أو استنادا إلى عضوية المجموعة.
ms.openlocfilehash: dd941be0d257aa356cf6e69bfdd59a8d1743ed93
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568945"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>تعيين Microsoft 365 جديدة إلى حسابات المستخدمين

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

بالنسبة إلى نموذج الهوية الخاص بالسحابة فقط، يمكنك تعيين Microsoft 365 جديدة إلى حسابات المستخدمين عند إنشائها، استنادا إلى كيفية إنشائها.

بالنسبة إلى نموذج الهوية المختلطة، عند مزامنة حسابات مستخدمي خدمات مجال Active Directory (AD DS) للمرة الأولى، لا يتم تعيين موقع أو ترخيص Microsoft 365 تلقائيا. **يجب تكوين كل حساب مستخدم مع موقع مستخدم قبل تعيين ترخيص أو إلى جانبه.**

في الحالتين، يجب تعيين ترخيص إلى حسابات المستخدمين بحيث يمكن للمستخدمين الوصول إلى Microsoft 365، مثل البريد الإلكتروني Microsoft Teams.

يمكنك تعيين تراخيص إلى حسابات المستخدمين إما بشكل فردي أو تلقائي من خلال عضوية المجموعة.

لتعيين تراخيص Microsoft 365 إلى حسابات مستخدمين فردية، يمكنك استخدام:

- [مركز مسؤولي Microsoft 365](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- مركز إدارة Azure AD

## <a name="group-based-licensing"></a>الترخيص المستند إلى المجموعة

يمكنك تكوين مجموعات الأمان في Azure AD لتعيين التراخيص تلقائيا من مجموعة من الاشتراكات إلى جميع أعضاء المجموعة. يعرف ذلك *بالترخيص المستند إلى المجموعة*. إذا تمت إضافة حساب مستخدم إلى المجموعة أو إزالته منها، سيتم تعيين تراخيص لاشتراكات المجموعة تلقائيا أو إلغاء تعيينها من حساب المستخدم.

تأكد من أن لديك تراخيص كافية لجميع أعضاء المجموعة. إذا نفت التراخيص لديك، فلن يتم تعيين تراخيص للمستخدمين الجدد حتى تصبح التراخيص متوفرة.

>[!Note]
>يجب ألا تقوم بتكوين الترخيص المستند إلى المجموعة للمجموعات التي تحتوي على حسابات Azure للأعمال (B2B).
>

لمزيد من المعلومات، راجع [الترخيص المستند إلى المجموعة في Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>الخطوات التالية

باستخدام المجموعة المناسبة من حسابات المستخدمين التي تم تعيين تراخيص لها، أصبحت الآن جاهزا ل:

- [تنفيذ الأمان](../security/office-365-security/security-roadmap.md)
- [نشر برامج العميل، مثل Microsoft 365 Apps](/DeployOffice/deployment-guide-microsoft-365-apps)
- [إعداد إدارة الأجهزة](device-management-roadmap-microsoft-365.md)
- [تكوين الخدمات والتطبيقات](configure-services-and-applications.md)