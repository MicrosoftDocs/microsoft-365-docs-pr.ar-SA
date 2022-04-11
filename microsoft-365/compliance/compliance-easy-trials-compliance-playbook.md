---
title: دليل المبادئ التجريبي لحلول التوافق Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MOE150
- MET150
description: دليل المبادئ التجريبي لحلول التوافق Microsoft 365.
ms.openlocfilehash: 8c5456344a97a0cfc4564c228eeba20067682070
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759159"
---
# <a name="trial-playbook-microsoft-365-compliance-solutions"></a>دليل المبادئ التجريبي: حلول التوافق Microsoft 365

مرحبا بك في دليل المبادئ التجريبي لحلول التوافق Microsoft 365. سيساعدك دليل المبادئ هذا على تحقيق أقصى استفادة من الإصدار التجريبي المجاني لمدة 90 يوما من خلال مساعدتك على اكتشاف قدرات قوية وشاملة لمنتجات التوافق والأمان Microsoft 365.

ستساعدك تجربة كل حل على اتخاذ قرارات مستنيرة لتلبية احتياجات الامتثال لمؤسستك.

ميزات:

- [التدقيق المتقدم](#advanced-audit)
- [توافق الاتصالات](#communication-compliance)
- [إدارة التوافق](#compliance-manager)
- [منع فقدان البيانات](#data-loss-prevention)
- [eDiscovery](#ediscovery)
- [حماية البيانات](#information-protection)
- [Insider Risk Management](#insider-risk-management)
- [إدارة السجلات](#records-management)

الوظائف الإضافية الاختيارية:

- [تقييمات متميزة ل Compliance Manager](#compliance-manager-premium-assessments)
- [Microsoft Priva Privacy Risk Management وطلبات حقوق موضوع Microsoft Priva](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-365"></a>إجراءات التوافق مع Microsoft 365

ابدأ بتجربة حلول التوافق من Microsoft بسهولة وسرعة دون تغيير بيانات التعريف الخاصة بمؤسستك. اعتمادا على أولوياتك، يمكنك البدء بأي من مجالات الحل هذه لرؤية القيمة الفورية. فيما يلي خمسة مخاوف تنظيمية قصوى كما هو موضح من قبل عملائنا والحلول الموصى بها للبدء بها.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="إجراءات التوافق مع Microsoft 365":::

## <a name="advanced-audit"></a>التدقيق المتقدم

**إجراء التحقيقات**

يساعد التدقيق المتقدم المؤسسات على إجراء تحقيقات الطب الشرعي والتوافق من خلال زيادة استبقاء سجل التدقيق المطلوب لإجراء تحقيق، وتوفير الوصول إلى الأحداث الهامة التي تساعد في تحديد نطاق التسوية، وتوفير وصول أسرع إلى واجهة برمجة تطبيقات نشاط الإدارة Office 365.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>الخطوة 1: [تطبيق ترخيص E5 على كل مستخدم ترغب في إنشاء أحداث E5 له](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

تتطلب ميزات التدقيق المتقدمة مثل القدرة على تسجيل الأحداث الهامة مثل MailItemsAccessed و Send ترخيص E5 مناسبا تم تعيينه للمستخدمين. بالإضافة إلى ذلك، يجب تمكين تطبيق/خدمة التدقيق المتقدم لهؤلاء المستخدمين.

إعداد التدقيق المتقدم للمستخدمين - للتحقق من تعيين تطبيق التدقيق المتقدم للمستخدمين، [نفذ الخطوات التالية لكل مستخدم](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users).

1. تمكين أحداث التدقيق المتقدمة - [تمكين SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-advanced-audit-events) لتدقيقها لكل مستخدم في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. إعداد نهج استبقاء التدقيق - [إنشاء نهج استبقاء سجل تدقيق إضافية](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) لتلبية متطلبات عمليات الأمان الخاصة بمؤسستك وفرق تكنولوجيا المعلومات والتوافق.
1. البحث عن أحداث التدقيق المتقدم - [البحث عن أحداث التدقيق المتقدم الهامة](set-up-advanced-audit.md#step-4-search-for-advanced-audit-events) والأنشطة الأخرى عند إجراء التحقيقات الجنائية.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>الخطوة 2: [إنشاء نهج سجل تدقيق جديدة لتحديد مدة الاحتفاظ بسجلات التدقيق في مؤسستك للأنشطة التي يقوم بها المستخدمون وتحديد مستويات الأولوية لنهجك](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> أفضل الممارسات التجريبية: إنشاء خلال أول 30 يوما

تعد نهج استبقاء سجل التدقيق جزءا من قدرات التدقيق المتقدم الجديدة في Microsoft 365. يتيح لك نهج استبقاء سجل التدقيق تحديد مدة الاحتفاظ بسجلات التدقيق في مؤسستك.

1. قبل إنشاء نهج استبقاء سجل التدقيق – [الأمور الأساسية التي يجب معرفتها](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) قبل إنشاء النهج الخاص بك.
1. [إنشاء نهج استبقاء سجل التدقيق](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [إدارة نهج استبقاء سجل التدقيق في مركز التوافق في Microsoft 365](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center) - يتم سرد نهج استبقاء سجل التدقيق في علامة تبويب نهج استبقاء التدقيق (تسمى أيضا لوحة المعلومات). يمكنك استخدام لوحة المعلومات لعرض نهج استبقاء التدقيق وتحريرها وحذفها.
1. إنشاء نهج استبقاء سجل التدقيق وإدارتها على PowerShell - يمكنك أيضا استخدام Security & Compliance Center PowerShell [لإنشاء نهج استبقاء سجل التدقيق وإدارتها](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). أحد أسباب استخدام PowerShell هو إنشاء نهج لنوع سجل أو نشاط غير متوفر في واجهة المستخدم.

## <a name="communication-compliance"></a>توافق الاتصالات

**تحديد انتهاكات سياسة قواعد السلوك والتصرف وفقا لها**

يساعدك توافق الاتصالات على تحديد انتهاكات الاتصال بذكاء لدعم بيئة عمل متوافقة وسليمة من خلال مساعدتك في اكتشاف الرسائل غير المناسبة، والتحقيق في انتهاكات النهج المحتملة، واتخاذ خطوات للمعالجة.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>الخطوة 1: [تمكين الأذونات للامتثال للاتصالات](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

[تعيين كافة مستخدمي التوافق إلى مجموعة دور توافق الاتصالات](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).

### <a name="step-2-enable-the-audit-log"></a>الخطوة 2: [تمكين سجل التدقيق](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

لاستخدام هذه الميزة، قم بتشغيل التدقيق حتى تتمكن مؤسستك من بدء تسجيل نشاط المستخدم والمسؤول في مؤسستك. عند تشغيل هذا، سيتم تسجيل النشاط في سجل التدقيق وسيتوفر لعرضه في تقرير. لمعرفة المزيد، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>الخطوة 3: [إنشاء نهج توافق الاتصالات](communication-compliance-policies.md)

[إنشاء نهج توافق الاتصالات باستخدام القوالب الموجودة](communication-compliance-policies.md): 1- المحتوى غير المناسب؛ 2- معلومات حساسة؛ 3- الامتثال التنظيمي؛ 4- تعارض في الاهتمام.

### <a name="step-4-investigate-and-remediate-alerts"></a>الخطوة 4: [التحقيق في التنبيهات ومعالجتها](communication-compliance-investigate-remediate.md)

[التحقيق في تنبيهات الامتثال للاتصالات ومعالجتها](communication-compliance-investigate-remediate.md) .

## <a name="compliance-manager"></a>إدارة التوافق

**إدارة التوافق التنظيمي بسهولة**

يمكن أن يساعدك Compliance Manager طوال رحلة الامتثال الخاصة بك، بدءا من جرد مخاطر حماية البيانات إلى إدارة تعقيدات تنفيذ عناصر التحكم، والبقاء على اطلاع دائم باللوائح والشهادات، وإعداد التقارير إلى المراجعين.

### <a name="step-1-get-to-know-compliance-manager"></a>الخطوة 1: [التعرف على Compliance Manager](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

صفحة نظرة عامة على Compliance Manager هي أفضل محطة أولى لمراجعة شاملة لما هو Compliance Manager وكيفية عمله. قد ترغب أيضا في الانتقال مباشرة إلى الأقسام الرئيسية من وثائقنا باستخدام الارتباطات أدناه:

- [فهم درجة التوافق الخاصة بك](compliance-manager.md#understanding-your-compliance-score)
- [نظرة عامة على العناصر الرئيسية: عناصر التحكم والتقييمات والقوالب وإجراءات التحسين](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [فهم لوحة معلومات Compliance Manager](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [تصفية طريقة عرض لوحة المعلومات](compliance-manager-setup.md#filtering-your-dashboard-view)
- [التعرف على إجراءات التحسين](compliance-manager-setup.md#improvement-actions-page)
- [فهم التقييمات](compliance-manager.md#assessments)
- [إجراء فحص سريع للبيئة الخاصة بك باستخدام Configuration Manager التوافق من Microsoft](compliance-manager-mcca.md)

![Compliance Manager - لوحة المعلومات.](../media/compliance-manager-dashboard.png "لوحة معلومات Compliance Manager")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>الخطوة 2: [تكوين Compliance Manager لإدارة أنشطة التوافق الخاصة بك](compliance-manager-assessments.md)

> [!TIP]
> أفضل الممارسات التجريبية: الفحص خلال أول 30 يوما

ابدأ العمل مع التقييمات واتخاذ إجراءات التحسين لتنفيذ عناصر التحكم وتحسين درجة التوافق الخاصة بك.

1. [اختر قالبا تم إنشاؤه مسبقا لإنشاء تقييمك الأول وإدارته](compliance-manager-assessments.md).
1. [فهم كيفية استخدام القوالب لإنشاء التقييمات](compliance-manager-templates.md).
1. [تنفيذ واختبار العمل على إجراءات التحسين لإكمال عناصر التحكم في التقييمات الخاصة بك](compliance-manager-improvement-actions.md).
1. [فهم أفضل لكيفية تأثير الإجراءات المختلفة على درجة الامتثال الخاصة بك](compliance-score-calculation.md).

> [!NOTE]
> يتضمن اشتراك Microsoft 365 أو Office 365 E1/E3 قالب Microsoft Data Protection Baseline. Microsoft 365 أو Office 365 E5، يتضمن توافق E5 قوالب ل:
>
> - أساس حماية البيانات من Microsoft
> - القانون العام لحماية البيانات (GDPR) للاتحاد الأوروبي  
> - ISO/IEC 27001،
> - NIST 800-53
>
> يتضمن Compliance Manager أكثر من 300 قالب تنظيمي أو متميز يمكن شراؤه كوظيفة إضافية. راجع القائمة هنا. مع أي قوالب متميزة (مضمنة في اشتراكك أو تم شراؤها كوظيفة إضافية) سوف تتلقى الإصدار العالمي من هذه القوالب، ما يسمح لك بإدارة توافقك مع أي منتج أو خدمة

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>الخطوة 3: [التحجيم: استخدام وظائف متقدمة لتلبية احتياجاتك المخصصة](compliance-manager-templates-create.md)

التقييمات المخصصة مفيدة لما يلي:

- إدارة التوافق للمنتجات غير Microsoft 365 مثل تطبيقات وخدمات الجهات الخارجية والتطبيقات المحلية والأصول الأخرى
- إدارة عناصر التحكم في الامتثال المخصصة أو الخاصة بالأعمال

1. [توسيع قالب Compliance Manager عن طريق إضافة عناصر التحكم وإجراءات التحسين الخاصة بك](compliance-manager-templates-extend.md)
1. [إنشاء القالب المخصص الخاص بك](compliance-manager-templates-create.md)
1. [تعديل قالب موجود لإضافة عناصر تحكم وإجراءات أو إزالتها](compliance-manager-templates-modify.md)
1. [إعداد الاختبار التلقائي لإجراءات التحسين](compliance-manager-setup.md#set-up-automated-testing)
1. [إعادة تعيين إجراءات التحسين إلى مستخدم آخر](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-loss-prevention"></a>منع فقدان البيانات

**حماية البيانات الحساسة**

للامتثال لمعايير الأعمال ولوائح الصناعة، تحتاج المؤسسات إلى حماية المعلومات الحساسة لمنع الكشف غير المقصود. إعداد نهج منع فقدان البيانات لتحديد المعلومات الحساسة ومراقبتها وحمايتها تلقائيا عبر Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>الخطوة 1: [حماية فقدان البيانات على مواقع Teams](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

إذا كانت مؤسستك لديها منع فقدان البيانات (DLP)، يمكنك تحديد النهج التي تمنع الأشخاص من مشاركة المعلومات الحساسة في قناة Microsoft Teams أو جلسة محادثة.

1. تعرف على [ترخيص DLP Microsoft Teams ونطاق حماية DLP](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [إضافة Microsoft Teams كموقع إلى نهج DLP الموجودة](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [تكوين نهج DLP الافتراضي الخاص بنا Teams](mip-easy-trials.md) أو [تحديد نهج DLP جديد Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>الخطوة 2: [حماية فقدان البيانات على مواقع الأجهزة](endpoint-dlp-getting-started.md)

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

تسمح لك DLP لنقطة النهاية من Microsoft بمراقبة أجهزة Windows 10 والكشف عن وقت استخدام العناصر الحساسة ومشاركتها.

1. إعداد نقاط النهاية - تأكد من أن أجهزة Windows 10 وmacOS التي تخطط لنشر DLP لنقطة النهاية [لتلبية هذه المتطلبات](endpoint-dlp-getting-started.md)
1. [إلحاق الأجهزة بإدارة الجهاز](endpoint-dlp-getting-started.md)  - يجب تمكين مراقبة الجهاز وإلحاق نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة وحمايتها على الجهاز. يتم تنفيذ كلا الإجراءين في مدخل التوافق Microsoft 365.
   - السيناريو 1 – [إلحاق الأجهزة](endpoint-dlp-getting-started.md) التي لم يتم إلحاقها بعد.
   - السيناريو 2 - [تم نشر Microsoft Defender لنقطة النهاية بالفعل وهناك نقاط نهاية تقوم بالإبلاغ فيها](endpoint-dlp-getting-started.md). ستظهر كل نقاط النهاية هذه في قائمة الأجهزة المدارة.
1. [تكوين نهج DLP الافتراضي للأجهزة](mip-easy-trials.md#dlp-for-devices) أو [تحديد نهج DLP جديد للأجهزة](endpoint-dlp-learn-about.md).
1. [عرض تنبيهات DLP لنقطة النهاية](dlp-configure-view-alerts-policies.md) في لوحة معلومات إدارة تنبيهات DLP.
1. [عرض بيانات DLP لنقطة النهاية](data-classification-activity-explorer.md) في مستكشف النشاط.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>الخطوة 3: [توسيع النهج في النطاق أو الحماية](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

لديك مرونة في كيفية تكوين نهج DLP الخاصة بك. يمكنك البدء بنهج DLP الافتراضي الخاص بنا Teams والأجهزة وتوسيع هذه النهج لحماية مواقع إضافية أو أنواع معلومات حساسة أو تسميات. بالإضافة إلى ذلك، يمكنك التوسع في إجراءات النهج وتخصيص التنبيه.

1. إضافة مواقع
1. إضافة أنواع معلومات حساسة أو تسميات للحماية
1. إضافة إجراءات
   - Teams:
      - [منع الوصول الخارجي إلى المستندات الحساسة](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [الحصول على تلميحات النهج للمساعدة في تعليم المستخدمين والإرشادات لتخصيص تلميحات النهج](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - الأجهزة: التبديل من التدقيق فقط إلى الحظر
1. [تكوين وعرض التنبيهات لنهج منع فقدان البيانات - Microsoft 365 | التوافق Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>eDiscovery

**اكتشاف المزيد باستخدام سير عمل شامل**

استفد من سير العمل الشامل للحفاظ على المحتوى الذي يستجيب للتحقيقات الداخلية والخارجية لمؤسستك وجمعه وتحليله وتصديره. يمكن للفرق القانونية أيضا إدارة عملية إعلام الاحتجاز القانوني بأكملها من خلال التواصل مع أمناء الحفظ المعنيين بقضية ما.

### <a name="step-1-required-permissions"></a>الخطوة 1 (مطلوبة): [الأذونات](https://aka.ms/ediscoveryninja)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

للوصول إلى Advanced eDiscovery أو إضافته كعضو في حالة Advanced eDiscovery، يجب تعيين الأذونات المناسبة للمستخدم.

1. [إعداد Advanced eDiscovery – تعيين أذونات eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [إضافة أعضاء أو إزالتهم من حالة](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>الخطوة 2 (مطلوبة): إنشاء حالة

> [!TIP]
> أفضل الممارسات التجريبية: إنشاء خلال أول 30 يوما

تستخدم المزيد من المؤسسات الحل Advanced eDiscovery في Microsoft 365 لعمليات eDiscovery الهامة. ويشمل ذلك الاستجابة للطلبات التنظيمية والتحقيقات والتقاضي.

1. إدارة Advanced eDiscovery – [تعرف على كيفية تكوين Advanced eDiscovery وإدارة الحالات باستخدام مركز توافق & الأمان وإدارة سير عمل في Advanced eDiscovery وتحليل نتائج البحث Advanced eDiscovery](/learn/modules/manage-advanced-ediscovery).
1. [إنشاء حالة eDiscovery باستخدام تنسيق الحالة الجديد ل Advance eDiscovery](advanced-ediscovery-new-case-format.md)
1. [إغلاق حالة أو حذفها](close-or-delete-case.md) - عند اكتمال الدعوى القانونية أو التحقيق، يمكنك إغلاقها أو حذفها. يمكنك أيضا إعادة فتح حالة مغلقة.

### <a name="step-3-optional-settings"></a>الخطوة 3 (اختيارية): الإعدادات

للسماح للأشخاص في مؤسستك ببدء إنشاء الحالات واستخدامها، يجب تكوين الإعدادات العمومية التي تنطبق على جميع الحالات في مؤسستك. في هذا الوقت، يكون الإعداد العمومي الوحيد هو **الكشف عن امتيازات الوكيل والعميل** (ستتوفر المزيد من الإعدادات العمومية في المستقبل).

1. [إعداد Advanced eDiscovery – الإعدادات العمومية](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-advanced-ediscovery)
1. [تكوين إعدادات البحث والتحليلات](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [إدارة المهام في Advanced eDiscovery](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>الخطوة 4 (اختيارية): [حدود التوافق](set-up-compliance-boundaries.md)

تنشئ حدود التوافق حدودا منطقية داخل مؤسسة تتحكم في مواقع محتوى المستخدم (مثل علب البريد وحسابات OneDrive ومواقع SharePoint) التي يمكن لمديري eDiscovery البحث فيها. كما يتحكمون في الأشخاص الذين يمكنهم الوصول إلى حالات eDiscovery المستخدمة لإدارة التحقيقات القانونية أو البشرية أو التحقيقات الأخرى داخل مؤسستك.

![تتكون حدود التوافق من عوامل تصفية أذونات البحث التي تتحكم في الوصول إلى الوكالات ومجموعات أدوار المسؤول التي تتحكم في الوصول إلى حالات eDiscovery.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

إعداد حدود التوافق لتحقيقات eDiscovery:

1. [تحديد سمة مستخدم لتعريف الوكالات الخاصة بك](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [إنشاء مجموعة أدوار لكل وكالة](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [إنشاء عامل تصفية أذونات بحث لفرض حد التوافق](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [إنشاء حالة eDiscovery للتحقيقات داخل الوكالة](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>الخطوة 5 (اختيارية): [التعرف على أداة البحث في المحتوى](search-for-content.md)

استخدم أداة البحث عن المحتوى في مركز التوافق في Microsoft 365 للعثور بسرعة على البريد الإلكتروني في علب بريد Exchange والمستندات في مواقع SharePoint ومواقع OneDrive ومحادثات المراسلة الفورية في Skype for Business. يمكنك استخدام أداة البحث عن المحتوى للبحث عن رسائل البريد الإلكتروني والمستندات ومحادثات المراسلة الفورية في أدوات التعاون مثل Microsoft Teams مجموعات Microsoft 365.

- [معرفة المزيد حول Advanced eDiscovery البحث](search-for-content.md#search-for-content)

## <a name="information-protection"></a>حماية البيانات

**اكتشاف المعلومات الحساسة وتصنيفها وحمايتها**

نفذ تسميات حماية البيانات في Microsoft والحساسية، لمساعدتك على اكتشاف المحتوى الحساس وتصنيفه وحمايته أينما كان يقيم أو ينتقل.

### <a name="step-1-start-your-information-protection-trial"></a>الخطوة 1: [بدء الإصدار التجريبي لحماية المعلومات](mip-easy-trials.md)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

يمكن للعملاء المؤهلين تنشيط التسميات والنهج الافتراضية حماية البيانات في Microsoft. عند تمكين التكوين الافتراضي في الإصدار التجريبي، سيستغرق تكوين جميع النهج للمستأجر الخاص بك حوالي دقيقتين وما يصل إلى 24 ساعة لمشاهدة نتائج هذه النهج الافتراضية.

اختيار التكوين الافتراضي، بنقرة واحدة، يتم تكوين ما يلي تلقائيا:

- تسميات الحساسية ونهج وصف الحساسية
- التسمية التلقائية من جانب العميل
- التسمية التلقائية من جانب الخدمة
- نهج منع فقدان البيانات (DLP) Teams والأجهزة

[تنشيط التسميات والنهج الافتراضية](mip-easy-trials.md#activate-the-default-labels-and-policies). إذا لزم الأمر، يمكنك التحرير يدويا بعد اكتمال التكوين.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>الخطوة 2: [تطبيق أوصاف الحساسية تلقائيا على المستندات](apply-sensitivity-label-automatically.md)

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

عند إنشاء وصف حساسية، يمكنك تعيين هذه التسمية تلقائيا إلى الملفات ورسائل البريد الإلكتروني عندما يتطابق مع الشروط التي تحددها.

1. [إنشاء أوصاف الحساسية وتكوينها](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [نشر نهج وصف الحساسية لجميع المستخدمين](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [إنشاء نهج تسمية تلقائية](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - اختر المعلومات التي تريد تطبيق التسمية عليها
   - تعريف المواقع لتطبيق التسمية
   - تحديد تسمية لتطبيقها
   - [تشغيل النهج في وضع المحاكاة](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![تكوين نهج جديد للتسمية التلقائية.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>الخطوة 3: [مراجعة نهج التسمية التلقائية وتشغيله](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

الآن في صفحة **"Information** **protectionAuto-labeling** > "، سترى نهج التسمية التلقائية في قسم **المحاكاة**.

حدد النهج الخاص بك للاطلاع على تفاصيل التكوين والحالة. عند اكتمال المحاكاة، حدد علامة التبويب "العناصر" لمراجعتها لمعرفة رسائل البريد الإلكتروني أو المستندات التي تطابق القواعد المحددة.

عندما تكون مستعدا لتشغيل النهج دون محاكاة، حدد خيار **تشغيل النهج** .

## <a name="insider-risk-management"></a>Insider Risk Management

**الكشف عن المخاطر الداخلية ومعالجتها**

استفد من الذكاء الاصطناعي لمساعدتك على تحديد المخاطر الداخلية وفرزها ومعالجتها بسرعة. باستخدام سجلات من Microsoft 365 وخدمات Azure، يمكنك تحديد النهج التي تراقب إشارات المخاطر الداخلية، ثم اتخاذ إجراءات المعالجة مثل تعزيز تعليم المستخدم أو بدء التحقيق.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>الخطوة 1 (مطلوبة): [تمكين الأذونات لإدارة المخاطر الداخلية](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

هناك أربع مجموعات أدوار تستخدم لتكوين الأذونات لإدارة ميزات إدارة المخاطر الداخلية.

[إضافة مستخدمين إلى مجموعة دور إدارة المخاطر الداخلية.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

إذا لم تتمكن من رؤية الأذونات، فالرجاء التحدث إلى مسؤول المستأجر لتعيين الأدوار الصحيحة.

### <a name="step-2-start-with-user-quick-start-guide"></a>الخطوة 2: [البدء بدليل البدء السريع للمستخدم](insider-risk-management-configure.md#recommended-actions-preview)

ابدأ بسرعة واحصل على أقصى استفادة من قدرات إدارة المخاطر الداخلية مع الإجراءات الموصى بها. تساعدك الإجراءات الموصى بها، المضمنة في صفحة النظرة العامة، على إرشادك خلال الخطوات اللازمة لتكوين النهج ونشرها واتخاذ إجراءات التحقيق لإجراءات المستخدم التي تنشئ تنبيهات من تطابقات النهج.

[حدد توصية من القائمة](insider-risk-management-configure.md#recommended-actions-preview) لبدء تكوين إدارة المخاطر الداخلية.

![الإجراءات الموصى بها لإدارة المخاطر من الداخل.](../media/insider-risk-recommended-actions.png)

يرشدك كل إجراء موصى به خلال الأنشطة المطلوبة للتوصية، بما في ذلك أي متطلبات وما يجب توقعه وتأثير تكوين الميزة في مؤسستك.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>الخطوة 3 (مطلوبة): [تمكين سجل تدقيق Microsoft 365](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

يتم تمكين التدقيق للمؤسسات Microsoft 365 بشكل افتراضي. قد تكون بعض المؤسسات قد عطلت التدقيق لأسباب محددة. إذا تم تعطيل التدقيق لمؤسستك، فقد يرجع ذلك إلى إيقاف تشغيل مسؤول آخر. نوصي بالتأكيد على أنه لا بأس من إعادة تشغيل التدقيق عند إكمال هذه الخطوة.

للحصول على إرشادات مفصلة خطوة بخطوة لتشغيل التدقيق، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md). بعد تشغيل التدقيق، يتم عرض رسالة تفيد بأنه يتم إعداد سجل التدقيق وأنه يمكنك إجراء بحث بعد ساعتين من اكتمال الإعداد. يجب عليك القيام بهذا الإجراء مرة واحدة فقط. لمزيد من المعلومات حول استخدام سجل التدقيق Microsoft 365، راجع [البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>الخطوة 4 (مطلوبة): [تمكين تحليلات المخاطر الداخلية وعرضها](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

تمكنك تحليلات إدارة المخاطر الداخلية من إجراء تقييم للمخاطر الداخلية المحتملة في مؤسستك دون تكوين أي نهج مخاطر من الداخل. قد تستغرق نتائج فحص التحليلات ما يصل إلى 48 ساعة قبل توفر نتائج التحليلات كتقارير للمراجعة. لمعرفة المزيد حول تحليلات التحليلات، راجع [إعدادات إدارة المخاطر ل Insider: التحليلات (معاينة)](insider-risk-management-settings.md) والاطلاع على [فيديو Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) لمساعدتك على فهم وضع المخاطر الداخلية ومساعدتك على اتخاذ إجراء من خلال إعداد النهج المناسبة لتحديد المستخدمين المعرضين للمخاطر.

لتمكين Insider risk Analytics، يجب أن تكون عضوا في Insider Risk Management أو Insider Risk Management Admin. [أكمل هذه الخطوات لتمكين تحليلات المخاطر الداخلية](insider-risk-management-configure.md).

## <a name="records-management"></a>إدارة التسجيلات

**أتمتة جدول الاستبقاء للسجلات الهامة للأعمال**

استخدم ميزات إدارة السجلات المتكاملة لأتمتة جدول الاستبقاء للسجلات التنظيمية القانونية والسجلات الهامة للأعمال. احصل على دعم دورة حياة المحتوى الكامل، من الإنشاء إلى التعاون، وإعلان السجل، والاستبقاء، والتصرف.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>الخطوة 1: استهداف نهج الاستبقاء ديناميكيا باستخدام نطاقات النهج التكيفي

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

تسمح لك نطاقات النهج التكيفية باستهداف نهج بشكل ديناميكي لبعض المستخدمين أو المجموعات أو المواقع استنادا إلى سمات AD الخاصة بهم.

يمكن تحديد سمات النطاقات من قائمة أو تخصيصها باستخدام منشئ استعلام متقدم.

تبقى النهج التي تستخدم نطاقات النهج التكيفية محدثة مع تغير المؤسسة مع انضمام موظفين جدد أو مغادرتهم. بالإضافة إلى ذلك، فإنها لا تخضع للحدود السابقة البالغة 100/1000 موقع مضمنة في النهج.

- إنشاء [نطاق نهج موائم](retention.md#adaptive-or-static-policy-scopes-for-retention)، واستخدامه مع نهج الاستبقاء

### <a name="step-2-automate-labeling-of-sensitive-information-with-the-ability-to-review-before-disposal"></a>الخطوة 2: أتمتة تسمية المعلومات الحساسة مع القدرة على المراجعة قبل التخلص منها

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

يمكن إعداد تسميات الاستبقاء لتطبيقها تلقائيا على المحتوى عندما تكتشف معلومات حساسة، مثل رقم بطاقة الائتمان. يؤدي ذلك إلى إزالة حاجة المستخدمين إلى تنفيذ نشاط التسمية يدويا.

في نهاية فترة الاستبقاء، سيتم إعلام المستخدمين الذين تحددهم ("المراجعون") لمراجعة المحتوى والموافقة على إجراء التخلص الدائم. وبهذه الطريقة إذا كان هناك شيء ما يحتاج إلى الاحتفاظ به لفترة أطول، فإنه يمكن أن يكون كذلك.

يمكن عرض كل من نشاط تطبيق التسمية ونشاط مراجعة الترتيب على شاشة نظرة عامة على إدارة السجلات.

1. [تطبيق تسميات الاستبقاء تلقائيا على المحتوى الذي يحتوي على معلومات حساسة](retention.md#retention-labels)
1. إنشاء تسمية استبقاء وتطبيقها مع [مراجعة الترتيب](disposition.md#disposition-reviews) في نهاية فترة الاستبقاء

### <a name="step-3-label-content-as-records-automatically-using-trainable-classifiers"></a>الخطوة 3: تسمية المحتوى كسجلات تلقائيا باستخدام المصنفات القابلة للتدريب

عند الإعلان عن المحتوى كسجل، يتم وضع قيود على العنصر من حيث الإجراءات المسموح بها أو المحظورة، ويتم تسجيل أنشطة إضافية حول العناصر، ويكون لديك إثبات التصرف إذا تم حذف العناصر في نهاية فترة الاستبقاء الخاصة بها.

المصنفات القابلة للتدريب هي أدوات تتعرف على أنواع مختلفة من المحتوى، استنادا إلى العينات التي تم تقديمها. اختر من بين مجموعة متنوعة من الخيارات المضمنة أو قم بإعداد مصنف مخصص لتلبية احتياجاتك المحددة.

1. إنشاء تسمية استبقاء [تعلن عن المحتوى كسجل أو سجل تنظيمي](records-management.md#records)
1. [تطبيق تسميات الاستبقاء تلقائيا على المحتوى باستخدام مصنفات قابلة للتدريب](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

### <a name="more-information-auto-apply-retention-labels--disposition-review"></a>مزيد من المعلومات: تطبيق تسميات الاستبقاء تلقائيا + مراجعة الترتيب

**تطبيق التسميات تلقائيا للاحتفاظ بما تحتاجه...** يمكن تطبيق تسميات الاستبقاء تلقائيا على المحتوى عندما يحتوي على:

- [أنواع معينة من المعلومات الحساسة](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)
- [كلمات أساسية معينة أو خصائص قابلة للبحث تتطابق مع استعلام تقوم بإنشائه](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [مطابقة للمصنفات القابلة للتدريب](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

**... ثم تخلص منه بأمان في النهاية.**

عند تشغيل مراجعة الترتيب في نهاية فترة الاستبقاء، يتلقى المراجعون الذين تختارهم إعلاما بالبريد الإلكتروني بأن لديهم محتوى لمراجعته.

لا يتم حذف المحتوى الذي ينتظر مراجعة الترتيب نهائيا إلا بعد أن يختار المراجع للمرحلة النهائية من الترتيب حذف المحتوى نهائيا.

## <a name="additional-trials-and-add-ons"></a>الإصدارات التجريبية الإضافية والوظائف الإضافية

### <a name="compliance-manager-premium-assessments"></a>تقييمات متميزة ل Compliance Manager

**تقييم المخاطر والاستجابة بكفاءة**

ساعد مؤسستك على تقييم المخاطر والاستجابة بكفاءة للمتطلبات الإقليمية ومتطلبات الصناعة التي تحكم جمع البيانات واستخدامها.

[مزيد من المعلومات حول إصدار التقييمات المتميزة ل Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

[دليل المبادئ التجريبي: التقييمات المتميزة ل Microsoft Compliance Manager](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Microsoft Priva Privacy Risk Management وطلبات حقوق موضوع Microsoft Priva

**تحديد & منع مخاطر الخصوصية**

تحديد مخاطر الخصوصية وحمايتها بشكل استباقي مثل تخزين البيانات ونقل البيانات والإفراط في المشاركة في البيانات ومساعدة مؤسستك على أتمتة طلبات الموضوع وإدارتها على نطاق واسع.

[تعرف على المزيد حول Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management).

[دليل المبادئ التجريبي: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>موارد إضافية

**ما هو مضمن**: للحصول على قائمة كاملة من حلول التوافق Microsoft 365 والميزات المدرجة حسب مستوى المنتج، اعرض [مصفوفة الميزة](https://go.microsoft.com/fwlink/?linkid=2139145).

**مكتبة المحتويات التقنية للأمان من Microsoft**: استكشف هذه المكتبة للعثور على إرشادات تفاعلية ومحتوى تعليمي آخر ذي صلة باحتياجاتك. [تفضل بزيارة المكتبة](/security).

**موارد أمان Microsoft**: من مكافحة البرامج الضارة إلى ثقة معدومة، احصل على جميع الموارد ذات الصلة لاحتياجات أمان مؤسستك. [قم بزيارة الموارد](/security/business/resources).
