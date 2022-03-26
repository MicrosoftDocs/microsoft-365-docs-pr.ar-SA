---
title: تنفيذ تقسيم VPN لتنفيذ Microsoft 365
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
description: كيفية تنفيذ تقسيم VPN للانقسام Microsoft 365
ms.openlocfilehash: ee8c0929682370d581c9d1b5c738d682d3f91a01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572898"
---
# <a name="implementing-vpn-split-tunneling-for-microsoft-365"></a>تنفيذ تقسيم VPN لتنفيذ Microsoft 365

>[!NOTE]
>هذه المقالة هي جزء من مجموعة من المقالات التي تعالج Microsoft 365 للمستخدمين البعيدين.

>- للحصول على نظرة عامة حول استخدام تقسيم VPN لتحسين Microsoft 365 للمستخدمين البعيدين، راجع نظرة عامة[: تقسيم VPN](microsoft-365-vpn-split-tunnel.md) للتحكم Microsoft 365.
>- للحصول على قائمة تفصيلية بسيناريوهات تقسيم VPN التي تم تقسيمها، راجع سيناريوهات تقسيم VPN الشائعة [لسيناريوهات](microsoft-365-vpn-common-scenarios.md) تقسيم VPN Microsoft 365.
>- للحصول على إرشادات حول تأمين Teams الوسائط في بيئات تقسيم VPN التي تم تقسيمها، راجع تأمين Teams الوسائط لتقسيم [VPN](microsoft-365-vpn-securing-teams.md).
>- للحصول على معلومات حول كيفية تكوين الدفق والأحداث المباشرة في بيئات VPN، راجع اعتبارات خاصة للبث والأحداث المباشرة [في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md).
>- للحصول على معلومات حول تحسين Microsoft 365 المستأجر على مستوى العالم للمستخدمين في الصين، راجع Microsoft 365 تحسين أداء [المستخدمين في الصين](microsoft-365-networking-china.md).

تركز استراتيجية Microsoft الموصى بها لتحسين اتصال العامل عن بعد على تخفيف المشاكل بسرعة وتوفير أداء عال باستخدام بعض الخطوات البسيطة. تقوم هذه الخطوات بضبط نهج VPN القديم لبضع نقاط نهاية معرفة تتجاوز خوادم VPN المزدبكة. يمكن تطبيق نموذج أمان مكافئ أو حتى متفوق على طبقات مختلفة لإزالة الحاجة إلى تأمين كل حركة المرور عند الخروج من شبكة الشركة. في معظم الحالات، يمكن تحقيق ذلك بفعالية في غضون ساعات ويمكن بعد ذلك توسيعه لأحمال العمل الأخرى حسب متطلبات الطلب والوقت التي تسمح بها.

## <a name="implement-vpn-split-tunneling"></a>تنفيذ تقسيم VPN

