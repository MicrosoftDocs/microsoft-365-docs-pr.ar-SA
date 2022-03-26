---
title: نقل موقع SharePoint إلى موقع جغرافي آخر
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: تعرف على كيفية نقل موقع SharePoint إلى موقع جغرافي آخر ضمن بيئتك الجغرافية المتعددة وتوقعات التغييرات التي يتم إدخالها على المستخدمين.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9e4132b8399cc69067d24af6c3c9ec8e3baf52bd
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63568940"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>نقل موقع SharePoint إلى موقع جغرافي آخر

باستخدام SharePoint الجغرافي للموقع، يمكنك نقل مواقع SharePoint إلى مواقع جغرافية أخرى ضمن بيئتك الجغرافية المتعددة.

يمكن نقل الأنواع التالية من المواقع بين المواقع الجغرافية:

- Microsoft 365 المتصلة بالمجموعة، بما في ذلك تلك المواقع المقترنة Microsoft Teams
- المواقع الحديثة التي لا Microsoft 365 اقتران مجموعة
- مواقع SharePoint الكلاسيكية
- مواقع الاتصالات

يجب أن تكون مسؤولا SharePoint أو مسؤولا لنقل موقع بين المواقع الجغرافية.

توجد نافذة للقراءة فقط أثناء SharePoint الجغرافي لموقع ويب لمدة 4-6 ساعات تقريبا، استنادا إلى محتويات الموقع.

## <a name="best-practices"></a>أفضل الممارسات

- جرب SharePoint موقع ويب على موقع اختبار للإلمام بالإجراء.
- تحقق من صحة ما إذا كان يمكن نقل الموقع قبل جدولة أو تنفيذ عملية الانتقال.
- عندما يكون من الممكن جدولة نقل المواقع الجغرافية الخارجية لساعات العمل الخارجية لتقليل تأثير المستخدم.
- التواصل مع المستخدمين ذوي التأثير قبل نقل المواقع.

## <a name="communicating-to-your-users"></a>التواصل مع المستخدمين

عند نقل SharePoint بين المواقع الجغرافية، من المهم التواصل مع مستخدمي المواقع (بشكل عام أي شخص لديه القدرة على تحرير الموقع) بما يمكن توقعه. يمكن أن يساعد ذلك على تقليل ارتباك المستخدمين والمكالمات إلى مكتب المساعدة. أرسل بريدا إلكترونيا إلى مستخدمي مواقعك قبل الانتقال واعلمهم بالمعلومات التالية:

- متى من المتوقع أن يبدأ الانتقال والمهى المتوقع أن يستغرقه
- الموقع الجغرافي الذي ينتقل إليه الموقع، وعنوان URL للوصول إلى الموقع الجديد
- يجب عليهم إغلاق ملفاتهم وليس إجراء عمليات تحرير أثناء التنقل.
- لن تتغير أذونات الملف والمشاركة بسبب الانتقال.
- ما يجب توقعه من تجربة المستخدم في بيئة متعددة الجغرافيا

تأكد من إرسال بريد إلكتروني إلى مستخدمي مواقعك عند اكتمال عملية الانتقال لإعلامهم بأنه يمكنهم استئناف العمل على مواقعهم.

## <a name="scheduling-sharepoint-site-moves"></a>جدولة SharePoint الموقع

يمكنك جدولة SharePoint الموقع بشكل مسبق (كما هو موضح لاحقا في هذه المقالة). يمكنك جدولة التحركات كما يلي:

- يمكنك جدولة ما يصل إلى 4000 حركة نقل في كل مرة.
- مع بدء الانتقالات، يمكنك جدولة المزيد، بحد أقصى 4000 حركة نقل معلقة في قائمة الانتظار وفي أي وقت معين.
- الحد الأقصى لحجم موقع SharePoint يمكن نقله هو 1 تيرابايت (1 تيرابايت).

لجدولة حركة SharePoint الموقع الجغرافي لفترة لاحقة، قم بتضمين إحدى المعلمات التالية عند بدء عملية الانتقال:

- `PreferredMoveBeginDate` – من المرجح أن يبدأ الانتقال في هذا الوقت المحدد.
- `PreferredMoveEndDate` – من المرجح أن تكتمل عملية الانتقال بحلول هذا الوقت المحدد، على أساس أفضل جهد.

يجب تحديد الوقت في الوقت العالمي المنسق (UTC) للمعلمتين.

## <a name="moving-the-site"></a>نقل الموقع

SharePoint نقل الموقع الجغرافي إلى الاتصال بتنفيذ عملية الانتقال من عنوان URL للمسؤول SharePoint في الموقع الجغرافي حيث يوجد الموقع.

