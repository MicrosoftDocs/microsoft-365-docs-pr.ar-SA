---
title: Azure ExpressRoute Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
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
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: تعرف على كيفية استخدام Azure ExpressRoute Office 365 تخطيط مشروع تنفيذ الشبكة إذا كنت تقوم بالنشر معه.
ms.openlocfilehash: 9a4f4be76751ec03610bd766f51ec91526ca18a4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575273"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute Office 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

تعرف على كيفية استخدام Azure ExpressRoute مع Office 365 وكيفية تخطيط مشروع تنفيذ الشبكة الذي سيكون مطلوبا إذا كنت تقوم بنشر Azure ExpressRoute لاستخدامه مع Office 365. غالبا ما تستفيد خدمات البنية الأساسية و النظام الأساسي التي يتم تشغيلها في Azure من خلال معالجة اعتبارات بنية الشبكة والأداء. نوصي ExpressRoute for Azure في هذه الحالات. تم تصميم البرامج كخدمة مثل Office 365 و Dynamics 365 للوصول إليها بأمان وموثوقية عبر الإنترنت. يمكنك القراءة حول أداء الإنترنت والأمان ومتى يمكنك التفكير في Azure ExpressRoute Office 365 في المقالة تقييم Office 365 [اتصال الشبكة](assessing-network-connectivity.md).

> [!NOTE]
> لا يوفر Microsoft Defender ل Endpoint التكامل مع Azure ExpressRoute. على الرغم من أن هذا لا يمنع العملاء من تحديد قواعد ExpressRoute التي تمكن الاتصال من شبكة خاصة ب Microsoft Defender للخدمات السحابية لنقطة النهاية، فإن الأمر متروك للعميل للحفاظ على القواعد مع تطور الخدمة أو البنية الأساسية السحابية.

