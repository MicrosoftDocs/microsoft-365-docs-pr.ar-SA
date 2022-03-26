---
title: طلبات الشبكة في Office for Mac
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تصف هذه المقالة نقاط النهاية Office for Mac عناوين URL التي تحاول التطبيقات الوصول إليها، والخدمات المتوفرة.
ms.openlocfilehash: 37071b0aaf9e6f172d99a10cb4a1506f1627ef03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568772"
---
# <a name="network-requests-in-office-for-mac"></a>طلبات الشبكة في Office for Mac

Office for Mac التطبيق تجربة تطبيق أصلية على نظام macOS الأساسي. تم تصميم كل تطبيق للعمل في مجموعة متنوعة من السيناريوهات، بما في ذلك الحالات التي لا يتوفر فيها الوصول إلى الشبكة. عندما يكون الجهاز متصلا بشبكة، تتصل التطبيقات تلقائيا بسلسلة من الخدمات المستندة إلى الويب لتوفير وظائف محسنة. تصف المعلومات التالية نقاط النهاية ومحددات URL التي تحاول التطبيقات الوصول إليها، والخدمات المقدمة. تكون هذه المعلومات مفيدة عند استكشاف مشاكل تكوين الشبكة وإصلاحها وإعداد سياسات للخوادم الوكيلة للشبكة. إن التفاصيل الموجودة في هذه المقالة مخصصة لتكملة مقالة URL Office 365 [نطاقات](urls-and-ip-address-ranges.md) العنوان، التي تتضمن نقاط النهاية لأجهزة الكمبيوتر التي تقوم بتشغيل Microsoft Windows. ما لم يتم ذكر ذلك، تنطبق المعلومات الواردة في هذه المقالة أيضا على Office 2019 for Mac و Office 2016 for Mac، المتوفرة للشراء مرة واحدة من متجر بيع بالتجزئة أو من خلال اتفاقية ترخيص مجموعة. 

  
معظم هذه المقالة هي جداول توضح تفاصيل عناوين URL للشبكة ونوع الخدمة أو الميزة التي توفرها نقطة النهاية هذه ووصفها. قد يختلف Office التطبيق في الخدمة واستخدام نقطة النهاية. يتم تعريف التطبيقات التالية في الجداول أدناه:
  
- W: Word
- P: PowerPoint
- س: Excel
- O: Outlook
- N: OneNote
   
يتم تعريف نوع URL كما يلي:
  
- ST: ثابت - يتم الترميز الثابت ل URL في تطبيق العميل.
    
- SS: Semi-Static - يتم ترميز عنوان URL كجزء من صفحة ويب أو معيد توجيه.
    
- CS: خدمة المؤتمرات - يتم إرجاع عنوان URL كجزء من Office التكوين.

    
## <a name="office-for-mac-default-configuration"></a>Office for Mac التكوين الافتراضي

 **التثبيت والتحديثات**
  
يتم استخدام نقاط نهاية الشبكة التالية لتنزيل برنامج تثبيت Office for Mac من شبكة تسليم المحتوى من Microsoft (CDN).
  
|**URL**|**النوع**|**الوصف**|
|:-----|:-----|:-----|
|```https://go.microsoft.com/fwlink/```  <br/> |ST  <br/> |Microsoft 365 ارتباط إعادة توجيه مدخل التثبيت إلى حزم التثبيت الأخيرة.  <br/> |
|```https://officecdn-microsoft-com.akamaized.net/```  <br/> |SS  <br/> |موقع حزم التثبيت على شبكة تسليم المحتوى.  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |SS  <br/> |موقع حزم التثبيت على شبكة تسليم المحتوى.  <br/> |
|```https://officeci-mauservice.azurewebsites.net/```  <br/> |ST  <br/> |نقطة النهاية "عنصر تحكم الإدارة" ل Microsoft AutoUpdate  <br/> |
   
 **تشغيل التطبيق الأول**
  
