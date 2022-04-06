---
title: جدول EmailUrlInfo في مخطط الصيد المتقدم
description: تعرف على معلومات الارتباط أو URL في جدول EmailUrlInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و EmailUrlInfo، ومرجع رسالة الشبكة، وurl، والارتباط
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
ms.openlocfilehash: d0c9a8f1456aaeedbc8d296a1f738d0b2c57a156
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63583141"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي `EmailUrlInfo` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول عناوين URL على رسائل البريد الإلكتروني والمرفقات التي يعالجها Microsoft Defender Office 365. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول. 

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، الذي تم إنشاؤه بواسطة Microsoft 365 |
| `Url` | `string` | عنوان URL الكامل في موضوع البريد الإلكتروني أو النص أو المرفق |
| `UrlDomain` | `string` | اسم المجال أو اسم المضيف ل URL |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
