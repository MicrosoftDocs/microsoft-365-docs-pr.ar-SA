---
title: التحقق من الأحداث في Microsoft Defender لنقطة النهاية
description: الاطلاع على التنبيهات المقترنة وإدارة الحادث ورؤية بيانات تعريف التنبيه لمساعدتك على التحقيق في حادث
keywords: التحقيق والحادث والتنبيهات والبيانات التعريفية والمخاطر ومصدر الكشف والأجهزة المتأثرة والأنماط والارتباط
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d66dde2c3f346449c7ecd03a7ef577e39cf98991
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468788"
---
# <a name="investigate-incidents-in-microsoft-defender-for-endpoint"></a>التحقق من الأحداث في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


تحقق من الأحداث التي تؤثر على شبكتك، وافهم معاناتها، وحقق في الأدلة لحلها.

عندما تحقق من حادث، سترى:

- تفاصيل الحادث
- تعليقات الأحداث والإجراءات
- علامات التبويب (التنبيهات، الأجهزة، التحقيقات، الدليل، الرسم البياني)

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUV]

## <a name="analyze-incident-details"></a>تحليل تفاصيل الحادث

انقر فوق حادث لرؤية جزء **الحادث**. حدد **فتح صفحة الحادث** لرؤية تفاصيل الحادث والمعلومات ذات الصلة (التنبيهات والأجهزة، التحقيق، الدليل، الرسم البياني).

:::image type="content" source="images/atp-incident-details.png" alt-text="تفاصيل حادث" lightbox="images/atp-incident-details.png":::

### <a name="alerts"></a>التنبيهات

يمكنك التحقق من التنبيهات ورؤية كيفية ربطها معا في حادث. يتم تجميع التنبيهات في أحداث استنادا إلى الأسباب التالية:

- التحقيق التلقائي - تم تشغيل التنبيه المرتبط أثناء التحقق من التنبيه الأصلي
- خصائص الملف - الملفات المقترنة بالتنبيه لها خصائص مماثلة
- اقتران يدوي - ربط التنبيهات يدويا من قبل مستخدم
- الوقت المتوقع - تم تشغيل التنبيهات على الجهاز نفسه ضمن إطار زمني معين
- الملف نفسه - الملفات المقترنة بالتنبيه هي نفسها تماما
- عنوان URL نفسه - عنوان URL الذي تسبب في تشغيل التنبيه هو نفسه تماما

:::image type="content" source="images/atp-incidents-alerts-reason.png" alt-text="تعرض علامة التبويب &quot;تنبيهات&quot; التي تحتوي على صفحة تفاصيل الحادث أسباب ربط التنبيهات معا في هذا الحادث" lightbox="images/atp-incidents-alerts-reason.png":::

يمكنك أيضا إدارة تنبيه لمشاهدة بيانات تعريف التنبيه بالإضافة إلى معلومات أخرى. لمزيد من المعلومات، راجع [التحقق من التنبيهات](investigate-alerts.md).

### <a name="devices"></a>الأجهزة

يمكنك أيضا التحقق من الأجهزة التي تكون جزءا من حادث معين أو ذات صلة به. لمزيد من المعلومات، راجع [التحقق من الأجهزة](investigate-machines.md).

:::image type="content" source="images/atp-incident-device-tab.png" alt-text="علامة التبويب &quot;الأجهزة&quot; في صفحة تفاصيل الحادث" lightbox="images/atp-incident-device-tab.png":::

### <a name="investigations"></a>التحقيق

حدد **"عمليات التحقيق** " لرؤية كل عمليات التحقيق التلقائية التي بدأها النظام استجابة لتنبيهات الحادث.

:::image type="content" source="images/atp-incident-investigations-tab.png" alt-text="علامة التبويب &quot;التحقيق&quot; في صفحة تفاصيل الحادث" lightbox="images/atp-incident-investigations-tab.png":::

## <a name="going-through-the-evidence"></a>المرور عبر الدليل

Microsoft Defender لنقطة النهاية التحقيق تلقائيا في كل الأحداث المدعومة للحوادث والكيانات المريبة في التنبيهات، مما يوفر لك ميزة "المسؤولية التلقائية" ومعلومات حول الملفات والعمليات والخدمات الهامة والمزيد.

سيتم وضع علامة على كل كيان من الوحدات التي تم تحليلها على أنها موبوءة أو تم إصلاحها أو مريبة.

:::image type="content" source="images/atp-incident-evidence-tab.png" alt-text="علامة التبويب &quot;دليل&quot; في صفحة تفاصيل الحادث" lightbox="images/atp-incident-evidence-tab.png":::

## <a name="visualizing-associated-cybersecurity-threats"></a>تمثيل تهديدات الأمن الإلكتروني المقترنة

Microsoft Defender لنقطة النهاية المعلومات المتعلقة بالخطر في حادث حتى تتمكن من رؤية الأنماط والارتباطات الواردة من نقاط بيانات مختلفة. يمكنك عرض هذا الارتباط من خلال رسم بياني للحادث.

### <a name="incident-graph"></a>رسم بياني للحوادث

تخبر **Graph** عن قصة هجوم الأمن الإلكتروني. على سبيل المثال، يعرض لك نقطة الإدخال، أي مؤشر اختراق أو نشاط تم ملاحظته على الجهاز. إلخ.

:::image type="content" source="images/atp-incident-graph-tab.png" alt-text="رسم بياني للحادث" lightbox="images/atp-incident-graph-tab.png":::

يمكنك النقر فوق الدوائر الموجودة في رسم الأحداث لعرض تفاصيل الملفات الضارة، واكتشافات الملفات المقترنة بها، وما هو عدد المثيلات الموجودة على مستوى العالم، وما إذا كان قد تم ملاحظتها في مؤسستك، إذا كان الأمر كذلك، عدد المثيلات.

:::image type="content" source="images/atp-incident-graph-details.png" alt-text="صفحة تفاصيل الحادث" lightbox="images/atp-incident-graph-details.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [قائمة انتظار الأحداث](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [التحقق من الأحداث في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/investigate-incidents)
- [إدارة Microsoft Defender لنقطة النهاية الأحداث](/microsoft-365/security/defender-endpoint/manage-incidents)
