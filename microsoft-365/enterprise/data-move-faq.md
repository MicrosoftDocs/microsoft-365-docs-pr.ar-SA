---
title: الأسئلة المتداولة حول نقل البيانات
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/31/2022
audience: ITPro
ms.topic: faq
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: ابحث عن إجابات للأسئلة المتداولة (الأسئلة المتداولة) حول نقل البيانات الأساسية إلى جغرافيا لمركز بيانات Office 365 جديد.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 3164612238010e72eb02510e1264cca528b80f38
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874308"
---
# <a name="data-move-general-faq"></a>الأسئلة المتداولة حول نقل البيانات

فيما يلي إجابات للأسئلة العامة حول نقل بيانات العملاء الأساسية الثابتة إلى جغرافيا لمركز بيانات جديد.

### <a name="what-customers-are-eligible-to-request-a-move"></a>ما العملاء المؤهلون لطلب النقل؟
<details><summary>انقر للتوسيع</summary>

سيتمكن العملاء التجاريون Microsoft 365 الحاليون الذين حددوا بلدا مؤهلا جغرافيا لمركز البيانات الجديد من طلب النقل. البرنامج موجود فقط للمستأجرين الذين تم تعيين رمز البلد المؤهل لهم إلى مستأجر Microsoft 365 ترحيل بيانات العملاء الأساسية الثابتة لأحمال العمل المؤهلة إلى الموقع الجغرافي لمركز البيانات Microsoft 365 المقابل. راجع [كيفية طلب نقل البيانات](request-your-data-move.md) لتأكيد أهلية البلد.

</details>

### <a name="how-do-we-define-core-customer-data"></a>كيف يمكننا تعريف بيانات العملاء الأساسية؟
<details><summary>انقر للتوسيع</summary>

