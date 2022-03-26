---
title: SharePoint نهاية دعم خادم 2007
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
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
description: انتهى دعم SharePoint Server 2007 في أكتوبر 2017. في هذه المقالة، تعرف على خيارات الترقية وا الترحيل والدعم.
ms.openlocfilehash: d09e0cf58ef814a76cdac28f6029189eaf655efc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572879"
---
# <a name="sharepoint-server-2007-end-of-support-roadmap"></a>SharePoint نهاية دعم خادم 2007

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

في **10 أكتوبر 2017**، Microsoft Office SharePoint انتهاء الدعم في Server 2007. إذا لم تقم بالترحيل من SharePoint Server 2007 إلى Microsoft 365 أو إصدار أحدث من SharePoint Server المحلي، حان الوقت لبدء التخطيط. توفر هذه المقالة موارد لمساعدتك على ترحيل البيانات إلى SharePoint عبر الإنترنت أو ترقية SharePoint الخادم المحلية.
  
## <a name="what-does-end-of-support-mean"></a>ما معنى *انتهاء الدعم* ؟

SharePoint، مثل معظم منتجات Microsoft، دورة حياة الدعم، حيث توفر Microsoft خلالها ميزات جديدة وتصلح الأخطاء وإصلاحات الأمان وما إلى ذلك. تدوم دورة الحياة هذه عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه ب نهاية دعم المنتج. بعد انتهاء الدعم، لم تعد Microsoft توفر:
  
- الدعم التقني للمشاكل التي قد تحدث.
    
- إصلاحات الأخطاء ل المشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.
    
- إصلاحات الأمان لنقاط الضعف التي قد تجعل الخادم عرضة للثغرات الأمنية.
    
- تحديثات المنطقة الزمنية.
    
ستبقى مزرعة SharePoint Server 2007 الخاصة بك قيد التشغيل بعد 10 أكتوبر 2017، ولكن لن يتم إصدار أي تحديثات أو تصحيحات أو إصلاحات أخرى للمنتج، بما في ذلك تصحيحات/إصلاحات الأمان. نقل دعم Microsoft جهود الدعم بشكل كامل إلى الإصدارات الأحدث من المنتج. نظرا لأن التثبيت لم يعد مدعوما أو مصححا، يجب ترقية المنتج أو ترحيل البيانات المهمة.
  
> [!TIP]
> إذا لم تكن قد خططت مسبقا للترقية أو الترحيل، فشاهد: SharePoint [ترحيل 2007](sharepoint-2007-migration-options.md) التي يجب التفكير فيها لبعض الأمثلة حول مكان البدء. يمكنك أيضا البحث عن [شركاء Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) الذين يمكنهم المساعدة في الترقية أو Microsoft 365 الترحيل (أو كليهما).
  
