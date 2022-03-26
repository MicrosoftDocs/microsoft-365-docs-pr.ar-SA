---
title: فقدان KBs حسب الم ID الخاص بالبرمجيات
description: استرداد تحديثات الأمان المفقودة حسب "معرّف البرنامج"
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، القائمة، الملف، المعلومات، معلومات، برنامج id، & إدارة الثغرات الأمنية api، Microsoft Defender for Endpoint tvm api
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 692d0ca44a46ef11bd7ab3e9bb32a0c98dd7e01a
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573828"
---
# <a name="get-missing-kbs-by-software-id"></a>فقدان KBs حسب الم ID الخاص بالبرمجيات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد KBs (تحديثات الأمان) المفقودة حسب "معرّف البرنامج"

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة](apis-intro.md) تطبيقات نقطة النهاية للحصول على التفاصيل.

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Software.read.All|"قراءة معلومات برنامج إدارة المخاطر والضعف"
مفوض (حساب العمل أو المدرسة)|Software.Read|"قراءة معلومات برنامج إدارة المخاطر والضعف"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/Software/{Id}/getmissingkbs
```

## <a name="request-header"></a>طلب رأس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح، ترجع هذه الطريقة 200 موافق، مع فقدان بيانات kb للبرنامج المحدد في الجسم.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/Software/microsoft-_-edge/getmissingkbs
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.


```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicProductFixDto)",
    "value": [
         {
            "id": "4540673",
            "name": "March 2020 Security Updates",
            "productsNames": [
                "edge"
            ],
            "url": "https://catalog.update.microsoft.com/v7/site/Search.aspx?q=KB4540673",
            "machineMissedOn": 240,
            "cveAddressed": 14
         },
         ...
        ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة المخاطر المستندة إلى & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [مخزون & برنامج الضعف](/microsoft-365/security/defender-endpoint/tvm-software-inventory)
