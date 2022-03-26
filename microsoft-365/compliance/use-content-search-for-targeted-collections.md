---
title: استخدام البحث في المحتوى للمجموعات المستهدفة
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
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: e3cbc79c-5e97-43d3-8371-9fbc398cd92e
ms.custom: seo-marvel-apr2020
description: استخدم بحث المحتوى في مركز التوافق في Microsoft 365 لتنفيذ مجموعة مستهدفة، تبحث عن عناصر في علبة بريد أو مجلد موقع معين.
ms.openlocfilehash: a72984e3d4363dfd5d89e6167621dd65c9d57653
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63566722"
---
# <a name="use-content-search-for-targeted-collections"></a>استخدام البحث في المحتوى للمجموعات المستهدفة

لا توفر أداة البحث في مركز التوافق في Microsoft 365 طريقة مباشرة في واجهة المستخدم للبحث في مجلدات معينة في علب بريد Exchange أو SharePoint OneDrive for Business ويب. ومع ذلك، من الممكن البحث في مجلدات معينة (تسمى مجموعة مستهدفة *) عن* طريق تحديد خاصية "اسم المجلد" للبريد الإلكتروني أو خاصية المسار (DocumentLink) للمواقع في بناء جملة استعلام البحث الفعلي. يكون استخدام "البحث في المحتوى" لتنفيذ مجموعة مستهدفة مفيدا عندما تكون واثقا من أن العناصر المستجيبة لقضية ما أو العناصر المميزة موجودة في علبة بريد أو مجلد موقع معين. يمكنك استخدام البرنامج النصي في هذه المقالة للحصول على "اسم المجلد" لمجلدات علب البريد أو المسار (DocumentLink) للمجلدات على موقع SharePoint OneDrive for Business ويب. بعد ذلك، يمكنك استخدام اسم المجلد أو المسار في استعلام البحث لإرجاع العناصر الموجودة في المجلد.

> [!NOTE]
> لإرجاع محتوى موجود في مجلد في موقع SharePoint أو OneDrive for Business، يستخدم البرنامج النصي في هذا الموضوع الخاصية مدارة في DocumentLink بدلا من الخاصية Path. إن الخاصية DocumentLink أكثر فعالية من الخاصية Path لأنها رجع كل المحتوى في مجلد، في حين أن الخاصية Path لن يتم إرجاع بعض ملفات الوسائط.

## <a name="before-you-run-a-targeted-collection"></a>قبل تشغيل مجموعة مستهدفة

- يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365 لتشغيل البرنامج النصي في الخطوة 1. لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md).

- يجب أيضا أن يتم تعيين دور "مستلمو البريد" في مؤسستك Exchange Online البريد. هذا مطلوب لتشغيل **أمر cmdlet Get-MailboxFolderStatistics** المضمن في البرنامج النصي. بشكل افتراضي، يتم تعيين دور مستلمي البريد إلى مجموعات دور إدارة المؤسسة وإدارة المستلمين في Exchange Online. لمزيد من المعلومات حول تعيين الأذونات في Exchange Online، راجع [إدارة أعضاء مجموعة الدور](/exchange/manage-role-group-members-exchange-2013-help). يمكنك أيضا إنشاء مجموعة دور مخصصة وتعيين دور مستلمي البريد إليها، ثم إضافة الأعضاء الذين يحتاجون إلى تشغيل البرنامج النصي في الخطوة 1. لمزيد من المعلومات، راجع [إدارة مجموعات الدور](/Exchange/permissions-exo/role-groups).

