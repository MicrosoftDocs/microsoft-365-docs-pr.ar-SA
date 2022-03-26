---
title: تعيين نهج انتهاء صلاحية كلمة المرور لمنظمتك
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
description: تعرف على كيف يمكن للمسؤول تعيين نهج انتهاء صلاحية كلمة مرور للأعمال أو المدرسة أو المؤسسات غير الربحية في مركز مسؤولي Microsoft 365.
ms.openlocfilehash: 9ba871a166169a0125b68808c124b10802424dfd
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63567543"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>تعيين نهج انتهاء صلاحية كلمة المرور لمنظمتك

## <a name="before-you-begin"></a>قبل البدء

هذه المقالة للأشخاص الذين يحددون نهج انتهاء صلاحية كلمة المرور للأعمال أو المدرسة أو المؤسسات غير الربحية. لإكمال هذه الخطوات، تحتاج إلى تسجيل الدخول باستخدام حساب المسؤول Microsoft 365 الخاص بك. [ما هو حساب المسؤول؟](/microsoft-365/admin/add-users/about-admin-roles).

ب أنت مسؤول، يمكنك جعل كلمات مرور المستخدم تنتهي صلاحيتها بعد عدد معين من الأيام، أو تعيين كلمات المرور حتى لا تنتهي صلاحيتها أبدا. بشكل افتراضي، يتم تعيين كلمات المرور على ألا تنتهي صلاحيتها أبدا لمنظمتك.

تشير الأبحاث الحالية بشكل قوي إلى أن التغييرات التي تم تعيينها لكلمة المرور قد أضرت أكثر من أن تكون جيدة. فهي تدفع المستخدمين إلى اختيار كلمات مرور غير محدثة أو إعادة استخدام كلمات المرور أو تحديث كلمات المرور القديمة بطرق يمكن تخمينها بسهولة من قبل المتسللين. نوصي بتمكين [المصادقة متعددة العوامل](../security-and-compliance/set-up-multi-factor-authentication.md). لمعرفة المزيد حول نهج كلمة المرور، راجع [توصيات نهج كلمة المرور](../misc/password-policy-recommendations.md).

يجب أن تكون [المسؤول العام](../add-users/about-admin-roles.md) لتنفيذ هذه الخطوات.

إذا كنت مستخدما، فلا تملك الأذونات لتعيين كلمة المرور لكي لا تنتهي صلاحيتها أبدا. اطلب من الدعم التقني للعمل أو المدرسة القيام بالخطوات في هذه المقالة.

> [!TIP]
> إذا كنت بحاجة إلى مساعدة بشأن الخطوات في هذا الموضوع، فنظر [في العمل مع أحد متخصصي Microsoft small business](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام "المساعدة في العمل"، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى المتخصصين في الشركات الصغيرة بينما تنمو أعمالك، من التكهين إلى الاستخدام اليومي.

## <a name="set-password-expiration-policy"></a>تعيين نهج انتهاء صلاحية كلمة المرور

اتبع الخطوات أدناه إذا كنت تريد تعيين كلمات مرور المستخدمين لتنتهي صلاحيتها بعد مرور فترة زمنية معينة.

1. في مركز مسؤولي Microsoft 365، انتقل إلى علامة <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**التبويب أمان & الخصوصية**</a> ضمن **علامة التبويب الإعدادات**.

    إذا لم تكن المسؤول العام، فلن ترى خيار الأمان والخصوصية.
  
1. حدد **نهج انتهاء صلاحية كلمة المرور**.
  
1. إذا كنت لا تريد أن يقوم المستخدمون بتغيير كلمات المرور، فقم ب إلغاء تحديد المربع بجانب تعيين كلمات مرور المستخدمين لتنتهي صلاحيتها بعد **عدد من الأيام**.

1. اكتب عدد مرات انتهاء صلاحية كلمات المرور. اختر عدد الأيام من 14 إلى 730.
  
1. في المربع الثاني، اكتب عندما يتم إعلام المستخدمين ب انتهاء صلاحية كلمة المرور الخاصة بهم، ثم حدد **حفظ**. اختر عدد الأيام من 1 إلى 30.

> [!IMPORTANT]
> لم تعد إعلامات انتهاء صلاحية كلمة المرور معتمدة Office تطبيقات الويب أو [مركز الإدارة](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>أشياء مهمة تحتاج إلى معرفتها حول ميزة انتهاء صلاحية كلمة المرور
  
لن يتم إجبار الأشخاص الذين يستخدمون Outlook فقط على إعادة تعيين كلمة Microsoft 365 المرور حتى تنتهي صلاحيتها في ذاكرة التخزين المؤقت. قد يكون ذلك بعد عدة أيام من تاريخ انتهاء الصلاحية الفعلي. لا يوجد حل بديل لهذا الأمر على مستوى المسؤول.

## <a name="prevent-last-password-from-being-used-again"></a>منع استخدام كلمة المرور الأخيرة مرة أخرى

إذا كنت تريد منع المستخدمين من إعادة تدوير كلمات المرور القديمة، يمكنك القيام بذلك عن طريق فرض محفوظات كلمات المرور في Active Directory المحلي (AD). راجع [إنشاء نهج كلمة مرور مخصص](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

في Azure AD، لا يمكن استخدام كلمة المرور الأخيرة مرة أخرى عندما يقوم المستخدم بتغيير كلمة مرور. يتم تطبيق نهج كلمة المرور على كل حسابات المستخدمين التي يتم إنشاؤها وإدارتها مباشرة في Azure AD. لا يمكن تعديل نهج كلمة المرور هذا. راجع [سياسات كلمة مرور Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>مزامنة كلمات مرور المستخدم من Active Directory المحلي إلى Azure AD (Microsoft 365)

هذه المقالة لإعداد نهج انتهاء الصلاحية لمستخدمي السحابة فقط (Azure AD). ولا ينطبق ذلك على مستخدمي الهوية المختلطة الذين يستخدمون مزامنة كلمة المرور أو المصادقة المرورية أو الاتحاد المحلي مثل ADFS.
  
للتعرف على كيفية مزامنة فهاشات كلمة مرور المستخدم من AD إلى Azure AD، راجع تنفيذ مزامنة كلمة المرور مع مزامنة [Azure AD الاتصال المزامنة](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>سياسات كلمات المرور وقيود الحساب في Azure Active Directory

يمكنك تعيين المزيد من سياسات كلمات المرور والقيود في Azure active directory. راجع سياسات [كلمة المرور وقيود الحساب في Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) للحصول على مزيد من المعلومات.

## <a name="update-password-policy"></a>تحديث نهج كلمة المرور

يحدث Set-MsolPasswordPolicy cmdlet نهج كلمة المرور لمجال أو مستأجر محدد ويشير إلى المدة الزمنية التي تظل فيها كلمة المرور صالحة قبل أن يتم تغييرها.

للتعرف على كيفية تحديث نهج كلمة المرور لمجال أو مستأجر معين، راجع [Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>المحتوى ذي الصلة

[السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم](../add-users/let-users-reset-passwords.md) (مقالة)/

[إعادة تعيين كلمات المرور](../add-users/reset-passwords.md) (مقالة)
