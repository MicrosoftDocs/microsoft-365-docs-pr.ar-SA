---
title: جدول DeviceTvmSoftwareVulnerabilitiesKB في مخطط الصيد المتقدم
description: تعرف على نقاط الضعف في البرامج التي تم تعقبها بواسطة برنامج & إدارة الثغرات في جدول DeviceTvmSoftwareVulnerabilitiesKB في مخطط الصيد المتقدم.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، وm365، والبحث، والاستعلام، وبيانات التعقب، والمرجع، والمرجع، و kusto، والأعمدة، ونوع البيانات، والوصف، والتهديد & إدارة الثغرات الأمنية، و TVM، وإدارة الأجهزة، والبرامج، والمخزون، والنقاط الأمنية، ومرجع CVE، و CVSS، و DeviceTvmSoftwareVulnerabilitiesKB
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
ms.openlocfilehash: 545e2a3ba12924d364facda14a7a564ead212f30
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570382"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftwareVulnerabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية



يحتوي `DeviceTvmSoftwareVulnerabilitiesKB` الجدول في مخطط الصيد المتقدم على قائمة بنقاط الضعف التي & [إدارة](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) الثغرات في تقييم الأجهزة لها. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `CveId` | `string` | معرف فريد تم تعيينه إلى ثغرة الأمان ضمن نظام الثغرات والتعرضات الشائعة (CVE) |
| `CvssScore` | `string` | درجة الخطورة المعينة لثغرة الأمان ضمن نظام تسجيل نقاط الضعف الشائع (CVSS) |
| `IsExploitAvailable` | `boolean` | تشير إلى ما إذا كان رمز استغلال الثغرة الأمنية متوفرا بشكل عام |
| `VulnerabilitySeverityLevel` | `string` | مستوى الخطورة المعين إلى ثغرة الأمان استنادا إلى نقاط CVSS والعوامل الديناميكية التي تتأثر بمشهد المخاطر |
| `LastModifiedTime` | `datetime` | تاريخ وتاريخ آخر تعديل للصنف أو بيانات التعريف ذات الصلة |
| `PublishedDate` | `datetime` | تم الكشف عن ثغرة أمنية في التاريخ للجمهور |
| `VulnerabilityDescription` | `string` | وصف الضعف والمخاطر المقترنة به |
| `AffectedSoftware` | `string` | قائمة بجميع منتجات البرامج المتأثرة بالهشاشة |

## <a name="related-topics"></a>المواضيع ذات الصلة

- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على المخاطر & إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)