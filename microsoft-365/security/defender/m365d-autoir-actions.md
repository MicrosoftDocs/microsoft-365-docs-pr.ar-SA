---
title: عرض الإجراءات وإدارتها في مركز الإجراءات
description: استخدام مركز الإجراءات لعرض إجراءات المعالجة وإدارتها
keywords: الإجراء، المركز، الهاتف التلقائي، تلقائي، التحقيق، الاستجابة، المعالجة
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
ms.openlocfilehash: a77a64e2323cc836df9b19694deb5c32ee877fb8
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500794"
---
# <a name="view-and-manage-actions-in-the-action-center"></a>عرض الإجراءات وإدارتها في مركز الإجراءات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

قد تؤدي ميزات الحماية من Microsoft 365 Defender إلى إجراءات إصلاح معينة. فيما يلي بعض الأمثلة:

- [يمكن أن تؤدي عمليات](m365d-autoir.md) البحث التلقائية إلى إجراءات إصلاح يتم اتخاذها تلقائيا أو بانتظار موافقتك.
- يمكن أن يؤدي برنامج الحماية من الفيروسات والحماية من البرامج الضارة وميزات الحماية من المخاطر الأخرى إلى إجراءات إصلاح، مثل حظر ملف أو URL أو عملية، أو إرسال عملية إصلاح إلى الفحص.
- يمكن لفريق عمليات الأمان اتخاذ إجراءات الإصلاح يدويا، مثل أثناء عمليات البحث المتقدمة أو أثناء [](advanced-hunting-overview.md) التحقق من [التنبيهات](investigate-alerts.md) أو [الأحداث](investigate-incidents.md).

> [!NOTE]
> يجب أن تكون [لديك الأذونات المناسبة](m365d-action-center.md#required-permissions-for-action-center-tasks) للموافقة على إجراءات المعالجة أو رفضها. لمزيد من المعلومات، راجع [المتطلبات الأساسية](m365d-configure-auto-investigation-response.md#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).

## <a name="review-pending-actions-in-the-action-center"></a>مراجعة الإجراءات المعلقة في مركز الإجراءات

من المهم الموافقة على (أو رفض) الإجراءات المعلقة في أسرع وقت ممكن بحيث يمكن متابعة عمليات التحقيق التلقائية وإكمالها في الوقت المناسب. 

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل ثم</a> سجل الدخول. 

2. في جزء التنقل، اختر **مركز الإجراءات**. 

3. في مركز الإجراءات، على علامة **التبويب معلق** ، حدد عنصر في القائمة. يفتح جزء منتفطها. فيما يلي مثال على ذلك.

   :::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="خيارات الموافقة على إجراء أو رفضه" lightbox="../../media/air-actioncenter-itemselected.png":::

4. راجع المعلومات في جزء المعلومات من خلال الجزء الذي يتم التقاطه، ثم قم بوا إحدى الخطوات التالية:
   - حدد **فتح صفحة التحقيق** لعرض مزيد من التفاصيل حول التحقيق.
   - حدد **موافقة** لبدء إجراء معلق.
   - حدد **رفض** لمنع اتخاذ إجراء معلق.
   - حدد **الانتقال إلى البحث** عن [طريق البحث المتقدم](advanced-hunting-overview.md). 

## <a name="undo-completed-actions"></a>التراجع عن الإجراءات المكتملة

إذا حددت أن جهازا أو ملفا لا يشكل خطرا، يمكنك التراجع عن إجراءات المعالجة التي تم اتخاذها، سواء تم اتخاذ هذه الإجراءات تلقائيا أو يدويا. في مركز الإجراءات، على علامة **التبويب محفوظات** ، يمكنك التراجع عن أي من الإجراءات التالية:  

| مصدر الإجراء | الإجراءات المعتمدة |
|:---|:---|
| - إجراء تحقيق تلقائي <br/>- برنامج الحماية من الفيروسات من Microsoft Defender <br/>- إجراءات الاستجابة اليدوية | - عزل الجهاز <br/>- تقييد تنفيذ التعليمات البرمجية <br/>- عزل ملف <br/>- إزالة مفتاح تسجيل <br/>- إيقاف خدمة <br/>- تعطيل برنامج تشغيل <br/>- إزالة مهمة مجدولة |

### <a name="undo-one-remediation-action"></a>التراجع عن إجراء إصلاحي واحد

1. انتقل إلى مركز الإجراءات ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) ثم سجل الدخول.

2. على علامة **التبويب** محفوظات، حدد إجراء تريد التراجع عنه.

3. في الجزء على الجانب الأيسر من الشاشة، حدد **تراجع**.

### <a name="undo-multiple-remediation-actions"></a>التراجع عن إجراءات المعالجة المتعددة

1. انتقل إلى مركز الإجراءات (https://security.microsoft.com/action-center) ثم سجل الدخول.

2. على علامة **التبويب** محفوظات، حدد الإجراءات التي تريد التراجع عنها. تأكد من تحديد العناصر التي لها نفس نوع الإجراء. يفتح جزء منتفط.

3. في جزء منتحل، حدد **تراجع**.

### <a name="to-remove-a-file-from-quarantine-across-multiple-devices"></a>لإزالة ملف من الفحص عبر أجهزة متعددة 

1. انتقل إلى مركز الإجراءات ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) ثم سجل الدخول.

2. على علامة **التبويب** محفوظات، حدد ملفا يحتوي على نوع الإجراء **ملف الفحص** .

3. في الجزء على الجانب الأيسر من الشاشة، حدد **تطبيق على X المزيد من** مثيلات هذا الملف، ثم حدد **تراجع**.

## <a name="next-steps"></a>الخطوات التالية

- [عرض تفاصيل ونتائج التحقيق التلقائي](m365d-autoir-results.md)
- [عنوان الموجبة الخاطئة أو السلبيات الخاطئة](m365d-autoir-report-false-positives-negatives.md)
