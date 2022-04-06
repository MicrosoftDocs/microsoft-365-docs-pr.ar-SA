---
title: تقييد API لتنفيذ التطبيق
description: استخدم API هذه لإنشاء مكالمات ذات صلة بتقييد تطبيق من التنفيذ.
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
ms.openlocfilehash: dee5ad9466793892d09af2f85faa9f3fd2348ca6
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583206"
---
# <a name="restrict-app-execution-api"></a>تقييد API لتنفيذ التطبيق

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

تقييد تنفيذ جميع التطبيقات على الجهاز باستثناء مجموعة محددة مسبقا.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

[!include[Device actions note](../../includes/machineactionsnote.md)]


> [!IMPORTANT]
>
> - يتوفر هذا الإجراء للأجهزة التي تعمل Windows 10 والإصدار 1709 أو الإصدارات الأحدث وعلى Windows 11.
> - تتوفر هذه الميزة إذا كانت مؤسستك تستخدم برنامج الحماية من الفيروسات من Microsoft Defender.
> - يجب أن يلبي هذا الإجراء Windows نهج تكامل التعليمات البرمجية ل Defender Application Control ومتطلبات التوقيع. لمزيد من المعلومات، راجع [تنسيقات نهج تكامل التعليمات البرمجية والتوقيع](/windows/device-security/device-guard/requirements-and-deployment-planning-guidelines-for-device-guard#code-integrity-policy-formats-and-signing).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.RestrictExecution|"تقييد تنفيذ التعليمات البرمجية"
مفوض (حساب العمل أو المدرسة)|Machine.RestrictExecution|"تقييد تنفيذ التعليمات البرمجية"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إجراءات المعالجة النشطة" (راجع إنشاء أدوار وإدارتها [للحصول على](user-roles.md) مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/restrictCodeExecution
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

إذا نجح هذا الأسلوب، فيرجع 201 - رمز الاستجابة الذي تم إنشاؤه و"إجراء [الجهاز](machineaction.md) " في هيئة الاستجابة.

إذا قمت بإرسال مكالمات API متعددة لتقييد تنفيذ التطبيق لنفس الجهاز، فإرجاع "إجراء جهاز معلق" أو HTTP 400 مع الرسالة "الإجراء قيد التقدم بالفعل".

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/restrictCodeExecution 
```

```json
{
  "Comment": "Restrict code execution due to alert 1234"
}
```

- لإزالة تقييد تنفيذ التعليمات البرمجية من جهاز، راجع [إزالة تقييد التطبيق](unrestrict-code-execution.md).
