---
title: البحث عن التهديدات عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات باستخدام التتبع المتقدم
description: دراسة سيناريوهات التتبع الشائعة ونماذج الاستعلامات التي تغطي الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات.
keywords: التتبع المتقدم وبيانات Office365 وأجهزة Windows وتطبيع رسائل البريد الإلكتروني في Office365 ورسائل البريد الإلكتروني والتطبيقات والهويات وتتبع التهديدات والبحث والاستعلام وبيانات تتبع الاستخدام Microsoft 365 Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 099ba7abe53be6269c1d01c0d39d9e5cfbe3557d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731681"
---
# <a name="hunt-for-threats-across-devices-emails-apps-and-identities"></a>البحث عن التهديدات عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يسمح لك [التتبع المتقدم](advanced-hunting-overview.md) في Microsoft 365 Defender بالبحث الاستباقي عن التهديدات عبر:
- الأجهزة التي تديرها Microsoft Defender لنقطة النهاية
- رسائل البريد الإلكتروني التي تمت معالجتها بواسطة Microsoft 365
- أنشطة تطبيق السحابة وأحداث المصادقة وأنشطة وحدة التحكم بالمجال المتعقبة بواسطة Microsoft Defender for Cloud Apps Microsoft Defender for Identity

مع هذا المستوى من الرؤية، يمكنك البحث بسرعة عن التهديدات التي تجتاز أقسام الشبكة، بما في ذلك عمليات الاختراق المتطورة التي تصل إلى البريد الإلكتروني أو الويب، ورفع الامتيازات المحلية، والحصول على بيانات اعتماد المجال المتميزة، والانتقال لاحقا إلى عبر أجهزتك. 

فيما يلي تقنيات عامة ونماذج استعلامات تستند إلى سيناريوهات التتبع المختلفة التي يمكن أن تساعدك على استكشاف كيفية إنشاء الاستعلامات عند البحث عن مثل هذه التهديدات المتطورة.

## <a name="get-entity-info"></a>الحصول على معلومات الكيان
استخدم هذه الاستعلامات للتعرف على كيفية الحصول بسرعة على معلومات حول حسابات المستخدمين والأجهزة والملفات. 

### <a name="obtain-user-accounts-from-email-addresses"></a>الحصول على حسابات المستخدمين من عناوين البريد الإلكتروني
عند إنشاء استعلامات عبر [الجداول التي تغطي الأجهزة ورسائل البريد الإلكتروني](advanced-hunting-schema-tables.md)، ستحتاج على الأرجح إلى الحصول على أسماء حسابات المستخدمين من عناوين البريد الإلكتروني للمرسل أو المستلم. يمكنك القيام بذلك بشكل عام إما للمستلم أو عنوان المرسل باستخدام *المضيف المحلي* من عنوان البريد الإلكتروني.

في القصاصة البرمجية أدناه، نستخدم [الدالة tostring()](/azure/data-explorer/kusto/query/tostringfunction) Kusto لاستخراج المضيف المحلي مباشرة قبل `@` عناوين البريد الإلكتروني للمستلم في العمود `RecipientEmailAddress`.

```kusto
//Query snippet showing how to extract the account name from an email address
AccountName = tostring(split(RecipientEmailAddress, "@")[0])
```
يوضح الاستعلام أدناه كيفية استخدام هذه القصاصة البرمجية:

```kusto
EmailEvents
| where Timestamp > ago(7d)
| project RecipientEmailAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
```

### <a name="merge-the-identityinfo-table"></a>دمج جدول IdentityInfo

يمكنك الحصول على أسماء الحسابات ومعلومات الحساب الأخرى عن طريق دمج [جدول IdentityInfo](advanced-hunting-identityinfo-table.md) أو الانضمام إليه. يحصل الاستعلام أدناه على قائمة عمليات الكشف عن التصيد الاحتيالي والبرامج الضارة من [جدول EmailEvents](advanced-hunting-emailevents-table.md) ثم يربط هذه المعلومات بالجدول `IdentityInfo` للحصول على معلومات مفصلة حول كل مستلم. 

```kusto
EmailEvents
| where Timestamp > ago(7d)
//Get email processing events where the messages were identified as either phishing or malware
| where ThreatTypes has "Malware" or ThreatTypes has "Phish"
//Merge email events with identity info to get recipient details
| join (IdentityInfo | distinct AccountUpn, AccountDisplayName, JobTitle, 
Department, City, Country) on $left.RecipientEmailAddress == $right.AccountUpn 
//Show important message and recipient details
| project Timestamp, NetworkMessageId, Subject, ThreatTypes, 
SenderFromAddress, RecipientEmailAddress, AccountDisplayName, JobTitle, 
Department, City, Country
```

