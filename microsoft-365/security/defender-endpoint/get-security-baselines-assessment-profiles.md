---
title: ملفات تعريف تقييم خطوط الأمان الأساسية
description: يوفر معلومات حول ملفات تعريف تقييم خطوط الأمان الأساسية لواجهات برمجة التطبيقات التي تسحب بيانات "إدارة المخاطر والثغرات الأمنية". هناك استدعاءات واجهة برمجة تطبيقات مختلفة للحصول على أنواع مختلفة من البيانات. بشكل عام، يحتوي كل استدعاء لواجهة برمجة التطبيقات على البيانات المطلوبة للأجهزة في مؤسستك.
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
ms.openlocfilehash: ca110cfba43b95790114928f1c0d3adcae46f087
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368505"
---
# <a name="list-all-security-baselines-assessment-profiles"></a>سرد كافة ملفات تعريف تقييم أساسيات الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender - تحديث](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ [التسجيل للحصول على إصدار تجريبي مجاني.- تحديث](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="1-get-security-baselines-assessment-profiles"></a>1. الحصول على ملفات تعريف تقييم أساسيات الأمان

تسترد واجهة برمجة التطبيقات هذه قائمة بجميع ملفات تعريف تقييم أساسات الأمان التي أنشأتها المؤسسة.  

### <a name="11-parameters"></a>1.1 معلمات

- يدعم استعلامات OData V4.  
- عوامل التشغيل المدعومة من OData:  
  - $filter على: id,name, operatingSystem, operatingSystemVersion, status, settingsNumber, passedDevices, totalDevices  
  - $top بقيمة قصوى تبلغ 10000.  
  - $skip.

### <a name="12-http-request"></a>طلب HTTP 1.2

```http
GET:/api/baselineProfiles
```

### <a name="13-request-headers"></a>1.3 عناوين الطلب

الاسم|نوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

### <a name="14-properties"></a>1.4 خصائص

|الخاصيه | نوع | الوصف |
|:---|:---|:---|
|معرف | سلسلة | معرف فريد لملف تعريف الأساس المحدد.
|اسم | سلسلة | اسم ملف التعريف.
|وصف | سلسلة | وصف ملف التعريف.
|المعيار | سلسلة | معيار ملف التعريف.
|الإصدار | سلسلة | إصدار ملف التعريف.
|نظام التشغيل|سلسلة|نظام التشغيل القابل للتطبيق لملف التعريف.
|operatingSystemVersion|سلسلة|إصدار نظام التشغيل القابل للتطبيق لملف التعريف.
|حاله|منطقي|الإشارة إلى ما إذا كان ملف التعريف نشطا أم لا
|مستوى التوافق|سلسلة|مستوى التوافق الذي تم اختياره لملف التعريف.
|رقم الإعدادات|الباحث|عدد التكوينات المحددة في ملف التعريف.
|createdBy|سلسلة|المستخدم الذي أنشأ ملف التعريف هذا.
|lastUpdatedBy|Datetime|آخر مستخدم قام بتعديل ملف التعريف هذا.
|createdOnTimeOffset|Datetime|تاريخ ووقت إنشاء ملف التعريف.
|lastUpdateTimeOffset|Datetime|تاريخ ووقت آخر تحديث لملف التعريف.
|passedDevices|الباحث|عدد الأجهزة المطبقة على ملف التعريف هذا المتوافقة مع كافة تكوينات ملف التعريف.
|totalDevices|الباحث|عدد الأجهزة المطبقة على ملف التعريف هذا.

## <a name="15-example"></a>مثال 1.5

### <a name="151-request-example"></a>مثال على طلب 1.5.1

```http
GET https://api.securitycenter.microsoft.com/api/baselineProfiles 
```

### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json
{  
    "@odata.context": "https:// api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.PublicBaselineProfileDto)",  
    "value": 
    [  
        {  
            "id": "02bcbb9d-d197-479e-811e-1cd5a6f9f8fa",  
            "name": "Windows 10 build 1909 CIS profile",  
            "description": "important",  
            "benchmark": "CIS",  
            "version": "1.0.0",  
            "operatingSystem": "Windows 10",  
            "operatingSystemVersion": "1909",  
            "status": true,  
            "complianceLevel": "Level 1 (L1) - Corporate/Enterprise Environment (general use)",  
            "settingsNumber": 51,  
            "createdBy": "user@org.net",  
            "lastUpdatedBy": null,  
            "createdOnTimestampUTC": "0001-01-01T00:00:00Z",  
            "lastUpdateTimestampUTC": "0001-01-01T00:00:00Z",  
            "passedDevices": 0,  
            "totalDevices": 10  
        }  
     ]  
}  
```

## <a name="see-also"></a>راجع أيضًا

- [تصدير تقييم أسس الأمان](export-security-baseline-assessment.md)
- [الحصول على تكوينات تقييم أساسيات الأمان](get-security-baselines-assessment-configurations.md)
