---
title: تكامل Microsoft 365 مع البيئات المحلية
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: في هذه المقالة، تعرف على كيفية تكامل Microsoft 365 مع خدمات الدليل الحالية والبيئات المحلية.
ms.openlocfilehash: a3ba75fd2f2b69e71d5b14b14e17827ed96e4dd4
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093888"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>تكامل Microsoft 365 مع البيئات المحلية

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك دمج Microsoft 365 مع خدمات مجال Active Directory محلي الموجودة (AD DS) ومع عمليات التثبيت المحلية لخادم Exchange Server أو Skype for Business Server 2015 أو SharePoint.
  
 - عند دمج AD DS، يمكنك مزامنة حسابات المستخدمين وإدارتها لكلا البيئتين. يمكنك أيضا إضافة مزامنة تجزئة كلمة المرور (PHS) أو تسجيل الدخول الأحادي (SSO) حتى يتمكن المستخدمون من تسجيل الدخول إلى كلتا البيئتين باستخدام بيانات الاعتماد المحلية الخاصة بهم.
 - عند التكامل مع منتجات الخادم المحلية، يمكنك إنشاء بيئة مختلطة. يمكن أن تساعد البيئة المختلطة في أثناء ترحيل المستخدمين أو المعلومات إلى Microsoft 365، أو يمكنك الاستمرار في الحصول على بعض المستخدمين أو بعض المعلومات المحلية والبعض في السحابة. لمزيد من المعلومات حول البيئات المختلطة، راجع [السحابة المختلطة](../solutions/cloud-architecture-models.md#hybrid).

يمكنك أيضا استخدام مستشاري Azure Active Directory (Azure AD) لإرشادات الإعداد المخصصة في مركز مسؤولي Microsoft 365 (يجب تسجيل الدخول إلى Microsoft 365):

- [دليل إعداد Azure AD](https://aka.ms/aadpguidance)
- [مزامنة المستخدمين من دليل مؤسستك](https://aka.ms/aadconnectpwsync)
- [مستشار نشر خدمات الأمان المشترك لـ Active Directory (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>قبل البدء

قبل دمج Microsoft 365 والبيئة المحلية، تحتاج أيضا إلى تخطيط [الشبكة وضبط الأداء](network-planning-and-performance.md). ستحتاج أيضا إلى فهم [نماذج الهوية](deploy-identity-solution-identity-model.md) المتاحة. 

راجع [إدارة حسابات Microsoft 365](manage-microsoft-365-accounts.md) للحصول على قائمة بالأدوات التي يمكنك استخدامها لإدارة حسابات المستخدمين Microsoft 365. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>دمج Microsoft 365 مع AD DS

إذا كان لديك حسابات مستخدمين موجودة في AD DS، فلا تريد إعادة إنشاء كل هذه الحسابات في Microsoft 365 والمخاطرة بإدخال اختلافات أو أخطاء بين البيئات. تساعدك مزامنة الدليل على عكس تلك الحسابات بين البيئات المحلية والبيئات عبر الإنترنت. باستخدام مزامنة الدليل، لن يضطر المستخدمون إلى تذكر معلومات جديدة لكل بيئة، ولا يتعين عليك إنشاء حسابات أو تحديثها مرتين. ستحتاج إلى [إعداد الدليل المحلي](prepare-for-directory-synchronization.md) لمزامنة الدليل.
  
![استخدم مزامنة الدليل للاحتفاظ بمعلومات حساب المستخدم المحلي وعلى الإنترنت متزامنة.](../media/microsoft-365-integration/directory-synchronization.png)
  
إذا كنت تريد تمكين المستخدمين من تسجيل الدخول إلى Microsoft 365 باستخدام بيانات الاعتماد المحلية الخاصة بهم، يمكنك أيضا تكوين تسجيل الدخول الأحادي. مع تسجيل الدخول الأحادي، يتم تكوين Microsoft 365 للثقة في البيئة المحلية لمصادقة المستخدم.
  
![مع تسجيل الدخول الأحادي، يتوفر نفس الحساب في كل من البيئات المحلية والبيئات عبر الإنترنت.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>مزامنة الدليل مع مزامنة تجزئة كلمة المرور أو بدونها أو المصادقة التمريرية (PTA)

يسجل المستخدم الدخول إلى بيئته المحلية باستخدام حساب المستخدم الخاص به (المجال\اسم المستخدم). عندما ينتقلون إلى Microsoft 365، يجب عليهم تسجيل الدخول مرة أخرى باستخدام حساب العمل أو المؤسسة التعليمية (user@domain.com). اسم المستخدم هو نفسه في كلتا البيئتين. عند إضافة PHS أو PTA، يكون لدى المستخدم نفس كلمة المرور لكلا البيئتين، ولكن سيتعين عليه توفير بيانات الاعتماد هذه مرة أخرى عند تسجيل الدخول إلى Microsoft 365. مزامنة الدليل مع PHS هي مزامنة الدليل الأكثر استخداما.

لإعداد مزامنة الدليل، استخدم الاتصال Azure AD. للحصول على الإرشادات، راجع [إعداد مزامنة الدليل Microsoft 365](set-up-directory-synchronization.md) [وAzure AD الاتصال مع الإعدادات السريعة](/azure/active-directory/hybrid/how-to-connect-install-express).

تعرف على المزيد حول [التحضير لمزامنة الدليل مع Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>مزامنة الدليل مع تسجيل الدخول الأحادي

يسجل المستخدم الدخول إلى بيئته المحلية باستخدام حساب المستخدم الخاص به. عند الانتقال إلى Microsoft 365، يتم إما تسجيل الدخول تلقائيا، أو تسجيل الدخول باستخدام نفس بيانات الاعتماد التي يستخدمونها للبيئة المحلية (المجال\اسم المستخدم).

لإعداد تسجيل الدخول الأحادي، يمكنك أيضا استخدام الاتصال Azure AD. للحصول على الإرشادات، راجع [التثبيت المخصص ل Azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-install-custom).

لمزيد من المعلومات، راجع [تسجيل الدخول الأحادي](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

يستبدل azure AD الاتصال الإصدارات القديمة من أدوات تكامل الهوية مثل DirSync وAzure AD Sync. إذا كنت تريد التحديث من Azure Active Directory Sync إلى الاتصال Azure AD، فراجع [إرشادات الترقية](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على Microsoft 365 Enterprise](microsoft-365-overview.md)