---
title: أفضل ممارسات استعلام التتبع المتقدمة في Microsoft 365 Defender
description: تعرف على كيفية إنشاء استعلامات سريعة وفعالة وخالية من الأخطاء بحثا عن التهديدات باستخدام التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، المخطط، kusto، تجنب المهلة، خطوط الأوامر، معرف العملية، التحسين، أفضل الممارسات، التحليل، الانضمام، التلخيص
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: c4236edcb2b5ec15b7c66be8f4b74ad0a2bc44c7
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603451"
---
# <a name="advanced-hunting-query-best-practices"></a>أفضل ممارسات استعلام التتبع المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

طبق هذه التوصيات للحصول على النتائج بشكل أسرع وتجنب المهلات أثناء تشغيل الاستعلامات المعقدة. لمزيد من الإرشادات حول تحسين أداء الاستعلام، اقرأ [أفضل ممارسات استعلام Kusto](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>فهم الحصص النسبية لمورد CPU
اعتمادا على حجمه، يمكن لكل مستأجر الوصول إلى كمية معينة من موارد وحدة المعالجة المركزية المخصصة لتشغيل استعلامات التتبع المتقدمة. للحصول على معلومات مفصلة حول معلمات الاستخدام المختلفة، [اقرأ حول الحصص النسبية المتقدمة للتتبع ومعلمات الاستخدام](advanced-hunting-limits.md).

بعد تشغيل الاستعلام، يمكنك مشاهدة وقت التنفيذ واستخدام الموارد الخاصة به (منخفض، متوسط، عال). يشير High إلى أن الاستعلام استغرق المزيد من الموارد للتشغيل ويمكن تحسينه لإرجاع النتائج بشكل أكثر كفاءة.

:::image type="content" source="../../media/resource-usage.png" alt-text="تفاصيل الاستعلام ضمن علامة التبويب **Results** في مدخل Microsoft 365 Defender" lightbox="../../media/resource-usage.png":::

يجب على العملاء الذين يقومون بتشغيل استعلامات متعددة بانتظام تعقب الاستهلاك وتطبيق إرشادات التحسين في هذه المقالة لتقليل التعطيل الناتج عن تجاوز الحصص النسبية أو معلمات الاستخدام.

شاهد [تحسين استعلامات KQL](https://www.youtube.com/watch?v=ceYvRuPp5D8) للاطلاع على بعض الطرق الأكثر شيوعا لتحسين استعلاماتك.  

## <a name="general-optimization-tips"></a>تلميحات التحسين العامة

- **تحجيم الاستعلامات الجديدة** — إذا كنت تشك في أن الاستعلام سيرجع مجموعة نتائج كبيرة، فقم بتقييمه أولا باستخدام [عامل تشغيل العد](/azure/data-explorer/kusto/query/countoperator). استخدم [الحد](/azure/data-explorer/kusto/query/limitoperator) أو المرادف `take` لتجنب مجموعات النتائج الكبيرة.
- **تطبيق عوامل التصفية في وقت مبكر** — تطبيق عوامل تصفية الوقت وعوامل التصفية الأخرى لتقليل مجموعة البيانات، خاصة قبل استخدام دالات التحويل وتحليلها، مثل [substring()](/azure/data-explorer/kusto/query/substringfunction)، [أو replace()](/azure/data-explorer/kusto/query/replacefunction)، [أو trim()](/azure/data-explorer/kusto/query/trimfunction)، أو [toupper()](/azure/data-explorer/kusto/query/toupperfunction)، أو [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). في المثال أدناه، يتم استخدام دالة التوزيع [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) بعد أن خفضت عوامل تشغيل التصفية عدد السجلات.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **يحتوي على دقات —** لتجنب البحث في الstrings الفرعية داخل الكلمات دون داع، استخدم `has` عامل التشغيل بدلا من `contains`. [التعرف على عوامل تشغيل السلسلة](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **ابحث في أعمدة معينة** — ابحث في عمود معين بدلا من تشغيل عمليات البحث في النص الكامل عبر كل الأعمدة. لا تستخدم `*` للتحقق من كافة الأعمدة.
- **حساس لحالة الأحرف للسرعة** - عمليات البحث الحساسة لحالة الأحرف أكثر تحديدا وأكثر أداء بشكل عام. أسماء [عوامل تشغيل السلسلة](/azure/data-explorer/kusto/query/datatypes-string-operators) الحساسة لحالة الأحرف، مثل `has_cs` و `contains_cs`، تنتهي بشكل عام ب `_cs`. يمكنك أيضا استخدام عامل تشغيل `==` يساوي حساس لحالة الأحرف بدلا من `=~`.
- **تحليل، لا تستخرج**— كلما أمكن، استخدم [عامل التشغيل الموزع](/azure/data-explorer/kusto/query/parseoperator) أو دالة تحليل مثل [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). تجنب عامل تشغيل السلسلة `matches regex` أو [الدالة extract()](/azure/data-explorer/kusto/query/extractfunction) وكلاهما يستخدم تعبيرا عاديا. احتفظ باستخدام التعبير العادي لسيناريوهات أكثر تعقيدا. [اقرأ المزيد حول تحليل الدالات](#parse-strings)
- **تصفية الجداول وليس التعبيرات**— لا تقم بالتصفية على عمود محسوب إذا كان بإمكانك التصفية على عمود جدول.
- **لا توجد مصطلحات مكونة من ثلاثة أحرف**— تجنب المقارنة أو التصفية باستخدام مصطلحات مكونة من ثلاثة أحرف أو أقل. لا تتم فهرسة هذه المصطلحات وستتطلب مطابقتها المزيد من الموارد.
- **المشروع بشكل انتقائي** — اجعل نتائجك أسهل في الفهم من خلال عرض الأعمدة التي تحتاج إليها فقط. يساعد أيضا عرض أعمدة معينة [قبل تشغيل عمليات](/azure/data-explorer/kusto/query/joinoperator) الربط أو عمليات مماثلة على تحسين الأداء.



## <a name="optimize-the-join-operator"></a>`join` تحسين عامل التشغيل
يقوم [عامل تشغيل الصلة](/azure/data-explorer/kusto/query/joinoperator) بدمج صفوف من جدولين من خلال مطابقة القيم في أعمدة محددة. طبق هذه التلميحات لتحسين الاستعلامات التي تستخدم عامل التشغيل هذا.

- **جدول أصغر إلى يسارك**— يطابق `join` عامل التشغيل السجلات الموجودة في الجدول على الجانب الأيمن من جملة الصلة مع السجلات الموجودة على اليمين. من خلال وجود الجدول الأصغر على اليسار، ستحتاج إلى مطابقة عدد أقل من السجلات، وبالتالي تسريع الاستعلام.

    في الجدول أدناه، نقوم بتقليل الجدول `DeviceLogonEvents` الأيسر لتغطية ثلاثة أجهزة محددة فقط قبل الانضمام إليه `IdentityLogonEvents` باستخدام معرفات SID للحساب.

    ```kusto
    DeviceLogonEvents
    | where DeviceName in ("device-1.domain.com", "device-2.domain.com", "device-3.domain.com")
    | where ActionType == "LogonFailed"
    | join
        (IdentityLogonEvents
        | where ActionType == "LogonFailed"
        | where Protocol == "Kerberos")
    on AccountSid
    ```

- **استخدم نكهة الصلة الداخلية** — [إن نكهة الصلة](/azure/data-explorer/kusto/query/joinoperator#join-flavors) الافتراضية أو صلة [innerunique تكرر](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) الصفوف الموجودة في الجدول الأيسر بواسطة مفتاح الصلة قبل إرجاع صف لكل تطابق إلى الجدول الأيمن. إذا كان الجدول الأيسر يحتوي على صفوف متعددة بنفس القيمة للمفتاح `join` ، فسيتم إلغاء تكرار هذه الصفوف لترك صف عشوائي واحد لكل قيمة فريدة.

    يمكن أن يترك هذا السلوك الافتراضي معلومات مهمة من الجدول الأيسر التي يمكن أن توفر نظرة ثاقبة مفيدة. على سبيل المثال، سيظهر الاستعلام أدناه رسالة بريد إلكتروني واحدة تحتوي على مرفق معين فقط، حتى لو تم إرسال المرفق نفسه باستخدام رسائل بريد إلكتروني متعددة:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    لمعالجة هذا القيد، نطبق نكهة [الصلة الداخلية](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) عن طريق تحديد `kind=inner` إظهار جميع الصفوف في الجدول الأيسر مع قيم مطابقة في اليمين:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **ضم السجلات من نافذة زمنية** — عند التحقيق في أحداث الأمان، يبحث المحللون عن الأحداث ذات الصلة التي تحدث في الفترة الزمنية نفسها تقريبا. يؤدي تطبيق نفس النهج عند استخدام `join` الأداء أيضا إلى الاستفادة من خلال تقليل عدد السجلات المراد التحقق منها.

    يتحقق الاستعلام أدناه من أحداث تسجيل الدخول في غضون 30 دقيقة من تلقي ملف ضار:

    ```kusto
    EmailEvents
    | where Timestamp > ago(7d)
    | where ThreatTypes has "Malware"
    | project EmailReceivedTime = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0])
    | join (
    DeviceLogonEvents
    | where Timestamp > ago(7d)
    | project LogonTime = Timestamp, AccountName, DeviceName
    ) on AccountName
    | where (LogonTime - EmailReceivedTime) between (0min .. 30min)
    ```
- **تطبيق عوامل تصفية الوقت على كلا الجانبين** - حتى إذا لم تكن تتحقق من نافذة زمنية معينة، فإن تطبيق عوامل تصفية الوقت على الجدولين الأيمن والأيسر يمكن أن يقلل من عدد السجلات للتحقق من الأداء وتحسينه `join` . ينطبق الاستعلام أدناه على `Timestamp > ago(1h)` كلا الجدولين بحيث يقوم بضم السجلات فقط من الساعة الماضية:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **استخدم تلميحات للأداء** — استخدم التلميحات مع `join` عامل التشغيل لإرشاد الخلفية لتوزيع التحميل عند تشغيل عمليات كثيفة الموارد. [معرفة المزيد حول تلميحات الانضمام](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    على سبيل المثال، يساعد **[تلميح التبديل العشوائي](/azure/data-explorer/kusto/query/shufflequery)** على تحسين أداء الاستعلام عند الانضمام إلى الجداول باستخدام مفتاح ذو علاقة أساسية عالية — مفتاح يحتوي على العديد من القيم الفريدة — مثل `AccountObjectId` في الاستعلام أدناه:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    يساعد **[تلميح البث](/azure/data-explorer/kusto/query/broadcastjoin)** عندما يكون الجدول الأيسر صغيرا (ما يصل إلى 100000 سجل) والجدول الأيمن كبير للغاية. على سبيل المثال، يحاول الاستعلام أدناه الانضمام إلى بعض رسائل البريد الإلكتروني التي تحتوي على مواضيع محددة مع _كل_ الرسائل التي تحتوي على ارتباطات في `EmailUrlInfo` الجدول:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>`summarize` تحسين عامل التشغيل
يقوم [عامل تشغيل التلخيص](/azure/data-explorer/kusto/query/summarizeoperator) بتجميع محتويات جدول. طبق هذه التلميحات لتحسين الاستعلامات التي تستخدم عامل التشغيل هذا.

- **البحث عن قيم مميزة**— بشكل عام، يتم استخدامها `summarize` للبحث عن قيم مميزة يمكن تكرارها. قد يكون من غير الضروري استخدامه لتجميع الأعمدة التي لا تحتوي على قيم متكررة.

    على الرغم من أن البريد الإلكتروني الواحد يمكن أن يكون جزءا من أحداث متعددة، فإن المثال أدناه _ليس_ استخداما `summarize` فعالا لأن معرف رسالة الشبكة لرسالة بريد إلكتروني فردية يأتي دائما مع عنوان مرسل فريد.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    `summarize` يمكن استبدال `project`عامل التشغيل بسهولة، ما ينتج عنه نفس النتائج المحتملة مع استهلاك موارد أقل:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    المثال التالي هو استخدام `summarize` أكثر كفاءة لأنه يمكن أن تكون هناك مثيلات متعددة مميزة لعنوان المرسل الذي يرسل البريد الإلكتروني إلى نفس عنوان المستلم. هذه المجموعات أقل تميزا ومن المحتمل أن تحتوي على تكرارات.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **قم بتبديل الاستعلام** — بينما `summarize` يتم استخدامه بشكل أفضل في الأعمدة ذات القيم المتكررة، يمكن أن تحتوي الأعمدة نفسها أيضا على _علاقة أساسية عالية_ أو أعداد كبيرة من القيم الفريدة. `join` مثل عامل التشغيل، يمكنك أيضا تطبيق [تلميح التبديل العشوائي](/azure/data-explorer/kusto/query/shufflequery) لتوزيع `summarize` تحميل المعالجة وربما تحسين الأداء عند العمل على أعمدة ذات علاقة أساسية عالية.

    يستخدم `summarize` الاستعلام أدناه لحساب عنوان البريد الإلكتروني المميز للمستلم، والذي يمكن تشغيله بمئات الآلاف في المؤسسات الكبيرة. لتحسين الأداء، فإنه يتضمن `hint.shufflekey`:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```



## <a name="query-scenarios"></a>سيناريوهات الاستعلام

### <a name="identify-unique-processes-with-process-ids"></a>تحديد العمليات الفريدة باستخدام معرفات العمليات

يتم إعادة استخدام معرفات العملية (PIDs) في Windows وإعادة استخدامها للعمليات الجديدة. من تلقاء نفسها، لا يمكن أن تكون بمثابة معرفات فريدة لعمليات معينة.

للحصول على معرف فريد لعملية على جهاز معين، استخدم معرف العملية مع وقت إنشاء العملية. عند ربط البيانات أو تلخيصها حول العمليات، قم بتضمين أعمدة لمعرف الجهاز (إما `DeviceId` أو)، ومعرف `DeviceName`العملية (`ProcessId` أو `InitiatingProcessId`)، ووقت إنشاء العملية (`ProcessCreationTime` أو `InitiatingProcessCreationTime`)

يبحث الاستعلام المثال التالي عن العمليات التي تصل إلى أكثر من 10 عناوين IP عبر المنفذ 445 (SMB)، ربما تفحص مشاركات الملفات.

مثال على الاستعلام:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

يلخص الاستعلام من قبل كليهما `InitiatingProcessId` `InitiatingProcessCreationTime` بحيث يبحث في عملية واحدة، دون خلط عمليات متعددة مع نفس معرف العملية.

### <a name="query-command-lines"></a>سطور أوامر الاستعلام
هناك العديد من الطرق لإنشاء سطر أوامر لإنجاز مهمة. على سبيل المثال، يمكن للمهاجم الرجوع إلى ملف صورة بدون مسار، أو بدون ملحق ملف، أو باستخدام متغيرات البيئة، أو باستخدام علامات الاقتباس. يمكن للمهاجم أيضا تغيير ترتيب المعلمات أو إضافة علامات اقتباس ومسافات متعددة.

لإنشاء استعلامات أكثر ديمومة حول سطور الأوامر، طبق الممارسات التالية:

- حدد العمليات المعروفة (مثل *net.exe* أو *psexec.exe*) من خلال مطابقة حقول أسماء الملفات، بدلا من التصفية على سطر الأوامر نفسه.
- توزيع مقاطع سطر الأوامر باستخدام [الدالة parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line)
- عند الاستعلام عن وسيطات سطر الأوامر، لا تبحث عن تطابق تام في وسيطات متعددة غير مرتبطة بترتيب معين. بدلا من ذلك، استخدم التعبيرات العادية أو استخدم عدة عوامل تشغيل منفصلة تحتوي على عوامل تشغيل.
- استخدام التطابقات غير الحساسة لحالة الأحرف. على سبيل المثال، استخدم `=~`وبدلا `contains` `in~`من `==`، و. `in``contains_cs`
- للتخفيف من تقنيات تشويش سطر الأوامر، ضع في اعتبارك إزالة علامات الاقتباس واستبدال الفواصل بمسافات واستبدال مسافات متتالية متعددة بمسافة واحدة. هناك تقنيات تشويش أكثر تعقيدا تتطلب أساليب أخرى، ولكن يمكن أن تساعد هذه التعديلات في معالجة تلك الشائعة.

توضح الأمثلة التالية طرقا مختلفة لإنشاء استعلام يبحث عن *net.exe* الملف لإيقاف خدمة جدار الحماية "MpsSvc":

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on file name, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc"

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc"
```

### <a name="ingest-data-from-external-sources"></a>استيعاب البيانات من مصادر خارجية
لدمج قوائم طويلة أو جداول كبيرة في الاستعلام، استخدم [عامل تشغيل البيانات الخارجية](/azure/data-explorer/kusto/query/externaldata-operator) لاستيعاب البيانات من URI محدد. يمكنك الحصول على بيانات من الملفات بتنسيقات TXT أو CSV أو JSON أو [تنسيقات أخرى](/azure/data-explorer/ingestion-supported-formats). يوضح المثال أدناه كيف يمكنك استخدام قائمة واسعة من تجزئة SHA-256 للبرامج الضارة التي توفرها MalwareBazaar (abuse.ch) للتحقق من المرفقات على رسائل البريد الإلكتروني:

```kusto
let abuse_sha256 = (externaldata(sha256_hash: string)
[@"https://bazaar.abuse.ch/export/txt/sha256/recent/"]
with (format="txt"))
| where sha256_hash !startswith "#"
| project sha256_hash;
abuse_sha256
| join (EmailAttachmentInfo
| where Timestamp > ago(1d)
) on $left.sha256_hash == $right.SHA256
| project Timestamp,SenderFromAddress,RecipientEmailAddress,FileName,FileType,
SHA256,ThreatTypes,DetectionMethods
```

### <a name="parse-strings"></a>توزيع السلاسل
هناك وظائف مختلفة يمكنك استخدامها للتعامل بكفاءة مع السلاسل التي تحتاج إلى تحليل أو تحويل.

| سلسلة | وظيفه | مثال على الاستخدام |
|--|--|--|
| سطور الأوامر | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | استخراج الأمر وكافة الوسيطات. |
| مسارات | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | استخراج مقاطع من مسار ملف أو مجلد. |
| أرقام الإصدارات | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | قم بفك تشفير رقم إصدار يتضمن ما يصل إلى أربعة أقسام وما يصل إلى ثمانية أحرف لكل مقطع. استخدم البيانات الموزعة لمقارنة عمر الإصدار. |
| عناوين IPv4 | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | تحويل عنوان IPv4 إلى عدد صحيح طويل. لمقارنة عناوين IPv4 دون تحويلها، استخدم [ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| عناوين IPv6 | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | تحويل عنوان IPv4 أو IPv6 إلى رمز IPv6 المتعارف عليه. لمقارنة عناوين IPv6، استخدم [ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

للتعرف على جميع دالات الفرز المدعومة، [اقرأ حول دالات سلسلة Kusto](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender لنقطة النهاية. [قم بتشغيل Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل التتبع المتقدمة من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender باتباع الخطوات الواردة في [ترحيل استعلامات التتبع المتقدمة من Microsoft Defender لنقطة النهاية](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [وثائق لغة الاستعلام Kusto](/azure/data-explorer/kusto/query/)
- [معلمات الاستخدام والحصص النسبية](advanced-hunting-limits.md)
- [معالجة أخطاء التتبع المتقدمة](advanced-hunting-errors.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)