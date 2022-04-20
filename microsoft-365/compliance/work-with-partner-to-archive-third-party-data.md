---
title: العمل مع شريك لأرشفة بيانات جهة خارجية
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: تعرف على كيفية إعداد موصل مخصص لاستيراد بيانات الجهات الخارجية من مصادر البيانات مثل Salesforce Chatter أو Yahoo Messenger أو Yammer.
ms.openlocfilehash: 72159d88cdeb8c573f1a71342ca7cbd015099568
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944492"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>العمل مع شريك لأرشفة بيانات جهة خارجية

يمكنك العمل مع شريك Microsoft لاستيراد البيانات وأرشفتها من مصدر بيانات تابع لجهة خارجية إلى Microsoft 365. يمكن أن يوفر لك الشريك موصلا مخصصا تم تكوينه لاستخراج العناصر من مصدر بيانات الجهات الخارجية (بشكل منتظم) ثم استيراد هذه العناصر. يحول موصل الشريك محتوى عنصر من مصدر البيانات إلى تنسيق رسالة بريد إلكتروني ثم يخزن العناصر في علب البريد. بعد استيراد بيانات الجهات الخارجية، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي وeDiscovery In-Place والأرشفة والتدقيق Microsoft 365 نهج الاستبقاء على هذه البيانات.

> [!IMPORTANT]
> لا يمكن تطبيق حل [توافق الاتصالات](communication-compliance.md) في Microsoft 365 على بيانات الجهات الخارجية التي تم استيرادها من قبل موصلات الشركاء المذكورة في هذه المقالة.

فيما يلي نظرة عامة على العملية والخطوات اللازمة للعمل مع شريك Microsoft لاستيراد بيانات الجهات الخارجية.

