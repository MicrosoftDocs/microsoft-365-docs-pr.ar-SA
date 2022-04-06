---
title: تصنيف التنبيه لقواعد إعادة توجيه علبة الوارد المريبة
description: تصنيف التنبيه لقواعد إعادة توجيه علبة الوارد المشبوهة لمراجعة التنبيهات واتخاذ الإجراءات الموصى بها لمعالجة الهجوم وحماية شبكتك.
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
ms.openlocfilehash: dca305b88e6e8db25e0a798c4361086bd7cb1e8b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666009"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>تصنيف التنبيه لقواعد إعادة توجيه علبة الوارد المريبة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن لجهات التهديد استخدام حسابات المستخدمين المخترقة لعدة أغراض ضارة، بما في ذلك قراءة رسائل البريد الإلكتروني في علبة الوارد الخاصة بالمستخدم، وإنشاء قواعد علبة الوارد لإعادة توجيه رسائل البريد الإلكتروني إلى حسابات خارجية، وإرسال رسائل التصيد الاحتيالي، من بين أمور أخرى. قواعد علبة الوارد الضارة شائعة على نطاق واسع أثناء اختراق البريد الإلكتروني للأعمال (BEC) وحملات التصيد الاحتيالي، ومن المهم مراقبتها باستمرار.

يساعدك دليل المبادئ هذا على التحقق من التنبيهات الخاصة بقواعد إعادة توجيه علبة الوارد المريبة، وتصنيفها بسرعة إما على أنها موجبة True Positive (TP) أو False Positive (TP). يمكنك بعد ذلك اتخاذ الإجراءات الموصى بها لتنبيهات TP لمعالجة الهجوم.

للحصول على نظرة عامة حول تصنيف التنبيه Microsoft Defender لـ Office 365 Microsoft Defender for Cloud Apps، راجع [مقالة المقدمة](alert-grading-playbooks.md).

نتائج استخدام دليل المبادئ هذا هي:

- لقد حددت التنبيهات المقترنة بقواعد إعادة توجيه علبة الوارد على أنها أنشطة ضارة (TP) أو غير ضارة (FP).

  إذا كانت ضارة، فقد قمت بإزالة قواعد إعادة توجيه علبة الوارد الضارة.

- لقد اتخذت الإجراء اللازم إذا تمت إعادة توجيه رسائل البريد الإلكتروني إلى عنوان بريد إلكتروني ضار.

## <a name="inbox-forwarding-rules"></a>قواعد إعادة توجيه علبة الوارد

يمكنك تكوين قواعد علبة الوارد لإدارة رسائل البريد الإلكتروني تلقائيا استنادا إلى معايير معرفة مسبقا. على سبيل المثال، يمكنك إنشاء قاعدة علبة الوارد لنقل كل الرسائل من مديرك إلى مجلد آخر، أو إعادة توجيه الرسائل التي تتلقاها إلى عنوان بريد إلكتروني آخر.

### <a name="suspicious-inbox-forwarding-rules"></a>قواعد إعادة توجيه علبة الوارد المريبة

بعد الوصول إلى علب بريد المستخدمين، غالبا ما ينشئ المهاجمون قاعدة علبة وارد تسمح لهم بتصفية البيانات الحساسة إلى عنوان بريد إلكتروني خارجي واستخدامها لأغراض ضارة.

تأتمت قواعد علبة الوارد الضارة عملية النقل غير المصرح به. مع قواعد محددة، ستتم إعادة توجيه كل بريد إلكتروني في علبة الوارد الخاصة بالمستخدم الهدف يطابق معايير القاعدة إلى علبة بريد المهاجم. على سبيل المثال، قد يرغب المهاجم في جمع البيانات الحساسة المتعلقة بالشؤون المالية. يقومون بإنشاء قاعدة علبة الوارد لإعادة توجيه كل رسائل البريد الإلكتروني التي تحتوي على كلمات أساسية، مثل "التمويل" و"الفاتورة" في الموضوع أو نص الرسالة، إلى علبة البريد الخاصة بهم.

قد يكون من الصعب جدا الكشف عن قواعد إعادة توجيه علبة الوارد المشبوهة لأن صيانة قواعد علبة الوارد مهمة شائعة يقوم بها المستخدمون. لذلك، من المهم مراقبة التنبيهات.

## <a name="workflow"></a>سير العمل

فيما يلي سير العمل لتحديد قواعد إعادة توجيه البريد الإلكتروني المشبوهة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="سير عمل التحقيق في التنبيه لقواعد إعادة توجيه علبة الوارد" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>خطوات التحقيق

يحتوي هذا القسم على إرشادات مفصلة خطوة بخطوة للاستجابة للحادث واتخاذ الخطوات الموصى بها لحماية مؤسستك من المزيد من الهجمات.

### <a name="review-generated-alerts"></a>مراجعة التنبيهات التي تم إنشاؤها

فيما يلي مثال على تنبيه قاعدة إعادة توجيه علبة الوارد في قائمة انتظار التنبيه.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="مثال على إعلام في قائمة انتظار التنبيه" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

فيما يلي مثال على تفاصيل التنبيه الذي تم تشغيله بواسطة قاعدة إعادة توجيه علبة وارد ضارة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="تفاصيل التنبيه الذي تم تشغيله بواسطة قاعدة إعادة توجيه علبة وارد ضارة" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>التحقيق في معلمات القاعدة

