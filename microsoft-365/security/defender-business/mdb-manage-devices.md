---
title: إدارة الأجهزة في Microsoft Defender for Business
description: تعرف على كيفية إضافة الأجهزة وإزالتها وإدارتها في Defender for Business، وحماية نقطة النهاية للشركات الصغيرة والمتوسطة الحجم.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 735f9e04a9176ce1b6626a050429c0b7323a7c0b
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772916"
---
# <a name="manage-devices-in-microsoft-defender-for-business"></a>إدارة الأجهزة في Microsoft Defender for Business

في Defender for Business، يمكنك إدارة الأجهزة كما يلي:

- [عرض قائمة بالأجهزة التي تم إلحاقها للاطلاع على](#view-the-list-of-onboarded-devices) مستوى المخاطر ومستوى التعرض وحالتها الصحية
- [اتخاذ إجراء على جهاز يحتوي على](#take-action-on-a-device-that-has-threat-detections) عمليات الكشف عن التهديدات
- [إلحاق جهاز ب Defender for Business](#onboard-a-device)  
- [إيقاف تشغيل جهاز من Defender for Business](#offboard-a-device)


## <a name="view-the-list-of-onboarded-devices"></a>عرض قائمة الأجهزة الملحقة

:::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="لقطة شاشة لمخزون الجهاز":::

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **"مخزون الجهاز**".

3. حدد جهازا لفتح لوحة القائمة المنبثقة الخاصة به، حيث يمكنك معرفة المزيد عن حالته واتخاذ إجراء. 

   إذا لم يكن لديك أي أجهزة مدرجة بعد، [فساعد الأجهزة على إلحاق Defender for Business](mdb-onboard-devices.md)

## <a name="take-action-on-a-device-that-has-threat-detections"></a>اتخاذ إجراء على جهاز يحتوي على عمليات الكشف عن التهديدات

:::image type="content" source="../../media/defender-business/mdb-selected-device.png" alt-text="لقطة شاشة لجهاز محدد مع توفر التفاصيل والإجراءات":::

1. في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، اختر **مخزون الجهاز**. 

2. حدد جهازا لفتح لوحة القائمة المنبثقة الخاصة به، وراجع المعلومات المعروضة.

3. حدد علامة الحذف (**...**) لفتح قائمة الإجراءات. 

4. حدد إجراء، مثل **تشغيل فحص مكافحة الفيروسات** أو **بدء التحقيق التلقائي**. 

## <a name="onboard-a-device"></a>إلحاق جهاز

راجع [إلحاق الأجهزة ب Defender for Business](mdb-onboard-devices.md).

## <a name="offboard-a-device"></a>إيقاف تشغيل جهاز

راجع [إزالة إلحاق جهاز](mdb-offboard-devices.md).

## <a name="next-steps"></a>الخطوات التالية

- [عرض الحوادث وإدارتها في Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)
- [إنشاء مجموعات الأجهزة أو تحريرها](mdb-create-edit-device-groups.md)