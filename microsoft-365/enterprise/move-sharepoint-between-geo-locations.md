---
title: نقل موقع SharePoint إلى موقع جغرافي مختلف
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
description: تعرف على كيفية نقل موقع SharePoint إلى موقع جغرافي مختلف داخل بيئتك متعددة المناطق الجغرافية وإبلاغ المستخدمين بتوقعات التغييرات.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0b388b3fa869e6207c72f62aa2f50b832acab43a
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940811"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>نقل موقع SharePoint إلى موقع جغرافي مختلف

باستخدام النقل الجغرافي لموقع SharePoint، يمكنك نقل مواقع SharePoint إلى مواقع جغرافية أخرى داخل بيئتك متعددة المناطق الجغرافية.

يمكن نقل الأنواع التالية من المواقع بين المواقع الجغرافية:

- المواقع المتصلة بمجموعة Microsoft 365، بما في ذلك تلك المواقع المقترنة ب Microsoft Teams
- المواقع الحديثة بدون اقتران مجموعة Microsoft 365
- مواقع SharePoint الكلاسيكية
- مواقع الاتصالات

يجب أن تكون مسؤولا عاما أو مسؤول SharePoint لنقل موقع بين المواقع الجغرافية.

توجد نافذة للقراءة فقط أثناء النقل الجغرافي لموقع SharePoint لمدة 4-6 ساعات تقريبا، استنادا إلى محتويات الموقع.

## <a name="best-practices"></a>أفضل الممارسات

- جرب نقل موقع SharePoint على موقع اختبار للتعرف على الإجراء.
- التحقق من إمكانية نقل الموقع قبل جدولة النقل أو تنفيذه.
- عندما ينتقل الجدول المحتمل عبر المواقع الجغرافية إلى ساعات العمل الخارجية لتقليل تأثير المستخدم.
- تواصل مع المستخدمين المتأثرين قبل نقل المواقع.

## <a name="communicating-to-your-users"></a>التواصل مع المستخدمين

عند نقل مواقع SharePoint بين المواقع الجغرافية، من المهم توصيل ما يمكن توقعه لمستخدمي المواقع (أي شخص لديه القدرة على تحرير الموقع بشكل عام). يمكن أن يساعد هذا في تقليل ارتباك المستخدم والمكالمات إلى مكتب المساعدة. أرسل بريدا إلكترونيا لمستخدمي مواقعك قبل النقل وقم بإعلامهم بالمعلومات التالية:

- متى من المتوقع بدء النقل والمدة التي من المتوقع أن تستغرقها
- الموقع الجغرافي الذي ينتقل إليه موقعه، وعنوان URL للوصول إلى الموقع الجديد
- يجب إغلاق ملفاتهم وعدم إجراء عمليات تحرير أثناء النقل.
- لن تتغير أذونات الملف والمشاركة بسبب النقل.
- ما يجب توقعه من تجربة المستخدم في بيئة متعددة المناطق الجغرافية

تأكد من إرسال بريد إلكتروني لمستخدمي مواقعك عندما تكتمل عملية النقل بنجاح لإعلامهم بأنه يمكنهم استئناف العمل على مواقعهم.

## <a name="scheduling-sharepoint-site-moves"></a>جدولة نقلات موقع SharePoint

يمكنك جدولة تنقلات موقع SharePoint مسبقا (كما هو موضح لاحقا في هذه المقالة). يمكنك جدولة عمليات النقل كما يلي:

- يمكنك جدولة ما يصل إلى 4000 عملية نقل في كل مرة.
- مع بدء الحركات، يمكنك جدولة المزيد، بحد أقصى 4000 عملية نقل معلقة في قائمة الانتظار وأي وقت معين.
- الحد الأقصى لحجم موقع SharePoint الذي يمكن نقله هو 1 تيرابايت (1 تيرابايت).

لجدولة نقل جغرافي لموقع SharePoint لوقت لاحق، قم بتضمين إحدى المعلمات التالية عند بدء النقل:

- `PreferredMoveBeginDate` – من المحتمل أن تبدأ عملية النقل في هذا الوقت المحدد.
- `PreferredMoveEndDate` – من المحتمل أن تكتمل هذه الخطوة بحلول هذا الوقت المحدد، على أساس أفضل جهد.

يجب تحديد الوقت في التوقيت العالمي المتفق عليه (UTC) لكلتا المعلمتين.

## <a name="moving-the-site"></a>نقل الموقع

يتطلب النقل الجغرافي لموقع SharePoint الاتصال بالنقل وتنفيذه من عنوان URL لمسؤول SharePoint في الموقع الجغرافي حيث يوجد الموقع.

على سبيل المثال، إذا كان URL الموقع، `https://contosohealthcare.sharepoint.com/sites/Turbines`فتواصل مع URL مسؤول SharePoint على `https://contosohealthcare-admin.sharepoint.com`:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

