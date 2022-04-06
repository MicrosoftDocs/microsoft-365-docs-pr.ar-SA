---
title: التطبيقات المتكاملة و Azure AD لمسؤولي Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: تعرف على كيفية تسجيل التطبيقات Office 365 وإدارتها في Azure AD، مما يسمح بتخويلات التطبيق على **مسؤول Azure AD DC** أو مستوى **المسؤول العام.**
ms.openlocfilehash: ddb22c6e1be3d337fe7b54f27cae6a197f823c71
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681249"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>التطبيقات المتكاملة و Azure AD لمسؤولي Microsoft 365

هناك ما هو أكثر من مجرد إدارة التطبيقات المتكاملة بدلا من مجرد [إدارة موافقة المستخدم على التطبيقات](../admin/misc/user-consent.md). مع ظهور واجهات برمجة تطبيقات REST Microsoft 365، يمكن للمستخدمين منح التطبيقات حق الوصول إلى بيانات Microsoft 365 الخاصة بهم، مثل البريد والتقويمات وجهات الاتصال والمستخدمين والمجموعات والملفات والمجلدات. بشكل افتراضي، يحتاج المستخدمون إلى منح أذونات لكل تطبيق بشكل فردي. 

ولكن هذا لا يحدث بشكل جيد إذا كنت تريد تخويل تطبيق مرة واحدة على **مسؤول Azure AD DC**، أو على مستوى  المسؤول العام وإدراجه في مؤسستك بكاملها من خلال محرر التطبيق. للقيام بذلك، يجب تسجيل التطبيق في Azure Active Directory (Azure AD). هناك بعض الخطوات التي يجب اتخاذها قبل أن تتمكن من تسجيل تطبيق في Azure AD وبعض المعلومات الخلفية التي يجب أن تعرفها من الممكن أن تساعدك على إدارة التطبيقات في Microsoft 365 مؤسستك.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>موارد Azure AD لمسؤولي Microsoft 365

يجب تنفيذ هاتين المهمتين قبل أن تتمكن من إدارة تطبيقاتك Microsoft 365 Azure AD.
  
|المتطلبات الأساسية|التعليقات|
|:-----|:-----|
|[استخدام اشتراك Azure AD المجاني](../compliance/use-your-free-azure-ad-subscription-in-office-365.md) <br/> |يأتي كل اشتراك مدفوع Microsoft 365 اشتراك مجاني في Azure AD. يمكنك استخدام Azure AD لإدارة تطبيقاتك وإنشاء حسابات المستخدمين وحسابات المجموعات وإدارتها. لاستخدام Azure AD، ما عليك سوى الانتقال إلى مدخل Azure [https://portal.azure.com](https://portal.azure.com) في تسجيل الدخول باستخدام حساب Microsoft 365 الخاص بك.  <br/> |
|[إدارة موافقة المستخدم على التطبيقات](../admin/misc/user-consent.md) <br/> |يجب عليك إدارة موافقة المستخدم على التطبيقات للسماح لتطبيقات جهة خارجية بالوصول إلى Microsoft 365 المستخدمين وتسجيل التطبيقات في Azure AD. على سبيل المثال، عندما يستخدم شخص ما تطبيقا من جهة خارجية، قد يطلب هذا التطبيق الإذن للوصول إلى تقويمه وتحرير الملفات الموجودة في مجلد OneDrive مجلد.  <br/> |
   
تتطلب Microsoft 365 إدارة التطبيقات أن تكون على دراية للتطبيقات في Azure AD. استخدم هذه المقالات لتعطيك الخلفية التي تحتاج إليها.
  
|مقالة|التعليقات|
|:-----|:-----|
|[تعرف على Microsoft 365 التطبيق](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |إذا لم يكن لديك أي جديد في تشغيل التطبيق، فقد تتساءل عن ماهيته وكيفية استخدامه. لقد تم تصميم "تشغيل التطبيق" لمساعدتك على الوصول إلى تطبيقاتك من أي مكان في Microsoft 365.  <br/> |
|[Office 365 نظرة عامة على واجهات برمجة التطبيقات لإدارة التطبيقات](/office/office-365-management-api/office-365-management-apis-overview) <br/> |تسمح Microsoft 365 برمجة التطبيقات لإدارة البيانات بتوفير الوصول إلى بيانات Microsoft 365 الخاصة بك، بما في ذلك الأشياء التي تهتم بها أكثر— البريد والتقويمات وجهات الاتصال والمستخدمين والمجموعات والملفات والمجلدات الخاصة بهم. <br/> |
|[دمج التطبيقات في Azure AD](/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | تعرف على التطبيقات المتكاملة مع Azure AD، وكيفية تسجيل التطبيق، وفهم المفاهيم وراء تطبيق مسجل، وتعرف على إرشادات العلامة التجارية لتطبيقات متعددة المستأجرين.  <br/> |
|[إضافة تجانبات مخصصة إلى ومطلق التطبيق](/office365/admin/manage/customize-the-app-launcher)  <br/> |يسهل Microsoft 365 التطبيق على المستخدمين العثور على تطبيقاتهم والوصول إليها. تصف هذه المقالة الطرق التي يمكنك استخدامها كمطور لكي تظهر تطبيقاتك في برامج تشغيل التطبيقات الخاصة بالمستخدمين، كما تمنحهم تجربة تسجيل الدخول (SSO) واحدة باستخدام بيانات Microsoft 365 الخاصة بهم.  <br/> |
|[برامج تعليمية حول تكامل Azure AD](/azure/active-directory/saas-apps/tutorial-list) <br/> |الهدف من هذه البرامج التعليمية هو أن تظهر لك كيفية تكوين Azure AD SSO في تطبيقات SaaS الخاصة ب جهة خارجية.  <br/> |
|[سيناريوهات المصادقة ل Azure AD](/azure/active-directory/develop/authentication-vs-authorization) <br/> |يبسط Azure AD المصادقة للمطورين من خلال توفير الهوية كخدمة، مع دعم البروتوكولات القياسية الصناعية مثل OAuth 2.0 و OpenID الاتصال، بالإضافة إلى مكتبات المصادر المفتوحة ل الأنظمة الأساسية المختلفة لمساعدتك على بدء الترميز بسرعة. يساعدك هذا المستند على فهم السيناريوهات المختلفة التي يدعمها Azure AD ويظهر لك كيفية البدء.  <br/> |
|[الوصول إلى التطبيق](/azure/active-directory/manage-apps/what-is-access-management) <br/> |يتيح Azure AD التكامل السهل مع العديد من البرامج الشائعة اليوم كخدمة (SaaS) تطبيقات. فهو يوفر إدارة الهوية والوصول، ويوفر لوحة Access للمستخدمين حيث يمكنهم اكتشاف الوصول إلى التطبيقات التي لديهم وحيث يمكنهم استخدام SSO للوصول إلى تطبيقاتهم. توفر لك هذه المقالة ارتباطات إلى الموارد ذات الصلة التي تمكنك من معرفة المزيد حول تحسينات الوصول إلى التطبيق ل Azure AD وكيفية المساهمة فيها.  <br/> |
|[تخصيص تجربتك Office 365](https://support.microsoft.com/office/personalize-your-office-365-experience-eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |يمكنك الوصول السريع إلى التطبيقات التي تستخدمها كل يوم عن طريق إضافة التطبيقات أو إزالتها في Microsoft 365 التطبيق.  <br/> |
