---
title: تنفيذ نفق انقسام VPN ل Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: كيفية تنفيذ نفق انقسام VPN ل Microsoft 365
ms.openlocfilehash: 6b578b9b1801921644c6982c15c160bce5fbb4dd
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941075"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>تنفيذ نفق انقسام VPN ل Microsoft 365

>[!NOTE]
>تشكل هذه المقالة جزءا من مجموعة من المقالات التي تتناول تحسين Microsoft 365 للمستخدمين البعيدين.

>- للحصول على نظرة عامة حول استخدام نفق انقسام VPN لتحسين اتصال Microsoft 365 للمستخدمين البعيدين، راجع [نظرة عامة: نفق انقسام VPN ل Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- للحصول على قائمة مفصلة بسيناريوهات الاتصال النفقي المنقسم ل VPN، راجع [سيناريوهات الاتصال النفقي المنقسم ل VPN الشائعة ل Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- للحصول على إرشادات حول تأمين حركة مرور وسائط Teams في بيئات الاتصال النفقي المنقسمة ل VPN، راجع [تأمين حركة مرور وسائط Teams للنفق المنقسم ل VPN](microsoft-365-vpn-securing-teams.md).
>- للحصول على معلومات حول كيفية تكوين Stream والأحداث المباشرة في بيئات VPN، راجع [الاعتبارات الخاصة ل Stream والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md).
>- للحصول على معلومات حول تحسين أداء المستأجر في جميع أنحاء العالم من Microsoft 365 للمستخدمين في الصين، راجع [تحسين أداء Microsoft 365 لمستخدمي الصين](microsoft-365-networking-china.md).

تركز استراتيجية Microsoft الموصى بها لتحسين اتصال العامل عن بعد على التخفيف السريع من المشكلات وتوفير أداء عال ببعض الخطوات البسيطة. تقوم هذه الخطوات بضبط نهج VPN القديم لعدد قليل من نقاط النهاية المحددة التي تتجاوز خوادم VPN المازدحامة. يمكن تطبيق نموذج أمان مكافئ أو حتى فائق في طبقات مختلفة لإزالة الحاجة إلى تأمين جميع نسبة استخدام الشبكة عند خروج شبكة الشركة. في معظم الحالات، يمكن تحقيق ذلك بفعالية في غضون ساعات ثم يمكن توسيعه إلى أحمال العمل الأخرى كما يسمح بالمتطلبات والوقت.

## <a name="implement-vpn-split-tunneling"></a>تنفيذ الاتصال النفقي المنقسم ل VPN

في هذه المقالة، ستجد الخطوات البسيطة المطلوبة لنقل بنية عميل VPN الخاص بك من _نفق مفروض VPN_ إلى _نفق مفروض VPN مع بعض الاستثناءات الموثوق بها_، [نموذج نفق انقسام VPN رقم 2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) في [سيناريوهات نفق انقسام VPN الشائعة ل Microsoft 365](microsoft-365-vpn-common-scenarios.md).

يوضح الرسم التخطيطي أدناه كيفية عمل حل نفق انقسام VPN الموصى به:

![تفاصيل حل VPN للنفق المنقسم.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. تحديد نقاط النهاية لتحسينها

في مقالة [نطاقات عناوين IP وعناوين URL في Microsoft 365](urls-and-ip-address-ranges.md) ، تحدد Microsoft بوضوح نقاط النهاية الرئيسية التي تحتاجها لتحسينها وتصنيفها على أنها **تحسين**. هناك حاليا أربعة عناوين URL فقط و20 شبكة فرعية IP تحتاج إلى تحسين. تمثل هذه المجموعة الصغيرة من نقاط النهاية حوالي 70٪ - 80٪ من حجم نسبة استخدام الشبكة إلى خدمة Microsoft 365 بما في ذلك نقاط النهاية الحساسة لزمن الانتقال مثل تلك الخاصة بوسائط Teams. بشكل أساسي هذه هي نسبة استخدام الشبكة التي نحتاج إلى الاهتمام بها بشكل خاص وهي أيضا نسبة استخدام الشبكة التي ستضع ضغطا لا يصدق على مسارات الشبكة التقليدية والبنية الأساسية للشبكة الظاهرية الخاصة.

تحتوي عناوين URL في هذه الفئة على الخصائص التالية:

- هل نقاط النهاية المملوكة ل Microsoft والمدارة، مستضافة على البنية الأساسية ل Microsoft
- توفير عناوين IP
- معدل تغيير منخفض ومن المتوقع أن يظل صغيرا في العدد (حاليا 20 شبكة فرعية IP)
- عرض النطاق الترددي و/أو زمن الانتقال حساس
- القدرة على توفير عناصر الأمان المطلوبة في الخدمة بدلا من أن تكون مضمنة على الشبكة
- حساب حوالي 70-80٪ من حجم نسبة استخدام الشبكة إلى خدمة Microsoft 365

لمزيد من المعلومات حول نقاط نهاية Microsoft 365 وكيفية تصنيفها وإدارتها، راجع [إدارة نقاط نهاية Microsoft 365](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>تحسين عناوين URL

يمكن العثور على "تحسين عناوين URL" الحالية في الجدول أدناه. في معظم الحالات، يجب أن تحتاج فقط إلى استخدام نقاط نهاية URL في [ملف PAC مستعرض](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) حيث يتم تكوين نقاط النهاية ليتم إرسالها مباشرة، بدلا من الوكيل.

| تحسين عناوين URL | منفذ/بروتوكول | الغرض |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | هذا هو أحد عناوين URL الأساسية التي يستخدمها Outlook للاتصال بخادم Exchange Online الخاص به ولديه عدد كبير من استخدام النطاق الترددي وعدد الاتصالات. إن زمن انتقال الشبكة المنخفض مطلوب للميزات عبر الإنترنت، بما في ذلك: البحث الفوري، وتقويمات علبة البريد الأخرى، والبحث عن التوفر/الانشغال، وإدارة القواعد والتنبيهات، وأرشيف Exchange عبر الإنترنت، ورسائل البريد الإلكتروني التي تغادر علبة الصادر. |
| <https://outlook.office.com> | TCP 443 | يتم استخدام URL هذا للوصول إلى Outlook Online Web Access للاتصال بخادم Exchange Online، وهو حساس لزمن انتقال الشبكة. الاتصال مطلوب بشكل خاص لتحميل الملفات الكبيرة وتنزيلها باستخدام SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | هذا هو URL الأساسي ل SharePoint Online ولديه استخدام عالي النطاق الترددي. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | هذا هو عنوان URL الأساسي ل OneDrive for Business ولديه استخدام عرض نطاق ترددي عال وربما عدد اتصالات عال من أداة مزامنة OneDrive for Business. |
| عناوين IP للوسائط في Teams (بدون عنوان URL) | UDP 3478 و3479 و3480 و3481 | تخصيص اكتشاف الترحيل وحركة المرور في الوقت الحقيقي. هذه هي نقاط النهاية المستخدمة لنسبة استخدام الوسائط في Skype for Business وMicrosoft Teams Media (المكالمات والاجتماعات وما إلى ذلك). يتم توفير معظم نقاط النهاية عندما يقوم عميل Microsoft Teams بإنشاء مكالمة (ويتم تضمينها ضمن عناوين IP المطلوبة المدرجة للخدمة). استخدام بروتوكول UDP مطلوب لجودة الوسائط المثلى.   |

في الأمثلة أعلاه، يجب استبدال **المستأجر** باسم مستأجر Microsoft 365. على سبيل المثال، **قد يستخدم contoso.onmicrosoft.com** _contoso.sharepoint.com_ _contoso-my.sharepoint.com._

#### <a name="optimize-ip-address-ranges"></a>تحسين نطاقات عناوين IP

في وقت كتابة نطاقات عناوين IP التي تتوافق معها نقاط النهاية هذه هي كما يلي. ينصح **بشدة** باستخدام [برنامج نصي مثل هذا](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category) المثال، [خدمة ويب MICROSOFT 365 IP وURL](microsoft-365-ip-web-service.md) أو [صفحة URL/IP](urls-and-ip-address-ranges.md) للتحقق من وجود أي تحديثات عند تطبيق التكوين، ووضع نهج للقيام بذلك بانتظام.

```markdown
104.146.128.0/17
13.107.128.0/22
13.107.136.0/22
13.107.18.10/31
13.107.6.152/31
13.107.64.0/18
131.253.33.215/32
132.245.0.0/16
150.171.32.0/22
150.171.40.0/22
204.79.197.215/32
23.103.160.0/20
40.104.0.0/15
40.108.128.0/17
40.96.0.0/13
52.104.0.0/14
52.112.0.0/14
52.96.0.0/14
52.120.0.0/14
```

### <a name="2-optimize-access-to-these-endpoints-via-the-vpn"></a>2. تحسين الوصول إلى نقاط النهاية هذه عبر VPN

الآن بعد أن حددنا نقاط النهاية الهامة هذه، نحتاج إلى تحويلها بعيدا عن نفق VPN والسماح لها باستخدام اتصال الإنترنت المحلي للمستخدم للاتصال مباشرة بالخدمة. تختلف الطريقة التي يتم بها إنجاز ذلك اعتمادا على منتج VPN والنظام الأساسي للجهاز المستخدم ولكن معظم حلول VPN ستسمح ببعض التكوين البسيط للنهج لتطبيق هذا المنطق. للحصول على معلومات حول إرشادات النفق المنقسم الخاص بالنظام الأساسي VPN، راجع [إرشادات HOWTO لأنظمة VPN الأساسية الشائعة](#howto-guides-for-common-vpn-platforms).

إذا كنت ترغب في اختبار الحل يدويا، يمكنك تنفيذ مثال PowerShell التالي لمحاكاة الحل على مستوى جدول التوجيه. يضيف هذا المثال مسارا لكل من الشبكات الفرعية ل Teams Media IP في جدول التوجيه. يمكنك اختبار أداء وسائط Teams قبل وبعد، ومراقبة الفرق في المسارات لنقاط النهاية المحددة.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>مثال: إضافة الشبكات الفرعية ل Teams Media IP إلى جدول التوجيه

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

في البرنامج النصي أعلاه، _$intIndex_ هو فهرس الواجهة المتصلة بالإنترنت (ابحث عن طريق تشغيل **get-netadapter** في PowerShell؛ ابحث عن قيمة _ifIndex_) _$gateway_ هي البوابة الافتراضية لتلك الواجهة (ابحث عن طريق تشغيل **ipconfig** في موجه الأوامر أو **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** في PowerShell).

بمجرد إضافة المسارات، يمكنك تأكيد أن جدول التوجيه صحيح عن طريق تشغيل **طباعة المسار** في موجه أوامر أو PowerShell. يجب أن يحتوي الإخراج على المسارات التي أضفتها، مع إظهار فهرس الواجهة (_22_ في هذا المثال) وبوابة تلك الواجهة (_192.168.1.1_ في هذا المثال):

![إخراج طباعة المسار.](../media/vpn-split-tunneling/vpn-route-print.png)

لإضافة مسارات _لكافة_ نطاقات عناوين IP الحالية في الفئة "تحسين"، يمكنك استخدام تباين البرنامج النصي التالي للاستعلام عن [خدمة ويب ل Microsoft 365 IP وURL](microsoft-365-ip-web-service.md) لمجموعة الشبكات الفرعية "تحسين IP" الحالية وإضافتها إلى جدول التوجيه.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>مثال: إضافة كافة الشبكات الفرعية "تحسين" إلى جدول التوجيه

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
# Query the web service for IPs in the Optimize category
$ep = Invoke-RestMethod ("https://endpoints.office.com/endpoints/worldwide?clientrequestid=" + ([GUID]::NewGuid()).Guid)
# Output only IPv4 Optimize IPs to $optimizeIps
$destPrefix = $ep | where {$_.category -eq "Optimize"} | Select-Object -ExpandProperty ips | Where-Object { $_ -like '*.*' }
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

إذا أضفت عن غير قصد مسارات بمعلمات غير صحيحة أو كنت ترغب ببساطة في إرجاع التغييرات، يمكنك إزالة المسارات التي أضفتها للتو مع الأمر التالي:

```powershell
foreach ($prefix in $destPrefix) {Remove-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

<!--- remmed until we add more reliable interface selection logic
#### Example script to add Teams Media subnets to the route table

```powershell
$adapter = get-netadapter | ? {$_.Status -eq "Up"}
$adapterIndex = $adapter.ifIndex
$gateway = (Get-NetIPConfiguration | Foreach IPv4DefaultGateway).NextHop

$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18"
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```
-->

يجب تكوين عميل VPN بحيث يتم توجيه نسبة استخدام الشبكة إلى **تحسين** عناوين IP بهذه الطريقة. يسمح هذا لنسبة استخدام الشبكة باستخدام موارد Microsoft المحلية مثل Microsoft 365 Service Front Door [مثل Azure Front Door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/) التي توفر خدمات Microsoft 365 ونقاط نهاية الاتصال بالقرب من المستخدمين قدر الإمكان. يتيح لنا ذلك تقديم مستويات أداء عالية للمستخدمين أينما كانوا في العالم، كما أنه يستفيد استفادة كاملة من [شبكة Microsoft العالمية ذات المستوى العالمي](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)، والتي من المحتمل أن تكون في غضون بضعة مللي ثانية من الخروج المباشر للمستخدمين.

## <a name="howto-guides-for-common-vpn-platforms"></a>إرشادات HOWTO لأنظمة VPN الأساسية الشائعة

يوفر هذا القسم ارتباطات إلى إرشادات مفصلة لتنفيذ الاتصال النفقي المنقسم لحركة مرور Microsoft 365 من الشركاء الأكثر شيوعا في هذه المساحة. سنضيف إرشادات إضافية عندما تصبح متوفرة.

- **عميل Windows 10 VPN**: [تحسين نسبة استخدام الشبكة ل Microsoft 365 للعاملين عن بعد باستخدام عميل WINDOWS 10 VPN الأصلي](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [تحسين نفق تقسيم Anyconnect ل Office365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [تحسين حركة مرور Microsoft 365 عبر نفق انقسام VPN استبعاد مسار الوصول](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: [تحسين حركة مرور Microsoft 365 على الوصول عن بعد من خلال الشبكات الظاهرية الخاصة عند استخدام BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **Citrix Gateway**: [تحسين نفق تقسيم Citrix Gateway VPN ل Office365](https://docs.citrix.com/en-us/citrix-gateway/current-release/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPN Tunneling: كيفية تكوين الاتصال النفقي المنقسم لاستبعاد تطبيقات Microsoft 365](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417)
- **Check Point VPN**: [كيفية تكوين Split Tunnel ل Microsoft 365 وتطبيقات SaaS الأخرى](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>المقالات ذات الصلة

[نظرة عامة: الاتصال النفقي المنقسم VPN ل Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[سيناريوهات الاتصال النفقي لتقسيم VPN الشائعة ل Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[تأمين نقل وسائط Teams للاتصال النفقي المنقسم لشبكة VPN](microsoft-365-vpn-securing-teams.md)

[اعتبارات خاصة ل Stream والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md)

[تحسين أداء Microsoft 365 لمستخدمي الصين](microsoft-365-networking-china.md)

[مبادئ اتصال شبكة Microsoft 365](microsoft-365-network-connectivity-principles.md)

[تقييم اتصال الشبكة Microsoft 365](assessing-network-connectivity.md)

[ضبط أداء شبكة Microsoft 365](network-planning-and-performance.md)

[طرق بديلة لمحترفي الأمان و تكنولوجيا المعلومات لتحقيق عناصر التحكم الأمنية الحديثة في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[تحسين أداء VPN في Microsoft: استخدام ملفات تعريف WINDOWS 10 VPN للسماح باتصالات التشغيل التلقائي](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[التشغيل على VPN: كيف تحافظ Microsoft على اتصال القوى العاملة عن بعد](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[شبكة Microsoft العمومية](/azure/networking/microsoft-global-network)
