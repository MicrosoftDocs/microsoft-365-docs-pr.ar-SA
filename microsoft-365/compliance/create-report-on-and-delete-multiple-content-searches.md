---
title: إنشاء عمليات البحث في المحتوى وإعداد تقرير بشأنها وحذفها
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
description: تعرف على كيفية أتمتة مهام البحث في المحتوى مثل إنشاء عمليات البحث وتشغيل التقارير باستخدام Security & Compliance Center PowerShell.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c6e84641fef819503349803cdd54d5aaa860fc50
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000213"
---
# <a name="create-report-on-and-delete-multiple-content-searches"></a>إنشاء عدة عمليات بحث في المحتوى وإعداد تقرير بشأنها وحذفها

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

 غالبا ما يكون إنشاء عمليات البحث عن الاكتشاف والإبلاغ عنها بسرعة خطوة مهمة في eDiscovery والتحقيقات عندما تحاول التعرف على البيانات الأساسية وثراء عمليات البحث وجودتها. لمساعدتك على القيام بذلك، يوفر Security & Compliance Center PowerShell مجموعة من أوامر cmdlets لأتمتة مهام البحث عن المحتوى التي تستغرق وقتا طويلا. توفر هذه البرامج النصية طريقة سريعة وسهلة لإنشاء عدد من عمليات البحث، ثم تشغيل تقارير نتائج البحث المقدرة التي يمكن أن تساعدك في تحديد كمية البيانات المعنية. يمكنك أيضا استخدام البرامج النصية لإنشاء إصدارات مختلفة من عمليات البحث لمقارنة النتائج التي ينتجها كل منها. يمكن أن تساعدك هذه البرامج النصية على تحديد بياناتك ومعالجتها بسرعة وكفاءة.

## <a name="before-you-create-a-content-search"></a>قبل إنشاء البحث في المحتوى

- يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل توافق Microsoft Purview لتشغيل البرامج النصية الموضحة في هذا الموضوع.

- لتجميع قائمة بعناوين URL لمواقع OneDrive for Business في مؤسستك التي يمكنك إضافتها إلى ملف CSV في الخطوة 1، راجع [إنشاء قائمة بكافة مواقع OneDrive في مؤسستك](/onedrive/list-onedrive-urls).

- تأكد من حفظ كافة الملفات التي تقوم بإنشائها في هذا الموضوع إلى المجلد نفسه. وهذا سيجعل من السهل تشغيل البرامج النصية.

- تتضمن البرامج النصية الحد الأدنى من معالجة الأخطاء. الغرض الأساسي منها هو إنشاء عمليات بحث محتوى متعددة وإعداد تقرير بشأنها وحذفها بسرعة.

- لا يتم دعم نماذج البرامج النصية المتوفرة في هذا الموضوع ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نماذج البرامج النصية AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نماذج البرامج النصية والوثائق معك. لن تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناتجة عن استخدام نماذج البرامج النصية أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-create-a-csv-file-that-contains-information-about-the-searches-you-want-to-run"></a>الخطوة 1: إنشاء ملف CSV يحتوي على معلومات حول عمليات البحث التي تريد تشغيلها

يحتوي ملف القيمة المفصولة بفاواصل (CSV) الذي تقوم بإنشائه في هذه الخطوة على صف لكل مستخدم يريد البحث. يمكنك البحث في علبة بريد المستخدم Exchange Online (التي تتضمن علبة بريد الأرشيف، إذا تم تمكينها) وموقع OneDrive for Business الخاص به. أو يمكنك البحث فقط في علبة البريد أو موقع OneDrive for Business. يمكنك أيضا البحث في أي موقع في مؤسستك SharePoint Online. سيقوم البرنامج النصي الذي تقوم بتشغيله في الخطوة 3 بإنشاء بحث منفصل لكل صف في ملف CSV.

1. انسخ النص التالي والصقه في ملف .txt باستخدام NotePad. احفظ هذا الملف في مجلد على الكمبيوتر المحلي. ستحفظ البرامج النصية الأخرى إلى هذا المجلد أيضا.

   ```text
   ExchangeLocation,SharePointLocation,ContentMatchQuery,StartDate,EndDate
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2000,12/31/2005
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2006,12/31/2010
   sarad@contoso.onmicrosoft.com,https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com,(lawsuit OR legal),1/1/2011,3/21/2016
   ,https://contoso.sharepoint.com/sites/contoso,,,3/21/2016
   ,https://contoso-my.sharepoint.com/personal/davidl_contoso_onmicrosoft_com,,1/1/2015,
   ,https://contoso-my.sharepoint.com/personal/janets_contoso_onmicrosoft_com,,1/1/2015,
   ```

   يسرد الصف الأول أو صف الرأس للملف المعلمات التي سيتم استخدامها بواسطة **New-ComplianceSearch** cmdlet (في البرنامج النصي في الخطوة 3) لإنشاء عمليات بحث محتوى جديدة. يتم فصل كل اسم معلمة بفواصل. تأكد من عدم وجود أي مسافات في صف الرأس. يمثل كل صف أسفل صف الرأس قيم المعلمات لكل عملية بحث. تأكد من استبدال بيانات العنصر النائب في ملف CSV ببياناتك الفعلية.

