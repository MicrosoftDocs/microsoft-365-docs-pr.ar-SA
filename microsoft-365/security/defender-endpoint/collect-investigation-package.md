---
title: تجميع حزمة التحقيق API
description: استخدم API هذه لإنشاء مكالمات ذات صلة بتجميع حزمة تحقيق من جهاز.
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
ms.openlocfilehash: e6a310c167a0f77f0022b9ba35ed9aa94e437eb9
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583107"
---
# <a name="collect-investigation-package-api"></a>تجميع حزمة التحقيق API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

تجميع حزمة التحقيق من جهاز.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

> [!IMPORTANT]
>
> - تتوفر إجراءات الاستجابة هذه فقط للأجهزة التي تعمل Windows 10 والإصدار 1703 أو الإصدارات الأحدث وعلى Windows 11.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Defender ل واجهات برمجة التطبيقات في نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.CollectForensics|'تجميع الأطباء الشرعيين'
مفوض (حساب العمل أو المدرسة)|Machine.CollectForensics|'تجميع الأطباء الشرعيين'

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "تنبيهات التحقيق" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/collectInvestigationPackage
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
تعليق|سلسلة|التعليق على إقران الإجراء. **مطلوب**.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 201 - رمز الاستجابة الذي تم إنشاؤه و"إجراء [الجهاز](machineaction.md) " في هيئة الاستجابة. إذا كانت مجموعة قيد التشغيل بالفعل، فإن ذلك يرجع 400 طلب غير جيد.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/fb9ab6be3965095a09c057be7c90f0a2/collectInvestigationPackage
```

```json
{
  "Comment": "Collect forensics due to alert 1234"
}
```
