---
title: تصنيف التنبيه لقواعد إعادة توجيه علبة الوارد المريبة
description: تصنيف التنبيه لقواعد إعادة توجيه علبة الوارد المريبة لمراجعة التنبيهات واتخاذ الإجراءات الموصى بها لإعادة توجيه الهجوم وحماية شبكتك.
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
ms.openlocfilehash: 08178a1672e3bdd5b124138f698b42be8181373a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572123"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>تصنيف التنبيه لقواعد إعادة توجيه علبة الوارد المريبة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن لممثلي التهديدات استخدام حسابات المستخدمين المخادعة لأغراض ضارة متعددة بما في ذلك قراءة رسائل البريد الإلكتروني في علبة الوارد الخاصة ب المستخدم، وإنشاء قواعد علبة الوارد من أجل إعادة توجيه رسائل البريد الإلكتروني إلى حسابات خارجية، وإرسال رسائل التصيد الاحتيالي، من بين أمور أخرى. قواعد علبة الوارد الضارة شائعة على نطاق واسع أثناء اختراق البريد الإلكتروني للأعمال وحملات التصيد الاحتيالي، ومن المهم مراقبتها باستمرار.

يساعدك هذا المصنف على التحقق من التنبيهات المتعلقة بقواعد إعادة توجيه علبة الوارد المريبة وتصحيحها بسرعة على أنها True Positive (TP) أو False Positive (TP). يمكنك بعد ذلك اتخاذ الإجراءات الموصى بها لتنبيهات TP لإعادة معالجة الهجوم. 

للحصول على نظرة عامة حول تصنيف التنبيهات ل Microsoft Defender Office 365 و Microsoft Defender لتطبيقات السحابة، راجع [مقالة المقدمة](alert-grading-playbooks.md).

نتائج استخدام هذا المصنف هي:

- لقد حددت التنبيهات المقترنة بقواعد إعادة توجيه علبة الوارد كالأنشطة الضارة (TP) أو الأنشطة الضارة (FP).

  إذا كانت ضارة، قمت بإزالة قواعد إعادة توجيه علبة الوارد الضارة.

- لقد اتخذت الإجراء اللازم إذا تم إعادة توجيه رسائل البريد الإلكتروني إلى عنوان بريد إلكتروني ضار.

## <a name="inbox-forwarding-rules"></a>قواعد إعادة توجيه علبة الوارد

يمكنك تكوين قواعد علبة الوارد لإدارة رسائل البريد الإلكتروني تلقائيا استنادا إلى معايير محددة مسبقا. على سبيل المثال، يمكنك إنشاء قاعدة علبة وارد لنقل كل الرسائل من المدير إلى مجلد آخر، أو إعادة توجيه الرسائل التي تتلقاها إلى عنوان بريد إلكتروني آخر.

### <a name="suspicious-inbox-forwarding-rules"></a>قواعد إعادة توجيه علبة الوارد المريبة

بعد اكتساب حق الوصول إلى علب بريد المستخدمين، غالبا ما يقوم المتطفلون بإنشاء قاعدة علبة وارد تسمح لهم بملء البيانات الحساسة إلى عنوان بريد إلكتروني خارجي واستخدامها لأغراض ضارة. 

تأتمتة قواعد علبة الوارد الضارة عملية الملء. باستخدام قواعد معينة، سيتم إعادة توجيه كل بريد إلكتروني في علبة الوارد الخاصة بالمستخدم الهدف يتطابق مع معايير القاعدة إلى علبة بريد المهاجم. على سبيل المثال، قد يرغب مهاجم في جمع بيانات حساسة ذات صلة بالتمويل. فهي تنشئ قاعدة علبة الوارد من أجل إعادة توجيه كل رسائل البريد الإلكتروني التي تحتوي على كلمات أساسية، مثل "الشؤون المالية" و"الفاتورة" في الموضوع أو نص الرسالة إلى علبة البريد الخاصة بهم.

قد يكون من الصعب جدا الكشف عن قواعد إعادة توجيه علبة الوارد المريبة لأن صيانة قواعد علبة الوارد مهمة شائعة يقوم بها المستخدمون. لذلك، من المهم مراقبة التنبيهات. 

## <a name="workflow"></a>سير العمل

إليك سير العمل لتحديد قواعد إعادة توجيه البريد الإلكتروني المريبة.
 
:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="تنبيه سير عمل التحقيق لقواعد إعادة توجيه علبة الوارد" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>خطوات التحقيق

يحتوي هذا القسم على إرشادات مفصلة خطوة بخطوة للاستجابة للحادث واتخاذ الخطوات الموصى بها لحماية مؤسستك من الهجمات الأخرى.

### <a name="review-generated-alerts"></a>مراجعة التنبيهات التي تم إنشاؤها

فيما يلي مثال لتنبيه قاعدة إعادة توجيه علبة الوارد في قائمة انتظار التنبيهات.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="مثال على إعلام في قائمة انتظار التنبيهات" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

فيما يلي مثال على تفاصيل التنبيه التي تم تشغيلها بواسطة قاعدة إعادة توجيه علبة وارد ضارة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="تفاصيل التنبيه الذي تم تشغيله بواسطة قاعدة إعادة توجيه علبة وارد ضارة" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>التحقق من معلمات القاعدة 

