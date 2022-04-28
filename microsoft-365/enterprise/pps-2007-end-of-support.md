---
title: مخطط نهاية الدعم ل PerformancePoint Server 2007
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- PSV120
- PDD140
- MET150
ms.assetid: 89d9feee-2285-419c-8c14-0f7f583536e0
f1.keywords:
- NOCSH
description: وصل PerformancePoint Server 2007 و ProClarity و SharePoint Server 2007 إلى نهاية الدعم. اقرأ هذه المقالة للمساعدة في التخطيط لترقية حل المعلومات المهنية.
ms.openlocfilehash: 381faab617828d3bb30106deaaae993ed8d2b786
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096337"
---
# <a name="performancepoint-server-2007-end-of-support-roadmap"></a>مخطط نهاية الدعم ل PerformancePoint Server 2007

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

وصلت Office 2007 خوادم وتطبيقات إلى نهاية دعمها، بما في ذلك الخوادم والتطبيقات التي قد تستخدمها كجزء من حلول المعلومات المهنية (BI). يسرد الجدول التالي تطبيقات BI المتأثرة:
  
|**تطبيقات Microsoft BI**|**تاريخ انتهاء دعم**|
|:-----|:-----|
|ProClarity Analytics Server 6.3 Service Pack 3  <br/> ProClarity Desktop Professional 6.3  <br/> ProClarity SharePoint Viewer 6.3  <br/> |11 يوليو2017  <br/> |
|SharePoint Server 2007 Service Pack 3  <br/> |10 أكتوبر 2017  <br/> |
|PerformancePoint Server 2007 Service Pack 3  <br/> |9 يناير / كانون الثاني 2018  <br/> |
   
لمزيد من المعلومات، راجع ["الموارد" لمساعدتك على الترقية من خوادم وعملاء Office 2007](upgrade-from-office-2007-servers-and-products.md).
  
## <a name="what-does-end-of-support-mean"></a>ماذا يعني *نهاية الدعم* ؟

مثل معظم منتجات Microsoft، يتمتع PerformancePoint Server 2007 SP3 وبرامج ProClarity وser 2007 SP3 SharePoint دورة حياة الدعم، حيث توفر Microsoft ميزات جديدة وتصحيحات الأخطاء وتحديثات الأمان. تستمر دورة حياة المنتج عادة لمدة 10 سنوات من الإصدار الأولي للمنتج. تعرف نهاية دورة الحياة هذه بانتهاء دعم المنتج. بما أن ProClarity و PerformancePoint Server و SharePoint Server 2007 قد وصلت إلى نهاية الدعم، لم تعد Microsoft توفر:
  
- الدعم التقني للمشاكل التي قد تحدث.
    
- إصلاحات الأخطاء للمشاكل التي يتم اكتشافها والتي قد تؤثر على استقرار الخوادم وإمكانية استخدامها.
    
- إصلاحات الأمان للثغرات الأمنية التي يتم اكتشافها والتي قد تجعل الخوادم أو التطبيقات عرضة للاختراقات الأمنية.
    
- تحديثات المنطقة الزمنية.
    
سيستمر تثبيت ProClarity و SharePoint Server 2007 SP3 و PerformancePoint Server 2007 SP3 في التشغيل على الرغم من انتهاء الدعم. ومع ذلك، نوصي بشدة بالرحل من هذه التطبيقات في أقرب وقت ممكن.
  
## <a name="what-are-my-options"></a>ما هي خياراتي؟

هناك الكثير من التغييرات على تطبيقات Microsoft BI منذ عام 2007، ولديك العديد من الخيارات التي يجب مراعاتها، كما هو ملخص في الجدول التالي.
  
