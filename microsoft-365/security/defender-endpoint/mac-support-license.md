---
title: استكشاف مشاكل الترخيص وإصلاحها Microsoft Defender لنقطة النهاية على Mac
description: استكشاف مشاكل الترخيص وإصلاحها في Microsoft Defender لنقطة النهاية Mac.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، أداء
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
ms.openlocfilehash: 35b77183ee9ceb00569c956d30debb0dd61e63f7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471704"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشاكل ترخيص Microsoft Defender لنقطة النهاية على macOS وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
 [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

أثناء المرور عبر Microsoft Defender لنقطة النهاية على [macOS](microsoft-defender-endpoint-mac.md) واختبار [النشر اليدوي أو](mac-install-manually.md) إثبات المبدأ (PoC)، قد تحصل على الخطأ التالي:

:::image type="content" source="images/no-license-found.png" alt-text="خطأ في الترخيص" lightbox="images/no-license-found.png":::

**الرسالة:** 

لم يتم العثور على أي ترخيص

يبدو أن مؤسستك لا تملك ترخيصا Microsoft 365 Enterprise الاشتراك.

اتصل بالمسؤول للحصول على المساعدة.

**السبب:** 

قمت بنشر و/أو تثبيت Microsoft Defender لنقطة النهاية على حزمة macOS ("تنزيل حزمة التثبيت")، ولكن ربما لم تكن قد قمت بتشغيل برنامج التكوين النصي ("تنزيل حزمة التهيئة")، أو لم يتم تعيين ترخيص للمستخدم.

يمكنك أيضا مواجهة هذا الخطأ عندما لا Microsoft Defender لنقطة النهاية على وكيل macOS. 


**الحل:**

اتبع الإرشادات MicrosoftDefenderATPOnboardingMacOs.py الموثقة هنا: [تكوين العميل](mac-install-manually.md#client-configuration)

بالنسبة إلى السيناريوهات التي Microsoft Defender لنقطة النهاية تحديث على macOS، ستحتاج إلى تحديث الوكيل. 
