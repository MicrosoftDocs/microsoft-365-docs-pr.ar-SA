---
title: جدول DeviceNetworkInfo في مخطط الصيد المتقدم
description: تعرف على معلومات تكوين الشبكة في جدول DeviceNetworkInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و MachinenetworkInfo، و DeviceNetworkInfo، الجهاز، الجهاز، جهاز، mac، ip، المحول، dns، dhcp، البوابة، البث
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
ms.openlocfilehash: 86c087c8a8cdfa80904612625c08ec37ca6813ca
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570646"
---
# <a name="devicenetworkinfo"></a>DeviceNetworkInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية



يحتوي `DeviceNetworkInfo` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول تكوين الشبكات للآلات، بما في ذلك محولات الشبكة وعناوين IP و MAC والشبكات أو المجالات المتصلة. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `NetworkAdapterName` | `string` | اسم محول الشبكة |
| `MacAddress` | `string` | عنوان MAC لمحول الشبكة |
| `NetworkAdapterType` | `string` | نوع محول الشبكة. للحصول على القيم المحتملة، راجع هذا [تعداد](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `NetworkAdapterStatus` | `string` | حالة تشغيل محول الشبكة. للحصول على القيم المحتملة، راجع هذا [تعداد](/dotnet/api/system.net.networkinformation.operationalstatus) |
| `TunnelType` | `string` | بروتوكول النقل، إذا تم استخدام الواجهة لهذا الغرض، على سبيل المثال 6to4 و Teredo و ISATAP و PPTP و SSTP و SSH |
| `ConnectedNetworks` | `string` | الشبكات التي يتصل بها المحول. يحتوي كل صفيف JSON على اسم الشبكة والفئة (عام أو خاص أو مجال) ووصفا وعلما يشير إلى ما إذا كان متصلا بشكل عام بالإنترنت |
| `DnsAddresses` | `string` | عناوين خادم DNS بتنسيق صفيف JSON |
| `IPv4Dhcp` | `string` | عنوان IPv4 للخادم DHCP |
| `IPv6Dhcp` | `string` | عنوان IPv6 للخادم DHCP |
| `DefaultGateways` | `string` | عناوين البوابة الافتراضية بتنسيق صفيف JSON |
| `IPAddresses` | `string` | صفيف JSON الذي يحتوي على كل عناوين IP المعينة إلى المحول، إلى جانب البادرة الخاصة بها على الشبكة الفرعية ومساحة عنوان IP، مثل عام أو خاص أو ارتباط-محلي |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)