---
title: تعقب سجل Microsoft Secure Score و تحقيق الأهداف
description: احصل على معلومات متعمقة حول النشاط الذي يؤثر على "نقاط Microsoft الآمنة". اكتشف الاتجاهات وحدد الأهداف.
keywords: نقاط آمنة من microsoft، نقاط آمنة، نقاط آمنة في Office 365، نقاط أمان microsoft، Microsoft 365 Defender مدخل، إجراءات التحسين
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: d740ab4fb999697edc9ce7c8f662f6d5c6681fdf
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500486"
---
# <a name="track-your-microsoft-secure-score-history-and-meet-goals"></a>تعقب سجل Microsoft Secure Score و تحقيق الأهداف

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[Microsoft Secure Score](microsoft-secure-score.md) هو قياس لوضعية الأمان في المؤسسة، مع رقم أعلى يشير إلى المزيد من إجراءات التحسين التي تم اتخاذها. يمكن العثور عليه في https://security.microsoft.com/securescore مدخل Microsoft 365 Defender[.](microsoft-365-defender.md#the-microsoft-365-defender-portal)

## <a name="gain-insights-into-activity-that-has-affected-your-score"></a>الحصول على معلومات متعمقة حول النشاط الذي يؤثر على نقاطك

عرض رسم بياني لسجلات مؤسستك مع مرور الوقت في علامة **التبويب** محفوظات.

يوجد أسفل الرسم البياني قائمة بكل الإجراءات التي تم اتخاذها في النطاق الزمني المحدد وسماتها، مثل النقاط والفئة الناتجة. يمكنك تخصيص نطاق تاريخ وتصفية حسب الفئة.

:::image type="content" source="../../media/secure-score/secure-score-history-activity.png" alt-text="مثال على الصفحة التي تصف محفوظات النشاط في مدخل Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-history-activity.png":::

إذا قمت بتحديد إجراء التحسين المقترن بنشاط ما، ستظهر القائمة من القائمة المن القائمة من القائمة flyout الكاملة للتحسين.

لعرض كل المحفوظات الخاصة ب إجراء التحسين المحدد هذا، حدد ارتباط المحفوظات في flyout.

:::image type="content" source="../../media/secure-score/secure-score-history-flyout.png" alt-text="جزء المحفوظات المتعلق بعمل التحسين في مدخل Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-history-flyout.png":::

## <a name="discover-trends-and-set-goals"></a>اكتشاف الاتجاهات وحدد الأهداف

في علامة **التبويب المقاييس &** الاتجاهات، هناك العديد من الرسوم البيانية والمخططات لتمنحك رؤية أكثر في الاتجاهات والأهداف المحددة. يمكنك تعيين نطاق التاريخ للصفحة الكاملة للمرئيات. تتضمن المرئيات:

* **منطقة "نقاط آمنة** " الخاصة بك - مخصصة استنادا إلى أهداف المؤسسة وتعريفات نطاقات النقاط الجيدة، أو الجيدة، أو غير الصالحة.
* **اتجاه الانحدار** - مخطط زمني للنقاط التي تم انحدارها بسبب تغييرات التكوين أو المستخدم أو الجهاز.  
* **اتجاه المقارنة** - كيفية مقارنة "نقاط آمنة" في مؤسستك مع الآخرين مع مرور الوقت. يمكن أن تتضمن طريقة العرض هذه خطوطا تمثل متوسط نقاط المؤسسات ذات عدد مقاعد مماثل وعرض مقارنة مخصص يمكنك تعيينه.
* **اتجاه قبول المخاطر** - مخطط زمني لتنفيذ إجراءات التحسين تم وضع علامة عليه على أنه "تم قبول المخاطر".
* **تغييرات الدرجات** - عدد النقاط التي تم تحقيقها والنقاط التي تم تراجعها والتغييرات التي تم إدخالها على نقاطك في نطاق التاريخ المحدد.

### <a name="compare-your-score-to-organizations-like-yours"></a>مقارنة نقاطك بمنظمات مثل مؤسستك

هناك مكانان لمعرفة كيفية مقارنة نقاطك مع المؤسسات المشابهة لسجلاتك.

#### <a name="comparison-bar-chart"></a>مخطط شريطي مقارنة

يتوفر مخطط المقارنة الشريطي على علامة التبويب **نظرة** عامة. مرر فوق المخطط لعرض فرصة النتيجة والنتيجة. 

:::image type="content" source="../../media/secure-score/secure-score-comparison-bar.png" alt-text="مثال على الرسم البياني الشريطي لعشرات المؤسسات المماثلة في مدخل Microsoft 365 Defender" lightbox="../../media/secure-score/secure-score-comparison-bar.png":::

يتم إخفاء هوية بيانات المقارنة حتى لا نعرف بالضبط المستأجرين الآخرين في هذا الخلط.

![رسم بياني شريطي لحرز نتائج مماثلة في المؤسسة.](../../media/secure-score/secure-score-comparison-screenshot.png)

#### <a name="comparison-trend"></a>اتجاه المقارنة

في علامة **التبويب المقاييس & الاتجاهات** ، يمكنك عرض كيفية مقارنة "نقاط آمنة" في مؤسستك مع الآخرين مع مرور الوقت.

:::image type="content" source="../../media/secure-score/secure-score-comparison-trend.png" alt-text="مثال على رسم بياني لخط نقاط مؤسسة مماثلة مع مرور الوقت في Microsoft 365 Defender المدخل" lightbox="../../media/secure-score/secure-score-comparison-trend.png":::

## <a name="we-want-to-hear-from-you"></a>نريد أن نستمع منك

إذا كانت لديك أي مشاكل، فأعلمنا بذلك من خلال النشر في مجتمع الأمان [والخصوصية & التوافق](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . نحن نراقب المجتمع وسنوفر المساعدة.

## <a name="related-resources"></a>الموارد ذات الصلة

- [نظرة عامة حول Microsoft Secure Score](microsoft-secure-score.md)
- [تقييم وضعية الأمان](microsoft-secure-score-improvement-actions.md)
- [ما هو قادم](microsoft-secure-score-whats-coming.md)
- [ما الجديد](microsoft-secure-score-whats-new.md)
