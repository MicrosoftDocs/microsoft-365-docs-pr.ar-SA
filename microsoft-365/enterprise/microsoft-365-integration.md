---
title: Microsoft 365 التكامل مع البيئات المحلية
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: في هذه المقالة، تعرف على كيفية Microsoft 365 مع خدمات الدليل الموجودة والبيئات المحلية.
ms.openlocfilehash: ca407e6cb77f829b4c6e8de680772817659aeeec
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63570026"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Microsoft 365 التكامل مع البيئات المحلية

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك دمج Microsoft 365 مع خدمات مجال Active Directory المحلية (AD DS) والتثبيتات المحلية ل Exchange Server أو Skype for Business Server 2015 أو SharePoint Server.
  
 - عند دمج AD DS، يمكنك مزامنة حسابات المستخدمين وإدارتها للبيئات. يمكنك أيضا إضافة مزامنة كلمة المرور المتزامنة (PHS) أو تسجيل الدخول الفردي (SSO) بحيث يمكن للمستخدمين تسجيل الدخول إلى كلتا البيئات باستخدام بيانات الاعتماد المحلية الخاصة بهم.
 - عند التكامل مع منتجات الخادم المحلية، يمكنك إنشاء بيئة مختلطة. يمكن أن تساعدك البيئة المختلطة عند ترحيل المستخدمين أو المعلومات Microsoft 365، أو يمكنك الاستمرار في الحصول على بعض المستخدمين أو بعض المعلومات المحلية والبعض في السحابة. لمزيد من المعلومات حول البيئات المختلطة، راجع [السحابة المختلطة](../solutions/cloud-architecture-models.md#hybrid).

يمكنك أيضا استخدام مستشاري Azure Active Directory (Azure AD) للحصول على إرشادات الإعداد المخصصة في مركز مسؤولي Microsoft 365 (يجب أن تكون قد قمت Microsoft 365):

- [دليل إعداد Azure AD](https://aka.ms/aadpguidance)
- [مزامنة المستخدمين من دليل المؤسسة](https://aka.ms/aadconnectpwsync)
- [مستشار نشر خدمات اتحاد Active Directory (AD FS)](https://aka.ms/adfsguidance)
   
## <a name="before-you-begin"></a>قبل البدء

قبل دمج Microsoft 365 وبيئة العمل المحلية، ستحتاج أيضا إلى تخطيط الشبكة [وضبط الأداء](network-planning-and-performance.md). وسترغب أيضا في فهم نماذج [الهوية المتوفرة](deploy-identity-solution-identity-model.md). 

راجع [إدارة Microsoft 365 الحسابات](manage-microsoft-365-accounts.md) للحصول على قائمة الأدوات التي يمكنك استخدامها لإدارة Microsoft 365 المستخدمين. 
  
## <a name="integrate-microsoft-365-with-ad-ds"></a>تكامل Microsoft 365 مع AD DS

إذا كان لديك حسابات مستخدمين موجودة في AD DS، فلا تريد إعادة إنشاء كل هذه الحسابات في Microsoft 365 والمخاطرة بإدخال الاختلافات أو الأخطاء بين البيئات. تساعدك مزامنة الدليل على انعكاس تلك الحسابات بين البيئات المحلية والبيئات عبر الإنترنت. باستخدام مزامنة الدليل، لن يحتاج المستخدمون إلى تذكر معلومات جديدة لكل بيئة، ولا تحتاج إلى إنشاء حسابات أو تحديثها مرتين. ستحتاج إلى [إعداد الدليل](prepare-for-directory-synchronization.md) في الموقع لمزامنة الدليل.
  
![استخدم مزامنة الدليل للحفاظ على مزامنة معلومات حساب المستخدم على الإنترنت أو الموقع.](../media/microsoft-365-integration/directory-synchronization.png)
  
إذا كنت تريد أن يتمكن المستخدمون من تسجيل الدخول Microsoft 365 بيانات الاعتماد الخاصة بهم في الموقع، يمكنك أيضا تكوين SSO. باستخدام SSO، يتم Microsoft 365 الثقة في البيئة المحلية لمصادقة المستخدم.
  
![عند تسجيل الدخول مرة واحدة، يتوفر الحساب نفسه في كل من البيئات المحلية والبيئات عبر الإنترنت.](../media/microsoft-365-integration/single-sign-on.png)

### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication-pta"></a>مزامنة الدليل مع مزامنة كلمة المرور أو المصادقة المرورية (PTA) أو بدونها

يقوم المستخدم بتسجيل الدخول إلى بيئته المحلية باستخدام حساب المستخدم الخاص به (المجال\اسم المستخدم). عند الانتقال إلى Microsoft 365، يجب عليهم تسجيل الدخول مرة أخرى باستخدام حساب العمل أو المدرسة (user@domain.com). اسم المستخدم هو نفسه في كلتا البيئات. عند إضافة PHS أو PTA، يكون لدى المستخدم كلمة المرور نفسها للبيئات، ولكن يجب توفير بيانات الاعتماد هذه مرة أخرى عند تسجيل الدخول إلى Microsoft 365. مزامنة الدليل مع PHS هي مزامنة الدليل الأكثر استخداما.

لإعداد مزامنة الدليل، استخدم Azure AD الاتصال. للحصول على الإرشادات، [](set-up-directory-synchronization.md) راجع إعداد مزامنة الدليل Microsoft 365 [و Azure AD الاتصال إعدادات صريحة](/azure/active-directory/hybrid/how-to-connect-install-express).

تعرف على المزيد [حول التحضير لمزامنة الدليل Microsoft 365](prepare-for-directory-synchronization.md).

### <a name="directory-synchronization-with-sso"></a>مزامنة الدليل مع SSO

يقوم المستخدم بتسجيل الدخول إلى بيئته المحلية باستخدام حساب المستخدم الخاص به. عند الانتقال إلى Microsoft 365، يتم تسجيل دخولهم تلقائيا، أو يسجلون دخولهم باستخدام بيانات الاعتماد نفسها التي يستخدمونها لبيئة العمل المحلية (المجال\اسم المستخدم).

لإعداد SSO، يمكنك أيضا استخدام Azure AD الاتصال. للحصول على الإرشادات، راجع [التثبيت المخصص ل Azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-install-custom).

لمزيد من المعلومات، راجع [تسجيل الدخول المفرد](/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="azure-ad-connect"></a>Azure AD Connect

يحل azure AD الاتصال إصدارات قديمة من أدوات تكامل الهوية مثل DirSync ومزامنة Azure AD. إذا كنت تريد التحديث من مزامنة Azure Active Directory إلى Azure AD الاتصال، فشاهد [إرشادات الترقية](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started). 

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 Enterprise عامة](microsoft-365-overview.md)