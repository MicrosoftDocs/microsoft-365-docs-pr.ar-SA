---
title: استخدام البحث عن المحتوى للمجموعات المستهدفة
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: استخدم البحث في المحتوى في مدخل توافق Microsoft Purview لتنفيذ مجموعة مستهدفة، والتي تبحث عن عناصر في علبة بريد معينة أو مجلد موقع معين.
ms.openlocfilehash: 224da8e651599d1d007684a069b0dbb9d30a6119
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015529"
---
# <a name="use-content-search-for-targeted-collections"></a>استخدام البحث عن المحتوى للمجموعات المستهدفة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

لا توفر أداة البحث في المحتوى في مدخل توافق Microsoft Purview طريقة مباشرة في واجهة المستخدم للبحث في مجلدات معينة في علب بريد Exchange أو SharePoint ومواقع OneDrive for Business. ومع ذلك، من الممكن البحث في مجلدات معينة (تسمى *مجموعة مستهدفة*) عن طريق تحديد خاصية معرف المجلد للبريد الإلكتروني أو المسار (DocumentLink) للمواقع في بناء جملة استعلام البحث الفعلي. يعد استخدام "البحث عن المحتوى" لتنفيذ مجموعة مستهدفة مفيدا عندما تكون واثقا من وجود العناصر التي تستجيب لحالة أو عناصر مميزة في علبة بريد معينة أو مجلد موقع معين. يمكنك استخدام البرنامج النصي في هذه المقالة للحصول على معرف المجلد لمجلدات علبة البريد أو المسار (DocumentLink) للمجلدات الموجودة على موقع SharePoint OneDrive for Business. ثم يمكنك استخدام معرف المجلد أو المسار في استعلام بحث لإرجاع العناصر الموجودة في المجلد.

> [!NOTE]
> لإرجاع المحتوى الموجود في مجلد في موقع SharePoint أو OneDrive for Business، يستخدم البرنامج النصي في هذا الموضوع الخاصية المدارة في DocumentLink بدلا من خاصية المسار. تعد الخاصية DocumentLink أكثر قوة من خاصية "المسار" لأنها ستقوم بإرجاع كافة المحتويات في مجلد، في حين أن خاصية "المسار" لن ترجع بعض ملفات الوسائط.

## <a name="before-you-run-a-targeted-collection"></a>قبل تشغيل مجموعة مستهدفة

- يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل التوافق لتشغيل البرنامج النصي في الخطوة 1. لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md).

- يجب أيضا تعيين دور مستلمي البريد في مؤسستك Exchange Online. هذا مطلوب لتشغيل **Get-MailboxFolderStatistics** cmdlet، المضمن في البرنامج النصي. بشكل افتراضي، يتم تعيين دور مستلمي البريد إلى مجموعات دور إدارة المؤسسة وإدارة المستلمين في Exchange Online. لمزيد من المعلومات حول تعيين الأذونات في Exchange Online، راجع [إدارة أعضاء مجموعة الأدوار](/exchange/manage-role-group-members-exchange-2013-help). يمكنك أيضا إنشاء مجموعة أدوار مخصصة وتعيين دور مستلمي البريد إليها، ثم إضافة الأعضاء الذين يحتاجون إلى تشغيل البرنامج النصي في الخطوة 1. لمزيد من المعلومات، راجع [إدارة مجموعات الأدوار](/Exchange/permissions-exo/role-groups).

