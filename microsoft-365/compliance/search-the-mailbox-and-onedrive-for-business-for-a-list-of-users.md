---
title: استخدام البحث عن المحتوى لقائمة مستخدمين على موقع & OneDrive for Business علبة البريد
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: استخدم البحث عن المحتوى والبرامج النصية في هذه المقالة للبحث في علب البريد ومواقع OneDrive for Business لمجموعة من المستخدمين.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a75296bd17a1f4b77c22298f6c9a294ec06bd182
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098439"
---
# <a name="use-content-search-to-search-the-mailbox-and-onedrive-for-business-site-for-a-list-of-users"></a>استخدام البحث عن المحتوى للبحث في علبة البريد وموقع OneDrive for Business عن قائمة المستخدمين

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يوفر Security & Compliance Center PowerShell عددا من أوامر cmdlets التي تتيح لك أتمتة المهام ذات الصلة ب eDiscovery التي تستغرق وقتا طويلا. حاليا، يستغرق إنشاء بحث في المحتوى في مدخل توافق Microsoft Purview للبحث في عدد كبير من مواقع محتوى الوصي وقتا وإعدادا. قبل إنشاء عملية بحث، يجب عليك جمع عنوان URL لكل موقع OneDrive for Business ثم إضافة كل علبة بريد وموقع OneDrive for Business إلى البحث. في الإصدارات المستقبلية، سيكون من الأسهل القيام بذلك في مدخل التوافق. حتى ذلك الحين، يمكنك استخدام البرنامج النصي في هذه المقالة لأتمتة هذه العملية. يطالبك هذا البرنامج النصي باسم مجال MySite الخاص بالمؤسسة (على سبيل المثال، **contoso** في عنوان URL `https://contoso-my.sharepoint.com`) وقائمة بعناوين البريد الإلكتروني للمستخدم واسم البحث عن المحتوى الجديد واستعلام البحث المطلوب استخدامه. يحصل البرنامج النصي على عنوان URL OneDrive for Business لكل مستخدم في القائمة، ثم يقوم بإنشاء "بحث المحتوى" وبدء تشغيله للبحث في علبة البريد وموقع OneDrive for Business لكل مستخدم في القائمة، باستخدام استعلام البحث الذي توفره.
  
## <a name="permissions-and-script-information"></a>الأذونات ومعلومات البرنامج النصي

- يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل التوافق ومسؤولا عاما SharePoint Online لتشغيل البرنامج النصي في الخطوة 3.

- تأكد من حفظ قائمة المستخدمين الذين تقوم بإنشائها في الخطوة 2 والبرامج النصية في الخطوة 3 إلى المجلد نفسه. وهذا سيجعل من السهل تشغيل البرنامج النصي.

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي منه هو البحث بسرعة وسهولة في علبة البريد وموقع OneDrive for Business لكل مستخدم.

- لا يتم دعم نماذج البرامج النصية المتوفرة في هذا الموضوع ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نماذج البرامج النصية AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نماذج البرامج النصية والوثائق معك. لن تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناتجة عن استخدام نماذج البرامج النصية أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>الخطوة 1: تثبيت SharePoint Online Management Shell

الخطوة الأولى هي تثبيت SharePoint Online Management Shell. ليس عليك استخدام shell في هذا الإجراء، ولكن عليك تثبيته لأنه يحتوي على متطلبات مسبقة مطلوبة من قبل البرنامج النصي الذي تقوم بتشغيله في الخطوة 3. تسمح هذه المتطلبات الأساسية للبرنامج النصي بالاتصال ب SharePoint Online للحصول على عناوين URL لمواقع OneDrive for Business.
  
انتقل إلى [إعداد بيئة Windows PowerShell Windows PowerShell SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) وقم بتنفيذ الخطوة 1 والخطوة 2 لتثبيت SharePoint Online Management Shell.
  
## <a name="step-2-generate-a-list-of-users"></a>الخطوة 2: إنشاء قائمة المستخدمين

سيقوم البرنامج النصي في الخطوة 3 بإنشاء "بحث في المحتوى" للبحث في علب البريد وحسابات OneDrive لقائمة المستخدمين. يمكنك فقط كتابة عناوين البريد الإلكتروني في ملف نصي، أو يمكنك تشغيل أمر في Windows PowerShell للحصول على قائمة بعناوين البريد الإلكتروني وحفظها في ملف (موجود في المجلد نفسه الذي ستحفظ البرنامج النصي إليه في الخطوة 3).
  
