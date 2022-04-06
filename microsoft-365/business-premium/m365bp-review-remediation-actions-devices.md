---
title: مراجعة إجراءات المعالجة في Microsoft 365 Business Premium
description: تعرف على كيفية عرض المعالجة التي تم اتخاذها تلقائيا أو التي تنتظر الموافقة في مركز الإجراءات
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
ms.openlocfilehash: 160cef2ec7691fbc9debad809b20461a0d3efe23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705533"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>مراجعة إجراءات المعالجة في Microsoft 365 Business Premium

مع اكتشاف التهديدات، يتم تشغيل إجراءات المعالجة. وفقا للتهديدات الخاصة وكيفية تكوين إعدادات الأمان، قد يتم اتخاذ إجراءات المعالجة تلقائيا أو عند الموافقة فقط. تتضمن أمثلة إجراءات الإصلاح إرسال ملف إلى الفحص، وتوقف عملية من التشغيل، وإزالة مهمة مجدولة. يتم تعقب جميع إجراءات الإصلاح في مركز الإجراءات، الموجود في [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center).

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="لقطة شاشة لمركز الإجراءات في M365.":::

**تصف هذه المقالة**:

- [كيفية استخدام مركز الإجراءات](#how-to-use-your-action-center)

- [أنواع إجراءات المعالجة](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>كيفية استخدام مركز الإجراءات

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول.

2. في جزء التنقل، اختر **مركز الإجراءات**.

3. حدد علامة **التبويب معلق** لعرض (أو رفض) أي إجراءات معلقة والموافقة عليها. يمكن أن تنشأ مثل هذه الإجراءات من الحماية من الفيروسات/الحماية من البرامج الضارة أو عمليات التحقيق التلقائية أو أنشطة الاستجابة اليدوية أو جلسات الاستجابة المباشرة.

4. حدد علامة **التبويب** محفوظات لعرض قائمة الإجراءات المكتملة. 

## <a name="types-of-remediation-actions"></a>أنواع إجراءات المعالجة

يتضمن اشتراكك عدة أنواع مختلفة من إجراءات المعالجة للتهديدات التي تم الكشف عنها. تتضمن هذه الإجراءات إجراءات الاستجابة اليدوية والإجراءات التالية للتحري التلقائي والإجراءات المباشرة للاستجابة.

يسرد الجدول التالي إجراءات الإصلاح المتوفرة:

| المصدر  | الإجراءات  |
|---------|---------|
| [عمليات التحقيق التلقائية](../security/defender-endpoint/automated-investigations.md)      | - عزل ملف <br/>- إزالة مفتاح تسجيل <br/>- اقتل عملية <br/>- إيقاف خدمة <br/>- تعطيل برنامج تشغيل <br/>- إزالة مهمة مجدولة        |
| [إجراءات الاستجابة اليدوية](../security/defender-endpoint/respond-machine-alerts.md)   | - تشغيل مسح الحماية من الفيروسات <br/>- عزل الجهاز <br/>- إيقاف وفحص <br/>- إضافة مؤشر لحظر ملف أو السماح به       |
| [الاستجابة المباشرة](../security/defender-endpoint/live-response.md)   | - تجميع بيانات الطب الشرعي <br/>- تحليل ملف <br/>- تشغيل برنامج نصي <br/>- إرسال كيان مريب إلى Microsoft لتحليله <br/>- إعادة وسائط ملف <br/>- البحث بشكل استباقي عن التهديدات         |
