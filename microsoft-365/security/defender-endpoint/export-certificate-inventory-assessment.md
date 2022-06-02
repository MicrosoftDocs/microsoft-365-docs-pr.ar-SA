---
title: أساليب تقييم الشهادة وخصائصها لكل جهاز
description: يوفر معلومات حول واجهات برمجة التطبيقات للشهادات التي تسحب بيانات "إدارة المخاطر والثغرات الأمنية". هناك استدعاءات واجهة برمجة تطبيقات مختلفة للحصول على أنواع مختلفة من البيانات. بشكل عام، يحتوي كل استدعاء لواجهة برمجة التطبيقات على البيانات المطلوبة للأجهزة في مؤسستك.
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
ms.openlocfilehash: c5f89d92e754648dcaffb134de70516c7274625d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838925"
---
# <a name="export-certificate-inventory-per-device"></a>تصدير مخزون الشهادات لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
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

## <a name="1-export-certificate-assessment-json-response"></a>1. تصدير تقييم الشهادة (استجابة JSON)

### <a name="11-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 1.1

إرجاع كافة تقييمات الشهادات لجميع الأجهزة، على أساس كل جهاز. يقوم بإرجاع جدول مع إدخال منفصل لكل مجموعة فريدة من DeviceId وSmpprint و Path.

#### <a name="12-limitations"></a>1.2 القيود

- الحد الأقصى لحجم الصفحة هو 200,000.
- قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="13-parameters"></a>1.3 معلمات

- حجم الصفحة (الافتراضي = 50,000): عدد النتائج في الاستجابة.
- $top: عدد النتائج التي سيتم إرجاعها (لا ترجع @odata.nextLink وهكذا لا تسحب كافة البيانات).

### <a name="14-http-request"></a>طلب HTTP 1.4

```http
GET /api/machines/certificateAssessmentByMachine
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
|معرف الجهاز|سلسلة|معرف فريد للجهاز في الخدمة.
|اسم الجهاز|سلسلة|اسم المجال المؤهل بالكامل (FQDN) للجهاز.
|بصمه الابهام|منطقي|معرف فريد للشهادة.
|مسار|سلسلة|موقع الشهادة.
|SignatureAlgorithm|سلسلة|خوارزمية التجزئة وخوارزمية التشفير المستخدمة.
|حجم المفتاح|سلسلة|حجم المفتاح المستخدم في خوارزمية التوقيع.
|تاريخ انتهاء الصلاحية|سلسلة|التاريخ والوقت اللذين لم تعد الشهادة صالحة بعدهما.
|تاريخ الإصدار|سلسلة|أقرب تاريخ ووقت تصبح فيه الشهادة صالحة.
|نوع الموضوع|سلسلة|يشير إلى ما إذا كان صاحب الشهادة هو CA أو كيان نهائي.
|الرقم التسلسلي|سلسلة|معرف فريد للشهادة داخل أنظمة المرجع المصدق.
|تم الإصدار إلى|الكائن|الكيان الذي تنتمي إليه الشهادة؛ يمكن أن يكون جهازا أو فردا أو مؤسسة.
|تاريخ الإصدار|الكائن|الكيان الذي تحقق من المعلومات ووقع الشهادة.
|KeyUsage|سلسلة|الاستخدامات المشفرة الصالحة للمفتاح العام للشهادة.
|ExtendedKeyUsage|سلسلة|استخدامات أخرى صالحة للشهادة.
|RbacGroupId|سلسلة|معرف مجموعة التحكم في الوصول استنادا إلى الدور (RBAC).
|RbacGroupName|سلسلة|مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعات RBAC، فستكون القيمة "غير معينة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".

## <a name="16-example"></a>مثال 1.6

### <a name="161-request-example"></a>مثال على طلب 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/BaselineComplianceAssessmentByMachine
```

### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json

  {
     "@odata.context":"https://127.0.0.1/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetCertificateAssessment)",
      "value":[
        {
        "deviceId":"49126b9e4a5473b5229c73799e9e55c48668101b",
        "deviceName":"testmachine5",
        "thumbprint":"A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "path":"LocalMachine\\TestSignRoot\\A4B37F4F6DE956922273D5CB8E7E0AAFB7033B90",
        "signatureAlgorithm":"sha384ECDSA",
        "keyLength":0,"notAfter":"0001-01-01T00:00:00Z",
        "notBefore":"0001-01-01T00:00:00Z",
        "subjectType":"CA",
        "serialNumber":"6086A185EAFA2B9943B4671603F40323",
        "subjectObject":null,
        "issuerObject":null,
        "keyUsageArray":null,
        "extendedKeyUsageArray":null,
        "isSelfSigned":false,
        "rbacGroupId":4226,
        "rbacGroupName":"testO6343398Gq31"}],
        "@odata.nextLink":"https://127.0.0.1/api/machines/CertificateAssessmentByMachine?pagesize=1&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMi0wMy0yMS8wNTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjF9"
  }
```

## <a name="2-export-certificate-assessment-via-files"></a>2. تصدير تقييم الشهادة (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 2.1

إرجاع كافة تقييمات الشهادات لجميع الأجهزة، على أساس كل جهاز. يقوم بإرجاع جدول مع إدخال منفصل لكل مجموعة فريدة من DeviceId وSmpprint و Path.

#### <a name="22-limitations"></a>2.2 القيود

- قيود المعدل لواجهة برمجة التطبيقات هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة. 

### <a name="23-parameters"></a>2.3 معلمات

- sasValidHours: عدد الساعات التي ستكون فيها عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى).

### <a name="24-http-request"></a>طلب HTTP 2.4

```http
GET /api/machines/certificateAssessmentExport
```

### <a name="25-properties-json-response"></a>2.5 خصائص (استجابة JSON)

> [!NOTE]
> الملفات مضغوطة & بتنسيق Json متعدد الأسطر.
>
> عناوين URL للتنزيل صالحة لمدة 3 ساعات فقط؛ وإلا، يمكنك استخدام المعلمة.
>
> لتكبير سرعات التنزيل، تأكد من تنزيل البيانات من نفس منطقة Azure حيث توجد بياناتك.
>
> كل سجل هو تقريبا 1 كيلوبايت من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار المعلمة pageSize التي تناسبك.
>
> قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها. استخدم الأعمدة الموثقة فقط.

الخاصية (المعرف)|نوع البيانات|الوصف
:---|:---|:---
|تصدير الملفات|سلسلة[صفيف]|قائمة بتنزيل عناوين URL للملفات التي تحمل اللقطة الحالية للمؤسسة.
|تاريخ الإنشاء|Datetime|وقت إنشاء التصدير.


## <a name="26-example"></a>مثال 2.6

### <a name="261-request-example"></a>مثال على طلب 2.6.1

```http
GET https://api.securitycenter.contoso.com/api/machines/certificateAssessmentExport
```

### <a name="262-response-example"></a>مثال على الاستجابة 2.6.2

```json
    {
        "@odata.context":"https://127.0.0.1/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
        "exportFiles":["https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4226/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=IMmwTOYmGvU0ei5AHLNAxnFCmZkE2jvBHzRmuAu9xaA%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=4414/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=2r0y74WZsATa0DjQTwfBxNqL5vN2Wl0AZKHMNrxuJ30%3D","https://tvmexportexternalstgeus.blob.core.windows.net/temp-5c080622-f613-42bb-9fee-e17ccdff90d3/2022-03-20/1318/CertificateAssessmentExport/json/OrgId=47d41a0c-188d-46d3-bbea-a93dbc0bfcaa/_RbacGroupId=75/part-00000-65a62a9d-7a01-4d78-bbdb-6d3e07b34cc9.c000.json.gz?sv=2020-02-10&st=2022-03-20T13%3A35%3A37Z&se=2022-03-20T16%3A35%3A37Z&sr=b&sp=r&sig=uVdY4%2BBpMdPMwaD3G0RJTZkS4R9J8oN8I3tu%2FOcG35c%3D"],
        "generatedTime":"2022-03-20T13:18:00Z"
   }
```
