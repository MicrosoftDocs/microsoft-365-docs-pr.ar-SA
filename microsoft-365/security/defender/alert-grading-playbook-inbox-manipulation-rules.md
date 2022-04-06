---
title: تصنيف التنبيه لقواعد معالجة علبة الوارد المريبة
description: تصنيف التنبيه لقواعد معالجة علبة الوارد المشبوهة لمراجعة التنبيهات واتخاذ الإجراءات الموصى بها لمعالجة الهجوم وحماية شبكتك.
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
ms.openlocfilehash: e663d02037633599b9dffc19e1ebbd174aa279e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663171"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>تصنيف التنبيه لقواعد معالجة علبة الوارد المريبة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن لجهات التهديد استخدام حسابات المستخدمين المخترقة للعديد من الأغراض الضارة، بما في ذلك قراءة رسائل البريد الإلكتروني في علبة الوارد الخاصة بالمستخدم، وإنشاء قواعد علبة الوارد لإعادة توجيه رسائل البريد الإلكتروني إلى حسابات خارجية، وحذف التتبعات، وإرسال رسائل التصيد الاحتيالي. تعد قواعد علبة الوارد الضارة شائعة أثناء عمليات اختراق البريد الإلكتروني للأعمال (BEC) وحملات التصيد الاحتيالي ومن المهم مراقبتها باستمرار.

يساعدك دليل المبادئ هذا على التحقيق في أي حادث يتعلق بقواعد معالجة علبة الوارد المشبوهة التي تم تكوينها من قبل المهاجمين واتخاذ الإجراءات الموصى بها لمعالجة الهجوم وحماية شبكتك. دليل المبادئ هذا خاص بفرق الأمان، بما في ذلك محللي مركز عمليات الأمان (SOC) ومسؤولي تكنولوجيا المعلومات الذين يراجعون التنبيهات ويتحققون منها ويصنفونها. يمكنك بسرعة تصنيف التنبيهات إما إيجابية True Positive (TP) أو False Positive (TP) واتخاذ الإجراءات الموصى بها لتنبيهات TP لمعالجة الهجوم.

نتائج استخدام دليل المبادئ هذا هي:

- لقد حددت التنبيهات المقترنة بقواعد معالجة علبة الوارد على أنها أنشطة ضارة (TP) أو غير ضارة (FP).

  إذا كانت ضارة، فقد قمت بإزالة قواعد معالجة علبة الوارد الضارة.

- لقد اتخذت الإجراء اللازم إذا تمت إعادة توجيه رسائل البريد الإلكتروني إلى عنوان بريد إلكتروني ضار.

## <a name="inbox-manipulation-rules"></a>قواعد معالجة علبة الوارد

يتم تعيين قواعد علبة الوارد لإدارة رسائل البريد الإلكتروني تلقائيا استنادا إلى معايير معرفة مسبقا. على سبيل المثال، يمكنك إنشاء قاعدة علبة الوارد لنقل كل الرسائل من مديرك إلى مجلد آخر، أو إعادة توجيه الرسائل التي تتلقاها إلى عنوان بريد إلكتروني آخر.

### <a name="malicious-inbox-manipulation-rules"></a>قواعد معالجة علبة الوارد الضارة

قد يقوم المهاجمون بإعداد قواعد البريد الإلكتروني لإخفاء رسائل البريد الإلكتروني الواردة في علبة بريد المستخدم المخترقة لحجب أنشطتهم الضارة عن المستخدم. وقد يقومون أيضا بتعيين قواعد في علبة بريد المستخدم المخترقة لحذف رسائل البريد الإلكتروني، أو نقل رسائل البريد الإلكتروني إلى مجلد آخر أقل وضوحا (مثل RSS)، أو إعادة توجيه رسائل البريد إلى حساب خارجي. قد تقوم بعض القواعد بنقل كل رسائل البريد الإلكتروني إلى مجلد آخر ووضع علامة عليها على أنها "مقروءة"، بينما قد تنقل بعض القواعد رسائل البريد التي تحتوي على كلمات أساسية معينة فقط في رسالة البريد الإلكتروني أو الموضوع.

