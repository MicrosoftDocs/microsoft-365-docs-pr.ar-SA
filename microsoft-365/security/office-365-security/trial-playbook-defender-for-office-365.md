---
title: دليل المبادئ التجريبي Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: دليل المبادئ التجريبي لحلول Microsoft Defender لـ Office 365.
ms.openlocfilehash: f23c45d117735997c219278621be7f314602cd8f
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130681"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>دليل المبادئ التجريبي: Microsoft Defender لـ Office 365

مرحبا بك في دليل المبادئ التجريبي Microsoft Defender لـ Office 365. سيساعدك دليل المبادئ هذا على تحقيق أقصى استفادة من الإصدار التجريبي المجاني لمدة 90 يوما من خلال تعليمك كيفية حماية مؤسستك باستخدام Defender لـ Office 365. باستخدام توصيات Microsoft، ستتعرف على كيفية مساعدة Defender لـ Office 365 في تحديد نهج الحماية وتحليل التهديدات التي تتعرض لها مؤسستك والاستجابة للهجمات.

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="تمثيل رسومي لكافة مكونات Microsoft Defender لـ Office 365." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

هذه الإجراءات هي توصيات من فريق Microsoft Defender حول الميزات الرئيسية لتجربة الإصدار التجريبي لمدة 90 يوما.

## <a name="step-1-getting-started"></a>الخطوة 1: بدء الاستخدام

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>بدء الإصدار التجريبي Microsoft Defender لـ Office 365

بعد بدء الإصدار التجريبي وإكمال عملية الإعداد، قد يستغرق سريان التغييرات ما يصل إلى ساعتين.

لقد قمنا تلقائيا بتكوين [نهج الأمان المعينة مسبقا](preset-security-policies.md) في بيئتك. تمثل هذه النهج ملف تعريف حماية أساس مناسب لمعظم المستخدمين. تتضمن الحماية القياسية ما يلي:

- خزينة الارتباطات خزينة والمرفقات ونهج مكافحة التصيد الاحتيالي التي يتم تحديد نطاقها للمستأجر بأكمله أو مجموعة فرعية من المستخدمين الذين قد تكون اخترتهم أثناء عملية إعداد الإصدار التجريبي.
- خزينة حماية المرفقات SharePoint OneDrive Microsoft Teams.
- خزينة حماية الارتباطات لتطبيقات Office 365 المدعومة.

