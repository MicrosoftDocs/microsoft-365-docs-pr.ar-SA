---
title: استخدام برنامج PowerShell النصي للبحث في سجل التدقيق
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: استخدم برنامج PowerShell النصي الذي يقوم بتشغيل Search-UnifiedAuditLog cmdlet في Exchange Online للبحث في سجل التدقيق. تم تحسين هذا البرنامج النصي لإرجاع مجموعة كبيرة من سجلات التدقيق في كل مرة تقوم فيها بتشغيله. يقوم البرنامج النصي بتصدير هذه السجلات إلى ملف CSV يمكنك عرضه أو تحويله باستخدام Power Query في Excel.
ms.openlocfilehash: 0c1d8d6ab8f6a2c8a0dc6a1c858a164c2f4ff494
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632828"
---
# <a name="use-a-powershell-script-to-search-the-audit-log"></a>استخدام برنامج PowerShell النصي للبحث في سجل التدقيق

أصبح الأمان والتوافق والتدقيق أولوية قصوى لمسؤولي تكنولوجيا المعلومات في عالم اليوم. يحتوي Microsoft 365 على العديد من الإمكانات المضمنة لمساعدة المؤسسات على إدارة الأمان والتوافق والتدقيق. على وجه الخصوص، يمكن أن يساعدك تسجيل التدقيق الموحد في التحقيق في حوادث الأمان ومشكلات التوافق. يمكنك استرداد سجلات التدقيق باستخدام الأساليب التالية:

- [واجهة برمجة تطبيقات نشاط إدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)

- [أداة البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مدخل التوافق في Microsoft Purview

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) cmdlet في Exchange Online PowerShell

إذا كنت بحاجة إلى استرداد سجلات التدقيق بشكل منتظم، يجب عليك التفكير في حل يستخدم واجهة برمجة تطبيقات نشاط الإدارة Office 365 لأنه يمكن أن يوفر للمؤسسات الكبيرة قابلية التوسع والأداء لاسترداد ملايين سجلات التدقيق على أساس مستمر. يعد استخدام أداة البحث في سجل التدقيق في مدخل التوافق طريقة جيدة للعثور بسرعة على سجلات التدقيق لعمليات معينة تحدث في نطاق زمني أقصر. قد يؤدي استخدام نطاقات زمنية أطول في أداة البحث في سجل التدقيق، خاصة للمؤسسات الكبيرة، إلى إرجاع عدد كبير جدا من السجلات بحيث يمكن إدارتها أو تصديرها بسهولة.

عندما تكون هناك حالات تحتاج فيها إلى استرداد بيانات التدقيق يدويا للتحقيق أو الحدث المحدد، خاصة بالنسبة لنطاقات التاريخ الأطول في المؤسسات الأكبر حجما، قد يكون استخدام أمر cmdlet **Search-UnifiedAuditLog** هو الخيار الأفضل. تتضمن هذه المقالة برنامج PowerShell نصيا يستخدم cmdlet يمكنه استرداد 50000 سجل تدقيق (في كل مرة تقوم فيها بتشغيل cmdlet) ثم تصديرها إلى ملف CSV يمكنك تنسيقه باستخدام Power Query في Excel للمساعدة في مراجعتك. يؤدي استخدام البرنامج النصي في هذه المقالة أيضا إلى تقليل فرصة انتهاء مهلة عمليات البحث الكبيرة في سجل التدقيق في الخدمة.

## <a name="before-you-run-the-script"></a>قبل تشغيل البرنامج النصي

- يجب تمكين تسجيل التدقيق لمؤسستك لاستخدام البرنامج النصي بنجاح لإرجاع سجلات التدقيق. يتم تشغيل تسجيل التدقيق بشكل افتراضي لمؤسسات Microsoft 365 Office 365 للمؤسسات. للتحقق من تشغيل البحث في سجل التدقيق لمؤسستك، يمكنك تشغيل الأمر التالي في Exchange Online PowerShell:

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  تشير قيمة الخاصية `True` **UnifiedAuditLogIngestionEnabled** إلى أن البحث في سجل التدقيق قيد التشغيل.

