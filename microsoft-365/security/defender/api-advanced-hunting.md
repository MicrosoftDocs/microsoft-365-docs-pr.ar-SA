---
title: Microsoft 365 Defender المتقدمة لصيد API
description: تعرف على كيفية تشغيل استعلامات البحث المتقدمة باستخدام Microsoft 365 Defender API المتقدمة
keywords: البحث المتقدم، واجهات برمجة التطبيقات، api، M365 Defender، Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 05957fcf7cf2b3b03fbc757fc8b21e67156b285a
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500816"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender المتقدمة لصيد API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

[إن الصيد](advanced-hunting-overview.md) المتقدم هو أداة بحث عن المخاطر تستخدم استعلامات تم إنشاءها بشكل خاص لفحص بيانات الأحداث خلال 30 يوما في Microsoft 365 Defender.[](advanced-hunting-query-language.md) يمكنك استخدام استعلامات البحث المتقدمة لفحص النشاط غير المعتاد، والكشف عن التهديدات المحتملة، وحتى الاستجابة للهجمات. تسمح لك API للصيد المتقدم باستعلام بيانات الأحداث بشكل مبرمجة.

## <a name="quotas-and-resource-allocation"></a>الحصص النسبية وتخصيص الموارد

تتعلق الشروط التالية بكل الاستعلامات.

1. تستكشف الاستعلامات البيانات من الأيام الثلاثين الماضية وإرجاعها.
2. يمكن أن تظهر النتائج ما يصل إلى 100000 صف.
3. يمكنك إجراء ما يصل إلى 45 مكالمة لكل دقيقة لكل مستأجر.
4. يتم حظر الاستعلامات إذا وصل المستأجر إلى 100٪ حتى بعد دورة ال 15 دقيقة التالية.
5. إذا تم تشغيل طلب واحد لأكثر من 10 دقائق، سيتم ا والوقت الذي سيتم فيه إرجاع خطأ.
6. يشير `429` رمز استجابة HTTP إلى أنك وصلت إلى الحصة النسبية، إما حسب عدد الطلبات المرسلة أو حسب وقت التشغيل المخصص. اقرأ نص الاستجابة لفهم الحد الذي وصلت إليه. 

> [!NOTE]
> تكون كل الحصص النسبية المذكورة أعلاه (على سبيل المثال 15 مكالمة لكل دقيقة) لكل حجم مستأجر. هذه الحصص النسبية هي الحد الأدنى.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء API للصيد المتقدم. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات للحماية](api-access.md)

نوع الإذن | الإذن | اسم عرض الأذونات
-|-|-
Application | AdvancedQuery.Read.All| تشغيل الاستعلامات المتقدمة
مفوض (حساب العمل أو المدرسة) | AdvancedQuery.Read | تشغيل الاستعلامات المتقدمة

>[!Note]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
>- يجب أن يكون للمستخدم دور 'عرض البيانات' AD
>- يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة.

## <a name="http-request"></a>طلب HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>طلب رؤوس

رأس | القيمة
-|-
التخويل | حامل {token} **ملاحظة: مطلوب**
نوع المحتوى | application/json

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة | النوع | الوصف
-|-|-
استعلام | نص | الاستعلام الذي سيتم تشغيله. **ملاحظة: مطلوب**

## <a name="response"></a>الاستجابة

إذا نجح ذلك، سيتم إرجاع هذه الطريقة `200 OK`، وسيرجع كائن _QueryResponse_ في هيئة الاستجابة.

يحتوي كائن الاستجابة على ثلاث خصائص المستوى الأعلى:

1. Stats - قاموس إحصائيات أداء الاستعلام.
2. مخطط - مخطط الاستجابة، قائمة Name-Type لكل عمود.
3. النتائج - قائمة بالأحداث المتقدمة للصيد.

## <a name="example"></a>مثال

في المثال التالي، يرسل المستخدم الاستعلام أدناه ويتلقى كائن استجابة API يحتوي `Stats`على و `Schema`و `Results`.

### <a name="query"></a>استعلام

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>كائن استجابة

```json
{
    "Stats": {
        "ExecutionTime": 4.621215,
        "resource_usage": {
            "cache": {
                "memory": {
                    "hits": 773461,
                    "misses": 4481,
                    "total": 777942
                },
                "disk": {
                    "hits": 994,
                    "misses": 197,
                    "total": 1191
                }
            },
            "cpu": {
                "user": "00:00:19.0468750",
                "kernel": "00:00:00.0156250",
                "total cpu": "00:00:19.0625000"
            },
            "memory": {
                "peak_per_node": 236822432
            }
        },
        "dataset_statistics": [
            {
                "table_row_count": 2,
                "table_size": 102
            }
        ]
    },
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-08-30T06:38:35.7664356Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        },
        {
            "Timestamp": "2020-08-30T06:38:30.5163363Z",
            "FileName": "conhost.exe",
            "InitiatingProcessFileName": "powershell.exe"
        }
    ]
}
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [التعرف على حدود API والترخيص](api-terms.md)
- [فهم رموز الخطأ](api-error-codes.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
