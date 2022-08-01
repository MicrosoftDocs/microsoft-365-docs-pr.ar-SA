---
title: إمكانية توسعة Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: تعرف على توسيع حلول Microsoft Purview باستخدام موصلات بيانات الجهات الخارجية وواجهات برمجة تطبيقات Microsoft Graph.
ms.openlocfilehash: 7fc3bf0fb177e07011d0e6388109deec7df14c05
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67106416"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>إمكانية توسعة Microsoft Purview وقابلية Microsoft Priva

تساعد حلول Microsoft Purview المؤسسات على تقييم مخاطر الامتثال الخاصة بها بذكاء، وتحكم البيانات الحساسة وتحميها، وتستجيب بفعالية للمتطلبات التنظيمية. يعد Microsoft Purview غنيا بسيناريوهات قابلية التوسع ويمكن المؤسسات من تكييف حلول الامتثال وتوسيعها ودمجها وتسريعها ودعمها.

هناك كتلتان أساسيتان أساسيتان لإمكانية توسعة الامتثال:

- **موصلات البيانات**. يستخدم لاستيراد بيانات غير تابعة ل Microsoft وأرشفتها حتى تتمكن من تطبيق قدرات الحماية والحوكمة في Microsoft 365 على بيانات الجهات الخارجية.

- **واجهات برمجة التطبيقات**. تمكين الوصول البرمجي إلى قدرات Microsoft Purview.

## <a name="data-connectors"></a>موصلات البيانات

