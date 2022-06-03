---
title: إلغاء واجهة برمجة تطبيقات إجراء الجهاز
description: تعرف على كيفية إلغاء إجراء جهاز تم تشغيله بالفعل
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني،
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 08f302a541e60cb2844dc6ef2b91509556f03330
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873721"
---
# <a name="cancel-machine-action-api"></a>إلغاء واجهة برمجة تطبيقات إجراء الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/defender-endpoint)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

إلغاء إجراء جهاز تم تشغيله بالفعل لم يتم تشغيله بعد في الحالة النهائية (مكتمل، تم الإلغاء، فشل).

## <a name="limitations"></a>القيود

1. قيود المعدل لواجهة برمجة التطبيقات هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع ["بدء الاستخدام](apis-intro.md)".

|نوع الإذن|اذن|اسم عرض الإذن|
|---|---|---|
|Application|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|جمع الأدلة الجنائية <br>جهاز عزل<br>تقييد تنفيذ التعليمات البرمجية<br>  جهاز المسح الضوئي<br>  جهاز إيقاف التجهيز<br> الإيقاف والعزل<br> تشغيل الاستجابة المباشرة على جهاز معين|
|مفوض (حساب العمل أو المؤسسة التعليمية)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|جمع الأدلة الجنائية<br> جهاز عزل<br>  تقييد تنفيذ التعليمات البرمجية<br> جهاز المسح الضوئي<br>جهاز إيقاف التجهيز<br> الإيقاف والعزل<br> تشغيل الاستجابة المباشرة على جهاز معين|

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>عناوين الطلبات

|الاسم|نوع|الوصف|
|---|---|---|
|التخويل|سلسلة|حامل {token}. مطلوب.|
|نوع المحتوى|سلسله|التطبيق/json. مطلوب.|

## <a name="request-body"></a>نص الطلب

|المعلمه|نوع|الوصف|
|---|---|---|
|التعليق|سلسلة|تعليق لإقرانه بإجراء الإلغاء.|

## <a name="response"></a>استجابه

إذا نجحت، يقوم هذا الأسلوب بإرجاع 200، تعليمة برمجية استجابة موافق مع كيان إجراء الجهاز. إذا لم يتم العثور على كيان إجراء الجهاز ذي المعرف المحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>المثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```HTTP
POST
https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/cancel
```

```JSON
{
    "Comment": "Machine action was canceled by automation"
}
```

## <a name="related-topic"></a>الموضوع ذو الصلة

- [الحصول على واجهة برمجة تطبيقات إجراء الجهاز](get-machineaction-object.md)
