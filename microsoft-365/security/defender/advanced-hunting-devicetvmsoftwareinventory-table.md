---
title: DeviceTvmSoftwareInventory جدول في مخطط الصيد المتقدم
description: تعرف على مخزون البرامج في أجهزتك في جدول DeviceTvmSoftwareInventory لم المخطط المتقدم للصيد.
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
ms.openlocfilehash: a9a17c6e336704cfe09e1c864e9700a4492e8c87
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569863"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

>[!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.


يحتوي `DeviceTvmSoftwareInventory` الجدول في مخطط الصيد المتقدم على مخزون إدارة & الثغرات في [](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) البرامج المثبتة حاليا على الأجهزة في شبكتك، بما في ذلك معلومات إنهاء الدعم. يمكنك، على سبيل المثال، البحث عن الأحداث التي تتضمن أجهزة مثبتة مع إصدار برنامج معرض حاليا للخطر. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

>[!NOTE]
> تم `DeviceTvmSoftwareInventory` استبدال `DeviceTvmSoftwareVulnerabilities` الجدولين و `DeviceTvmSoftwareInventoryVulnerabilities` . يتضمن الجدولان الأولان معا المزيد من الأعمدة التي يمكنك استخدامها للمساعدة في إعلامك بأنشطة إدارة المخاطر أو البحث عن الأجهزة المعرضة.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز. يشير ذلك إلى أنظمة تشغيل محددة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 Windows 10 Windows 7. |
| `OSVersion` | `string` | إصدار نظام التشغيل الذي يتم تشغيله على الجهاز |
| `OSArchitecture` | `string` | هندسة نظام التشغيل الذي يعمل على الجهاز |
| `SoftwareVendor` | `string` | اسم مورد البرامج |
| `SoftwareName` | `string` | اسم منتج البرنامج |
| `SoftwareVersion` | `string` | رقم إصدار منتج البرنامج |
| `EndOfSupportStatus` | `string` | تشير إلى مرحلة دورة حياة منتج البرنامج بالنسبة إلى تاريخ انتهاء الدعم المحدد (EOS) أو تاريخ انتهاء العمر الإنتاجي (EOL) |
| `EndOfSupportDate` | `string` | تاريخ انتهاء الدعم (EOS) أو تاريخ انتهاء العمر (EOL) لمنتج البرنامج |
| `ProductCodeCpe` | `string` | CPE لمنتج البرنامج أو 'غير متوفر' حيث لا توجد CPE |


## <a name="related-topics"></a>المواضيع ذات الصلة

- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على المخاطر & إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)