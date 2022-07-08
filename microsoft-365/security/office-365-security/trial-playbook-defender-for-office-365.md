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
ms.custom: trial-playbook
ms.openlocfilehash: 6f19499a3c00fc1520d8bffb64336a789c017d28
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687729"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>دليل المبادئ التجريبي: Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على:**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

مرحبا بك في دليل المبادئ التجريبي Microsoft Defender لـ Office 365! سيساعدك دليل المبادئ هذا على تحقيق أقصى استفادة من الإصدار التجريبي المجاني لمدة 90 يوما من خلال تعليمك كيفية حماية مؤسستك باستخدام Defender لـ Office 365.

لديك الآن خيار تجربة Defender لـ Office 365 بإحدى طريقتين:

- **وضع الحظر (مستحسن):** إذا كان سجل تبادل البريد (MX) يشير إلى Microsoft 365، يمكنك تقييم قدرات Defender لـ Office 365 في وضع الحظر. Defender لـ Office 365 تطبيق إعدادات [نهج الأمان القياسية التي تم تعيينها مسبقا](preset-security-policies.md) تلقائيا.

  طوال فترة التقييم، يمكنك الاختيار في أي وقت للاشتراك في قالب حماية أعلى (إعدادات نهج الأمان المحددة مسبقا)، أو يمكنك إنشاء نهج الحماية الفردية الخاصة بك لتناسب احتياجاتك.

- **وضع التدقيق**: إذا كان سجل MX يشير إلى مكان آخر غير Microsoft 365 (على سبيل المثال، بوابة بريد إلكتروني تابعة لجهة خارجية)، يمكنك تقييم Defender لـ Office 365 في وضع التدقيق. لن يتخذ Defender لـ Office 365 إجراء حظر على الرسائل التي نحدد أنها ضارة.

  سيتم تسجيل هذه التهديدات وإتاحتها لمراجعتك من خلال [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report)، الذي يمنحك معلومات مفصلة عن أنواع التهديدات المكتشفة، ومن كانت التهديدات تستهدفها، وأكثر من ذلك بكثير. تشير هذه "المصيدات" الإضافية إلى قدرات الحماية الإضافية Defender لـ Office 365 عبر قدرات Exchange Online Protection القياسية (EOP) أو قدرات بوابات البريد الإلكتروني الأخرى التابعة لجهات خارجية. بمجرد أن تصبح راضيا وجاهزا لاستخدام Defender لـ Office 365، يمكنك [الترحيل إلى Defender لـ Office 365](migrate-to-defender-for-office-365.md).

:::image type="content" source="../../media/mdo-trial-playbook-what-is-mdo.png" alt-text="تمثيل رسومي لكافة مكونات Microsoft Defender لـ Office 365." lightbox="../../media/mdo-trial-playbook-what-is-mdo.png":::

باستخدام التوصيات الواردة في هذا الدليل، ستتعرف على كيفية مساعدة Defender لـ Office 365 في تحديد نهج الحماية وتحليل التهديدات التي تتعرض لها مؤسستك والاستجابة للهجمات.

لنبدأ!

## <a name="blocking-mode"></a>وضع الحظر

### <a name="step-1-getting-started-in-blocking-mode"></a>الخطوة 1: البدء في وضع الحظر

#### <a name="start-your-microsoft-defender-for-office-365-trial"></a>بدء الإصدار التجريبي Microsoft Defender لـ Office 365

بعد بدء الإصدار التجريبي وإكمال [عملية الإعداد](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-in-blocking-mode)، قد يستغرق سريان التغييرات ما يصل إلى ساعتين.

لقد قمنا تلقائيا بتكوين [نهج الأمان المعينة مسبقا](preset-security-policies.md) في بيئتك. تمثل هذه النهج ملف تعريف حماية أساس مناسب لمعظم المستخدمين. تتضمن الحماية القياسية ما يلي:

- الارتباطات الآمنة والمرفقات الآمنة ونهج مكافحة التصيد الاحتيالي التي يتم تحديد نطاقها للمستأجر بأكمله أو مجموعة فرعية من المستخدمين الذين قد تكون اخترتهم أثناء عملية إعداد الإصدار التجريبي.
- حماية المرفقات الآمنة ل SharePoint وOneDrive وMicrosoft Teams.
- حماية الارتباطات الآمنة لتطبيقات Office 365 المدعومة.

