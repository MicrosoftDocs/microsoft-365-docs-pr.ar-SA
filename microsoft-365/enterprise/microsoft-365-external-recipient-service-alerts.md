---
title: تنبيهات خدمة المستلمين الخارجيين
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
f1.keywords:
- NOCSH
description: استخدم تنبيهات خدمة المستلمين الخارجيين لمراقبة علب البريد قيد الاحتجاز التي تصل إلى الحصة النسبية لعلبة البريد.
ROBOTS: NOINDEX
ms.openlocfilehash: 2eac85b5a4b6f0f1c7c8737041edc9de50b5a074
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840442"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>تنبيهات الخدمة للرسائل التي تنتظر التسليم إلى المستلمين الخارجيين في مراقبة Exchange Online

تعلم تنبيهات الخدمة المسؤولين عن البريد في قائمة الانتظار للمستلمين الخارجيين خارج Exchange Online. قد تتطلب هذه التنبيهات إجراءات معالجة خارج Microsoft، ولكنها يمكن أن توفر لك المعلومات اللازمة للمعالجة.

يتم عرض تنبيهات الخدمة هذه في مركز مسؤولي Microsoft 365. لعرض تنبيهات الخدمة هذه، انتقل إلى **Health** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Service health**</a> >  **Exchange Online** ثم انقر فوق علامة التبويب **"مشاكل نشطة**". اسم تنبيهات الخدمة هذه هو "وضع الرسائل في قائمة الانتظار للمستلمين الخارجيين فوق الحدود".

![تنبيه الخدمة للرسائل المعلقة لتسليمها إلى المستلمين الخارجيين المعروضة في لوحة معلومات المراقبة Exchange Online.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

عند النقر نقرا مزدوجا فوق تنبيه الخدمة، يتم عرض صفحة منبثقة مشابهة لما يلي.

![المحتوى في تنبيه الخدمة للرسائل التي تنتظر التسليم إلى المستلمين الخارجيين.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>ماذا تشير تنبيهات الخدمة هذه؟

تعلمك تنبيهات الخدمة للرسائل المعلقة بتسليمها إلى المستلمين الخارجيين بأن الرسائل الموجهة إلى مستلمين خارج Exchange Online قد يتم تأخيرها. قد يكون وضع الرسائل في قائمة الانتظار بسبب البيئة المحلية أو حل المراسلة أو دفتر اليومية التابع لجهة خارجية.

فيما يلي بعض الأسباب الشائعة لوضع الرسائل في قائمة الانتظار إلى المستلمين الخارجيين. ومع ذلك، قد لا تقتصر المشكلات التي تتسبب في تنبيهات الخدمة هذه على هذه الأسباب.

- تغييرات DNS

- معدلات إرسال زائدة

- عوامل نقل الرسائل المحلية (MTA) أو حلول عمل اليومية مع مساحة قرص منخفضة أو خالية

- MTAs في الضغط الخلفي

- مشاكل الشبكة، بما في ذلك موازنات التحميل

- مشاكل الشهادة

يحتوي كل تنبيه خدمة على توصيات عالية المستوى لمعالجة المشكلة. يشير تنبيه الخدمة أيضا إلى عدد الرسائل في قائمة الانتظار في وقت التنبيه، والمجال الذي يتم وضع الرسائل في قائمة الانتظار فيه، ورمز الخطأ SMTP المقترن بمعظم الرسائل المدرجة في قائمة الانتظار.

لمزيد من المعلومات لتحديد السبب الجذري لتنبيهات الخدمة هذه، راجع [تحليل معلومات تدفق البريد في Exchange Online](../security/office-365-security/mail-flow-intelligence-in-office-365.md). تتضمن هذه المقالة أيضا إجراءات مقترحة لإصلاح السبب الجذري.

> [!NOTE]
> لا يمكن ل Microsoft حساب كل رمز خطأ SMTP يوفره موردون تابعون لجهات خارجية. لذلك، قد يطلب من المسؤولين التحقق من رموز الأخطاء الخاصة ب MTA أو حلول دفتر اليومية المستخدمة من قبل مؤسستهم.

## <a name="more-information"></a>معلومات إضافية

إذا قامت مؤسستك مؤخرا بإنشاء موصلات تدفق البريد أو تغييرها في مؤسستك المحلية أو Exchange Online، فراجع المقالات التالية للحصول على مزيد من المعلومات.

- [تكوين تدفق البريد باستخدام الموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [إعداد الموصلات لتوجيه البريد](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [أفضل ممارسات تدفق البريد](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [رؤى تدفق البريد في مركز توافق & الأمان](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [رؤى قوائم الانتظار في لوحة معلومات تدفق البريد](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [تتبع رسالة بريد إلكتروني في Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
