---
title: التوجيه باستخدام ExpressRoute لـ Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: في هذه المقالة، تعرف على متطلبات توجيه Azure ExpressRoute ودوائره ومجالات التوجيه لاستخدامها مع Office 365.
ms.openlocfilehash: c63e3ae14c9b369265622f17c2e542818620aa3e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092900"
---
# <a name="routing-with-expressroute-for-office-365"></a>التوجيه باستخدام ExpressRoute لـ Office 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

لفهم نسبة استخدام الشبكة التوجيه بشكل صحيح إلى Office 365 باستخدام Azure ExpressRoute، ستحتاج إلى فهم ثابت [لمتطلبات توجيه ExpressRoute](/azure/expressroute/expressroute-routing) الأساسية [ودوائر ExpressRoute ومجالات التوجيه](/azure/expressroute/expressroute-circuit-peerings). تحدد هذه المبادئ الأساسية لاستخدام ExpressRoute التي سيعتمد عليها العملاء Office 365.
  
تتضمن بعض العناصر الرئيسية في المقالات أعلاه التي ستحتاج إلى فهمها ما يلي:
  
- لا يتم تعيين دوائر ExpressRoute إلى بنية أساسية فعلية محددة، ولكنها اتصال منطقي يتم إجراؤه في موقع إقران واحد من قبل Microsoft وموفر إقران بالنيابة عنك.

- هناك تعيين 1:1 بين دائرة ExpressRoute ومفتاح العميل.

- يمكن أن تدعم كل دائرة علاقتي تناظر مستقلتين (تناظر Azure Private، وإقران Microsoft)؛ يتطلب Office 365 تناظر Microsoft.

- تحتوي كل دائرة على نطاق ترددي ثابت تتم مشاركته عبر جميع علاقات التناظر.

- يجب التحقق من صحة أي عناوين IPv4 عامة وأرقام AS عامة سيتم استخدامها لدائرة ExpressRoute على أنها مملوكة لك، أو تعيينها لك حصريا من قبل مالك نطاق العناوين.

- دوائر ExpressRoute الظاهرية متكررة عالميا وستتبع ممارسات توجيه BGP القياسية. هذا هو السبب في أننا نوصي بدائرة فعلية لكل خروج إلى الموفر الخاص بك في تكوين نشط/نشط.

