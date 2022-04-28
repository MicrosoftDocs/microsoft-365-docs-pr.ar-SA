---
title: Azure ExpressRoute ل Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية استخدام Azure ExpressRoute مع Office 365 وتخطيط مشروع تنفيذ الشبكة إذا كنت تقوم بالنشر معه.
ms.openlocfilehash: bbb53913ede8a51d5e6d9bf6e39386cd3e8de304
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096843"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute ل Office 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

تعرف على كيفية استخدام Azure ExpressRoute مع Office 365 وكيفية تخطيط مشروع تنفيذ الشبكة المطلوب إذا كنت تقوم بنشر Azure ExpressRoute للاستخدام مع Office 365. غالبا ما تستفيد خدمات البنية الأساسية والنظام الأساسي التي تعمل في Azure من خلال معالجة اعتبارات بنية الشبكة والأداء. نوصي باستخدام ExpressRoute ل Azure في هذه الحالات. تم إنشاء عروض البرامج كخدمة مثل Office 365 و Dynamics 365 للوصول إليها بشكل آمن وموثوق عبر الإنترنت. يمكنك القراءة حول أداء الإنترنت والأمان ومتى قد تفكر في Azure ExpressRoute Office 365 في [المقالة تقييم اتصال الشبكة Office 365](assessing-network-connectivity.md).

> [!NOTE]
> لا يوفر Microsoft Defender لنقطة النهاية التكامل مع Azure ExpressRoute. في حين أن هذا لا يمنع العملاء من تحديد قواعد ExpressRoute التي تمكن الاتصال من شبكة خاصة إلى Microsoft Defender لنقطة النهاية الخدمات السحابية، فإن الأمر متروك للعميل للحفاظ على القواعد مع تطور الخدمة أو البنية الأساسية السحابية.

