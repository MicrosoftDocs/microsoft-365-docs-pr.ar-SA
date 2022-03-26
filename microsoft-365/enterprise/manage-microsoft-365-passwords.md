---
title: إدارة Microsoft 365 مرور حساب المستخدم
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية إدارة كلمات مرور Microsoft 365 المستخدم.
ms.openlocfilehash: 6a0d4298f3d6c46ab067795bccf01123605ce1aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572949"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>إدارة Microsoft 365 مرور حساب المستخدم

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك إدارة كلمات Microsoft 365 حساب المستخدم بعدة طرق مختلفة، استنادا إلى تكوين هويتك. يمكنك إدارة حسابات المستخدمين في مركز مسؤولي Microsoft 365 [](/admin)أو في خدمات مجال Active Directory (AD DS) أو في مركز إدارة Azure Active Directory (Azure AD).

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>التخطيط للكيفية التي ستدير بها كلمات مرور حساب المستخدم وكيفية إدارتها

يعتمد مكان إدارة حسابات المستخدمين وكيفية إدارتها على نموذج الهوية الذي تريد استخدامه Microsoft 365. النموذجان مختلطان وسحابي فقط.
  
### <a name="cloud-only"></a>السحابة فقط

يمكنك إدارة كلمات مرور حساب المستخدم في:

- [مركز مسؤولي Microsoft 365](/admin)
- مركز إدارة Azure AD
    
### <a name="hybrid"></a>مختلط

باستخدام الهوية المختلطة، يتم تخزين كلمات المرور في AD DS لذا يجب استخدام أدوات AD DS المحلية لإدارة كلمات مرور حساب المستخدم. حتى عند استخدام مزامنة كلمة المرور المالتجزئة (PHS)، حيث يخزن Azure AD إصدارا مالتجزئة من الإصدار المالتجزئة بالفعل في AD DS، يجب عليك أنت والمستخدمين إدارة كلمات المرور الخاصة بهم في AD DS.

باستخدام [كتابة كلمة المرور،](#pw_writeback) يمكن للمستخدمين تغيير كلمات مرور AD DS الخاصة بهم من خلال Azure AD.

## <a name="prevent-bad-passwords"></a>منع كلمات المرور غير الصحيحة

يجب أن يستخدم جميع المستخدمين إرشادات [كلمة مرور Microsoft](https://www.microsoft.com/research/publication/password-guidance) لإنشاء كلمات مرور حساب المستخدم الخاصة بهم.

لمنع المستخدمين من إنشاء كلمة مرور يمكن تحديدها بسهولة، استخدم حماية كلمة مرور Azure AD، التي تستخدم كل من قائمة كلمات مرور محظورة شاملة وقائمة كلمات مرور مخصصة اختيارية محظورة تحددها. على سبيل المثال، يمكنك تحديد مصطلحات خاصة لمنظمتك، مثل:

- أسماء العلامات التجارية
- أسماء المنتجات
- المواقع (على سبيل المثال، المقر الرئيسي للشركة)
- الشروط الداخلية الخاصة بالشركة
- الاختصارات التي لها معنى خاص بالشركة

يمكنك حظر كلمات المرور غير الصحيحة [في السحابة](/azure/active-directory/authentication/concept-password-ban-bad) ول [AD DS في الموقع.](/azure/active-directory/authentication/concept-password-ban-bad-on-premises)

## <a name="simplify-user-sign-in"></a>تبسيط تسجيل الدخول إلى المستخدم

يعمل Azure AD Seamless Single Sign-On (Azure AD Seamless SSO) مع PHS ومصادقة Pass-Through (PTA)، للسماح للمستخدمين تسجيل الدخول إلى الخدمات التي تستخدم حسابات مستخدم Azure AD دون الحاجة إلى كتابة كلمات المرور الخاصة بهم، وفي العديد من الحالات، أسماء المستخدمين الخاصة بهم. يمنح ذلك المستخدمين إمكانية وصول أسهل إلى التطبيقات المستندة إلى السحابة، مثل Office 365، دون الحاجة إلى أي مكونات إضافية في الموقع المحلي مثل خوادم اتحاد الهويات.

يمكنك تكوين Azure AD SSO السلس باستخدام أداة Azure AD الاتصال. راجع الإرشادات [لتكوين Azure AD Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>تبسيط تحديثات كلمات المرور ل AD DS

باستخدام إعادة كتابة كلمة المرور، يمكنك السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم من خلال Azure AD، الذي يتم نسخه بعد ذلك نسخا متماثلا إلى AD DS. لا يحتاج المستخدمون إلى الوصول إلى AD DS في الموقع لتحديث كلمات المرور الخاصة بهم. هذا الأمر ذو قيمة بالنسبة إلى التجوال أو المستخدمين البعيدين الذين ليس لديهم اتصال بالوصول عن بعد بالشبكة المحلية.

إن كتابة كلمة المرور مطلوبة لاستخدام إمكانات حماية هوية Azure AD بشكل كامل، مثل مطالبة المستخدمين بتغيير كلمات المرور المحلية عند الكشف عن وجود خطر كبير من اختراق الحساب.

للحصول على مزيد من المعلومات وإرشادات التكوين، راجع [Azure AD SSPR مع إعادة كتابة كلمة المرور](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>قم بالترقية إلى الإصدار الأخير من Azure AD الاتصال لضمان الحصول على أفضل تجربة ممكنة وميزات جديدة بمجرد إصدارها. لمزيد من المعلومات، راجع [التثبيت المخصص ل Azure AD الاتصال](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>تبسيط عمليات إعادة تعيين كلمة المرور

تسمح إعادة تعيين كلمة المرور للخدمة الذاتية (SSPR) للمستخدمين بإعادة تعيين كلمات المرور أو الحسابات أو إلغاء تأمينها. لتنبيهك إلى إساءة الاستخدام أو إساءة الاستخدام، يمكنك استخدام التقارير المفصلة التي تتعقب عند وصول المستخدمين إلى النظام، إلى جانب الإعلامات. يجب تمكين إعادة [كتابة كلمة المرور](#pw_writeback) قبل أن تتمكن من نشر إعادة تعيين كلمة المرور.

راجع الإرشادات [اللازمة ل طرح إعادة تعيين كلمة المرور](/azure/active-directory/authentication/howto-sspr-deployment).