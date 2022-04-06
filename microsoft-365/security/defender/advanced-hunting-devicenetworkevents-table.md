---
title: DeviceNetworkEvents جدول في مخطط الصيد المتقدم
description: تعرف على أحداث اتصال الشبكة التي يمكنك الاستعلام عنها من جدول DeviceNetworkEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و devicenetworkevents، و NetworkCommunicationEvents، واتصال الشبكة، و ip البعيد، و ip المحلي
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
ms.openlocfilehash: 6e791efaf418b57716b1f53541292b37805898f4
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63583078"
---
# <a name="devicenetworkevents"></a>DeviceNetworkEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية



يحتوي `DeviceNetworkEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول اتصالات الشبكة والأحداث ذات الصلة. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `ActionType` | `string` | نوع النشاط الذي تم تشغيل الحدث به. راجع [مرجع المخطط داخل المدخل](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) للحصول على التفاصيل |
| `RemoteIP` | `string` | عنوان IP الذي كان متصلا ب |
| `RemotePort` | `int` | منفذ TCP على الجهاز البعيد الذي كان متصلا ب |
| `RemoteUrl` | `string` | عنوان URL أو اسم المجال المؤهل بالكامل (FQDN) الذي كان قيد الاتصال |
| `LocalIP` | `string` | عنوان IP المعين إلى الجهاز المحلي المستخدم أثناء الاتصال |
| `LocalPort` | `int` | منفذ TCP على الجهاز المحلي المستخدم أثناء الاتصال |
| `Protocol` | `string` | البروتوكول المستخدم أثناء الاتصال |
| `LocalIPType` | `string` | نوع عنوان IP، على سبيل المثال عام، خاص، محجوز، تكرار تكراري، Teredo، FourToSixMapping، وبث |
| `RemoteIPType` | `string` | نوع عنوان IP، على سبيل المثال عام، خاص، محجوز، تكرار تكراري، Teredo، FourToSixMapping، وبث |
| `InitiatingProcessSHA1` | `string` | SHA-1 من العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessSHA256` | `string` | SHA-256 من العملية (ملف صورة) التي بدأت الحدث. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `InitiatingProcessMD5` | `string` | م 5 من عملية (ملف صورة) التي بدأت الحدث |
| `InitiatingProcessFileName` | `string` | اسم العملية التي بدأت الحدث |
| `InitiatingProcessFileSize` | `long` | حجم الملف الذي كان يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessVersionInfoCompanyName` | `string` | اسم الشركة من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoProductName` | `string` | اسم المنتج من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoProductVersion` | `string` | إصدار المنتج من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | اسم الملف الداخلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | اسم الملف الأصلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoFileDescription` | `string` | الوصف من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessId` | `int` | "معرّف العملية" (PID) للعملية التي بدأت الحدث |
| `InitiatingProcessCommandLine` | `string` | سطر الأوامر المستخدم لتشغيل العملية التي بدأت الحدث |
| `InitiatingProcessCreationTime` | `datetime` | تاريخ وتاريخ بدء العملية التي بدأت الحدث |
| `InitiatingProcessFolderPath` | `string` | مجلد يحتوي على العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessParentFileName` | `string` | اسم العملية الأصل التي تباعدت بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentId` | `int` | "معرّف العملية" (PID) للعملية الأصل التي تم تباعدها بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentCreationTime` | `datetime` | التاريخ والوقت الذي بدأ فيه أصل العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountDomain` | `string` | مجال الحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountName` | `string` | اسم المستخدم للحساب الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountSid` | `string` | معرف الأمان (SID) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountObjectId` | `string` | Azure AD Object ID لحساب المستخدم الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessIntegrityLevel` | `string` | مستوى تكامل العملية التي بدأت الحدث. Windows تعيين مستويات التكامل للعمليات استنادا إلى خصائص معينة، مثل إذا تم تشغيلها من تنزيل عبر الإنترنت. تؤثر مستويات التكامل هذه على الأذونات في الموارد |
| `InitiatingProcessTokenElevation` | `string` | نوع الرمز المميز الذي يشير إلى وجود أو عدم وجود ارتفاع امتياز التحكم بالوصول إلى المستخدم (UAC) المطبق على العملية التي بدأت الحدث |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp |
| `AppGuardContainerId` | `string` | معرف للحاوية الظاهرية المستخدمة بواسطة Application Guard لعزل نشاط المستعرض |
| `AdditionalFields` | `string` | معلومات إضافية حول الحدث بتنسيق صفيف JSON |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
