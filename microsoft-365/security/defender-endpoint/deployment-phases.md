---
title: مراحل النشر
description: تعرف على كيفية نشر Microsoft Defender لنقطة النهاية من خلال إعداد نقاط نهاية هذه الخدمة وإعدادها وضبطها
keywords: النشر، والتحضير، والإعداد، واللوح، والطور، والنشر، والنشر، والتكوين
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
ms.openlocfilehash: 5715a796e0c7b78ae369f074b5edcb6ccfc8ae90
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63573376"
---
# <a name="deployment-phases"></a>مراحل النشر

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تعرف على كيفية نشر Microsoft Defender لنقطة النهاية بحيث يمكن لمؤسستك الاستفادة من الحماية الوقائية، والكشف بعد الخرق، والتحري التلقائي، والاستجابة.

يساعدك هذا الدليل على العمل عبر المساهمين لإعداد بيئتك، ثم على الأجهزة المجهزة بطريقة منهجية، والانتقال من التقييم إلى التجربة ذات المغزى، إلى النشر الكامل.

يتوافق كل مقطع مع مقالة منفصلة في هذا الحل.

![صورة لمراحل النشر مع تفاصيل من جدول.](images/deployment-guide-phases.png)


![ملخص مراحل النشر: الإعداد والإعداد واللوح.](images/phase-diagrams/deployment-phases.png)

<br>

****

|المرحلة|الوصف|
|---|---|
|[المرحلة 1: التحضير](prepare-deployment.md)|تعرف على ما تحتاج إلى وضعه في الاعتبار عند نشر Defender لنقطة النهاية مثل موافقات المساهمين، اعتبارات البيئة، أذونات الوصول، واعتماد ترتيب القدرات.|
|[المرحلة الثانية: الإعداد](production-deployment.md)|احصل على إرشادات حول الخطوات الأولية التي تحتاج إلى اتخاذها حتى تتمكن من الوصول إلى المدخل مثل التحقق من صحة الترخيص وإكمال معالج الإعداد وتكوين الشبكة.|
|[المرحلة 3: Onboard](onboarding.md)|تعرف على كيفية الاستفادة من حلقات النشر وأدوات التهيئة المعتمدة استنادا إلى نوع نقطة النهاية وتكوين الإمكانات المتوفرة.|
|

بعد إكمال هذا الدليل، سيتم إعدادك باستخدام أذونات الوصول الصحيحة، سيتم اكمال نقاط النهاية وإعداد بيانات المستشعر للخدمة، وإمكانيات مثل حماية الجيل التالي والحد من سطح الهجوم.

بغض النظر عن بنية البيئة وطريقة النشر التي تختارها موضحة في إرشادات نشر [](deployment-strategy.md) الخطة، سيدعمك هذا الدليل في نقاط نهاية التهيئة.

## <a name="key-capabilities"></a>الإمكانات الأساسية

على الرغم من أن Microsoft Defender ل Endpoint يوفر العديد من الإمكانات، فإن الغرض الأساسي من دليل النشر هذا هو بدء استخدام أجهزة الالتحاق. بالإضافة إلى الالإضافة، فإن هذه الإرشادات ستطلق عليك الإمكانات التالية.

<br>

****

|الإمكانية|الوصف|
|---|---|
|الكشف عن نقطة النهاية والاستجابة لها|يتم وضع قدرات الكشف عن نقاط النهاية والاستجابة للكشف عن محاولات التسلل والانتهاكات النشطة والكشف عنها والاستجابة لها.|
|حماية الجيل التالي|لمزيد من تعزيز محيط الأمان للشبكة، يستخدم Microsoft Defender ل Endpoint حماية الجيل التالي المصممة لالتقاط جميع أنواع التهديدات الناشئة.|
|الحد من سطح الهجوم|توفير خط الدفاع الأول في المكدس. ومن خلال ضمان تعيين إعدادات التكوين بشكل صحيح وتطبيق أساليب التخفيف من المخاطر، تقاوم هذه الإمكانات الهجمات واستغلالها.|
|

تتوفر كل هذه الإمكانات لحاملي تراخيص نقطة النهاية من Microsoft Defender. لمزيد من المعلومات، راجع [متطلبات الترخيص](minimum-requirements.md#licensing-requirements).

## <a name="scope"></a>النطاق

### <a name="in-scope"></a>في النطاق

- استخدام إدارة نقاط النهاية من Microsoft Microsoft Endpoint Configuration Manager لتهيئة نقاط النهاية في الخدمة وتكوين القدرات
- تمكين قدرات Defender لنقطة النهاية الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية)
- تمكين قدرات النظام الأساسي لحماية نقطة نهاية نقطة النهاية (EPP) ل Defender
  - حماية الجيل التالي
  - الحد من سطح الهجوم

### <a name="out-of-scope"></a>خارج النطاق

ما يلي خارج نطاق دليل النشر هذا:

- تكوين حلول  الأطراف الخارجية التي قد تتكامل مع Defender for Endpoint
- اختبار الاختراق في بيئة الإنتاج

## <a name="see-also"></a>راجع أيضًا

- [المرحلة 1: التحضير](prepare-deployment.md)
- [المرحلة الثانية: إعداد](production-deployment.md)
- [المرحلة 3: Onboard](onboarding.md)
- [تخطيط النشر](deployment-strategy.md)
