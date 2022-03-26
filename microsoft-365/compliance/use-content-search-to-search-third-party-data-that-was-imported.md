---
title: استخدام "البحث في المحتوى" للبحث عن البيانات المستوردة من جهة خارجية
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: ec2677ff-c4d7-4363-a9e7-22c80e015688
description: استخدم أداة eDiscovery للبحث في المحتوى للبحث عن العناصر المستوردة إلى علب البريد في Microsoft 365 من مصدر بيانات جهة خارجية عن طريق إنشاء استعلامات.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 068a6e3164154129ba9148b41138d50c518042ed
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566944"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>استخدام "البحث في المحتوى" للبحث عن بيانات جهة خارجية تم استيرادها بواسطة موصل شريك مخصص

يمكنك استخدام أداة [eDiscovery](content-search.md) للبحث في المحتوى في مركز التوافق في Microsoft 365 للبحث عن العناصر المستوردة إلى علب البريد في Microsoft 365 من مصدر بيانات جهة خارجية. يمكنك إنشاء استعلام للبحث في كل عناصر البيانات التي تم استيرادها من جهة خارجية أو يمكنك إنشاء استعلام للبحث في عناصر بيانات خاصة ب جهة خارجية. يمكنك أيضا إنشاء نهج استبقاء مستند إلى استعلام أو قائمة احتجاز eDiscovery مستندة إلى استعلام للحفاظ على بيانات جهة خارجية.
  
لمزيد من المعلومات حول العمل مع شريك لاستيراد بيانات جهة خارجية وقائمة بأنواع بيانات الأطراف الخارجية التي يمكنك استيرادها إلى Microsoft 365، راجع العمل مع شريك لأرشفة بيانات جهة خارجية [في Office 365](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> تنطبق الإرشادات الواردة في هذه المقالة فقط على بيانات جهة خارجية تم استيرادها بواسطة موصل شريك مخصص. لا تنطبق هذه المقالة على بيانات الأطراف الخارجية التي يتم استيرادها باستخدام موصلات البيانات الخاصة ب جهة [خارجية في مركز](archiving-third-party-data.md#third-party-data-connectors) التوافق من Microsoft.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>إنشاء استعلام للبحث في كل بيانات  الأطراف الخارجية

للبحث (أو وضع البيانات في وضع الانتظار) عن أي نوع من بيانات الأطراف الخارجية التي قمت `kind:externaldata` باستيرادها إلى Office 365، يمكنك استخدام زوج قيمة خاصية الرسالة في مربع الكلمة الأساسية للبحث في المحتوى أو عند إنشاء قائمة الانتظار المستندة إلى الاستعلام. على سبيل المثال، للبحث عن العناصر المستوردة من أي مصدر بيانات جهة خارجية واحتواء الكلمة "contoso" في الخاصية Subject الخاصة بالعنصر المستورد، يمكنك استخدام الاستعلام التالي: 
  
```powershell
kind:externaldata AND subject:contoso
```

يتضمن مثال استعلام الكلمة الأساسية السابق خاصية الموضوع. للحصول على قائمة بالخصائص الأخرى لعناصر بيانات الأطراف الخارجية التي يمكن تضمينها في استعلام الكلمة الأساسية، راجع القسم "مزيد من المعلومات" في العمل مع شريك لأرشفة بيانات جهة [خارجية في](work-with-partner-to-archive-third-party-data.md#more-information) Office 365.
  
عند إنشاء استعلامات للبحث عن بيانات جهة خارجية مع الاستمرار عليها، يمكنك أيضا استخدام الشروط لتضييق نطاق نتائج البحث. لمزيد من المعلومات حول إنشاء استعلامات البحث في المحتوى، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث في المحتوى](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>إنشاء استعلام للبحث عن أنواع معينة من بيانات  الأطراف الخارجية

بدلا من البحث في كل أنواع بيانات الجهة الخارجية، يمكنك إنشاء استعلامات تبحث فقط عن نوع معين من بيانات الجهة الخارجية باستخدام خاصية الرسالة التالية *:* زوج القيم في مربع الكلمة الأساسية للبحث في المحتوى:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

على سبيل المثال، للبحث في بيانات Facebook التي تحتوي على الكلمة "contoso" في خاصية الموضوع، يمكنك استخدام الاستعلام التالي:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

يسرد الجدول التالي  `itemclass:` أنواع بيانات الأطراف الخارجية التي يمكنك البحث عنها، والقيمة التي يجب استخدامها لخصخصة الرسالة للبحث عن هذا النوع من البيانات الخاصة ب جهة خارجية على وجه التحديد. لا يتحسس بناء جملة الاستعلام حالة التحسس. 
  
|**نوع بيانات جهة خارجية**|**القيمة للممتلكات `itemclass:`**|
|:-----|:-----|
|AIM  <br/> | `ipm.externaldata.AIM*` <br/> |
|الأميركية للانوثب  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL مع Pivot Client  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|Apple الحامض  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|Ares  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Axs Exchange  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|Axs الأرشيف المحلي  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|عنصر نائب ل Axs  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Axs Signed  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|الدببة  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|BitTorrent  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|Blackberry  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|سجلات المكالمات في BlackBerry  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|BlackBerry PIN  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|بلومبرغ  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|رسالة بلومبرغ  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|مراسلة بلومبرغ  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|المربع  <br/> | `ipm.externaldata.Box*` <br/> |
|خادم حضور المراسلة الفورية &amp; في Cisco  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|CipherCloud for Salesforce Chatter  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|مباشرة الاتصال  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|Facebook  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|Flickr  <br/> | `ipm.externaldata.Flickr*` <br/> |
|Gnutella  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|الوابسستر  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM Connections  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|ICE Chat  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|إنستجرام  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|IRC  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|محاذاة للذهان  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|Mobile Guard  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|MySpace  <br/> | `ipm.externaldata.MySpace*` <br/> |
|NEONetwork  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce Chatter  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype for Business  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack Enterprise Grid  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|SoftEther  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|السيمفونية  <br/> | `ipm.externaldata.Symphony*` <br/> |
|طومسون رويتر  <br/> | `ipm.externaldata.Reuters*` <br/> |
| Thomson Reuters Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|Tor  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|دردشة UBS  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|WinMX  <br/> | `ipm.externaldata.WinMX*` <br/> |
|ويني  <br/> | `ipm.externaldata.Winny*` <br/> |
|Yahoo!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|أصفر جاكيت  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