لمزيد من المعلومات حول Office 2007 ونهاية الدعم، راجع الموارد لمساعدتك على الترقية من [خوادم Office 2007 والعملاء](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-are-my-options"></a>ما هي خياراتي؟

يجب أن تكون أول محطة لك هي موقع [دورة حياة المنتج](/lifecycle/products/?alpha=Microsoft+Office+SharePoint+Server+2007). إذا كان لديك منتج Microsoft المحلي الذي يعمر، فتحقق من تاريخ انتهاء الدعم بحيث يكون لديك سنة أو نحو ذلك لجدولة ترقية أو ترحيل. عندما تختار الخطوة التالية، فكر في ميزات المنتج التي ستكون جيدة بما يكفي وأفضل. فيما يلي مثال على ذلك: 
  
|**جيد**|**أفضل**|**الأفضل**|
|:-----|:-----|:-----|
|SharePoint Server 2010  <br/> |SharePoint Server 2013  <br/> |SharePoint Online  <br/> |
||SharePoint المختلط  <br/> |SharePoint Server 2016  <br/> |
| | |SharePoint المختلط  <br/> |
   
إذا اخترت خيار "جيد بما فيه الكفاية"، ستحتاج قريبا إلى بدء التخطيط لترقية أخرى بعد إكمال عملية الترحيل من SharePoint Server 2007. 

>[!NOTE] 
>تخضع تواريخ انتهاء الدعم للتغيير. تحقق من [موقع دورة حياة المنتج](https://support.microsoft.com/lifecycle).
  
## <a name="where-can-i-go-next"></a>أين يمكنني الانتقال بعد ذلك؟

SharePoint أن يكون الخادم مثبتا على خوادمك الخاصة. أو يمكنك استخدام SharePoint Online، وهي خدمة عبر الإنترنت تكون جزءا من Microsoft 365. الخيارات الخاصة بك هي:
  
- الترحيل إلى SharePoint Online.
    
- ترقية SharePoint الخادم في الموقع.
    
- القيام بكلا الأمرين أعلاه.
    
- تنفيذ حل [SharePoint المختلط](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
    
كن على دراية بالتكاليف المخفية المقترنة بصيانة مزرعة خوادم، والحفاظ على التخصيصات أو اخفاؤها، وترقية الأجهزة التي SharePoint الخادم. إن امتلاك مزرعة خادم SharePoint يكون مجزية إذا كان ذلك ضروريا. ولكن إذا قمت بتشغيل المزرعة على خوادم SharePoint دون تخصيص كثيف، يمكنك الاستفادة من الترحيل إلى SharePoint Online.
  
> [!IMPORTANT]
> هناك خيار آخر إذا كان المحتوى في SharePoint 2007 غير مستخدم بشكل غير معتاد. يختار بعض مسؤولي SharePoint إنشاء اشتراك Microsoft 365، إعداد موقع SharePoint Online جديد، ثم قطعه عن SharePoint 2007 بشكل نظيف، مع أخذ المستندات الضرورية فقط إلى مواقع SharePoint عبر الإنترنت. يمكن عندئذ استنزاف البيانات من موقع SharePoint 2007 إلى الأرشيفات. فكر في كيفية عمل المستخدمين مع البيانات من تثبيت SharePoint 2007. قد تكون هناك طرق إبداعية لإدارة احتياجاتك.
  
|**SharePoint Online (SPO)**|**SharePoint الخادم في الموقع**|
|:-----|:-----|
|تكلفة عالية في الوقت (خطة / تنفيذ/التحقق)  <br/> |تكلفة عالية في الوقت (خطة / تنفيذ/التحقق)  <br/> |
|تكلفة أقل في عمليات التمويل (بدون شراء أجهزة)  <br/> |تكلفة أعلى في الأموال (الأجهزة + devs/admins)  <br/> |
|التكلفة مرة واحدة في عملية الترحيل  <br/> |التكلفة المتكررة مرة واحدة لكل عملية ترحيل مستقبلية  <br/> |
|التكلفة الإجمالية المنخفضة للملكية/الصيانة  <br/> |التكلفة الإجمالية العالية للملكية/الصيانة  <br/> |
   
عند الترحيل إلى Microsoft 365، سيكون للنقل مرة واحدة تكلفة أعلى بشكل أكبر، بينما تقوم بتنظيم البيانات وتقرر ما يجب أخذه إلى السحابة وما يجب تركه خلفك. ولكن ستكون الترقيات المستقبلية تلقائية، ولن تحتاج بعد ذلك إلى إدارة تحديثات الأجهزة والبرامج. كما سيتم أيضا دعم وقت العمل في المزرعة باتفاقية مستوى خدمة Microsoft ([SLA](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)).
  
### <a name="migrate-to-sharepoint-online"></a>الترحيل إلى SharePoint Online

تأكد من أن SharePoint Online لديه كل الميزات التي تحتاج إليها. راجع [Microsoft 365 Office 365 أوصاف الخدمة](/office365/servicedescriptions/office-365-service-descriptions-technet-library).
  
لا يمكنك الترحيل مباشرة من SharePoint 2007 إلى SharePoint Online. سيتم نقلك إلى SharePoint Online يدويا. إذا قمت بالترقية إلى SharePoint Server 2013 أو SharePoint Server 2016، فقد تستخدم API ترحيل SharePoint (لترحيل المعلومات إلى OneDrive for Business، على سبيل المثال).
  
|**محترف عبر الإنترنت**|**con عبر الإنترنت**|
|:-----|:-----|
|توفر Microsoft أجهزة SPO وإدارة جميع الأجهزة.  <br/> |قد تختلف الميزات المتوفرة بين SharePoint Server في الموقع وSPO.  <br/> |
|أنت مسؤول Sharepoint أو المسؤول العام لاشتراكك، ويمكنك تعيين المسؤولين إلى مواقع SPO.  <br/> |لا توجد بعض الإجراءات المتوفرة لمسؤول المزرعة SharePoint الخادم في الموقع أو لا يتم تضمينها بالضرورة في دور مسؤول SharePoint في Microsoft 365.  <br/> |
|تطبق Microsoft التصحيحات والتصحيحات والتحديثات على الأجهزة والبرامج الأساسية. <br/> |نظرا لعدم إمكانية الوصول إلى نظام الملفات الأساسي في الخدمة، يكون التخصيص محدودا.  <br/> |
|تنشر Microsoft [اتفاقيات مستوى الخدمة](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) وتتحرك بسرعة لحل أحداث مستوى الخدمة. <br/> |يتم إجراء النسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى بشكل تلقائي بواسطة الخدمة في SharePoint Online. يتم الكتابة فوق النسخ الاحتياطية إذا لم يتم استخدامها. <br/> |
|يتم تنفيذ اختبار الأمان وضبط أداء الخادم بشكل مستمر في الخدمة بواسطة Microsoft. <br/> |يتم تثبيت التغييرات التي يتم إدخالها على واجهة المستخدم SharePoint الأخرى بواسطة الخدمة وقد تحتاج إلى تشغيلها أو إيقاف تشغيلها. <br/> |
|Microsoft 365 العديد من معايير الصناعة: عروض [التوافق من Microsoft](/compliance/regulatory/offering-home).  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) المساعدة المقدمة ل الترحيل محدودة.  <br/> سيكون جزء كبير من الترقية يدويا أو عبر API هجرة SPO الموضحة في SharePoint [عبر الإنترنت OneDrive لمحتوى الترحيل](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|لن يكون لدى مهندسي دعم Microsoft وموظفي مراكز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك. <br/> |قد تكون هناك تكاليف إضافية إذا كان من اللازم ترقية الأجهزة لدعم الإصدار الأحدث من SharePoint، أو إذا كانت المزرعة الثانوية مطلوبة للترقية.  <br/> |
|يمكن للشركاء المساعدة في المهمة التي يتم القيام بها مرة واحدة تهجر بياناتك إلى SharePoint عبر الإنترنت.  <br/> ||
|يتم تحديث المنتجات عبر الإنترنت تلقائيا. على الرغم من أن الميزات قد يتم إهمالها، إلا أنه لا يوجد نهاية حقيقية للدعم. <br/> ||
   
إذا قررت إنشاء موقع Microsoft 365 جديد وست ترحيل البيانات إليه يدويا كما هو مطلوب، فتحقق من Microsoft 365 [البيانات](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint الخادم في الموقع

لا توجد طريقة لتخطي الإصدارات في SharePoint الترقيات. يتم إجراء الترقيات بشكل تسلسلي:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
يعني الانتقال من SharePoint 2007 إلى SharePoint Server 2016 استثمارا كبيرا للوقت وسيتضمن تكاليف في الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج والإدارة. يجب ترقية التخصيصات أو التخلي عنها.
  
> [!NOTE]
> من الممكن الحفاظ على مزرعة SharePoint 2007 التي تنتهي حياتها، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث يتم تشغيل المزرعة المنفصلة جنبا إلى جنب)، ثم تخطيط عملية ترحيل المحتوى يدويا وتنفيذها (لتنزيل المحتوى أو إعادة تحميله، على سبيل المثال). ولكن احذر من بعض المخاطر التي قد تفرزها عمليات الانتقال اليدوية، مثل نقل المستندات التي استبدلت الحساب الذي تم تعديله الأخير باسم الحساب المستعار الذي يقوم بالنقل اليدوي. يمكنك أيضا التفكير في العمل الذي يجب إنجازه قبل الوقت المحدد، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنيات القائمة. فكر مسبقا في البيانات التي يمكنك نقلها إلى مساحة التخزين أو الحذف لتقليل تأثير الترحيل.
  
من المهم تنظيف بيئتك قبل الترقية. كن على يقين من أن المزرعة الموجودة تعمل قبل الترقية، وقبل أن تسحبها بالتأكيد!
  
تذكر مراجعة مسارات الترقية المعتمدة *وغير المعتمدة*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
إذا كان لديك تخصيصات، فمن المهم أن يكون لديك خطة لكل خطوة في مسار الترحيل: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**محترف في الموقع**|**con في الموقع**|
|:-----|:-----|
|التحكم الكامل بكل جوانب SharePoint المزرعة، من جهاز الخادم لأعلى.  <br/> |تقع على عاتق شركتك مسؤولية كل فواصل العمل وإصلاحاتها (يمكنك المشاركة في دعم Microsoft مدفوع إذا لم ينهي منتجك بعد انتهاء الدعم).  <br/> |
|مجموعة الميزات الكاملة من SharePoint الخادم في الموقع مع خيار توصيل المزرعة الخاصة بك في موقع SharePoint عبر الإنترنت عبر المختلط.  <br/> |الترقية والتصحيحات وإصلاحات الأمان والصيانة SharePoint الخادم المدارة في الموقع.  <br/> |
|الوصول الكامل لمزيد من التخصيص.  <br/> |[يجب تكوين عروض](/compliance/regulatory/offering-home) التوافق من Microsoft يدويا في الموقع.  <br/> |
|يتم إجراء اختبار الأمان وضبط أداء الخادم في مكانك المحلي (تحت سيطرتك).  <br/> |Microsoft 365 هذه الميزات متوفرة SharePoint Online التي لا يتم تشغيلها مع SharePoint الخادم في الموقع.  <br/> |
|يمكن للشركاء المساعدة في عملية نقل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).  <br/> |لن SharePoint مواقع الخادم استخدام [شهادات SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو مشاهد في SharePoint Online.  <br/> |
|التحكم الكامل في اصطلاحات التسمية، ونقر فوقها واستعادتها، وخيارات الاسترداد الأخرى في SharePoint الخادم في الموقع.  <br/> |SharePoint إلى أن الخادم المحلي يتحسس دورة حياة المنتج.  <br/> |
   
### <a name="upgrade-resources"></a>موارد الترقية

تأكد من أن بيئتك تلبي متطلبات الأجهزة والبرامج، ثم اتبع أساليب الترقية المعتمدة.
  
- **متطلبات الأجهزة/البرامج ل**: 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **حدود البرنامج وحدوده ل**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **نظرة عامة حول عملية الترقية ل**: 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>إنشاء حل SharePoint مختلط بين SharePoint Online وs premises

إذا كانت الإجابة على احتياجات الترحيل في مكان ما بين التحكم الذاتي الذي يقدمه المحلي والتكلفة المنخفضة للملكية التي يقدمها SharePoint Online، يمكنك توصيل مزرعة SharePoint Server 2013 أو 2016 ب SharePoint Online عبر المختلطات. [تعرف على SharePoint المختلطة](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).
  
إذا قررت أن مزرعة SharePoint Server المختلطة ستستفيد منها شركتك، فاطلع على الأنواع الموجودة من المختلطات وكيفية تكوين الاتصال بين مزرعة SharePoint SharePoint واشتراكك Microsoft 365.
  
| الخيار | الوصف |
|:-----|:-----|
[عروض التوافق من Microsoft](/compliance/regulatory/offering-home)  <br/> |[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) المساعدة المقدمة ل الترحيل محدودة.  <br/> سيكون جزء كبير من الترقية يدويا، أو عبر API هجرة SPO الموضحة في SharePoint [عبر الإنترنت OneDrive لمحتوى الترحيل](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).  <br/> |
|لا تتوفر لمهندسي دعم Microsoft وموظفي مركز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك.<br/> |قد تكون هناك تكاليف إضافية إذا كان من اللازم ترقية البنية الأساسية للأجهزة لدعم الإصدار الأحدث من SharePoint، أو إذا كانت المزرعة الثانوية مطلوبة للترقية.  <br/> |
|يمكن للشركاء المساعدة في المهمة التي يتم القيام بها مرة واحدة تهجر بياناتك إلى SharePoint عبر الإنترنت.  <br/> ||
|يتم تحديث المنتجات عبر الإنترنت تلقائيا عبر الخدمة. على الرغم من أن الميزات قد يتم إهمالها، لا يوجد نهاية حقيقية للدعم.<br/> ||
   
إذا قررت إنشاء موقع Microsoft 365 جديد وست ترحيل البيانات إليه يدويا كما هو مطلوب، فتحقق من Microsoft 365 [البيانات](https://www.microsoft.com/microsoft-365/).
  
### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint الخادم في الموقع

لا توجد طريقة لتخطي الإصدارات في SharePoint الترقيات. يتم إجراء الترقيات بشكل تسلسلي:
  
- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016
   
يعني الانتقال من SharePoint 2007 إلى SharePoint Server 2016 استثمارا كبيرا في الوقت وسيتضمن تكاليف الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج والإدارة. يجب ترقية التخصيصات أو التخلي عنها.
  
> [!NOTE]
> من الممكن الحفاظ على مزرعة SharePoint 2007 التي تنتهي حياتها، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث يتم تشغيل المزرعة المنفصلة جنبا إلى جنب)، ثم تخطيط عملية ترحيل المحتوى يدويا وتنفيذها (لتنزيل المحتوى أو إعادة تحميله، على سبيل المثال). ولكن احذر من المخاطر المحتملة للتنقلات اليدوية، مثل نقل المستندات التي استبدلت الحساب الذي تم تعديله الأخير باسم الحساب المستعار الذي يقوم بالنقل اليدوي، والعمل الذي يجب إنجازه قبل الوقت المحدد، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنى القائمة. فكر في البيانات التي يمكنك نقلها إلى مساحة التخزين أو الحذف لتقليل تأثير الترحيل.
  
قم بتنظيف بيئتك قبل الترقية. كن على يقين من أن المزرعة الموجودة تعمل قبل الترقية وقبل أن تسحبها بالتأكيد! 
  
تذكر مراجعة مسارات الترقية المعتمدة *وغير المعتمدة*: 
  
- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)
    
إذا كان *لديك تخصيصات*، فمن المهم أن يكون لديك خطة للترقية لكل خطوة في مسار الترحيل: 
  
- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))
    
- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))
    
- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)
    
|**الفرضيات Pro**|**Con في الموقع**|
|:-----|:-----|
|التحكم الكامل بكل جوانب SharePoint المزرعة، من جهاز الخادم لأعلى.  <br/> |تقع على عاتق شركتك مسؤولية كل الاستراحة والتثواب. (يمكنك المشاركة في دعم Microsoft مدفوع إذا لم ينهي منتجك بعد انتهاء الدعم.)  <br/> |
|مجموعة الميزات الكاملة من SharePoint الخادم في الموقع مع خيار توصيل المزرعة الخاصة بك في موقع SharePoint عبر الإنترنت عبر المختلط.  <br/> |الترقية والتصحيحات وإصلاحات الأمان والصيانة SharePoint الخادم المدارة في الموقع.  <br/> |
|الوصول الكامل لمزيد من التخصيص.  <br/> |[يجب تكوين عروض](/compliance/regulatory/offering-home) التوافق من Microsoft يدويا في الموقع.  <br/> |
|يتم إجراء اختبار الأمان وضبط أداء الخادم في مكانك تحت سيطرتك.  <br/> |Microsoft 365 الميزات المتوفرة SharePoint Online التي لا يتم تشغيلها مع SharePoint Server في الموقع  <br/> |
|يمكن للشركاء المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).  <br/> |لن تستخدم SharePoint الخادم شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو مشاهد في SharePoint Online.  <br/> |
|التحكم الكامل في اصطلاحات التسمية، ونقر فوقها واستعادتها، وخيارات الاسترداد الأخرى في SharePoint الخادم في الموقع.  <br/> |SharePoint إلى أن الخادم المحلي يتحسس دورة حياة المنتج.  <br/> |
   
