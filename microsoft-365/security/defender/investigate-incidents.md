---
title: التحقيق في الحوادث في Microsoft 365 Defender
description: التحقيق في الحوادث المتعلقة بالأجهزة والمستخدمين وعلب البريد.
keywords: الحدث، والحوادث، والتحليل، والاستجابة، والأجهزة، والأجهزة، والمستخدمين، والهويات، والبريد، والبريد الإلكتروني، وعلبة البريد، والتحقيق، والرسم البياني، والأدلة
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
ms.openlocfilehash: 8138c07ab871ab1a6a8d89df980c914983bbb58e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666933"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>التحقيق في الحوادث في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

Microsoft 365 Defender تجميع جميع التنبيهات والأصول والتحقيقات والأدلة ذات الصلة من جميع أجهزتك والمستخدمين وعلب البريد في حادث لمنحك نظرة شاملة على النطاق الكامل للهجوم.

ضمن حادث ما، يمكنك تحليل التنبيهات التي تؤثر على شبكتك، وفهم ما تعنيه، وتجميع الأدلة حتى تتمكن من وضع خطة معالجة فعالة.

## <a name="initial-investigation"></a>التحقيق الأولي

قبل التعمق في التفاصيل، ألق نظرة على خصائص الحادث وملخصه.

يمكنك البدء بتحديد الحدث من عمود علامة الاختيار. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="تحديد حدث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

