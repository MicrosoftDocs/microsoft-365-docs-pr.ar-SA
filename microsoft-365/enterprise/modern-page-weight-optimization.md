---
title: تحسين عرض الصفحة في صفحات الموقع الحديثة SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: sstewart
search.appverid:
- MET150
description: تعرف على كيفية استخدام أداة "تشخيص الصفحة" لتحسين عرض الصفحة في SharePoint صفحات الموقع الحديثة عبر الإنترنت.
ms.openlocfilehash: 01a1976972983cccf3e93006e395f789d5882eff
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101194"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>تحسين عرض الصفحة في صفحات الموقع الحديثة SharePoint Online

SharePoint صفحات الموقع الحديثة عبر الإنترنت تحتوي على تعليمات برمجية متسلسلة مطلوبة لعرض محتوى الصفحة، بما في ذلك الصور والنصوص والعناصر في منطقة المحتوى أسفل أشرطة التنقل/الأوامر والتعليمات البرمجية الأخرى ل HTML التي تشكل إطار عمل الصفحة. وزن الصفحة هو مقياس لرمز HTML هذا، ويجب أن يقتصر على ضمان أوقات تحميل الصفحة المثلى.

ستساعدك هذه المقالة على فهم كيفية تقليل عرض الصفحة في صفحات موقعك الحديثة.

>[!NOTE]
>لمزيد من المعلومات حول الأداء في SharePoint المداخل الحديثة عبر الإنترنت، راجع [Performance في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>استخدام "تشخيصات الصفحة" لأداة SharePoint لتحليل عرض الصفحة

أداة "تشخيص الصفحة" SharePoint هي ملحق مستعرض Microsoft Edge الجديد (https://www.microsoft.com/edge) ومستعرضات Chrome التي تحلل كل من مدخل SharePoint Online الحديث وصفحات موقع النشر الكلاسيكية. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت الأداة "تشخيصات الصفحة SharePoint" والتعرف عليها، [قم بزيارة "استخدام أداة تشخيص الصفحة" SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>تعمل أداة "تشخيص الصفحة" فقط مع SharePoint Online، ولا يمكن استخدامها في صفحة نظام SharePoint.

عند تحليل صفحة موقع SharePoint باستخدام أداة تشخيص الصفحة SharePoint، يمكنك رؤية معلومات حول الصفحة في **وزن الصفحة أقل من 500 كيلوبايت** من جزء _الاختبارات التشخيصية_. ستظهر النتيجة باللون الأخضر إذا كان عرض الصفحة تحت قيمة الأساس، والأحمر إذا تجاوز عرض الصفحة قيمة الأساس.

تتضمن النتائج المحتملة ما يلي:

- **الانتباه مطلوب** (أحمر): يتجاوز وزن الصفحة 500 كيلوبايت
- **لا يلزم اتخاذ أي إجراء** (أخضر): وزن الصفحة أقل من 500 كيلوبايت

إذا ظهر **عرض الصفحة أقل من 500 كيلوبايت** في القسم **"الانتباه المطلوب** "، يمكنك النقر فوق النتيجة للحصول على التفاصيل.

![طلبات SharePoint النتائج.](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>معالجة مشكلات وزن الصفحة

إذا تجاوز عرض الصفحة 500 كيلوبايت، يمكنك تحسين وقت تحميل الصفحة الإجمالي عن طريق تقليل عدد أجزاء ويب وتقييد محتوى الصفحة بدرجة مناسبة.

تتضمن الإرشادات العامة لتقليل عرض الصفحة ما يلي:

- قم بتقييد محتوى الصفحة بكمية معقولة واستخدم صفحات متعددة للمحتوى ذي الصلة.
- تقليل استخدام أجزاء الويب التي تحتوي على اكياس خصائص كبيرة.
- استخدم طرق العرض المحتسبة غير التفاعلية عندما يكون ذلك ممكنا.
- تحسين أحجام الصور عن طريق تغيير حجم الصور بشكل مناسب، باستخدام تنسيقات الصور المضغوطة والتأكد من تنزيلها من شبكة تسليم المحتوى.

يمكنك العثور على إرشادات إضافية للحد من عرض الصفحة في المقالة التالية:

- [تحسين أداء الصفحة في SharePoint](/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

قبل إجراء مراجعات الصفحة لمعالجة مشكلات الأداء، دون ملاحظة لوقت تحميل الصفحة في نتائج التحليل. قم بتشغيل الأداة مرة أخرى بعد المراجعة لمعرفة ما إذا كانت النتيجة الجديدة ضمن معيار الأساس، وتحقق من وقت تحميل الصفحة الجديدة لمعرفة ما إذا كان هناك تحسن.

![نتائج وقت تحميل الصفحة.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>يمكن أن يختلف وقت تحميل الصفحة استنادا إلى مجموعة متنوعة من العوامل مثل تحميل الشبكة ووقت اليوم والظروف العابرة الأخرى. يجب اختبار وقت تحميل الصفحة عدة مرات قبل إجراء التغييرات وبعدها لمساعدتك على متوسط النتائج.

## <a name="related-topics"></a>المواضيع ذات الصلة

[ضبط أداء SharePoint Online](tune-sharepoint-online-performance.md)

[ضبط أداء Office 365](tune-microsoft-365-performance.md)

[الأداء في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance)

[شبكات تسليم المحتوى](content-delivery-networks.md)

[استخدام شبكة تسليم المحتوى Office 365 (CDN) مع SharePoint Online](use-microsoft-365-cdn-with-spo.md)