راجع [صفحة الأسئلة المتداولة](/azure/expressroute/expressroute-faqs) للحصول على مزيد من المعلومات حول الخدمات المدعومة والتكاليف وتفاصيل التكوين. راجع [مقالة مواقع ExpressRoute](/azure/expressroute/expressroute-locations) للحصول على معلومات حول قائمة موفري الاتصال الذين يقدمون دعم إقران Microsoft. لقد سجلنا أيضا سلسلة [Azure ExpressRoute](https://channel9.msdn.com/series/aer) مكونة من 10 أجزاء لسلسلة تدريب Office 365 على القناة 9 للمساعدة في شرح المفاهيم بشكل أكثر شمولا.
  
## <a name="ensuring-route-symmetry"></a>ضمان تماثل المسار

يمكن الوصول إلى خوادم Office 365 الأمامية على كل من الإنترنت وExpressRoute. تفضل هذه الخوادم العودة إلى دوائر ExpressRoute المحلية عند توفرهما. ولهذا السبب، هناك إمكانية عدم تماثل المسار إذا كانت نسبة استخدام الشبكة من شبكتك تفضل التوجيه عبر دوائر الإنترنت الخاصة بك. المسارات غير المتماثلة هي مشكلة لأن الأجهزة التي تقوم بفحص حزم البيانات ذات الحالة يمكنها حظر نسبة استخدام الشبكة المرجعة التي تتبع مسارا مختلفا عن الحزم الصادرة المتبعة.
  
بغض النظر عما إذا كنت تبدأ اتصالا Office 365 عبر الإنترنت أو ExpressRoute، يجب أن يكون المصدر عنوانا قابلا للتوجيه بشكل عام. مع تناظر العديد من العملاء مباشرة مع Microsoft، فإن وجود عناوين خاصة حيث يكون التكرار ممكنا بين العملاء غير ممكن.
  
فيما يلي سيناريوهات حيث سيتم بدء الاتصالات من Office 365 إلى الشبكة المحلية. لتبسيط تصميم الشبكة، نوصي بتوجيه ما يلي عبر مسار الإنترنت.
  
- خدمات SMTP مثل البريد من مستأجر Exchange Online إلى مضيف محلي أو SharePoint Online Mail المرسل من SharePoint Online إلى مضيف محلي. يتم استخدام بروتوكول SMTP على نطاق أوسع داخل شبكة Microsoft من بادئات المسار المشتركة عبر دوائر ExpressRoute والإعلان عن خوادم SMTP المحلية عبر ExpressRoute سوف تسبب فشلا مع هذه الخدمات الأخرى.

- ADFS أثناء التحقق من صحة كلمة المرور لتسجيل الدخول.

- [Exchange Server عمليات النشر المختلطة](/exchange/exchange-hybrid).

- [SharePoint البحث المختلط المتحد](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS المختلط](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business الاتحاد المختلط](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) و/أو [Skype for Business](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype for Business Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

لكي تقوم Microsoft بالرجوع إلى شبكتك لتدفقات نسبة استخدام الشبكة ثنائية الاتجاه هذه، يجب مشاركة مسارات BGP إلى أجهزتك المحلية مع Microsoft. عند الإعلان عن بادئات المسار إلى Microsoft عبر ExpressRoute، يجب اتباع أفضل الممارسات التالية:

1) لا تعلن عن نفس بادئة مسار عنوان IP العام إلى الإنترنت العام وعبر ExpressRoute. من المستحسن أن تكون إعلانات بادئة مسار IP BGP إلى Microsoft عبر ExpressRoute من نطاق لا يتم الإعلان عنه إلى الإنترنت على الإطلاق. إذا لم يكن من الممكن تحقيق ذلك بسبب مساحة عنوان IP المتوفرة، فمن الضروري التأكد من الإعلان عن نطاق أكثر تحديدا عبر ExpressRoute من أي دوائر إنترنت.

2) استخدم تجمعات عناوين IP NAT منفصلة لكل دائرة ExpressRoute وفصلها عن دوائر الإنترنت الخاصة بك.

3) سيؤدي أي مسار يتم الإعلان عنه إلى Microsoft إلى جذب نسبة استخدام الشبكة من أي خادم في شبكة Microsoft، وليس فقط تلك التي يتم الإعلان عن المسارات لشبكتك عبر ExpressRoute. الإعلان فقط عن المسارات إلى الخوادم حيث يتم تعريف سيناريوهات التوجيه وفهمها جيدا من قبل فريقك. الإعلان عن بادئات مسار عنوان IP منفصلة في كل من دوائر ExpressRoute المتعددة من شبكتك.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>تحديد التطبيقات والميزات التي يتم توجيهها عبر ExpressRoute

عند تكوين علاقة تناظر باستخدام مجال توجيه إقران Microsoft وتتم الموافقة على الوصول المناسب، ستتمكن من رؤية جميع خدمات PaaS وSaaS المتوفرة عبر ExpressRoute. يمكن إدارة خدمات Office 365 المصممة ل ExpressRoute مع [مجتمعات BGP](./bgp-communities-in-expressroute.md) أو [عوامل تصفية المسار](/azure/expressroute/how-to-routefilter-portal).
  
يتم سرد كل من ميزات Office 365 المتوفرة باستخدام إقران Microsoft في [مقالة نقاط النهاية Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) حسب نوع التطبيق وFQDN. السبب في استخدام FQDN في الجداول هو السماح للعملاء بإدارة نسبة استخدام الشبكة باستخدام ملفات PAC أو تكوينات الوكيل الأخرى، راجع دليلنا [لإدارة نقاط النهاية Office 365](./managing-office-365-endpoints.md) على سبيل المثال ملفات PAC.
  