بيانات العملاء الأساسية هي مصطلح يشير إلى مجموعة فرعية من بيانات العملاء المحددة في [شروط خدمات Microsoft Online](https://aka.ms/ost):

- Exchange Online محتوى علبة البريد (نص البريد الإلكتروني وإدخالات التقويم ومحتوى مرفقات البريد الإلكتروني)
- SharePoint محتوى الموقع عبر الإنترنت والملفات المخزنة داخل هذا الموقع
- الملفات التي تم تحميلها إلى OneDrive for Business

</details>

### <a name="what-is-in-scope-for-teams-migration"></a>ما هو نطاق الترحيل Teams؟
<details><summary>انقر للتوسيع</summary>

بالإضافة إلى Exchange Online و SharePoint Online و OneDrive for Business; ستقوم Microsoft بترحيل بيانات Teams إلى مركز البيانات المحلي.

- Teams رسائل الدردشة، بما في ذلك الرسائل الخاصة ورسائل القناة.
- Teams الصور المستخدمة في الدردشات.

يتم تخزين ملفات Teams في SharePoint Online ويتم تخزين ملفات الدردشة Teams في OneDrive for Business. يتم تخزين البريد الصوتي والتقويم وجهات الاتصال في Exchange Online. في كثير من الحالات، تستخدم Exchange Online SharePoint Online و OneDrive for Business بالفعل من قبل العميل في الموقع الجغرافي لمركز البيانات المحلي وهي أيضا جزء من برنامج الترحيل Microsoft 365 للبلدان المؤهلة للعملاء.

</details>

### <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>في أي مرحلة اكتملت عملية الترحيل الخاصة بي بحيث يتم تخزين بيانات العميل الأساسية للمستأجر في وضع السكون في الموقع الجغرافي الجديد الخاص بي؟
<details><summary>انقر للتوسيع</summary>

بسبب التبعيات المشتركة بين Exchange Online و SharePoint Online/OneDrive for Business، لا يمكن اعتبار أي ترحيل مكتملا حتى يتم ترحيل كلتا الخدمتين. غالبا ما يتم ترحيل Exchange Online SharePoint Online/OneDrive for Business في أوقات منفصلة وبشكل مستقل عن بعضهما البعض. يتلقى مسؤولو مستأجر العميل تأكيدا في مركز الرسائل عند اكتمال كل عملية ترحيل خدمة ويمكنهم عرض بطاقة موقع البيانات في مركز مسؤول في أي وقت لتأكيد بيانات العميل الأساسية في موقع الراحة لكل خدمة.

</details>

### <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>كيف يمكنك التأكد من أن بيانات العميل آمنة أثناء النقل ومن أنني لن أختبر وقت التعطل؟
<details><summary>انقر للتوسيع</summary>

نقل البيانات هي عملية خدمة خلفية بأقل تأثير على المستخدمين النهائيين. يتم سرد الميزات التي يمكن أن تتأثر في [أثناء وبعد نقل البيانات](during-and-after-your-data-move.md). نحن نلتزم [باتفاقية مستوى خدمة Microsoft Online Services (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) للتوفر بحيث لا يحتاج العملاء إلى الاستعداد أو المراقبة أثناء النقل.

تقوم جميع خدمات Microsoft 365 بتشغيل نفس الإصدارات في مراكز البيانات، حتى تتمكن من التأكد من وجود وظائف متسقة. خدمتك مدعومة بالكامل طوال العملية.

</details>

### <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>ما تأثير وجود خدمات مختلفة في مناطق جغرافية مختلفة؟
<details><summary>انقر للتوسيع</summary>

قد تكون بعض خدمات Microsoft 365 موجودة في مناطق جغرافية مختلفة لبعض العملاء الحاليين والعملاء الذين هم في منتصف عملية النقل. تعمل خدماتنا بشكل مستقل عن بعضها البعض ولا يوجد أي تأثير على تجربة المستخدم إذا كانت هذه هي الحالة. ومع ذلك، لأغراض موقع البيانات، لا يمكن اعتبار ترحيل المستأجر مكتملا حتى يتم ترحيل كل من Exchange Online SharePoint Online/OneDrive for Business إلى نفس جغرافيا لمركز البيانات.

</details>

### <a name="where-is-my-core-customer-data-located"></a>أين توجد بيانات العميل الأساسية؟
<details><summary>انقر للتوسيع</summary>

يمكن لمسؤولي مستأجري العملاء عرض بطاقة موقع البيانات في مركز مسؤول في أي وقت لتأكيد بيانات العميل الأساسية في موقع الراحة لكل خدمة، خاصة للمستأجر الخاص بهم. كما ننشر موقع جغرافيا لمركز البيانات ومراكز البيانات وموقع بيانات العملاء Office 365 على [Microsoft 365 خرائط مركز البيانات التفاعلية](https://office.com/datamaps) كمرجع لبيانات العملاء الأساسية الافتراضية الحالية في مواقع الراحة للمستأجرين الجدد. يمكنك التحقق من موقع بيانات العميل الثابتة عبر قسم "موقع البيانات" ضمن "ملف تعريف المؤسسة" في مركز مسؤولي Microsoft 365.

</details>

### <a name="when-will-i-be-able-to-request-a-move"></a>متى سأتمكن من طلب نقل؟
<details><summary>انقر للتوسيع</summary>

الرجاء الرجوع إلى صفحة ["كيفية طلب نقل البيانات](request-your-data-move.md) " للإطارات الزمنية المدعومة جغرافيا لمركز البيانات.

</details>

### <a name="how-can-i-request-to-be-moved"></a>كيف يمكنني طلب النقل؟
<details><summary>انقر للتوسيع</summary>

سيرى العملاء المؤهلون صفحة في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com/) الخاصة بهم. الرجاء الاطلاع [على كيفية طلب نقل البيانات](request-your-data-move.md) للحصول على إرشادات حول كيفية طلب النقل.

</details>

### <a name="can-i-change-my-selection-after-requesting-a-move"></a>هل يمكنني تغيير التحديد بعد طلب النقل؟
<details><summary>انقر للتوسيع</summary>

لا يمكن لنا إزالتها من العملية بعد إرسال طلبك.

</details>

### <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>ماذا يحدث إذا لم اطلب نقل قبل الموعد النهائي؟
<details><summary>انقر للتوسيع</summary>

لا يمكننا قبول طلبات الترحيل بعد فترة التسجيل المفتوحة.

</details>

### <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>ماذا لو أردت نقل بياناتي للحصول على أداء أفضل للشبكة؟
<details><summary>انقر للتوسيع</summary>

التقارب المادي لمركز بيانات Microsoft 365 ليس ضمانا لأداء أفضل للشبكات. هناك العديد من العوامل والمكونات التي تؤثر على أداء الشبكة بين المستخدم النهائي وخدمة Microsoft 365. لمزيد من المعلومات حول هذا الأمر وضبط الأداء، راجع [تخطيط الشبكة وضبط الأداء Microsoft 365](network-planning-and-performance.md).

</details>

### <a name="do-all-the-services-move-their-data-on-the-same-day"></a>هل تنقل جميع الخدمات بياناتها في نفس اليوم؟
<details><summary>انقر للتوسيع</summary>

تتحرك كل خدمة بشكل مستقل ومن المحتمل أن تنقل بياناتها في أوقات مختلفة.

</details>

### <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>هل يمكنني الاختيار عندما أرغب في نقل بياناتي؟
<details><summary>انقر للتوسيع</summary>

لا يمكن للعملاء تحديد تاريخ معين، ولا يمكنهم تأخير نقلهم، ولا يمكننا مشاركة تاريخ أو إطار زمني محدد للتحركات.

</details>

### <a name="can-you-share-when-my-data-will-be-moved"></a>هل يمكنك مشاركة وقت نقل بياناتي؟
<details><summary>انقر للتوسيع</summary>

تعد عمليات نقل البيانات عملية خلفية بأقل تأثير على المستخدمين النهائيين. يمنعنا التعقيد والدقة والحجم الذي نحتاج إليه لتنفيذ عمليات نقل البيانات داخل بيئة يتم تشغيلها عالميا وتلقائيا من المشاركة عند توقع اكتمال نقل البيانات للمستأجر الخاص بك أو أي مستأجر واحد آخر. سيتلقى العملاء تأكيدا واحدا في مركز الرسائل لكل خدمة مشاركة عند اكتمال نقل البيانات.

</details>

### <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>ماذا يحدث إذا تمكن المستخدمون من الوصول إلى الخدمات أثناء نقل البيانات؟
<details><summary>انقر للتوسيع</summary>

راجع [أثناء نقل البيانات وبعده](during-and-after-your-data-move.md) للحصول على قائمة كاملة من الميزات التي قد تكون محدودة أثناء نقل أجزاء من البيانات لكل خدمة.

</details>

### <a name="how-do-i-know-the-move-is-complete"></a>كيف أعمل تعرف أن النقل مكتمل؟
<details><summary>انقر للتوسيع</summary>

شاهد Microsoft 365 Message Center للتأكيد على اكتمال نقل بيانات كل خدمة. عند نقل بيانات كل خدمة، سنقوم بنشر إشعار الإكمال حتى تحصل على ثلاثة إشعارات إكمال: واحدة لكل Exchange Online، SharePoint Online، و Skype for Business Online. يمكنك أيضا التحقق من موقع بيانات العميل الثابتة عبر قسم "موقع البيانات" ضمن "ملف تعريف المؤسسة" في مركز مسؤولي Microsoft 365.

</details>

### <a name="i-am-a-microsoft-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>أنا عميل Microsoft 365 في إحدى المناطق الجغرافية الجديدة لمركز البيانات، ولكن عندما قمت بالتسجيل، قمت باختيار بلد آخر. كيف يمكن نقلي إلى جغرافيا لمركز البيانات الجديد؟
<details><summary>انقر للتوسيع</summary>

لا يمكن تغيير بلد التسجيل المقترن بالمستأجر. بدلا من ذلك، تحتاج إلى إنشاء مستأجر Microsoft 365 جديد باشتراك جديد ونقل المستخدمين والبيانات يدويا إلى المستأجر الجديد.

</details>

### <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-microsoft-365-during-the-exchange-online-move"></a>ماذا يحدث إذا كنا بصدد ترحيل بيانات البريد الإلكتروني إلى Microsoft 365 أثناء نقل Exchange Online؟
<details><summary>انقر للتوسيع</summary>

هذا سيناريو شائع جدا ومدعم بالكامل. لا يتداخل الترحيل السحابي بين المناطق الجغرافية لمركز البيانات مع أي عمليات ترحيل محلية لعلب بريد السحابة.

</details>

### <a name="can-i-pilot-some-users"></a>هل يمكنني تجربة بعض المستخدمين؟
<details><summary>انقر للتوسيع</summary>

يمكنك إنشاء مستأجر تجريبي منفصل لاختبار الاتصال، ولكن لا يمكن دمج المستأجر التجريبي بأي طريقة مع المستأجر الحالي.

</details>

### <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>لا أريد الانتظار حتى تقوم Microsoft بنقل بياناتي. هل يمكنني فقط إنشاء مستأجر جديد ونقل نفسي؟
<details><summary>انقر للتوسيع</summary>

نعم، ومع ذلك، لن تكون العملية سلسة كما لو كانت Microsoft ستقوم بنقل البيانات.

إذا قمت بإنشاء مستأجر جديد بعد توفر جغرافيا لمركز البيانات الجديد، فسيتم استضافة المستأجر الجديد في المنطقة الجغرافية الجديدة. هذا المستأجر الجديد منفصل تماما عن المستأجر السابق وستكون مسؤولا عن نقل جميع علب بريد المستخدمين ومحتوى الموقع وأسماء المجالات وأي بيانات أخرى. لاحظ أنه لا يمكنك نقل اسم المستأجر من مستأجر إلى آخر. نوصي بالانتظار حتى يتم تشغيل برنامج النقل الذي توفره Microsoft لأننا سنهتم بنقل جميع الإعدادات والبيانات والاشتراكات للمستخدمين.

</details>

### <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>تم بالفعل نقل بيانات عميلي إلى جغرافيا لمركز بيانات جديد. هل يمكنني العودة؟
<details><summary>انقر للتوسيع</summary>

لا، هذا غير ممكن. لا يمكن نقل العملاء الذين تم نقلهم إلى مراكز بيانات جغرافية جديدة مرة أخرى. كعميل في أي جغرافيا، سوف تواجه نفس جودة الخدمة والأداء وعناصر التحكم في الأمان كما فعلت من قبل. [Microsoft 365 يتوفر Multi Geo](https://aka.ms/multi-geo) لبعض العملاء كوظيفة إضافية ويسمح لمستأجر واحد بإنشاء مناطق جغرافية متعددة للأقمار الصناعية ونقل بيانات المستخدم إلى تلك المناطق الجغرافية مع التزامات موقع البيانات.

</details>

### <a name="will-microsoft-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>هل سيكون Microsoft 365 المستأجرون المستضافون في مراكز البيانات الجديدة متاحين للمستخدمين خارج البلد؟
<details><summary>انقر للتوسيع</summary>

نعم. تحتفظ Microsoft بشبكة عالمية كبيرة مع اتصالات عامة بالإنترنت في أكثر من 130 موقعا في 35 دولة حول العالم مع اتفاقيات تناظر مع أكثر من 2700 موفر خدمة إنترنت (ISPs). سيتمكن المستخدمون من الوصول إلى مراكز البيانات من أي مكان يتواجدون فيه على الإنترنت.

</details>

### <a name="my-tenant-has-configured-the-multi-geo-add-on-can-i-still-enroll-in-my-tenant-in-the-microsoft-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>قام المستأجر الخاص بي بتكوين الوظيفة الإضافية Multi Geo. هل يمكنني الاستمرار في التسجيل في المستأجر في Microsoft 365 Move Program؟ لتغيير الموقع الجغرافي الافتراضي ونقل أي مستخدم ليس في منطقة الأقمار الصناعية إلى الموقع الجغرافي الافتراضي الجديد؟
<details><summary>انقر للتوسيع</summary>

نعم، المستأجر الخاص بك مؤهل للتسجيل ولكن هناك اعتبارات كبيرة لأن النقل على مستوى المستأجر غير مدعوم بالكامل للعملاء الذين قاموا بتكوين [Multi-Geo](https://aka.ms/multi-geo).

لا يمكن SharePoint Online و OneDrive for Business الترحيل إلى جغرافيا لمركز البيانات الجديد على مستوى المستأجر من خلال هذا البرنامج. يمكن لمسؤول العميل تكوين مشاركات OneDrive for Business للانتقال إلى أي منطقة متوفرة باستخدام Multi-Geo، ولكن لا يمكن تغيير الموقع الافتراضي للمستأجر بمجرد تكوين Multi-Geo لمستأجر.

للعملاء الذين يختارون الترحيل - سنقوم بنقل جميع علب البريد Exchange Online من الموقع الجغرافي الافتراضي الحالي إلى جغرافيا لمركز البيانات المحلي الجديد وتحديث منطقة Exchange Online الافتراضية. لن ننقل أي علب بريد EXO تم تكوينها في مناطق الأقمار الصناعية متعددة المناطق الجغرافية لمواصلة احترام موقع بيانات منطقة الأقمار الصناعية كما كنت تنوي.  Teams عمليات ترحيل مستأجر خدمة الدردشة للعملاء الذين يعانون من تكوين Multi Geo تتصرف بطريقة مماثلة Exchange Online.

</details>

### <a name="i-have-public-folders-deployed-in-my-tenant-what-will-be-the-impact-on-public-folder-access-during-or-after-the-move"></a>لدي مجلدات عامة تم نشرها في المستأجر الخاص بي. ما تأثير ذلك على الوصول إلى المجلدات العامة أثناء النقل أو بعده؟
<details><summary>انقر للتوسيع</summary>

لا يوجد أي تأثير على وصول المستخدمين النهائيين إلى المجلدات العامة أثناء نقل المجلدات العامة أو بعده. ومع ذلك، قد لا تتوفر المجلدات العامة للإدارة في أداة مركز Exchange مسؤول حتى يتم نقل كافة علب بريد المجلدات العامة في نفس المنطقة. الرجاء مراجعة [هذه المقالة](https://aka.ms/pfxrf) للحصول على مزيد من التفاصيل.

</details>

### <a name="related-topics"></a>المواضيع ذات الصلة

[نقل البيانات الأساسية إلى جغرافيا لمركز بيانات Microsoft 365 جديد](moving-data-to-new-datacenter-geos.md)

[كيفية طلب نقل البيانات](request-your-data-move.md)

[Microsoft 365 متعدد الجغرافيا](https://aka.ms/multi-geo)

[Microsoft 365 خريطة مركز البيانات التفاعلية](https://office.com/datamaps)

[دعم Microsoft 365](../admin/get-help-support.md)

[جغرافيا لمركز بيانات جديد Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions)

[خدمات Azure حسب المنطقة](https://azure.microsoft.com/regions/)
