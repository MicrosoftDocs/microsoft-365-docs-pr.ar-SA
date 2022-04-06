---
title: المخطط الزمني للحدث في إدارة المخاطر والثغرات الأمنية
description: إن المخطط الزمني للأحداث هو موجز أخبار المخاطر الذي يساعدك على تفسير كيفية تقديم المخاطر في المؤسسة، وما هي عمليات التخفيف التي تم تقليلها.
keywords: مخطط زمني للحدث، Microsoft Defender لنقطة النهاية زمني للحدث، Microsoft Defender لنقطة النهاية الزمني لحدث tvm، إدارة المخاطر والثغرات الأمنية، Microsoft Defender لنقطة النهاية
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 81c3a3a6d1d35551eec34d0fe12aba2f1fc6ec5e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469680"
---
# <a name="event-timeline---threat-and-vulnerability-management"></a>المخطط الزمني للحدث - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

إن المخطط الزمني للأحداث هو موجز أخبار المخاطر الذي يساعدك على تفسير كيفية تقديم المخاطر في المؤسسة من خلال نقاط الضعف الجديدة أو حالات استغلال جديدة. يمكنك عرض الأحداث التي قد تؤثر على مخاطر مؤسستك. على سبيل المثال، يمكنك العثور على نقاط الضعف الجديدة التي تم تقديمها، ونقاط الضعف التي أصبحت قابلة للاستغلال، واستغلال التي تم إضافتها إلى مجموعة أدوات استغلال، والمزيد.

يوضح المخطط الزمني للأحداث أيضا قصة نتيجة التعرض [](tvm-exposure-score.md) للضوء و"نقاط [Microsoft الآمنة](tvm-microsoft-secure-score-devices.md) للأجهزة" حتى تتمكن من تحديد سبب التغييرات الكبيرة. يمكن أن تؤثر الأحداث على أجهزتك أو على نقاطك للأجهزة. يمكنك تقليل التعرض عن طريق معالجة ما يجب معالجته استنادا إلى توصيات [الأمان ذات الأولوية](tvm-security-recommendation.md).

> [!TIP]
> للحصول على رسائل بريد إلكتروني حول أحداث ثغرة أمنية جديدة، راجع تكوين إعلامات البريد الإلكتروني للثغرات [الأمنية في Microsoft Defender لنقطة النهاية](configure-vulnerability-email-notifications.md)

## <a name="navigate-to-the-event-timeline-page"></a>الانتقال إلى صفحة المخطط الزمني للحدث

توجد أيضا ثلاث نقاط إدخال من لوحة إدارة المخاطر والثغرات الأمنية [التالية](tvm-dashboard-insights.md):

- **بطاقة نتيجة التعرض** للضوء في المؤسسة: مرر فوق نقاط الحدث في الرسم البياني "نقاط التعرض للضوء مع مرور الوقت" وحدد "مشاهدة كل الأحداث من هذا اليوم". تمثل الأحداث نقاط الضعف في البرامج.
- **Microsoft Secure Score للأجهزة**: مرر فوق نقاط الحدث في الرسم البياني "نقاطك للأجهزة مع مرور الوقت" وحدد "مشاهدة كل الأحداث من هذا اليوم". تمثل الأحداث تقييمات تكوين جديدة.
- **بطاقة الأحداث العليا**: حدد "إظهار المزيد" في أسفل جدول الأحداث العلوية. تعرض البطاقة الأحداث الثلاثة الأكثر تأثيرا في آخر 7 أيام. يمكن أن تتضمن الأحداث التأثيرية ما إذا كان الحدث يؤثر على عدد كبير من الأجهزة، أو إذا كان ثغرة أمنية هامة.

### <a name="exposure-score-and-microsoft-secure-score-for-devices-graphs"></a>درجة التعرض للضوء و"نقاط آمنة ل Microsoft" الرسوم البيانية للأجهزة

