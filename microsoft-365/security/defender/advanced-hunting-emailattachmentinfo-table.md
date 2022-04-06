---
title: جدول EmailAttachmentInfo في مخطط التتبع المتقدم
description: تعرف على معلومات مرفق البريد الإلكتروني في جدول EmailAttachmentInfo لمخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، EmailAttachmentInfo، معرف رسالة الشبكة، المرسل، المستلم، معرف المرفق، اسم المرفق، حكم البرامج الضارة
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
ms.openlocfilehash: e787f79b5af90f45dd2823f53402830c7fc287db
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664029"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

`EmailAttachmentInfo` يحتوي الجدول في مخطط [التتبع المتقدم](advanced-hunting-overview.md) على معلومات حول المرفقات على رسائل البريد الإلكتروني التي تتم معالجتها بواسطة Microsoft Defender لـ Office 365. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، [راجع مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، تم إنشاؤه بواسطة Microsoft 365 |
| `SenderFromAddress` | `string` | عنوان البريد الإلكتروني للمرسل في رأس FROM، وهو مرئي لمستلمي البريد الإلكتروني على عملاء البريد الإلكتروني |
| `SenderDisplayName` | `string` | اسم المرسل المعروض في دفتر العناوين، عادة ما يكون مزيجا من اسم معطى أو أول، وحرف أول متوسط، واسم العائلة أو اللقب |
| `SenderObjectId` | `string` | معرف فريد لحساب المرسل في Azure AD |
| `RecipientEmailAddress` | `string` | عنوان البريد الإلكتروني للمستلم، أو عنوان البريد الإلكتروني للمستلم بعد توسيع قائمة التوزيع |
| `RecipientObjectId` | `string` | معرف فريد لمستلم البريد الإلكتروني في Azure AD |
| `FileName` | `string` | اسم الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FileType` | `string` | نوع ملحق الملف |
| `SHA256` | `string` | SHA-256 من الملف الذي تم تطبيق الإجراء المسجل عليه. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `ThreatTypes` | `string` | حكم من مكدس تصفية البريد الإلكتروني بشأن ما إذا كان البريد الإلكتروني يحتوي على برامج ضارة أو تصيد احتيالي أو تهديدات أخرى |
| `ThreatNames` | `string` | تم العثور على اسم الكشف عن البرامج الضارة أو التهديدات الأخرى |
| `DetectionMethods` | `string` | الأساليب المستخدمة للكشف عن البرامج الضارة أو التصيد الاحتيالي أو التهديدات الأخرى الموجودة في البريد الإلكتروني |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد متكرر. لتعريف الأحداث الفريدة، يجب استخدام هذا العمود بالتزامن مع أعمدة DeviceName وStamp timestamp. |
| `FileSize` | `string` | حجم الملف بالبايت |

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
