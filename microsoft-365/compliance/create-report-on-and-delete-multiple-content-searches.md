---
title: إنشاء عمليات بحث متعددة في المحتوى وإنشاء تقرير حولها وحذفها
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: 1d463dda-a3b5-4675-95d4-83db19c9c4a3
description: تعرف على كيفية أتمتة مهام "البحث في المحتوى" مثل إنشاء عمليات البحث وتشغيل التقارير باستخدام ميزة & مركز التوافق PowerShell.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 602997114c46a68be13182a504d0b123e98d2be2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568538"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>إنشاء عمليات بحث متعددة في المحتوى وإنشاء تقرير حولها وحذفها

 غالبا ما يكون إنشاء عمليات البحث عن الاكتشاف والإبلاغ عنها خطوة مهمة في eDiscovery وعمليات البحث عندما تحاول التعرف على البيانات الأساسية وثراء عمليات البحث وجودتها. لمساعدتك على القيام بذلك، & مركز التوافق PowerShell مجموعة من cmdlets لأتمتة مهام البحث في المحتوى التي تستغرق وقتا طويلا. توفر هذه البرامج النصية طريقة سريعة وسهلة لإنشاء عدد من عمليات البحث، ثم تقوم بتشغيل تقارير نتائج البحث المقدرة التي يمكن أن تساعدك على تحديد كمية البيانات المعنية. يمكنك أيضا استخدام البرامج النصية لإنشاء إصدارات مختلفة من عمليات البحث لمقارنة النتائج التي ينتجها كل منها. يمكن أن تساعدك هذه البرامج النصية على التعرف على بياناتك بسرعة وفعالية وإبطالها.

## <a name="before-you-create-a-content-search"></a>قبل إنشاء بحث في المحتوى

- يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365 لتشغيل البرامج النصية الموضحة في هذا الموضوع.

- لتجميع قائمة عناوين URL لمواقع OneDrive for Business في مؤسستك التي يمكنك إضافتها إلى ملف CSV في الخطوة 1، راجع إنشاء قائمة بكل مواقع OneDrive في [مؤسستك](/onedrive/list-onedrive-urls).

- تأكد من حفظ كل الملفات التي تقوم بإنشاءها في هذا الموضوع إلى المجلد نفسه. سيسهل ذلك تشغيل البرامج النصية.

- تتضمن البرامج النصية الحد الأدنى من معالجة الأخطاء. الغرض الأساسي منها هو إنشاء عمليات بحث متعددة في المحتوى وإنشاء تقارير حولها وحذفها بسرعة.

- البرامج النصية العينة المتوفرة في هذا الموضوع غير معتمدة ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرامج النصية العينة AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام البرامج النصية والوثائق العينة أو أدائها معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها المسؤولية عن أي أضرار أيا كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام البرامج النصية أو الوثائق العينة أو عدم القدرة على استخدامها،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>الخطوة 1: إنشاء ملف CSV يحتوي على معلومات حول عمليات البحث التي تريد تشغيلها

يحتوي ملف القيمة المفصولة بفصول (CSV) الذي تقوم بإنشاءه في هذه الخطوة على صف لكل مستخدم يرغب في البحث. يمكنك البحث في علبة بريد المستخدم Exchange Online (التي تتضمن علبة بريد الأرشيف، إذا تم تمكينها) OneDrive for Business الخاص به. أو يمكنك البحث فقط في علبة البريد أو OneDrive for Business الموقع. يمكنك أيضا البحث في أي موقع في SharePoint عبر الإنترنت. سينشئ البرنامج النصي الذي تقوم بتشغيله في الخطوة 3 عملية بحث منفصلة لكل صف في ملف CSV.

1. انسخ النص التالي واللصق فيه .txt باستخدام "المفكرة". احفظ هذا الملف في مجلد على الكمبيوتر المحلي. ستحفظ البرامج النصية الأخرى في هذا المجلد أيضا.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   يسرد الصف الأول أو صف الرأس في الملف المعلمات التي سيتم استخدامها بواسطة **cmdlet** البحث عن التوافق الجديد (في البرنامج النصي في الخطوة 3) لإنشاء بحث محتوى جديد. يتم فصل كل اسم معلمة ب فاصلة. تأكد من عدم وجود أي مسافات في صف الرأس. يمثل كل صف أسفل صف الرأس قيم المعلمات لكل بحث. تأكد من استبدال بيانات العنصر النائب في ملف CSV بالبيانات الفعلية.

