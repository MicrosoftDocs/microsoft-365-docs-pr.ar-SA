---
title: الخطوة 1. زيادة أمان تسجيل الدخول للعاملين المختلطين باستخدام MFA
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: يتطلب من العاملين المختلطين تسجيل الدخول باستخدام المصادقة متعددة العوامل (MFA).
ms.openlocfilehash: 3bccf8b3ab6bc57417c6b9beafa35c8c7230f20f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569294"
---
# <a name="step-1-increase-sign-in-security-for-hybrid-workers-with-mfa"></a>الخطوة 1. زيادة أمان تسجيل الدخول للعاملين المختلطين باستخدام MFA

لزيادة أمان تسجيل الدخول للعاملين المختلطين، استخدم المصادقة متعددة العوامل (MFA). تتطلب MFA أن تخضع تسجيلات الدخول من قبل المستخدم لعملية تحقق إضافية تتجاوز كلمة مرور حساب المستخدم. حتى لو حدد مستخدم ضار كلمة مرور حساب مستخدم، يجب أن يكون قادرا أيضا على الاستجابة لعملية تحقق إضافية، مثل رسالة نصية مرسلة إلى هاتف ذكي قبل منح حق الوصول.

![ينتج عن كلمة المرور الصحيحة بالإضافة إلى التحقق الإضافي تسجيل الدخول بنجاح.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

بالنسبة لجميع المستخدمين، بما في ذلك العاملين المختلطين وخاصة المسؤولين، توصي Microsoft بشدة ب MFA.

هناك ثلاث طرق لمطلب المستخدمين استخدام MFA استنادا إلى Microsoft 365 الخاص بك.

|الخطة  |توصية  |
|---------|---------|
|كل Microsoft 365 (بدون تراخيص Azure AD Premium P1 أو P2)     |[تمكين إعدادات الأمان الافتراضية في Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). تتضمن إعدادات الأمان الافتراضية في Azure AD MFA للمستخدمين والمسؤولين.   |
|Microsoft 365 E3 (بما في ذلك تراخيص Azure AD Premium P1)     | استخدم [سياسات الوصول الشرطي](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) الشائعة لتكوين السياسات التالية: <br>- [طلب MFA للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [طلب MFA لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [حظر المصادقة القديمة](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (بما في ذلك تراخيص Azure AD Premium P2)     | الاستفادة من Azure AD Identity Protection، ابدأ في تنفيذ مجموعة Microsoft الموصى بها من الوصول الشرطي والسياسات ذات [الصلة من خلال](../security/office-365-security/identity-access-policies.md) إنشاء هذه السياسات:<br> - [يتطلب MFA عندما تكون مخاطر تسجيل الدخول متوسطة أو عالية](../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br>- [حظر العملاء الذين لا يدعمون المصادقة الحديثة](../security/office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br>- [يجب على المستخدمين المعرضين لمخاطر عالية تغيير كلمة المرور](../security/office-365-security/identity-access-policies.md#high-risk-users-must-change-password)       |
| | |

## <a name="security-defaults"></a>إعدادات الأمان الافتراضية

إن إعدادات الأمان الافتراضية هي ميزة جديدة Microsoft 365 اشتراكات Office 365 المدفوعة أو التجريبية التي تم إنشاؤها بعد 21 أكتوبر 2019. تم تشغيل إعدادات الأمان الافتراضية لهذه الاشتراكات، مما يتطلب من جميع المستخدمين استخدام ***MFA*** مع Microsoft Authenticator التطبيق.
 
يكون لدى المستخدمين 14 يوما للتسجيل للحصول على MFA باستخدام تطبيق Microsoft Authenticator من هواتفهم الذكية، التي تبدأ من المرة الأولى التي يسجلون فيها الدخول بعد تمكين إعدادات الأمان الافتراضية. بعد مرور 14 يوما، لن يتمكن المستخدم من تسجيل الدخول حتى يتم إكمال تسجيل MFA.

تضمن إعدادات الأمان الافتراضية أن جميع المؤسسات لديها مستوى أساسي من الأمان عند تسجيل الدخول من قبل المستخدم يتم تمكينه بشكل افتراضي. يمكنك تعطيل إعدادات الأمان الافتراضية لصالح MFA باستخدام سياسات الوصول الشرطي أو للحسابات الفردية.

لمزيد من المعلومات، راجع نظرة [عامة حول إعدادات الأمان الافتراضية](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

## <a name="conditional-access-policies"></a>نهج الوصول المشروط

إن سياسات الوصول الشرطي هي مجموعة من القواعد التي تحدد الشروط التي يتم بها تقييم تسجيلات الدخول والسماح بها. على سبيل المثال، يمكنك إنشاء نهج الوصول الشرطي الذي يعني:

- إذا كان اسم حساب المستخدم عضوا في مجموعة للمستخدمين الذين تم تعيينهم لأدوار Exchange أو المستخدم أو كلمة المرور أو الأمان أو SharePoint أو المسؤول العام، فاطلب منك الحصول على MFA قبل السماح بالوصول.

يتيح لك هذا النهج طلب MFA استنادا إلى عضوية المجموعة، بدلا من محاولة تكوين حسابات مستخدمين فردية ل MFA عند تعيينها أو عدم تعيينها من أدوار المسؤولين هذه.

يمكنك أيضا استخدام سياسات الوصول الشرطي للإمكانات الأكثر تقدما، مثل المطالبة بأن يتم تسجيل الدخول من جهاز متوافق، مثل الكمبيوتر المحمول الذي يعمل Windows 11 أو 10.

يتطلب الوصول الشرطي تراخيص Azure AD Premium P1، والتي يتم تضمينها مع Microsoft 365 E3 و E5.

لمزيد من المعلومات، راجع نظرة [عامة حول الوصول الشرطي](/azure/active-directory/conditional-access/overview).

## <a name="azure-ad-identity-protection-support"></a>دعم حماية هوية Azure AD

باستخدام Azure AD Identity Protection، يمكنك إنشاء نهج وصول شرطي إضافي على ما يلي:

- إذا تم تحديد خطر تسجيل الدخول على أنه متوسط أو عال، فاطلب MFA.

يتطلب Azure AD Identity Protection تراخيص Azure AD Premium P2، المضمنة مع Microsoft 365 E5.

لمزيد من المعلومات، راجع [الوصول الشرطي المستند إلى المخاطر](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk#require-mfa-medium-or-high-sign-in-risk-users).

باستخدام Azure AD Identity Protection، يمكنك أيضا إنشاء نهج يطلب من المستخدمين التسجيل للحصول على MFA. لمزيد من المعلومات، راجع [تكوين نهج تسجيل مصادقة Azure AD متعددة العوامل](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)


## <a name="using-these-methods-together"></a>استخدام هذه الأساليب معا

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

## <a name="let-your-users-reset-their-own-passwords"></a>السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم

Self-Service إعادة تعيين كلمة المرور (SSPR) المستخدمين من إعادة تعيين كلمات المرور الخاصة بهم دون التأثير على موظفي المعلومات. يمكن للمستخدمين إعادة تعيين كلمات المرور الخاصة بهم بسرعة في أي وقت ومن أي مكان. لمزيد من المعلومات، راجع تخطيط نشر إعادة تعيين كلمة مرور [خدمة Azure AD الذاتية](/azure/active-directory/authentication/howto-sspr-deployment).

## <a name="sign-in-to-saas-apps-with-azure-ad"></a>تسجيل الدخول إلى تطبيقات SaaS باستخدام Azure AD

بالإضافة إلى توفير مصادقة سحابية للمستخدمين، يمكن أن يكون Azure AD أيضا طريقة مركزية لتأمين جميع تطبيقاتك، سواء كانت في موقع العمل أو في سحابة Microsoft أو في سحابة أخرى. من [خلال دمج تطبيقاتك في Azure AD](/azure/active-directory/manage-apps/plan-an-application-integration)، يمكنك أن تجعل من السهل على العاملين المختلطين اكتشاف التطبيقات التي يحتاجون إليها، كما يمكنك تسجيل الدخول إليها بأمان.

## <a name="admin-technical-resources-for-mfa-and-identity"></a>الموارد التقنية للمسؤول ل MFA والهوية

- [أفضل 5 طرق يمكن أن يساعدك بها Azure AD على تمكين العمل عن بعد](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/top-5-ways-your-azure-ad-can-help-you-enable-remote-work/ba-p/1144691)
- [البنية الأساسية للهوية Microsoft 365](../enterprise/deploy-identity-solution-overview.md)
- [مقاطع فيديو تدريبية حول Azure Academy Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)

## <a name="results-of-step-1"></a>نتائج الخطوة 1

بعد نشر MFA، يمكن للمستخدمين:

- مطلوب لاستخدام MFA في تسجيل الدخول.
- أكملت عملية تسجيل MFA وهي تستخدم MFA لجميع عمليات تسجيل الدخول.
- يمكن استخدام SSPR لإعادة تعيين كلمات المرور الخاصة بهم.

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 2: توفير الوصول عن بعد إلى التطبيقات والخدمات المحلية.](../media/empower-people-to-work-remotely/remote-workers-step-grid-2.png)](empower-people-to-work-remotely-remote-access.md)

تابع مع [الخطوة 2](empower-people-to-work-remotely-remote-access.md) لتوفير الوصول عن بعد إلى التطبيقات والخدمات المحلية.