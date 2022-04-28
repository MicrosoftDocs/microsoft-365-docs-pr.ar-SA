---
title: تعيين تراخيص Microsoft 365 لحسابات المستخدمين
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: يصف كيفية تعيين تراخيص Microsoft 365 لحسابات المستخدمين، إما بشكل فردي أو استنادا إلى عضوية المجموعة.
ms.openlocfilehash: ab9769aa4dee6a9f7982f72f377b0c7e0d3f444e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091402"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>تعيين تراخيص Microsoft 365 لحسابات المستخدمين

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

بالنسبة إلى نموذج الهوية السحابي فقط، يمكنك تعيين تراخيص Microsoft 365 لحسابات المستخدمين عند إنشائها، اعتمادا على كيفية إنشائها.

بالنسبة إلى نموذج الهوية المختلطة، عندما تتم مزامنة حسابات المستخدمين خدمات مجال Active Directory (AD DS) للمرة الأولى، لا يتم تعيين موقع أو ترخيص Microsoft 365 تلقائيا. **يجب تكوين كل حساب مستخدم مع موقع مستخدم قبل تعيين ترخيص أو بجانبه.**

في كلتا الحالتين، يجب تعيين ترخيص لحسابات المستخدمين حتى يتمكن المستخدمون من الوصول إلى خدمات Microsoft 365، مثل البريد الإلكتروني Microsoft Teams.

يمكنك تعيين تراخيص لحسابات المستخدمين إما بشكل فردي أو تلقائيا من خلال عضوية المجموعة.

لتعيين تراخيص Microsoft 365 لحسابات المستخدمين الفردية، يمكنك استخدام:

- [مركز مسؤولي Microsoft 365](../admin/manage/assign-licenses-to-users.md)
- [PowerShell](assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)
- مركز إدارة Azure AD

## <a name="group-based-licensing"></a>الترخيص المستند إلى المجموعة

يمكنك تكوين مجموعات الأمان في Azure AD لتعيين التراخيص تلقائيا من مجموعة من الاشتراكات لجميع أعضاء المجموعة. يعرف هذا باسم *الترخيص المستند إلى المجموعة*. إذا تمت إضافة حساب مستخدم إلى المجموعة أو إزالته منها، فسيتم تعيين تراخيص اشتراكات المجموعة تلقائيا أو إلغاء تعيينها من حساب المستخدم.

تأكد من أن لديك تراخيص كافية لجميع أعضاء المجموعة. إذا نفدت التراخيص، فلن يتم تعيين تراخيص للمستخدمين الجدد حتى تصبح التراخيص متوفرة.

>[!Note]
>يجب عدم تكوين الترخيص المستند إلى المجموعة للمجموعات التي تحتوي على حسابات Azure business to business (B2B).
>

لمزيد من المعلومات، راجع [الترخيص المستند إلى المجموعة في Azure AD](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>الخطوات التالية

مع المجموعة المناسبة من حسابات المستخدمين التي تم تعيين تراخيص لها، أنت الآن جاهز ل:

- [تنفيذ الأمان](../security/office-365-security/security-roadmap.md)
- [نشر برامج العميل، مثل Microsoft 365 Apps](/DeployOffice/deployment-guide-microsoft-365-apps)
- [إعداد إدارة الأجهزة](device-management-roadmap-microsoft-365.md)
- [تكوين الخدمات والتطبيقات](configure-services-and-applications.md)