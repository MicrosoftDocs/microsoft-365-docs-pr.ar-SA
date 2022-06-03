---
title: Upload الملفات إلى مكتبة الاستجابة المباشرة
description: تعرف على كيفية تحميل ملف إلى مكتبة الاستجابة المباشرة.
keywords: واجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، وتحميلها إلى المكتبة
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
ms.openlocfilehash: 8e0bc9ca78a7e0baad7c07e73790215618aff9ab
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873722"
---
#  <a name="upload-files-to-the-live-response-library"></a>Upload الملفات إلى مكتبة الاستجابة المباشرة  

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

[!include[Prerelease information](../../includes/prerelease.md)]

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

Upload ملف لمكتبة الاستجابة المباشرة.

## <a name="limitations"></a>القيود

1.  الحد الأقصى لحجم الملف هو 20 ميغابايت.

2.  قيود المعدل لواجهة برمجة التطبيقات هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع ["بدء الاستخدام](apis-intro.md)".


| نوع الإذن                    | اذن     | اسم عرض الإذن        |
|------------------------------------|----------------|--------------------------------|
| Application                        | Library.Manage | إدارة مكتبة الاستجابة المباشرة |
| مفوض (حساب العمل أو المؤسسة التعليمية) | Library.Manage | إدارة مكتبة الاستجابة المباشرة |

## <a name="http-request"></a>طلب HTTP

Upload

```HTTP
POST https://api.securitycenter.microsoft.com/api/libraryfiles
```

## <a name="request-headers"></a>عناوين الطلبات

|  الاسم   |    نوع    |       الوصف                         |
|-----------------|--------|--------------------------------|
| التخويل   | سلسلة | حامل.\<token> مطلوب.      |
| نوع المحتوى    | سلسله | بيانات متعددة الجزء/النموذج. مطلوب. |

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير كائن بيانات النموذج مع المعلمات التالية:

| المعلمه         |     نوع         |       الوصف                                        |
|-----------------------|--------------|------------------------------------------------------------|
| ملف                  | محتوى الملف | الملف الذي سيتم تحميله إلى مكتبة الاستجابة المباشرة. مطلوب |
| الوصف           | سلسلة       | وصف الملف.                                  |
| ParametersDescription | سلسلة       | (اختياري) المعلمات المطلوبة لتشغيل البرنامج النصي. القيمة الافتراضية هي سلسلة فارغة.                |
| تجاوز الفهرسين      | منطقي      | (اختياري) ما إذا كنت تريد تجاوز الملف إذا كان موجودا بالفعل. القيمة الافتراضية هي سلسلة فارغة.          |



## <a name="response"></a>استجابه

-   إذا نجحت، يقوم هذا الأسلوب بإرجاع 200 - رمز استجابة موافق وكيان مكتبة الاستجابة المباشرة التي تم تحميلها في نص الاستجابة.

-   إذا لم ينجح: يرجع هذا الأسلوب 400 - طلب غير صحيح.  
    يشير الطلب غير الصحيح عادة إلى نص غير صحيح.

## <a name="example"></a>المثال

طلب

فيما يلي مثال على الطلب باستخدام curl.

```CURL
curl -X POST https://api.securitycenter.microsoft.com/api/libraryfiles -H
"Authorization: Bearer \$token" -F "file=\@mdatp1.png" -F
"ParametersDescription=test"  
-F "HasParameters=true" -F "OverrideIfExists=true" -F "Description=test
description"
```

## <a name="related-topic"></a>الموضوع ذو الصلة

-  [تشغيل الاستجابة المباشرة](run-live-response.md) 