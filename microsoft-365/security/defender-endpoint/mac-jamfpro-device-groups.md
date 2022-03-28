---
title: إعداد مجموعات الأجهزة في Jamf Pro
description: تعرف على كيفية إعداد مجموعات الأجهزة في Jamf Pro ل Microsoft Defender ل Endpoint على macOS
keywords: الجهاز، المجموعة، microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamfpro، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: 3b9d6255320b5d702768614059bb9edff28be3b3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63575745"
---
# <a name="set-up-microsoft-defender-for-endpoint-on-macos-device-groups-in-jamf-pro"></a>إعداد Microsoft Defender ل Endpoint على مجموعات أجهزة macOS في Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

قم بإعداد مجموعات الأجهزة بطريقة مماثلة لمجموعات تنظيم نهج المجموعة Microsoft Endpoint Configuration Manager مجموعات الأجهزة ومجموعات أجهزة Intune.

1. انتقل إلى **مجموعات الكمبيوتر الثابتة**.

2. حدد **جديد**. 

    ![صورة Jamf Pro1.](images/jamf-pro-static-group.png)

3. قم بتوفير اسم عرض وحدد **حفظ**.

    ![صورة Jamf Pro2.](images/jamfpro-machine-group.png)

4. سترى الآن مجموعة **أجهزة Contoso** ضمن **مجموعات الكمبيوتر الثابتة**.

    ![صورة Jamf Pro3.](images/contoso-machine-group.png)

## <a name="next-step"></a>الخطوة التالية
- [إعداد Microsoft Defender ل Endpoint على سياسات macOS في Jamf Pro](mac-jamfpro-policies.md)
