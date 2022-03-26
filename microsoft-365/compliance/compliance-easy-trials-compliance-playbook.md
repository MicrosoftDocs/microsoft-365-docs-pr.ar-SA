---
title: Microsoft 365 الإصدار التجريبي لحلول التوافق
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
description: Microsoft 365 الإصدار التجريبي لحلول التوافق.
ms.openlocfilehash: 896e3fe81c74cc2a594ab88807e0b9505fed1a18
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754260"
---
# <a name="trial-playbook-microsoft-365-compliance-solutions"></a>دليل التشغيل التجريبي: Microsoft 365 التوافق

مرحبا بك في Microsoft 365 الإصدار التجريبي لحلول التوافق. سيساعدك هذا المصنف على الاستفادة إلى أفضل مدى من الإصدار التجريبي المجاني الذي لمدة 90 يوما من خلال مساعدتك على اكتشاف قدرات قوية وشاملة Microsoft 365 منتجات الأمان والتوافق.

سيساعدك تجربة كل حل على اتخاذ قرارات مخبرة لتلبية احتياجات توافق مؤسستك.

الميزات:

- [التدقيق المتقدم](#advanced-audit)
- [توافق الاتصالات](#communication-compliance)
- [إدارة التوافق](#compliance-manager)
- [منع فقدان البيانات](#data-loss-prevention)
- [eDiscovery](#ediscovery)
- [حماية المعلومات](#information-protection)
- [إدارة مخاطر Insider](#insider-risk-management)
- [إدارة التسجيلات](#records-management)

الوظائف الإضافية الاختيارية:

- [التقييمات المتميزة لمدير التوافق](#compliance-manager-premium-assessments)
- [Microsoft Priva Privacy Risk Management و Microsoft Priva Subject Rights Requests](#microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests)

## <a name="compliance-actions-with-microsoft-365"></a>إجراءات التوافق مع Microsoft 365

ابدأ بسهولة وسرعة تجربة حلول التوافق من Microsoft دون تغيير بيانات التعريف الخاصة مؤسستك. استنادا إلى أولوياتك، يمكنك البدء بأي من مناطق الحلول هذه لرؤية القيمة الفورية. فيما يلي خمسة أهم المشاكل التنظيمية كما هو موصى به من قبل عملائنا والحلول الموصى بها للبدء بها.

:::image type="content" source="../media/compliance-trial/workflow.png" alt-text="إجراءات التوافق مع Microsoft 365":::

## <a name="advanced-audit"></a>التدقيق المتقدم

**إجراء عمليات التحقيق**

تساعد "التدقيق المتقدم" المؤسسات على إجراء التحريات التحليلية والتوافقية من خلال زيادة استبقاء سجل التدقيق المطلوب لإجراء تحقيق، وتوفير الوصول إلى الأحداث الأكثر أهمية التي تساعد على تحديد نطاق اختراق، وتوفير وصول أسرع إلى Office 365 API لنشاط الإدارة.

### <a name="step-1-apply-the-e5-license-to-each-user-for-which-youd-like-to-generate-e5-events"></a>الخطوة 1: [تطبيق ترخيص E5 على كل](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users) مستخدم تريد إنشاء أحداث E5 له

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

تتطلب ميزات التدقيق المتقدمة مثل القدرة على تسجيل الأحداث المهمة مثل MailItemsAccessed وSed send ترخيص E5 مناسب تم تعيينه للمستخدمين. بالإضافة إلى ذلك، يجب تمكين خطة الخدمة/تطبيق التدقيق المتقدم لهؤلاء المستخدمين.

إعداد التدقيق المتقدم للمستخدمين - للتحقق من تعيين تطبيق التدقيق المتقدم للمستخدمين، قم بتنفيذ [الخطوات التالية لكل مستخدم](set-up-advanced-audit.md#step-1-set-up-advanced-audit-for-users).

1. تمكين أحداث التدقيق المتقدم - تمكين [SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint](set-up-advanced-audit.md#step-2-enable-advanced-audit-events) لتدقيقها لكل مستخدم [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
1. إعداد سياسات استبقاء التدقيق - [أنشئ](set-up-advanced-audit.md#step-3-set-up-audit-retention-policies) المزيد من سياسات استبقاء سجل التدقيق لتلبية متطلبات عمليات الأمان في مؤسستك وفرق المعلومات والتوافق.
1. البحث عن أحداث التدقيق المتقدم - ابحث [عن أحداث التدقيق](set-up-advanced-audit.md#step-4-search-for-advanced-audit-events) المتقدم والأنشطة الأخرى عند إجراء التحريات التحليلية.

### <a name="step-2-create-new-audit-log-policies-to-specify-how-long-to-retain-audit-logs-in-your-org-for-activities-performed-by-users-and-define-priority-levels-for-your-policies"></a>الخطوة 2: إنشاء سياسات سجل تدقيق جديدة لتحديد المدة التي يجب فيها الاحتفاظ بسجلات التدقيق في المؤسسة الخاصة بالأنشطة التي يقوم بها المستخدمون وتحديد مستويات الأولوية [لنهجك](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy)

> [!TIP]
> أفضل الممارسات التجريبية: إنشاء خلال أول 30 يوما

إن سياسات استبقاء سجل التدقيق هي جزء من قدرات التدقيق المتقدم الجديدة في Microsoft 365. يتيح لك نهج استبقاء سجل التدقيق تحديد المدة التي يجب فيها الاحتفاظ بسجلات التدقيق في مؤسستك.

1. قبل إنشاء نهج استبقاء سجل تدقيق – [أشياء أساسية يجب معرفتها](audit-log-retention-policies.md#before-you-create-an-audit-log-retention-policy) قبل إنشاء النهج.
1. [إنشاء نهج استبقاء سجل تدقيق](audit-log-retention-policies.md#create-an-audit-log-retention-policy)
1. [إدارة سياسات استبقاء](audit-log-retention-policies.md#manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center) سجل التدقيق في مركز التوافق في Microsoft 365 - يتم سرد سياسات استبقاء سجل التدقيق ضمن علامة التبويب سياسات استبقاء التدقيق (تسمى أيضا لوحة المعلومات). يمكنك استخدام لوحة المعلومات لعرض سياسات استبقاء التدقيق وتحريرها وحذفها.
1. إنشاء سياسات استبقاء سجل التدقيق وإدارتها في PowerShell - يمكنك أيضا استخدام & مركز التوافق PowerShell لإنشاء سياسات استبقاء سجل التدقيق [وإدارتها](audit-log-retention-policies.md#create-and-manage-audit-log-retention-policies-in-powershell). أحد أسباب استخدام PowerShell هو إنشاء نهج لنوع سجل أو نشاط غير متوفر في واجهة المستخدم.

## <a name="communication-compliance"></a>توافق الاتصالات

**تحديد انتهاكات نهج قواعد السلوك والتصرف بشأنها**

يساعدك توافق الاتصالات على التعرف على انتهاكات الاتصالات بشكل ذكي لدعم بيئة عمل متوافقة وسليمة من خلال مساعدتك على الكشف عن الرسائل غير المناسبة، التحقيق في الانتهاكات المحتملة للسياسة، واتخاذ الخطوات اللازمة لإعادة المعالجة.

### <a name="step-1-enable-permissions-for-communication-compliance"></a>الخطوة 1: [تمكين الأذونات لتوافق الاتصالات](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

[تعيين جميع مستخدمي التوافق إلى مجموعة دور توافق الاتصالات](communication-compliance-configure.md#step-1-required-enable-permissions-for-communication-compliance).
### <a name="step-2-enable-the-audit-log"></a>الخطوة 2: [تمكين سجل التدقيق](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

لاستخدام هذه الميزة، قم تشغيل التدقيق حتى تتمكن مؤسستك من بدء تسجيل نشاط المستخدم والمسؤول في مؤسستك. عند تشغيل هذا، سيتم تسجيل النشاط في سجل التدقيق وسيتوفر لعرضه في تقرير. لمعرفة المزيد، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md).

### <a name="step-3-create-a-communication-compliance-policy"></a>الخطوة 3: [إنشاء نهج لتوافق الاتصالات](communication-compliance-policies.md)

[إنشاء نهج توافق الاتصالات باستخدام القوالب الموجودة](communication-compliance-policies.md): 1- المحتوى غير المناسب؛ 2- المعلومات الحساسة؛ 3- التوافق التنظيمي؛ 4- تعارض الاهتمامات.

### <a name="step-4-investigate-and-remediate-alerts"></a>الخطوة 4: [التحقق من التنبيهات و إصلاحها](communication-compliance-investigate-remediate.md)

[التحقق من تنبيهات](communication-compliance-investigate-remediate.md) توافق الاتصالات و إصلاحها.

## <a name="compliance-manager"></a>إدارة التوافق

**إدارة توافق المؤسسة بسهولة**

يمكن أن تساعدك إدارة التوافق خلال رحلة التوافق، من جرد مخاطر حماية البيانات إلى إدارة تعقيدات تنفيذ عناصر التحكم، والبقاء على اتم المعلومات مع اللوائح والشهادات، وإعداد التقارير للمراجعين.

### <a name="step-1-get-to-know-compliance-manager"></a>الخطوة 1: [تعرف على إدارة التوافق](compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

صفحة نظرة عامة حول إدارة التوافق هي أفضل محطة أولى للمراجعة الشاملة لمدير التوافق وكيفية عمله. قد ترغب أيضا في الانتقال مباشرة إلى المقاطع الرئيسية من وثائقنا باستخدام الارتباطات أدناه:

- [فهم نقاط التوافق](compliance-manager.md#understanding-your-compliance-score)
- [نظرة عامة على العناصر الأساسية: عناصر التحكم والتقييمات والقوالب والإجراءات الخاصة بالتحسين](compliance-manager.md#key-elements-controls-assessments-templates-improvement-actions)
- [فهم لوحة معلومات إدارة التوافق](compliance-manager-setup.md#understand-the-compliance-manager-dashboard)
- [تصفية طريقة عرض لوحة المعلومات](compliance-manager-setup.md#filtering-your-dashboard-view)
- [التعرف على إجراءات التحسين](compliance-manager-setup.md#improvement-actions-page)
- [فهم التقييمات](compliance-manager.md#assessments)
- [إجراء فحص سريع لبيئة باستخدام إدارة تكوين التوافق من Microsoft](compliance-manager-mcca.md)

![إدارة التوافق - لوحة المعلومات.](../media/compliance-manager-dashboard.png "لوحة معلومات إدارة التوافق")

### <a name="step-2-configure-compliance-manager-to-manage-your-compliance-activities"></a>الخطوة 2: [تكوين إدارة التوافق لإدارة أنشطة التوافق](compliance-manager-assessments.md)

> [!TIP]
> أفضل الممارسات التجريبية: فحص خلال أول 30 يوما

ابدأ العمل باستخدام التقييمات واعمل على تنفيذ إجراءات التحسين لتطبيق عناصر التحكم وتحسين درجة التوافق.

1. [اختر قالبا تم إنشاؤه مسبقا لإنشاء التقييم الأول وإدارته](compliance-manager-assessments.md).
1. [فهم كيفية استخدام القوالب لإنشاء التقييمات](compliance-manager-templates.md).
1. [تنفيذ العمل واختباره على إجراءات التحسين لإكمال عناصر التحكم في التقييمات](compliance-manager-improvement-actions.md).
1. [فهم أفضل لكيفية تأثير الإجراءات المختلفة على نقاط التوافق](compliance-score-calculation.md).

> [!NOTE]
> Microsoft 365 أو Office 365 E1/E3 قالب أساسي لحماية البيانات من Microsoft. Microsoft 365 أو Office 365 E5، يتضمن توافق E5 قوالب ل:
>
> - الأساس لحماية البيانات من Microsoft
> - GDPR في الاتحاد الأوروبي  
> - ISO/IEC 27001،
> - NIST 800-53
>
> تتضمن إدارة التوافق أكثر من 300 قالب تنظيمي أو قوالب متميزة يمكن شراؤها كعنود إضافي. راجع القائمة هنا. مع أي قوالب متميزة (مضمنة مع اشتراكك أو تم شراؤها كعنود إضافي) ستتلقى الإصدار العام من هذه القوالب، مما يسمح لك بإدارة توافقك مع أي منتج أو خدمة

### <a name="step-3-scaling-up-use-advanced-functionality-to-meet-your-custom-needs"></a>الخطوة 3: زيادة حجم التطبيق [: استخدام الوظائف المتقدمة لتلبية احتياجاتك المخصصة](compliance-manager-templates-create.md)

التقييمات المخصصة مفيدة ل:

- إدارة التوافق للمنتجات غير Microsoft 365 مثل التطبيقات والخدمات الخاصة ب جهة خارجية والتطبيقات المحلية وأصول أخرى
- إدارة عناصر التحكم بالتوافق المخصصة أو الخاصة بأعمالك

1. [توسيع قالب إدارة التوافق عن طريق إضافة عناصر التحكم الخاصة بك والإجراءات التحسين الخاصة بك](compliance-manager-templates-extend.md)
1. [إنشاء قالب مخصص خاص بك](compliance-manager-templates-create.md)
1. [تعديل قالب موجود لإضافة عناصر التحكم والإجراءات أو إزالتها](compliance-manager-templates-modify.md)
1. [إعداد الاختبار التلقائي لأفعال التحسين](compliance-manager-setup.md#set-up-automated-testing)
1. [إعادة تعيين إجراءات التحسين إلى مستخدم آخر](compliance-manager-setup.md#reassign-improvement-actions-to-another-user)

## <a name="data-loss-prevention"></a>منع فقدان البيانات

**حماية البيانات الحساسة**

للامتثال لمعايير العمل وأنظمة الصناعة، تحتاج المؤسسات إلى حماية المعلومات الحساسة لمنع الكشف عنها عن غير قصد. قم بإعداد سياسات منع فقدان البيانات لتحديد المعلومات الحساسة ومراقبتها وحمايتها تلقائيا عبر Microsoft 365.

### <a name="step-1-protect-data-loss-on-teams-locations"></a>الخطوة 1: [حماية فقدان البيانات على Teams المواقع](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

إذا كانت مؤسستك لديها منع فقدان البيانات (DLP)، يمكنك تعريف سياسات تمنع الأشخاص من مشاركة المعلومات الحساسة في قناة Microsoft Teams أو جلسة محادثة.

1. تعرف على [ترخيص DLP Microsoft Teams ونطاق حماية DLP](dlp-microsoft-teams.md#dlp-licensing-for-microsoft-teams)
1. [إضافة Microsoft Teams كم موقع إلى سياسات DLP الموجودة](dlp-microsoft-teams.md#add-microsoft-teams-as-a-location-to-existing-dlp-policies)
1. [تكوين نهج DLP الافتراضي](mip-easy-trials.md) Teams [تعريف نهج DLP جديد Microsoft Teams](dlp-microsoft-teams.md#define-a-new-dlp-policy-for-microsoft-teams)

### <a name="step-2-protect-data-loss-on-device-locations"></a>الخطوة 2: [حماية فقدان البيانات على مواقع الأجهزة](endpoint-dlp-getting-started.md)

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

تسمح لك Microsoft Endpoint DLP بمراقبة أجهزة Windows 10 والكشف عن وقت استخدام العناصر الحساسة ومشاركتها.

1. إعداد نقاط النهاية - تأكد من أن أجهزة Windows 10 و macOS التي تخطط لنشر DLP لنقطة النهاية لتلبية [هذه المتطلبات](endpoint-dlp-getting-started.md)
1. [الأجهزة المجهزة في إدارة](endpoint-dlp-getting-started.md)  الأجهزة - يجب تمكين مراقبة الجهاز وتكوين نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة على جهاز وحمايتها. يتم كلا هذين الإجراءات في مدخل Microsoft 365 التوافق.
   - السيناريو 1 – [الأجهزة التي لم](endpoint-dlp-getting-started.md) يتم اجهزتها بعد.
   - السيناريو 2 - [تم نشر Microsoft Defender لنقطة النهاية بالفعل وتوجد نقاط نهاية يتم فيها إعداد التقارير](endpoint-dlp-getting-started.md). ستظهر كل نقاط النهاية هذه في قائمة الأجهزة المدارة.
1. [تكوين نهج DLP الافتراضي للأجهزة](mip-easy-trials.md#dlp-for-devices) أو [تعريف نهج DLP جديد للأجهزة](endpoint-dlp-learn-about.md).
1. [عرض تنبيهات DLP لنقطة](dlp-configure-view-alerts-policies.md) النهاية في لوحة معلومات إدارة تنبيهات DLP.
1. [عرض بيانات DLP لنقطة النهاية](data-classification-activity-explorer.md) في مستكشف النشاط.

### <a name="step-3-expand-policies-in-scope-or-protection"></a>الخطوة 3: [توسيع السياسات في النطاق أو الحماية](dlp-learn-about-dlp.md#dlp-policy-configuration-overview)

تتمتع بالمرونة في كيفية تكوين سياسات DLP. يمكنك البدء باستخدام نهج DLP الافتراضي Teams والأجهزة وتوسيع هذه النهج لحماية المواقع أو أنواع المعلومات الحساسة أو التسميات الإضافية. بالإضافة إلى ذلك، يمكنك توسيع إجراءات النهج وتخصيص التنبيه.

1. إضافة مواقع
1. إضافة أنواع أو تسميات معلومات حساسة لحمايتها
1. إضافة إجراءات
   - Teams:
      - [منع الوصول الخارجي إلى المستندات الحساسة](dlp-microsoft-teams.md#prevent-external-access-to-sensitive-documents)
      - [الحصول على تلميحات النهج للمساعدة في تعليم المستخدمين وإرشادات لتخصيص تلميحات النهج](dlp-microsoft-teams.md#policy-tips-help-educate-users)
   - الأجهزة: التبديل من التدقيق إلى الحظر فقط
1. [تكوين التنبيهات وعرضها لنهج منع فقدان البيانات - Microsoft 365 التوافق | Microsoft Docs](dlp-configure-view-alerts-policies.md)

## <a name="ediscovery"></a>eDiscovery

**اكتشاف المزيد باستخدام سير عمل من نهاية إلى نهاية**

استفد من سير عمل شامل للحفاظ على المحتوى المستجيب للتباحثات الداخلية والخارجية في مؤسستك وجمعه وتحليله وتصديره. يمكن للفرق القانونية أيضا إدارة عملية إعلام الاحتجاز القانوني بالكامل من خلال التواصل مع اطباء الوصاية المشاركين في قضية ما.

### <a name="step-1-required-permissions"></a>الخطوة 1 (مطلوبة): [الأذونات](https://aka.ms/ediscoveryninja)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

للوصول إلى Advanced eDiscovery أو إضافته كعضو في Advanced eDiscovery، يجب أن يتم تعيين الأذونات المناسبة للمستخدم.

1. [إعداد Advanced eDiscovery – تعيين أذونات eDiscovery](get-started-with-advanced-ediscovery.md#step-2-assign-ediscovery-permissions)
1. [إضافة أعضاء أو إزالتهم من حالة](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

### <a name="step-2-required-create-a-case"></a>الخطوة 2 (مطلوب): إنشاء حالة

> [!TIP]
> أفضل الممارسات التجريبية: إنشاء خلال أول 30 يوما

يستخدم المزيد من المؤسسات Advanced eDiscovery في Microsoft 365 لعمليات eDiscovery الهامة. يشمل ذلك الاستجابة للطلبات التنظيمية، التحقيق، والدعاوى القضائية.

1. إدارة Advanced eDiscovery – تعرف على كيفية تكوين Advanced eDiscovery، وإدارة الحالات باستخدام مركز توافق الأمان &، وإدارة سير عمل في Advanced eDiscovery، وتحليل Advanced eDiscovery [البحث](/learn/modules/manage-advanced-ediscovery).
1. [إنشاء حالة eDiscovery باستخدام تنسيق حالة eDiscovery الجديد](advanced-ediscovery-new-case-format.md)
1. [إغلاق حالة أو حذفها](close-or-delete-case.md) - عند اكتمال الدعوى القانونية أو التحقيق، يمكنك إغلاقها أو حذفها. يمكنك أيضا إعادة فتح حالة مغلقة.

### <a name="step-3-optional-settings"></a>الخطوة 3 (اختيارية): الإعدادات

للسماح للأشخاص في مؤسستك ببدء إنشاء حالات واستخدامها، يجب تكوين الإعدادات العالمية التي تنطبق على كل الحالات في مؤسستك. في الوقت نفسه، يكون الإعداد العام الوحيد هو الكشف عن امتيازات المحامي **والعميل** (سيتوفر المزيد من الإعدادات العامة في المستقبل).

1. [إعداد Advanced eDiscovery – الإعدادات](get-started-with-advanced-ediscovery.md#step-3-configure-global-settings-for-advanced-ediscovery)
1. [تكوين إعدادات البحث والتحليلات](configure-search-and-analytics-settings-in-advanced-ediscovery.md)
1. [إدارة المهام في Advanced eDiscovery](managing-jobs-ediscovery20.md)

### <a name="step-4-optional-compliance-boundaries"></a>الخطوة 4 (اختيارية): [حدود التوافق](set-up-compliance-boundaries.md)

تنشئ حدود التوافق حدودا منطقية داخل مؤسسة تتحكم في مواقع محتوى المستخدم (مثل علب البريد وحسابات OneDrive ومواقع SharePoint) التي يمكن لمديري eDiscovery البحث فيها. كما تتحكم أيضا في الأشخاص الذين يمكنهم الوصول إلى حالات eDiscovery المستخدمة لإدارة عمليات التحقيق القانونية أو الموارد البشرية أو أي تحقيق آخر داخل مؤسستك.

![تتكون حدود التوافق من عوامل تصفية أذونات البحث التي تتحكم في الوصول إلى الوكالات ومجموعات دور المسؤول التي تتحكم في الوصول إلى حالات eDiscovery.](../media/M365_ComplianceBoundary_OrgChart_v2.png)

إعداد حدود التوافق لتحريات eDiscovery:

1. [تحديد سمة مستخدم لتعريف الوكالات](set-up-compliance-boundaries.md#step-1-identify-a-user-attribute-to-define-your-agencies)
1. [إنشاء مجموعة دور لكل وكالة](set-up-compliance-boundaries.md#step-2-create-a-role-group-for-each-agency)
1. [إنشاء عامل تصفية أذونات البحث لفرض حد التوافق](set-up-compliance-boundaries.md#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)
1. [إنشاء حالة eDiscovery لتحريات داخل الوكالة](set-up-compliance-boundaries.md#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

### <a name="step-5-optional-learn-about-content-search-tool"></a>الخطوة 5 (اختيارية): [التعرف على أداة البحث في المحتوى](search-for-content.md)

استخدم أداة البحث في المحتوى في مركز التوافق في Microsoft 365 للعثور بسرعة على البريد الإلكتروني في علب بريد Exchange والمستندات في مواقع SharePoint ومواقع OneDrive ومحادثات المراسلة الفورية في Skype for Business. يمكنك استخدام أداة البحث في المحتوى للبحث عن البريد الإلكتروني والمستندات ومحادثات المراسلة الفورية في أدوات التعاون مثل Microsoft Teams Microsoft 365 المجموعات.

- [معرفة المزيد حول Advanced eDiscovery البحث](search-for-content.md#search-for-content)

## <a name="information-protection"></a>حماية المعلومات

**اكتشاف المعلومات الحساسة وتصنيفها وحمايتها**

يمكنك حماية البيانات في Microsoft تسميات الحساسية والحساسية لمساعدتك على اكتشاف المحتوى الحساس وتصنيفه وحمايته أينما كان أو يسافر.

### <a name="step-1-start-your-information-protection-trial"></a>الخطوة 1: [بدء الإصدار التجريبي لحماية المعلومات](mip-easy-trials.md)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

يمكن للعملاء المؤهلين تنشيط التسميات والسياسات الافتراضية حماية البيانات في Microsoft. عند تمكين التكوين الافتراضي في الإصدار التجريبي، سيستغرق الأمر دقيقتين تقريبا لتكوين كل سياسات المستأجر وما يصل إلى 24 ساعة لرؤية نتائج هذه السياسات الافتراضية.

عند اختيار التكوين الافتراضي، بنقرة واحدة، يتم تكوين ما يلي تلقائيا:

- تسميات الحساسية ونهاية تسمية الحساسية
- التسمية التلقائية من جانب العميل
- التسمية التلقائية من جانب الخدمة
- سياسات منع فقدان البيانات (DLP) Teams والأجهزة

[تنشيط التسميات والسياسات الافتراضية](mip-easy-trials.md#activate-the-default-labels-and-policies). إذا لزم الأمر، يمكنك التحرير يدويا بعد اكتمال التكوين.

### <a name="step-2-automatically-apply-sensitivity-labels-to-documents"></a>الخطوة 2: [تطبيق تسميات الحساسية تلقائيا على المستندات](apply-sensitivity-label-automatically.md)

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

عند إنشاء تسمية حساسية، يمكنك تلقائيا تعيين هذه التسمية للملفات ورسائل البريد الإلكتروني عندما تطابق الشروط التي تحددها.

1. [إنشاء تسميات الحساسية وتكوينها](create-sensitivity-labels.md#create-and-configure-sensitivity-labels)
1. [نشر نهج تسمية الحساسية لجميع المستخدمين](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
1. [إنشاء نهج تسمية تلقائية](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
   - اختر المعلومات التي تريد تطبيق التسمية عليها
   - تعريف مواقع لتطبيق التسمية
   - تحديد تسمية لتطبيقها
   - [تشغيل النهج في وضع المحاكاة](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)

![تكوين نهج جديد للتسمية التلقائية.](../media/auto-labeling-wizard.png)

### <a name="step-3-review-and-turn-on-auto-labeling-policy"></a>الخطوة 3: [مراجعة نهج التسمية التلقائية ثم تشغيله](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)

الآن في **صفحة تسمية حماية** >  المعلومات، يمكنك رؤية نهج التسمية التلقائية في المقطع **محاكاة**.

حدد النهج الخاص بك لرؤية تفاصيل التكوين الحالة. عند اكتمال عملية المحاكاة، حدد علامة التبويب العناصر التي يجب مراجعتها لمعرفة رسائل البريد الإلكتروني أو المستندات التي تطابقت مع القواعد المحددة.

عندما تكون جاهزا لتشغيل النهج بدون محاكاة، حدد **الخيار تشغيل النهج** .

## <a name="insider-risk-management"></a>إدارة مخاطر Insider

**الكشف عن مخاطر insider و إصلاحها**

استفد من الذكاء الاصطناعي لمساعدتك على تحديد المخاطر الداخلية وفرزها و إصلاحها بسرعة. باستخدام السجلات من خدمات Microsoft 365 و Azure، يمكنك تعريف سياسات تراقب إشارات مخاطر insider، ثم اتخاذ إجراءات إصلاحية مثل ترقية تعليم المستخدم أو بدء التحقيق.

### <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>الخطوة 1 (مطلوبة): [تمكين الأذونات لإدارة مخاطر insider](insider-risk-management-configure.md#step-1-required-enable-permissions-for-insider-risk-management)

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

هناك أربع مجموعات دور يتم استخدامها لتكوين الأذونات لإدارة ميزات إدارة مخاطر insider.

[إضافة مستخدمين إلى مجموعة دور إدارة مخاطر insider.](insider-risk-management-configure.md#add-users-to-an-insider-risk-management-role-group)

إذا لم تتمكن من رؤية الأذونات، فالرجاء التحدث إلى مسؤول المستأجر لتعيين الأدوار الصحيحة.

### <a name="step-2-start-with-user-quick-start-guide"></a>الخطوة 2: [البدء مع دليل البدء السريع للمستخدم](insider-risk-management-configure.md#recommended-actions-preview)

يمكنك البدء بسرعة والحصول على أفضل إمكانيات إدارة مخاطر insider باستخدام الإجراءات الموصى بها. مضمنة في صفحة نظرة عامة، تساعدك الإجراءات الموصى بها على إرشادك عبر الخطوات اللازمة لتكوين النهج ونشرها واتخاذ إجراءات التحقيق حول إجراءات المستخدم التي تنشئ تنبيهات من تطابقات النهج.

[حدد توصية من القائمة](insider-risk-management-configure.md#recommended-actions-preview) للبدء في تكوين إدارة مخاطر insider.

![إجراءات إدارة مخاطر Insider الموصى بها.](../media/insider-risk-recommended-actions.png)

يرشدك كل إجراء مستحسن عبر الأنشطة المطلوبة للتوصية، بما في ذلك أي متطلبات وما يجب توقعه وتأثير تكوين الميزة في مؤسستك.

### <a name="step-3-required-enable-the-microsoft-365-audit-log"></a>الخطوة 3 ([مطلوبة): تمكين Microsoft 365 التدقيق](insider-risk-management-configure.md#step-2-required-enable-the-microsoft-365-audit-log)

يتم تمكين التدقيق Microsoft 365 المؤسسات بشكل افتراضي. قد تكون بعض المؤسسات قد عطلت التدقيق لأسباب معينة. إذا كانت عملية التدقيق معطلة لمنظمتك، فقد يكون ذلك بسبب إيقاف تشغيلها من قبل مسؤول آخر. نوصي بتأكيد أنه لا بأس في تشغيل التدقيق مرة أخرى عند إكمال هذه الخطوة.

للحصول على إرشادات مفصلة خطوة بخطوة حول تشغيل التدقيق، راجع تشغيل البحث في سجل التدقيق [أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md). بعد تشغيل التدقيق، يتم عرض رسالة تعلمك بأنه يتم إعداد سجل التدقيق، كما يمكنك تشغيل عملية بحث خلال ساعتين بعد اكتمال عملية الإعداد. ما عليك سوى القيام بهذا الإجراء مرة واحدة. لمزيد من المعلومات حول استخدام Microsoft 365 التدقيق، راجع [البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md).

### <a name="step-4-required-enable-and-view-insider-risk-analytics-insights"></a>الخطوة 4 (مطلوبة): تمكين تحليلات مخاطر [insider وعرضها](insider-risk-management-configure.md#step-3-optional-enable-and-view-insider-risk-analytics-insights)

تمكنك تحليلات إدارة مخاطر Insider من إجراء تقييم لمخاطر insider المحتملة في مؤسستك دون تكوين أي من سياسات مخاطر insider. قد تستغرق نتائج الفحص التحليلي ما يصل إلى 48 ساعة قبل توفر نتائج التحليلات كلتقارير لمراجعتها. لمعرفة المزيد حول تحليلات التحليلات، راجع إعدادات إدارة مخاطر [Insider: التحليلات (معاينة)](insider-risk-management-settings.md) واستعرض فيديو تحليلات إدارة المخاطر ل [Insider](https://www.youtube.com/watch?v=5c0P5MCXNXk) لمساعدتك على فهم وضعية مخاطر insider الخاصة بك ومساعدتك على اتخاذ إجراء من خلال إعداد سياسات مناسبة لتحديد المستخدمين الخطرين.

لتمكين تحليلات مخاطر insider، يجب أن تكون عضوا في إدارة مخاطر Insider أو مسؤول إدارة مخاطر Insider. أكمل هذه الخطوات [لتمكين تحليلات مخاطر insider](insider-risk-management-configure.md).

## <a name="records-management"></a>إدارة التسجيلات

**أتمتة جدول الاستبقاء للسجلات الهامة للأعمال**

استخدم ميزات إدارة السجلات المتكاملة لأتمتة جدول الاستبقاء للسجلات التنظيمية والقانونية والحرجة للأعمال. احصل على دعم دورة حياة المحتوى الكامل، من الإنشاء إلى التعاون والإعلان عن السجل والاستبقاء والتصرف.

### <a name="step-1-dynamically-target-retention-policies-with-adaptive-policy-scopes"></a>الخطوة 1: نهج الاستبقاء المستهدفة ديناميكيا باستخدام نطاقات النهج التكييفية

> [!TIP]
> أفضل الممارسات التجريبية: اليوم 1

تسمح لك نطاقات النهج التكييفية باستهداف نهج بشكل ديناميكي لمستخدمين معينين أو مجموعات أو مواقع معينة استنادا إلى سمات AD الخاصة بهم.

يمكن تحديد سمات النطاقات من قائمة أو تخصيصها باستخدام منشئ استعلام متقدم.

تبقى النهج التي تستخدم نطاقات النهج التكييفية حالية مع تغير المؤسسة مع انضمام الموظفين الجدد أو مغادرتهم. بالإضافة إلى ذلك، لا تخضع للحدود السابقة التي كانت 100/1000 موقع مضمنة في نهج.

- إنشاء نطاق [نهج تكييفي](retention.md#adaptive-or-static-policy-scopes-for-retention) واستخدامه مع نهج استبقاء

### <a name="step-2-automate-labeling-of-sensitive-information-with-the-ability-to-review-before-disposal"></a>الخطوة 2: أتمتة تسمية المعلومات الحساسة مع إمكانية المراجعة قبل التخلص منها

> [!TIP]
> أفضل الممارسات التجريبية: الإعداد خلال أول 30 يوما

يمكن إعداد تسميات الاستبقاء لتطبيقها تلقائيا على المحتوى عندما يكشف عن معلومات حساسة، مثل رقم بطاقة الائتمان. يؤدي ذلك إلى إزالة حاجة المستخدمين إلى تنفيذ نشاط التسميات يدويا.

في نهاية فترة الاستبقاء، سيتم إعلام المستخدمين الذين تحددهم ("المراجعون") لمراجعة المحتوى والموافقة على إجراء التخلص الدائم. بهذه الطريقة، إذا كان هناك شيء ما يحتاج إلى الاحتفاظ به لفترة أطول، فقد يكون كذلك.

يمكن عرض نشاط تطبيق التسمية ونشاط مراجعة الترتيب على شاشة نظرة عامة على إدارة السجلات.

1. [تطبيق تسميات الاستبقاء بشكل تلقائي على المحتوى الذي يحتوي على معلومات حساسة](retention.md#retention-labels)
1. إنشاء تسمية استبقاء مع [مراجعة الترتيب](disposition.md#disposition-reviews) وتطبيقها في نهاية فترة الاستبقاء

### <a name="step-3-label-content-as-records-automatically-using-trainable-classifiers"></a>الخطوة 3: تسمية المحتوى كسجلات تلقائيا باستخدام المصنفات القابلة للتدريب

عند الإعلان عن المحتوى كسجل، يتم وضع قيود على العنصر من حيث الإجراءات المسموح بها أو المحظورة، كما يتم تسجيل أنشطة إضافية حول العناصر، وستثبت عدم الترتيب إذا تم حذف العناصر في نهاية فترة استبقاء العناصر.

إن المصنفات القابلة للتدريب هي أدوات تتعرف على أنواع مختلفة من المحتويات، استنادا إلى عينات تم تقديمها لها. اختر من بين مجموعة متنوعة من الخيارات المضمنة أو قم بإعداد تصنيف مخصص لتلبية احتياجاتك الخاصة.

1. إنشاء تسمية استبقاء [تعلن عن المحتوى كسجل أو سجل تنظيمي](records-management.md#records)
1. [تطبيق تسميات استبقاء تلقائية على المحتوى باستخدام تصنيفات قابلة للتدريب](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

### <a name="more-information-auto-apply-retention-labels--disposition-review"></a>مزيد من المعلومات: تطبيق تسميات الاستبقاء بشكل تلقائي + مراجعة الترتيب

**يمكنك تطبيق التسميات تلقائيا للاحتفاظ بما تحتاج إليه...**
يمكن تطبيق تسميات الاستبقاء تلقائيا على المحتوى عندما يحتوي على:

- [أنواع معينة من المعلومات الحساسة](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)
- [كلمات أساسية معينة أو خصائص قابلة للبحث تتطابق مع استعلام أنشأته](apply-retention-labels-automatically.md#auto-apply-labels-to-content-with-keywords-or-searchable-properties)
- [مطابقة للمصنفات القابلة للتدريب](apply-retention-labels-automatically.md#auto-apply-labels-to-content-by-using-trainable-classifiers)

**... ثم قم بالتخلص منه بأمان في النهاية.**

عند تشغيل مراجعة الترتيب في نهاية فترة الاستبقاء، يتلقى المراجعون الذين تختارهم إعلاما بالبريد الإلكتروني بأن لديهم محتوى لمراجعته.

يتم حذف المحتوى الذي ينتظر مراجعة الترتيب بشكل دائم فقط بعد أن يختار المراجع للمرحلة الأخيرة من الترتيب حذف المحتوى بشكل دائم.

## <a name="additional-trials-and-add-ons"></a>الإصدارات التجريبية الإضافية وا الوظائف الإضافية

### <a name="compliance-manager-premium-assessments"></a>التقييمات المتميزة لمدير التوافق

**تقييم المخاطر والاستجابة بفعالية**

ساعد مؤسستك على تقييم المخاطر والاستجابة بفعالية لمتطلبات الدول والمتطلبات الإقليمية ومتطلبات الصناعة التي تحكم تجميع البيانات واستخدامها.

[مزيد من المعلومات حول الإصدار التجريبي لتقييمات Premium لمدير التوافق](compliance-easy-trials-compliance-manager-assessments.md).

[دليل التشغيل التجريبي: التقييمات المتميزة من Microsoft Compliance Manager](compliance-easy-trials-compliance-manager-assessment-playbook.md)

### <a name="microsoft-priva-privacy-risk-management-and-microsoft-priva-subject-rights-requests"></a>Microsoft Priva Privacy Risk Management و Microsoft Priva Subject Rights Requests

**تحديد & من مخاطر الخصوصية**

تحديد مخاطر الخصوصية وحمايتها بشكل استباقي، مثل تخزين البيانات ونقل البيانات وتكرار مشاركة البيانات بشكل استباقي ومساعدة مؤسستك على أتمتة طلبات المواضيع وإدارتها على نطاق واسع.

[تعرف على المزيد حول Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management).

[دفتر التشغيل التجريبي: Microsoft Priva](/privacy/solutions/privacymanagement/privacy-management-trial-playbook)

## <a name="additional-resources"></a>موارد إضافية

**الميزات المضمنة**: للحصول على قائمة كاملة Microsoft 365 والميزات المدرجة حسب مستوى المنتج، يمكنك عرض [مصفوفة الميزات](https://go.microsoft.com/fwlink/?linkid=2139145).

**مكتبة المحتويات التقنية في Microsoft Security**: استكشف هذه المكتبة للعثور على أدلة تفاعلية ومحتوى تعلم آخر ذي صلة باحتياجاتك. [تفضل بزيارة المكتبة](/security).

**موارد أمان Microsoft**: من مكافحة البرامج الضارة إلى الثقة الصفرية، احصل على كل الموارد ذات الصلة لتلبية احتياجات أمان مؤسستك. [تفضل بزيارة الموارد](/security/business/resources).