- يدعم البرنامج النصي في هذه المقالة المصادقة الحديثة. يمكنك استخدام البرنامج النصي كما هو إذا كنت Microsoft 365 أو Microsoft 365 سحابة القطاع الحكومي أخرى. إذا كنت أحد Office 365 ألمانيا، أو مؤسسة Microsoft 365 سحابة القطاع الحكومي عالية المستوى، أو مؤسسة Microsoft 365 DoD، يجب تحرير البرنامج النصي لتشغيله بنجاح. بشكل خاص`Connect-ExchangeOnline`، يجب تحرير الخط واستخدام المعلمة *ExchangeEnvironmentName* (والقيمة المناسبة لنوع مؤسستك) للاتصال Exchange Online PowerShell.  `Connect-IPPSSession` كما يجب تحرير السطر واستخدام معلمتي *ConnectionUri* و *AzureADAuthorizationEndpointUri* (والقيم المناسبة لنوع مؤسستك) للاتصال بمركز التوافق & PowerShell. لمزيد من المعلومات، راجع الأمثلة في الاتصال Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) [الاتصال إلى مركز التوافق & PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- في كل مرة تقوم فيها بتشغيل البرنامج النصي، يتم إنشاء جلسة PowerShell جديدة عن بعد. وهذا يعني أنه يمكنك استخدام كل جلسات PowerShell البعيدة المتوفرة لك. لمنع حدوث ذلك، قم بتشغيل الأمر التالي لقطع اتصال جلسات PowerShell النشطة البعيدة.

  ```powershell
  Get-PSSession | Remove-PSSession
  ```

    لمزيد من المعلومات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي من البرنامج النصي هو عرض قائمة بملفات مجلد علبة البريد أو مسارات الموقع التي يمكن استخدامها في بناء جملة استعلام البحث في "البحث في المحتوى" لتنفيذ مجموعة مستهدفة.

- البرنامج النصي النموذجي الموفر في هذا الموضوع غير معتمد ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرنامج النصي النموذجي AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام أو أداء البرنامج النصي النموذجي والوثائق معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها المسؤولية عن أي أضرار أيا كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام البرامج النصية أو الوثائق العينة أو عدم القدرة على استخدامها،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>الخطوة 1: تشغيل البرنامج النصي للحصول على قائمة بالمجلدات لعلبة بريد أو موقع

سيرجع البرنامج النصي الذي تقوم بتشغيله في هذه الخطوة الأولى قائمة بمجلدات علب البريد أو SharePoint ومجلدات OneDrive for Business، وملفات أو مسار المجلد المناظر لكل مجلد. عند تشغيل هذا البرنامج النصي، سيطالبك بالمعلومات التالية.

- **عنوان البريد الإلكتروني أو عنوان URL** الموقع: اكتب عنوان بريد إلكتروني لمرسل الرسالة لإرجاع قائمة بمجلدات Exchange البريد وملفات المجلدات. أو اكتب عنوان URL لموقع SharePoint أو موقع OneDrive for Business لإرجاع قائمة مسارات للموقع المحدد. فيما يلي بعض الأمثلة:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive for Business**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **بيانات اعتماد المستخدم**: سيستخدم البرنامج النصي بيانات الاعتماد للاتصال Exchange Online PowerShell أو الأمان & مركز التوافق PowerShell باستخدام المصادقة الحديثة. كما تم شرحه مسبقا، يجب أن يتم تعيين الأذونات المناسبة لك لتشغيل هذا البرنامج النصي بنجاح.

لعرض قائمة بمجلدات علبة البريد أو أسماء ارتباطات مستندات الموقع (المسار):

1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `GetFolderSearchParameters.ps1`.

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the Microsoft 365 compliance center.            #
   # The script will then:                                            #
   #    * If an email address is supplied: list the folders for the target mailbox.            #
   #    * If a SharePoint or OneDrive for Business site is supplied: list the documentlinks (folder paths) #
   #    * for the site.                                                                                    #
   #    * In both cases, the script supplies the correct search properties (folderid: or documentlink:)    #
   #      appended to the folder ID or documentlink to use in a Content Search.                #
   # Notes:                                                #
   #    * For SharePoint and OneDrive for Business, the paths are searched recursively; this means the     #
   #      the current folder and all sub-folders are searched.                        #
   #    * For Exchange, only the specified folder will be searched; this means sub-folders in the folder    #
   #      will not be searched.  To search sub-folders, you need to use the specify the folder ID for    #
   #      each sub-folder that you want to search.                                #
   #    * For Exchange, only folders in the user's primary mailbox will be returned by the script.        #
   #########################################################################################################
   # Collect the target email address or SharePoint Url
   $addressOrSite = Read-Host "Enter an email address or a URL for a SharePoint or OneDrive for Business site"
   # Authenticate with Exchange Online and the Microsoft 365 compliance center (Exchange Online Protection - EOP)
   if ($addressOrSite.IndexOf("@") -ige 0)
   {
      # List the folder Ids for the target mailbox
      $emailAddress = $addressOrSite
      # Connect to Exchange Online PowerShell
      if (!$ExoSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-ExchangeOnline -ShowBanner:$false -CommandName Get-MailboxFolderStatistics
      }
      $folderQueries = @()
      $folderStatistics = Get-MailboxFolderStatistics $emailAddress
      foreach ($folderStatistic in $folderStatistics)
      {
          $folderId = $folderStatistic.FolderId;
          $folderPath = $folderStatistic.FolderPath;
          $encoding= [System.Text.Encoding]::GetEncoding("us-ascii")
          $nibbler= $encoding.GetBytes("0123456789ABCDEF");
          $folderIdBytes = [Convert]::FromBase64String($folderId);
          $indexIdBytes = New-Object byte[] 48;
          $indexIdIdx=0;
          $folderIdBytes | select -skip 23 -First 24 | %{$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -shr 4];$indexIdBytes[$indexIdIdx++]=$nibbler[$_ -band 0xF]}
          $folderQuery = "folderid:$($encoding.GetString($indexIdBytes))";
          $folderStat = New-Object PSObject
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderPath -Value $folderPath
          Add-Member -InputObject $folderStat -MemberType NoteProperty -Name FolderQuery -Value $folderQuery
          $folderQueries += $folderStat
      }
      Write-Host "-----Exchange Folders-----"
      $folderQueries |ft
   }
   elseif ($addressOrSite.IndexOf("http") -ige 0)
   {
      $searchName = "SPFoldersSearch"
      $searchActionName = "SPFoldersSearch_Preview"
      # List the folders for the SharePoint or OneDrive for Business Site
      $siteUrl = $addressOrSite
      # Connect to Security & Compliance Center PowerShell
      if (!$SccSession)
      {
          Import-Module ExchangeOnlineManagement
          Connect-IPPSSession
      }
      # Clean-up, if the script was aborted, the search we created might not have been deleted.  Try to do so now.
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
      # Create a Content Search against the SharePoint Site or OneDrive for Business site and only search for folders; wait for the search to complete
      $complianceSearch = New-ComplianceSearch -Name $searchName -ContentMatchQuery "contenttype:folder" -SharePointLocation $siteUrl
      Start-ComplianceSearch $searchName
      do{
          Write-host "Waiting for search to complete..."
          Start-Sleep -s 5
          $complianceSearch = Get-ComplianceSearch $searchName
      }while ($complianceSearch.Status -ne 'Completed')
      if ($complianceSearch.Items -gt 0)
      {
          # Create a Compliance Search Action and wait for it to complete. The folders will be listed in the .Results parameter
          $complianceSearchAction = New-ComplianceSearchAction -SearchName $searchName -Preview
          do
          {
              Write-host "Waiting for search action to complete..."
              Start-Sleep -s 5
              $complianceSearchAction = Get-ComplianceSearchAction $searchActionName
          }while ($complianceSearchAction.Status -ne 'Completed')
          # Get the results and print out the folders
          $results = $complianceSearchAction.Results
          $matches = Select-String "Data Link:.+[,}]" -Input $results -AllMatches
          foreach ($match in $matches.Matches)
          {
              $rawUrl = $match.Value
              $rawUrl = $rawUrl -replace "Data Link: " -replace "," -replace "}"
              Write-Host "DocumentLink:""$rawUrl"""
          }
      }
      else
      {
          Write-Host "No folders were found for $siteUrl"
      }
      Remove-ComplianceSearch $searchName -Confirm:$false -ErrorAction 'SilentlyContinue'
   }
   else
   {
      Write-Error "Couldn't recognize $addressOrSite as an email address or a site URL"
   }
   ```

2. على الكمبيوتر المحلي، افتح Windows PowerShell واذهب إلى المجلد حيث حفظت البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. أدخل المعلومات التي يطالبك بها البرنامج النصي.

    يعرض البرنامج النصي قائمة بمجلدات علبة البريد أو مجلدات الموقع للمستخدم المحدد. اترك هذه النافذة مفتوحة بحيث يمكنك نسخ اسم ارتباط مستند أو اسم مجلد أو اسم مجلد ولصقه في استعلام بحث في الخطوة 2.

    > [!TIP]
    > بدلا من عرض قائمة المجلدات على شاشة الكمبيوتر، يمكنك إعادة توجيه إخراج البرنامج النصي إلى ملف نصي. سيتم حفظ هذا الملف في المجلد حيث يوجد البرنامج النصي. على سبيل المثال، لإعادة توجيه إخراج البرنامج النصي إلى ملف نصي، قم بتشغيل الأمر التالي في الخطوة 3:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` بعد ذلك، يمكنك نسخ مجلد أو ارتباط مستند من الملف لاستخدامه في استعلام بحث.

