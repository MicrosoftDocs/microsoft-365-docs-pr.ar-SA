---
title: Project نهاية الدعم ل Server 2010
ms.author: efrene
author: efrene
manager: pamg
ms.date: 04/14/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: IT_ProjectAdmin
search.appverid:
- MET150
- ZPJ120
- PJU120
- PJW120
description: ينتهي الدعم Project Server 2010 في 13 أبريل 2021. استخدم هذه المقالة كدليل للترقية إلى Project Online أو إصدار أحدث من Project Server في الموقع.
ms.openlocfilehash: 9d04df22af0a0614270907f4ad4026324b026211
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575352"
---
# <a name="project-server-2010-end-of-support-roadmap"></a>Project نهاية دعم خادم 2010

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

Project إلى نهاية الدعم في **13 أبريل 2021**. تم تمديد هذا التاريخ من تاريخ انتهاء الدعم السابق في 13 أكتوبر 2020. إذا كنت تستخدم حاليا Project Server 2010، فلاحظ أن هذه المنتجات ذات الصلة لها تواريخ انتهاء الدعم التالية:

|المنتج |تاريخ انتهاء الدعم|
|---|---|
|Project القياسي 2010|13 أكتوبر 2020|
|Project 2010 Professional|13 أكتوبر 2020|

لمزيد من المعلومات حول الوصول إلى نهاية الدعم، راجع الترقية من [Office 2010 ومنتجات العملاء](plan-upgrade-previous-versions-office.md).

## <a name="what-does-end-of-support-mean"></a>ما معنى *انتهاء الدعم* ؟

تكون دورة حياة كل منتجات Microsoft تقريبا، حيث تحصل خلالها على ميزات جديدة وتصلح الأخطاء وتحديثات الأمان. تدوم دورة الحياة هذه عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه ب نهاية دعم المنتج. بعد Project انتهاء دعم خادم 2010 في 13 أبريل 2021، لن توفر Microsoft ما يلي:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء ل المشاكل التي يتم اكتشافها وقد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان لنقاط الضعف التي يتم اكتشافها وقد تجعل الخادم عرضة للثغرات الأمنية.

- تحديثات المنطقة الزمنية.

سيستمر تثبيت Project Server 2010 في العمل بعد هذا التاريخ. ولكن نظرا إلى التغييرات المذكورة سابقا، نوصي بشدة بالترحيل من Project Server 2010 في أسرع وقت ممكن.

## <a name="what-are-my-options"></a>ما هي خياراتي؟

خيارات الترحيل الخاصة بك هي:

- الترحيل إلى Project Online

- الترحيل إلى إصدار أحدث من Project Server (يفضل Project Server 2019)

فيما يلي المسارين الذي يمكنك اتخاذه لتجنب انتهاء دعم Project Server 2010.

![Project مسارات ترقية Server 2010.](../media/project-server-2010-end-of-support/project-server-2010-end-of-support-timeline.png)

|لماذا أفضل الترحيل إلى Project Server 2019؟|لماذا أفضل الترحيل إلى Project Online؟|
|---|---|
|تقيدني قواعد العمل من تشغيل أعمالي في السحابة.  <br/><br/>  أحتاج إلى التحكم في التحديثات التي يتم تحديثها إلى بيئتي.|لدي مستخدمين جوالين أو مستخدمين بعيدين.<br/><br/>  إن تكاليف ترحيل الخوادم المحليه هي مصدر قلق كبير (الأجهزة والبرامج والوقت والجهد لتنفيذها، وما إلى ذلك).). <br/><br/>  بعد الترحيل، تكون تكاليف الحفاظ على بيئتي مصدر قلق (على سبيل المثال، التحديثات التلقائية، وضمان وقت التشغيل، وما إلى ذلك).|