على سبيل المثال، قد يتم تعيين قاعدة علبة الوارد للبحث عن كلمات أساسية مثل "فاتورة" أو "تصيد احتيالي" أو "عدم الرد" أو "بريد إلكتروني مريب" أو "بريد عشوائي" من بين أمور أخرى، ونقلها إلى حساب بريد إلكتروني خارجي. قد يستخدم المهاجمون أيضا علبة بريد المستخدم المخترقة لتوزيع البريد العشوائي أو رسائل البريد الإلكتروني التصيد الاحتيالي أو البرامج الضارة.

## <a name="workflow"></a>سير العمل

فيما يلي سير العمل لتحديد أنشطة قاعدة معالجة علبة الوارد المشبوهة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="سير عمل التحقيق في التنبيه لقواعد معالجة علبة الوارد" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::

## <a name="investigation-steps"></a>خطوات التحقيق

يحتوي هذا القسم على إرشادات مفصلة خطوة بخطوة للاستجابة للحادث واتخاذ الخطوات الموصى بها لحماية مؤسستك من المزيد من الهجمات.

### <a name="1-review-the-alerts"></a>1. مراجعة التنبيهات

فيما يلي مثال على تنبيه قاعدة معالجة علبة الوارد في قائمة انتظار التنبيه.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="مثال لقاعدة معالجة علبة الوارد" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

فيما يلي مثال على تفاصيل تنبيه تم تشغيله بواسطة قاعدة معالجة علبة وارد ضارة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="تفاصيل التنبيه الذي تم تشغيله بواسطة قاعدة معالجة علبة وارد ضارة" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::

### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. التحقيق في معلمات قاعدة معالجة علبة الوارد

تحديد ما إذا كانت القواعد تبدو مريبة وفقا لمعلمات القاعدة أو المعايير التالية:

- الكلمات الرئيسيه

   قد يطبق المهاجم قاعدة المعالجة فقط على رسائل البريد الإلكتروني التي تحتوي على كلمات معينة. يمكنك العثور على هذه الكلمات الأساسية ضمن سمات معينة مثل: "BodyContainsWords" أو "SubjectContainsWords" أو "SubjectOrBodyContainsWords".

   إذا كانت هناك تصفية حسب الكلمات الأساسية، فتحقق مما إذا كانت الكلمات الأساسية تبدو مريبة لك (السيناريوهات الشائعة هي تصفية رسائل البريد الإلكتروني المتعلقة بأنشطة المهاجم، مثل "التصيد الاحتيالي" و"البريد العشوائي" و"عدم الرد"، من بين أمور أخرى).

   إذا لم يكن هناك عامل تصفية على الإطلاق، فقد يكون مريبا أيضا.

- مجلد الوجهة

   لتجنب الكشف عن الأمان، قد يقوم المهاجم بنقل رسائل البريد الإلكتروني إلى مجلد أقل وضوحا ووضع علامة على رسائل البريد الإلكتروني كمقروءة (على سبيل المثال، مجلد "RSS"). إذا طبق المهاجم الإجراءين "MoveToFolder" و"MarkAsRead"، فتحقق مما إذا كان المجلد الوجهة مرتبطا بطريقة ما بالكلمات الأساسية في القاعدة لتحديد ما إذا كان يبدو مريبا أم لا.

- حذف الكل

   سيقوم بعض المهاجمين فقط بحذف جميع رسائل البريد الإلكتروني الواردة لإخفاء نشاطهم. في الغالب، تعد قاعدة "حذف كل رسائل البريد الإلكتروني الواردة" دون تصفيتها باستخدام الكلمات الأساسية مؤشرا على النشاط الضار.

فيما يلي مثال على تكوين قاعدة "حذف كافة رسائل البريد الإلكتروني الواردة" (كما هو موضح في RawEventData.Parameters) لسجل الأحداث ذي الصلة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="مثال على حذف كافة تكوين قاعدة رسائل البريد الإلكتروني الواردة" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::

### <a name="3-investigate-the-ip-address"></a>3. التحقق من عنوان IP

راجع سمات عنوان IP الذي نفذ الحدث ذي الصلة لإنشاء القاعدة:

