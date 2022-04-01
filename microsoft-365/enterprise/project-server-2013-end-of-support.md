---
title: Project نهاية الدعم ل Server 2013
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 10/11/2021
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
description: ينتهي الدعم Project Server 2013 في 11 أبريل 2023. استخدم هذه المقالة كدليل للترقية إلى Project Online أو إصدار أحدث من Project Server في الموقع.
ms.openlocfilehash: 5a9ae38e819dfdb8f9cc2ca3719dccea2d33fa3e
ms.sourcegitcommit: 16e3a6e6df253de1153e46d058941cd9a2bbf2b2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/10/2021
ms.locfileid: "63579983"
---
# <a name="project-server-2013-end-of-support-roadmap"></a>Project نهاية دعم خادم 2013

Project إلى نهاية الدعم في **11 أبريل 2023**. إذا كنت تستخدم حاليا Project Server 2013، فلاحظ أن تطبيق سطح المكتب Project 2013 له أيضا تواريخ انتهاء الدعم نفسها.

## <a name="what-does-end-of-support-mean"></a>ما معنى *انتهاء الدعم* ؟

تكون دورة حياة كل منتجات Microsoft تقريبا، حيث تحصل خلالها على ميزات جديدة وتصلح الأخطاء وتحديثات الأمان. تدوم دورة الحياة هذه عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه ب نهاية دعم المنتج. بعد Project انتهاء دعم خادم 2013 في 11 أبريل 2023، لن توفر Microsoft ما يلي:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء ل المشاكل التي يتم اكتشافها وقد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان لنقاط الضعف التي يتم اكتشافها وقد تجعل الخادم عرضة للثغرات الأمنية.

- تحديثات المنطقة الزمنية.

سيستمر تثبيت Project Server 2013 في العمل بعد هذا التاريخ. ولكن نظرا إلى التغييرات المذكورة سابقا، نوصي بشدة بالترحيل من Project Server 2013 في أسرع وقت ممكن.

## <a name="what-are-my-options"></a>ما هي خياراتي؟

خيارات الترحيل الخاصة بك هي:

- الترحيل إلى Project Online

- الترحيل إلى إصدار أحدث من Project Server (يفضل أن يكون Project اشتراك الخادم)

|لماذا أفضل الترحيل إلى Project Server 2019؟|لماذا أفضل الترحيل إلى Project Online؟|
|---|---|
|تقيدني قواعد العمل من تشغيل أعمالي في السحابة.  <br/><br/>  أحتاج إلى التحكم في التحديثات التي يتم تحديثها إلى بيئتي.|لدي مستخدمين جوالين أو مستخدمين بعيدين.<br/><br/>  إن تكاليف ترحيل الخوادم المحليه هي مصدر قلق كبير (الأجهزة والبرامج والوقت والجهد لتنفيذها، وما إلى ذلك).). <br/><br/>  بعد الترحيل، تكون تكاليف الحفاظ على بيئتي مصدر قلق (على سبيل المثال، التحديثات التلقائية، وضمان وقت التشغيل، وما إلى ذلك).|

> [!NOTE]
> Project لا يدعم الخادم التكوين المختلط لأن Project الخادم Project Online لا يمكنهما مشاركة تجمع الموارد نفسه.

## <a name="important-considerations-for-migrating-from-project-server-2013"></a>اعتبارات مهمة لرقم Project Server 2013

فكر في ما يلي عندما تخطط للترحيل من Project Server 2013:

- **الحصول على المساعدة من موفر حلول Microsoft** - قد تكون الترقية من Project Server 2013 تحديا. يتطلب الكثير من الإعداد والتخطيط. قد يكون الأمر صعبا على وجه الخصوص إذا لم تكن الشخص الذي قام بإعداد Project Server 2013. يتوفر موفرو حلول Microsoft للمساعدة، سواء كنت تخطط للترحيل إلى Project اشتراك الخادم أو إلى Project Online. ابحث عن موفر حل في [مركز موفر حلول Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **الوقت والصبر** - سيستغرق التخطيط للترقية والتنفيذ والاختبار الكثير من الوقت والجهد، خاصة للترقية إلى Project اشتراك الخادم. إذا كنت تقوم بالترحيل من Project Server 2013 إلى Project Server Subscription Edition، فيجب أولا الترحيل إلى Project Server 2016 والتحقق من بياناتك ثم Project اشتراك الخادم. قد ترغب في مراجعة موفر حلول Microsoft للحصول على إطار زمني وتكلفة مقدرة لمساعدته.

## <a name="migrate-to-project-online"></a>الترحيل إلى Project Online

إذا اخترت الترحيل من Project Server 2013 إلى Project Online، يمكنك اتباع هذه الخطوات لترحيل بيانات خطة المشروع يدويا:

1. احفظ خطط المشروع من Project Server 2013 بتنسيق mpp. .

2. باستخدام Project Professional 2016 أو Project Professional 2019 أو عميل سطح المكتب Project Online، افتح كل ملف .mpp، ثم احفظه ونشره Project Online.

يمكنك إنشاء تكوين PWA يدويا في Project Online (على سبيل المثال، إعادة إنشاء أي حقول مخصصة مطلوبة أو تقويمات المؤسسة). يمكن لموفري حلول Microsoft أيضا المساعدة في هذه العملية.

الموارد الأساسية:

|المورد|الوصف|
|---|---|
|[بدء العمل مع Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|كيفية إعداد Project Online|
|[Project Online وصف الخدمة](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|معلومات حول الخطط Project Online المتوفرة|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>الترحيل إلى إصدار أحدث من Project Server

نحن نعتقد اعتقادا قويا أنك تحصل على أفضل قيمة وتجربة مستخدم من خلال عملية Project Online. ولكننا نفهم أيضا أن بعض المؤسسات تحتاج إلى الاحتفاظ بيانات المشروع في الموقع. إذا اخترت الاحتفاظ بالبيانات المحلية لمشروعك، يمكنك ترحيل بيئة Project Server 2013 إلى Project Server 2016 أو Project Server 2019 أو Project Server Subscription Edition.

إذا لم تتمكن من الترحيل إلى Project Online، نوصي بالترحيل إلى Project اشتراك الخادم الذي يتضمن معظم الميزات الأساسية في الإصدارات السابقة من Project Server. وهو الأكثر تطابقا مع التجربة المتوفرة مع Project Online، على الرغم من أن بعض الميزات متوفرة فقط في Project Online. العوامل الإضافية التي يجب التفكير فيها هي:

- Project اشتراك Server Edition نموذج تحديث مستمر يلغي الحاجة إلى إصدار إصدارات رئيسية جديدة من Project Server من الآن.
- سينتهي الدعم Project Server 2016 2019 في 14 يوليو 2026. إذا قمت بالترحيل إلى أي من الإصدارين، ستحتاج إلى التخطيط لترقية أخرى في غضون ثلاث سنوات. لمزيد من المعلومات، راجع صفحات دورة حياة الدعم لكل من [2016](/lifecycle/products/project-server-2016) [و2019](/lifecycle/products/project-server-2019).

بعد إكمال كل عملية ترحيل، تأكد من ترحيل بياناتك بنجاح.

### <a name="how-do-i-migrate-to-project-server-subscription-edition"></a>كيف أقوم بالترحيل إلى Project اشتراك الخادم؟

تمنع الاختلافات الهندسية Project Server 2013 Project Server Subscription Edition مسار ترحيل مباشر. لذلك ستحتاج إلى ترحيل بيانات Project Server 2013 أولا Project Server 2016، ثم Project اشتراك الخادم. 

1. الترحيل إلى Project Server 2016.

2. الترحيل من Project Server 2016 إلى Project اشتراك الخادم.

بعد إكمال كل عملية ترحيل، تأكد من ترحيل بياناتك بنجاح.

### <a name="step-1-migrate-to-project-server-2016"></a>الخطوة 1: الترحيل إلى Project Server 2016

للحصول على معلومات شاملة حول الترقية من Project Server 2013 إلى Project Server 2016، راجع الترقية [إلى Project Server 2016](/project/upgrade-to-project-server-2016).

الموارد الأساسية:

- [نظرة عامة Project Server 2016 عملية](/project/upgrade-to-project-server-2016) الترقية: احصل على نظرة عامة عالية المستوى حول كيفية الترقية من Project Server 2013 إلى Project Server 2016.
- [التخطيط للترقية إلى Project Server 2016](/project/plan-for-upgrade-to-project-server-2016): انظر إلى اعتبارات التخطيط عند الترقية من Project Server 2013 إلى Project Server 2016، بما في ذلك متطلبات النظام.
- [الترقية إلى Project Server 2016](/project/upgrading-to-project-server-2016): راجع الإرشادات المفصلة حول عملية الترقية.

### <a name="step-2-migrate-to-project-server-subscription-edition"></a>الخطوة 2: الترحيل إلى Project اشتراك الخادم

بعد الانتقال إلى Project Server 2016 التحقق من ترحيل بياناتك بنجاح، فإن الخطوة التالية هي الترحيل إلى Project اشتراك الخادم.

لمزيد من المعلومات، راجع [الترقية إلى Project اشتراك الخادم](/project/upgrade-project-server-subscription-edition).

الموارد الأساسية:

- [نظرة عامة على Project ترقية إصدار اشتراك الخادم](/project/overview-project-server-subscription-edition-upgrade-process): فهم ما يجب فعله للترقية من Project Server 2013 إلى Project Server 2016.
- [التخطيط للترقية إلى Project اشتراك الخادم](/Project/plan-upgrade-project-server-subscription-edition): انظر إلى اعتبارات التخطيط التي يجب اتخاذها عند الترقية من Project Server 2013 إلى Project Server 2016.
- [الترقية إلى Project اشتراك الخادم:](/project/how-to-upgrade-project-server-subscription-edition) راجع الإرشادات المفصلة حول عملية الترقية.


