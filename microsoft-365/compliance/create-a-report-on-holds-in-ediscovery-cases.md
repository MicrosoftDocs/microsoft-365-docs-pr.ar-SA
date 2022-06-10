---
title: استخدام برنامج نصي لإنشاء تقرير يحتوي على eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 05/10/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: cca08d26-6fbf-4b2c-b102-b226e4cd7381
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية إنشاء تقرير يحتوي على معلومات حول كافة قوائم الاحتجاز المقترنة بحالات eDiscovery.
ms.openlocfilehash: 9db08335ff023172092e7bf8bada7a3976956d29
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016999"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>استخدام برنامج نصي لإنشاء تقرير حول قوائم الاحتجاز في حالات eDiscovery

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يتيح البرنامج النصي في هذه المقالة لمسؤولي eDiscovery ومديري eDiscovery إنشاء تقرير يحتوي على معلومات حول جميع قوائم الاحتجاز المقترنة بحالات eDiscovery (قياسي) وeDiscovery (Premium) في مدخل الامتثال ل Microsoft Purview. يحتوي التقرير على معلومات مثل اسم الحالة المقترنة باحتجاز، ومواقع المحتوى الموضوعة قيد الاحتجاز، وما إذا كان الاحتجاز مستندا إلى الاستعلام. إذا كانت هناك حالات لا تحتوي على أي قوائم احتجاز، فسينشئ البرنامج النصي تقريرا إضافيا بقائمة من الحالات دون احتجاز.

راجع القسم ["مزيد من المعلومات](#more-information) " للحصول على وصف مفصل للمعلومات المضمنة في التقرير.

## <a name="admin-requirements-and-script-information"></a>متطلبات المسؤول ومعلومات البرنامج النصي

- لإنشاء تقرير حول جميع حالات eDiscovery في مؤسستك، يجب أن تكون مسؤول eDiscovery في مؤسستك. إذا كنت مدير eDiscovery، فسيتضمن التقرير معلومات حول الحالات التي يمكنك الوصول إليها فقط. لمزيد من المعلومات حول أذونات eDiscovery، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md).

- يحتوي البرنامج النصي في هذه المقالة على الحد الأدنى من معالجة الأخطاء. الغرض الأساسي هو إنشاء تقرير بسرعة حول قوائم الاحتجاز المقترنة بحالات eDiscovery في مؤسستك.

- لا يتم دعم نماذج البرامج النصية المتوفرة في هذا الموضوع ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نماذج البرامج النصية AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نماذج البرامج النصية والوثائق معك. لن تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناتجة عن استخدام نماذج البرامج النصية أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-connect-to-security--compliance-powershell"></a>الخطوة 1: الاتصال إلى Security & Compliance PowerShell

الخطوة الأولى هي الاتصال ب Security & Compliance PowerShell لمؤسستك. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>الخطوة 2: تشغيل البرنامج النصي للإبلاغ عن عمليات الاحتجاز المقترنة بحالات eDiscovery

بعد الاتصال ب Security & Compliance PowerShell، فإن الخطوة التالية هي إنشاء وتشغيل البرنامج النصي الذي يجمع معلومات حول حالات eDiscovery في مؤسستك.

1. احفظ النص التالي في ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، CaseHoldsReport.ps1.

   ```powershell
   #script begin
   " "
   write-host "***********************************************"
   write-host "   Security & Compliance Center   " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "        eDiscovery cases - Holds report         " -foregroundColor yellow -backgroundcolor darkgreen
   write-host "***********************************************"
   " "
   #prompt users to specify a path to store the output files
   $time=get-date
   $Path = Read-Host 'Enter a folder path to save the report to a .csv file (filename is created automatically)'
   $outputpath=$Path+'\'+'CaseHoldsReport'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   $noholdsfilepath=$Path+'\'+'CaseswithNoHolds'+' '+$time.day+'-'+$time.month+'-'+$time.year+' '+$time.hour+'.'+$time.minute+'.csv'
   #add case details to the csv file
   function add-tocasereport{
   Param([string]$casename,
   [String]$casetype,
   [String]$casestatus,
   [datetime]$casecreatedtime,
   [string]$casemembers,
   [datetime]$caseClosedDateTime,
   [string]$caseclosedby,
   [string]$holdname,
   [String]$Holdenabled,
   [string]$holdcreatedby,
   [string]$holdlastmodifiedby,
   [string]$ExchangeLocation,
   [string]$sharePointlocation,
   [string]$ContentMatchQuery,
   [datetime]$holdcreatedtime,
   [datetime]$holdchangedtime
   )
   $addRow = New-Object PSObject
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case name" -Value $casename
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case type" -Value $casetype
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case status" -Value $casestatus
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case members" -Value $casemembers
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case created time" -Value $casecreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed time" -Value $caseClosedDateTime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Case closed by" -Value $caseclosedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold name" -Value $holdname
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold enabled" -Value $Holdenabled
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created by" -Value $holdcreatedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold last changed by" -Value $holdlastmodifiedby
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Exchange locations" -Value  $ExchangeLocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "SharePoint locations" -Value $sharePointlocation
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold query" -Value $ContentMatchQuery
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold created time (UTC)" -Value $holdcreatedtime
   Add-Member -InputObject $addRow -MemberType NoteProperty -Name "Hold changed time (UTC)" -Value $holdchangedtime
   $allholdreport = $addRow | Select-Object "Case name","Case type","Case status","Hold name","Hold enabled","Case members", "Case created time","Case closed time","Case closed by","Exchange locations","SharePoint locations","Hold query","Hold created by","Hold created time (UTC)","Hold last changed by","Hold changed time (UTC)"
   $allholdreport | export-csv -path $outputPath -notypeinfo -append -Encoding ascii
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Standard) cases and holds..."
   " "
   $edc =Get-ComplianceCase -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casestatus $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }
   #get information on the cases and pass values to the case report function
   " "
   write-host "Gathering a list of eDiscovery (Premium) cases and holds..."
   " "
   $edc =Get-ComplianceCase -CaseType Advanced -ErrorAction SilentlyContinue
   foreach($cc in $edc)
   {
   write-host "Working on case :" $cc.name
   if($cc.status -eq 'Closed')
   {
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   add-tocasereport -casename $cc.name -casestatus -casetype $cc.casetype $cc.Status -caseclosedby $cc.closedby -caseClosedDateTime $cc.ClosedDateTime -casemembers $cmembers
   }
   else{
   $cmembers = ((Get-ComplianceCaseMember -Case $cc.name).windowsLiveID)-join ';'
   $policies = Get-CaseHoldPolicy -Case $cc.Name | %{ Get-CaseHoldPolicy $_.Name -Case $_.CaseId -DistributionDetail}
   if ($policies -ne $NULL)
   {
   foreach ($policy in $policies)
   {
   $rule=Get-CaseHoldRule -Policy $policy.name
   add-tocasereport -casename $cc.name -casetype $cc.casetype -casemembers $cmembers -casestatus $cc.Status -casecreatedtime $cc.CreatedDateTime -holdname $policy.name -holdenabled $policy.enabled -holdcreatedby $policy.CreatedBy -holdlastmodifiedby $policy.LastModifiedBy -ExchangeLocation (($policy.exchangelocation.name)-join ';') -SharePointLocation (($policy.sharePointlocation.name)-join ';') -ContentMatchQuery $rule.ContentMatchQuery -holdcreatedtime $policy.WhenCreatedUTC -holdchangedtime $policy.WhenChangedUTC
   }
   }
   else{
   write-host "No hold policies found in case:" $cc.name -foregroundColor 'Yellow'
   " "
   [string]$cc.name | out-file -filepath $noholdsfilepath -append
   }
   }
   }

   " "
   Write-host "Script complete! Report files saved to this folder: '$Path'"
   " "
   #script end
   ```

