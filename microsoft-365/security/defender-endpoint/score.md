---
title: أساليب النقاط وخصائصها
description: استرداد درجة التعرض للضوء في مؤسستك، والنتيجة الآمنة للجهاز، والنتيجة التعرض للضوء حسب مجموعة الأجهزة
keywords: apis وpis الرسوم البيانية و apis المعتمدة والنتيجة والنتيجة التعرض للضوء والنتيجة الآمنة للجهاز والنتيجة التعرض للضوء حسب مجموعة الأجهزة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fe69b42c2d8bf80089b749cd41e59664cc2921e3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63575777"
---
# <a name="score-resource-type"></a>نوع مورد الدرجة

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

الأسلوب|نوع الإرجاع|الوصف
:---|:---|:---
[الحصول على نقاط التعرض للضوء](get-exposure-score.md)|[النتيجة](score.md)|احصل على درجة التعرض في المؤسسة.
[الحصول على نقاط آمنة للجهاز](get-device-secure-score.md)|[النتيجة](score.md)|احصل على نقاط آمنة لجهاز المؤسسة.
[درجة التعرض للقائمة حسب مجموعة الأجهزة](get-machine-group-exposure-score.md)|[النتيجة](score.md)|سرد النقاط حسب مجموعة الأجهزة.

## <a name="properties"></a>الخصائص

الخاصية|النوع|الوصف
:---|:---|:---
النتيجة|مزدوج|النتيجة الحالية.
الوقت|DateTime|التاريخ والوقت الذي تم فيه استدعاء هذه API.
RbacGroupName|سلسلة|اسم مجموعة الجهاز.
RbacGroupId|سلسلة|"معرّف مجموعة الأجهزة".
