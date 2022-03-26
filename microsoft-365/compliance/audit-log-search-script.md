---
title: استخدام برنامج PowerShell النصي للبحث في سجل التدقيق
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: استخدم برنامج PowerShell النصي الذي يقوم Search-UnifiedAuditLog cmdlet Exchange Online للبحث في سجل التدقيق. تم تحسين هذا البرنامج النصي لإرجاع مجموعة كبيرة من سجلات التدقيق في كل مرة تقوم فيها بتشغيله. يقوم البرنامج النصي بتصدير هذه السجلات إلى ملف CSV يمكنك عرضه أو تحويله باستخدام Power Query في Excel.
ms.openlocfilehash: 60f78f5a5eebeaa90f01b4b251d917f178c06ae9
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63569780"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>استخدام برنامج PowerShell النصي للبحث في سجل التدقيق

أصبح الأمان والتوافق والتدقيق أولوية عليا لمسؤولي تكنولوجيا المعلومات في عالم اليوم. Microsoft 365 العديد من الإمكانات المضمنة لمساعدة المؤسسات على إدارة الأمان والتوافق والتدقيق. بشكل خاص، يمكن أن تساعدك عملية تسجيل التدقيق الموحد على التحقيق في أحداث الأمان وم مشاكل التوافق. يمكنك استرداد سجلات التدقيق باستخدام الأساليب التالية:

- [API Office 365 نشاط الإدارة](/office/office-365-management-api/office-365-management-activity-api-reference)

- أداة [البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مركز التوافق في Microsoft 365

- Cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) في Exchange Online PowerShell

إذا كنت بحاجة إلى استرداد سجلات التدقيق بشكل منتظم، يجب عليك التفكير في حل يستخدم API لنشاط الإدارة في Office 365 لأنه يمكن أن يوفر إمكانية التوسع والأداء في المؤسسات الكبيرة لاسترداد الملايين من سجلات التدقيق بشكل مستمر. استخدام أداة البحث في سجل التدقيق في مركز التوافق في Microsoft 365 طريقة جيدة للبحث بسرعة عن سجلات التدقيق لعمليات معينة تحدث في نطاق وقت أقصر. قد يعود استخدام نطاقات زمنية أطول في أداة البحث في سجل التدقيق، خاصة بالنسبة إلى المؤسسات الكبيرة، عددا كبيرا جدا من السجلات التي يمكن إدارتها أو تصديرها بسهولة.

عند وجود حالات تحتاج فيها إلى استرداد بيانات التدقيق يدويا من أجل تحقيق أو حادث معين، خاصة بالنسبة لنطاقات تاريخ أطول في المؤسسات الكبيرة، قد يكون استخدام **الأمر cmdlet Search-UnifiedAuditLog** هو الخيار الأفضل. تتضمن هذه المقالة برنامج PowerShell النصي الذي يستخدم الأمر cmdlet الذي يمكنه استرداد 50000 سجل تدقيق (في كل مرة تقوم فيها بتشغيل الأمر cmdlet) ثم تصديرها إلى ملف CSV يمكنك تنسيقه باستخدام Power Query في Excel لمساعدتك في المراجعة. كما يقلل استخدام البرنامج النصي في هذه المقالة من احتمالية أن تكون عمليات البحث الكبيرة في سجل التدقيق قد انتهت في الخدمة.

## <a name="before-you-run-the-script"></a>قبل تشغيل البرنامج النصي

- يجب تمكين تسجيل التدقيق لمنظمتك من استخدام البرنامج النصي بنجاح لإرجاع سجلات التدقيق. يتم تشغيل تسجيل التدقيق بشكل افتراضي Microsoft 365 Office 365 المؤسسات. للتحقق من تشغيل البحث في سجل التدقيق لمنظمتك، يمكنك تشغيل الأمر التالي في Exchange Online PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  تشير قيمة **الخاصية UnifiedAuditLogIngestionEnabled** إلى أنه تم تشغيل البحث في سجل التدقيق.`True`

