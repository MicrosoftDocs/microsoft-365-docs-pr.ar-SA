---
title: نظرة ثاقبة على الرسائل التي تم إعادة توجيهها بشكل تلقائي
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: يمكن للمسؤولين التعرف على تقرير الرسائل التي تم إعادة توجيهها بشكل تلقائي في لوحة معلومات تدفق البريد في مركز التوافق & الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 4603e7d895c847513a41dc52764070f970a50d15
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476368"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>نظرة ثاقبة على الرسائل التي تم إعادة توجيهها بشكل تلقائي في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**تعرض رؤى** الرسائل التي تم إعادة توجيهها تلقائيا [](mail-flow-insights-v2.md) في لوحة معلومات تدفق البريد [](https://protection.office.com) في مركز التوافق & الأمان معلومات حول الرسائل التي يتم إعادة توجيهها تلقائيا من مؤسستك إلى المستلمين في المجالات الخارجية.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="عنصر واجهة المستخدم تحديدا رسائل إعادة توجيه تلقائية في مركز & الأمان" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>تفاصيل الرسائل التي تم إعادة توجيهها بشكل تلقائي

عندما تنقر فوق عدد الرسائل في عنصر واجهة المستخدم، يظهر جزء من عنصر عنصر واجهة المستخدم يعرض المزيد من المعلومات حول الرسائل التي تم إعادة توجيهها بشكل تلقائي:

- **الرسائل التي تم إعادة توجيهها بشكل تلقائي من خلال أساليب إعادة توجيه**:

  - **حسب قواعد تدفق البريد**
  - **حسب قواعد علبة الوارد**
  - **من خلال إعادة توجيه SMTP**: يشير هذا الأسلوب إلى إعادة توجيه تلقائية يمكن للمسؤولين تكوينها على علبة بريد كما هو موضح في تكوين إعادة توجيه البريد الإلكتروني [لعلبة بريد](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - ارتباط إلى [تقرير إعادة توجيه لمزيد](view-mail-flow-reports.md#forwarding-report) من التفاصيل.

- **الرسائل التي يتم إعادة توجيهها بشكل تلقائي حسب المجالات والمستخدمين**:

  - **أهم 5 مجالات تم إعادة توجيهها إلى**
  - **مجالات جديدة (الأسبوع الماضي)**
  - **أهم 5 مستخدمين في إعادة توجيه**
  - **المستخدمون الجدد (الأسبوع الماضي)**
  - ارتباط إلى [تقرير إعادة توجيه التعديلات](mfi-new-users-forwarding-email.md#forwarding-modifications-report) للحصول على مزيد من التفاصيل.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="عنصر واجهة مستخدم الرسائل التي تم إعادة توجيهها بشكل تلقائي في مركز & الأمان" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Insights

يتم إنشاء رؤى استنادا إلى بيانات التقرير:

- [إعادة توجيه البريد الإلكتروني للمستخدمين الجدد](mfi-new-users-forwarding-email.md)
- [إعادة توجيه البريد الإلكتروني لمجالات جديدة](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).