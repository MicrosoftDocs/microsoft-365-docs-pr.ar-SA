---
title: استخدم PowerShell لتوصيل الورديات ب Blue Yonder Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية استخدام PowerShell لدمج Shifts مع Blue Yonder Workforce Management.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 22b820bdbb372b5f07967836613a9d7348bd7b1c
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66858072"
---
# <a name="use-powershell-to-connect-shifts-to-blue-yonder-workforce-management"></a>استخدم PowerShell لتوصيل الورديات ب Blue Yonder Workforce Management

## <a name="overview"></a>نظرة عامة

استخدم [موصل Microsoft Teams Shifts ل Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) لدمج تطبيق Shifts في Microsoft Teams مع Workforce Management Blue Yonder (Blue Yonder WFM). بعد إعداد الاتصال، يمكن للعاملين في الخطوط الأمامية عرض جداولهم وإدارتها بسلاسة في Blue Yonder WFM من داخل Shifts.

في هذه المقالة، نرشدك إلى كيفية استخدام PowerShell لإعداد الموصل وتكوينه لدمج Shifts مع Blue Yonder WFM.

لإعداد الاتصال، يمكنك تشغيل برنامج نصي PowerShell. يقوم البرنامج النصي بتكوين الموصل، وتطبيق إعدادات المزامنة، وإنشاء الاتصال، وتعيين مثيلات WFM Blue Yonder إلى الفرق. تحدد إعدادات المزامنة الميزات الممكنة في Shifts ومعلومات الجدولة التي تتم مزامنتها بين WFM وShifts في Blue Yonder. تحدد التعيينات علاقة المزامنة بين مثيلات WFM Blue Yonder والفرق في Teams. يمكنك التعيين إلى الفرق الموجودة والفرق الجديدة.

نحن نقدم برنامجين نصيين. يمكنك استخدام أي من البرنامجين النصيين، اعتمادا على ما إذا كنت تريد التعيين إلى الفرق الموجودة أو إنشاء فرق جديدة لتعيينها.

يمكنك إعداد اتصالات متعددة، لكل منهما إعدادات مزامنة مختلفة. على سبيل المثال، إذا كانت مؤسستك تحتوي على مواقع متعددة ذات متطلبات جدولة مختلفة، قم بإنشاء اتصال بإعدادات مزامنة فريدة لكل موقع. ضع في اعتبارك أنه يمكن تعيين مثيل WFM أزرق إلى فريق واحد فقط في أي وقت. إذا تم تعيين مثيل بالفعل إلى فريق، فلا يمكن تعيينه إلى فريق آخر.

مع WFM Blue Yonder كنظام سجل، يمكن للعاملين في الخطوط الأمامية رؤية الورديات وتبديلها، وإدارة توفرهم، وطلب الإجازة في الورديات على أجهزتهم. يمكن لمديري الخطوط الأمامية الاستمرار في استخدام Blue Yonder WFM لإعداد الجداول الزمنية.

> [!NOTE]
> يمكنك أيضا استخدام [معالج موصل Shifts](shifts-connector-wizard.md) في مركز مسؤولي Microsoft 365 لتوصيل Shifts WFM Blue Yonder.

## <a name="before-you-begin"></a>قبل البدء

### <a name="prerequisites"></a>المتطلبات الأساسية

[!INCLUDE [shifts-connector-prerequisites](includes/shifts-connector-prerequisites.md)]

### <a name="admin-role-to-manage-the-connector-using-powershell"></a>مسؤول الدور لإدارة الموصل باستخدام PowerShell

[!INCLUDE [shifts-connector-admin-role](includes/shifts-connector-admin-role.md)]

## <a name="set-up-your-environment"></a>إعداد البيئة الخاصة بك

[!INCLUDE [shifts-connector-set-up-environment](includes/shifts-connector-set-up-environment.md)]

## <a name="connect-to-teams"></a>الاتصال ب Teams

قم بتشغيل ما يلي للاتصال ب Teams.

```powershell
Connect-MicrosoftTeams
```

عند مطالبتك، سجل الدخول باستخدام بيانات اعتماد المسؤول. لقد أعددت الآن لتشغيل البرامج النصية في هذه المقالة وShifts connector cmdlets.

## <a name="identify-the-teams-you-want-to-map"></a>تحديد الفرق التي تريد تعيينها

> [!NOTE]
> أكمل هذه الخطوة إذا كنت تقوم بتعيين مثيلات Blue Yonder WFM إلى الفرق الموجودة. إذا كنت تقوم بإنشاء فرق جديدة لتعيينها، يمكنك تخطي هذه الخطوة.

