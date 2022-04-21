---
title: استخدام برنامج نصي لإضافة مستخدمين إلى قائمة احتجاز في حالة eDiscovery (قياسي)
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
description: تعرف على كيفية تشغيل برنامج نصي لإضافة علب بريد & OneDrive for Business مواقع إلى قائمة احتجاز جديدة مقترنة بحالة eDiscovery في مدخل توافق Microsoft Purview.
ms.openlocfilehash: 70ec2481e8fa352be47544cd2fe6a772c2fbb325
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000873"
---
# <a name="use-a-script-to-add-users-to-a-hold-in-a-ediscovery-standard-case"></a>استخدام برنامج نصي لإضافة مستخدمين إلى قائمة احتجاز في حالة eDiscovery (قياسي)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يوفر Security & Compliance Center PowerShell أوامر cmdlets تتيح لك أتمتة المهام التي تستغرق وقتا طويلا المتعلقة بإنشاء حالات eDiscovery وإدارتها. حاليا، يستغرق استخدام حالة Microsoft Purview eDiscovery (Standard) في مدخل الامتثال ل Microsoft Purview لوضع عدد كبير من مواقع محتوى الوصي قيد الاحتجاز وقتا وإعدادا. على سبيل المثال، قبل إنشاء قائمة احتجاز، يجب عليك جمع عنوان URL لكل موقع OneDrive for Business تريد وضعه قيد الاحتجاز. ثم لكل مستخدم تريد وضعه قيد الاحتجاز، يجب إضافة علبة بريده وموقع OneDrive for Business الخاص به إلى قائمة الاحتجاز. يمكنك استخدام البرنامج النصي في هذه المقالة لأتمتة هذه العملية.
  
