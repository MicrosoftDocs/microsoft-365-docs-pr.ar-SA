---
title: تحديث واجهة برمجة تطبيقات الحدث
description: تعرف على كيفية تحديث الحوادث باستخدام واجهة برمجة تطبيقات Microsoft 365 Defender
keywords: تحديث، واجهة برمجة تطبيقات، حدث
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
ms.openlocfilehash: c7350059bdd5006cf57ccf35f71b67e371e75708
ms.sourcegitcommit: 1e53bf8208c30d7b60685896207cc1142bebf34a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67059722"
---
# <a name="update-incidents-api"></a>تحديث واجهة برمجة تطبيقات الأحداث

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

التحديثات خصائص الحادث الحالي. الخصائص القابلة للتحديث هي: `status`و، `determination`و، `classification`و، `assignedTo`و، `tags`و `comments`.

### <a name="quotas-resource-allocation-and-other-constraints"></a>الحصص النسبية وتخصيص الموارد والقيود الأخرى

1. يمكنك إجراء ما يصل إلى 50 مكالمة في الدقيقة أو 1500 مكالمة في الساعة قبل الوصول إلى حد التقييد.
2. يمكنك تعيين الخاصية `determination` فقط إذا تم `classification` تعيينها إلى TruePositive.

إذا تم تقييد طلبك، فسيرجع رمز استجابة `429` . سيشير نص الاستجابة إلى الوقت الذي يمكنك فيه بدء إجراء مكالمات جديدة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-access.md).

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Incident.ReadWrite.All|قراءة وكتابة جميع الحوادث
مفوض (حساب العمل أو المؤسسة التعليمية)|Incident.ReadWrite|أحداث القراءة والكتابة

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم، يحتاج المستخدم إلى إذن لتحديث الحدث في المدخل.

## <a name="http-request"></a>طلب HTTP

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|التطبيق/json. **مطلوب**.

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير قيم الحقول التي يجب تحديثها. ستحافظ الخصائص الموجودة غير المضمنة في نص الطلب على قيمها، إلا إذا كان يجب إعادة حسابها بسبب التغييرات في القيم ذات الصلة. للحصول على أفضل أداء، يجب حذف القيم الموجودة التي لم تتغير.

الخاصيه|نوع|الوصف
---|---|---
حاله|التعداد|تحديد الحالة الحالية للحادث. القيم المحتملة هي: `Active`و، `Resolved`و `Redirected`.
معين إلى|سلسله|مالك الحادث.
تصنيف|التعداد|مواصفات الحدث. القيم المحتملة هي: `Unknown`, , `TruePositive``FalsePositive`.
تحديد|التعداد|تحديد تحديد الحادث. القيم المحتملة هي: `NotAvailable`, `Apt`, `Malware`, `SecurityPersonnel`, , `SecurityTesting`, `Other``UnwantedSoftware`.
العلامات|قائمة السلاسل|قائمة بعلامات الحادث.
التعليق|سلسله|تعليق لإضافته إلى الحدث.

>[!NOTE]
>حوالي 29 أغسطس 2022، سيتم إهمال قيم تحديد التنبيه المدعومة مسبقا ('Apt' و'SecurityPersonnel') ولن تعود متوفرة عبر واجهة برمجة التطبيقات.

## <a name="response"></a>استجابه

إذا نجحت، يرجع `200 OK`هذا الأسلوب. سيحتوي نص الاستجابة على كيان الحادث بخصائص محدثة. إذا لم يتم العثور على حادث بالمعرف المحدد، فترجع `404 Not Found`الطريقة.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

فيما يلي مثال على الطلب.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

### <a name="response-example"></a>مثال على الاستجابة

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"],
    "comments": [
          {
              "comment": "pen testing",
              "createdBy": "secop2@contoso.com",
              "createdTime": "2021-05-02T09:34:21.5519738Z"
          },
          {
              "comment": "valid incident",
              "createdBy": "secop2@contoso.comt",
              "createdTime": "2021-05-02T09:36:27.6652581Z"
          }
      ]
}
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-access.md)
- [التعرف على حدود واجهة برمجة التطبيقات والترخيص](api-terms.md)
- [فهم رموز الأخطاء](api-error-codes.md)
- [واجهات برمجة التطبيقات للحوادث](api-incident.md)
- [سرد الأحداث](api-list-incidents.md)
- [نظرة عامة على الحوادث](incidents-overview.md)
