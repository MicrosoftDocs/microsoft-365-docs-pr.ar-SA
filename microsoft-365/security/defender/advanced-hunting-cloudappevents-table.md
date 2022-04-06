---
title: جدول CloudAppEvents في مخطط التتبع المتقدم
description: تعرف على الأحداث من التطبيقات والخدمات السحابية في جدول CloudAppEvents لمخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، CloudAppEvents، Defender for Cloud Apps
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
ms.openlocfilehash: 77b4ebd42a8c105340d6d965380aa42b64ae6734
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664953"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

`CloudAppEvents` يحتوي الجدول في مخطط [التتبع المتقدم](advanced-hunting-overview.md) على معلومات حول الأنشطة في العديد من التطبيقات والخدمات السحابية التي تغطيها Microsoft Defender for Cloud Apps. للحصول على قائمة كاملة، انتقل إلى [التطبيقات والخدمات التي تمت تغطيتها](#apps-and-services-covered). استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

> [!IMPORTANT]
> يتضمن هذا الجدول معلومات كانت متوفرة في `AppFileEvents` الجدول. بدءا من 7 مارس 2021، يجب على المستخدمين الذين يتتبعون الأنشطة المتعلقة بالملفات في الخدمات السحابية في هذا التاريخ وخارجه استخدام `CloudAppEvents` الجدول بدلا من ذلك. <br><br>تأكد من البحث عن الاستعلامات وقواعد الكشف المخصصة التي لا تزال تستخدم `AppFileEvents` الجدول وتحريرها لاستخدام `CloudAppEvents` الجدول. يمكن العثور على المزيد من الإرشادات حول تحويل الاستعلامات المتأثرة في [Hunt عبر أنشطة تطبيق السحابة مع Microsoft 365 Defender التتبع المتقدم](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، [راجع مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `ActionType` | `string` | نوع النشاط الذي قام بتشغيل الحدث |
| `Application` | `string` | التطبيق الذي نفذ الإجراء المسجل |
| `ApplicationId` | `string` | معرف فريد للتطبيق |
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure Active Directory |
| `AccountId` | `string` | معرف للحساب كما تم العثور عليه بواسطة Microsoft Defender for Cloud Apps. يمكن أن يكون معرف Azure Active Directory أو اسم المستخدم الأساسي أو معرفات أخرى. |
| `AccountDisplayName` | `string` | اسم مستخدم الحساب المعروض في دفتر العناوين. عادة ما يكون مزيجا من اسم معين أو أول، وبدء متوسط، واسم العائلة أو اللقب. |
| `IsAdminOperation` | `string` | الإشارة إلى ما إذا كان قد تم تنفيذ النشاط من قبل مسؤول |
| `DeviceType` | `string` | نوع الجهاز استنادا إلى الغرض والوظائف، مثل "جهاز الشبكة" أو "محطة العمل" أو "الخادم" أو "الجوال" أو "وحدة تحكم الألعاب" أو "الطابعة" |
| `OSPlatform` | `string` | نظام أساسي لنظام التشغيل الذي يعمل على الجهاز. يشير هذا العمود إلى أنظمة تشغيل محددة، بما في ذلك الاختلافات داخل العائلة نفسها، مثل Windows 11 Windows 10 Windows 7. |
| `IPAddress` | `string` | عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة |
| `IsAnonymousProxy` | `string` | الإشارة إلى ما إذا كان عنوان IP ينتمي إلى وكيل مجهول معروف |
| `CountryCode` | `string` | رمز مكون من حرفين يشير إلى البلد الذي تم فيه تخصيص عنوان IP للعميل جغرافيا |
| `City` | `string` | المدينة التي تم فيها تحديد موقع عنوان IP للعميل |
| `Isp` | `string` | موفر خدمة الإنترنت (ISP) المقترن بعنوان IP |
| `UserAgent` | `string` | معلومات عامل المستخدم من مستعرض الويب أو تطبيق عميل آخر |
| `ActivityType` | `string` | نوع النشاط الذي قام بتشغيل الحدث |
| `ActivityObjects` | `dynamic` | قائمة الكائنات، مثل الملفات أو المجلدات، التي كانت مضمنة في النشاط المسجل |
| `ObjectName` | `string` | اسم الكائن الذي تم تطبيق الإجراء المسجل عليه |
| `ObjectType` | `string` | نوع الكائن، مثل ملف أو مجلد، الذي تم تطبيق الإجراء المسجل عليه |
| `ObjectId` | `string` | معرف فريد للكائن الذي تم تطبيق الإجراء المسجل عليه |
| `ReportId` | `string` | معرف فريد للحدث |
| `RawEventData` | `string` | معلومات الحدث البسيطة من التطبيق أو الخدمة المصدر بتنسيق JSON |
| `AdditionalFields` | `dynamic` | معلومات إضافية حول الكيان أو الحدث |
| `AccountType` | `string` | نوع حساب المستخدم، الذي يشير إلى دوره العام ومستويات الوصول الخاصة به، مثل Regular و System و Admin و DcAdmin و System و Application |
| `IsExternalUser` | `boolean` | الإشارة إلى ما إذا كان المستخدم داخل الشبكة لا ينتمي إلى مجال المؤسسة |
| `IsImpersonated` | `boolean` | الإشارة إلى ما إذا كان قد تم تنفيذ النشاط من قبل مستخدم واحد لمستخدم آخر (منتحل) |
| `IPTags` | `dynamic` | المعلومات المعرفة من قبل العميل المطبقة على عناوين IP ونطاقات عناوين IP محددة |
| `IPCategory` | `string` | معلومات إضافية حول عنوان IP |
| `UserAgentTags` | `dynamic` | مزيد من المعلومات التي يوفرها Microsoft Defender for Cloud Apps في علامة في حقل عامل المستخدم. يمكن أن يكون لها أي من القيم التالية: العميل الأصلي، المستعرض القديم، نظام التشغيل القديم، الروبوت |

## <a name="apps-and-services-covered"></a>التطبيقات والخدمات التي تمت تغطيتها

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
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
