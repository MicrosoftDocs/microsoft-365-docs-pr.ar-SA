---
title: Microsoft 365 Defender التكامل مع Microsoft Sentinel
description: استخدم Microsoft Sentinel ك SIEM Microsoft 365 Defender الأحداث والحوادث.
keywords: الأحداث والتنبيهات، التحقيق، التحليل، الاستجابة، الارتباط، الهجوم، الأجهزة، الأجهزة، المستخدمون، الهويات، الهوية، علبة البريد، البريد الإلكتروني، 365، microsoft، m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: d0add9fe000966cdeb2ffc5ce23e4ba0690bbadb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578249"
---
# <a name="microsoft-365-defender-integration-with-microsoft-sentinel"></a>Microsoft 365 Defender التكامل مع Microsoft Sentinel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يرسل Microsoft 365 Defender Microsoft Sentinel (preview) جميع Microsoft 365 Defender والتنبيهات إلى Microsoft Sentinel ويحافظ على مزامنة الأحداث. 

بمجرد إضافة الموصل، ستتضمن أحداث Microsoft 365 Defender&mdash; جميع التنبيهات والكيانات والمعلومات ذات الصلة المقترنة التي تم تلقيها من Microsoft Defender لنقطة النهاية و Microsoft Defender for Identity و Microsoft Defender for Office 365 و Microsoft Defender لتطبيقات السحابة&mdash; يتم تدفقها إلى Microsoft Sentinel كالبيانات الخاصة بمعلومات الأمان وإدارة الأحداث (SIEM)، مما يوفر لك السياق لتنفيذ الفرز والاستجابة للحوادث باستخدام Microsoft Sentinel. 

بمجرد الوصول إلى Microsoft Sentinel، تبقى الأحداث متزامنة بشكل ثنائي الاتجاه مع Microsoft 365 Defender، مما يسمح لك ب الاستفادة من مزايا كل من مدخل Microsoft 365 Defender و Microsoft Sentinel في مدخل Azure للتحري عن الحادث والاستجابة له.

شاهد هذه النظرة العامة القصيرة حول تكامل Microsoft Sentinel مع Microsoft 365 Defender (4 دقائق).

<br>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRo]


إليك كيفية عمل ذلك.

:::image type="content" source="../../media/microsoft-365-defender-integration-with-azure-sentinel/microsoft-365-defender-integration-with-azure-sentinel.png" alt-text="تدفق بيانات الحادث ومشاركتها بين Microsoft 365 Defender Microsoft Sentinel.":::

## <a name="next-steps"></a>الخطوات التالية

1. احصل على فهم أعمق [لتكامل Microsoft 365 Defender مع Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).
2. [الاتصال البيانات من Microsoft 365 Defender إلى Microsoft Sentinel](/azure/sentinel/connect-microsoft-365-defender).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الأحداث في Microsoft 365 Defender](incidents-overview.md)
- [التحقق من الأحداث باستخدام Microsoft Sentinel](/azure/sentinel/tutorial-investigate-cases)
