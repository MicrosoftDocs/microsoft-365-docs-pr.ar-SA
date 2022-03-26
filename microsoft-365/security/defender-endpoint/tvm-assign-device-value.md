---
title: تعيين قيمة الجهاز - إدارة المخاطر والثغرات الأمنية
description: تعرف على كيفية تعيين قيمة منخفضة أو عادية أو عالية لجهاز لمساعدتك على التمييز بين أولويات الأصول.
keywords: Microsoft Defender لقيمة جهاز نقطة النهاية، إدارة المخاطر والثغرات الأمنية جهاز، أجهزة ذات قيمة عالية، درجة التعرض لقيمة الجهاز
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
ms.openlocfilehash: cb8c0bd0870ea240e64c33dfac2fd6c00156def8
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573352"
---
# <a name="assign-device-value---threat-and-vulnerability-management"></a>تعيين قيمة الجهاز - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

يساعدك تحديد قيمة الجهاز على التمييز بين أولويات الأصول. يتم استخدام قيمة الجهاز لتضمين الرغبة في المخاطر لأصل فردي في حساب إدارة المخاطر والثغرات الأمنية التعرض للضوء. ستنال الأجهزة المعينة ك "قيمة عالية" مزيدا من الوزن.

يمكنك أيضا استخدام [API لقيمة الجهاز المحددة](set-device-value.md).

خيارات قيمة الجهاز:

- منخفض
- عادي (افتراضي)
- عال

أمثلة على الأجهزة التي يجب تعيين قيمة عالية لها:

- وحدات تحكم المجال، Active Directory
- الأجهزة التي تواجه الإنترنت
- أجهزة VIP
- الأجهزة التي تستضيف خدمات الإنتاج الداخلية/الخارجية

## <a name="choose-device-value"></a>اختيار قيمة الجهاز

1. انتقل إلى أي صفحة جهاز، والمكان الأسهل هو من مخزون الجهاز.

2. حدد **قيمة الجهاز** من ثلاث نقاط إلى جانب شريط الإجراءات في أعلى الصفحة.

    ![مثال لقيمة الجهاز المنسدلة.](images/tvm-device-value-dropdown.png)

3. ستظهر منتحلة من خلال قيمة الجهاز الحالية ومعناها. راجع قيمة الجهاز واختر الجهاز الأكثر ملائمة لجهازك.
![مثال لقيمة الجهاز من خلال flyout.](images/tvm-device-value-flyout.png)

## <a name="how-device-value-impacts-your-exposure-score"></a>كيفية تأثير قيمة الجهاز على درجة التعرض للضوء

إن درجة التعرض للضوء هي متوسط مرجح عبر جميع الأجهزة. إذا كان لديك مجموعات أجهزة، يمكنك أيضا تصفية الدرجة حسب مجموعة الأجهزة.

- الأجهزة العادية التي يكون وزنها 1
- الأجهزة ذات القيمة المنخفضة التي يكون وزنها 0,75
- الأجهزة ذات القيمة العالية لديها الوزن من NumberOfAssets / 10.
    - إذا كان لديك 100 جهاز، سيكون وزن كل جهاز عالي القيمة 10 (100/10)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [درجة التعرض للضوء](tvm-exposure-score.md)
- [واجهات برمجة التطبيقات](next-gen-threat-and-vuln-mgt.md#apis)