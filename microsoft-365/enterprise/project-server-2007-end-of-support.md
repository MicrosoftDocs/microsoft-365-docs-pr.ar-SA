---
title: Project نهاية دعم خادم 2007
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 1/31/2018
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
ms.assetid: d379018f-72b7-4284-b40a-6c23c8ae38fe
description: في 10 أكتوبر 2017، انتهى دعم Project Server 2007 و Project Portfolio Server و Project 2007. استخدم هذه المقالة التخطيط للترقية الآن.
ms.openlocfilehash: c492c7154006a139589cff1c768dd77c13804c07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570041"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>Project نهاية دعم خادم 2007

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

انتهى الدعم Office 2007 وتطبيقاته في 2017، وأنت بحاجة إلى التفكير في خطط الترحيل. إذا كنت تستخدم حاليا Project Server 2007 والمنتجات ذات الصلة، فلاحظ تواريخ انتهاء الدعم التالية:
  
|**المنتج**|**تاريخ انتهاء الدعم**|
|:-----|:-----|
|Project Server 2007  <br/> |10 أكتوبر 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 أكتوبر 2017  <br/> |
|Project 2007 Standard  <br/> |10 أكتوبر 2017  <br/> |
|Project 2007 Professional  <br/> |10 أكتوبر 2017  <br/> |
   
