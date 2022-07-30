---
title: جدول DeviceTvmSoftwareInventory في مخطط التتبع المتقدم
description: تعرف على مخزون البرامج في أجهزتك في جدول DeviceTvmSoftwareInventory لمخطط التتبع المتقدم.
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، إدارة الثغرات الأمنية & التهديد، أجهزة التلفزيون، إدارة الأجهزة، البرامج، المخزون، الثغرات الأمنية، معرف CVE، OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: aaab93748ea3bea8ce5de54f5996f5dbc6373f29
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67099074"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

>[!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.


`DeviceTvmSoftwareInventory` يحتوي الجدول في مخطط التتبع المتقدم على مخزون [إدارة الثغرات الأمنية & المخاطر](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) للبرامج المثبتة حاليا على الأجهزة في شبكتك، بما في ذلك معلومات نهاية الدعم. يمكنك، على سبيل المثال، البحث عن الأحداث التي تتضمن الأجهزة المثبتة مع إصدار برنامج ضعيف حاليا. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

>[!NOTE]
> تم `DeviceTvmSoftwareInventory` استبدال `DeviceTvmSoftwareInventoryVulnerabilities` الجدول والجداول`DeviceTvmSoftwareVulnerabilities`. يتضمن الجدولان الأولان معا المزيد من الأعمدة التي يمكنك استخدامها للمساعدة في إبلاغ أنشطة إدارة الفئات الضعيفة أو البحث عن الأجهزة المعرضة للخطر.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، راجع [مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز. يشير هذا إلى أنظمة تشغيل معينة، بما في ذلك الاختلافات داخل العائلة نفسها، مثل Windows 11 Windows 10 وWindows 7. |
| `OSVersion` | `string` | إصدار نظام التشغيل الذي يعمل على الجهاز |
| `OSArchitecture` | `string` | بنية نظام التشغيل الذي يعمل على الجهاز |
| `SoftwareVendor` | `string` | اسم مورد البرامج |
| `SoftwareName` | `string` | اسم منتج البرنامج |
| `SoftwareVersion` | `string` | رقم إصدار منتج البرنامج |
| `EndOfSupportStatus` | `string` | الإشارة إلى مرحلة دورة حياة منتج البرنامج بالنسبة إلى تاريخ انتهاء الدعم المحدد (EOS) أو تاريخ انتهاء العمر الافتراضي (EOL) |
| `EndOfSupportDate` | `string` | تاريخ انتهاء الدعم (EOS) أو تاريخ انتهاء العمر الافتراضي (EOL) لمنتج البرنامج |
| `ProductCodeCpe` | `string` | CPE لمنتج البرنامج أو "غير متوفر" حيث لا يوجد CPE |
| `CveTags` | `string` | صفيف من العلامات ذات الصلة ب CVE. العلامات المعتمدة حاليا هي "ZeroDay" و"NoSecurityUpdate".

## <a name="related-topics"></a>المواضيع ذات الصلة

- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على إدارة الثغرات الأمنية & المخاطر](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)