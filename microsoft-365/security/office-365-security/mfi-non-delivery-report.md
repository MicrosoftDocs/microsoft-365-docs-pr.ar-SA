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
description: يمكن للمسؤولين معرفة كيفية استخدام تقرير تفاصيل عدم التسليم في لوحة معلومات تدفق البريد في مركز توافق & الأمان لمراقبة رموز الأخطاء الأكثر تكرارا في تقارير عدم التسليم (المعروفة أيضا بتقارير بعدم التسليم أو رسائل البريد المرتد) من المرسلين في مؤسستك.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 663e145bcf9d6dc95f0f71b3b0b50a78419ed989
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973498"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>تقرير بعدم التسليم في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يعرض **تقرير عدم التسليم** في [لوحة معلومات تدفق البريد](mail-flow-insights-v2.md) في [مركز توافق & الأمان](https://protection.office.com) رموز الأخطاء الأكثر مصادفة في تقارير عدم التسليم (المعروفة أيضا بتقارير بعدم التسليم أو رسائل البريد المرتد) للمستخدمين في مؤسستك. يعرض هذا التقرير تفاصيل التقارير بعدم التسليم حتى تتمكن من استكشاف مشاكل تسليم البريد الإلكتروني وإصلاحها.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير عدم التسليم في لوحة معلومات تدفق البريد في مركز توافق & الأمان" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>طريقة عرض التقرير لتقرير عدم التسليم

سيؤدي النقر فوق عنصر واجهة مستخدم **تقرير عدم التسليم** إلى نقلك إلى **تقرير عدم التسليم**.

بشكل افتراضي، يظهر النشاط لكافة رموز الأخطاء. إذا **نقرت فوق "إظهار البيانات"**، يمكنك تحديد رمز خطأ معين من القائمة المنسدلة.

إذا قمت بالمرور فوق لون معين (رمز الخطأ) في يوم معين في المخطط، فسترى العدد الإجمالي للرسائل الخاصة بالخطأ.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="طريقة عرض التقرير في تقرير المجال غير المقبول" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>طريقة عرض جدول التفاصيل لتقرير عدم التسليم

إذا نقرت فوق **"عرض جدول التفاصيل** " في طريقة عرض التقرير، فستظهر المعلومات التالية:

- **تاريخ**
- **رمز تقرير عدم التسليم**
- **عدد**
- **رسائل نموذجية**: معرفات الرسائل لعينة من الرسائل المتأثرة.

إذا نقرت فوق **"عوامل التصفية** " في طريقة عرض جدول التفاصيل، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

لإرسال التقرير عبر البريد الإلكتروني لنطاق تاريخ معين إلى مستلم واحد أو أكثر، انقر فوق **"طلب التنزيل**".

عند تحديد صف في الجدول، تظهر قائمة منبثقة تتضمن المعلومات التالية:

- **تاريخ**
- **رمز تقرير عدم التسليم**: يمكنك النقر فوق الارتباط للعثور على مزيد من المعلومات حول الأسباب والحلول لرمز الخطأ المحدد.
- **عدد**
- **نماذج الرسائل**: يمكنك النقر فوق **"عرض نماذج الرسائل** " لرؤية نتائج [تتبع الرسائل](message-trace-scc.md) لعينة من الرسائل المتأثرة.

:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="القائمة المنبثقة للتفاصيل بعد تحديد صف في طريقة عرض جدول التفاصيل في تقرير عدم التسليم" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول نتائج التحليلات الأخرى في لوحة معلومات تدفق البريد، راجع [رؤى تدفق البريد في مركز التوافق & الأمان](mail-flow-insights-v2.md).
