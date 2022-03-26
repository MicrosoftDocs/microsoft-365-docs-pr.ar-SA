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
ms.openlocfilehash: 22985d1fd6e79693a526c8ec008e189593543ae6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569471"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online مراقبة Microsoft 365

يمكنك استخدام Exchange Online في مركز مسؤولي Microsoft 365 لمراقبة حالة الخدمة Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> الاشتراك الخاص Microsoft 365 مؤسستك. Exchange Online هذه المراقبة معلومات حول الأحداث والاستشارات التي يتم تجميعها في هذه الفئات:

- **البنية** الأساسية: يتم اكتشاف المشكلة في Microsoft 365 الأساسية التي تملكها Microsoft لتوفير تحديثات منتظمة وحل المشكلة. على سبيل المثال، لا يمكن للمستخدمين الوصول إلى Exchange Online بسبب مشاكل تتعلق Exchange أو أي بنية Microsoft 365 سحابية أخرى.
- **البنية الأساسية التابعة لأي** جهة خارجية: يتم اكتشاف المشكلة في البنية الأساسية التابعة لأي جهة خارجية التي اتخذت مؤسستك تبعية لها وتتطلب اتخاذ إجراء من مؤسستك لحلها. على سبيل المثال، يتم كبح معاملات مصادقة المستخدمين بواسطة موفر خدمة رمز أمان مميز (STS) جهة خارجية يمنع المستخدمين من الاتصال Exchange Online.
- **البنية الأساسية للعملاء**: يتم اكتشاف المشكلة في البنية الأساسية لم المؤسسة ويتطلب اتخاذ إجراء من مؤسستك لحلها. على سبيل المثال، يتعذر على المستخدمين الوصول Exchange Online لأنه يتعذر عليهم الحصول على رمز مصادقة مميز من موفر STS المستضاف بواسطة مؤسستك بسبب شهادة منتهية الصلاحية.

فيما يلي مثال على صفحة حالة  الخدمة في مركز مسؤولي Microsoft 365، المتوفرة من "حالة > حالة الخدمة"  لسيناريوهات حساب الأولوية [والتنظيم](../admin/setup/priority-accounts.md).

