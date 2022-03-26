---
title: DeviceFileEvents table في مخطط الصيد المتقدم
description: تعرف على الأحداث ذات الصلة بالملفات في جدول DeviceFileEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و filecreationevents، و DeviceFileEvents، الملفات، المسار، الهاش، sha1، sha256، md5
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
ms.openlocfilehash: 2350e2dfd4736743f23d181d4fc2c6de0d82ccc0
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63572305"
---
# <a name="devicefileevents"></a>DeviceFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يحتوي `DeviceFileEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول إنشاء الملفات وتعديلها وغيرها من أحداث نظام الملفات. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `ActionType` | `string` | نوع النشاط الذي تم تشغيل الحدث به. راجع [مرجع المخطط داخل المدخل](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) للحصول على التفاصيل |
| `FileName` | `string`| اسم الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FolderPath` | `string` | مجلد يحتوي على الملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA1` | `string` | SHA-1 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA256` | `string` | SHA-256 للملف الذي تم تطبيق الإجراء المسجل عليه. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `MD5` | `string` | MD5 من الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FileOriginUrl` | `string` | عنوان URL حيث تم تنزيل الملف من |
| `FileOriginReferrerUrl` | `string` | URL لصفحة الويب التي تربط الملف الذي تم تنزيله |
| `FileOriginIP` | `string` | عنوان IP حيث تم تنزيل الملف من |
| `PreviousFolderPath` | `string` | المجلد الأصلي الذي يحتوي على الملف قبل تطبيق الإجراء المسجل |
| `PreviousFileName` | `string` | الاسم الأصلي للملف الذي تمت إعادة تسميته نتيجة الإجراء |
| `FileSize` | `long` | حجم الملف بالبايت |
| `InitiatingProcessAccountDomain` | `string` | مجال الحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountName` | سلسلة | اسم المستخدم للحساب الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountSid` | `string` | معرف الأمان (SID) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountObjectId` | `string` | Azure AD Object ID لحساب المستخدم الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessMD5` | `string` | م 5 من عملية (ملف صورة) التي بدأت الحدث |
| `InitiatingProcessSHA1` | `string` | SHA-1 من العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessSHA256` | `string` | SHA-256 من العملية (ملف صورة) التي بدأت الحدث. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `InitiatingProcessFolderPath` | `string` | مجلد يحتوي على العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessFileName` | `string` | اسم العملية التي بدأت الحدث |
| `InitiatingProcessFileSize` | `long` | حجم العملية (ملف الصورة) الذي بدأ الحدث |
| `InitiatingProcessVersionInfoCompanyName` | `string` | اسم الشركة من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoProductName` | `string` | اسم المنتج من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
|` InitiatingProcessVersionInfoProductVersion` | `string` | إصدار المنتج من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | اسم الملف الداخلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | اسم الملف الأصلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoFileDescription` | `string` | الوصف من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessId` | `int` | "معرّف العملية" (PID) للعملية التي بدأت الحدث |
| `InitiatingProcessCommandLine` | `string` | سطر الأوامر المستخدم لتشغيل العملية التي بدأت الحدث |
| `InitiatingProcessCreationTime` | `datetime` | تاريخ وتاريخ بدء العملية التي بدأت الحدث |
| `InitiatingProcessIntegrityLevel` | `string` | مستوى تكامل العملية التي بدأت الحدث. Windows تعيين مستويات التكامل للعمليات استنادا إلى خصائص معينة، مثل إذا تم تشغيلها من تنزيل عبر الإنترنت. تؤثر مستويات التكامل هذه على الأذونات في الموارد |
| `InitiatingProcessTokenElevation` | `string` | نوع الرمز المميز الذي يشير إلى وجود أو عدم وجود ارتفاع امتياز التحكم بالوصول إلى المستخدم (UAC) المطبق على العملية التي بدأت الحدث |
| `InitiatingProcessParentId` | `int` | "معرّف العملية" (PID) للعملية الأصل التي تم تباعدها بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentFileName` | `string` | اسم العملية الأصل التي تباعدت بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentCreationTime` | `datetime` | التاريخ والوقت الذي بدأ فيه أصل العملية المسؤولة عن الحدث |
| `RequestProtocol` | `string` | بروتوكول الشبكة، إذا كان ذلك قابلا للتطبيق، يستخدم لبدء النشاط: غير معروف أو محلي أو SMB أو NFS |
| `RequestSourceIP` | `string` | عنوان IPv4 أو IPv6 للجهاز البعيد الذي بدأ النشاط |
| `RequestSourcePort` | `string` | منفذ المصدر على الجهاز البعيد الذي بدأ النشاط |
| `RequestAccountName` | `string` | اسم المستخدم للحساب المستخدم لبدء النشاط عن بعد |
| `RequestAccountDomain` | `string` | مجال الحساب المستخدم لبدء النشاط عن بعد |
| `RequestAccountSid` | `string` | معرف الأمان (SID) للحساب المستخدم لبدء النشاط عن بعد |
| `ShareName` | `string` | اسم المجلد المشترك الذي يحتوي على الملف |
| `InitiatingProcessFileSize` | `long` | حجم الملف الذي كان يدير العملية المسؤولة عن الحدث |
| `SensitivityLabel` | `string` | التسمية المطبقة على بريد إلكتروني أو ملف أو محتوى آخر لتصنيفه لحماية المعلومات |
| `SensitivitySubLabel` | `string` | تم تطبيق اسم فرعي على بريد إلكتروني أو ملف أو محتوى آخر لتصنيفه لحماية المعلومات؛ يتم تجميع تسميات الحساسية الفرعية ضمن تسميات الحساسية ولكن يتم التعامل معها بشكل مستقل |
| `IsAzureInfoProtectionApplied` | `boolean` | تشير إلى ما إذا كان الملف مشفرا بواسطة Azure Information Protection |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp. |
| `AppGuardContainerId` | `string` | معرف للحاوية الظاهرية المستخدمة بواسطة Application Guard لعزل نشاط المستعرض |
| `AdditionalFields` | `string` | معلومات إضافية حول الكيان أو الحدث |
>[!NOTE]
> سيتم دائما عرض معلومات هاشش الملف عندما تكون متوفرة. ومع ذلك، هناك عدة أسباب محتملة وراء عدم حساب SHA1 أو SHA256 أو MD5. على سبيل المثال، قد يكون الملف موجودا في مساحة تخزين عن بعد، أو مؤمنا بواسطة عملية أخرى، أو مضغوطا، أو تم وضع علامة ظاهري عليه. في هذه السيناريوهات، تظهر معلومات تفريغ الملف فارغة.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