يتم الاتصال بنقاط نهاية الشبكة التالية عند بدء تشغيل أول تطبيق Office. توفر نقاط النهاية هذه وظائف محسنة Office للمستخدمين، ويتم الاتصال عناوين URL بغض النظر عن نوع الترخيص (بما في ذلك عمليات تثبيت الترخيص الكلي).
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://config.edge.skype.com/```  <br/> |WXPON  <br/> |ST  <br/> |تكوين 'رحلة الطيران' - يسمح بالميزات الخفيفة والتجربة.  <br/> |
|```https://ocos-office365-s2s.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |اختبار تكوين الشبكة "الطيران"  <br/> |
|```https://client-office365-tas.msedge.net/```  <br/> |WXPON  <br/> |ST  <br/> |اختبار تكوين الشبكة "الطيران"  <br/> |
|```https://officeclient.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office التكوين - القائمة الرئيسية لنقاط نهاية الخدمة.  <br/> |
|```https://nexusrules.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office تنزيل بيانات استخدام القواعد - لإعلام العميل بالبيانات والأحداث التي يجب تحميلها إلى خدمة بيانات المحتوى.  <br/> |
|```https://mobile.pipe.aria.microsoft.com/```  <br/> |N  <br/> |CS  <br/> |OneNote بيانات عن بعد  <br/> |
|```https://nexus.officeapps.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |Office بيانات Upload التقارير - يتم تحميل "Heartbeart" والأحداث التي تحدث على العميل إلى خدمة بيانات الارتقام.  <br/> |
|```https://templateservice.office.com/```  <br/> |WXP  <br/> |CS  <br/> |Office القالب - توفر للمستخدمين قوالب مستندات عبر الإنترنت.  <br/> |
|```https://omextemplates.content.office.net/```  <br/> |WXP  <br/> |CS  <br/> |Office تنزيلات القوالب - تخزين صور قوالب PNG.  <br/> |
|```https://store.office.com/```  <br/> |WXP  <br/> |CS  <br/> |تكوين المتجر لتطبيقات Office.  <br/> |
|```https://odc.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Office كتالوج خدمات تكامل المستندات (قائمة بالخدمات ونقاط النهاية) واكتشاف المجال المنزلي.  <br/> |
|```https://cdn.odc.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |موارد ل Home Realm Discovery v2 (15.40 واللاحقة)  <br/> |
|```https://officecdn.microsoft.com/```  <br/> |WXPON  <br/> |ST  <br/> |بيانات التحديث التلقائي من Microsoft - التحقق لمعرفة ما إذا كانت هناك تحديثات متوفرة  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |WXPO  <br/> |SS  <br/> |مكتبة Microsoft Ajax JavaScript  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |تطبيق Wikipedia Office التكوين والموارد.  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing تطبيق الخريطة Office تكوين الموارد.  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |يمكن Graph تطبيق Office وتكوينه وموارده.  <br/> |
|```https://www.onenote.com/```  <br/> |N  <br/> |ST  <br/> |ما هو المحتوى الجديد OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |ST  <br/> |محتوى جديد OneNote.  <br/> |
|```https://site-cdn.onenote.net/```  <br/> |N  <br/> |SS  <br/> |ما هي الصور الجديدة OneNote.  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |ST  <br/> |خدمة الدعم داخل التطبيق.  <br/> |
|```https://prod-global-autodetect.acompli.net/```  <br/> |O  <br/> |ST  <br/> |خدمة الكشف عن حساب البريد الإلكتروني.  <br/> |
|```https://autodiscover-s.outlook.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook AutoDiscovery  <br/> |
|```https://outlook.office365.com/```  <br/> |WXPO  <br/> |ST  <br/> |Outlook نقطة نهاية Microsoft 365 الخدمة.  <br/> |
|```https://r1.res.office365.com/```  <br/> |O  <br/> |ST  <br/> |أيقونات Outlook الإضافية.  <br/> |
   
> [!NOTE]
> تعمل Office التكوين كخدمة اكتشاف تلقائي لجميع عملاء Microsoft Office، وليس فقط ل Mac. نقاط النهاية التي يتم إرجاعها في الاستجابة شبه ثابتة في هذا التغيير غير متكد، ولكن لا يزال ممكنا. 
  
 **تسجيل الدخول**
  
يتم الاتصال بنقاط نهاية الشبكة التالية عند تسجيل الدخول إلى مساحة تخزين مستندة إلى السحابة. استنادا إلى نوع حسابك، قد يتم الاتصال بالخدمات المختلفة. على سبيل المثال:
  
- **MSA: حساب Microsoft** - يستخدم عادة لسيناريوهات البيع بالتجزئة والبيع بالتجزئة 
    
