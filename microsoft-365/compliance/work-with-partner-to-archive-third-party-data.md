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
description: تعرف على كيفية إعداد موصل مخصص لاستيراد بيانات جهة خارجية من مصادر بيانات مثل Salesforce Chatter أو Yahoo Messenger أو Yammer.
ms.openlocfilehash: 53c6cae76327c7a8fb8ca89de464ad8a63e75d6a
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63566124"
---
# <a name="work-with-a-partner-to-archive-third-party-data"></a>العمل مع شريك لأرشفة بيانات جهة خارجية

يمكنك العمل مع شريك Microsoft لاستيراد البيانات وأرشفتها من مصدر بيانات جهة خارجية إلى Microsoft 365. يمكن أن يوفر لك الشريك موصلا مخصصا تم تكوينه لاستخراج العناصر من مصدر بيانات جهة خارجية (بشكل منتظم) ثم استيراد هذه العناصر. يحول موصل الشريك محتوى عنصر من مصدر البيانات إلى تنسيق رسالة بريد إلكتروني ثم يخزن العناصر في علب البريد. بعد استيراد بيانات جهة خارجية، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية و eDiscovery و In-Place الأرشفة والتدقيق Microsoft 365 والاستبقاء لهذه البيانات.

> [!IMPORTANT]
> لا [يمكن تطبيق](communication-compliance.md) حل توافق Microsoft 365 على بيانات الأطراف الخارجية التي تستوردها موصلات الشركاء المذكورة في هذه المقالة.

فيما يلي نظرة عامة حول العملية والخطوات اللازمة للعمل مع شريك Microsoft لاستيراد بيانات جهة خارجية.

