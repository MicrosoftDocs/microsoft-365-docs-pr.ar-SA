---
title: جدول CloudAppEvents في مخطط الصيد المتقدم
description: تعرف على الأحداث من تطبيقات السحابة وخدماتها في جدول CloudAppEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، و m365، والبحث، والاستعلام، وبيانات التعقب، ومرجع المخطط، و kusto، والأعمدة، ونوع البيانات، والوصف، و CloudAppEvents، و Defender for Cloud Apps
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: daed3fb87aab498cdf91247a59e48af685aed010
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/28/2021
ms.locfileid: "63572306"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender



يحتوي `CloudAppEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول الأنشطة في مختلف تطبيقات السحابة والخدمات التي يغطيها Microsoft Defender لتطبيقات السحابة. للحصول على قائمة كاملة، الانتقال إلى [التطبيقات والخدمات التي تم تناولها](#apps-and-services-covered). استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول. 

>[!IMPORTANT]
>يتضمن هذا الجدول المعلومات التي كانت متوفرة في `AppFileEvents` الجدول. بدءا من 7 مارس 2021 `CloudAppEvents` ، يجب على المستخدمين الذين يتعقبون الأنشطة المتعلقة بالملفات في الخدمات السحابية في هذا التاريخ وخارجه استخدام الجدول بدلا من ذلك. <br><br>تأكد من البحث عن الاستعلامات وقواعد الكشف المخصصة `AppFileEvents` التي لا تزال تستخدم الجدول وتحريرها لاستخدام `CloudAppEvents` الجدول. يمكن العثور على مزيد من الإرشادات حول تحويل الاستعلامات المتأثرة في "البحث عبر أنشطة تطبيقات السحابة" Microsoft 365 Defender [البحث المتقدم](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).


للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `ActionType` | `string` | نوع النشاط الذي تسبب في تشغيل الحدث |
| `Application` | `string` | التطبيق الذي ينفذ الإجراء المسجل |
| `ApplicationId` | `string` | معرف فريد للتطبيق |
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure Active Directory |
| `AccountId` | `string` | معرف للحساب كما وجده Microsoft Defender لتطبيقات السحابة. قد يكون معرف Azure Active Directory أو اسم المستخدم الأساسي أو معرفات أخرى. |
| `AccountDisplayName` | `string` | اسم مستخدم الحساب المعروض في دفتر العنوان. عادة ما تكون تركيبة من اسم معين أو أول، وابتداء وسطي، واسم عائلة أو اسم عائلة. |
| `IsAdminOperation` | `string` | تشير إلى ما إذا كان قد تم تنفيذ النشاط من قبل مسؤول |
| `DeviceType` | `string` | نوع الجهاز استنادا إلى الغرض والوظائف، مثل "جهاز الشبكة" أو "محطة العمل" أو "الخادم" أو "الجوال" أو "وحدة تحكم الألعاب" أو "الطابعة" | 
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يتم تشغيله على الجهاز. يشير هذا العمود إلى أنظمة تشغيل معينة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 Windows 10 Windows 7. |
| `IPAddress` | `string` | عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة |
| `IsAnonymousProxy` | `string` | تشير إلى ما إذا كان عنوان IP ينتمي إلى وكيل مجهول معروف |
| `CountryCode` | `string` | رمز من حرفين يشير إلى البلد حيث تم تحديد الموقع الجغرافي لرسالة عنوان IP للعميل |
| `City` | `string` | المدينة حيث تم تحديد الموقع الجغرافي  عنوان IP للعميل |
| `Isp` | `string` | موفر خدمة الإنترنت (ISP) المقترن وعنوان IP |
| `UserAgent` | `string` | معلومات وكيل المستخدم من مستعرض الويب أو تطبيق عميل آخر |
| `ActivityType` | `string` | نوع النشاط الذي تسبب في تشغيل الحدث |
| `ActivityObjects` | `dynamic` | قائمة العناصر، مثل الملفات أو المجلدات، التي كانت مضمونة في النشاط المسجل |
| `ObjectName` | `string` | اسم الكائن الذي تم تطبيق الإجراء المسجل عليه |
| `ObjectType` | `string` | نوع الكائن، مثل ملف أو مجلد، الذي تم تطبيق الإجراء المسجل عليه |
| `ObjectId` | `string` | معرف فريد للكائن الذي تم تطبيق الإجراء المسجل عليه |
| `ReportId` | `string` | معرف فريد للحدث |
| `RawEventData` | `string` | معلومات الحدث الخام من التطبيق أو الخدمة المصدر بتنسيق JSON |
| `AdditionalFields` | `dynamic` | معلومات إضافية حول الكيان أو الحدث |
| `AccountType` | `string` | نوع حساب المستخدم، مع الإشارة إلى دوره العام ومستويات الوصول الخاصة به، مثل العادية، النظام، المسؤول، DcAdmin، النظام، التطبيق | 
| `IsExternalUser` | `boolean` | تشير إلى ما إذا كان المستخدم داخل الشبكة لا ينتمي إلى مجال المؤسسة | 
| `IsImpersonated` | `boolean` | تشير إلى ما إذا كان النشاط قد تم من قبل مستخدم واحد لمستخدم آخر (منتحل) | 
| `IPTags` | `dynamic` | المعلومات المعرفة من قبل العميل المطبقة على عناوين IP المحددة ونطاقات عناوين IP | 
| `IPCategory` | `string` | معلومات إضافية حول عنوان IP | 
| `UserAgentTags` | `dynamic` | مزيد من المعلومات التي يوفرها Microsoft Defender لتطبيقات السحابة في علامة في حقل وكيل المستخدم. يمكن أن يكون أي من القيم التالية: العميل الأصلي، المستعرض قديم، نظام التشغيل قديم، روبوت | 

## <a name="apps-and-services-covered"></a>التطبيقات والخدمات التي تم تناولها

- Dropbox
- Dynamics 365
- Exchange Online
- Microsoft Teams
- OneDrive for Business
- Power Automate
- Power BI
- SharePoint Online
- Skype for Business
- Office 365
- Yammer 

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
