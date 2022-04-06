---
title: Upload حزمتك
description: كيفية تحميل التطبيق وال الثنائيات والتبعيات إلى Test Base
search.appverid: MET150
author: mansipatel-usl
ms.author: rshastri
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 99b25757b3f7b0b3d4fcd43f97bab2ac303de6fa
ms.sourcegitcommit: b1a2b09edbcfcc62ff3f1ecf5bd8adb1afa344c8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/22/2021
ms.locfileid: "63583339"
---
# <a name="step-2-uploading-a-package"></a>الخطوة 2: تحميل حزمة

في صفحة مدخل قاعدة الاختبار، انتقل إلى Upload **حزمة** جديدة على شريط التنقل الأيسر كما هو موضح أدناه:

:::image type="content" alt-text="Upload حزمة جديدة." source="Media/Upload-New-Package.png" lightbox="Media/Upload-New-Package.png":::

بعد ذلك، اتبع الخطوات أدناه لتحميل حزمة جديدة.

## <a name="enter-details-for-your-package"></a>إدخال تفاصيل الحزمة

على علامة التبويب تفاصيل الاختبار، اكتب اسم الحزمة والإصدار والتفاصيل الأخرى كما هو المطلوب.

**يمكن إجراء اختبار "** خارج الصندوق" و"الوظائف" عبر لوحة المعلومات هذه.

توفر الخطوات أدناه دليلا حول كيفية تعبئة تفاصيل الحزمة:

1. أدخل الاسم الذي تريد إعطاءه للحزمة الخاصة بك في `Package name` الحقل.

    > [!NOTE]
    > يجب أن يكون اسم الحزمة ومزيج الإصدار الذي تم إدخاله فريدين داخل مؤسستك. يتم التحقق من صحة ذلك بواسطة علامة الاختيار كما هو موضح أدناه.

    - إذا اخترت إعادة استخدام اسم حزمة، فيجب أن يكون رقم الإصدار فريدا (أي أنه لم يتم استخدامه أبدا مع حزمة تحمل هذا الاسم الخاص).

    - إذا لم تجتاز تركيبة اسم الحزمة + الإصدار عملية التحقق من التفرد، سترى رسالة خطأ تظهر "حزمة مع هذا الإصدار من الحزمة *موجودة بالفعل".*

    :::image type="content" alt-text="صورة لتحميل إرشادات الحزمة." source="Media/Instructions.png":::

2. أدخل إصدارا في الحقل "إصدار الحزمة".

    :::image type="content" alt-text="إصدار الحزمة." source="Media/ApplicationVersion.png":::

3. حدد نوع الاختبار الذي تريد تشغيله على هذه الحزمة.

    يقوم اختبار "خارج المربع" **(OOB)** بإجراء عملية تثبيت الحزمة الخاصة بك، و تشغيلها *، و* إغلاقها، و *إلغاء* تثبيتها. بعد التثبيت، يتم تكرار روتين إغلاق التشغيل 30 مرة قبل تشغيل إلغاء تثبيت واحد.

    يوفر لك اختبار OOB هذا بيانات قياس بيانات قياسية على الحزمة لمقارنتها عبر Windows البيانات.

    من **شأن الاختبار الوظيفي** تنفيذ البرنامج النصي (البرامج النصية) الاختبارية التي تم تحميلها على الحزمة. يتم تشغيل البرامج النصية في تسلسل التحميل وسيتوقف الفشل في برنامج نصي معين عن تنفيذ البرامج النصية التالية.

    > [!NOTE]
    > **يتم** تشغيل كل البرامج النصية لمدة 80 دقيقة على الأكثر.

4. حدد نوع تحديث نظام التشغيل.

    - تمكن 'تحديثات الأمان' حزمتك من اختبارها مقابل Windows تحديثات الأمان الشهرية قبل الإصدار.
    - تمكن 'تحديثات الميزات' حزمتك من اختبارها مقابل Windows الإصدار نصف السنوي من إصدارات الميزات من Windows Insider.
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="نوع تحديث نظام التشغيل." source="Media/OSUpdateType.png":::

5. حدد إصدار (إصدارات) نظام التشغيل لاختبارات تحديث الأمان.

    في المنسدلة تحديد متعدد، حدد إصدار (إصدارات) نظام التشغيل Windows تثبيت الحزمة على.

    - لاختبار الحزمة فقط مقابل Windows تشغيل العميل، حدد الإصدارات القابلة للتطبيق Windows نظام تشغيل العميل من قائمة القوائم.
    - لاختبار الحزمة فقط مقابل Windows تشغيل الخادم، حدد الإصدارات القابلة للتطبيق Windows Os Server من قائمة القوائم.
    - لاختبار الحزمة مقابل Windows العميل Windows Server، حدد كل أنظمة التشغيل القابلة للتطبيق من قائمة القوائم.

    > [!NOTE]
    > إذا قمت بتحديد اختبار الحزمة مقابل كل من خوادم OSes والعميل، فالرجاء التأكد من أن الحزمة متوافقة ويمكن تشغيلها على كل من OSes

    :::image type="content" alt-text="تحديد إصدار نظام تشغيل." source="Media/OSVersion.png":::
    <!---
    Change to the correct picture
    -->

6. حدد خيارات لاختبارات تحديث الميزة:

    - في خيار "تحديد قناة Insider"، `Windows Insider Program Channel` حدد كبنية يجب اختبار حزمك مقابلها.

      نستخدم حاليا الإصدارات التي تم إصدارها في قناة الإصدار بيتا ل Insider.

    - في الخيار "تحديد أساس نظام التشغيل ل Insight"، حدد Windows نظام التشغيل الذي سيتم استخدامه كخط أساسي في مقارنة نتائج الاختبار.

    > [!NOTE]
    > نحن لا ندعم اختبار تحديث الميزات لم OSes للخادم في هذا الوقت
    <!---
    Note to actual note format for markdown
    -->
    <!---
    Change to the correct picture
    -->
    :::image type="content" alt-text="اختبار تحديث الميزات." source="Media/FeatureUpdate.png":::

7. يجب أن تبدو صفحة تفاصيل الاختبار المكتملة كما يلي:

    :::image type="content" alt-text="عرض تفاصيل الاختبار." source="Media/TestDetails.png":::

## <a name="next-steps"></a>الخطوات التالية

تغطي المقالة التالية تحميل الثنائيات إلى خدمتنا.

> [!div class="nextstepaction"]
> [الخطوة التالية](binaries.md)

<!---
Add button for next page
-->
