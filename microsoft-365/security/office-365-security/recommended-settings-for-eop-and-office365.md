---
title: توصيات Microsoft لإعدادات أمان EOP Defender لـ Office 365
keywords: Office 365 توصيات الأمان، إطار نهج المرسل، تقارير الرسائل المستندة إلى المجال والمطابقة، DomainKeys Identified Mail، الخطوات، كيفية عمله، أساسيات الأمان، الخطوط الأساسية ل EOP، الخطوط الأساسية Defender لـ Office 365، إعداد Defender لـ Office 365، إعداد EOP، تكوين Defender لـ Office 365 وتكوين EOP وتكوين الأمان
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: ما هي أفضل الممارسات لإعدادات الأمان Exchange Online Protection (EOP) Defender لـ Office 365؟ ما هي التوصيات الحالية للحماية القياسية؟ ما الذي يجب استخدامه إذا كنت تريد أن تكون أكثر صرامة؟ وما هي الإضافات التي تحصل عليها إذا كنت تستخدم Defender لـ Office 365 أيضا؟
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 921523ea3c1d73dc83c148cc2e61aab416ed9302
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599288"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>الإعدادات الموصى بها ل EOP والأمان Microsoft Defender لـ Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** هو جوهر الأمان لاشتراكات Microsoft 365 ويساعد على منع رسائل البريد الإلكتروني الضارة من الوصول إلى علب الوارد الخاصة بالموظف. ولكن مع ظهور هجمات جديدة وأكثر تعقيدا كل يوم، غالبا ما تكون هناك حاجة إلى حماية محسنة. **تحتوي Microsoft Defender لـ Office 365** الخطة 1 أو الخطة 2 على ميزات إضافية تمنح المسؤولين المزيد من طبقات الأمان والتحكم والتحقيق.

على الرغم من أننا نمكن مسؤولي الأمان من تخصيص إعدادات الأمان الخاصة بهم، هناك مستويان من مستويات الأمان في EOP Microsoft Defender لـ Office 365 نوصي بهما: **قياسي** **وضيق**. على الرغم من اختلاف بيئات العملاء واحتياجاتهم، فإن مستويات التصفية هذه ستساعد على منع البريد غير المرغوب فيه من الوصول إلى علبة الوارد الخاصة بالموظفين في معظم الحالات.

لتطبيق الإعدادات القياسية أو الصارمة تلقائيا على المستخدمين، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

تصف هذه المقالة الإعدادات الافتراضية، وكذلك الإعدادات القياسية والضيقة الموصى بها للمساعدة في حماية المستخدمين. تحتوي الجداول على الإعدادات في مدخل Microsoft 365 Defender وPowerShell (Exchange Online PowerShell أو Exchange Online Protection PowerShell المستقل للمؤسسات التي لا تحتوي على علب بريد Exchange Online).

