---
title: تحليلات تدفق البريد في لوحة معلومات تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: يمكن للمسؤولين التعرف على الرؤى والتقارير المتوفرة في لوحة معلومات تدفق البريد في مركز التوافق & الأمان.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 81313744f8c5f14abed59b77182f64e410f9d588
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566923"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>تحليلات تدفق البريد في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكن للمسؤولين استخدام لوحة معلومات تدفق البريد في مركز التوافق & الأمان لاكتشاف الاتجاهات ورؤى المعلومات واتخاذ إجراءات لإصلاح المشاكل المتعلقة بتدفق البريد في مؤسساتهم.

![لوحة معلومات تدفق البريد في مركز & الأمان.](../../media/mail-flow-dashboard-v2.png)

إن الرؤى المتوفرة هي:

- [نظرة ثاقبة على الرسائل التي تم إعادة توجيهها بشكل تلقائي](mfi-auto-forwarded-messages-report.md)

- [إصلاح إمكانية معرفة حلقة البريد](mfi-mail-loop-insight.md) <sup>1</sup>

- [إصلاح بطء تحليلات قواعد تدفق البريد1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [خريطة تدفق البريد](mfi-mail-flow-map-report.md)

- [المجالات الجديدة التي يتم إعادة توجيهها رؤى البريد الإلكتروني2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [مستخدمون جدد يراسلون تحليلات البريد الإلكتروني2](mfi-new-users-forwarding-email.md)<sup></sup>

- [تقرير مجال غير مقبول](mfi-non-accepted-domain-report.md)

- [تقرير بعدم التسليم](mfi-non-delivery-report.md)

- [نظرة ثاقبة حول تدفق البريد الصادر والداخل](mfi-outbound-and-inbound-mail-flow.md)

- [نظرة ثاقبة حول قوائم الانتظار](mfi-queue-alerts-and-queues.md)

- [تقرير ورؤى عملاء SMTP Auth](mfi-smtp-auth-clients-report.md)

- [معرفة حالة تدفق بريد المجال العلوي](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> تظهر هذه المعرفة الدقيقة في المنطقة المستحسنة لك في لوحة معلومات تدفق البريد فقط بعد اكتشاف المشكلة. وإلا، فلن تراها.

<sup>2</sup> لا تظهر هذه المعرفة الدقيقة على لوحة معلومات تدفق البريد، ولكنها مرئية على صفحة تقرير إعادة توجيه بعد [](view-mail-flow-reports.md#forwarding-report) اكتشاف المشكلة. وإلا، فلن تراها.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>الأذونات المطلوبة لعرض لوحة معلومات تدفق البريد

تتوفر لوحة معلومات تدفق البريد لأعضاء مجموعات الدور التالية:

- **إدارة المؤسسة** في مركز & الأمان (المسؤولون العامون).

- **[Exchange مسؤول في](/azure/active-directory/roles/permissions-reference#exchange-administrator)** Azure Active Directory.

- **مسؤول MailFlow** في مركز & الأمان. إذا لم يكن الحساب أيضا عضوا في "إدارة المؤسسة" أو Exchange دور المسؤول، فنظر في المشاكل التالية:
  - يجب على المستخدم تسجيل الدخول إلى مركز & التوافق مباشرة في <https://protection.office.com>.
  - لن يكون لدى المستخدم سوى إذن القراءة فقط في لوحة معلومات تدفق البريد.
  - لن يكون لدى المستخدم حق الوصول إلى مركز مسؤولي Microsoft 365.

لمزيد من المعلومات حول الأذونات، راجع [الأذونات في](permissions-in-the-security-and-compliance-center.md) مركز التوافق & الأمان وامنح المستخدمين حق الوصول إلى [مركز التوافق & الأمان](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>مكان العثور على لوحة معلومات تدفق البريد

افتح "مركز & الأمان" <https://protection.office.com>في ، ثم قم بتوسيع **تدفق** البريد، ثم حدد **لوحة المعلومات**.

الانتقال مباشرة إلى لوحة معلومات تدفق البريد، افتح <https://protection.office.com/mailflow/dashboard>.