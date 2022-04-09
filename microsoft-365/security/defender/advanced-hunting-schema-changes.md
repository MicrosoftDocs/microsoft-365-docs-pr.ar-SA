---
title: تسمية التغييرات في مخطط التتبع المتقدم Microsoft 365 Defender
description: تعقب ومراجعة جداول تغييرات التسمية والأعمدة في مخطط التتبع المتقدم
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، الجدول، البيانات، تسمية التغييرات، إعادة تسمية
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
ms.openlocfilehash: 4e58bb3d8c8cc7c507c4136abcabeb7e42b6827d
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731494"
---
# <a name="advanced-hunting-schema---naming-changes"></a>مخطط التتبع المتقدم - تسمية التغييرات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

يتم تحديث [مخطط التتبع المتقدم](advanced-hunting-schema-tables.md) بانتظام لإضافة جداول وأعمدة جديدة. في بعض الحالات، تتم إعادة تسمية أسماء الأعمدة الموجودة أو استبدالها لتحسين تجربة المستخدم. راجع هذه المقالة لمراجعة تغييرات التسمية التي قد تؤثر على الاستعلامات.

يتم تطبيق تغييرات التسمية تلقائيا على الاستعلامات التي يتم حفظها في Defender for Cloud، بما في ذلك الاستعلامات المستخدمة بواسطة قواعد الكشف المخصصة. لا تحتاج إلى تحديث هذه الاستعلامات يدويا. ومع ذلك، ستحتاج إلى تحديث الاستعلامات التالية:
- الاستعلامات التي يتم تشغيلها باستخدام واجهة برمجة التطبيقات
- الاستعلامات التي يتم حفظها في مكان آخر خارج Defender for Cloud

## <a name="december-2020"></a>2020 ديسمبر

| اسم الجدول | اسم العمود الأصلي | اسم عمود جديد | سبب التغيير
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | ملاحظات العملاء |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | ملاحظات العملاء |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | ملاحظات العملاء |

## <a name="january-2021"></a>2021 يناير

| اسم العمود | اسم القيمة الأصلية | اسم قيمة جديدة | سبب التغيير
|--|--|--|--|
| `DetectionSource` | Defender for Cloud Apps | Microsoft Defender for Cloud Apps | الوسم |
| `DetectionSource` | WindowsDefenderAtp| الكشف التلقائي والاستجابة على النقط النهائية| الوسم |
| `DetectionSource` | WindowsDefenderAv | مكافحه الفيروسات | الوسم |
| `DetectionSource` | شاشة WindowsDefenderSmart |  Smartscreen | الوسم |
| `DetectionSource` | CustomerTI | TI مخصص | الوسم |
| `DetectionSource` | OfficeATP | Microsoft Defender لـ Office 365 | الوسم |
| `DetectionSource` | MTP | Microsoft 365 Defender | الوسم |
| `DetectionSource` | AzureATP | Microsoft Defender for Identity | الوسم |
| `DetectionSource` | CustomDetection | الكشف المخصص | الوسم |
| `DetectionSource` | الاستثمار التلقائي |التحقيق التلقائي | الوسم |
| `DetectionSource` | ThreatExperts | خبراء المخاطر في Microsoft | الوسم |
| `DetectionSource` | الجهة الخارجية TI | أجهزة استشعار الجهة الخارجية | الوسم |
| `ServiceSource` | Microsoft Defender ATP| Microsoft Defender for Endpoint | الوسم |
|`ServiceSource` |الحماية من التهديدات من Microsoft | Microsoft 365 Defender | الوسم |
| `ServiceSource` | Office 365 ATP |Microsoft Defender لـ Office 365 | الوسم |
| `ServiceSource` |Azure ATP |Microsoft Defender for Identity | الوسم |

`DetectionSource` متوفر في جدول [AlertInfo](advanced-hunting-alertinfo-table.md) . `ServiceSource` متوفر في جداول [AlertEvidence](advanced-hunting-alertevidence-table.md) و [AlertInfo](advanced-hunting-alertinfo-table.md) . 

## <a name="february-2021"></a>2021 فبراير عام

1. في [جدولي EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) و [EmailEvents](advanced-hunting-emailevents-table.md)، `MalwareFilterVerdict`تم استبدال `ThreatTypes` العمود والأعمدة`PhishFilterVerdict`. `MalwareDetectionMethod` تم أيضا استبدال الأعمدة والعمود `PhishDetectionMethod` بالعمود`DetectionMethods`. يسمح لنا هذا التبسيط بتوفير المزيد من المعلومات ضمن الأعمدة الجديدة. يتم توفير التعيين أدناه.

    | اسم الجدول | اسم العمود الأصلي | اسم عمود جديد | سبب التغيير
    |--|--|--|--|
    | `EmailAttachmentInfo` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | تضمين المزيد من أساليب الكشف |
    | `EmailAttachmentInfo`  | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | تضمين المزيد من أنواع التهديدات |
    | `EmailEvents` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | تضمين المزيد من أساليب الكشف |
    | `EmailEvents` | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | تضمين المزيد من أنواع التهديدات |


2. في الجداول `EmailAttachmentInfo` ، `EmailEvents` `ThreatNames` تمت إضافة العمود لإعطاء مزيد من المعلومات حول تهديد البريد الإلكتروني. يحتوي هذا العمود على قيم مثل البريد العشوائي أو التصيد الاحتيالي.

3. في جدول [DeviceInfo](advanced-hunting-deviceinfo-table.md) ، `DeviceObjectId` تم استبدال العمود بالعمود `AadDeviceId` استنادا إلى ملاحظات العملاء.

4. في جدول [DeviceEvents](advanced-hunting-deviceevents-table.md) ، تم تعديل العديد من أسماء ActionType لتعكس وصف الإجراء بشكل أفضل. يمكن العثور على تفاصيل التغييرات أدناه.

    | اسم الجدول | اسم ActionType الأصلي | اسم ActionType جديد | سبب التغيير
    |--|--|--|--|
    | `DeviceEvents` | `DlpPocPrintJob` | `FilePrinted` | ملاحظات العملاء |
    | `DeviceEvents` | `UsbDriveMount` | `UsbDriveMounted` | ملاحظات العملاء |
    | `DeviceEvents` | `UsbDriveUnmount` | `UsbDriveUnmounted` | ملاحظات العملاء |
    | `DeviceEvents` | `WriteProcessMemoryApiCall` | `WriteToLsassProcessMemory` | ملاحظات العملاء |

## <a name="march-2021"></a>مارس 2021

`DeviceTvmSoftwareInventoryVulnerabilities` تم إهمال الجدول. استبدالها هي الجداول`DeviceTvmSoftwareInventory`.`DeviceTvmSoftwareVulnerabilities`

## <a name="may-2021"></a>مايو 2021

`AppFileEvents` تم إهمال الجدول. `CloudAppEvents` يتضمن الجدول معلومات كانت موجودة في `AppFileEvents` الجدول، بالإضافة إلى أنشطة أخرى في الخدمات السحابية.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
