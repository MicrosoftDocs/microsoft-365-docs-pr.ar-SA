---
title: نماذج معمارية SharePoint و Exchange و Skype for Business و Lync
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/16/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Ent_Architecture
ms.assetid: 5b49fa68-f8f2-4705-af96-5f5475e8539a
search.appverid:
- MET150
description: احصل على ملصقات ل IT تصف النماذج المعمارية وخيارات النشر و النظام الأساسي SharePoint Exchange Skype for Business وLync.
ms.openlocfilehash: 813a143d281f85e6cbc9c0456dceaf20c674d13b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570009"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>نماذج معمارية SharePoint و Exchange و Skype for Business و Lync

تصف ملصقات IT في هذه المقالة النماذج المعمارية وخيارات النشر SharePoint Exchange Skype for Business وLync. كما أنها توفر معلومات التصميم لنشر SharePoint Microsoft Azure.
  
باستخدام Microsoft 365، يمكنك توفير خدمات الاتصال والتعاون المألوفة عبر السحابة. مع بعض الاستثناءات، تظل تجربة المستخدم هي نفسها سواء كنت تحتفظ بنشر موقعي أو تستخدم Microsoft 365. 

تعقد تجربة المستخدم الموحدة هذه قرار مكان وضع كل حمل عمل. ويطرح أيضا أسئلة:
  
- كيف يمكنك اختيار نظام أساسي لأحمال العمل الفردية؟
    
- هل من المنطقي الاحتفاظ بأي خدمة في الموقع؟
    
- في أي سيناريو يكون التوزيع المختلط مناسبا؟
    
- كيف يتلاءم Azure مع الصورة؟
    
- ما هي تكوينات Office الخادم التي يدعمها Azure؟
    
> [!TIP]
> تتوفر معظم الملصقات في هذه المقالة بلغات متعددة. تتضمن اللغات المتوفرة اللغة الصينية والإنجليزية والفرنسية والألمانية والإيطالية واليابانية والكورية والبرتغالية والروسية والإسبانية. لتنزيل ملصق بوا إحدى هذه اللغات، ضمن الصورة المصغرة للملصق، حدد **المزيد من اللغات**.
  
