---
title: API لتنبيهات القائمة
description: تعرف على كيفية استخدام API لتنبيهات القائمة لاسترداد مجموعة من التنبيهات في Microsoft Defender لنقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيهات، الأخيرة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 7c720e7743fda39f7950a7df44bea0007988b94b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583099"
---
# <a name="list-alerts-api"></a>API لتنبيهات القائمة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>وصف API
استرداد مجموعة من التنبيهات.
<br>يدعم [استعلامات OData V4](https://www.odata.org/documentation/).
<br>عوامل التشغيل المعتمدة في OData:
<br>```$filter``` على: ```alertCreationTime```، ، ```lastUpdateTime```، ```incidentId```، ```InvestigationId```، ```id```، ```asssignedTo```، ، ```detectionSource```، ، ```lastEventTime```، ```status```، ، والخصائص ```severity``` ```category``` .
<br>```$top``` مع القيمة القصوى 10000
<br>```$skip```
<br>```$expand``` من ```evidence```
<br>الاطلاع على أمثلة على [استعلامات OData باستخدام Microsoft Defender لنقطة النهاية](exposed-apis-odata-samples.md)


## <a name="limitations"></a>القيود
1. يمكنك الحصول على التنبيهات التي تم التحديث الأخير لها وفقا لفترة الاستبقاء التي تم تكوينها.
2. الحد الأقصى لحجم الصفحة هو 10000.
3. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة. 


## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن | الإذن | اسم عرض الأذونات
:---|:---|:---
Application | Alert.read.All | "قراءة كل التنبيهات"
Application | Alert.ReadWrite.All | "قراءة كل التنبيهات وكتابتها"
مفوض (حساب العمل أو المدرسة) | Alert.Read | "قراءة التنبيهات"
مفوض (حساب العمل أو المدرسة) | Alert.ReadWrite | "قراءة التنبيهات وكتابتها"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)
> - ستتضمن الاستجابة التنبيهات المقترنة بالأجهزة التي يمكن للمستخدم الوصول إليها فقط، استنادا إلى إعدادات مجموعة الأجهزة (راجع إنشاء مجموعات الأجهزة وإدارتها للحصول على مزيد من المعلومات)[](machine-groups.md)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/alerts
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح، ترجع هذه الطريقة 200 موافق، وقائمة [بكائنات التنبيه](alerts.md) في جزء الاستجابة.

## <a name="example-1---default"></a>مثال 1 - افتراضي

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/alerts
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.

