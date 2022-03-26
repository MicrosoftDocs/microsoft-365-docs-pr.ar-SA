---
title: تعيين API لقيمة الجهاز
description: تعرف على كيفية تحديد قيمة جهاز باستخدام Microsoft Defender ل API لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، العلامات، علامات الجهاز
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: b85e7e9fc96b447c6e2528249e516c45ea3e66d1
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63571594"
---
# <a name="set-device-value-api"></a>تعيين API لقيمة الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

تعيين قيمة الجهاز لجهاز [معين](machine.md).<br>
لمزيد [من المعلومات، راجع تعيين قيم](tvm-assign-device-value.md) الجهاز.

## <a name="limitations"></a>القيود

1. يمكنك النشر على الأجهزة التي رأيتها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.
2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.ReadWrite.All|"قراءة كل معلومات الجهاز وكتابتها"
مفوض (حساب العمل أو المدرسة)|Machine.ReadWrite|"قراءة معلومات الجهاز وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إدارة إعداد الأمان". للحصول على مزيد من المعلومات (راجع [إنشاء أدوار وإدارتها](user-roles.md) )
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الجهاز (راجع [إنشاء مجموعات](machine-groups.md) الجهاز وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{machineId}/setDeviceValue
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
:---|:---|:---
DeviceValue|تعداد|قيمة الجهاز. القيم المسموح بها هي: "عادي" و"منخفض" و"عال". **مطلوب**.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 - رمز استجابة موافق والآلة المحدثة في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال لطلب يضيف علامة الجهاز.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/setDeviceValue
```

```json
{
  "DeviceValue" : "High"
}
```
