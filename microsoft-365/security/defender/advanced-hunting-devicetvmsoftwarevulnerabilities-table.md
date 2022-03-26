---
title: جدول DeviceTvmSoftwareVulnerabilities في مخطط الصيد المتقدم
description: تعرف على نقاط الضعف في البرامج الموجودة على الأجهزة وقائمة تحديثات الأمان المتوفرة التي تعالج كل ثغرة أمنية في جدول DeviceTvmSoftwareVulnerabilities في مخطط الصيد المتقدم.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، وm365، والبحث، والاستعلام، وبيانات التعقب، ومرجع المخطط، و kusto، والأعمدة، ونوع البيانات، والوصف، والتهديدات & إدارة الثغرات الأمنية، و TVM، وإدارة الأجهزة، والبرامج، والمخزون، والنقاط الضعف، ومرجع CVE، OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: a6588134ba2cdf166a465998cd0b1a4fd7134dbb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570714"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

>[!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

يحتوي `DeviceTvmSoftwareVulnerabilities` الجدول في مخطط الصيد المتقدم على قائمة المخاطر & [نقاط](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) الضعف في منتجات البرامج المثبتة. يتضمن هذا الجدول أيضا معلومات نظام التشغيل وملفات CVE ومعلومات الخطورة. يمكنك استخدام هذا الجدول، على سبيل المثال، للبحث عن الأحداث التي تتضمن أجهزة بها نقاط ضعف شديدة في برامجها. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

>[!NOTE]
> تم `DeviceTvmSoftwareInventory` استبدال `DeviceTvmSoftwareVulnerabilities` الجدولين و `DeviceTvmSoftwareInventoryVulnerabilities` . يتضمن الجدولان الأولان معا المزيد من الأعمدة التي يمكنك استخدامها للمساعدة في إعلام إدارة الثغرات الأمنية أو البحث عن الأجهزة المعرضة.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز. تشير إلى أنظمة تشغيل محددة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 و Windows 10 و Windows 7. |
| `OSVersion` | `string` | إصدار نظام التشغيل الذي يتم تشغيله على الجهاز |
| `OSArchitecture` | `string` | هندسة نظام التشغيل الذي يعمل على الجهاز |
| `SoftwareVendor` | `string` | اسم ناشر البرنامج |
| `SoftwareName` | `string` | اسم منتج البرنامج |
| `SoftwareVersion` | `string` | رقم إصدار منتج البرنامج |
| `CveId` | `string` | معرف فريد تم تعيينه إلى ثغرة الأمان ضمن نظام الثغرات والتعرضات الشائعة (CVE) |
| `VulnerabilitySeverityLevel` | `string` | مستوى الخطورة المعين إلى ثغرة الأمان استنادا إلى نقاط CVSS والعوامل الديناميكية التي تتأثر بمشهد المخاطر |
| `RecommendedSecurityUpdate` | `string` | اسم تحديث الأمان الذي وفره ناشر البرنامج أو وصفه لمعالجة الثغرة الأمنية |
| `RecommendedSecurityUpdateId` | `string` | معرف تحديثات الأمان القابلة للتطبيق أو المعرف لمقالات قاعدة المعارف أو الإرشادات المطابقة (KB) |



## <a name="related-topics"></a>المواضيع ذات الصلة

- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على المخاطر & إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)