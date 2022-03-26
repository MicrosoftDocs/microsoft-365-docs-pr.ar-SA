---
title: استخدم موصلات البيانات لاستيراد بيانات جهة خارجية وأرشفتها في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية استيراد بيانات جهة خارجية وأرشفتها من الأنظمة الأساسية لل الوسائط الاجتماعية و الأنظمة الأساسية للمراسلة الفورية و الأنظمة الأساسية لتعاون المستندات Microsoft 365 علب البريد.
ms.openlocfilehash: 06833acd3ea29e30d8789fbb05e0a081309c7f2b
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/15/2022
ms.locfileid: "63566707"
---
# <a name="learn-about-connectors-for-third-party-data"></a>التعرف على الموصلات لبيانات  الأطراف الخارجية

Microsoft 365 للمسؤولين استخدام موصلات البيانات لاستيراد بيانات غير Microsoft أو كيانات خارجية أو أرشفتها من الأنظمة الأساسية لل الوسائط الاجتماعية ونظم المراسلة الفورية ونظم التعاون في العمل على المستندات إلى علب البريد في Microsoft 365 الخاصة بك. إحدى الفوائد الأساسية لاستخدام موصلات البيانات لاستيراد بيانات جهة خارجية وأرشفتها في Microsoft 365 هي أنه يمكنك تطبيق حلول توافق Microsoft 365 مختلفة للبيانات بعد استيرادها. يساعدك ذلك على ضمان توافق البيانات غير الخاصة ب Microsoft في مؤسستك مع اللوائح والمعايير التي تؤثر على مؤسستك.

شاهد هذا الدليل التفاعلي الذي يوضح كيفية إنشاء موصلات بيانات لاستيراد بيانات جهة خارجية وأرشفتها وأمثلة حول تطبيق حلول التوافق على البيانات بعد استيرادها إلى Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>موصلات بيانات جهة خارجية

يوفر مركز التوافق في Microsoft 365 موصلات بيانات أصلية من Microsoft لاستيراد بيانات من مصادر بيانات مختلفة، مثل LinkedIn وSwit Bloomberg وTwitter وموصلات البيانات التي تدعم حل إدارة مخاطر Insider. بالإضافة إلى موصلات البيانات هذه، تعمل Microsoft مع الشركاء التاليين لتوفير المزيد من موصلات بيانات الجزء الثالث في مركز التوافق في Microsoft 365. تعمل مؤسستك مع هؤلاء الشركاء لإعداد خدمة الأرشفة الخاصة بهم قبل إنشاء موصل بيانات مقابل في مركز التوافق في Microsoft 365.

