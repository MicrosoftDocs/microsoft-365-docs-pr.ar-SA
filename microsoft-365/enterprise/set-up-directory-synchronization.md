---
title: إعداد مزامنة الدليل Microsoft 365
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
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: تعرف على كيفية إعداد مزامنة الدليل بين Microsoft 365 Active Directory محلي.
ms.openlocfilehash: 49240d056520a83c0828440e21c5cf26943bae8e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092878"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>إعداد مزامنة الدليل Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يستخدم Microsoft 365 مستأجر Azure Active Directory (Azure AD) لتخزين الهويات وإدارتها للمصادقة والأذونات للوصول إلى الموارد المستندة إلى السحابة. 

إذا كان لديك مجال Active Directory محلي Domain Services (AD DS) أو غابة، يمكنك مزامنة حسابات مستخدمي AD DS والمجموعات وجهات الاتصال مع مستأجر Azure AD لاشتراكك في Microsoft 365. هذه هي الهوية المختلطة Microsoft 365. فيما يلي مكوناته.

![مكونات مزامنة الدليل Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

يعمل Azure AD الاتصال على خادم محلي ويتزامن AD DS مع مستأجر Azure AD. إلى جانب مزامنة الدليل، يمكنك أيضا تحديد خيارات المصادقة هذه:

- مزامنة تجزئة كلمة المرور (PHS)

  يقوم Azure AD بإجراء المصادقة نفسها.

- المصادقة التمريرية (PTA)

  لدى Azure AD AD DS إجراء المصادقة.

- مصادقة جهات الاتصال الخارجية

  يشير Azure AD إلى كمبيوتر العميل الذي يطلب المصادقة إلى موفر هوية آخر.

راجع [الهويات المختلطة](plan-for-directory-synchronization.md) لمزيد من المعلومات.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. مراجعة المتطلبات الأساسية ل Azure AD الاتصال

يمكنك الحصول على اشتراك Azure AD مجاني مع اشتراكك في Microsoft 365. عند إعداد مزامنة الدليل، ستقوم بتثبيت الاتصال Azure AD على أحد الخوادم المحلية.
  
بالنسبة Microsoft 365 ستحتاج إلى:
  
- تحقق من مجالك المحلي. يرشدك معالج الاتصال Azure AD خلال هذا.
- احصل على أسماء المستخدمين وكلمات المرور لحسابات المسؤول لمستأجر Microsoft 365 و AD DS.

بالنسبة إلى الخادم المحلي الذي تقوم بتثبيت Azure AD الاتصال عليه، ستحتاج إلى:
  
|**نظام تشغيل الخادم**|**برامج أخرى**|
|:-----|:-----|
|Windows Server 2012 R2 والإي وقت لاحق | - يتم تثبيت PowerShell بشكل افتراضي، ولا يلزم اتخاذ أي إجراء.  <br> - يتم تقديم Net 4.5.1 والإصدارات الأحدث من خلال Windows Update. تأكد من تثبيت آخر التحديثات إلى Windows Server في لوحة التحكم. |
|Windows Server 2008 R2 مع حزمة الخدمة 1 (SP1)** أو Windows Server 2012 | - يتوفر أحدث إصدار من PowerShell في إطار عمل إدارة Windows 4.0. ابحث عنه في [مركز تنزيل Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - يتوفر .Net 4.5.1 والإصدارات الأحدث في [مركز تنزيل Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008‏ | - يتوفر أحدث إصدار مدعوم من PowerShell في إطار عمل إدارة Windows 3.0، متوفر على [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - يتوفر .Net 4.5.1 والإصدارات الأحدث في [مركز تنزيل Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

راجع [المتطلبات الأساسية ل Azure Active Directory الاتصال](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) للحصول على تفاصيل متطلبات الأجهزة والبرامج والحساب والأذونات ومتطلبات شهادة SSL وحدود العناصر ل Azure AD الاتصال.
  
يمكنك أيضا مراجعة [محفوظات إصدار](/azure/active-directory/hybrid/reference-connect-version-history) Azure AD الاتصال لمعرفة ما هو مضمن ومصلح في كل إصدار.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. تثبيت الاتصال Azure AD وتكوين مزامنة الدليل

قبل البدء، تأكد من أن لديك:

- اسم المستخدم وكلمة المرور لمسؤول عمومي Microsoft 365
- اسم المستخدم وكلمة المرور لمسؤول مجال AD DS
- أسلوب المصادقة (PHS، PTA، موحد)
- ما إذا كنت تريد استخدام [تسجيل الدخول الأحادي السلس إلى Azure AD (SSO)](/azure/active-directory/hybrid/how-to-connect-sso)

اتبع الخطوات التالية:

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) (https://admin.microsoft.com)واختر **"المستخدمون** \> **النشطاء"** على شريط التنقل الأيمن.
2. في صفحة **"المستخدمون النشطون**"، اختر **مزامنة الدليل** **"المزيد**" \> (ثلاث نقاط).
  
3. في صفحة **إعداد Azure Active Directory**، حدد **Go إلى مركز التنزيل للحصول على ارتباط أداة Azure AD الاتصال** للبدء. 
4. اتبع الخطوات الواردة في [الاتصال Azure AD وخريطة طريق تثبيت Azure AD الاتصال Health](/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. إنهاء إعداد المجالات

اتبع الخطوات الواردة في [إنشاء سجلات DNS Microsoft 365 عند إدارة سجلات DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) لإنهاء إعداد المجالات.

## <a name="next-step"></a>الخطوة التالية

[تعيين التراخيص لحسابات المستخدمين](assign-licenses-to-user-accounts.md)