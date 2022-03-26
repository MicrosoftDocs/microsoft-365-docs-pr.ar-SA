---
title: استخدام برنامج نصي لإنشاء تقرير يتولى eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 9/11/2017
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
description: تعرف على كيفية إنشاء تقرير يحتوي على معلومات حول كل حالات التحميس المقترنة ب eDiscovery.
ms.openlocfilehash: 568d4fa351879d271004d0f0749881f3de4b4a49
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567129"
---
# <a name="use-a-script-to-create-a-report-on-holds-in-ediscovery-cases"></a>استخدام برنامج نصي لإنشاء تقرير حول حالات التحميس في حالات eDiscovery

يتيح البرنامج النصي في هذه المقالة لمسؤولي eDiscovery ومديري eDiscovery إنشاء تقرير يحتوي على معلومات حول كل حالات التحميس المقترنة بالتقارير الأساسية Advanced eDiscovery في مركز التوافق في Microsoft 365. يحتوي التقرير على معلومات مثل اسم حالة الانتظار المقترنة به، ومواقع المحتوى التي تم وضعها قيد الانتظار، وما إذا كانت قائمة الانتظار مستندة إلى الاستعلام. إذا كانت هناك حالات لا تتضمن أي من حالات الانتظار، فإن البرنامج النصي سينشئ تقريرا إضافيا مع قائمة من الحالات بدون أي حالات تم فيها الانتظار.

راجع القسم [مزيد من المعلومات](#more-information) للحصول على وصف مفصل للمعلومات المضمنة في التقرير.

## <a name="admin-requirements-and-script-information"></a>متطلبات المسؤول ومعلومات البرنامج النصي

- لإنشاء تقرير حول كل حالات eDiscovery في مؤسستك، يجب أن تكون مسؤول eDiscovery في مؤسستك. إذا كنت مدير eDiscovery، سيتضمن التقرير فقط معلومات حول الحالات التي يمكنك الوصول إليها. لمزيد من المعلومات حول أذونات eDiscovery، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md).

- البرنامج النصي في هذه المقالة به الحد الأدنى من معالجة الأخطاء. الغرض الأساسي هو إنشاء تقرير بسرعة حول حالات التحميس المقترنة ب eDiscovery في مؤسستك.

- البرامج النصية العينة المتوفرة في هذا الموضوع غير معتمدة ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرامج النصية العينة AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام البرامج النصية والوثائق العينة أو أدائها معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها المسؤولية عن أي أضرار أيا كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام البرامج النصية أو الوثائق العينة أو عدم القدرة على استخدامها،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.

## <a name="step-1-connect-to-security--compliance-center-powershell"></a>الخطوة 1: الاتصال إلى مركز & التوافق PowerShell

الخطوة الأولى هي الاتصال بمركز & التوافق PowerShell لمنظمتك. للحصول على إرشادات مفصلة خطوة بخطوة، راجع الاتصال [إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-2-run-the-script-to-report-on-holds-associated-with-ediscovery-cases"></a>الخطوة 2: تشغيل البرنامج النصي للتقرير حول حالات التحميس المقترنة ب eDiscovery

بعد الاتصال بمركز التوافق & PowerShell، فإن الخطوة التالية هي إنشاء البرنامج النصي الذي يجمع معلومات حول حالات eDiscovery في مؤسستك وتشغيله.

1. احفظ النص التالي في Windows PowerShell نصي باستخدام لاحقة اسم الملف .ps1، على سبيل المثال، CaseHoldsReport.ps1.

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
   write-host "Gathering a list of Core eDiscovery cases and holds..."
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
   write-host "Gathering a list of Advanced eDiscovery cases and holds..."
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

2. في جلسة Windows PowerShell التي تم فتحها في الخطوة 1، انتقل إلى المجلد حيث حفظت البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\CaseHoldsReport.ps1
   ```

   سيطالب البرنامج النصي بالمجلد الهدف لحفظ التقرير فيه.

4. اكتب اسم المسار الكامل للمجلد لحفظ التقرير فيه، ثم اضغط على **Enter**.

   > [!TIP]
   > لحفظ التقرير في المجلد نفسه الذي يوجد فيه البرنامج النصي، اكتب فترة (".") عند مطالبتك بالمجلد الهدف. لحفظ التقرير في مجلد فرعي في المجلد حيث يوجد البرنامج النصي، ما عليك سوى كتابة اسم المجلد الفرعي.

   يبدأ البرنامج النصي بتجميع معلومات حول كل حالات eDiscovery في مؤسستك. لا يمكنك الوصول إلى ملف التقرير أثناء تشغيل البرنامج النصي. بعد اكتمال البرنامج النصي، يتم عرض رسالة تأكيد في Windows PowerShell العمل. بعد عرض هذه الرسالة، يمكنك الوصول إلى التقرير في المجلد الذي حددته في الخطوة 4. اسم ملف التقرير هو `CaseHoldsReport<DateTimeStamp>.csv`.

   بالإضافة إلى ذلك، ينشئ البرنامج النصي أيضا تقريرا مع قائمة من الحالات التي لا تتضمن أي حالات. اسم الملف لهذا التقرير هو `CaseswithNoHolds<DateTimeStamp>.csv`.

   فيما يلي مثال لتشغيل البرنامج CaseHoldsReport.ps1 النصي.

   ![الإخراج بعد تشغيل البرنامج CaseHoldsReport.ps1 النصي.](../media/7d312ed5-505e-4ec5-8f06-3571e3524a1a.png)

## <a name="more-information"></a>معلومات إضافية

تحتوي حالة الحالة على تقرير يتم إنشاؤه عند تشغيل البرنامج النصي في هذه المقالة يحتوي على المعلومات التالية حول كل جلسة مع الاستمرار. كما تم شرحه مسبقا، يجب أن تكون مسؤول eDiscovery لإرجاع معلومات لكل التكاتف في مؤسستك. لمزيد من المعلومات حول حالات التحميس، راجع [حالات eDiscovery](./get-started-core-ediscovery.md).

- اسم الاستمرار واسم حالة eDiscovery المقترنة به.

- سواء كان الاستمرار مقترن ب "النواة" أو Advanced eDiscovery أخرى.

- سواء كانت حالة eDiscovery نشطة أو مغلقة أم لا.

- سواء تم تمكين أو تعطيل الاستمرار أم لا.

- أعضاء حالة eDiscovery المقترنة بالمهمة. يمكن لأعضاء الحالة عرض حالة أو إدارتها، استنادا إلى أذونات eDiscovery التي تم تعيينها.

- الوقت والتاريخ الذي تم فيه إنشاء حالة القضيه.

- إذا كانت حالة ما مغلقة، فإن الشخص الذي أغلقها والوقت والتاريخ الذي تم إغلاقها فيه.

- يتم Exchange علب البريد ومواقع SharePoint المواقع الموجودة في الانتظار.

- إذا كان الاستمرار مستندا إلى استعلام، فإن بناء جملة الاستعلام.

- الوقت والتاريخ الذي تم فيه إنشاء فترة الانتظار والشخص الذي أنشأه.

- تاريخ وتاريخ آخر تغيير في فترة الانتظار والشخص الذي قام بتغييره.
