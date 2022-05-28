---
title: مخطط نهاية دعم SharePoint Server 2007
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 01/28/2019
audience: ITPro
ms.topic: conceptual
f1.keywords:
- CSH
ms.custom:
- vsemail
- MS_WSS_DirectoryManagement
- MS_WSS_ConfigEmail
- globalemailconfig
- configssc
- AppDefToBDC
- seo-marvel-apr2020
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- OFU120
- SPS150
- OSU140
- WSU120
- OSR120
- SPO160
- PJW120
- SPB160
- OSI150
- OSI160
- BSA160
- OSU160
ms.assetid: ba124775-d5c0-4d68-b88d-8458ad4c3717
description: انتهى دعم SharePoint Server 2007 في أكتوبر 2017. في هذه المقالة، تعرف على خيارات الترقية والترحيل والدعم.
ms.openlocfilehash: 7f98e3652e2836a0c4193efbe33147fd09ced01e
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/28/2022
ms.locfileid: "65771942"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>مخطط نهاية دعم SharePoint Server 2007

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

في **10 أكتوبر 2017**، وصل Microsoft Office SharePoint Server 2007 إلى نهاية الدعم. إذا لم تكن قد قمت بالترحيل من SharePoint Server 2007 إلى Microsoft 365 أو إصدار أحدث من SharePoint Server المحلي، فهذا هو الوقت المناسب لبدء التخطيط. توفر هذه المقالة موارد لمساعدتك في ترحيل البيانات إلى SharePoint Online أو ترقية خادم SharePoint المحلي.
  
## <a name="what-does-end-of-support-mean"></a>ماذا يعني *نهاية الدعم* ؟

يحتوي SharePoint Server، مثل معظم منتجات Microsoft، على دورة حياة الدعم، حيث توفر Microsoft ميزات جديدة وتصحيحات الأخطاء وتصحيحات الأمان وما إلى ذلك. تستمر دورة الحياة هذه عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه بانتهاء دعم المنتج. بعد انتهاء الدعم، لم تعد Microsoft توفر:
  
- الدعم التقني للمشاكل التي قد تحدث.
    
- إصلاحات الأخطاء للمشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.
    
- إصلاحات الأمان للثغرات الأمنية التي قد تجعل الخادم عرضة للخروقات الأمنية.
    
- تحديثات المنطقة الزمنية.
    
ستظل مزرعة SharePoint Server 2007 قيد التشغيل بعد 10 أكتوبر 2017، ولكن لن يتم إصدار أي تحديثات أو تصحيحات أو إصلاحات للمنتج، بما في ذلك تصحيحات/إصلاحات الأمان. قام دعم Microsoft بتحويل جهود الدعم بالكامل إلى الإصدارات الأحدث من المنتج. نظرا إلى أن التثبيت لم يعد مدعوما أو مصححا، يجب ترقية المنتج أو ترحيل البيانات المهمة.
  
> [!TIP]
> إذا لم تكن قد خططت بالفعل للترقية أو الترحيل، فراجع: [SharePoint خيارات الترحيل 2007 التي يجب أخذها في الاعتبار](sharepoint-2007-migration-options.md) لبعض الأمثلة حول مكان البدء. يمكنك أيضا البحث عن [شركاء Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) الذين يمكنهم المساعدة في الترقية أو Microsoft 365 الترحيل (أو كليهما).
  
