---
title: تصدير تقييم تكوين آمن لكل جهاز
description: إرجاع إدخال لكل مجموعة فريدة من DeviceId، ConfigurationId.
keywords: api، apis، تقييم التصدير، تقييم كل جهاز، تقرير تقييم الضعف، تقييم ضعف الجهاز، تقرير ضعف الجهاز، تقييم التكوين الآمن، تقرير التكوين الآمن، تقييم الثغرات في البرامج، تقرير ثغرة البرامج، تقرير الضعف حسب الجهاز،
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: ab33db7fb7acf1969973a7af8f80ea97ef3d378f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/05/2021
ms.locfileid: "63571684"
---
# <a name="export-secure-configuration-assessment-per-device"></a>تصدير تقييم تكوين آمن لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
ترجع كافة التكوينات و الحالة الخاصة بها، على أساس كل جهاز.

هناك مكالمات API مختلفة للحصول على أنواع مختلفة من البيانات. نظرا لأن كمية البيانات يمكن أن تكون كبيرة، هناك طريقتان يمكن استردادها:

- [تصدير تقييم تكوين **آمن OData**](#1-export-secure-configuration-assessment-odata): تسحب API كل البيانات في مؤسستك كاستجابات Json، باتباع بروتوكول OData. هذا الأسلوب هو الأفضل بالنسبة _إلى المؤسسات الصغيرة التي تستخدم أقل من 100 كيلووات من الأجهزة_. تم ربط الاستجابة، \@بحيث يمكنك استخدام الحقل odata.nextLink من الاستجابة للحصول على النتائج التالية.

- [تصدير تقييم تكوين آمن **عبر الملفات**](#2-export-secure-configuration-assessment-via-files): يمكن حل API هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. لذلك، يوصى به بالنسبة إلى المؤسسات الكبيرة، مع أكثر من 100 كيلووات من الأجهزة. تسحب API هذه كل البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل كل البيانات من Azure Storage. تمكنك API هذه من تنزيل كل بياناتك من Azure Storage كما يلي:

  - اتصل ب API للحصول على قائمة عناوين URL للتنزيل مع كل بيانات مؤسستك.

  - قم بتنزيل كل الملفات باستخدام عناوين URL للتنزيل و معالجة البيانات كما تريد.

البيانات التي يتم تجميعها (باستخدام _OData_ أو _عبر_ الملفات) هي اللقطة الحالية من الحالة الحالية، ولا تحتوي على بيانات تاريخية. لجمع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!Note]
>
> ما لم يشار إلى خلاف ذلك، تكون كل أساليب تقييم التصدير **** المدرجة تصديرا كاملا حسب **_الجهاز (يشار_** إليه أيضا **_بكل جهاز_**).

## <a name="1-export-secure-configuration-assessment-odata"></a>1. تصدير تقييم تكوين آمن (OData)

### <a name="11-api-method-description"></a>وصف أسلوب 1.1 API

تحتوي استجابة API هذه على تقييم التكوين الآمن على الأجهزة التي يتم عرضها، وترجع إدخالا لكل مجموعة فريدة من DeviceId، ConfigurationId.

#### <a name="111-limitations"></a>1.1.1 القيود

- الحد الأقصى لحجم الصفحة هو 200000.

- قيود السعر ل API هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="12-permissions"></a>1.2 الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة](apis-intro.md) تطبيقات نقطة النهاية للحصول على التفاصيل.

