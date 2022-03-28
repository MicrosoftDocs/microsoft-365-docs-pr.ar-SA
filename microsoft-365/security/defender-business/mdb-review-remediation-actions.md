---
title: مراجعة إجراءات المعالجة في Microsoft Defender for Business
description: عرض المعالجة التي تم اتخاذها تلقائيا أو التي تنتظر الموافقة في مركز الإجراءات
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/10/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b5bb61d4a0b8f3cb0732633463fbf2c96ec258e9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575948"
---
# <a name="review-remediation-actions-in-the-action-center"></a>مراجعة إجراءات المعالجة في مركز الإجراءات

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

مع اكتشاف التهديدات، يتم تشغيل إجراءات المعالجة. وفقا للتهديدات الخاصة وكيفية تكوين إعدادات الأمان، قد يتم اتخاذ إجراءات المعالجة تلقائيا أو عند الموافقة فقط. تتضمن أمثلة إجراءات الإصلاح إرسال ملف إلى الفحص، وتوقف عملية من التشغيل، وإزالة مهمة مجدولة. يتم تعقب جميع إجراءات المعالجة في مركز الإجراءات.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="لقطة شاشة لمركز الإجراءات":::

**تصف هذه المقالة**:

- [كيفية استخدام مركز الإجراءات](#how-to-use-the-action-center)

- [إجراءات المعالجة](#remediation-actions)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="how-to-use-the-action-center"></a>كيفية استخدام مركز الإجراءات

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول.

2. في جزء التنقل، اختر **مركز الإجراءات**.

3. حدد علامة **التبويب معلق** لعرض (أو رفض) أي إجراءات معلقة والموافقة عليها. يمكن أن تنشأ مثل هذه الإجراءات من الحماية من الفيروسات/الحماية من البرامج الضارة أو عمليات التحقيق التلقائية أو أنشطة الاستجابة اليدوية أو جلسات الاستجابة المباشرة.

4. حدد علامة **التبويب** محفوظات لعرض قائمة الإجراءات المكتملة. 

## <a name="remediation-actions"></a>إجراءات المعالجة

يتضمن Microsoft Defender for Business العديد من إجراءات المعالجة. تتضمن هذه الإجراءات إجراءات الاستجابة اليدوية والإجراءات التالية للتحري التلقائي والإجراءات المباشرة للاستجابة.

يسرد الجدول التالي إجراءات الإصلاح المتوفرة:

| المصدر  | الإجراءات  |
|---------|---------|
| [عمليات التحقيق التلقائية](../defender-endpoint/automated-investigations.md)      | - عزل ملف <br/>- إزالة مفتاح تسجيل <br/>- اقتل عملية <br/>- إيقاف خدمة <br/>- تعطيل برنامج تشغيل <br/>- إزالة مهمة مجدولة        |
| [إجراءات الاستجابة اليدوية](../defender-endpoint/respond-machine-alerts.md)   | - تشغيل مسح الحماية من الفيروسات <br/>- عزل الجهاز <br/>- إيقاف وفحص <br/>- إضافة مؤشر لحظر ملف أو السماح به       |
| [الاستجابة المباشرة](../defender-endpoint/live-response.md)   | - تجميع بيانات الطب الشرعي <br/>- تحليل ملف <br/>- تشغيل برنامج نصي <br/>- إرسال كيان مريب إلى Microsoft لتحليله <br/>- إعادة وسائط ملف <br/>- البحث بشكل استباقي عن التهديدات         |

## <a name="next-steps"></a>الخطوات التالية

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)