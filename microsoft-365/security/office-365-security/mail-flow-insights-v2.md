---
title: رؤى تدفق البريد في لوحة معلومات تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: يمكن للمسؤولين التعرف على الرؤى والتقارير المتوفرة في لوحة معلومات تدفق البريد في مركز التوافق & الأمان.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: eef35eedd5a7f182160b9a6a8b27a59cf9cdd9c0
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129167"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>نتائج تحليلات تدفق البريد في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكن للمسؤولين استخدام لوحة معلومات تدفق البريد في مركز التوافق & الأمان لاكتشاف الاتجاهات والرؤى واتخاذ إجراءات لإصلاح المشكلات المتعلقة بتدفق البريد في مؤسستهم.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="لوحة معلومات تدفق البريد في مركز توافق & الأمان" lightbox="../../media/mail-flow-dashboard-v2.png":::

النتائج المعرفية المتوفرة هي:

- [نتائج تحليلات الرسائل التي تمت إعادة توجيهها تلقائياً](mfi-auto-forwarded-messages-report.md)

- [إصلاح التكرار الحلقي المحتمل للبريد1](mfi-mail-loop-insight.md)<sup></sup>

- [إصلاح قواعد تدفق البريد البطيئة insight1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [خريطة تدفق البريد](mfi-mail-flow-map-report.md)

- [المجالات الجديدة التي تتم إعادة توجيهها عبر البريد الإلكتروني insight2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [مستخدمون جدد يعيدون توجيه رؤى البريد الإلكتروني2](mfi-new-users-forwarding-email.md)<sup></sup>

- [تقرير مجال غير مقبول](mfi-non-accepted-domain-report.md)

- [تقرير بعدم التسليم](mfi-non-delivery-report.md)

- [نظرة ثاقبة على تدفق البريد الصادر والوارد](mfi-outbound-and-inbound-mail-flow.md)

- [تحليلات قوائم الانتظار](mfi-queue-alerts-and-queues.md)

- [تحليلات عملاء SMTP Auth وتقريرهم](mfi-smtp-auth-clients-report.md)

- [نظرة ثاقبة لحالة تدفق بريد المجال العلوي](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> تظهر هذه الرؤى في المنطقة **"مستحسن"** في لوحة معلومات تدفق البريد فقط بعد اكتشاف المشكلة. وإلا، فلن تتمكن من رؤيتها.

<sup>2</sup> لا تظهر هذه الرؤى على لوحة معلومات تدفق البريد، ولكنها مرئية على صفحة [تقرير إعادة التوجيه](view-mail-flow-reports.md#forwarding-report) بعد اكتشاف المشكلة. وإلا، فلن تتمكن من رؤيتها.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>الأذونات المطلوبة لعرض لوحة معلومات تدفق البريد

تتوفر لوحة معلومات تدفق البريد لأعضاء مجموعات الأدوار التالية:

- **إدارة المؤسسة** في مركز توافق & الأمان (المسؤولون العموميون).

- **[مسؤول Exchange](/azure/active-directory/roles/permissions-reference#exchange-administrator)** في Azure Active Directory.

- **مسؤول MailFlow** في مركز توافق & الأمان. إذا لم يكن الحساب أيضا عضوا في مجموعات أدوار إدارة المؤسسة أو مسؤول Exchange، ففكر في المشكلات التالية:
  - يجب على المستخدم تسجيل الدخول إلى Security & Compliance Center مباشرة في <https://protection.office.com>.
  - سيكون لدى المستخدم إذن للقراءة فقط للوحة معلومات تدفق البريد فقط.
  - لن يكون لدى المستخدم حق الوصول إلى مركز مسؤولي Microsoft 365.

لمزيد من المعلومات حول الأذونات، راجع [الأذونات في مركز توافق & الأمان](permissions-in-the-security-and-compliance-center.md) [ومنح المستخدمين حق الوصول إلى مركز التوافق & الأمان](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>مكان العثور على لوحة معلومات تدفق البريد

افتح Security & Compliance Center في <https://protection.office.com>توسيع **تدفق البريد**، ثم حدد **لوحة المعلومات**.

للانتقال مباشرة إلى لوحة معلومات تدفق البريد، افتح <https://protection.office.com/mailflow/dashboard>.