- يجب تعيين دور سجلات التدقيق View-Only أو سجلات التدقيق في Exchange Online لتشغيل البرنامج النصي بنجاح. بشكل افتراضي، يتم تعيين هذه الأدوار إلى مجموعات دور إدارة التوافق وإدارة المؤسسة في صفحة الأذونات في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. لمزيد من المعلومات، راجع قسم "متطلبات البحث في سجل التدقيق" في [البحث في سجل التدقيق في مركز التوافق](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log).

- قد يستغرق إكمال البرنامج النصي وقتا طويلا. تعتمد المدة التي يستغرقها التشغيل على نطاق التاريخ وحجم الفاصل الزمني الذي تقوم بتكوين البرنامج النصي لاسترداد سجلات التدقيق له. ستؤدي نطاقات التاريخ الأكبر والفاصلات الزمنية الأصغر إلى وقت تشغيل طويل. راجع الجدول في الخطوة 2 للحصول على مزيد من المعلومات حول نطاق التاريخ والفاصل الزمني.

- لا يتم دعم نموذج البرنامج النصي الوارد في هذه المقالة ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نموذج البرنامج النصي AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نموذج البرنامج النصي والوثائق معك. لا تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرنامج النصي أو إنتاجه أو تسليمه مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناشئة عن استخدام نموذج البرنامج النصي أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-connect-to-exchange-online-powershell"></a>الخطوة 1: الاتصال Exchange Online PowerShell

الخطوة الأولى هي الاتصال Exchange Online PowerShell. يمكنك الاتصال باستخدام المصادقة الحديثة أو المصادقة متعددة العوامل (MFA). للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-modify-and-run-the-script-to-retrieve-audit-records"></a>الخطوة 2: تعديل البرنامج النصي وتشغيله لاسترداد سجلات التدقيق

بعد الاتصال Exchange Online PowerShell، تتمثل الخطوة التالية في إنشاء البرنامج النصي وتعديله وتشغيله لاسترداد بيانات التدقيق. تحتوي الأسطر السبعة الأولى في البرنامج النصي للبحث في سجل التدقيق على المتغيرات التالية التي يمكنك تعديلها لتكوين البحث. راجع الجدول في الخطوة 2 للحصول على وصف لهذه المتغيرات.

1. احفظ النص التالي في برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1. على سبيل المثال، SearchAuditLog.ps1.

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

