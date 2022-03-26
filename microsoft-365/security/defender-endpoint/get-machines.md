---
title: API (API) أجهزة القائمة
description: تعرف على كيفية استخدام API (برمجة تطبيقات) أجهزة القائمة لاسترداد مجموعة من الأجهزة التي تواصلت مع Microsoft Defender لسحابة نقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، الأجهزة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.topic: article
ms.collection: M365-security-compliance
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 6e522f2baac234097ed75d26eb1427719211a7de
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570507"
---
# <a name="list-machines-api"></a>API (API) أجهزة القائمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد مجموعة من [الأجهزة](machine.md) التي تواصلت مع سحابة نقطة النهاية ل Microsoft Defender.

يدعم [استعلامات OData V4](https://www.odata.org/documentation/).

يتم دعم استعلام OData `$filter` على: `computerDnsName`و و `version``deviceValue``id`و `aadDeviceId`و `machineTags`و `lastSeen`و و`exposureLevel``onboardingStatus` و `lastIpAddress``rbacGroupId``healthStatus``osPlatform``riskScore` .
<br>```$stop``` مع القيمة القصوى 10000
<br>```$skip``` الاطلاع على أمثلة في [استعلامات OData باستخدام Defender for Endpoint](exposed-apis-odata-samples.md)

## <a name="limitations"></a>القيود

1. يمكنك الحصول على الأجهزة التي رأيتها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.
2. الحد الأقصى لحجم الصفحة هو 10000.
3. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة. 

## <a name="permissions"></a>الأذونات

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Machine.Read.All|"قراءة كل ملفات تعريف الجهاز"
Application|Machine.ReadWrite.All|"قراءة كل معلومات الجهاز وكتابتها"
مفوض (حساب العمل أو المدرسة)|Machine.Read|"قراءة معلومات الجهاز"
مفوض (حساب العمل أو المدرسة)|Machine.ReadWrite|"قراءة معلومات الجهاز وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - ستتضمن الاستجابة الأجهزة فقط، التي يمكن للمستخدم الوصول إليها، استنادا إلى إعدادات مجموعة الأجهزة (راجع [إنشاء مجموعات](machine-groups.md) الأجهزة وإدارتها للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجحت الأجهزة وكانت موجودة - 200 موافق [مع قائمة كيانات](machine.md) الأجهزة في الجسم. إذا لم يكن هناك أجهزة حديثة - 404 لم يتم العثور عليها.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Machines",
    "value": [
        {
            "id": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
            "computerDnsName": "mymachine1.contoso.com",
            "firstSeen": "2018-08-02T14:55:03.7791856Z",
            "lastSeen": "2018-08-02T14:55:03.7791856Z",
            "osPlatform": "Windows10" "Windows11",
            "version": "1709",
            "osProcessor": "x64",
            "lastIpAddress": "172.17.230.209",
            "lastExternalIpAddress": "167.220.196.71",
            "osBuild": 18209,
            "healthStatus": "Active",
            "rbacGroupId": 140,
            "rbacGroupName": "The-A-Team",
            "riskScore": "Low",
            "exposureLevel": "Medium",
            "isAadJoined": true,
            "aadDeviceId": "80fe8ff8-2624-418e-9591-41f0491218f9",
            "machineTags": [ "test tag 1", "test tag 2" ]
        }
        ...
    ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [استعلامات OData باستخدام Microsoft Defender ل Endpoint](exposed-apis-odata-samples.md)
