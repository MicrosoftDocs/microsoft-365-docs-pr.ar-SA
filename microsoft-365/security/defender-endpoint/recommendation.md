---
title: أساليب التوصيات وخصائصها
description: استرداد أحدث التنبيهات.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيهات، الأخيرة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: f6e8295d83d5ab6fb86726903800d2779f394836
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63575778"
---
# <a name="recommendation-resource-type"></a>نوع مورد التوصيات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>الأساليب

<br>

****

|الأسلوب|نوع الإرجاع|الوصف|
|---|---|---|
|[سرد كل التوصيات](get-all-recommendations.md)|مجموعة التوصيات|استرداد قائمة بكل توصيات الأمان التي تؤثر على المؤسسة|
|[الحصول على توصية بواسطة الم ID](get-recommendation-by-id.md)|توصية|استرداد توصية أمان بواسطة المرجع|
|[الحصول على برنامج توصية](list-recommendation-software.md)|[البرامج](software.md)|استرداد توصية أمان ذات صلة برامج معينة|
|[الحصول على أجهزة التوصيات](get-recommendation-machines.md)|مجموعة MachineRef|استرداد قائمة الأجهزة المقترنة بتوصية الأمان|
|[الحصول على نقاط الضعف في التوصيات](get-recommendation-vulnerabilities.md)|[مجموعة نقاط الضعف](vulnerability.md)|استرداد قائمة نقاط الضعف المقترنة بتوصيات الأمان|
|

## <a name="properties"></a>الخصائص

<br>

****

|الخاصية|النوع|الوصف|
|---|---|---|
|الم id|سلسلة|"معرّف التوصية"|
|productName|سلسلة|اسم البرنامج ذي الصلة|
|recommendationName|سلسلة|اسم التوصية|
|نقاط الضعف|طويل|عدد نقاط الضعف المكتشفة|
|المورد|سلسلة|اسم المورد ذي الصلة|
|recommendedVersion|سلسلة|الإصدار المستحسن|
|المستحسنProgram|سلسلة|البرنامج المستحسن|
|recommendedVendor|سلسلة|المورد المستحسن|
|recommendationCategory|سلسلة|فئة التوصيات. القيم المحتملة هي: "الحسابات" و"التطبيق" و"الشبكة" و"OS" و"SecurityControls"|
|الفئة الفرعية|سلسلة|الفئة الفرعية للتوصية|
|severityScore|مزدوج|التأثير المحتمل لتكوين Microsoft Secure Score للأجهزة (1-10)|
|publicExploit|منطقي|يتوفر استغلال عام|
|activeAlert|منطقي|التنبيه النشط مقترن بهذه التوصية|
|associatedThreats|مجموعة سلاسل|يقترن تقرير تحليل المخاطر بهذه التوصية|
|remediationType|سلسلة|نوع المعالجة. القيم المحتملة هي: "ConfigurationChange", "Update","Upgrade","Uninstall"|
|الحالة|تعداد|حالة استثناء التوصية. القيم المحتملة هي: "نشط" و"استثناء"|
|configScoreImpact|مزدوج|تأثير "نقاط Microsoft الآمنة للأجهزة"|
|التعرض للضوءتفعية|مزدوج|تأثير درجة التعرض للضوء|
|totalMachineCount|طويل|عدد الأجهزة المثبتة|
|exposedMachinesCount|طويل|عدد الأجهزة المثبتة التي يتم عرضها لنقاط الضعف|
|nonProductivityImpactedAssets|طويل|عدد الأجهزة غير المتأثرة|
|relatedComponent|سلسلة|مكون البرامج ذات الصلة|
|
