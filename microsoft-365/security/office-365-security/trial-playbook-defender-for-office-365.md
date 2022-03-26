---
title: Microsoft Defender Office 365 الإصدار التجريبي
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: Microsoft Defender for Office 365 الإصدار التجريبي من الحلول.
ms.openlocfilehash: 8e0ae58983321d16051e8fc5e0a0d1210d937353
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63572107"
---
# <a name="trial-playbook-microsoft-defender-for-office-365"></a>دفتر التشغيل التجريبي: Microsoft Defender Office 365

مرحبا بك في Microsoft Defender Office 365 الإصدار التجريبي. سيساعدك هذا المصنف على الاستفادة إلى أفضل مدى من الإصدار التجريبي المجاني لمدة 90 يوما من خلال تعليمك كيفية حماية مؤسستك باستخدام Defender Office 365. باستخدام توصيات Microsoft، ستتعرف على كيفية مساعدة Defender for Office 365 في تحديد سياسات الحماية وتحليل التهديدات التي تواجهها مؤسستك والاستجابة للهجمات.

![تمثيل رسومي لجميع مكونات Microsoft Defender Office 365.](../../media/mdo-trial-playbook-what-is-mdo.png)

هذه الإجراءات هي توصيات من فريق Microsoft Defender حول الميزات الأساسية لتجربتها في الإصدار التجريبي الذي لمدة 90 يوما.

## <a name="step-1-getting-started"></a>الخطوة 1: بدء العمل

### <a name="start-your-microsoft-defender-for-office-365-trial"></a>بدء تشغيل الإصدار التجريبي من Microsoft Defender Office 365 الإصدار التجريبي

بعد بدء الإصدار التجريبي وإكمال عملية الإعداد، قد يستغرق الأمر ساعتين حتى يتم تنفيذ التغييرات.

لقد قمنا تلقائيا بتكوين سياسات [أمان تم إعدادها مسبقا](preset-security-policies.md) في بيئتك. تمثل هذه السياسات ملف تعريف حماية أساسي مناسب لمعظم المستخدمين. تتضمن الحماية القياسية:

- خزينة الارتباطات خزينة المرفقات ونهج مكافحة التصيد الاحتيالي التي تم تحديد نطاقها للمستأجر أو مجموعة فرعية من المستخدمين الذين ربما اخترتهم أثناء عملية إعداد الإصدار التجريبي.
- حماية SharePoint OneDrive Office وتطبيقات Microsoft Teams.

شاهد هذا الفيديو لمعرفة المزيد: الحماية من الارتباطات الضارة باستخدام خزينة [في Microsoft Defender Office 365 - YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

### <a name="enable-users-to-report-suspicious-content"></a>تمكين المستخدمين من الإبلاغ عن محتوى مريب

يمكن Office 365 Defender للمستخدمين من الإبلاغ عن الرسائل إلى فرق الأمان الخاصة بهم ويسمح للمسؤولين بإرسال الرسائل إلى Microsoft لتحليلها.

- نشر الوظائف [الإضافية "رسالة التقرير" أو "الإبلاغ عن التصيد الاحتيالي" الإضافية](enable-the-report-message-add-in.md).
- إنشاء سير عمل [ل الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md).
- استخدم [مدخل الواجبات المرسلة](admin-submission.md).

شاهد هذا الفيديو لمعرفة المزيد: تعرف على كيفية استخدام مدخل الواجبات المرسلة [لإرسال الرسائل لتحليلها - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

### <a name="review-reports-to-understand-the-threat-landscape"></a>مراجعة التقارير لفهم مشهد التهديدات

استخدم قدرات إعداد التقارير في Defender Office 365 للحصول على مزيد من التفاصيل حول بيئتك.

- فهم التهديدات التي يتم تلقيها في البريد الإلكتروني وأدوات التعاون باستخدام تقرير [حالة الحماية من المخاطر](view-email-security-reports.md#threat-protection-status-report).
- راجع مكان حظر التهديدات باستخدام تقرير [حالة تدفق البريد](view-email-security-reports.md#mailflow-status-report).
- [راجع الارتباطات](view-reports-for-mdo.md#url-protection-report) التي تم عرضها من قبل المستخدمين أو تم حظرها بواسطة النظام.

![إرسال & إلى تقارير التعاون في Microsoft 365 Defender الإلكتروني.](../../media/mdo-trial-playbook-reporting.png)

## <a name="step-2-intermediate-steps"></a>الخطوة 2: الخطوات المتوسطة

### <a name="prioritize-focus-on-your-most-targeted-users"></a>تحديد أولوية التركيز على المستخدمين الأكثر استهدافا

يمكنك حماية المستخدمين الأكثر استهدافا والأكثر ظهورا باستخدام حماية حساب الأولوية في Defender Office 365، مما يساعدك على تحديد أولويات سير العمل لضمان أمان هؤلاء المستخدمين.

- حدد المستخدمين الأكثر استهدافا أو الأكثر ظهورا.
- [ضع علامة على هؤلاء المستخدمين](../../admin/setup/priority-accounts.md#add-priority-accounts-from-the-setup-page) ك حسابات ذات أولوية.
- تعقب التهديدات التي تواجه حساب الأولوية في المدخل.

شاهد هذا الفيديو لمعرفة المزيد: حماية حسابات الأولوية في [Microsoft Defender Office 365 - YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

![التنبيهات في Microsoft 365 Defender المدخل.](../../media/mdo-trial-playbook-alerts.png)

### <a name="avoid-costly-breaches-by-preventing-user-compromise"></a>تجنب الخروقات مكلفة من خلال منع اختراق المستخدم

احصل على تنبيهات باحتمال حدوث اختراق وقيود تأثير هذه التهديدات بشكل تلقائي لمنع المهاجمين من الوصول بشكل أكبر إلى بيئتك.

- راجع [تنبيهات المستخدمين التي تم اختراقها](address-compromised-users-quickly.md#compromised-user-alerts).
- [التحقق من المستخدمين](address-compromised-users-quickly.md) المساسين والاستجابة لها.

![تحقق من المستخدمين المساسين.](../../media/mdo-trial-playbook-investigation.png)

شاهد هذا الفيديو لمعرفة المزيد: الكشف عن اختراق في [Microsoft Defender Office 365 - YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

### <a name="use-threat-explorer-to-investigate-malicious-email"></a>استخدام "مستكشف التهديدات" للتحقق من البريد الإلكتروني الضار

تمكنك Office 365 Defender for Office 365 من التحقق من الأنشطة التي تعرض الأشخاص في مؤسستك للخطر واتخاذ إجراء لحماية مؤسستك. يمكنك القيام بذلك باستخدام ["مستكشف التهديدات" أو (الكشف في الوقت الحقيقي).](threat-explorer.md)

- [البحث عن البريد الإلكتروني المريب](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered) الذي تم تسليمه: البحث عن الرسائل وحذفها، أو تحديد عنوان IP لمرسل بريد إلكتروني ضار، أو بدء حادث لمزيد من التحقيق.
- [تحقق من إجراء التسليم وموقعه](investigate-malicious-email-that-was-delivered.md#check-the-delivery-action-and-location): يتيح لك هذا الاختيار معرفة موقع رسائل البريد الإلكتروني التي تواجه مشكلة.
- [عرض المخطط الزمني لبريدك الإلكتروني](investigate-malicious-email-that-was-delivered.md#view-the-timeline-of-your-email): ما عليك سوى البحث عن فريق عمليات الأمان.

### <a name="see-campaigns-targeting-your-organization"></a>الاطلاع على الحملات التي تستهدف مؤسستك

شاهد الصورة الأكبر باستخدام طرق عرض الحملة في Defender for Office 365، مما يوفر لك طريقة عرض لحملات الهجمات التي تستهدف مؤسستك وتأثيرها على المستخدمين.

- [تحديد الحملات](campaigns.md#what-is-a-campaign) التي تستهدف المستخدمين.
- [تمثيل نطاق](campaigns.md#campaign-views-in-the-microsoft-365-defender-portal) الهجوم بشكل مرئي.
- [تعقب تفاعل المستخدم](campaigns.md#campaign-details) مع هذه الرسائل.

![تفاصيل الحملة في مدخل Microsoft 365 Defender.](../../media/mdo-trial-playbook-campaign-details.png)

شاهد هذا الفيديو لمعرفة المزيد: [طرق عرض الحملات في Microsoft Defender Office 365 - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

### <a name="use-automation-to-remediate-risks"></a>استخدام التنفيذ التلقائي في معالجة المخاطر

قم بالاستجابة بفاعلية باستخدام الاستجابات والتحريات التلقائية (AIR) لمراجعة التهديدات وتحديد أولوياتها والاستجابة لها.

- [تعرف على المزيد](automated-investigation-response-office.md) حول دفاتر تشغيل التحقيق.
- [عرض تفاصيل ونتائج](email-analysis-investigations.md) التحقيق.
- إزالة التهديدات من [خلال الموافقة على إجراءات المعالجة](air-remediation-actions.md).

![نتائج التحقيق.](../../media/mdo-trial-playbook-investigation-results.png)

## <a name="step-3-advanced-content"></a>الخطوة 3: المحتوى المتقدم

### <a name="dive-deep-into-data-with-query-based-hunting"></a>التعمق في البيانات باستخدام البحث المستند إلى الاستعلامات

استخدم الصيد المتقدم لكتابة قواعد الكشف المخصصة، وفحص الأحداث في بيئتك بشكل استباقي، وتحديد موقع مؤشرات التهديدات. استكشف البيانات الأولية في بيئتك.

- [إنشاء قواعد الكشف المخصصة](../defender/advanced-hunting-overview.md#get-started-with-advanced-hunting).
- [الوصول إلى الاستعلامات المشتركة التي](../defender/advanced-hunting-shared-queries.md) أنشأها الآخرون.

شاهد هذا الفيديو لمعرفة المزيد: [مكافحة التهديدات باستخدام Microsoft 365 Defender - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

### <a name="train-users-to-spot-threats-by-simulating-attacks"></a>تدريب المستخدمين على اكتشاف التهديدات من خلال محاكاة الهجمات

قم بتزويد المستخدمين بالمعرفة المناسبة للتعرف على التهديدات وإعداد تقرير عن الرسائل المريبة من خلال التدريب على محاكاة الهجمات في Defender for Office 365.

- [محاكاة التهديدات الواقعية](attack-simulation-training.md) لتحديد المستخدمين المعرضين للخطر.
- [تعيين تدريب](attack-simulation-training.md#assign-training) للمستخدمين استنادا إلى نتائج المحاكاة.
- [تعقب تقدم](attack-simulation-training-insights.md) مؤسستك في عمليات المحاكاة وإكمال التدريب.

![تحليلات التدريب على محاكاة الهجمات في Microsoft 365 Defender الإلكتروني.](../../media/mdo-trial-playbook-attack-simulation-training-results.png)

## <a name="additional-resources"></a>موارد إضافية

- **دليل تفاعلي**: غير مألوف مع Defender for Office 365؟ راجع [الدليل التفاعلي](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) لفهم كيفية البدء.
- **مستندات Microsoft**: احصل على معلومات مفصلة حول Office 365 يعمل بها Defender for Office 365 وكيفية تنفيذه على أفضل نحو لمنظمتك. تفضل [بزيارة المستندات](overview.md).
- **الميزات المضمنة**: للحصول على قائمة كاملة Office 365 أمان البريد الإلكتروني المدرجة حسب مستوى المنتج، يمكنك عرض [مصفوفة الميزات](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **لماذا يعرض Defender Office 365**: تعرض ورقة بيانات Office 365 Defender for [Office 365](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4FCiy) أهم 10 أسباب لاختيار العملاء ل Microsoft.
