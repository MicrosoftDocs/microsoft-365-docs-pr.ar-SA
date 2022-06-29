---
title: استخدام Office 365 Content Delivery Network (CDN) مع SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/13/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: تعرف على كيفية استخدام Office 365 Content Delivery Network (CDN) لتسريع تسليم أصول SharePoint Online.
ms.openlocfilehash: 19a6ef51c73340c9f048ffa60208a5216a1959db
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492502"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>استخدام شبكة تسليم المحتوى Office 365 (CDN) مع SharePoint Online

يمكنك استخدام Office 365 Content Delivery Network (CDN) المضمنة لاستضافة الأصول الثابتة لتوفير أداء أفضل لصفحات SharePoint Online. يحسن Office 365 CDN الأداء عن طريق تخزين الأصول الثابتة مؤقتا بالقرب من المستعرضات التي تطلبها، ما يساعد على تسريع التنزيلات وتقليل زمن الانتقال. أيضا، يستخدم Office 365 CDN [بروتوكول HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) لتحسين الضغط والبنية الأساسية لبرنامج ربط العمليات التجارية ل HTTP. يتم تضمين خدمة Office 365 CDN كجزء من اشتراكك في SharePoint Online.

> [!NOTE]
> تتوفر Office 365 CDN فقط للمستأجرين في سحابة **الإنتاج** (في جميع أنحاء العالم). لا يدعم المستأجرون في سحابة حكومة الولايات المتحدة والصين حاليا Office 365 CDN.

تتكون Office 365 CDN من شبكات تسليم المحتوى المتعددة التي تسمح لك باستضافة الأصول الثابتة في مواقع أو _أصول_ متعددة، وخدمتها من شبكات عالمية عالية السرعة. استنادا إلى نوع المحتوى الذي تريد استضافته في Office 365 CDN، يمكنك إضافة أصول **عامة** أو أصول **خاصة** أو كليهما. راجع [اختيار ما إذا كان يجب أن يكون كل أصل عاما أو خاصا](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) لمزيد من المعلومات حول الفرق بين الأصول العامة والخاصة.

![رسم تخطيطي تصوري Office 365 CDN.](../media/O365-CDN/o365-cdn-flow-transparent.png "رسم تخطيطي تصوري Office 365 CDN")

إذا كنت على دراية بالفعل بالطريقة التي تعمل بها شبكات تسليم المحتوى، فستحتاج فقط إلى إكمال بعض الخطوات لتمكين Office 365 CDN للمستأجر الخاص بك. يصف هذا الموضوع كيفية القيام بذلك. تابع القراءة للحصول على معلومات حول كيفية البدء في استضافة الأصول الثابتة.

