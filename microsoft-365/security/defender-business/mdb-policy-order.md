---
title: فهم ترتيب النهج في Microsoft Defender for Business
description: تعرف على ترتيب الأولوية مع السياسات في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 373f3eb821e00f903837f98896ed5dab0588e946
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63580012"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>فهم ترتيب النهج في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>طلب النهج في Microsoft Defender for Business

يتضمن Microsoft Defender for Business سياسات محددة مسبقا للمساعدة على ضمان حماية الأجهزة التي يستخدمها الموظفون. يمكن لفريق الأمان إضافة سياسات جديدة أيضا. على سبيل المثال، افترض أنك تريد تطبيق إعدادات معينة على بعض الأجهزة وإعدادات مختلفة على أجهزة أخرى. يمكنك القيام بذلك عن طريق إضافة سياسات، مثل سياسات حماية الجيل التالي أو سياسات جدار الحماية.

عند إضافة سياسات، ستلاحظ أنه تم تعيين ترتيب الأولوية. يمكنك تحرير ترتيب الأولوية بالنسبة إلى السياسات التي تحددها، ولكن لا يمكنك تغيير ترتيب الأولوية بالنسبة إلى السياسات الافتراضية. على سبيل المثال، لنفترض أنه بالنسبة Windows العميل لديك، لديك ثلاثة من سياسات حماية الجيل التالي. في هذه الحالة، يكون النهج الافتراضي رقم 3 في الأولوية. يمكنك تغيير ترتيب النهج التي تم عددها من 1 إلى 2، ولكن سيظل النهج الافتراضي رقم 3 في القائمة. 

**الشيء المهم الذي يجب تذكره حول النهج المتعددة هو أن الأجهزة ستتلقى النهج المطبق الأول فقط.** عند الإشارة إلى المثال السابق لثلاثة من سياسات الجيل التالي، افترض أن لديك أجهزة مستهدفة بواسطة جميع هذه السياسات الثلاثة. في هذه الحالة، ستتلقى هذه الأجهزة النهج رقم 1، ولكن لن تتلقى النهج التي تم عددها من 2 إلى 3. 

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="key-points-to-remember-about-policy-order"></a>النقاط الأساسية التي يجب تذكرها حول ترتيب النهج

- يتم تعيين ترتيب الأولوية إلى السياسات.

- تتلقى الأجهزة النهج المطبق الأول فقط.

- يمكنك تغيير ترتيب الأولوية بالنسبة إلى السياسات.

- يتم منح السياسات الافتراضية أقل ترتيب من الأولوية.

## <a name="next-steps"></a>الخطوات التالية

- [بدء استخدام Defender for Business](mdb-get-started.md)

- [إدارة الأجهزة](mdb-manage-devices.md)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)