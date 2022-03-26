---
title: DeviceLogonEvents table في مخطط الصيد المتقدم
description: تعرف على أحداث المصادقة أو تسجيل الدخول في جدول DeviceLogonEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، نوع البيانات، الوصف، تسجيل الدخول، DeviceLogonEvents، المصادقة، تسجيل الدخول، تسجيل الدخول
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
ms.openlocfilehash: dbafb4c967bca09195277aa4c79c95dd1dc87afb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570647"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية



يحتوي `DeviceLogonEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول تسجيلات تسجيل المستخدمين وغيرها من أحداث المصادقة على الأجهزة. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `ActionType` | `string` |نوع النشاط الذي تسبب في تشغيل الحدث |
| `LogonType` | `string` | نوع جلسة تسجيل تسجيل، على وجه التحديد:<br><br> - **تفاعلي** - يتفاعل المستخدم فعليا مع الجهاز باستخدام لوحة المفاتيح والشاشة المحلية<br><br> - **تسجيلات تسجيل (RDP)** التفاعلية عن بعد - يتفاعل المستخدم مع الجهاز عن بعد باستخدام سطح المكتب البعيد أو خدمات المحطة الطرفية أو المساعدة عن بعد أو عملاء RDP الآخرين<br><br> - **الشبكة** - جلسة العمل التي تبدأ عند الوصول إلى الجهاز باستخدام PsExec أو عند الوصول إلى الموارد المشتركة على الجهاز، كالطابعات والمجلدات المشتركة،<br><br> - **دفعة** - جلسة عمل تبدأ بالمهام المجدولة<br><br> - **الخدمة** - جلسة العمل التي تبدأ بواسطة الخدمات عند بدء تشغيلها<br> |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `Protocol` | `string` | البروتوكول المستخدم أثناء الاتصال |
| `FailureReason` | `string` | معلومات تشرح سبب فشل الإجراء المسجل |
| `IsLocalAdmin` | `boolean` | مؤشر منطقي حول ما إذا كان المستخدم مسؤولا محليا على الجهاز |
| `LogonId` | `string` | معرف لجلسة تسجيل تسجيل. هذا المعرف فريد على الجهاز نفسه فقط بين إعادة التشغيل |
| `RemoteDeviceName` | `string` | اسم الجهاز الذي ينفذ عملية عن بعد على الجهاز المتأثر. استنادا إلى الحدث الذي يتم الإعلام به، قد يكون هذا الاسم اسم مجال مؤهلا بالكامل (FQDN) أو اسم NetBIOS أو اسم مضيف بدون معلومات المجال |
| `RemoteIP` | `string` | عنوان IP الذي كان متصلا ب |
| `RemoteIPType` | `string` | نوع عنوان IP، على سبيل المثال عام، خاص، محجوز، تكرار تكراري، Teredo، FourToSixMapping، وبث |
| `RemotePort` | `int` | منفذ TCP على الجهاز البعيد الذي كان متصلا ب |
| `InitiatingProcessAccountDomain` | `string` | مجال الحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountName` | `string` | اسم المستخدم للحساب الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountSid` | `string` | معرف الأمان (SID) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي يدير العملية المسؤولة عن الحدث |
| ` InitiatingProcessAccountObjectId` | `string` | Azure AD Object ID لحساب المستخدم الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessIntegrityLevel` | `string` | مستوى تكامل العملية التي بدأت الحدث. Windows تعيين مستويات التكامل للعمليات استنادا إلى خصائص معينة، مثل إذا تم تشغيلها من تنزيل عبر الإنترنت. تؤثر مستويات التكامل هذه على الأذونات في الموارد |
| `InitiatingProcessTokenElevation` | `string` | نوع الرمز المميز الذي يشير إلى وجود أو عدم وجود ارتفاع امتياز التحكم بالوصول إلى المستخدم (UAC) المطبق على العملية التي بدأت الحدث |
| `InitiatingProcessSHA1` | `string` | SHA-1 من العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessSHA256` | `string` | SHA-256 من العملية (ملف صورة) التي بدأت الحدث. لا يتم ملء هذا الحقل عادة— استخدم عمود SHA1 عند توفره |
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
| `InitiatingProcessParentId` | `int` | "معرّف العملية" (PID) للعملية الأصل التي تم تباعدها بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentFileName` | `string` | اسم العملية الأصل التي تباعدت بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentCreationTime` | `datetime` | التاريخ والوقت الذي بدأ فيه أصل العملية المسؤولة عن الحدث |
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