> [!NOTE]
> لا نوصي باستخدام ExpressRoute Microsoft 365 لأنه لا يوفر نموذج الاتصال الأفضل للخدمة في معظم الحالات. على هذا النحو، يلزم تخويل Microsoft لاستخدام نموذج الاتصال هذا Microsoft 365. نقوم بمراجعة كل طلب عميل و تخويل ExpressRoute Microsoft 365 فقط في السيناريوهات النادرة حيث يكون ذلك ضروريا. الرجاء قراءة دليل [ExpressRoute for Microsoft 365](https://aka.ms/erguide) للحصول على مزيد من المعلومات، وبعد مراجعة شاملة للمستند باستخدام فرق الأمان والشبكات والإنتاجية، اعمل مع فريق حساب Microsoft لإرسال استثناء إذا لزم الأمر. ستتلقى الاشتراكات غير المصرح بها التي تحاول إنشاء عوامل تصفية المسار Office 365 رسالة [خطأ](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>التخطيط ل Azure ExpressRoute Office 365

بالإضافة إلى الاتصال بالإنترنت، يمكنك اختيار توجيه مجموعة فرعية من حركة مرور شبكة Office 365 عبر اتصال مباشر يوفر إمكانية التنبؤ وSLA وقت تشغيل بنسبة 99.95٪ لمكونات شبكة Microsoft. يوفر لك Azure ExpressRoute اتصال الشبكة المخصص هذا Office 365 خدمات Microsoft السحابية الأخرى.

بغض النظر عما إذا كان لديك MPLS WAN موجود، يمكن إضافة ExpressRoute إلى بنية الشبكة بوا واحدة من ثلاث طرق؛ من خلال موفر موقع تبادل سحابي مدعم، أو موفر اتصال نقطة إلى نقطة Ethernet، أو من خلال موفر اتصال MPLS. تعرف على [الموفرين المتوفرين في المنطقة](/azure/expressroute/expressroute-locations). سيمكن اتصال ExpressRoute المباشر الاتصال للتطبيقات الموضحة في [Office 365 الخدمات المضمنة؟](azure-expressroute.md#BKMK_WhatDoIGet) أدناه. سيستمر مرور الشبكة لجميع التطبيقات والخدمات الأخرى في اجتياز الإنترنت.

فكر في الرسم التخطيطي التالي للشبكة عالية المستوى الذي يعرض عميل Office 365 نموذجي يتصل ب مراكز بيانات Microsoft عبر الإنترنت للوصول إلى جميع تطبيقات Microsoft مثل Office 365 و Windows Update و TechNet. يستخدم العملاء مسار شبكة مماثلا بغض النظر عما إذا كانوا يتصلون من شبكة المحلية أو من اتصال إنترنت مستقل.

![Office 365 اتصال الشبكة.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

انظر الآن إلى الرسم التخطيطي الذي تم تحديثه والذي Office 365 عميل يستخدم كل من الإنترنت و ExpressRoute للاتصال Office 365. لاحظ أن بعض الاتصالات مثل عقد DNS العامة وشبكة تسليم المحتوى لا تزال تتطلب اتصال الإنترنت العام. لاحظ أيضا أن مستخدمي العميل الذين لم يتم تحديد موقعهم في المبنى المتصل في ExpressRoute يتصلون بالإنترنت.

![Office 365 الاتصال باستخدام ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

هل ما زلت تريد الحصول على مزيد من المعلومات؟ تعرف على [كيفية إدارة حركة مرور الشبكة باستخدام Azure ExpressRoute Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) وتعرف على كيفية تكوين [Azure ExpressRoute Office 365](/azure/expressroute/expressroute-faqs). لقد سجلنا أيضا سلسلة تدريب من [Azure ExpressRoute](https://channel9.msdn.com/series/aer) Office 365 10 جزء على القناة 9 للمساعدة في شرح المفاهيم بشكل أكثر دقة.

## <a name="what-office-365-services-are-included"></a>ما Office 365 الخدمات المضمنة؟
<a name="BKMK_WhatDoIGet"> </a>

يسرد الجدول التالي Office 365 الخدمات المعتمدة عبر ExpressRoute. الرجاء مراجعة [مقالة Office 365](./urls-and-ip-address-ranges.md) نقاط النهاية لفهم طلبات الشبكة لهذه التطبيقات التي تتطلب اتصالا بالإنترنت.

| التطبيقات المضمنة |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype for Business <sup>Online1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint <sup>Online1</sup> <br/> OneDrive for Business <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|المدخل <sup>والمشترك1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD الاتصال <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> يحتوي كل من هذه التطبيقات على متطلبات اتصال بالإنترنت غير معتمدة عبر ExpressRoute، راجع مقالة [](./urls-and-ip-address-ranges.md) نقاط Office 365 نقاط النهاية للحصول على مزيد من المعلومات.

الخدمات غير المضمنة مع ExpressRoute ل Office 365 هي تنزيلات عميل Microsoft 365 Apps for enterprise، تسجيل الدخول إلى موفر الهوية المحلي، وخدمة Office 365 (التي يتم تشغيلها بواسطة 21 Vianet) في الصين.

## <a name="implementing-expressroute-for-office-365"></a>تنفيذ ExpressRoute Office 365

يتطلب تنفيذ ExpressRoute مشاركة مالكي الشبكة والتطبيقات ويتطلب تخطيطا دقيقا لتحديد بنية توجيه الشبكة الجديدة [](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408)ومتطلبات النطاق الترددي، حيث سيتم تطبيق الأمان، والتوفر العالي، وما إلى ذلك. لتنفيذ ExpressRoute، ستحتاج إلى:

1. فهم كامل لحاجة ExpressRoute في تخطيط الاتصال Office 365 الخاص بك. تعرف على التطبيقات التي ستستخدم الإنترنت أو ExpressRoute وخطط سعة الشبكة والأمان واحتياجات التوفر العالية بشكل كامل في سياق استخدام كل من الإنترنت و ExpressRoute Office 365 المرور.

2. تحديد مواقع الخروج والنظير لكل من الإنترنت و ExpressRoute <sup>traffic1</sup>.

3. تحديد السعة المطلوبة على الإنترنت واتصالات ExpressRoute.

4. ضع خطة لتطبيق الأمان وغيرها من عناصر التحكم بالمحيط الخارجي <sup>القياسية1</sup>.

5. لديك حساب Microsoft Azure صالح للاشتراك في ExpressRoute.

6. حدد نموذج اتصال [وموفر معتمد](/azure/expressroute/expressroute-locations). ضع في اعتبارك أنه يمكن للعملاء تحديد عدة نماذج اتصال أو شركاء، ولا يحتاج الشريك إلى أن يكون هو نفسه موفر الشبكة الحالي.

7. تحقق من صحة النشر قبل توجيه حركة المرور إلى ExpressRoute.

8. تنفيذ [QoS وتقييم](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) التوسع الإقليمي بشكل اختياري.

<sup>1</sup> اعتبارات الأداء المهمة. يمكن أن تؤثر القرارات هنا بشكل كبير على زمن زمن التأخر الذي يكون أمرا بالغ الأهمية للتطبيقات مثل Skype for Business.

للحصول على مراجع إضافية، استخدم [دليل](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) التوجيه بالإضافة إلى وثائق [ExpressRoute](/azure/expressroute/expressroute-introduction).

لشراء ExpressRoute Office 365، ستحتاج إلى العمل مع موفر معتمد واحد أو أكثر لتوفير دوائر الأرقام والحجم [](/azure/expressroute/expressroute-locations) المطلوبة باستخدام اشتراك ExpressRoute Premium. لا توجد تراخيص إضافية للشراء من Office 365.

إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/expressrouteoffice365]()

هل أنت جاهز التسجيل في [ExpressRoute Office 365](https://aka.ms/ert)؟

## <a name="related-topics"></a>مواضيع ذات صلة

[تقييم Office 365 الشبكة](assessing-network-connectivity.md)

[إدارة ExpressRoute Office 365 الاتصال](managing-expressroute-for-connectivity.md)

[التوجيه باستخدام ExpressRoute Office 365](routing-with-expressroute.md)

[تخطيط الشبكة باستخدام ExpressRoute Office 365](network-planning-with-expressroute.md)

[تنفيذ ExpressRoute Office 365](implementing-expressroute.md)

[استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365](bgp-communities-in-expressroute.md)

[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Office 365 الأداء باستخدام الأساسات ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)

[خطة استكشاف الأخطاء وإصلاحها Office 365](performance-troubleshooting-plan.md)

[نطاقات عناوين IP وعناوين URL في Office 365](urls-and-ip-address-ranges.md)

[Office 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 Enterprise عامة](microsoft-365-overview.md)
