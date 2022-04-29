---
title: جدول UrlClickEvents في مخطط التتبع المتقدم
description: تعرف على كيفية البحث عن حملات التصيد الاحتيالي والنقرات المشبوهة باستخدام جدول UrlClickEvents في مخطط التتبع المتقدم.
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، UrlClickEvents، الارتباطات الآمنة، التصيد الاحتيالي، البرامج الضارة، النقرات الضارة، outlook، الفرق، البريد الإلكتروني، office365
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: bb7ee0397c79cc64c6f7396b6c3ca9450c8306f2
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130198"
---
# <a name="urlclickevents"></a>UrlClickEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لـ Office 365


`UrlClickEvents` يحتوي الجدول في مخطط التتبع المتقدم على معلومات حول [خزينة نقرات الارتباطات](../office-365-security/safe-links.md) من رسائل البريد الإلكتروني Microsoft Teams وتطبيقات Office 365 في تطبيقات سطح المكتب والأجهزة المحمولة والويب المعتمدة. 

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، راجع [مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي نقر فيه المستخدم فوق الارتباط |
| `Url` | `string` | URL الكامل الذي تم النقر فوقه من قبل المستخدم |
| `ActionType` | `string` | الإشارة إلى ما إذا كان قد تم السماح بالنقر أو حظره بواسطة ارتباطات خزينة أو تم حظره بسبب نهج مستأجر، على سبيل المثال، من قائمة "حظر السماح للمستأجر"|
| `AccountUpn` | `string` | اسم المستخدم الأساسي للحساب الذي انقر فوق الارتباط|
| `Workload` | `string` | التطبيق الذي قام المستخدم بالنقر فوق الارتباط منه، مع قيم البريد الإلكتروني Office Teams|
| `NetworkMessageId` | `string` | المعرف الفريد للبريد الإلكتروني الذي يحتوي على الارتباط الذي تم النقر فوقه، الذي تم إنشاؤه بواسطة Microsoft 365|
| `IPAddress` | `string` | عنوان IP العام للجهاز الذي قام المستخدم بالنقر فوق الارتباط منه|
| `ThreatTypes` | `string` | الحكم في وقت النقر، والذي يوضح ما إذا كان عنوان URL قد أدى إلى برامج ضارة أو تصيد احتيالي أو تهديدات أخرى|
| `DetectionMethods` | `string` | تقنية الكشف التي تم استخدامها لتحديد التهديد في وقت النقر|
| `IsClickedThrough` | `bool` | الإشارة إلى ما إذا كان المستخدم قادرا على النقر فوق عنوان URL الأصلي أو لم يكن مسموحا به|
| `UrlChain` | `string` | بالنسبة للسيناريوهات التي تتضمن عمليات إعادة التوجيه، فإنه يتضمن عناوين URL الموجودة في سلسلة إعادة التوجيه|
| `ReportId` | `string` | هذا هو المعرف الفريد لحدث النقر. لاحظ أنه بالنسبة لسيناريوهات النقر، سيكون لمعرف التقرير نفس القيمة، وبالتالي يجب استخدامه لربط حدث نقر.|

يمكنك تجربة هذا الاستعلام المثال الذي يستخدم `UrlClickEvents` الجدول لإرجاع قائمة الارتباطات التي تم السماح للمستخدم بالمتابعة فيها: 

```kusto
// Search for malicious links where user was allowed to proceed through
UrlClickEvents
| where ActionType == "ClickAllowed" or IsClickedThrough !="0"
| where ThreatTypes has "Phish"
| summarize by ReportId, IsClickedThrough, AccountUpn, NetworkMessageId, ThreatTypes, Timestamp
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [ارتباطات خزينة في Microsoft Defender لـ Office 365](../office-365-security/safe-links.md)
- [اتخاذ إجراء بشأن نتائج استعلام التتبع المتقدمة](advanced-hunting-take-action.md)