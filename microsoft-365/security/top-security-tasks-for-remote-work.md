---
title: أهم 12 مهام لفرق الأمان لدعم العمل من المنزل
f1.keywords:
- CSH
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- remotework
ms.custom: admindeeplinkDEFENDER
description: حماية البريد الإلكتروني وبيانات العمل من التهديدات الإلكترونية، بما في ذلك برامج الفدية الضارة والتصيد الاحتيالي والمرفقات الضارة.
ms.openlocfilehash: 1277d001118dda764aa9b2a968f1024d5befcac1
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755072"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>أهم 12 مهام لفرق الأمان لدعم العمل من المنزل

إذا كنت مثل [Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) وعثرت فجأة على نفسك تدعم قوة عمل منزلية أساسية، فنحن نريد مساعدتك على ضمان عمل مؤسستك بأمان قدر الإمكان. تعطي هذه المقالة الأولوية للمهام لمساعدة فرق الأمان على تنفيذ قدرات الأمان الأكثر أهمية في أسرع وقت ممكن.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="أهم 12 مهام لفرق الأمان لدعم العمل من المنزل" lightbox="../media/security/security-support-remote-work.png":::

إذا كنت مؤسسة صغيرة أو متوسطة الحجم تستخدم إحدى خطط Microsoft للأعمال، فشاهد هذه الموارد بدلا من ذلك:

- [أفضل 10 طرق لتأمين Office 365 Microsoft 365 خطط الأعمال](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 للحملات](../business-premium/index.md) (يتضمن تكوين أمان مستحسن Microsoft 365 Business)

بالنسبة للعملاء الذين يستخدمون خطط المؤسسة، توصي Microsoft لإكمال المهام المدرجة في الجدول التالي التي تنطبق على خطة الخدمة. إذا كنت تقوم بدمج اشتراكات بدلا من Microsoft 365 خطة مؤسسة، فلاحظ ما يلي:

- Microsoft 365 E3 Enterprise Mobility + Security (EMS) E3 و Azure AD P1
- Microsoft 365 E5 EMS E5 و Azure AD P2

****

