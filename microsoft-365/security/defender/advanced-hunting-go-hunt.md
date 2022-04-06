---
title: الحصول على معلومات ذات صلة حول كيان باستخدام البحث عن
description: تعرف على كيفية استخدام أداة البحث السريع للاستعلام بسرعة للحصول على معلومات ذات صلة حول كيان أو حدث باستخدام الصيد المتقدم.
keywords: الصيد المتقدم، والحادث، وال pivot، والكيانات، والصيد، والأحداث ذات الصلة، وصيد التهديدات عبر الإنترنت، والبحث، والاستعلام، والتعقب، Microsoft 365، Microsoft 365 Defender
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e14f2d5e35585cf5b0edfe433084fa7c8a1d5280
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63583190"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>البحث بسرعة عن معلومات الكيان أو الحدث باستخدام البحث السريع

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

باستخدام إجراء *البحث* السريع، يمكنك التحقق بسرعة من الأحداث وأنواع الكيانات المختلفة باستخدام قدرات البحث المتقدمة القوية المستندة [إلى الاستعلام.](advanced-hunting-overview.md) يقوم هذا الإجراء تلقائيا بتشغيل استعلام بحث متقدم للعثور على معلومات ذات صلة حول الحدث أو الكيان المحدد.

يتوفر *إجراء البحث* عن الانتقال في مقاطع مختلفة من Defender for Cloud عند عرض تفاصيل الحدث أو الكيان. على سبيل المثال، يمكنك استخدام *البحث من* المقاطع التالية:

- في [صفحة الحادث،](investigate-incidents.md#summary) يمكنك مراجعة تفاصيل حول المستخدمين والأجهزة والعديد من الكيانات الأخرى المقترنة بحادث. عند تحديد كيان، ستحصل على معلومات إضافية بالإضافة إلى الإجراءات المختلفة التي يمكنك اتخاذها على هذا الكيان. في المثال أدناه، يتم تحديد علبة بريد، تعرض تفاصيل حول علبة البريد بالإضافة إلى خيار البحث عن مزيد من المعلومات حول علبة البريد.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="صفحة **علب البريد** مع الخيار **Go hunt** في مدخل Microsoft 365 Defender" lightbox="../../media/go-hunt-1-incident.png":::

- في صفحة الحادث، يمكنك أيضا الوصول إلى قائمة الكيانات ضمن علامة **التبويب** دليل. يوفر تحديد أحد هذه الكيانات خيارا للبحث بسرعة عن معلومات حول هذا الكيان.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="خيار البحث عن جزء من الدليل في صفحة **Incident** في Microsoft 365 Defender المدخل" lightbox="../../media/go-hunt-2-entity.png":::


- عند عرض المخطط الزمني لجهاز، يمكنك تحديد حدث في المخطط الزمني لعرض معلومات إضافية حول هذا الحدث. بمجرد تحديد حدث ما، يمكنك الحصول على خيار البحث عن أحداث أخرى ذات صلة في عملية البحث المتقدم.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="الخيار **البحث عن الأحداث ذات الصلة** على صفحة حدث في علامة التبويب **Timelines** في Microsoft 365 Defender المدخل" lightbox="../../media/go-hunt-3-event.png":::

يتم من خلال تحديد **"** البحث عن" أو "البحث عن الأحداث ذات الصلة" تمرير استعلامات مختلفة، استنادا إلى ما إذا كنت قد حددت كيانا أو حدثا.

## <a name="query-for-entity-information"></a>استعلام للحصول على معلومات الكيان
عند استخدام *البحث* عن استعلام للحصول على معلومات حول مستخدم أو جهاز أو أي نوع آخر من الكيانات، يتحقق الاستعلام من كافة جداول المخططات ذات الصلة لأي أحداث تتضمن ذلك الكيان. لإبقاء النتائج قابلة للإدارة، يتم تحديد نطاق الاستعلام في الفترة الزمنية نفسها تقريبا كال نشاط الأقرب خلال الثلاثين يوما الماضية الذي يتضمن الكيان والمقترن بالحادث.

فيما يلي مثال على استعلام البحث عن جهاز:

```kusto
let selectedTimestamp = datetime(2020-06-02T02:06:47.1167157Z);
let deviceName = "fv-az770.example.com";
let deviceId = "device-guid";
search in (DeviceLogonEvents, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceImageLoadEvents, DeviceEvents, DeviceImageLoadEvents, IdentityLogonEvents, IdentityQueryEvents)
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
and DeviceName == deviceName
// or RemoteDeviceName == deviceName
// or DeviceId == deviceId
| take 100
```
### <a name="supported-entity-types"></a>أنواع الكيانات المعتمدة
يمكنك استخدام *البحث عن بعد* تحديد أي نوع من أنواع الكيانات التالية:

- الملفات
- رسائل البريد الإلكتروني
- مجموعات البريد الإلكتروني
- علب البريد
- المستخدمون
- الأجهزة
- عناوين IP
- عناوين URL

## <a name="query-for-event-information"></a>استعلام للحصول على معلومات الحدث
عند استخدام *البحث* عن استعلام للحصول على معلومات حول حدث مخطط زمني، يتحقق الاستعلام من كافة جداول المخططات ذات الصلة للأحداث الأخرى حول وقت الحدث المحدد. على سبيل المثال، يسرد الاستعلام التالي الأحداث في جداول المخططات المختلفة التي وقعت في الفترة الزمنية نفسها على الجهاز نفسه:

```kusto
// List relevant events 30 minutes before and after selected LogonAttempted event
let selectedEventTimestamp = datetime(2020-06-04T01:29:09.2496688Z);
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
    Timestamp between ((selectedEventTimestamp - 30m) .. (selectedEventTimestamp + 30m))
    and DeviceId == "079ecf9c5798d249128817619606c1c47369eb3e"
| sort by Timestamp desc
| extend Relevance = iff(Timestamp == selectedEventTimestamp, "Selected event", iff(Timestamp < selectedEventTimestamp, "Earlier event", "Later event"))
| project-reorder Relevance
```

## <a name="adjust-the-query"></a>ضبط الاستعلام
مع بعض المعرفة [بلغة الاستعلام](advanced-hunting-query-language.md)، يمكنك ضبط الاستعلام إلى تفضيلاتك. على سبيل المثال، يمكنك ضبط هذا الخط، الذي يحدد حجم النافذة الزمنية:

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

بالإضافة إلى تعديل الاستعلام للحصول على نتائج أكثر صلة، يمكنك أيضا:
- [عرض النتائج كمخططات](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [إنشاء قاعدة اكتشاف مخصصة](custom-detection-rules.md)

>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender for Endpoint. [قم Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender باتباع الخطوات الواردة في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [قواعد الكشف المخصصة](custom-detection-rules.md)
