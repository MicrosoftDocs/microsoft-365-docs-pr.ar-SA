---
title: إدارة الأجهزة في Microsoft Defender for Business
description: تعرف على كيفية إدارة الأجهزة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f47e72b3651b4a86eed4001fc51f051f47e2f3c7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63572103"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>إدارة الأجهزة في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

في Microsoft Defender for Business، يمكنك إدارة الأجهزة كما يلي:

- [عرض قائمة بالأجهزة المجهزة](#view-the-list-of-onboarded-devices) لمشاهدة مستوى المخاطر ومستوى التعرض للضوء فيها وصحتها

- [اتخاذ إجراء على جهاز](#take-action-on-a-device-that-has-threat-detections) به أجهزة الكشف عن المخاطر

- [ا متن جهاز إلى Defender for Business](#onboard-a-device)  

- [إيقاف تشغيل جهاز من Defender for Business](#offboard-a-device)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="view-the-list-of-onboarded-devices"></a>عرض قائمة الأجهزة المجهزة

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="لقطة شاشة لمخزون الأجهزة":::

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. في جزء التنقل، اختر **مخزون الجهاز**.

3. حدد جهازا لفتح لوحة منتهية، حيث يمكنك معرفة المزيد حول حالة الجهاز واتخاذ إجراء. 

   إذا لم يكن لديك أي أجهزة مدرجة بعد، الأجهزة [المجهزة على Microsoft Defender for Business](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>اتخاذ إجراء على جهاز به أجهزة الكشف عن المخاطر

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="لقطة شاشة لجهاز محدد مع تفاصيل والإجراءات المتوفرة":::

1. في Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، اختر **مخزون الجهاز**. 

2. حدد جهازا لفتح لوحة القائمة flyout الخاصة به، وراجع المعلومات التي يتم عرضها.

3. حدد البقصاصة (**...**) لفتح قائمة الإجراءات. 

4. حدد إجراء، مثل **تشغيل مسح الحماية من الفيروسات** أو **بدء التحقيق التلقائي**. 

## <a name="onboard-a-device"></a>االلوح بجهاز

راجع [الأجهزة المجهزة ل Microsoft Defender for Business](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>إيقاف تشغيل جهاز

راجع [إيقاف تشغيل جهاز](mdb-onboard-devices.md#offboarding-a-device).

## <a name="next-steps"></a>الخطوات التالية

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)

- [إنشاء مجموعات الأجهزة أو تحريرها](mdb-create-edit-device-groups.md)