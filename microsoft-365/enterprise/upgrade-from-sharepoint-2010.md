---
title: الترقية من SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 04/13/2020
audience: ITPro
ms.topic: conceptual
ms.prod: office-online-server
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
search.appverid:
- MET150
- WSU140
- OSU140
ms.assetid: 985a357f-6db7-401f-bf7a-1bafdf1f312c
f1.keywords:
- NOCSH
description: ابحث عن المعلومات والموارد للترقية من SharePoint 2010 وخادم SharePoint 2010. دعم كلا طرفي 13 أبريل 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: eba7c6739aef420bc90ef866dbd6f3becbccd8ff
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115950"
---
# <a name="upgrading-from-sharepoint-2010"></a>الترقية من SharePoint 2010

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

سيصل Microsoft SharePoint 2010 وser SharePoint Server 2010 إلى نهاية الدعم في **13 أبريل 2021**. توفر هذه المقالة موارد لمساعدتك في ترحيل بيانات SharePoint Server 2010 الموجودة إلى SharePoint Online في Microsoft 365 أو ترقية بيئة SharePoint Server 2010 المحلية.

## <a name="what-is-end-of-support"></a>ما هي *نهاية الدعم*؟

تحتوي معظم منتجات Microsoft على دورة حياة دعم، تحصل خلالها على ميزات جديدة وتصحيحات الأخطاء وتصحيحات الأمان وما إلى ذلك. بعد تاريخ انتهاء الدعم، لا يتوقف المنتج عن العمل، ولكن لم تعد Microsoft توفر:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء للمشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان للثغرات الأمنية التي قد تجعل الخادم عرضة للخروقات الأمنية.

- تحديثات المنطقة الزمنية.

وهذا يعني أنه لن تكون هناك تحديثات أو تصحيحات أو إصلاحات أخرى للمنتج (بما في ذلك تصحيحات/إصلاحات الأمان). سيحول دعم Microsoft جهود الدعم بالكامل إلى الإصدارات الأحدث.

مع اقتراب نهاية دعم SharePoint Server 2010، احذف البيانات التي لم تعد بحاجة إليها قبل ترقية المنتج وترحيل بياناتك المهمة.

