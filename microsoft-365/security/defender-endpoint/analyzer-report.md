---
title: فهم تقرير HTML لمحلل العميل
description: تعرف على كيفية تحليل Microsoft Defender لنقطة النهاية HTML الخاص ب "محلل العملاء"
keywords: تقرير محلل العميل، تقرير html، محلل العميل
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1f843c62d44ed7c25f07568cc0ee92709fb080a7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468888"
---
# <a name="understand-the-client-analyzer-html-report"></a>فهم تقرير HTML لمحلل العميل

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

وينتج محلل العميل تقريرا بتنسيق HTML. تعرف على كيفية مراجعة التقرير لتحديد مشاكل المستشعر المحتملة حتى تتمكن من استكشاف الأخطاء وإصلاحها.

استخدم المثال التالي لفهم التقرير.

 مثال إخراج من المحلل على جهاز تم إرساءه إلى "معرف المؤسسة" منتهية الصلاحية وفشل في الوصول إلى أحد Microsoft Defender لنقطة النهاية URL:

:::image type="content" source="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png" alt-text="صفحة نتائج محلل عميل MDE" lightbox="images/147cbcf0f7b6f0ff65d200bf3e4674cb.png":::

- في الأعلى، يتم سرد إصدار البرنامج النصي و وقت تشغيل البرنامج النصي كمرجع
- يوفر **القسم معلومات** الجهاز معرفات نظام التشغيل والجهاز الأساسية لتعريف الجهاز الذي يعمل عليه المحلل بشكل فريد.
- توفر **تفاصيل أمان نقطة** النهاية معلومات عامة حول Microsoft Defender لنقطة النهاية ذات الصلة بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender وعمليات الاستشعار. إذا لم تكن العمليات الهامة عبر الإنترنت كما هو متوقع، سيتغير اللون إلى اللون الأحمر.
  
-   توفر **تفاصيل أمان نقطة** النهاية معلومات عامة حول Microsoft Defender لنقطة النهاية ذات الصلة بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender وعمليات الاستشعار. إذا لم تكن العمليات الهامة عبر الإنترنت كما هو متوقع، سيتغير اللون إلى اللون الأحمر.

    :::image type="content" source="images/85f56004dc6bd1679c3d2c063e36cb80.png" alt-text="صفحة &quot;التحقق من ملخص النتائج&quot;" lightbox="images/85f56004dc6bd1679c3d2c063e36cb80.png":::

-   في **التحقق من ملخص** النتائج، سيكون لديك عدد مجمع للخطأ أو التحذير أو الأحداث الإعلامية التي كشف عنها المحلل.

-   في **النتائج المفصلة**، سترى قائمة (تم فرزها حسب الخطورة) مع النتائج والإرشادات استنادا إلى الملاحظات التي قام المحلل بها.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>فتح تذكرة دعم إلى Microsoft وتضمين نتائج محلل

لتضمين ملفات نتائج المحلل [عند فتح تذكرة دعم](contact-support.md#open-a-service-request)، تأكد من استخدام المقطع المرفقات  وتضمين `MDEClientAnalyzerResult.zip` الملف:

:::image type="content" source="images/508c189656c3deb3b239daf811e33741.png" alt-text="مطالبة مرفق" lightbox="images/508c189656c3deb3b239daf811e33741.png":::

> [!NOTE]
> إذا كان حجم الملف أكبر من 25 مبايت، سيوفر مهندس الدعم المعين لقضيتك مساحة عمل آمنة مخصصة لتحميل الملفات الكبيرة لتحليلها.
