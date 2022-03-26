---
title: تقليل الثغرات في اليوم الصفري - إدارة المخاطر والثغرات الأمنية
description: تعرف على كيفية البحث عن نقاط الضعف في اليوم الصفري وكيفية تقليلها في بيئتك من خلال إدارة المخاطر والثغرات الأمنية.
keywords: نقاط الضعف في Microsoft Defender for Endpoint tvm صفر يوم، تلفاز، & إدارة الثغرات الأمنية، صفر يوم، 0 يوم، تقليل نقاط الضعف لمدة 0 أيام، CVE المعرضة للخطر
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
ms.openlocfilehash: f4a3e227dd43a812bea64e227e315d207eb6fc7b
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63571558"
---
# <a name="mitigate-zero-day-vulnerabilities---threat-and-vulnerability-management"></a>تقليل الثغرات في اليوم الصفري - إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

فهشاشة اليوم الصفري هي خطأ في البرامج التي لم يتم إصدار أي تصحيح رسمي أو تحديث أمان لها. قد يكون مورد البرنامج على علم بالثغرة الأمنية أو قد لا يكون على علم بها، ولا تتوفر أي معلومات عامة حول هذا الخطر. غالبا ما تكون نقاط الضعف في اليوم الصفري ذات مستويات عالية الخطورة، كما يتم استغلالها بنشاط.

لن يعرض إدارة الثغرات الأمنية المخاطر والثغرات الأمنية إلا نقاط الضعف في اليوم الصفري التي لديها معلومات حولها.

## <a name="find-information-about-zero-day-vulnerabilities"></a>البحث عن معلومات حول نقاط الضعف في اليوم الصفري

بمجرد العثور على ثغرة في اليوم الصفري، سيتم نقل معلومات حولها من خلال التجارب التالية في Microsoft 365 Defender المدخل.

> [!NOTE]
> تتوفر حاليا إمكانية ثغرة أمنية لمدة 0 أيام فقط Windows المنتجات.

### <a name="threat-and-vulnerability-management-dashboard"></a>لوحة معلومات إدارة الثغرات الأمنية المخاطر

ابحث عن التوصيات باستخدام علامة صفر يوم في بطاقة "أهم توصيات الأمان".

![أهم التوصيات باستخدام علامة يوم صفري.](images/tvm-zero-day-top-security-recommendations.png)

ابحث عن أفضل البرامج باستخدام علامة اليوم الصفري في بطاقة "البرامج الأكثر عرضة للتأثر".

![البرامج الأكثر عرضة للتأثر بعلامة يوم صفري.](images/tvm-zero-day-top-software.png)

### <a name="weaknesses-page"></a>صفحة نقاط الضعف

ابحث عن ثغرة اليوم الصفرية المسماة مع وصف وتفاصيل.

- إذا تم تعيين بطاقة CVE-ID لهذه الثغرة الأمنية، سترى تسمية اليوم الصفري بجانب اسم CVE.

- إذا لم يتم تعيين CVE-ID لهذه الثغرة الأمنية، فتعثر عليها تحت اسم داخلي مؤقت يبدو مثل "TVM-XXXX-XXXX". سيتم تحديث الاسم بعد تعيين CVE-ID رسمي، ولكن سيبقى الاسم الداخلي السابق قابلا للبحث في اللوحة الجانبية.

:::image type="content" alt-text="مثال ليوم صفري لصفحة CVE-2020-17087 في نقاط الضعف." source="images/tvm-zero-day-weakness-name.png" lightbox="images/tvm-zero-day-weakness-name.png":::

### <a name="software-inventory-page"></a>صفحة مخزون البرامج

ابحث عن برنامج باستخدام علامة اليوم الصفري. يمكنك التصفية حسب علامة "اليوم الصفري" لرؤية البرامج ذات الثغرات في اليوم الصفري فقط.

:::image type="content" alt-text="مثال ليوم صفري Windows Server 2016 في صفحة مخزون البرامج." source="images/tvm-zero-day-software-inventory.png" lightbox="images/tvm-zero-day-software-inventory.png":::

### <a name="software-page"></a>صفحة البرامج

