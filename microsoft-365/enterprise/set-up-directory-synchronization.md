---
title: إعداد مزامنة الدليل Microsoft 365
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
description: تعرف على كيفية إعداد مزامنة الدليل بين Microsoft 365 و Active Directory الخاص بك.
ms.openlocfilehash: 61b2dd822d0e65ebbf97ddcbfc3c8a03887c45a6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575280"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>إعداد مزامنة الدليل Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

Microsoft 365 المستأجر Azure Active Directory (Azure AD) لتخزين الهويات وإدارتها للمصادقة والأذونات للوصول إلى الموارد المستندة إلى السحابة. 

إذا كان لديك مجال أو غابة خدمات مجال Active Directory (AD DS) المحلي، يمكنك مزامنة حسابات المستخدمين والمجموعات وجهات الاتصال في AD DS مع مستأجر Azure AD لاشتراكك في خدمة Microsoft 365 AD. هذه هي الهوية المختلطة Microsoft 365. فيما يلي مكوناته.

![مكونات مزامنة الدليل Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

يتم تشغيل الاتصال Azure AD على خادم في الموقع ويزامن AD DS مع مستأجر Azure AD. إلى جانب مزامنة الدليل، يمكنك أيضا تحديد خيارات المصادقة التالية:

- مزامنة كلمة المرور (PHS)

  يقوم Azure AD بتنفيذ المصادقة نفسها.

- المصادقة المرورية (PTA)

  يقوم Azure AD ب AD DS بتنفيذ المصادقة.

- المصادقة الخارجية

  يشير Azure AD إلى كمبيوتر العميل الذي يطلب المصادقة إلى موفر هوية آخر.

لمزيد [من المعلومات، راجع الهويات](plan-for-directory-synchronization.md) المختلطة.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. مراجعة المتطلبات الأساسية ل Azure AD الاتصال

يمكنك الحصول على اشتراك Azure AD مجاني مع Microsoft 365 اشتراكك. عند إعداد مزامنة الدليل، سيتم تثبيت Azure AD الاتصال على أحد الخوادم في الموقع.
  
على Microsoft 365 ستحتاج إلى:
  
- تحقق من المجال الخاص بك في الموقع. يرشدك معالج Azure AD الاتصال خلال هذا الأمر.
- احصل على أسماء المستخدمين وكلمات المرور لحسابات المسؤولين في Microsoft 365 المستأجر وDD DS.

بالنسبة للخادم الذي تقوم بتثبيت Azure AD عليه الاتصال، ستحتاج إلى:
  
|**نظام تشغيل الخادم**|**برامج أخرى**|
|:-----|:-----|
|Windows Server 2012 R2 واللاحقة | - يتم تثبيت PowerShell بشكل افتراضي، ولا يلزم اتخاذ أي إجراء.  <br> - يتم عرض Net 4.5.1 وال الإصدارات اللاحقة من خلال Windows Update. تأكد من تثبيت التحديثات الأخيرة Windows Server في لوحة التحكم. |
|Windows Server 2008 R2 مع حزمة الخدمة 1 (SP1)** أو Windows Server 2012 | - يتوفر الإصدار الأخير من PowerShell في إطار عمل إدارة Windows 4.0. ابحث عنه في [مركز التنزيل ل Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - يتوفر .Net 4.5.1 وال الإصدارات اللاحقة في [مركز التنزيل ل Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008‏ | - يتوفر أحدث إصدار مدعوم من PowerShell في إطار عمل إدارة Windows 3.0، المتوفر في [مركز التنزيل من Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - يتوفر .Net 4.5.1 وال الإصدارات اللاحقة في [مركز التنزيل ل Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

راجع المتطلبات الأساسية ل [Azure Active Directory الاتصال](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) للحصول على تفاصيل متطلبات الأجهزة والبرامج الحساب والأذونات ومتطلبات شهادة SSL وحدود الكائنات ل Azure AD الاتصال.
  
يمكنك أيضا مراجعة محفوظات إصدار Azure AD الاتصال لمعرفة ما هو [](/azure/active-directory/hybrid/reference-connect-version-history) مضمن ومصلح في كل إصدار.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. تثبيت Azure AD الاتصال مزامنة الدليل وتكوينها

قبل البدء، تأكد من أن لديك:

- اسم المستخدم وكلمة المرور لمسؤول Microsoft 365 عام
- اسم المستخدم وكلمة المرور لمسؤول مجال AD DS
- أسلوب المصادقة (PHS، PTA، المتحدة)
- ما إذا كنت تريد استخدام تسجيل الدخول الفردي السلس من [Azure AD (SSO)](/azure/active-directory/hybrid/how-to-connect-sso)

اتبع الخطوات التالية:

1. سجل الدخول [إلى مركز مسؤولي Microsoft 365 (](https://admin.microsoft.com)https://admin.microsoft.com) واختر **المستخدمون** \> **النشطون** على التنقل الأيسر.
2. في صفحة **المستخدمون النشطون** ، اختر **المزيد** (ثلاث نقاط) \> **مزامنة الدليل**.
  
3. في صفحة **إعداد Azure Active Directory**، حدد الانتقال إلى مركز التنزيل للحصول على ارتباط أداة **Azure AD الاتصال** للبدء. 
4. اتبع الخطوات في [خارطة طريق تثبيت Azure AD الاتصال Azure AD الاتصال Azure AD](/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. إنهاء إعداد المجالات

اتبع الخطوات في [إنشاء سجلات DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) Microsoft 365 عند إدارة سجلات DNS لإنهاء إعداد المجالات.

## <a name="next-step"></a>الخطوة التالية

[تعيين تراخيص إلى حسابات المستخدمين](assign-licenses-to-user-accounts.md)