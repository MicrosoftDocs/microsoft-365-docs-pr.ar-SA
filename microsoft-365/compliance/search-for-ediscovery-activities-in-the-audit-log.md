---
title: البحث عن أنشطة eDiscovery في سجل التدقيق
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 67cc7f42-a53d-4751-b929-6005c80798f7
description: تعرف على الأحداث التي يتم تسجيلها عندما يقوم المستخدمون المعينون لأذونات eDiscovery بإجراء البحث في المحتوى و eDiscovery الأساسي Advanced eDiscovery المهام في مركز التوافق في Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: eb1a6f1ee0ff9c84f4dbfc7f42427ae9dda499de
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63566327"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>البحث عن أنشطة eDiscovery في سجل التدقيق

يتم تسجيل الأنشطة المتعلقة بالبحث في المحتوى والأنشطة ذات الصلة ب eDiscovery (ل eDiscovery الأساسية و Advanced eDiscovery) التي يتم تنفيذها في مركز التوافق في Microsoft 365 أو عن طريق تشغيل الأمرين cmdlets المطابقين ل PowerShell في سجل التدقيق. يتم تسجيل الأحداث عندما يقوم المسؤولون أو مديرو eDiscovery (أو أي مستخدم تم تعيين أذونات eDiscovery له) بتنفيذ المهام التالية البحث في المحتوى و eDiscovery الأساسية في مركز التوافق في Microsoft 365:
  
- إنشاء حالات أساسية Advanced eDiscovery وإدارتها

- إنشاء عمليات البحث في المحتوى وبدءها وتحريرها

- تنفيذ إجراءات البحث، مثل معاينة نتائج البحث وتصديرها وحذفها

- إدارة المراجعين ومراجعة المجموعات في Advanced eDiscovery

- تكوين تصفية الأذونات للبحث في المحتوى

- إدارة دور مسؤول eDiscovery
  
لمزيد من المعلومات حول البحث في سجل التدقيق والأذونات المطلوبة وتصدير نتائج البحث، راجع البحث في [سجل التدقيق في](search-the-audit-log-in-security-and-compliance.md) مركز التوافق في Microsoft 365.
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>كيفية البحث عن أنشطة eDiscovery وعرضها

في الوقت الحالي، يجب عليك القيام ببعض الأمور المحددة لعرض أنشطة eDiscovery في سجل التدقيق. إليك كيفية ذلك.
  
1. انتقل إلى <https://compliance.microsoft.com> حساب العمل أو المدرسة الخاص بك ثم سجل الدخول إليه.

2. في جزء التنقل الأيسر من مركز التوافق في Microsoft 365، انقر فوق **تدقيق**.

3. في القائمة **المنسدل** الأنشطة، ضمن **أنشطة eDiscovery** أو Advanced eDiscovery، انقر فوق نشاط واحد أو أكثر للبحث عنه.

    > [!NOTE]
    > تتضمن **القائمة المنسدل** الأنشطة أيضا مجموعة من الأنشطة المسماة **أنشطة cmdlet eDiscovery** التي إرجاع السجلات من سجل تدقيق cmdlet.
  
4. حدد تاريخا ونطاقا من الوقت لعرض أحداث eDiscovery التي وقعت خلال تلك الفترة.

5. في المربع **المستخدمون** ، حدد مستخدما واحدا أو أكثر لعرض نتائج البحث له. اترك هذا المربع فارغا لإرجاع الإدخالات لجميع المستخدمين.

6. انقر **فوق** بحث لتشغيل البحث باستخدام معايير البحث.

7. بعد عرض نتائج البحث، يمكنك النقر فوق **تصفية** النتائج لتصفية سجلات النشاط الناتجة أو فرزها. لسوء الحظ، لا يمكنك استخدام التصفية لاستبعاد أنشطة معينة بشكل صريح. 

