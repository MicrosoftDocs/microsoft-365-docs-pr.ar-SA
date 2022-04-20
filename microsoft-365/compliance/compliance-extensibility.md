---
title: إمكانية توسعة Microsoft Purview
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: تعرف على توسيع حلول Microsoft Purview باستخدام موصلات بيانات تابعة لجهة خارجية وMicrosoft Graph واجهات برمجة التطبيقات.
ms.openlocfilehash: e61cd2dfa8121a0925cc89fd5373569d9697936a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64942744"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>إمكانية توسعة Microsoft Purview وMicrosoft Priva

تساعد حلول Microsoft Purview المؤسسات على تقييم مخاطر الامتثال الخاصة بها بذكاء، وتحكم البيانات الحساسة وتحميها، وتستجيب بفعالية للمتطلبات التنظيمية. يعد Microsoft Purview غنيا بسيناريوهات قابلية التوسع ويمكن المؤسسات من تكييف حلول الامتثال وتوسيعها ودمجها وتسريعها ودعمها.

هناك كتلتان أساسيتان أساسيتان لإمكانية توسعة الامتثال:

- **موصلات البيانات**. يستخدم لاستيراد بيانات غير تابعة ل Microsoft وأرشفتها حتى تتمكن من تطبيق قدرات الحماية والحوكمة Microsoft 365 على بيانات الجهات الخارجية.

- **واجهات برمجة التطبيقات**. تمكين الوصول البرمجي إلى قدرات Microsoft Purview.

## <a name="data-connectors"></a>موصلات البيانات

