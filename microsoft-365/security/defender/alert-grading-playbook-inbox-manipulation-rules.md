---
title: تصنيف التنبيه لقواعد معالجة علبة الوارد المريبة
description: تصنيف التنبيه لقواعد معالجة علبة الوارد المريبة لمراجعة التنبيهات واتخاذ الإجراءات الموصى بها لإعادة معالجة الهجوم وحماية شبكتك.
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
ms.openlocfilehash: 89d068feb5051a72e7592b7ea365b2e253e35115
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583792"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>تصنيف التنبيه لقواعد معالجة علبة الوارد المريبة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن لممثلي التهديدات استخدام حسابات المستخدمين المخادعة للعديد من الأغراض الضارة بما في ذلك قراءة رسائل البريد الإلكتروني في علبة الوارد الخاصة للمستخدم وإنشاء قواعد علبة الوارد إعادة توجيه رسائل البريد الإلكتروني إلى حسابات خارجية وحذف عمليات التتبع وإرسال رسائل التصيد الاحتيالي. قواعد علبة الوارد الضارة شائعة أثناء اختراق البريد الإلكتروني للأعمال وحملات التصيد الاحتيالي ومن المهم مراقبتها باستمرار. 

يساعدك هذا المصنف على التحقق من أي حادث يتعلق بقواعد معالجة علبة الوارد المريبة التي قام المهاجمون بتكوينها واتخاذ الإجراءات الموصى بها لإعادة معالجة الهجوم وحماية شبكتك. يتم تشغيل هذا المصنف لفرق الأمان، بما في ذلك محللي مركز عمليات الأمان (SOC) ومديري تكنولوجيا المعلومات الذين يراجعون التنبيهات ويتحققون منها ويدرجونها. يمكنك بسرعة تقدير التنبيهات على أنها True Positive (TP) أو False Positive (TP) واتخاذ الإجراءات الموصى بها لتنبيهات TP لإعادة معالجة الهجوم. 

نتائج استخدام هذا المصنف هي:

- لقد حددت التنبيهات المقترنة بقواعد معالجة علبة الوارد كالأنشطة الضارة (TP) أو الأنشطة الضارة (FP).

  إذا كانت ضارة، قمت بإزالة قواعد معالجة علبة الوارد الضارة.

- لقد اتخذت الإجراء اللازم إذا تم إعادة توجيه رسائل البريد الإلكتروني إلى عنوان بريد إلكتروني ضار.

## <a name="inbox-manipulation-rules"></a>قواعد معالجة علبة الوارد

يتم تعيين قواعد علبة الوارد لإدارة رسائل البريد الإلكتروني تلقائيا استنادا إلى معايير محددة مسبقا. على سبيل المثال، يمكنك إنشاء قاعدة علبة وارد لنقل كل الرسائل من المدير إلى مجلد آخر، أو إعادة توجيه الرسائل التي تتلقاها إلى عنوان بريد إلكتروني آخر.

### <a name="malicious-inbox-manipulation-rules"></a>قواعد معالجة علبة الوارد الضارة

قد يقوم المتطفلون بإعداد قواعد البريد الإلكتروني لإخفاء رسائل البريد الإلكتروني الواردة في علبة بريد المستخدم التي تم اختراقها لحجب أنشطتهم الضارة عن المستخدم. وقد يقوم أيضا بتعيين القواعد في علبة بريد المستخدم التي تم اختراقها لحذف رسائل البريد الإلكتروني، أو نقل رسائل البريد الإلكتروني إلى مجلد آخر أقل وضوحا (مثل RSS)، أو إعادة توجيه رسائل البريد إلى حساب خارجي. قد تؤدي بعض القواعد إلى نقل كل رسائل البريد الإلكتروني إلى مجلد آخر وتمييزها على أنها "قراءة"، بينما قد تحرك بعض القواعد رسائل البريد التي تحتوي على كلمات أساسية معينة فقط في رسالة البريد الإلكتروني أو الموضوع. 