2. افتح ملف .txt في Excel، ثم استخدم المعلومات الموجودة في الجدول التالي لتحرير الملف مع معلومات لكل عملية بحث.

   ****

   |المعلمه|الوصف|
   |---|---|
   |`ExchangeLocation`|عنوان SMTP لعل بريد المستخدم.|
   |`SharePointLocation`|عنوان URL لموقع OneDrive for Business الخاص بالمستخدم أو URL لأي موقع في مؤسستك. بالنسبة إلى URL لمواقع OneDrive for Business، استخدم هذا التنسيق: ` https://<your organization>-my.sharepoint.com/personal/<user alias>_<your organization>_onmicrosoft_com `. على سبيل المثال،  `https://contoso-my.sharepoint.com/personal/sarad_contoso_onmicrosoft_com`.|
   |`ContentMatchQuery`|استعلام البحث للبحث. لمزيد من المعلومات حول إنشاء استعلام بحث، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md).|
   |`StartDate`|بالنسبة للبريد الإلكتروني، التاريخ الذي تم فيه تلقي الرسالة أو بعدها من قبل مستلم أو تم إرسالها من قبل المرسل. بالنسبة للمستندات الموجودة على مواقع SharePoint أو OneDrive for Business، تم آخر تعديل في المستند أو بعده.|
   |`EndDate`|بالنسبة للبريد الإلكتروني، يتم إرسال تاريخ إرسال الرسالة من قبل المستخدم أو قبلها. بالنسبة للمستندات الموجودة على مواقع SharePoint أو OneDrive for Business، التاريخ الذي تم فيه آخر تعديل للمستند أو قبله.|
   |

3. احفظ ملف Excel كملف CSV إلى مجلد على الكمبيوتر المحلي. سيستخدم البرنامج النصي الذي تقوم بإنشائه في الخطوة 3 المعلومات الموجودة في ملف CSV هذا لإنشاء عمليات البحث.

## <a name="step-2-connect-to-security--compliance-center-powershell"></a>الخطوة 2: الاتصال إلى Security & Compliance Center PowerShell

الخطوة التالية هي الاتصال ب Security & Compliance Center PowerShell لمؤسستك. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="step-3-run-the-script-to-create-and-start-the-searches"></a>الخطوة 3: تشغيل البرنامج النصي لإنشاء عمليات البحث وبدءها

سيقوم البرنامج النصي في هذه الخطوة بإنشاء بحث محتوى منفصل لكل صف في ملف CSV الذي قمت بإنشائه في الخطوة 1. عند تشغيل هذا البرنامج النصي، ستتم مطالبتك بقيمتين:

- **معرف مجموعة البحث** - يوفر هذا الاسم طريقة سهلة لتنظيم عمليات البحث التي تم إنشاؤها من ملف CSV. تتم تسمية كل عملية بحث تم إنشاؤها باستخدام معرف مجموعة البحث، ثم يتم إلحاق رقم باسم البحث. على سبيل المثال، إذا أدخلت **ContosoCase** لمعرف مجموعة البحث، فستتم تسمية عمليات البحث **ContosoCase_1** **ContosoCase_2** **ContosoCase_3** وهكذا. لاحظ أن الاسم الذي تكتبه حساس لحالة الأحرف. عند استخدام معرف مجموعة البحث في الخطوة 4 والخطوة 5، يجب استخدام الحالة نفسها التي استخدمتها عند إنشائه.

- **ملف CSV** - اسم ملف CSV الذي قمت بإنشائه في الخطوة 1. تأكد من تضمين استخدام اسم الملف الكامل، وقم بتضمين ملحق الملف .csv؛ على سبيل المثال،  `ContosoCase.csv`.

لتشغيل البرنامج النصي:

1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `CreateSearches.ps1`. احفظ الملف إلى المجلد نفسه حيث حفظت الملفات الأخرى.

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

2. في Windows PowerShell، انتقل إلى المجلد حيث قمت بحفظ البرنامج النصي في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```Powershell
   .\CreateSearches.ps1
   ```

3. في موجه **معرف مجموعة البحث** ، اكتب اسم مجموعة البحث، ثم اضغط على **مفتاح الإدخال Enter**؛ على سبيل المثال،  `ContosoCase`. تذكر أن هذا الاسم حساس لحالة الأحرف، لذلك سيتعين عليك كتابته بنفس الطريقة في الخطوات التالية.

4. في موجه **ملف CSV المصدر** ، اكتب اسم ملف CSV، بما في ذلك ملحق ملف .csv؛ على سبيل المثال،  `ContosoCase.csv`.

5. اضغط على **مفتاح الإدخال Enter** لمتابعة تشغيل البرنامج النصي.

   يعرض البرنامج النصي تقدم إنشاء عمليات البحث وتشغيلها. عند اكتمال البرنامج النصي، فإنه يعود إلى المطالبة.

   ![عينة إخراج من تشغيل البرنامج النصي لإنشاء عمليات بحث توافق متعددة.](../media/37d59b0d-5f89-4dbc-9e2d-0e88e2ed7b4c.png)

