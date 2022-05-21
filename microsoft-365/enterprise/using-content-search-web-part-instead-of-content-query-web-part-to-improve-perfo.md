---
title: استخدام "جزء ويب البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى" لتحسين الأداء في SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 4/20/2015
audience: Admin
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
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: تعرف على كيفية زيادة الأداء عن طريق استبدال جزء ويب الخاص باستعلام المحتوى بجزء ويب للبحث في المحتوى في SharePoint Server 2013 و SharePoint Online.
ms.openlocfilehash: 45b43b3071ca39c67283ac70ab92b20e2fc7e21a
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621985"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>استخدام "جزء ويب البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى" لتحسين الأداء في SharePoint Online

تصف هذه المقالة كيفية زيادة الأداء عن طريق استبدال جزء ويب الخاص باستعلام المحتوى بجزء ويب للبحث في المحتوى في SharePoint Server 2013 و SharePoint Online.
  
إحدى أقوى الميزات الجديدة في SharePoint Server 2013 و SharePoint Online هي جزء ويب للبحث عن المحتوى (CSWP). يستخدم جزء ويب هذا فهرس البحث لاسترداد النتائج بسرعة، والتي تظهر للمستخدم. استخدم جزء ويب للبحث في المحتوى بدلا من جزء ويب استعلام المحتوى (CQWP) في صفحاتك لتحسين أداء المستخدمين.
  
سيؤدي استخدام جزء ويب للبحث في المحتوى عبر جزء ويب استعلام المحتوى دائما إلى أداء أفضل لتحميل الصفحة على SharePoint Online. هناك القليل من التكوين الإضافي للحصول على الاستعلام الصحيح، ولكن المكافآت هي أداء محسن ومستخدمون أكثر سعادة.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>مقارنة اكتساب الأداء الذي تحصل عليه من استخدام "جزء ويب البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى"

تظهر الأمثلة التالية مكاسب الأداء النسبية التي قد تتلقاها عند استخدام جزء ويب للبحث في المحتوى بدلا من جزء ويب استعلام المحتوى. تكون التأثيرات أكثر وضوحا مع بنية موقع معقدة واستعلامات محتوى واسعة.
  
يحتوي موقع المثال هذا على الخصائص التالية:
  
- 8 مستويات من المواقع الفرعية.
    
- القوائم التي تستخدم نوع محتوى مخصص "فاكهة".
    
- في جزء ويب، يكون استعلام المحتوى واسعا، حيث يقوم بإرجاع كافة العناصر ذات نوع محتوى "الفاكهة".
    
- يستخدم المثال 50 عنصرا فقط عبر المواقع الثمانية. ستكون التأثيرات أكثر وضوحا للمواقع التي تحتوي على المزيد من المحتوى.
    
فيما يلي لقطة شاشة لنتائج جزء ويب الخاص باستعلام المحتوى.
  
![رسم يعرض استعلام المحتوى لجزء ويب.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
في Internet Explorer، استخدم علامة تبويب **الشبكة** الخاصة بأدوات المطور F12 لإلقاء نظرة على تفاصيل رأس الاستجابة. في لقطة الشاشة التالية، تبلغ قيمة **SPRequestDuration** لتحميل الصفحة هذا 924 مللي ثانية. 
  
![لقطة شاشة تعرض مدة الطلب 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 يشير **SPRequestDuration** إلى مقدار العمل الذي يتم على الخادم لإعداد الصفحة. يؤدي تبديل المحتوى حسب الاستعلام أجزاء ويب باستخدام "المحتوى حسب البحث" أجزاء ويب إلى تقليل الوقت المستغرق لعرض الصفحة بشكل كبير. وعلى النقيض من ذلك، تحتوي صفحة تحتوي على جزء ويب للبحث في المحتوى مكافئ، مع إرجاع نفس عدد النتائج على قيمة **SPRequestDuration** تبلغ 106 مللي ثانية كما هو موضح في لقطة الشاشة هذه: 
  
![لقطة شاشة تعرض مدة الطلب 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>إضافة جزء ويب للبحث في المحتوى في SharePoint Online

تشبه إضافة جزء ويب للبحث في المحتوى جزء ويب استعلام المحتوى العادي. راجع المقطع *"إضافة جزء ويب للبحث في المحتوى"* في [تكوين جزء ويب للبحث في المحتوى في SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>إنشاء استعلام البحث الصحيح لجزء ويب الخاص بالبحث في المحتوى

بمجرد إضافة جزء ويب للبحث في المحتوى، يمكنك تحسين البحث وإرجاع العناصر التي تريدها. للحصول على إرشادات مفصلة حول كيفية القيام بذلك، راجع القسم *"عرض المحتوى عن طريق تكوين استعلام متقدم في جزء ويب للبحث في المحتوى"* في [تكوين جزء ويب للبحث في المحتوى في SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>أداة إنشاء الاستعلام واختباره

للحصول على أداة لإنشاء الاستعلامات المعقدة واختبارها، راجع [أداة استعلام البحث](https://sp2013searchtool.codeplex.com/) على Codeplex. 
  

