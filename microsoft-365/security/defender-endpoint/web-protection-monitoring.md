---
title: مراقبة أمان استعراض الويب في Microsoft Defender لنقطة النهاية
description: استخدام حماية الويب في Microsoft Defender لنقطة النهاية لمراقبة أمان استعراض الويب
keywords: حماية الويب، الحماية من المخاطر على الويب، استعراض الويب، المراقبة، التقارير، البطاقات، قائمة المجالات، الأمان، التصيد الاحتيالي، البرامج الضارة، استغلال، مواقع الويب، حماية الشبكة، Edge، Internet Explorer، Chrome، Firefox، مستعرض ويب
search.appverid: met150
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
ms.openlocfilehash: 6d10354f68dd5ba26db7f4260425559167c8888c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570416"
---
# <a name="monitor-web-browsing-security"></a>مراقبة أمان استعراض الويب

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

تتيح لك ميزة حماية الويب مراقبة أمان استعراض الويب في مؤسستك من خلال التقارير > **حماية** ويب في Microsoft 365 Defender ويب. يحتوي التقرير على بطاقات توفر إحصائيات الكشف عن تهديدات الويب.

- **عمليات الكشف** عن تهديدات الويب مع مرور الوقت - تعرض هذه البطاقة الحالية عدد تهديدات الويب التي تم الكشف عنها حسب النوع خلال الفترة الزمنية المحددة (آخر 30 يوما، آخر 3 أشهر، آخر 6 أشهر)

  :::image type="content" alt-text="صورة البطاقة التي تعرض الكشف عن تهديدات الويب مع مرور الوقت." source="images/wtp-blocks-over-time.png" lightbox="images/wtp-blocks-over-time.png":::

- **ملخص الحماية من** المخاطر على الويب - تعرض هذه البطاقة إجمالي عمليات الكشف عن تهديدات الويب خلال ال 30 يوما الماضية، مع عرض التوزيع عبر الأنواع المختلفة من تهديدات الويب. يفتح تحديد شريحة قائمة المجالات التي تم العثور عليها مع مواقع الويب الضارة أو غير المرغوب فيها.

  :::image type="content" alt-text="صورة البطاقة التي تعرض ملخص الحماية من تهديدات الويب." source="images/wtp-summary.png" lightbox="images/wtp-summary.png":::

> [!NOTE]
> قد يستغرق الأمر ما يصل إلى 12 ساعة قبل أن تنعكس الكتلة في البطاقات أو قائمة المجالات.

## <a name="types-of-web-threats"></a>أنواع تهديدات الويب

تصنف حماية ويب مواقع الويب الضارة وغير المرغوب فيها كما يلي:

- **التصيد** الاحتيالي - مواقع الويب التي تحتوي على نماذج ويب منتحلة وغيرها من آليات التصيد الاحتيالي المصممة لتخدع المستخدمين في الكشف عن بيانات الاعتماد والمعلومات الحساسة الأخرى
- **البرامج الضارة** - مواقع الويب التي تستضيف البرامج الضارة وتستغل التعليمات البرمجية
- **مؤشر مخصص** - مواقع الويب التي أضفت عناوين URL أو مجالاتها إلى قائمة [المؤشرات](manage-indicators.md) المخصصة للحظر

## <a name="view-the-domain-list"></a>عرض قائمة المجالات

حدد فئة معينة من تهديدات الويب في بطاقة ملخص الحماية من المخاطر **على** الويب لفتح **صفحة** المجالات. تعرض هذه الصفحة قائمة المجالات ضمن فئة التهديدات هذه. توفر الصفحة المعلومات التالية لكل مجال:

- **عدد الوصول** - عدد طلبات عناوين URL في المجال
- **كتل** - عدد المرات التي تم فيها حظر الطلبات
- **اتجاه Access** - تغيير في عدد محاولات الوصول
- **فئة التهديد** - نوع التهديد على الويب
- **الأجهزة** - عدد الأجهزة التي بها محاولات وصول

حدد مجالا لعرض قائمة الأجهزة التي حاولت الوصول إلى عناوين URL في هذا المجال وقائمة عناوين URL.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول حماية الويب](web-protection-overview.md)
- [تصفية محتوى ويب](web-content-filtering.md)
- [الحماية من المخاطر على الويب](web-threat-protection.md)
- [الاستجابة إلى تهديدات الويب](web-protection-response.md)