### <a name="get-device-information"></a>الحصول على معلومات الجهاز
يوفر [مخطط التتبع المتقدم](advanced-hunting-schema-tables.md) معلومات واسعة عن الجهاز في جداول مختلفة. على سبيل المثال، يوفر [جدول DeviceInfo](advanced-hunting-deviceinfo-table.md) معلومات شاملة عن الجهاز استنادا إلى بيانات الأحداث المجمعة بانتظام. يستخدم `DeviceInfo` هذا الاستعلام الجدول للتحقق مما إذا كان المستخدم (`<account-name>`) الذي يحتمل أن يكون قد قام بتسجيل الدخول إلى أي أجهزة ثم يسرد التنبيهات التي تم تشغيلها على تلك الأجهزة.

>[!Tip]
> يستخدم `kind=inner` هذا الاستعلام لتحديد [صلة داخلية](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor)، مما يمنع إلغاء تكرار قيم الجانب الأيسر ل `DeviceId`.

```kusto
DeviceInfo
//Query for devices that the potentially compromised account has logged onto
| where LoggedOnUsers contains '<account-name>'
| distinct DeviceId
//Crosscheck devices against alert records in AlertEvidence and AlertInfo tables
| join kind=inner AlertEvidence on DeviceId
| project AlertId
//List all alerts on devices that user has logged on to
| join AlertInfo on AlertId
| project AlertId, Timestamp, Title, Severity, Category 
```


### <a name="get-file-event-information"></a>الحصول على معلومات حدث الملف

استخدم الاستعلام التالي للحصول على معلومات حول الأحداث ذات الصلة بالملف. 

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceFileEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="get-network-event-information"></a>الحصول على معلومات أحداث الشبكة

استخدم الاستعلام التالي للحصول على معلومات حول الأحداث المتعلقة بالشبكة.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-agent-version-information"></a>الحصول على معلومات إصدار عامل الجهاز

