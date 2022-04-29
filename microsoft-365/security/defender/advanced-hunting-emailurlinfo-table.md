---
title: جدول EmailUrlInfo في مخطط التتبع المتقدم
description: تعرف على معلومات URL أو الارتباط في جدول EmailUrlInfo لمخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، EmailUrlInfo، معرف رسالة الشبكة، url، الارتباط
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
ms.openlocfilehash: 9453a5a7ddb48ff09ca217aa23c5e557d57d00e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130944"
---
# <a name="emailurlinfo"></a>EmailUrlInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لـ Office 365

`EmailUrlInfo` يحتوي الجدول في مخطط [التتبع المتقدم](advanced-hunting-overview.md) على معلومات حول عناوين URL على رسائل البريد الإلكتروني والمرفقات التي تتم معالجتها بواسطة Microsoft Defender لـ Office 365. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول. 

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، [راجع مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، تم إنشاؤه بواسطة Microsoft 365 |
| `Url` | `string` | URL الكامل في موضوع البريد الإلكتروني أو النص الأساسي أو المرفق |
| `UrlDomain` | `string` | اسم المجال أو اسم المضيف ل URL |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد متكرر. لتعريف الأحداث الفريدة، يجب استخدام هذا العمود بالتزامن مع أعمدة DeviceName وStamp timestamp |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
