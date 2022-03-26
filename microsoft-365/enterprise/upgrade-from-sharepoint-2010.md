---
title: الترقية من SharePoint 2010
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
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
description: ابحث عن المعلومات والموارد للترقية من SharePoint 2010 SharePoint Server 2010. دعم كلا الطرفين في 13 أبريل 2021.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7ce6b333e39d02000514c174579a1ad0fa816771
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575274"
---
# <a name="upgrading-from-sharepoint-2010"></a>الترقية من SharePoint 2010

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

سيصل SharePoint Microsoft 2010 SharePoint Server 2010 إلى نهاية الدعم في **13 أبريل 2021**. توفر هذه المقالة موارد لمساعدتك على ترحيل بيانات SharePoint Server 2010 الموجودة إلى SharePoint Online في Microsoft 365 أو ترقية بيئة SharePoint Server 2010 المحلية.

## <a name="what-is-end-of-support"></a>ما هو *انتهاء الدعم*؟

تحتوي معظم منتجات Microsoft على دورة حياة الدعم، حيث تحصل خلالها على ميزات جديدة وت تصحيحات الأخطاء وإصلاحات الأمان وما إلى ذلك. بعد انتهاء تاريخ الدعم، لا يتوقف المنتج عن العمل، ولكن لم تعد Microsoft توفر:

- الدعم التقني للمشاكل التي قد تحدث.

- إصلاحات الأخطاء ل المشاكل التي قد تؤثر على استقرار الخادم وإمكانية استخدامه.

- إصلاحات الأمان لنقاط الضعف التي قد تجعل الخادم عرضة للثغرات الأمنية.

- تحديثات المنطقة الزمنية.

وهذا يعني أنه لن يتم إجراء أي تحديثات أو تصحيحات أو إصلاحات للمنتج (بما في ذلك تصحيحات/إصلاحات الأمان). سيبدل دعم Microsoft جهود الدعم بشكل كامل إلى الإصدارات الأحدث.

مع اقتراب نهاية دعم SharePoint Server 2010، احذف البيانات التي لم تعد بحاجة إليها قبل ترقية المنتج وترحيل بياناتك المهمة.

