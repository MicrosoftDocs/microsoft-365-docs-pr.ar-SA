---
title: جدول DeviceInfo في مخطط الصيد المتقدم
description: تعرف على نظام التشغيل واسم الكمبيوتر ومعلومات الجهاز الأخرى في جدول DeviceInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و machineInfo، و DeviceInfo، والجهاز، والجهاز، و OS، و النظام الأساسي، والمستخدمون
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
ms.openlocfilehash: 245a9aa11bcaf10ba6f3b8fe0fe429267a355560
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63575769"
---
# <a name="deviceinfo"></a>DeviceInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يحتوي `DeviceInfo` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول الأجهزة في المؤسسة، بما في ذلك إصدار نظام التشغيل والمستخدمين النشطين واسم الكمبيوتر. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `ClientVersion` | `string` | إصدار عامل نقطة النهاية أو المستشعر الذي يعمل على الجهاز |
| `PublicIP` | `string` | عنوان IP عام يستخدمه الجهاز المكبس للاتصال بالخدمة في Microsoft Defender for Endpoint. قد يكون هذا هو عنوان IP للجهاز نفسه أو جهاز NAT أو وكيل |
| `OSArchitecture` | `string` | هندسة نظام التشغيل الذي يعمل على الجهاز |
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز. يشير ذلك إلى أنظمة تشغيل محددة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 Windows 10 Windows 7. |
| `OSBuild` | `string` | إصدار إصدار نظام التشغيل الذي يتم تشغيله على الجهاز |
| `IsAzureADJoined` | `boolean` | مؤشر منطقي حول ما إذا كان الجهاز منضما إلى Azure Active Directory |
| `AadDeviceId` | `string` | معرف فريد للجهاز في Azure AD |
| `LoggedOnUsers` | `string` | قائمة بجميع المستخدمين الذين تم تسجيل دخولهم إلى الجهاز في وقت الحدث بتنسيق صفيف JSON |
| `RegistryDeviceTag` | `string` | علامة الجهاز المضافة من خلال السجل |
| `OSVersion` | `string` | إصدار نظام التشغيل الذي يتم تشغيله على الجهاز |
| `MachineGroup` | `string` | مجموعة الجهاز للجهاز. يتم استخدام هذه المجموعة بواسطة عنصر تحكم الوصول المستند إلى الدور لتحديد الوصول إلى الجهاز |
| `ReportId` | `long` | معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود بالتزامن مع عمودي DeviceName و Timestamp |
| `OnboardingStatus` | `string` | تشير إلى ما إذا كان الجهاز قيد التشغيل حاليا أم لا في Microsoft Defender لنقطة النهاية أو إذا كان الجهاز غير معتمد |
|`AdditionalFields` | `string` | معلومات إضافية حول الحدث بتنسيق صفيف JSON |
|`DeviceCategory` | `string` | تصنيف أوسع نطاقا يعمل على مجموعات أنواع أجهزة معينة ضمن الفئات التالية: نقطة النهاية، جهاز الشبكة، IoT، غير معروف |
|`DeviceType` | `string` | نوع الجهاز استنادا إلى الغرض والوظائف، مثل جهاز الشبكة أو محطة العمل أو الخادم أو الهاتف المحمول أو وحدة التحكم بالألعاب أو الطابعة |
|`DeviceSubType` | `string` | تعديل إضافي لأنواع معينة من الأجهزة، على سبيل المثال، يمكن أن يكون الجهاز المحمول كمبيوتر لوحي أو هاتف ذكي؛ متوفر فقط إذا كان اكتشاف الجهاز يعثر على معلومات كافية حول هذه السمة |
|`Model` | `string` | اسم النموذج أو رقم المنتج من المورد أو الشركة المصنعة، متوفر فقط إذا كان اكتشاف الجهاز يعثر على معلومات كافية حول هذه السمة |
|`Vendor` | `string` | اسم مورد المنتج أو الشركة المصنعة، متوفر فقط إذا كان اكتشاف الجهاز يعثر على معلومات كافية حول هذه السمة |
|`OSDistribution` | `string` | توزيع النظام الأساسي ل OS، مثل أنظمة Ubuntu أو RedHat ل Linux الأساسية |
|`OSVersionInfo` | `string` | معلومات إضافية حول إصدار نظام التشغيل، مثل الاسم الشائع أو اسم الرمز أو رقم الإصدار |
|`MergedDeviceIds` | `string` | هويات الجهاز السابقة التي تم تعيينها إلى الجهاز نفسه |
|`MergedToDeviceId` | `string` | أحدث معرّف جهاز تم تعيينه إلى جهاز |

يوفر `DeviceInfo` الجدول معلومات الجهاز استنادا إلى نبضات القلب، وهي تقارير دورية أو إشارات من جهاز. كل خمس عشرة دقيقة، يرسل الجهاز دقات قلب جزئية تحتوي على سمات متغيرة بشكل متكرر مثل `LoggedOnUsers`. مرة واحدة في اليوم، يتم إرسال دقات قلب كاملة تحتوي على سمات الجهاز.

يمكنك استخدام الاستعلام النموذجي التالي للحصول على أحدث حالة لجهاز:

```kusto
// Get latest information on user/device
DeviceInfo
| where DeviceName == "example" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId 
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
