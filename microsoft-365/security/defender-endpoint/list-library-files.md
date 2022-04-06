---
title: ملفات مكتبة القائمة
description: تعرف على كيفية سرد ملفات مكتبة الاستجابة المباشرة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، الأجهزة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.collection:
- M365-security-compliance
ms.topic: reference
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 9c9bf11856cf518a1cd387b88a3b70dc4a34cc91
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705573"
---
#  <a name="list-library-files"></a>ملفات مكتبة القائمة 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

سرد ملفات مكتبة الاستجابة المباشرة.

## <a name="limitations"></a>القيود

1.  قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md).

|نوع الإذن                       |      الإذن          |  اسم عرض الأذونات | 
|-----------------|--------|---------------------------|  
| Application                        | Library.Manage | إدارة مكتبة الاستجابة المباشرة |
| مفوض (حساب العمل أو المدرسة) | Library.Manage | إدارة مكتبة الاستجابة المباشرة |

## <a name="http-request"></a>طلب HTTP

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>طلب رؤوس

| الاسم         |      النوع                     | الوصف
|-----------------|--------|---------------------------|
| التخويل   | سلسلة | حامل {token}. مطلوب. |

## <a name="request-body"></a>طلب الحصول على "هيئة"
فارغ

## <a name="response"></a>الاستجابة 
إذا نجح هذا الأسلوب، فيرجع رمز الاستجابة 200 - موافق مع مجموعة من كيانات ملفات مكتبة الاستجابة المباشرة.

## <a name="example"></a>مثال

**طلب**

فيما يلي مثال على طلب يحصل على كل ملفات مكتبة الاستجابة المباشرة

```HTTP
GET https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```JSON
HTTP/1.1 200 Ok
Content-type: application/json
{
"\@odata.context": "https://api.securitycenter.microsoft.com
/api/\$metadata\#LibraryFiles",
"value": [
    {
    "fileName": "script1.ps1",
    "sha256": "6e212a0db618507c44e4ec8ee7499dfef7e5767e5f8d31144df3b96fd1145caf",
    "description": null,
    "creationTime": "2019-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2019-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": true,
    "parametersDescription": "test"
    },
    {
    "fileName": "script.sh",
    "sha256": "d0f3e3b0641dbf88ee39c822516e81a909d1d06d22341dd9b1f12aa5e5c027a2",
    "description": null,
    "creationTime": "2018-10-24T11:15:35.3688259Z",
    "lastUpdatedTime": "2018-10-24T11:15:35.3688259Z",
    "createdBy": "username",
    "hasParameters": false
    },
    {
    "fileName": "memdump.exe",
    "sha256": "fa70b87730290c0d30fe255d1dfb65de82f96286ebfeeb1d88ed3cc831329825",
    "description": "Process memory dump",
    "creationTime": "2018-10-24T10:54:23.2009016Z",
    "lastUpdatedTime": "2018-10-24T10:54:23.2009016Z",
    "createdBy": "admin",
    "hasParameters": false
    }
]
}
```


## <a name="related-topic"></a>موضوع ذو صلة
- [تشغيل الاستجابة المباشرة](run-live-response.md) 