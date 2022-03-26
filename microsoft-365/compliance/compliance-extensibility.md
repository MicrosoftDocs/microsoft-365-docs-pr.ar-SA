---
title: Microsoft 365 التوافق
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
description: تعرف على Microsoft 365 حلول التوافق باستخدام موصلات بيانات جهة خارجية و Microsoft Graph واجهات برمجة التطبيقات.
ms.openlocfilehash: 0632de40141b86e6dfdebf3f5c3a97ca50219357
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570080"
---
# <a name="microsoft-365-compliance-and-microsoft-priva-extensibility"></a>Microsoft 365 التوافق وامتثال Microsoft Priva

Microsoft 365 حلول التوافق هذه المؤسسات على تقييم مخاطر التوافق الخاصة بها بذكاء، وإدارة البيانات الحساسة وحمايتها، والاستجابة بفعالية للمتطلبات التنظيمية. Microsoft 365 التوافق غنية بسيناريوهات قابلة للتوسعة وتمكن المؤسسات من تكييف حلول التوافق الخاصة بها وتوسيعها ودمجها وتسريعها ودعمها.

هناك كتلتان إنشاء رئيسيتان لتوسعة التوافق:

- **موصلات البيانات**. يتم استخدامها لاستيراد بيانات غير Microsoft وأرشفتها حتى تتمكن من تطبيق Microsoft 365 الحماية والحوكمة على بيانات جهة خارجية.

- **واجهات برمجة التطبيقات**. تمكين الوصول برمجيا إلى Microsoft 365 التوافق.

## <a name="data-connectors"></a>موصلات البيانات

