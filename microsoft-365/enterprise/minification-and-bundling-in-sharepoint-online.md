---
title: التصغير والتجميع في SharePoint Online
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
description: تعرف على كيفية استخدام تقنيات التصغير والتجميع مع Web Essentials لتقليل طلبات HTTP والوقت المستغرق لتحميل الصفحات في SharePoint Online.
ms.openlocfilehash: b02cf095b1d7f05a82df1cf98a590ff762453f8a
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637616"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>التصغير والتجميع في SharePoint Online

تصف هذه المقالة كيفية استخدام تقنيات التصغير والتجميع مع Web Essentials لتقليل عدد طلبات HTTP وتقليل الوقت المستغرق لتحميل الصفحات في SharePoint Online.
  
عند تخصيص موقعك على ويب، يمكنك في نهاية المطاف إضافة عدد كبير من الملفات الإضافية إلى الخادم لدعم التخصيص. تزيد إضافة JavaScript وCSS وصور إضافية من عدد طلبات HTTP إلى الخادم، مما يؤدي بدوره إلى زيادة الوقت المستغرق لعرض صفحة ويب. إذا كان لديك ملفات متعددة من نفس النوع، يمكنك تجميع هذه الملفات لجعل تنزيل هذه الملفات أسرع.
  
بالنسبة لملفات JavaScript وCSS، يمكنك أيضا استخدام نهج يسمى التصغير، حيث يمكنك تقليل الحجم الإجمالي للملفات عن طريق إزالة المسافة البيضاء والأحرف الأخرى غير الضرورية.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>تصغير ملفات JavaScript وCSS وتخزينها باستخدام Web Essentials

يمكنك استخدام برامج تابعة لجهة خارجية مثل Web Essentials لتجميع ملفات CSS وJavaScript.
  
> [!IMPORTANT]
> Web Essentials هو مشروع تابع لجهة خارجية ومفتوح المصدر قائم على المجتمع. البرنامج هو ملحق Visual Studio 2012 Visual Studio 2013 ولا تدعمه Microsoft. لتنزيل Web Essentials، تفضل بزيارة موقع [الويب في Web Essentials 2012](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebEssentials2012).
  
يوفر Web Essentials شكلين من تجميع البيانات:
 
- .bundle: لملفات CSS وJavaScript
- .sprite: للصور (متوفر فقط في Visual Studio 2013)

يمكنك استخدام Web Essentials إذا كانت لديك ميزة موجودة مع بعض عناصر العلامة التجارية المشار إليها داخل صفحة رئيسية مخصصة، مثل:
  
![لقطة شاشة لعنصر العلامة التجارية في الصفحة الرئيسية المخصصة.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>لإنشاء مجموعة TE000127218 وCSS في Web Essentials
  
1. في Visual Studio، في مستكشف الحلول، حدد الملفات التي تريد تضمينها في المجموعة.
2. انقر بزر الماوس الأيمن فوق الملفات المحددة ثم حدد **Web Essentials** \> **Create JavaScript bundle file** من قائمة السياق. على سبيل المثال:

    ![لقطة شاشة تعرض خيارات قائمة Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>عرض نتائج تجميع ملفات JavaScript وCSS

عند إنشاء مجموعة JavaScript وCSS، ينشئ Web Essentials ملف XML يسمى ملف وصفة يحدد ملفات JavaScript وCSS بالإضافة إلى بعض معلومات التكوين الأخرى:
  
![لقطة شاشة لملف وصفة JavaScript وCSS.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
بالإضافة إلى ذلك، إذا تم تعيين علامة التصغير إلى true في وصفة التجميع، يتم تقليل حجم الملفات وجمعها معا. وهذا يعني أنه تم إنشاء إصدارات جديدة من ملفات JavaScript التي يمكنك الرجوع إليها في الصفحة الرئيسية.
  
![لقطة شاشة لعلامة minify المعينة إلى true.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
عند تحميل صفحة من موقع ويب، يمكنك استخدام أدوات المطور من مستعرض الويب الخاص بك، مثل Internet Explorer 11، لمعرفة عدد الطلبات المرسلة إلى الخادم والمدة التي استغرقها تحميل كل ملف.
  
الشكل التالي هو نتيجة تحميل ملفات JavaScript وCSS قبل التصغير.
  
![لقطة شاشة تعرض 80 عنصرا يتم تنزيلها.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
بعد تجميع ملفات CSS وJavaScript معا، انخفض عدد الطلبات إلى 74 وكل ملف استغرق وقتا أطول قليلا من الملفات الأصلية لتنزيلها بشكل فردي:
  
![لقطة شاشة تعرض 74 عنصرا يتم تنزيلها.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
بعد تجميع البيانات، يتم تقليل ملف مجموعة JavaScript بشكل ملحوظ من 815 كيلوبايت إلى 365 كيلوبايت:
  
![لقطة شاشة تعرض حجم التنزيل المخفض.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>تجميع الصور عن طريق إنشاء مجموعة صور

على غرار كيفية تجميع ملفات JavaScript وCSS، يمكنك دمج العديد من الأيقونات الصغيرة والصور الشائعة الأخرى في ورقة صور كبيرة ثم استخدام CSS للكشف عن الصور الفردية. بدلا من تنزيل كل صورة فردية، يقوم مستعرض الويب الخاص بالمستخدم بتنزيل ورقة sprite مرة واحدة ثم تخزينها مؤقتا على الكمبيوتر المحلي. يؤدي ذلك إلى تحسين أداء تحميل الصفحة عن طريق تقليل عدد التنزيلات والرحلات الدائرية إلى خادم الويب.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>لإنشاء صورة sprite في Web Essentials**
  
1. في Visual Studio، في مستكشف الحلول، حدد الملفات التي تريد تضمينها في المجموعة.
2. انقر بزر الماوس الأيمن فوق الملفات المحددة ثم حدد **Web Essentials** \> **Create image sprite** من قائمة السياق. على سبيل المثال:

    ![Screenshot showing how to create an image sprite.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. اختر موقعا لحفظ ملف sprite. ملف .sprite هو ملف XML يصف الإعدادات والملفات في مجموعة الصور. توضح الأرقام التالية مثالا لملف sprite PNG وملف .sprite XML المطابق له.

    ![لقطة شاشة لملف sprite.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![لقطة شاشة لملف sprite XML.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
