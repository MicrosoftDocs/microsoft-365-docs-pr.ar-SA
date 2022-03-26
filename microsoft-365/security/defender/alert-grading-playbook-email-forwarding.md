---
title: تصنيف التنبيهات لنشاط إعادة توجيه البريد الإلكتروني المريب
description: تصنيف التنبيهات لنشاط إعادة توجيه البريد الإلكتروني المريب لمراجعة التنبيهات واتخاذ الإجراءات الموصى بها من أجل معالجة الهجوم وحماية شبكتك.
keywords: الأحداث والتنبيهات، التحقيق، التحليل، الاستجابة، الارتباط، الهجوم، الأجهزة، الأجهزة، المستخدمون، الهويات، الهوية، علبة البريد، البريد الإلكتروني، 365، microsoft، m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 2349fb9ac736653b9a74c42aecf5e71cc95381ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570946"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>تصنيف التنبيهات لنشاط إعادة توجيه البريد الإلكتروني المريب

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن لممثلي التهديدات استخدام حسابات المستخدمين المخادعة لأغراض ضارة متعددة، بما في ذلك قراءة رسائل البريد الإلكتروني في علبة الوارد الخاصة للمستخدم، إعادة توجيه رسائل البريد الإلكتروني إلى مستلمين خارجيين، وإرسال رسائل التصيد الاحتيالي، من بين أمور أخرى. قد يكون المستخدم المستهدف غير على علم بأنه يتم إعادة توجيه رسائل البريد الإلكتروني الخاصة به. هذا أسلوب شائع جدا يستخدمه المهاجمون عند اختراق حسابات المستخدمين.

يمكن إعادة توجيه رسائل البريد الإلكتروني يدويا أو تلقائيا باستخدام قواعد إعادة توجيه. يمكن تنفيذ إعادة توجيه تلقائية بطرق متعددة مثل قواعد علبة الوارد Exchange قاعدة النقل (ETR) وS SMTP Forwarding. في حين أن إعادة توجيه الرسائل يدويا تتطلب إجراء مباشرا من المستخدمين، فقد لا يكونوا على علم بكل رسائل البريد الإلكتروني التي تم إعادة توجيهها بشكل تلقائي. في Microsoft 365، يتم رفع تنبيه عندما يقوم المستخدم إعادة توجيه بريد إلكتروني تلقائيا إلى عنوان بريد إلكتروني يحتمل أن يكون ضارا.

يساعدك هذا المصنف على التحقق من تنبيهات نشاط إعادة توجيه البريد الإلكتروني المريبة ودرجتها بسرعة إما على أنها True Positive (TP) أو False Positive (FP). يمكنك بعد ذلك اتخاذ الإجراءات الموصى بها لتنبيهات TP لإعادة معالجة الهجوم.

للحصول على نظرة عامة حول تصنيف التنبيهات ل Microsoft Defender Office 365 و Microsoft Defender لتطبيقات السحابة، راجع [مقالة المقدمة](alert-grading-playbooks.md).

نتائج استخدام هذا المصنف هي:

- لقد حددت التنبيهات المقترنة ببريد إلكتروني تم إعادة توجيهه بشكل تلقائي كالأنشطة الضارة (TP) أو الأنشطة الضارة (FP).

  إذا كانت ضارة، لقد أوقفت إعادة توجيه البريد [الإلكتروني](../office-365-security/external-email-forwarding.md) التلقائي لعلب البريد المتأثرة.

- لقد اتخذت الإجراء اللازم إذا تم إعادة توجيه رسائل البريد الإلكتروني إلى عنوان بريد إلكتروني ضار.

## <a name="email-forwarding-rules"></a>قواعد إعادة توجيه البريد الإلكتروني

تسمح قواعد إعادة توجيه البريد الإلكتروني للمستخدمين بإنشاء قاعدة إعادة توجيه رسائل البريد الإلكتروني المرسلة إلى علبة بريد مستخدم إلى علبة بريد مستخدم آخر داخل المؤسسة أو خارجها. يقوم بعض مستخدمي البريد الإلكتروني، لا سيما الذين لديهم علب بريد متعددة، بتكوين قواعد إعادة توجيه لنقل رسائل البريد الإلكتروني لصاحب العمل إلى حسابات البريد الإلكتروني الخاصة بهم. إن إعادة توجيه البريد الإلكتروني ميزة مفيدة ولكنها قد تشكل أيضا خطرا على الأمان بسبب إمكانية الكشف عن المعلومات. قد يستخدم المهاجمون هذه المعلومات لمهاجمة مؤسستك أو شركاءها.

