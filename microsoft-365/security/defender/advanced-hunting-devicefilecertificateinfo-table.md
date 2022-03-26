---
title: DeviceFileCertificateInfo في مخطط الصيد المتقدم
description: تعرف على معلومات توقيع الملفات في جدول DeviceFileCertificateInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، و m365، والبحث، والاستعلام، وبيانات التعقب، ومرجع المخطط، و kusto، والأعمدة، ونوع البيانات، والتوقيع الرقمي، والشهادة، وتوقيع الملفات، و DeviceFileCertificateInfo
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
ms.openlocfilehash: 7b43b6ad8ed1422830f08358f460b20b16588996
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63575770"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يحتوي `DeviceFileCertificateInfo` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول شهادات توقيع الملفات. يستخدم هذا الجدول البيانات التي يتم الحصول عليها من أنشطة التحقق من الشهادة التي يتم تنفيذها بشكل منتظم على الملفات على نقاط النهاية.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `SHA1` | `string` | SHA-1 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `IsSigned` | `boolean` | تشير إلى ما إذا كان الملف قد تم توقيعه |
| `SignatureType` | `string` | تشير إلى ما إذا كان قد تم قراءة معلومات التوقيع كمحتوى مضمن في الملف نفسه أو قراءتها من ملف كتالوج خارجي |
| `Signer` | `string` | معلومات حول توقيع الملف |
| `SignerHash` | `string` | قيمة هاش فريدة تحدد موقع |
| `Issuer` | `string` | معلومات حول المرجع المشهادات المصدر (CA) |
| `IssuerHash` | `string` | قيمة هاش فريدة تحدد مرجع مشهادات إصدار (CA) |
| `CertificateSerialNumber` | `string` | معرف الشهادة الفريدة لمرجع المصدر (CA) |
| `CrlDistributionPointUrls` | `string` |  صفيف JSON يسرد عناوين URL الخاصة باشتركات الشبكة التي تحتوي على شهادات وقوائم إلغاء الشهادات (CRLs) |
| `CertificateCreationTime` | `datetime` | تاريخ وقت إنشاء الشهادة |
| `CertificateExpirationTime` | `datetime` | التاريخ والوقت الذي تم تعيين الشهادة على انتهاء صلاحيتها |
| `CertificateCountersignatureTime` | `datetime` | تاريخ الشهادة والوقت الذي تم فيه تعيينه بالعداد |
| `IsTrusted` | `boolean` | تشير إلى ما إذا كان الملف موثوقا به استنادا إلى نتائج الدالة WinVerifyTrust، التي تقوم بالتحقق من معلومات الشهادة الجذر غير المعروفة والتواقيع غير الصالحة والشهادات التي تم إبطالها وغير ذلك من السمات القابلة للأسئلة |
| `IsRootSignerMicrosoft` | `boolean` | تشير إلى ما إذا كان موقع الشهادة الجذر هو Microsoft |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp. | 

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
