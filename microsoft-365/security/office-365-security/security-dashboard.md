---
title: نظرة عامة حول لوحة معلومات الأمان
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
description: استخدم لوحة معلومات الأمان الجديدة لمراجعة Office 365 الحماية من المخاطر، وعرض تنبيهات الأمان والعمل عليها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4bc9d813732c4c67531aeb47a673111d62bbf417
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475730"
---
# <a name="security-dashboard-in-the-security--compliance-center"></a>لوحة معلومات الأمان في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-functions-and-how-to-open-security-dashboard"></a>الدالات الأساسية وكيفية فتح لوحة معلومات الأمان

يمكن مركز & الأمان في <https://protection.office.com> مؤسستك من إدارة حماية البيانات والتوافق. إذا افترضنا أن لديك الأذونات اللازمة، تمكنك لوحة معلومات الأمان من مراجعة حالة الحماية من المخاطر، بالإضافة إلى عرض تنبيهات الأمان والتصرف بشأنها.

شاهد الفيديو للحصول على نظرة عامة، ثم اقرأ هذه المقالة لمعرفة المزيد.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1VV3o]

استنادا إلى ما يتضمنه اشتراك مؤسستك، تتضمن لوحة معلومات الأمان العديد من عناصر واجهة المستخدم، مثل ملخص إدارة المخاطر، حالة الحماية من المخاطر، الكشف عن التهديدات الأسبوعية العالمية، البرامج الضارة، والمزيد، كما هو موضح في الأقسام التالية.

لعرض لوحة معلومات الأمان في مركز & الأمان، انتقل إلى لوحة **معلومات إدارة** \> **المخاطر**. الانتقال مباشرة إلى لوحة معلومات الأمان، استخدم <https://protection.office.com/searchandinvestigation/dashboard>.

