---
title: تحسين iFrames في صفحات موقع النشر الحديثة والكلاسيكية SharePoint Online
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: تعرف على كيفية تحسين أداء iFrames في SharePoint صفحات موقع النشر الحديثة والكلاسيكية عبر الإنترنت.
ms.openlocfilehash: 0e8710b76d20388ba3514b32fe598e982a7a9561
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100688"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>تحسين iFrames في صفحات موقع النشر الحديثة والكلاسيكية SharePoint Online

يمكن أن تكون iFrames مفيدة لمعاينة المحتوى المنسق مثل مقاطع الفيديو أو الوسائط الأخرى. ومع ذلك، نظرا لأن iFrames تقوم بتحميل صفحة منفصلة داخل صفحة موقع SharePoint، يمكن أن يحتوي المحتوى المحمل في iFrame على صور كبيرة أو مقاطع فيديو أو عناصر أخرى يمكن أن تساهم في أوقات تحميل الصفحة الإجمالية ولا يمكنك التحكم فيها على الصفحة. ستساعدك هذه المقالة على فهم كيفية تحديد كيفية تأثير iFrames في صفحاتك على زمن الانتقال المتصور للمستخدم، وكيفية معالجة المشكلات الشائعة.

>[!NOTE]
>لمزيد من المعلومات حول الأداء في المواقع الحديثة SharePoint Online، راجع [Performance في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>استخدام "تشخيصات الصفحة" لأداة SharePoint لتحليل أجزاء ويب باستخدام iFrames

أداة "تشخيص الصفحة" SharePoint هي ملحق مستعرض Microsoft Edge الجديد (https://www.microsoft.com/edge) ومستعرضات Chrome التي تحلل كل من مدخل SharePoint Online الحديث وصفحات موقع النشر الكلاسيكية. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت الأداة "تشخيصات الصفحة SharePoint" والتعرف عليها، [قم بزيارة "استخدام أداة تشخيص الصفحة" SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>تعمل أداة "تشخيص الصفحة" فقط مع SharePoint Online، ولا يمكن استخدامها في صفحة نظام SharePoint.

عند تحليل صفحة موقع SharePoint باستخدام أداة تشخيص الصفحة SharePoint، يمكنك رؤية معلومات حول أجزاء ويب التي تحتوي على iFrames في جزء _الاختبارات التشخيصية_. مقياس الأساس هو نفسه للصفحات الحديثة والكلاسيكية.

تتضمن النتائج المحتملة ما يلي:

- **الانتباه مطلوب** (أحمر): تحتوي الصفحة على ثلاثة أجزاء ويب **أو أكثر** باستخدام iFrames
- **فرص التحسين** (أصفر): تحتوي الصفحة على **جزء ويب واحد أو جزأين** على الويب باستخدام iFrames
- **لا يوجد إجراء مطلوب** (أخضر): لا تحتوي الصفحة على أجزاء ويب باستخدام iFrames

إذا ظهرت **أجزاء ويب التي تستخدم نتائج iFrames المكتشفة** في قسم **فرص التحسين** أو **الانتباه المطلوب)** من النتائج، يمكنك النقر فوق النتيجة لرؤية أجزاء الويب التي تحتوي على iFrames.

![نتائج أداة تشخيص الصفحة.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>معالجة مشكلات أداء iFrame

استخدم **أجزاء ويب باستخدام نتيجة iFrames المكتشفة** في أداة تشخيص الصفحة لتحديد أجزاء الويب التي تحتوي على iFrames وقد تساهم في بطء أوقات تحميل الصفحة.

iFrames بطيئة بطبيعتها لأنها تقوم بتحميل صفحة خارجية منفصلة بما في ذلك جميع المحتويات المرتبطة مثل javascript وCSS وعناصر إطار العمل، مما قد يزيد من الحمل على صفحة الموقع بواسطة عامل اثنين أو أكثر.

اتبع الإرشادات أدناه لضمان الاستخدام الأمثل ل iFrames.

- عندما يكون ذلك ممكنا، استخدم الصور بدلا من iFrames إذا كانت المعاينة صغيرة للبدء أو غير تفاعلية.
- إذا كان يجب استخدام iFrames، فقم بتصغير الرقم و/أو انقله خارج منفذ العرض.
- تعد ملفات Office المضمنة مثل Word Excel PowerPoint تفاعلية ولكنها بطيئة التحميل. غالبا ما تؤدي الصور المصغرة للصور التي تحتوي على ارتباط إلى المستند الكامل أداء أفضل.
- تميل مقاطع فيديو YouTube المضمنة وموجزات Twitter إلى الأداء بشكل أفضل في iFrames، ولكنها تستخدم هذه الأنواع من التضمينات بحكمة.
- تعد أجزاء ويب المعزولة استثناء معقولا، ولكنها تقلل من رقمها وموضعها في منفذ العرض.
- إذا كان iFrame موجودا خارج منفذ العرض، ففكر في استخدام _خادم التقاطع_ لتأخير عرض iFrame حتى يظهر.

قبل إجراء مراجعات الصفحة لمعالجة مشكلات الأداء، دون ملاحظة لوقت تحميل الصفحة في نتائج التحليل. قم بتشغيل الأداة مرة أخرى بعد المراجعة لمعرفة ما إذا كانت النتيجة الجديدة ضمن معيار الأساس، وتحقق من وقت تحميل الصفحة الجديدة لمعرفة ما إذا كان هناك تحسن.

![نتائج وقت تحميل الصفحة.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>يمكن أن يختلف وقت تحميل الصفحة استنادا إلى مجموعة متنوعة من العوامل مثل تحميل الشبكة ووقت اليوم والظروف العابرة الأخرى. يجب اختبار وقت تحميل الصفحة عدة مرات قبل إجراء التغييرات وبعدها لمساعدتك على متوسط النتائج.

## <a name="related-topics"></a>المواضيع ذات الصلة

[ضبط أداء SharePoint Online](tune-sharepoint-online-performance.md)

[ضبط أداء Office 365](tune-microsoft-365-performance.md)

[الأداء في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance)