---
title: استخدام برنامج نصي لإضافة مستخدمين إلى حالة الانتظار في حالة eDiscovery الأساسية
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
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: bad352ff-d5d2-45d8-ac2a-6cb832f10e73
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: تعرف على كيفية تشغيل برنامج نصي لإضافة علب بريد & OneDrive for Business إلى مجموعة جديدة مقترنة ب eDiscovery case في مركز التوافق في Microsoft 365.
ms.openlocfilehash: fd11ccb6c262cd0e31a65d2a1f95d5dbcd92869c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566538"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-core-ediscovery-case"></a>استخدام برنامج نصي لإضافة مستخدمين إلى حالة الانتظار في حالة eDiscovery الأساسية

يوفر & مركز التوافق PowerShell cmdlets التي تسمح لك بأتمتة المهام التي تستغرق وقتا طويلا والمهمات ذات الصلة بإنشاء حالات eDiscovery وإدارتها. في الوقت الحالي، يتطلب استخدام حالة eDiscovery الأساسية في مركز التوافق في Microsoft 365 وضع عدد كبير من مواقع المحتوى غير المهيأ قيد الانتظار وقتا وإعدادا. على سبيل المثال، قبل إنشاء جلسة الانتظار، يجب تجميع عنوان URL لكل موقع OneDrive for Business تريد وضعه في وضع الانتظار. ثم لكل مستخدم تريد وضعه في وضع الانتظار، يجب إضافة علبة بريده OneDrive for Business إلى الانتظار. يمكنك استخدام البرنامج النصي في هذه المقالة لأتمتة هذه العملية.
  