في Azure-Portal، انتقل إلى صفحة ["كافة المجموعات](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups)" للحصول على قائمة ب TeamIds للفرق في مؤسستك.

دون معرفات الفريق للفرق التي تريد تعيينها. سيطالبك البرنامج النصي بإدخال هذه المعلومات.

> [!NOTE]
> إذا كان هناك فريق واحد أو أكثر لديه جدول حالي، فسيزيل البرنامج النصي الجداول من تلك الفرق. وإلا، فسترى ورديات مكررة.

## <a name="run-the-script"></a>تشغيل البرنامج النصي

تشغيل البرنامج النصي:

- لإعداد اتصال وإنشاء فرق جديدة لتعيينها، [قم بتشغيل هذا البرنامج النصي](#set-up-a-connection-and-create-new-teams-to-map).
- لإعداد اتصال وتعيين إلى الفرق الموجودة، [قم بتشغيل هذا البرنامج النصي](#set-up-a-connection-and-map-to-existing-teams).

يقوم البرنامج النصي بالإجراءات التالية. ستتم مطالبتك بإدخال تفاصيل الإعداد والتكوين.

1. يختبر ويتحقق من الاتصال ب Blue Yonder WFM باستخدام بيانات اعتماد حساب الخدمة WFM الأزرق وعناوين URL للخدمة التي تقوم بإدخالها.
1. تكوين موصل Shifts.
1. تطبيق إعدادات المزامنة. تتضمن هذه الإعدادات تكرار المزامنة (بالدقائق) وبيانات الجدولة التي تتم مزامنتها بين WFM Blue Yonder وShifts. يتم تعريف بيانات الجدولة في المعلمات التالية:

    - تحدد المعلمة **enabledConnectorScenarios** البيانات التي تتم مزامنتها من Blue Yonder WFM إلى Shifts. الخيارات هي `Shift`، `SwapRequest`، `UserShiftPreferences`، `OpenShift`، `OpenShiftRequest`، ، `TimeOff`. `TimeOffRequest`
    - تحدد معلمة **enabledWfiScenarios** البيانات التي تتم مزامنتها من Shifts إلى Blue Yonder WFM. الخيارات هي `SwapRequest`, `OpenShiftRequest`, , `UserShiftPreferences``TimeOffRequest`.

    لمعرفة المزيد، راجع [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance). للاطلاع على قائمة خيارات المزامنة المعتمدة لكل معلمة، قم بتشغيل [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

    > [!IMPORTANT]
    > يتيح البرنامج النصي المزامنة لجميع هذه الخيارات. إذا كنت تريد تغيير إعدادات المزامنة، يمكنك القيام بذلك بعد إعداد الاتصال. لمعرفة المزيد، راجع [استخدام PowerShell لإدارة اتصال Shifts ب Blue Yonder Workforce Management](shifts-connector-powershell-manage.md).

1. إنشاء الاتصال.
1. تعيين مثيلات WFM أزرق إلى الفرق. تستند التعيينات إلى معرفات مثيل Blue Yonder WFM وTeamIds التي تقوم بإدخالها أو الفرق الجديدة التي تقوم بإنشائها، اعتمادا على البرنامج النصي الذي تقوم بتشغيله. إذا كان لدى الفريق جدول زمني موجود، يزيل البرنامج النصي بيانات الجدول للنطاق الزمني والتاريخ الذي تحدده.

تشير رسالة النجاح على الشاشة إلى أنه تم إعداد الاتصال بنجاح.

## <a name="if-you-need-to-make-changes-to-a-connection"></a>إذا كنت بحاجة إلى إجراء تغييرات على اتصال

لإجراء تغييرات على اتصال بعد إعداده، راجع [استخدام PowerShell لإدارة اتصال الورديات ب Blue Yonder Workforce Management](shifts-connector-powershell-manage.md). على سبيل المثال، يمكنك تحديث إعدادات المزامنة وتعيينات الفريق وتعطيل المزامنة للاتصال.

## <a name="scripts"></a>البرامج النصيه

### <a name="set-up-a-connection-and-create-new-teams-to-map"></a>إعداد اتصال وإنشاء فرق جديدة لتعيينها

```powershell
#Map WFM instances to teams script
Write-Host "Map WFM sites to teams"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview)
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM super user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName
if ($testResult.Code -ne $NULL) {
    write $testResult
    throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create a connection instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Enter your Microsoft 365's user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency"

#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
$InstanceResponse = New-CsTeamsShiftsConnectionInstance -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -DesignatedActorId $teamsUserId -EnabledConnectorScenario $enabledConnectorScenario -EnabledWfiScenario $wfiSupportedScenario -SyncFrequencyInMin $syncFreq -ConnectorAdminEmail $AdminEmailList
$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
    Write-Host "Success"
} else {
    throw "Connector instance creation failed"
}

#Retrieve the list of WFM instances
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if ($WfmTeamIds -ne $NULL && $WfmTeamIds.Count -gt 0){
    [System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
    throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionWfmUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while ($true)
{

#Create a new Teams team with owner set to system account and name set to the site name
Write-Host "Creating a Teams team"
$teamsTeamName = Read-Host -Prompt "Input the Teams team name"
$Team = New-Team -DisplayName $teamsTeamName -Visibility "Public" -Owner $teamsUserId
Write-Host "Success"
$TeamsTeamId=$Team.GroupId

#Add users to the Team for Shifts
Write-Host "Adding users to Teams team"
$currentUser = Read-Host -Prompt "Input the current user's user name or ID"
Add-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
$failedWfmUsers=@()
foreach ($user in $WFMUsers) {
    try {
    $userEmail = $user.Name + "@" +$domain
    Add-TeamUser -GroupId $TeamsTeamId -User $userEmail
    } catch {
        $failedWfmUsers+=$user
    }
}
if($failedWfmUsers.Count -gt 0){
    Write-Host "There are WFM users not existed in Teams tenant:"
    write $failedWfmUsers
}

#Enable scheduling in the group
$RequestBody = @{
    Enabled = $true
    TimeZone = "America/Los_Angeles"
}
$teamUpdateUrl="https://graph.microsoft.com/v1.0/teams/"+$TeamsTeamId+"/schedule"
$Schedule = Invoke-MgGraphRequest -Uri $teamUpdateUrl -Method PUT -Body $RequestBody

#Create a mapping of the new team to the WFM instance
Write-Host "Create a mapping of the new team to the site"
$TimeZone = Read-Host -Prompt "Input the time zone of team mapping"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone $TimeZone -WfmTeamId $WfmTeamId
Write-Host "Success"

$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}

#The Teams admin was set as an owner directly when creating a new team, removing it from owners
Remove-TeamUser -GroupId $TeamsTeamId -User $currentUser -Role Owner
Disconnect-MgGraph
```

### <a name="set-up-a-connection-and-map-to-existing-teams"></a>إعداد اتصال وتعيين إلى الفرق الموجودة

```powershell
#Map WFM sites to existing teams script
Write-Host "Map WFM sites to existing teams"
Start-Sleep 1

#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#Connect to MS Graph
Connect-MgGraph -Scopes "User.Read.All","Group.ReadWrite.All"

#List connector types available (comment out if not implemented for preview)
Write-Host "Listing connector types available"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$connectors = Get-CsTeamsShiftsConnectionConnector
write $connectors
$blueYonder = $connectors | where {$_.Id -match $BlueYonderId}
$enabledConnectorScenario = $blueYonder.SupportedScenario
$wfiSupportedScenario = $blueYonder.wfiSupportedScenario

#Prompt for entering of WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM super user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Test connection settings
Write-Host "Testing connection settings"
$InstanceName = Read-Host -Prompt 'Input connection instance name'
$adminApiUrl = Read-Host -Prompt 'Input admin api url'
$cookieAuthUrl = Read-Host -Prompt 'Input cookie authorization url'
$essApiUrl = Read-Host -Prompt 'Input ess api url'
$federatedAuthUrl = Read-Host -Prompt 'Input federated authorization url'
$retailWebApiUrl = Read-Host -Prompt 'Input retail web api url'
$siteManagerUrl = Read-Host -Prompt 'Input site manager url'
$testResult = Test-CsTeamsShiftsConnectionValidate -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName
if ($testResult.Code -ne $NULL) {
    write $testResult
    throw "Validation failed, conflict found"
}
Write-Host "Test complete, no conflicts found"

#Create a connection instance (includes WFM site team ids)
Write-Host "Creating a connection instance"
$designatorName = Read-Host -Prompt "Enter your Microsoft 365 user name"
$domain = $designatorName.Split("@")[1]
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$syncFreq = Read-Host -Prompt "Input sync frequency in minutes. Value should be equal to or more than 10."

#Read admin email list
[psobject[]]$AdminEmailList = @()
while ($true){
$AdminEmail = Read-Host -Prompt "Enter admin's email to receive error report"
$AdminEmailList += $AdminEmail
$title    = 'Adding another email'
$question = 'Would you like to add another admin email?'
$choices  = '&Yes', '&No'
$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
$InstanceResponse = New-CsTeamsShiftsConnectionInstance -Name $InstanceName -ConnectorId $BlueYonderId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -DesignatedActorId $teamsUserId -EnabledConnectorScenario $enabledConnectorScenario -EnabledWfiScenario $wfiSupportedScenario -SyncFrequencyInMin $syncFreq -ConnectorAdminEmail AdminEmailList

$InstanceId = $InstanceResponse.id
$Etag = $InstanceResponse.etag
if ($InstanceId -ne $null){
    Write-Host "Success"
} else {
    throw "Connector instance creation failed"
}

#Retrieve the list of WFM instances
Write-Host "Listing the WFM team sites"
$WfmTeamIds = Get-CsTeamsShiftsConnectionWfmTeam -ConnectorInstanceId $InstanceId
write $WfmTeamIds
if ($WfmTeamIds -ne $NULL && $WfmTeamIds.Count -gt 0){
    [System.String]$WfmTeamId = Read-Host -Prompt "Input the ID of WFM team you want to map"
}
else {
    throw "The WfmTeamId list is null or empty"
}

#Retrieve the list of WFM users and their roles
Write-Host "Listing WFM users and roles"
$WFMUsers = Get-CsTeamsShiftsConnectionWfmUser -ConnectorInstanceId $InstanceId -WfmTeamId $WfmTeamId
write $WFMUsers

#Keep mapping teams until user stops it
while ($true)
{

$TeamsTeamId = Read-Host -Prompt "Input the ID of the Teams team to be mapped"
#Clear schedule of the Teams team
Write-Host "Clear schedule of the existing team"
$startTime = Read-Host -Prompt "Input the start time of clear schedule"
$endTime = Read-Host -Prompt "Input the end time of clear schedule"

$entityTypeString = Read-Host -Prompt 'Input the entity types of clear schedule'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$entityType = $entityTypeString -Split {$Delimiters -contains $_}
$entityType = $entityType.Trim()
$entityType = $entityType.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
Remove-CsTeamsShiftsScheduleRecord -TeamId $TeamsTeamId -DateRangeStartDate $startTime -DateRangeEndDate $endTime -ClearSchedulingGroup:$True -EntityType $entityType -DesignatedActorId $$teamsUserId

#Create a mapping of the new team to the WFM instance
Write-Host "Create a mapping of the existing team to the site"
$TimeZone = Read-Host -Prompt "Input the time zone of team mapping"
$teamMappingResult = New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone $TimeZone -WfmTeamId $WfmTeamId
Write-Host "Success"


$title    = 'Connecting another team'
$question = 'Would you like to connect another team?'
$choices  = '&Yes', '&No'

$decision = $Host.UI.PromptForChoice($title, $question, $choices, 1)
if ($decision -eq 1) {
    break
}
}
Disconnect-MgGraph
```

## <a name="shifts-connector-cmdlets"></a>تبديل أوامر cmdlets الخاصة بالموصل

للحصول على تعليمات حول أوامر cmdlets لموصل Shifts، بما في ذلك cmdlets المستخدمة في البرامج النصية، ابحث عن **CsTeamsShiftsConnection** في [مرجع Teams PowerShell cmdlet](/powershell/teams/intro). فيما يلي ارتباطات لبعض أوامر cmdlets شائعة الاستخدام.

- [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation)
- [New-CsTeamsShiftsConnectionInstance](/powershell/module/teams/new-csteamsshiftsconnectioninstance)
- [Get-CsTeamsShiftsConnectionInstance](/powershell/module/teams/get-csteamsshiftsconnectioninstance)
- [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance)
- [Remove-CsTeamsShiftsConnectionInstance](/powershell/module/teams/remove-csteamsshiftsconnectioninstance)
- [Test-CsTeamsShiftsConnectionValidate](/powershell/module/teams/test-csteamsshiftsconnectionvalidate)
- [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap)
- [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap)
- [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap)
- [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector)
- [Get-CsTeamsShiftsConnectionSyncResult](/powershell/module/teams/get-csteamsshiftsconnectionsyncresult)
- [Get-CsTeamsShiftsConnectionWfmUser](/powershell/module/teams/get-csteamsshiftsconnectionwfmuser)
- [Get-CsTeamsShiftsConnectionWfmTeam](/powershell/module/teams/get-csteamsshiftsconnectionwfmteam)
- [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport)
- [Remove-CsTeamsShiftsScheduleRecord](/powershell/module/teams/remove-csteamsshiftsschedulerecord)

## <a name="related-articles"></a>المقالات ذات الصلة

- [موصلات الورديات](shifts-connectors.md)
- [استخدم PowerShell لإدارة اتصال الورديات ب Blue Yonder Workforce Management](shifts-connector-powershell-manage.md)
- [إدارة تطبيق الورديات](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [نظرة عامة على Teams PowerShell](/microsoftteams/teams-powershell-overview)
- [مرجع Cmdlet ل Teams PowerShell](/powershell/teams/intro)