- **OrgID: حساب المؤسسة** - يستخدم عادة للسيناريوهات التجارية 
    
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://login.windows.net/```  <br/> |WXPON  <br/> |ST  <br/> |Windows التخويل  <br/> |
|```https://login.microsoftonline.com/```  <br/> |WXPON  <br/> |ST  <br/> |Microsoft 365 تسجيل الدخول (OrgID)  <br/> |
|```https://login.live.com/```  <br/> |WXPON  <br/> |ST  <br/> |خدمة تسجيل الدخول إلى حساب Microsoft (MSA)  <br/> |
|```https://auth.gfx.ms/```  <br/> |WXPON  <br/> |CS  <br/> |Microsoft Account Login Service Helper (MSA)  <br/> |
|```https://secure.aadcdn.microsoftonline-p.com/```  <br/> |WXPON  <br/> |SS  <br/> |Microsoft 365 تسجيل الدخول (OrgID)  <br/> |
|```https://ocws.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |"موقع تخزين المستندات والأماكن"  <br/> |
|```https://roaming.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |خدمة المستندات المستخدمة مؤخرا (MRU)  <br/> |
   
> [!NOTE]
> بالنسبة لتراخيص البيع بالتجزئة والمستندة إلى الاشتراك، يقوم تسجيل الدخول بتنشيط المنتج، وتمكين الوصول إلى موارد السحابة مثل OneDrive. بالنسبة إلى عمليات تثبيت الترخيص الحجمي، لا تزال مطالبة المستخدمين تسجيل الدخول (بشكل افتراضي)، ولكن هذا مطلوب فقط للوصول إلى موارد السحابة، حيث يتم تنشيط المنتج بالفعل. 
  
 **تنشيط المنتج**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 الاشتراك وترخيص البيع بالتجزئة. وبشكل خاص، لا ينطبق ذلك على عمليات تثبيت الترخيص الكلي.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://ols.officeapps.live.com/```  <br/> |WXPON  <br/> |CS  <br/> |Office الترخيص  <br/> |
   
 **ما هو المحتوى الجديد**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 الاشتراك فقط.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://contentstorage.osi.office.net/```  <br/> |WXPO  <br/> |SS  <br/> |ما هو محتوى صفحة JSON الجديدة.  <br/> |
   
 **الباحث**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 الاشتراك فقط.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |خدمة الباحث على الويب  <br/> |
|```https://cdn.entity.osi.office.net/```  <br/> |W  <br/> |CS  <br/> |المحتوى الثابت للباحث  <br/> |
|```https://www.bing.com/```  <br/> |W  <br/> |CS  <br/> |موفر محتوى الباحث  <br/> |
   
 **البحث الذكي**
  
تنطبق نقاط نهاية الشبكة التالية على كل من Microsoft 365 الاشتراك وتنشيط ترخيص البيع بالتجزئة/الترخيص الحجمي.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://uci.officeapps.live.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights ويب  <br/> |
|```https://ajax.googleapis.com/```  <br/> |WXPN  <br/> |CS  <br/> |مكتبة JQuery  <br/> |
|```https://cdnjs.cloudflare.com/```  <br/> |WXPN  <br/> |CS  <br/> |دعم مكتبة JavaScript  <br/> |
|```https://www.bing.com/```  <br/> |WXPN  <br/> |CS  <br/> |Insights المحتوى  <br/> |
|```https://tse1.mm.bing.net/```  <br/> |WXPN  <br/> |CS  <br/> |Insights المحتوى  <br/> |
   
 **مصمم PowerPoint**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 الاشتراك فقط.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://pptsgs.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint ويب لمصمم  <br/> |
   
 **ميزة البدء السريع في PowerPoint**
  
تنطبق نقاط نهاية الشبكة التالية على Microsoft 365 الاشتراك فقط.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://pptcts.officeapps.live.com/```  <br/> |P  <br/> |CS  <br/> |PowerPoint QuickStarter على الويب  <br/> |
   
 **إرسال ابتسامة/وجه عابس**
  
تنطبق نقاط نهاية الشبكة التالية على كل من Microsoft 365 الاشتراك وتنشيط ترخيص البيع بالتجزئة/الترخيص الحجمي.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://sas.office.microsoft.com/```  <br/> |WXPON  <br/> |CS  <br/> |إرسال خدمة ابتسامة  <br/> |
   
 **الاتصال بالدعم**
  
تنطبق نقاط نهاية الشبكة التالية على كل من Microsoft 365 الاشتراك وتنشيط ترخيص البيع بالتجزئة/الترخيص الحجمي.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://powerlift-frontdesk.acompli.net/```  <br/> |O  <br/> |CS  <br/> |الاتصال ب خدمة الدعم  <br/> |
|```https://acompli.helpshift.com/```  <br/> |O  <br/> |CS  <br/> |خدمة الدعم داخل التطبيق  <br/> |
   
 **حفظ بتنسيق PDF**
  
