---
title: الحصول على واجهة برمجة تطبيقات مجموعة مجموعات أجهزة RBAC
description: تعرف على كيفية استخدام واجهة برمجة تطبيقات مجموعة Get KB لاسترداد مجموعة من مجموعات أجهزة RBAC في Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، get، RBAC، المجموعة
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
ms.openlocfilehash: 528b80b3c40fd7df853190788abb347ed90a82e4
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825157"
---
# <a name="get-kb-collection-api"></a>الحصول على واجهة برمجة تطبيقات مجموعة KB

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد مجموعة من مجموعات أجهزة RBAC.

## <a name="permissions"></a>الأذونات

يحتاج المستخدم إلى أذونات القراءة.

## <a name="http-request"></a>طلب HTTP

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
```

## <a name="request-headers"></a>عناوين الطلبات

راس|قيمه
:---|:---
التخويل | حامل {token}. **مطلوب**.
نوع المحتوى | تطبيق/json

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت - 200 موافق.

## <a name="example"></a>المثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://graph.microsoft.com/testwdatppreview/machinegroups
Content-type: application/json
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.
يحتوي معرف الحقل على **معرف** مجموعة الأجهزة ومساوي ل **rbacGroupId** للحقل في معلومات الأجهزة.
الحقل **غير المجمع** صحيح فقط لمجموعة واحدة لكافة الأجهزة التي لم يتم تعيينها إلى أي مجموعة. هذه المجموعة كالمعتاد لها اسم "UnassignedGroup".

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
