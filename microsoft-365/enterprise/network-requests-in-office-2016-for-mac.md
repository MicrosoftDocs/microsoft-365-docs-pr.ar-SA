---
title: طلبات الشبكة في Office for Mac
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/9/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Adm_O365_Setup
- seo-marvel-apr2020
search.appverid: MOM160
ms.assetid: afdae969-4046-44b9-9adb-f1bab216414b
description: تصف هذه المقالة نقاط النهاية وعناوين URL التي Office for Mac التطبيقات التي تحاول الوصول إليها والخدمات المقدمة.
ms.openlocfilehash: 477225cf99ead3f5609c8082644293d4ac006603
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091116"
---
# <a name="network-requests-in-office-for-mac"></a>طلبات الشبكة في Office for Mac

توفر تطبيقات Office for Mac تجربة تطبيق أصلية على نظام macOS الأساسي. تم تصميم كل تطبيق للعمل في مجموعة متنوعة من السيناريوهات، بما في ذلك الحالات التي لا يتوفر فيها وصول إلى الشبكة. عند توصيل جهاز بشبكة، تتصل التطبيقات تلقائيا بسلسلة من الخدمات المستندة إلى الويب لتوفير وظائف محسنة. تصف المعلومات التالية نقاط النهاية وعناوين URL التي تحاول التطبيقات الوصول إليها، والخدمات المقدمة. هذه المعلومات مفيدة عند استكشاف مشكلات تكوين الشبكة وإصلاحها وتعيين نهج لخوادم وكيل الشبكة. تهدف التفاصيل الواردة في هذه المقالة إلى إكمال [مقالة عنوان URL ونطاقات العناوين Office 365](urls-and-ip-address-ranges.md)، والتي تتضمن نقاط النهاية لأجهزة الكمبيوتر التي تقوم بتشغيل Microsoft Windows. ما لم تتم الإشارة إلى ذلك، تنطبق المعلومات الواردة في هذه المقالة أيضا على Office 2019 for Mac و Office 2016 for Mac، والتي تتوفر كشراء لمرة واحدة من متجر بيع بالتجزئة أو من خلال اتفاقية ترخيص مجمع. 

  
تتضمن معظم هذه المقالة جداول توضح تفاصيل عناوين URL للشبكة ونوع ووصف الخدمة أو الميزة التي توفرها نقطة النهاية هذه. قد يختلف كل تطبيق من تطبيقات Office في استخدام الخدمة ونقطة النهاية. يتم تعريف التطبيقات التالية في الجداول أدناه:
  
- W: Word
- P: PowerPoint
- س: Excel
- O: Outlook
- N: OneNote
   
يتم تعريف نوع URL كما يلي:
  
- ST: ثابت - يتم ترميز عنوان URL في تطبيق العميل.
    
- SS: Semi-Static - يتم ترميز عنوان URL كجزء من صفحة ويب أو معاد التوجيه.
    
- CS: Config Service - يتم إرجاع URL كجزء من Office Configuration Service.

    
## <a name="office-for-mac-default-configuration"></a>التكوين الافتراضي Office for Mac

 **التثبيت والتحديثات**
  
يتم استخدام نقاط نهاية الشبكة التالية لتنزيل برنامج تثبيت Office for Mac من شبكة تسليم المحتوى من Microsoft (CDN).
  
|**URL**|**نوع**|**الوصف**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |سانت  <br/> |Microsoft 365 خدمة إعادة توجيه مدخل التثبيت إلى أحدث حزم التثبيت.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |موقع حزم التثبيت على شبكة تسليم المحتوى.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |موقع حزم التثبيت على شبكة تسليم المحتوى.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |سانت  <br/> |نقطة نهاية التحكم في الإدارة للتكرار التلقائي لبرامج Microsoft  <br/> |
   
 **تشغيل التطبيق الأول**
  
