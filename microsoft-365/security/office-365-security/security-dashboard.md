---
title: نظرة عامة على لوحة معلومات الأمان
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: fe0b9b8f-faa9-44ff-8095-4d1b2f507b74
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: استخدم لوحة معلومات الأمان الجديدة لمراجعة Office 365 حالة الحماية من التهديدات، وعرض تنبيهات الأمان والعمل عليها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: defda5c112cf29cb944b502f442cf0e721a32676
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971727"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>لوحة معلومات الأمان في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="basic-functions-and-how-to-open-security-dashboard"></a>الوظائف الأساسية وكيفية فتح لوحة معلومات الأمان

يمكن مركز توافق & الأمان في <https://protection.office.com> مؤسستك من إدارة حماية البيانات والامتثال. بافتراض أن لديك الأذونات اللازمة، تمكنك لوحة معلومات الأمان من مراجعة حالة الحماية من التهديدات، بالإضافة إلى عرض تنبيهات الأمان والعمل عليها.

شاهد الفيديو للحصول على نظرة عامة، ثم اقرأ هذه المقالة لمعرفة المزيد.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

استنادا إلى ما يتضمنه اشتراك مؤسستك، تتضمن لوحة معلومات الأمان العديد من عناصر واجهة المستخدم، مثل ملخص إدارة المخاطر وحالة الحماية من التهديدات واكتشافات التهديدات الأسبوعية العالمية والبرامج الضارة والمزيد، كما هو موضح في الأقسام التالية.

