---
title: إجراءات المعالجة في Microsoft 365 Defender
description: احصل على نظرة عامة على إجراءات المعالجة التي تتبع التحقيقات التلقائية في Microsoft 365 Defender
keywords: تلقائي، تحقيق، تنبيه، مشغل، إجراء، معالجة
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
ms.openlocfilehash: 669d4f3b4e8c2d805f72f9113cea1e9e926f3390
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492349"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>إجراءات المعالجة في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

في أثناء وبعد إجراء تحقيق تلقائي في Microsoft 365 Defender، يتم تحديد إجراءات المعالجة للعناصر الضارة أو المشبوهة. يتم اتخاذ بعض أنواع إجراءات المعالجة على الأجهزة، ويشار إليها أيضا بنقاط النهاية. يتم اتخاذ إجراءات معالجة أخرى على الهويات والحسابات ومحتوى البريد الإلكتروني. تكتمل التحقيقات التلقائية بعد اتخاذ إجراءات المعالجة أو الموافقة عليها أو رفضها.

> [!IMPORTANT]
> يعتمد ما إذا كانت إجراءات المعالجة يتم اتخاذها تلقائيا أو فقط على الموافقة على إعدادات معينة، مثل مستويات التشغيل التلقائي. لمعرفة المزيد، راجع المقالات التالية:
>
> - [تكوين قدرات التحقيق والاستجابة التلقائية في Microsoft 365 Defender](m365d-configure-auto-investigation-response.md)
> - [تكوين حسابات الإجراءات في Microsoft Defender for Identity](/defender-for-identity/manage-action-accounts)
> - [كيفية معالجة التهديدات على الأجهزة](../defender-endpoint/automated-investigations.md)
> - [إجراءات التهديدات والمعالجة على البريد الإلكتروني & محتوى التعاون](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

يلخص الجدول التالي إجراءات المعالجة المعتمدة حاليا في Microsoft 365 Defender.

|إجراءات معالجة الجهاز (نقطة النهاية)  |إجراءات معالجة البريد الإلكتروني  |المستخدمون (الحسابات)  |
|:---------|:---------|----------|
|- جمع حزمة التحقيق <br/>- عزل الجهاز (يمكن التراجع عن هذا الإجراء)<br/>- جهاز Offboard <br/>- تنفيذ التعليمات البرمجية للإصدار <br/>- تحرير من العزل <br/>- نموذج الطلب <br/>- تقييد تنفيذ التعليمات البرمجية (يمكن التراجع عن هذا الإجراء) <br/>- تشغيل فحص مكافحة الفيروسات <br/>- الإيقاف والعزل <br/>- يحتوي على أجهزة من الشبكة     |- حظر URL (وقت النقر)<br/>- حذف مبدئي لرسائل البريد الإلكتروني أو المجموعات<br/>- البريد الإلكتروني للعزل<br/>- عزل مرفق بريد إلكتروني<br/>- إيقاف تشغيل إعادة توجيه البريد الخارجي          |- تعطيل المستخدم<br />- إعادة تعيين كلمة مرور المستخدم<br />- تأكيد تعرض المستخدم للخطر          |

يمكن عرض إجراءات المعالجة، سواء كانت معلقة أو مكتملة بالفعل، في [مركز الصيانة](m365d-action-center.md).

## <a name="remediation-actions-that-follow-automated-investigations"></a>إجراءات المعالجة التي تتبع التحقيقات التلقائية

عند اكتمال التحقيق التلقائي، يتم التوصل إلى حكم لكل قطعة من الأدلة المعنية. اعتمادا على الحكم، يتم تحديد إجراءات المعالجة. في بعض الحالات، يتم اتخاذ إجراءات المعالجة تلقائيا؛ وفي حالات أخرى، تنتظر إجراءات المعالجة الموافقة. كل ذلك يعتمد على كيفية [تكوين التحقيق التلقائي والاستجابة](m365d-configure-auto-investigation-response.md).

يسرد الجدول التالي الأحكام والنتائج المحتملة:

| الحكم    | الكيانات المتأثرة    | نتائج|
|------|------|------|
| الخبيثه    | الأجهزة (نقاط النهاية)    | يتم اتخاذ إجراءات المعالجة تلقائيا (بافتراض تعيين [مجموعات](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) الأجهزة الخاصة بمؤسستك إلى **"كاملة" - معالجة التهديدات تلقائيا**)|
| الخطر | المستخدمون | يتم اتخاذ إجراءات المعالجة تلقائيا |
| الخبيثه    | محتوى البريد الإلكتروني (عناوين URL أو المرفقات) | إجراءات المعالجة الموصى بها معلقة للموافقة|
| المشبوهه    | الأجهزة أو محتوى البريد الإلكتروني | إجراءات المعالجة الموصى بها معلقة للموافقة|
| لم يتم العثور على أي تهديدات    | الأجهزة أو محتوى البريد الإلكتروني    | لا توجد حاجة إلى إجراءات المعالجة|

## <a name="remediation-actions-that-are-taken-manually"></a>إجراءات المعالجة التي يتم اتخاذها يدويا

بالإضافة إلى إجراءات المعالجة التي تتبع التحقيقات التلقائية، يمكن لفريق عمليات الأمان اتخاذ بعض إجراءات المعالجة يدويا. وتتضمن ما يلي:

- إجراء الجهاز اليدوي، مثل عزل الجهاز أو عزل الملفات
- إجراء البريد الإلكتروني اليدوي، مثل حذف رسائل البريد الإلكتروني مبدئيا
- إجراء المستخدم اليدوي، مثل تعطيل المستخدم أو إعادة تعيين كلمة مرور المستخدم
- إجراء [التتبع المتقدم](../defender-endpoint/advanced-hunting-overview.md) على الأجهزة أو المستخدمين أو البريد الإلكتروني
- إجراء [المستكشف](../office-365-security/threat-explorer.md) على محتوى البريد الإلكتروني، مثل نقل البريد الإلكتروني إلى البريد الإلكتروني غير الهام، أو الحذف غير الهام للبريد الإلكتروني، أو الحذف الثابت للبريد الإلكتروني
- إجراء [استجابة مباشرة](/windows/security/threat-protection/microsoft-defender-atp/live-response) يدوي، مثل حذف ملف وإيقاف عملية وإزالة مهمة مجدولة
- إجراء الاستجابة المباشرة باستخدام [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis)، مثل عزل جهاز وتشغيل فحص مكافحة الفيروسات والحصول على معلومات حول ملف

## <a name="next-steps"></a>الخطوات التالية

- [زيارة مركز الصيانة](m365d-action-center.md)
- [عرض إجراءات الإصلاح وإدارتها](m365d-autoir-actions.md)
- [معالجة الإيجابيات الخاطئة أو السلبيات الخاطئة](m365d-autoir-report-false-positives-negatives.md)
- [عزل الأجهزة من الشبكة](../defender-endpoint\respond-machine-alerts.md#contain-devices-from-the-network)
