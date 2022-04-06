---
title: تصنيف التنبيه لنشاط إعادة توجيه البريد الإلكتروني المشبوه
description: تصنيف التنبيه لنشاط إعادة توجيه البريد الإلكتروني المشبوه لمراجعة التنبيهات واتخاذ الإجراءات الموصى بها لمعالجة الهجوم وحماية شبكتك.
keywords: الحوادث والتنبيهات والتحقيق والتحليل والاستجابة والارتباط والهجوم والأجهزة والأجهزة والمستخدمين والهويات والهوية وعلبة البريد والبريد الإلكتروني و365 وmicrosoft وm365
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
ms.openlocfilehash: dcfb6d01503dd4499ce6431b95a433c4cb598de1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663215"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>تصنيف التنبيه لنشاط إعادة توجيه البريد الإلكتروني المشبوه

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن لجهات التهديد استخدام حسابات المستخدمين المخترقة لعدة أغراض ضارة، بما في ذلك قراءة رسائل البريد الإلكتروني في علبة الوارد الخاصة بالمستخدم، وإعادة توجيه رسائل البريد الإلكتروني إلى المستلمين الخارجيين، وإرسال رسائل التصيد الاحتيالي، من بين أمور أخرى. قد لا يدرك المستخدم المستهدف أنه يتم إعادة توجيه رسائل البريد الإلكتروني الخاصة به. هذا أسلوب شائع جدا يستخدمه المهاجمون عند اختراق حسابات المستخدمين.

يمكن إعادة توجيه رسائل البريد الإلكتروني إما يدويا أو تلقائيا باستخدام قواعد إعادة التوجيه. يمكن تنفيذ إعادة التوجيه التلقائي بطرق متعددة مثل قواعد علبة الوارد Exchange قاعدة النقل (ETR) وإعادة توجيه SMTP. بينما يتطلب إعادة التوجيه اليدوي إجراء مباشرا من المستخدمين، فقد لا يكونوا على دراية بجميع رسائل البريد الإلكتروني التي تمت إعادة توجيهها تلقائيا. في Microsoft 365، يتم رفع تنبيه عندما يقوم مستخدم تلقائيا بإعادة توجيه رسالة بريد إلكتروني إلى عنوان بريد إلكتروني يحتمل أن يكون ضارا.

يساعدك دليل المبادئ هذا على التحقق من تنبيهات نشاط إعادة توجيه البريد الإلكتروني المشبوهة وتصنيفها بسرعة إما على أنها إيجابية True (TP) أو إيجابية خاطئة (FP). يمكنك بعد ذلك اتخاذ الإجراءات الموصى بها لتنبيهات TP لمعالجة الهجوم.

للحصول على نظرة عامة حول تصنيف التنبيه Microsoft Defender لـ Office 365 Microsoft Defender for Cloud Apps، راجع [مقالة المقدمة](alert-grading-playbooks.md).

نتائج استخدام دليل المبادئ هذا هي:

- لقد حددت التنبيهات المقترنة برسائل البريد الإلكتروني التي تمت إعادة توجيهها تلقائيا على أنها أنشطة ضارة (TP) أو غير ضارة (FP).

  إذا كانت ضارة، فقد [أوقفت إعادة التوجيه التلقائي للبريد الإلكتروني](../office-365-security/external-email-forwarding.md) لعلب البريد المتأثرة.

- لقد اتخذت الإجراء اللازم إذا تمت إعادة توجيه رسائل البريد الإلكتروني إلى عنوان بريد إلكتروني ضار.

## <a name="email-forwarding-rules"></a>قواعد إعادة توجيه البريد الإلكتروني

تسمح قواعد إعادة توجيه البريد الإلكتروني للمستخدمين بإنشاء قاعدة لإعادة توجيه رسائل البريد الإلكتروني المرسلة إلى علبة بريد المستخدم إلى علبة بريد مستخدم آخر داخل المؤسسة أو خارجها. يقوم بعض مستخدمي البريد الإلكتروني، لا سيما الذين لديهم علب بريد متعددة، بتكوين قواعد إعادة التوجيه لنقل رسائل البريد الإلكتروني لصاحب العمل إلى حسابات البريد الإلكتروني الخاصة بهم. تعد إعادة توجيه البريد الإلكتروني ميزة مفيدة ولكنها قد تشكل أيضا خطرا أمنيا بسبب إمكانية الكشف عن المعلومات. قد يستخدم المهاجمون هذه المعلومات لمهاجمة مؤسستك أو شركائها.