> [!NOTE]
> لا نوصي باستخدام ExpressRoute Microsoft 365 لأنه لا يوفر أفضل نموذج اتصال للخدمة في معظم الحالات. على هذا النحو، يلزم تخويل Microsoft لاستخدام نموذج الاتصال هذا Microsoft 365. نراجع كل طلب عميل ونخول ExpressRoute Microsoft 365 فقط في السيناريوهات النادرة حيث يكون ذلك ضروريا. يرجى قراءة [دليل ExpressRoute Microsoft 365](https://aka.ms/erguide) للحصول على مزيد من المعلومات ومتابعة مراجعة شاملة للمستند مع فرق الإنتاجية والشبكة والأمان، والعمل مع فريق حساب Microsoft لإرسال استثناء إذا لزم الأمر. ستتلقى الاشتراكات غير المصرح بها التي تحاول إنشاء عوامل تصفية التوجيه Office 365 [رسالة خطأ](https://support.microsoft.com/kb/3181709).

## <a name="planning-azure-expressroute-for-office-365"></a>التخطيط ل Azure ExpressRoute Office 365

بالإضافة إلى الاتصال بالإنترنت، يمكنك اختيار توجيه مجموعة فرعية من نسبة استخدام الشبكة Office 365 عبر اتصال مباشر يوفر إمكانية التنبؤ وSLA وقت التشغيل بنسبة 99.95٪ لمكونات شبكة Microsoft. يوفر لك Azure ExpressRoute اتصال الشبكة المخصص هذا Office 365 وخدمات Microsoft السحابية الأخرى.

بغض النظر عما إذا كان لديك شبكة MPLS WAN موجودة، يمكن إضافة ExpressRoute إلى بنية الشبكة بإحدى الطرق الثلاث؛ من خلال موفر موقع مشترك لتبادل السحابة مدعوم، أو موفر اتصال Ethernet من نقطة إلى نقطة، أو من خلال موفر اتصال MPLS. تعرف على [الموفرين المتوفرين في منطقتك](/azure/expressroute/expressroute-locations). سيؤدي اتصال ExpressRoute المباشر إلى تمكين الاتصال بالتطبيقات الموضحة في [ما هي خدمات Office 365 المضمنة أدناه.](azure-expressroute.md#BKMK_WhatDoIGet) ستستمر نسبة استخدام الشبكة لجميع التطبيقات والخدمات الأخرى في اجتياز الإنترنت.

ضع في اعتبارك الرسم التخطيطي التالي لشبكة الاتصال عالية المستوى الذي يعرض عميلا نموذجيا Office 365 يتصل بمراكز بيانات Microsoft عبر الإنترنت للوصول إلى جميع تطبيقات Microsoft مثل Office 365 Windows Update وTechNet. يستخدم العملاء مسار شبكة مشابها بغض النظر عما إذا كانوا يتصلون من شبكة محلية أو من اتصال مستقل بالإنترنت.

![Office 365 اتصال الشبكة.](../media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

الآن انظر إلى الرسم التخطيطي المحدث الذي يصور عميلا Office 365 يستخدم كل من الإنترنت وExpressRoute للاتصال Office 365. لاحظ أن بعض الاتصالات مثل DNS العامة وعقد شبكة تسليم المحتوى لا تزال تتطلب اتصالا عاما بالإنترنت. لاحظ أيضا أن مستخدمي العميل غير الموجودين في مبنى ExpressRoute المتصل يتصلون عبر الإنترنت.

![Office 365 الاتصال مع ExpressRoute.](../media/251788c4-0937-4584-9b2c-df08e11611fc.png)

هل ما زلت بحاجة إلى مزيد من المعلومات؟ تعرف على كيفية [إدارة نسبة استخدام الشبكة باستخدام Azure ExpressRoute Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) وتعلم كيفية [تكوين Azure ExpressRoute Office 365](/azure/expressroute/expressroute-faqs). لقد سجلنا أيضا 10 أجزاء من [Azure ExpressRoute لسلسلة تدريب Office 365](https://channel9.msdn.com/series/aer) على القناة 9 للمساعدة في شرح المفاهيم بشكل أكثر شمولا.

## <a name="what-office-365-services-are-included"></a>ما هي خدمات Office 365 المضمنة؟
<a name="BKMK_WhatDoIGet"> </a>

يسرد الجدول التالي خدمات Office 365 المعتمدة عبر ExpressRoute. الرجاء مراجعة [مقالة نقاط النهاية Office 365](./urls-and-ip-address-ranges.md) لفهم طلبات الشبكة لهذه التطبيقات التي تتطلب الاتصال بالإنترنت.

| التطبيقات المضمنة |
|:-----|
|Exchange Online <sup>1</sup> <br/> Exchange Online Protection <sup>1</sup> <br/> Delve <sup>1</sup> <br/> |
|Skype for Business <sup>Online1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint <sup>Online1</sup> <br/> OneDrive for Business <sup>1</sup> <br/> Project Online <sup>1</sup> <br/> |
|المدخل <sup>والمشاركة1</sup> <br/> Azure Active Directory (Azure AD) <sup>1</sup> <br/> Azure AD الاتصال <sup>1</sup> <br/> Office <sup>1</sup> <br/> |

<sup>1</sup> لكل تطبيق من هذه التطبيقات متطلبات اتصال بالإنترنت غير معتمدة عبر ExpressRoute، راجع [مقالة نقاط النهاية Office 365](./urls-and-ip-address-ranges.md) لمزيد من المعلومات.

الخدمات غير المضمنة مع ExpressRoute Office 365 هي Microsoft 365 Apps for enterprise تنزيلات العميل وتسجيل الدخول الداخلي لموفر الهوية وخدمة Office 365 (المشغلة بواسطة 21 Vianet) في الصين.

## <a name="implementing-expressroute-for-office-365"></a>تنفيذ ExpressRoute Office 365

يتطلب تنفيذ ExpressRoute مشاركة مالكي الشبكة والتطبيقات ويتطلب تخطيطا دقيقا لتحديد [بنية توجيه الشبكة](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) الجديدة ومتطلبات النطاق الترددي، حيث سيتم تنفيذ الأمان، وقابلية الوصول العالية، وما إلى ذلك. لتنفيذ ExpressRoute، ستحتاج إلى:

1. فهم الحاجة إلى ExpressRoute بشكل كامل في تخطيط الاتصال Office 365. فهم التطبيقات التي ستستخدم الإنترنت أو ExpressRoute والتخطيط الكامل لقدرات الشبكة والأمان واحتياجات قابلية الوصول العالية في سياق استخدام كل من الإنترنت وExpressRoute لنسبة استخدام الشبكة Office 365.

2. تحديد مواقع الخروج والتناظر لكل من الإنترنت وExpressRoute <sup>traffic1</sup>.

3. تحديد السعة المطلوبة على الإنترنت واتصالات ExpressRoute.

4. ضع خطة لتنفيذ عناصر التحكم الأمنية وغيرها من عناصر التحكم القياسية <sup>المحيطة1</sup>.

5. امتلاك حساب Microsoft Azure صالح للاشتراك في ExpressRoute.

6. حدد نموذج اتصال [وموفر معتمد](/azure/expressroute/expressroute-locations). ضع في اعتبارك أنه يمكن للعملاء تحديد نماذج اتصال أو شركاء متعددين ولا يحتاج الشريك إلى أن يكون هو نفسه موفر الشبكة الحالي.

7. التحقق من صحة النشر قبل توجيه نسبة استخدام الشبكة إلى ExpressRoute.

8. [تنفيذ QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) وتقييم التوسع الإقليمي اختياريا.

<sup>1</sup> اعتبارات الأداء الهامة. يمكن أن تؤثر القرارات هنا بشكل كبير على زمن الانتقال وهو أمر بالغ الأهمية لتطبيقات مثل Skype for Business.

للحصول على مراجع إضافية، استخدم [دليل التوجيه](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) بالإضافة إلى [وثائق ExpressRoute](/azure/expressroute/expressroute-introduction).

لشراء ExpressRoute Office 365، ستحتاج إلى العمل مع [موفر](/azure/expressroute/expressroute-locations) معتمد واحد أو أكثر لتوفير دوائر العدد والحجم المطلوبة مع اشتراك ExpressRoute Premium. لا توجد تراخيص إضافية للشراء من Office 365.

فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/expressrouteoffice365]()

هل أنت جاهز للتسجيل في [ExpressRoute للحصول على Office 365](https://aka.ms/ert)؟

## <a name="related-topics"></a>المواضيع ذات الصلة

[تقييم اتصال الشبكة Office 365](assessing-network-connectivity.md)

[إدارة ExpressRoute للاتصال Office 365](managing-expressroute-for-connectivity.md)

[التوجيه باستخدام ExpressRoute لـ Office 365](routing-with-expressroute.md)

[تخطيط الشبكة باستخدام ExpressRoute لـ Office 365](network-planning-with-expressroute.md)

[تنفيذ ExpressRoute Office 365](implementing-expressroute.md)

[استخدام مجتمعات BGP في ExpressRoute لسيناريوهات Office 365](bgp-communities-in-expressroute.md)

[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[ضبط الأداء Office 365 باستخدام الخطوط الأساسية ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)

[خطة استكشاف أخطاء الأداء وإصلاحها Office 365](performance-troubleshooting-plan.md)

[نطاقات عناوين IP وعناوين URL في Office 365](urls-and-ip-address-ranges.md)

[Office 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على Microsoft 365 Enterprise](microsoft-365-overview.md)
