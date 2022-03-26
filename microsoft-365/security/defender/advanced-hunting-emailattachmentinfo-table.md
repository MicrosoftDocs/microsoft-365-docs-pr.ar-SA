---
title: جدول EmailAttachmentInfo في مخطط الصيد المتقدم
description: تعرف على معلومات مرفق البريد الإلكتروني في جدول EmailAttachmentInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و EmailAttachmentInfo، ومرجع رسالة الشبكة، والمرسل، والمستلم، ومرجع المرفق، واسم المرفق، وحكم البرامج الضارة
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
ms.openlocfilehash: ac3e7aeff6778709f68aa1da74446cf55a1a6c06
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63572362"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

يحتوي `EmailAttachmentInfo` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول المرفقات على رسائل البريد الإلكتروني التي تتم معالجتها بواسطة Microsoft Defender Office 365. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، الذي تم إنشاؤه بواسطة Microsoft 365 |
| `SenderFromAddress` | `string` | عنوان البريد الإلكتروني للمرسل في رأس FROM، وهو مرئي لمستلمي البريد الإلكتروني على عملاء البريد الإلكتروني |
| `SenderDisplayName` | `string` | اسم المرسل المعروض في دفتر العنوان، عادة ما يكون خليطا من اسم معين أو أول وأول أول وأولية وسطى واسم عائلة أو اسم عائلة |
| `SenderObjectId` | `string` | معرف فريد لحساب المرسل في Azure AD |
| `RecipientEmailAddress` | `string` | عنوان البريد الإلكتروني للمستلم أو عنوان البريد الإلكتروني للمستلم بعد توسيع قائمة التوزيع |
| `RecipientObjectId` | `string` | معرف فريد لمستلم البريد الإلكتروني في Azure AD |
| `FileName` | `string` | اسم الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FileType` | `string` | نوع ملحق الملف |
| `SHA256` | `string` | SHA-256 للملف الذي تم تطبيق الإجراء المسجل عليه. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `ThreatTypes` | `string` | قرار من مكدس تصفية البريد الإلكتروني حول ما إذا كان البريد الإلكتروني يحتوي على برامج ضارة أو تصيد احتيالي أو تهديدات أخرى |
| `ThreatNames` | `string` | تم العثور على اسم الكشف عن البرامج الضارة أو التهديدات الأخرى |
| `DetectionMethods` | `string` | الأساليب المستخدمة للكشف عن البرامج الضارة أو التصيد الاحتيالي أو التهديدات الأخرى الموجودة في البريد الإلكتروني |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp. |
| `FileSize` | `string` | حجم الملف بالبايت |

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
