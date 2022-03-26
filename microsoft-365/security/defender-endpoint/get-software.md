---
title: قائمة البرامج
description: استرداد قائمة مخزون البرامج
keywords: apis، apis الخاصة بالرسم البياني، apis المعتمدة، الحصول، القائمة، الملف، المعلومات، مخزون البرامج، & إدارة الثغرات الأمنية api، Microsoft Defender for Endpoint tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 0f2db10e24212808253e197c562468c03f3ae293
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63572324"
---
# <a name="list-software-inventory-api"></a>قائمة ب API لمخزون البرامج

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد مخزون برامج المؤسسة.
<br>يدعم [استعلامات OData V4](https://www.odata.org/documentation/).
<br>عوامل التشغيل المعتمدة في OData:
<br>```$filter``` على:  ```id```، ```name```، والخصائص ```vendor``` .
<br>```$top``` مع الحد الأقصى لقيمة 10000.
<br>```$skip```.
<br>راجع الأمثلة في [استعلامات OData باستخدام Microsoft Defender ل Endpoint](exposed-apis-odata-samples.md).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة](apis-intro.md) تطبيقات نقطة النهاية للحصول على التفاصيل.

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Software.read.All|"قراءة معلومات برنامج إدارة المخاطر والضعف"
مفوض (حساب العمل أو المدرسة)|Software.Read|"قراءة معلومات برنامج إدارة المخاطر والضعف"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/Software
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجحت هذه الطريقة، ترجع هذه الطريقة 200 موافق مع مخزون البرامج في الجسم.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/Software
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Software",
    "value": [
            {
                "id": "microsoft-_-edge",
                "name": "edge",
                "vendor": "microsoft",
                "weaknesses": 467,
                "publicExploit": true,
                "activeAlert": false,
                "exposedMachines": 172,
                "impactScore": 2.39947438
            }
            ...
        ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة المخاطر المستندة إلى & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [مخزون & برنامج الضعف](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
