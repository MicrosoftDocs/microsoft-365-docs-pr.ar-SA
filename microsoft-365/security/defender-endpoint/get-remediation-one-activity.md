---
title: الحصول على نشاط معالجة واحد بواسطة المعرّف
description: إرجاع معلومات لنشاط المعالجة المحدد.
keywords: apis, remediation, remediation api, get, remediation tasks, remediation by ID,
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
ms.openlocfilehash: cac976b7c189a44ff206b64bb9fe0f1a5d8c5d4a
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65838949"
---
# <a name="get-one-remediation-activity-by-id"></a>الحصول على نشاط معالجة واحد بواسطة المعرّف

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف واجهة برمجة التطبيقات

إرجاع معلومات لنشاط المعالجة المحدد. تقديم نفس الأعمدة مثل [Get all remediation activity](get-remediation-all-activities.md)"، ولكنه يرجع نتائج _لنشاط المعالجة المحدد فقط_.

[تعرف على المزيد حول أنشطة المعالجة](tvm-remediation.md).

## <a name="list-a-specified-remediation-activity-for-id"></a>سرد نشاط معالجة محدد ل (المعرف)

**URL:** GET: /api/remediationTasks/\{id\}

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوب لاستدعاء واجهة برمجة التطبيقات هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|اذن|اسم عرض الإذن
:---|:---|:---
Application|RemediationTasks.Read.All|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'
مفوض (حساب العمل أو المؤسسة التعليمية)|RemediationTask.Read.Read|\'قراءة معلومات الثغرة الأمنية لإدارة المخاطر والثغرات الأمنية\'

## <a name="properties"></a>خصائص

الخاصية (المعرف)|نوع البيانات|الوصف|مثال لقيمة مرجعة
:---|:---|:---|:---
الفئة|سلسلة|فئة نشاط المعالجة (تكوين البرامج/الأمان)|البرامج
completerEmail|سلسلة|إذا قام شخص ما بإكمال نشاط المعالجة يدويا، فإن هذا العمود يحتوي على بريده الإلكتروني|فارغه
معرف الإكمال|سلسلة|إذا تم إكمال نشاط المعالجة يدويا من قبل شخص ما، فإن هذا العمود يحتوي على معرف الكائن|فارغه
CompletionMethod|سلسلة|يمكن إكمال نشاط المعالجة "تلقائيا" (إذا تم تصحيح جميع الأجهزة) أو "يدويا" بواسطة شخص يحدد "وضع علامة كمكتمل"|تلقائي
createdOn|Datetime|وقت إنشاء نشاط المعالجة هذا|2021-01-12T18:54:11.5499478Z
الوصف|سلسلة|وصف نشاط المعالجة هذا|قم بتحديث Microsoft Silverlight إلى إصدار لاحق للتخفيف من الثغرات الأمنية المعروفة التي تؤثر على أجهزتك.
تاريخ الاستحقاق|Datetime|تاريخ الاستحقاق الذي عينه المنشئ لنشاط المعالجة هذا|2021-01-13T00:00:00Z
fixedDevices||عدد الأجهزة التي تم تصحيحها|2
المعرّف|سلسلة|معرف نشاط المعالجة هذا|097d9735-5479-4899-b1b7-77398899df92
معرف الاسم|سلسلة|اسم المنتج ذي الصلة|Microsoft Silverlight
الاولويه|سلسلة|الأولوية التي عينها المنشئ لنشاط المعالجة هذا (عالي\متوسط\منخفض)|عاليه
Productid|سلسلة|معرف المنتج ذي الصلة|microsoft-_-silverlight
productivityImpactRemediationType|سلسلة|يمكن طلب بعض تغييرات التكوين فقط للأجهزة التي لا تؤثر على المستخدمين. تشير هذه القيمة إلى التحديد بين "كافة الأجهزة المكشوفة" أو "الأجهزة التي لا تؤثر على المستخدم فقط".|AllExposedAssets
rbacGroupNames|سلسلة|أسماء مجموعات الأجهزة ذات الصلة|[ "Windows Servers", "Windows 11", "Windows 10" ]
مخطط موصى به|سلسلة|البرنامج الموصى به للترقية إلى|فارغه
RecommendedVendor|سلسلة|المورد الموصى به للترقية إلى|فارغه
recommendedVersion|سلسلة|الإصدار الموصى به للتحديث/الترقية إليه|فارغه
الحوسبة ذات الصلة|سلسلة|المكون ذي الصلة لنشاط المعالجة هذا (على غرار المكون ذي الصلة لتوصية الأمان)|Microsoft Silverlight
requesterEmail|سلسلة|عنوان البريد الإلكتروني لمنشئ|globaladmin@UserName.contoso.com
معرف الطالب|سلسلة|معرف كائن المنشئ|r647211f-2e16-43f2-a480-16ar3a2a796r
requesterNotes|سلسلة|الملاحظات (النص المجاني) التي أضافها المنشئ لنشاط المعالجة هذا|فارغه
Scid|سلسلة|SCID لتوصية الأمان ذات الصلة|فارغه
حاله|سلسلة|حالة نشاط المعالجة (نشط/مكتمل)|النشطه
statusLastModifiedOn|Datetime|تاريخ تحديث حقل الحالة|2021-01-12T18:54:11.5499487Z
targetDevices|طويله|عدد الأجهزة المكشوفة التي تنطبق عليها هذه المعالجة|43
عنوان|سلسلة|عنوان نشاط المعالجة هذا|Microsoft Silverlight
نوع|سلسلة|نوع المعالجة|تحديث
معرف المورد|سلسلة|اسم المورد ذي الصلة|Microsoft

## <a name="example"></a>المثال

### <a name="request-example"></a>مثال على الطلب

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c
```

### <a name="response-example"></a>مثال على الاستجابة

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks/$entity",
    "id": "03942ef5-aecb-4c6e-b555-d6a97013844c",
    "title": "Update Microsoft Silverlight",
    "createdOn": "2021-02-10T13:20:36.4718166Z",
    "requesterId": "65548a1d-efo0-4a7a-8d19-1b967b5c36f4",
    "requesterEmail": "user1@contoso.com",
    "status": "Active",
    "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
    "description": "Update Silverlight to a later version to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.",
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
```

## <a name="see-also"></a>راجع أيضًا

- [أساليب وخصائص المعالجة](get-remediation-methods-properties.md)
- [سرد كل أنشطة المعالجة](get-remediation-all-activities.md)
- [سرد الأجهزة التي تم عرضها لنشاط معالجة واحد](get-remediation-exposed-devices-activities.md)
- [& إدارة الثغرات الأمنية المخاطر المستندة إلى المخاطر](next-gen-threat-and-vuln-mgt.md)
- [الثغرات الأمنية في مؤسستك](tvm-weaknesses.md)
