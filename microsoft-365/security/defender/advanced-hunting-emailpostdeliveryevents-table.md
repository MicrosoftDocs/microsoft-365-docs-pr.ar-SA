---
title: جدول EmailPostDeliveryEvents في مخطط التتبع المتقدم
description: تعرف على إجراءات ما بعد التسليم التي تم اتخاذها على رسائل البريد الإلكتروني Microsoft 365 في جدول EmailPostDeliveryEvents لمخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، EmailPostDeliveryEvents، معرف رسالة الشبكة، المرسل، المستلم، معرف المرفق، اسم المرفق، حكم البرامج الضارة، حكم التصيد الاحتيالي، عدد المرفقات، عدد الارتباطات، عدد عناوين url
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 876b240d73613637cc2f564ce6415873b645293c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130572"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لـ Office 365

`EmailPostDeliveryEvents` يحتوي الجدول في مخطط [التتبع المتقدم](advanced-hunting-overview.md) على معلومات حول إجراءات ما بعد التسليم التي تم اتخاذها على رسائل البريد الإلكتروني التي تتم معالجتها بواسطة Microsoft 365. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) التي يدعمها جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على مزيد من المعلومات حول رسائل البريد الإلكتروني الفردية، يمكنك أيضا استخدام الجداول [`EmailEvents`](advanced-hunting-emailevents-table.md)والجداول[`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md).[`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، [راجع مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، تم إنشاؤه بواسطة Microsoft 365 |
| `InternetMessageId` | `string` | معرف عام للبريد الإلكتروني الذي تم تعيينه بواسطة نظام إرسال البريد الإلكتروني |
| `Action` | `string` | الإجراء الذي تم اتخاذه على الكيان |
| `ActionType` | `string` | نوع النشاط الذي أدى إلى الحدث: المعالجة اليدوية، التصيد الاحتيالي ZAP، برنامج ضار ZAP |
| `ActionTrigger` | `string` | الإشارة إلى ما إذا كان قد تم تشغيل إجراء من قبل مسؤول (يدويا أو من خلال الموافقة على إجراء مؤتمت معلق)، أو بواسطة آلية خاصة، مثل ZAP أو التسليم الديناميكي |
| `ActionResult` | `string` | نتيجة الإجراء |
| `RecipientEmailAddress` | `string` | عنوان البريد الإلكتروني للمستلم، أو عنوان البريد الإلكتروني للمستلم بعد توسيع قائمة التوزيع |
| `DeliveryLocation` | `string` | الموقع الذي تم فيه تسليم البريد الإلكتروني: علبة الوارد/المجلد، العناصر المحلية/الخارجية، غير الهام، العزل، فشل، إسقاط، العناصر المحذوفة |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد متكرر. لتعريف الأحداث الفريدة، يجب استخدام هذا العمود بالتزامن مع أعمدة DeviceName وStamp timestamp. |
| `ThreatTypes` | `string` | حكم من مكدس تصفية البريد الإلكتروني بشأن ما إذا كان البريد الإلكتروني يحتوي على برامج ضارة أو تصيد احتيالي أو تهديدات أخرى |
| `DetectionMethods` | `string` | الأساليب المستخدمة للكشف عن البرامج الضارة أو التصيد الاحتيالي أو التهديدات الأخرى الموجودة في البريد الإلكتروني |

## <a name="supported-event-types"></a>أنواع الأحداث المعتمدة
يلتقط هذا الجدول الأحداث بالقيم التالية `ActionType` :

- **المعالجة اليدوية** – اتخذ المسؤول إجراء يدويا على رسالة بريد إلكتروني بعد تسليمها إلى علبة بريد المستخدم. ويشمل ذلك الإجراءات التي يتم اتخاذها يدويا من خلال [مستكشف التهديدات](../office-365-security/threat-explorer.md) أو الموافقات على [إجراءات التحقيق والاستجابة التلقائية (AIR](m365d-autoir-actions.md)).
- **Phish ZAP** – اتخذت [عملية الإزالة التلقائية لمدة صفر ساعة (ZAP)](../office-365-security/zero-hour-auto-purge.md) إجراء على رسالة بريد إلكتروني للتصيد الاحتيالي بعد التسليم.
- **Malware ZAP** – اتخذت عملية الإزالة التلقائية لمدة صفر ساعة (ZAP) إجراء على رسالة بريد إلكتروني تم العثور عليها تحتوي على برامج ضارة بعد التسليم.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
