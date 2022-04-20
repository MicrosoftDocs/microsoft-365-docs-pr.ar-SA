---
title: التدقيق (Premium) في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-audit
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: يوفر تدقيق Microsoft Purview (Premium) قدرات تدقيق جديدة لمساعدة مؤسستك في التحقيقات الجنائية والتوافقية.
ms.openlocfilehash: 5e224d4d7073f96f4dc17d48f6caf19840905d06
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941050"
---
# <a name="microsoft-purview-audit-premium"></a>تدقيق Microsoft Purview (Premium)

توفر [وظيفة التدقيق](search-the-audit-log-in-security-and-compliance.md) في Microsoft Purview للمؤسسات إمكانية رؤية العديد من أنواع الأنشطة التي تم تدقيقها عبر العديد من الخدمات المختلفة في Microsoft 365. يساعد تدقيق Microsoft Purview (Premium) المؤسسات على إجراء تحقيقات الطب الشرعي والتوافق من خلال زيادة استبقاء سجل التدقيق المطلوب لإجراء تحقيق، وتوفير الوصول إلى الأحداث الهامة (باستخدام البحث في سجل التدقيق في مدخل توافق Microsoft Purview وواجهة برمجة تطبيقات نشاط الإدارة Office 365) التي تساعد في تحديد نطاق التسوية، والوصول بشكل أسرع إلى Office 365 Management Activity API.

