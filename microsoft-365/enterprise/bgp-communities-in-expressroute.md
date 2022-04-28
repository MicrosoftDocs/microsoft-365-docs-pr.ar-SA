---
title: استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية استخدام مجتمعات BGP في Azure ExpressRoute لإدارة عدد بادئات IP وعرض النطاق الترددي المطلوب لسيناريوهات Office 365.
ms.openlocfilehash: 3e7ec6373299741cc1d34c18cc6be5b9366f3de6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095763"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365

يعتمد الاتصال Office 365 باستخدام Azure ExpressRoute على إعلانات BGP لشبكات IP الفرعية المحددة التي تمثل الشبكات التي يتم فيها نشر نقاط نهاية Office 365. نظرا للطبيعة العالمية Office 365 وعدد الخدمات التي تشكل Office 365، غالبا ما يحتاج العملاء إلى إدارة الإعلانات التي يقبلونها على شبكتهم. تقليل عدد الشبكات الفرعية ل IP؛ يشار إليها باسم بادئات IP خلال الجزء المتبقي من هذه المقالة، لتتماشى مع مصطلحات إدارة شبكة BGP، تخدم الأهداف النهائية التالية للعملاء:
  
- **إدارة عدد بادئات IP المعلن عنها المقبولة** - سيرغب العملاء الذين لديهم بنية أساسية داخلية للشبكة أو مشغل شبكة يدعم فقط عددا محدودا من بادئات IP والعملاء الذين لديهم ناقل شبكة يفرض رسوما على قبول البادئات فوق عدد محدود في تقييم العدد الإجمالي للبادئات التي تم الإعلان عنها بالفعل إلى شبكتهم وتحديد التطبيقات Office 365 الأنسب ل ExpressRoute.

- **إدارة مقدار النطاق الترددي المطلوب على دائرة Azure ExpressRoute** - قد يرغب العملاء في التحكم في مغلف النطاق الترددي لخدمات Office 365 عبر مسار ExpressRoute مقابل مسار الإنترنت. يسمح هذا للعملاء بحجز النطاق الترددي ExpressRoute لتطبيقات معينة مثل Skype for Business وتوجيه تطبيقات Office 365 المتبقية عبر مسار الإنترنت.

لمساعدة العملاء في تحقيق هذه الأهداف، يتم وضع علامة على بادئات IP Office 365 التي يتم الإعلان عنها عبر ExpressRoute بقيم مجتمع BGP الخاصة بالخدمة كما هو موضح في المثال أدناه.
  
> [!NOTE]
> يجب أن تتوقع تضمين بعض نسبة استخدام الشبكة المقترنة بتطبيقات أخرى في قيمة المجتمع. هذا سلوك متوقع لبرنامج عالمي كخدمة يقدم مع الخدمات المشتركة ومراكز البيانات. وقد تم تقليل هذا حيثما أمكن مع الهدفين المذكورين أعلاه، وإدارة عدد البادئات و/أو النطاق الترددي في الاعتبار.

|**الخدمة**|**قيمة مجتمع BGP**|**ملاحظات**|
|:-----|:-----|:-----|
|Exchange Online\*  <br/> |12076:5010  <br/> |يتضمن خدمات Exchange وEOP\*  <br/> |
|SharePoint Online\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype for Business\*  <br/> |12076:5030  <br/> |خدمات & Microsoft Teams Skype for Business Online  <br/> |
|خدمات Office 365 الأخرى\*  <br/> |12076:5100  <br/> |يتضمن Azure Active Directory (سيناريوهات مزامنة المصادقة والدليل) بالإضافة إلى خدمات مدخل Office 365  <br/> |
|\*يتم توثيق نطاق سيناريوهات الخدمة المضمنة في ExpressRoute في [مقالة نقاط النهاية Office 365](./urls-and-ip-address-ranges.md).  <br/> \*\*قد تتم إضافة خدمات إضافية وقيم مجتمع BGP في المستقبل. [راجع القائمة الحالية لمجتمعات BGP](/azure/expressroute/expressroute-routing).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>ما هي السيناريوهات الأكثر شيوعا لاستخدام مجتمعات BGP؟

