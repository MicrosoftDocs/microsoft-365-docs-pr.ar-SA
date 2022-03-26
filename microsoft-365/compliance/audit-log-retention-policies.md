---
title: إدارة سياسات استبقاء سجل التدقيق
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: إن سياسات استبقاء سجل التدقيق هي جزء من قدرات التدقيق المتقدم الجديدة في Microsoft 365. يتيح لك نهج استبقاء سجل التدقيق تحديد المدة التي يجب فيها الاحتفاظ بسجلات التدقيق في مؤسستك.
ms.openlocfilehash: f8c269aa4541c438942c69831857ed531681b742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63565967"
---
# <a name="manage-audit-log-retention-policies"></a>إدارة سياسات استبقاء سجل التدقيق

يمكنك إنشاء سياسات استبقاء سجل التدقيق وإدارتها في مركز التوافق في Microsoft 365. إن سياسات استبقاء سجل التدقيق هي جزء من قدرات التدقيق المتقدم الجديدة في Microsoft 365. يتيح لك نهج استبقاء سجل التدقيق تحديد المدة التي يجب فيها الاحتفاظ بسجلات التدقيق في مؤسستك. يمكنك الاحتفاظ بسجلات التدقيق لمدة تصل إلى 10 سنوات. يمكنك إنشاء سياسات استنادا إلى المعايير التالية:

- كل الأنشطة في واحدة أو أكثر من Microsoft 365 الخدمات
- أنشطة معينة (في خدمة Microsoft 365) يتم تنفيذها بواسطة جميع المستخدمين أو من قبل مستخدمين محددين
- مستوى أولوية يحدد النهج الذي له الأسبقية في وجود نهج متعددة في مؤسستك

## <a name="default-audit-log-retention-policy"></a>نهج استبقاء سجل التدقيق الافتراضي

