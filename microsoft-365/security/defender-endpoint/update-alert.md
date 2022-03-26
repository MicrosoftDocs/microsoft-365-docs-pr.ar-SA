---
title: تحديث API كيان التنبيه
description: تعرف على كيفية تحديث تنبيه Microsoft Defender لنقطة النهاية باستخدام API هذا. يمكنك تحديث خصائص الحالة وتحديدها وتصنيفها وتعيينها إلى.
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4efe1460374350d054bbe6d19543c75454d7b5ce
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63570530"
---
# <a name="update-alert"></a>تحديث التنبيه

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API
تحديث خصائص التنبيه [الموجود](alerts.md).

يتوفر إرسال **التعليق** مع خصائص التحديث أو بدونها.

الخصائص القابلة للتحديث هي: `status`و `determination`و `classification`و و `assignedTo`.

## <a name="limitations"></a>القيود

1. يمكنك تحديث التنبيهات المتوفرة في API. لمزيد من المعلومات، راجع [تنبيهات القائمة](get-alerts.md).
2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alerts.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Alert.ReadWrite|"قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "التحقيق في التنبيهات" (لمزيد من المعلومات، راجع إنشاء [أدوار وإدارتها](user-roles.md) )
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (لمزيد من المعلومات، راجع إنشاء [مجموعات الأجهزة وإدارتها](machine-groups.md)

## <a name="http-request"></a>طلب HTTP

```http
PATCH /api/alerts/{id}
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في نسخة الطلب الأساسية، اعرض القيم الخاصة الحقول ذات الصلة التي يجب تحديثها.

ستحافظ الخصائص الموجودة غير المضمنة في هيئة الطلب على قيمها السابقة أو سيتم إعادة حسابها استنادا إلى التغييرات التي تم إدخالها على قيم الخصائص الأخرى.

للحصول على أفضل أداء، يجب عدم تضمين القيم الموجودة التي لم تتغير.

الخاصية|النوع|الوصف
:---|:---|:---
الحالة|سلسلة|يحدد الحالة الحالية للتنبيه. قيم الخاصية هي: 'جديد' و'InProgress' و'تم الحل'.
assignedTo|سلسلة|مالك التنبيه
التصنيف|سلسلة|تحدد مواصفات التنبيه. قيم الخاصية هي: 'غير معروف'، 'FalsePositive'، 'TruePositive'.
التحديد|سلسلة|يحدد تحديد التنبيه. قيم الخاصية هي: 'NotAvailable' و'Apt' و'Malware' و'SecurityPersonnel' و'SecurityTesting' و'UnwantedSoftware' و'أخرى'
تعليق|سلسلة|التعليق الذي يجب إضافته إلى التنبيه.

## <a name="response"></a>الاستجابة

إذا نجح، ترجع هذه الطريقة 200 موافق، وترجع [كيان](alerts.md) التنبيه في هيئة الاستجابة مع الخصائص المحدثة. إذا لم يتم العثور على تنبيه مع الم ID المحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
PATCH https://api.securitycenter.microsoft.com/api/alerts/121688558380765161_2136280442
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
