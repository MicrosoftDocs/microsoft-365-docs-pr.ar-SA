---
title: حذف ملف من مكتبة الاستجابة المباشرة
description: تعرف على كيفية حذف ملف من مكتبة الاستجابة المباشرة.
keywords: واجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، والحذف من المكتبة
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
ms.openlocfilehash: 97a2a2152a60ff542cb946c4283fe3f26c4b9c8e
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874119"
---
#  <a name="delete-a-file-from-the-live-response-library"></a>حذف ملف من مكتبة الاستجابة المباشرة  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

حذف ملف من مكتبة الاستجابة المباشرة.

## <a name="limitations"></a>القيود

1.  قيود المعدل لواجهة برمجة التطبيقات هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع ["بدء الاستخدام](apis-intro.md)".

| نوع الإذن                    | اذن     | اسم عرض الإذن        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | إدارة مكتبة الاستجابة المباشرة |
| مفوض (حساب العمل أو المؤسسة التعليمية) | Library.Manage | إدارة مكتبة الاستجابة المباشرة |

## <a name="http-request"></a>طلب HTTP

حذف https://api.securitycenter.microsoft.com/api/libraryfiles/{fileName}

## <a name="request-headers"></a>عناوين الطلبات

| الاسم            | نوع   | الوصف               |
|-----------------|--------|---------------------------|
| التخويل   | سلسلة | حامل\<token>\. مطلوب. |

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

-   إذا كان الملف موجودا في المكتبة وتم حذفه بنجاح 204 بلا محتوى.

-   إذا لم يتم العثور على اسم الملف المحدد 404 لم يتم العثور عليه.

## <a name="example"></a>المثال

طلب

فيما يلي مثال على الطلب.

```HTTP
DELETE https://api.securitycenter.microsoft.com/api/libraryfiles/script1.ps1
```

## <a name="related-topic"></a>الموضوع ذو الصلة
- [تشغيل الاستجابة المباشرة](run-live-response.md) 