> [!NOTE]
> تستمر دورة حياة البرنامج عادة لمدة عشر سنوات من الإصدار الأولي. يمكن [لموفري حلول Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) مساعدتك في الترقية إلى الإصدار التالي من البرنامج أو الترحيل إلى Microsoft 365 الترحيل (أو كليهما). تأكد من أنك على دراية بتواريخ نهاية الدعم للتقنيات الأساسية الهامة أيضا، خاصة لإصدار Microsoft SQL Server الذي تستخدمه مع SharePoint. لمزيد من المعلومات، راجع [نهج دورة الحياة الثابتة](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>التخطيط مسبقا

تحقق من التواريخ التي تدعم انتهاء في [موقع دورة حياة المنتج](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). خطط لترقياتك أو عمليات الترحيل مع وضع هذه التواريخ في الاعتبار. تذكر أن منتجك *لن يتوقف عن العمل* في التاريخ المدرج. ولكن نظرا إلى أنه لن يتم تصحيح التثبيت بعد ذلك التاريخ، فسترغب في التخطيط لانتقال سلس إلى الإصدار التالي من المنتج.

تساعد هذه المصفوفة على رسم دورة تدريبية بين خيارات الترحيل:

|منتج نهاية الدعم|جيده |افضل|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (محلي)|SharePoint Online|
||SharePoint Server 2013 مختلط مع SharePoint Online|SharePoint Server 2016 (محلي)|
|||SharePoint البحث المختلط على السحابة|

إذا اخترت خيارا على الطرف المنخفض من المقياس (جيد)، فستحتاج إلى بدء التخطيط لترقية أخرى بعد وقت قصير من الترحيل من SharePoint Server 2010.

فيما يلي المسارات الثلاثة التي يمكنك اتباعها لتجنب نهاية دعم SharePoint Server 2010.

![مسارات ترقية SharePoint Server 2010.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> نهاية دعم SharePoint Server 2010 و SharePoint Foundation 2010 مجدول حاليا في 13 أبريل 2021. ولكن تأكد من التحقق من [موقع دورة حياة المنتج](https://support.microsoft.com/lifecycle) لمعرفة التواريخ الأحدث.

## <a name="whats-next"></a>ماذا بعد ذلك؟

يمكن تثبيت SharePoint Server 2013 و SharePoint Foundation 2013 محليا على خوادمك الخاصة. أو يمكنك استخدام SharePoint Online، وهي خدمة عبر الإنترنت تشكل جزءا من Microsoft 365. يمكنك اختيار:

- ترحيل إلى SharePoint Online.

- ترقية SharePoint Server أو SharePoint Foundation محليا.

- قم بكليهما أعلاه.

- تنفيذ حل [مختلط SharePoint](/sharepoint/hybrid/hybrid).

ضع في اعتبارك التكاليف المخفية للحفاظ على مزرعة خوادم، بما في ذلك صيانة التخصيصات أو ترحيلها وترقية الأجهزة. إذا قمت بحساب هذه العوامل، فسيكون من الأسهل الترقية المحلية. إذا قمت بتشغيل المزرعة على خوادم SharePoint قديمة دون تخصيص كبير، يمكنك الاستفادة من الترحيل المخطط له إلى SharePoint Online. بالنسبة إلى بيئة SharePoint Server المحلية، يمكنك أيضا التفكير في نقل بعض البيانات في SharePoint Online لتقليل النفقات العامة لإدارة الأجهزة.

> [!NOTE]
> يمكن لمسؤولي SharePoint إنشاء اشتراك Microsoft 365 وإعداد مواقع SharePoint Online جديدة، ثم القص بعيدا عن SharePoint Server 2010 بشكل نظيف، مع نقل المستندات الأساسية فقط إلى المواقع الجديدة. بعد ذلك، يمكن استنفاد أي بيانات متبقية من موقع SharePoint Server 2010 إلى أرشيفات محلية.

|SharePoint Online|SharePoint Server المحلي|
|---|---|
|تكلفة عالية في الوقت (الخطة/التنفيذ/التحقق)|تكلفة عالية في الوقت (الخطة/التنفيذ/التحقق)|
|انخفاض التكلفة في الأموال (بدون شراء الأجهزة)|ارتفاع التكلفة في الأموال (مشتريات الأجهزة)|
|التكلفة لمرة واحدة في الترحيل|التكلفة المتكررة لمرة واحدة لكل ترحيل مستقبلي|
|انخفاض التكلفة الإجمالية للملكية/الصيانة|التكلفة الإجمالية العالية للتملك/الصيانة|

سيكون للانتقال لمرة واحدة إلى Microsoft 365 تكلفة أعلى أثناء تنظيم البيانات وتحديد ما يجب اتخاذه إلى السحابة وما يجب تركه خلفك. ولكن بعد ترحيل بياناتك، ستكون الترقيات المستقبلية تلقائية، حيث لن تحتاج بعد الآن إلى إدارة تحديثات الأجهزة والبرامج. وسيتم دعم وقت إعداد المزرعة بواسطة [اتفاقية مستوى خدمة Microsoft (SLA).](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)

### <a name="migrate-to-sharepoint-online"></a>الترحيل إلى SharePoint Online

تأكد من أن SharePoint Online يوفر جميع الميزات التي تحتاج إليها. راجع [وصف الخدمة SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

لا يمكنك الترحيل مباشرة من SharePoint Server 2010 (أو SharePoint Foundation 2010) إلى SharePoint Online. الكثير من عمل الترحيل يدوي. ولكن هذه المرحلة تمنحك الفرصة لتقليم البيانات والمواقع التي لم تعد هناك حاجة إليها قبل النقل. يمكنك أرشفة بيانات أخرى في التخزين. 

تذكر أن SharePoint Server 2010 و SharePoint Foundation 2010 لن يتوقفا عن العمل في نهاية الدعم. لذلك يمكن أن يكون لدى المسؤولين فترة لا يزال فيها SharePoint قيد التشغيل إذا نسي عملاؤهم نقل بعض بياناتهم.

إذا قمت بالترقية إلى SharePoint Server 2013 أو SharePoint Server 2016 وقررت وضع البيانات في SharePoint Online، فقد تستخدم [واجهة برمجة تطبيقات الترحيل SharePoint](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) لترحيل المعلومات إلى OneDrive for Business.

|ميزة SharePoint Online|عيب SharePoint Online|
|---|---|
|توفر Microsoft أجهزة SPO وجميع إدارة الأجهزة.|قد تختلف الميزات المتوفرة بين SharePoint Server المحلي وSPO.|
|أنت المسؤول SharePoint أو المسؤول العام لاشتراكك ويمكنك تعيين المسؤولين إلى مواقع SPO.|بعض الإجراءات المتوفرة لمسؤول مزرعة في SharePoint Server المحلي غير موجودة (أو ليست ضرورية) في دور مسؤول SharePoint في Microsoft 365. ولكن SharePoint الإدارة وإدارة مجموعة المواقع المشتركة وملكية الموقع محلية لمؤسستك.|
|تطبق Microsoft التصحيحات والإصلاحات والتحديثات على الأجهزة والبرامج الأساسية، بما في ذلك خوادم SQL التي يتم تشغيل SharePoint Online عليها.|نظرا لعدم وجود وصول إلى نظام الملفات الأساسي في الخدمة، فإن التخصيص محدود.|
|تنشر Microsoft [اتفاقيات مستوى الخدمة](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) وتتحرك بسرعة لحل الحوادث على مستوى الخدمة.|يتم أتمتة النسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى بواسطة الخدمة في SharePoint Online. تتم الكتابة فوق النسخ الاحتياطية إذا لم يتم استخدامها.|
|يتم إجراء اختبار الأمان وضبط أداء الخادم بشكل مستمر في الخدمة من قبل Microsoft.|يتم تثبيت التغييرات على واجهة المستخدم وميزات SharePoint الأخرى بواسطة الخدمة وقد تحتاج إلى تشغيلها أو إيقاف تشغيلها.|
|Microsoft 365 تفي بالعديد من معايير الصناعة: [عروض الامتثال من Microsoft](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) المساعدة في الترحيل محدودة.  <br/> سيكون جزء كبير من الترقية يدويا أو عبر واجهة برمجة تطبيقات ترحيل SPO الموضحة في [SharePoint Online وخريطة طريق محتوى ترحيل OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|ليس لدى مهندسي دعم Microsoft وموظفي مركز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك.|يمكن أن تكون هناك تكاليف إضافية إذا كانت البنية الأساسية للأجهزة تحتاج إلى ترقية لدعم الإصدار الأحدث من SharePoint أو إذا كانت هناك حاجة إلى مزرعة ثانوية للترقية.|
|يمكن لموفري الحلول المساعدة في مهمة ترحيل البيانات لمرة واحدة إلى SharePoint Online.|لا تكون كل التغييرات التي تم إجراؤها على SharePoint Online ضمن عنصر التحكم الخاص بك. بعد الترحيل، قد تؤثر اختلافات التصميم في القوائم والمكتبات والميزات الأخرى بشكل مؤقت على إمكانية الاستخدام.|
|يتم تحديث المنتجات عبر الإنترنت تلقائيا عبر الخدمة. قد يتم إهمال الميزات، ولكن لا توجد نهاية حقيقية لدورة حياة الدعم.|هناك دورة حياة نهاية الدعم لخادم SharePoint أو SharePoint Foundation بالإضافة إلى خوادم SQL الأساسية.|

إذا قررت إنشاء موقع Microsoft 365 جديد وستقوم بترحيل البيانات إليه يدويا حسب الحاجة، فتحقق من [خيارات Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint Server المحلي

اعتبارا من SharePoint Server 2019، يجب أن يتم إجراء الترقيات *بشكل تسلسلي*. لا توجد طريقة للترقية من SharePoint Server 2010 إلى SharePoint Server 2016 أو إلى SharePoint 2019 مباشرة. مسار الترقية التسلسلي:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

سيستغرق الأمر وقتا والتخطيط لاتباع المسار بأكمله من SharePoint 2010 إلى SharePoint Server 2016. تتضمن الترقيات تكاليف الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج والإدارة. وقد تحتاج أيضا إلى ترقية التخصيصات أو حتى التخلي عنها. تأكد من توثيق التخصيصات الهامة قبل ترقية مزرعة SharePoint Server.

> [!NOTE]
> من الممكن الحفاظ على نهاية الدعم SharePoint مزرعة 2010، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث تعمل المزارع المنفصلة جنبا إلى جنب)، ثم تخطيط وتنفيذ ترحيل يدوي للمحتوى (لتنزيل المحتوى وإعادة تحميله، على سبيل المثال). ولكن هناك مخاطر محتملة لهذه الحركات اليدوية، مثل المستندات الواردة من عام 2010 والتي تحتوي على حساب حالي تم تعديله أخيرا باسم مستعار للحساب الذي يقوم بالنقل اليدوي. ويجب القيام ببعض العمل مسبقا، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنيات القوائم. تأكد من تنظيف البيئة قبل الترقية. ضع في اعتبارك البيانات التي يمكنك نقلها إلى التخزين أو لم تعد بحاجة إليها. وهذا يمكن أن يقلل من تأثير الترحيل. تأكد من أن المزرعة الحالية تعمل قبل الترقية، و(بالتأكيد) قبل إيقاف تشغيلها!

تذكر مراجعة *مسارات الترقية المعتمدة وغير المعتمدة*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

إذا كان لديك *تخصيصات*، فمن المهم أن تخطط لكل خطوة في مسار الترحيل:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|ميزة محلية|عيب محلي|
|---|---|
|التحكم الكامل في جميع جوانب مزرعة SharePoint (SQL الخاصة بها)، من أجهزة الخادم.|جميع الفواصل والإصلاحات هي مسؤولية شركتك. ولكن يمكنك المشاركة في دعم Microsoft المدفوع إذا لم يكن منتجك قد تجاوز نهاية الدعم.|
|مجموعة ميزات كاملة من SharePoint Server المحلي مع خيار توصيل المزرعة المحلية باشتراك SharePoint Online عبر مختلط.|تتم إدارة الترقية والتصحيحات وتصحيحات الأمان وترقيات الأجهزة وجميع صيانة SharePoint Server ومزرعة SQL الخاصة به محليا.|
|الوصول الكامل لخيارات تخصيص أكبر من SharePoint Online.|يجب تكوين [عروض التوافق من Microsoft](/compliance/regulatory/offering-home) يدويا محليا.|
|يتم إجراء اختبار الأمان وضبط أداء الخادم في أماكن عملك تحت سيطرتك.|قد توفر Microsoft 365 ميزات SharePoint Online التي لا تعمل بشكل تفاعلي مع SharePoint Server المحلي.|
|يمكن لموفري الحلول المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).|لن تستخدم مواقع SharePoint Server شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو موضح في SharePoint Online.|
|التحكم الكامل في اصطلاحات التسمية والنسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى في SharePoint Server المحلي.|SharePoint الخادم المحلي حساس لدورات حياة المنتج.|

### <a name="upgrade-resources"></a>ترقية الموارد

ابدأ بمقارنة متطلبات الأجهزة والبرامج. إذا كانت بيئتك الحالية لا تفي بالمتطلبات الأساسية، فقد تحتاج إلى ترقية الأجهزة في المزرعة أو خوادم SQL أولا. 

قد تقرر نقل بعض مواقعك إلى الأجهزة "دائمة الخضرة" SharePoint Online. بمجرد إجراء التقييم الخاص بك، اتبع مسارات وأساليب الترقية المدعومة.

- *متطلبات الأجهزة/البرامج من أجل:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *حدود البرامج وحدودها ل:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)

- *نظرة عامة على عملية الترقية من أجل:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>إنشاء حل مختلط باستخدام SharePoint Online وخادم SharePoint المحلي

يوفر الإعداد المختلط أفضل ما في الموقع المحلي وعلى الإنترنت لبعض احتياجات الترحيل. يمكنك توصيل مزارع SharePoint Server 2013 أو 2016 أو 2019 SharePoint Online لإنشاء SharePoint مختلط: [تعرف على الحلول المختلطة SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx).

إذا كانت مزرعة SharePoint Server المختلطة هي هدف الترحيل الخاص بك، فقم بتحديد المواقع والمستخدمين الذين يجب نقلهم عبر الإنترنت وأيهم بحاجة إلى البقاء محليا. يمكن أن يساعد تصنيف محتوى مزرعة SharePoint Server على أنه تأثير كبير أو متوسط أو منخفض على شركتك في اتخاذ هذا القرار. قد تحتاج فقط إلى مشاركة حسابات المستخدمين لتسجيل الدخول وفهرس البحث SharePoint Server مع SharePoint Online. ولكن قد لا يكون هذا العامل واضحا حتى تنظر إلى كيفية استخدام مواقعك. إذا قررت شركتك لاحقا ترحيل المحتوى بالكامل إلى SharePoint Online، فيمكنك نقل جميع الحسابات والبيانات المتبقية عبر الإنترنت وإخراج المزرعة المحلية من الخدمة. سيتم إدارة/إدارة مزرعة SharePoint من خلال وحدات التحكم Microsoft 365 من تلك النقطة فصاعدا.

تأكد من التعرف على الأنواع الحالية من المجموعات المختلطة وكيفية تكوين الاتصال بين مزرعة SharePoint المحلية واشتراكك في Microsoft 365.

|الخيار|الوصف|
|---|---|
|[عروض التوافق مع Microsoft](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) المساعدة في الترحيل محدودة.<br/><br/> سيكون جزء كبير من الترقية يدويا أو عبر واجهة برمجة تطبيقات ترحيل SPO الموضحة في [SharePoint Online وخريطة طريق محتوى ترحيل OneDrive](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|ليس لدى مهندسي دعم Microsoft وموظفي مركز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك.|قد تكون هناك تكاليف إضافية إذا كانت البنية الأساسية للأجهزة تحتاج إلى ترقية لدعم الإصدار الأحدث من SharePoint، أو إذا كانت هناك حاجة إلى مزرعة ثانوية.|
|يمكن للشركاء المساعدة في مهمة ترحيل البيانات لمرة واحدة إلى SharePoint Online.||
|يتم تحديث المنتجات عبر الإنترنت تلقائيا عبر الخدمة. قد يتم إهمال الميزات، ولكن لا توجد نهاية حقيقية للدعم.||

إذا قررت إنشاء موقع Microsoft 365 جديد وترحيل البيانات إليه يدويا حسب الحاجة، فتحقق من [خيارات Microsoft 365](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint Server المحلي

لا توجد طريقة لتخطي الإصدارات في SharePoint الترقيات. وهذا يعني أن الترقيات تنتقل بشكل تسلسلي:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

لاتخاذ المسار بأكمله من SharePoint 2007 إلى SharePoint Server 2016 سيعني استثمارا كبيرا في الوقت وسيشمل الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج وتكاليف الإدارة. يجب ترقية التخصيصات أو التخلي عنها، وفقا لأهمية الميزة.

> [!NOTE]
> من الممكن الحفاظ على نهاية العمر الافتراضي SharePoint مزرعة 2007، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث تعمل المزارع المنفصلة جنبا إلى جنب)، ثم تخطيط وتنفيذ ترحيل يدوي للمحتوى (لتنزيل المحتوى وإعادة تحميله، على سبيل المثال). ولكن هناك بعض العيوب لهذه الحركات اليدوية، مثل عمليات نقل المستندات التي تستبدل آخر حساب تم تعديله بالاسم المستعار للحساب الذي يقوم بالنقل اليدوي. ويجب القيام بالكثير من العمل قبل الوقت المحدد، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنيات القوائم. على أي حال، ضع في اعتبارك البيانات التي يمكنك نقلها إلى التخزين أو لم تعد بحاجة إلى تقليل تأثير الترحيل.

تأكد من تنظيف البيئة قبل الترقية. تأكد من أن المزرعة الحالية تعمل قبل الترقية، و بالتأكيد قبل إيقاف تشغيلها!

تذكر مراجعة *مسارات الترقية المعتمدة وغير المعتمدة*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

إذا كان لديك *تخصيصات*، فمن الضروري التخطيط للترقية لكل خطوة في مسار الترحيل:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|محترف محلي|con المحلي|
|---|---|
|التحكم الكامل في جميع جوانب SharePoint Farm، من أجهزة الخادم.|جميع الفواصل والإصلاحات هي مسؤولية شركتك. (ولكن يمكنك المشاركة في دعم Microsoft المدفوع إذا لم يكن منتجك قد تجاوز نهاية الدعم.)|
|مجموعة ميزات كاملة من SharePoint Server المحلي مع خيار توصيل المزرعة المحلية باشتراك SharePoint Online عبر مختلط.|الترقية والتصحيحات وتصحيحات الأمان وجميع صيانة SharePoint Server المدارة محليا.|
|الوصول الكامل لمزيد من التخصيص.|يجب تكوين [عروض التوافق من Microsoft](/compliance/regulatory/offering-home) يدويا محليا.|
|يتم إجراء اختبار الأمان وضبط أداء الخادم في أماكن عملك تحت سيطرتك.|قد توفر Microsoft 365 ميزات SharePoint Online التي لا تعمل بشكل تفاعلي مع SharePoint Server المحلي.|
|يمكن للشركاء المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).|لن تستخدم مواقع SharePoint Server شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو موضح في SharePoint Online.|
|التحكم الكامل في اصطلاحات التسمية والنسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى في SharePoint Server المحلي.|SharePoint الخادم المحلي حساس لدورات حياة المنتج.|

### <a name="upgrade-resources"></a>ترقية الموارد

ابدأ بمعرفة أنك تلبي متطلبات الأجهزة والبرامج، ثم اتبع أساليب الترقية المدعومة.

- *متطلبات الأجهزة/البرامج من أجل*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/sharepoint/install/hardware-software-requirements-2013) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *حدود البرامج وحدودها ل*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/sharepoint/install/software-boundaries-limits-2019)

- *نظرة عامة على عملية الترقية من أجل*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>إنشاء حل مختلط SharePoint بين SharePoint Online وin-premises

إذا كانت الإجابة على احتياجات الترحيل الخاصة بك في مكان ما بين عنصر التحكم الذي يقدمه الموقع وانخفاض تكلفة الملكية التي يقدمها SharePoint Online، يمكنك توصيل SharePoint Server 2013 أو 2016 بالمزارع SharePoint Online من خلال المختلطة. [تعرف على الحلول المختلطة SharePoint](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

إذا قررت أن مزرعة خوادم SharePoint المختلطة ستستفيد من عملك، فتعرف على الأنواع المختلطة الموجودة وكيفية تكوين الاتصال بين مزرعة SharePoint المحلية واشتراكك في Microsoft 365.

قد تحتاج إلى إنشاء بيئة تطوير/اختبار Microsoft 365، والتي يمكنك إعدادها باستخدام [Test Lab Guides](m365-enterprise-test-lab-guides.md). بعد الحصول على اشتراك تجريبي أو شراء Microsoft 365، يمكنك إنشاء مجموعات المواقع المشتركة والشبكات ومكتبات المستندات في SharePoint Online التي يمكنك ترحيل البيانات إليها. يمكنك الترحيل يدويا، باستخدام واجهة برمجة تطبيقات الترحيل، أو، إذا كنت تريد ترحيل محتوى "الموقع الخاص بي" إلى OneDrive for Business، من خلال المعالج المختلط.

> [!NOTE]
> لاستخدام الخيار المختلط، يجب أولا ترقية مزرعة SharePoint Server 2010 محليا إلى SharePoint Server 2013 أو 2016. لا يدعم SharePoint Foundation 2010 و SharePoint Foundation 2013 الاتصالات المختلطة مع SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>ملخص خيارات عميل Office 2010 وخوادمه Windows 7

للحصول على ملخص مرئي لخيارات الترقية والترحيل والانتقال إلى السحابة لعملاء وخوادم Office 2010 Windows 7، راجع [نهاية ملصق الدعم](../downloads/Office2010Windows7EndOfSupport.pdf).

[![نهاية دعم عملاء وخوادم Office 2010 وملصق Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

يوضح هذا الملصق المسارات المختلفة التي يمكنك اتباعها لتجنب Office منتجات العميل والخادم في عام 2010 Windows نهاية الدعم، مع تمييز المسارات المفضلة ودعم الخيارات في Microsoft 365 Enterprise.

يمكنك أيضا [تنزيل](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) هذا الملصق وطباعته بتنسيق حرفي أو قانوني أو جدولي (11 × 17).

## <a name="related-articles"></a>المقالات ذات الصلة

[موارد لمساعدتك على الترقية من خوادم وعملاء Office 2007 أو 2010](upgrade-from-office-2010-servers-and-products.md)

[نظرة عامة على عملية الترقية من SharePoint 2010 إلى SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[أفضل الممارسات للترقية من SharePoint 2010 إلى SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[استكشاف مشاكل ترقية قاعدة البيانات وإصلاحها في SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[البحث عن موفري حلول Microsoft للمساعدة في الترقية](https://go.microsoft.com/fwlink/?linkid=841249)

[نهج خدمة المنتج المحدث SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[نهج خدمة المنتج المحدث لخادم SharePoint 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
