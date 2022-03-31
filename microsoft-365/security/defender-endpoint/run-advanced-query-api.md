---
title: API للصيد المتقدم
ms.reviewer: ''
description: تعرف على كيفية استخدام API للصيد المتقدم لتشغيل الاستعلامات المتقدمة على Microsoft Defender لنقطة النهاية. تعرف على القيود وشاهد مثالا.
keywords: apis، apis المعتمدة، البحث المتقدم، الاستعلام
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 2e5898c0227128c099c7f0fe1ca99a6d9c8001ef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63578150"
---
# <a name="advanced-hunting-api"></a>API للصيد المتقدم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="limitations"></a>القيود

1. يمكنك فقط تشغيل استعلام على البيانات من آخر 30 يوما.

2. ستتضمن النتائج 100000 صف كحد أقصى.

3. عدد عمليات التنفيذ محدود لكل مستأجر:
   - مكالمات API: ما يصل إلى 45 مكالمة في الدقيقة، ما يصل إلى 1500 مكالمة في الساعة.
   - وقت التنفيذ: 10 دقائق من وقت التشغيل كل ساعة و3 ساعات من وقت التشغيل في اليوم.

4. أقصى وقت تنفيذ لطلب واحد هو 10 دقائق.

5. تمثل الاستجابة 429 الوصول إلى حد الحصة النسبية إما حسب عدد الطلبات أو وحدة المعالجة المركزية (CPU). اقرأ نص الاستجابة لفهم الحد الذي تم الوصول إليه.

6. لا يمكن أن يتجاوز الحد الأقصى لحجم نتيجة الاستعلام لطلب واحد 124 MB. إذا تم تجاوزه، فHTTP 400 طلب غير جيد مع الرسالة "تجاوز تنفيذ الاستعلام حجم النتيجة المسموح به. تحسين الاستعلام من خلال تحديد كمية النتائج والمحاولة مرة أخرى" سيظهر.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|AdvancedQuery.Read.All|"تشغيل الاستعلامات المتقدمة"
مفوض (حساب العمل أو المدرسة)|AdvancedQuery.Read|"تشغيل الاستعلامات المتقدمة"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون للمستخدم دور 'عرض البيانات' AD
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

## <a name="request-headers"></a>طلب رؤوس

رأس|القيمة
:---|:---
التخويل|حامل {token}. **مطلوب**.
نوع المحتوى|application/json

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
:---|:---|:---
استعلام|نص|الاستعلام الذي سيتم تشغيله. **مطلوب**.

## <a name="response"></a>الاستجابة

إذا نجحت هذه الطريقة، ترجع هذه الطريقة 200 موافق، والعائن _QueryResponse_ في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

```json
{
    "Query":"DeviceProcessEvents
|where InitiatingProcessFileName =~ 'powershell.exe'
|where ProcessCommandLine contains 'appdata'
|project Timestamp, FileName, InitiatingProcessFileName, DeviceId
|limit 2"
}
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

> [!NOTE]
> قد يتم اقتطاع كائن الاستجابة الموضح هنا للإيجاز. سيتم إرجاع كل الخصائص من مكالمة فعلية.

```json
{
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
        },
        {
            "Name": "DeviceId",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-02-05T01:10:26.2648757Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        },
        {
            "Timestamp": "2020-02-05T01:10:26.5614772Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        }
    ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مقدمة حول Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)
- [الصيد المتقدم من المدخل](advanced-hunting-query-language.md)
- [الصيد المتقدم باستخدام PowerShell](run-advanced-query-sample-powershell.md)