على سبيل المثال، قد يتم تعيين قاعدة علبة الوارد للبحث عن كلمات أساسية مثل "فاتورة" أو "تصيد احتيالي" أو "عدم الرد" أو "بريد إلكتروني مريب" أو "بريد عشوائي" من بين كلمات أخرى، ثم نقلها إلى حساب بريد إلكتروني خارجي. قد يستخدم المتطفلون أيضا علبة بريد المستخدم التي تم اختراقها لتوزيع البريد العشوائي أو رسائل البريد الإلكتروني التصيد الاحتيالي أو البرامج الضارة. 

## <a name="workflow"></a>سير العمل

إليك سير العمل لتحديد أنشطة قواعد معالجة علبة الوارد المريبة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="تنبيه سير عمل التحقيق لقواعد معالجة علبة الوارد" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::


## <a name="investigation-steps"></a>خطوات التحقيق

يحتوي هذا القسم على إرشادات مفصلة خطوة بخطوة للاستجابة للحادث واتخاذ الخطوات الموصى بها لحماية مؤسستك من الهجمات الأخرى.

### <a name="1-review-the-alerts"></a>1. مراجعة التنبيهات

فيما يلي مثال على تنبيه قاعدة معالجة علبة الوارد في قائمة انتظار التنبيهات.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="مثال لقاعدة معالجة علبة الوارد" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

فيما يلي مثال التفاصيل الخاصة بتنبيه تم تشغيله بواسطة قاعدة معالجة علبة وارد ضارة.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="تفاصيل التنبيه الذي تم تشغيله بواسطة قاعدة معالجة علبة الوارد الضارة" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::


### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. التحقق من معلمات قاعدة معالجة علبة الوارد 

تحديد ما إذا كانت القواعد تبدو مريبة وفقا لمعلمات القواعد أو المعايير التالية:

- الكلمات الأساسية

   قد يطبق المهاجم قاعدة المعالجة فقط على رسائل البريد الإلكتروني التي تحتوي على كلمات معينة. يمكنك العثور على هذه الكلمات الأساسية ضمن سمات معينة مثل: "BodyContainsWords" أو "SubjectContainsWords" أو "SubjectOrBodyContainsWords". 

   إذا كانت هناك تصفية حسب الكلمات الأساسية، فتحقق مما إذا كانت الكلمات الأساسية تبدو مريبة بالنسبة لك (السيناريوهات الشائعة هي تصفية رسائل البريد الإلكتروني ذات الصلة بأنشطة المتطفلين، مثل "التصيد الاحتيالي" و"البريد العشوائي" و"عدم الرد"، من بين أمور أخرى).

   إذا لم يكن هناك أي عامل تصفية على الإطلاق، فقد يكون مريبا أيضا.

- مجلد الوجهة

   للتجنب من الكشف عن الأمان، قد يحرك المهاجم رسائل البريد الإلكتروني إلى مجلد أقل وضوحا وي وضع علامة على رسائل البريد الإلكتروني كمقرأة (على سبيل المثال، مجلد "RSS"). إذا قام المهاجم بتطبيق الإجراء "MoveToFolder" و"MarkAsRead"، فتحقق مما إذا كان المجلد الوجهة مرتبطا بشكل ما بالكلمات الأساسية في القاعدة لتحديد ما إذا كان يبدو مريبا أم لا. 

- حذف الكل

   سيحذف بعض المهاجمين كل رسائل البريد الإلكتروني الواردة لإخفاء نشاطهم. في الغالب، القاعدة "حذف كل رسائل البريد الإلكتروني الواردة" دون تصفيتها باستخدام الكلمات الأساسية هي مؤشر لنشاط ضار. 
 
فيما يلي مثال لتكوين قاعدة "حذف كل رسائل البريد الإلكتروني الواردة" (كما هو مشاهد في RawEventData.Parameters) من سجل الأحداث ذي الصلة. 

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="مثال على حذف كل تكوين قاعدة رسائل البريد الإلكتروني الواردة" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::


