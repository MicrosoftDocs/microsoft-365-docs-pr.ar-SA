---
title: استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: تعرف على كيفية استخدام مجتمعات BGP في Azure ExpressRoute لإدارة عدد البادئات IP و النطاق الترددي المطلوب Office 365 السيناريوهات.
ms.openlocfilehash: afcbbbebda8dcc7c9425831b44f0d95f0eca5a18
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570013"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365

يستند الاتصال ب Office 365 Azure ExpressRoute إلى إعلانات BGP الخاصة بالشبكات الفرعية المحددة ل IP التي تمثل الشبكات التي يتم Office 365 نقاط النهاية. نظرا للطبيعة العالمية Office 365 وعدد الخدمات التي تشكل Office 365، يحتاج العملاء في أغلب الأحيان إلى إدارة الإعلانات التي يقبلونها على شبكتهم. تقليل عدد عناوين IP الفرعية؛ المشار إليه ببادئات IP خلال الجزء المتبقي من هذه المقالة، لمحاذاة مصطلحات إدارة شبكة BGP، يخدم الأهداف النهاية التالية للعملاء:
  
- إدارة عدد البادئات المعلن عنها ل **IP** المقبولة - العملاء الذين لديهم بنية أساسية لشبكة داخلية أو مشغل شبكة يدعم فقط عددا محدودا من البادئات IP، وسيرغب العملاء الذين لديهم مشغل شبكة يتولى قبول البادئات فوق رقم محدود في تقييم العدد الإجمالي للبادئات التي تم الإعلان عنها مسبقا للشبكة وتحديد تطبيقات Office 365 الأكثر ملاءمة ل ExpressRoute.

- إدارة مقدار النطاق الترددي المطلوب على دائرة **Azure ExpressRoute** - قد يرغب العملاء في التحكم في مغلف النطاق الترددي لخدمات Office 365 عبر مسار ExpressRoute مقابل مسار الإنترنت. يسمح هذا للعملاء بحجز النطاق الترددي ExpressRoute للتطبيقات المحددة مثل Skype for Business توجيه التطبيقات Office 365 المتبقية عبر مسار الإنترنت.

لمساعدة العملاء في تحقيق هذه الأهداف، Office 365 ببادئات IP التي يتم الإعلان عنها عبر ExpressRoute بقيم مجتمع BGP خاصة بالخدمة كما هو موضح في المثال أدناه.
  
> [!NOTE]
> يجب أن تتوقع تضمين بعض حركة مرور الشبكة المقترنة بالت تطبيقات أخرى في قيمة المجتمع. هذا السلوك المتوقع للبرنامج العام كعرض خدمة مع الخدمات المشتركة و مراكز البيانات. وقد تم تصغير ذلك حيثما أمكن مع الهدفين أعلاه، مع إدارة عدد البادات و/أو النطاق الترددي في الاعتبار.

