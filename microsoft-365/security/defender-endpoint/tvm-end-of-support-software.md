---
title: التخطيط لنهاية الدعم والإصدارات البرمجية
description: اكتشف إصدارات البرامج والبرامج التي لم تعد معتمدة ولن تتلقى تحديثات الأمان وخطط لها.
keywords: إدارة المخاطر والثغرات الأمنية Microsoft Defender لنقطة النهاية أمان tvm وتوصية أمان الإنترنت والتوصيات المتعلقة بالأمان القابل للتنفيذ
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3997e2cb372a2cbbbdb0d8e9b51c5b57bd38c7aa
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476676"
---
# <a name="plan-for-end-of-support-software-and-software-versions-with-threat-and-vulnerability-management"></a>التخطيط لإصدارات برامج نهاية الدعم والبرامج باستخدام إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

يعني انتهاء الدعم (EOS)، المعروف ب انتهاء العمر العمري (EOL)، للبرامج أو إصدارات البرامج أنه لن يتم دعمها أو خدمتها، ولن تتلقى تحديثات الأمان. عندما تستخدم إصدارات برامج أو برامج ذات دعم منته، تعرض مؤسستك لنقاط الضعف الأمنية والمخاطر القانونية المالية.

من الضروري أن يعمل مسؤولي الأمان وإدارة تكنولوجيا المعلومات معا لضمان تكوين مخزون البرامج في المؤسسة للحصول على أفضل النتائج والتوافق والنظام البيئي لشبكة سليمة. يجب عليهم فحص الخيارات لإزالة التطبيقات التي وصلت إلى نهاية الدعم وتحديث الإصدارات التي لم تعد معتمدة أو استبدالها. من الأفضل إنشاء خطة وتنفيذها قبل انتهاء تواريخ الدعم.

> [!NOTE]
> تتوفر إمكانية انتهاء الدعم حاليا لمنتجات Windows فقط.

## <a name="find-software-or-software-versions-that-are-no-longer-supported"></a>البحث عن إصدارات البرامج أو البرامج التي لم تعد معتمدة

1. من القائمة إدارة المخاطر والثغرات الأمنية، انتقل إلى [**توصيات الأمان**](tvm-security-recommendation.md).
2. انتقل إلى **لوحة عوامل التصفية** وابحث عن مقطع العلامات. حدد واحدا أو أكثر من خيارات علامة EOS. ثم **تطبيق**.

   :::image type="content" source="images/tvm-eos-tag.png" alt-text="برامج EOS، إصدارات EOS، إصدارات EOS القادمة" lightbox="images/tvm-eos-tag.png":::

3. سترى قائمة بالتوصيات ذات الصلة بالبرمجيات التي تم إنهاء دعمها أو إصدارات البرامج التي تنتهي الدعم أو الإصدارات ذات نهاية الدعم القادمة. كما تظهر هذه العلامات في [صفحة مخزون](tvm-software-inventory.md) البرامج.

   :::image type="content" source="images/tvm-eos-tags-column.png" alt-text="علامة التوصيات EOS" lightbox="images/tvm-eos-tags-column.png":::

## <a name="list-of-versions-and-dates"></a>قائمة بالإصدارات والتواريخ

لعرض قائمة بالإصدارات التي وصلت إلى نهاية الدعم أو الانتهاء أو الدعم قريبا، وتلك التواريخ، اتبع الخطوات التالية:

1. ستظهر رسالة في النشرة من خلال توصيات الأمان للبرامج ذات الإصدارات التي وصلت إلى نهاية الدعم، أو ستصل إلى نهاية الدعم قريبا.

   :::image type="content" source="images/eos-upcoming-eos.png" alt-text="ارتباط توزيع الإصدار" lightbox="images/eos-upcoming-eos.png":::

2. حدد ارتباط **توزيع الإصدار** الذي تريد الانتقال إليه في صفحة التنقل لأسفل للبرنامج. هناك، يمكنك رؤية قائمة بالإصدارات التي تمت تصفيتها باستخدام علامات تحددها على أنها نهاية الدعم أو نهاية الدعم القادمة.

   :::image type="content" source="images/software-drilldown-eos.png" alt-text="صفحة التنقل لأسفل للبرنامج مع تفاصيل نهاية برنامج الدعم" lightbox="images/software-drilldown-eos.png":::

3. حدد أحد الإصدارات في الجدول لفتحه. على سبيل المثال، الإصدار 10.0.18362.1. ستظهر منتحلة من خلال نهاية تاريخ الدعم.

   :::image type="content" source="images/version-eos-date.png" alt-text="عرض تاريخ انتهاء الدعم" lightbox="images/version-eos-date.png":::

بمجرد تحديد إصدارات البرامج والبرامج المعرضة للخطر بسبب حالة انتهاء الدعم الخاصة بها، يجب أن تقرر ما إذا كنت تريد تحديثها أو إزالتها من مؤسستك. يؤدي القيام بذلك إلى تقليل تعرض مؤسستك لنقاط الضعف والتهديدات المستمرة المتقدمة.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [توصيات الأمان](tvm-security-recommendation.md)
- [مخزون البرامج](tvm-software-inventory.md)
