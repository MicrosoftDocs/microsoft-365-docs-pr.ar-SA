---
title: نشر البنية الأساسية للهوية Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-scenario
- m365solution-overview
ms.custom:
- intro-overview
description: نشر البنية الأساسية للهوية Microsoft 365.
ms.openlocfilehash: 77dbb7c5c38e2ecd8d8ef5ae71044565c2ae6b20
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/06/2022
ms.locfileid: "63575208"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>نشر البنية الأساسية للهوية Microsoft 365

في Microsoft 365 خاصة بالمؤسسة، تم تخطيط البنية الأساسية للهوية وتنفيذها جيدا لتمهيد الطريق لمزيد من الأمان، بما في ذلك تقييد الوصول إلى أحمال العمل الإنتاجية وبياناتها فقط للمستخدمين والأجهزة المصادق عليها. الأمان للهويات هو عنصر أساسي في نشر "الثقة الصفرية"، حيث يتم مصادقة كل محاولات الوصول إلى الموارد سواء المحلية أو في السحابة والمصادقة عليها.

للحصول على معلومات حول ميزات الهوية لكل Microsoft 365 للمؤسسة ودور Azure Active Directory (Azure AD) والمكونات المحلية والمستندة إلى السحابة وتكوينات المصادقة الأكثر شيوعا، راجع ملصق البنية الأساسية للهوية[.](../downloads/m365e-identity-infra.pdf)

