---
title: نماذج معمارية لـ SharePoint وExchange وSkype for Business وLync
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: احصل على ملصقات تكنولوجيا المعلومات التي تصف النماذج المعمارية والنشر وخيارات النظام الأساسي SharePoint Exchange Skype for Business وLync.
ms.openlocfilehash: 859d952fc9a2e4e9315c7fef3e56b4e59d0f60d6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096865"
---
# <a name="architectural-models-for-sharepoint-exchange-skype-for-business-and-lync"></a>نماذج معمارية لـ SharePoint وExchange وSkype for Business وLync

تصف ملصقات تكنولوجيا المعلومات في هذه المقالة النماذج المعمارية وخيارات النشر SharePoint Exchange Skype for Business وLync. كما أنها توفر معلومات التصميم لنشر SharePoint في Microsoft Azure.
  
باستخدام Microsoft 365، يمكنك توفير خدمات تعاون واتصالات مألوفة من خلال السحابة. مع بعض الاستثناءات، تظل تجربة المستخدم هي نفسها سواء كنت تحتفظ بنشر محلي أو تستخدم Microsoft 365. 

وتعقد تجربة المستخدم الموحدة هذه قرار مكان وضع كل حمل عمل. كما أنه يثير أسئلة:
  
- كيف يمكنك اختيار نظام أساسي لأحمال العمل الفردية؟
    
- هل من المنطقي الاحتفاظ بأي خدمة في الموقع؟
    
- في أي سيناريو يكون النشر المختلط مناسبا؟
    
- كيف يتلاءم Azure مع الصورة؟
    
- ما هي تكوينات أحمال عمل الخادم Office التي يدعمها Azure؟
    
> [!TIP]
> تتوفر معظم الملصقات في هذه المقالة بلغات متعددة. تتضمن اللغات المتوفرة اللغات الصينية والإنجليزية والفرنسية والألمانية والإيطالية واليابانية والكورية والبرتغالية والروسية والإسبانية. لتنزيل ملصق بإحدى هذه اللغات، ضمن صورة الملصق المصغرة، حدد **المزيد من اللغات**.
  