لمزيد من المعلومات Office خوادم 2007 التي ستصل إلى التقاعد، راجع الترقية من خوادم [Office 2007 ومنتجات العملاء](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>ما معنى *انتهاء الدعم* ؟

تحتوي معظم منتجات Microsoft على دورة حياة الدعم التي تحصل خلالها على ميزات جديدة وإصلاحات الأخطاء وإصلاحات الأمان وما إلى ذلك. تدوم دورة الحياة هذه عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه ب نهاية دعم المنتج. لأن Project Server 2007 وصل إلى نهاية الدعم في 10 أكتوبر 2017، لم تعد Microsoft توفر:
  
- الدعم التقني للمشاكل التي قد تحدث.
    
- إصلاحات الأخطاء ل المشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.
    
- إصلاحات الأمان لنقاط الضعف التي قد تجعل الخادم عرضة للثغرات الأمنية.
    
- تحديثات المنطقة الزمنية.
    
سيستمر تثبيت Project Server 2007 في العمل بعد هذا التاريخ. ولكن نظرا إلى التغييرات المذكورة سابقا، نوصي بشدة بالترحيل من Project Server 2007 بأسرع وقت ممكن.
  
## <a name="what-are-my-options"></a>ما هي خياراتي؟

إذا كنت تستخدم Project Server 2007، ستحتاج إلى استكشاف خيارات الترحيل، وهي:
  
- الترحيل إلى Project Online
    
- الترحيل إلى إصدار أحدث من خادم Project المحلي (يفضل Project Server 2016)
    
|**لماذا أفضل الترحيل إلى Project Online**|**لماذا أفضل الترحيل إلى Project Server 2016**|
|:-----|:-----|
| لدي مستخدمو الأجهزة المحمولة.  <br/> <br/>تكاليف الترحيل هي مصدر قلق كبير (الأجهزة والبرامج وساعات العمل والجهد لتنفيذها). <br/><br/>  بعد الترحيل، تكون تكاليف الحفاظ على بيئتي مصدر قلق رئيسي (على سبيل المثال، التحديثات التلقائية، ضمان وقت التشغيل، وما إلى ذلك).  <br/> | تقيدني قواعد العمل من تشغيل أعمالي في السحابة.<br/><br/>  أحتاج إلى التحكم في التحديثات التي يتم تحديثها إلى بيئتي.  |
   
> [!NOTE]
> لمزيد من المعلومات حول خيارات الانتقال من خوادم Office 2007، راجع الموارد لمساعدتك على الترقية من [خوادم Office 2007 والعملاء](upgrade-from-office-2007-servers-and-products.md). لاحظ أن Project Server لا يدعم تكوينا مختلطا، Project لا يمكن Project Online الخادم أو الخادم مشاركة تجمع الموارد نفسه. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>اعتبارات مهمة عند الترحيل من Project Server 2007

فكر في ما يلي عندما تخطط للترحيل من Project Server 2007:
  
- **الحصول على المساعدة من أحد شركاء Microsoft** - قد تكون الترقية من Project Server 2007 صعبة وتتطلب الكثير من الإعداد والتخطيط. قد يكون الأمر صعبا بشكل خاص إذا لم تكن الشخص الذي قام بإعداد Project Server 2007 في الأصل. لحسن الحظ، هناك شركاء Microsoft يمكنهم المساعدة، سواء كنت تخطط للترحيل إلى Project Server 2016 أو Project Online. ابحث عن شريك Microsoft لمساعدتك في عملية الترحيل في [مركز شركاء Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). ابحث عن المصطلح *Gold Project وإدارة قائمة* المشاريع لعرض قائمة بجميع شركاء Microsoft الذين لديهم خبرة في Project. 
    
- **التخطيط للتخصيصات** - قد لا تعمل العديد من التخصيصات التي قمت بها في بيئة Project Server 2007 عند الترحيل إلى Project Server 2016 أو Project Online. هناك اختلافات ملحوظة في Project Server بين الإصدارات. تختلف أيضا أنظمة التشغيل المطلوبة، وخادمات قواعد البيانات، ومستعرضات ويب العميل المعتمدة. خطط كيفية اختبار التخصيصات أو إعادة إنشاءها لبيئة جديدة. يوفر التخطيط أيضا فرصة جيدة للنظر في ما إذا كان لا يزال هناك حاجة إلى كل تخصيص. لمزيد من المعلومات، راجع إنشاء [خطة للتخصيصات الحالية أثناء الترقية إلى SharePoint 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **الوقت والصبر** - سيستغرق التخطيط للترقية والتنفيذ والاختبار وقتا وجهدا، خاصة إذا قمت بالترقية إلى Project Server 2016. على سبيل المثال، إذا قمت بالترحيل من Project Server 2007 إلى Project Server 2016، يجب أولا الترحيل إلى Project Server 2010 والتحقق من بياناتك ثم القيام بالشيء نفسه عند الترحيل إلى كل إصدار متتال. قد ترغب في مراجعة الأمر مع شريك Microsoft للحصول على تقديرات حول المدة التي سيستغرقها ذلك وتكلفتها.
    
## <a name="migrate-to-project-online"></a>الترحيل إلى Project Online

إذا اخترت الترحيل من Project Server 2007 إلى Project Online، يمكنك القيام بما يلي لترحيل بيانات خطة المشروع يدويا:
  
1. احفظ خطط المشروع من Project Server 2003 بتنسيق mpp. .
    
2. في Project Professional 2013 أو Project Professional 2016 أو عميل سطح المكتب Project Online، افتح كل ملف .mpp، ثم احفظه ونشره Project Online.
    
يمكنك إنشاء تكوين Microsoft Project Web App (PWA) يدويا في Project Online. على سبيل المثال، إعادة إنشاء أي حقول مخصصة مطلوبة أو تقويمات المؤسسة. يمكن لشركاء Microsoft أيضا المساعدة في هذه العملية.
  
الموارد الأساسية:
  
|**المورد**|**الوصف**|
|:-----|:-----|
|[بدء العمل مع Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |كيفية إعداد Project Online <br/> |
|[Project Online أوصاف الخدمة](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |معلومات حول مختلف Project Online المتوفرة لك <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>الترحيل إلى إصدار أحدث من Project Server

نحن نعتقد اعتقادا قويا أنك تحصل على أفضل قيمة وتجربة مستخدم من خلال عملية Project Online. ولكننا ندرك أيضا أن بعض المؤسسات تحتاج إلى الاحتفاظ بيانات المشروع في بيئة المحلية. إذا اخترت الاحتفاظ بالبيانات المحلية لمشروعك، يمكنك ترحيل بيئة Project Server 2007 إلى Project Server 2010 أو Project Server 2013 أو Project Server 2016.
  
إذا لم تتمكن من الترحيل إلى Project Online، نوصي بالترحيل إلى Project Server 2016. Project Server 2016 كل ميزات الإصدارات السابقة من Project Server. وهو الأكثر تطابقا مع التجربة المتوفرة مع Project Online، على الرغم من أن بعض الميزات متوفرة فقط في Project Online.
  
بعد كل عملية ترحيل، يجب التحقق من ترحيل بياناتك بنجاح.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>كيف يمكنني الترحيل إلى Project Server 2016؟

تمنع الاختلافات Project بين Project Server 2016 Server 2007 وS 2007 مسار ترحيل مباشر. وبالتالي، يجب ترحيل بيانات Project Server 2007 إلى كل إصدار متتابع من Project Server حتى تصل إلى Project Server 2016.
  
اتبع هذه الخطوات Project Server 2016:
  
1. الترحيل من Project Server 2007 إلى Project Server 2010.
    
2. الترحيل من Project Serve 2010 إلى Project Server 2013.
    
3. الترحيل من Project Server 2013 إلى Project Server 2016.
    
بعد كل عملية ترحيل، تأكد من ترحيل بياناتك بنجاح.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>الخطوة 1: الترحيل من Project Server 2007 إلى Project Server 2010

للحصول على وصف شامل لما تحتاج إلى القيام به للترقية من Project Server 2007 إلى Project Server 2010، راجع الترقية إلى [Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
الموارد الأساسية:
  
|**المورد**|**الوصف**|
|:-----|:-----|
|[Project نظرة عامة حول ترقية Server 2010](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |طريقة عرض عالية المستوى لما يجب فعله للترقية من Project Server 2007 إلى Project Server 2010 <br/> |
|[التخطيط للترقية إلى Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |اعتبارات التخطيط عند الترقية من Project Server 2007 إلى Project Server 2010، بما في ذلك متطلبات النظام  <br/> |
   
#### <a name="how-do-i-upgrade"></a>كيف يمكنني الترقية؟

للحصول على التفاصيل، راجع [الترقية إلى Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)). ولكن من المهم أن تدرك أن هناك طريقتين مميزتين يمكنك استخدامهم للترقية:
  
- **ترقية إرفاق قاعدة البيانات:** لا يرقي هذا الأسلوب إلا المحتوى الخاص ببيئة الخاص بك، وليس إعدادات التكوين. يكون مطلوبا إذا كنت تقوم بالترقية من Office Project Server 2007 الذي تم نشره على الأجهزة التي تدعم نظام تشغيل خادم 32 بت فقط. هناك نوعان من أساليب ترقية إرفاق قاعدة البيانات:
    
  - **الترقية الكاملة** لإرفاق قاعدة البيانات - ترحيل بيانات المشروع المخزنة في قواعد بيانات Office Project Server 2007، بالإضافة إلى بيانات موقع Microsoft Project Web App المخزنة في قاعدة بيانات محتوى SharePoint ويب.
    
  - **الترقية الأساسية *لإرفاق قاعدة*** البيانات - ترحيل بيانات المشروع المخزنة في قواعد بيانات Project Server فقط.
    
- **الترقية المكينة**: تتم ترقية بيانات التكوين للمزرعة وكل المحتويات الموجودة في المزرعة على الأجهزة الموجودة في ترتيب ثابت. عند بدء عملية الترقية، يأخذ الإعداد المزرعة بأكملها دون اتصال. لا تتوفر مواقع الويب Microsoft Project مواقع ويب App حتى تنتهي الترقية، ثم يعيد الإعداد تشغيل الخادم. بعد بدء الترقية في مكانها، لا يمكنك إيقاف الترقية مؤقتا أو العودة إلى الإصدار السابق. من الأفضل عمل صورة معكوسة لبيئة الإنتاج الخاصة بك والترقية في مكانها إلى هذه البيئة، وليس في بيئة الإنتاج. 
    
موارد إضافية:
  
- [SuperFlow لترقية Microsoft Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [الترحيل من Project Server 2007 إلى Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [اعتبارات الترقية Project Web App أجزاء ويب](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project أدوات تطوير البرامج (SDK)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>الخطوة 2: الترحيل إلى Project Server 2013

بعد التحقق من ترحيل بياناتك بنجاح، تكون الخطوة التالية هي الترحيل إلى Project Server 2013.
  
للحصول على وصف شامل لما يجب فعله للترقية من Project Server 2010 إلى Project Server 2013، راجع الترقية إلى [Project Server 2013](/project/upgrade-to-project-server-2016). 
  
الموارد الأساسية:
  
|**المورد**|**الوصف**|
|:-----|:-----|
|[نظرة عامة على عملية ترقية Project Server 2013](/project/upgrade-to-project-server-2016) <br/> |نظرة عامة على ما يجب فعله للترقية من Project Server 2010 إلى Project Server 2013  <br/> |
|[التخطيط للترقية إلى Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |اعتبارات التخطيط عند الترقية من Project Server 2010 إلى Project Server 2013، بما في ذلك متطلبات النظام <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>أشياء يجب معرفتها حول الترقية إلى هذا الإصدار

[ما الجديد في ترقية Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) يصف التغييرات المهمة للترقية لهذا الإصدار. وأهمها ما يلي: 
  
- لا توجد ترقية في مكان Project Server 2013. أسلوب إرفاق قاعدة البيانات هو الأسلوب الوحيد المعتمد للترقية من Project Server 2010 إلى Project Server 2013.
    
- لن تقوم عملية الترقية بتحويل بيانات Project Server 2010 إلى تنسيق Project Server 2013 فحسب، بل ستدمج أيضا قواعد بيانات Project Server 2010 الأربع في قاعدة بيانات Project Web App واحدة.
    
- في إصدارات 2013، SharePoint الخادم Project الخادم إلى مصادقة مستندة إلى المطالبات. إذا كنت تستخدم المصادقة الكلاسيكية، يجب عليك التفكير في هذا العامل للترقية. لمزيد من المعلومات، راجع [الترحيل من الوضع الكلاسيكي إلى المصادقة المستندة إلى المطالبات في SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
موارد إضافية:
  
- [نظرة عامة حول عملية الترقية إلى Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [ترقية قواعد البيانات Project Web App المواقع (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [Microsoft Project رسم تخطيطي لعملية ترقية الخادم](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [دمج قاعدة البيانات الرائع Project ترحيل الخادم 2010 إلى 2013 في 8 خطوات سهلة](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>الخطوة 3: الترحيل إلى Project Server 2016

بعد التحقق من ترحيل البيانات بنجاح، تكون الخطوة التالية هي الترحيل إلى Project Server 2016.
  
للحصول على وصف شامل لما تحتاج إلى القيام به للترقية من Project Server 2013 إلى Project Server 2016، راجع الترقية [إلى Project Server 2016](//project/upgrading-to-project-server-2016).
  
الموارد الأساسية:
  
|**المورد**|**الوصف**|
|:-----|:-----|
|[نظرة عامة على Project Server 2016 الترقية](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |نظرة عامة حول ما يجب فعله للترقية من Project Server 2013 إلى Project Server 2016 <br/> |
|[التخطيط للترقية إلى Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |اعتبارات التخطيط التي تقوم بالترقية من Project Server 2013 إلى Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>أشياء يجب معرفتها حول الترقية إلى هذا الإصدار

[تخبرك الأشياء التي تحتاج إلى معرفتها Project Server 2016 الترقية](/project/plan-for-upgrade-to-project-server-2016) ببعض التغييرات المهمة للترقية لهذا الإصدار، والتي تتضمن:
  
- عند إنشاء بيئة Project Server 2016 التي لترحيل بيانات Project Server 2013، يتم تضمين ملفات تثبيت Project Server 2016 في SharePoint Server 2016. لمزيد من المعلومات، راجع [نشر Project Server 2016](/project/deploy-project-server-2016).
    
- يتم إهمال خطط الموارد في Project Server 2016. سيتم Project خطط موارد خادم 2013 إلى "مشاركة الموارد" في Project Server 2016 وفي Project Online. راجع [نظرة عامة: تفاعلات الموارد](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) للحصول على مزيد من المعلومات. 
    
## <a name="migrate-from-portfolio-server-2007"></a>الترحيل من Portfolio Server 2007

Project استخدام Portfolio Server 2007 مع Project Server 2007 لاستراتيجية قائمة المشاريع وتحديد الأولويات والتحسين. لم يتم إنشاء Project إضافية من "خادم حافظة المشاريع" بعد هذا الإصدار. ومع ذلك، تتوفر ميزات إدارة Project Server 2016 في Premium من Project Online. ولكن لا يمكن ترحيل Project Portfolio Server 2007 إلى أي منهما. يجب إعادة إنشاء بيانات مثل برامج تشغيل الأعمال.
  
الموارد الأخرى:
  
- [Project Online أوصاف الخدمة:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) راجع ميزات إدارة المشاريع المضمنة مع Project Server 2016 Project Online Premium.
    
- [Microsoft Office Project ترحيل Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>المواضيع ذات الصلة

[SharePoint نهاية دعم خادم 2007](sharepoint-2007-end-of-support.md)
  
[موارد لمساعدتك على الترقية من Office عملاء وخادمات 2007](upgrade-from-office-2007-servers-and-products.md)
