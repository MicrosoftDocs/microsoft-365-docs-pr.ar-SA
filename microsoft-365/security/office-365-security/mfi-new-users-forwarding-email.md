---
title: مستخدمون جدد يراسلون تحليلات البريد الإلكتروني
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: يمكن للمسؤولين معرفة كيفية استخدام معلومات المستخدمين الجدد حول إعادة توجيه البريد الإلكتروني في مركز التوافق & الأمان للتحقق من وقت إعادة توجيه الرسائل للمستخدمين في مؤسساتهم إلى مجالات جديدة.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 7e7f97f2f246be609db813f1d42ef6aed6a152a9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470252"
---
# <a name="new-users-forwarding-email-insight-in-the-security--compliance-center"></a>إعادة توجيه المستخدمين الجدد رؤى البريد الإلكتروني في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

من المريب أن تبدأ حسابات المستخدمين الجدد في مؤسستك فجأة في إعادة توجيه رسائل البريد الإلكتروني إلى مجالات خارجية.

تقوم **معرفة المجالات** الجديدة التي يتم إعادة توجيهها بالبريد الإلكتروني [](https://protection.office.com) في مركز & الأمان بالتكليفات عندما يقوم المستخدمون الذين تم إنشاؤهم حديثا في مؤسستك ب إعادة توجيه الرسائل إلى مجالات خارجية. قد يشير هذا الشرط إلى استخدام حسابات المسؤولين الم اختراق لإنشاء المستخدمين الجدد. إذا كنت تشك في أن الحسابات قد تم اختراقها، فشاهد الرد [على حساب بريد إلكتروني م اختراق](responding-to-a-compromised-email-account.md).

تظهر هذه المعرفة فقط عند اكتشاف المشكلة، كما تظهر على صفحة [تقرير إعادة](view-mail-flow-reports.md#forwarding-report) توجيه.

:::image type="content" source="../../media/mfi-new-users-forwarding-email.png" alt-text="نظرة ثاقبة حول إعادة توجيه البريد الإلكتروني للمستخدمين الجدد" lightbox="../../media/mfi-new-users-forwarding-email.png":::

عند النقر فوق عنصر واجهة المستخدم، تظهر عنصر واجهة مستخدم حيث يمكنك العثور على مزيد من التفاصيل حول الرسائل التي تم إعادة توجيهها، بما في ذلك ارتباط [](#forwarding-modifications-report) إلى تقرير تعديلات إعادة توجيه كما هو موضح لاحقا في هذه المقالة.

:::image type="content" source="../../media/mfi-new-users-forwarding-email-details.png" alt-text="قائمة التفاصيل التي تظهر بعد النقر فوق نظرة ثاقبة حول إعادة توجيه البريد الإلكتروني للمستخدمين الجدد" lightbox="../../media/mfi-new-users-forwarding-email-details.png":::

يمكنك أيضا الوصول إلى صفحة التفاصيل هذه عند تحديد المعرفة الدقيقة بعد النقر فوق عرض الكل في  منطقة أهم & **توصيات** **في (** \> لوحة **معلومات التقارير أو** <https://protection.office.com/insightdashboard>).

يمكنك النقر فوق **الارتباط الاطلاع على التقرير المقترن** برؤى الانتقال إلى تقرير إعادة توجيه  التعديلات كما هو موضح في المقطع التالي.

## <a name="forwarding-modifications-report"></a>تقرير إعادة توجيه التعديلات

يعرض **تقرير "إعادة توجيه التعديلات** " تفاصيل حول الرسائل التي يتم إعادة توجيهها تلقائيا من المرسلين في مؤسستك:

- الحسابات التي تم إنشاؤها حديثا التي تقوم ب إعادة توجيه الرسائل إلى مجالات خارجية.
- الحسابات التي ترسل الرسائل إلى مجالات خارجية لم يتم إعادة توجيهها من قبل مرسلين آخرين في مؤسستك.

يمكن أن تشكل هذه الأنواع من الرسائل التي تم إعادة توجيهها خطرا على الأمان أو التوافق، وقد تشير إلى وجود حسابات معرضة للاختطار.

يحتوي التقرير على بيانات لمدة تصل إلى 90 يوما. بشكل افتراضي، يعرض التقرير بيانات آخر 7 أيام.

لا يتوفر هذا التقرير مباشرة في لوحة معلومات [تدفق](mail-flow-insights-v2.md) البريد أو في [لوحة معلومات التقارير](view-mail-flow-reports.md). بالإضافة إلى النقر فوق الارتباط **رؤية التقرير المقترن** بالرؤى في إعادة توجيه تحليلات البريد  الإلكتروني للمستخدمين الجدد، يمكنك الوصول إلى التقرير من خلال:

- النقر فوق **الارتباط تقرير إعادة توجيه الإعلامات** في تفاصيل المجالات الجديدة [التي يتم إعادة توجيهها رؤى البريد الإلكتروني](mfi-new-domains-being-forwarded-email.md).
- فتح <https://protection.office.com/reportv2?id=MailFlowNewForwarding>.

### <a name="report-view-for-the-forwarding-modifications-report"></a>طريقة عرض التقرير للتقرير "إعادة توجيه التعديلات"

تتوفر المخططات التالية في طريقة عرض التقرير:

- **إظهار البيانات ل: مستخدمو إعادة توجيه جدد**:

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarding-users.png" alt-text="طريقة عرض مستخدمي إعادة توجيه جديدة في تقرير &quot;إعادة توجيه التعديلات&quot;" lightbox="../../media/forwarding-modifications-report-new-forwarding-users.png":::

- **إظهار البيانات ل: مجالات إعادة توجيه جديدة**:

    :::image type="content" source="../../media/forwarding-modifications-report-new-forwarded-domains.png" alt-text="طريقة عرض المجالات الجديدة التي تم إعادة توجيهها في تقرير تعديلات إعادة توجيه" lightbox="../../media/forwarding-modifications-report-new-forwarded-domains.png":::

إذا نقرت فوق **عوامل التصفية** في طريقة عرض التقرير، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

### <a name="details-table-view-for-the-forwarding-modifications-report"></a>طريقة عرض جدول التفاصيل للتقرير "إعادة توجيه التعديلات"

إذا نقرت فوق **عرض جدول التفاصيل**، فإن المعلومات المعروضة تعتمد على المخطط الذي كنت تنظر إليه:

- **إظهار البيانات ل: مستخدمو إعادة توجيه جدد**:

  - **الاسم**: عنوان البريد الإلكتروني للمرسل.
  - **نوع إعادة توجيه**
  - **عنوان المستلم**
  - **التفاصيل**
  - **Count**
  - **تاريخ إعادة توجيه أول**

- **إظهار البيانات ل: مجالات إعادة توجيه جديدة**:

  - **الاسم**: مجال البريد الإلكتروني للمرسل.
  - **نوع إعادة توجيه**
  - **عنوان المستلم**
  - **التفاصيل**
  - **Count**
  - **تاريخ إعادة توجيه أول**

إذا نقرت فوق **عوامل التصفية** في طريقة عرض جدول التفاصيل، يمكنك تحديد نطاق تاريخ مع **تاريخ البدء** **وتاريخ الانتهاء**.

إذا حددت صفا من الجدول، تظهر من خلال  المعلومات التالية من خلال المعلومات التالية:

- **الاسم**: هذا هو عنوان البريد الإلكتروني للمرسل (من عرض البيانات ل **:** طريقة عرض مستخدمي إعادة توجيه جديدة) أو مجال البريد الإلكتروني للمرسل (من إظهار البيانات ل **:** طريقة عرض مجالات إعادة توجيه جديدة).
- **نوع إعادة توجيه**
- **المستلم**
- **التفاصيل**
- **Count**
- **تاريخ البدء**
- **توصية**: من هنا، يمكنك النقر فوق الارتباط لإدارة المستخدم في مركز مسؤولي Microsoft 365.

  :::image type="content" source="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png" alt-text="من خارج &quot;التفاصيل&quot; من جدول التفاصيل ل طريقة عرض المستخدمين &quot;إعادة توجيه جديدة&quot; في تقرير &quot;إعادة توجيه التعديلات&quot;" lightbox="../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png":::

للعودة إلى طريقة عرض التقارير، انقر فوق **عرض التقرير**.

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
