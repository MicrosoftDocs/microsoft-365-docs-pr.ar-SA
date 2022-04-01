---
title: سرد كل أنشطة الإصلاح
description: إرجاع معلومات حول كل أنشطة الإصلاح.
keywords: apis, remediation, remediation api, get, remediation tasks, all remediation,
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3e387c8fb6ca9f1aca756ef2ab0b4c0684033370
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63579572"
---
# <a name="list-all-remediation-activities"></a>سرد كل أنشطة الإصلاح

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إرجاع معلومات حول كل أنشطة الإصلاح.

[تعرف على المزيد حول أنشطة الإصلاح](tvm-remediation.md).

**URL:** GET: /api/remediationTasks
<br>يدعم [استعلامات OData V4](https://www.odata.org/documentation/).
<br>عوامل التشغيل المعتمدة في OData:
<br>```$filter``` على:  ```createdon``` والخصائص ```status``` .
<br>```$top``` مع الحد الأقصى لقيمة 10000.
<br>```$skip```.
<br>راجع الأمثلة في [استعلامات OData باستخدام Microsoft Defender ل Endpoint](exposed-apis-odata-samples.md).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|RemediationTasks.Read.All|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة)|RemediationTask.Read|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'

## <a name="properties"></a>الخصائص

الخاصية (الم ID)|نوع البيانات|الوصف|مثال لقيمة تم إرجاعها
:---|:---|:---|:---
الفئة|سلسلة|فئة نشاط الإصلاح (تكوين البرامج/الأمان)|البرامج
completerEmail|سلسلة|إذا تم إكمال نشاط المعالجة يدويا من قبل شخص ما، فإن هذا العمود يحتوي على بريده الإلكتروني|Null
completerId|سلسلة|إذا تم إكمال نشاط المعالجة يدويا من قبل شخص ما، فإن هذا العمود يحتوي على "معروض الكائن" الخاص به|Null
completionMethod|سلسلة|يمكن إكمال نشاط المعالجة "تلقائيا" (إذا تم تصحيح جميع الأجهزة) أو "يدويا" من قبل شخص يقوم بتحديد "وضع علامة كمكتملة"|تلقائي
createdOn|DateTime|الوقت الذي تم فيه إنشاء نشاط الإصلاح هذا|2021-01-12T18:54:11.5499478Z
الوصف|سلسلة|وصف لنشاط الإصلاح هذا|قم بتحديث Microsoft Silverlight إلى إصدار أحدث للحد من الثغرات المعروفة التي تؤثر على أجهزتك.
dueOn|DateTime|تاريخ الاستحقاق الذي حدده المبدع لنشاط الإصلاح هذا|2021-01-13T00:00:00Z
fixedDevices|.|عدد الأجهزة التي تم إصلاحها|2
الم ID|سلسلة|الم ID الخاص بنشاط الإصلاح هذا|097d9735-5479-4899-b1b7-77398899df92
nameId|سلسلة|اسم المنتج ذي الصلة|Microsoft Silverlight
الأولوية|سلسلة|أولوية مجموعة المبدعين لنشاط الإصلاح هذا (High\Medium\Low)|عال
productId|سلسلة|"معرّف المنتج ذي الصلة"|microsoft-_-silverlight
productivityImpactRemediationType|سلسلة|يمكن طلب بعض تغييرات التكوين فقط للأجهزة التي لا تؤثر على المستخدمين. تشير هذه القيمة إلى التحديد بين "جميع الأجهزة المعرضة" أو "الأجهزة التي لا تؤثر على المستخدم فقط".|AllExposedAssets
rbacGroupNames|سلسلة|أسماء مجموعة الأجهزة ذات الصلة|[ "Windows الخوادم"، "Windows 11"، "Windows 10" ]
المستحسنProgram|سلسلة|البرنامج المستحسن للترقية إلى|Null
recommendedVendor|سلسلة|المورد المستحسن للترقية إلى|Null
recommendedVersion|سلسلة|الإصدار المستحسن للتحديث/الترقية إلى|Null
relatedComponent|سلسلة|المكون ذو الصلة لنشاط الإصلاح هذا (مماثل للمكون ذي الصلة لتوصية الأمان)|Microsoft Silverlight
requesterEmail|سلسلة|عنوان البريد الإلكتروني "منشئ"|globaladmin@UserName.contoso.com
requesterId|سلسلة|"معر ة كائن منشئ"|r647211f-2e16-43f2-a480-16ar3a2a796r
requesterNotes|سلسلة|الملاحظات (نص مجاني) التي أضافها المبدع لنشاط الإصلاح هذا|Null
Scid|سلسلة|SCID لتوصية الأمان ذات الصلة|Null
الحالة|سلسلة|حالة نشاط المعالجة (نشط/مكتمل)|نشط
statusLastModifiedOn|DateTime|تاريخ تحديث حقل الحالة|2021-01-12T18:54:11.5499487Z
targetDevices|طويل|عدد الأجهزة التي يتم عرضها التي ينطبق هذا الإصلاح على|43
العنوان|سلسلة|عنوان نشاط الإصلاح هذا|تحديث Microsoft Silverlight
النوع|سلسلة|نوع المعالجة|تحديث
موردمزيد|سلسلة|اسم المورد ذي الصلة|Microsoft

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/
```

### <a name="response-example"></a>مثال على الاستجابة

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks",
    "value": [
        {
            "id": "03942ef5-aewb-4w6e-b555-d6a97013844w",
            "title": "Update Microsoft Silverlight",
            "createdOn": "2021-02-10T13:20:36.4718166Z",
            "requesterId": "65548a1d-ef00-4a7a-8d19-1b967b5c36f4",
            "requesterEmail": "user1@contoso.com",
            "status": "Active",
            "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
            "description": "Update Silverlight to a later version  to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.",
            "relatedComponent": "Microsoft Silverlight",
            "targetDevices": 18511,
            "rbacGroupNames": [
                "UnassignedGroup",
                "hhh"
            ],
            "fixedDevices": 2866,
            "requesterNotes": "test",
            "dueOn": "2021-02-11T00:00:00Z",
            "category": "Software",
            "productivityImpactRemediationType": null,
            "priority": "Medium",
            "completionMethod": null,
            "completerId": null,
            "completerEmail": null,
            "scid": null,
            "type": "Update",
            "productId": "microsoft-_-silverlight",
            "vendorId": "microsoft",
            "nameId": "silverlight",
            "recommendedVersion": null,
            "recommendedVendor": null,
            "recommendedProgram": null
        }
    ]
}
```

## <a name="see-also"></a>راجع أيضًا

- [أساليب المعالجة وخصائصها](get-remediation-methods-properties.md)
- [الحصول على نشاط إصلاحي واحد بواسطة الم ID](get-remediation-one-activity.md)
- [سرد الأجهزة التي تم عرضها لنشاط إصلاحي واحد](get-remediation-exposed-devices-activities.md)
- [المخاطر المستندة إلى المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [نقاط الضعف في مؤسستك](tvm-weaknesses.md)
