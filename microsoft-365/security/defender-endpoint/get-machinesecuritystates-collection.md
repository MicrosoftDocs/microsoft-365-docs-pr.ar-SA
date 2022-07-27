---
title: الحصول على واجهة برمجة تطبيقات مجموعة حالات أمان الأجهزة
description: استرداد مجموعة من حالات أمان الجهاز باستخدام Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، الحصول، الجهاز، الأمان، الحالة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.openlocfilehash: c7750868c557ba4ebb4c37584b69e710ae1a449b
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051437"
---
# <a name="get-machines-security-states-collection-api"></a>الحصول على واجهة برمجة تطبيقات مجموعة حالات أمان الأجهزة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد مجموعة من حالات أمان الأجهزة.

## <a name="permissions"></a>الأذونات

يحتاج المستخدم إلى أذونات القراءة.

## <a name="http-request"></a>طلب HTTP

```http
GET /testwdatppreview/machinesecuritystates
```

## <a name="request-headers"></a>عناوين الطلبات

عنوان|قيمه
:---|:---
التخويل|حامل {token}. **مطلوب**.
نوع المحتوى|تطبيق/json

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت - 200 موافق.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

فيما يلي مثال على الطلب.

```http
GET https://graph.microsoft.com/testwdatppreview/machinesecuritystates
Content-type: application/json
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

يحتوي *معرف* الحقل على معرف الجهاز ومساوي *لمعرف* الحقل* في معلومات الأجهزة.

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
