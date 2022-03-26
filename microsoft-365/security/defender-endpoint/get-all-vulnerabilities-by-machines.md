---
title: الحصول على جميع نقاط الضعف حسب الجهاز والبرامج
description: استرداد قائمة بكل الثغرات التي تؤثر على المؤسسة حسب الجهاز والبرامج
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول على معلومات الضعف، Microsoft Defender for Endpoint tvm api
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
ms.openlocfilehash: 45c29a70f97c681e6236f4327fed8e344d9dc8ac
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570668"
---
# <a name="list-vulnerabilities-by-machine-and-software"></a>الثغرات في القائمة حسب الجهاز والبرامج

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

استرداد قائمة بكل الثغرات التي تؤثر على المؤسسة لكل [جهاز](machine.md) [وبرامج.](software.md)

- إذا كانت الثغرة الأمنية بها KB إصلاح، ستظهر في الاستجابة.
- يدعم [استعلامات OData V4](https://www.odata.org/documentation/).
- يتم دعم استعلام `$filter` OData على الخصائص: `id`و و `cveId`و `machineId`و`fixingKbId``productName``productVersion``severity``productVendor`.
<br>```$stop``` مع القيمة القصوى 10000
<br>```$skip```

> [!TIP]
> هذه هي API رائعة [لتكامل Power BI](api-power-bi.md).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة](apis-intro.md) تطبيقات نقطة النهاية للحصول على التفاصيل.

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Vulnerability.Read.All|"قراءة معلومات ضعف إدارة المخاطر والنقاط الأمنية"
مفوض (حساب العمل أو المدرسة)|ثغرة أمنية.قراءة|"قراءة معلومات ضعف إدارة المخاطر والنقاط الأمنية"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/vulnerabilities/machinesVulnerabilities
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق مع قائمة نقاط الضعف في الجسم.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/vulnerabilities/machinesVulnerabilities
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicAssetVulnerabilityDto)",
    "value": [
        {
            "id": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21-_-CVE-2020-6494-_-microsoft-_-edge_chromium-based-_-81.0.416.77-_-",
            "cveId": "CVE-2020-6494",
            "machineId": "5afa3afc92a7c63d4b70129e0a6f33f63a427e21",
            "fixingKbId": null,
            "productName": "edge_chromium-based",
            "productVendor": "microsoft",
            "productVersion": "81.0.416.77",
            "severity": "Low"
        },
        {
            "id": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283-_-CVE-2016-3348-_-microsoft-_-windows_server_2012_r2-_-6.3.9600.19728-_-3185911",
            "cveId": "CVE-2016-3348",
            "machineId": "7a704e17d1c2977c0e7b665fb18ae6e1fe7f3283",
            "fixingKbId": "3185911",
            "productName": "windows_server_2012_r2",
            "productVendor": "microsoft",
            "productVersion": "6.3.9600.19728",
            "severity": "Low"
        },
        ...
    ]

}
```

## <a name="see-also"></a>راجع أيضًا

- [المخاطر المستندة إلى إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [نقاط الضعف في مؤسستك](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
