---
title: DeviceEvents table في مخطط الصيد المتقدم
description: تعرف على الحماية من الفيروسات وجدار الحماية وأنواع الأحداث الأخرى في جدول أحداث الأجهزة المتنوعة (DeviceEvents) في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و أحداث الأمان، و الحماية من الفيروسات، وجدار الحماية، وحرس الهجمات، و DeviceEvents
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
ms.openlocfilehash: 54eef2d828f9a236ae457769c8c4ff9ba429dac9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63575771"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يحتوي الجدول `DeviceEvents` أو أحداث الأجهزة المتنوعة في مخطط الصيد المتقدم على معلومات [](advanced-hunting-overview.md) حول أنواع الأحداث المختلفة، بما في ذلك الأحداث التي يتم تشغيلها بواسطة عناصر التحكم في الأمان، مثل برنامج الحماية من الفيروسات لـ Windows Defender والحماية من استغلالها. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).


| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `ActionType` | `string` | نوع النشاط الذي تم تشغيل الحدث به. راجع [مرجع المخطط داخل المدخل](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) للحصول على التفاصيل |
| `FileName` | `string` | اسم الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FolderPath` | `string` | مجلد يحتوي على الملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA1` | `string` | SHA-1 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA256` | `string` | SHA-256 للملف الذي تم تطبيق الإجراء المسجل عليه. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `MD5` | `string` | MD5 من الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FileSize` | `long` | حجم الملف بالبايت |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `RemoteUrl` | `string` | عنوان URL أو اسم المجال المؤهل بالكامل (FQDN) الذي كان قيد الاتصال |
| `RemoteDeviceName` | `string` | اسم الجهاز الذي ينفذ عملية عن بعد على الجهاز المتأثر. استنادا إلى الحدث الذي يتم الإعلام به، قد يكون هذا الاسم اسم مجال مؤهلا بالكامل (FQDN) أو اسم NetBIOS أو اسم مضيف بدون معلومات المجال |
| `ProcessId` | `int` | "معرّف العملية" (PID) للعملية التي تم إنشاؤها حديثا |
| `ProcessCommandLine` | `string` | سطر الأوامر المستخدم لإنشاء العملية الجديدة |
| `ProcessCreationTime` | `datetime` | تاريخ العملية والوقت الذي تم إنشاؤه فيه |
| `ProcessTokenElevation` | `string` | نوع الرمز المميز الذي يشير إلى وجود أو عدم وجود رفع امتياز التحكم بالوصول إلى المستخدم (UAC) المطبق على العملية التي تم إنشاؤها حديثا |
| `LogonId` | `string` | معرف لجلسة تسجيل تسجيل. هذا المعرف فريد على الجهاز نفسه فقط بين إعادة التشغيل |
| `RegistryKey` | `string` | مفتاح التسجيل الذي تم تطبيق الإجراء المسجل عليه |
| `RegistryValueName` | `string` | اسم قيمة السجل التي تم تطبيق الإجراء المسجل عليها |
| `RegistryValueData` | `string` | بيانات قيمة السجل التي تم تطبيق الإجراء المسجل عليها |
| `RemoteIP` | `string` | عنوان IP الذي كان متصلا ب |
| `RemotePort` | `int` | منفذ TCP على الجهاز البعيد الذي كان متصلا ب |
| `LocalIP` | `string` | عنوان IP المعين إلى الجهاز المحلي المستخدم أثناء الاتصال |
| `LocalPort` | `int` | منفذ TCP على الجهاز المحلي المستخدم أثناء الاتصال |
| `FileOriginUrl` | `string` | عنوان URL حيث تم تنزيل الملف من |
| `FileOriginIP` | `string` | عنوان IP حيث تم تنزيل الملف من |
| `InitiatingProcessSHA1` | `string` | SHA-1 من العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessSHA256` | `string` | SHA-256 من العملية (ملف صورة) التي بدأت الحدث. لا يتم ملء هذا الحقل عادة — استخدم عمود SHA1 عند توفره. |
| `InitiatingProcessMD5` | `string` | م 5 من عملية (ملف صورة) التي بدأت الحدث |
| `InitiatingProcessFileName` | `string` | اسم العملية التي بدأت الحدث |
| `InitiatingProcessFileSize` | `long` | حجم الملف الذي كان يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessFolderPath` | `string` | مجلد يحتوي على العملية (ملف الصورة) التي بدأت الحدث |
| `InitiatingProcessId` | `int` | "معرّف العملية" (PID) للعملية التي بدأت الحدث |
| `InitiatingProcessCommandLine` | `string` | سطر الأوامر المستخدم لتشغيل العملية التي بدأت الحدث |
| `InitiatingProcessCreationTime` | `datetime` | تاريخ وتاريخ بدء العملية التي بدأت الحدث |
| `InitiatingProcessAccountDomain` | `string` | مجال الحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountName` | `string` | اسم المستخدم للحساب الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountSid` | `string` | معرف الأمان (SID) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي يدير العملية المسؤولة عن الحدث |
| `InitiatingProcessAccountObjectId` | `string` | Azure AD Object ID لحساب المستخدم الذي قام بتولى العملية المسؤولة عن الحدث |
| `InitiatingProcessVersionInfoCompanyName` | `string` | اسم الشركة من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoProductName` | `string` | اسم المنتج من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoProductVersion` | `string` | إصدار المنتج من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | اسم الملف الداخلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | اسم الملف الأصلي من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessVersionInfoFileDescription` | `string` | الوصف من معلومات إصدار العملية (ملف الصورة) المسؤول عن الحدث |
| `InitiatingProcessParentId` | `int` | "معرّف العملية" (PID) للعملية الأصل التي تم تباعدها بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentFileName` | `string` | اسم العملية الأصل التي تباعدت بين العملية المسؤولة عن الحدث |
| `InitiatingProcessParentCreationTime` | `datetime` | التاريخ والوقت الذي بدأ فيه أصل العملية المسؤولة عن الحدث |
| `InitiatingProcessLogonId` | `string` | معرف لجلسة تسجيل من العملية التي بدأت الحدث. هذا المعرف فريد على الجهاز نفسه فقط بين إعادة التشغيل |
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
