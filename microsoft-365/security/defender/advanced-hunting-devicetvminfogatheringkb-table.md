---
title: جدول DeviceTvmInfoGatheringKB في مخطط التتبع المتقدم
description: تعرف على بيانات التعريف لأحداث التقييم في جدول DeviceTvmInfoGathering لمخطط التتبع المتقدم.
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
ms.openlocfilehash: c654ca395762426072bf8e5e20fd3f62e78a480c
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66857501"
---
# <a name="devicetvminfogatheringkb"></a>DeviceTvmInfoGatheringKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

`DeviceTvmInfoGatheringKB` يحتوي الجدول في مخطط التتبع المتقدم على بيانات تعريف لبيانات أحداث التقييم [إدارة الثغرات الأمنية في Microsoft Defender](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) التي تم جمعها في `DeviceTvmInfoGathering` الجدول. `DeviceTvmInfoGatheringKB` يحتوي الجدول على قائمة بتكوينات مختلفة وتقييمات مساحة سطح الهجوم المستخدمة بواسطة جمع معلومات إدارة الثغرات الأمنية في Defender لتقييم الأجهزة. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، راجع [مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `IgId` | `string` | معرف فريد لجزء المعلومات التي تم جمعها |
| `FieldName` | `string` | اسم الحقل الذي تظهر فيه هذه المعلومات في عمود AdditionalFields لجدول DeviceTvmInfoGathering |
| `Description` | `string` | وصف المعلومات التي تم جمعها |
| `Categories` | `string` | قائمة بالفئات التي تنتمي إليها المعلومات، بتنسيق صفيف JSON  |
| `DataStructure` | `string` | بنية بيانات المعلومات التي تم جمعها  |

يمكنك استخدام هذا الجدول لاستكشاف أنواع المعلومات المتوفرة حتى تتمكن في `DeviceTvmInfoGathering` وقت لاحق من ضبط استعلام التتبع الخاص بك.

على سبيل المثال، للاطلاع على قائمة المعلومات التي يتم تجميعها، يمكنك تجربة الاستعلام التالي:

```kusto
// Check out what is being collected 
DeviceTvmInfoGatheringKB  
```

من النتائج، لنفترض أنك أصبحت مهتما بالفئات المتوفرة، يمكنك استخدام الاستعلام التالي:

```kusto
// Return all available categories 
DeviceTvmInfoGatheringKB 
| mv-expand Categories to typeof(string) 
| distinct Categories 
```

بعد ذلك، لنفترض أنك تريد رؤية فئات التقييم التي تتضمن بروتوكول TLS:

```kusto
// Return all findings for a specified category 
DeviceTvmInfoGatheringKB 
| where Categories contains "tls" 
```

باستخدام الحقول الناتجة، يمكنك بعد ذلك استخدام `DeviceTvmInfoGathering` الجدول للحصول على قائمة بالأجهزة باستخدام إصدار عميل TLS 1.0.

```kusto
// Return all devices on which the TLS version 1.0 is enabled 
DeviceTvmInfoGathering 
| where AdditionalFields.TlsClient10 == "Enabled" or AdditionalFields.TlsServer10 == "Enabled" 
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [DeviceTvmInfoGathering](advanced-hunting-devicetvminfogathering-table.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على إدارة الثغرات الأمنية في Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
