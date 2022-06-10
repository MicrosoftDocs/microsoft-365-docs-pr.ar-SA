---
title: ترحيل عمليات بحث eDiscovery القديمة وحتفظ بها إلى مدخل الامتثال ل Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: 3b80db06faea9c76c7df671468b94fc11f0c63df
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010077"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-compliance-portal"></a>ترحيل عمليات بحث eDiscovery القديمة وحتفظ بها إلى مدخل التوافق

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يوفر مدخل توافق Microsoft Purview تجربة محسنة لاستخدام eDiscovery، بما في ذلك: الموثوقية الأعلى والأداء الأفضل والعديد من الميزات المصممة لسير عمل eDiscovery بما في ذلك الحالات لتنظيم المحتوى حسب المسألة ومجموعات المراجعة لمراجعة المحتوى والتحليلات للمساعدة في احصاء البيانات للمراجعة مثل التجميع شبه المكرر ومؤشرات ترابط البريد الإلكتروني وتحليل النسق والترميز التنبؤي.

لمساعدة العملاء على الاستفادة من الوظائف الجديدة والمحسنة، توفر هذه المقالة إرشادات أساسية حول كيفية ترحيل عمليات البحث In-Place eDiscovery وسحبها من <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> إلى مدخل التوافق.

> [!NOTE]
> نظرا لوجود العديد من السيناريوهات المختلفة، توفر هذه المقالة إرشادات عامة لانتقال عمليات البحث والحفظ إلى حالة eDiscovery (قياسي) في مدخل التوافق. استخدام حالات eDiscovery ليست مطلوبة دائما، ولكنها تضيف طبقة إضافية من الأمان من خلال السماح لك بتعيين أذونات للتحكم في من لديه حق الوصول إلى حالات eDiscovery في مؤسستك.

## <a name="before-you-begin"></a>قبل البدء

