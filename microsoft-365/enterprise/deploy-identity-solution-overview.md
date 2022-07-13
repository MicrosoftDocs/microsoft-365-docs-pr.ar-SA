---
title: نشر البنية الأساسية للهوية ل Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-overview
- zerotrust-solution
ms.custom:
- intro-overview
description: نشر البنية الأساسية لهويتك ل Microsoft 365.
ms.openlocfilehash: 7140fc9a34855c39487474f160856bf671666f24
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748418"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>نشر البنية الأساسية للهوية ل Microsoft 365

في Microsoft 365 للمؤسسات، تمهد البنية الأساسية للهوية المخططة والمنفذة جيدا الطريق لأمان أقوى، بما في ذلك تقييد الوصول إلى أحمال عمل الإنتاجية وبياناتها إلى المستخدمين والأجهزة المصادق عليها فقط. يعد أمان الهويات عنصرا رئيسيا لنشر ثقة معدومة، حيث تتم مصادقة جميع محاولات الوصول إلى الموارد المحلية وفي السحابة وتخويلها.

للحصول على معلومات حول ميزات الهوية لكل Microsoft 365 للمؤسسة، ودور Azure Active Directory (Azure AD)، والمكونات المحلية والمستندة إلى السحابة، وتكوينات المصادقة الأكثر شيوعا، راجع [ملصق البنية الأساسية للهوية](../downloads/m365e-identity-infra.pdf).

