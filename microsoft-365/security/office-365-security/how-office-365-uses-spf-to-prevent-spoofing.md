---
title: كيف يمنع إطار نهج المرسل (SPF) الانتحال
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 12/15/2016
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3aff33c5-1416-4867-a23b-e0c0c5b4d2be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: تعرف على Microsoft 365 استخدام سجل TXT الخاص ب إطار نهج المرسل (SPF) في DNS لضمان ثقة أنظمة البريد الإلكتروني الوجهة بالرسائل المرسلة من مجالك المخصص.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 76bc783dc624487b438ca41dcd9fc38bd9bce911
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "63565904"
---
# <a name="how-microsoft-365-uses-sender-policy-framework-spf-to-prevent-spoofing"></a>كيفية Microsoft 365 إطار نهج المرسل (SPF) لمنع الانتحال

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 **ملخص:** تصف هذه المقالة Microsoft 365 يستخدم سجل TXT الخاص ب إطار نهج المرسل (SPF) في DNS لضمان ثقة أنظمة البريد الإلكتروني الوجهة بالرسائل المرسلة من مجالك المخصص. ينطبق هذا الأمر على البريد الصادر المرسل من Microsoft 365. الرسائل المرسلة من Microsoft 365 إلى مستلم داخل Microsoft 365 المرور دائما عبر SPF.

إن سجل SPF TXT هو سجل DNS يساعد على منع الخادعة والتصيد الاحتيالي من خلال التحقق من اسم المجال الذي يتم إرسال رسائل البريد الإلكتروني منه. يتحقق SPF من أصل رسائل البريد الإلكتروني من خلال التحقق من عنوان IP للمرسل مقابل المالك المزعوم لمجال الإرسال.

> [!NOTE]
> تم إهمال أنواع سجلات SPF بواسطة "فريق المهام الهندسية عبر الإنترنت" (IETF) في عام 2014. بدلا من ذلك، تأكد من استخدام سجلات TXT في DNS لنشر معلومات SPF. تستخدم بقية هذه المقالة مصطلح سجل SPF TXT للوضوح.

يقوم مسؤولي المجالات بنشر معلومات SPF في سجلات TXT في DNS. تحدد معلومات SPF خوادم البريد الإلكتروني الصادر المعتمدة. تتحقق أنظمة البريد الإلكتروني الوجهة من أن الرسائل تنشأ من خوادم البريد الإلكتروني الصادر المعتمدة. إذا كنت ملما بالفعل باستخدام SPF، أو إذا كان لديك عملية نشر بسيطة، وما عليك سوى معرفة ما يجب تضمينه في سجل SPF TXT في DNS ل Microsoft 365، يمكنك الانتقال إلى إعداد [SPF في Microsoft 365](set-up-spf-in-office-365-to-help-prevent-spoofing.md) للمساعدة على منع ال انتحال. إذا لم يكن لديك نشر مستضاف بالكامل في Microsoft 365، أو إذا كنت تريد الحصول على مزيد من المعلومات حول كيفية عمل SPF أو كيفية استكشاف الأخطاء وإصلاحها ل SPF Microsoft 365، فاستمر في القراءة.

> [!NOTE]
> في السابق، كان عليك إضافة سجل SPF TXT مختلف إلى مجالك المخصص إذا كنت تستخدم أيضا SharePoint Online. لم يعد هذا مطلوبا. يجب أن يقلل هذا التغيير من خطر SharePoint رسائل الإعلام عبر الإنترنت في مجلد البريد الإلكتروني غير الهام. لست بحاجة إلى إجراء أي تغييرات على الفور، ولكن إذا تلقيت رسالة الخطأ "عدد كبير جدا من عمليات البحث"، فعدل سجل SPF TXT كما هو موضح في إعداد [SPF في Microsoft 365](set-up-spf-in-office-365-to-help-prevent-spoofing.md) للمساعدة في منع الانتحال.

## <a name="how-spf-works-to-prevent-spoofing-and-phishing-in-microsoft-365"></a>كيفية عمل SPF لمنع الخادعة والتصيد الاحتيالي في Microsoft 365
<a name="HowSPFWorks"> </a>