تنطبق نقاط نهاية الشبكة التالية على كل من Microsoft 365 الاشتراك وتنشيط ترخيص البيع بالتجزئة/الترخيص الحجمي.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://wordcs.officeapps.live.com/```  <br/> |W  <br/> |CS  <br/> |خدمة تحويل مستندات Word (PDF)  <br/> |
   
 **Office التطبيقات (الوظائف الإضافية المليقية)**
  
تنطبق نقاط نهاية الشبكة التالية على كل من Microsoft 365 الاشتراك وتنشيط ترخيص البيع بالتجزئة/الترخيص الحجمي عند Office الوظائف الإضافية للتطبيقات الموثوق بها.
  
|**URL**|**التطبيقات**|**النوع**|**الوصف**|
|:-----|:-----|:-----|:-----|
|```https://store.office.com/```  <br/> |WXPO  <br/> |CS  <br/> |تطبيق Office المتجر  <br/> |
|```https://wikipedia.firstpartyapps.oaspapps.com/```  <br/> |W  <br/> |SS  <br/> |موارد تطبيق Wikipedia  <br/> |
|```https://excelbingmap.firstpartyapps.oaspapps.com/```  <br/> |X  <br/> |SS  <br/> |Bing تعيين موارد تطبيق الخريطة  <br/> |
|```https://peoplegraph.firstpartyapps.oaspapps.com```  <br/> |X  <br/> |SS  <br/> |الأشخاص Graph موارد التطبيق  <br/> |
|```https://o15.officeredir.microsoft.com/```  <br/> |WPX  <br/> |SS  <br/> |Office إعادة التوجيه  <br/> |
|```https://appsforoffice.microsoft.com/```  <br/> |WXP  <br/> |SS  <br/> |Office JavaScript  <br/> |
|```https://telemetry.firstpartyapps.oaspapps.com/```  <br/> |WX  <br/> |SS  <br/> |خدمة بيانات الاغتراف وإعداد التقارير لتطبيقات Office  <br/> |
|```https://ajax.microsoft.com/```  <br/> |W  <br/> |SS  <br/> |مكتبة Microsoft Ajax JavaScript  <br/> |
|```https://ajax.aspnetcdn.com/```  <br/> |X  <br/> |SS  <br/> |مكتبة Microsoft Ajax JavaScript  <br/> |
|```https://c.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |Office JavaScript  <br/> |
|```https://c1.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الدعم  <br/> |
|```https://cs.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الدعم  <br/> |
|```https://c.bing.com/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الدعم  <br/> |
|```https://*.cdn.optimizely.com/```  <br/> |WPXO  <br/> |SS  <br/> |مكتبة JavaScript  <br/> |
|```https://errors.client.optimizely.com/```  <br/> |WPX  <br/> |SS  <br/> |الإبلاغ عن الأخطاء  <br/> |
|```https://*-contentstorage.osi.office.net/```  <br/> |WPXO  <br/> |SS  <br/> |موارد الخط  <br/> |
|```https://nexus.ensighten.com/```  <br/> |WPXO  <br/> |SS  <br/> |خدمة بيانات التهية  <br/> |
|```https://browser.pipe.aria.microsoft.com/```  <br/> |WPXO  <br/> |SS  <br/> |الإبلاغ عن بيانات الاغتراف  <br/> |
|```https://*.vo.msecnd.net/```  <br/> |WPXO  <br/> |SS  <br/> |Microsoft Store الأصول  <br/> |
|```https://*.wikipedia.org/```  <br/> |W  <br/> |SS  <br/> |موارد صفحة Wikipedia  <br/> |
|```https://upload.wikimedia.org/```  <br/> |W  <br/> |SS  <br/> |موارد وسائط Wikipedia  <br/> |
|```https://wikipedia.firstpartyappssandbox.oappseperate.com/```  <br/> |W  <br/> |SS  <br/> |إطار الحماية ل Wikipedia  <br/> |
|```https://*.virtualearth.net/```  <br/> |X  <br/> |SS  <br/> |قوالب الخرائط  <br/> |
   
 **الارتباطات الآمنة**
  
تنطبق نقطة نهاية الشبكة التالية على Office التطبيقات Microsoft 365 الاشتراك فقط.
  
