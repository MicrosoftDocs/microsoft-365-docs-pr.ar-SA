---
title: تقرير سلامة الجهاز وتوافقه في Microsoft Defender لنقطة النهاية
description: تعقب اكتشافات حالة صحة الجهاز وحالة الحماية من الفيروسات والنظام الأساسي لنظام التشغيل وإصدارات Windows 10 باستخدام تقرير سلامة الجهاز والامتثال
keywords: حالة الصحة، برنامج الحماية من الفيروسات، نظام التشغيل الأساسي، إصدار windows 10، الإصدار، الصحة، التوافق، الحالة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 50c7a6a4563e8231d28b11144347ca0fb1de46a9
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418193"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>تقرير سلامة الجهاز وتوافقه في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender 

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل
- Mac OS
- ينكس
- دائره الرقابه الداخليه
- الروبوت

هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يوفر تقرير حالة الأجهزة معلومات عالية المستوى حول الأجهزة في مؤسستك. يتضمن التقرير معلومات اتجاهية تظهر حالة حالة جهاز الاستشعار وحالة الحماية من الفيروسات والأنظمة الأساسية لنظام التشغيل وإصدارات Windows 10 (Windows 11).

يتم تنظيم لوحة المعلومات في قسمين:

:::image type="content" source="images/device-reports.png" alt-text="تقرير الجهاز" lightbox="images/device-reports.png":::


<br>

****

|قسم|الوصف|
|---|---|
|1|اتجاهات الجهاز|
|2|ملخص الجهاز (اليوم الحالي)|
|||

## <a name="device-trends"></a>اتجاهات الجهاز

بشكل افتراضي، تعرض اتجاهات الجهاز معلومات الجهاز من فترة 30 يوما التي تنتهي في اليوم الكامل الأخير. للحصول على منظور أفضل للاتجاهات التي تحدث في مؤسستك، يمكنك ضبط فترة إعداد التقارير عن طريق ضبط الفترة الزمنية المعروضة. لضبط الفترة الزمنية، حدد نطاقا زمنيا من الخيارات المنسدلة:

- 30 يوماً
- ثلاثة شهور
- ستة أشهر
- المخصصه

> [!NOTE]
> يتم تطبيق عوامل التصفية هذه فقط على قسم اتجاهات الجهاز. لا يؤثر على قسم ملخص الجهاز.

## <a name="device-summary"></a>ملخص الجهاز

في حين أن اتجاهات الأجهزة تعرض معلومات الجهاز المتداولة، يعرض ملخص الجهاز معلومات الجهاز التي تم تحديد نطاقها إلى اليوم الحالي.

> [!NOTE]
> يتم تحديد نطاق البيانات التي تظهر في قسم الملخص إلى 180 يوما قبل التاريخ الحالي. على سبيل المثال، إذا كان تاريخ اليوم هو 27 مارس 2019، فستعكس البيانات الموجودة في قسم الملخص الأرقام بدءا من 28 سبتمبر 2018 إلى 27 مارس 2019.
>
> لا يتم تطبيق عامل التصفية المطبق على قسم الاتجاهات على قسم الملخص.

يسمح لك قسم اتجاهات الجهاز بالتنقل لأسفل إلى قائمة الأجهزة مع تطبيق عامل التصفية المطابق عليه. على سبيل المثال، سيؤدي النقر فوق الشريط "غير نشط" في بطاقة حالة حماية جهاز الاستشعار إلى إحضار قائمة الأجهزة مع نتائج تعرض فقط الأجهزة التي تكون حالة جهاز الاستشعار الخاصة بها غير نشطة.

## <a name="device-attributes"></a>سمات الجهاز

يتكون التقرير من بطاقات تعرض سمات الجهاز التالية:

- **الحالة الصحية**: تعرض معلومات حول حالة جهاز الاستشعار على الأجهزة، وتوفر طريقة عرض مجمعة للأجهزة النشطة، أو التي تواجه ضعف الاتصالات، أو غير نشطة، أو حيث لا يتم رؤية بيانات جهاز الاستشعار.
- **حالة مكافحة الفيروسات لأجهزة Windows 10 النشطة**: تعرض عدد الأجهزة وحالة برنامج الحماية من الفيروسات من Microsoft Defender.
- **أنظمة نظام التشغيل الأساسية**: تظهر توزيع أنظمة نظام التشغيل الأساسية الموجودة داخل مؤسستك.
- **Windows 10 الإصدارات**: يعرض توزيع أجهزة Windows 10 وإصداراتها في مؤسستك.

## <a name="filter-data"></a>تصفية البيانات

استخدم عوامل التصفية المتوفرة لتضمين أجهزة ذات سمات معينة أو استبعادها.

يمكنك تحديد عوامل تصفية متعددة لتطبيقها من سمات الجهاز.

> [!NOTE]
> تنطبق عوامل التصفية هذه على **جميع** البطاقات في التقرير.

على سبيل المثال، لإظهار بيانات حول أجهزة Windows 10 مع حالة حماية أداة الاستشعار النشطة:

1. ضمن **عوامل التصفية > حالة حماية المستشعر > نشط**.
2. ثم حدد **الأنظمة الأساسية لنظام التشغيل > Windows 10**.
3. حدد **Apply**.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-topic"></a>الموضوع ذو الصلة

- [تقرير الحماية من التهديدات](threat-protection-reports.md)