### <a name="upgrade-resources"></a>موارد الترقية

تأكد من أن بيئتك تلبي متطلبات الأجهزة والبرامج. ثم اتبع أساليب الترقية المعتمدة.
  
- **متطلبات الأجهزة/البرامج ل:** 
    
    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
    
- **حدود البرنامج وحدوده ل:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)
    
- **نظرة عامة حول عملية الترقية ل:** 
    
    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)
    
### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>إنشاء حل SharePoint مختلط بين SharePoint Online وs premises

إذا كانت الإجابة على احتياجات الترحيل في مكان ما بين التحكم الذاتي الذي يقدمه المحلي والتكلفة المنخفضة للملكية التي يقدمها SharePoint Online، يمكنك توصيل مزرعة SharePoint Server 2013 أو 2016 ب SharePoint Online عبر المختلطات. [التعرف على SharePoint المختلطة](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)
  
إذا قررت أن مزرعة SharePoint Server المختلطة ستستفيد منها شركتك، فاطلع على الأنواع الموجودة من المختلطات وكيفية تكوين الاتصال بين مزرعة SharePoint SharePoint واشتراكك Microsoft 365.
  
هناك طريقة جيدة لمعرفة كيفية عمل ذلك وهي إنشاء بيئة Microsoft 365 اختبار/اختبار، يمكنك إعدادها باستخدام ["أدلة اختبار المعمل](m365-enterprise-test-lab-guides.md)". بعد الحصول على اشتراك تجريبي أو Microsoft 365، يمكنك إنشاء مجموعات المواقع والمستندات والويب ومكتبات المستندات في SharePoint عبر الإنترنت حيث يمكنك ترحيل البيانات. يمكنك الترحيل يدويا، باستخدام API للترحيل، أو، إذا كنت تريد ترحيل محتوى الموقع الخاص OneDrive for Business، من خلال المعالج المختلط.
  
> [!NOTE]
> تذكر أنه لاستخدام الخيار المختلط، ستحتاج مزرعة SharePoint 2007 إلى ترقية، على مستوى الموقع، إلى SharePoint Server 2013 أو SharePoint Server 2016.
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[استكشاف الأخطاء وإصلاحها واستئناف الترقية (Office SharePoint Server 2007)](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262967(v=office.12))
  
[استكشاف مشاكل الترقية وإصلاحها (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/cc262967(v=office.14))
  
[استكشاف مشاكل ترقية قاعدة البيانات وإصلاحها في SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)
  
[البحث عن شركاء Microsoft للمساعدة في الترقية](https://go.microsoft.com/fwlink/?linkid=841249)
  
[موارد لمساعدتك على الترقية من Office عملاء وخادمات 2007](upgrade-from-office-2007-servers-and-products.md)
