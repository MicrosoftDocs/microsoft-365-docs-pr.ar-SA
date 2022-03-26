---
title: توافق الاتصالات مع حلول SIEM
description: تعرف على تكامل توافق الاتصالات مع حلول SIEM.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d957b5fec4341cd7335f5c5a49b6654ffaf51f68
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "63570838"
---
# <a name="communication-compliance-with-siem-solutions"></a>توافق الاتصالات مع حلول SIEM

[التوافق مع](communication-compliance.md) الاتصالات هو حل مخاطر insider في Microsoft 365 يساعد على تقليل مخاطر الاتصال من خلال مساعدتك على الكشف عن الرسائل غير المناسبة في مؤسستك والتقاطها والعمل عليها. يتم استخدام معلومات الأمان وحلول إدارة الأحداث (SIEM) مثل [Microsoft Sentinel أو](https://azure.microsoft.com/services/azure-sentinel) [Splunk](https://www.splunk.com/) بشكل شائع لتجميع التهديدات وتعقبها داخل المؤسسة.

هناك حاجة شائعة ل المؤسسات وهي دمج تنبيهات توافق الاتصالات وحلول SIEM هذه. باستخدام هذا التكامل، يمكن ل المؤسسات عرض تنبيهات توافق الاتصالات في حل SIEM الخاص بها، ثم معالجة التنبيهات ضمن سير عمل توافق الاتصالات وتجربة المستخدم. على سبيل المثال، يرسل موظف رسالة مسيئة إلى موظف آخر ويكشف عن هذه الرسالة بواسطة مراقبة نهج توافق الاتصالات للمحتوى غير المناسب. يتم تعقب هذه الأحداث في Microsoft 365 التدقيق (المعروف أيضا باسم "سجل التدقيق الموحد") بواسطة حل توافق الاتصالات ويتم استيرادها إلى حل SIEM. يتم عندئذ تشغيل تنبيه في حل SIEM الخاص بالمنظمة من الأحداث التي يتم مراقبتها في Microsoft 365 التدقيق المقترنة بتنبيهات توافق الاتصالات. يتم إعلام المحقين بالتنبيه في حلول SIEM، ثم يحققون في التنبيه ويحلونه في حل توافق الاتصالات.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>تنبيهات توافق الاتصالات في Microsoft 365 التدقيق

يتم التقاط كافة تطابقات نهج توافق الاتصالات في Microsoft 365 التدقيق. تظهر الأمثلة التالية التفاصيل المتوفرة لأنشطة مطابقة نهج توافق الاتصالات المحددة:

**مثال على إدخال سجل التدقيق في قالب نهج المحتوى غير المناسب متطابق:**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/7/2021 5:30:11 AM
UserIds: user1@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-07T05:30:11","Id":"44e98a7e-57fd-4f89-79b8-08d941084a35","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<HE1P190MB04600526C0524C75E5750C5AC61A9@HE1P190MB0460.EURP190.PROD.OUTLOOK.COM\>","UserId":"user1@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"53be0bf4-75ee-4315-b65d-17d63bdd53ae","SRPolicyName":"Adult images","SRRuleMatchDetails":\[\]}}
ResultIndex: 24
ResultCount: 48
Identity: 44e98a7e-57fd-4f89-79b8-08d941084a35
IsValid: True
ObjectState: Unchanged
```

**مثال على إدخال Microsoft 365 تدقيق نهج مع تطابق الكلمات الأساسية المخصصة (نوع المعلومات الحساسة المخصصة):**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/6/2021 9:50:12 PM
UserIds: user2@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-06T21:50:12","Id":"5c61aae5-26fc-4c8e-0791-08d940c8086f","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"public\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<20210706174831.24375086.807067@sailthru.com\>","UserId":"user2@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"a97cf128-c0fc-42a1-88e3-fd3b88af9941","SRPolicyName":"Insiders","SRRuleMatchDetails":\[{"SRCategoryName":"New insiders lexicon"}\]}}
ResultIndex: 46
ResultCount: 48
Identity: 5c61aae5-26fc-4c8e-0791-08d940c8086f
IsValid: True
ObjectState: Unchanged
```

> [!NOTE]
> في الوقت الحالي، قد يكون هناك فترة تأخير تصل إلى 24 ساعة بين وقت تسجيل تطابق النهج في تدقيق Microsoft 365 والوقت الذي يمكنك فيه التحقق من تطابقات النهج في توافق الاتصالات.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>تكوين توافق الاتصالات وتكامل Microsoft Sentinel

