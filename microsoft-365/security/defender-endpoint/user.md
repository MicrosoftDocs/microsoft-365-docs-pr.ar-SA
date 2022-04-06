---
title: نوع مورد المستخدم
description: استرداد أحدث تنبيهات Microsoft Defender لنقطة النهاية ذات الصلة بالمستخدمين.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيهات، الأخيرة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 01b7eb32415e431dce37935abb4a1a69776db0f9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583191"
---
# <a name="user-resource-type"></a>نوع مورد المستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

الأسلوب|نوع الإرجاع|الوصف
---|---|---
[قائمة التنبيهات ذات الصلة بالمستخدم](get-user-related-alerts.md)|[مجموعة التنبيهات](alerts.md)|سرد كل التنبيهات المقترنة [بمستخدم](user.md).
[قائمة الأجهزة ذات الصلة بالمستخدم](get-user-related-machines.md)|[مجموعة](machine.md) الآلات|سرد جميع الأجهزة التي تم تسجيل دخولها من قبل [المستخدم](user.md).
