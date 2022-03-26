---
title: الترقية من SharePoint 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: sharepoint-server-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: ابحث عن المعلومات والموارد للترقية من SharePoint Server 2013 SharePoint Foundation 2013. دعم كلا الطرفين في 11 أبريل 2023.
ms.openlocfilehash: 05f545b67d60d6bcc45587049e49a5f5c1f6d654
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/10/2021
ms.locfileid: "63575916"
---
# <a name="upgrading-from-sharepoint-2013"></a>الترقية من SharePoint 2013

سيبلغ كل من microsoft SharePoint Server 2013 SharePoint Foundation 2013 نهاية الدعم في **11 أبريل 2023**. توفر هذه المقالة موارد لمساعدتك على ترحيل بيانات SharePoint Server الحالية إلى SharePoint Online في Microsoft 365 أو ترقية بيئة SharePoint 2013. بالنسبة لبقية هذه المقالة، سنستخدم SharePoint 2013 للإشارة إلى كل من SharePoint Server 2013 SharePoint Foundation 2013.

## <a name="what-is-end-of-support"></a>ما هو *انتهاء الدعم*؟

تحتوي معظم منتجات Microsoft على دورة حياة الدعم، حيث تحصل خلالها على ميزات جديدة وت تصحيحات الأخطاء وإصلاحات الأمان وما إلى ذلك. بعد انتهاء تاريخ الدعم، لا يتوقف المنتج عن العمل، ولكن لم تعد Microsoft توفر:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء ل المشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان لنقاط الضعف التي قد تجعل الخادم عرضة للثغرات الأمنية.

- تحديثات المنطقة الزمنية.

وهذا يعني أنه لن يتم إجراء أي تحديثات أو تصحيحات أو إصلاحات للمنتج (بما في ذلك تصحيحات/إصلاحات الأمان). سيبدل دعم Microsoft جهود الدعم بشكل كامل إلى الإصدارات الأحدث.

