---
title: API (API) لكيانات تنبيهات "تحديث الدفعات"
description: تعرف على كيفية تحديث تنبيهات Microsoft Defender لنقطة النهاية في دفعة باستخدام API هذه. يمكنك تحديث خصائص الحالة وتحديدها وتصنيفها وتعيينها إلى.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيه، المعلومات، الم id
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: a2d695a2b406d4850f0e9896af3ec3b2aede8870
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570696"
---
# <a name="batch-update-alerts"></a>تنبيهات التحديثات الدفعية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>وصف API

تحديث خصائص دفعة من التنبيهات [الموجودة](alerts.md).

يتوفر إرسال **التعليق** مع خصائص التحديث أو بدونها.

الخصائص القابلة للتحديث هي: `status`و `classification` `determination``assignedTo`.

## <a name="limitations"></a>القيود

1. يمكنك تحديث التنبيهات المتوفرة في API. لمزيد [من المعلومات، راجع تنبيهات](get-alerts.md) القائمة.
2. قيود السعر ل API هذه هي 10 مكالمات في الدقيقة و500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن | الإذن | اسم عرض الأذونات
:---|:---|:---
Application | Alert.ReadWrite.All | "قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة) | Alert.ReadWrite | "قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "التحقيق في التنبيهات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (راجع إنشاء [مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.
نوع المحتوى | سلسلة | application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في جزء الطلب، قم بتزويدك ب IDs الخاصة بالتنبيهات المطلوب تحديثها وقيم الحقول ذات الصلة التي تريد تحديثها لهذه التنبيهات.

ستحافظ الخصائص الموجودة غير المضمنة في هيئة الطلب على قيمها السابقة أو سيتم إعادة حسابها استنادا إلى التغييرات التي تم إدخالها على قيم الخصائص الأخرى.

للحصول على أفضل أداء، يجب عدم تضمين القيم الموجودة التي لم تتغير.

الخاصية | النوع | الوصف
:---|:---|:---
alertIds | ListString&lt;&gt;| قائمة بالم IDs الخاصة بالتنبيهات التي سيتم تحديثها. **مطلوب**
الحالة | سلسلة | يحدد الحالة المحدثة للتنبيهات المحددة. قيم الخاصية هي: 'جديد' و'InProgress' و'تم الحل'.
assignedTo | سلسلة | مالك التنبيهات المحددة
تصنيف | سلسلة | يحدد مواصفات التنبيهات المحددة. قيم الخاصية هي: 'غير معروف'، 'FalsePositive'، 'TruePositive'. 
تحديد | سلسلة | يحدد تحديد التنبيهات المحددة. قيم الخاصية هي: 'NotAvailable' و'Apt' و'Malware' و'SecurityPersonnel' و'SecurityTesting' و'UnwantedSoftware' و'أخرى'
تعليق | سلسلة | التعليق الذي يجب إضافته إلى التنبيهات المحددة.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق، مع وجود هيئة استجابة فارغة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
