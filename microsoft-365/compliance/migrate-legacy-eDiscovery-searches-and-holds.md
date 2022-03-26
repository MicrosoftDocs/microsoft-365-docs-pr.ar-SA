---
title: ترحيل عمليات البحث القديمة في eDiscovery وتحملها إلى مركز التوافق في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
ms.openlocfilehash: fe3f65e2545b71f8cfbaea76dfd34fd2720a790f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63567201"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-microsoft-365-compliance-center"></a>ترحيل عمليات البحث القديمة في eDiscovery وتحملها إلى مركز التوافق في Microsoft 365

يوفر مركز التوافق في Microsoft 365 تجربة محسنة لاستخدام eDiscovery، بما في ذلك: وثوقية أعلى وأداء أفضل والعديد من الميزات المصممة لمسيرات سير عمل eDiscovery بما في ذلك الحالات لتنظيم المحتوى حسب المادة ومراجعة المجموعات لمراجعة المحتوى والتحليلات للمساعدة في نسخ البيانات لمراجعتها مثل تجميع التكرار تقريبا، وترابط البريد الإلكتروني، وتحليل المحتوى، والترميز المتوقع.

لمساعدة العملاء على الاستفادة من الوظائف الجديدة والمحسنة، توفر هذه المقالة إرشادات أساسية حول كيفية ترحيل عمليات البحث في eDiscovery في In-Place والمحتجزة من <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز</a> إدارة Exchange إلى مركز التوافق في Microsoft 365.

> [!NOTE]
> نظرا إلى وجود العديد من السيناريوهات المختلفة، توفر هذه المقالة إرشادات عامة للانتقال إلى عمليات البحث وتحمل حالة eDiscovery أساسية في مركز التوافق في Microsoft 365. لا يتطلب استخدام حالات eDiscovery دائما، ولكنها تضيف طبقة أمان إضافية من خلال السماح لك بتعيين أذونات للتحكم في من لديه حق الوصول إلى حالات eDiscovery في مؤسستك.

## <a name="before-you-begin"></a>قبل البدء

- يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365 لتشغيل أوامر PowerShell الموضحة في هذه المقالة. يجب أن تكون أيضا عضوا في مجموعة دور إدارة الاكتشافات في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange الإدارة</a>.

- توفر هذه المقالة إرشادات حول كيفية إنشاء مع الاستمرار eDiscovery. سيتم تطبيق نهج الاستمرار على علب البريد من خلال عملية غير متزامنة. عند إنشاء مع الاستمرار eDiscovery، يجب إنشاء كل من CaseHoldPolicy و CaseHoldRule، وإلا لن يتم إنشاء الاستمرار ولن يتم وضع مواقع المحتوى قيد الانتظار.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-center-powershell"></a>الخطوة 1: الاتصال Exchange Online PowerShell والأمان في مركز & PowerShell

الخطوة الأولى هي الاتصال Exchange Online PowerShell والأمان & Compliance Center PowerShell. يمكنك نسخ البرنامج النصي التالي ولصقه في نافذة PowerShell ثم تشغيله. وستطلب منك بيانات اعتماد المؤسسة التي تريد الاتصال بها. 

```powershell
$UserCredential = Get-Credential
$sccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $sccSession -DisableNameChecking
$exoSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $exoSession -AllowClobber -DisableNameChecking
```

يجب تشغيل الأوامر في الخطوات التالية في جلسة PowerShell هذه.

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>الخطوة 2: الحصول على قائمة بعمليات In-Place eDiscovery باستخدام Get-MailboxSearch

بعد المصادقة، يمكنك الحصول على قائمة بعمليات البحث In-Place eDiscovery عن طريق تشغيل **الأمر cmdlet البحث في Get-MailboxSearch** . انسخ الأمر التالي واللصق فيه في PowerShell ثم قم بتشغيله. سيتم سرد قائمة عمليات البحث مع أسمائها ووضع أي In-Place عمليات بحث.

