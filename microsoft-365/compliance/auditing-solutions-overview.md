---
title: حلول تدقيق Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- m365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية تدقيق أنشطة المستخدمين والمسؤولين في مؤسستك Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8ceaea2b888c144fb5c6bc34d9d7788ab595b56b
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864573"
---
# <a name="auditing-solutions-in-microsoft-purview"></a>حلول التدقيق في Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

توفر حلول التدقيق Microsoft Purview حلا متكاملا لمساعدة المؤسسات على الاستجابة الفعالة للأحداث الأمنية والتحقيقات الجنائية والتحقيقات الداخلية والتزامات الامتثال. يتم تسجيل الآلاف من عمليات المستخدم والمسؤول التي يتم تنفيذها في العشرات من خدمات وحلول Microsoft 365 وتسجيلها والاحتفاظ بها في سجل التدقيق الموحد لمؤسستك. يمكن البحث في سجلات التدقيق لهذه الأحداث من قبل عمليات الأمان، والمسؤولين عن تكنولوجيا المعلومات، وفرق المخاطر الداخلية، والامتثال والتحريين القانونيين في مؤسستك. توفر هذه الإمكانية رؤية للأنشطة التي يتم تنفيذها عبر مؤسستك Microsoft 365.

## <a name="microsoft-purview-auditing-solutions"></a>حلول تدقيق Microsoft Purview

يوفر Microsoft Purview حلين للتدقيق: التدقيق (قياسي) والتدقيق (Premium).

![القدرات الرئيسية للتدقيق (القياسي) والتدقيق (Premium).](..\media\AuditingSolutionsComparison.png)

### <a name="audit-standard"></a>التدقيق (قياسي)

يوفر لك Microsoft Purview Audit (Standard) القدرة على تسجيل الأنشطة التي تم تدقيقها والبحث عنها وتشغيل التحقيقات الجنائية وتقنية المعلومات والتوافق والشؤون القانونية.