في لوحة إدارة المخاطر والثغرات الأمنية، مرر فوق الرسم البياني لنقاط التعرض للضوء لعرض أهم أحداث ثغرة البرامج منذ ذلك اليوم التي تؤثر على أجهزتك. مرر فوق رسم Microsoft Secure Score للأجهزة لعرض تقييمات تكوين الأمان الجديدة التي تؤثر على نقاطك.

إذا لم يكن هناك أي أحداث تؤثر على أجهزتك أو على نقاطك للأجهزة، لن يتم عرض أي منها.

:::image type="content" source="images/tvm-event-timeline-exposure-score350.png" alt-text="تمايض درجة التعرض للضوء" lightbox="images/tvm-event-timeline-exposure-score350.png":::
:::image type="content" source="images/tvm-event-timeline-device-hover360.png" alt-text="Microsoft Secure Score for Devices hover" lightbox="images/tvm-event-timeline-device-hover360.png":::

### <a name="drill-down-to-events-from-that-day"></a>التنقل لأسفل وصولا إلى الأحداث من ذلك اليوم

يأخذك **تحديد إظهار كل الأحداث من هذا اليوم** إلى صفحة المخطط الزمني للحدث مع نطاق تاريخ مخصص لذلك اليوم.

:::image type="content" source="images/tvm-event-timeline-drilldown.png" alt-text="صفحة المخطط الزمني للحدث" lightbox="images/tvm-event-timeline-drilldown.png":::

حدد **نطاق مخصص** لتغيير نطاق التاريخ إلى نطاق آخر مخصص، أو نطاق وقت معين مسبقا.

:::image type="content" source="images/tvm-event-timeline-dates.png" alt-text="خيارات نطاق تاريخ المخطط الزمني للحدث" lightbox="images/tvm-event-timeline-dates.png":::

## <a name="event-timeline-overview"></a>نظرة عامة على المخطط الزمني للحدث

في صفحة المخطط الزمني للحدث، يمكنك عرض كل المعلومات الضرورية ذات الصلة بحدث ما.

الميزات:

- تخصيص الأعمدة
- التصفية حسب نوع الحدث أو النسبة المئوية للأجهزة التي تم التأثير عليها
- عرض 30 أو 50 أو 100 عنصر لكل صفحة

يظهر العددان الكبيران في أعلى الصفحة عدد نقاط الضعف الجديدة والنقاط الأمنية القابلة للاستغلال، وليس الأحداث. قد يكون لبعض الأحداث نقاط ضعف متعددة، وقد يكون لبعض نقاط الضعف أحداث متعددة.

:::image type="content" source="images/tvm-event-timeline-overview-mixed-type.png" alt-text="المخطط الزمني للحدث" lightbox="images/tvm-event-timeline-overview-mixed-type.png":::

### <a name="columns"></a>أعمدة

- **التاريخ**: الشهر، اليوم، السنة
- **الحدث**: حدث تأثير، بما في ذلك مكون الأجهزة التي تم التأثير عليها ونوعها وعددها
- **المكون ذو الصلة**: البرنامج
- **الأجهزة التي تم التأثير عليها في** الأصل: عدد الأجهزة التي تم التأثير عليها والنسبة المئوية لها عند حدوث هذا الحدث في الأصل. يمكنك أيضا التصفية حسب النسبة المئوية للأجهزة التي تم التأثير عليها في الأصل، من إجمالي عدد الأجهزة.
- **الأجهزة التي تم التأثير عليها حاليا**: العدد الحالي والنسبة المئوية للأجهزة التي يؤثر عليها هذا الحدث حاليا. يمكنك العثور على هذا الحقل عن طريق تحديد **تخصيص الأعمدة**.
- **الأنواع**: تعكس الأحداث ذات الطابع الزمني التي تؤثر على النتيجة. يمكن تصفيتها.
  - استغلال مضاف إلى مجموعة أدوات استغلال
  - تم التحقق من استغلال
  - استغلال عام جديد
  - ثغرة أمنية جديدة
  - تقييم تكوين جديد