> [!NOTE]
> لمزيد من المعلومات حول خيارات الترحيل، راجع الموارد لمساعدتك على الترقية من خوادم Office [2010 والعملاء](upgrade-from-office-2010-servers-and-products.md). لاحظ أن Project Server لا يدعم التكوين المختلط لأن Project الخادم Project Online لا يمكنهما مشاركة تجمع الموارد نفسه.

### <a name="what-are-my-options-for-project-client"></a>ما هي خياراتي Project العميل؟

إذا كنت تستخدم Project Professional 2010 أو Project Standard 2010، فالخيارات هي:

- الانتقال إلى إصدار أحدث من Project Professional أو Project Standard
- الانتقال إلى حل عبر الإنترنت، مثل Project Online أو Project ويب

#### <a name="move-to-a-newer-version-of-project-client"></a>الانتقال إلى إصدار أحدث من عميل Project

إذا كنت تقوم بانقل من Project Standard 2010، يمكنك الانتقال إلى إصدار أحدث من Project Standard (Project Standard 2016 أو Project Standard 2019). نوصيك بالنقل إلى الإصدار الأحدث للاستفادة من أحدث الميزات. يعني الترحيل إلى إصدار أقل Project Standard 2016 أيضا أنك ستحتاج إلى الترحيل مرة أخرى في وقت أقرب.

وبالمثل، إذا كنت تقوم باستراج Project Professional 2010، يمكنك الانتقال إلى إصدار أحدث (Project Professional 2019 أو Project Professional 2016). مرة أخرى، انتقل إلى الإصدار الأحدث إذا أمكن. إذا كنت Project Professional للاتصال ب Project Server، فتأكد من الترحيل إلى إصدار من Project Professional يتصل مع إصدار Project Server الذي تستخدمه.

Project Professional يمكن لمستخدمي 2010 أيضا الترحيل إلى Project Online لسطح المكتب، وهو إصدار مستند إلى الاشتراك من Project Professional 2019. وهي مضمنة في Project (النظام 3) Project (النظام 5) اشتراكات.

#### <a name="move-to-an-online-solution"></a>الانتقال إلى حل عبر الإنترنت