## <a name="step-4-run-the-script-to-report-the-search-estimates"></a>الخطوة 4: تشغيل البرنامج النصي للإبلاغ عن تقديرات البحث

بعد إنشاء عمليات البحث، تتمثل الخطوة التالية في تشغيل برنامج نصي يعرض تقريرا بسيطا لعدد مرات البحث لكل عملية بحث تم إنشاؤها في الخطوة 3. يتضمن التقرير أيضا حجم النتائج لكل عملية بحث، وإجمالي عدد مرات الدخول والحجم الإجمالي لكافة عمليات البحث. عند تشغيل البرنامج النصي لإعداد التقارير، ستتم مطالبتك بمعرف مجموعة البحث واسم ملف CSV إذا كنت تريد حفظ التقرير إلى ملف CSV.

1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `SearchReport.ps1`. احفظ الملف إلى المجلد نفسه حيث حفظت الملفات الأخرى.

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

2. في Windows PowerShell، انتقل إلى المجلد حيث قمت بحفظ البرنامج النصي في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```Powershell
   .\SearchReport.ps1
   ```

3. في موجه **معرف مجموعة البحث** ، اكتب اسم مجموعة البحث، ثم اضغط على **مفتاح الإدخال Enter**؛ على سبيل المثال  `ContosoCase`. تذكر أن هذا الاسم حساس لحالة الأحرف، لذلك سيتعين عليك كتابته بنفس الطريقة التي كتبتها عند تشغيل البرنامج النصي في الخطوة 3.

4. في **مسار "ملف" لحفظ التقرير إلى ملف CSV (اتركه فارغا لعرض التقرير فقط)،** اكتب اسم ملف لمسار اسم الملف الكامل (بما في ذلك ملحق ملف .csv) إذا كنت تريد حفظ التقرير إلى ملف CSV. اسم ملف CSV، بما في ذلك ملحق ملف .csv. على سبيل المثال، يمكنك الكتابة  `ContosoCaseReport.csv` لحفظه في الدليل الحالي أو يمكنك الكتابة  `C:\Users\admin\OneDrive for Business\ContosoCase\ContosoCaseReport.csv` لحفظه في مجلد آخر. يمكنك أيضا ترك المطالبة فارغة لعرض التقرير ولكن لا يمكنك حفظه في ملف.

5. اضغط على **مفتاح الإدخال Enter**.

   يعرض البرنامج النصي تقدم إنشاء عمليات البحث وتشغيلها. عند اكتمال البرنامج النصي، يتم عرض التقرير.

   ![قم بتشغيل تقرير البحث لعرض تقديرات مجموعة البحث.](../media/3b5f2595-71d5-4a14-9214-fad156c981f8.png)

> [!NOTE]
> إذا تم تحديد نفس علبة البريد أو الموقع كموقع محتوى في أكثر من عملية بحث واحدة في مجموعة بحث، فقد يتضمن تقدير إجمالي النتائج في التقرير (لكل من عدد العناصر والحجم الإجمالي) نتائج للعناصر نفسها. وذلك لأنه سيتم حساب نفس رسالة البريد الإلكتروني أو المستند أكثر من مرة إذا كان يطابق الاستعلام لعمليات بحث مختلفة في مجموعة البحث.

## <a name="step-5-run-the-script-to-delete-the-searches"></a>الخطوة 5: تشغيل البرنامج النصي لحذف عمليات البحث

نظرا لأنك قد تقوم بإنشاء الكثير من عمليات البحث، فإن هذا البرنامج النصي الأخير يسهل حذف عمليات البحث التي أنشأتها في الخطوة 3 بسرعة. مثل البرامج النصية الأخرى، يطالبك هذا أيضا بمعرف مجموعة البحث. سيتم حذف كافة عمليات البحث باستخدام معرف مجموعة البحث في اسم البحث عند تشغيل هذا البرنامج النصي.

1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `DeleteSearches.ps1`. احفظ الملف إلى المجلد نفسه حيث حفظت الملفات الأخرى.

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

2. في Windows PowerShell، انتقل إلى المجلد حيث قمت بحفظ البرنامج النصي في الخطوة السابقة، ثم قم بتشغيل البرنامج النصي؛ على سبيل المثال:

   ```Powershell
   .\DeleteSearches.ps1
   ```

3. في موجه **معرف مجموعة البحث** ، اكتب اسم مجموعة البحث لعمليات البحث التي تريد حذفها، ثم اضغط على **مفتاح الإدخال Enter**؛ على سبيل المثال،  `ContosoCase`. تذكر أن هذا الاسم حساس لحالة الأحرف، لذلك سيتعين عليك كتابته بنفس الطريقة التي كتبتها عند تشغيل البرنامج النصي في الخطوة 3.

   يعرض البرنامج النصي اسم كل عملية بحث يتم حذفها.

   ![قم بتشغيل البرنامج النصي لحذف عمليات البحث في مجموعة البحث.](../media/9d97b9d6-a539-4d9b-a4e4-e99989144ec7.png)
