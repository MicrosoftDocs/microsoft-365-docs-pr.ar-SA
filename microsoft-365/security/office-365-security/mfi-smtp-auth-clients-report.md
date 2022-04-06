---
title: تحليلات عملاء SMTP Auth والتقارير في لوحة معلومات تدفق البريد
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
description: يمكن للمسؤولين التعرف على كيفية استخدام معلومات SMTP الصادقة والتقارير في لوحة معلومات تدفق البريد في مركز التوافق ل الأمان & لمراقبة مرسلي البريد الإلكتروني في المؤسسة الذين يستخدمون SMTP المصادق عليه (SMTP AUTH) لإرسال رسائل البريد الإلكتروني.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8c2152820e7f3d5dbf04534e5f0b0fec344ecc7b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474982"
---
# <a name="smtp-auth-clients-insight-and-report-in-the-security--compliance-center"></a>نظرة ثاقبة حول عملاء SMTP أو تقريرهم في مركز التوافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تسلط نظرة ثاقبة لعملاء **SMTP Auth** في لوحة معلومات تدفق البريد بالإضافة إلى تقرير عملاء [SMTP Auth](#smtp-auth-clients-report) المقترن في مركز التوافق ل الأمان [&](https://protection.office.com) الضوء على استخدام بروتوكول إرسال عميل SMTP AUTH من قبل المستخدمين أو حسابات النظام في مؤسستك.[](mail-flow-insights-v2.md) يقدم هذا البروتوكول القديم (الذي يستخدم نقطة النهاية smtp.office365.com) المصادقة الأساسية فقط، وهو عرضة لأن يتم استخدامه بواسطة الحسابات الم اختراق لإرسال البريد الإلكتروني. تتيح لك الرؤى والتقارير التحقق من النشاط غير المعتاد لمرسلات البريد الإلكتروني ل SMTP AUTH. كما يعرض بيانات استخدام TLS للعملاء أو الأجهزة التي تستخدم SMTP AUTH.

يشير عنصر واجهة المستخدم إلى عدد المستخدمين أو حسابات الخدمة التي استخدمت بروتوكول اونث SMTP في آخر 7 أيام.

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-widget.png" alt-text="عنصر واجهة مستخدم عملاء SMTP Auth في لوحة معلومات تدفق البريد في مركز & الأمان" lightbox="../../media/mfi-smtp-auth-clients-report-widget.png":::

إذا نقرت فوق عدد الرسائل على عنصر واجهة المستخدم، تظهر من خلال عنصر واجهة المستخدم **عميل SMTP Auth** . توفر هذه الأخيرة طريقة عرض مجمعة لاستخدام TLS وإجماليات أحجامها خلال الأسبوع الماضي.

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-details.png" alt-text="القائمة flyout Details بعد النقر فوق عنصر واجهة مستخدم عملاء SMTP Auth في لوحة معلومات تدفق البريد" lightbox="../../media/mfi-smtp-auth-clients-report-details.png":::

يمكنك النقر فوق ارتباط تقرير **عملاء SMTP Auth** الانتقال إلى تقرير عملاء SMTP Auth كما هو موضح في القسم التالي.

## <a name="smtp-auth-clients-report"></a>تقرير عملاء SMTP Auth

### <a name="report-view-for-the-smtp-auth-clients-report"></a>طريقة عرض التقرير للتقرير "عملاء SMTP Auth"

بشكل افتراضي، يعرض التقرير بيانات آخر 7 أيام، ولكن البيانات متوفرة خلال آخر 90 يوما.

يحتوي قسم النظرة العامة على المخططات التالية:

- عرض البيانات حسب **:** إرسال مستوى الصوت: بشكل افتراضي، يعرض المخطط عدد رسائل عميل SMTP Auth التي تم إرسالها من كل المجالات (إظهار البيانات ل **:** يتم تحديد كل مجالات المرسلين بشكل افتراضي). يمكنك تصفية النتائج إلى مجال مرسل معين بالنقر فوق إظهار البيانات لمجال  المرسل وتحديده من القائمة المنسدلة. إذا قمت ب hover a specific data point (day) ، يتم عرض عدد الرسائل.

  :::image type="content" source="../../media/mfi-smtp-auth-clients-report-sending-volume-view.png" alt-text="طريقة العرض &quot;إرسال مستوى الصوت&quot; في تقرير عملاء SMTP Auth في مركز & الأمان" lightbox="../../media/mfi-smtp-auth-clients-report-sending-volume-view.png":::

- **عرض البيانات حسب: استخدام TLS**: يعرض المخطط النسبة المئوية لاستخدام TLS لكل رسائل عميل SMTP Auth خلال الفترة الزمنية المحددة. يسمح لك هذا المخطط بتحديد المستخدمين وحسابات النظام التي لا تزال تستخدم الإصدارات القديمة من TLS واتخاذ إجراء بشأنها.

  :::image type="content" source="../../media/mfi-smtp-auth-clients-report-tls-usage-view.png" alt-text="طريقة عرض استخدام TLS في تقرير عملاء SMTP Auth في مركز & الأمان" lightbox="../../media/mfi-smtp-auth-clients-report-tls-usage-view.png":::

إذا نقرت فوق **عوامل التصفية** في طريقة عرض التقرير، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

انقر **فوق طلب تقرير** لتلقي إصدار أكثر تفصيلا من التقرير في رسالة بريد إلكتروني. يمكنك تحديد نطاق التاريخ والمستلمين لتلقي التقرير.

### <a name="details-table-view-for-the-smtp-auth-clients-report"></a>طريقة عرض جدول التفاصيل الخاصة بتقرير عملاء SMTP Auth

إذا نقرت فوق **عرض جدول التفاصيل**، فإن المعلومات المعروضة تعتمد على المخطط الذي كنت تنظر إليه:

- **عرض البيانات حسب: إرسال مستوى الصوت**: تظهر المعلومات التالية في جدول:

  - **عنوان المرسل**
  - **عدد الرسائل**

  إذا حددت صفا، يتم عرض التفاصيل نفسها في من خلال مجموعة من المعلومات.

- **عرض البيانات حسب: استخدام TLS**: تظهر المعلومات التالية في جدول:

  - **عنوان المرسل**
  - **TLS1.0٪**<sup>\*</sup>
  - **TLS1.1٪**<sup>\*</sup>
  - **TLS1.2٪**<sup>\*</sup>
  - **عدد الرسائل**

  <sup>\*</sup> يعرض هذا العمود كلا من النسبة المئوية للرسائل الواردة من المرسل وعددها.

إذا نقرت فوق **عوامل التصفية** في طريقة عرض جدول التفاصيل، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

إذا حددت صفا، يتم عرض تفاصيل مماثلة في مجموعة من المعلومات:

:::image type="content" source="../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png" alt-text="من جانب منزه التفاصيل من جدول التفاصيل ل طريقة عرض استخدام TLS في تقرير عملاء SMTP Auth" lightbox="../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png":::

انقر **فوق طلب تقرير** لتلقي إصدار أكثر تفصيلا من التقرير في رسالة بريد إلكتروني. يمكنك تحديد نطاق التاريخ والمستلمين لتلقي التقرير.

للعودة إلى طريقة عرض التقارير، انقر فوق **عرض التقرير**.

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
