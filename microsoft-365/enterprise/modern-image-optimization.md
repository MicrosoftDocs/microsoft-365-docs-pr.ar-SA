---
title: تحسين الصور في SharePoint صفحات الموقع الحديثة عبر الإنترنت
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
description: تعرف على كيفية استخدام الأدوات المضمنة في SharePoint Online لتحسين الصور في SharePoint صفحات الموقع الحديثة عبر الإنترنت.
ms.openlocfilehash: 85280dfc903c56c89308c50fa94979fd98b2003c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569617"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a>تحسين الصور في SharePoint صفحات الموقع الحديثة عبر الإنترنت

ستساعدك هذه المقالة على فهم كيفية تحسين الصور في SharePoint صفحات الموقع الحديثة عبر الإنترنت.

للحصول على معلومات حول تحسين الصور في مواقع النشر الكلاسيكية، راجع تحسين الصور [SharePoint Online](image-optimization-for-sharepoint-online.md)..

>[!NOTE]
>لمزيد من المعلومات حول الأداء في SharePoint الإنترنت الحديثة، راجع الأداء [في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a>استخدام أداة تشخيص الصفحة SharePoint لتحليل تحسين الصور

أداة تشخيص الصفحة SharePoint هي ملحق مستعرض للمستعرض الجديد Microsoft Edge (https://www.microsoft.com/edge) ومستعرضات Chrome التي تحلل كل من SharePoint الحديث عبر الإنترنت وصفحات موقع النشر الكلاسيكي. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت أداة تشخيص الصفحة SharePoint للتعرف عليها، تفضل بزيارة استخدام أداة تشخيص الصفحة [SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>تعمل الأداة "تشخيص الصفحة" فقط SharePoint Online، ولا يمكن استخدامها على صفحة SharePoint ويب.

عند تحليل موقع SharePoint حديث باستخدام أداة تشخيص الصفحة SharePoint، يمكنك رؤية معلومات حول الصور الكبيرة في جزء _الاختبارات_ التشخيصية.

تتضمن النتائج المحتملة:

- **الانتباه مطلوب** (أحمر): تحتوي الصفحة على **صورة واحدة أو** أكثر يزيد حجمها عن 300KB
- **لا يتطلب أي إجراء** (أخضر): لا تحتوي الصفحة على صور يزيد حجمها عن 300KB

إذا ظهر **الناتج صور** كبيرة تم الكشف عنها في المقطع **انتباه** مطلوب من النتائج، يمكنك النقر فوق النتيجة للاطلاع على تفاصيل إضافية.

![نتائج أداة تشخيص الصفحة.](../media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a>إصلاح مشاكل الصور الكبيرة

إذا كانت الصفحة تحتوي على صور يزيد حجمها عن 300 ك.ب، فحدد النتيجة الصور الكبيرة التي تم الكشف عنها لمعرفة الصور الكبيرة جدا. في SharePoint صفحات الإنترنت الحديثة، يتم توفير التسليمات للصور وحجمها تلقائيا استنادا إلى حجم نافذة المستعرض و دقة جهاز عرض العميل. يجب عليك دائما تحسين الصور لاستخدام الويب قبل التحميل إلى SharePoint Online. سيتم تقليل حجم الصور الكبيرة جدا و الدقة تلقائيا مما قد يؤدي إلى خصائص عرض غير متوقعة.

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