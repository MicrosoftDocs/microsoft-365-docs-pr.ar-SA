---
title: تحديث واجهة برمجة تطبيقات كيان التنبيه
description: تعرف على كيفية تحديث تنبيه Microsoft Defender لنقطة النهاية باستخدام واجهة برمجة التطبيقات هذه. يمكنك تحديث الحالة، وتحديد، والتصنيف، والخصائص المعينة إلى.
keywords: واجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، والحصول على، والتنبيه، والمعلومات، والمعرف
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
ms.openlocfilehash: c015372c9f0fcf6cf0e25af1902af970e11156d0
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67099107"
---
# <a name="update-alert"></a>تحديث التنبيه

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات
التحديثات خصائص [التنبيه](alerts.md) الموجود.

تتوفر عمليات إرسال **التعليق** مع تحديث الخصائص أو بدونها.

الخصائص القابلة للتحديث هي: `status`و، `determination`و، `classification`و `assignedTo`.

## <a name="limitations"></a>القيود

1. يمكنك تحديث التنبيهات المتوفرة في واجهة برمجة التطبيقات. لمزيد من المعلومات، راجع ["تنبيهات القائمة](get-alerts.md)".
2. قيود المعدل لواجهة برمجة التطبيقات هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن|إذن|اسم عرض الإذن
:---|:---|:---
Application|Alerts.ReadWrite.All|"قراءة كافة التنبيهات وكتابتها"
مفوض (حساب العمل أو المؤسسة التعليمية)|Alert.ReadWrite|"تنبيهات القراءة والكتابة"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يحتاج المستخدم إلى الحصول على إذن الدور التالي على الأقل: "التحقيق في التنبيهات" (لمزيد من المعلومات، راجع [إنشاء الأدوار وإدارتها](user-roles.md) )
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (لمزيد من المعلومات، راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md)

## <a name="http-request"></a>طلب HTTP

```http
PATCH /api/alerts/{id}
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
إذن|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|التطبيق/json. **مطلوب**.

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير القيم للحقول ذات الصلة التي يجب تحديثها.

ستحتفظ الخصائص الموجودة غير المضمنة في نص الطلب بقيمها السابقة أو إعادة حسابها استنادا إلى التغييرات التي أجريت على قيم الخصائص الأخرى.

للحصول على أفضل أداء، يجب عدم تضمين القيم الموجودة التي لم تتغير.

مال|نوع|الوصف
:---|:---|:---
حالة|سلسلة|تحديد الحالة الحالية للتنبيه. قيم الخاصية هي: "جديد" و"InProgress" و"تم الحل".
معين إلى|سلسلة|مالك التنبيه
تصنيف|سلسلة|تحديد مواصفات التنبيه. قيم الخاصية هي: 'غير معروف'، 'FalsePositive'، 'TruePositive'.
عزم|سلسلة|يحدد تحديد التنبيه. قيم الخصائص هي: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
التعليق|سلسلة|تعليق لإضافته إلى التنبيه.

>[!NOTE]
>حوالي 29 أغسطس 2022، سيتم إهمال قيم تحديد التنبيه المدعومة مسبقا ('Apt' و'SecurityPersonnel') ولن تعود متوفرة عبر واجهة برمجة التطبيقات.

## <a name="response"></a>استجابه

إذا نجحت، ترجع هذه الطريقة 200 OK، وكيان [التنبيه](alerts.md) في نص الاستجابة مع الخصائص المحدثة. إذا لم يتم العثور على تنبيه بالمعرف المحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>مثل

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