توفر Microsoft موصلات بيانات تابعة لجهة خارجية يمكن تكوينها في مدخل التوافق في Microsoft Purview. للحصول على قائمة بموصلات البيانات التي توفرها Microsoft، راجع جدول [موصلات البيانات التابعة لجهة خارجية](archiving-third-party-data.md#third-party-data-connectors) . يلخص جدول موصلات البيانات التابعة لجهة خارجية أيضا حلول التوافق التي يمكنك تطبيقها على بيانات الجهات الخارجية بعد استيراد البيانات وأرشفتها في Microsoft 365، وارتباطات إلى الإرشادات المفصلة خطوة بخطوة لكل موصل.

لمعرفة المزيد حول Microsoft Purview Data Connectors، راجع [أرشفة بيانات الجهات الخارجية](archiving-third-party-data.md). إذا لم يكن نوع بيانات جهة خارجية مدعوما من قبل موصلات البيانات المتوفرة في مدخل التوافق، يمكنك العمل مع شريك يمكنه تزويدك بموصل مخصص. للحصول على قائمة بالشركاء الذين يمكنك العمل معهم والعملية المفصلة خطوة بخطوة لهذا الأسلوب، راجع ["العمل مع شريك" لأرشفة بيانات الجهات الخارجية](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>المتطلبات الأساسية لموصلات البيانات

تتطلب العديد من موصلات البيانات المتوفرة في مدخل التوافق لاستيراد بيانات الجهات الخارجية وأرشفتها إعداد مهام التكوين وتنفيذها في مصدر بيانات الجهات الخارجية. يتم توثيق هذه المتطلبات الأساسية بالتفصيل لكل موصل بيانات تابع لجهة خارجية.

بالنسبة إلى موصلات البيانات في مدخل التوافق الذي يوفره أحد شركاء Microsoft، ستحتاج مؤسستك إلى علاقة عمل مع الشريك قبل أن تتمكن من نشر موصل.

للحصول على إرشادات ومتطلبات موصلات البيانات التابعة لجهة خارجية، راجع قسم "موصلات البيانات" في [إرشادات Microsoft 365 للأمان & التوافق - أوصاف الخدمة | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>واجهات برمجه التطبيقات

تتوفر Microsoft Purview وواجهات برمجة التطبيقات Microsoft Priva في حماية البيانات في Microsoft SDK وMicrosoft Graph API وواجهة برمجة تطبيقات نشاط الإدارة Office 365. تعد بعض واجهات برمجة التطبيقات للامتثال جزءا من مجموعة جديدة من واجهات برمجة تطبيقات الأمان والتوافق التي تمكن المطورين لعملاء Microsoft 365 وموردي البرامج المستقلين ومكاملي النظام وموفري خدمات الأمان المدارة من إنشاء حلول أمان وتوافق عالية القيمة.

لمعرفة المزيد حول كيفية الوصول إلى واجهات برمجة تطبيقات Graph، راجع [نظرة عامة على Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>واجهات برمجة تطبيقات Microsoft Graph لطلبات حقوق الموضوع

وفقا لبعض لوائح الخصوصية في جميع أنحاء العالم، يمكن للأفراد تقديم طلبات لمراجعة أو إدارة البيانات الشخصية المتعلقة بأنفسهم التي جمعتها الشركات. يشار إلى هذه الطلبات على أنها *طلبات حقوق الموضوع* ضمن حل طلبات حقوق أصحاب البيانات في Microsoft Priva. يشار أيضا إلى طلبات حقوق الموضوع *بطلبات موضوع البيانات* (DSRs) أو *طلبات الوصول إلى موضوع البيانات* (DSARs). تمكن واجهات برمجة تطبيقات Microsoft Graph لطلبات حقوق الموضوع المطورين من دمج طلبات حقوق الموضوع المتعلقة ب Microsoft 365 مع النظام البنائي للخصوصية الأوسع. تتيح إمكانية التوسع المستندة إلى واجهة برمجة التطبيقات هذه للمؤسسات الاستجابة لطلبات حقوق الموضوع بطريقة موحدة عبر ملكية البيانات بأكملها التي تغطي كل من بيئات Microsoft والبيئات غير التابعة ل Microsoft. تساعد هذه الإمكانية أيضا في الأتمتة على نطاق واسع وتساعد المؤسسات على تلبية اللوائح الصناعية بشكل أكثر كفاءة دون الاعتماد على العمليات اليدوية.

لمعرفة المزيد، راجع [واجهات برمجة تطبيقات Microsoft Graph لطلب حقوق الموضوع](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>حماية البيانات في Microsoft (MIP) SDK

تعرض MIP SDK خدمات التسمية والحماية من مراكز الأمان والتوافق ل Microsoft 365 لتطبيقات وخدمات الجهات الخارجية. يمكن للمطورين استخدام SDK لإنشاء دعم أصلي لتطبيق التسميات والحماية على الملفات. يمكن للمطورين تحديد الإجراءات التي يجب اتخاذها عند الكشف عن تسميات معينة، والسبب في المعلومات المشفرة بواسطة MIP.

تتضمن حالات استخدام MIP SDK عالية المستوى ما يلي:

- تطبيق خط العمل الذي يطبق تسميات التصنيف على الملفات عند التصدير.

- تطبيق تصميم CAD/CAM الذي يوفر دعما أصليا لأوصاف الحساسية.

- وسيط أمان الوصول إلى السحابة أو حل منع فقدان البيانات الذي يمكنه تشفير البيانات باستخدام azure حماية البيانات.

لمعرفة المزيد حول MIP SDK والمتطلبات الأساسية والسيناريوهات الإضافية والعينات، راجع [نظرة عامة على MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>واجهة برمجة تطبيقات Microsoft Graph ل Teams DLP

تستخدم قدرات [منع فقدان البيانات (DLP)](dlp-microsoft-teams.md) على نطاق واسع في Microsoft Teams خاصة مع انتقال المؤسسات إلى العمل عن بعد. [أعلنا مؤخرا عن التوفر العام](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) لواجهة برمجة تطبيقات إعلام تغيير Microsoft Graph للرسائل في Teams. تمكن واجهة برمجة التطبيقات هذه المطورين من إنشاء تطبيقات يمكنها الاستماع إلى رسائل Microsoft Teams في الوقت الفعلي تقريبا ثم تنفيذ سيناريوهات DLP لكل من العملاء والشركاء. بالإضافة إلى ذلك، يتيح لك Microsoft Graph Patch API تطبيق إجراءات DLP على رسائل Teams.

تشكل واجهات برمجة التطبيقات هاتين واجهة برمجة تطبيقات Microsoft Graph ل Teams DLP. يمكنك البدء بتجربة [نموذج التطبيق](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). لمزيد من المعلومات حول خطافات ويب لمراسلة Microsoft Teams، راجع [الوثائق](/graph/api/subscription-post-subscriptions).

للحصول على متطلبات الترخيص ل Teams DLP، راجع [إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft Graph API ل eDiscovery (معاينة)

باستخدام [eDiscovery (Premium)](overview-ediscovery-20.md)، يمكن للمؤسسات اكتشاف البيانات حيث تقيم، وإدارة المزيد من مهام سير عمل eDiscovery الشاملة مع قدرات ذكية للتعلم الآلي والتحليلات لتقليل البيانات إلى المجموعة ذات الصلة - كل ذلك بينما تظل البيانات داخل حدود الأمان والتوافق في Microsoft 365.

يمكن استخدام واجهات برمجة تطبيقات الرسم البياني ل eDiscovery (Premium) لإنشاء الحالات وإدارتها، ومراجعة المجموعات، ومراجعة استعلامات المجموعة بطريقة قابلة للتطوير وقابلة للتكرار. وهذا يمكن العملاء والشركاء من إنشاء التطبيقات وسير العمل لأتمتة العمليات الشائعة والمتكررة مثل إنشاء الحالات وإدارة أمناء الحفظ والموقوفين القانونيين.

تتوفر المجموعة الأولى من واجهات برمجة تطبيقات الرسم البياني ل eDiscovery في المعاينة العامة. نخطط لإضافة المزيد من القدرات بحلول نهاية السنة التقويمية. لمعرفة المزيد حول واجهات برمجة التطبيقات هذه والتحديثات الأخرى ل eDiscovery (Premium)، راجع هذه [المدونة](https://aka.ms/Ignite2020AeDAA).

للحصول على متطلبات الترخيص ل eDiscovery (Premium) وواجهة برمجة التطبيقات، راجع قسم "eDiscovery" في [إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft Graph API لتصدير Teams

أرشفة معلومات المؤسسة (EIA) ل Microsoft Teams هو سيناريو رئيسي لعملائنا لأنه يسمح لهم بحل المتطلبات التنظيمية. بالإضافة إلى قدراتنا المضمنة لأرشفة المحتوى في Microsoft Teams، يمكن للعملاء والشركاء الآن استخدام واجهات برمجة التطبيقات لتصدير Teams لحل سيناريوهات التطبيق والتكامل المخصصة. تدعم واجهات برمجة التطبيقات لتصدير Teams التصدير المجمع (ما يصل إلى 200 طلب في الثانية/لكل تطبيق/لكل مستأجر) لرسائل Teams ومرفقات الرسائل. يمكن أيضا الوصول إلى الرسائل المحذوفة بواسطة واجهة برمجة التطبيقات لمدة تصل إلى 30 يوما بعد حذفها. لمزيد من المعلومات حول واجهات برمجة التطبيقات هذه لتصدير Teams وكيفية استخدامها في تطبيقاتك، راجع [تصدير المحتوى باستخدام واجهات برمجة التطبيقات لتصدير Microsoft Teams](/microsoftteams/export-teams-content).

للحصول على متطلبات الترخيص لاستخدام واجهات برمجة تطبيقات تصدير Teams، راجع [إرشادات ترخيص Microsoft 365 للأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>واجهات برمجة تطبيقات موصل Microsoft Graph (معاينة)

باستخدام [موصلات Microsoft Graph](/microsoftsearch/connectors-overview)، يمكن للمؤسسات فهرسة بيانات الجهات الخارجية بحيث تظهر في نتائج البحث من Microsoft. تعمل هذه الميزة على توسيع أنواع مصادر المحتوى التي يمكن البحث فيها في تطبيقات إنتاجية Microsoft 365 والنظام البنائي الأوسع ل Microsoft. يمكن استضافة بيانات الجهات الخارجية محليا أو في السحب العامة أو الخاصة. بدءا من eDiscovery (Premium)، نقوم بتمكين معاينة المطور لقيمة التوافق المضمنة لتطبيقات Microsoft 365 المتصلة. يتيح هذا التوافق للتطبيقات المدمجة في النظام البنائي Microsoft 365 لتمكين المستخدمين من تجارب التوافق السلسة. لمعرفة المزيد حول كيفية دمج واجهات برمجة تطبيقات Microsoft Graph Connector في طريقة عرض التطبيقات، راجع [إنشاء الاتصالات وتحديثها وحذفها في Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).

### <a name="microsoft-graph-api-for-records-management-preview"></a>Microsoft Graph API لإدارة السجلات (معاينة)

تتطلب المؤسسات من جميع الأنواع حلا لإدارة السجلات لإدارة السجلات الهامة عبر بياناتها. [إدارة سجلات Microsoft Purview](records-management.md) يساعد المنظمة على إدارة التزاماتها القانونية، ويوفر القدرة على إظهار الامتثال للوائح، ويزيد من الكفاءة مع التصرف المنتظم في العناصر التي لم تعد مطلوبة.

يتم استخدام حل إدارة السجلات من قبل المؤسسات في وحدات تخزين كبيرة للاستفادة من قدراته المختلفة في حماية بياناتها أو وصفها أو الاحتفاظ بها أو حذفها. تتيح واجهات برمجة تطبيقات Microsoft Graph لإدارة السجلات للمؤسسات إدارة تسميات الاستبقاء والإجراءات المرتبطة بها بشكل أكثر كفاءة، وأتمتة المهام المتكررة، وتزويد العملاء بالمرونة في الخيارات.

الآن، يدعم الإصدار الأول من واجهات برمجة تطبيقات الرسم البياني لإدارة السجلات إدارة تسميات الاستبقاء والاستبقاء المستند إلى الحدث. أمثلة على السيناريوهات:

- **إدارة تسميات الاستبقاء**
    
    يحتاج مسؤولو ومطورو إدارة السجلات إلى الحفاظ على أنظمة إدارة السجلات الخاصة بهم باستخدام التسميات التي يتم إنشاؤها وتحديثها وحذفها بشكل دوري.
    
    يستخدم المطورون والمسؤولون عن التوافق واجهات برمجة التطبيقات Graph لإدارة السجلات لتنفيذ عمليات CRUD على كيان التسمية للحفاظ على أنظمتهم.

- **تشغيل حدث لتسمية موجودة**
    
    عندما يترك موظف مؤسسة، يتم تحديث المعلومات في نظام إدارة الموارد البشرية. من تاريخ المغادرة، يجب الاحتفاظ بالمستندات السرية لمدة سبع سنوات. تحتوي هذه المستندات بالفعل على تسمية الاستبقاء "Employee_departure" المطبقة عليها.
    
    يستخدم المطورون والمسؤولون عن التوافق واجهات برمجة التطبيقات Graph لإدارة السجلات لقراءة التسمية "Employee_departure" والبحث عن نوع الحدث المقترن "event-employee_departure".
    
    ثم يستخدمون واجهات برمجة التطبيقات للرسم البياني لإدارة السجلات لإنشاء حدث لنوع الحدث المقترن. تبدأ فترة الاستبقاء للمستندات السرية بعد إنشاء هذا الحدث.

لمزيد من المعلومات حول واجهات برمجة تطبيقات الرسم البياني لإدارة السجلات، راجع [استخدام واجهة برمجة تطبيقات إدارة سجلات Microsoft Graph](/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-beta&preserve-view=true).

للحصول على متطلبات الترخيص لاستخدام واجهات برمجة التطبيقات هذه، راجع معلومات إدارة السجلات من إرشادات Microsoft 365 للأمان & التوافق، [إدارة دورة البيانات في Microsoft Purview & إدارة سجلات Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management--microsoft-purview-records-management) القسم.
