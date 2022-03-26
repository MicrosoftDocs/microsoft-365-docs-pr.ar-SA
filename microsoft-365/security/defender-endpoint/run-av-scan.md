---
title: تشغيل API لمسح برامج الحماية من الفيروسات
description: استخدم API هذه لإنشاء مكالمات ذات صلة بتشغيل فحص الحماية من الفيروسات على جهاز.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، إزالة الجهاز من عزله
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
ms.openlocfilehash: 3208ff32c2adda051b79fea684af915a909dd062
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/06/2022
ms.locfileid: "63575843"
---
# <a name="run-antivirus-scan-api"></a>تشغيل API لمسح برامج الحماية من الفيروسات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

ابدأ برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي على جهاز.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
>
> - يتوفر هذا الإجراء للأجهزة التي تعمل Windows 10 والإصدار 1709 أو الإصدارات الأحدث وعلى Windows 11.
> - يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender (Microsoft Defender AV) جنبا إلى جنب مع حلول الحماية من الفيروسات الأخرى، سواء برنامج الحماية من الفيروسات من Microsoft Defender هو حل الحماية من الفيروسات النشط أم لا. برنامج الحماية من الفيروسات من Microsoft Defender في الوضع "غير النشط". لمزيد من المعلومات، [راجع برنامج الحماية من الفيروسات من Microsoft Defender التوافق](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.Scan|'جهاز المسح الضوئي'
مفوض (حساب العمل أو المدرسة)|Machine.Scan|'جهاز المسح الضوئي'

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إجراءات المعالجة النشطة" (راجع إنشاء أدوار وإدارتها [للحصول على](user-roles.md) مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/runAntiVirusScan
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
:---|:---|:---
تعليق|سلسلة|التعليق على إقران الإجراء. **مطلوب**.
ScanType|سلسلة|تعريف نوع المسح الضوئي. **مطلوب**.

**يتحكم ScanType** في نوع الفحص الذي يجب القيام به ويمكن أن يكون واحدا من ما يلي:

- **سريع**: إجراء مسح سريع على الجهاز
- **كامل**: إجراء الفحص الكامل على الجهاز

## <a name="response"></a>الاستجابة

إذا نجحت هذه الطريقة، فإرجاع 201، التعليمات البرمجية للاستجابة التي تم إنشاؤها، كائن _MachineAction_ في هيئة الاستجابة.

إذا قمت بإرسال مكالمات API متعددة لتشغيل عملية فحص برنامج الحماية من الفيروسات لنفس الجهاز، فإنه يرجع "إجراء جهاز معلق" أو HTTP 400 مع الرسالة "الإجراء قيد التقدم بالفعل".

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runAntiVirusScan 
```

```json
{
  "Comment": "Check machine for viruses due to alert 3212",
  "ScanType": "Full"
}
```
