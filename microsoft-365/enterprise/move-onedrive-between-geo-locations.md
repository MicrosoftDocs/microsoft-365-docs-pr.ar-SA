---
title: نقل موقع OneDrive إلى موقع جغرافي آخر
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: يمكنك العثور على معلومات حول OneDrive موقع ويب إلى موقع جغرافي آخر، بما في ذلك كيفية جدولة نقل الموقع وإعلام المستخدمين بتوقعاتهم.
ms.openlocfilehash: f0a9e319d20c7b56701d776e85a0618ed30e5f78
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569590"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>نقل موقع OneDrive إلى موقع جغرافي آخر

باستخدام OneDrive الجغرافي، يمكنك نقل موقع OneDrive إلى موقع جغرافي آخر. OneDrive التنقل الجغرافي بواسطة SharePoint Online أو المسؤول Microsoft 365 العام. قبل بدء عملية نقل OneDrive الجغرافي، تأكد من إعلام المستخدم الذي OneDrive نقله ويوصيه بغلق كل الملفات طوال مدة الانتقال. (إذا كان لدى المستخدم مستند مفتوح باستخدام عميل Office أثناء عملية الانتقال، يجب حفظ المستند في الموقع الجديد عند اكتمال عملية الانتقال.) يمكن جدولة عملية الانتقال في وقت مستقبلي، إذا أردت ذلك.

تستخدم OneDrive الخدمة Azure Blob Storage لتخزين المحتوى. سيتم نقل مساحة التخزين blob المقترنة بمساحة التخزين OneDrive المستخدم من الموقع الجغرافي المصدر إلى الموقع الجغرافي الوجهة في غضون 40 يوما من OneDrive تكون متوفرة للمستخدم. سيتم استعادة الوصول إلى OneDrive المستخدم بمجرد توفر OneDrive الوجهة.

أثناء OneDrive التنقل الجغرافي (حوالي ساعتين إلى 6 ساعات) يتم تعيين OneDrive المستخدم للقراءة فقط. لا يزال يمكن للمستخدم الوصول إلى ملفاته عبر المزامنة من OneDrive أو موقع OneDrive في SharePoint Online. بعد OneDrive نقل الموقع الجغرافي، سيتم توصيل المستخدم تلقائيا ب OneDrive في الموقع الجغرافي الوجهة عند الانتقال إلى OneDrive في Microsoft 365 التطبيق. سيبدأ تطبيق المزامنة تلقائيا في المزامنة من الموقع الجديد.

