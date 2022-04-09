---
title: جدول DeviceLogonEvents في مخطط التتبع المتقدم
description: تعرف على أحداث المصادقة أو تسجيل الدخول في جدول DeviceLogonEvents لمخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، الوصف، تسجيل الدخول، DeviceLogonEvents، المصادقة، تسجيل الدخول، تسجيل الدخول
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
ms.openlocfilehash: 516b74eb8d1e62194718e0ad3234b3269e07fb83
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731362"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint



`DeviceLogonEvents` يحتوي الجدول في مخطط [التتبع المتقدم](advanced-hunting-overview.md) على معلومات حول تسجيلات دخول المستخدم وأحداث المصادقة الأخرى على الأجهزة. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) التي يدعمها جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، [راجع مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `ActionType` | `string` |نوع النشاط الذي قام بتشغيل الحدث |
| `LogonType` | `string` | نوع جلسة تسجيل الدخول، على وجه التحديد:<br><br> - **تفاعلي** - يتفاعل المستخدم فعليا مع الجهاز باستخدام لوحة المفاتيح والشاشة المحلية<br><br> - **تسجيلات الدخول التفاعلية عن بعد (RDP)** - يتفاعل المستخدم مع الجهاز عن بعد باستخدام سطح المكتب البعيد أو الخدمات الطرفية أو المساعدة عن بعد أو عملاء RDP الآخرين<br><br> - **الشبكة** - تم بدء جلسة العمل عند الوصول إلى الجهاز باستخدام PsExec أو عند الوصول إلى الموارد المشتركة على الجهاز، مثل الطابعات والمجلدات المشتركة<br><br> - **Batch** - جلسة عمل تم بدئها بواسطة المهام المجدولة<br><br> - **الخدمة** - جلسة العمل التي تبدأها الخدمات عند بدء تشغيلها<br> |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `Protocol` | `string` | البروتوكول المستخدم أثناء الاتصال |
| `FailureReason` | `string` | معلومات تشرح سبب فشل الإجراء المسجل |
| `IsLocalAdmin` | `boolean` | مؤشر منطقي حول ما إذا كان المستخدم مسؤولا محليا على الجهاز |
| `LogonId` | `string` | معرف جلسة تسجيل الدخول. هذا المعرف فريد على نفس الجهاز فقط بين عمليات إعادة التشغيل |
| `RemoteDeviceName` | `string` | اسم الجهاز الذي نفذ عملية عن بعد على الجهاز المتأثر. استنادا إلى الحدث الذي يتم الإبلاغ عنه، قد يكون هذا الاسم اسم مجال مؤهل بالكامل (FQDN) أو اسم NetBIOS أو اسم مضيف بدون معلومات المجال |
| `RemoteIP` | `string` | عنوان IP الذي كان يتم الاتصال به |
| `RemoteIPType` | `string` | نوع عنوان IP، على سبيل المثال، Public و Private و Reserved و Loopback و Teredo و FourToSixMapping و Broadcast |
| `RemotePort` | `int` | منفذ TCP على الجهاز البعيد الذي كان يتم الاتصال به |
| `InitiatingProcessAccountDomain` | `string` | مجال الحساب الذي قام بتشغيل العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountName` | `string` | اسم المستخدم للحساب الذي قام بتشغيل العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountSid` | `string` | معرف الأمان (SID) للحساب الذي قام بتشغيل العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي قام بتشغيل العملية المسؤولة عن الحدث |
| ` InitiatingProcessAccountObjectId` | `string` | معرف كائن Azure AD لحساب المستخدم الذي قام بتشغيل العملية المسؤولة عن الحدث |
| `InitiatingProcessIntegrityLevel` | `string` | مستوى تكامل العملية التي بدأت الحدث. Windows تعيين مستويات التكامل للعمليات استنادا إلى خصائص معينة، مثل ما إذا تم تشغيلها من تنزيل الإنترنت. تؤثر مستويات التكامل هذه على أذونات الموارد |
| `InitiatingProcessTokenElevation` | `string` | نوع الرمز المميز الذي يشير إلى وجود أو غياب رفع امتياز التحكم في وصول المستخدم (UAC) المطبق على العملية التي بدأت الحدث |
| `InitiatingProcessSHA1` | `string` | SHA-1 للعملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessSHA256` | `string` | SHA-256 للعملية (ملف الصورة) التي بدأت الحدث. لا يتم ملء هذا الحقل عادة— استخدم عمود SHA1 عند توفره |
| `InitiatingProcessMD5` | `string` | تجزئة MD5 للعملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessFileName` | `string` | اسم العملية التي بدأت الحدث |
| `InitiatingProcessFileSize` | `long` | حجم الملف الذي قام بتشغيل العملية المسؤولة عن الحدث |
| `InitiatingProcessVersionInfoCompanyName` | `string` | اسم الشركة من معلومات إصدار العملية (ملف الصورة) المسؤولة عن الحدث |
| `InitiatingProcessVersionInfoProductName` | `string` | اسم المنتج من معلومات إصدار العملية (ملف الصورة) المسؤولة عن الحدث |
| `InitiatingProcessVersionInfoProductVersion` | `string` | إصدار المنتج من معلومات إصدار العملية (ملف الصورة) المسؤولة عن الحدث |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | اسم الملف الداخلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | اسم الملف الأصلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoFileDescription` | `string` | الوصف من معلومات إصدار العملية (ملف الصورة) المسؤولة عن الحدث |
| `InitiatingProcessId` | `int` | معرف العملية (PID) للعملية التي بدأت الحدث |
| `InitiatingProcessCommandLine` | `string` | سطر الأوامر المستخدم لتشغيل العملية التي بدأت الحدث |
| `InitiatingProcessCreationTime` | `datetime` | تاريخ ووقت بدء العملية التي بدأت الحدث |
| `InitiatingProcessFolderPath` | `string` | المجلد الذي يحتوي على العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessParentId` | `int` | معرف العملية (PID) للعملية الأصل التي أفرزت العملية المسؤولة عن الحدث |
| `InitiatingProcessParentFileName` | `string` | اسم العملية الأصل التي أفرزت العملية المسؤولة عن الحدث |
| `InitiatingProcessParentCreationTime` | `datetime` | تاريخ ووقت بدء العملية المسؤولة عن الحدث |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد متكرر. لتعريف الأحداث الفريدة، يجب استخدام هذا العمود بالتزامن مع أعمدة DeviceName وStamp timestamp |
| `AppGuardContainerId` | `string` | معرف الحاوية الظاهرية المستخدمة من قبل Application Guard لعزل نشاط المستعرض |
| `AdditionalFields` | `string` | معلومات إضافية حول الحدث بتنسيق صفيف JSON |

>[!NOTE]
>مجموعة DeviceLogonEvents غير معتمدة على أجهزة Windows 7 أو Windows Server 2008R2 التي تم إلحاقها ب Defender لنقطة النهاية. نوصي بالترقية إلى نظام تشغيل أحدث للرؤية المثلى إلى نشاط تسجيل دخول المستخدم.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