```powershell
Get-MailboxSearch
```

سيتشابه إخراج cmdlet مع ما يلي:

![مثال PowerShell Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>الخطوة 3: الحصول على معلومات حول عمليات In-Place eDiscovery وعمليات In-Place التي تريد ترحيلها

مرة أخرى، سوف تستخدم **الأمر cmdlet Get-MailboxSearch** ، ولكن هذه المرة للحصول على خصائص البحث. يمكنك تخزين هذه الخصائص في متغير لاستخدامه لاحقا. يخزن المثال التالي نتائج **الأمر cmdlet Get-MailboxSearch** في متغير ثم يعرض خصائص البحث.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | FL
```

سيتشابه إخراج هذين الأمرين مع ما يلي:

![مثال على إخراج PowerShell من استخدام Get-MailboxSearch بحث فردي.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> مدة مدة In-Place الانتظار في هذا المثال غير محدودة (*ItemHoldPeriod: Unlimited*). هذا الأمر نموذجي لسيناريوهات eDiscovery وسيناريوهات التحقيق القانوني. إذا كانت مدة الاحتجاز ذات قيمة مختلفة عن القيمة غير المتوقعة، فمن المرجح أن السبب هو أنه يتم استخدام الاحتجاز للاحتفاظ بالمحتوى في سيناريو استبقاء. بدلا من استخدام أمر cmdlets eDiscovery في مركز التوافق ل الأمان & PowerShell لسيناريوهات الاستبقاء، نوصي باستخدام [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) و [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) للاحتفاظ بالمحتوى. ستكون نتيجة استخدام هذه cmdlets مماثلة لاستخدام **New-CaseHoldPolicy** و **New-CaseHoldRule**، ولكن يمكنك تحديد فترة استبقاء و إجراء استبقاء، مثل حذف المحتوى بعد انتهاء فترة الاستبقاء. كما أن استخدام cmdlets الاستبقاء لا يتطلب إقران الاحتفاظات مع حالة eDiscovery.

## <a name="step-4-create-a-case-in-the-microsoft-365-compliance-center"></a>الخطوة 4: إنشاء حالة في Microsoft 365 التوافق

لإنشاء مع الاستمرار eDiscovery، يجب إنشاء حالة eDiscovery لاقران الاستمرار بها. ينشئ المثال التالي حالة eDiscovery باستخدام اسم من اختيارك. سنقوم بتخزين خصائص الحالة الجديدة في متغير لاستخدامها لاحقا. يمكنك عرض هذه الخصائص عن طريق تشغيل `$case | FL` الأمر بعد إنشاء الحالة.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```
![مثال لتشغيل الأمر New-ComplianceCase.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>الخطوة 5: إنشاء الاستمرار في eDiscovery

بعد إنشاء الحالة، يمكنك إنشاء فترة الانتظار وإقرانها مع الحالة التي أنشأتها في الخطوة السابقة. من المهم تذكر أنه يجب عليك إنشاء كل من نهج الاستمرار في حالة القضيتين ولقاعدة الاستمرار في حالة القضيتين. إذا لم يتم إنشاء قاعدة الاستمرار في حالة القضيه بعد إنشاء نهج الاستمرار في حالة القضيه، فلن يتم إنشاء eDiscovery ولن يتم وضع أي محتوى قيد الانتظار.

قم بتشغيل الأوامر التالية لإعادة إنشاء الاستمرار eDiscovery الذي تريد ترحيله. تستخدم هذه الأمثلة الخصائص من In-Place Hold من الخطوة 3 التي تريد ترحيلها. ينشئ الأمر الأول نهج الاستمرار حالة جديدة ويحفظ الخصائص في متغير. ينشئ الأمر الثاني قاعدة الاستمرار في حالة التناظر.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![مثال على استخدام Cmdlets NewCaseHoldPolicy و NewCaseHoldRule.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>الخطوة 6: التحقق من الاستمرار في eDiscovery

للتأكد من عدم وجود أي مشاكل في إنشاء وضع الانتظار، من الجيد التحقق من نجاح حالة توزيع الانتظار. يعني التوزيع أنه قد تم تطبيق فترة الانتظار على كل مواقع المحتوى المحددة في *معلمة ExchangeLocation* في الخطوة السابقة. للقيام بذلك، يمكنك تشغيل **الأمر Cmdlet Get-CaseHoldPolicy** . نظرا لعدم تحديث الخصائص المحفوظة  في $policy المتغير الذي أنشأته في الخطوة السابقة تلقائيا في المتغير، يجب إعادة تشغيل أمر cmdlet للتحقق من نجاح التوزيع. قد يستغرق توزيع نهج حالة الحالة بنجاح ما بين 5 دقائق و24 ساعة.

تشغيل الأمر التالي للتحقق من توزيع الاستمرار في eDiscovery بنجاح.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

تشير قيمة **النجاح** ل خاصية *DistributionStatus* إلى أنه تم وضع الانتظار بنجاح على مواقع المحتوى. إذا لم يكن التوزيع مكتملا بعد، يتم عرض قيمة **معلق** .

![مثال على Get-CaseHoldPolicy PowerShell.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>الخطوة 7: إنشاء البحث

الخطوة الأخيرة هي إعادة إنشاء البحث الذي حددته في الخطوة 3 وإقرانه مع الحالة. بعد إنشاء البحث، يمكنك تشغيله باستخدام **الأمر cmdlet Start-ComplianceSearch** أو تشغيله في وقت لاحق.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![مثال على New-ComplianceSearch PowerShell.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-microsoft-365-compliance-center"></a>الخطوة 8: التحقق من الحالة، مع الاستمرار، والبحث في مركز التوافق في Microsoft 365

للتأكد من إعداد كل شيء بشكل صحيح، انتقل إلى مركز التوافق في Microsoft 365 في [https://compliance.microsoft.com](https://compliance.microsoft.com)، وانقر فوق **eDiscovery > Core**.

![Microsoft 365 مركز التوافق eDiscovery.](../media/MigrateLegacyeDiscovery7.png)

يتم سرد الحالة التي قمت بإنشاءها في الخطوة 3 على الصفحة **Core eDiscovery** . افتح الحالة ثم لاحظ وضع علامة الانتظار التي أنشأتها في الخطوة 4 في **المدرجة ضمن علامة** التبويب الاستمرار. يمكنك تحديد فترة الانتظار لرؤية التفاصيل على صفحة النشرة flyout، بما في ذلك عدد علب البريد التي تم تطبيق الاستمرار عليها وعلى حالة التوزيع.

![يحتفظ eDiscovery في مركز التوافق في Microsoft 365.](../media/MigrateLegacyeDiscovery8.png)

يتم إدراج البحث الذي أنشأته في الخطوة 7 **ضمن علامة التبويب** عمليات البحث في حالة.

![البحث عن حالة eDiscovery في مركز التوافق في Microsoft 365.](../media/MigrateLegacyeDiscovery9.png)

إذا قمت بترحيل In-Place eDiscovery دون إقرانه مع حالة eDiscovery، سيتم إدراجه في صفحة البحث في المحتوى في مركز التوافق في Microsoft 365.

## <a name="more-information"></a>معلومات إضافية

- لمزيد من المعلومات حول In-Place eDiscovery & في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange،</a> راجع:
  
  - [eDiscovery في مكان](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [الاحتجاز المانع والدعاوى القضائية](/exchange/security-and-compliance/in-place-and-litigation-holds)

- لمزيد من المعلومات حول PowerShell cmdlets المستخدمة في المقالة، راجع:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)
  
  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)
  
  - [New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
  
  - [البحث عن التوافق الجديد](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- لمزيد من المعلومات حول مركز التوافق في Microsoft 365، راجع [نظرة عامة على مركز التوافق في Microsoft 365](microsoft-365-compliance-center.md).