- **ممكن بشكل افتراضي**. يتم تشغيل التدقيق (القياسي) بشكل افتراضي لجميع المؤسسات التي لها الاشتراك المناسب. وهذا يعني أنه سيتم تسجيل سجلات الأنشطة التي تم تدقيقها ويمكن البحث فيها. الإعداد الوحيد المطلوب هو تعيين الأذونات اللازمة للوصول إلى أداة البحث في سجل التدقيق (و cmdlet المقابلة) والتأكد من تعيين الترخيص الصحيح للمستخدم لميزات التدقيق Microsoft Purview (Premium).
- **الآلاف من أحداث التدقيق القابلة للبحث**. يمكنك البحث عن مجموعة واسعة من الأنشطة التي تم تدقيقها والتي تحدث في معظم خدمات Microsoft 365 في مؤسستك. للحصول على قائمة جزئية بالأنشطة التي يمكنك البحث فيها، راجع [الأنشطة التي تم تدقيقها](search-the-audit-log-in-security-and-compliance.md#audited-activities). للحصول على قائمة بالخدمات والميزات التي تدعم الأنشطة التي تم تدقيقها، راجع [نوع سجل التدقيق](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **أداة البحث في التدقيق في مدخل التوافق في Microsoft Purview**. استخدم أداة البحث في سجل التدقيق في مدخل التوافق للبحث عن سجلات التدقيق. يمكنك البحث عن أنشطة معينة، والأنشطة التي قام بها مستخدمون محددون، والأنشطة التي حدثت مع نطاق تاريخ. فيما يلي لقطة شاشة لأداة البحث في التدقيق في مركز الامتثال.

   ![أداة البحث في سجل التدقيق في مدخل التوافق.](../media/AuditLogSearchToolMCC.png)

- **Search-UnifiedAuditLog cmdlet**. يمكنك أيضا استخدام **Search-UnifiedAuditLog** cmdlet في Exchange Online PowerShell (cmdlet الأساسي لأداة البحث) للبحث عن أحداث التدقيق أو لاستخدامها في برنامج نصي. لمزيد من المعلومات، اطلع على:

  - [مرجع cmdlet ل Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)
  - [استخدام برنامج PowerShell النصي للبحث في سجل التدقيق](audit-log-search-script.md)

- **تصدير سجلات التدقيق إلى ملف CSV**. بعد تشغيل أداة البحث في سجل التدقيق في مدخل التوافق، يمكنك تصدير سجلات التدقيق التي تم إرجاعها بواسطة البحث إلى ملف CSV. يتيح لك ذلك استخدام Microsoft Excel الفرز والتصفية على خصائص سجل التدقيق المختلفة. يمكنك أيضا استخدام Excel Power Query وظائف التحويل لتقسيم كل خاصية في كائن AuditData JSON إلى عموده الخاص. يتيح لك ذلك عرض بيانات مشابهة ومقارنة بيانات مشابهة لأحداث مختلفة بشكل فعال. لمزيد من المعلومات، راجع [تصدير سجلات سجل التدقيق وتكوينها وعرضها](export-view-audit-log-records.md).

- **الوصول إلى سجلات التدقيق عبر واجهة برمجة تطبيقات نشاط الإدارة Office 365**. الطريقة الثالثة للوصول إلى سجلات التدقيق واستردادها هي استخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365. يتيح هذا للمؤسسات الاحتفاظ ببيانات التدقيق لفترات أطول من 90 يوما الافتراضية ويسمح لها باستيراد بيانات التدقيق الخاصة بها إلى حل SIEM. لمزيد من المعلومات، راجع [مرجع واجهة برمجة تطبيقات نشاط الإدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

- **الاحتفاظ بسجل التدقيق لمدة 90 يوما**. عند تنفيذ نشاط مدقق من قبل مستخدم أو مسؤول، يتم إنشاء سجل تدقيق وتخزينه في سجل التدقيق لمؤسستك. في Audit (Standard)، يتم الاحتفاظ بالسجلات لمدة 90 يوما، ما يعني أنه يمكنك البحث عن الأنشطة التي حدثت خلال الأشهر الثلاثة الماضية.

### <a name="audit-premium"></a>التدقيق (متميز)

يعتمد التدقيق (Premium) على قدرات التدقيق (القياسي) من خلال توفير نهج استبقاء سجل التدقيق، والاحتفاظ بسجلات التدقيق لفترة أطول، والأحداث الهامة عالية القيمة، والوصول إلى النطاق الترددي الأعلى إلى واجهة برمجة تطبيقات نشاط الإدارة Office 365.

- **نهج استبقاء سجل التدقيق**. يمكنك إنشاء نهج مخصصة لاستبقاء سجل التدقيق للاحتفاظ بسجلات التدقيق لفترات زمنية أطول تصل إلى سنة واحدة (وما يصل إلى 10 سنوات للمستخدمين الذين لديهم ترخيص وظيفة إضافية مطلوب). يمكنك إنشاء نهج للاحتفاظ بسجلات التدقيق استنادا إلى الخدمة التي تحدث فيها الأنشطة التي تم تدقيقها أو أنشطة معينة مدققة أو المستخدم الذي يقوم بنشاط مدقق.

- **الاحتفاظ بسجلات التدقيق لفترة أطول**. يتم الاحتفاظ بسجلات تدقيق Exchange SharePoint وAzure Active Directory لمدة عام واحد بشكل افتراضي. يتم الاحتفاظ بسجلات التدقيق لكافة الأنشطة الأخرى لمدة 90 يوما بشكل افتراضي، أو يمكنك استخدام نهج استبقاء سجل التدقيق لتكوين فترات استبقاء أطول.

- **أحداث التدقيق (Premium) عالية القيمة والحاسمة**. يمكن أن تساعد سجلات التدقيق للأحداث الهامة مؤسستك على إجراء تحقيقات الطب الشرعي والتوافق من خلال توفير رؤية لأحداث مثل وقت الوصول إلى عناصر البريد، أو عند الرد على عناصر البريد وإعادة توجيهها، أو متى وما بحث المستخدم عنهما في Exchange Online SharePoint Online. يمكن أن تساعدك هذه الأحداث الحاسمة في التحقيق في الخروقات المحتملة وتحديد نطاق التسوية.

- **عرض نطاق ترددي أعلى لواجهة برمجة تطبيقات نشاط الإدارة Office 365**. يوفر التدقيق (Premium) للمؤسسات المزيد من النطاق الترددي للوصول إلى سجلات التدقيق من خلال واجهة برمجة تطبيقات نشاط الإدارة Office 365. على الرغم من أن جميع المؤسسات (التي لديها تدقيق (قياسي) أو تدقيق (Premium)) يتم تخصيص أساس لها في البداية يبلغ 2000 طلب في الدقيقة، إلا أن هذا الحد سيزداد ديناميكيا اعتمادا على عدد مقاعد المؤسسة واشتراك الترخيص الخاص بها. يؤدي هذا إلى حصول المؤسسات التي تمتلك "التدقيق" (Premium) على ضعف النطاق الترددي تقريبا مثل المؤسسات التي تستخدم التدقيق (قياسي).

لمزيد من المعلومات التفصيلية حول ميزات التدقيق (Premium)، راجع [التدقيق (Premium) في Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>مقارنة القدرات الرئيسية

يقارن الجدول التالي القدرات الرئيسية المتوفرة في التدقيق (القياسي) والتدقيق (Premium). يتم تضمين كافة وظائف التدقيق (القياسي) في التدقيق (Premium).

|القدره|التدقيق (قياسي)|التدقيق (متميز)|
|:------|:-------------|:-------------|
|ممكن بشكل افتراضي|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)|
|الآلاف من أحداث التدقيق القابلة للبحث|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)|
|أداة البحث في التدقيق في مدخل التوافق|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)|
|Search-UnifiedAuditLog cmdlet|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)|
|تصدير سجلات التدقيق إلى ملف CSV|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)|
|الوصول إلى سجلات التدقيق عبر واجهة برمجة تطبيقات نشاط الإدارة <sup>1</sup> Office 365|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)</sup>|
|الاحتفاظ بسجل التدقيق لمدة 90 يوما|![دعم.](../media/check-mark.png)|![دعم.](../media/check-mark.png)|
|الاحتفاظ بسجل التدقيق لمدة سنة واحدة||![دعم.](../media/check-mark.png)|
|الاحتفاظ بسجل التدقيق لمدة 10 سنوات <sup>2</sup>||![دعم](../media/check-mark.png)|
|نهج استبقاء سجل التدقيق||![دعم](../media/check-mark.png)|
|أحداث عالية القيمة وحاسمة||![دعم](../media/check-mark.png)|

