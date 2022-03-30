---
title: 'الخطوة 3: حماية حسابات Microsoft 365 المستخدمين'
f1.keywords:
- NOCSH
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
ms.date: 09/30/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365initiative-coredeploy
ms.custom: ''
description: يتطلب من المستخدمين تسجيل الدخول بأمان باستخدام المصادقة متعددة العوامل (MFA) والميزات الأخرى.
ms.openlocfilehash: c144b374ecc49128e11635c034f3b4b76020eafd
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63577002"
---
# <a name="step-3-protect-your-microsoft-365-user-accounts"></a>الخطوة 3: حماية حسابات Microsoft 365 المستخدمين

لزيادة أمان تسجيل الدخول من قبل المستخدم:

- استخدام Windows Hello for Business
- استخدام الحماية بكلمة مرور Azure Active Directory (Azure AD)
- استخدام المصادقة متعددة العوامل (MFA)
- نشر تكوينات الوصول إلى الهوية والجهاز
- الحماية من اختراق بيانات الاعتماد باستخدام حماية هوية Azure AD

## <a name="windows-hello-for-business"></a>Windows Hello for Business

Windows Hello for Business في Windows 10 Enterprise كلمات المرور بمصادقة قوية ذات عاملين عند تسجيل الدخول على Windows جديد. العاملان هو نوع جديد من بيانات اعتماد المستخدم المرتبطة بجهاز وبقياس حيوي أو رقم PIN.

لمزيد من المعلومات، [راجع Windows Hello نظرة عامة حول الأعمال](/windows/security/identity-protection/hello-for-business/hello-overview).


## <a name="azure-ad-password-protection"></a>حماية كلمة مرور Azure AD

يكشف Azure AD Password Protection عن كلمات المرور الضعيفة المعروفة ومتغيراتها ويحظرها، كما يمكن أن يمنع مصطلحات ضعيفة إضافية خاصة بمنظمتك. يتم تطبيق قوائم كلمات المرور المحظورة بشكل افتراضي تلقائيا على جميع المستخدمين في مستأجر Azure AD. يمكنك تعريف إدخالات إضافية في قائمة كلمات مرور محظورة مخصصة. عندما يقوم المستخدمون بتغيير كلمات المرور أو إعادة تعيينها، يتم التحقق من قوائم كلمات المرور المحظورة هذه لفرض استخدام كلمات مرور قوية.

