---
title: تصدير تقييم مخزون البرامج لكل جهاز
description: إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion.
keywords: api، apis، تقييم التصدير، تقييم كل جهاز، تقرير تقييم الضعف، تقييم ضعف الجهاز، تقرير ضعف الجهاز، تقييم التكوين الآمن، تقرير التكوين الآمن، تقييم الثغرات في البرامج، تقرير ثغرة البرامج، تقرير الضعف حسب الجهاز،
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
ms.openlocfilehash: 4c3464a3aec242bd098503ac5bca997943ac2a4a
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63574330"
---
# <a name="export-software-inventory-assessment-per-device"></a>تصدير تقييم مخزون البرامج لكل جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


تحصل مكالمات API المختلفة على أنواع مختلفة من البيانات. نظرا لأن كمية البيانات يمكن أن تكون كبيرة، هناك طريقتان يمكن استردادها:

- [استجابة **JSON** لتقييم مخزون البرامج](#1-export-software-inventory-assessment-json-response) تسحب API كل البيانات في مؤسستك كاستجابات Json. هذا الأسلوب هو الأفضل بالنسبة _إلى المؤسسات الصغيرة التي تستخدم أقل من 100 جهاز K_. تم ربط الاستجابة، \@بحيث يمكنك استخدام الحقل odata.nextLink من الاستجابة للحصول على النتائج التالية.

- [تصدير تقييم مخزون البرامج **عبر الملفات**](#2-export-software-inventory-assessment-via-files)  يمكن حل API هذا سحب كميات أكبر من البيانات بشكل أسرع وأكثر موثوقية. لذلك، يوصى به بالنسبة إلى المؤسسات الكبيرة، التي بها أكثر من 100 جهاز K. تسحب API هذه كل البيانات في مؤسستك كملفات تنزيل. تحتوي الاستجابة على عناوين URL لتنزيل كل البيانات من Azure Storage. تمكنك API هذه من تنزيل كل بياناتك من Azure Storage كما يلي:
  - اتصل ب API للحصول على قائمة عناوين URL للتنزيل مع كل بيانات مؤسستك.
  - قم بتنزيل كل الملفات باستخدام عناوين URL للتنزيل و معالجة البيانات كما تريد.

البيانات التي يتم تجميعها (باستخدام استجابة _Json_ أو _عبر_ الملفات) هي اللقطة الحالية من الحالة الحالية. ولا تحتوي على بيانات تاريخية. لتجميع البيانات التاريخية، يجب على العملاء حفظ البيانات في مخازن البيانات الخاصة بهم.

> [!NOTE]
> ما لم يشار إلى خلاف ذلك، تكون كل أساليب تقييم التصدير **** المدرجة تصديرا كاملا حسب **_الجهاز (يشار_** إليه أيضا **_بكل جهاز_**).

## <a name="1-export-software-inventory-assessment-json-response"></a>1. تقييم مخزون البرامج (استجابة JSON)

### <a name="11-api-method-description"></a>وصف أسلوب 1.1 API

تحتوي استجابة API هذه على كل بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion.

#### <a name="limitations"></a>القيود

- الحد الأقصى لحجم الصفحة هو 200000.
- قيود السعر ل API هذه هي 30 مكالمة في الدقيقة و1000 مكالمة في الساعة.

### <a name="12-permissions"></a>1.2 الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Software.read.All|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة)|Software.Read|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'

### <a name="13-url"></a>1.3 URL

```http
GET /api/machines/SoftwareInventoryByMachine
```

### <a name="14-parameters"></a>1.4 المعلمات

- pageSize (افتراضي = 50000): عدد النتائج في الاستجابة.
- $top: عدد النتائج التي يجب إرجاعها (لا يتم إرجاع @odata.nextLink وبالتالي لا يسحب كل البيانات)

### <a name="15-properties"></a>1.5 خصائص

> [!NOTE]
>
> - يبلغ عدد البيانات في كل سجل 0,5KB تقريبا. يجب أن تأخذ هذا في الاعتبار عند اختيار المعلمة حجم الصفحة الصحيحة لك.
> - يتم سرد الخصائص المعرفة في الجدول التالي أبجديا، حسب معرف الخاصية. عند تشغيل API هذه، لن يتم بالضرورة إرجاع الإخراج الناتج بنفس الترتيب المدرج في هذا الجدول.
> - قد يتم إرجاع بعض الأعمدة الإضافية في الاستجابة. هذه الأعمدة مؤقتة وقد تتم إزالتها، يرجى استخدام الأعمدة الموثقة فقط.

<br>

****

الخاصية (الم ID)|نوع البيانات|الوصف|مثال لقيمة تم إرجاعها
:---|:---|:---|:---
DeviceId|سلسلة|معرف فريد للجهاز في الخدمة.|9eaf3a8b5962e0e6b1af9ec756664a9b823df2d1
DeviceName|سلسلة|اسم المجال المؤهل بالكامل (FQDN) للجهاز.|johnlaptop.europe.contoso.com
DiskPaths|Array[string]|دليل القرص على أن المنتج مثبت على الجهاز.|[ "C:\\ ملفات البرامج (x86)\\MicrosoftSilverlightApplication\\\\silverlight.exe\\" ]
EndOfSupportDate|سلسلة|تاريخ انتهاء أو انتهاء دعم هذا البرنامج.|2020-12-30
EndOfSupportStatus|سلسلة|نهاية حالة الدعم. يمكن أن يحتوي على هذه القيم المحتملة: بلا، إصدار EOS، إصدار EOS القادم، برامج EOS، برامج EOS القادمة.|EOS القادم
الم ID|سلسلة|معرف فريد للسجل.|123ABG55_573AG&mnp!
NumberOfWeaknesses|int|عدد نقاط الضعف في هذا البرنامج على هذا الجهاز|3
OSPlatform|سلسلة|النظام الأساسي لنظام التشغيل الذي يتم تشغيله على الجهاز. هذه هي أنظمة تشغيل محددة ذات تباينات داخل العائلة نفسها، مثل Windows 10 Windows 11. راجع أنظمة التشغيل و الأنظمة الأساسية المدعومة من tvm للحصول على التفاصيل.|Windows10 Windows 11
RbacGroupName|سلسلة|مجموعة التحكم بالوصول المستند إلى الدور (RBAC). إذا لم يتم تعيين هذا الجهاز إلى أي مجموعة RBAC، ستكون القيمة "غير معين". إذا لم تحتوي المؤسسة على أي من مجموعات RBAC، ستكون القيمة "بلا".|الخوادم
RegistryPaths|Array[string]|دليل التسجيل على أن المنتج مثبت على الجهاز.|[ "HKEY_LOCAL_MACHINE\\ SOFTWAREWOW6432NodeMicrosoft\\\\\\ Windows\\ CurrentVersionUninstallMicrosoft\\\\ Silverlight" ]
SoftwareFirstSeenTimestamp|سلسلة|في المرة الأولى التي يتم فيها رؤية هذا البرنامج على الجهاز.|2019-04-07 02:06:47
SoftwareName|سلسلة|اسم منتج البرنامج.|Silverlight
SoftwareVendor|سلسلة|اسم مورد البرامج.|microsoft
SoftwareVersion|سلسلة|رقم إصدار منتج البرنامج.|81.0.4044.138
|

### <a name="16-examples"></a>1.6 أمثلة

#### <a name="161-request-example"></a>1.6.1 مثال على طلب

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

### <a name="21-api-method-description"></a>وصف أسلوب API 2.1

تحتوي استجابة API هذه على كل بيانات البرامج المثبتة لكل جهاز. إرجاع جدول مع إدخال لكل مجموعة فريدة من DeviceId و SoftwareVendor و SoftwareName و SoftwareVersion.

#### <a name="211-limitations"></a>2.1.1 القيود

قيود السعر ل API هذه هي 5 مكالمات في الدقيقة و20 مكالمة في الساعة.

### <a name="22-permissions"></a>2.2 الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Software.read.All|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة)|Software.Read|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'

### <a name="23-url"></a>2.3 URL

```http
GET /api/machines/SoftwareInventoryExport
```

### <a name="parameters"></a>المعلمات

- sasValidHours: عدد الساعات التي ستكون عناوين URL للتنزيل صالحة لمدة (24 ساعة كحد أقصى)

### <a name="25-properties"></a>2.5 خصائص

> [!NOTE]
>
> - يتم ضغط الملفات بتنسيق gzip & بتنسيق JSON متعدد الخطوط.
> - عناوين URL للتنزيل صالحة فقط لمدة 3 ساعات. وبخلاف ذلك، يمكنك استخدام المعلمة.
> - للحصول على أقصى سرعة تنزيل لبياناتك، يمكنك التأكد من أنك تقوم بالتحميل من منطقة Azure نفسها التي تقيم فيها بياناتك.

<br>

****

الخاصية (الم ID)|نوع البيانات|الوصف|مثال لقيمة تم إرجاعها
:---|:---|:---|:---
تصدير الملفات|arraystring\[\]|قائمة عناوين URL للتنزيل للملفات التي تحمل اللقطة الحالية الخاصة بالمنظمة|"[Https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...1", "https://tvmexportstrstgeus.blob.core.windows.net/tvm-export...2"]
GeneratedTime|سلسلة|الوقت الذي تم فيه إنشاء التصدير.|2021-05-20T08:00:00Z
|

### <a name="26-examples"></a>2.6 أمثلة

#### <a name="261-request-example"></a>2.6.1 مثال على طلب

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
- [تصدير تقييم تكوين آمن لكل جهاز](get-assessment-secure-config.md)
- [تقييم نقاط الضعف في البرامج لكل جهاز](get-assessment-software-vulnerabilities.md)

أخرى ذات صلة

- [المخاطر المستندة إلى المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [نقاط الضعف في مؤسستك](tvm-weaknesses.md)
