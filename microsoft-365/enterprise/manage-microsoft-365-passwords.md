---
title: إدارة كلمات مرور حساب المستخدم Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: تعرف على كيفية إدارة كلمات مرور حساب المستخدم Microsoft 365.
ms.openlocfilehash: 689f88c2380f0655af70cea08404ed7163fa1239
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094383"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>إدارة كلمات مرور حساب المستخدم Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك إدارة كلمات مرور حساب المستخدم Microsoft 365 بعدة طرق مختلفة، اعتمادا على تكوين هويتك. يمكنك إدارة حسابات المستخدمين في [مركز مسؤولي Microsoft 365](/admin) أو في خدمات مجال Active Directory (AD DS) أو في مركز إدارة Azure Active Directory (Azure AD).

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>التخطيط لمكان وكيفية إدارة كلمات مرور حساب المستخدم

يعتمد مكان وكيفية إدارة حسابات المستخدمين على نموذج الهوية الذي تريد استخدامه Microsoft 365. النموذجان هما السحابة فقط والمختلطة.
  
### <a name="cloud-only"></a>السحابة فقط

يمكنك إدارة كلمات مرور حساب المستخدم في:

- [مركز مسؤولي Microsoft 365](/admin)
- مركز إدارة Azure AD
    
### <a name="hybrid"></a>مختلط

باستخدام الهوية المختلطة، يتم تخزين كلمات المرور في AD DS لذا يجب عليك استخدام أدوات AD DS المحلية لإدارة كلمات مرور حساب المستخدم. حتى عند استخدام مزامنة تجزئة كلمة المرور (PHS)، حيث يقوم Azure AD بتخزين إصدار متجزئة من الإصدار المتجزئة بالفعل في AD DS، يجب عليك أنت والمستخدمين إدارة كلمات المرور الخاصة بهم في AD DS.

مع [إعادة كتابة كلمة المرور](#pw_writeback)، يمكن للمستخدمين تغيير كلمات مرور AD DS الخاصة بهم من خلال Azure AD.

## <a name="prevent-bad-passwords"></a>منع كلمات المرور غير الصالحة

يجب أن يستخدم جميع المستخدمين [إرشادات كلمة المرور الخاصة ب Microsoft](https://www.microsoft.com/research/publication/password-guidance) لإنشاء كلمات مرور حساب المستخدم الخاصة بهم.

لمنع المستخدمين من إنشاء كلمة مرور سهلة التحديد، استخدم حماية كلمة مرور Azure AD، والتي تستخدم كل من قائمة كلمات المرور المحظورة العمومية وقائمة كلمات المرور المحظورة المخصصة الاختيارية التي تحددها. على سبيل المثال، يمكنك تحديد المصطلحات الخاصة بمؤسستك، مثل:

- أسماء العلامة التجارية
- أسماء المنتجات
- المواقع (على سبيل المثال، مثل المقر الرئيسي للشركة)
- الشروط الداخلية الخاصة بالشركة
- الاختصارات التي لها معنى محدد للشركة

يمكنك حظر كلمات المرور السيئة [في السحابة](/azure/active-directory/authentication/concept-password-ban-bad) ول [AD DS المحلي](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

## <a name="simplify-user-sign-in"></a>تبسيط تسجيل دخول المستخدم

يعمل Sign-On Single Sign-On Azure AD Seamless SSO مع PHS ومصادقة Pass-Through (PTA)، للسماح للمستخدمين بتسجيل الدخول إلى الخدمات التي تستخدم حسابات مستخدمي Azure AD دون الحاجة إلى كتابة كلمات المرور الخاصة بهم، وفي كثير من الحالات، أسماء المستخدمين الخاصة بهم. وهذا يمنح المستخدمين إمكانية وصول أسهل إلى التطبيقات المستندة إلى السحابة، مثل Office 365، دون الحاجة إلى أي مكونات محلية إضافية مثل خوادم اتحاد الهوية.

يمكنك تكوين تسجيل الدخول الأحادي السلس إلى Azure AD باستخدام أداة الاتصال Azure AD. راجع [الإرشادات لتكوين تسجيل الدخول الأحادي السلس إلى Azure AD](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>تبسيط تحديثات كلمة المرور إلى AD DS

مع إعادة كتابة كلمة المرور، يمكنك السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم من خلال Azure AD، والتي يتم نسخها بعد ذلك إلى AD DS. لا يحتاج المستخدمون إلى الوصول إلى AD DS المحلي لتحديث كلمات المرور الخاصة بهم. يعد هذا الأمر ذا قيمة بالنسبة إلى التجوال أو المستخدمين البعيدين الذين ليس لديهم اتصال بالوصول عن بعد إلى الشبكة المحلية.

مطلوب إعادة كتابة كلمة المرور للاستفادة الكاملة من قدرات Azure AD Identity Protection، مثل مطالبة المستخدمين بتغيير كلمات المرور المحلية الخاصة بهم عندما يكون هناك خطر كبير من الكشف عن اختراق الحساب.

لمزيد من المعلومات وإرشادات التكوين، راجع [Azure AD SSPR مع إعادة كتابة كلمة المرور](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>قم بالترقية إلى أحدث إصدار من Azure AD الاتصال لضمان أفضل تجربة ممكنة وميزات جديدة عند إصدارها. لمزيد من المعلومات، راجع [التثبيت المخصص ل Azure AD الاتصال](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>تبسيط عمليات إعادة تعيين كلمة المرور

تسمح إعادة تعيين كلمة مرور الخدمة الذاتية (SSPR) للمستخدمين بإعادة تعيين كلمات المرور أو الحسابات الخاصة بهم أو إلغاء تأمينها. لتنبيهك إلى إساءة الاستخدام أو إساءة الاستخدام، يمكنك استخدام التقارير المفصلة التي تتعقب وقت وصول المستخدمين إلى النظام، إلى جانب الإعلامات. يجب تمكين [إعادة كتابة كلمة المرور](#pw_writeback) قبل أن تتمكن من نشر عمليات إعادة تعيين كلمة المرور.

راجع [الإرشادات الخاصة بإعادة تعيين كلمة المرور](/azure/active-directory/authentication/howto-sspr-deployment).