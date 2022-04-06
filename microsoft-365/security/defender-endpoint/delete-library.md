---
title: حذف ملف من مكتبة الاستجابة المباشرة
description: تعرف على كيفية حذف ملف من مكتبة الاستجابة المباشرة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحذف من المكتبة
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
ms.openlocfilehash: 23625c8b7160d604df5f3a8b1b1387fc31027acf
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705553"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>حذف ملف من مكتبة الاستجابة المباشرة  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

حذف ملف من مكتبة الاستجابة المباشرة.

## <a name="limitations"></a>القيود

1.  قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md).

| نوع الإذن                    | الإذن     | اسم عرض الأذونات        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | إدارة مكتبة الاستجابة المباشرة |
| مفوض (حساب العمل أو المدرسة) | Library.Manage | إدارة مكتبة الاستجابة المباشرة |

## <a name="http-request"></a>طلب HTTP

DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>طلب رؤوس

| الاسم            | النوع   | الوصف               |
|-----------------|--------|---------------------------|
| التخويل   | سلسلة | حامل\<token>\. مطلوب. |

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

-   إذا كان الملف موجودا في المكتبة وحذف بنجاح 204 بلا محتوى.

-   إذا لم يتم العثور على اسم الملف المحدد 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

طلب

فيما يلي مثال على الطلب.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>موضوع ذو صلة
- [تشغيل الاستجابة المباشرة](run-live-response.md) 