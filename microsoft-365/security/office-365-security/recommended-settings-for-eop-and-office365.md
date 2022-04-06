---
title: توصيات Microsoft لإعدادات أمان EOP Defender لـ Office 365 EOP
keywords: Office 365 الأمان، إطار نهج المرسل، الإبلاغ عن الرسائل والمطابقة المستندة إلى المجال، البريد المعرف لمجالات المفاتيح، الخطوات، كيفية عمله، خطوط الأمان الأساسية، خطوط الأساس ل EOP، الأساسات ل Defender لـ Office 365 ، إعداد Defender لـ Office 365 ، إعداد EOP ، تكوين Defender لـ Office 365 تكوين EOP وتكوين الأمان
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
description: ما هي أفضل الممارسات Exchange Online Protection (EOP) Defender لـ Office 365 الأمان؟ ما هي التوصيات الحالية للحماية القياسية؟ ما الذي يجب استخدامه إذا كنت تريد أن تكون أكثر صرامة؟ وما هي ميزاتك الإضافية التي تحصل عليها إذا كنت تستخدم أيضا Defender لـ Office 365؟
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b4b6c9df3b8c458aaf548ff9c8cfe8cc51fa5824
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507154"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>الإعدادات المستحسنة ل EOP Microsoft Defender لـ Office 365 الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** هو جوهر الأمان لاشتراكات Microsoft 365 ويساعد على منع رسائل البريد الإلكتروني الضارة من الوصول إلى علبة الوارد الخاصة بالموظف. ولكن مع ظهور هجمات جديدة أكثر تعقيدا كل يوم، غالبا ما تكون الحماية المحسنة مطلوبة. **Microsoft Defender لـ Office 365** الخطة 1 أو الخطة 2 على ميزات إضافية تمنح المسؤولين المزيد من طبقات الأمان والتحكم والتحري.

على الرغم من أننا نعمل على تمكين مسؤولي الأمان من تخصيص إعدادات الأمان الخاصة بهم، إلا أن هناك مستويين من مستويات الأمان في EOP Microsoft Defender لـ Office 365 نوصي باستخدامهما: **قياسي** **وصارم**. على الرغم من أن بيئات العملاء واحتياجاتهم مختلفة، ستساعد مستويات التصفية هذه على منع وصول البريد غير المرغوب فيه إلى علبة الوارد الخاصة بالموظفين في معظم الحالات.

