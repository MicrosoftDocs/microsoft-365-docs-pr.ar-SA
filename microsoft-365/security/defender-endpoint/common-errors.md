---
title: أخطاء شائعة في Microsoft Defender ل API لنقطة النهاية
description: قائمة بأخطاء Microsoft Defender الشائعة ل API لنقطة النهاية مع الأوصاف.
keywords: واجهات برمجة التطبيقات، Microsoft Defender ل API نقطة النهاية، الأخطاء، استكشاف الأخطاء وإصلاحها
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
ms.openlocfilehash: d960091409a71fd23e52a098ae3d8164c7df5aef
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573324"
---
# <a name="common-rest-api-error-codes"></a>رموز أخطاء REST API الشائعة



[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


* قد يتم إرجاع رموز الخطأ المدرجة في الجدول التالي بواسطة عملية على أي من واجهات برمجة تطبيقات نقطة النهاية ل Microsoft Defender.
* بالإضافة إلى رمز الخطأ، تحتوي كل استجابة للخطأ على رسالة خطأ، والتي يمكن أن تساعد في حل المشكلة.
* الرسالة هي نص مجاني يمكن تغييره.
* في أسفل الصفحة، يمكنك العثور على أمثلة الاستجابة.

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

رمز الخطأ|رمز حالة HTTP|رسالة
---|---|---
BadRequest|BadRequest (400)|رسالة الخطأ "طلب غير جيد عام".
ODataError|BadRequest (400)|استعلام OData URI غير صالح (تم تحديد الخطأ المحدد).
InvalidInput|BadRequest (400)|إدخال غير صالح {الإدخال غير صالح}.
InvalidRequestBody|BadRequest (400)|طلب غير صالح.
InvalidHashValue|BadRequest (400)|قيمة هاش {هاش غير صالح} غير صالحة.
InvalidDomainName|BadRequest (400)|اسم المجال {المجال غير الصالح} غير صالح.
InvalidIpAddress|BadRequest (400)|عنوان IP {IP غير صالح} غير صالح.
InvalidUrl|BadRequest (400)|URL {URL غير صالح} غير صالح.
MaximumBatchSizeExceeded|BadRequest (400)|تم تجاوز الحد الأقصى لحجم الدفعة. تم استلامه: {حجم الدفعة تم استلامه}، مسموح به: {حجم الدفعة مسموح}.
MissingRequiredParameter|BadRequest (400)|المعلمة {المعلمة المفقودة} مفقودة.
OsPlatformNotSupported|BadRequest (400)|نظام التشغيل الأساسي {client OS Platform} غير معتمد لهذا الإجراء.
ClientVersionNotSupported|BadRequest (400)|يتم دعم {الإجراء المطلوب} على إصدار العميل {إصدار العميل المعتمد} والإصدارات الأحدث.
غير مصرح به|غير مصرح به (401)|غير مصرح به (رأس تخويل غير صالح أو منتهية الصلاحية).
ممنوع|ممنوع (403)|ممنوع (رمز مميز صالح ولكن إذن غير كاف للتحرك).
DisabledFeature|ممنوع (403)|لم يتم تمكين ميزة المستأجر.
"غير مسموح به"،|ممنوع (403)|{العملية غير مسموح بها والسبب}.
NotFound|لم يتم العثور على (404)|رسالة خطأ عام لم يتم العثور عليها.
ResourceNotFound|لم يتم العثور على (404)|لم يتم العثور على المورد {المورد المطلوب}.
InternalServerError|خطأ خادم داخلي (500)|(لا توجد رسالة خطأ، إعادة محاولة العملية)
TooManyRequests|عدد كبير جدا من الطلبات (429)|ستمثل الاستجابة بلوغ حد الحصة النسبية إما حسب عدد الطلبات أو وحدة المعالجة المركزية (CPU).

## <a name="body-parameters-are-case-sensitive"></a>المعلمات الأساسية حساسة للقضية

تتحسس المعلمات الأساسية التي تم إرسالها حالة التحسس حاليا.

إذا واجهت أخطاء **InvalidRequestBody** أو **MissingRequiredParameter** ، فقد يكون ذلك بسبب معلمة رأس مال خاطئة أو حرف حرف أصغر.

راجع صفحة وثائق API وتحقق من تطابق المعلمات التي تم إرسالها مع المثال ذي الصلة.

## <a name="correlation-request-id"></a>"معرّف طلب الارتباط"

تحتوي كل استجابة للخطأ على معلمة ID فريدة للتعقب.

اسم خاصية هذه المعلمة هو "الهدف".

عند الاتصال بنا بشأن خطأ ما، سيساعد إرفاق هذا المعرف في العثور على السبب الجذر للمشكلة.

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
