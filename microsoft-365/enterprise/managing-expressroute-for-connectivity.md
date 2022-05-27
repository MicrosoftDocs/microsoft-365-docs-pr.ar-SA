---
title: إدارة ExpressRoute للاتصال Office 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 7/13/2017
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
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: تعرف على كيفية إدارة ExpressRoute Office 365، بما في ذلك المجالات الشائعة لتكوينها مثل تصفية البادئة والأمان والتوافق.
ms.openlocfilehash: 493a7c0ca14d05a2b84763b9e9485f828574a930
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753859"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>إدارة ExpressRoute للاتصال Office 365

يوفر ExpressRoute ل Office 365 مسار توجيه بديلا للوصول إلى العديد من خدمات Office 365 دون الحاجة إلى جميع نسبة استخدام الشبكة للانحراف إلى الإنترنت. على الرغم من أن الاتصال بالإنترنت Office 365 لا يزال مطلوبا، فإن المسارات المحددة التي تعلن عنها Microsoft من خلال BGP إلى شبكتك تجعل دائرة ExpressRoute المباشرة مفضلة ما لم تكن هناك تكوينات أخرى في شبكتك. تتضمن المجالات الثلاثة الشائعة التي قد ترغب في تكوينها لإدارة هذا التوجيه تصفية البادئة والأمان والتوافق.
  
