---
title: خيارات التنقل SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
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
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: تصف هذه المقالة مواقع خيارات التنقل مع SharePoint النشر في SharePoint Online.
ms.openlocfilehash: c59006db8505991bd41d29714caae144b284f07d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569637"
---
# <a name="navigation-options-for-sharepoint-online"></a>خيارات التنقل SharePoint Online

تصف هذه المقالة مواقع خيارات التنقل مع SharePoint النشر في SharePoint Online. يؤثر اختيار التنقل وتكوينه بشكل كبير على أداء المواقع وقابليتها للتدرج في SharePoint Online. يجب SharePoint استخدام قالب موقع النشر فقط إذا لزم الأمر لمدخل مركزي، ويجب تمكين ميزة النشر على مواقع محددة فقط وعند الحاجة إلى ذلك بشكل مطلق حيث يمكن أن تؤثر على الأداء عند استخدامها بشكل غير صحيح.

>[!NOTE]
>إذا كنت تستخدم خيارات التنقل SharePoint مثل قائمة ميغا أو التنقل المتتالي أو التنقل الموزع، فإن هذه المقالة لا تنطبق على موقعك. تستفيد SharePoint الحديثة من التسلسل الهيكلي لموقع أكثر تسطحا ونموذج hub-and-spoke. يسمح هذا الأمر بتحقق العديد من السيناريوهات التي لا تتطلب استخدام SharePoint النشر.

## <a name="overview-of-navigation-options"></a>نظرة عامة حول خيارات التنقل

يمكن أن يؤثر تكوين موفر التنقل بشكل كبير على أداء الموقع بأكمله، ويجب أخذه في الاعتبار بعناية لاختيار موفر تنقل وتكوين يمقياس بفعالية لمتطلبات موقع ويب SharePoint ويب. هناك موفران للتنقل خارج الصندوق، بالإضافة إلى تنفيذات تنقل مخصصة.

