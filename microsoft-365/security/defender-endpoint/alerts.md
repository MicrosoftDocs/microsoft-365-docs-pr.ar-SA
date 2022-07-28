---
title: الحصول على واجهة برمجة تطبيقات التنبيهات
description: تعرف على أساليب وخصائص نوع مورد التنبيه في Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، get، التنبيهات، الأخيرة
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
ms.openlocfilehash: e03de336dbbcdad5b9e18730936a507bf1d627bc
ms.sourcegitcommit: 1e53bf8208c30d7b60685896207cc1142bebf34a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67059789"
---
# <a name="alert-resource-type"></a>نوع مورد التنبيه

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="methods"></a>اساليب

<br>

****

|الاسلوب|نوع الإرجاع|الوصف|
|---|---|---|
|[الحصول على تنبيه](get-alert-info-by-id.md)|[تنبيه](alerts.md)|الحصول على كائن [تنبيه](alerts.md) واحد.|
|[تنبيهات القائمة](get-alerts.md)|مجموعة [التنبيهات](alerts.md)|قائمة مجموعة [التنبيهات](alerts.md) .|
|[تحديث التنبيه](update-alert.md)|[تنبيه](alerts.md)|تحديث [تنبيه](alerts.md) معين.|
|[تنبيهات التحديثات الدفعية](batch-update-alerts.md)||تحديث دفعة من [التنبيهات](alerts.md).|
|[إنشاء تنبيه](create-alert-by-reference.md)|[تنبيه](alerts.md)|إنشاء تنبيه استنادا إلى بيانات الحدث التي تم الحصول عليها من [التتبع المتقدم](run-advanced-query-api.md).|
|[سرد المجالات ذات الصلة](get-alert-related-domain-info.md)|مجموعة المجالات|سرد عناوين URL المقترنة بالتنبيه.|
|[سرد الملفات ذات الصلة](get-alert-related-files-info.md)|[مجموعة الملفات](files.md)|سرد كيانات [الملف](files.md) المقترنة [بالتنبيه](alerts.md).|
|[سرد عناوين IP ذات الصلة](get-alert-related-ip-info.md)|مجموعة IP|سرد عناوين IP المقترنة بالتنبيه.|
|[الحصول على الأجهزة ذات الصلة](get-alert-related-machine-info.md)|[الجهاز](machine.md)|[الجهاز](machine.md) المقترن [بالتنبيه](alerts.md).|
|[الحصول على المستخدمين المرتبطين](get-alert-related-user-info.md)|[User](user.md)|[المستخدم](user.md) المقترن [بالتنبيه](alerts.md).|
|

## <a name="properties"></a>خصائص

<br>

****

|الخاصيه|نوع|الوصف|
|---|---|---|
|id|سلسلة|معرف التنبيه.|
|عنوان|سلسلة|عنوان التنبيه.|
|وصف|سلسلة|وصف التنبيه.|
|alertCreationTime|Nullable DateTimeOffset|التاريخ والوقت (في UTC) تم إنشاء التنبيه.|
|lastEventTime|Nullable DateTimeOffset|آخر تكرار للحدث الذي أدى إلى تشغيل التنبيه على نفس الجهاز.|
|firstEventTime|Nullable DateTimeOffset|التكرار الأول للحدث الذي أدى إلى تشغيل التنبيه على هذا الجهاز.|
|lastUpdateTime|Nullable DateTimeOffset|التاريخ والوقت (في UTC) تم آخر تحديث للتنبيه.|
|resolvedTime|Nullable DateTimeOffset|التاريخ والوقت الذي تم فيه تغيير حالة التنبيه إلى "تم الحل".|
|معرف الحدث|قيمة طويلة فارغة|معرف [الحادث](view-incidents-queue.md) الخاص بالتنبيه.|
|معرف التحقيق|قيمة طويلة فارغة|معرف [التحقيق](automated-investigations.md) المتعلق بالتنبيه.|
|حالة التحقيق|قائمة تعداد فارغة|الحالة الحالية [للتحقيق](automated-investigations.md). القيم المحتملة هي: 'غير معروف'، 'تم الإنهاء'، 'SuccessfullyRemediated'، 'Benign'، 'Failed'، 'PartiallyRemediated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallyInvestigated', 'TerminatedByUser', 'TerminatedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'SuppressedAlert'.|
|معين إلى|سلسلة|مالك التنبيه.|
|rbacGroupName|سلسلة|اسم مجموعة أجهزة RBAC.|
|mitreTechniques|سلسلة|معرف تقنية Mitre Enterprise.|
|مستخدم ذي صلة|سلسلة|تفاصيل المستخدم المتعلقة بتنبيه معين.|
|شده|التعداد|خطورة التنبيه. القيم المحتملة هي: "غير محدد"، و"معلوماتي"، و"منخفض"، و"متوسط" و"مرتفع".|
|حاله|التعداد|تحديد الحالة الحالية للتنبيه. القيم المحتملة هي: "غير معروف" و"جديد" و"InProgress" و"تم الحل".|
|تصنيف|قائمة تعداد فارغة|مواصفات التنبيه. القيم المحتملة هي: 'غير معروف'، 'FalsePositive'، 'TruePositive'.|
|تحديد|قائمة تعداد فارغة|يحدد تحديد التنبيه. القيم المحتملة هي: 'NotAvailable', 'Apt', 'Malware', 'SecurityPersonnel', 'SecurityTesting', 'UnwantedSoftware', 'Other'.|
|الفئه|سلسلة|فئة التنبيه.|
|مصدر الكشف|سلسلة|مصدر الكشف.|
|threatFamilyName|سلسلة|عائلة المخاطر.|
|اسم التهديد|سلسلة|اسم التهديد.|
|معرف الجهاز|سلسلة|معرف كيان [جهاز](machine.md) مقترن بالتنبيه.|
|اسم الكمبيوتر|سلسلة|اسم [الجهاز](machine.md) المؤهل بالكامل.|
|aadTenantId|سلسلة|معرف Azure Active Directory.|
|معرف الكشف|سلسلة|معرف جهاز الكشف الذي قام بتشغيل التنبيه.|
|تعليقات|قائمة تعليقات التنبيه|يحتوي كائن تعليق التنبيه على: سلسلة تعليق وسلسلة createdBy ووقت تاريخ createTime.|
|الادله|قائمة بأدلة التنبيه|الأدلة المتعلقة بالتنبيه. راجع المثال أدناه.|
|

>[!NOTE]
>حوالي 29 أغسطس 2022، سيتم إهمال قيم تحديد التنبيه المدعومة مسبقا ('Apt' و'SecurityPersonnel') ولن تعود متوفرة عبر واجهة برمجة التطبيقات.

### <a name="response-example-for-getting-single-alert"></a>مثال استجابة للحصول على تنبيه واحد:

```http
GET https://api.securitycenter.microsoft.com/api/alerts/da637472900382838869_1364969609
```

```json
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
}
```
