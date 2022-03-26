---
title: جدول DeviceTvmSecureConfigurationAssessment في مخطط الصيد المتقدم
description: تعرف على أحداث تقييم الأمان في جدول DeviceTvmSecureConfigurationAssessment في مخطط الصيد المتقدم. توفر هذه الأحداث معلومات الجهاز وتفاصيل تكوين الأمان والتأثير ومعلومات التوافق.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، وm365، والبحث، والاستعلام، وبيانات التعقب، ومرجع المخطط، و kusto، والأعمدة، ونوع البيانات، والوصف، والتهديد & إدارة الثغرات الأمنية، و TVM، وإدارة الأجهزة، وتكوين الأمان، و DeviceTvmSecureConfigurationAssesment
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
ms.openlocfilehash: 43f44458cde7d466d1097034e7bcc9d0e3072745
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570410"
---
# <a name="devicetvmsecureconfigurationassessment"></a>DeviceTvmSecureConfigurationAssessment

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية


يحتوي كل صف في `DeviceTvmSecureConfigurationAssessment` الجدول على حدث تقييم لتكوين أمان معين من [المخاطر & إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). استخدم هذا المرجع للتحقق من نتائج التقييم الأخيرة وتحديد ما إذا كانت الأجهزة متوافقة أم لا.

يمكنك ضم هذا الجدول باستخدام [الجدول DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) `ConfigurationId` `ConfigurationDescription` `DeviceTvmSecureConfigurationAssessmentKB` باستخدام، على سبيل المثال، عرض الوصف النصي لتكوين من عمود الجدول، في نتائج تقييم التكوين.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يتم تشغيله على الجهاز. تشير إلى أنظمة تشغيل محددة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 و Windows 10 و Windows 7.|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه إنشاء السجل |
| `ConfigurationId` | `string` | معرف فريد لتكوين معين |
| `ConfigurationCategory` | `string` | الفئة أو المجموعة التي ينتمي إليها التكوين: التطبيق، نظام التشغيل، الشبكة، الحسابات، عناصر التحكم في الأمان |
| `ConfigurationSubcategory` | `string` | الفئة الفرعية أو التجميع الفرعي الذي ينتمي إليه التكوين. في العديد من الحالات، تصف السلسلة قدرات أو ميزات معينة. |
| `ConfigurationImpact` | `string` | التأثير تصنيف التكوين على درجة التكوين الإجمالية (1-10) |
| `IsCompliant` | `boolean` | تشير إلى ما إذا كان التكوين أو النهج مكونا بشكل صحيح |
| `IsApplicable` | `boolean` | تشير إلى ما إذا كان التكوين أو النهج ينطبق على الجهاز |
| `Context` | `string` | معلومات سياقية إضافية حول التكوين أو النهج |
| `IsExpectedUserImpact` | `boolean` | تشير إلى ما إذا كان سيكون هناك تأثير للمستخدم إذا تم تطبيق التكوين أو النهج |

يمكنك تجربة هذا الاستعلام على سبيل المثال لإرجاع معلومات على الأجهزة ذات تكوينات برامج الحماية من الفيروسات غير المتوافقة مع بيانات تعريف التكوين ذات الصلة من `DeviceTvmSecureConfigurationAssessmentKB` الجدول:

```kusto
// Get information on devices with antivirus configurations issues
DeviceTvmSecureConfigurationAssessment
| where ConfigurationSubcategory == 'Antivirus' and IsApplicable == 1 and IsCompliant == 0
| join kind=leftouter (
    DeviceTvmSecureConfigurationAssessmentKB
    | project ConfigurationId, ConfigurationName, ConfigurationDescription, RiskDescription, Tags, ConfigurationImpact
) on ConfigurationId
| project DeviceName, OSPlatform, ConfigurationId, ConfigurationName, ConfigurationCategory, ConfigurationSubcategory, ConfigurationDescription, RiskDescription, ConfigurationImpact, Tags
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على المخاطر & إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)