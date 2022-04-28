---
title: مخطط نهاية دعم Project Server 2007
ms.author: efrene
author: efrene
manager: scotv
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
description: في 10 أكتوبر 2017، انتهى الدعم ل Project Server 2007 Project Portfolio Server و Project 2007. استخدم هذه المقالة للتخطيط للترقية الآن.
ms.openlocfilehash: 1c46a0c422a0eb66b4991589a0996092c40f5fba
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090176"
---
# <a name="project-server-2007-end-of-support-roadmap"></a>مخطط نهاية دعم Project Server 2007

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

انتهى الدعم لخوادم وتطبيقات Office 2007 في عام 2017، وتحتاج إلى النظر في خطط الترحيل. إذا كنت تستخدم حاليا Project Server 2007 والمنتجات ذات الصلة، فلاحظ تواريخ نهاية الدعم التالية:
  
|**المنتج**|**تاريخ انتهاء الدعم**|
|:-----|:-----|
|Project Server 2007  <br/> |10 أكتوبر 2017  <br/> |
|Project Portfolio Server 2007  <br/> |10 أكتوبر 2017  <br/> |
|Project 2007 Standard  <br/> |10 أكتوبر 2017  <br/> |
|Project 2007 Professional  <br/> |10 أكتوبر 2017  <br/> |
   