يحدد SPF ما إذا كان المرسل مسموحا له بإرساله نيابة عن مجال أم لا. إذا لم يسمح للمرسل بذلك، أي إذا فشل البريد الإلكتروني في التحقق من SPF على الخادم المتلقي، يحدد نهج البريد العشوائي الذي تم تكوينه على هذا الخادم ما يجب فعله بالرسالة.

يحتوي كل سجل SPF TXT على ثلاثة أجزاء: الإعلان بأنه سجل SPF TXT وعناوين IP المسموح لها بإرسال البريد من مجالك والمجالات الخارجية التي يمكن إرسالها نيابة عن مجالك، ولقاعدة فرض. تحتاج إلى الثلاثة كلها في سجل SPF TXT صالح. تصف هذه المقالة كيفية تشكيل سجل SPF TXT وتوفر أفضل الممارسات للعمل مع الخدمات في Microsoft 365. يتم أيضا توفير ارتباطات إلى إرشادات حول العمل مع جهة تسجيل المجالات لنشر سجلك إلى DNS.

### <a name="spf-basics-ip-addresses-allowed-to-send-from-your-custom-domain"></a>أساسيات SPF: عناوين IP المسموح بإرسالها من مجالك المخصص
<a name="SPFBasicsIPaddresses"> </a>

أطلع على بناء الجملة الأساسي لقاعدة SPF:

v=spf1 \<IP\> \<enforcement rule\>

على سبيل المثال، لنقل أن قاعدة SPF التالية موجودة contoso.com:

v=spf1 \<IP address #1\> \<IP address #2\> \<IP address #3\> \<enforcement rule\>

في هذا المثال، ترشد قاعدة SPF خادم البريد الإلكتروني المتلقي لقبول البريد فقط من عناوين IP هذه لمجال contoso.com:

- عنوان IP رقم 1

- عنوان IP رقم 2

- عنوان IP #3

تخبر قاعدة SPF هذه خادم البريد الإلكتروني المتلقي بأنه إذا كانت الرسالة من contoso.com، وليس من أحد عناوين IP الثلاثة هذه، يجب على الخادم المتلقي تطبيق قاعدة التنفيذ على الرسالة. عادة ما تكون قاعدة التنفيذ أحد الخيارات التالية:

- **فشل صعب.** وضع علامة "فشل كبير" على الرسالة في مغلف الرسالة، ثم اتبع نهج البريد العشوائي المكون من الخادم المتلقي لهذا النوع من الرسائل.

- **فشل ناعم.** وضع علامة "فشل ناعم" على الرسالة في مغلف الرسالة. يتم عادة تكوين خوادم البريد الإلكتروني لتسليم هذه الرسائل على أي حال. لا يرى معظم المستخدمين هذه العلامة.

- **محايد.** لا تفعل شيئا، أي عدم وضع علامة على مغلف الرسالة. يتم عادة حجز هذا لأغراض الاختبار ونادرا ما يتم استخدامه.

تظهر الأمثلة التالية كيفية عمل SPF في حالات مختلفة. في هذه الأمثلة، contoso.com هو المرسل woodgrovebank.com يكون المستلم.

### <a name="example-1-email-authentication-of-a-message-sent-directly-from-sender-to-receiver"></a>مثال 1: مصادقة البريد الإلكتروني لرسالة مرسلة مباشرة من مرسل إلى مستلم
<a name="spfExample1"> </a>

يعمل SPF بشكل أفضل عندما يكون المسار من المرسل إلى المستلم مباشرا، على سبيل المثال:

![رسم تخطيطي يعرض كيفية مصادقة SPF للبريد الإلكتروني عند إرساله مباشرة من خادم إلى خادم.](../../media/835c20a7-ed4c-49c4-91fe-b8ebb3e452a1.jpg)

عندما woodgrovebank.com الرسالة، إذا كان عنوان IP رقم 1 في سجل TXT ل SPF ل contoso.com، فإن الرسالة تمرر التحقق من SPF ثم يتم مصادقتها.

### <a name="example-2-spoofed-sender-address-fails-the-spf-check"></a>المثال 2: فشل عنوان المرسل المهتز في التحقق من SPF
<a name="spfExample2"> </a>