> [!NOTE]
> يجب أن تكون مسؤولا عاما أو مسؤول أمان أو قارئ أمان لعرض لوحة معلومات الأمان. تتطلب بعض عناصر واجهة المستخدم أذونات إضافية لعرضها. لمعرفة المزيد، راجع [الأذونات في مركز & الأمان](permissions-in-the-security-and-compliance-center.md)[.

## <a name="threat-management-summary"></a>ملخص إدارة المخاطر

يخبرك عنصر واجهة مستخدم ملخص إدارة المخاطر بنظرة سريعة حول كيفية حماية مؤسستك من التهديدات خلال الأيام السبعة (7) الماضية.

:::image type="content" source="../../media/SecDash-ThreatMgmtSummary.png" alt-text="لوحة معلومات الأمان - عنصر واجهة مستخدم ملخص إدارة المخاطر" lightbox="../../media/SecDash-ThreatMgmtSummary.png":::

تعتمد المعلومات التي ستشاهدها في ملخص إدارة المخاطر على ما يتضمنه اشتراكك. يصف الجدول التالي المعلومات المضمنة Office 365 E3 Office 365 E5.

|Office 365 E3|Office 365 E5|
|---|---|
|رسائل البرامج الضارة المحظورة<br>رسائل التصيد الاحتيالي المحظورة<br>الرسائل التي تم إعلام المستخدمين بها<br><br><br><br>|رسائل البرامج الضارة المحظورة<br>رسائل التصيد الاحتيالي المحظورة<br>الرسائل التي تم إعلام المستخدمين بها<br>البرامج الضارة التي تم حظرها في اليوم الصفري<br>تم الكشف عن رسائل التصيد الاحتيالي المتقدمة<br>عناوين URL الضارة المحظورة|

لعرض عنصر واجهة مستخدم ملخص إدارة المخاطر أو الوصول إليه، يجب أن تكون لديك الأذونات لعرض Defender لـ Office 365 التقارير. لمعرفة المزيد، راجع [ما الأذونات المطلوبة لعرض Defender لـ Office 365 التقارير؟](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

## <a name="threat-protection-status"></a>حالة الحماية من المخاطر

يعرض عنصر واجهة مستخدم حالة الحماية من المخاطر فعالية الحماية من المخاطر من خلال طريقة عرض متصاعدة ومفصلة من التصيد الاحتيالي والبرامج الضارة.

:::image type="content" source="../../media/tpswidget.png" alt-text="عنصر واجهة مستخدم حالة الحماية من المخاطر" lightbox="../../media/tpswidget.png":::

تعتمد التفاصيل على ما إذا كان Microsoft 365 يتضمن [Exchange Online Protection (](exchange-online-protection-overview.md)EOP) مع أو [بدون](defender-for-office-365.md) Microsoft Defender لـ Office 365.

|إذا كان اشتراكك يتضمن...|سترى هذه التفاصيل|
|---|---|
|EOP ولكن ليس Microsoft Defender لـ Office 365|البريد الإلكتروني الضار الذي تم اكتشافه وحظره بواسطة EOP.<p> راجع [تقرير حالة الحماية من المخاطر (EOP).](view-email-security-reports.md#threat-protection-status-report)|
|Microsoft Defender لـ Office 365|تم الكشف عن المحتوى الضار والبريد الإلكتروني الضار وحظره بواسطة EOP Defender لـ Office 365 <p> العدد المجمع لرسائل البريد الإلكتروني الفريدة التي تحتوي على محتوى ضار تم حظره بواسطة محرك الحماية [](zero-hour-auto-purge.md)من البرامج الضارة وميزات إزالة تلقائية لمدة ساعة وميزات Defender لـ Office 365 (بما في ذلك [ارتباطات خزينة](safe-links.md) ومرفقات [خزينة](safe-attachments.md) و مكافحة التصيد الاحتيالي [في Defender لـ Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)). <p> راجع [تقرير حالة الحماية من المخاطر](view-reports-for-mdo.md#threat-protection-status-report).|

لعرض عنصر واجهة مستخدم حالة الحماية من المخاطر أو الوصول إليه، يجب أن تكون لديك الأذونات لعرض Defender لـ Office 365 التقارير. لمعرفة المزيد، راجع [ما الأذونات المطلوبة لعرض Defender لـ Office 365 التقارير؟](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports)

## <a name="global-weekly-threat-detections"></a>الكشف عن المخاطر الأسبوعية العالمية

يعرض عنصر واجهة مستخدم الكشف عن المخاطر الأسبوعية العالمية عدد التهديدات التي تم اكتشافها في رسائل البريد الإلكتروني خلال الأيام السبعة الماضية (7).

:::image type="content" source="../../media/globalweeklythreatdetections.png" alt-text="عنصر واجهة مستخدم الكشف عن المخاطر الأسبوعية العالمية" lightbox="../../media/globalweeklythreatdetections.png":::

يتم حساب المقاييس كما هو موضح في الجدول التالي:

|متري|كيفية حسابه|
|---|---|
|الرسائل الممسوحة ضوئيا|عدد رسائل البريد الإلكتروني الممسوحة ضوئيا مضروبة في عدد المستلمين|
|تم إيقاف التهديدات|عدد رسائل البريد الإلكتروني المحددة على أنها تحتوي على برامج ضارة مضروبة في عدد المستلمين|
|تم حظره [بواسطة Defender لـ Office 365](defender-for-office-365.md)|عدد رسائل البريد الإلكتروني التي تم حظرها Defender لـ Office 365 مضروبا في عدد المستلمين|
|تمت الإزالة بعد التسليم|عدد الرسائل التي تمت إزالتها [بواسطة إزالة تلقائية لمدة ساعة (ZAP)](zero-hour-auto-purge.md) مضروبا في عدد المستلمين|

## <a name="malware"></a>البرامج الضارة

تظهر عناصر واجهة مستخدم البرامج الضارة تفاصيل حول اتجاهات البرامج الضارة وأنواع عائلة البرامج الضارة على مدار الأيام السبعة (7) الماضية.

:::image type="content" source="../../media/malwarewidgetatpe5.png" alt-text="اتجاهات البرامج الضارة وأنواع العائلة" lightbox="../../media/malwarewidgetatpe5.png":::

## <a name="insights"></a>Insights

Insights المشاكل الأساسية التي يجب عليك مراجعتها، بل تتضمن أيضا توصيات والإجراءات التي يجب التفكير فيها.

:::image type="content" source="../../media/smartinsights.png" alt-text="الرؤى الذكية" lightbox="../../media/smartinsights.png":::

على سبيل المثال، قد ترى أنه يتم تسليم رسائل البريد الإلكتروني التصيد الاحتيالي لأن بعض المستخدمين قد عطلوا خيارات البريد غير الهام. لمعرفة المزيد حول كيفية عمل الرؤى، راجع التقارير والأفكار [في مركز](reports-and-insights-in-security-and-compliance.md) التوافق & الأمان.

## <a name="threat-investigation-and-response"></a>التحقيق في التهديدات والاستجابة لها

إذا كان اشتراك مؤسستك يتضمن Microsoft Defender لـ Office 365 [2](office-365-ti.md)، فإن لوحة معلومات الأمان تحتوي على قسم يتضمن أدوات متقدمة للتحري عن المخاطر والاستجابة لها. تتضمن هذه الأدوات [قدرات الاستجابة والتحري التلقائية](automated-investigation-response-office.md). يمكن أن تكون الاستجابة والتحريات التلقائية مفيدة في سيناريوهات مثل معالجة حسابات المستخدمين [التي تم اختراقها بسرعة](address-compromised-users-quickly.md).

لمعرفة المزيد، راجع [بدء استخدام الاستجابة والتحري التلقائي (AIR) في Office 365](office-365-air.md).

## <a name="trends"></a>الاتجاهات

يوجد بالقرب من أسفل لوحة معلومات الأمان قسم **الاتجاهات** ، الذي يلخص اتجاهات تدفق البريد الإلكتروني لمنظمتك. توفر التقارير معلومات حول البريد الإلكتروني المصنف كبريد عشوائي، والبرامج الضارة، ومحاولات التصيد الاحتيالي، والبريد الإلكتروني الجيد. انقر فوق لوحة لعرض معلومات أكثر تفصيلا في التقرير.

:::image type="content" source="../../media/trends.png" alt-text="القسم &quot;الاتجاهات&quot; الذي يلخص اتجاهات تدفق البريد الإلكتروني في المؤسسة" lightbox="../../media/trends.png":::

وإذا كان اشتراك مؤسستك يتضمن [Defender لـ Office 365 2](office-365-ti.md)، سيكون لديك أيضا تقرير تنبيهات إدارة المخاطر الأخيرة في هذا القسم الذي يمكن  فريق الأمان من عرض تنبيهات الأمان ذات الأولوية العالية واتخاذ إجراء بشأنها.

لعرض عنصر واجهة مستخدم البريد الإلكتروني المرسل والمستلم أو الوصول إليه، يجب أن يكون لديك الأذونات لعرض Defender لـ Office 365 الواردة. لمعرفة المزيد، راجع [ما الأذونات المطلوبة لعرض Defender لـ Office 365 التقارير؟](view-reports-for-mdo.md#what-permissions-are-needed-to-view-the-defender-for-office-365-reports).

لعرض عنصر واجهة مستخدم تنبيهات إدارة المخاطر الأخيرة أو الوصول إليه، يجب أن يكون لديك الأذونات لعرض التنبيهات. لمعرفة المزيد، راجع [أذونات RBAC المطلوبة لعرض التنبيهات](../../compliance/alert-policies.md#rbac-permissions-required-to-view-alerts).

## <a name="related-articles"></a>المقالات ذات الصلة

[عرض تقارير أمان البريد الإلكتروني في مركز & الأمان](view-email-security-reports.md)

[عرض تقارير Microsoft Defender لـ Office 365](view-reports-for-mdo.md)

[Defender لـ Office 365](defender-for-office-365.md)

[Office 365 الاستجابة والتحري عن المخاطر](office-365-ti.md)