في بعض الحالات، استخدمنا مجال حرف بدل حيث يتم الإعلان عن واحد أو أكثر من FQDNs الفرعية بشكل مختلف عن مجال أحرف البدل ذات المستوى الأعلى. يحدث ذلك عادة عندما يمثل حرف البدل قائمة طويلة من الخوادم التي يتم الإعلان عنها كلها إلى ExpressRoute والإنترنت، بينما يتم الإعلان عن مجموعة فرعية صغيرة من الوجهات فقط إلى الإنترنت، أو العكس. راجع الجداول أدناه لفهم مكان الاختلافات.
  
يعرض هذا الجدول FQDNs حرف البدل التي يتم الإعلان عنها لكل من الإنترنت وAzure ExpressRoute إلى جانب FQDNs الفرعية التي يتم الإعلان عنها فقط على الإنترنت.

|**مجال أحرف البدل المعلن عنها لدوائر ExpressRoute والإنترنت**|**يتم الإعلان عن شبكة FQDN الفرعية لدوائر الإنترنت فقط**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

عادة ما تهدف ملفات PAC إلى إرسال طلبات الشبكة إلى نقاط النهاية المعلن عنها في ExpressRoute مباشرة إلى الدائرة وجميع طلبات الشبكة الأخرى إلى وكيلك. إذا كنت تقوم بتكوين ملف PAC مثل هذا، فقم بإنشاء ملف PAC بالترتيب التالي:
  
1. قم بتضمين FQDNs الفرعية من العمود الثاني في الجدول أعلاه في أعلى ملف PAC الخاص بك، وإرسال نسبة استخدام الشبكة نحو وكيلك. لقد أنشأنا نموذج ملف PAC لاستخدامه في مقالتنا حول [إدارة نقاط النهاية Office 365](./managing-office-365-endpoints.md).

2. قم بتضمين جميع FQDNs التي تم وضع علامة عليها ل ExpressRoute في [هذه المقالة](./urls-and-ip-address-ranges.md) أسفل القسم الأول، وإرسال نسبة استخدام الشبكة مباشرة إلى دائرة ExpressRoute.

3. قم بتضمين أي نقاط نهاية شبكة أخرى أو قواعد أسفل هذين الإدخالين، وإرسال نسبة استخدام الشبكة نحو الوكيل الخاص بك.

يعرض هذا الجدول مجالات أحرف البدل التي يتم الإعلان عنها إلى دوائر الإنترنت فقط إلى جانب FQDNs الفرعية التي يتم الإعلان عنها إلى دوائر Azure ExpressRoute والإنترنت. بالنسبة لملف PAC أعلاه، يتم سرد FQDNs في العمود 2 في الجدول أدناه على أنها يتم الإعلان عنها إلى ExpressRoute في الارتباط المشار إليه، ما يعني أنها سيتم تضمينها في المجموعة الثانية من الإدخالات في الملف.

|**مجال أحرف البدل المعلن عنها لدوائر الإنترنت فقط**|**تم الإعلان عن شبكة FQDN الفرعية لدوائر ExpressRoute والإنترنت**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>توجيه Office 365 نسبة استخدام الشبكة عبر الإنترنت وExpressRoute

لتوجيه التطبيق Office 365 الذي تختاره، ستحتاج إلى تحديد عدد من العوامل الرئيسية.
  
1. مقدار النطاق الترددي الذي سيتطلبه التطبيق. أخذ العينات من الاستخدام الحالي هو الأسلوب الوحيد الموثوق به لتحديد هذا في مؤسستك.

2. موقع (مواقع) الخروج الذي تريد أن تغادر نسبة استخدام الشبكة منه. يجب أن تخطط لتقليل زمن انتقال الشبكة للاتصال Office 365 لأن هذا سيؤثر على الأداء. نظرا لأن Skype for Business تستخدم الصوت والفيديو في الوقت الحقيقي، فإنها عرضة لزمن انتقال ضعيف للشبكة.

3. إذا كنت تريد أن تستخدم كل مواقع الشبكة أو مجموعة فرعية منها ExpressRoute.

4. المواقع التي يقدم منها موفر الشبكة الذي اخترته ExpressRoute.