لنفترض أن التصيد الاحتيالي يعثر على طريقة للانتحال contoso.com:

![رسم تخطيطي يعرض كيفية مصادقة SPF للبريد الإلكتروني عند إرساله من خادم منتحل.](../../media/235dac3d-cdc5-466e-86e0-37b5979de198.jpg)

بما أن عنوان IP رقم 12 ليس في سجل SPF TXT ل contoso.com، تفشل الرسالة في التحقق من SPF وقد يختار المستلم وضع علامة عليه كبريد عشوائي.

### <a name="example-3-spf-and-forwarded-messages"></a>المثال 3: SPF والرسائل التي تم إعادة توجيهها
<a name="spfExample3"> </a>

أحد عيوب SPF هو أنه لا يعمل عند إعادة توجيه رسالة بريد إلكتروني. على سبيل المثال، افترض أن المستخدم في woodgrovebank.com قام بإعداد قاعدة إعادة توجيه لإرسال كل رسائل البريد الإلكتروني إلى حساب outlook.com:

![رسم تخطيطي يظهر كيف يتعذر على SPF مصادقة البريد الإلكتروني عند إعادة توجيه الرسالة.](../../media/6e92acd6-463e-4a1b-8327-fb1cf861f356.jpg)

تمر الرسالة في الأصل بالتحقق من SPF في woodgrovebank.com ولكنها تفشل في التحقق من SPF في outlook.com لأن IP #25 غير في سجل SPF TXT ل contoso.com. Outlook.com بعد ذلك وضع علامة على الرسالة كرسالة عشوائية. لل حل هذه المشكلة، استخدم SPF مع أساليب مصادقة البريد الإلكتروني الأخرى مثل DKIM و DMARC.

### <a name="spf-basics-including-third-party-domains-that-can-send-mail-on-behalf-of-your-domain"></a>أساسيات SPF: بما في ذلك مجالات  الأطراف الخارجية التي يمكنها إرسال البريد نيابة عن مجالك
<a name="SPFBasicsIncludes"> </a>

بالإضافة إلى عناوين IP، يمكنك أيضا تكوين سجل SPF TXT لتضمين المجالات كمرسلين. تضاف هذه إلى سجل SPF TXT كعبارات "تضمين". على سبيل المثال، contoso.com تريد تضمين كل عناوين IP الخاصة خوادم البريد من contoso.net contoso.org التي تملكها أيضا. للقيام بذلك، contoso.com نشر سجل SPF TXT يبدو كما يلي:

```text
v=spf1 include:contoso.net include:contoso.org -all
```

عندما يرى الخادم المتلقي هذا السجل في DNS، يقوم أيضا بإجراء عملية البحث DNS على سجل SPF TXT ل contoso.net ثم ل contoso.org. إذا تم العثور على بيان تضمين إضافي ضمن سجلات contoso.net أو contoso.org، سيتبع ذلك أيضا. للمساعدة في منع هجمات رفض الخدمة، الحد الأقصى لعدد عمليات البحث عن DNS لرسالة بريد إلكتروني واحدة هو 10. تمثل كل العبارة المتضمنة عملية البحث الإضافية ل DNS. إذا تجاوزت الرسالة الحد 10، ففشلت الرسالة في SPF. بمجرد أن تصل الرسالة إلى هذا الحد، وفقا لطريقة تكوين الخادم المتلقي، قد يتلقى المرسل رسالة نصها الرسالة التي تم إنشاؤها "عدد كبير جدا من البحث" أو أن "تم تجاوز الحد الأقصى لعدد القفزات للرسالة" (والذي قد يحدث عند تكرار عملية البحث وتجاوز المهلة DNS). للحصول على تلميحات حول كيفية تجنب هذا الأمر، راجع استكشاف الأخطاء وإصلاحها[: أفضل الممارسات ل SPF في](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot) Microsoft 365.

## <a name="requirements-for-your-spf-txt-record-and-microsoft-365"></a>متطلبات سجل SPF TXT Microsoft 365
<a name="SPFReqsinO365"> </a>