إليك أمر [powerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) يمكنك تشغيله للحصول على قائمة بعناوين البريد الإلكتروني لجميع المستخدمين في مؤسستك وحفظها في ملف نصي يسمى `Users.txt`. 
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > Users.txt
```

بعد تشغيل هذا الأمر، تأكد من فتح الملف وإزالة الرأس الذي يحتوي على اسم الخاصية. `PrimarySmtpAddress` يجب أن يحتوي الملف النصي فقط على قائمة بعناوين البريد الإلكتروني، وليس أي شيء آخر. تأكد من عدم وجود صفوف فارغة قبل قائمة عناوين البريد الإلكتروني أو بعدها.
  
## <a name="step-3-run-the-script-to-create-and-start-the-search"></a>الخطوة 3: تشغيل البرنامج النصي لإنشاء البحث وبدء تشغيله

عند تشغيل البرنامج النصي في هذه الخطوة، سيطالبك بالمعلومات التالية. تأكد من أن هذه المعلومات جاهزة قبل تشغيل البرنامج النصي.
  
- **بيانات اعتماد المستخدم -** سيستخدم البرنامج النصي بيانات الاعتماد الخاصة بك للوصول إلى SharePoint Online للحصول على عناوين URL OneDrive for Business والاتصال ب Security & Compliance Center PowerShell. 
    
- **اسم مجال MySite** - مجال MySite هو المجال الذي يحتوي على كافة مواقع OneDrive for Business في مؤسستك. على سبيل المثال، إذا كان عنوان URL لمجال MySite الخاص بك ، **https://contoso-my.sharepoint.com** فستدخل  `contoso` عندما يطالبك البرنامج النصي باسم مجال MySite الخاص بك. 
    
- **اسم المسار للملف النصي من الخطوة 2** - اسم المسار للملف النصي الذي أنشأته في الخطوة 2. إذا كان الملف النصي والبرامج النصية موجودة في المجلد نفسه، فأدخل اسم الملف النصي. وإلا، أدخل اسم المسار الكامل للملف النصي. 
    
- **اسم البحث عن المحتوى** - اسم البحث في المحتوى الذي سيتم إنشاؤه بواسطة البرنامج النصي. 
    
- **استعلام البحث** - يتم إنشاء استعلام البحث الذي سيتم استخدامه مع البحث في المحتوى وتشغيله. لمزيد من المعلومات حول استعلامات البحث، راجع [استعلامات الكلمات الأساسية وشروط البحث في eDiscovery](keyword-queries-and-search-conditions.md).


**لتشغيل البرنامج النصي:**
    
1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف .ps1؛ على سبيل المثال، `SearchEXOOD4B.ps1`. احفظ الملف في المجلد نفسه حيث حفظت قائمة المستخدمين في الخطوة 2.
    
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

2. افتح Windows PowerShell وانتقل إلى المجلد حيث قمت بحفظ البرنامج النصي وقائمة المستخدمين من الخطوة 2.
    
3. بدء تشغيل البرنامج النصي؛ على سبيل المثال:
    
    ```powershell
    .\SearchEXOOD4B.ps1
    ```

4. عند مطالبتك ببيانات الاعتماد، أدخل عنوان بريدك الإلكتروني وكلمة المرور، ثم انقر فوق **"موافق**". 
    
5. أدخل المعلومات التالية عند مطالبتك من قبل البرنامج النصي. اكتب كل جزء من المعلومات ثم اضغط على **مفتاح الإدخال Enter**.
    
    - اسم مجال MySite الخاص بك. 
    
    - اسم المسار للملف النصي الذي يحتوي على قائمة المستخدمين.
    
    - اسم للبحث عن المحتوى.
    
    - استعلام البحث (اترك هذا فارغا لإرجاع كافة العناصر في مواقع المحتوى).
    
    يحصل البرنامج النصي على عناوين URL لكل موقع OneDrive for Business ثم ينشئ البحث ويبدأه. يمكنك إما تشغيل **الأمر Get-ComplianceSearch** cmdlet في Security & Compliance Center PowerShell لعرض إحصائيات البحث ونتائجه، أو يمكنك الانتقال إلى صفحة **البحث في المحتوى** في مدخل التوافق لعرض معلومات حول البحث.
