---
title: الدالة AssignedIPAddresses() في الصيد المتقدم Microsoft 365 Defender
description: تعرف على كيفية استخدام الدالة AssignedIPAddresses() للحصول على أحدث عناوين IP المعينة لجهاز
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، مرجع المخطط، kusto، FileProfile، ملف تعريف الملف، الدالة، الإثراء
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
ms.openlocfilehash: b82a079a476ee6ed3d5465b52bca381cd49746b5
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63571449"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

استخدم الدالة `AssignedIPAddresses()` في [استعلامات](advanced-hunting-overview.md) البحث المتقدمة للحصول بسرعة على أحدث عناوين IP التي تم تعيينها إلى جهاز. إذا حددت وسيطة timestamp، فإن هذه الدالة تحصل على أحدث عناوين IP في الوقت المحدد. 

ترجع هذه الدالة جدولا بالأعمدة التالية:

| عمود | نوع البيانات | الوصف |
|------------|-------------|-------------|
| `Timestamp` | `datetime` | آخر مرة تم فيها ملاحظة الجهاز باستخدام عنوان IP |
| `IPAddress` | `string` | عنوان IP المستخدم من قبل الجهاز |
| `IPType` | `string` | تشير إلى ما إذا كان عنوان IP عنوانا عام أو خاصا |
| `NetworkAdapterType` | `int` | نوع محول الشبكة المستخدم بواسطة الجهاز الذي تم تعيين عنوان IP له. للحصول على القيم المحتملة، راجع هذا [تعداد](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | `int` | الشبكات التي يتصل بها المحول مع عنوان IP المعين. يحتوي كل صفيف JSON على اسم الشبكة والفئة (عام أو خاص أو مجال) ووصفا وعلما يشير إلى ما إذا كان متصلا بشكل عام بالإنترنت |

## <a name="syntax"></a>بناء الجملة

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>الوسيطات

- **x** —`DeviceId` أو `DeviceName` قيمة تحدد الجهاز
- **y** —`Timestamp` قيمة (datetime) التي ترشد الدالة للحصول على أحدث عناوين IP المعينة من وقت معين. إذا لم يتم تحديدها، ترجع الدالة أحدث عناوين IP.

## <a name="examples"></a>أمثلة

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>الحصول على قائمة عناوين IP المستخدمة بواسطة جهاز منذ 24 ساعة

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>الحصول على عناوين IP التي يستخدمها جهاز والعثور على الأجهزة التي تتواصل معه
يستخدم هذا الاستعلام الدالة `AssignedIPAddresses()` للحصول على عناوين IP معينة للجهاز (`example-device-name`) في أو قبل تاريخ معين (`example-date`). ثم يستخدم عناوين IP للعثور على اتصالات الجهاز الذي تبدأه أجهزة أخرى. 

```kusto
let Date = datetime(example-date);
let DeviceName = "example-device-name";
// List IP addresses used on or before the specified date
AssignedIPAddresses(DeviceName, Date)
| project DeviceName, IPAddress, AssignedTime = Timestamp 
// Get all network events on devices with the assigned IP addresses as the destination addresses
| join kind=inner DeviceNetworkEvents on $left.IPAddress == $right.RemoteIP
// Get only network events around the time the IP address was assigned
| where Timestamp between ((AssignedTime - 1h) .. (AssignedTime + 1h))
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)