يطالبك البرنامج النصي باسم مجال "الموقع الخاص بي" الخاص بالمؤسسة (على سبيل المثال، `contoso` في عنوان URL https://contoso-my.sharepoint.com)، واسم حالة eDiscovery الحالية، واسم قائمة الاحتجاز الجديدة المقترنة بالحالة، وقائمة عناوين البريد الإلكتروني للمستخدمين الذين تريد وضعهم قيد الاحتجاز، واستعلام بحث لاستخدامه إذا كنت تريد إنشاء قائمة احتجاز مستندة إلى استعلام. ثم يحصل البرنامج النصي على عنوان URL لموقع OneDrive for Business لكل مستخدم في القائمة، ويقوم بإنشاء قائمة الاحتجاز الجديدة، ثم يضيف علبة البريد وموقع OneDrive for Business لكل مستخدم في القائمة إلى قائمة الاحتجاز. يقوم البرنامج النصي أيضا بإنشاء ملفات السجل التي تحتوي على معلومات حول قائمة الاحتجاز الجديدة.
  
فيما يلي الخطوات التي يجب اتخاذها لإجراء ذلك:
  
[الخطوة 1: تثبيت SharePoint Online Management Shell](#step-1-install-the-sharepoint-online-management-shell)
  
[الخطوة 2: إنشاء قائمة المستخدمين](#step-2-generate-a-list-of-users)
  
[الخطوة 3: تشغيل البرنامج النصي لإنشاء قائمة احتجاز وإضافة مستخدمين](#step-3-run-the-script-to-create-a-hold-and-add-users)
  
## <a name="before-you-add-users-to-a-hold"></a>قبل إضافة مستخدمين إلى قائمة احتجاز

- يجب أن تكون عضوا في مجموعة دور eDiscovery Manager في مدخل التوافق ومسؤول SharePoint Online لتشغيل البرنامج النصي في الخطوة 3. لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery في مركز التوافق & للأمان Office 365](assign-ediscovery-permissions.md).

- يمكن إضافة 1000 علبة بريد و100 موقع كحد أقصى إلى قائمة احتجاز مقترنة بحالة eDiscovery في مدخل التوافق. بافتراض أن كل مستخدم تريد وضعه قيد الاحتجاز لديه موقع OneDrive for Business، يمكنك إضافة 100 مستخدم كحد أقصى إلى قائمة احتجاز باستخدام البرنامج النصي في هذه المقالة.

- تأكد من حفظ قائمة المستخدمين الذين تقوم بإنشائها في الخطوة 2 والبرامج النصية في الخطوة 3 إلى المجلد نفسه. وهذا سيجعل من السهل تشغيل البرنامج النصي.

- يضيف البرنامج النصي قائمة المستخدمين إلى قائمة احتجاز جديدة مقترنة بحالة موجودة. تأكد من إنشاء الحالة التي تريد إقران قائمة الاحتجاز بها قبل تشغيل البرنامج النصي.

- يدعم البرنامج النصي في هذه المقالة المصادقة الحديثة عند الاتصال ب Security & Compliance Center PowerShell و SharePoint Online Management Shell. يمكنك استخدام البرنامج النصي كما هو إذا كنت Microsoft 365 أو مؤسسة Microsoft 365 سحابة القطاع الحكومي. إذا كنت مؤسسة Office 365 ألمانيا أو مؤسسة Microsoft 365 سحابة القطاع الحكومي عالية أو مؤسسة Microsoft 365 DoD، فستضطر إلى تحرير البرنامج النصي لتشغيله بنجاح. على وجه التحديد، يجب عليك تحرير السطر `Connect-IPPSSession` واستخدام معلمات *ConnectionUri* *وAzureADAuthorizationEndpointUri* (والقيم المناسبة لنوع مؤسستك) للاتصال ب Security & Compliance Center PowerShell. لمزيد من المعلومات، راجع الأمثلة في [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell#connect-to-security--compliance-center-powershell-without-using-mfa).

- يتم قطع اتصال البرنامج النصي تلقائيا ب Security & Compliance Center PowerShell و SharePoint Online Management Shell.

- يتضمن البرنامج النصي الحد الأدنى من معالجة الأخطاء. الغرض الأساسي منه هو وضع علبة البريد وموقع OneDrive for Business لكل مستخدم بسرعة وسهولة قيد الاحتجاز.

- لا يتم دعم نماذج البرامج النصية المتوفرة في هذا الموضوع ضمن أي برنامج دعم أو خدمة قياسية من Microsoft. يتم توفير نماذج البرامج النصية AS IS دون ضمان من أي نوع. وتخلي Microsoft المزيد من المسؤولية عن جميع الضمانات الضمنية، بما في ذلك، على سبيل المثال لا الحصر، أي ضمانات ضمنية لقابلية تجارية أو للياقة لغرض معين. يبقى الخطر بأكمله الناشئ عن استخدام أو أداء نماذج البرامج النصية والوثائق معك. لن تتحمل شركة Microsoft أو كتابها أو أي شخص آخر مشارك في إنشاء البرامج النصية أو إنتاجها أو تسليمها مسؤولية أي أضرار مهما كانت (بما في ذلك، على سبيل المثال لا الحصر، الأضرار الناجمة عن فقدان أرباح الأعمال أو انقطاع العمل أو فقدان معلومات العمل أو أي خسارة في المالية الأخرى) الناتجة عن استخدام نماذج البرامج النصية أو الوثائق أو عدم القدرة على استخدامها،  حتى إذا تم إعلام Microsoft باحتمال حدوث مثل هذه الأضرار.

## <a name="step-1-install-the-sharepoint-online-management-shell"></a>الخطوة 1: تثبيت SharePoint Online Management Shell

الخطوة الأولى هي تثبيت SharePoint Online Management Shell إذا لم يكن مثبتا بالفعل على الكمبيوتر المحلي. ليس عليك استخدام shell في هذا الإجراء، ولكن عليك تثبيته لأنه يحتوي على متطلبات مسبقة مطلوبة من قبل البرنامج النصي الذي تقوم بتشغيله في الخطوة 3. تسمح هذه المتطلبات الأساسية للبرنامج النصي بالاتصال ب SharePoint Online للحصول على عناوين URL لمواقع OneDrive for Business.
  
انتقل إلى [إعداد بيئة Windows PowerShell SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) وقم بتنفيذ الخطوة 1 والخطوة 2 لتثبيت SharePoint Online Management Shell على الكمبيوتر المحلي.

## <a name="step-2-generate-a-list-of-users"></a>الخطوة 2: إنشاء قائمة المستخدمين

سيقوم البرنامج النصي في الخطوة 3 بإنشاء قائمة احتجاز مقترنة بحالة eDiscovery، وإضافة علب البريد ومواقع OneDrive for Business لقائمة مستخدمين إلى قائمة الاحتجاز. يمكنك فقط كتابة عناوين البريد الإلكتروني في ملف نصي، أو يمكنك تشغيل أمر في Windows PowerShell للحصول على قائمة بعناوين البريد الإلكتروني وحفظها في ملف (موجود في المجلد نفسه الذي ستحفظ البرنامج النصي إليه في الخطوة 3).
  
إليك أمر PowerShell (الذي تقوم بتشغيله باستخدام PowerShell البعيد المتصل بمؤسستك Exchange Online) للحصول على قائمة بعناوين البريد الإلكتروني لجميع المستخدمين في مؤسستك وحفظها في ملف نصي يسمى HoldUsers.txt.
  
```powershell
Get-Mailbox -ResultSize unlimited -Filter { RecipientTypeDetails -eq 'UserMailbox'} | Select-Object PrimarySmtpAddress > HoldUsers.txt
```

بعد تشغيل هذا الأمر، افتح الملف النصي وقم بإزالة الرأس الذي يحتوي على اسم الخاصية. `PrimarySmtpAddress` ثم قم بإزالة كل عناوين البريد الإلكتروني باستثناء عناوين المستخدمين الذين تريد إضافتهم إلى قائمة الاحتجاز التي ستقوم بإنشائها في الخطوة 3. تأكد من عدم وجود صفوف فارغة قبل قائمة عناوين البريد الإلكتروني أو بعدها.
  
## <a name="step-3-run-the-script-to-create-a-hold-and-add-users"></a>الخطوة 3: تشغيل البرنامج النصي لإنشاء قائمة احتجاز وإضافة مستخدمين

عند تشغيل البرنامج النصي في هذه الخطوة، سيطالبك بالمعلومات التالية. تأكد من أن هذه المعلومات جاهزة قبل تشغيل البرنامج النصي.
  
- **بيانات اعتماد المستخدم:** سيستخدم البرنامج النصي بيانات الاعتماد الخاصة بك للاتصال ب Security & Compliance Center باستخدام PowerShell. كما سيستخدم بيانات الاعتماد هذه للوصول إلى SharePoint Online للحصول على عناوين URL OneDrive for Business لقائمة المستخدمين.

- **اسم مجال SharePoint:** يطالبك البرنامج النصي بإدخال هذا الاسم حتى يتمكن من الاتصال <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">بمركز إدارة SharePoint</a>. كما يستخدم اسم المجال لعناوين URL OneDrive في مؤسستك. على سبيل المثال، إذا كان URL لمركز الإدارة الخاص بك وعنوان `https://contoso-admin.sharepoint.com` URL الخاص OneDrive هو `https://contoso-my.sharepoint.com`، فستدخل `contoso` عندما يطالبك البرنامج النصي باسم مجالك.

- **اسم الحالة:** اسم حالة موجودة. سيقوم البرنامج النصي بإنشاء قائمة احتجاز جديدة مقترنة بهذه الحالة.

- **اسم قائمة الاحتجاز:** اسم قائمة الاحتجاز التي سيقوم البرنامج النصي بإنشائها وإقرانها بالحالة المحددة.

- **استعلام البحث عن قائمة احتجاز مستندة إلى استعلام:** يمكنك إنشاء قائمة احتجاز مستندة إلى استعلام بحيث يتم وضع المحتوى الذي يفي بمعايير البحث المحددة فقط قيد الاحتجاز. لوضع كل المحتوى قيد الاحتجاز، ما عليك سوى الضغط على **مفتاح الإدخال Enter** عندما تتم مطالبتك باستعلام بحث.

- **تشغيل قائمة الاحتجاز أم لا:** يمكنك تشغيل البرنامج النصي مؤقتا بعد إنشائه أو يمكنك أن تجعل البرنامج النصي ينشئ قائمة الاحتجاز دون تمكينه. إذا لم يكن البرنامج النصي قيد الانتظار، يمكنك تشغيله لاحقا في مدخل التوافق أو عن طريق تشغيل أوامر PowerShell التالية:

  ```powershell
  Set-CaseHoldPolicy -Identity <name of the hold> -Enabled $true
  ```

  ```powershell
  Set-CaseHoldRule -Identity <name of the hold> -Disabled $false
  ```

- **اسم الملف النصي مع قائمة المستخدمين** - اسم الملف النصي من الخطوة 2 الذي يحتوي على قائمة المستخدمين لإضافتها إلى قائمة الاحتجاز. إذا كان هذا الملف موجودا في نفس المجلد مثل البرنامج النصي، فما عليك سوى كتابة اسم الملف (على سبيل المثال، HoldUsers.txt). إذا كان الملف النصي في مجلد آخر، فاكتب اسم المسار الكامل للملف.

بعد جمع المعلومات التي سيطالبك بها البرنامج النصي، فإن الخطوة الأخيرة هي تشغيل البرنامج النصي لإنشاء قائمة احتجاز جديدة وإضافة مستخدمين إليها.
  
1. احفظ النص التالي إلى ملف برنامج نصي Windows PowerShell باستخدام لاحقة اسم الملف ل `.ps1`. على سبيل المثال، `AddUsersToHold.ps1`.

```powershell
#script begin
" "
write-host "***********************************************"
write-host "   Security & Compliance Center PowerShell  " -foregroundColor yellow -backgroundcolor darkgreen
write-host "   eDiscovery (Standard) cases - Add users to a hold   " -foregroundColor yellow -backgroundcolor darkgreen 
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

2. على الكمبيوتر المحلي، افتح Windows PowerShell وانتقل إلى المجلد حيث حفظت البرنامج النصي.

3. تشغيل البرنامج النصي؛ على سبيل المثال:

   ```powershell
   .\AddUsersToHold.ps1
   ```

4. أدخل المعلومات التي يطالبك البرنامج النصي بها.

   يتصل البرنامج النصي ب Security & Compliance Center PowerShell، ثم ينشئ قائمة الاحتجاز الجديدة في حالة eDiscovery ويضيف علب البريد OneDrive for Business للمستخدمين في القائمة. يمكنك الانتقال إلى الحالة على صفحة **eDiscovery** في مدخل التوافق لعرض قائمة الاحتجاز الجديدة.

بعد الانتهاء من تشغيل البرنامج النصي، يقوم بإنشاء ملفات السجل التالية، ويحفظها في المجلد حيث يوجد البرنامج النصي.
  
- **LocationsOnHold.txt:** يحتوي على قائمة بعلب البريد ومواقع OneDrive for Business التي وضعها البرنامج النصي قيد الاحتجاز بنجاح.

- **LocationsNotOnHold.txt:** يحتوي على قائمة بعلب البريد والمواقع OneDrive for Business التي لم يضعها البرنامج النصي قيد الاحتجاز. إذا كان لدى المستخدم علبة بريد، ولكن ليس موقع OneDrive for Business، فسيتم تضمين المستخدم في قائمة مواقع OneDrive for Business التي لم يتم وضعها قيد الاحتجاز.

- **GetCaseHoldPolicy.txt:** يحتوي على إخراج **Cmdlet Get-CaseHoldPolicy** للاحتفاظ الجديد، والذي تم تشغيل البرنامج النصي بعد إنشاء قائمة الاحتجاز الجديدة. تتضمن المعلومات التي تم إرجاعها بواسطة أمر cmdlet هذا قائمة بالمستخدمين الذين تم وضع علب بريدهم ومواقع OneDrive for Business الخاصة بهم قيد الاحتجاز وما إذا كان الاحتجاز ممكنا أو معطلا. 

- **GetCaseHoldRule.txt:** يحتوي على إخراج **Cmdlet Get-CaseHoldRule** للاحتفاظ الجديد، والذي تم تشغيل البرنامج النصي بعد إنشاء قائمة الاحتجاز الجديدة. تتضمن المعلومات التي تم إرجاعها بواسطة أمر cmdlet هذا استعلام البحث إذا استخدمت البرنامج النصي لإنشاء قائمة احتجاز مستندة إلى الاستعلام.