[![ملصق البنية الأساسية للهوية.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

راجع هذا الملصق المكون من صفحتين للزيادة السريعة في مفاهيم الهوية وتكوينات Microsoft 365 للمؤسسة.

يمكنك [تنزيل هذا الملصق](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) وطباعته بتنسيق حرفي أو قانوني أو جدولة (11 × 17).

هذا الحل هو الخطوة الأولى لإنشاء مكدس نشر Microsoft 365 ثقة معدومة.

![مكدس نشر Microsoft 365 ثقة معدومة](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

لمزيد من المعلومات، راجع [خطة نشر Microsoft 365 ثقة معدومة](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>ما هو موجود في هذا الحل

يرشدك هذا الحل من خلال نشر بنية أساسية للهوية لمستأجر Microsoft 365 لتوفير الوصول لموظفيك والحماية من الهجمات المستندة إلى الهوية.

![نشر البنية الأساسية للهوية ل Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

الخطوات الواردة في هذا الحل هي:

1. [تحديد نموذج هويتك.](deploy-identity-solution-identity-model.md)
2. [حماية حسابات Microsoft 365 المميزة.](protect-your-global-administrator-accounts.md)
3. [حماية حسابات مستخدمي Microsoft 365.](microsoft-365-secure-sign-in.md)
4. [نشر نموذج هويتك.](cloud-only-identities.md)

يدعم هذا الحل المبادئ الرئيسية [ثقة معدومة](https://www.microsoft.com/security/business/zero-trust/):

- **تحقق بشكل صريح:** المصادقة والتخويل دائما استنادا إلى جميع نقاط البيانات المتوفرة.
- **استخدام الوصول الأقل امتيازا:** الحد من وصول المستخدم باستخدام Just-In-Time و Just-Enough-Access (JIT/JEA)، والسياسات التكيفية المستندة إلى المخاطر، وحماية البيانات.
- **افترض خرقا:** تقليل نصف قطر التفجير والوصول إلى المقطع. تحقق من التشفير الشامل واستخدم التحليلات للحصول على الرؤية، ودفع الكشف عن التهديدات، وتحسين الدفاعات.

على عكس الوصول التقليدي إلى إنترانت، والذي يثق في كل شيء خلف جدار حماية المؤسسة، ثقة معدومة تعامل كل تسجيل دخول والوصول كما لو كانت تنشأ من شبكة غير خاضعة للرقابة، سواء كانت خلف جدار حماية المؤسسة أو على الإنترنت. يتطلب ثقة معدومة حماية الشبكة والبنية الأساسية والهويات ونقاط النهاية والتطبيقات والبيانات.

## <a name="microsoft-365-capabilities-and-features"></a>إمكانات Microsoft 365 وميزاته

يوفر Azure AD مجموعة كاملة من قدرات إدارة الهوية والأمان لمستأجر Microsoft 365.

|القدرة أو الميزة|الوصف|الترخيص|
|---|---|---|
|[المصادقة متعددة العوامل (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|تتطلب المصادقة متعددة العوامل من المستخدمين توفير نموذجين للتحقق، مثل كلمة مرور المستخدم بالإضافة إلى إعلام من تطبيق Microsoft Authenticator أو مكالمة هاتفية. تقلل المصادقة متعددة العوامل إلى حد كبير من مخاطر إمكانية استخدام بيانات الاعتماد المسروقة للوصول إلى بيئتك. يستخدم Microsoft 365 Azure AD خدمة المصادقة متعددة العوامل لتسجيل الدخول المستند إلى المصادقة متعددة العوامل.|Microsoft 365 E3 أو E5|
|[الوصول المشروط](/azure/active-directory/conditional-access/overview)|Azure AD تقيم شروط تسجيل دخول المستخدم وتستخدم نهج الوصول المشروط لتحديد الوصول المسموح به. على سبيل المثال، في هذه الإرشادات، نوضح لك كيفية إنشاء نهج وصول مشروط لطلب توافق الجهاز للوصول إلى البيانات الحساسة. وهذا يقلل إلى حد كبير من خطر أن يتمكن المتسلل الذي لديه جهازه الخاص وبيانات الاعتماد المسروقة من الوصول إلى بياناتك الحساسة. كما أنه يحمي البيانات الحساسة على الأجهزة، لأن الأجهزة يجب أن تفي بمتطلبات محددة من أجل الصحة والأمان.|Microsoft 365 E3 أو E5|
|[مجموعات Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups)|تعتمد نهج الوصول المشروط وإدارة الأجهزة باستخدام Intune وحتى أذونات الملفات والمواقع في مؤسستك على التعيين لحسابات المستخدمين أو مجموعات Azure AD. نوصي بإنشاء مجموعات Azure AD تتوافق مع مستويات الحماية التي تنفذها. على سبيل المثال، من المحتمل أن يكون موظفوك التنفيذيون أهدافا ذات قيمة أعلى للمتسللين. لذلك، من المنطقي إضافة حسابات المستخدمين لهؤلاء الموظفين إلى مجموعة Azure AD وتعيين هذه المجموعة إلى نهج الوصول المشروط والنهج الأخرى التي تفرض مستوى أعلى من الحماية للوصول.|Microsoft 365 E3 أو E5|
|[حماية الهوية في Azure AD](/azure/active-directory/identity-protection/overview)|يمكنك من اكتشاف الثغرات الأمنية المحتملة التي تؤثر على هويات مؤسستك وتكوين نهج المعالجة التلقائي إلى مخاطر تسجيل الدخول المنخفضة والمتوسطة وعالية ومخاطر المستخدم. تعتمد هذه الإرشادات على تقييم المخاطر هذا لتطبيق نهج الوصول المشروط للمصادقة متعددة العوامل. تتضمن هذه الإرشادات أيضا نهج الوصول المشروط الذي يتطلب من المستخدمين تغيير كلمة المرور الخاصة بهم إذا تم الكشف عن نشاط عالي المخاطر لحسابهم.|Microsoft 365 E5 أو Microsoft 365 E3 باستخدام التراخيص الإضافية E5 Security أو EMS E5 أو Azure AD Premium P2|
|[الخدمة الذاتية لإعادة تعيين كلمة المرور(SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|اسمح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم بشكل آمن ودون تدخل مكتب المساعدة، من خلال توفير التحقق من أساليب المصادقة المتعددة التي يمكن للمسؤول التحكم بها.|Microsoft 365 E3 أو E5|
|[Azure AD الحماية بكلمة مرور](/azure/active-directory/authentication/concept-password-ban-bad)|الكشف عن كلمات المرور الضعيفة المعروفة ومتغيراتها ومصطلحات ضعيفة إضافية خاصة بمؤسستك وحظرها. يتم تطبيق قوائم كلمات المرور المحظورة العمومية الافتراضية تلقائيا على جميع المستخدمين في مستأجر Azure AD. يمكنك تحديد إدخالات إضافية في قائمة كلمات مرور محظورة مخصصة. عندما يغير المستخدمون كلمات المرور الخاصة بهم أو يعيدون تعيينها، يتم التحقق من قوائم كلمات المرور المحظورة هذه لفرض استخدام كلمات مرور قوية.|Microsoft 365 E3 أو E5|
|

## <a name="next-steps"></a>الخطوات التالية

استخدم هذه الخطوات لنشر نموذج هوية وبنية أساسية للمصادقة لمستأجر Microsoft 365:

1. [تحديد نموذج هوية السحابة الخاص بك.](deploy-identity-solution-identity-model.md)
2. [حماية حسابات Microsoft 365 المميزة.](protect-your-global-administrator-accounts.md)
3. [حماية حسابات مستخدمي Microsoft 365.](microsoft-365-secure-sign-in.md)
4. نشر نموذج هوية السحابة الخاص بك: [السحابة فقط](cloud-only-identities.md) أو [المختلطة](prepare-for-directory-synchronization.md).

[![تحديد نموذج الهوية الذي يجب استخدامه لمستأجر Microsoft 365](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>موارد الهوية السحابية الإضافية ل Microsoft

### <a name="manage"></a>الإدارة

لإدارة نشر هوية سحابة Microsoft، راجع:

- [حسابات المستخدمين](manage-microsoft-365-accounts.md)
- [التراخيص](assign-licenses-to-user-accounts.md)
- [كلمات المرور](manage-microsoft-365-passwords.md)
- [المجموعات](manage-microsoft-365-groups.md)
- [حوكمة](manage-microsoft-365-identity-governance.md)
- [مزامنة الدليل](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>كيف تقوم Microsoft بالهوية ل Microsoft 365

تعرف على كيفية إدارة خبراء تكنولوجيا المعلومات في Microsoft [للهويات وتأمين الوصول](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>يتوفر مورد عرض تكنولوجيا المعلومات هذا باللغة الإنجليزية فقط.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>كيف قامت شركة Contoso بالهوية ل Microsoft 365

للحصول على مثال على كيفية نشر مؤسسة خيالية ولكنها ممثلة متعددة الجنسيات بنية أساسية لهوية مختلطة لخدمات سحابة Microsoft 365، راجع [Identity ل Contoso Corporation](contoso-identity.md).

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