قد يستخدم العملاء مجتمعات BGP لتنظيم مجموعات من بادئات IP التي يتم قبولها من قبل شبكتهم من خلال Azure ExpressRoute، ما يؤثر على إجمالي عدد بادئات IP ومغلف النطاق الترددي المتوقع لبعض خدمات Office 365. من المهم أن نفهم أن جميع Office 365 تتطلب حركة مرور مرتبطة بالإنترنت بغض النظر عن استخدام Azure ExpressRoute أو مجتمعات BGP. السيناريوهات الثلاثة التالية هي الاستخدامات الأكثر شيوعا لهذه الوظيفة.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>السيناريو 1: تقليل عدد بادئات IP Office 365

شركة Contoso Corporation هي شركة مكونة من 50000 شخص تستخدم حاليا Office 365 ل Exchange Online و SharePoint Online. في مراجعة متطلبات ExpressRoute، تحدد Contoso أجهزة الشبكة الخاصة بها في العديد من المواقع الإقليمية التي لا يمكنها التعامل مع أحجام جداول التوجيه التي تزيد عن 100 إدخال مسار إضافي. راجعت شركة Contoso العدد الإجمالي لبادئات IP التي سيعلن عنها ExpressRoute للمجموعة الكاملة من خدمات Office 365 واستنتجت أنها تتجاوز 100. للبقاء ضمن 100 إدخال مسار إضافي، تحدد Contoso نطاق استخدام ExpressRoute Office 365 إلى قيمة مجتمع BGP SharePoint Online فقط، 12076:5020، التي تم تلقيها من خلال إقران ExpressRoute Microsoft.

|**علامة مجتمع BGP المستخدمة**|**الوظائف القابلة للتوجيه عبر Azure ExpressRoute**|**مسارات الإنترنت المطلوبة**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive for Business  <br/> | طلبات DNS و CRL و &amp; CDN  <br/>  جميع خدمات Office 365 الأخرى غير مدعومة بشكل خاص عبر Azure ExpressRoute  <br/>  جميع خدمات Microsoft السحابية الأخرى  <br/>  مدخل Office 365، مصادقة Office 365، &amp; Office في مستعرض  <br/>  Exchange Online و Exchange Online Protection و Skype for Business Online  <br/> |

> [!NOTE]
> لتحقيق عدد بادئات أقل لكل خدمة، سيستمر الحد الأدنى من التداخل بين الخدمات. هذا سلوك متوقع.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>السيناريو 2: تحديد نطاق ExpressRoute واستخدام النطاق الترددي الداخلي لبعض خدمات Office 365

شركة Fabrikam Inc، وهي مؤسسة كبيرة متعددة الجنسيات مع شبكة موزعة غير متجانسة، هي مشترك في العديد من خدمات Office 365 بما في ذلك؛ Exchange Online و SharePoint Online و Skype for Business Online. يمكن أن تتعامل البنية الأساسية للتوجيه الداخلي لشركة Fabrikam مع الآلاف من بادئات IP في جداول التوجيه الخاصة بها؛ ومع ذلك، لا تريد شركة Fabrikam سوى توفير ExpressRoute والنطاق الترددي الداخلي لتطبيقات Office 365 الأكثر حساسية لأداء الشبكة واستخدام النطاق الترددي الحالي للإنترنت لجميع تطبيقات Office 365 الأخرى.
  
لهذا السبب، تقوم شركة Fabrikam بنطاق Azure ExpressRoute الترددي الخاص بها Skype for Business فقط قيمة مجتمع BGP عبر الإنترنت، 12076:5030، المستلمة من خلال إقران ExpressRoute Microsoft. تستمر نسبة استخدام الشبكة المتبقية المقترنة Office 365 في استخدام نقاط خروج الإنترنت.

