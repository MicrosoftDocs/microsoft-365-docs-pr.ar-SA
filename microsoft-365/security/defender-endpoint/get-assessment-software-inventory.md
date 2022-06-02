---
title: تصدير تقييم مخزون البرامج لكل جهاز
description: إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion.
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
ms.openlocfilehash: 296b977452802d8e1ed8949cf6a8871cac171f3a
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839983"
---
# <a name="export-software-inventory-assessment-per-device"></a>تصدير تقييم مخزون البرامج لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


تحصل استدعاءات واجهة برمجة التطبيقات المختلفة على أنواع مختلفة من البيانات. نظرا لأن كمية البيانات يمكن أن تكون كبيرة، هناك طريقتان يمكن استردادها:

- [تصدير **استجابة JSON** لتقييم مخزون البرامج](#1-export-software-inventory-assessment-json-response) تسحب واجهة برمجة التطبيقات جميع البيانات في مؤسستك كاستجابات Json. هذا الأسلوب هو الأفضل _للمؤسسات الصغيرة التي تحتوي على أقل من 100 كيلوبايت_. الاستجابة مرقمة الصفحات، بحيث يمكنك استخدام \@حقل odata.nextLink من الاستجابة لإحضار النتائج التالية.

- [تصدير تقييم مخزون البرامج **عبر الملفات**](#2-export-software-inventory-assessment-via-files)  يتيح حل واجهة برمجة التطبيقات هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. لذلك، يوصى به للمؤسسات الكبيرة، مع أكثر من 100 كيلوبايت من الأجهزة. تسحب واجهة برمجة التطبيقات هذه جميع البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل جميع البيانات من Azure Storage. تمكنك واجهة برمجة التطبيقات هذه من تنزيل جميع بياناتك من Azure Storage كما يلي:
  - اتصل بواجهة برمجة التطبيقات للحصول على قائمة بتنزيل عناوين URL مع جميع بيانات مؤسستك.
  - قم بتنزيل جميع الملفات باستخدام عناوين URL التنزيل ومعالجة البيانات كما تريد.

البيانات التي يتم جمعها (باستخدام _استجابة Json_ أو _عبر الملفات_) هي اللقطة الحالية للحالة الحالية. لا يحتوي على بيانات تاريخية. لجمع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!NOTE]
> ما لم تتم الإشارة إلى خلاف ذلك، فإن جميع أساليب تقييم التصدير المدرجة هي **_التصدير الكامل_** **_والجهاز_** (يشار إليها أيضا **_حسب الجهاز_**).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. تصدير تقييم مخزون البرامج (استجابة JSON)

### <a name="11-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 1.1

تحتوي استجابة واجهة برمجة التطبيقات هذه على جميع بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion.

#### <a name="limitations"></a>القيود

- الحد الأقصى لحجم الصفحة هو 200,000.
- قيود المعدل لواجهة برمجة التطبيقات هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="12-permissions"></a>1.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Software.Read.All|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'
مفوض (حساب العمل أو المؤسسة التعليمية)|Software.Read|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'

### <a name="13-url"></a>URL 1.3

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 معلمات

- حجم الصفحة (الافتراضي = 50,000): عدد النتائج في الاستجابة.
- $top: عدد النتائج التي سيتم إرجاعها (لا ترجع @odata.nextLink وبالتالي لا تسحب كافة البيانات)

### <a name="15-properties"></a>1.5 خصائص

> [!NOTE]
>
> - كل سجل هو حوالي 0.5 كيلوبايت من البيانات. يجب أن تأخذ هذا في الاعتبار عند اختيار معلمة حجم الصفحة الصحيحة لك.
> - يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية. عند تشغيل واجهة برمجة التطبيقات هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.
> - قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
:---|:---|:---|:---
معرف الجهاز|سلسله|معرف فريد للجهاز في الخدمة.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
اسم الجهاز|سلسله|اسم المجال المؤهل بالكامل (FQDN) للجهاز.|johnlaptop.europe.contoso.com
DiskPaths|Array[string]|دليل القرص على تثبيت المنتج على الجهاز.|[ "ج:\\ Program Files (x86)\\Microsoft\\Silverlight\\Application\\silverlight.exe" ]
EndOfSupportDate|سلسله|التاريخ الذي سينتهي فيه دعم هذا البرنامج أو سينتهي.|2020-12-30
EndOfSupportStatus|سلسله|حالة نهاية الدعم. يمكن أن تحتوي على هذه القيم المحتملة: None، وإصدار EOS، وإصدار EOS القادم، وبرامج EOS، وبرامج EOS القادمة.|EOS القادم
معرف|سلسله|معرف فريد للسجل.|123ABG55_573AG&mnp!
NumberOfWeaknesses|الباحث|عدد نقاط الضعف في هذا البرنامج على هذا الجهاز|3
OSPlatform|سلسله|نظام أساسي لنظام التشغيل الذي يعمل على الجهاز. هذه هي أنظمة تشغيل محددة مع اختلافات داخل نفس العائلة، مثل Windows 10 Windows 11. راجع أنظمة التشغيل والأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل.|Windows10 و Windows 11
RbacGroupName|سلسله|مجموعة التحكم في الوصول استنادا إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، فسيتم "إلغاء تعيين القيمة". إذا لم تتضمن المؤسسة أي مجموعات RBAC، فستكون القيمة "بلا".|الخوادم
RegistryPaths|Array[string]|دليل التسجيل على تثبيت المنتج في الجهاز.|[ "HKEY_LOCAL_MACHINE\\ SOFTWARE\\WOW6432Node\\Microsoft\\ Windows\\ CurrentVersion\\Uninstall\\Microsoft Silverlight" ]
طابع SoftwareFirstSeenTimestamp|سلسله|في المرة الأولى التي ظهر فيها هذا البرنامج على الجهاز.|2019-04-07 02:06:47
اسم البرنامج|سلسله|اسم منتج البرنامج.|سلفرليغت
برنامجVendor|سلسله|اسم مورد البرامج.|Microsoft
SoftwareVersion|سلسله|رقم إصدار منتج البرنامج.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 أمثلة

#### <a name="161-request-example"></a>مثال على طلب 1.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pageSize=5  &sinceTime=2021-05-19T18%3A35%3A49.924Z
```

#### <a name="162-response-example"></a>مثال على الاستجابة 1.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Collection(contoso.windowsDefenderATP.api.AssetSoftware)",
    "value": [
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "windows_10" "Windows_11",
            "softwareVersion": "10.0.17763.1637",
            "numberOfWeaknesses": 58,
            "diskPaths": [],
            "registryPaths": [],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "Upcoming EOS Version",
            "endOfSupportDate": "2021-05-11T00:00:00+00:00"
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": ".net_framework",
            "softwareVersion": "4.0.0.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4.0\\Client\\Install"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eed80d086e79bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.7.214.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f68765ddaf71234bde6bd733d6a9c59ad4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2be2f5ea3142726e63f16a.DomainPII_21eeb80d086e79dbfa178aedfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "configuration_manager",
            "softwareVersion": "5.0.8634.1000",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\{B7D3A842-E826-4542-B39B-1D883264B279}"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        },
        {
            "deviceId": "00044f38765bbaf712342dbe6db733b6a9c59ab4",
            "rbacGroupName": "hhh",
            "deviceName": "ComputerPII_18993b45912eeb224b2de2f5ea3142726e63f16a.DomainPII_21eeb80d086e79bdfa178eadfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "Windows10" "Windows11",
            "softwareVendor": "microsoft",
            "softwareName": "system_center_2012_endpoint_protection",
            "softwareVersion": "4.10.209.0",
            "numberOfWeaknesses": 0,
            "diskPaths": [],
            "registryPaths": [
                "HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Microsoft Security Client"
            ],
            "softwareFirstSeenTimestamp": "2020-12-30 11:07:15",
            "endOfSupportStatus": "None",
            "endOfSupportDate": null
        }
    ],
    "@odata.nextLink": "https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryByMachine?pagesize=5&$skiptoken=eyJFeHBvcnREZWZpbml0aW9uIjp7IlRpbWVQYXRoIjoiMjAyMS0wMS0yNS8wMjAwLyJ9LCJFeHBvcnRGaWxlSW5kZXgiOjAsIkxpbmVTdG9wcGVkQXQiOjV9"
}
```

## <a name="2-export-software-inventory-assessment-via-files"></a>2. تصدير تقييم مخزون البرامج (عبر الملفات)

### <a name="21-api-method-description"></a>وصف أسلوب واجهة برمجة التطبيقات 2.1

تحتوي استجابة واجهة برمجة التطبيقات هذه على جميع بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion.

#### <a name="211-limitations"></a>2.1.1 القيود

قيود المعدل لواجهة برمجة التطبيقات هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="22-permissions"></a>2.2 أذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
---|---|---
Application|Software.Read.All|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'
مفوض (حساب العمل أو المؤسسة التعليمية)|Software.Read|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'

### <a name="23-url"></a>URL 2.3

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>معلمات

- sasValidHours: عدد الساعات التي ستكون فيها عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى)

