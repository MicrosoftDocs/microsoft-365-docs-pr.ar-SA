---
title: Microsoft 365 هوية السحابة فقط
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
description: يصف كيفية إنشاء المستخدمين والمجموعات عندما يستخدم اشتراكك في Microsoft 365 هوية السحابة فقط.
ms.openlocfilehash: 7b2ad2cee32f075302ea591806214b697fa9b206
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091358"
---
# <a name="microsoft-365-cloud-only-identity"></a>Microsoft 365 هوية السحابة فقط

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

إذا اخترت نموذج الهوية السحابية فقط، فلديك بالفعل مستأجر Azure Active Directory (Azure AD) لاشتراكك في Microsoft 365 لتخزين جميع المستخدمين والمجموعات وجهات الاتصال. بعد إعداد الحماية لحسابات المسؤولين في [الخطوة 2](protect-your-global-administrator-accounts.md) وحسابات المستخدمين في [الخطوة 3](microsoft-365-secure-sign-in.md) من هذا الحل، أنت الآن جاهز لبدء إنشاء الحسابات والمجموعات الجديدة التي تحتاجها مؤسستك.

فيما يلي المكونات الأساسية للهوية السحابية فقط.
 
![المكونات الأساسية للهوية السحابية فقط.](../media/about-microsoft-365-identity/cloud-only-identity.png)

يمكن تصنيف المستخدمين وحساباتهم في المؤسسات بعدد من الطرق. على سبيل المثال، بعض الموظفين ولديهم حالة دائمة. وبعضهم من الموردين أو المقاولين أو الشركاء الذين لديهم حالة مؤقتة. بعض المستخدمين الخارجيين الذين ليس لديهم حسابات مستخدمين ولكن يجب منحهم حق الوصول إلى خدمات وموارد معينة لدعم التفاعل والتعاون. على سبيل المثال:

- تمثل حسابات المستأجرين المستخدمين داخل مؤسستك الذين تقوم بترخيصهم للخدمات السحابية

- تمثل حسابات الأعمال إلى الأعمال (B2B) المستخدمين من خارج مؤسستك الذين تدعوهم للمشاركة في التعاون

يمكنك تقييم أنواع المستخدمين في مؤسستك. ما هي المجموعات؟ على سبيل المثال، يمكنك تجميع المستخدمين حسب وظيفة عالية المستوى أو غرض لمؤسستك.

بالإضافة إلى ذلك، يمكن مشاركة بعض الخدمات السحابية مع مستخدمين من خارج مؤسستك دون أي حسابات مستخدمين. ستحتاج إلى تحديد مجموعات المستخدمين هذه أيضا.

يمكنك استخدام المجموعات في Azure AD لعدة أغراض تبسط إدارة بيئة السحابة الخاصة بك. على سبيل المثال، باستخدام مجموعات Azure AD، يمكنك:

- استخدم الترخيص المستند إلى المجموعة لتعيين تراخيص Microsoft 365 لحسابات المستخدمين تلقائيا بمجرد إضافتها كأعضاء.
- إضافة حسابات المستخدمين إلى مجموعات معينة بشكل ديناميكي استنادا إلى سمات حساب المستخدم، مثل اسم القسم.
- توفير المستخدمين تلقائيا لتطبيقات خدمة تأجير البرامج (SaaS) وحماية الوصول إلى تلك التطبيقات باستخدام المصادقة متعددة العوامل (MFA) ونهج الوصول المشروط الأخرى.
- توفير الأذونات ومستويات الوصول للفرق ومواقع الفرق SharePoint Online.

## <a name="next-steps-for-cloud-only-identity"></a>الخطوات التالية للهوية السحابية فقط

- [إدارة حسابات المستخدمين](manage-microsoft-365-accounts.md)
- [تعيين التراخيص لحسابات المستخدمين](assign-licenses-to-user-accounts.md)
- [إدارة المجموعات وعضوية المجموعة](manage-microsoft-365-groups.md)
- [إدارة كلمات مرور حساب المستخدم](manage-microsoft-365-passwords.md)
