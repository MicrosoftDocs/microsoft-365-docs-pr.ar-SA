---
title: جدول DeviceTvmSoftwareEvidenceBeta في مخطط الصيد المتقدم
description: تعرف على كيفية استخدام الجدول DeviceTvmSoftwareEvidenceBeta في مخطط الصيد المتقدم.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و الخطر & إدارة الثغرات الأمنية، و الدليل، و دليل البرامج، و TVM، وإدارة الأجهزة، والبرامج، والمخزون، والنقاط الضعف، ومرجع CVE، OS DeviceTvmSoftwareEvidenceBeta
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
ms.openlocfilehash: 7fd064b906e4afe5e337df85d9dc6f174edc99cf
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/30/2021
ms.locfileid: "63575958"
---
# <a name="devicetvmsoftwareevidencebeta"></a>DeviceTvmSoftwareEvidenceBeta

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

> [!IMPORTANT]
> الجدول `DeviceTvmSoftwareEvidenceBeta` موجود حاليا في الإصدار بيتا. بمجرد أن يترك بيتا، سيتغير اسم الجدول النهائي وقد تتغير أسماء الأعمدة أيضا. بعد ذلك، من المرجح أن تكسر التعديلات الاستعلامات التي لا تزال تستخدم الأسماء السابقة. ننصح المستخدمين بمراجعة استعلاماتهم وضبطها عند الانتهاء من هذا الجدول. 


يحتوي `DeviceTvmSoftwareEvidenceBeta` الجدول في مخطط الصيد المتقدم على بيانات من إدارة المخاطر & [الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) المرتبطة [بقسم دليل البرنامج](/microsoft-365/security/defender-endpoint/tvm-software-inventory#software-evidence). يتيح لك هذا الجدول عرض دليل على مكان اكتشاف برنامج معين على جهاز. يمكنك استخدام هذا الجدول، على سبيل المثال، لتحديد مسارات ملفات برامج معينة. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `SoftwareVendor` | `string` | اسم ناشر البرنامج |
| `SoftwareName` | `string` | اسم منتج البرنامج |
| `SoftwareVersion` | `string` | رقم إصدار منتج البرنامج |
| `RegistryPaths` | `dynamic` | مسارات التسجيل حيث تم الكشف عن أدلة تشير إلى وجود البرنامج على جهاز |
| `DiskPaths` | `dynamic` | مسارات القرص حيث تم الكشف عن دليل على مستوى الملف يشير إلى وجود البرنامج على جهاز |
| `LastSeenTime` | `string` | تاريخ وتاريخ آخر مرة رأيت فيها هذه الخدمة الجهاز |




## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على المخاطر & إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [البحث الاستباقي عن التهديدات](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