توفر Microsoft موصلات بيانات تابعة لجهة خارجية يمكن تكوينها في مدخل توافق Microsoft Purview. للحصول على قائمة بموصلات البيانات التي توفرها Microsoft، راجع جدول [موصلات البيانات التابعة لجهة خارجية](archiving-third-party-data.md#third-party-data-connectors) . يلخص جدول موصلات البيانات التابعة لجهة خارجية أيضا حلول التوافق التي يمكنك تطبيقها على بيانات الجهات الخارجية بعد استيراد البيانات وأرشفتها في Microsoft 365، وارتباطات إلى الإرشادات المفصلة خطوة بخطوة لكل موصل.

لمعرفة المزيد حول موصلات البيانات Microsoft 365، راجع [أرشفة بيانات الجهات الخارجية](archiving-third-party-data.md). إذا لم يكن نوع بيانات جهة خارجية مدعوما من قبل موصلات البيانات المتوفرة في مدخل التوافق، يمكنك العمل مع شريك يمكنه تزويدك بموصل مخصص. للحصول على قائمة بالشركاء الذين يمكنك العمل معهم والعملية المفصلة خطوة بخطوة لهذا الأسلوب، راجع ["العمل مع شريك" لأرشفة بيانات الجهات الخارجية](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>المتطلبات الأساسية لموصلات البيانات

تتطلب العديد من موصلات البيانات المتوفرة في مدخل التوافق لاستيراد بيانات الجهات الخارجية وأرشفتها إعداد مهام التكوين وتنفيذها في مصدر بيانات الجهات الخارجية. يتم توثيق هذه المتطلبات الأساسية بالتفصيل لكل موصل بيانات تابع لجهة خارجية.

بالنسبة إلى موصلات البيانات في مدخل التوافق الذي يوفره أحد شركاء Microsoft، ستحتاج مؤسستك إلى علاقة عمل مع الشريك قبل أن تتمكن من نشر موصل.

للحصول على إرشادات ومتطلبات موصلات البيانات التابعة لجهة خارجية، راجع قسم "موصلات البيانات" في [إرشادات Microsoft 365 للأمان & التوافق - أوصاف الخدمة | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>واجهات برمجه التطبيقات

تتوفر واجهات برمجة تطبيقات Microsoft Purview وMicrosoft Priva في حماية البيانات في Microsoft SDK وMicrosoft Graph API وواجهة برمجة تطبيقات نشاط الإدارة Office 365. تعد بعض واجهات برمجة التطبيقات للامتثال جزءا من مجموعة جديدة من واجهات برمجة تطبيقات الأمان والتوافق التي تمكن المطورين للعملاء Microsoft 365 وموردي البرامج المستقلين ومكاملي النظام وموفري خدمات الأمان المدارة من إنشاء حلول أمان وتوافق عالية القيمة.

لمعرفة المزيد حول كيفية الوصول إلى واجهات برمجة التطبيقات Graph، راجع [نظرة عامة على Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Microsoft Graph واجهات برمجة التطبيقات لطلبات حقوق الموضوع

وفقا لبعض لوائح الخصوصية في جميع أنحاء العالم، يمكن للأفراد تقديم طلبات لمراجعة أو إدارة البيانات الشخصية المتعلقة بأنفسهم التي جمعتها الشركات. يشار إلى هذه الطلبات *بطلبات حقوق الموضوع* ضمن حل طلبات حقوق موضوع Microsoft Priva. يشار أيضا إلى طلبات حقوق الموضوع *بطلبات موضوع البيانات* (DSRs) أو *طلبات الوصول إلى موضوع البيانات* (DSARs). تمكن واجهات برمجة تطبيقات Microsoft Graph لطلبات حقوق الموضوع المطورين من دمج طلبات حقوق الموضوع المتعلقة Microsoft 365 مع نظام الخصوصية البنائي الأوسع. تتيح إمكانية التوسع المستندة إلى واجهة برمجة التطبيقات هذه للمؤسسات الاستجابة لطلبات حقوق الموضوع بطريقة موحدة عبر ملكية البيانات بأكملها التي تغطي كل من بيئات Microsoft والبيئات غير التابعة ل Microsoft. تساعد هذه الإمكانية أيضا في الأتمتة على نطاق واسع وتساعد المؤسسات على تلبية اللوائح الصناعية بشكل أكثر كفاءة دون الاعتماد على العمليات اليدوية.

لمعرفة المزيد، راجع [واجهات برمجة تطبيقات Microsoft Graph لطلب حقوق الموضوع](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>حماية البيانات في Microsoft (MIP) SDK

تعرض MIP SDK خدمات التسمية والحماية من مراكز الأمان والتوافق Microsoft 365 لتطبيقات وخدمات الجهات الخارجية. يمكن للمطورين استخدام SDK لإنشاء دعم أصلي لتطبيق التسميات والحماية على الملفات. يمكن للمطورين تحديد الإجراءات التي يجب اتخاذها عند الكشف عن تسميات معينة، والسبب في المعلومات المشفرة بواسطة MIP.

تتضمن حالات استخدام MIP SDK عالية المستوى ما يلي:

- تطبيق خط العمل الذي يطبق تسميات التصنيف على الملفات عند التصدير.

- تطبيق تصميم CAD/CAM الذي يوفر دعما أصليا لأوصاف الحساسية.

- وسيط أمان الوصول إلى السحابة أو حل منع فقدان البيانات الذي يمكنه تشفير البيانات باستخدام azure حماية البيانات.

لمعرفة المزيد حول MIP SDK والمتطلبات الأساسية والسيناريوهات الإضافية والعينات، راجع [نظرة عامة على MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft Graph API ل DLP Teams

تستخدم قدرات [منع فقدان البيانات (DLP)](dlp-microsoft-teams.md) على نطاق واسع في Microsoft Teams خاصة مع تحول المؤسسات إلى العمل عن بعد. [أعلنا مؤخرا عن التوفر العام](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) ل Microsoft Graph Change Notification API للرسائل في Teams. تمكن واجهة برمجة التطبيقات هذه المطورين من إنشاء تطبيقات يمكنها الاستماع إلى رسائل Microsoft Teams في الوقت الفعلي تقريبا ثم تنفيذ سيناريوهات DLP لكل من العملاء والشركاء. بالإضافة إلى ذلك، يتيح لك Microsoft Graph Patch API تطبيق إجراءات DLP على الرسائل Teams.

تشكل واجهات برمجة التطبيقات هاتين واجهة برمجة تطبيقات Microsoft Graph ل DLP Teams. يمكنك البدء بتجربة [نموذج التطبيق](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). لمزيد من المعلومات حول Microsoft Teams خطافات الويب للمراسلة، راجع [الوثائق](/graph/api/subscription-post-subscriptions).

للحصول على متطلبات الترخيص Teams DLP، راجع [إرشادات الترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft Graph API ل eDiscovery (معاينة)

باستخدام [eDiscovery (Premium)](overview-ediscovery-20.md)، يمكن للمؤسسات اكتشاف البيانات حيث تقيم، وإدارة المزيد من مهام سير عمل eDiscovery الشاملة مع قدرات ذكية للتعلم الآلي والتحليلات لتقليل البيانات إلى المجموعة ذات الصلة - كل ذلك بينما تظل البيانات داخل حدود الأمان والتوافق Microsoft 365.

يمكن استخدام واجهات برمجة التطبيقات Graph ل eDiscovery (Premium) لإنشاء الحالات وإدارتها، ومراجعة المجموعات، ومراجعة استعلامات المجموعة بطريقة قابلة للتطوير وقابلة للتكرار. وهذا يمكن العملاء والشركاء من إنشاء التطبيقات وسير العمل لأتمتة العمليات الشائعة والمتكررة مثل إنشاء الحالات وإدارة أمناء الحفظ والموقوفين القانونيين.

تتوفر المجموعة الأولى من واجهات برمجة التطبيقات Graph ل eDiscovery في المعاينة العامة. نخطط لإضافة المزيد من القدرات بحلول نهاية السنة التقويمية. لمعرفة المزيد حول واجهات برمجة التطبيقات هذه والتحديثات الأخرى ل eDiscovery (Premium)، راجع هذه [المدونة](https://aka.ms/Ignite2020AeDAA).

للحصول على متطلبات الترخيص ل eDiscovery (Premium) وواجهة برمجة التطبيقات، راجع قسم "eDiscovery" في [إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft Graph API لتصدير Teams

أرشفة معلومات المؤسسة (EIA) Microsoft Teams هو سيناريو رئيسي لعملائنا لأنه يسمح لهم بحل المتطلبات التنظيمية. بالإضافة إلى قدراتنا المضمنة لأرشفة المحتوى في Microsoft Teams، يمكن للعملاء والشركاء الآن استخدام Teams تصدير واجهات برمجة التطبيقات لحل سيناريوهات التطبيق والتكامل المخصصة. تدعم Teams Export APIs التصدير المجمع (ما يصل إلى 200 طلب في الثانية/لكل تطبيق/لكل مستأجر) من رسائل Teams ومرفقات الرسائل. يمكن أيضا الوصول إلى الرسائل المحذوفة بواسطة واجهة برمجة التطبيقات لمدة تصل إلى 30 يوما بعد حذفها. لمزيد من المعلومات حول هذه Teams تصدير واجهات برمجة التطبيقات وكيفية استخدامها في تطبيقاتك، راجع [تصدير المحتوى باستخدام واجهات برمجة تطبيقات التصدير Microsoft Teams](/microsoftteams/export-teams-content).

للحصول على متطلبات الترخيص لاستخدام واجهات برمجة تطبيقات تصدير Teams، راجع [إرشادات الترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Microsoft Graph Connector APIs (معاينة)

باستخدام [موصلات Microsoft Graph](/microsoftsearch/connectors-overview)، يمكن للمؤسسات فهرسة بيانات الجهات الخارجية بحيث تظهر في نتائج البحث من Microsoft. تعمل هذه الميزة على توسيع أنواع مصادر المحتوى التي يمكن البحث فيها في تطبيقات الإنتاجية Microsoft 365 والنظام البنائي الأوسع ل Microsoft. يمكن استضافة بيانات الجهات الخارجية محليا أو في السحب العامة أو الخاصة. بدءا من eDiscovery (Premium)، نقوم بتمكين معاينة المطور لقيمة التوافق المضمنة للتطبيقات المتصلة Microsoft 365. وهذا يتيح التوافق للتطبيقات المدمجة في النظام البنائي Microsoft 365 لتمكين المستخدمين من تجارب الامتثال السلسة. لمعرفة المزيد حول كيفية دمج واجهات برمجة تطبيقات Microsoft Graph Connector في طريقة عرض تطبيقاتك، راجع [إنشاء الاتصالات وتحديثها وحذفها في microsoft Graph](/graph/connecting-external-content-connectors-api-overview).
