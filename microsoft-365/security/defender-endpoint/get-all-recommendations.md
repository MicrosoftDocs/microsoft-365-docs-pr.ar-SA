---
title: سرد كل التوصيات
description: استرداد قائمة بكل توصيات الأمان التي تؤثر على المؤسسة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول على توصيات الأمان، Microsoft Defender for Endpoint tvm api، إدارة المخاطر والثغرات الأمنية، إدارة المخاطر والثغرات الأمنية api
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
ms.openlocfilehash: 727b20e6784016aac423a74c6b564fa96d6f5733
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573315"
---
# <a name="list-all-recommendations"></a>سرد كل التوصيات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

استرداد قائمة بكل توصيات الأمان التي تؤثر على المؤسسة.


## <a name="api-description"></a>وصف API

إرجاع معلومات حول كل توصيات الأمان التي تؤثر على المؤسسة.

*URL:* GET:/api/recommendations
<br>يدعم [استعلامات OData V4](https://www.odata.org/documentation/).
<br>عوامل التشغيل المعتمدة في OData:
<br>```$filter``` على:  ```id```، ، ```productName```، ```vendor```، ```recommendedVersion```، ```recommendationCategory```، ```subCategory```، ، ```severityScore```، ```remediationType```، ```recommendedProgram```، ، ```recommendedVendor```والخصائص ```status``` .
<br>```$top``` مع الحد الأقصى لقيمة 10000.
<br>```$skip```.
<br>راجع الأمثلة في [استعلامات OData باستخدام Microsoft Defender ل Endpoint](exposed-apis-odata-samples.md).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة](apis-intro.md) تطبيقات نقطة النهاية للحصول على التفاصيل.

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|SecurityRecommendation.Read.All|"قراءة معلومات توصيات الأمان الخاصة بإدارة المخاطر والضعف"
مفوض (حساب العمل أو المدرسة)|SecurityRecommendation.Read |"قراءة معلومات توصيات الأمان الخاصة بإدارة المخاطر والضعف"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/recommendations
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع 200 موافق مع قائمة توصيات الأمان في الجسم.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/recommendations
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11",
            "productName": "windows_10" "Windows_11",
            "recommendationName": "Update Windows 10" "Update Windows 11",
            "weaknesses": 397,
            "vendor": "microsoft",
            "recommendedVersion": "",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": true,
            "activeAlert": false,
            "associatedThreats": [
                "3098b8ef-23b1-46b3-aed4-499e1928f9ed",
                "40c189d5-0330-4654-a816-e48c2b7f9c4b",
                "4b0c9702-9b6c-4ca2-9d02-1556869f56f8",
                "e8fc2121-3cf3-4dd2-9ea0-87d7e1d2b29d",
                "94b6e94b-0c1d-4817-ac06-c3b8639be3ab"
            ],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 7.674418604651163,
            "totalMachineCount": 37,
            "exposedMachinesCount": 7,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Windows 10" "Windows 11"
        }
        ...
     ]
}
```

## <a name="see-also"></a>راجع أيضًا

- [إدارة المخاطر المستندة إلى & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [توصية أمان & المخاطر](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