نوع الإذن | الإذن | اسم عرض الأذونات
---|---|---
Application | Vulnerability.Read.All | \'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة) | ثغرة أمنية.قراءة | \'قراءة معلومات ضعف إدارة المخاطر والضعف\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentByMachine
```

### <a name="14-parameters"></a>1.4 المعلمات

- pageSize \(default = 50,000\) – عدد النتائج في الاستجابة

- \$أعلى – لا \(\@يؤدي عدد النتائج التي يتم إرجاعها إلى إرجاع odata.nextLink وبالتالي لا يسحب كل البيانات\)

### <a name="15-properties"></a>1.5 خصائص

>[!Note]
>
>- يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية.  عند تشغيل API هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.
>
>- قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.
>

الخاصية (الم ID) | نوع البيانات | الوصف | مثال لقيمة تم إرجاعها
:---|:---|:---|:---
ConfigurationCategory | سلسلة | الفئة أو المجموعة التي ينتمي إليها التكوين: التطبيق، نظام التشغيل، الشبكة، الحسابات، عناصر التحكم في الأمان | عناصر التحكم في الأمان
ConfigurationId | سلسلة | معرف فريد لتكوين معين | scid-10000
ConfigurationImpact | سلسلة | التأثير تصنيف التكوين على درجة التكوين الإجمالية (1-10) | 9
ConfigurationName | سلسلة | اسم العرض الخاص بالتهيئة | الأجهزة المجهزة ل Microsoft Defender لنقطة النهاية
ConfigurationSubcategory | سلسلة | الفئة الفرعية أو التجميع الفرعي الذي ينتمي إليه التكوين. في العديد من الحالات، يصف ذلك قدرات أو ميزات معينة. | الأجهزة المجهزة
DeviceId | سلسلة | معرف فريد للجهاز في الخدمة. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | سلسلة | اسم المجال المؤهل بالكامل (FQDN) للجهاز. | johnlaptop.europe.contoso.com
IsApplicable | bool | تشير إلى ما إذا كان التكوين أو النهج قابلا للتطبيق | true
IsCompliant | bool | تشير إلى ما إذا كان التكوين أو النهج مكونا بشكل صحيح | خطأ
IsExpectedUserImpact | bool | تشير إلى ما إذا كان سيكون هناك تأثير على المستخدم إذا كان سيتم تطبيق التكوين | true
OSPlatform | سلسلة | النظام الأساسي لنظام التشغيل الذي يتم تشغيله على الجهاز. يشير ذلك إلى أنظمة تشغيل معينة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 10 Windows 7. راجع أنظمة التشغيل و الأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل. | Windows10
RbacGroupName | سلسلة | مجموعة التحكم بالوصول المستند إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، ستكون القيمة "غير معين". إذا لم تحتوي المؤسسة على أي من مجموعات RBAC، ستكون القيمة "بلا". | الخوادم
RecommendationReference | سلسلة | مرجع لمرجع التوصية المرتبط بهذا البرنامج. | sca-_-scid-20000
Timestamp | سلسلة | آخر مرة تم فيها رؤية التكوين على الجهاز | 2020-11-03 10:13:34.8476880

### <a name="16-examples"></a>1.6 أمثلة

#### <a name="161-request-example"></a>1.6.1 مثال على طلب

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
            "osPlatform": "Windows10",
            "osVersion": "NT kernel 6.x",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "0002a1be533813b9a8c6de739785365bce7910",
            "rbacGroupName": "hhh",
            "deviceName": null,
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
            "osVersion": "10.0",
            "timestamp": "2021-01-11 09:47:58.854",
            "configurationId": "scid-10000",
            "configurationCategory": "Network",
            "configurationSubcategory": "",
            "configurationImpact": 5,
            "isCompliant": true,
            "isApplicable": true,
            "isExpectedUserImpact": false,
            "configurationName": "Disable insecure administration protocol – Telnet",
            "recommendationReference": "sca-_-scid-10000"
        },
        {
            "deviceId": "00044f912345bdaf756492dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663d45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
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
            "osPlatform": "Windows10",
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

## <a name="2-export-secure-configuration-assessment-via-files"></a>2. تصدير تقييم تكوين آمن (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب API 2.1

تحتوي استجابة API هذه على تقييم التكوين الآمن على الأجهزة التي يتم عرضها، وترجع إدخالا لكل مجموعة فريدة من DeviceId، ConfigurationId.

#### <a name="212-limitations"></a>2.1.2 القيود

قيود السعر ل API هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="22-permissions"></a>2.2 الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن | الإذن | اسم عرض الأذونات
---|---|---
Application | Vulnerability.Read.All | \'قراءة معلومات الثغرة "إدارة المخاطر والثغرات الأمنية"\'
مفوض (حساب العمل أو المدرسة) | ثغرة أمنية.قراءة | \'قراءة معلومات الثغرة "إدارة المخاطر والثغرات الأمنية"\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SecureConfigurationsAssessmentExport
```

### <a name="parameters"></a>المعلمات

- sasValidHours – عدد الساعات التي ستكون عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى).

### <a name="25-properties"></a>2.5 خصائص

>[!Note]
>
>- يتم ضغط الملفات بتنسيق gzip & بتنسيق Json متعدد الخطوط.
>
>- عناوين URL للتنزيل صالحة فقط لمدة 3 ساعات؛ وإلا يمكنك استخدام المعلمة.
>
>- للحصول على أقصى سرعة تنزيل لبياناتك، يمكنك التأكد من أنك تقوم بالتحميل من منطقة Azure نفسها التي تتواجد فيها بياناتك.
>
الخاصية (الم ID) | نوع البيانات | الوصف | مثال لقيمة تم إرجاعها
:---|:---|:---|:---
تصدير الملفات | arraystring\[\] | قائمة عناوين URL للتنزيل للملفات التي تحمل اللقطة الحالية الخاصة بالمنظمة | [  Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2” ]
GeneratedTime | سلسلة | الوقت الذي تم فيه إنشاء التصدير. | 2021-05-20T08:00:00Z ]

### <a name="26-examples"></a>2.6 أمثلة

#### <a name="261-request-example"></a>2.6.1 مثال على طلب

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

- [تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessmnt-1methods-properties.md)

- [تصدير تقييم مخزون البرامج لكل جهاز](get-assessmnt-software-inventory.md)

- [تقييم نقاط الضعف في البرامج لكل جهاز](get-assessmnt-software-vulnerabilities.md)

أخرى ذات صلة

- [المخاطر المستندة إلى المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)

- [نقاط الضعف في مؤسستك](tvm-weaknesses.md)