- **اتجاه الدرجة**: اتجاه درجة التعرض للضوء

### <a name="icons"></a>الأيقونات

تظهر الأيقونات التالية بجانب الأحداث:

- ![أيقونة الخطأ.](images/tvm-black-bug-icon.png) استغلال عام جديد
- ![أيقونة تحذير التقرير.](images/report-warning-icon.png) تم نشر ثغرة أمنية جديدة
- ![مجموعة أدوات استغلال.](images/bug-lightning-icon2.png) استغلال تم العثور عليه في مجموعة أدوات استغلال
- ![أيقونة الخطأ مع أيقونة التحذير.](images/bug-caution-icon2.png) استغلال متحقق منه

### <a name="drill-down-to-a-specific-event"></a>التنقل لأسفل وصولا إلى حدث معين

بمجرد تحديد حدث، ستظهر قائمة منسدة مع قائمة بالتفاصيل وأجهزة الكمبيوتر الشخصية الحالية التي تؤثر على أجهزتك. يمكنك إظهار المزيد من CVEs أو عرض التوصية ذات الصلة.

يساعدك السهم أسفل "اتجاه الدرجة" في تحديد ما إذا كان من المحتمل أن يكون هذا الحدث قد رفع درجة التعرض في المؤسسة أو خفضها. يعني ارتفاع درجة التعرض للضوء أن الأجهزة أكثر عرضة للاستغلال.

:::image type="content" source="images/tvm-event-timeline-flyout500.png" alt-text="من حولاء المخطط الزمني للحدث" lightbox="images/tvm-event-timeline-flyout500.png":::

من هناك، **حدد الانتقال إلى عرض توصيات الأمان** ذات الصلة بالتوصية التي تعالج ثغرة البرامج الجديدة في [صفحة توصيات الأمان](tvm-security-recommendation.md). بعد قراءة تفاصيل الوصف والضعف في توصية الأمان، يمكنك إرسال طلب إصلاح، وتعقب الطلب في [صفحة المعالجة](tvm-remediation.md).

## <a name="view-event-timelines-in-software-pages"></a>عرض المخططات الزمنية للأحداث في صفحات البرامج

لفتح صفحة برنامج، حدد حدثا > اسم البرنامج المرتبط تشعبيا (مثل Visual Studio 2017) في المقطع المسمى "المكون المرتبط" في عنصر منتحل. [معرفة المزيد حول صفحات البرامج](tvm-software-inventory.md#software-pages)

ستظهر صفحة كاملة مع كل تفاصيل برنامج معين. مرر الماوس فوق الرسم البياني لرؤية المخطط الزمني للأحداث لهذا البرنامج المحدد.

:::image type="content" source="images/tvm-event-timeline-software2.png" alt-text="صفحة البرنامج التي تحتوي على مخطط زمني للحدث" lightbox="images/tvm-event-timeline-software2.png":::

انتقل إلى علامة تبويب المخطط الزمني للحدث لعرض كل الأحداث ذات الصلة بهذا البرنامج. يمكنك أيضا الاطلاع على توصيات الأمان ونقاط الضعف المكتشفة والأجهزة المثبتة وتوزيع الإصدار.

:::image type="content" source="images/tvm-event-timeline-software-pages.png" alt-text="صفحة البرنامج التي تحتوي على علامة تبويب المخطط الزمني للحدث" lightbox="images/tvm-event-timeline-software-pages.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [لوحة المعلومات](tvm-dashboard-insights.md)
- [درجة التعرض للضوء](tvm-exposure-score.md)
- [توصيات الأمان](tvm-security-recommendation.md)
- [إصلاح الثغرات](tvm-remediation.md)
- [مخزون البرامج](tvm-software-inventory.md)
