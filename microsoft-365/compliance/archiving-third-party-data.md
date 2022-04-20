---
title: استخدام موصلات البيانات لاستيراد بيانات الجهات الخارجية وأرشفتها في Microsoft 365
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
description: تعرف على كيفية استيراد بيانات الجهات الخارجية وأرشفتها من منصات وسائل التواصل الاجتماعي ومنصات المراسلة الفورية وأنظمة التعاون الأساسية للمستندات إلى علب بريد Microsoft 365.
ms.openlocfilehash: 0588ab242f2d198c486b7ce0318939e204076421
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934940"
---
# <a name="learn-about-connectors-for-third-party-data"></a>التعرّف على الموصلات لبيانات الأطراف الخارجية

يتيح Microsoft 365 للمسؤولين استخدام موصلات البيانات لاستيراد البيانات غير الخاصة ب Microsoft وأرشفتها، وبيانات الجهات الخارجية من أنظمة الوسائط الاجتماعية وأنظمة المراسلة الفورية وأنظمة التعاون الأساسية للمستندات، إلى علب البريد في مؤسستك Microsoft 365. تتمثل إحدى الفوائد الأساسية لاستخدام موصلات البيانات لاستيراد بيانات الجهات الخارجية وأرشفتها في Microsoft 365 في أنه يمكنك تطبيق حلول Microsoft Purview المختلفة على البيانات بعد استيرادها. يساعدك ذلك على التأكد من أن بيانات مؤسستك غير التابعة ل Microsoft تتوافق مع اللوائح والمعايير التي تؤثر على مؤسستك.

شاهد هذا الدليل التفاعلي الذي يوضح كيفية إنشاء موصلات بيانات لاستيراد بيانات الجهات الخارجية وأرشفتها وأمثلة لتطبيق حلول التوافق على البيانات بعد استيرادها إلى Microsoft 365.

