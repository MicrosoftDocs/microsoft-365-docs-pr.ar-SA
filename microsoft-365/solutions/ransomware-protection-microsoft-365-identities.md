---
title: الخطوة 3. حماية الهويات
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، هامور، هجوم مهين، هجوم برامج الفدية الضارة، التشفير، علم الفيروسات المشفرة، الثقة الصفرية
description: استخدم تسجيل الدخول الآمن والوصول المشروط لحماية مواردك Microsoft 365 من هجمات برامج الفدية الضارة.
ms.openlocfilehash: 548e0649d7180ef39f693049210a91c1e0dce312
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575080"
---
# <a name="step-3-protect-identities"></a>الخطوة 3. حماية الهويات

استخدم المقاطع التالية لحماية مؤسستك من اختراق بيانات الاعتماد، التي تكون عادة المرحلة الأولى من هجوم برامج الفدية الضارة الأكبر.

## <a name="increase-sign-in-security"></a>زيادة أمان تسجيل الدخول

استخدم [المصادقة بدون كلمة](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) مرور لحسابات المستخدمين في Azure Active Directory (Azure AD).

أثناء الانتقال إلى المصادقة بدون كلمة مرور، استخدم أفضل الممارسات هذه لحسابات المستخدمين التي لا تزال تستخدم مصادقة كلمة المرور:

- حظر كلمات المرور المخصصة والضعيفة المعروفة باستخدام [Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad).
- توسيع حظر كلمات المرور المخصصة والضعيفة المعروفة إلى خدمات مجال [Active Directory المحلية (AD DS) باستخدام Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).
- اسمح للمستخدمين بتغيير كلمات المرور الخاصة بهم باستخدام إعادة تعيين كلمة مرور الخدمة [الذاتية (SSPR).](/azure/active-directory/authentication/concept-sspr-howitworks)

بعد ذلك، نفذ [سياسات الوصول إلى الأجهزة والهوية الشائعة](/microsoft-365/security/office-365-security/identity-access-policies). توفر هذه السياسات مستوى أعلى من الأمان للوصول إلى Microsoft 365 السحابية. 

بالنسبة إلى تسجيل الدخول إلى المستخدم، تتضمن هذه السياسات ما يلي:

- يتطلب المصادقة متعددة العوامل (MFA) [لحسابات الأولوية](/microsoft-365/admin/setup/priority-accounts) (على الفور) وفي النهاية جميع حسابات المستخدمين.
- يتطلب تسجيل الدخول عالي الخطورة لاستخدام MFA.
- يتطلب من المستخدمين ذوي المخاطر العالية تسجيل الدخول لتغيير كلمات المرور الخاصة بهم.

## <a name="prevent-privilege-escalation"></a>منع تصاعد الامتيازات

استخدم أفضل الممارسات هذه:

- تنفيذ مبدأ أقل امتياز [](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) واستخدام الحماية بكلمة مرور كما هو موضح في زيادة أمان [](#increase-sign-in-security) تسجيل الدخول لحسابات المستخدمين التي لا تزال تستخدم كلمات المرور في تسجيل الدخول. 
- تجنب استخدام حسابات الخدمة على مستوى المجال على مستوى المسؤول. 
- تقييد الامتيازات الإدارية المحلية للحد من تثبيت "طروادة الوصول البعيد" والتطبيقات الأخرى غير المرغوب فيها.
- استخدم Azure AD Conditional Access للتحقق من صحة ثقة المستخدمين ومحطات العمل بشكل صريح قبل السماح بالوصول إلى المداخل الإدارية. راجع [هذا المثال](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management) لمدخل Azure.
- تمكين إدارة كلمة مرور المسؤول المحلي.
- تحديد مكان تسجيل الدخول إلى الحسابات ذات الامتيازات العالية وكشف بيانات الاعتماد. يجب ألا تكون الحسابات ذات الامتيازات العالية موجودة على محطات العمل.
- تعطيل التخزين المحلي لكلمات المرور وبيانات الاعتماد.

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

يجب أن تجعل المستخدمين في مؤسستك على علم ب:

- المتطلبات الجديدة لكلمات مرور أقوى.
- التغييرات في عمليات تسجيل الدخول، مثل الاستخدام المطلوب ل MFA وتسجيل أسلوب المصادقة الثانوية ل MFA.
- استخدام صيانة كلمة المرور مع SSPR. على سبيل المثال، لا مزيد من المكالمات إلى helpdesk لإعادة تعيين كلمة المرور.
- المطالبة ب طلب MFA أو تغيير كلمة مرور تسجيل الدخول التي يتم تحديدها على أنها مخاطرة.

## <a name="resulting-configuration"></a>التكوين الناتج

إليك حماية برامج الفدية الضارة للمستأجر للحصول على الخطوات من 1 إلى 3.

![الحماية من برامج الفدية الضارة Microsoft 365 المستأجر بعد الخطوة 3](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step3.png)

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 4 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step4.png)](ransomware-protection-microsoft-365-devices.md)

تابع مع [الخطوة 4](ransomware-protection-microsoft-365-devices.md) لحماية الأجهزة (نقاط النهاية) في Microsoft 365 المستأجر. 
