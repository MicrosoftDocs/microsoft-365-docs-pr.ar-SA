---
title: حماية بيانات مؤسستك باستخدام التحكم في الجهاز
description: مراقبة أمان بيانات مؤسستك من خلال تقارير التحكم في الجهاز.
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
ms.openlocfilehash: 6fe93be2ec244628f2bf2195eb453307235ea06f
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129174"
---
# <a name="device-control-report"></a>تقرير التحكم في الجهاز

**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender لنقطة النهاية يحمي التحكم في الجهاز من فقدان البيانات من خلال مراقبة استخدام الوسائط والتحكم فيه من قبل الأجهزة في مؤسستك، مثل استخدام أجهزة التخزين القابلة للإزالة ومحركات أقراص USB.

باستخدام تقرير التحكم في الجهاز، يمكنك عرض الأحداث المتعلقة باستخدام الوسائط. وتشمل هذه الأحداث ما يلي:

- **أحداث التدقيق:** إظهار عدد أحداث التدقيق التي تحدث عند اتصال الوسائط الخارجية.
- **أحداث النهج:** إظهار عدد أحداث النهج التي تحدث عند تشغيل نهج التحكم في الجهاز.

> [!NOTE]
> يتم تمكين حدث التدقيق لتعقب استخدام الوسائط بشكل افتراضي للأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية.

## <a name="understanding-the-audit-events"></a>فهم أحداث التدقيق

تتضمن أحداث التدقيق ما يلي:

- **تحميل محرك أقراص USB وإلغاء التحميل:** تدقيق الأحداث التي يتم إنشاؤها عند تحميل محرك أقراص USB أو إلغاء تحميله.
- **PnP:** يتم إنشاء أحداث تدقيق أجهزة التوصيل و التشغيل عند توصيل تخزين قابل للإزالة أو طابعة أو وسائط Bluetooth.
- **التحكم في الوصول إلى التخزين القابل للإزالة:** يتم إنشاء الأحداث عند تشغيل نهج التحكم في الوصول إلى التخزين القابل للإزالة. يمكن أن يكون التدقيق أو الحظر أو السماح.

## <a name="monitor-device-control-security"></a>مراقبة أمان التحكم في الجهاز

يعمل التحكم في الجهاز في Defender لنقطة النهاية على تمكين مسؤولي الأمان من خلال الأدوات التي تمكنهم من تعقب أمان التحكم في الأجهزة في مؤسستهم من خلال التقارير. يمكنك العثور على تقرير التحكم في الجهاز في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). انتقل إلى **تقرير الأمان** **العام** >  **للتقارير** > . ابحث عن بطاقة **التحكم في الجهاز** ، وحدد الارتباط لفتح التقرير. 

تعرض بطاقة حماية الجهاز على لوحة معلومات **التقارير** عدد أحداث التدقيق التي تم إنشاؤها بواسطة نوع الوسائط، على مدى آخر 180 يوما.

يعرض الزر **"عرض التفاصيل** " المزيد من بيانات استخدام الوسائط في صفحة **تقرير عنصر تحكم الجهاز** .

توفر الصفحة لوحة معلومات تحتوي على عدد مجمع من الأحداث لكل نوع وقائمة أحداث وتعرض 500 حدث لكل صفحة، ولكن يمكن للمسؤولين التمرير لأسفل لرؤية المزيد من الأحداث ويمكنهم التصفية حسب النطاق الزمني واسم فئة الوسائط ومعرف الجهاز.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Detaileddevicecontrolreport.png" alt-text="صفحة تفاصيل تقرير عنصر التحكم في الجهاز في مدخل Microsoft 365 Defender" lightbox="images/Detaileddevicecontrolreport.png":::

عند تحديد حدث، تظهر قائمة منبثقة تعرض لك المزيد من المعلومات:

- **التفاصيل العامة:** التاريخ ووضع الإجراء والنهج والوصول إلى هذا الحدث.
- **معلومات الوسائط:** تتضمن معلومات الوسائط اسم الوسائط واسم الفئة والمعرف الفريد العمومي للفئة ومعرف الجهاز ومعرف المورد والرقم التسلسلي ونوع الناقل.
- **تفاصيل الموقع:** اسم الجهاز والمستخدم ومعرف جهاز MDATP.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/devicecontrolreportfilter.png" alt-text="عامل التصفية على صفحة تقرير عنصر تحكم الجهاز" lightbox="images/devicecontrolreportfilter.png":::

لمشاهدة نشاط في الوقت الحقيقي لهذه الوسائط عبر المؤسسة، حدد الزر **"فتح التتبع المتقدم** ". يتضمن ذلك استعلاما مضمنا ومحددا مسبقا.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicecontrolreportquery.png" alt-text="الاستعلام على صفحة تقرير عنصر تحكم الجهاز" lightbox="images/Devicecontrolreportquery.png":::

للاطلاع على أمان الجهاز، حدد زر **"فتح صفحة الجهاز** " في القائمة المنبثقة. يفتح هذا الزر صفحة كيان الجهاز.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/Devicesecuritypage.png" alt-text="صفحة كيان الجهاز" lightbox="images/Devicesecuritypage.png":::

## <a name="reporting-delays"></a>الإبلاغ عن التأخيرات

قد يكون هناك تأخير يصل إلى 12 ساعة من وقت حدوث اتصال وسائط إلى الوقت الذي يظهر فيه الحدث في البطاقة أو في قائمة المجالات.