2. تعديل المتغيرات المدرجة في الجدول التالي لتكوين معايير البحث. يتضمن البرنامج النصي قيما نموذجية لهذه المتغيرات، ولكن يجب عليك تغييرها (ما لم يذكر خلاف ذلك) لتلبية متطلباتك المحددة.

   <br>

   ****

   |متغير|قيمة نموذجية|الوصف|
   |---|---|---|
   |`$logFile`|"d:\temp\AuditSearchLog.txt"|تحديد اسم وموقع ملف السجل الذي يحتوي على معلومات حول تقدم البحث في سجل التدقيق الذي تم تنفيذه بواسطة البرنامج النصي. يكتب البرنامج النصي الطوابع الزمنية UTC إلى ملف السجل.|
   |`$outputFile`|"d:\temp\AuditRecords.csv"|تحديد اسم وموقع ملف CSV الذي يحتوي على سجلات التدقيق التي تم إرجاعها بواسطة البرنامج النصي.|
   |`[DateTime]$start` و `[DateTime]$end`|[DateTime]::UtcNow.AddDays(-1) <br/>[DateTime]::UtcNow|تحديد نطاق التاريخ للبحث في سجل التدقيق. سيقوم البرنامج النصي بإرجاع سجلات لأنشطة التدقيق التي حدثت ضمن نطاق التاريخ المحدد. على سبيل المثال، لإرجاع الأنشطة التي تم تنفيذها في يناير 2021، يمكنك استخدام تاريخ `"2021-01-01"` بدء وتاريخ `"2021-01-31"` انتهاء (تأكد من إحاطة القيم بعلامات اقتباس مزدوجة) ترجع القيمة النموذجية في البرنامج النصي سجلات الأنشطة التي تم تنفيذها في الساعات ال 24 السابقة. إذا لم تقم بتضمين طابع زمني في القيمة، يكون الطابع الزمني الافتراضي هو 12:00 ص (منتصف الليل) في التاريخ المحدد.|
   |`$record`|"AzureActiveDirectory"|تحديد نوع سجل أنشطة التدقيق (تسمى أيضا *العمليات*) للبحث عن. تشير هذه الخاصية إلى الخدمة أو الميزة التي تم تشغيل نشاط فيها. للحصول على قائمة بأنواع السجلات التي يمكنك استخدامها لهذا المتغير، راجع [نوع سجل التدقيق](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype). يمكنك استخدام اسم نوع السجل أو قيمة ENUM. <br/><br/>**تلميح:** لإرجاع سجلات التدقيق لكافة أنواع السجلات، استخدم القيمة `$null` (بدون علامات اقتباس مزدوجة).|
   |`$resultSize`|5000|تحديد عدد النتائج التي يتم إرجاعها في كل مرة يتم فيها استدعاء أمر cmdlet **Search-UnifiedAuditLog** بواسطة البرنامج النصي (يسمى *مجموعة نتائج*). قيمة 5000 هي القيمة القصوى التي يدعمها cmdlet. اترك هذه القيمة كما هي.|
   |`$intervalMinutes`|60|للمساعدة في التغلب على حد السجلات التي تم إرجاعها وهو 5000 سجل، يأخذ هذا المتغير نطاق البيانات الذي حددته ويقسمه إلى فواصل زمنية أصغر. الآن يخضع كل فاصل زمني، وليس نطاق التاريخ بأكمله، إلى حد إخراج السجل 5000 للأمر. يجب أن تكون القيمة الافتراضية ل 5000 سجل لكل فاصل زمني مدته 60 دقيقة ضمن نطاق التاريخ كافية لمعظم المؤسسات. ولكن، إذا أرجع البرنامج النصي خطأ يقول، `maximum results limitation reached`فقم بإنقاص الفاصل الزمني (على سبيل المثال، إلى 30 دقيقة أو حتى 15 دقيقة) وأعد تشغيل البرنامج النصي.|
   ||||

   تتوافق معظم المتغيرات المدرجة في الجدول السابق مع معلمات أمر cmdlet **Search-UnifiedAuditLog** . لمزيد من المعلومات حول هذه المعلمات، راجع [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

3. على الكمبيوتر المحلي، افتح Windows PowerShell وانتقل إلى المجلد حيث حفظت البرنامج النصي المعدل.

4. تشغيل البرنامج النصي في Exchange Online PowerShell؛ على سبيل المثال:

   ```powershell
   .\SearchAuditLog.ps1
   ```

يعرض البرنامج النصي رسائل التقدم أثناء تشغيله. بعد الانتهاء من تشغيل البرنامج النصي، يقوم بإنشاء ملف السجل وملف CSV الذي يحتوي على سجلات التدقيق ويحفظها في المجلدات المعرفة بواسطة `$logFile` المتغيرات.`$outputFile`

> [!IMPORTANT]
> هناك حد 50000 للحد الأقصى لعدد سجلات التدقيق التي يتم إرجاعها في كل مرة تقوم فيها بتشغيل cmdlet في البرنامج النصي. إذا قمت بتشغيل هذا البرنامج النصي وإرجاع 50000 نتيجة، فمن المحتمل أن سجلات التدقيق للأنشطة التي حدثت ضمن نطاق التاريخ لم يتم تضمينها. إذا حدث ذلك، نوصي بتقسيم نطاق التاريخ إلى مدد أصغر ثم إعادة تشغيل البرنامج النصي لكل نطاق تاريخ. على سبيل المثال، إذا كان نطاق التاريخ الذي يبلغ 90 يوما يرجع 50000 نتيجة، فيمكنك إعادة تشغيل البرنامج النصي مرتين، مرة واحدة لأول 45 يوما في نطاق التاريخ ثم مرة أخرى لل 45 يوما التالية.

## <a name="step-3-format-and-view-the-audit-records"></a>الخطوة 3: تنسيق سجلات التدقيق وعرضها

بعد تشغيل البرنامج النصي وتصدير سجلات التدقيق إلى ملف CSV، قد تحتاج إلى تنسيق CSV لتسهيل مراجعة سجلات التدقيق وتحليلها. إحدى طرق القيام بذلك هي ميزة تحويل JSON Power Query في Excel لتقسيم كل خاصية في كائن JSON في عمود **AuditData** إلى عمودها الخاص. للحصول على إرشادات مفصلة خطوة بخطوة، راجع "الخطوة 2: تنسيق سجل التدقيق الذي تم تصديره باستخدام محرر Power Query" في [تصدير سجلات سجل التدقيق وتكوينها وعرضها](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).
