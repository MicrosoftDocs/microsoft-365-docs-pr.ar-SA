---
title: عرض قائمة انتظار الأحداث وتنظيمها
ms.reviewer: ''
description: راجع قائمة الأحداث وتعرف على كيفية تطبيق عوامل التصفية للحد من القائمة والحصول على طريقة عرض أكثر تركيزا.
keywords: العرض والتنظيم والحوادث والجمعية، التحقيق، قائمة الانتظار، ttp
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
ms.openlocfilehash: df5cbf5297a17dafb80a93ed49c7f7d81bc49d68
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474344"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>عرض قائمة انتظار Microsoft Defender لنقطة النهاية الأحداث وتنظيمها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

تعرض **قائمة انتظار** "الأحداث" مجموعة من الأحداث التي تم وضع علامة عليها من الأجهزة الموجودة في شبكتك. يساعدك ذلك على الفرز عبر الأحداث لتحديد أولويات قرار استجابة الأمان الإلكتروني المستنير وإنشاءه.

بشكل افتراضي، تعرض قائمة الانتظار الأحداث التي تم عرضها في آخر 30 يوما، مع عرض آخر حادث في أعلى القائمة، مما يساعدك على رؤية الأحداث الأخيرة أولا.

هناك العديد من الخيارات التي يمكنك الاختيار من بينها لتخصيص طريقة عرض قائمة انتظار الأحداث. 

في أعلى شريط التنقل، يمكنك:
- تخصيص الأعمدة لإضافة أعمدة أو إزالتها 
- تعديل عدد العناصر التي تريد عرضها لكل صفحة
- تحديد العناصر التي تريد إظهارها لكل صفحة
- تحديد الأحداث على دفعات لتعيينها 
- التنقل بين الصفحات
- تطبيق عوامل التصفية

:::image type="content" source="images/atp-incident-queue.png" alt-text="قائمة انتظار &quot;الأحداث&quot;" lightbox="images/atp-incident-queue.png":::

## <a name="sort-and-filter-the-incidents-queue"></a>فرز قائمة انتظار الأحداث وتصفيتها
يمكنك تطبيق عوامل التصفية التالية للحد من قائمة الأحداث والحصول على طريقة عرض أكثر تركيزا.

### <a name="severity"></a>الخطورة

خطورة الحادث | الوصف
:---|:---
عال </br>(Red) | غالبا ما تقترن التهديدات بخطر دائم متقدم (APT). تشير هذه الأحداث إلى وجود مخاطر عالية بسبب خطورة الضرر الذي يمكن أن تسببه على الأجهزة.
متوسط </br>(Orange) | نادرا ما يتم ملاحظة التهديدات في المؤسسة، مثل تغيير التسجيل الغريب وتنفيذ الملفات المريبة والسلوكيات التي تم ملاحظتها في مراحل الهجوم.
منخفض </br>(أصفر) | التهديدات المقترنة بالبرامج الضارة الشائعة وأدوات الإختراق التي لا تشير بالضرورة إلى وجود خطر متقدم يستهدف المؤسسة.
معلوماتية </br>(رمادي) | قد لا تعتبر الأحداث الإعلامية ضارة بالشبكة ولكنها قد تكون جيدة لتعقبها.

## <a name="assigned-to"></a>تم تعيين إلى
يمكنك اختيار تصفية القائمة عن طريق تحديد المعينة لأي شخص أو تلك المعينة لك.

### <a name="category"></a>الفئة
يتم تصنيف الأحداث استنادا إلى وصف المرحلة التي تكون فيها سلسلة مكافحة أمن الإنترنت. تساعد طريقة العرض هذه محلل المخاطر في تحديد الأولوية والالحاح وإستراتيجية الاستجابة المقابلة لنشرها استنادا إلى السياق.

### <a name="status"></a>الحالة
يمكنك اختيار تحديد قائمة الأحداث المعروضة استنادا إلى حالة هذه الأحداث لمعرفة الأحداث النشطة أو التي تم حلها.

### <a name="data-sensitivity"></a>حساسية البيانات
استخدم عامل التصفية هذا لإظهار الأحداث التي تحتوي على تسميات الحساسية.

## <a name="incident-naming"></a>تسمية الأحداث

لفهم نطاق الحادث بنظرة سريعة، يتم تلقائيا إنشاء أسماء الأحداث استنادا إلى سمات التنبيه مثل عدد نقاط النهاية المتأثرة والمستخدمين المتأثرين ومصادر الكشف أو الفئات.

على سبيل المثال: *حادث متعدد المراحل على نقاط نهاية متعددة تم اعجابها بواسطة مصادر متعددة.*

> [!NOTE]
> ستحتفظ الأحداث التي كانت موجودة قبل طرح تسمية الأحداث التلقائية باسمها.


## <a name="see-also"></a>راجع أيضًا
- [قائمة انتظار الأحداث](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [إدارة الأحداث](manage-incidents.md)
- [التحقيق في الأحداث](investigate-incidents.md)

