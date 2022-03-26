---
title: درجة التعرض للقائمة حسب مجموعة الأجهزة
description: استرداد قائمة نقاط التعرض للضوء حسب مجموعة الأجهزة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، درجة التعرض للضوء، مجموعة الأجهزة، درجة التعرض لمجموعة الأجهزة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: ba046d35b6cf93754fc1daf3d2b211d69e6c27d8
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63571405"
---
# <a name="list-exposure-score-by-device-group"></a>درجة التعرض للقائمة حسب مجموعة الأجهزة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

استرداد درجة التعرض للضوء لكل مجموعة جهاز.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Score.Read.All|"قراءة نقاط إدارة المخاطر والضعف"
مفوض (حساب العمل أو المدرسة)|Score.Read|"قراءة نقاط إدارة المخاطر والضعف"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/exposureScore/ByMachineGroups
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
---|---|---
|التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق، مع قائمة نقاط التعرض للضوء لكل بيانات مجموعة جهاز في جزء الاستجابة.

## <a name="example"></a>مثال

### <a name="example-request"></a>طلب مثال

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/exposureScore/ByMachineGroups
```

### <a name="example-response"></a>مثال على استجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ExposureScore",
    "value": [
        {
            "time": "2019-12-03T09:51:28.214338Z",
            "score": 41.38041766305988,
            "rbacGroupName": "GroupOne"
        },
        {
            "time": "2019-12-03T09:51:28.2143399Z",
            "score": 37.403726933165366,
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة المخاطر المستندة إلى & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [درجة & التعرض للمخاطر](/microsoft-365/security/defender-endpoint/tvm-exposure-score)
