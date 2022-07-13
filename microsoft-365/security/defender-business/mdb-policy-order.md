---
title: فهم ترتيب النهج في Microsoft Defender for Business
description: تعرف على ترتيب الأولوية مع نهج الأمان عبر الإنترنت لحماية أجهزة شركتك باستخدام Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 361a1a08569f24c83498fddeb0e4c2b9bd8c5d02
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770866"
---
# <a name="understand-policy-order-in-microsoft-defender-for-business"></a>فهم ترتيب النهج في Microsoft Defender for Business

## <a name="policy-order-in-defender-for-business"></a>ترتيب النهج في Defender for Business

يتضمن Defender for Business نهج معرفة مسبقا للمساعدة في ضمان حماية الأجهزة التي يستخدمها موظفوك. يمكن لفريق الأمان إضافة نهج جديدة أيضا. على سبيل المثال، افترض أنك تريد تطبيق إعدادات معينة على بعض الأجهزة وإعدادات مختلفة على أجهزة أخرى. يمكنك القيام بذلك عن طريق إضافة نهج، مثل نهج الحماية من الجيل التالي أو نهج جدار الحماية.

عند إضافة النهج، ستلاحظ أنه تم تعيين ترتيب الأولوية. يمكنك تحرير ترتيب الأولوية للنهج التي تحددها، ولكن لا يمكنك تغيير ترتيب الأولوية للنهج الافتراضية. على سبيل المثال، افترض أنه بالنسبة إلى أجهزة عميل Windows لديك، لديك ثلاثة نهج حماية من الجيل التالي. في هذه الحالة، النهج الافتراضي الخاص بك هو رقم 3 في الأولوية. يمكنك تغيير ترتيب النهج التي تم ترقيمها 1 و2، ولكن النهج الافتراضي سيبقى الرقم 3 في قائمتك. 

**الشيء المهم الذي يجب تذكره حول نهج متعددة هو أن الأجهزة ستتلقى النهج المطبق الأول فقط.** بالإشارة إلى مثالنا السابق لثلاثة نهج من الجيل التالي، افترض أن لديك أجهزة مستهدفة من قبل جميع النهج الثلاثة. في هذه الحالة، ستتلقى هذه الأجهزة رقم النهج 1، ولكنها لن تتلقى النهج التي تم ترقيمها 2 و3. 


## <a name="key-points-to-remember-about-policy-order"></a>النقاط الرئيسية التي يجب تذكرها حول ترتيب النهج

- يتم تعيين ترتيب الأولوية للنهج.
- تتلقى الأجهزة النهج المطبق الأول فقط.
- يمكنك تغيير ترتيب الأولوية للنهج.
- يتم إعطاء النهج الافتراضية أدنى ترتيب من الأولوية.

## <a name="next-steps"></a>الخطوات التالية

- [بدء استخدام Defender for Business](mdb-get-started.md)
- [إدارة الأجهزة](mdb-manage-devices.md)
- [عرض الحوادث وإدارتها في Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)