|**URL**|**النوع**|**الوصف**|
|:-----|:-----|:-----|
|```https://*.oscs.protection.outlook.com/```  <br/> |CS  <br/> |خدمة ارتباطات microsoft خزينة Microsoft  <br/> |
   
 **الإبلاغ عن الأععطل**
  
تنطبق نقطة نهاية الشبكة التالية على جميع تطبيقات Office لكل من Microsoft 365 الاشتراك وتنشيط ترخيص البيع بالتجزئة/الترخيص بالحجم. عندما تتعطل عملية بشكل غير متوقع، يتم إنشاء تقرير ويرسل إلى خدمة Watson.
  
|**URL**|**النوع**|**الوصف**|
|:-----|:-----|:-----|
|```https://watson.microsoft.com/```  <br/> |ST  <br/> |خدمة "الإبلاغ عن الخطأ من Microsoft"  <br/> |
|```https://officeci.azurewebsites.net/```  <br/> |ST  <br/> |Office التعاون Insights الخدمة  <br/> |
   
## <a name="options-for-reducing-network-requests-and-traffic"></a>خيارات لتقليل طلبات الشبكة و حركة المرور

يوفر التكوين الافتراضي Office for Mac المستخدم أفضل تجربة للمستخدم، من حيث الوظائف وإبقاء الجهاز مواكبا للمواعيد. في بعض السيناريوهات، قد ترغب في منع التطبيقات من الاتصال بنقاط نهاية الشبكة. يناقش هذا القسم خيارات للقيام بذلك.
  
 ### <a name="disabling-cloud-sign-in-and-office-add-ins"></a>تعطيل السحابة Sign-In Office Add-Ins
  
قد يكون لعملاء الترخيص الحجمي سياسات صارمة حول حفظ المستندات في مساحة تخزين مستندة إلى السحابة. يمكن تعيين التفضيل التالي لكل تطبيق لتعطيل تسجيل الدخول إلى MSA/OrgID، والوصول إلى Office الإضافية.
  
- ```defaults write com.microsoft.Word UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Excel UseOnlineContent -integer 0```

- ```defaults write com.microsoft.Powerpoint UseOnlineContent -integer 0```

إذا حاول المستخدمون الوصول إلى الدالة Sign-In، سيشاهدون خطأ عدم وجود اتصال شبكة. ونظرا لأن هذا التفضيل يمنع أيضا تنشيط المنتج عبر الإنترنت، يجب استخدامه فقط في عمليات تثبيت الترخيص الكلي. وبشكل خاص، سيمنع استخدام هذا التفضيل Office التطبيقات من الوصول إلى نقاط النهاية التالية:
  
- ```https://odc.officeapps.live.com```
    
- ```https://*.firstpartyapps.oaspapps.com```
    
- جميع نقاط النهاية المدرجة في المقطع "تسجيل الدخول" أعلاه.
    
- جميع نقاط النهاية المدرجة في القسم "البحث الذكي" أعلاه.
    
- جميع نقاط النهاية المدرجة في المقطع "تنشيط المنتج" أعلاه.
    
- جميع نقاط النهاية المدرجة في المقطع "Office التطبيقات (الملاكا الوظائف الإضافية)" أعلاه.
    
لإعادة إنشاء الوظائف الكاملة للمستخدم، قم بتعيين التفضيل إلى "2" أو إزالته.
  
> [!NOTE]
> يتطلب هذا التفضيل Office for Mac 15.25 [160726] أو أي وقت لاحق. 
  
### <a name="telemetry"></a>بيانات تتبع الاستخدام
  
Office for Mac إرسال معلومات بيانات التكليف إلى Microsoft في فواصل زمنية منتظمة. يتم تحميل البيانات إلى نقطة نهاية 'Nexus'. تساعد بيانات بيانات التكليف فريق الهندسة على تقييم الحالة وأي سلوكيات غير متوقعة لكل تطبيق Office. هناك فئتان من بيانات بيانات الاقتراف:
  
- **تحتوي "** دقات القلب" على معلومات حول الإصدار والترخيص. يتم إرسال هذه البيانات مباشرة عند تشغيل التطبيق. 
    
- **يحتوي** الاستخدام على معلومات حول كيفية استخدام التطبيقات والأخطاء غير الهلكة. يتم إرسال هذه البيانات كل 60 دقيقة. 
    