الغرض من هذه المرحلة هو تحديد ما إذا كانت القواعد تبدو مريبة وفقا لمعايير معينة:

مستلمو قاعدة إعادة توجيه:

- التحقق من صحة عنوان البريد الإلكتروني الوجهة ليس علبة بريد إضافية يملكها المستخدم نفسه (تجنب الحالات التي يقوم فيها المستخدم ب إعادة توجيه رسائل البريد الإلكتروني ذاتيا بين علب البريد الشخصية). 
- التحقق من صحة عنوان البريد الإلكتروني الوجهة ليس عنوانا داخليا أو مجالا فرعيا ينتمي إلى الشركة.

عوامل التصفية:
 
- إذا كانت قاعدة علبة الوارد تحتوي على عوامل تصفية تبحث عن كلمات أساسية معينة في موضوع البريد الإلكتروني أو النص الرئيسي له، فتحقق مما إذا كانت الكلمات الأساسية المتوفرة، مثل الشؤون المالية وبيانات الاعتماد والشبكات، من بين أمور أخرى، تبدو مرتبطة بنشاط ضار. يمكنك العثور على عوامل التصفية هذه ضمن السمات التالية (التي تظهر في العمود RawEventData الحدث): "BodyContainsWords" أو "SubjectContainsWords" أو "SubjectOrBodyContainsWords"
- إذا اختار المهاجم عدم تعيين أي عامل تصفية إلى رسائل البريد، وبدلا من ذلك، كانت قاعدة علبة الوارد ترسل كل عناصر علبة البريد إلى علبة بريد المهاجم)، فهذا السلوك مريبا أيضا. 

### <a name="investigate-ip-address"></a>التحقق من عنوان IP

راجع السمات المرتبطة عنوان IP الذي ينفذ الحدث ذي الصلة بإنشاء القاعدة:

1. ابحث عن الأنشطة السحابية المريبة الأخرى التي تم إنشاءها من نفس IP في المستأجر. على سبيل المثال، قد يكون النشاط المريب عدة محاولات فشل لتسجيل الدخول. 
2. هل ISP شائع ومعقول لهذا المستخدم؟
3. هل الموقع شائع ومعقول لهذا المستخدم؟

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>التحقق من أي نشاط مريب باستخدام علبة الوارد الخاصة بالمستخدم قبل إنشاء القواعد

يمكنك مراجعة كل أنشطة المستخدم قبل إنشاء القواعد والتحقق من وجود مؤشرات اختراق والتحقق من إجراءات المستخدم التي تبدو مريبا. على سبيل المثال، فشل تسجيل الدخول لعدة مرات.  

- تسجيل الدخول: 

  تحقق من أن نشاط تسجيل الدخول قبل حدث إنشاء القاعدة غير مريبا (مثل الموقع الشائع أو ISP أو عامل المستخدم). 

- تنبيهات أو أحداث أخرى 

   - هل تم تشغيل تنبيهات أخرى للمستخدم قبل إنشاء القاعدة. إذا كان الأمر كذلك، فقد يشير ذلك إلى أنه تم اختراق المستخدم. 

   - إذا كان التنبيه يرتبط بتنبيهات أخرى للإشارة إلى حادث، فهل يحتوي الحادث على تنبيهات إيجابية حقيقية أخرى؟ 

## <a name="advanced-hunting-queries"></a>استعلامات الصيد المتقدمة

[إن "الصيد المتقدم](advanced-hunting-overview.md) " هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك فحص الأحداث في شبكتك وتحديد موقع مؤشرات التهديدات. 

تشغيل هذا الاستعلام للعثور على كل أحداث قواعد علبة الوارد الجديدة خلال نافذة زمنية معينة.  

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

*ستحتوي RuleConfig* على تكوين القاعدة.

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان ISP شائعا للمستخدم بالنظر إلى محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان البلد شائعا للمستخدم من خلال الاطلاع على محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان وكيل المستخدم شائعا للمستخدم بالنظر إلى محفوظات المستخدم.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

قم بتشغيل هذا الاستعلام للتحقق مما إذا كان المستخدمون الآخرين قد أنشأوا قاعدة إعادة توجيه إلى الوجهة نفسها (قد يشير ذلك إلى أن المستخدمين الآخرين قد تم اختراقهم أيضا).

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

1. قم بتعطيل قاعدة علبة الوارد الضارة. 
2. إعادة تعيين بيانات اعتماد حساب المستخدم. يمكنك أيضا التحقق مما إذا تم اختراق حساب المستخدم باستخدام Microsoft Defender for Cloud Apps، الذي يحصل على إشارات الأمان من Azure Active Directory (Azure AD) Identity Protection.
3. ابحث عن الأنشطة الضارة الأخرى التي ينفذها المستخدم المتأثّر.
4. تحقق من أي نشاط مريب آخر في المستأجر تم إنشاءه من نفس IP أو من ISP نفسه (إذا كان ISP شائعا) للعثور على مستخدمين آخرين تم اختراقهم.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول تصنيف التنبيهات](alert-grading-playbooks.md)
- [نشاط إعادة توجيه البريد الإلكتروني المريب](alert-grading-playbook-email-forwarding.md)
- [قواعد معالجة علبة الوارد المريبة](alert-grading-playbook-inbox-manipulation-rules.md)
- [التحقق من التنبيهات](investigate-alerts.md)
