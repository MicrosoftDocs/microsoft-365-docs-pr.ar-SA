---
title: API (برمجة برمجة برمجة) جهاز Offboard
description: تعرف على كيفية استخدام API ل offboard جهاز من Microsoft Defender ل Endpoint.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، حزمة تجميع التحقيق
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
ms.openlocfilehash: 1279f7271abbd4086c946492e95daa52962dbae5
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/03/2022
ms.locfileid: "63570363"
---
# <a name="offboard-machine-api"></a>API (برمجة برمجة برمجة) جهاز Offboard

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

جهاز إيقاف التشغيل من Defender لنقطة النهاية.

## <a name="limitations"></a>القيود

- قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> يتم دعم API هذه Windows 11 أو Windows 10 أو الإصدار 1703 والإصدارات الأحدث أو Windows Server 2019 والإصدارات الأحدث.
>
> إن API هذه غير معتمدة على أجهزة MacOS أو Linux.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Defender ل واجهات برمجة التطبيقات في نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Machine.Offboard|'جهاز Offboard'
مفوض (حساب العمل أو المدرسة)|Machine.Offboard|'جهاز Offboard'

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يحتاج المستخدم إلى دور "المسؤول العام" في AD
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

يمكن العثور على "معر ة الجهاز" في عنوان URL عند تحديد الجهاز. بشكل عام، إنه رقم alphanumeric من 40 رقما يمكن العثور عليه في عنوان URL.

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
---|---|---
تعليق|سلسلة|التعليق على إقران الإجراء. **مطلوب**.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 201 - رمز الاستجابة الذي تم إنشاؤه و"إجراء [الجهاز](machineaction.md) " في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
