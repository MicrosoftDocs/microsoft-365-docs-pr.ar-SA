---
title: API لمؤشرات الاستيراد
description: تعرف على كيفية استخدام دفعة استيراد مؤشر API في Microsoft Defender لنقطة النهاية.
keywords: apis، apis المعتمدة، إرسال، ti، مؤشر، تحديث
ms.prod: w10
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
ms.custom: api
ms.openlocfilehash: 7306489e537e583055e037ce9d8ce04add248844
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570506"
---
# <a name="import-indicators-api"></a>API لمؤشرات الاستيراد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إرسال دفعة من كيانات [المؤشر](ti-indicator.md) أو تحديثها.

لا يتم دعم "CIDR" ل IPs.

## <a name="limitations"></a>القيود

1. حدود السعر ل API هذه هي 30 مكالمة في الدقيقة.
2. يوجد حد 15000 مؤشر [نشط لكل](ti-indicator.md) مستأجر.
3. الحد الأقصى لحجم الدفعة لمكاتب API واحد هو 500.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Ti.ReadWrite|"مؤشرات القراءة والكتابة"
Application|Ti.ReadWrite.All|"قراءة كل المؤشرات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Ti.ReadWrite|"مؤشرات القراءة والكتابة"

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
:---|:---|:---
المؤشرات|مؤشر<[القائمة](ti-indicator.md)>|قائمة [المؤشرات](ti-indicator.md). **مطلوب**

## <a name="response"></a>الاستجابة

- إذا نجح هذا الأسلوب، فيرجع رمز الاستجابة 200 - موافق مع قائمة بنتائج الاستيراد لكل مؤشر، راجع المثال أدناه.
- إذا لم ينجح: يتم إرجاع هذا الأسلوب 400 - طلب غير جيد. عادة ما يشير الطلب غير الصحيح إلى وجود هيئة غير صحيحة.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

```json
{
    "Indicators":
    [
        {
            "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "title": "demo",
            "application": "demo-test",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Informational",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": ["group1", "group2"]
        },
        {
            "indicatorValue": "2233223322332233223322332233223322332233223322332233223322332222",
            "indicatorType": "FileSha256",
            "title": "demo2",
            "application": "demo-test2",
            "expirationTime": "2021-12-12T00:00:00Z",
            "action": "Alert",
            "severity": "Medium",
            "description": "demo2",
            "recommendedActions": "nothing",
            "rbacGroupNames": []
        }
    ]
}
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "value": [
        {
            "id": "2841",
            "indicator": "220e7d15b011d7fac48f2bd61114db1022197f7f",
            "isFailed": false,
            "failureReason": null
        },
        {
            "id": "2842",
            "indicator": "2233223322332233223322332233223322332233223322332233223322332222",
            "isFailed": false,
            "failureReason": null
        }
    ]
}
```

## <a name="related-topic"></a>موضوع ذو صلة

- [إدارة المؤشرات](manage-indicators.md)
