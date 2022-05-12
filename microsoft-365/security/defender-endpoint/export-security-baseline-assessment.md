---
title: أساليب وخصائص تقييم أساس الأمان لكل جهاز
description: يوفر معلومات حول واجهات برمجة التطبيقات لأساسيات الأمان التي تسحب بيانات "إدارة المخاطر والثغرات الأمنية". هناك استدعاءات واجهة برمجة تطبيقات مختلفة للحصول على أنواع مختلفة من البيانات. بشكل عام، يحتوي كل استدعاء لواجهة برمجة التطبيقات على البيانات المطلوبة للأجهزة في مؤسستك.
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
ms.openlocfilehash: 1cf677ccf4716ede6182db48bb1e1a2622fd9abe
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368482"
---
# <a name="export-security-baselines-assessment-per-device"></a>تصدير تقييم أسس الأمان لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender - تحديث](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة إدارة الثغرات الأمنية في Microsoft Defender؟ [التسجيل للحصول على إصدار تجريبي مجاني.- تحديث](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

هناك استدعاءات واجهة برمجة تطبيقات مختلفة للحصول على أنواع مختلفة من البيانات. بشكل عام، يحتوي كل استدعاء لواجهة برمجة التطبيقات على البيانات المطلوبة للأجهزة في مؤسستك.

- **استجابة JSON**  تسحب واجهة برمجة التطبيقات جميع البيانات في مؤسستك كاستجابات JSON. هذا الأسلوب هو الأفضل _للمؤسسات الصغيرة التي تحتوي على أقل من 100 كيلوبايت_. الاستجابة مرقمة الصفحات، بحيث يمكنك استخدام \@حقل odata.nextLink من الاستجابة لإحضار النتائج التالية.

- **عبر الملفات** يتيح حل واجهة برمجة التطبيقات هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. لذلك، يوصى به للمؤسسات الكبيرة، مع أكثر من 100 كيلوبايت من الأجهزة. تسحب واجهة برمجة التطبيقات هذه جميع البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل جميع البيانات من Azure Storage. يمكنك تنزيل البيانات من Azure Storage كما يلي:
  - اتصل بواجهة برمجة التطبيقات للحصول على قائمة بتنزيل عناوين URL مع جميع بيانات مؤسستك.
  - قم بتنزيل جميع الملفات باستخدام عناوين URL التنزيل ومعالجة البيانات كما تريد.

البيانات التي يتم جمعها باستخدام إما "_استجابة JSON_ أو _عبر الملفات_" هي اللقطة الحالية للحالة الحالية. لا يحتوي على بيانات تاريخية. لجمع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!NOTE]
> ما لم تتم الإشارة إلى خلاف ذلك، فإن جميع أساليب تقييم أساس أمان التصدير المدرجة هي **_التصدير الكامل_** **_والجهاز_** (يشار إليها أيضا **_حسب الجهاز_**)

## <a name="1-export-security-baselines-assessment-json-response"></a>1. تصدير تقييم خطوط أساس الأمان (استجابة JSON)

### <a name="11-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 1.1

إرجاع كافة تقييمات خطوط الأمان الأساسية لجميع الأجهزة، على أساس كل جهاز. يقوم بإرجاع جدول مع إدخال منفصل لكل مجموعة فريدة من DeviceId و ProfileId و ConfigurationId.

#### <a name="12-limitations"></a>1.2 القيود

- الحد الأقصى لحجم الصفحة هو 200,000.
- قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="13-parameters"></a>1.3 معلمات

- حجم الصفحة (الافتراضي = 50,000): عدد النتائج في الاستجابة.
- $top: عدد النتائج التي سيتم إرجاعها (لا ترجع @odata.nextLink وهكذا لا تسحب كافة البيانات).

### <a name="14-http-request"></a>طلب HTTP 1.4

```http
GET /api/machines/baselineComplianceAssessmentByMachine
```

### <a name="15-properties-json-response"></a>1.5 خصائص (استجابة JSON)

> [!NOTE]
> كل سجل هو تقريبا 1 كيلوبايت من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار المعلمة pageSize الصحيحة.
>
> قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها. استخدم الأعمدة الموثقة فقط.
>
> يتم سرد الخصائص المعرفة في الجدول التالي أبجديا حسب معرف الخاصية. عند تشغيل واجهة برمجة التطبيقات هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.