على سبيل المثال، إذا كان عنوان URL للموقع هو <https://contosohealthcare.sharepoint.com/sites/Turbines>، فاتصل SharePoint URL للمسؤول في <https://contosohealthcare-admin.sharepoint.com>:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![SharePoint نافذة Online Management Shell التي تعرض Connect-SPOService الأوامر.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>التحقق من صحة البيئة

نوصي بإجراء عملية التحقق من الصحة قبل جدولة أي نقل موقع للتأكد من أنه يمكن نقل الموقع.

لا ندعم نقل المواقع باستخدام:

- Business Connectivity Services
- نماذج InfoPath
- قوالب إدارة حقوق استخدام المعلومات (IRM) المطبقة

للتأكد من توافق كل المواقع الجغرافية، تشغيل `Get-SPOGeoMoveCrossCompatibilityStatus`. سيعرض هذا كل المواقع الجغرافية وما إذا كانت البيئة متوافقة مع الموقع الجغرافي الوجهة.

لإجراء التحقق من الصحة `Start-SPOSiteContentMove` `-ValidationOnly` فقط على موقعك، استخدم مع المعلمة للتحقق مما إذا كان الموقع قادرا على نقله. على سبيل المثال:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

سيرجع هذا *الأمر النجاح* إذا كان الموقع جاهزا لنقله أو فشله في حالة وجود أي من الشروط المحظورة.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>بدء نقل SharePoint موقع جغرافي لموقع بدون Microsoft 365 مقترن

بشكل افتراضي، سيتغير URL الأولي للموقع إلى عنوان URL للموقع الجغرافي الوجهة. على سبيل المثال:

<https://Contoso.sharepoint.com/sites/projectx> إلى <https://ContosoEUR.sharepoint.com/sites/projectx>

بالنسبة للمواقع التي لا Microsoft 365 مجموعة، يمكنك أيضا إعادة تسمية الموقع باستخدام المعلمة`-DestinationUrl`. على سبيل المثال:

<https://Contoso.sharepoint.com/sites/projectx> إلى <https://ContosoEUR.sharepoint.com/sites/projecty>

