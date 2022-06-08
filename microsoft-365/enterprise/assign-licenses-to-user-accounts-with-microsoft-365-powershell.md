---
title: تعيين تراخيص Microsoft 365 لحسابات المستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell لتعيين ترخيص Microsoft 365 للمستخدمين غير المرخصين.
ms.openlocfilehash: a336c932ca31cc145e50baaaf9c77a992f39ab33
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940371"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>تعيين تراخيص Microsoft 365 لحسابات المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise وOffice 365 Enterprise.*

لا يمكن للمستخدمين استخدام أي خدمات Microsoft 365 حتى يتم تعيين ترخيص لحسابهم من خطة ترخيص. يمكنك استخدام PowerShell لتعيين التراخيص بسرعة للحسابات غير المرخصة. 

يجب أولا تعيين موقع لحسابات المستخدمين. يعد تحديد موقع جزءا مطلوبا لإنشاء حساب مستخدم جديد في [مركز إدارة Microsoft 365](../admin/add-users/add-users.md). 

الحسابات التي تتم مزامنتها من خدمات مجال Active Directory المحلية لا يكون لها موقع محدد بشكل افتراضي. يمكنك تكوين موقع لهذه الحسابات من:

- مركز مسؤولي Microsoft 365
- [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
- مدخل [Microsoft Azure](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**مستخدمو** **Active Directory** >  > حساب المستخدم >**بلد معلومات** >  **جهة اتصال** **ملف التعريف** >  أو المنطقة).

>[!Note]
>[تعرف على كيفية تعيين تراخيص لحسابات المستخدمين](../admin/manage/assign-licenses-to-users.md) باستخدام مركز إدارة Microsoft 365. للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>استخدام Microsoft Graph PowerShell SDK

أولا، [اتصل بمستأجر Microsoft 365](/graph/powershell/get-started#authentication).

يتطلب تعيين تراخيص لمستخدم وإزالتها نطاق أذونات User.ReadWrite.All أو أحد الأذونات الأخرى المدرجة في [الصفحة المرجعية لواجهة برمجة تطبيقات الرسم البياني 'تعيين الترخيص'](/graph/api/user-assignlicense).

نطاق أذونات Organization.Read.All مطلوب لقراءة التراخيص المتوفرة في المستأجر.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

`Get-MgSubscribedSku` قم بتشغيل الأمر لعرض خطط الترخيص المتوفرة وعدد التراخيص المتوفرة في كل خطة في مؤسستك. عدد التراخيص المتوفرة في كل خطة هو **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. لمزيد من المعلومات حول خطط الترخيص والتراخيص والخدمات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

للبحث عن الحسابات غير المرخصة في مؤسستك، قم بتشغيل هذا الأمر.

```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All
```

يمكنك فقط تعيين التراخيص لحسابات المستخدمين التي تم تعيين **الخاصية UsageLocation** إلى رمز بلد ISO 3166-1 alpha-2 صالح. على سبيل المثال، الولايات المتحدة للولايات المتحدة، وFR ل فرنسا. لا تتوفر بعض خدمات Microsoft 365 في بعض البلدان. لمزيد من المعلومات، راجع ["حول قيود الترخيص](https://go.microsoft.com/fwlink/p/?LinkId=691730)".

للبحث عن حسابات لا تحتوي على قيمة **UsageLocation** ، قم بتشغيل هذا الأمر.

```powershell
Get-MgUser -Select Id,DisplayName,Mail,UserPrincipalName,UsageLocation,UserType | where { $_.UsageLocation -eq $null -and $_.UserType -eq 'Member' }
```

لتعيين قيمة **UsageLocation** على حساب، قم بتشغيل هذا الأمر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"

Update-MgUser -UserId $userUPN -UsageLocation $userLoc
```

على سبيل المثال:

```powershell
Update-MgUser -UserId "belindan@litwareinc.com" -UsageLocation US
```

إذا كنت تستخدم **Get-MgUser** cmdlet دون استخدام المعلمة **-All** ، يتم إرجاع أول 100 حساب فقط.

### <a name="assigning-licenses-to-user-accounts"></a>تعيين تراخيص لحسابات المستخدمين

لتعيين ترخيص لمستخدم، استخدم الأمر التالي في PowerShell.
  
```powershell
Set-MgUserLicense -UserId $userUPN -AddLicenses @{SkuId = "<SkuId>"} -RemoveLicenses @()
```

يعين هذا المثال ترخيصا من خطة ترخيص **SPE_E5** (Microsoft 365 E5) **إلى litwareinc.com المستخدم\@** غير المرخص:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

يعين هذا المثال **SPE_E5** (Microsoft 365 E5) و **EMSPREMIUM** (ENTERPRISE MOBILITY + SECURITY E5) إلى المستخدم **besoftn\@litwareinc.com**:
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$e5EmsSku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'EMSPREMIUM'
$addLicenses = @(
    @{SkuId = $e5Sku.SkuId},
    @{SkuId = $e5EmsSku.SkuId}
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

يعين هذا المثال **SPE_E5** (Microsoft 365 E5) مع إيقاف تشغيل خدمات **MICROSOFTBOOKINGS** (Microsoft Bookings **) LOCKBOX_ENTERPRISE (** Customer Lockbox):
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

يقوم هذا المثال بتحديث مستخدم **باستخدام SPE_E5** (Microsoft 365 E5) وإيقاف تشغيل خطط خدمة Sway و Forms مع ترك الخطط المعطلة الموجودة للمستخدم في حالته الحالية:
  
```powershell
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

### <a name="assign-licenses-to-a-user-by-copying-the-license-assignment-from-another-user"></a>تعيين التراخيص لمستخدم عن طريق نسخ تعيين الترخيص من مستخدم آخر

يعين هذا المثال **litwareinc.com jamesp\@** بنفس خطة الترخيص التي تم تطبيقها على **litwareinc.com:\@**

```powershell
$mgUser = Get-MgUser -UserId "belindan@litwareinc.com"
Set-MgUserLicense -UserId "jamesp@litwareinc.com" -AddLicenses $mgUser.AssignedLicenses -RemoveLicenses @()
```

### <a name="move-a-user-to-a-different-subscription-license-plan"></a>نقل مستخدم إلى اشتراك مختلف (خطة ترخيص)

يقوم هذا المثال بترقية مستخدم من خطة ترخيص **SPE_E3** (Microsoft 365 E3) إلى خطة ترخيص **SPE_E5** (Microsoft 365 E5):

```powershell
$e3Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E3'
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

# Unassign E3
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{} -RemoveLicenses @($e3Sku.SkuId)
# Assign E5
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()
```

يمكنك التحقق من التغيير في الاشتراك لحساب المستخدم باستخدام هذا الأمر.

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية للرسم البياني

>[!Note]
>من المقرر إيقاف Set-AzureADUserLicense cmdlet. الرجاء ترحيل البرامج النصية إلى cmdlet Set-MgUserLicense Microsoft Graph كما هو موضح أعلاه. لمزيد من المعلومات، راجع [ترحيل تطبيقاتك للوصول إلى واجهات برمجة تطبيقات إدارة التراخيص من Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

بعد ذلك، قم بإدراج خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، احصل على اسم تسجيل الدخول للحساب الذي تريد إضافة ترخيص إليه، والمعروف أيضا باسم اسم المستخدم الأساسي (UPN).

بعد ذلك، تأكد من تعيين موقع استخدام لحساب المستخدم.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

إذا لم يتم تعيين موقع استخدام، يمكنك تعيين موقع باستخدام هذه الأوامر:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

وأخيرا، حدد اسم تسجيل دخول المستخدم واسم خطة الترخيص وقم بتشغيل هذه الأوامر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام وحدة Microsoft Azure Active Directory النمطية ل Windows PowerShell

>[!Note]
>من المقرر إيقاف أوامر cmdlets Set-MsolUserLicense New-MsolUser (-LicenseAssignment). الرجاء ترحيل البرامج النصية إلى cmdlet Set-MgUserLicense Microsoft Graph كما هو موضح أعلاه. لمزيد من المعلومات، راجع [ترحيل تطبيقاتك للوصول إلى واجهات برمجة تطبيقات إدارة التراخيص من Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

`Get-MsolAccountSku` قم بتشغيل الأمر لعرض خطط الترخيص المتوفرة وعدد التراخيص المتوفرة في كل خطة في مؤسستك. عدد التراخيص المتوفرة في كل خطة هو **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. لمزيد من المعلومات حول خطط الترخيص والتراخيص والخدمات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>لا يدعم PowerShell Core وحدة Microsoft Azure Active Directory النمطية لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

للبحث عن الحسابات غير المرخصة في مؤسستك، قم بتشغيل هذا الأمر.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

يمكنك فقط تعيين التراخيص لحسابات المستخدمين التي تم تعيين **الخاصية UsageLocation** إلى رمز بلد ISO 3166-1 alpha-2 صالح. على سبيل المثال، الولايات المتحدة للولايات المتحدة، وFR ل فرنسا. لا تتوفر بعض خدمات Microsoft 365 في بعض البلدان. لمزيد من المعلومات، راجع ["حول قيود الترخيص](https://go.microsoft.com/fwlink/p/?LinkId=691730)".
    
للبحث عن حسابات لا تحتوي على قيمة **UsageLocation** ، قم بتشغيل هذا الأمر.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

لتعيين قيمة **UsageLocation** على حساب، قم بتشغيل هذا الأمر.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

على سبيل المثال:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
إذا كنت تستخدم **Get-MsolUser** cmdlet دون استخدام المعلمة **-All** ، يتم إرجاع أول 500 حساب فقط.

### <a name="assigning-licenses-to-user-accounts"></a>تعيين تراخيص لحسابات المستخدمين
    
لتعيين ترخيص لمستخدم، استخدم الأمر التالي في PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

يعين هذا المثال ترخيصا من خطة ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) **إلى litwareinc.com المستخدم\@** غير المرخص:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

لتعيين ترخيص لجميع المستخدمين غير المرخصين، قم بتشغيل هذا الأمر.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>لا يمكنك تعيين تراخيص متعددة لمستخدم من خطة الترخيص نفسها. إذا لم يكن لديك ما يكفي من التراخيص المتوفرة، يتم تعيين التراخيص للمستخدمين بالترتيب الذي يتم إرجاعها به بواسطة **Get-MsolUser** cmdlet حتى نفاد التراخيص المتوفرة.
>

يعين هذا المثال تراخيص من خطة ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) لجميع المستخدمين غير المرخصين:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

يعين هذا المثال هذه التراخيص نفسها للمستخدمين غير المرخصين في قسم المبيعات في الولايات المتحدة:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>نقل مستخدم إلى اشتراك مختلف (خطة ترخيص) مع الوحدة النمطية Azure Active Directory PowerShell for Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
بعد ذلك، احصل على اسم تسجيل الدخول لحساب المستخدم الذي تريد تبديل الاشتراكات له، والمعروف أيضا باسم المستخدم الأساسي (UPN).

بعد ذلك، قم بإدراج الاشتراكات (خطط الترخيص) للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، قم بإدراج الاشتراكات التي يحتوي عليها حساب المستخدم حاليا باستخدام هذه الأوامر.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

تحديد الاشتراك الذي يمتلكه المستخدم حاليا (اشتراك FROM) والاشتراك الذي ينتقل إليه المستخدم (اشتراك TO).

وأخيرا، حدد أسماء اشتراكات TO و FROM (أرقام أجزاء SKU) وقم بتشغيل هذه الأوامر.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

يمكنك التحقق من التغيير في الاشتراك لحساب المستخدم باستخدام هذه الأوامر.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