> [!VIDEO https://mslearn.cloudguides.com/guides/Archive%20data%20from%20non-Microsoft%20sources%20in%20Microsoft%20365]

## <a name="third-party-data-connectors"></a>موصلات بيانات الجهات الخارجية

يوفر مدخل توافق Microsoft Purview موصلات بيانات تابعة لجهة خارجية أصلية من Microsoft لاستيراد البيانات من مصادر بيانات مختلفة، مثل LinkedIn و Instant Bloomberg وTwitter وموصلات البيانات التي تدعم حل إدارة المخاطر ل Insider. بالإضافة إلى موصلات البيانات هذه، تعمل Microsoft مع الشركاء التاليين لتوفير العديد من موصلات البيانات من الجزء الثالث في مدخل التوافق. تعمل مؤسستك مع هؤلاء الشركاء لإعداد خدمة الأرشفة الخاصة بهم قبل إنشاء موصل بيانات مقابل في مدخل التوافق.

- [فيريتاس](#veritas-data-connectors)

- [TeleMessage](#telemessage-data-connectors)

- [17a-4 LLC](#17a-4-data-connectors)

- [CellTrust](#celltrust-data-connectors)

يتم استيراد بيانات الجهات الخارجية المدرجة في الأقسام التالية (باستثناء بيانات الموارد البشرية وبيانات التالفة الفعلية المستخدمة لحل إدارة المخاطر Microsoft 365 Insider) إلى علب بريد المستخدمين. يتم تطبيق حلول Microsoft Purview التي تدعم بيانات الجهات الخارجية على علبة بريد المستخدم حيث يتم تخزين البيانات.

### <a name="microsoft-data-connectors"></a>موصلات بيانات Microsoft

يسرد الجدول التالي موصلات بيانات الجهات الخارجية الأصلية المتوفرة في مدخل التوافق. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها بعد استيراد بيانات الجهات الخارجية وأرشفتها في Microsoft 365. راجع [نظرة عامة حول حلول التوافق التي تدعم قسم بيانات الجهات الخارجية](#overview-of-compliance-solutions-that-support-third-party-data) للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات الجهات الخارجية.

انقر فوق الارتباط في عمود **بيانات الجهات الخارجية** للانتقال إلى الإرشادات المفصلة خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

|بيانات الجهات الخارجية  |احتجاز التقاضي|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة المخاطر الداخلية  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[رسالة Bloomberg](archive-bloomberg-message-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)||
|[الرعاية الصحية EHR الملحمية](import-epic-data.md) ||||||![علامة اختيار](../media/checkmark.png)|
|[ف يسبوك](archive-facebook-data-with-sample-connector.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[الرعاية الصحية العامة في EHR](import-healthcare-data.md) ||||||![علامة اختيار](../media/checkmark.png)|
|[الموارد البشرية (HR)](import-hr-data.md) ||||||![علامة اختيار](../media/checkmark.png)|
|[دردشة ICE](archive-icechat-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Instant Bloomberg](archive-instant-bloomberg-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[LinkedIn](archive-linkedin-data.md)   |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[الريشة المادية](import-physical-badging-data.md) ||||||![علامة اختيار](../media/checkmark.png)|
|[Slack eDiscovery](archive-slack-data-microsoft.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Twitter](archive-twitter-data-with-sample-connector.md)     |![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
||||||||

### <a name="veritas-data-connectors"></a>موصلات بيانات Veritas

يسرد الجدول في هذا القسم موصلات البيانات التابعة لجهة خارجية المتوفرة بالشراكة مع Veritas. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات الجهات الخارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع [نظرة عامة حول حلول التوافق التي تدعم قسم بيانات الجهات الخارجية](#overview-of-compliance-solutions-that-support-third-party-data) للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات الجهات الخارجية.

قبل أن تتمكن من أرشفة بيانات الجهات الخارجية في Microsoft 365، يجب عليك العمل مع Veritas لإعداد خدمة الأرشفة (تسمى *Merge1*) لمؤسستك. لمزيد من المعلومات، انقر فوق الارتباط الموجود في عمود **بيانات الجهات الخارجية** للانتقال إلى الإرشادات المفصلة خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

|بيانات الجهات الخارجية  |احتجاز التقاضي|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة المخاطر الداخلية  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust](archive-celltrust-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Cisco Jabber على MS SQL](archive-ciscojabberonmssql-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Cisco Jabber على Oracle](archive-ciscojabberonoracle-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Cisco Jabber على PostgreSQL](archive-ciscojabberonpostgresql-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[EML](archive-eml-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[الاتصال بـ FX](archive-fxconnect-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Jive](archive-jive-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[بيانات MS SQL](archive-mssqldatabaseimporter-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[Pivot](archive-pivot-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Redtail Speak](archive-redtailspeak-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[التعامل مع Reuters](archive-reutersdealing-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Reuters Eikon](archive-reuterseikon-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Reuters FX](archive-reutersfx-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[RingCentral](archive-ringcentral-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Salesforce Chatter](archive-salesforcechatter-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[ServiceNow](archive-servicenow-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[Skype for Business](archive-skypeforbusiness-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Slack eDiscovery](archive-slack-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Symphony](archive-symphony-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[نص محدد](archive-text-delimited-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[Twitter](archive-veritas-twitter-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[Webex Teams](archive-webexteams-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[صفحات ويب](archive-webpagecapture-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[مساحة العمل من Facebook](archive-workplacefromfacebook-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[XIP](archive-xip-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[XSLT/XML](archive-xslt-xml-data.md)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[Yieldbroker](archive-yieldbroker-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[YouTube](archive-youtube-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|||
|[اجتماعات Zoom](archive-zoommeetings-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
||||||||

### <a name="telemessage-data-connectors"></a>موصلات بيانات TeleMessage

يسرد الجدول في هذا القسم موصلات البيانات التابعة لجهة خارجية المتوفرة بالشراكة مع TeleMessage. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات الجهات الخارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع [نظرة عامة حول حلول التوافق التي تدعم قسم بيانات الجهات الخارجية](#overview-of-compliance-solutions-that-support-third-party-data) للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات الجهات الخارجية.

قبل أن تتمكن من أرشفة بيانات الجهات الخارجية في Microsoft 365، يجب عليك العمل مع TeleMessage لإعداد خدمة الأرشفة لمؤسستك. لمزيد من المعلومات، انقر فوق الارتباط الموجود في عمود **بيانات الجهات الخارجية** للانتقال إلى الإرشادات المفصلة خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

تتوفر موصلات بيانات TeleMessage أيضا في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. لمزيد من المعلومات، راجع [موصلات البيانات في القسم السحابي لحكومة الولايات المتحدة](#data-connectors-in-the-us-government-cloud) في هذه المقالة.

|بيانات الجهات الخارجية  |احتجاز التقاضي|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة المخاطر الداخلية  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[الروبوت](archive-android-archiver-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[AT&T Network](archive-att-network-archiver-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[شبكة الجرس](archive-bell-network-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[رقم المؤسسة](archive-enterprise-number-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[شبكة O2](archive-o2-network-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[شبكة مهى](archive-rogers-network-archiver-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[اشاره](archive-signal-archiver-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[برقيه](archive-telegram-archiver-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[شبكة TELUS](archive-telus-network-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Verizon Network](archive-verizon-network-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[WeChat](archive-wechat-data.md)|![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Whatsapp](archive-whatsapp-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
||||||||

### <a name="17a-4-data-connectors"></a>موصلات بيانات 17a-4

يسرد الجدول في هذا القسم موصلات البيانات التابعة لجهة خارجية المتوفرة بالشراكة مع 17a-4 LLC. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات الجهات الخارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع [نظرة عامة حول حلول التوافق التي تدعم قسم بيانات الجهات الخارجية](#overview-of-compliance-solutions-that-support-third-party-data) للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات الجهات الخارجية.

قبل أن تتمكن من أرشفة بيانات الجهات الخارجية في Microsoft 365، يجب عليك العمل مع 17a-4 LLC لإعداد خدمة الأرشفة الخاصة بهم (تسمى *DataParser*) لمؤسستك. لمزيد من المعلومات، انقر فوق الارتباط الموجود في عمود **بيانات الجهات الخارجية** للانتقال إلى الإرشادات المفصلة خطوة بخطوة لإنشاء موصل لنوع البيانات هذا.

تتوفر أيضا موصلات بيانات 17a-4 في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. لمزيد من المعلومات، راجع [موصلات البيانات في القسم السحابي لحكومة الولايات المتحدة](#data-connectors-in-the-us-government-cloud) في هذه المقالة.

|بيانات الجهات الخارجية  |احتجاز التقاضي|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة المخاطر الداخلية  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[بلاك بيري](archive-17a-4-blackberry-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[بلومبرغ](archive-17a-4-bloomberg-data.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Cisco Jabber](archive-17a-4-cisco-jabber-data.md)   |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Cisco Webex](archive-17a-4-webex-teams-data.md)   |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[مجموعة الحقائق](archive-17a-4-factset-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[الصمامات](archive-17a-4-fuze-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[الاتصال بـ FX](archive-17a-4-fxconnect-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[دردشة ICE](archive-17a-4-ice-im-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[InvestEdge](archive-17a-4-investedge-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[LivePerson Conversational Cloud](archive-17a-4-liveperson-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[الساخر](archive-17a-4-quip-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Refinitiv Eikon Messenger](archive-17a-4-refinitiv-messenger-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[ServiceNow](archive-17a-4-servicenow-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
[Skype for Business Server](archive-17a-4-skype-for-business-server-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[الركود](archive-17a-4-slack-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[SQL](archive-17a-4-sql-database-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[Symphony](archive-17a-4-symphony-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
|[التكبير](archive-17a-4-zoom-data.md)    |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
||||||||

### <a name="celltrust-data-connectors"></a>موصلات بيانات CellTrust

يسرد الجدول في هذا القسم موصل البيانات التابع لجهة خارجية المتوفر بالشراكة مع CellTrust. يلخص الجدول أيضا حلول التوافق التي يمكنك تطبيقها على بيانات الجهات الخارجية بعد استيرادها وأرشفتها في Microsoft 365. راجع [نظرة عامة حول حلول التوافق التي تدعم قسم بيانات الجهات الخارجية](#overview-of-compliance-solutions-that-support-third-party-data) للحصول على وصف أكثر تفصيلا لكل حل توافق وكيفية دعمه لبيانات الجهات الخارجية.

قبل أن تتمكن من أرشفة بيانات الجهات الخارجية في Microsoft 365، يجب عليك العمل مع CellTrust لإعداد خدمة الأرشفة الخاصة بها (تسمى *CellTrust SL2*) لمؤسستك. لمزيد من المعلومات، انقر فوق الارتباط في عمود **بيانات الجهات الخارجية** للانتقال إلى الإرشادات المفصلة خطوة بخطوة لإنشاء موصل CellTrust SL2.

|بيانات الجهات الخارجية  |احتجاز التقاضي|eDiscovery  |إعدادات الاستبقاء  |إدارة السجلات  |توافق الاتصالات  |إدارة المخاطر الداخلية  |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|[CellTrust SL2](archive-data-from-celltrustsl2.md)     |![علامة الاختيار.](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)|![علامة اختيار](../media/checkmark.png)||
||||||||

يتوفر موصل بيانات CellTrust SL2 أيضا في بيئات سحابة القطاع الحكومي في Microsoft 365 سحابة حكومة الولايات المتحدة. لمزيد من المعلومات، راجع [موصلات البيانات في القسم السحابي لحكومة الولايات المتحدة](#data-connectors-in-the-us-government-cloud) في هذه المقالة.

## <a name="overview-of-compliance-solutions-that-support-third-party-data"></a>نظرة عامة على حلول التوافق التي تدعم بيانات الجهات الخارجية

تصف الأقسام التالية بعض الأشياء التي يمكن أن تساعدك حلول Microsoft Purview على إدارة بيانات الجهات الخارجية المدرجة في الجدول السابق.

### <a name="litigation-hold"></a>احتجاز التقاضي

يمكنك وضع [احتجاز التقاضي](create-a-litigation-hold.md) على علبة بريد المستخدم للاحتفاظ ببيانات الجهات الخارجية. عند إنشاء قائمة احتجاز، يمكنك تحديد مدة احتجاز (تسمى أيضا *احتجاز يستند إلى الوقت*) بحيث يتم الاحتفاظ ببيانات الجهات الخارجية المحذوفة والمعدلة لفترة محددة ثم حذفها نهائيا من علبة البريد. أو يمكنك فقط الاحتفاظ بالمحتوى إلى أجل غير مسمى (يسمى *احتجاز لا نهائي*) أو حتى تتم إزالة احتجاز التقاضي.

### <a name="ediscovery"></a>eDiscovery

أدوات eDiscovery الأساسية الثلاث في Microsoft 365 هي البحث عن المحتوى وMicrosoft Purview eDiscovery (قياسي) وMicrosoft Purview eDiscovery (Premium).

- **[البحث عن المحتوى](content-search.md).** يمكنك استخدام أداة البحث في المحتوى للبحث في علب البريد عن بيانات الجهات الخارجية التي قمت باستيرادها. يمكنك استخدام استعلامات البحث وشروطه لتضييق نطاق نتائج البحث وتصدير نتائج البحث.

- **[eDiscovery (قياسي).](get-started-core-ediscovery.md)** تعتمد هذه الأداة على وظيفة البحث والتصدير الأساسية من خلال تمكينك من إنشاء حالات تتيح لك التحكم في الأشخاص الذين يمكنهم الوصول إلى بيانات الحالة، ووضع قائمة احتجاز على علب بريد المستخدمين أو محتوى علبة البريد الذي يطابق معايير البحث. وهذا يعني أنه يمكنك وضع قائمة احتجاز eDiscovery على بيانات الجهات الخارجية التي تم استيرادها إلى علب بريد المستخدمين.

- **[eDiscovery (Premium)](overview-ediscovery-20.md).** تعمل هذه الأداة القوية على توسيع وظيفة حالة eDiscovery (Standard) من خلال السماح لك بإضافة أمناء لحالة ما، ووضع بيانات الوصي قيد الاحتجاز، ثم تحميل بيانات جهة خارجية للوصي في مراجعة لمزيد من التحليل مثل الموضوعات والكشف المكرر. بعد تحميل بيانات الجهات الخارجية في مجموعة مراجعة، يمكنك الاستعلام عنها وتصفيتها إلى مجموعة نتائج ضيقة.

   يتيح لك كل من eDiscovery (Standard) وeDiscovery (Premium) إدارة بيانات الجهات الخارجية التي قد تكون ذات صلة بالتحقيقات القانونية أو الداخلية لمؤسستك.

### <a name="retention-settings"></a>إعدادات الاستبقاء

يمكنك تطبيق [نهج استبقاء](retention.md) على علب بريد المستخدمين للاحتفاظ ببيانات الجهات الخارجية (ومحتوى علبة البريد الأخرى) ثم حذفها بعد انتهاء فترة الاستبقاء. يمكنك أيضا استخدام نهج الاستبقاء لحذف بيانات الجهات الخارجية من عمر معين أو [استخدام تسميات الاستبقاء لتشغيل مراجعة الترتيب](disposition.md) عند انتهاء فترة الاستبقاء لبيانات الجهات الخارجية.

### <a name="records-management"></a>إدارة السجلات

تتيح لك ميزة [إدارة السجلات](records-management.md) في Microsoft 365 الإعلان عن بيانات الجهات الخارجية كسجل. يمكن إجراء ذلك يدويا من قبل المستخدمين الذين يطبقون تسمية استبقاء تميز بيانات الجهات الخارجية في علبة بريدهم كسجل. أو يمكنك تطبيق تسميات الاستبقاء تلقائيا عن طريق تحديد المعلومات الحساسة أو الكلمات الأساسية أو أنواع المحتويات في بيانات الجهات الخارجية.

### <a name="communication-compliance"></a>توافق الاتصالات

يمكنك استخدام [توافق الاتصالات](communication-compliance.md) لفحص بيانات الجهات الخارجية للتأكد من أنها متوافقة مع معايير بيانات مؤسستك. يمكنك القيام بذلك من خلال الكشف عن إجراءات المعالجة والتقاطها واتخاذها للرسائل غير المناسبة في مؤسستك. على سبيل المثال، يمكنك مراقبة بيانات الجهات الخارجية التي تقوم باستيرادها للغة المسيئة والمعلومات الحساسة والتوافق التنظيمي.

### <a name="insider-risk-management"></a>إدارة المخاطر الداخلية

يمكن استخدام الإشارات من بيانات الجهات الخارجية، مثل بيانات الموارد البشرية الانتقائية، بواسطة حل [إدارة المخاطر في Insider](insider-risk-management.md) لتقليل المخاطر الداخلية من خلال السماح لك بالكشف عن الأنشطة المحفوفة بالمخاطر في مؤسستك والتحقيق فيها والعمل عليها. على سبيل المثال، يتم استخدام البيانات المستوردة من قبل موصل بيانات الموارد البشرية كمؤشرات مخاطر للمساعدة في الكشف عن سرقة بيانات الموظفين المغادرين.

## <a name="using-ediscovery-tools-to-search-for-third-party-data"></a>استخدام أدوات eDiscovery للبحث عن بيانات الجهات الخارجية

بعد استخدام موصلات البيانات لاستيراد بيانات الجهات الخارجية وأرشفتها في علب بريد المستخدمين، يمكنك استخدام أدوات eDiscovery Microsoft 365 للبحث عن بيانات الجهات الخارجية. يمكنك أيضا أدوات eDiscovery لإنشاء قوائم احتجاز مستندة إلى استعلام مقترنة بحالات eDiscovery (قياسي) وeDiscovery (Premium) للحفاظ على بيانات الجهات الخارجية. لمزيد من المعلومات حول أدوات eDiscovery، راجع [حلول eDiscovery في Microsoft 365](ediscovery.md).

للبحث عن (أو وضع قيد الاحتجاز) أي نوع من بيانات الجهات الخارجية التي قمت باستيرادها إلى علب بريد المستخدمين باستخدام موصل بيانات، يمكنك استخدام استعلام البحث التالي. تأكد من تحديد نطاق البحث إلى علب بريد المستخدمين.

```powershell
kind:externaldata
```

يمكنك استخدام هذا الاستعلام في مربع **الكلمات الأساسية** للبحث في المحتوى أو البحث المقترن بحالة eDiscovery (قياسي) أو مجموعة في eDiscovery (Premium).

![استعلام للبحث عن بيانات الجهات الخارجية.](..\media\SearchThirdPartyData1.png)

يمكنك أيضا استخدام زوج الخاصية `kind:externaldata` :value لتضييق نطاق عمليات البحث إلى بيانات الجهات الخارجية. على سبيل المثال، للبحث عن العناصر المستوردة من أي مصدر بيانات تابع لجهة خارجية يحتوي على كلمة *contoso* في خاصية **الموضوع** للعنصر المستورد، استخدم الاستعلام التالي في مربع **الكلمات الأساسية** :

```powershell
subject:contoso AND kind:externaldata
```

بدلا من ذلك، يمكنك استخدام شرط **نوع الرسالة** لتكوين نفس الاستعلام.

![استخدم شرط نوع الرسالة لتضييق نطاق عمليات البحث إلى بيانات الجهات الخارجية.](..\media\SearchThirdPartyData2.png)

للبحث عن نوع معين من بيانات الجهات الخارجية المؤرشفة، استخدم خاصية علبة بريد **فئة العنصر** في استعلام بحث. استخدم الخاصية التالية:تنسيق القيمة:

```powershell
itemclass:ipm.externaldata.<third-party data type>
```

يتضمن كل عنصر تم استيراده بواسطة موصل بيانات تابع لجهة خارجية خاصية **فئة العنصر** بقيمة تتوافق مع نوع بيانات الجهات الخارجية. على سبيل المثال، للبحث عن بيانات Facebook التي تحتوي على كلمة *contoso*، في الخاصية **"الموضوع** " للعنصر المستورد، استخدم الاستعلام التالي:

```powershell
subject:contoso AND itemclass:ipm.externaldata.facebook*
```

فيما يلي بعض الأمثلة لقيم **فئة العناصر** لأنواع مختلفة من بيانات الجهات الخارجية.

| **نوع بيانات جهة خارجية** | **قيمة خاصية itemclass**   |
|---------------------------|-------------------------------------|
| رسالة Bloomberg         | ipm.externaldata.bloombergmessage* |
| CellTrust                 | ipm.externaldata.celltrust*        |
| Pivot                     | ipm.externaldata.pivot*            |
| أرشيف WhatsApp         | ipm.externaldata.whatsapparchiver* |
|||

قيم الخاصية *itemclass* ليست حساسة لحالة الأحرف. بشكل عام، استخدم اسم نوع البيانات التابع لجهة خارجية (بدون مسافات) متبوعا بحرف بدل ( * ).

لمزيد من المعلومات حول إنشاء استعلامات بحث eDiscovery، راجع [استعلامات الكلمات الأساسية وشروط البحث ل eDiscovery](keyword-queries-and-search-conditions.md).

## <a name="data-connectors-in-the-us-government-cloud"></a>موصلات البيانات في سحابة حكومة الولايات المتحدة

تتوفر بعض موصلات البيانات في سحابة حكومة الولايات المتحدة. تشير الأقسام التالية إلى البيئات الحكومية المحددة التي تدعم موصلات بيانات الجهات الخارجية. لمزيد من المعلومات حول سحب حكومة الولايات المتحدة، راجع [Microsoft 365 حكومة الولايات المتحدة](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/microsoft-365-government-how-to-buy).

### <a name="veritas-data-connectors-in-the-us-government-cloud-preview"></a>موصلات بيانات Veritas في سحابة حكومة الولايات المتحدة (معاينة)

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي عالية  |وزاره الدفاع  |
|:---------|:---------|:---------|:---------|
|CellTrust| نعم | لا | لا |
|Cisco Jabber على MS SQL| نعم | لا | لا |
|Cisco Jabber على Oracle| نعم | لا | لا |
|Cisco Jabber على PostgreSQL| نعم | لا | لا |
|EML| نعم | لا | لا |
|الاتصال بـ FX| نعم | لا | لا |
|Jive| نعم | لا | لا |
|بيانات MS SQL| نعم | لا | لا |
|Pivot| نعم | لا | لا |
|Redtail Speak| نعم | لا | لا |
|التعامل مع Reuters| نعم | لا | لا |
|Reuters Eikon| نعم | لا | لا |
|Reuters FX| نعم | لا | لا |
|RingCentral| نعم | لا | لا |
|Salesforce Chatter| نعم | لا | لا |
|ServiceNow| نعم | لا | لا |
|Skype for Business| نعم | لا | لا |
|Slack eDiscovery| نعم | لا | لا |
|Symphony| نعم | لا | لا |
|نص محدد| نعم | لا | لا |
|Twitter| نعم | لا | لا |
|Webex Teams| نعم | لا | لا |
|صفحات ويب| نعم | لا | لا |
|مساحة العمل من Facebook| نعم | لا | لا |
|XIP| نعم | لا | لا |
|XSLT/XML| نعم | لا | لا |
|Yieldbroker| نعم | لا | لا |
|YouTube| لا | لا | لا |
|اجتماعات Zoom| نعم | لا | لا |
|||||

### <a name="telemessage-data-connectors-in-the-us-government-cloud"></a>موصلات بيانات TeleMessage في سحابة حكومة الولايات المتحدة

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي عالية  |وزاره الدفاع  |
|:---------|:---------|:---------|:---------|
|أرشفة Android | نعم | لا | لا |
|أرشيفي شبكة AT&T SMS/MMS | نعم | لا | لا |
|أرشيف شبكة جرس SMS/MMS | نعم | لا | لا |
|أرشفة رقم المؤسسة | نعم | لا | لا |
|O2 SMS وأرشيف الشبكة الصوتية | نعم         | لا | لا |
|أرشفة شبكة Rogers | نعم         | لا | لا |
|أرشفة الإشارة | نعم | لا | لا |
|أرشفة Telegram | نعم | لا | لا |
|TELUS SMS Network Archiver | نعم | لا | لا |
|أرشيفي الشبكة Verizon SMS/MMS | نعم | لا | لا |
|أرشيف WeChat | نعم | لا | لا |
|أرشيف WhatsApp | نعم | لا | لا |
|||||

### <a name="17a-4-data-connectors-in-the-us-government-cloud"></a>17a-4 موصلات بيانات في سحابة حكومة الولايات المتحدة

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي عالية  |وزاره الدفاع  |
|:---------|:---------|:---------|:---------|
|محلل البيانات BlackBerry | نعم | لا | لا |
|محلل البيانات Bloomberg  | نعم | لا | لا |
|محلل البيانات Cisco Jabber  | نعم | لا | لا |
|محلل البيانات Cisco Webex  | نعم | لا | لا |
|محلل البيانات FactSet  | نعم | لا | لا |
|محلل البيانات Fuze  | نعم | لا | لا |
|محلل بيانات الاتصال بـ FX  | نعم | لا | لا |
|محلل البيانات ICE  | نعم | لا | لا |
|محلل البيانات InvestEdge  | نعم | لا | لا |
|محلل بيانات سحابة محادثة LivePerson  | نعم | لا | لا |
|محلل بيانات Quip  | نعم | لا | لا |
|محلل بيانات Refinitiv Eikon Messenger  | نعم | لا | لا |
|محلل بيانات ServiceNow  | نعم | لا | لا |
|محلل بيانات Skype for Business Server | نعم | لا | لا |
|محلل بيانات Slack | نعم | لا | لا |
|محلل بيانات SQL  | نعم | لا | لا |
|محلل بيانات Symphony | نعم | لا | لا |
|محلل بيانات Zoom | نعم | لا | لا |
|||||

### <a name="celltrust-data-connectors-in-the-us-government-cloud"></a>موصلات بيانات CellTrust في سحابة حكومة الولايات المتحدة

|موصل البيانات  |سحابة القطاع الحكومي  |سحابة القطاع الحكومي عالية  |وزاره الدفاع  |
|:---------|:---------|:---------|:---------|
|CellTrust SL2 | نعم | لا | لا |
|||||

## <a name="working-with-a-microsoft-partner-to-archive-third-party-data"></a>العمل مع شريك Microsoft لإرشفة بيانات الجهات الخارجية

خيار آخر لاستيراد بيانات الجهات الخارجية وأرشفتها هو أن تعمل مؤسستك مع شريك Microsoft. إذا لم تكن موصلات البيانات المتوفرة في مركز توافق Microsoft تدعم نوع بيانات جهة خارجية، فيمكنك العمل مع شريك يمكنه توفير موصل مخصص سيتم تكوينه لاستخراج العناصر من مصدر بيانات الجهات الخارجية بشكل منتظم ثم الاتصال بسحابة Microsoft بواسطة واجهة برمجة تطبيقات تابعة لجهة خارجية واستيراد هذه العناصر إلى Microsoft 365. يقوم موصل الشريك أيضا بتحويل محتوى عنصر من مصدر بيانات جهة خارجية إلى رسالة بريد إلكتروني ثم استيراده إلى علبة بريد في Microsoft 365.

للحصول على قائمة بالشركاء الذين يمكنك العمل معهم والعملية المفصلة خطوة بخطوة لهذا الأسلوب، راجع ["العمل مع شريك" لأرشفة بيانات الجهات الخارجية في Microsoft 365](work-with-partner-to-archive-third-party-data.md).
