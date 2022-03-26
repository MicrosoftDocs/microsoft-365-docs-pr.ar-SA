---
title: البحث عن الأجهزة المعرضة
description: تعرف على إدارة المخاطر والثغرات الأمنية يمكن استخدامها لمساعدة مسؤولو الأمان، لمسؤولي المعلومات، و SecOps على التعاون في العمل.
keywords: سيناريوهات Microsoft Defender ل Endpoint-tvm وسيناريوهات Microsoft Defender for Endpoint و tvm و tvm وتقليل المخاطر والتعرض لنقاط الضعف في & وتقليل المخاطر والثغرات وتحسين تكوين الأمان وزيادة نقاط الأمان في Microsoft Secure للأجهزة وزيادة المخاطر في & نقاط الضعف في Microsoft Secure Score للأجهزة ونقاط Microsoft Secure Score للأجهزة ونقاط التعرض للضوء و عناصر التحكم بالأمان
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 40544ab3879acd026d7f327e63d02bdb79d00d83
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63572237"
---
# <a name="hunt-for-exposed-devices---threat-and-vulnerability-management"></a>البحث عن الأجهزة المعرضة - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="use-advanced-hunting-to-find-devices-with-vulnerabilities"></a>استخدام الصيد المتقدم للعثور على الأجهزة التي بها نقاط ضعف

الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الخام. يمكنك فحص الأحداث في شبكتك بشكل استباقي لتحديد موقع مؤشرات التهديدات والكيانات. يتيح الوصول المرن إلى البيانات البحث بدون قيود عن التهديدات المعروفة والمحتملة. [تعرف على المزيد حول الصيد المتقدم](advanced-hunting-overview.md)

### <a name="schema-tables"></a>جداول المخطط

- [DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md) - مخزون البرامج المثبتة على الأجهزة، بما في ذلك معلومات الإصدار الخاصة بها ووضع انتهاء الدعم.

- [DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md) - نقاط الضعف في البرامج الموجودة على الأجهزة وقائمة تحديثات الأمان المتوفرة التي تعالج كل ثغرة أمنية.

- [DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md) - قاعدة معارف الثغرات التي يتم الكشف عنها بشكل عام، بما في ذلك ما إذا كانت التعليمات البرمجية للاستغلال متوفرة بشكل عام.

- [DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md) - إدارة الثغرات الأمنية التقييم، مما يشير إلى حالة تكوينات الأمان المختلفة على الأجهزة.

- [DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md) - قاعدة معارف لتكوينات الأمان المختلفة المستخدمة بواسطة إدارة الثغرات & المخاطر لتقييم الأجهزة؛ يتضمن تعيينات لمعايير ومقاييس مختلفة

## <a name="check-which-devices-are-involved-in-high-severity-alerts"></a>التحقق من الأجهزة المتدخلة في تنبيهات عالية الخطورة

1. انتقل إلى **البحث** \> **المتقدم للصيد** من جزء التنقل على الجانب الأيسر Microsoft 365 Defender المدخل.

2. قم بالتمرير لأسفل وصولا إلى مخطط الصيد المتقدم ل TVM لكي تطلع نفسك على أسماء الأعمدة.

3. أدخل الاستعلامات التالية:

    ```kusto
    // Search for devices with High active alerts or Critical CVE public exploit
    let DeviceWithHighAlerts = AlertInfo
    | where Severity == "High"
    | project Timestamp, AlertId, Title, ServiceSource, Severity
    | join kind=inner (AlertEvidence | where EntityType == "Machine" | project AlertId, DeviceId, DeviceName) on AlertId
    | summarize HighSevAlerts = dcount(AlertId) by DeviceId;
    let DeviceWithCriticalCve = DeviceTvmSoftwareVulnerabilities
    | join kind=inner(DeviceTvmSoftwareVulnerabilitiesKB) on CveId
    | where IsExploitAvailable == 1 and CvssScore >= 7
    | summarize NumOfVulnerabilities=dcount(CveId),
    DeviceName=any(DeviceName) by DeviceId;
    DeviceWithCriticalCve
    | join kind=inner DeviceWithHighAlerts on DeviceId
    | project DeviceId, DeviceName, NumOfVulnerabilities, HighSevAlerts
    ```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [توصيات الأمان](tvm-security-recommendation.md)
- [واجهات برمجة التطبيقات](next-gen-threat-and-vuln-mgt.md#apis)
- [تكوين الوصول إلى البيانات إدارة المخاطر والثغرات الأمنية الأدوار](user-roles.md#create-roles-and-assign-the-role-to-an-azure-active-directory-group)
- [نظرة عامة متقدمة حول الصيد](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [كل الجداول المتقدمة للصيد](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference.md)