يوفر التدقيق المتقدم في Microsoft 365 نهج استبقاء سجل التدقيق الافتراضي لجميع المؤسسات. يحتفظ هذا النهج بجميع سجلات التدقيق Exchange Online SharePoint عبر الإنترنت OneDrive for Business و Azure Active Directory لمدة عام واحد. يحتفظ هذا النهج الافتراضي بسجلات التدقيق التي تحتوي على قيمة **Exchange** و SharePoint و **OneDrive** و **AzureActiveDirectory** ل خاصية **حمل** العمل (وهي الخدمة التي حدث فيها النشاط). لا يمكن تعديل النهج الافتراضي. راجع القسم [مزيد من المعلومات](#more-information) في هذه المقالة للحصول على قائمة بأنواع السجلات لكل حمل عمل مضمن في النهج الافتراضي.

> [!NOTE]
> لا ينطبق نهج استبقاء سجل التدقيق الافتراضي إلا على سجلات التدقيق للنشاط الذي يقوم به المستخدمون الذين تم تعيين ترخيص Office 365 أو Microsoft 365 E5 أو لديهم ترخيص وظائف التوافق في Microsoft 365 E5 eDiscovery و E5 eDiscovery وY audit الإضافية. إذا كان لديك مستخدمون غير E5 أو مستخدمين ضيوف في مؤسستك، يتم الاحتفاظ بسجلات التدقيق المقابلة الخاصة بهم لمدة 90 يوما.

## <a name="before-you-create-an-audit-log-retention-policy"></a>قبل إنشاء نهج استبقاء سجل التدقيق

- يجب تعيين دور تكوين المؤسسة في مركز التوافق في Microsoft 365 لإنشاء نهج استبقاء تدقيق أو تعديله.

- يمكنك الحصول على 50 من سياسات استبقاء سجل التدقيق كحد أقصى في مؤسستك.

- للاحتفاظ بسجل تدقيق لمدة أطول من 90 يوما (وما يصل إلى سنة واحدة)، يجب تعيين ترخيص ل Office 365 E5 أو Microsoft 365 E5 للمستخدم الذي ينشئ سجل التدقيق (من خلال إجراء نشاط مدقق) أو لديه ترخيص وظائف التوافق في Microsoft 365 E5 أو E5 eDiscovery وY audit. للاحتفاظ بسجلات التدقيق لمدة 10 سنوات، يجب أيضا تعيين ترخيص الوظائف الإضافية للاحتفاظ بسجل التدقيق لمدة 10 سنوات بالإضافة إلى ترخيص E5 للمستخدم الذي ينشئ سجل التدقيق.

- تأخذ كل نهج استبقاء سجل التدقيق المخصصة (التي أنشأتها مؤسستك) الأولوية على نهج الاستبقاء الافتراضي. على سبيل المثال، إذا قمت بإنشاء نهج استبقاء سجل تدقيق لنشاط علبة بريد Exchange التي تتضمن فترة استبقاء أقصر من سنة واحدة، سيتم الاحتفاظ بسجلات التدقيق لأنشطة علبة بريد Exchange لمدة أقصر يحددها النهج المخصص.

## <a name="create-an-audit-log-retention-policy"></a>إنشاء نهج استبقاء سجل تدقيق

1. انتقل إلى <https://compliance.microsoft.com> حساب مستخدم تم تعيين دور تكوين المؤسسة له في صفحة الأذونات في الصفحة مركز التوافق في Microsoft 365.

2. في الجزء الأيسر من مركز التوافق في Microsoft 365، انقر فوق **تدقيق**.

3. انقر فوق **علامة التبويب سياسات استبقاء** التدقيق.

4. انقر **فوق إنشاء نهج استبقاء التدقيق**، ثم أكمل الحقول التالية على صفحة قائمة منتظة:

   ![صفحة من حولاء نهج استبقاء التدقيق الجديد.](../media/CreateAuditLogRetentionPolicy.png)

   1. **اسم النهج:** اسم نهج استبقاء سجل التدقيق. يجب أن يكون هذا الاسم فريدا في مؤسستك، ولا يمكن تغييره بعد إنشاء النهج.

   2. **الوصف:** اختياري، ولكنه مفيد لتوفير معلومات حول النهج، مثل نوع السجل أو حمل العمل والمستخدمين المحددين في النهج والمدة.

   3. **المستخدمون:** حدد مستخدما واحدا أو أكثر لتطبيق النهج عليه. إذا تركت هذا المربع فارغا، سيتم تطبيق النهج على جميع المستخدمين. إذا تركت نوع **السجل فارغا** ، فيجب عليك تحديد مستخدم.

   4. **نوع السجل:** نوع سجل التدقيق الذي ينطبق عليه النهج. إذا تركت هذه الخاصية فارغة، فيجب تحديد مستخدم في **المربع** المستخدمون. يمكنك تحديد نوع سجل واحد أو أنواع سجلات متعددة:
      - إذا قمت بتحديد نوع سجل واحد، يتم عرض حقل **الأنشطة** ديناميكيا. يمكنك استخدام القائمة المنسدل لتحديد أنشطة من نوع السجل المحدد لتطبيق النهج عليها. إذا لم تحدد أنشطة معينة، سيتم تطبيق النهج على كل الأنشطة من نوع السجل المحدد.
      - إذا حددت أنواع سجلات متعددة، فلا تملك القدرة على تحديد الأنشطة. سيتم تطبيق النهج على كل أنشطة أنواع السجلات المحددة.

   5. **المدة:** مقدار الوقت للاحتفاظ بسجلات التدقيق التي تفي بمعايير النهج.

   6. **الأولوية:** تحدد هذه القيمة الترتيب الذي تتم به معالجة سياسات استبقاء سجل التدقيق في مؤسستك. تشير القيمة الدنيا إلى أولوية أعلى. الأولوية الصحيحة هي القيم الرقمية بين **1** **و10000**. القيمة **1** هي الأولوية العليا، **وقيمة 10000** هي أقل أولوية. على سبيل المثال، يأخذ النهج الذي له القيمة **5** الأولوية على نهج بقيمة **10**. كما تم شرحه مسبقا، فإن أي نهج استبقاء سجل تدقيق مخصص له الأولوية على النهج الافتراضي لمنظمتك.

5. انقر **فوق** حفظ لإنشاء نهج استبقاء سجل التدقيق الجديد.

يتم عرض النهج الجديد في القائمة على علامة التبويب نهج **استبقاء** التدقيق.

## <a name="manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center"></a>إدارة سياسات استبقاء سجل التدقيق في مركز التوافق في Microsoft 365

يتم سرد سياسات استبقاء سجل التدقيق **على علامة التبويب** "سياسات استبقاء التدقيق" (تسمى أيضا لوحة *المعلومات*). يمكنك استخدام لوحة المعلومات لعرض سياسات استبقاء التدقيق وتحريرها وحذفها.

### <a name="view-policies-in-the-dashboard"></a>عرض السياسات في لوحة المعلومات

يتم سرد سياسات استبقاء سجل التدقيق في لوحة المعلومات. إحدى ميزات عرض السياسات في لوحة المعلومات هي أنه يمكنك النقر فوق عمود الأولوية لقائمة  السياسات في الأولوية التي يتم تطبيقها عليها. كما هو موضح مسبقا، تشير القيمة الدنيا إلى أولوية أعلى.

![عمود الأولوية في لوحة معلومات سياسات استبقاء التدقيق.](../media/AuditLogRetentionDashboardPriority.png)

يمكنك أيضا تحديد نهج لعرض إعداداته على صفحة قائمة منتحلة.

> [!NOTE]
> لا يتم عرض نهج استبقاء سجل التدقيق الافتراضي لمنظمتك في لوحة المعلومات.

### <a name="edit-policies-in-the-dashboard"></a>تحرير السياسات في لوحة المعلومات

لتحرير نهج، حدده لعرض صفحة منتحلة. يمكنك تعديل إعداد واحد أو أكثر ثم حفظ التغييرات.

> [!IMPORTANT]
>
> إذا كنت تستخدم **الأمر cmdlet New-UnifiedAuditLogRetentionPolicy**، فمن الممكن إنشاء نهج استبقاء سجل تدقيق لأنواع السجلات أو الأنشطة غير المتوفرة في أداة إنشاء نهج استبقاء التدقيق  في لوحة المعلومات. في هذه الحالة، لن تتمكن من تحرير النهج (على سبيل المثال، تغيير مدة الاستبقاء أو إضافة الأنشطة وإزالتها) من لوحة معلومات نهج **استبقاء** التدقيق. لن تتمكن من عرض النهج وحذفه إلا في مركز التوافق. لتحرير النهج، يجب استخدام الأمر [Cmdlet Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) في مركز التوافق & PowerShell.>
>
> **تلميح:** يتم عرض رسالة في أعلى صفحة القائمة العلوية لنهج يجب تحريرها باستخدام PowerShell.

### <a name="delete-policies-in-the-dashboard"></a>حذف سياسات في لوحة المعلومات

لحذف نهج، انقر فوق **الأيقونة حذف** ![حذف.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) ثم تأكد من أنك تريد حذف النهج. تتم إزالة النهج من لوحة المعلومات، ولكن قد يستغرق الأمر ما يصل إلى 30 دقيقة لإزالة النهج من مؤسستك.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>إنشاء سياسات استبقاء سجل التدقيق وإدارتها في PowerShell

يمكنك أيضا استخدام الأمان & Compliance Center PowerShell لإنشاء سياسات استبقاء سجل التدقيق وإدارتها. أحد أسباب استخدام PowerShell هو إنشاء نهج لنوع سجل أو نشاط غير متوفر في واجهة المستخدم.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>إنشاء نهج استبقاء سجل تدقيق في PowerShell

اتبع هذه الخطوات لإنشاء نهج استبقاء سجل التدقيق في PowerShell:

1. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. قم بتشغيل الأمر التالي لإنشاء نهج استبقاء سجل التدقيق:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   ينشئ هذا المثال نهج استبقاء سجل التدقيق المسمى "Microsoft Teams التدقيق" باستخدام هذه الإعدادات:

   - وصف النهج.
   - تحتفظ بكل Microsoft Teams الأنشطة (كما تم تعريفها بواسطة *المعلمة RecordType*).
   - تحتفظ Microsoft Teams التدقيق لمدة 10 سنوات.
   - أولوية 100.

فيما يلي مثال آخر لإنشاء نهج استبقاء سجل التدقيق. يحتفظ هذا النهج بسجلات التدقيق لنشاط "تسجيل دخول المستخدم" لمدة ستة أشهر للمستخدم admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

لمزيد من المعلومات، راجع [New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>عرض السياسات في PowerShell

استخدم [الأمر cmdlet Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) في مركز التوافق & PowerShell لعرض نهج استبقاء سجل التدقيق.

إليك أمر نموذج لعرض الإعدادات لكل سياسات استبقاء سجل التدقيق في مؤسستك. يفرز هذا الأمر السياسات من الأولوية العليا إلى الأقل.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> لا **تقوم عملية cmdlet Get-UnifiedAuditLogRetentionPolicy** بإرجاع نهج استبقاء سجل التدقيق الافتراضي لم المؤسسة.

### <a name="edit-policies-in-powershell"></a>تحرير السياسات في PowerShell

استخدم [الأمر cmdlet Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) في مركز التوافق & PowerShell لتحرير نهج استبقاء سجل تدقيق موجود.

### <a name="delete-policies-in-powershell"></a>حذف سياسات في PowerShell

استخدم [الأمر cmdlet Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) في Security & Compliance Center PowerShell لحذف نهج استبقاء سجل التدقيق. قد يستغرق الأمر ما يصل إلى 30 دقيقة لإزالة النهج من مؤسستك.

## <a name="more-information"></a>معلومات إضافية

كما ذكر سابقا، يتم الاحتفاظ بسجلات التدقيق للعمليات في Azure Active Directory Exchange Online و SharePoint Online و OneDrive for Business لمدة عام واحد بشكل افتراضي. يسرد الجدول التالي كل أنواع السجلات (لكل من هذه الخدمات) المضمنة في نهج استبقاء سجل التدقيق الافتراضي. وهذا يعني أنه يتم الاحتفاظ بسجلات التدقيق لأي عملية باستخدام هذا النوع من السجلات لمدة سنة واحدة إلا إذا كان نهج استبقاء سجل التدقيق المخصص له الأسبقية لنوع سجل معين أو عملية أو مستخدم معين. يتم عرض قيمة "تعداد" (التي يتم عرضها كقيمة للممتلكات RecordType في سجل تدقيق) لكل نوع سجل بين  الوالدين.

<br>

****

|AzureActiveDirectory|Exchange |SharePoint أو OneDrive|
|---|---|---|
|AzureActiveDirectory (8)|ExchangeAdmin (1)|ComplianceDLPSharePoint (11)|
|AzureActiveDirectoryAccountLogon (9)|ExchangeItem (2)|ComplianceDLPSharePointClassification (33)|
|AzureActiveDirectoryStsLogon (15)|الحملة (62)|Project (35)|
||ComplianceDLPExchange (13)|SharePoint (4)|
||ComplianceSupervisionExchange (68)|SharePointCommentOperation (37)|
||CustomerKeyServiceEncryption (69)|SharePointContentTypeOperation (55)|
||ExchangeAggregatedOperation (19)|SharePointFieldOperation (56)|
||ExchangeItemAregregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