شاهد هذا الفيديو لمعرفة المزيد: [الحماية من الارتباطات الضارة باستخدام ارتباطات خزينة في Microsoft Defender لـ Office 365 - YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>تمكين المستخدمين من الإبلاغ عن المحتوى المشبوه

Defender لـ Office 365 تمكين المستخدمين من الإبلاغ عن الرسائل إلى فرق الأمان الخاصة بهم ويسمح للمسؤولين بإرسال الرسائل إلى Microsoft للتحليل.

- نشر [الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي](enable-the-report-message-add-in.md)".
- قم بإنشاء سير عمل للإبلاغ [عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md).
- استخدم [مدخل عمليات الإرسال](admin-submission.md).

شاهد هذا الفيديو لمعرفة المزيد: [تعرف على كيفية استخدام مدخل عمليات الإرسال لإرسال الرسائل للتحليل - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>مراجعة التقارير لفهم مشهد التهديد

استخدم قدرات إعداد التقارير في Defender لـ Office 365 للحصول على مزيد من التفاصيل حول بيئتك.

- فهم التهديدات التي يتم تلقيها في البريد الإلكتروني وأدوات التعاون باستخدام [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report).
- تعرف على مكان حظر التهديدات باستخدام [تقرير حالة تدفق البريد](view-email-security-reports.md#mailflow-status-report).
- [راجع الارتباطات](view-reports-for-mdo.md#url-protection-report) التي تم عرضها من قبل المستخدمين أو حظرها من قبل النظام.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="تقارير التعاون & البريد الإلكتروني في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-reporting.png":::

## <a name="step-2-intermediate-steps"></a>الخطوة 2: الخطوات المتوسطة

### <a name="prioritize-focus-on-your-most-targeted-users"></a>تحديد أولويات التركيز على المستخدمين الأكثر استهدافا

قم بحماية المستخدمين الأكثر استهدافا والأكثر وضوحا باستخدام "حماية الحساب ذات الأولوية" في Defender لـ Office 365، مما يساعدك على تحديد أولويات سير العمل لضمان أمان هؤلاء المستخدمين.

- تحديد المستخدمين الأكثر استهدافا أو الأكثر وضوحا.
- [وضع علامة على هؤلاء المستخدمين](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) كحسابات ذات أولوية.
- تعقب التهديدات لحساب الأولوية في جميع أنحاء المدخل.

شاهد هذا الفيديو لمعرفة المزيد: [حماية الحسابات ذات الأولوية في Microsoft Defender لـ Office 365 - YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

:::image type="content" source="../../media/mdo-trial-playbook-alerts.png" alt-text="التنبيهات في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-alerts.png":::

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>تجنب الخروقات المكلفة من خلال منع اختراق المستخدم

احصل على تنبيه للاختراق المحتمل وتقييد تأثير هذه التهديدات تلقائيا لمنع المهاجمين من الوصول بشكل أعمق إلى بيئتك.

- مراجعة [تنبيهات المستخدم المخترقة](address-compromised-users-quickly.md#compromised-user-alerts).
- [التحقيق والاستجابة](address-compromised-users-quickly.md) للمستخدمين المخترقين.

:::image type="content" source="../../media/mdo-trial-playbook-investigation.png" alt-text="التحقيق في المستخدمين المخترقين." lightbox="../../media/mdo-trial-playbook-investigation.png":::

شاهد هذا الفيديو لمعرفة المزيد: [الكشف عن الاختراق والاستجابة له في Microsoft Defender لـ Office 365 - YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>استخدام مستكشف التهديدات للتحقيق في رسائل البريد الإلكتروني الضارة

يمكنك Defender لـ Office 365 من التحقيق في الأنشطة التي تعرض الأشخاص في مؤسستك للخطر واتخاذ إجراءات لحماية مؤسستك. يمكنك القيام بذلك باستخدام [مستكشف التهديدات](threat-explorer.md).

- [ابحث عن بريد إلكتروني مريب تم تسليمه](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): البحث عن الرسائل وحذفها، أو تحديد عنوان IP لمرسل بريد إلكتروني ضار، أو بدء حدث لمزيد من التحقيق.
- [تحقق من إجراء التسليم وموقعه](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): يتيح لك هذا الفحص معرفة موقع رسائل البريد الإلكتروني التي بها مشكلة.
- [عرض المخطط الزمني للبريد الإلكتروني:](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email) ما عليك سوى البحث عن فريق عمليات الأمان.

### <a name="see-campaigns-targeting-your-organization"></a>الاطلاع على الحملات التي تستهدف مؤسستك

اطلع على الصورة الأكبر باستخدام "طرق عرض الحملة" في Defender لـ Office 365، مما يمنحك رؤية لحملات الهجوم التي تستهدف مؤسستك وتأثيرها على المستخدمين.

- [تحديد الحملات التي](campaigns.md#what-is-a-campaign) تستهدف المستخدمين.
- [تصور نطاق](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) الهجوم.
- [تعقب تفاعل المستخدم](campaigns.md#campaign-details) مع هذه الرسائل.

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="تفاصيل الحملة في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

شاهد هذا الفيديو لمعرفة المزيد: [طرق عرض الحملة في Microsoft Defender لـ Office 365 - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>استخدام الأتمتة لمعالجة المخاطر

الاستجابة بكفاءة باستخدام التحقيق التلقائي والاستجابة (AIR) لمراجعة التهديدات وتحديد أولوياتها والاستجابة لها.

- [تعرف على المزيد](automated-investigation-response-office.md) حول أدلة مبادئ التحقيق.
- [عرض تفاصيل ونتائج](email-analysis-investigations.md) التحقيق.
- القضاء على التهديدات من خلال [الموافقة على إجراءات المعالجة](air-remediation-actions.md).

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="نتائج التحقيق." lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

## <a name="step-3-advanced-content"></a>الخطوة 3: المحتوى المتقدم

### <a name="dive-deep-into-data-with-query-based-hunting"></a>التعمق في البيانات باستخدام التتبع المستند إلى الاستعلام

استخدم التتبع المتقدم لكتابة قواعد الكشف المخصصة، وفحص الأحداث في بيئتك بشكل استباقي، وتحديد مؤشرات التهديد. استكشف البيانات الأولية في بيئتك.

- [إنشاء قواعد الكشف المخصصة](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [الوصول إلى الاستعلامات المشتركة](../defender/advanced-hunting-shared-queries.md) التي أنشأها الآخرون.

شاهد هذا الفيديو لمعرفة المزيد: [تتبع المخاطر باستخدام Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>تدريب المستخدمين على اكتشاف التهديدات من خلال محاكاة الهجمات

تزويد المستخدمين بالمعرفة الصحيحة لتحديد التهديدات والإبلاغ عن الرسائل المشبوهة مع تدريب محاكاة الهجوم في Defender لـ Office 365.

- [محاكاة التهديدات الواقعية](attack-simulation-training.md) لتحديد المستخدمين المعرضين للخطر.
- [تعيين التدريب](attack-simulation-training.md#assign-training) للمستخدمين استنادا إلى نتائج المحاكاة.
- [تعقب تقدم](attack-simulation-training-insights.md) مؤسستك في عمليات المحاكاة وإكمال التدريب.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="رؤى التدريب على محاكاة الهجوم في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>موارد إضافية

- **دليل تفاعلي**: غير مألوف مع Defender لـ Office 365؟ راجع [الدليل التفاعلي](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) لفهم كيفية البدء.
- **مستندات Microsoft**: احصل على معلومات مفصلة حول كيفية عمل Defender لـ Office 365 وكيفية تنفيذها بشكل أفضل لمؤسستك. تفضل بزيارة [المستندات](overview.md).
- **ما هو مضمن**: للحصول على قائمة كاملة من ميزات أمان البريد الإلكتروني Office 365 المدرجة حسب مستوى المنتج، قم بعرض [مصفوفة الميزة](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **لماذا Defender لـ Office 365**: تعرض [ورقة بيانات Defender لـ Office 365](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) أهم 10 أسباب لاختيار العملاء ل Microsoft.
