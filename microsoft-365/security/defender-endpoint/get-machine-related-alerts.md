---
title: الحصول على API للتنبيهات ذات الصلة بالآلة
description: تعرف على كيفية استخدام API للحصول على تنبيهات متعلقة بالآلة. تسمح لك API هذه باسترداد كل التنبيهات المرتبطة بجهاز معين في Microsoft Defender ل Endpoint.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول، الأجهزة، ذات الصلة، التنبيهات
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
ms.openlocfilehash: 49cc0fca3ae7617b86ab079daace92eb3790db94
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63572264"
---
# <a name="get-machine-related-alerts--api"></a>الحصول على API للتنبيهات ذات الصلة بالآلة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد كل [التنبيهات](alerts.md) ذات الصلة بجهاز معين.

## <a name="limitations"></a>القيود

1. يمكنك الاستعلام عن الأجهزة التي تم تحديثها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.
2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Alert.read.All|"قراءة كل التنبيهات"
Application|Alert.ReadWrite.All|"قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة) | Alert.Read | "قراءة التنبيهات"
مفوض (حساب العمل أو المدرسة) | Alert.ReadWrite | "قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات". لمزيد من المعلومات حول الأذونات، راجع [إنشاء أدوار وإدارتها](user-roles.md).
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة. لمزيد من المعلومات حول إعدادات مجموعة الأجهزة، راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md).

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{id}/alerts
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح الجهاز وكان موجودا: 200 موافق مع [قائمة كيانات التنبيه](alerts.md) في الجسم. إذا لم يتم العثور على الجهاز: 404 لم يتم العثور عليه.