|**علامة مجتمع BGP المستخدمة**|**الوظائف القابلة للتوجيه عبر Azure ExpressRoute**|**مسارات الإنترنت المطلوبة**|
|:-----|:-----|:-----|
|Skype for Business  <br/> (12076:5030)  <br/> |Skype إشارات SIP والتنزيلات والصوت والفيديو ومشاركة سطح المكتب  <br/> | طلبات DNS و CRL و &amp; CDN  <br/>  جميع خدمات Office 365 الأخرى غير مدعومة بشكل خاص عبر Azure ExpressRoute  <br/>  جميع خدمات Microsoft السحابية الأخرى  <br/>  مدخل Office 365، مصادقة Office 365، &amp; Office في مستعرض  <br/>  Skype for Business بيانات تتبع الاستخدام، Skype التلميحات السريعة للعميل، واتصال المراسلة الفورية العام  <br/>  Exchange Online Exchange Online Protection و SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>السيناريو 3: تحديد نطاق Azure ExpressRoute لخدمات Office 365 فقط

يعد بنك Woodgrove عميلا للعديد من خدمات Microsoft السحابية بما في ذلك Office 365. بعد تقييم سعة الشبكة واستهلاك Woodgrove Bank يقرر نشر Azure ExpressRoute كمسار مفضل لخدمات Office 365 المدعومة. يمكن أن تدعم جداول التوجيه المجموعة الكاملة من بادئات IP Office 365 ودوائر Azure ExpressRoute التي وفرتها تدعم جميع احتياجات النطاق الترددي وزمن الانتقال المتوقع.
  
لضمان نسبة استخدام الشبكة المقترنة بخدمات Microsoft السحابية بخلاف Office 365، يحدد Woodgrove Bank نطاق استخدام ExpressRoute Office 365 لجميع بادئات IP التي تم وضع علامة عليها بقيم مجتمع BGP محددة Office 365، 12076:5010، 12076:5020، 12076:5030، 12076:5100.

|**علامة مجتمع BGP المستخدمة**|**الوظائف القابلة للتوجيه عبر Azure ExpressRoute**|**مسارات الإنترنت المطلوبة**|
|:-----|:-----|:-----|
|خدمات Exchange Skype for Business & Microsoft Teams SharePoint &amp; وخدمات أخرى  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |&amp; Exchange Online Protection Exchange Online  <br/> SharePoint Online &amp; OneDrive for Business  <br/> Skype إشارات SIP والتنزيلات والصوت والفيديو ومشاركة سطح المكتب  <br/> مدخل Office 365، مصادقة Office 365، &amp; Office في مستعرض  <br/> | طلبات DNS و CRL و &amp; CDN  <br/>  جميع خدمات Office 365 الأخرى غير مدعومة بشكل خاص عبر Azure ExpressRoute  <br/>  جميع خدمات Microsoft السحابية الأخرى  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>اعتبارات التخطيط الرئيسية لاستخدام مجتمعات BGP

يجب على العملاء الذين يختارون الاستفادة من مجتمعات BGP للتأثير على كيفية الإعلان عن ExpressRoute ونشره من خلال شبكة العملاء مراعاة الاعتبارات التالية:
  
- عند استخدام مجتمعات BGP في تصميم الشبكة، من المهم ضمان استمرار الحفاظ على تماثل المسار. في بعض الحالات، قد تؤدي إضافة مجتمعات BGP أو إزالتها إلى إنشاء حالة يكون فيها التوجيه المتماثل مقطوعا ويجب تحديث تكوين التوجيه لإعادة إنشاء التوجيه المتماثل.

- تحديد نطاق Azure ExpressRoute مع قيم مجتمع BGP هو إجراء عميل. ستعلن Microsoft عن جميع بادئات IP المقترنة بعلاقة التناظر بغض النظر عن أي نطاق تم تكوينه من قبل العميل.

- لا يدعم Azure ExpressRoute أي إجراءات على شبكة Microsoft استنادا إلى مجتمعات BGP المعينة من قبل العميل.