> [!TIP]
> هناك شبكات CDN أخرى مستضافة من Microsoft يمكن استخدامها مع Office 365 لسيناريوهات الاستخدام المتخصصة، ولكن لا تتم مناقشتها في هذا الموضوع لأنها تقع خارج نطاق Office 365 CDN. لمزيد من المعلومات، راجع [شبكات تسليم المحتوى الأخرى من Microsoft](content-delivery-networks.md#other-microsoft-cdns).

 **عد إلى [تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>نظرة عامة حول العمل مع Office 365 CDN في SharePoint Online

لإعداد Office 365 CDN لمؤسستك، اتبع الخطوات الأساسية التالية:

+ [التخطيط لتوزيع شبكة تسليم المحتوى Office 365](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [تحديد الأصول الثابتة التي تريد استضافتها على شبكة تسليم المحتوى](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [حدد المكان الذي تريد تخزين أصولك](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets) فيه. يمكن أن يكون هذا الموقع موقعا أو مكتبة أو مجلدا في SharePoint ويطلق عليه اسم _الأصل_.
  + [اختر ما إذا كان يجب أن يكون كل أصل عاما أو خاصا](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). يمكنك إضافة أصول متعددة لكل من الأنواع العامة والخاصة.

+ إعداد وتكوين شبكة تسليم المحتوى، باستخدام إما PowerShell أو CLI ل Microsoft 365

  + [إعداد وتكوين شبكة تسليم المحتوى باستخدام SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [إعداد وتكوين شبكة تسليم المحتوى باستخدام PnP PowerShell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [إعداد وتكوين شبكة تسليم المحتوى باستخدام CLI ل Microsoft 365](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  عند إكمال هذه الخطوة، سيكون لديك:

  + تمكين شبكة تسليم المحتوى لمؤسستك.
  + أضف أصولك، مع تحديد كل أصل على أنه عام أو خاص.

بمجرد الانتهاء من الإعداد، يمكنك [إدارة شبكة تسليم المحتوى Office 365](use-microsoft-365-cdn-with-spo.md#CDNManage) بمرور الوقت عن طريق:

+ إضافة الأصول وتحديثها وإزالتها
+ إضافة الأصول وإزالتها
+ تكوين نهج شبكة تسليم المحتوى
+ تعطيل شبكة تسليم المحتوى إذا لزم الأمر

وأخيرا، راجع [استخدام أصول شبكة تسليم المحتوى للتعرف](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) على كيفية الوصول إلى أصول شبكة تسليم المحتوى من الأصول العامة والخاصة.

راجع [استكشاف أخطاء Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) وإصلاحها للحصول على إرشادات حول حل المشكلات الشائعة.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>التخطيط لتوزيع شبكة تسليم المحتوى Office 365

قبل نشر Office 365 CDN لمستأجر Office 365 الخاص بك، يجب مراعاة العوامل التالية كجزء من عملية التخطيط الخاصة بك.

  + [تحديد الأصول الثابتة التي تريد استضافتها على شبكة تسليم المحتوى](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [تحديد المكان الذي تريد تخزين أصولك فيه](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [اختر ما إذا كان يجب أن يكون كل أصل عاما أو خاصا](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>تحديد الأصول الثابتة التي تريد استضافتها على شبكة تسليم المحتوى

بشكل عام، تعتبر شبكات تسليم المحتوى أكثر فعالية لاستضافة _الأصول الثابتة_، أو الأصول التي لا تتغير في كثير من الأحيان. القاعدة الجيدة هي تحديد الملفات التي تلبي بعض هذه الشروط أو كلها:

+ الملفات الثابتة المضمنة في صفحة (مثل البرامج النصية والصور) التي قد يكون لها تأثير تزايدي كبير على أوقات تحميل الصفحة
+ ملفات كبيرة مثل الملفات التنفيذية وملفات التثبيت
+ مكتبات الموارد التي تدعم التعليمات البرمجية من جانب العميل

على سبيل المثال، يمكن للملفات الصغيرة التي يتم طلبها بشكل متكرر مثل صور الموقع والبرامج النصية تحسين أداء عرض الموقع بشكل كبير وتقليل الحمل بشكل متزايد على مواقع SharePoint Online عند إضافتها إلى أصل شبكة تسليم المحتوى. يمكن تنزيل الملفات الكبيرة مثل الملفات التنفيذية للتثبيت من شبكة تسليم المحتوى، مما يؤدي إلى تأثير إيجابي على الأداء وتقليل الحمل على موقع SharePoint Online، حتى لو لم يتم الوصول إليها في كثير من الأحيان.

يعتمد تحسين الأداء على أساس كل ملف على العديد من العوامل، بما في ذلك قرب العميل من أقرب نقطة نهاية شبكة تسليم المحتوى، والشروط العابرة على الشبكة المحلية، وما إلى ذلك. العديد من الملفات الثابتة صغيرة جدا، ويمكن تنزيلها من Office 365 في أقل من ثانية. ومع ذلك، قد تحتوي صفحة ويب على العديد من الملفات المضمنة مع وقت تنزيل تراكمي لعدة ثوان. يمكن أن يؤدي تقديم هذه الملفات من شبكة تسليم المحتوى إلى تقليل وقت تحميل الصفحة الإجمالي بشكل كبير. راجع [ما هي مكاسب الأداء التي توفرها شبكة تسليم المحتوى؟](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) على سبيل المثال.

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>تحديد المكان الذي تريد تخزين أصولك فيه

تقوم شبكة تسليم المحتوى بإحضار أصولك من موقع يسمى _الأصل_. يمكن أن يكون الأصل موقع SharePoint أو مكتبة مستندات أو مجلدا يمكن الوصول إليه بواسطة عنوان URL. تتمتع بمرونة كبيرة عند تحديد الأصول لمؤسستك. على سبيل المثال، يمكنك تحديد أصول متعددة أو أصل واحد حيث تريد وضع جميع أصول شبكة تسليم المحتوى. يمكنك اختيار الحصول على أصول عامة أو خاصة لمؤسستك. ستختار معظم المؤسسات تنفيذ مزيج من الاثنين.

يمكنك إنشاء حاوية جديدة لأصولك مثل المجلدات أو مكتبات المستندات، وإضافة الملفات التي تريد توفيرها من شبكة تسليم المحتوى. هذا نهج جيد إذا كان لديك مجموعة محددة من الأصول التي تريد أن تكون متوفرة من شبكة تسليم المحتوى، وتريد تقييد مجموعة أصول شبكة تسليم المحتوى لتلك الملفات فقط في الحاوية.

يمكنك أيضا تكوين مجموعة مواقع مشتركة أو موقع أو مكتبة أو مجلد موجود كأصل، مما سيجعل جميع الأصول المؤهلة في الحاوية متوفرة من شبكة تسليم المحتوى. قبل إضافة حاوية موجودة كأصل، من المهم التأكد من أنك على دراية بمحتوياتها وأذوناتها حتى لا تعرض الأصول دون قصد للوصول المجهول أو المستخدمين غير المصرح لهم.

يمكنك تعريف _نهج شبكة تسليم المحتوى_ لاستبعاد المحتوى في أصولك من شبكة تسليم المحتوى. تستثني نهج CDN الأصول في الأصول العامة أو الخاصة حسب سمات مثل _نوع الملف_ _وتصنيف الموقع_، ويتم تطبيقها على جميع أصول CdnType (خاص أو عام) الذي تحدده في النهج. على سبيل المثال، إذا أضفت أصل خاص يتكون من موقع يحتوي على مواقع فرعية متعددة، يمكنك تحديد نهج لاستبعاد المواقع التي تم وضع علامة **عليها كسرية** حتى لا يتم تقديم المحتوى من المواقع التي تم تطبيق هذا التصنيف عليها من شبكة تسليم المحتوى. سيتم تطبيق النهج على المحتوى من _جميع_ الأصول الخاصة التي أضفتها إلى شبكة تسليم المحتوى.

ضع في اعتبارك أنه كلما زاد عدد الأصول، زاد التأثير على الوقت الذي تستغرقه خدمة CDN لمعالجة الطلبات. نوصي بتحديد عدد الأصول قدر الإمكان.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>اختر ما إذا كان يجب أن يكون كل أصل عاما أو خاصا

عند تحديد أصل، يمكنك تحديد ما إذا كان يجب جعله _عاما_ أو _خاصا_. الوصول إلى أصول CDN في الأصول العامة مجهول، ويتم تأمين محتوى شبكة تسليم المحتوى في الأصول الخاصة بواسطة الرموز المميزة التي تم إنشاؤها ديناميكيا لمزيد من الأمان. بغض النظر عن الخيار الذي تختاره، تقوم Microsoft بكل الأحمال الثقيلة لك عندما يتعلق الأمر بإدارة شبكة تسليم المحتوى نفسها. يمكنك أيضا تغيير رأيك لاحقا، بعد إعداد شبكة تسليم المحتوى وتحديد أصولك.

يوفر كل من الخيارات العامة والخاصة مكاسب أداء مماثلة، ولكن كل منها له سمات ومزايا فريدة.

يمكن الوصول إلى الأصول **العامة** داخل Office 365 CDN بشكل مجهول، ويمكن الوصول إلى الأصول المستضافة من قبل أي شخص لديه عنوان URL إلى الأصل. نظرا لأن الوصول إلى المحتوى في الأصول العامة مجهول، يجب عليك استخدامه فقط لتخزين المحتوى العام غير الحساس مؤقتا مثل ملفات JavaScript والبرامج النصية والأيقونات والصور.

توفر الأصول **الخاصة** داخل Office 365 CDN وصولا خاصا إلى محتوى المستخدم مثل مكتبات مستندات SharePoint Online والمواقع والصور الخاصة. يتم تأمين الوصول إلى المحتوى في الأصول الخاصة بواسطة الرموز المميزة التي تم إنشاؤها ديناميكيا بحيث لا يمكن الوصول إليها إلا من قبل المستخدمين الذين لديهم أذونات لمكتبة المستندات الأصلية أو موقع التخزين. يمكن استخدام الأصول الخاصة في Office 365 CDN فقط لمحتوى SharePoint Online، ويمكنك فقط الوصول إلى الأصول في الأصول الخاصة من خلال إعادة التوجيه من مستأجر SharePoint Online.

يمكنك قراءة المزيد حول كيفية عمل وصول شبكة تسليم المحتوى إلى الأصول في أصل خاص في [استخدام الأصول في الأصول الخاصة](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>سمات ومزايا استضافة الأصول في الأصول العامة

+ يمكن للجميع الوصول إلى الأصول المعروضة في أصل عام بشكل مجهول.
    > [!IMPORTANT]
    > يجب عدم وضع الموارد التي تحتوي على معلومات المستخدم أو التي تعتبر حساسة لمؤسستك في أصل عام.

+ إذا قمت بإزالة أصل من أصل عام، فقد يستمر توفر الأصل لمدة تصل إلى 30 يوما من ذاكرة التخزين المؤقت؛ ومع ذلك، سنقوم ببطلان الارتباطات إلى الأصل في شبكة تسليم المحتوى في غضون 15 دقيقة.

+ عند استضافة أوراق الأنماط (ملفات CSS) في أصل عام، يمكنك استخدام المسارات النسبية وعناوين URL داخل التعليمات البرمجية. وهذا يعني أنه يمكنك الرجوع إلى موقع صور الخلفية والعناصر الأخرى بالنسبة إلى موقع الأصل الذي يستدعيه.

+ بينما يمكنك إنشاء عنوان URL للأصل العام، يجب عليك المتابعة بحذر والتأكد من استخدام خاصية سياق الصفحة واتباع الإرشادات للقيام بذلك. والسبب في ذلك هو أنه إذا أصبح الوصول إلى شبكة تسليم المحتوى غير متوفر، فلن يتم حل URL تلقائيا لمؤسستك في SharePoint Online وقد ينتج عنه ارتباطات مقطوعة وأخطاء أخرى. كما أن عنوان URL عرضة للتغيير ولهذا السبب يجب ألا يكون مجرد تعليمة برمجية ثابتة إلى قيمته الحالية.

+ أنواع الملفات الافتراضية المضمنة في الأصول العامة هي .css و.eot و .gif و.ico و.jpeg و .jpg و .js و.map و .png و.svg و.ttf و.woff و.woff2. يمكنك تحديد أنواع ملفات إضافية.

+ يمكنك تكوين نهج لاستبعاد الأصول التي تم تحديدها بواسطة تصنيفات المواقع التي تحددها. على سبيل المثال، يمكنك اختيار استبعاد كافة الأصول التي تم وضع علامة عليها على أنها "سرية" أو "مقيدة" حتى لو كانت نوع ملف مسموح به وموجودة في أصل عام.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>سمات ومزايا استضافة الأصول في الأصول الخاصة

+ يمكن استخدام الأصول الخاصة لأصول SharePoint Online فقط.

+ يمكن للمستخدمين الوصول إلى الأصول من أصل خاص فقط إذا كان لديهم أذونات للوصول إلى الحاوية. يتم منع الوصول المجهول إلى هذه الأصول.

+ يجب الإشارة إلى الأصول في الأصول الخاصة من مستأجر SharePoint Online. لا يعمل الوصول المباشر إلى أصول شبكة تسليم المحتوى الخاصة.

+ إذا قمت بإزالة أصل من الأصل الخاص، فقد يستمر توفر الأصل لمدة تصل إلى ساعة من ذاكرة التخزين المؤقت؛ ومع ذلك، سنقوم بإبطال الارتباطات إلى الأصل في شبكة تسليم المحتوى في غضون 15 دقيقة من إزالة الأصل.

+ أنواع الملفات الافتراضية المضمنة في الأصول الخاصة هي .gif و.ico و.jpeg و .jpg و .js و .png. يمكنك تحديد أنواع ملفات إضافية.

+ تماما كما هو الحال مع الأصول العامة، يمكنك تكوين نهج لاستبعاد الأصول التي تم تحديدها بواسطة تصنيفات المواقع التي تحددها حتى إذا كنت تستخدم أحرف البدل لتضمين جميع الأصول داخل مجلد أو مكتبة مستندات.

لمزيد من المعلومات حول سبب استخدام Office 365 CDN ومفاهيم CDN العامة وشبكات تسليم المحتوى الأخرى التي يمكنك استخدامها مع مستأجر Office 365، راجع [شبكات تسليم المحتوى](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>أصول CDN الافتراضية

ما لم تحدد خلاف ذلك، Office 365 إعداد بعض الأصول الافتراضية لك عند تمكين Office 365 CDN. إذا اخترت في البداية عدم توفيرها، يمكنك إضافة هذه الأصول بعد إكمال الإعداد. ما لم تفهم عواقب تخطي إعداد الأصول الافتراضية ولديك سبب محدد للقيام بذلك، يجب أن تسمح بإنشائها عند تمكين شبكة تسليم المحتوى.

أصول شبكة تسليم المحتوى الخاصة الافتراضية:

+ \*/userphoto.aspx
+ \*/siteassets

أصول شبكة تسليم المحتوى العامة الافتراضية:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _clientideassets_ هو أصل عام افتراضي تمت إضافته إلى خدمة Office 365 CDN في ديسمبر 2017. يجب أن يكون هذا الأصل موجودا لكي تعمل إطار عمل SharePoint الحلول في شبكة تسليم المحتوى. إذا قمت بتمكين Office 365 CDN قبل ديسمبر 2017، أو إذا تخطيت إعداد الأصول الافتراضية عند تمكين CDN، يمكنك إضافة هذا الأصل يدويا. لمزيد من المعلومات، راجع [جزء ويب الخاص بي من جانب العميل أو إطار عمل SharePoint الحل لا يعمل](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>إعداد وتكوين Office 365 CDN باستخدام SharePoint Online Management Shell

تتطلب الإجراءات الواردة في هذا القسم استخدام SharePoint Online Management Shell للاتصال ب SharePoint Online. للحصول على الإرشادات، راجع [الاتصال ب SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

أكمل هذه الخطوات لإعداد وتكوين شبكة تسليم المحتوى لاستضافة أصولك في SharePoint Online باستخدام SharePoint Online Management Shell.

<details>
  <summary>انقر للتوسيع</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>تمكين مؤسستك من استخدام Office 365 CDN

قبل إجراء تغييرات على إعدادات شبكة تسليم المحتوى للمستأجر، يجب استرداد الحالة الحالية لتكوين شبكة تسليم المحتوى الخاصة في مستأجر Office 365. الاتصال بالمستأجر باستخدام SharePoint Online Management Shell:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

الآن استخدم **الأمر cmdlet Get-SPOTenantCdnEnabled** لاسترداد إعدادات حالة شبكة تسليم المحتوى من المستأجر:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

سيتم إخراج حالة CDN ل CdnType المحدد إلى الشاشة.

استخدم **Set-SPOTenantCdnEnabled** cmdlet لتمكين مؤسستك من استخدام شبكة تسليم المحتوى Office 365. يمكنك تمكين مؤسستك من استخدام الأصول العامة أو الأصول الخاصة أو كليهما في الوقت نفسه. يمكنك أيضا تكوين شبكة تسليم المحتوى لتخطي إعداد الأصول الافتراضية عند تمكينها. يمكنك دائما إضافة هذه الأصول لاحقا كما هو موضح في هذا الموضوع.

في Windows PowerShell ل SharePoint Online:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

على سبيل المثال، لتمكين مؤسستك من استخدام الأصول العامة والخاصة، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

لتمكين مؤسستك من استخدام الأصول العامة والخاصة ولكن تخطي إعداد الأصول الافتراضية، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

راجع [أصول CDN الافتراضية](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) للحصول على معلومات حول الأصول التي يتم توفيرها بشكل افتراضي عند تمكين Office 365 CDN، والتأثير المحتمل لتخطي إعداد الأصول الافتراضية.

لتمكين مؤسستك من استخدام الأصول العامة، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

لتمكين مؤسستك من استخدام الأصول الخاصة، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

لمزيد من المعلومات حول أمر cmdlet هذا، راجع [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>تغيير قائمة أنواع الملفات لتضمينها في Office 365 CDN (اختياري)

> [!TIP]
> عند تعريف أنواع الملفات باستخدام **Cmdlet Set-SPOTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد إضافة أنواع ملفات إضافية إلى القائمة، فاستخدم cmdlet أولا لمعرفة أنواع الملفات المسموح بها بالفعل وتضمينها في القائمة مع أنواع الملفات الجديدة.

استخدم **Set-SPOTenantCdnPolicy** cmdlet لتعريف أنواع الملفات الثابتة التي يمكن استضافتها بواسطة الأصول العامة والخاصة في شبكة تسليم المحتوى. بشكل افتراضي، يتم السماح بأنواع الأصول الشائعة، على سبيل المثال.css، .gif، .jpg، .js.

في Windows PowerShell ل SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

على سبيل المثال، لتمكين CDN من استضافة ملفات .css والملفات .png، يمكنك إدخال الأمر:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

لمعرفة أنواع الملفات المسموح بها حاليا بواسطة شبكة تسليم المحتوى، استخدم **الأمر Get-SPOTenantCdnPolicies** cmdlet:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

لمزيد من المعلومات حول أوامر cmdlets هذه، راجع [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) و [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>تغيير قائمة تصنيفات المواقع التي تريد استبعادها من شبكة تسليم المحتوى Office 365 (اختياري)

> [!TIP]
> عند استبعاد تصنيفات المواقع باستخدام **Cmdlet Set-SPOTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت ترغب في استبعاد تصنيفات مواقع إضافية، فاستخدم cmdlet أولا لمعرفة التصنيفات التي تم استبعادها بالفعل ثم إضافتها مع التصنيفات الجديدة.

استخدم **Set-SPOTenantCdnPolicy** cmdlet لاستبعاد تصنيفات المواقع التي لا تريد توفيرها عبر شبكة تسليم المحتوى. بشكل افتراضي، لا يتم استبعاد تصنيفات المواقع.

في Windows PowerShell ل SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

لمعرفة تصنيفات المواقع المقيدة حاليا، استخدم **الأمر Get-SPOTenantCdnPolicies** cmdlet:

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

الخصائص التي سيتم إرجاعها هي _IncludeFileExtensions_ و _ExcludeRestrictedSiteClassifications_ و _ExcludeIfNoScriptDisabled_.

تحتوي _الخاصية IncludeFileExtensions_ على قائمة ملحقات الملفات التي سيتم تقديمها من شبكة تسليم المحتوى.

> [!NOTE]
> تختلف ملحقات الملفات الافتراضية بين العامة والخاصة.

تحتوي الخاصية _ExcludeRestrictedSiteClassifications_ على تصنيفات المواقع التي تريد استبعادها من شبكة تسليم المحتوى. على سبيل المثال، يمكنك استبعاد المواقع التي تم وضع علامة **"سري** " عليها بحيث لا يتم تقديم المحتوى من المواقع التي تم تطبيق هذا التصنيف عليها من شبكة تسليم المحتوى.

تستثني _الخاصية ExcludeIfNoScriptDisabled_ المحتوى من شبكة تسليم المحتوى استنادا إلى إعدادات السمة _NoScript_ على مستوى الموقع. بشكل افتراضي، يتم تعيين السمة _NoScript_ إلى **"ممكن** للمواقع _الحديثة_ " و" **معطل** للمواقع _الكلاسيكية_ ". يعتمد هذا على إعدادات المستأجر.

لمزيد من المعلومات حول أوامر cmdlets هذه، راجع [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) و [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>إضافة أصل لأصولك

استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف أصل. يمكنك تحديد أصول متعددة. الأصل هو URL يشير إلى مكتبة أو مجلد SharePoint يحتوي على الأصول التي تريد استضافتها بواسطة شبكة تسليم المحتوى.

> [!IMPORTANT]
> يجب عدم وضع الموارد التي تحتوي على معلومات المستخدم أو التي تعتبر حساسة لمؤسستك في أصل عام.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

قيمة _المسار_ هي المسار النسبي للمكتبة أو المجلد الذي يحتوي على الأصول. يمكنك استخدام أحرف البدل بالإضافة إلى المسارات النسبية. تدعم الأصول أحرف البدل الملحقة ب URL. يسمح لك هذا بإنشاء أصول تمتد عبر مواقع متعددة. على سبيل المثال، لتضمين كافة الأصول في مجلد الصفحات الرئيسية لكافة مواقعك كأصل عام داخل شبكة تسليم المحتوى، اكتب الأمر التالي:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ يمكن استخدام معدل حرف البدل ***/** فقط في بداية المسار، وسيتطابق مع كافة مقاطع URL ضمن عنوان URL المحدد.
+ يمكن أن يشير المسار إلى مكتبة مستندات أو مجلد أو موقع. على سبيل المثال، سيتطابق المسار _*/site1_ مع كافة مكتبات المستندات الموجودة ضمن الموقع.

يمكنك إضافة أصل بمسار نسبي محدد. لا يمكنك إضافة أصل باستخدام المسار الكامل.

يضيف هذا المثال أصل خاص لمكتبة مجموعات المواقع على موقع معين:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

يضيف هذا المثال أصل خاص لمجلد _folder1_ في مكتبة أصول المواقع المشتركة لمجموعة المواقع المشتركة:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

إذا كانت هناك مسافة في المسار، يمكنك إما إحاطة المسار بعلامات اقتباس مزدوجة أو استبدال المساحة برمز URL ٪20. تضيف الأمثلة التالية أصل خاص لمجلد _المجلد 1_ في مكتبة أصول المواقع المشتركة لمجموعة المواقع المشتركة:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> في الأصول الخاصة، يجب أن يكون للأصول التي تتم مشاركتها من أصل إصدار رئيسي منشور قبل أن تتمكن من الوصول إليها من شبكة تسليم المحتوى.

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>مثال: تكوين أصل عام للصفحات الرئيسية ومكتبة الأنماط ل SharePoint Online

عادة، يتم إعداد هذه الأصول لك بشكل افتراضي عند تمكين Office 365 CDN. ومع ذلك، إذا كنت تريد تمكينها يدويا، فاتبع هذه الخطوات.

+ استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف مكتبة الأنماط كأصل عام.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف الصفحات الرئيسية كأصل عام.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>مثال: تكوين أصل خاص لأصول الموقع وصفحات الموقع وصور النشر ل SharePoint Online

+ استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف مجلد أصول الموقع كأصل خاص.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف مجلد صفحات الموقع كأصل خاص.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف مجلد صور النشر كأصل خاص.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>مثال: تكوين أصل خاص لمجموعة مواقع مشتركة ل SharePoint Online

استخدم **cmdlet Add-SPOTenantCdnOrigin** لتعريف مجموعة مواقع مشتركة كأصل خاص. على سبيل المثال:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد ترى رسالة _"التكوين" المعلقة_ المتوقعة مع اتصال مستأجر SharePoint Online بخدمة CDN. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>إدارة Office 365 CDN

بمجرد إعداد شبكة تسليم المحتوى، يمكنك إجراء تغييرات على التكوين أثناء تحديث المحتوى أو مع تغير احتياجاتك، كما هو موضح في هذا القسم.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>إضافة أصول أو تحديثها أو إزالتها من Office 365 CDN

بمجرد الانتهاء من خطوات الإعداد، يمكنك إضافة أصول جديدة وتحديث الأصول الموجودة أو إزالتها كلما أردت. ما عليك سوى إجراء تغييرات على الأصول الموجودة في المجلد أو مكتبة SharePoint التي حددتها كأصل. إذا قمت بإضافة أصل جديد، فإنه يتوفر من خلال شبكة تسليم المحتوى على الفور. ومع ذلك، إذا قمت بتحديث الأصل، سيستغرق نشر النسخة الجديدة وتوافرها في شبكة تسليم المحتوى ما يصل إلى 15 دقيقة.

إذا كنت بحاجة إلى استرداد موقع الأصل، يمكنك استخدام **Get-SPOTenantCdnOrigins** cmdlet. للحصول على معلومات حول كيفية استخدام أمر cmdlet هذا، راجع [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>إزالة أصل من Office 365 CDN

يمكنك إزالة الوصول إلى مجلد أو مكتبة SharePoint حددتها كأصل. للقيام بذلك، استخدم **الأمر remove-SPOTenantCdnOrigin** cmdlet.

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

للحصول على معلومات حول كيفية استخدام أمر cmdlet هذا، راجع [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>تعديل أصل في Office 365 CDN

لا يمكنك تعديل أصل قمت بإنشائه. بدلا من ذلك، قم بإزالة الأصل ثم أضف نقطة جديدة. لمزيد من المعلومات، راجع [إزالة أصل من Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) [وإضافة أصل لأصولك](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>تعطيل Office 365 CDN

استخدم **Set-SPOTenantCdnEnabled** cmdlet لتعطيل شبكة تسليم المحتوى لمؤسستك. إذا كانت لديك الأصول العامة والخاصة الممكنة لشبكة تسليم المحتوى، فستحتاج إلى تشغيل cmdlet مرتين كما هو موضح في الأمثلة التالية.

لتعطيل استخدام الأصول العامة في شبكة تسليم المحتوى، أدخل الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

لتعطيل استخدام الأصول الخاصة في شبكة تسليم المحتوى، أدخل الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

لمزيد من المعلومات حول أمر cmdlet هذا، راجع [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>إعداد وتكوين Office 365 CDN باستخدام PnP PowerShell

تتطلب الإجراءات الواردة في هذا القسم استخدام PnP PowerShell للاتصال ب SharePoint Online. للحصول على الإرشادات، راجع [بدء استخدام PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started).

أكمل هذه الخطوات لإعداد وتكوين شبكة تسليم المحتوى لاستضافة أصولك في SharePoint Online باستخدام PnP PowerShell.

<details>
  <summary>انقر للتوسيع</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>تمكين مؤسستك من استخدام Office 365 CDN

قبل إجراء تغييرات على إعدادات شبكة تسليم المحتوى للمستأجر، يجب استرداد الحالة الحالية لتكوين شبكة تسليم المحتوى الخاصة في مستأجر Office 365. الاتصال بالمستأجر باستخدام PnP PowerShell:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

الآن استخدم **Get-PnPTenantCdnEnabled** cmdlet لاسترداد إعدادات حالة شبكة تسليم المحتوى من المستأجر:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

سيتم إخراج حالة CDN ل CdnType المحدد إلى الشاشة.

استخدم **Set-PnPTenantCdnEnabled** cmdlet لتمكين مؤسستك من استخدام شبكة تسليم المحتوى Office 365. يمكنك تمكين مؤسستك من استخدام الأصول العامة أو الأصول الخاصة أو كليهما في الوقت نفسه. يمكنك أيضا تكوين شبكة تسليم المحتوى لتخطي إعداد الأصول الافتراضية عند تمكينها. يمكنك دائما إضافة هذه الأصول لاحقا كما هو موضح في هذا الموضوع.

في PnP PowerShell:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

على سبيل المثال، لتمكين مؤسستك من استخدام الأصول العامة والخاصة، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

لتمكين مؤسستك من استخدام الأصول العامة والخاصة ولكن تخطي إعداد الأصول الافتراضية، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

راجع [أصول CDN الافتراضية](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) للحصول على معلومات حول الأصول التي يتم توفيرها بشكل افتراضي عند تمكين Office 365 CDN، والتأثير المحتمل لتخطي إعداد الأصول الافتراضية.

لتمكين مؤسستك من استخدام الأصول العامة، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

لتمكين مؤسستك من استخدام الأصول الخاصة، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

لمزيد من المعلومات حول أمر cmdlet هذا، راجع [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>تغيير قائمة أنواع الملفات لتضمينها في Office 365 CDN (اختياري)

> [!TIP]
> عند تعريف أنواع الملفات باستخدام **Set-PnPTenantCdnPolicy** cmdlet، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد إضافة أنواع ملفات إضافية إلى القائمة، فاستخدم cmdlet أولا لمعرفة أنواع الملفات المسموح بها بالفعل وتضمينها في القائمة مع أنواع الملفات الجديدة.

استخدم **Set-PnPTenantCdnPolicy** cmdlet لتعريف أنواع الملفات الثابتة التي يمكن استضافتها بواسطة الأصول العامة والخاصة في شبكة تسليم المحتوى. بشكل افتراضي، يتم السماح بأنواع الأصول الشائعة، على سبيل المثال.css، .gif، .jpg، .js.

في PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

على سبيل المثال، لتمكين CDN من استضافة ملفات .css والملفات .png، يمكنك إدخال الأمر:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

لمعرفة أنواع الملفات المسموح بها حاليا بواسطة شبكة تسليم المحتوى، استخدم **Cmdlet Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

لمزيد من المعلومات حول أوامر cmdlets هذه، راجع [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) و [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>تغيير قائمة تصنيفات المواقع التي تريد استبعادها من شبكة تسليم المحتوى Office 365 (اختياري)

> [!TIP]
> عند استبعاد تصنيفات المواقع باستخدام **Cmdlet Set-PnPTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت ترغب في استبعاد تصنيفات مواقع إضافية، فاستخدم cmdlet أولا لمعرفة التصنيفات التي تم استبعادها بالفعل ثم إضافتها مع التصنيفات الجديدة.

استخدم **Set-PnPTenantCdnPolicy** cmdlet لاستبعاد تصنيفات المواقع التي لا تريد توفيرها عبر شبكة تسليم المحتوى. بشكل افتراضي، لا يتم استبعاد تصنيفات المواقع.

في PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

لمعرفة تصنيفات المواقع المقيدة حاليا، استخدم **Get-PnPTenantCdnPolicies** cmdlet:

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

الخصائص التي سيتم إرجاعها هي _IncludeFileExtensions_ و _ExcludeRestrictedSiteClassifications_ و _ExcludeIfNoScriptDisabled_.

تحتوي _الخاصية IncludeFileExtensions_ على قائمة ملحقات الملفات التي سيتم تقديمها من شبكة تسليم المحتوى.

> [!NOTE]
> تختلف ملحقات الملفات الافتراضية بين العامة والخاصة.

تحتوي الخاصية _ExcludeRestrictedSiteClassifications_ على تصنيفات المواقع التي تريد استبعادها من شبكة تسليم المحتوى. على سبيل المثال، يمكنك استبعاد المواقع التي تم وضع علامة **"سري** " عليها بحيث لا يتم تقديم المحتوى من المواقع التي تم تطبيق هذا التصنيف عليها من شبكة تسليم المحتوى.

تستثني _الخاصية ExcludeIfNoScriptDisabled_ المحتوى من شبكة تسليم المحتوى استنادا إلى إعدادات السمة _NoScript_ على مستوى الموقع. بشكل افتراضي، يتم تعيين السمة _NoScript_ إلى **"ممكن** للمواقع _الحديثة_ " و" **معطل** للمواقع _الكلاسيكية_ ". يعتمد هذا على إعدادات المستأجر.

لمزيد من المعلومات حول أوامر cmdlets هذه، راجع [Set-PnPTenantCdnPolicy](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnPolicy.html) و [Get-PnPTenantCdnPolicies](https://pnp.github.io/powershell/cmdlets/Get-PnPTenantCdnPolicies.html).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>إضافة أصل لأصولك

استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف أصل. يمكنك تحديد أصول متعددة. الأصل هو URL يشير إلى مكتبة أو مجلد SharePoint يحتوي على الأصول التي تريد استضافتها بواسطة شبكة تسليم المحتوى.

> [!IMPORTANT]
> يجب عدم وضع الموارد التي تحتوي على معلومات المستخدم أو التي تعتبر حساسة لمؤسستك في أصل عام.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

قيمة _المسار_ هي المسار النسبي للمكتبة أو المجلد الذي يحتوي على الأصول. يمكنك استخدام أحرف البدل بالإضافة إلى المسارات النسبية. تدعم الأصول أحرف البدل الملحقة ب URL. يسمح لك هذا بإنشاء أصول تمتد عبر مواقع متعددة. على سبيل المثال، لتضمين كافة الأصول في مجلد الصفحات الرئيسية لكافة مواقعك كأصل عام داخل شبكة تسليم المحتوى، اكتب الأمر التالي:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ يمكن استخدام معدل حرف البدل ***/** فقط في بداية المسار، وسيتطابق مع كافة مقاطع URL ضمن عنوان URL المحدد.
+ يمكن أن يشير المسار إلى مكتبة مستندات أو مجلد أو موقع. على سبيل المثال، سيتطابق المسار _*/site1_ مع كافة مكتبات المستندات الموجودة ضمن الموقع.

يمكنك إضافة أصل بمسار نسبي محدد. لا يمكنك إضافة أصل باستخدام المسار الكامل.

يضيف هذا المثال أصل خاص لمكتبة أصول الموقع على موقع معين:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

يضيف هذا المثال أصل خاص لمجلد _folder1_ في مكتبة أصول المواقع المشتركة لمجموعة المواقع المشتركة:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

إذا كانت هناك مسافة في المسار، يمكنك إما إحاطة المسار بعلامات اقتباس مزدوجة أو استبدال المساحة برمز URL ٪20. تضيف الأمثلة التالية أصل خاص لمجلد _المجلد 1_ في مكتبة أصول المواقع المشتركة لمجموعة المواقع المشتركة:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

> [!NOTE]
> في الأصول الخاصة، يجب أن يكون للأصول التي تتم مشاركتها من أصل إصدار رئيسي منشور قبل أن تتمكن من الوصول إليها من شبكة تسليم المحتوى.

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>مثال: تكوين أصل عام للصفحات الرئيسية ومكتبة الأنماط ل SharePoint Online

عادة، يتم إعداد هذه الأصول لك بشكل افتراضي عند تمكين Office 365 CDN. ومع ذلك، إذا كنت تريد تمكينها يدويا، فاتبع هذه الخطوات.

+ استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف مكتبة الأنماط كأصل عام.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف الصفحات الرئيسية كأصل عام.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>مثال: تكوين أصل خاص لأصول الموقع وصفحات الموقع وصور النشر ل SharePoint Online

+ استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف مجلد أصول الموقع كأصل خاص.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف مجلد صفحات الموقع كأصل خاص.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف مجلد صور النشر كأصل خاص.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>مثال: تكوين أصل خاص لمجموعة مواقع مشتركة ل SharePoint Online

استخدم **Add-PnPTenantCdnOrigin** cmdlet لتعريف مجموعة مواقع مشتركة كأصل خاص. على سبيل المثال:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

لمزيد من المعلومات حول هذا الأمر وبنيته، راجع [Add-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Add-PnPTenantCdnOrigin.html).

بمجرد تشغيل الأمر، يقوم النظام بمزامنة التكوين عبر مركز البيانات. قد ترى رسالة _"التكوين" المعلقة_ المتوقعة مع اتصال مستأجر SharePoint Online بخدمة CDN. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>إدارة Office 365 CDN

بمجرد إعداد شبكة تسليم المحتوى، يمكنك إجراء تغييرات على التكوين أثناء تحديث المحتوى أو مع تغير احتياجاتك، كما هو موضح في هذا القسم.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>إضافة أصول أو تحديثها أو إزالتها من Office 365 CDN

بمجرد الانتهاء من خطوات الإعداد، يمكنك إضافة أصول جديدة وتحديث الأصول الموجودة أو إزالتها كلما أردت. ما عليك سوى إجراء تغييرات على الأصول الموجودة في المجلد أو مكتبة SharePoint التي حددتها كأصل. إذا قمت بإضافة أصل جديد، فإنه يتوفر من خلال شبكة تسليم المحتوى على الفور. ومع ذلك، إذا قمت بتحديث الأصل، سيستغرق نشر النسخة الجديدة وتوافرها في شبكة تسليم المحتوى ما يصل إلى 15 دقيقة.

إذا كنت بحاجة إلى استرداد موقع الأصل، يمكنك استخدام **Get-PnPTenantCdnOrigin** cmdlet. للحصول على معلومات حول كيفية استخدام أمر cmdlet هذا، راجع [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>إزالة أصل من Office 365 CDN

يمكنك إزالة الوصول إلى مجلد أو مكتبة SharePoint حددتها كأصل. للقيام بذلك، استخدم **الأمر Remove-PnPTenantCdnOrigin** cmdlet.

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

للحصول على معلومات حول كيفية استخدام أمر cmdlet هذا، راجع [Remove-PnPTenantCdnOrigin](https://pnp.github.io/powershell/cmdlets/Remove-PnPTenantCdnOrigin.html).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>تعديل أصل في Office 365 CDN

لا يمكنك تعديل أصل قمت بإنشائه. بدلا من ذلك، قم بإزالة الأصل ثم أضف نقطة جديدة. لمزيد من المعلومات، راجع [إزالة أصل من Office 365 CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) [وإضافة أصل لأصولك](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>تعطيل Office 365 CDN

استخدم **Set-PnPTenantCdnEnabled** cmdlet لتعطيل CDN لمؤسستك. إذا كانت لديك الأصول العامة والخاصة الممكنة لشبكة تسليم المحتوى، فستحتاج إلى تشغيل cmdlet مرتين كما هو موضح في الأمثلة التالية.

لتعطيل استخدام الأصول العامة في شبكة تسليم المحتوى، أدخل الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

لتعطيل استخدام الأصول الخاصة في شبكة تسليم المحتوى، أدخل الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

لمزيد من المعلومات حول أمر cmdlet هذا، راجع [Set-PnPTenantCdnEnabled](https://pnp.github.io/powershell/cmdlets/Set-PnPTenantCdnEnabled.html).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>إعداد وتكوين Office 365 CDN باستخدام CLI ل Microsoft 365

تتطلب الإجراءات الواردة في هذا القسم تثبيت [CLI ل Microsoft 365](https://aka.ms/cli-m365). بعد ذلك، اتصل بمستأجر Office 365 باستخدام أمر [تسجيل الدخول](https://pnp.github.io/cli-microsoft365/cmd/login/).

أكمل هذه الخطوات لإعداد شبكة تسليم المحتوى وتكوينها لاستضافة أصولك في SharePoint Online باستخدام CLI ل Microsoft 365.

<details>
  <summary>انقر للتوسيع</summary>

### <a name="enable-the-office-365-cdn"></a>تمكين Office 365 CDN

يمكنك إدارة حالة Office 365 CDN في المستأجر الخاص بك باستخدام أمر [مجموعة spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/).

لتمكين Office 365 Public CDN في المستأجر الخاص بك تنفيذ:

```cli
spo cdn set --type Public --enabled true
```

لتمكين Office 365 SharePoint CDN، نفذ:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>عرض الحالة الحالية Office 365 CDN

للتحقق مما إذا كان نوع معين من Office 365 CDN ممكنا أو معطلا، استخدم أمر [الحصول على spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/).

للتحقق مما إذا تم تمكين Office 365 Public CDN، نفذ:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>عرض أصول Office 365 CDN

لعرض Office 365 أساسيات شبكة تسليم المحتوى العامة التي تم تكوينها حاليا:

```cli
spo cdn origin list --type Public
```

راجع [أصول CDN الافتراضية](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) للحصول على معلومات حول الأصول التي يتم توفيرها بشكل افتراضي عند تمكين Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>إضافة أصل Office 365 CDN

> [!IMPORTANT]
> يجب ألا تضع أبدا الموارد التي تعتبر حساسة لمؤسستك في مكتبة مستندات SharePoint تم تكوينها كأصل عام.

استخدم أمر [إضافة spo cdn الأصلي](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) لتعريف أصل شبكة تسليم المحتوى. يمكنك تحديد أصول متعددة. الأصل هو URL يشير إلى مكتبة أو مجلد SharePoint يحتوي على الأصول التي تريد استضافتها بواسطة شبكة تسليم المحتوى.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

أين `path` هو المسار النسبي للمجلد الذي يحتوي على الأصول. يمكنك استخدام أحرف البدل بالإضافة إلى المسارات النسبية.

لتضمين كافة الأصول في **"معرض الصفحات الرئيسية"** لكافة المواقع كأصل عام، نفذ:

```cli
spo cdn origin add --type Public --origin */masterpage
```

لتكوين أصل خاص لمجموعة مواقع مشتركة معينة، نفذ ما يلي:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> بعد إضافة أصل شبكة تسليم المحتوى، قد يستغرق الأمر ما يصل إلى 15 دقيقة لتتمكن من استرداد الملفات عبر خدمة CDN. يمكنك التحقق مما إذا كان الأصل المعين قد تم تمكينه بالفعل باستخدام أمر [قائمة أصل spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) .

### <a name="remove-an-office-365-cdn-origin"></a>إزالة أصل Office 365 CDN

استخدم الأمر [إزالة أصل spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) لإزالة أصل CDN لنوع CDN المحدد.

لإزالة أصل عام من تكوين شبكة تسليم المحتوى، نفذ:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> لا تؤثر إزالة أصل شبكة تسليم المحتوى على الملفات المخزنة في أي مكتبة مستندات تتطابق مع هذا الأصل. إذا تمت الإشارة إلى هذه الأصول باستخدام عنوان URL ل SharePoint، فسيعود SharePoint تلقائيا إلى عنوان URL الأصلي الذي يشير إلى مكتبة المستندات. ومع ذلك، إذا تمت الإشارة إلى الأصول باستخدام عنوان URL عام ل CDN، فإن إزالة الأصل ستؤدي إلى قطع الارتباط وستحتاج إلى تغييرها يدويا.

### <a name="modify-an-office-365-cdn-origin"></a>تعديل أصل Office 365 CDN

لا يمكن تعديل أصل شبكة تسليم المحتوى الموجودة. بدلا من ذلك، يجب إزالة أصل CDN المحدد مسبقا باستخدام `spo cdn origin remove` الأمر وإضافة أمر جديد باستخدام `spo cdn origin add` الأمر.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>تغيير أنواع الملفات لتضمينها في Office 365 CDN

بشكل افتراضي، يتم تضمين أنواع الملفات التالية في شبكة تسليم المحتوى: _.css و.eot و .gif و.ico و.jpeg و .jpg و .js و.map و .png و.svg و.ttf و.woff و.woff2_. إذا كنت بحاجة إلى تضمين أنواع ملفات إضافية في شبكة تسليم المحتوى، يمكنك تغيير تكوين شبكة تسليم المحتوى باستخدام أمر [مجموعة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) .

> [!NOTE]
> عند تغيير قائمة أنواع الملفات، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد تضمين أنواع ملفات إضافية، فاستخدم أولا أمر [قائمة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) لمعرفة أنواع الملفات التي تم تكوينها حاليا.

لإضافة نوع ملف _JSON_ إلى القائمة الافتراضية لأنواع الملفات المضمنة في شبكة تسليم المحتوى العامة، نفذ:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>تغيير قائمة تصنيفات المواقع التي تريد استبعادها من شبكة تسليم المحتوى Office 365

استخدم أمر [مجموعة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) لاستبعاد تصنيفات المواقع التي لا تريد توفيرها عبر شبكة تسليم المحتوى. بشكل افتراضي، لا يتم استبعاد تصنيفات المواقع.

> [!NOTE]
> عند تغيير قائمة تصنيفات المواقع المستبعدة، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت ترغب في استبعاد تصنيفات إضافية، فاستخدم أولا أمر [قائمة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) لمعرفة التصنيفات التي تم تكوينها حاليا.

لاستبعاد المواقع المصنفة على أنها _HBI_ من شبكة تسليم المحتوى العامة، نفذ

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>تعطيل Office 365 CDN

لتعطيل Office 365 CDN استخدم `spo cdn set` الأمر، على سبيل المثال:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>استخدام أصول شبكة تسليم المحتوى

الآن بعد أن قمت بتمكين شبكة تسليم المحتوى وتكوين الأصول والنهج، يمكنك البدء في استخدام أصول شبكة تسليم المحتوى.

سيساعدك هذا القسم على فهم كيفية استخدام عناوين URL لشبكة تسليم المحتوى في صفحات SharePoint ومحتواه بحيث يعيد SharePoint توجيه طلبات الأصول في الأصول العامة والخاصة إلى شبكة تسليم المحتوى.

+ [تحديث الارتباطات إلى أصول CDN](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [استخدام الأصول في الأصول العامة](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [استخدام الأصول في الأصول الخاصة](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

للحصول على معلومات حول كيفية استخدام شبكة تسليم المحتوى لاستضافة أجزاء ويب من جانب العميل، راجع الموضوع ["استضافة جزء ويب من جانب العميل" من Office 365 CDN (مرحبًا بالعالم الجزء 4).](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)

> [!NOTE]
> إذا أضفت مجلد _ClientSideAssets_ إلى قائمة أصول شبكة تسليم المحتوى **الخاصة** ، فستفشل أجزاء ويب المخصصة المستضافة على شبكة تسليم المحتوى في العرض. يمكن للملفات التي تستخدمها أجزاء ويب SPFX فقط استخدام شبكة تسليم المحتوى العامة ومجلد ClientSideAssets هو أصل افتراضي لشبكة تسليم المحتوى العامة.

### <a name="updating-links-to-cdn-assets"></a>تحديث الارتباطات إلى أصول CDN

لاستخدام الأصول التي أضفتها إلى أصل، ما عليك سوى تحديث الارتباطات إلى الملف الأصلي مع المسار إلى الملف في الأصل.

+ تحرير الصفحة أو المحتوى الذي يحتوي على ارتباطات بأصول أضفتها إلى أصل. يمكنك أيضا استخدام إحدى الطرق المتعددة للبحث عن الارتباطات واستبدالها بشكل عمومي عبر موقع إدخال أو مجموعة مواقع مشتركة إذا كنت تريد تحديث الارتباط إلى أصل معين في كل مكان يظهر فيه.
+ لكل ارتباط إلى أصل، استبدل المسار بالمسار إلى الملف في أصل شبكة تسليم المحتوى. يمكنك استخدام مسارات نسبية.
+ حفظ الصفحة أو المحتوى.

على سبيل المثال، ضع في اعتبارك الصورة _/الموقع/SiteAssets/images/image.png_، التي قمت بنسخها إلى مجلد مكتبة المستندات _/site/CDN_origins/public/_. لاستخدام أصل CDN، استبدل المسار الأصلي إلى موقع ملف الصورة بالمسار إلى الأصل لجعل عنوان URL _/site/CDN_origins/public/image.png_ الجديد.

إذا كنت تريد استخدام عنوان URL الكامل للأصل بدلا من مسار نسبي، قم بإنشاء الارتباط كما يلي:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> بشكل عام، يجب عدم ترميز عناوين URL بشكل ثابت مباشرة إلى الأصول في شبكة تسليم المحتوى. ومع ذلك، يمكنك إنشاء عناوين URL يدويا للأصول في الأصول العامة إذا لزم الأمر. لمزيد من المعلومات، راجع [عناوين URL لشبكة تسليم المحتوى ذات الترميز الثابت للأصول العامة](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

لمعرفة كيفية التحقق من أن الأصول يتم تقديمها من شبكة تسليم المحتوى، راجع [كيف أعمل التأكد من أن الأصول تخدمها شبكة تسليم المحتوى؟](use-microsoft-365-cdn-with-spo.md#CDNConfirm) في [استكشاف أخطاء شبكة تسليم المحتوى Office 365](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) وإصلاحها.

### <a name="using-assets-in-public-origins"></a>استخدام الأصول في الأصول العامة

تعيد **ميزة النشر** في SharePoint Online تلقائيا كتابة عناوين URL للأصول المخزنة في الأصول العامة إلى مكافئات شبكة تسليم المحتوى بحيث يتم تقديم الأصول من خدمة CDN بدلا من SharePoint.

إذا كان أصلك في موقع تم تمكين ميزة "النشر"، وتوجد الأصول التي تريد إلغاء تحميلها إلى شبكة تسليم المحتوى في إحدى الفئات التالية، فسيعيد SharePoint تلقائيا كتابة عناوين URL للأصول في الأصل، شريطة ألا يتم استبعاد الأصل بواسطة نهج CDN.

فيما يلي نظرة عامة حول الارتباطات التي تتم إعادة كتابتها تلقائيا بواسطة ميزة نشر SharePoint:

+ عناوين URL IMG/LINK/CSS في استجابات HTML لصفحة النشر الكلاسيكية
  + يتضمن ذلك الصور التي أضافها الكتاب ضمن محتوى HTML لصفحة
+ عناوين URL لجزء ويب لعرض شرائح مكتبة الصور
+ نتائج حقول الصور في SPList REST API (RenderListDataAsStream)
  + استخدام _الخاصية الجديدة ImageFieldsToTryRewriteToCdnUrls_ لتوفير قائمة بالحقول مفصولة بفواصل
  + يدعم حقول الارتباطات التشعبية وحقول PublishingImage
+ تسليمات صور SharePoint

يوضح الرسم التخطيطي التالي سير العمل عندما يتلقى SharePoint طلبا لصفحة تحتوي على أصول من أصل عام.

![الرسم التخطيطي لسير العمل: استرداد أصول Office 365 CDN من أصل عام.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "سير العمل: استرداد أصول Office 365 CDN من أصل عام")

> [!TIP]
> إذا كنت تريد تعطيل إعادة الكتابة التلقائية لعناوين URL معينة على صفحة، يمكنك سحب الصفحة وإضافة معلمة سلسلة الاستعلام **؟ NoAutoReWrites=true** إلى نهاية كل ارتباط تريد تعطيله.

#### <a name="constructing-cdn-urls-for-public-assets"></a>إنشاء عناوين URL لشبكة تسليم المحتوى للأصول العامة

إذا لم يتم تمكين ميزة _النشر_ لأصل عام، أو لم يكن الأصل أحد أنواع الارتباطات المعتمدة بواسطة ميزة إعادة الكتابة التلقائية لخدمة CDN، يمكنك إنشاء عناوين URL يدويا إلى موقع شبكة تسليم المحتوى للأصول واستخدام عناوين URL هذه في المحتوى الخاص بك.

> [!NOTE]
> لا يمكنك ترميز عناوين URL ل CDN أو إنشائها إلى أصول في أصل خاص لأن رمز الوصول المميز المطلوب الذي يشكل القسم الأخير من عنوان URL يتم إنشاؤه في وقت طلب المورد. يمكنك إنشاء عنوان URL لشبكة تسليم المحتوى العامة ويجب ألا يكون عنوان URL مرمزا بشكل ثابت لأنه عرضة للتغيير.

بالنسبة لأصول شبكة تسليم المحتوى العامة، سيبدو تنسيق URL كما يلي:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

استبدل **TenantHostName** باسم المستأجر الخاص بك. على سبيل المثال:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> يجب استخدام خاصية سياق الصفحة لإنشاء البادئة بدلا من الترميز الثابت "https://publiccdn.sharepointonline.com". عنوان URL عرضة للتغيير ويجب عدم ترميزه برمجيا. إذا كنت تستخدم قوالب العرض مع SharePoint Online الكلاسيكي، فيمكنك استخدام الخاصية "window._spPageContextInfo.publicCdnBaseUrl" في قالب العرض لبادئة عنوان URL. إذا كنت أجزاء ويب SPFx ل SharePoint الحديث والكلاسيكي، يمكنك استخدام الخاصية "this.context.pageContext.legacyPageContext.publicCdnBaseUrl". سيوفر هذا البادئة بحيث إذا تم تغييرها، فسيتم تحديث تنفيذك معها. كمثال على SPFx، يمكن إنشاء URL باستخدام الخاصية "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "relativeURL للعنصر". الرجاء مراجعة [استخدام CDN في التعليمات البرمجية من جانب العميل](https://youtu.be/IH1RbQlbhIA) التي تعد جزءا من [سلسلة أداء الموسم 1](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>استخدام الأصول في الأصول الخاصة

لا يلزم تكوين إضافي لاستخدام الأصول في الأصول الخاصة. يعيد SharePoint Online تلقائيا كتابة عناوين URL للأصول في الأصول الخاصة بحيث يتم تقديم طلبات هذه الأصول دائما من شبكة تسليم المحتوى. لا يمكنك إنشاء عناوين URL يدويا إلى أصول CDN في أصول خاصة لأن عناوين URL هذه تحتوي على رموز مميزة يجب إنشاؤها تلقائيا بواسطة SharePoint Online في الوقت المطلوب فيه الأصل.

الوصول إلى الأصول في الأصول الخاصة محمي بالرموز المميزة التي تم إنشاؤها ديناميكيا استنادا إلى أذونات المستخدم إلى الأصل، مع التحذيرات الموضحة في الأقسام التالية. يجب أن يكون لدى المستخدمين حق الوصول **للقراءة** على الأقل إلى أصول شبكة تسليم المحتوى لعرض المحتوى.

يوضح الرسم التخطيطي التالي سير العمل عندما يتلقى SharePoint طلبا لصفحة تحتوي على أصول من أصل خاص.

![الرسم التخطيطي لسير العمل: استرداد أصول Office 365 CDN من أصل خاص.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "سير العمل: استرداد أصول Office 365 CDN من أصل خاص")

#### <a name="token-based-authorization-in-private-origins"></a>التخويل المستند إلى الرمز المميز في الأصول الخاصة

يتم منح الوصول إلى الأصول في الأصول الخاصة في Office 365 CDN بواسطة الرموز المميزة التي تم إنشاؤها بواسطة SharePoint Online. يتم تلقائيا منح المستخدمين الذين لديهم إذن بالوصول إلى المجلد أو المكتبة المعينة من قبل الأصل الرموز المميزة التي تسمح للمستخدم بالوصول إلى الملف استنادا إلى مستوى الأذونات الخاص بهم. رموز الوصول المميزة هذه صالحة لمدة 30 إلى 90 دقيقة بعد إنشائها للمساعدة في منع هجمات إعادة عرض الرمز المميز.

بمجرد إنشاء رمز الوصول المميز، يقوم SharePoint Online بإرجاع URI مخصص إلى العميل الذي يحتوي على معلمتي تخويل _(_ الرمز المميز لتخويل الحافة) _وoat_ (رمز تخويل الأصل). بنية كل رمز مميز هي _وقت انتهاء الصلاحية< بتنسيق وقت Epoch >__<'secure signature'>_. على سبيل المثال:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> يمكن لأي شخص يمتلك الرمز المميز الوصول إلى المورد في شبكة تسليم المحتوى. ومع ذلك، لا تتم مشاركة عناوين URL التي تحتوي على رموز الوصول المميزة هذه إلا عبر HTTPS، لذلك لن يتمكن المستخدمون غير المصرح لهم من الوصول إلى الأصل إلا إذا تمت مشاركة عنوان URL بشكل صريح قبل انتهاء صلاحية الرمز المميز.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>الأذونات على مستوى العنصر غير معتمدة للأصول في الأصول الخاصة

من المهم ملاحظة أن SharePoint Online لا يدعم الأذونات على مستوى العنصر للأصول في الأصول الخاصة. على سبيل المثال، بالنسبة إلى ملف موجود في `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`، يمكن للمستخدمين الوصول الفعال إلى الملف وفقا للشروط التالية:

|User  |الأذونات  |الوصول الفعال  |
|---------|---------|---------|
|المستخدم 1     |لديه حق الوصول إلى المجلد1         |يمكن الوصول إلى image1.jpg من شبكة تسليم المحتوى         |
|المستخدم 2     |ليس لديه حق الوصول إلى المجلد1         |يتعذر الوصول إلى image1.jpg من شبكة تسليم المحتوى         |
|المستخدم 3     |ليس لديه حق الوصول إلى المجلد1، ولكن يتم منحه إذنا صريحا للوصول إلى image1.jpg في SharePoint Online         |يمكن الوصول إلى image1.jpg الأصل مباشرة من SharePoint Online، ولكن ليس من شبكة تسليم المحتوى         |
|المستخدم 4     |لديه حق الوصول إلى المجلد1، ولكن تم رفض الوصول إلى image1.jpg في SharePoint Online بشكل صريح         |يتعذر الوصول إلى الأصل من SharePoint Online، ولكن يمكنه الوصول إلى الأصل من شبكة تسليم المحتوى على الرغم من رفض الوصول إلى الملف في SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>استكشاف أخطاء Office 365 CDN وإصلاحها

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>كيف أعمل تأكيد أن الأصول تخدمها شبكة تسليم المحتوى؟

بمجرد إضافة ارتباطات إلى أصول CDN إلى صفحة، يمكنك التأكد من أن الأصل يتم تقديمه من شبكة تسليم المحتوى من خلال الاستعراض إلى الصفحة، والنقر بزر الماوس الأيمن فوق الصورة بمجرد عرضها ومراجعة عنوان URL للصورة.

يمكنك أيضا استخدام أدوات مطور المستعرض لعرض عنوان URL لكل أصل على صفحة، أو استخدام أداة تتبع شبكة تابعة لجهة خارجية.

> [!NOTE]
> إذا كنت تستخدم أداة شبكة مثل Fiddler لاختبار الأصول الخاصة بك خارج عرض الأصل من صفحة SharePoint، يجب إضافة رأس المرجعي يدويا "مرجع: `https://yourdomain.sharepoint.com`" إلى طلب GET حيث يكون URL هو URL الجذر لمستأجر SharePoint Online.

لا يمكنك اختبار عناوين URL لشبكة تسليم المحتوى مباشرة في مستعرض ويب لأنه يجب أن يكون لديك مرجع قادم من SharePoint Online. ومع ذلك، إذا أضفت عنوان URL الخاص بأصل شبكة تسليم المحتوى إلى صفحة SharePoint ثم فتحت الصفحة في مستعرض، فسترى أصل CDN معروضا على الصفحة.

لمزيد من المعلومات حول استخدام أدوات المطور في مستعرض Microsoft Edge، راجع [أدوات مطور Microsoft Edge](/microsoft-edge/devtools-guide).

لمشاهدة فيديو قصير مستضاف في [قناة SharePoint Developer Patterns and Practices YouTube](https://aka.ms/sppnp-videos) يوضح كيفية التحقق من عمل شبكة تسليم المحتوى، يرجى مراجعة [التحقق من استخدام شبكة تسليم المحتوى وضمان الاتصال الأمثل بالشبكة](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>لماذا الأصول من أصل جديد غير متوفرة؟
لن تكون الأصول في الأصول الجديدة متاحة للاستخدام على الفور، حيث يستغرق التسجيل وقتا لنشرها من خلال شبكة تسليم المحتوى وتحميل الأصول من الأصل إلى تخزين شبكة تسليم المحتوى. يعتمد الوقت المطلوب لتوفر الأصول في شبكة تسليم المحتوى على عدد الأصول وأحجام الملفات.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>لا يعمل جزء الويب الخاص بي من جانب العميل أو حل إطار عمل SharePoint الخاص بي

عند تمكين Office 365 CDN للأصول العامة، تقوم خدمة CDN تلقائيا بإنشاء هذه الأصول الافتراضية:

+ */MASTERPAGE
+ */مكتبة الأنماط
+ */CLIENTSIDEASSETS

إذا كان أصل */clientsideassets مفقودا، فستفشل إطار عمل SharePoint الحلول، ولا يتم إنشاء رسائل تحذير أو خطأ. قد يكون هذا الأصل مفقودا إما بسبب تمكين CDN مع تعيين المعلمة _-NoDefaultOrigins_ **إلى $true**، أو لأنه تم حذف الأصل يدويا.

يمكنك التحقق لمعرفة الأصول الموجودة مع أمر PowerShell التالي:

```powershell
Get-SPOTenantCdnOrigins -CdnType Public
```

أو يمكنك التحقق من Office 365 CLI:

```cli
spo cdn origin list
```

لإضافة الأصل في PowerShell:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

لإضافة الأصل في Office 365 CLI:

```cli
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>ما هي وحدات PowerShell وواجهة سطر الأوامر التي أحتاجها للعمل مع شبكة تسليم المحتوى Office 365؟

يمكنك اختيار العمل مع Office 365 CDN باستخدام الوحدة النمطية **SharePoint Online Management Shell** PowerShell أو **Office 365 CLI**.

+ [بدء استخدام SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [تثبيت Office 365 CLI](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>راجع أيضًا

[شبكات تسليم المحتوى](./content-delivery-networks.md)

[تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md)

[سلسلة أداء SharePoint - سلسلة فيديو Office 365 CDN](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