|الخطوة|مهمة|كل Office 365 Enterprise الجديدة|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[تمكين مصادقة Azure AD متعددة العوامل (MFA)](#1-enable-azure-ad-multi-factor-authentication-mfa)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[الحماية من التهديدات](#2-protect-against-threats)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[تكوين Microsoft Defender Office 365](#3-configure-microsoft-defender-for-office-365)|||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[تكوين Microsoft Defender for Identity](#4-configure-microsoft-defender-for-identity)|||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[تشغيل Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[تكوين حماية تطبيق Intune mobile للهواتف وأجهزة الكمبيوتر اللوحية](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[تكوين MFA والوصول الشرطي للضيوف، بما في ذلك حماية تطبيق Intune](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[تسجيل أجهزة الكمبيوتر في إدارة الأجهزة وتتطلب أجهزة كمبيوتر متوافقة](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[تحسين الشبكة لاتصال السحابة](#9-optimize-your-network-for-cloud-connectivity)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[تدريب المستخدمين](#10-train-users)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[بدء استخدام Microsoft Defender لتطبيقات السحابة](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[مراقبة التهديدات واتخاذ إجراء](#12-monitor-for-threats-and-take-action)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![مضمن.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

قبل البدء، تحقق من Microsoft 365 [نقاط](./defender/microsoft-secure-score.md) آمنة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a>. من لوحة معلومات مركزية، يمكنك مراقبة وتحسين أمان Microsoft 365 البيانات والتطبيقات والأجهزة والبنية الأساسية. ستمنح نقاطا لتكوين ميزات الأمان الموصى بها أو تنفيذ المهام ذات الصلة بالامن (مثل عرض التقارير) أو معالجة التوصيات باستخدام تطبيق أو برنامج من جهة خارجية. سترفع المهام الموصى بها في هذه المقالة نقاطك.

:::image type="content" source="../media/secure-score.png" alt-text="شاشة Microsoft Secure Score في مدخل Microsoft 365 Defender" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: تمكين مصادقة Azure AD متعددة العوامل (MFA)

أفضل شيء يمكنك القيام به لتحسين الأمان للموظفين الذين يعملون من المنزل هو تشغيل MFA. إذا لم تكن لديك عمليات في مكانها، فتعامل مع هذا الأمر كطيار طوارئ وتأكد من أن الأشخاص المدعمين جاهزون لمساعدة الموظفين الذين يتعثرون. بما أنه لا يمكنك على الأرجح توزيع أجهزة أمان الأجهزة، Windows Hello المقاييس الحيوية وتطبيقات مصادقة الهواتف الذكية مثل Microsoft Authenticator.

عادة، توصي Microsoft بأن تمنح المستخدمين 14 يوما لتسجيل جهازهم للمصادقة متعددة العوامل قبل طلب المصادقة متعددة العوامل. ومع ذلك، إذا كانت قوة العمل لديك تعمل فجأة من المنزل، فامضي قدما واطلب منك الحصول على MFA كالأولوية الأمنية و كن مستعدا لمساعدة المستخدمين الذين يحتاجون إليها.

سيستغرق تطبيق هذه السياسات بضع دقائق فقط، ولكن كن مستعدا لدعم المستخدمين خلال الأيام القليلة القادمة.

****

|الخطة|توصية|
|---|---|
|Microsoft 365 التخطيط (بدون Azure AD P1 أو P2)|[تمكين إعدادات الأمان الافتراضية في Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). تتضمن إعدادات الأمان الافتراضية في Azure AD MFA للمستخدمين والمسؤولين.|
|Microsoft 365 E3 (مع Azure AD P1)|استخدم [سياسات الوصول الشرطي](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) الشائعة لتكوين السياسات التالية: <br/>- [طلب MFA للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [طلب MFA لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [حظر المصادقة القديمة](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (باستخدام Azure AD P2)|الاستفادة من Azure AD Identity Protection، ابدأ في تنفيذ مجموعة Microsoft الموصى بها من الوصول الشرطي والسياسات ذات [الصلة من خلال](./office-365-security/identity-access-policies.md) إنشاء هذه السياسات:<br/> - [يتطلب MFA عندما تكون مخاطر تسجيل الدخول متوسطة أو عالية](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [حظر العملاء الذين لا يدعمون المصادقة الحديثة](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [يجب على المستخدمين المعرضين لمخاطر عالية تغيير كلمة المرور](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2: الحماية من التهديدات

تتضمن Microsoft 365 الجديدة مجموعة متنوعة من ميزات الحماية من المخاطر. يتطلب توفير حماية لهذه الميزات بضع دقائق فقط.

- الحماية من البرامج الضارة
- الحماية من عناوين URL والملفات الضارة
- الحماية من التصيد الاحتيالي
- الحماية من البريد العشوائي

راجع [الحماية من التهديدات](office-365-security/protect-against-threats.md) في Office 365 للحصول على الإرشادات التي يمكنك استخدامها كنقطة بداية.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: تكوين Microsoft Defender Office 365

يحمي Microsoft Defender Office 365، المضمن مع Microsoft 365 E5 Office 365 E5، مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. قد يستغرق هذا الأمر عدة ساعات للتكوين.

Microsoft Defender Office 365:

- يحمي مؤسستك من تهديدات البريد الإلكتروني غير المعروفة في الوقت الحقيقي باستخدام الأنظمة الذكية التي تفحص المرفقات والربط للمحتوى الضار. تتضمن هذه الأنظمة التلقائية نظام أساسي قوي للتقويم ونماذج تعليمية آلية ونماذج تعلم آلي.
- يحمي مؤسستك عند تعاون المستخدمين في العمل على الملفات ومشاركتها، من خلال تحديد الملفات الضارة وحظرها في مواقع الفريق ومكتبات المستندات.
- يطبق نماذج التعلم الآلي والخوارزميات المتقدمة للكشف عن التصيد الاحتيالي لتجنب هجمات التصيد الاحتيالي.

للحصول على نظرة عامة، بما في ذلك ملخص الخطط، راجع [Defender for Office 365](./office-365-security/defender-for-office-365.md).

يمكن للمسؤول العام تكوين هذه الحماية:

- [إعداد خزينة الارتباطات](office-365-security/set-up-safe-links-policies.md)
- [تكوين الإعدادات خزينة الارتباطات](office-365-security/configure-global-settings-for-safe-links.md)
- [إعداد خزينة المرفقات](office-365-security/set-up-safe-attachments-policies.md)

ستحتاج إلى العمل مع مسؤول Exchange Online ومسؤول SharePoint عبر الإنترنت لتكوين Defender for Office 365 أحمال العمل هذه:

- [Microsoft Defender ل Endpoint SharePoint OneDrive و Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: تكوين Microsoft Defender for Identity

[إن Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) هو حل أمان مستند إلى السحابة ويرفع من مستوى إشارات Active Directory في الموقع للتعرف على التهديدات المتقدمة والهويات المضرة والإجراءات الضارة ل insider الموجهة إلى مؤسستك والكشف عنها والتحقق منها. التركيز على هذا التالي لأنه يحمي البنية الأساسية المحلية والسحابية، وليس لديه تبعيات أو متطلبات أساسية، ويمكن أن يوفر فائدة فورية.

- راجع التشغيل السريع ل [Microsoft Defender for Identity](/azure-advanced-threat-protection/install-atp-step1) للحصول على الإعداد بسرعة
- شاهد [الفيديو: مقدمة حول Microsoft Defender for Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- مراجعة المراحل [الثلاث لنشر Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5: تشغيل Microsoft 365 Defender

الآن وقد تم تكوين Microsoft Defender Office 365 و Microsoft Defender for Identity، يمكنك عرض الإشارات المدمجة من هذه الإمكانات في لوحة معلومات واحدة. [يجمع Microsoft 365 Defender](./defender/microsoft-365-defender.md) التنبيهات والحوادث والتحري التلقائي والاستجابة والصيد المتقدم عبر أحمال العمل (Microsoft Defender for Identity و Defender for Office 365 و Microsoft Defender for Endpoint و Microsoft Defender for Cloud Apps) في جزء واحد في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a>.

<!--
:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="The MTP dashboard in the Microsoft 365 Defender portal" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::
--> 

بعد تكوين واحد أو أكثر من خدمات Defender Office 365، قم تشغيل MTP. تضاف الميزات الجديدة باستمرار إلى MTP؛ يمكنك الاشتراك لتلقي ميزات المعاينة.

- [معرفة المزيد حول MTP](./defender/microsoft-365-defender.md)
- [تشغيل MTP](./defender/m365d-enable.md)
- [الاشتراك في ميزات المعاينة](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: تكوين حماية تطبيق Intune للجوال للهواتف وأجهزة الكمبيوتر اللوحية

Microsoft Intune Mobile Application Management (MAM) إدارة بيانات مؤسستك وحمايتها على الهواتف وأجهزة الكمبيوتر اللوحية دون إدارة هذه الأجهزة. إليك كيفية عمل ذلك:

- يمكنك إنشاء نهج حماية التطبيق (APP) الذي يحدد التطبيقات التي يتم إدارتها على الجهاز والسلوكيات المسموح بها (مثل منع نسخ البيانات من تطبيق مدار إلى تطبيق غير مدار). يمكنك إنشاء نهج واحد لكل نظام أساسي (iOS وAndroid).
- بعد إنشاء سياسات حماية التطبيق، عليك فرض هذه من خلال إنشاء قاعدة وصول شرطي في Azure AD لتطلب تطبيقات معتمدة وحماية بيانات APP.

تتضمن سياسات حماية التطبيق العديد من الإعدادات. لحسن الحظ، لست بحاجة إلى التعرف على كل إعداد وتحديد الخيارات. تجعل Microsoft من السهل تطبيق تكوين الإعدادات من خلال التوصية بنقاط البدء. يتضمن [إطار عمل حماية البيانات الذي يستخدم سياسات حماية](/mem/intune/apps/app-protection-framework) التطبيق ثلاثة مستويات يمكنك الاختيار من بينها.

والأفضل من ذلك، تقوم Microsoft بتنسيق إطار حماية التطبيق هذا باستخدام مجموعة من الوصول الشرطي والسياسات ذات الصلة، نوصي باستخدام كل المؤسسات كنقطة بداية. إذا قمت بتنفيذ MFA باستخدام الإرشادات في هذه المقالة، فهذا يعني أنك في منتصف الطريق!

لتكوين حماية تطبيق الأجهزة المحمولة، استخدم الإرشادات في سياسات الوصول إلى الأجهزة والهوية [الشائعة](./office-365-security/identity-access-policies.md):

 1. استخدم إرشادات [تطبيق سياسات حماية بيانات التطبيق](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) لإنشاء سياسات لنظامي التشغيل iOS وAndroid. يوصى بالمستوى 2 (حماية البيانات المحسنة) لحماية الأساس.
 2. قم بإنشاء قاعدة وصول شرطي إلى [يتطلب التطبيقات المعتمدة وحماية التطبيق](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: تكوين MFA والوصول الشرطي للضيوف، بما في ذلك حماية تطبيق Intune mobile

بعد ذلك، دعنا نضمن لك الاستمرار في التعاون والعمل مع الضيوف. إذا كنت تستخدم خطة Microsoft 365 E3 ثم قمت بتنفيذ MFA لجميع المستخدمين، يتم تعيينك.

إذا كنت تستخدم خطة Microsoft 365 E5 وتستفيد من Azure Identity Protection ل MFA المستندة إلى المخاطر، يجب إجراء بعض التعديلات (لأن حماية هوية Azure AD لا تمتد إلى الضيوف):

- قم بإنشاء قاعدة وصول شرطي جديدة لتطلب MFA دائما للضيوف والمستخدمين الخارجيين.
- قم بتحديث قاعدة الوصول الشرطي ل MFA المستندة إلى المخاطر لاستبعاد الضيوف والمستخدمين الخارجيين.

استخدم [الإرشادات في تحديث](./office-365-security/identity-access-policies-guest-access.md) النهج الشائعة للسماح بالوصول الخارجي والضيف وحمايته لفهم كيفية عمل وصول الضيف مع Azure AD وتحديث النهج المتأثرة.

تنطبق سياسات حماية تطبيق Intune mobile التي أنشأتها، إلى جانب قاعدة الوصول الشرطي التي تتطلب التطبيقات المعتمدة وحماية التطبيق، على حسابات الضيوف وستساعد على حماية بيانات مؤسستك.

> [!NOTE]
> إذا قمت بالفعل بتسجيل أجهزة الكمبيوتر الشخصية في إدارة الأجهزة لكي تحتاج إلى أجهزة كمبيوتر متوافقة، ستحتاج أيضا إلى استبعاد حسابات الضيوف من قاعدة الوصول الشرطي التي تفرض توافق الجهاز.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: تسجيل أجهزة الكمبيوتر في إدارة الأجهزة وتتطلب أجهزة كمبيوتر متوافقة

هناك العديد من الطرق لتسجيل أجهزة القوة العاملة لديك. تعتمد كل طريقة على ملكية الجهاز (الشخصية أو الشركة) ونوع الجهاز (iOS و Windows وAndroid) ومتطلبات الإدارة (إعادة التعيين والتقارب والقفل). قد يستغرق هذا الأمر بعض الوقت للفرز. راجع: [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).

أسرع طريقة للانتهاء هي إعداد التسجيل [التلقائي Windows 10 الأجهزة](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

يمكنك أيضا الاستفادة من هذه البرامج التعليمية:

- [استخدام Autopilot لتسجيل Windows في Intune](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [استخدام ميزات تسجيل الأجهزة الخاصة بالشركة من Apple في Apple Business Manager (ABM) لتسجيل أجهزة iOS/iPadOS في Intune](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

بعد تسجيل الأجهزة، استخدم الإرشادات في [سياسات الوصول](./office-365-security/identity-access-policies.md) إلى الأجهزة والهوية الشائعة لإنشاء هذه النهج:

- [تعريف سياسات توافق الجهاز](./office-365-security/identity-access-policies.md#define-device-compliance-policies) — تتضمن الإعدادات المستحسنة Windows 10 الحماية من الفيروسات. إذا كان لديك Microsoft 365 E5، فاستخدم Microsoft Defender لنقطة النهاية لمراقبة حالة أجهزة الموظفين. تأكد من أن سياسات التوافق الخاصة بأنظمت التشغيل الأخرى تتضمن برامج الحماية من الفيروسات ونقطة النهاية.
- [تتطلب أجهزة كمبيوتر متوافقة](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) — هذه هي قاعدة الوصول الشرطي في Azure AD التي تفرض سياسات توافق الجهاز.

يمكن لمنظمه واحدة فقط إدارة جهاز، لذا تأكد من استبعاد حسابات الضيوف من قاعدة الوصول الشرطي في Azure AD. إذا لم تستثني المستخدمين الخارجيين والضيوف من النهج التي تتطلب توافق الأجهزة، فإن هذه النهج ستحظر هؤلاء المستخدمين. لمزيد من المعلومات، راجع تحديث السياسات الشائعة للسماح [بالوصول الخارجي والضيف وحمايته](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: تحسين الشبكة لاتصال السحابة

إذا كنت تعمل بسرعة على تمكين معظم الموظفين للعمل من المنزل، يمكن أن يكون لهذا التبديل المفاجئ لأنماط الاتصال تأثير كبير على البنية الأساسية لشبكة الشركة. تم تحجيم العديد من الشبكات وتصميمها قبل اعتماد الخدمات السحابية. في العديد من الحالات، تكون الشبكات غير مصممة للعاملين عن بعد، ولكن لم يتم تصميمها بحيث يتم استخدامها عن بعد من قبل جميع المستخدمين في الوقت نفسه.

يتم بشكل مفاجئ وضع عناصر الشبكة مثل مركزات VPN وأجهزة الخروج المركزية للشبكة (مثل الأجهزة التي تعمل على منع فقدان البيانات والتكامل الترددي المركزي للإنترنت ودوائر MPLS المرتد والقدرة على NAT وما إلى ذلك) تحت ضغط هائل بسبب حمل الأعمال بكاملها باستخدامها. والنتيجة النهائية هي ضعف الأداء والإنتاجية إلى جانب تجربة مستخدم ضعيفة للمستخدمين الذين يتكيفون مع العمل من المنزل.

يتم توفير بعض الحماية التي تم توفيرها بشكل تقليدي عن طريق توجيه حركة المرور مرة أخرى عبر شبكة شركة من خلال تطبيقات السحابة التي يمكن للمستخدمين الوصول إليها. إذا وصلت إلى هذه الخطوة في هذه المقالة، فهذا يعني أنك قمت بتنفيذ مجموعة من عناصر التحكم المتطورة في أمان السحابة لخدمات Microsoft 365 البيانات. باستخدام عناصر التحكم هذه في مكانها، قد تكون جاهزا توجيه حركة مرور المستخدمين البعيدين مباشرة إلى Office 365. إذا كنت لا تزال بحاجة إلى ارتباط VPN للوصول إلى تطبيقات أخرى، يمكنك تحسين أداءك وتجربة المستخدم بشكل كبير من خلال تنفيذ تقسيم التقسيمات. بعد أن تتوصل إلى اتفاقية في مؤسستك، يمكن تحقيق ذلك في غضون يوم واحد من قبل فريق شبكة منسق بشكل جيد.

راجع هذه الموارد على المستندات للحصول على مزيد من المعلومات:

- [نظرة عامة: تحسين الاتصال للمستخدمين البعيدين باستخدام تقسيم VPN](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [تنفيذ تقسيم VPN ل Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

مقالات المدونة الأخيرة حول هذا الموضوع:

- [كيفية تحسين حركة المرور بسرعة للموظفين البعيدين & التحميل على البنية الأساسية](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [طرق بديلة لمحترفي الأمان تكنولوجيا المعلومات لتحقيق عناصر التحكم الحديثة في الأمان في سيناريوهات العمل عن بعد الفريدة اليوم](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: تدريب المستخدمين

يمكن للمستخدمين التدريب على حفظ المستخدمين وفريق عمليات الأمان كثيرا من الوقت والإحباط. إن احتمال فتح المرفقات أو النقر فوق الارتباطات في رسائل البريد الإلكتروني مشكوك فيها أقل من قبل المستخدمين الملهمين، ومن المرجح أن يتجنبوا مواقع الويب المريبة.

يوفر "كتيب حملة [](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) الأمن الإلكتروني لمدرسة هارفارد جامعتين" إرشادات ممتازة حول تأسيس ثقافة قوية للوعي الأمني داخل مؤسستك، بما في ذلك تدريب المستخدمين على التعرف على هجمات التصيد الاحتيالي.

Microsoft 365 الموارد التالية للمساعدة على إعلام المستخدمين في مؤسستك:

****

|المفهوم|الموارد|
|---|---|
|Microsoft 365|[مسارات التعلم القابلة للتخصيص](/office365/customlearning/) <p>يمكن أن تساعدك هذه الموارد على جمع التدريب للمستخدمين النهائيين في مؤسستك|
|Microsoft 365 الأمان|[Learning النمطية: تأمين مؤسستك باستخدام أمان مضمن وذكي من Microsoft 365](/learn/modules/security-with-microsoft-365) <p>تمكنك هذه الوحدة النمطية من وصف كيفية Microsoft 365 ميزات الأمان معا والتعبير عن فوائد ميزات الأمان هذه.|
|المصادقة متعددة العوامل|[التحقق على خطوتين: ما هي صفحة التحقق الإضافية؟](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>تساعد هذه المقالة المستخدمين على فهم المصادقة متعددة العوامل ولماذا يتم استخدامها في مؤسستك.|

بالإضافة إلى هذا الإرشاد، توصي Microsoft بأن يتخذ المستخدمون الإجراءات الموضحة في هذه المقالة: حماية حسابك وأجهزتك من المتسللين [والبرامج](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx) الضارة. تتضمن هذه الإجراءات:

- استخدام كلمات مرور قوية
- حماية الأجهزة
- تمكين ميزات الأمان على Windows 10 الشخصية وأجهزة Mac (للأجهزة غير التي يتم إجهزتها)

توصي Microsoft أيضا بأن يقوم المستخدمون بحماية حسابات بريدهم الإلكتروني الشخصية من خلال اتخاذ الإجراءات الموصى بها في المقالات التالية:

- [المساعدة في حماية حساب بريدك الإلكتروني Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [حماية حساب Gmail باستخدام التحقق على خطوتين](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: بدء استخدام Microsoft Defender لتطبيقات السحابة

[يوفر Microsoft Defender for Cloud Apps](/cloud-app-security) رؤية غنية، والتحكم في سفر البيانات، وتحليلات معقدة لتحديد مكافحة الهجمات الإلكترونية عبر جميع خدمات السحابة. بمجرد بدء استخدام Defender for Cloud Apps، يتم تمكين سياسات الكشف عن الشذوذ تلقائيا، ولكن يكون ل Defender for Cloud Apps فترة تعلم أولية من سبعة أيام لا يتم خلالها رفع جميع تنبيهات الكشف عن الشذوذ.

بدء استخدام Defender for Cloud Apps الآن. في وقت لاحق، يمكنك إعداد عناصر تحكم ومراقبة أكثر تعقيدا.

- [تشغيل سريع: بدء استخدام Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [الحصول على التحليلات السلوكية الفورية والاكتشاف الشذوذ](/cloud-app-security/anomaly-detection-policy)
- [تعرف على المزيد حول Microsoft Defender لتطبيقات السحابة](/cloud-app-security/what-is-cloud-app-security)
- [مراجعة الميزات والإمكانات الجديدة](/cloud-app-security/release-notes)
- [الاطلاع على إرشادات الإعداد الأساسية](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: مراقبة التهديدات واتخاذ إجراء

Microsoft 365 على عدة طرق لمراقبة الحالة واتخاذ الإجراءات المناسبة. نقطة البداية الأفضل هي Microsoft 365 Defender، حيث <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"></a>يمكنك عرض "نقاط [Microsoft Secure](./defender/microsoft-secure-score.md)" الخاصة مؤسستك وأي تنبيهات أو كيانات تتطلب انتباهك.

- [بدء العمل باستخدام Microsoft 365 Defender الإلكتروني](./defender/microsoft-365-defender.md#the-microsoft-365-defender-portal)
- [راجع مداخل الأمان في Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>الخطوات التالية

تهانينا! لقد قمت بتنفيذ بعض من أهم حماية الأمان بسرعة وكانت مؤسستك أكثر أمانا. أنت الآن جاهز للمضي إلى أبعد من ذلك باستخدام قدرات الحماية من المخاطر (بما في ذلك Microsoft Defender for Endpoint)، وإمكانيات تصنيف البيانات والحماية، وتأمين الحسابات الإدارية. للحصول على مجموعة أعمق ومنهجية من توصيات الأمان Microsoft 365، راجع Microsoft 365 الأمان لصانعي قرارات الأعمال [(BDMs).](Microsoft-365-security-for-bdm.md)

يمكنك أيضا زيارة موقع Microsoft الجديد Defender for Cloud [على docs.microsoft.com/security](/security).
