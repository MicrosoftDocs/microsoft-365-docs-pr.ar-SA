---
title: الحصول على برمجة برمجة API (برمجة برمجة برمجة) لمجموعات أمان الأجهزة
description: استرداد مجموعة من ولايات أمان الجهاز باستخدام Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول، الجهاز، الأمان، الحالة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.custom: api
ms.openlocfilehash: 91df2aab70b2bb8edb46700feefdae59df4ac68b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63571539"
---
# <a name="get-machines-security-states-collection-api"></a>الحصول على API (API) لمجموعات أجهزة الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد مجموعة من الحالات الأمنية للأجهزة.

## <a name="permissions"></a>الأذونات

يحتاج المستخدم إلى أذونات القراءة.

## <a name="http-request"></a>طلب HTTP

```http
GET /testwdatppreview/machinesecuritystates
```

## <a name="request-headers"></a>طلب رؤوس

رأس|القيمة
:---|:---
التخويل|حامل {token}. **مطلوب**.
نوع المحتوى|application/json

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح - 200 موافق.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
GET https://graph.microsoft.com/testwdatppreview/machinesecuritystates
Content-type: application/json
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

يحتوي *"معرّف* الحقل" على "معرّف الجهاز" ويساوي "معرّف *الحقل** في معلومات الأجهزة".

```json
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineSecurityStates",
    "@odata.count":444,
    "@odata.nextLink":"https://graph.microsoft.com/testwdatppreview/machinesecuritystates?$skiptoken=[continuation token]",
    "value":[
        {
            "id":"000050e1b4afeee3742489ede9ad7a3e16bbd9c4",
            "build":14393,
            "revision":2485,
            "architecture":"Amd64",
            "osVersion":"10.0.14393.2485.amd64fre.rs1_release.180827-1809",
            "propertiesRequireAttention":[
                "AntivirusNotReporting",
                "EdrImpairedCommunications"
            ]
        },
        ...
    ]
}
```
