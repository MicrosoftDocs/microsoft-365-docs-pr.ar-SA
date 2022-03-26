---
title: الدالة DeviceFromIP() في البحث المتقدم Microsoft 365 Defender
description: تعرف على كيفية استخدام الدالة DeviceFromIP() للحصول على الأجهزة التي تم تعيين عنوان IP معين لها
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، مرجع المخطط، kusto، الجهاز، devicefromIP، الدالة، الإثراء
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
ms.openlocfilehash: 4a1f1198c247aefbcbb093d1a5f5105704255692
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570648"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


استخدم الدالة `DeviceFromIP()` في استعلامات الصيد المتقدمة للحصول بسرعة على قائمة الأجهزة التي تم تعيينها إلى عنوان IP معين في وقت معين.[](advanced-hunting-overview.md) 

ترجع هذه الدالة جدولا بالأعمدة التالية:

| عمود | نوع البيانات | الوصف |
|------------|-------------|-------------|
| `IP` | `string` | عنوان IP  |
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |


## <a name="syntax"></a>بناء الجملة

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>الوسيطات

يتم استدعاء هذه الدالة كجزء من استعلام.

- **x**—تكون المعلمة الأولى عادة عمودا في الاستعلام. في هذه الحالة، إنه `IP`العمود المسمى ، عنوان IP الذي تريد رؤية قائمة الأجهزة التي تم تعيينها له. يجب أن يكون عنوان IP محلي. عناوين IP الخارجية غير معتمدة.
- **y**— المعلمة الاختيارية الثانية هي `Timestamp`، التي ترشد الدالة للحصول على أحدث الأجهزة المعينة من وقت معين. إذا لم يتم تحديدها، ترجع الدالة أحدث السجلات المتوفرة.

## <a name="example"></a>مثال


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>الحصول على أحدث الأجهزة التي تم تعيين عناوين IP محددة لها

```kusto
DeviceNetworkEvents 
| limit 100 
| project IP = LocalIP 
| invoke DeviceFromIP()
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