يمكنك أيضا الترحيل من Project Professional 2010 أو Project Standard 2010 إلى Project مستند إلى الاشتراك عبر الإنترنت. تتضمن Project (النظام 3) "Project Online" والعرض السحابي الأخير Project [الويب](https://support.office.com/article/what-can-you-do-with-project-for-the-web-b30f5442-be5f-43d2-9072-c95bff778ea1). يقدم كلاهما ميزات وفوائد جديدة تستحق الاستكشاف.

لمزيد من المعلومات حول الميزات والتراخيص، راجع وصف Microsoft Project [الخدمة](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

## <a name="important-considerations-for-migrating-from-project-server-2010"></a>اعتبارات مهمة لرقم Project Server 2010

فكر في ما يلي عندما تخطط للترحيل من Project Server 2010:

- **الحصول على المساعدة من موفر حلول Microsoft** - قد تكون الترقية من Project Server 2010 تحديا. يتطلب الكثير من الإعداد والتخطيط. قد يكون الأمر صعبا على وجه الخصوص إذا لم تكن الشخص الذي قام بإعداد Project Server 2010. يتوفر موفرو حلول Microsoft للمساعدة، سواء كنت تخطط للترحيل إلى Project Server 2019 أو Project Online. ابحث عن موفر حل في [مركز موفر حلول Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249).

- **التخطيط للتخصيصات** - قد لا تعمل التخصيصات في بيئة Project Server 2010 عند الترحيل إلى Project Server 2019 أو Project Online. هناك اختلافات ملحوظة في Project Server بين الإصدارات. كذلك، تختلف أنظمة التشغيل المطلوبة، وخادمات قواعد البيانات، ومستعرضات الويب التي تعمل مع الإصدارات. لديك خطة حول كيفية اختبار التخصيصات أو إعادة إنشاءها في البيئة الجديدة. اغتنم هذه الفرصة لتحديد ما إذا كانت هناك حاجة إلى تخصيصات معينة. لمزيد من المعلومات، راجع إنشاء [خطة للتخصيصات الحالية أثناء الترقية إلى SharePoint 2013](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013).

- **الوقت والصبر** - سيستغرق التخطيط للترقية والتنفيذ والاختبار الكثير من الوقت والجهد، خاصة للترقية إلى Project Server 2019. إذا كنت تقوم بالترحيل من Project Server 2010 إلى Project Server 2019، فيجب أولا الترحيل إلى Project Server 2013 والتحقق من بياناتك ثم الترحيل إلى Project Server 2016 ثم إلى Project Server 2019. قد ترغب في مراجعة موفر حلول Microsoft للحصول على إطار زمني وتكلفة مقدرة لمساعدته.

## <a name="migrate-to-project-online"></a>الترحيل إلى Project Online

إذا اخترت الترحيل من Project Server 2010 إلى Project Online، يمكنك اتباع هذه الخطوات لترحيل بيانات خطة المشروع يدويا:

1. احفظ خطط المشروع من Project Server 2010 بتنسيق .mpp.

2. باستخدام Project Professional 2016 أو Project Professional 2019 أو عميل سطح المكتب Project Online، افتح كل ملف .mpp، ثم احفظه ونشره Project Online.

يمكنك إنشاء تكوين PWA يدويا في Project Online (على سبيل المثال، إعادة إنشاء أي حقول مخصصة مطلوبة أو تقويمات المؤسسة). يمكن لموفري حلول Microsoft أيضا المساعدة في هذه العملية.

الموارد الأساسية:

|المورد|الوصف|
|---|---|
|[بدء العمل مع Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11)|كيفية إعداد Project Online|
|[Project Online وصف الخدمة](/office365/servicedescriptions/project-online-service-description/project-online-service-description)|معلومات حول الخطط Project Online المتوفرة|

## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>الترحيل إلى إصدار أحدث من Project Server

نحن نعتقد اعتقادا قويا أنك تحصل على أفضل قيمة وتجربة مستخدم من خلال عملية Project Online. ولكننا نفهم أيضا أن بعض المؤسسات تحتاج إلى الاحتفاظ بيانات المشروع في الموقع. إذا اخترت الاحتفاظ بالبيانات المحلية لمشروعك، يمكنك ترحيل بيئة Project Server 2010 إلى Project Server 2013 أو Project Server 2016 أو Project Server 2019.

إذا لم تتمكن من الترحيل إلى Project Online، نوصي بالترحيل إلى Project Server 2019. Project Server 2019 معظم الميزات الأساسية في الإصدارات السابقة من Project Server. وهو الأكثر تطابقا مع التجربة المتوفرة مع Project Online، على الرغم من أن بعض الميزات متوفرة فقط في Project Online.

بعد إكمال كل عملية ترحيل، تأكد من ترحيل بياناتك بنجاح.

> [!NOTE]
> إذا كنت مقتصرا على حل موقعي وتدرس فقط عملية Project Server 2013، فاحذر من أن هذا الإصدار لا يتبقى سوى بضع سنوات أخرى من الدعم. نهاية تاريخ الدعم ل Project Server 2013 مع حزمة الخدمة 2 أكتوبر 13، 2023. لمزيد من المعلومات حول تواريخ انتهاء الدعم، راجع [نهج دورة حياة منتج Microsoft](/lifecycle/).

### <a name="how-do-i-migrate-to-project-server-2019"></a>كيف يمكنني الترحيل إلى Project Server 2019؟

تمنع الاختلافات الهندسية Project Server 2010 Project Server 2019 مسار ترحيل مباشر. لذلك ستحتاج إلى ترحيل بيانات Project Server 2010 إلى كل إصدار متتال من Project Server حتى تصل إلى Project Server 2019. خطوات ترقية Project Server 2010 إلى Project Server 2019:

1. الترحيل إلى Project Server 2013.

2. الترحيل من Project الخدمة 2013 إلى Project Server 2016.

3. الترحيل من Project Server 2016 إلى Project Server 2019.

بعد إكمال كل عملية ترحيل، تأكد من ترحيل بياناتك بنجاح.

### <a name="step-1-migrate-to-project-server-2013"></a>الخطوة 1: الترحيل إلى Project Server 2013

للحصول على معلومات شاملة حول الترقية من Project Server 2010 إلى Project Server 2013، راجع الترقية إلى [Project Server 2013](/project/upgrade-to-project-server-2016).

الموارد الأساسية:

- [نظرة عامة على عملية ترقية Project Server 2013](/project/upgrade-to-project-server-2016)

  احصل على نظرة عامة عالية المستوى حول كيفية الترقية من Project Server 2010 إلى Project Server 2013.
- [التخطيط للترقية إلى Project Server 2013](/project/plan-for-upgrade-to-project-server-2016)

  ألق نظرة على اعتبارات التخطيط عند الترقية من Project Server 2010 إلى Project Server 2013، بما في ذلك متطلبات النظام.

- [ما الجديد في ترقية Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) يغطي التغييرات المهمة لهذا الإصدار، بما في ذلك:

  - لا توجد ترقية في مكان Project Server 2013. أسلوب إرفاق قاعدة البيانات هو الطريقة الوحيدة المعتمدة للترقية من Project Server 2010 إلى Project Server 2013.

  - لن تقوم عملية الترقية بتحويل بيانات Project Server 2010 إلى تنسيق Project Server 2013 فحسب، بل ستدمج أيضا قواعد بيانات Project Server 2010 الأربع في قاعدة بيانات Project Web App واحدة.

  - تم SharePoint كل من Project Server 2013 و Server 2013 إلى مصادقة مستندة إلى المطالبات من الإصدار السابق. إذا كنت تستخدم المصادقة الكلاسيكية، ستحتاج إلى التفكير في ذلك عند الترقية. لمزيد من المعلومات، راجع [الترحيل من الوضع الكلاسيكي إلى المصادقة المستندة إلى المطالبات في SharePoint 2013](/sharepoint/upgrade-and-update/migrate-from-classic-mode-to-claims-based-authentication-in-sharepoint-2013).

الموارد الأساسية:

- [نظرة عامة حول عملية الترقية إلى Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)

- [ترقية قواعد البيانات Project Web App المواقع (Project Server 2013)](/project/upgrading-to-project-server-2016)

- [Microsoft Project رسم تخطيطي لعملية ترقية الخادم](https://go.microsoft.com/fwlink/p/?linkid=841270)

- [دمج قاعدة البيانات الرائع Project ترحيل الخادم 2010 إلى 2013 في 8 خطوات سهلة](https://go.microsoft.com/fwlink/p/?linkid=841271)

### <a name="step-2-migrate-to-project-server-2016"></a>الخطوة 2: الترحيل إلى Project Server 2016

بعد الانتقال إلى Project Server 2013 والتحقق من ترحيل بياناتك بنجاح، فإن الخطوة التالية هي الترحيل إلى Project Server 2016.

لمزيد من المعلومات، راجع [الترقية إلى Project Server 2016](/Project/upgrade-to-project-server-2016).

الموارد الأساسية:

- [نظرة عامة على Project Server 2016 الترقية](/Project/overview-of-the-project-server-2016-upgrade-process)

  تعرف على ما يجب فعله للترقية من Project Server 2013 إلى Project Server 2016.

- [التخطيط للترقية إلى Project Server 2016](/Project/plan-for-upgrade-to-project-server-2016)

  ألق نظرة على اعتبارات التخطيط التي يجب اتخاذها عند الترقية من Project Server 2013 إلى Project Server 2016.

[تغطي الأمور التي تحتاج إلى معرفتها Project Server 2016 الترقية](/project/plan-for-upgrade-to-project-server-2016#thingknow) التغييرات المهمة للترقية إلى هذا الإصدار، والتي تتضمن:

- عند إنشاء بيئة Project Server 2016، لاحظ أن Project Server 2016 تثبيت الملفات مضمنة في SharePoint Server 2016. لمزيد من المعلومات، راجع [نشر Project Server 2016](/project/deploy-project-server-2016).

- يتم إهمال خطط الموارد في Project Server 2016. سيتم Project خطط موارد خادم 2013 إلى "مشاركة الموارد" في Project Server 2016 وفي Project Online. راجع [نظرة عامة: تفاعلات الموارد](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) للحصول على مزيد من المعلومات.

### <a name="step-3-migrate-to-project-server-2019"></a>الخطوة 3: الترحيل إلى Project Server 2019

بعد الترحيل إلى Project Server 2016 التحقق من ترحيل بياناتك بنجاح، فإن الخطوة التالية هي ترحيل البيانات إلى Project Server 2019.

لمعرفة ما يجب فعله للترقية من Project Server 2016 إلى Project Server 2019، راجع الترقية إلى [Project Server 2019](/Project/upgrade-to-project-server-2016).

الموارد الأساسية:

- [نظرة عامة حول عملية ترقية Project Server 2019](/project/overview-of-the-project-server-2019-upgrade-process)

  احصل على فهم عال المستوى لما تحتاج إلى القيام به للترقية من Project Server 2013 إلى Project Server 2016.

- [التخطيط للترقية إلى Project Server 2019](/project/plan-for-upgrade-to-project-server-2019)

  ألق نظرة على اعتبارات التخطيط للترقية من Project Server 2016 إلى Project Server 2019.

- [الأمور التي تحتاج إلى معرفتها حول Project Server 2019](/project/plan-for-upgrade-to-project-server-2016)<br/><br/>تعرف على التغييرات المهمة للترقية إلى هذا الإصدار، والتي تتضمن:

  - لترحيل البيانات من قاعدة بيانات Project Server 2016 البيانات إلى SharePoint Server 2019 بيانات المحتوى.  Project Server 2019 إنشاء قاعدة بيانات خادم Project الخاصة به في SharePoint Server.

  - بعد الترقية، كن على علم بعدة تغييرات في Project Web App.  للحصول على التفاصيل، راجع [ما الجديد في Project Server 2019](/project/what-s-new-for-it-pros-in-project-server-2019#PWAChanges).

**الموارد الأخرى**:

- [Project Online أوصاف الخدمة](/office365/servicedescriptions/project-online-service-description/project-online-service-description): راجع ميزات إدارة المشاريع المضمنة مع Project Server 2016 Project Online Premium.

- [Microsoft Office Project ترحيل Portfolio Server 2010](https://go.microsoft.com/fwlink/p/?linkid=841279)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>ملخص خيارات Office 2010 والعميل Windows 7

للحصول على ملخص مرئي حول خيارات الترقية والترحيل والانتقال إلى السحابة لعملاء Office 2010 وخادم Windows 7، راجع نهاية ملصق [الدعم](../downloads/Office2010Windows7EndOfSupport.pdf).

[![انتهاء الدعم لعملاء Office 2010 وملصقات Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

يوضح هذا الملصق المسارات المختلفة التي يمكنك اتخاذها لتجنب إنهاء الدعم لمنتجات عميل Office 2010 وخادم Windows 7، مع تمييز المسارات المفضلة ودعم الخيارات في Microsoft 365 Enterprise.

يمكنك أيضا تنزيل [هذا](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) الملصق وطباعته بتنسيق حرف أو قانوني أو جدولي (11 × 17).

## <a name="related-topics"></a>المواضيع ذات الصلة

[الترقية من SharePoint 2010](upgrade-from-sharepoint-2010.md)

[الترقية من Office عملاء وخادمات 2010](upgrade-from-office-2010-servers-and-products.md)
