---
title: خريطة تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين التعرف على كيفية استخدام خريطة تدفق البريد في لوحة معلومات تدفق البريد في مركز توافق الأمان & لتصور وتعقب كيفية تدفق البريد إلى المؤسسة وإخرا منها عبر الموصلات وبدون استخدام الموصلات.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd8df34c9484b7a2b8aa2bdd57d160e22f71d247
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473794"
---
# <a name="mail-flow-map-in-the-security--compliance-center"></a>خريطة تدفق البريد في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

توفر **خريطة تدفق** البريد في لوحة [](mail-flow-insights-v2.md) معلومات تدفق البريد في [مركز](https://protection.office.com) & الأمان معلومات حول كيفية تدفق البريد عبر مؤسستك. يمكنك استخدام هذه المعلومات للتعرف على الأنماط وتحديد حالات الشذوذ وإصلاح المشاكل عند حدوثها.

:::image type="content" source="../../media/mfi-mail-flow-map-widget.png" alt-text="عنصر واجهة مستخدم خريطة تدفق البريد في لوحة معلومات تدفق البريد في مركز & الأمان" lightbox="../../media/mfi-mail-flow-map-widget.png":::

بشكل افتراضي، يعرض عنصر واجهة المستخدم نمط تدفق البريد من اليوم السابق في مخطط يعرف بالرسم التخطيطي *Sankey* . يمكنك استخدام سهم لليسار ![لليسار.](../../media/scc-left-arrow.png) وسهم لليمين ![لعرض](../../media/scc-right-arrow.png) المعلومات من أيام مختلفة. يمثل كل لون مختلف تدفق البريد عبر موصل آخر وارد أو الصادر (أو بدون استخدام الموصلات). إذا مرر فوق لون معين، يتم عرض عدد الرسائل لهذا النوع من الموصلات.

## <a name="report-view-for-the-mail-flow-map"></a>طريقة عرض التقرير لخريطة تدفق البريد

يؤدي النقر فوق عنصر واجهة مستخدم **خريطة تدفق** البريد إلى نقلك إلى **تقرير خريطة تدفق** البريد.

تتوفر المخططات التالية في طريقة عرض التقرير:

- **إظهار البيانات ل: نظرة عامة**: هذه طريقة عرض أكبر من عنصر واجهة المستخدم بشكل أساسي. إذا مرر فوق لون معين، يتم عرض عدد الرسائل لهذا النوع من الموصلات.

    :::image type="content" source="../../media/mfi-mail-flow-map-report-overview.png" alt-text="طريقة العرض &quot;نظرة عامة&quot; في تقرير خريطة تدفق البريد" lightbox="../../media/mfi-mail-flow-map-report-overview.png":::

- **إظهار البيانات ل: التفاصيل**: تعرض طريقة العرض هذه تفاصيل حول الموصلات ومجالات الوجهة. يتم سرد أهم مجالات المرسل والمستلم، والباقي في **مجالات أخرى**. إذا مرر فوق لون وقسم معينين، يتم عرض عدد الرسائل.

    :::image type="content" source="../../media/mfi-mail-flow-map-report-detail.png" alt-text="طريقة العرض &quot;تفاصيل&quot; في تقرير خريطة تدفق البريد" lightbox="../../media/mfi-mail-flow-map-report-detail.png":::

إذا نقرت فوق **عوامل التصفية** في طريقة عرض التقرير، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

لبريد التقرير عبر البريد الإلكتروني لنطاق تاريخ معين لمستلم واحد أو أكثر، انقر فوق **طلب التنزيل**.

يتم عرض الرؤى ذات الصلة أسفل خريطة تدفق البريد إذا كانت متوفرة (على سبيل المثال، إصلاح إمكانية معرفة حلقة [البريد](mfi-mail-loop-insight.md).

## <a name="details-table-view-for-the-mail-flow-map"></a>طريقة عرض جدول التفاصيل لخريطة تدفق البريد

إذا نقرت **فوق عرض جدول التفاصيل** في طريقة عرض التقرير، يتم عرض المعلومات التالية:

- **التاريخ**
- **الفئة**
- **موصل / موفر خدمة جهة خارجية**
- **مجال المرسل/المستلم**
- **عدد الرسائل**

إذا نقرت فوق **عوامل التصفية** في طريقة عرض جدول التفاصيل، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

إذا حددت صفا، يتم عرض تفاصيل مماثلة في مجموعة من المعلومات:

:::image type="content" source="../../media/mfi-mail-flow-map-view-details-table-details.png" alt-text="القائمة المنسابة التفاصيل من جدول التفاصيل في خريطة تدفق البريد" lightbox="../../media/mfi-mail-flow-map-view-details-table-details.png":::

لبريد التقرير عبر البريد الإلكتروني لنطاق تاريخ معين لمستلم واحد أو أكثر، انقر فوق **طلب التنزيل**.

للعودة إلى طريقة عرض التقارير، انقر فوق **عرض التقرير**.

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
