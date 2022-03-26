---
title: تعيين وقت المخزن المؤقت في Microsoft Bookings
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 271f43e4-b8f7-4d63-8059-b5747679bb7e
description: قم بتعيين وقت المخزن المؤقت قبل الموعد أو بعده في Microsoft Bookings للسماح بتنظيف المعدات أو إعادة تعيينها.
ms.openlocfilehash: a33159b0b5f168bbb61c88bc9b4181e05c8abbb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569662"
---
# <a name="set-buffer-time-in-microsoft-bookings"></a>تعيين وقت المخزن المؤقت في Microsoft Bookings

قد تتطلب بعض مواعيدك وقتا قبل الاجتماع مع العميل أو بعده لإعداد الغرفة والمعدات أو تنظيفها أو إعادة تعيينها. أو إذا كنت في وضع التنقل بين مواعيد العملاء، فقد تحتاج إلى الوقت للتأكد من أنه يمكنك أنت وفريقك التنقل بين المواعيد دون جعل العميل ينتظر.

يمكنك تعيين وقت المخزن المؤقت قبل بدء المواعيد أو بعد انتهاء المواعيد أو كليهما لإعطاء الموظفين الوقت الإضافي الذي يحتاجونه للتحضير لموعدهم التالي.

## <a name="set-buffer-time-defaults"></a>تعيين الإعدادات الافتراضية للوقت المؤقت

يتم تعيين الإعدادات الافتراضية للوقت المؤقت على صفحة **تفاصيل الخدمة** في Bookings. مثل كل الإعدادات الافتراضية للخدمة التي تم تعيينها على هذه الصفحة، يمكن تحرير هذه الإعدادات الافتراضية من قبلك لحجز معين لتلبية احتياجات العملاء المحددة.

يمكن العثور على إعداد وقت المخزن المؤقت أسفل منتقيات المدة الافتراضية في **صفحة تفاصيل** الخدمة. قبل أن تتمكن من تعيينه لخدمة معينة، يجب تمكين إعداد وقت المخزن المؤقت عن طريق تحديد تبديل وقت المخزن المؤقت. يؤدي هذا إلى ظهور  المسقطتين قبل وبعد، والتي يتم استخدامها لاختيار الفترة الزمنية الافتراضية التي يجب الاحتفاظ بها قبل كل حجز وبعده، كما هو موضح هنا:

   ![صورة Bookings مع تمكين وقت المخزن المؤقت.](../media/bookings-buffertime.png)

<!--## Buffer time and appointment timing

To avoid confusion about when customers expect to meet with you, Bookings shows buffer time and actual appointment time (the time your customers expect to meet with you) on your calendar, and in email confirmations and reminders to relevant staff. For example, below is what you’d see in Bookings for an appointment with a customer that includes 15 minutes of pre-appointment buffer time.

Note that the event itself (on the left in the image below) shows lighter shading for the buffer time and darker shading for the actual customer appointment. The appointment call-out (which is opened when you select the event) specifically states that the appointment is from 9:00AM to 10:00AM with Katie Jordan and includes 15 minutes of buffer time before the appointment and 0 minutes after the appointment. Confirmations and reminders to staff similarly reference specific buffer and appointment time while the customer would only get confirmations and reminders that reference a 9:00AM to 10:00AM appointment time.

   ![Image of Bookings appointment call-out with buffer time showing.](../media/bookings-buffertime-callout.png)
-->

## <a name="buffer-time-and-availability"></a>وقت المخزن المؤقت وتوفره

لا يرى عملاؤك بشكل مباشر الأوقات التي قمت بتعيينها ولا يمكنهم تغييرها. ومع ذلك، نظرا لأنه يتم استخدام وقت المخزن المؤقت لحساب مدة الخدمة الإجمالية، سيشاهد العملاء أنت والموظفين ذوي الصلة كما تم حجزهم أثناء كل من المخزن المؤقت ومواعيد الموعد العادية. يرى العملاء أيضا التوفر لك ولالموظفين فقط إذا كان هناك وقت كاف لكل من الموعد والوقت المؤقت الخاص به.

على سبيل المثال، يتطلب الموعد لمدة ساعة واحدة مع فترة تخزين مؤقت لمدة 15 دقيقة قبل الموعد فترة زمنية متوفرة من ساعة واحدة و15 دقيقة على الأقل. وبالتالي، فإن تعيين موعد لهذه الخدمة سيملأ فترة زمنية 75 دقيقة في التقويم ويحتاج إلى 75 دقيقة من التوفر للحجز دون تعارض.
