---
title: التحقق من الأحداث في Microsoft 365 Defender
description: تحقق من الأحداث المتعلقة بالأجهزة والمستخدمين علب البريد.
keywords: حادث، أحداث، تحليل، استجابة، أجهزة، أجهزة، مستخدمين، هويات، بريد، بريد إلكتروني، علبة بريد، تحقيق، رسم بياني، دليل
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
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 776680db7b2666cc964f82e88cd6af9e6bab7558
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500244"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>التحقق من الأحداث في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

Microsoft 365 Defender تجميع جميع التنبيهات والأصول والتباحثات والأدلة ذات الصلة من جميع الأجهزة والمستخدمين علب البريد في حادث ما لتمنحك نظرة شاملة على كامل نطاق الهجوم.

في أي حادث، يمكنك تحليل التنبيهات التي تؤثر على شبكتك، وفهم معنيها، وتكاتف الدليل بحيث تتمكن من وضع خطة إصلاح فعالة.

## <a name="initial-investigation"></a>التحقيق الأولي

قبل الخوض في التفاصيل، أطلع على خصائص الحادث وملخصه.

يمكنك البدء بتحديد الحادث من عمود علامة الاختيار. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="تحديد حادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

عند القيام بذلك، يتم فتح جزء ملخص مع معلومات أساسية حول الحادث، مثل الخطورة، الشخص الذي تم تعيينه له، و [MITRE ATT&CK&trade;](https://attack.mitre.org/) للحادث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="الجزء الذي يعرض تفاصيل الملخص لحادث في Microsoft 365 Defender المدخل." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

من هنا، يمكنك تحديد **فتح صفحة الحادث**. يفتح هذا الصفحة الرئيسية للحادث حيث ستجد المزيد من المعلومات الموجزة و علامات التبويب الخاصة بالتنبيهات والأجهزة والمستخدمين والتحريات والأدلة.

يمكنك أيضا فتح الصفحة الرئيسية لحادث عن طريق تحديد اسم الحادث من قائمة انتظار الحادث.

## <a name="summary"></a>الملخص

توفر **لك صفحة** الملخص نظرة سريعة على أهم الأمور التي يجب ملاحظتها حول الحادث.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="المعلومات الموجزة لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

يتم تنظيم المعلومات في هذه الأقسام.

| مقطع | الوصف |
|:-------|:-----|
| التنبيهات والفئات | طريقة عرض مرئية رقمية حول مدى تقدم الهجوم مقابل سلسلة الاقتات. كما هو الأمر مع منتجات أمان Microsoft الأخرى، Microsoft 365 Defender إلى [إطار عمل MITRE ATT&CK&trade;](https://attack.mitre.org/). يعرض المخطط الزمني للتنبيهات الترتيب الزمني الذي حدثت به التنبيهات وبالنسبة لكل منها، حالة التنبيهات واسمها. |
| النطاق |  يعرض عدد الأجهزة والمستخدمين علب البريد التي تم التأثير عليها ويدرج الكيانات في ترتيب مستوى المخاطر بأولوية التحقيق. |
| الدليل | يعرض عدد الكيانات المتأثرة بالحادث. |
| معلومات الحادث | يعرض خصائص الحادث، مثل العلامات، الحالة، والخطورة. |
|||

استخدم صفحة **الملخص** لتقييم الأهمية النسبية للحادث والوصول بسرعة إلى التنبيهات المقترنة والكيانات ذات التأثير.

## <a name="alerts"></a>التنبيهات

على علامة **التبويب** تنبيهات، يمكنك عرض قائمة انتظار التنبيهات للتنبيهات ذات الصلة بالحادث ومعلومات أخرى حولها مثل:

- الخطورة.
- الوحدات التي كانت متدخلة في التنبيه.
- مصدر التنبيهات (Microsoft Defender for Identity و Microsoft Defender لنقطة النهاية و Microsoft Defender لـ Office 365 و Defender for Cloud Apps و الوظائف الإضافية الخاصة بحوكمة التطبيق).
- سبب ارتباطهما معا.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="جزء التنبيهات لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-alerts.png":::

بشكل افتراضي، يتم ترتيب التنبيهات بشكل زمني للسماح لك برؤية كيفية تنفيذ الهجوم مع مرور الوقت. عند تحديد تنبيه ضمن حادث، Microsoft 365 Defender عرض معلومات التنبيه الخاصة بسيااق الحادث الإجمالي. 

يمكنك رؤية أحداث التنبيه، التي تسببت التنبيهات المشغلة الأخرى في التنبيه الحالي، وجميع الكيانات والأنشطة المتأثرة بالهجمة، بما في ذلك الأجهزة والملفات والمستخدمين علب البريد.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="تفاصيل تنبيه ضمن حادث في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

تحتوي صفحة تنبيه الحادث على الأقسام التالية:

- قصة التنبيه، التي تتضمن:

   - ماذا حدث

   - الإجراءات التي تم اتخاذها

   - الأحداث ذات الصلة

- خصائص التنبيه في الجزء الأيمن (الحالة والتفاصيل والوصف وغيرها)

لن يكون لدى كل تنبيه كل الأقسام الفرعية المدرجة في **مقطع قصة** التنبيه.

تعرف على كيفية استخدام قائمة انتظار التنبيهات وصفحات التنبيه في [تنبيهات الاستقصاء](investigate-alerts.md).

## <a name="devices"></a>الأجهزة

**تسرد علامة** التبويب الأجهزة جميع الأجهزة ذات الصلة بالحادث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="صفحة الأجهزة لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-devices.png":::

يمكنك تحديد علامة الاختيار لجهاز ما لرؤية تفاصيل الجهاز وبيانات الدليل والتنبيهات النشطة والمستخدمين الذين سجلوا دخولهم. حدد اسم الجهاز لرؤية تفاصيل الجهاز في مخزون جهاز Defender for Endpoint. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="الصفحة ذات الصلة بخيار مخزون الجهاز في Microsoft Defender لنقطة النهاية." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

من صفحة الجهاز، يمكنك جمع معلومات إضافية حول الجهاز، مثل كل تنبيهاته وم يومياته وتوصيات الأمان. على سبيل المثال، من  علامة التبويب مخطط زمني، يمكنك التمرير عبر المخطط الزمني للجهاز وعرض كل الأحداث والسلوكيات التي تم ملاحظتها على الجهاز بترتيب زمني، تتقاطع مع التنبيهات التي تم رفعها.

> [!TIP]
> يمكنك إجراء عمليات فحص عند الطلب على صفحة جهاز. في مدخل Microsoft 365 Defender، اختر نقاط النهاية > **مخزون الجهاز**. حدد جهازا به تنبيهات، ثم قم بتشغيل فحص الحماية من الفيروسات. يتم تعقب الإجراءات، مثل عمليات مسح الفيروسات، وهي مرئية على **صفحة مخزون** الجهاز. لمعرفة المزيد، راجع [تشغيل مسح الحماية من الفيروسات ل Defender على الأجهزة](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>المستخدمون

**تسرد علامة** التبويب المستخدمون جميع المستخدمين الذين تم تحديدهم كجزء من الحادث أو مرتبطين به. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="صفحة المستخدمون في Microsoft 365 Defender المدخل." lightbox="../../media/investigate-incidents/incident-users.png":::

يمكنك تحديد علامة الاختيار للمستخدم لرؤية تفاصيل تهديدات حساب المستخدم والتعرض ومعلومات الاتصال. حدد اسم المستخدم لرؤية تفاصيل حساب مستخدم إضافية.

تعرف على كيفية عرض معلومات مستخدم إضافية وإدارة مستخدمي حادث في [التحقيق مع المستخدمين](investigate-users.md).


## <a name="mailboxes"></a>علب البريد

**تسرد علامة** التبويب علب البريد كل علب البريد التي تم تحديد أنها جزء من الحادث أو ذات صلة به. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="صفحة علب البريد لحادث في Microsoft 365 Defender المدخل." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

يمكنك تحديد علامة الاختيار لعلبة بريد لرؤية قائمة بالتنبيهات النشطة. حدد اسم علبة البريد لرؤية تفاصيل علبة البريد الإضافية على صفحة المستكشف Defender لـ Office 365.

## <a name="investigations"></a>التحقيق

**تسرد علامة التبويب** "عمليات التحقيق [](m365d-autoir.md)" كل عمليات التحقيق التلقائية التي تم تشغيلها بواسطة التنبيهات في هذا الحادث. ستؤدي عمليات التحقيق التلقائية إلى تنفيذ إجراءات إصلاحية أو انتظار موافقة المحلل على الإجراءات، استنادا إلى الطريقة التي قمت من خلالها بتكوين عمليات التحقيق التلقائية لتشغيلها في Defender for Endpoint Defender لـ Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="صفحة &quot;التحقيق&quot; لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-investigations.png":::

حدد التحقيق للانتقال إلى صفحة التفاصيل الخاصة به للحصول على معلومات كاملة حول حالة الإصلاح والتحري. إذا كانت هناك أي إجراءات معلقة للموافقة عليها كجزء من التحقيق، ستظهر في علامة التبويب محفوظات **الإجراءات المعلقة** . اتخاذ إجراء كجزء من معالجة الحادث.

هناك أيضا علامة **تبويب رسم بياني للتحري** تعرض:

- اتصال التنبيهات بالأصول التي تم التأثير عليها في مؤسستك.
- ما هي الكيانات المرتبطة بالتنبيهات وكيف أنها جزء من قصة الهجوم.
- تنبيهات الحادث.

يساعدك رسم التحقيق البياني على فهم النطاق الكامل للهجوم بسرعة من خلال توصيل الكيانات المريبة المختلفة التي تكون جزءا من الهجوم بأصولها ذات الصلة مثل المستخدمين والأجهزة علب البريد. 

لمزيد من المعلومات، راجع [إجراء التحقيق التلقائي والاستجابة في Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>الدليل والرد

تعرض **علامة التبويب** دليل والاستجابة كل الأحداث المدعومة والكيانات المريبة في التنبيهات في الحادث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="صفحة الدليل والرد لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender التحقق تلقائيا من كل الأحداث المدعومة للحوادث والكيانات المريبة في التنبيهات، مما يوفر لك معلومات حول رسائل البريد الإلكتروني والملفات والعمليات والخدمات وعناوين IP الهامة والمزيد. يساعدك ذلك على الكشف بسرعة عن التهديدات المحتملة في الحادث وحظرها.

يتم وضع علامة على كل كيان من الوحدات التي تم تحليلها بواسطة قرار (ضار، مريب، نظيف) وبوضع إصلاح. يساعدك ذلك على فهم حالة المعالجة للحادث بأكمله والخطوات التالية التي يمكن اتخاذها.

## <a name="graph-preview"></a>Graph (معاينة)

تعرض **Graph** علامة تبويب الفيديو النطاق الكامل للهجوم، وكيفية انتشار الهجوم عبر شبكتك مع مرور الوقت، ومن أين بدأ، والمدى الذي ذهب منه المهاجم. وهو يقوم بتوصيل الكيانات المريبة المختلفة التي تكون جزءا من الهجوم بأصولها ذات الصلة مثل المستخدمين والأجهزة علب البريد. 

من علامة **Graph**، يمكنك:

1. تشغيل التنبيهات والعقد على الرسم البياني عند حدوثها مع مرور الوقت لفهم التسلسل الزمني للهجوم.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="تشغيل التنبيهات والعقد على صفحة Graph":::
 

2. افتح جزء كيان، مما يسمح لك بمراجعة تفاصيل الكيان والعمل على إجراءات المعالجة، مثل حذف ملف أو عزل جهاز.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="جزء الكيان على صفحة Graph في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. تمييز التنبيهات استنادا إلى الكيان المرتبط بها.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="تمييز تنبيه على صفحة Graph" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>الخطوات التالية

حسب الحاجة:

- [التحقق من تنبيهات حادث](investigate-alerts.md)
- [التحقق من مستخدمي حادث](investigate-users.md)

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [تحديد أولوية الأحداث](incident-queue.md)
- [إدارة الأحداث](manage-incidents.md)
