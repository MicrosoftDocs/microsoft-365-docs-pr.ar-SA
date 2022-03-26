---
title: API لمؤشرات القائمة
description: تعرف على كيفية استخدام API لمؤشرات القائمة لاسترداد مجموعة من كافة المؤشرات النشطة في Microsoft Defender لنقطة النهاية.
keywords: apis، api العامة، apis المعتمدة، مجموعة المؤشرات
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: adc3cfecba10431a909b72f875442d80b6638f03
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570667"
---
# <a name="list-indicators-api"></a>API لمؤشرات القائمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد مجموعة من كافة [المؤشرات النشطة](ti-indicator.md).

يدعم [استعلامات OData V4](https://www.odata.org/documentation/).

يتم دعم استعلام `$filter` OData على الخصائص: `application`و و `createdByDisplayName`و `expirationTime`و `generateAlert``rbacGroupNames``severity` `action``creationTimeDateTimeUtc``indicatorValue``createdBy``title``rbacGroupIds``indicatorType`.
<br>```$stop``` مع الحد الأقصى لقيمة 10000. 
<br>```$skip```.

الاطلاع على أمثلة على [استعلامات OData باستخدام Microsoft Defender لنقطة النهاية](exposed-apis-odata-samples.md)

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة. 

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Ti.ReadWrite|"مؤشرات القراءة والكتابة"
Application|Ti.ReadWrite.All|"قراءة كل المؤشرات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Ti.ReadWrite|"مؤشرات القراءة والكتابة"

## <a name="http-request"></a>طلب HTTP

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع رمز الاستجابة 200، موافق مع [مجموعة من كيانات](ti-indicator.md) المؤشر.

> [!NOTE]
> إذا كان التطبيق لديه الإذن 'Ti.ReadWrite.All'، سيتم عرضه لكل المؤشرات. وإلا، سيتم عرضها للمؤشرات التي تم إنشاؤها فقط.

## <a name="example-1"></a>المثال 1

### <a name="example-1-request"></a>مثال 1 لطلب

فيما يلي مثال لطلب يحصل على كل المؤشرات

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

### <a name="example-1-response"></a>مثال 1 استجابة

فيما يلي مثال على الاستجابة.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "995",
            "indicatorValue": "12.13.14.15",
            "indicatorType": "IpAddress",
            "action": "Alert",
            "application": "demo-test",
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T11:15:35.3688259Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "test",
            "rbacGroupNames": []
        },
        {
            "id": "996",
            "indicatorValue": "220e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```

## <a name="example-2"></a>المثال 2

### <a name="example-2-request"></a>مثال 2 لطلب

فيما يلي مثال لطلب يحصل على كل المؤشرات مع إجراء 'AlertAndBlock' 

```http
GET https://api.securitycenter.microsoft.com/api/indicators?$filter=action+eq+'AlertAndBlock'
```

### <a name="example-2-response"></a>مثال 2 استجابة

فيما يلي مثال على الاستجابة.

```json
HTTP/1.1 200 Ok
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Indicators",
    "value": [
        {
            "id": "997",
            "indicatorValue": "111e7d15b0b3d7fac48f2bd61114db1022197f7f",
            "indicatorType": "FileSha1",
            "action": "AlertAndBlock",
            "application": null,
            "source": "TestPrdApp",
            "sourceType": "AadApp",
            "title": "test",
            "creationTimeDateTimeUtc": "2018-10-24T10:54:23.2009016Z",
            "createdBy": "45097602-1234-5678-1234-9f453233e62c",
            "expirationTime": "2020-12-12T00:00:00Z",
            "lastUpdateTime": "2019-10-24T10:54:23.2009016Z",
            "lastUpdatedBy": TestPrdApp,
            "severity": "Informational",
            "description": "test",
            "recommendedActions": "TEST",
            "rbacGroupNames": [ "Group1", "Group2" ]
        }
        ...
    ]
}
```