### <a name="25-properties"></a>2.5 خصائص

> [!NOTE]
>
> - الملفات مضغوطة & بتنسيق JSON متعدد الأسطر.
> - عناوين URL للتنزيل صالحة لمدة 3 ساعات فقط. وإلا يمكنك استخدام المعلمة.
> - للحصول على أقصى سرعة تنزيل لبياناتك، يمكنك التأكد من أنك تقوم بتنزيل البيانات من نفس منطقة Azure الموجودة بها.

<br>

****

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
:---|:---|:---|:---
تصدير الملفات|سلسلة الصفيف\[\]|قائمة بتنزيل عناوين URL للملفات التي تحمل اللقطة الحالية للمؤسسة|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
تاريخ الإنشاء|سلسله|الوقت الذي تم فيه إنشاء التصدير.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 أمثلة

#### <a name="261-request-example"></a>مثال على طلب 2.6.1

```http
GET https://api.securitycenter.microsoft.com/api/machines/SoftwareInventoryExport
```

#### <a name="262-response-example"></a>مثال على الاستجابة 2.6.2

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.ExportFilesResponse",
    "exportFiles": [
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00393-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c000.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=...",
        "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export/2021-01-11/1101/SoftwareInventory/json/OrgId=12345678-195f-4223-9c7a-99fb420fd000/part-00394-e423630d-4c69-4490-8769-a4f5468c4f25.c001.json.gz?sv=2019-12-12&st=2021-01-11T11%3A55%3A51Z&se=2021-01-11T14%3A55%3A51Z&sr=b&sp=r&sig=..."
    ],
    "generatedTime": "2021-01-11T11:01:00Z"
}
```

## <a name="see-also"></a>راجع أيضًا

- [تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessment-methods-properties.md)
- [تصدير تقييم التكوين الآمن لكل جهاز](get-assessment-secure-config.md)
- [تصدير تقييم الثغرات الأمنية للبرامج لكل جهاز](get-assessment-software-vulnerabilities.md)

أخرى ذات صلة

- [& إدارة الثغرات الأمنية المخاطر المستندة إلى المخاطر](next-gen-threat-and-vuln-mgt.md)
- [الثغرات الأمنية في مؤسستك](tvm-weaknesses.md)