> [!NOTE]
> قد يتم اقتطاع قائمة الاستجابة المعروضة هنا للإيجاز. سيتم إرجاع كل التنبيهات من مكالمة فعلية.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Alerts",
    "value": [
        {
            "id": "da637308392288907382_-880718168",
            "incidentId": 7587,
            "investigationId": 723156,
            "assignedTo": "secop123@contoso.com",
            "severity": "Low",
            "status": "New",
            "classification": "TruePositive",
            "determination": null,
            "investigationState": "Queued",
            "detectionSource": "WindowsDefenderAv",
            "category": "SuspiciousActivity",
            "threatFamilyName": "Meterpreter",
            "title": "Suspicious 'Meterpreter' behavior was detected",
            "description": "Malware and unwanted software are undesirable applications that perform annoying, disruptive, or harmful actions on affected machines. Some of these undesirable applications can replicate and spread from one machine to another. Others are able to receive commands from remote attackers and perform activities associated with cyber attacks.\n\nA malware is considered active if it is found running on the machine or it already has persistence mechanisms in place. Active malware detections are assigned higher severity ratings.\n\nBecause this malware was active, take precautionary measures and check for residual signs of infection.",
            "alertCreationTime": "2020-07-20T10:53:48.7657932Z",
            "firstEventTime": "2020-07-20T10:52:17.6654369Z",
            "lastEventTime": "2020-07-20T10:52:18.1362905Z",
            "lastUpdateTime": "2020-07-20T10:53:50.19Z",
            "resolvedTime": null,
            "machineId": "12ee6dd8c833c8a052ea231ec1b19adaf497b625",
            "computerDnsName": "temp123.middleeast.corp.microsoft.com",
            "rbacGroupName": "MiddleEast",
            "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
            "threatName": null,
            "mitreTechniques": [
                "T1064",
                "T1085",
                "T1220"
            ],
            "relatedUser": {
                "userName": "temp123",
                "domainName": "DOMAIN"
            },
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2020-07-21T01:00:37.8404534Z"
                }
            ],
            "evidence": []
        }
        ...
    ]
}
```

## <a name="example-2---get-10-latest-alerts-with-related-evidence"></a>مثال 2 - الحصول على أحدث 10 تنبيهات مع أدلة ذات صلة

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/alerts?$top=10&$expand=evidence
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.

> [!NOTE]
> قد يتم اقتطاع قائمة الاستجابة المعروضة هنا للإيجاز. سيتم إرجاع كل التنبيهات من مكالمة فعلية.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Alerts",
    "value": [
        {
            "id": "da637472900382838869_1364969609",
            "incidentId": 1126093,
            "investigationId": null,
            "assignedTo": null,
            "severity": "Low",
            "status": "New",
            "classification": null,
            "determination": null,
            "investigationState": "Queued",
            "detectionSource": "WindowsDefenderAtp",
            "detectorId": "17e10bbc-3a68-474a-8aad-faef14d43952",
            "category": "Execution",
            "threatFamilyName": null,
            "title": "Low-reputation arbitrary code executed by signed executable",
            "description": "Binaries signed by Microsoft can be used to run low-reputation arbitrary code. This technique hides the execution of malicious code within a trusted process. As a result, the trusted process might exhibit suspicious behaviors, such as opening a listening port or connecting to a command-and-control (C&C) server.",
            "alertCreationTime": "2021-01-26T20:33:57.7220239Z",
            "firstEventTime": "2021-01-26T20:31:32.9562661Z",
            "lastEventTime": "2021-01-26T20:31:33.0577322Z",
            "lastUpdateTime": "2021-01-26T20:33:59.2Z",
            "resolvedTime": null,
            "machineId": "111e6dd8c833c8a052ea231ec1b19adaf497b625",
            "computerDnsName": "temp123.middleeast.corp.microsoft.com",
            "rbacGroupName": "A",
            "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
            "threatName": null,
            "mitreTechniques": [
                "T1064",
                "T1085",
                "T1220"
            ],
            "relatedUser": {
                "userName": "temp123",
                "domainName": "DOMAIN"
            },
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2021-01-26T01:00:37.8404534Z"
                }
            ],
            "evidence": [
                {
                    "entityType": "User",
                    "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
                    "sha1": null,
                    "sha256": null,
                    "fileName": null,
                    "filePath": null,
                    "processId": null,
                    "processCommandLine": null,
                    "processCreationTime": null,
                    "parentProcessId": null,
                    "parentProcessCreationTime": null,
                    "parentProcessFileName": null,
                    "parentProcessFilePath": null,
                    "ipAddress": null,
                    "url": null,
                    "registryKey": null,
                    "registryHive": null,
                    "registryValueType": null,
                    "registryValue": null,
                    "accountName": "name",
                    "domainName": "DOMAIN",
                    "userSid": "S-1-5-21-11111607-1111760036-109187956-75141",
                    "aadUserId": "11118379-2a59-1111-ac3c-a51eb4a3c627",
                    "userPrincipalName": "temp123@microsoft.com",
                    "detectionStatus": null
                },
                {
                    "entityType": "Process",
                    "evidenceCreationTime": "2021-01-26T20:33:58.6133333Z",
                    "sha1": "ff836cfb1af40252bd2a2ea843032e99a5b262ed",
                    "sha256": "a4752c71d81afd3d5865d24ddb11a6b0c615062fcc448d24050c2172d2cbccd6",
                    "fileName": "rundll32.exe",
                    "filePath": "C:\\Windows\\SysWOW64",
                    "processId": 3276,
                    "processCommandLine": "rundll32.exe  c:\\temp\\suspicious.dll,RepeatAfterMe",
                    "processCreationTime": "2021-01-26T20:31:32.9581596Z",
                    "parentProcessId": 8420,
                    "parentProcessCreationTime": "2021-01-26T20:31:32.9004163Z",
                    "parentProcessFileName": "rundll32.exe",
                    "parentProcessFilePath": "C:\\Windows\\System32",
                    "ipAddress": null,
                    "url": null,
                    "registryKey": null,
                    "registryHive": null,
                    "registryValueType": null,
                    "registryValue": null,
                    "accountName": null,
                    "domainName": null,
                    "userSid": null,
                    "aadUserId": null,
                    "userPrincipalName": null,
                    "detectionStatus": "Detected"
                },
                {
                    "entityType": "File",
                    "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
                    "sha1": "8563f95b2f8a284fc99da44500cd51a77c1ff36c",
                    "sha256": "dc0ade0c95d6db98882bc8fa6707e64353cd6f7767ff48d6a81a6c2aef21c608",
                    "fileName": "suspicious.dll",
                    "filePath": "c:\\temp",
                    "processId": null,
                    "processCommandLine": null,
                    "processCreationTime": null,
                    "parentProcessId": null,
                    "parentProcessCreationTime": null,
                    "parentProcessFileName": null,
                    "parentProcessFilePath": null,
                    "ipAddress": null,
                    "url": null,
                    "registryKey": null,
                    "registryHive": null,
                    "registryValueType": null,
                    "registryValue": null,
                    "accountName": null,
                    "domainName": null,
                    "userSid": null,
                    "aadUserId": null,
                    "userPrincipalName": null,
                    "detectionStatus": "Detected"
                }
            ]
        },
        ...
    ]
}
```

## <a name="see-also"></a>راجع أيضًا

[استعلامات OData باستخدام Microsoft Defender ل Endpoint](exposed-apis-odata-samples.md)
