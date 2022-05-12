---
title: تكوينات تقييم خطوط الأمان الأساسية
description: يوفر معلومات حول تكوينات تقييم خطوط الأمان الأساسية التي تسحب بيانات "إدارة المخاطر والثغرات الأمنية". هناك استدعاءات واجهة برمجة تطبيقات مختلفة للحصول على أنواع مختلفة من البيانات. بشكل عام، يحتوي كل استدعاء لواجهة برمجة التطبيقات على البيانات المطلوبة للأجهزة في مؤسستك.
keywords: api, apis, export assessment, per device assessment, per machine assessment, vulnerability assessment report, device vulnerability assessment, device vulnerability report, secure configuration assessment, secure configuration report, software vulnerabilities assessment, software vulnerability report, software vulnerability report, vulnerability report by machine,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: bf29fc20cf3e68abd931bcc27526003c85691ff5
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368506"
---
# <a name="list-security-baselines-assessment-configurations"></a>سرد تكوينات تقييم أساسيات الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender - تحديث](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ [التسجيل للحصول على إصدار تجريبي مجاني.- تحديث](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)


## <a name="1-get-all-security-baselines-assessment-configurations"></a>1. الحصول على كافة تكوينات تقييم أساسات الأمان

تسترد واجهة برمجة التطبيقات هذه قائمة بجميع تكوينات وإعدادات تقييم أسس الأمان المحتملة لجميع المعايير المتاحة.

### <a name="11-parameters"></a>1.1 معلمات

- يدعم استعلامات OData V4
- عوامل التشغيل المدعومة من OData:
  - `$filter` في:  `id`,  `category`,  `name`, `CCE`
  - `$top` بقيمة قصوى 10000
  - `$skip`

### <a name="12-http-request"></a>طلب HTTP 1.2

```http
GET /api/baselineConfigurations 
```

### <a name="13-request-headers"></a>1.3 عناوين الطلب

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

### <a name="14-response"></a>1.4 استجابة

إذا نجحت، يرجع هذا الأسلوب 200 موافق مع قائمة تكوينات الأساس في النص الأساسي.  

### <a name="15-properties"></a>1.5 خصائص

|الخاصيه | نوع | الوصف |
|:---|:---|:---|
|معرف | سلسلة | معرف فريد للتكوين المحدد في معيار الأساس.
|اسم | سلسلة | يظهر اسم التكوين في المعيار.
|وصف | سلسلة | وصف التكوين كما يظهر في المعيار.
|الفئه | سلسلة | فئة التكوين كما تظهر في المعيار.
|مستوى التوافق|سلسلة|مستوى الامتثال للمعيار حيث يظهر هذا التكوين.
|`cce`|الباحث|CCE لهذا التكوين كما يظهر في المعيار.
|الاساس المنطقي |سلسلة|الأساس المنطقي لهذا التكوين كما يظهر في المعيار. بالنسبة لمعيار STIG، لا يتم توفير ذلك لهذا التكوين.

## <a name="16-example"></a>مثال 1.6

### <a name="151-request-example"></a>مثال على طلب 1.5.1

```http
GET https://api.securitycenter.microsoft.com/api/baselineConfigurations
```

### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json
{  
    "@odata.context": " https://api-df.securitycenter.microsoft.com/api/$metadata#BaselineConfigurations ", 
    "value": [  
        {  
            "id": "1.1.8", 
            "name": "(L1) Ensure 'Allow importing of payment info' is set to 'Disabled'",  
            "description": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">This policy setting controls whether users are able to import payment information from another browser into Microsoft Edge as well as whether payment information is imported on first use.</p>",  
            "category": "Microsoft Edge",  
            "complianceLevels": [  
                "Level 1 (L1) - Corporate/Enterprise Environment (general use)",  
                "Level 2 (L2) - High Security/Sensitive Data Environment (limited functionality)"  
            ],  
            "cce": "",  
            "rationale": "<p xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">Having payment information automatically imported or allowing users to import payment data from another browser into Microsoft Edge could allow for sensitive data to be imported into Edge.</p>",  
            "remediation": "<div xmlns:xhtml=\"http://www.w3.org/1999/xhtml\">\r\n  <p>\r\n    <p>\r\nTo establish the recommended configuration via GP, set the following UI path to                 <span class=\"inline_block\">Disabled</span></p>\r\n    <code class=\"code_block\">Computer Configuration\\Policies\\Administrative Templates\\Microsoft Edge\\Allow importing of payment info\r\n</code>\r\n    <p>\r\n      <strong>Note:</strong>\r\n This Group Policy path may not exist by default. It is provided by the Group Policy template                 <span class=\"inline_block\">MSEdge.admx/adml</span>\r\n that can be downloaded from Microsoft                 <a href=\"https://www.microsoft.com/en-us/edge/business/download\">here</a>\r\n.              </p>\r\n    <p class=\"bold\">Impact:</p>\r\n    <p>\r\n      <p>Users will be unable to perform a payment information import from other browsers into Microsoft Edge.</p>\r\n    </p>\r\n  </p>\r\n</div>",  
            "benchmarkName": "CIS"  
"recommendedValue": [ 
                "Equals '0'" 
            ], 
            "source": [ 
                "hkey_local_machine\\software\\policies\\microsoft\\windows\\eventlog\\security\\retention" 
            ]
        }, 
    ] 
} 
```

## <a name="see-also"></a>راجع أيضًا

- [تصدير تقييم أسس الأمان](export-security-baseline-assessment.md)
- [الحصول على ملفات تعريف تقييم أساسيات الأمان](get-security-baselines-assessment-profiles.md)
