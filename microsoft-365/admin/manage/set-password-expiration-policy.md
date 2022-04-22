---
title: تعيين نهج انتهاء صلاحية كلمة المرور لمؤسستك
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: تعرف على كيفية تعيين المسؤول لنهج انتهاء صلاحية كلمة المرور للأعمال أو المؤسسة التعليمية أو المؤسسات غير الربحية في مركز مسؤولي Microsoft 365.
ms.openlocfilehash: ed94cb8bc3bdcc1c1f30c6cb9bf56907c83de41e
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022328"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>تعيين نهج انتهاء صلاحية كلمة المرور لمؤسستك

## <a name="before-you-begin"></a>قبل البدء

هذه المقالة مخصصة للأشخاص الذين يقومون بتعيين نهج انتهاء صلاحية كلمة المرور للأعمال أو المؤسسة التعليمية أو المؤسسات غير الربحية. لإكمال هذه الخطوات، تحتاج إلى تسجيل الدخول باستخدام حساب مسؤول Microsoft 365. [ما هو حساب المسؤول؟](/microsoft-365/admin/add-users/about-admin-roles).

بصفتك مسؤولا، يمكنك جعل كلمات مرور المستخدم تنتهي صلاحيتها بعد عدد معين من الأيام، أو تعيين كلمات المرور على ألا تنتهي صلاحيتها أبدا. بشكل افتراضي، يتم تعيين كلمات المرور على ألا تنتهي صلاحيتها أبدا لمؤسستك.

تشير الأبحاث الحالية بقوة إلى أن تغييرات كلمة المرور التي تم تفويضها تؤدي إلى ضرر أكبر من الجيد. إنها تدفع المستخدمين إلى اختيار كلمات المرور الضعيفة، أو إعادة استخدام كلمات المرور، أو تحديث كلمات المرور القديمة بطرق يمكن تخمينها بسهولة من قبل المتسللين. نوصي بتمكين [المصادقة متعددة العوامل](../security-and-compliance/set-up-multi-factor-authentication.md). لمعرفة المزيد حول نهج كلمة المرور، راجع [توصيات نهج كلمة المرور](../misc/password-policy-recommendations.md).

يجب أن تكون [مسؤولا عاما](../add-users/about-admin-roles.md) لتنفيذ هذه الخطوات.

إذا كنت مستخدما، فليس لديك الأذونات لتعيين كلمة المرور إلى عدم انتهاء صلاحيتها أبدا. اطلب من الدعم التقني للعمل أو المؤسسة التعليمية تنفيذ الخطوات الواردة في هذه المقالة بالنيابة عنك.

> [!TIP]
> إذا كنت بحاجة إلى مساعدة في الخطوات الواردة في هذا الموضوع، ففكر في [العمل مع أحد متخصصي الشركات الصغيرة من Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام مساعد الأعمال، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى متخصصي الشركات الصغيرة أثناء تطوير أعمالك، بدءً من الإلحاق إلى الاستخدام اليومي.

## <a name="set-password-expiration-policy"></a>تعيين نهج انتهاء صلاحية كلمة المرور

اتبع الخطوات أدناه إذا كنت تريد تعيين كلمات مرور المستخدمين لتنتهي صلاحيتها بعد فترة زمنية معينة.

1. في مركز مسؤولي Microsoft 365، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">علامة تبويب **خصوصية & الأمان**</a> ضمن **الإعدادات Org**.

    إذا لم تكن مسؤولا عموميا أو مسؤولا أمنيا، فلن ترى خيار الأمان والخصوصية.
  
1. حدد **نهج انتهاء صلاحية كلمة المرور**.
  
1. إذا كنت لا تريد أن يضطر المستخدمون إلى تغيير كلمات المرور، فقم بإلغاء تحديد المربع الموجود بجانب **تعيين كلمات مرور المستخدمين لتنتهي صلاحيتها بعد مرور عدد من الأيام**.

1. اكتب عدد مرات انتهاء صلاحية كلمات المرور. اختر عددا من الأيام من 14 إلى 730.
  
1. في المربع الثاني، اكتب عندما يتم إعلام المستخدمين بانتهاء صلاحية كلمة المرور الخاصة بهم، ثم حدد **"حفظ**". اختر عددا من الأيام من 1 إلى 30.

> [!IMPORTANT]
> لم تعد إعلامات انتهاء صلاحية كلمة المرور معتمدة في Office تطبيقات الويب أو [مركز الإدارة](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>الأمور المهمة التي تحتاج إلى معرفتها حول ميزة انتهاء صلاحية كلمة المرور
  
لن يتم إجبار الأشخاص الذين يستخدمون تطبيق Outlook فقط على إعادة تعيين كلمة مرور Microsoft 365 الخاصة بهم حتى تنتهي صلاحيتها في ذاكرة التخزين المؤقت. قد يكون هذا بعد عدة أيام من تاريخ انتهاء الصلاحية الفعلي. لا يوجد حل بديل لذلك على مستوى المسؤول.

## <a name="prevent-last-password-from-being-used-again"></a>منع استخدام كلمة المرور الأخيرة مرة أخرى

إذا كنت تريد منع المستخدمين من إعادة استخدام كلمات المرور القديمة، يمكنك القيام بذلك عن طريق فرض محفوظات كلمات المرور في Active Directory محلي (AD). راجع [إنشاء نهج كلمة مرور مخصص](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

في Azure AD، لا يمكن استخدام كلمة المرور الأخيرة مرة أخرى عندما يغير المستخدم كلمة مرور. يتم تطبيق نهج كلمة المرور على جميع حسابات المستخدمين التي يتم إنشاؤها وإدارتها مباشرة في Azure AD. لا يمكن تعديل نهج كلمة المرور هذا. راجع [نهج كلمة مرور Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>مزامنة تجزئة كلمات مرور المستخدم من Active Directory محلي إلى Azure AD (Microsoft 365)

هذه المقالة مخصصة لإعداد نهج انتهاء الصلاحية لمستخدمي السحابة فقط (Azure AD). لا ينطبق على مستخدمي الهوية المختلطة الذين يستخدمون مزامنة تجزئة كلمة المرور أو المصادقة التمريرية أو الاتحاد المحلي مثل ADFS.
  
لمعرفة كيفية مزامنة تجزئة كلمة مرور المستخدم من AD المحلي إلى Azure AD، راجع [تنفيذ مزامنة تجزئة كلمة المرور مع مزامنة azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>نهج كلمة المرور وقيود الحساب في Azure Active Directory

يمكنك تعيين المزيد من نهج كلمة المرور والقيود في دليل Azure النشط. راجع [نهج كلمة المرور وقيود الحساب في Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) للحصول على مزيد من المعلومات.

## <a name="update-password-policy"></a>تحديث نهج كلمة المرور

يقوم Set-MsolPasswordPolicy cmdlet بتحديث نهج كلمة المرور لمجال أو مستأجر محدد ويشير إلى طول الوقت الذي تظل فيه كلمة المرور صالحة قبل أن يتم تغييرها.

لمعرفة كيفية تحديث نهج كلمة المرور لمجال أو مستأجر معين، راجع [Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>المحتويات ذات الصلة

[السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم](../add-users/let-users-reset-passwords.md) (المقالة)/

[إعادة تعيين كلمات المرور](../add-users/reset-passwords.md) (مقالة)