استخدم الاستعلام التالي للحصول على إصدار العامل قيد التشغيل على جهاز.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where ClientVersion startswith "20.1"
| summarize by DeviceId
| join kind=inner (
    DeviceNetworkEvents 
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


### <a name="example-query-for-macos-devices"></a>استعلام مثال لأجهزة macOS

استخدم استعلام المثال التالي لمشاهدة جميع الأجهزة التي تعمل بنظام التشغيل macOS مع إصدار أقدم من Catalina.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OSPlatform == "macOS" and  OSVersion !contains "10.15" and OSVersion !contains "11."
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```

### <a name="get-device-status-info"></a>الحصول على معلومات حالة الجهاز

استخدم الاستعلام التالي للحصول على حالة جهاز. في المثال التالي، يتحقق الاستعلام لمعرفة ما إذا كان الجهاز قد تم إلحاقه.

```kusto
DeviceInfo
| where Timestamp > ago(1d)
| where OnboardingStatus != "Onboarded"
| summarize by DeviceId
| join kind=inner (
    DeviceInfo
    | where Timestamp > ago(1d)
) on DeviceId
| take 10
```


## <a name="hunting-scenarios"></a>سيناريوهات التتبع

### <a name="list-logon-activities-of-users-that-received-emails-that-were-not-zapped-successfully"></a>سرد أنشطة تسجيل الدخول للمستخدمين الذين تلقوا رسائل بريد إلكتروني لم يتم تجاوزها بنجاح
تعالج [عملية الإزالة التلقائية بدون ساعة (ZAP)](../office-365-security/zero-hour-auto-purge.md) رسائل البريد الإلكتروني الضارة بعد تلقيها. إذا فشل ZAP، فقد يتم تشغيل التعليمات البرمجية الضارة في النهاية على الجهاز وترك الحسابات معرضة للخطر. يتحقق هذا الاستعلام من نشاط تسجيل الدخول الذي قام به مستلمو رسائل البريد الإلكتروني التي لم تتم معالجتها بنجاح بواسطة ZAP.

```kusto
EmailPostDeliveryEvents 
| where Timestamp > ago(7d)
//List malicious emails that were not zapped successfully
| where ActionType has "ZAP" and ActionResult == "Error"
| project ZapTime = Timestamp, ActionType, NetworkMessageId , RecipientEmailAddress 
//Get logon activity of recipients using RecipientEmailAddress and AccountUpn
| join kind=inner IdentityLogonEvents on $left.RecipientEmailAddress == $right.AccountUpn
| where Timestamp between ((ZapTime-24h) .. (ZapTime+24h))
//Show only pertinent info, such as account name, the app or service, protocol, the target device, and type of logon
| project ZapTime, ActionType, NetworkMessageId , RecipientEmailAddress, AccountUpn, 
LogonTime = Timestamp, AccountDisplayName, Application, Protocol, DeviceName, LogonType
```

### <a name="get-logon-attempts-by-domain-accounts-targeted-by-credential-theft"></a>الحصول على محاولات تسجيل الدخول من قبل حسابات المجال المستهدفة بسرقة بيانات الاعتماد
يحدد هذا الاستعلام أولا كافة تنبيهات الوصول إلى بيانات الاعتماد في `AlertInfo` الجدول. ثم يقوم بدمج الجدول أو ضمه `AlertEvidence` ، الذي يقوم بفرزه لأسماء الحسابات المستهدفة وعوامل التصفية للحسابات المرتبطة بالمجال فقط. وأخيرا، فإنه يتحقق من `IdentityLogonEvents` الجدول للحصول على جميع أنشطة تسجيل الدخول من قبل الحسابات المستهدفة المرتبطة بالمجال.

```kusto
AlertInfo
| where Timestamp > ago(30d)
//Get all credential access alerts
| where Category == "CredentialAccess"
//Get more info from AlertEvidence table to get the SID of the target accounts
| join AlertEvidence on AlertId
| extend IsJoined=(parse_json(AdditionalFields).Account.IsDomainJoined)
| extend TargetAccountSid=tostring(parse_json(AdditionalFields).Account.Sid)
//Filter for domain-joined accounts only
| where IsJoined has "true"
//Merge with IdentityLogonEvents to get all logon attempts by the potentially compromised target accounts
| join kind=inner IdentityLogonEvents on $left.TargetAccountSid == $right.AccountSid
//Show only pertinent info, such as account name, the app or service, protocol, the accessed device, and type of logon
| project AccountDisplayName, TargetAccountSid, Application, Protocol, DeviceName, LogonType
```

### <a name="check-if-files-from-a-known-malicious-sender-are-on-your-devices"></a>التحقق مما إذا كانت الملفات من مرسل ضار معروف موجودة على أجهزتك
بافتراض أنك تعرف عنوان بريد إلكتروني يرسل ملفات ضارة (`MaliciousSender@example.com`)، يمكنك تشغيل هذا الاستعلام لتحديد ما إذا كانت الملفات من هذا المرسل موجودة على أجهزتك. يمكنك استخدام هذا الاستعلام، على سبيل المثال، لتحديد الأجهزة المتأثرة بحملة توزيع البرامج الضارة.

```kusto
EmailAttachmentInfo
| where SenderFromAddress =~ "MaliciousSender@example.com"
//Get emails with attachments identified by a SHA-256
| where isnotempty(SHA256)
| join (
//Check devices for any activity involving the attachments
DeviceFileEvents
| project FileName, SHA256, DeviceName, DeviceId
) on SHA256
| project Timestamp, FileName , SHA256, DeviceName, DeviceId,  NetworkMessageId, SenderFromAddress, RecipientEmailAddress
```

### <a name="review-logon-attempts-after-receipt-of-malicious-emails"></a>مراجعة محاولات تسجيل الدخول بعد تلقي رسائل بريد إلكتروني ضارة
يبحث هذا الاستعلام عن آخر 10 عمليات تسجيل دخول تم إجراؤها بواسطة مستلمي البريد الإلكتروني في غضون 30 دقيقة بعد تلقيهم رسائل بريد إلكتروني ضارة معروفة. يمكنك استخدام هذا الاستعلام للتحقق مما إذا تم اختراق حسابات مستلمي البريد الإلكتروني.

```kusto
//Define new table for malicious emails
let MaliciousEmails=EmailEvents
//List emails detected as malware, getting only pertinent columns
| where ThreatTypes has "Malware" 
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
MaliciousEmails
| join (
//Merge malicious emails with logon events to find logons by recipients
IdentityLogonEvents
| project LogonTime = Timestamp, AccountName, DeviceName
) on AccountName 
//Check only logons within 30 minutes of receipt of an email
| where (LogonTime - TimeEmail) between (0min.. 30min)
| take 10
```

### <a name="review-powershell-activities-after-receipt-of-emails-from-known-malicious-sender"></a>مراجعة أنشطة PowerShell بعد تلقي رسائل البريد الإلكتروني من مرسل ضار معروف
غالبا ما تحتوي رسائل البريد الإلكتروني الضارة على مستندات ومرفقات أخرى مصممة خصيصا لتشغيل أوامر PowerShell لتسليم حمولات إضافية. إذا كنت على علم برسائل البريد الإلكتروني الواردة من مرسل ضار معروف (`MaliciousSender@example.com`)، يمكنك استخدام هذا الاستعلام لإدراج أنشطة PowerShell التي حدثت في غضون 30 دقيقة بعد تلقي رسالة بريد إلكتروني من المرسل ومراجعتها.  

```kusto
//Define new table for emails from specific sender
let EmailsFromBadSender=EmailEvents
| where SenderFromAddress =~ "MaliciousSender@example.com"
| project TimeEmail = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0]);
//Merge emails from sender with process-related events on devices
EmailsFromBadSender
| join (
DeviceProcessEvents
//Look for PowerShell activity
| where FileName =~ "powershell.exe"
//Add line below to check only events initiated by Outlook
//| where InitiatingProcessParentFileName =~ "outlook.exe"
| project TimeProc = Timestamp, AccountName, DeviceName, InitiatingProcessParentFileName, InitiatingProcessFileName, FileName, ProcessCommandLine
) on AccountName 
//Check only PowerShell activities within 30 minutes of receipt of an email
| where (TimeProc - TimeEmail) between (0min.. 30min)
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
