---
title: الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business
description: عند اكتشاف التهديدات، يمكنك اتخاذ إجراءات للاستجابة لتلك التهديدات وتخفيفها.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f57774f993c0044878655713202d6835a2a69173
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63572099"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

يمكن Microsoft 365 Defender المدخل فريق الأمان من الاستجابة للتهديدات التي تم الكشف عنها وتخفيفها. تعرفك هذه المقالة على مثال حول كيفية استخدام Defender for Business.

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="view-detected-threats"></a>عرض التهديدات التي تم الكشف عنها

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. بطاقات الإشعار على الصفحة الرئيسية. تخبرك البطاقات بنظرة سريعة عن عدد التهديدات التي تم الكشف عنها، إلى جانب عدد حسابات المستخدمين ونقاط النهاية (الأجهزة) والأصول الأخرى التي تأثرت. الصورة التالية هي مثال على البطاقات التي قد تراها:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="لقطة شاشة لرطاقات في مدخل Microsoft 365 Defender":::

3. حدد زرا أو رابطا على البطاقة لعرض مزيد من المعلومات واتخاذ إجراء. على سبيل المثال، تتضمن بطاقة **الأجهزة المعرضة** **للمخاطر زر عرض** التفاصيل. ويأخذنا تحديد هذا الزر **إلى صفحة مخزون** الجهاز، كما هو موضح في الصورة التالية:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="لقطة شاشة لمخزون الأجهزة":::

   **تسرد صفحة مخزون** الجهاز أجهزة الشركة، إلى جانب مستوى المخاطر ومستوى التعرض لها.

4. حدد عنصر، مثل جهاز. يتم فتح جزء القائمة من القائمة flyout ويعرض المزيد من المعلومات حول التنبيهات والحوادث التي تم إنشاؤها لهذا العنصر، كما هو موضح في الصورة التالية:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="لقطة شاشة ل جزء &quot;النشرة flyout&quot; لجهاز محدد":::

5. في القائمة من القائمة flyout، اعرض المعلومات التي يتم عرضها. حدد الشطب (...) لفتح قائمة تسرد الإجراءات المتوفرة، كما هو موضح في الصورة التالية: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="لقطة شاشة للتصرفات المتوفرة لجهاز محدد":::

6. حدد إجراء متوفرا. على سبيل المثال، يمكنك اختيار **تشغيل** فحص الحماية من الفيروسات، مما برنامج الحماية من الفيروسات من Microsoft Defender بدء فحص سريع على الجهاز. أو، يمكنك تحديد **بدء التحقيق التلقائي** لبدء تحقيق تلقائي على الجهاز.

## <a name="next-steps"></a>الخطوات التالية

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)