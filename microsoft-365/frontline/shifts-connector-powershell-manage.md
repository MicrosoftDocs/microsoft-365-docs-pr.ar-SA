---
title: استخدم PowerShell لإدارة اتصال الورديات ب Blue Yonder Workforce Management
author: LanaChin
ms.author: v-lanachin
ms.reviewer: ''
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية استخدام PowerShell لإدارة اتصال Shifts Workforce Management Blue Yonder.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 1064401dee3a25a7d1749db6e4a36a110f21da0b
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823668"
---
# <a name="use-powershell-to-manage-your-shifts-connection-to-blue-yonder-workforce-management"></a>استخدم PowerShell لإدارة اتصال الورديات ب Blue Yonder Workforce Management

## <a name="overview"></a>نظرة عامة

يمكنك [موصل Microsoft Teams Shifts ل Blue Yonder](shifts-connectors.md#microsoft-teams-shifts-connector-for-blue-yonder) من دمج تطبيق Shifts في Microsoft Teams مع Workforce Management Blue Yonder (Blue Yonder WFM). بعد إعداد اتصال، يمكن للعاملين في الخطوط الأمامية عرض جداولهم وإدارتها بسلاسة في Blue Yonder WFM من داخل الورديات.

يمكنك استخدام [معالج موصل Shifts](shifts-connector-wizard.md) في مركز مسؤولي Microsoft 365 أو [PowerShell](shifts-connector-blue-yonder-powershell-setup.md) لإعداد اتصال. بعد إعداد اتصال، يمكنك إدارته باستخدام [Shifts connector PowerShell cmdlets](#shifts-connector-cmdlets).

تصف هذه المقالة كيفية استخدام PowerShell للقيام بما يلي:

- [التحقق من حالة إعداد الاتصال](#check-connection-setup-status)
- [عرض تقرير خطأ لاتصال](#view-an-error-report-for-a-connection)
- [حل أخطاء الاتصال](#resolve-connection-errors)
- [تغيير إعدادات الاتصال](#change-connection-settings)
- [إلغاء تعيين فريق من اتصال وتعيينه إلى اتصال آخر](#unmap-a-team-from-one-connection-and-map-it-to-another-connection)
- [تعطيل المزامنة لاتصال](#disable-sync-for-a-connection)

> [!NOTE]
> تفترض هذه المقالة أنك قمت بالفعل بإعداد اتصال ب Blue Yonder WFM، إما باستخدام المعالج أو PowerShell.

## <a name="before-you-begin"></a>قبل البدء

[!INCLUDE [shifts-connector-admin-role](includes/shifts-connector-admin-role.md)]

## <a name="set-up-your-environment"></a>إعداد البيئة الخاصة بك

> [!NOTE]
> تأكد من اتباع هذه الخطوات لإعداد بيئتك قبل تشغيل أي من الأوامر أو البرامج النصية في هذه المقالة.

[!INCLUDE [shifts-connector-set-up-environment](includes/shifts-connector-set-up-environment.md)]

7. الاتصال ب Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    عند مطالبتك، سجل الدخول باستخدام بيانات اعتماد المسؤول. لقد أعددت الآن لتشغيل البرامج النصية في هذه المقالة وShifts connector cmdlets.

## <a name="check-connection-setup-status"></a>التحقق من حالة إعداد الاتصال

<a name="setup_status"> </a>

للتحقق من حالة الاتصال الذي قمت بإعداده باستخدام معرف العملية الذي تلقيته بالبريد الإلكتروني:

1. [قم بإعداد بيئتك](#set-up-your-environment) (إذا لم تكن قد أنشأتها بالفعل).
1. قم بتشغيل الأمر التالي. يمنحك هذا الأمر الحالة الإجمالية لتعيينات الفريق للاتصال.

    ``` powershell
    Get-CsTeamsShiftsConnectionOperation -OperationId <YourOperationId>
    ```

لمعرفة المزيد، راجع [Get-CsTeamsShiftsConnectionOperation](/powershell/module/teams/get-csteamsshiftsconnectionoperation).

## <a name="view-an-error-report-for-a-connection"></a>عرض تقرير خطأ لاتصال

<a name="error_report"> </a>

يمكنك تشغيل تقرير يعرض تفاصيل الخطأ لاتصال. يسرد التقرير تعيينات الفريق والمستخدم التي نجحت وفشلت. كما يوفر معلومات حول أي مشكلات متعلقة بالحسابات المقترنة بالاتصال.

1. [قم بإعداد بيئتك](#set-up-your-environment) (إذا لم تكن قد أنشأتها بالفعل).
1. الحصول على قائمة بتقارير الأخطاء لاتصال.

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. لعرض تقرير خطأ معين، قم بتشغيل الأمر التالي:

    ``` powershell
    Get-CsTeamsShiftsConnectionErrorReport -ErrorReportId <ErrorReportId>
    ```

لمعرفة المزيد، راجع [Get-CsTeamsShiftsConnectionErrorReport](/powershell/module/teams/get-csteamsshiftsconnectionerrorreport).

## <a name="resolve-connection-errors"></a>حل أخطاء الاتصال

### <a name="user-mapping-errors"></a>أخطاء تعيين المستخدم

قد تحدث أخطاء تعيين المستخدم إذا لم يكن مستخدم واحد أو أكثر في مثيل Blue Yonder WFM عضوا في الفريق المعين في Teams. لحل هذه المشكلة، تأكد من أن المستخدمين في الفريق المعين يتطابقون مع المستخدمين في مثيل WFM Blue Yonder.

لعرض تفاصيل المستخدمين غير المعينين، [قم بإعداد البيئة الخاصة بك](#set-up-your-environment) (إذا لم تكن قد قمت بالفعل)، ثم قم بتشغيل البرنامج النصي التالي.

```powershell
#View sync errors script
Write-Host "View sync errors"
Start-Sleep 1

#Ensure Teams module is of version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#List connection instances available
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to retrieve user sync results from'
}
else {
    throw "Instance list is empty"
}

#Get a list of the mappings
Write-Host "Listing team mappings"
$mappings = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $mappings

#For each mapping, retrieve the failed mappings
ForEach ($mapping in $mappings){
    $teamsTeamId = $mapping.TeamId
    $wfmTeamId = $mapping.WfmTeamId
    Write-Host "Failed mapped users in the mapping of ${teamsTeamId} and ${wfmTeamId}:"
    $userSyncResult = Get-CsTeamsShiftsConnectionSyncResult -ConnectorInstanceId $InstanceId -TeamId $teamsTeamId
    Write-Host "Failed AAD users:"
    write $userSyncResult.FailedAadUser
    Write-Host "Failed WFM users:"
    write $userSyncResult.FailedWfmUser
}
```

### <a name="account-authorization-errors"></a>أخطاء تخويل الحساب

قد تحدث أخطاء في تخويل الحساب إذا كان حساب خدمة WFM Blue Yonder أو بيانات اعتماد حساب نظام Microsoft 365 غير صحيح أو لم يكن لديه الأذونات المطلوبة.

لتغيير حساب خدمة WFM Blue Yonder أو بيانات اعتماد حساب نظام Microsoft 365 للاتصال، يمكنك تشغيل [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) cmdlet أو استخدام البرنامج النصي PowerShell في قسم [إعدادات الاتصال "تغيير](#change-connection-settings)" في هذه المقالة.

## <a name="change-connection-settings"></a>تغيير إعدادات الاتصال
<a name="change_settings"> </a>

استخدم هذا البرنامج النصي لتغيير إعدادات الاتصال. تتضمن الإعدادات التي يمكنك تغييرها حساب خدمة Blue Yonder WFM وكلمة المرور وحساب نظام Microsoft 365 وتعيينات الفريق وإعدادات المزامنة.

تتضمن إعدادات المزامنة تكرار المزامنة (بالدقائق) وبيانات الجدولة التي تتم مزامنتها بين WFM وShifts Blue Yonder. يتم تعريف بيانات الجدولة في المعلمات التالية، والتي يمكنك عرضها عن طريق تشغيل [Get-CsTeamsShiftsConnectionConnector](/powershell/module/teams/get-csteamsshiftsconnectionconnector).

- تحدد المعلمة **enabledConnectorScenarios** البيانات التي تتم مزامنتها من Blue Yonder WFM إلى Shifts. الخيارات هي `Shift`، `SwapRequest`، `UserShiftPreferences`، `OpenShift`، `OpenShiftRequest`، ، `TimeOff`. `TimeOffRequest`
- تحدد معلمة **enabledWfiScenarios** البيانات التي تتم مزامنتها من Shifts إلى Blue Yonder WFM. الخيارات هي `SwapRequest`, `OpenShiftRequest`, , `UserShiftPreferences``TimeOffRequest`.

    > [!NOTE]
    > إذا اخترت عدم مزامنة الورديات المفتوحة أو طلبات الورديات المفتوحة أو طلبات التبديل أو طلبات الإجازة بين الورديات WFM Blue Yonder، فهناك خطوة أخرى تحتاج إلى القيام بها لإخفاء الإمكانية في الورديات. بعد تشغيل هذا البرنامج النصي، تأكد من اتباع الخطوات الواردة في قسم [تعطيل الورديات المفتوحة، وفتح طلبات الورديات، وطلبات التبديل، وطلبات الإجازة](#disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests) لاحقا في هذه المقالة.

> [!IMPORTANT]
> بالنسبة للإعدادات التي لا تريد تغييرها، ستحتاج إلى إعادة إدخال الإعدادات الأصلية عندما يطلب منك البرنامج النصي.

[قم بإعداد البيئة الخاصة بك](#set-up-your-environment) (إذا لم تكن قد قمت بالفعل)، ثم قم بتشغيل البرنامج النصي التالي.

```powershell
#Update connector instance and mapping script
Write-Host "Update connector instance and mapping"
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

#List connection instances available
Write-Host "Listing connection instances available"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Prompt for the WFM username and password
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

#Get the instance ID
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$InstanceId = Read-Host -Prompt 'Input the instance ID that you want to update'
$Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
$Etag = $Instance.etag

#Change sync setting
$designatorName = Read-Host -Prompt "Input designated actor's user name"
$designator = Get-MgUser -UserId $designatorName
$teamsUserId = $designator.Id
$UpdatedInstanceName = Read-Host -Prompt 'Input new connection instance name'
$updatedConnectorScenarioString = Read-Host -Prompt 'Input new enabled connector scenarios'
$updatedWfiScenarioString = Read-Host -Prompt 'Input new enabled WFI scenarios'
$Delimiters = ",", ".", ":", ";", " ", "`t"
$updatedConnectorScenario = $updatedConnectorScenarioString -Split {$Delimiters -contains $_}
$updatedConnectorScenario = $updatedConnectorScenario.Trim()
$updatedConnectorScenario = $updatedConnectorScenario.Split('',[System.StringSplitOptions]::RemoveEmptyEntries)
$updatedWfiScenario = $updatedWfiScenarioString -Split {$Delimiters -contains $_}
$updatedWfiScenario = $updatedWfiScenario.Trim()
$updatedWfiScenario = $updatedWfiScenario.Split('', [System.StringSplitOptions]::RemoveEmptyEntries)
$adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
$cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
$essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
$federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
$retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
$siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
$syncFreq = Read-Host -Prompt 'Input new sync frequency'

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
$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $teamsUserId -EnabledConnectorScenario $updatedConnectorScenario -EnabledWfiScenario $updatedWfiScenario -Name $UpdatedInstanceName -SyncFrequencyInMin $syncFreq -IfMatch $Etag -ConnectorAdminEmail $AdminEmailList

#Get a list of the mappings
Write-Host "Listing mappings"
$TeamMaps = Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId
write $TeamMaps

#Modify a mapping
#Remove a mapping
Write-Host "Removing a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to unlink'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to unlink'
Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId
Write-Host "Success"

#Add a mapping
Write-Host "Adding a mapping"
$TeamsTeamId = Read-Host -Prompt 'Input the Teams team ID that you want to link'
$WfmTeamId = Read-Host -Prompt 'Input the WFM team ID that you want to link'
New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId $InstanceId -TeamId $TeamsTeamId -TimeZone "America/Los_Angeles" -WfmTeamId $WfmTeamId
Write-Host "Success"
```

## <a name="disable-open-shifts-open-shifts-requests-swap-requests-and-time-off-requests"></a>تعطيل الورديات المفتوحة وطلبات الورديات المفتوحة وطلبات التبديل وطلبات الإجازة

> [!IMPORTANT]
> اتبع هذه الخطوات فقط إذا اخترت تعطيل الورديات المفتوحة أو طلبات الوردية المفتوحة أو طلبات التبديل أو طلبات الإجازة باستخدام البرنامج النصي في قسم [إعدادات الاتصال "تغيير](#change-connection-settings) " الموجود سابقا في هذه المقالة أو باستخدام [Set-CsTeamsShiftsConnectionInstance](/powershell/module/teams/set-csteamsshiftsconnectioninstance) cmdlet. يؤدي إكمال هذه الخطوة إلى إخفاء الإمكانية في Shifts. بدون هذه الخطوة الثانية، سيظل المستخدمون يرون الإمكانية في Shifts، وسيحصلون على رسالة خطأ "عملية غير معتمدة" إذا حاولوا استخدامها.

لإخفاء الورديات المفتوحة وطلبات التبديل وطلبات الإجازة في الورديات، استخدم [نوع مورد جدولة](/graph/api/resources/schedule) واجهة برمجة التطبيقات Graph لتعيين المعلمات ```false``` التالية لكل فريق قمت بتعيينه إلى مثيل WFM أزرق:

- الورديات المفتوحة: ```openShiftsEnabled```
- طلبات التبديل:  ```swapShiftsRequestsEnabled```
- طلبات الإجازة: ```timeOffRequestsEnabled```

لإخفاء طلبات الورديات المفتوحة في الورديات، انتقل إلى **الإعدادات** في الورديات، ثم أوقف تشغيل إعداد **"الورديات المفتوحة** ".

## <a name="unmap-a-team-from-one-connection-and-map-it-to-another-connection"></a>إلغاء تعيين فريق من اتصال وتعيينه إلى اتصال آخر

> [!NOTE]
> يجب أن يكون حساب نظام Microsoft 365 هو نفسه لكلا الاتصالين. إذا لم يكن كذلك، فستتلقى رسالة الخطأ "ملف تعريف الممثل المعين هذا لا يحتوي على امتيازات ملكية الفريق".

إذا كنت تريد إلغاء تعيين فريق من اتصال واحد وتعيينه إلى اتصال آخر:

1. [قم بإعداد بيئتك](#set-up-your-environment) (إذا لم تكن قد أنشأتها بالفعل).
1. عرض قائمة بكافة تعيينات الفريق للاتصال.

    ```powershell
    Get-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId>
    ```

1. إزالة تعيين فريق من الاتصال.

    ```powershell
    Remove-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId>
    ```

1. تعيين الفريق إلى اتصال آخر.

    ```powershell
    New-CsTeamsShiftsConnectionTeamMap -ConnectorInstanceId <ConnectorInstanceId> -TeamId <TeamId> -WfmTeamId <SiteId> -TimeZone <TimeZone>
    ```

لمعرفة المزيد، راجع [Get-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/get-csteamsshiftsconnectionteammap) و [Remove-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/remove-csteamsshiftsconnectionteammap) و [New-CsTeamsShiftsConnectionTeamMap](/powershell/module/teams/new-csteamsshiftsconnectionteammap).

## <a name="disable-sync-for-a-connection"></a>تعطيل المزامنة لاتصال

استخدم هذا البرنامج النصي لتعطيل المزامنة للاتصال. ضع في اعتبارك أن هذا البرنامج النصي لا يزيل اتصالا أو يحذفه. يؤدي ذلك إلى إيقاف المزامنة بحيث لا تتم مزامنة أي بيانات بين Shifts و Blue Yonder WFM للاتصال الذي تحدده.

[قم بإعداد البيئة الخاصة بك](#set-up-your-environment) (إذا لم تكن قد قمت بالفعل)، ثم قم بتشغيل البرنامج النصي التالي.

```powershell
#Disable sync script
Write-Host "Disable sync"
#Ensure Teams module is at least version x
Write-Host "Checking Teams module version"
try {
    Get-InstalledModule -Name "MicrosoftTeams" -MinimumVersion 4.1.0
} catch {
    throw
}

#List connection instances available
Write-Host "Listing connection instances"
$InstanceList = Get-CsTeamsShiftsConnectionInstance
write $InstanceList

#Get an instance
if ($InstanceList.Count -gt 0){
    $InstanceId = Read-Host -Prompt 'Input the instance ID that you want to disable sync'
    $Instance = Get-CsTeamsShiftsConnectionInstance -ConnectorInstanceId $InstanceId
    $Etag = $Instance.etag
    $InstanceName = $Instance.Name
    $DesignatedActorId = $Instance.designatedActorId
    $adminApiUrl = $Instance.ConnectorSpecificSettingAdminApiUrl
    $cookieAuthUrl = $Instance.ConnectorSpecificSettingCookieAuthUrl
    $essApiUrl = $Instance.ConnectorSpecificSettingEssApiUrl
    $federatedAuthUrl = $Instance.ConnectorSpecificSettingFederatedAuthUrl
    $retailWebApiUrl = $Instance.ConnectorSpecificSettingRetailWebApiUrl
    $siteManagerUrl = $Instance.ConnectorSpecificSettingSiteManagerUrl
    $ConnectorAdminEmail = $Instance.ConnectorAdminEmail
}
else {
    throw "Instance list is empty"
}

#Remove scenarios in the mapping
Write-Host "Disabling scenarios in the team mapping"
$UpdatedInstanceName = $InstanceName + " - Disabled"
$BlueYonderId = "6A51B888-FF44-4FEA-82E1-839401E9CD74"
$WfmUserName = Read-Host -Prompt 'Input your WFM user name'
$WfmPwd = Read-Host -Prompt 'Input your WFM password' -AsSecureString
$plainPwd =[Runtime.InteropServices.Marshal]::PtrToStringAuto([Runtime.InteropServices.Marshal]::SecureStringToBSTR($WfmPwd))

$UpdatedInstance = Set-CsTeamsShiftsConnectionInstance -ConnectorId $BlueYonderId -ConnectorInstanceId $InstanceId -ConnectorSpecificSettingAdminApiUrl $adminApiUrl -ConnectorSpecificSettingCookieAuthUrl $cookieAuthUrl -ConnectorSpecificSettingEssApiUrl $essApiUrl -ConnectorSpecificSettingFederatedAuthUrl $federatedAuthUrl -ConnectorSpecificSettingLoginPwd $plainPwd -ConnectorSpecificSettingLoginUserName $WfmUserName -ConnectorSpecificSettingRetailWebApiUrl $retailWebApiUrl -ConnectorSpecificSettingSiteManagerUrl $siteManagerUrl -DesignatedActorId $DesignatedActorId -EnabledConnectorScenario @() -EnabledWfiScenario @() -Name $UpdatedInstanceName -SyncFrequencyInMin 60 -IfMatch $Etag -ConnectorAdminEmail $ConnectorAdminEmail

if ($UpdatedInstance.Id -ne $null) {
    Write-Host "Success"
}
else {
    throw "Update instance failed"
}
```

## <a name="shifts-connector-cmdlets"></a>تبديل أوامر cmdlets الخاصة بالموصل

للحصول على تعليمات حول أوامر cmdlets لموصل Shifts، ابحث عن **CsTeamsShiftsConnection** في [مرجع Teams PowerShell cmdlet](/powershell/teams/intro). فيما يلي ارتباطات لبعض أوامر cmdlets شائعة الاستخدام.

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
- [استخدم معالج موصل Shifts لتوصيل الورديات ب Blue Yonder Workforce Management](shifts-connector-wizard.md)
- [استخدم PowerShell لتوصيل الورديات ب Blue Yonder Workforce Management](shifts-connector-blue-yonder-powershell-setup.md)
- [إدارة تطبيق الورديات](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [نظرة عامة على Teams PowerShell](/microsoftteams/teams-powershell-overview)
