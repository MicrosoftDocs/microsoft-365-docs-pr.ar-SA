---
title: EmailPostDeliveryEvents table في مخطط الصيد المتقدم
description: تعرف على إجراءات ما بعد التسليم التي تم Microsoft 365 البريد الإلكتروني في جدول EmailPostDeliveryEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و EmailPostDeliveryEvents، ومرجع رسالة الشبكة، والمرسل، والمستلم، ومرجع المرفق، واسم المرفق، وحكم البرامج الضارة، وحكم التصيد الاحتيالي، وعد المرفقات، وعد الارتباطات، وعد عنوان URL
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
ms.openlocfilehash: 59d611ae89aeedf386cd0dcad5939a9510f0820e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570529"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي `EmailPostDeliveryEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول إجراءات ما بعد التسليم التي تم اتخاذها على رسائل البريد الإلكتروني التي تتم معالجتها بواسطة Microsoft 365. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على مزيد من المعلومات حول رسائل البريد الإلكتروني الفردية، يمكنك أيضا استخدام [`EmailEvents`](advanced-hunting-emailevents-table.md)الجداول [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)[`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) و. للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، الذي تم إنشاؤه بواسطة Microsoft 365 |
| `InternetMessageId` | `string` | معرف عام للبريد الإلكتروني الذي تم تعيينه بواسطة نظام إرسال البريد الإلكتروني |
| `Action` | `string` | الإجراء الذي تم اتخاذه على الكيان |
| `ActionType` | `string` | نوع النشاط الذي تسبب في الحدث: المعالجة اليدوية، التصيد الاحتيالي ZAP، البرامج الضارة ZAP |
| `ActionTrigger` | `string` | تشير إلى ما إذا كان أحد الإجراءات قد تم تشغيله من قبل مسؤول (يدويا أو من خلال الموافقة على إجراء تلقائي معلق)، أو بواسطة آلية خاصة، مثل ZAP أو التسليم الديناميكي |
| `ActionResult` | `string` | نتيجة الإجراء |
| `RecipientEmailAddress` | `string` | عنوان البريد الإلكتروني للمستلم أو عنوان البريد الإلكتروني للمستلم بعد توسيع قائمة التوزيع |
| `DeliveryLocation` | `string` | الموقع الذي تم تسليم البريد الإلكتروني فيه: علبة الوارد/المجلد، العناصر المحلية/الخارجية، البريد غير الهام، الفحص، فشل، إسقاط، العناصر المحذوفة |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp. |
| `ThreatTypes` | `string` | قرار من مكدس تصفية البريد الإلكتروني حول ما إذا كان البريد الإلكتروني يحتوي على برامج ضارة أو تصيد احتيالي أو تهديدات أخرى |
| `DetectionMethods` | `string` | الأساليب المستخدمة للكشف عن البرامج الضارة أو التصيد الاحتيالي أو التهديدات الأخرى الموجودة في البريد الإلكتروني |

## <a name="supported-event-types"></a>أنواع الأحداث المعتمدة
يلتقط هذا الجدول الأحداث التي بها القيم `ActionType` التالية:

- **المعالجة اليدوية** – اتخذ المسؤول إجراء يدويا على رسالة بريد إلكتروني بعد تسليمها إلى علبة بريد المستخدم. يشمل ذلك الإجراءات التي يتم اتخاذها يدويا من خلال ["](../office-365-security/threat-explorer.md) مستكشف التهديدات" أو الموافقات على إجراءات الاستجابة والتحريات [التلقائية (AIR](m365d-autoir-actions.md)).
- **Phish ZAP** – اتخذت عملية إزالة تلقائية [لمدة ساعة (ZAP)](../office-365-security/zero-hour-auto-purge.md) إجراء على رسالة بريد إلكتروني تصيد احتيالي بعد التسليم.
- **البرامج الضارة ZAP** – اتخذت عملية إزالة تلقائية لمدة ساعة (ZAP) إجراء على رسالة بريد إلكتروني تم العثور عليها تحتوي على البرامج الضارة بعد التسليم.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