![تعرض نافذة SharePoint Online Management Shell الأمر Connect-SPOService.](../media/move-onedrive-between-geo-locations-image1.png)

### <a name="validating-the-environment"></a>التحقق من صحة البيئة

نوصي بإجراء التحقق من الصحة قبل جدولة أي نقل موقع للتأكد من إمكانية نقل الموقع.

لا ندعم نقل المواقع باستخدام:

- Business Connectivity Services
- نماذج InfoPath
- قوالب إدارة حقوق استخدام المعلومات (IRM) المطبقة

للتأكد من توافق جميع المواقع الجغرافية، قم بتشغيل `Get-SPOGeoMoveCrossCompatibilityStatus`. سيؤدي ذلك إلى عرض جميع المواقع الجغرافية الخاصة بك وما إذا كانت البيئة متوافقة مع الموقع الجغرافي الوجهة.

لإجراء التحقق من الصحة فقط على موقعك، استخدمها `Start-SPOSiteContentMove` مع `-ValidationOnly` المعلمة للتحقق من إمكانية نقل الموقع. على سبيل المثال:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

سيؤدي ذلك إلى إرجاع *Success* إذا كان الموقع جاهزا ليتم نقله أو *فشله* في حالة وجود أي من الشروط المحظورة.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-microsoft-365-group"></a>بدء نقل جغرافي لموقع SharePoint لموقع لا يحتوي على مجموعة Microsoft 365 مقترنة

بشكل افتراضي، سيتغير URL الأولي للموقع إلى عنوان URL للموقع الجغرافي الوجهة. على سبيل المثال:

`https://Contoso.sharepoint.com/sites/projectx` ل `https://ContosoEUR.sharepoint.com/sites/projectx`

بالنسبة للمواقع التي لا تحتوي على اقتران مجموعة Microsoft 365، يمكنك أيضا إعادة تسمية الموقع باستخدام المعلمة `-DestinationUrl` . على سبيل المثال:

<https://Contoso.sharepoint.com/sites/projectx> ل `https://ContosoEUR.sharepoint.com/sites/projecty`

لبدء نقل الموقع، قم بتشغيل:

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

