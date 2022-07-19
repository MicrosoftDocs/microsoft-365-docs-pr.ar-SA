---
title: ضبط تفضيلات الجدولة ل Scheduler لنظرة عامة على Microsoft 365
ms.author: shivb
author: shivbijlani
manager: charlle
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: تعرف على كيفية ضبط تفضيلات الجدولة ل Scheduler ل Microsoft 365.
ms.openlocfilehash: e6b6f4426b173bced90fcc8f2a705bc3e48cd09e
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/07/2022
ms.locfileid: "66857373"
---
# <a name="scheduling-preferences-used-by-scheduler"></a>تفضيلات الجدولة المستخدمة من قبل Scheduler

يستخدم Scheduler العديد من تفضيلات Outlook لجدولة اجتماع لمنظم. ستؤثر أي تغييرات على إعدادات التفضيلات في عملاء Outlook على كيفية معالجة Scheduler للطلبات المرسلة إلى Cortana. على سبيل المثال، إذا قام أحد المنظمين بتغيير تفضيل المنطقة الزمنية على صفحة الإعدادات في Outlook Web، فستتم افتراضيا كافة الطلبات من قبل المنظم الذي يليه إلى المنطقة الزمنية الجديدة.

## <a name="supported-settings"></a>الإعدادات المدعومة

- **المنطقة الزمنية**. يستخدم مجدول المنطقة الزمنية لتحديد الوقت المناسب للاجتماعات. راجع [إضافة مناطق زمنية أو إزالتها أو تغييرها](https://support.microsoft.com/en-us/office/add-remove-or-change-time-zones-5ab3e10e-5a6c-46af-ab48-156fedf70c04) للحصول على معلومات.

- **ساعات العمل وأيامه**. بالنسبة لمعظم أنواع الاجتماعات، يحدد Scheduler وقتا وفقا لتفضيلات أسبوع العمل وساعات الاجتماع الخاصة بالمنظم. راجع [تغيير ساعات العمل والأيام في Outlook](https://support.microsoft.com/en-us/office/change-your-work-hours-and-days-in-outlook-a27f261d-0681-415f-8ac1-388ab21e833f) للحصول على معلومات.

- **الاجتماعات عبر الإنترنت**. يمكنك تشغيل خيار "التقويم" بحيث يتم عقد كل الاجتماعات التي تقوم بجدولتها من Outlook و Scheduler عبر الإنترنت باستخدام تفاصيل المؤتمر. يدعم Scheduler حاليا Teams وSkype كموفري اجتماعات. راجع [إنشاء كل اجتماعات Teams](https://support.microsoft.com/en-us/office/schedule-a-teams-meeting-from-outlook-883cc15c-580f-441a-92ea-0992c00a9b0f#bkmk_makeallteamsmtngs) للحصول على معلومات.

- **مدة الاجتماع الافتراضية**. إذا لم يحدد المنظم مدة الاجتماع المطلوبة في الطلب، فسيستخدم Scheduler مدة الاجتماع المفضلة للطلب. يتوفر هذا الإعداد فقط في عميل Windows Outlook.

   1. حدد **"خيارات** **الملف** > " لعرض مربع الحوار "خيارات Outlook".

   2. حدد **"التقويم"** من القائمة الموجودة على يمين مربع الحوار.

   3. في إعدادات خيارات التقويم على يمين مربع الحوار، حدد **المدة الافتراضية للمواعيد والاجتماعات الجديدة**.

      :::image type="content" source="../media/OutlookOptions.png" alt-text="تقويم Outlook مربع حوار الخيارات في Windows حيث يمكنك إعداد وقت العمل ومدة الاجتماع الافتراضية وتحديد تقصير الاجتماعات لاستخدام Scheduler.":::

- **تجنب الاجتماعات من الخلف إلى الخلف**. يمكن لإعداد Outlook بدء الاجتماعات في وقت متأخر أو إنهاء الاجتماعات في وقت مبكر لتجنب الاجتماعات من الخلف إلى الخلف. كما يمكن ل Scheduler تقصير مدة الاجتماع وفقا للتفضيلات التي قمت بتعيينها. راجع [تغيير طول الاجتماع الافتراضي](https://techcommunity.microsoft.com/t5/hybrid-work/change-default-meeting-length-in-outlook-avoid-back-to-back/m-p/1247361) للحصول على معلومات.

> [!NOTE]
> إذا كنت تستخدم عميل Windows، فيجب تحديد **"تخزين إعدادات Outlook" في السحابة** لمزامنة تفضيلاتك عبر Scheduler وعملاء Outlook الآخرين.
> :::image type="content" source="../media/OutlookOptions2.png" alt-text="مربع حوار خيارات تقويم Outlook في Windows. حدد &quot;تخزين إعدادات Outlook&quot; في السحابة لمزامنة تفضيلات الجدولة عبر العملاء.":::