![صفحة حالة الخدمة في مركز مسؤولي Microsoft 365.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**سيتم تحديد المشاكل** في مؤسستك وسيستخدمها مراقبة على مستوى المؤسسة ومراقبة حساب الأولوية.

تشير قيمة عمود "حالة" ضمن  المشاكل في مؤسستك إلى ما إذا كانت البنية الأساسية لم مؤسستك أو برامج الأطراف الخارجية تؤثر على تجربة حالة الخدمة لمستخدمي مؤسستك و/أو حسابات الأولوية في Exchange Online. تتطلب استشارات أو أحداث *إجراءاتك* لحلها.

تشير قيمة عمود **"الصحة** " ضمن "صحة خدمة **Microsoft** " إلى أن الخدمة سليمة أو أن لها استشارات أو أحداث استنادا إلى الخدمات السحابية التي تحافظ عليها Microsoft.

فيما يلي مثال لصفحة مراقبة Exchange Online في مركز مسؤولي Microsoft 365 التي تعرض حالة سيناريوهات حساب على مستوى المؤسسة والأولوية المتوفرة من > حالة الخدمة **> Exchange Online**.

![صفحة Exchange Online في مركز مسؤولي Microsoft 365.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example.png)

باستخدام **صفحة Exchange Online**، يمكنك معرفة ما إذا كانت Exchange Online سليمة أم لا وما إذا كانت هناك أي أحداث أو استشارات مرتبطة. باستخدام Exchange Online، يمكنك الاطلاع على حالة الخدمة لسيناريوهات بريد إلكتروني معينة وعرض إشارات في الوقت الحقيقي تقريبا لتحديد تأثير السيناريو على مستوى المؤسسة. يمكنك أيضا الاطلاع على حالة سيناريوهات حساب الأولوية.

## <a name="requirements"></a>المتطلبات

يتم تمكين هذه المعاينة للعملاء الذين يلبيون هذه المتطلبات:

- تحتاج مؤسستك إلى الحصول على عدد تراخيص لا يقل عن 5000 ترخيص من واحد أو مجموعة من هذه المنتجات: Office 365 E3 أو Microsoft 365 E3 أو Office 365 E5 أو Microsoft 365 E5.

  على سبيل المثال، يمكن أن تملك مؤسستك 3000 ترخيص Office 365 E3 و2500 Microsoft 365 E5، لإجمالي 5500 ترخيص من المنتجات المؤهلة.

- تحتاج مؤسستك إلى أن يكون لديها 50 مستخدما نشطا شهريا على الأقل لخدمات Microsoft 365 أساسية واحدة أو أكثر، بما في ذلك Microsoft Teams و OneDrive for Business و SharePoint عبر الإنترنت و Exchange Online و Office التطبيقات.

- يمكن لأي دور مع أذونات "لوحة معلومات صحة الخدمة" الوصول إلى Exchange Online المراقبة. للحصول على مزيد من المعلومات، اطلع على [كيفية التحقق من حالة خدمة Microsoft 365](view-service-health.md).

## <a name="organization-level-scenarios"></a>سيناريوهات على مستوى المؤسسة

مع Exchange Online تدعم مراقبة السيناريوهات التالية:

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

  ![مثال على مراقبة Exchange تسليم البريد.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

بالنسبة إلى هذه السيناريوهات، تكون الأرقام الرئيسية للدقائق الثلاثين الأخيرة في لوحة المعلومات الرئيسية. تظهر طرق العرض المفصلة لكل من هذه السيناريوهات الاتجاه القريب في الوقت الحقيقي لسبعة أيام مع إجمالي 30 دقيقة مقارنة مع الأسبوع السابق.

## <a name="priority-accounts-monitoring-scenarios"></a>سيناريوهات مراقبة الحسابات ذات الأولوية

باستخدام Exchange Online الأولوية للحساب، يمكنك عرض حالة السيناريوهات التالية بعد تكوين [حسابات الأولوية](/microsoft-365/admin/setup/priority-accounts):

- Exchange الترخيص

- تخزين علبة البريد

- حد الرسالة

- المجلدات الفرعية لكل مجلد

- التسلسل الهيكلي لمجلدات

- العناصر القابلة لاستردادها

يتحقق Exchange الترخيص من عدم تمكن حساب الأولوية من تسجيل الدخول بسبب مشاكل الترخيص غير الصالحة، والتي يمكن معالجتها من قبل مسؤول المستأجر.

تحقق السيناريوهات الخمسة المتبقية أعلاه مما إذا كانت علبة بريد حساب الأولوية قريبة من الوصول إلى الحدود الموضحة في Exchange Online [الواردة](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

بالنسبة إلى هذه السيناريوهات، يمكنك رؤية استشارات وحادثات نشطة ومحلولة تؤثر على حساباتك ذات الأولوية. سيتم عرض معلومات تعريف حسابات الأولوية في تفاصيل الاستشارات أو الأحداث إلى جانب التوصيات. فيما يلي مثال من الصفحة في "حالة > **حالة الخدمة" > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="مثال على الإستشارات والحوادث النشطة والمحلولة التي تؤثر على حسابات الأولوية الخاصة بك":::

في جزء الحساب المتأثر، العمود **الحالة** به القيمتين التاليتين:

- تم إصلاح المشكلة التي تتسبب في حدوث الاستشارات أو الحادث لحساب الأولوية. لم تعد هناك مشكلة. 

- نشط: المشكلة التي تتسبب في حدوث الاستشارات أو الحادث مستمرة لحساب الأولوية. لا تزال المشكلة قائمة. 

- متأخر: لم يتم معالجة المشكلة التي تتسبب في حدوث الاستشارات أو الحادث لحساب الأولوية خلال 96 ساعة، لذا يتم تعليقها. لا تزال المشكلة قائمة. 

فيما يلي مثال على ذلك.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="مثال عن عمود الحالة في جزء الحساب المتأثر":::

سيتم حل مشكلة أو استشارات بعد عدم وجود حسابات في **حالة نشط** . 

## <a name="send-us-feedback"></a>إرسال ملاحظاتك إلينا

هناك طريقتان لتقديم الملاحظات:

- استخدم الخيار **تقديم ملاحظات** متوفرا على كل صفحة من صفحات مركز مسؤولي Microsoft 365.

- إرسال ملاحظات باستخدام **الارتباط هل هذا المنشور مفيد؟** لحادث أو استشارات معينة.

  !["هل هذا المنشور مفيد؟" ارتباط لحادث أو استشارات معينة.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

#### <a name="1-why-dont-i-see-exchange-online-monitoring-under-health-in-the-microsoft-365-admin-center"></a>1. لماذا لا أرى "مراقبة Exchange Online" ضمن حالة في مركز مسؤولي Microsoft 365؟ 

أولا، تأكد من تمكين مركز الإدارة الجديد على الصفحة **الرئيسية** <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365.</a>

بعد ذلك، تأكد من تلبية كل من المتطلبات التالية:

- تحتاج مؤسستك إلى الحصول على عدد تراخيص لا يقل عن 5000 ترخيص، من واحد أو مجموعة من هذه المنتجات: Office 365 E3، Microsoft 365 E3، Office 365 E5، Microsoft 365 E5.

- تحتاج مؤسستك إلى أن يكون لديها 50 مستخدما نشطا شهريا على الأقل لخدمات Microsoft 365 أساسية واحدة أو أكثر، بما في ذلك Microsoft Teams و OneDrive for Business و SharePoint عبر الإنترنت و Exchange Online و Office التطبيقات.

إذا كان عدد التراخيص لمنظمتك أقل من 5000 مستخدم وكان عدد المستخدمين النشطين الشهريين أقل من 50 مستخدما في الخدمات الأساسية، فلن يتم تمكين مراقبة Exchange Online إلا بعد تلبية هذه المتطلبات.

#### <a name="2-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>2. يبدو عدد المستخدمين النشطين في لوحة المعلومات لكل عميل منخفضا. لدينا عدد كبير من التراخيص النشطة المعينة للمستخدمين. ما معنى هذا؟

يستند عدد المستخدمين النشطين الموضح في المراقبة إلى نافذة 30 دقيقة حيث قام المستخدمون بتنفيذ النشاط الموضح في الميزة. يجب عدم الخلط بين هذا وبين أرقام الاستخدام. لعرض أرقام الاستخدام، استخدم تقارير النشاط في مركز مسؤولي Microsoft 365 (**ReportsUsage** > ).<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a>

#### <a name="3-will-there-be-other-monitoring-scenarios-for-other-services-such-as-teams-and-sharepoint"></a>3. هل سيكون هناك سيناريوهات مراقبة أخرى لخدمات أخرى مثل Teams SharePoint؟

تقوم Microsoft بدمج هذه التجربة مباشرة داخل لوحة معلومات حالة الخدمة في مركز مسؤولي Microsoft 365. سيوفر ذلك فرصا ل Microsoft لتوسيع سيناريوهات المراقبة للخدمات الأخرى، والتي سيتم الإعلان عنها عند وجود أخبار لمشاركتها.

#### <a name="4-what-is-the-plan-for-general-availability-of-this-experience"></a>4. ما هي خطة التوفر العام لهذه التجربة؟

قامت Microsoft Exchange Online المراقبة المباشرة <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank"> على لوحة معلومات</a> حالة الخدمة في مركز مسؤولي Microsoft 365.

مع هذه التجربة المتكاملة الجديدة، فإن خطة Microsoft هي جمع ملاحظاتك ثم تحديد خطتنا للتوفر العام.

#### <a name="5-is-this-a-free-included-or-paid-extra-feature"></a>5. هل هذه ميزة مجانية (مضمنة) أو مدفوعة (إضافية)؟ 

هذه ميزة مجانية في المعاينة ومتوفرة فقط للعملاء الذين يلبيون المتطلبات المذكورة في السؤال 1. لا يوجد خيار مدفوع لتلقي هذا المحتوى.

#### <a name="6-how-do-i-provide-feedback"></a>6. كيف يمكنني تقديم الملاحظات؟

للحصول على ملاحظات عامة، استخدم الأيقونة **تقديم** ملاحظات في الزاوية السفلية اليسرى **من صفحة** Exchange Online الملاحظات. 

للحصول على ملاحظات حول الأحداث أو النصائح، استخدم الارتباط **هل هذا المنشور مفيد؟**

#### <a name="7-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>7. أين يتم استخدام البيانات للسيناريوهات التي تظهر اتجاهات النشاط؟

يتم استخدام البيانات في Exchange Online الخدمة. إذا حدث فشل قبل وصول الطلب إلى Exchange Online أو حدث فشل في Exchange Online، سترى إسقاط في إشارة النشاط.

#### <a name="8-are-there-any-privacy-concerns"></a>8. هل هناك أي مشاكل تتعلق بالخصوصية؟

تركز عملية المراقبة على بيانات تعريف الخدمة ولا يتم مراقبة محتوى المستخدم.

## <a name="see-also"></a>راجع أيضًا

- [كيفية التحقق من Microsoft 365 الخدمة](view-service-health.md) 

- [Exchange Online الحدود](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits)

- [إدارة حسابات الأولوية ومراقبتها](/microsoft-365/admin/setup/priority-accounts)

- [استخدام "حسابات الأولوية" في Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)

- [تنبيهات الخدمة لاستخدام علبة البريد في مراقبة Exchange Online البريد](microsoft-365-mailbox-utilization-service-alerts.md)

- [تنبيهات الخدمة لتأخيرات مصدر MRS في مراقبة Exchange Online](microsoft-365-mrs-source-delays-service-alerts.md)
