---
title: تصدير تقييم الثغرات الأمنية للبرامج لكل جهاز
description: تكون استجابة واجهة برمجة التطبيقات لكل جهاز وتحتوي على برامج ضعيفة مثبتة على أجهزتك المكشوفة وأي ثغرات أمنية معروفة في منتجات البرامج هذه. يتضمن هذا الجدول أيضا معلومات نظام التشغيل ومعرف CVE ومعلومات خطورة الثغرات الأمنية.
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
ms.openlocfilehash: 86d2b0b09748a83c9b73430c4c6e371ca2e37f31
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838954"
---
# <a name="export-software-vulnerabilities-assessment-per-device"></a>تصدير تقييم الثغرات الأمنية للبرامج لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

إرجاع جميع الثغرات الأمنية المعروفة في البرامج وتفاصيلها لجميع الأجهزة، على أساس كل جهاز.

تحصل استدعاءات واجهة برمجة التطبيقات المختلفة على أنواع مختلفة من البيانات. نظرا لأن كمية البيانات يمكن أن تكون كبيرة، هناك طريقتان يمكن استردادها:

1. [**تصدير استجابة JSON** لتقييم الثغرات الأمنية للبرامج](#1-export-software-vulnerabilities-assessment-json-response)  تسحب واجهة برمجة التطبيقات جميع البيانات في مؤسستك كاستجابات Json. هذا الأسلوب هو الأفضل _للمؤسسات الصغيرة التي تحتوي على أقل من 100 كيلوبايت_. الاستجابة مرقمة الصفحات، بحيث يمكنك استخدام \@حقل odata.nextLink من الاستجابة لإحضار النتائج التالية.

2. [تصدير تقييم الثغرات الأمنية للبرامج **عبر الملفات**](#2-export-software-vulnerabilities-assessment-via-files) يتيح حل واجهة برمجة التطبيقات هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. يوصى باستخدام الملفات عبر المؤسسات الكبيرة، مع أكثر من 100 كيلوبايت من الأجهزة. تسحب واجهة برمجة التطبيقات هذه جميع البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل جميع البيانات من Azure Storage. تمكنك واجهة برمجة التطبيقات هذه من تنزيل جميع بياناتك من Azure Storage كما يلي:
   - اتصل بواجهة برمجة التطبيقات للحصول على قائمة بتنزيل عناوين URL مع جميع بيانات مؤسستك.
   - قم بتنزيل جميع الملفات باستخدام عناوين URL التنزيل ومعالجة البيانات كما تريد.

3. [**استجابة JSON** لتقييم الثغرات الأمنية في برامج دلتا](#3-delta-export-software-vulnerabilities-assessment-json-response)  إرجاع جدول مع إدخال لكل مجموعة فريدة من: DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion و CveId و EventTimestamp.
تسحب واجهة برمجة التطبيقات البيانات في مؤسستك كاستجابات Json. الاستجابة مرقمة الصفحات، بحيث يمكنك استخدام حقل @odata.nextLink من الاستجابة لإحضار النتائج التالية.

   يتم استخدام "تقييم الثغرات الأمنية للبرامج بالكامل (استجابة JSON)" للحصول على لقطة كاملة لتقييم الثغرات الأمنية للبرامج لمؤسستك حسب الجهاز. ومع ذلك، يتم استخدام استدعاء واجهة برمجة تطبيقات تصدير دلتا لإحضار التغييرات التي حدثت بين تاريخ محدد والتاريخ الحالي فقط (استدعاء واجهة برمجة تطبيقات "delta"). بدلا من الحصول على تصدير كامل مع كمية كبيرة من البيانات في كل مرة، ستحصل فقط على معلومات محددة حول الثغرات الأمنية الجديدة والثابتة والمحدثة. يمكن أيضا استخدام استدعاء واجهة برمجة تطبيقات استجابة JSON لتصدير دلتا لحساب مؤشرات الأداء الرئيسية المختلفة مثل "كم عدد الثغرات الأمنية التي تم إصلاحها؟" أو "كم عدد الثغرات الأمنية الجديدة التي تمت إضافتها إلى مؤسستي؟"

   نظرا لأن استدعاء واجهة برمجة تطبيقات استجابة JSON لتصدير Delta للثغرات الأمنية للبرامج يرجع البيانات لنطاق تاريخ مستهدف فقط، فإنه لا يعتبر _تصديرا كاملا_.

البيانات التي يتم جمعها (باستخدام _استجابة Json_ أو _عبر الملفات_) هي اللقطة الحالية للحالة الحالية. لا يحتوي على بيانات تاريخية. لجمع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!NOTE]
> ما لم تتم الإشارة إلى خلاف ذلك، فإن جميع أساليب تقييم التصدير المدرجة هي **_التصدير الكامل_** **_والجهاز_** (يشار إليها أيضا **_حسب الجهاز_**).

## <a name="1-export-software-vulnerabilities-assessment-json-response"></a>1. تصدير تقييم الثغرات الأمنية للبرامج (استجابة JSON)

### <a name="11-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 1.1

تحتوي استجابة واجهة برمجة التطبيقات هذه على جميع بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion و CVEID.

#### <a name="111-limitations"></a>1.1.1 القيود

- الحد الأقصى لحجم الصفحة هو 200,000.
- قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="12-permissions"></a>1.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Vulnerability.Read.All|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'
مفوض (حساب العمل أو المؤسسة التعليمية)|Vulnerability.Read|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'

### <a name="13-url"></a>URL 1.3

```http
GET /api/machines/SoftwareVulnerabilitiesByMachine
```

### <a name="14-parameters"></a>1.4 معلمات

- حجم الصفحة (الافتراضي = 50,000): عدد النتائج في الاستجابة.
- $top: عدد النتائج التي سيتم إرجاعها (لا ترجع @odata.nextLink وهكذا لا تسحب كافة البيانات).

### <a name="15-properties"></a>1.5 خصائص

> [!NOTE]
>
> - كل سجل هو تقريبا 1 كيلوبايت من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار معلمة حجم الصفحة الصحيحة لك.
> - قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.
> - يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية. عند تشغيل واجهة برمجة التطبيقات هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
:---|:---|:---|:---
CveId|سلسلة|المعرف الفريد المعين إلى ثغرة الأمان الأمنية ضمن نظام الثغرات الأمنية والتعرضات الشائعة (CVE).|CVE-2020-15992
CvssScore|سلسلة|درجة CVSS ل CVE.|6.2
معرف الجهاز|سلسلة|معرف فريد للجهاز في الخدمة.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
اسم الجهاز|سلسلة|اسم المجال المؤهل بالكامل (FQDN) للجهاز.|johnlaptop.europe.contoso.com
DiskPaths|سلسلة الصفيف\[\]|دليل القرص على تثبيت المنتج على الجهاز.|[ "C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe" ]
مستوى الاستغلال|سلسلة|مستوى قابلية الاستغلال لهذه الثغرات الأمنية (NoExploit، ExploitIsPublic، ExploitIsVerified، ExploitIsInKit)|ExploitIsInKit
الطابع الزمني الأول ل FirstSeen|سلسلة|في المرة الأولى التي تم فيها رؤية CVE لهذا المنتج على الجهاز.|2020-11-03 10:13:34.8476880
معرف|سلسلة|معرف فريد للسجل.|123ABG55_573AG&mnp!
الطابع LastSeenTimestamp|سلسلة|في المرة الأخيرة التي تم فيها رؤية CVE على الجهاز.|2020-11-03 10:13:34.8476880
OSPlatform|سلسلة|نظام أساسي لنظام التشغيل الذي يعمل على الجهاز. تشير هذه الخاصية إلى أنظمة تشغيل محددة ذات تباينات داخل نفس العائلة، مثل Windows 10 Windows 11. راجع أنظمة التشغيل والأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل.|Windows10 و Windows 11
RbacGroupName|سلسلة|مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، فستكون القيمة "غير معينة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".|الخوادم
التوصية بالاستدلال|سلسلة|مرجع إلى معرف التوصية المتعلق بهذا البرنامج.|_va-microsoft-silverlight_
RecommendedSecurityUpdate (اختياري)|سلسلة|اسم أو وصف تحديث الأمان الذي يوفره مورد البرنامج لمعالجة مشكلة الثغرة الأمنية.|تحديثات الأمان لشهر أبريل 2020
RecommendedSecurityUpdateId (اختياري)|سلسلة|معرف تحديثات الأمان أو المعرف القابل للتطبيق للإرشادات المطابقة أو مقالات قاعدة معارف (KB)|4550961
RegistryPaths|سلسلة الصفيف\[\]|دليل التسجيل على تثبيت المنتج في الجهاز.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\MicrosoftSilverlight" ]
اسم البرنامج|سلسلة|اسم منتج البرنامج.|كروم
برنامجVendor|سلسلة|اسم مورد البرامج.|جوجل
SoftwareVersion|سلسلة|رقم إصدار منتج البرنامج.|81.0.4044.138
VulnerabilitySeverityLevel|سلسلة|مستوى الخطورة المعين للثغرة الأمنية الأمنية استنادا إلى درجة CVSS والعوامل الديناميكية المتأثرة بمشهد التهديد.|المتوسطه
|

### <a name="16-examples"></a>1.6 أمثلة

#### <a name="161-request-example"></a>مثال على طلب 1.6.1

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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
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
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.17763.1637",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
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
            "recommendationReference": "va-_-microsoft-_-windows_10" "va-_-microsoft-_-windows_11"
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilitiesByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-vulnerabilities-assessment-via-files"></a>2. تصدير تقييم الثغرات الأمنية في البرامج (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 2.1

تحتوي استجابة واجهة برمجة التطبيقات هذه على جميع بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion و CVEID.

#### <a name="212-limitations"></a>2.1.2 القيود

قيود المعدل لواجهة برمجة التطبيقات هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="22-permissions"></a>2.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل](apis-intro.md).

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Vulnerability.Read.All|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'
مفوض (حساب العمل أو المؤسسة التعليمية)|Vulnerability.Read|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/SoftwareVulnerabilitiesExport
```

### <a name="24-parameters"></a>2.4 معلمات

- sasValidHours: عدد الساعات التي ستكون فيها عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى).

### <a name="25-properties"></a>2.5 خصائص

> [!NOTE]
>
> - الملفات مضغوطة & بتنسيق Json متعدد الأسطر.
> - عناوين URL للتنزيل صالحة لمدة 3 ساعات فقط؛ وإلا يمكنك استخدام المعلمة.
> - للحصول على أقصى سرعة تنزيل لبياناتك، يمكنك التأكد من أنك تقوم بتنزيل البيانات من نفس منطقة Azure الموجودة بها.
>
> - كل سجل هو تقريبا 1 كيلوبايت من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار معلمة حجم الصفحة الصحيحة لك.
> - قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
:---|:---|:---|:---
تصدير الملفات|سلسلة الصفيف\[\]|قائمة بتنزيل عناوين URL للملفات التي تحمل اللقطة الحالية للمؤسسة.|["https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
تاريخ الإنشاء|سلسلة|الوقت الذي تم فيه إنشاء التصدير.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 أمثلة

#### <a name="261-request-example"></a>مثال على طلب 2.6.1

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

## <a name="3-delta-export-software-vulnerabilities-assessment-json-response"></a>3. تقييم الثغرات الأمنية في برامج التصدير دلتا (استجابة JSON)

### <a name="31-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 3.1

إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion و CveId. تسحب واجهة برمجة التطبيقات البيانات في مؤسستك كاستجابات Json. الاستجابة مرقمة الصفحات، بحيث يمكنك استخدام حقل @odata.nextLink من الاستجابة لإحضار النتائج التالية. على عكس تقييم الثغرات الأمنية الكاملة للبرامج (استجابة JSON) (الذي يستخدم للحصول على لقطة كاملة لتقييم الثغرات الأمنية للبرامج لمؤسستك حسب الجهاز) يتم استخدام استدعاء واجهة برمجة تطبيقات استجابة JSON للتصدير دلتا لإحضار التغييرات التي حدثت فقط بين تاريخ محدد والتاريخ الحالي (استدعاء واجهة برمجة تطبيقات "delta"). بدلا من الحصول على تصدير كامل مع كمية كبيرة من البيانات في كل مرة، ستحصل فقط على معلومات محددة حول الثغرات الأمنية الجديدة والثابتة والمحدثة. يمكن أيضا استخدام استدعاء واجهة برمجة تطبيقات استجابة JSON لتصدير دلتا لحساب مؤشرات الأداء الرئيسية المختلفة مثل "كم عدد الثغرات الأمنية التي تم إصلاحها؟" أو "كم عدد الثغرات الأمنية الجديدة التي تمت إضافتها إلى مؤسستي؟"

> [!NOTE]
> يوصى بشدة باستخدام تقييم الثغرات الأمنية لبرنامج التصدير الكامل عن طريق استدعاء واجهة برمجة التطبيقات للجهاز مرة واحدة على الأقل في الأسبوع، وتتغير الثغرات الأمنية الإضافية لبرامج التصدير حسب واجهة برمجة تطبيقات الجهاز (delta) التي تستدعي جميع الأيام الأخرى من الأسبوع. على عكس واجهات برمجة تطبيقات استجابة JSON للتقييمات الأخرى، فإن "تصدير دلتا" ليس تصديرا كاملا. يتضمن تصدير دلتا فقط التغييرات التي حدثت بين تاريخ محدد والتاريخ الحالي (استدعاء واجهة برمجة تطبيقات "delta").

#### <a name="311-limitations"></a>3.1.1 القيود

- الحد الأقصى لحجم الصفحة هو 200,000.
- المعلمة sinceTime لها حد أقصى 14 يوما.
- قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="32-permissions"></a>3.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Vulnerability.Read.All|'قراءة معلومات الثغرات الأمنية لإدارة المخاطر والثغرات الأمنية'
مفوض (حساب العمل أو المؤسسة التعليمية)|Vulnerability.Read|'قراءة معلومات الثغرات الأمنية لإدارة المخاطر والثغرات الأمنية'

### <a name="33-url"></a>URL 3.3

```http
GET /api/machines/SoftwareVulnerabilityChangesByMachine
```

### <a name="34-parameters"></a>3.4 معلمات

- منذ الوقت (مطلوب): البيانات بين وقت محدد واليوم.
- حجم الصفحة (الافتراضي = 50,000): عدد النتائج في الاستجابة.
- $top: عدد النتائج التي سيتم إرجاعها (لا ترجع @odata.nextLink وهكذا لا تسحب جميع البيانات).

### <a name="35-properties"></a>3.5 خصائص

يحتوي كل سجل تم إرجاعه على جميع البيانات من تقييم الثغرات الأمنية لبرنامج التصدير الكامل بواسطة واجهة برمجة تطبيقات الجهاز، بالإضافة إلى حقلين إضافيين:  _**EventTimestamp**_ _**والحالة**_.

> [!NOTE]
>
> - قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، لذا يرجى استخدام الأعمدة الموثقة فقط.
> - يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية. عند تشغيل واجهة برمجة التطبيقات هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال للقيمة التي تم إرجاعها
:---|:---|:---|:---
CveId |سلسلة|المعرف الفريد المعين إلى ثغرة الأمان الأمنية ضمن نظام الثغرات الأمنية والتعرضات الشائعة (CVE).|CVE-2020-15992  
CvssScore|سلسلة|درجة CVSS ل CVE.|6.2  
معرف الجهاز|سلسلة|معرف فريد للجهاز في الخدمة.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1  
اسم الجهاز|سلسلة|اسم المجال المؤهل بالكامل (FQDN) للجهاز.|johnlaptop.europe.contoso.com  
DiskPaths|Array[string]|دليل القرص على تثبيت المنتج على الجهاز.|["C:\Program Files (x86)\Microsoft\Silverlight\Application\silverlight.exe"]  
الطابع الزمني للحدث|سلسلة|الوقت الذي تم فيه العثور على حدث delta هذا.|2021-01-11T11:06:08.291Z
مستوى الاستغلال|سلسلة|مستوى قابلية الاستغلال لهذه الثغرات الأمنية (NoExploit، ExploitIsPublic، ExploitIsVerified، ExploitIsInKit)|ExploitIsInKit  
الطابع الزمني الأول ل FirstSeen|سلسلة|في المرة الأولى التي تم فيها رؤية CVE لهذا المنتج على الجهاز.|2020-11-03 10:13:34.8476880  
معرف|سلسلة|معرف فريد للسجل.|123ABG55_573AG&mnp!  
الطابع LastSeenTimestamp|سلسلة|في المرة الأخيرة التي تم فيها رؤية CVE على الجهاز.|2020-11-03 10:13:34.8476880  
OSPlatform|سلسلة|النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز؛ أنظمة تشغيل محددة مع اختلافات داخل العائلة نفسها، مثل Windows 10 Windows 11. راجع أنظمة التشغيل والأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل.|Windows10 و Windows 11 
RbacGroupName|سلسلة|مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، فستكون القيمة "غير معينة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".|الخوادم  
التوصية بالاستدلال|سلسله|مرجع إلى معرف التوصية المتعلق بهذا البرنامج.|va--microsoft--silverlight  
RecommendedSecurityUpdate |سلسلة|اسم أو وصف تحديث الأمان الذي يوفره مورد البرنامج لمعالجة مشكلة الثغرة الأمنية.|تحديثات الأمان لشهر أبريل 2020  
RecommendedSecurityUpdateId |سلسلة|معرف تحديثات الأمان أو المعرف القابل للتطبيق للإرشادات المطابقة أو مقالات قاعدة معارف (KB)|4550961  
RegistryPaths |Array[string]|دليل التسجيل على تثبيت المنتج في الجهاز.|[ "HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\Google Chrome" ]  
اسم البرنامج|سلسلة|اسم منتج البرنامج.|كروم  
برنامجVendor|سلسلة|اسم مورد البرامج.|جوجل  
SoftwareVersion|سلسلة|رقم إصدار منتج البرنامج.|81.0.4044.138  
حاله|سلسلة|**جديد** (لثغرة أمنية جديدة تم تقديمها على جهاز) (1) **ثابتة** (إذا لم تعد هذه الثغرة الأمنية موجودة على الجهاز، ما يعني أنه تمت معالجتها). (2) **محدث** (إذا تغيرت ثغرة أمنية على جهاز. التغييرات المحتملة هي: درجة CVSS، ومستوى قابلية الاستغلال، ومستوى الخطورة، و DiskPaths، و RegistryPaths، و RecommendedSecurityUpdate). |الثابته
VulnerabilitySeverityLevel|سلسلة|مستوى الخطورة الذي تم تعيينه إلى ثغرة الأمان الأمنية. وهو يستند إلى درجة CVSS والعوامل الديناميكية المتأثرة بمشهد التهديد.|المتوسطه
|

#### <a name="clarifications"></a>الايضاحات

- إذا تم تحديث البرنامج من الإصدار 1.0 إلى الإصدار 2.0، وتم عرض كلا الإصدارين إلى CVE-A، فستتلقى حدثين منفصلين:
   1. تم التصحيح: تم تصحيح CVE-A على الإصدار 1.0.
   1. جديد: تمت إضافة CVE-A على الإصدار 2.0.

- إذا ظهر ثغرة أمنية معينة (على سبيل المثال، CVE-A) لأول مرة في وقت محدد (على سبيل المثال، 10 يناير) على برنامج مع الإصدار 1.0، وبعد بضعة أيام تم تحديث هذا البرنامج إلى الإصدار 2.0 الذي تعرض أيضا لنفس CVE-A، فستتلقى هذين الحدثين المنفصلين:
   1. تم التصحيح: CVE-X، FirstSeenTimestamp 10 يناير، الإصدار 1,0.
   1. جديد: CVE-X، FirstSeenTimestamp 10 يناير، الإصدار 2.0.

### <a name="36-examples"></a>3.6 أمثلة

#### <a name="361-request-example"></a>مثال على طلب 3.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareVulnerabilityChangesByMachine?pageSize=5&sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="362-response-example"></a>مثال على الاستجابة 3.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(microsoft.windowsDefenderATP.api.DeltaAssetVulnerability)",
    "value": [
        {
            "id": "008198251234544f7dfa715e278d4cec0c16c171_chrome_87.0.4280.88__",
            "deviceId": "008198251234544f7dfa715e278b4cec0c19c171",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_1c8fee370690ca24b6a0d3f34d193b0424943a8b8.DomainPII_0dc1aee0fa366d175e514bd91a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "87.0.4280.88",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Google Chrome"
            ],
            "lastSeenTimestamp": "2021-01-04 00:29:42",
            "firstSeenTimestamp": "2020-11-06 03:12:44",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "00e59c61234533860738ecf488eec8abf296e41e_onedrive_20.64.329.3__",
            "deviceId": "00e56c91234533860738ecf488eec8abf296e41e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_82c13a8ad8cf3dbaf7bf34fada9fa3aebc124116.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "onedrive",
            "softwareVersion": "20.64.329.3",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_USERS\\S-1-5-21-2127521184-1604012920-1887927527-24918864\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\OneDriveSetup.exe"
            ],
            "lastSeenTimestamp": "2020-12-11 19:49:48",
            "firstSeenTimestamp": "2020-12-07 18:25:47",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-onedrive",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "01aa8c73095bb12345918663f3f94ce322107d24_firefox_83.0.0.0_CVE-2020-26971_",
            "deviceId": "01aa8c73065bb12345918693f3f94ce322107d24",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_42684eb981bea2d670027e7ad2caafd3f2b381a3.DomainPII_21eed80b086e76dbfa178eabfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "mozilla",
            "softwareName": "firefox",
            "softwareVersion": "83.0.0.0",
            "cveId": "CVE-2020-26971",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "193220",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Mozilla Firefox\\firefox.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Mozilla Firefox 83.0 (x86 en-US)"
            ],
            "lastSeenTimestamp": "2021-01-05 17:04:30",
            "firstSeenTimestamp": "2020-05-06 12:42:19",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-mozilla-_-firefox",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "026f0fcb12345fbd2decd1a339702131422d362e_project_16.0.13701.20000__",
            "deviceId": "029f0fcb13245fbd2decd1a336702131422d392e",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_a5706750acba75f15d69cd17f4a7fcd268d6422c.DomainPII_f290e982685f7e8eee168b4332e0ae5d2a069cd6.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.19042.685",
            "osArchitecture": "x64",
            "softwareVendor": "microsoft",
            "softwareName": "project",
            "softwareVersion": "16.0.13701.20000",
            "cveId": null,
            "vulnerabilitySeverityLevel": null,
            "recommendedSecurityUpdate": null,
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\ProjectProRetail - en-us"
            ],
            "lastSeenTimestamp": "2021-01-03 23:38:03",
            "firstSeenTimestamp": "2019-08-01 22:56:12",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-microsoft-_-project",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        },
        {
            "id": "038df381234510b357ac19d0113ef622e4e212b3_chrome_81.0.4044.138_CVE-2020-16011_",
            "deviceId": "038df381234510d357ac19b0113ef922e4e212b3",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_365f5c0bb7202c163937dad3d017969b2d760eb4.DomainPII_29596a43a2ef2bbfa00f6a16c0cb1d108bc63e32.DomainPII_3c5fefd2e6fda2f36257359404f6c1092aa6d4b8.net",
            "osPlatform": "Windows10" "Windows11",
            "osVersion": "10.0.18363.1256",
            "osArchitecture": "x64",
            "softwareVendor": "google",
            "softwareName": "chrome",
            "softwareVersion": "81.0.4044.138",
            "cveId": "CVE-2020-16011",
            "vulnerabilitySeverityLevel": "High",
            "recommendedSecurityUpdate": "ADV 200002",
            "recommendedSecurityUpdateId": null,
            "recommendedSecurityUpdateUrl": null,
            "diskPaths": [
                "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            ],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{C4EBFDFD-0C55-3E5F-A919-E3C54949024A}"
            ],
            "lastSeenTimestamp": "2020-12-10 22:45:41",
            "firstSeenTimestamp": "2020-07-26 02:13:43",
            "exploitabilityLevel": "NoExploit",
            "recommendationReference": "va-_-google-_-chrome",
            "status": "Fixed",
            "eventTimestamp": "2021-01-11T11:06:08.291Z"
        }
    ],
    "@odata.nextLink": "https://wpatdadi-eus-stg.cloudapp.net/api/machines/SoftwareVulnerabilitiesTimeline?sincetime=2021-01-11&pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0xMS8xMTAxLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="see-also"></a>راجع أيضًا

- [تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessment-methods-properties.md)
- [تصدير تقييم التكوين الآمن لكل جهاز](get-assessment-secure-config.md)
- [تصدير تقييم مخزون البرامج لكل جهاز](get-assessment-software-inventory.md)

أخرى ذات صلة

- [& إدارة الثغرات الأمنية المخاطر المستندة إلى المخاطر](next-gen-threat-and-vuln-mgt.md)
- [الثغرات الأمنية في مؤسستك](tvm-weaknesses.md)