|**إذا كنت تستخدم هذا ...**|**استكشاف هذه الخيارات ...**|**ضع هذا في الاعتبار ...**|
|:-----|:-----|:-----|
| إمكانات تحليلات مراقبة &amp; PerformancePoint Server 2007، بما في ذلك:<br/>- خادم مراقبة PerformancePoint <br/>- مصمم لوحة معلومات PerformancePoint<br/>- عارض لوحة المعلومات لخدمات SharePoint (يستخدم لعرض لوحات معلومات PerformancePoint وبطاقات الأداء والتقارير)<br/> |**Excel مع Excel في مستعرض** (في السحابة أو في الموقع). للحصول على نظرة عامة، راجع [قدرات المعلومات المهنية في Excel Microsoft 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx).<br/><br/> **Power BI** (في السحابة أو في الموقع). للحصول على نظرة عامة، راجع [ما هو Power BI؟](https://go.microsoft.com/fwlink/?linkid=841341) <br/><br/> **SQL Server Reporting Services** (محلي). للحصول على نظرة عامة، راجع [SQL Server Reporting Services (SSRS): إنشاء تقارير الجوال والمقسمة إلى صفحات ونشرها وإدارتها](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports). <br/><br/> **خدمات PerformancePoint** (محلي). للحصول على نظرة عامة، راجع [أحدث الميزات في خدمات PerformancePoint (SharePoint Server 2010).](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14)) <br/> |يتوفر Excel كحل عبر الإنترنت (مستند إلى السحابة) أو حل محلي. يمكن تلبية العديد من احتياجات التقارير ولوحة المعلومات مع Excel.  <br/><br/> يتوفر Power BI كحل عبر الإنترنت أو محليا. Power BI غير مضمن في Microsoft 365. ولكن يمكنك البدء في استخدام Power BI مجانا. في وقت لاحق، اعتمادا على استخدام البيانات واحتياجات العمل، يمكنك الترقية إلى Power BI Pro باستخدام Microsoft 365 E5.<br/> <br/> تعد خدمات التقارير خدمات PerformancePoint حلولا محلية. <br/><br/> يتوفر خدمات PerformancePoint في SharePoint Server 2010 و SharePoint Server 2013 و SharePoint Server 2016. <br/> <br/> لا تتوفر بعض الميزات وأنواع التقارير التي كانت متوفرة في PerformancePoint Server 2007 في Excel أو Power BI أو Reporting Services أو خدمات PerformancePoint. راجع الميزات المتوفرة لتحديد أفضل حل لاحتياجات عملك. <br/> |
| برنامج ProClarity، بما في ذلك:<br/>- ProClarity Desktop Professional<br/> - ProClarity Analytics Server<br/>- ProClarity SharePoint Viewer<br/> |**اعمل مع شريك Microsoft** لتحديد الحل الذي يلبي احتياجاتك على أفضل شكل. تفضل بزيارة [مركز شركاء Microsoft](https://go.microsoft.com/fwlink/?linkid=841249). <br/><br/> يمكنك أيضا استخدام Excel مع Excel في مستعرض أو Power BI أو SQL Server Reporting Services أو خدمات PerformancePoint.  <br/> |تتوفر العديد من ميزات برنامج ProClarity وليس جميعها في عروض Microsoft الأخرى، بما في ذلك Excel وPower BI وخدمات التقارير خدمات PerformancePoint.  <br/> |
|SharePoint Server 2007 KPIs (تسمى أيضا MOSS KPIs)  <br/> |**Excel باستخدام Excel Services**. للحصول على نظرة عامة، راجع [المعلومات المهنية في Excel و Excel Services (SharePoint Server 2013).](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |يمكن استخدام واجهات برمجة تطبيقات MOSS التي تم إنشاؤها باستخدام SharePoint Server 2007 في SharePoint Server 2010 و SharePoint Server 2013 و SharePoint Server 2016. ولكن لا يمكنك إنشاء مؤشرات KPIs MOSS جديدة.  <br/> |
|Excel 2007  <br/> |**Excel** (في السحابة أو في الموقع). للحصول على نظرة عامة، راجع [قدرات المعلومات المهنية في Excel Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/><br/> **Power BI** (في السحابة أو في الموقع). للحصول على نظرة عامة، راجع [ما هو Power BI؟](https://go.microsoft.com/fwlink/?linkid=841341) <br/> |يقدم كل من Excel وPower BI حلولا مستندة إلى السحابة ومحلية لمؤسستك، مع دعم مجموعة واسعة من مصادر البيانات.  <br/> |
   
### <a name="help-selecting-a-solution"></a>المساعدة في تحديد حل

مع توفر العديد من خيارات المعلومات المهنية، قد يبدو من المرهقة تحديد الخيار الأفضل. يتوفر لدينا دليل عبر الإنترنت لمساعدتك. راجع [اختيار أدوات Microsoft Business Intelligence (BI) للتحليل وإعداد التقارير](/sql/reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting).
  
### <a name="what-if-i-dont-upgrade-now"></a>ماذا لو لم أترقية الآن؟

يمكنك اختيار عدم الترقية على الفور. ستستمر الخوادم والتطبيقات الموجودة في التشغيل. ولكن لن تتلقى أي تحديثات أخرى، بما في ذلك تحديثات الأمان، منذ انتهاء الدعم. وإذا حدث خطأ ما في تطبيقات الخادم، فلن تتمكن من الحصول على المساعدة من الدعم التقني من Microsoft.
  
## <a name="how-do-i-plan-my-upgrade"></a>كيف أعمل التخطيط للترقية الخاصة بي؟

بعد استكشاف خيارات الترقية، تتمثل الخطوة التالية في إعداد خطة ترقية. تتضمن الأقسام التالية معلومات وموارد إضافية للمساعدة. لديك أربعة خيارات رئيسية، بما في ذلك خياران يعملان في السحابة أو في الموقع، واثنين من الخيارات المحلية فقط:
  
|**الخيار**|**في السحابة أو في أماكن العمل؟**|
|:-----|:-----|
|[Excel مع خادم SharePoint (محلي)](#excel-with-sharepoint-server-on-premises) <br/> |كل  <br/> |
|[Power BI](#use-power-bi-in-the-cloud-or-on-premises)<br/> |كل  <br/> |
|[خدمات التقارير](#use-reporting-services-on-premises) <br/> |محلي فقط  <br/> |
|[PerformancePoint Services](#use-performancepoint-services-on-premises) <br/> |محلي فقط  <br/> |
   
### <a name="use-excel-in-the-cloud-or-on-premises"></a>استخدام Excel (في السحابة أو في الموقع)

باستخدام Excel، والذي يعرف أيضا *باسم Excel Services* في SharePoint Server، يمكنك عرض المصنفات واستخدامها في نافذة المستعرض، حتى إذا لم يكن Excel مثبتا على الكمبيوتر. يمكنك استخدام Excel لإنشاء التقارير وبطاقات الأداء ولوحات المعلومات. بعد ذلك، شارك المصنفات مع الآخرين، الذين يمكنهم استخدام Excel في مستعرض، سواء كانوا يستخدمون SharePoint Online كجزء من Microsoft 365 أو SharePoint Server المحلي. يمكنك استخدام البيانات المخزنة محليا أو في السحابة، والتي تمكنك من استخدام مجموعة متنوعة من مصادر البيانات.
  
يقارن الجدول التالي المزايا الرئيسية لاستخدام Excel مع Microsoft 365 باستخدام Excel مع SharePoint Server. يتبع ذلك مزيد من المعلومات.
  
|**Excel مع Microsoft 365 (في السحابة)**|**Excel مع خادم SharePoint (محلي)**|
|:-----|:-----|
|**يمكنك الحصول على أحدث إصدار من Excel**. باستخدام Microsoft 365، يمكنك الحصول على أحدث إصدار من Excel، والذي يتضمن أنواع مخططات جديدة قوية، والقدرة على إنشاء المخططات والجداول بسرعة وسهولة، ودعم المزيد من مصادر البيانات. <br/> <br/> **الإعداد أبسط بكثير**. يتم تضمين Excel مع Microsoft 365 للأعمال، لذلك لا توجد أي مهمة شاقة من جانبك. قم بالتسجيل وتسجيل الدخول، وستكون قيد التشغيل بشكل أسرع وأكثر كفاءة مما إذا قمت بترقية الخوادم المحلية. <br/> <br/> **يمكن للأشخاص الوصول إلى مصنفاتهم في كل مكان**. يمكن للأشخاص عرض المصنفات بشكل آمن من أي مكان، باستخدام أجهزة الكمبيوتر والهاتف الذكي والكمبيوتر اللوحي. <br/> <br/> **هناك المزيد!** راجع [قدرات المعلومات المهنية في Excel Office 365](https://support.office.com/article/26c0548e-124c-4fd3-aab3-5f64568cb743.aspx). <br/> |**يمكنك إدارة الإعدادات العمومية**. بصفتك مسؤول SharePoint، يمكنك تحديد الإعدادات العمومية، مثل الأمان وموازنة التحميل وإدارة جلسة العمل والتخزين المؤقت في المصنف واتصالات البيانات الخارجية. <br/> <br/> **يمكنك استخدام Excel Services مع خدمات PerformancePoint**. يمكنك تكوين Excel Services خدمات PerformancePoint كجزء من تثبيت خادم SharePoint، وتضمين تقارير Excel Services في لوحات معلومات PerformancePoint. <br/> <br/> **هناك المزيد!** راجع [المعلومات المهنية في Excel Excel Services (SharePoint Server 2013).](https://support.office.com/article/2740f10c-579d-4b40-a1d9-7beb5d38547c.aspx) <br/> |
   
#### <a name="excel-with-microsoft-365-in-the-cloud"></a>Excel مع Microsoft 365 (في السحابة)

إذا انتقلت إلى Microsoft 365، فستتوفر لديك أحدث الخدمات والتطبيقات، بما في ذلك Excel 2016. خدمات PerformancePoint غير متوفر في Microsoft 365، لذلك ستقوم باستبدال محتوى لوحة معلومات PerformancePoint بمصنفات Excel أو تقارير أخرى. والخبر السار هو أن Excel 2016 لديها الكثير من أنواع المخططات الجديدة، وأنه من الأسهل من أي وقت مضى إنشاء لوحات معلومات مثيرة للإعجاب في Excel. وتتم إضافة الميزات الجديدة بانتظام. لمعرفة المزيد، اطلع على [أحدث الميزات في Excel 2016 Windows](https://support.office.com/article/5fdb9208-ff33-45b6-9e08-1f5cdb3a6c73.aspx).
  
أيضا، إذا اشتريت 50 مقعد أو أكثر من Microsoft 365، يمكن لفريق Microsoft FastTrack مساعدتك في الإعداد. لمعرفة المزيد، تفضل بزيارة [FastTrack](https://www.microsoft.com/fasttrack/microsoft-365).
  
#### <a name="excel-with-sharepoint-server-on-premises"></a>Excel مع خادم SharePoint (محلي)

إذا قمت بالترقية إلى إصدار أحدث من SharePoint، يمكنك استخدام Excel مع Excel Services أو في مستعرض، كما يلي:
  
- Excel Services في SharePoint Server 2010
    
- Excel Services في SharePoint Server 2013
    
- تم تثبيت Excel، الذي يعد جزءا من Office Online Server، بشكل منفصل عن SharePoint Server 2016
    
يمكنك تكوين خدمات PerformancePoint في الإصدار الجديد من SharePoint Server أيضا، واستخدامه مع Excel.
  
لمعرفة المزيد حول خيارات الترقية SharePoint، راجع [SharePoint مخطط نهاية الدعم لخادم 2007](sharepoint-2007-end-of-support.md).
  
لمعرفة المزيد حول Excel Services، راجع [نظرة عامة على Excel Services (SharePoint Server 2010).](/previous-versions/office/sharepoint-server-2010/ee424405(v=office.14))
  
### <a name="use-power-bi-in-the-cloud-or-on-premises"></a>استخدام Power BI (في السحابة أو في الموقع)

Power BI عبارة عن مجموعة من أدوات تحليلات الأعمال لتحليل البيانات ومشاركة الرؤى. باستخدام Power BI، يمكنك استخدام مصادر البيانات المحلية أو عبر الإنترنت لإنشاء تقارير ولوحات معلومات تفاعلية. يمكن للأشخاص عرض التقارير ولوحات المعلومات واستخدامها على أجهزة الكمبيوتر أو الأجهزة المحمولة الخاصة بهم.
  
لا يعد Power BI جزءا من خادم Microsoft 365 أو SharePoint. إنه عرض منفصل يتضمن Power BI Desktop وبوابات Power BI خدمة Power BI. يتكامل Power BI أيضا مع SharePoint Online. يمكنك البدء باستخدام Power BI مجانا. استنادا إلى استخدام البيانات واحتياجات العمل، يمكنك الترقية لاحقا إلى Power BI Pro باستخدام Microsoft 365 E5. لمعرفة المزيد، راجع [ما هو Power BI؟](https://go.microsoft.com/fwlink/?linkid=841341)
  
### <a name="use-reporting-services-on-premises"></a>استخدام Reporting Services (محلي)

يوفر SQL Server Reporting Services حلا قويا لإعداد التقارير. يمكنك تكوين خدمات التقارير إما في الوضع الأصلي أو الوضع المتكامل SharePoint. يمكنك استخدام العديد من الأدوات المختلفة لكتابة التقارير، بما في ذلك مصمم التقارير مُنشئ التقارير وPower View. باستخدام أحدث إصدار من SQL Server، يمكنك أيضا استخدام SQL Server Publisher "تقرير الجوال" لتقديم التقارير التي تتدرج إلى أي حجم شاشة. يتيح هذا للعارضين استخدام التقارير على أجهزتهم المحمولة. لمعرفة المزيد، راجع [SQL Server Reporting Services (SSRS): إنشاء تقارير الجوال والمقسمة إلى صفحات ونشرها وإدارتها](/sql/reporting-services/create-deploy-and-manage-mobile-and-paginated-reports).
  
### <a name="use-performancepoint-services-on-premises"></a>استخدام خدمات PerformancePoint (محلي)

تم بيع PerformancePoint Server 2007 بشكل منفصل عن SharePoint Server 2007. بدءا من SharePoint Server 2010، خدمات PerformancePoint هو تطبيق خدمة في SharePoint Server. لذلك، لا تحتاج إلى شراء تراخيص أو أجهزة خادم منفصلة لاستخدام خدمات PerformancePoint.
  
للانتقال من PerformancePoint Server 2007 إلى خدمات PerformancePoint، يمكنك الانتقال إلى إصدار أحدث من SharePoint Server وتكوين خدمات PerformancePoint. يحدد إصدار SharePoint Server الذي تنتقل إليه ما إذا كان يمكنك استيراد محتوى لوحة المعلومات الموجود من PerformancePoint Server 2007 إلى خدمات PerformancePoint.
  
- إذا قمت بالترقية إلى SharePoint Server 2010، يمكنك استيراد محتوى لوحة معلومات PerformancePoint من PerformancePoint Server 2007 إلى خدمات PerformancePoint في SharePoint Server 2010. لمعرفة المزيد، راجع [معالج الاستيراد: محتوى PerformancePoint Server 2007 إلى SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/ee681485(v=office.14)).
    
- إذا انتقلت إلى SharePoint Server 2013 أو SharePoint Server 2016، فستحتاج على الأرجح إلى إنشاء محتوى لوحة معلومات جديد (مصادر البيانات والتقارير وبطاقات الأداء وصفحات لوحة المعلومات).
    
لبدء استخدام خطة الترقية خدمات PerformancePoint، راجع الموارد التالية:
  
- [مخطط نهاية دعم SharePoint Server 2007](sharepoint-2007-end-of-support.md)
    
- عندما تعرف أي إصدار من SharePoint تنتقل إليه، راجع المقالة المقابلة خدمات PerformancePoint:
    
  - [التخطيط خدمات PerformancePoint (SharePoint Server 2010)](/previous-versions/office/sharepoint-server-2010/ee681486(v=office.14))
    
  - [نظرة عامة على خدمات PerformancePoint في SharePoint Server 2013](/sharepoint/administration/performancepoint-services-overview)
    
  - [نظرة عامة على خدمات PerformancePoint في SharePoint Server 2016](/sharepoint/administration/performancepoint-services-overview)
    
عند الترقية إلى خدمات PerformancePoint، تحصل على العديد من الميزات والتحسينات الجديدة. يوفر خدمات PerformancePoint بطاقات أداء محسنة؛ مرئيات جديدة، مثل تقرير تفاصيل شجرة التحليل وتفاصيل KPI؛ والمزيد من أنواع المخططات؛ وقدرات تصفية تحليل معلومات الوقت بشكل أفضل؛ وتحسين التوافق مع إمكانية وصول ذوي الاحتياجات الخاصة. لمعرفة المزيد، اطلع على أحدث [الميزات في خدمات PerformancePoint (SharePoint Server 2010).](/previous-versions/office/sharepoint-server-2010/ee661741(v=office.14))
  
## <a name="where-can-i-get-help-with-my-upgrade"></a>أين يمكنني الحصول على المساعدة في الترقية؟

سواء قمت بالترقية محليا أو الانتقال إلى Microsoft 365، نوصي بالعمل مع شريك Microsoft. يمكن أن يساعدك الشريك المؤهل في تحديد الحل الذي يلبي احتياجات عملك ويساعدك في النشر. تفضل بزيارة [مركز شركاء Microsoft](https://go.microsoft.com/fwlink/?linkid=841249)، واستخدم عوامل تصفية البحث للعثور على موفر حلول.
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[موارد لمساعدتك على الترقية من خوادم وعملاء Office 2007](upgrade-from-office-2007-servers-and-products.md)