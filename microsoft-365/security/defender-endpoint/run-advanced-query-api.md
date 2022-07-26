---
title: التتبع المتقدم لواجهات برمجة التطبيقات
ms.reviewer: ''
description: تعلم كيفية استخدام واجهة برمجة تطبيقات التتبع المتقدمة لتشغيل الاستعلامات المتقدمة على Microsoft Defender لنقطة النهاية. تعرف على القيود واطلع على مثال.
keywords: واجهة برمجة التطبيقات، واجهة برمجة التطبيقات المدعومة، التتبع المتقدم، الاستعلام
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
ms.openlocfilehash: 9f361a404ec3f8893ff4573fdc4db29904a5e766
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020616"
---
# <a name="advanced-hunting-api"></a>واجهة برمجة تطبيقات التتبع المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> [!NOTE]
> يمكن لواجهة برمجة التطبيقات هذه الاستعلام عن الجداول التي تنتمي إلى Microsoft Defender لنقطة النهاية فقط. تتطلب الجداول التي تنتمي إلى خدمات Microsoft 365 Defender أخرى استخدام [واجهة برمجة تطبيقات التتبع المتقدمة Microsoft 365 Defender](/microsoft-365/security/defender/api-advanced-hunting).

## <a name="limitations"></a>القيود

1. يمكنك تشغيل استعلام على البيانات فقط من آخر 30 يوما.

2. ستتضمن النتائج 100000 صف كحد أقصى.

3. عدد عمليات التنفيذ محدود لكل مستأجر:
   - مكالمات واجهة برمجة التطبيقات: ما يصل إلى 45 مكالمة في الدقيقة، ما يصل إلى 1500 مكالمة في الساعة.
   - وقت التنفيذ: 10 دقائق من وقت التشغيل كل ساعة و3 ساعات من وقت التشغيل في اليوم.

4. وقت التنفيذ الأقصى لطلب واحد هو 10 دقائق.

5. ستمثل الاستجابة 429 الوصول إلى حد الحصة النسبية إما حسب عدد الطلبات أو حسب وحدة المعالجة المركزية. قراءة نص الاستجابة لفهم الحد الذي تم الوصول إليه.

6. لا يمكن أن يتجاوز الحد الأقصى لحجم نتيجة الاستعلام لطلب واحد 124 ميغابايت. إذا تم تجاوزه، HTTP 400 Bad Request مع الرسالة "تجاوز تنفيذ الاستعلام حجم النتيجة المسموح به. يمكنك تحسين الاستعلام عن طريق الحد من كمية النتائج والمحاولة مرة أخرى".

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application|AdvancedQuery.Read.All|"تشغيل الاستعلامات المتقدمة"
مفوض (حساب العمل أو المؤسسة التعليمية)|AdvancedQuery.Read|"تشغيل الاستعلامات المتقدمة"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون للمستخدم دور "عرض البيانات" AD
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md) لمزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/advancedqueries/run
```

## <a name="request-headers"></a>عناوين الطلبات

عنوان|قيمه
:---|:---
التخويل|حامل {token}. **مطلوب**.
نوع المحتوى|تطبيق/json

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير كائن JSON بالمعلمات التالية:

المعلمه|نوع|الوصف
:---|:---|:---
الاستعلام|النص|الاستعلام المطلوب تشغيله. **مطلوب**.

## <a name="response"></a>استجابه

إذا نجحت، يقوم هذا الأسلوب بإرجاع 200 OK، و _QueryResponse_ object في نص الاستجابة.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

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
> قد يتم اقتطاع كائن الاستجابة المعروض هنا للإيجاز. سيتم إرجاع كافة الخصائص من مكالمة فعلية.

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

- [مقدمة واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [التتبع المتقدم من المدخل](advanced-hunting-query-language.md)
- [الصيد المتقدم باستخدام PowerShell](run-advanced-query-sample-powershell.md)
