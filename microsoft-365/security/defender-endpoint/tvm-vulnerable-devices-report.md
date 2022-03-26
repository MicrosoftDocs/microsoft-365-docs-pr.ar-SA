---
title: تقرير الأجهزة المعرضة - إدارة المخاطر والثغرات الأمنية
description: تقرير يعرض اتجاهات الأجهزة الضعيفة والإحصاءات الحالية. الهدف هو فهم نفس ونطاق التعرض لجهازك.
keywords: أجهزة Microsoft Defender ل Endpoint-tvm الضعيفة، Microsoft Defender ل Endpoint، tvm، تقليل المخاطر & التعرض للثغرات، تقليل المخاطر والثغرات، مراقبة تكوين الأمان
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
ms.openlocfilehash: 50b30d38a42aab37c295a9f65bd070dd9613927c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570450"
---
# <a name="vulnerable-devices-report---threat-and-vulnerability-management"></a>تقرير الأجهزة المعرضة - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

يعرض التقرير المخططات البيانية والمخططات الشريطية مع اتجاهات الأجهزة المعرضة للتأثر والإحصاءات الحالية. الهدف هو فهم نفس ونطاق التعرض لجهازك.

الوصول إلى التقرير في مدخل Microsoft 365 Defender من خلال الذهاب إلى التقارير > **الأجهزة المعرضة للخطر**

هناك عمودان:

- الاتجاهات (مع مرور الوقت). يمكن أن يظهر آخر 30 يوما أو 3 أشهر أو 6 أشهر أو نطاق تاريخ مخصص.
- الحالة (المعلومات الحالية)

**عامل** التصفية: يمكنك تصفية البيانات حسب مستويات خطورة الضعف أو استغلال التوفر أو عمر الضعف أو النظام الأساسي لنظام التشغيل أو Windows 10 أو Windows 11 أو مجموعة الأجهزة.

**التنقل لأسفل**: إذا كانت هناك معرفة متعمقة تريد استكشافها بشكل أكبر، فحدد المخطط الشريطي ذا الصلة لعرض قائمة تمت تصفيتها من الأجهزة في صفحة مخزون الجهاز. من هناك، يمكنك تصدير القائمة.

## <a name="severity-level-graphs"></a>الرسوم البيانية لمستوى الخطورة

يتم حساب كل جهاز مرة واحدة فقط وفقا لأخطر ثغرة أمنية يتم العثور عليها على هذا الجهاز.

:::image type="content" alt-text="رسم بياني واحد لمستويات خطورة الجهاز الحالي، ورسم بياني واحد يعرض المستويات مع مرور الوقت." source="images/tvm-report-severity.png" lightbox="images/tvm-report-severity.png":::

## <a name="exploit-availability-graphs"></a>استغلال الرسوم البيانية للتوفر

يتم حساب كل جهاز مرة واحدة فقط استنادا إلى أعلى مستوى من استغلال معروف.

:::image type="content" alt-text="رسم بياني واحد لتوفر الجهاز الحالي، ورسم بياني واحد يعرض التوفر مع مرور الوقت." source="images/tvm-report-exploit-availability.png" lightbox="images/tvm-report-exploit-availability.png":::

## <a name="vulnerability-age-graphs"></a>الرسوم البيانية لعمر الضعف

يتم حساب كل جهاز مرة واحدة فقط ضمن أقدم تاريخ منشور ثغرة أمنية. فنقاط الضعف القديمة لديها فرصة أكبر لتعرضها للاستغلال.

:::image type="content" alt-text="رسم بياني واحد لعمر ضعف الجهاز الحالي، ورسم بياني واحد يعرض العمر مع مرور الوقت." source="images/tvm-report-age.png" lightbox="images/tvm-report-age.png":::

## <a name="vulnerable-devices-by-operating-system-platform-graphs"></a>الأجهزة المعرضة من خلال تشغيل المخططات البيانية للنظام الأساسي لنظام التشغيل

عدد الأجهزة التي يتم عرضها على كل نظام تشغيل بسبب الثغرات في البرامج.

:::image type="content" alt-text="رسم بياني واحد للأجهزة الحالية المعرضة للخطر من خلال النظام الأساسي لنظام التشغيل، ورسم بياني واحد يعرض الأجهزة المعرضة للتأثر بواسطة أنظمة التشغيل الأساسية مع مرور الوقت." source="images/tvm-report-os.png" lightbox="images/tvm-report-os.png":::

## <a name="vulnerable-devices-by-windows-version-graphs"></a>الأجهزة المعرضة للخطر Windows الرسوم البيانية للإصدارات

عدد الأجهزة على كل إصدار Windows 10 أو Windows 11 يتم عرضها بسبب التطبيقات أو نظام التشغيل المعرضة.

:::image type="content" alt-text="رسم بياني واحد للأجهزة الحالية المعرضة Windows 10، ورسم بياني واحد يعرض الأجهزة المعرضة حسب Windows 10 مع مرور الوقت." source="images/tvm-report-version.png" lightbox="images/tvm-report-version.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [توصيات الأمان](tvm-security-recommendation.md)