توفر Microsoft موصلات بيانات جهة خارجية يمكن تكوينها في مركز التوافق في Microsoft 365. للحصول على قائمة بموصلات البيانات التي توفرها Microsoft، راجع جدول موصلات البيانات [من جهة](archiving-third-party-data.md#third-party-data-connectors) خارجية. يلخص جدول موصلات البيانات الخاصة ب جهة خارجية أيضا حلول التوافق التي يمكنك تطبيقها على بيانات جهة خارجية بعد استيراد البيانات وأرشفتها في Microsoft 365، بالإضافة إلى ارتباطات إلى الإرشادات خطوة بخطوة لكل موصل.

لمعرفة المزيد حول Microsoft 365 موصلات البيانات، راجع [أرشفة بيانات جهة خارجية](archiving-third-party-data.md). إذا لم يكن نوع بيانات جهة خارجية مدعوما بواسطة موصلات البيانات المتوفرة في مركز التوافق في Microsoft 365، يمكنك العمل مع شريك يمكنه تزويدك بموصل مخصص. للحصول على قائمة بالشركاء الذين يمكنك العمل معهم والعملية خطوة بخطوة لهذا الأسلوب، راجع العمل مع شريك لأرشفة [بيانات جهة خارجية](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>المتطلبات الأساسية لموصلات البيانات

تتطلب العديد من موصلات البيانات المتوفرة في مركز التوافق في Microsoft 365 لاستيراد بيانات جهة خارجية وأرشفتها إعداد مهام التكوين في مصدر البيانات الخاص ب جهة خارجية. يتم توثيق هذه المتطلبات الأساسية بالتفصيل لكل موصل بيانات جهة خارجية.

بالنسبة إلى موصلات البيانات في مركز التوافق في Microsoft 365 التي يوفرها أحد شركاء Microsoft، ستحتاج مؤسستك إلى علاقة عمل مع الشريك قبل أن تتمكن من نشر موصل.

للحصول على الإرشادات والمتطلبات المتعلقة بموصلات البيانات الخاصة ب جهة خارجية، راجع القسم "موصلات البيانات" في [إرشادات Microsoft 365 لتوافق & - أوصاف الخدمة | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>واجهات برمجة التطبيقات

Microsoft 365 التوافق و واجهات برمجة تطبيقات Microsoft Priva في حماية البيانات في Microsoft SDK و Microsoft Graph API و Office 365 API لنشاط الإدارة. بعض واجهات برمجة تطبيقات التوافق هي جزء من مجموعة جديدة من واجهات برمجة تطبيقات الأمان والتوافق التي تمكن المطورين لعملاء Microsoft 365 وموردي البرامج المستقلين وتكامل الأنظمة وموفري خدمات الأمان المدارة من إنشاء حلول أمان وتوافق عالية القيمة.

لمعرفة المزيد حول كيفية الوصول إلى Graph واجهات برمجة التطبيقات، راجع [نظرة عامة على Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>واجهات Graph برمجة تطبيقات Microsoft لطلبات حقوق الموضوع

وفقا لأنظمة خصوصية معينة حول العالم، يمكن للأفراد تقديم طلبات لمراجعة البيانات الشخصية أو إدارتها عن أنفسهم التي تقوم الشركات بتجميعها. يشار إلى هذه الطلبات بطلبات *حقوق* الموضوع ضمن حل طلبات حقوق موضوع Microsoft Priva. يشار أيضا إلى طلبات حقوق الموضوع بطلبات موضوع *البيانات (* DSRs) أو طلبات الوصول إلى موضوع *البيانات (* DSARs). تمكن Graph واجهات برمجة تطبيقات Microsoft لطلبات حقوق الموضوع المطورين من Microsoft 365 طلبات حقوق الموضوع ذات الصلة مع نظام خصوصية أوسع. تمكن إمكانية التوسعة المستندة إلى API المؤسسات من الاستجابة لطلبات حقوق الموضوع بطريقة موحدة عبر مساحة البيانات بالكامل التي تغطي بيئات Microsoft والبيئات غير الخاصة ب Microsoft. تساعد هذه الإمكانية أيضا في التنفيذ التلقائي على نطاق واسع وتساعد المؤسسات على تلبية اللوائح التنظيمية الصناعية بفعالية أكبر دون الاعتماد على العمليات اليدوية.

لمعرفة المزيد، راجع [Microsoft Graph واجهات برمجة التطبيقات لطلب حقوق الموضوع](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>حماية البيانات في Microsoft SDK (MIP)

يعرض MIP SDK خدمات التسمية والحماية من مراكز Microsoft 365 الأمان والتوافق إلى تطبيقات وخدمات  الأطراف الخارجية. يمكن للمطورين استخدام SDK لإنشاء دعم أصلي لتطبيق التسميات والحماية على الملفات. يمكن للمطورين تحديد الإجراءات التي يجب اتخاذها عند الكشف عن تسميات معينة، والسبب وراء المعلومات المشفرة باستخدام MIP.

تتضمن حالات استخدام MIP SDK عالية المستوى ما يلي:

- تطبيق خط العمل الذي يطبق تسميات التصنيف على الملفات عند التصدير.

- تطبيق تصميم CAD/CAM يوفر الدعم الأصلي لتسمية MIP.

- وسيط أمان الوصول السحابي أو حل منع فقدان البيانات الذي يمكنه تشفير البيانات باستخدام Azure Information Protection.

لمعرفة المزيد حول MIP SDK والمتطلبات الأساسية والسيناريوهات الإضافية والعينات، راجع [نظرة عامة على MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft Graph API Teams DLP

[تستخدم قدرات منع فقدان البيانات (DLP)](dlp-microsoft-teams.md) على نطاق واسع في Microsoft Teams خاصة مع تحول المؤسسات إلى العمل عن بعد. لقد [أعلنا مؤخرا](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) عن التوفر العام ل API الإعلامات Graph Microsoft للرسائل في Teams. تمكن API هذه المطورين من إنشاء تطبيقات يمكنها الاستماع Microsoft Teams الرسائل في الوقت الحقيقي تقريبا ثم تنفيذ سيناريوهات DLP لكل من العملاء والشركاء. بالإضافة إلى ذلك، Graph API ل Microsoft تطبيق إجراءات DLP Teams الرسائل.

تشكل واجهات برمجة التطبيقات هاتين Graph API Teams DLP. يمكنك البدء من خلال تجربة [التطبيق النموذجي](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). لمزيد من المعلومات حول Microsoft Teams ويب للمراسلة، راجع [الوثائق](/graph/api/subscription-post-subscriptions).

للحصول على متطلبات الترخيص Teams DLP، راجع Microsoft 365 إرشادات الترخيص [لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft Graph API ل eDiscovery (معاينة)

باستخدام [Advanced eDiscovery](overview-ediscovery-20.md)، يمكن أن تكتشف المؤسسات البيانات التي تعيش فيها، وتدير المزيد من مهام سير عمل eDiscovery بشكل منته باستخدام قدرات ذكية للتعلم الآلي والتحليلات لتقليل البيانات إلى المجموعة ذات الصلة ، كل ذلك بينما تبقى البيانات ضمن حدود الأمان والتوافق في Microsoft 365.

Graph واجهات برمجة التطبيقات Advanced eDiscovery يمكن استخدامها لإنشاء الحالات وإدارتها ومراجعة مجموعات الاستعلامات ومراجعة مجموعة الاستعلامات بطريقة قابلة للتكرار وقابلة للتكرار. يمكن ذلك العملاء والشركاء من إنشاء تطبيقات ومسيرات عمل لأتمتة العمليات الشائعة والمكررة مثل إنشاء الحالات وإدارة عاملين في عمليات الاحتجاز والحجز القانوني.

تتوفر المجموعة الأولى من Graph برمجة التطبيقات ل eDiscovery في المعاينة العامة. نخطط لإضافة المزيد من الإمكانات بنهاية سنة التقويم. لمعرفة المزيد حول واجهات برمجة التطبيقات هذه والتحديثات الأخرى Advanced eDiscovery، راجع هذه [المدونة](https://aka.ms/Ignite2020AeDAA).

للحصول على متطلبات الترخيص ل Advanced eDiscovery وPI( API)، راجع القسم "eDiscovery" في Microsoft 365 إرشادات الترخيص [لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft Graph API Teams تصدير

أرشفة معلومات المؤسسة (EIA) Microsoft Teams هو سيناريو رئيسي لعملائنا حيث إنه يسمح لهم بحل المتطلبات التنظيمية. بالإضافة إلى إمكانياتنا المضمنة لأرشفة المحتوى في Microsoft Teams، يمكن للعملاء والشركاء الآن استخدام Teams واجهات برمجة تطبيقات التصدير لحل سيناريوهات التطبيق والتكامل المخصصة. تدعم Teams واجهات برمجة تطبيقات التصدير التصدير المجمع (ما يصل إلى 200 طلب لكل ثانية/لكل تطبيق/لكل مستأجر) للرسائل Teams ومرفقات الرسائل. يمكن أيضا الوصول إلى الرسائل المحذوفة بواسطة API لمدة تصل إلى 30 يوما بعد حذفها. لمزيد من المعلومات حول هذه Teams واجهات برمجة تطبيقات التصدير وكيفية استخدامها في تطبيقاتك، راجع تصدير المحتوى باستخدام Microsoft Teams [واجهات برمجة تطبيقات التصدير](/microsoftteams/export-teams-content).

للحصول على متطلبات الترخيص لاستخدام واجهات برمجة التطبيقات Teams تصدير، راجع Microsoft 365 إرشادات الترخيص [لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>واجهات برمجة تطبيقات Graph Microsoft (معاينة)

باستخدام [موصلات microsoft Graph](/microsoftsearch/connectors-overview)، يمكن أن تقوم المؤسسات بفهرسة بيانات جهة خارجية بحيث تظهر في البحث من Microsoft النتائج. تعمل هذه الميزة على توسيع أنواع مصادر المحتوى التي يمكن البحث عنها في تطبيقات Microsoft 365 الإنتاجية والنظام البيئي ل Microsoft على نطاق أوسع. يمكن استضافة بيانات  الأطراف الخارجية في سحابات عامة أو خاصة. بدءا من Advanced eDiscovery، نحن نعمل على تمكين معاينة المطور لقيمة التوافق المضمنة للتطبيقات Microsoft 365 المتصلة. يمكن ذلك التوافق للتطبيقات التي يتم دمجها في Microsoft 365 لتمكين المستخدمين من تجارب التوافق السلسة. لمعرفة المزيد حول كيفية تضمين Microsoft Graph واجهات برمجة تطبيقات الموصل في طريقة عرض التطبيقات، راجع إنشاء اتصالات وتحديثها [وحذفها في Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).
