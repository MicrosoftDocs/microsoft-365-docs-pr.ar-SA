---
title: API لملفات التوقف والعزل
description: تعرف على كيفية إيقاف تشغيل ملف على جهاز وحذف الملف في Microsoft Defender لنقطة النهاية. راجع مثالا.
keywords: apis، api للرسم البياني، apis المعتمدة، ملف إيقاف وفحص
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
ms.openlocfilehash: 1f61e238030c5c8c31e514ef76cf90ffc4b5bd92
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570452"
---
# <a name="stop-and-quarantine-file-api"></a>API لملفات التوقف والعزل

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إيقاف تنفيذ ملف على جهاز وحذفه.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

[!include[Device actions note](../../includes/machineactionsnote.md)]

> [!IMPORTANT]
> لا يمكنك اتخاذ هذا الإجراء إلا إذا:
>
> - يتم تشغيل الجهاز الذي تقوم باتخاذ الإجراء عليه Windows 10 أو الإصدار 1703 أو الإصدارات الأحدث أو Windows 11
> - لا ينتمي الملف إلى ناشرين موثوق بهم من جهة خارجية أو لم يتم توقيعه من قبل Microsoft
> - برنامج الحماية من الفيروسات من Microsoft Defender أن يكون قيد التشغيل على الأقل في الوضع "غير النشط". لمزيد من المعلومات، [راجع برنامج الحماية من الفيروسات من Microsoft Defender التوافق](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).


## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.StopAndQuarantine|"إيقاف وفحص"
Application|Machine.Read.All|"قراءة كل ملفات تعريف الجهاز"
Application|Machine.ReadWrite.All|"قراءة كل معلومات الجهاز وكتابتها"
مفوض (حساب العمل أو المدرسة)|Machine.StopAndQuarantine|"إيقاف وفحص"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "إجراءات المعالجة النشطة" (راجع إنشاء أدوار وإدارتها [للحصول على](user-roles.md) مزيد من المعلومات)
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/StopAndQuarantineFile
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
Sha1|سلسلة|Sha1 من الملف للتوقف والعزل على الجهاز. **مطلوب**.

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 201 - رمز الاستجابة الذي تم إنشاؤه و"إجراء [الجهاز](machineaction.md) " في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/StopAndQuarantineFile 
```

```json
{
  "Comment": "Stop and quarantine file on machine due to alert 441688558380765161_2136280442",
  "Sha1": "87662bc3d60e4200ceaf7aae249d1c343f4b83c9"
}
```
