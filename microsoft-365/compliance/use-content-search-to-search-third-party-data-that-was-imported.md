---
title: استخدام البحث عن المحتوى للبحث في البيانات المستوردة من جهة خارجية
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
description: استخدم أداة eDiscovery للبحث عن العناصر المستوردة إلى علب البريد في Microsoft 365 من مصدر بيانات تابع لجهة خارجية عن طريق إنشاء استعلامات.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9a6a7bcdf0cbd7f14e20cc8400e5d834dc7da0a1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000884"
---
# <a name="use-content-search-to-search-third-party-data-imported-by-a-custom-partner-connector"></a>استخدام البحث عن المحتوى للبحث في بيانات الجهات الخارجية التي تم استيرادها بواسطة موصل شريك مخصص

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكنك استخدام [أداة البحث في المحتوى eDiscovery](content-search.md) في مدخل توافق Microsoft Purview للبحث عن العناصر المستوردة إلى علب البريد في Microsoft 365 من مصدر بيانات تابع لجهة خارجية. يمكنك إنشاء استعلام للبحث في كافة عناصر بيانات الجهات الخارجية المستوردة أو يمكنك إنشاء استعلام للبحث في عناصر بيانات خاصة بجهة خارجية. كما يمكنك أيضا إنشاء نهج استبقاء يستند إلى استعلام أو قائمة احتجاز eDiscovery مستندة إلى استعلام للاحتفاظ ببيانات الجهات الخارجية.
  
لمزيد من المعلومات حول العمل مع شريك لاستيراد بيانات الجهات الخارجية وقائمة بأنواع بيانات الجهات الخارجية التي يمكنك استيرادها إلى Microsoft 365، راجع ["العمل مع شريك" لأرشفة بيانات الجهات الخارجية في Office 365](work-with-partner-to-archive-third-party-data.md).

