---
title: مركز حماية Microsoft Defender معلومات عمليات الأمان
description: استخدم لوحة المعلومات لتحديد الأجهزة المعرضة للمخاطر، وتعقب حالة الخدمة، وشاهد الإحصائيات والمعلومات حول الأجهزة والتنبيهات.
keywords: لوحة المعلومات والتنبيهات والتنبيهات الجديدة والمتقدمة والحل والمخاطر والأجهزة المعرضة للمخاطر والكشف عن الفيروسات والإبلاغ عنها والإحصاءات والمخططات والرسومات البيانية والصحة والكشف النشط عن البرامج الضارة وفئة المخاطر والفئات وسرقة كلمات المرور وفيروسات الفدية الضارة والاستغلال والمخاطر وانخفاض الخطورة والبرامج الضارة النشطة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c08f592ac72be10bb4b967521e7e504a9ae70a86
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472628"
---
# <a name="microsoft-defender-security-center-security-operations-dashboard"></a>مركز حماية Microsoft Defender معلومات عمليات الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-abovefoldlink)

لوحة **معلومات عمليات** الأمان هي المكان الذي يتم الكشف عن تهديدات نقاط النهاية والرد عليها فيه. ويوفر نظرة عامة عالية المستوى حول مكان رؤية الاكتشافات وتسليط الضوء على الحالات التي تحتاج فيها إلى إجراءات الاستجابة.

تعرض لوحة المعلومات لقطة من:

- التنبيهات النشطة
- الأجهزة المعرضة للمخاطر
- صحة المستشعر
- Service health
- إعداد تقارير الأجهزة اليومية
- عمليات التحقيق التلقائية النشطة
- إحصائيات التحريات التلقائية
- المستخدمون المعرضون للمخاطر
- الأنشطة المريبة

:::image type="content" source="images/atp-sec-ops-dashboard.png" alt-text="لوحة معلومات عمليات الأمان" lightbox="images/atp-sec-ops-dashboard.png":::

يمكنك استكشاف التنبيهات والأجهزة واستكشافها لتحديد ما إذا كان قد حدثت أنشطة مريبة في شبكتك وأين ومتى حدثت لمساعدتك على فهم السياق الذي ظهرت فيه.

من لوحة **معلومات عمليات** الأمان، سترى الأحداث المجمعة لتسهيل تحديد الأحداث أو السلوكيات الهامة على جهاز. يمكنك أيضا التنقل لأسفل في الأحداث والمؤشرات ذات المستوى المنخفض.

كما أنه به أيضا تجانبات قابلة للنقر فوقها تعطي مؤثرات مرئية حول حالة الصحة العامة لمنظمتك. تفتح كل لوحة طريقة عرض مفصلة لنظرة عامة مناظرة.

## <a name="active-alerts"></a>التنبيهات النشطة

يمكنك عرض العدد الإجمالي للتنبيهات النشطة من آخر 30 يوما في الشبكة من اللوحة. يتم تجميع التنبيهات في **جديد** و **في تقدم**.

:::image type="content" source="images/active-alerts-tile.png" alt-text="صفحة التنبيهات النشطة" lightbox="images/active-alerts-tile.png":::

يتم تصنيف كل مجموعة بشكل فرعي إلى مستويات خطورة التنبيهات المطابقة لها. انقر فوق عدد التنبيهات داخل كل حلقة تنبيه لرؤية طريقة عرض تم فرزها من قائمة انتظار تلك الفئة (**جديد** أو **في تقدم**).

لمزيد من المعلومات، راجع [نظرة عامة على التنبيهات](alerts-queue.md).

يتضمن كل صف فئة خطورة التنبيه ووصفا قصيرا للتنبيه. يمكنك النقر فوق تنبيه لرؤية طريقة العرض المفصلة الخاصة به. لمزيد من المعلومات، راجع [التحقق Microsoft Defender لنقطة النهاية التنبيهات](investigate-alerts.md) [والتنبيهات العامة](alerts-queue.md).

## <a name="devices-at-risk"></a>الأجهزة المعرضة للمخاطر

تعرض لك هذه اللوحة قائمة بالأجهزة التي تتضمن أكبر عدد من التنبيهات النشطة. يظهر العدد الإجمالي للتنبيهات لكل جهاز في دائرة بجانب اسم الجهاز، ثم يتم تصنيفها حسب مستويات الخطورة في أقصى نهاية اللوحة (مرر فوق كل شريط خطورة لرؤية تسميته).

:::image type="content" source="images/devices-at-risk-tile.png" alt-text="صفحة &quot;الأجهزة المعرضة للمخاطر&quot;" lightbox="images/devices-at-risk-tile.png":::

انقر فوق اسم الجهاز للاطلاع على تفاصيل حول هذا الجهاز. لمزيد من المعلومات، راجع [التحقق من الأجهزة في Microsoft Defender لنقطة النهاية الأجهزة](investigate-machines.md).

يمكنك أيضا النقر فوق قائمة **الأجهزة** في أعلى اللوحة للذهاب مباشرة إلى قائمة الأجهزة، التي تم فرزها حسب عدد التنبيهات النشطة. لمزيد من المعلومات، راجع [التحقق من الأجهزة في Microsoft Defender لنقطة النهاية الأجهزة](investigate-machines.md).

## <a name="devices-with-sensor-issues"></a>الأجهزة التي بها مشاكل في المستشعر