2. افتح .txt في Excel، ثم استخدم المعلومات في الجدول التالي لتحرير الملف الذي يحتوي على معلومات لكل عملية بحث.

   ****

   |المعلمة|الوصف|
   |---|---|
   |`ExchangeLocation`|عنوان SMTP لعلبة بريد المستخدم.|
   |`SharePointLocation`|عنوان URL الخاص OneDrive for Business المستخدم أو عنوان URL لأي موقع في مؤسستك. بالنسبة إلى عنوان URL OneDrive for Business، استخدم هذا التنسيق: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. على سبيل المثال،  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|استعلام البحث للبحث. لمزيد من المعلومات حول إنشاء استعلام بحث، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث في المحتوى](keyword-queries-and-search-conditions.md).|
   |`StartDate`|بالنسبة للبريد الإلكتروني، التاريخ الذي تم استلام الرسالة فيه من قبل مستلم أو تم إرساله من قبل المرسل أو بعده. بالنسبة للمستندات SharePoint أو OneDrive for Business، كان تاريخ التعديل الأخير في المستند أو بعده.|
   |`EndDate`|بالنسبة للبريد الإلكتروني، تم إرسال التاريخ الذي تم إرسال الرسالة فيه بواسطة المستخدم أو قبلها. بالنسبة للمستندات SharePoint أو OneDrive for Business، تم تعديل التاريخ الأخير في المستند أو قبله.|
   |

3. احفظ Excel كملف CSV إلى مجلد على الكمبيوتر المحلي. سيستخدم البرنامج النصي الذي تقوم بإنشاءه في الخطوة 3 المعلومات في ملف CSV هذا لإنشاء عمليات البحث.

## <a name="step-2-connect-to-security--compliance-center-powershell"></a>الخطوة 2: الاتصال إلى مركز & التوافق PowerShell

