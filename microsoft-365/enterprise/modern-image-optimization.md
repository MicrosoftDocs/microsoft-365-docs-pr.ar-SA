---
title: تحسين الصور في صفحات الموقع الحديثة SharePoint Online
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
description: تعرف على كيفية استخدام الأدوات المضمنة في SharePoint Online لتحسين الصور في صفحات الموقع الحديثة SharePoint Online.
ms.openlocfilehash: 102555e25e48af19432a26e6e2a0cb17c78044b3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093822"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>تحسين الصور في صفحات الموقع الحديثة SharePoint Online

ستساعدك هذه المقالة على فهم كيفية تحسين الصور في صفحات الموقع الحديثة SharePoint Online.

للحصول على معلومات حول تحسين الصور في مواقع النشر الكلاسيكية، راجع [تحسين الصور SharePoint Online](image-optimization-for-sharepoint-online.md).

>[!NOTE]
>لمزيد من المعلومات حول الأداء في SharePoint المداخل الحديثة عبر الإنترنت، راجع [Performance في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>استخدام أداة "تشخيص الصفحة" SharePoint لتحليل تحسين الصورة

أداة "تشخيص الصفحة" SharePoint هي ملحق مستعرض Microsoft Edge الجديد (https://www.microsoft.com/edge) ومستعرضات Chrome التي تحلل كل من مدخل SharePoint Online الحديث وصفحات موقع النشر الكلاسيكية. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت الأداة "تشخيصات الصفحة SharePoint" والتعرف عليها، [قم بزيارة "استخدام أداة تشخيص الصفحة" SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>تعمل أداة "تشخيص الصفحة" فقط مع SharePoint Online، ولا يمكن استخدامها في صفحة نظام SharePoint.

عند تحليل موقع حديث SharePoint باستخدام أداة تشخيص الصفحة SharePoint، يمكنك رؤية معلومات حول الصور الكبيرة في جزء _الاختبارات التشخيصية_.

تتضمن النتائج المحتملة ما يلي:

- **الانتباه مطلوب** (أحمر): تحتوي الصفحة على صورة **واحدة أو أكثر** يزيد حجمها عن 300 كيلوبايت
- **لا يلزم اتخاذ أي إجراء** (أخضر): لا تحتوي الصفحة على صور يزيد حجمها عن 300 كيلوبايت

إذا ظهرت **النتيجة "الصور الكبيرة المكتشفة** " في القسم **"الانتباه" المطلوب** من النتائج، يمكنك النقر فوق النتيجة للاطلاع على تفاصيل إضافية.

![نتائج أداة تشخيص الصفحة.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>معالجة مشكلات الصور الكبيرة

إذا كانت الصفحة تحتوي على صور يزيد حجمها عن 300 كيلوبايت، فحدد النتيجة **"الصور الكبيرة" المكتشفة** لمعرفة الصور الكبيرة جدا. في صفحات SharePoint Online الحديثة، يتم توفير تسليمات الصور وتغيير حجمها تلقائيا استنادا إلى حجم نافذة المستعرض ودقة جهاز عرض العميل. يجب عليك دائما تحسين الصور لاستخدام الويب قبل التحميل إلى SharePoint Online. سيتم تلقائيا تقليل حجم الصور الكبيرة جدا ودقتها مما قد يؤدي إلى خصائص عرض غير متوقعة.

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