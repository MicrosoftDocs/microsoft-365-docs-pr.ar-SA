---
title: رموز الخطأ Microsoft 365 Defender REST API
description: تعرف على رموز الخطأ الشائعة Microsoft 365 Defender REST API
keywords: api، خطأ، رموز، أخطاء شائعة، Microsoft 365 Defender، رموز أخطاء api
search.product: eADQiWindows 10XVcnh
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 499ab1722b2754e893361784f7ff1ce257ceb58b
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63571566"
---
# <a name="common-microsoft-365-defender-rest-api-error-codes"></a>رموز الخطأ Microsoft 365 Defender REST API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

قد يتم إرجاع رموز الأخطاء بواسطة عملية على أي من واجهات Microsoft 365 Defender برمجة التطبيقات. ستحتوي كل استجابة للخطأ على رسالة خطأ، والتي يمكن أن تساعد في حل المشكلة. يوفر عمود رسالة الخطأ في مقطع الجدول بعض الرسائل العينة. سيختلف محتوى الرسائل الفعلية استنادا إلى العوامل التي تم تشغيل الاستجابة لها. ويشار إلى المحتوى المتغير في الجدول بأقواس زاوية.

## <a name="error-codes"></a>رموز الخطأ

رمز الخطأ | رمز حالة HTTP | رسالة
-|-|-
BadRequest | BadRequest (400) | رسالة الخطأ "طلب غير جيد عام".
ODataError | BadRequest (400) | استعلام OData URI غير صالح \<the specific error is specified\>.
InvalidInput | BadRequest (400) | إدخال غير صالح \<the invalid input\>.
InvalidRequestBody | BadRequest (400) | طلب غير صالح.
InvalidHashValue | BadRequest (400) | قيمة "هاش \<the invalid hash\> " غير صالحة.
InvalidDomainName | BadRequest (400) | اسم المجال \<the invalid domain\> غير صالح.
InvalidIpAddress | BadRequest (400) | \<the invalid IP\> عنوان IP غير صالح.
InvalidUrl | BadRequest (400) | عنوان URL \<the invalid URL\> غير صالح.
MaximumBatchSizeExceeded | BadRequest (400) | تم تجاوز الحد الأقصى لحجم الدفعة. تم التسلم: \<batch size received\>، مسموح به: {حجم الدفعة مسموح}.
MissingRequiredParameter | BadRequest (400) | المعلمة \<the missing parameter\> مفقودة.
OsPlatformNotSupported | BadRequest (400) | نظام التشغيل الأساسي \<the client OS Platform\> غير معتمد لهذا الإجراء.
ClientVersionNotSupported | BadRequest (400) | \<The requested action\> معتمد على إصدار العميل \<supported client version\> والإصدارات الأحدث.
غير مصرح به | غير مصرح به (401) | غير مصرح به <br /><br />*ملاحظة: يحدث عادة بسبب رأس تخويل غير صالح أو منتهية الصلاحية.*
ممنوع | ممنوع (403) | ممنوع <br /><br />*ملاحظة: رمز مميز صالح ولكن إذن غير كاف لل الإجراء*.
DisabledFeature | ممنوع (403) | لم يتم تمكين ميزة المستأجر.
"غير مسموح به"، | ممنوع (403) | \<the disallowed operation and the reason\>.
NotFound | لم يتم العثور على (404) | رسالة خطأ عام لم يتم العثور عليها.
ResourceNotFound | لم يتم العثور على (404) | لم \<the requested resource\> يتم العثور على المورد.
InternalServerError | خطأ خادم داخلي (500) | *ملاحظة: لا توجد رسالة خطأ، أو إعادة محاولة العملية أو الاتصال [ب Microsoft](../../admin/get-help-support.md) إذا لم يتم حلها*

## <a name="examples"></a>أمثلة

```json
{
    "error": {
        "code": "ResourceNotFound",
        "message": "Machine 123123123 was not found",
        "target": "43f4cb08-8fac-4b65-9db1-745c2ae65f3a"
    }
}
```

```json
{
    "error": {
        "code": "InvalidRequestBody",
        "message": "Request body is incorrect",
        "target": "1fa66c0f-18bd-4133-b378-36d76f3a2ba0"
    }
}
```

## <a name="body-parameters"></a>المعلمات الأساسية

> [!IMPORTANT]
> المعلمات الأساسية حساسة لالحالتين.

إذا واجهت خطأ *InvalidRequestBody* أو *MissingRequiredParameter* ، فقد يكون ذلك بسبب خطأ مطبعي. راجع وثائق API وتحقق من تطابق المعلمات التي تم إرسالها مع المثال ذي الصلة.

## <a name="tracking-id"></a>تعقب الم ID

تحتوي كل استجابة للخطأ على معلمة ID فريدة للتعقب. اسم خاصية هذه المعلمة هو *الهدف*. عند الاتصال بنا بشأن خطأ ما، سيساعدنا إرفاق هذا المعرف في العثور على السبب الجذر للمشكلة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [Microsoft 365 Defender نظرة عامة على واجهات برمجة التطبيقات](api-overview.md)
- [واجهات Microsoft 365 Defender برمجة التطبيقات المعتمدة](api-supported.md)
- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [التعرف على حدود API والترخيص](api-terms.md)