الخيار الأول، التنقل [](#using-structural-navigation-in-sharepoint-online)الهيكلي، هو خيار التنقل الموصى به في SharePoint Online لمواقع SharePoint الكلاسيكية، إذا قمت ب تشغيل التخزين المؤقت للتنقل البنائي **لموقعك**. يعرض موفر التنقل هذا عناصر التنقل أسفل الموقع الحالي، واختياريا الموقع الحالي وأشقائه. ويوفر قدرات إضافية مثل اقتطاع الأمان وتسطير بنية الموقع. إذا كان التخزين المؤقت معطلا، فإن ذلك سي يؤثر سلبا على الأداء وقابلية التوسع، وقد يخضع للتقيد.

أما الخيار الثاني، [**وهو التنقل المدار (**](#using-managed-navigation-and-metadata-in-sharepoint-online)بيانات التعريف)، فيمثل عناصر التنقل باستخدام مجموعة مصطلحات بيانات التعريف المدارة. نوصي بتعطيل اقتطاع الأمان ما لم يكن مطلوبا. يتم تمكين اقتطاع الأمان ك إعداد آمن بشكل افتراضي لموفر التنقل هذا؛ على الرغم من ذلك، لا تتطلب العديد من المواقع وجود نفقات أكبر لاقتطاع الأمان نظرا لأن عناصر التنقل غالبا ما تكون متناسقة لجميع مستخدمي الموقع. باستخدام التكوين المستحسن لتعطيل اقتطاع الأمان، لا يتطلب موفر التنقل هذا تعداد بنية الموقع، كما أنه قابل للتدرج بدرجة كبيرة مع تأثير الأداء المقبول.

بالإضافة إلى موفري التنقل غير المتنقلين، نفذ العديد من العملاء تنفيذات بديلة للتنقل المخصص بنجاح. راجع [البرمجة النصية من](#using-search-driven-client-side-scripting) جانب العميل التي يتم البحث عنها في هذه المقالة.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>إيجابيات وسلبيات SharePoint التنقل عبر الإنترنت

يلخص الجدول التالي إيجابيات كل خيار وسلبياته.

|التنقل الهيكلي  |التنقل المدار  |التنقل الذي يحركه البحث  |موفر التنقل المخصص  |
|---------|---------|---------|---------|
|المحترفين:<br/><br/>صيانة سهلة<br/>الأمان المقتطاع<br/>التحديثات تلقائيا في غضون 24 ساعة عند تغيير المحتوى<br/>     |المحترفين:<br/><br/>صيانة سهلة<br/>|المحترفين:<br/><br/>الأمان المقتطاع<br/>التحديثات تلقائيا عند إضافة المواقع<br/>وقت التحميل السريع وبنية التنقل المخزنة مؤقتا محليا<br/>|المحترفين:<br/><br/>خيارات أوسع متوفرة<br/>التحميل السريع عند استخدام التخزين المؤقت بشكل صحيح<br/>تعمل العديد من الخيارات بشكل جيد مع تصميم الصفحة المستجيبة<br/>|
|سلبيات:<br/><br/>**يؤثر على الأداء إذا تم تعطيل التخزين المؤقت**<br/>يخضع لليوتد<br/>|سلبيات:<br/><br/>لم يتم تحديثه تلقائيا لعكس بنية الموقع<br/>**يؤثر على الأداء إذا تم تمكين اقتطاع الأمان** أو عندما تكون بنية التنقل معقدة<br/>|سلبيات:<br/><br/>لا توجد إمكانية طلب المواقع بسهولة<br/>يتطلب تخصيص الصفحة الرئيسية (المهارات التقنية المطلوبة)<br/>|سلبيات:<br/><br/>التطوير المخصص مطلوب<br/>مصدر البيانات الخارجية / ذاكرة التخزين المؤقت المخزنة مطلوبة على سبيل المثال Azure<br/>|

سيعتمد الخيار الأكثر ملاءمة لموقعك على متطلبات موقعك وعلى قدراتك التقنية. إذا كنت تريد موفر تنقل سهل التكوين يتم تحديثه تلقائيا عند تغيير المحتوى، فإن التنقل الهيكلي مع تمكين التخزين المؤقت هو خيار جيد[](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43).

>[!NOTE]
>من خلال تطبيق المبدأ نفسه مثل مواقع SharePoint الحديثة من خلال تبسيط بنية الموقع بشكل عام إلى بنية أكثر إطراء، غير هرمية، يعمل على تحسين الأداء ويبسط الانتقال إلى مواقع SharePoint الحديثة. يعني هذا الأمر أنه بدلا من وجود مجموعة مواقع واحدة مع مئات المواقع (الwebs الفرعية)، فإن الطريقة الأفضل هي أن يكون لديك العديد من مجموعات المواقع مع عدد قليل جدا من المواقع الفرعية (مجموعات فرعية).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>تحليل أداء التنقل في SharePoint Online

أداة [تشخيص الصفحة SharePoint](./page-diagnostics-for-spo.md) هي ملحق مستعرض لمستعرضي Microsoft Edge وChrome يقوم بتحليل كل من SharePoint الحديثة عبر الإنترنت وصفحات موقع النشر الكلاسيكية. تعمل هذه الأداة فقط مع SharePoint Online، ولا يمكن استخدامها على صفحة SharePoint النظام.

تقوم الأداة بإنشاء تقرير لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة مسبقا من القواعد وتعرض معلومات مفصلة عندما تقع نتائج الاختبار خارج قيمة الأساس. SharePoint يمكن للمسؤولين والمصممين عبر الإنترنت استخدام الأداة لا استكشاف مشاكل الأداء وإصلاحها لضمان تحسين الصفحات الجديدة قبل النشر.

**SPRequestDuration بشكل** خاص هو الوقت الذي يستغرقه SharePoint لمعالجة الصفحة. يمكن أن يساهم التنقل الكثيف (مثل بما في ذلك الصفحات في التنقل) والتسلسلات الهيكلية المعقدة للموقع وخيارات التكوين والطبولوجيا الأخرى بشكل كبير في المدد الأطول.

## <a name="using-structural-navigation-in-sharepoint-online"></a>استخدام التنقل الهيكلي في SharePoint Online

هذا هو التنقل خارج المربع المستخدم بشكل افتراضي وهو الحل الأكثر مباشرة. ولا يتطلب أي تخصيص ويمكن للمستخدم غير التقني إضافة العناصر وإخفاء العناصر وإدارة التنقل من صفحة الإعدادات بسهولة. نوصي بتمكين [التخزين المؤقت](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)، وإلا فهناك مقايضة مكلفة للأداء.

### <a name="how-to-implement-structural-navigation-caching"></a>كيفية تنفيذ التخزين المؤقت للتنقل الهيكلي

ضمن **موقع الإعدادات** >  **Look و** **FeelNavigation** > ، يمكنك التحقق من صحة ما إذا كان التنقل الهيكلي محددا للتنقل العام أو التنقل الحالي. سيكون لتحديد **إظهار الصفحات** تأثير سلبي على الأداء.

![التنقل الهيكلي مع تحديد إظهار المواقع الفرعية.](../media/SPONavOptionsStructuredShowSubsites.png)

يمكن تمكين التخزين المؤقت أو تعطيله على مستوى مجموعة المواقع الموقعة وعلى مستوى الموقع، ويمكن تمكينه لكليهما بشكل افتراضي. لتمكين على مستوى مجموعة المواقع، ضمن **موقع** >  >  الإعدادات مجموعة الموقع التنقل في مجموعة المواقع، قم ب تحديد المربع **تمكين التخزين المؤقت**.

![تمكين التخزين المؤقت على مستوى الموقع.](../media/structural-nav/structural-nav-caching-site-coll.png)

لتمكين على مستوى الموقع، ضمن **موقع الإعدادات** >  **التنقل،** ابحث عن خانة الاختيار **تمكين التخزين المؤقت**.

![تمكين التخزين المؤقت على مستوى الموقع.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>استخدام التنقل المدار والبيانات التعريفية في SharePoint Online

التنقل المدار هو خيار آخر غير ممكن يمكنك استخدامه لإعادة إنشاء معظم الوظائف نفسها مثل التنقل الهيكلي. يمكن تكوين بيانات التعريف المدارة لتمكين اقتطاع الأمان أو تعطيله. عند تكوينه مع تعطيل اقتطاع الأمان، يكون التنقل المدار فعالا إلى حد ما أثناء تحميل كل ارتباطات التنقل بعدد ثابت من مكالمات الخادم. ومع ذلك، فإن تمكين اقتطاع الأمان يلغي بعض ميزات أداء التنقل المدار.

إذا كنت بحاجة إلى تمكين اقتطاع الأمان، نوصي بما يلي:

- تحديث كل ارتباطات URL سهلة الاستخدام إلى ارتباطات بسيطة
- إضافة عقد اقتطاع الأمان المطلوبة كعناول URL سهلة الاستخدام
- تحديد عدد عناصر التنقل بمستويات لا يزيد عددها عن 100 عنصر ولا يزيد عمقها عن 3 مستويات

لا تتطلب العديد من المواقع اقتطاع الأمان، حيث إن بنية التنقل غالبا ما تكون متناسقة لجميع مستخدمي الموقع. إذا كان اقتطاع الأمان معطلا وأضيف ارتباط إلى التنقل لا يمكن لجميع المستخدمين الوصول إليه، سيبقى الارتباط اعرض ولكن سيؤدي إلى رسالة تم رفض الوصول إليها. لا يوجد خطر الوصول غير قصد إلى المحتوى.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>كيفية تنفيذ التنقل المدار والنتائج

هناك العديد من المقالات docs.microsoft.com حول تفاصيل التنقل المدار. على سبيل المثال، راجع [نظرة عامة على التنقل المدار في SharePoint Server](/sharepoint/administration/overview-of-managed-navigation).

من أجل تنفيذ التنقل المدار، يمكنك إعداد مصطلحات باستخدام عناوين URL المطابقة لهيكل التنقل للموقع. يمكن حتى أن يتم إدارة التنقل المدار يدويا لاستبدال التنقل الهيكلي في العديد من الحالات. على سبيل المثال:

![SharePoint بنية موقع عبر الإنترنت.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>استخدام البرمجة النصية من جانب العميل التي يتم البحث عنها

تشمل إحدى الفئات الشائعة لتطبيقات التنقل المخصصة أنماط تصميم تم عرضها من قبل العميل تخزن ذاكرة تخزين مؤقت محلية لعقد التنقل.

لدى موفري التنقل هذه بعض المزايا الأساسية:

- فهي تعمل بشكل عام بشكل جيد مع تصميمات الصفحات المستجيبة.
- فهي قابلة للتدرج وأداء شديد لأنها يمكن عرضها بدون تكلفة مورد (وتحديثها في الخلفية بعد انتهاء 2010).
- يمكن لموفري التنقل استرداد بيانات التنقل باستخدام استراتيجيات متنوعة، تتراوح بين تكوينات ثابتة بسيطة وموفري بيانات ديناميكيين مختلفين.

مثال لموفر البيانات هو استخدام التنقل الذي يحركه البحث، والذي يسمح بالمرونة في تعداد عقد التنقل ومعالجة اقتطاع الأمان بفعالية.

هناك خيارات شائعة أخرى لإنشاء **موفري تنقل مخصصين**. الرجاء مراجعة [حلول التنقل SharePoint عبر](/sharepoint/dev/solution-guidance/portal-navigation) الإنترنت للحصول على إرشادات إضافية حول إنشاء موفر تنقل مخصص.

باستخدام البحث، يمكنك الاستفادة من فهارس مضمنة في الخلفية باستخدام تتبع ارتباطات مستمرة. يتم سحب نتائج البحث من فهرس البحث والنتائج مقتطاعة إلى الأمان. بشكل عام، يكون هذا أسرع من موفري التنقل غير المتنقلين عند الحاجة إلى اقتطاع الأمان. سيسرع استخدام البحث عن بنية التنقل، خاصة إذا كان لديك بنية موقع معقدة، من وقت تحميل الصفحة إلى حد كبير. إن الميزة الرئيسية لهذا الأمر على التنقل المدار هي أنك تستفيد من اقتطاع الأمان.

يتضمن هذا النهج إنشاء صفحة رئيسية مخصصة واستبدال التعليمات البرمجية للتنقل خارج المربع ب HTML مخصص. اتبع هذا الإجراء الموضح في المثال التالي لاستبدال رمز التنقل في الملف `seattle.html`. في هذا المثال، ستفتح الملف `seattle.html` وتستبدل العنصر بكامله `id="DeltaTopNavigation"` مع تعليمات HTML البرمجية المخصصة.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>مثال: استبدال التعليمات البرمجية للتنقل خارج المربع في صفحة رئيسية

1. انتقل إلى صفحة الإعدادات الموقع.
2. افتح معرض الصفحات الرئيسية بالنقر فوق **الصفحات الرئيسية**.
3. من هنا يمكنك التنقل عبر المكتبة وتنزيل الملف `seattle.master`.
4. قم بتحرير التعليمة البرمجية باستخدام محرر نص وحذف كتلة التعليمات البرمجية في لقطة الشاشة التالية.<br/>![احذف كتلة التعليمات البرمجية المعروضة.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. قم بإزالة التعليمة البرمجية `<SharePoint:AjaxDelta id="DeltaTopNavigation">` بين العلامات `<\SharePoint:AjaxDelta>` و واستبدالها بالقصاصة التالية:<br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. استبدل URL في علامة تحميل ارتساء الصورة في البداية، مع ارتباط إلى صورة تحميل في مجموعة المواقع. بعد إجراء التغييرات، أعد تسمية الملف ثم قم بتحميله إلى معرض الصفحات الرئيسية. يؤدي ذلك إلى إنشاء ملف .master جديد.<br/>
7. إن HTML هذا هو العلامة الأساسية التي سيتم ملؤها بنتائج البحث التي يتم إرجاعها من التعليمات البرمجية ل JavaScript. ستحتاج إلى تحرير التعليمة البرمجية لتغيير قيمة الجذر var = "URL مجموعة المواقع الموقعة" كما هو مثبت في قصاصة البيانات التالية:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. يتم تعيين النتائج إلى الصفيف self.nodes، كما يتم إنشاء تسلسل هيكلي من العناصر باستخدام linq.js تعيين الإخراج إلى الصفيف self.hierarchy. هذا الصفيف هو الكائن المنضم إلى HTML. يتم ذلك في الدالة toggleView() من خلال تمرير الكائن الذاتي إلى الدالة ko.applyBinding() .<br/>يؤدي ذلك بعد ذلك إلى ربط الصفيف الهرمي ب HTML التالي:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

معالجات الأحداث `mouseenter` `mouseexit` الخاصة بالتنقل في المستوى الأعلى وإضافتها لمعالجة القوائم المنسدلة في الموقع الفرعي التي يتم القيام بها في `addEventsToElements()` الدالة.

في مثال التنقل المركب، يعرض تحميل صفحة جديدة بدون التخزين المؤقت المحلي الوقت المنقضي على الخادم وقد تم قصه من التنقل الهيكلي للمعيار القياسي للحصول على نتيجة مماثلة لنهج التنقل المدار.

### <a name="about-the-javascript-file"></a>حول ملف JavaScript...

>[!NOTE]
>إذا كنت تستخدم JavaScript مخصص، فتأكد من تمكين CDN عام وأن الملف في موقع CDN.

يكون ملف JavaScript بأكمله كما يلي:

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

لتلخيص التعليمة البرمجية المعروضة أعلاه `jQuery $(document).ready` `viewModel object` `loadNavigationNodes()` في الدالة، يتم إنشاء ثم يتم استدعاء الدالة على هذا الكائن. تعمل هذه الدالة إما على تحميل التسلسل الهيكلي للتنقل الذي تم إنشاؤه مسبقا والمخزن في مساحة التخزين المحلية في HTML5 في مستعرض العميل أو أنها تستدعي الدالة `queryRemoteInterface()`.

`QueryRemoteInterface()` إنشاء طلب باستخدام الدالة `getRequest()` باستخدام معلمة الاستعلام المعرفة مسبقا في البرنامج النصي ثم إرجاع البيانات من الخادم. هذه البيانات هي في الأساس صفيف لكل المواقع في مجموعة المواقع التي يتم تمثيلها ككائنات نقل البيانات ذات خصائص مختلفة.

بعد ذلك، يتم تحليل `SPO.Models.NavigationNode` `Knockout.js` هذه البيانات في الكائنات المعرفة مسبقا التي تستخدم لإنشاء خصائص يمكن ملاحظتها لاستخدامها بواسطة ربط البيانات بالقيم ب HTML الذي قمنا بتعريفه مسبقا.

يتم بعد ذلك وضع العناصر في صفيف نتائج. يتم تحليل هذا الصفيف في JSON باستخدام "الضربة الخاطفة" وتخزينه في مساحة تخزين المستعرض المحلي لتحسين الأداء على تحميلات الصفحات المستقبلية.

### <a name="benefits-of-this-approach"></a>فوائد هذا النهج

إحدى الفوائد [الرئيسية لهذا النهج](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) هي أنه باستخدام تخزين HTML5 المحلي، يتم تخزين التنقل محليا للمستخدم في المرة التالية التي يقوم فيها بتحميل الصفحة. نحصل على تحسينات الأداء الرئيسية من استخدام API للبحث عن التنقل الهيكلي؛ ومع ذلك، يتطلب تنفيذ هذه الوظيفة وتخصيصها بعض الإمكانية التقنية.

في [عملية التنفيذ على](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) سبيل المثال، يتم ترتيب المواقع بالطريقة نفسها التي يتم بها ترتيب التنقل البنائي خارج المربع؛ ترتيب أبجدي. إذا أردت أن تنحرف عن هذا الترتيب، فقد يكون تطويره والمحافظة عليه أكثر تعقيدا. كما يتطلب منك هذا النهج أن تنحرف عن الصفحات الرئيسية المعتمدة. إذا لم يتم الاحتفاظ بالصفحة الرئيسية المخصصة، سيفتقد موقعك التحديثات والتحسينات التي تقوم بها Microsoft للصفحات الرئيسية.

[التعليمة البرمجية أعلاه](#about-the-javascript-file) لها التبعيات التالية:

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - https://linqjs.codeplex.com/أو github.com/neuecc/linq.js

لا يحتوي الإصدار الحالي من LinqJS على الأسلوب ByHierarchy المستخدم في التعليمة البرمجية أعلاه وسيقطع رمز التنقل. لإصلاح ذلك، أضف الأسلوب التالي إلى Linq.js قبل السطر `Flatten: function ()`.

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>المواضيع ذات الصلة

[نظرة عامة على التنقل المدار في SharePoint Server](/sharepoint/administration/overview-of-managed-navigation)

[التخزين المؤقت للتنقل الهيكلي والأداء](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)