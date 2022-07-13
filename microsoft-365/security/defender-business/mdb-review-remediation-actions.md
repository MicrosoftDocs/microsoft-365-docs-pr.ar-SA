---
title: مراجعة إجراءات المعالجة في Microsoft Defender for Business
description: عرض المعالجة التي تم اتخاذها على التهديدات المكتشفة باستخدام Defender for Business. يمكنك عرض الإجراءات في مركز الصيانة في مدخل Microsoft 365 Defender.
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
ms.openlocfilehash: 63bbeb218693174402264bb59a6c014e63e14bef
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66770966"
---
# <a name="review-remediation-actions-in-the-action-center"></a>مراجعة إجراءات المعالجة في مركز الصيانة

ومع اكتشاف التهديدات، يتم تشغيل إجراءات المعالجة. اعتمادا على التهديد المعين وكيفية تكوين إعدادات الأمان الخاصة بك، قد يتم اتخاذ إجراءات المعالجة تلقائيا أو فقط بناء على الموافقة. تتضمن أمثلة إجراءات المعالجة ما يلي: 
- إرسال ملف إلى العزل
- إيقاف تشغيل عملية
- إزالة مهمة مجدولة

يتم تعقب جميع إجراءات المعالجة في مركز الصيانة.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="لقطة شاشة لمركز الصيانة":::

**تصف هذه المقالة**:

- [كيفية استخدام مركز الصيانة](#how-to-use-the-action-center)
- [إجراءات المعالجة](#remediation-actions)


## <a name="how-to-use-the-action-center"></a>كيفية استخدام مركز الصيانة

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **مركز الصيانة**.

3. حدد علامة التبويب **"معلق** " لعرض أي إجراءات معلقة والموافقة عليها (أو رفضها). يمكن أن تنشأ الإجراءات من الحماية من الفيروسات/الحماية من البرامج الضارة، أو التحقيقات التلقائية، أو أنشطة الاستجابة اليدوية، أو جلسات الاستجابة المباشرة.

4. حدد علامة التبويب " **محفوظات** " لعرض قائمة بالإجراءات المكتملة.

## <a name="remediation-actions"></a>إجراءات المعالجة

يتضمن Defender for Business العديد من إجراءات المعالجة. تتضمن هذه الإجراءات إجراءات الاستجابة اليدوية، والإجراءات التي تلي التحقيق التلقائي، وإجراءات الاستجابة المباشرة.

يسرد الجدول التالي إجراءات المعالجة المتوفرة.

| مصدر  | الاجراءات  |
|---------|---------|
| [التحقيقات التلقائية](../defender-endpoint/automated-investigations.md)      |<ul><li>عزل ملف</li><li>إزالة مفتاح تسجيل</li><li>إنهاء عملية</li><li>إيقاف خدمة</li><li>تعطيل برنامج تشغيل</li><li>إزالة مهمة مجدولة </li></ul> |
| [إجراءات الاستجابة اليدوية](../defender-endpoint/respond-machine-alerts.md)   |<ul><li>تشغيل مسح الحماية من الفيروسات</li><li>عزل جهاز</li><li>الإيقاف والعزل</li><li>إضافة مؤشر لحظر ملف أو السماح به</li></ul> |
| [الاستجابة المباشرة](../defender-endpoint/live-response.md)   |<ul><li>جمع البيانات الجنائية</li><li>تحليل ملف</li><li>تشغيل برنامج نصي</li><li>إرسال كيان مريب إلى Microsoft للتحليل</li><li>معالجة ملف </li><li>البحث الاستباقي عن التهديدات</li></ul>|

## <a name="next-steps"></a>الخطوات التالية

- [الاستجابة للتهديدات وتخفيفها في Defender for Business](mdb-respond-mitigate-threats.md)
- [إدارة الأجهزة في Defender for Business](mdb-manage-devices.md)
