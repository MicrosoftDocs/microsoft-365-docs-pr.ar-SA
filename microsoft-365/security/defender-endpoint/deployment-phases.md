---
title: نظرة عامة على نشر Microsoft Defender لنقطة النهاية
description: تعرف على كيفية نشر Microsoft Defender لنقطة النهاية عن طريق إعداد نقاط النهاية وإعدادها وإلحاقها بتلك الخدمة
keywords: النشر، والإعداد، والإعداد، والإلحاق، والمرحلة، والنشر، والنشر، والاعتماد، والتكوين
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-overview
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3520d249e7241eb1b890c3939fe6e6165d5c6011
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607598"
---
# <a name="microsoft-defender-for-endpoint-deployment-overview"></a>نظرة عامة على نشر Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تعرف على كيفية نشر Microsoft Defender لنقطة النهاية بحيث يمكن لمؤسستك الاستفادة من الحماية الوقائية والكشف عن ما بعد الاختراق والتحقيق التلقائي والاستجابة.

يساعدك هذا الدليل على العمل عبر المساهمين لإعداد البيئة الخاصة بك ثم إلحاق الأجهزة بطريقة منهجية، والانتقال من التقييم، إلى إصدار تجريبي ذي مغزى، إلى النشر الكامل.

يتوافق كل قسم مع مقالة منفصلة في هذا الحل.

:::image type="content" source="images/deployment-guide-phases.png" alt-text="مراحل النشر مع تفاصيل من الجدول" lightbox="images/deployment-guide-phases.png":::


:::image type="content" source="images/phase-diagrams/deployment-phases.png" alt-text="ملخص مراحل النشر: الإعداد والإعداد والإلحاق" lightbox="images/phase-diagrams/deployment-phases.png":::

<br>

****

|المرحله|الوصف|
|---|---|
|[المرحلة 1: التحضير](prepare-deployment.md)|تعرف على ما تحتاج إلى مراعاته عند نشر Defender لنقطة النهاية مثل موافقات المساهمين واعتبارات البيئة وأذونات الوصول وترتيب اعتماد القدرات.|
|[المرحلة 2: الإعداد](production-deployment.md)|احصل على إرشادات حول الخطوات الأولية التي تحتاج إلى اتخاذها بحيث يمكنك الوصول إلى المدخل مثل التحقق من صحة الترخيص وإكمال معالج الإعداد وتكوين الشبكة.|
|[المرحلة 3: التجهيز للاستخدام](onboarding.md)|تعرف على كيفية الاستفادة من حلقات النشر وأدوات الإلحاق المدعومة استنادا إلى نوع نقطة النهاية وتكوين القدرات المتوفرة.|
|

بعد الانتهاء من هذا الدليل، سيتم إعدادك باستخدام أذونات الوصول الصحيحة، وسيتم إلحاق نقاط النهاية الخاصة بك وإعداد تقارير عن بيانات أداة الاستشعار إلى الخدمة، وسيتم تطبيق قدرات مثل حماية الجيل التالي وتقليل الأجزاء المعرضة للهجوم.

بغض النظر عن بنية البيئة وطريقة النشر التي تختارها الموضحة في إرشادات [نشر الخطة](deployment-strategy.md) ، فإن هذا الدليل سيدعمك في إعداد نقاط النهاية.

## <a name="key-capabilities"></a>القدرات الرئيسية

في حين أن Microsoft Defender لنقطة النهاية يوفر العديد من القدرات، فإن الغرض الأساسي من دليل النشر هذا هو الحصول على البدء عن طريق إلحاق الأجهزة. بالإضافة إلى الإلحاق، تساعدك هذه الإرشادات على بدء استخدام الإمكانات التالية.

<br>

****

|القدره|الوصف|
|---|---|
|الكشف عن نقطة النهاية والاستجابة لها|يتم وضع قدرات الكشف عن نقطة النهاية والاستجابة للكشف عن محاولات الاختراق والاختراقات النشطة والتحقيق فيها والاستجابة لها.|
|حماية الجيل التالي|لزيادة تعزيز محيط الأمان لشبكتك، تستخدم Microsoft Defender لنقطة النهاية حماية الجيل التالي المصممة لالتقاط جميع أنواع التهديدات الناشئة.|
|قواعد تقليل الأجزاء المعرضة للهجوم|توفير خط الدفاع الأول في المكدس. من خلال ضمان تعيين إعدادات التكوين بشكل صحيح وتطبيق تقنيات التخفيف من الاستغلال، تقاوم هذه القدرات الهجمات واستغلالها.|
|

تتوفر جميع هذه الإمكانات لحاملي التراخيص Microsoft Defender لنقطة النهاية. لمزيد من المعلومات، راجع [متطلبات الترخيص](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>نطاق

### <a name="in-scope"></a>في النطاق

- استخدام Microsoft إدارة نقاط النهاية ونقطة نهاية Microsoft Configuration Manager إلى نقاط النهاية المضمنة في الخدمة وتكوين القدرات
- تمكين قدرات Defender لنقطة النهاية للكشف عن نقاط النهاية والاستجابة لها (EDR)
- تمكين قدرات النظام الأساسي لحماية نقطة النهاية Defender لنقطة النهاية (EPP)
  - حماية الجيل التالي
  - قواعد تقليل الأجزاء المعرضة للهجوم

### <a name="out-of-scope"></a>خارج النطاق

فيما يلي خارج نطاق دليل النشر هذا:

- تكوين حلول الجهات الخارجية التي قد تتكامل مع Defender لنقطة النهاية
- اختبار الاختراق في بيئة الإنتاج

## <a name="see-also"></a>راجع أيضًا

- [المرحلة 1: التحضير](prepare-deployment.md)
- [المرحلة 2: إعداد](production-deployment.md)
- [المرحلة 3: التجهيز للاستخدام](onboarding.md)
- [تخطيط النشر](deployment-strategy.md)
