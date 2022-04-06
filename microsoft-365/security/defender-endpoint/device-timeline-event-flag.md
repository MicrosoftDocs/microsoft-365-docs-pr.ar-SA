---
title: Microsoft Defender لنقطة النهاية أحداث المخطط الزمني للجهاز
description: استخدام Microsoft Defender لنقطة النهاية أحداث المخطط الزمني للجهاز
keywords: Defender for Endpoint device timeline, event flags
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
ms.technology: mde
ms.openlocfilehash: 44292893249872c1c4b8dc3b4f66d10085fb0a2b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471176"
---
# <a name="microsoft-defender-for-endpoint-device-timeline-event-flags"></a>Microsoft Defender لنقطة النهاية أحداث المخطط الزمني للجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تساعدك علامة الحدث في المخطط الزمني لجهاز Defender for Endpoint على تصفية أحداث معينة وتنظيمها عندما تحقق من الهجمات المحتملة.

يوفر المخطط الزمني لجهاز Defender for Endpoint طريقة عرض ذات ترتيب زمني للأحداث والتنبيهات المقترنة التي تم ملاحظتها على جهاز. توفر قائمة الأحداث هذه إمكانية الرؤية الكاملة لأي أحداث وملفات وعناوين IP يتم ملاحظتها على الجهاز. قد تكون القائمة طويلة في بعض الأحيان. تساعدك علامة أحداث المخطط الزمني للجهاز على تعقب الأحداث التي قد تكون ذات صلة.

بعد مرورك على مخطط زمني للجهاز، يمكنك فرز الأحداث المحددة التي قمت بتصفيتها وتصديرها التي تم وضع علامة عليها.

أثناء التنقل في المخطط الزمني للجهاز، يمكنك البحث عن أحداث معينة وتصفيتها. يمكنك تعيين علامة الحدث حسب:

- تمييز الأحداث الأكثر أهمية
- وضع علامة على الأحداث التي تتطلب تعمقا
- إنشاء مخطط زمني واضح للخرق

## <a name="flag-an-event"></a>وضع علامة على حدث

1. البحث عن الحدث الذي تريد وضع علامة عليه

2. انقر فوق أيقونة العلامة في العمود وضع علامة. 

:::image type="content" source="images/device-flags.png" alt-text="علامة المخطط الزمني للجهاز" lightbox="images/device-flags.png":::

## <a name="view-flagged-events"></a>عرض الأحداث التي تم وضع علامة عليها

1. في المقطع عوامل **تصفية المخطط الزمني** ، يمكنك تمكين الأحداث **التي تم وضع علامة عليها**.
2. انقر فوق **تطبيق**. يتم عرض الأحداث التي تم وضع علامة عليها فقط.

يمكنك تطبيق عوامل تصفية إضافية بالنقر فوق شريط الوقت. لن يظهر هذا سوى الأحداث قبل الحدث الذي تم وضع علامة عليه.  

:::image type="content" source="images/device-flag-filter.png" alt-text="علامة المخطط الزمني للجهاز مع تشغيل عامل التصفية" lightbox="images/device-flag-filter.png":::