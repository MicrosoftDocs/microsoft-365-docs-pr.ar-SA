---
title: إعداد التقارير وتتبع الرسائل
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: f40253f2-50a1-426e-9979-be74ba74cb61
ms.custom:
- seo-marvel-apr2020
description: في هذه المقالة، ستتعرف على التقارير وأدوات استكشاف الأخطاء وإصلاحها المتوفرة لمسؤولي Microsoft Exchange Online الحماية (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d4f0289054baec0e5bcedf4e9e3d434ab51ef92b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566504"
---
# <a name="reporting-and-message-trace-in-eop"></a>إعداد التقارير وتتبع الرسائل في EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في Microsoft 365 المؤسسات التي بها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، يوفر EOP العديد من التقارير المختلفة التي يمكن أن تساعدك على تحديد الحالة العامة لمنظمتك وصحتها. هناك أيضا أدوات تساعدك على استكشاف أحداث معينة وإصلاحها (مثل رسالة لا تصل إلى المستلمين المقصودين)، بالإضافة إلى تقارير التدقيق للمساعدة في متطلبات التوافق.

## <a name="usage-reports"></a>تقارير الاستخدام

- **Microsoft 365 المجموعات**: عرض معلومات حول عدد Microsoft 365 المجموعات التي تم إنشاؤها أو استخدامها. لمزيد من المعلومات، [راجع Microsoft 365 التقارير في مركز الإدارة - Microsoft 365 المجموعات](../../admin/activity-reports/office-365-groups.md).
- **نشاط البريد** الإلكتروني: عرض معلومات حول عدد الرسائل المرسلة والمستلمة والقراءة في مؤسستك بكاملها، ومن قبل مستخدمين محددين. لمزيد من المعلومات، راجع Microsoft 365 [التقارير في مركز الإدارة - نشاط البريد الإلكتروني](../../admin/activity-reports/email-activity.md).
- **استخدام تطبيق البريد الإلكتروني**: عرض معلومات حول تطبيقات البريد الإلكتروني المستخدمة. يشمل ذلك العدد الإجمالي للاتصالات لكل تطبيق، والإصدارات Outlook التي يتم توصيلها. لمزيد من المعلومات، [راجع Microsoft 365 التقارير في مركز الإدارة - استخدام تطبيقات البريد الإلكتروني](../../admin/activity-reports/email-apps-usage.md).
- **استخدام علبة** البريد: عرض معلومات حول التخزين المستخدم واستهلاك الحصة النسبية وعد العناصر والنشاط الأخير (نشاط إرسال أو قراءة) لعلب البريد. لمزيد من المعلومات، راجع Microsoft 365 [التقارير في مركز الإدارة - استخدام علبة البريد](../../admin/activity-reports/mailbox-usage.md).

## <a name="security-reports-in-the-microsoft-365-defender-portal"></a>تقارير الأمان في مدخل Microsoft 365 Defender

توفر هذه التقارير المحسنة تجربة إعداد تقارير تفاعلية لمسؤولي EOP، تتضمن معلومات ملخصة، والقدرة على التنقل لأسفل للحصول على مزيد من التفاصيل.

- **Defender for Office 365**: عرض معلومات خزينة ارتباطات خزينة المرفقات التي هي جزء من Microsoft Defender Office 365. لمزيد من المعلومات، راجع [عرض Defender Office 365 التقارير في Microsoft 365 Defender المدخل](view-reports-for-mdo.md).
- **EOP**: عرض معلومات حول الكشف عن البرامج الضارة والبريد المنتحل والكشف عن البريد العشوائي وتدفق البريد من مؤسستك وإلجاء منها. لمزيد من المعلومات، راجع [عرض تقارير أمان البريد الإلكتروني في Microsoft 365 Defender الإلكتروني](view-email-security-reports.md).

## <a name="mail-flow-insights-in-the-security--compliance-center"></a>تحليلات تدفق البريد في مركز & الأمان

لمزيد من المعلومات، راجع [تحليلات تدفق البريد في مركز & الأمان](mail-flow-insights-v2.md).

## <a name="custom-reports-using-microsoft-graph"></a>التقارير المخصصة التي تستخدم Microsoft Graph

يمكنك إنشاء تقارير متوفرة في مركز الإدارة برمجيا باستخدام Microsoft Graph. لمزيد من المعلومات، راجع نظرة عامة Graph [Microsoft](/graph/overview) واستخدام تقارير Office 365 [في Microsoft Graph](/graph/api/resources/report).

## <a name="message-trace"></a>تتبع الرسائل

تتبع رسائل البريد الإلكتروني أثناء تنقلها عبر EOP. يمكنك تحديد ما إذا تم تلقي رسالة بريد إلكتروني أو رفضها أو تأجيلها أو تسليمها بواسطة الخدمة. كما تعرض الإجراءات التي تم اتخاذها على الرسالة قبل أن تصل إلى وضعها النهائي.

يمكنك استخدام هذه المعلومات للإجابة على أسئلة المستخدم بطريقة فعالة، استكشاف مشاكل تدفق البريد وإصلاحها، والتحقق من صحة تغييرات النهج، وتخفيف الحاجة إلى الاتصال بالدعم التقني للحصول على المساعدة.

راجع [تتبع الرسائل في Microsoft 365 Defender المدخل](message-trace-scc.md).

## <a name="audit-logging"></a>تسجيل التدقيق

يتعقب التغييرات المعينة التي قام بها المسؤولون في مؤسستك. يمكن أن تساعدك هذه التقارير على استكشاف مشاكل التكوين وإصلاحها أو العثور على سبب مشاكل الأمان أو التوافق. راجع [تقارير التدقيق في Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

## <a name="reporting-and-message-trace-data-availability-and-latency"></a>إعداد التقارير وتعقب الرسائل لتوفر البيانات ومدى زمن زمنها

يصف الجدول التالي الوقت الذي تتوفر فيه بيانات تتبع الرسائل وإعداد تقارير EOP ومدى طولها.

<br>

****

|نوع التقرير|البيانات المتوفرة ل (فترة النظر للخلف)|زمن زمن التأخر|
|---|---|---|
|تقارير ملخص حماية البريد|90 يوما|يتم إكمال تجميع بيانات الرسائل في الغالب في غضون 24-48 ساعة. قد تحدث بعض التغييرات التجميعية التزايدية الثانوية لمدة تصل إلى 5 أيام.|
|تقارير تفاصيل حماية البريد|90 يوما|للحصول على بيانات التفاصيل التي يقل عمرها عن 7 أيام، يجب أن تظهر البيانات في غضون 24 ساعة ولكن قد لا تكون مكتملة حتى 48 ساعة. قد تحدث بعض التغييرات التزايدية البسيطة لمدة تصل إلى 5 أيام. <p> لعرض تقارير التفاصيل للرسائل التي يزيد عمرها عن 7 أيام، قد تستغرق النتائج بضع ساعات.|
|بيانات تتبع الرسائل|90 يوما|عند تشغيل تتبع الرسائل للرسائل التي يقل عمرها عن 7 أيام، يجب أن تظهر الرسائل في غضون 5-30 دقيقة.<p> عند تشغيل تتبع الرسائل للرسائل التي يزيد عمرها عن 7 أيام، قد تستغرق النتائج بضع ساعات.|
|

> [!NOTE]
> إن توفر البيانات و زمن زمن الوصول هو نفسه سواء طلب عبر مركز الإدارة أو PowerShell البعيد.
