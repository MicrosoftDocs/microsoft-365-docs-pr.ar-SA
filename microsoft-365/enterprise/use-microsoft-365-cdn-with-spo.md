---
title: استخدام Office 365 تسليم المحتوى (CDN) مع SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية استخدام Office 365 تسليم المحتوى (CDN) لتسريع تسليم SharePoint عبر الإنترنت.
ms.openlocfilehash: f4279da3bba7647f2e99179acb0147fe5d002f57
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/14/2022
ms.locfileid: "63568942"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a>استخدام Office 365 تسليم المحتوى (CDN) مع SharePoint Online

يمكنك استخدام شبكة تسليم Office 365 تسليم المحتوى (CDN) المضمنة لاستضافة الأصول الثابتة لتوفير أداء أفضل لصفحات SharePoint الإنترنت. تحسن Office 365 CDN الأداء عن طريق التخزين المؤقت للأصول الثابتة بالقرب من المستعرضات التي تطلبها، مما يساعد على تسريع التنزيلات وتقليل زمن زمن الوصول. كما تستخدم Office 365 CDN [بروتوكول HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) لتحسين الضغط وHTTP. يتم Office 365 خدمة CDN كجزء من اشتراكك في SharePoint Online.

> [!NOTE]
> تتوفر Office 365 CDN فقط للمستأجرين في **سحابة** الإنتاج (على مستوى العالم). لا يدعم المستأجرون في سحابة الحكومة الأمريكية والصين وألمانيا حاليا Office 365 CDN.

تتألف Office 365 CDN من شبكات CDN متعددة تسمح لك باستضافة أصول ثابتة في مواقع أو أصول متعددة، وخدمتها من شبكات عالمية عالية السرعة. استنادا إلى نوع المحتوى الذي تريد استضافته في Office 365 CDN، يمكنك إضافة أصول عامة أو أصول خاصة أو  كليهما.  راجع [اختيار ما إذا كان يجب أن يكون كل](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) أصل عام أو خاص للحصول على مزيد من المعلومات حول الفرق بين الأصول العامة والخاصة.

![Office 365 تخطيطي تصوري ل CDN.](../media/O365-CDN/o365-cdn-flow-transparent.png "Office 365 تخطيطي تصوري ل CDN")

إذا كنت ملما بالفعل بالطريقة التي تعمل بها CDNs، ما عليك سوى إكمال بضع خطوات لتمكين Office 365 CDN للمستأجر. يصف هذا الموضوع كيفية ذلك. تابع القراءة للحصول على معلومات حول كيفية بدء استضافة الأصول الثابتة.