تتطلب الإجراءات في هذه المقالة Microsoft Office SharePoint Online [PowerShell النمطية](https://www.microsoft.com/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>التواصل مع المستخدمين

عند نقل OneDrive بين المواقع الجغرافية، من المهم توصيل المستخدمين بما يجب توقعه. يمكن أن يساعد ذلك على تقليل ارتباك المستخدمين والمكالمات إلى مكتب المساعدة. أرسل بريدا إلكترونيا إلى المستخدمين قبل الانتقال واعلمهم بالمعلومات التالية:

- متى من المتوقع أن يبدأ الانتقال والمهى المتوقع أن يستغرقه
- الموقع الجغرافي الذي OneDrive الانتقال إليه، وعنوان URL للوصول إلى الموقع الجديد
- يجب عليهم إغلاق ملفاتهم وليس إجراء عمليات تحرير أثناء التنقل.
- لن تتغير أذونات الملف والمشاركة نتيجة للنقل.
- ما يجب توقعه من [تجربة المستخدم في بيئة متعددة الجغرافيا](multi-geo-user-experience.md)

تأكد من إرسال بريد إلكتروني للمستخدمين عند اكتمال عملية الانتقال بنجاح لإعلامهم بأنه يمكنهم استئناف العمل في OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>جدولة OneDrive الموقع

يمكنك جدولة OneDrive الموقع مسبقا (كما هو موضح لاحقا في هذه المقالة). نوصيك بالبدء بعدد صغير من المستخدمين للتحقق من صحة مهام سير العمل وإستراتيجيات الاتصال. بمجرد أن تطمئن إلى العملية، يمكنك جدولة التحركات كما يلي:

- يمكنك جدولة ما يصل إلى 4000 حركة نقل في كل مرة.
- مع بدء الانتقالات، يمكنك جدولة المزيد، بحد أقصى 4000 حركة نقل معلقة في قائمة الانتظار وفي أي وقت معين.
- الحد الأقصى لحجم OneDrive التي يمكن نقلها هو تيرابايت واحد (1 تيرابايت).

## <a name="moving-a-onedrive-site"></a>نقل موقع OneDrive ويب

لتنفيذ عملية نقل OneDrive الجغرافي، يجب على مسؤول المستأجر أولا تعيين موقع البيانات المفضلة (PDL) للمستخدم إلى الموقع الجغرافي المناسب. بعد تعيين PDL، انتظر لمدة 24 ساعة على الأقل حتى تتم مزامنة تحديث PDL عبر المواقع الجغرافية قبل بدء OneDrive الجغرافي.

عند استخدام cmdlets الخاصة بالنقل الجغرافي، اتصل ب SPO Service في الموقع الجغرافي OneDrive الحالي للمستخدم، باستخدام بناء الجملة التالي:

```powershell
Connect-SPOService -url https://<tenantName>-admin.sharepoint.com
```

على سبيل المثال: لنقل OneDrive المستخدم "Matt@contosoenergy.onmicrosoft.com"، اتصل بمركز إدارة SHAREPOINT يورو حيث يوجد موقع المستخدم OneDrive الجغرافي لليورو:

```powershell
Connect-SPOService -url https://contosoenergyeur-admin.sharepoint.com
```

![لقطة شاشة من نافذة PowerShell تعرض الأمر cmdlet للاتصال ب sposervice.](../media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>التحقق من صحة البيئة

قبل بدء عملية نقل OneDrive الجغرافي، نوصي بالتحقق من صحة البيئة.

للتأكد من توافق كل المواقع الجغرافية، تشغيل:

```powershell
Get-SPOGeoMoveCrossCompatibilityStatus
```

سترى قائمة بالمواقع الجغرافية الخاصة بك وما إذا كان يمكن نقل المحتوى بين سيتم توضيحها ب "متوافق". إذا كان الأمر يرجع "غير متوافق"، فيرجى إعادة محاولة التحقق من صحة الحالة في وقت لاحق.

إذا احتوى OneDrive على الموقع الفرعي، على سبيل المثال، فلا يمكن نقله. يمكنك استخدام الأمر cmdlet Start-SPOUserAndContentMove مع المعلمة -ValidationOnly للتحقق من OneDrive يمكن نقله:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly
```

سيرجع هذا الأمر النجاح إذا كانت OneDrive جاهزة للتحريك أو فشل إذا كان هناك عقد قانوني أو مكان فرعي قد يمنع عملية الانتقال. بعد التحقق من أن OneDrive جاهزا للتحريك، يمكنك بدء عملية الانتقال.

## <a name="start-a-onedrive-geo-move"></a>بدء حركة OneDrive الجغرافي

لبدء عملية الانتقال، يمكنك تشغيل:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>
```

باستخدام هذه المعلمات:

- _UserPrincipalName_ – UPN للمستخدم الذي OneDrive نقله.
- _DestinationDataLocation_ – Geo-Location المكان الذي OneDrive نقله. يجب أن يكون هذا هو موقع البيانات المفضل للمستخدم.

على سبيل المثال، لنقل OneDrive matt@contosoenergy.onmicrosoft.com من اليورو إلى AUS، تشغيل:

```powershell
Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS
```

![لقطة شاشة من نافذة PowerShell تظهر Start-SPOUserAndContentMove cmdlet.](../media/move-onedrive-between-geo-locations-image2.png)

لجدولة حركة نقل جغرافي لفترة لاحقة، استخدم إحدى المعلمات التالية:

- _المفضلةMoveBeginDate_ – من المرجح أن يبدأ الانتقال في هذا الوقت المحدد. يجب تحديد الوقت في "الوقت العالمي المنسق" (UTC).
- _BestedMoveEndDate_ – من المرجح أن تكتمل عملية الانتقال بحلول هذا الوقت المحدد، على أساس أفضل جهد. يجب تحديد الوقت في "الوقت العالمي المنسق" (UTC).

## <a name="cancel-a-onedrive-geo-move"></a>إلغاء OneDrive جغرافي

يمكنك إيقاف الانتقال الجغرافي لمحتوى OneDrive المستخدم، شرط ألا يكون الانتقال في تقدم أو مكتمل باستخدام أمر cmdlet:

```powershell
Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>
```

حيث _UserPrincipalName_ هو UPN للمستخدم الذي OneDrive تريد إيقافه.

## <a name="determining-current-status"></a>تحديد الحالة الحالية

يمكنك التحقق من حالة OneDrive الجغرافي للتنقل داخل الموقع الجغرافي المتصل به أو خارجه باستخدام Get-SPOUserAndContentMoveState cmdlet.

يتم وصف حالة الانتقال في الجدول التالي.

|الحالة|الوصف|
|---|---|
|NotStarted|لم يبدأ الانتقال|
|InProgress (*n*/4)|يتم التقدم في عملية الانتقال في إحدى الحالات التالية: <ul><li>التحقق من الصحة (1/4)</li><li>النسخ الاحتياطي (2/4)</li><li>استعادة (3/4)</li><li>التنظيف (4/4)</li></ul>|
|النجاح|اكتملت عملية الانتقال بنجاح.|
|فشل|فشل الانتقال.|

للعثور على حالة نقل مستخدم معين، استخدم المعلمة *UserPrincipalName* :

```powershell
Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>
```

للعثور على حالة كل التنقلات داخل الموقع الجغرافي المتصل به أو الخروج منه، استخدم المعلمة *MoveState* مع إحدى القيم التالية: NotStarted و InProgress و Success و Failed و All.

```powershell
Get-SPOUserAndContentMoveState -MoveState <value>
```

يمكنك أيضا إضافة المعلمة *"إسهاب* " للحصول على أوصاف أكثر إسهاب حالة الانتقال.

## <a name="user-experience"></a>أسلوب عمل المستخدم

يجب أن يلاحظ مستخدمو OneDrive حدوث أقل قدر من الانقطاع إذا OneDrive نقلهم إلى موقع جغرافي آخر. إلى جانب حالة القراءة فقط الموجزة أثناء النقل، ستستمر الارتباطات والأذونات الموجودة في العمل كما هو متوقع بمجرد اكتمال النقل.

### <a name="users-onedrive"></a>بيانات المستخدم OneDrive

أثناء تقدم عملية الانتقال، يتم تعيين OneDrive المستخدم للقراءة فقط. بمجرد اكتمال عملية الانتقال، يتم توجيه المستخدم إلى موقعه الجغرافي الجديد OneDrive عندما ينتقل إلى OneDrive Microsoft 365 أو مستعرض ويب.

### <a name="permissions-on-onedrive-content"></a>الأذونات على OneDrive المحتويات

سيستمر المستخدمون الذين لديهم OneDrive الوصول إلى المحتوى في الوصول إلى المحتوى أثناء عملية الانتقال وبعد اكتماله.

### <a name="onedrive-sync-app"></a>المزامنة من OneDrive التطبيق

سيكشف المزامنة من OneDrive التطبيق المزامنة وينقلها تلقائيا إلى موقع OneDrive الجديد بمجرد OneDrive التنقل الجغرافي. لا يحتاج المستخدم إلى تسجيل الدخول مرة أخرى أو اتخاذ أي إجراء آخر.  (الإصدار 17.3.6943.0625 أو إصدار أحدث من تطبيق المزامنة مطلوب.)

إذا قام أحد المستخدمين بتحديث ملف أثناء OneDrive الجغرافي، سيعلمه تطبيق المزامنة بأن تحميلات الملفات معلقة أثناء عملية الانتقال.

### <a name="sharing-links"></a>ارتباطات المشاركة

عند OneDrive النقل الجغرافي، سيتم تلقائيا إعادة توجيه الارتباطات المشتركة الموجودة للملفات التي تم نقلها إلى الموقع الجغرافي الجديد.

### <a name="onenote-experience"></a>OneNote تجربة المستخدم

OneNote عميل win32 والتطبيق UWP (Universal) الكشف تلقائيا عن دفاتر الملاحظات ومزامنتها بسلاسة مع موقع OneDrive الجديد بمجرد OneDrive الجغرافيا. لا يحتاج المستخدم إلى تسجيل الدخول مرة أخرى أو اتخاذ أي إجراء آخر. المؤشر المرئي الوحيد للمستخدم هو أن مزامنة دفتر الملاحظات ستفشل عند OneDrive التنقل الجغرافي قيد التقدم. تتوفر هذه التجربة على الإصدارات التالية OneNote العميل:

- OneNote win32 – الإصدار 16.0.8326.2096 (والإصدارات الأحدث)
- OneNote UWP – الإصدار 16.0.8431.1006 (والإصدارات الأحدث)
- OneNote Mobile App – الإصدار 16.0.8431.1011 (والإصدارات الأحدث)

### <a name="teams-app"></a>Teams التطبيق

عند OneDrive نقل الموقع الجغرافي، سيكون للمستخدمين حق الوصول إلى ملفاتهم OneDrive على Teams. بالإضافة إلى ذلك، فإن الملفات التي تمت مشاركتها Teams الدردشة من OneDrive قبل الانتقال الجغرافي ستستمر في العمل بعد اكتمال عملية التنقل.

### <a name="onedrive-mobile-app-ios"></a>OneDrive Mobile App (iOS)

عند OneDrive نقل الموقع الجغرافي، يحتاج المستخدم إلى تسجيل الخروج ثم تسجيل الدخول مرة أخرى على تطبيق iOS Mobile للمزامنة مع موقع OneDrive الجديد.

### <a name="existing-followed-groups-and-sites"></a>المجموعات والمواقع الموجودة والمتابعة

سوف تظهر المواقع والمجموعات المتابعة في موقع OneDrive بغض النظر عن موقعها الجغرافي. سيتم فتح المواقع والمجموعات المستضافة في موقع جغرافي آخر في علامة تبويب منفصلة.

### <a name="delve-geo-url-updates"></a>Delve URL الجغرافية

سيتم إرسال المستخدمين إلى Delve الجغرافي المطابق ل PDL فقط بعد نقل OneDrive إلى الموقع الجغرافي الجديد.