أخبرنا برأيك! أرسل لنا بريدا إلكترونيا على [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 
  
استخدم الارتباطات التالية للحصول على الملصقات التي تحتاجها:
  
- **النماذج المعمارية**: استخدم هذه الموارد لتحديد النظام الأساسي والتكوين المثاليين SharePoint 2016 Skype for Business 2015.
    
  - [نماذج Microsoft SharePoint 2016 المعمارية](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_ArchModel)
    
  - [قواعد بيانات SharePoint Server 2016](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2016_Databases)
    
  - [نماذج Microsoft Skype for Business 2015 المعمارية](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SfB2015_ArchModel)
    
- **النظام الأساسي**: استخدم هذه الموارد لتحديد النظام الأساسي والتكوين المثاليين SharePoint 2013 Exchange 2013 وLync 2013.
    
  - [خيارات النظام الأساسي SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#SP2013_Options)
    
  - [خيارات النظام الأساسي Exchange 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Exch2013_options)
    
  - [خيارات النظام الأساسي في Lync 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Lync2013_Options)
    
- **SharePoint Server 2013 في Azure**: استخدم ملصقات تكنولوجيا المعلومات هذه لتصميم أحمال عمل SharePoint Server 2013 وتكوينها في خدمات البنية الأساسية ل Azure.
    
  - [مواقع الإنترنت في Azure باستخدام SharePoint Server 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#Azure_sharepoint2013)
    
  - [نموذج التصميم: مواقع الإنترنت في Azure SharePoint 2013](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#DesignSampleInternetSites)
    
  - [SharePoint الإصلاح بعد الكارثة إلى Azure](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md#sharepoint_recovery_Azure)
    
## <a name="architectural-models-posters"></a>ملصقات النماذج المعمارية

توفر ملصقات تكنولوجيا المعلومات ل SharePoint 2016 و Skype for Business 2015 طريقة لمقارنة أساليب النشر بتنسيق سهل الطباعة. تسرد الملصقات جميع خيارات التكوين أو النظام الأساسي. وهي توفر المعلومات التالية لكل خيار:
  
- **نظرة عامة**: ملخص موجز للنظام الأساسي، بما في ذلك رسم تخطيطي تصوري.
    
- **الأفضل ل**: السيناريوهات الشائعة المناسبة بشكل مثالي للنظام الأساسي.
    
- **متطلبات الترخيص**: التراخيص التي تحتاجها للتوزيع.
    
- **مهام التصميم**: القرارات التي تحتاج إلى اتخاذها كمهندس.
    
- **مهام أو مسؤوليات محترفي تكنولوجيا المعلومات**: المسؤوليات اليومية التي يحتاج موظفو تكنولوجيا المعلومات إلى التخطيط لها.
    
<a name="SP2016_ArchModel"> </a>
### <a name="microsoft-sharepoint-server-2016-architectural-models"></a>نماذج Microsoft SharePoint Server 2016 المعمارية

|البند|الوصف|
|---|---|
|[![صورة مصغرة لملصق SharePoint Server 2016 Architectural Models.](../media/7d3e590c-1f3b-42cf-920d-9edac8fa3e04.png)          ](https://www.microsoft.com/download/details.aspx?id=52650) <br/> [PDF](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.pdf)\| [](https://download.microsoft.com/download/4/F/A/4FA0F94B-EE2F-41DB-A047-D9864FEF41E9/SharePoint2016ArchitecturalModels.vsdx)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=52650)    |يصف ملصق تكنولوجيا المعلومات هذا التكوينات SharePoint Online وAzure SharePoint المحلية التي يحتاج صانعو القرار في مجال الأعمال ومهندسو الحلول إلى معرفتها. <br/><br/> - **SharePoint Online (SaaS)**: استهلاك SharePoint من خلال نموذج اشتراك خدمة تأجير البرامج (SaaS). <br/> - **SharePoint المختلطة**: انقل مواقع وتطبيقات SharePoint إلى السحابة بالسرعة التي تناسبك. <br/> - **SharePoint في Azure (IaaS):** قم بتوسيع البيئة المحلية الخاصة بك إلى Azure، ونشر خوادم SharePoint 2016 هناك. (يوصى بهذا النموذج لبيئات قابلية الوصول العالية أو التعافي من الكوارث وبيئات التطوير/الاختبار.) <br/> - **SharePoint المحلي**: تخطيط بيئة SharePoint وتوزيعها وصيانتها وتخصيصها في مركز بيانات تحتفظ به.|
   
<a name="SP2016_Databases"> </a>
### <a name="sharepoint-server-2016-databases"></a>قواعد بيانات SharePoint Server 2016

|البند|الوصف|
|---|---|
|[![صورة مصغرة لملصق قواعد بيانات SharePoint Server 2016.](../media/c53e9de7-3bf8-446d-8766-e6700c8dd8e1.png)](https://www.microsoft.com/download/details.aspx?id=55041) <br/> [PDF](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.pdf)\| [](https://download.microsoft.com/download/D/5/D/D5DC1121-8BC5-4953-834F-1B5BB03EB691/DBrefguideSPS2016_tabloid.vsdx)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=55041)    |يعد ملصق تكنولوجيا المعلومات هذا مرجعا سريعا لقواعد بيانات SharePoint Server 2016. سترى تفاصيل لكل قاعدة بيانات: <br/><br/> - الحجم <br/> - إرشادات التحجيم <br/> - أنماط الإدخال/الإخراج <br/> - المتطلبات <br/><br/>  تعرض الصفحة الأولى قواعد بيانات النظام SharePoint وتطبيقات الخدمة التي تحتوي على قواعد بيانات متعددة. تعرض الصفحة الثانية جميع تطبيقات الخدمة التي تحتوي على قواعد بيانات واحدة. <br/><br/>  لمزيد من المعلومات، راجع [أنواع قواعد البيانات والأوصاف في SharePoint Server 2016](/SharePoint/technical-reference/database-types-and-descriptions).|
   
<a name="SfB2015_ArchModel"> </a>
### <a name="microsoft-skype-for-business-2015-architectural-models"></a>نماذج Microsoft Skype for Business 2015 المعمارية

|البند|الوصف|
|---|---|
|[![صورة مصغرة لملصق النماذج المعمارية Skype for Business.](../media/132288c0-6ae4-4394-88ab-b57dae367714.png)](https://www.microsoft.com/download/details.aspx?id=55022) <br/> [PDF](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.pdf)\| [](https://download.microsoft.com/download/7/7/4/7741262C-A60D-41F7-863B-99BF5964FBFE/Skype%20for%20Business%20Architectural%20Models.vsd)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=55022)    |يصف هذا الملصق Skype for Business التبادل الفرعي الخاص عبر الإنترنت والشبكات المحلية والمختلطة والسحابية (PBX). كما يصف التكامل مع تكوينات Exchange SharePoint التي يحتاج صانعو القرار في مجال الأعمال ومهندسو الحلول إلى معرفتها. <br/><br/> الملصق مخصص لمحترفي تكنولوجيا المعلومات لزيادة الوعي بالنماذج المعمارية الأساسية التي يمكن من خلالها استهلاك Skype for Business Online Skype for Business المحلي. <br/><br/>ابدأ بالتكوين الأنسب لاحتياجات مؤسستك وخططها. ضع في اعتبارك التكوينات الأخرى واستخدامها حسب الحاجة. على سبيل المثال، قد ترغب في التفكير في التكامل مع Exchange SharePoint أو حل يستفيد من عرض PBX السحابي من Microsoft.|
   
## <a name="platform-options-posters"></a>ملصقات خيارات النظام الأساسي

توفر ملصقات تكنولوجيا المعلومات ل SharePoint 2013 Exchange 2013 وLync 2013 طريقة لمقارنة أساليب النشر بنظرة سريعة. يسرد كل ملصق جميع التكوينات أو خيارات النظام الأساسي. يوفر المعلومات التالية لكل خيار:
  
- **نظرة عامة**: ملخص موجز للنظام الأساسي، بما في ذلك رسم تخطيطي تصوري.
    
- **الأفضل ل**: السيناريوهات الشائعة المناسبة بشكل مثالي للنظام الأساسي.
    
- **متطلبات الترخيص**: التراخيص التي تحتاجها للتوزيع.
    
- **مهام التصميم**: القرارات التي تحتاج إلى اتخاذها كمهندس.
    
- **مهام أو مسؤوليات محترفي تكنولوجيا المعلومات**: المسؤوليات اليومية التي يحتاج موظفو تكنولوجيا المعلومات إلى التخطيط لها.
    
<a name="SP2013_Options"> </a>
## <a name="sharepoint-2013-platform-options"></a>خيارات النظام الأساسي SharePoint 2013

|البند|الوصف|
|---|---|
|[![صورة مصغرة لملصق خيارات النظام الأساسي SharePoint 2013.](../media/SP-PlatformOptions.jpg)](https://www.microsoft.com/download/details.aspx?id=40332) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=324594)\| [](https://go.microsoft.com/fwlink/p/?LinkId=324593)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=40332)    |بالنسبة إلى صانعي القرار والمهندسين المعماريين في مجال الأعمال، يعرض هذا الملصق خيارات النظام الأساسي SharePoint 2013، SharePoint في Microsoft 365، والمختلط المحلي مع Microsoft 365 وAzure والنشر المحلي فقط. يتضمن نظرة عامة على كل بنية وتوصيات ومتطلبات ترخيص وقوائم مهام المهندس المعماري ومهام محترفي تكنولوجيا المعلومات لكل نظام أساسي. يسلط الملصق الضوء على العديد من حلول SharePoint على Azure.|
   
<a name="Exch2013_options"> </a>
## <a name="exchange-2013-platform-options"></a>خيارات النظام الأساسي Exchange 2013

|البند|الوصف|
|---|---|
|[![صورة مصغرة لملصق خيارات النظام الأساسي Exchange.](../media/ITPro-Other-Exchange2013PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=42676) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=398740)\| [](https://go.microsoft.com/fwlink/p/?LinkID=398742)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=42676)    |بالنسبة لصانعي القرار والمهندسين المعماريين في مجال الأعمال، يصف هذا الملصق خيارات النظام الأساسي Exchange 2013. يمكن للعملاء الاختيار من بين Exchange Online باستخدام Microsoft 365 Exchange المختلط Exchange Server المحلي Exchange المستضافة. يوضح الملصق تفاصيل كل خيار معماري، بما في ذلك السيناريوهات المثالية لكل منها ومتطلبات الترخيص ومسؤوليات محترفي تكنولوجيا المعلومات.|
   
<a name="Lync2013_Options"> </a>
## <a name="lync-2013-platform-options"></a>خيارات النظام الأساسي في Lync 2013

|البند|الوصف|
|---|---|
|[![صورة مصغرة لملصق خيارات النظام الأساسي في Lync 2013.](../media/Lync-PlatformOptions.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41677) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkID=391837)\| [](https://go.microsoft.com/fwlink/p/?LinkID=391839)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41677)    |بالنسبة إلى صانعي القرار والمهندسين المعماريين في مجال الأعمال، يصف هذا الملصق خيارات النظام الأساسي ل Lync 2013. يمكن للعملاء الاختيار من Lync Online باستخدام Microsoft 365 وLync المختلط وLync Server المحلي وLync المستضاف. يوضح ملصق تكنولوجيا المعلومات تفاصيل كل خيار معماري، بما في ذلك السيناريوهات المثالية لكل منها ومتطلبات الترخيص ومسؤوليات محترفي تكنولوجيا المعلومات.|
   
<a name="Lync2013_Options"> </a>
## <a name="sharepoint-in-azure-solutions-posters"></a>SharePoint في ملصقات حلول Azure

تعرض ملصقات تكنولوجيا المعلومات SharePoint في Azure الحلول المستندة إلى Azure التي تستخدم SharePoint Server 2013.
  
<a name="Azure_sharepoint2013"> </a>
### <a name="internet-sites-in-microsoft-azure-using-sharepoint-server-2013"></a>مواقع الإنترنت في Microsoft Azure باستخدام SharePoint Server 2013

|البند|الوصف|
|---|---|
|[![صورة لمواقع الإنترنت في Azure باستخدام ملصق SharePoint Server 2013.](../media/MS-AZ-SPInternetSites.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41992) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392552)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392551)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41992)    |يوضح هذا الملصق أنشطة التصميم الرئيسية والتصميم الموصى به للمواقع التي تواجه الإنترنت في Azure.  <br/><br/> لمزيد من المعلومات، راجع المقالات التالية:  <br/><br/> - [مواقع الإنترنت في Azure باستخدام SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [تصميمات Azure ل SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="DesignSampleInternetSites"> </a>
### <a name="internet-sites-in-azure-for-sharepoint-2013"></a>مواقع الإنترنت في Azure SharePoint 2013

|البند|الوصف|
|---|---|
|[![صورة لمواقع الإنترنت في Microsoft Azure لملصق SharePoint Server 2013.](../media/MS-AZ-InternetSitesDesignSample.jpg)          ](https://www.microsoft.com/download/details.aspx?id=41991) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392549)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392548)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41991)    |استخدم نموذج التصميم هذا كنقطة بداية للبنية الخاصة بك لموقع يواجه الإنترنت في Azure باستخدام SharePoint Server 2013. <br/><br/> لمزيد من المعلومات، راجع المقالات التالية:  <br/><br/> - [مواقع الإنترنت في Azure باستخدام SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md) <br/> - [تصميمات Azure ل SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
<a name="sharepoint_recovery_Azure"> </a>
### <a name="sharepoint-disaster-recovery-to-microsoft-azure"></a>SharePoint التعافي من الكوارث إلى Microsoft Azure

|البند|الوصف|
|---|---|
|[![صورة لملصق SharePoint عملية استرداد البيانات بعد الكوارث إلى Azure.](../media/SP-DR-Azure.png)          ](https://www.microsoft.com/download/details.aspx?id=41993) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555)\| [](https://go.microsoft.com/fwlink/p/?LinkId=392554)\| Visio [المزيد من اللغات](https://www.microsoft.com/download/details.aspx?id=41993)    |يعرض ملصق تكنولوجيا المعلومات هذا مبادئ البنية لبيئة التعافي من الكوارث في Azure. <br/><br/> لمزيد من المعلومات، راجع المقالات التالية:  <br/><br/> - [الإصلاح بعد كارثة SharePoint Server 2013 في Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md) <br/> - [تصميمات Azure ل SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md)|
   
## <a name="see-also"></a>راجع أيضًا

- [مركز الحلول والهندسة من Microsoft 365](../solutions/index.yml)
  
- [نماذج هندسة سحابة Microsoft](../solutions/cloud-architecture-models.md)
  
- [Microsoft 365 أدلة مختبر الاختبار](m365-enterprise-test-lab-guides.md)
  
- [حلول مختلطة](hybrid-solutions.md)