- يدعم البرنامج النصي في هذه المقالة المصادقة الحديثة. يمكنك استخدام البرنامج النصي كما هو إذا كنت Microsoft 365 أو مؤسسة Microsoft 365 سحابة القطاع الحكومي. إذا كنت مؤسسة Office 365 ألمانيا أو مؤسسة Microsoft 365 سحابة القطاع الحكومي عالية أو مؤسسة Microsoft 365 DoD، فستضطر إلى تحرير البرنامج النصي لتشغيله بنجاح. وبشكل خاص، يجب عليك تحرير السطر `Connect-ExchangeOnline` واستخدام معلمة *ExchangeEnvironmentName* (والقيمة المناسبة لنوع مؤسستك) للاتصال Exchange Online PowerShell.  أيضا، يجب عليك تحرير السطر `Connect-IPPSSession` واستخدام معلمات *ConnectionUri* *وAzureADAuthorizationEndpointUri* (والقيم المناسبة لنوع مؤسستك) للاتصال ب Security & Compliance PowerShell. لمزيد من المعلومات، راجع الأمثلة في [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-without-using-mfa) [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- في كل مرة تقوم فيها بتشغيل البرنامج النصي، يتم إنشاء جلسة PowerShell بعيدة جديدة. وهذا يعني أنه يمكنك استخدام جميع جلسات PowerShell البعيدة المتوفرة لك. لمنع حدوث ذلك، قم بتشغيل الأوامر التالية لقطع اتصال جلسات عمل PowerShell البعيدة النشطة.

  ```powershell
  Get-PSSession | Remove-PSSession; Disconnect-ExchangeOnline
  ```

    لمزيد من المعلومات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي من البرنامج النصي هو عرض قائمة بسرعة بمعرفات مجلد علبة البريد أو مسارات الموقع التي يمكن استخدامها في بناء جملة استعلام البحث في البحث عن المحتوى لتنفيذ مجموعة مستهدفة.

- البرنامج النصي النموذجي المتوفر في هذا الموضوع غير معتمد ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نموذج البرنامج النصي AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نموذج البرنامج النصي والوثائق معك. لن تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناتجة عن استخدام نماذج البرامج النصية أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site"></a>الخطوة 1: تشغيل البرنامج النصي للحصول على قائمة بالمجلدات الخاصة بعلبة بريد أو موقع

سيقوم البرنامج النصي الذي تقوم بتشغيله في هذه الخطوة الأولى بإرجاع قائمة بمجلدات علبة البريد أو SharePoint ومجلدات OneDrive for Business ومعرف المجلد أو المسار المطابق لكل مجلد. عند تشغيل هذا البرنامج النصي، سيطالبك بالمعلومات التالية.

- **عنوان البريد الإلكتروني أو عنوان URL للموقع**: اكتب عنوان بريد إلكتروني للوصي لإرجاع قائمة بمجلدات علبة البريد Exchange ومعرف المجلد. أو اكتب عنوان URL لموقع SharePoint أو موقع OneDrive for Business لإرجاع قائمة بالمسارات للموقع المحدد. فيما يلي بعض الأمثلة:

  - **Exchange**:`stacig@contoso.onmicrosoft.com`

  - **SharePoint**:`https://contoso.sharepoint.com/sites/marketing`

  - **OneDrive for Business**:`https://contoso-my.sharepoint.com/personal/stacig_contoso_onmicrosoft_com`

- **بيانات اعتماد المستخدم**: سيستخدم البرنامج النصي بيانات الاعتماد للاتصال Exchange Online PowerShell أو Security & Compliance PowerShell باستخدام المصادقة الحديثة. كما هو موضح سابقا، يجب تعيين الأذونات المناسبة لتشغيل هذا البرنامج النصي بنجاح.

لعرض قائمة بمجلدات علبة البريد أو أسماء ارتباطات مستندات الموقع (المسار):

1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `GetFolderSearchParameters.ps1`.

   ```powershell
   #########################################################################################################
   # This PowerShell script will prompt you for:                                #
   #    * Admin credentials for a user who can run the Get-MailboxFolderStatistics cmdlet in Exchange    #
   #      Online and who is an eDiscovery Manager in the compliance portal.            #
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
   # Authenticate with Exchange Online and the compliance portal (Exchange Online Protection - EOP)
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
      # Connect to Security & Compliance PowerShell
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

2. على الكمبيوتر المحلي، افتح Windows PowerShell وانتقل إلى المجلد حيث حفظت البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\GetFolderSearchParameters.ps1
   ```

4. أدخل المعلومات التي يطالبك البرنامج النصي بها.

    يعرض البرنامج النصي قائمة بمجلدات علب البريد أو مجلدات الموقع للمستخدم المحدد. اترك هذه النافذة مفتوحة بحيث يمكنك نسخ معرف مجلد أو اسم ارتباط مستند ولصقه في استعلام بحث في الخطوة 2.

    > [!TIP]
    > بدلا من عرض قائمة بالمجلدات على شاشة الكمبيوتر، يمكنك إعادة توجيه إخراج البرنامج النصي إلى ملف نصي. سيتم حفظ هذا الملف في المجلد حيث يوجد البرنامج النصي. على سبيل المثال، لإعادة توجيه إخراج البرنامج النصي إلى ملف نصي، قم بتشغيل الأمر التالي في الخطوة 3:  `.\GetFolderSearchParameters.ps1 > StacigFolderIds.txt` بعد ذلك يمكنك نسخ معرف مجلد أو ارتباط مستند من الملف لاستخدامه في استعلام البحث.

### <a name="script-output-for-mailbox-folders"></a>إخراج البرنامج النصي لمجلدات علبة البريد

إذا كنت تحصل على معرفات مجلد علبة البريد، يتصل البرنامج النصي Exchange Online PowerShell، ويشغل **Get-MailboxFolderStatisics** cmdlet، ثم يعرض قائمة المجلدات من علبة البريد المحددة. لكل مجلد في علبة البريد، يعرض البرنامج النصي اسم المجلد في عمود **FolderPath** ومعرف المجلد في العمود **FolderQuery** . بالإضافة إلى ذلك، يضيف البرنامج النصي بادئة **folderId** (وهو اسم خاصية علبة البريد) إلى معرف المجلد. لأن خاصية **folderid** هي خاصية قابلة للبحث، ستستخدمها  `folderid:<folderid>` في استعلام بحث في الخطوة 2 للبحث في هذا المجلد. 

> [!IMPORTANT]
> يتضمن البرنامج النصي في هذه المقالة منطق الترميز الذي يحول قيم معرف المجلد المكونة من 64 حرفا التي يتم إرجاعها بواسطة **Get-MailboxFolderStatistics** إلى تنسيق 48 حرفا نفسه الذي تتم فهرسته للبحث. إذا قمت بتشغيل **الأمر Get-MailboxFolderStatistics** cmdlet في PowerShell للحصول على معرف مجلد (بدلا من تشغيل البرنامج النصي في هذه المقالة)، فسيفشل استعلام بحث يستخدم قيمة معرف المجلد هذه. يجب تشغيل البرنامج النصي للحصول على معرفات المجلد المنسقة تنسيقا صحيحا التي يمكن استخدامها في البحث عن المحتوى.

فيما يلي مثال على الإخراج الذي تم إرجاعه بواسطة البرنامج النصي لمجلدات علبة البريد.

![مثال لقائمة مجلدات علبة البريد ومعرف المجلدات التي تم إرجاعها بواسطة البرنامج النصي.](../media/cd739207-eb84-4ebf-a03d-703f3d3a797d.png)

يوضح المثال في الخطوة 2 الاستعلام المستخدم للبحث في المجلد الفرعي "عمليات الإزالة" في مجلد "العناصر القابلة للاسترداد" الخاص بالمستخدم.

### <a name="script-output-for-site-folders"></a>إخراج البرنامج النصي لمجلدات الموقع

إذا كنت تحصل على مسار خاصية **ارتباط المستند** من مواقع SharePoint أو OneDrive for Business، يتصل البرنامج النصي ب Security & Compliance PowerShell، ويقوم بإنشاء "بحث محتوى" جديد يبحث في الموقع عن المجلدات، ثم يعرض قائمة بالمجلدات الموجودة في الموقع المحدد. يعرض البرنامج النصي اسم كل مجلد ويضيف بادئة **ارتباط المستند** إلى عنوان URL للمجلد. نظرا لأن خاصية **ارتباط المستند** هي خاصية قابلة للبحث، فستستخدم `documentlink:<path>` زوج الخاصية:القيمة في استعلام بحث في الخطوة 2 للبحث في هذا المجلد. يعرض البرنامج النصي 100 مجلد موقع كحد أقصى. إذا كان هناك أكثر من 100 مجلد موقع، يتم عرض المجلدات الأحدث.

فيما يلي مثال على الإخراج الذي تم إرجاعه بواسطة البرنامج النصي لمجلدات الموقع.

![مثال لقائمة أسماء ارتباطات المستندات لمجلدات الموقع التي تم إرجاعها بواسطة البرنامج النصي.](../media/519e8347-7365-4067-af78-96c465dc3d15.png)

## <a name="step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection"></a>الخطوة 2: استخدام معرف مجلد أو ارتباط مستند لتنفيذ مجموعة مستهدفة

بعد تشغيل البرنامج النصي لتجميع قائمة بمعرفات المجلدات أو ارتباطات المستندات لمستخدم معين، الخطوة التالية للانتقال إلى مدخل التوافق وإنشاء بحث محتوى جديد للبحث في مجلد معين. ستستخدم  `folderid:<folderid>` زوج الخاصية أو  `documentlink:<path>` الخاصية:value في استعلام البحث الذي قمت بتكوينه في مربع الكلمة الأساسية للبحث في المحتوى (أو كقيمة للمعلمة  *ContentMatchQuery*  إذا كنت تستخدم **New-ComplianceSearch** cmdlet). يمكنك دمج الخاصية  `folderid` أو  `documentlink` معلمات البحث الأخرى أو شروط البحث. إذا قمت بتضمين الخاصية  `folderid` أو  `documentlink` الخاصية فقط في الاستعلام، فسيرجع البحث كافة العناصر الموجودة في المجلد المحدد.

1. انتقل إلى <https://compliance.microsoft.com> تسجيل الدخول باستخدام الحساب وبيانات الاعتماد التي استخدمتها لتشغيل البرنامج النصي في الخطوة 1.

2. في الجزء الأيمن من مركز التوافق، انقر فوق **"إظهار كل** > **البحث في المحتوى**"، ثم انقر فوق **"بحث جديد**".

3. في مربع **الكلمات الأساسية** ، الصق `folderid:<folderid>` القيمة أو  `documentlink:<path>/*` التي تم إرجاعها بواسطة البرنامج النصي في الخطوة 1.

    على سبيل المثال، سيبحث الاستعلام في لقطة الشاشة التالية عن أي عنصر في المجلد الفرعي "عمليات الإزالة" في مجلد "العناصر القابلة للاسترداد" الخاص بالمستخدم (تظهر قيمة `folderid` الخاصية للمجلد الفرعي "عمليات الإزالة" في لقطة الشاشة في الخطوة 1):

    ![الصق معرف المجلد أو ارتباط المستند في مربع الكلمة الأساسية لاستعلام البحث.](../media/FolderIDSearchQuery.png)
    > [!IMPORTANT]
    > تتطلب عمليات البحث في ارتباط المستند استخدام عملية زائدة  `asterisk '/*'`.  

4. ضمن **"المواقع**"، حدد **مواقع محددة** ثم انقر فوق **"تعديل**".

5. قم بأحد الإجراءات التالية، استنادا إلى ما إذا كنت تبحث في مجلد علبة بريد أو مجلد موقع:

    - إلى جانب **Exchange البريد الإلكتروني**، انقر فوق **اختيار مستخدمين أو مجموعات أو فرق** ثم أضف علبة البريد نفسها التي حددتها عند تشغيل البرنامج النصي في الخطوة 1.

      او

    - إلى جانب **مواقع SharePoint**، انقر فوق **"اختيار المواقع**" ثم أضف نفس URL الموقع الذي حددته عند تشغيل البرنامج النصي في الخطوة 1.

6. بعد حفظ موقع المحتوى للبحث فيه، انقر فوق **"حفظ & تشغيل**"، واكتب اسما ل "البحث في المحتوى"، ثم انقر فوق **"حفظ"** لبدء عملية البحث عن المجموعة المستهدفة.

### <a name="examples-of-search-queries-for-targeted-collections"></a>أمثلة على استعلامات البحث للمجموعات المستهدفة

فيما يلي بعض الأمثلة على استخدام والخصائص  `folderid`  `documentlink` في استعلام بحث لتنفيذ مجموعة مستهدفة. يتم استخدام العناصر النائبة  `folderid:<folderid>` لتوفير المساحة  `documentlink:<path>` .

- يبحث هذا المثال في ثلاثة مجلدات مختلفة لعلب البريد. يمكنك استخدام بناء جملة استعلام مماثل للبحث في المجلدات المخفية في مجلد "العناصر القابلة للاسترداد" الخاص بالمستخدم.

  ```powershell
  folderid:<folderid> OR folderid:<folderid> OR folderid:<folderid>
  ```

- يبحث هذا المثال في مجلد علبة البريد عن العناصر التي تحتوي على عبارة محددة.

  ```powershell
  folderid:<folderid> AND "Contoso financial results"
  ```

- يبحث هذا المثال في مجلد موقع (وأي مجلدات فرعية) عن المستندات التي تحتوي على الأحرف "NDA" في العنوان.

  ```powershell
  documentlink:"<path>/*" AND filename:nda
  ```

- يبحث هذا المثال في مجلد موقع (وأي مجلد فرعي) عن المستندات التي تم تغييرها داخل نطاق تاريخ.

  ```powershell
  documentlink:"<path>/*" AND (lastmodifiedtime>=01/01/2017 AND lastmodifiedtime<=01/21/2017)
  ```

## <a name="more-information"></a>معلومات إضافية

ضع الأشياء التالية في الاعتبار عند استخدام البرنامج النصي في هذه المقالة لتنفيذ المجموعات المستهدفة.

- لا يزيل البرنامج النصي أي مجلدات من النتائج. لذلك قد تكون بعض المجلدات المدرجة في النتائج غير قابلة للبحث (أو إرجاع عناصر صفرية) لأنها تحتوي على محتوى تم إنشاؤه بواسطة النظام أو لأنها تحتوي فقط على مجلدات فرعية وليس عناصر علبة البريد.

- يقوم هذا البرنامج النصي بإرجاع معلومات المجلد لعل بريد المستخدم الأساسي فقط. لا يقوم بإرجاع معلومات حول المجلدات في علبة بريد الأرشيف الخاصة بالمستخدم. لإرجاع معلومات حول المجلدات في علبة بريد الأرشيف الخاصة بالمستخدم، يمكنك تحرير البرنامج النصي. للقيام بذلك، قم بتغيير السطر `$folderStatistics = Get-MailboxFolderStatistics $emailAddress` إلى `$folderStatistics = Get-MailboxFolderStatistics $emailAddress -Archive` ثم احفظ البرنامج النصي الذي تم تحريره وقم بتشغيله. سيؤدي هذا التغيير إلى إرجاع معرفات المجلد للمجلدات والمجلدات الفرعية في علبة بريد الأرشيف الخاصة بالمستخدم. للبحث في علبة بريد الأرشيف بأكملها، يمكنك توصيل كافة خصائص معرف المجلد:أزواج القيم بعامل `OR` تشغيل في استعلام بحث.

- عند البحث في مجلدات علبة البريد، سيتم البحث في المجلد المحدد فقط (الذي تم تعريفه بواسطة الخاصية `folderid` الخاصة به)، ولن يتم البحث في المجلدات الفرعية. للبحث في المجلدات الفرعية، تحتاج إلى استخدام معرف المجلد للمجلد الفرعي الذي تريد البحث فيه.

- عند البحث في مجلدات الموقع، سيتم البحث في المجلد (الذي تم تعريفه `documentlink` بواسطة الخاصية الخاصة به) وكافة المجلدات الفرعية.

- عند تصدير نتائج البحث الذي حددت `folderid` فيه الخاصية فقط في استعلام البحث، يمكنك اختيار خيار التصدير الأول، "يتم تشفير كافة العناصر، باستثناء العناصر التي لها تنسيق غير متعرف عليه، أو لم تتم فهرستها لأسباب أخرى." سيتم دائما تصدير كافة العناصر الموجودة في المجلد بغض النظر عن حالة الفهرسة الخاصة بها لأن معرف المجلد تتم فهرسته دائما.