> [!NOTE]
> يمكن أن تساعدك الوحدة النمطية Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) ل PowerShell (المسؤولين) في العثور على القيم الحالية لهذه الإعدادات. على وجه التحديد، ينشئ **Get-ORCAReport** cmdlet تقييم مكافحة البريد العشوائي ومكافحة التصيد الاحتيالي وإعدادات الحماية الأخرى للرسائل. يمكنك تنزيل الوحدة النمطية ORCA في <https://www.powershellgallery.com/packages/ORCA/>.
>
> في المؤسسات Microsoft 365، نوصي بترك عامل تصفية البريد الإلكتروني غير الهام في Outlook تعيينه إلى "**بلا تصفية تلقائية**" لمنع التعارضات غير الضرورية (الإيجابية والسلبية) مع أحكام تصفية البريد العشوائي من EOP. لمزيد من المعلومات، راجع المقالات التالية:
>
> - [تكوين إعدادات البريد الإلكتروني غير الهام على علب بريد Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md)
> - [حول إعدادات البريد الإلكتروني غير الهام في Outlook](configure-junk-email-settings-on-exo-mailboxes.md#about-junk-email-settings-in-outlook)
> - [تغيير مستوى الحماية في عامل تصفية البريد الإلكتروني غير الهام](https://support.microsoft.com/en-us/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b)
> - [إنشاء قوائم المرسلين الآمنة في EOP](create-safe-sender-lists-in-office-365.md)
> - [إنشاء قوائم المرسلين المحظورة في EOP](create-block-sender-lists-in-office-365.md)

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>الحماية من البريد العشوائي والبرامج الضارة والحماية من التصيد الاحتيالي في EOP

تعد مكافحة البريد العشوائي والبرامج الضارة والتصيد الاحتيالي ميزات EOP التي يمكن للمسؤولين تكوينها. نوصي بالتكوينات القياسية أو الصارمة التالية.

### <a name="eop-anti-spam-policy-settings"></a>إعدادات نهج مكافحة البريد العشوائي EOP

لإنشاء نهج مكافحة البريد العشوائي وتكوينها، راجع [تكوين نهج مكافحة البريد العشوائي في EOP](configure-your-spam-filter-policies.md).

|اسم ميزة الأمان|افتراضي|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|---|
|**حد البريد الإلكتروني المجمع & خصائص البريد العشوائي**|||||
|**حد البريد الإلكتروني المجمع** <br/><br/> _BulkThreshold_|7|6|4|للحصول على التفاصيل، راجع [مستوى الشكاوى المجمعة (BCL) في EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|يتوفر هذا الإعداد فقط في PowerShell.|
|**زيادة إعدادات نقاط البريد العشوائي**|قباله|قباله|قباله|تعد كل هذه الإعدادات جزءا من عامل تصفية البريد العشوائي المتقدم (ASF). لمزيد من المعلومات، راجع [إعدادات ASF في قسم نهج مكافحة البريد العشوائي](#asf-settings-in-anti-spam-policies) في هذه المقالة.|
|**وضع علامة كإعدادات البريد العشوائي**|قباله|قباله|قباله|معظم هذه الإعدادات هي جزء من ASF. لمزيد من المعلومات، راجع [إعدادات ASF في قسم نهج مكافحة البريد العشوائي](#asf-settings-in-anti-spam-policies) في هذه المقالة.|
|**يحتوي على لغات معينة** <br/><br/> _EnableLanguageBlockList_ <br/><br/> _LanguageBlockList_|**قباله** <br/><br/> `$false` <br/><br/> فارغه|**قباله** <br/><br/> `$false` <br/><br/> فارغه|**قباله** <br/><br/> `$false` <br/><br/> فارغه|ليس لدينا توصية محددة لهذا الإعداد. يمكنك حظر الرسائل بلغات معينة استنادا إلى احتياجات عملك.|
|**من هذه البلدان** <br/><br/> _EnableRegionBlockList_ <br/><br/> _RegionBlockList_|**قباله** <br/><br/> `$false` <br/><br/> فارغه|**قباله** <br/><br/> `$false` <br/><br/> فارغه|**قباله** <br/><br/> `$false` <br/><br/> فارغه|ليس لدينا توصية محددة لهذا الإعداد. يمكنك حظر الرسائل الواردة من بلدان معينة استنادا إلى احتياجات عملك.|
|**وضع الاختبار** (_TestModeAction_)|**None**|**None**|**None**|هذا الإعداد هو جزء من ASF. لمزيد من المعلومات، راجع [إعدادات ASF في قسم نهج مكافحة البريد العشوائي](#asf-settings-in-anti-spam-policies) في هذه المقالة.|
|**الاجراءات**||||أينما حددت **رسالة العزل**، يتوفر مربع **نهج تحديد العزل** . تحدد نهج العزل ما يسمح للمستخدمين بالقيام به للرسائل المعزولة. <br/><br/> تستخدم نهج الأمان القياسية والضيقة المحددة مسبقا نهج العزل الافتراضية (AdminOnlyAccessPolicy أو DefaultFullAccessPolicy دون إعلامات العزل) كما هو موضح في الجدول [هنا](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> عند إنشاء نهج جديد لمكافحة البريد العشوائي، تعني القيمة الفارغة أن نهج العزل الافتراضي يستخدم لتحديد القدرات التاريخية للرسائل التي تم عزلها بواسطة هذا الحكم المحدد (AdminOnlyAccessPolicy مع عدم وجود إعلامات عزل **للتصيد الاحتيالي عالي الثقة**؛ DefaultFullAccessPolicy مع عدم وجود إعلامات عزل لكل شيء آخر). <br/><br/> يمكن للمسؤولين إنشاء وتحديد نهج العزل المخصصة التي تحدد قدرات أكثر تقييدا أو أقل تقييدا للمستخدمين في نهج مكافحة البريد العشوائي الافتراضية أو المخصصة. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).|
|إجراء الكشف عن **البريد العشوائي** <br/><br/> _SpamAction_|**نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**رسالة العزل** <br/><br/> `Quarantine`||
|إجراء الكشف عن **البريد العشوائي عالي الثقة** <br/><br/> _HighConfidenceSpamAction_|**نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**رسالة العزل** <br/><br/> `Quarantine`|**رسالة العزل** <br/><br/> `Quarantine`||
|إجراء الكشف عن **التصيد الاحتيالي** <br/><br/> _PhishSpamAction_|**نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام**<sup>\*</sup> <br/><br/> `MoveToJmf`|**رسالة العزل** <br/><br/> `Quarantine`|**رسالة العزل** <br/><br/> `Quarantine`|<sup>\*</sup> القيمة الافتراضية هي **نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام** في نهج مكافحة البريد العشوائي الافتراضي وفي نهج مكافحة البريد العشوائي الجديدة التي تقوم بإنشائها في PowerShell. القيمة الافتراضية هي **رسالة العزل** في نهج مكافحة البريد العشوائي الجديدة التي تقوم بإنشائها في مدخل Microsoft 365 Defender.|
|إجراء الكشف عن **التصيد الاحتيالي عالي الثقة** <br/><br/> _HighConfidencePhishAction_|**رسالة العزل** <br/><br/> `Quarantine`|**رسالة العزل** <br/><br/> `Quarantine`|**رسالة العزل** <br/><br/> `Quarantine`||
|إجراء الكشف **المجمع** <br/><br/> _BulkSpamAction_|**نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**رسالة العزل** <br/><br/> `Quarantine`||
|**الاحتفاظ بالبريد العشوائي في العزل لعدة أيام** <br/><br/> _QuarantineRetentionPeriod_|15 يوما<sup>\*</sup>|30 يوماً|30 يوماً|<sup>\*</sup> القيمة الافتراضية هي 15 يوما في نهج مكافحة البريد العشوائي الافتراضي وفي نهج مكافحة البريد العشوائي الجديدة التي تقوم بإنشائها في PowerShell. القيمة الافتراضية هي 30 يوما في نهج مكافحة البريد العشوائي الجديدة التي تقوم بإنشائها في مدخل Microsoft 365 Defender. <br/><br/> تؤثر هذه القيمة أيضا على الرسائل التي يتم عزلها بواسطة نهج مكافحة التصيد الاحتيالي. لمزيد من المعلومات، راجع [رسائل البريد الإلكتروني المعزولة في EOP](quarantine-email-messages.md).|
|**تمكين تلميحات أمان البريد العشوائي** <br/><br/> _InlineSafetyTipsEnabled_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|تمكين الإزالة التلقائية بدون ساعة (ZAP) لرسائل التصيد الاحتيالي <br/><br/> _PhishZapEnabled_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|تمكين ZAP لرسائل البريد العشوائي <br/><br/> _SpamZapEnabled_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**السماح بقائمة حظر &**|||||
|المرسلون المسموح بهم <br/><br/> _الenders المسموح بها_|None|None|None||
|مجالات المرسل المسموح بها <br/><br/> _AllowedSenderDomains_|None|None|None|تعد إضافة المجالات إلى قائمة المرسلين المسموح بهم فكرة سيئة للغاية. سيتمكن المهاجمون من إرسال بريد إلكتروني إليك يمكن تصفيته بخلاف ذلك. <br/><br/> استخدم [التحليل الذكي للانتحال](learn-about-spoof-intelligence.md) وقائمة [السماح/الحظر للمستأجر](tenant-allow-block-list.md) لمراجعة كل المرسلين الذين ينتحلون عناوين البريد الإلكتروني للمرسلين في مجالات البريد الإلكتروني الخاصة بمؤسستك أو ينتحلون عناوين البريد الإلكتروني للمرسلين في المجالات الخارجية.|
|المرسلون المحظورون <br/><br/> _الenders المحظورة_|None|None|None||
|مجالات المرسلين المحظورة <br/><br/> _BlockedSenderDomains_|None|None|None||

#### <a name="asf-settings-in-anti-spam-policies"></a>إعدادات ASF في نهج مكافحة البريد العشوائي

يصف الجدول في هذا القسم إعدادات تصفية البريد العشوائي المتقدمة (ASF) المتوفرة في نهج مكافحة البريد العشوائي. كل هذه الإعدادات **متوقفة عن التشغيل** لكل من المستويات **القياسية** **والضيقة** . لمزيد من المعلومات حول إعدادات ASF، راجع [إعدادات تصفية البريد العشوائي المتقدمة (ASF) في EOP](advanced-spam-filtering-asf-options.md).

|اسم ميزة الأمان|التعليق|
|---|---|
|**ارتباطات الصور إلى المواقع البعيدة** (_IncreaseScoreWithImageLinks_)||
|**عنوان IP رقمي في عنوان URL** (_IncreaseScoreWithNumericIps_)||
|**إعادة توجيه URL إلى منفذ آخر** (_IncreaseScoreWithRedirectToOtherPort_)||
|**ارتباطات إلى مواقع ويب .biz أو .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**رسائل فارغة** (_MarkAsSpamEmptyMessages_)||
|**تضمين العلامات في HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript أو VBScript في HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**علامات النموذج في HTML** (_MarkAsSpamFormTagsInHtml_)||
|**وضع إطار أو علامات iframe في HTML** (_MarkAsSpamFramesInHtml_)||
|**أخطاء ويب في HTML** (_MarkAsSpamWebBugsInHtml_)||
|**علامات الكائن في HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**الكلمات الحساسة** (_MarkAsSpamSensitiveWordList_)||
|**سجل SPF: فشل ثابت** (_MarkAsSpamSpfRecordHardFail_)||
|**فشل ثابت في تصفية معرف المرسل** (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**وضع الاختبار** (_TestModeAction_)|بالنسبة لإعدادات ASF التي تدعم **الاختبار** كإجراء، يمكنك تكوين إجراء وضع الاختبار إلى **بلا**، **أو إضافة نص X-Header افتراضي**، أو **إرسال رسالة مخفية** (`None`، أو، `AddXHeader`أو `BccMessage`). لمزيد من المعلومات، راجع [تمكين إعدادات ASF أو تعطيلها أو اختبارها](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>إعدادات نهج البريد العشوائي الصادر EOP

لإنشاء نهج البريد العشوائي الصادرة وتكوينها، راجع [تكوين تصفية البريد العشوائي الصادر في EOP](configure-the-outbound-spam-policy.md).

لمزيد من المعلومات حول حدود الإرسال الافتراضية في الخدمة، راجع [حدود الإرسال](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> نهج البريد العشوائي الصادرة ليست جزءا من نهج الأمان القياسية أو الصارمة التي تم تعيينها مسبقا. تشير القيم **القياسية** **والضيقة** إلى قيمنا **الموصى بها** في نهج البريد العشوائي الصادر الافتراضي أو نهج البريد العشوائي الصادرة المخصصة التي تقوم بإنشائها.

|اسم ميزة الأمان|افتراضي|اوصت<br/>Standard|اوصت<br/>صارمه|التعليق|
|---|:---:|:---:|:---:|---|
|**تعيين حد رسالة خارجي** <br/><br/> _RecipientLimitExternalPerHour_|0|500|400|تعني القيمة الافتراضية 0 استخدام إعدادات الخدمة الافتراضية.|
|**تعيين حد رسالة داخلي** <br/><br/> _RecipientLimitInternalPerHour_|0|1000|800|تعني القيمة الافتراضية 0 استخدام إعدادات الخدمة الافتراضية.|
|**تعيين حد رسائل يومي** <br/><br/> _RecipientLimitPerDay_|0|1000|800|تعني القيمة الافتراضية 0 استخدام إعدادات الخدمة الافتراضية.|
|**القيود المفروضة على المستخدمين الذين يصلون إلى حد الرسالة** <br/><br/> _ActionWhenThresholdReached_|**تقييد المستخدم من إرسال البريد حتى اليوم التالي** <br/><br/> `BlockUserForToday`|**تقييد المستخدم من إرسال البريد** <br/><br/> `BlockUser`|**تقييد المستخدم من إرسال البريد** <br/><br/> `BlockUser`||
|**قواعد إعادة التوجيه التلقائية** <br/><br/> _AutoForwardingMode_|**تلقائي - يتحكم فيه النظام** <br/><br/> `Automatic`|**تلقائي - يتحكم فيه النظام** <br/><br/> `Automatic`|**تلقائي - يتحكم فيه النظام** <br/><br/> `Automatic`|
|**إرسال نسخة من الرسائل الصادرة التي تتجاوز هذه الحدود لهؤلاء المستخدمين والمجموعات** <br/><br/> _BccSuspiciousOutboundMail_ <br/><br/> _BccSuspiciousOutboundAdditionalRecipients_|غير محدد <br/><br/> `$false` <br/><br/> فارغه|غير محدد <br/><br/> `$false` <br/><br/> فارغه|غير محدد <br/><br/> `$false` <br/><br/> فارغه|ليس لدينا توصية محددة لهذا الإعداد. <br/><br/> يعمل هذا الإعداد فقط في نهج البريد العشوائي الصادر الافتراضي. لا يعمل في نهج البريد العشوائي الصادرة المخصصة التي تقوم بإنشائها.|
|**إعلام هؤلاء المستخدمين والمجموعات إذا تم حظر مرسل بسبب إرسال بريد عشوائي صادر** <br/><br/> _NotifyOutboundSpam_ <br/><br/> _NotifyOutboundSpamRecipients_|غير محدد <br/><br/> `$false` <br/><br/> فارغه|غير محدد <br/><br/> `$false` <br/><br/> فارغه|غير محدد <br/><br/> `$false` <br/><br/> فارغه|نهج [التنبيه](../../compliance/alert-policies.md) الافتراضي **المسمى المستخدم المقيد من إرسال البريد الإلكتروني** يرسل بالفعل إعلامات البريد الإلكتروني إلى أعضاء مجموعة **TenantAdmins** (**المسؤولين العموميين**) عندما يتم حظر المستخدمين بسبب تجاوز الحدود في النهج. **نوصي بشدة باستخدام نهج التنبيه بدلا من هذا الإعداد في نهج البريد العشوائي الصادر لإعلام المسؤولين والمستخدمين الآخرين**. للحصول على الإرشادات، راجع [التحقق من إعدادات التنبيه للمستخدمين المقيدين](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>إعدادات نهج مكافحة البرامج الضارة EOP

لإنشاء نهج مكافحة البرامج الضارة وتكوينها، راجع [تكوين نهج مكافحة البرامج الضارة في EOP](configure-anti-malware-policies.md).

|اسم ميزة الأمان|افتراضي|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|---|
|**إعدادات الحماية**|||||
|**تمكين عامل تصفية المرفقات الشائع** <br/><br/> _EnableFileFilter_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|يقوم هذا الإعداد بعزل الرسائل التي تحتوي على مرفقات قابلة للتنفيذ استنادا إلى نوع الملف، بغض النظر عن محتوى المرفق.|
|**تمكين الإزالة التلقائية بدون ساعة للبرامج الضارة** <br/><br/> _ZapEnabled_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**نهج العزل**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|عند إنشاء نهج جديد لمكافحة البرامج الضارة، تعني القيمة الفارغة أن نهج العزل الافتراضي يستخدم لتحديد القدرات التاريخية للرسائل التي تم عزلها كبريد ضار (AdminOnlyAccessPolicy دون إعلامات العزل). <br/><br/> تستخدم نهج الأمان القياسية والضيقة المحددة مسبقا نهج العزل الافتراضي (AdminOnlyAccessPolicy مع عدم وجود إعلامات عزل) كما هو موضح في الجدول [هنا](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> يمكن للمسؤولين إنشاء وتحديد نهج العزل المخصصة التي تحدد المزيد من القدرات للمستخدمين في نهج مكافحة البرامج الضارة الافتراضية أو المخصصة. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).|
|**إعلامات المستلمين**|||||
|**إعلام المستلمين عند عزل الرسائل على أنها برامج ضارة** <br/><br/> _العمل_|غير محدد <br/><br/> _DeleteMessage_|غير محدد <br/><br/> _DeleteMessage_|غير محدد <br/><br/> _DeleteMessage_|إذا تم الكشف عن البرامج الضارة في مرفق بريد إلكتروني، يتم عزل الرسالة ويمكن إصدارها من قبل مسؤول فقط.|
|**إعلامات المرسل**|||||
|**إعلام المرسلين الداخليين عند عزل الرسائل على أنها برامج ضارة** <br/><br/> _EnableInternalSenderNotifications_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**إعلام المرسلين الخارجيين عند عزل الرسائل على أنها برامج ضارة** <br/><br/> _EnableExternalSenderNotifications_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**إعلامات المسؤول**|||||
|**إعلام مسؤول بالرسائل غير المصدقة من المرسلين الداخليين** <br/><br/> _EnableInternalSenderAdminNotifications_ <br/><br/> _InternalSenderAdminAddress_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|ليس لدينا توصية محددة لهذا الإعداد.|
|**إعلام مسؤول بالرسائل غير المصدقة من مرسلين خارجيين** <br/><br/> _EnableExternalSenderAdminNotifications_ <br/><br/> _ExternalSenderAdminAddress_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|ليس لدينا توصية محددة لهذا الإعداد.|
|**تخصيص الإعلامات**||||ليس لدينا أي توصيات محددة لهذه الإعدادات.|
|**استخدام نص إعلام مخصص** <br/><br/> _التعليقات التوضيحية المخصصة_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**من الاسم** <br/><br/> _CustomFromName_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`||
|**من العنوان** <br/><br/> _CustomFromAddress_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`||
|**تخصيص الإعلامات للرسائل الواردة من المرسلين الداخليين**||||يتم استخدام هذه الإعدادات فقط إذا **تم تحديد إعلام المرسلين الداخليين عند عزل الرسائل كالبرمجيات الضارة** أو **إعلام مسؤول بالرسائل التي لم يتم تسليمها من المرسلين الداخليين** .|
|**الموضوع** <br/><br/> _CustomInternalSubject_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`||
|**رساله** <br/><br/> _CustomInternalBody_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`||
|**تخصيص الإعلامات للرسائل الواردة من مرسلين خارجيين**||||يتم استخدام هذه الإعدادات فقط إذا **تم تحديد إعلام المرسلين الخارجيين عند عزل الرسائل كالبرمجيات الضارة** أو **إعلام مسؤول بالرسائل غير المرسلة من المرسلين الخارجيين** .|
|**الموضوع** <br/><br/> _CustomExternalSubject_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`||
|**رساله** <br/><br/> _CustomExternalBody_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>إعدادات نهج مكافحة التصيد الاحتيالي EOP

لمزيد من المعلومات حول هذه الإعدادات، راجع [إعدادات الانتحال](set-up-anti-phishing-policies.md#spoof-settings). لتكوين هذه الإعدادات، راجع [تكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md).

تكون إعدادات تزييف البيانات متداخلة، ولكن لا يعتمد إعداد **إظهار تلميح الأمان جهة الاتصال الأولى** على إعدادات تزييف هوية.

|اسم ميزة الأمان|افتراضي|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|---|
|**حد التصيد الاحتيالي & الحماية**|||||
|**تمكين التحليل الذكي للانتحال** <br/><br/> _EnableSpoofIntelligence_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**الاجراءات**|||||
|**إذا تم الكشف عن الرسالة على أنها منتحلة** <br/><br/> _AuthenticationFailAction_|**نقل الرسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**نقل الرسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**عزل الرسالة** <br/><br/> `Quarantine`|ينطبق هذا الإعداد على المرسلين المخادعة الذين تم حظرهم تلقائيا كما هو موضح في [التحليل الذكي للانتحال](learn-about-spoof-intelligence.md) أو المحظورين يدويا في [قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md). <br/><br/> إذا قمت بتحديد **عزل الرسالة**، يتوفر مربع **نهج تطبيق العزل** لتحديد نهج العزل الذي يحدد ما يسمح للمستخدمين بالقيام به للرسائل التي يتم عزلها على أنها تزييف. عند إنشاء نهج جديد لمكافحة التصيد الاحتيالي، تعني القيمة الفارغة أن نهج العزل الافتراضي يستخدم لتحديد القدرات التاريخية للرسائل التي تم عزلها على أنها تزييف (DefaultFullAccessPolicy دون إعلامات العزل). <br/><br/> تستخدم نهج الأمان القياسية والضيقة المحددة مسبقا نهج العزل الافتراضي (DefaultFullAccessPolicy مع عدم وجود إعلامات عزل) كما هو موضح في الجدول [هنا](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> يمكن للمسؤولين إنشاء نهج العزل المخصصة وتحديدها التي تحدد قدرات أكثر تقييدا أو أقل تقييدا للمستخدمين في نهج مكافحة التصيد الاحتيالي الافتراضية أو المخصصة. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).|
|**إظهار تلميح الأمان جهة الاتصال الأولى** <br/><br/> _EnableFirstContactSafetyTips_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|لمزيد من المعلومات، راجع [تلميح الأمان جهة الاتصال الأولى](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**إظهار (؟) للمرسلين غير المصادق عليهم للانتحال** <br/><br/> _EnableUnauthenticatedSender_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|إضافة علامة استفهام (؟) إلى صورة المرسل في Outlook للمرسلين المخادعة غير المعروفين. لمزيد من المعلومات، راجع [مؤشرات المرسلين غير المصادق عليهم](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|
|**إظهار علامة "via"** <br/><br/> _EnableViaTag_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|إضافة علامة عبر (chris@contoso.com عبر fabrikam.com) إلى عنوان "من" إذا كان مختلفا عن المجال في توقيع DKIM أو عنوان **MAIL FROM** . <br/><br/> لمزيد من المعلومات، راجع [مؤشرات المرسلين غير المصادق عليهم](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|

## <a name="microsoft-defender-for-office-365-security"></a>أمان Microsoft Defender لـ Office 365

تأتي مزايا الأمان الإضافية مع اشتراك Microsoft Defender لـ Office 365. للحصول على أحدث الأخبار والمعلومات، يمكنك الاطلاع على [أحدث الميزات في Defender لـ Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - يوفر نهج مكافحة التصيد الاحتيالي الافتراضي في Microsoft Defender لـ Office 365 [الحماية من الانتحال](set-up-anti-phishing-policies.md#spoof-settings) وذكاء علبة البريد لجميع المستلمين. ومع ذلك، لا يتم تكوين ميزات [حماية الانتحال](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) المتوفرة الأخرى [والإعدادات المتقدمة](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) أو تمكينها في النهج الافتراضي. لتمكين جميع ميزات الحماية، قم بتعديل نهج مكافحة التصيد الاحتيالي الافتراضي أو إنشاء نهج إضافية لمكافحة التصيد الاحتيالي.
>
> - على الرغم من عدم وجود نهج افتراضي خزينة المرفقات أو نهج ارتباطات خزينة، يوفر نهج الأمان المعين مسبقا **للحماية المضمنة** حماية خزينة المرفقات وحماية الارتباطات خزينة لكافة المستلمين (المستخدمون الذين لم يتم تعريفهم في نهج مرفقات خزينة مخصصة أو نهج ارتباطات خزينة). لمزيد من المعلومات، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).
>
> - [لا تعتمد خزينة المرفقات لحماية SharePoint OneDrive Microsoft Teams](mdo-for-spo-odb-and-teams.md) [وحماية المستندات خزينة](safe-docs.md) على نهج الارتباطات خزينة.

إذا كان اشتراكك يتضمن Microsoft Defender لـ Office 365 أو إذا قمت بشراء Defender لـ Office 365 كوظيفة إضافية، فقم بتعيين التكوينات القياسية أو الصارمة التالية.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>إعدادات نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365

يحصل عملاء EOP على مكافحة التصيد الاحتيالي الأساسي كما هو موضح سابقا، ولكن Defender لـ Office 365 يتضمن المزيد من الميزات والتحكم للمساعدة في منع الهجمات واكتشافها ومعالجتها. لإنشاء هذه النهج وتكوينها، راجع [تكوين نهج مكافحة التصيد الاحتيالي في Defender لـ Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>الإعدادات المتقدمة في نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365

لمزيد من المعلومات حول هذا الإعداد، راجع [حدود التصيد الاحتيالي المتقدمة في نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). لتكوين هذا الإعداد، راجع [تكوين نهج مكافحة التصيد الاحتيالي في Defender لـ Office 365](configure-mdo-anti-phishing-policies.md).

|اسم ميزة الأمان|افتراضي|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|---|
|**حد البريد الإلكتروني للتصيد الاحتيالي** <br/><br/> _PhishThresholdLevel_|**1 - قياسي** <br/><br/> `1`|**2 - هجومي** <br/><br/> `2`|**3 - أكثر صرامة** <br/><br/> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>إعدادات الانتحال في نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365

لمزيد من المعلومات حول هذه الإعدادات، راجع [إعدادات انتحال الهوية في نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). لتكوين هذه الإعدادات، راجع [تكوين نهج مكافحة التصيد الاحتيالي في Defender لـ Office 365](configure-mdo-anti-phishing-policies.md).

|اسم ميزة الأمان|افتراضي|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|---|
|**حد التصيد الاحتيالي & الحماية**|||||
|**تمكين المستخدمين من الحماية** (حماية المستخدم منتحلة) <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|غير محدد <br/><br/> `$false` <br/><br/> اي|المحدد <br/><br/> `$true` <br/><br/> \<list of users\>|المحدد <br/><br/> `$true` <br/><br/> \<list of users\>|نوصي بإضافة مستخدمين (مرسلي الرسائل) في الأدوار الرئيسية. داخليا، قد يكون المرسلون المحميون الرئيس التنفيذي والمدير المالي وغيرهم من كبار القادة. خارجيا، يمكن أن يتضمن المرسلون المحميون أعضاء مجلس الإدارة أو مجلس الإدارة. <br/><br/> في نهج الأمان التي تم تعيينها مسبقا، لا يمكنك تحديد المستخدمين الذين يجب حمايتهم. تحتاج إلى تعطيل نهج الأمان المعينة مسبقا واستخدام نهج مخصصة لمكافحة التصيد الاحتيالي لإضافة مستخدمين في الأدوار الرئيسية كما هو مقترح.|
|**تمكين المجالات للحماية** (حماية المجال منتحلة)|غير محدد|المحدد|المحدد||
|**تضمين المجالات التي أملكها** <br/><br/> _EnableOrganizationDomainsProtection_|قباله <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**تضمين مجالات مخصصة** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|قباله <br/><br/> `$false` <br/><br/> اي|المحدد <br/><br/> `$true` <br/><br/> \<list of domains\>|المحدد <br/><br/> `$true` <br/><br/> \<list of domains\>|نوصي بإضافة المجالات (مجالات المرسلين) التي لا تملكها، ولكنك تتفاعل معها بشكل متكرر. <br/><br/> في نهج الأمان التي تم تعيينها مسبقا، لا يمكنك تحديد مجالات custm لحمايتها. تحتاج إلى تعطيل نهج الأمان المعينة مسبقا واستخدام نهج مكافحة التصيد الاحتيالي المخصصة لإضافة مجالات مخصصة للحماية كما هو مقترح.|
|**إضافة المرسلين والمجالات الموثوق بها** <br/><br/> _الendenders المستثناة_ <br/><br/> _ExcludedDomains_|None|None|None|استنادا إلى مؤسستك، نوصي بإضافة المرسلين أو المجالات التي تم تعريفها بشكل غير صحيح على أنها محاولات انتحال.|
|**تمكين تحليل معلومات علبة البريد** <br/><br/> _EnableMailboxIntelligence_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**تمكين التحليل الذكي لحماية الانتحال** <br/><br/> _EnableMailboxIntelligenceProtection_|قباله <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|يسمح هذا الإعداد بالإجراء المحدد للكشف عن الانتحال بواسطة تحليل معلومات علبة البريد.|
|**الاجراءات**||||أينما حددت **«Quarantine the message»**، يتوفر مربع **«Select quarantine policy** ». تحدد نهج العزل ما يسمح للمستخدمين بالقيام به للرسائل المعزولة. <br/><br/> تستخدم نهج الأمان القياسية والضيقة المحددة مسبقا نهج العزل الافتراضي (DefaultFullAccessPolicy مع عدم وجود إعلامات عزل) كما هو موضح في الجدول [هنا](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> عند إنشاء نهج جديد لمكافحة التصيد الاحتيالي، تعني القيمة الفارغة أن نهج العزل الافتراضي يستخدم لتحديد القدرات التاريخية للرسائل التي تم عزلها بواسطة هذا الحكم (DefaultFullAccessPolicy لجميع أنواع الكشف عن الانتحال). <br/><br/> يمكن للمسؤولين إنشاء نهج عزل مخصصة وتحديدها تحدد قدرات أقل تقييدا أو أكثر تقييدا للمستخدمين في نهج مكافحة التصيد الاحتيالي الافتراضية أو المخصصة. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).|
|**إذا تم الكشف عن الرسالة كمستخدم منتحل** <br/><br/> _TargetedUserProtectionAction_|**عدم تطبيق أي إجراء** <br/><br/> `NoAction`|**عزل الرسالة** <br/><br/> `Quarantine`|**عزل الرسالة** <br/><br/> `Quarantine`|تذكر أن نهج الأمان التي تم تعيينها مسبقا لا تسمح لك بتحديد المستخدمين الذين يجب حمايتهم، لذلك لا يقوم هذا الإعداد بشكل فعال بأي شيء في نهج الأمان التي تم تعيينها مسبقا.|
|**إذا تم الكشف عن الرسالة كمجال منتحل** <br/><br/> _TargetedDomainProtectionAction_|**عدم تطبيق أي إجراء** <br/><br/> `NoAction`|**عزل الرسالة** <br/><br/> `Quarantine`|**عزل الرسالة** <br/><br/> `Quarantine`|تذكر أن نهج الأمان التي تم تعيينها مسبقا لا تسمح لك بتحديد المجالات المخصصة التي تريد حمايتها، لذلك يؤثر هذا الإعداد على المجالات التي تملكها فقط، وليس المجالات المخصصة.|
|**إذا كشف تحليل معلومات علبة البريد عن مستخدم منتحل** <br/><br/> _MailboxIntelligenceProtectionAction_|**عدم تطبيق أي إجراء** <br/><br/> `NoAction`|**نقل الرسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**عزل الرسالة** <br/><br/> `Quarantine`||
|**إظهار تلميح الأمان انتحال المستخدم** <br/><br/> _EnableSimilarUsersSafetyTips_|قباله <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**إظهار تلميح الأمان انتحال المجال** <br/><br/> _EnableSimilarDomainsSafetyTips_|قباله <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**إظهار الأحرف غير العادية لانتحال هوية المستخدم تلميح الأمان** <br/><br/> _EnableUnusualCharactersSafetyTips_|قباله <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>إعدادات نهج مكافحة التصيد الاحتيالي EOP في Microsoft Defender لـ Office 365

هذه هي نفس الإعدادات المتوفرة في [إعدادات نهج مكافحة البريد العشوائي في EOP](#eop-anti-spam-policy-settings).

### <a name="safe-attachments-settings"></a>إعدادات مرفقات خزينة

تتضمن خزينة المرفقات في Microsoft Defender لـ Office 365 الإعدادات العمومية التي لا علاقة لها بنهج المرفقات خزينة والإعدادات الخاصة بكل نهج ارتباطات خزينة. لمزيد من المعلومات، راجع [خزينة المرفقات في Defender لـ Office 365](safe-attachments.md).

على الرغم من عدم وجود نهج افتراضي خزينة المرفقات، يوفر نهج الأمان المعين مسبقا **للحماية المضمنة** حماية المرفقات خزينة لكافة المستلمين (المستخدمون الذين لم يتم تعريفهم في نهج المرفقات خزينة المخصصة). لمزيد من المعلومات، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>الإعدادات العمومية لمرفقات خزينة

> [!NOTE]
> يتم تعيين الإعدادات العمومية لمرفقات خزينة بواسطة نهج الأمان المعين مسبقا **للحماية المضمنة**، ولكن ليس من خلال نهج الأمان **القياسية** أو **الصارمة** المعينة مسبقا. وفي كلتا الحالتين، يمكن للمسؤولين تعديل إعدادات المرفقات خزينة العمومية هذه في أي وقت.
>
> يعرض العمود **الافتراضي** القيم قبل وجود نهج الأمان المعين مسبقا **للحماية المضمنة** . يعرض عمود **الحماية المضمن** القيم التي تم تعيينها بواسطة نهج الأمان المعين مسبقا **للحماية المضمنة** ، والتي هي أيضا قيمنا الموصى بها.

لتكوين هذه الإعدادات، راجع [تشغيل خزينة المرفقات SharePoint والمستندات OneDrive Microsoft Teams والمستندات](turn-on-mdo-for-spo-odb-and-teams.md) [خزينة في Microsoft 365 E5](safe-docs.md).

في PowerShell، يمكنك استخدام [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) cmdlet لهذه الإعدادات.

|اسم ميزة الأمان|افتراضي|الحماية المضمنة|التعليق|
|---|:---:|:---:|---|
|**تشغيل Defender لـ Office 365 SharePoint OneDrive Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|قباله <br/><br/> `$false`|في <br/><br/> `$true`|لمنع المستخدمين من تنزيل ملفات ضارة، راجع [استخدام SharePoint Online PowerShell لمنع المستخدمين من تنزيل الملفات الضارة](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**تشغيل مستندات خزينة لعملاء Office** <br/><br/> _EnableSafeDocs_|قباله <br/><br/> `$false`|في <br/><br/> `$true`|هذه الميزة متوفرة وذات معنى فقط مع التراخيص غير المضمنة في Defender لـ Office 365 (على سبيل المثال، Microsoft 365 E5 أو الأمان في Microsoft 365 E5). لمزيد من المعلومات، راجع [خزينة المستندات في Microsoft 365 E5](safe-docs.md).|
|**السماح للأشخاص بالنقر عبر "طريقة عرض محمية" حتى إذا حددت المستندات خزينة الملف على أنه ضار** <br/><br/> _AllowSafeDocsOpen_|قباله <br/><br/> `$false`|قباله <br/><br/> `$false`|يرتبط هذا الإعداد بمستندات خزينة.|

#### <a name="safe-attachments-policy-settings"></a>إعدادات نهج المرفقات خزينة

لتكوين هذه الإعدادات، راجع [إعداد نهج المرفقات خزينة في Defender لـ Office 365](set-up-safe-attachments-policies.md).

في PowerShell، يمكنك استخدام [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) و [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) cmdlets لهذه الإعدادات.

> [!NOTE]
> كما هو موضح سابقا، لا يوجد نهج افتراضي خزينة المرفقات، ولكن يتم تعيين حماية المرفقات خزينة لكافة المستلمين بواسطة [نهج الأمان المعين مسبقا **للحماية المضمنة**](preset-security-policies.md).
>
> يشير العمود **الافتراضي في العمود المخصص** إلى القيم الافتراضية في نهج المرفقات خزينة الجديدة التي تقوم بإنشائها. تشير الأعمدة المتبقية (ما لم تتم الإشارة إلى خلاف ذلك) إلى القيم التي تم تكوينها في نهج الأمان المعينة مسبقا المقابلة.

|اسم ميزة الأمان|الافتراضي في مخصص|الحماية المضمنة|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|:---:|---|
|**استجابة برامج ضارة غير معروفة خزينة المرفقات** <br/><br/> _التمكين_ _والإجراء_|**قباله** <br/><br/> `-Enable $false` و `-Action Block`|**حظر** <br/><br/> `-Enable $true` و `-Action Block`|**حظر** <br/><br/> `-Enable $true` و `-Action Block`|**حظر** <br/><br/> `-Enable $true` و `-Action Block`|عندما تكون المعلمة _Enable_ $false، لا يهم قيمة معلمة _الإجراء_ .|
|**نهج العزل** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy| <br/><br/> تستخدم نهج الأمان القياسية والضيقة المحددة مسبقا نهج العزل الافتراضي (AdminOnlyAccessPolicy مع عدم وجود إعلامات عزل) كما هو موضح في الجدول [هنا](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br/><br/> عند إنشاء نهج مرفقات خزينة جديد، تعني القيمة الفارغة أن نهج العزل الافتراضي يستخدم لتحديد القدرات التاريخية للرسائل التي تم عزلها بواسطة مرفقات خزينة (AdminOnlyAccessPolicy بدون إعلامات العزل). <br/><br/> يمكن للمسؤولين إنشاء وتحديد نهج العزل المخصصة التي تحدد المزيد من القدرات للمستخدمين. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).|
|**إعادة توجيه المرفق مع المرفقات المكتشفة** : **تمكين إعادة التوجيه** <br/><br/> _اعاده توجيه_ <br/><br/> _عنوان إعادة التوجيه_|غير محدد ولم يتم تحديد عنوان بريد إلكتروني. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ فارغ (`$null`)|غير محدد ولم يتم تحديد عنوان بريد إلكتروني. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ فارغ (`$null`)|تحديد عنوان بريد إلكتروني وتحديده. <br/><br/> `$true` <br/><br/> عنوان بريد إلكتروني|تحديد عنوان بريد إلكتروني وتحديده. <br/><br/> `$true` <br/><br/> عنوان بريد إلكتروني|إعادة توجيه الرسائل إلى مسؤول أمان للمراجعة. <br/><br/> **ملاحظة**: لم يتم تكوين هذا الإعداد في نهج الأمان **القياسية** أو **الصارمة** أو **المضمنة المعينة** مسبقا. تشير القيم **القياسية** **والضيقة** إلى قيمنا **الموصى بها** في نهج المرفقات خزينة الجديدة التي تقوم بإنشائها.|
|**تطبيق استجابة الكشف عن المرفقات خزينة إذا تعذر إكمال الفحص (مهلة أو أخطاء)** <br/><br/> _ActionOnError_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||

### <a name="safe-links-settings"></a>إعدادات ارتباطات خزينة

تتضمن خزينة الارتباطات في Defender لـ Office 365 إعدادات عمومية تنطبق على كافة المستخدمين المضمنين في نهج الارتباطات خزينة النشطة والإعدادات الخاصة بكل نهج ارتباطات خزينة. لمزيد من المعلومات، راجع [الارتباطات خزينة في Defender لـ Office 365](safe-links.md).

على الرغم من عدم وجود نهج ارتباطات خزينة افتراضي، يوفر نهج الأمان المعين مسبقا **للحماية المضمنة** حماية خزينة الارتباطات لكافة المستلمين (المستخدمين الذين لم يتم تعريفهم في نهج الارتباطات خزينة المخصصة). لمزيد من المعلومات، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>الإعدادات العمومية لاارتباطات خزينة

> [!NOTE]
> يتم تعيين الإعدادات العمومية للارتباطات خزينة بواسطة نهج الأمان المعين مسبقا **للحماية المضمنة**، ولكن ليس من خلال نهج الأمان **القياسية** أو **الصارمة** المعينة مسبقا. وفي كلتا الحالتين، يمكن للمسؤولين تعديل إعدادات ارتباطات خزينة العمومية هذه في أي وقت.
>
> يعرض العمود **الافتراضي** القيم قبل وجود نهج الأمان المعين مسبقا **للحماية المضمنة** . يعرض عمود **الحماية المضمن** القيم التي تم تعيينها بواسطة نهج الأمان المعين مسبقا **للحماية المضمنة** ، والتي هي أيضا قيمنا الموصى بها.

لتكوين هذه الإعدادات، راجع [تكوين الإعدادات العمومية للارتباطات خزينة في Defender لـ Office 365](configure-global-settings-for-safe-links.md).

في PowerShell، يمكنك استخدام [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) cmdlet لهذه الإعدادات.

|اسم ميزة الأمان|افتراضي|الحماية المضمنة|التعليق|
|---|:---:|:---:|---|
|**حظر عناوين URL التالية** <br/><br/> _عناوين Url المستبعدة_|فارغه <br/><br/> `$null`|فارغه <br/><br/> `$null`|ليس لدينا توصية محددة لهذا الإعداد. <br/><br/> لمزيد من المعلومات، راجع [قائمة "حظر عناوين URL التالية" لارتباطات خزينة](safe-links.md#block-the-following-urls-list-for-safe-links).
|**استخدام ارتباطات خزينة في تطبيقات Office 365** <br/><br/> _EnableSafeLinksForO365Clients_|في <br/><br/> `$true`|في <br/><br/> `$true`|استخدم ارتباطات خزينة في تطبيقات Office 365 المدعومة لسطح المكتب والجوال (iOS وAndroid). لمزيد من المعلومات، راجع [إعدادات الارتباطات خزينة لتطبيقات Office 365](safe-links.md#safe-links-settings-for-office-365-apps).|
|**عدم التعقب عندما ينقر المستخدمون فوق الارتباطات المحمية في تطبيقات Office 365** <br/><br/> _TrackClicks_|في <br/><br/> `$false`|قباله <br/><br/> `$true`|يؤدي إيقاف تشغيل هذا الإعداد (تعيين _TrackClicks_ إلى) إلى `$true`تعقب نقرات المستخدم في تطبيقات Office 365 المدعومة.|
|**عدم السماح للمستخدمين بالنقر فوق عنوان URL الأصلي في تطبيقات Office 365** <br/><br/> _AllowClickThrough_|في <br/><br/> `$false`|في <br/><br/> `$false`|يؤدي تشغيل هذا الإعداد (تعيين _AllowClickThrough_ إلى ) إلى `$false`منع النقر إلى عنوان URL الأصلي في تطبيقات Office 365 المدعومة.|

#### <a name="safe-links-policy-settings"></a>إعدادات نهج الارتباطات خزينة

لتكوين هذه الإعدادات، راجع [إعداد نهج الارتباطات خزينة في Microsoft Defender لـ Office 365](set-up-safe-links-policies.md).

في PowerShell، يمكنك استخدام [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) و [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) cmdlets لهذه الإعدادات.

> [!NOTE]
> كما هو موضح سابقا، لا يوجد نهج افتراضي للارتباطات خزينة، ولكن يتم تعيين حماية الارتباطات خزينة لكافة المستلمين بواسطة [نهج الأمان المعين مسبقا **للحماية المضمنة**](preset-security-policies.md).
>
> يشير العمود **الافتراضي في العمود المخصص** إلى القيم الافتراضية في نهج الارتباطات خزينة الجديدة التي تقوم بإنشائها. تشير الأعمدة المتبقية (ما لم تتم الإشارة إلى خلاف ذلك) إلى القيم التي تم تكوينها في نهج الأمان المعينة مسبقا المقابلة.

|اسم ميزة الأمان|الافتراضي في مخصص|الحماية المضمنة|Standard|صارمه|التعليق|
|---|:---:|:---:|:---:|:---:|---|
|**URL & انقر فوق إعدادات الحماية**||||||
|**إجراء على عناوين URL التي يحتمل أن تكون ضارة داخل رسائل البريد الإلكتروني**||||||
|**تشغيل: خزينة تتحقق الارتباطات من قائمة الارتباطات الضارة المعروفة عندما ينقر المستخدمون فوق الارتباطات في البريد الإلكتروني** <br/><br/> _EnableSafeLinksForEmail_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**تطبيق ارتباطات خزينة على رسائل البريد الإلكتروني المرسلة داخل المؤسسة** <br/><br/> _EnableForInternalSenders_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**تطبيق فحص URL في الوقت الحقيقي للارتباطات والارتباطات المشبوهة التي تشير إلى الملفات** <br/><br/> _فحوصات ضوئية_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**انتظر حتى يكتمل مسح URL قبل تسليم الرسالة** <br/><br/> _DeliverMessageAfterScan_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**لا تقم بإعادة كتابة عناوين URL، بل قم بالتحقق عبر واجهة برمجة تطبيقات الارتباطات خزينة فقط** <br/><br/> _DisableURLRewrite_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**عدم إعادة كتابة عناوين URL التالية في البريد الإلكتروني** <br/><br/> _عناوين Url DoNotRewrite_|غير محدد <br/><br/> فارغه|غير محدد <br/><br/> فارغه|غير محدد <br/><br/> فارغه|غير محدد <br/><br/> فارغه|ليس لدينا توصية محددة لهذا الإعداد. لمزيد من المعلومات، راجع [قوائم "عدم إعادة كتابة عناوين URL التالية" في نهج الارتباطات خزينة](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**إجراء لعناوين URL التي يحتمل أن تكون ضارة في Microsoft Teams**||||||
|**في: خزينة تتحقق الارتباطات من قائمة الارتباطات الضارة المعروفة عندما ينقر المستخدمون فوق الارتباطات في Microsoft Teams** <br/><br/> _EnableSafeLinksForTeams_|غير محدد <br/><br/> `$false`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**انقر فوق إعدادات الحماية**||||||
|**تعقب نقرات المستخدم** <br/><br/> _TrackUserClicks_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`||
|**السماح للمستخدمين بالنقر فوق عنوان URL الأصلي** <br/><br/> _AllowClickThrough_|المحدد <br/><br/> `$true`|المحدد <br/><br/> `$true`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|يؤدي إيقاف تشغيل هذا الإعداد (تعيين _AllowClickThrough_ إلى ) إلى `$false`منع النقر إلى عنوان URL الأصلي.|
|**عرض العلامة التجارية للمؤسسة على صفحات الإعلامات والتحذيرات** <br/><br/> _EnableOrganizationBranding_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|ليس لدينا توصية محددة لهذا الإعداد. <br/><br/> قبل تشغيل هذا الإعداد، تحتاج إلى اتباع الإرشادات الواردة في [تخصيص نسق Microsoft 365 لمؤسستك](../../admin/setup/customize-your-organization-theme.md) لتحميل شعار الشركة.|
|**الاعلام**||||||
|**كيف تريد إعلام المستخدمين؟**|**استخدام نص الإعلام الافتراضي**|**استخدام نص الإعلام الافتراضي**|**استخدام نص الإعلام الافتراضي**|**استخدام نص الإعلام الافتراضي**|ليس لدينا توصية محددة لهذا الإعداد. <br/><br/> يمكنك تحديد **استخدام نص الإعلام المخصص** (_CustomNotificationText_) لإدخال نص إعلام مخصص لاستخدامه. يمكنك أيضا تحديد **"استخدام المترجم من Microsoft" للترجمة التلقائية** (_UseTranslatedNotificationText_) لترجمة نص الإعلام المخصص إلى لغة المستخدم.

## <a name="related-articles"></a>المقالات ذات الصلة

- هل تبحث عن أفضل الممارسات **لقواعد تدفق البريد Exchange (المعروفة أيضا بقواعد النقل**)؟ راجع [أفضل الممارسات لتكوين قواعد تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- يمكن للمسؤولين والمستخدمين إرسال إيجابيات خاطئة (بريد إلكتروني جيد تم وضع علامة عليه على أنه سيئ) وسلبيات خاطئة (مسموح بالبريد الإلكتروني غير صالح) إلى Microsoft للتحليل. لمزيد من المعلومات، راجع [تقارير الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md).

- استخدم هذه الارتباطات للحصول على معلومات حول كيفية **إعداد** [خدمة EOP](/exchange/standalone-eop/set-up-your-eop-service) **وتكوين** [Microsoft Defender لـ Office 365](defender-for-office-365.md). لا تنس التوجيهات المفيدة في "[الحماية من التهديدات في Office 365](protect-against-threats.md)".

- يمكن العثور على **أساسيات الأمان Windows** هنا: [أين يمكنني الحصول على خطوط أساس الأمان؟](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) لخيارات عنصر نهج المجموعة/المحلي، [واستخدام خطوط أساس الأمان لتكوين أجهزة Windows في Intune](/intune/protect/security-baselines) للأمان المستند إلى Intune. وأخيرا، تتوفر مقارنة بين أساسات الأمان Microsoft Defender لنقطة النهاية Microsoft Intune في [مقارنة Microsoft Defender لنقطة النهاية وأساسيات أمان Intune Windows](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
