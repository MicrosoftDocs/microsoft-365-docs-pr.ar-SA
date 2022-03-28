---
title: التوجيه باستخدام ExpressRoute Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: في هذه المقالة، تعرف على متطلبات التوجيه والدوائر ومجالات التوجيه في Azure ExpressRoute لاستخدامها مع Office 365.
ms.openlocfilehash: d6fab2dd9a7e7519eb1f56cebccaf345685cc0cd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63575281"
---
# <a name="routing-with-expressroute-for-office-365"></a>التوجيه باستخدام ExpressRoute Office 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

لفهم توجيه حركة المرور بشكل صحيح Office 365 Azure ExpressRoute، ستحتاج إلى فهم ثابت لمتطلبات توجيه [ExpressRoute](/azure/expressroute/expressroute-routing) الأساسية ودوائر [ExpressRoute](/azure/expressroute/expressroute-circuit-peerings) ومجالات التوجيه. وهي ترسي المبادئ الأساسية لاستخدام ExpressRoute Office 365 العملاء الذين سيعتمدون عليها.
  
تتضمن بعض العناصر الأساسية في المقالات أعلاه التي ستحتاج إلى فهمها ما يلي:
  
- لا يتم تعيين دوائر ExpressRoute إلى بنية أساسية مادية معينة، ولكنها اتصال منطقي يتم في موقع نظير واحد بواسطة Microsoft وموفر نظير بالنيابة عنك.

- يوجد تعيين 1:1 بين دائرة ExpressRoute ومفتاح عميل.

- يمكن أن تدعم كل دائرة علاقتي نظير مستقلتين (نظير Azure Private ونظير Microsoft)؛ Office 365 Microsoft النظير.

- تحتوي كل دائرة على نطاق ترددي ثابت يتم مشاركته عبر جميع علاقات النظير.

- يجب التحقق من صحة أي عناوين IPv4 عامة وأرقم AS عامة سيتم استخدامها لدائرة ExpressRoute على أنها مملوكة لك، أو تعيينها لك حصريا من قبل مالك نطاق العناوين.

- إن دوائر ExpressRoute الظاهرية متكرارة بشكل عمومي وستتبع ممارسات التوجيه القياسية ل BGP. ولهذا السبب نوصي بإجراء دارتين فعليتين لكل الخروج إلى الموفر الخاص بك في تكوين نشط/نشط.

