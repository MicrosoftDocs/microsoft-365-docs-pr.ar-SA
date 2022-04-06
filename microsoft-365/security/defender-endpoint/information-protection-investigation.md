---
title: استخدام تسميات الحساسية لتحديد أولوية الاستجابة للحوادث
description: تعرف على كيفية استخدام تسميات الحساسية لتحديد أولويات الأحداث التحقيق فيها
keywords: المعلومات والحماية والبيانات والفقدان والمنع والملصقات و dlp والحادثة والتحري والتحري
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
ms.technology: mde
ms.openlocfilehash: 465c149e3ad82384b574b43c66da917a46e4a2ce
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474146"
---
# <a name="use-sensitivity-labels-to-prioritize-incident-response"></a>استخدام تسميات الحساسية لتحديد أولوية الاستجابة للحوادث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تشتمل دورة حياة المخاطر الثابتة المتقدمة النموذجية على عملية تهوية البيانات. في حادث الأمان، من المهم أن تكون لديك القدرة على تحديد أولويات التحقيق حيث قد تكون الملفات الحساسة معرضة للخطر بحيث تكون بيانات الشركة ومعلوماتها محمية.

يساعد Defender for Endpoint على جعل تحديد أولويات أحداث الأمان أكثر بساطة باستخدام تسميات الحساسية. تحدد تسميات الحساسية بسرعة الحوادث التي قد تتضمن أجهزة ذات معلومات حساسة مثل المعلومات السرية.

## <a name="investigate-incidents-that-involve-sensitive-data"></a>التحقق من الأحداث التي تتضمن بيانات حساسة

تعرف على كيفية استخدام تسميات حساسية البيانات لتحديد أولوية التحقيق في الأحداث.

> [!NOTE]
> يتم الكشف عن التسميات الإصدار 1809 من Windows 10 أو أي وقت لاحق، Windows 11.

1. في Microsoft 365 Defender، حدد أحداث & **تنبيهات** \> **التنبيهات**.

2. قم بالتمرير إلى اليمين لرؤية العمود **حساسية** البيانات. يعكس هذا العمود تسميات الحساسية التي تم ملاحظتها على الأجهزة ذات الصلة بالحوادث مما يوفر إشارة إلى ما إذا كانت الملفات الحساسة قد تكون متأثِّره بالحادث.

   :::image type="content" source="images/data-sensitivity-column.png" alt-text="الخيار &quot;سري للغاية&quot; في عمود حساسية البيانات" lightbox="images/data-sensitivity-column.png":::

    يمكنك أيضا التصفية استنادا إلى **حساسية البيانات**

    :::image type="content" source="images/data-sensitivity-filter.png" alt-text="عامل تصفية حساسية البيانات" lightbox="images/data-sensitivity-filter.png":::

3. افتح صفحة الحادث لمزيد من التحقيق.

   :::image type="content" source="images/incident-page.png" alt-text="تفاصيل صفحة الحادث" lightbox="images/incident-page.png":::

4. حدد علامة **التبويب** الأجهزة لتحديد الأجهزة التي تخزن الملفات مع تسميات الحساسية.

   :::image type="content" source="images/investigate-devices-tab.png" alt-text="علامة التبويب &quot;جهاز&quot;" lightbox="images/investigate-devices-tab.png":::

5. حدد الأجهزة التي تخزن البيانات الحساسة وابحث عبر المخطط الزمني لتحديد الملفات التي قد تؤثر عليها، ثم اتخاذ الإجراء المناسب لضمان حماية البيانات.

   يمكنك تضييق نطاق الأحداث المعروضة على المخطط الزمني للجهاز من خلال البحث عن تسميات حساسية البيانات. سيعرض القيام بذلك الأحداث المقترنة بالملفات التي لها اسم التسمية فقط.

   :::image type="content" source="images/machine-timeline-labels.png" alt-text="المخطط الزمني للجهاز مع نتائج بحث ضيقة استنادا إلى التسمية" lightbox="images/machine-timeline-labels.png":::

> [!TIP]
> يتم أيضا عرض نقاط البيانات هذه من خلال 'DeviceFileEvents' في عملية البحث المتقدم، مما يسمح للاستعلامات المتقدمة وجداول الاكتشاف بأخذ تسميات الحساسية ووضع حماية الملفات في الاعتبار.