8. لعرض تفاصيل حول نشاط ما، انقر فوق سجل النشاط في قائمة نتائج البحث. 

    يتم **عرض صفحة** تفاصيل من القائمة المطيرة التي تحتوي على الخصائص المفصلة من سجل الحدث. لعرض تفاصيل إضافية، انقر فوق **مزيد من المعلومات**. للحصول على وصف لهذه الخصائص، راجع [القسم الخصائص المفصلة لأنشطة eDiscovery](#detailed-properties-for-ediscovery-activities) .

9. إذا أردت ذلك، يمكنك تصدير نتائج البحث في سجل التدقيق إلى ملف CSV، ثم استخدام Excel Power Query لتنسيق هذه السجلات وتصفيتها. لمزيد من المعلومات، راجع [تصدير سجلات](export-view-audit-log-records.md) سجل التدقيق وتكوينها وعرضها.

## <a name="ediscovery-activities"></a>أنشطة eDiscovery

يصف الجدول التالي أنشطة البحث في المحتوى و eDiscovery الأساسية التي يتم تسجيلها عندما يقوم مسؤول أو مدير eDiscovery بتنفيذ نشاط مرتبط ب eDiscovery باستخدام مركز التوافق في Microsoft 365. قد يتم إرجاع بعض الأنشطة Advanced eDiscovery عند البحث عن أنشطة في هذه القائمة.
  
> [!NOTE]
> توفر أنشطة eDiscovery الموضحة في هذا القسم معلومات مماثلة لأنشطة eDiscovery cmdlet الموضحة في المقطع التالي. نوصي باستخدام أنشطة eDiscovery الموضحة في هذا القسم لأنها ستظهر في نتائج البحث في سجل التدقيق في غضون 30 دقيقة. قد يستغرق ظهور أنشطة eDiscovery cmdlet في نتائج البحث في سجل التدقيق ما يصل إلى 24 ساعة.
  
|**اسم ودود**|**العملية**|**cmdlet المطابق**|**الوصف**|
|:-----|:-----|:-----|:-----|
|عضو مضاف إلى حالة eDiscovery  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |تم إضافة مستخدم كعضو في حالة eDiscovery. كعضو في حالة ما، يمكن للمستخدم تنفيذ مهام متنوعة ذات صلة بالحالتين استنادا إلى ما إذا تم تعيين الأذونات اللازمة له.  <br/> |
|البحث في المحتوى الذي تم تغييره  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |تم تغيير بحث محتوى موجود. يمكن أن تتضمن التغييرات إضافة مواقع المحتوى أو إزالتها أو تحرير استعلام البحث.  <br/> |
|عضوية مسؤول eDiscovery التي تم تغييرها  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |تم تغيير قائمة مسؤولي eDiscovery في مؤسستك. يتم تسجيل هذا النشاط عند استبدال قائمة مسؤولي eDiscovery مع مجموعة من المستخدمين الجدد. إذا تمت إضافة مستخدم واحد أو إزالته، يتم تسجيل العملية CaseAdminAdded.  <br/> |
|حالة eDiscovery التي تم تغييرها  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |تم تغيير حالة eDiscovery. تتضمن التغييرات إغلاق حالة مفتوحة أو إعادة فتح حالة مغلقة.  <br/> |
|عضوية حالة eDiscovery التي تم تغييرها  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |تم تغيير قائمة العضوية في حالة eDiscovery. يتم تسجيل هذا النشاط عند استبدال كل الأعضاء بمجموعه من المستخدمين الجدد. إذا تمت إضافة عضو واحد أو إزالته، يتم تسجيل عملية CaseMemberAdded أو CaseMemberRemoved.  <br/> |
|عامل تصفية أذونات البحث الذي تم تغييره  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |تم تغيير عامل تصفية أذونات البحث.  <br/> |
|تم تغيير استعلام البحث عن حالة eDiscovery مع الاستمرار  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |تم تغيير قائمة الانتظار المستندة إلى الاستعلام والمقترنة ب eDiscovery case. تتضمن التغييرات المحتملة تحرير الاستعلام أو نطاق التاريخ لفترة انتظار مستندة إلى الاستعلام.  <br/> |
|تنزيل عنصر معاينة البحث في المحتوى  <br/> |PreviewItemDownloaded  <br/> |N/A  <br/> |قام مستخدم بتنزيل عنصر إلى الكمبيوتر المحلي (بالنقر فوق الارتباط **تنزيل العنصر** الأصلي) عند معاينة نتائج البحث.  <br/> |
|عنصر معاينة البحث في المحتوى مدرج  <br/> |PreviewItemListed  <br/> |N/A  <br/> |قام مستخدم بالنقر فوق  معاينة نتائج البحث لعرض صفحة معاينة نتائج البحث، التي تسرد ما يصل إلى 1000 عنصر من نتائج البحث.  <br/> |
|عرض عنصر معاينة البحث في المحتوى  <br/> |PreviewItemRendered  <br/> |N/A  <br/> |عرض مدير eDiscovery عنصر بالنقر فوقه عند معاينة نتائج البحث.  <br/> |
|البحث في المحتوى الذي تم إنشاؤه  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |تم إنشاء بحث محتوى جديد.  <br/> |
|مسؤول eDiscovery الذي تم إنشاؤه  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |تم إضافة مستخدم كمسؤول eDiscovery في المؤسسة.  <br/> |
|حالة eDiscovery التي تم إنشاؤها  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |تم إنشاء حالة eDiscovery. عند إنشاء حالة، يجب عليك فقط أن تعطيها اسما. تؤدي المهام الأخرى ذات الصلة بالحالتين، مثل إضافة الأعضاء وإنشاء عمليات التحمس وإنشاء عمليات البحث في المحتوى المقترنة بهذه الحالة إلى تسجيل أحداث إضافية.  <br/> |
|عامل تصفية أذونات البحث الذي تم إنشاؤه  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |تم إنشاء عامل تصفية أذونات البحث.  <br/> |
|استعلام البحث الذي تم إنشاؤه ل eDiscovery case hold  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |تم إنشاء قائمة الانتظار المستندة إلى الاستعلام والمقترنة ب eDiscovery case.  <br/> |
|البحث عن محتوى محذوف  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |تم حذف بحث محتوى موجود.  <br/> |
|مسؤول eDiscovery المحذوف  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |تم حذف مسؤول eDiscovery من مؤسستك.  <br/> |
|حالة eDiscovery المحذوفة  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |تم حذف حالة eDiscovery. يجب إزالة أي جلسة مع الاستمرار مقترنة بالقضية قبل أن يمكن حذف الحالة.  <br/> |
|عامل تصفية أذونات البحث المحذوفة  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |تم حذف عامل تصفية أذونات البحث.  <br/> |
|استعلام البحث المحذوف ل eDiscovery case hold  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |تم حذف قائمة الانتظار المستندة إلى الاستعلام والمقترنة ب eDiscovery case. غالبا ما تكون إزالة الاستعلام من الانتظار ناتجة عن حذف جلسة انتظار. عند حذف استعلام الانتظار أو الانتظار، يتم إصدار مواقع المحتوى التي كانت في الانتظار.  <br/> |
|تصدير البحث في المحتوى الذي تم تنزيله  <br/> |SearchExportDownloaded  <br/> |N/A  <br/> |قام مستخدم بتنزيل نتائج البحث في المحتوى إلى الكمبيوتر المحلي. يجب **بدء تصدير** نشاط البحث في المحتوى الذي تم بدءه قبل تنزيل نتائج البحث.  <br/> |
|نتائج البحث في المحتوى التي تم معاينتها  <br/> |SearchPreviewed  <br/> |N/A  <br/> |قام مستخدم بمعاينة نتائج البحث في المحتوى.  <br/> |
|نتائج البحث في المحتوى التي تم إزالةها  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |قام مستخدم بحذف نتائج البحث في المحتوى عن طريق تشغيل الأمر **New-ComplianceSearchAction -Purge** .  <br/> |
|تحليل تمت إزالته للبحث في المحتوى  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |تم حذف إجراء التحضير للبحث في المحتوى (لإعداد نتائج البحث Advanced eDiscovery) . إذا كان عمر إجراء التحضير أقل من أسبوعين، تم حذف نتائج البحث التي تم إعدادها Advanced eDiscovery من مساحة تخزين Microsoft Azure. إذا كان إجراء الإعداد أقدم من أسبوعين، فهذا يعني أن هذا الحدث يشير إلى أنه تم حذف إجراء التحضير المطابق فقط.  <br/> |
|التصدير المزال للبحث في المحتوى  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |تم حذف إجراء تصدير البحث في المحتوى. إذا كان عمر إجراء التصدير أقل من أسبوعين، تم حذف نتائج البحث التي تم تحميلها إلى منطقة تخزين Microsoft Azure. إذا كان إجراء التصدير أقدم من أسبوعين، فهذا يعني أن هذا الحدث يشير إلى أنه تم حذف إجراء التصدير المناظر فقط.  <br/> |
|العضو الذي تمت إزالته من حالة eDiscovery  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |تمت إزالة مستخدم كعضو في حالة eDiscovery.  <br/> |
|نتائج المعاينة التي تمت إزالتها للبحث في المحتوى  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |تم حذف إجراء معاينة البحث في المحتوى.  <br/> |
|إجراء إزالة تمت إزالته تم تنفيذها على البحث في المحتوى  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |تم حذف إجراء إزالة البحث في المحتوى.  <br/> |
|تقرير البحث الذي تمت إزالته  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |تم حذف إجراء تقرير تصدير البحث في المحتوى.  <br/> |
|بدء تحليل البحث في المحتوى  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |تم إعداد نتائج البحث في المحتوى لتحليلها في Advanced eDiscovery.  <br/> |
|البحث عن المحتوى الذي تم بدءه  <br/> |SearchStarted  <br/> |Start-ComplianceSearch  <br/> |تم بدء البحث في المحتوى. عند إنشاء بحث محتوى أو تغييره باستخدام مركز التوافق في Microsoft 365، يتم بدء البحث تلقائيا.<br/> |
|بدء تصدير البحث في المحتوى  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |قام مستخدم بتصدير نتائج البحث في المحتوى.  <br/> |
|تقرير التصدير الذي بدأ  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |قام مستخدم بتصدير تقرير البحث في المحتوى.  <br/> |
|بحث المحتوى المتوقف  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |أوقف مستخدم عملية بحث في المحتوى.  <br/> |
|(none)|CaseViewed|Get-ComplianceCase|عرض مستخدم حالة eDiscovery الأساسية في مركز التوافق. يتضمن سجل التدقيق لهذا الحدث اسم الحالة التي تم عرضها. |
|(none)|SearchViewed|Get-ComplianceSearch|عرض مستخدم البحث في المحتوى في مركز التوافق من خلال الوصول إلى البحث على علامة التبويب عمليات  البحث في حالة eDiscovery الأساسية أو الوصول إليه على صفحة البحث **في المحتوى**. يتضمن سجل التدقيق لهذا الحدث هوية البحث الذي تم عرضه.|
|(none)|ViewedSearchExported|Get-ComplianceSearchAction -Export|عرض مستخدم عملية تصدير البحث في المحتوى في مركز التوافق من خلال الوصول إلى عملية التصدير على علامة  التبويب عمليات التصدير على صفحة **البحث في** المحتوى. يتم تسجيل هذا النشاط أيضا عندما يقوم المستخدم ب عرض عملية تصدير مقترنة ب حالة eDiscovery الأساسية.|
|(none)|ViewedSearchPreviewed|Get-ComplianceSearchAction -Preview|قام مستخدم بمعاينة نتائج البحث في المحتوى في مركز التوافق. يتم تسجيل هذا النشاط أيضا عندما يقوم المستخدم بمعاينة نتائج عملية بحث مقترنة ب حالة eDiscovery الأساسية.|
|||||
  
## <a name="advanced-ediscovery-activities"></a>Advanced eDiscovery الأنشطة

يصف الجدول التالي Advanced eDiscovery التي تم تسجيلها في سجل التدقيق. يمكن استخدام هذه الأنشطة لمساعدتك على تعقب تقدم النشاط في حالة Advanced eDiscovery أخرى.

|**اسم ودود**|**العملية**|**الوصف**|
|:-----|:-----|:-----|
|إضافة بيانات إلى مجموعة مراجعة أخرى|AddWorkingSetQueryToWorkingSet|أضاف المستخدم مستندات من مجموعة مراجعة واحدة إلى مجموعة مراجعة مختلفة.|
|مجموعة البيانات المضافة لمراجعتها|AddQueryToWorkingSet|أضاف المستخدم نتائج البحث من بحث محتوى مقترن Advanced eDiscovery حالة إلى مجموعة مراجعة.|
|مجموعة البيانات غير Microsoft 365 المضافة لمراجعتها|AddNonOffice365DataToWorkingSet|أضاف المستخدم بيانات Microsoft 365 إلى مجموعة مراجعة.|
|مجموعة المستندات التي تم إصلاحها والمضافة لمراجعتها|AddRemediatedData|يقوم المستخدم بتحميل المستندات التي بها أخطاء فهرسة تم تصحيحها إلى مجموعة مراجعة.|
|البيانات التي تم تحليلها في مجموعة المراجعة|RunAlgo|قام المستخدم ب إجراء تحليلات على المستندات في مجموعة مراجعة.|
|مستند مشروح توضيحي في مجموعة المراجعة|تعليق توضيحيDocument|قام المستخدم بشرح مستند في مجموعة مراجعة. تتضمن التعليقات التوضيحية محتوى إعادة تنشيط في مستند.|
|مقارنة مجموعات التحميل|LoadComparisonJob|قام المستخدم بمقارنة مجموعتين مختلفتين من التحميلات في مجموعة مراجعة. مجموعة التحميل هي عند إضافة بيانات من بحث محتوى مقترن بالقضية إلى مجموعة مراجعة.|
|المستندات التي تم تحويلها إلى PDF|BurnJob|قام المستخدم بتحويل كل المستندات التي تم تحريرها في مجموعة مراجعة إلى ملفات PDF.|
|مجموعة المراجعة التي تم إنشاؤها|CreateWorkingSet|أنشأ المستخدم مجموعة مراجعة.|
|البحث في مجموعة المراجعة التي تم إنشاؤها|CreateWorkingSetSearch|أنشأ المستخدم استعلام بحث يبحث في المستندات في مجموعة مراجعة.|
|علامة تم إنشاؤها|CreateTag|أنشأ المستخدم مجموعة علامات في مجموعة مراجعة. يمكن أن تحتوي مجموعة العلامات على علامة واحدة أو أكثر من العلامات الخاصة. بعد ذلك، يتم استخدام هذه العلامات لعلامة المستندات في مجموعة المراجعة.|
|البحث في مجموعة المراجعة المحذوفة|DeleteWorkingSetSearch|حذف المستخدم استعلام بحث في مجموعة مراجعة.|
|علامة محذوفة|DeleteTag|حذف المستخدم علامة أو مجموعة علامات في مجموعة مراجعة.|
|مستند تم تنزيله|DownloadDocument|قام المستخدم بتنزيل مستند من مجموعة مراجعة.|
|علامة تم تحريرها|UpdateTag|قام المستخدم بتغيير علامة في مجموعة مراجعة.|
|المستندات التي تم تصديرها من مجموعة المراجعة|ExportJob|قام المستخدم بتصدير المستندات من مجموعة مراجعة.|
|إعداد حالة الضبط|UpdateCaseSettings|قام المستخدم بتعديل إعدادات حالة. تتضمن إعدادات الحالة معلومات حالة الاتصال وأذونات الوصول والإعدادات التي تتحكم في سلوك البحث والتحليلات.|
|البحث في مجموعة المراجعة المعدلة|UpdateWorkingSetSearch|قام المستخدم بتحرير استعلام بحث في مجموعة مراجعة.|
|البحث في مجموعة المراجعة المعاينة|PreviewWorkingSetSearch|قام المستخدم بمعاينة نتائج استعلام بحث في مجموعة مراجعة.|
|تصحيح مستندات الخطأ|ErrorRemediationJob|يقوم المستخدم بإصلاح الملفات التي تحتوي على أخطاء الفهرسة.|
|مستند تم وضع علامة عليه|TagFiles|يقوم المستخدم بعلامة مستند في مجموعة مراجعة.|
|النتائج المعلمة لاستعلام|TagJob|يقوم المستخدم بعلامة على كل المستندات التي تتطابق مع معايير استعلام البحث في مجموعة مراجعة.|
|مستند تم عرضه في مجموعة المراجعة|ViewDocument|عرض المستخدم مستندا في مجموعة مراجعة.|
|||

## <a name="ediscovery-cmdlet-activities"></a>أنشطة eDiscovery cmdlet

يسرد الجدول التالي سجلات سجل تدقيق cmdlet التي يتم تسجيلها عندما يقوم مسؤول أو مستخدم بتنفيذ نشاط مرتبط ب eDiscovery باستخدام مركز التوافق أو عن طريق تشغيل الأمر cmdlet المناظر في مركز التوافق & مركز التوافق PowerShell. تختلف المعلومات المفصلة في سجل التدقيق عن أنشطة cmdlet المدرجة في هذا الجدول وأنشطة eDiscovery الموضحة في المقطع السابق.
  
كما ذكر سابقا، قد يستغرق ظهور أنشطة eDiscovery cmdlet في نتائج البحث في سجل التدقيق ما يصل إلى 24 ساعة.
  
> [!TIP]
> ترتبط cmdlets في **عمود العملية** في الجدول التالي بموضوع تعليمات cmdlet المطابق على TechNet. انتقل إلى موضوع تعليمات cmdlet للحصول على وصف للمعلمات المتوفرة لكل cmdlet. يتم تضمين المعلمة وقيمة المعلمة التي تم استخدامها مع cmdlet في إدخال سجل التدقيق لكل نشاط cmdlet eDiscovery تم تسجيله. 
  
|**اسم ودود**|**العملية (cmdlet)**|**الوصف**|
|:-----|:-----|:-----|
|تم إنشاء الاستمرار في حالة eDiscovery  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |تم إنشاء الاستمرار في حالة eDiscovery. يمكن إنشاء جلسة انتظار باستخدام أو بدون تحديد مصدر محتوى. إذا تم تحديد مصادر المحتوى، سيتم تعريفها في إدخال سجل التدقيق.  <br/> |
|تم حذف الاستمرار من حالة eDiscovery  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |تم حذف مع الاستمرار المقترن بقضيه eDiscovery. يحرر حذف أحد الانتظار كل مواقع المحتوى من وضع الانتظار. يؤدي حذف الاستمرار أيضا إلى حذف قواعد الاستمرار حالة الحذف المقترنة مع الاستمرار (راجع **Remove-CaseHoldRule** أدناه).  <br/> |
|تم تغيير حالة الانتظار في حالة eDiscovery  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |تم تغيير الاستمرار المقترن ب eDiscovery. تتضمن التغييرات المحتملة إضافة مواقع المحتويات أو إزالتها أو إيقاف تشغيل (تعطيل) وضع الانتظار.  <br/> |
|استعلام البحث الذي تم إنشاؤه ل eDiscovery case hold  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |تم إنشاء قائمة الانتظار المستندة إلى الاستعلام والمقترنة ب eDiscovery case.  <br/> |
|استعلام البحث المحذوف ل eDiscovery case hold  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |تم حذف قائمة الانتظار المستندة إلى الاستعلام والمقترنة ب eDiscovery case. غالبا ما تكون إزالة الاستعلام من الانتظار ناتجة عن حذف جلسة انتظار. عند حذف استعلام الانتظار أو الانتظار، يتم إصدار مواقع المحتوى التي كانت في الانتظار.  <br/> |
|تم تغيير استعلام البحث عن حالة eDiscovery مع الاستمرار  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |تم تغيير قائمة الانتظار المستندة إلى الاستعلام والمقترنة ب eDiscovery case. تتضمن التغييرات المحتملة تحرير الاستعلام أو نطاق التاريخ لفترة انتظار مستندة إلى الاستعلام.  <br/> |
|حالة eDiscovery التي تم إنشاؤها  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |تم إنشاء حالة eDiscovery. عند إنشاء حالة، يجب عليك فقط أن تعطيها اسما. تؤدي المهام الأخرى ذات الصلة بالحالتين، مثل إضافة الأعضاء وإنشاء عمليات التحمس وإنشاء عمليات البحث في المحتوى المقترنة بهذه الحالة إلى تسجيل أحداث إضافية.  <br/> |
|حالة eDiscovery المحذوفة  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |تم حذف حالة eDiscovery. يجب إزالة أي جلسة مع الاستمرار مقترنة بالقضية قبل أن يمكن حذف الحالة.  <br/> |
|حالة eDiscovery التي تم تغييرها  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |تم تغيير حالة eDiscovery. تتضمن التغييرات إغلاق حالة مفتوحة أو إعادة فتح حالة مغلقة.  <br/> |
|عضو مضاف إلى حالة eDiscovery  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |تم إضافة مستخدم كعضو في حالة eDiscovery. كعضو في حالة ما، يمكن للمستخدم تنفيذ مهام متنوعة ذات صلة بالحالتين استنادا إلى ما إذا تم تعيين الأذونات اللازمة له.  <br/> |
|العضو الذي تمت إزالته من حالة eDiscovery  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |تمت إزالة مستخدم كعضو في حالة eDiscovery.  <br/> |
|عضوية حالة eDiscovery التي تم تغييرها  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |تم تغيير قائمة العضوية في حالة eDiscovery. يتم تسجيل هذا النشاط عند استبدال كل الأعضاء بمجموعه من المستخدمين الجدد. إذا تمت إضافة عضو واحد أو إزالته، يتم تسجيل العملية **Add-ComplianceCaseMember** أو **Remove-ComplianceCaseMember** .  <br/> |
|البحث في المحتوى الذي تم إنشاؤه  <br/> |[البحث عن التوافق الجديد](/powershell/module/exchange/new-compliancesearch) <br/> |تم إنشاء بحث محتوى جديد.  <br/> |
|البحث عن محتوى محذوف  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |تم حذف بحث محتوى موجود.  <br/> |
|البحث في المحتوى الذي تم تغييره  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |تم تغيير بحث محتوى موجود. يمكن أن تتضمن التغييرات إضافة مواقع المحتوى التي يتم البحث عنها وتحرير استعلام البحث أو إزالتها.  <br/> |
|البحث عن المحتوى الذي تم بدءه  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |تم بدء البحث في المحتوى. عند إنشاء بحث محتوى أو تغييره باستخدام واجهة GUI لمركز التوافق، يتم بدء البحث تلقائيا. إذا قمت بإنشاء بحث أو تغييره باستخدام **الأمر cmdlet البحث عن جديد-ComplianceSearch** أو **Set-ComplianceSearch** ، يجب تشغيل الأمر **cmdlet Start-ComplianceSearch** لبدء البحث.  <br/> |
|بحث المحتوى المتوقف  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |تم إيقاف البحث في المحتوى الذي كان قيد التشغيل.  <br/> |
|إجراء البحث في المحتوى الذي تم إنشاؤه  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |تم إنشاء إجراء بحث في المحتوى. تتضمن إجراءات البحث في المحتوى معاينة نتائج البحث وتصدير نتائج البحث وتحضير نتائج البحث للتحليل في Advanced eDiscovery وحذف العناصر التي تتطابق مع معايير البحث في المحتوى بشكل دائم.  <br/> |
|إجراء البحث في المحتوى المحذوف  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |تم حذف إجراء البحث في المحتوى.  <br/> |
|عامل تصفية أذونات البحث الذي تم إنشاؤه  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |تم إنشاء عامل تصفية أذونات البحث.  <br/> |
|عامل تصفية أذونات البحث المحذوفة  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |تم حذف عامل تصفية أذونات البحث.  <br/> |
|عامل تصفية أذونات البحث الذي تم تغييره  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |تم تغيير عامل تصفية أذونات البحث.  <br/> |
|مسؤول eDiscovery الذي تم إنشاؤه  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |تم إضافة مستخدم كمسؤول eDiscovery في مؤسستك.  <br/> |
|مسؤول eDiscovery المحذوف  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |تم حذف مسؤول eDiscovery من مؤسستك.  <br/> |
|عضوية مسؤول eDiscovery التي تم تغييرها  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |تم تغيير قائمة مسؤولي eDiscovery في مؤسستك. يتم تسجيل هذا النشاط عند استبدال قائمة مسؤولي eDiscovery مع مجموعة من المستخدمين الجدد. إذا تمت إضافة مستخدم واحد أو إزالته، يتم تسجيل العملية **Add-eDiscoveryCaseAdmin** أو **Remove-eDiscoveryCaseAdmin** .  <br/> |
|(none)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|يتم تسجيل هذا النشاط عندما يعرض المستخدم قائمة ب eDiscovery أو Advanced eDiscovery الحالات. يتم تسجيل هذا النشاط أيضا عندما يقوم المستخدم ب عرض حالة معينة في Core eDiscovery. عندما يعرض المستخدم حالة معينة، يتضمن سجل التدقيق هوية الحالة التي تم عرضها. إذا عرض المستخدم قائمة حالات فقط، فإن سجل التدقيق لا يحتوي على هوية حالة.|
|(none)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|يتم تسجيل هذا النشاط عندما يعرض المستخدم قائمة بعمليات البحث في المحتوى أو عمليات البحث المقترنة ب حالة eDiscovery الأساسية. يتم تسجيل هذا النشاط أيضا عندما يقوم المستخدم ب عرض بحث محتوى معين أو عرض بحث معين مقترن ب حالة eDiscovery أساسية. عندما يعرض المستخدم عملية بحث معينة، يتضمن سجل التدقيق هوية البحث الذي تم عرضه. إذا عرض المستخدم قائمة عمليات البحث فقط، فإن سجل التدقيق لا يحتوي على هوية بحث.
|(none)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|يتم تسجيل هذا النشاط عندما يعرض المستخدم قائمة إجراءات البحث عن التوافق (مثل عمليات التصدير أو المعاينات أو عمليات الازدحام) أو الإجراءات المقترنة ب حالة eDiscovery الأساسية. يتم تسجيل هذا النشاط أيضا عندما يقوم المستخدم ب عرض إجراء بحث توافق معين (مثل تصدير) أو عرض إجراء معين مقترن ب حالة eDiscovery أساسية. عندما يعرض المستخدم إجراء بحث، يتضمن سجل التدقيق هوية إجراء البحث الذي تم عرضه. إذا عرض المستخدم قائمة إجراءات فقط، فإن سجل التدقيق لا يحتوي على هوية إجراء.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>الخصائص المفصلة لأنشطة eDiscovery

يصف الجدول التالي الخصائص المضمنة في صفحة القائمة المنجلية لنشاط eDiscovery المدرج في نتائج البحث. ويتم أيضا تضمين هذه الخصائص في ملف CSV عند تصدير نتائج البحث في سجل التدقيق. لن يتضمن سجل التدقيق لنشاط eDiscovery كل خاصية مفصلة مدرجة أدناه.
  
> [!TIP]
> عند تصدير نتائج البحث، يحتوي ملف CSV على عمود يسمى **AudtiData**، يحتوي على الخصائص المفصلة الموضحة في الجدول التالي في خاصية متعددة القيم. يمكنك استخدام ميزة Power Query في Excel لتقسيم هذا العمود إلى أعمدة متعددة بحيث يكون لكل خاصية عمودها الخاص. ينم ذلك عن فرز وتصفية واحدة أو أكثر من هذه الخصائص. لمزيد من المعلومات، راجع المقطع "تصدير نتائج البحث إلى ملف" [في البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**الخاصية**|**الوصف**|
|:-----|:-----|
|Case  <br/> |هوية (GUID) حالة eDiscovery التي تم إنشاؤها أو تغييرها أو حذفها.  <br/> |
|ClientApplication  <br/> |أنشطة eDiscovery cmdlet لها قيمة **EMC** لهذه الخاصية. يشير ذلك إلى النشاط الذي تم القيام به باستخدام واجهة المستخدم (GUI) لمركز التوافق أو تشغيل الأمر cmdlet في PowerShell.  <br/> |
|ClientIP  <br/> |عنوان IP للجهاز الذي تم استخدامه عند تسجيل النشاط. يتم عرض عنوان IP بتنسيق عنوان IPv4 أو IPv6.  <br/> |
|ClientRequestId  <br/> | بالنسبة لأنشطة eDiscovery، تكون هذه الخاصية عادة فارغة.  <br/> |
|CmdletVersion  <br/> |رقم الإصدار الخاص بالإصدار الخاص بمركز التوافق الذي يتم تشغيله في مؤسستك.  <br/> |
|CreationTime  <br/> |التاريخ والوقت في "الوقت العالمي المنسق" (UTC) عند اكتمال نشاط eDiscovery.  <br/> |
|EffectiveOrganization  <br/> |اسم مؤسسة Microsoft 365.  <br/> |
|ExchangeLocations  <br/> |يتم Exchange Online علب البريد المضمنة في البحث في المحتوى أو الموضوعة قيد الانتظار في حالة eDiscovery.  <br/> |
|الاستثناءات  <br/> |علب البريد أو مواقع المواقع التي يتم استبعادها من البحث في المحتوى أو الانتظار في حالة eDiscovery.  <br/> |
|ExtendedProperties  <br/> |خصائص إضافية من عملية بحث في المحتوى أو إجراء البحث في المحتوى أو الاستمرار في حالة eDiscovery، مثل كائن GUID ومعا معلمات cmdlet و cmdlet المطابقة التي تم استخدامها عند تنفيذ النشاط.  <br/> |
|الم ID  <br/> |الم ID من إدخال التقرير. يعرف المعرِّف إدخال سجل التدقيق بشكل فريد.  <br/> |
|NonPIIParameters  <br/> |قائمة بالمعلمات (بدون أي قيم) التي تم استخدامها مع الأمر cmdlet المعرف في خاصية العملية. إن المعلمات المدرجة في هذه الخاصية هي نفسها تلك المدرجة في الخاصية Parameters.  <br/> |
|ObjectId  <br/> |GUID أو اسم الكائن (على سبيل المثال، البحث في المحتوى أو حالة eDiscovery الأساسية) التي تم إنشاؤها أو الوصول إليها أو تغييرها أو حذفها بواسطة النشاط المدرج في الخاصية العملية. يتم تعريف هذا الكائن أيضا في عمود العنصر في نتائج البحث في سجل التدقيق.  <br/> |
|ObjectType  <br/> |نوع كائن eDiscovery الذي أنشأه المستخدم أو حذفه أو عدله؛ على سبيل المثال، إجراء البحث في المحتوى (معاينة أو تصدير أو إزالة) أو حالة eDiscovery أو بحث في المحتوى.  <br/> |
|العملية  <br/> |اسم العملية التي تتوافق مع نشاط eDiscovery الذي تم إجراءه.  <br/> |
|OrganizationId  <br/> |GUID الخاص Microsoft 365 مؤسستك.  <br/> |
|المعلمات  <br/> |اسم المعلمات التي تم استخدامها مع الأمر cmdlet المناظر وقيمتها.  <br/> |
|PublicFolderLocations  <br/> |مواقع المجلدات العامة في Exchange Online التي يتم تضمينها في البحث في المحتوى أو التي يتم وضعها قيد الانتظار في حالة eDiscovery.  <br/> |
|استعلام  <br/> |استعلام البحث المقترن بالنشاط، مثل البحث في المحتوى أو قائمة الانتظار المستندة إلى الاستعلام.  <br/> |
|RecordType  <br/> |نوع العملية المشار إليها بواسطة السجل. تشير القيمة **18** إلى حدث مرتبط بنشاط مدرج في قسم أنشطة [eDiscovery cmdlet](#ediscovery-cmdlet-activities) . تشير القيمة **24** إلى حدث مرتبط بنشاط مدرج في القسم كيفية البحث عن أنشطة [eDiscovery وعرضها](#how-to-search-for-and-view-ediscovery-activities) .  <br/> |
|ResultStatus  <br/> |تشير إلى ما إذا كان الإجراء (المحدد في خاصية العملية) قد نجح أم لا.  <br/> |
|SecurityComplianceCenterEventType  <br/> |تشير إلى أن النشاط كان حدثا لمركز التوافق. سيكون لكل أنشطة eDiscovery قيمة **0** لهذه الخاصية.  <br/> |
|SharepointLocations  <br/> |يتم SharePoint المواقع عبر الإنترنت المضمنة في البحث في المحتوى أو التي تم وضعها قيد الانتظار في حالة eDiscovery.  <br/> |
|StartTime  <br/> |التاريخ والوقت في "الوقت العالمي المنسق" (UTC) عند بدء نشاط eDiscovery.  <br/> |
|UserId  <br/> |المستخدم الذي قام بتنفيذ النشاط (المحدد في خاصية العملية) الذي أدى إلى تسجيل السجل. يتم أيضا تضمين سجلات نشاط eDiscovery التي يتم تنفيذها بواسطة حسابات النظام (مثل NT AUTHORITY\SYSTEM) في سجل التدقيق.  <br/> |
|UserKey  <br/> |معرف بديل للمستخدم المعرف في الخاصية UserId. بالنسبة لأنشطة eDiscovery، تكون قيمة هذه الخاصية عادة نفس خاصية UserId.  <br/> |
|UserServicePlan  <br/> |الاشتراك المستخدم من قبل مؤسستك. بالنسبة لأنشطة eDiscovery، تكون هذه الخاصية عادة فارغة.  <br/> |
|UserType  <br/> |نوع المستخدم الذي قام بتنفيذ العملية. تشير القيم التالية إلى نوع المستخدم.  <br/> 0 مستخدم عادي. 2 مسؤول في مؤسستك. 3 مسؤول مركز بيانات Microsoft أو حساب نظام مركز البيانات. 4 حساب النظام. 5 تطبيق. 6 A الخدمة الأساسية. |
|الإصدار  <br/> |تشير إلى رقم إصدار النشاط (المعرف بواسطة خاصية العملية) الذي تم تسجيله.  <br/> |
|حمل العمل  <br/> |الخدمة التي حدث فيها النشاط. بالنسبة لأنشطة eDiscovery، تكون القيمة **SecurityComplianceCenter**.  <br/> |