راجع صفحة [الأسئلة الشائعة](/azure/expressroute/expressroute-faqs) للحصول على مزيد من المعلومات حول الخدمات المعتمدة والتكاليف وتفاصيل التكوين. راجع [مقالة مواقع ExpressRoute](/azure/expressroute/expressroute-locations) للحصول على معلومات حول قائمة موفري الاتصال الذين يقدمون دعم نظير Microsoft. لقد قمنا أيضا بتسجيل سلسلة تدريب [Azure ExpressRoute](https://channel9.msdn.com/series/aer) Office 365 10 جزء على القناة 9 للمساعدة في شرح المفاهيم بشكل أكثر دقة.
  
## <a name="ensuring-route-symmetry"></a>ضمان تماثل المسار

يمكن Office 365 الوصول إلى الخوادم الأمامية على كل من الإنترنت و ExpressRoute. ستفضل هذه الخوادم إعادة التوجيه إلى دوائر ExpressRoute في الموقع عند توفرهما. وبسبب ذلك، هناك احتمال عدم تماثل المسار إذا كانت حركة المرور من الشبكة تفضل التوجيه عبر دوائر الإنترنت. تمثل المسارات غير المتماثلة مشكلة لأن الأجهزة التي تقوم بإجراء فحص الحزمة بشكل دقيق يمكنها منع إرجاع حركة المرور التي تتبع مسارا مختلفا عن الحزم الصادرة التي تم اتباعها.
  
بغض النظر عما إذا كنت تقوم ببدء اتصال Office 365 عبر الإنترنت أو ExpressRoute، يجب أن يكون المصدر عنوانا قابلا التوجيه بشكل عام. مع أقران العديد من العملاء مباشرة مع Microsoft، لا يمكن الحصول على عناوين خاصة حيث يمكن التكرار بين العملاء.
  
فيما يلي السيناريوهات التي سيتم فيها بدء Office 365 الاتصال بالشبكة المحلية. لتبسيط تصميم الشبكة، نوصي توجيه ما يلي عبر مسار الإنترنت.
  
- خدمات SMTP مثل البريد من مستأجر Exchange Online إلى مضيف أو بريد إلكتروني SharePoint تم إرساله من SharePoint عبر الإنترنت إلى مضيف في الموقع. يتم استخدام بروتوكول SMTP على نطاق أوسع داخل شبكة Microsoft مقارنة ببادئات المسار المشتركة عبر دوائر ExpressRoute، وستتسبب خوادم SMTP الإعلانية المحلية عبر ExpressRoute في حدوث حالات فشل مع هذه الخدمات الأخرى.

- ADFS أثناء التحقق من صحة كلمة المرور من أجل تسجيل الدخول.

- [Exchange Server التوزيع المختلط](/exchange/exchange-hybrid).

- [SharePoint البحث المختلط المتحدة](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS المختلطة](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business المختلط](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) و/[أو Skype for Business الاتحاد.](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)

- [Skype for Business Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

لكي تقوم Microsoft بالعودة إلى شبكتك لتدفقات حركة المرور ثنائية الاتجاه هذه، يجب مشاركة مسارات BGP إلى أجهزتك المحلية مع Microsoft. عندما تعلن عنبادئات المسار إلى Microsoft عبر ExpressRoute، يجب اتباع أفضل الممارسات التالية:

1) لا تعلن عن نفس مقدمة مسار عنوان IP العامة إلى الإنترنت العام و عبر ExpressRoute. من المستحسن أن تكون إعلانات IP BGP Route Prefix ل Microsoft عبر ExpressRoute من نطاق لا يتم الإعلان عنه على الإنترنت على الإطلاق. إذا لم يكن ذلك ممكنا بسبب مساحة عنوان IP المتوفرة، فمن الضروري التأكد من الإعلان عن نطاق أكثر تحديدا عبر ExpressRoute من أي دائرة إنترنت.

2) استخدم تجمعات عناوين IP ل NAT منفصلة لكل دائرة ExpressRoute ومنفصلة عن تلك الخاصة بدوائر الإنترنت.

3) سيجذب أي مسار يتم الإعلان عنه إلى Microsoft حركة مرور الشبكة من أي خادم في شبكة Microsoft، وليس فقط تلك التي يتم الإعلان عن المسارات الخاصة بها إلى شبكتك عبر ExpressRoute. الإعلان فقط عن المسارات إلى الخوادم حيث يتم تعريف سيناريوهات التوجيه وفهمها جيدا من قبل فريقك. الإعلان عن البادئات المنفصلة لمسار عنوان IP في كل دائرة من دوائر ExpressRoute المتعددة من الشبكة.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>تحديد التطبيقات والميزات التي يتم توجيهها عبر ExpressRoute

عندما تقوم بتكوين علاقة نظير باستخدام مجال توجيه النظير من Microsoft وموافق عليها للوصول المناسب، ستكون قادرا على رؤية كل خدمات PaaS وSaaS المتوفرة عبر ExpressRoute. يمكن Office 365 التي تم تصميمها ل ExpressRoute باستخدام [مجتمعات BGP](./bgp-communities-in-expressroute.md) أو [عوامل تصفية المسار](/azure/expressroute/how-to-routefilter-portal).
  
يتم سرد Office 365 الميزات المتوفرة باستخدام نظير Microsoft في مقالة [نقاط](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) نهاية Office 365 حسب نوع التطبيق و FQDN. سبب استخدام FQDN في الجداول هو السماح للعملاء بإدارة حركة المرور باستخدام ملفات PAC أو تكوينات الوكيل الأخرى، راجع دليل إدارة نقاط نهاية Office 365 على سبيل المثال [ملفات](./managing-office-365-endpoints.md) PAC.
  
في بعض الحالات، استخدمنا مجال أحرف بدل حيث يتم الإعلان عن واحد أو أكثر من أسماء FQDN الفرعية بشكل مختلف عن مجال أحرف البدل الأعلى مستوى. يحدث ذلك عادة عندما يمثل أحرف البدل قائمة طويلة من الخوادم التي يتم الإعلان عنها كلها ل ExpressRoute والإنترنت، بينما يتم الإعلان عن مجموعة فرعية صغيرة من الوجهات فقط على الإنترنت، أو العكس. راجع الجداول أدناه لفهم مكان الاختلافات.
  