> [!NOTE]
> يتوفر التدقيق (Premium) للمؤسسات التي لها اشتراك Office 365 E5/A5/G5 أو Microsoft 365 Enterprise E5/A5/G5. يجب تعيين ترخيص Microsoft 365 E5/A5/G5 Compliance أو E5/A5/G5 eDiscovery والتدقيق إلى المستخدمين لميزات التدقيق (Premium) مثل الاحتفاظ بسجلات التدقيق على المدى الطويل وإنشاء أحداث التدقيق (Premium) للتحقيقات. لمزيد من المعلومات حول الترخيص، راجع:<br/>- [متطلبات ترخيص التدقيق (Premium)](auditing-solutions-overview.md#licensing-requirements)<br/>- [Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

توفر هذه المقالة نظرة عامة على قدرات التدقيق (Premium) وتوضح لك كيفية إعداد المستخدمين للتدقيق (Premium).

## <a name="long-term-retention-of-audit-logs"></a>الاحتفاظ بسجلات التدقيق على المدى الطويل

يحتفظ التدقيق (Premium) بكافة سجلات تدقيق Exchange SharePoint وAzure Active Directory لمدة عام واحد. يتم تحقيق ذلك من خلال نهج استبقاء سجل تدقيق افتراضي يحتفظ بأي سجل تدقيق يحتوي على قيمة **Exchange أو** **SharePoint** أو **AzureActiveDirectory لخاصية** **Workload** (التي تشير إلى الخدمة التي حدث فيها النشاط) لمدة عام واحد. يمكن أن يساعد الاحتفاظ بسجلات التدقيق لفترات أطول في تحقيقات الطب الشرعي أو الامتثال الجارية. لمزيد من المعلومات، راجع قسم "نهج استبقاء سجل التدقيق الافتراضي" في [إدارة نهج استبقاء سجل التدقيق](audit-log-retention-policies.md#default-audit-log-retention-policy).

بالإضافة إلى قدرات الاستبقاء لمدة عام واحد من التدقيق (Premium)، قمنا أيضا بإطلاق القدرة على الاحتفاظ بسجلات التدقيق لمدة 10 سنوات. يساعد الاحتفاظ بسجلات التدقيق لمدة 10 سنوات على دعم التحقيقات طويلة الأمد والاستجابة للالتزامات التنظيمية والقانونية والداخلية.

> [!NOTE]
> سيتطلب الاحتفاظ بسجلات التدقيق لمدة 10 سنوات ترخيص وظيفة إضافية لكل مستخدم. بعد تعيين هذا الترخيص لمستخدم وتعيين نهج استبقاء سجل تدقيق مناسب لمدة 10 سنوات لهذا المستخدم، ستبدأ سجلات التدقيق التي يغطيها هذا النهج في الاحتفاظ بها لفترة 10 سنوات. هذا النهج ليس بأثر رجعي ولا يمكنه الاحتفاظ بسجلات التدقيق التي تم إنشاؤها قبل إنشاء نهج استبقاء سجل التدقيق لمدة 10 سنوات. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول التدقيق (Premium)](#faqs-for-audit-premium) في هذه المقالة.

### <a name="audit-log-retention-policies"></a>نهج استبقاء سجل التدقيق

يتم الاحتفاظ بكافة سجلات التدقيق التي تم إنشاؤها في خدمات أخرى غير مشمولة بنهج استبقاء سجل التدقيق الافتراضي (الموضحة في القسم السابق) لمدة 90 يوما. ولكن يمكنك إنشاء نهج استبقاء سجل تدقيق مخصصة للاحتفاظ بسجلات تدقيق أخرى لفترات زمنية أطول تصل إلى 10 سنوات. يمكنك إنشاء نهج للاحتفاظ بسجلات التدقيق استنادا إلى معيار واحد أو أكثر من المعايير التالية:

- خدمة Microsoft 365 التي تحدث فيها الأنشطة التي تم تدقيقها.

- أنشطة محددة تم تدقيقها.

- المستخدم الذي يقوم بنشاط مدقق.

يمكنك أيضا تحديد مدة الاحتفاظ بسجلات التدقيق التي تطابق النهج ومستوى الأولوية بحيث تأخذ نهج معينة الأولوية على النهج الأخرى. لاحظ أيضا أن أي نهج استبقاء سجل تدقيق مخصص سيكون له الأسبقية على نهج استبقاء التدقيق الافتراضي في حالة الحاجة إلى الاحتفاظ بسجلات تدقيق Exchange أو SharePoint أو Azure Active Directory لمدة أقل من عام (أو لمدة 10 سنوات) لبعض المستخدمين أو جميعهم في مؤسستك. لمزيد من المعلومات، راجع [إدارة نهج استبقاء سجل التدقيق](audit-log-retention-policies.md).

## <a name="audit-premium-events"></a>تدقيق (Premium) الأحداث

يساعد التدقيق (Premium) المؤسسات على إجراء تحقيقات الطب الشرعي والتوافق من خلال توفير الوصول إلى أحداث مهمة مثل وقت الوصول إلى عناصر البريد، ووقت الرد على عناصر البريد وإعادة توجيهها، ومتى أجرى المستخدم البحث في Exchange Online SharePoint Online وما قام بالبحث فيه. يمكن أن تساعدك هذه الأحداث في التحقيق في الخروقات المحتملة وتحديد نطاق التسوية. بالإضافة إلى هذه الأحداث في Exchange SharePoint، هناك أحداث في خدمات Microsoft 365 الأخرى التي تعتبر أحداثا مهمة وتتطلب تعيين [ترخيص التدقيق المناسب (Premium)](auditing-solutions-overview.md#licensing-requirements) للمستخدمين. يجب تعيين ترخيص تدقيق (Premium) للمستخدمين بحيث يتم إنشاء سجلات التدقيق عند قيام المستخدمين بتنفيذ هذه الأحداث.

يوفر التدقيق (Premium) الأحداث التالية:

- [MailItemsAccessed](#mailitemsaccessed)

- [ارسال](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

- [أحداث التدقيق الأخرى (Premium) في Microsoft 365](#other-audit-premium-events-in-microsoft-365)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

الحدث MailItemsAccessed هو إجراء تدقيق علبة بريد ويتم تشغيله عند الوصول إلى بيانات البريد بواسطة بروتوكولات البريد وعملاء البريد. يمكن أن يساعد هذا الحدث المحققين على تحديد انتهاكات البيانات وتحديد نطاق الرسائل التي ربما تم اختراقها. إذا تمكن مهاجم من الوصول إلى رسائل البريد الإلكتروني، فسيتم تشغيل الإجراء MailItemsAccessed حتى إذا لم تكن هناك إشارة صريحة إلى أن الرسائل تمت قراءتها بالفعل (بمعنى آخر، يتم تسجيل نوع الوصول مثل الربط أو المزامنة في سجل التدقيق).

يحل الحدث MailItemsAccessed محل MessageBind في تسجيل تدقيق علبة البريد في Exchange Online ويوفر هذه التحسينات:

- كان MessageBind قابلا للتكوين فقط لنوع تسجيل دخول مستخدم AuditAdmin؛ لم ينطبق على إجراءات المفوض أو المالك. تنطبق MailItemsAccessed على كافة أنواع تسجيل الدخول.

- لا يغطي MessageBind سوى الوصول بواسطة عميل البريد. لم يتم تطبيقه على أنشطة المزامنة. يتم تشغيل أحداث MailItemsAccessed بواسطة كل من أنواع الوصول إلى الربط والمزامنة.

- قد تؤدي إجراءات MessageBind إلى إنشاء سجلات تدقيق متعددة عند الوصول إلى رسالة البريد الإلكتروني نفسها، ما أدى إلى تدقيق "الضوضاء". في المقابل، يتم تجميع أحداث MailItemsAccessed في سجلات تدقيق أقل.

للحصول على معلومات حول سجلات التدقيق لأنشطة MailItemsAccessed، راجع [استخدام التدقيق (Premium) للتحقيق في الحسابات المخترقة](mailitemsaccessed-forensics-investigations.md).

للبحث عن سجلات التدقيق MailItemsAccessed، يمكنك البحث عن نشاط **عناصر علبة البريد التي تم الوصول إليها** في القائمة المنسدلة **لأنشطة علبة البريد Exchange** في [أداة البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مدخل التوافق.

![البحث عن إجراءات MailItemsAccessed في أداة البحث في سجل التدقيق.](../media/AdvAudit_MailItemsAccessed.png)

يمكنك أيضا تشغيل [أوامر Search-UnifiedAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-unifiedauditlog) أو [Search-MailboxAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-mailboxauditlog) في Exchange Online PowerShell.

### <a name="send"></a>ارسال

الحدث "إرسال" هو أيضا إجراء تدقيق علبة بريد ويتم تشغيله عندما ينفذ المستخدم أحد الإجراءات التالية:

- إرسال رسالة بريد إلكتروني

- الردود على رسالة بريد إلكتروني

- إعادة توجيه رسالة بريد إلكتروني

يمكن للباحثين استخدام حدث "إرسال" لتحديد البريد الإلكتروني المرسل من حساب تم اختراقه. يحتوي سجل التدقيق لحدث "إرسال" على معلومات حول الرسالة، مثل وقت إرسال الرسالة ومعرف InternetMessage وسطر الموضوع وما إذا كانت الرسالة تحتوي على مرفقات. يمكن أن تساعد معلومات التدقيق هذه المحققين على تحديد معلومات حول رسائل البريد الإلكتروني المرسلة من حساب مخترق أو المرسلة من قبل المهاجم. بالإضافة إلى ذلك، يمكن للباحثين استخدام أداة eDiscovery Microsoft 365 للبحث عن الرسالة (باستخدام سطر الموضوع أو معرف الرسالة) لتحديد المستلمين الذين تم إرسال الرسالة إليهم والمحتويات الفعلية للرسالة المرسلة.

للبحث عن سجلات التدقيق "إرسال"، يمكنك البحث عن نشاط **الرسالة المرسلة** في القائمة المنسدلة **لأنشطة علبة البريد Exchange** في [أداة البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مدخل التوافق.

![البحث عن إجراءات الرسائل المرسلة في أداة البحث في سجل التدقيق.](../media/AdvAudit_SentMessage.png)

يمكنك أيضا تشغيل [Search-UnifiedAuditLog -Operations Send](/powershell/module/exchange/search-unifiedauditlog) أو [Search-MailboxAuditLog -Operations Send](/powershell/module/exchange/search-mailboxauditlog) commands in Exchange Online PowerShell.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

يتم تشغيل الحدث SearchQueryInitiatedExchange عندما يستخدم شخص ما Outlook للبحث عن عناصر في علبة بريد. يتم تشغيل الأحداث عند إجراء عمليات البحث في بيئات Outlook التالية:

- Outlook (عميل سطح المكتب)

- Outlook على ويب (OWA)

- Outlook لنظام التشغيل iOS

- Outlook لنظام التشغيل Android

- تطبيق البريد Windows 10

يمكن للتحقق من استخدام الحدث SearchQueryInitiatedExchange لتحديد ما إذا كان المهاجم الذي ربما قام باختراق حساب بحث عن معلومات حساسة في علبة البريد أو حاول الوصول إليها. يحتوي سجل التدقيق لحدث SearchQueryInitiatedExchange على معلومات مثل النص الفعلي لاستعلام البحث. يشير سجل التدقيق أيضا إلى بيئة Outlook التي تم إجراء البحث فيها. من خلال النظر إلى استعلامات البحث التي قد يكون المهاجم قد قام بها، يمكن للمحقق فهم الهدف من بيانات البريد الإلكتروني التي تم البحث عنها بشكل أفضل.

للبحث عن سجلات تدقيق SearchQueryInitiatedExchange، يمكنك البحث عن نشاط **البحث عن البريد الإلكتروني الذي تم تنفيذه** في القائمة المنسدلة **لأنشطة البحث** في [أداة البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مركز التوافق.

![البحث عن إجراءات البحث عن البريد الإلكتروني التي تم تنفيذها في أداة البحث في سجل التدقيق.](../media/AdvAudit_SearchExchange.png)

يمكنك أيضا تشغيل [Search-UnifiedAuditLog -Operations SearchQueryInitiatedExchange](/powershell/module/exchange/search-unifiedauditlog) في Exchange Online PowerShell.

> [!NOTE]
> يجب تمكين SearchQueryInitiatedExchange لتسجيل الدخول حتى تتمكن من البحث عن هذا الحدث في سجل التدقيق. للحصول على الإرشادات، راجع [إعداد التدقيق (Premium).](set-up-advanced-audit.md#step-2-enable-audit-premium-events)

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

على غرار البحث عن عناصر علبة البريد، يتم تشغيل الحدث SearchQueryInitiatedSharePoint عندما يبحث شخص عن عناصر في SharePoint. يتم تشغيل الأحداث عند إجراء عمليات البحث على الصفحة الجذر أو الافتراضية للأنواع التالية من مواقع SharePoint:

- المواقع الرئيسية

- مواقع الاتصالات

- مواقع المركز

- المواقع المقترنة Microsoft Teams

يمكن للتحقق من استخدام الحدث SearchQueryInitiatedSharePoint لتحديد ما إذا كان المهاجم حاول العثور على معلومات حساسة (وربما الوصول إليها) في SharePoint. يحتوي سجل التدقيق لحدث SearchQueryInitiatedSharePoint أيضا على النص الفعلي لاستعلام البحث. يشير سجل التدقيق أيضا إلى نوع موقع SharePoint الذي تم البحث فيه. من خلال النظر في استعلامات البحث التي قد يكون المهاجم قد قام بها، يمكن للمحقق فهم هدف ونطاق بيانات الملف التي يتم البحث عنها بشكل أفضل.

للبحث عن سجلات تدقيق SearchQueryInitiatedSharePoint، يمكنك البحث عن نشاط **البحث SharePoint المنجز** في القائمة المنسدلة **"أنشطة البحث**" في [أداة البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مركز التوافق.

![البحث عن إجراءات البحث SharePoint المنفذة في أداة البحث في سجل التدقيق.](../media/AdvAudit_SearchSharePoint.png)

يمكنك أيضا تشغيل [Search-UnifiedAuditLog -Operations SearchQueryInitiatedSharePoint](/powershell/module/exchange/search-unifiedauditlog) في Exchange Online PowerShell.

> [!NOTE]
> يجب تمكين SearchQueryInitiatedSharePoint لتسجيل الدخول حتى تتمكن من البحث عن هذا الحدث في سجل التدقيق. للحصول على الإرشادات، راجع [إعداد التدقيق (Premium).](set-up-advanced-audit.md#step-2-enable-audit-premium-events)

### <a name="other-audit-premium-events-in-microsoft-365"></a>أحداث التدقيق الأخرى (Premium) في Microsoft 365

بالإضافة إلى الأحداث في Exchange Online و SharePoint Online، هناك أحداث في خدمات Microsoft 365 الأخرى التي يتم تسجيلها عند تعيين ترخيص التدقيق المناسب (Premium) للمستخدمين. توفر خدمات Microsoft 365 التالية أحداث التدقيق (Premium). حدد الارتباط المقابل للانتقال إلى مقال يحدد هذه الأحداث ويصفها.

- [Microsoft Forms](search-the-audit-log-in-security-and-compliance.md#microsoft-forms-activities)

- [Microsoft Stream](/stream/audit-logs#actions-logged-in-stream)

- [Microsoft Teams](/microsoftteams/audit-log-events#teams-activities)

- [Yammer](search-the-audit-log-in-security-and-compliance.md#yammer-activities)

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>وصول النطاق الترددي العالي إلى واجهة برمجة تطبيقات نشاط الإدارة Office 365

تم تقييد المؤسسات التي تصل إلى سجلات التدقيق من خلال واجهة برمجة تطبيقات نشاط الإدارة Office 365 من خلال قيود على مستوى الناشر. وهذا يعني أنه بالنسبة إلى ناشر يسحب البيانات نيابة عن العديد من العملاء، تمت مشاركة الحد من قبل جميع هؤلاء العملاء.

مع إصدار التدقيق (Premium)، نحن ننتقل من حد على مستوى الناشر إلى حد على مستوى المستأجر. والنتيجة هي أن كل مؤسسة ستحصل على حصة النطاق الترددي المخصصة بالكامل للوصول إلى بيانات التدقيق الخاصة بها. النطاق الترددي ليس حدا ثابتا ومقرنا مسبقا ولكن يتم تصميمه على مجموعة من العوامل بما في ذلك عدد المقاعد في المؤسسة وأن مؤسسات E5/A5/G5 ستحصل على نطاق ترددي أكثر من المؤسسات غير E5/A5/G5.

يتم في البداية تخصيص أساس لكل المؤسسات يبلغ 2000 طلب في الدقيقة. سيزداد هذا الحد ديناميكيا اعتمادا على عدد مقاعد المؤسسة واشتراك الترخيص الخاص بها. ستحصل مؤسسات E5/A5/G5 على ضعف النطاق الترددي تقريبا الذي تحصل عليه المؤسسات غير التابعة ل E5/A5/G5. سيكون هناك أيضا حد أقصى للنطاق الترددي لحماية صحة الخدمة.

لمزيد من المعلومات، راجع قسم "تقييد واجهة برمجة التطبيقات" في [مرجع واجهة برمجة تطبيقات نشاط الإدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-audit-premium"></a>الأسئلة المتداولة للتدقيق (Premium)

**هل يحتاج كل مستخدم إلى ترخيص E5/A5/G5 للاستفادة من التدقيق (Premium)؟**

للاستفادة من قدرات التدقيق على مستوى المستخدم (Premium)، يجب تعيين ترخيص E5/A5/G5 للمستخدم. هناك بعض القدرات التي ستتحقق من الترخيص المناسب لعرض الميزة للمستخدم. على سبيل المثال، إذا كنت تحاول الاحتفاظ بسجلات التدقيق لمستخدم لم يتم تعيين الترخيص المناسب له لأكثر من 90 يوما، فسيرجع النظام رسالة خطأ.

**لدى مؤسستي اشتراك E5/A5/G5، هل أحتاج إلى القيام بأي شيء للوصول إلى سجلات التدقيق لأحداث التدقيق (Premium)؟**

بالنسبة للعملاء والمستخدمين المؤهلين الذين تم تعيين ترخيص E5/A5/G5 المناسب لهم، لا يوجد أي إجراء مطلوب للوصول إلى أحداث التدقيق (Premium)، باستثناء تمكين أحداث SearchQueryInitiatedExchange و SearchQueryInitiatedSharePoint (كما هو موضح سابقا في هذه المقالة). سيتم إنشاء أحداث التدقيق (Premium) للمستخدمين الذين لديهم تراخيص E5/A5/G5 فقط بمجرد تعيين هذه التراخيص.

**هل تتوفر الأحداث الجديدة في Audit (Premium) في واجهة برمجة تطبيقات نشاط الإدارة Office 365؟**

نعم. طالما يتم إنشاء سجلات التدقيق للمستخدمين الذين لديهم الترخيص المناسب، ستتمكن من الوصول إلى هذه السجلات عبر واجهة برمجة تطبيقات نشاط الإدارة Office 365.

**ماذا يحدث لبيانات سجل التدقيق في مؤسستي إذا قمت بإنشاء نهج استبقاء سجل التدقيق لمدة 10 سنوات عند إصدار الميزة للتوفر العام ولكن قبل إتاحة ترخيص الوظيفة الإضافية المطلوبة؟**

سيتم الاحتفاظ بأي بيانات سجل تدقيق تغطيها سياسة استبقاء سجل التدقيق لمدة 10 سنوات التي قمت بإنشائها بعد إصدار الميزة للتوفر العام في الربع الأخير من عام 2020 لمدة 10 سنوات. يتضمن ذلك نهج استبقاء سجل التدقيق لمدة 10 سنوات التي تم إنشاؤها قبل إصدار ترخيص الوظيفة الإضافية المطلوبة للشراء في مارس 2021. ومع ذلك، نظرا لأن ترخيص الاحتفاظ بسجل التدقيق لمدة 10 سنوات متوفر الآن، فستحتاج إلى شراء تراخيص الوظائف الإضافية هذه وتعيينها لجميع المستخدمين الذين تغطي بيانات التدقيق الخاصة بهم نهج استبقاء التدقيق لمدة 10 سنوات.
