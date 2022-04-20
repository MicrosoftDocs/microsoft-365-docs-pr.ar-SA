---
title: نظرة عامة على Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية مساعدة Exchange Online Protection (EOP) في حماية مؤسسة البريد الإلكتروني المحلية في بيئات مستقلة ومختلطة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 19bf82a530cd61b253047261bb44893266a240d8
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941556"
---
# <a name="exchange-online-protection-overview"></a>نظرة عامة على Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) هي خدمة التصفية المستندة إلى السحابة التي تحمي مؤسستك من البريد العشوائي والبرامج الضارة وتهديدات البريد الإلكتروني الأخرى. يتم تضمين EOP في جميع المؤسسات Microsoft 365 التي تحتوي على علب بريد Exchange Online.

> [!NOTE]
> يتوفر EOP أيضا في حد ذاته لحماية علب البريد المحلية وفي البيئات المختلطة لحماية علب بريد Exchange المحلية. لمزيد من المعلومات، راجع [Exchange Online Protection المستقلة](/exchange/standalone-eop/standalone-eop).

خطوات إعداد ميزات أمان EOP ومقارنة الأمان الإضافي الذي تحصل عليه في Microsoft Defender لـ Office 365، راجع [الحماية من التهديدات](protect-against-threats.md). تتوفر الإعدادات الموصى بها لميزات EOP في [الإعدادات المستحسنة ل EOP والأمان Microsoft Defender لـ Office 365](recommended-settings-for-eop-and-office365.md).

تشرح بقية هذه المقالة كيفية عمل EOP والميزات المتوفرة في EOP.

## <a name="how-eop-works"></a>كيفية عمل EOP

لفهم كيفية عمل EOP، من المفيد معرفة كيفية معالجة البريد الإلكتروني الوارد:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="رسم البريد الإلكتروني من الإنترنت أو ملاحظات العملاء التي تمر إلى EOP ومن خلال الاتصال، ومكافحة البرامج الضارة، وتصفية نهج مائل لقواعد تدفق البريد، وتصفية المحتوى، قبل الحكم إما بالبريد غير الهام أو العزل، أو تسليم بريد المستخدم النهائي" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. عندما تدخل رسالة واردة EOP، فإنها تمر في البداية من خلال تصفية الاتصال، والتي تتحقق من سمعة المرسل. يتم إيقاف معظم البريد العشوائي في هذه المرحلة ورفضه من قبل EOP. لمزيد من المعلومات، راجع [تكوين تصفية الاتصال](configure-the-connection-filter-policy.md).

2. ثم يتم فحص الرسالة للبحث عن البرامج الضارة. إذا تم العثور على برامج ضارة في الرسالة أو المرفقات، يتم تسليم الرسالة إلى العزل. بشكل افتراضي، يمكن للمسؤولين فقط عرض الرسائل المعزولة للبرامج الضارة والتفاعل معها. ولكن، يمكن للمسؤولين إنشاء نهج [العزل](quarantine-policies.md) واستخدامها لتحديد ما يسمح للمستخدمين القيام به للرسائل المعزولة. لمعرفة المزيد حول الحماية من البرامج الضارة، راجع [الحماية من البرامج الضارة في EOP](anti-malware-protection.md).

