---
title: خيارات التنقل ل SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تصف هذه المقالة مواقع خيارات التنقل مع تمكين نشر SharePoint في SharePoint Online.
ms.openlocfilehash: c95666a0fdb78fa584d9ca32ce19f10e4db89753
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940921"
---
# <a name="navigation-options-for-sharepoint-online"></a>خيارات التنقل ل SharePoint Online

تصف هذه المقالة مواقع خيارات التنقل مع تمكين نشر SharePoint في SharePoint Online. يؤثر اختيار التنقل وتكوينه بشكل كبير على أداء المواقع وقابليتها للتوسع في SharePoint Online. يجب استخدام قالب موقع نشر SharePoint فقط إذا لزم الأمر لمدخل مركزي ويجب تمكين ميزة النشر على مواقع معينة فقط وعندما تكون مطلوبة تماما حيث يمكن أن تؤثر على الأداء عند استخدامها بشكل غير صحيح.

>[!NOTE]
>إذا كنت تستخدم خيارات التنقل الحديثة في SharePoint مثل القائمة الضخمة أو التنقل المتتالي أو التنقل في لوحة الوصل، فلن تنطبق هذه المقالة على موقعك. تستفيد بنيات مواقع SharePoint الحديثة من التدرج الهرمي لموقع أكثر تبسيطا ونموذج النظام المحوري. يسمح هذا بالعديد من السيناريوهات التي لا تتطلب استخدام ميزة نشر SharePoint.

## <a name="overview-of-navigation-options"></a>نظرة عامة على خيارات التنقل

يمكن أن يؤثر تكوين موفر التنقل بشكل كبير على أداء الموقع بأكمله، ويجب أخذ الاعتبار الدقيق لاختيار موفر التنقل والتكوين الذي يتوسع بشكل فعال لمتطلبات موقع SharePoint. هناك اثنان من موفري التنقل الجاهزين، بالإضافة إلى تطبيقات التنقل المخصصة.

