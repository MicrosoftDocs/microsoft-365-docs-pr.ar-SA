---
title: جدول AlertInfo في مخطط الصيد المتقدم
description: تعرف على أحداث جيل التنبيه في جدول AlertInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، وصيد التهديدات الإلكترونية، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، ونوع البيانات، والوصف، و AlertInfo، والتنبيه، والخطورة، والفئة، و MITRE، و ATT&CK، و Microsoft Defender for Endpoint، و Microsoft Defender ل Office 365، Microsoft Cloud App Security و MCAS و Microsoft Defender for Identity
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
ms.openlocfilehash: 0298b4f83ac748048215af4f5b1f8261a2a8c67c
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63573293"
---
# <a name="alertinfo"></a>AlertInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender



يحتوي `AlertInfo` الجدول في مخطط [](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول التنبيهات من Microsoft Defender ل Endpoint و Microsoft Defender ل Office 365 و Microsoft Defender for Cloud Apps و Microsoft Defender for Identity. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `AlertId` | `string` | معرف فريد للتنبيه |
| `Title` | `string` | عنوان التنبيه |
| `Category` | `string` | نوع مؤشر الخطر أو نشاط الخرق الذي يحدده التنبيه |
| `Severity` | `string` | تشير إلى التأثير المحتمل (عال أو متوسط أو منخفض) لمؤشر الخطر أو نشاط الخرق الذي يحدده التنبيه |
| `ServiceSource` | `string` | المنتج أو الخدمة التي وفرت معلومات التنبيه |
| `DetectionSource` | `string` | تقنية الكشف أو المستشعر الذي حدد المكون أو النشاط الجدير بالملاحظة |
| `AttackTechniques` | `string` | MITRE ATT&تقنيات CK المقترنة بنشاط تشغيل التنبيه |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
