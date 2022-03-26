---
title: الحصول على API خريطة CVE-KB
description: تعرف على كيفية استخدام API لخريطة Get CVE-KB لاسترداد خريطة CVEs إلى KBs وتفاصيل CVE في Microsoft Defender ل Endpoint.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول على، cve، kb
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
ROBOTS: NOINDEX
ms.technology: mde
ms.custom: api
ms.openlocfilehash: d0672804d0d2a8221480fe76e4237114a88f4cfb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573314"
---
# <a name="get-cve-kb-map-api"></a>الحصول على API خريطة CVE-KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد خريطة ل CVEs إلى تفاصيل KBs و CVE.

## <a name="permissions"></a>الأذونات

يحتاج المستخدم إلى أذونات القراءة.

## <a name="http-request"></a>طلب HTTP

```http
GET /testwdatppreview/cvekbmap
```

## <a name="request-headers"></a>طلب رؤوس

رأس|القيمة
:---|:---
التخويل|حامل {token}. **مطلوب**.
نوع المحتوى|application/json

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح وخريطة موجودة - 200 موافق.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب:

```http
GET https://graph.microsoft.com/testwdatppreview/CveKbMap
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة:

```json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#CveKbMap",
    "@odata.count": 4168,
    "value": [
        {
            "cveKbId": "CVE-2015-2482-3097617",
            "cveId": "CVE-2015-2482",
            "kbId":"3097617",
            "title": "Cumulative Security Update for Internet Explorer",
            "severity": "Critical"
        },
    ...
}
```
