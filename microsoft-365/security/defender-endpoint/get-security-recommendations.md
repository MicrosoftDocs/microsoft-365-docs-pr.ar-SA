---
title: الحصول على توصيات الأمان
description: استرداد مجموعة من توصيات الأمان المتعلقة بمعرف جهاز معين.
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، الحصول على، قائمة، ملف، معلومات، توصية الأمان لكل جهاز، واجهة برمجة تطبيقات إدارة الثغرات الأمنية & التهديد، واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية tvm
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
ms.openlocfilehash: e00937145cfff6eb9a0996683eacfb424b68091b
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020022"
---
# <a name="get-security-recommendations"></a>الحصول على توصيات الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ تعرف على المزيد حول كيفية التسجيل في [الإصدار التجريبي من المعاينة العامة إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

استرداد مجموعة من توصيات الأمان المتعلقة بمعرف جهاز معين.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application|SecurityRecommendation.Read.All|'قراءة معلومات توصية أمان إدارة المخاطر والثغرات الأمنية'
مفوض (حساب العمل أو المؤسسة التعليمية)|SecurityRecommendation.Read|'قراءة معلومات توصية أمان إدارة المخاطر والثغرات الأمنية'

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{machineId}/recommendations
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت، ترجع هذه الطريقة 200 موافق مع توصيات الأمان في النص الأساسي.

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/recommendations
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-git-scm-_-git",
            "productName": "git",
            "recommendationName": "Update Git to version 2.24.1.2",
            "weaknesses": 3,
            "vendor": "git-scm",
            "recommendedVersion": "2.24.1.2",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": false,
            "activeAlert": false,
            "associatedThreats": [],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 0,
            "totalMachineCount": 0,
            "exposedMachinesCount": 1,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Git"
        },
...
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة الثغرات الأمنية & المخاطر المستندة إلى المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [توصية أمان الثغرات الأمنية & المخاطر](/microsoft-365/security/defender-endpoint/tvm-security-recommendation)