- تحتاج إلى تثبيت الوحدة النمطية Exchange Online V2. للحصول على الإرشادات، راجع [تثبيت وحدة EXO V2 وصيانتها](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

- يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل التوافق لتشغيل أوامر PowerShell الموضحة في هذه المقالة. يجب أن تكون أيضا عضوا في مجموعة دور إدارة الاكتشافات في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>.

- توفر هذه المقالة إرشادات حول كيفية إنشاء قائمة احتجاز eDiscovery. سيتم تطبيق نهج الاحتجاز على علب البريد من خلال عملية غير متزامنة. عند إنشاء قائمة احتجاز eDiscovery، يجب إنشاء كل من CaseHoldPolicy و CaseHoldRule، وإلا فلن يتم إنشاء قائمة الاحتجاز ولن يتم وضع مواقع المحتوى قيد الاحتجاز.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-powershell"></a>الخطوة 1: الاتصال Exchange Online PowerShell والأمان & Compliance PowerShell

الخطوة الأولى هي الاتصال Exchange Online PowerShell والأمان & Compliance PowerShell في نفس نافذة PowerShell. يمكنك نسخ الأوامر التالية ولصقها في نافذة PowerShell ثم تشغيلها. ستتم مطالبتك ببيانات الاعتماد.

```powershell
Connect-IPPSSession
Connect-ExchangeOnline -UseRPSSession
```

للحصول على إرشادات مفصلة، راجع [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>الخطوة 2: الحصول على قائمة بعمليات البحث In-Place eDiscovery باستخدام Get-MailboxSearch

بعد الاتصال، يمكنك الحصول على قائمة In-Place عمليات البحث في eDiscovery عن طريق تشغيل **Get-MailboxSearch** cmdlet. انسخ الأمر التالي والصقه في نافذة PowerShell ثم قم بتشغيله.

```powershell
Get-MailboxSearch
```

سيتم سرد قائمة عمليات البحث بأسماء الأشخاص وحالة أي In-Place عمليات احتجاز.

سيكون إخراج cmdlet مشابها للآتي:

![مثال على PowerShell Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>الخطوة 3: الحصول على معلومات حول عمليات البحث في eDiscovery In-Place وعمليات In-Place التي تريد ترحيلها

مرة أخرى سوف تستخدم **Get-MailboxSearch** cmdlet، ولكن هذه المرة للحصول على خصائص البحث. يمكنك تخزين هذه الخصائص في متغير لاستخدامها لاحقا. يخزن المثال التالي نتائج **Get-MailboxSearch** cmdlet في متغير ثم يعرض خصائص البحث.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | Format-List
```

سيكون إخراج هذين الأمرين مشابها لما يلي:

![مثال على إخراج PowerShell من استخدام Get-MailboxSearch للبحث الفردي.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> مدة احتجاز In-Place في هذا المثال غير محددة (*ItemHoldPeriod: غير محدودة*). هذا نموذجي لسيناريوهات eDiscovery والتحقيق القانوني. إذا كانت مدة الاحتجاز مختلفة عن قيمة غير محددة، فمن المحتمل أن يكون السبب هو استخدام قائمة الاحتجاز للاحتفاظ بالمحتوى في سيناريو استبقاء. بدلا من استخدام أوامر cmdlets eDiscovery في Security & Compliance PowerShell لسيناريوهات الاستبقاء، نوصي باستخدام [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) و [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) للاحتفاظ بالمحتوى. ستكون نتيجة استخدام أوامر cmdlets هذه مشابهة لاستخدام **New-CaseHoldPolicy** و **New-CaseHoldRule**، ولكن ستتمكن من تحديد فترة استبقاء وإجراء استبقاء، مثل حذف المحتوى بعد انتهاء فترة الاستبقاء. أيضا، لا يتطلب استخدام أوامر cmdlets الاستبقاء إقران قوائم الاحتفاظ بحالة eDiscovery.

## <a name="step-4-create-a-case-in-the-microsoft-purview-compliance-portal"></a>الخطوة 4: إنشاء حالة في مدخل توافق Microsoft Purview

لإنشاء قائمة احتجاز eDiscovery، يجب عليك إنشاء حالة eDiscovery لإقران قائمة الاحتجاز بها. ينشئ المثال التالي حالة eDiscovery باستخدام اسم من اختيارك. سنقوم بتخزين خصائص الحالة الجديدة في متغير للاستخدام لاحقا. يمكنك عرض هذه الخصائص عن طريق تشغيل `$case | FL` الأمر بعد إنشاء الحالة.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```

![مثال على تشغيل الأمر New-ComplianceCase.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>الخطوة 5: إنشاء قائمة احتجاز eDiscovery

بعد إنشاء الحالة، يمكنك إنشاء قائمة الاحتجاز وإقرانها بالحالة التي قمت بإنشائها في الخطوة السابقة. من المهم أن تتذكر أنه يجب عليك إنشاء كل من نهج احتجاز الحالة وقاعدة احتجاز الحالة. إذا لم يتم إنشاء قاعدة احتجاز الحالة بعد إنشاء نهج احتجاز الحالة، فلن يتم إنشاء احتجاز eDiscovery ولن يتم وضع أي محتوى قيد الاحتجاز.

قم بتشغيل الأوامر التالية لإعادة إنشاء قائمة احتجاز eDiscovery التي تريد ترحيلها. تستخدم هذه الأمثلة الخصائص من In-Place قائمة الاحتجاز من الخطوة 3 التي تريد ترحيلها. ينشئ الأمر الأول نهج احتجاز حالة جديدة ويحفظ الخصائص إلى متغير. ينشئ الأمر الثاني قاعدة احتجاز الحالة المقابلة.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![مثال على استخدام NewCaseHoldPolicy و NewCaseHoldRule cmdlets.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>الخطوة 6: التحقق من قائمة احتجاز eDiscovery

للتأكد من عدم وجود مشاكل في إنشاء قائمة الاحتجاز، من الجيد التحقق من نجاح حالة توزيع قائمة الاحتجاز. يعني التوزيع أنه تم تطبيق قائمة الاحتجاز على كافة مواقع المحتوى المحددة في معلمة *ExchangeLocation* في الخطوة السابقة. للقيام بذلك، يمكنك تشغيل **الأمر cmdlet Get-CaseHoldPolicy** . نظرا لعدم تحديث الخصائص المحفوظة في متغير *$policy* الذي قمت بإنشائه في الخطوة السابقة تلقائيا في المتغير، تحتاج إلى إعادة تشغيل cmdlet للتحقق من نجاح التوزيع. قد يستغرق توزيع نهج احتجاز الحالات بنجاح ما بين 5 دقائق و24 ساعة.

قم بتشغيل الأمر التالي للتحقق من توزيع قائمة احتجاز eDiscovery بنجاح.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

تشير قيمة **Success** *لخاصية DistributionStatus* إلى أنه تم وضع قائمة الاحتجاز بنجاح على مواقع المحتوى. إذا لم يكتمل التوزيع بعد، يتم عرض قيمة **Pending** .

![مثال Get-CaseHoldPolicy PowerShell.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>الخطوة 7: إنشاء البحث

الخطوة الأخيرة هي إعادة إنشاء البحث الذي حددته في الخطوة 3 وإقرانه بالحالة. بعد إنشاء البحث، يمكنك تشغيله باستخدام **Start-ComplianceSearch** cmdlet أو تشغيله في وقت لاحق.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![مثال New-ComplianceSearch PowerShell.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-compliance-portal"></a>الخطوة 8: التحقق من الحالة، والاحتفاظ بها، والبحث في مدخل التوافق

للتأكد من إعداد كل شيء بشكل صحيح، انتقل إلى مدخل التوافق في [https://compliance.microsoft.com](https://compliance.microsoft.com)، وانقر فوق **eDiscovery > Core**.

![Microsoft Purview compliance portal eDiscovery.](../media/MigrateLegacyeDiscovery7.png)

يتم سرد الحالة التي قمت بإنشائها في الخطوة 3 في صفحة **eDiscovery (Standard** ). افتح الحالة ثم لاحظ قائمة الاحتجاز التي قمت بإنشائها في الخطوة 4 في القائمة ضمن علامة التبويب **"احتجاز** ". يمكنك تحديد قائمة الاحتجاز للاطلاع على التفاصيل في صفحة القائمة المنبثقة، بما في ذلك عدد علب البريد التي يتم تطبيق الاحتجاز عليها وحالة التوزيع.

![يحتفظ eDiscovery في مدخل التوافق.](../media/MigrateLegacyeDiscovery8.png)

يتم سرد البحث الذي قمت بإنشائه في الخطوة 7 في علامة التبويب **"عمليات البحث"** في الحالة.

![البحث في حالة eDiscovery في مدخل التوافق.](../media/MigrateLegacyeDiscovery9.png)

إذا قمت بترحيل بحث In-Place eDiscovery ولكنك لم تقم بإقرانه بحالة eDiscovery، فسيتم إدراجه في صفحة البحث في المحتوى في مدخل التوافق.

## <a name="more-information"></a>معلومات إضافية

- لمزيد من المعلومات حول In-Place eDiscovery & في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>، راجع:

  - [eDiscovery موضعي](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [الاحتجاز الموضعي والتقاضي](/exchange/security-and-compliance/in-place-and-litigation-holds)

- لمزيد من المعلومات حول أوامر PowerShell cmdlets المستخدمة في المقالة، راجع:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)

  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)

  - [New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)

  - [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- لمزيد من المعلومات حول مدخل التوافق، راجع [نظرة عامة على مدخل توافق Microsoft Purview](microsoft-365-compliance-center.md).