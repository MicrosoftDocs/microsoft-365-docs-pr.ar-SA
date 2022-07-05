---
title: أهم 12 مهمة لفرق الأمان لدعم العمل من المنزل
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
description: قم بحماية البريد الإلكتروني وبيانات عملك من التهديدات الإلكترونية، بما في ذلك برامج الفدية الضارة والتصيد الاحتيالي والمرفقات الضارة.
ms.openlocfilehash: bc1dd84e83e5c5f1828e65203585d38acc28de5e
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617249"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>أهم 12 مهمة لفرق الأمان لدعم العمل من المنزل

إذا كنت مثل [Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) وفجأة وجدت نفسك تدعم القوى العاملة القائمة على المنزل في المقام الأول، نريد مساعدتك على ضمان أن مؤسستك تعمل بأمان قدر الإمكان. تعطي هذه المقالة الأولوية للمهام لمساعدة فرق الأمان على تنفيذ أهم قدرات الأمان في أسرع وقت ممكن.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="أهم المهام التي يجب تنفيذها لدعم العمل من المنزل" lightbox="../media/security/security-support-remote-work.png":::


إذا كنت مؤسسة صغيرة أو متوسطة الحجم تستخدم إحدى خطط أعمال Microsoft، فراجع هذه الموارد بدلا من ذلك:

- [أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 for Campaigns](../business-premium/index.md) (يتضمن تكوين أمان موصى به ل Microsoft 365 Business)

بالنسبة للعملاء الذين يستخدمون خطط المؤسسة، توصي Microsoft بإكمال المهام المدرجة في الجدول التالي التي تنطبق على خطة الخدمة. إذا كنت تقوم بدمج الاشتراكات بدلا من شراء خطة مؤسسة Microsoft 365، فلاحظ ما يلي:

- يتضمن Microsoft 365 E3 Enterprise Mobility + Security (EMS) E3 و Azure AD P1
- يتضمن Microsoft 365 E5 EMS E5 و Azure AD P2

****

