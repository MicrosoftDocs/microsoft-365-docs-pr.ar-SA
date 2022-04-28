---
title: تكامل Azure مع Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-identity-device-management
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: دمج Microsoft 365 مع Azure AD إذا كنت تريد مزامنة كلمة المرور أو تسجيل الدخول الأحادي مع البيئة المحلية.
ms.openlocfilehash: bebbad10d0fb7a61437dcb24398ebb88d90db739
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096821"
---
# <a name="azure-integration-with-microsoft-365"></a>تكامل Azure مع Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يستخدم Microsoft 365 Azure Active Directory (Azure AD) لإدارة هويات المستخدمين في الخلفية. يتضمن اشتراكك في Microsoft 365 اشتراك Azure AD مجانيا بحيث يمكنك دمج Active Directory محلي Domain Services (AD DS) لمزامنة حسابات المستخدمين وكلمات المرور أو إعداد تسجيل الدخول الأحادي. يمكنك أيضا شراء ميزات متقدمة لإدارة حساباتك بشكل أفضل.
  
يوفر Azure AD أيضا وظائف أخرى، مثل إدارة التطبيقات المتكاملة، التي يمكنك استخدامها لتوسيع وتخصيص اشتراكات Microsoft 365.
  
يمكنك استخدام مستشاري نشر Azure AD لإعداد موجه وتجربة تكوين في مركز مسؤولي Microsoft 365 (يجب تسجيل الدخول إلى Microsoft 365):

 - [مستشار الاتصال Azure AD](https://aka.ms/aadconnectpwsync)
 - [مستشار نشر AD FS](https://aka.ms/adfsguidance)
 - [دليل إعداد Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>إصدارات Azure AD وإدارة الهوية Microsoft 365

إذا كان لديك اشتراك مدفوع في Microsoft 365، فلديك أيضا اشتراك Azure AD مجاني. يمكنك استخدام Azure AD لإنشاء حسابات المستخدمين والمجموعة وإدارتها. لتنشيط هذا الاشتراك، يجب عليك إكمال التسجيل لمرة واحدة. بعد ذلك، يمكنك الوصول إلى Azure AD من مركز مسؤولي Microsoft 365. 

للحصول على إرشادات لتسجيل اشتراك Azure AD المجاني، راجع [استخدام اشتراك Azure AD المجاني](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). لا تنتقل مباشرة إلى azure.microsoft.com للتسجيل أو سينتهي بك الأمر باشتراك تجريبي أو مدفوع إلى Microsoft Azure منفصل عن اشتراك Azure AD المجاني مع Microsoft 365. 
  
باستخدام الاشتراك المجاني، يمكنك المزامنة مع الدلائل المحلية، وإعداد تسجيل الدخول الأحادي، والمزامنة مع العديد من البرامج مثل تطبيقات الخدمة، مثل Salesforce وDropBox وغيرها الكثير.
  
إذا كنت تريد وظائف AD DS المحسنة والمزامنة ثنائية الاتجاه وقدرات الإدارة الأخرى، يمكنك ترقية اشتراكك المجاني إلى اشتراك متميز مدفوع. للحصول على التفاصيل، راجع [إصدارات Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).
  
لمزيد من المعلومات حول Microsoft 365 وAzure AD، راجع [نماذج الهوية Microsoft 365](deploy-identity-solution-identity-model.md).
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>توسيع قدرات مستأجر Microsoft 365

|**ميزه**|**الوصف**|
|:-----|:-----|
|تطبيقات متكاملة  <br/> |يمكنك منح التطبيقات الفردية حق الوصول إلى بيانات Microsoft 365، مثل البريد والتقويمات وجهات الاتصال والمستخدمين والمجموعات والملفات والمجلدات. يمكنك أيضا تخويل هذه التطبيقات على **مسؤول Azure AD DC**، أو مستوى **المسؤول العام** وجعلها متاحة لشركتك بأكملها عن طريق تسجيل التطبيقات في Azure AD. لمزيد من المعلومات، راجع [التطبيقات المتكاملة وAzure AD لمسؤولي Microsoft 365](integrated-apps-and-azure-ads.md).<br/> لمزيد من المعلومات، راجع [حول أدوار المسؤولين](/microsoft-365/admin/add-users/about-admin-roles?). <br/> راجع أيضا [تسجيل الدخول الأحادي](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|تطبيقات الطاقة  <br/> | Power Apps هي تطبيقات تركز على الأجهزة المحمولة التي يمكنها الاتصال بمصادر البيانات الموجودة لديك مثل قوائم SharePoint وتطبيقات البيانات الأخرى. راجع [إنشاء Power App لقائمة في SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) [وصفحة Power Apps](https://powerapps.microsoft.com/) للحصول على التفاصيل.  <br/> |
   
## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على Microsoft 365 Enterprise](microsoft-365-overview.md)