لمزيد من المعلومات حول Office خوادم 2007 التي وصلت إلى مرحلة التوقف، راجع [الترقية من خوادم Office 2007 ومنتجات العميل](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>ماذا يعني *نهاية الدعم* ؟

تحتوي معظم منتجات Microsoft على دورة حياة دعم تحصل خلالها على ميزات جديدة وتصحيحات الأخطاء وتصحيحات الأمان وما إلى ذلك. تستمر دورة الحياة هذه عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه بانتهاء دعم المنتج. نظرا إلى أن Project Server 2007 وصل إلى نهاية دعمه في 10 أكتوبر 2017، لم تعد Microsoft توفر:
  
- الدعم التقني للمشاكل التي قد تحدث.
    
- إصلاحات الأخطاء للمشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.
    
- إصلاحات الأمان للثغرات الأمنية التي قد تجعل الخادم عرضة للخروقات الأمنية.
    
- تحديثات المنطقة الزمنية.
    
سيستمر تثبيت Project Server 2007 في التشغيل بعد هذا التاريخ. ولكن بسبب التغييرات المذكورة سابقا، نوصي بشدة بالرحل من Project Server 2007 في أقرب وقت عملي.
  
## <a name="what-are-my-options"></a>ما هي خياراتي؟

إذا كنت تستخدم Project Server 2007، فستحتاج إلى استكشاف خيارات الترحيل، وهي:
  
- الترحيل إلى Project Online
    
- الترحيل إلى إصدار محلي أحدث من Project Server (يفضل أن يكون Project Server 2016)
    
|**لماذا أفضل الترحيل إلى Project Online**|**لماذا أفضل الترحيل إلى Project Server 2016**|
|:-----|:-----|
| لدي مستخدمو الأجهزة المحمولة.  <br/> <br/>تشكل تكاليف الترحيل مصدر قلق كبير (الأجهزة والبرامج والساعات والجهد في التنفيذ). <br/><br/>  بعد الترحيل، تشكل تكاليف الحفاظ على بيئتي مصدر قلق كبير (على سبيل المثال، التحديثات التلقائية ووقت التشغيل المضمون وما إلى ذلك).  <br/> | تقيدني قواعد العمل من تشغيل أعمالي في السحابة.<br/><br/>  أحتاج إلى التحكم في تحديثات البيئة الخاصة بي.  |
   
> [!NOTE]
> لمزيد من المعلومات حول خيارات الانتقال من خوادم Office 2007، راجع ["الموارد" لمساعدتك على الترقية من خوادم وعملاء Office 2007](upgrade-from-office-2007-servers-and-products.md). لاحظ أن Project Server لا يدعم التكوين المختلط، لأن Project Server و Project Online لا يمكنهما مشاركة نفس تجمع الموارد. 
  
## <a name="important-considerations-when-you-migrate-from-project-server-2007"></a>الاعتبارات المهمة عند الترحيل من Project Server 2007

ضع في اعتبارك ما يلي عندما تخطط للرحل من Project Server 2007:
  
- **الحصول على المساعدة من شريك Microsoft** - قد تكون الترقية من Project Server 2007 صعبة وتتطلب الكثير من الإعداد والتخطيط. قد يكون من الصعب بشكل خاص إذا لم تكن الشخص الذي قام بإعداد Project Server 2007 في الأصل. لحسن الحظ، هناك شركاء Microsoft يمكنهم المساعدة، سواء كنت تخطط للرحل إلى Project Server 2016 أو Project Online. ابحث عن شريك Microsoft للمساعدة في الترحيل في [مركز شركاء Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841249). ابحث عن مصطلح *Gold Project وإدارة قائمة المشاريع* لعرض قائمة بجميع شركاء Microsoft الذين لديهم خبرة في Project. 
    
- **التخطيط للتخصيصات -** قد لا تعمل العديد من التخصيصات التي أجريتها في بيئة Project Server 2007 عند الترحيل إلى Project Server 2016 أو Project Online. هناك اختلافات كبيرة في بنية Project Server بين الإصدارات. تختلف أيضا أنظمة التشغيل المطلوبة وخوادم قواعد البيانات ومستعرضات ويب العميل المدعومة. خطط لكيفية اختبار التخصيصات أو إعادة بنائها للبيئة الجديدة. كما يوفر التخطيط فرصة جيدة للنظر في ما إذا كانت هناك حاجة إلى كل تخصيص. لمزيد من المعلومات، راجع [إنشاء خطة للتخصيصات الحالية أثناء الترقية إلى SharePoint 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
    
- **الوقت والصبر** - سيستغرق تخطيط الترقية وتنفيذها واختبارها وقتا وجهدا، خاصة إذا قمت بالترقية إلى Project Server 2016. على سبيل المثال، إذا قمت بالترقية من Project Server 2007 إلى Project Server 2016، فستحتاج أولا إلى الترحيل إلى Project Server 2010، والتحقق من بياناتك، ثم القيام بنفس الشيء عند الترحيل إلى كل إصدار متتابع. قد ترغب في التحقق مع شريك Microsoft للحصول على تقديرات للمدة التي سيستغرقها ذلك وما ستتكلفه.
    
## <a name="migrate-to-project-online"></a>الترحيل إلى Project Online

إذا اخترت الترحيل من Project Server 2007 إلى Project Online، يمكنك القيام بما يلي بترحيل بيانات خطة المشروع يدويا:
  
1. احفظ خطط المشروع من تنسيق Project Server 2003 إلى mpp.
    
2. في Project Professional 2013 أو Project Professional 2016 أو عميل سطح المكتب Project Online، افتح كل ملف mpp. ثم احفظه وانشره إلى Project Online.
    
يمكنك إنشاء تكوين Microsoft Project Web App (PWA) يدويا في Project Online. على سبيل المثال، أعد إنشاء أي حقول مخصصة مطلوبة أو تقويمات المؤسسة. يمكن لشركاء Microsoft أيضا المساعدة في هذه العملية.
  
الموارد الرئيسية:
  
|**الموارد**|**الوصف**|
|:-----|:-----|
|[بدء استخدام Project Online](https://support.office.com/article/e3e5f64f-ada5-4f9d-a578-130b2d4e5f11) <br/> |كيفية إعداد Project Online واستخدامها <br/> |
|[أوصاف خدمة Project Online](/office365/servicedescriptions/project-online-service-description/project-online-service-description) <br/> |معلومات حول خطط Project Online المختلفة المتوفرة لك <br/> |
   
## <a name="migrate-to-a-newer-on-premises-version-of-project-server"></a>الترحيل إلى إصدار محلي أحدث من Project Server

نعتقد بشدة أنك تحصل على أفضل قيمة وتجربة مستخدم من خلال الترحيل إلى Project Online. ولكننا نفهم أيضا أن بعض المؤسسات تحتاج إلى الاحتفاظ ببيانات المشروع في بيئة محلية. إذا اخترت الاحتفاظ ببيانات المشروع محليا، فيمكنك ترحيل بيئة Project Server 2007 إلى Project Server 2010 أو Project Server 2013 أو Project Server 2016.
  
إذا تعذر عليك الترحيل إلى Project Online، نوصي بالتهحيل إلى Project Server 2016. يتضمن Project Server 2016 كافة ميزات الإصدارات السابقة من Project Server. وهو الأكثر تطابقا مع التجربة المتوفرة مع Project Online، على الرغم من أن بعض الميزات متوفرة فقط في Project Online.
  
بعد كل عملية ترحيل، يجب التحقق من ترحيل بياناتك بنجاح.
  
> [!NOTE]
>
  
### <a name="how-do-i-migrate-to-project-server-2016"></a>كيف أعمل الترحيل إلى Project Server 2016؟

الاختلافات الهيكلية بين Project Server 2007 و Project Server 2016 تمنع مسار الترحيل المباشر. لذلك يجب ترحيل بيانات Project Server 2007 إلى كل إصدار متتابع من Project Server حتى تصل إلى Project Server 2016.
  
اتبع هذه الخطوات Project Server 2016:
  
1. ترحيل من Project Server 2007 إلى Project Server 2010.
    
2. ترحيل من Project 2010 إلى Project Server 2013.
    
3. ترحيل من Project Server 2013 إلى Project Server 2016.
    
بعد كل عملية ترحيل، تأكد من ترحيل بياناتك بنجاح.
  
### <a name="step-1-migrate-from-project-server-2007-to-project-server-2010"></a>الخطوة 1: الترحيل من Project Server 2007 إلى Project Server 2010

للحصول على وصف شامل لما تحتاج إلى القيام به للترقية من Project Server 2007 إلى Project Server 2010، راجع [الترقية إلى Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)).
  
الموارد الرئيسية:
  
|**الموارد**|**الوصف**|
|:-----|:-----|
|[نظرة عامة على ترقية Project Server 2010](/previous-versions/office/project-server-2010/ee662496(v=office.14)) <br/> |طريقة عرض عالية المستوى لما تحتاج إلى القيام به للترقية من Project Server 2007 إلى Project Server 2010 <br/> |
|[التخطيط للترقية إلى Project Server 2010](/previous-versions/office/project-server-2010/ff603505(v=office.14)) <br/> |اعتبارات التخطيط عند الترقية من Project Server 2007 إلى Project Server 2010، بما في ذلك متطلبات النظام  <br/> |
   
#### <a name="how-do-i-upgrade"></a>كيف أعمل الترقية؟

للحصول على التفاصيل، راجع [الترقية إلى Project Server 2010](/previous-versions/office/project-server-2010/gg502590(v=office.14)). ولكن من المهم أن تفهم أن هناك طريقتين متميزتين يمكنك استخدامهما للترقية:
  
- **ترقية إرفاق قاعدة البيانات:** يقوم هذا الأسلوب فقط بترقية المحتوى للبيئة الخاصة بك، وليس إعدادات التكوين. وهي مطلوبة إذا كنت تقوم بالترقية من Office Project Server 2007 المنشورة على الأجهزة التي تدعم نظام تشغيل خادم 32 بت فقط. هناك نوعان من أساليب ترقية إرفاق قاعدة البيانات:
    
  - ***الترقية الكاملة* لإرفاق قاعدة البيانات** - ترحيل بيانات المشروع المخزنة في قواعد بيانات Office Project Server 2007، بالإضافة إلى بيانات موقع تطبيق ويب Microsoft Project المخزنة في قاعدة بيانات محتوى SharePoint.
    
  - ***ترقية الذاكرة الأساسية* لإرفاق قاعدة البيانات** - ترحيل بيانات المشروع المخزنة في قواعد بيانات خادم Project فقط.
    
- **الترقية الموضعية**: تتم ترقية بيانات التكوين الخاصة بالمزرعة وكافة المحتويات الموجودة في المزرعة على الأجهزة الموجودة بترتيب ثابت. عند بدء عملية الترقية، يأخذ الإعداد المزرعة بأكملها دون اتصال. لا تتوفر مواقع الويب ومواقع Microsoft Project Web App حتى تنتهي الترقية، ثم يعيد الإعداد تشغيل الخادم. بعد بدء الترقية الموضعية، لا يمكنك إيقاف الترقية مؤقتا أو العودة إلى الإصدار السابق. من الأفضل إنشاء صورة معكوسة لبيئة الإنتاج الخاصة بك وإجراء الترقية الموضعية إلى هذه البيئة، وليس في بيئة الإنتاج الخاصة بك. 
    
موارد إضافية:
  
- [SuperFlow لترقية Microsoft Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [الترحيل من Project Server 2007 إلى Project Server 2010](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [اعتبارات الترقية Project Web App أجزاء ويب](/previous-versions/office/project-server-2010/gg314581(v=office.14))
    
- [Project Software Development Kit (SDK)](/previous-versions/office/developer/office-2010/ms481966(v=office.14))
    
### <a name="step-2-migrate-to-project-server-2013"></a>الخطوة 2: الترحيل إلى Project Server 2013

بعد التحقق من ترحيل البيانات بنجاح، تتمثل الخطوة التالية في الترحيل إلى Project Server 2013.
  
للحصول على وصف شامل لما تحتاج إلى القيام به للترقية من Project Server 2010 إلى Project Server 2013، راجع [الترقية إلى Project Server 2013](/project/upgrade-to-project-server-2016). 
  
الموارد الرئيسية:
  
|**الموارد**|**الوصف**|
|:-----|:-----|
|[نظرة عامة على عملية ترقية Project Server 2013](/project/upgrade-to-project-server-2016) <br/> |نظرة عامة على ما تحتاج إلى القيام به للترقية من Project Server 2010 إلى Project Server 2013  <br/> |
|[التخطيط للترقية إلى Project Server 2013](/project/plan-for-upgrade-to-project-server-2016) <br/> |اعتبارات التخطيط عند الترقية من Project Server 2010 إلى Project Server 2013، بما في ذلك متطلبات النظام <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>أشياء يجب معرفتها حول الترقية إلى هذا الإصدار

[ما الجديد في ترقية Project Server 2013](/project/what-s-new-in-project-server-2013-upgrade) يصف التغييرات المهمة للترقية لهذا الإصدار. وأهمها ما يلي: 
  
- لا توجد ترقية موضعية إلى Project Server 2013. أسلوب إرفاق قاعدة البيانات هو الأسلوب الوحيد المعتمد للترقية من Project Server 2010 إلى Project Server 2013.
    
- لن تقوم عملية الترقية بتحويل بيانات Project Server 2010 إلى تنسيق Project Server 2013 فحسب، بل ستقوم أيضا بدمج قواعد البيانات الأربع Project Server 2010 إلى قاعدة بيانات Project Web App واحدة.
    
- في إصدارات 2013، تم تغيير كل من SharePoint Server وخادم Project Server إلى المصادقة المستندة إلى المطالبات. إذا كنت تستخدم المصادقة الكلاسيكية، فستحتاج إلى مراعاة هذا العامل للترقية. لمزيد من المعلومات، راجع [الترحيل من الوضع الكلاسيكي إلى المصادقة المستندة إلى المطالبات في SharePoint 2013](/sharepoint/security-for-sharepoint-server/security-for-sharepoint-server).
    
موارد إضافية:
  
- [نظرة عامة على عملية الترقية إلى Project Server 2013](/project/overview-of-the-project-server-2016-upgrade-process)
    
- [ترقية قواعد البيانات ومجموعات المواقع المشتركة Project Web App (Project Server 2013)](/project/upgrading-to-project-server-2016)
    
- [رسم تخطيطي لعملية ترقية Microsoft Project Server](https://go.microsoft.com/fwlink/p/?linkid=841270)
    
- [دمج قاعدة البيانات الرائعة، ترحيل Project Server 2010 إلى 2013 في 8 خطوات سهلة](https://go.microsoft.com/fwlink/p/?linkid=841271)
    
### <a name="step-3-migrate-to-project-server-2016"></a>الخطوة 3: الترحيل إلى Project Server 2016

بعد التحقق من ترحيل البيانات بنجاح، تتمثل الخطوة التالية في الترحيل إلى Project Server 2016.
  
للحصول على وصف شامل لما تحتاج إلى القيام به للترقية من Project Server 2013 إلى Project Server 2016، راجع [الترقية إلى Project Server 2016](//project/upgrading-to-project-server-2016).
  
الموارد الرئيسية:
  
|**الموارد**|**الوصف**|
|:-----|:-----|
|[نظرة عامة على عملية ترقية Project Server 2016](/previous-versions/office/project-server-2010/ee662104(v=office.14)) <br/> |نظرة عامة على ما تحتاج إلى القيام به للترقية من Project Server 2013 إلى Project Server 2016 <br/> |
|[التخطيط للترقية إلى Project Server 2016](/project/plan-for-upgrade-to-project-server-2016) <br/> |اعتبارات التخطيط التي ترقيتها من Project Server 2013 إلى Project Server 2016 <br/> |
   
#### <a name="things-to-know-about-upgrading-to-this-version"></a>أشياء يجب معرفتها حول الترقية إلى هذا الإصدار

[تخبرك الأشياء التي تحتاج إلى معرفتها حول Project Server 2016 الترقية](/project/plan-for-upgrade-to-project-server-2016) ببعض التغييرات المهمة للترقية لهذا الإصدار، والتي تتضمن:
  
- عند إنشاء بيئة Project Server 2016 التي ستقوم بترحيل بيانات Project Server 2013 إليها، يتم تضمين ملفات تثبيت Project Server 2016 في SharePoint Server 2016. لمزيد من المعلومات، راجع [نشر Project Server 2016](/project/deploy-project-server-2016).
    
- يتم إهمال خطط الموارد في Project Server 2016. سيتم ترحيل خطط موارد Project Server 2013 إلى التفاوض بشأن الموارد في Project Server 2016 وفي Project Online. راجع [النظرة العامة: التفاوض بشأن الموارد](https://support.office.com/article/73eefb5a-81fe-42bf-980e-9532b1bdc870) للحصول على مزيد من المعلومات. 
    
## <a name="migrate-from-portfolio-server-2007"></a>الترحيل من خادم قائمة المشاريع 2007

تم استخدام Project Portfolio Server 2007 مع Project Server 2007 لاستراتيجية قائمة المشاريع وتحديد الأولويات والتحسين. لم يتم إنشاء إصدارات إضافية من Project خادم قائمة المشاريع بعد هذا الإصدار. ومع ذلك، تتوفر ميزات إدارة قائمة المشاريع في Project Server 2016 والإصدار Premium من Project Online. ولكن لا يمكن ترحيل البيانات من Project Portfolio Server 2007 إلى أي منهما. يجب إعادة إنشاء بيانات مثل برامج تشغيل الأعمال.
  
الموارد الأخرى:
  
- [Project Online أوصاف الخدمة:](/office365/servicedescriptions/project-online-service-description/project-online-service-description) راجع ميزات إدارة قائمة المشاريع المضمنة مع Project Server 2016 Project Online Premium.
    
- [دليل ترحيل Microsoft Office Project Portfolio Server 2007.](https://go.microsoft.com/fwlink/p/?linkid=841279)
    
## <a name="related-topics"></a>المواضيع ذات الصلة

[مخطط نهاية دعم SharePoint Server 2007](sharepoint-2007-end-of-support.md)
  
[موارد لمساعدتك على الترقية من خوادم وعملاء Office 2007](upgrade-from-office-2007-servers-and-products.md)
