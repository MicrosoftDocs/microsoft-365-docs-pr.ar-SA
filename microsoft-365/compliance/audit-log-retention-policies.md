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
description: تعد نهج استبقاء سجل التدقيق جزءا من قدرات تدقيق Microsoft Purview (Premium) الجديدة. يتيح لك نهج استبقاء سجل التدقيق تحديد مدة الاحتفاظ بسجلات التدقيق في مؤسستك.
ms.openlocfilehash: a19e12f82fc577406ea4257fc315902ca8238358
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000367"
---
# <a name="manage-audit-log-retention-policies"></a>إدارة سياسات استبقاء سجل التدقيق

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكنك إنشاء نهج استبقاء سجل التدقيق وإدارتها في مدخل توافق Microsoft Purview. تعد نهج استبقاء سجل التدقيق جزءا من قدرات تدقيق Microsoft Purview (Premium) الجديدة. يتيح لك نهج استبقاء سجل التدقيق تحديد مدة الاحتفاظ بسجلات التدقيق في مؤسستك. يمكنك الاحتفاظ بسجلات التدقيق لمدة تصل إلى 10 سنوات. يمكنك إنشاء نهج استنادا إلى المعايير التالية:

- كافة الأنشطة في واحدة أو أكثر من خدمات Microsoft 365
- أنشطة محددة (في خدمة Microsoft 365) يتم تنفيذها بواسطة جميع المستخدمين أو بواسطة مستخدمين محددين
- مستوى أولوية يحدد النهج الذي له الأسبقية في وجود نهج متعددة في مؤسستك

## <a name="default-audit-log-retention-policy"></a>نهج استبقاء سجل التدقيق الافتراضي

