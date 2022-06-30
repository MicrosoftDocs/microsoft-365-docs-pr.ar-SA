---
title: جدول DeviceFileCertificateInfo في مخطط التتبع المتقدم
description: تعرف على معلومات توقيع الملفات في جدول DeviceFileCertificateInfo لمخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، العمود، نوع البيانات، التوقيع الرقمي، الشهادة، توقيع الملفات، DeviceFileCertificateInfo
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
ms.openlocfilehash: 019ca8eced735b8a9e24c2b0f3e3baae37757875
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554544"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

`DeviceFileCertificateInfo` يحتوي الجدول في مخطط [التتبع المتقدم](advanced-hunting-overview.md) على معلومات حول شهادات توقيع الملفات. يستخدم هذا الجدول البيانات التي تم الحصول عليها من أنشطة التحقق من الشهادة التي يتم تنفيذها بانتظام على الملفات على نقاط النهاية.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، [راجع مرجع التتبع المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | تاريخ ووقت تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `SHA1` | `string` | SHA-1 من الملف الذي تم تطبيق الإجراء المسجل عليه |
| `IsSigned` | `boolean` | الإشارة إلى ما إذا كان الملف موقع |
| `SignatureType` | `string` | الإشارة إلى ما إذا كان قد تمت قراءة معلومات التوقيع كمحتوى مضمن في الملف نفسه أو قراءتها من ملف كتالوج خارجي |
| `Signer` | `string` | معلومات حول موقع الملف |
| `SignerHash` | `string` | قيمة تجزئة فريدة تحدد الموقع |
| `Issuer` | `string` | معلومات حول المرجع المصدق المصدر (CA) |
| `IssuerHash` | `string` | قيمة تجزئة فريدة تحدد إصدار المرجع المصدق (CA) |
| `CertificateSerialNumber` | `string` | معرف الشهادة الفريدة للمرجع المصدق المصدر (CA) |
| `CrlDistributionPointUrls` | `string` |  صفيف JSON يسرد عناوين URL لمشاركات الشبكة التي تحتوي على الشهادات وقوائم إبطال الشهادات (CRLs) |
| `CertificateCreationTime` | `datetime` | تاريخ ووقت إنشاء الشهادة |
| `CertificateExpirationTime` | `datetime` | تاريخ ووقت تعيين الشهادة لتنتهي صلاحيتها |
| `CertificateCountersignatureTime` | `datetime` | تاريخ ووقت توقيع الشهادة |
| `IsTrusted` | `boolean` | الإشارة إلى ما إذا كان الملف موثوقا به استنادا إلى نتائج الدالة WinVerifyTrust، التي تتحقق من معلومات شهادة الجذر غير المعروفة والتواقيع غير الصالحة والشهادات التي تم إبطالها والسمات الأخرى المشكوك فيها |
| `IsRootSignerMicrosoft` | `boolean` | الإشارة إلى ما إذا كان موقع الشهادة الجذر هو Microsoft وما إذا كان الملف مضمنا في نظام التشغيل Windows |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد متكرر. لتعريف الأحداث الفريدة، يجب استخدام هذا العمود بالتزامن مع أعمدة DeviceName وStamp timestamp. | 

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
