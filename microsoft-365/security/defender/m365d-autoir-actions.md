---
title: عرض الإجراءات وإدارتها في مركز الصيانة
description: استخدام مركز الصيانة لعرض إجراءات المعالجة وإدارتها
keywords: إجراء، مركز، تلقائي، تلقائي، تحقيق، استجابة، معالجة
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 43c48081a86e33cd918bc4de8f01859bc1107583
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666823"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>عرض الإجراءات وإدارتها في مركز الصيانة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يمكن أن تؤدي ميزات الحماية من التهديدات في Microsoft 365 Defender إلى إجراءات معالجة معينة. فيما يلي بعض الأمثلة:

- يمكن أن تؤدي [التحقيقات التلقائية](m365d-autoir.md) إلى إجراءات المعالجة التي يتم اتخاذها تلقائيا أو في انتظار موافقتك.
- يمكن أن تؤدي ميزات الحماية من الفيروسات والحماية من البرامج الضارة وغيرها من ميزات الحماية من التهديدات إلى إجراءات المعالجة، مثل حظر ملف أو عنوان URL أو عملية أو إرسال بيانات اصطناعية إلى العزل.
- يمكن لفريق عمليات الأمان اتخاذ إجراءات المعالجة يدويا، مثل أثناء [التتبع المتقدم](advanced-hunting-overview.md) أو أثناء التحقيق في [التنبيهات](investigate-alerts.md) أو [الحوادث](investigate-incidents.md).

> [!NOTE]
> يجب أن يكون لديك [الأذونات المناسبة](m365d-action-center.md#required-permissions-for-action-center-tasks) للموافقة على إجراءات المعالجة أو رفضها. لمزيد من المعلومات، راجع [المتطلبات الأساسية](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>مراجعة الإجراءات المعلقة في مركز الصيانة

من المهم الموافقة على (أو رفض) الإجراءات المعلقة في أقرب وقت ممكن بحيث يمكن متابعة التحقيقات التلقائية وإكمالها في الوقت المناسب. 

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> وسجل الدخول. 

2. في جزء التنقل، اختر **مركز الصيانة**. 

3. في مركز الصيانة، ضمن علامة التبويب **"معلق** "، حدد عنصرا في القائمة. يتم فتح جزء القائمة المنبثقة الخاص به. فيما يلي مثال على ذلك.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="خيارات الموافقة على إجراء أو رفضه" lightbox="../../media/air-actioncenter-itemselected.png":::

4. راجع المعلومات في جزء القائمة المنبثقة، ثم اتخذ إحدى الخطوات التالية:
   - حدد **صفحة فتح التحقيق** لعرض مزيد من التفاصيل حول التحقيق.
   - حدد **"موافقة** " لبدء إجراء معلق.
   - حدد **"رفض** " لمنع اتخاذ إجراء معلق.
   - حدد **Go hunt** للانتقال إلى [التتبع المتقدم](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>التراجع عن الإجراءات المكتملة

إذا حددت أن جهازا أو ملفا ليس تهديدا، يمكنك التراجع عن إجراءات المعالجة التي تم اتخاذها، سواء تم اتخاذ هذه الإجراءات تلقائيا أو يدويا. في مركز الصيانة، على علامة التبويب " **محفوظات** "، يمكنك التراجع عن أي من الإجراءات التالية:  

| مصدر الإجراء | الإجراءات المدعومة |
|:---|:---|
| - التحقيق التلقائي <br/>- برنامج الحماية من الفيروسات من Microsoft Defender <br/>- إجراءات الاستجابة اليدوية | - عزل الجهاز <br/>- تقييد تنفيذ التعليمات البرمجية <br/>- عزل ملف <br/>- إزالة مفتاح التسجيل <br/>- إيقاف خدمة <br/>- تعطيل برنامج تشغيل <br/>- إزالة مهمة مجدولة |

### <a name="undo-one-remediation-action"></a>التراجع عن إجراء معالجة واحد

1. انتقل إلى مركز الصيانة ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) وسجل الدخول.

2. في علامة التبويب " **محفوظات** "، حدد إجراء تريد التراجع عنه.

3. في الجزء الموجود على الجانب الأيسر من الشاشة، حدد **"تراجع".**

### <a name="undo-multiple-remediation-actions"></a>التراجع عن إجراءات المعالجة المتعددة

1. انتقل إلى مركز الصيانة (https://security.microsoft.com/action-center) وسجل الدخول.

2. في علامة التبويب " **محفوظات** "، حدد الإجراءات التي تريد التراجع عنها. تأكد من تحديد العناصر التي لها نفس نوع الإجراء. يتم فتح جزء قائمة منبثقة.

3. في جزء القائمة المنبثقة، حدد **"تراجع**".

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>لإزالة ملف من العزل عبر أجهزة متعددة 

1. انتقل إلى مركز الصيانة ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) وسجل الدخول.

2. في علامة التبويب " **محفوظات** "، حدد ملفا يحتوي على نوع **إجراء ملف العزل** .

3. في الجزء الموجود على الجانب الأيسر من الشاشة، حدد **تطبيق على X المزيد من مثيلات هذا الملف**، ثم حدد **"تراجع".**

## <a name="next-steps"></a>الخطوات التالية

- [عرض تفاصيل ونتائج التحقيق التلقائي](m365d-autoir-results.md)
- [معالجة الإيجابيات الخاطئة أو السلبيات الخاطئة](m365d-autoir-report-false-positives-negatives.md)