الغرض من هذه المرحلة هو تحديد ما إذا كانت القواعد تبدو مريبة وفقا لمعايير معينة:

مستلمو قاعدة إعادة التوجيه:

- التحقق من صحة عنوان البريد الإلكتروني الوجهة ليس علبة بريد إضافية يملكها نفس المستخدم (تجنب الحالات التي يقوم فيها المستخدم بإعادة توجيه رسائل البريد الإلكتروني ذاتيا بين علب البريد الشخصية).
- التحقق من صحة عنوان البريد الإلكتروني الوجهة ليس عنوانا داخليا أو مجالا فرعيا ينتمي إلى الشركة.

عوامل التصفيه:

- إذا كانت قاعدة علبة الوارد تحتوي على عوامل تصفية تبحث عن كلمات أساسية معينة في موضوع البريد الإلكتروني أو نصه، فتحقق مما إذا كانت الكلمات الأساسية المتوفرة، مثل التمويل وبيانات الاعتماد والشبكات، من بين أمور أخرى، تبدو مرتبطة بنشاط ضار. يمكنك العثور على عوامل التصفية هذه ضمن السمات التالية (التي تظهر في عمود RawEventData الحدث): "BodyContainsWords" أو "SubjectContainsWords" أو "SubjectOrBodyContainsWords"
- إذا اختار المهاجم عدم تعيين أي عامل تصفية إلى رسائل البريد، وبدلا من ذلك تقوم قاعدة علبة الوارد بإعادة توجيه كافة عناصر علبة البريد إلى علبة بريد المهاجم)، فإن هذا السلوك مريب أيضا.

### <a name="investigate-ip-address"></a>التحقق من عنوان IP

راجع السمات المتعلقة بعنوان IP الذي نفذ الحدث ذي الصلة لإنشاء القاعدة:

1. ابحث عن أنشطة سحابية مشبوهة أخرى نشأت من نفس IP في المستأجر. على سبيل المثال، قد يكون النشاط المشبوه عدة محاولات تسجيل دخول فاشلة.
2. هل ISP شائع معقول لهذا المستخدم؟
3. هل الموقع شائع معقول لهذا المستخدم؟

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>التحقيق في أي نشاط مريب باستخدام علبة الوارد الخاصة بالمستخدم قبل إنشاء القواعد

يمكنك مراجعة جميع أنشطة المستخدم قبل إنشاء القواعد، والتحقق من مؤشرات التسوية، والتحقيق في إجراءات المستخدم التي تبدو مريبة. على سبيل المثال، فشلت عدة عمليات تسجيل دخول.

- تسجيل الدخول:

  التحقق من أن نشاط تسجيل الدخول قبل حدث إنشاء القاعدة ليس مريبا (مثل الموقع المشترك أو موفر خدمة الإنترنت أو عامل المستخدم).

- تنبيهات أو حوادث أخرى
  - هل تم تشغيل تنبيهات أخرى للمستخدم قبل إنشاء القاعدة. إذا كان الأمر كذلك، فقد يشير ذلك إلى تعرض المستخدم للخطر.
  - إذا كان التنبيه مرتبطا بتنبيهات أخرى للإشارة إلى حادث، فهل يحتوي الحدث على تنبيهات إيجابية صحيحة أخرى؟

## <a name="advanced-hunting-queries"></a>استعلامات التتبع المتقدمة

[التتبع المتقدم](advanced-hunting-overview.md) هو أداة تتبع المخاطر المستندة إلى الاستعلام تتيح لك فحص الأحداث في شبكتك وتحديد موقع مؤشرات التهديد.

قم بتشغيل هذا الاستعلام للعثور على كافة أحداث قاعدة علبة الوارد الجديدة أثناء نافذة زمنية معينة.

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

ستحتوي *RuleConfig* على تكوين القاعدة.

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان موفر خدمة ISP شائعا للمستخدم من خلال النظر في محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان البلد شائعا للمستخدم من خلال النظر في محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان عامل المستخدم شائعا للمستخدم من خلال النظر في محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان المستخدمون الآخرون قد أنشأوا قاعدة إعادة توجيه إلى الوجهة نفسها (قد يشير إلى أن المستخدمين الآخرين قد تم اختراقهم أيضا).

```kusto
let start_date = now(-10h);
let end_date = now();
let dest_email = ""; // enter here destination email as seen in the alert
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
| where RuleConfig has dest_email
```

## <a name="recommended-actions"></a>الإجراءات الموصى بها

1. تعطيل قاعدة علبة الوارد الضارة.
2. إعادة تعيين بيانات اعتماد حساب المستخدم. يمكنك أيضا التحقق مما إذا تم اختراق حساب المستخدم باستخدام Microsoft Defender for Cloud Apps، والذي يحصل على إشارات الأمان من Azure Active Directory (Azure AD) Identity Protection.
3. ابحث عن أنشطة ضارة أخرى قام بها المستخدم المتأثر.
4. تحقق من وجود نشاط مريب آخر في المستأجر من نفس IP أو من نفس ISP (إذا كان ISP غير شائع) للعثور على مستخدمين آخرين تم اختراقهم.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على تصنيف التنبيه](alert-grading-playbooks.md)
- [نشاط إعادة توجيه البريد الإلكتروني المريب](alert-grading-playbook-email-forwarding.md)
- [قواعد معالجة علبة الوارد المريبة](alert-grading-playbook-inbox-manipulation-rules.md)
- [التحقق من التنبيهات](investigate-alerts.md)
