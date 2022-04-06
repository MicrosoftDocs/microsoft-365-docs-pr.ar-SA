---
title: تقرير مجال غير مقبول في لوحة معلومات تدفق البريد
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
description: يمكن للمسؤولين التعرف على كيفية استخدام تقرير المجال غير المقبول في لوحة معلومات تدفق البريد في مركز توافق الأمان & لمراقبة الرسائل الواردة من مؤسستك المحلي حيث لم يتم تكوين مجال المرسل في Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 25a8b1adb882aa83861e936d48534fc0a5f826e4
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679665"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>تقرير مجال غير مقبول في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يعرض  تقرير المجال غير المقبول في لوحة معلومات [](mail-flow-insights-v2.md) تدفق البريد في مركز توافق الأمان [&](https://protection.office.com) معلومات حول الرسائل الواردة من مؤسسة البريد الإلكتروني التي لم يتم تكوين مجال المرسل فيها كمجال مقبول في مؤسستك Microsoft 365.

Microsoft 365 هذه الرسائل إذا كانت لدينا بيانات لإثبات أن الهدف من هذه الرسائل ضار. وبالتالي، من المهم أن تفهم ما يحدث وتصلح المشكلة.

![عنصر واجهة مستخدم المجال غير المقبول في لوحة معلومات تدفق البريد في مركز & الأمان.](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a>طريقة عرض التقرير الخاصة تقرير المجال غير المقبول

يؤدي النقر فوق المخطط **على عنصر واجهة** مستخدم المجال غير المقبول إلى أخذك إلى تقرير **المجال غير** المقبول.

بشكل افتراضي، يتم عرض نشاط كل الموصلات المتأثرة. إذا نقرت **فوق إظهار البيانات ل**، يمكنك تحديد موصل معين من المنسدلة.

إذا مرر فوق نقطة بيانات (يوم) في المخطط، سترى العدد الإجمالي للرسائل للموصل.

![طريقة عرض التقرير في تقرير المجال غير المقبول.](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>طريقة عرض جدول التفاصيل الخاصة بتقرير المجال غير المقبول

إذا نقرت **فوق عرض جدول التفاصيل** في طريقة عرض التقرير، يتم عرض المعلومات التالية:

- **التاريخ**
- **اسم الموصل الوارد**
- **مجال المرسل**
- **عدد الرسائل**
- **نموذج للرسائل**: هويات الرسالة لعينة من الرسائل المتأثرة.

إذا نقرت فوق **عوامل التصفية** في طريقة عرض جدول التفاصيل، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

لبريد التقرير عبر البريد الإلكتروني لنطاق تاريخ معين لمستلم واحد أو أكثر، انقر فوق **طلب التنزيل**.

عندما تحدد صفا في الجدول، تظهر من خلال المعلومات التالية:

- **التاريخ**
- **اسم الموصل الوارد**
- **مجال المرسل**
- **عدد الرسائل**
- **نموذج للرسائل**: يمكنك النقر فوق **عرض الرسائل العينة** للاطلاع على نتائج [تتبع](message-trace-scc.md) الرسائل لعينة من الرسائل المتأثرة.

![تفاصيل من حولاء بعد تحديد صف في طريقة عرض جدول التفاصيل في تقرير المجال غير المقبول.](../../media/mfi-non-accepted-domain-report-details-flyout.png)

للعودة إلى طريقة عرض التقارير، انقر فوق **عرض التقرير**.

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
