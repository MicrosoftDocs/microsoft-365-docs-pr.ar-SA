---
title: Upload الثنائيات للتطبيقات
description: كيفية بدء استخدام Test Base ل M365
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 200da9ca73bc666f3f11fc3fda95493d2c0954fb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575576"
---
# <a name="step-3-upload-your-binaries-dependencies-and-scripts"></a>الخطوة 3: Upload الثنائيات والتبعيات والنصية

في علامة التبويب هذه، سيتم تحميل حزمة بريدية واحدة تحتوي على الثنائيات والتبعيات والنصية المستخدمة لتشغيل مجموعة الاختبار.

> [!NOTE]
> يجب أن يكون حجم الحزمة البريدية بين 10 مبايت كحد أدنى و2 غيغابايت كحد أقصى.

## <a name="upload-package-zip-file"></a>Upload zip الخاص بالحزمة

:::image type="content" alt-text="Upload الثنائيات." source="Media/AddBinaries.png":::

  - يمكن أن تتضمن التبعيات التي تم تحميلها إطارات عمل اختبارية أو محركات النصية أو بيانات سيتم الوصول إليها لتشغيل التطبيق أو حالات الاختبار. على سبيل المثال، يمكنك تحميل Selenium ومثبت برنامج تشغيل ويب للمساعدة في تشغيل الاختبارات المستندة إلى المستعرض.
  - من أفضل الممارسات التأكد من الاحتفاظ بأنشطة البرنامج النصي وحدات نمطية، أي. 
    - ينفذ `Install` البرنامج النصي عمليات التثبيت فقط.
    - لا `Launch` يتم تشغيل البرنامج النصي إلا للتطبيق.
    - يغلق `Close` البرنامج النصي التطبيق فقط.
    - إلغاء تثبيت `Uninstall` التطبيق فقط في البرنامج النصي الاختياري.

**حاليا، لا يدعم المدخل سوى برامج PowerShell النصية.**


## <a name="next-steps"></a>الخطوات التالية 

التقدم إلى المقالة التالية الانتقال إلى الخطوة 4: **تعيين المهام الاختبارية**.
> [!div class="nextstepaction"]
> [الرجوع للخلف](uploadApplication.md)
> [!div class="nextstepaction"]
> [الخطوة التالية](testtask.md)

