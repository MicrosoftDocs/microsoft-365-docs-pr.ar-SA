---
title: تأخير تحميل الصور وJavaScript في SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
audience: Admin
ms.topic: troubleshooting
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
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: تعرف على كيفية تقليل وقت التحميل لصفحات SharePoint Online باستخدام JavaScript لتأخير تحميل الصور وJavaScript غير الضرورية.
ms.openlocfilehash: af75b3ede1136894bea0a7f4c00cc9498d194fe3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101282"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>تأخير تحميل الصور وJavaScript في SharePoint Online

تصف هذه المقالة كيف يمكنك تقليل وقت تحميل صفحات SharePoint Online باستخدام JavaScript لتأخير تحميل الصور وأيضا بالانتظار لتحميل JavaScript غير الضرورية حتى بعد تحميل الصفحة.
  
يمكن أن تؤثر الصور سلبا على سرعات تحميل الصفحة على SharePoint Online. بشكل افتراضي، تقوم معظم مستعرضات الإنترنت الحديثة بإحضار الصور مسبقا عند تحميل صفحة HTML. قد يؤدي ذلك إلى بطء تحميل الصفحة بشكل غير داع إذا لم تكن الصور مرئية على الشاشة حتى يقوم المستخدم بالتمرير لأسفل. يمكن أن تمنع الصور المستعرض من تحميل الجزء المرئي من الصفحة. لحل هذه المشكلة، يمكنك استخدام JavaScript لتخطي تحميل الصور أولا. كما يمكن أن يؤدي تحميل JavaScript غير الضرورية إلى إبطاء أوقات التنزيل على صفحات SharePoint أيضا. يصف هذا الموضوع بعض الأساليب التي يمكنك استخدامها لتحسين أوقات تحميل الصفحة باستخدام JavaScript في SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>تحسين أوقات تحميل الصفحة عن طريق تأخير تحميل الصور في SharePoint صفحات عبر الإنترنت باستخدام JavaScript

يمكنك استخدام JavaScript لمنع مستعرض ويب من إحضار الصور مسبقا. يؤدي ذلك إلى تسريع عرض المستند بشكل عام. للقيام بذلك، يمكنك إزالة قيمة سمة src من \<img\> العلامة واستبدالها بالمسار إلى ملف في سمة بيانات مثل: data-src. على سبيل المثال:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

باستخدام هذا الأسلوب، لا يقوم المستعرض بتنزيل الصور على الفور. إذا كانت الصورة موجودة بالفعل في منفذ العرض، فسيخبر JavaScript المستعرض باسترداد عنوان URL من سمة البيانات وإدراجه كقيمة للسمة src. يتم تحميل الصورة فقط أثناء تمرير المستخدم وتأتي في العرض.
  
لتحقيق كل ذلك، ستحتاج إلى استخدام JavaScript.
  
في ملف نصي، حدد الدالة **isElementInViewport()** للتحقق مما إذا كان أحد العناصر في جزء المستعرض المرئي للمستخدم أم لا.
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

بعد ذلك، استخدم **isElementInViewport()** في الدالة **loadItemsInView()** . ستقوم الدالة **loadItemsInView()** بتحميل كافة الصور التي تحتوي على قيمة للسمة data-src إذا كانت في جزء المستعرض المرئي للمستخدم. أضف الدالة التالية إلى الملف النصي:
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

وأخيرا، قم باستدعاء **loadItemsInView()** من داخل **window.onscroll()** كما هو موضح في المثال التالي. وهذا يضمن تحميل أي صور موجودة في منفذ العرض حيث يحتاجها المستخدم، ولكن ليس من قبل. أضف ما يلي إلى الملف النصي:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

بالنسبة SharePoint Online، تحتاج إلى إرفاق الدالة التالية بحدث التمرير على علامة مساحة \<div\> العمل #s4. ويعود سبب ذلك إلى تجاوز أحداث النافذة لضمان بقاء الشريط مرفقا بأعلى الصفحة.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

احفظ الملف النصي كملف JavaScript مع .js الملحق، على سبيل المثال delayLoadImages.js.
  
بمجرد الانتهاء من كتابة delayLoadImages.js، يمكنك إضافة محتويات الملف إلى صفحة رئيسية في SharePoint Online. يمكنك القيام بذلك عن طريق إضافة ارتباط برنامج نصي إلى الرأس في الصفحة الرئيسية. بمجرد أن يكون في صفحة رئيسية، سيتم تطبيق JavaScript على جميع الصفحات في موقع SharePoint Online الذي يستخدم تخطيط الصفحة الرئيسية هذا. بدلا من ذلك، إذا كنت تنوي استخدام هذا فقط على صفحة واحدة من موقعك، فاستخدم جزء ويب الخاص بمحرر البرنامج النصي لتضمين JavaScript في الصفحة. راجع هذه المواضيع للحصول على مزيد من المعلومات:
  
- [كيفية: تطبيق صفحة رئيسية على موقع في SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [كيفية: إنشاء تخطيط صفحة في SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>مثال: الإشارة إلى ملف delayLoadImages.js JavaScript من صفحة رئيسية في SharePoint Online
  
لكي يعمل هذا، تحتاج أيضا إلى الإشارة إلى jQuery في الصفحة الرئيسية. في المثال التالي، يمكنك أن ترى في تحميل الصفحة الأولية أنه تم تحميل صورة واحدة فقط ولكن هناك عدة صور أخرى على الصفحة.
  
![لقطة شاشة تعرض صورة واحدة محملة على الصفحة.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
تعرض لقطة الشاشة التالية بقية الصور التي يتم تنزيلها بعد التمرير إلى طريقة العرض.
  
![لقطة شاشة تعرض العديد من الصور التي تم تحميلها على الصفحة.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
يمكن أن يكون تأخير تحميل الصورة باستخدام JavaScript تقنية فعالة في زيادة الأداء؛ ومع ذلك، إذا تم تطبيق التقنية على موقع ويب عام، فلن تتمكن محركات البحث من تتبع الارتباطات في الصور بنفس الطريقة التي تتبع بها صورة مكونة بانتظام. يمكن أن يؤثر هذا على التصنيفات على محركات البحث لأن بيانات التعريف على الصورة نفسها ليست موجودة بالفعل حتى يتم تحميل الصفحة. يقوم متتبعو الفهرس في محرك البحث بقراءة HTML فقط وبالتالي لن يروا الصور كمحتوى على الصفحة. الصور هي أحد العوامل المستخدمة في تصنيف الصفحات في نتائج البحث. إحدى طرق حل هذه المشكلة هي استخدام نص تمهيدي لصورك.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>نموذج التعليمات البرمجية GitHub: إدخال JavaScript لتحسين الأداء

لا تفوت المقالة وعينة التعليمات البرمجية على [حقن JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) المتوفرة على GitHub.
  
## <a name="see-also"></a>راجع أيضًا

[المستعرضات المدعومة في Office 2013 و Microsoft 365 Apps for enterprise](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[كيفية: تطبيق صفحة رئيسية على موقع في SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[كيفية: إنشاء تخطيط صفحة في SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)