في هذه المقالة، ستعثر على الخطوات البسيطة المطلوبة لترحيل بنية عميل VPN الخاص بك من VPN إجباريا على الاجتياج إلى نظام حماية _VPN_ إجباري مع بعض الاستثناءات الموثوق بها، نموذج انقسام VPN المنقسم [للنفقات #2](microsoft-365-vpn-common-scenarios.md#2-vpn-forced-tunnel-with-a-small-number-of-trusted-exceptions) في سيناريوهات تقسيم [VPN](microsoft-365-vpn-common-scenarios.md) الشائعة التي تم تقسيمها Microsoft 365.

يوضح الرسم التخطيطي أدناه كيفية عمل حل تقسيم VPN المنقسم الموصى به:

![تفاصيل حل VPN المنقسمة.](../media/vpn-split-tunneling/vpn-split-tunnel-example.png)

### <a name="1-identify-the-endpoints-to-optimize"></a>1. تحديد نقاط النهاية لتحسينها

في المقالة Microsoft 365 نطاقات عناوين [IP وURLS](urls-and-ip-address-ranges.md)، تحدد Microsoft بوضوح نقاط النهاية الرئيسية التي تحتاج إلى تحسينها وتصنيفها على أنها **تحسين**. هناك حاليا أربعة عناوين URL و20 شبكة IP فرعية تحتاج إلى تحسين. تمثل هذه المجموعة الصغيرة من نقاط النهاية حوالي 70٪ - 80٪ من حجم حركة المرور إلى خدمة Microsoft 365 بما في ذلك نقاط النهاية الحساسة لنقطة زمن Teams المرور. بشكل أساسي، هذه هي حركة المرور التي نحتاج إلى العناية الخاصة بها، وهي أيضا حركة المرور التي ستضع ضغطا لا يصدق على مسارات الشبكة التقليدية والبنية الأساسية لشبكة VPN.

عناوين URL في هذه الفئة لها الخصائص التالية:

- هل تملك Microsoft نقاط نهاية مدارة ومستضافة على البنية الأساسية ل Microsoft
- تم توفير IPs
- معدل التغيير منخفض ومن المتوقع أن يظل صغيرا في العدد (حاليا 20 شبكة IP فرعية)
- حساسة للانطاق الترددي و/أو زمن زمن الإرسال
- القدرة على توفير عناصر الأمان المطلوبة في الخدمة بدلا من توفيرها على الشبكة
- تمثل حوالي 70-80٪ من حجم حركة المرور إلى خدمة Microsoft 365

لمزيد من المعلومات Microsoft 365 نقاط النهاية وكيفية تصنيفها وإدارتها، راجع إدارة Microsoft 365 [نقاط النهاية](managing-office-365-endpoints.md).

#### <a name="optimize-urls"></a>تحسين عناوين URL

يمكن العثور على عناوين URL "تحسين" الحالية في الجدول أدناه. في معظم الحالات، يجب أن تحتاج فقط إلى استخدام نقاط نهاية URL في ملف [PAC](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) في المستعرض حيث تم تكوين نقاط النهاية لكي يتم إرسالها مباشرة، بدلا من الوكيل.

| تحسين عناوين URL | المنفذ/البروتوكول | الغرض |
| --- | --- | --- |
| <https://outlook.office365.com> | TCP 443 | هذا هو أحد عناوين URL Outlook الأساسية التي تستخدمها للاتصال Exchange Online الخادم الخاص بها، كما أنها تستخدم نطاق ترددي كبير وتحسب عدد الاتصال. زمن زمن الوصول المنخفض للشبكة مطلوب للميزات عبر الإنترنت بما في ذلك: البحث الفوري وتقويمات علب البريد الأخرى والبحث الحر / المشغول وإدارة القواعد والتنبيهات Exchange عبر الإنترنت ورسائل البريد الإلكتروني التي تغادر علبة الصادر. |
| <https://outlook.office.com> | TCP 443 | يتم استخدام عنوان URL هذا Outlook Online Access للاتصال Exchange Online الخادم، كما أنه حساس ل زمن وصول الشبكة. الاتصال مطلوب بشكل خاص لتحميل الملفات الكبيرة وتنزيلها باستخدام SharePoint Online. |
| \<tenant\>https://.sharepoint.com | TCP 443 | هذا هو عنوان URL الأساسي SharePoint Online وهو يحتوي على استخدام نطاق ترددي عال. |
| \<tenant\>https://-my.sharepoint.com | TCP 443 | هذا هو عنوان URL الأساسي OneDrive for Business به استخدام نطاق ترددي عال وربما عدد اتصال عال من أداة OneDrive for Business المزامنة. |
| Teams الوسائط (بدون عنوان URL) | UDP 3478 و3479 و3480 و3481 | ترحيل تخصيص الاكتشاف و نقل البيانات في الوقت الحقيقي. هذه هي نقاط النهاية المستخدمة Skype for Business Microsoft Teams الوسائط (المكالمات والاجتماعات وما إلى ذلك). يتم توفير معظم نقاط النهاية عندما Microsoft Teams العميل مكالمة (وهي موجودة ضمن IPs المطلوبة المدرجة للخدمة). استخدام بروتوكول UDP مطلوب للحصول على جودة وسائط مثالية.   |

في الأمثلة أعلاه، **يجب** استبدال المستأجر باسم المستأجر Microsoft 365 المستأجر. على سبيل المثال **، contoso.onmicrosoft.com** _استخدام contoso.sharepoint.com_ _contoso-my.sharepoint.com._

#### <a name="optimize-ip-address-ranges"></a>تحسين نطاقات عناوين IP

في وقت كتابة نطاقات عناوين IP التي تتوافق مع نقاط النهاية هذه هي كما يلي. نوصي بشدة باستخدام  برنامج نصي مثل هذا المثال[](https://github.com/microsoft/Office365NetworkTools/tree/master/Scripts/Display%20URL-IPs-Ports%20per%20Category)، خدمة ويب IP وURL في [Microsoft 365](microsoft-365-ip-web-service.md) أو [صفحة URL/IP](urls-and-ip-address-ranges.md) للتحقق من أي تحديثات عند تطبيق التكوين، ووضع نهج للقيام بذلك بشكل منتظم.

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

الآن وقد قمنا بتحديد نقاط النهاية الهامة هذه، نحتاج إلى تحويل مسارها بعيدا عن توقف VPN والسماح له باستخدام اتصال الإنترنت المحلي للمستخدم للاتصال مباشرة بالخدمة. ستختلف الطريقة التي يتم بها تنفيذ ذلك وفقا لمنتج VPN و النظام الأساسي للجهاز المستخدمين ولكن معظم حلول VPN ستسمح ببعض التكوين البسيط من النهج لتطبيق هذا المنطق. للحصول على إرشادات تقسيم النظام الأساسي ل VPN الخاصة، راجع إرشادات [HOWTO لرهاصات VPN الأساسية الشائعة](#howto-guides-for-common-vpn-platforms).

إذا كنت ترغب في اختبار الحل يدويا، يمكنك تنفيذ مثال PowerShell التالي لمحاكاة الحل على مستوى جدول المسار. يضيف هذا المثال مسارا لكل Teams وسائط IP الفرعية إلى جدول المسار. يمكنك اختبار Teams الوسائط قبل وبعد ذلك، ومراقبة الفرق في المسارات لنقاط النهاية المحددة.

#### <a name="example-add-teams-media-ip-subnets-into-the-route-table"></a>مثال: إضافة Teams وسائط IP فرعية إلى جدول المسار

```powershell
$intIndex = "" # index of the interface connected to the internet
$gateway = "" # default gateway of that interface
$destPrefix = "52.120.0.0/14", "52.112.0.0/14", "13.107.64.0/18" # Teams Media endpoints
# Add routes to the route table
foreach ($prefix in $destPrefix) {New-NetRoute -DestinationPrefix $prefix -InterfaceIndex $intIndex -NextHop $gateway}
```

في البرنامج النصي أعلاه، _$intIndex_ هو فهرس الواجهة المتصلة بالإنترنت (ابحث عن طريق تشغيل **get-netadapter** في PowerShell، وابحث عن قيمة _ifIndex_) و _$gateway_ هو البوابة الافتراضية لهذه الواجهة (ابحث عن طريق تشغيل **ipconfig** في موجه أوامر أو **(Get-NetIPConfiguration | Foreach IPv4DefaultGateway). NextHop** في PowerShell).

بعد إضافة المسارات، يمكنك تأكيد صحة جدول المسار عن طريق تشغيل طباعة المسار في موجه أوامر أو PowerShell. يجب أن يحتوي الإخراج على المسارات التي أضفتها، مع عرض فهرس الواجهة (_22_ في هذا المثال) وبوابة تلك الواجهة (_192.168.1.1_ في هذا المثال):

![توجيه إخراج الطباعة.](../media/vpn-split-tunneling/vpn-route-print.png)

لإضافة مسارات لكل نطاقات  عناوين IP الحالية في الفئة تحسين، يمكنك استخدام تباين البرنامج النصي التالي للاستعلام عن خدمة ويب عنوان IP [وURL ل Microsoft 365](microsoft-365-ip-web-service.md) الخاصة بمجموعة عناوين IP الفرعية الحالية وإضافتها إلى جدول المسار.

#### <a name="example-add-all-optimize-subnets-into-the-route-table"></a>مثال: إضافة كافة "تحسين" الشبكة الفرعية إلى جدول المسار

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

إذا أضفت مسارات بمعلمات غير صحيحة عن غير قصد أو كنت ترغب ببساطة في العودة إلى تغييراتك، يمكنك إزالة المسارات التي أضفتها للتو باستخدام الأمر التالي:

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

يجب تكوين عميل VPN بحيث يتم توجيه حركة المرور إلى **IPs** تحسين بهذه الطريقة. يسمح ذلك لحركة المرور ب استخدام موارد Microsoft المحلية مثل Microsoft 365 الأمامية للخدمة مثل [Azure Front Door](https://azure.microsoft.com/blog/azure-front-door-service-is-now-generally-available/) التي توفر خدمات Microsoft 365 ونقاط نهاية الاتصال إلى أقرب حد ممكن للمستخدمين. يتيح لنا ذلك تقديم مستويات أداء عالية للمستخدمين أينما كانوا في العالم والاستفادة بشكل كامل من شبكة [Microsoft](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/) العالمية ذات المستوى العالمي، والتي من المرجح أن تكون ضمن بضع مللي ثانية من الخروج المباشر للمستخدمين.

## <a name="howto-guides-for-common-vpn-platforms"></a>أدلة HOWTO لرهاصات VPN الأساسية الشائعة

يوفر هذا القسم ارتباطات إلى أدلة مفصلة لتنفيذ تقسيم البيانات Microsoft 365 البيانات من الشركاء الأكثر شيوعا في هذه المساحة. سنضيف أدلة إضافية عندما تصبح متوفرة.

- **Windows 10 VPN**: تحسين [Microsoft 365 المرور للعاملين عن بعد باستخدام عميل VPN الأصلي Windows 10 VPN](/windows/security/identity-protection/vpn/vpn-office-365-optimization)
- **Cisco Anyconnect**: [تحسين Anyconnect Split Splitهاي في Office365](https://www.cisco.com/c/en/us/support/docs/security/anyconnect-secure-mobility-client/215343-optimize-anyconnect-split-tunnel-for-off.html)
- **Palo Alto GlobalProtect**: [تحسين Microsoft 365 المرور عبر VPN Split Splitواستثناء مسار الوصول](https://live.paloaltonetworks.com/t5/Prisma-Access-Articles/GlobalProtect-Optimizing-Office-365-Traffic/ta-p/319669)
- **F5 Networks BIG-IP APM**: تحسين Microsoft 365 المرور على الوصول البعيد من خلال [شبكات VPN عند استخدام BIG-IP APM](https://devcentral.f5.com/s/articles/SSL-VPN-Split-Tunneling-and-Office-365)
- **بوابة Citrix**: [تحسين تقسيم خدمة VPN لبوابة Citrix ل Office365](https://docs.citrix.com/citrix-gateway/13/optimizing-citrix-gateway-vpn-split-tunnel-for-office365.html)
- **Pulse Secure**: [VPNتأمين: كيفية تكوين تقسيم تقسيم إلى آخر لاستبعاد تطبيقات](https://kb.pulsesecure.net/articles/Pulse_Secure_Article/KB44417) Microsoft 365
- **نقطة اختيار VPN**: [كيفية تكوين Split Split Split For Microsoft 365 وتطبيقات SaaS الأخرى](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk167000)

## <a name="related-articles"></a>المقالات ذات الصلة

[نظرة عامة: تقسيم VPN إلى تقسيم Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[سيناريوهات تقسيم VPN الشائعة للانقسام Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[تأمين Teams الوسائط من أجل تقسيم VPN](microsoft-365-vpn-securing-teams.md)

[اعتبارات خاصة للبث والأحداث المباشرة في بيئات VPN](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 تحسين أداء المستخدمين في الصين](microsoft-365-networking-china.md)

[Microsoft 365 "مبادئ اتصال الشبكة"](microsoft-365-network-connectivity-principles.md)

[تقييم Microsoft 365 الشبكة](assessing-network-connectivity.md)

[Microsoft 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[طرق بديلة لمحترفي الأمان تكنولوجيا المعلومات لتحقيق عناصر التحكم الحديثة في الأمان في سيناريوهات العمل عن بعد الفريدة اليوم (مدونة فريق أمان Microsoft)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[تحسين أداء VPN في Microsoft: Windows 10 ملفات تعريف VPN للسماح باتصالات التشغيل التلقائي](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[تشغيل VPN: كيف تحافظ Microsoft على اتصال القوى العاملة البعيدة](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[شبكة Microsoft العامة](/azure/networking/microsoft-global-network)