- [Veritas](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

يتم استيراد بيانات  الأطراف الخارجية المدرجة في الأقسام التالية (باستثناء بيانات الموارد البشرية وبيانات سوء الاستخدام الفعلية المستخدمة لحل إدارة مخاطر Microsoft 365 Insider) إلى علب بريد المستخدمين. يتم Microsoft 365 حلول التوافق التي تدعم بيانات جهة خارجية على علبة بريد المستخدم حيث يتم تخزين البيانات.

### <a name="microsoft-data-connectors"></a>موصلات بيانات Microsoft

يسرد الجدول التالي موصلات البيانات الأصلية المتوفرة في مركز التوافق في Microsoft 365. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها بعد استيراد بيانات جهة خارجية وأرشفتها في Microsoft 365. راجع القسم [نظرة](#overview-of-compliance-solutions-that-support-third-party-data) عامة حول حلول التوافق التي تدعم بيانات جهة خارجية للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات جهة خارجية.

انقر فوق الارتباط في **عمود** البيانات الخاص ب جهة خارجية للحصول على الإرشادات خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

|بيانات جهة خارجية  |الاحتجاز في الدعاوى القضائية|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة مخاطر Insider  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[رسالة بلومبرغ](archive-bloomberg-message-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)||
|[الرعاية الصحية في Epic EHR](import-epic-data.md) ||||||![علامة الاختيار](../media/checkmark.png)|
|[Facebook](archive-facebook-data-with-sample-connector.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[الرعاية الصحية العامة ل EHR](import-healthcare-data.md) ||||||![علامة الاختيار](../media/checkmark.png)|
|[الموارد البشرية (HR)](import-hr-data.md) ||||||![علامة الاختيار](../media/checkmark.png)|
|[ICE Chat](archive-icechat-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[الازدوج الفعلي](import-physical-badging-data.md) ||||||![علامة الاختيار](../media/checkmark.png)|
|[Slack eDiscovery](archive-slack-data-microsoft.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>موصلات بيانات Veritas

يسرد الجدول في هذا القسم موصلات بيانات  توفرها جهة خارجية والمتوفرة في شراكة مع Veritas. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات جهة خارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع القسم [نظرة](#overview-of-compliance-solutions-that-support-third-party-data) عامة حول حلول التوافق التي تدعم بيانات جهة خارجية للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات جهة خارجية.

قبل أن تتمكن من أرشفة بيانات جهة خارجية في Microsoft 365، يجب العمل مع Veritas لإعداد خدمة الأرشفة الخاصة بها (تسمى *Merge1*) لم المؤسسة. للحصول على مزيد من المعلومات، انقر فوق الارتباط  في عمود البيانات الخاص ب جهة خارجية للحصول على الإرشادات خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

|بيانات جهة خارجية  |الاحتجاز في الدعاوى القضائية|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة مخاطر Insider  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Cisco Jabber على MS SQL](archive-ciscojabberonmssql-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Cisco Jabber على Oracle](archive-ciscojabberonoracle-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Cisco Jabber على PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[FX الاتصال](archive-fxconnect-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[MS SQL البيانات](archive-mssqldatabaseimporter-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[Pivot](archive-pivot-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[التعامل مع رويتر](archive-reutersdealing-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Salesforce Chatter](archive-salesforcechatter-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[Skype for Business](archive-skypeforbusiness-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Slack eDiscovery](archive-slack-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[السيمفونية](archive-symphony-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[تم فرز النص](archive-text-delimited-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[صفحات ويب](archive-webpagecapture-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[مساحة العمل من Facebook](archive-workplacefromfacebook-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|||
|[اجتماعات التكبير/التصغير](archive-zoommeetings-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>موصلات بيانات TeleMessage

يسرد الجدول في هذا القسم موصلات بيانات  توفرها جهة خارجية والمتوفرة في شراكة مع TeleMessage. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات جهة خارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع القسم [نظرة](#overview-of-compliance-solutions-that-support-third-party-data) عامة حول حلول التوافق التي تدعم بيانات جهة خارجية للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات جهة خارجية.

قبل أن تتمكن من أرشفة بيانات جهة خارجية في Microsoft 365، يجب العمل على TeleMessage لإعداد خدمة الأرشفة لم المؤسسة. للحصول على مزيد من المعلومات، انقر فوق الارتباط  في عمود البيانات الخاص ب جهة خارجية للحصول على الإرشادات خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

تتوفر أيضا موصلات بيانات TeleMessage في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. لمزيد من المعلومات، راجع المقطع [موصلات البيانات في سحابة الحكومة](#data-connectors-in-the-us-government-cloud) الأمريكية في هذه المقالة.

|بيانات جهة خارجية  |الاحتجاز في الدعاوى القضائية|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة مخاطر Insider  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[Android](archive-android-archiver-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[AT&T Network](archive-att-network-archiver-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Bell Network](archive-bell-network-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[رقم المؤسسة](archive-enterprise-number-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[O2 Network](archive-o2-network-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[شبكة باهية](archive-rogers-network-archiver-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[إشارة](archive-signal-archiver-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[برقية](archive-telegram-archiver-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[TELUS Network](archive-telus-network-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[WhatsApp](archive-whatsapp-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>17a-4 موصلات بيانات

يسرد الجدول في هذا القسم موصلات بيانات  توفرها جهة خارجية والمتوفرة في شراكة مع 17a-4 LLC. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات جهة خارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع القسم [نظرة](#overview-of-compliance-solutions-that-support-third-party-data) عامة حول حلول التوافق التي تدعم بيانات جهة خارجية للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات جهة خارجية.

قبل أن تتمكن من أرشفة بيانات جهة خارجية في Microsoft 365، يجب العمل مع 17a-4 LLC لإعداد خدمة الأرشفة الخاصة بها (تسمى *DataParser*) لم المؤسسة. للحصول على مزيد من المعلومات، انقر فوق الارتباط  في عمود البيانات الخاص ب جهة خارجية للحصول على الإرشادات خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

تتوفر أيضا موصلات البيانات 17a-4 في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. لمزيد من المعلومات، راجع المقطع [موصلات البيانات في سحابة الحكومة](#data-connectors-in-the-us-government-cloud) الأمريكية في هذه المقالة.

|بيانات جهة خارجية  |الاحتجاز في الدعاوى القضائية|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة مخاطر Insider  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[BlackBerry](archive-17a-4-blackberry-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[بلومبرغ](archive-17a-4-bloomberg-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[FactSet](archive-17a-4-factset-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Fuze](archive-17a-4-fuze-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[FX الاتصال](archive-17a-4-fxconnect-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[ICE Chat](archive-17a-4-ice-im-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[LivePerson Conversational Cloud](archive-17a-4-liveperson-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Quip](archive-17a-4-quip-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
[Skype for Business Server](archive-17a-4-skype-for-business-server-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[فترة Slack](archive-17a-4-slack-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[السيمفونية](archive-17a-4-symphony-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
|[تكبير/تصغير](archive-17a-4-zoom-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>موصلات بيانات CellTrust

يسرد الجدول في هذا القسم موصل البيانات الخاص ب جهة خارجية والمتوفر في شراكة مع CellTrust. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات جهة خارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع القسم [نظرة](#overview-of-compliance-solutions-that-support-third-party-data) عامة حول حلول التوافق التي تدعم بيانات جهة خارجية للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات جهة خارجية.

قبل أن تتمكن من أرشفة بيانات جهة خارجية في Microsoft 365، يجب العمل مع CellTrust لإعداد خدمة الأرشفة الخاصة بها (تسمى *CellTrust SL2*) لمنظمتك. لمزيد من المعلومات، انقر فوق الارتباط في عمود  بيانات جهة خارجية للحصول على الإرشادات خطوة بخطوة لإنشاء موصل CellTrust SL2.

|بيانات جهة خارجية  |الاحتجاز في الدعاوى القضائية|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة مخاطر Insider  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)|![علامة الاختيار](../media/checkmark.png)||
||||||||

يتوفر موصل بيانات CellTrust SL2 أيضا في بيئات سحابة القطاع الحكومي في Microsoft 365 الحكومة الأمريكية. لمزيد من المعلومات، راجع المقطع [موصلات البيانات في سحابة الحكومة](#data-connectors-in-the-us-government-cloud) الأمريكية في هذه المقالة.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>نظرة عامة حول حلول التوافق التي تدعم بيانات  الأطراف الخارجية

تصف الأقسام التالية بعض الأمور التي يمكن أن تساعدك Microsoft 365 حلول التوافق على إدارة بيانات  الأطراف الخارجية المدرجة في الجدول السابق.

### <a name="litigation-hold"></a>الاحتجاز في الدعاوى القضائية

يمكنك وضع الاحتجاز [بسبب الدعاوى](create-a-litigation-hold.md) القضائية على علبة بريد مستخدم للاحتفاظ بالبيانات الخاصة بجهة خارجية. عند إنشاء فترة الانتظار، يمكنك تحديد مدة الانتظار (تسمى أيضا فترة الانتظار المستندة إلى *الوقت) بحيث* يتم الاحتفاظ بالبيانات التي تم حذفها وتعديلها من جهة خارجية لفترة محددة ثم يتم حذفها نهائيا من علبة البريد. أو يمكنك الاحتفاظ بالمحتوى إلى أجل غير مسمى (يسمى الاحتجاز غير *المحدود) أو* حتى تتم إزالة الاحتجاز في الدعاوى القضائية.

### <a name="ediscovery"></a>eDiscovery

أدوات eDiscovery الأساسية الثلاثة في Microsoft 365 هي البحث في المحتوى و eDiscovery الأساسي Advanced eDiscovery.

- **[البحث في المحتوى](content-search.md).** يمكنك استخدام أداة البحث في المحتوى للبحث في علب البريد عن بيانات جهة خارجية قمت باستيرادها. يمكنك استخدام استعلامات البحث والشروط لتضييق نطاق نتائج البحث وتصدير نتائج البحث.

- **[eDiscovery الأساسي](get-started-core-ediscovery.md).** تقوم هذه الأداة بالبنية على وظيفة البحث والتصدير الأساسية من خلال تمكينك من إنشاء حالات تتيح لك التحكم في من يمكنه الوصول إلى بيانات حالة الدعوى، أو وضع وضع الانتظار على علب بريد المستخدمين أو محتوى علبة البريد الذي يتطابق مع معايير البحث. وهذا يعني أنه يمكنك وضع eDiscovery في وضع الاحتفاظ بالبيانات التي تم استيرادها إلى علب بريد المستخدمين.

- **[Advanced eDiscovery](overview-ediscovery-20.md).** تقوم هذه الأداة القوية بتوسيع وظيفة حالة eDiscovery الأساسية من خلال السماح لك بإضافة اُمتكينين إلى حالة، ووضع بيانات المتسلل قيد الانتظار، ثم تحميل بيانات جهة خارجية لمعيد الرعاية في مراجعة لمزيد من التحليل مثل المحتوى والكشف المكرر. بعد تحميل بيانات جهة خارجية إلى مجموعة مراجعة، يمكنك الاستعلام عنها وتصفيتها إلى مجموعة نتائج ضيقة.

   تسمح لك كل من eDiscovery الأساسي Advanced eDiscovery بإدارة بيانات الجهات الخارجية التي قد تكون ذات صلة بالتحقيقات القانونية أو الداخلية في مؤسستك.

### <a name="retention-settings"></a>إعدادات الاستبقاء

يمكنك تطبيق نهج [استبقاء](retention.md) على علب بريد المستخدمين للاحتفاظ بالبيانات الخاصة بجهة خارجية (ومحتوى علبة البريد الأخرى) ثم حذفها بعد انتهاء فترة الاستبقاء. يمكنك أيضا استخدام سياسات الاستبقاء لحذف بيانات جهات خارجية من عمر معين أو استخدام تسميات الاستبقاء لتحريك مراجعة الترتيب عند انتهاء فترة استبقاء بيانات الأطراف الخارجية.[](disposition.md)

### <a name="records-management"></a>إدارة السجلات

تتيح [لك ميزة إدارة](records-management.md) السجلات في Microsoft 365 الإعلان عن بيانات جهة خارجية كسجل. يمكن إجراء ذلك يدويا من قبل المستخدمين الذين يطبقون تسمية استبقاء وضع علامة على بيانات جهة خارجية في علبة بريدهم كسجل. أو يمكنك تطبيق تسميات الاستبقاء بشكل تلقائي من خلال تحديد المعلومات الحساسة أو الكلمات الأساسية أو أنواع المحتويات في بيانات  الأطراف الخارجية.

### <a name="communication-compliance"></a>توافق الاتصالات

يمكنك استخدام [توافق الاتصالات](communication-compliance.md) لفحص بيانات جهة خارجية للتأكد من توافقها مع معايير بيانات مؤسستك. يمكنك القيام بذلك من خلال الكشف عن إجراءات المعالجة الخاصة بالرسائل غير المناسبة في مؤسستك، والتقاطها، وأخذها. على سبيل المثال، يمكنك مراقبة بيانات الجهات الخارجية التي تستوردها للغة مسيئة ومعلومات حساسة وتوافق تنظيمي.

### <a name="insider-risk-management"></a>إدارة مخاطر Insider

يمكن استخدام الإشارات من بيانات جهة خارجية، مثل بيانات الموارد البشرية الاختيارية، بواسطة حل إدارة مخاطر [Insider](insider-risk-management.md) لتقليل المخاطر الداخلية من خلال السماح لك بالكشف عن الأنشطة المعرضة للمخاطر في مؤسستك، والتحري عنها، والعمل عليها. على سبيل المثال، يتم استخدام البيانات المستوردة بواسطة موصل بيانات الموارد البشرية كمؤشرات مخاطر للمساعدة في الكشف عن عمليات سرقة بيانات الموظفين المغادرين.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>استخدام أدوات eDiscovery للبحث عن بيانات جهة خارجية

بعد استخدام موصلات البيانات لاستيراد بيانات جهة خارجية وأرشفتها في علب بريد المستخدمين، يمكنك استخدام Microsoft 365 eDiscovery للبحث عن بيانات جهة خارجية. يمكنك أيضا أدوات eDiscovery لإنشاء عمليات الاحتفاظ المستندة إلى الاستعلام المقترنة ب eDiscovery الأساسية Advanced eDiscovery للحفاظ على بيانات  الأطراف الخارجية. لمزيد من المعلومات حول أدوات eDiscovery، راجع [حلول eDiscovery في](ediscovery.md) Microsoft 365.

للبحث عن (أو وضع الانتظار) أي نوع من أنواع بيانات  الأطراف الخارجية التي قمت باستيرادها إلى علب بريد المستخدمين باستخدام موصل بيانات، يمكنك استخدام استعلام البحث التالي. تأكد من تحديد نطاق البحث لعلب بريد المستخدمين.

```powershell
kind:externaldata
```

يمكنك استخدام هذا الاستعلام في المربع كلمات  أساسية للبحث في المحتوى، أو بحث مقترن ب حالة eDiscovery الأساسية، أو مجموعة في Advanced eDiscovery.

![استعلام للبحث عن بيانات جهة خارجية.](..\media\SearchThirdPartyData1.png)

يمكنك أيضا استخدام زوج `kind:externaldata` الخاصية:القيمة لتضييق نطاق عمليات البحث إلى بيانات جهة خارجية. على سبيل المثال، للبحث عن العناصر المستوردة من أي مصدر بيانات جهة خارجية يحتوي على الكلمة *contoso* في الخاصية **Subject** الخاصة بالعنصر المستورد، استخدم الاستعلام التالي في المربع **الكلمات الأساسية:**

```powershell
subject:contoso AND kind:externaldata
```

بدلا من ذلك، يمكنك **استخدام شرط نوع** الرسالة لتكوين الاستعلام نفسه.

![استخدم شرط نوع الرسالة لتضييق نطاق عمليات البحث إلى بيانات جهة خارجية.](..\media\SearchThirdPartyData2.png)

للبحث عن نوع معين من بيانات الأطراف الخارجية المؤرشفة، استخدم خاصية **علبة بريد** فئة العناصر في استعلام بحث. استخدم الخاصية التالية:تنسيق القيمة:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

يتضمن كل عنصر يتم استيراده بواسطة موصل بيانات جهة خارجية خاصية **فئة** العناصر مع قيمة تتطابق مع نوع البيانات الخاص ب جهة خارجية. على سبيل المثال، للبحث عن بيانات Facebook التي تحتوي على الكلمة *contoso*، في خاصية **الموضوع** الخاصة بالعنصر المستورد، استخدم الاستعلام التالي:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

فيما يلي بعض الأمثلة لقيم **فئة** العناصر لأنواع مختلفة من بيانات الأطراف الخارجية.

| **نوع بيانات جهة خارجية** | **قيمة للممتلكات itemclass**   |
|---------------------------|-------------------------------------|
| رسالة بلومبرغ         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| WhatsApp Archiver         | ipm.externaldata.whatsapparchiver* |
|||

لا *تتحسس قيم الخاصية itemclass* حالة التحسس. بشكل عام، استخدم اسم نوع بيانات جهة خارجية (بدون مسافات) متبوعة حرف بدل ( * ) .

لمزيد من المعلومات حول إنشاء استعلامات بحث eDiscovery، راجع استعلامات الكلمات الأساسية [وشروط البحث ل eDiscovery](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>موصلات البيانات في السحابة "الحكومة الأمريكية"

تتوفر بعض موصلات البيانات في السحابة "الحكومة الأمريكية". تشير الأقسام التالية إلى بيئات حكومية معينة تدعم موصلات بيانات جهة خارجية. لمزيد من المعلومات حول سحب الحكومة الأمريكية، راجع Microsoft 365 [الحكومة الأمريكية](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>موصلات بيانات Veritas في سحابة الحكومة الأمريكية (معاينة)

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي High  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust| نعم | لا | لا |
|Cisco Jabber على MS SQL| نعم | لا | لا |
|Cisco Jabber على Oracle| نعم | لا | لا |
|Cisco Jabber على PostgreSQL| نعم | لا | لا |
|EML| نعم | لا | لا |
|FX الاتصال| نعم | لا | لا |
|Jive| نعم | لا | لا |
|MS SQL البيانات| نعم | لا | لا |
|Pivot| نعم | لا | لا |
|Redtail Speak| نعم | لا | لا |
|التعامل مع رويتر| نعم | لا | لا |
|Reuters Eikon| نعم | لا | لا |
|Reuters FX| نعم | لا | لا |
|RingCentral| نعم | لا | لا |
|Salesforce Chatter| نعم | لا | لا |
|ServiceNow| نعم | لا | لا |
|Skype for Business| نعم | لا | لا |
|Slack eDiscovery| نعم | لا | لا |
|السيمفونية| نعم | لا | لا |
|تم فرز النص| نعم | لا | لا |
|Twitter| نعم | لا | لا |
|Webex Teams| نعم | لا | لا |
|صفحات ويب| نعم | لا | لا |
|مساحة العمل من Facebook| نعم | لا | لا |
|XIP| نعم | لا | لا |
|XSLT/XML| نعم | لا | لا |
|Yieldbroker| نعم | لا | لا |
|YouTube| لا | لا | لا |
|اجتماعات التكبير/التصغير| نعم | لا | لا |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>موصلات بيانات TeleMessage في السحابة "الحكومة الأمريكية"

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي High  |DoD  |
|:---------|:---------|:---------|:---------|
|أرشفة Android | نعم | لا | لا |
|AT&T SMS/MMS Network Archiver | نعم | لا | لا |
|Bell SMS/MMS Network Archiver | نعم | لا | لا |
|"أرشفة أرقام المؤسسة" | نعم | لا | لا |
|O2 SMS وأرشفة الشبكة الصوتية | نعم         | لا | لا |
|أرشفة شبكة عمرو | نعم         | لا | لا |
|أرشفة الإشارة | نعم | لا | لا |
|"أرشفة الترقيات" | نعم | لا | لا |
|TELUS SMS Network Archiver | نعم | لا | لا |
|Verizon SMS/MMS Network Archiver | نعم | لا | لا |
|WeChat Archiver | نعم | لا | لا |
|WhatsApp Archiver | نعم | لا | لا |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>17a-4 موصلات بيانات في السحابة "الحكومة الأمريكية"

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي High  |DoD  |
|:---------|:---------|:---------|:---------|
|BlackBerry DataParser | نعم | لا | لا |
|Bloomberg DataParser  | نعم | لا | لا |
|Cisco Jabber DataParser  | نعم | لا | لا |
|Cisco Webex DataParser  | نعم | لا | لا |
|FactSet DataParser  | نعم | لا | لا |
|Fuze DataParser  | نعم | لا | لا |
|FX الاتصال DataParser  | نعم | لا | لا |
|ICE DataParser  | نعم | لا | لا |
|InvestEdge DataParser  | نعم | لا | لا |
|LivePerson Conversational Cloud DataParser  | نعم | لا | لا |
|Quip DataParser  | نعم | لا | لا |
|Refinitiv Eikon Messenger DataParser  | نعم | لا | لا |
|ServiceNow DataParser  | نعم | لا | لا |
|Skype for Business Server DataParser | نعم | لا | لا |
|Slack DataParser | نعم | لا | لا |
|SQL DataParser  | نعم | لا | لا |
|Symphony DataParser | نعم | لا | لا |
|Zoom DataParser | نعم | لا | لا |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>موصلات بيانات CellTrust في السحابة "الحكومة الأمريكية"

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي High  |DoD  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | نعم | لا | لا |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>العمل مع شريك Microsoft لأرشفة بيانات جهة خارجية

هناك خيار آخر لاستيراد بيانات جهة خارجية وأرشفتها وهو أن تعمل مؤسستك مع شريك Microsoft. إذا لم يكن نوع بيانات جهة خارجية مدعوما بواسطة موصلات البيانات المتوفرة في مركز التوافق من Microsoft، يمكنك العمل مع شريك يمكنه توفير موصل مخصص سيتم تكوينه لاستخراج العناصر من مصدر بيانات جهة خارجية بشكل منتظم ثم الاتصال بسحابة Microsoft بواسطة API من جهة خارجية واستيراد هذه العناصر إلى Microsoft 365. يحول موصل الشريك أيضا محتوى عنصر من مصدر بيانات جهة خارجية إلى رسالة بريد إلكتروني ثم يستورده إلى علبة بريد في Microsoft 365.

للحصول على قائمة بالشركاء التي يمكنك العمل عليها والعملية خطوة بخطوة لهذا الأسلوب، راجع العمل مع شريك لأرشفة بيانات جهة [خارجية](work-with-partner-to-archive-third-party-data.md) في Microsoft 365.
