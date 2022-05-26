---
title: Microsoft 365 Defender واجهة برمجة تطبيقات التتبع المتقدمة
description: تعرف على كيفية تشغيل استعلامات التتبع المتقدمة باستخدام واجهة برمجة تطبيقات التتبع المتقدمة Microsoft 365 Defender
keywords: التتبع المتقدم، واجهات برمجة التطبيقات، واجهة برمجة التطبيقات، M365 Defender، Microsoft 365 Defender
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
ms.openlocfilehash: e485bcf400dbaf36c63e3a0ed8677c9bf7c8f23a
ms.sourcegitcommit: 852075d8d8a4ca052f69e854396d1565ef713500
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/26/2022
ms.locfileid: "65692750"
---
# <a name="microsoft-365-defender-advanced-hunting-api"></a>Microsoft 365 Defender واجهة برمجة تطبيقات التتبع المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

[التتبع المتقدم](advanced-hunting-overview.md) هو أداة تتبع المخاطر تستخدم [استعلامات تم إنشاؤها خصيصا](advanced-hunting-query-language.md) لفحص بيانات الحدث في Microsoft 365 Defender خلال ال 30 يوما الماضية. يمكنك استخدام استعلامات التتبع المتقدمة لفحص النشاط غير العادي، والكشف عن التهديدات المحتملة، وحتى الاستجابة للهجمات. تسمح لك واجهة برمجة تطبيقات التتبع المتقدمة بالاستعلام برمجيا عن بيانات الحدث.

## <a name="quotas-and-resource-allocation"></a>الحصص النسبية وتخصيص الموارد

تتعلق الشروط التالية بكافة الاستعلامات.

1. تستكشف الاستعلامات البيانات وتعيدها من ال 30 يوما الماضية.
2. يمكن أن ترجع النتائج ما يصل إلى 100000 صف.
3. يمكنك إجراء ما يصل إلى 45 مكالمة في الدقيقة لكل مستأجر.
4. يتم حظر الاستعلامات إذا وصل المستأجر إلى 100٪ حتى بعد دورة ال 15 دقيقة التالية.
5. إذا تم تشغيل طلب واحد لأكثر من 10 دقائق، فستنقضى المهلة وترجع رسالة خطأ.
6. `429` يشير رمز استجابة HTTP إلى أنك وصلت إلى حصة نسبية، إما حسب عدد الطلبات المرسلة، أو حسب وقت التشغيل المخصص. اقرأ نص الاستجابة لفهم الحد الذي وصلت إليه. 

> [!NOTE]
> جميع الحصص النسبية المذكورة أعلاه (على سبيل المثال 15 مكالمة لكل دقيقة) على نطاق المستأجر. هذه الحصص النسبية هي الحد الأدنى.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة تطبيقات التتبع المتقدمة. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [Access Microsoft 365 Defender Protection APIs](api-access.md).

نوع الإذن | اذن | اسم عرض الإذن
-|-|-
Application | AdvancedWating.Read.All| تشغيل الاستعلامات المتقدمة
مفوض (حساب العمل أو المؤسسة التعليمية) | AdvancedWating.Read | تشغيل الاستعلامات المتقدمة

>[!Note]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
>- يحتاج المستخدم إلى الحصول على دور "عرض البيانات" AD
>- يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة.

## <a name="http-request"></a>طلب HTTP

```HTTP
POST https://api.security.microsoft.com/api/advancedhunting/run
```

## <a name="request-headers"></a>عناوين الطلبات

عنوان | قيمه
-|-
التخويل | ملاحظة {token} للحامل **: مطلوبة**
نوع المحتوى | تطبيق/json

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير كائن JSON بالمعلمات التالية:

المعلمه | نوع | الوصف
-|-|-
الاستعلام | النص | الاستعلام المطلوب تشغيله. **(مطلوب)**

## <a name="response"></a>استجابه

إذا نجحت، سيتم إرجاع `200 OK`هذا الأسلوب، وعنصر _QueryResponse_ في نص الاستجابة.

يحتوي كائن الاستجابة على ثلاث خصائص من المستوى الأعلى:

1. الإحصائيات - قاموس إحصائيات أداء الاستعلام.
2. مخطط - مخطط الاستجابة، قائمة بأزواج Name-Type لكل عمود.
3. النتائج - قائمة بأحداث التتبع المتقدمة.

## <a name="example"></a>المثال

في المثال التالي، يرسل المستخدم الاستعلام أدناه ويتلقى كائن استجابة واجهة برمجة التطبيقات الذي يحتوي على `Stats`، `Schema`و `Results`.

### <a name="query"></a>الاستعلام

```json
{
    "Query":"DeviceProcessEvents | where InitiatingProcessFileName =~ \"powershell.exe\" | project Timestamp, FileName, InitiatingProcessFileName | order by Timestamp desc | limit 2"
}

```

### <a name="response-object"></a>كائن الاستجابة

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

- [الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-access.md)
- [التعرف على حدود واجهة برمجة التطبيقات والترخيص](api-terms.md)
- [فهم رموز الأخطاء](api-error-codes.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
