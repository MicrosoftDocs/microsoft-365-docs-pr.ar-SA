---
title: استنساخ حزمة موجودة
description: كيفية استنساخ حزمة موجودة
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 05/27/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 1e0f4ca8939a965347126076f5fef7e85a103c9c
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "66857350"
---
# <a name="clone-an-existing-package"></a>استنساخ حزمة موجودة

في هذا القسم، ستتعلم كيفية إنشاء حزمة جديدة عن طريق تكرار الحزمة المنشورة مسبقا كنقطة بداية. هناك العديد من المداخل على مدخل قاعدة الاختبار لبدء رحلة حزمة النسخ.

> [!IMPORTANT]
> لاستخدام وظيفة حزمة النسخ، تحتاج إلى أن يكون لديك حزمة واحدة على الأقل تم تحميلها بنجاح على قاعدة الاختبار. 

## <a name="starting-from-the-new-package-page"></a>بدءا من صفحة الحزمة الجديدة

> [!div class="mx-imgBorder"]
> [![إرشادات](Media/clonepackage01_guidance.png) الاستنساخ ](Media/clonepackage01_guidance.png#lightbox)

1. في صفحة **الحزمة الجديدة** ، يمكنك التحديد على **الحزمة الموجودة** Clone. ثم حدد حزمة واحدة من قائمة الحزم الموجودة وانقر فوق **"Clone".** 

   > [!div class="mx-imgBorder"]
   > [![استنساخ الحزمة](Media/clonepackage02_clone_package.png) الموجودة ](Media/clonepackage02_clone_package.png#lightbox)

2. سيتم توجيهك إلى خطوات إنشاء الحزمة الجديدة مع جميع المعلومات والتكوينات التي تم ملؤها مسبقا مثل الحزمة التي نسختها. المعلومات الوحيدة التي يجب عليك تغييرها هي **إصدار الحزمة** ضمن قسم **المعلومات الأساسية** . 

   > [!NOTE]
   > يجب أن يكون الجمع بين اسم الحزمة والإصدار فريدا داخل حساب قاعدة الاختبار. 

   > [!div class="mx-imgBorder"]
   > [![حزم المعلومات](Media/clonepackage03_basic_information.png) الأساسية ](Media/clonepackage03_basic_information.png#lightbox)

3. يمكنك:

   - معاينة كافة معلومات إعداد الحزمة التي تم ملؤها مسبقا تكرارها من حزمة النسخ. 
   - قم بإجراء أي تغييرات من الخطوة 1 إلى الخطوة 4 (راجع تحميل الحزمة المضغوطة التي تم إنشاؤها مسبقا للحصول على إرشادات أكثر تفصيلا). 
   - المراجعة والنشر إلى قاعدة الاختبار. 


## <a name="starting-from-the-manage-packages-page"></a>بدءا من صفحة إدارة الحزم

في صفحة **إدارة الحزم** ، يمكنك استنساخ حزمة عن طريق تحديد أيقونة **"Clone"** ضمن عمود الإجراءات السريعة. 

> [!div class="mx-imgBorder"]
> [![صفحة](Media/clonepackage04_manage_packages.png) إدارة الحزم ](Media/clonepackage04_manage_packages.png#lightbox)

أو يمكنك الانتقال إلى صفحة **نظرة عامة على الحزمة** الخاصة بالحزمة المحددة التي حددتها من صفحة **إدارة الحزم** وتحديد أيقونة **"Clone package** " في قائمة الإجراءات العلوية.

> [!div class="mx-imgBorder"]
> [![النسخ من صفحة](Media/clonepackage05_overview.png) النظرة العامة ](Media/clonepackage05_overview.png#lightbox)

