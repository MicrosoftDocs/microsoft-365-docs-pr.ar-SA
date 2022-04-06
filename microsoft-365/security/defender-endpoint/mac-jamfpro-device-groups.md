---
title: إعداد مجموعات الأجهزة في Jamf Pro
description: تعرف على كيفية إعداد مجموعات الأجهزة في Jamf Pro for Microsoft Defender لنقطة النهاية على macOS
keywords: الجهاز، المجموعة، microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamfpro، macos، catalina، mojave، high sierra
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c22a1a68af2722e6b17d155a37632c1f6417b605
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471748"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>إعداد Microsoft Defender لنقطة النهاية على مجموعات أجهزة macOS في Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

قم بإعداد مجموعات الأجهزة بطريقة مماثلة لمجموعات تنظيم نهج المجموعة Microsoft Endpoint Configuration Manager مجموعات الأجهزة ومجموعات أجهزة Intune.

1. انتقل إلى **مجموعات الكمبيوتر الثابتة**.

2. حدد **جديد**. 

   :::image type="content" source="images/jamf-pro-static-group.png" alt-text="صفحة Jamf Pro1" lightbox="images/jamf-pro-static-group.png":::

3. قم بتوفير اسم عرض وحدد **حفظ**.

   :::image type="content" source="images/jamfpro-machine-group.png" alt-text="صفحة Jamf Pro2" lightbox="images/jamfpro-machine-group.png":::

4. سترى الآن مجموعة **أجهزة Contoso** ضمن **مجموعات الكمبيوتر الثابتة**.

   :::image type="content" source="images/contoso-machine-group.png" alt-text="صفحة Jamf Pro3" lightbox="images/contoso-machine-group.png":::

## <a name="next-step"></a>الخطوة التالية
- [إعداد Microsoft Defender لنقطة النهاية على سياسات macOS في Jamf Pro](mac-jamfpro-policies.md)
