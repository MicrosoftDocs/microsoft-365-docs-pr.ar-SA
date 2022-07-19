---
title: جدول DeviceTvmInfoGathering في مخطط التتبع المتقدم
description: تعرف على أحداث التقييم بما في ذلك حالة التكوينات المختلفة وحالات مساحة الأجزاء المعرضة للهجوم للأجهزة في جدول DeviceTvmInfoGathering لمخطط التتبع المتقدم.
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
ms.openlocfilehash: 738168153738f8bf4e12220829114efc0cc8beb2
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857466"
---
# <a name="devicetvminfogathering"></a>DeviceTvmInfoGathering

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

>[!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

`DeviceTvmInfoGathering` يحتوي الجدول في مخطط التتبع المتقدم على أحداث تقييم [إدارة الثغرات الأمنية في Microsoft Defender](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) بما في ذلك حالة التكوينات المختلفة وحالات مساحة سطح الهجوم للأجهزة. يمكنك استخدام هذا الجدول للبحث عن أحداث التقييم المتعلقة بالتخفيف لمدة صفر أيام، وتقييم الوضع للتهديدات الناشئة التي تدعم تقارير حالة التخفيف من تحليلات التهديدات، وإصدارات بروتوكول TLS الممكنة على الخوادم، والمزيد. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، راجع [مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `LastSeenTime` | `datetime` | تاريخ ووقت آخر مرة شاهدت فيها الخدمة الجهاز |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `OSPlatform` | `string` | نظام أساسي لنظام التشغيل الذي يعمل على الجهاز. يشير هذا إلى أنظمة تشغيل معينة، بما في ذلك الاختلافات داخل العائلة نفسها، مثل Windows 10 وWindows 7. |
| `AdditionalFields` | `string` | معلومات إضافية حول الحدث  |

على سبيل المثال، لعرض الأجهزة المتأثرة [بالثغرة الأمنية Log4Shell](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) حيث لم يتم تطبيق التخفيف من المخاطر البديلة بعد، أو تم تطبيقها وهي معلقة لإعادة التشغيل، يمكنك استخدام الاستعلام التالي.

```kusto
DeviceTvmInfoGathering
| where AdditionalFields.Log4JEnvironmentVariableMitigation in ("RebootRequired", "false")
| join kind=inner (
    DeviceTvmSoftwareVulnerabilities
    | where CveId == "CVE-2021-44228"
) on DeviceId
| summarize any(DeviceName), any(AdditionalFields.Log4JEnvironmentVariableMitigation) by DeviceId
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [DeviceTvmInfoGatheringKB](advanced-hunting-devicetvminfogatheringkb-table.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على إدارة الثغرات الأمنية في Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [تعرف على كيفية إدارة ثغرة Log4Shell الأمنية في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/tvm-manage-log4shell-guidance)