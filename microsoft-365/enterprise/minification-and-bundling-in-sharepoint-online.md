---
title: التكبير والتقديس في SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
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
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: تعرف على كيفية استخدام تقنيات التكبير والتقديس مع Web Essentials لتقليل طلبات HTTP والوقت المستغرق لتحميل الصفحات في SharePoint Online.
ms.openlocfilehash: fabf690f523cabf67fe775bbd1a10251a477f633
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63575278"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>التكبير والتقديس في SharePoint Online

تصف هذه المقالة كيفية استخدام تقنيات التكبير والتعداد مع Web Essentials لتقليل عدد طلبات HTTP وتقليل الوقت المستغرق لتحميل الصفحات في SharePoint Online.
  
عند تخصيص موقعك على ويب، يمكنك في النهاية إضافة عدد كبير من الملفات الإضافية إلى الخادم لدعم التخصيص. تؤدي إضافة صور JavaScript و CSS وصور إضافية إلى زيادة عدد طلبات HTTP إلى الخادم، مما يزيد بدوره من الوقت المستغرق لعرض صفحة ويب. إذا كان لديك ملفات متعددة من النوع نفسه، يمكنك تجميع هذه الملفات لجعل تنزيل هذه الملفات أسرع.
  
بالنسبة لملفات JavaScript و CSS، يمكنك أيضا استخدام نهج يسمى التكبير، حيث يمكنك تقليل الحجم الإجمالي للملفات عن طريق إزالة المساحة البيضاء والأحرف الأخرى غير الضرورية.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>تكبير ملفات JavaScript و CSS وتكديسها باستخدام Web Essentials

يمكنك استخدام برامج جهة خارجية مثل Web Essentials لحزم ملفات CSS و JavaScript.
  
> [!IMPORTANT]
> Web Essentials هو مشروع من جهة خارجية مفتوح المصدر يستند إلى المجتمع. البرنامج هو ملحق Visual Studio 2012 Visual Studio 2013 ولا تدعمه Microsoft. لتنزيل Web Essentials، تفضل بزيارة موقع ويب على .[https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629)
  
يوفر Web Essentials شكلين من أشكال تجميع العناصر:
  
- .bundle: لملفات CSS و JavaScript
- .sprite: للصور (متوفر فقط في Visual Studio 2013)

يمكنك استخدام Web Essentials إذا كانت لديك ميزة موجودة مع بعض عناصر العلامة التجارية المشار إليها داخل صفحة رئيسية مخصصة، مثل:
  
![لقطة شاشة لعناصر العلامة التجارية في الصفحة الرئيسية المخصصة.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>لإنشاء مجموعة TE000127218 و CSS في Web Essentials
  
1. في Visual Studio، في Solution Explorer، حدد الملفات التي تريد تضمينها في المجموعة.
2. انقر بضغطة زر الماوس الأيمن فوق الملفات المحددة، ثم حدد **Web Essentials** \> **إنشاء ملف مجموعة JavaScript** من قائمة السياق. على سبيل المثال:

    ![لقطة شاشة تعرض خيارات قائمة Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>عرض نتائج تجميع ملفات JavaScript و CSS

عند إنشاء مجموعة JavaScript و CSS، ينشئ Web Essentials ملف XML يسمى ملف وصفة يعرف ملفات JavaScript و CSS بالإضافة إلى بعض معلومات التكوين الأخرى:
  
![لقطة شاشة لملف وصفة JavaScript و CSS.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
بالإضافة إلى ذلك، إذا تم تعيين علامة التكبير إلى true في وصفة تجميع الملفات، فينخفض حجم الملفات ويضاف بعضها إلى مجموعة. وهذا يعني أنه قد تم إنشاء إصدارات جديدة محدثة من ملفات JavaScript يمكنك الرجوع إليها في الصفحة الرئيسية.
  
![لقطة شاشة لعلم الحد الذي تم تعيينه إلى true.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
عند تحميل صفحة من موقع ويب، يمكنك استخدام أدوات المطور من مستعرض الويب، مثل Internet Explorer 11، لمعرفة عدد الطلبات المرسلة إلى الخادم والمهة التي استغرقها تحميل كل ملف.
  
الشكل التالي هو نتيجة تحميل ملفات JavaScript و CSS قبل التكبير.
  
![لقطة شاشة تعرض 80 عنصر يتم تنزيلها.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
بعد تجميع ملفات CSS و JavaScript معا، انخفض عدد الطلبات إلى 74 طلب واستغرق كل ملف وقتا أطول قليلا من الملفات الأصلية للتنزيل بشكل فردي:
  
![لقطة شاشة تعرض 74 عنصر يتم تنزيلها.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
بعد تجميع الملفات، يتم تقليل ملف مجموعة JavaScript بشكل ملحوظ من 815 كيلوبت إلى 365 كيلوبت في الثانية:
  
![لقطة شاشة تعرض حجم تنزيل مصغر.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>تجميع الصور عن طريق إنشاء مجموعة صور

على غرار كيفية تجميع ملفات JavaScript و CSS، يمكنك دمج العديد من الأيقونات الصغيرة والصور الشائعة الأخرى في ورقة مجموعة أكبر ثم استخدام CSS للكشف عن الصور الفردية. بدلا من تنزيل كل صورة فردية، يقوم مستعرض الويب الخاص المستخدم بتنزيل ورقة "مجموعة الصور" مرة واحدة ثم تخزينها مؤقتا على الكمبيوتر المحلي. من خلال خفض عدد التنزيلات والرحلات المستديرة إلى خادم الويب، من خلال تحسين أداء تحميل الصفحة.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>لإنشاء مجموعة صور في Web Essentials**
  
1. في Visual Studio، في Solution Explorer، حدد الملفات التي تريد تضمينها في المجموعة.
2. انقر بضغطة زر الماوس الأيمن فوق الملفات المحددة، ثم حدد **Web Essentials** \> **إنشاء** مجموعة صور من قائمة السياق. على سبيل المثال:

    ![لقطة شاشة تعرض كيفية إنشاء مجموعة صور.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. اختر موقع لحفظ ملف "مجموعة احفظه". ملف .sprite هو ملف XML يصف الإعدادات والملفات في مجموعة الصور. تظهر الأرقام التالية مثالا لملف PNG من نوع sprite وملف .sprite XML المناظر له.

    ![لقطة شاشة لملف "مجموعة صور".](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![لقطة شاشة لملف sprite XML.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