- ابحث عن أنشطة سحابية مشبوهة أخرى نشأت من نفس IP في المستأجر. على سبيل المثال، قد يكون النشاط المشبوه عدة محاولات فاشلة لتسجيل الدخول.
- هل ISP شائع معقول لهذا المستخدم؟
- هل الموقع شائع معقول لهذا المستخدم؟

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. التحقيق في النشاط المشبوه من قبل المستخدم قبل إنشاء القواعد

يمكنك مراجعة جميع أنشطة المستخدم قبل إنشاء القواعد، والتحقق من مؤشرات التسوية، والتحقيق في إجراءات المستخدم التي تبدو مريبة.

على سبيل المثال، بالنسبة إلى عمليات تسجيل الدخول الفاشلة المتعددة، افحص:

- نشاط تسجيل الدخول

   تحقق من أن نشاط تسجيل الدخول قبل إنشاء القاعدة ليس مريبا. (الموقع المشترك / ISP / عامل المستخدم).

- التنبيهات

   تحقق مما إذا كان المستخدم قد تلقى تنبيهات قبل إنشاء القواعد. قد يشير هذا إلى أنه قد يتم اختراق حساب المستخدم. على سبيل المثال، تنبيه السفر المستحيل، والبلد غير المتكرر، وتسجيلات الدخول الفاشلة المتعددة، من بين أمور أخرى.)

- الحادث

   تحقق مما إذا كان التنبيه مقترنا بتنبيهات أخرى تشير إلى وقوع حادث. إذا كان الأمر كذلك، فتحقق مما إذا كان الحدث يحتوي على تنبيهات إيجابية حقيقية أخرى.

## <a name="advanced-hunting-queries"></a>استعلامات التتبع المتقدمة

[التتبع المتقدم](advanced-hunting-overview.md) هو أداة تتبع المخاطر المستندة إلى الاستعلام تتيح لك فحص الأحداث في شبكتك لتحديد موقع مؤشرات التهديد.

استخدم هذا الاستعلام للبحث عن كافة أحداث قاعدة علبة الوارد الجديدة أثناء نافذة زمنية معينة.

```kusto
let start_date = now(-10h);
let end_date = now();
let user_id = ""; // enter here the user id
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where AccountObjectId == user_id
| where Application == @"Microsoft Exchange Online"
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
```

سيوفر عمود *RuleConfig* تكوين قاعدة علبة الوارد الجديد.

استخدم هذا الاستعلام للتحقق مما إذا كان موفر خدمة ISP شائعا للمستخدم من خلال النظر في محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

استخدم هذا الاستعلام للتحقق مما إذا كان البلد شائعا للمستخدم من خلال الاطلاع على محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

استخدم هذا الاستعلام للتحقق مما إذا كان عامل المستخدم شائعا للمستخدم من خلال النظر في محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

## <a name="recommended-actions"></a>الإجراءات الموصى بها

1. تعطيل قاعدة علبة الوارد الضارة.
2. إعادة تعيين بيانات اعتماد حساب المستخدم. يمكنك أيضا التحقق مما إذا تم اختراق حساب المستخدم باستخدام Microsoft Defender for Cloud Apps، والذي يحصل على إشارات الأمان من Azure Active Directory (Azure AD) Identity Protection.
3. ابحث عن أنشطة ضارة أخرى يتم تنفيذها بواسطة حساب المستخدم المتأثر.
4. تحقق من وجود نشاط مريب آخر في المستأجر الذي تم إنشاؤه من نفس IP أو من نفس موفر خدمة الإنترنت (إذا كان موفر خدمة الإنترنت غير شائع) للعثور على حسابات المستخدمين المخترقة الأخرى.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على تصنيف التنبيه](alert-grading-playbooks.md)
- [نشاط إعادة توجيه البريد الإلكتروني المريب](alert-grading-playbook-email-forwarding.md)
- [قواعد إعادة توجيه علبة الوارد المريبة](alert-grading-playbook-inbox-forwarding-rules.md)
- [التحقق من التنبيهات](investigate-alerts.md)
