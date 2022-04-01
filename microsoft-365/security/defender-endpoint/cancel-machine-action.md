---
title: API (API) الإجراء "إلغاء الجهاز"
description: تعرف على كيفية إلغاء إجراء جهاز تم بدء تشغيله بالفعل
keywords: apis، رسم api،
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
ms.openlocfilehash: fc4191043e19df7fea4f350d85acd78d2eca1551
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579627"
---
# <a name="cancel-machine-action-api"></a>API (API) الإجراء "إلغاء الجهاز"

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2146631)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2146631)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إلغاء إجراء جهاز تم بدء تشغيله بالفعل لم يكن في الحالة النهائية بعد (مكتمل أو ملغى أو فشل).

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md).

|نوع الإذن|الإذن|اسم عرض الأذونات|
|---|---|---|
|Application|Machine.CollectForensics <br> Machine.Isolate <br> Machine.RestrictExecution <br> Machine.Scan <br> Machine.Offboard <br> Machine.StopAndQuarantine <br> Machine.LiveResponse|جمع الطب الشرعي <br>جهاز عزل<br>تقييد تنفيذ التعليمات البرمجية<br>  جهاز المسح الضوئي<br>  جهاز Offboard<br> إيقاف وفحص<br> تشغيل الاستجابة المباشرة على جهاز معين|
|مفوض (حساب العمل أو المدرسة)|Machine.CollectForensics<br> Machine.Isolate  <br>Machine.RestrictExecution<br> Machine.Scan<br> Machine.Offboard<br> Machine.StopAndQuarantineMachine.LiveResponse|جمع الطب الشرعي<br> جهاز عزل<br>  تقييد تنفيذ التعليمات البرمجية<br> جهاز المسح الضوئي<br>جهاز Offboard<br> إيقاف وفحص<br> تشغيل الاستجابة المباشرة على جهاز معين|

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/machineactions/<machineactionid>/cancel
```

## <a name="request-headers"></a>طلب رؤوس

|الاسم|النوع|الوصف|
|---|---|---|
|التخويل|سلسلة|حامل {token}. مطلوب.|
|نوع المحتوى|سلسلة|application/json. مطلوب.|

## <a name="request-body"></a>طلب الحصول على "هيئة"

|المعلمة|النوع|الوصف|
|---|---|---|
|تعليق|سلسلة|تعليق لاقرانه مع إجراء الإلغاء.|

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع رمز الاستجابة 200، موافق مع كيان إجراء آلي. إذا لم يتم العثور على كيان إجراء الجهاز الذي له الم id المحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

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

## <a name="related-topic"></a>موضوع ذو صلة

- [الحصول على API للعمل على الجهاز](get-machineaction-object.md)
