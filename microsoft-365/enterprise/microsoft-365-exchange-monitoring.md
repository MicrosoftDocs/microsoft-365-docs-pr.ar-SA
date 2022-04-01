---
title: Exchange Online مراقبة Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: استخدم Exchange Online المعلومات للحصول على معلومات حول أحداث البريد الإلكتروني أو استشارات البريد الإلكتروني في Microsoft 365.
ms.openlocfilehash: 07d43a6f61ffe3e38f927d47e09d0a9685925f73
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520651"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online مراقبة Microsoft 365

Exchange Online مراقبة الأداء على السيناريوهات التالية على مستوى المؤسسة:

- **عملاء البريد** الإلكتروني: يمكنك عرض الحالة لعملاء البريد الإلكتروني التالي استنادا إلى نشاط قراءة البريد الإلكتروني:

  - Outlook سطح المكتب
  - Outlook على ويب
  - عملاء البريد الأصليين لنظامي التشغيل iOS وAndroid
  - Outlook تطبيق الأجهزة المحمولة في iOS وAndroid
  - Outlook Mac

   بالنسبة إلى هؤلاء العملاء، يمكنك رؤية عدد المستخدمين النشطين في آخر 30 دقيقة استنادا إلى قراءة المستخدمين لبريد إلكتروني، إلى جانب عدد الأحداث والاستشارات في لوحة المعلومات. تقارن هذه البيانات بنفس الفاصل الزمني في الأسبوع السابق لمعرفة ما إذا كانت هناك مشكلة.

   >[!Note]
   > يتم قياس عدد المستخدمين النشطين بنشاط واحد، على سبيل المثال، عندما يقرأ المستخدم رسالة بريد إلكتروني. فهو لا يمثل سوى آخر 30 دقيقة من النشاط.

- **اتصال التطبيق**: يستند الاتصال المقدر إلى النسبة المئوية للاتصالات الصناعية الناجحة بين أجهزة مؤسستك Exchange Online، وقد يتضمن مشاكل خارجة عن تحكم Microsoft. لمعرفة المزيد، راجع Microsoft 365 [البصريات للاتصال](microsoft-365-connectivity-optics.md).

- **المصادقة الأساسية والمصادقة الحديثة**: عدد المستخدمين الذين تم التحقق من صحتهم بنجاح Exchange Online الخدمة.

- **تدفق البريد**: عدد الرسائل التي تم تسليمها بنجاح إلى علبة بريد دون أي تأخير بعد أن وصلت الرسالة إلى Microsoft 365 البريد.

- **افتح Outlook ويب**: عدد المستخدمين الذين تم بنجاح Outlook على ويب.
  
فيما يلي مثال على السيناريوهات على مستوى المؤسسة Exchange Online لوحة المعلومات الرئيسية.