عندما تستخدم Microsoft Sentinel لتجميع تطابقات نهج توافق الاتصالات، يستخدم Sentinel Microsoft 365 التدقيق كمصدر البيانات. لدمج تنبيهات توافق الاتصالات مع Sentinel، أكمل الخطوات التالية:

1. [Onboard to Microsoft Sentinel](/azure/sentinel/quickstart-onboard). كجزء من عملية التهيئة، ستكوين مصادر البيانات.
2. قم بتكوين موصل Microsoft Office 365 Microsoft [Sentinel،](/azure/sentinel/data-connectors-reference#microsoft-office-365) وحدد *ضمن تكوين* الموصل Exchange.
3. تكوين استعلام البحث لاسترداد تنبيهات توافق الاتصالات. على سبيل المثال:

    *| OfficeActivity | حيث OfficeWorkload == "Exchange" و Operation == "SupervisionRuleMatch" | الفرز حسب TimeGenerated*

    للتصفية لمستخدم معين، يمكنك استخدام تنسيق الاستعلام التالي:

    *| OfficeActivity | حيث OfficeWorkload == "Exchange" و Operation == "SupervisionRuleMatch" و UserId == "User1@Contoso.com" | الفرز حسب TimeGenerated*

لمزيد من المعلومات حول Microsoft 365 تدقيق Office 365 التي تم تجميعها بواسطة Microsoft Sentinel، راجع [مرجع سجلات جهاز عرض Azure](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>تكوين توافق الاتصالات وتكامل Splunk

لدمج تنبيهات توافق الاتصالات مع Splunk، أكمل الخطوات التالية:

1. تثبيت [الوظائف الإضافية Splunk Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. تكوين تطبيق تكامل في Azure AD ل الوظائف الإضافية Splunk Microsoft Office 365
3. تكوين استعلامات البحث في حل Splunk. استخدم مثال البحث التالي لتحديد كل تنبيهات توافق الاتصالات:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=SupervisionRuleMatch*

لتصفية النتائج للحصول على نهج توافق اتصالات معين، يمكنك استخدام *المعلمة SRPolicyMatchDetails.SRPolicyName* .

على سبيل المثال، قد يرجع مثال البحث التالي تنبيهات للمطابقات مع نهج توافق الاتصالات المسمى *المحتوى غير المناسب*:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

يعرض الجدول التالي نتائج بحث نموذجية لأنواع نهج مختلفة:

| أنواع النهج | مثال على نتائج البحث |
| :------------------ | :--------------------------------------- |
| نهج يكشف عن قائمة الكلمات الأساسية المخصصة لنوع المعلومات الحساسة | { <br> وقت الإنشاء: 2021-09-17T16:29:57 <br> الم ID: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: true <br> ObjectId: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> العملية: الإشرافRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM. ملاحظة"،"CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> الإصدار: 1 <br> حمل العمل: Exchange <br> } |
| نهج يكشف عن لغة غير ملائمة | { <br> وقت الإنشاء: 2021-09-17T23:44:35 <br> الم ID: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: true <br> ObjectId: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> العملية: الإشرافRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM.Yammer. الرسالة"،"CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> الإصدار: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>تكوين توافق الاتصالات مع حلول SIEM الأخرى

لاسترداد تطابقات نهج توافق الاتصالات من Microsoft 365 التدقيق، يمكنك إما استخدام PowerShell أو Office 365 [API للإدارة](/office/office-365-management-api/office-365-management-activity-api-reference).

عند استخدام PowerShell، يمكنك استخدام أي من هذه المعلمات مع **الأمر cmdlet Search-UnifiedAuditLog** لتصفية أحداث سجل التدقيق لأنشطة توافق الاتصالات.

| معلمة سجل التدقيق | قيمة معلمة توافق الاتصالات |
| :------------------ | :--------------------------------------- |
| العمليات          | الإشرافRuleMatch                     |
| RecordType          | ComplianceSupervisionExchange            |

على سبيل المثال، ما يلي نموذج للبحث باستخدام المعلمة **Operations** *وقيمة SupervisionRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
فيما يلي نموذج للبحث باستخدام المعلمة **RecordsType** *وقيمة ComplianceSupervisionExchange* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>الموارد

- [تدقيق توافق الاتصالات](communication-compliance-reports-audits.md#audit)
- [التدقيق المتقدم في Microsoft 365](advanced-audit.md)
- [Office 365 API لنشاط الإدارة](/office/office-365-management-api/office-365-management-activity-api-reference)
