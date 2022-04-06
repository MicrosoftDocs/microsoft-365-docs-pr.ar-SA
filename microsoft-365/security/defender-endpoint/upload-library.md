---
title: Upload الملفات إلى مكتبة الاستجابة المباشرة
description: تعرف على كيفية تحميل ملف إلى مكتبة الاستجابة المباشرة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، التحميل إلى المكتبة
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
ms.openlocfilehash: 84ec7e361cccdc886650b0710f738a4315c4db8d
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705593"
---
#  <a name="upload-files-to-the-live-response-library"></a>Upload الملفات إلى مكتبة الاستجابة المباشرة  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

Upload ملف إلى مكتبة استجابة مباشرة.

## <a name="limitations"></a>القيود

1.  الحد الأقصى لحجم الملف هو 20MB.

2.  قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md).


| نوع الإذن                    | الإذن     | اسم عرض الأذونات        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | إدارة مكتبة الاستجابة المباشرة |
| مفوض (حساب العمل أو المدرسة) | Library.Manage | إدارة مكتبة الاستجابة المباشرة |

## <a name="http-request"></a>طلب HTTP

Upload

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>طلب رؤوس

|  الاسم   |    النوع    |       الوصف                         |
|-----------------|--------|--------------------------------|
| التخويل   | سلسلة | \<token>حامل. مطلوب.      |
| نوع المحتوى    | سلسلة | multipart/form-data. مطلوب. |

## <a name="request-body"></a>طلب الحصول على "هيئة"

في نموذج الطلب، زود كائن بيانات النموذج بالمعلمات التالية:

| المعلمة         |     النوع         |       الوصف                                        |
|-----------------------|--------------|------------------------------------------------------------|
| ملف                  | محتوى الملف | الملف الذي سيتم تحميله إلى مكتبة استجابة مباشرة. مطلوب |
| الوصف           | سلسلة       | وصف الملف.                                  |
| ParametersDescription | سلسلة       | (اختياري) المعلمات المطلوبة لتشغيل البرنامج النصي. القيمة الافتراضية هي سلسلة فارغة.                |
| تجاوزIfExists      | منطقي      | (اختياري) ما إذا كنت تريد تجاوز الملف إذا كان موجودا بالفعل. القيمة الافتراضية هي سلسلة فارغة.          |



## <a name="response"></a>الاستجابة

-   إذا نجح هذا الأسلوب، فيرجع رمز الاستجابة 200 - موافق كيان مكتبة الاستجابة المباشرة التي تم تحميلها في هيئة الاستجابة.

-   إذا لم ينجح: ترجع هذه الطريقة 400 - طلب غير جيد.  
    عادة ما يشير الطلب غير الصحيح إلى وجود هيئة غير صحيحة.

## <a name="example"></a>مثال

طلب

فيما يلي مثال للطلب باستخدام حليق.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>موضوع ذو صلة

-  [تشغيل الاستجابة المباشرة](run-live-response.md) 