يوفر التدقيق (Premium) في Microsoft 365 نهج استبقاء سجل التدقيق الافتراضي لكافة المؤسسات. يحتفظ هذا النهج بكافة سجلات تدقيق Exchange Online SharePoint Online و OneDrive for Business وAzure Active Directory لمدة عام واحد. يحتفظ هذا النهج الافتراضي بسجلات التدقيق التي تحتوي على قيمة **Exchange** **SharePoint** **OneDrive** **وAzureActiveDirectory لخاصية** **Workload** (وهي الخدمة التي حدث فيها النشاط). لا يمكن تعديل النهج الافتراضي. راجع المقطع ["مزيد من المعلومات](#more-information) " في هذه المقالة للحصول على قائمة بأنواع السجلات لكل حمل عمل مضمن في النهج الافتراضي.

> [!NOTE]
> ينطبق نهج استبقاء سجل التدقيق الافتراضي فقط على سجلات التدقيق للنشاط الذي يقوم به المستخدمون الذين تم تعيين ترخيص Office 365 أو Microsoft 365 E5 لهم أو لديهم ترخيص وظيفة إضافية التوافق في Microsoft 365 E5 أو E5 eDiscovery و Audit. إذا كان لديك مستخدمون غير E5 أو مستخدمين ضيوف في مؤسستك، يتم الاحتفاظ بسجلات التدقيق المقابلة لمدة 90 يوما.

## <a name="before-you-create-an-audit-log-retention-policy"></a>قبل إنشاء نهج استبقاء سجل التدقيق

- يجب تعيين دور "تكوين المؤسسة" في مدخل التوافق لإنشاء نهج استبقاء التدقيق أو تعديله.

- يمكن أن يكون لديك 50 نهج استبقاء سجل تدقيق كحد أقصى في مؤسستك.

- للاحتفاظ بسجل تدقيق لمدة أطول من 90 يوما (وما يصل إلى سنة واحدة)، يجب تعيين ترخيص Office 365 E5 أو ترخيص Microsoft 365 E5 للمستخدم الذي يقوم بإنشاء سجل التدقيق (عن طريق تنفيذ نشاط مدقق) أو الحصول على ترخيص التوافق في Microsoft 365 E5 أو E5 eDiscovery ووظيفة التدقيق الإضافية. للاحتفاظ بسجلات التدقيق لمدة 10 سنوات، يجب أيضا تعيين ترخيص إضافي لاستبقاء سجل التدقيق لمدة 10 سنوات للمستخدم الذي ينشئ سجل التدقيق بالإضافة إلى ترخيص E5.

- جميع نهج استبقاء سجل التدقيق المخصصة (التي تم إنشاؤها بواسطة مؤسستك) لها الأولوية على نهج الاستبقاء الافتراضي. على سبيل المثال، إذا قمت بإنشاء نهج استبقاء سجل تدقيق لنشاط علبة بريد Exchange التي لها فترة استبقاء أقصر من سنة واحدة، فسيتم الاحتفاظ بسجلات التدقيق لأنشطة علبة بريد Exchange لمدة أقصر يحددها النهج المخصص.

## <a name="create-an-audit-log-retention-policy"></a>إنشاء نهج استبقاء سجل التدقيق

1. انتقل إلى <https://compliance.microsoft.com> حساب مستخدم تم تعيينه لدور "تكوين المؤسسة" في صفحة "الأذونات" في مدخل التوافق وسجل الدخول باستخدامه.

2. في الجزء الأيمن من مدخل التوافق، انقر فوق **"تدقيق**".

3. انقر فوق علامة التبويب **"تدقيق نهج الاستبقاء** ".

4. انقر فوق **"إنشاء نهج استبقاء التدقيق**"، ثم أكمل الحقول التالية في صفحة القائمة المنبثقة:

   ![صفحة قائمة منبثقة جديدة لنهج استبقاء التدقيق.](../media/CreateAuditLogRetentionPolicy.png)

   1. **اسم النهج:** اسم نهج استبقاء سجل التدقيق. يجب أن يكون هذا الاسم فريدا في مؤسستك، ولا يمكن تغييره بعد إنشاء النهج.

   2. **وصف:** اختياري، ولكنه مفيد لتوفير معلومات حول النهج، مثل نوع السجل أو حمل العمل والمستخدمين المحددين في النهج والمدة.

   3. **المستخدمين:** حدد مستخدما واحدا أو أكثر لتطبيق النهج عليه. إذا تركت هذا المربع فارغا، فسيتم تطبيق النهج على جميع المستخدمين. إذا تركت **نوع السجل** فارغا، فيجب تحديد مستخدم.

   4. **نوع السجل:** نوع سجل التدقيق الذي ينطبق عليه النهج. إذا تركت هذه الخاصية فارغة، فيجب تحديد مستخدم في المربع **"المستخدمون** ". يمكنك تحديد نوع سجل واحد أو أنواع سجلات متعددة:
      - إذا قمت بتحديد نوع سجل واحد، يتم عرض الحقل **"الأنشطة"** ديناميكيا. يمكنك استخدام القائمة المنسدلة لتحديد أنشطة من نوع السجل المحدد لتطبيق النهج عليه. إذا لم تختر أنشطة معينة، فسيتم تطبيق النهج على كافة الأنشطة من نوع السجل المحدد.
      - إذا قمت بتحديد أنواع سجلات متعددة، فلن تتمكن من تحديد الأنشطة. سيتم تطبيق النهج على كافة أنشطة أنواع السجلات المحددة.

   5. **مده:** مقدار الوقت للاحتفاظ بسجلات التدقيق التي تفي بمعايير النهج.

   6. **الاولويه:** تحدد هذه القيمة الترتيب الذي تتم به معالجة نهج استبقاء سجل التدقيق في مؤسستك. تشير القيمة الأقل إلى أولوية أعلى. الأولويات الصالحة هي قيم رقمية بين **1** **و10000**. القيمة **1** هي الأولوية القصوى، والقيمة **10000** هي أقل أولوية. على سبيل المثال، نهج بقيمة **5** له الأولوية على نهج بقيمة **10**. كما هو موضح سابقا، فإن أي نهج استبقاء سجل تدقيق مخصص يأخذ الأولوية على النهج الافتراضي لمؤسستك.

5. انقر فوق **"حفظ"** لإنشاء نهج استبقاء سجل التدقيق الجديد.

يتم عرض النهج الجديد في القائمة على علامة تبويب **نهج استبقاء التدقيق** .

## <a name="manage-audit-log-retention-policies-in-the-compliance-portal"></a>إدارة نهج استبقاء سجل التدقيق في مدخل التوافق

يتم سرد نهج استبقاء سجل التدقيق في علامة تبويب **نهج استبقاء التدقيق** (تسمى أيضا *لوحة المعلومات*). يمكنك استخدام لوحة المعلومات لعرض نهج استبقاء التدقيق وتحريرها وحذفها.

### <a name="view-policies-in-the-dashboard"></a>عرض النهج في لوحة المعلومات

يتم سرد نهج استبقاء سجل التدقيق في لوحة المعلومات. تتمثل إحدى ميزات عرض النهج في لوحة المعلومات في أنه يمكنك النقر فوق عمود **الأولوية** لإدراج النهج في الأولوية التي يتم تطبيقها فيها. كما هو موضح سابقا، تشير القيمة الأقل إلى أولوية أعلى.

![عمود الأولوية في لوحة معلومات نهج استبقاء التدقيق.](../media/AuditLogRetentionDashboardPriority.png)

يمكنك أيضا تحديد نهج لعرض إعداداته على صفحة القائمة المنبثقة.

> [!NOTE]
> لا يتم عرض نهج استبقاء سجل التدقيق الافتراضي لمؤسستك في لوحة المعلومات.

### <a name="edit-policies-in-the-dashboard"></a>تحرير النهج في لوحة المعلومات

لتحرير نهج، حدده لعرض صفحة القائمة المنبثقة. يمكنك تعديل إعداد واحد أو أكثر ثم حفظ التغييرات.

> [!IMPORTANT]
>
> إذا كنت تستخدم **New-UnifiedAuditLogRetentionPolicy** cmdlet، فمن الممكن إنشاء نهج استبقاء سجل التدقيق لأنواع السجلات أو الأنشطة غير المتوفرة في أداة **إنشاء نهج استبقاء التدقيق** في لوحة المعلومات. في هذه الحالة، لن تتمكن من تحرير النهج (على سبيل المثال، تغيير مدة الاستبقاء أو إضافة أنشطة وإزالتها) من لوحة معلومات **نهج استبقاء التدقيق** . ستتمكن فقط من عرض النهج وحذفه في مركز الامتثال. لتحرير النهج، سيتعين عليك استخدام [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) cmdlet في Security & Compliance Center PowerShell.>
>
> **تلميح:** يتم عرض رسالة في أعلى صفحة القائمة المنبثقة للنهج التي يجب تحريرها باستخدام PowerShell.

### <a name="delete-policies-in-the-dashboard"></a>حذف النهج في لوحة المعلومات

لحذف نهج، انقر فوق الأيقونة **"حذف** ![حذف".](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) ثم تأكد من أنك تريد حذف النهج. تتم إزالة النهج من لوحة المعلومات، ولكن قد يستغرق الأمر ما يصل إلى 30 دقيقة لإزالة النهج من مؤسستك.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>إنشاء نهج استبقاء سجل التدقيق وإدارتها في PowerShell

