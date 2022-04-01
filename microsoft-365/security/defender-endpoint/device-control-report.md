---
title: حماية بيانات مؤسستك باستخدام التحكم في الجهاز
description: راقب أمان البيانات في مؤسستك من خلال تقارير التحكم في الجهاز.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: deniseb
author: denisebmsft
ms.reviewer: dansimp
ms.topic: article
manager: dansimp
audience: ITPro
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 8a31ce05ed6986159d9f6e4c489e6f7707cfecc4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465278"
---
# <a name="device-control-report"></a>تقرير التحكم في الجهاز

**ينطبق على:** 
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender لنقطة النهاية التحكم في الجهاز من فقدان البيانات، من خلال مراقبة استخدام الوسائط والتحكم فيها بواسطة الأجهزة في مؤسستك، مثل استخدام أجهزة التخزين القابلة للإزالة ومحركات أقراص USB.

باستخدام تقرير التحكم في الجهاز، يمكنك عرض الأحداث المتعلقة باستخدام الوسائط، مثل:

- **أحداث التدقيق:** إظهار عدد أحداث التدقيق التي تحدث عند اتصال الوسائط الخارجية.
- **أحداث النهج:** إظهار عدد أحداث النهج التي تحدث عند تشغيل نهج التحكم في الجهاز.

> [!NOTE]
> يتم تمكين حدث التدقيق لتعقب استخدام الوسائط بشكل افتراضي للأجهزة المجهزة Microsoft Defender لنقطة النهاية.

## <a name="understanding-the-audit-events"></a>فهم أحداث التدقيق

تتضمن أحداث التدقيق ما يلي:

- **تحميل محرك أقراص USB و إلغاء الفرز:** تدقيق الأحداث التي يتم إنشاؤها عند تثبيت محرك أقراص USB أو إلغاء تثبيته.
- **PnP: أجهزة التوصيل و التشغيل** إنشاء أحداث التدقيق عند توصيل السعة التخزينية القابلة للإزالة أو الطابعة أو Bluetooth الوسائط.
- **عنصر تحكم الوصول إلى التخزين القابل للإزالة:** يتم إنشاء الأحداث عند تشغيل نهج التحكم بالوصول إلى التخزين القابل للإزالة. يمكن أن يكون تدقيق أو حظر أو السماح.

## <a name="monitor-device-control-security"></a>مراقبة أمان التحكم في الجهاز

يعمل التحكم في Microsoft Defender لنقطة النهاية على تمكين مسؤولي الأمان باستخدام الأدوات التي تمكنهم من تعقب أمان التحكم في جهاز المؤسسة من خلال التقارير. يمكنك العثور على تقرير التحكم في الجهاز في Microsoft 365 Defender من خلال الذهاب إلى **تقارير > حماية الجهاز**.

تعرض بطاقة حماية الجهاز على لوحة  معلومات التقارير عدد أحداث التدقيق التي تم إنشاؤها بواسطة نوع الوسائط، على مدار آخر 180 يوما.

> [!div class="mx-imgBorder"]
> ![DeviceControlReportCard](https://user-images.githubusercontent.com/81826151/138504137-e9a7673e-e988-48cd-820d-2625ec6df352.png)

يعرض **الزر عرض التفاصيل** المزيد من بيانات استخدام الوسائط في **صفحة تقرير التحكم في** الجهاز.

توفر الصفحة لوحة معلومات تحتوي على عدد مجمع من الأحداث لكل نوع وقائمة أحداث. يمكن للمسؤولين التصفية على النطاق الزمني واسم فئة الوسائط وم ID الجهاز.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="صفحة تفاصيل تقرير التحكم في الجهاز في مدخل Microsoft 365 Defender" lightbox="images/Detaileddevicecontrolreport.png":::

عندما تحدد حدثا، تظهر من خلال منير تعرض لك المزيد من المعلومات:

- **التفاصيل العامة:** التاريخ ووضع الإجراء ون نهج هذا الحدث والوصول إليه.
- **معلومات الوسائط:** تتضمن معلومات الوسائط اسم الوسائط واسم الفئة وD GUID للصف و"معرِّف الجهاز" و"مورد" و"الرقم التسلسلي" و"نوع الحافلة".
- **تفاصيل الموقع:** اسم الجهاز والمستخدم وم id جهاز MDATP.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="صفحة &quot;عامل التصفية على تقرير التحكم في الجهاز&quot;" lightbox="images/devicecontrolreportfilter.png":::

لرؤية نشاط الوقت الحقيقي لهذه الوسائط عبر المؤسسة، حدد الزر **فتح البحث** المتقدم. يشمل ذلك استعلاما مضمنا معرفا مسبقا.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="صفحة الاستعلام على تقرير التحكم في الجهاز" lightbox="images/Devicecontrolreportquery.png":::

لمشاهدة أمان الجهاز، حدد الزر **فتح صفحة الجهاز** على منتحل المعلومات. يفتح هذا الزر صفحة كيان الجهاز.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="صفحة كيان الجهاز" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>تأخيرات إعداد التقارير

يمكن أن يحدث تأخير لمدة 12 ساعة في تقرير التحكم في الجهاز من وقت حدوث اتصال وسائط إلى الوقت الذي يظهر فيه الحدث في البطاقة أو في قائمة المجالات.