[الخطوة 1: البحث عن شريك بيانات تابع لجهة خارجية](#step-1-find-a-third-party-data-partner)

[الخطوة 2: إنشاء علبة بريد بيانات تابعة لجهة خارجية وتكوينها](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[الخطوة 3: تكوين علب بريد المستخدمين لبيانات الجهات الخارجية](#step-3-configure-user-mailboxes-for-third-party-data)

[الخطوة 4: تزويد شريكك بمعلومات](#step-4-provide-your-partner-with-information)

[الخطوة 5: تسجيل موصل بيانات الجهات الخارجية في Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>كيفية عمل عملية استيراد البيانات من جهة خارجية

يوضح الرسم التوضيحي والوصف التالي كيفية عمل عملية استيراد البيانات من جهة خارجية عند العمل مع شريك.

![كيفية عمل عملية استيراد البيانات من جهة خارجية.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. يعمل العميل مع الشريك الذي يختاره لتكوين موصل يستخرج العناصر من مصدر البيانات التابع لجهة خارجية ثم يستورد هذه العناصر إلى Microsoft 365.

2. يتصل موصل الشريك بمصادر بيانات تابعة لجهة خارجية عبر واجهة برمجة تطبيقات تابعة لجهة خارجية (على أساس مجدول أو حسب التكوين) ويستخرج العناصر من مصدر البيانات. يحول موصل الشريك محتوى عنصر إلى تنسيق رسالة بريد إلكتروني. راجع المقطع ["مزيد من المعلومات](#more-information) " للحصول على وصف لمخطط تنسيق الرسالة.

3. يتصل موصل الشريك بخدمة Azure في Microsoft 365 باستخدام Exchange Web Service (EWS) عبر نقطة نهاية معروفة.

4. يتم استيراد العناصر إلى علبة بريد مستخدم معين أو إلى علبة بريد بيانات "التقاط الكل" التابعة لجهة خارجية. يستند ما إذا كان يتم استيراد عنصر إلى علبة بريد مستخدم معينة أو إلى علبة بريد بيانات جهة خارجية إلى المعايير التالية:

   1. **العناصر التي تحتوي على معرف مستخدم يتوافق مع حساب مستخدم:** إذا كان بإمكان موصل الشريك تعيين معرف المستخدم للعنصر في مصدر بيانات جهة خارجية إلى معرف مستخدم معين في Microsoft 365، يتم نسخ العنصر إلى مجلد **"عمليات الإزالة**" في مجلد "العناصر القابلة للاسترداد" الخاص بالمستخدم. لا يمكن للمستخدمين الوصول إلى العناصر في مجلد "عمليات الإزالة". ومع ذلك، يمكنك استخدام أدوات eDiscovery للبحث عن عناصر في مجلد "عمليات الإزالة".

   1. **العناصر التي لا تحتوي على معرف مستخدم يتوافق مع حساب مستخدم:** إذا تعذر على موصل الشريك تعيين معرف المستخدم لعنصر إلى معرف مستخدم معين، يتم نسخ العنصر إلى مجلد **علبة الوارد** في علبة بريد البيانات التابعة لجهة خارجية. يسمح لك استيراد العناصر إلى علبة الوارد أو لشخص ما في مؤسستك بتسجيل الدخول إلى علبة بريد الجهات الخارجية لعرض هذه العناصر وإدارتها، ومعرفة ما إذا كان يجب إجراء أي تعديلات في تكوين موصل الشريك.

## <a name="step-1-find-a-third-party-data-partner"></a>الخطوة 1: البحث عن شريك بيانات تابع لجهة خارجية

أحد المكونات الرئيسية لأرشفة بيانات الجهات الخارجية في Microsoft 365 هو البحث عن شريك Microsoft متخصص في التقاط البيانات من مصدر بيانات تابع لجهة خارجية واستيرادها إلى Microsoft 365 والعمل معه. بعد استيراد البيانات، يمكن أرشفتها والحفاظ عليها مع بيانات Microsoft الأخرى لمؤسستك، مثل البريد الإلكتروني من Exchange والمستندات من SharePoint OneDrive for Business. ينشئ الشريك موصلا يستخرج البيانات من مصادر البيانات التابعة لجهة خارجية لمؤسستك (مثل BlackBerry وFacebook وGoogle+وThomson Connectors وTwitter وYouTube) ويمرر تلك البيانات إلى واجهة برمجة تطبيقات Microsoft 365 تقوم باستيراد العناصر إلى علب بريد Exchange كرسائل بريد إلكتروني.

تسرد الأقسام التالية شركاء Microsoft (ومصادر بيانات الجهات الخارجية التي يدعمونها) المشاركين في البرنامج لأرشفة بيانات الجهات الخارجية في Microsoft 365.

[17a-4 LLC](#17a-4-llc)

[ArchiveSocial](#archivesocial)

[فيريتاس](#veritas)

[نص مفتوح](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

يدعم [17a-4 LLC](https://www.17a-4.com) مصادر بيانات الجهات الخارجية التالية:

- بلاك بيري

- بيانات بلومبيرغ عمليات الدفق

- Cisco Jabber

- مجموعة الحقائق

- HipChat

- InvestEdge

- LivePerson

- عمليات الدفق بيانات MessageLabs

- نص مفتوح

- تعليمات Live ل Oracle/ATG "النقر للاتصال"

- Pivot IMIMAR

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype for Business (Lync/OCS)

- Skype for Business Online (Lync Online)

- قواعد بيانات SQL

- Squawker

- ThomsonHomsonHoms Eikon Messenger

### <a name="archivesocial"></a>ArchiveSocial

يدعم [ArchiveSocial](https://www.archivesocial.com) مصادر بيانات الجهات الخارجية التالية:

- ف يسبوك

- فل يكر

- اينستاجرام

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>فيريتاس

تدعم [Veritas](https://www.globanet.com) مصادر بيانات الجهات الخارجية التالية:

- AOL مع Pivot Client

- BlackBerry Call Logs (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- دردشة بلومبيرغ

- بريد بلومبيرغ

- مربع

- CipherCloud ل Salesforce Chatter

- Cisco IM &amp; Presence Server (v10, v10.5.1 SU1, v11.0, v11.5 SU2)

- Cisco Webex Teams

- Citrix Workspace &amp; ShareFile

- CrowdCompass

- ملفات نصية محددة مخصصة

- ملفات XML المخصصة

- Facebook (صفحات)

- مجموعة الحقائق

- FXConnect

- ICE Chat/YellowJacket

- Jive

- Macgregor XIP

- Microsoft Exchange Server

- Microsoft OneDrive for Business

- Microsoft Teams

- Microsoft Yammer

- حماية الأجهزة المحمولة

- Pivot

- Salesforce Chatter

- Skype for Business Online

- Skype for Business، الإصدارات 2007 R2 - 2016 (محليا)

- Slack Enterprise Grid

- Symphony

- Thomson Messengers Eikon

- Thomson Reuters Messenger

- ThomsonFxs Dealings 3000 / FX Trading

- Twitter

- UBS Chat

- YouTube

### <a name="opentext"></a>نص مفتوح

يدعم [OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) مصادر بيانات الجهات الخارجية التالية:

- Axs Encrypted

- Exchange Axs

- الأرشيف المحلي ل Axs

- عنصر نائب ل Axs

- Axs Signed

- بلومبرغ

- ThomsonHomson

### <a name="smarsh"></a>Smarsh

يدعم [Smarsh](https://www.smarsh.com) مصادر بيانات الجهات الخارجية التالية:

- الهدف

- المعرف الأمريكي

- تفاحة فافة

- AOL مع عميل Pivot

- اريس

- Bazaar Voice

- مشاركة الدب

- Bit Unity

- BlackBerry Call Logs (v5, v10, v12)

- BlackBerry Messenger (v5, v10, v12)

- BlackBerry PIN (v5, v10, v12)

- BlackBerry SMS (v5, v10, v12)

- بريد بلومبيرغ

- CellTrust

- استيراد الدردشة

- الدردشة في الوقت الحقيقي التسجيل والنهج

- الثرثره

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Unified Presence Server (v8.6.3, v8.6.4, v8.6.5)

- استيراد التعاون

- تسجيل التعاون في الوقت الحقيقي

- الاتصال المباشر

- ف يسبوك

- مجموعة الحقائق

- FastTrack

- نوتلا

- Google+

- GoToMyPC

- وثبة

- HubConnex

- IBM Connections (v3.0.1, v4.0, v4.5, v4.5 CR3, v5)

- IBM Connections Chat Cloud

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- IBM SameTime Community (v8.0.2, v8.5.1 IFR2, v8.5.2 IFR1, v9.1)

- IBM SameTime Complete 9.0

- IBM SameTime Conference 9.0

- IBM SameTime Meeting 8.5.2 IFR1

- ICE/YellowJacket

- استيراد المراسلة الفورية

- تسجيل المراسلة الفورية ونهجها في الوقت الحقيقي

- Indii Messenger

- Instant Bloomberg

- الايرسي

- Jive

- Jive 6 Real Time Logging (v6, v7)

- استيراد Jive

- JXTA

- LinkedIn

- Microsoft Lync (2010، 2013)

- MFTP

- صوت Microsoft Lync 2013

- Microsoft SharePoint (2010، 2013)

- Microsoft Office SharePoint Online

- Microsoft UC (الاتصالات الموحدة)

- MindAlign

- حماية الأجهزة المحمولة

- MSN

- المساحة

- الشبكات المناظرة على شبكة الإنترنت

- Microsoft 365 Lync Dedicated

- Microsoft 365 رسالة فورية مشتركة

- Pinterest

- Pivot

- QQ

- Skype for Business 2015

- اللينة

- Symphony

- Thomson Messengers Eikon

- Thomson Reuters Messenger

- تور

- TTT

- Twitter

- WinMX

- Winny

- ياهو

- Yammer

- YouTube


### <a name="verba"></a>Verba

يدعم [Verba](https://www.verba.com) مصادر بيانات الجهات الخارجية التالية:

- فيديو Aveo Aura

- Avice Aura Voice

- Avtec Radio

- Bosch/Telex Radio

- فيديو BroadSoft

- BroadSoft Voice

- Centile Voice

- رسالة فورية من Cisco Jabber

- فيديو Cisco UC

- Cisco UC Voice

- فيديو Cisco UCCX/UCCE

- Cisco UCCX/UCCE Voice

- راديو ESChat

- Geoman Contact Expert

- IP Trade Voice

- Luware LUCS Contact Center

- Microsoft UC (الاتصالات الموحدة)

- مركز Mitel MiContact ل Lync (prairieFyre)

- فيديو وحدة تحكم حدود جلسة عمل Oracle / Acme

- Oracle / Acme Packet Session Border Controller Voice

- Singtel Mobile Voice

- فيديو SIPREC

-  SIPREC Voice

- رسالة فورية Skype for Business / Lync

- فيديو Skype for Business / Lync

- Skype for Business / Lync Voice

- سماعة صوت

- فيديو SIP/H.323 قياسي

- صوت SIP/H.323 قياسي

- صوت Truphone

- راديو لويEdPair

- شاشة كمبيوتر سطح المكتب Windows

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>الخطوة 2: إنشاء علبة بريد بيانات تابعة لجهة خارجية وتكوينها في Microsoft 365

فيما يلي خطوات إنشاء علبة بريد بيانات تابعة لجهة خارجية وتكوينها لاستيراد البيانات إلى Microsoft 365. كما هو موضح سابقا، يتم استيراد العناصر إلى علبة البريد هذه إذا تعذر على موصل الشريك تعيين معرف المستخدم للعنصر إلى حساب مستخدم.

 **أكمل هذه المهام في مركز مسؤولي Microsoft 365**

1. إنشاء حساب مستخدم وتعيين ترخيص Exchange Online الخطة 2 له؛ راجع [إضافة مستخدمين إلى Microsoft 365](../admin/add-users/add-users.md). يلزم ترخيص الخطة 2 لوضع علبة البريد في "احتجاز التقاضي" أو تمكين علبة بريد أرشيف لها حصة تخزين تصل إلى 1.5 تيرابايت.

2. أضف حساب المستخدم الخاص بعلبة بريد بيانات الجهات الخارجية إلى دور **مسؤول مسؤول Exchange** في Microsoft 365؛ راجع [تعيين أدوار المسؤولين في Microsoft 365](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > اكتب بيانات الاعتماد لحساب المستخدم هذا. تحتاج إلى توفيرها لشريكك، كما هو موضح في الخطوة 4.

 **إكمال هذه المهام في مركز إدارة Exchange**

1. إخفاء علبة بريد بيانات الجهات الخارجية من دفتر العناوين وقوائم العناوين الأخرى في مؤسستك؛ راجع [إدارة علب بريد المستخدمين](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). بدلا من ذلك، يمكنك تشغيل أمر PowerShell التالي:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. قم بتعيين إذن **FullAccess** إلى علبة بريد بيانات الجهات الخارجية بحيث يمكن للمسؤولين أو مسؤولي التوافق فتح علبة بريد بيانات الجهات الخارجية في عميل سطح المكتب Outlook؛ راجع [أذونات إدارة المستلمين](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. تمكين الميزات التالية المتعلقة بالامتثال لعل بريد بيانات الجهات الخارجية:

    - تمكين علبة بريد الأرشيف؛ راجع [تمكين علب بريد الأرشيف](enable-archive-mailboxes.md) وتمكين [الأرشفة ذات التوسيع التلقائي](enable-autoexpanding-archiving.md). يتيح لك ذلك توفير مساحة تخزين في علبة البريد الأساسية عن طريق إعداد نهج أرشيف ينقل عناصر بيانات الجهات الخارجية إلى علبة بريد الأرشيف. يوفر لك هذا ما يصل إلى 1.5 تيرابايت من التخزين لبيانات الجهات الخارجية.

    - ضع علبة بريد بيانات الجهات الخارجية في "احتجاز التقاضي". يمكنك أيضا تطبيق نهج استبقاء Microsoft 365 في مركز الأمان والتوافق. يؤدي وضع علبة البريد هذه قيد الاحتجاز إلى الاحتفاظ بالعناصر الخاصة ببيانات الجهات الخارجية (إلى أجل غير مسمى أو لمدة محددة) ومنع إزالتها من علبة البريد. راجع أحد المواضيع التالية:

      - [وضع علبة بريد في احتجاز التقاضي](./create-a-litigation-hold.md)

      - [التعرف على نهج الاستبقاء وتسميات الاستبقاء](retention.md)

    - تمكين تسجيل تدقيق علبة البريد للوصول إلى علبة بريد البيانات الخاصة بالمالك والمفوض والمسؤول؛ راجع [تمكين تدقيق علبة البريد](enable-mailbox-auditing.md). يسمح لك هذا بتدقيق كافة الأنشطة التي يقوم بها أي مستخدم لديه حق الوصول إلى علبة بريد بيانات الجهات الخارجية.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>الخطوة 3: تكوين علب بريد المستخدمين لبيانات الجهات الخارجية

الخطوة التالية هي تكوين علب بريد المستخدمين لدعم بيانات الجهات الخارجية. أكمل هذه المهام باستخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> أو باستخدام أوامر cmdlets Windows PowerShell المقابلة.

1. تمكين علبة بريد الأرشيف لكل مستخدم؛ راجع [تمكين علب بريد الأرشيف](enable-archive-mailboxes.md) وتمكين [الأرشفة ذات التوسيع التلقائي](enable-autoexpanding-archiving.md).

2. ضع علب بريد المستخدمين في "احتجاز التقاضي" أو طبق نهج استبقاء Microsoft 365؛ راجع أحد المواضيع التالية:

    - [وضع علبة بريد في احتجاز التقاضي](./create-a-litigation-hold.md)

    - [التعرف على نهج الاستبقاء وتسميات الاستبقاء](retention.md)

    كما ذكر سابقا، عند وضع علب البريد قيد الاحتجاز، يمكنك تعيين مدة للاحتفاظ بالعناصر من مصدر بيانات جهة خارجية أو يمكنك اختيار الاحتفاظ بالعناصر إلى أجل غير مسمى.

## <a name="step-4-provide-your-partner-with-information"></a>الخطوة 4: تزويد شريكك بمعلومات

الخطوة الأخيرة هي تزويد شريكك بالمعلومات التالية حتى يتمكنوا من تكوين الموصل للاتصال بمؤسستك لاستيراد البيانات إلى علب بريد المستخدمين وعلبة بريد بيانات الجهات الخارجية.

- نقطة النهاية المستخدمة للاتصال بخدمة Azure في Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- بيانات اعتماد تسجيل الدخول (Microsoft 365 معرف المستخدم وكلمة المرور) الخاصة بعلبة بريد البيانات التابعة لجهة خارجية التي قمت بإنشائها في الخطوة 2. بيانات الاعتماد هذه مطلوبة بحيث يمكن لموصل الشريك الوصول إلى العناصر واستيرادها إلى علب بريد المستخدمين وعلبة بريد البيانات الخاصة بالجهة الخارجية.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>الخطوة 5: تسجيل موصل بيانات الجهات الخارجية في Azure Active Directory

بدءا من 30 سبتمبر 2018، ستبدأ خدمة Azure في Microsoft 365 باستخدام المصادقة الحديثة في Exchange Online لمصادقة موصلات البيانات التابعة لجهة خارجية التي تحاول الاتصال بمؤسستك لاستيراد البيانات. والسبب في هذا التغيير هو أن المصادقة الحديثة توفر أمانا أكثر من الأسلوب الحالي، والذي كان يستند إلى قائمة السماح لموصلات الجهات الخارجية التي تستخدم نقطة النهاية الموضحة مسبقا للاتصال بخدمة Azure.

لتمكين موصل بيانات تابع لجهة خارجية للاتصال Microsoft 365 باستخدام أسلوب المصادقة الحديث الجديد، يجب على المسؤول في مؤسستك الموافقة على تسجيل الموصل كتطبيق خدمة موثوق به في Azure Active Directory. يتم ذلك عن طريق قبول طلب إذن للسماح للموصل بالوصول إلى بيانات مؤسستك في Azure Active Directory. بعد قبول هذا الطلب، تتم إضافة موصل البيانات التابع لجهة خارجية كتطبيق مؤسسة إلى Azure Active Directory ويتم تمثيله ككيان خدمة. لمزيد من المعلومات حول عملية الموافقة، راجع  [موافقة مسؤول المستأجر](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

فيما يلي خطوات الوصول إلى طلب تسجيل الموصل وقبوله:

1. انتقل إلى [هذه الصفحة](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) وسجل الدخول باستخدام بيانات اعتماد مسؤول عام.

   يتم عرض مربع الحوار التالي. يمكنك توسيع علامة الاقباط لمراجعة الأذونات التي سيتم تعيينها إلى الموصل.

   ![يتم عرض مربع حوار طلب الأذونات.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. انقر فوق **"قبول**".

بعد قبول الطلب، يتم عرض مدخل [Azure](https://portal.azure.com) . لعرض قائمة التطبيقات لمؤسستك، انقر فوق تطبيقات **Azure Active DirectoryEnterprise** > . يتم سرد موصل بيانات Microsoft 365 جهة خارجية على جزء **تطبيقات Enterprise**.

> [!IMPORTANT]
> بعد 30 سبتمبر 2018، لن يتم استيراد بيانات الجهات الخارجية إلى علب البريد في مؤسستك إذا لم تقم بتسجيل موصل بيانات تابع لجهة خارجية في Azure Active Directory. لاحظ أنه يجب أيضا تسجيل موصلات البيانات التابعة لجهة خارجية (تلك التي تم إنشاؤها قبل 30 سبتمبر 2018) في Azure Active Directory باتباع الإجراء الوارد في الخطوة 5.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>إبطال الموافقة على موصل بيانات تابع لجهة خارجية

بعد موافقة مؤسستك على طلب الأذونات لتسجيل موصل بيانات تابع لجهة خارجية في Azure Active Directory، يمكن لمؤسستك إبطال هذه الموافقة في أي وقت. ومع ذلك، فإن إبطال الموافقة على موصل يعني أنه لن يتم استيراد البيانات من مصدر بيانات جهة خارجية إلى Microsoft 365.

لإلغاء الموافقة على موصل بيانات تابع لجهة خارجية، يمكنك حذف التطبيق (عن طريق حذف كيان الخدمة المقابل) من Azure Active Directory باستخدام جزء **تطبيقات المؤسسة** في مدخل Azure، أو باستخدام [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) في Microsoft 365 PowerShell. يمكنك أيضا استخدام [cmdlet Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) في Azure Active Directory PowerShell.

## <a name="more-information"></a>معلومات إضافية

- كما هو موضح سابقا، يتم استيراد عناصر من مصادر بيانات تابعة لجهة خارجية إلى علب بريد Exchange كرسائل بريد إلكتروني. يقوم موصل الشريك باستيراد العنصر باستخدام مخطط مطلوب من قبل واجهة برمجة تطبيقات Microsoft 365. يصف الجدول التالي خصائص رسالة عنصر من مصدر بيانات تابع لجهة خارجية بعد استيراده إلى علبة بريد Exchange كرسالة بريد إلكتروني. يشير الجدول أيضا إلى ما إذا كانت خاصية الرسالة إلزامية. يجب ملء الخصائص الإلزامية. إذا يفتقد عنصر إلى خاصية إلزامية، فلن يتم استيراده إلى Microsoft 365. ترجع عملية الاستيراد رسالة خطأ تشرح سبب عدم استيراد عنصر والخاصية المفقودة.<br/><br/>

    |**خاصية الرسالة**|**الزاميه؟**|**الوصف**|**قيمة المثال**|
    |:-----|:-----|:-----|:-----|
    |**من** <br/> |نعم  <br/> |المستخدم الذي قام في الأصل بإنشاء العنصر أو إرساله في مصدر بيانات الجهات الخارجية. يحاول موصل الشريك تعيين معرف المستخدم من العنصر المصدر (على سبيل المثال مقبض Twitter) إلى حساب مستخدم لجميع المشاركين (المستخدمين في الحقلين "من" و"إلى"). سيتم استيراد نسخة من الرسالة إلى علبة بريد كل مشارك. إذا لم يتم تعيين أي من المشاركين من العنصر إلى حساب مستخدم، فسيتم استيراد العنصر إلى علبة بريد الأرشفة التابعة لجهة خارجية في Microsoft 365.  <br/> <br/> يجب أن يكون لدى المشارك الذي تم تعريفه كمرسل للعنصر علبة بريد نشطة في المؤسسة التي يتم استيراد العنصر إليها. إذا لم يكن لدى المرسل علبة بريد نشطة، فسيتم إرجاع الخطأ التالي:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**ل** <br/> |نعم  <br/> |المستخدم الذي تلقى عنصرا، إذا كان قابلا للتطبيق على عنصر في مصدر البيانات.  <br/> | `bob@contoso.com` <br/> |
    |**الموضوع** <br/> |لا  <br/> |الموضوع من العنصر المصدر.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**تاريخ** <br/> |نعم  <br/> |تاريخ إنشاء العنصر في الأصل أو نشره في مصدر بيانات العميل. على سبيل المثال، هذا التاريخ الذي تم فيه تغريد رسالة Twitter.  <br/> | `01 NOV 2015` <br/> |
    |**الجسم** <br/> |لا  <br/> |محتويات الرسالة أو النشر. بالنسبة لبعض مصادر البيانات، قد تكون محتويات هذه الخاصية هي نفسها محتوى الخاصية **SUBJECT** . أثناء عملية الاستيراد، يحاول موصل الشريك الحفاظ على الدقة الكاملة من مصدر المحتوى قدر الإمكان. إذا كان من الممكن تضمين ملفات أو رسومات أو محتوى آخر من النص الأساسي للعنصر المصدر في هذه الخاصية. وإلا، يتم تضمين المحتوى من العنصر المصدر في الخاصية **"مرفق** ". تعتمد محتويات هذه الخاصية على موصل الشريك وعلى قدرة النظام الأساسي المصدر.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**المرفق** <br/> |لا  <br/> |إذا كان أحد العناصر في مصدر البيانات (مثل تغريدة في Twitter أو محادثة مراسلة فورية) يحتوي على ملف مرفق أو يتضمن صورا، فسيحاول اتصال الشريك أولا تضمين مرفقات في خاصية **BODY** . إذا لم يكن ذلك ممكنا، فسيتم إضافته إلى الخاصية ** ATTACHMENT **. تتضمن الأمثلة الأخرى للمرفقات تسجيلات الإعجاب في Facebook وبيانات التعريف من مصدر المحتوى والاستجابات لرسالة أو منشور.  <br/> | `image.gif` <br/> |
    |**MESSAGECLASS** <br/> |نعم  <br/> | هذه خاصية متعددة القيم، يتم إنشاؤها وتعبئتها بواسطة موصل الشريك. تنسيق هذه الخاصية هو  `IPM.NOTE.Source.Event`. (يجب أن تبدأ هذه الخاصية ب  `IPM.NOTE`. يشبه هذا التنسيق التنسيق الخاص بفئة  `IPM.NOTE.X` الرسائل.) تتضمن هذه الخاصية المعلومات التالية:  <br/><br/>`Source`: يشير إلى مصدر بيانات الجهات الخارجية؛ على سبيل المثال، Twitter أو Facebook أو BlackBerry.  <br/> <br/>  `Event`: يشير إلى نوع النشاط الذي تم تنفيذه في مصدر بيانات الجهات الخارجية الذي أنتج العناصر؛ على سبيل المثال، تغريدة في Twitter أو منشور في Facebook. الأحداث خاصة لمصدر البيانات.  <br/> <br/>  أحد أغراض هذه الخاصية هو تصفية عناصر معينة استنادا إلى مصدر البيانات حيث تم إنشاء عنصر أو استنادا إلى نوع الحدث. على سبيل المثال، في بحث eDiscovery، يمكنك إنشاء استعلام بحث للعثور على كل التغريدات التي تم نشرها من قبل مستخدم معين.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- عند استيراد العناصر بنجاح إلى علب البريد في Microsoft 365، يتم إرجاع معرف فريد مرة أخرى إلى المتصل كجزء من استجابة HTTP. يمكن استخدام هذا المعرف، المسمى  `x-IngestionCorrelationID`، لأغراض استكشاف الأخطاء وإصلاحها اللاحقة من قبل الشركاء لتعقب العناصر من طرف إلى طرف. من المستحسن أن يلتقط الشركاء هذه المعلومات ويسجلونها وفقا لذلك في نهايتها. فيما يلي مثال على استجابة HTTP تظهر هذا المعرف:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- يمكنك استخدام أداة البحث عن المحتوى في مركز الأمان والتوافق للبحث عن العناصر التي تم استيرادها إلى علب البريد من مصدر بيانات تابع لجهة خارجية. للبحث بشكل خاص عن هذه العناصر المستوردة، يمكنك استخدام أزواج قيم خصائص الرسالة التالية في مربع الكلمة الأساسية للبحث في المحتوى.

  - **`kind:externaldata`**: استخدم زوج قيمة الخاصية هذا للبحث في كافة أنواع بيانات الجهات الخارجية. على سبيل المثال، للبحث عن العناصر التي تم استيرادها من مصدر بيانات تابع لجهة خارجية وتحتوي على الكلمة "contoso" في خاصية الموضوع للعنصر المستورد، يمكنك استخدام استعلام  `kind:externaldata AND subject:contoso`الكلمة الأساسية.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: استخدم زوج قيمة الخاصية هذا للبحث فقط في نوع تحديد بيانات الجهات الخارجية. على سبيل المثال، للبحث في بيانات Facebook التي تحتوي على الكلمة "contoso" في خاصية الموضوع فقط، يمكنك استخدام استعلام  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`الكلمة الأساسية.

  للحصول على قائمة كاملة بالقيم المطلوب استخدامها لأنواع بيانات الجهات الخارجية للخاصية`itemclass`، راجع ["استخدام البحث في المحتوى" للبحث في بيانات الجهات الخارجية التي تم استيرادها إلى Microsoft 365](use-content-search-to-search-third-party-data-that-was-imported.md).

   لمزيد من المعلومات حول استخدام البحث في المحتوى وإنشاء استعلامات البحث عن الكلمات الأساسية، راجع:

  - [البحث في المحتوى](content-search.md)

  - [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md)