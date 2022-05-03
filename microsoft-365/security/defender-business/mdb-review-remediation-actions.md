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
ms.openlocfilehash: 438d43548b4318499c44aea65399a7d5a3a5f43d
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174373"
---
# <a name="review-remediation-actions-in-the-action-center"></a>مراجعة إجراءات المعالجة في مركز الصيانة

ومع اكتشاف التهديدات، يتم تشغيل إجراءات المعالجة. اعتمادا على التهديد المعين وكيفية تكوين إعدادات الأمان الخاصة بك، قد يتم اتخاذ إجراءات المعالجة تلقائيا أو فقط بناء على الموافقة. تتضمن أمثلة إجراءات المعالجة إرسال ملف إلى العزل، وإيقاف تشغيل عملية، وإزالة مهمة مجدولة. يتم تعقب جميع إجراءات المعالجة في مركز الصيانة.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="لقطة شاشة لمركز الصيانة":::

**تصف هذه المقالة**:

- [كيفية استخدام مركز الصيانة](#how-to-use-the-action-center)
- [إجراءات المعالجة](#remediation-actions)

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="how-to-use-the-action-center"></a>كيفية استخدام مركز الصيانة

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **مركز الصيانة**.

3. حدد علامة التبويب **"معلق** " لعرض أي إجراءات معلقة والموافقة عليها (أو رفضها). يمكن أن تنشأ هذه الإجراءات من الحماية من الفيروسات/الحماية من البرامج الضارة أو التحقيقات التلقائية أو أنشطة الاستجابة اليدوية أو جلسات الاستجابة المباشرة.

4. حدد علامة التبويب " **محفوظات** " لعرض قائمة بالإجراءات المكتملة. 

## <a name="remediation-actions"></a>إجراءات المعالجة

تتضمن Microsoft Defender for Business العديد من إجراءات المعالجة. تتضمن هذه الإجراءات إجراءات الاستجابة اليدوية، والإجراءات التي تلي التحقيق التلقائي، وإجراءات الاستجابة المباشرة.

يسرد الجدول التالي إجراءات المعالجة المتوفرة:

| مصدر  | الاجراءات  |
|---------|---------|
| [التحقيقات التلقائية](../defender-endpoint/automated-investigations.md)      | - عزل ملف <br/>- إزالة مفتاح التسجيل <br/>- إنهاء عملية <br/>- إيقاف خدمة <br/>- تعطيل برنامج تشغيل <br/>- إزالة مهمة مجدولة        |
| [إجراءات الاستجابة اليدوية](../defender-endpoint/respond-machine-alerts.md)   | - تشغيل فحص مكافحة الفيروسات <br/>- عزل الجهاز <br/>- الإيقاف والعزل <br/>- إضافة مؤشر لحظر ملف أو السماح به       |
| [الاستجابة المباشرة](../defender-endpoint/live-response.md)   | - جمع البيانات الجنائية <br/>- تحليل ملف <br/>- تشغيل برنامج نصي <br/>- إرسال كيان مريب إلى Microsoft للتحليل <br/>- معالجة ملف <br/>- البحث بشكل استباقي عن التهديدات         |

## <a name="next-steps"></a>الخطوات التالية

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)
- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)