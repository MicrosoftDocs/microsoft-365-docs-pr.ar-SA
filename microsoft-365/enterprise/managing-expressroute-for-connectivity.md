---
title: إدارة ExpressRoute Office 365 الاتصال
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية إدارة ExpressRoute Office 365، بما في ذلك المناطق الشائعة لتكوين مثل تصفية البادأ والأمان والتوافق.
ms.openlocfilehash: bffe82249a9d8a531ee85525f9db0eb38a344d50
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572884"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>إدارة ExpressRoute Office 365 الاتصال

يوفر ExpressRoute for Office 365 مسار توجيه بديل للوصول إلى العديد من خدمات Office 365 دون الحاجة إلى كل حركة المرور للانحدار إلى الإنترنت. على الرغم من أن الاتصال بالإنترنت Office 365 ما زال مطلوبا، إلا أن المسارات المحددة التي تعلن عنها Microsoft عبر BGP إلى شبكتك تجعل دائرة ExpressRoute المباشرة مفضلة ما لم تكن هناك تكوينات أخرى في شبكتك. تتضمن المناطق الثلاث الشائعة التي قد ترغب في تكوينها لإدارة هذا التوجيه تصفية البادرة والأمان والتوافق.
  
> [!NOTE]
> قامت Microsoft بتغيير كيفية مراجعة مجال توجيه النظير من Microsoft ل Azure ExpressRoute. بدءا من 31 يوليو 2017، يمكن لجميع عملاء Azure ExpressRoute تمكين نظير Microsoft مباشرة من وحدة تحكم Azure الإدارية أو عبر PowerShell. بعد تمكين "نظير Microsoft"، يمكن لأي عميل إنشاء عوامل تصفية المسار لتلقي إعلانات مسار BGP للتطبيقات "مشاركة العملاء في Dynamics 365" (المعروفة سابقا باسم CRM Online). يجب على العملاء الذين يحتاجون إلى Azure ExpressRoute Office 365 الحصول على مراجعة من Microsoft قبل أن يمكنهم إنشاء عوامل تصفية المسار Office 365. يرجى الاتصال بفريق حساب Microsoft للتعرف على كيفية طلب مراجعة لتمكين Office 365 ExpressRoute. ستتلقى الاشتراكات غير المصرح بها التي تحاول إنشاء عوامل تصفية المسار Office 365 رسالة [خطأ](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>تصفية الباد ة

توصي Microsoft بأن يقبل العملاء جميع مسارات BGP كما هو معلن عنه من Microsoft، تخضع المسارات المتوفرة لعملية مراجعة والتحقق من الصحة صارمة تزيل أي فوائد للتدقيق الإضافي. يوفر ExpressRoute بشكل أصلي عناصر التحكم الموصى بها مثل ملكيةبادات IP وتكاملها ومقياسها - بدون تصفية المسار الوارد من جانب العميل.
  
إذا كنت تحتاج إلى التحقق من صحة إضافية لملكية المسار عبر النظير العام ل ExpressRoute، يمكنك التحقق من المسارات المعلن عنها مقابل قائمة جميعبادات IP IPv4 و IPv6 التي تمثل نطاقات IP العامة ل [Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). تغطي هذه النطاقات مساحة عنوان Microsoft الكاملة وتتغير بشكل غير متكامل، مما يوفر مجموعة موثوقة من النطاقات للتصفية مقابل ذلك يوفر أيضا حماية إضافية للعملاء القلقين بشأن المسارات المملوكة لغير Microsoft التي يتم تسريبها إلى بيئتهم. في حال وجود تغيير، سيتم تغييره في الأول من الشهر وسيتغير رقم الإصدار في مقطع التفاصيل في الصفحة في كل مرة يتم فيها  تحديث الملف.
  
هناك عدد من الأسباب لتجنب استخدام نطاقات عناوين IP Office 365 URL ونطاقات [عناوين IP](./urls-and-ip-address-ranges.md) في إنشاء قوائم تصفية البادأه. بما في ذلك ما يلي:
  
- تخضع Office 365 IP للبادئات الكثير من التغييرات بشكل متكرر.

- تم Office 365 عناوين URL وIP لإدارة قوائم السماح بجدار الحماية والبنية الأساسية للوكيل، وليس التوجيه.

- لا Office 365 عناوين URL ونطاقات عناوين IP الأخرى خدمات Microsoft التي قد تكون في نطاق اتصالات ExpressRoute.

|**الخيار**|**التعقيد**|**تغيير عنصر التحكم**|
|:-----|:-----|:-----|
|قبول جميع مسارات Microsoft  <br/> |**منخفض:** يعتمد العميل على عناصر تحكم Microsoft لضمان امتلاك جميع المسارات بشكل صحيح.  <br/> |بلا  <br/> |
|تصفية supernets المملوكة ل Microsoft  <br/> |**متوسط:** ينفذ العميل قوائم تصفية البادائح الملخصة للسماح فقط للمسارات المملوكة ل Microsoft.  <br/> |يجب على العملاء التأكد من أن التحديثات غير المحدثة تنعكس في عوامل تصفية المسار.  <br/> |
|تصفية Office 365 IP  <br/> [!CAUTION] Not-Recommended |**عال:** يقوم العميل بتصفية المسارات استنادا إلى Office 365 IP المحددة.  <br/> |يجب على العملاء تنفيذ عملية إدارة تغيير قوية للتحديثات الشهرية.  <br/> [!CAUTION] يتطلب هذا الحل إدخال تغييرات مهمة على الوقت. من المرجح أن تؤدي التغييرات التي لم يتم تنفيذها في الوقت المحدد إلى انقطاع الخدمة.   |

يستند الاتصال ب Office 365 Azure ExpressRoute إلى إعلانات BGP الخاصة بالشبكات الفرعية المحددة ل IP التي تمثل الشبكات التي يتم Office 365 نقاط النهاية. نظرا للطبيعة العالمية Office 365 وعدد الخدمات التي Office 365، يحتاج العملاء في أغلب الأحيان إلى إدارة الإعلانات التي يقبلونها على شبكتهم. إذا كنت قلقا بشأن عدد البادئات المعلن عنها في بيئتك، فإن ميزة مجتمع [BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) تسمح لك بتصفية الإعلانات إلى مجموعة معينة من Office 365 الخدمات. هذه الميزة الآن في المعاينة.
  
بغض النظر عن كيفية إدارة إعلانات مسار BGP القادمة من Microsoft، لن تحصل على أي تعرض خاص لخدمات Office 365 عند مقارنتها بالاتصال بشبكة Office 365 عبر دائرة إنترنت فقط. تحافظ Microsoft على نفس مستويات الأمان والتوافق والأداء بغض النظر عن نوع الدائرة التي يستخدمها العميل للاتصال Office 365.
  
### <a name="security"></a>الأمان

توصي Microsoft بالمحافظة على عناصر التحكم المحيطة بالشبكة والأمان الخاصة بك للاتصالات التي يتم توجيهها من ونهاية إلى نظير ExpressRoute العام و Microsoft، الذي يتضمن اتصالات من خدمات Office 365 وإلصاق منها. يجب أن تكون عناصر التحكم في الأمان في مكانها لطلبات الشبكة التي تسافر إلى الخارج من شبكتك إلى شبكة Microsoft بالإضافة إلى الوارد من شبكة Microsoft إلى شبكتك.
  
#### <a name="outbound-from-customer-to-microsoft"></a>الصادر من العميل إلى Microsoft
  
عندما تتصل أجهزة الكمبيوتر Office 365، فإنها تتصل بنفس مجموعة نقاط النهاية بغض النظر عما إذا كان الاتصال يتم عبر الإنترنت أو دائرة ExpressRoute. بغض النظر عن الدائرة المستخدمة، توصي Microsoft بمعاملة Office 365 الخدمات على أنها أكثر ثقة من وجهات الإنترنت العامة. يجب أن تركز عناصر التحكم في الأمان الصادر على المنافذ والبروتوكولات لتقليل التعرض للضوء وتقليل الصيانة المستمرة. تتوفر معلومات المنفذ المطلوبة في المقالة المرجعية Office 365 [نقاط](./urls-and-ip-address-ranges.md) النهاية.
  
لمزيد من عناصر التحكم، يمكنك استخدام تصفية مستوى FQDN داخل البنية الأساسية للوكيل لتقييد بعض طلبات الشبكة الموجهة للإنترنت أو Office 365 أو فحصها. تتطلب المحافظة على قائمة FQDN كميزات تم إصدارها وتطوير عروض Office 365 إدارة أكثر فعالية للتغيير وتعقب التغييرات في نقاط نهاية Office 365 [المنشورة](./urls-and-ip-address-ranges.md).
  
> [!CAUTION]
> توصي Microsoft بعدم الاعتماد فقط علىبادات IP لإدارة الأمان الصادر Office 365.

|**الخيار**|**التعقيد**|**تغيير عنصر التحكم**|
|:-----|:-----|:-----|
|بلا قيود  <br/> |**منخفض:** يسمح العميل بالوصول الصادر غير المقيد إلى Microsoft.  <br/> |بلا  <br/> |
|قيود المنفذ  <br/> |**منخفض:** يقوم العميل بتقييد الوصول الصادر إلى Microsoft بواسطة المنافذ المتوقعة.  <br/> |غير متكد.  <br/> |
|قيود FQDN  <br/> |**عال:** يقوم العميل بتقييد الوصول الصادر Office 365 استنادا إلى FQDNs المنشورة.  <br/> |التغييرات الشهرية.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>الوارد من Microsoft إلى العميل
  
هناك العديد من السيناريوهات الاختيارية التي تتطلب من Microsoft بدء الاتصالات بالشبكة.
  
- ADFS أثناء التحقق من صحة كلمة المرور الخاصة تسجيل الدخول.

- [Exchange Server التوزيع المختلط](/exchange/exchange-hybrid).

- البريد من Exchange Online مستأجر إلى مضيف في الموقع.

- SharePoint إرسال البريد عبر الإنترنت من SharePoint Online إلى مضيف في الموقع.

- [SharePoint البحث المختلط المتحدة](/SharePoint/hybrid/display-hybrid-federated-search-results-in-sharepoint-online).

- [SharePoint BCS المختلطة](/SharePoint/hybrid/deploy-a-business-connectivity-services-hybrid-solution).

- [Skype for Business المختلط](/skypeforbusiness/hybrid/plan-hybrid-connectivity?bc=%2fSkypeForBusiness%2fbreadcrumb%2ftoc.json&toc=%2fSkypeForBusiness%2ftoc.json) و/[أو Skype for Business الاتحاد.](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features)

- [Skype for Business Cloud Connector](/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

توصي Microsoft بقبول هذه الاتصالات عبر دائرة الإنترنت بدلا من دائرة ExpressRoute لتقليل التعقيدات. إذا كان الامتثال أو الأداء يحتاج إلى إملاء يجب قبول هذه الاتصالات الواردة عبر دائرة ExpressRoute، من المستحسن استخدام جدار حماية أو وكيل عكسي لنطاق الاتصالات المقبولة. يمكنك استخدام نقاط [Office 365](./urls-and-ip-address-ranges.md) لتحديد FQDN وبادئات IP المناسبة.
  
### <a name="compliance"></a>التوافق

لا نعتمد على مسار التوجيه الذي تستخدمه لأي من عناصر التحكم في التوافق لدينا. بغض النظر عما إذا كنت تتصل Office 365 عبر دائرة ExpressRoute أو الإنترنت، فلن تتغير عناصر التحكم في التوافق لدينا. يجب مراجعة مستويات مصادقة الأمان والتوافق المختلفة Office 365 لمعرفة الخيار الأفضل لتلبية احتياجات مؤسستك.
  
إليك ارتباط مختصر يمكنك استخدامه للعودة: [https://aka.ms/manageexpressroute365]()
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[شبكات تسليم المحتوى](content-delivery-networks.md)
  
[نطاقات عناوين IP وعناوين URL في Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[إدارة Office 365 نقاط النهاية](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Azure ExpressRoute Office 365 التدريب](https://channel9.msdn.com/series/aer)