![لقطة شاشة لنافذة PowerShell تعرض Start-SPOSiteContentMove cmdlet.](../media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-a-microsoft-365-group-connected-site"></a>بدء نقل جغرافي لموقع SharePoint لموقع متصل بمجموعة Microsoft 365

لنقل موقع متصل بمجموعة Microsoft 365، يجب أولا على المسؤول العام أو مسؤول SharePoint تغيير سمة موقع البيانات المفضل (PDL) لمجموعة Microsoft 365.

لتعيين PDL لمجموعة Microsoft 365:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

بمجرد تحديث PDL، يمكنك بدء نقل الموقع:

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>إلغاء النقل الجغرافي لموقع SharePoint

يمكنك إيقاف النقل الجغرافي لموقع SharePoint، شريطة ألا تكون عملية النقل قيد التقدم أو مكتملة `Stop-SPOSiteContentMove` باستخدام cmdlet.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>تحديد حالة النقل الجغرافي لموقع SharePoint

يمكنك تحديد حالة نقل الموقع في خارج المنطقة الجغرافية التي تتصل بها باستخدام أوامر cmdlet التالية:

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (مواقع غير متصلة بالمجموعة)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (المواقع المتصلة بالمجموعة)

استخدم المعلمة `-SourceSiteUrl` لتحديد الموقع الذي تريد رؤية حالة النقل له.

يتم وصف حالات النقل في الجدول التالي.

****

|حاله|الوصف|
|---|---|
|جاهز للتشغيل|لم يتم بدء النقل.|
|المقرر|النقل في قائمة الانتظار ولكن لم يبدأ بعد.|
|InProgress (n/4)|عملية النقل قيد التقدم في إحدى الحالات التالية: التحقق من الصحة (1/4)، النسخ الاحتياطي (2/4)، الاستعادة (3/4)، التنظيف (4/4).|
|النجاح|اكتمل النقل بنجاح.|
|فشل|فشل النقل.|
|

يمكنك أيضا تطبيق `-Verbose` الخيار للاطلاع على معلومات إضافية حول النقل.

## <a name="user-experience"></a>تجربة المستخدم

يجب أن يلاحظ مستخدمو الموقع الحد الأدنى من التعطيل عند نقل موقعهم إلى موقع جغرافي مختلف. وبصرف النظر عن حالة القراءة فقط القصيرة أثناء النقل، ستستمر الارتباطات والأذونات الموجودة في العمل كما هو متوقع بمجرد اكتمال النقل.

### <a name="site"></a>الموقع

بينما تكون عملية النقل قيد التقدم، يتم تعيين الموقع للقراءة فقط. بمجرد اكتمال النقل، يتم توجيه المستخدم إلى الموقع الجديد في الموقع الجغرافي الجديد عند النقر فوق الإشارات المرجعية أو الارتباطات الأخرى إلى الموقع.

### <a name="permissions"></a>الأذونات

سيستمر وصول المستخدمين الذين لديهم أذونات للموقع إلى الموقع أثناء النقل وبعد اكتماله.

### <a name="sync-app"></a>مزامنة التطبيق

سيكتشف تطبيق المزامنة المزامنة تلقائيا وينقلها بسلاسة إلى موقع الموقع الجديد بمجرد اكتمال نقل الموقع. لا يحتاج المستخدم إلى تسجيل الدخول مرة أخرى أو اتخاذ أي إجراء آخر. (الإصدار 17.3.6943.0625 أو إصدار أحدث من تطبيق المزامنة المطلوب.)

إذا قام مستخدم بتحديث ملف أثناء عملية النقل، فسيعلمه تطبيق المزامنة بأن تحميلات الملفات معلقة أثناء النقل.

### <a name="sharing-links"></a>مشاركة الارتباطات

عند اكتمال النقل الجغرافي لموقع SharePoint، ستتم إعادة توجيه الارتباطات المشتركة الموجودة للملفات التي تم نقلها تلقائيا إلى الموقع الجغرافي الجديد.

### <a name="most-recently-used-files-in-office-mru"></a>أحدث الملفات المستخدمة مؤخرا في Office (MRU)

يتم تحديث خدمة MRU مع url الموقع وعناوين URL للمحتوى الخاص به بمجرد اكتمال النقل. ينطبق هذا على Word وExcel وPowerPoint.

### <a name="onenote-experience"></a>تجربة OneNote

سيقوم عميل OneNote win32 وتطبيق UWP (Universal) تلقائيا بالكشف عن دفاتر الملاحظات ومزامنتها بسلاسة إلى موقع الموقع الجديد بمجرد اكتمال نقل الموقع. لا يحتاج المستخدم إلى تسجيل الدخول مرة أخرى أو اتخاذ أي إجراء آخر. المؤشر المرئي الوحيد للمستخدم هو أن مزامنة دفتر الملاحظات ستفشل عندما يكون نقل الموقع قيد التقدم. تتوفر هذه التجربة على إصدارات عميل OneNote التالية:

- OneNote win32 – الإصدار 16.0.8326.2096 (والإصدارات الأحدث)
- OneNote UWP – الإصدار 16.0.8431.1006 (والإصدارات الأحدث)
- تطبيق OneNote للأجهزة المحمولة – الإصدار 16.0.8431.1011 (والإصدارات الأحدث)

### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>Teams (ينطبق على المواقع المتصلة بمجموعة Microsoft 365)

عند اكتمال النقل الجغرافي لموقع SharePoint، سيتمكن المستخدمون من الوصول إلى ملفات موقع مجموعة Microsoft 365 الخاصة بهم على تطبيق Teams. بالإضافة إلى ذلك، ستستمر الملفات التي تمت مشاركتها عبر دردشة Teams من موقعها قبل النقل الجغرافي في العمل بعد اكتمال النقل.

لا يدعم النقل الجغرافي لموقع SharePoint نقل القنوات الخاصة من جغرافيا إلى آخر. تبقى القنوات الخاصة في الموقع الجغرافي الأصلي.
  

### <a name="sharepoint-mobile-app-iosandroid"></a>SharePoint Mobile App (iOS/Android)

يتوافق تطبيق SharePoint Mobile عبر المناطق الجغرافية ويتمكن من اكتشاف الموقع الجغرافي الجديد للموقع.

### <a name="sharepoint-workflows"></a>مهام سير عمل SharePoint

يجب إعادة نشر مهام سير عمل SharePoint 2013 بعد نقل الموقع. يجب أن تستمر مهام سير عمل SharePoint 2010 في العمل بشكل طبيعي.

### <a name="apps"></a>تطبيقات

إذا كنت تقوم بنقل موقع مع تطبيقات، فيجب إعادة تثبيت التطبيق في الموقع الجغرافي الجديد للموقع لأن التطبيق واتصالاته قد لا تكون متوفرة في الموقع الجغرافي الوجهة.

### <a name="flow"></a>تدفق

في معظم الحالات، ستستمر التدفقات في العمل بعد النقل الجغرافي لموقع SharePoint. نوصي باختبارها بمجرد اكتمال النقل.

### <a name="power-apps"></a>تطبيقات الطاقة

يجب إعادة إنشاء Power Apps في موقع الوجهة.

### <a name="data-movement-between-geo-locations"></a>حركة البيانات بين المواقع الجغرافية

يستخدم SharePoint تخزين Azure Blob لمحتوياته، بينما يتم تخزين بيانات التعريف المقترنة بالمواقع وملفاتها داخل SharePoint. بعد نقل الموقع من موقعه الجغرافي المصدر إلى موقعه الجغرافي الوجهة، ستقوم الخدمة أيضا بنقل Blob Storage المقترن به. يتم إكمال Blob Storage في حوالي 40 يوما.