لمزيد من المعلومات حول خوادم Office 2007 ونهاية الدعم، راجع ["الموارد" لمساعدتك على الترقية من Office خوادم وعملاء 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>ما هي خياراتي؟

يجب أن تكون المحطة الأولى [هي موقع دورة حياة المنتج](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). إذا كان لديك منتج Microsoft محلي قديم، فتحقق من تاريخ انتهاء الدعم بحيث يكون لديك سنة أو نحو ذلك لجدولة ترقية أو ترحيل. عند اختيار الخطوة التالية، ضع في اعتبارك ميزات المنتج التي ستكون جيدة بما فيه الكفاية وأفضل وأفضل. فيما يلي مثال على ذلك: 
  
|**جيده**|**افضل**|**افضل**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint مختلط  <br/> |SharePoint Server 2016  <br/> |
| | |SharePoint مختلط  <br/> |
   
إذا اخترت الخيار "جيد بما فيه الكفاية"، فستحتاج قريبا إلى بدء التخطيط لترقية أخرى بعد اكتمال الترحيل من SharePoint Server 2007. 

>[!NOTE] 
>تخضع تواريخ نهاية الدعم للتغيير. تحقق من [موقع دورة حياة المنتج](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>أين يمكنني الانتقال بعد ذلك؟

يمكن تثبيت SharePoint Server محليا على الخوادم الخاصة بك. أو يمكنك استخدام SharePoint Online، وهي خدمة عبر الإنترنت تشكل جزءا من Microsoft 365. خياراتك هي:
  
- ترحيل إلى SharePoint Online.
    
- ترقية SharePoint Server المحلي.
    
- قم بكليهما أعلاه.
    
- تنفيذ حل [مختلط SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
    
كن على دراية بالتكاليف المخفية المرتبطة بصيانة مزرعة خوادم، وصيانة التخصيصات أو ترحيلها، وترقية الأجهزة التي يحتاجها SharePoint Server. يعد وجود مزرعة SharePoint Server محلية أمرا مجزيا إذا لزم الأمر. ولكن إذا قمت بتشغيل المزرعة على خوادم SharePoint القديمة دون تخصيص كبير، يمكنك الاستفادة من الترحيل إلى SharePoint Online.
  
> [!IMPORTANT]
> هناك خيار آخر إذا كان المحتوى في SharePoint 2007 غير مستخدم بشكل متكرر. يختار بعض مسؤولي SharePoint إنشاء اشتراك Microsoft 365، وإعداد موقع SharePoint Online جديد، ثم القص عن SharePoint 2007 بشكل نظيف، مع نقل المستندات الأساسية فقط إلى مواقع SharePoint Online الجديدة. يمكن بعد ذلك استنفاد البيانات من موقع SharePoint 2007 إلى الأرشيفات. ضع في اعتبارك كيفية عمل المستخدمين مع البيانات من تثبيت SharePoint 2007. قد تكون هناك طرق إبداعية لإدارة احتياجاتك.
  
|**SharePoint Online (SPO)**|**SharePoint Server المحلي**|
|:-----|:-----|
|تكلفة عالية في الوقت (خطة / تنفيذ /التحقق)  <br/> |تكلفة عالية في الوقت (خطة / تنفيذ /التحقق)  <br/> |
|انخفاض التكلفة في الأموال (بدون شراء الأجهزة)  <br/> |تكلفة أعلى في الأموال (الأجهزة + devs/admins)  <br/> |
|التكلفة لمرة واحدة في الترحيل  <br/> |التكلفة المتكررة لمرة واحدة لكل ترحيل مستقبلي  <br/> |
|انخفاض التكلفة الإجمالية للملكية/الصيانة  <br/> |التكلفة الإجمالية العالية للتملك/الصيانة  <br/> |
   
عند الترحيل إلى Microsoft 365، ستتكبد عملية النقل لمرة واحدة تكلفة أكبر مقدما، بينما تقوم بتنظيم البيانات وتحديد ما يجب أخذه إلى السحابة وما يجب تركه خلفك. ولكن الترقيات المستقبلية ستكون تلقائية، ولن تحتاج بعد الآن إلى إدارة تحديثات الأجهزة والبرامج. علاوة على ذلك، سيتم دعم وقت إعداد المزرعة بواسطة اتفاقية مستوى خدمة Microsoft ([SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)).
  
### <a name="migrate-to-sharepoint-online"></a>الترحيل إلى SharePoint Online

تأكد من أن SharePoint Online يحتوي على جميع الميزات التي تحتاج إليها. راجع [Microsoft 365 وأوصاف الخدمة Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
لا يمكنك الترحيل مباشرة من SharePoint 2007 إلى SharePoint Online. سيتم نقلك إلى SharePoint Online يدويا. إذا قمت بالترقية إلى SharePoint Server 2013 أو SharePoint Server 2016، فقد تستخدم واجهة برمجة تطبيقات ترحيل SharePoint (لترحيل المعلومات إلى OneDrive for Business، على سبيل المثال).
  
|**محترف عبر الإنترنت**|**con عبر الإنترنت**|
|:-----|:-----|
|توفر Microsoft أجهزة SPO وجميع إدارة الأجهزة.  <br/> |قد تختلف الميزات المتوفرة بين SharePoint Server المحلي وSPO.  <br/> |
|أنت المسؤول SharePoint أو المسؤول العام لاشتراكك ويمكنك تعيين المسؤولين إلى مواقع SPO.  <br/> |بعض الإجراءات المتوفرة لمسؤول مزرعة في SharePoint Server المحلي غير موجودة أو غير مضمنة بالضرورة في دور مسؤول SharePoint في Microsoft 365.  <br/> |
|تطبق Microsoft التصحيحات والإصلاحات والتحديثات على الأجهزة والبرامج الأساسية. <br/> |نظرا لعدم وجود وصول إلى نظام الملفات الأساسي في الخدمة، فإن التخصيص محدود.  <br/> |
|تنشر Microsoft [اتفاقيات مستوى الخدمة](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) وتتحرك بسرعة لحل الحوادث على مستوى الخدمة. <br/> |يتم أتمتة النسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى بواسطة الخدمة في SharePoint Online. تتم الكتابة فوق النسخ الاحتياطية إذا لم يتم استخدامها. <br/> |
|يتم إجراء اختبار الأمان وضبط أداء الخادم على أساس مستمر في الخدمة بواسطة Microsoft. <br/> |يتم تثبيت التغييرات على واجهة المستخدم وميزات SharePoint الأخرى بواسطة الخدمة وقد تحتاج إلى تشغيلها أو إيقاف تشغيلها. <br/> |
|Microsoft 365 تفي بالعديد من معايير الصناعة: [عروض الامتثال من Microsoft](/compliance/regulatory/offering-home).  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) المساعدة في الترحيل محدودة.  <br/> سيكون جزء كبير من الترقية يدويا أو عبر واجهة برمجة تطبيقات ترحيل SPO الموضحة في [SharePoint Online وخريطة طريق محتوى ترحيل OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|لن يكون لدى مهندسي دعم Microsoft وموظفي مركز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك. <br/> |قد تكون هناك تكاليف إضافية إذا كانت هناك حاجة إلى ترقية الأجهزة لدعم الإصدار الأحدث من SharePoint، أو إذا كانت هناك حاجة إلى مزرعة ثانوية للترقية.  <br/> |
|يمكن للشركاء المساعدة في مهمة ترحيل البيانات لمرة واحدة إلى SharePoint Online.  <br/> ||
|يتم تحديث المنتجات عبر الإنترنت تلقائيا. على الرغم من أن الميزات قد تإهمال، لا توجد نهاية حقيقية للدعم. <br/> ||
   
إذا قررت إنشاء موقع Microsoft 365 جديد وستقوم بترحيل البيانات إليه يدويا حسب الحاجة، فتحقق من [خيارات Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint Server المحلي

لا توجد طريقة لتخطي الإصدارات في SharePoint الترقيات. يتم إجراء الترقيات بشكل تسلسلي:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
للانتقال من SharePoint 2007 إلى SharePoint Server 2016 يعني استثمارا كبيرا في الوقت وسيشمل تكاليف في الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج والإدارة. يجب ترقية التخصيصات أو التخلي عنها.
  
> [!NOTE]
> من الممكن الحفاظ على نهاية العمر الافتراضي SharePoint مزرعة 2007، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث تعمل المزارع المنفصلة جنبا إلى جنب)، ثم تخطيط وتنفيذ ترحيل يدوي للمحتوى (لتنزيل المحتوى وإعادة تحميله، على سبيل المثال). ولكن احذر من بعض مزالق عمليات النقل اليدوية، مثل عمليات نقل المستندات التي تستبدل آخر حساب تم تعديله باسم مستعار للحساب الذي يقوم بالنقل اليدوي. ضع في اعتبارك أيضا العمل الذي يجب القيام به مسبقا، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنيات القوائم. ضع في اعتبارك مسبقا البيانات التي يمكنك نقلها إلى التخزين أو الحذف لتقليل تأثير الترحيل.
  
من المهم تنظيف بيئتك قبل الترقية. تأكد من أن المزرعة الحالية تعمل قبل الترقية، و بالتأكيد قبل إيقاف تشغيلها!
  
تذكر مراجعة *مسارات الترقية المعتمدة وغير المعتمدة*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
إذا كان لديك تخصيصات، فمن المهم أن يكون لديك خطة لكل خطوة في مسار الترحيل: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**محترف محلي**|**con المحلي**|
|:-----|:-----|
|التحكم الكامل في جميع جوانب SharePoint Farm، من أجهزة الخادم.  <br/> |تقع مسؤولية جميع الفواصل والإصلاحات على عاتق شركتك (يمكنك المشاركة في دعم Microsoft المدفوع إذا لم يكن منتجك قد تجاوز نهاية الدعم).  <br/> |
|مجموعة ميزات كاملة من SharePoint Server المحلي مع خيار توصيل المزرعة المحلية باشتراك SharePoint Online عبر مختلط.  <br/> |الترقية والتصحيحات وتصحيحات الأمان وجميع صيانة SharePoint Server المدارة محليا.  <br/> |
|الوصول الكامل لمزيد من التخصيص.  <br/> |يجب تكوين [عروض التوافق من Microsoft](/compliance/regulatory/offering-home) يدويا محليا.  <br/> |
|يتم إجراء اختبار الأمان وضبط أداء الخادم في أماكن عملك (تحت سيطرتك).  <br/> |قد توفر Microsoft 365 ميزات SharePoint Online التي لا تعمل بشكل تفاعلي مع SharePoint Server المحلي.  <br/> |
|يمكن للشركاء المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).  <br/> |لن تستخدم مواقع SharePoint Server شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو موضح في SharePoint Online.  <br/> |
|التحكم الكامل في اصطلاحات التسمية والنسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى في SharePoint Server المحلي.  <br/> |SharePoint الخادم المحلي حساس لدورات حياة المنتج.  <br/> |
   
### <a name="upgrade-resources"></a>ترقية الموارد

تأكد من أن بيئتك تلبي متطلبات الأجهزة والبرامج، ثم اتبع أساليب الترقية المدعومة.
  
- **متطلبات الأجهزة/البرامج من أجل**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **حدود البرامج وحدودها ل**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **نظرة عامة على عملية الترقية من أجل**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>إنشاء حل مختلط SharePoint بين SharePoint Online وin-premises

إذا كانت الإجابة على احتياجات الترحيل الخاصة بك في مكان ما بين التحكم الذاتي الذي يقدمه المحلي وخفض تكلفة الملكية التي تقدمها SharePoint Online، يمكنك توصيل SharePoint مزرعة Server 2013 أو 2016 SharePoint Online من خلال المختلطة. [تعرف على SharePoint الحلول المختلطة](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
إذا قررت أن مزرعة خوادم SharePoint المختلطة ستستفيد من عملك، فتعرف على الأنواع المختلطة الموجودة وكيفية تكوين الاتصال بين مزرعة SharePoint المحلية واشتراكك في Microsoft 365.
  
| الخيار | الوصف |
|:-----|:-----|
[عروض التوافق مع Microsoft](/compliance/regulatory/offering-home)  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) المساعدة في الترحيل محدودة.  <br/> سيكون جزء كبير من الترقية يدويا، أو عبر واجهة برمجة تطبيقات ترحيل SPO الموضحة في [SharePoint Online وخريطة طريق محتوى الترحيل OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|لا يتوفر لدى مهندسي دعم Microsoft وموظفي مركز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك.<br/> |يمكن أن تكون هناك تكاليف إضافية إذا كانت البنية الأساسية للأجهزة تحتاج إلى ترقية لدعم الإصدار الأحدث من SharePoint، أو إذا كانت هناك حاجة إلى مزرعة ثانوية للترقية.  <br/> |
|يمكن للشركاء المساعدة في مهمة ترحيل البيانات لمرة واحدة إلى SharePoint Online.  <br/> ||
|يتم تحديث المنتجات عبر الإنترنت تلقائيا عبر الخدمة. على الرغم من أن الميزات قد تإهمال، فلا توجد نهاية حقيقية للدعم.<br/> ||
   
إذا قررت إنشاء موقع Microsoft 365 جديد وستقوم بترحيل البيانات إليه يدويا حسب الحاجة، فتحقق من [خيارات Microsoft 365](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint Server المحلي

لا توجد طريقة لتخطي الإصدارات في SharePoint الترقيات. يتم إجراء الترقيات بشكل تسلسلي:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
للانتقال من SharePoint 2007 إلى SharePoint Server 2016 سيعني استثمارا كبيرا في الوقت وسيتطلب تكاليف الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج والإدارة. يجب ترقية التخصيصات أو التخلي عنها.
  
> [!NOTE]
> من الممكن الحفاظ على نهاية العمر الافتراضي SharePoint مزرعة 2007، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث تعمل المزارع المنفصلة جنبا إلى جنب)، ثم تخطيط وتنفيذ ترحيل يدوي للمحتوى (لتنزيل المحتوى وإعادة تحميله، على سبيل المثال). ولكن احذر من المخاطر المحتملة للحركات اليدوية، مثل عمليات نقل المستندات التي تحل محل الحساب الذي تم تعديله أخيرا باسم مستعار للحساب الذي يقوم بالنقل اليدوي، والعمل الذي يجب القيام به مسبقا، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنيات القوائم. ضع في اعتبارك البيانات التي يمكنك نقلها إلى التخزين أو حذفها لتقليل تأثير الترحيل.
  
قم بتنظيف البيئة قبل الترقية. تأكد من أن المزرعة الحالية تعمل قبل الترقية وتأكد من إيقاف تشغيلها! 
  
تذكر مراجعة *مسارات الترقية المعتمدة وغير المعتمدة*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
إذا كان لديك *تخصيصات*، فمن المهم أن يكون لديك خطة للترقية لكل خطوة في مسار الترحيل: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**Pro المحلية**|**Con المحلي**|
|:-----|:-----|
|التحكم الكامل في جميع جوانب SharePoint Farm، من أجهزة الخادم.  <br/> |جميع الفواصل والإصلاحات هي مسؤولية شركتك. (يمكنك المشاركة في دعم Microsoft المدفوع إذا لم يكن منتجك قد تجاوز نهاية الدعم.)  <br/> |
|مجموعة ميزات كاملة من SharePoint Server المحلي مع خيار توصيل المزرعة المحلية باشتراك SharePoint Online عبر مختلط.  <br/> |الترقية والتصحيحات وتصحيحات الأمان وجميع صيانة SharePoint Server المدارة محليا.  <br/> |
|الوصول الكامل لمزيد من التخصيص.  <br/> |يجب تكوين [عروض التوافق من Microsoft](/compliance/regulatory/offering-home) يدويا محليا.  <br/> |
|يتم إجراء اختبار الأمان وضبط أداء الخادم في أماكن عملك تحت سيطرتك.  <br/> |قد تجعل Microsoft 365 الميزات متوفرة ل SharePoint Online التي لا تعمل بشكل تفاعلي مع SharePoint Server المحلي  <br/> |
|يمكن للشركاء المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).  <br/> |لن تستخدم مواقع SharePoint Server شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو موضح في SharePoint Online.  <br/> |
|التحكم الكامل في اصطلاحات التسمية والنسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى في SharePoint Server المحلي.  <br/> |SharePoint الخادم المحلي حساس لدورات حياة المنتج.  <br/> |
   
### <a name="upgrade-resources"></a>ترقية الموارد

تأكد من أن بيئتك تلبي متطلبات الأجهزة والبرامج. ثم اتبع أساليب الترقية المعتمدة.
  
- **متطلبات الأجهزة/البرامج من أجل:** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **حدود البرامج وحدودها ل:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **نظرة عامة على عملية الترقية من أجل:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>إنشاء حل مختلط SharePoint بين SharePoint Online وin-premises

إذا كانت الإجابة على احتياجات الترحيل الخاصة بك في مكان ما بين التحكم الذاتي الذي يقدمه المحلي وخفض تكلفة الملكية التي تقدمها SharePoint Online، يمكنك توصيل SharePoint مزرعة Server 2013 أو 2016 SharePoint Online من خلال المختلطة. [تعرف على الحلول المختلطة SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
إذا قررت أن مزرعة خوادم SharePoint المختلطة ستستفيد من عملك، فتعرف على الأنواع المختلطة الموجودة وكيفية تكوين الاتصال بين مزرعة SharePoint المحلية واشتراكك في Microsoft 365.
  
إحدى الطرق الجيدة لمعرفة كيفية عمل ذلك هي إنشاء بيئة تطوير/اختبار Microsoft 365، والتي يمكنك إعدادها باستخدام [Test Lab Guides](m365-enterprise-test-lab-guides.md). بعد الحصول على اشتراك تجريبي أو شراء Microsoft 365، يمكنك إنشاء مجموعات المواقع المشتركة والشبكات ومكتبات المستندات في SharePoint Online التي يمكنك ترحيل البيانات إليها. يمكنك الترحيل يدويا، باستخدام واجهة برمجة تطبيقات الترحيل، أو، إذا كنت تريد ترحيل محتوى "الموقع الخاص بي" إلى OneDrive for Business، من خلال المعالج المختلط.
  
> [!NOTE]
> تذكر أنه لاستخدام الخيار المختلط، ستحتاج مزرعة SharePoint 2007 إلى الترقية، محليا، إلى SharePoint Server 2013 أو SharePoint Server 2016.
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[استكشاف أخطاء الترقية واستئنافها (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[استكشاف مشكلات الترقية وإصلاحها (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[استكشاف مشاكل ترقية قاعدة البيانات وإصلاحها في SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[البحث عن شركاء Microsoft للمساعدة في الترقية](https://go.microsoft.com/fwlink/?linkid=841249)
  
[موارد لمساعدتك على الترقية من خوادم وعملاء Office 2007](upgrade-from-office-2007-servers-and-products.md)
