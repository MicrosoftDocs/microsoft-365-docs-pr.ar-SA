---
title: جدول AlertEvidence في مخطط الصيد المتقدم
description: تعرف على المعلومات المقترنة بالتنبيهات في جدول AlertEvidence في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و AlertInfo، و التنبيه، والكيانات، و الدليل، والملف، وعنوان IP، والجهاز، والجهاز، والمستخدم، الحساب
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
ms.openlocfilehash: 9d7fc7e757b15c3682368cbd6c41b32c18724422
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63571450"
---
# <a name="alertevidence"></a>AlertEvidence

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي الجدول في مخطط [](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول كيانات مختلفة، مثل الملفات وعناوين IP وعناوين URL والمستخدمين أو الأجهزة، مقترنة بتنبيهات من Microsoft Defender ل Endpoint و Microsoft Defender ل Office 365 و Microsoft Defender لتطبيقات السحابة و Microsoft Defender for Identity.`AlertEvidence` استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `AlertId` | `string` | معرف فريد للتنبيه |
| `ServiceSource` | `string` | المنتج أو الخدمة التي وفرت معلومات التنبيه |
| `EntityType` | `string` | نوع الكائن، مثل ملف أو عملية أو جهاز أو مستخدم |
| `EvidenceRole` | `string` | كيفية مشاركة الكيان في تنبيه، مع الإشارة إلى ما إذا كان متأثيا أو مرتبطا فقط |
| `EvidenceDirection` | `string` | تشير إلى ما إذا كان الكيان هو مصدر اتصال الشبكة أو وجهة الاتصال بالشبكة |
| `FileName` | `string` | اسم الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FolderPath` | `string` | مجلد يحتوي على الملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA1` | `string` | SHA-1 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA256` | `string` | SHA-256 للملف الذي تم تطبيق الإجراء المسجل عليه. لا يتم ملء هذا الحقل عادة— استخدم عمود SHA1 عند توفره. |
| `FileSize` | `int` | حجم الملف بالبايت |
| `ThreatFamily` | `string` | عائلة البرامج الضارة التي تم تصنيف الملف أو العملية المريبة أو الضارة ضمن |
| `RemoteIP` | `string` | عنوان IP الذي كان متصلا ب |
| `RemoteUrl` | `string` | عنوان URL أو اسم المجال المؤهل بالكامل (FQDN) الذي كان قيد الاتصال |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure Active Directory |
| `AccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `LocalIP` | `string` | عنوان IP المعين للجهاز المحلي المستخدم أثناء الاتصال |
| `NetworkMessageId` | `string` | معرف فريد للبريد الإلكتروني، تم إنشاؤه بواسطة Office 365 |
| `EmailSubject` | `string` | موضوع البريد الإلكتروني |
| `ApplicationId` | `string` | معرف فريد للتطبيق |
| `Application` | `string` | التطبيق الذي ينفذ الإجراء المسجل |
| `ProcessCommandLine` | `string` | سطر الأوامر المستخدم لإنشاء العملية الجديدة |
| `AdditionalFields` | `string` | معلومات إضافية حول الحدث بتنسيق صفيف JSON |
| `RegistryKey` |`string` | مفتاح التسجيل الذي تم تطبيق الإجراء المسجل عليه |
| `RegistryValueName` |`string` | اسم قيمة السجل التي تم تطبيق الإجراء المسجل عليها |
| `RegistryValueData` |`string` | بيانات قيمة السجل التي تم تطبيق الإجراء المسجل عليها |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