إذا قمت بإعداد البريد عند إعداد Microsoft 365، قمت بالفعل بإنشاء سجل TXT SPF يعرف خوادم مراسلات Microsoft كمصدر شرعي للبريد لمجالك. يبدو هذا السجل على الأرجح كما يلي:

```text
v=spf1 include:spf.protection.outlook.com -all
```

إذا كنت عميلا مستضافا بالكامل، أي أنه ليس لديك خوادم بريد في الموقع ترسل البريد الصادر، فهذا هو سجل SPF TXT الوحيد الذي تحتاج إلى نشره Office 365.

إذا كان لديك نشر مختلط (أي أن لديك بعض علب البريد المحلية والبعض الآخر مستضاف في Microsoft 365)، أو إذا كنت عميلا مستقلا ل Exchange Online Protection (EOP) (أي أن مؤسستك تستخدم EOP لحماية علب البريد المحلية)، يجب إضافة عنوان IP الصادر لكل خادم من خوادم البريد المحلية على الحافة إلى سجل SPF TXT في DNS.

## <a name="form-your-spf-txt-record-for-microsoft-365"></a>تشكيل سجل TXT ل SPF Microsoft 365
<a name="FormYourSPF"> </a>

استخدم معلومات بناء الجملة في هذه المقالة لتشكيل سجل SPF TXT لمجالك المخصص. على الرغم من وجود خيارات بناء جملة أخرى لم يتم ذكرها هنا، إلا أنها الخيارات الأكثر استخداما. بعد تكوين السجل، ستحتاج إلى تحديث السجل لدى جهة تسجيل المجالات.

للحصول على معلومات حول المجالات التي ستحتاج إلى تضمينها Microsoft 365، راجع سجلات [DNS الخارجية المطلوبة ل SPF](../../enterprise/external-domain-name-system-records.md). استخدم [الإرشادات خطوة بخطوة](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) لتحديث سجلات SPF (TXT) جهة تسجيل المجالات.

### <a name="spf-txt-record-syntax-for-microsoft-365"></a>بناء جملة سجل SPF TXT Microsoft 365
<a name="SPFSyntaxO365"> </a>

سجل SPF TXT النموذجي Microsoft 365 له بناء الجملة التالي:

```text
v=spf1 [<ip4>|<ip6>:<IP address>] [include:<domain name>] <enforcement rule>
```

على سبيل المثال:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 include:spf.protection.outlook.com -all
```

حيث:

- **v=spf1** مطلوب. يعرف هذا سجل TXT كسجل SPF TXT.

- **يشير ip4** إلى أنك تستخدم عناوين الإصدار 4 من IP. **يشير ip6** إلى أنك تستخدم عناوين الإصدار 6 من IP. إذا كنت تستخدم عناوين IP IPv6، فاستبدل **ip4** **ب ip6** في الأمثلة في هذه المقالة. يمكنك أيضا تحديد نطاقات عناوين IP باستخدام "تصنيف CIDR"، على سبيل المثال **ip4:192.168.0.1/26**.

- _عنوان IP_ هو عنوان IP الذي تريد إضافته إلى سجل SPF TXT. عادة ما يكون هذا هو عنوان IP الخاص بخادم البريد الصادر لمنظمتك. يمكنك سرد عدة خوادم بريد واردة. للحصول على مزيد من المعلومات، راجع مثال[: سجل SPF TXT](how-office-365-uses-spf-to-prevent-spoofing.md#ExampleSPFMultipleMailServerO365) لعدة خوادم بريد واردة والمزيد Microsoft 365.

- _اسم المجال_ هو المجال الذي تريد إضافته كمرسل شرعي. للحصول على قائمة بأسماء المجالات التي يجب تضمينها Microsoft 365، راجع [سجلات DNS الخارجية المطلوبة ل SPF](../../enterprise/external-domain-name-system-records.md).

- عادة ما تكون قاعدة التنفيذ واحدة من القواعد التالية:

  - -all

    يشير إلى فشل صعب. إذا كنت تعرف كل عناوين IP المعتمدة لمجالك، فسجلها في سجل SPF TXT واستخدم مؤهل الكل (الفشل الثابت). أيضا، إذا كنت تستخدم SPF فقط، أي أنك لا تستخدم DMARC أو DKIM، يجب استخدام مؤهل الكل. نوصي باستخدام هذا المؤهل دائما.

  - ~all

    يشير إلى الفشل الناعم. إذا لم تكن متأكدا من أن لديك قائمة كاملة من عناوين IP، يجب عليك استخدام مؤهل ~all (فشل ناعم). أيضا، إذا كنت تستخدم DMARC مع p=quarantine أو p=reject، يمكنك استخدام ~all. وبخلاف ذلك، استخدم -all.

  - ?all

    يشير إلى محايد. يتم استخدام هذا عند اختبار SPF. لا نوصي باستخدام هذا المؤهل في النشر المباشر.

### <a name="example-spf-txt-record-to-use-when-all-of-your-mail-is-sent-by-microsoft-365"></a>مثال: سجل SPF TXT لاستخدامه عند إرسال كل البريد بواسطة Microsoft 365
<a name="ExampleSPFNoSP"> </a>

إذا تم إرسال كل البريد بواسطة Microsoft 365، فاستخدمه في سجل SPF TXT:

```text
v=spf1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-a-hybrid-scenario-with-one-on-premises-exchange-server-and-microsoft-365"></a>مثال: سجل SPF TXT سيناريو مختلط مع سجل Exchange Server Microsoft 365
<a name="ExampleSPFHybridOneExchangeServer"> </a>