لعرض لوحة معلومات الأمان في مركز توافق & الأمان، انتقل إلى **لوحة معلومات** **إدارة** \> التهديدات. للانتقال مباشرة إلى لوحة معلومات الأمان، استخدم <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> يجب أن تكون مسؤولا عاما أو مسؤول أمان أو قارئ أمان لعرض لوحة معلومات الأمان. تتطلب بعض عناصر واجهة المستخدم أذونات إضافية لعرضها. لمعرفة المزيد، راجع ["الأذونات" في مركز توافق & الأمان](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>ملخص إدارة المخاطر

يخبرك عنصر واجهة مستخدم ملخص إدارة المخاطر بنظرة سريعة حول كيفية حماية مؤسستك من التهديدات خلال الأيام السبعة الماضية (7).

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="لوحة معلومات الأمان - عنصر واجهة مستخدم ملخص إدارة التهديدات" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

تعتمد المعلومات التي ستشاهدها في ملخص إدارة المخاطر على ما يتضمنه اشتراكك. يصف الجدول التالي المعلومات المضمنة Office 365 E3 Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|تم حظر رسائل البرامج الضارة<br>رسائل التصيد الاحتيالي محظورة<br>الرسائل التي أبلغ عنها المستخدمون<br><br><br><br>|تم حظر رسائل البرامج الضارة<br>رسائل التصيد الاحتيالي محظورة<br>الرسائل التي أبلغ عنها المستخدمون<br>تم حظر البرامج الضارة في اليوم الصفري<br>تم الكشف عن رسائل تصيد احتيالي متقدمة<br>عناوين URL الضارة محظورة|

لعرض عنصر واجهة مستخدم ملخص إدارة المخاطر أو الوصول إليه، يجب أن يكون لديك أذونات لعرض تقارير Defender لـ Office 365. لمعرفة المزيد، راجع [الأذونات المطلوبة لعرض تقارير Defender لـ Office 365؟](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>حالة الحماية من التهديدات

يظهر عنصر واجهة مستخدم حالة الحماية من التهديدات فعالية الحماية من التهديدات مع عرض مفصل ومتجه للتصيد الاحتيالي والبرامج الضارة.

:::image type="content" source="../../media/tpswidget.png" alt-text="عنصر واجهة مستخدم حالة الحماية من التهديدات" lightbox="../../media/tpswidget.png":::

تعتمد التفاصيل على ما إذا كان اشتراكك في Microsoft 365 يتضمن [Exchange Online Protection](exchange-online-protection-overview.md) (EOP) مع [Microsoft Defender لـ Office 365 أو بدونها](defender-for-office-365.md).

|إذا كان اشتراكك يتضمن...|سترى هذه التفاصيل|
|---|---|
|EOP ولكن ليس Microsoft Defender لـ Office 365|البريد الإلكتروني الضار الذي تم اكتشافه وحظره بواسطة EOP.<p> راجع [تقرير حالة الحماية من التهديدات (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Microsoft Defender لـ Office 365|المحتوى الضار والبريد الإلكتروني الضار الذي تم اكتشافه وحظره بواسطة EOP و Defender لـ Office 365 <p> العدد المجمع لرسائل البريد الإلكتروني الفريدة مع محتوى ضار محظور بواسطة محرك مكافحة البرامج الضارة، [والإزالة التلقائية لمدة صفر ساعة](zero-hour-auto-purge.md)، وميزات Defender لـ Office 365 (بما في ذلك [الارتباطات خزينة](safe-links.md) [والمرفقات خزينة](safe-attachments.md) [ومكافحة التصيد الاحتيالي في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> راجع [تقرير حالة الحماية من التهديدات](view-reports-for-mdo.md#threat-protection-status-report).|

لعرض عنصر واجهة مستخدم حالة الحماية من التهديدات أو الوصول إليه، يجب أن يكون لديك أذونات لعرض تقارير Defender لـ Office 365. لمعرفة المزيد، راجع [الأذونات المطلوبة لعرض تقارير Defender لـ Office 365؟](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>عمليات الكشف الأسبوعية العالمية عن التهديدات

يظهر عنصر واجهة مستخدم Global Weekly Threat Detections عدد التهديدات التي تم اكتشافها في رسائل البريد الإلكتروني على مدار الأيام السبعة الماضية (7) أيام.

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="عنصر واجهة مستخدم Global Weekly Threat Detections" lightbox="../../media/globalweeklythreatdetections.png":::

يتم حساب المقاييس كما هو موضح في الجدول التالي:

|متري|كيفية حسابه|
|---|---|
|الرسائل الممسوحة ضوئيا|عدد رسائل البريد الإلكتروني التي تم مسحها ضوئيا مضروبة في عدد المستلمين|
|تم إيقاف التهديدات|عدد رسائل البريد الإلكتروني التي تم تحديدها على أنها تحتوي على برامج ضارة مضروبة في عدد المستلمين|
|محظور بواسطة [Defender لـ Office 365](defender-for-office-365.md)|عدد رسائل البريد الإلكتروني المحظورة بواسطة Defender لـ Office 365 مضروبة في عدد المستلمين|
|تمت الإزالة بعد التسليم|عدد الرسائل التي تمت إزالتها بواسطة [الإزالة التلقائية بدون ساعة (ZAP)](zero-hour-auto-purge.md) مضروبة في عدد المستلمين|

## <a name="malware"></a>البرامج الضاره

تعرض عناصر واجهة المستخدم للبرامج الضارة تفاصيل حول اتجاهات البرامج الضارة وأنواع عائلة البرامج الضارة على مدى الأيام السبعة الماضية (7) أيام.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="اتجاهات البرامج الضارة وأنواع العائلة" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Insights

Insights ليس فقط المشكلات الرئيسية التي يجب مراجعتها، بل تتضمن أيضا توصيات وإجراءات يجب مراعاتها.

:::image type="content" source="../../media/smartinsights.png" alt-text="نتائج التحليلات الذكية" lightbox="../../media/smartinsights.png":::

على سبيل المثال، قد ترى أنه يتم تسليم رسائل البريد الإلكتروني للتصيد الاحتيالي لأن بعض المستخدمين قاموا بتعطيل خيارات البريد غير الهام الخاصة بهم. لمعرفة المزيد حول كيفية عمل الرؤى، راجع [التقارير والرؤى في مركز التوافق & الأمان](reports-and-insights-in-security-and-compliance.md).

## <a name="threat-investigation-and-response"></a>التحقيق في التهديدات والاستجابة لها

إذا كان اشتراك مؤسستك يتضمن [Microsoft Defender لـ Office 365 الخطة 2](office-365-ti.md)، فإن "لوحة معلومات الأمان" تحتوي على قسم يتضمن أدوات متقدمة للتحقيق في التهديدات والاستجابة لها. وتشمل هذه الأدوات [قدرات التحقيق والاستجابة التلقائية](automated-investigation-response-office.md). يمكن أن يكون التحقيق التلقائي والاستجابة مفيدين في سيناريوهات مثل [معالجة حسابات المستخدمين المخترقة بسرعة](address-compromised-users-quickly.md).

لمعرفة المزيد، راجع [بدء استخدام التحقيق التلقائي والاستجابة (AIR) في Office 365](office-365-air.md).

## <a name="trends"></a>الاتجاهات

يوجد بالقرب من أسفل لوحة معلومات الأمان قسم **"الاتجاهات** "، الذي يلخص اتجاهات تدفق البريد الإلكتروني لمؤسستك. توفر التقارير معلومات حول البريد الإلكتروني المصنف على أنه بريد عشوائي، والبرامج الضارة، ومحاولات التصيد الاحتيالي، والبريد الإلكتروني الجيد. انقر فوق لوحة لعرض معلومات أكثر تفصيلا في التقرير.

:::image type="content" source="../../media/trends.png" alt-text="قسم &quot;الاتجاهات&quot; الذي يلخص اتجاهات تدفق البريد الإلكتروني للمؤسسة" lightbox="../../media/trends.png":::

وإذا كان اشتراك مؤسستك يتضمن [Defender لـ Office 365 الخطة 2](office-365-ti.md)، فسيكون لديك أيضا تقرير **تنبيهات إدارة التهديدات الأخيرة** في هذا القسم الذي يمكن فريق الأمان من عرض تنبيهات الأمان ذات الأولوية العالية واتخاذ إجراء بشأنها.

لعرض عنصر واجهة مستخدم "البريد الإلكتروني المرسل" و"المستلم" أو الوصول إليه، يجب أن يكون لديك أذونات لعرض تقارير Defender لـ Office 365. لمعرفة المزيد، راجع [الأذونات المطلوبة لعرض تقارير Defender لـ Office 365؟](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

لعرض عنصر واجهة مستخدم "تنبيهات إدارة المخاطر الأخيرة" أو الوصول إليه، يجب أن يكون لديك أذونات لعرض التنبيهات. لمعرفة المزيد، راجع [أذونات RBAC المطلوبة لعرض التنبيهات](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>المقالات ذات الصلة

[عرض تقارير أمان البريد الإلكتروني في مركز توافق & الأمان](view-email-security-reports.md)

[عرض تقارير Microsoft Defender لـ Office 365](view-reports-for-mdo.md)

[دليل إعداد Microsoft Defender لـ Office 365](defender-for-office-365.md)

[Office 365 التحقيق والاستجابة للمخاطر](office-365-ti.md)
