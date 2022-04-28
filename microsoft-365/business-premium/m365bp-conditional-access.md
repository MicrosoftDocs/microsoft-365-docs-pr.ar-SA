---
title: إعدادات الأمان الافتراضية والوصول المشروط
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية مساعدة إعدادات الأمان الافتراضية في حماية مؤسستك من الهجمات المتعلقة بالهوية من خلال توفير إعدادات أمان تم تكوينها مسبقا Microsoft 365 Business Premium.
ms.openlocfilehash: af9b19dcf33f1b79d4057662cf759ace27aec38f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095257"
---
# <a name="security-defaults-and-multi-factor-authentication"></a>إعدادات الأمان الافتراضية والمصادقة متعددة العوامل

تم تصميم Microsoft 365 Business Premium للمساعدة في حماية حسابات المستخدمين في شركتك باستخدام إعدادات الأمان المكونة مسبقا. تتضمن هذه الإعدادات تمكين المصادقة متعددة العوامل (MFA) لجميع المسؤولين وحسابات المستخدمين. بالنسبة لمعظم المؤسسات، توفر إعدادات الأمان الافتراضية مستوى جيدا من أمان تسجيل الدخول.

لمزيد من المعلومات حول إعدادات الأمان الافتراضية والنهج التي تفرضها، راجع [ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

توفر هذه المقالة معلومات حول:

- [إعدادات الأمان الافتراضية](#security-defaults) (مناسبة لمعظم الشركات)
- [الوصول المشروط](#conditional-access) (للشركات التي لها متطلبات أمنية أكثر صرامة)

> [!NOTE]
> إذا كنت تستخدم نهج الوصول المشروط، فستحتاج إلى إيقاف تشغيلها قبل استخدام إعدادات الأمان الافتراضية. يمكنك استخدام إعدادات الأمان الافتراضية أو نهج الوصول المشروط، ولكن لا يمكنك استخدام كليهما في الوقت نفسه.

## <a name="security-defaults"></a>إعدادات الأمان الافتراضية

تم تصميم إعدادات الأمان الافتراضية للمساعدة في حماية حسابات مستخدمي شركتك من البداية. عند التشغيل، توفر إعدادات الأمان الافتراضية إعدادات افتراضية آمنة تساعد على الحفاظ على أمان شركتك من خلال:

- مطالبة جميع المستخدمين والمسؤولين بالتسجيل في المصادقة متعددة العوامل باستخدام تطبيق Microsoft Authenticator.
- تحدي المستخدمين الذين لديهم المصادقة متعددة العوامل، في الغالب عندما يظهرون على جهاز أو تطبيق جديد، ولكن في كثير من الأحيان للأدوار والمهام الهامة.
- تعطيل المصادقة من عملاء المصادقة القديمة التي لا يمكنها إجراء المصادقة متعددة العوامل.
- حماية المسؤولين عن طريق طلب مصادقة إضافية في كل مرة يسجلون فيها الدخول.

المصادقة متعددة العوامل هي خطوة أولى مهمة في تأمين شركتك، وتجعل إعدادات الأمان الافتراضية تمكين المصادقة متعددة العوامل سهلة التنفيذ. إذا تم إنشاء اشتراكك في 22 أكتوبر 2019 أو بعده، فربما تم تمكين إعدادات الأمان الافتراضية تلقائيا لكي&mdash; تتمكن من التحقق من إعداداتك للتأكيد.

> [!TIP]
> لمزيد من المعلومات حول إعدادات الأمان الافتراضية والنهج التي تفرضها، راجع [ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

### <a name="to-enable-security-defaults-or-confirm-theyre-already-enabled"></a>لتمكين إعدادات الأمان الافتراضية (أو تأكيد تمكينها بالفعل)

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> باستخدام مسؤول الأمان أو مسؤول الوصول المشروط أو بيانات اعتماد المسؤول العمومي.

2. في الجزء الأيمن، حدد **Show All،** ثم ضمن **مراكز الإدارة**، حدد **Azure Active Directory**.

3. في الجزء الأيمن من **مركز إدارة Azure Active Directory،** حدد **Azure Active Directory**.

4. من القائمة اليسرى للوحة المعلومات، في قسم **"Manage** "، حدد **"Properties**".

    :::image type="content" source="../media/m365-campaigns-conditional-access/azure-ad-properties.png" alt-text="لقطة شاشة لمركز إدارة Azure Active Directory تعرض موقع عنصر قائمة الخصائص.":::

5. في أسفل صفحة **"Properties"** ، حدد **"Manage Security defaults**".

6. في الجزء الأيمن، سترى إعداد **تمكين إعدادات الأمان الافتراضية** . إذا تم تحديد **"نعم** "، يتم تمكين إعدادات الأمان الافتراضية بالفعل ولا يلزم اتخاذ أي إجراء آخر. إذا لم يتم تمكين إعدادات الأمان الافتراضية حاليا، فحدد **"نعم"** لتمكينها، ثم حدد **"حفظ**".

## <a name="conditional-access"></a>الوصول المشروط

> [!NOTE]
> إذا كنت تستخدم إعدادات الأمان الافتراضية، فستحتاج إلى إيقاف تشغيلها قبل استخدام الوصول المشروط. يمكنك استخدام إعدادات الأمان الافتراضية أو نهج الوصول المشروط، ولكن لا يمكنك استخدام كليهما في الوقت نفسه.

إذا كانت شركتك أو شركتك لديها متطلبات أمان معقدة أو كنت بحاجة إلى تحكم أكثر دقة في نهج الأمان الخاصة بك، فيجب عليك التفكير في استخدام الوصول المشروط بدلا من إعدادات الأمان الافتراضية لتحقيق وضع أمان مشابه أو أعلى.

يتيح لك الوصول المشروط إنشاء النهج التي تتفاعل مع أحداث تسجيل الدخول وتحديدها وطلب إجراءات إضافية قبل منح المستخدم حق الوصول إلى تطبيق أو خدمة. يمكن أن تكون نهج الوصول المشروط متعددة المستويات ومحددة، ما يمكن المستخدمين من أن يكونوا منتجين في أي مكان ووقت، ولكن أيضا حماية مؤسستك.

تتوفر إعدادات الأمان الافتراضية لجميع العملاء، بينما يتطلب الوصول المشروط إحدى الخطط التالية:

- Azure Active Directory Premium P1 أو P2
- Microsoft 365 Business Premium
- Microsoft 365 E3 أو E5
- Enterprise Mobility & Security E3 أو E5

إذا كنت تريد استخدام الوصول المشروط لتكوين النهج، فراجع الإرشادات المفصلة خطوة بخطوة التالية:

- [طلب المصادقة متعددة العوامل للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [طلب المصادقة متعددة العوامل لإدارة Azure](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management)
- [حظر المصادقة القديمة](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)
- [طلب المصادقة متعددة العوامل لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [يتطلب تسجيل Azure AD MFA](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy) - يتطلب Azure AD Identity Protection، الذي يعد جزءا من Azure Active Directory Premium P2

لمعرفة المزيد حول الوصول المشروط، راجع [ما هو الوصول المشروط؟](/azure/active-directory/conditional-access/overview) لمزيد من المعلومات حول إنشاء نهج الوصول المشروط، راجع [إنشاء نهج الوصول المشروط](/azure/active-directory/authentication/tutorial-enable-azure-mfa#create-a-conditional-access-policy).

> [!NOTE]
> إذا كان لديك خطة أو ترخيص يوفر الوصول المشروط ولكن لم تقم بعد بإنشاء أي نهج وصول مشروط، فأنت مدعو لاستخدام إعدادات الأمان الافتراضية. ومع ذلك، ستحتاج إلى إيقاف تشغيل إعدادات الأمان الافتراضية قبل أن تتمكن من استخدام نهج الوصول المشروط.

## <a name="next-objective"></a>الهدف التالي

إعداد طرق [للحماية من البرامج الضارة والتهديدات الأخرى](m365bp-increase-protection.md).