- يجب أن يتم تعيين دور View-Only "سجلات التدقيق" أو "سجلات التدقيق" في Exchange Online البرنامج النصي بنجاح. بشكل افتراضي، يتم تعيين هذه الأدوار إلى مجموعات أدوار إدارة التوافق وإدارة المؤسسة على صفحة الأذونات <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">في Exchange مركز الإدارة</a>. لمزيد من المعلومات، راجع القسم "متطلبات البحث في سجل التدقيق" في البحث في سجل التدقيق [في مركز التوافق](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- قد يستغرق إكمال البرنامج النصي وقتا طويلا. تعتمد المدة التي يستغرقها التشغيل على نطاق التاريخ وحجم الفاصل الزمني الذي تقوم بتكوين البرنامج النصي لاسترداد سجلات التدقيق له. ستنتج عن نطاقات التاريخ الكبيرة وفترات زمنية أصغر وقتا طويلا. راجع الجدول في الخطوة 2 للحصول على مزيد من المعلومات حول نطاق التاريخ والفترات الزمنية.

- البرنامج النصي النموذجي الموفر في هذه المقالة غير معتمد ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرنامج النصي النموذجي AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام أو أداء البرنامج النصي النموذجي والوثائق معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرنامج النصي أو إنتاجه أو تسليمه المسؤولية عن أي أضرار من أي نوع (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام أو عدم القدرة على استخدام نموذج البرنامج النصي أو الوثائق،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.

## <a name="step-1-connect-to-exchange-online-powershell"></a>الخطوة 1: الاتصال Exchange Online PowerShell

الخطوة الأولى هي الاتصال Exchange Online PowerShell. يمكنك الاتصال باستخدام المصادقة الحديثة أو باستخدام المصادقة متعددة العوامل (MFA). للحصول على إرشادات مفصلة خطوة بخطوة، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>الخطوة 2: تعديل البرنامج النصي وتشغيله لاسترداد سجلات التدقيق

بعد الاتصال ب PowerShell Exchange Online الخطوة التالية هي إنشاء البرنامج النصي وتعديله وتشغيله لاسترداد بيانات التدقيق. تحتوي الأسطر السبعة الأولى في البرنامج النصي للبحث في سجل التدقيق على المتغيرات التالية التي يمكنك تعديلها لتكوين البحث. راجع الجدول في الخطوة 2 للحصول على وصف لهذه المتغيرات.

1. احفظ النص التالي في Windows PowerShell نصي باستخدام لاحقة اسم الملف .ps1. على سبيل المثال، SearchAuditLog.ps1.

   ```powershell
   #Modify the values for the following variables to configure the audit log search.
   $logFile = "d:\AuditLogSearch\AuditLogSearchLog.txt"
   $outputFile = "d:\AuditLogSearch\AuditLogRecords.csv"
   [DateTime]$start = [DateTime]::UtcNow.AddDays(-1)
   [DateTime]$end = [DateTime]::UtcNow
   $record = "AzureActiveDirectory"
   $resultSize = 5000
   $intervalMinutes = 60
   
   #Start script
   [DateTime]$currentStart = $start
   [DateTime]$currentEnd = $start
   
   Function Write-LogFile ([String]$Message)
   {
       $final = [DateTime]::Now.ToUniversalTime().ToString("s") + ":" + $Message
       $final | Out-File $logFile -Append
   }
   
   Write-LogFile "BEGIN: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize."
   Write-Host "Retrieving audit records for the date range between $($start) and $($end), RecordType=$record, ResultsSize=$resultSize"
   
   $totalCount = 0
   while ($true)
   {
       $currentEnd = $currentStart.AddMinutes($intervalMinutes)
       if ($currentEnd -gt $end)
       {
           $currentEnd = $end
       }
   
       if ($currentStart -eq $currentEnd)
       {
           break
       }
   
       $sessionID = [Guid]::NewGuid().ToString() + "_" +  "ExtractLogs" + (Get-Date).ToString("yyyyMMddHHmmssfff")
       Write-LogFile "INFO: Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       Write-Host "Retrieving audit records for activities performed between $($currentStart) and $($currentEnd)"
       $currentCount = 0
   
       $sw = [Diagnostics.StopWatch]::StartNew()
       do
       {
           $results = Search-UnifiedAuditLog -StartDate $currentStart -EndDate $currentEnd -RecordType $record -SessionId $sessionID -SessionCommand ReturnLargeSet -ResultSize $resultSize
   
           if (($results | Measure-Object).Count -ne 0)
           {
               $results | export-csv -Path $outputFile -Append -NoTypeInformation
   
               $currentTotal = $results[0].ResultCount
               $totalCount += $results.Count
               $currentCount += $results.Count
               Write-LogFile "INFO: Retrieved $($currentCount) audit records out of the total $($currentTotal)"
   
               if ($currentTotal -eq $results[$results.Count - 1].ResultIndex)
               {
                   $message = "INFO: Successfully retrieved $($currentTotal) audit records for the current time range. Moving on!"
                   Write-LogFile $message
                   Write-Host "Successfully retrieved $($currentTotal) audit records for the current time range. Moving on to the next interval." -foregroundColor Yellow
                   ""
                   break
               }
           }
       }
       while (($results | Measure-Object).Count -ne 0)
   
       $currentStart = $currentEnd
   }
   
   Write-LogFile "END: Retrieving audit records between $($start) and $($end), RecordType=$record, PageSize=$resultSize, total count: $totalCount."
   Write-Host "Script complete! Finished retrieving audit records for the date range between $($start) and $($end). Total count: $totalCount" -foregroundColor Green
   ```

2. تعديل المتغيرات المدرجة في الجدول التالي لتكوين معايير البحث. يتضمن البرنامج النصي قيما نموذجية لهذه المتغيرات، ولكن يجب تغييرها (ما لم يذكر خلاف ذلك) لتلبية متطلباتك المحددة.

   <br>

   ****

   |متغير|قيمة نموذجية|الوصف|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|يحدد اسم ملف السجل وموقعه الذي يحتوي على معلومات حول تقدم عملية البحث في سجل التدقيق التي ينفذها البرنامج النصي. يكتب البرنامج النصي الحروف الزمنية UTC إلى ملف السجل.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|يحدد اسم ملف CSV الذي يحتوي على سجلات التدقيق التي تم إرجاعها بواسطة البرنامج النصي وموقعه.|
   |`[DateTime]$start` و `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|يحدد نطاق التاريخ للبحث في سجل التدقيق. سيرجع البرنامج النصي سجلات لأنشطة التدقيق التي وقعت ضمن نطاق التاريخ المحدد. على سبيل المثال، لإرجاع الأنشطة التي تم تنفيذها في يناير 2021 `"2021-01-01"` `"2021-01-31"` ، يمكنك استخدام تاريخ بدء وتاريخ انتهاء (تأكد من إحاطة القيم بين علامات اقتباس مزدوجة) ترجع القيمة العينة في البرنامج النصي سجلات الأنشطة التي تم تنفيذها في الساعات ال 24 السابقة. إذا لم تكن قد قمت بتضمين عاينة زمنية في القيمة، فإن الوقت الافتراضي هو 12:00 صباحا (منتصف الليل) في التاريخ المحدد.|
   |`$record`|"AzureActiveDirectory"|يحدد نوع سجل أنشطة التدقيق (تسمى أيضا *العمليات*) للبحث عنه. تشير هذه الخاصية إلى الخدمة أو الميزة التي تم تشغيل نشاط فيها. للحصول على قائمة بأنواع السجلات التي يمكنك استخدامها لهذا المتغير، راجع [نوع سجل التدقيق](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). يمكنك استخدام اسم نوع السجل أو قيمة ENUM. <br/><br/>**تلميح:** لإرجاع سجلات التدقيق لكل أنواع السجلات، استخدم القيمة `$null` (بدون علامات اقتباس مزدوجة).|
   |`$resultSize`|5000|يحدد عدد النتائج التي يتم إرجاعها في كل مرة يتم فيها استدعاء أمر cmdlet **Search-UnifiedAuditLog** بواسطة البرنامج النصي (يسمى *مجموعة نتائج*). القيمة 5000 هي الحد الأقصى للقيمة المعتمدة بواسطة cmdlet. اترك هذه القيمة كما هي.|
   |`$intervalMinutes`|60|للمساعدة على التغلب على الحد الأقصى لعدد السجلات التي تم إرجاعها وهو 5000 سجل، يأخذ هذا المتغير نطاق البيانات الذي حددته ويقطعه إلى فواصل زمنية أصغر. يخضع الآن كل فاصل زمني، وليس نطاق التاريخ بأكمله، إلى حد إخراج السجل 5000 من الأمر. يجب أن تكون القيمة الافتراضية ل 5000 سجل لكل فاصل زمني لمدة 60 دقيقة ضمن نطاق التاريخ كافية لمعظم المؤسسات. ولكن، إذا كان البرنامج النصي `maximum results limitation reached`يرجع خطأ يقول، فقلل الفاصل الزمني (على سبيل المثال، إلى 30 دقيقة أو حتى 15 دقيقة) ثم اعيد تشغيل البرنامج النصي.|
   ||||

   تتوافق معظم المتغيرات المدرجة في الجدول السابق مع معلمات **الأمر cmdlet Search-UnifiedAuditLog** . لمزيد من المعلومات حول هذه المعلمات، راجع [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. على الكمبيوتر المحلي، افتح Windows PowerShell واذهب إلى المجلد حيث حفظت البرنامج النصي المعدل.

4. تشغيل البرنامج النصي في Exchange Online PowerShell؛ على سبيل المثال:

   ```powershell
   .\SearchAuditLog.ps1
   ```

يعرض البرنامج النصي رسائل التقدم أثناء تشغيله. بعد الانتهاء من تشغيل البرنامج النصي، يتم إنشاء ملف السجل وملف CSV `$logFile` الذي يحتوي على سجلات التدقيق ويحفظها في المجلدات المعرفة بواسطة المتغيرين و `$outputFile` .

> [!IMPORTANT]
> يوجد حد 50000 كحد أقصى لعدد سجلات التدقيق التي يتم إرجاعها في كل مرة تقوم فيها بتشغيل الأمر cmdlet في البرنامج النصي. إذا قمت بتشغيل هذا البرنامج النصي وأرجعت 50000 نتيجة، فمن المرجح أن سجلات التدقيق الخاصة بالأنشطة التي حدثت ضمن نطاق التاريخ لم يتم تضمينها. إذا حدث ذلك، نوصي بتقسيم نطاق التاريخ إلى مدد أصغر ثم إعادة تشغيل البرنامج النصي لكل نطاق تاريخ. على سبيل المثال، إذا كان نطاق التاريخ 90 يوما يرجع 50000 نتيجة، يمكنك إعادة تشغيل البرنامج النصي مرتين، مرة واحدة لأول 45 يوما في نطاق التاريخ، ثم مرة أخرى لمدة 45 يوما القادمة.

## <a name="step-3-format-and-view-the-audit-records"></a>الخطوة 3: تنسيق سجلات التدقيق وعرضها

بعد تشغيل البرنامج النصي وتصدير سجلات التدقيق إلى ملف CSV، قد تحتاج إلى تنسيق CSV لتسهيل مراجعة سجلات التدقيق وتحليلها. إحدى الطرق للقيام بذلك هي ميزة تحويل Power Query JSON في Excel لتقسيم كل خاصية في كائن JSON في عمود **بيانات** التدقيق إلى عمودها الخاص. للحصول على إرشادات مفصلة خطوة بخطوة، راجع "الخطوة 2: تنسيق سجل التدقيق الذي تم تصديره باستخدام محرر Power Query" في تصدير سجلات سجل التدقيق وتكوينها [وعرضها](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
