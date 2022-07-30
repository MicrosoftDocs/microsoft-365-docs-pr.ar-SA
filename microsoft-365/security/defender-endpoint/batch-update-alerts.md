---
title: واجهة برمجة تطبيقات كيانات تنبيه Batch Update
description: تعرف على كيفية تحديث تنبيهات Microsoft Defender لنقطة النهاية في دفعة واحدة باستخدام واجهة برمجة التطبيقات هذه. يمكنك تحديث الحالة، وتحديد، والتصنيف، والخصائص المعينة إلى.
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
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 7bda1310178759def39b6ba9baedb25de875fb11
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67099125"
---
# <a name="batch-update-alerts"></a>تنبيهات التحديثات الدفعية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

التحديثات خصائص دفعة من [التنبيهات](alerts.md) الموجودة.

تتوفر عمليات إرسال **التعليق** مع تحديث الخصائص أو بدونها.

الخصائص القابلة للتحديث هي: `status`و، `determination`و `classification` `assignedTo`.

## <a name="limitations"></a>القيود

1. يمكنك تحديث التنبيهات المتوفرة في واجهة برمجة التطبيقات. راجع ["تنبيهات القائمة"](get-alerts.md) للحصول على مزيد من المعلومات.
2. قيود المعدل لواجهة برمجة التطبيقات هذه هي 10 مكالمات في الدقيقة و500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن | إذن | اسم عرض الإذن
:---|:---|:---
Application | Alert.ReadWrite.All | "قراءة كافة التنبيهات وكتابتها"
مفوض (حساب العمل أو المؤسسة التعليمية) | Alert.ReadWrite | "تنبيهات القراءة والكتابة"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يحتاج المستخدم إلى الحصول على إذن الدور التالي على الأقل: "التحقيق في التنبيهات" (راجع [إنشاء الأدوار وإدارتها](user-roles.md) لمزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md) لمزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST /api/alerts/batchUpdate
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
إذن | سلسلة | حامل {token}. **مطلوب**.
نوع المحتوى | سلسلة | التطبيق/json. **مطلوب**.

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير معرفات التنبيهات التي سيتم تحديثها وقيم الحقول ذات الصلة التي ترغب في تحديثها لهذه التنبيهات.

ستحتفظ الخصائص الموجودة غير المضمنة في نص الطلب بقيمها السابقة أو إعادة حسابها استنادا إلى التغييرات التي أجريت على قيم الخصائص الأخرى.

للحصول على أفضل أداء، يجب عدم تضمين القيم الموجودة التي لم تتغير.

مال | نوع | الوصف
:---|:---|:---
alertIds | سلسلة قائمة&lt;&gt;| قائمة بمعرفات التنبيهات التي سيتم تحديثها. **مطلوب**
حالة | سلسلة | تحديد الحالة المحدثة للتنبيهات المحددة. قيم الخاصية هي: "جديد" و"InProgress" و"تم الحل".
معين إلى | سلسلة | مالك التنبيهات المحددة
تصنيف | سلسلة | تحديد مواصفات التنبيهات المحددة. قيم الخاصية هي: "True positive" و"Informational, expected activity" و"False positive".
عزم | سلسلة | تحديد التنبيهات المحددة. قيم الخصائص هي: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'
التعليق | سلسلة | تعليق لإضافته إلى التنبيهات المحددة.

>[!NOTE]
>حوالي 29 أغسطس 2022، سيتم إهمال قيم تحديد التنبيه المدعومة مسبقا ('Apt' و'SecurityPersonnel') ولن تعود متوفرة عبر واجهة برمجة التطبيقات.

## <a name="response"></a>استجابه

إذا نجحت هذه الطريقة، ترجع 200 موافق، مع نص استجابة فارغ.

## <a name="example"></a>مثل

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
