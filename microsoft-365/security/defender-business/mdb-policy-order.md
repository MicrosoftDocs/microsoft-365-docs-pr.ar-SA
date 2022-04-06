---
title: فهم ترتيب النهج في Microsoft Defender for Business
description: تعرف على ترتيب الأولوية مع النهج في Microsoft Defender for Business
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
ms.openlocfilehash: 13e803666cc7af14af52031eb86a2f86edf06f80
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666295"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>فهم ترتيب النهج في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business [للعملاء Microsoft 365 Business Premium](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم معاينة Defender for Business باعتباره اشتراكا مستقلا، وسيتم طرحه تدريجيا للعملاء وشركاء تكنولوجيا المعلومات الذين [يقومون بالتسجيل هنا](https://aka.ms/mdb-preview) لطلبه. تتضمن المعاينة [مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بانتظام.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالنواتج/الخدمات التي تم إصدارها مسبقا والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المقدمة هنا. 

## <a name="policy-order-in-microsoft-defender-for-business"></a>ترتيب النهج في Microsoft Defender for Business

تتضمن Microsoft Defender for Business نهج معرفة مسبقا للمساعدة في ضمان حماية الأجهزة التي يستخدمها موظفوك. يمكن لفريق الأمان إضافة نهج جديدة أيضا. على سبيل المثال، افترض أنك تريد تطبيق إعدادات معينة على بعض الأجهزة وإعدادات مختلفة على أجهزة أخرى. يمكنك القيام بذلك عن طريق إضافة نهج، مثل نهج الحماية من الجيل التالي أو نهج جدار الحماية.

عند إضافة النهج، ستلاحظ أنه تم تعيين ترتيب الأولوية. يمكنك تحرير ترتيب الأولوية للنهج التي تحددها، ولكن لا يمكنك تغيير ترتيب الأولوية للنهج الافتراضية. على سبيل المثال، افترض أنه بالنسبة لأجهزة عميل Windows لديك، لديك ثلاثة نهج حماية من الجيل التالي. في هذه الحالة، النهج الافتراضي الخاص بك هو رقم 3 في الأولوية. يمكنك تغيير ترتيب النهج التي تم ترقيمها 1 و2، ولكن النهج الافتراضي سيبقى الرقم 3 في قائمتك. 

**الشيء المهم الذي يجب تذكره حول نهج متعددة هو أن الأجهزة ستتلقى النهج المطبق الأول فقط.** بالإشارة إلى مثالنا السابق لثلاثة نهج من الجيل التالي، افترض أن لديك أجهزة مستهدفة من قبل جميع النهج الثلاثة. في هذه الحالة، ستتلقى هذه الأجهزة رقم النهج 1، ولكنها لن تتلقى النهج التي تم ترقيمها 2 و3. 

>
> **هل لديك دقيقة؟**
> يرجى الاطلاع <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">على استطلاعنا القصير حول Microsoft Defender for Business</a>. يسعدنا أن نستمع إليك!
>

## <a name="key-points-to-remember-about-policy-order"></a>النقاط الرئيسية التي يجب تذكرها حول ترتيب النهج

- يتم تعيين ترتيب الأولوية للنهج.

- تتلقى الأجهزة النهج المطبق الأول فقط.

- يمكنك تغيير ترتيب الأولوية للنهج.

- يتم إعطاء النهج الافتراضية أدنى ترتيب من الأولوية.

## <a name="next-steps"></a>الخطوات التالية

- [بدء استخدام Defender for Business](mdb-get-started.md)

- [إدارة الأجهزة](mdb-manage-devices.md)

- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)