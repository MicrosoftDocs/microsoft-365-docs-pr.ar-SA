---
title: سرد الأجهزة التي تم عرضها لنشاط إصلاحي واحد
description: إرجاع معلومات حول الأجهزة التي يتم عرضها لمهمة المعالجة المحددة.
keywords: apis, remediation, remediation api, get, remediation tasks, remediation exposed devices
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
ms.openlocfilehash: 1a7dffa064b68b2c1ce0296b66eef663eb471496
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570253"
---
# <a name="list-exposed-devices-of-one-remediation-activity"></a>سرد الأجهزة التي تم عرضها لنشاط إصلاحي واحد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إرجاع معلومات حول الأجهزة التي يتم عرضها لمهمة المعالجة المحددة.

[تعرف على المزيد حول أنشطة الإصلاح](tvm-remediation.md).

## <a name="list-exposed-devices-associated-with-a-remediation-task-id"></a>قائمة الأجهزة التي يتم عرضها والمقترنة بمهمة إصلاح (id)

**URL:** GET: /api/remediationTasks/\{id\}/machineReferences

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية للحصول على التفاصيل.](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|RemediationTasks.Read.All|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'
مفوض (حساب العمل أو المدرسة)|RemediationTask.Read.Read|\'قراءة معلومات ضعف إدارة المخاطر والضعف\'

## <a name="properties-details"></a>تفاصيل الخصائص

الخاصية (الم id)|نوع البيانات|الوصف|مثال
:---|:---|:---|:---
الم id|سلسلة|"معرّف الجهاز"|w2957837fwda8w9ae7f023dba081059dw8d94503
computerDnsName|سلسلة|اسم الجهاز|PC-SRV2012R2Foo.UserNameVldNet.local
osPlatform|سلسلة|نظام تشغيل الجهاز|WindowsServer2012R2
rbacGroupName|سلسلة|اسم مجموعة الأجهزة المقترنة بهذا الجهاز|الخوادم

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c/machinereferences
```

### <a name="response-example"></a>مثال على الاستجابة

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "3cb5df6bb3640a2d37ad09fcd357b182d684fafc",
            "computerDnsName": "ComputerPII_2ea21b2d97c9df23c143ad9e3e454cb674232529.DomainPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3d9b1ca53e8f077199c7dcbfc9dbfa78f9bf1918",
            "computerDnsName": "ComputerPII_001d606fc149567c192747f48fae304b43c0ddba.DomainxPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3db8b27e6172951d7ea2e2d75945abec56feaf82",
            "computerDnsName": "ComputerPII_ce60cfbjj4b82a091deb5eae560332bba99a9bd7.DomainPII_0bc1aee0fa396d175e514bd61a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3bad326dcda5b53fab47408cd4a7080f3f3cc8ab",
            "computerDnsName": "ComputerPII_b6b35960dd6539d1d1cef5ada02e235e7b357408.DomainPII_21eed80b089e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        }
]
}
```

## <a name="see-also"></a>راجع أيضًا

- [أساليب المعالجة وخصائصها](get-remediation-methods-properties.md)
- [الحصول على نشاط إصلاحي واحد بواسطة الم ID](get-remediation-one-activity.md)
- [سرد كل أنشطة الإصلاح](get-remediation-all-activities.md)
- [المخاطر المستندة إلى المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [نقاط الضعف في مؤسستك](tvm-weaknesses.md)
