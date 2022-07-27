---
title: واجهة برمجة تطبيقات مؤشرات القائمة
description: تعرف على كيفية استخدام واجهة برمجة تطبيقات مؤشرات القائمة لاسترداد مجموعة من كافة المؤشرات النشطة في Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة التطبيقات العامة، واجهة برمجة التطبيقات المدعومة، مجموعة المؤشرات
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
ms.openlocfilehash: 1679f5f1b38ac3857b07625a883e267229eda8c6
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051041"
---
# <a name="list-indicators-api"></a>واجهة برمجة تطبيقات مؤشرات القائمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

استرداد مجموعة من كافة [المؤشرات](ti-indicator.md) النشطة.

يدعم [استعلامات OData V4](https://www.odata.org/documentation/).

يتم اعتماد استعلام OData على: `application`و، `createdByDisplayName`و، `expirationTime`و`generateAlert`، و`title`، و، `rbacGroupNames`و، `rbacGroupIds`والخصائص`creationTimeDateTimeUtc``indicatorValue``action``indicatorType``createdBy``severity`.`$filter`
<br>```$stop``` بقيمة قصوى 10000. 
<br>```$skip```.

راجع الأمثلة في [استعلامات OData باستخدام Microsoft Defender لنقطة النهاية](exposed-apis-odata-samples.md)

## <a name="limitations"></a>القيود

1. قيود المعدل لواجهة برمجة التطبيقات هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة. 

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع ["بدء الاستخدام"](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application|Ti.ReadWrite|"مؤشرات القراءة والكتابة"
Application|Ti.ReadWrite.All|'قراءة كافة المؤشرات وكتابتها'
مفوض (حساب العمل أو المؤسسة التعليمية)|Ti.ReadWrite|"مؤشرات القراءة والكتابة"

## <a name="http-request"></a>طلب HTTP

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت، يقوم هذا الأسلوب بإرجاع 200، رمز استجابة موافق مع مجموعة من كيانات [المؤشر](ti-indicator.md) .

> [!NOTE]
> إذا كان التطبيق يحتوي على إذن 'Ti.ReadWrite.All'، فسيتم عرضه على كافة المؤشرات. وإلا، فسيتم عرضه فقط على المؤشرات التي أنشأها.

## <a name="example-1"></a>‏المثال 1‏

### <a name="example-1-request"></a>مثال 1 طلب

فيما يلي مثال على طلب يحصل على كافة المؤشرات

```http
GET https://api.securitycenter.microsoft.com/api/indicators
```

### <a name="example-1-response"></a>مثال 1 للاستجابة

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

## <a name="example-2"></a>مثال 2

### <a name="example-2-request"></a>مثال 2 طلب

فيما يلي مثال على طلب يحصل على كافة المؤشرات مع إجراء "AlertAndBlock" 

```http
GET https://api.securitycenter.microsoft.com/api/indicators?$filter=action+eq+'AlertAndBlock'
```

### <a name="example-2-response"></a>مثال 2 للاستجابة

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