لبدء نقل الموقع، يمكنك تشغيل:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![لقطة شاشة من نافذة PowerShell تظهر Start-SPOSiteContentMove cmdlet.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>بدء SharePoint موقع جغرافي لموقع Microsoft 365 متصل بالمجموعة

لنقل موقع Microsoft 365 متصل بالمجموعة، يجب على المسؤول العام أو المسؤول SharePoint أولا تغيير السمة موقع البيانات المفضلة (PDL) لمجموعة Microsoft 365.

لتعيين PDL لمجموعة Microsoft 365:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

بعد تحديث PDL، يمكنك بدء نقل الموقع:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>إلغاء نقل موقع SharePoint الجغرافي

يمكنك إيقاف SharePoint الموقع الجغرافي، شرط ألا يكون الانتقال في تقدم أو مكتمل باستخدام `Stop-SPOSiteContentMove` cmdlet.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>تحديد حالة حركة نقل موقع SharePoint الجغرافي

يمكنك تحديد حالة نقل موقع خارج الموقع الجغرافي الذي تتصل به باستخدام cmdlets التالية:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (مواقع غير متصلة بالمجموعة)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (المواقع المتصلة بالمجموعة)

استخدم المعلمة `-SourceSiteUrl` لتحديد الموقع الذي تريد رؤية حالة نقله.

يتم وصف حالة الانتقال في الجدول التالي.

****

|الحالة|الوصف|
|---|---|
|جاهز للتحريك|لم يبدأ الانتقال.|
|مجدول|الانتقال في قائمة الانتظار ولكن لم يبدأ بعد.|
|InProgress (n/4)|يتم الآن نقل البيانات في إحدى الحالات التالية: التحقق من الصحة (1/4) ونظيف (2/4) والاستعادة (3/4) والتنظيف (4/4).|
|النجاح|اكتملت عملية الانتقال بنجاح.|
|فشل|فشل الانتقال.|
|

يمكنك أيضا تطبيق الخيار `-Verbose` لرؤية معلومات إضافية حول عملية الانتقال.

## <a name="user-experience"></a>تجربة المستخدم

يجب أن يلاحظ مستخدمو الموقع أقل قدر من الانقطاع عند نقل موقعهم إلى موقع جغرافي آخر. إلى جانب حالة القراءة فقط الموجزة أثناء النقل، ستستمر الارتباطات والأذونات الموجودة في العمل كما هو متوقع بمجرد اكتمال النقل.

### <a name="site"></a>الموقع

أثناء تقدم عملية الانتقال، يتم تعيين الموقع إلى للقراءة فقط. بمجرد اكتمال النقل، يتم توجيه المستخدم إلى الموقع الجديد في الموقع الجغرافي الجديد عند النقر فوق الإشارات المرجعية أو الارتباطات الأخرى إلى الموقع.

### <a name="permissions"></a>الأذونات

سيستمر المستخدمون الذين لديهم أذونات للوصول إلى الموقع في الوصول إلى الموقع أثناء عملية الانتقال وبعد اكتماله.

### <a name="sync-app"></a>تطبيق المزامنة

سيكشف تطبيق المزامنة المزامنة وينقلها تلقائيا إلى موقع الموقع الجديد بمجرد اكتمال عملية نقل الموقع. لا يحتاج المستخدم إلى تسجيل الدخول مرة أخرى أو اتخاذ أي إجراء آخر. (الإصدار 17.3.6943.0625 أو إصدار أحدث من تطبيق المزامنة مطلوب.)

إذا قام أحد المستخدمين بتحديث ملف أثناء تقدم عملية الانتقال، سيعلمه تطبيق المزامنة بأن تحميلات الملفات معلقة أثناء الانتقال.

### <a name="sharing-links"></a>ارتباطات المشاركة

عند اكتمال SharePoint الجغرافي للموقع، سيتم تلقائيا إعادة توجيه الارتباطات المشتركة الموجودة للملفات التي تم نقلها إلى الموقع الجغرافي الجديد.

### <a name="most-recently-used-files-in-office-mru"></a>أحدث الملفات المستخدمة في Office (MRU)

يتم تحديث خدمة MRU باستخدام عنوان url للموقع ومحتوياته عناوين URL بمجرد اكتمال عملية الانتقال. ينطبق هذا الأمر على Word Excel و PowerPoint.

### <a name="onenote-experience"></a>OneNote العمل

OneNote عميل win32 والتطبيق UWP (Universal) الكشف تلقائيا عن دفاتر الملاحظات ومزامنتها بسلاسة مع موقع الموقع الجديد بمجرد اكتمال نقل الموقع. لا يحتاج المستخدم إلى تسجيل الدخول مرة أخرى أو اتخاذ أي إجراء آخر. المؤشر المرئي الوحيد للمستخدم هو أن مزامنة دفتر الملاحظات ستفشل عندما يكون نقل الموقع قيد التقدم. تتوفر هذه التجربة على الإصدارات التالية OneNote العميل:

- OneNote win32 – الإصدار 16.0.8326.2096 (والإصدارات الأحدث)
- OneNote UWP – الإصدار 16.0.8431.1006 (والإصدارات الأحدث)
- OneNote Mobile App – الإصدار 16.0.8431.1011 (والإصدارات الأحدث)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (ينطبق على Microsoft 365 المتصلة بالمجموعة)

عند اكتمال SharePoint الموقع الجغرافي، سيكون لدى المستخدمين حق الوصول إلى Microsoft 365 موقع المجموعة على Teams التطبيق. بالإضافة إلى ذلك، ستستمر الملفات Teams المشتركة عبر الدردشة من موقعها قبل الانتقال الجغرافي في العمل بعد اكتمال عملية التنقل.

SharePoint الموقع الجغرافي نقل القنوات الخاصة من موقع جغرافي إلى آخر. تظل القنوات الخاصة في الموقع الجغرافي الأصلي.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint Mobile App (iOS/Android)

إن SharePoint Mobile App متوافق مع الموقع الجغرافي وقادر على الكشف عن الموقع الجغرافي الجديد.

### <a name="sharepoint-workflows"></a>SharePoint سير العمل

SharePoint إعادة نشر مهام سير العمل في 2013 بعد نقل الموقع. SharePoint مهام سير العمل في 2010 أن تستمر في العمل بشكل طبيعي.

### <a name="apps"></a>التطبيقات

إذا كنت تنقل موقع يحتوي على تطبيقات، فيجب إعادة تثبيت التطبيق في الموقع الجغرافي الجديد للموقع حيث قد لا يتوفر التطبيق واتصالاته في الموقع الجغرافي الوجهة.

### <a name="flow"></a>Flow

في معظم الحالات، سيستمر عمل التدفقات بعد SharePoint الموقع الجغرافي. نوصي باختبارها بمجرد اكتمال عملية الانتقال.

### <a name="power-apps"></a>تطبيقات الطاقة

يجب إعادة إنشاء تطبيقات Power في موقع الوجهة.

### <a name="data-movement-between-geo-locations"></a>حركة البيانات بين المواقع الجغرافية

SharePoint تخزين Azure Blob لمحتواه، بينما يتم تخزين بيانات التعريف المقترنة بالمواقع وملفاتها ضمن SharePoint. بعد نقل الموقع من موقعه الجغرافي المصدر إلى موقعه الجغرافي الوجهة، تنقل الخدمة أيضا مساحة تخزين Blob المقترنة بها. سيكتمل نقل مساحة تخزين Blob في غضون 40 يوما تقريبا.
