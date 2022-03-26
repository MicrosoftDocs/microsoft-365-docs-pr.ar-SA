---
title: مراجعة
description: راجع المقطع بعد التكهين.
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
ms.openlocfilehash: 3bb6ef605d360e259ef9fa91ed51da35506a2942
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575578"
---
# <a name="step-6-review-your-selections-to-create-your-package"></a>الخطوة 6: مراجعة التحديدات لإنشاء الحزمة.

1. في علامة التبويب هذه، تعرض الخدمة تفاصيل الاختبار وتدير فحص اكتمال سريع.

    تظهر **رسالة التحقق من الصحة** التي تم تمريرها أو فشل **التحقق** من الصحة ما إذا كان يمكنك المتابعة إلى الخطوات التالية أم لا.

2. راجع تفاصيل الاختبار وإذا كان راضيا، انقر فوق **الزر** إنشاء.

    :::image type="content" alt-text="عرض التحقق من الصحة." source="Media/validation.png" lightbox="Media/validation.png":::

3. سيتم من خلال هذا الأمر تهيئة الحزمة في بيئة Test Base. إذا تم إنشاء الحزمة بنجاح، سيتم تشغيل اختبار تلقائي يتحقق مما إذا كان يمكن تنفيذ الحزمة بنجاح على Azure.

    ![نتيجة ناجحة.](Media/successful.png)

    > [!NOTE]
    > سوف تحصل على إعلام من مدخل Azure لإعلامك بنجاح عملية التحقق من الحزمة أو فشلها.
    >
    > تجدر الإشارة إلى أن العملية قد تستغرق ما يصل إلى 24 ساعة، لذلك من المرجح أن تكون انتهاء 24 ساعة على صفحة ويب إذا لم تكن نشطا فيها، وبالتالي، لن يبلغك الإعلام باكتمال هذا التشغيل عند الطلب.

    - Peradventure يحدث ذلك، يمكنك عرض حالة الحزمة الخاصة بك على علامة **التبويب إدارة الحزم** .

      :::image type="content" alt-text="صورة لإدارة الحزم." source="Media/managepackages.png" lightbox="Media/managepackages.png":::

    - بالنسبة للاختبارات الناجحة، يمكن رؤية نتائجها عبر صفحات نتائج "ملخص  الاختبار" و"نتائج  تحديثات الأمان" و"تحديثات الميزات" في فواصل زمنية مجدولة، غالبا ما تبدأ بعد بضعة أيام من التحميل.
  
    - أثناء فشل الاختبارات، تطلب منك تحميل حزمة جديدة. 

      يمكنك تنزيل سجلات **الاختبار لمزيد** من التحليل من صفحات نتائج تحديث الأمان  وتحديثات **الميزة.**

    - إذا واجهت حالات فشل اختبار متكررة، فالرجاء التواصل مع testbasepreview@microsoft.com تفاصيل الخطأ.

## <a name="next-steps"></a>الخطوات التالية

اكتشف إرشادات المحتوى عبر الارتباط أدناه.

> [!div class="nextstepaction"]
> [الخطوة التالية](contentguideline.md)
