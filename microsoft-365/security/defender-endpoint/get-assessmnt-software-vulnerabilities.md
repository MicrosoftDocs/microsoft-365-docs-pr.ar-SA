---
title: تقييم نقاط الضعف في البرامج لكل جهاز
description: تكون استجابة API لكل جهاز وتحتوي على برامج ضعيفة مثبتة على أجهزتك المعرضة بالإضافة إلى أي نقاط ضعف معروفة في منتجات البرامج هذه. يتضمن هذا الجدول أيضا معلومات نظام التشغيل وملفات CVE ومعلومات الخطورة.
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
ms.openlocfilehash: 951f78ba361a12e404a5cce2071f931eab30c43f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/05/2021
ms.locfileid: "63575531"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>تقييم نقاط الضعف في البرامج لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]
>
>
إرجاع كل الثغرات المعروفة في البرامج وتفاصيلها لجميع الأجهزة، على أساس كل جهاز.

هناك مكالمات API مختلفة للحصول على أنواع مختلفة من البيانات. نظرا لأن كمية البيانات يمكن أن تكون كبيرة جدا، هناك طريقتان يمكن استردادها:

- [تقييم نقاط الضعف في برامج التصدير OData](#1-export-software-vulnerabilities-assessment-odata)  تسحب API كل البيانات في مؤسستك كاستجابات Json، باتباع بروتوكول OData. هذا الأسلوب هو الأفضل بالنسبة _إلى المؤسسات الصغيرة التي تستخدم أقل من 100 كيلووات من الأجهزة_. تم ربط الاستجابة، \@بحيث يمكنك استخدام الحقل odata.nextLink من الاستجابة للحصول على النتائج التالية.

- [تقييم نقاط الضعف في البرامج عبر الملفات](#2-export-software-vulnerabilities-assessment-via-files) يمكن حل API هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. لذلك، يوصى به بالنسبة إلى المؤسسات الكبيرة، مع أكثر من 100 كيلووات من الأجهزة. تسحب API هذه كل البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل كل البيانات من Azure Storage. تمكنك API هذه من تنزيل كل بياناتك من Azure Storage كما يلي:

  - اتصل ب API للحصول على قائمة عناوين URL للتنزيل مع كل بيانات مؤسستك.

  - قم بتنزيل كل الملفات باستخدام عناوين URL للتنزيل و معالجة البيانات كما تريد.

البيانات التي يتم تجميعها (باستخدام _OData_ أو _عبر_ الملفات) هي اللقطة الحالية من الحالة الحالية، ولا تحتوي على بيانات تاريخية. لجمع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!Note]
>
> ما لم يشار إلى خلاف ذلك، تكون كل أساليب تقييم التصدير **** المدرجة تصديرا كاملا حسب **_الجهاز (يشار_** إليه أيضا **_بكل جهاز_**).

## <a name="1-export-software-vulnerabilities-assessment-odata"></a>1. تقييم نقاط الضعف في البرامج (OData)

### <a name="11-api-method-description"></a>وصف أسلوب 1.1 API

تحتوي استجابة API هذه على كل بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion و CVEID.

#### <a name="limitations"></a>القيود

>- الحد الأقصى لحجم الصفحة هو 200000.
>
>- قيود السعر ل API هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="12-permissions"></a>1.2 الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن | الإذن | اسم عرض الأذونات
---|---|---
Application | Vulnerability.Read.All | \'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة) | ثغرة أمنية.قراءة | \'قراءة معلومات ضعف إدارة المخاطر والضعف\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 المعلمات

- pageSize (default = 50,000) – عدد النتائج في الاستجابة
- $top – عدد النتائج التي يجب إرجاعها (لا يتم إرجاع @odata.nextLink وبالتالي لا يسحب كل البيانات)

### <a name="15-properties"></a>1.5 خصائص
>
>[!Note]
>
>- يبلغ كل سجل حوالي 1KB من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار المعلمة حجم الصفحة الصحيحة لك.
>
>- قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.
>
>- يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية.  عند تشغيل API هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.
>

الخاصية (الم ID) | نوع البيانات | الوصف | مثال لقيمة تم إرجاعها
:---|:---|:---|:---
CveId | سلسلة | معرف فريد تم تعيينه إلى ثغرة الأمان ضمن نظام الثغرات والتعرضات الشائعة (CVE). | CVE-2020-15992
CvssScore | سلسلة | درجة CVSS ل CVE. | 6.2
DeviceId | سلسلة | معرف فريد للجهاز في الخدمة. | 9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName | سلسلة | اسم المجال المؤهل بالكامل (FQDN) للجهاز. | johnlaptop.europe.contoso.com
DiskPaths  | Arraystring\[\] | دليل القرص على أن المنتج مثبت على الجهاز. | [ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
قابلية استغلالالمستويات | سلسلة | مستوى إمكانية استغلال هذه الثغرة (NoExploit، ExploitIsPublic، ExploitIsVerified، ExploitIsInKit) | ExploitIsInKit
FirstSeenTimestamp | سلسلة | في المرة الأولى التي يتم فيها رؤية CVE لهذا المنتج على الجهاز. | 2020-11-03 10:13:34.8476880
الم ID | سلسلة | معرف فريد للسجل. | 123ABG55_573AG&mnp!
LastSeenTimestamp | سلسلة | آخر مرة تم فيها رؤية CVE على الجهاز. | 2020-11-03 10:13:34.8476880
OSPlatform | سلسلة | النظام الأساسي لنظام التشغيل الذي يتم تشغيله على الجهاز. يشير ذلك إلى أنظمة تشغيل معينة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 10 Windows 7. راجع أنظمة التشغيل و الأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل. | Windows10
RbacGroupName  | سلسلة | مجموعة التحكم بالوصول المستند إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، ستكون القيمة "غير معين". إذا لم تحتوي المؤسسة على أي من مجموعات RBAC، ستكون القيمة "بلا". | الخوادم
RecommendationReference | سلسلة | مرجع لمرجع التوصية المرتبط بهذا البرنامج. | _va-microsoft-silverlight_
RecommendedSecurityUpdate (اختياري) | سلسلة | اسم تحديث الأمان الذي وفره مورد البرنامج أو وصفه لمعالجة الثغرة الأمنية. | تحديثات الأمان ل أبريل 2020
RecommendedSecurityUpdateId (اختياري) | سلسلة | معرف تحديثات الأمان القابلة للتطبيق أو المعرف لمقالات قاعدة المعارف أو الإرشادات المطابقة (KB) | 4550961
RegistryPaths  | Arraystring\[\] | دليل التسجيل على أن المنتج مثبت على الجهاز. | [ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
SoftwareName | سلسلة | اسم منتج البرنامج. | chrome
SoftwareVendor | سلسلة | اسم مورد البرامج. | google
SoftwareVersion | سلسلة | رقم إصدار منتج البرنامج. | 81.0.4044.138
VulnerabilitySeverityLevel  | سلسلة | مستوى الخطورة المعين إلى ثغرة الأمان استنادا إلى نقاط CVSS والعوامل الديناميكية التي تتأثر بمشهد المخاطر. | متوسط

### <a name="16-examples"></a>1.6 أمثلة

#### <a name="161-request-example"></a>1.6.1 مثال على طلب

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pageSize=5
```

#### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.AssetVulnerability)",
    "value": [
        {
            "id": "00044f612345baf759462dbe6db733b6a9c59ab4_edge_10.0.17763.1637__",
            "deviceId": "00044f612345daf756462bde6bd733b9a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d089e79bdfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "edge",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-edge"
        },
        {
            "id": "00044f912345baf756462bde6db733b9a9c56ad4_.net_framework_4.0.0.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eeb80b086e79bdfa178eabfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-.net_framework"
        },
        {
            "id": "00044f912345baf756462dbe6db733d6a9c59ab4_system_center_2012_endpoint_protection_4.10.209.0__",
            "deviceId": "00044f912345daf756462bde6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eed224b2be2f5ea3142726e63f16a.DomainPII_21eed80b089e79bdfa178eadfa25e8be6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-system_center_2012_endpoint_protection"
        },
        {
            "id": "00044f612345bdaf759462dbe6bd733b6a9c59ab4_onedrive_20.245.1206.2__",
            "deviceId": "00044f91234daf759492dbe6bd733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_189663d45612eed224b2be2f5ea3142729e63f16a.DomainPII_21eed80b086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.245.1206.2",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2944539346-1310925172-2349113062-1001\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-30 13:18:33",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive"
        },
        {
            "id": "00044f912345daf759462bde6db733b6a9c56ab4_windows_10_10.0.17763.1637__",
            "deviceId": "00044f912345daf756462dbe6db733d6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18663b45912eeb224d2be2f5ea3142729e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8de6acfa346.corp.contoso.com",
            "osPlatform": "Windows10",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10",
            "softwareVersion": "10.0.17763.1637",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [],
            "lastSeenTimestamp": "2020-12-30 14:17:26",
            "firstSeenTimestamp": "2020-12-30 11:07:15",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-windows_10"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. تقييم نقاط الضعف في البرامج (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب API 2.1

تحتوي استجابة API هذه على كل بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion و CVEID.

#### <a name="212-limitations"></a>2.1.2 القيود

قيود السعر ل API هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="22-permissions"></a>2.2 الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل](apis-intro.md).

نوع الإذن | الإذن | اسم عرض الأذونات
---|---|---
Application | Vulnerability.Read.All | \'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة) | ثغرة أمنية.قراءة | \'قراءة معلومات ضعف إدارة المخاطر والضعف\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 المعلمات

- sasValidHours – عدد الساعات التي ستكون عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى)

### <a name="25-properties"></a>2.5 خصائص

>[!Note]
>
>- يتم ضغط الملفات بتنسيق gzip & بتنسيق Json متعدد الخطوط.
>
>- عناوين URL للتنزيل صالحة فقط لمدة 3 ساعات؛ وإلا يمكنك استخدام المعلمة.
>
>- للحصول على أقصى سرعة تنزيل لبياناتك، يمكنك التأكد من أنك تقوم بالتحميل من منطقة Azure نفسها التي تقيم فيها بياناتك.
>

>[!Note]
>
>- يبلغ كل سجل حوالي 1KB من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار المعلمة حجم الصفحة الصحيحة لك.
>
>- قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.
>

الخاصية (الم ID) | نوع البيانات | الوصف | مثال لقيمة تم إرجاعها
:---|:---|:---|:---
تصدير الملفات | arraystring\[\]  | قائمة بتنزيل عناوين URL للملفات التي تحمل اللقطة الحالية الخاصة بالمنظمة. | [  “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1”, “https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2”  ]
GeneratedTime | سلسلة | الوقت الذي تم فيه إنشاء التصدير. | 2021-05-20T08:00:00Z

### <a name="26-examples"></a>2.6 أمثلة

#### <a name="261-request-example"></a>2.6.1 مثال على طلب

```http
GET https://api-us.securitycenter.contoso.com/api/machines/SoftwareVulnerabilitiesExport
```

#### <a name="262-response-example"></a>مثال على الاستجابة 2.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/VaExport/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-bcc26c4f-e531-48db-9892-c93ac5d72d5c.c002.json.gz?sv=2019-12-12&st=2021-01-11T11%3A35%3A13Z&se=2021-01-11T14%3A35%3A13Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>راجع أيضًا

- [تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessmnt-1methods-properties.md)

- [تصدير تقييم تكوين آمن لكل جهاز](get-assessmnt-secure-cfg.md)

- [تصدير تقييم مخزون البرامج لكل جهاز](get-assessmnt-software-inventory.md)

أخرى ذات صلة

- [المخاطر المستندة إلى المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)

- [نقاط الضعف في مؤسستك](tvm-weaknesses.md)