الخطوة التالية هي الاتصال بمركز & التوافق PowerShell لمنظمتك. للحصول على إرشادات مفصلة خطوة بخطوة، راجع الاتصال [إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>الخطوة 3: تشغيل البرنامج النصي لإنشاء عمليات البحث وبدءها

سينشئ البرنامج النصي في هذه الخطوة بحث محتوى منفصلا لكل صف في ملف CSV الذي أنشأته في الخطوة 1. عند تشغيل هذا البرنامج النصي، سيطلب منك قيمتين:

- **"معرِّف** مجموعة البحث" - يوفر هذا الاسم طريقة سهلة لتنظيم عمليات البحث التي تم إنشاؤها من ملف CSV. تسمى كل عملية بحث يتم إنشاؤها باسم "اسم مجموعة البحث"، ثم يتم إلحاق رقم باسم البحث. على سبيل المثال، إذا أدخلت **ContosoCase** لم ID مجموعة البحث، فتسمى عمليات البحث ContosoCase_1 ContosoCase_2 ContosoCase_3 وما إلى ذلك.  تجدر الإشارة إلى أن الاسم الذي تكتبه يتحسس حالة التحسس. عند استخدام "معرّف مجموعة البحث" في الخطوة 4 والخطوة 5، يجب استخدام الحالة نفسها كما فعلت عند إنشائها.

- **ملف CSV** - اسم ملف CSV الذي أنشأته في الخطوة 1. تأكد من تضمين اسم الملف الكامل، بما في ذلك .csv الملف؛ على سبيل المثال،  `ContosoCase.csv`.

لتشغيل البرنامج النصي:

1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `CreateSearches.ps1`. احفظ الملف في المجلد نفسه حيث حفظت الملفات الأخرى.

   ```Powershell
   # Get the Search Group ID and the location of the CSV input file
   $searchGroup = Read-Host 'Search Group ID'
   $csvFile = Read-Host 'Source CSV file'

   # Do a quick check to make sure our group name will not collide with other searches
   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    $searchName = $searchGroup +'_' + $searchCounter
    $search = Get-ComplianceSearch $searchName -EA SilentlyContinue
    if ($search)
    {
       Write-Error "The Search Group ID conflicts with existing searches.  Please choose a search group name and restart the script."
       return
    }
    $searchCounter++
   }

   $searchCounter = 1
   import-csv $csvFile |
     ForEach-Object{

    # Create the query
    $query = $_.ContentMatchQuery
    if(($_.StartDate -or $_.EndDate))
    {
          # Add the appropriate date restrictions.  NOTE: Using the Date condition property here because it works across Exchange, SharePoint, and OneDrive for Business.
          # For Exchange, the Date condition property maps to the Sent and Received dates; for SharePoint and OneDrive for Business, it maps to Created and Modified dates.
          if($query)
          {
              $query += " AND"
          }
          $query += " ("
          if($_.StartDate)
          {
              $query += "Date >= " + $_.StartDate
          }
          if($_.EndDate)
          {
              if($_.StartDate)
              {
                  $query += " AND "
              }
              $query += "Date <= " + $_.EndDate
          }
          $query += ")"
    }

     # -ExchangeLocation can't be set to an empty string, set to null if there's no location.
     $exchangeLocation = $null
     if ( $_.ExchangeLocation)
     {
           $exchangeLocation = $_.ExchangeLocation
     }

    # Create and run the search
    $searchName = $searchGroup +'_' + $searchCounter
    Write-Host "Creating and running search: " $searchName -NoNewline
    $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $exchangeLocation -SharePointLocation $_.SharePointLocation -ContentMatchQuery $query

    # Start and wait for each search to complete
    Start-ComplianceSearch $search.Name
    while ((Get-ComplianceSearch $search.Name).Status -ne "Completed")
    {
       Write-Host " ." -NoNewline
       Start-Sleep -s 3
    }
    Write-Host ""

    $searchCounter++
   }
   ```

2. في Windows PowerShell، انتقل إلى المجلد حيث حفظت البرنامج النصي في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. في المطالبة **بم ID مجموعة البحث** ، اكتب اسم مجموعة البحث، ثم اضغط على **Enter**؛ على سبيل المثال،  `ContosoCase`. تذكر أن هذا الاسم يتحسس حالة التحسس، لذا يجب عليك كتابة الاسم بالطريقة نفسها في الخطوات التالية.

4. في موجه **ملف مصدر CSV** ، اكتب اسم ملف CSV، بما في ذلك .csv الملف؛ على سبيل المثال،  `ContosoCase.csv`.

5. اضغط **على Enter** لمواصلة تشغيل البرنامج النصي.

   يعرض البرنامج النصي تقدم إنشاء عمليات البحث وتشغيلها. عند اكتمال البرنامج النصي، فإنه يرجع إلى المطالبة.

   ![نموذج الإخراج من تشغيل البرنامج النصي لإنشاء عمليات بحث توافق متعددة.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>الخطوة 4: تشغيل البرنامج النصي للتقرير عن تقديرات البحث

بعد إنشاء عمليات البحث، تكون الخطوة التالية هي تشغيل برنامج نصي يعرض تقريرا بسيطا حول عدد عمليات البحث لكل عملية بحث تم إنشاؤها في الخطوة 3. يتضمن التقرير أيضا حجم النتائج لكل عملية بحث، وإجمالي عدد النتائج والحجم الإجمالي لجميع عمليات البحث. عند تشغيل البرنامج النصي لإعداد التقارير، سيطلب منك اسم ملف CSV ومعرف مجموعة البحث إذا كنت تريد حفظ التقرير في ملف CSV.

1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `SearchReport.ps1`. احفظ الملف في المجلد نفسه حيث حفظت الملفات الأخرى.

   ```Powershell
   $searchGroup = Read-Host 'Search Group ID'
   $outputFile = Read-Host 'Enter a file name or file path to save the report to a .csv file. Leave blank to only display the report'
   $searches = Get-ComplianceSearch | ?{$_.Name -clike $searchGroup + "_*"}
   $allSearchStats = @()
   foreach ($partialObj in $searches)
   {
      $search = Get-ComplianceSearch $partialObj.Name
      $sizeMB = [System.Math]::Round($search.Size / 1MB, 2)
      $searchStatus = $search.Status
      if($search.Errors)
      {
          $searchStatus = "Failed"
      }elseif($search.NumFailedSources -gt 0)
      {
          $searchStatus = "Failed Sources"
      }
      $searchStats = New-Object PSObject
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Name -Value $search.Name
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name ContentMatchQuery -Value $search.ContentMatchQuery
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Status -Value $searchStatus
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name Items -Value $search.Items
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size" -Value $search.Size
      Add-Member -InputObject $searchStats -MemberType NoteProperty -Name "Size(MB)" -Value $sizeMB
      $allSearchStats += $searchStats
   }
   # Calculate the totals
   $allItems = ($allSearchStats | Measure-Object Items -Sum).Sum
   # Convert the total size to MB and round to the nearst 100th
   $allSize = ($allSearchStats | Measure-Object 'Size' -Sum).Sum
   $allSizeMB = [System.Math]::Round($allSize  / 1MB, 2)
   # Get the total successful searches and total of all searches
   $allSuccessCount = ($allSearchStats |?{$_.Status -eq "Completed"}).Count
   $allCount = $allSearchStats.Count
   $allStatus = [string]$allSuccessCount + " of " + [string]$allCount
   # Totals Row
   $totalSearchStats = New-Object PSObject
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Name -Value "Total"
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Status -Value $allStatus
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name Items -Value $allItems
   Add-Member -InputObject $totalSearchStats -MemberType NoteProperty -Name "Size(MB)" -Value $allSizeMB
   $allSearchStats += $totalSearchStats
   # Just get the columns we're interested in showing
   $allSearchStatsPrime = $allSearchStats | Select-Object Name, Status, Items, "Size(MB)", ContentMatchQuery
   # Print the results to the screen
   $allSearchStatsPrime |ft -AutoSize -Wrap
   # Save the results to a CSV file
   if ($outputFile)
   {
      $allSearchStatsPrime | Export-Csv -Path $outputFile -NoTypeInformation
   }
   ```

2. في Windows PowerShell، انتقل إلى المجلد حيث حفظت البرنامج النصي في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```Powershell
   .\SearchReport.ps1
   ```

3. في المطالبة **بم ID مجموعة البحث** ، اكتب اسم مجموعة البحث، ثم اضغط على **Enter**؛ على سبيل المثال  `ContosoCase`. تذكر أن هذا الاسم حساس للقضية، لذا يجب عليك كتابته بالطريقة نفسها التي قمت بها عند تشغيل البرنامج النصي في الخطوة 3.

4. في مسار ملف لحفظ التقرير في ملف **CSV (** اتركه فارغا لعرض التقرير فقط)، اكتب اسم ملف لمسار اسم الملف الكامل (بما في ذلك ملحق ملف .csv) إذا كنت تريد حفظ التقرير في ملف CSV. اسم ملف CSV، بما في ذلك .csv الملف. على سبيل المثال، يمكنك الكتابة  `ContosoCaseReport.csv` لحفظه  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` في الدليل الحالي أو يمكنك الكتابة لحفظه في مجلد آخر. يمكنك أيضا ترك المطالبة فارغة لعرض التقرير وليس حفظه في ملف.

5. اضغط **على Enter**.

   يعرض البرنامج النصي تقدم إنشاء عمليات البحث وتشغيلها. عند اكتمال البرنامج النصي، يتم عرض التقرير.

   ![تشغيل تقرير البحث لعرض تقديرات مجموعة البحث.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> إذا تم تحديد علبة البريد أو الموقع نفسه كموا موقع محتوى في أكثر من عملية بحث واحدة في مجموعة بحث، فقد تتضمن النتائج الإجمالية في التقرير (لكل من عدد العناصر والحجم الإجمالي) نتائج للعناصر نفسها. وذلك لأن نفس رسالة البريد الإلكتروني أو المستند سيتم حسابه أكثر من مرة واحدة إذا كان يتطابق مع الاستعلام لعمليات البحث المختلفة في مجموعة البحث.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>الخطوة 5: تشغيل البرنامج النصي لحذف عمليات البحث

نظرا لأنك قد تقوم بإنشاء الكثير من عمليات البحث، فإن هذا البرنامج النصي الأخير يسهل عملية حذف عمليات البحث التي أنشأتها في الخطوة 3 بسرعة. مثل البرامج النصية الأخرى، يطالبك هذا البرنامج أيضا "لمعر مجموعة البحث". سيتم حذف كل عمليات البحث باستخدام "اسم مجموعة البحث" في اسم البحث عند تشغيل هذا البرنامج النصي.

1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `DeleteSearches.ps1`. احفظ الملف في المجلد نفسه حيث حفظت الملفات الأخرى.

   ```Powershell
   # Delete all searches in a search group
   $searchGroup = Read-Host 'Search Group ID'
   Get-ComplianceSearch |
      ForEach-Object{
      # If the name matches the search group name pattern (case sensitive), delete the search
      if ($_.Name -cmatch $searchGroup + "_\d+")
      {
          Write-Host "Deleting search: " $_.Name
          Remove-ComplianceSearch $_.Name -Confirm:$false
      }
   }
   ```

2. في Windows PowerShell، انتقل إلى المجلد حيث حفظت البرنامج النصي في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. في المطالبة **بم ID مجموعة البحث** ، اكتب اسم مجموعة البحث لعمليات البحث التي تريد حذفها، ثم اضغط على **Enter**؛ على سبيل المثال،  `ContosoCase`. تذكر أن هذا الاسم حساس للقضية، لذا يجب عليك كتابته بالطريقة نفسها التي قمت بها عند تشغيل البرنامج النصي في الخطوة 3.

   يعرض البرنامج النصي اسم كل عملية بحث يتم حذفها.

   ![قم بتشغيل البرنامج النصي لحذف عمليات البحث في مجموعة البحث.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
