---
title: تحسين iFrames SharePoint صفحات موقع النشر الحديثة والكلاسيكية عبر الإنترنت
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
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: تعرف على كيفية تحسين أداء iFrames SharePoint صفحات موقع النشر الحديثة والكلاسيكية عبر الإنترنت.
ms.openlocfilehash: e38dd3922444228cdf54c8ef306fbbd9eafb81c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568802"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a>تحسين iFrames SharePoint صفحات موقع النشر الحديثة والكلاسيكية عبر الإنترنت

يمكن أن تكون iFrames مفيدة لمعاينة المحتوى الغني مثل ملفات الفيديو أو الوسائط الأخرى. ومع ذلك، نظرا لأن iFrames تقوم بتحميل صفحة منفصلة داخل صفحة موقع SharePoint، فقد يحتوي المحتوى الذي تم تحميله في iFrame على صور أو مقاطع فيديو أو عناصر أخرى كبيرة يمكن أن تساهم في إجمالي أوقات تحميل الصفحة ولا يمكنك التحكم بها على الصفحة. ستساعدك هذه المقالة على فهم كيفية تحديد كيفية تأثير iFrames في صفحاتك على زمن الوصول المتوقع للمستخدم، وكيفية حل المشاكل الشائعة.

>[!NOTE]
>لمزيد من المعلومات حول الأداء في SharePoint الحديثة عبر الإنترنت، راجع الأداء [في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance).

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a>استخدام أداة تشخيص الصفحة SharePoint لتحليل أجزاء الويب باستخدام iFrames

أداة تشخيص الصفحة SharePoint هي ملحق مستعرض للمستعرض الجديد Microsoft Edge (https://www.microsoft.com/edge) ومستعرضات Chrome التي تحلل كل من SharePoint الحديث عبر الإنترنت وصفحات موقع النشر الكلاسيكي. توفر الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة من معايير الأداء. لتثبيت أداة تشخيص الصفحة SharePoint للتعرف عليها، تفضل بزيارة استخدام أداة تشخيص الصفحة [SharePoint Online](page-diagnostics-for-spo.md).

>[!NOTE]
>تعمل الأداة "تشخيص الصفحة" فقط SharePoint Online، ولا يمكن استخدامها على صفحة SharePoint ويب.

عند تحليل صفحة موقع SharePoint باستخدام أداة تشخيص الصفحة SharePoint، يمكنك رؤية معلومات حول أجزاء ويب التي تحتوي على iFrames في جزء الاختبارات التشخيصية. مقياس الأساس هو نفسه للصفحات الحديثة والكلاسيكية.

تتضمن النتائج المحتملة:

- **الانتباه مطلوب** (أحمر): تحتوي الصفحة على **ثلاثة أجزاء ويب أو** أكثر باستخدام iFrames
- **فرص التحسين (الأصفر** ): تحتوي الصفحة على **جزء ويب** واحد أو جزأين باستخدام iFrames
- **ما من إجراء مطلوب** (أخضر): لا تحتوي الصفحة على أجزاء ويب باستخدام iFrames

إذا كانت أجزاء ويب التي تستخدم **iFrames** التي تم الكشف عنها تظهر في المقطع  فرص التحسين أو الانتباه المطلوب **)** من النتائج، يمكنك النقر فوق النتيجة لرؤية أجزاء الويب التي تحتوي على iFrames.

![نتائج أداة تشخيص الصفحة.](../media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a>إصلاح مشاكل أداء iFrame

استخدم أجزاء **ويب باستخدام iFrames** التي تم الكشف عنها في أداة تشخيص الصفحة لتحديد أجزاء الويب التي تحتوي على iFrames وقد تساهم في إبطاء أوقات تحميل الصفحات.

تكون iFrames بطيئة في جوهرها لأنها تحمل صفحة خارجية منفصلة بما في ذلك كل المحتوى المقترن مثل javascript و CSS وعناصر إطار العمل، مما قد يزيد من النفقات العامة لصفحة الموقع بعامل من اثنين أو أكثر.

اتبع الإرشادات أدناه لضمان الاستخدام الأمثل ل iFrames.

- إذا كان ذلك ممكنا، فاستخدم الصور بدلا من iFrames إذا كانت المعاينة صغيرة لتبدأ ب أو غير تفاعلية.
- إذا كان يجب استخدام iFrames، فقم بتصغير الرقم و/أو نقله خارج منفذ العرض.
- الملفات Office مثل Word Excel و PowerPoint تفاعلية، ولكن يتم تحميلها ببطء. غالبا ما يؤدي أداء الصور المصغرة التي بها ارتباط إلى المستند الكامل إلى أداء أفضل.
- تميل مقاطع فيديو YouTube المضمنة ومو موجزات Twitter إلى الأداء بشكل أفضل في iFrames، ولكنها تستخدم هذه الأنواع من التضمينات بعناية.
- أجزاء الويب المعزولة استثناء معقول، ولكن تصغير عددها وموضعها في منفذ العرض.
- إذا كان iFrame موجودا خارج منفذ العرض، ف فكر في استخدام _تقاطعObserver_ لتأخير عرض iFrame حتى يتم عرضه.

قبل إجراء مراجعات للصفحة من أجل حل مشاكل الأداء، دون وقت تحميل الصفحة في نتائج التحليل. قم بتشغيل الأداة مرة أخرى بعد المراجعة لمعرفة ما إذا كانت النتيجة الجديدة ضمن معيار الأساس، وتحقق من وقت تحميل الصفحة الجديدة لمعرفة ما إذا كان هناك أي تحسين.

![نتائج وقت تحميل الصفحة.](../media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
>يمكن أن يختلف وقت تحميل الصفحة استنادا إلى مجموعة متنوعة من العوامل مثل تحميل الشبكة والوقت من اليوم والشروط الأخرى غير المتتية. يجب اختبار وقت تحميل الصفحة بضع مرات قبل إجراء التغييرات وبعدها لمساعدتك على متوسط النتائج.

## <a name="related-topics"></a>المواضيع ذات الصلة

[ضبط SharePoint عبر الإنترنت](tune-sharepoint-online-performance.md)

[ضبط Office 365 الأداء](tune-microsoft-365-performance.md)

[الأداء في تجربة SharePoint الحديثة](/sharepoint/modern-experience-performance)