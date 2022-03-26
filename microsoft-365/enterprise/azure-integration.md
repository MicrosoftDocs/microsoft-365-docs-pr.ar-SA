---
title: تكامل Azure مع Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: ادمج Microsoft 365 مع Azure AD إذا كنت تريد مزامنة كلمة المرور أو تسجيل الدخول مرة واحدة مع بيئتك المحلية.
ms.openlocfilehash: 2d560c2d94552b91c4325a74f99d2f34aa1af399
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63568795"
---
# <a name="azure-integration-with-microsoft-365"></a>تكامل Azure مع Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

Microsoft 365 Azure Active Directory (Azure AD) لإدارة هويات المستخدمين في الكواليس. يتضمن Microsoft 365 اشتراك Azure AD مجانيا بحيث يمكنك دمج خدمات مجال Active Directory المحلية (AD DS) لمزامنة حسابات المستخدمين وكلمات المرور أو إعداد تسجيل الدخول الفردي. يمكنك أيضا شراء ميزات متقدمة لإدارة حساباتك بشكل أفضل.
  
يوفر Azure AD أيضا وظائف أخرى، مثل إدارة التطبيقات المتكاملة، التي يمكنك استخدامها لتوسيع اشتراكاتك وتخصيصها Microsoft 365 اشتراكاتك.
  
يمكنك استخدام مستشاري نشر Azure AD لتجربة إعداد وتكوين موجهة في مركز مسؤولي Microsoft 365 (يجب أن تكون قد قمت Microsoft 365):

 - [مستشار Azure AD الاتصال Azure](https://aka.ms/aadconnectpwsync)
 - [مستشار نشر AD FS](https://aka.ms/adfsguidance)
 - [دليل إعداد Azure AD](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-microsoft-365-identity-management"></a>إصدارات Azure AD Microsoft 365 إدارة الهويات

إذا كان لديك اشتراك مدفوع Microsoft 365، فإن لديك أيضا اشتراك Azure AD مجاني. يمكنك استخدام Azure AD لإنشاء حسابات المستخدمين وحسابات المجموعات وإدارتها. لتنشيط هذا الاشتراك، يجب إكمال التسجيل مرة واحدة. بعد ذلك، يمكنك الوصول إلى Azure AD من مركز مسؤولي Microsoft 365. 

للحصول على إرشادات لتسجيل اشتراك Azure AD المجاني، راجع [استخدام اشتراك Azure AD المجاني](../compliance/use-your-free-azure-ad-subscription-in-office-365.md). لا تذهب مباشرة إلى azure.microsoft.com التسجيل أو سينتهي بك المطاف باشتراك تجريبي أو مدفوع في Microsoft Azure منفصل عن اشتراك Azure AD المجاني مع Microsoft 365. 
  
باستخدام الاشتراك المجاني، يمكنك المزامنة مع الدلائل في الموقع، إعداد تسجيل الدخول الفردي، والمزامنة مع العديد من البرامج مثل تطبيقات الخدمة، مثل Salesforce و DropBox والمزيد.
  
إذا كنت تريد تحسين وظائف AD DS والمزامنة ثنائية الاتجاه وإمكانيات الإدارة الأخرى، يمكنك ترقية اشتراكك المجاني إلى اشتراك مدفوع premium. للحصول على التفاصيل، راجع [إصدارات Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).
  
لمزيد من المعلومات حول Microsoft 365 و Azure AD، راجع Microsoft 365 [الهوية.](deploy-identity-solution-identity-model.md)
  
## <a name="extend-the-capabilities-of-your-microsoft-365-tenant"></a>توسيع قدرات المستأجر Microsoft 365 المستأجر

|**الميزة**|**الوصف**|
|:-----|:-----|
|التطبيقات المتكاملة  <br/> |يمكنك منح التطبيقات الفردية حق الوصول إلى Microsoft 365 الخاصة بك، مثل البريد والتقويمات وجهات الاتصال والمستخدمين والمجموعات والملفات والمجلدات. يمكنك أيضا تخويل هذه التطبيقات على **مسؤول Azure AD DC** أو على  مستوى المسؤول العام وجعلها متوفرة للشركة بأكملها من خلال تسجيل التطبيقات في Azure AD. لمزيد من المعلومات، راجع التطبيقات المتكاملة و [Azure AD لمسؤولي Microsoft 365.](integrated-apps-and-azure-ads.md)<br/> لمزيد من المعلومات، راجع [حول أدوار المسؤولين](/microsoft-365/admin/add-users/about-admin-roles?). <br/> راجع أيضا [تسجيل الدخول المفرد](/azure/active-directory/manage-apps/what-is-single-sign-on).  <br/> |
|تطبيقات الطاقة  <br/> | تطبيقات Power Apps هي تطبيقات مركزة للأجهزة المحمولة التي يمكنها الاتصال ومصادر البيانات الموجودة لديك مثل SharePoint وتطبيقات البيانات الأخرى. راجع [إنشاء Power App لقائمة](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) في SharePoint Online وصفحة [Power Apps](https://powerapps.microsoft.com/) للحصول على التفاصيل.  <br/> |
   
## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 Enterprise عامة](microsoft-365-overview.md)