شاهد هذا الفيديو لمعرفة المزيد: [الحماية من الارتباطات الضارة باستخدام الارتباطات الآمنة في Microsoft Defender لـ Office 365 - YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

#### <a name="enable-users-to-report-suspicious-content-in-blocking-mode"></a>تمكين المستخدمين من الإبلاغ عن المحتوى المشبوه في وضع الحظر

Defender لـ Office 365 تمكين المستخدمين من الإبلاغ عن الرسائل إلى فرق الأمان الخاصة بهم ويسمح للمسؤولين بإرسال الرسائل إلى Microsoft للتحليل.

- نشر [الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي](enable-the-report-message-add-in.md)".
- قم بإنشاء سير عمل للإبلاغ [عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md).
- استخدم [مدخل عمليات الإرسال](admin-submission.md).

شاهد هذا الفيديو لمعرفة المزيد: [تعرف على كيفية استخدام مدخل عمليات الإرسال لإرسال الرسائل للتحليل - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-blocking-mode"></a>مراجعة التقارير لفهم مشهد التهديد في وضع الحظر

استخدم قدرات إعداد التقارير في Defender لـ Office 365 للحصول على مزيد من التفاصيل حول بيئتك.

- فهم التهديدات التي يتم تلقيها في البريد الإلكتروني وأدوات التعاون باستخدام [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report).
- تعرف على مكان حظر التهديدات باستخدام [تقرير حالة تدفق البريد](view-email-security-reports.md#mailflow-status-report).
- [راجع الارتباطات](view-reports-for-mdo.md#url-protection-report) التي تم عرضها من قبل المستخدمين أو حظرها من قبل النظام.

:::image type="content" source="../../media/mdo-trial-playbook-reporting.png" alt-text="تقارير التعاون & البريد الإلكتروني في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-reporting.png":::

### <a name="step-2-intermediate-steps-in-blocking-mode"></a>الخطوة 2: الخطوات المتوسطة في وضع الحظر

#### <a name="prioritize-focus-on-your-most-targeted-users"></a>تحديد أولويات التركيز على المستخدمين الأكثر استهدافا

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

#### <a name="use-threat-explorer-to-investigate-malicious-email"></a>استخدام مستكشف التهديدات للتحقيق في رسائل البريد الإلكتروني الضارة

يمكنك Defender لـ Office 365 من التحقيق في الأنشطة التي تعرض الأشخاص في مؤسستك للخطر واتخاذ إجراءات لحماية مؤسستك. يمكنك القيام بذلك باستخدام [مستكشف التهديدات](threat-explorer.md).

- [ابحث عن بريد إلكتروني مريب تم تسليمه](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): البحث عن الرسائل وحذفها، أو تحديد عنوان IP لمرسل بريد إلكتروني ضار، أو بدء حدث لمزيد من التحقيق.
- [تحقق من إجراء التسليم وموقعه](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): يتيح لك هذا الفحص معرفة موقع رسائل البريد الإلكتروني التي بها مشكلة.
- [عرض المخطط الزمني للبريد الإلكتروني:](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email) ما عليك سوى البحث عن فريق عمليات الأمان.

#### <a name="see-campaigns-targeting-your-organization"></a>الاطلاع على الحملات التي تستهدف مؤسستك

اطلع على الصورة الأكبر باستخدام "طرق عرض الحملة" في Defender لـ Office 365، مما يمنحك رؤية لحملات الهجوم التي تستهدف مؤسستك وتأثيرها على المستخدمين.

- [تحديد الحملات التي](campaigns.md#what-is-a-campaign) تستهدف المستخدمين.
- [تصور نطاق](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) الهجوم.
- [تعقب تفاعل المستخدم](campaigns.md#campaign-details) مع هذه الرسائل.

  :::image type="content" source="../../media/mdo-trial-playbook-campaign-details.png" alt-text="تفاصيل الحملة في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-campaign-details.png":::

شاهد هذا الفيديو لمعرفة المزيد: [طرق عرض الحملة في Microsoft Defender لـ Office 365 - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

#### <a name="use-automation-to-remediate-risks"></a>استخدام الأتمتة لمعالجة المخاطر

الاستجابة بكفاءة باستخدام التحقيق التلقائي والاستجابة (AIR) لمراجعة التهديدات وتحديد أولوياتها والاستجابة لها.

- [تعرف على المزيد](automated-investigation-response-office.md) حول أدلة مبادئ التحقيق.
- [عرض تفاصيل ونتائج](email-analysis-investigations.md) التحقيق.
- القضاء على التهديدات من خلال [الموافقة على إجراءات المعالجة](air-remediation-actions.md).

:::image type="content" source="../../media/mdo-trial-playbook-investigation-results.png" alt-text="نتائج التحقيق." lightbox="../../media/mdo-trial-playbook-investigation-results.png":::

### <a name="step-3-advanced-content-in-blocking-mode"></a>الخطوة 3: المحتوى المتقدم في وضع الحظر

#### <a name="dive-deep-into-data-with-query-based-hunting"></a>التعمق في البيانات باستخدام التتبع المستند إلى الاستعلام

استخدم التتبع المتقدم لكتابة قواعد الكشف المخصصة، وفحص الأحداث في بيئتك بشكل استباقي، وتحديد مؤشرات التهديد. استكشف البيانات الأولية في بيئتك.

- [إنشاء قواعد الكشف المخصصة](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [الوصول إلى الاستعلامات المشتركة](../defender/advanced-hunting-shared-queries.md) التي أنشأها الآخرون.

شاهد هذا الفيديو لمعرفة المزيد: [تتبع المخاطر باستخدام Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

#### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>تدريب المستخدمين على اكتشاف التهديدات من خلال محاكاة الهجمات

تزويد المستخدمين بالمعرفة الصحيحة لتحديد التهديدات والإبلاغ عن الرسائل المشبوهة مع تدريب محاكاة الهجوم في Defender لـ Office 365.

- [محاكاة التهديدات الواقعية](attack-simulation-training.md) لتحديد المستخدمين المعرضين للخطر.
- [تعيين التدريب](attack-simulation-training.md#assign-training) للمستخدمين استنادا إلى نتائج المحاكاة.
- [تعقب تقدم](attack-simulation-training-insights.md) مؤسستك في عمليات المحاكاة وإكمال التدريب.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="رؤى التدريب على محاكاة الهجوم في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="auditing-mode"></a>وضع التدقيق

### <a name="step-1-get-started-in-auditing-mode"></a>الخطوة 1: البدء في وضع التدقيق

#### <a name="start-your-defender-for-office-365-evaluation"></a>بدء تقييم Defender لـ Office 365

بعد الانتهاء من [عملية الإعداد](try-microsoft-defender-for-office-365.md#set-up-an-evaluation-in-audit-mode)، قد يستغرق سريان التغييرات ما يصل إلى ساعتين. لقد قمنا تلقائيا بتكوين نهج التقييم المعينة مسبقا في بيئتك.

تضمن نهج التقييم عدم اتخاذ أي إجراء بشأن البريد الإلكتروني الذي تم اكتشافه بواسطة Defender لـ Office 365.

#### <a name="enable-users-to-report-suspicious-content-in-auditing-mode"></a>تمكين المستخدمين من الإبلاغ عن المحتوى المشبوه في وضع التدقيق

Defender لـ Office 365 تمكين المستخدمين من الإبلاغ عن الرسائل إلى فرق الأمان الخاصة بهم ويسمح للمسؤولين بإرسال الرسائل إلى Microsoft للتحليل.

- نشر [الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي](enable-the-report-message-add-in.md)".
- قم بإنشاء سير عمل للإبلاغ [عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md).
- استخدم [مدخل عمليات الإرسال](admin-submission.md).

شاهد هذا الفيديو لمعرفة المزيد: [تعرف على كيفية استخدام مدخل عمليات الإرسال لإرسال الرسائل للتحليل - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### <a name="review-reports-to-understand-the-threat-landscape-in-auditing-mode"></a>مراجعة التقارير لفهم مشهد التهديد في وضع التدقيق

استخدم قدرات إعداد التقارير في Defender لـ Office 365 للحصول على مزيد من التفاصيل حول بيئتك.

- توفر [لوحة معلومات التقييم](try-microsoft-defender-for-office-365.md#reporting-in-audit-mode) عرضا سهلا للتهديدات التي اكتشفها Defender لـ Office 365 أثناء التقييم.
- فهم التهديدات التي يتم تلقيها في البريد الإلكتروني وأدوات التعاون باستخدام [تقرير حالة الحماية من التهديدات](view-email-security-reports.md#threat-protection-status-report).

### <a name="step-2-intermediate-steps-in-auditing-mode"></a>الخطوة 2: الخطوات المتوسطة في وضع التدقيق

#### <a name="use-threat-explorer-to-investigate-malicious-email-in-auditing-mode"></a>استخدام مستكشف التهديدات للتحقيق في البريد الإلكتروني الضار في وضع التدقيق

يمكنك Defender لـ Office 365 من التحقيق في الأنشطة التي تعرض الأشخاص في مؤسستك للخطر واتخاذ إجراءات لحماية مؤسستك. يمكنك القيام بذلك باستخدام [مستكشف التهديدات](threat-explorer.md).

- [ابحث عن بريد إلكتروني مريب تم تسليمه](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered): البحث عن الرسائل وحذفها، أو تحديد عنوان IP لمرسل بريد إلكتروني ضار، أو بدء حدث لمزيد من التحقيق.
- [تحقق من إجراء التسليم وموقعه](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): يتيح لك هذا الفحص معرفة موقع رسائل البريد الإلكتروني التي بها مشكلة.
- [عرض المخطط الزمني للبريد الإلكتروني:](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email) ما عليك سوى البحث عن فريق عمليات الأمان.

#### <a name="convert-to-standard-protection-at-the-end-of-evaluation-period"></a>التحويل إلى الحماية القياسية في نهاية فترة التقييم

عندما تكون مستعدا لتشغيل نهج Defender لـ Office 365 في الإنتاج، يمكنك استخدام "التحويل إلى الحماية القياسية" ضمن تجربة إدارة التقييم للانتقال بسهولة إلى الحماية القياسية في [نهج الأمان المحددة مسبقا](preset-security-policies.md).

1. في صفحة **تقييم Microsoft Defender لـ Office 365**، <https://security.microsoft.com/atpEvaluation>انقر فوق **"إدارة**".

   :::image type="content" source="../../media/mdo-trial-playbook-mdo-evaluation-page.png" alt-text="انقر فوق &quot;إدارة&quot; على صفحة تقييم Defender لـ Office 365 في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-mdo-evaluation-page.png":::

2. في القائمة المنبثقة التي تفتح، انقر فوق **"تحويل إلى حماية قياسية**"

   :::image type="content" source="../../media/mdo-trial-playbook-manage-flyout.png" alt-text="انقر فوق &quot;تحويل إلى حماية قياسية&quot; في القائمة المنبثقة &quot;إدارة&quot; في صفحة تقييم Defender لـ Office 365." lightbox="../../media/mdo-trial-playbook-manage-flyout.png":::

3. في مربع الحوار **"تحويل إلى حماية قياسية** " الذي يتم فتحه، انقر فوق **"متابعة** " لبدء الإعداد.

#### <a name="migrate-from-a-third-party-protection-service-or-device-to-defender-for-office-365"></a>الترحيل من خدمة حماية أو جهاز تابع لجهة خارجية إلى Defender لـ Office 365

إذا كان لديك بالفعل خدمة حماية أو جهاز موجود تابع لجهة خارجية يقع أمام Microsoft 365، يمكنك ترحيل حمايتك إلى Microsoft Defender لـ Office 365 للحصول على مزايا تجربة إدارة موحدة، وتكلفة محتملة أقل (باستخدام المنتجات التي تدفع ثمنها بالفعل)، ومنتج مكتمل مع حماية أمان متكاملة.

لمزيد من المعلومات، راجع [الترحيل من خدمة حماية أو جهاز تابع لجهة خارجية إلى Microsoft Defender لـ Office 365](migrate-to-defender-for-office-365.md).

### <a name="step-3-advanced-content-in-auditing-mode"></a>الخطوة 3: المحتوى المتقدم في وضع التدقيق

#### <a name="train-users-to-spot-threats-by-simulating-attacks-in-auditing-mode"></a>تدريب المستخدمين على اكتشاف التهديدات من خلال محاكاة الهجمات في وضع التدقيق

تزويد المستخدمين بالمعرفة الصحيحة لتحديد التهديدات والإبلاغ عن الرسائل المشبوهة مع تدريب محاكاة الهجوم في Defender لـ Office 365.

- [محاكاة التهديدات الواقعية](attack-simulation-training.md) لتحديد المستخدمين المعرضين للخطر.
- [تعيين التدريب](attack-simulation-training.md#assign-training) للمستخدمين استنادا إلى نتائج المحاكاة.
- [تعقب تقدم](attack-simulation-training-insights.md) مؤسستك في عمليات المحاكاة وإكمال التدريب.

  :::image type="content" source="../../media/mdo-trial-playbook-attack-simulation-training-results.png" alt-text="رؤى التدريب على محاكاة الهجوم في مدخل Microsoft 365 Defender." lightbox="../../media/mdo-trial-playbook-attack-simulation-training-results.png":::

## <a name="additional-resources"></a>موارد إضافية

- **دليل تفاعلي**: غير مألوف مع Defender لـ Office 365؟ راجع [الدليل التفاعلي](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) لفهم كيفية البدء.
- **دليل بدء الاستخدام السريع**: [Microsoft Defender لـ Office 365](https://go.microsoft.com/fwlink/p/?linkid=2197415)
- **مستندات Microsoft**: احصل على معلومات مفصلة حول كيفية عمل Defender لـ Office 365 وكيفية تنفيذها بشكل أفضل لمؤسستك. تفضل بزيارة [المستندات](overview.md).
- **ما هو مضمن**: للحصول على قائمة كاملة من ميزات أمان البريد الإلكتروني Office 365 المدرجة حسب مستوى المنتج، قم بعرض [مصفوفة الميزة](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **لماذا Defender لـ Office 365**: تعرض [ورقة بيانات Defender لـ Office 365](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) أهم 10 أسباب لاختيار العملاء ل Microsoft.
