---
title: التقارير في Microsoft Defender for Business
description: الحصول على نظرة عامة حول التقارير المتوفرة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 68b5c15b69c1f485bb9ed90bab06c2ceaa2978d9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583775"
---
# <a name="reports-in-microsoft-defender-for-business"></a>التقارير في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

تتوفر عدة تقارير في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). تصف هذه المقالة هذه التقارير، وكيفية استخدامها، وكيفية العثور عليها.

<br/><br/>

## <a name="reports-in-defender-for-business"></a>التقارير في Defender for Business

|تقرير  |الوصف  |
|---------|---------|
| **تقرير الأمان**  | يوفر تقرير الأمان معلومات حول هويات الشركة وأجهزتها وتطبيقاتها. للوصول إلى هذا التقرير، في جزء التنقل، اختر **تقرير ReportsGeneralSecurity** >  > . <br/><br/>**تلميح** يمكنك عرض معلومات مماثلة على الصفحة الرئيسية لمدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). |
| **الحماية من المخاطر**  | يوفر تقرير الحماية من المخاطر معلومات حول التنبيهات واتجاهات التنبيهات. استخدم العمود **اتجاهات التنبيه** لعرض معلومات حول التنبيهات التي تم تشغيلها على مدار آخر 30 يوما. استخدم عمود **حالة** التنبيه لعرض معلومات اللقطة الحالية حول التنبيهات، مثل فئات التنبيهات التي لم يتم حلها وتصنيفها. للوصول إلى هذا التقرير، في جزء التنقل، اختر **ReportsEndpointsThreat** >  >  **protection**. <br/><br/>**تلميح**: يمكنك أيضا **استخدام القائمة "** أحداث" لعرض معلومات حول التنبيهات. في جزء التنقل، اختر **أحداث** لعرض الأحداث الحالية وإدارتها. لمعرفة المزيد، راجع [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md). |
| **صحة الجهاز وتوافقه** | يوفر تقرير حماية الجهاز وتوافقه معلومات حول حماية الجهاز واتجاهاته. يمكنك استخدام هذا التقرير لتحديد ما إذا كانت أدوات استشعار Defender for Business تعمل بشكل صحيح على الأجهزة وعلى الحالة الحالية برنامج الحماية من الفيروسات من Microsoft Defender. للوصول إلى هذا التقرير، في جزء التنقل، اختر **ReportsEndpointsDevice** >  >  **health and compliance**. <br/><br/>**تلميح**: يمكنك **استخدام قائمة مخزون** الجهاز لعرض معلومات حول أجهزة الشركة. في جزء التنقل، اختر **مخزون الجهاز**. لمعرفة المزيد، راجع [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md). |
| **الأجهزة المعرضة** | يوفر تقرير الأجهزة المعرضة للخطر معلومات حول الأجهزة والاتجاهات. استخدم العمود **الاتجاهات** لعرض معلومات حول الأجهزة التي كانت بها تنبيهات على مدار آخر 30 يوما. استخدم عمود **الحالة** لعرض معلومات اللقطة الحالية حول الأجهزة التي بها تنبيهات. للوصول إلى هذا التقرير، في جزء التنقل، اختر **أجهزة** ReportsEndpointsVulnerable >  > .<br/><br/>**تلميح**: يمكنك **استخدام قائمة مخزون** الجهاز لعرض معلومات حول أجهزة الشركة. في جزء التنقل، اختر **مخزون الجهاز**. لمعرفة المزيد، راجع [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md). |
| **حماية ويب** | يعرض تقرير حماية الويب محاولات الوصول إلى مواقع التصيد الاحتيالي، و متجهات البرامج الضارة، والمواقع المستغلة، والمواقع غير الملوثة أو ذات السمعة المنخفضة، والمواقع المحظورة بشكل صريح. تتضمن فئات المواقع المحظورة محتوى البالغين والمواقع الترفيهية ومواقع المسؤولية القانونية والمزيد. للوصول إلى هذا التقرير، في جزء التنقل، اختر **ReportsEndpointsWeb** >  >  **protection**.<br/><br/>**تلميح**: إذا لم تكن قد قمت بعد بتكوين حماية ويب للشركة، **فاختر** زر الإعدادات في طريقة عرض التقرير. بعد ذلك **، ضمن قواعد**، اختر **تصفية محتوى ويب**. لمعرفة المزيد حول تصفية محتوى الويب، راجع [تصفية محتوى ويب](../defender-endpoint/web-content-filtering.md). |

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="see-also"></a>راجع أيضًا

- [بدء استخدام Microsoft Defender for Business](mdb-get-started.md)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)