أعلمنا رأيك! أرسل لنا بريدا إلكترونيا [على cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
استخدم الارتباطات التالية للحصول على الملصقات التي تحتاج إليها:
  
- **النماذج الهندسية**: استخدم هذه الموارد لتحديد النظام الأساسي المثالي وتكوين SharePoint 2016 Skype for Business 2015.
    
  - [نماذج SharePoint 2016 ل Microsoft](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [SharePoint بيانات Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [نماذج Skype for Business 2015 الهندسية من Microsoft](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **النظام** الأساسي: استخدم هذه الموارد لتحديد النظام الأساسي المثالي وتكوين SharePoint 2013 Exchange 2013 وLync 2013.
    
  - [SharePoint النظام الأساسي ل 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [Exchange النظام الأساسي ل 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [خيارات النظام الأساسي ل Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 في Azure**: استخدم ملصقات المعلومات هذه لتصميم أحمال عمل SharePoint Server 2013 وتكوينها في خدمات البنية الأساسية في Azure.
    
  - [مواقع الإنترنت في Azure SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [عينة تصميم: مواقع الإنترنت في Azure SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint إلى Azure بعد حدوث كارثة](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>ملصقات النماذج الهندسية

توفر ملصقات SharePoint 2016 Skype for Business 2015 طريقة لمقارنة أساليب النشر بتنسيق سهل الطباعة. تتضمن الملصقات قائمة بكل خيارات التكوين أو النظام الأساسي. فهي توفر المعلومات التالية لكل خيار:
  
- **نظرة** عامة: ملخص مختصر عن النظام الأساسي، بما في ذلك رسم تخطيطي تصوري.
    
- **الأفضل ل**: السيناريوهات الشائعة التي تناسب النظام الأساسي بشكل مثالي.
    
- **متطلبات الترخيص**: التراخيص التي تحتاج إليها للنشر.
    
- **المهام الهندسية**: القرارات التي تحتاج إلى اتخاذها كمهندس معماري.
    
- **مهام محترفي IT أو مسؤولياتهم**: المسؤوليات اليومية التي يحتاج موظفوها إلى التخطيط لها.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>نماذج معمارية SharePoint Microsoft Server 2016

|عنصر|الوصف|
|---|---|
|[![صورة مصغرة لملصق SharePoint الهندسة المعمارية ل Server 2016.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=52650)    |يصف ملصق المعلومات هذا SharePoint Online و Azure SharePoint تكوينات العمل التي يحتاج صانعو قرارات الأعمال ومهندسو الحلول إلى معرفتها. <br/><br/> - **SharePoint Online (SaaS)**: SharePoint عبر برنامج كنموذج اشتراك خدمة (SaaS). <br/> - **SharePoint المختلطة**: ان SharePoint المواقع والتطبيقات إلى السحابة بالسرعة التي تريدها. <br/> - **SharePoint Azure (IaaS)**: توسيع البيئة المحلية إلى Azure، ونشر SharePoint 2016 هناك. (يوصى باستخدام هذا النموذج لبيئات الاسترداد السريع أو حالات التوفر في حالات الكوارث وبيئات dev/test.) <br/> - **SharePoint** المحلية: تخطيط بيئة SharePoint ونشرها والمحافظة عليها وتخصيصها في مركز بيانات تحتفظ به.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>SharePoint قواعد بيانات الخادم 2016

|عنصر|الوصف|
|---|---|
|[![صورة مصغرة لملصق قواعد بيانات SharePoint Server 2016.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=55041)    |ملصق IT هذا هو مرجع سريع لقواعد بيانات SharePoint Server 2016. سترى تفاصيل لكل قاعدة بيانات: <br/><br/> - الحجم <br/> - إرشادات التحجيم <br/> - أنماط I/O <br/> - المتطلبات <br/><br/>  تعرض الصفحة الأولى قواعد SharePoint وتطبيقات الخدمة التي تحتوي على قواعد بيانات متعددة. تعرض الصفحة الثانية كل تطبيقات الخدمة التي تحتوي على قواعد بيانات واحدة. <br/><br/>  لمزيد من المعلومات، راجع أنواع قاعدة البيانات [وأوصافها في SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>نماذج Skype for Business المعمارية ل Microsoft 2015

|عنصر|الوصف|
|---|---|
|[![صورة مصغرة لملصق Skype for Business الهندسة المعمارية.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=55022)    |يصف هذا الملصق Skype for Business عبر الإنترنت والمختلط والمختلط والسحابي (PBX). كما يصف التكامل مع Exchange SharePoint التي يحتاج صانعو قرارات الأعمال ومهندسو الحلول إلى معرفتها. <br/><br/> إن الملصق مخصص لمهنيي المعلومات لزيادة الوعي بالنماذج الهندسية الأساسية التي يمكن من خلالها Skype for Business الإنترنت Skype for Business محليا. <br/><br/>ابدأ التكوين الأكثر ملاءمة لاحتياجات المؤسسة وخططها. يمكنك التفكير في تكوينات أخرى واستخدامها حسب الحاجة. على سبيل المثال، قد ترغب في التفكير في التكامل مع Exchange SharePoint أو حل يستفيد من عرض PBX السحابي من Microsoft.|
   
## <a name="platform-options-posters"></a>ملصقات خيارات النظام الأساسي

توفر ملصقات SHAREPOINT 2013 Exchange 2013 وLync 2013 طريقة لمقارنة أساليب النشر بنظرة سريعة. يسرد كل ملصق كل التكوينات أو خيارات النظام الأساسي. يوفر المعلومات التالية لكل خيار:
  
- **نظرة** عامة: ملخص مختصر عن النظام الأساسي، بما في ذلك رسم تخطيطي تصوري.
    
- **الأفضل ل**: السيناريوهات الشائعة التي تناسب النظام الأساسي بشكل مثالي.
    
- **متطلبات الترخيص**: التراخيص التي تحتاج إليها للنشر.
    
- **المهام الهندسية**: القرارات التي تحتاج إلى اتخاذها كمهندس معماري.
    
- **مهام محترفي IT أو مسؤولياتهم**: المسؤوليات اليومية التي يحتاج موظفوها إلى التخطيط لها.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>SharePoint النظام الأساسي ل 2013

|عنصر|الوصف|
|---|---|
|[![صورة مصغرة لملصق خيارات النظام الأساسي SharePoint 2013.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=40332)    |بالنسبة لصانعي قرارات الأعمال والمهندسين المعماريين، يعرض هذا الملصق خيارات النظام الأساسي لكل من SharePoint 2013 و SharePoint في Microsoft 365 والهجين المختلط في الموقع مع عمليات النشر Microsoft 365 و Azure والنشرات في الموقع فقط. ويتضمن نظرة عامة حول كل هندسة وتوصيات ومتطلبات ترخيص وقوائم للمهام الهندسية ومهام محترفي المعلومات لكل نظام أساسي. يسلط الملصق الضوء على SharePoint على Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>Exchange النظام الأساسي ل 2013

|عنصر|الوصف|
|---|---|
|[![صورة مصغرة لملصق Exchange النظام الأساسي.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=42676)    |بالنسبة لصانعي قرارات الأعمال والمهندسين المعماريين، يصف هذا الملصق خيارات النظام الأساسي Exchange 2013. يمكن للعملاء الاختيار من Exchange Online باستخدام Microsoft 365 وهجين Exchange Exchange Server والمستضافة Exchange. يفصيل الملصق كل خيار معماري، بما في ذلك السيناريوهات المثالية لكل منها ومتطلبات الترخيص ومسؤوليات محترفي المعلومات.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>خيارات النظام الأساسي ل Lync 2013

|عنصر|الوصف|
|---|---|
|[![صورة مصغرة لملصق خيارات النظام الأساسي في Lync 2013.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41677)    |بالنسبة لصانعي قرارات الأعمال والمهندسين المعماريين، يصف هذا الملصق خيارات النظام الأساسي ل Lync 2013. يمكن للعملاء الاختيار من Lync Online باستخدام Lync Microsoft 365 وLync وLync Server المستضاف وLync Server المستضاف. يفصيل ملصق المعلومات كل خيار معماري، بما في ذلك السيناريوهات المثالية لكل منها ومتطلبات الترخيص ومسؤوليات محترفي المعلومات.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint في ملصقات حلول Azure

تظهر ملصقات SHAREPOINT في Azure الحلول المستندة إلى Azure التي تستخدم SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>مواقع الإنترنت في Microsoft Azure باستخدام SharePoint Server 2013

|عنصر|الوصف|
|---|---|
|[![صورة لمواقع الإنترنت في Azure باستخدام SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41992)    |يوضح هذا الملصق أنشطة التصميم الأساسية والهندسة المستحسنة للمواقع التي تواجه الإنترنت في Azure.  <br/><br/> لمزيد من المعلومات، راجع المقالات التالية:  <br/><br/> - [مواقع الإنترنت في Azure SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [هندسة Azure SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>مواقع الإنترنت في Azure SharePoint 2013

|عنصر|الوصف|
|---|---|
|[![صورة لمواقع الإنترنت في Microsoft Azure SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41991)    |استخدم عينة التصميم هذه كنقطة بداية لهندستك الخاصة لموقع مواجه للإنترنت في Azure باستخدام SharePoint Server 2013. <br/><br/> لمزيد من المعلومات، راجع المقالات التالية:  <br/><br/> - [مواقع الإنترنت في Azure SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [هندسة Azure SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint إلى Microsoft Azure بعد حدوث كارثة

|عنصر|الوصف|
|---|---|
|[![صورة لملصق SharePoint في عملية استرداد البيانات في مرحلة ما بعد الكوارث إلى Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41993)    |يعرض ملصق IT هذا مبادئ البنية لبيئة استرداد الكوارث في Azure. <br/><br/> لمزيد من المعلومات، راجع المقالات التالية:  <br/><br/> - [SharePoint الخادم 2013 في Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [هندسة Azure SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>راجع أيضًا

- [Microsoft 365 حل وهندسة](../solutions/index.yml)
  
- [نماذج هندسة سحابة Microsoft](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 اختبارات الاختبار](m365-enterprise-test-lab-guides.md)
  
- [الحلول المختلطة](hybrid-solutions.md)