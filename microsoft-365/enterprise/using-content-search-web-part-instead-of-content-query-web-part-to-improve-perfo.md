---
title: استخدام "جزء ويب البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى" لتحسين الأداء في SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية زيادة الأداء من خلال استبدال جزء ويب الخاص باستعلام المحتوى بجزء ويب للبحث في المحتوى في SharePoint Server 2013 SharePoint Online.
ms.openlocfilehash: d41983a5771e42d357ae4d2adb5864e2a74fdd57
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572883"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>استخدام "جزء ويب البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى" لتحسين الأداء في SharePoint Online

تصف هذه المقالة كيفية زيادة الأداء من خلال استبدال جزء ويب الخاص باستعلام المحتوى بجزء ويب للبحث في المحتوى في SharePoint Server 2013 SharePoint Online.
  
إحدى الميزات الجديدة الأكثر قوة ل SharePoint Server 2013 SharePoint Online هي جزء ويب للبحث في المحتوى (CSWP). يستخدم جزء ويب هذا فهرس البحث لاسترداد النتائج التي تظهر للمستخدم بسرعة. استخدم جزء ويب للبحث في المحتوى بدلا من جزء ويب الخاص باستعلام المحتوى (CQWP) في صفحاتك لتحسين أداء المستخدمين.
  
يؤدي دائما استخدام جزء ويب البحث في المحتوى عبر جزء ويب استعلام المحتوى إلى أداء تحميل صفحة أفضل بشكل ملحوظ على SharePoint Online. هناك القليل من التكوين الإضافي للحصول على الاستعلام المناسب، ولكن المكافآت هي أداء محسن ومستخدمين أكثر بسعادة.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>مقارنة مكسب الأداء الذي تحصل عليه من استخدام جزء ويب "البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى"

تظهر الأمثلة التالية المكاسب النسبية للأداء التي قد تتلقاها عند استخدام "جزء ويب البحث في المحتوى" بدلا من "جزء ويب استعلام المحتوى". تكون التأثيرات أكثر وضوحا مع بنية موقع معقدة واستعلامات محتوى واسعة جدا.
  
يحتوي موقع المثال هذا على الخصائص التالية:
  
- 8 مستويات من الموقع الفرعي.
    
- القوائم التي تستخدم نوع محتوى مخصص "فاكهة".
    
- في جزء ويب، يكون استعلام المحتوى واسعا، مع إرجاع كل العناصر التي تحتوي على نوع المحتوى "فاكهة".
    
- يستخدم المثال 50 عنصر فقط عبر 8 مواقع. سوف تكون التأثيرات أكثر وضوحا للمواقع ذات المحتوى الأكثر.
    
إليك لقطة شاشة لنتائج جزء ويب الخاص باستعلام المحتوى.
  
![رسم يعرض استعلام المحتوى لجزء ويب.](../media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
في Internet Explorer، استخدم علامة **التبويب** شبكة لأدوات المطور F12 لنظرة على تفاصيل رأس الاستجابة. في لقطة الشاشة التالية، تكون قيمة **SPRequestDuration** لتحميل هذه الصفحة 924 مللي ثانية. 
  
![لقطة شاشة تعرض مدة الطلب 924.](../media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **تشير SPRequestDuration** إلى مقدار العمل الذي يتم على الخادم لتحضير الصفحة. يؤدي تبديل المحتوى أجزاء ويب الاستعلام باستخدام المحتوى حسب أجزاء ويب إلى تقليل الوقت المستغرق في عرض الصفحة بشكل كبير. في المقابل، تحتوي الصفحة التي تحتوي على جزء ويب للبحث في المحتوى مكافئ لها، مع إرجاع العدد نفسه من النتائج على **قيمة SPRequestDuration** 106 مللي ثانية كما هو موضح في لقطة الشاشة هذه: 
  
![لقطة شاشة تعرض مدة الطلب 106.](../media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>إضافة جزء ويب للبحث في المحتوى في SharePoint Online

تعد إضافة جزء ويب للبحث في المحتوى مشابهة إلى حد كبير لجزء ويب العادي لاستعلام المحتوى. راجع المقطع *"إضافة جزء ويب للبحث في المحتوى"* في تكوين جزء ويب للبحث في [المحتوى في SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>إنشاء استعلام البحث المناسب لجزء ويب "البحث في المحتوى"

بعد إضافة جزء ويب للبحث في المحتوى، يمكنك تحسين البحث وإرجاع العناصر التي تريدها. للحصول على إرشادات مفصلة حول كيفية القيام بذلك، راجع المقطع "عرض المحتوى من خلال تكوين استعلام متقدم في جزء ويب للبحث في المحتوى *"* في تكوين جزء ويب للبحث في المحتوى في [SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>أداة إنشاء الاستعلام واختباره

للحصول على أداة لإنشاء الاستعلامات المعقدة واختبارها، راجع أداة [استعلام البحث](https://sp2013searchtool.codeplex.com/) على Codeplex. 
  

