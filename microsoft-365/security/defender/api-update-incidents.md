---
title: API لحادث التحديث
description: تعرف على كيفية تحديث الأحداث باستخدام Microsoft 365 Defender API
keywords: تحديث، api، حادث
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
ms.openlocfilehash: 447a4b5eb3f4eb521e7cc3bd2df23a42f16d2ef1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63573231"
---
# <a name="update-incidents-api"></a>تحديث الأحداث API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

## <a name="api-description"></a>وصف API

تحديث خصائص حادث موجود. الخصائص القابلة للتحديث هي: `status`و `determination`و و `classification`و `assignedTo`و `tags`و `comments`.

### <a name="quotas-resource-allocation-and-other-constraints"></a>الحصص النسبية وتخصيص الموارد والقيود الأخرى

1. يمكنك إجراء ما يصل إلى 50 مكالمة في الدقيقة أو 1500 مكالمة في الساعة قبل أن تصل إلى حد الحد المكبل.
2. يمكنك تعيين الخاصية `determination` فقط إذا `classification` تم تعيينها إلى TruePositive.

إذا تم لتقييد طلبك، فإنه سيرجع رمز `429` استجابة. سيشير جسمك للاستجابة إلى الوقت الذي يمكنك فيه بدء إجراء مكالمات جديدة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [الوصول إلى Microsoft 365 Defender برمجة التطبيقات](api-access.md).

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Incident.ReadWrite.All|قراءة كل الأحداث وكتابتها
مفوض (حساب العمل أو المدرسة)|Incident.ReadWrite|أحداث القراءة والكتابة

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم، يحتاج المستخدم إلى الحصول على إذن لتحديث الحادث في المدخل.

## <a name="http-request"></a>طلب HTTP

```HTTP
PATCH /api/incidents/{id}
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في نسخة الطلب الأساسية، زود القيم الخاصة الحقول التي يجب تحديثها. ستحافظ الخصائص الموجودة غير المضمنة في هيئة الطلب على قيمها، إلا إذا كان من المطلوب إعادة حسابها بسبب التغييرات التي تم إدخالها على القيم ذات الصلة. للحصول على أفضل أداء، يجب حذف القيم الموجودة التي لم تتغير.

الخاصية|النوع|الوصف
---|---|---
الحالة|تعداد|تحدد الحالة الحالية للحادث. القيم المحتملة هي: `Active`و `Resolved`و و `Redirected`.
assignedTo|سلسلة|مالك الحادث.
تصنيف|تعداد|مواصفات الحادث. القيم المحتملة هي: `Unknown`، `FalsePositive`و . `TruePositive`
تحديد|تعداد|تحدد تحديد الحادث. القيم المحتملة هي: `NotAvailable`، ، `Apt`، `Malware`، `SecurityPersonnel`، `UnwantedSoftware``SecurityTesting`، `Other`.
العلامات|قائمة السلسلة|قائمة علامات الأحداث.
تعليق|سلسلة|التعليق الذي يجب إضافته إلى الحادث.

## <a name="response"></a>الاستجابة

إذا نجح ذلك، فإن هذا الأسلوب يرجع `200 OK`. سيحتوي النص النصي للاستجابة على كيان الحادث الذي يحتوي على خصائص محدثة. إذا لم يتم العثور على حادث مع المرجع المحدد، فإن الأسلوب يرجع `404 Not Found`.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

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

- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [التعرف على حدود API والترخيص](api-terms.md)
- [فهم رموز الخطأ](api-error-codes.md)
- [واجهات برمجة التطبيقات للحوادث](api-incident.md)
- [سرد الأحداث](api-list-incidents.md)
- [نظرة عامة حول الأحداث](incidents-overview.md)