يعرض هذا الجدول أحرف البدل FQDN التي يتم الإعلان عنها لكل من الإنترنت و Azure ExpressRoute إلى جانب FQDNs الفرعية التي يتم الإعلان عنها للإنترنت فقط.

|**مجال أحرف البدل المعلن عنه لدوائر ExpressRoute والإنترنت**|**تم الإعلان عن FQDN الفرعية لدوائر الإنترنت فقط**|
|:-----|:-----|
|\*.microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*.officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

عادة ما تكون ملفات PAC مخصصة لإرسال طلبات الشبكة إلى نقاط النهاية المعلن عنها في ExpressRoute مباشرة إلى الدائرة وكل طلبات الشبكة الأخرى إلى الوكيل. إذا كنت تقوم بتكوين ملف PAC بهذه الطريقة، ف قم بتكوين ملف PAC بالترتيب التالي:
  
1. قم بتضمين FQDNs الفرعية من العمود الثاني في الجدول أعلاه في أعلى ملف PAC، مع إرسال حركة المرور إلى الوكيل. لقد قمنا ببناء نموذج لملف PAC لكي تستخدمه في مقالتنا [حول إدارة Office 365 نقاط النهاية](./managing-office-365-endpoints.md).

2. قم بتضمين كل FQDN التي تم الإعلان عنها ل ExpressRoute في هذه المقالة أسفل المقطع الأول، مع إرسال حركة المرور مباشرة إلى دائرة ExpressRoute.[](./urls-and-ip-address-ranges.md)

3. قم بتضمين أي نقاط نهاية شبكة أخرى أو قواعد أسفل هذين الإدخالين، وإرسال حركة المرور باتجاه الوكيل.

يعرض هذا الجدول مجالات أحرف البدل التي يتم الإعلان عنها لدوائر الإنترنت فقط إلى جانب FQDNs الفرعية التي يتم الإعلان عنها ل Azure ExpressRoute ودوائر الإنترنت. بالنسبة لملف PAC أعلاه، يتم سرد FQDN في العمود 2 في الجدول أدناه على أنه يتم الإعلان عنه ل ExpressRoute في الارتباط المشار إليه، مما يعني أنه سيتم تضمينها في المجموعة الثانية من الإدخالات في الملف.

|**مجال أحرف البدل المعلن عنه لدوائر الإنترنت فقط**|**تم الإعلان عن FQDN الفرعي لدوائر ExpressRoute والإنترنت**|
|:-----|:-----|
|\*.office.com  <br/> |\*.outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> www.office.com  <br/> |
|\*.office.net  <br/> |agent.office.net  <br/> |
|\*.office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*.outlook.com  <br/> |\*.protection.outlook.com  <br/> \*.mail.protection.outlook.com  <br/> autodiscover-\<tenant\>.outlook.com  <br/> |
|\*.windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>توجيه Office 365 المرور عبر الإنترنت و ExpressRoute

للمسار إلى Office 365 من اختيارك، ستحتاج إلى تحديد عدد من العوامل الرئيسية.
  
1. مقدار النطاق الترددي الذي سيتطلبه التطبيق. يعد أخذ عينات من الاستخدام الحالي الطريقة الوحيدة الموثوق بها لتحديد ذلك في مؤسستك.

2. موقع (مواقع) الخروج التي تريد أن تغادر منها حركة مرور الشبكة. يجب أن تخطط لتقليل زمن زمن نقل الشبكة للاتصال بالإنترنت Office 365 يؤثر ذلك على الأداء. ولأن Skype for Business يستخدم الصوت والفيديو في الوقت الحقيقي، فإنه عرضة لتأخر الشبكة الرديئة.

3. إذا كنت تريد أن تستخدم كل مواقع الشبكة أو مجموعة فرعية من مواقع الشبكة الخاصة بك ExpressRoute.

4. المواقع التي يوفر منها موفر الشبكة الذي اخترته ExpressRoute.

