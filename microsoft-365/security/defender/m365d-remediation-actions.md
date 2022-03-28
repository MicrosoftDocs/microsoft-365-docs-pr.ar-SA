---
title: إجراءات المعالجة في Microsoft 365 Defender
description: احصل على نظرة عامة حول إجراءات الإصلاح التي تتبع عمليات التحقيق التلقائية في Microsoft 365 Defender
keywords: تلقائي، التحقيق، التنبيه، المشغل، الإجراء، المعالجة
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
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: c922213a262fdc9c61d6f79d0205e6ead96fd44a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575809"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>إجراءات المعالجة في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

أثناء إجراء تحقيق تلقائي في Microsoft 365 Defender، يتم تحديد إجراءات المعالجة لعناصر ضارة أو مريبة. يتم اتخاذ بعض أنواع إجراءات الإصلاح على الأجهزة، يشار إليها أيضا بنقاط النهاية. يتم اتخاذ إجراءات إصلاح أخرى على محتوى البريد الإلكتروني. تكتمل عمليات التحقيق التلقائية بعد اتخاذ إجراءات المعالجة أو الموافقة عليها أو رفضها.

> [!IMPORTANT]
> تعتمد إجراءات المعالجة التي يتم اتخاذها تلقائيا أو عند الموافقة فقط على إعدادات معينة، مثل كيفية مستويات التنفيذ التلقائي. لمعرفة المزيد، راجع المقالات التالية:
> - [تكوين قدرات الاستجابة والتحري التلقائية في Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [كيفية معالجة التهديدات على الأجهزة](../defender-endpoint/automated-investigations.md)
> - [التهديدات والإجراءات الإصلاحية على البريد & محتوى التعاون](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

يلخص الجدول التالي إجراءات المعالجة المعتمدة حاليا في Microsoft 365 Defender. 

|إجراءات إصلاح الجهاز (نقطة النهاية)  |إجراءات إصلاح البريد الإلكتروني  |
|:---------|:---------|
|- تجميع حزمة التحقيق <br/>- عزل الجهاز (يمكن التراجع عن هذا الإجراء)<br/>- جهاز Offboard <br/>- تنفيذ رمز الإصدار <br/>- تحرير من الفحص <br/>- نموذج الطلب <br/>- تقييد تنفيذ التعليمات البرمجية (يمكن التراجع عن هذا الإجراء) <br/>- تشغيل مسح الحماية من الفيروسات <br/>- إيقاف وفحص      |- حظر URL (وقت النقر)<br/>- حذف رسائل البريد الإلكتروني أو المجموعات بشكل غير مهين<br/>- عزل البريد الإلكتروني<br/>- عزل مرفق بريد إلكتروني<br/>- إيقاف تشغيل إعادة توجيه البريد الخارجي          |

يمكن عرض إجراءات الإصلاح، سواء كانت موافقة معلقة أو مكتملة بالفعل، في [مركز الإجراءات](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>إجراءات المعالجة التي تتبع عمليات التحقيق التلقائية

عند اكتمال التحقيق التلقائي، يتم الوصول إلى قرار لكل قطعة من الإثباتات. وفقا للحكم، يتم تحديد إجراءات الإصلاح. في بعض الحالات، يتم اتخاذ إجراءات المعالجة تلقائيا؛ في حالات أخرى، تنتظر إجراءات المعالجة الموافقة. يعتمد كل ذلك على كيفية [تكوين الاستجابة والتحري التلقائي](m365d-configure-auto-investigation-response.md).

يسرد الجدول التالي الأحكام والنتائج المحتملة:

| الحكم    | الكيانات المتأثرة    | النتائج|
|------|------|------|
| ضار    | الأجهزة (نقاط النهاية)    | يتم اتخاذ إجراءات المعالجة تلقائيا (مع افتراض تعيين مجموعات الأجهزة في مؤسستك إلى [](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) كامل - تهديدات المعالجة **تلقائيا**)|
| ضار    | محتوى البريد الإلكتروني (عناوين URL أو المرفقات) | إجراءات الإصلاح الموصى بها معلقة للموافقة|
| مريبا    | الأجهزة أو محتوى البريد الإلكتروني | إجراءات الإصلاح الموصى بها معلقة للموافقة|
| لم يتم العثور على أي تهديدات    | الأجهزة أو محتوى البريد الإلكتروني    | لا حاجة إلى أي إجراءات إصلاحية|


## <a name="remediation-actions-that-are-taken-manually"></a>إجراءات المعالجة التي يتم اتخاذها يدويا

بالإضافة إلى إجراءات الإصلاح التي تتبع عمليات التحقيق التلقائية، يمكن لفريق عمليات الأمان اتخاذ إجراءات إصلاح معينة يدويا. وتتضمن ما يلي:

- إجراء يدوي على الجهاز، مثل عزل الجهاز أو عزل الملفات
- إجراء البريد الإلكتروني اليدوي، مثل حذف رسائل البريد الإلكتروني بشكل تلقائي 
- [إجراء متقدم للصيد](../defender-endpoint/advanced-hunting-overview.md) على الأجهزة أو البريد الإلكتروني
- [إجراء المستكشف](../office-365-security/threat-explorer.md) على محتوى البريد الإلكتروني، مثل نقل البريد الإلكتروني إلى البريد الإلكتروني غير الهام أو حذف البريد الإلكتروني بشكل تلقائي أو حذفه بشكل نهائي
- إجراء [الاستجابة المباشرة](/windows/security/threat-protection/microsoft-defender-atp/live-response) اليدوية، مثل حذف ملف، أو إيقاف عملية، أو إزالة مهمة مجدولة
- إجراء استجابة مباشرة باستخدام [Microsoft Defender ل واجهات](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis) برمجة تطبيقات نقطة النهاية، مثل عزل جهاز وتشغيل فحص الحماية من الفيروسات والحصول على معلومات حول ملف

## <a name="next-steps"></a>الخطوات التالية

- [زيارة مركز الإجراءات](m365d-action-center.md)
- [عرض إجراءات الإصلاح وإدارتها](m365d-autoir-actions.md)
- [عنوان الموجبة الخاطئة أو السلبيات الخاطئة](m365d-autoir-report-false-positives-negatives.md)