|**الخدمة**|**قيمة مجتمع BGP**|**ملاحظات**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |يتضمن Exchange وخدمات EOP\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype for Business\*  <br/> |12076:5030  <br/> |Skype for Business عبر الإنترنت & Microsoft Teams عبر الإنترنت  <br/> |
|الخدمات Office 365 الأخرى\*  <br/> |12076:5100  <br/> |يتضمن Azure Active Directory (سيناريوهات المصادقة ومزامنة الدليل) بالإضافة إلى Office 365 المدخل  <br/> |
|\*تم توثيق نطاق سيناريوهات الخدمة المضمنة في ExpressRoute في Office 365 [نقاط النهاية](./urls-and-ip-address-ranges.md).  <br/> \*\*قد تضاف خدمات إضافية وقيم مجتمع BGP في المستقبل. [راجع القائمة الحالية لمجتمعات BGP](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>ما هي السيناريوهات الأكثر شيوعا لاستخدام مجتمعات BGP؟

يمكن للعملاء استخدام مجتمعات BGP لتنظيم مجموعات من البادئات IP التي يتم قبولها من خلال شبكتهم من خلال Azure ExpressRoute، مما يؤثر على العدد الإجمالي لبادئات IP ومغلف النطاق الترددي المتوقع لخدمات Office 365 معينة. من المهم فهم أن كل Office 365 تتطلب حركة مرور مرتبطة بالإنترنت بغض النظر عن استخدام مجتمعات Azure ExpressRoute أو BGP. السيناريوهات الثلاثة التالية هي الاستخدامات الأكثر شيوعا لهذه الوظيفة.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>السيناريو 1: تقليل عدد Office 365 IP

شركة Contoso Corporation هي شركة من 50000 شخص تستخدم حاليا Office 365 Exchange Online SharePoint Online. في مراجعة متطلبات ExpressRoute، يحدد Contoso أجهزة الشبكة الخاصة به في العديد من المواقع الإقليمية التي لا يمكنها معالجة أحجام جدول التوجيه التي فوق 100 إدخال توجيه إضافي. راجعت شركة Contoso العدد الإجمالي لبادئات IP التي سيعلن عنها ExpressRoute للحصول على مجموعة كاملة من خدمات Office 365 واستنتجت أنها تتجاوز 100. للبقاء ضمن إدخالات المسار الإضافية التي عددها 100 إدخال، يوسع Contoso نطاق استخدام ExpressRoute ل Office 365 لقيمة مجتمع BGP ل SharePoint Online فقط، 12076:5020، التي يتم تلقيها من خلال نظير ExpressRoute Microsoft.

|**علامة مجتمع BGP المستخدمة**|**الوظائف القابلة التوجيه عبر Azure ExpressRoute**|**مسارات الإنترنت مطلوبة**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint عبر &amp; OneDrive for Business  <br/> | طلبات DNS وCRL وCDN &amp;  <br/>  جميع الخدمات Office 365 الأخرى غير المعتمدة بشكل خاص عبر Azure ExpressRoute  <br/>  جميع خدمات Microsoft السحابية الأخرى  <br/>  Office 365، Office 365، Office &amp; في مستعرض  <br/>  Exchange Online Exchange Online Protection و Skype for Business Online  <br/> |

> [!NOTE]
> لتحقيق عدد أقل من الباديات لكل خدمة، يستمر الحد الأدنى من التداخل بين الخدمات. هذا سلوك متوقع.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>السيناريو 2: تحديد نطاق ExpressRoute واستخدام النطاق الترددي الداخلي لبعض Office 365 الخدمات

شركة Fabrikam Inc، وهي مؤسسة كبيرة متعددة البلدان مع شبكة غير متجانسة موزعة، هي مشترك في العديد من الخدمات Office 365 منها؛ Exchange Online SharePoint عبر الإنترنت Skype for Business عبر الإنترنت. يمكن للبنية الأساسية التوجيه الداخلية ل Fabrikam معالجة الآلاف منبادئ IP في جداول التوجيه الخاصة بها؛ ومع ذلك، لا تريد Fabrikam سوى توفير ExpressRoute وعرض النطاق الترددي الداخلي للتطبيقات Office 365 الأكثر حساسية لأداء الشبكة واستخدام النطاق الترددي الموجود للإنترنت لجميع تطبيقات Office 365 الأخرى.
  
لهذا السبب، تقوم شركة Fabrikam بنطاق ترددي Azure ExpressRoute إلى Skype for Business Online BGP Community، 12076:5030 فقط، التي يتم تلقيها من خلال نظير ExpressRoute Microsoft. تستمر حركة مرور الشبكة المتبقية المقترنة Office 365 في استخدام نقاط الخروج عبر الإنترنت.

|**علامة مجتمع BGP المستخدمة**|**الوظائف القابلة التوجيه عبر Azure ExpressRoute**|**مسارات الإنترنت مطلوبة**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype إشارة SIP وتنزيلها والصوت والفيديو ومشاركة سطح المكتب  <br/> | طلبات DNS وCRL وCDN &amp;  <br/>  جميع الخدمات Office 365 الأخرى غير المعتمدة بشكل خاص عبر Azure ExpressRoute  <br/>  جميع خدمات Microsoft السحابية الأخرى  <br/>  Office 365، Office 365، Office &amp; في مستعرض  <br/>  Skype for Business بيانات Skype، تلميحات سريعة للعميل، اتصال المراسلة الفورية العام  <br/>  Exchange Online Exchange Online Protection و SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>السيناريو 3: تحديد تحديد Azure ExpressRoute لخدمات Office 365 فقط

إن Woodgrove Bank هو أحد عملاء العديد من خدمات Microsoft السحابية بما في ذلك Office 365. بعد تقييم سعة الشبكة واستهلاكها، يقرر Woodgrove Bank نشر Azure ExpressRoute كمسار مفضل لخدمات Office 365 المعتمدة. يمكن أن تدعم جداول التوجيه المجموعة الكاملة من Office 365 IP ودوائر Azure ExpressRoute التي تم توفيرها لدعم كل احتياجات زمن الوصول و النطاق الترددي المتوقع.
  
لضمان حركة مرور الشبكة المقترنة بالخدمات السحابية ل Microsoft غير Office 365، يوسع Woodgrove Bank نطاق استخدام ExpressRoute for Office 365 لجميعبادات IP المعلمة بقيم مجتمع BGP Office 365 المحددة، 12076:5010، 12076:5020، 12076:5030، 12076:5100.

|**علامة مجتمع BGP المستخدمة**|**الوظائف القابلة التوجيه عبر Azure ExpressRoute**|**مسارات الإنترنت مطلوبة**|
|:-----|:-----|:-----|
|Exchange أو Skype for Business & Microsoft Teams أو SharePoint أو خدمات &amp; أخرى  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Exchange Online Protection  <br/> SharePoint عبر &amp; OneDrive for Business  <br/> Skype إشارة SIP وتنزيلها والصوت والفيديو ومشاركة سطح المكتب  <br/> Office 365، Office 365، Office &amp; في مستعرض  <br/> | طلبات DNS وCRL وCDN &amp;  <br/>  جميع الخدمات Office 365 الأخرى غير المعتمدة بشكل خاص عبر Azure ExpressRoute  <br/>  جميع خدمات Microsoft السحابية الأخرى  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>اعتبارات التخطيط الأساسية لاستخدام مجتمعات BGP

يجب أن يأخذ العملاء الذين يختارون الاستفادة من مجتمعات BGP للتأثير على كيفية الإعلان عن ExpressRoute ونشره عبر شبكة العملاء الاعتبارات التالية في الاعتبار:
  
- عند استخدام مجتمعات BGP في تصميم الشبكة، من المهم ضمان الحفاظ على تماثل المسار. في بعض الحالات، قد يؤدي إضافة مجتمعات BGP أو إزالتها إلى إنشاء حالة يكون فيها التوجيه المتماثل مقطوعا ويجب تحديث تكوين التوجيه لإعادة إنشاء توجيه متماثل.

- تحديد مكان Azure ExpressRoute باستخدام قيم مجتمع BGP هو إجراء عميل. ستقوم Microsoft بالإعلان عن كلبادات IP المقترنة بعلاقة النظير بغض النظر عن أي تحديد للصفوف تم تكوينه بواسطة العميل.

- لا يدعم Azure ExpressRoute أي إجراءات على شبكة Microsoft استنادا إلى مجتمعات BGP المعينة للعميل.

- يتم وضع علامة فقط على Office 365 IP المستخدمة بواسطة قيم مجتمع BGP الخاصة بالخدمة، أما مجتمعات BGP الخاصة بموقع معين، فهى غير معتمدة. Office 365 الخدمات العامة بطبيعتها، فتصفية البادئات استنادا إلى موقع المستأجر أو البيانات ضمن Office 365 غير معتمدة. النهج الموصى به هو تكوين الشبكة لتنسيق مسار الشبكة الأقصر أو الأكثر تفضيلا من موقع شبكة المستخدم إلى شبكة Microsoft العامة، بغض النظر عن الموقع الفعلي  عنوان IP لخدمة Office 365 التي يطلبها.

- تمثلبادات IP المضمنة في كل قيمة مجتمع BGP شبكة فرعية تحتوي على عناوين IP Office 365 المقترنة بالقيمة. في بعض الحالات، يوجد في أكثر من Office 365 تطبيق عناوين IP داخل شبكة فرعية مما يؤدي إلى وجودبادية IP في أكثر من قيمة مجتمع واحدة. من المتوقع أن يحدث هذا السلوك، على الرغم من أنه نادرا، بسبب تجزئة التخصيص ولا يؤثر على عدد الباديء أو أهداف إدارة النطاق الترددي. يتم تشجيع العملاء على استخدام نهج "السماح بما هو مطلوب" بدلا من "رفض ما هو غير مطلوب" عند الاستفادة من مجتمعات BGP Office 365 لتقليل التأثير.

- لا يغير استخدام مجتمعات BGP متطلبات اتصال الشبكة الأساسية أو التكوين المطلوب لاستخدام Office 365. لا يزال العملاء الذين Office 365 الوصول إلى الإنترنت مطلوبين ليتمكنوا من الوصول إلى الإنترنت.

- يؤثر تحديد موقع Azure ExpressRoute مع مجتمعات BGP فقط على المسارات التي يمكن للشبكة الداخلية رؤياها عبر علاقة النظير من Microsoft. قد تحتاج إلى إجراء تكوينات إضافية على مستوى التطبيق مثل استخدام تكوين PAC أو WPAD بالتزامن مع التوجيه النطاقي.

- بالإضافة إلى استخدام مجتمعات BGP المعينة من Microsoft، قد يختار العملاء تعيين مجتمعات BGP الخاصة بهم لبادئات IP Office 365 التي تم تعلمها من خلال Azure ExpressRoute للتأثير على التوجيه الداخلي. حالة الاستخدام الشائعة هي تعيين مجتمع BGP مستند إلى موقع لكل المسارات التي يتم تعلمها عبر كل موقع نظير ExpressRoute معين، ثم استخدام تلك المعلومات في عملية النقل لأسفل في شبكة العملاء لتنسيق مسار الشبكة الأقصر أو الأكثر تفضيلا في شبكة Microsoft. إن استخدام مجتمعات BGP المعينة للعميل مع ExpressRoute Office 365 خارج نطاق تحكم Microsoft أو إمكانية الرؤية.

إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>مواضيع ذات صلة

[تقييم Office 365 الشبكة](assessing-network-connectivity.md)
  
[Azure ExpressRoute Office 365](azure-expressroute.md)
  
[إدارة ExpressRoute Office 365 الاتصال](managing-expressroute-for-connectivity.md)
  
[التوجيه باستخدام ExpressRoute Office 365](routing-with-expressroute.md)
  
[تخطيط الشبكة باستخدام ExpressRoute Office 365](network-planning-with-expressroute.md)
  
[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute و QoS في Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[تدفق المكالمة باستخدام ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[تنفيذ ExpressRoute Office 365](implementing-expressroute.md)
  
[دعم مجتمعات BGP](/azure/expressroute/expressroute-routing)
  
[Office 365 الأداء باستخدام الأساسات ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)
  
[خطة استكشاف الأخطاء وإصلاحها Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute Office 365 التدريب](https://channel9.msdn.com/series/aer)