توفر **لوحة الأجهزة التي** بها مشاكل في المستشعر معلومات حول قدرة الجهاز الفردي على توفير بيانات المستشعر Microsoft Defender لنقطة النهاية الخدمة. فهي تقوم بلتقارير حول عدد الأجهزة التي تتطلب الانتباه وتساعدك على تحديد الأجهزة التي بها مشاكل.

:::image type="content" source="images/atp-tile-sensor-health.png" alt-text="لوحة &quot;الأجهزة التي بها مشاكل المستشعر&quot;" lightbox="images/atp-tile-sensor-health.png":::

هناك مؤشرا حالة يوفران معلومات حول عدد الأجهزة التي لا يتم إبلاغ الخدمة بها بشكل صحيح:

- **تكوين غير صحيح**: قد تقوم هذه الأجهزة بشكل جزئي بالإبلاغ عن بيانات المستشعر Microsoft Defender لنقطة النهاية الخدمة وقد تكون بها أخطاء تكوين يجب تصحيحها.
- **غير نشط**: الأجهزة التي توقفت عن Microsoft Defender لنقطة النهاية الخدمة لأكثر من سبعة أيام في الشهر الماضي.

عندما تنقر فوق أي من المجموعات، سيتم توجيهك إلى قائمة الأجهزة، وتصفيتها وفقا لاختيارك. لمزيد من المعلومات، راجع [التحقق من حالة المستشعر](check-sensor-status.md) [والتحقق من الأجهزة](investigate-machines.md).

## <a name="service-health"></a>Service health

**تطلعك Service health** اللوحة على ما إذا كانت الخدمة نشطة أو إذا كانت هناك مشاكل.

:::image type="content" source="images/status-tile.png" alt-text="الصفحة Service health" lightbox="images/status-tile.png":::

لمزيد من المعلومات حول صحة الخدمة، راجع [التحقق من Microsoft Defender لنقطة النهاية الخدمة](service-status.md).

## <a name="daily-devices-reporting"></a>إعداد تقارير الأجهزة اليومية

تعرض **لوحة إعداد التقارير** للأجهزة اليومية رسما بيانيا شريطيا يمثل عدد الأجهزة التي تبلغ يوميا في آخر 30 يوما. مرر فوق أشرطة فردية على الرسم البياني لمعرفة عدد الأجهزة التي يتم الإبلاغ عنها بشكل دقيق في كل يوم.

:::image type="content" source="images/atp-daily-devices-reporting.png" alt-text="لوحة إعداد التقارير للأجهزة اليومية" lightbox="images/atp-daily-devices-reporting.png":::

## <a name="active-automated-investigations"></a>عمليات التحقيق التلقائية النشطة

يمكنك عرض العدد الإجمالي للتحريات التلقائية من آخر 30 يوما في شبكتك من لوحة "عمليات التحقيق **التلقائية** النشطة". يتم تجميع التحريات في الإجراءات **المعلقة** **والانتظار للجهاز** **وتشغيله**.

:::image type="content" source="images/atp-active-investigations-tile.png" alt-text="عمليات البحث التلقائية النشطة" lightbox="images/atp-active-investigations-tile.png":::

## <a name="automated-investigations-statistics"></a>إحصائيات التحريات التلقائية

تعرض هذه اللوحة إحصائيات ذات صلة بالتباحثات التلقائية في الأيام السبعة الأخيرة. وهو يعرض عدد عمليات التحقيق المكتملة وعدد عمليات التحقيق التي تم إصلاحها بنجاح ومتوسط الوقت المعلق الذي يستغرقه بدء التحقيق ومتوسط الوقت المستغرق في معالجة تنبيه وعدد التنبيهات التي تم التحقق منها وعدد ساعات التنفيذ التلقائي التي تم حفظها من تحقيق يدوي نموذجي. 

:::image type="content" source="images/atp-automated-investigations-statistics.png" alt-text="إحصائيات الاختبارات التلقائية" lightbox="images/atp-automated-investigations-statistics.png":::

يمكنك النقر فوق عمليات التحقيق التلقائية، والتحريات التي تمت المعالجة، والتنبيهات التي تم التحقق فيها  للانتقال إلى صفحة "التحقيق"، التي تمت تصفيتها حسب الفئة المناسبة. يتيح لك هذا الأمر الاطلاع على تصنيف تفصيلي للتحريات في السياق.

## <a name="users-at-risk"></a>المستخدمون المعرضون للمخاطر

تعرض لك اللوحة قائمة حسابات المستخدمين مع التنبيهات الأكثر نشاطا وعدد التنبيهات التي تظهر على التنبيهات العالية أو المتوسطة أو المنخفضة. 

:::image type="content" source="images/atp-users-at-risk.png" alt-text="صفحة المستخدمون المعرضون للمخاطر" lightbox="images/atp-users-at-risk.png":::

انقر فوق حساب المستخدم للاطلاع على تفاصيل حول حساب المستخدم. لمزيد من المعلومات، راجع [التحقق من حساب مستخدم](investigate-user.md).

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-secopsdashboard-belowfoldlink)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [فهم Microsoft Defender لنقطة النهاية المدخل](use.md)
- [نظرة عامة على المدخل](portal-overview.md)
- [عرض لوحة معلومات إدارة & المخاطر](tvm-dashboard-insights.md)
- [عرض لوحة معلومات تحليل المخاطر واتخاذ إجراءات تخفيف الموصى بها](threat-analytics.md)