### <a name="3-investigate-the-ip-address"></a>3. التحقق من عنوان IP

راجع سمات عنوان IP الذي ينفذ الحدث ذي الصلة بإنشاء القاعدة:

- ابحث عن الأنشطة السحابية المريبة الأخرى التي تم إنشاءها من نفس IP في المستأجر. على سبيل المثال، قد يكون النشاط المريب عدة محاولات فشل لتسجيل الدخول. 
- هل ISP شائع ومعقول لهذا المستخدم؟
- هل الموقع شائع ومعقول لهذا المستخدم؟

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. التحقق من النشاط المريب من قبل المستخدم قبل إنشاء القواعد

يمكنك مراجعة كل أنشطة المستخدمين قبل إنشاء القواعد والتحقق من وجود مؤشرات اختراق والتحقق من إجراءات المستخدم التي تبدو مريبا. 

على سبيل المثال، بالنسبة إلى عمليات تسجيل الدخول المتعددة الفاشلة، افحص: 

- نشاط تسجيل الدخول 

   تحقق من أن نشاط تسجيل الدخول قبل إنشاء القاعدة غير مريبا. (الموقع الشائع / ISP / user-agent). 

- التنبيهات

   تحقق مما إذا كان المستخدم قد تلقى تنبيهات قبل إنشاء القواعد. قد يشير ذلك إلى أنه قد يتم اختراق حساب المستخدم. على سبيل المثال، تنبيه السفر المستحيل، البلد غير المتواف، عمليات تسجيل الدخول المتعددة الفاشلة، من بين أمور أخرى.)

- حادث

   تحقق مما إذا كان التنبيه مقترن بتنبيهات أخرى تشير إلى حادث. إذا كان الأمر كذلك، فتحقق مما إذا كان الحادث يحتوي على تنبيهات إيجابية حقيقية أخرى.

## <a name="advanced-hunting-queries"></a>استعلامات الصيد المتقدمة

[إن "الصيد المتقدم](advanced-hunting-overview.md) " هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك فحص الأحداث في شبكتك لتحديد موقع مؤشرات التهديدات. 

استخدم هذا الاستعلام للعثور على كل أحداث قواعد علبة الوارد الجديدة أثناء نافذة زمنية معينة.  

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

سيوفر *العمود RuleConfig* تكوين قاعدة علبة الوارد الجديدة.

استخدم هذا الاستعلام للتحقق مما إذا كان ISP شائعا للمستخدم بالنظر إلى محفوظات المستخدم.

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

استخدم هذا الاستعلام للتحقق مما إذا كان وكيل المستخدم شائعا للمستخدم بالنظر إلى محفوظات المستخدم.

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

1. قم بتعطيل قاعدة علبة الوارد الضارة.
2. إعادة تعيين بيانات اعتماد حساب المستخدم. يمكنك أيضا التحقق مما إذا تم اختراق حساب المستخدم باستخدام Microsoft Defender for Cloud Apps، الذي يحصل على إشارات الأمان من Azure Active Directory (Azure AD) Identity Protection.
3. ابحث عن أنشطة ضارة أخرى يتم تنفيذها بواسطة حساب المستخدم المتأثّر.
4. تحقق من أي نشاط مريب آخر في المستأجر تم إنشاءه من نفس IP أو من ISP نفسه (إذا كان ISP شائعا) للعثور على حسابات مستخدمين أخرى تم اختراقها.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول تصنيف التنبيهات](alert-grading-playbooks.md)
- [نشاط إعادة توجيه البريد الإلكتروني المريب](alert-grading-playbook-email-forwarding.md)
- [قواعد إعادة توجيه علبة الوارد المريبة](alert-grading-playbook-inbox-forwarding-rules.md)
- [التحقق من التنبيهات](investigate-alerts.md)
