---
title: توافق الاتصالات مع حلول إدارة معلومات الأمان والأحداث
description: تعرف على تكامل توافق الاتصالات مع حلول SIEM.
keywords: Microsoft 365، وMicrosoft Purview، والامتثال، وتوافق الاتصالات
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
ms.openlocfilehash: f111fbd831f36cd8f1647e4b99565a24372387b8
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953859"
---
# <a name="communication-compliance-with-siem-solutions"></a>توافق الاتصالات مع حلول إدارة معلومات الأمان والأحداث

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[توافق الاتصالات](communication-compliance.md) هو حل مخاطر من الداخل في Microsoft Purview يساعد على تقليل مخاطر الاتصال من خلال مساعدتك في اكتشاف الرسائل غير المناسبة في مؤسستك والتقاطها والعمل عليها. عادة ما تستخدم حلول إدارة معلومات الأمان والأحداث (SIEM) مثل [Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel) أو [Splunk](https://www.splunk.com/) لتجميع التهديدات وتتبعها داخل المؤسسة.

من الاحتياجات المشتركة للمؤسسات دمج تنبيهات الامتثال للاتصالات وحلول SIEM هذه. مع هذا التكامل، يمكن للمؤسسات عرض تنبيهات توافق الاتصالات في حل SIEM الخاص بها ثم معالجة التنبيهات ضمن سير عمل توافق الاتصالات وتجربة المستخدم. على سبيل المثال، يرسل موظف رسالة مسيئة إلى موظف آخر ويتم الكشف عن هذه الرسالة من خلال مراقبة نهج توافق الاتصالات للمحتوى غير المناسب. يتم تعقب هذه الأحداث في Microsoft 365 Audit (المعروف أيضا باسم "سجل التدقيق الموحد") بواسطة حل توافق الاتصالات واستيرادها إلى حل SIEM. ثم يتم تشغيل تنبيه في حل SIEM للمؤسسة من الأحداث المراقبة في Microsoft 365 التدقيق المقترنة بتنبيهات توافق الاتصالات. يتم إعلام المحققين بالتنبيه في حلول SIEM ثم يحققون في التنبيه ويعالجونه في حل التوافق مع الاتصالات.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>تنبيهات التوافق مع الاتصالات في Microsoft 365 Audit

يتم تسجيل جميع تطابقات نهج التوافق مع الاتصالات في Microsoft 365 Audit. توضح الأمثلة التالية التفاصيل المتوفرة لأنشطة مطابقة نهج توافق الاتصالات المحددة:

**مثال لإدخال سجل التدقيق لمطابقة قالب نهج المحتوى غير المناسب:**

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

**مثال على إدخال سجل تدقيق Microsoft 365 لنهج مع مطابقة كلمة أساسية مخصصة (نوع معلومات حساسة مخصصة):**

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
> حاليا، قد يكون هناك تأخير لمدة 24 ساعة بين وقت تسجيل تطابق النهج في Microsoft 365 Audit والوقت الذي يمكنك فيه التحقق من تطابقات النهج في توافق الاتصالات.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>تكوين توافق الاتصالات وتكامل Microsoft Sentinel

عند استخدام Microsoft Sentinel لتجميع تطابقات نهج توافق الاتصالات، يستخدم Sentinel Microsoft 365 Audit كمصدر بيانات. لدمج تنبيهات توافق الاتصالات مع Sentinel، أكمل الخطوات التالية:

1. [إلحاق ب Microsoft Sentinel](/azure/sentinel/quickstart-onboard). كجزء من عملية الإلحاق، ستقوم بتكوين مصادر البيانات الخاصة بك.
2. تكوين [موصل بيانات](/azure/sentinel/data-connectors-reference#microsoft-office-365) Microsoft Sentinel Microsoft Office 365 وضمن تكوين الموصل، حدد *Exchange*.
3. تكوين استعلام البحث لاسترداد تنبيهات التوافق مع الاتصالات. على سبيل المثال:

    *| | OfficeActivity حيث OfficeWorkload == "Exchange" والعملية == "RangRuleMatch" | فرز حسب TimeGenerated*

    للتصفية لمستخدم معين، يمكنك استخدام تنسيق الاستعلام التالي:

    *| | OfficeActivity حيث OfficeWorkload == "Exchange" والعملية == "CorrelationRuleMatch" وUserId == "User1@Contoso.com" | فرز حسب TimeGenerated*

لمزيد من المعلومات حول سجلات التدقيق Microsoft 365 Office 365 جمعها Microsoft Sentinel، راجع [مرجع سجلات Azure Monitor](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>تكوين توافق الاتصالات وتكامل Splunk

لدمج تنبيهات توافق الاتصالات مع Splunk، أكمل الخطوات التالية:

1. تثبيت [الوظيفة الإضافية Splunk ل Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. تكوين تطبيق تكامل في Azure AD للوظيفة الإضافية Splunk Microsoft Office 365
3. تكوين استعلامات البحث في حل Splunk الخاص بك. استخدم مثال البحث التالي لتحديد جميع تنبيهات توافق الاتصالات:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=UmbrellaRuleMatch*

لتصفية النتائج لنهج توافق اتصالات محدد، يمكنك استخدام معلمة *SRPolicyMatchDetails.SRPolicyName* .

على سبيل المثال، قد يرجع مثال البحث التالي تنبيهات للتطابقات مع نهج توافق الاتصالات *المسمى محتوى غير مناسب*:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=UmbrellaRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

يعرض الجدول التالي نماذج نتائج البحث لأنواع النهج المختلفة:

| أنواع النهج | مثال على نتائج البحث |
| :------------------ | :--------------------------------------- |
| نهج الكشف عن قائمة كلمات أساسية مخصصة لنوع المعلومات الحساسة | { <br> وقت الإنشاء: 2021-09-17T16:29:57 <br> المعرف: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: true <br> Objectid: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> العملية: NullRuleMatch <br> معرف المؤسسة: d6a06676-95e8-4632-b949-44bc00f0793f <br> نوع السجل: 68 <br> ResultStatus: {"ItemClass":"IPM. ملاحظة","CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> معرف المستخدم: user1@contoso.OnMicrosoft.com <br> UserKey: الإشراف علىStoreDeliveryAgent <br> UserType: 0 <br> الإصدار: 1 <br> حمل العمل: Exchange <br> } |
| نهج الكشف عن اللغة غير المناسبة | { <br> وقت الإنشاء: 2021-09-17T23:44:35 <br> المعرف: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: true <br> Objectid: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> العملية: NullRuleMatch <br> معرف المؤسسة: d6a06676-95e8-4632-b949-44bc00f0793f <br> نوع السجل: 68 <br> ResultStatus: {"ItemClass":"IPM.Yammer. رسالة","CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> معرف المستخدم: user1@contoso.com <br> UserKey: الإشراف علىStoreDeliveryAgent <br> UserType: 0 <br> الإصدار: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>تكوين توافق الاتصالات مع حلول SIEM الأخرى

لاسترداد تطابقات نهج توافق الاتصالات من Microsoft 365 Audit، يمكنك إما استخدام PowerShell أو [واجهة برمجة تطبيقات إدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

عند استخدام PowerShell، يمكنك استخدام أي من هذه المعلمات مع أمر cmdlet **Search-UnifiedAuditLog** لتصفية أحداث سجل التدقيق لأنشطة توافق الاتصالات.

| معلمة سجل التدقيق | قيمة معلمة توافق الاتصالات |
| :------------------ | :--------------------------------------- |
| عمليات          | متطابقات لRuruleMatch                     |
| نوع السجل          | ComplianceSupervisionExchange            |

على سبيل المثال، ما يلي هو نموذج بحث باستخدام **معلمة العمليات** وقيمة *ParaerRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
فيما يلي نموذج بحث باستخدام معلمة **RecordsType** وقيمة *ComplianceSupervisionExchange* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>الموارد

- [تدقيق التوافق مع الاتصالات](communication-compliance-reports-audits.md#audit)
- [تدقيق Microsoft Purview (Premium)](advanced-audit.md)
- [مرجع واجهة برمجة تطبيقات نشاط إدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)
