---
title: DeviceTvmSecureConfiguration جدولAssessmentKB في مخطط الصيد المتقدم
description: تعرف على التكوينات الآمنة المتنوعة التي تم تقييمها بواسطة إدارة نقاط الضعف & في جدول DeviceTvmSecureConfigurationAssessmentKB في مخطط الصيد المتقدم.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و الخطر & إدارة الثغرات الأمنية، و TVM، وإدارة الأجهزة، وتكوين الأمان، إطار عمل MITRE ATT&CK، قاعدة المعارف، KB، DeviceTvmSecureConfigurationAssessmentKB
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
ms.openlocfilehash: 81f03a665a0c825388335c925cb908f3b931a918
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63571444"
---
# <a name="devicetvmsecureconfigurationassessmentkb"></a>DeviceTvmSecureConfigurationAssessmentKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية


يحتوي `DeviceTvmSecureConfigurationAssessmentKB` الجدول في مخطط الصيد المتقدم على معلومات حول التكوينات الآمنة المختلفة التي تم فحصها بواسطة & [إدارة نقاط الضعف](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). وتتضمن أيضا معلومات المخاطر، والمعايير الصناعية ذات الصلة، وTT ل MITRE&وأساليب CK المعمول بها.

لا يرجع هذا الجدول الأحداث أو السجلات. نوصي بضم هذا الجدول إلى [جدول DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) `ConfigurationId` باستخدام لعرض معلومات نصية حول تكوينات الأمان في التقييمات التي تم إرجاعها.

على سبيل المثال، عند الاستعلام عن `DeviceTvmSecureConfigurationAssessment` الجدول، قد ترغب `ConfigurationDescription` في عرض لتكوينات الأمان التي تظهر في نتائج التقييم. يمكنك الاطلاع على هذه المعلومات من خلال الانضمام إلى هذا الجدول لاستخدامه `DeviceTvmSecureConfigurationAssessment` `ConfigurationId` أو مشروعه `ConfigurationDescription`.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `ConfigurationId` | `string` | معرف فريد لتكوين معين |
| `ConfigurationImpact` | `string` | التأثير تصنيف التكوين على درجة التكوين الإجمالية (1-10) |
| `ConfigurationName` | `string` | اسم العرض الخاص بالتهيئة |
| `ConfigurationDescription` | `string` | وصف التكوين |
| `RiskDescription` | `string` | وصف الخطر المقترن |
| `ConfigurationCategory` | `string` | الفئة أو المجموعة التي ينتمي إليها التكوين: التطبيق، نظام التشغيل، الشبكة، الحسابات، عناصر التحكم في الأمان|
| `ConfigurationSubcategory` | `string` |الفئة الفرعية أو التجميع الفرعي الذي ينتمي إليه التكوين. في العديد من الحالات، يصف ذلك قدرات أو ميزات معينة. |
| `ConfigurationBenchmarks` | `string` | قائمة معايير الصناعة التي توصي بنفس التكوين أو التكوين المشابه |
| `Tags` | `string` | تسميات تمثل سمات مختلفة تستخدم لتعريف تكوين أمان أو تصنيفه |
| `RemediationOptions` | `string` | الإجراءات الموصى بها لتقليل أي مخاطر مقترنة أو معالجتها |

يمكنك تجربة استعلام المثال هذا لإرجاع بيانات تعريف التكوين ذات الصلة إلى جانب المعلومات على الأجهزة ذات تكوينات الحماية من الفيروسات غير المتوافقة من `DeviceTvmSecureConfigurationAssessment` الجدول:

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