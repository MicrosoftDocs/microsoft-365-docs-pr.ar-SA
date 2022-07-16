---
title: التغيير من خطة Microsoft 365 E إلى خطة Microsoft 365 F
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على الأمور التي يجب أخذها في الاعتبار وكيفية التحضير إذا كنت تقوم بتبديل بعض المستخدمين من خطة Microsoft 365 E إلى خطة Microsoft 365 F.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_FLW
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 90e29a5ec2ddf70afb299398113be034580eda85
ms.sourcegitcommit: 1efb75d033860977239b479f92e7eaf274b5fbf0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2022
ms.locfileid: "66827149"
---
# <a name="changing-from-a-microsoft-365-e-plan-to-a-microsoft-365-f-plan"></a>التغيير من خطة Microsoft 365 E إلى خطة Microsoft 365 F

إذا كنت تفكر في تبديل بعض المستخدمين من خطة Microsoft 365 E إلى خطة Microsoft 365 [F3](https://www.microsoft.com/microsoft-365/enterprise/f3) أو [F1](https://www.microsoft.com/microsoft-365/enterprise/f1) ، فإن هذه المقالة توفر إرشادات لمساعدتك في إعداد مؤسستك للتغيير. يؤثر التغيير من خطة E إلى خطة F على الخدمات والميزات التي يمكن للمستخدمين الوصول إليها.

الخطط E مخصصة للعاملين في مجال المعلومات (الموظفون الذين يعملون عادة في مكتب) والخطط F مخصصة للعاملين في الخطوط الأمامية (الموظفون المتنقلون، وغالبا على الأجهزة المحمولة، ويعملون مباشرة مع العملاء أو الجمهور العام). قد تستمر كل خطة في التطور بمرور الوقت لتصبح أكثر تخصيصا للعاملين في مجال المعلومات والعاملين في الخطوط الأمامية على التوالي. لمعرفة المزيد، راجع [فهم أنواع المستخدمين في الخطوط الأمامية والترخيص](flw-licensing-options.md).

ستحصل على نظرة عامة حول ما يجب توقعه عند تبديل المستخدمين إلى خطة F، وكيفية الاستعداد للتغيير، وما يجب فعله بعد تبديل الخطط لانتقال العاملين في الخطوط الأمامية في مؤسستك.

## <a name="understand-the-key-differences-between-e-and-f-plans"></a>فهم الاختلافات الرئيسية بين خطط E وF

ابدأ بالتعرف على الخدمة واختلافات الميزات بين الخطط.

وتشمل بعض الاختلافات الرئيسية ما يلي:

- لا تتضمن خطط F تطبيقات Office لسطح المكتب أو تطبيق Outlook لسطح المكتب.
- تقتصر الخطط F على الأجهزة التي تحتوي على شاشات متكاملة أصغر من 10.1 بوصة على تطبيقات Office للأجهزة المحمولة.
- تقوم خطط F [بتثبيت تطبيقات عامل الواجهة الأمامية](pin-teams-apps-based-on-license.md) مثل Walkie Talkie والمهام والورديات والموافقات بشكل افتراضي في Microsoft Teams.

في هذا القسم، قمنا بتضمين مزيد من المعلومات حول هذه الاختلافات الرئيسية وتمييز بعض الاختلافات الإضافية التي يجب الانتباه إليها. ضع في اعتبارك أن هذه ليست قائمة شاملة. لمعرفة المزيد:

- راجع [مقارنة خطة العمل الحديثة](https://go.microsoft.com/fwlink/p/?linkid=2139145) للحصول على مقارنة مفصلة لما هو مضمن في خطط E وF.
- راجع [توفر الخدمة](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options#service-availability-within-each-microsoft-365-and-office-365-plan) [وتوافر الميزات عبر الخطط](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description#feature-availability-across-some-plans) للحصول على قائمة بتوفر الخدمة والميزات عبر خطط E وF.

### <a name="office-apps"></a>تطبيقات Office

لا يتم تضمين تطبيقات Office لسطح المكتب في خطط F3 وF1. يمكن للعاملين في الخطوط الأمامية استخدام Office على الويب وتطبيقات Office للأجهزة المحمولة لإنجاز المهام. ضع في اعتبارك أن مستخدمي F3 لديهم حق الوصول الكامل إلى المستندات في Office على الويب وأن مستخدمي F1 لديهم حق الوصول للقراءة فقط.

|الخدمة أو الميزة|Microsoft 365 E3/E5  |Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|تطبيقات Office لسطح المكتب (Word وExcel وOneNote وPowerPoint وAccess وPublisher)|نعم|لا|لا|
|Office على الويب (Word وExcel وOneNote وPowerPoint)|نعم|نعم|للقراءة فقط|
|تطبيقات Office للأجهزة المحمولة (Word وExcel وPowerPoint وOutlook وOneNote)|نعم|نعم&sup1;|للقراءة فقط|

&sup1; تحرير الملفات المدعومة على الأجهزة المزودة بشاشات متكاملة أقل من 10.1 بوصة.

#### <a name="office-for-the-web"></a>Office للويب

باستخدام Office على الويب، يستخدم موظفو الخطوط الأمامية مستعرض ويب لفتح ملفات Word وExcel وOneNote وPowerPoint.

إليك بعض الاختلافات التي يجب أن تكون على علم بها عند استخدام Office على الويب. للحصول على مقارنة ميزات مفصلة بين Office على الويب وتطبيقات Office لسطح المكتب، راجع [وصف الخدمة Office على الويب](/office365/servicedescriptions/office-online-service-description/office-online-service-description).

|الخدمة أو الميزة|بعض الاختلافات |التعرف على المزيد|
|---------|---------|---------|
|**Word للويب**|<ul><li> يمكن فتح المستندات الممكنة بماكرو (.docm) والقوالب (.dotm) وتحريرها ولكن لا يتم تشغيل وحدات الماكرو.</li><li>يمكن فتح المستندات المحمية بأذونات المستخدم (IRM) المحمية بالأذونات المعرفة من قبل المستخدم (IRM).</li></ul>|<ul><li>[وصف خدمة Word على الويب](/office365/servicedescriptions/office-online-service-description/word-online)</li><li>[الاختلافات بين استخدام مستند في المستعرض وفي Word](https://support.microsoft.com//office/differences-between-using-a-document-in-the-browser-and-in-word-3e863ce3-e82c-4211-8f97-5b33c36c55f8)</li></ul>|
|**Excel للويب**|<ul><li>يمكن فتح المصنفات الممكنة بماكرو (xlsm.) وتحريرها ولكن لا يتم تشغيل وحدات الماكرو.</li><li>[قيود حجم الملف](https://support.microsoft.com/office/file-size-limits-for-workbooks-in-sharepoint-9e5bc6f8-018f-415a-b890-5452687b325e)<ul><li>لعرض مصنف مخزن في SharePoint Online أو التفاعل معه، يجب أن يكون حجم المصنف أقل من 100 ميغابايت. </li><li>لفتح مصنف مرفق برسالة بريد إلكتروني في Outlook على ويب، يجب أن يكون حجم المصنف أقل من 10 ميغابايت.</li></ul></ul>|<ul><li>[وصف الخدمة Excel على الويب](/office365/servicedescriptions/office-online-service-description/excel-online)</li><li>[الاختلافات بين استخدام مصنف في المستعرض وفي Excel](https://support.microsoft.com/office/differences-between-using-a-workbook-in-the-browser-and-in-excel-f0dc28ed-b85d-4e1d-be6d-5878005db3b6)</li><li>تعمل معظم دالات Excel في مستعرض كما تعمل في Excel. للحصول على قائمة بالاستثناءات، راجع [الدالات في Excel وفي Excel على الويب](https://support.microsoft.com/office/differences-between-using-a-workbook-in-the-browser-and-in-excel-f0dc28ed-b85d-4e1d-be6d-5878005db3b6#__functions).</li></ul>|
|**OneNote للويب**|<ul><li>يقتصر البحث على المقطع الحالي.</li><li>التكبير والتصغير غير متوفرين. بدلا من ذلك، يمكن للمستخدمين استخدام ميزة التكبير/التصغير في المستعرض.</li></ul>|<ul><li>[وصف الخدمة OneNote على الويب](/office365/servicedescriptions/office-online-service-description/onenote-online)</li><li>[الاختلافات بين استخدام دفتر ملاحظات في المستعرض وفي OneNote](https://support.microsoft.com/office/differences-between-using-a-notebook-in-the-browser-and-in-onenote-a3d1fc13-ac74-456b-b391-b633a62aa83f)</li></ul>|
|**PowerPoint للويب**|<ul><li>يمكن فتح ملفات تصل إلى 2 غيغابايت.</li><li>يمكن فتح العروض التقديمية الممكنة بماكرو وتحريرها (.pptm و.potm وppsm. ولكن لا يتم تشغيل وحدات الماكرو.</li></ul>|<ul><li>[وصف الخدمة PowerPoint على الويب](/office365/servicedescriptions/office-online-service-description/powerpoint-online)</li><li>[كيفية تصرف بعض الميزات في PowerPoint المستند إلى الويب](https://support.microsoft.com/office/how-certain-features-behave-in-web-based-powerpoint-a931f0c8-1305-4428-8f7c-9cfa00ef28c5)</li></ul>|

#### <a name="office-mobile"></a>Office mobile

يمكن للعاملين في الخطوط الأمامية الحصول على Office على أجهزتهم المحمولة بطريقتين:

- قم بتثبيت تطبيق Office للأجهزة المحمولة الذي يجمع بين Word وExcel وPowerPoint.
- تثبيت تطبيقات Office للأجهزة المحمولة الفردية ل Word وExcel وPowerPoint وOneNote.

لمعرفة المزيد، راجع [تثبيت Office وإعداده على جهاز Android](https://support.microsoft.com/office/install-and-set-up-office-on-an-android-cafe9d6f-8b0c-4b03-b20a-12438a82a22d) [وتثبيت Office وإعداده على جهاز iPhone أو iPad](https://support.microsoft.com/office/install-and-set-up-office-on-an-iphone-or-ipad-9df6d10c-7281-4671-8666-6ca8e339b628).

لمزيد من المعلومات حول الميزات المتوفرة في Office للأجهزة المحمولة، راجع [ما يمكنك فعله في تطبيقات Office على الأجهزة المحمولة مع اشتراك Microsoft 365](https://support.microsoft.com/office/what-you-can-do-in-the-office-apps-on-mobile-devices-with-a-microsoft-365-subscription-9ef8b63a-05fd-4f9c-bac5-29da046833ea).

#### <a name="email"></a>البريد الالكتروني

لدى مستخدمي F3 علبة بريد بحجم 2 غيغابايت يمكنهم الوصول إليها من خلال Outlook على ويب. لمقارنة الميزات بين Outlook على ويب وتطبيق Outlook لسطح المكتب، راجع [مقارنة Outlook للكمبيوتر الشخصي Outlook على ويب وOutlook for iOS & Android](https://support.microsoft.com/office/compare-outlook-for-pc-outlook-on-the-web-and-outlook-for-ios-android-b26a7bf5-0ac7-48ba-97af-984e0645dde5).

لا يملك مستخدمو F1 حقوق علبة البريد. على الرغم من توفير علبة بريد للمستخدمين من خلال خطة Exchange Kiosk، إلا أنه لا يحق لهم استخدامها. نوصي [بتعطيل Outlook على ويب](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) لمستخدمي F1.

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|علبة بريد Exchange Online|نعم (علبة بريد 100 غيغابايت)|نعم (علبة بريد 2 غيغابايت)|لا&sup1؛|
|تطبيق Outlook لسطح المكتب|نعم|لا|لا|
|علبة بريد الأرشيف|نعم|لا|لا|
|تفويض الوصول|نعم|لا|لا|

&sup1; يتضمن F1 خطة Exchange Kiosk لتمكين تقويم Teams فقط ولا يتضمن حقوق علبة البريد.

لمعرفة المزيد، راجع [وصف الخدمة Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description).

#### <a name="teams"></a>الفرق

تتضمن خطط F3 وF1 تطبيق Teams لسطح المكتب وتطبيق الأجهزة المحمولة وتطبيق الويب للاتصال والتعاون بين العاملين في الخطوط الأمامية. يمكن للعاملين في الخطوط الأمامية الوصول إلى ميزات Teams بما في ذلك الاجتماعات والدردشة والقنوات والمحتوى والتطبيقات. ومع ذلك، لن يتمكنوا من إنشاء أحداث مباشرة وندوات عبر الإنترنت أو استخدام قدرات Teams Phone.

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|الأحداث المباشرة|نعم|لا|لا|
|بينرس|نعم|لا|لا|
|هاتف Teams|نعم|لا|لا|

#### <a name="sharepoint"></a>SharePoint

يمكن لمستخدمي F3 وF1 التعاون في العمل على المستندات والوصول إلى الموارد على مستوى المؤسسة مثل مواد التدريب المخزنة في SharePoint. ضع في اعتبارك أن خطط F3 وF1 لا تتضمن علب بريد الموقع أو المواقع الشخصية.

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|علبة بريد الموقع|نعم|لا|لا|
|الموقع الشخصي|نعم|لا|لا|

لمعرفة المزيد حول حدود SharePoint، راجع [حدود SharePoint](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).

#### <a name="content-services"></a>خدمات المحتوى

لدى مستخدمي F3 وF1 سعة تخزينية تبلغ 2 غيغابايت من OneDrive لتخزين الملفات ومشاركتها. لمعرفة المزيد، راجع [وصف خدمة OneDrive](/office365/servicedescriptions/onedrive-for-business-service-description).

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|OneDrive|تخزين غير محدود&sup1;|تخزين بسعة 2 غيغابايت|تخزين بسعة 2 غيغابايت|
|Microsoft Stream|نعم|نعم&sup2;|نعم&sup2;|
|Sway|نعم|نعم|لا|
|Visio للويب|نعم|نعم|للقراءة فقط|
|الخوض|نعم|لا|لا|

&sup1; ما يصل إلى 5 تيرابايت من مساحة التخزين الأولية في OneDrive لكل مستخدم استنادا إلى [الحصة النسبية الافتراضية](/onedrive/set-default-storage-space) للمستأجر للاشتراكات التي تحتوي على أكثر من خمسة مستخدمين. يمكن طلب المزيد من التخزين.</br>
&sup2; يمكن للمستخدمين تسجيل الاجتماعات واستهلاك محتوى Stream ولكن لا يمكنهم النشر إلى Stream أو المشاركة فيه.

#### <a name="insights-and-analytics"></a>التحليلات والرؤى

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Viva Insights|نعم|لا|لا|
|Power BI|نعم|لا|لا|

#### <a name="work-management-and-automation"></a>إدارة العمل والتشغيل التلقائي

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|تطبيقات الطاقة|نعم|نعم|لا|
|Power Automate|نعم|نعم|لا|
|Power Virtual Agents|نعم|نعم|لا|
|Dataverse for Teams|نعم|نعم|لا|
|Microsoft Forms|نعم&sup1;|نعم&sup1;|لا|
|Microsoft To Do|نعم|نعم|لا|

&sup1; يمكن للمستخدمين المرخص لهم إنشاء النماذج ومشاركتها وإدارتها. لا يلزم وجود ترخيص لإكمال نموذج أو الاستجابة له.

#### <a name="windows"></a>بالنسبة لنظام التشغيل

|الخدمة أو الميزة|Microsoft 365 E3/E5|Microsoft 365 F3|Microsoft 365 F1|
|---------|---------|---------|---------|
|Windows 11 Enterprise|نعم|نعم&sup1;|لا|

&sup1; لا Long-Term قناة الخدمة (LTSC) أو Microsoft Desktop Optimization Pack (MDOP). البنية الأساسية لسطح المكتب الظاهري (VDI) فقط للمستخدمين المرخصين لجهاز مشترك مع جودة الخدمة (QoS)، (باستثناء Azure Virtual Desktop).

## <a name="what-to-expect"></a>ما يجب توقعه

يسرد الجدول التالي الأشياء المهمة التي يجب مراعاتها والإجراءات الموصى بها التي يجب اتخاذها أثناء عملية التغيير. استخدم هذه المعلومات لمساعدتك على تحديد ما يجب فعله قبل التبديل وما يجب التخطيط له بعد اكتمال التبديل. 

سنشير إلى هذا الجدول في مقاطع لاحقة من هذه المقالة.

|الخدمة أو الميزة |قبل التبديل|بعد التبديل|
|---------|---------|---------|
|تطبيقات Office| <ul><li>تحديد الملفات المخزنة على أجهزة الكمبيوتر المحلية للمستخدمين ومساعدة المستخدمين على نقلها إلى OneDrive الخاص بهم.</li><li>ضع في اعتبارك أن تطبيقات Office لسطح المكتب ستنتقل إلى وضع الأداء الوظيفي المنخفض بعد التغيير إلى خطة F. كن مستعدا لإلغاء تثبيت تطبيقات Office لسطح المكتب بعد التبديل.</li></ul>| المستخدمين:</br> <ul><li>سجل الدخول إلى [office.com](https://www.office.com) للوصول إلى Office على الويب.</li><li>[تثبيت تطبيقات Office للأجهزة المحمولة واستخدامها](https://support.microsoft.com/office/set-up-office-apps-and-email-on-a-mobile-device-7dabb6cb-0046-40b6-81fe-767e0b1f014f) (إن لم يكن بالفعل).</li><li>يمكن للمستخدمين أيضا التعاون مباشرة في العمل على المستندات من مكتبات مستندات SharePoint وOneDrive وTeams وYammmer.</li></ul>المسؤولين:<ul><li>إلغاء تثبيت تطبيقات Office لسطح المكتب من أجهزة كمبيوتر المستخدمين.</li></ul>      |
|البريد الإلكتروني، Exchange، Outlook|<ul><li>حدد علب بريد المستخدمين التي يزيد حجمها عن 2 غيغابايت باستخدام [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics?view=exchange-ps) Exchange PowerShell cmdlet، ثم قم بتقليل حجم علبة البريد، حسب الحاجة. لمعرفة المزيد، راجع [حدود تخزين علبة البريد في Outlook على ويب](https://support.microsoft.com/office/mailbox-storage-limits-in-outlook-on-the-web-f170fe90-b859-4034-bcda-e186fc6a26f5).</li><li>إذا كان لدى المستخدمين علبة بريد أرشيف:</li><ul><li>انقل محتوى علبة بريد الأرشيف مرة أخرى إلى علبة بريد المستخدم.</li><li>تحقق من أي نهج أرشيف قد تنقل البريد الإلكتروني تلقائيا استنادا إلى عمر الرسائل باستخدام [Get-EXOMailbox](/powershell/module/exchange/get-exomailbox?view=exchange-ps) Exchange Online PowerShell cmdlet.</li></ul> <li>تحديد الوصول إلى علبة بريد الموقع واستخدامها.</li><li>تطبيق Outlook لسطح المكتب والبيانات والتكوين:</li><ul><li>تحديد المستخدمين وأجهزة الكمبيوتر التي تستخدم ملفات بيانات Outlook (pst.).</li><li>تحديد قواعد عميل Outlook فقط الموجودة وتوثيقها.</li><li>تصدير تواقيع البريد الإلكتروني.</li></ul></ul>|المستخدمين:</br><ul><li>سجل الدخول إلى [office.com](https://www.office.com) للوصول إلى Outlook على ويب.</li><li>[إعداد البريد الإلكتروني على الأجهزة المحمولة](https://support.microsoft.com/office/set-up-office-apps-and-email-on-a-mobile-device-7dabb6cb-0046-40b6-81fe-767e0b1f014f) (إن لم يكن بالفعل).</li><li>التحقق من تواقيع البريد وتحديثها.</li><li>التحقق من قواعد علبة البريد وتحديثها.</li></ul>المسؤولين:<ul><li> [قم بتعطيل Outlook على ويب](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-outlook-web-app) لمستخدمي F1 واطلب منهم عدم الوصول إلى علبة البريد من خلال أي أساليب أخرى.</li></ul>|
|الفرق | <ul><li>تحديد استخدام الأحداث المباشرة والندوات عبر الإنترنت.</li><li>تحديد المستخدمين الذين تم تمكين Teams Phone لهم. إذا كان المستخدمون يستخدمون هذه الميزة، فقد لا يكونوا المجموعة المناسبة من المستخدمين للانتقال إلى خطة F.</li></ul>      ||
|OneDrive | <ul><li>تحديد المستخدمين الذين يستخدمون أكثر من أو ما يقرب من 2 غيغابايت من مساحة التخزين. (سيصبح OneDrive للقراءة فقط للمستخدمين الذين تجاوزوا حد 2 غيغابايت بعد التبديل إلى خطة F.)</li><li>لمساعدة المستخدمين على تقليل عدد الملفات المخزنة في OneDrive والمقدار الإجمالي للتخزين المستخدم.</li><li>تأكد من مزامنة جميع الملفات بشكل كامل من أجهزة كمبيوتر المستخدمين إلى OneDrive.</li></ul>| |

## <a name="prepare-to-switch-plans"></a>التحضير لتبديل الخطط

### <a name="create-a-change-management-strategy"></a>إنشاء استراتيجية إدارة التغيير

تتضمن استراتيجية إدارة التغيير المثلى كيفية التواصل مع المستخدمين وتدريبهم ودعمهم قبل وبعد تبديلهم إلى خطة F. على سبيل المثال، إليك بعض الأمور التي يجب أخذها في الاعتبار:

- كيف سيكون المستخدمون على علم بالتبديل؟
- كيف سيتعلم المستخدمون التنقل بين الاختلافات في الخدمات والميزات؟ قد يحتاج التبديل إلى خطة F إلى جهد متزايد في التدريب لأنها تتطلب تغييرا في السلوك.
- كيف سيحصل المستخدمون على المساعدة والدعم؟

عند إنشاء استراتيجيتك، ضع في اعتبارك تفضيلات الاتصال والتدريب. للمساعدة في ضمان انتقال ناجح، خصص المراسلة والتدريب والدعم لتلبية الاحتياجات المحددة للعاملين في الخطوط الأمامية وثقافة الشركة.

فيما يلي بعض الأفكار للمساعدة في تخطيط استراتيجيتك.

|اتصال|التدريب|الدعم|
|---------|---------|---------|
|<ul><li>البريد الالكتروني</li><li>مديرو الأقسام أو المتاجر</li><li>ابطال</li><li>الفرق والقنوات</li><li>مجتمعات Yammer</li></ul> |<ul><li>موارد التعليمات والتدريب والفيديو عبر الإنترنت من Microsoft</li><li>التدريب الداخلي</li></ul>|<ul><li>مساعد داخلي</li><li>موقع إنترانت ذاتي الخدمة</li><li>موارد التعليمات والتدريب والفيديو عبر الإنترنت من Microsoft</li><li>متنزهو الطوابق والأبطال</li></ul>         |

قد ترغب أيضا في الاطلاع على موارد الاعتماد هذه لمساعدتك على إشراك المستخدمين وتدريبهم:

- [Microsoft 365 – اعتماد Microsoft](https://adoption.microsoft.com/microsoft-365/)
- [Teams للعاملين في الخطوط الأمامية – اعتماد Microsoft](https://adoption.microsoft.com/microsoft-teams/frontline-workers/)

### <a name="back-up-or-prepare-data"></a>نسخ البيانات احتياطيا أو إعدادها

تحديد البيانات التي يرغب المستخدمون في الاحتفاظ بها أو نسخها احتياطيا أو إعدادها. اتبع الإرشادات الواردة في القسم ["ما يجب توقعه](#what-to-expect) " سابقا في هذه المقالة وأكمل الإجراءات الموصى بها في العمود **"قبل التبديل"** في الجدول لكل مكون من المكونات التالية:

- تطبيقات Office
- البريد الإلكتروني، Exchange، Outlook
- الفرق
- OneDrive

لمزيد من المعلومات، راجع [النسخ الاحتياطي للبيانات قبل تبديل الخطط](/microsoft-365/commerce/subscriptions/back-up-data-before-switching-plans).

## <a name="switch-users-to-a-microsoft-365-f-plan"></a>تبديل المستخدمين إلى خطة Microsoft 365 F

يمكنك استخدام مركز مسؤولي Microsoft 365 لتغيير الخطط يدويا أو نهج نصي من خلال PowerShell cmdlets. أيا كان الأسلوب الذي تختاره، فمن المهم إكمال تعيين تغيير الترخيص في عملية واحدة. بمعنى آخر، قم بإزالة ترخيص E موجود واستبداله بتعيين ترخيص F في نفس العملية.

تجنب إزالة ترخيص موجود لمستخدم ثم إعادة تعيين ترخيص جديد في وقت لاحق. يمكن أن يؤثر القيام بذلك على بيانات المستخدم. لمعرفة المزيد، راجع [ماذا يحدث لبيانات المستخدم عند إزالة ترخيصه؟](/microsoft-365/admin/manage/remove-licenses-from-users?view=o365-worldwide#what-happens-to-a-users-data-when-you-remove-their-license).

للحصول على إرشادات مفصلة خطوة بخطوة حول كيفية تغيير الخطط في مركز إدارة Microsoft، راجع [تغيير خطط Microsoft يدويا](/microsoft-365/commerce/subscriptions/change-plans-manually).

## <a name="what-to-do-after-switching-plans"></a>ما يجب فعله بعد تبديل الخطط

اتبع الإرشادات الواردة في القسم ["ما يجب توقعه](#what-to-expect) " سابقا في هذه المقالة وأكمل الإجراءات الموصى بها في العمود **"بعد التبديل** " في الجدول لكل مكون من المكونات التالية:

- تطبيقات Office
- البريد الإلكتروني، Exchange، Outlook
- الفرق
- OneDrive

إبلاغ المستخدمين بإكمال التغيير وإعلامهم بكيفية الحصول على المساعدة كما هو محدد في استراتيجية إدارة التغيير. قد ترغب في تضمين ارتباطات إلى [موارد التعليمات والتعلم](#user-setup-help-and-learning-resources) لدعمها في المرحلة الانتقالية.

## <a name="user-setup-help-and-learning-resources"></a>إعداد المستخدم والتعليمات وموارد التعلم

فيما يلي بعض الارتباطات إلى الإعداد والتعليمات وموارد التعلم التي يمكنك مشاركتها مع العاملين في الخطوط الأمامية للتدريب والدعم.

|App|الروابط |
|---------|---------|
|Office للويب|<ul><li>[تدريب Office على الويب](https://support.microsoft.com/office/office-for-the-web-training-e315b031-2bd5-40a1-99ca-264ebf2c8f96)</li><li>[بدء استخدام Office على الويب في Microsoft 365](https://support.microsoft.com/office/get-started-with-office-for-the-web-in-microsoft-365-5622c7c9-721d-4b3d-8cb9-a7276c2470e5)</li></ul>|
|Outlook على ويب|<ul><li>[التعرف على Outlook على ويب](https://support.microsoft.com/office/get-to-know-outlook-on-the-web-3f1a229b-0d60-438f-b515-dd7a28026bc1)</li><li>[الحصول على تعليمات حول Outlook على ويب](https://support.microsoft.com/office/get-help-with-outlook-on-the-web-cf659288-35cc-4c6c-8c75-e8e4317fda11)</li><li>[مقاطع فيديو Outlook على ويب](https://support.microsoft.com/office/learn-more-about-outlook-on-the-web-adbacbab-fe59-4259-a550-6cb7f85f19ec)</li></ul>|
|Office mobile|اعداد:</br><ul><li>[إعداد تطبيقات Office والبريد الإلكتروني على Android](https://support.microsoft.com/office/set-up-office-apps-and-email-on-android-6ef2ebf2-fc2d-474a-be4a-5a801365c87f)</li><li>[إعداد تطبيقات Office والبريد الإلكتروني على أجهزة iOS](https://support.microsoft.com/office/set-up-the-office-app-and-outlook-on-ios-devices-0402b37e-49c4-4419-a030-f34c2013041f)</li></ul>تعليمات تطبيق Office للأجهزة المحمولة:<ul><li>[تعليمات تطبيق Office للأجهزة المحمولة ل Android](https://support.microsoft.com/office/microsoft-office-app-for-android-0383d031-a1c6-46c9-b734-53cd1d22765b)</li><li>[تعليمات تطبيق Office ل iOS](https://support.microsoft.com/office/microsoft-office-app-for-ios-c8880c05-883a-46b6-ad32-9bffa31228d0)</li></ul>تعليمات تطبيق Office للأجهزة المحمولة الفردية:<ul><li>[Word for Android الهواتف](https://support.microsoft.com/office/word-for-android-phones-help-764afb31-ad50-4645-8f51-820ecf731d8f) وأجهزة [الكمبيوتر اللوحية Word for Android](https://support.microsoft.com/office/word-for-android-tablets-help-8a0dcd56-fb32-4e0d-95d8-997c066125c8) [وWord for iPhone](https://support.microsoft.com/office/word-for-iphone-help-d41a5299-f6fa-4cca-b529-46a8069c5796) [Word for iPad](https://support.microsoft.com/office/word-for-ipad-help-6567cf2a-c949-4213-912d-f7a14f6264c5)</li><li>[Excel for Android الهواتف](https://support.microsoft.com/office/excel-for-android-phones-help-f818cb37-bfac-485d-8480-363b3da40596) وأجهزة [الكمبيوتر اللوحي Excel for Android](https://support.microsoft.com/office/word-for-android-tablets-help-8a0dcd56-fb32-4e0d-95d8-997c066125c8) [وExcel for iPhone](https://support.microsoft.com/office/excel-for-iphone-help-b367819b-05b4-4a56-ab1c-678da62e1fd3) [Excel for iPad](https://support.microsoft.com/office/excel-for-ipad-help-6b5dc2e1-a8e4-48e6-bb69-cb9a3964bc91)</li><li>[PowerPoint for Android الهواتف](https://support.microsoft.com/office/powerpoint-for-android-phones-help-f6714e00-0ee2-48d1-bd3d-e1997565861f) وأجهزة [الكمبيوتر اللوحية PowerPoint for Android](https://support.microsoft.com/office/powerpoint-for-android-tablets-help-2ada1d22-3784-4943-bc47-9d1ede42875c) [وPowerPoint for iPhone](https://support.microsoft.com/office/powerpoint-for-iphone-help-754fcb37-783b-4e8a-afca-edb900221b8b) [PowerPoint for iPad](https://support.microsoft.com/office/powerpoint-for-ipad-help-b75ce3bb-03e3-46df-a792-647573fef84a)</li><li>[OneNote for Android](https://support.microsoft.com/office/microsoft-onenote-for-android-46b4b49d-2bef-4746-9c30-6abb5e20b688)[، OneNote for iPhone](https://support.microsoft.com/office/microsoft-onenote-for-iphone-b93a0ea8-1285-4d31-a7c5-86a849731902)، [OneNote for iPad](https://support.microsoft.com/office/microsoft-onenote-help-ipad-f44e5bcd-5203-4553-9de4-0c56e6500825)</li></ul>
|الفرق|<ul><li>[فيديو تدريبي على Teams](https://support.microsoft.com/office/microsoft-teams-video-training-4f108e54-240b-4351-8084-b1089f0d21d7)</li><li>[تساعد Teams في & التعلم](https://support.microsoft.com/teams)</li></ul>|