- يتم وضع علامة على بادئات IP المستخدمة من قبل Office 365 بقيم مجتمع BGP الخاصة بالخدمة فقط، ولا يتم دعم مجتمعات BGP الخاصة بالموقع. Office 365 الخدمات عمومية بطبيعتها، فإن تصفية البادئات استنادا إلى موقع المستأجر أو البيانات داخل السحابة Office 365 غير مدعومة. النهج الموصى به هو تكوين الشبكة لتنسيق أقصر مسار شبكة أو الأكثر تفضيلا من موقع شبكة المستخدم إلى شبكة Microsoft العمومية، بغض النظر عن الموقع الفعلي لعنوان IP للخدمة Office 365 التي يطلبها.

- تمثل بادئات IP المضمنة في كل قيمة مجتمع BGP شبكة فرعية تحتوي على عناوين IP لتطبيق Office 365 المقترن بالقيمة. في بعض الحالات، يحتوي أكثر من تطبيق Office 365 واحد على عناوين IP داخل شبكة فرعية مما يؤدي إلى وجود بادئة IP في أكثر من قيمة مجتمع واحدة. هذا متوقع، على الرغم من نادرا، السلوك بسبب تجزئة التخصيص ولا يؤثر على عدد البادئة أو أهداف إدارة النطاق الترددي. يتم تشجيع العملاء على استخدام نهج "السماح بما هو مطلوب" بدلا من "رفض ما لا حاجة إليه" عند الاستفادة من مجتمعات BGP Office 365 لتقليل التأثير.

- لا يؤدي استخدام مجتمعات BGP إلى تغيير متطلبات اتصال الشبكة الأساسية أو التكوين المطلوب لاستخدام Office 365. لا يزال العملاء الذين يرغبون في الوصول إلى Office 365 مطلوبين لكي يتمكنوا من الوصول إلى الإنترنت.

- لا يؤثر تحديد نطاق Azure ExpressRoute مع مجتمعات BGP إلا على المسارات التي يمكن أن تراها شبكتك الداخلية عبر علاقة تناظر Microsoft. قد تحتاج إلى إجراء تكوينات إضافية على مستوى التطبيق مثل استخدام تكوين PAC أو WPAD بالتزامن مع التوجيه المحدد النطاق.

- بالإضافة إلى استخدام مجتمعات BGP المعينة من Microsoft، قد يختار العملاء تعيين مجتمعات BGP الخاصة بهم Office 365 بادئات IP التي تم تعلمها من خلال Azure ExpressRoute للتأثير على التوجيه الداخلي. حالة الاستخدام الشائعة هي تعيين مجتمع BGP يستند إلى موقع لجميع المسارات التي تم تعلمها من خلال كل موقع تناظر ExpressRoute معين ثم استخدام انتقال المعلومات من الخادم في شبكة العملاء لتنسيق مسار الشبكة الأقصر أو الأكثر تفضيلا في شبكة Microsoft. استخدام مجتمعات BGP المعينة من قبل العميل مع ExpressRoute لسيناريوهات Office 365 خارج نطاق تحكم Microsoft أو الرؤية.

فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/bgpexpressroute365]().
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[تقييم اتصال الشبكة Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute ل Office 365](azure-expressroute.md)
  
[إدارة ExpressRoute للاتصال Office 365](managing-expressroute-for-connectivity.md)
  
[التوجيه باستخدام ExpressRoute لـ Office 365](routing-with-expressroute.md)
  
[تخطيط الشبكة باستخدام ExpressRoute لـ Office 365](network-planning-with-expressroute.md)
  
[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute وQoS في Skype for Business Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[تدفق المكالمات باستخدام ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[تنفيذ ExpressRoute Office 365](implementing-expressroute.md)
  
[دعم مجتمعات BGP](/azure/expressroute/expressroute-routing)
  
[ضبط الأداء Office 365 باستخدام الخطوط الأساسية ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)
  
[خطة استكشاف أخطاء الأداء وإصلاحها Office 365](performance-troubleshooting-plan.md)
  
[Azure ExpressRoute للتدريب على Office 365](https://channel9.msdn.com/series/aer)