---
title: واجهة برمجة تطبيقات مؤشرات الاستيراد
description: تعرف على كيفية استخدام دفعة استيراد واجهة برمجة تطبيقات المؤشر في Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة التطبيقات المدعومة، الإرسال، ti، المؤشر، التحديث
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
ms.custom: api
ms.openlocfilehash: c2e53fdf2c8786c8f9e605d822024eeef4ed170e
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051591"
---
# <a name="import-indicators-api"></a>واجهة برمجة تطبيقات مؤشرات الاستيراد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

إرسال أو التحديثات دفعة من كيانات [المؤشر](ti-indicator.md).

لا يتم اعتماد تدوين CIDR ل IPs.

## <a name="limitations"></a>القيود

1. قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة.
2. يوجد حد يبلغ 15000 [مؤشر](ti-indicator.md) نشط لكل مستأجر.
3. الحد الأقصى لحجم الدفعة لاستدعاء واجهة برمجة تطبيقات واحد هو 500.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع ["بدء الاستخدام"](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application|Ti.ReadWrite|"مؤشرات القراءة والكتابة"
Application|Ti.ReadWrite.All|'قراءة كافة المؤشرات وكتابتها'
مفوض (حساب العمل أو المؤسسة التعليمية)|Ti.ReadWrite|"مؤشرات القراءة والكتابة"

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators/import
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسله|التطبيق/json. **مطلوب**.

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير كائن JSON بالمعلمات التالية:

المعلمه|نوع|الوصف
:---|:---|:---
المؤشرات|[مؤشر](ti-indicator.md)<القائمة>|قائمة [المؤشرات](ti-indicator.md). **مطلوب**

## <a name="response"></a>استجابه

- إذا نجحت، يقوم هذا الأسلوب بإرجاع 200 - رمز استجابة موافق بقائمة نتائج الاستيراد لكل مؤشر، راجع المثال أدناه.
- إذا لم ينجح: ترجع هذه الطريقة 400 - طلب غير صحيح. يشير الطلب غير الصحيح عادة إلى نص غير صحيح.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

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

## <a name="related-topic"></a>الموضوع ذو الصلة

- [إدارة المؤشرات](manage-indicators.md)
