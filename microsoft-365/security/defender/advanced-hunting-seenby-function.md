---
title: الدالة SeenBy() في التتبع المتقدم Microsoft 365 Defender
description: تعرف على كيفية استخدام الدالة SeenBy() للبحث عن الأجهزة الملحقة التي اكتشفت جهازا معينا
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، SeenBy، اكتشاف الجهاز، الوظيفة، الإثراء
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
ms.openlocfilehash: 4a17efeeaf62ddcf63988f055ca93b536e68c962
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174981"
---
# <a name="seenby"></a>SeenBy()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

`SeenBy()` يتم استدعاء الدالة لمشاهدة قائمة بالأجهزة المضمنة التي شاهدت جهازا معينا باستخدام ميزة اكتشاف الجهاز.

ترجع هذه الدالة جدولا يحتوي على العمود التالي:

| العمود | نوع البيانات | الوصف |
|------------|---------------|-------------|
| `DeviceId` | `string` | معرف فريد للجهاز في الخدمة |


## <a name="syntax"></a>بناء الجمله

```kusto
invoke SeenBy(x)
```

- حيث **x** هو معرف الجهاز الذي تهمه

>[!TIP]
> ستعرض وظائف الإثراء معلومات تكميلية فقط عند توفرها. إن توفر المعلومات متنوع ويعتمد على الكثير من العوامل. تأكد من مراعاة هذا عند استخدام SeenBy() في الاستعلامات أو في إنشاء عمليات الكشف المخصصة. للحصول على أفضل النتائج، نوصي باستخدام الدالة SeenBy() مع جدول DeviceInfo.

### <a name="example-obtain-list-of-onboarded-devices-that-have-seen-a-device"></a>مثال: الحصول على قائمة بالأجهزة الملحقة التي شاهدت جهازا

```kusto
DeviceInfo 
| where OnboardingStatus <> "Onboarded" 
| limit 100 | invoke SeenBy()
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [الحصول على المزيد من أمثلة الاستعلام](advanced-hunting-shared-queries.md)