> [!NOTE]
> تدوم دورة حياة البرنامج عادة لمدة خمس سنوات من الدعم الرئيسي من الإصدار الأولي، ومن المحتمل أن تصل إلى 5 سنوات إضافية من الدعم الموسع. [يمكن لموفري حلول Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) مساعدتك على الترقية إلى الإصدار التالي من البرنامج أو الترحيل إلى Microsoft 365 (أو كليهما). تأكد من أنك على دراية بمواعيد انتهاء الدعم للتقنيات الأساسية الهامة أيضا، خاصة بالنسبة إلى إصدار Microsoft SQL Server الذي تستخدمه مع SharePoint. لمزيد من المعلومات، راجع [نهج دورة الحياة الثابتة](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>التخطيط للمستقبل

تحقق من التواريخ التي ينتهي دعمها على موقع دورة حياة المنتج SharePoint [Server 2013](/lifecycle/products/sharepoint-server-2013) [SharePoint Foundation 2013](/lifecycle/products/sharepoint-foundation-2013). خطط للترقية أو الترحيل مع وضع هذه التواريخ في الاعتبار. تذكر أن *منتجك لن يتوقف عن العمل* في التاريخ المدرج. ولكن بما أنه لن يتم تصحيح التثبيت بعد ذلك التاريخ، فسوف تحتاج إلى التخطيط لانتقال سلس إلى الإصدار التالي من المنتج. يسرد الجدول أدناه الخيارات المتوفرة لك.

|منتج انتهاء الدعم|جيد|أفضل|الأفضل|
|---|---|---|---|
|SharePoint Server 2013<BR>SharePoint Foundation 2013|الترقية إلى SharePoint Server 2016 أو 2019|الترقية إلى SharePoint اشتراك الخادم|الترحيل إلى SharePoint في Microsoft 365

## <a name="whats-next"></a>ماذا بعد ذلك؟

نوصي بالحلول SharePoint في Microsoft 365 للاستفادة من أحدث حلول التعاون والذكاء والأمان في Microsoft 365. تم تصميم ميزات التجربة الحديثة في Microsoft 365 بحيث تكون جذابة ومرنة وأداء.

إذا كنت بحاجة إلى الاحتفاظ بنشر SharePoint، نوصي بنشر مختلط يمكنك من ترحيل أكبر قدر ممكن من وظائف SharePoint قدر SharePoint في Microsoft 365. راجع [SharePoint المختلط للتعرف](/sharepoint/hybrid/hybrid) على تنفيذ مختلط وخطط له.

### <a name="migrate-to-sharepoint-in-microsoft-365"></a>الترحيل إلى SharePoint في Microsoft 365

يمكنك استخدام أداة SharePoint الترحيل (SPMT) لترحيل المواقع والمحتوى إلى SharePoint في Microsoft 365. لدينا مكتبة واسعة من المحتويات التي يمكن أن تساعدك على التخطيط للمستقبل، تنفيذ الترحيل، استكشاف الأخطاء التي قد تواجهها وإصلاحها. [نظرة عامة SharePoint أداة الترحيل](/sharepointmigration/introducing-the-sharepoint-migration-tool) هي مكان جيد للبدء.

### <a name="upgrade-to-sharepoint-server-subscription-edition"></a>الترقية إلى SharePoint اشتراك الخادم

على الرغم من عدم وجود مسار مباشر للترقية من SharePoint 2013 إلى إصدار الاشتراك، لا يزال هذا هو الخيار الثاني الأفضل. السبب الأساسي هو أن SharePoint اشتراك Server Edition يقدم نموذج تحديث مستمر يلغي الحاجة إلى إصدار إصدارات رئيسية جديدة من SharePoint Server في المستقبل.

للترقية إلى إصدار الاشتراك، يجب تشغيل SharePoint Server 2016 أو 2019. نظرا لأنه لا يوجد أيضا مسار مباشر من SharePoint 2013 إلى 2019 أيضا، فإن الخيار الأفضل هو الترقية إلى 2016 أولا ثم الترقية إلى إصدار الاشتراك. راجع الارتباطات أدناه لمعرفة المزيد حول الترقية إلى إصدار الاشتراك وخطط لها:

- [الترقية إلى SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [الترقية إلى SharePoint اشتراك الخادم](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-subscription-edition)

حتى لو كنت بحاجة إلى الاحتفاظ بنشر SharePoint المحلي، نوصي بترحيل أجزاء من مواقعك أو محتوياتك إلى Microsoft 365 باستخدام تطبيق [SharePoint](/sharepoint/hybrid/hybrid) المختلط لبدء الاستفادة من تجارب التعاون الحديثة وميزات الأمان والتوافق في Microsoft 365.  

### <a name="upgrade-to-sharepoint-server-2016-or-2019"></a>الترقية إلى SharePoint Server 2016 أو 2019

كل من SharePoint Server 2016 و2019 هي الأنظمة الأساسية المعتمدة إذا كنت تخطط للاحتفاظ بنشر SharePoint في الموقع بعد انتهاء الدعم لعام 2013. ومع ذلك **، سيبلغ كلا الإصدارين نهاية الدعم في 14 يوليو 2026**. وهذا يعني أنك ستحتاج إلى التخطيط لترقية أخرى في غضون 3 سنوات بعد انتهاء تاريخ الدعم لعام 2013. فيما يلي صفحات دورة حياة الدعم لكلا المنتجين:

- [SharePoint دعم الخادم 2016 لتواريخ دورة الحياة](/lifecycle/products/sharepoint-server-2016)
- [SharePoint Server 2019 تواريخ دورة حياة الدعم](/lifecycle/products/sharepoint-server-2019)

لمعرفة المزيد وخطط للترقية، راجع المقالات التالية:

- [الترقية إلى SharePoint Server 2016](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
- [الترقية إلى SharePoint Server 2019](/sharepoint/upgrade-and-update/upgrade-to-sharepoint-server-2019)

حتى لو كنت بحاجة إلى الاحتفاظ بنشر SharePoint المحلي، نوصي بترحيل أجزاء من مواقعك أو محتوياتك إلى Microsoft 365 باستخدام تطبيق [SharePoint](/sharepoint/hybrid/hybrid) المختلط لبدء الاستفادة من تجارب التعاون الحديثة وميزات الأمان والتوافق في Microsoft 365.  