> [!NOTE]
> <sup>1</sup> يتضمن التدقيق (Premium) وصولا أكبر للنطاق الترددي إلى واجهة برمجة تطبيقات نشاط الإدارة Office 365، والتي توفر وصولا أسرع إلى بيانات التدقيق.<br/><sup>2</sup> بالإضافة إلى الترخيص المطلوب للتدقيق (Premium) (الموضحة في القسم التالي)، يجب تعيين إضافة الاحتفاظ بسجل التدقيق لمدة 10 سنوات للمستخدم على الترخيص للاحتفاظ بسجلات التدقيق لمدة 10 سنوات.

## <a name="licensing-requirements"></a>متطلبات الترخيص

تحدد الأقسام التالية متطلبات الترخيص للتدقيق (القياسي) والتدقيق (Premium). يتم تضمين وظيفة التدقيق (القياسي) مع التدقيق (Premium).

### <a name="audit-standard"></a>التدقيق (قياسي)

- اشتراك Microsoft Business Basic
- اشتراك Microsoft Business Standard
- اشتراك Microsoft 365 Apps للأعمال
- اشتراك Microsoft 365 Enterprise E3
- Microsoft 365 Business Premium
- اشتراك Microsoft 365 Education A3
- اشتراك Microsoft 365 Government G3
- اشتراك Microsoft 365 Government G1
- Microsoft 365 اشتراك Frontline F1 أو F3 أو الوظيفة الإضافية F5 Security
- اشتراك Office 365 Enterprise E3
- اشتراك Office 365 Enterprise E1
- اشتراك Office 365 Education A1
- اشتراك Office 365 Education A3

### <a name="audit-premium"></a>التدقيق (متميز)

- اشتراك Microsoft 365 Enterprise E5
- Microsoft 365 Enterprise اشتراك E3 + الوظيفة الإضافية التوافق في Microsoft 365 E5
- Microsoft 365 Enterprise اشتراك E3 + الوظيفة الإضافية Microsoft 365 E5 eDiscovery و Audit
- اشتراك Microsoft 365 Education A5
- اشتراك Microsoft 365 Education A3 + الوظيفة الإضافية توافق Microsoft 365 A5
- Microsoft 365 Education اشتراك A3 + الوظيفة الإضافية eDiscovery والتدقيق Microsoft 365 A5
- اشتراك Microsoft 365 Government G5
- Microsoft 365 اشتراك Government G3 + الوظيفة الإضافية Microsoft 365 G5 Compliance
- اشتراك Microsoft 365 Government G3 + Microsoft 365 eDiscovery والوظيفة الإضافية Audit
- Microsoft 365 Frontline F5 Compliance أو الوظيفة الإضافية F5 Security & Compliance
- اشتراك Office 365 Enterprise E5
- اشتراك Office 365 Education A5

## <a name="set-up-microsoft-purview-auditing-solutions"></a>إعداد حلول تدقيق Microsoft Purview

لبدء استخدام حلول التدقيق في Microsoft Purview، راجع إرشادات الإعداد التالية.

### <a name="set-up-audit-standard"></a>إعداد التدقيق (قياسي)

الخطوة الأولى هي إعداد التدقيق (قياسي) ثم بدء تشغيل عمليات البحث في سجل التدقيق.