بمجرد تحديد الإجابات على هذه الأسئلة، يمكنك توفير دائرة ExpressRoute تلبي احتياجات النطاق الترددي والموقع. لمزيد من المساعدة في تخطيط الشبكة، راجع [دليل ضبط الشبكة Office 365](./network-planning-and-performance.md) [ودراسة الحالة حول كيفية تعامل Microsoft مع تخطيط أداء الشبكة](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>مثال 1: موقع جغرافي واحد
  
هذا المثال هو سيناريو لشركة وهمية تسمى Trey Research لديها موقع جغرافي واحد.
  
يسمح للموظفين في Trey Research فقط بالاتصال بالخدمات ومواقع الويب على الإنترنت التي يسمح بها قسم الأمان بشكل صريح على زوج من الوكلاء الخارجيين الذين يقعون بين شبكة الشركة و ISP الخاص بهم.
  
تخطط Trey Research لاستخدام Azure ExpressRoute Office 365 وتدرك أن بعض نسبة استخدام الشبكة مثل نسبة استخدام الشبكة الموجهة لشبكات تسليم المحتوى لن تكون قادرة على التوجيه عبر ExpressRoute للاتصال Office 365. نظرا لأن جميع نسبة استخدام الشبكة توجه بالفعل إلى أجهزة الوكيل بشكل افتراضي، ستستمر هذه الطلبات في العمل كما كانت من قبل. بعد أن تحدد Trey Research أنها يمكنها تلبية متطلبات توجيه Azure ExpressRoute، فإنها تستمر في إنشاء دائرة وتكوين التوجيه وربط دائرة ExpressRoute الجديدة بشبكة ظاهرية. بمجرد وجود تكوين Azure ExpressRoute الأساسي، يستخدم Trey Research [ملف PAC #2 الذي ننشره](./managing-office-365-endpoints.md) لتوجيه نسبة استخدام الشبكة مع البيانات الخاصة بالعميل عبر ExpressRoute المباشر للاتصالات Office 365.
  
كما هو موضح في الرسم التخطيطي التالي، يمكن ل Trey Research تلبية متطلبات توجيه نسبة استخدام الشبكة Office 365 عبر الإنترنت ومجموعة فرعية من نسبة استخدام الشبكة عبر ExpressRoute باستخدام مجموعة من تغييرات تكوين الوكيل الصادر والتوجيه.
  
1. باستخدام [ملف PAC #2 ننشره](./managing-office-365-endpoints.md) لتوجيه نسبة استخدام الشبكة من خلال نقطة خروج منفصلة للإنترنت ل Azure ExpressRoute Office 365.

2. يتم تكوين العملاء مع مسار افتراضي نحو وكلاء Trey Research.

في هذا السيناريو المثال، تستخدم Trey Research جهاز وكيل صادر. وبالمثل، قد يرغب العملاء الذين لا يستخدمون Azure ExpressRoute Office 365 في استخدام هذه التقنية لتوجيه نسبة استخدام الشبكة استنادا إلى تكلفة فحص نسبة استخدام الشبكة الموجهة لنقاط النهاية عالية الحجم المعروفة.
  
أعلى عدد من FQDNs ل Exchange Online و SharePoint Online و Skype for Business Online هي التالية:
  
![شبكة حافة عميل ExpressRoute.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com، outlook.office.com

- \<tenant-name\>.sharepoint.com، \<tenant-name\>-my.sharepoint.com، \<tenant-name\>-\<app\>.sharepoint.com

- \*.Lync.com جنبا إلى جنب مع نطاقات IP لنسبة استخدام الشبكة غير TCP

- \*broadcast.officeapps.live.com، \*excel.officeapps.live.com، \*onenote.officeapps.live.com، \*powerpoint.officeapps.live.com، \*view.officeapps.live.com، \*visio.officeapps.live.com، \*word-edit.officeapps.live.com، \*word-view.officeapps.live.com، office.live.com

تعرف على المزيد حول [نشر إعدادات الوكيل وإدارتها في Windows 8](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) وضمان [عدم تقييد الوكيل Office 365](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
مع دائرة ExpressRoute واحدة، لا توجد قابلية وصول عالية ل Trey Research. في حالة فشل زوج أجهزة Edge المتكررة من Trey التي تخدم اتصال ExpressRoute، لا توجد دائرة ExpressRoute إضافية للفشل فيها. وهذا يترك Trey Research في مشكلة لأن الفشل في الإنترنت سيتطلب إعادة تكوين يدوي وفي بعض الحالات عناوين IP جديدة. إذا أراد Trey إضافة قابلية وصول عالية، فإن الحل الأبسط هو إضافة دوائر ExpressRoute إضافية لكل موقع وتكوين الدوائر بطريقة نشطة/نشطة.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>توجيه ExpressRoute Office 365 مع مواقع متعددة

السيناريو الأخير، توجيه نسبة استخدام الشبكة Office 365 عبر ExpressRoute هو الأساس لبنية توجيه أكثر تعقيدا. بغض النظر عن عدد المواقع، فإن عدد القارات التي توجد فيها هذه المواقع، وعدد دوائر ExpressRoute، وما إلى ذلك، ستكون هناك حاجة إلى القدرة على توجيه بعض نسبة استخدام الشبكة إلى الإنترنت وبعض نسبة استخدام الشبكة عبر ExpressRoute.
  
تتضمن الأسئلة الإضافية التي يجب الإجابة عليها للعملاء الذين يعانون من مواقع متعددة في مناطق جغرافية متعددة ما يلي:
  
1. هل تحتاج إلى دائرة ExpressRoute في كل موقع؟ إذا كنت تستخدم Skype for Business Online أو كنت مهتما بحساسية زمن الانتقال SharePoint Online أو Exchange Online، يوصى بزوج متكرر من دوائر ExpressRoute النشطة/النشطة في كل موقع. راجع Skype for Business دليل جودة الوسائط والاتصال بالشبكة للحصول على مزيد من التفاصيل.

2. إذا لم تكن دائرة ExpressRoute متوفرة في منطقة معينة، فكيف يجب Office 365 توجيه نسبة استخدام الشبكة الموجهة؟

3. ما هي الطريقة المفضلة لدمج نسبة استخدام الشبكة في حالة الشبكات التي تحتوي على العديد من المواقع الصغيرة؟

يمثل كل من هذه تحديا فريدا يتطلب منك تقييم شبكتك والخيارات المتوفرة من Microsoft.

|**النظر**|**مكونات الشبكة المراد تقييمها**|
|:-----|:-----|
|دوائر في أكثر من موقع واحد  <br/> |نوصي بتكوين دائرتين على الأقل بطريقة نشطة/نشطة.  <br/> يجب مقارنة احتياجات التكلفة وزمن الانتقال والنطاق الترددي.  <br/> استخدم تكلفة مسار BGP وملفات PAC و NAT لإدارة التوجيه باستخدام دوائر متعددة.  <br/> |
|التوجيه من المواقع دون دائرة ExpressRoute  <br/> |نوصي بالانحدار وحل DNS بالقرب من الشخص الذي يبدأ طلب Office 365.  <br/> يمكن استخدام إعادة توجيه DNS للسماح للمكاتب البعيدة باكتشاف نقطة النهاية المناسبة.  <br/> يجب أن يكون لدى العملاء في المكتب البعيد مسار متوفر يوفر الوصول إلى دائرة ExpressRoute.  <br/> |
|دمج المكاتب الصغيرة  <br/> |وينبغي مقارنة النطاق الترددي المتوفر واستخدام البيانات بعناية.  <br/> |

> [!NOTE]
> تفضل Microsoft ExpressRoute على الإنترنت إذا كان المسار متوفرا بغض النظر عن الموقع الفعلي.
  
ويجب مراعاة كل من هذه الاعتبارات لكل شبكة فريدة. وفيما يلي مثال على ذلك.
  
### <a name="example-2-multi-geographic-locations"></a>مثال 2: مواقع جغرافية متعددة
  
هذا المثال هو سيناريو لشركة وهمية تسمى "Humongous Insurance" لديها مواقع جغرافية متعددة.
  
يتم توزيع التأمين الهمومي جغرافيا مع المكاتب في جميع أنحاء العالم. يريدون تنفيذ Azure ExpressRoute Office 365 للحفاظ على معظم نسبة استخدام الشبكة Office 365 على اتصالات الشبكة المباشرة. كما أن شركة Humongous Insurance لديها مكاتب في قارتين إضافيتين. سيحتاج الموظفون في المكتب البعيد حيث لا يكون ExpressRoute ممكنا إلى العودة إلى أحد المرافق الأساسية أو كليهما لاستخدام اتصال ExpressRoute.
  
المبدأ التوجيهي هو الحصول على Office 365 نسبة استخدام الشبكة الموجهة إلى مركز بيانات Microsoft في أسرع وقت ممكن. في هذا المثال، يجب أن يقرر Humongous Insurance ما إذا كان يجب على مكاتبهم البعيدة التوجيه عبر الإنترنت للوصول إلى مركز بيانات Microsoft عبر أي اتصال في أسرع وقت ممكن أو ما إذا كان يجب توجيه مكاتبهم البعيدة عبر شبكة داخلية للوصول إلى مركز بيانات Microsoft عبر اتصال ExpressRoute في أسرع وقت ممكن.
  
تم تصميم مراكز بيانات Microsoft وشبكاتها وبنية تطبيقاتها لتأخذ اتصالات متباينة عالميا وتخدمها بأكثر طريقة ممكنة. هذه هي واحدة من أكبر الشبكات في العالم. لن تتمكن الطلبات الموجهة Office 365 التي تظل على شبكات العملاء لفترة أطول من اللازم من الاستفادة من هذه البنية.
  
في حالة شركة Humongous Insurance، يجب أن تستمر اعتمادا على التطبيقات التي تنوي استخدامها عبر ExpressRoute. على سبيل المثال، إذا كان عميلا Skype for Business Online، أو يخطط لاستخدام اتصال ExpressRoute عند الاتصال باجتماعات Skype for Business Online الخارجية، فإن التصميم الموصى به في Skype for Business  تتمثل جودة الوسائط عبر الإنترنت ودليل اتصال الشبكة في توفير دائرة ExpressRoute إضافية للموقع الثالث. قد يكون هذا أكثر تكلفة من منظور الشبكات؛ ومع ذلك، قد يؤدي توجيه الطلبات من قارة إلى أخرى قبل التسليم إلى مركز بيانات Microsoft إلى تجربة سيئة أو غير قابلة للاستخدام أثناء Skype for Business عبر الإنترنت من الاجتماعات والاتصالات.
  
إذا كان Humongous Insurance لا يستخدم أو لا يخطط لاستخدام Skype for Business Online بأي طريقة، فقد يكون توجيه Office 365 نسبة استخدام الشبكة الموجهة مرة أخرى إلى قارة ذات اتصال ExpressRoute ممكنا على الرغم من أنه قد يتسبب في زمن انتقال غير ضروري أو ازدحام TCP. في كلتا الحالتين، يوصى بتوجيه حركة مرور الإنترنت الموجهة إلى الإنترنت في الموقع المحلي للاستفادة من شبكات تسليم المحتوى التي يعتمد عليها Office 365.
  
![ExpressRoute متعدد الجغرافيا.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
عندما تخطط شركة Hongous Insurance لاستراتيجيتها متعددة الجغرافيا، هناك العديد من الأشياء التي يجب مراعاتها حول حجم الدائرة وعدد الدوائر وتجاوز الفشل وما إلى ذلك.
  
مع وجود ExpressRoute في موقع واحد مع مناطق متعددة تحاول استخدام الدائرة، تريد شركة Humongous Insurance التأكد من إرسال الاتصالات Office 365 من المكتب البعيد إلى مركز بيانات Office 365 الأقرب إلى المقر الرئيسي وتلقيها من قبل موقع المقر الرئيسي. للقيام بذلك، ينفذ Humongous Insurance إعادة توجيه DNS لتقليل عدد الرحلات الدائرية وبحث DNS المطلوب لإنشاء الاتصال المناسب ببيئة Office 365 الأقرب إلى نقطة خروج الإنترنت في المقر الرئيسي. وهذا يمنع العميل من حل خادم واجهة أمامية محلية ويضمن Front-End الخادم الذي يتصل به الشخص ليكون بالقرب من المقر الرئيسي حيث يقوم Humongous Insurance بالتناظر مع Microsoft. يمكنك أيضا تعلم [تعيين معاد توجيه شرطي لاسم مجال](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
في هذا السيناريو، ستحل نسبة استخدام الشبكة من المكتب البعيد البنية الأساسية Office 365 الأمامية في أمريكا الشمالية وتستخدم Office 365 للاتصال بخوادم الواجهة الخلفية وفقا لبنية تطبيق Office 365. على سبيل المثال، ستقوم Exchange Online بإنهاء الاتصال في أمريكا الشمالية وستتصل خوادم الواجهة الأمامية هذه بخادم علبة البريد الخلفية أينما كان المستأجر. جميع الخدمات لديها خدمة الباب الأمامي الموزعة على نطاق واسع تتكون من وجهات أحادية الإرسال و anycast.
  
إذا كان لدى هومونغوس مكاتب رئيسية في قارات متعددة، يوصى بما لا يقل عن دائرتين نشطة/نشطة لكل منطقة من أجل تقليل زمن الانتقال للتطبيقات الحساسة مثل Skype for Business Online. إذا كانت جميع المكاتب في قارة واحدة، أو لا تستخدم التعاون في الوقت الحقيقي، فإن وجود نقطة خروج موحدة أو موزعة هو قرار خاص بالعميل. عند توفر دوائر متعددة، سيضمن توجيه BGP تجاوز الفشل إذا أصبحت أي دائرة واحدة غير متوفرة.
  
تعرف على المزيد حول [تكوينات التوجيه](/azure/expressroute/expressroute-config-samples-routing) النموذجية و [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>التوجيه الانتقائي باستخدام ExpressRoute

قد تكون هناك حاجة إلى التوجيه الانتقائي باستخدام ExpressRoute لأسباب مختلفة، مثل الاختبار، طرح ExpressRoute لمجموعة فرعية من المستخدمين. هناك العديد من الأدوات التي يمكن للعملاء استخدامها لتوجيه حركة مرور الشبكة Office 365 بشكل انتقائي عبر ExpressRoute:
  
1. **تصفية/فصل المسار** - السماح لمسارات BGP Office 365 عبر ExpressRoute إلى مجموعة فرعية من الشبكات الفرعية أو أجهزة التوجيه الخاصة بك. يتم توجيه هذا بشكل انتقائي حسب مقطع شبكة العملاء أو موقع المكتب الفعلي. هذا أمر شائع للإطلاق التدريجي ل ExpressRoute Office 365 ويتم تكوينه على أجهزة BGP.

2. **ملفات PAC/عناوين URL** - توجيه نسبة استخدام الشبكة الموجهة Office 365 ل FQDNs معينة لتوجيهها على مسار معين. يؤدي هذا بشكل انتقائي إلى توجيه الكمبيوتر العميل كما هو محدد بواسطة [نشر ملف PAC](./managing-office-365-endpoints.md).

3. **تصفية** -  المسار [تعد عوامل تصفية المسار](/azure/expressroute/how-to-routefilter-portal) طريقة لاستهلاك مجموعة فرعية من الخدمات المدعومة من خلال تناظر Microsoft.

4. **مجتمعات BGP** - تسمح التصفية استنادا إلى [علامات مجتمع BGP](./bgp-communities-in-expressroute.md) للعميل بتحديد التطبيقات Office 365 التي تجتاز ExpressRoute وأيها يجتاز الإنترنت.

فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[تقييم اتصال الشبكة Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute ل Office 365](azure-expressroute.md)
  
[إدارة ExpressRoute للاتصال Office 365](managing-expressroute-for-connectivity.md)
  
[تخطيط الشبكة باستخدام ExpressRoute لـ Office 365](network-planning-with-expressroute.md)
  
[تنفيذ ExpressRoute Office 365](implementing-expressroute.md)
  
[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[تحسين شبكتك ل Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute وQoS في Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[تدفق المكالمات باستخدام ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365](bgp-communities-in-expressroute.md)
  
[ضبط الأداء Office 365 باستخدام الخطوط الأساسية ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)
  
[خطة استكشاف أخطاء الأداء وإصلاحها Office 365](performance-troubleshooting-plan.md)
  
[نطاقات عناوين IP وعناوين URL في Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 الشبكة وضبط الأداء](network-planning-and-performance.md)