يتم الاتصال بنقاط نهاية الشبكة التالية عند التشغيل الأول تطبيق Office. توفر نقاط النهاية هذه وظائف Office محسنة للمستخدمين، ويتم الاتصال بعناوين URL بغض النظر عن نوع الترخيص (بما في ذلك تثبيتات الترخيص المجمع).
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |سانت  <br/> |تكوين 'Flighting' - يسمح بضوء الميزة والتجريب.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |سانت  <br/> |اختبار تكوين الشبكة 'Flighting'  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |سانت  <br/> |اختبار تكوين الشبكة 'Flighting'  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |سانت  <br/> |Office Configuration Service - قائمة رئيسية لنقاط نهاية الخدمة.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |سانت  <br/> |Office تنزيل بيانات تتبع الاستخدام للقواعد - إعلام العميل بالبيانات والأحداث التي يجب تحميلها إلى خدمة بيانات تتبع الاستخدام.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote خدمة بيانات تتبع الاستخدام  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |سانت  <br/> |Office تقرير Upload بيانات تتبع الاستخدام - يتم تحميل "Heartbeart" وأحداث الخطأ التي تحدث على العميل إلى خدمة بيانات تتبع الاستخدام.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office Template Service - يوفر للمستخدمين قوالب مستندات عبر الإنترنت.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office تنزيلات القوالب - تخزين صور قوالب PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |تكوين المتجر لتطبيقات Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office كتالوج خدمات تكامل المستندات (قائمة الخدمات ونقاط النهاية) واكتشاف النطاق الرئيسي.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |الموارد الخاصة ب Home Realm Discovery v2 (15.40 والإصدارات الأحدث)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |سانت  <br/> |Microsoft AutoUpdate Manifests - يتحقق لمعرفة ما إذا كانت هناك تحديثات متوفرة  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |مكتبة Microsoft Ajax JavaScript  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |ث  <br/> |SS  <br/> |تطبيق Wikipedia لتكوين وموارد Office.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing تطبيق الخريطة لتكوين Office والموارد.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |يقوم الأشخاص Graph التطبيق لتكوين Office والموارد.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |سانت  <br/> |ما هو المحتوى الجديد OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |سانت  <br/> |محتوى جديد OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |ما هي الصور الجديدة OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |يا  <br/> |سانت  <br/> |خدمة الدعم داخل التطبيق.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |يا  <br/> |سانت  <br/> |خدمة الكشف عن حساب البريد الإلكتروني.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |سانت  <br/> |Outlook AutoDiscovery  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |سانت  <br/> |Outlook نقطة نهاية لخدمة Microsoft 365.  <br/> |
|```https://r1.res.office365.com/```  <br/> |يا  <br/> |سانت  <br/> |أيقونات الوظائف الإضافية Outlook.  <br/> |
   
> [!NOTE]
> تعمل Office Configuration Service كخدمة اكتشاف تلقائي لجميع عملاء Microsoft Office، وليس فقط ل Mac. نقاط النهاية التي يتم إرجاعها في الاستجابة شبه ثابتة في هذا التغيير غير متكررة جدا، ولكن لا تزال ممكنة. 
  
 **تسجيل الدخول**
  
يتم الاتصال بنقاط نهاية الشبكة التالية عند تسجيل الدخول إلى التخزين المستند إلى السحابة. استنادا إلى نوع حسابك، قد يتم الاتصال بخدمات مختلفة. على سبيل المثال:
  
- **MSA: حساب Microsoft** - يستخدم عادة لسيناريوهات المستهلك والبيع بالتجزئة 
    
