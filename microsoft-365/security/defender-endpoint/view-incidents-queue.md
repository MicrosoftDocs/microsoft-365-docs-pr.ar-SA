---
title: عرض قائمة انتظار الأحداث وتنظيمها
ms.reviewer: ''
description: راجع قائمة الحوادث وتعرف على كيفية تطبيق عوامل التصفية للحد من القائمة والحصول على طريقة عرض أكثر تركيزا.
keywords: العرض، والتنظيم، والحوادث، والتجميع، والتحقيقات، وقوائم الانتظار، وttp
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a2d75b935c19a20c37ecdbdb77feff73bbed4a79
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/11/2022
ms.locfileid: "66714630"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>عرض قائمة انتظار أحداث Microsoft Defender لنقطة النهاية وتنظيمها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

تعرض **قائمة انتظار الحوادث** مجموعة من الحوادث التي تم وضع علامة عليها من الأجهزة في شبكتك. فهو يساعدك على فرز الحوادث لتحديد أولويات وإنشاء قرار مدروس للاستجابة للأمان عبر الإنترنت.

بشكل افتراضي، تعرض قائمة الانتظار الحوادث التي تمت مشاهدتها في آخر 30 يوما، مع عرض أحدث حادث في أعلى القائمة، مما يساعدك على رؤية أحدث الحوادث أولا.

هناك العديد من الخيارات التي يمكنك الاختيار من بينها لتخصيص طريقة عرض قائمة انتظار الحوادث. 

في الجزء العلوي من التنقل، يمكنك:
- تخصيص الأعمدة لإضافة أعمدة أو إزالتها 
- تعديل عدد العناصر المطلوب عرضها لكل صفحة
- تحديد العناصر التي تريد إظهارها لكل صفحة
- حدد Batch الأحداث التي تريد تعيينها 
- التنقل بين الصفحات
- تطبيق عوامل التصفية
- تخصيص نطاقات التاريخ وتطبيقها

:::image type="content" source="images/atp-incident-queue.png" alt-text="قائمة انتظار الحوادث" lightbox="images/atp-incident-queue.png":::

## <a name="sort-and-filter-the-incidents-queue"></a>فرز قائمة انتظار الأحداث وتصفيتها
يمكنك تطبيق عوامل التصفية التالية للحد من قائمة الحوادث والحصول على طريقة عرض أكثر تركيزا.

### <a name="severity"></a>شده

خطورة الحادث | الوصف
:---|:---
عاليه </br>(أحمر) | التهديدات المرتبطة غالبا بالتهديدات المستمرة المتقدمة (APT). تشير هذه الحوادث إلى مخاطر عالية بسبب شدة الضرر الذي يمكن أن تلحقه بالأجهزة.
المتوسطه </br>(برتقالي) | نادرا ما تلاحظ التهديدات في المؤسسة، مثل تغيير السجل الشاذ وتنفيذ الملفات المشبوهة والسلوكيات الملحوظة النموذجية لمراحل الهجوم.
منخفضه </br>(أصفر) | التهديدات المرتبطة بالبرامج الضارة الشائعة وأدوات الاختراق التي لا تشير بالضرورة إلى تهديد متقدم يستهدف المؤسسة.
اعلاميه </br>(رمادي) | قد لا تعتبر الحوادث الإعلامية ضارة بالشبكة ولكنها قد تكون جيدة لتتبعها.

## <a name="assigned-to"></a>تم التعيين إلى
يمكنك اختيار تصفية القائمة عن طريق تحديد معين إلى أي شخص أو أي شخص تم تعيينه لك.

### <a name="category"></a>الفئة
يتم تصنيف الحوادث استنادا إلى وصف المرحلة التي تكون فيها سلسلة القتل المتعلقة بالأمان عبر الإنترنت. يساعد هذا العرض محلل المخاطر على تحديد الأولوية والسرعة واستراتيجية الاستجابة المقابلة للنشر استنادا إلى السياق.

### <a name="status"></a>حاله
يمكنك اختيار تحديد قائمة الحوادث المعروضة استنادا إلى حالتها لمعرفة الحوادث النشطة أو التي تم حلها.

### <a name="data-sensitivity"></a>حساسية البيانات
استخدم عامل التصفية هذا لإظهار الحوادث التي تحتوي على تسميات الحساسية.

## <a name="incident-naming"></a>تسمية الحدث

لفهم نطاق الحدث بنظرة سريعة، يتم إنشاء أسماء الحوادث تلقائيا استنادا إلى سمات التنبيه مثل عدد نقاط النهاية المتأثرة والمستخدمين المتأثرين ومصادر الكشف أو الفئات.

على سبيل المثال: *حدث متعدد المراحل على نقاط نهاية متعددة تم الإبلاغ عنها من قبل مصادر متعددة.*

> [!NOTE]
> ستحتفظ الحوادث التي كانت موجودة قبل إطلاق تسمية الحوادث التلقائية باسمها.


## <a name="see-also"></a>راجع أيضًا
- [قائمة انتظار الأحداث](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [إدارة الأحداث](manage-incidents.md)
- [التحقيق في الأحداث](investigate-incidents.md)