في بيئة مختلطة، إذا كان عنوان IP ل Exchange Server المحلية هو 192.168.0.1، لكي تتمكن من تعيين قاعدة فرض SPF على الفشل الثابت، قم ب إنشاء سجل SPF TXT كما يلي:

```text
v=spf1 ip4:192.168.0.1 include:spf.protection.outlook.com -all
```

### <a name="example-spf-txt-record-for-multiple-outbound-on-premises-mail-servers-and-microsoft-365"></a>مثال: سجل SPF TXT لعدة خوادم بريد في الداخل Microsoft 365
<a name="ExampleSPFMultipleMailServerO365"> </a>

إذا كان لديك عدة خوادم بريد صادر، فتضمن عنوان IP لكل خادم بريد في سجل SPF TXT وافصل كل عنوان IP مع مسافة متبوع ببيان "ip4:". على سبيل المثال:

```text
v=spf1 ip4:192.168.0.1 ip4:192.168.0.2 ip4:192.168.0.3 include:spf.protection.outlook.com -all
```

## <a name="next-steps-set-up-spf-for-microsoft-365"></a>الخطوات التالية: إعداد SPF Microsoft 365
<a name="SPFNextSteps"> </a>

بعد أن تقوم بالتكتاب من سجل SPF TXT، اتبع الخطوات في [إعداد SPF في Microsoft 365](set-up-spf-in-office-365-to-help-prevent-spoofing.md) للمساعدة في منع االإضافة إلى مجالك.