![سير العمل لإعداد التدقيق (قياسي).](../media/BasicAuditingWorkflow.png)

1. تحقق من أن مؤسستك لديها اشتراك يدعم التدقيق (قياسي) وإذا كان ذلك ممكنا، اشتراك يدعم التدقيق (Premium).

2. قم بتعيين الأذونات في Exchange Online للأشخاص في مؤسستك الذين سيستخدمون أداة البحث في سجل التدقيق في مدخل التوافق أو يستخدمون **cmdlet Search-UnifiedAuditLog**. وبوجه خاص، يجب تعيين دور سجلات التدقيق أو سجلات التدقيق View-Only للمستخدمين في Exchange Online.

3. البحث في سجل التدقيق. بعد إكمال الخطوة 1 والخطوة 2، يمكن للمستخدمين في مؤسستك استخدام أداة البحث في سجل التدقيق (أو cmdlet المطابقة) للبحث عن الأنشطة التي تم تدقيقها.

للحصول على إرشادات أكثر تفصيلا، راجع [إعداد التدقيق (قياسي).](set-up-basic-audit.md)

### <a name="set-up-audit-premium"></a>إعداد التدقيق (متميز)

إذا كان لدى مؤسستك اشتراك يدعم التدقيق (Premium)، فنفذ الخطوات التالية لإعداد القدرات الإضافية واستخدامها في Audit (Premium).

![سير العمل لإعداد التدقيق (Premium).](../media/AdvancedAuditWorkflow.png)

1. إعداد التدقيق (Premium) للمستخدمين. تتكون هذه الخطوة من المهام التالية:

   - التحقق من تعيين الترخيص أو ترخيص الوظيفة الإضافية المناسب للمستخدمين للتدقيق (Premium).
  
   - يجب أن يكون تشغيل تطبيق/خطة خدمة التدقيق (Premium) لهؤلاء المستخدمين.
  
   - تمكين تدقيق الأحداث الهامة ثم تشغيل تطبيق/خطة خدمة التدقيق (Premium) لهؤلاء المستخدمين.

2. تمكين تسجيل أحداث التدقيق (Premium) عندما يقوم المستخدمون بإجراء عمليات بحث في Exchange Online SharePoint Online.

3. إعداد نهج استبقاء سجل التدقيق. بالإضافة إلى النهج الافتراضي الذي يحتفظ بسجلات التدقيق Exchange SharePoint Azure AD لمدة عام واحد، يمكنك إنشاء نهج استبقاء سجل تدقيق إضافية لتلبية متطلبات عمليات الأمان وفرق تكنولوجيا المعلومات والتوافق في مؤسستك.

4. ابحث عن أحداث التدقيق (Premium) الهامة والأنشطة الأخرى عند إجراء التحقيقات الجنائية. بعد الانتهاء من الخطوة 1 والخطوة 2، يمكنك البحث في سجل التدقيق عن أحداث التدقيق (Premium) والأنشطة الأخرى أثناء التحقيقات الجنائية للحسابات المخترقة وأنواع أخرى من تحقيقات الأمان أو الامتثال.

للحصول على إرشادات أكثر تفصيلا، راجع [إعداد التدقيق (Premium).](set-up-advanced-audit.md)

<!--
## Encrypt audit records using Customer Key

You can enable Customer Key encryption for audit records. Auditing builds on the [Service encryption with Customer Key](customer-key-overview.md) to encrypt sensitive information in your organization's auditing data. Implementing Customer Key provides extra protection by preventing unauthorized systems or Microsoft data center personnel from viewing your auditing data in the auditing pipeline and at rest. Using Customer Key to encrypt your auditing data also helps you meet regulatory or compliance obligations because your organization provides and controls the encryption keys.

To implement Customer Key for auditing, you have to create a multi-workload Data Encryption Policy (DEP), which defines the encryption hierarchy. For detailed step-by-step instructions, see [Set up Customer Key](customer-key-set-up.md).

> [!NOTE]
> Not all audit records in your organization are encrypted. The Microsoft Purview service that generates specific audit records for activity in that service defines whether the audit record is encrypted or not.
-->

## <a name="training"></a>التدريب

يمكن أن يساعد تدريب فريق عمليات الأمان ومسؤولي تكنولوجيا المعلومات وفريق المحققين في الامتثال على أساسيات التدقيق (القياسي) والتدقيق (Premium) مؤسستك على البدء بسرعة أكبر باستخدام التدقيق للمساعدة في تحقيقاتك. يوفر Microsoft Purview المورد التالي لمساعدة هؤلاء المستخدمين في مؤسستك على البدء في التدقيق: [وصف قدرات eDiscovery والتدقيق Microsoft Purview](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
