---
title: مراجعة إجراءات المعالجة في Microsoft 365 Business Premium
description: تعرف على كيفية عرض المعالجة التي تم اتخاذها تلقائيا أو التي تنتظر الموافقة في مركز الصيانة.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 73790afedc78961562b592d1eb4decd4a8f1b0d4
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490388"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>مراجعة إجراءات المعالجة في Microsoft 365 Business Premium

حسنا، لقد اكتشفت خرقا أمنيا، ولكن ماذا تفعل؟ يعتمد ذلك على طبيعة ذلك.

تتضمن أمثلة إجراءات المعالجة إرسال ملف إلى العزل أو إيقاف تشغيل عملية أو إزالة مهمة مجدولة بالكامل. يتم تعقب جميع إجراءات المعالجة في مركز الصيانة، الموجود في [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="لقطة شاشة لمركز الصيانة في M365.":::

**تصف هذه المقالة**:

- [كيفية استخدام مركز الصيانة](#how-to-use-your-action-center)

- [أنواع إجراءات المعالجة](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>كيفية استخدام مركز الصيانة

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **مركز الصيانة**.

3. حدد علامة التبويب **"معلق** " لعرض أي إجراءات معلقة والموافقة عليها (أو رفضها). يمكن أن تنشأ هذه الإجراءات من الحماية من الفيروسات/الحماية من البرامج الضارة أو التحقيقات التلقائية أو أنشطة الاستجابة اليدوية أو جلسات الاستجابة المباشرة.

4. حدد علامة التبويب " **محفوظات** " لعرض قائمة بالإجراءات المكتملة.

## <a name="types-of-remediation-actions"></a>أنواع إجراءات المعالجة

يتضمن اشتراكك عدة أنواع مختلفة من إجراءات المعالجة للتهديدات المكتشفة. تتضمن هذه الإجراءات إجراءات الاستجابة اليدوية، والإجراءات التي تلي التحقيق التلقائي، وإجراءات الاستجابة المباشرة.

يسرد الجدول التالي إجراءات المعالجة المتوفرة:

| مصدر  | الاجراءات  |
|---------|---------|
| [التحقيقات التلقائية](../security/defender-endpoint/automated-investigations.md)      | - عزل ملف <br/>- إزالة مفتاح التسجيل <br/>- إنهاء عملية <br/>- إيقاف خدمة <br/>- تعطيل برنامج تشغيل <br/>- إزالة مهمة مجدولة        |
| [إجراءات الاستجابة اليدوية](../security/defender-endpoint/respond-machine-alerts.md)   | - تشغيل فحص مكافحة الفيروسات <br/>- عزل الجهاز <br/>- الإيقاف والعزل <br/>- إضافة مؤشر لحظر ملف أو السماح به       |
| [الاستجابة المباشرة](../security/defender-endpoint/live-response.md)   | - جمع البيانات الجنائية <br/>- تحليل ملف <br/>- تشغيل برنامج نصي <br/>- إرسال كيان مريب إلى Microsoft للتحليل <br/>- معالجة ملف <br/>- البحث بشكل استباقي عن التهديدات         |