[![ملصق البنية الأساسية للهوية.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

راجع هذا الملصق الذي من صفحتين للزيادة سريعا في مفاهيم الهوية وتكوينات Microsoft 365 للمؤسسات.

يمكنك تنزيل [هذا الملصق](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) وطباعته بتنسيق حرف أو قانوني أو جدولي (11 × 17).

هذا الحل هو الخطوة الأولى لإنشاء مكدس نشر Microsoft 365 الثقة الصفرية.

![مكدس Microsoft 365 الثقة الصفرية](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

لمزيد من المعلومات، راجع Microsoft 365 [نشر الثقة الصفرية](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>ما هو في هذا الحل

يقدم لك هذا الحل خطوات من خلال نشر بنية أساسية للهوية لمستأجر Microsoft 365 لتوفير الوصول للموظفين والحماية من الهجمات المستندة إلى الهوية.

![نشر البنية الأساسية للهوية Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

الخطوات في هذا الحل هي:

1. [حدد نموذج هويتك.](deploy-identity-solution-identity-model.md)
2. [حماية الحسابات Microsoft 365 المميزة.](protect-your-global-administrator-accounts.md)
3. [حماية حسابات Microsoft 365 المستخدمين.](microsoft-365-secure-sign-in.md)
4. [نشر نموذج هويتك.](cloud-only-identities.md)

يدعم هذا الحل المبادئ الأساسية [للثقة الصفرية](https://www.microsoft.com/security/business/zero-trust/):

- **تحقق بشكل صريح:** المصادقة والتفويض دائما استنادا إلى كل نقاط البيانات المتوفرة.
- **استخدام أقل وصول للامتيازات:** تقييد وصول المستخدمين باستخدام Just-In-Time و Just-Enough-Access (JIT/JEA) ونهج التكييف المستندة إلى المخاطر وحماية البيانات.
- **افترض خرق:** تقليل نصف قطر الناسف والوصول إلى المقطع. تحقق من التشفير النهائي واستخدام التحليلات للحصول على الرؤية، والكشف عن تهديدات محرك الأقراص، وتحسين الدفاعات.

بخلاف الوصول التقليدي إلى الإنترانت، الذي يثق في كل شيء خلف جدار الحماية الخاص بأي مؤسسة، يعامل Zero Trust كل تسجيل دخول والوصول كما لو كان منبثقا من شبكة غير خاضعة للتحكم، سواء كان ذلك خلف جدار حماية المؤسسة أو على الإنترنت. يتطلب "الثقة الصفرية" الحماية للشبكة والبنية الأساسية والهويات ونقاط النهاية والتطبيقات والبيانات.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 وميزات

يوفر Azure AD مجموعة كاملة من قدرات إدارة الهوية والأمان لمستأجر Microsoft 365 الخاص بك.

|الإمكانية أو الميزة|الوصف|الترخيص|
|---|---|---|
|[المصادقة متعددة العوامل (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|تتطلب MFA من المستخدمين توفير شكلين من التحقق، مثل كلمة مرور المستخدم بالإضافة إلى إعلام من تطبيق Microsoft Authenticator أو مكالمة هاتفية. تقلل MFA إلى حد كبير من مخاطر استخدام بيانات الاعتماد التي تمت سرقتها للوصول إلى بيئتك. Microsoft 365 خدمة Azure AD Multi-Factor Authentication في تسجيلات الدخول المستندة إلى المصادقة متعددة العوامل.|Microsoft 365 E3 أو E5|
|[الوصول الشرطي](/azure/active-directory/conditional-access/overview)|يقيم Azure AD شروط تسجيل دخول المستخدم ويستخدم سياسات الوصول الشرطي لتحديد الوصول المسموح به. على سبيل المثال، في هذه الإرشادات، سنعرض لك كيفية إنشاء نهج وصول شرطي لتطلب توافق الجهاز للوصول إلى البيانات الحساسة. هذا يقلل إلى حد كبير من خطر وصول المتسلل باستخدام جهازه الخاص وبيانات الاعتماد التي تمت سرقتها إلى بياناتك الحساسة. كما أنه يحمي البيانات الحساسة على الأجهزة، لأنه يجب أن تلبي الأجهزة متطلبات محددة للحماية والأمان.|Microsoft 365 E3 أو E5|
|[مجموعات Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups)|تعتمد سياسات الوصول الشرطي وإدارة الأجهزة باستخدام Intune وحتى الأذونات للملفات والمواقع في مؤسستك على التعيين إلى حسابات المستخدمين أو مجموعات Azure AD. نوصي بإنشاء مجموعات Azure AD تتوافق مع مستويات الحماية التي تقوم بتنفيذها. على سبيل المثال، من المرجح أن يكون فريق العمل التنفيذي لديك أهدافا ذات قيمة أعلى للمتسللين. وبالتالي، فمن المنطقي إضافة حسابات المستخدمين لهؤلاء الموظفين إلى مجموعة Azure AD وتعيين هذه المجموعة إلى سياسات الوصول المشروط ونهج أخرى تفرض مستوى أعلى من الحماية للوصول.|Microsoft 365 E3 أو E5|
|[حماية هوية Azure AD](/azure/active-directory/identity-protection/overview)|تمكنك من الكشف عن نقاط الضعف المحتملة التي تؤثر على هويات مؤسستك وتكوين نهج المعالجة التلقائية إلى مخاطر تسجيل الدخول المنخفضة والمتوسطة والأعلى وخطر المستخدم. يعتمد هذا الإرشاد على تقييم المخاطر هذا لتطبيق نهج الوصول الشرطي للمصادقة متعددة العوامل. يتضمن هذا الإرشاد أيضا نهج الوصول المشروط الذي يتطلب من المستخدمين تغيير كلمة المرور الخاصة بهم إذا تم الكشف عن نشاط عالي المخاطر لحسابهم.|Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظائف الإضافية أمان E5 أو EMS E5 أو تراخيص Azure AD Premium P2|
|[الخدمة الذاتية لإعادة تعيين كلمة المرور(SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|اسمح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم بأمان وبدون تدخل مكتب المساعدة، من خلال توفير التحقق من أساليب المصادقة المتعددة التي يمكن للمسؤول التحكم بها.|Microsoft 365 E3 أو E5|
|[حماية كلمة مرور Azure AD](/azure/active-directory/authentication/concept-password-ban-bad)|اكتشف كلمات المرور الضعيفة المعروفة ومتغيراتها ومصطلحاتها الضعيفة الإضافية الخاصة بمنظمتك وحظرها. يتم تطبيق قوائم كلمات المرور المحظورة بشكل افتراضي تلقائيا على جميع المستخدمين في مستأجر Azure AD. يمكنك تعريف إدخالات إضافية في قائمة كلمات مرور محظورة مخصصة. عندما يقوم المستخدمون بتغيير كلمات المرور أو إعادة تعيينها، يتم التحقق من قوائم كلمات المرور المحظورة هذه لفرض استخدام كلمات مرور قوية.|Microsoft 365 E3 أو E5|
|

## <a name="next-steps"></a>الخطوات التالية

استخدم هذه الخطوات لنشر نموذج هوية والبنية الأساسية للمصادقة لمستأجر Microsoft 365 الخاص بك:

1. [حدد نموذج الهوية السحابية.](deploy-identity-solution-identity-model.md)
2. [حماية الحسابات Microsoft 365 المميزة.](protect-your-global-administrator-accounts.md)
3. [حماية حسابات Microsoft 365 المستخدمين.](microsoft-365-secure-sign-in.md)
4. نشر نموذج الهوية السحابية: [السحابة فقط أو](cloud-only-identities.md) [المختلط](prepare-for-directory-synchronization.md).

[![تحديد نموذج الهوية الذي يجب استخدامه لمستأجر Microsoft 365 الخاص بك](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>موارد هوية سحابية إضافية من Microsoft

### <a name="manage"></a>إدارة

لإدارة نشر الهوية السحابية من Microsoft، راجع:

- [حسابات المستخدمين](manage-microsoft-365-accounts.md)
- [التراخيص](assign-licenses-to-user-accounts.md)
- [كلمات المرور](manage-microsoft-365-passwords.md)
- [المجموعات](manage-microsoft-365-groups.md)
- [إدارة](manage-microsoft-365-identity-governance.md)
- [مزامنة الدليل](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>كيف تقوم Microsoft بالهوية Microsoft 365

تعرف على كيفية إدارة خبراء تقنيات المعلومات [في Microsoft للهويات والوصول الآمن](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>يتوفر مورد IT Showcase هذا باللغة الإنجليزية فقط.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>كيف قام Contoso بالهوية Microsoft 365

للحصول على مثال حول كيفية نشر مؤسسة خيالية ولكن تمثيلية متعددة الجنسيات للبنية الأساسية للهوية المختلطة لخدمات السحابة Microsoft 365، راجع الهوية الخاصة ب [Contoso Corporation](contoso-identity.md).

<!--

## Plan

To plan for your identity implementation:

- [Understand the different identity models](about-microsoft-365-identity.md)
- [Plan for hybrid identity and directory synchronization](plan-for-directory-synchronization.md)

## Deploy

To deploy your identity implementation:

- [Protect your global administrator accounts](protect-your-global-administrator-accounts.md)
- [Configure and use cloud-only identities](cloud-only-identities.md)
- [Configure and use hybrid identities](prepare-for-directory-synchronization.md)
- [Set up directory synchronization](set-up-directory-synchronization.md)
- If needed, deploy [hybrid identity scenarios](hybrid-solutions.md)

### Identity and device access recommendations

To help ensure a secure and productive workforce, Microsoft provides a set of recommendations for [identity and device access](../security/office-365-security/microsoft-365-policies-configurations.md). For identity, use the recommendations and settings in these articles:

- [Prerequisites](../security/office-365-security/identity-access-prerequisites.md)
- [Common identity and device access policies](../security/office-365-security/identity-access-policies.md)

--> 