### <a name="suspicious-email-forwarding-activity"></a>نشاط إعادة توجيه البريد الإلكتروني المريب

قد يقوم المتطفلون بإعداد قواعد البريد الإلكتروني لإخفاء رسائل البريد الإلكتروني الواردة في علبة بريد المستخدم التي تم اختراقها لحجب أنشطتهم الضارة عن المستخدم. وقد يقوم أيضا بتعيين القواعد في علبة بريد المستخدم التي تم اختراقها لحذف رسائل البريد الإلكتروني أو نقل رسائل البريد الإلكتروني إلى مجلد آخر أقل وضوحا مثل مجلد RSS أو إعادة توجيه رسائل البريد الإلكتروني إلى حساب خارجي.  

قد تؤدي بعض القواعد إلى نقل كل رسائل البريد الإلكتروني إلى مجلد آخر وتمييزها على أنها "قراءة"، بينما قد تحرك بعض القواعد رسائل البريد التي تحتوي على كلمات أساسية معينة فقط في رسالة البريد الإلكتروني أو الموضوع. على سبيل المثال، قد يتم تعيين قاعدة علبة الوارد للبحث عن كلمات أساسية مثل "فاتورة" أو "تصيد احتيالي" أو "عدم الرد" أو "بريد إلكتروني مريب" أو "بريد عشوائي" من بين كلمات أخرى، ثم نقلها إلى حساب بريد إلكتروني خارجي. قد يستخدم المتطفلون أيضا علبة بريد المستخدم التي تم اختراقها لتوزيع البريد العشوائي أو رسائل البريد الإلكتروني التصيد الاحتيالي أو البرامج الضارة.
 
يستطيع Microsoft Defender Office 365 الكشف عن قواعد إعادة توجيه البريد الإلكتروني المريبة وتنبيهها، مما يسمح لك بالكشف عن القواعد المخفية وحذفها في المصدر.

لمزيد من المعلومات، راجع منشورات المدونة هذه:

- [اختراق البريد الإلكتروني للأعمال](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [في كواليس اختراق البريد الإلكتروني للأعمال: استخدام بيانات المخاطر عبر المجالات لتعطيل حملة BEC كبيرة](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)


## <a name="alert-details"></a>تفاصيل التنبيه

لمراجعة تنبيه نشاط إعادة توجيه البريد الإلكتروني المريب، افتح صفحة **التنبيهات** لرؤية **مقطع قائمة** النشاط. فيما يلي مثال على ذلك.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="قائمة الأنشطة المتعلقة بالتنبيه" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

حدد **نشاط**  لعرض تفاصيل هذا النشاط في شريط جانبي. فيما يلي مثال على ذلك.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="تفاصيل النشاط" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

يحتوي **حقل** السبب على المعلومات التالية المتعلقة بهذا التنبيه.

- نوع إعادة توجيه (FT) هو أحد الخطوات التالية:

    -  Exchange النقل (ETR): مع إعادة توجيهها باستخدام Exchange النقل 

    -  SMTP: تم إعادة توجيهه باستخدام "إعادة توجيه علبة البريد"

    -  علبة الوارد: تم إعادة توجيهها باستخدام قاعدة علبة الوارد

- معرف تتبع الرسائل (MTI): هذا هو المعرف (NetworkMessageId) للبريد الإلكتروني الذي تم إعادة توجيهه الذي تم تشغيل هذا التنبيه. إن NetworkMessageId هو المعرف الفريد لبريد إلكتروني في مؤسستك.
- إعادة توجيه (F): المستخدم الذي قام ب إعادة توجيه هذا البريد الإلكتروني.
- قائمة المستلمين المريبة (SRL): قائمة المستلمين المريبين في هذا البريد الإلكتروني.
- قائمة المستلمين (RL): قائمة بكل المستلمين في هذا البريد الإلكتروني.

## <a name="investigation-workflow"></a>سير عمل التحقيق

أثناء التحقق من هذا التنبيه، يجب تحديد:

- هل تم اختراق حساب المستخدم علبة البريد الخاصة به؟
- هل الأنشطة ضارة؟

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>هل تم اختراق حساب المستخدم علبة البريد الخاصة به؟

بالنظر إلى سلوك المرسل السابق والأنشطة الأخيرة، يجب أن تتمكن من تحديد ما إذا كان يجب اعتبار حساب المستخدم م اختراقا أم لا. يمكنك الاطلاع على تفاصيل التنبيهات التي تم رفعها من صفحة المستخدم في Microsoft 365 Defender المدخل. 

يمكنك أيضا تحليل هذه الأنشطة الإضافية لعلبة البريد المتأثرة:

- استخدام "مستكشف التهديدات" لفهم التهديدات المرتبطة بالبريد الإلكتروني

    - لاحظ عدد رسائل البريد الإلكتروني الأخيرة التي أرسلها المرسل على أنها رسائل تصيد احتيالي أو بريد عشوائي أو برامج ضارة.

    - لاحظ عدد رسائل البريد الإلكتروني المرسلة التي تحتوي على معلومات حساسة. 

- تقييم سلوك تسجيل الدخول الخطر في مدخل Microsoft Azure.
- تحقق من وجود أي أنشطة ضارة على جهاز المستخدم.

### <a name="are-the-activities-malicious"></a>هل الأنشطة ضارة؟

تحقق من نشاط إعادة توجيه البريد الإلكتروني. على سبيل المثال، تحقق من نوع البريد الإلكتروني أو مستلم هذا البريد الإلكتروني أو الطريقة التي يتم بها إعادة توجيه البريد الإلكتروني. 

لمزيد من المعلومات، راجع المقالات التالية:

- [نظرة ثاقبة على الرسائل التي تم إعادة توجيهها بشكل تلقائي](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [مستخدمون جدد يراسلون تحليلات البريد الإلكتروني](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [الاستجابة إلى حساب بريد إلكتروني م اختراق](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

إليك سير العمل لتحديد أنشطة إعادة توجيه البريد الإلكتروني المريبة.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="تنبيه سير عمل التحقيق من أجل إعادة توجيه البريد الإلكتروني" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

يمكنك التحقق من تنبيه إعادة توجيه البريد الإلكتروني باستخدام "مستكشف التهديدات" أو استعلامات البحث المتقدمة، استنادا إلى توفر الميزات في مدخل Microsoft 365 Defender الإلكتروني. يمكنك اختيار اتباع العملية بأكملها أو جزء من العملية حسب الحاجة.

## <a name="using-threat-explorer"></a>استخدام "مستكشف التهديدات"

يوفر "مستكشف التهديدات" تجربة تحقيق تفاعلية للتهديدات ذات الصلة بالبريد الإلكتروني لتحديد ما إذا كان هذا النشاط مريبا أم لا. يمكنك استخدام المؤشرات التالية من معلومات التنبيه:

- SRL/RL: استخدم قائمة المستلمين (مريبون) (SRL) للعثور على هذه التفاصيل:
 
    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="مثال لقائمة المستلمين" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

    - روبوت Who آخر إعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين؟

    - كم عدد رسائل البريد الإلكتروني التي تم إعادة توجيهها إلى هؤلاء المستلمين؟

    - ما مدى تكرار إعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين؟
 

- MTI: استخدم "المعرف تتبع الرسائل/شبكة الرسائل" للعثور على هذه التفاصيل:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="مثال لمعر &quot;رسالة الشبكة&quot;" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

    - ما التفاصيل الإضافية المتوفرة لهذا البريد الإلكتروني؟ على سبيل المثال: الموضوع ومسار الإرجاع وال timestamp.

    - ما هو أصل هذا البريد الإلكتروني؟ هل هناك أي رسائل بريد إلكتروني مماثلة؟

    - هل يحتوي هذا البريد الإلكتروني على عناوين URL؟ هل يشير عنوان URL إلى أي بيانات حساسة؟

    - هل يحتوي البريد الإلكتروني على أي مرفقات؟ هل تحتوي المرفقات على معلومات حساسة؟

    - ما الإجراء الذي تم اتخاذه على البريد الإلكتروني؟ هل تم حذفه أو وضع علامة عليه كمقرأ أو تم نقله إلى مجلد آخر؟

    - هل هناك أي تهديدات مقترنة بهذا البريد الإلكتروني؟ هل هذا البريد الإلكتروني جزء من أي حملة؟

استنادا إلى الإجابات على هذه الأسئلة، يجب أن تكون قادرا على تحديد ما إذا كان البريد الإلكتروني ضارا أو غير جيد.

## <a name="advanced-hunting-queries"></a>استعلامات الصيد المتقدمة

لاستخدام [استعلامات "](advanced-hunting-overview.md) البحث المتقدم" لجمع المعلومات المتعلقة بتنبيه وتحديد ما إذا كان النشاط مريبا أم لا، تأكد من إمكانية الوصول إلى الجداول التالية:

- EmailEvents - يحتوي على معلومات ذات صلة بتدفق البريد الإلكتروني.

- EmailUrlInfo - يحتوي على معلومات ذات صلة عناوين URL في رسائل البريد الإلكتروني.

- CloudAppEvents -يحتوي على سجل تدقيق أنشطة المستخدمين.

- IdentityLogonEvents - يحتوي على معلومات تسجيل الدخول لجميع المستخدمين.

>[!Note]
>بعض المعلمات فريدة لمنظمتك أو شبكتك. قم بتعبئة هذه المعلمات المحددة كما هو محدد في كل استعلام.
>

تشغيل هذا الاستعلام لمعرفة من قام أيضا ب إعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

تشغيل هذا الاستعلام لمعرفة عدد رسائل البريد الإلكتروني التي تم إعادة توجيهها إلى هؤلاء المستلمين.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

يمكنك تشغيل هذا الاستعلام لمعرفة مدى تكرار إعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

تشغيل هذا الاستعلام لمعرفة ما إذا كان البريد الإلكتروني يحتوي على أي عناوين URL.
 
```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

تشغيل هذا الاستعلام لمعرفة ما إذا كان البريد الإلكتروني يحتوي على أي مرفقات.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

قم بتشغيل هذا الاستعلام لمعرفة ما إذا كان "المرسل" قد أنشأ أي قواعد جديدة.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with display name of Forwarder
let action_types = pack_array(
    "New-InboxRule", 
    "UpdateInboxRules", 
    "Set-InboxRule", 
    "Set-Mailbox",    
    "New-TransportRule",
    "Set-TransportRule");
CloudAppEvents
| where AccountDisplayName == sender
| where ActionType in (action_types)
```

قم بتشغيل هذا الاستعلام لمعرفة ما إذا كان هناك أي أحداث تسجيل دخول غير متجانسة من هذا المستخدم. على سبيل المثال: مواقع IPs غير معروفة وتطبيقات جديدة والبلدان غير الشائعة والأحداث المتعددة التي تم تسجيل تسجيلها.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder 
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>التحقق من قواعد إعادة توجيه

يمكنك أيضا العثور على قواعد إعادة توجيه مريبة باستخدام مركز إدارة Exchange، استنادا إلى نوع القاعدة (قيمة FT في التنبيه).

- ETR 

  Exchange قواعد النقل في القسم **القواعد**. تحقق من أن كل القواعد كما هو متوقع.

- SMTP

  يمكنك الاطلاع على قواعد إعادة توجيه علبة البريد عن طريق تحديد **\> \> علبة بريد المرسل إدارة إعدادات تدفق البريد تحرير إعادة توجيه \> البريد الإلكتروني**.

- علبة الواردRule

  يتم تكوين قواعد علبة الوارد باستخدام عميل البريد الإلكتروني. يمكنك استخدام [الأمر Get-InboxRule](/powershell/module/exchange/get-inboxrule) PowerShell cmdlet لقائمة قواعد علبة الوارد التي أنشأها المستخدمون.

### <a name="additional-investigation"></a>تحقيق إضافي

إلى جانب الإثباتات التي تم اكتشافها حتى الآن، يمكنك تحديد ما إذا كان هناك قواعد إعادة توجيه جديدة يتم إنشاؤها. تحقق من عنوان IP المقترن بالقاعدة. تأكد من أنه ليس عنوان IP غير عادي ومتناسق مع الأنشطة العادية التي يقوم بها المستخدم.

## <a name="recommended-actions"></a>الإجراءات الموصى بها

بمجرد تحديد أن الأنشطة المقترنة تجعل هذا التنبيه "True Positive"، قم بتصنيف التنبيه واتخاذ هذه الإجراءات لتصحيح المشكلة:

1. قم بتعطيل قاعدة إعادة توجيه علبة الوارد وحذفها.
2. بالنسبة لنوع إعادة توجيه علبة الوارد، قم بإعادة تعيين بيانات اعتماد حساب المستخدم.
3. بالنسبة لنوع إعادة توجيه SMTP أو ETR، تحقق من أنشطة حساب المستخدم الذي أنشأ التنبيه.

    - تحقق من أي أنشطة إدارة مريبة أخرى.

    - إعادة تعيين بيانات اعتماد حساب المستخدم.

4. تحقق من الأنشطة الإضافية التي تم إنشاءها من الحسابات وعناوين IP والمرسلين المريبين.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول تصنيف التنبيهات](alert-grading-playbooks.md)
- [قواعد إعادة توجيه علبة الوارد المريبة](alert-grading-playbook-inbox-forwarding-rules.md)
- [قواعد معالجة علبة الوارد المريبة](alert-grading-playbook-inbox-manipulation-rules.md)
- [التحقق من التنبيهات](investigate-alerts.md)
