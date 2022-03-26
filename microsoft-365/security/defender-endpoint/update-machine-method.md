---
title: تحديث API للكيان الآلي
description: تعرف على كيفية تحديث علامات الجهاز باستخدام API هذا. يمكنك تحديث العلامات وخصائص قيمة الجهاز.
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
ms.openlocfilehash: 77876024faa7452ff284e30a587e72855068cc98
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63574343"
---
# <a name="update-machine"></a>تحديث الجهاز 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

تحديث خصائص الجهاز [الموجود](machine.md).

الخصائص القابلة للتحديث هي: `machineTags` و `deviceValue`.

## <a name="limitations"></a>القيود

1. يمكنك تحديث الأجهزة المتوفرة في API. 
2. إلحاق العلامات فقط في مجموعة العلامات في جهاز التحديث. إذا كانت العلامات موجودة، فيجب تضمينها في مجموعة العلامات في الجسم.
3. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.ReadWrite.All|"قراءة معلومات الجهاز وكتابتها لجميع الأجهزة"
مفوض (حساب العمل أو المدرسة)|Machine.ReadWrite|"قراءة معلومات الجهاز وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: 'تحقيق التنبيهات'. لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md).
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة. لمزيد من المعلومات، راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md).

## <a name="http-request"></a>طلب HTTP

```http
PATCH /api/machines/{machineId}
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
machineTags|مجموعة سلاسل|مجموعة من [علامات](machine.md) الجهاز.
deviceValue|تعداد قابل للبطلان|قيمة [الجهاز](tvm-assign-device-value.md). القيم المحتملة هي: "عادي" و"منخفض" و"عال".

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق، ويرجع [كيان الجهاز في](machine.md) هيئة الاستجابة مع الخصائص المحدثة.

إذا كانت مجموعة علامات الجهاز في النص النصي لا تحتوي على علامات جهاز موجودة - يستبدل كل العلامات والعلامات المتوفرة في النص النصي للطلب.

إذا لم يتم العثور على الجهاز الذي به الم ID المحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
PATCH https://api.securitycenter.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10" "Windows11",
                     "Windows Insider - Fast"
    ]
}
```
