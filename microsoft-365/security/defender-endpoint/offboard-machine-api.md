---
title: إيقاف تشغيل واجهة برمجة تطبيقات الجهاز
description: تعرف على كيفية استخدام واجهة برمجة التطبيقات لإلغاء إلحاق جهاز من Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، جمع حزمة التحقيق
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
ms.openlocfilehash: a9e46b428500b41b143585434f7a16c13227db1c
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669749"
---
# <a name="offboard-machine-api"></a>إيقاف تشغيل واجهة برمجة تطبيقات الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

جهاز إيقاف تشغيل من Defender لنقطة النهاية.

## <a name="limitations"></a>القيود

- قيود المعدل لواجهة برمجة التطبيقات هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

  [!include[Machine actions note](../../includes/machineactionsnote.md)]

> [!NOTE]
> يتم دعم واجهة برمجة التطبيقات هذه على Windows 11 أو Windows 10 أو الإصدار 1703 والإصدارات الأحدث أو Windows Server 2019 والإصدارات الأحدث.
>
> واجهة برمجة التطبيقات هذه غير معتمدة على أجهزة MacOS أو Linux.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [Use Defender لواجهات برمجة التطبيقات لنقطة النهاية](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Machine.Offboard|'جهاز Offboard'
مفوض (حساب العمل أو المؤسسة التعليمية)|Machine.Offboard|'جهاز Offboard'

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يحتاج المستخدم إلى دور AD "global مسؤول"
> - يحتاج المستخدم إلى الوصول إلى الجهاز، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md) لمزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machines/{id}/offboard
```

يمكن العثور على معرف الجهاز في عنوان URL عند تحديد الجهاز. بشكل عام، هو رقم أبجدي رقمي مكون من 40 رقما يمكن العثور عليه في عنوان URL.

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسله|التطبيق/json. **مطلوب**.

## <a name="request-body"></a>نص الطلب

في نص الطلب، قم بتوفير كائن JSON بالمعلمات التالية:

المعلمه|نوع|الوصف
---|---|---
التعليق|سلسلة|تعليق لإقرانه بالإجراء. **مطلوب**.

## <a name="response"></a>استجابه

إذا نجحت، يقوم هذا الأسلوب بإرجاع 200 - رمز استجابة تم إنشاؤه و [Machine Action](machineaction.md) في نص الاستجابة.

## <a name="example"></a>المثال

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
