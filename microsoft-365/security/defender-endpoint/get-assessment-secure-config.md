---
title: تصدير تقييم التكوين الآمن لكل جهاز
description: إرجاع إدخال لكل مجموعة فريدة من DeviceId، ConfigurationId.
keywords: api, apis, export assessment, per device assessment, vulnerability assessment report, device vulnerability assessment, device vulnerability report, secure configuration assessment, secure configuration report, software vulnerabilities assessment, software vulnerability report, vulnerability report by machine,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6d706dc8552490b7705cc23fca4751f810211d47
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839274"
---
# <a name="export-secure-configuration-assessment-per-device"></a>تصدير تقييم التكوين الآمن لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

إرجاع كافة التكوينات وحالتها، على أساس كل جهاز.

هناك استدعاءات واجهة برمجة تطبيقات مختلفة للحصول على أنواع مختلفة من البيانات. نظرا لأن كمية البيانات يمكن أن تكون كبيرة، هناك طريقتان يمكن استردادها:

- [تصدير **استجابة JSON** لتقييم التكوين الآمن](#1-export-secure-configuration-assessment-json-response): تسحب واجهة برمجة التطبيقات جميع البيانات في مؤسستك كاستجابات Json. هذا الأسلوب هو الأفضل _للمؤسسات الصغيرة التي تحتوي على أقل من 100 كيلوبايت_. الاستجابة مرقمة الصفحات، بحيث يمكنك استخدام \@حقل odata.nextLink من الاستجابة لإحضار النتائج التالية.

- [تصدير تقييم التكوين الآمن **عبر الملفات**](#2-export-secure-configuration-assessment-via-files): يتيح حل واجهة برمجة التطبيقات هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. لذلك، يوصى به للمؤسسات الكبيرة، التي تحتوي على أكثر من 100 كيلوبايت. تسحب واجهة برمجة التطبيقات هذه جميع البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل جميع البيانات من Azure Storage. تمكنك واجهة برمجة التطبيقات هذه من تنزيل جميع بياناتك من Azure Storage كما يلي:

  - اتصل بواجهة برمجة التطبيقات للحصول على قائمة بتنزيل عناوين URL مع جميع بيانات مؤسستك.

  - قم بتنزيل جميع الملفات باستخدام عناوين URL التنزيل ومعالجة البيانات كما تريد.

البيانات التي يتم جمعها (باستخدام _استجابة JSON_ أو _عبر الملفات_) هي اللقطة الحالية للحالة الحالية، ولا تحتوي على بيانات تاريخية. من أجل جمع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!NOTE]
> ما لم تتم الإشارة إلى خلاف ذلك، فإن جميع أساليب تقييم التصدير المدرجة هي **_التصدير الكامل_** **_والجهاز_** (يشار إليها أيضا **_حسب الجهاز_**).

## <a name="1-export-secure-configuration-assessment-json-response"></a>1. تصدير تقييم التكوين الآمن (استجابة JSON)

### <a name="11-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 1.1

تحتوي استجابة واجهة برمجة التطبيقات هذه على "تقييم التكوين الآمن" على أجهزتك المكشوفة، وترجع إدخالا لكل مجموعة فريدة من DeviceId، ConfigurationId.

#### <a name="111-limitations"></a>1.1.1 القيود

- الحد الأقصى لحجم الصفحة هو 200,000.

- قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="12-permissions"></a>1.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md) للحصول على التفاصيل.

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Vulnerability.Read.All|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'
مفوض (حساب العمل أو المؤسسة التعليمية)|Vulnerability.Read|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'

### <a name="13-url"></a>URL 1.3

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 معلمات

- \(حجم الصفحة الافتراضي = 50000\): عدد النتائج في الاستجابة.
- \$الأعلى: لا يرجع \@عدد النتائج التي سيتم إرجاعها \(odata.nextLink وبالتالي لا يسحب كافة البيانات\).

### <a name="15-properties"></a>1.5 خصائص

