---
title: تحسين عرض الصفحة في SharePoint صفحات الموقع الحديثة عبر الإنترنت
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية استخدام أداة تشخيص الصفحة لتحسين عرض الصفحة في SharePoint صفحات الموقع الحديثة عبر الإنترنت.
ms.openlocfilehash: 2c7221befc89fd0385b3e96a31fc7721f012628d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568946"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a>تحسين عرض الصفحة في SharePoint صفحات الموقع الحديثة عبر الإنترنت

SharePoint صفحات الموقع الحديثة عبر الإنترنت التعليمات البرمجية التسلسلية المطلوبة لتقديم محتوى الصفحة للصفحة، بما في ذلك الصور والنص والكائنات في منطقة المحتوى أسفل أشرطة التنقل/الأوامر وغيرها من تعليمات HTML البرمجية التي تشكل إطار عمل الصفحة. إن عرض الصفحة هو قياس لرمز HTML هذا، ويجب أن يكون محدودا لضمان أفضل أوقات تحميل الصفحات.

ستساعدك هذه المقالة على فهم كيفية تقليل عرض الصفحة في صفحات الموقع الحديثة.

>[!NOTE]
>لمزيد من المعلومات حول الأداء في SharePoint الإنترنت الحديثة، راجع الأداء [في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a>استخدام أداة تشخيص الصفحة SharePoint لتحليل عرض الصفحة

أداة تشخيص الصفحة SharePoint هي ملحق مستعرض للمستعرض الجديد Microsoft Edge (https://www.microsoft.com/edge) ومستعرضات Chrome التي تحلل كل من SharePoint الحديث عبر الإنترنت وصفحات موقع النشر الكلاسيكي. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت أداة تشخيص الصفحة SharePoint للتعرف عليها، تفضل بزيارة استخدام أداة تشخيص الصفحة [SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>تعمل الأداة "تشخيص الصفحة" فقط SharePoint Online، ولا يمكن استخدامها على صفحة SharePoint ويب.

عند تحليل صفحة موقع SharePoint باستخدام أداة تشخيص الصفحة ل SharePoint، يمكنك الاطلاع على معلومات حول الصفحة في نتيجة عرض الصفحة أقل من **500KB** من جزء اختبارات التشخيص. ستظهر النتيجة باللون الأخضر إذا كان عرض الصفحة تحت قيمة الأساس، والأحمر إذا تجاوز عرض الصفحة قيمة الأساس.

تتضمن النتائج المحتملة:

- **الانتباه مطلوب** (أحمر): يتجاوز عرض الصفحة 500 ألف ك.ب
- **لا يتطلب أي إجراء** (أخضر): يكون عرض الصفحة أقل من 500KB

إذا ظهر **عرض الصفحة أقل من 500KB** في المقطع **الانتباه** المطلوب، يمكنك النقر فوق النتيجة للحصول على التفاصيل.

![طلبات SharePoint النتائج.](../media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a>إصلاح مشاكل عرض الصفحة

إذا تجاوز عرض الصفحة 500KB، يمكنك تحسين الوقت الإجمالي لتحميل الصفحة عن طريق تقليل عدد أجزاء ويب وقصر محتوى الصفحة على درجة مناسبة.

تتضمن الإرشادات العامة لتقليل عرض الصفحة ما يلي:

- يمكنك حصر محتوى الصفحة بمبلغ معقول واستخدام صفحات متعددة للمحتوى ذي الصلة.
- تقليل استخدام أجزاء ويب التي بها اكياس ملكية كبيرة.
- استخدم طرق عرض الالتفاف غير التفاعلية عندما يكون ذلك ممكنا.
- يمكنك تحسين أحجام الصور عن طريق تحديد حجم الصور بشكل مناسب، باستخدام تنسيقات الصور المضغوطة وضمان تنزيلها من CDN.

يمكنك العثور على إرشادات إضافية للحد من عرض الصفحة في المقالة التالية:

- [تحسين أداء الصفحة في SharePoint](/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

قبل إجراء مراجعات للصفحة من أجل حل مشاكل الأداء، دون وقت تحميل الصفحة في نتائج التحليل. قم بتشغيل الأداة مرة أخرى بعد المراجعة لمعرفة ما إذا كانت النتيجة الجديدة ضمن معيار الأساس، وتحقق من وقت تحميل الصفحة الجديدة لمعرفة ما إذا كان هناك أي تحسين.

![نتائج وقت تحميل الصفحة.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>يمكن أن يختلف وقت تحميل الصفحة استنادا إلى مجموعة متنوعة من العوامل مثل تحميل الشبكة والوقت من اليوم والشروط الأخرى غير المتتية. يجب اختبار وقت تحميل الصفحة بضع مرات قبل إجراء التغييرات وبعدها لمساعدتك على متوسط النتائج.

## <a name="related-topics"></a>المواضيع ذات الصلة

[ضبط SharePoint عبر الإنترنت](tune-sharepoint-online-performance.md)

[ضبط Office 365 الأداء](tune-microsoft-365-performance.md)

[الأداء في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance)

[شبكات تسليم المحتوى](content-delivery-networks.md)

[استخدام Office 365 تسليم المحتوى (CDN) مع SharePoint Online](use-microsoft-365-cdn-with-spo.md)