يمكنك أيضا استخدام Security & Compliance Center PowerShell لإنشاء نهج استبقاء سجل التدقيق وإدارتها. أحد أسباب استخدام PowerShell هو إنشاء نهج لنوع سجل أو نشاط غير متوفر في واجهة المستخدم.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>إنشاء نهج استبقاء سجل التدقيق في PowerShell

اتبع هذه الخطوات لإنشاء نهج استبقاء سجل التدقيق في PowerShell:

1. [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. قم بتشغيل الأمر التالي لإنشاء نهج استبقاء سجل التدقيق:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   ينشئ هذا المثال نهج استبقاء سجل التدقيق المسمى "نهج التدقيق Microsoft Teams" باستخدام هذه الإعدادات:

   - وصف النهج.
   - الاحتفاظ بكافة أنشطة Microsoft Teams (كما تم تعريفها بواسطة معلمة *RecordType*).
   - يحتفظ بسجلات تدقيق Microsoft Teams لمدة 10 سنوات.
   - أولوية 100.

فيما يلي مثال آخر لإنشاء نهج استبقاء سجل التدقيق. يحتفظ هذا النهج بسجلات التدقيق لنشاط "المستخدم المسجل الدخول" لمدة ستة أشهر للمستخدم admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

لمزيد من المعلومات، راجع [New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>عرض النهج في PowerShell

استخدم [cmdlet Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) في Security & Compliance Center PowerShell لعرض نهج استبقاء سجل التدقيق.

فيما يلي نموذج أمر لعرض الإعدادات لكافة نهج استبقاء سجل التدقيق في مؤسستك. يقوم هذا الأمر بفرز النهج من الأولوية الأعلى إلى الأقل.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> لا يقوم **cmdlet Get-UnifiedAuditLogRetentionPolicy** بإرجاع نهج استبقاء سجل التدقيق الافتراضي لمؤسستك.

### <a name="edit-policies-in-powershell"></a>تحرير النهج في PowerShell

استخدم [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) cmdlet في Security & Compliance Center PowerShell لتحرير نهج استبقاء سجل تدقيق موجود.

### <a name="delete-policies-in-powershell"></a>حذف النهج في PowerShell

استخدم [cmdlet Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) في Security & Compliance Center PowerShell لحذف نهج استبقاء سجل التدقيق. قد يستغرق الأمر ما يصل إلى 30 دقيقة حتى تتم إزالة النهج من مؤسستك.

## <a name="more-information"></a>معلومات إضافية

كما ذكر سابقا، يتم الاحتفاظ بسجلات التدقيق للعمليات في Azure Active Directory، Exchange Online، SharePoint Online، OneDrive for Business، لمدة عام واحد بشكل افتراضي. يسرد الجدول التالي كافة أنواع السجلات (لكل من هذه الخدمات) المضمنة في نهج استبقاء سجل التدقيق الافتراضي. وهذا يعني أنه يتم الاحتفاظ بسجلات التدقيق لأي عملية باستخدام نوع السجل هذا لمدة عام واحد ما لم يكن نهج استبقاء سجل التدقيق المخصص له الأسبقية لنوع سجل معين أو عملية أو مستخدم معين. يتم عرض قيمة قائمة التعداد (التي يتم عرضها كقيمة لخاصية RecordType في سجل تدقيق) لكل نوع سجل بين أقواس.

<br>

****

|AzureActiveDirectory|Exchange |SharePoint أو OneDrive|
|---|---|---|
|AzureActiveDirectory (8)|ExchangeAdmin (1)|ComplianceDLPSharePoint (11)|
|AzureActiveDirectoryAccountLogon (9)|ExchangeItem (2)|ComplianceDLPSharePointClassification (33)|
|AzureActiveDirectoryStsLogon (15)|حملة (62)|Project (35)|
||ComplianceDLPExchange (13)|SharePoint (4)|
||ComplianceSupervisionExchange (68)|SharePointCommentOperation (37)|
||CustomerKeyServiceEncryption (69)|SharePointContentTypeOperation (55)|
||ExchangeAggregatedOperation (19)|SharePointFieldOperation (56)|
||ExchangeItemAggregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