- **OrgID: حساب المؤسسة** - يستخدم عادة للسيناريوهات التجارية 
    
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |سانت  <br/> |خدمة تخويل Windows  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |سانت  <br/> |Microsoft 365 Login Service (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |سانت  <br/> |خدمة تسجيل الدخول إلى حساب Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |مساعد خدمة تسجيل الدخول إلى حساب Microsoft (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |العلامة التجارية لتسجيل الدخول Microsoft 365 (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |محدد موقع تخزين المستندات والأماكن  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |خدمة المستندات الأحدث استخداما (MRU)  <br/> |
   
> [!NOTE]
> بالنسبة لتراخيص البيع بالتجزئة والمستندة إلى الاشتراك، يؤدي تسجيل الدخول إلى تنشيط المنتج، وتمكين الوصول إلى موارد السحابة مثل OneDrive. بالنسبة لتثبيتات الترخيص المجمع، لا تزال تتم مطالبة المستخدمين بتسجيل الدخول (بشكل افتراضي)، ولكن هذا مطلوب فقط للوصول إلى موارد السحابة، حيث تم تنشيط المنتج بالفعل. 
  
 **تنشيط المنتج**
  
تنطبق نقاط نهاية الشبكة التالية على عمليات تنشيط Microsoft 365 Subscription و Retail License. على وجه التحديد، لا ينطبق هذا على عمليات تثبيت الترخيص المجمع.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |خدمة ترخيص Office  <br/> |
   
 **المحتوى الجديد**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 Subscription فقط.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |ما هو محتوى صفحة JSON الجديد.  <br/> |
   
 **الباحث**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 Subscription فقط.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |ث  <br/> |CS  <br/> |خدمة ويب للباحث  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |ث  <br/> |CS  <br/> |محتوى ثابت للباحث  <br/> |
|```https://www.bing.com/```  <br/> |ث  <br/> |CS  <br/> |موفر محتوى الباحث  <br/> |
   
 **البحث الذكي**
  
تنطبق نقاط نهاية الشبكة التالية على كل من عمليات تنشيط الاشتراك Microsoft 365 والبيع بالتجزئة/الترخيص المجمع.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |خدمة ويب Insights  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |مكتبة JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |دعم مكتبة JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |موفر محتوى Insights  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |موفر محتوى Insights  <br/> |
   
 **مصمم PowerPoint**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 Subscription فقط.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |ف  <br/> |CS  <br/> |خدمة ويب PowerPoint Designer  <br/> |
   
 **ميزة البدء السريع في PowerPoint**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 Subscription فقط.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |ف  <br/> |CS  <br/> |خدمة ويب PowerPoint QuickStarter  <br/> |
   
 **إرسال ابتسامة/وجه عابس**
  
تنطبق نقاط نهاية الشبكة التالية على كل من عمليات تنشيط الاشتراك Microsoft 365 والبيع بالتجزئة/الترخيص المجمع.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |إرسال خدمة ابتسامة  <br/> |
   
 **الاتصال بالدعم**
  
تنطبق نقاط نهاية الشبكة التالية على كل من عمليات تنشيط الاشتراك Microsoft 365 والبيع بالتجزئة/الترخيص المجمع.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |يا  <br/> |CS  <br/> |الاتصال بخدمة الدعم  <br/> |
|```https://acompli.helpshift.com/```  <br/> |يا  <br/> |CS  <br/> |خدمة الدعم داخل التطبيق  <br/> |
   
 **حفظ بتنسيق PDF**
  
تنطبق نقاط نهاية الشبكة التالية على كل من عمليات تنشيط الاشتراك Microsoft 365 والبيع بالتجزئة/الترخيص المجمع.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |ث  <br/> |CS  <br/> |خدمة تحويل مستندات Word (PDF)  <br/> |
   
 **تطبيقات Office (الوظائف الإضافية الملقبة)**
  
تنطبق نقاط نهاية الشبكة التالية على كل من تنشيطات الاشتراك Microsoft 365 وترخيص البيع بالتجزئة/الترخيص المجمع عندما تكون وظائف التطبيق الإضافية Office موثوقا بها.
  
|**URL**|**تطبيقات**|**نوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |تكوين مخزن تطبيق Office  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |ث  <br/> |SS  <br/> |موارد تطبيق Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing تعيين موارد التطبيق  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |الأشخاص Graph موارد التطبيق  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |خدمة إعادة توجيه Office  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office مكتبات JavaScript  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |خدمة بيانات تتبع الاستخدام وإعداد التقارير لتطبيقات Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |ث  <br/> |SS  <br/> |مكتبة Microsoft Ajax JavaScript  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |مكتبة Microsoft Ajax JavaScript  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office مكتبات JavaScript  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الدعم  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الدعم  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الدعم  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |مكتبة JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |إرسال تقرير عن الخطأ  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الخط  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |خدمة بيانات تتبع الاستخدام  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |تقرير بيانات تتبع الاستخدام  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |مكتبة الأصول Microsoft Store  <br/> |
|```https://*.wikipedia.org/```  <br/> |ث  <br/> |SS  <br/> |موارد صفحة ويكيبيديا  <br/> |
|```https://upload.wikimedia.org/```  <br/> |ث  <br/> |SS  <br/> |موارد وسائط ويكيبيديا  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |ث  <br/> |SS  <br/> |إطار بيئة الاختبار المعزولة في ويكيبيديا  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |قوالب الخريطة  <br/> |
   
 **الارتباطات الآمنة**
  
تنطبق نقطة نهاية الشبكة التالية على جميع تطبيقات Office لاشتراك Microsoft 365 فقط.
  
|**URL**|**نوع**|**الوصف**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |Microsoft خزينة Link Service  <br/> |
   
 **الإبلاغ عن الأعطال**
  
تنطبق نقطة نهاية الشبكة التالية على جميع تطبيقات Office لكل من تنشيطات الاشتراك Microsoft 365 وتجزئة/ترخيص مجمع. عند تعطل عملية بشكل غير متوقع، يتم إنشاء تقرير وإرساله إلى خدمة Watson.
  
|**URL**|**نوع**|**الوصف**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |سانت  <br/> |Microsoft Error Reporting Service  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |سانت  <br/> |Office خدمة Insights التعاونية  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>خيارات لتقليل طلبات الشبكة وحركة المرور

يوفر التكوين الافتراضي Office for Mac أفضل تجربة للمستخدم، سواء من حيث الوظائف أو الحفاظ على تحديث الجهاز. في بعض السيناريوهات، قد ترغب في منع التطبيقات من الاتصال بنقاط نهاية الشبكة. يناقش هذا القسم خيارات القيام بذلك.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>تعطيل Sign-In السحابة Office Add-Ins
  
قد يكون لدى عملاء الترخيص المجمع نهج صارمة حول حفظ المستندات في التخزين المستند إلى السحابة. يمكن تعيين التفضيل التالي لكل تطبيق لتعطيل تسجيل الدخول إلى MSA/OrgID، والوصول إلى Office الوظائف الإضافية.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

إذا حاول المستخدمون الوصول إلى الدالة Sign-In، فسيرى خطأ أن اتصال الشبكة غير موجود. نظرا لأن هذا التفضيل يمنع أيضا تنشيط المنتج عبر الإنترنت، يجب استخدامه فقط لتثبيتات الترخيص المجمع. على وجه التحديد، سيؤدي استخدام هذا التفضيل إلى منع التطبيقات Office من الوصول إلى نقاط النهاية التالية:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- كافة نقاط النهاية المدرجة في المقطع "تسجيل الدخول" أعلاه.
    
- كافة نقاط النهاية المدرجة في قسم "البحث الذكي" أعلاه.
    
- كافة نقاط النهاية المدرجة في قسم "تنشيط المنتج" أعلاه.
    
- كافة نقاط النهاية المدرجة في قسم "Office Apps (aka add-ins)" أعلاه.
    
لإعادة إنشاء وظائف كاملة للمستخدم، قم بتعيين التفضيل إلى '2' أو قم بإزالته.
  
> [!NOTE]
> يتطلب هذا التفضيل Office for Mac النسخة 15.25 [160726] أو أحدث. 
  
### <a name="telemetry"></a>بيانات تتبع الاستخدام
  
يرسل Office for Mac معلومات تتبع الاستخدام مرة أخرى إلى Microsoft على فترات منتظمة. يتم تحميل البيانات إلى نقطة نهاية 'Nexus'. تساعد بيانات تتبع الاستخدام فريق الهندسة على تقييم الحالة وأي سلوكيات غير متوقعة لكل تطبيق Office. هناك فئتان من بيانات تتبع الاستخدام:
  
- يحتوي **Heartbeat** على معلومات الإصدار والترخيص. يتم إرسال هذه البيانات مباشرة عند تشغيل التطبيق. 
    
- يحتوي **الاستخدام** على معلومات حول كيفية استخدام التطبيقات والأخطاء غير الفادحة. يتم إرسال هذه البيانات كل 60 دقيقة. 
    
تأخذ Microsoft خصوصيتك على محمل الجد. يمكنك القراءة حول نهج Microsoft لجمع البيانات في [https://privacy.microsoft.com](https://privacy.microsoft.com). لمنع التطبيقات من إرسال القياس عن بعد "الاستخدام"، يمكن ضبط تفضيل **SendAllTelemetryEnabled** . التفضيل لكل تطبيق، ويمكن تعيينه عبر ملفات تعريف تكوين macOS، أو يدويا من المحطة الطرفية: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

يتم دائما إرسال بيانات تتبع أخطاء الاتصال ولا يمكن تعطيلها.
  
### <a name="crash-reporting"></a>الإبلاغ عن الأعطال
  
عند حدوث خطأ فادح في التطبيق، سيتم إنهاء التطبيق بشكل غير متوقع وتحميل تقرير تعطل إلى خدمة "Watson". يتكون تقرير التعطل من مكدس المكالمات، وهو قائمة بالخطوات التي كان التطبيق يعالجها قبل التعطل. تساعد هذه الخطوات فريق الهندسة على تحديد الوظيفة الدقيقة التي فشلت ولماذا.
  
في بعض الحالات، ستؤدي محتويات المستند إلى تعطل التطبيق. إذا كان التطبيق يعرف المستند على أنه السبب، فسيسأل المستخدم عما إذا كان من المناسب أيضا إرسال المستند مع مكدس المكالمات. يمكن للمستخدمين اتخاذ خيار مستنير لهذا السؤال. قد يكون لمسؤولي تكنولوجيا المعلومات متطلبات صارمة بشأن إرسال المستندات واتخاذ القرار نيابة عن المستخدم عدم إرسال المستندات مطلقا. يمكن تعيين التفضيل التالي لمنع إرسال المستندات ومنع المطالبة للمستخدم:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> إذا تم تعيين **SendAllTelemetryEnabled** إلى **FALSE**، يتم تعطيل كافة تقارير الأعطال لهذه العملية. لتمكين الإبلاغ عن الأعطال دون إرسال بيانات تتبع الاستخدام، يمكن تعيين التفضيل التالي: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>التحديثات
  
تصدر Microsoft تحديثات Office for Mac على فترات منتظمة (عادة مرة واحدة في الشهر). نحن نشجع المستخدمين ومسؤولي تكنولوجيا المعلومات بشدة على إبقاء الأجهزة محدثة لضمان تثبيت أحدث إصلاحات الأمان. في الحالات التي يرغب فيها مسؤولو تكنولوجيا المعلومات في التحكم الدقيق في تحديثات الجهاز وإدارتها، يمكن تعيين التفضيل التالي لمنع عملية "التحديث التلقائي" من الكشف تلقائيا عن تحديثات المنتجات وتقديمها:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>حظر الطلبات باستخدام جدار حماية/وكيل
  
إذا كانت مؤسستك تحظر طلبات عناوين URL عبر جدار حماية أو خادم وكيل، فتأكد من تكوين عناوين URL المدرجة في هذا المستند إما كما هو مسموح به، أو حظر مدرج مع استجابة 40X (على سبيل المثال، 403 أو 404). ستسمح الاستجابة 40X للتطبيقات Office بقبول عدم القدرة على الوصول إلى المورد بأمان، وستوفر تجربة مستخدم أسرع، من مجرد إسقاط الاتصال، ما سيؤدي بدوره إلى إعادة محاولة العميل.
  
إذا كان الخادم الوكيل يتطلب المصادقة، فسيتم إرجاع استجابة 407 إلى العميل. للحصول على أفضل تجربة، تأكد من أنك تستخدم Office for Mac الإصدارات 15.27 أو الإصدارات الأحدث، لأنها تتضمن إصلاحات محددة للعمل مع خوادم NTLM وKerberos.
  
  
## <a name="see-also"></a>راجع أيضًا

[نطاقات عناوين IP وعناوين URL في Office 365](urls-and-ip-address-ranges.md)