بمجرد تحديد الإجابات على هذه الأسئلة، يمكنك توفير دائرة ExpressRoute تلبي النطاق الترددي واحتياجات الموقع. للحصول على مزيد من المساعدة في تخطيط الشبكة، [Office 365](./network-planning-and-performance.md) دليل ضبط الشبكة و دراسة الحالة حول كيفية معالجة [Microsoft لتخطيط أداء الشبكة](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>المثال 1: موقع جغرافي واحد
  
هذا المثال هو سيناريو لشركة خيالية تسمى Trey Research التي لديها موقع جغرافي واحد.
  
يسمح للموظفين في Trey Research بالاتصال فقط بالخدمات ومواقع الويب على الإنترنت التي يسمح بها قسم الأمان بشكل صريح على زوج من المحترفين الصادرين الذين يجلسون بين شبكة الشركة ومقسم خدمة الإنترنت الخاص بهم.
  
تخطط Trey Research لاستخدام Azure ExpressRoute ل Office 365 وتدرك أن بعض حركة المرور مثل حركة المرور الموجهة إلى شبكات تسليم المحتوى لن تتمكن من التوجيه عبر اتصال ExpressRoute Office 365. ونظرا لأن كل حركة المرور يتم توجيهها بالفعل إلى الأجهزة الوكيلة بشكل افتراضي، فإن هذه الطلبات ستستمر في العمل كما كان من قبل. بعد أن يحدد Trey Research أنه يمكنه تلبية متطلبات توجيه Azure ExpressRoute، يمكنه المتابعة لإنشاء دائرة وتكوين التوجيه وربط دائرة ExpressRoute الجديدة بشبكة ظاهرية. بمجرد أن يتم تكوين Azure ExpressRoute الأساسي، تستخدم Trey Research ملف [PAC رقم 2](./managing-office-365-endpoints.md) الذي نقوم بنشره لتوجيه حركة المرور باستخدام بيانات خاصة بعملائنا عبر ExpressRoute المباشر لاتصالات Office 365.
  
كما هو موضح في الرسم التخطيطي التالي، يمكن ل Trey Research تلبية متطلبات توجيه حركة Office 365 عبر الإنترنت، بالإضافة إلى مجموعة فرعية من حركة المرور عبر ExpressRoute باستخدام مجموعة من تغييرات تكوين الوكيل الصادر والقادم.
  
1. باستخدام ملف [PAC رقم 2](./managing-office-365-endpoints.md) الذي ننشره من أجل توجيه حركة المرور عبر نقطة الخروج المنفصلة عبر الإنترنت ل Azure ExpressRoute Office 365.

2. يتم تكوين العملاء باستخدام مسار افتراضي نحو ووكلاء Trey Research.

في سيناريو المثال هذا، يستخدم Trey Research جهاز وكيل الصادر. وعلى نحو مماثل، قد يرغب العملاء الذين لا يستخدمون Azure ExpressRoute ل Office 365 في استخدام هذه التقنية في توجيه حركة المرور استنادا إلى تكلفة فحص حركة المرور الموجهة إلى نقاط النهاية ذات الكمية العالية المعروفة.
  
فيما يلي أعلى مستوى صوت ل FQDN Exchange Online SharePoint عبر الإنترنت Skype for Business عبر الإنترنت:
  
![ExpressRoute customer edge network.](../media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com، outlook.office.com

- \<tenant-name\>.sharepoint.com، \<tenant-name\>-my.sharepoint.com، \<tenant-name\>-\<app\>.sharepoint.com

- \*.Lync.com جنبا إلى جنب مع نطاقات IP لحركة مرور غير TCP

- \*broadcast.officeapps.live.com excel.officeapps.live.com \*أو \*onenote.officeapps.live.com \*أو powerpoint.officeapps.live.com أو view.officeapps.live.com \*\*أو visio.officeapps.live.com \*أو word-edit.officeapps.live.com \*أو word-view.officeapps.live.com أو office.live.com

تعرف على المزيد [حول نشر](/archive/blogs/deploymentguys/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy) إعدادات الوكيل وإدارتها في Windows 8 وضمان عدم Office 365 [الوكيل لديك.](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx)
  
مع دائرة ExpressRoute واحدة، لا يوجد توفر عال ل Trey Research. في حالة فشل الزوج المتكرار من أجهزة Edge الخاصة ب Trey التي تقوم بخدمة اتصال ExpressRoute، لا توجد دائرة ExpressRoute إضافية للفشل فيها. هذا الأمر يجعل Trey Research في وضع الورطة حيث يتطلب الفشل في الاتصال بالإنترنت إعادة تكوين يدوية وفي بعض الحالات عناوين IP جديدة. إذا كان تري يرغب في إضافة توفر عال، فإن أبسط حل هو إضافة دوائر ExpressRoute إضافية لكل موقع وتكوين الدوائر بطريقة نشطة/نشطة.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>توجيه ExpressRoute Office 365 مع مواقع متعددة

السيناريو الأخير، توجيه Office 365 المرور عبر ExpressRoute هو أساس بنية التوجيه الأكثر تعقيدا. بغض النظر عن عدد المواقع وعدد المناطق التي توجد فيها هذه المواقع وعدد دوائر ExpressRoute وما إلى ذلك، فإن القدرة على توجيه بعض حركة المرور إلى الإنترنت وبعض حركة المرور عبر ExpressRoute ستكون مطلوبة.
  
تتضمن الأسئلة الإضافية التي يجب الإجابة عليها للعملاء الذين في مواقع متعددة في مناطق جغرافية متعددة ما يلي:
  
1. هل تحتاج إلى دائرة ExpressRoute في كل موقع؟ إذا كنت تستخدم Skype for Business Online أو كنت قلقا بشأن حساسية زمن التأخر ل SharePoint Online أو Exchange Online، فمن المستحسن استخدام زوج متكرار من دارات ExpressRoute النشطة/النشطة في كل موقع. راجع دليل Skype for Business جودة الوسائط واتصال الشبكة للحصول على مزيد من التفاصيل.

2. إذا لم تتوفر دائرة ExpressRoute في منطقة معينة، فكيف Office 365 توجيه حركة المرور الموجهة؟

3. ما هو الأسلوب المفضل لدمج حركة المرور في حالة الشبكات ذات المواقع الصغيرة الكثيرة؟

يشكل كل واحد من هذه الخيارات تحديا فريدا يتطلب منك تقييم شبكتك والخيارات المتوفرة من Microsoft.

|**مراعاة**|**مكونات الشبكة التي يجب تقييمها**|
|:-----|:-----|
|دارات في أكثر من موقع واحد  <br/> |نوصي بتكوين دارتين على الأقل بطريقة نشطة/نشطة.  <br/> يجب مقارنة التكلفة و زمن زمن الإرسال واحتياجات النطاق الترددي.  <br/> استخدم تكلفة مسار BGP وملفات PAC و NAT لإدارة التوجيه باستخدام دوائر متعددة.  <br/> |
|التوجيه من مواقع بدون دائرة ExpressRoute  <br/> |نوصي بالتراجع وحل DNS بالقرب من الشخص الذي يبدأ طلب الحصول على Office 365.  <br/> يمكن استخدام إعادة توجيه DNS للسماح للمكاتب البعيدة باكتشاف نقطة النهاية المناسبة.  <br/> يجب أن يتوفر للعملاء في المكتب البعيد مسار يوفر إمكانية الوصول إلى دائرة ExpressRoute.  <br/> |
|دمج مكتب صغير  <br/> |يجب مقارنة النطاق الترددي المتاح واستخدام البيانات بعناية.  <br/> |

> [!NOTE]
> ستفضل Microsoft ExpressRoute عبر الإنترنت إذا كان المسار متوفرا بغض النظر عن الموقع الفعلي.
  
يجب أخذ كل من هذه الاعتبارات في الاعتبار لكل شبكة فريدة. فيما يلي مثال على ذلك.
  
### <a name="example-2-multi-geographic-locations"></a>المثال 2: المواقع الجغرافية المتعددة
  
هذا المثال هو سيناريو لشركة خيالية تسمى 'التأمين الهمونغي' التي لديها مواقع جغرافية متعددة.
  
إن التأمين الطواف مشتت جغرافيا مع المكاتب في جميع أنحاء العالم. يريدون تنفيذ Azure ExpressRoute Office 365 الاحتفاظ بمعظم Office 365 المرور على اتصالات الشبكة المباشرة. كما أن شركة التأمين الطواف لديها مكاتب في قارتين إضافيتين. سيحتاج الموظفون في المكتب البعيد حيث لا يكون ExpressRoute قابلا للتنفيذ إلى العودة إلى أحد أو كل من المرافق الأساسية لاستخدام اتصال ExpressRoute.
  
المبدأ التوجيهي هو Office 365 نقل البيانات إلى مركز بيانات Microsoft في أسرع وقت ممكن. في هذا المثال، يجب أن تقرر شركة Humongous Insurance ما إذا كان يتعين على مكاتبها البعيدة التوجيه عبر الإنترنت للوصول إلى مركز بيانات Microsoft عبر أي اتصال في أسرع وقت ممكن أو إذا كان يتعين على مكاتبها البعيدة التوجيه عبر شبكة داخلية للوصول إلى مركز بيانات Microsoft عبر اتصال ExpressRoute في أسرع وقت ممكن.
  
لقد تم تصميم مراكز البيانات والشبكات وهندسة التطبيقات الخاصة ب Microsoft لاتصالات مختلفة عالميا وخدمتها بالطريقة الأكثر فعالية الممكنة. هذه إحدى أكبر الشبكات في العالم. لن تتمكن الطلبات الموجهة Office 365 التي تبقى على شبكات العملاء أطول من اللازم من الاستفادة من هذه البنية.
  
في حالة التأمين الطواف، يجب المتابعة وفقا للتطبيقات التي ينوى استخدامها عبر ExpressRoute. على سبيل المثال، إذا كان أحد عملاء Skype for Business Online، أو يخطط لاستخدام اتصال ExpressRoute عند الاتصال باجتماعات Skype for Business عبر الإنترنت، فإن التصميم الموصى به في Skype for Business  دليل اتصال الشبكة وجودة الوسائط عبر الإنترنت هو توفير دائرة ExpressRoute إضافية للموقع الثالث. قد يكون هذا أكثر تكلفة من منظور الشبكة؛ ومع ذلك، قد يتسبب توجيه الطلبات من قارة إلى أخرى قبل تسليمها إلى مركز بيانات Microsoft في تجربة سيئة أو غير قابلة للاستخدام أثناء Skype for Business عبر الإنترنت والاتصالات.
  
إذا لم يكن التأمين الهمجي يستخدم أو لا يخطط لاستخدام Skype for Business Online بأي شكل من الأشكال، فقد يكون توجيه حركة مرور الشبكة الموجهة إلى Office 365 إلى قارة ذات اتصال ExpressRoute أمرا عمليا على الرغم من أن ذلك قد يؤدي إلى زمن غير ضروري أو ازدحام TCP. في كلتا الحالتين، من المستحسن توجيه حركة مرور الإنترنت الموجهة إلى الإنترنت على الموقع المحلي للاستفادة من شبكات تسليم المحتوى التي Office 365 عليها.
  
![ExpressRoute متعدد الجغرافيا.](../media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
عندما يخطط التأمين الهمجي لاإستراتيجيته المتعددة الجغرافيا، هناك العديد من الأمور التي يجب عليك التفكير فيها حول حجم الدائرة وعدد الدوائر والفشل وما إلى ذلك.
  
باستخدام ExpressRoute في موقع واحد مع مناطق متعددة تحاول استخدام الدائرة، يريد التأمين الهمجي ضمان إرسال الاتصالات إلى Office 365 من المكتب البعيد إلى مركز بيانات Office 365 أقرب مركز بيانات الرئيسي وتسلمها من موقع المقر الرئيسي. للقيام بذلك، ينفذ التأمين الهمجي إعادة توجيه DNS لتقليل عدد الرحلات المستديرة وابحث DNS المطلوبة لإنشاء الاتصال المناسب ببيئة Office 365 الأقرب إلى نقطة الخروج إلى الإنترنت في المقر الرئيسي. يمنع ذلك العميل من حل خادم محلي أمامي ويضمن خادم Front-End الذي يتصل به الشخص بالقرب من المقر الرئيسي حيث ينافر التأمين الطواف مع Microsoft. يمكنك أيضا التعرف على [تعيين "إعادة توجيه شرطي" لاسم المجال](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc794735(v=ws.10)).
  
في هذا السيناريو، ستحل حركة المرور من المكتب البعيد البنية الأساسية الأمامية Office 365 في أمريكا الشمالية وستستخدم Office 365 للاتصال بخادمات الخادم وفقا لهياية Office 365. على سبيل المثال، Exchange Online إنهاء الاتصال في أمريكا الشمالية، وستتصل تلك الخوادم الأمامية بخادم علبة البريد الخلفية أينما يقيم المستأجر. كل الخدمات لديها خدمة باب أمامي موزعة على نطاق واسع تتكون من وجهات unicast و anycast.
  
إذا كان للهمونجوس مكاتب رئيسية في قارات متعددة، فمن المستحسن أن يكون هناك دارتان نشطتان/نشطة على الأقل في كل منطقة من أجل تقليل زمن زمن تقدم التطبيقات الحساسة مثل Skype for Business Online. إذا كانت كل المكاتب في قارة واحدة، أو لا تستخدم التعاون في الوقت الحقيقي، فإن وجود نقطة الخروج المجمعة أو الموزعة قرار خاص بكل عميل. عند توفر دوائر متعددة، يضمن توجيه BGP الفشل إذا لم تتوفر أي دائرة واحدة.
  
تعرف على المزيد [حول تكوينات التوجيه العينة](/azure/expressroute/expressroute-config-samples-routing) و [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](/azure/expressroute/expressroute-config-samples-nat).
  
## <a name="selective-routing-with-expressroute"></a>التوجيه الاختياري باستخدام ExpressRoute

قد يكون التوجيه الاختياري باستخدام ExpressRoute مطلوبا لأسباب مختلفة، مثل الاختبار، طرح ExpressRoute إلى مجموعة فرعية من المستخدمين. هناك العديد من الأدوات التي يمكن للعملاء استخدامها Office 365 حركة مرور الشبكة عبر ExpressRoute:
  
1. **تصفية المسار/** تحسينه - مما يسمح لمسارات BGP Office 365 ExpressRoute إلى مجموعة فرعية من الشاشات الفرعية أو الموجهات. يتم توجيه هذا بشكل انتقائي حسب مقطع شبكة العملاء أو موقع المكتب الفعلي. هذا أمر شائع في عملية طرح ExpressRoute Office 365، وقد تم تكوينه على أجهزة BGP.

2. **ملفات PAC/عناوين URL** - Office 365 توجيه حركة مرور الشبكة الموجهة إلى شبكات FQDN معينة لتوجيهها على مسار معين. يتم توجيه هذا بشكل انتقائي بواسطة الكمبيوتر العميل كما هو معرف بواسطة [نشر ملف PAC](./managing-office-365-endpoints.md).

3. **تصفية المسار** -  [عوامل تصفية المسار](/azure/expressroute/how-to-routefilter-portal) هي طريقة لاستهلاك مجموعة فرعية من الخدمات المعتمدة من خلال نظير Microsoft.

4. **مجتمعات BGP** - تسمح التصفية استنادا إلى علامات مجتمع [BGP](./bgp-communities-in-expressroute.md) للعميل بتحديد تطبيقات Office 365 التي ستعبر ExpressRoute والتي ستعبر الإنترنت.

إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/erorouting]()
  
## <a name="related-topics"></a>مواضيع ذات صلة

[تقييم Office 365 الشبكة](assessing-network-connectivity.md)
  
[Azure ExpressRoute Office 365](azure-expressroute.md)
  
[إدارة ExpressRoute Office 365 الاتصال](managing-expressroute-for-connectivity.md)
  
[تخطيط الشبكة باستخدام ExpressRoute Office 365](network-planning-with-expressroute.md)
  
[تنفيذ ExpressRoute Office 365](implementing-expressroute.md)
  
[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[تحسين الشبكة ل Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute و QoS في Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[تدفق المكالمة باستخدام ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365](bgp-communities-in-expressroute.md)
  
[Office 365 الأداء باستخدام الأساسات ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)
  
[خطة استكشاف الأخطاء وإصلاحها Office 365](performance-troubleshooting-plan.md)
  
[نطاقات عناوين IP وعناوين URL في Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Office 365 الشبكة وضبط الأداء](network-planning-and-performance.md)