يطالبك البرنامج النصي باسم مجال "الموقع الخاص بي" في مؤسستك ( `contoso` على سبيل المثال، في عنوان URL https://contoso-my.sharepoint.com)، اسم حالة eDiscovery موجودة، واسم الاستمرار الجديد المقترن بهذه الحالة، وقائمة عناوين البريد الإلكتروني للمستخدمين الذين تريد وضعهم في وضع الانتظار، واستعلام بحث لاستخدامه إذا كنت تريد إنشاء قائمة انتظار مستندة إلى الاستعلام. يحصل البرنامج النصي بعد ذلك على عنوان URL الخاص OneDrive for Business لكل مستخدم في القائمة، وينشئ قائمة الانتظار الجديدة، ثم يضيف علبة البريد OneDrive for Business لكل مستخدم في القائمة إلى قائمة الانتظار. يقوم البرنامج النصي أيضا بإنشاء ملفات السجل التي تحتوي على معلومات حول جلسة الانتظار الجديدة.
  
فيما يلي الخطوات اللازمة لجعل هذا الأمر يحدث:
  
[الخطوة 1: تثبيت SharePoint Online Management Shell](#step-1-install-the-sharepoint-online-management-shell)
  
[الخطوة 2: إنشاء قائمة بالمستخدمين](#step-2-generate-a-list-of-users)
  
[الخطوة 3: تشغيل البرنامج النصي لإنشاء جلسة الانتظار وإضافة مستخدمين](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>قبل إضافة مستخدمين إلى الانتظار

- يجب أن تكون عضوا في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365 ومسؤول SharePoint عبر الإنترنت لتشغيل البرنامج النصي في الخطوة 3. لمزيد من المعلومات، راجع تعيين أذونات [eDiscovery في Office 365 Security & Compliance Center](assign-ediscovery-permissions.md).

- يمكن إضافة 1000 علبة بريد و100 موقع كحد أقصى إلى فترة الانتظار المقترنة ب حالة eDiscovery في مركز التوافق في Microsoft 365. إذا افترضنا أن كل مستخدم تريد وضعه في وضع الانتظار لديه موقع OneDrive for Business، يمكنك إضافة 100 مستخدم كحد أقصى إلى وضع الانتظار باستخدام البرنامج النصي في هذه المقالة.

- تأكد من حفظ قائمة المستخدمين الذين تقوم بإنشاءهم في الخطوة 2 والنص النصي في الخطوة 3 إلى المجلد نفسه. سيسهل ذلك تشغيل البرنامج النصي.

- يضيف البرنامج النصي قائمة المستخدمين إلى قائمة انتظار جديدة مقترنة بقضيه موجودة. تأكد من إنشاء حالة الانتظار التي تريد إقرانها قبل تشغيل البرنامج النصي.

- يدعم البرنامج النصي في هذه المقالة المصادقة الحديثة عند الاتصال بمركز التوافق & PowerShell SharePoint Online Management Shell. يمكنك استخدام البرنامج النصي كما هو إذا كنت Microsoft 365 أو Microsoft 365 سحابة القطاع الحكومي أخرى. إذا كنت أحد Office 365 ألمانيا، أو مؤسسة Microsoft 365 سحابة القطاع الحكومي عالية المستوى، أو مؤسسة Microsoft 365 DoD، يجب تحرير البرنامج النصي لتشغيله بنجاح. بشكل خاص `Connect-IPPSSession` ، يجب تحرير السطر واستخدام معلمات *ConnectionUri* و *AzureADAuthorizationEndpointUri* (والقيم المناسبة لنوع مؤسستك) للاتصال بمركز التوافق & PowerShell. لمزيد من المعلومات، راجع الأمثلة في الاتصال [إلى & مركز التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- يتم قطع اتصال البرنامج النصي تلقائيا & مركز التوافق PowerShell SharePoint Online Management Shell.

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. والغرض الأساسي منه هو وضع علبة البريد OneDrive for Business كل مستخدم في وضع الانتظار بسرعة وسهولة.

- البرامج النصية العينة المتوفرة في هذا الموضوع غير معتمدة ضمن أي برنامج أو خدمة دعم قياسية من Microsoft. يتم توفير البرامج النصية العينة AS IS بدون ضمان من أي نوع. وتنقر Microsoft أيضا عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية ل قابلية الاستخدام أو اللياقة لغرض معين. يبقى الخطر بأكمله الناتج عن استخدام البرامج النصية والوثائق العينة أو أدائها معك. لا تتحمل Microsoft بأي حال من الأحوال، أو كتابها، أو أي شخص آخر يشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها المسؤولية عن أي أضرار أيا كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن خسارة أرباح الأعمال أو انقطاع الأعمال أو فقدان معلومات العمل أو أي خسارة مادية أخرى) الناشئة عن استخدام البرامج النصية أو الوثائق العينة أو عدم القدرة على استخدامها،  حتى لو تم نصح Microsoft بإمكانية حدوث مثل هذه الأضرار.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>الخطوة 1: تثبيت SharePoint Online Management Shell

الخطوة الأولى هي تثبيت SharePoint Online Management Shell إذا لم يكن مثبتا بالفعل على الكمبيوتر المحلي. لست بحاجة إلى استخدام shell في هذا الإجراء، ولكن يجب تثبيته لأنه يحتوي على المتطلبات الأساسية التي يتطلبها البرنامج النصي الذي تقوم بتشغيله في الخطوة 3. تسمح هذه المتطلبات الأساسية البرنامج النصي بالتواصل مع SharePoint Online للحصول على عناوين URL OneDrive for Business ويب.
  
انتقل إلى [إعداد بيئة SharePoint Online Management Shell Windows PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) وانجز الخطوة 1 والخطوة 2 لتثبيت SharePoint Online Management Shell على الكمبيوتر المحلي.

## <a name="step-2-generate-a-list-of-users"></a>الخطوة 2: إنشاء قائمة بالمستخدمين

سينشئ البرنامج النصي في الخطوة 3 مع الاستمرار مقترن ب eDiscovery case، وإضافة علب البريد ومواقع OneDrive for Business لقائمة المستخدمين إلى قائمة الانتظار. يمكنك فقط كتابة عناوين البريد الإلكتروني في ملف نصي، أو يمكنك تشغيل أمر في Windows PowerShell للحصول على قائمة عناوين البريد الإلكتروني وحفظها في ملف (الموجود في المجلد نفسه الذي ستحفظ البرنامج النصي فيه في الخطوة 3).
  
إليك أمر PowerShell (الذي تقوم بتشغيله باستخدام PowerShell البعيد المتصل بمنظمة Exchange Online) للحصول على قائمة عناوين البريد الإلكتروني لجميع المستخدمين في مؤسستك وحفظها في ملف نصي باسم HoldUsers.txt.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

بعد تشغيل هذا الأمر، افتح الملف النصي وأزل الرأس الذي يحتوي على اسم الخاصية،  `PrimarySmtpAddress`. بعد ذلك، قم بإزالة كل عناوين البريد الإلكتروني باستثناء عناوين المستخدمين الذين تريد إضافتهم إلى قائمة الانتظار التي ستنشئها في الخطوة 3. تأكد من عدم وجود صفوف فارغة قبل قائمة عناوين البريد الإلكتروني أو بعدها.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>الخطوة 3: تشغيل البرنامج النصي لإنشاء جلسة الانتظار وإضافة مستخدمين

عند تشغيل البرنامج النصي في هذه الخطوة، سيطالبك بالمعلومات التالية. تأكد من أن هذه المعلومات جاهزة قبل تشغيل البرنامج النصي.
  
- **بيانات اعتماد المستخدم:** سيستخدم البرنامج النصي بيانات الاعتماد للاتصال بمركز & الأمان مع PowerShell. كما سيستخدم بيانات الاعتماد هذه للوصول إلى SharePoint Online للحصول على OneDrive for Business URL لقائمة المستخدمين.

- **اسم المجال SharePoint:** يطالبك البرنامج النصي بإدخال هذا الاسم حتى يمكنه الاتصال SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز الإدارة</a>. كما يستخدم اسم المجال OneDrive URL في مؤسستك. على سبيل المثال، إذا كان عنوان URL `https://contoso-admin.sharepoint.com` الخاص بمركز الإدارة وكان `https://contoso-my.sharepoint.com`عنوان URL الخاص OneDrive ، `contoso` يمكنك إدخاله عندما يطالبك البرنامج النصي باسم مجالك.

- **اسم الحالة:** اسم حالة موجودة. سينشئ البرنامج النصي مع الاستمرار الجديد المقترن بهذه الحالة.

- **اسم الانتظار:** سيتم إنشاء اسم الاستمرار في البرنامج النصي وإقرانه مع حالة الحروف المحددة.

- **استعلام البحث عن قائمة الانتظار المستندة إلى الاستعلام:** يمكنك إنشاء قائمة مستندة إلى الاستعلام بحيث يتم وضع المحتوى الذي يلبي معايير البحث المحددة فقط قيد الانتظار. لكي يتم وضع كل المحتويات في وضع الانتظار، ما عليك سوى الضغط على **Enter** عندما تتم مطالبتك باستعلام بحث.

- **تشغيل جلسة الانتظار أو عدم تشغيلها:** يمكنك تشغيل البرنامج النصي مع الاستمرار بعد إنشائه أو يمكنك تمكين البرنامج النصي من إنشاء فترة الانتظار دون تمكينه. إذا لم يكن البرنامج النصي قيد التشغيل، يمكنك تشغيله لاحقا في مركز التوافق في Microsoft 365 أو عن طريق تشغيل أوامر PowerShell التالية:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **اسم الملف النصي مع** قائمة المستخدمين - اسم الملف النصي من الخطوة 2 الذي يحتوي على قائمة المستخدمين الذين تريد إضافتهم إلى قائمة الانتظار. إذا كان هذا الملف موجودا في المجلد نفسه حيث يوجد البرنامج النصي، ما عليك سوى كتابة اسم الملف (على سبيل المثال، HoldUsers.txt). إذا كان الملف النصي في مجلد آخر، فا اكتب اسم المسار الكامل للملف.

بعد تجميع المعلومات التي سيطالبك بها البرنامج النصي، تكون الخطوة الأخيرة هي تشغيل البرنامج النصي لإنشاء الاستمرار الجديد وإضافة مستخدمين له.
  
1. احفظ النص التالي في ملف نصي Windows PowerShell باستخدام لاحقة اسم الملف ل `.ps1`. على سبيل المثال، `AddUsersToHold.ps1`.

```powershell
#script begin
" "
write-host "***********************************************"
write-host "   Security & Compliance Center PowerShell  " -foregroundColor yellow -backgroundcolor darkgreen
write-host "   Core eDiscovery cases - Add users to a hold   " -foregroundColor yellow -backgroundcolor darkgreen 
write-host "***********************************************"
" "
# Connect to SCC PowerShell using modern authentication
if (!$SccSession)
{
  Import-Module ExchangeOnlineManagement
  Connect-IPPSSession
}

# Get the organization's domain name. We use this to create the SharePoint admin URL and root URL for OneDrive for Business.
""
$mySiteDomain = Read-Host "Enter the domain name for your SharePoint organization. We use this name to connect to SharePoint admin center and for the OneDrive URLs in your organization. For example, 'contoso' in 'https://contoso-admin.sharepoint.com' and 'https://contoso-my.sharepoint.com'"
""

# Connect to PnP Online using modern authentication
Import-Module PnP.PowerShell
Connect-PnPOnline -Url https://$mySiteDomain-admin.sharepoint.com -UseWebLogin

# Load the SharePoint assemblies from the SharePoint Online Management Shell
# To install, go to https://go.microsoft.com/fwlink/p/?LinkId=255251
if (!$SharePointClient -or !$SPRuntime -or !$SPUserProfile)
{
    $SharePointClient = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client")
    $SPRuntime = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.Runtime")
    $SPUserProfile = [System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SharePoint.Client.UserProfiles")
    if (!$SharePointClient)
    {
        Write-Error "The SharePoint Online Management Shell isn't installed. Please install it from: https://go.microsoft.com/fwlink/p/?LinkId=255251 and then re-run this script."
        return;
    }
}

# Get other required information
do{
$casename = Read-Host "Enter the name of the case"
$caseexists = (get-compliancecase -identity "$casename" -erroraction SilentlyContinue).isvalid
if($caseexists -ne 'True')
{""
write-host "A case named '$casename' doesn't exist. Please specify the name of an existing case, or create a new case and then re-run the script." -foregroundColor Yellow
""}
}While($caseexists -ne 'True')
""
do{
$holdName = Read-Host "Enter the name of the new hold"
$holdexists=(get-caseholdpolicy -identity "$holdname" -case "$casename" -erroraction SilentlyContinue).isvalid
if($holdexists -eq 'True')
{""
write-host "A hold named '$holdname' already exists. Please specify a new hold name." -foregroundColor Yellow
""}
}While($holdexists -eq 'True')
""
$holdQuery = Read-Host "Enter a search query to create a query-based hold, or press Enter to hold all content"
""
$holdstatus = read-host "Do you want the hold enabled after it's created? (Yes/No)"
do{
""
$inputfile = read-host "Enter the name of the text file that contains the email addresses of the users to add to the hold"
""
$fileexists = test-path -path $inputfile
if($fileexists -ne 'True'){write-host "$inputfile doesn't exist. Please enter a valid file name." -foregroundcolor Yellow}
}while($fileexists -ne 'True')
#Import the list of addresses from the txt file.  Trim any excess spaces and make sure all addresses 
    #in the list are unique.
  [array]$emailAddresses = Get-Content $inputfile -ErrorAction SilentlyContinue | where {$_.trim() -ne ""}  | foreach{ $_.Trim() }
  [int]$dupl = $emailAddresses.count
  [array]$emailAddresses = $emailAddresses | select-object -unique
  $dupl -= $emailAddresses.count
#Validate email addresses so the hold creation does not run in to an error.
if($emailaddresses.count -gt 0){
write-host ($emailAddresses).count "addresses were found in the text file. There were $dupl duplicate entries in the file." -foregroundColor Yellow
""
Write-host "Validating the email addresses. Please wait..." -foregroundColor Yellow
""
$finallist =@()
foreach($emailAddress in $emailAddresses)
{
if((get-recipient $emailaddress -erroraction SilentlyContinue).isvalid -eq 'True')
{$finallist += $emailaddress}
else {"Unable to find the user $emailaddress"
[array]$excludedlist += $emailaddress}
}
""
#Find user's OneDrive account URL using email address
Write-Host "Getting the URL for each user's OneDrive for Business site." -foregroundColor Yellow 
""
$AdminUrl = "https://$mySiteDomain-admin.sharepoint.com"
$mySiteUrlRoot = "https://$mySiteDomain-my.sharepoint.com"
$urls = @()
foreach($emailAddress in $finallist)
{
try
{
$url=Get-PnPUserProfileProperty -Account $emailAddress | Select PersonalUrl
$urls += $url.PersonalUrl
       Write-Host "- $emailAddress => $url"
       [array]$ODadded += $url.PersonalUrl
       }catch { 
 Write-Warning "Could not locate OneDrive for $emailAddress"
 [array]$ODExluded += $emailAddress
 Continue }
}
$urls | FL
if(($finallist.count -gt 0) -or ($urls.count -gt 0)){
""
Write-Host "Creating the hold named $holdname. Please wait..." -foregroundColor Yellow
if(($holdstatus -eq "Y") -or ($holdstatus -eq  "y") -or ($holdstatus -eq "yes") -or ($holdstatus -eq "YES")){
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $True | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery | out-null
}
else{
New-CaseHoldPolicy -Name "$holdName" -Case "$casename" -ExchangeLocation $finallist -SharePointLocation $urls -Enabled $false | out-null
New-CaseHoldRule -Name "$holdName" -Policy "$holdname" -ContentMatchQuery $holdQuery -disabled $false | out-null
}
""
}
else {"No valid locations were identified. Therefore, the hold wasn't created."}
#write log files (if needed)
$newhold=Get-CaseHoldPolicy -Identity "$holdname" -Case "$casename" -erroraction SilentlyContinue
$newholdrule=Get-CaseHoldRule -Identity "$holdName" -erroraction SilentlyContinue
if(($ODAdded.count -gt 0) -or ($ODExluded.count -gt 0) -or ($finallist.count -gt 0) -or ($excludedlist.count -gt 0) -or ($newhold.isvalid -eq 'True') -or ($newholdrule.isvalid -eq 'True'))
{
Write-Host "Generating output files..." -foregroundColor Yellow
if($ODAdded.count -gt 0){
"OneDrive Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.SharePointLocation.name | add-content .\LocationsOnHold.txt}
if($ODExluded.count -gt 0){ 
"Users without OneDrive locations" | add-content .\LocationsNotOnHold.txt
"================================" | add-content .\LocationsNotOnHold.txt
$ODExluded | add-content .\LocationsNotOnHold.txt}
if($finallist.count -gt 0){
" " | add-content .\LocationsOnHold.txt
"Exchange Locations" | add-content .\LocationsOnHold.txt
"==================" | add-content .\LocationsOnHold.txt 
$newhold.ExchangeLocation.name | add-content .\LocationsOnHold.txt}
if($excludedlist.count -gt 0){
" "| add-content .\LocationsNotOnHold.txt
"Mailboxes not added to the hold" | add-content .\LocationsNotOnHold.txt
"===============================" | add-content .\LocationsNotOnHold.txt
$excludedlist | add-content .\LocationsNotOnHold.txt}
$FormatEnumerationLimit=-1
if($newhold.isvalid -eq 'True'){$newhold|fl >.\GetCaseHoldPolicy.txt}
if($newholdrule.isvalid -eq 'True'){$newholdrule|Fl >.\GetCaseHoldRule.txt}
}
}
else {"The hold wasn't created because no valid entries were found in the text file."}
""
#Disconnect from SCC PowerShell and PnPOnline

Write-host "Disconnecting from SCC PowerShell and PnP Online" -foregroundColor Yellow
Get-PSSession | Remove-PSSession
Disconnect-PnPOnline

Write-host "Script complete!" -foregroundColor Yellow
""
#script end
```

2. على الكمبيوتر المحلي، افتح Windows PowerShell واذهب إلى المجلد حيث حفظت البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. أدخل المعلومات التي يطالبك بها البرنامج النصي.

   يتصل البرنامج النصي بمركز التوافق & PowerShell، ثم ينشئ قائمة الانتظار الجديدة في حالة eDiscovery ويضيف علب البريد OneDrive for Business للمستخدمين في القائمة. يمكنك الانتقال إلى الحالة على **صفحة eDiscovery** في مركز التوافق في Microsoft 365 لعرض الانتظار الجديد.

بعد الانتهاء من تشغيل البرنامج النصي، ينشئ ملفات السجل التالية، ويحفظها في المجلد حيث يوجد البرنامج النصي.
  
- **LocationsOnHold.txt:** يحتوي على قائمة علب البريد OneDrive for Business المواقع التي وضعها البرنامج النصي قيد الانتظار بنجاح.

- **LocationsNotOnHold.txt:** يحتوي على قائمة علب البريد OneDrive for Business التي لم يتم وضع البرنامج النصي عليها في وضع الانتظار. إذا كان لدى المستخدم علبة بريد، وليس موقع OneDrive for Business، سيتم تضمين المستخدم في قائمة المواقع OneDrive for Business التي لم يتم وضعها قيد الانتظار.

- **GetCaseHoldPolicy.txt:** يحتوي على إخراج **أمر cmdlet Get-CaseHoldPolicy** الخاص باحتواء الملف الجديد، الذي تم تشغيل البرنامج النصي بعد إنشاء الاستمرار الجديد. تتضمن المعلومات التي يتم إرجاعها بواسطة أمر cmdlet هذا قائمة بالمستخدمين الذين تم وضع علب بريدهم ومواقعهم OneDrive for Business قيد الانتظار وما إذا كان قد تم تمكين الاستمرار أو تعطيله. 

- **GetCaseHoldRule.txt:** يحتوي على إخراج **أمر cmdlet Get-CaseHoldRule** الخاص باحتواء الملف الجديد، الذي تم تشغيل البرنامج النصي بعد إنشاء الاستمرار الجديد. تتضمن المعلومات التي يتم إرجاعها بواسطة الأمر cmdlet هذا استعلام البحث إذا استخدمت البرنامج النصي لإنشاء قائمة الانتظار المستندة إلى الاستعلام.