3. تستمر الرسالة من خلال تصفية النهج، حيث يتم تقييمها مقابل أي قواعد تدفق بريد (تعرف أيضا باسم قواعد النقل) التي قمت بإنشائها. على سبيل المثال، يمكن أن ترسل القاعدة إعلاما إلى مدير عند وصول رسالة من مرسل معين.

   في المؤسسة المحلية التي لها Exchange Enterprise CAL مع تراخيص الخدمات، يحدث أيضا [التحقق من فقدان بيانات Microsoft Purview (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) في EOP في هذه المرحلة.

4. تمر الرسالة من خلال تصفية المحتوى (مكافحة البريد العشوائي والانتحال) حيث يتم تعريف الرسائل الضارة على أنها بريد عشوائي أو بريد عشوائي عالي الثقة أو تصيد احتيالي أو تصيد احتيالي عالي الثقة أو مجموعة (نهج مكافحة البريد العشوائي) أو تزييف هوية (إعدادات تزييف هوية في نهج مكافحة التصيد الاحتيالي). يمكنك تكوين الإجراء الذي يجب اتخاذه على الرسالة استنادا إلى حكم التصفية (العزل، والانتقال إلى مجلد البريد الإلكتروني غير الهام، وما إلى ذلك)، وما يمكن للمستخدمين القيام به للرسائل المعزولة باستخدام [نهج العزل](quarantine-policies.md). لمزيد من المعلومات، راجع [تكوين نهج مكافحة البريد العشوائي](configure-your-spam-filter-policies.md) [وتكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md).

يتم تسليم الرسالة التي تنجح في تمرير كافة طبقات الحماية هذه إلى المستلمين.

لمزيد من المعلومات، راجع [ترتيب حماية البريد الإلكتروني وأسبقيته](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>مراكز بيانات EOP

يعمل EOP على شبكة عالمية من مراكز البيانات المصممة لتوفير أفضل توفر. على سبيل المثال، إذا أصبح مركز البيانات غير متوفر، يتم توجيه رسائل البريد الإلكتروني تلقائيا إلى مركز بيانات آخر دون أي انقطاع في الخدمة. تقبل الخوادم في كل مركز بيانات الرسائل بالنيابة عنك، ما يوفر طبقة من الفصل بين مؤسستك والإنترنت، وبالتالي تقليل الحمل على خوادمك. من خلال هذه الشبكة عالية التوفر، يمكن ل Microsoft التأكد من وصول البريد الإلكتروني إلى مؤسستك في الوقت المناسب.

ينفذ EOP موازنة التحميل بين مراكز البيانات ولكن فقط داخل منطقة. إذا كنت متوفرا في منطقة واحدة، فستتم معالجة كل رسائلك باستخدام توجيه البريد لتلك المنطقة.

### <a name="eop-features"></a>ميزات EOP

يوفر هذا القسم نظرة عامة عالية المستوى على الميزات الرئيسية المتوفرة في EOP.

للحصول على معلومات حول المتطلبات والحدود المهمة وتوافر الميزات عبر جميع خطط اشتراك EOP، راجع [وصف خدمة Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**الملاحظات**:

- يستخدم EOP العديد من قوائم حظر URL التي تساعد في اكتشاف الارتباطات الضارة المعروفة داخل الرسائل.
- يستخدم EOP قائمة واسعة من المجالات المعروفة بإرسال البريد العشوائي.
- يستخدم EOP العديد من محركات مكافحة البرامج الضارة للمساعدة في حماية عملائنا تلقائيا في جميع الأوقات.
- يفحص EOP الحمولة النشطة في نص الرسالة وكافة مرفقات الرسائل للكشف عن البرامج الضارة.
- للحصول على القيم الموصى بها لنهج الحماية، راجع [الإعدادات الموصى بها ل EOP والأمان Microsoft Defender لـ Office 365](recommended-settings-for-eop-and-office365.md).
- للحصول على إرشادات سريعة لتكوين نهج الحماية، راجع [الحماية من التهديدات](protect-against-threats.md).

|ميزه|تعليقات|
|---|---|
|**حمايه**||
|مكافحة البرامج الضارة|[الحماية من البرامج الضارة في EOP](anti-malware-protection.md) <p> [الأسئلة المتداولة حول الحماية من البرامج الضارة](anti-malware-protection-faq-eop.yml) <p> [تكوين نهج مكافحة البرامج الضارة في EOP](configure-anti-malware-policies.md)|
|مكافحة البريد العشوائي الوارد|[الحماية من البريد العشوائي في EOP](anti-spam-protection.md) <p> [الأسئلة المتداولة حول الحماية من البريد العشوائي](anti-spam-protection-faq.yml) <p> [تكوين نهج مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md)|
|مكافحة البريد العشوائي الصادر|[الحماية من البريد العشوائي الصادر في EOP](outbound-spam-controls.md) <p> [تكوين تصفية البريد العشوائي الصادر في EOP](configure-the-outbound-spam-policy.md) <p> [التحكم في إعادة توجيه البريد الإلكتروني الخارجي التلقائي في Microsoft 365](external-email-forwarding.md)|
|تصفية الاتصال|[تكوين تصفية الاتصال](configure-the-connection-filter-policy.md)|
|مكافحة التصيد الاحتيالي|[نهج مكافحة التصيد الاحتيالي في Microsoft 365](set-up-anti-phishing-policies.md) <p> [تكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md)|
|الحماية من تزييف الهوية|[تزييف التحليل الذكي في EOP](learn-about-spoof-intelligence.md) <p> [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md)|
|الإزالة التلقائية بدون ساعة (ZAP) لرسائل البرامج الضارة والبريد العشوائي والتصيد الاحتيالي التي تم تسليمها|[ZAP في Exchange Online](zero-hour-auto-purge.md)|
|نُهج أمان مُعدّة مسبقاً|[نهج الأمان التي تم تعيينها مسبقا في EOP و Microsoft Defender لـ Office 365](preset-security-policies.md) <p> [محلل التكوين لنهج الحماية في EOP Microsoft Defender لـ Office 365](configuration-analyzer-for-security-policies.md)|
|قائمة السماح/الحظر للمستأجر|[إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md)|
|حظر القوائم لمرسلي الرسائل|[إنشاء قوائم المرسلين المحظورة في EOP](create-block-sender-lists-in-office-365.md)|
|السماح بقوائم لمرسلي الرسائل|[إنشاء قوائم المرسلين الآمنة في EOP](create-safe-sender-lists-in-office-365.md)|
|حظر الحافة المستندة إلى الدليل (DBEB)|[استخدام حظر الحافة المستندة إلى الدليل لرفض الرسائل المرسلة إلى مستلمين غير صالحين](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**العزل والإرسالات**||
|إرسال المسؤول|[استخدام عمليات إرسال المسؤول لإرسال رسائل البريد العشوائي والتصيد الاحتيالي وعناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md)|
|عمليات إرسال المستخدم (علبة بريد مخصصة)|[نهج عمليات إرسال المستخدم](user-submission.md)|
|العزل - المسؤولون|[إدارة الرسائل والملفات المعزولة كمسؤول في EOP](manage-quarantined-messages-and-files.md) <p> [الأسئلة المتداولة حول الرسائل المعزولة](quarantine-faq.yml) <p> [الإبلاغ عن الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md) <p> [رؤوس رسائل مكافحة البريد العشوائي في Microsoft 365](anti-spam-message-headers.md) <p> يمكنك تحليل رؤوس الرسائل للرسائل المعزولة باستخدام [محلل رأس الرسالة في](https://mha.azurewebsites.net/).|
|العزل - المستخدمون النهائيون|[البحث عن الرسائل المعزولة وتحريرها كمستخدم في EOP](find-and-release-quarantined-messages-as-a-user.md) <p> [استخدام إعلامات العزل لإصدار الرسائل المعزولة والإبلاغ بها](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [سياسات العزل](quarantine-policies.md)|
|**تدفق البريد**||
|قواعد تدفق البريد|[قواعد تدفق البريد (قواعد النقل) في Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [شروط قاعدة تدفق البريد والاستثناءات (دالات التقييم) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [إجراءات قاعدة تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [إدارة قواعد تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [إجراءات قاعدة تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|المجالات المقبولة|[إدارة المجالات المقبولة في Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|الروابط|[تكوين تدفق البريد باستخدام الموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|تصفية محسنة للموصلات|[تصفية محسنة للموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**رصد**||
|تتبع الرسائل|[تتبع الرسائل](message-trace-scc.md) <p> [تتبع الرسائل في مركز إدارة Exchange](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|تقارير تعاون & البريد الإلكتروني|[عرض تقارير أمان البريد الإلكتروني](view-email-security-reports.md)|
|تقارير تدفق البريد|[عرض تقارير تدفق البريد](view-mail-flow-reports.md) <p> [تقارير تدفق البريد في مركز إدارة Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|رؤى تدفق البريد|[رؤى تدفق البريد](mail-flow-insights-v2.md) <p> [رؤى تدفق البريد في مركز إدارة Exchange](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|تدقيق التقارير|[تدقيق التقارير في مركز إدارة Exchange](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|نُهج التنبيهات|[نُهج التنبيهات](../../compliance/alert-policies.md)|
|**اتفاقيات مستوى الخدمة (SLAs) والدعم**||
|اتفاقية مستوى الخدمة لفعالية البريد العشوائي|\> 99%|
|نسبة إيجابية خاطئة ل SLA|\< 1:250,000|
|الكشف عن الفيروسات وحظر اتفاقية مستوى الخدمة|100٪ من الفيروسات المعروفة|
|اتفاقية مستوى الخدمة لوقت التشغيل الشهري|99.999%|
|الدعم التقني الهاتف والويب على مدار 24 ساعة في اليوم، سبعة أيام في الأسبوع|[تعليمات ودعم EOP](help-and-support-for-eop.md).|
|**ميزات أخرى**||
|شبكة عمومية متكررة جغرافيا من الخوادم|يعمل EOP على شبكة عالمية من مراكز البيانات المصممة للمساعدة في توفير أفضل توفر. لمزيد من المعلومات، راجع قسم [مراكز بيانات EOP](#eop-datacenters) سابقا في هذه المقالة.|
|وضع الرسائل في قائمة الانتظار عندما لا يمكن للخادم المحلي قبول البريد|تبقى الرسائل المؤجلة في قوائم الانتظار الخاصة بنا لمدة يوم واحد. تستند محاولات إعادة محاولة الرسائل إلى الخطأ الذي نحصل عليه مرة أخرى من نظام البريد الخاص بالمستلم. في المتوسط، تتم إعادة محاولة الرسائل كل 5 دقائق. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول وضع EOP في قائمة الانتظار والتأجيل والرسائل المرتدة](eop-queued-deferred-and-bounced-messages-faq.yml).|
|Office 365 تشفير الرسائل متوفر كوظيفة إضافية|لمزيد من المعلومات، راجع [التشفير في Office 365](../../compliance/encryption.md).|
|||