![سيناريوهات على مستوى المؤسسة Exchange Online المراقبة.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

بالنسبة إلى هذه السيناريوهات، تكون الأرقام الرئيسية للدقائق الثلاثين الأخيرة في لوحة المعلومات الرئيسية. تظهر طرق العرض المفصلة لكل من هذه السيناريوهات الاتجاه القريب في الوقت الحقيقي لسبعة أيام مع إجمالي 30 دقيقة مقارنة مع الأسبوع السابق.

![مثال على مراقبة Exchange تسليم البريد.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

ستلاحظ أحداثا أو استشارات تم إنشاؤها لمنظمتك باستخدام "مصدر المشكلة" في الاتصال الذي تم وضع علامة عليه على أنه "مؤسستك". هذه الإعلامات تستهدف مؤسستك بشكل فردي وتتضمن مشاكل تتطلب انتباهك لتخفيف حدتها وحلها. للحصول على مزيد من المعلومات حول أنواع مختلفة من المشاكل التي يتم إنشاؤها وإعلامها في حالة الخدمة لإعلام مؤسستك بشأن التأثير المحتمل، راجع المقالات التالية:

- [تنبيهات الخدمة لاستخدام علبة البريد](microsoft-365-mailbox-utilization-service-alerts.md)

- [تنبيهات الخدمة لتأخيرات مصدر MRS](microsoft-365-mrs-source-delays-service-alerts.md)

- [تنبيهات الخدمة للرسائل المعلقة للتسليم إلى المستلمين الخارجيين](microsoft-365-external-recipient-service-alerts.md)

## <a name="priority-accounts-monitoring-scenarios"></a>سيناريوهات مراقبة الحسابات ذات الأولوية

باستخدام Exchange Online الأولوية للحساب، يمكنك عرض حالة السيناريوهات التالية بعد تكوين [حسابات الأولوية](/microsoft-365/admin/setup/priority-accounts):

- Exchange الترخيص

- تخزين علبة البريد

- حد الرسالة

- المجلدات الفرعية لكل مجلد

- التسلسل الهيكلي لمجلدات

- العناصر القابلة لاستردادها

يتحقق Exchange الترخيص من عدم قدرة حساب الأولوية على تسجيل الدخول بسبب مشاكل الترخيص غير الصالحة، والتي يمكن معالجتها من قبل مسؤول المستأجر.

تحقق السيناريوهات الخمسة المتبقية أعلاه مما إذا كانت علبة بريد حساب الأولوية قريبة من الوصول إلى الحدود الموضحة في Exchange Online [الواردة](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

بالنسبة إلى هذه السيناريوهات، يمكنك رؤية استشارات وحادثات نشطة ومحلولة تؤثر على حساباتك ذات الأولوية. سيتم عرض معلومات تعريف حسابات الأولوية في تفاصيل الاستشارات أو الأحداث إلى جانب التوصيات. فيما يلي مثال من الصفحة في **صفحة** > Service health > Exchange Online.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="مثال على الإستشارات والحوادث النشطة والمحلولة التي تؤثر على حسابات الأولوية الخاصة بك":::

في جزء الحساب المتأثر، العمود **الحالة** به القيمتين التاليتين:

- تم إصلاح المشكلة التي تتسبب في حدوث الاستشارات أو الحادث لحساب الأولوية. لم تعد هناك مشكلة. 

- نشط: المشكلة التي تتسبب في حدوث الاستشارات أو الحادث مستمرة لحساب الأولوية. لا تزال المشكلة قائمة. 

- متأخر: لم يتم معالجة المشكلة التي تتسبب في حدوث الاستشارات أو الحادث لحساب الأولوية خلال 96 ساعة، لذا تم إيقافه مؤقتا. لا تزال المشكلة قائمة. 

فيما يلي مثال على ذلك.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="مثال عن عمود الحالة في جزء الحساب المتأثر":::

سيتم حل مشكلة أو استشارات بعد عدم وجود حسابات في **حالة نشط** .

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

### <a name="1-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>1. يبدو عدد المستخدمين النشطين في لوحة المعلومات لكل عميل منخفضا. لدينا عدد كبير من التراخيص النشطة المعينة للمستخدمين. ما معنى هذا؟

يستند عدد المستخدمين النشطين الموضح في المراقبة إلى نافذة 30 دقيقة حيث قام المستخدمون بتنفيذ النشاط الموضح في الميزة. يجب عدم الخلط بين هذا وبين أرقام الاستخدام. لعرض أرقام الاستخدام، استخدم تقارير النشاط في مركز مسؤولي Microsoft 365 (**ReportsUsage** > ).<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>

### <a name="2-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>2. أين يتم استخدام البيانات للسيناريوهات التي تظهر اتجاهات النشاط؟

يتم استخدام البيانات في Exchange Online الخدمة. إذا حدث فشل قبل أن يصل الطلب إلى Exchange Online أو حدث فشل في Exchange Online، سترى إسقاط في إشارة النشاط.