### <a name="script-output-for-mailbox-folders"></a>إخراج البرنامج النصي لمجلدات علب البريد

إذا كنت تحصل على "لملفات البريد"، يتصل البرنامج النصي ب Exchange Online PowerShell، ويدير الأمر **cmdlet Get-MailboxFolderStatisics**، ثم يعرض قائمة المجلدات من علبة البريد المحددة. لكل مجلد في علبة البريد، يعرض البرنامج النصي اسم المجلد في عمود **FolderPath** وملفات الما بعد ذلك في العمود **FolderQuery** . بالإضافة إلى ذلك، يضيف البرنامج النصيبادة **المجلدمزيد** (وهو اسم خاصية علبة البريد) إلى "معريف المجلد". نظرا لأن **الخاصية folderid** هي خاصية قابلة للبحث، يمكنك استخدامها  `folderid:<folderid>` في استعلام بحث في الخطوة 2 للبحث في هذا المجلد. 

> [!IMPORTANT]
> يتضمن البرنامج النصي في هذه المقالة منطق ترميز يحول قيم "المرجع" لمجلد من 64 حرفا التي يتم إرجاعها بواسطة **Get-MailboxFolderStatistics** إلى التنسيق نفسه الذي يحتوي على 48 حرفا الذي يتم فهرسته للبحث. إذا قمت فقط بتشغيل **الأمر cmdlet Get-MailboxFolderStatistics** في PowerShell للحصول على "اسم المجلد" (بدلا من تشغيل البرنامج النصي في هذه المقالة)، سيفشل استعلام البحث الذي يستخدم قيمة "Id" هذه المجلد. يجب تشغيل البرنامج النصي للحصول على "لمعانات المجلدات" التي تم تنسيقها بشكل صحيح التي يمكن استخدامها في "البحث في المحتوى".

