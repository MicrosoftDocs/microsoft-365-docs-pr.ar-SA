---
title: Exchange Online Protection (EOP)
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
description: تعرف على Exchange Online Protection (EOP) المساعدة في حماية مؤسسة البريد الإلكتروني المحلية في بيئات مستقلة ومختلطة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3fb49a24ae378be990efd727450a06889cc50679
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473354"
---
# <a name="exchange-online-protection-overview"></a>Exchange Online Protection عامة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) هي خدمة التصفية المستندة إلى السحابة التي تحمي مؤسستك من البريد العشوائي والبرامج الضارة وتهديدات البريد الإلكتروني الأخرى. يتم تضمين EOP في Microsoft 365 المؤسسات التي Exchange Online البريد.

> [!NOTE]
> يتوفر EOP أيضا بمفرده لحماية علب البريد المحلية وفي البيئات المختلطة لحماية علب البريد Exchange المحلية. لمزيد من المعلومات، راجع [قائمة مستقلة Exchange Online Protection](/exchange/standalone-eop/standalone-eop).

الخطوات اللازمة لإعداد ميزات أمان EOP ومقارنة الأمان المضاف الذي تحصل عليه في Microsoft Defender لـ Office 365، راجع الحماية [من التهديدات](protect-against-threats.md). تتوفر الإعدادات المستحسنة لمميزات EOP في الإعدادات المستحسنة [ل EOP Microsoft Defender لـ Office 365 الأمان](recommended-settings-for-eop-and-office365.md).

تشرح بقية هذه المقالة كيفية عمل EOP والميزات المتوفرة في EOP.

## <a name="how-eop-works"></a>كيفية عمل EOP

لفهم كيفية عمل EOP، من المساعدة في معرفة كيفية عمله مع البريد الإلكتروني الوارد:

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="رسم البريد الإلكتروني من الإنترنت أو ملاحظات العملاء التي تمر إلى EOP وعبر الاتصال، و مكافحة البرامج الضارة، وتصفية قواعد تدفق البريد-الشرطة المائلة-نهج، وتصفية المحتوى، قبل الحكم إما بالبريد غير الهام أو الفحص أو تسليم بريد المستخدم النهائي" lightbox="../../media/tp_emailprocessingineopt3.png":::

1. عندما تدخل رسالة واردة EOP، تمر في البداية عبر تصفية الاتصال، التي تحقق من سمعة المرسل. يتم إيقاف معظم البريد العشوائي في هذه المرحلة ويرفضه EOP. لمزيد من المعلومات، راجع [تكوين تصفية الاتصال](configure-the-connection-filter-policy.md).

2. بعد ذلك، يتم فحص الرسالة للكشف عن البرامج الضارة. إذا تم العثور على البرامج الضارة في الرسالة أو المرفقات (المرفقات) يتم تسليم الرسالة إلى الفحص. بشكل افتراضي، يمكن للمسؤولين فقط عرض الرسائل التي تم فحص البرامج الضارة والتفاعل معها. ولكن، يمكن للمسؤولين إنشاء سياسات الفحص [](quarantine-policies.md) واستخدامها لتحديد ما يسمح للمستخدمين به للرسائل المعزولة. لمعرفة المزيد حول الحماية من البرامج الضارة، راجع [الحماية من البرامج الضارة في EOP](anti-malware-protection.md).

