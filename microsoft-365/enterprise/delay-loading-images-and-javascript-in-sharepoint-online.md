---
title: تأخير تحميل الصور و JavaScript في SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية تقليل وقت تحميل صفحات SharePoint عبر الإنترنت باستخدام JavaScript لتأخير تحميل الصور و JavaScript غير الضرورية.
ms.openlocfilehash: 6b8eb479ae33b47081e33e45338c02d46f36e055
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568973"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>تأخير تحميل الصور و JavaScript في SharePoint Online

تصف هذه المقالة كيف يمكنك تقليل وقت التحميل لصفحات SharePoint Online باستخدام JavaScript لتأخير تحميل الصور وأيضا عن طريق الانتظار لتحميل JavaScript غير الضرورية حتى بعد تحميل الصفحة.
  
يمكن أن تؤثر الصور سلبا على سرعات تحميل الصفحة على SharePoint عبر الإنترنت. بشكل افتراضي، تقوم معظم مستعرضات الإنترنت الحديثة بإحضار الصور مسبقا عند تحميل صفحة HTML. قد يؤدي ذلك إلى بطء تحميل الصفحة بشكل غير داع إذا لم تكن الصور مرئية على الشاشة حتى يقوم المستخدم بالتمرير لأسفل. يمكن للصور منع المستعرض من تحميل الجزء المرئي من الصفحة. لل حل هذه المشكلة، يمكنك استخدام JavaScript لتخطي تحميل الصور أولا. كما أن تحميل JavaScript غير الضرورية قد يبطئ أوقات التنزيل على SharePoint الصفحات أيضا. يصف هذا الموضوع بعض الأساليب التي يمكنك استخدامها لتحسين أوقات تحميل الصفحات باستخدام JavaScript في SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>تحسين أوقات تحميل الصفحات عن طريق تأخير تحميل الصور في SharePoint عبر الإنترنت باستخدام JavaScript

يمكنك استخدام JavaScript لمنع مستعرض ويب من إحضار الصور مسبقا. يؤدي ذلك إلى زيادة سرعة عرض المستند بشكل عام. للقيام بذلك، يمكنك إزالة قيمة السمة src \<img\> من العلامة واستبدالها بالمسار إلى ملف في سمة بيانات مثل: data-src. على سبيل المثال:
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

باستخدام هذا الأسلوب، لا ينزيل المستعرض الصور على الفور. إذا كانت الصورة موجودة بالفعل في منفذ العرض، فإن JavaScript يخبر المستعرض باسترداد عنوان URL من سمة البيانات وإدراجه كقيمة السمة src. يتم تحميل الصورة فقط عندما يقوم المستخدم بالتمرير ويدخل في طريقة العرض.
  
لجعل كل هذا يحدث، ستحتاج إلى استخدام JavaScript.
  
في ملف نصي، حدد الدالة **isElementInViewport()** للتحقق مما إذا كان العنصر في جزء المستعرض المرئي للمستخدم أم لا.
  
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

بعد ذلك، **استخدم isElementInViewport()** في **الدالة loadItemsInView()** . **ستحمل الدالة loadItemsInView()** كل الصور التي لها قيمة السمة data-src إذا كانت في جزء المستعرض المرئي للمستخدم. أضف الدالة التالية إلى الملف النصي:
  
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

وأخيرا، قم باستدعاء **loadItemsInView()** من **داخل window.onscroll()** كما هو موضح في المثال التالي. يضمن ذلك تحميل أي صور في منفذ العرض حسب ما يحتاجه المستخدم، وليس من قبل. أضف ما يلي إلى الملف النصي:
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

بالنسبة SharePoint Online، ستحتاج إلى إرفاق الدالة التالية بحدث التمرير على علامة #s4 مساحة العمل\<div\>. وذلك بسبب تجاوز أحداث النافذة لضمان استمرار إرفاق الشريط بأعلى الصفحة.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

احفظ الملف النصي كملف JavaScript مع ملحق .js، على سبيل delayLoadImages.js.
  
بعد الانتهاء من كتابة delayLoadImages.js، يمكنك إضافة محتويات الملف إلى صفحة رئيسية في SharePoint Online. يمكنك القيام بذلك عن طريق إضافة ارتباط برنامج نصي إلى الرأس في الصفحة الرئيسية. بمجرد أن يكون في صفحة رئيسية، سيتم تطبيق JavaScript على كل الصفحات الموجودة في SharePoint Online التي تستخدم تخطيط الصفحة الرئيسية هذا. بدلا من ذلك، إذا كنت تنوي استخدام هذا على صفحة واحدة فقط من موقعك، فاستخدم جزء ويب الخاص محرر البرنامج النصي لتضمين JavaScript في الصفحة. راجع هذه المواضيع للحصول على مزيد من المعلومات:
  
- [كيفية: تطبيق صفحة رئيسية على موقع في SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [كيفية: إنشاء تخطيط صفحة في SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>مثال: الإشارة إلى ملف JavaScript delayLoadImages.js من صفحة رئيسية في SharePoint Online
  
لكي يعمل ذلك، ستحتاج أيضا إلى الإشارة إلى jQuery في الصفحة الرئيسية. في المثال التالي، يمكنك أن ترى في تحميل الصفحة الأولية أنه تم تحميل صورة واحدة فقط ولكن هناك عدة صور أخرى على الصفحة.
  
![لقطة شاشة تعرض صورة واحدة تم تحميلها على الصفحة.](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
تعرض لقطة الشاشة التالية باقي الصور التي يتم تنزيلها بعد تمريرها إلى طريقة العرض.
  
![لقطة شاشة تعرض العديد من الصور التي تم تحميلها على الصفحة.](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
يمكن أن يكون تأخير تحميل الصور باستخدام JavaScript أسلوبا فعالا في زيادة الأداء؛ ومع ذلك، إذا تم تطبيق التقنية على موقع ويب عام، فإن محركات البحث لن تتمكن من تتبع ارتباطات الصور بنفس الطريقة التي تتبع بها ارتباطات صورة تم تكوينها بشكل منتظم. يمكن أن يؤثر ذلك على التصنيفات على محركات البحث لأن بيانات التعريف على الصورة نفسها لا تكون هناك بالفعل حتى يتم تحميل الصفحة. لا تقرأ متتبعات ارتباطات محركات البحث سوى HTML وبالتالي لن ترى الصور كمحتوى على الصفحة. الصور هي أحد العوامل المستخدمة لتصنف الصفحات في نتائج البحث. وتكمن إحدى الطرق التي يمكن استخدامها في استخدام نص تمهيدي للصور.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub التعليمات البرمجية: إدخال JavaScript لتحسين الأداء

لا تفوت المقالة ونموذج التعليمات البرمجية في عملية إقضاع [JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) المتوفرة على GitHub.
  
## <a name="see-also"></a>راجع أيضًا

[المستعرضات المعتمدة في Office 2013 Microsoft 365 Apps for enterprise](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[كيفية: تطبيق صفحة رئيسية على موقع في SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[كيفية: إنشاء تخطيط صفحة في SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)