تأخذ Microsoft خصوصيتك على محمل الجد. يمكنك القراءة حول نهج تجميع بيانات Microsoft في [https://privacy.microsoft.com](https://privacy.microsoft.com). لمنع التطبيقات من إرسال بيانات بيانات الاستخدام، يمكن ضبط التفضيل **SendAllTelemetryEnabled** . يكون التفضيل لكل تطبيق، ويمكن تعيينه عبر ملفات تعريف تكوين macOS، أو يدويا من المحطة الطرفية: 
  
```defaults write com.microsoft.Word SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Excel SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Powerpoint SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Outlook SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.onenote.mac SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.autoupdate2 SendAllTelemetryEnabled -bool FALSE```

```defaults write com.microsoft.Office365ServiceV2 SendAllTelemetryEnabled -bool FALSE```

يتم دائما إرسال بيانات قياس بيانات عن بعد لنبضات القلب ولا يمكن تعطيلها.
  
### <a name="crash-reporting"></a>الإبلاغ عن الأععطل
  
عند حدوث خطأ فادح في التطبيق، سيتم إنهاء التطبيق بشكل غير متوقع وتحميل تقرير تعطل إلى خدمة 'Watson'. يتكون تقرير الأعطبة من مكدس استدعاءات، وهي قائمة الخطوات التي كان التطبيق ي معالجة لها مما يؤدي إلى العطل. تساعد هذه الخطوات فريق الهندسة على تحديد الدالة الدقيقة التي فشلت ولماذا.
  
في بعض الحالات، ستتسبب محتويات المستند في تعطل التطبيق. إذا قام التطبيق بتعريف المستند على أنه السبب، سيسأل المستخدم ما إذا كان من غير العادي إرسال المستند مع مكدس المكالمة. يمكن للمستخدمين اختيار هذا السؤال عن علم. قد يكون لدى مسؤولي تكنولوجيا المعلومات متطلبات صارمة بشأن نقل المستندات واتخاذ القرار نيابة عن المستخدم عدم إرسال المستندات أبدا. يمكن تعيين التفضيل التالي لمنع إرسال المستندات، ولمنع المطالبة للمستخدم:
  
```defaults write com.microsoft.errorreporting IsAttachFilesEnabled -bool FALSE```

> [!NOTE]
> إذا **تم تعيين SendAllTelemetryEnabled** إلى **FALSE**، يتم تعطيل كل تقارير الأعاطل لهذه العملية. لتمكين الإبلاغ عن التعطل دون إرسال بيانات تتبع الاستخدام، يمكن تعيين التفضيل التالي: ```defaults write com.microsoft.errorreporting IsMerpEnabled -bool TRUE``` 
  
### <a name="updates"></a>التحديثات
  
تصدر Microsoft Office for Mac تحديثات منتظمة (عادة ما تكون مرة واحدة في الشهر). إننا نشجع المستخدمين والمسؤولين في تكنولوجيا المعلومات بشدة على تحديث الأجهزة لضمان تثبيت إصلاحات الأمان الأخيرة. في الحالات التي يرغب فيها مسؤولي تكنولوجيا المعلومات في التحكم في تحديثات الجهاز وإدارتها بشكل وثيق، يمكن تعيين التفضيل التالي لمنع عملية التحديث التلقائي من الكشف عن تحديثات المنتجات وتقديمها تلقائيا:
  
```defaults write com.microsoft.autoupdate2 HowToCheck -string 'Manual'```

### <a name="blocking-requests-with-a-firewallproxy"></a>حظر الطلبات باستخدام جدار حماية/وكيل
  
إذا كانت مؤسستك تقوم بحظر الطلبات إلى عناوين URL عبر جدار حماية أو خادم وكيل، فتأكد من تكوين عناوين URL المدرجة في هذا المستند كما هو مسموح به، أو حظر مدرج مع استجابة 40X (على سبيل المثال، 403 أو 404). ستسمح استجابة 40X للتطبيقات التي تم إدخالها في Office بقبول عدم القدرة على الوصول إلى المورد بطريقة سهلة، وستوفر تجربة مستخدم أسرع مقارنة بإسقاط الاتصال، مما يؤدي بدوره إلى إعادة محاولة العميل.
  
إذا كان الخادم الوكيل يتطلب المصادقة، سيتم إرجاع استجابة 407 إلى العميل. للحصول على أفضل تجربة، تأكد من أنك تستخدم Office for Mac 15.27 أو أي وقت لاحق، لأنها تتضمن تصحيحات معينة للعمل مع خوادم NTLM وKerberos.
  
  
## <a name="see-also"></a>راجع أيضًا

[نطاقات عناوين IP وعناوين URL في Office 365](urls-and-ip-address-ranges.md)