2. في جلسة Windows PowerShell التي تم فتحها في الخطوة 1، انتقل إلى المجلد حيث قمت بحفظ البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   سيطالب البرنامج النصي بالمجلد الهدف لحفظ التقرير فيه.

4. اكتب اسم المسار الكامل للمجلد لحفظ التقرير فيه، ثم اضغط على **مفتاح الإدخال Enter**.

   > [!TIP]
   > لحفظ التقرير في المجلد نفسه الذي يوجد فيه البرنامج النصي، اكتب نقطة (.") عند مطالبتك بمجلد هدف. لحفظ التقرير في مجلد فرعي في المجلد حيث يوجد البرنامج النصي، ما عليك سوى كتابة اسم المجلد الفرعي.

   يبدأ البرنامج النصي في جمع معلومات حول جميع حالات eDiscovery في مؤسستك. لا تقم بالوصول إلى ملف التقرير أثناء تشغيل البرنامج النصي. بعد اكتمال البرنامج النصي، يتم عرض رسالة تأكيد في جلسة Windows PowerShell. بعد عرض هذه الرسالة، يمكنك الوصول إلى التقرير في المجلد الذي حددته في الخطوة 4. اسم الملف للتقرير هو `CaseHoldsReport<DateTimeStamp>.csv`.

   بالإضافة إلى ذلك، يقوم البرنامج النصي أيضا بإنشاء تقرير بقائمة من الحالات التي لا تحتوي على أي قوائم احتجاز. اسم الملف لهذا التقرير هو `CaseswithNoHolds<DateTimeStamp>.csv`.

   فيما يلي مثال على تشغيل البرنامج النصي CaseHoldsReport.ps1.

   ![الإخراج بعد تشغيل البرنامج النصي CaseHoldsReport.ps1.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>معلومات إضافية

تحتوي الحالة على تقرير تم إنشاؤه عند تشغيل البرنامج النصي في هذه المقالة يحتوي على المعلومات التالية حول كل احتجاز. كما هو موضح سابقا، يجب أن تكون مسؤول eDiscovery لإرجاع معلومات لكافة عمليات الاحتجاز في مؤسستك. لمزيد من المعلومات حول حالات احتجاز [الحالة، راجع حالات eDiscovery](./get-started-core-ediscovery.md).

- اسم قائمة الاحتجاز واسم حالة eDiscovery المقترنة بها.

- ما إذا كان الاحتجاز مقترنا بحالة eDiscovery (قياسي) أو eDiscovery (Premium).

- ما إذا كانت حالة eDiscovery نشطة أو مغلقة أم لا.

- ما إذا كانت قائمة الاحتجاز ممكنة أو معطلة أم لا.

- أعضاء حالة eDiscovery المقترنة بها. يمكن لأعضاء الحالة عرض حالة أو إدارتها، اعتمادا على أذونات eDiscovery التي تم تعيينها لهم.

- الوقت والتاريخ الذي تم فيه إنشاء الحالة.

- إذا تم إغلاق حالة ما، فإن الشخص الذي أغلقها ووقت وتاريخ إغلاقها.

- علب بريد Exchange ومواقع SharePoint الموجودة قيد الاحتجاز.

- إذا كانت قائمة الاحتجاز مستندة إلى الاستعلام، فإن بناء جملة الاستعلام.

- وقت وتاريخ إنشاء قائمة الاحتجاز والشخص الذي أنشأها.

- الوقت والتاريخ الذي تم فيه تغيير قائمة الاحتجاز الأخيرة والشخص الذي قام بتغييرها.
