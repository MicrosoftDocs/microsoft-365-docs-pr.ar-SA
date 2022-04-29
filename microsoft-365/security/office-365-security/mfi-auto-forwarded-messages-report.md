---
title: نتائج تحليلات الرسائل التي تمت إعادة توجيهها تلقائياً
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: يمكن للمسؤولين التعرف على تقرير الرسائل التي تمت إعادة توجيهها تلقائيا في لوحة معلومات تدفق البريد في مركز التوافق & الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2f102f4fbea558f0972fbd4f3e8f4a4bea257bf4
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131031"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>نظرة ثاقبة للرسائل التي تمت إعادة توجيهها تلقائيا في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تعرض **نتيجة تحليلات الرسائل التي تمت إعادة توجيهها تلقائيا** في [لوحة معلومات تدفق البريد](mail-flow-insights-v2.md) في [مركز توافق & الأمان](https://protection.office.com) معلومات حول الرسائل التي تتم إعادة توجيهها تلقائيا من مؤسستك إلى المستلمين في المجالات الخارجية.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="عنصر واجهة المستخدم وهو الرسائل التي تمت إعادة توجيهها تلقائيا في مركز توافق & الأمان" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>تفاصيل الرسائل التي تمت إعادة توجيهها تلقائيا

عند النقر فوق عدد الرسائل في عنصر واجهة المستخدم، يظهر جزء قائمة منبثقة يعرض المزيد من المعلومات حول الرسائل التي تمت إعادة توجيهها تلقائيا:

- **الرسائل التي تتم إعادة توجيهها تلقائيا من خلال أساليب إعادة التوجيه**:

  - **حسب قواعد تدفق البريد**
  - **حسب قواعد علبة الوارد**
  - **بواسطة إعادة توجيه SMTP**: يشير هذا الأسلوب إلى إعادة التوجيه التلقائي الذي يمكن للمسؤولين تكوينه على علبة بريد كما هو موضح في [تكوين إعادة توجيه البريد الإلكتروني لعل بريد.](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding)
  - ارتباط إلى [تقرير إعادة التوجيه](view-mail-flow-reports.md#forwarding-report) للحصول على مزيد من التفاصيل.

- **الرسائل التي تتم إعادة توجيهها تلقائيا بواسطة المجالات والمستخدمين**:

  - **أهم 5 مجالات تمت إعادة توجيهها إلى**
  - **المجالات الجديدة (الأسبوع الماضي)**
  - **أفضل 5 مستخدمين لإعادة التوجيه**
  - **مستخدمون جدد (الأسبوع الماضي)**
  - ارتباط إلى [تقرير تعديلات إعادة التوجيه](mfi-new-users-forwarding-email.md#forwarding-modifications-report) لمزيد من التفاصيل.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="عنصر واجهة مستخدم الرسائل التي تمت إعادة توجيهها تلقائيا في مركز توافق & الأمان" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Insights

يتم إنشاء رؤيتين استنادا إلى بيانات التقرير:

- [إعادة توجيه البريد الإلكتروني للمستخدمين الجدد](mfi-new-users-forwarding-email.md)
- [المجالات الجديدة التي تتم إعادة توجيهها بالبريد الإلكتروني](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول نتائج التحليلات الأخرى في لوحة معلومات تدفق البريد، راجع [رؤى تدفق البريد في مركز التوافق & الأمان](mail-flow-insights-v2.md).