لمزيد من المعلومات، راجع [تكوين حماية كلمة مرور Azure AD](/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>MFA

تتطلب MFA أن تخضع تسجيلات الدخول من قبل المستخدم لعملية تحقق إضافية تتجاوز كلمة مرور حساب المستخدم. حتى لو حدد مستخدم ضار كلمة مرور حساب مستخدم، يجب أن يكون قادرا أيضا على الاستجابة لعملية تحقق إضافية، مثل رسالة نصية مرسلة إلى هاتف ذكي قبل منح حق الوصول.

![ينتج عن كلمة المرور الصحيحة بالإضافة إلى التحقق الإضافي تسجيل الدخول بنجاح.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

الخطوة الأولى في استخدام MFA هي طلبها لكل [حسابات المسؤولين](protect-your-global-administrator-accounts.md)، المعروفة أيضا باسم الحسابات المتميزة. بعد هذه الخطوة الأولى، توصي Microsoft ب MFA لجميع المستخدمين.

هناك ثلاث طرق لمطلب المستخدمين استخدام MFA استنادا إلى Microsoft 365 الخاص بك.

| الخطة | توصية |
|---------|---------|
|كل Microsoft 365 (بدون تراخيص Azure AD Premium P1 أو P2)     |[تمكين إعدادات الأمان الافتراضية في Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). تتضمن إعدادات الأمان الافتراضية في Azure AD MFA للمستخدمين والمسؤولين.   |
|Microsoft 365 E3 (بما في ذلك تراخيص Azure AD Premium P1)     | استخدم سياسات [الوصول الشرطي](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) الشائعة لتكوين السياسات التالية: <br>- [طلب MFA للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [طلب MFA لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [حظر المصادقة القديمة](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (بما في ذلك تراخيص Azure AD Premium P2)     | الاستفادة من Azure AD Identity Protection، ابدأ في تنفيذ مجموعة Microsoft الموصى بها من الوصول الشرطي والسياسات ذات الصلة من خلال إنشاء هاتين النهجين:<br> - [يتطلب MFA عندما تكون مخاطر تسجيل الدخول متوسطة أو عالية](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) <br>- [يجب على المستخدمين المعرضين لمخاطر عالية تغيير كلمة المرور](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)       |
| | |

### <a name="security-defaults"></a>إعدادات الأمان الافتراضية

إن إعدادات الأمان الافتراضية هي ميزة جديدة Microsoft 365 اشتراكات Office 365 المدفوعة أو التجريبية التي تم إنشاؤها بعد 21 أكتوبر 2019. تم تشغيل إعدادات الأمان الافتراضية لهذه الاشتراكات، مما يتطلب من جميع المستخدمين استخدام ***MFA*** مع Microsoft Authenticator التطبيق.
 
يكون لدى المستخدمين 14 يوما للتسجيل للحصول على MFA باستخدام تطبيق Microsoft Authenticator من هواتفهم الذكية، التي تبدأ من المرة الأولى التي يسجلون فيها الدخول بعد تمكين إعدادات الأمان الافتراضية. بعد مرور 14 يوما، لن يتمكن المستخدم من تسجيل الدخول حتى يتم إكمال تسجيل MFA.

تضمن إعدادات الأمان الافتراضية أن جميع المؤسسات لديها مستوى أساسي من الأمان عند تسجيل الدخول من قبل المستخدم يتم تمكينه بشكل افتراضي. يمكنك تعطيل إعدادات الأمان الافتراضية لصالح MFA باستخدام سياسات الوصول الشرطي أو للحسابات الفردية.

لمزيد من المعلومات، راجع [نظرة عامة حول إعدادات الأمان الافتراضية](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>نهج الوصول المشروط

إن سياسات الوصول الشرطي هي مجموعة من القواعد التي تحدد الشروط التي يتم فيها تقييم تسجيل الدخول ومنح حق الوصول. على سبيل المثال، يمكنك إنشاء نهج الوصول الشرطي الذي يعني:

- إذا كان اسم حساب المستخدم عضوا في مجموعة للمستخدمين الذين تم تعيين أدوارهم إلى Exchange أو المستخدم أو كلمة المرور أو الأمان أو SharePoint أو **Exchange** أو **مسؤول SharePoint** أو المسؤول العام، فاطلب منك الحصول على MFA قبل السماح بالوصول.

يتيح لك هذا النهج طلب MFA استنادا إلى عضوية المجموعة، بدلا من محاولة تكوين حسابات مستخدمين فردية ل MFA عند تعيينها أو عدم تعيينها من أدوار المسؤولين هذه.

يمكنك أيضا استخدام سياسات الوصول الشرطي للإمكانات الأكثر تقدما، مثل المطالبة بأن يتم تسجيل الدخول من جهاز متوافق، مثل الكمبيوتر المحمول الذي يعمل Windows 10.

يتطلب الوصول الشرطي تراخيص Azure AD Premium P1، والتي يتم تضمينها مع Microsoft 365 E3 و E5.

لمزيد من المعلومات، راجع [نظرة عامة حول الوصول الشرطي](/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>استخدام هذه الأساليب معا

ضع ما يلي في الاعتبار:

- لا يمكنك تمكين إعدادات الأمان الافتراضية إذا تم تمكين أي من سياسات الوصول الشرطي.
- لا يمكنك تمكين أي من سياسات الوصول الشرطي إذا تم تمكين إعدادات الأمان الافتراضية.

إذا تم تمكين إعدادات الأمان الافتراضية، فيطلب من جميع المستخدمين الجدد تسجيل MFA واستخدام Microsoft Authenticator الجديد. 

يعرض هذا الجدول نتائج تمكين MFA باستخدام إعدادات الأمان الافتراضية ونهج الوصول الشرطي.

| الأسلوب | تم التمكين | معطل | أسلوب مصادقة إضافي |
|:-------|:-----|:-------|:-------|
| **إعدادات الأمان الافتراضية**  | لا يمكن استخدام سياسات الوصول الشرطي | استخدام سياسات الوصول الشرطي | Microsoft Authenticator التطبيق |
| **نهج الوصول المشروط** | إذا تم تمكين أي من هذه الإعدادات، لا يمكنك تمكين إعدادات الأمان الافتراضية | إذا تم تعطيل الكل، يمكنك تمكين إعدادات الأمان الافتراضية  | يحدد المستخدم أثناء تسجيل MFA  |
||||

## <a name="zero-trust-identity-and-device-access-configurations"></a>تكوينات الوصول إلى الأجهزة وهوية الثقة الصفرية

يوصى باستخدام إعدادات ونهج الوصول إلى الأجهزة وهوية الثقة الصفرية وميزات المتطلبات الأساسية وإعداداتها جنبا إلى جنب مع سياسات الوصول الشرطي و Intune و Azure AD Identity Protection التي تحدد ما إذا كان يجب منح طلب وصول معين وفي أي شروط. يستند هذا التحديد إلى حساب المستخدم الخاص تسجيل الدخول والجهاز المستخدم والتطبيق الذي يستخدمه المستخدم للوصول والموقع الذي يتم منه طلب الوصول وتقييم مخاطر الطلب. تساعد هذه الإمكانية على ضمان وصول المستخدمين والأجهزة المعتمدة فقط إلى مواردك الهامة.

>[!Note]
>يتطلب Azure AD Identity Protection تراخيص Azure AD Premium P2، المضمنة مع Microsoft 365 E5.
>

يتم تعريف سياسات الوصول إلى الأجهزة والهوية لتستخدم في ثلاث مستويات: 

- حماية الأساس هي الحد الأدنى من مستوى الأمان للهويات والأجهزة التي تقوم بالوصول إلى تطبيقاتك وبياناتك.
- توفر الحماية الحساسة أمان إضافي لبيانات معينة. تخضع الهويات والأجهزة لمستويات أعلى من متطلبات الأمان وصحة الجهاز.
- تكون الحماية للبيئات التي تحتوي على بيانات منظمة أو مصنفة بشكل كبير خاصة بمبالغ صغيرة من البيانات المصنفة بدرجة عالية أو التي تحتوي على أسرار تجارية أو تخضع لأنظمة البيانات. تخضع الهويات والأجهزة لمستويات أعلى بكثير من متطلبات الأمان و حماية الجهاز. 

توفر هذه المستويات وتكويناتها المقابلة مستويات متناسقة من الحماية عبر البيانات والهويات والأجهزة.

توصي Microsoft بشدة بتكوين ونهج الوصول إلى الأجهزة وهوية الصفر في مؤسستك، بما في ذلك إعدادات معينة Microsoft Teams Exchange Online والوصول SharePoint. لمزيد من المعلومات، راجع [تكوينات الوصول إلى الجهاز وهوية الثقة الصفرية](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="azure-ad-identity-protection"></a>حماية هوية Azure AD

في هذا القسم، ستتعرف على كيفية تكوين سياسات تحمي من اختراق بيانات الاعتماد، حيث يحدد مهاجم اسم حساب المستخدم وكلمة المرور للوصول إلى الخدمات والبيانات السحابية الخاصة ب المؤسسة. يوفر Azure AD Identity Protection عددا من الطرق للمساعدة في منع مهاجم من التأثير على بيانات اعتماد حساب المستخدم.

باستخدام Azure AD Identity Protection، يمكنك:

|الإمكانية|الوصف|
|:---------|:---------|
| تحديد نقاط الضعف المحتملة في هويات مؤسستك ومعالجة هذه الثغرات | يستخدم Azure AD التعلم الآلي للكشف عن حالات الشذوذ والأنشطة المريبة، مثل تسجيل الدخول وأنشطة ما بعد تسجيل الدخول. باستخدام هذه البيانات، تقوم Azure AD Identity Protection بإنشاء تقارير وتنبيهات تساعدك على تقييم المشاكل واتخاذ الإجراءات اللازمة.|
|الكشف عن الإجراءات المريبة المرتبطة بهويات مؤسستك والاستجابة لها تلقائيا|يمكنك تكوين سياسات تستند إلى المخاطر تستجيب تلقائيا للقضايا التي تم الكشف عنها عند الوصول إلى مستوى مخاطر معين. يمكن لهذه السياسات، بالإضافة إلى عناصر التحكم بالوصول الشرطي الأخرى التي يوفرها Azure AD و Microsoft Intune، إما أن تمنع الوصول تلقائيا أو تتخذ إجراءات تصحيحية، بما في ذلك إعادة تعيين كلمة المرور والمطالبة بمصادقة Azure AD متعددة العوامل من أجل تسجيل الدخول لاحقا. |
| التحقيق في الأحداث المريبة وحلها باستخدام الإجراءات الإدارية | يمكنك التحقق من أحداث المخاطر باستخدام معلومات حول حادث الأمان. تتوفر مهام سير العمل الأساسية لتعقب عمليات البحث وبدء إجراءات المعالجة، مثل إعادة تعيين كلمة المرور. |
|||

راجع [المزيد من المعلومات حول حماية هوية Azure AD](/azure/active-directory/identity-protection/overview-identity-protection).

راجع الخطوات [اللازمة لتمكين Azure AD Identity Protection](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies).

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>موارد المسؤول التقنية ل MFA و تسجيل الدخول الآمن

- [MFA Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [نشر الهوية Microsoft 365](deploy-identity-solution-overview.md)
- [مقاطع فيديو تدريبية حول Azure Academy Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [تكوين نهج تسجيل المصادقة متعددة العوامل في Azure AD](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [تكوينات الوصول إلى الأجهزة والهوية](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="next-step"></a>الخطوة التالية

![نشر نموذج الهوية](../media/deploy-identity-solution-overview/deploy-identity-solution-identity-infrastructure.png)

تابع مع الخطوة 4 لنشر البنية الأساسية للهوية استنادا إلى نموذج الهوية الذي اخترته:

- [هوية السحابة فقط](cloud-only-identities.md)
- [الهوية المختلطة](prepare-for-directory-synchronization.md)