### <a name="suspicious-email-forwarding-activity"></a>نشاط إعادة توجيه البريد الإلكتروني المريب

قد يقوم المهاجمون بإعداد قواعد البريد الإلكتروني لإخفاء رسائل البريد الإلكتروني الواردة في علبة بريد المستخدم المخترقة لحجب أنشطتهم الضارة عن المستخدم. وقد يقومون أيضا بتعيين قواعد في علبة بريد المستخدم المخترقة لحذف رسائل البريد الإلكتروني، أو نقل رسائل البريد الإلكتروني إلى مجلد آخر أقل وضوحا مثل مجلد RSS، أو إعادة توجيه رسائل البريد الإلكتروني إلى حساب خارجي.

قد تقوم بعض القواعد بنقل كل رسائل البريد الإلكتروني إلى مجلد آخر ووضع علامة عليها على أنها "مقروءة"، بينما قد تنقل بعض القواعد رسائل البريد التي تحتوي على كلمات أساسية معينة فقط في رسالة البريد الإلكتروني أو الموضوع. على سبيل المثال، قد يتم تعيين قاعدة علبة الوارد للبحث عن كلمات أساسية مثل "فاتورة" أو "تصيد احتيالي" أو "عدم الرد" أو "بريد إلكتروني مريب" أو "بريد عشوائي" من بين أمور أخرى، ونقلها إلى حساب بريد إلكتروني خارجي. قد يستخدم المهاجمون أيضا علبة بريد المستخدم المخترقة لتوزيع البريد العشوائي أو رسائل البريد الإلكتروني التصيد الاحتيالي أو البرامج الضارة.

Microsoft Defender لـ Office 365 إمكانية الكشف عن قواعد إعادة توجيه البريد الإلكتروني المشبوهة والتنبيه إليها، مما يسمح لك بالبحث عن القواعد المخفية في المصدر وحذفها.

لمزيد من المعلومات، راجع منشورات المدونة هذه:

- [اختراق البريد الإلكتروني للأعمال](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [خلف الكواليس من اختراق البريد الإلكتروني للأعمال: استخدام بيانات التهديد عبر المجالات لتعطيل حملة BEC كبيرة](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)

## <a name="alert-details"></a>تفاصيل التنبيه

لمراجعة تنبيه نشاط إعادة توجيه البريد الإلكتروني المشبوه، افتح صفحة **"التنبيهات** " للاطلاع على قسم **قائمة "النشاط** ". فيما يلي مثال على ذلك.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="قائمة الأنشطة المتعلقة بالتنبيه" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

حدد **النشاط**  لعرض تفاصيل هذا النشاط في الشريط الجانبي. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="تفاصيل النشاط" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

يحتوي الحقل **Reason** على المعلومات التالية المتعلقة بهذا التنبيه.

- نوع إعادة التوجيه (FT) هو أحد الإجراءات التالية:
  - Exchange قاعدة النقل (ETR): تمت إعادة توجيهها باستخدام قاعدة النقل Exchange
  - SMTP: تمت إعادة التوجيه باستخدام إعادة توجيه علبة البريد
  - علبة الوارد: تمت إعادة توجيهها باستخدام قاعدة علبة الوارد

- معرف تتبع الرسائل (MTI): هذا هو معرف (NetworkMessageId) للبريد الإلكتروني الذي تمت إعادة توجيهه الذي قام بتشغيل هذا التنبيه. NetworkMessageId هو المعرف الفريد لرسالة بريد إلكتروني في مؤسستك.
- إعادة التوجيه (F): المستخدم الذي قام بإعادة توجيه هذا البريد الإلكتروني.
- قائمة مستلمين مريبة (SRL): قائمة المستلمين التي تعتبر مريبة في هذا البريد الإلكتروني.
- قائمة المستلمين (RL): قائمة بكل المستلمين في هذا البريد الإلكتروني.

## <a name="investigation-workflow"></a>سير عمل التحقيق

أثناء التحقق من هذا التنبيه، يجب عليك تحديد:

- هل تم اختراق حساب المستخدم وعلبة البريد الخاصة به؟
- هل الأنشطة ضارة؟

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>هل تم اختراق حساب المستخدم وعلبة البريد الخاصة به؟

من خلال النظر في سلوك المرسل السابق والأنشطة الأخيرة، يجب أن تكون قادرا على تحديد ما إذا كان يجب اعتبار حساب المستخدم مخترقا أم لا. يمكنك الاطلاع على تفاصيل التنبيهات التي تم رفعها من صفحة المستخدم في مدخل Microsoft 365 Defender.

يمكنك أيضا تحليل هذه الأنشطة الإضافية لعل البريد المتأثر:

- استخدام مستكشف التهديدات لفهم التهديدات المتعلقة بالبريد الإلكتروني
  - لاحظ عدد رسائل البريد الإلكتروني الأخيرة التي تم اكتشافها من قبل المرسل على أنها تصيد احتيالي أو بريد عشوائي أو برامج ضارة.
  - لاحظ عدد رسائل البريد الإلكتروني المرسلة التي تحتوي على معلومات حساسة.

- تقييم سلوك تسجيل الدخول المحفوفة بالمخاطر في مدخل Microsoft Azure.
- تحقق من وجود أي أنشطة ضارة على جهاز المستخدم.

### <a name="are-the-activities-malicious"></a>هل الأنشطة ضارة؟

التحقيق في نشاط إعادة توجيه البريد الإلكتروني. على سبيل المثال، تحقق من نوع البريد الإلكتروني أو مستلم هذا البريد الإلكتروني أو الطريقة التي تتم بها إعادة توجيه البريد الإلكتروني.

لمزيد من المعلومات، راجع المقالات التالية:

- [رؤى الرسائل التي تمت إعادة توجيهها تلقائيا](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [مستخدمون جدد يعيدون توجيه رؤى البريد الإلكتروني](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [الاستجابة إلى حساب بريد إلكتروني تم اختراقه](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

فيما يلي سير العمل لتحديد أنشطة إعادة توجيه البريد الإلكتروني المشبوهة.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="سير عمل التحقيق في التنبيه لإعادة توجيه البريد الإلكتروني" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

يمكنك التحقق من تنبيه إعادة توجيه البريد الإلكتروني باستخدام مستكشف التهديدات أو باستخدام استعلامات تتبع متقدمة، استنادا إلى توفر الميزات في مدخل Microsoft 365 Defender. يمكنك اختيار اتباع العملية بأكملها أو جزء من العملية حسب الحاجة.

## <a name="using-threat-explorer"></a>استخدام مستكشف المخاطر

يوفر مستكشف التهديدات تجربة تحقيق تفاعلية للتهديدات المتعلقة بالبريد الإلكتروني لتحديد ما إذا كان هذا النشاط مريبا أم لا. يمكنك استخدام المؤشرات التالية من معلومات التنبيه:

- SRL/RL: استخدم قائمة المستلمين (المشبوهة) (SRL) للعثور على هذه التفاصيل:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="مثال لقائمة المستلمين" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

  - روبوت Who آخر قام بإعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين؟
  - كم عدد رسائل البريد الإلكتروني التي تمت إعادة توجيهها إلى هؤلاء المستلمين؟
  - ما مدى تكرار إعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين؟

- MTI: استخدم معرف تتبع الرسائل/معرف رسالة الشبكة للعثور على هذه التفاصيل:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="مثال لمعرف رسالة الشبكة" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

  - ما هي التفاصيل الإضافية المتوفرة لهذا البريد الإلكتروني؟ على سبيل المثال: الموضوع ومسار الإرجاع والطوابع الزمنية.
  - ما هو أصل هذا البريد الإلكتروني؟ هل هناك أي رسائل بريد إلكتروني مماثلة؟
  - هل يحتوي هذا البريد الإلكتروني على أي عناوين URL؟ هل يشير URL إلى أي بيانات حساسة؟
  - هل يحتوي البريد الإلكتروني على أي مرفقات؟ هل تحتوي المرفقات على معلومات حساسة؟
  - ما الإجراء الذي تم اتخاذه على البريد الإلكتروني؟ هل تم حذفه أو وضع علامة عليه كمقروء أو نقله إلى مجلد آخر؟
  - هل هناك أي تهديدات مقترنة بهذا البريد الإلكتروني؟ هل هذا البريد الإلكتروني جزء من أي حملة؟

استنادا إلى إجابات هذه الأسئلة، يجب أن تكون قادرا على تحديد ما إذا كان البريد الإلكتروني ضارا أم غير ضار.

## <a name="advanced-hunting-queries"></a>استعلامات التتبع المتقدمة

لاستخدام استعلامات [التتبع المتقدمة](advanced-hunting-overview.md) لجمع المعلومات المتعلقة بالتنبيه وتحديد ما إذا كان النشاط مريبا أم لا، تأكد من أن لديك حق الوصول إلى الجداول التالية:

- EmailEvents - يحتوي على معلومات تتعلق بتدفق البريد الإلكتروني.

- EmailUrlInfo - يحتوي على معلومات تتعلق بعناوين URL في رسائل البريد الإلكتروني.

- CloudAppEvents -Contains audit log of user activities.

- IdentityLogonEvents - يحتوي على معلومات تسجيل الدخول لجميع المستخدمين.

> [!NOTE]
> بعض المعلمات فريدة لمؤسستك أو شبكتك. املأ هذه المعلمات المحددة كما هو مرشاد في كل استعلام.

قم بتشغيل هذا الاستعلام لمعرفة من قام بإعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين (SRL/RL).

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

قم بتشغيل هذا الاستعلام لمعرفة عدد رسائل البريد الإلكتروني التي تمت إعادة توجيهها إلى هؤلاء المستلمين.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

قم بتشغيل هذا الاستعلام لمعرفة مدى تكرار إعادة توجيه رسائل البريد الإلكتروني إلى هؤلاء المستلمين.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

قم بتشغيل هذا الاستعلام لمعرفة ما إذا كان البريد الإلكتروني يحتوي على أي عناوين URL.

```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

قم بتشغيل هذا الاستعلام لمعرفة ما إذا كان البريد الإلكتروني يحتوي على أي مرفقات.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

قم بتشغيل هذا الاستعلام لمعرفة ما إذا كان "إعادة التوجيه" (المرسل) قد أنشأ أي قواعد جديدة.

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

قم بتشغيل هذا الاستعلام لمعرفة ما إذا كانت هناك أي أحداث تسجيل دخول غير طبيعية من هذا المستخدم. على سبيل المثال: عناوين IP غير معروفة والتطبيقات الجديدة والبلدان غير المألوفة وأحداث تسجيل الدخول المتعددة.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>التحقق من قواعد إعادة التوجيه

يمكنك أيضا العثور على قواعد إعادة التوجيه المشبوهة باستخدام مركز إدارة Exchange، استنادا إلى نوع القاعدة (قيمة FT في التنبيه).

- ETR

  يتم سرد قواعد النقل Exchange في قسم **"القواعد**". تحقق من أن جميع القواعد كما هو متوقع.

- SMTP

  يمكنك رؤية قواعد إعادة توجيه علبة البريد عن طريق تحديد "**تحرير إعادة توجيه \> البريد الإلكتروني" في علبة بريد\> المرسل" "إدارة إعدادات \> تدفق البريد**".

- علبة الوارد

  يتم تكوين قواعد علبة الوارد مع عميل البريد الإلكتروني. يمكنك استخدام [Get-InboxRule](/powershell/module/exchange/get-inboxrule) PowerShell cmdlet لإدراج قواعد علبة الوارد التي أنشأها المستخدمون.

### <a name="additional-investigation"></a>تحقيق إضافي

إلى جانب الأدلة المكتشفة حتى الآن، يمكنك تحديد ما إذا كانت هناك قواعد إعادة توجيه جديدة يتم إنشاؤها. تحقق من عنوان IP المقترن بالقاعدة. تأكد من أنه ليس عنوان IP غير مألوف ويتوافق مع الأنشطة المعتادة التي يقوم بها المستخدم.

## <a name="recommended-actions"></a>الإجراءات الموصى بها

بمجرد تحديد أن الأنشطة المقترنة تجعل هذا التنبيه "إيجابية True"، قم بتصنيف التنبيه واتخاذ هذه الإجراءات للمعالجة:

1. تعطيل قاعدة إعادة توجيه علبة الوارد وحذفها.
2. بالنسبة لنوع إعادة توجيه InboxRule، قم بإعادة تعيين بيانات اعتماد حساب المستخدم.
3. بالنسبة لنوع إعادة توجيه SMTP أو ETR، تحقق من أنشطة حساب المستخدم الذي أنشأ التنبيه.

    - التحقيق في أي أنشطة إدارية مريبة أخرى.

    - إعادة تعيين بيانات اعتماد حساب المستخدم.

4. تحقق من وجود أنشطة إضافية نشأت من الحسابات المتأثرة وعناوين IP والمرسلين المشبوهين.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على تصنيف التنبيه](alert-grading-playbooks.md)
- [قواعد إعادة توجيه علبة الوارد المريبة](alert-grading-playbook-inbox-forwarding-rules.md)
- [قواعد معالجة علبة الوارد المريبة](alert-grading-playbook-inbox-manipulation-rules.md)
- [التحقق من التنبيهات](investigate-alerts.md)