فيما يلي مثال على الإخراج الذي تم إرجاعه بواسطة البرنامج النصي لمجلدات علبة البريد.

![مثال لقائمة مجلدات علبة البريد وملفات المرجع بواسطة البرنامج النصي.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

يوضح المثال في الخطوة 2 الاستعلام المستخدم للبحث في المجلد الفرعي عمليات الازدحام في مجلد العناصر القابلة لاسترداد المستخدم.

### <a name="script-output-for-site-folders"></a>إخراج البرنامج النصي لمجلدات الموقع

إذا كنت تحصل على مسار الخاصية **documentlink** من مواقع SharePoint أو OneDrive for Business، يتصل البرنامج النصي ب Security & Compliance PowerShell، وينشئ بحث محتوى جديد يبحث في الموقع عن مجلدات، ثم يعرض قائمة بالمجلدات الموجودة في الموقع المحدد. يعرض البرنامج النصي اسم كل مجلد ويضيفبادة ارتباط **المستند** إلى عنوان URL للمجلد. نظرا لأن **خاصية documentlink** `documentlink:<path>` هي خاصية قابلة للبحث، فسوف تستخدم الخاصية:قيمة زوج في استعلام بحث في الخطوة 2 للبحث في هذا المجلد. يعرض البرنامج النصي 100 مجلد موقع كحد أقصى. إذا كان هناك أكثر من 100 مجلد موقع، يتم عرض المجلدات الجديدة.

فيما يلي مثال على الإخراج الذي تم إرجاعه بواسطة البرنامج النصي لمجلدات الموقع.

![مثال لقائمة أسماء ارتباطات المستندات لمجلدات المواقع التي تم إرجاعها بواسطة البرنامج النصي.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>الخطوة 2: استخدام مجلد أو ارتباط مستند لتنفيذ مجموعة مستهدفة

بعد تشغيل البرنامج النصي لجمع قائمة بملفات تعريف المجلد أو ارتباطات المستندات لمستخدم معين، الخطوة التالية هي الانتقال إلى مركز التوافق في Microsoft 365 وإنشاء بحث محتوى جديد للبحث في مجلد معين. سوف تستخدم زوج الخاصية or:value في استعلام البحث الذي تقوم بتكوينه في المربع الكلمة الأساسية البحث في المحتوى (أو كقيمة لمعلمة *ContentMatchQuery* إذا كنت تستخدم **cmdlet البحث في New-ComplianceSearch**).`folderid:<folderid>` `documentlink:<path>` يمكنك دمج الخاصية  `folderid` OR  `documentlink` مع معلمات البحث الأخرى أو شروط البحث. إذا قمت بتضمين الخاصية  `folderid` OR  `documentlink` فقط في الاستعلام، فإن البحث سيرجع كل العناصر الموجودة في المجلد المحدد.

1. انتقل إلى <https://compliance.microsoft.com> الحساب وبيانات الاعتماد التي استخدمتها لتشغيل البرنامج النصي في الخطوة 1، ثم سجل الدخول.

2. في الجزء الأيسر من مركز التوافق، انقر فوق **إظهار كل** >  البحث، ثم انقر فوق **بحث جديد**.

3. في المربع **كلمات** أساسية، اللصق أو `folderid:<folderid>`  `documentlink:<path>/*` القيمة التي تم إرجاعها بواسطة البرنامج النصي في الخطوة 1.

    على سبيل المثال، سيبحث الاستعلام في لقطة الشاشة التالية عن أي عنصر في المجلد الفرعي "إزالة" في مجلد "العناصر القابلة لاسترداد" الخاص بالمستخدم ( `folderid` تظهر قيمة الخاصية للمجلد الفرعي "إزالة" في لقطة الشاشة في الخطوة 1):

    ![اللصق في مجلد أو ارتباط المستند إلى مربع الكلمة الأساسية لاستعلام البحث.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > تتطلب عمليات البحث في ارتباطات المستندات استخدام زائد  `asterisk '/*'`.  

4. ضمن **المواقع**، حدد **مواقع محددة** ثم انقر فوق **تعديل**.

5. يمكنك القيام بوا واحد مما يلي، استنادا إلى ما إذا كنت تبحث في مجلد علبة بريد أو مجلد موقع:

    - إلى **Exchange** الإلكتروني، انقر فوق اختيار المستخدمين  أو المجموعات أو الفرق، ثم أضف علبة البريد نفسها التي حددتها عند تشغيل البرنامج النصي في الخطوة 1.

      أو

    - إلى **SharePoint**، انقر فوق اختيار مواقع ثم أضف  عنوان URL الموقع نفسه الذي حددته عند تشغيل البرنامج النصي في الخطوة 1.

6. بعد حفظ موقع المحتوى للبحث، انقر فوق **حفظ &،** وا اكتب اسما للبحث في المحتوى، ثم انقر فوق حفظ لبدء عملية البحث  في المجموعة المستهدفة.

### <a name="examples-of-search-queries-for-targeted-collections"></a>أمثلة على استعلامات البحث للمجموعات المستهدفة

فيما يلي بعض الأمثلة حول استخدام الخاصية  `folderid` و  `documentlink` في استعلام البحث لتنفيذ مجموعة مستهدفة. يتم استخدام العنصر النائب لتوفير  `folderid:<folderid>`  `documentlink:<path>` المساحة.

- يبحث هذا المثال في ثلاثة مجلدات مختلفة لعلب البريد. يمكنك استخدام بناء جملة استعلام مماثل للبحث في المجلدات المخفية في مجلد "العناصر القابلة للاسترداد" الخاص بالمستخدم.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- يبحث هذا المثال في مجلد علبة البريد عن العناصر التي تحتوي على عبارة دقيقة.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- يبحث هذا المثال في مجلد موقع (وأي مجلدات فرعية) عن المستندات التي تحتوي على الأحرف "NDA" في العنوان.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- يبحث هذا المثال في مجلد موقع (وأي مجلد فرعي) عن المستندات التي تم تغييرها ضمن نطاق تاريخ.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>معلومات إضافية

ضع الأمور التالية في الاعتبار عند استخدام البرنامج النصي في هذه المقالة لتنفيذ المجموعات المستهدفة.

- لا يزيل البرنامج النصي أي مجلدات من النتائج. وبالتالي، قد تكون بعض المجلدات المدرجة في النتائج غير قابلة لل البحث (أو إرجاع عناصر صفرية) لأنها تحتوي على محتوى تم إنشاؤه بواسطة النظام أو لأنها تحتوي فقط على مجلدات فرعية وليس على عناصر علبة بريد.

- يقوم هذا البرنامج النصي بإرجاع معلومات المجلد لعلبة البريد الأساسية الخاصة بالمستخدم فقط. ولا يقوم بإرجاع معلومات حول المجلدات في علبة بريد الأرشيف الخاصة بالمستخدم. لإرجاع معلومات حول المجلدات في علبة بريد الأرشيف الخاصة بالمستخدم، يمكنك تحرير البرنامج النصي. للقيام بذلك، قم بتغيير السطر إلى `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` ثم احفظ البرنامج النصي الذي تم تحريره ثم قم بتشغيله. سيرجع هذا التغيير مجلدات المجلدات والمجلدات الفرعية في علبة بريد الأرشيف الخاصة بالمستخدم. للبحث في علبة بريد الأرشيف بكاملها، يمكنك توصيل كل خاصية "اسم المجلد":أزواج `OR` القيم بعامل تشغيل في استعلام بحث.

- عند البحث في مجلدات علب البريد، سيتم البحث في المجلد المحدد فقط ( `folderid` المعرف بواسطة الخاصية الخاصة به)، ولن يتم البحث في المجلدات الفرعية. للبحث في المجلدات الفرعية، ستحتاج إلى استخدام "معرّف المجلد" للمجلد الفرعي الذي تريد البحث فيه.

- عند البحث في مجلدات الموقع، سيتم البحث في المجلد (المعرف بواسطة الخاصية `documentlink` الخاصة به) وجميع المجلدات الفرعية.

- `folderid` عند تصدير نتائج عملية بحث قمت بتحديد الخاصية فيها فقط في استعلام البحث، يمكنك اختيار خيار التصدير الأول، "كل العناصر، باستثناء العناصر التي لها تنسيق غير م التعرف عليه، مشفرة أو لم يتم فهرستها لأسباب أخرى." سيتم دائما تصدير كل العناصر الموجودة في المجلد بغض النظر عن حالة الفهرسة الخاصة بها لأنه يتم دائما فهرسة اسم المجلد.
