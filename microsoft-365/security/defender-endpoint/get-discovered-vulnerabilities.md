---
title: الحصول على نقاط الضعف المكتشفة
description: استرداد مجموعة من الثغرات الأمنية المكتشفة المتعلقة بمعرف جهاز معين.
keywords: واجهة برمجة التطبيقات، وواجهة برمجة تطبيقات الرسم البياني، وواجهة برمجة التطبيقات المدعومة، والحصول على، وقائمة، وملف، ومعلومات، ونقاط الضعف المكتشفة، وواجهة برمجة تطبيقات إدارة الثغرات الأمنية & التهديد، وواجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية tvm
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
ms.openlocfilehash: 95e350a6288ecefabe86aaa7b802deae0ffafaa1
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020000"
---
# <a name="get-discovered-vulnerabilities"></a>الحصول على نقاط الضعف المكتشفة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ تعرف على المزيد حول كيفية التسجيل في [الإصدار التجريبي من المعاينة العامة إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/get-defender-vulnerability-management.md).

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات
استرداد مجموعة من الثغرات الأمنية المكتشفة المتعلقة بمعرف جهاز معين.

## <a name="limitations"></a>القيود
1. قيود المعدل لواجهة برمجة التطبيقات هذه هي 50 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

نوع الإذن | اذن | اسم عرض الإذن
:---|:---|:---
Application |Vulnerability.Read.All | 'قراءة معلومات الثغرات الأمنية لإدارة المخاطر والثغرات الأمنية'
مفوض (حساب العمل أو المؤسسة التعليمية) | Vulnerability.Read | 'قراءة معلومات الثغرات الأمنية لإدارة المخاطر والثغرات الأمنية'

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{machineId}/vulnerabilities
```

## <a name="request-headers"></a>عناوين الطلبات

الاسم|نوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>نص الطلب

فارغه

## <a name="response"></a>استجابه

إذا نجحت، ترجع هذه الطريقة 200 موافق مع معلومات الثغرات الأمنية المكتشفة في النص الأساسي.

## <a name="example"></a>المثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/vulnerabilities
```

### <a name="response"></a>استجابه

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

- [إدارة الثغرات الأمنية & المخاطر المستندة إلى المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [الثغرات الأمنية في مؤسستك](/microsoft-365/security/defender-endpoint/tvm-weaknesses)