الخيار الأول، [**التنقل الهيكلي**](#using-structural-navigation-in-sharepoint-online)، هو خيار التنقل الموصى به في SharePoint Online لمواقع SharePoint الكلاسيكية، **إذا قمت بتشغيل التخزين المؤقت للتنقل الهيكلي لموقعك**. يعرض موفر التنقل هذا عناصر التنقل أسفل الموقع الحالي، وبشكل اختياري الموقع الحالي وأخواته. ويوفر قدرات إضافية مثل اقتطاع الأمان وتعداد بنية الموقع. إذا تم تعطيل التخزين المؤقت، فسيؤثر ذلك سلبا على الأداء وقابلية التوسع، وقد يكون عرضة للتقييد.

يمثل الخيار الثاني، [**التنقل المدار (بيانات التعريف)،**](#using-managed-navigation-and-metadata-in-sharepoint-online) عناصر التنقل باستخدام مجموعة مصطلحات بيانات التعريف المدارة. نوصي بتعطيل اقتطاع الأمان ما لم يكن مطلوبا. يتم تمكين اقتطاع الأمان كإعداد آمن افتراضي لموفر التنقل هذا؛ ومع ذلك، لا تتطلب العديد من المواقع حملا زائدا من اقتطاع الأمان نظرا لأن عناصر التنقل غالبا ما تكون متناسقة لجميع مستخدمي الموقع. باستخدام التكوين الموصى به لتعطيل اقتطاع الأمان، لا يتطلب موفر التنقل هذا تعداد بنية الموقع وهو قابل للتطوير بدرجة كبيرة مع تأثير أداء مقبول.

بالإضافة إلى موفري التنقل الجاهزين، نفذ العديد من العملاء بنجاح تطبيقات تنقل مخصصة بديلة. راجع [البرمجة النصية من جانب العميل المستندة إلى البحث في هذه المقالة](#using-search-driven-client-side-scripting) .
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>إيجابيات وسلبيات خيارات التنقل في SharePoint Online

يلخص الجدول التالي إيجابيات وسلبيات كل خيار.

|التنقل البنائي  |التنقل المدار  |التنقل المستند إلى البحث  |موفر التنقل المخصص  |
|---------|---------|---------|---------|
|الايجابيات:<br/><br/>سهولة الصيانة<br/>تم اقتطاع الأمان<br/>يتم التحديث تلقائيا في غضون 24 ساعة عند تغيير المحتوى<br/>     |الايجابيات:<br/><br/>سهولة الصيانة<br/>|الايجابيات:<br/><br/>تم اقتطاع الأمان<br/>التحديثات تلقائيا عند إضافة المواقع<br/>وقت التحميل السريع وبنية التنقل المخزنة مؤقتا محليا<br/>|الايجابيات:<br/><br/>الاختيار الأوسع للخيارات المتاحة<br/>التحميل السريع عند استخدام التخزين المؤقت بشكل صحيح<br/>تعمل العديد من الخيارات بشكل جيد مع تصميم الصفحة المتجاوب<br/>|
|سلبيات:<br/><br/>**يؤثر على الأداء إذا تم تعطيل التخزين المؤقت**<br/>يخضع للتقييد<br/>|سلبيات:<br/><br/>لم يتم تحديثه تلقائيا ليعكس بنية الموقع<br/>**يؤثر على الأداء إذا تم تمكين اقتطاع الأمان** أو عندما تكون بنية التنقل معقدة<br/>|سلبيات:<br/><br/>لا توجد إمكانية لطلب المواقع بسهولة<br/>يتطلب تخصيص الصفحة الرئيسية (المهارات التقنية المطلوبة)<br/>|سلبيات:<br/><br/>التطوير المخصص مطلوب<br/>مطلوب مصدر البيانات الخارجية / ذاكرة التخزين المؤقت المخزنة، على سبيل المثال، Azure<br/>|

سيعتمد الخيار الأنسب لموقعك على متطلبات موقعك وعلى قدراتك التقنية. إذا كنت تريد موفر تنقل سهل التكوين يحدث تلقائيا عند تغيير المحتوى، فإن التنقل الهيكلي [مع تمكين التخزين المؤقت](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) يعد خيارا جيدا.

>[!NOTE]
>يؤدي تطبيق المبدأ نفسه الذي تطبقه مواقع SharePoint الحديثة عن طريق تبسيط بنية الموقع الإجمالية إلى بنية مبسطة وغير هرمية إلى تحسين الأداء وتبسيط الانتقال إلى مواقع SharePoint الحديثة. ما يعنيه هذا هو أنه بدلا من وجود مجموعة مواقع مشتركة واحدة مع مئات المواقع (المجموعات الفرعية)، فإن النهج الأفضل هو أن يكون لديك العديد من مجموعات المواقع المشتركة مع عدد قليل جدا من المواقع الفرعية (المواقع الفرعية).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>تحليل أداء التنقل في SharePoint Online

إن [أداة "تشخيص الصفحة" ل SharePoint](./page-diagnostics-for-spo.md) هي ملحق مستعرض لمستعرضات Microsoft Edge وChrome التي تحلل كل من مدخل SharePoint Online الحديث وصفحات موقع النشر الكلاسيكية. تعمل هذه الأداة مع SharePoint Online فقط، ولا يمكن استخدامها في صفحة نظام SharePoint.

تنشئ الأداة تقريرا لكل صفحة تم تحليلها يعرض كيفية أداء الصفحة مقابل مجموعة محددة مسبقا من القواعد وتعرض معلومات مفصلة عندما تقع نتائج الاختبار خارج قيمة الأساس. يمكن لمسؤولي ومصممي SharePoint Online استخدام الأداة لاستكشاف مشكلات الأداء وإصلاحها لضمان تحسين الصفحات الجديدة قبل النشر.

**SPRequestDuration** على وجه الخصوص هو الوقت الذي يستغرقه SharePoint لمعالجة الصفحة. يمكن أن يساهم التنقل الكثيف (مثل تضمين الصفحات في التنقل) والتسلسلات الهيكلية المعقدة للموقع وخيارات التكوين والمخطط الأخرى بشكل كبير في المدد الأطول.

## <a name="using-structural-navigation-in-sharepoint-online"></a>استخدام التنقل الهيكلي في SharePoint Online

هذا هو التنقل الجاهز المستخدم بشكل افتراضي وهو الحل الأكثر مباشرة. لا يتطلب أي تخصيص ويمكن للمستخدم غير التقني أيضا إضافة عناصر وإخفاء العناصر وإدارة التنقل من صفحة الإعدادات بسهولة. نوصي [بتمكين التخزين المؤقت](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)، وإلا فهناك مفاضلة مكلفة في الأداء.

### <a name="how-to-implement-structural-navigation-caching"></a>كيفية تنفيذ التخزين المؤقت للتنقل الهيكلي

ضمن **"** التنقل في إعدادات  >  الموقع **" و"شكله** > **"، يمكنك** التحقق من صحة ما إذا كان التنقل الهيكلي محددا للتنقل العمومي أو التنقل الحالي. سيكون لتحديد **"إظهار الصفحات"** تأثير سلبي على الأداء.

![التنقل الهيكلي مع تحديد "إظهار المواقع الفرعية".](../media/SPONavOptionsStructuredShowSubsites.png)

يمكن تمكين التخزين المؤقت أو تعطيله على مستوى مجموعة المواقع المشتركة وعلى مستوى الموقع، ويتم تمكينه لكليهما بشكل افتراضي. للتمكين على مستوى مجموعة المواقع المشتركة، ضمن **"التنقل ضمن مجموعة** المواقع المشتركة **لإدارة** >  مجموعة المواقع المشتركة **"** > ، حدد المربع **"تمكين التخزين المؤقت**".

![تمكين التخزين المؤقت على مستوى مجموعة المواقع المشتركة.](../media/structural-nav/structural-nav-caching-site-coll.png)

للتمكين على مستوى الموقع، ضمن **"التنقل** **في إعدادات** >  الموقع"، حدد المربع "**تمكين التخزين المؤقت**".

![تمكين التخزين المؤقت على مستوى الموقع.](../media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>استخدام التنقل المدار وبيانات التعريف في SharePoint Online

التنقل المدار هو خيار آخر غير قابل للاستخدام يمكنك استخدامه لإعادة إنشاء معظم الوظائف نفسها مثل التنقل الهيكلي. يمكن تكوين بيانات التعريف المدارة لتمكين اقتطاع الأمان أو تعطيله. عند تكوينه مع تعطيل اقتطاع الأمان، يكون التنقل المدار فعالا إلى حد ما لأنه يقوم بتحميل كافة ارتباطات التنقل مع عدد ثابت من استدعاءات الخادم. ومع ذلك، فإن تمكين اقتطاع الأمان ينفي بعض مزايا الأداء للتنقل المدار.

إذا كنت بحاجة إلى تمكين اقتطاع الأمان، نوصي بما يلي:

- تحديث كافة ارتباطات URL المألوفة إلى ارتباطات بسيطة
- إضافة عقد اقتطاع الأمان المطلوبة كعناوين URL مألوفة
- تحديد عدد عناصر التنقل إلى ما لا يزيد عن 100 ولا يزيد عمقه عن 3 مستويات

لا تتطلب العديد من المواقع اقتطاع الأمان، حيث إن بنية التنقل غالبا ما تكون متناسقة لجميع مستخدمي الموقع. إذا تم تعطيل اقتطاع الأمان وإضافة ارتباط إلى التنقل الذي لا يملك جميع المستخدمين حق الوصول إليه، فسيستمر الارتباط في الظهور ولكنه سيؤدي إلى رسالة مرفوضة للوصول. لا يوجد خطر من الوصول غير المقصود إلى المحتوى.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>كيفية تنفيذ التنقل المدار والنتائج

هناك العديد من المقالات حول docs.microsoft.com حول تفاصيل التنقل المدار. على سبيل المثال، راجع [نظرة عامة على التنقل المدار في SharePoint Server](/sharepoint/administration/overview-of-managed-navigation).

لتنفيذ التنقل المدار، يمكنك إعداد المصطلحات باستخدام عناوين URL المطابقة لبنية التنقل للموقع. يمكن حتى تنظيم التنقل المدار يدويا لاستبدال التنقل الهيكلي في كثير من الحالات. على سبيل المثال:

![بنية موقع SharePoint Online.](../media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>استخدام البرمجة النصية من جانب العميل المستندة إلى البحث

تتضمن إحدى الفئات الشائعة لتطبيقات التنقل المخصصة أنماط التصميم التي يعرضها العميل والتي تخزن ذاكرة التخزين المؤقت المحلية لعقد التنقل.

يتمتع موفرو التنقل هؤلاء ببعض المزايا الرئيسية:

- تعمل بشكل جيد بشكل عام مع تصميمات الصفحات المتجاوبة.
- وهي قابلة للتطوير للغاية وقابلة للتنفيذ لأنها يمكن أن تعرض بدون تكلفة مورد (وتحديث في الخلفية بعد مهلة).
- يمكن لموفري التنقل استرداد بيانات التنقل باستخدام استراتيجيات مختلفة، بدءا من التكوينات الثابتة البسيطة إلى العديد من موفري البيانات الديناميكيين.

مثال على موفر البيانات هو استخدام **التنقل المستند إلى البحث**، والذي يسمح بالمرونة لتعداد عقد التنقل ومعالجة اقتطاع الأمان بكفاءة.

هناك خيارات شائعة أخرى لإنشاء **موفري تنقل مخصصين**. الرجاء مراجعة [حلول التنقل لمداخل SharePoint Online](/sharepoint/dev/solution-guidance/portal-navigation) للحصول على مزيد من الإرشادات حول إنشاء موفر تنقل مخصص.

باستخدام البحث، يمكنك الاستفادة من الفهارس المضمنة في الخلفية باستخدام تتبع الارتباطات المستمر. يتم سحب نتائج البحث من فهرس البحث ويتم اقتطاع النتائج بأمان. هذا أسرع بشكل عام من موفري التنقل الجاهزين عند الحاجة إلى اقتطاع الأمان. سيؤدي استخدام البحث عن التنقل الهيكلي، خاصة إذا كان لديك بنية موقع معقدة، إلى تسريع وقت تحميل الصفحة بشكل كبير. الميزة الرئيسية لهذا على التنقل المدار هي أنك تستفيد من اقتطاع الأمان.

يتضمن هذا الأسلوب إنشاء صفحة رئيسية مخصصة واستبدال رمز التنقل الجاهز ب HTML مخصص. اتبع هذا الإجراء الموضح في المثال التالي لاستبدال رمز التنقل في الملف `seattle.html`. في هذا المثال، ستفتح `seattle.html` الملف وتستبدل العنصر `id="DeltaTopNavigation"` بأكمله برمز HTML مخصص.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>مثال: استبدال رمز التنقل الجاهز في صفحة رئيسية

1. انتقل إلى صفحة "إعدادات الموقع".
2. افتح معرض الصفحات الرئيسية بالنقر فوق **"الصفحات الرئيسية**".
3. من هنا يمكنك التنقل عبر المكتبة وتنزيل الملف `seattle.master`.
4. تحرير التعليمات البرمجية باستخدام محرر نص وحذف كتلة التعليمات البرمجية في لقطة الشاشة التالية.<br/>![حذف كتلة التعليمات البرمجية المعروضة.](../media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. قم بإزالة التعليمات البرمجية بين العلامات `<SharePoint:AjaxDelta id="DeltaTopNavigation">` واستبدالها `<\SharePoint:AjaxDelta>` بالمقتطف التالي:<br/>

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
6. استبدل عنوان URL في علامة ارتساء صورة التحميل في البداية، بارتباط إلى صورة تحميل في مجموعة المواقع المشتركة. بعد إجراء التغييرات، أعد تسمية الملف ثم قم بتحميله إلى معرض الصفحات الرئيسية. يؤدي هذا إلى إنشاء ملف .master جديد.<br/>
7. HTML هذا هو العلامات الأساسية التي سيتم ملؤها بواسطة نتائج البحث التي تم إرجاعها من التعليمات البرمجية JavaScript. ستحتاج إلى تحرير التعليمات البرمجية لتغيير قيمة جذر var = "عنوان URL لمجموعة المواقع المشتركة" كما هو موضح في القصاصة البرمجية التالية:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. يتم تعيين النتائج إلى صفيف self.nodes ويتم إنشاء تسلسل هرمي من العناصر باستخدام linq.js تعيين الإخراج إلى صفيف self.hierarchy. هذا الصفيف هو الكائن المرتبط ب HTML. يتم ذلك في الدالة toggleView() عن طريق تمرير الكائن الذاتي إلى الدالة ko.applyBinding() .<br/>يؤدي ذلك بعد ذلك إلى ربط صفيف التدرج الهرمي ب HTML التالي:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

تتم إضافة معالجات الأحداث إلى `mouseenter` `mouseexit` التنقل ذي المستوى الأعلى لمعالجة القوائم المنسدلة لموقع فرعي التي يتم تنفيذها في الدالة `addEventsToElements()` .

في مثال التنقل المعقد لدينا، يظهر تحميل صفحة جديد بدون التخزين المؤقت المحلي الوقت المستغرق على الخادم قد تم تقليله من التنقل الهيكلي القياسي للحصول على نتيجة مماثلة لنهج التنقل المدار.

### <a name="about-the-javascript-file"></a>حول ملف JavaScript...

>[!NOTE]
>إذا كنت تستخدم JavaScript مخصصا، فتأكد من تمكين شبكة تسليم المحتوى العامة وأن الملف موجود في موقع شبكة تسليم المحتوى.

ملف JavaScript بأكمله كما يلي:

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

لتلخيص التعليمات البرمجية الموضحة أعلاه في الدالة `jQuery $(document).ready` ، يوجد إنشاء `viewModel object` ثم يتم استدعاء الدالة `loadNavigationNodes()` على هذا الكائن. تعمل هذه الدالة إما على تحميل التسلسل الهيكلي للتنقل الذي تم إنشاؤه مسبقا والمخزن في التخزين المحلي HTML5 لمستعرض العميل أو تستدعي الدالة `queryRemoteInterface()`.

`QueryRemoteInterface()` بناء طلب باستخدام الدالة `getRequest()` مع معلمة الاستعلام المعرفة سابقا في البرنامج النصي ثم إرجاع البيانات من الخادم. هذه البيانات هي في الأساس صفيف من كافة المواقع في مجموعة المواقع المشتركة الممثلة ككائنات نقل بيانات ذات خصائص مختلفة.

ثم يتم تحليل هذه البيانات في الكائنات المعرفة `SPO.Models.NavigationNode` مسبقا التي تستخدم `Knockout.js` لإنشاء خصائص يمكن ملاحظتها للاستخدام من قبل البيانات التي تقوم بربط القيم في HTML الذي قمنا بتعريفه سابقا.

ثم يتم وضع الكائنات في صفيف النتائج. يتم تحليل هذا الصفيف في JSON باستخدام الواق ومخزن في تخزين المستعرض المحلي لتحسين الأداء على أحمال الصفحات المستقبلية.

### <a name="benefits-of-this-approach"></a>فوائد هذا النهج

تتمثل إحدى الفوائد الرئيسية [لهذا الأسلوب](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) في أنه باستخدام التخزين المحلي HTML5، يتم تخزين التنقل محليا للمستخدم في المرة التالية التي يقوم فيها بتحميل الصفحة. نحصل على تحسينات الأداء الرئيسية من استخدام واجهة برمجة تطبيقات البحث للتنقل الهيكلي؛ ومع ذلك، فإنه يتطلب بعض القدرة التقنية لتنفيذ وتخصيص هذه الوظيفة.

في [مثال التنفيذ](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page)، يتم ترتيب المواقع بنفس طريقة التنقل الهيكلي الجاهز؛ ترتيب أبجدي. إذا أردت الانحراف عن هذا الترتيب، فسيكون تطويره وصيانته أكثر تعقيدا. كما يتطلب منك هذا النهج الانحراف عن الصفحات الرئيسية المدعومة. إذا لم يتم الاحتفاظ بالصفحة الرئيسية المخصصة، فسيفوت موقعك التحديثات والتحسينات التي تقوم بها Microsoft على الصفحات الرئيسية.

تحتوي [التعليمات البرمجية أعلاه](#about-the-javascript-file) على التبعيات التالية:

- jQuery - https://jquery.com/
- KnockoutJS - https://knockoutjs.com/
- Linq.js - `https://linqjs.codeplex.com/`أو github.com/neuecc/linq.js

لا يحتوي الإصدار الحالي من LinqJS على أسلوب ByHierarchy المستخدم في التعليمات البرمجية أعلاه وسيقطع رمز التنقل. لإصلاح ذلك، أضف الأسلوب التالي إلى ملف Linq.js قبل السطر `Flatten: function ()`.

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