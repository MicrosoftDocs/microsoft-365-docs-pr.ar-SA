---
title: تنبيهات خدمة المستلمين الخارجيين
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
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
description: استخدم تنبيهات خدمة المستلمين الخارجيين لمراقبة علب البريد الموقوقة التي تصل إلى الحصة النسبية لعلبة البريد.
ms.openlocfilehash: 8db8e090ec5430f13153bc3edf5b3315c041d9cf
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64567995"
---
# <a name="service-alerts-for-messages-pending-delivery-to-external-recipients-in-exchange-online-monitoring"></a>تنبيهات الخدمة للرسائل المعلقة للتسليم إلى المستلمين الخارجيين في Exchange Online مراقبة

تبلغ تنبيهات الخدمة المسؤولين عن وضع البريد في قائمة انتظار للمستلمين الخارجيين خارج Exchange Online. قد تتطلب هذه التنبيهات إجراءات إصلاح خارج Microsoft، ولكن يمكنها أن توفر لك المعلومات اللازمة لإعادة المعالجة.

يتم عرض تنبيهات الخدمة هذه في مركز مسؤولي Microsoft 365. لعرض تنبيهات الخدمة هذه، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank"></a> >  >  حالة Estado de funcionamento dos serviços **Exchange Online** ثم انقر فوق **علامة التبويب مشاكل** نشطة. اسم تنبيهات الخدمة هذه هو "قائمة انتظار الرسائل إلى مستلمين خارجيين فوق الحدود".

![تنبيه الخدمة للرسائل المعلقة للتسليم إلى المستلمين الخارجيين المعروضة في Exchange Online لوحة معلومات المراقبة.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts1.png)

عندما تنقر نقرا مزدوجا فوق تنبيه الخدمة، يتم عرض صفحة من القائمة flyout مماثلة لما يلي.

![المحتوى في تنبيه الخدمة للرسائل المعلقة للتسليم إلى مستلمين خارجيين.](../media/microsoft-365-exchange-monitoring/ExternalRecipientsServiceAlerts2.png)

## <a name="what-do-these-service-alerts-indicate"></a>ماذا تشير تنبيهات الخدمة هذه؟

تنبيهات الخدمة للرسائل المعلقة للتسليم إلى مستلمين خارجيين تعلمك بأن الرسائل الموجهة إلى مستلمين خارج Exchange Online قد يتم تأخيرها. قد يكون سبب وضع الرسائل في قائمة الانتظار هو البيئة المحلية أو حل المراسلة أو دفتر اليومية من جهة خارجية.

فيما يلي بعض الأسباب الشائعة لرسائل قائمة الانتظار إلى مستلمين خارجيين. ومع ذلك، قد لا تقتصر المشاكل التي تتسبب في تنبيهات الخدمة هذه على هذه الأسباب.

- تغييرات DNS

- أسعار الإرسال الزائد

- حلول وكلاء نقل الرسائل (MTA) أو دفتر اليومية المحلي مع مساحة قرص منخفضة إلى بلا مساحة مجانية

- MTAs في الضغط على الخلف

- مشاكل الشبكة، بما في ذلك موازنات التحميل

- مشاكل الشهادة

يحتوي كل تنبيه خدمة على توصيات عالية المستوى حول حل المشكلة. يشير تنبيه الخدمة أيضا إلى عدد الرسائل التي كانت في قائمة الانتظار في وقت التنبيه، والمجال الذي يتم فيه إرسال الرسائل في قائمة الانتظار، إلى جانب رمز الخطأ SMTP المقترن بم معظم الرسائل في قائمة الانتظار.

لمزيد من المعلومات حول تحديد السبب الجذر لتنبيهات الخدمة هذه، راجع معلومات تدفق البريد [في](../security/office-365-security/mail-flow-intelligence-in-office-365.md) Exchange Online. تتضمن هذه المقالة أيضا الإجراءات المقترحة لإصلاح السبب الجذر.

> [!NOTE]
> لا تستطيع Microsoft حساب كل رمز خطأ SMTP تم توفيره من قبل موردي الجهات الخارجية. وبالتالي، قد يطلب من المسؤولين التحقق من رموز الأخطاء الخاصة بحلول MTA أو دفتر اليومية الخاصة بهم التي تستخدمها المؤسسة.

## <a name="more-information"></a>معلومات إضافية

إذا أنشأت مؤسستك مؤخرا أو غيرت موصلات تدفق البريد في مؤسستك Exchange Online أو مؤسستك، فشاهد المقالات التالية للحصول على مزيد من المعلومات.

- [تكوين تدفق البريد باستخدام الموصلات في Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

- [إعداد الموصلات توجيه البريد](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail)

- [أفضل ممارسات تدفق البريد](/exchange/mail-flow-best-practices/mail-flow-best-practices)

- [تحليلات تدفق البريد في مركز & الأمان](/microsoft-365/security/office-365-security/mail-flow-insights-v2)

- [معرفة قوائم الانتظار في لوحة معلومات تدفق البريد](/microsoft-365/security/office-365-security/mfi-queue-alerts-and-queues#queues-insight-in-the-mail-flow-dashboard)

- [تتبع رسالة بريد إلكتروني في Exchange Online](/exchange/monitoring/trace-an-email-message/trace-an-email-message)
