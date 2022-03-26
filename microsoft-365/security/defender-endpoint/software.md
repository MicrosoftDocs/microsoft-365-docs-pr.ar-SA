---
title: أساليب البرنامج وخصائصه
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
ms.openlocfilehash: 6b08b7c4ebb0a818dec5bdf799c3114d91764259
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573368"
---
# <a name="software-resource-type"></a>نوع مورد البرنامج

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="methods"></a>الأساليب

<br>

****

|الأسلوب|نوع الإرجاع|الوصف|
|---|---|---|
|[قائمة البرامج](get-software.md)|مجموعة برامج|سرد مخزون البرامج التنظيمية|
|[الحصول على البرامج حسب الم ID](get-software-by-id.md)|البرامج|الحصول على برنامج معين من خلال "معرّف البرامج" الخاص به|
|[توزيع إصدار برنامج القائمة](get-software-ver-distribution.md)|مجموعة التوزيع|سرد توزيع إصدار البرنامج حسب "معرّف البرنامج"|
|[سرد الأجهزة حسب البرنامج](get-machines-by-software.md)|مجموعة MachineRef|استرداد قائمة بالأجهزة المقترنة بمرجع البرنامج|
|[الثغرات في القائمة حسب البرنامج](get-vuln-by-software.md)|[مجموعة نقاط الضعف](vulnerability.md)|استرداد قائمة نقاط الضعف المقترنة بم ID البرنامج|
|[فقدان KBs](get-missing-kbs-software.md)|مجموعة KB|الحصول على قائمة ب KBs المفقودة المقترنة بم ID البرنامج|
|

## <a name="properties"></a>الخصائص

<br>

****

|الخاصية|النوع|الوصف|
|---|---|---|
|الم id|سلسلة|"معرّف البرامج"|
|الاسم|سلسلة|اسم البرنامج|
|المورد|سلسلة|اسم ناشر البرامج|
|نقاط الضعف|طويل|عدد نقاط الضعف المكتشفة|
|publicExploit|منطقي|يوجد استغلال عام لبعض نقاط الضعف|
|activeAlert|منطقي|التنبيه النشط مقترن بهذا البرنامج|
|exposedMachines|طويل|عدد الأجهزة المعرضة|
|impactScore|مزدوج|تأثير نقاط التعرض للضوء لهذا البرنامج|
|