> [!NOTE]
> قامت Microsoft بتغيير كيفية مراجعة مجال توجيه Microsoft Peering ل Azure ExpressRoute. بدءا من 31 يوليو 2017، يمكن لجميع عملاء Azure ExpressRoute تمكين Microsoft Peering مباشرة من وحدة تحكم Azure الإدارية أو عبر PowerShell. بعد تمكين Microsoft Peering، يمكن لأي عميل إنشاء عوامل تصفية توجيه لتلقي إعلانات مسار BGP لتطبيقات Dynamics 365 Customer Engagement (المعروفة سابقا باسم CRM Online). يجب على العملاء الذين يحتاجون إلى Azure ExpressRoute Office 365 الحصول على مراجعة من Microsoft قبل أن يتمكنوا من إنشاء عوامل تصفية التوجيه Office 365. الرجاء الاتصال بفريق حساب Microsoft للتعرف على كيفية طلب مراجعة لتمكين Office 365 ExpressRoute. ستتلقى الاشتراكات غير المصرح بها التي تحاول إنشاء عوامل تصفية التوجيه Office 365 [رسالة خطأ](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>تصفية البادئة

توصي Microsoft العملاء بقبول جميع مسارات BGP كما هو معلن من Microsoft، وتخضع المسارات المقدمة لعملية مراجعة والتحقق من الصحة صارمة لإزالة أي فوائد للتدقيق الإضافي. يوفر ExpressRoute في الأصل عناصر التحكم الموصى بها مثل ملكية بادئة IP، والتكامل، والمقياس - دون تصفية المسار الوارد على جانب العميل.
  
إذا كنت بحاجة إلى التحقق من صحة ملكية المسار عبر نظير ExpressRoute العام، يمكنك التحقق من المسارات المعلن عنها مقابل قائمة جميع بادئات IP IPv4 وIPv6 التي تمثل [نطاقات IP العامة ل Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). تغطي هذه النطاقات مساحة عنوان Microsoft الكاملة وتتغير بشكل غير متكرر، ما يوفر مجموعة موثوقة من النطاقات للتصفية مقابل تلك التي توفر أيضا حماية إضافية للعملاء المعنيين بالمسارات غير المملوكة ل Microsoft التي تتسرب إلى بيئتهم. في حالة وجود تغيير، سيتم إجراؤه في الأول من الشهر وسيتغير رقم الإصدار في قسم **التفاصيل** في الصفحة في كل مرة يتم فيها تحديث الملف.
  
هناك العديد من الأسباب لتجنب استخدام [عناوين URL Office 365 ونطاقات عناوين IP](./urls-and-ip-address-ranges.md) لإنشاء قوائم تصفية البادئة. بما في ذلك ما يلي:
  
- تخضع بادئات IP Office 365 الكثير من التغييرات بشكل متكرر.

- تم تصميم عناوين URL Office 365 ونطاقات عناوين IP لإدارة قوائم السماح لجدار الحماية والبنية الأساسية للوكيل، وليس التوجيه.

- لا تغطي نطاقات عناوين IP وعناوين URL Office 365 خدمات Microsoft الأخرى التي قد تكون في نطاق اتصالات ExpressRoute.

|**الخيار**|**تعقيد**|**تغيير عنصر التحكم**|
|:-----|:-----|:-----|
|قبول جميع مسارات Microsoft  <br/> |**منخفضه:** يعتمد العميل على عناصر تحكم Microsoft لضمان امتلاك جميع المسارات بشكل صحيح.  <br/> |None  <br/> |
|تصفية الشبكات الفائقة المملوكة ل Microsoft  <br/> |**المتوسطه:** يقوم العميل بتنفيذ قوائم تصفية البادئة الملخصة للسماح فقط بالمسارات المملوكة ل Microsoft.  <br/> |يجب على العملاء التأكد من أن التحديثات غير المتكررة تنعكس في عوامل تصفية المسار.  <br/> |
|تصفية نطاقات IP Office 365  <br/> [!CAUTION] Not-Recommended |**عاليه:** يقوم العميل بتصفية المسارات استنادا إلى بادئات IP Office 365 المحددة.  <br/> |يجب على العملاء تنفيذ عملية قوية لإدارة التغيير للتحديثات الشهرية.  <br/> [!CAUTION] يتطلب هذا الحل تغييرات مستمرة كبيرة. من المحتمل أن تؤدي التغييرات التي لم يتم تنفيذها في الوقت المناسب إلى انقطاع الخدمة.   |

يعتمد الاتصال Office 365 باستخدام Azure ExpressRoute على إعلانات BGP لشبكات IP الفرعية المحددة التي تمثل الشبكات التي يتم فيها نشر نقاط نهاية Office 365. نظرا للطبيعة العالمية Office 365 وعدد الخدمات التي تشكل Office 365، غالبا ما يحتاج العملاء إلى إدارة الإعلانات التي يقبلونها على شبكتهم. إذا كنت مهتما بعدد البادئات المعلن عنها في بيئتك، فإن ميزة [مجتمع BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) تسمح لك بتصفية الإعلانات إلى مجموعة معينة من خدمات Office 365. هذه الميزة قيد المعاينة الآن.
  
بغض النظر عن كيفية إدارة إعلانات مسار BGP الواردة من Microsoft، لن تحصل على أي تعرض خاص لخدمات Office 365 عند مقارنتها بالاتصال Office 365 عبر دائرة الإنترنت وحدها. تحتفظ Microsoft بنفس مستويات الأمان والتوافق والأداء بغض النظر عن نوع الدائرة التي يستخدمها العميل للاتصال Office 365.
  
### <a name="security"></a>الأمان

توصي Microsoft بالحفاظ على عناصر التحكم الخاصة بالشبكة والأمان المحيطة للاتصالات التي تنتقل من وإلى إقران ExpressRoute العام وMicrosoft، والذي يتضمن اتصالات من خدمات Office 365 وإلصادرها. يجب أن تكون عناصر التحكم في الأمان في مكانها لطلبات الشبكة التي تنتقل إلى الخارج من شبكتك إلى شبكة Microsoft والواردة من شبكة Microsoft إلى شبكتك.
  
#### <a name="outbound-from-customer-to-microsoft"></a>الصادرة من العميل إلى Microsoft
  
عندما تتصل أجهزة الكمبيوتر Office 365، فإنها تتصل بنفس مجموعة نقاط النهاية بغض النظر عما إذا كان الاتصال يتم عبر الإنترنت أو دائرة ExpressRoute. بغض النظر عن الدائرة المستخدمة، توصي Microsoft بمعاملة خدمات Office 365 على أنها أكثر موثوقية من وجهات الإنترنت العامة. يجب أن تركز عناصر التحكم في الأمان الصادرة على المنافذ والبروتوكولات لتقليل التعرض وتقليل الصيانة المستمرة. تتوفر معلومات المنفذ المطلوبة في المقالة المرجعية [لنقاط النهاية Office 365](./urls-and-ip-address-ranges.md).
  
بالنسبة لعناصر التحكم المضافة، يمكنك استخدام تصفية مستوى FQDN داخل البنية الأساسية للوكيل لتقييد أو فحص بعض طلبات الشبكة المخصصة للإنترنت أو Office 365 أو فحصها. يتطلب الاحتفاظ بقائمة FQDNs مع إصدار الميزات وتطوير عروض Office 365 إدارة تغيير أكثر قوة وتعقب التغييرات على [نقاط نهاية Office 365 المنشورة](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> توصي Microsoft بعدم الاعتماد فقط على بادئات IP لإدارة الأمان الصادر إلى Office 365.

|**الخيار**|**تعقيد**|**تغيير عنصر التحكم**|
|:-----|:-----|:-----|
|لا توجد قيود  <br/> |**منخفضه:** يسمح العميل بالوصول الصادر غير المقيد إلى Microsoft.  <br/> |None  <br/> |
|قيود المنفذ  <br/> |**منخفضه:** يقيد العميل الوصول الصادر إلى Microsoft بواسطة المنافذ المتوقعة.  <br/> |نادره.  <br/> |
|قيود FQDN  <br/> |**عاليه:** يقيد العميل الوصول الصادر إلى Office 365 استنادا إلى FQDNs المنشورة.  <br/> |التغييرات الشهرية.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>الواردة من Microsoft إلى العميل
  
هناك العديد من السيناريوهات الاختيارية التي تتطلب من Microsoft بدء الاتصالات بالشبكة.
  
- ADFS أثناء التحقق من صحة كلمة المرور لتسجيل الدخول.

- [Exchange Server عمليات النشر المختلطة](/exchange/exchange-hybrid).

- البريد من مستأجر Exchange Online إلى مضيف محلي.

- SharePoint Online Mail المرسل من SharePoint Online إلى مضيف محلي.

- [SharePoint البحث المختلط المتحد](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS المختلطة](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business الاتحاد المختلط](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) و/أو [Skype for Business](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).

- [Skype for Business Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

توصي Microsoft بقبول هذه الاتصالات عبر دائرة الإنترنت بدلا من دائرة ExpressRoute لتقليل التعقيد. إذا كانت احتياجات التوافق أو الأداء الخاصة بك تملي هذه الاتصالات الواردة يجب قبولها عبر دائرة ExpressRoute، باستخدام جدار حماية أو وكيل عكسي لتحديد نطاق الاتصالات المقبولة يوصى بها. يمكنك استخدام [نقاط النهاية Office 365](./urls-and-ip-address-ranges.md) لمعرفة FQDNs وبادئات IP الصحيحة.
  
### <a name="compliance"></a>التوافق

لا نعتمد على مسار التوجيه الذي تستخدمه لأي من عناصر التحكم في التوافق لدينا. بغض النظر عما إذا كنت تتصل بخدمات Office 365 عبر ExpressRoute أو دائرة الإنترنت، لن تتغير عناصر التحكم في التوافق لدينا. يجب عليك مراجعة مستويات شهادات التوافق والأمان المختلفة Office 365 لمعرفة الخيار الأفضل لتلبية احتياجات مؤسستك.
  
فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[شبكات تسليم المحتوى](content-delivery-networks.md)
  
[نطاقات عناوين IP وعناوين URL في Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[إدارة نقاط نهاية Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute للتدريب على Office 365](https://channel9.msdn.com/series/aer)