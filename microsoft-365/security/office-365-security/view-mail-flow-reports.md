---
title: عرض تقارير تدفق البريد في لوحة معلومات التقارير
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين التعرف على تقارير تدفق البريد المتوفرة في لوحة معلومات التقارير في مركز التوافق & الأمان.
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d1fc133a8e05541f402e35cf8d62ee9662af661b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476214"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>عرض تقارير تدفق البريد في لوحة معلومات التقارير في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> تتوفر معظم التقارير في هذه المقالة أيضا في مدخل Microsoft 365 Defender أو Exchange إدارة (EAC). لمزيد من المعلومات، راجع المواضيع التالية:
>
> - [تقارير تدفق البريد في مركز إدارة Exchange الجديد](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [عرض تقارير أمان البريد الإلكتروني في مدخل Microsoft 365 Defender الإلكتروني](view-email-security-reports.md)

بالإضافة إلى تقارير تدفق البريد المتوفرة في لوحة معلومات تدفق البريد في مركز [](mail-flow-insights-v2.md) التوافق ل الأمان &، تتوفر مجموعة متنوعة من تقارير تدفق البريد الإضافية في لوحة معلومات التقارير لمساعدتك على مراقبة Microsoft 365 الخاصة بك.

إذا كانت لديك [الأذونات اللازمة](#what-permissions-are-needed-to-view-these-reports)، يمكنك عرض هذه التقارير في مركز & التوافق <https://protection.office.com> من خلال الذهاب إلى **لوحة معلومات** \> **التقارير**. الانتقال مباشرة إلى لوحة معلومات التقارير، افتح <https://protection.office.com/insightdashboard>.

:::image type="content" source="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png" alt-text="لوحة معلومات التقارير في مركز & الأمان" lightbox="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png":::

## <a name="connector-report"></a>تقرير الموصل

> [!NOTE]
> تم استبدال هذا التقرير ب "تقرير الرسائل  الواردة **" و"** تقرير الرسائل الصادرة" في EAC. لمزيد من المعلومات، راجع تقارير الرسائل الواردة والرسائل الصادرة [في EAC الجديد](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports).

## <a name="exchange-transport-rule-report"></a>Exchange قاعدة النقل

يعرض **Exchange قاعدة** نقل البريد الإلكتروني تأثير قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) على الرسائل الواردة والبريد الصادر في مؤسستك.

لعرض التقرير، افتح مركز التوافق & في <https://protection.office.com>،  \> واذهب إلى لوحة معلومات التقارير وحدد Exchange **النقل**. للذهاب مباشرة إلى التقرير، افتح <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/scc-transport-rule-report-widget.png" alt-text="عنصر Exchange قاعدة النقل في لوحة معلومات التقارير" lightbox="../../media/scc-transport-rule-report-widget.png":::

> [!NOTE]
> يتوفر **Exchange قاعدة** النقل الآن في EAC. لمزيد من المعلومات، [راجع Exchange قاعدة النقل في EAC الجديد](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

## <a name="forwarding-report"></a>إعادة توجيه التقرير

> [!NOTE]
> يتوفر **تقرير إعادة توجيه** الآن في EAC. لمزيد من المعلومات، راجع [تقرير الرسائل التي تم إعادة توجيهها بشكل تلقائي في EAC الجديد](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>تقرير حالة تدفق البريد

يشبه **تقرير حالة تدفق البريد** تقرير البريد الإلكتروني المرسل [](#sent-and-received-email-report)والمستلم، مع معلومات إضافية حول البريد الإلكتروني المسموح به أو المحظور على الحافة. هذا هو التقرير الوحيد الذي يحتوي على معلومات حماية الحافة، ويظهر فقط مقدار البريد الإلكتروني المحظور قبل السماح له بالتقييم بواسطة Exchange Online Protection (EOP). من المهم أن تدرك أنه إذا تم إرسال رسالة إلى خمسة مستلمين، فإننا نحسبها على أنها خمس رسائل مختلفة وليس رسالة واحدة.

لعرض التقرير، افتح [مركز & التوافق](https://protection.office.com)، واذهب  \> إلى لوحة معلومات التقارير **وحدد** **تقرير حالة تدفق البريد**. الانتقال مباشرة إلى تقرير **حالة تدفق البريد،** افتح <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/scc-mail-flow-status-report-widget.png" alt-text="عنصر واجهة مستخدم تقرير حالة تدفق البريد في لوحة معلومات التقارير" lightbox="../../media/scc-mail-flow-status-report-widget.png":::

> [!NOTE]
> يؤدي النقر فوق عنصر واجهة المستخدم لهذا التقرير في مركز & الأمان (protection.office.com) الآن إلى الوصول إلى التقرير الكامل في مدخل Microsoft 365 Defender (security.microsoft.com). للحصول على تفاصيل حول التقرير، راجع [تقرير حالة تدفق البريد](view-email-security-reports.md#mailflow-status-report).

## <a name="sent-and-received-email-report"></a>تقرير البريد الإلكتروني المرسل والمستلم

> [!NOTE]
> تم استبدال هذا التقرير بواسطة تقرير [حالة تدفق البريد](#mailflow-status-report).

## <a name="top-senders-and-recipients-report"></a>تقرير أهم المرسلين والمستلمين

يعرض **أهم المرسلين** والمستلمين أهم مرسلي الرسائل في مؤسستك، بالإضافة إلى أهم المستلمين للرسائل التي تم الكشف عنها بواسطة EOP Defender لـ Office 365 الحماية.

لعرض التقرير، افتح مركز التوافق & في <https://protection.office.com>،  \> واذهب إلى لوحة معلومات التقارير وحدد أهم المرسلين **والمستلمين**. الانتقال مباشرة إلى التقرير، افتح أحد عناوين URL التالية:

- Defender لـ Office 365:<https://protection.office.com/TopSenderRecipientsATP>
- EOP: <https://protection.office.com/TopSenderRecipients>

:::image type="content" source="../../media/scc-top-senders-and-recipients-widget.png" alt-text="عنصر واجهة مستخدم أهم المرسلين والمستلمين في لوحة معلومات التقارير" lightbox="../../media/scc-top-senders-and-recipients-widget.png":::

> [!NOTE]
> على الرغم من أن النقر فوق عنصر واجهة المستخدم لهذا التقرير في مركز التوافق & الأمان يأخذك إلى صفحة protection.office.com، إلا أن محتوى الصفحة من مدخل Microsoft 365 Defender. للحصول على تفاصيل حول التقرير، راجع [تقرير أهم المرسلين والمستلمين](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="what-permissions-are-needed-to-view-these-reports"></a>ما هي الأذونات المطلوبة لعرض هذه التقارير؟

لعرض التقارير الموضحة في هذه المقالة واستخدامها، يجب أن تكون عضوا في إحدى مجموعات الدور التالية في مركز التوافق & الأمان:

- **إدارة المؤسسة**
- **مسؤول الأمان**
- **قارئ الأمان**
- **القارئ العام**

لمزيد من المعلومات، راجع [الأذونات في مركز & الأمان](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات المطلوبة في مركز التوافق & الأمان والأذونات للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

[تقارير ذكية ورؤى في مركز & الأمان](reports-and-insights-in-security-and-compliance.md)

[تحليلات تدفق البريد في مركز & الأمان](mail-flow-insights-v2.md)

[عرض تقارير أمان البريد الإلكتروني في مركز & الأمان](view-email-security-reports.md)

[عرض تقارير Microsoft Defender لـ Office 365](view-reports-for-mdo.md)
