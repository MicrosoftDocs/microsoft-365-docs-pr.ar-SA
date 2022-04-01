---
title: فهم تقرير HTML لمحلل العميل
description: تعرف على كيفية تحليل تقرير HTML الخاص ب Microsoft Defender for Endpoint Client Analyzer
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
ms.openlocfilehash: ab6a23d1f2c8893a86fb6432ab9fece95a10006c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579705"
---
# <a name="understand-the-client-analyzer-html-report"></a>فهم تقرير HTML لمحلل العميل

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

وينتج محلل العميل تقريرا بتنسيق HTML. تعرف على كيفية مراجعة التقرير لتحديد مشاكل المستشعر المحتملة حتى تتمكن من استكشاف الأخطاء وإصلاحها.

استخدم المثال التالي لفهم التقرير.

 مثال إخراج من المحلل على جهاز تم تشغيله إلى "معروف المؤسسة" منتهية الصلاحية وفشل في الوصول إلى أحد عناوين URL المطلوبة من Microsoft Defender لنقطة النهاية:

![صورة لنتيجة محلل العميل.](images/147cbcf0f7b6f0ff65d200bf3e4674cb.png)

- في الأعلى، يتم سرد إصدار البرنامج النصي و وقت تشغيل البرنامج النصي كمرجع
- يوفر **القسم معلومات** الجهاز معرفات نظام التشغيل والجهاز الأساسية لتعريف الجهاز الذي يعمل عليه المحلل بشكل فريد.
- توفر **تفاصيل أمان نقطة** النهاية معلومات عامة حول العمليات ذات الصلة بنقطة النهاية ل Microsoft Defender بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender وعمليات الاستشعار. إذا لم تكن العمليات الهامة عبر الإنترنت كما هو متوقع، سيتغير اللون إلى اللون الأحمر.

  ![صورة لالنتيجة المفصلة لمحلل العميل](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   توفر **تفاصيل أمان نقطة** النهاية معلومات عامة حول العمليات ذات الصلة بنقطة النهاية ل Microsoft Defender بما في ذلك برنامج الحماية من الفيروسات من Microsoft Defender وعمليات الاستشعار. إذا لم تكن العمليات الهامة عبر الإنترنت كما هو متوقع، سيتغير اللون إلى اللون الأحمر.

  ![صورة النتيجة المفصلة لمحلل العميل.](images/85f56004dc6bd1679c3d2c063e36cb80.png)

-   في **ملخص التحقق** من النتائج، سيكون لديك عدد مجمع للخطأ أو التحذير أو الأحداث الإعلامية التي كشف عنها المحلل.

-   في **النتائج المفصلة** ، سترى قائمة (تم فرزها حسب الخطورة) مع النتائج والإرشادات استنادا إلى الملاحظات التي قام بها المحلل.

## <a name="open-a-support-ticket-to-microsoft-and-include-the-analyzer-results"></a>فتح تذكرة دعم إلى Microsoft وتضمين نتائج محلل

لتضمين ملفات نتائج المحلل [عند فتح تذكرة دعم](contact-support.md#open-a-service-request)، تأكد من استخدام المقطع المرفقات  وتضمين `MDEClientAnalyzerResult.zip` الملف:

![صورة لمطالبة المرفق.](images/508c189656c3deb3b239daf811e33741.png)

> [!NOTE]
> إذا كان حجم الملف أكبر من 25 مبايت، سيوفر مهندس الدعم المعين لقضيتك مساحة عمل آمنة مخصصة لتحميل الملفات الكبيرة لتحليلها.