> [!NOTE]
> تدوم دورة حياة البرنامج عادة لمدة عشر سنوات من الإصدار الأولي. [يمكن لموفري حلول Microsoft](https://go.microsoft.com/fwlink/?linkid=841249) مساعدتك على الترقية إلى الإصدار التالي من البرنامج أو الترحيل Microsoft 365 الترحيل (أو كليهما). تأكد من أنك على دراية بمواعيد انتهاء الدعم للتقنيات الأساسية الهامة أيضا، خاصة بالنسبة إلى إصدار Microsoft SQL Server الذي تستخدمه مع SharePoint. لمزيد من المعلومات، راجع [نهج دورة الحياة الثابتة](https://support.microsoft.com/help/14085).

## <a name="plan-ahead"></a>التخطيط للمستقبل

تحقق من التواريخ التي ينتهي دعمها على موقع [دورة حياة المنتج](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010). خطط للترقية أو الترحيل مع وضع هذه التواريخ في الاعتبار. تذكر أن *منتجك لن يتوقف عن العمل* في التاريخ المدرج. ولكن بما أنه لن يتم تصحيح التثبيت بعد ذلك التاريخ، فسوف تحتاج إلى التخطيط لانتقال سلس إلى الإصدار التالي من المنتج.

تساعد هذه المصفوفة على رسم دورة تدريبية بين خيارات الترحيل:

|منتج انتهاء الدعم|جيد |الأفضل|
|---|---|---|
|SharePoint Server 2010|SharePoint Server 2013 (المحلي)|SharePoint Online|
||SharePoint Hybrid Server 2013 مع SharePoint Online|SharePoint Server 2016 (المحلي)|
|||SharePoint البحث المختلط في السحابة|

إذا اخترت خيارا في الطرف المنخفض من المقياس (جيد)، ستحتاج إلى بدء التخطيط لترقية أخرى بعد عملية الترحيل مباشرة من SharePoint Server 2010.

فيما يلي المسارات الثلاثة التي يمكنك اتخاذها لتجنب انتهاء دعم SharePoint Server 2010.

![SharePoint مسارات ترقية Server 2010.](../media/upgrade-from-sharepoint-2010/upgrade-from-sharepoint-2010-paths.png)

> [!NOTE]
> انتهاء دعم SharePoint Server 2010 SharePoint Foundation 2010 مجدول حاليا في 13 أبريل 2021. ولكن تأكد من التحقق من موقع [دورة حياة المنتج](https://support.microsoft.com/lifecycle) للحصول على التواريخ الأكثر اتساما بالمواعيد الحالية.

## <a name="whats-next"></a>ماذا بعد ذلك؟

SharePoint Server 2013 SharePoint Foundation 2013 على الخوادم الخاصة بك. أو يمكنك استخدام SharePoint Online، وهي خدمة عبر الإنترنت تكون جزءا من Microsoft 365. يمكنك اختيار:

- الترحيل إلى SharePoint Online.

- ترقية SharePoint Server أو SharePoint Foundation في الموقع.

- القيام بكلا الأمرين أعلاه.

- تنفيذ حل [SharePoint المختلط](/sharepoint/hybrid/hybrid).

فكر في التكاليف المخفية للحفاظ على مزرعة خوادم، بما في ذلك صيانة التخصيصات أو اخفاؤها وترقية الأجهزة. إذا قمت ب حساب هذه العوامل، سيكون من الأسهل الترقية في الموقع. إذا قمت بتشغيل المزرعة على خوادم SharePoint دون تخصيص كثيف، يمكنك الاستفادة من الترحيل المخطط له إلى SharePoint Online. للحصول على بيئة خادم SharePoint، يمكنك أيضا نقل بعض البيانات في SharePoint عبر الإنترنت لتقليل النفقات العامة لإدارة الأجهزة.

> [!NOTE]
> SharePoint المسؤولين عن إنشاء اشتراك Microsoft 365، إعداد مواقع SharePoint عبر الإنترنت جديدة، ثم قطعها عن SharePoint Server 2010 بشكل نظيف، مع أخذ المستندات الضرورية فقط إلى المواقع الجديدة. بعد ذلك، يمكن استنزاف أي بيانات متبقة من موقع SharePoint Server 2010 إلى أرشيفات موقعية.

|SharePoint Online|SharePoint الخادم في الموقع|
|---|---|
|تكلفة عالية في الوقت (الخطة/التنفيذ/التحقق)|تكلفة عالية في الوقت (الخطة/التنفيذ/التحقق)|
|تكلفة أقل في عمليات التمويل (بدون شراء أجهزة)|تكلفة أعلى في عمليات التمويل (مشتريات الأجهزة)|
|التكلفة مرة واحدة في عملية الترحيل|التكلفة المتكررة مرة واحدة لكل عملية ترحيل مستقبلية|
|التكلفة الإجمالية المنخفضة للملكية/الصيانة|التكلفة الإجمالية العالية للملكية/الصيانة|

سيكلف الانتقال مرة واحدة إلى Microsoft 365 تكلفة أعلى أثناء تنظيم البيانات وتقرر ما يجب أخذه إلى السحابة وما يجب تركه خلفك. ولكن بعد ترحيل بياناتك، ستكون الترقيات المستقبلية تلقائية، حيث لن تحتاج بعد ذلك إلى إدارة تحديثات الأجهزة والبرامج. كما سيتم دعم وقت العمل في المزرعة باتفاقية مستوى خدمة [Microsoft (SLA).](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement)

### <a name="migrate-to-sharepoint-online"></a>الترحيل إلى SharePoint Online

تأكد من SharePoint Online كل الميزات التي تحتاج إليها. راجع [SharePoint وصف الخدمة](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description).

لا يمكنك الترحيل مباشرة من SharePoint Server 2010 (أو SharePoint Foundation 2010) إلى SharePoint Online. الكثير من عمل الترحيل يدوي. ولكن هذه المرحلة تمنحك فرصة لتقليم البيانات والمواقع التي لم تعد مطلوبة قبل الانتقال. يمكنك أرشفة بيانات أخرى في مساحة تخزين. 

تذكر أن SharePoint Server 2010 SharePoint Foundation 2010 لن يتوقفا عن العمل في نهاية الدعم. لذا يمكن للمسؤولين الحصول على فترة زمنية SharePoint تشغيلها إذا نسي عملاؤهم نقل بعض بياناتهم.

إذا قمت بالترقية إلى SharePoint Server 2013 أو SharePoint Server 2016 وقررت وضع البيانات في SharePoint Online، يمكنك استخدام [API ترحيل SharePoint](https://support.office.com/article/Upload-on-premises-content-to-SharePoint-Online-using-PowerShell-cmdlets-555049c6-15ef-45a6-9a1f-a1ef673b867c?ui=en-US&amp;rs=en-US&amp;ad=US) لترحيل المعلومات إلى OneDrive for Business.

|SharePoint عبر الإنترنت|SharePoint الضار عبر الإنترنت|
|---|---|
|توفر Microsoft أجهزة SPO وإدارة جميع الأجهزة.|قد تختلف الميزات المتوفرة بين SharePoint Server في الموقع وSPO.|
|أنت مسؤول Sharepoint أو المسؤول العام لاشتراكك، ويمكنك تعيين المسؤولين إلى مواقع SPO.|بعض الإجراءات المتوفرة لمسؤول المزرعة في SharePoint الخادم المحلي غير موجودة (أو ليست ضرورية) في دور مسؤول SharePoint في Microsoft 365. ولكن SharePoint إدارة المواقع المشتركة وإدارة مجموعة المواقع المشتركة وملكية الموقع محليا لمجموعتك.|
|تطبق Microsoft التصحيحات والتصحيحات والتحديثات على الأجهزة والبرامج الأساسية، بما في ذلك SQL التي يتم تشغيل SharePoint Online عليها.|نظرا لعدم إمكانية الوصول إلى نظام الملفات الأساسي في الخدمة، يكون التخصيص محدودا.|
|تنشر Microsoft [اتفاقيات مستوى الخدمة](/office365/servicedescriptions/office-365-platform-service-description/service-level-agreement) وتتحرك بسرعة لحل أحداث مستوى الخدمة.|يتم إجراء النسخ الاحتياطي والاستعادة وخيارات الاسترداد الأخرى بشكل تلقائي بواسطة الخدمة في SharePoint Online. يتم الكتابة فوق النسخ الاحتياطية إذا لم يتم استخدامها.|
|يتم تنفيذ اختبار الأمان وضبط أداء الخادم بشكل مستمر في الخدمة بواسطة Microsoft.|يتم تثبيت التغييرات التي يتم إدخالها على واجهة المستخدم SharePoint الأخرى بواسطة الخدمة وقد تحتاج إلى تشغيلها أو إيقاف تشغيلها.|
|Microsoft 365 العديد من معايير الصناعة: عروض [التوافق من Microsoft](/compliance/regulatory/offering-home).|[FastTrack](https://go.microsoft.com/fwlink/?linkid=518597) المساعدة المقدمة ل الترحيل محدودة.  <br/> سيكون جزء كبير من الترقية يدويا أو عبر API هجرة SPO الموضحة في SharePoint [عبر الإنترنت OneDrive لمحتوى الترحيل](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|لا تتوفر لمهندسي دعم Microsoft وموظفي مراكز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك.|قد تكون هناك تكاليف إضافية إذا كان من اللازم ترقية البنية الأساسية للأجهزة لدعم الإصدار الأحدث من SharePoint أو إذا كانت المزرعة الثانوية مطلوبة للترقية.|
|يمكن لموفري الحلول المساعدة في المهمة التي يتم القيام بها مرة واحدة تهجر البيانات إلى SharePoint عبر الإنترنت.|لا توجد كل التغييرات SharePoint Online ضمن عنصر التحكم الخاص بك. بعد الترحيل، قد تؤثر اختلافات التصميم في القوائم والمكتبات والميزات الأخرى على إمكانية الاستخدام بشكل مؤقت.|
|يتم تحديث المنتجات عبر الإنترنت تلقائيا عبر الخدمة. قد يتم إهمال الميزات، ولكن لا يوجد نهاية حقيقية لنهاية دورة حياة الدعم.|هناك دورة حياة نهاية الدعم للخادم SharePoint أو SharePoint الأساس بالإضافة إلى SQL الأساسية.|

إذا قررت إنشاء موقع Microsoft 365 جديد وست ترحيل البيانات إليه يدويا كما هو مطلوب، فتحقق من Microsoft 365 [البيانات](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint الخادم في الموقع

في SharePoint Server 2019، يجب أن يتم إجراء الترقيات *بشكل تسلسلي*. لا توجد طريقة للترقية من SharePoint Server 2010 إلى SharePoint Server 2016 أو SharePoint 2019 مباشرة. مسار الترقية التسلسلية:

- SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

سيستغرق الأمر بعض الوقت والتخطيط لاتباع المسار بالكامل من SharePoint 2010 إلى SharePoint Server 2016. تتضمن الترقيات تكاليف الأجهزة (SQL يجب أيضا ترقية الخوادم والبرامج والإدارة. وقد تحتاج أيضا إلى ترقية التخصيصات أو حتى التخلي عنها. تأكد من توثيق التخصيصات الهامة قبل ترقية SharePoint Server.

> [!NOTE]
> من الممكن الاحتفاظ بمزرعة نهاية الدعم في SharePoint 2010، وتثبيت مزرعة خادم SharePoint 2016 على أجهزة جديدة (بحيث يتم تشغيل المزرعة المنفصلة جنبا إلى جنب)، ثم تخطيط عملية ترحيل المحتوى يدويا وتنفيذها (لتنزيل المحتوى أو إعادة تحميله، على سبيل المثال). ولكن هناك بعض المخاطر المحتملة لهذه الحركات اليدوية، مثل المستندات القادمة من 2010 التي لديها حساب تم تعديله الأخير الحالي مع الاسم المستعار للحساب الذي يقوم بالنقل اليدوي. ويجب إنجاز بعض العمل قبل الوقت المحدد، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنيات القائمة. تأكد من تنظيف بيئتك قبل الترقية. فكر في البيانات التي يمكنك نقلها إلى مساحة التخزين أو التي لم تعد بحاجة إليها. يمكن أن يقلل ذلك من تأثير الترحيل. كن على يقين من أن المزرعة الموجودة تعمل قبل الترقية، و(بالتأكيد) قبل أن تسحب الخدمة!

تذكر مراجعة مسارات الترقية المعتمدة *وغير المعتمدة*:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

إذا كانت *لديك تخصيصات*، فمن المهم التخطيط لكل خطوة في مسار الترحيل:

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|الميزة في الموقع|العيب في الموقع|
|---|---|
|التحكم الكامل في جميع جوانب SharePoint المزرعة (SQL الخاصة بها)، من جهاز الخادم لأعلى.|تقع على عاتق شركتك مسؤولية كل الاستراحة والتثواب. ولكن يمكنك المشاركة في دعم Microsoft المدفوع إذا لم ينهي منتجك الدعم بعد.|
|مجموعة الميزات الكاملة من SharePoint الخادم في الموقع مع خيار توصيل المزرعة الخاصة بك في موقع SharePoint عبر الإنترنت عبر المختلط.|تتم إدارة الترقية والتصحيحات وإصلاحات الأمان وترقيات الأجهزة والصيانة SharePoint الخادم ومزرعته SQL المحلية.|
|الوصول الكامل للحصول على خيارات تخصيص أكبر من تلك المتوفرة مع SharePoint Online.|[يجب تكوين عروض](/compliance/regulatory/offering-home) التوافق من Microsoft يدويا في الموقع.|
|يتم إجراء اختبار الأمان وضبط أداء الخادم في مكانك تحت سيطرتك.|Microsoft 365 الميزات المتوفرة SharePoint Online التي لا يتم تشغيلها مع SharePoint الخادم في الموقع.|
|يمكن لموفري الحلول المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).|لن تستخدم SharePoint الخادم شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو مشاهد في SharePoint Online.|
|التحكم الكامل في اصطلاحات التسمية ونسخها احتياطيا واستعادتها وخيارات الاسترداد الأخرى في SharePoint الخادم في الموقع.|SharePoint إلى أن الخادم المحلي يتحسس دورة حياة المنتج.|

### <a name="upgrade-resources"></a>موارد الترقية

ابدأ بمقارنة متطلبات الأجهزة والبرامج. إذا لم تلبي بيئتك الحالية المتطلبات الأساسية، فقد تحتاج إلى ترقية الأجهزة في المزرعة أو SQL الخوادم أولا. 

قد تقرر نقل بعض مواقعك إلى الأجهزة "دائمة الخضرة" في SharePoint Online. بعد إجراء التقييم، اتبع مسارات وأساليب الترقية المعتمدة.

- *متطلبات الأجهزة/البرامج ل:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *حدود البرنامج وحدوده ل:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *نظرة عامة حول عملية الترقية ل:*

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-hybrid-solution-with-sharepoint-online-and-sharepoint-server-on-premises"></a>إنشاء حل مختلط باستخدام SharePoint Online SharePoint Server في الموقع

يوفر الإعداد المختلط أفضل ما في كل من المحلية أو عبر الإنترنت لبعض احتياجات الترحيل. يمكنك توصيل SharePoint Server 2013 أو 2016 أو 2019 ب SharePoint Online لإنشاء SharePoint مختلط[: تعرف](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx) على SharePoint المختلطة.

إذا كانت مزرعة SharePoint Server هي هدف الترحيل، فاحسب المواقع والمستخدمين الذين يجب التنقل عبر الإنترنت والمواقع التي يجب أن تبقى في الموقع. يمكن أن SharePoint على محتوى مزرعة الخادم كتأثر عال أو متوسط أو منخفض على شركتك في اتخاذ هذا القرار. قد تحتاج فقط إلى مشاركة حسابات المستخدمين لتسجيل الدخول وفهرس البحث SharePoint Server مع SharePoint Online. ولكن قد لا يكون هذا العامل واضحا حتى تنظر إلى كيفية استخدام مواقعك. إذا قررت شركتك لاحقا ترحيل كل المحتوى إلى SharePoint Online، يمكنك نقل كل الحسابات والبيانات المتبقية عبر الإنترنت وسحب المزرعة المحلي. سيتم إدارة/إدارة SharePoint من خلال Microsoft 365 التحكم من هذه النقطة.

تأكد من التعرف على أنواع المختلطات الموجودة وكيفية تكوين الاتصال بين المزرعة SharePoint والمزرعة Microsoft 365 الخاص بك.

|الخيار|الوصف|
|---|---|
|[عروض التوافق من Microsoft](/compliance/regulatory/offering-home).|[FastTrack](https://www.microsoft.com/fasttrack/microsoft-365) المساعدة المقدمة ل الترحيل محدودة.<br/><br/> سيكون جزء كبير من الترقية يدويا أو عبر API هجرة SPO الموضحة في SharePoint [عبر الإنترنت OneDrive لمحتوى الترحيل](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets).|
|لا تتوفر لمهندسي دعم Microsoft وموظفي مراكز البيانات حق وصول مسؤول غير مقيد إلى اشتراكك.|قد تكون هناك تكاليف إضافية إذا كان من اللازم ترقية البنية الأساسية للأجهزة لدعم الإصدار الأحدث من SharePoint، أو إذا كانت هناك حاجة إلى مزرعة ثانوية.|
|يمكن للشركاء المساعدة في المهمة التي يتم القيام بها مرة واحدة تهجر بياناتك إلى SharePoint عبر الإنترنت.||
|يتم تحديث المنتجات عبر الإنترنت تلقائيا عبر الخدمة. قد يتم إهمال الميزات، ولكن لا يوجد نهاية حقيقية للدعم.||

إذا قررت إنشاء موقع Microsoft 365 جديد وترحيل البيانات إليه يدويا كما هو مطلوب، فتحقق من Microsoft 365 [البيانات](https://www.microsoft.com/microsoft-365/).

### <a name="upgrade-sharepoint-server-on-premises"></a>ترقية SharePoint الخادم في الموقع

لا توجد طريقة لتخطي الإصدارات في SharePoint الترقيات. وهذا يعني أن الترقيات تتم بشكل تسلسلي:

- SharePoint 2007 \> SharePoint Server 2010 \> SharePoint Server 2013 \> SharePoint Server 2016

يعني المسار بأكمله من SharePoint 2007 إلى SharePoint Server 2016 استثمارا كبيرا في الوقت وسيتضمن الأجهزة (يجب أيضا ترقية خوادم SQL) والبرامج وتكاليف الإدارة. ستحتاج التخصيصات إلى ترقية أو التخلي عنها، وفقا لحرجية الميزة.

> [!NOTE]
> من الممكن الحفاظ على مزرعة SharePoint 2007 التي تنتهي حياتها، وتثبيت مزرعة SharePoint Server 2016 على أجهزة جديدة (بحيث يتم تشغيل المزرعة المنفصلة جنبا إلى جنب)، ثم تخطيط عملية ترحيل المحتوى يدويا وتنفيذها (لتنزيل المحتوى أو إعادة تحميله، على سبيل المثال). ولكن هناك بعض العيوب التي تعيب عمليات النقل اليدوية هذه، مثل نقل المستندات التي استبدلت آخر حساب تم تعديله باسم الحساب المستعار الذي يقوم بالتحريك اليدوي. ويجب إنجاز الكثير من العمل قبل الوقت المحدد، مثل إعادة إنشاء المواقع والمواقع الفرعية والأذونات وبنى القائمة. على أي حال، فكر في البيانات التي يمكنك نقلها إلى مساحة التخزين أو لم تعد بحاجة إلى تقليل تأثير الترحيل.

تأكد من تنظيف بيئتك قبل الترقية. كن على يقين من أن المزرعة الموجودة تعمل قبل الترقية، وقبل أن تسحبها بالتأكيد!

تذكر مراجعة مسارات الترقية المعتمدة *وغير المعتمدة*:

- [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262747(v=office.12))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/review-supported-editions-and-products-for-upgrading-to-sharepoint-2013)

إذا كانت *لديك تخصيصات*، فمن المهم التخطيط للترقية لكل خطوة في مسار الترحيل:

- [SharePoint 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263203(v=office.12))

- [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc263203(v=office.14))

- [SharePoint Server 2013](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013)

|محترف في الموقع|con في الموقع|
|---|---|
|التحكم الكامل بكل جوانب SharePoint المزرعة، من جهاز الخادم لأعلى.|تقع على عاتق شركتك مسؤولية كل الاستراحة والتثواب. (ولكن يمكنك المشاركة في دعم Microsoft مدفوع إذا لم ينهي منتجك بعد انتهاء الدعم.)|
|مجموعة الميزات الكاملة من SharePoint الخادم في الموقع مع خيار توصيل المزرعة الخاصة بك في موقع SharePoint عبر الإنترنت عبر المختلط.|الترقية والتصحيحات وإصلاحات الأمان والصيانة SharePoint الخادم المدارة في الموقع.|
|الوصول الكامل لمزيد من التخصيص.|[يجب تكوين عروض](/compliance/regulatory/offering-home) التوافق من Microsoft يدويا في الموقع.|
|يتم إجراء اختبار الأمان وضبط أداء الخادم في مكانك الداخلي تحت سيطرتك.|Microsoft 365 هذه الميزات متوفرة SharePoint Online التي لا يتم تشغيلها مع SharePoint الخادم في الموقع.|
|يمكن للشركاء المساعدة في ترحيل البيانات إلى الإصدار التالي من SharePoint Server (وما بعده).|لن تستخدم SharePoint الخادم شهادات [SSL/TLS](/SharePoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016) تلقائيا كما هو مشاهد في SharePoint Online.|
|التحكم الكامل في اصطلاحات التسمية ونسخها احتياطيا واستعادتها وخيارات الاسترداد الأخرى في SharePoint الخادم في الموقع.|SharePoint إلى أن الخادم المحلي يتحسس دورة حياة المنتج.|

### <a name="upgrade-resources"></a>موارد الترقية

ابدأ بمعرفة أنك تلبي متطلبات الأجهزة والبرامج، ثم اتبع أساليب الترقية المعتمدة.

- *متطلبات الأجهزة/البرامج ل*:

    [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262485(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/hardware-and-software-requirements-0) |  [SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)

- *حدود البرنامج وحدوده ل*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc262787(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc262787(v=office.14)) |  [SharePoint Server 2013](/SharePoint/install/software-boundaries-and-limits) |  [SharePoint Server 2016](/SharePoint/install/software-boundaries-and-limits-0)

- *نظرة عامة حول عملية الترقية ل*:

    [SharePoint Server 2007](/previous-versions/office/sharepoint-2007-products-and-technologies/cc303420(v=office.12)) |  [SharePoint Server 2010](/previous-versions/office/sharepoint-server-2010/cc303420(v=office.14)) |  [SharePoint Server 2013](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016) |  [SharePoint Server 2016](/SharePoint/upgrade-and-update/upgrade-to-sharepoint-server-2016)

### <a name="create-a-sharepoint-hybrid-solution-between-sharepoint-online-and-on-premises"></a>إنشاء حل SharePoint مختلط بين SharePoint Online وs premises

إذا كانت الإجابة على احتياجات الترحيل في مكان ما بين عنصر التحكم الذي يقدمه المحلي والتكلفة المنخفضة للملكية التي يقدمها SharePoint Online، يمكنك توصيل مزارع SharePoint Server 2013 أو 2016 ب SharePoint Online عبر المختلطات. [التعرف على SharePoint المختلطة](https://support.office.com/article/4c89a95a-a58c-4fc1-974a-389d4f195383.aspx)

إذا قررت أن مزرعة SharePoint Server المختلطة ستستفيد منها شركتك، فاطلع على الأنواع الموجودة من المختلطات وكيفية تكوين الاتصال بين مزرعة SharePoint SharePoint واشتراكك Microsoft 365.

قد ترغب في إنشاء بيئة Microsoft 365 اختبار/اختبار، يمكنك إعدادها باستخدام ["أدلة اختبار المعمل](m365-enterprise-test-lab-guides.md)". بعد الحصول على اشتراك تجريبي أو Microsoft 365، يمكنك إنشاء مجموعات المواقع والمستندات والويب ومكتبات المستندات في SharePoint عبر الإنترنت حيث يمكنك ترحيل البيانات. يمكنك الترحيل يدويا، باستخدام API للترحيل، أو، إذا كنت تريد ترحيل محتوى الموقع الخاص OneDrive for Business، من خلال المعالج المختلط.

> [!NOTE]
> لاستخدام الخيار المختلط، يجب ترقية مزرعة SharePoint Server 2010 أولا إلى SharePoint Server 2013 أو 2016. SharePoint Foundation 2010 SharePoint Foundation 2013 الاتصالات المختلطة مع SharePoint Online.

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>ملخص خيارات Office 2010 والعميل Windows 7

للحصول على ملخص مرئي حول خيارات الترقية والترحيل والانتقال إلى السحابة لعملاء Office 2010 وخادم Windows 7، راجع نهاية ملصق [الدعم](../downloads/Office2010Windows7EndOfSupport.pdf).

[![انتهاء الدعم لعملاء Office 2010 وملصقات Windows 7.](../media/upgrade-from-office-2010-servers-and-products/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

يوضح هذا الملصق المسارات المختلفة التي يمكنك اتخاذها لتجنب منتجات Office 2010 العميل وخادم Windows 7، مع تمييز المسارات المفضلة Microsoft 365 Enterprise الخيارات.

يمكنك أيضا تنزيل [هذا](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) الملصق وطباعته بتنسيق حرف أو قانوني أو جدولي (11 × 17).

## <a name="related-articles"></a>المقالات ذات الصلة

[الموارد لمساعدتك على الترقية من Office 2007 أو 2010 والعملاء](upgrade-from-office-2010-servers-and-products.md)

[نظرة عامة على عملية الترقية من SharePoint 2010 إلى SharePoint 2013](/SharePoint/upgrade-and-update/overview-of-the-upgrade-process-from-sharepoint-2010-to-sharepoint-2013)

[أفضل الممارسات للترقية من SharePoint 2010 إلى SharePoint 2013](/SharePoint/upgrade-and-update/best-practices-for-upgrading-from-sharepoint-2010-to-sharepoint-2013)

[استكشاف مشاكل ترقية قاعدة البيانات وإصلاحها في SharePoint 2013](/SharePoint/upgrade-and-update/troubleshoot-database-upgrade-issues-in-sharepoint-2013)

[البحث عن موفري حلول Microsoft لمساعدتك في الترقية](https://go.microsoft.com/fwlink/?linkid=841249)

[نهج صيانة المنتجات المحدث SharePoint 2013](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-2013)

[نهج صيانة المنتج المحدث SharePoint Server 2016](/SharePoint/product-servicing-policy/updated-product-servicing-policy-for-sharepoint-server-2016)