3. تستمر الرسالة من خلال تصفية النهج، حيث يتم تقييمها مقابل أي قواعد تدفق بريد (تعرف أيضا بقواعد النقل) التي أنشأتها. على سبيل المثال، يمكن للقاعدة إرسال إعلام إلى مدير عند وصول رسالة من مرسل معين.

   في المؤسسة المحلية التي Exchange Enterprise CAL مع تراخيص الخدمات، يتم أيضا التحقق من منع فقدان البيانات [(DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) في EOP في هذه المرحلة.

4. تمر الرسالة عبر تصفية المحتوى (مكافحة البريد العشوائي و مكافحة الانتحال) حيث يتم تعريف الرسائل الضارة على أنها بريد عشوائي أو بريد عشوائي عالي الثقة أو تصيد احتيالي أو تصيد احتيالي عالي الثقة أو مجموعة (سياسات مكافحة البريد العشوائي) أو انتحال (إعدادات الانتحال في سياسات مكافحة التصيد الاحتيالي). يمكنك تكوين الإجراء الذي يجب اتخاذه على الرسالة استنادا إلى قرار التصفية (الفحص والانتقال إلى مجلد البريد الإلكتروني غير الهام وغير ذلك)، وما يمكن للمستخدمين فعله بالرسائل المعزولة باستخدام سياسات [الفحص.](quarantine-policies.md) لمزيد من المعلومات، راجع [تكوين سياسات](configure-your-spam-filter-policies.md) مكافحة البريد العشوائي وتكوين سياسات مكافحة التصيد الاحتيالي [في EOP](configure-anti-phishing-policies-eop.md).

يتم تسليم رسالة نجحت في تمرير كل طبقات الحماية هذه إلى المستلمين.

لمزيد من المعلومات، راجع [ترتيب حماية البريد الإلكتروني وأسبقيته](how-policies-and-protections-are-combined.md).

### <a name="eop-datacenters"></a>مراكز بيانات EOP

يتم تشغيل EOP على شبكة عالمية من مراكز البيانات المصممة لتوفير أفضل توفر. على سبيل المثال، إذا لم يكن مركز البيانات متوفرا، يتم توجيه رسائل البريد الإلكتروني تلقائيا إلى مركز بيانات آخر دون أي انقطاع في الخدمة. تقبل الخوادم في كل مركز بيانات الرسائل بالنيابة عنك، مما يوفر طبقة فصل بين مؤسستك والإنترنت، مما يؤدي إلى تقليل التحميل على الخوادم. من خلال هذه الشبكة المتوفرة بشكل كبير، يمكن أن تضمن Microsoft وصول البريد الإلكتروني إلى مؤسستك في الوقت المناسب.

ينفذ EOP موازنة التحميل بين مراكز البيانات ولكن ضمن منطقة فقط. إذا تم توفير بريدك في منطقة واحدة، سيتم معالجة كل رسائلك باستخدام توجيه البريد لهذه المنطقة.

### <a name="eop-features"></a>ميزات EOP

يوفر هذا القسم نظرة عامة عالية المستوى حول الميزات الرئيسية المتوفرة في EOP.

للحصول على معلومات حول المتطلبات والحدود الهامة وتوفر الميزات عبر كل خطط اشتراك EOP، راجع وصف Exchange Online Protection [الخدمة](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description).

**ملاحظات**:

- يستخدم EOP العديد من قوائم حظر URL التي تساعد في الكشف عن الارتباطات الضارة المعروفة داخل الرسائل.
- يستخدم EOP قائمة واسعة من المجالات المعروفة بإرسال البريد العشوائي.
- يستخدم EOP العديد من محركات الحماية من البرامج الضارة للمساعدة في حماية عملائنا تلقائيا في جميع الأوقات.
- يفحص EOP الحمولة النشطة في نص الرسالة وكل مرفقات الرسائل للبرامج الضارة.
- للحصول على القيم الموصى بها لنهج الحماية، راجع الإعدادات المستحسنة [ل EOP Microsoft Defender لـ Office 365 الأمان](recommended-settings-for-eop-and-office365.md).
- للحصول على إرشادات سريعة لتكوين سياسات الحماية، راجع [الحماية من التهديدات](protect-against-threats.md).

|الميزة|التعليقات|
|---|---|
|**الحماية**||
|مكافحة البرامج الضارة|[الحماية من البرامج الضارة في EOP](anti-malware-protection.md) <p> [الأسئلة الشائعة حول الحماية من البرامج الضارة](anti-malware-protection-faq-eop.yml) <p> [تكوين سياسات مكافحة البرامج الضارة في EOP](configure-anti-malware-policies.md)|
|مكافحة البريد العشوائي الوارد|[الحماية من البريد العشوائي في EOP](anti-spam-protection.md) <p> [الأسئلة الشائعة حول الحماية من البريد العشوائي](anti-spam-protection-faq.yml) <p> [تكوين سياسات مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md)|
|مكافحة البريد العشوائي الصادر|[الحماية من البريد العشوائي الصادر في EOP](outbound-spam-controls.md) <p> [تكوين تصفية البريد العشوائي الصادر في EOP](configure-the-outbound-spam-policy.md) <p> [التحكم في إعادة توجيه البريد الإلكتروني الخارجي تلقائيا في Microsoft 365](external-email-forwarding.md)|
|تصفية الاتصال|[تكوين تصفية الاتصال](configure-the-connection-filter-policy.md)|
|مكافحة التصيد الاحتيالي|[سياسات مكافحة التصيد الاحتيالي في Microsoft 365](set-up-anti-phishing-policies.md) <p> [تكوين سياسات مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md)|
|الحماية من ال انتحال|[المعلومات الاستخبارية المنتحلة في EOP](learn-about-spoof-intelligence.md) <p> [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md)|
|إزالة تلقائية لمدة ساعة (ZAP) للبرامج الضارة والبريد العشوائي ورسائل التصيد الاحتيالي التي تم تسليمها|[ZAP في Exchange Online](zero-hour-auto-purge.md)|
|سياسات الأمان التي تم الإعداد المسبق لها|[سياسات الأمان المحددة مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md) <p> [محلل التكوين لنهج الحماية في EOP Microsoft Defender لـ Office 365](configuration-analyzer-for-security-policies.md)|
|قائمة السماح/الحظر للمستأجر|[إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md)|
|حظر القوائم لمرسلي الرسائل|[إنشاء قوائم المرسلين المحظورين في EOP](create-block-sender-lists-in-office-365.md)|
|السماح ب القوائم لمرسلي الرسائل|[إنشاء قوائم مرسلين آمنة في EOP](create-safe-sender-lists-in-office-365.md)|
|حظر Edge المستند إلى الدليل (DBEB)|[استخدام حظر Edge المستند إلى الدليل لرفض الرسائل المرسلة إلى مستلمين غير صالحين](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)|
|**الفحص والتقديمات**||
|إرسال المسؤول|[استخدام إرسال المسؤول لإرسال البريد العشوائي والتصيد الاحتيالي عناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md)|
|إرسالات المستخدم (علبة بريد مخصصة)|[نهج إرسالات المستخدم](user-submission.md)|
|الفحص - المسؤولون|[إدارة الرسائل والملفات المعزولة كمسؤول في EOP](manage-quarantined-messages-and-files.md) <p> [الأسئلة الشائعة حول الرسائل المعزولة](quarantine-faq.yml) <p> [الإبلاغ عن الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md) <p> [رؤوس رسائل مكافحة البريد العشوائي في Microsoft 365](anti-spam-message-headers.md) <p> يمكنك تحليل رؤوس الرسائل للرسائل المعزولة باستخدام محلل [رؤوس الرسائل في](https://mha.azurewebsites.net/).|
|الفحص - المستخدمون النهائيون|[البحث عن الرسائل المعزولة وإطلاقها كمستخدم في EOP](find-and-release-quarantined-messages-as-a-user.md) <p> [استخدام إعلامات الفحص للافراج عن الرسائل المعزولة](use-spam-notifications-to-release-and-report-quarantined-messages.md) <p> [سياسات الفحص](quarantine-policies.md)|
|**تدفق البريد**||
|قواعد تدفق البريد|[قواعد تدفق البريد (قواعد النقل) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) <p> [شروط قاعدة تدفق البريد والاستثناءات (الشروط) في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions) <p> [إجراءات قاعدة تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions) <p> [إدارة قواعد تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules) <p> [إجراءات قاعدة تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-procedures)|
|المجالات المقبولة|[إدارة المجالات المقبولة في Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)|
|الموصلات|[تكوين تدفق البريد باستخدام الموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)|
|تصفية محسنة للموصلات|[تصفية محسنة للموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)|
|**المراقبة**||
|تتبع الرسائل|[تتبع الرسائل](message-trace-scc.md) <p> [تتبع الرسائل في Exchange إدارة](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac)|
|إرسال & تقارير التعاون عبر البريد الإلكتروني|[عرض تقارير أمان البريد الإلكتروني](view-email-security-reports.md)|
|تقارير تدفق البريد|[عرض تقارير تدفق البريد](view-mail-flow-reports.md) <p> [تقارير تدفق البريد في Exchange إدارة البريد](/exchange/monitoring/mail-flow-reports/mail-flow-reports)|
|تحليلات تدفق البريد|[تحليلات تدفق البريد](mail-flow-insights-v2.md) <p> [تحليلات تدفق البريد في Exchange إدارة البريد](/exchange/monitoring/mail-flow-insights/mail-flow-insights)|
|تقارير التدقيق|[تقارير التدقيق في مركز إدارة Exchange](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports)|
|سياسات التنبيه|[سياسات التنبيه](../../compliance/alert-policies.md)|
|**اتفاقيات مستوى الخدمة (SLAs) والدعم**||
|SLA بفعالية البريد العشوائي|\> 99%|
|خطأ في نسبة موجبة ل SLA|\< 1:250,000|
|الكشف عن الفيروسات وحظر SLA|100٪ من الفيروسات المعروفة|
|SLA وقت التشغيل الشهري|99.999%|
|الهاتف الدعم التقني على الويب على مدار 24 ساعة في اليوم، سبعة أيام في الأسبوع|[تعليمات ودعم EOP](help-and-support-for-eop.md).|
|**ميزات أخرى**||
|شبكة خوادم عالمية مترددة جغرافيا|يتم تشغيل EOP على شبكة عالمية من مراكز البيانات التي تم تصميمها للمساعدة في توفير أفضل توفر. لمزيد من المعلومات، راجع القسم [مراكز بيانات EOP](#eop-datacenters) سابقا في هذه المقالة.|
|وضع الرسالة في قائمة انتظار عندما يتعذر على الخادم في الموقع قبول البريد|تبقى الرسائل المؤجلة في قوائم الانتظار ليوم واحد. تستند محاولات إعادة محاولة الرسائل إلى الخطأ الذي نرجعه من نظام البريد الخاص بالمستلم. في المتوسط، يتم إعادة إعادة الرسائل كل 5 دقائق. لمزيد من المعلومات، راجع الأسئلة الشائعة حول [الرسائل المرتدة](eop-queued-deferred-and-bounced-messages-faq.yml) والمؤجلة والمرتدة في قائمة انتظار EOP.|
|Office 365 تشفير الرسائل المتوفرة كعناية إضافية|لمزيد من المعلومات، راجع [التشفير في Office 365](../../compliance/encryption.md).|
|||
