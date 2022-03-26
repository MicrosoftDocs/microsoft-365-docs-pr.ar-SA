---
title: الحصول على API مجموعة مجموعات RBAC على جهاز
description: تعرف على كيفية استخدام API للحصول على مجموعة KB لاسترداد مجموعة من مجموعات أجهزة RBAC في Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول على، RBAC، مجموعة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: leonidzh
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 10/07/2018
ms.custom: api
ms.openlocfilehash: 699a7e2738f1e0c89977bd152832f45935a06387
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570508"
---
# <a name="get-kb-collection-api"></a>الحصول على API مجموعة KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد مجموعة من مجموعات أجهزة RBAC.

## <a name="permissions"></a>الأذونات

يحتاج المستخدم إلى أذونات القراءة.

## <a name="http-request"></a>طلب HTTP

```http
GET /testwdatppreview/machinegroups
```

## <a name="request-headers"></a>طلب رؤوس

رأس|القيمة
:---|:---
التخويل | حامل {token}. **مطلوب**.
نوع المحتوى | application/json

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح - 200 موافق.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.
يحتوي "معرّف الحقل" على " **معرّف** مجموعة الأجهزة" ويساوي " **rbacGroupId** " الحقل في معلومات الأجهزة.
يتم **إلغاء تجميع** الحقل فقط لمجموعة واحدة لكل الأجهزة التي لم يتم تعيينها إلى أي مجموعة. هذه المجموعة كالعادة لها اسم "مجموعة غير معينة".

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context":"https://graph.microsoft.com/testwdatppreview/$metadata#MachineGroups",
    "@odata.count":7,
    "value":[
        {
            "id":86,
            "name":"UnassignedGroup",
            "description":"",
            "ungrouped":true},
        ...
}
```
