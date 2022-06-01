---
title: تنبيهات خدمة ."."
ms.author: kvice
author: kelleyvice-msft
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
description: استخدم استشارات خدمة ترحيل علبة البريد لمراقبة التأخيرات في طلبات ترحيل علبة البريد في مؤسستك.
ms.openlocfilehash: fe6f60b75fb7d27781d442faf82ff981ac54808a
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810726"
---
# <a name="service-advisories-for-mrs-source-delays-in-exchange-online-monitoring"></a>إرشادات الخدمة للتأخيرات في مصادر الخدمات الخارجية في المراقبة Exchange Online

تخبرك استشارات خدمة تأخير مصدر خدمة النسخ المتماثل لعلب البريد (CV) بحدود التخزين أو مشاكل استخدام المعالج المرتفعة على جانب المستأجر (مصدر الترحيل) التي قد تؤدي إلى تأخير عمليات ترحيل علب البريد في مؤسستك Microsoft 365. تتضمن إرشادات الخدمة هذه أيضا ارتباطات إلى موارد Microsoft لمساعدتك في حل هذه المشاكل.

يتم عرض إرشادات الخدمة هذه في مركز مسؤولي Microsoft 365. لعرض إرشادات الخدمة هذه، انتقل إلى **Health** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Service health**</a> >  **Exchange Online** ثم انقر فوق علامة التبويب **"مشاكل نشطة**".

## <a name="what-do-these-service-advisories-indicate"></a>ماذا تشير إرشادات الخدمة هذه؟

تخبرك هذه الخدمة الاستشارية بوجود تأخيرات محتملة في عمليات ترحيل علب البريد في مؤسستك. ويشمل ذلك عمليات الترحيل عبر الغابات، والترحيلات الإلحاقية، وإلحاق عمليات الترحيل. تحتوي استشارات الخدمة على جدول يتضمن معلومات حول عمليات الترحيل الحالية في مؤسستك. فيما يلي مثال على الجدول الذي يتضمن معلومات حول تأخيرات الترحيل.

| BatchGuid | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | خادم المصادر | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|12345678-1234-1234-1234-1234567891011|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|87654321-4321-4321-4321-1101987654321|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

تصف القائمة التالية كل عمود في المثال السابق.

- **BatchGuid**: GUID فريد لمهمة الترحيل.

- **ExchangeGuid**: المعرف الفريد العمومي (GUID) لعل بريد المستخدم الذي يتم ترحيله.

- **RequestGuid**: المعرف الفريد العمومي (GUID) لطلب الترحيل.

- **DelayReason**: سبب الترحيل المتأخر.

- **QueueHours**: المدة التي تم فيها وضع الترحيل في قائمة الانتظار والانتظار.

- **DelayInHours**: المدة التي تم فيها تأخير الترحيل.

- **SourceServer**: الخادم المحلي الذي ينشأ منه الترحيل.

- **RemoteDatabaseName**: اسم قاعدة البيانات الذي ينشأ منه الترحيل.

## <a name="more-information"></a>معلومات إضافية

لمزيد من المعلومات حول عمليات ترحيل البريد وSED، راجع المقالات التالية:

- [نقل علبة البريد في Exchange](/exchange/recipients/mailbox-moves)

- [Microsoft 365 وأداء الترحيل Office 365 وأفضل الممارسات](/exchange/mailbox-migration/office-365-migration-best-practices)

- [تحليل أداء ترحيل علبة البريد](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [استكشاف أخطاء عمليات الترحيل البطيئة وإصلاحها](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [طرق ترحيل حسابات بريد إلكتروني متعددة إلى Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
