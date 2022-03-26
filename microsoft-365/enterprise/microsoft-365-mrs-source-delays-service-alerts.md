---
title: تنبيهات خدمة MRS
ms.author: markjjo
author: markjjo
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appveyor:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: استخدم تنبيهات خدمة ترحيل علب البريد لمراقبة التأخيرات في طلبات ترحيل علبة البريد في مؤسستك.
ms.openlocfilehash: 25c569030bd5da914dc6eb7ec0e58ebadfe4d766
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63575188"
---
# <a name="service-alerts-for-mrs-source-delays-in-exchange-online-monitoring"></a>تنبيهات الخدمة لتأخيرات مصدر MRS في مراقبة Exchange Online

تنبيهات خدمة تأخير مصدر علبة البريد (MRS) تعلمك بقيود التخزين أو مشاكل استخدام المعالجات العالية على جانب المستأجر (مصدر الترحيل) التي قد تؤخر ترحيل علب البريد في Microsoft 365 الخاصة بك. تتضمن تنبيهات الخدمة هذه أيضا ارتباطات إلى موارد Microsoft لمساعدتك على حل هذه المشاكل.

يتم عرض تنبيهات الخدمة هذه في مركز مسؤولي Microsoft 365. لعرض تنبيهات الخدمة هذه، انتقل إلى **حالة HealthService** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Exchange Online**</a> >  **ثم انقر** فوق **علامة التبويب مشاكل** نشطة.

## <a name="what-do-these-service-alerts-indicate"></a>ماذا تشير تنبيهات الخدمة هذه؟

يبلغك تنبيه الخدمة هذا بالتأخيرات المحتملة في ترحيل علب البريد في مؤسستك. يشمل ذلك الترحيل عبر الغابات، وهجرات الضم، وهجرات الضم. يحتوي تنبيه الخدمة على جدول يتضمن معلومات حول الترحيلات الحالية في مؤسستك. فيما يلي مثال على الجدول مع معلومات حول تأخيرات الترحيل.

| BatchName | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|ترحيل السيدة|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|مراقبة مستأجر MRS|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

تصف القائمة التالية كل عمود في المثال السابق.

- **اسم الدفعة**: اسم فريد لوظيفة الترحيل.

- **ExchangeGuid**: المعرف الفريد العام (GUID) لعلبة بريد المستخدم التي يتم ترحيلها.

- **RequestGuid**: GUID لطلب الترحيل.

- **DelayReason**: سبب الترحيل المؤجل.

- **قوائم الانتظار**: المدة التي تم فيها وضع الترحيل في قائمة الانتظار.

- **DelayInHours**: المدة التي تم فيها تأخير الترحيل.

- **SourceServer**: الخادم المحلية التي تنشأ منها عملية الترحيل.

- **RemoteDatabaseName**: اسم قاعدة البيانات الذي ينشأ منه الترحيل.

## <a name="more-information"></a>معلومات إضافية

لمزيد من المعلومات حول ترحيلات علب البريد و MRS، راجع المقالات التالية:

- [تنتقل علبة البريد في Exchange](/exchange/recipients/mailbox-moves)

- [Microsoft 365 Office 365 الترحيل وأفضل الممارسات](/exchange/mailbox-migration/office-365-migration-best-practices)

- [تحليل أداء ترحيل علبة البريد](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [استكشاف الأخطاء في الترحيلات البطيئة وإصلاحها](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [طرق لترحيل حسابات بريد إلكتروني متعددة إلى Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
