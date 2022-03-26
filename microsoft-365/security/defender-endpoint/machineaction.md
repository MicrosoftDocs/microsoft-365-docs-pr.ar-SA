---
title: machineAction نوع المورد
description: تعرف على أساليب وخصائص نوع مورد MachineAction في Microsoft Defender لنقطة النهاية.
keywords: apis، apis المعتمدة، الحصول، تنشيط الجهاز، الأخيرة
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
ms.technology: mde
ms.openlocfilehash: 625170f0e589ece6f6277dc8445f3af7bef11837
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63574227"
---
# <a name="machineaction-resource-type"></a>نوع مورد MachineAction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- لمزيد من المعلومات، راجع [إجراءات الاستجابة](respond-machine-alerts.md).

|الأسلوب|نوع الإرجاع|الوصف|
|---|---|---|
|[List MachineActions](get-machineactions-collection.md)|[إجراء الجهاز](machineaction.md)|[كيانات إجراءات](machineaction.md) جهاز القائمة.|
|[الحصول على MachineAction](get-machineaction-object.md)|[إجراء الجهاز](machineaction.md)|الحصول على كيان [إجراء جهاز](machineaction.md) واحد.|
|[تجميع حزمة التحقيق](collect-investigation-package.md)|[إجراء الجهاز](machineaction.md)|تجميع حزمة التحقيق من [جهاز](machine.md).|
|[الحصول على حزمة التحقيق SAS URI](get-package-sas-uri.md)|[إجراء الجهاز](machineaction.md)|احصل على URI لتنزيل حزمة التحقيق.|
|[جهاز عزل](isolate-machine.md)|[إجراء الجهاز](machineaction.md)|عزل [الجهاز](machine.md) عن الشبكة.|
|[تحرير الجهاز من العزل](unisolate-machine.md)|[إجراء الجهاز](machineaction.md)|إصدار [الجهاز](machine.md) من عزل.|
|[تقييد تنفيذ التطبيق](restrict-code-execution.md)|[إجراء الجهاز](machineaction.md)|تقييد تنفيذ التطبيق.|
|[إزالة تقييد التطبيق](unrestrict-code-execution.md)|[إجراء الجهاز](machineaction.md)|إزالة تقييد تنفيذ التطبيق.|
|[تشغيل مسح الحماية من الفيروسات](run-av-scan.md)|[إجراء الجهاز](machineaction.md)|قم بتشغيل فحص AV باستخدام Windows Defender (عند الاقتضاء).|
|[جهاز Offboard](offboard-machine-api.md)|[إجراء الجهاز](machineaction.md)|جهاز إيقاف [التشغيل](machine.md) من Microsoft Defender ل Endpoint.|
|[ملف إيقاف وفحص](stop-and-quarantine-file.md)|[إجراء الجهاز](machineaction.md)|أوقف تنفيذ ملف على جهاز واحذفه.|
|[تشغيل الاستجابة المباشرة](run-live-response.md)|[إجراء الجهاز](machineaction.md)|تشغيل تسلسل أوامر الاستجابة المباشرة على جهاز|
|[الحصول على نتيجة استجابة مباشرة](get-live-response-result.md)|كيان URL|استرداد ارتباط تنزيل نتيجة أمر استجابة مباشرة معين بواسطة الفهرس الخاص به.|
|[إجراء إلغاء الجهاز](cancel-machine-action.md)|[إجراء الجهاز](machineaction.md)|إلغاء إجراء جهاز نشط.|

<br>

## <a name="properties"></a>الخصائص

|الخاصية|النوع|الوصف|
|---|---|---|
|الم ID|Guid|هوية كيان [إجراء](machineaction.md) الجهاز.|
|اكتب|تعداد|نوع الإجراء. القيم المحتملة هي: "RunAntiVirusScan" و"Offboard" و"Live Response" و"CollectInvestigationPackage" و"Isolate" و"Unisolate" و"StopAndQuarantineFile" و"RestrictCodeExecution" و"CanrrictCodeExecution".|
|النطاق|سلسلة|نطاق الإجراء. "كامل" أو "انتقائي" للعزل أو "سريع" أو "كامل" لمسح مكافحة الفيروسات.|
|طالب|سلسلة|هوية الشخص الذي نفذ الإجراء.|
|externalID|سلسلة|المعرف الذي يمكن للعميل إرساله في طلب الارتباط المخصص.|
|requestSource|سلسلة|اسم المستخدم/التطبيق الذي قام بتقديم الإجراء.|
|الأوامر|صفيف|الأوامر التي يجب تشغيلها. القيم المسموح بها هي PutFile و RunScript و GetFile.|
|إلغاءRequestor|سلسلة|هوية الشخص الذي ألغى الإجراء.|
|requestorComment|سلسلة|التعليق الذي تم كتابته عند إصدار الإجراء.|
|إلغاءComment|سلسلة|التعليق الذي تم كتابته عند إلغاء الإجراء.|
|الحالة|تعداد|الحالة الحالية للوامر. القيم المحتملة هي: "معلق" و"InProgress" و"نجح" و"فشل" و"مهى" و"تم إلغاء".|
|machineId|سلسلة|هو الم ID [للجهاز](machine.md) الذي تم تنفيذ الإجراء عليه.|
|computerDnsName|سلسلة|اسم [الجهاز الذي](machine.md) تم تنفيذ الإجراء عليه.|
|creationDateTimeUtc|DateTimeOffset|التاريخ والوقت الذي تم فيه إنشاء الإجراء.|
|إلغاءDateTimeUtc|DateTimeOffset|التاريخ والوقت الذي تم فيه إلغاء الإجراء.|
|lastUpdateDateTimeUtc|DateTimeOffset|آخر تاريخ وتاريخ تم فيه تحديث حالة الإجراء.|
|العنوان|سلسلة|عنوان إجراء الجهاز.|
|relatedFileInfo|الفئة|يحتوي على خصائص اثنين. سلسلة `fileIdentifier`، تعداد مع `fileIdentifierType` القيم المحتملة: "Sha1" و"Sha256" و"Md5".|

## <a name="json-representation"></a>تمثيل Json

```json
{
        "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
        "type": "Isolate",
        "scope": "Selective",
        "requestor": "Analyst@TestPrd.onmicrosoft.com",
        "requestorComment": "test for docs",
        "status": "Succeeded",
        "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
        "computerDnsName": "desktop-test",
        "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
        "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
        "relatedFileInfo": null
}
```