> [!IMPORTANT]
> تنطبق الإرشادات الواردة في هذه المقالة فقط على بيانات الجهات الخارجية التي تم استيرادها من قبل موصل شريك مخصص. لا تنطبق هذه المقالة على بيانات الجهات الخارجية التي يتم استيرادها باستخدام [موصلات البيانات التابعة لجهة خارجية](archiving-third-party-data.md#third-party-data-connectors) في مركز توافق Microsoft.
  
## <a name="creating-a-query-to-search-all-third-party-data"></a>إنشاء استعلام للبحث في كافة بيانات الجهات الخارجية

للبحث عن (أو وضع قيد الاحتجاز) أي نوع من بيانات الجهات الخارجية التي قمت باستيرادها إلى Office 365، يمكنك استخدام `kind:externaldata` زوج قيمة خاصية الرسالة في مربع الكلمة الأساسية للبحث في المحتوى أو عند إنشاء قائمة احتجاز مستندة إلى استعلام. على سبيل المثال، للبحث عن عناصر مستوردة من أي مصدر بيانات تابع لجهة خارجية وتحتوي على الكلمة "contoso" في خاصية الموضوع للعنصر المستورد، يمكنك استخدام الاستعلام التالي: 
  
```powershell
kind:externaldata AND subject:contoso
```

يتضمن مثال استعلام الكلمة الأساسية السابق خاصية الموضوع. للحصول على قائمة بالخصائص الأخرى لعناصر البيانات التابعة لجهة خارجية التي يمكن تضمينها في استعلام كلمة أساسية، راجع القسم "مزيد من المعلومات" في ["العمل مع شريك" لأرشفة بيانات الجهات الخارجية في Office 365](work-with-partner-to-archive-third-party-data.md#more-information).
  
عند إنشاء استعلامات للبحث عن بيانات الجهات الخارجية والاحتفاظ بها، يمكنك أيضا استخدام الشروط لتضييق نطاق نتائج البحث. لمزيد من المعلومات حول إنشاء استعلامات البحث في المحتوى، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md).
  
## <a name="creating-a-query-to-search-specific-types-of-third-party-data"></a>إنشاء استعلام للبحث في أنواع معينة من بيانات الجهات الخارجية

بدلا من البحث في كافة أنواع بيانات الجهات الخارجية، يمكنك إنشاء استعلامات تبحث فقط عن نوع محدد من بيانات الجهات الخارجية باستخدام خاصية الرسالة التالية *: زوج القيمة* في مربع الكلمة الأساسية للبحث في المحتوى:
  
```powershell
itemclass:ipm.externaldata.<third-party data type>* 
```

على سبيل المثال، للبحث في بيانات Facebook التي تحتوي على الكلمة "contoso" في خاصية الموضوع، يمكنك استخدام الاستعلام التالي:
  
```powershell
itemclass:ipm.externaldata.Facebook* AND subject:contoso
```

يسرد الجدول التالي أنواع بيانات الجهات الخارجية التي يمكنك البحث فيها، والقيمة التي يجب استخدامها لخاصية  `itemclass:` الرسالة للبحث بشكل خاص عن هذا النوع من بيانات الجهات الخارجية. بناء جملة الاستعلام غير حساس لحالة الأحرف. 
  
|**نوع بيانات جهة خارجية**|**قيمة الخاصية `itemclass:`**|
|:-----|:-----|
|الهدف  <br/> | `ipm.externaldata.AIM*` <br/> |
|المعرف الأمريكي  <br/> | `ipm.externaldata.AmericanIdol*` <br/> |
|AOL مع Pivot Client  <br/> | `ipm.externaldata.Pivot.IM` <br/> |
|تفاحة فافة  <br/> | `ipm.externaldata.AppleJuice*` <br/> |
|اريس  <br/> | `ipm.externaldata.Ares*` <br/> |
|Axs Encrypted  <br/> | `ipm.externaldata.AxsEncrypted*` <br/> |
|Exchange Axs  <br/> | `ipm.externaldata.AxsExchange*` <br/> |
|الأرشيف المحلي ل Axs  <br/> | `ipm.externaldata.AxsLocalArchive*` <br/> |
|عنصر نائب ل Axs  <br/> | `ipm.externaldata.AxsPlaceHolder*` <br/> |
|Axs Signed  <br/> | `ipm.externaldata.AxsSigned*` <br/> |
|Bazaarvoice  <br/> | `ipm.externaldata.Bazaarvoice*` <br/> |
|بيرشير  <br/> | `ipm.externaldata.Bearshare*` <br/> |
|تورنت  <br/> | `ipm.externaldata.BitTorrent*` <br/> |
|بلاك بيري  <br/> | `ipm.externaldata.Blackberry*` <br/> |
|سجلات مكالمات BlackBerry  <br/> | `ipm.externaldata.BlackBerryCall*` <br/> |
|BlackBerry Messenger  <br/> | `ipm.externaldata.BlackBerryMessenger*` <br/> |
|BlackBerry PIN  <br/> | `ipm.externaldata.BlackBerryPIN*` <br/> |
|BlackBerry SMS  <br/> | `ipm.externaldata.BlackBerrySMS*` <br/> |
|بلومبرغ  <br/> | `ipm.externaldata.Bloomberg*` <br/> |
|رسالة Bloomberg  <br/> | `ipm.externaldata.conversation.Bloomberg Message*` <br/> |
|مراسلة بلومبيرغ  <br/> | `ipm.externaldata.BloombergMessaging*` <br/> |
|مربع  <br/> | `ipm.externaldata.Box*` <br/> |
|خادم حالة حضور المراسلة الفورية &amp; في Cisco  <br/> | `ipm.externaldata.Jabber.IM` <br/> |
|Cisco Jabber  <br/> | `ipm.externaldata.Jabber*` <br/> |
|CipherCloud ل Salesforce Chatter  <br/> | `ipm.externaldata.Chatter.Post` <br/>  `ipm.externaldata.Chatter.Comment` <br/> |
|الاتصال المباشر  <br/> | `ipm.externaldata.DirectConnect*` <br/> |
|ف يسبوك  <br/> | `ipm.externaldata.Facebook*` <br/> |
|FastTrack  <br/> | `ipm.externaldata.FastTrack*` <br/> |
|FXConnect  <br/> | `ipm.externaldata.FXConnect.chat` <br/> |
|فل يكر  <br/> | `ipm.externaldata.Flickr*` <br/> |
|نوتلا  <br/> | `ipm.externaldata.Gnutella*` <br/> |
|Google+  <br/> | `ipm.externaldata.GooglePlus*` <br/> |
|Google Talk  <br/> | `ipm.externaldata.GoogleTalk*` <br/> |
|GoToMyPC  <br/> | `ipm.externaldata.GoToMyPC*` <br/> |
|HipChat  <br/> | `ipm.externaldata.HipChat*` <br/> |
|وثبة  <br/> | `ipm.externaldata.Hopster*` <br/> |
|HubConnex  <br/> | `ipm.externaldata.HubConnex*` <br/> |
|IBM Connections  <br/> | `ipm.externaldata.Connections*` <br/> |
|IBM SameTime  <br/> | `ipm.externaldata.Sametime*` <br/> |
|دردشة ICE  <br/> | `ipm.externaldata.conversation.Ice Chat*` <br/> |
|Indii Messenger  <br/> | `ipm.externaldata.Indii*` <br/> |
|اينستاجرام  <br/> | `ipm.externaldata.Instagram*` <br/> |
|Instant Bloomberg  <br/> | `ipm.externaldata.InstantBloomberg*` <br/> |
|InvestEdge  <br/> | `ipm.externaldata.InvestEdge*` <br/> |
|الايرسي  <br/> | `ipm.externaldata.IRC*` <br/> |
|Jive  <br/> | `ipm.externaldata.Jive*` <br/> |
|JiveApiRetention  <br/> | `ipm.externaldata.JiveApiRetention*` <br/> |
|JXTA  <br/> | `ipm.externaldata.JXTA*` <br/> |
|LinkedIn  <br/> | `ipm.externaldata.LinkedIn*` <br/> |
|MFTP  <br/> | `ipm.externaldata.MFTP*` <br/> |
|Microsoft UC  <br/> | `ipm.externaldata.MicrosoftUC*` <br/> |
|محاذاة للعقل  <br/> | `ipm.externaldata.MindAlign*` <br/> |
|حماية الأجهزة المحمولة  <br/> | `ipm.externaldata.MobileGuard*` <br/> |
|MSN  <br/> | `ipm.externaldata.MSN*` <br/> |
|ماي سبيس  <br/> | `ipm.externaldata.MySpace*` <br/> |
|الشبكات المناظرة على شبكة الإنترنت  <br/> | `ipm.externaldata.NEONetwork*` <br/> |
|OpenNap  <br/> | `ipm.externaldata.OpenNap*` <br/> |
|Pinterest  <br/> | `ipm.externaldata.Pinterest*` <br/> |
|Pivot  <br/> | `ipm.externaldata.Pivot*` <br/> |
|QQ  <br/> | `ipm.externaldata.QQ*` <br/> |
|Microsoft SharePoint  <br/> | `ipm.externaldata.SharePoint*` <br/> |
|Salesforce Chatter  <br/> | `ipm.externaldata.Chatter*` <br/> |
|Skype for Business  <br/> | `ipm.externaldata.Skype*` <br/> |
|Slack Enterprise Grid  <br/> | `ipm.externaldata.Slack.IM` <br/> |
|اللينة  <br/> | `ipm.externaldata.SoftEther*` <br/> |
|Squawker  <br/> | `ipm.externaldata.Squawker*` <br/> |
|Symphony  <br/> | `ipm.externaldata.Symphony*` <br/> |
|ThomsonHomson  <br/> | `ipm.externaldata.Reuters*` <br/> |
| ThomsonHomsonHoms Eikon Messenger  <br/> | `ipm.externaldata.ReutersEikon*` <br/> |
|تور  <br/> | `ipm.externaldata.Tor*` <br/> |
|TTT  <br/> | `ipm.externaldata.TTT*` <br/> |
|Twitter  <br/> | `ipm.externaldata.Twitter*` <br/> |
|UBS Chat  <br/> | `ipm.externaldata.UBS*` <br/> |
|Vimeo  <br/> | `ipm.externaldata.Vimeo*` <br/> |
|WinMX  <br/> | `ipm.externaldata.WinMX*` <br/> |
|Winny  <br/> | `ipm.externaldata.Winny*` <br/> |
|ياهو!  <br/> | `ipm.externaldata.Yahoo!*` <br/> |
|Yammer  <br/> | `ipm.externaldata.Yammer*` <br/> |
|YellowJacket  <br/> | `ipm.externaldata.YellowJacket*` <br/> |
|YouTube  <br/> | `ipm.externaldata.YouTube*` <br/> |