[الخطوة 1: البحث عن شريك بيانات جهة خارجية](#step-1-find-a-third-party-data-partner)

[الخطوة 2: إنشاء علبة بريد بيانات جهة خارجية وتكوينها](#step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365)

[الخطوة 3: تكوين علب بريد المستخدمين لبيانات كيانات خارجية](#step-3-configure-user-mailboxes-for-third-party-data)

[الخطوة 4: تزويد شريكك بالمعلومات](#step-4-provide-your-partner-with-information)

[الخطوة 5: تسجيل موصل بيانات جهة خارجية في Azure Active Directory](#step-5-register-the-third-party-data-connector-in-azure-active-directory)

## <a name="how-the-third-party-data-import-process-works"></a>كيفية عمل عملية استيراد البيانات من جهة خارجية

يوضح الرسم التوضيحي التالي والوصف التالي كيفية عمل عملية استيراد البيانات من جهة خارجية عند العمل مع شريك.

![كيفية عمل عملية استيراد البيانات من جهة خارجية.](../media/5d4cf8e9-b4cc-4547-90c8-d12d04a9f0e7.png)

1. يعمل العميل مع الشريك الذي تختاره لتكوين موصل يقوم باستخراج العناصر من مصدر بيانات جهة خارجية ثم استيراد هذه العناصر إلى Microsoft 365.

2. يتصل موصل الشريك بمصادر بيانات جهة خارجية عبر API (على أساس مجدول أو كما تم تكوينه) ويستخرج العناصر من مصدر البيانات. يحول موصل الشريك محتوى عنصر إلى تنسيق رسالة بريد إلكتروني. راجع القسم [مزيد من المعلومات](#more-information) للحصول على وصف لم مخطط تنسيق الرسالة.

3. يتصل موصل الشريك لخدمة Azure في Microsoft 365 باستخدام Exchange ويب (EWS) عبر نقطة نهاية معروفة.

4. يتم استيراد العناصر إلى علبة بريد مستخدم معين أو إلى علبة بريد بيانات "التقاط الكل" من جهة خارجية. يستند استيراد عنصر إلى علبة بريد مستخدم معينة أو إلى علبة بريد بيانات جهة خارجية إلى المعايير التالية:

   1. **العناصر التي لديها "معرّف مستخدم" يتطابق مع حساب مستخدم:** إذا كان بامكن لموصل الشريك تعيين اسم المستخدم الخاص بالعنصر في مصدر البيانات الخاص ب جهة خارجية إلى "معرِّف مستخدم" معين في Microsoft 365، يتم نسخ العنصر إلى المجلد  "إزالة" في مجلد "العناصر القابلة لاسترداد" الخاص بالمستخدم. لا يمكن للمستخدمين الوصول إلى العناصر في مجلد "إزالة". ومع ذلك، يمكنك استخدام أدوات eDiscovery للبحث عن العناصر في مجلد "إزالة".

   1. العناصر التي ليس لديها "اسم مستخدم" **يتطابق مع حساب مستخدم:** إذا لم يكن موصل الشريك يمكنه تعيين "تعريف المستخدم" الخاص بعنصر ما إلى "معرِّف مستخدم" معين، يتم نسخ  العنصر إلى مجلد علبة الوارد في علبة بريد البيانات الخاصة ب جهة خارجية. تسمح لك عملية استيراد العناصر إلى علبة الوارد أو أي شخص في مؤسستك تسجيل الدخول إلى علبة بريد جهة خارجية لعرض هذه العناصر وإدارتها، وترى ما إذا كان يجب إجراء أي تعديلات في تكوين موصل الشريك.

## <a name="step-1-find-a-third-party-data-partner"></a>الخطوة 1: البحث عن شريك بيانات جهة خارجية

أحد المكونات الأساسية لأرشفة بيانات جهة خارجية في Microsoft 365 هو البحث عن شريك Microsoft متخصص في التقاط البيانات من مصدر بيانات جهة خارجية واستيرادها إلى Microsoft 365. بعد استيراد البيانات، يمكن أرشفتها والحفاظ عليها مع بيانات Microsoft الأخرى في مؤسستك، مثل البريد الإلكتروني من Exchange والمستندات من SharePoint OneDrive for Business. ينشئ الشريك موصلا يستخرج البيانات من مصادر بيانات جهة خارجية في مؤسستك (مثل BlackBerry و Facebook و Google+و Thomson Reuters و Twitter و YouTube) ويمرر هذه البيانات إلى API Microsoft 365 الذي يستورد العناصر إلى علب بريد Exchange كرسائل بريد إلكتروني.

تقوم الأقسام التالية سرد شركاء Microsoft (ومصادر بيانات  الأطراف الخارجية التي يدعمونها) المشاركين في البرنامج لأرشفة بيانات جهة خارجية في Microsoft 365.

[17a-4 LLC](#17a-4-llc)

[ArchiveSocial](#archivesocial)

[Veritas](#veritas)

[OpenText](#opentext)

[Smarsh](#smarsh)

[Verba](#verba)

### <a name="17a-4-llc"></a>17a-4 LLC

[تدعم 17a-4 LLC](https://www.17a-4.com) مصادر البيانات الخارجية التالية:

- BlackBerry

- بيانات بلومبرغ عمليات الدفق

- Cisco Jabber

- FactSet

- HipChat

- InvestEdge

- LivePerson

- بيانات MessageLabs عمليات الدفق

- OpenText

- تعليمات Live الخاصة ب Oracle/ATG

- Pivot IMTRADER

- Microsoft SharePoint

- MindAlign

- Sitrion One (Newsgator)

- Skype for Business (Lync/OCS)

- Skype for Business Online (Lync Online)

- SQL البيانات

- Squawker

- Thomson Reuters Eikon Messenger

### <a name="archivesocial"></a>ArchiveSocial

[تدعم ArchiveSocial](https://www.archivesocial.com) مصادر البيانات الخارجية التالية:

- Facebook

- Flickr

- إنستجرام

- LinkedIn

- Pinterest

- Twitter

- YouTube

- Vimeo

### <a name="veritas"></a>Veritas

[يدعم Veritas](https://www.globanet.com) مصادر بيانات الأطراف الخارجية التالية:

- AOL مع Pivot Client

- BlackBerry Call Logs (v5، v10، v12)

- BlackBerry Messenger (v5، v10، v12)

- رمز PIN BlackBerry (v5، v10، v12)

- BlackBerry SMS (v5، v10، v12)

- دردشة بلومبرغ

- بريد بلومبرغ

- المربع

- CipherCloud for Salesforce Chatter

- Cisco IM &amp; Presence Server (v10, v10.5.1 SU1, v11.0, v11.5 SU2)

- Cisco Webex Teams

- Citrix Workspace &amp; ShareFile

- CrowdCompass

- ملفات نصية مخصصة

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

- Mobile Guard

- Pivot

- Salesforce Chatter

- Skype for Business Online

- Skype for Business الإصدارات 2007 R2 - 2016 (المحلي)

- Slack Enterprise Grid

- السيمفونية

- تومسون رويتر إيكون

- تومسون رويتر ماسنجر

- Thomson Reuters Dealings 3000 / FX Trading

- Twitter

- دردشة UBS

- YouTube

### <a name="opentext"></a>OpenText

[يدعم OpenText](https://www.opentext.com/what-we-do/products/opentext-product-offerings-catalog/rebranded-products/daegis) مصادر البيانات الخارجية التالية:

- Axs Encrypted

- Axs Exchange

- Axs الأرشيف المحلي

- عنصر نائب ل Axs

- Axs Signed

- بلومبرغ

- طومسون رويتر

### <a name="smarsh"></a>Smarsh

[يدعم Smarsh](https://www.smarsh.com) مصادر بيانات الأطراف الخارجية التالية:

- AIM

- الأميركية للانوثب

- Apple الحامض

- AOL مع عميل Pivot

- Ares

- Bazaar Voice

- مشاركة الدب

- Bit Torrent

- BlackBerry Call Logs (v5، v10، v12)

- BlackBerry Messenger (v5، v10، v12)

- رمز PIN BlackBerry (v5، v10، v12)

- BlackBerry SMS (v5، v10، v12)

- بريد بلومبرغ

- CellTrust

- استيراد الدردشة

- تسجيل الدردشة في الوقت الحقيقي ونهاية

- الدردشة

- Cisco IM &amp; Presence Server (v9.0.1, v9.1, v9.1.1 SU1, v10, v10.5.1 SU1)

- Cisco Unified Presence Server (v8.6.3، v8.6.4، v8.6.5)

- استيراد التعاون

- التسجيل في الوقت الحقيقي للتعاون

- مباشرة الاتصال

- Facebook

- FactSet

- FastTrack

- Gnutella

- Google+

- GoToMyPC

- الوابسستر

- HubConnex

- IBM Connections (v3.0.1، v4.0، v4.5، v4.5 CR3، v5)

- سحابة دردشة IBM Connections

- IBM Connections Social Cloud

- IBM SameTime Advanced 8.5.2 IFR1

- IBM SameTime Communicate 9.0

- مجتمع IBM SameTime (v8.0.2، v8.5.1 IFR2، v8.5.2 IFR1، v9.1)

- IBM SameTime Complete 9.0

- مؤتمر IBM SameTime 9.0

- اجتماع IBM SameTime 8.5.2 IFR1

- ICE/YellowJacket

- استيراد المراسلة الفورية

- المراسلة الفورية في الوقت الحقيقي التسجيل ونهاية

- Indii Messenger

- Instant Bloomberg

- IRC

- Jive

- Jive 6 التسجيل في الوقت الحقيقي (v6، v7)

- استيراد Jive

- JXTA

- LinkedIn

- Microsoft Lync (2010، 2013)

- MFTP

- Microsoft Lync 2013 Voice

- Microsoft SharePoint (2010، 2013)

- Microsoft Office SharePoint Online

- Microsoft UC (Unified Communications)

- MindAlign

- Mobile Guard

- MSN

- م المساحة الخاصة بى

- NEONetwork

- Microsoft 365 Lync Dedicated

- Microsoft 365 المراسلة الفورية المشتركة

- Pinterest

- Pivot

- QQ

- Skype for Business 2015

- SoftEther

- السيمفونية

- تومسون رويتر إيكون

- تومسون رويتر ماسنجر

- Tor

- TTT

- Twitter

- WinMX

- ويني

- Yahoo

- Yammer

- YouTube


### <a name="verba"></a>Verba

[يدعم Verba](https://www.verba.com) مصادر البيانات التالية الخاصة ب جهة خارجية:

- فيديو Avaya Aura

- Avaya Aura Voice

- Avtec Radio

- Bosch/Telex Radio

- فيديو BroadSoft

- BroadSoft Voice

- صوت Centile

- Cisco Jabber IM

- فيديو Cisco UC

- Cisco UC Voice

- فيديو Cisco UCCX/UCCE

- Cisco UCCX/UCCE Voice

- ESChat Radio

- Geoman Contact Expert

- IP Trade Voice

- مركز جهات اتصال Luware LUCS

- Microsoft UC (Unified Communications)

- Mitel MiContact Center ل Lync (prairieFyre)

- فيديو وحدة التحكم في جلسة عمل Oracle / Acme

- صوت وحدة التحكم في جلسة عمل Oracle / Acme

- Singtel Mobile Voice

- SIPREC Video

-  SIPREC Voice

- Skype for Business / المراسلة الفورية في Lync

- Skype for Business / فيديو Lync

- Skype for Business / Lync Voice

- السماعات الصوتية

- فيديو SIP/H.323 القياسي

- صوت SIP/H.323 القياسي

- صوت Truphone

- TwistedPair Radio

- Windows كمبيوتر سطح المكتب

## <a name="step-2-create-and-configure-a-third-party-data-mailbox-in-microsoft-365"></a>الخطوة 2: إنشاء علبة بريد بيانات جهة خارجية وتكوينها في Microsoft 365

فيما يلي الخطوات اللازمة لإنشاء علبة بريد بيانات جهة خارجية وتكوينها لاستيراد البيانات إلى Microsoft 365. كما تم شرحه سابقا، يتم استيراد العناصر إلى علبة البريد هذه إذا كان موصل الشريك لا يمكنه تعيين اسم المستخدم الخاص بالعنصر إلى حساب مستخدم.

 **أكمل هذه المهام في مركز مسؤولي Microsoft 365**

1. إنشاء حساب مستخدم وتعيينه Exchange Online الخطة 2؛ راجع إضافة مستخدمين [إلى](../admin/add-users/add-users.md) Microsoft 365. يجب الحصول على ترخيص الخطة 2 لكي يتم وضع علبة البريد في وضع الاحتجاز بسبب الدعاوى القضائية أو تمكين علبة بريد الأرشيف التي لها حصة تخزينية تصل إلى 1.5 تيراف.

2. أضف حساب المستخدم لعلبة بريد بيانات جهة خارجية إلى دور مسؤول Exchange  في Microsoft 365؛ راجع تعيين [أدوار المسؤولين في Microsoft 365](../admin/add-users/assign-admin-roles.md).

    > [!TIP]
    > اكتب بيانات الاعتماد لحساب المستخدم هذا. تحتاج إلى توفيرها لشريكك، كما هو موضح في الخطوة 4.

 **إكمال هذه المهام في مركز إدارة Exchange**

1. إخفاء علبة بريد البيانات الخاصة ب جهة خارجية من دفتر العنوان وقوائم العنوان الأخرى في مؤسستك؛ راجع [إدارة علب بريد المستخدمين](/exchange/recipients-in-exchange-online/manage-user-mailboxes/manage-user-mailboxes). بدلا من ذلك، يمكنك تشغيل الأمر PowerShell التالي:

    ```powershell
    Set-Mailbox -Identity <identity of third-party data mailbox> -HiddenFromAddressListsEnabled $true
    ```

2. قم بتعيين إذن **FullAccess** إلى علبة بريد بيانات الجهات الخارجية بحيث يمكن للمسؤولين أو مسؤولي التوافق فتح علبة بريد البيانات الخاصة بالجهات الخارجية في عميل سطح مكتب Outlook؛ راجع إدارة الأذونات [للمستلمين](https://go.microsoft.com/fwlink/p/?LinkId=692104).

3. تمكين الميزات التالية ذات الصلة بالتوافق لعلبة بريد بيانات جهة خارجية:

    - تمكين علبة بريد الأرشيف؛ راجع [تمكين علب بريد الأرشيف](enable-archive-mailboxes.md) [وتمكين أرشفة التوسع التلقائي](enable-autoexpanding-archiving.md). يتيح لك ذلك تحرير مساحة تخزين في علبة البريد الأساسية من خلال إعداد نهج أرشفة ينقل عناصر بيانات جهة خارجية إلى علبة بريد الأرشيف. يوفر لك ذلك مساحة تخزين تصل إلى 1.5 تي TB لبيانات  الأطراف الخارجية.

    - ضع علبة بريد البيانات الخاصة ب جهة خارجية في الاحتجاز بسبب الدعاوى القضائية. يمكنك أيضا تطبيق نهج استبقاء Microsoft 365 في مركز الأمان والتوافق. ويحتفظ وضع علبة البريد هذه قيد الانتظار بالعناصر الخاصة بالبيانات الخاصة بجهة خارجية (لمدة غير محددة أو لمدة محددة) ويمنع إبقائها من علبة البريد. راجع أحد المواضيع التالية:

      - [وضع علبة بريد في الاحتجاز بسبب الدعاوى القضائية](./create-a-litigation-hold.md)

      - [التعرف على سياسات الاستبقاء وتسميات الاستبقاء](retention.md)

    - تمكين تسجيل تدقيق علبة البريد لمالك علبة البريد ومفوضها ومسؤولها للوصول إلى علبة بريد بيانات جهة خارجية؛ راجع [تمكين تدقيق علبة البريد](enable-mailbox-auditing.md). يسمح لك ذلك بتدقيق كل النشاط الذي يقوم به أي مستخدم لديه حق الوصول إلى علبة بريد بيانات جهة خارجية.

## <a name="step-3-configure-user-mailboxes-for-third-party-data"></a>الخطوة 3: تكوين علب بريد المستخدمين لبيانات كيانات خارجية

الخطوة التالية هي تكوين علب بريد المستخدمين لدعم بيانات  الأطراف الخارجية. أكمل هذه المهام باستخدام Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">الإدارة أو</a> باستخدام Windows PowerShell cmdlets المطابقة.

1. تمكين علبة بريد الأرشيف لكل مستخدم؛ راجع [تمكين علب بريد الأرشيف](enable-archive-mailboxes.md) [وتمكين أرشفة التوسع التلقائي](enable-autoexpanding-archiving.md).

2. ضع علب بريد المستخدمين في الاحتجاز بسبب الدعاوى القضائية أو طبق Microsoft 365 استبقاء؛ راجع أحد المواضيع التالية:

    - [وضع علبة بريد في الاحتجاز بسبب الدعاوى القضائية](./create-a-litigation-hold.md)

    - [التعرف على سياسات الاستبقاء وتسميات الاستبقاء](retention.md)

    كما ذكر سابقا، عند وضع علب البريد في وضع الانتظار، يمكنك تعيين مدة لطول مدة الاحتفاظ بالعناصر من مصدر بيانات جهة خارجية أو يمكنك اختيار الاحتفاظ بالعناصر إلى أجل غير مسمى.

## <a name="step-4-provide-your-partner-with-information"></a>الخطوة 4: تزويد شريكك بالمعلومات

الخطوة الأخيرة هي تزويد شريكك بالمعلومات التالية ليمكنه تكوين الموصل للاتصال بالمنظمة لاستيراد البيانات إلى علب بريد المستخدمين و لعلبة بريد البيانات الخاصة ب جهة خارجية.

- نقطة النهاية المستخدمة للاتصال بالخدمة Azure في Microsoft 365:

    ```http
    https://office365ingestionsvc.gble1.protection.outlook.com/service/ThirdPartyIngestionService.svc
    ```

- بيانات اعتماد تسجيل الدخول (Microsoft 365 المستخدم وكلمة المرور) لعلبة بريد البيانات التي أنشأتها في الخطوة 2. بيانات الاعتماد هذه مطلوبة حتى يمكن لموصل الشريك الوصول إلى العناصر واستيرادها إلى علب بريد المستخدمين ونهاية علبة بريد البيانات الخاصة ب جهة خارجية.

## <a name="step-5-register-the-third-party-data-connector-in-azure-active-directory"></a>الخطوة 5: تسجيل موصل بيانات جهة خارجية في Azure Active Directory

بدءا من 30 سبتمبر 2018، ستبدأ خدمة Azure في Microsoft 365 باستخدام المصادقة الحديثة في Exchange Online لمصادقة موصلات بيانات جهة خارجية تحاول الاتصال بمنظمتك لاستيراد البيانات. والسبب في هذا التغيير هو أن المصادقة الحديثة توفر المزيد من الأمان مقارنة بالطريقة الحالية، التي كانت تستند إلى قائمة السماح للموصلات الخارجية التي تستخدم نقطة النهاية الموضحة مسبقا للاتصال بالخدمة Azure.

لتمكين موصل بيانات جهة خارجية من الاتصال Microsoft 365 باستخدام أسلوب المصادقة الحديثة الجديد، يجب أن يوافق المسؤول في مؤسستك على تسجيل الموصل ك تطبيق خدمة موثوق به في Azure Active Directory. يتم ذلك من خلال قبول طلب إذن للسماح للموصل بالوصول إلى بيانات مؤسستك في Azure Active Directory. بعد قبول هذا الطلب، يضاف موصل بيانات جهة خارجية كتطبيق مؤسسة إلى Azure Active Directory ويمثله كخدمة رئيسية. لمزيد من المعلومات حول عملية الموافقة، راجع  [موافقة مسؤول المستأجر](/skype-sdk/trusted-application-api/docs/tenantadminconsent).

فيما يلي الخطوات اللازمة للوصول إلى الطلب وقبوله لتسجيل الموصل:

1. انتقل إلى [هذه الصفحة،](https://login.microsoftonline.com/common/oauth2/authorize?client_id=8dfbc50b-2111-4d03-9b4d-dd0d00aae7a2&response_type=code&redirect_uri=https://portal.azure.com/&nonce=1234&prompt=admin_consent) ثم سجل الدخول باستخدام بيانات اعتماد المسؤول العام.

   يتم عرض مربع الحوار التالي. يمكنك توسيع الإقراب لمراجعة الأذونات التي سيتم تعيينها للموصل.

   ![يتم عرض مربع الحوار طلب الأذونات.](../media/O365-ThirdPartyDataConnector-OptIn1.png)

2. انقر **فوق قبول**.

بعد قبول الطلب، يتم عرض مدخل [Azure](https://portal.azure.com) . لعرض قائمة التطبيقات لمنظمتك، انقر فوق **تطبيقات Azure Active DirectoryEnterprise** > . يتم Microsoft 365 موصل بيانات جهة خارجية على شفرة **تطبيقات** Enterprise.

> [!IMPORTANT]
> بعد 30 سبتمبر 2018، لن يتم استيراد بيانات كيانات خارجية إلى علب البريد في مؤسستك إذا لم تسجل موصل بيانات جهة خارجية في Azure Active Directory. تجدر الإشارة إلى أنه يجب أيضا تسجيل موصلات البيانات الموجودة من جهة خارجية (تلك التي تم إنشاؤها قبل 30 سبتمبر 2018) في Azure Active Directory باتباع الإجراء في الخطوة 5.

### <a name="revoking-consent-for-a-third-party-data-connector"></a>إبطال الموافقة على موصل بيانات جهة خارجية

بعد موافقة مؤسستك على طلب الأذونات لتسجيل موصل بيانات جهة خارجية في Azure Active Directory، يمكن لمنظمتك إبطال هذه الموافقة في أي وقت. ومع ذلك، فإن إبطال الموافقة على موصل يعني أنه لن يتم استيراد البيانات من مصدر بيانات جهة خارجية إلى Microsoft 365.

لإبطال الموافقة على موصل بيانات جهة خارجية، يمكنك حذف التطبيق (عن طريق حذف الخدمة الأساسية المطابقة) من Azure Active Directory باستخدام شفرة تطبيقات **Enterprise** في مدخل Azure، أو باستخدام [Remove-MsolServicePrincipal](/powershell/module/msonline/remove-msolserviceprincipal) في Microsoft 365 PowerShell. يمكنك أيضا استخدام [الأمر cmdlet Remove-AzureADServicePrincipal](/powershell/module/azuread/remove-azureadserviceprincipal) في Azure Active Directory PowerShell.

## <a name="more-information"></a>معلومات إضافية

- كما تم شرحه سابقا، يتم استيراد عناصر من مصادر بيانات جهة خارجية Exchange علب البريد كرسائل بريد إلكتروني. يستورد موصل الشريك العنصر باستخدام مخطط مطلوب بواسطة Microsoft 365 API. يصف الجدول التالي خصائص الرسالة الخاصة بعنصر من مصدر بيانات جهة خارجية بعد استيراده إلى علبة بريد Exchange كرسالة بريد إلكتروني. يشير الجدول أيضا إلى ما إذا كانت خاصية الرسالة إلزامية. يجب ملء الخصائص الإلزامية. إذا كان أحد العناصر مفقودا خاصية إلزامية، فلن يتم استيراده إلى Microsoft 365. ترجع عملية الاستيراد رسالة خطأ توضح سبب عدم استيراد عنصر ما والممتلكات المفقودة.<br/><br/>

    |**الخاصية "رسالة"**|**هل هو إلزامي؟**|**الوصف**|**قيمة المثال**|
    |:-----|:-----|:-----|:-----|
    |**FROM** <br/> |نعم  <br/> |المستخدم الذي أنشأ العنصر في الأصل أو أرسله في مصدر بيانات جهة خارجية. يحاول موصل الشريك تعيين "تعريف المستخدم" من العنصر المصدر (على سبيل المثال مقبض Twitter) إلى حساب مستخدم لكل المشاركين (المستخدمون في الحقلين FROM و TO). سيتم استيراد نسخة من الرسالة إلى علبة بريد كل مشارك. إذا لم يكن من الممكن تعيين أي من المشاركين من العنصر إلى حساب مستخدم، سيتم استيراد العنصر إلى علبة بريد الأرشفة الخارجية في Microsoft 365.  <br/> <br/> يجب أن يكون لدى المشارك الذي تم تعريفه كمرسل العنصر علبة بريد نشطة في المؤسسة التي يتم استيراد العنصر لها. إذا لم يكن المرسل لديه علبة بريد نشطة، يتم إرجاع الخطأ التالي:<br/><br/>  `One or more messages in the Request failed to be delivered to either From or Sender email address. You will need to resend your entire Request. Error: The request failed. The remote server returned an error: (401) Unauthorized.`  | `bob@contoso.com` <br/> |
    |**TO** <br/> |نعم  <br/> |المستخدم الذي استلم أحد العناصر، إذا كان ذلك قابلا للتطبيق على عنصر في مصدر البيانات.  <br/> | `bob@contoso.com` <br/> |
    |**SUBJECT** <br/> |لا  <br/> |الموضوع من العنصر المصدر.  <br/> | `"Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/> |
    |**DATE** <br/> |نعم  <br/> |تاريخ إنشاء العنصر أو نشره في الأصل في مصدر بيانات العميل. على سبيل المثال، هذا التاريخ الذي تم فيه تغريد رسالة Twitter.  <br/> | `01 NOV 2015` <br/> |
    |**BODY** <br/> |لا  <br/> |محتويات الرسالة أو المنشور. بالنسبة لبعض مصادر البيانات، قد تكون محتويات هذه الخاصية هي نفسها محتوى الخاصية **SUBJECT** . أثناء عملية الاستيراد، يحاول موصل الشريك الحفاظ على الجودة الكاملة من مصدر المحتوى قدر الإمكان. إذا أمكن تضمين الملفات أو الرسومات أو المحتوى الآخر من جزء العنصر المصدر في هذه الخاصية. وبخلاف ذلك، يتم تضمين المحتوى من العنصر المصدر في **الخاصية المرفق** . تعتمد محتويات هذه الخاصية على موصل الشريك وعلى قدرة النظام الأساسي المصدر.  <br/> | `Author: bob@contoso.com` <br/>  `Date: 10 DEC 2014` <br/>  `Tweet: "Mega deals with Contoso coming your way! #ContosoHolidayDeals"` <br/>  `Date: 01 NOV 2015` <br/> |
    |**المرفق** <br/> |لا  <br/> |إذا كان هناك عنصر في مصدر البيانات (مثل تغريدة في Twitter أو محادثة مراسلة فورية) يحتوي على ملف مرفق أو يتضمن صورا، فإن اتصال الشريك سيحاول أولا تضمين المرفقات في الخاصية **BODY** . إذا لم يكن ذلك ممكنا، فإنه يضاف إلى الخاصية ** المرفق ** . تتضمن الأمثلة الأخرى للمرفقات "أعجبات" في Facebook، و"بيانات التعريف" من مصدر المحتوى، والاستجابات لرسالة أو منشور.  <br/> | `image.gif` <br/> |
    |**MESSAGECLASS** <br/> |نعم  <br/> | هذه خاصية متعددة القيم، يتم إنشاؤها و ملؤها بواسطة موصل الشريك. تنسيق هذه الخاصية هو  `IPM.NOTE.Source.Event`. (يجب أن تبدأ هذه الخاصية ب  `IPM.NOTE`. يشبه هذا التنسيق  `IPM.NOTE.X` التنسيق لفئة الرسالة.) تتضمن هذه الخاصية المعلومات التالية:  <br/><br/>`Source`: يشير إلى مصدر بيانات جهة خارجية؛ على سبيل المثال، Twitter أو Facebook أو BlackBerry.  <br/> <br/>  `Event`: يشير إلى نوع النشاط الذي تم إجراءه في مصدر بيانات جهة خارجية الذي أنتج العناصر؛ على سبيل المثال، تغريدة في Twitter أو منشور في Facebook. الأحداث خاصة كمصدر البيانات.  <br/> <br/>  أحد أغراض هذه الخاصية هو تصفية عناصر معينة استنادا إلى مصدر البيانات حيث تم إنشاء عنصر أو استنادا إلى نوع الحدث. على سبيل المثال، في عملية بحث eDiscovery، يمكنك إنشاء استعلام بحث للعثور على كل التغريدات التي تم نشرها بواسطة مستخدم معين.  <br/> | `IPM.NOTE.Twitter.Tweet` <br/> |

- عند استيراد العناصر بنجاح إلى علب البريد في Microsoft 365، يتم إرجاع معرف فريد مرة أخرى إلى المتصل كجزء من استجابة HTTP. يمكن استخدام هذا  `x-IngestionCorrelationID`المعرف، المسمى ، لأغراض استكشاف الأخطاء وإصلاحها اللاحقة من قبل الشركاء لتعقب العناصر من النهاية إلى النهاية. من المستحسن أن يلتقط الشركاء هذه المعلومات ويسجلونها وفقا لذلك من نهايتهم. فيما يلي مثال على استجابة HTTP تظهر هذا المعرف:

    ```http
    HTTP/1.1 200 OK
    Content-Type: text/xml; charset=utf-8
    Server: Microsoft-IIS/8.5
    x-IngestionCorrelationID: 1ec7667d-f097-47fe-a9a2-bc7ab0a7552b
    X-AspNet-Version: 4.0.30319
    X-Powered-By: ASP.NET
    Date: Tue, 02 Feb 2016 22:55:33 GMT
    ```

- يمكنك استخدام أداة البحث في المحتوى في مركز الأمان والتوافق للبحث عن العناصر التي تم استيرادها إلى علب البريد من مصدر بيانات جهة خارجية. للبحث بشكل خاص عن هذه العناصر المستوردة، يمكنك استخدام أزواج قيم خاصية الرسالة التالية في مربع الكلمة الأساسية للبحث في المحتوى.

  - **`kind:externaldata`**: استخدم زوج قيمة الخاصية هذا للبحث في كل أنواع بيانات  الأطراف الخارجية. على سبيل المثال، للبحث عن العناصر التي تم استيرادها من مصدر بيانات جهة خارجية وكانت تحتوي على الكلمة "contoso" في الخاصية Subject الخاصة بالعنصر المستورد، يمكنك استخدام استعلام الكلمة الأساسية  `kind:externaldata AND subject:contoso`.

  - **`itemclass:ipm.externaldata.<third-party data type>`**: استخدم زوج قيمة الخاصية هذا للبحث فقط عن نوع معين من بيانات  الجهة الخارجية. على سبيل المثال، للبحث في بيانات Facebook التي تحتوي على الكلمة "contoso" فقط في خاصية الموضوع، يمكنك استخدام استعلام الكلمة الأساسية  `itemclass:ipm.externaldata.Facebook* AND subject:contoso`.

  للحصول على قائمة كاملة بالقيم `itemclass` التي يجب استخدامها لأنواع بيانات الأطراف الخارجية للممتلكات، راجع استخدام البحث في المحتوى للبحث عن بيانات جهة خارجية تم استيرادها إلى [Microsoft 365.](use-content-search-to-search-third-party-data-that-was-imported.md)

   لمزيد من المعلومات حول استخدام البحث في المحتوى وإنشاء استعلامات البحث عن الكلمات الأساسية، راجع:

  - [البحث في المحتوى](content-search.md)

  - [استعلامات الكلمات الأساسية وشروط البحث في البحث في المحتوى](keyword-queries-and-search-conditions.md)