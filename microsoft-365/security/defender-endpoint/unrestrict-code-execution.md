---
title: إزالة API لقيود التطبيق
description: استخدم API هذه لإنشاء مكالمات ذات صلة بإزالة قيد من التطبيقات من التنفيذ.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، إزالة الجهاز من عزله
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: c2fe35d73cd9abf3483c32067bf59334c6ad016b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570732"
---
# <a name="remove-app-restriction-api"></a>إزالة API لقيود التطبيق

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

تمكين تنفيذ أي تطبيق على الجهاز.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - يتوفر عزل كامل للأجهزة Windows 10 الإصدار 1703.
> - يتوفر عزل انتقائي للأجهزة Windows 10 أو الإصدار 1709 أو الإصدارات الأحدث.
> - عند عزل جهاز، يتم السماح ببعض العمليات والوجهات فقط. وبالتالي، لن تتمكن الأجهزة التي تقف خلف خدمة VPN كاملة من الوصول إلى خدمة سحابة Microsoft Defender for Endpoint بعد عزل الجهاز. نوصي باستخدام VPN مقسم للانقسام ل Microsoft Defender لنقطة النهاية برنامج الحماية من الفيروسات من Microsoft Defender البيانات ذات الصلة بالحماية المستندة إلى السحابة.

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
POST https://api.securitycenter.microsoft.com/api/machines/{id}/unrestrictCodeExecution
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

إذا أرسلت مكالمات API متعددة لإزالة قيود التطبيق على الجهاز نفسه، فإرجاع "إجراء الجهاز المعلق" أو HTTP 400 مع الرسالة "الإجراء قيد التقدم بالفعل".

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution 
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}

```

لتقييد تنفيذ التعليمات البرمجية على جهاز، راجع [تقييد تنفيذ التطبيق](restrict-code-execution.md).
