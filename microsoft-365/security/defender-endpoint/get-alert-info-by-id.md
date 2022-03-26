---
title: الحصول على معلومات التنبيه بواسطة ID API
description: تعرف على كيفية استخدام "الحصول على معلومات التنبيه بواسطة API للمعرف" لاسترداد تنبيه معين بواسطة المعرف الخاص به في Microsoft Defender لنقطة النهاية.
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
ms.openlocfilehash: 09866afa2b965f8587114d49f92d8068c535a0c7
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63572353"
---
# <a name="get-alert-information-by-id-api"></a>الحصول على معلومات التنبيه بواسطة ID API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد تنبيه [معين](alerts.md) بواسطة المرجع الخاص به.

## <a name="limitations"></a>القيود

- يمكنك الحصول على التنبيهات التي تم التحديث الأخير لها وفقا لفترة الاستبقاء التي تم تكوينها.
- قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md).

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alert.read.All|"قراءة كل التنبيهات"
Application|Alert.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Alert.Read|"قراءة التنبيهات"
مفوض (حساب العمل أو المدرسة)|Alert.ReadWrite|"قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (راجع إنشاء [مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/alerts/{id}
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق، [و كيان](alerts.md) التنبيه في هيئة الاستجابة. إذا لم يتم العثور على تنبيه به الم ID المحدد - 404 لم يتم العثور عليه.