> [!NOTE]
>
> - يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية. عند تشغيل واجهة برمجة التطبيقات هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.
> - قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
---|---|---|---
ConfigurationCategory|سلسله|الفئة أو التجميع الذي ينتمي إليه التكوين: التطبيق ونظام التشغيل والشبكة والحسابات وعناصر التحكم في الأمان|عناصر التحكم في الأمان
ConfigurationId|سلسله|معرف فريد لتكوين معين|scid-10000
ConfigurationImpact|سلسله|التأثير المصنف للتكوين على درجة التكوين الإجمالية (1-10)|9
اسم التكوين|سلسله|اسم العرض للتكوين|إلحاق الأجهزة Microsoft Defender لنقطة النهاية
ConfigurationSubcategory|سلسله|الفئة الفرعية أو التجميع الفرعي الذي ينتمي إليه التكوين. في كثير من الحالات، يصف هذا قدرات أو ميزات معينة.|إلحاق الأجهزة
معرف الجهاز|سلسله|معرف فريد للجهاز في الخدمة.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
اسم الجهاز|سلسله|اسم المجال المؤهل بالكامل (FQDN) للجهاز.|johnlaptop.europe.contoso.com
IsApplicable|Bool|الإشارة إلى ما إذا كان التكوين أو النهج قابلا للتطبيق|صحيح
IsCompliant|Bool|الإشارة إلى ما إذا كان التكوين أو النهج قد تم تكوينه بشكل صحيح|كاذبه
IsExpectedUserImpact|Bool|الإشارة إلى ما إذا كان سيكون هناك تأثير للمستخدم إذا كان سيتم تطبيق التكوين|صحيح
OSPlatform|سلسله|نظام أساسي لنظام التشغيل الذي يعمل على الجهاز. يشير هذا إلى أنظمة تشغيل محددة، بما في ذلك الاختلافات داخل نفس العائلة، مثل Windows 10 Windows 11. راجع أنظمة التشغيل والأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل.|Windows10 و Windows 11
RbacGroupName|سلسله|مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، فسيتم "إلغاء تعيين القيمة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".|الخوادم
التوصية بالاستدلال|سلسله|مرجع إلى معرف التوصية المتعلق بهذا البرنامج.|sca-_scid-20000
الطابع الزمني|سلسله|آخر مرة تم فيها رؤية التكوين على الجهاز|2020-11-03 10:13:34.8476880
|

### <a name="16-examples"></a>1.6 أمثلة

#### <a name="161-request-example"></a>مثال على طلب 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pageSize=5
```

#### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json
{
    "@odata.context": "api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetConfiguration)",
    "value": [
        {
            "deviceId": "00013ee62c6b12345b10214e1801b217b50ab455c293d",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_5d96860d69c73fdd06fc8d1679e1eb73eceb8330",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-20000",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Onboard Devices",
            "configurationImpact": 9,
            "isCompliant": false,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Onboard devices to Microsoft Defender for Endpoint",
            "recommendationReference": "sca-_-scid-20000"
        },
        {
            "deviceId": "0002a1de123456a8c06de736785395d4ce7610",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol - Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-39",
            "configurationCategory": "OS",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Enable 'Domain member: Digitally sign secure channel data (when possible)'",
            "recommendationReference": "sca-_-scid-39"
        },
        {
            "deviceId": "00044f912345daf759462bde6bd733d6a9c56ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45612eeb224d2de2f5ea3142726e63f16a.DomainPII_21eed80d086e76dbfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-6093",
            "configurationCategory": "Security controls",
            "configurationSubcategory": "Antivirus",
            "configurationImpact": 5,
            "isCompliant": false,
            "isApplicable": false,
            "isExpectedUserImpact": false,
            "configurationName": "Enable Microsoft Defender Antivirus real-time behavior monitoring for Linux",
            "recommendationReference": "sca-_-scid-6093"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. تصدير تقييم التكوين الآمن (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 2.1

تحتوي استجابة واجهة برمجة التطبيقات هذه على "تقييم التكوين الآمن" على أجهزتك المكشوفة، وترجع إدخالا لكل مجموعة فريدة من DeviceId، ConfigurationId.

#### <a name="212-limitations"></a>2.1.2 القيود

قيود المعدل لواجهة برمجة التطبيقات هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="22-permissions"></a>2.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Vulnerability.Read.All|\'قراءة معلومات الثغرات الأمنية "إدارة المخاطر والثغرات الأمنية"\'
مفوض (حساب العمل أو المؤسسة التعليمية)|Vulnerability.Read|\'قراءة معلومات الثغرات الأمنية "إدارة المخاطر والثغرات الأمنية"\'

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>معلمات

- sasValidHours: عدد الساعات التي ستكون فيها عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى).

### <a name="25-properties"></a>2.5 خصائص

> [!NOTE]
>
> - الملفات مضغوطة & بتنسيق Json متعدد الأسطر.
> - عناوين URL للتنزيل صالحة لمدة 3 ساعات فقط؛ وإلا يمكنك استخدام المعلمة.
> - للحصول على أقصى سرعة تنزيل لبياناتك، يمكنك التأكد من التنزيل من نفس منطقة Azure التي توجد فيها بياناتك.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
---|---|---|---
تصدير الملفات|سلسلة الصفيف\[\]|قائمة بتنزيل عناوين URL للملفات التي تحمل اللقطة الحالية للمؤسسة|["Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
تاريخ الإنشاء|سلسله|الوقت الذي تم فيه إنشاء التصدير.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 أمثلة

#### <a name="261-request-example"></a>مثال على طلب 2.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SecureConfigurationsAssessmentExport
```

#### <a name="262-response-example"></a>مثال على الاستجابة 2.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#contoso.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/ScaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>راجع أيضًا

- [تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessment-methods-properties.md)
- [تصدير تقييم مخزون البرامج لكل جهاز](get-assessment-software-inventory.md)
- [تصدير تقييم الثغرات الأمنية للبرامج لكل جهاز](get-assessment-software-vulnerabilities.md)

أخرى ذات صلة

- [& إدارة الثغرات الأمنية المخاطر المستندة إلى المخاطر](next-gen-threat-and-vuln-mgt.md)
- [الثغرات الأمنية في مؤسستك](tvm-weaknesses.md)
