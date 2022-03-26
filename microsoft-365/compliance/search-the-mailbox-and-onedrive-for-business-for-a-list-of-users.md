---
title: البحث في موقع & OneDrive for Business عن قائمة بالمستخدمين الذين لديهم "بحث في المحتوى"
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 1/3/2017
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
ms.assetid: 5f4f8206-2d6a-4cb2-bbc6-7a0698703cc0
description: استخدم البحث في المحتوى والنص النصي في هذه المقالة للبحث في علب البريد OneDrive for Business عن مجموعة من المستخدمين.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2fdf749511cc859c0aec2ea947c3a53cb800cf8c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/25/2021
ms.locfileid: "63567159"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>استخدام "البحث في المحتوى" للبحث في علبة البريد OneDrive for Business عن قائمة المستخدمين

يوفر & مركز التوافق PowerShell عددا من cmdlets التي تسمح لك بأتمتة المهام ذات الصلة ب eDiscovery التي تستغرق وقتا طويلا. في الوقت الحالي، يتطلب إنشاء بحث في المحتوى في مركز التوافق في Microsoft 365 البحث في عدد كبير من مواقع المحتوى غير المهيأ وقتا وإعدادا. قبل إنشاء عملية بحث، يجب تجميع عنوان URL لكل موقع OneDrive for Business ثم إضافة كل علبة بريد OneDrive for Business إلى البحث. في الإصدارات المستقبلية، سيكون ذلك أسهل في مركز التوافق في Microsoft 365. حتى ذلك الحين، يمكنك استخدام البرنامج النصي في هذه المقالة لأتمتة هذه العملية. يطالبك هذا البرنامج النصي باسم مجال MySite الخاص بالمكتبة (على سبيل المثال **، contoso** في عنوان URL `https://contoso-my.sharepoint.com`) وقائمة عناوين البريد الإلكتروني للمستخدم واسم البحث في المحتوى الجديد واستعلام البحث الذي يجب استخدامه. يحصل البرنامج النصي على ONEDRIVE FOR BUSINESS URL لكل مستخدم في القائمة، ثم يقوم بإنشاء "بحث محتوى" يبدأ البحث في علبة البريد OneDrive for Business لكل مستخدم في القائمة، باستخدام استعلام البحث الذي توفره.
  
## <a name="permissions-and-script-information"></a>الأذونات ومعلومات البرنامج النصي

- يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365 ومسؤول SharePoint Online لتشغيل البرنامج النصي في الخطوة 3.

- تأكد من حفظ قائمة المستخدمين الذين تقوم بإنشاءهم في الخطوة 2 والنص النصي في الخطوة 3 إلى المجلد نفسه. سيسهل ذلك تشغيل البرنامج النصي.

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي منه هو البحث بسرعة وسهولة في علبة البريد OneDrive for Business موقع كل مستخدم.

- البرامج النصية العينة المتوفرة في هذا الموضوع غير معتمدة ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرامج النصية العينة AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام البرامج النصية والوثائق العينة أو أدائها معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها المسؤولية عن أي أضرار أيا كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام البرامج النصية أو الوثائق العينة أو عدم القدرة على استخدامها،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>الخطوة 1: تثبيت SharePoint Online Management Shell

الخطوة الأولى هي تثبيت SharePoint Online Management Shell. لست بحاجة إلى استخدام shell في هذا الإجراء، ولكن يجب تثبيته لأنه يحتوي على المتطلبات الأساسية التي يتطلبها البرنامج النصي الذي تقوم بتشغيله في الخطوة 3. تسمح هذه المتطلبات الأساسية البرنامج النصي بالتواصل مع SharePoint Online للحصول على عناوين URL OneDrive for Business ويب.
  
انتقل إلى [إعداد بيئة SharePoint Online Management Shell Windows PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)، ثم قم بتنفيذ الخطوة 1 والخطوة 2 لتثبيت SharePoint Online Management Shell.
  
