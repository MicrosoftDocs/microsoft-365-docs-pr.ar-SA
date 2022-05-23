---
title: تعيين وقت المخزن المؤقت Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: قم بتعيين وقت المخزن المؤقت قبل الموعد أو بعده في Microsoft Bookings للسماح بالوقت لتنظيف المعدات أو إعادة تعيينها.
ms.openlocfilehash: 49e58d53cec466c824a40281e3199f1544e74744
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637572"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>تعيين وقت المخزن المؤقت في Microsoft Bookings

قد تتطلب بعض مواعيدك وقتا قبل أو بعد الاجتماع مع العميل لإعداد الغرفة والأجهزة أو تنظيفها أو إعادة تعيينها. أو إذا كنت على الطريق بين مواعيد العملاء، فقد تحتاج إلى وقت لضمان إمكانية التنقل بين المواعيد مع فريقك دون انتظار العميل.

يمكنك تعيين وقت المخزن المؤقت قبل بدء المواعيد أو بعد انتهاء المواعيد أو كليهما لمنح الموظفين الوقت الإضافي الذي يحتاجونه للتحضير لموعدهم التالي.

## <a name="set-buffer-time-defaults"></a>تعيين إعدادات وقت المخزن المؤقت الافتراضية

يتم تعيين الإعدادات الافتراضية لوقت المخزن المؤقت على صفحة **تفاصيل الخدمة** في Bookings. مثل جميع إعدادات الخدمة الافتراضية المعينة على هذه الصفحة، يمكن تحرير هذه الإعدادات الافتراضية من قبلك لحجز معين لتلبية احتياجات العملاء المحددة.

يمكن العثور على إعداد وقت المخزن المؤقت في صفحة **تفاصيل الخدمة** . قبل أن تتمكن من تعيينه لخدمة معينة، يجب تمكين إعداد وقت المخزن المؤقت عن طريق تحديد تبديل وقت المخزن المؤقت. يؤدي هذا إلى ظهور القائمة المنسدلة **"قبل** " و" **بعد** "، والتي يتم استخدامها لاختيار مقدار الوقت الافتراضي للاحتفاظ به قبل وبعد كل حجز، كما هو موضح هنا:

   ![صورة Bookings مع تمكين وقت المخزن المؤقت.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>وقت المخزن المؤقت والتوافر

لا يرى عملاؤك بشكل مباشر ولا يمكنهم تغيير أوقات المخزن المؤقت التي قمت بتعيينها. ومع ذلك، نظرا لاستخدام وقت المخزن المؤقت لحساب المدة الإجمالية للخدمة، سيرى العملاء أنت والموظفين المعنيين كما تم حجزهم خلال أوقات المواعيد المؤقتة والمواعيد العادية. كما لا يرى العملاء أيضا توفرا لك ولموظفيك إلا إذا كان هناك وقت كاف للموعد ووقت المخزن المؤقت الخاص به.

على سبيل المثال، يتطلب الموعد لمدة ساعة واحدة مع وقت مؤقت قبل الموعد مدته 15 دقيقة كتلة زمنية متوفرة مدتها ساعة واحدة و15 دقيقة على الأقل. لذلك، فإن موعد هذه الخدمة سيملأ فترة زمنية مدتها 75 دقيقة في التقويم ويحتاج إلى 75 دقيقة من التوفر للحجز دون تعارض.
