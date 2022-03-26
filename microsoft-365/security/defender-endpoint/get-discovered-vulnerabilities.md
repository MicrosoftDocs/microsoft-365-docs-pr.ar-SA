---
title: الحصول على نقاط الضعف المكتشفة
description: استرداد مجموعة من نقاط الضعف المكتشفة المرتبطة بمرجع جهاز معين.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، القائمة، الملف، المعلومات، نقاط الضعف المكتشفة، & إدارة الثغرات الأمنية api، Microsoft Defender for Endpoint tvm api
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
ms.openlocfilehash: 282c9b33efbb261e4d8cb0180cda0f3bc7e03584
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573327"
---
# <a name="get-discovered-vulnerabilities"></a>الحصول على نقاط الضعف المكتشفة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API
استرداد مجموعة من نقاط الضعف المكتشفة المرتبطة بمرجع جهاز معين.

## <a name="limitations"></a>القيود
1. قيود السعر ل API هذه هي 50 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن | الإذن | اسم عرض الأذونات
:---|:---|:---
Application |Vulnerability.Read.All | "قراءة معلومات ضعف إدارة المخاطر والنقاط الأمنية"
مفوض (حساب العمل أو المدرسة) | ثغرة أمنية.قراءة | "قراءة معلومات ضعف إدارة المخاطر والنقاط الأمنية"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{machineId}/vulnerabilities
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق مع معلومات الثغرة الأمنية التي تم اكتشافها في الجسم.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/vulnerabilities
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
        {
            "id": "CVE-2019-1348",
            "name": "CVE-2019-1348",
            "description": "Git could allow a remote attacker to bypass security restrictions, caused by a flaw in the --export-marks option of git fast-import. By persuading a victim to import specially-crafted content, an attacker could exploit this vulnerability to overwrite arbitrary paths.",
            "severity": "Medium",
            "cvssV3": 4.3,
            "exposedMachines": 1,
            "publishedOn": "2019-12-13T00:00:00Z",
            "updatedOn": "2019-12-13T00:00:00Z",
            "publicExploit": false,
            "exploitVerified": false,
            "exploitInKit": false,
            "exploitTypes": [],
            "exploitUris": []
        }
    ]
}
```

## <a name="see-also"></a>راجع أيضًا

- [إدارة المخاطر المستندة إلى & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [نقاط الضعف في مؤسستك](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