ابحث عن علامة اليوم الصفري لكل برنامج تأثر بضعف اليوم الصفري.

:::image type="content" alt-text="مثال ليوم صفري لصفحة Windows Server 2016." source="images/tvm-zero-day-software-page.png" lightbox="images/tvm-zero-day-software-page.png":::

### <a name="security-recommendations-page"></a>صفحة توصيات الأمان

عرض اقتراحات واضحة حول خيارات الإصلاح وتخفيف المخاطر، بما في ذلك الحلول البديله في حال وجودها. يمكنك التصفية حسب علامة "اليوم الصفري" لرؤية توصيات الأمان التي تعالج الثغرات في اليوم الصفري فقط.

إذا كان هناك برنامج به ثغرة أمنية في اليوم الصفري ونقاط ضعف إضافية يجب معالجتها، فسوف تحصل على توصية واحدة حول جميع نقاط الضعف.

:::image type="content" alt-text="مثال ليوم صفري Windows Server 2016 في صفحة توصيات الأمان." source="images/tvm-zero-day-security-recommendation.png" lightbox="images/tvm-zero-day-security-recommendation.png":::

## <a name="addressing-zero-day-vulnerabilities"></a>معالجة الثغرات في اليوم الصفري

انتقل إلى صفحة توصيات الأمان وحدد توصية ذات يوم صفري. سيتم فتح مجموعة من المعلومات مع معلومات حول اليوم الصفري ونقاط الضعف الأخرى لهذا البرنامج.

سيكون هناك ارتباط إلى خيارات التخفيف و الحلول البديله إذا كانت متوفرة. قد تساعد الحلول البديله على تقليل المخاطر التي تشكلها ثغرة اليوم الصفري هذه حتى يمكن نشر تصحيح أو تحديث أمان.

افتح خيارات المعالجة واختر نوع الانتباه. يوصى باستخدام خيار المعالجة "مطلوب الانتباه" لنقاط الضعف في اليوم الصفري، نظرا لأنه لم يتم إصدار تحديث بعد. لن تتمكن من تحديد تاريخ الاستحقاق، نظرا لأنه لا يوجد أي إجراء محدد لتنفيذه. إذا كانت هناك نقاط ضعف قديمة لهذا البرنامج الذي تريد إصلاحه، يمكنك تجاوز خيار المعالجة "مطلوب الانتباه" واختيار "تحديث".

![مثال حول منار اليوم Windows Server 2016 في صفحة توصيات الأمان.](images/tvm-zero-day-recommendation-flyout400.png)

## <a name="track-zero-day-remediation-activities"></a>تعقب أنشطة المعالجة لمدة صفرية

انتقل إلى صفحة [إدارة المخاطر والثغرات الأمنية المعالجة لعرض](tvm-remediation.md) عنصر نشاط المعالجة. إذا اخترت خيار المعالجة "مطلوب الانتباه"، لن يكون هناك شريط تقدم أو حالة تذكرة أو تاريخ الاستحقاق نظرا لأنه لا يوجد أي إجراء فعلي يمكننا مراقبته. يمكنك التصفية حسب نوع المعالجة، مثل "تحديث البرنامج" أو "الانتباه المطلوب"، لرؤية كل عناصر النشاط في الفئة نفسها.

## <a name="patching-zero-day-vulnerabilities"></a>تصحيح الثغرات في اليوم الصفري

عند إصدار تصحيح لليوم الصفري، سيتم تغيير التوصية إلى "تحديث" وتسمية زرقاء بجانبه تقول "تحديث أمان جديد لليوم الصفري". لن يتم اعتبارها يوما صفريا، وستزال علامة اليوم الصفري من كل الصفحات.

![توصية ل "تحديث Microsoft Windows 10" باستخدام تسمية تصحيح جديدة.](images/tvm-zero-day-patch.jpg)

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [لوحة المعلومات](tvm-dashboard-insights.md)
- [توصيات الأمان](tvm-security-recommendation.md)
- [مخزون البرامج](tvm-software-inventory.md)
- [نقاط الضعف في المؤسسة](tvm-weaknesses.md)