الخاصية (المعرف)|نوع البيانات|الوصف
:---|:---|:---
|معرف التكوين|سلسلة|معرف فريد لتكوين معين في معيار الأساس.
|معرف ملف التعريف|سلسلة|معرف فريد لملف التعريف الذي تم تقييمه.
|معرف الجهاز|سلسلة|معرف فريد للجهاز في الخدمة.
|اسم الجهاز|سلسلة|اسم المجال المؤهل بالكامل (FQDN) للجهاز.
|isApplicable|منطقي|يشير إلى ما إذا كان التكوين قابلا للتطبيق على هذا الجهاز.
|isCompliant|منطقي|يشير إلى ما إذا كان الجهاز متوافقا مع التكوين.
|id|سلسلة|معرف فريد للسجل، وهو مزيج من DeviceId و ProfileId و ConfigurationId.
|osVersion|سلسلة|إصدار معين من نظام التشغيل الذي يعمل على الجهاز.
|osPlatform|سلسلة|نظام التشغيل الأساسي الذي يعمل على الجهاز. أنظمة تشغيل محددة مع اختلافات داخل نفس العائلة، مثل Windows 10 Windows 11. راجع [أنظمة التشغيل والأنظمة الأساسية المدعومة من TVM](tvm-supported-os.md) للحصول على التفاصيل.
|rbacGroupId|الباحث|معرف مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين الجهاز إلى أي مجموعة RBAC، فسيتم "إلغاء تعيين القيمة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".
|rbacGroupName|سلسلة|مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين الجهاز إلى أي مجموعة RBAC، فسيتم "إلغاء تعيين القيمة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".
|DataCollectionTimeOffset|Datetime|الوقت الذي تم فيه جمع البيانات من الجهاز. قد لا يظهر هذا الحقل إذا لم يتم تجميع أي بيانات.
|ComplianceCalculationTimeOffset|Datetime|وقت إجراء عملية حساب التقييم.
|RecommendedValue|سلسلة|مجموعة من القيم المتوقعة لإعداد الجهاز الحالي لتكون شكوى.
|القيمة الحالية|سلسلة|مجموعة من القيم المكتشفة الموجودة على الجهاز.
|مصدر|سلسلة|مسار التسجيل أو الموقع الآخر المستخدم لتحديد إعداد الجهاز الحالي.

## <a name="16-example"></a>مثال 1.6

### <a name="161-request-example"></a>مثال على طلب 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json
{ 
"@odata.context": " https://api.securitycenter.microsoft.com /api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetBaselineAssessment)", 
"value": [
{ 
    "id": "0000682575d5d473e82ed4d8680425d152411251_9e1b90be-e83e-485b-a5ec-4a429412e734_1.1.1", 
    "configurationId": "1.1.1", 
    "deviceId": "0000682575d5d473242222425d152411251", 
    "deviceName": " ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596 ", 
    "profileId": "9e1b90be-e83e-485b-a5ec-4a429412e734", 
    "osPlatform": "WindowsServer2019", 
    "osVersion": "10.0.17763.2330", 
    "rbacGroupId": 86, 
    "rbacGroupName": "UnassignedGroup", 
    "isApplicable": true, 
    "isCompliant": false, 
    "dataCollectionTimeOffset": "2021-12-22T00:08:02.478Z", 
    "recommendedValue": [ 
                    "Greater than or equal '24'" 
                ], 
                "currentValue": [ 
                    "24" 
                ], 
                "source": [ 
                    "password_hist_len"
                ], 
}
```

## <a name="2-export-security-baselines-assessment-via-files"></a>2. تصدير تقييم خطوط أساس الأمان (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 2.1

إرجاع كافة تقييمات خطوط الأمان الأساسية لجميع الأجهزة، على أساس كل جهاز. يقوم بإرجاع جدول مع إدخال منفصل لكل مجموعة فريدة من DeviceId و ProfileId و ConfigurationId.

### <a name="22-limitations"></a>2.2 القيود

- قيود المعدل لواجهة برمجة التطبيقات هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/BaselineComplianceAssessmentExport
```

### <a name="24-parameters"></a>2.4 معلمات

- sasValidHours: عدد الساعات التي ستكون فيها عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى). 

### <a name="25-properties-via-files"></a>2.5 خصائص (عبر الملفات)

> [!NOTE]
> الملفات مضغوطة & بتنسيق Json متعدد الأسطر.
>
>عناوين URL للتنزيل صالحة لمدة 3 ساعات فقط؛ وإلا يمكنك استخدام المعلمة.
>
>لتكبير سرعات التنزيل، تأكد من تنزيل البيانات من نفس منطقة Azure حيث توجد بياناتك.
>
>كل سجل هو تقريبا 1 كيلوبايت من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار المعلمة pageSize التي تناسبك.
>
>قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها. استخدم الأعمدة الموثقة فقط.

الخاصية (المعرف)|نوع البيانات|الوصف
:---|:---|:---
|تصدير الملفات|array[string]|قائمة بتنزيل عناوين URL للملفات التي تحمل اللقطة الحالية للمؤسسة.
|تاريخ الإنشاء|سلسلة|الوقت الذي تم فيه إنشاء التصدير.

## <a name="26-example"></a>مثال 2.6

### <a name="261-request-example"></a>مثال على طلب 2.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentExport
```

### <a name="262-response-example"></a>مثال على الاستجابة 2.6.2

```json
{ 
    "@odata.context": "https://api.securitycenter. contoso.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse", 
    "exportFiles": 
    [ 
    "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId= OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00000-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv=ABCD", 
   "https://tvmexportexternalstgeus.blob.core.windows.net/temp-1ebd3d09-d06a-4aad-ab80-ebc536cec61c/2021-12-22/0500/BaselineAssessmentExport/json/OrgId=<Org Id>/_RbacGroupId=<Rbac Group Id>/part-00001-c09dfd00-2278-4735-b23a-71733751fcbc.c000.json.gz?sv= ABCD", 
    ], 
    "generatedTime": "2021-01-11T11:01:00Z" 
}
```

## <a name="see-also"></a>راجع أيضًا

- [الحصول على ملفات تعريف تقييم أساسيات الأمان](get-security-baselines-assessment-profiles.md)
- [الحصول على تكوينات تقييم أساسيات الأمان](get-security-baselines-assessment-configurations.md)
