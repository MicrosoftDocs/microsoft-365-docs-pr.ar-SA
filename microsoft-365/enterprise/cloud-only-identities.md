---
title: Microsoft 365 الهوية السحابية فقط
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
description: يصف كيفية إنشاء المستخدمين والمجموعات عندما Microsoft 365 اشتراكك باستخدام هوية السحابة فقط.
ms.openlocfilehash: 81c13a6b7e32883d4cb846ef5956102f08fecd6e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63575291"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 الهوية السحابية فقط

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

إذا اخترت نموذج الهوية السحابية فقط، فإن لديك بالفعل مستأجر Azure Active Directory (Azure AD) لاشتراك Microsoft 365 لتخزين جميع المستخدمين والمجموعات وجهات الاتصال. بعد إعداد حماية حسابات المسؤولين في [الخطوة 2](protect-your-global-administrator-accounts.md) وحسابات المستخدمين في الخطوة [3](microsoft-365-secure-sign-in.md) من هذا الحل، أصبحت الآن جاهزا لبدء إنشاء الحسابات والمجموعات الجديدة التي تحتاجها مؤسستك.

فيما يلي المكونات الأساسية للهوية السحابية فقط.
 
![المكونات الأساسية للهوية السحابية فقط.](../media/about-microsoft-365-identity/cloud-only-identity.png)

يمكن تصنيف المستخدمين وحسابات المستخدمين الخاصة بهم في المؤسسات بعدد من الطرق. على سبيل المثال، بعض الموظفين لديهم حالة دائمة. بعضهم موردون أو متعاقدون أو شركاء لديهم حالة مؤقتة. بعض المستخدمين الخارجيين الذين ليس لديهم حسابات مستخدمين ولكن يجب منحهم حق الوصول إلى خدمات وموارد معينة لدعم التفاعل والتعاون. على سبيل المثال:

- تمثل حسابات المستأجرين المستخدمين داخل مؤسستك الذين تقوم بالترخيص للخدمات السحابية

- تمثل حسابات الأعمال إلى الأعمال (B2B) المستخدمين من خارج مؤسستك الذين تدعوهم للمشاركة في التعاون

اخز أنواع المستخدمين في مؤسستك. ما هي المجموعات؟ على سبيل المثال، يمكنك تجميع المستخدمين حسب وظيفة أو غرض عال المستوى لمجموعتك.

بالإضافة إلى ذلك، يمكن مشاركة بعض الخدمات السحابية مع مستخدمين من خارج مؤسستك بدون أي حسابات مستخدمين. ستحتاج إلى تحديد مجموعات المستخدمين هذه أيضا.

يمكنك استخدام المجموعات في Azure AD لأغراض متعددة تبسط إدارة بيئتك السحابية. على سبيل المثال، باستخدام مجموعات Azure AD، يمكنك:

- استخدم الترخيص المستند إلى المجموعة لتعيين تراخيص Microsoft 365 حسابات المستخدمين تلقائيا بمجرد إضافتها كأعضاء.
- أضف حسابات المستخدمين إلى مجموعات معينة بشكل ديناميكي استنادا إلى سمات حساب المستخدم، مثل اسم القسم.
- توفير المستخدمين تلقائيا للبرامج كخدمة (SaaS) ولحماية الوصول إلى تلك التطبيقات باستخدام المصادقة متعددة العوامل (MFA) ونهج الوصول الشرطي الأخرى.
- توفير الأذونات ومستويات الوصول للفرق SharePoint مواقع الفرق عبر الإنترنت.

## <a name="next-steps-for-cloud-only-identity"></a>الخطوات التالية للهوية السحابية فقط

- [إدارة حسابات المستخدمين](manage-microsoft-365-accounts.md)
- [تعيين تراخيص إلى حسابات المستخدمين](assign-licenses-to-user-accounts.md)
- [إدارة المجموعات وعضوية المجموعة](manage-microsoft-365-groups.md)
- [إدارة كلمات مرور حساب المستخدم](manage-microsoft-365-passwords.md)