> [!TIP]
> هناك CDNs أخرى مستضافة من Microsoft يمكن استخدامها مع Office 365 لسيناريوهات الاستخدام المتخصصة، ولكن لا يتم مناقشتها في هذا الموضوع لأنها تقع خارج نطاق Office 365 CDN. لمزيد من المعلومات، راجع [CDNs Microsoft أخرى](content-delivery-networks.md#other-microsoft-cdns).

 **ارجع إلى [تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md).**

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a>نظرة عامة حول العمل مع Office 365 CDN في SharePoint Online

لإعداد مجموعة Office 365 CDN لمنظمتك، اتبع الخطوات الأساسية التالية:

+ [التخطيط لنشر Office 365 CDN](use-microsoft-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + [حدد الأصول الثابتة التي تريد استضافتها على CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets).
  + [حدد المكان الذي تريد تخزين الأصول فيه](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets). يمكن أن يكون هذا الموقع SharePoint أو مكتبة أو مجلد ويسمى _أصل._
  + [اختر ما إذا كان يجب أن يكون كل أصل عام أو خاص](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). يمكنك إضافة أصول متعددة لكل من النوعين العام والخاص.

+ إعداد CDN وتكوينه، باستخدام PowerShell أو CLI Microsoft 365

  + [إعداد CDN وتكوينها باستخدام SharePoint Online Management Shell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPShell)
  + [إعداد CDN وتكوينها باستخدام PnP PowerShell](use-microsoft-365-cdn-with-spo.md#CDNSetupinPnPPosh)
  + [قم بإعداد CDN وتكوينها باستخدام CLI Microsoft 365](use-microsoft-365-cdn-with-spo.md#CDNSetupinCLI)

  عند إكمال هذه الخطوة، سيكون لديك:

  + تمكين CDN لمنظمتك.
  + أضف أصولك، مع تحديد كل أصل ك عام أو خاص.

بمجرد أن تنجز عملية الإعداد، يمكنك إدارة Office 365 [CDN](use-microsoft-365-cdn-with-spo.md#CDNManage) مع مرور الوقت من خلال:

+ إضافة الأصول وتحديثها وإزالتها
+ إضافة أصول وإزالتها
+ تكوين سياسات CDN
+ إذا لزم الأمر، تعطيل CDN

وأخيرا، راجع [استخدام أصول CDN](use-microsoft-365-cdn-with-spo.md#using-your-cdn-assets) للتعرف على كيفية الوصول إلى أصول CDN من أصول عامة وخاصة.

راجع [استكشاف الأخطاء وإصلاحها Office 365 CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting) للحصول على إرشادات حول حل المشاكل الشائعة.

## <a name="plan-for-deployment-of-the-office-365-cdn"></a>التخطيط لنشر Office 365 CDN

قبل نشر Office 365 CDN لمستأجر Office 365، يجب أن تفكر في العوامل التالية كجزء من عملية التخطيط.

  + [تحديد الأصول الثابتة التي تريد استضافتها على CDN](use-microsoft-365-cdn-with-spo.md#CDNAssets)
  + [تحديد المكان الذي تريد تخزين الأصول فيه](use-microsoft-365-cdn-with-spo.md#CDNStoreAssets)
  + [اختيار ما إذا كان يجب أن يكون كل أصل عام أو خاص](use-microsoft-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<a name="CDNAssets"> </a>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a>تحديد الأصول الثابتة التي تريد استضافتها على CDN

بشكل عام، تكون CDNs أكثر فعالية لاستضافة الأصول الثابتة أو الأصول التي لا تتغير كثيرا. من الجيد تحديد الملفات التي تفي ببعض هذه الشروط أو كلها:

+ الملفات الثابتة المضمنة في صفحة (مثل البرامج النصية والصور) التي قد يكون لها تأثير تزايدي ملحوظ على أوقات تحميل الصفحة
+ الملفات الكبيرة مثل الملفات القابلة للتنفيذ وملفات التثبيت
+ مكتبات الموارد التي تدعم التعليمات البرمجية من جانب العميل

على سبيل المثال، يمكن للملفات الصغيرة التي يتم طلبها بشكل متكرر مثل صور الموقع والنصية تحسين أداء عرض الموقع بشكل ملحوظ وتقليل التحميل بشكل متزايد على مواقع SharePoint عبر الإنترنت عند إضافتها إلى أصل CDN. يمكن تنزيل الملفات الأكبر حجما مثل التثبيتات القابلة للتنفيذ من CDN، مما يؤثر بشكل إيجابي على الأداء ويخفض التحميل على موقع SharePoint Online، حتى لو لم يتم الوصول إليها كلما كان ذلك.

يعتمد تحسين الأداء على كل ملف على العديد من العوامل، بما في ذلك تقارب العميل لأقرب نقطة نهاية CDN، والشروط العرضية على الشبكة المحلية، وما إلى ذلك. العديد من الملفات الثابتة صغيرة جدا، ويمكن تنزيلها من Office 365 في أقل من ثانية. ومع ذلك، قد تحتوي صفحة ويب على العديد من الملفات المضمنة مع وقت تنزيل تراكمي لعدة ثوان. من شأن خدمة هذه الملفات من CDN تقليل وقت تحميل الصفحة بشكل ملحوظ. راجع [ما هي أرباح الأداء التي تقدمها CDN؟](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) على سبيل المثال.

<a name="CDNStoreAssets"> </a>
### <a name="determine-where-you-want-to-store-your-assets"></a>تحديد المكان الذي تريد تخزين الأصول فيه

تقوم CDN بإحضار الأصول من موقع _يسمى الأصل._ يمكن أن يكون الأصل SharePoint موقع ويب أو مكتبة مستندات أو مجلد يمكن الوصول إليه بواسطة عنوان URL. تتمتع بمرونة كبيرة عند تحديد أصول لمنظمتك. على سبيل المثال، يمكنك تحديد أصول متعددة أو أصل واحد حيث تريد وضع كل أصول CDN. يمكنك اختيار الحصول على أصول عامة أو خاصة لمنظمتك. ستختار معظم المؤسسات تنفيذ تركيبة من الاثنين.

يمكنك إنشاء حاوية جديدة لأصولك مثل المجلدات أو مكتبات المستندات، وإضافة الملفات التي تريد جعلها متوفرة من CDN. هذه هي الطريقة الجيدة إذا كان لديك مجموعة معينة من الأصول التي تريد أن تكون متوفرة من CDN، وتريد تقييد مجموعة أصول CDN فقط لتلك الملفات الموجودة في الحاوية.

يمكنك أيضا تكوين مجموعة مواقع أو موقع أو مكتبة أو مجلد موجود من الأصل، مما يجعل جميع الأصول المؤهلة في الحاوية متوفرة من CDN. قبل إضافة حاوية موجودة كمنشأ، من المهم التأكد من أنك على علم بمحتوياتها وأذوناتها حتى لا تعرض الأصول عن غير قصد للوصول المجهول أو للمستخدمين غير المصرح لهم.

يمكنك تعريف سياسات _CDN_ لاستبعاد المحتوى في أصولك من CDN. تستبعد نهج CDN الأصول في الأصل العام أو الخاص بواسطة سمات مثل نوع الملف وتصنيف الموقع، كما يتم تطبيقها على كافة أصول CdnType (الخاصة أو العامة) التي تحددها في النهج. على سبيل المثال، إذا أضفت أصل خاص يتكون من موقع يحتوي على مواقع فرعية متعددة، يمكنك تعريف نهج لاستبعاد المواقع التي تم وضع علامة سري عليها بحيث لا يتم تقديم  المحتوى من المواقع التي تم تطبيق هذا التصنيف عليها من شبكة CDN. سيتم تطبيق النهج على المحتوى من _كل_ الأصول الخاصة التي أضفتها إلى CDN.

ضع في اعتبارك أنه كلما زاد عدد الأصول، زاد التأثير على الوقت الذي تستغرقه خدمة CDN لمعالجة الطلبات. نوصيك بحصر عدد الأصول إلى أقصى حد ممكن.

<a name="CDNOriginChoosePublicPrivate"> </a>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a>اختيار ما إذا كان يجب أن يكون كل أصل عام أو خاص

عند تحديد أصل، يمكنك تحديد ما إذا كان يجب أن يكون عام _أو_ _خاص_. إن الوصول إلى أصول CDN في الأصول العامة مجهول، ومحتوى CDN في الأصول الخاصة مؤمن بواسطة الرموز المميزة التي يتم إنشاؤها ديناميكيا لزيادة الأمان. بغض النظر عن الخيار الذي تختاره، تقوم Microsoft بكل الأحمال بالنسبة لك عندما يتعلق الأمر بالإدارة في CDN نفسها. يمكنك أيضا تغيير رأيك لاحقا، بعد إعداد CDN وتعرف على أصولك.

يوفر كل من الخيارين العام والخاص نفس المكاسب في الأداء، ولكن لكل منهما سمات ومزايا فريدة.

**يمكن** الوصول إلى الأصول العامة Office 365 CDN بشكل مجهول، ويمكن الوصول إلى الأصول المستضافة من قبل أي شخص لديه عنوان URL للأصول. نظرا لأن الوصول إلى المحتوى في أصول عامة مجهول، يجب استخدامها فقط لذاكرة التخزين المؤقت للمحتوى العام غير الحساس مثل ملفات JavaScript، البرامج النصية، الأيقونات والصور.

**توفر** الأصول الخاصة ضمن Office 365 CDN إمكانية وصول خاصة إلى محتوى المستخدمين مثل SharePoint المستندات والمواقع والصور الخاصة عبر الإنترنت. يتم تأمين الوصول إلى المحتوى في الأصول الخاصة بواسطة الرموز المميزة التي تم إنشاؤها ديناميكيا بحيث يمكن الوصول إليها فقط من قبل المستخدمين الذين لديهم أذونات الوصول إلى مكتبة المستندات الأصلية أو موقع التخزين الأصلي. يمكن استخدام الأصول الخاصة في Office 365 CDN فقط لمحتوى SharePoint عبر الإنترنت، كما يمكنك الوصول إلى الأصول في أصول خاصة فقط من خلال إعادة التوجيه من مستأجر SharePoint Online.

يمكنك قراءة المزيد حول كيفية عمل وصول CDN إلى الأصول في أصل خاص في [استخدام الأصول في أصول خاصة](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins).

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a>سمات وميزات أصول الاستضافة في الأصول العامة

+ يمكن الوصول إلى الأصول التي يتم عرضها في أصل عام من قبل الجميع بشكل مجهول.
    > [!IMPORTANT]
    > يجب ألا تقوم أبدا ب وضع الموارد التي تحتوي على معلومات المستخدم أو التي تعتبر حساسة لمنظمتك في الأصل العام.

+ إذا قمت بإزالة أصل من أصل عام، فقد يستمر توفر الأصل لمدة تصل إلى 30 يوما من ذاكرة التخزين المؤقت؛ ومع ذلك، سنقوم بإبطال الارتباطات إلى الأصل في CDN في غضون 15 دقيقة.

+ عند استضافة أوراق نمط (ملفات CSS) في أصل عام، يمكنك استخدام المسارات النسبية وملفات URIs داخل التعليمة البرمجية. وهذا يعني أنه يمكنك الإشارة إلى موقع صور الخلفية والكائنات الأخرى بالنسبة إلى موقع الأصل الذي يتصل به.

+ على الرغم من أنه يمكنك إنشاء عنوان URL لأصل عام، يجب المتابعة بحذر والتأكد من استخدام خاصية سياق الصفحة واتبع الإرشادات للقيام بذلك. والسبب في ذلك هو أنه إذا لم يكن الوصول إلى CDN متوفرا، فإن عنوان URL لن يتم حله تلقائيا لمنظمتك في SharePoint Online وقد ينتج عنه ارتباطات مقطوعة وأخطاء أخرى. يخضع URL أيضا للتغيير ولهذا السبب يجب ألا يتم فقط الترميز الثابت لقيمته الحالية.

+ أنواع الملفات الافتراضية المضمنة لأصول عامة هي .css و .eot و .gif و .ico و .jpeg و .jpg و .js و .map و .png و .svg و .ttf و .woff و .woff2. يمكنك تحديد أنواع ملفات إضافية.

+ يمكنك تكوين نهج لاستبعاد الأصول التي تم تحديدها بواسطة تصنيفات المواقع التي تحددها. على سبيل المثال، يمكنك اختيار استبعاد كل الأصول التي تم وضع علامة "سري" عليها أو "مقيد" حتى لو كانت من أنواع الملفات المسموح بها والموجودة في أصل عام.

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a>سمات وميزات أصول الاستضافة في الأصول الخاصة

+ يمكن استخدام الأصول الخاصة فقط SharePoint عبر الإنترنت.

+ يمكن للمستخدمين الوصول إلى الأصول من أصل خاص فقط إذا كانت لديهم الأذونات للوصول إلى الحاوية. يتم منع الوصول المجهول إلى هذه الأصول.

+ يجب أن يشار إلى الأصول في الأصول الخاصة من SharePoint Online. لا يعمل الوصول المباشر إلى أصول CDN الخاصة.

+ إذا قمت بإزالة أصل من الأصل الخاص، فقد يستمر توفر الأصل لمدة تصل إلى ساعة من ذاكرة التخزين المؤقت؛ ومع ذلك، سنقوم بإبطال الارتباطات إلى الأصل في CDN في غضون 15 دقيقة من إزالة الأصل.

+ أنواع الملفات الافتراضية المضمنة لأصول خاصة هي .gif و .ico و jpeg و .jpg و .js و .png. يمكنك تحديد أنواع ملفات إضافية.

+ كما هو حال الأصول العامة، يمكنك تكوين نهج لاستبعاد الأصول التي تم تحديدها بواسطة تصنيفات المواقع التي تحددها حتى إذا كنت تستخدم أحرف البدل لتضمين كافة الأصول ضمن مجلد أو مكتبة مستندات.

لمزيد من المعلومات حول سبب استخدام شبكة تسليم المحتويات Office 365 CDN ومفاهيم CDN العامة وشبكات MICROSOFT CDN الأخرى التي يمكنك استخدامها مع مستأجر Office 365، راجع شبكات تسليم [المحتوى](content-delivery-networks.md).

### <a name="default-cdn-origins"></a>أصول CDN الافتراضية

ما لم تحدد خلاف ذلك، Office 365 إعداد بعض الأصول الافتراضية لك عند تمكين Office 365 CDN. إذا اخترت في البداية عدم توفيرها، يمكنك إضافة هذه الأصول بعد إكمال الإعداد. إلا إذا كنت تفهم نتائج تخطي إعداد الأصول الافتراضية وكان لديك سبب محدد للقيام بذلك، يجب أن تسمح بإنشاء هذه الإعدادات عند تمكين CDN.

أصول CDN الخاصة الافتراضية:

+ \*/userphoto.aspx
+ \*/siteassets

أصول CDN العامة الافتراضية:

+ \*/masterpage
+ \*/style library
+ \*/clientsideassets

> [!NOTE]
> _إن clientsideassets_ هي أصل عام افتراضي تم إضافته إلى Office 365 CDN في ديسمبر 2017. يجب أن يكون هذا الأصل موجودا حتى إطار عمل SharePoint حلول في CDN لكي تعمل. إذا قمت بتمكين Office 365 CDN قبل ديسمبر 2017، أو إذا تخطيت إعداد الأصول الافتراضية عند تمكين CDN، يمكنك إضافة هذا الأصل يدويا. لمزيد من المعلومات، راجع [جزء الويب من جانب العميل أو إطار عمل SharePoint لا يعمل الحل](use-microsoft-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).

<a name="CDNSetupinPShell"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a>إعداد قاعدة البيانات وتكوينها Office 365 CDN باستخدام SharePoint Online Management Shell

تتطلب الإجراءات في هذا القسم استخدام SharePoint Online Management Shell للاتصال SharePoint Online. للحصول على الإرشادات، [راجع الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

أكمل هذه الخطوات لإعداد CDN وتكوينها لاستضافة الأصول في SharePoint Online باستخدام SharePoint Online Management Shell.

<details>
  <summary>انقر لتوسيع</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>تمكين مؤسستك من استخدام Office 365 CDN

قبل إجراء تغييرات على إعدادات CDN للمستأجر، يجب استرداد الحالة الحالية لتكوين CDN الخاص في Office 365 المستأجر. الاتصال إلى المستأجر باستخدام SharePoint Online Management Shell:

```powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

استخدم الآن **الأمر Cmdlet Get-SPOTenantCdnEnabled** لاسترداد إعدادات حالة CDN من المستأجر:

```powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

سيتم إخراج حالة CDN ل CdnType المحدد إلى الشاشة.

استخدم **الأمر cmdlet Set-SPOTenantCdnEnabled** لتمكين مؤسستك من استخدام Office 365 CDN. يمكنك تمكين مؤسستك من استخدام الأصول العامة أو الأصول الخاصة أو كليهما في وقت واحد. يمكنك أيضا تكوين CDN لتخطي إعداد الأصول الافتراضية عند تمكينها. يمكنك دائما إضافة هذه الأصول لاحقا كما هو موضح في هذا الموضوع.

في Windows PowerShell ل SharePoint Online:

```powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

على سبيل المثال، لتمكين مؤسستك من استخدام الأصلين العام والخاص، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

لتمكين مؤسستك من استخدام الأصول العامة والخاصة على حد سواء ولكن تخطي إعداد الأصول الافتراضية، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

راجع [أصول CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) الافتراضية للحصول على معلومات حول الأصول التي يتم توفيرها بشكل افتراضي عند تمكين Office 365 CDN، والتأثير المحتمل لتخطي إعداد الأصول الافتراضية.

لتمكين مؤسستك من استخدام الأصول العامة، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

لتمكين مؤسستك من استخدام الأصول الخاصة، اكتب الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

لمزيد من المعلومات حول الأمر cmdlet هذا، راجع [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

<a name="Office365CDNforSPOFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>تغيير قائمة أنواع الملفات لتضمينها في Office 365 CDN (اختياري)

> [!TIP]
> عند تعريف أنواع الملفات باستخدام **الأمر cmdlet Set-SPOTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد إضافة أنواع ملفات إضافية إلى القائمة، فاستخدم الأمر cmdlet أولا لمعرفة أنواع الملفات المسموح بها بالفعل، ثم قم بتضمينها في القائمة مع أنواع الملفات الجديدة.

استخدم **الأمر cmdlet Set-SPOTenantCdnPolicy** لتعريف أنواع الملفات الثابتة التي يمكن استضافتها بواسطة الأصول العامة والخاصة في CDN. بشكل افتراضي، يتم السماح بأنواع الأصول الشائعة، على سبيل المثال css.، .gif، .jpg، .js.

في Windows PowerShell ل SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

على سبيل المثال، لتمكين CDN من استضافة ملفات css. .png، يجب إدخال الأمر:

```powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

لمعرفة أنواع الملفات المسموح بها حاليا بواسطة CDN، استخدم **الأمر cmdlet Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

لمزيد من المعلومات حول هذه cmdlets، راجع [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) و [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>تغيير قائمة تصنيفات المواقع التي تريد استبعادها من Office 365 CDN (اختياري)

> [!TIP]
> عند استبعاد تصنيفات المواقع باستخدام **الأمر cmdlet Set-SPOTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد استبعاد تصنيفات مواقع إضافية، فاستخدم الأمر cmdlet أولا لمعرفة التصنيفات التي تم استبعادها بالفعل ثم قم بإضافتها مع التصنيفات الجديدة.

استخدم **الأمر cmdlet Set-SPOTenantCdnPolicy** لاستبعاد تصنيفات المواقع التي لا تريد إتاحتها عبر CDN. بشكل افتراضي، لا يتم استبعاد تصنيفات المواقع.

في Windows PowerShell ل SharePoint Online:

```powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

لمعرفة تصنيفات المواقع المقيدة حاليا، استخدم **الأمر Cmdlet Get-SPOTenantCdnPolicies** :

```powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

الخصائص التي سيتم إرجاعها هي _IncludeFileExtensions_ و _ExcludeRestrictedSiteClassifications_ و _ExcludeIfNoScriptDisabled_.

تحتوي _الخاصية IncludeFileExtensions_ على قائمة ملحقات الملفات التي سيتم تقديمها من CDN.

> [!NOTE]
> تختلف ملحقات الملفات الافتراضية بين عام وخاصة.

تحتوي _الخاصية ExcludeRestrictedSiteClassifications_ على تصنيفات المواقع التي تريد استبعادها من CDN. على سبيل المثال، يمكنك استثناء المواقع التي تم  وضع علامة سري عليها بحيث لا يتم تقديم المحتوى من المواقع التي تم تطبيق هذا التصنيف عليها من شبكة CDN.

_تستبعد الخاصية ExcludeIfNoScriptDisabled_ المحتوى من CDN استنادا إلى إعدادات سمة _NoScript_ على مستوى الموقع. بشكل افتراضي، يتم تعيين السمة _NoScript_ إلى **"** تمكين _للمواقع_ الحديثة" و **"معطل** _للمواقع الكلاسيكية_ ". يعتمد ذلك على إعدادات المستأجر.

لمزيد من المعلومات حول هذه cmdlets، راجع [Set-SPOTenantCdnPolicy](/powershell/module/sharepoint-online/) و [Get-SPOTenantCdnPolicies](/powershell/module/sharepoint-online/).

<a name="Office365CDNforSPOOriginPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>إضافة أصل لأصولك

استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف أصل. يمكنك تعريف أصول متعددة. الأصل هو عنوان URL يشير إلى SharePoint أو مجلد يحتوي على الأصول التي تريد استضافتها بواسطة CDN.

> [!IMPORTANT]
> يجب ألا تقوم أبدا ب وضع الموارد التي تحتوي على معلومات المستخدم أو التي تعتبر حساسة لمنظمتك في الأصل العام.

```powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

قيمة المسار _هي_ المسار النسبي للمكتبة أو المجلد الذي يحتوي على الأصول. يمكنك استخدام أحرف البدل بالإضافة إلى المسارات النسبية. تدعم الأصول أحرف البدل التي تم إعانتها مسبقا إلى عنوان URL. يسمح لك ذلك بإنشاء أصول تمتد عبر مواقع متعددة. على سبيل المثال، لتضمين كل الأصول في مجلد "الصور الرئيسية" لكل مواقعك كمنشأ عام ضمن شبكة CDN، اكتب الأمر التالي:

```powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ يمكن استخدام معدل أحرف البدل ***/** فقط في بداية المسار، وسيتطابق مع كل أجزاء URL ضمن عنوان URL المحدد.
+ يمكن أن يشير المسار إلى مكتبة مستندات أو مجلد أو موقع. على سبيل المثال، سيطابق المسار _*/site1_ كل مكتبات المستندات ضمن الموقع.

يمكنك إضافة أصل باستخدام مسار نسبي معين. لا يمكنك إضافة أصل باستخدام المسار الكامل.

يضيف هذا المثال أصلا خاصا لمكتبة siteassets على موقع معين:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

يضيف هذا المثال أصلا خاصا لمجلد _المجلد1_ في مكتبة أصول مواقع مجموعة المواقع الموقعة:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

إذا كانت هناك مسافة في المسار، يمكنك إما إحاطة المسار ب علامات اقتباس مزدوجة أو استبدال المسافة ب ترميز URL ٪20. تضيف الأمثلة التالية أصلا خاصا لمجلد المجلد _1_ في مكتبة أصول مواقع مجموعة المواقع الموقعة:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

> [!NOTE]
> في الأصول الخاصة، يجب أن يكون لدى الأصول التي تمت مشاركتها من أصل إصدار رئيسي تم نشره قبل أن يمكن الوصول إليها من CDN.

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePublicOrigin"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>مثال: تكوين أصل عام للصفحات الرئيسية ومكتبة النمط ل SharePoint Online

عادة، يتم إعداد هذه الأصول لك بشكل افتراضي عند تمكين Office 365 CDN. ومع ذلك، إذا كنت تريد تمكينها يدويا، فاتبع الخطوات التالية.

+ استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف مكتبة النمط كمصدر عام.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف الصفحات الرئيسية كمصدر عام.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOrigin"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>مثال: تكوين أصل خاص لأصول الموقع وصفحات الموقع وصور النشر ل SharePoint Online

+ استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف مجلد أصول الموقع كمصدر خاص.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف مجلد صفحات الموقع كمصدر خاص.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف مجلد صور النشر كمصدر خاص.

  ```powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOriginSiteCollection"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>مثال: تكوين أصل خاص لمجموعه مواقع SharePoint Online

استخدم **الأمر cmdlet Add-SPOTenantCdnOrigin** لتعريف مجموعة مواقع ويب كمصدر خاص. على سبيل المثال:

```powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Add-SPOTenantCdnOrigin).

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد تظهر رسالة _تكوين معلقة_ من المتوقع أن يتم SharePoint اتصال المستأجر عبر الإنترنت بالخدمة CDN. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="CDNManage"> </a>
### <a name="manage-the-office-365-cdn"></a>إدارة Office 365 CDN

بعد إعداد CDN، يمكنك إجراء تغييرات على التكوين عند تحديث المحتوى أو عندما تتغير احتياجاتك، كما هو موضح في هذا القسم.

<a name="Office365CDNforSPOaddremoveasset"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>إضافة أصول أو تحديثها أو إزالتها من Office 365 CDN

بعد إكمال خطوات الإعداد، يمكنك إضافة أصول جديدة وتحديث الأصول الموجودة أو إزالتها كلما أردت ذلك. ما عليك سوى إجراء تغييرات على الأصول في المجلد أو SharePoint المكتبة التي حددتها كمنشأ. إذا قمت بإضافة أصل جديد، فإنه يتوفر عبر شبكة CDN على الفور. ومع ذلك، إذا قمت بتحديث الأصل، سيستغرق نشر النسخة الجديدة وتصبح متوفرة في CDN ما يصل إلى 15 دقيقة.

إذا كنت بحاجة إلى استرداد موقع الأصل، يمكنك استخدام **الأمر Get-SPOTenantCdnOrigins** cmdlet. للحصول على معلومات حول كيفية استخدام الأمر cmdlet هذا، راجع [Get-SPOTenantCdnOrigins](/powershell/module/sharepoint-online/Get-SPOTenantCdnOrigins).

<a name="Office365CDNforSPORemoveOriginPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>إزالة أصل من Office 365 CDN

يمكنك إزالة الوصول إلى مجلد أو مكتبة SharePoint قمت بتحديدها كمجلد أصل. للقيام بذلك، استخدم **الأمر cmdlet Remove-SPOTenantCdnOrigin** .

```powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

للحصول على معلومات حول كيفية استخدام الأمر cmdlet هذا، راجع [Remove-SPOTenantCdnOrigin](/powershell/module/sharepoint-online/Remove-SPOTenantCdnOrigin).

<a name="Office365CDNforSPOModifyOrigin"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>تعديل أصل في Office 365 CDN

لا يمكنك تعديل أصل أنشأته. بدلا من ذلك، قم بإزالة الأصل ثم قم بإضافة أصل جديد. لمزيد من المعلومات، راجع إزالة أصل من Office 365 [CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPosh) وإضافة أصل [لأصولك](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>تعطيل Office 365 CDN

استخدم **الأمر cmdlet Set-SPOTenantCdnEnabled** لتعطيل CDN لمنظمتك. إذا تم تمكين الأصلين العام والخاص ل CDN، يجب تشغيل الأمر cmdlet مرتين كما هو موضح في الأمثلة التالية.

لتعطيل استخدام الأصول العامة في CDN، أدخل الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

لتعطيل استخدام الأصول الخاصة في CDN، أدخل الأمر التالي:

```powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

لمزيد من المعلومات حول الأمر cmdlet هذا، راجع [Set-SPOTenantCdnEnabled](/powershell/module/sharepoint-online/Set-SPOTenantCdnEnabled).

</details>

<a name="CDNSetupinPnPPosh"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-pnp-powershell"></a>إعداد قاعدة Office 365 CDN وتكوينها باستخدام PnP PowerShell

تتطلب الإجراءات في هذا القسم استخدام PnP PowerShell للاتصال SharePoint Online. للحصول على الإرشادات، راجع [بدء باستخدام PnP PowerShell](https://github.com/SharePoint/PnP-PowerShell#getting-started).

أكمل هذه الخطوات لإعداد شبكة CDN وتكوينها لاستضافة الأصول في SharePoint Online باستخدام PnP PowerShell.

<details>
  <summary>انقر لتوسيع</summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a>تمكين مؤسستك من استخدام Office 365 CDN

قبل إجراء تغييرات على إعدادات CDN للمستأجر، يجب استرداد الحالة الحالية لتكوين CDN الخاص في Office 365 المستأجر. الاتصال إلى المستأجر باستخدام PnP PowerShell:

```powershell
Connect-PnPOnline -Url https://contoso-admin.sharepoint.com -UseWebLogin
```

استخدم الآن **Cmdlet Get-PnPTenantCdnEnabled** لاسترداد إعدادات حالة CDN من المستأجر:

```powershell
Get-PnPTenantCdnEnabled -CdnType <Public | Private>
```

سيتم إخراج حالة CDN ل CdnType المحدد إلى الشاشة.

استخدم **الأمر cmdlet Set-PnPTenantCdnEnabled** لتمكين مؤسستك من استخدام Office 365 CDN. يمكنك تمكين مؤسستك من استخدام الأصول العامة أو الأصول الخاصة أو كليهما في الوقت نفسه. يمكنك أيضا تكوين CDN لتخطي إعداد الأصول الافتراضية عند تمكينها. يمكنك دائما إضافة هذه الأصول لاحقا كما هو موضح في هذا الموضوع.

في PnP PowerShell:

```powershell
Set-PnPTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

على سبيل المثال، لتمكين مؤسستك من استخدام الأصلين العام والخاص، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true
```

لتمكين مؤسستك من استخدام الأصول العامة والخاصة على حد سواء ولكن تخطي إعداد الأصول الافتراضية، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

راجع [أصول CDN](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) الافتراضية للحصول على معلومات حول الأصول التي يتم توفيرها بشكل افتراضي عند تمكين Office 365 CDN، والتأثير المحتمل لتخطي إعداد الأصول الافتراضية.

لتمكين مؤسستك من استخدام الأصول العامة، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $true
```

لتمكين مؤسستك من استخدام الأصول الخاصة، اكتب الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $true
```

لمزيد من المعلومات حول الأمر cmdlet هذا، راجع [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

<a name="Office365CDNforPnPPoshFileType"> </a>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a>تغيير قائمة أنواع الملفات لتضمينها في Office 365 CDN (اختياري)

> [!TIP]
> عند تعريف أنواع الملفات باستخدام **الأمر cmdlet Set-PnPTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد إضافة أنواع ملفات إضافية إلى القائمة، فاستخدم الأمر cmdlet أولا لمعرفة أنواع الملفات المسموح بها بالفعل، ثم قم بتضمينها في القائمة مع أنواع الملفات الجديدة.

استخدم **الأمر cmdlet Set-PnPTenantCdnPolicy** لتعريف أنواع الملفات الثابتة التي يمكن استضافتها بواسطة الأصول العامة والخاصة في CDN. بشكل افتراضي، يتم السماح بأنواع الأصول الشائعة، على سبيل المثال css.، .gif، .jpg، .js.

في PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

على سبيل المثال، لتمكين CDN من استضافة ملفات css. .png، يجب إدخال الأمر:

```powershell
Set-PnPTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

لمعرفة أنواع الملفات المسموح بها حاليا بواسطة CDN، استخدم **cmdlet Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

لمزيد من المعلومات حول cmdlets هذه، راجع [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) و [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforPnPPoshSiteClassification"> </a>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a>تغيير قائمة تصنيفات المواقع التي تريد استبعادها من Office 365 CDN (اختياري)

> [!TIP]
> عند استبعاد تصنيفات المواقع باستخدام **الأمر cmdlet Set-PnPTenantCdnPolicy** ، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد استبعاد تصنيفات مواقع إضافية، فاستخدم الأمر cmdlet أولا لمعرفة التصنيفات التي تم استبعادها بالفعل ثم قم بإضافتها مع التصنيفات الجديدة.

استخدم **الأمر cmdlet Set-PnPTenantCdnPolicy** لاستبعاد تصنيفات المواقع التي لا تريد جعلها متوفرة عبر CDN. بشكل افتراضي، لا يتم استبعاد تصنيفات المواقع.

في PnP PowerShell:

```powershell
Set-PnPTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications>"
```

لمعرفة تصنيفات المواقع المقيدة حاليا، استخدم **cmdlet Get-PnPTenantCdnPolicies** :

```powershell
Get-PnPTenantCdnPolicies -CdnType <Public | Private>
```

الخصائص التي سيتم إرجاعها هي _IncludeFileExtensions_ و _ExcludeRestrictedSiteClassifications_ و _ExcludeIfNoScriptDisabled_.

تحتوي _الخاصية IncludeFileExtensions_ على قائمة ملحقات الملفات التي سيتم تقديمها من CDN.

> [!NOTE]
> تختلف ملحقات الملفات الافتراضية بين عام وخاصة.

تحتوي _الخاصية ExcludeRestrictedSiteClassifications_ على تصنيفات المواقع التي تريد استبعادها من CDN. على سبيل المثال، يمكنك استثناء المواقع التي تم  وضع علامة سري عليها بحيث لا يتم تقديم المحتوى من المواقع التي تم تطبيق هذا التصنيف عليها من شبكة CDN.

_تستبعد الخاصية ExcludeIfNoScriptDisabled_ المحتوى من CDN استنادا إلى إعدادات سمة _NoScript_ على مستوى الموقع. بشكل افتراضي، يتم تعيين السمة _NoScript_ إلى **"** تمكين _للمواقع_ الحديثة" و **"معطل** _للمواقع الكلاسيكية_ ". يعتمد ذلك على إعدادات المستأجر.

لمزيد من المعلومات حول cmdlets هذه، راجع [Set-PnPTenantCdnPolicy](/powershell/module/sharepoint-pnp/set-pnptenantcdnpolicy) و [Get-PnPTenantCdnPolicies](/powershell/module/sharepoint-pnp/get-pnptenantcdnpolicies).

<a name="Office365CDNforSPOOriginPnPPosh"> </a>
### <a name="add-an-origin-for-your-assets"></a>إضافة أصل لأصولك

استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف أصل. يمكنك تعريف أصول متعددة. الأصل هو عنوان URL يشير إلى SharePoint أو مجلد يحتوي على الأصول التي تريد استضافتها بواسطة CDN.

> [!IMPORTANT]
> يجب ألا تقوم أبدا ب وضع الموارد التي تحتوي على معلومات المستخدم أو التي تعتبر حساسة لمنظمتك في الأصل العام.

```powershell
Add-PnPTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

قيمة المسار _هي_ المسار النسبي للمكتبة أو المجلد الذي يحتوي على الأصول. يمكنك استخدام أحرف البدل بالإضافة إلى المسارات النسبية. تدعم الأصول أحرف البدل التي تم إعانتها مسبقا إلى عنوان URL. يسمح لك ذلك بإنشاء أصول تمتد عبر مواقع متعددة. على سبيل المثال، لتضمين كل الأصول في مجلد "الصور الرئيسية" لكل مواقعك كمنشأ عام ضمن شبكة CDN، اكتب الأمر التالي:

```powershell
Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ يمكن استخدام معدل أحرف البدل ***/** فقط في بداية المسار، وسيتطابق مع كل أجزاء URL ضمن عنوان URL المحدد.
+ يمكن أن يشير المسار إلى مكتبة مستندات أو مجلد أو موقع. على سبيل المثال، سيطابق المسار _*/site1_ كل مكتبات المستندات ضمن الموقع.

يمكنك إضافة أصل باستخدام مسار نسبي معين. لا يمكنك إضافة أصل باستخدام المسار الكامل.

يضيف هذا المثال أصل خاص لمكتبة أصول الموقع على موقع معين:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

يضيف هذا المثال أصلا خاصا لمجلد _المجلد1_ في مكتبة أصول مواقع مجموعة المواقع الموقعة:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

إذا كانت هناك مسافة في المسار، يمكنك إما إحاطة المسار ب علامات اقتباس مزدوجة أو استبدال المسافة ب ترميز URL ٪20. تضيف الأمثلة التالية أصلا خاصا لمجلد المجلد _1_ في مكتبة أصول مواقع مجموعة المواقع الموقعة:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

> [!NOTE]
> في الأصول الخاصة، يجب أن يكون لدى الأصول التي تمت مشاركتها من أصل إصدار رئيسي تم نشره قبل أن يمكن الوصول إليها من CDN.

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePublicOriginPnPPosh"> </a>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a>مثال: تكوين أصل عام للصفحات الرئيسية ومكتبة النمط ل SharePoint Online

عادة، يتم إعداد هذه الأصول لك بشكل افتراضي عند تمكين Office 365 CDN. ومع ذلك، إذا كنت تريد تمكينها يدويا، فاتبع الخطوات التالية.

+ استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف مكتبة النمط كمنشأ عام.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف الصفحات الرئيسية كمنشأ عام.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOriginPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a>مثال: تكوين أصل خاص لأصول الموقع وصفحات الموقع وصور النشر ل SharePoint Online

+ استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف مجلد أصول الموقع كمجلد أصل خاص.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف مجلد صفحات الموقع على أنه أصل خاص.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف مجلد صور النشر كمصدر خاص.

  ```powershell
  Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="ExamplePrivateOriginSiteCollectionPnPPosh"> </a>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a>مثال: تكوين أصل خاص لمجموعه مواقع SharePoint Online

استخدم **الأمر cmdlet Add-PnPTenantCdnOrigin** لتعريف مجموعة مواقع ويب كمنشأ خاص. على سبيل المثال:

```powershell
Add-PnPTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

لمزيد من المعلومات حول هذا الأمر بناء الجملة، راجع [Add-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/add-pnptenantcdnorigin).

بعد تشغيل الأمر، يتزامن النظام مع التكوين عبر مركز البيانات. قد تظهر رسالة _تكوين معلقة_ من المتوقع أن يتم SharePoint اتصال المستأجر عبر الإنترنت بالخدمة CDN. قد يستغرق ذلك ما يصل إلى 15 دقيقة.

<a name="CDNManagePnPPosh"> </a>
### <a name="manage-the-office-365-cdn"></a>إدارة Office 365 CDN

بعد إعداد CDN، يمكنك إجراء تغييرات على التكوين عند تحديث المحتوى أو عندما تتغير احتياجاتك، كما هو موضح في هذا القسم.

<a name="Office365CDNforSPOaddremoveassetPnPPosh"> </a>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a>إضافة أصول أو تحديثها أو إزالتها من Office 365 CDN

بعد إكمال خطوات الإعداد، يمكنك إضافة أصول جديدة وتحديث الأصول الموجودة أو إزالتها كلما أردت ذلك. ما عليك سوى إجراء تغييرات على الأصول في المجلد أو SharePoint المكتبة التي حددتها كمنشأ. إذا قمت بإضافة أصل جديد، فإنه يتوفر عبر شبكة CDN على الفور. ومع ذلك، إذا قمت بتحديث الأصل، سيستغرق نشر النسخة الجديدة وتصبح متوفرة في CDN ما يصل إلى 15 دقيقة.

إذا كنت بحاجة إلى استرداد موقع الأصل، يمكنك استخدام **الأمر Get-PnPTenantCdnOrigin** cmdlet. للحصول على معلومات حول كيفية استخدام الأمر cmdlet هذا، راجع [Get-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/get-pnptenantcdnorigin).

<a name="Office365CDNforSPORemoveOriginPnPPosh"> </a>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a>إزالة أصل من Office 365 CDN

يمكنك إزالة الوصول إلى مجلد أو مكتبة SharePoint قمت بتحديدها كمجلد أصل. للقيام بذلك، استخدم **الأمر cmdlet Remove-PnPTenantCdnOrigin** .

```powershell
Remove-PnPTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

للحصول على معلومات حول كيفية استخدام الأمر cmdlet هذا، راجع [Remove-PnPTenantCdnOrigin](/powershell/module/sharepoint-pnp/remove-pnptenantcdnorigin).

<a name="Office365CDNforSPOModifyOriginPnPPosh"> </a>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a>تعديل أصل في Office 365 CDN

لا يمكنك تعديل أصل أنشأته. بدلا من ذلك، قم بإزالة الأصل ثم قم بإضافة أصل جديد. لمزيد من المعلومات، راجع إزالة أصل من Office 365 [CDN](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPORemoveOriginPnPPosh) وإضافة أصل [لأصولك](use-microsoft-365-cdn-with-spo.md#Office365CDNforSPOOriginPnPPosh).

<a name="Office365CDNforSPODisable"> </a>
#### <a name="disable-the-office-365-cdn"></a>تعطيل Office 365 CDN

استخدم **الأمر cmdlet Set-PnPTenantCdnEnabled** لتعطيل CDN لمنظمتك. إذا تم تمكين الأصلين العام والخاص ل CDN، يجب تشغيل الأمر cmdlet مرتين كما هو موضح في الأمثلة التالية.

لتعطيل استخدام الأصول العامة في CDN، أدخل الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Public -Enable $false
```

لتعطيل استخدام الأصول الخاصة في CDN، أدخل الأمر التالي:

```powershell
Set-PnPTenantCdnEnabled -CdnType Private -Enable $false
```

لمزيد من المعلومات حول الأمر cmdlet هذا، راجع [Set-PnPTenantCdnEnabled](/powershell/module/sharepoint-pnp/set-pnptenantcdnenabled).

</details>

<a name="CDNSetupinCLI"> </a>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-cli-for-microsoft-365"></a>إعداد قاعدة Office 365 CDN وتكوينها باستخدام CLI Microsoft 365

تتطلب الإجراءات في هذا القسم تثبيت [CLI Microsoft 365](https://aka.ms/cli-m365). بعد ذلك، اتصل Office 365 المستأجر باستخدام [أمر تسجيل](https://pnp.github.io/cli-microsoft365/cmd/login/) الدخول.

أكمل هذه الخطوات لإعداد CDN وتكوينها لاستضافة الأصول في SharePoint Online باستخدام CLI Microsoft 365.

<details>
  <summary>انقر لتوسيع</summary>

### <a name="enable-the-office-365-cdn"></a>تمكين Office 365 CDN

يمكنك إدارة حالة Office 365 CDN في المستأجر باستخدام الأمر [مجموعة spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-set/).

لتمكين الوصول Office 365 CDN العامة في المستأجر، نفذ ما يلي:

```cli
spo cdn set --type Public --enabled true
```

لتمكين CDN Office 365 SharePoint، نفذ:

```cli
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a>عرض الحالة الحالية ل Office 365 CDN

للتحقق مما إذا كان نوع Office 365 CDN معينا أو معطلا، استخدم الأمر [الحصول على spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-get/).

للتحقق مما إذا كانت Office 365 CDN العامة تم تمكينها، قم بتنفيذ:

```cli
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a>عرض Office 365 CDN

لعرض الإعدادات المكونة Office 365 العامة لأصول CDN، قم بتنفيذ:

```cli
spo cdn origin list --type Public
```

راجع [أصول CDN الافتراضية](use-microsoft-365-cdn-with-spo.md#default-cdn-origins) للحصول على معلومات حول الأصول التي يتم توفيرها بشكل افتراضي عند تمكين Office 365 CDN.

### <a name="add-an-office-365-cdn-origin"></a>إضافة Office 365 CDN

> [!IMPORTANT]
> يجب ألا تقوم أبدا ب وضع الموارد التي تعتبر حساسة لمنظمتك في مكتبة مستندات SharePoint تم تكوينها كأصل عام.

استخدم الأمر [إضافة أصل spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-add/) لتعريف أصل CDN. يمكنك تعريف أصول متعددة. الأصل هو عنوان URL يشير إلى SharePoint أو مجلد يحتوي على الأصول التي تريد استضافتها بواسطة CDN.

```cli
spo cdn origin add --type [Public | Private] --origin <path>
```

أين `path` يوجد المسار النسبي للمجلد الذي يحتوي على الأصول. يمكنك استخدام أحرف البدل بالإضافة إلى المسارات النسبية.

لتضمين كافة الأصول في معرض الصفحات **الرئيسية** لكل المواقع باعتبارها أصولا عامة، قم بتنفيذ:

```cli
spo cdn origin add --type Public --origin */masterpage
```

لتكوين أصل خاص لمجموعه مواقع محددة، قم بتنفيذ:

```cli
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> بعد إضافة أصل CDN، قد يستغرق الأمر ما يصل إلى 15 دقيقة لكي تتمكن من استرداد الملفات عبر خدمة CDN. يمكنك التحقق مما إذا كان الأصل الخاص قد تم تمكينه بالفعل باستخدام الأمر [قائمة أصل spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) .

### <a name="remove-an-office-365-cdn-origin"></a>إزالة Office 365 CDN

استخدم أمر [إزالة أصل spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-remove/) لإزالة أصل CDN لنوع CDN المحدد.

لإزالة أصل عام من تكوين CDN، قم بتنفيذ:

```cli
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> لا تؤثر إزالة أصل CDN على الملفات المخزنة في أي مكتبة مستندات تتطابق مع ذلك الأصل. إذا تم الإشارة إلى هذه الأصول باستخدام عنوان URL الخاص SharePoint، SharePoint تلقائيا إلى عنوان URL الأصلي الذي يشير إلى مكتبة المستندات. ومع ذلك، إذا تمت الإشارة إلى الأصول باستخدام عنوان URL CDN عام، فإن إزالة الأصل ستقطع الارتباط وستحتاج إلى تغييرها يدويا.

### <a name="modify-an-office-365-cdn-origin"></a>تعديل أصل Office 365 CDN

لا يمكن تعديل أصل CDN موجود. بدلا من ذلك، يجب إزالة أصل CDN المعرف مسبقا باستخدام `spo cdn origin remove` الأمر وإضافة أمر جديد باستخدام `spo cdn origin add` الأمر.

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a>تغيير أنواع الملفات لتضمينها في Office 365 CDN

بشكل افتراضي، يتم تضمين أنواع الملفات التالية في CDN: _.css و .eot و .gif و .ico و .jpeg و .jpg و .js و .map و .png و .svg و .ttf و .woff و .woff2_. إذا كنت بحاجة إلى تضمين أنواع ملفات إضافية في CDN، يمكنك تغيير تكوين CDN باستخدام الأمر [مجموعة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) .

> [!NOTE]
> عند تغيير قائمة أنواع الملفات، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد تضمين أنواع ملفات إضافية، فاستخدم أولا الأمر [قائمة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-origin-list/) لمعرفة أنواع الملفات التي تم تكوينها حاليا.

لإضافة نوع _ملف JSON_ إلى القائمة الافتراضية لأنواع الملفات المضمنة في CDN العامة، قم بتنفيذ:

```cli
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a>تغيير قائمة تصنيفات المواقع التي تريد استبعادها من Office 365 CDN

استخدم الأمر [مجموعة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-set/) لاستبعاد تصنيفات المواقع التي لا تريد جعلها متوفرة عبر CDN. بشكل افتراضي، لا يتم استبعاد تصنيفات المواقع.

> [!NOTE]
> عند تغيير قائمة تصنيفات المواقع المستبعدة، يمكنك الكتابة فوق القائمة المعرفة حاليا. إذا كنت تريد استثناء تصنيفات إضافية، فاستخدم أولا الأمر [قائمة نهج spo cdn](https://pnp.github.io/cli-microsoft365/cmd/spo/cdn/cdn-policy-list/) لمعرفة التصنيفات التي تم تكوينها حاليا.

لاستبعاد المواقع المصنفة _ك HBI_ من شبكة CDN العامة، نفذ

```cli
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a>تعطيل Office 365 CDN

لتعطيل Office 365 CDN، `spo cdn set` استخدم الأمر، على سبيل المثال:

```cli
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a>استخدام أصول CDN

الآن وقد قمت بتمكين CDN وتكوين الأصول والسياسات، يمكنك البدء باستخدام أصول CDN.

سيساعدك هذا القسم على فهم كيفية استخدام عناوين URL ل CDN في صفحات SharePoint والمحتوى بحيث يعيد SharePoint توجيه طلبات الأصول في الأصلين العام والخاص إلى CDN.

+ [تحديث الارتباطات إلى أصول CDN](use-microsoft-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [استخدام الأصول في الأصول العامة](use-microsoft-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [استخدام الأصول في الأصول الخاصة](use-microsoft-365-cdn-with-spo.md#using-assets-in-private-origins)

للحصول على معلومات حول كيفية استخدام CDN لاستضافة أجزاء ويب من جانب العميل، راجع الموضوع استضافة جزء ويب من جانب العميل من Office 365 [CDN (الجزء 4 من Hello World)](/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).

> [!NOTE]
> إذا أضفت مجلد _ClientSideAssets_ إلى قائمة **أصول CDN** الخاصة، ستفشل أجزاء ويب المخصصة المستضافة في CDN في العرض. يمكن للملفات التي تستخدمها أجزاء ويب SPFX استخدام CDN العام فقط، كما أن مجلد ClientSideAssets هو أصل افتراضي ل CDN العام.

### <a name="updating-links-to-cdn-assets"></a>تحديث الارتباطات إلى أصول CDN

لاستخدام الأصول التي أضفتها إلى أصل، ما عليك سوى تحديث الارتباطات إلى الملف الأصلي باستخدام المسار إلى الملف الموجود في الأصل.

+ قم بتحرير الصفحة أو المحتوى الذي يحتوي على ارتباطات إلى الأصول التي أضفتها إلى أصل. يمكنك أيضا استخدام أحد الأساليب العديدة للبحث بشكل عمومي عن الارتباطات واستبدالها عبر موقع أو مجموعة مواقع ويب إذا كنت تريد تحديث الارتباط لأصل معين في كل مكان يظهر فيه.
+ لكل ارتباط إلى أصل، استبدل المسار بالمسار إلى الملف الموجود في أصل CDN. يمكنك استخدام المسارات النسبية.
+ احفظ الصفحة أو المحتوى.

على سبيل المثال، فكر في الصورة _/site/SiteAssets/images/image.png_، التي نسختها إلى مجلد _مكتبة المستندات /site/CDN_origins/public/_. لاستخدام أصل CDN، استبدل المسار الأصلي لموقع ملف الصورة بالمسار إلى الأصل لجعل عنوان URL _/site/CDN_origins/public/image.png_.

إذا كنت تريد استخدام عنوان URL الكامل للأصول بدلا من مسار نسبي، فنشئ الارتباط كما يلي:

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> بشكل عام، يجب عدم استخدام عناوين URL للترميز الثابت مباشرة إلى الأصول في CDN. ومع ذلك، يمكنك إنشاء عناوين URL يدويا للأصول في الأصول العامة إذا لزم الأمر. لمزيد من المعلومات، راجع [عناوين URL ل CDN لتشطيب عناوين URL للأصول العامة](use-microsoft-365-cdn-with-spo.md#constructing-cdn-urls-for-public-assets).

للتعرف على كيفية التحقق من أن الأصول يتم تقديمها من CDN، راجع كيف يمكنني تأكيد أن الأصول يتم خدمتها بواسطة [CDN؟](use-microsoft-365-cdn-with-spo.md#CDNConfirm) في استكشاف الأخطاء وإصلاحها Office 365 [CDN](use-microsoft-365-cdn-with-spo.md#CDNTroubleshooting).

### <a name="using-assets-in-public-origins"></a>استخدام الأصول في الأصول العامة

تقوم  ميزة النشر في SharePoint Online تلقائيا بإعادة كتابة عناوين URL للأصول المخزنة في أصول عامة إلى مكافئات CDN الخاصة بها بحيث يتم تقديم الأصول من خدمة CDN بدلا من SharePoint.

إذا كان أصلك موجودا في موقع تم تمكين ميزة النشر فيه، وكانت الأصول التي تريد تفريغها إلى شبكة CDN في إحدى الفئات التالية، سيعيد SharePoint كتابة عناوين URL لأصول الأصل تلقائيا، شرط عدم استبعاد الأصل بواسطة نهج CDN.

فيما يلي نظرة عامة حول الارتباطات التي يتم إعادة كتابتها تلقائيا بواسطة SharePoint النشر:

+ عناوين URL ل IMG/LINK/CSS في استجابات HTML لصفحة النشر الكلاسيكية
  + يشمل ذلك الصور التي أضافها الكتاب ضمن محتوى HTML لصفحة
+ عناوين URL للصورة "عرض شرائح مكتبة الصور"
+ حقول الصور في نتائج SPList REST API (RenderListDataAsStream)
  + استخدام الخاصية _الجديدة ImageFieldsToTryRewriteToCdnUrls_ لتوفير قائمة حقول مفصولة بفصول
  + دعم حقول الارتباطات التشعبية والحقول PublishingImage
+ SharePoint الصور

يوضح الرسم التخطيطي التالي سير العمل عندما يتلقى SharePoint طلب صفحة تحتوي على أصول من أصل عام.

![رسم تخطيطي لسير العمل: استرداد Office 365 CDN من أصل عام.](../media/O365-CDN/o365-cdn-public-steps-transparent.png "سير العمل: استرداد Office 365 CDN من أصل عام")

> [!TIP]
> إذا كنت تريد تعطيل إعادة الكتابة التلقائية الخاصة عناوين URL معينة على صفحة، يمكنك سحب الصفحة وإضافة معلمة سلسلة الاستعلام **؟ NoAutoReWrites=true** إلى نهاية كل ارتباط تريد تعطيله.

#### <a name="constructing-cdn-urls-for-public-assets"></a>إنشاء عناوين URL CDN للأصول العامة

إذا لم  يتم تمكين ميزة النشر لأصل عام، أو إذا لم يكن الأصل أحد أنواع الارتباطات المعتمدة بواسطة ميزة إعادة الكتابة التلقائية لخدمة CDN، يمكنك إنشاء عناوين URL يدويا إلى موقع CDN للأصول واستخدام عناوين URL هذه في المحتوى.

> [!NOTE]
> لا يمكنك إنشاء عناوين URL ل CDN أو ترميزها لأصول ذات أصل خاص لأن رمز الوصول المميز المطلوب الذي يشكل المقطع الأخير من عنوان URL يتم إنشاؤه في الوقت الذي يتم فيه طلب المورد. يمكنك إنشاء URL الخاص ب CDN العام ويجب ألا يتم الترميز الثابت ل URL حيث إنه عرضة للتغيير.

بالنسبة لأصول CDN العامة، سيبدو تنسيق URL كما يلي:

```http
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

**استبدل TenantHostName** باسم المستأجر. على سبيل المثال:

```http
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

> [!NOTE]
> يجب استخدام خاصية سياق الصفحة لإنشاء البادرة بدلا من الترميز الثابت "https://publiccdn.sharepointonline.com". عنوان URL عرضة للتغيير ويجب ألا يتم الترميز الثابت له. إذا كنت تستخدم قوالب العرض مع classic SharePoint Online، يمكنك استخدام الخاصية "window._spPageContextInfo.publicCdnBaseUrl" في قالب العرض لبادئه عنوان URL. إذا كنت تستخدم إطار عمل SharePoint ويب للأجزاء الحديثة والكلاسيكية SharePoint يمكنك استخدام الخاصية "this.context.pageContext.legacyPageContext.publicCdnBaseUrl". سيوفر ذلك البادئه بحيث يتم تحديث التنفيذ بها إذا تم تغييرها. كمثال ل إطار عمل SharePoint، يمكن إنشاء عنوان URL باستخدام الخاصية "this.context.pageContext.legacyPageContext.publicCdnBaseUrl" + "/" + "host" + "/" + "relativeURL الخاص العنصر". الرجاء الاطلاع [على استخدام CDN في التعليمات البرمجية](https://youtu.be/IH1RbQlbhIA) من جانب العميل التي هي جزء من [سلسلة أداء الموسم 1](https://aka.ms/sppnp-perfvideos)


### <a name="using-assets-in-private-origins"></a>استخدام الأصول في الأصول الخاصة

لا يلزم تكوين إضافي لاستخدام الأصول في الأصول الخاصة. SharePoint يقوم Online تلقائيا بإعادة كتابة عناوين URL للأصول في أصول خاصة بحيث يتم دائما تقديم طلبات هذه الأصول من CDN. لا يمكنك إنشاء عناوين URL يدويا لأصول CDN في أصول خاصة لأن عناوين URL هذه تحتوي على رموز مميزه يجب إنشاؤها تلقائيا بواسطة SharePoint عبر الإنترنت في الوقت الذي يتم فيه طلب الأصل.

يتم حماية الوصول إلى الأصول في الأصول الخاصة بواسطة الرموز المميزة التي يتم إنشاؤها ديناميكيا استنادا إلى أذونات المستخدمين في الأصل، مع التحذيرات الموضحة في الأقسام التالية. يجب أن **يكون لدى** المستخدمين حق الوصول للقراءة على الأقل إلى أصول CDN لكي يعرضوا المحتوى.

يوضح الرسم التخطيطي التالي سير العمل عندما يتلقى SharePoint طلب صفحة تحتوي على أصول من أصل خاص.

![رسم تخطيطي لسير العمل: استرداد Office 365 CDN من أصل خاص.](../media/O365-CDN/o365-cdn-private-steps-transparent.png "سير العمل: استرداد Office 365 CDN من أصل خاص")

#### <a name="token-based-authorization-in-private-origins"></a>التخويل المستند إلى الرمز المميز في الأصول الخاصة

يتم منح حق الوصول إلى الأصول في أصول خاصة في Office 365 CDN بواسطة الرموز المميزة التي تم إنشاؤها بواسطة SharePoint Online. يتم منح المستخدمين الذين لديهم إذن الوصول إلى المجلد أو المكتبة المعينة بواسطة الأصل تلقائيا الرموز المميزة التي تسمح للمستخدم بالوصول إلى الملف استنادا إلى مستوى الأذونات الخاص به. تكون رموز الوصول المميزة هذه صالحة لمدة 30 إلى 90 دقيقة بعد إنشاؤها للمساعدة في منع هجمات إعادة عرض الرموز.

بمجرد إنشاء رمز الوصول المميز، SharePoint Online بإرجاع URI مخصص للعميل يحتوي على معلمتي تخويل _تناول (_ الرمز المميز لتخويل الحافة) والشوفان _(الرمز_ المميز للتخويل الأصلي). يتم تحديد بنية كل _رمز مميز< انتهاء_ الصلاحية في تنسيق الوقت >__< توقيع آمن >. على سبيل المثال:

```http
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> يمكن لأي شخص في حوزته الوصول إلى المورد في CDN. ومع ذلك، لا يتم مشاركة عناوين URL التي تحتوي على رموز الوصول المميزة هذه إلا عبر HTTPS، وبالتالي، لن يتمكن المستخدمون غير المصرح لهم من الوصول إلى عنوان URL إلا إذا تمت مشاركة عنوان URL بشكل صريح قبل انتهاء صلاحية الرمز المميز.

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a>الأذونات على مستوى العنصر غير معتمدة للأصول في الأصول الخاصة

من المهم ملاحظة أن SharePoint Online لا يدعم الأذونات على مستوى العنصر للأصول في الأصول الخاصة. على سبيل المثال، بالنسبة إلى ملف موجود في `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`، يمكن للمستخدمين الوصول الفعال إلى الملف بالشروط التالية:

|User  |الأذونات  |الوصول الفعال  |
|---------|---------|---------|
|المستخدم 1     |لديه حق الوصول إلى المجلد1         |إمكانية الوصول image1.jpg من CDN         |
|المستخدم 2     |لا يمكن الوصول إلى المجلد1         |يتعذر الوصول image1.jpg من CDN         |
|المستخدم 3     |لا يمكن الوصول إلى المجلد1، ولكن يتم منحه إذنا صريحا للوصول إلى image1.jpg في SharePoint Online         |يمكن الوصول إلى image1.jpg مباشرة من SharePoint Online، ولكن ليس من CDN         |
|المستخدم 4     |لديه حق الوصول إلى المجلد1، ولكن تم رفضه صراحة الوصول إلى image1.jpg في SharePoint Online         |لا يمكن الوصول إلى الأصل من SharePoint Online، ولكن يمكنه الوصول إلى الأصل من شبكة CDN على الرغم من رفض الوصول إلى الملف في SharePoint Online         |

<a name="CDNTroubleshooting"></a>

## <a name="troubleshooting-the-office-365-cdn"></a>استكشاف الأخطاء وإصلاحها Office 365 CDN

<a name="CDNConfirm"></a>

### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a>كيف يمكنني تأكيد أن الأصول يتم تقديمها بواسطة CDN؟

بعد إضافة ارتباطات إلى أصول CDN إلى صفحة، يمكنك تأكيد أن الأصل يتم تقديمه من شبكة CDN من خلال الاستعراض إلى الصفحة، والنقر بيمين فوق الصورة بمجرد عرض عنوان URL للصورة ومراجعته.

يمكنك أيضا استخدام أدوات المطور في المستعرض لعرض عنوان URL لكل أصل على صفحة، أو استخدام أداة تتبع شبكة جهة خارجية.

> [!NOTE]
> إذا كنت تستخدم أداة شبكة مثل Fiddler لاختبار الأصول خارج عرض الأصل من صفحة SharePoint، فيجب إضافة رأس الحكم يدويا "المشير: `https://yourdomain.sharepoint.com`" إلى طلب GET حيث URL هو URL الجذر لمستأجر SharePoint Online.

لا يمكنك اختبار عناوين URL ل CDN مباشرة في مستعرض ويب لأنه يجب أن يكون لديك SharePoint Online. ومع ذلك، إذا أضفت عنوان URL لأصل CDN إلى صفحة SharePoint ثم فتحت الصفحة في مستعرض، فستعرض أصول CDN على الصفحة.

لمزيد من المعلومات حول استخدام أدوات المطور في Microsoft Edge المستعرض، راجع Microsoft Edge [أدوات المطور](/microsoft-edge/devtools-guide).

لمشاهدة فيديو قصير مستضاف في قناة [YouTube](https://aka.ms/sppnp-videos) SharePoint أنماط المطورين وممارساتهم يظهر كيفية التحقق من عمل شبكة CDN، الرجاء الاطلاع على التحقق من استخدام [CDN](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5) وضمان الاتصال الأمثل بالشبكة.

### <a name="why-are-assets-from-a-new-origin-unavailable"></a>لماذا الأصول من أصل جديد غير متوفرة؟
لن تتوفر الأصول في الأصول الجديدة للاستخدام على الفور، حيث يستغرق نشر التسجيل عبر شبكة CDN ولتحميل الأصول من الأصل إلى مساحة تخزين CDN. يتوقف الوقت المطلوب لتوفر الأصول في شبكة CDN على عدد الأصول وحجم الملفات.

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a>لا يعمل جزء الويب الخاص إطار عمل SharePoint العميل

عندما تقوم بتمكين Office 365 CDN لأصول عامة، تقوم خدمة CDN تلقائيا بإنشاء هذه الأصول الافتراضية:

+ */MASTERPAGE
+ */STYLE LIBRARY
+ */CLIENTSIDEASSETS

إذا كان أصل */clientsideassets مفقودا، إطار عمل SharePoint فشل الحلول، ولن يتم إنشاء رسائل تحذير أو خطأ. قد يكون هذا الأصل مفقودا إما لأنه تم تمكين CDN باستخدام _المعلمة NoDefaultOrigins_ التي تم تعيينها $true أو بسبب حذف الأصل يدويا.

يمكنك التحقق لمعرفة الأصول الموجودة باستخدام الأمر PowerShell التالي:

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

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a>ما هي وحدات PowerShell النمطية وقذائف CLI التي أحتاج إليها للعمل مع Office 365 CDN؟

يمكنك اختيار العمل مع شبكة OFFICE 365 CDN باستخدام الوحدة النمطية SharePoint **Online Management Shell** PowerShell أو Office 365 **CLI**.

+ [بدء العمل مع SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
+ [تثبيت Office 365 CLI](https://pnp.github.io/cli-microsoft365/user-guide/installing-cli/)

## <a name="see-also"></a>راجع أيضًا

[شبكات تسليم المحتوى](./content-delivery-networks.md)

[تخطيط الشبكة وضبط الأداء Office 365](./network-planning-and-performance.md)

[SharePoint سلسلة أداء - Office 365 فيديو CDN](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