على الرغم من أن SPF تم تصميمه للمساعدة في منع انتحاله، ولكن هناك أساليب انتحال لا يمكن ل SPF حمايتها. من أجل الحماية من هذه، بمجرد إعداد SPF، يجب أيضا تكوين DKIM و DMARC Microsoft 365. للبدء، راجع [استخدام DKIM للتحقق من صحة](use-dkim-to-validate-outbound-email.md) البريد الإلكتروني الصادر المرسل من مجالك المخصص في Microsoft 365. بعد ذلك، راجع [استخدام DMARC للتحقق من صحة البريد الإلكتروني في Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="troubleshooting-best-practices-for-spf-in-microsoft-365"></a>استكشاف الأخطاء وإصلاحها: أفضل الممارسات ل SPF في Microsoft 365
<a name="SPFTroubleshoot"> </a>

يمكنك إنشاء سجل SPF TXT واحد فقط لمجالك المخصص. يؤدي إنشاء سجلات متعددة إلى حدوث حالة من حالة التخلف عن العمل، وسيفشل SPF. لتجنب حدوث ذلك، يمكنك إنشاء سجلات منفصلة لكل منطقة فرعية. على سبيل المثال، أنشئ سجلا واحدا contoso.com سجلا آخر bulkmail.contoso.com.

إذا كانت رسالة بريد إلكتروني تتسبب في إجراء أكثر من 10 عمليات البحث في DNS قبل تسليمها، سيستجيب خادم البريد المتلقي بخطأ دائم، يسمى أيضا ب  _permerror_، ويتسبب في فشل الرسالة في التحقق من SPF. قد يستجيب الخادم المتلقي أيضا مع تقرير بعدم التسليم (NDR) يحتوي على خطأ مماثل لخطأ:

- تجاوزت الرسالة عدد القفزات.

- تطلبت الرسالة الكثير من البحث.

## <a name="avoiding-the-too-many-lookups-error-when-you-use-third-party-domains-with-microsoft-365"></a>تجنب الخطأ "عدد كبير جدا من البحث" عند استخدام مجالات جهة خارجية مع Microsoft 365
<a name="SPFTroubleshoot"> </a>

توجه بعض سجلات SPF TXT لمجالات  الأطراف الخارجية الخادم المتلقي لتنفيذ عدد كبير من عمليات البحث في DNS. على سبيل المثال، في وقت كتابة هذه Salesforce.com يحتوي على 5 عبارات تضمين في سجله:

```text
v=spf1 include:_spf.google.com
include:_spfblock.salesforce.com
include:_qa.salesforce.com
include:_spfblock1.salesforce.com
include:spf.mandrillapp.com mx ~all
```

لتجنب الخطأ، يمكنك تنفيذ نهج حيث يجب على أي شخص يرسل بريدا إلكترونيا مجمعا، على سبيل المثال، استخدام مجال فرعي لهذا الغرض تحديدا. بعد ذلك، يمكنك تعريف سجل SPF TXT مختلف للمسهم الفرعي الذي يتضمن البريد الإلكتروني المجمع.

 في بعض الحالات، مثل مثال salesforce.com، يجب استخدام المجال في سجل SPF TXT، ولكن في حالات أخرى، قد تكون جهة خارجية قد أنشأت بالفعل مجالا فرعيا لاستخدامه لهذا الغرض. على سبيل المثال exacttarget.com إنشاء سجل فرعي تحتاج إلى استخدامه لسجل SPF TXT:

```text
cust-spf.exacttarget.com
```

عندما تقوم بتضمين مجالات جهة خارجية في سجل SPF TXT، يجب أن تؤكد مع الطرف الثالث المجال أو المجال الفرعي الذي يجب استخدامه لتجنب الوصول إلى حد البحث 10.

## <a name="how-to-view-your-current-spf-txt-record-and-determine-the-number-of-lookups-that-it-requires"></a>كيفية عرض سجل SPF TXT الحالي وتحديد عدد البحث الذي يتطلبه
<a name="SPFTroubleshoot"> </a>

يمكنك استخدام nslookup لعرض سجلات DNS، بما في ذلك سجل SPF TXT. يتوفر عدد من الأدوات المجانية عبر الإنترنت التي يمكنك استخدامها لعرض محتويات سجل SPF TXT. بالنظر إلى سجل SPF TXT ومتابعته لسلسلة عبارات التضمين وإعادة التوجيه، يمكنك تحديد عدد عمليات البحث في DNS التي يتطلبها السجل. ستحسب بعض الأدوات عبر الإنترنت حتى هذه البحثات و تعرضها لك. سيساعد تعقب هذا الرقم في منع الرسائل المرسلة من مؤسستك من تشغيل خطأ دائم، يسمى خطأ perm، من الخادم المتلقي.

## <a name="for-more-information"></a>لمزيد من المعلومات
<a name="SPFTroubleshoot"> </a>

هل تحتاج إلى مساعدة في إضافة سجل SPF TXT؟ اقرأ المقالة إنشاء [سجلات DNS](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md#add-or-edit-an-spf-txt-record-to-help-prevent-email-spam-outlook-exchange-online) لدى أي موفر استضافة DNS Microsoft 365 للحصول على معلومات مفصلة حول استخدام إطار نهج المرسل مع مجالك المخصص في Microsoft 365. [تتضمن رؤوس رسائل مكافحة البريد](anti-spam-message-headers.md) العشوائي حقول بناء الجملة Microsoft 365 التحقق من SPF.