## <a name="step-2-generate-a-list-of-users"></a>الخطوة 2: إنشاء قائمة بالمستخدمين

سينشئ البرنامج النصي في الخطوة 3 البحث في المحتوى للبحث في علب البريد OneDrive عن قائمة المستخدمين. يمكنك فقط كتابة عناوين البريد الإلكتروني في ملف نصي، أو يمكنك تشغيل أمر في Windows PowerShell للحصول على قائمة عناوين البريد الإلكتروني وحفظها في ملف (الموجود في المجلد نفسه الذي ستحفظ البرنامج النصي فيه في الخطوة 3).
  
إليك أمر [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) الذي يمكنك تشغيله للحصول على قائمة عناوين البريد الإلكتروني لجميع المستخدمين في مؤسستك وحفظها في ملف نصي باسم `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

بعد تشغيل هذا الأمر، تأكد من فتح الملف وإزالة الرأس الذي يحتوي على اسم الخاصية،  `PrimarySmtpAddress`. يجب أن يحتوي الملف النصي فقط على قائمة عناوين البريد الإلكتروني، وليس أي شيء آخر. تأكد من عدم وجود صفوف فارغة قبل قائمة عناوين البريد الإلكتروني أو بعدها.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>الخطوة 3: تشغيل البرنامج النصي لإنشاء البحث وبدءه

عند تشغيل البرنامج النصي في هذه الخطوة، سيطالبك بالمعلومات التالية. تأكد من أن هذه المعلومات جاهزة قبل تشغيل البرنامج النصي.
  
- **بيانات اعتماد** المستخدم - سيستخدم البرنامج النصي بيانات الاعتماد للوصول إلى SharePoint Online للحصول على عناوين URL OneDrive for Business والاتصال بمركز التوافق & PowerShell. 
    
- **اسم مجال MySite** الخاص بك - مجال MySite هو المجال الذي يحتوي على كل OneDrive for Business في مؤسستك. على سبيل المثال، إذا كان عنوان URL لمجال MySite **https://contoso-my.sharepoint.com** الخاص بك هو ،  `contoso` يمكنك إدخاله عندما يطالبك البرنامج النصي باسم مجال MySite الخاص بك. 
    
- **اسم المسار للملف النصي من الخطوة 2** - اسم المسار للملف النصي الذي أنشأته في الخطوة 2. إذا كان الملف النصي والنص النصي موجودين في المجلد نفسه، أدخل اسم الملف النصي. وإلا، أدخل اسم المسار الكامل للملف النصي. 
    
- **اسم البحث في المحتوى** - اسم البحث في المحتوى الذي سيتم إنشاؤه بواسطة البرنامج النصي. 
    
- **استعلام البحث** - يتم إنشاء استعلام البحث الذي سيتم استخدامه مع "البحث في المحتوى" وتشغيله. لمزيد من المعلومات حول استعلامات البحث، راجع [استعلامات الكلمات الأساسية وشروط البحث ل eDiscovery](keyword-queries-and-search-conditions.md).


**لتشغيل البرنامج النصي:**
    
1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `SearchEXOOD4B.ps1`. احفظ الملف في المجلد نفسه حيث حفظت قائمة المستخدمين في الخطوة 2.
    
  ```powershell
  # This PowerShell script will prompt you for the following information:
  #    * Your user credentials 
  #    * The name of your organization's MySite domain                                              
  #    * The pathname for the text file that contains a list of user email addresses
  #    * The name of the Content Search that will be created
  #    * The search query string
  # The script will then:
  #    * Find the OneDrive for Business site for each user in the text file
  #    * Create and start a Content Search using the above information
  # Get user credentials
  if (!$credentials)
  {
      $credentials = Get-Credential
  }
  # Get the user's MySite domain name.  We use this to create the admin URL and root URL for OneDrive for Business
  $mySiteDomain = Read-Host "What is your organization's MySite domain?  For example,  'contoso' for 'https://contoso-my.sharepoint.com'"
  $AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
  $mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
  # Get other required information
  $inputfile = read-host "Enter the file name of the text file that contains the email addresses for the users you want to search"
  $searchName = Read-Host "Enter the name for the new search"
  $searchQuery = Read-Host "Enter the search query you want to use"
  $emailAddresses = Get-Content $inputfile | where {$_ -ne ""}  | foreach{ $_.Trim() }
  # Connect to Security & Compliance Center PowerShell
  if (!$s -or !$a)
  {
      Import-Module ExchangeOnlineManagement
      Connect-IPPSSession
  }
  
  # Load the SharePoint assemblies from the SharePoint Online Management Shell
  # To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
  if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
  {
      $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
      $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
      $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
      if (!$SharePointClient)
      {
          Write-Error "SharePoint Online Management Shell isn't installed, please install from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then run this script again"
          return;
      }
  }
  if (!$spCreds)
  {
      $spCreds = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($credentials.UserName, $credentials.Password)
  }
  # Add the path of the User Profile Service to the SPO admin URL, then create a new webservice proxy to access it
  $proxyaddr = "$AdminUrl/_vti_bin/UserProfileService.asmx?wsdl"
  $UserProfileService= New-WebServiceProxy -Uri $proxyaddr -UseDefaultCredential False
  $UserProfileService.Credentials = $credentials
  # Take care of auth cookies
  $strAuthCookie = $spCreds.GetAuthenticationCookie($AdminUrl)
  $uri = New-Object System.Uri($AdminUrl)
  $container = New-Object System.Net.CookieContainer
  $container.SetCookies($uri, $strAuthCookie)
  $UserProfileService.CookieContainer = $container
  Write-Host "Getting each user's OneDrive for Business URL"
  $urls = @()
  foreach($emailAddress in $emailAddresses)
  {
      try
      {
          $prop = $UserProfileService.GetUserProfileByName("i:0#.f|membership|$emailAddress") | Where-Object { $_.Name -eq "PersonalSpace" } 
          $url = $prop.values[0].value
          $furl = $mySiteUrlRoot + $url
          $urls += $furl
          Write-Host "-$emailAddress => $furl"
      }
      catch
      {
          Write-Warning "Could not locate OneDrive for $emailAddress"
      }
  }
  Write-Host "Creating and starting the search"
  $search = New-ComplianceSearch -Name $searchName -ExchangeLocation $emailAddresses -SharePointLocation $urls -ContentMatchQuery $searchQuery
  # Finally, start the search and then display the status
  if($search)
  {
      Start-ComplianceSearch $search.Name
      Get-ComplianceSearch $search.Name
  }
  
  ```

2. افتح Windows PowerShell واذهب إلى المجلد حيث حفظت البرنامج النصي وقائمة المستخدمين من الخطوة 2.
    
3. بدء البرنامج النصي؛ على سبيل المثال:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. عند مطالبتك بإدخال بيانات الاعتماد، أدخل عنوان البريد الإلكتروني وكلمة المرور، ثم انقر فوق **موافق**. 
    
5. أدخل المعلومات التالية عند مطالبتك بها بواسطة البرنامج النصي. اكتب كل معلومة، ثم اضغط على **Enter**.
    
    - اسم مجال MySite الخاص بك. 
    
    - اسم المسار للملف النصي الذي يحتوي على قائمة المستخدمين.
    
    - اسم للبحث في المحتوى.
    
    - استعلام البحث (اترك هذا فارغا لإرجاع كل العناصر في مواقع المحتوى).
    
    يحصل البرنامج النصي على عناوين URL لكل OneDrive for Business ويب ثم ينشئ البحث ويبدأه. يمكنك إما تشغيل الأمر **Cmdlet البحث عن Get-ComplianceSearch** في مركز التوافق & PowerShell لعرض إحصائيات البحث ونتائجه، أو يمكنك الانتقال إلى صفحة البحث في المحتوى في مركز التوافق في Microsoft 365  لعرض معلومات حول البحث.
