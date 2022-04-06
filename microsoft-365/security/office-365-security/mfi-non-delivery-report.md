---
title: تقرير بعدم التسليم في لوحة معلومات تدفق البريد
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
description: يمكن للمسؤولين معرفة كيفية استخدام تقرير تفاصيل عدم التسليم في لوحة معلومات تدفق البريد في مركز توافق الأمان & لمراقبة رموز الخطأ الأكثر شيوعا في تقارير عدم التسليم (المعروفة أيضا بالتقارير بعدم التسليم أو رسائل البريد المرتد) من المرسلين في مؤسستك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bc408f6bb28b11e77c49755b888c44e0ea4d9f57
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473728"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>تقرير بعدم التسليم في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يعرض  تقرير عدم التسليم في لوحة معلومات [](mail-flow-insights-v2.md) تدفق البريد [في مركز](https://protection.office.com) توافق الأمان & رموز الأخطاء الأكثر مصادفة في تقارير عدم التسليم (المعروفة أيضا بالتقارير بعدم التسليم أو رسائل البريد المرتد) للمستخدمين في مؤسستك. يعرض هذا التقرير تفاصيل التقارير غير التسليمية حتى تتمكن من استكشاف مشاكل تسليم البريد الإلكتروني وإصلاحها.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير عدم التسليم في لوحة معلومات تدفق البريد في مركز & الأمان" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>طريقة عرض التقرير للتقرير بعدم التسليم

يؤدي النقر **فوق عنصر واجهة** مستخدم تقرير عدم التسليم إلى أخذك إلى **تقرير عدم التسليم**.

بشكل افتراضي، يتم عرض نشاط كل رموز الأخطاء. إذا نقرت **فوق إظهار البيانات ل**، يمكنك تحديد رمز خطأ معين من المنسدلة.

إذا مرر فوق لون معين (رمز الخطأ) في يوم معين في المخطط، سترى العدد الإجمالي للرسائل الخاصة بالخطأ.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="طريقة عرض التقرير في تقرير المجال غير المقبول" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>طريقة عرض جدول التفاصيل للتقرير بعدم التسليم

إذا نقرت **فوق عرض جدول التفاصيل** في طريقة عرض التقرير، يتم عرض المعلومات التالية:

- **التاريخ**
- **رمز تقرير بعدم التسليم**
- **Count**
- **نموذج للرسائل**: هويات الرسالة لعينة من الرسائل المتأثرة.

إذا نقرت فوق **عوامل التصفية** في طريقة عرض جدول التفاصيل، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

لبريد التقرير عبر البريد الإلكتروني لنطاق تاريخ معين لمستلم واحد أو أكثر، انقر فوق **طلب التنزيل**.

عندما تحدد صفا في الجدول، تظهر من خلال المعلومات التالية:

- **التاريخ**
- **رمز التقرير بعدم التسليم**: يمكنك النقر فوق الارتباط للعثور على مزيد من المعلومات حول أسباب رمز الخطأ المحدد وحلوله.
- **Count**
- **نموذج للرسائل**: يمكنك النقر فوق **عرض الرسائل العينة** للاطلاع على نتائج [تتبع](message-trace-scc.md) الرسائل لعينة من الرسائل المتأثرة.


:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="من حولي التفاصيل بعد تحديد صف في طريقة عرض جدول التفاصيل في تقرير عدم التسليم" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