عند القيام بذلك، يفتح جزء ملخص مع معلومات أساسية حول الحادث، مثل الخطورة، لمن تم تعيينه له، وفئات [MITRE ATT&CK&trade;](https://attack.mitre.org/) للحدث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="الجزء الذي يعرض تفاصيل الملخص لحادث في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

من هنا، يمكنك تحديد **فتح صفحة الحدث**. يؤدي ذلك إلى فتح الصفحة الرئيسية للحادث حيث ستجد المزيد من المعلومات الموجزة وعلامات التبويب للتنبيهات والأجهزة والمستخدمين والتحقيقات والأدلة.

يمكنك أيضا فتح الصفحة الرئيسية لحدث ما عن طريق تحديد اسم الحدث من قائمة انتظار الحدث.

## <a name="summary"></a>الملخص

تمنحك صفحة **الملخص** نظرة سريعة على أهم الأشياء التي يجب ملاحظتها حول الحادث.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="المعلومات الموجزة لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

يتم تنظيم المعلومات في هذه الأقسام.

| قسم | الوصف |
|:-------|:-----|
| التنبيهات والفئات | طريقة عرض مرئية ورقمية لمدى تقدم الهجوم مقابل سلسلة القتل. كما هو الحال مع منتجات أمان Microsoft الأخرى، تتم محاذاة Microsoft 365 Defender مع إطار [عمل MITRE ATT&CK&trade;](https://attack.mitre.org/). يعرض المخطط الزمني للتنبيهات الترتيب الزمني الذي حدثت به التنبيهات ولكل حالة واسم. |
| نطاق |  يعرض عدد الأجهزة والمستخدمين وعلب البريد المتأثرة ويسرد الكيانات بترتيب مستوى المخاطر وأولوية التحقيق. |
| الادله | عرض عدد الكيانات المتأثرة بالحادث. |
| معلومات الحادث | يعرض خصائص الحدث، مثل العلامات والحالة والخطورة. |
|||

استخدم صفحة **الملخص** لتقييم الأهمية النسبية للحادث والوصول بسرعة إلى التنبيهات المرتبطة والكيانات المتأثرة.

## <a name="alerts"></a>التنبيهات

في علامة التبويب **«Alerts** »، يمكنك عرض قائمة انتظار التنبيه للتنبيهات المتعلقة بالحادث ومعلومات أخرى حولها مثل:

- شده.
- الكيانات التي شاركت في التنبيه.
- مصدر التنبيهات (Microsoft Defender for Identity، Microsoft Defender لنقطة النهاية، Microsoft Defender لـ Office 365، و Defender for Cloud Apps، والوظيفة الإضافية لإدارة التطبيقات).
- سبب ارتباطهما معا.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="جزء التنبيهات لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-alerts.png":::

بشكل افتراضي، يتم ترتيب التنبيهات ترتيبا زمنيا للسماح لك برؤية كيفية تشغيل الهجوم بمرور الوقت. عند تحديد تنبيه داخل حدث، Microsoft 365 Defender يعرض معلومات التنبيه الخاصة بسياق الحدث العام. 

يمكنك مشاهدة أحداث التنبيه، والتي تسببت فيها التنبيهات الأخرى التي تم تشغيلها في التنبيه الحالي، وجميع الكيانات والأنشطة المتأثرة التي ينطوي عليها الهجوم، بما في ذلك الأجهزة والملفات والمستخدمين وعلب البريد.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="تفاصيل تنبيه داخل حدث في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

تحتوي صفحة تنبيه الحادث على الأقسام التالية:

- قصة التنبيه، والتي تتضمن:

   - ماذا حدث

   - الإجراءات المتخذة

   - الأحداث ذات الصلة

- خصائص التنبيه في الجزء الأيمن (الحالة والتفاصيل والوصف وغيرها)

لن يحتوي كل تنبيه على جميع الأقسام الفرعية المدرجة في قسم **قصة التنبيه** .

تعرف على كيفية استخدام صف التنبيه وصفحات التنبيه في التحقيق في [التنبيهات](investigate-alerts.md).

## <a name="devices"></a>الاجهزه

تسرد علامة التبويب **"الأجهزة** " جميع الأجهزة المتعلقة بالحادث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="صفحة الأجهزة لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-devices.png":::

يمكنك تحديد علامة الاختيار لجهاز للاطلاع على تفاصيل الجهاز وبيانات الدليل والتنبيهات النشطة والمستخدمين الذين سجلوا دخولهم. حدد اسم الجهاز للاطلاع على تفاصيل الجهاز في مخزون جهاز Defender لنقطة النهاية. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="الصفحة المتعلقة بخيار مخزون الجهاز في Microsoft Defender لنقطة النهاية." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

من صفحة الجهاز، يمكنك جمع معلومات إضافية حول الجهاز، مثل جميع تنبيهاته، وجدول زمني، وتوصيات الأمان. على سبيل المثال، من علامة التبويب **"الخط الزمني** "، يمكنك التمرير عبر المخطط الزمني للجهاز وعرض جميع الأحداث والسلوكيات التي تمت ملاحظتها على الجهاز بترتيب زمني، يتقاطع مع التنبيهات التي تم رفعها.

> [!TIP]
> يمكنك إجراء عمليات فحص حسب الطلب على صفحة الجهاز. في مدخل Microsoft 365 Defender، اختر **نقاط النهاية > مخزون الجهاز**. حدد جهازا يحتوي على تنبيهات، ثم قم بتشغيل فحص مكافحة الفيروسات. يتم تعقب الإجراءات، مثل عمليات فحص مكافحة الفيروسات، وتكون مرئية على صفحة **مخزون الجهاز** . لمعرفة المزيد، راجع [فحص Run Defender Antivirus على الأجهزة](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>المستخدمون

تسرد علامة التبويب **"المستخدمون** " جميع المستخدمين الذين تم تعريفهم ليكونوا جزءا من الحدث أو مرتبطين به. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="صفحة المستخدمين في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

يمكنك تحديد علامة الاختيار لمستخدم للاطلاع على تفاصيل مخاطر حساب المستخدم والتعرض له ومعلومات الاتصال به. حدد اسم المستخدم للاطلاع على تفاصيل حساب المستخدم الإضافية.

تعرف على كيفية عرض معلومات إضافية للمستخدم وإدارة مستخدمي حدث في [التحقيق مع المستخدمين](investigate-users.md).


## <a name="mailboxes"></a>صناديق البريد

تسرد علامة التبويب **"علب البريد** " كافة علب البريد التي تم تعريفها لتكون جزءا من الحدث أو مرتبطة به. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="صفحة علب البريد لحدث في مدخل Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

يمكنك تحديد علامة الاختيار لعلبة بريد لعرض قائمة بالتنبيهات النشطة. حدد اسم علبة البريد للاطلاع على تفاصيل علبة البريد الإضافية على صفحة "المستكشف" Defender لـ Office 365.

## <a name="investigations"></a>التحقيقات

تسرد علامة التبويب **"التحقيقات** " جميع [التحقيقات التلقائية](m365d-autoir.md) التي تم تشغيلها بواسطة التنبيهات في هذا الحادث. ستقوم التحقيقات التلقائية بتنفيذ إجراءات المعالجة أو انتظار موافقة المحلل على الإجراءات، اعتمادا على كيفية تكوين التحقيقات التلقائية لتشغيلها في Defender لنقطة النهاية Defender لـ Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="صفحة التحقيقات لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-investigations.png":::

حدد التحقيق للانتقال إلى صفحة التفاصيل الخاصة به للحصول على معلومات كاملة حول حالة التحقيق والمعالجة. إذا كان هناك أي إجراءات معلقة للموافقة عليها كجزء من التحقيق، فستظهر في علامة تبويب **محفوظات الإجراءات المعلقة** . اتخاذ إجراء كجزء من معالجة الحادث.

هناك أيضا علامة تبويب **رسم بياني للتحقيق** تظهر:

- اتصال التنبيهات بالأصول المتأثرة في مؤسستك.
- الكيانات المرتبطة بالتنبيهات وكيفية أنها جزء من قصة الهجوم.
- التنبيهات الخاصة بالحادث.

يساعدك الرسم البياني للتحقيق على فهم النطاق الكامل للهجوم بسرعة من خلال ربط مختلف الكيانات المشبوهة التي تشكل جزءا من الهجوم بأصولها ذات الصلة مثل المستخدمين والأجهزة وعلب البريد. 

لمزيد من المعلومات، راجع [التحقيق التلقائي والاستجابة في Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>الأدلة والاستجابة

تعرض علامة التبويب **"دليل" و"استجابة** " جميع الأحداث المدعومة والكيانات المشبوهة في التنبيهات في الحدث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="صفحة الأدلة والاستجابة لحادث في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender التحقيق تلقائيا في جميع الأحداث المدعومة من الأحداث والكيانات المشبوهة في التنبيهات، ما يوفر لك معلومات حول رسائل البريد الإلكتروني والملفات والعمليات والخدمات وعناوين IP الهامة والمزيد. يساعدك هذا على الكشف بسرعة عن التهديدات المحتملة في الحادث وحظرها.

يتم وضع علامة على كل كيان من الكيانات التي تم تحليلها بحكم (ضار، مريب، نظيف) وحالة معالجة. يساعدك هذا على فهم حالة المعالجة للحادث بأكمله والخطوات التالية التي يمكن اتخاذها.

## <a name="graph-preview"></a>Graph (معاينة)

تظهر علامة تبويب **Graph** النطاق الكامل للهجوم، وكيفية انتشار الهجوم عبر شبكتك بمرور الوقت، ومن أين بدأ، وإلى أي مدى ذهب المهاجم. وهو يربط مختلف الكيانات المشبوهة التي تشكل جزءا من الهجوم بأصولها ذات الصلة مثل المستخدمين والأجهزة وعلب البريد. 

من علامة التبويب **Graph**، يمكنك:

1. قم بتشغيل التنبيهات والعقد على الرسم البياني كما حدثت بمرور الوقت لفهم ترتيب الهجوم.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="تشغيل التنبيهات والعقد على صفحة Graph":::
 

2. افتح جزء كيان، مما يسمح لك بمراجعة تفاصيل الكيان والعمل على إجراءات المعالجة، مثل حذف ملف أو عزل جهاز.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="جزء الكيان في صفحة Graph في مدخل Microsoft 365 Defender" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. قم بتمييز التنبيهات استنادا إلى الكيان المرتبط بها.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="تمييز تنبيه على صفحة Graph" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>الخطوات التالية

حسب الحاجة:

- [التحقيق في تنبيهات الحادث](investigate-alerts.md)
- [التحقيق في مستخدمي حدث](investigate-users.md)

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [تحديد أولوية الأحداث](incident-queue.md)
- [إدارة الأحداث](manage-incidents.md)
