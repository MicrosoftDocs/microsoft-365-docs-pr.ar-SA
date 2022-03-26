---
title: أفضل ممارسات استعلام البحث المتقدم في Microsoft 365 Defender
description: تعرف على كيفية إنشاء استعلامات سريعة وفعالة و خالية من الأخطاء حول البحث عن التهديدات باستخدام البحث المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و المخطط، و kusto، و تجنب المهيأ، وخطوط الأوامر، وم id العملية، وتحسين، وأفضل الممارسات، و تحليل، والانضمام، والتلخيص
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
ms.openlocfilehash: d797fb8843bdf5d29e9af43cac152461eb379e5f
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63570414"
---
# <a name="advanced-hunting-query-best-practices"></a>أفضل ممارسات استعلام البحث المتقدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

طبق هذه التوصيات للحصول على النتائج بشكل أسرع وتجنب المهات أثناء تشغيل الاستعلامات المعقدة. للحصول على مزيد من الإرشادات حول تحسين أداء الاستعلام، اقرأ [أفضل ممارسات استعلام Kusto](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>فهم الحصص النسبية لمورد CPU
استنادا إلى حجمه، يمكن لكل مستأجر الوصول إلى كمية معينة من موارد CPU المخصصة لتشغيل استعلامات الصيد المتقدمة. للحصول على معلومات مفصلة حول معلمات الاستخدام المختلفة، [اقرأ حول الحصص النسبية](advanced-hunting-limits.md) المتقدمة للصيد ومعاينات الاستخدام.

بعد تشغيل الاستعلام، يمكنك رؤية وقت التنفيذ واستخدام الموارد (منخفض ومتوسط وأعلى). عالية تشير إلى أن الاستعلام قد تطلب المزيد من الموارد لتشغيله ويمكن تحسينه لإرجاع النتائج بفعالية أكبر.

:::image type="content" source="../../media/resource-usage.png" alt-text="تفاصيل الاستعلام ضمن علامة التبويب **النتائج** في مدخل Microsoft 365 Defender" lightbox="../../media/resource-usage.png":::

يجب على العملاء الذين يديرون استعلامات متعددة بشكل منتظم تعقب الاستهلاك وتطبيق إرشادات التحسين في هذه المقالة لتقليل الانقطاع الناتج عن تجاوز الحصص النسبية أو معلمات الاستخدام.

## <a name="general-optimization-tips"></a>تلميحات التحسين العامة

- **حجم الاستعلامات الجديدة** —إذا كنت تعتقد أن استعلاما سيرجع مجموعة نتائج كبيرة، فقيمها أولا باستخدام [عامل تشغيل العدد](/azure/data-explorer/kusto/query/countoperator). استخدم [الحد](/azure/data-explorer/kusto/query/limitoperator) أو المرادف `take` لتجنب مجموعات النتائج الكبيرة.
- تطبيق **عوامل** التصفية مبكرا—يمكنك تطبيق عوامل تصفية الوقت و عوامل التصفية الأخرى لتقليل مجموعة البيانات، خاصة قبل استخدام دالات التحويل والحل، مثل [substring()](/azure/data-explorer/kusto/query/substringfunction)أو [replace()](/azure/data-explorer/kusto/query/replacefunction)أو [trim()](/azure/data-explorer/kusto/query/trimfunction)أو [toupper()](/azure/data-explorer/kusto/query/toupperfunction)أو [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction). في المثال أدناه، يتم استخدام دالة تحليل [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) بعد أن خفضت عوامل التصفية عدد السجلات.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **يحتوي على يدق** يحتوي على — `has` لتجنب البحث في الضمنات الفرعية داخل الكلمات بدون داع، استخدم عامل التشغيل بدلا من `contains`. [التعرف على عوامل تشغيل السلاسل](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **ابحث في أعمدة معينة** — ابحث في عمود معين بدلا من تشغيل عمليات البحث في النص الكامل عبر كل الأعمدة. لا تستخدم للتحقق `*` من كل الأعمدة.
- **تتحسس حالة التحسس للسرعة**—تكون عمليات البحث الحساسة لالحالتين أكثر تحديدا وبشكل عام أكثر أداء. أسماء عوامل تشغيل السلاسل الحساسة [لالحالتين](/azure/data-explorer/kusto/query/datatypes-string-operators)، مثل `has_cs` و `contains_cs`، تنتهي عادة ب `_cs`. يمكنك أيضا استخدام عامل التشغيل "يساوي" الذي يتحسس حالة الحالة بدلا `==` من `=~`.
- **تحليل، لا** تستخرج— استخدم عامل التشغيل [تحليل](/azure/data-explorer/kusto/query/parseoperator) أو دالة تحليل مثل [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction)، كلما أمكن ذلك. تجنب عامل `matches regex` تشغيل السلسلة أو الدالة [extract()](/azure/data-explorer/kusto/query/extractfunction)، وكلاهما يستخدم تعبيرا عاديا. احجز استخدام التعبير العادي للسيناريوهات الأكثر تعقيدا. [قراءة المزيد حول دالات تحليل](#parse-strings)
- **تصفية الجداول وليس التعبيرات**—لا تقوم بالتصفية على عمود محسوب إذا كان بإمكانك التصفية على عمود جدول.
- **لا توجد مصطلحات من ثلاثة أحرف** — تجنب المقارنة أو التصفية باستخدام مصطلحات ذات ثلاثة أحرف أو أقل. لا يتم فهرسة هذه الشروط وستتطلب مطابقتها موارد إضافية.
- **Project اختياريا** — اجعل فهم النتائج أسهل من خلال تقديم الأعمدة التي تحتاج إليها فقط. يساعد أيضا عرض أعمدة معينة قبل تشغيل عمليات [الانضمام](/azure/data-explorer/kusto/query/joinoperator) أو عمليات مماثلة على تحسين الأداء.

## <a name="optimize-the-join-operator"></a>تحسين عامل `join` التشغيل
[يدمج عامل تشغيل](/azure/data-explorer/kusto/query/joinoperator) الضم الصفوف من جدولين من خلال مطابقة القيم في أعمدة محددة. طبق هذه التلميحات لتحسين الاستعلامات التي تستخدم عامل التشغيل هذا.

- **جدول أصغر إلى اليسار**— `join` يطابق عامل التشغيل السجلات في الجدول على الجانب الأيمن من بيان الانضمام إلى السجلات على الجانب الأيسر. من خلال وجود الجدول الأصغر على اليمين، ستحتاج إلى مطابقة عدد أقل من السجلات، مما يسرع الاستعلام.

    في الجدول أدناه، نقوم بخفض `DeviceLogonEvents` `IdentityLogonEvents` الجدول الأيسر لتغطية ثلاثة أجهزة محددة فقط قبل الانضمام به بواسطة SIDs للحساب.

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

- استخدم نكهات الضم **الداخلي— نكهات** الضم [](/azure/data-explorer/kusto/query/joinoperator#join-flavors) الافتراضية أو [الضم](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) الداخلي يكبل الصفوف في الجدول الأيمن بمفتاح الانضمام قبل إرجاع صف لكل تطابق إلى الجدول الصحيح. إذا كان الجدول `join` الأيسر يحتوي على صفوف متعددة بنفس قيمة المفتاح، سيتم تكرار هذه الصفوف لترك صف عشوائي واحد لكل قيمة فريدة.

    يمكن أن يترك هذا السلوك الافتراضي معلومات مهمة من الجدول الأيسر من الممكن أن توفر معلومات مفيدة. على سبيل المثال، سيعرض الاستعلام أدناه رسالة بريد إلكتروني واحدة فقط تحتوي على مرفق معين، حتى لو تم إرسال المرفق نفسه باستخدام رسائل بريد إلكتروني متعددة:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    لمعالجة هذا القيد، نطبق [](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) `kind=inner` طعم الانضمام الداخلي من خلال تحديد إظهار كل الصفوف في الجدول الأيمن مع قيم متطابقة في الجانب الأيسر:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **ضم السجلات من نافذة زمنية** — عند التحقق من أحداث الأمان، يطلع المحللون على الأحداث ذات الصلة التي تحدث في الفترة الزمنية نفسها تقريبا. كما يؤدي تطبيق النهج نفسه عند استخدام `join` ذلك إلى تحسين الأداء عن طريق تقليل عدد السجلات التي يجب التحقق منها.

    يتحقق الاستعلام أدناه من وجود أحداث تسجيل تسجيل في غضون 30 دقيقة من استلام ملف ضار:

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
- **يمكنك تطبيق عوامل**`join` تصفية الوقت على كلا الجانبين— حتى إذا لم تكن تقوم بالتحقق من نافذة زمنية معينة، فإن تطبيق عوامل تصفية الوقت على الجدولين الأيمن والأيسار يمكن أن يقلل من عدد السجلات للتحقق من الأداء وتحسينه. ينطبق الاستعلام أدناه `Timestamp > ago(1h)` على الجدولين بحيث يقوم بضم السجلات من الساعة الماضية فقط:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **استخدم تلميحات للأداء** — استخدم `join` تلميحات مع عامل التشغيل لكي ترشد الواجهة الخلفية لتوزيع التحميل عند تشغيل العمليات التي تستخدم الموارد بشكل كبير. [تعرف على المزيد حول تلميحات الانضمام](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    على سبيل المثال، **[](/azure/data-explorer/kusto/query/shufflequery)** يساعد تلميح تبديل الجداول على تحسين أداء الاستعلام عند الانضمام إلى الجداول باستخدام مفتاح مع علاقة أساسية عالية — مفتاح مع العديد من القيم الفريدة — `AccountObjectId` مثل في الاستعلام أدناه:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    يساعد **[تلميح البث](/azure/data-explorer/kusto/query/broadcastjoin)** عندما يكون الجدول الأيمن صغيرا (ما يصل إلى 100000 سجل) وكان الجدول الأيسر كبيرا للغاية. على سبيل المثال، يحاول الاستعلام أدناه الانضمام إلى بعض رسائل البريد الإلكتروني التي تتضمن مواضيع معينة مع كل الرسائل التي  تحتوي على ارتباطات في `EmailUrlInfo` الجدول:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>تحسين عامل `summarize` التشغيل
[يجمع عامل تشغيل](/azure/data-explorer/kusto/query/summarizeoperator) التلخيص محتويات جدول. طبق هذه التلميحات لتحسين الاستعلامات التي تستخدم عامل التشغيل هذا.

- **البحث عن قيم مميزة**— بشكل عام، استخدمها `summarize` للعثور على قيم مميزة يمكن أن تكون متكررة. قد لا يكون من الضروري استخدامه لتجميع الأعمدة التي لا تملك قيما متكررة.

    على الرغم من أن رسالة بريد  `summarize` إلكتروني واحدة يمكن أن تكون جزءا من أحداث متعددة، فإن المثال أدناه ليس استخداما فعالا لأن عنوان المرسل الفريد دائما هو "معر ة رسالة شبكة" لبريد إلكتروني فردي.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    يمكن `summarize` استبدال عامل `project`التشغيل بسهولة ب ، مما يؤدي إلى الحصول على النتائج نفسها مع استهلاك موارد أقل:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    المثال التالي هو استخدام أكثر فعالية `summarize` لأنه يمكن أن يكون هناك مثيلات مميزة متعددة عنوان مرسل يرسل بريدا إلكترونيا إلى عنوان المستلم نفسه. هذه المجموعات أقل تميزا ومن المرجح أن يكون لها تكرارات.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **تبديل الاستعلام بشكل** متكرر— `summarize` على الرغم من أنه الأفضل استخداما في الأعمدة ذات القيم المتكررة، يمكن أن يكون للأعمدة نفسها أيضا  علاقة أساسية عالية أو أعداد كبيرة من القيم الفريدة. مثل عامل `join` التشغيل، [](/azure/data-explorer/kusto/query/shufflequery) `summarize` يمكنك أيضا تطبيق تلميح تبديل خلطة مع لتوزيع تحميل المعالجة ومن المحتمل أن يحسن الأداء عند التشغيل على أعمدة ذات علاقة أساسية عالية.

    يستخدم الاستعلام أدناه حساب `summarize` عنوان بريد إلكتروني مميز للمستلم، والذي يمكن تشغيله بمئات الآلاف في المؤسسات الكبيرة. لتحسين الأداء، يتضمن `hint.shufflekey`:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

## <a name="query-scenarios"></a>سيناريوهات الاستعلام

### <a name="identify-unique-processes-with-process-ids"></a>تحديد عمليات فريدة باستخدام "معرّف العمليات"

يتم إعادة تدوير "الم IDs" للعمليات (PIDs) في Windows وإعادة استخدامها للعمليات الجديدة. ولا يمكنها أن تعمل بمفردها كمعرف فريد لعمليات معينة.

للحصول على معرف فريد لعملية على جهاز معين، استخدم معرف العملية مع وقت إنشاء العملية. عندما تقوم بضم البيانات حول العمليات أو تلخيصها، قم بتضمين أعمدة لمعرف الجهاز (`DeviceId``DeviceName`إما أو)، معرف العملية (`ProcessId` `InitiatingProcessId`أو )، والوقت الذي تم فيه إنشاء العملية (`ProcessCreationTime` أو `InitiatingProcessCreationTime`)

يعثر الاستعلام في المثال التالي على العمليات التي يمكن من الوصول إلى أكثر من 10 عناوين IP عبر المنفذ 445 (SMB)، وربما إجراء مسح ضوئي بحثا عن أسهم الملفات.

مثال استعلام:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

يلخص الاستعلام حسب كليهما `InitiatingProcessId` `InitiatingProcessCreationTime` ومن ثم يطلع على عملية واحدة، من دون خلط عمليات متعددة باستخدام نفس معرّف العملية.

### <a name="query-command-lines"></a>أسطر أوامر الاستعلام
هناك طرق عديدة لإنشاء سطر أوامر لتنفيذ مهمة. على سبيل المثال، يمكن للمهاجم الإشارة إلى ملف صورة بدون مسار أو بدون ملحق ملف أو استخدام متغيرات البيئة أو علامات اقتباس. يمكن للمهاجم أيضا تغيير ترتيب المعلمات أو إضافة عدة علامات اقتباس ومساحات.

لإنشاء استعلامات أكثر ديمومة حول أسطر الأوامر، طبق الممارسات التالية:

- تحديد العمليات المعروفة (مثلnet.exeأو ** *psexec.exe*) من خلال المطابقة في حقول اسم الملف، بدلا من التصفية على سطر الأوامر نفسه.
- تحليل مقاطع سطر الأوامر باستخدام الدالة [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line)
- عند الاستعلام عن وسيطات سطر الأوامر، لا تبحث عن تطابق دقيق في وسيطات متعددة غير مرتبطة في ترتيب معين. بدلا من ذلك، استخدم التعبيرات العادية أو استخدم عوامل تشغيل منفصلة متعددة.
- استخدم تطابقات حالة غير حساسة. على سبيل المثال، استخدم `=~`و و و `contains` بدلا من `==`و `in`و `contains_cs``in~`.
- للحد من أساليب التهتيم في سطر الأوامر، يجب عليك التفكير في إزالة علامات الاقتباس واستبدال الفاصلات بالمساحات واستبدال مسافات متتالية متعددة بمساحة واحدة. هناك أساليب أكثر تعقيدا للتعتيم تتطلب أساليب أخرى، ولكن يمكن أن تساعد هذه التعديلات في معالجة الأساليب الشائعة.

تظهر الأمثلة التالية طرقا مختلفة لإنشاء استعلام للبحث عن الملف *net.exeلإيقاف خدمة* جدار الحماية "MpsSvc":

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

### <a name="ingest-data-from-external-sources"></a>استخدام البيانات من مصادر خارجية
لتضمين قوائم طويلة أو جداول كبيرة في الاستعلام، استخدم عامل [](/azure/data-explorer/kusto/query/externaldata-operator) تشغيل البيانات الخارجية لاستلام البيانات من URI محدد. يمكنك الحصول على بيانات من ملفات بتنسيق TXT أو CSV أو JSON أو [تنسيقات أخرى](/azure/data-explorer/ingestion-supported-formats). يوضح المثال أدناه كيف يمكنك استخدام القائمة الموسعة من توابل البرامج الضارة SHA-256 التي توفرها MalwareBazaar (abuse.ch) للتحقق من المرفقات على رسائل البريد الإلكتروني:

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

### <a name="parse-strings"></a>تحليل السلاسل
هناك العديد من الدالات التي يمكنك استخدامها لمعالجة السلاسل التي تحتاج إلى تحليل أو تحويل بكفاءة.

| سلسلة | الدالة | مثال على الاستخدام |
|--|--|--|
| خطوط الأوامر | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | استخراج الأمر وكل الوسيطات. |
| المسارات | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | استخراج مقاطع مسار ملف أو مجلد. |
| أرقام الإصدارات | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | فك بناء رقم إصدار يصل إلى أربعة أقسام وما يصل إلى ثمانية أحرف لكل مقطع. استخدم البيانات التي تم تحليلها لمقارنة عمر الإصدار. |
| عناوين IPv4 | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | تحويل عنوان IPv4 إلى عدد صحيح طويل. لمقارنة عناوين IPv4 دون تحويلها، استخدم ipv4_compare [()](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| عناوين IPv6 | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | تحويل عنوان IPv4 أو IPv6 إلى iPv6 notation المكين. لمقارنة عناوين IPv6، استخدم ipv6_compare [()](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

للتعرف على كل دالات تحليل معتمدة، اقرأ [حول دالات سلسلة Kusto](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender for Endpoint. [قم Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender باتباع الخطوات الواردة في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [وثائق لغة استعلام Kusto](/azure/data-explorer/kusto/query/)
- [معلمات الاستخدام والحصص النسبية](advanced-hunting-limits.md)
- [معالجة أخطاء الصيد المتقدمة](advanced-hunting-errors.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)