|خطوه|المهمه|كافة خطط Office 365 Enterprise|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[تمكين المصادقة متعددة العوامل (MFA) Azure AD](#1-enable-azure-ad-multi-factor-authentication-mfa)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[الحماية من التهديدات](#2-protect-against-threats)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[تكوين Microsoft Defender لـ Office 365](#3-configure-microsoft-defender-for-office-365)|||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[تكوين Microsoft Defender for Identity](#4-configure-microsoft-defender-for-identity)|||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[تمكين Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[تكوين حماية تطبيق Intune للأجهزة المحمولة للهواتف وأجهزة الكمبيوتر اللوحية](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[تكوين المصادقة متعددة العوامل والوصول المشروط للضيوف، بما في ذلك حماية تطبيق Intune](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[تسجيل أجهزة الكمبيوتر في إدارة الأجهزة وتتطلب أجهزة كمبيوتر متوافقة](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[تحسين شبكتك للاتصال السحابي](#9-optimize-your-network-for-cloud-connectivity)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[تدريب المستخدمين](#10-train-users)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[بدء العمل باستخدام Microsoft Defender للتطبيقات السحابية](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[مراقبة التهديدات واتخاذ إجراء](#12-monitor-for-threats-and-take-action)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![تضمين.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

قبل البدء، تحقق من [درجة أمان Microsoft 365](./defender/microsoft-secure-score.md) في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>. من لوحة معلومات مركزية، يمكنك مراقبة وتحسين الأمان لهويات Microsoft 365 والبيانات والتطبيقات والأجهزة والبنية الأساسية. يتم منحك نقاط لتكوين ميزات الأمان الموصى بها، أو تنفيذ المهام المتعلقة بالأمان (مثل عرض التقارير)، أو معالجة التوصيات باستخدام تطبيق أو برنامج تابع لجهة خارجية. سترفع المهام الموصى بها في هذه المقالة درجاتك.

:::image type="content" source="../media/secure-score.png" alt-text="شاشة Microsoft Secure Score في مدخل Microsoft 365 Defender" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: تمكين المصادقة متعددة العوامل Azure AD (MFA)

أفضل شيء واحد يمكنك القيام به لتحسين الأمان للموظفين الذين يعملون من المنزل هو تشغيل المصادقة متعددة العوامل. إذا لم يكن لديك عمليات موجودة بالفعل، فتعامل مع هذا الأمر على أنه إصدار تجريبي للطوارئ وتأكد من أن لديك أشخاص دعم جاهزين لمساعدة الموظفين الذين يعانون من مشكلة. نظرا لأنك ربما لا تستطيع توزيع أجهزة أمان الأجهزة، استخدم Windows Hello المقاييس الحيوية وتطبيقات مصادقة الهاتف الذكي مثل Microsoft Authenticator.

عادة، توصي Microsoft بمنح المستخدمين 14 يوما لتسجيل أجهزتهم للمصادقة متعددة العوامل قبل طلب المصادقة متعددة العوامل. ومع ذلك، إذا كانت القوى العاملة الخاصة بك تعمل فجأة من المنزل، فتقدم واطلب المصادقة متعددة العوامل كأولوية أمنية وتكون مستعدا لمساعدة المستخدمين الذين يحتاجون إليها.

سيستغرق تطبيق هذه النهج بضع دقائق فقط، ولكن كن مستعدا لدعم المستخدمين خلال الأيام القليلة القادمة.

****

|الخطة|توصية|
|---|---|
|خطط Microsoft 365 (بدون Azure AD P1 أو P2)|[تمكين إعدادات الأمان الافتراضية في Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). تتضمن إعدادات الأمان الافتراضية في Azure AD المصادقة متعددة العوامل للمستخدمين والمسؤولين.|
|Microsoft 365 E3 (مع Azure AD P1)|استخدم [نهج الوصول المشروط الشائعة](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) لتكوين النهج التالية: <br/>- [طلب المصادقة متعددة العوامل للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [طلب المصادقة متعددة العوامل لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [حظر المصادقة القديمة](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (مع Azure AD P2)|الاستفادة من Azure AD Identity Protection، ابدأ في تنفيذ [مجموعة Microsoft الموصى بها من الوصول المشروط والسياسات ذات الصلة](./office-365-security/identity-access-policies.md) من خلال إنشاء هذه النهج:<br/> - [طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول متوسطا أو مرتفعا](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [حظر العملاء الذين لا يدعمون المصادقة الحديثة](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [يجب على المستخدمين المعرضين لمخاطر عالية تغيير كلمة المرور](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2: الحماية من التهديدات

تتضمن جميع خطط Microsoft 365 مجموعة متنوعة من ميزات الحماية من التهديدات. يستغرق رفع الحماية لهذه الميزات بضع دقائق فقط.

- الحماية من البرامج الضارة
- الحماية من عناوين URL والملفات الضارة
- الحماية من التصيد الاحتيالي
- الحماية من البريد العشوائي

راجع [الحماية من التهديدات في Office 365](office-365-security/protect-against-threats.md) للحصول على إرشادات يمكنك استخدامها كنقطة بداية.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: تكوين Microsoft Defender لـ Office 365

Microsoft Defender لـ Office 365، المضمنة في Microsoft 365 E5 Office 365 E5، تحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والارتباطات (URLs) وأدوات التعاون. قد يستغرق تكوين هذا عدة ساعات.

Microsoft Defender لـ Office 365:

- يحمي مؤسستك من تهديدات البريد الإلكتروني غير المعروفة في الوقت الحقيقي باستخدام الأنظمة الذكية التي تفحص المرفقات والارتباطات للحصول على محتوى ضار. تتضمن هذه الأنظمة التلقائية نظاما أساسيا قويا لتهيئة البيانات، ونماذج الاستعناف، والتعلم الآلي.
- حماية مؤسستك عند تعاون المستخدمين ومشاركة الملفات، من خلال تحديد الملفات الضارة وحظرها في مواقع الفريق ومكتبات المستندات.
- تطبيق نماذج التعلم الآلي والخوارزميات المتقدمة للكشف عن الانتحال لتجنب هجمات التصيد الاحتيالي.

للحصول على نظرة عامة، بما في ذلك ملخص للخطط، راجع [Defender لـ Office 365](./office-365-security/defender-for-office-365.md).

يمكن للمسؤول العام تكوين هذه الحماية:

- [إعداد نهج الارتباطات الآمنة](office-365-security/set-up-safe-links-policies.md)
- [تكوين الإعدادات العمومية للارتباطات الآمنة](office-365-security/configure-global-settings-for-safe-links.md)
- [إعداد نهج المرفقات الآمنة](office-365-security/set-up-safe-attachments-policies.md)

ستحتاج إلى العمل مع مسؤول Exchange Online ومسؤول SharePoint Online لتكوين Defender لـ Office 365 لأحمال العمل هذه:

- [Microsoft Defender لنقطة النهاية ل SharePoint وOneDrive وMicrosoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: تكوين Microsoft Defender for Identity

[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) هو حل أمان مستند إلى السحابة يستفيد من إشاراتك Active Directory محلي لتحديد التهديدات المتقدمة والهويات المخترقة والإجراءات الداخلية الضارة الموجهة إلى مؤسستك واكتشافها والتحقيق فيها. ركز على هذا بعد ذلك لأنه يحمي بنيتك الأساسية السحابية والبنية الأساسية السحابية الخاصة بك، ولا يحتوي على تبعيات أو متطلبات أساسية، ويمكن أن يوفر فائدة فورية.

- راجع [Microsoft Defender for Identity التشغيل السريع](/azure-advanced-threat-protection/install-atp-step1) للحصول على الإعداد بسرعة
- شاهد [الفيديو: مقدمة حول Microsoft Defender for Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- مراجعة [المراحل الثلاث لتوزيع Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5: تشغيل Microsoft 365 Defender

الآن بعد أن قمت Microsoft Defender لـ Office 365 وتكوينها Microsoft Defender for Identity، يمكنك عرض الإشارات المدمجة من هذه القدرات في لوحة معلومات واحدة. [يجمع Microsoft 365 Defender](./defender/microsoft-365-defender.md) بين التنبيهات والحوادث والتحقيق التلقائي والاستجابة والتتبع المتقدم عبر أحمال العمل (Microsoft Defender for Identity Defender لـ Office 365 وMicrosoft Defender لنقطة النهاية و Microsoft Defender for Cloud Apps) في جزء واحد في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>.

:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="لوحة معلومات Microsoft 365 Defender" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::

بعد تكوين واحدة أو أكثر من خدمات Defender لـ Office 365، قم بتشغيل MTP. تتم إضافة ميزات جديدة باستمرار إلى MTP؛ ضع في اعتبارك الاشتراك في تلقي ميزات المعاينة.

- [تعرف على المزيد حول MTP](./defender/microsoft-365-defender.md)
- [تشغيل MTP](./defender/m365d-enable.md)
- [الاشتراك في ميزات المعاينة](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: تكوين حماية تطبيق Intune للأجهزة المحمولة للهواتف وأجهزة الكمبيوتر اللوحية

تسمح لك Microsoft Intune Mobile Application Management (MAM) بإدارة بيانات مؤسستك وحمايتها على الهواتف وأجهزة الكمبيوتر اللوحية دون إدارة هذه الأجهزة. إليك كيفية عملها:

- يمكنك إنشاء نهج حماية التطبيقات (APP) الذي يحدد التطبيقات التي تتم إدارتها على الجهاز والسلوكيات المسموح بها (مثل منع نسخ البيانات من تطبيق مدار إلى تطبيق غير مدار). يمكنك إنشاء نهج واحد لكل نظام أساسي (iOS وAndroid).
- بعد إنشاء نهج حماية التطبيقات، يمكنك فرضها عن طريق إنشاء قاعدة وصول مشروط في Azure AD لطلب التطبيقات المعتمدة وحماية بيانات APP.

تتضمن نهج حماية التطبيقات العديد من الإعدادات. لحسن الحظ، لا تحتاج إلى التعرف على كل إعداد وتزن الخيارات. تسهل Microsoft تطبيق تكوين الإعدادات من خلال التوصية بنقاط البدء. يتضمن [إطار عمل حماية البيانات الذي يستخدم نهج حماية التطبيقات](/mem/intune/apps/app-protection-framework) ثلاثة مستويات يمكنك الاختيار من بينها.

والأفضل من ذلك، أن Microsoft تنسق إطار حماية التطبيق هذا مع مجموعة من الوصول المشروط والنهج ذات الصلة التي نوصي باستخدامها من قبل جميع المؤسسات كنقطة بداية. إذا قمت بتطبيق المصادقة متعددة العوامل باستخدام الإرشادات الواردة في هذه المقالة، فأنت في منتصف الطريق!

لتكوين حماية تطبيق الأجهزة المحمولة، استخدم الإرشادات الواردة في [نهج الوصول إلى الأجهزة والهوية الشائعة](./office-365-security/identity-access-policies.md):

 1. استخدم إرشادات [نهج تطبيق حماية البيانات](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) لإنشاء نهج لنظامي التشغيل iOS وAndroid. يوصى بالمستوى 2 (حماية البيانات المحسنة) لحماية الأساس.
 2. إنشاء قاعدة وصول مشروط لطلب [التطبيقات المعتمدة وحماية التطبيقات](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: تكوين المصادقة متعددة العوامل والوصول المشروط للضيوف، بما في ذلك حماية تطبيق Intune للأجهزة المحمولة

بعد ذلك، لنتأكد من أنه يمكنك الاستمرار في التعاون والعمل مع الضيوف. إذا كنت تستخدم خطة Microsoft 365 E3 وقمت بتطبيق المصادقة متعددة العوامل لجميع المستخدمين، فأنت معين.

إذا كنت تستخدم خطة Microsoft 365 E5 وكنت تستفيد من Azure Identity Protection للمصادقة متعددة العوامل المستندة إلى المخاطر، فستحتاج إلى إجراء بعض التعديلات (لأن حماية الهوية Azure AD لا تمتد إلى الضيوف):

- إنشاء قاعدة وصول مشروط جديدة لطلب المصادقة متعددة العوامل دائما للضيوف والمستخدمين الخارجيين.
- تحديث قاعدة الوصول المشروط إلى المصادقة متعددة العوامل المستندة إلى المخاطر لاستبعاد الضيوف والمستخدمين الخارجيين.

استخدم الإرشادات في [تحديث النهج الشائعة للسماح بوصول الضيف والخارجي وحمايتها](./office-365-security/identity-access-policies-guest-access.md) لفهم كيفية عمل وصول الضيف مع Azure AD وتحديث النهج المتأثرة.

تنطبق نهج حماية تطبيقات Intune للأجهزة المحمولة التي قمت بإنشائها، إلى جانب قاعدة الوصول المشروط لطلب التطبيقات المعتمدة وحماية التطبيقات، على حسابات الضيوف وستساعد في حماية بيانات مؤسستك.

> [!NOTE]
> إذا قمت بالفعل بتسجيل أجهزة الكمبيوتر في إدارة الأجهزة لطلب أجهزة كمبيوتر متوافقة، فستحتاج أيضا إلى استبعاد حسابات الضيوف من قاعدة الوصول المشروط التي تفرض توافق الجهاز.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: تسجيل أجهزة الكمبيوتر في إدارة الأجهزة وتتطلب أجهزة كمبيوتر متوافقة

هناك عدة طرق لتسجيل أجهزة القوى العاملة الخاصة بك. تعتمد كل طريقة على ملكية الجهاز (الشخصية أو الشركة) ونوع الجهاز (iOS وWindows وAndroid) ومتطلبات الإدارة (إعادة التعيين والترابط والتأمين). قد يستغرق هذا بعض الوقت للفرز. راجع: [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).

أسرع طريقة للمتابعة هي [إعداد التسجيل التلقائي للأجهزة Windows 10](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

يمكنك أيضا الاستفادة من هذه البرامج التعليمية:

- [استخدام Autopilot لتسجيل أجهزة Windows في Intune](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [استخدام ميزات تسجيل أجهزة شركة Apple في Apple Business Manager (ABM) لتسجيل أجهزة iOS/iPadOS في Intune](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

بعد تسجيل الأجهزة، استخدم الإرشادات الواردة في [نهج الوصول إلى الأجهزة والهوية الشائعة](./office-365-security/identity-access-policies.md) لإنشاء هذه النهج:

- [تحديد نهج توافق الجهاز](./office-365-security/identity-access-policies.md#define-device-compliance-policies) — تتضمن الإعدادات الموصى بها Windows 10 طلب الحماية من الفيروسات. إذا كان لديك Microsoft 365 E5، فاستخدم Microsoft Defender لنقطة النهاية لمراقبة حالة أجهزة الموظفين. تأكد من أن نهج التوافق لأنظمة التشغيل الأخرى تتضمن الحماية من الفيروسات وبرامج الحماية من الفيروسات في نقطة النهاية.
- [المطالبة بأجهزة كمبيوتر متوافقة](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) — هذه هي قاعدة الوصول المشروط في Azure AD التي تفرض نهج توافق الجهاز.

يمكن لمؤسسة واحدة فقط إدارة جهاز، لذا تأكد من استبعاد حسابات الضيوف من قاعدة الوصول المشروط في Azure AD. إذا لم تقم باستبعاد المستخدمين الضيوف والخارجيين من النهج التي تتطلب توافق الجهاز، فإن هذه النهج ستحظر هؤلاء المستخدمين. لمزيد من المعلومات، راجع [تحديث النهج الشائعة للسماح بوصول الضيف والخارجي وحمايتها](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: تحسين شبكتك للاتصال السحابي

إذا كنت تمكن بسرعة الجزء الأكبر من موظفيك من العمل من المنزل، فإن هذا التبديل المفاجئ لأنماط الاتصال يمكن أن يكون له تأثير كبير على البنية الأساسية لشبكة الشركة. تم توسيع العديد من الشبكات وتصميمها قبل اعتماد الخدمات السحابية. في كثير من الحالات، تكون الشبكات متسامحة مع العمال عن بعد، ولكن لم يتم تصميمها لاستخدامها عن بعد من قبل جميع المستخدمين في وقت واحد.

يتم فجأة وضع عناصر الشبكة مثل مكثفات VPN ومعدات خروج الشبكة المركزية (مثل الوكلاء وأجهزة منع فقدان البيانات) وعرض النطاق الترددي للإنترنت المركزي ودوائر Backhaul MPLS وإمكانية NAT وما إلى ذلك تحت ضغط هائل بسبب تحميل الشركة بأكملها باستخدامها. والنتيجة النهائية هي ضعف الأداء والإنتاجية إلى جانب تجربة المستخدم الضعيفة للمستخدمين الذين يتكيفون مع العمل من المنزل.

بعض الحماية التي تم توفيرها تقليديا عن طريق توجيه نسبة استخدام الشبكة مرة أخرى من خلال شبكة الشركة يتم توفيرها من خلال تطبيقات السحابة التي يصل إليها المستخدمون. إذا وصلت إلى هذه الخطوة في هذه المقالة، فقد نفذت مجموعة من عناصر التحكم المتطورة في أمان السحابة لخدمات Microsoft 365 وبياناته. مع وضع عناصر التحكم هذه في مكانها، قد تكون جاهزا لتوجيه نسبة استخدام الشبكة للمستخدمين البعيدين مباشرة إلى Office 365. إذا كنت لا تزال بحاجة إلى ارتباط VPN للوصول إلى تطبيقات أخرى، يمكنك تحسين الأداء وتجربة المستخدم بشكل كبير من خلال تنفيذ الاتصال النفقي المنقسم. بمجرد التوصل إلى اتفاق في مؤسستك، يمكن تحقيق ذلك في غضون يوم واحد من قبل فريق شبكة منسق بشكل جيد.

راجع هذه الموارد على المستندات للحصول على مزيد من المعلومات:

- [نظرة عامة: تحسين الاتصال للمستخدمين عن بعد باستخدام الاتصال النفقي المنقسم ل VPN](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [تنفيذ الاتصال النفقي المنقسم ل VPN Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

مقالات المدونة الأخيرة حول هذا الموضوع:

- [كيفية تحسين نسبة استخدام الشبكة بسرعة للموظفين عن بعد & تقليل الحمل على البنية الأساسية الخاصة بك](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [طرق بديلة لمحترفي الأمان و تكنولوجيا المعلومات لتحقيق عناصر تحكم أمنية حديثة في سيناريوهات العمل عن بعد الفريدة اليوم](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: تدريب المستخدمين

يمكن لتدريب المستخدمين حفظ المستخدمين وفريق عمليات الأمان لديك الكثير من الوقت والإحباط. من غير المرجح أن يفتح المستخدمون الادهاء المرفقات أو ينقروا فوق الارتباطات في رسائل البريد الإلكتروني المشكوك فيها، ومن المرجح أن يتجنبوا مواقع الويب المشبوهة.

يوفر [دليل حملة الأمان عبر الإنترنت](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) لمدرسة جامعة هارفرد إرشادات ممتازة حول تأسيس ثقافة قوية للوعي الأمني داخل مؤسستك، بما في ذلك تدريب المستخدمين على تحديد هجمات التصيد الاحتيالي.

يوفر Microsoft 365 الموارد التالية للمساعدة في إعلام المستخدمين في مؤسستك:

****

|مفهوم|الموارد|
|---|---|
|Microsoft 365|[مسارات التعلم القابلة للتخصيص](/office365/customlearning/) <p>يمكن أن تساعدك هذه الموارد على تجميع التدريب للمستخدمين النهائيين في مؤسستك|
|الأمان في Microsoft 365|[وحدة التعلم: تأمين مؤسستك باستخدام الأمان الذكي المضمن من Microsoft 365](/learn/modules/security-with-microsoft-365) <p>تمكنك هذه الوحدة النمطية من وصف كيفية عمل ميزات أمان Microsoft 365 معا ولشرح فوائد ميزات الأمان هذه.|
|المصادقة متعددة العوامل|[التحقق على خطوتين: ما هي صفحة التحقق الإضافية؟](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>تساعد هذه المقالة المستخدمين على فهم ماهية المصادقة متعددة العوامل وسبب استخدامها في مؤسستك.|

بالإضافة إلى هذه الإرشادات، توصي Microsoft المستخدمين باتخاذ الإجراءات الموضحة في هذه المقالة: [حماية حسابك والأجهزة من المتسللين والبرامج الضارة](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). تتضمن هذه الإجراءات ما يلي:

- استخدام كلمات مرور قوية
- حماية الأجهزة
- تمكين ميزات الأمان على أجهزة كمبيوتر Windows 10 وMac (للأجهزة غير المدارة)

توصي Microsoft أيضا المستخدمين بحماية حسابات البريد الإلكتروني الشخصية الخاصة بهم من خلال اتخاذ الإجراءات الموصى بها في المقالات التالية:

- [المساعدة في حماية حساب بريدك الإلكتروني Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [حماية حساب Gmail الخاص بك من خلال التحقق على خطوين](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: بدء استخدام Microsoft Defender for Cloud Apps

يوفر [Microsoft Defender for Cloud Apps](/cloud-app-security) رؤية غنية، والتحكم في السفر إلى البيانات، وتحليلات متطورة لتحديد التهديدات الإلكترونية ومكافحتها عبر جميع خدمات السحابة. بمجرد البدء في استخدام Defender for Cloud Apps، يتم تمكين نهج الكشف عن الحالات الشاذة تلقائيا، ولكن لدى Defender for Cloud Apps فترة تعلم أولية مدتها سبعة أيام لا يتم خلالها رفع جميع تنبيهات الكشف عن الحالات الشاذة.

ابدأ استخدام Defender for Cloud Apps الآن. يمكنك لاحقا إعداد مراقبة وعناصر تحكم أكثر تطورا.

- [التشغيل السريع: بدء استخدام Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [الحصول على تحليلات سلوكية فورية واكتشاف الشذوذ](/cloud-app-security/anomaly-detection-policy)
- [تعرف على المزيد حول Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [مراجعة الميزات والقدرات الجديدة](/cloud-app-security/release-notes)
- [الاطلاع على إرشادات الإعداد الأساسية](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: مراقبة التهديدات واتخاذ إجراء

يتضمن Microsoft 365 عدة طرق لمراقبة الحالة واتخاذ الإجراءات المناسبة. أفضل نقطة بداية هي <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، حيث يمكنك عرض [نقاط Microsoft الآمنة](./defender/microsoft-secure-score.md) لمؤسستك، وأي تنبيهات أو كيانات تتطلب انتباهك.

- [بدء استخدام مدخل Microsoft 365 Defender](./defender/microsoft-365-defender-portal.md)
- [الاطلاع على بوابات الأمان في Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>الخطوات التالية

تهانينا! لقد نفذت بسرعة بعض أهم الحماية الأمنية وأن مؤسستك أكثر أمانا. الآن أنت مستعد للمضي قدما في قدرات الحماية من التهديدات (بما في ذلك Microsoft Defender لنقطة النهاية)، وتصنيف البيانات وقدرات الحماية، وتأمين الحسابات الإدارية. للحصول على مجموعة أعمق وأسلوبية من توصيات الأمان ل Microsoft 365، راجع [Microsoft 365 Security for Business Decision Makers (BDMs).](Microsoft-365-security-for-bdm.md)

قم أيضا بزيارة Defender for Cloud الجديد من Microsoft على [docs.microsoft.com/security](/security).