لتطبيق الإعدادات القياسية أو الصارم تلقائيا على المستخدمين، راجع تعيين سياسات الأمان مسبقا في [EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

تصف هذه المقالة الإعدادات الافتراضية، وأيضا الإعدادات القياسية والمتقيدة الموصى بها للمساعدة في حماية المستخدمين. تحتوي الجداول على الإعدادات في مدخل Microsoft 365 Defender و PowerShell (Exchange Online PowerShell أو powerShell Exchange Online Protection مستقلة ل PowerShell ل المؤسسات التي لا Exchange Online علب بريدها).

> [!TIP]
> لا يمكنك تغيير الإعدادات القياسية والتقيدية الموصى بها في Microsoft 365 Defender المدخل. لتغيير القيم الموصى بها مثل **تمكين المستخدمين من الحماية**، ستحتاج إلى استخدام Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
>
> يمكن Office 365 وحدة تحليل التكوين الموصى بها للحماية المتقدمة من المخاطر (ORCA) ل PowerShell مساعدتك (المسؤولين) في العثور على القيم الحالية لهذه الإعدادات. وبشكل خاص، ينشئ **الأمر Cmdlet Get-ORCAReport** تقييما لإعدادات مكافحة البريد العشوائي والتصيد الاحتيالي وغير ذلك من إعدادات الرسائل. يمكنك تنزيل الوحدة النمطية ORCA في <https://www.powershellgallery.com/packages/ORCA/>.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>الحماية من البريد العشوائي والبرامج الضارة والحماية من التصيد الاحتيالي في EOP

إن مكافحة البريد العشوائي، و مكافحة البرامج الضارة، و مكافحة التصيد الاحتيالي هي ميزات EOP التي يمكن تكوينها من قبل المسؤولين. نوصي بإجراء التكوينات القياسية أو الصارم التالية.

### <a name="eop-anti-spam-policy-settings"></a>إعدادات نهج مكافحة البريد العشوائي ل EOP

لإنشاء سياسات مكافحة البريد العشوائي وتكوينها، راجع تكوين سياسات مكافحة البريد العشوائي [في EOP](configure-your-spam-filter-policies.md).

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**حد البريد الإلكتروني المجمع & البريد العشوائي**|||||
|**حد البريد الإلكتروني المجمع** <br/><br/> _BulkThreshold_|7|6|4|للحصول على التفاصيل، راجع مستوى الشكوى [المجمعة (BCL) في EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|يتوفر هذا الإعداد فقط في PowerShell.|
|**زيادة إعدادات نقاط البريد** العشوائي|إيقاف التشغيل|إيقاف التشغيل|إيقاف التشغيل|كل هذه الإعدادات هي جزء من تصفية البريد العشوائي المتقدمة (ASF). لمزيد من المعلومات، راجع القسم [إعدادات ASF في سياسات](#asf-settings-in-anti-spam-policies) مكافحة البريد العشوائي في هذه المقالة.|
|**وضع علامة على إعدادات البريد** العشوائي|إيقاف التشغيل|إيقاف التشغيل|إيقاف التشغيل|معظم هذه الإعدادات هي جزء من ASF. لمزيد من المعلومات، راجع القسم [إعدادات ASF في سياسات](#asf-settings-in-anti-spam-policies) مكافحة البريد العشوائي في هذه المقالة.|
|**يحتوي على لغات معينة** <br/><br/> _EnableLanguageBlockList_ <br/><br/> _LanguageBlockList_|**إيقاف التشغيل** <br/><br/> `$false` <br/><br/> فارغ|**إيقاف التشغيل** <br/><br/> `$false` <br/><br/> فارغ|**إيقاف التشغيل** <br/><br/> `$false` <br/><br/> فارغ|ليس لدينا توصيات محددة لهذا الإعداد. يمكنك حظر الرسائل بلغات معينة استنادا إلى احتياجات عملك.|
|**من هذه البلدان** <br/><br/> _EnableRegionBlockList_ <br/><br/> _RegionBlockList_|**إيقاف التشغيل** <br/><br/> `$false` <br/><br/> فارغ|**إيقاف التشغيل** <br/><br/> `$false` <br/><br/> فارغ|**إيقاف التشغيل** <br/><br/> `$false` <br/><br/> فارغ|ليس لدينا توصيات محددة لهذا الإعداد. يمكنك حظر الرسائل الواردة من بلدان معينة استنادا إلى احتياجات أعمالك.|
|**وضع الاختبار** (_TestModeAction_)|**بلا**|**بلا**|**بلا**|هذا الإعداد هو جزء من ASF. لمزيد من المعلومات، راجع القسم [إعدادات ASF في سياسات](#asf-settings-in-anti-spam-policies) مكافحة البريد العشوائي في هذه المقالة.|
|**الإجراءات**||||أينما حددت رسالة **الفحص،** يتوفر **مربع** تحديد نهج الفحص. تحدد سياسات الفحص ما يسمح للمستخدمين به للرسائل المعزولة. <br/><br/> عند إنشاء نهج جديد لمكافحة البريد العشوائي، تعني القيمة الفارغة استخدام نهج الفحص الافتراضي لتعريف القدرات التاريخية للرسائل التي تم فحصها بواسطة هذا القرار (AdminOnlyAccessPolicy **لتصيد** احتيالي عالي الثقة؛ DefaultFullAccessPolicy لكل شيء آخر). <br/><br/> يمكن للمسؤولين إنشاء وتحديد سياسات الفحص المخصصة التي تحدد قدرات أكثر تقييدا أو أقل تقييدا للمستخدمين. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).|
|**إجراء الكشف** عن البريد العشوائي <br/><br/> _SpamAction_|**نقل رسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**نقل رسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**رسالة الفحص** <br/><br/> `Quarantine`||
|**إجراء الكشف عن البريد العشوائي** عالي الثقة <br/><br/> _HighConfidenceSpamAction_|**رسالة الفحص** <br/><br/> `MoveToJmf`|**رسالة الفحص** <br/><br/> `Quarantine`|**رسالة الفحص** <br/><br/> `Quarantine`||
|**إجراء الكشف عن** التصيد الاحتيالي <br/><br/> _PhishSpamAction_|**رسالة الفحص** <br/><br/> `MoveToJmf`|**رسالة الفحص** <br/><br/> `Quarantine`|**رسالة الفحص** <br/><br/> `Quarantine`||
|**إجراء الكشف عن التصيد الاحتيالي** عالي الثقة <br/><br/> _HighConfidencePhishAction_|**رسالة الفحص** <br/><br/> `Quarantine`|**رسالة الفحص** <br/><br/> `Quarantine`|**رسالة الفحص** <br/><br/> `Quarantine`||
|**إجراء** الكشف المجمع <br/><br/> _BulkSpamAction_|**نقل رسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**نقل رسالة إلى مجلد البريد الإلكتروني غير الهام** <br/><br/> `MoveToJmf`|**رسالة الفحص** <br/><br/> `Quarantine`||
|**الاحتفاظ بالبريد العشوائي في الفحص لعدة أيام** <br/><br/> _QuarantineRetentionPeriod_|15 يوما<sup>\*</sup>|30 يوماً|30 يوماً|<sup>\*</sup> القيمة الافتراضية هي 15 يوما في نهج مكافحة البريد العشوائي الافتراضي، وفي نهج مكافحة البريد العشوائي الجديدة التي تقوم بإنشاءها في PowerShell. القيمة الافتراضية هي 30 يوما في سياسات مكافحة البريد العشوائي الجديدة التي تقوم Microsoft 365 Defender الإلكتروني. <br/><br/> تؤثر هذه القيمة أيضا على الرسائل التي تم فحصها بواسطة سياسات مكافحة التصيد الاحتيالي. لمزيد من المعلومات، راجع [رسائل البريد الإلكتروني المعزولة في EOP](quarantine-email-messages.md).|
|**تمكين تلميحات أمان البريد العشوائي** <br/><br/> _InlineSafetyTipsEnabled_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|تمكين إزالة تلقائية لمدة ساعة (ZAP) لرسائل التصيد الاحتيالي <br/><br/> _PhishZapEnabled_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|تمكين ZAP لرسائل البريد العشوائي <br/><br/> _SpamZapEnabled_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**السماح & الحظر**|||||
|المرسلون المسموح لهم <br/><br/> _AllowedSenders_|بلا|بلا|بلا||
|مجالات المرسل المسموح بها <br/><br/> _AllowedSenderDomains_|بلا|بلا|بلا|تعد إضافة مجالات إلى قائمة المرسلين المسموح بها فكرة سيئة للغاية. يمكن للمهاجمين إرسال بريد إلكتروني إليك تمت تصفيته بخلاف ذلك. <br/><br/> استخدم المعلومات [](learn-about-spoof-intelligence.md) الاستخبارية المنتحلة وقائمة الحظر[/](tenant-allow-block-list.md)السماح بالمستأجر لمراجعة كل المرسلين الذين ينتحلون عناوين البريد الإلكتروني للمرسلين في مجالات البريد الإلكتروني في مؤسستك أو ينتحلون عناوين البريد الإلكتروني للمرسلين في المجالات الخارجية.|
|المرسلون المحظورون <br/><br/> _BlockedSenders_|بلا|بلا|بلا||
|مجالات المرسلين المحظورين <br/><br/> _BlockedSenderDomains_|بلا|بلا|بلا||

#### <a name="asf-settings-in-anti-spam-policies"></a>إعدادات ASF في سياسات مكافحة البريد العشوائي

يصف الجدول في هذا القسم إعدادات تصفية البريد العشوائي المتقدمة (ASF) المتوفرة في سياسات مكافحة البريد العشوائي. كل هذه الإعدادات م إيقاف **التشغيل** لكل من **المستويات** **القياسية والتقيدية** . لمزيد من المعلومات حول إعدادات ASF، راجع إعدادات تصفية البريد العشوائي المتقدمة [(ASF) في EOP](advanced-spam-filtering-asf-options.md).

|اسم ميزة الأمان|تعليق|
|---|---|
|**ارتباطات الصور إلى المواقع البعيدة** (_IncreaseScoreWithImageLinks_)||
|**عنوان IP رقمي في URL** (_IncreaseScoreWithNumericIps_)||
|**إعادة توجيه URL إلى منفذ آخر** (_IncreaseScoreWithRedirectToOtherPort_)||
|**ارتباطات إلى مواقع ويب .biz أو .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**الرسائل الفارغة** (_MarkAsSpamEmptyMessages_)||
|**تضمين العلامات في HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript أو VBScript في HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**علامات النموذج في HTML** (_MarkAsSpamFormTagsInHtml_)||
|**علامات الإطار أو iframe في HTML** (_MarkAsSpamFramesInHtml_)||
|**أخطاء الويب في HTML** (_MarkAsSpamWebBugsInHtml_)||
|**علامات الكائنات في HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**الكلمات الحساسة** (_MarkAsSpamSensitiveWordList_)||
|**سجل SPF: فشل صعب** (_MarkAsSpamSpfRecordHardFail_)||
|**فشل تصفية "لمعروف المرسل"** (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**وضع الاختبار** (_TestModeAction_)|بالنسبة لإعدادات ASF التي تدعم **"** الاختبار" ك إجراء، يمكنك تكوين إجراء وضع الاختبار إلى **بلا**، أو إضافة نص **X-Header** افتراضي، أو **إرسال** رسالة "مفبركة" (`None``AddXHeader`أو ، أو ).`BccMessage` لمزيد من المعلومات، راجع [تمكين إعدادات ASF أو تعطيلها أو اختبارها](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>إعدادات نهج البريد العشوائي الصادر من EOP

لإنشاء سياسات البريد العشوائي الصادر وتكوينها، راجع تكوين تصفية البريد العشوائي الصادر [في EOP](configure-the-outbound-spam-policy.md).

لمزيد من المعلومات حول حدود الإرسال الافتراضية في الخدمة، راجع [حدود الإرسال](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> لا تكون سياسات البريد العشوائي الصادر جزءا من سياسات الأمان القياسية أو تقيد الإعداد المسبق. تشير **القيم القياسية** **والتقيدية** إلى قيمنا **الموصى** بها في نهج البريد العشوائي الصادر الافتراضي أو النهج المخصصة التي تنشئها.

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**تعيين حد للرسالة الخارجية** <br/><br/> _RecipientLimitExternalPerHour_|0|500|400|تعني القيمة الافتراضية 0 استخدام الإعدادات الافتراضية للخدمة.|
|**تعيين حد داخلي للرسالة** <br/><br/> _RecipientLimitInternalPerHour_|0|1000|800|تعني القيمة الافتراضية 0 استخدام الإعدادات الافتراضية للخدمة.|
|**تعيين حد يومي للرسالة** <br/><br/> _RecipientLimitPerDay_|0|1000|800|تعني القيمة الافتراضية 0 استخدام الإعدادات الافتراضية للخدمة.|
|**القيود الموضوعة على المستخدمين الذين يصلون إلى الحد الأقصى للرسالة** <br/><br/> _ActionWhenThresholdReached_|**تقييد المستخدم من إرسال البريد حتى اليوم التالي** <br/><br/> `BlockUserForToday`|**تقييد المستخدم من إرسال البريد** <br/><br/> `BlockUser`|**تقييد المستخدم من إرسال البريد** <br/><br/> `BlockUser`||
|**قواعد إعادة توجيه تلقائية** <br/><br/> _AutoForwardingMode_|**تلقائي - يتم التحكم في النظام** <br/><br/> `Automatic`|**تلقائي - يتم التحكم في النظام** <br/><br/> `Automatic`|**تلقائي - يتم التحكم في النظام** <br/><br/> `Automatic`|
|**إرسال نسخة من الرسائل الصادرة التي تتجاوز هذه الحدود لهؤلاء المستخدمين والمجموعات** <br/><br/> _BccSuspiciousOutboundMail_ <br/><br/> _BccSuspiciousOutboundAdditionalRecipients_|غير محدد <br/><br/> `$false` <br/><br/> فارغ|غير محدد <br/><br/> `$false` <br/><br/> فارغ|غير محدد <br/><br/> `$false` <br/><br/> فارغ|ليس لدينا توصيات محددة لهذا الإعداد. <br/><br/> يعمل هذا الإعداد فقط في نهج البريد العشوائي الصادر الافتراضي. ولا يعمل في سياسات البريد العشوائي الصادر المخصصة التي تقوم بإنشاءها.|
|**إعلام المستخدمين والمجموعات إذا تم حظر مرسل بسبب إرسال بريد عشوائي إلى الخارج** <br/><br/> _NotifyOutboundSpam_ <br/><br/> _NotifyOutboundSpamRecipients_|غير محدد <br/><br/> `$false` <br/><br/> فارغ|غير محدد <br/><br/> `$false` <br/><br/> فارغ|غير محدد <br/><br/> `$false` <br/><br/> فارغ|يرسل نهج [](../../compliance/alert-policies.md) التنبيه الافتراضي المسمى المستخدم المحظور من إرسال البريد الإلكتروني بالفعل إعلامات بالبريد الإلكتروني إلى أعضاء مجموعة **TenantAdmins** **(** المسؤولون العامون) عند حظر المستخدمين بسبب تجاوز الحدود في النهج. نوصي بشدة باستخدام نهج التنبيه بدلا من هذا الإعداد في نهج البريد العشوائي الصادر لإعلام **المسؤولين والمستخدمين الآخرين**. للحصول على الإرشادات، راجع [التحقق من إعدادات التنبيه للمستخدمين المقيدين](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>إعدادات نهج مكافحة البرامج الضارة في EOP

لإنشاء سياسات مكافحة البرامج الضارة وتكوينها، راجع تكوين سياسات مكافحة البرامج الضارة [في EOP](configure-anti-malware-policies.md).

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**إعدادات الحماية**|||||
|**تمكين عامل تصفية المرفقات الشائع** <br/><br/> _EnableFileFilter_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|يفحص هذا الإعداد الرسائل التي تحتوي على مرفقات قابلة للتنفيذ استنادا إلى نوع الملف، بغض النظر عن محتوى المرفق.|
|**تمكين الازدحام التلقائي للبرامج الضارة بدون ساعة** <br/><br/> _ZapEnabled_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**نهج الفحص**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|عند إنشاء نهج جديد لمكافحة البرامج الضارة، تعني القيمة الفارغة استخدام نهج الفحص الافتراضي لتعريف القدرات التاريخية للرسائل التي تم فحصها كبرامج ضارة (AdminOnlyAccessPolicy). <br/><br/> يمكن للمسؤولين إنشاء وتحديد سياسات الفحص المخصصة التي تحدد المزيد من القدرات للمستخدمين. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).|
|**إعلامات المستلمين**|||||
|**إعلام المستلمين عند فحص الرسائل كبرامج ضارة** <br/><br/> _الإجراء_|غير محدد <br/><br/> _DeleteMessage_|غير محدد <br/><br/> _DeleteMessage_|غير محدد <br/><br/> _DeleteMessage_|إذا تم اكتشاف البرامج الضارة في مرفق بريد إلكتروني، يتم فحص الرسالة ويمكن إصدارها من قبل المسؤول فقط.|
|**إعلامات المرسل**|||||
|**إعلام المرسلين الداخليين عند فحص الرسائل كبرامج ضارة** <br/><br/> _EnableInternalSenderNotifications_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**إعلام المرسلين الخارجيين عند فحص الرسائل كبرامج ضارة** <br/><br/> _EnableExternalSenderNotifications_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**إعلامات المسؤول**|||||
|**إعلام مسؤول بالرسائل التي لم يتم إرسالها من مرسلين داخليين** <br/><br/> _EnableInternalSenderAdminNotifications_ <br/><br/> _InternalSenderAdminAddress_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|ليس لدينا توصيات محددة لهذا الإعداد.|
|**إعلام مسؤول بالرسائل غير المرسلة من مرسلين خارجيين** <br/><br/> _EnableExternalSenderAdminNotifications_ <br/><br/> _ExternalSenderAdminAddress_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|ليس لدينا توصيات محددة لهذا الإعداد.|
|**تخصيص الإعلامات**||||لا توجد لدينا توصيات محددة لهذه الإعدادات.|
|**استخدام نص إعلام مخصص** <br/><br/> _CustomNotifications_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**من الاسم** <br/><br/> _CustomFromName_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`||
|**من العنوان** <br/><br/> _CustomFromAddress_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`||
|**تخصيص الإعلامات للرسائل الواردة من المرسلين الداخليين**||||يتم استخدام هذه الإعدادات فقط إذا  تم تحديد إعلام المرسلين الداخليين عند فحص الرسائل كبرامج ضارة أو إعلام المسؤول بالرسائل التي لم يتم إرسالها من مرسلين داخليين.|
|**الموضوع** <br/><br/> _CustomInternalSubject_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`||
|**رسالة** <br/><br/> _CustomInternalBody_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`||
|**تخصيص الإعلامات للرسائل الواردة من مرسلين خارجيين**||||يتم استخدام هذه الإعدادات فقط إذا  تم تحديد إعلام المرسلين الخارجيين عند فحص الرسائل كبرامج ضارة أو إعلام المسؤول بالرسائل التي لم يتم إرسالها من مرسلين خارجيين.|
|**الموضوع** <br/><br/> _CustomExternalSubject_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`||
|**رسالة** <br/><br/> _CustomExternalBody_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>إعدادات نهج مكافحة التصيد الاحتيالي ل EOP

للحصول على مزيد من المعلومات حول هذه الإعدادات، راجع [إعدادات التهزاء](set-up-anti-phishing-policies.md#spoof-settings). لتكوين هذه الإعدادات، راجع تكوين سياسات مكافحة التصيد الاحتيالي [في EOP](configure-anti-phishing-policies-eop.md).

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**حد التصيد الاحتيالي & الحماية**|||||
|**تمكين المعلومات المنتحلة** <br/><br/> _EnableSpoofIntelligence_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**الإجراءات**|||||
|**إذا تم الكشف عن الرسالة على أنها منتحلة** <br/><br/> _AuthenticationFailAction_|**نقل رسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**نقل رسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**عزل الرسالة** <br/><br/> `Quarantine`|ينطبق هذا الإعداد على المرسلين المنتحلين الذين تم حظرهم تلقائيا كما هو موضح في معلومات المعلومات [](learn-about-spoof-intelligence.md) المنتحلة أو تم حظرهم يدويا في قائمة السماح[/](tenant-allow-block-list.md)الحظر للمستأجر. <br/><br/> إذا حددت **عزل** الرسالة، يتوفر مربع نهج  تطبيق الفحص لتحديد نهج الفحص الذي يعرف ما يسمح للمستخدمين به للرسائل التي تم فحصها على أنها انتحال. عند إنشاء نهج جديد لمكافحة التصيد الاحتيالي، تعني القيمة الفارغة استخدام نهج الفحص الافتراضي لتعريف الإمكانات التاريخية للرسائل التي تم فحصها على أنها خادعة (DefaultFullAccessPolicy). <br/><br/> يمكن للمسؤولين إنشاء وتحديد سياسات الفحص المخصصة التي تحدد قدرات أكثر تقييدا أو أقل تقييدا للمستخدمين. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).|
|**إظهار جهات الاتصال تلميح الأمان** <br/><br/> _EnableFirstContactSafetyTips_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|لمزيد من المعلومات، راجع [الاتصال تلميح الأمان](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**إظهار (?) للمرسلين الذين لم يتم اظهارهم للانتحال** <br/><br/> _EnableUnauthenticatedSender_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|إضافة علامة استفهام (؟) إلى صورة المرسل في Outlook لمرسلين منتحلين غير مجهولين. لمزيد من المعلومات، راجع [المرسل غير المأكد](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**إظهار علامة "via"** <br/><br/> _EnableViaTag_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|يضيف علامة عبر (chris@contoso.com عبر fabrikam.com) إلى العنوان من إذا كان مختلفا عن المجال في توقيع DKIM أو عنوان **MAIL FROM** . <br/><br/> لمزيد من المعلومات، راجع [المرسل غير المأكد](set-up-anti-phishing-policies.md#unauthenticated-sender).|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender لـ Office 365 الأمان

تأتي مزايا الأمان الإضافية مع Microsoft Defender لـ Office 365 اشتراك. للحصول على أحدث الأخبار والمعلومات، يمكنك الاطلاع على أحدث الأخبار [في](whats-new-in-defender-for-office-365.md) Defender لـ Office 365.

> [!IMPORTANT]
>
> - يوفر نهج مكافحة التصيد الاحتيالي الافتراضي في Microsoft Defender لـ Office 365 الحماية المنتحلة وذكاء علبة البريد لجميع المستلمين.[](set-up-anti-phishing-policies.md#spoof-settings) ومع ذلك، لا يتم [](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) تكوين ميزات حماية انتحال أخرى [](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) متوفرة وإعدادات متقدمة أو تمكينها في النهج الافتراضي. لتمكين جميع ميزات الحماية، قم بتعديل نهج مكافحة التصيد الاحتيالي الافتراضي أو قم بإنشاء نهج إضافية لمكافحة التصيد الاحتيالي.
>
> - على الرغم من عدم وجود نهج افتراضي لمرفقات خزينة أو نهج ارتباطات خزينة، فإن نهج الأمان المضمن للحماية المسبقة يوفر حماية المرفقات خزينة وحماية ارتباطات خزينة لكل المستلمين (المستخدمون غير المحددين في نهج مرفقات خزينة المخصصة أو نهج ارتباطات خزينة). لمزيد من المعلومات، راجع [إعدادات مسبقة لنهج الأمان في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).
>
> - [خزينة](mdo-for-spo-odb-and-teams.md) المرفقات SharePoint OneDrive والحماية Microsoft Teams المستندات والحماية خزينة لها تبعيات على خزينة الارتباطات.[](safe-docs.md)

إذا كان اشتراكك Microsoft Defender لـ Office 365 أو إذا قمت بشراء Defender لـ Office 365 الإضافية، فحدد التكوينات القياسية أو تقيد التالية.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>إعدادات نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365

يحصل عملاء EOP على معلومات أساسية حول مكافحة التصيد الاحتيالي كما هو موضح مسبقا، ولكن Defender لـ Office 365 يتضمن المزيد من الميزات والتحكم للمساعدة في منع الهجمات والكشف عنها وضبطها. لإنشاء هذه السياسات وتكوينها، راجع [تكوين سياسات](configure-mdo-anti-phishing-policies.md) مكافحة التصيد الاحتيالي في Defender لـ Office 365.

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>الإعدادات المتقدمة في سياسات مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365

لمزيد من المعلومات حول هذا الإعداد، راجع [حدود](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) التصيد الاحتيالي المتقدمة في سياسات مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365. لتكوين هذا الإعداد، راجع [تكوين سياسات](configure-mdo-anti-phishing-policies.md) مكافحة التصيد الاحتيالي في Defender لـ Office 365.

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**حد البريد الإلكتروني الخاص بالتصيد الاحتيالي** <br/><br/> _PhishThresholdLevel_|**1 - قياسي** <br/><br/> `1`|**2 - مهين** <br/><br/> `2`|**3 - أكثر عناء** <br/><br/> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>إعدادات انتحال في سياسات مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365

لمزيد من المعلومات حول هذه الإعدادات، راجع إعدادات انتحال الشخصية في [سياسات مكافحة التصيد](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) الاحتيالي في Microsoft Defender لـ Office 365. لتكوين هذه الإعدادات، راجع [تكوين سياسات](configure-mdo-anti-phishing-policies.md) مكافحة التصيد الاحتيالي في Defender لـ Office 365.

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**حد التصيد الاحتيالي & الحماية**|||||
|**تمكين المستخدمين من الحماية** (حماية المستخدمين المنتحلين) <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|غير محدد <br/><br/> `$false` <br/><br/> بلا|محدد <br/><br/> `$true` <br/><br/> \<list of users\>|محدد <br/><br/> `$true` <br/><br/> \<list of users\>|نوصي بإضافة مستخدمين (مرسلي الرسائل) في أدوار أساسية. داخليا، قد يكون المرسلون المحميون مديرك التنفيذي ومديرك المالي وقادة كبار آخرين. خارجيا، يمكن أن يتضمن المرسلون المحميون أعضاء في المجلس أو مجلس الإدارة. <br/><br/> في سياسات الأمان المحددة مسبقا، لا يمكنك تحديد المستخدمين الذين يجب حمايتهم. يجب تعطيل سياسات الأمان المحددة مسبقا واستخدام سياسات مخصصة لمكافحة التصيد الاحتيالي لإضافة مستخدمين إلى أدوار أساسية كما هو مقترح.|
|**تمكين المجالات من الحماية** (حماية المجال المنتحلة)|غير محدد|محدد|محدد||
|**تضمين المجالات التي أملكها** <br/><br/> _EnableOrganizationDomainsProtection_|إيقاف التشغيل <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**تضمين مجالات مخصصة** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|إيقاف التشغيل <br/><br/> `$false` <br/><br/> بلا|محدد <br/><br/> `$true` <br/><br/> \<list of domains\>|محدد <br/><br/> `$true` <br/><br/> \<list of domains\>|نوصي بإضافة مجالات (مجالات المرسلين) التي لا تملكها، ولكنك تتفاعل معها بشكل متكرر. <br/><br/> في سياسات الأمان التي تم تعيينها مسبقا، لا يمكنك تحديد مجالات custm لحمايتها. يجب تعطيل سياسات الأمان المحددة مسبقا واستخدام سياسات مخصصة لمكافحة التصيد الاحتيالي لإضافة مجالات مخصصة لحمايتها كما هو مقترح.|
|**إضافة مرسلين ومجالات موثوق بها** <br/><br/> _ExcludedSenders_ <br/><br/> _ExcludedDomains_|بلا|بلا|بلا|استنادا إلى مؤسستك، نوصي بإضافة المرسلين أو المجالات التي تم تعريفها بشكل غير صحيح كمحاولات انتحال.|
|**تمكين المعلومات الاستخبارية لعلبة البريد** <br/><br/> _EnableMailboxIntelligence_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**تمكين المعلومات الاستخبارية للحماية من انتحال الشخصية** <br/><br/> _EnableMailboxIntelligenceProtection_|إيقاف التشغيل <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|يتيح هذا الإعداد الإجراء المحدد للكشف عن انتحال المعلومات بواسطة معلومات علبة البريد.|
|**الإجراءات**||||أينما حددت **عزل الرسالة،** يتوفر **مربع** تحديد نهج الفحص. تحدد سياسات الفحص ما يسمح للمستخدمين به للرسائل المعزولة. <br/><br/> عند إنشاء نهج جديد لمكافحة التصيد الاحتيالي، تعني القيمة الفارغة استخدام نهج الفحص الافتراضي لتعريف القدرات التاريخية للرسائل التي تم فحصها بواسطة هذا القرار (DefaultFullAccessPolicy لكل أنواع الكشف عن الانتحال). <br/><br/> يمكن للمسؤولين إنشاء وتحديد سياسات الفحص المخصصة التي تحدد قدرات أقل تقييدا أو أكثر تقييدا للمستخدمين. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).|
|**إذا تم اكتشاف الرسالة كمستخدم منتحل** <br/><br/> _TargetedUserProtectionAction_|**عدم تطبيق أي إجراء** <br/><br/> `NoAction`|**عزل الرسالة** <br/><br/> `Quarantine`|**عزل الرسالة** <br/><br/> `Quarantine`|تذكر أن سياسات الأمان التي تم تعيينها مسبقا لا تسمح لك بتحديد المستخدمين الذين يجب حمايتهم، وبالتالي فإن هذا الإعداد لا يقوم بأي شيء في سياسات الأمان التي تم تعيينها مسبقا.|
|**إذا تم اكتشاف الرسالة كمجال منتحل** <br/><br/> _TargetedDomainProtectionAction_|**عدم تطبيق أي إجراء** <br/><br/> `NoAction`|**عزل الرسالة** <br/><br/> `Quarantine`|**عزل الرسالة** <br/><br/> `Quarantine`|تذكر أن سياسات الأمان التي تم تعيينها مسبقا لا تسمح لك بتحديد المجالات المخصصة لحمايتها، وبالتالي يؤثر هذا الإعداد على المجالات التي تملكها فقط، وليس المجالات المخصصة.|
|**إذا كشف الذكاء في علبة البريد عن مستخدم منتحل أو منتحل** <br/><br/> _MailboxIntelligenceProtectionAction_|**عدم تطبيق أي إجراء** <br/><br/> `NoAction`|**نقل رسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**عزل الرسالة** <br/><br/> `Quarantine`||
|**إظهار انتحال تلميح الأمان** <br/><br/> _EnableSimilarUsersSafetyTips_|إيقاف التشغيل <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**إظهار انتحال المجال تلميح الأمان** <br/><br/> _EnableSimilarDomainsSafetyTips_|إيقاف التشغيل <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**إظهار أحرف انتحال المستخدم غير تلميح الأمان** <br/><br/> _EnableUnusualCharactersSafetyTips_|إيقاف التشغيل <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>إعدادات نهج مكافحة التصيد الاحتيالي ل EOP في Microsoft Defender لـ Office 365

هذه هي الإعدادات نفسها المتوفرة في إعدادات نهج مكافحة البريد العشوائي [في EOP](#eop-anti-spam-policy-settings).

تكون الإعدادات المنتحلة مرتبطة، ولكن لا يعتمد إعداد  إظهار جهة تلميح الأمان الأولى على إعدادات الانتحال.

|اسم ميزة الأمان|افتراضي|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|---|
|**حد التصيد الاحتيالي & الحماية**|||||
|**تمكين المعلومات المنتحلة** <br/><br/> _EnableSpoofIntelligence_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**الإجراءات**|||||
|**إذا تم الكشف عن الرسالة على أنها منتحلة** <br/><br/> _AuthenticationFailAction_|**نقل رسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**نقل رسالة إلى مجلدات البريد الإلكتروني غير الهام للمستلمين** <br/><br/> `MoveToJmf`|**عزل الرسالة** <br/><br/> `Quarantine`|ينطبق هذا الإعداد على المرسلين المنتحلين الذين تم حظرهم تلقائيا كما هو موضح في معلومات المعلومات [](learn-about-spoof-intelligence.md) المنتحلة أو تم حظرهم يدويا في قائمة السماح[/](tenant-allow-block-list.md)الحظر للمستأجر. <br/><br/> إذا حددت **عزل** الرسالة، يتوفر مربع نهج  تطبيق الفحص لتحديد نهج الفحص الذي يعرف ما يسمح للمستخدمين به للرسائل المعزولة. عند إنشاء نهج جديد لمكافحة التصيد الاحتيالي، تعني القيمة الفارغة استخدام نهج الفحص الافتراضي لتعريف القدرات التاريخية للرسائل المعزولة (DefaultFullAccessPolicy). <br/><br/> يمكن للمسؤولين إنشاء نهج عزل مخصص وتحديده يحدد ما يسمح للمستلمين القيام به بهذه الرسائل في الفحص. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).|
|**إظهار جهات الاتصال تلميح الأمان** <br/><br/> _EnableFirstContactSafetyTips_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|لمزيد من المعلومات، راجع [الاتصال تلميح الأمان](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**إظهار (?) للمرسلين الذين لم يتم اظهارهم للانتحال** <br/><br/> _EnableUnauthenticatedSender_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|إضافة علامة استفهام (؟) إلى صورة المرسل في Outlook لمرسلين منتحلين غير مجهولين. لمزيد من المعلومات، راجع [المرسل غير المأكد](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**إظهار علامة "via"** <br/><br/> _EnableViaTag_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|يضيف علامة عبر (chris@contoso.com عبر fabrikam.com) إلى العنوان من إذا كان مختلفا عن المجال في توقيع DKIM أو عنوان **MAIL FROM** . <br/><br/> لمزيد من المعلومات، راجع [المرسل غير المأكد](set-up-anti-phishing-policies.md#unauthenticated-sender).|

### <a name="safe-attachments-settings"></a>خزينة المرفقات

خزينة المرفقات في Microsoft Defender لـ Office 365 الإعدادات العامة التي لا تربطها علاقة ونهج مرفقات خزينة، والإعدادات الخاصة بكل نهج خزينة ارتباطات. لمزيد من المعلومات، راجع خزينة [المرفقات في Defender لـ Office 365](safe-attachments.md).

على الرغم من عدم وجود نهج خزينة مرفقات افتراضي، إلا أن نهج الأمان  المضمن للحماية المسبقة يوفر خزينة حماية المرفقات لجميع المستلمين (المستخدمون غير المحددين في نهج مرفقات خزينة المخصصة). لمزيد من المعلومات، راجع [إعدادات مسبقة لنهج الأمان في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>الإعدادات "عام" خزينة المرفقات

> [!NOTE]
> يتم تعيين الإعدادات خزينة المرفقات بواسطة نهج الأمان المضمن للحماية المسبقة، ولكن ليس بواسطة نهج الأمان القياسية أو الصارم.  وفي كلتا  كلتا  الطريقتين، يمكن للمسؤولين تعديل إعدادات المرفقات خزينة في أي وقت.
>
> يعرض **العمود** الافتراضي القيم قبل وجود نهج الأمان المضمن للحماية  المضمنة. يعرض **عمود الحماية المضمنة** القيم التي تم تعيينها بواسطة نهج أمان  الحماية المضمنة، وهي أيضا القيم الموصى بها.

لتكوين هذه الإعدادات، راجع تشغيل خزينة [](turn-on-mdo-for-spo-odb-and-teams.md) للمستندات SharePoint و OneDrive و Microsoft Teams خزينة في [Microsoft 365 E5](safe-docs.md).

في PowerShell، يمكنك استخدام [الأمر Cmdlet Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) لهذه الإعدادات.

|اسم ميزة الأمان|افتراضي|حماية مضمنة|تعليق|
|---|:---:|:---:|---|
|**قم Defender لـ Office 365 SharePoint OneDrive و Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|إيقاف التشغيل <br/><br/> `$false`|في <br/><br/> `$true`|لمنع المستخدمين من تنزيل الملفات الضارة، راجع [استخدام SharePoint Online PowerShell لمنع المستخدمين من تنزيل الملفات الضارة](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**تشغيل خزينة العملاء Office العملاء** <br/><br/> _EnableSafeDocs_|إيقاف التشغيل <br/><br/> `$false`|في <br/><br/> `$true`|تتوفر هذه الميزة وذات معنى فقط مع التراخيص غير المضمنة في Defender لـ Office 365 (على سبيل المثال، Microsoft 365 E5 أو الأمان في Microsoft 365 E5). لمزيد من المعلومات، راجع خزينة [المستندات في Microsoft 365 E5](safe-docs.md).|
|**السماح للأشخاص بالنقر عبر "طريقة عرض محمية" حتى خزينة المستندات تعرف الملف على أنه ضار** <br/><br/> _AllowSafeDocsOpen_|إيقاف التشغيل <br/><br/> `$false`|إيقاف التشغيل <br/><br/> `$false`|يرتبط هذا الإعداد خزينة المستندات.|

#### <a name="safe-attachments-policy-settings"></a>خزينة نهج المرفقات

لتكوين هذه الإعدادات، راجع إعداد خزينة [المرفقات في Defender لـ Office 365](set-up-safe-attachments-policies.md).

في PowerShell، يمكنك استخدام [الأمرين Cmdlets New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) و [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) لهذه الإعدادات.

> [!NOTE]
> كما هو موضح سابقا، لا يوجد نهج خزينة المرفقات، ولكن يتم تعيين خزينة حماية المرفقات لكل المستلمين بواسطة نهج الأمان المعين مسبقا للحماية [ المضمنة](preset-security-policies.md).
>
> يشير **العمود الافتراضي** في العمود المخصص إلى القيم الافتراضية في خزينة المرفقات الجديدة التي تقوم بإنشاءها. تشير الأعمدة المتبقية إلى (ما لم يذكر خلاف ذلك) القيم التي تم تكوينها في سياسات الأمان المقابلة التي تم إعدادها مسبقا.

|اسم ميزة الأمان|الإعداد الافتراضي في المخصص|حماية مضمنة|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|:---:|---|
|**خزينة البرامج الضارة غير المعروفة للمرفقات** <br/><br/> _التمكين_ _والتحرك_|**إيقاف التشغيل** <br/><br/> `-Enable $false` و `-Action Block`|**حظر** <br/><br/> `-Enable $true` و `-Action Block`|**حظر** <br/><br/> `-Enable $true` و `-Action Block`|**حظر** <br/><br/> `-Enable $true` و `-Action Block`|عندما _تكون_ المعلمة Enable $false، لا تهم قيمة معلمة الإجراء.|
|**نهج الفحص** (_Tag)_|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|عندما تنشئ نهج مرفقات خزينة جديد، تعني القيمة الفارغة استخدام نهج الفحص الافتراضي لتعريف القدرات التاريخية للرسائل التي تم فحصها بواسطة مرفقات خزينة (AdminOnlyAccessPolicy). <br/><br/> يمكن للمسؤولين إنشاء وتحديد سياسات الفحص المخصصة التي تحدد المزيد من القدرات للمستخدمين. لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md).|
|**إعادة توجيه المرفقات التي بها مرفقات تم الكشف عنها** : **تمكين إعادة التوجيه** <br/><br/> _إعادة توجيه_ <br/><br/> _RedirectAddress_|غير محدد ولا يوجد عنوان بريد إلكتروني محدد. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress فارغ_ (`$null`)|غير محدد ولا يوجد عنوان بريد إلكتروني محدد. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress فارغ_ (`$null`)|محددة وحدد عنوان بريد إلكتروني. <br/><br/> `$true` <br/><br/> عنوان بريد إلكتروني|محددة وحدد عنوان بريد إلكتروني. <br/><br/> `$true` <br/><br/> عنوان بريد إلكتروني|إعادة توجيه الرسائل إلى مسؤول أمان لمراجعتها. <br/><br/> **ملاحظة**: لم يتم تكوين هذا الإعداد **في سياسات الأمان** القياسية أو الصارم أو المضمنة. تشير **القيم القياسية** **والتقيدية** **إلى** قيمنا الموصى بها في خزينة المرفقات الجديدة التي تقوم بإنشاءها.|
|**تطبيق خزينة الكشف عن المرفقات إذا لم يكن المسح الضوئي مكتملا (2016 أو 2016)** <br/><br/> _ActionOnError_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||

### <a name="safe-links-settings"></a>خزينة الارتباطات

خزينة الارتباطات في Defender لـ Office 365 الإعدادات العامة التي تنطبق على جميع المستخدمين المضمنين في نهج ارتباطات خزينة النشطة والإعدادات الخاصة بكل نهج خزينة ارتباطات. لمزيد من المعلومات، راجع خزينة [الارتباطات في Defender لـ Office 365](safe-links.md).

على الرغم من عدم وجود نهج خزينة ارتباطات افتراضي، إلا أن  نهج الأمان المضمن للحماية المسبقة يوفر حماية ارتباطات خزينة لكل المستلمين (المستخدمون غير المحددين في نهج ارتباطات خزينة المخصصة). لمزيد من المعلومات، راجع [إعدادات مسبقة لنهج الأمان في EOP Microsoft Defender لـ Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>الإعدادات "عام" خزينة الارتباطات

> [!NOTE]
> يتم تعيين الإعدادات العامة خزينة الارتباطات بواسطة نهج الأمان المضمن للحماية  المسبقة، ولكن ليس بواسطة نهج الأمان القياسية أو الصارم.  وفي كلتا  كلتا  الطريقتين، يمكن للمسؤولين تعديل إعدادات الارتباطات خزينة في أي وقت.
>
> يعرض **العمود** الافتراضي القيم قبل وجود نهج الأمان المضمن للحماية  المضمنة. يعرض **عمود الحماية المضمنة** القيم التي تم تعيينها بواسطة نهج أمان  الحماية المضمنة، وهي أيضا القيم الموصى بها.

لتكوين هذه الإعدادات، راجع تكوين الإعدادات خزينة [ارتباطات في Defender لـ Office 365](configure-global-settings-for-safe-links.md).

في PowerShell، يمكنك استخدام [الأمر Cmdlet Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) لهذه الإعدادات.

|اسم ميزة الأمان|افتراضي|حماية مضمنة|تعليق|
|---|:---:|:---:|---|
|**حظر عناوين URL التالية** <br/><br/> _المستثناةUrls_|فارغ <br/><br/> `$null`|فارغ <br/><br/> `$null`|ليس لدينا توصيات محددة لهذا الإعداد. <br/><br/> لمزيد من المعلومات، راجع [القائمة "حظر عناوين URL التالية" خزينة الارتباطات](safe-links.md#block-the-following-urls-list-for-safe-links).
|**استخدام خزينة الارتباطات في Office 365 التطبيق** <br/><br/> _EnableSafeLinksForO365Clients_|في <br/><br/> `$true`|في <br/><br/> `$true`|استخدم خزينة الارتباطات في تطبيقات Office 365 سطح المكتب والأجهزة المحمولة (iOS وAndroid) المعتمدة. لمزيد من المعلومات، [راجع خزينة الارتباطات لتطبيقات Office 365.](safe-links.md#safe-links-settings-for-office-365-apps)|
|**عدم التعقب عندما ينقر المستخدمون فوق الارتباطات المحمية في Office 365 التطبيقات** <br/><br/> _TrackClicks_|في <br/><br/> `$false`|إيقاف التشغيل <br/><br/> `$true`|يؤدي إيقاف تشغيل هذا الإعداد (تعيين _TrackClicks إلى_ `$true`) إلى تعقب نقرات المستخدم في التطبيقات Office 365 المعتمدة.|
|**لا تدع المستخدمين ينقرون عبر عنوان URL الأصلي في Office 365 التطبيقات** <br/><br/> _AllowClickThrough_|في <br/><br/> `$false`|في <br/><br/> `$false`|يؤدي تشغيل هذا الإعداد (تعيين _AllowClickThrough إلى_ `$false`) إلى منع النقر عبر عنوان URL الأصلي في تطبيقات Office 365 المعتمدة.|

#### <a name="safe-links-policy-settings"></a>خزينة نهج الارتباطات

لتكوين هذه الإعدادات، راجع إعداد خزينة [الارتباطات في Microsoft Defender لـ Office 365](set-up-safe-links-policies.md).

في PowerShell، يمكنك استخدام [الأمرين Cmdlets New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) و [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) لهذه الإعدادات.

> [!NOTE]
> كما هو موضح مسبقا، لا يوجد نهج خزينة ارتباطات افتراضية، ولكن يتم تعيين خزينة ارتباطات الحماية لجميع المستلمين بواسطة نهج الأمان المعين مسبقا للحماية [ المضمنة](preset-security-policies.md).
>
> يشير **العمود الافتراضي** في العمود المخصص إلى القيم الافتراضية في خزينة الارتباطات الجديدة التي تقوم بإنشاءها. تشير الأعمدة المتبقية إلى (ما لم يذكر خلاف ذلك) القيم التي تم تكوينها في سياسات الأمان المقابلة التي تم إعدادها مسبقا.

|اسم ميزة الأمان|الإعداد الافتراضي في المخصص|حماية مضمنة|Standard|التقيد|تعليق|
|---|:---:|:---:|:---:|:---:|---|
|**عنوان URL & فوق إعدادات الحماية**||||||
|**إجراء على عناوين URL الضارة المحتملة ضمن رسائل البريد الإلكتروني**||||||
|**في: خزينة التحقق من قائمة الارتباطات المعروفة والضارة عندما ينقر المستخدمون فوق الارتباطات في البريد الإلكتروني** <br/><br/> _EnableSafeLinksForEmail_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**تطبيق خزينة ارتباطات إلى رسائل البريد الإلكتروني المرسلة ضمن المؤسسة** <br/><br/> _EnableForInternalSenders_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**تطبيق مسح URL في الوقت الحقيقي للربطات والربطات المريبة التي تشير إلى الملفات** <br/><br/> _ScanUrls_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**انتظر حتى اكتمال فحص URL قبل تسليم الرسالة** <br/><br/> _DeliverMessageAfterScan_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**عدم إعادة كتابة عناوين URL، إجراء عمليات التحقق عبر خزينة API الارتباطات فقط** <br/><br/> _DisableURLRewrite_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`||
|**عدم إعادة كتابة عناوين URL التالية في البريد الإلكتروني** <br/><br/> _DoNotRewriteUrls_|غير محدد <br/><br/> فارغ|غير محدد <br/><br/> فارغ|غير محدد <br/><br/> فارغ|غير محدد <br/><br/> فارغ|ليس لدينا توصيات محددة لهذا الإعداد. لمزيد من المعلومات، راجع "عدم إعادة كتابة قوائم [عناوين URL التالية" في خزينة الارتباطات.](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)|
|**إجراء عناوين URL التي قد تكون ضارة في Microsoft Teams**||||||
|**في: خزينة الارتباطات على قائمة الارتباطات المعروفة والضارة عندما ينقر المستخدمون فوق الارتباطات في Microsoft Teams** <br/><br/> _EnableSafeLinksForTeams_|غير محدد <br/><br/> `$false`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**انقر فوق إعدادات الحماية**||||||
|**تعقب نقرات المستخدم** <br/><br/> _TrackUserClicks_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`||
|**السماح للمستخدمين بالنقر عبر عنوان URL الأصلي** <br/><br/> _AllowClickThrough_|محدد <br/><br/> `$true`|محدد <br/><br/> `$true`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|يؤدي إيقاف تشغيل هذا الإعداد (تعيين _AllowClickThrough إلى_ `$false`) إلى منع النقر عبر عنوان URL الأصلي.|
|**عرض العلامة التجارية لمنظمتك على صفحات الإعلامات والتحذيرات** <br/><br/> _EnableOrganizationBranding_|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|غير محدد <br/><br/> `$false`|ليس لدينا توصيات محددة لهذا الإعداد. <br/><br/> قبل تشغيل هذا الإعداد، ستحتاج إلى اتباع الإرشادات الواردة في تخصيص Microsoft 365 [](../../admin/setup/customize-your-organization-theme.md) لمنظمتك لتحميل شعار الشركة.|
|**الإعلام**||||||
|**ما الذي ترغب في إعلام المستخدمين به؟**|**استخدام نص الإعلام الافتراضي**|**استخدام نص الإعلام الافتراضي**|**استخدام نص الإعلام الافتراضي**|**استخدام نص الإعلام الافتراضي**|ليس لدينا توصيات محددة لهذا الإعداد. <br/><br/> يمكنك تحديد **استخدام نص إعلام مخصص** (_CustomNotificationText_) لإدخال نص إعلام مخصص لاستخدامه. يمكنك أيضا تحديد **استخدام المترجم من Microsoft الترجمة** التلقائية (_UseTranslatedNotificationText_) لترجمة نص الإعلام المخصص إلى لغة المستخدم.

## <a name="related-articles"></a>المقالات ذات الصلة

- هل تبحث عن أفضل الممارسات Exchange **تدفق البريد الإلكتروني (المعروفة أيضا بقواعد النقل**)؟ راجع [أفضل الممارسات لتكوين قواعد تدفق البريد في Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- يمكن للمسؤولين والمستخدمين إرسال إيجابيات خاطئة (تم وضع علامة سيئة على البريد الإلكتروني الجيد) وسلبيات خاطئة (البريد الإلكتروني غير صالح مسموح به) إلى Microsoft لتحليلها. لمزيد من المعلومات، راجع [الإبلاغ عن الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md).

- استخدم هذه الارتباطات للحصول على معلومات حول كيفية **إعداد** خدمة [EOP](/exchange/standalone-eop/set-up-your-eop-service) وتكوين  [Microsoft Defender لـ Office 365.](defender-for-office-365.md) لا تنس التوجيهات المفيدة في "الحماية من التهديدات [في](protect-against-threats.md) Office 365".

- يمكن العثور على خطوط الأمان الأساسية ل **Windows** هنا: أين يمكنني الحصول على خطوط الأمان الأساسية [؟](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) للحصول على خيارات GPO/في الموقع الداخلي، واستخدام خطوط الأمان الأساسية لتكوين [أجهزة Windows في Intune](/intune/protect/security-baselines) لأمن يستند إلى Intune. وأخيرا، تتوفر مقارنة بين Microsoft Defender لنقطة النهاية Microsoft Intune الأمان الأساسية في مقارنة Microsoft Defender لنقطة النهاية Windows أمان [Intune](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
