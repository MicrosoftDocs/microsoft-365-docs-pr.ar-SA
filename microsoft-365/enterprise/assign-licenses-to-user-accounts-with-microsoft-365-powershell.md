---
title: تعيين Microsoft 365 جديدة إلى حسابات المستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: b9f076e4856820d9f10e4cf92718dd6ddd3971c5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569966"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a>تعيين Microsoft 365 جديدة إلى حسابات المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

لا يمكن للمستخدمين استخدام أي Microsoft 365 حتى يتم تعيين ترخيص لحسابهم من خطة ترخيص. يمكنك استخدام PowerShell لتعيين التراخيص بسرعة إلى حسابات غير مرخصة. 

يجب أولا تعيين موقع إلى حسابات المستخدمين. إن تحديد موقع هو جزء مطلوب لإنشاء حساب مستخدم جديد في [مركز مسؤولي Microsoft 365.](../admin/add-users/add-users.md) 

بشكل افتراضي، لا يتم تحديد موقع للحسابات التي تم مزامنتها من خدمات مجال Active Directory المحلية. يمكنك تكوين موقع لهذه الحسابات من:

- مركز مسؤولي Microsoft 365
 - [PowerShell](configure-user-account-properties-with-microsoft-365-powershell.md)
 - مدخل [Azure](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal) (**مستخدمو Active Directory** >  **>** حساب المستخدم > **ProfileContact** >  **infoCountry** >  أو المنطقة).

>[!Note]
>[تعرف على كيفية تعيين تراخيص إلى حسابات المستخدمين](../admin/manage/assign-licenses-to-users.md) باستخدام مركز مسؤولي Microsoft 365. للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

بعد ذلك، سرد خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، احصل على اسم تسجيل الدخول للحساب الذي تريد إضافة ترخيص له، المعروف أيضا بالاسم الرئيسي للمستخدم (UPN).

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

وأخيرا، حدد اسم تسجيل الدخول للمستخدم واسم خطة الترخيص و قم بتشغيل هذه الأوامر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

تجدر الإشارة إلى أننا سنبدأ في إهمال هذه الوحدة النمطية عندما تتوفر وظيفة هذه الوحدة النمطية في وحدة [Azure Active Directory PowerShell](/powershell/azuread/v2/azureactivedirectory) Graph النمطية الجديدة. ننصح العملاء الذين يستخدمون برامج PowerShell النصية الجديدة باستخدام الوحدة النمطية الجديدة بدلا من هذه الوحدة النمطية.

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

تشغيل الأمر `Get-MsolAccountSku` لعرض خطط الترخيص المتوفرة وعدد التراخيص المتوفرة في كل خطة في مؤسستك. عدد التراخيص المتوفرة في كل خطة هو ActiveUnitsWarningUnitsConsumedUnits -  - . لمزيد من المعلومات حول خطط الترخيص والتراخيص والخدمات، راجع عرض التراخيص [والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

للعثور على الحسابات غير مرخصة في مؤسستك، يمكنك تشغيل هذا الأمر.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

يمكنك فقط تعيين التراخيص إلى حسابات المستخدمين التي تم تعيين الخاصية **UsageLocation** لها إلى رمز بلد ISO 3166-1 alpha-2 صالح. على سبيل المثال، الولايات المتحدة الأمريكية و FR لفرنسا. بعض Microsoft 365 الخدمات غير متوفرة في بلدان معينة. لمزيد من المعلومات، راجع [حول قيود الترخيص](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
للعثور على حسابات لا تملك قيمة **UsageLocation** ، يمكنك تشغيل هذا الأمر.

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
    
إذا كنت تستخدم **الأمر Cmdlet Get-MsolUser** بدون استخدام **المعلمة -All** ، يتم إرجاع أول 500 حساب فقط.

### <a name="assigning-licenses-to-user-accounts"></a>تعيين التراخيص إلى حسابات المستخدمين
    
لتعيين ترخيص لمستخدم، استخدم الأمر التالي في PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

يعين هذا المثال ترخيصا من خطة ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) إلى **belindan\@** المستخدم غير المرخص litwareinc.com:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

لتعيين ترخيص لجميع المستخدمين غير المرخصين، قم بتشغيل هذا الأمر.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>لا يمكنك تعيين تراخيص متعددة لمستخدم من خطة الترخيص نفسها. إذا لم يكن لديك ما يكفي من التراخيص المتوفرة، يتم تعيين التراخيص للمستخدمين بالترتيب الذي يتم إرجاعه بواسطة أمر cmdlet **Get-MsolUser** حتى نهاية التراخيص المتوفرة.
>

يعين هذا المثال التراخيص من خطة ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) إلى جميع المستخدمين غير المرخصين:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

يعين هذا المثال هذه التراخيص نفسها للمستخدمين غير المرخصين في قسم المبيعات في الولايات المتحدة:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>نقل مستخدم إلى اشتراك آخر (خطة ترخيص) باستخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
بعد ذلك، احصل على اسم تسجيل الدخول لحساب المستخدم الذي تريد تبديل الاشتراكات له، المعروف أيضا بالاسم الرئيسي للمستخدم (UPN).

بعد ذلك، سرد الاشتراكات (خطط الترخيص) للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، سرد الاشتراكات التي لدى حساب المستخدم حاليا باستخدام هذه الأوامر.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

تحديد الاشتراك الذي لدى المستخدم حاليا (اشتراك FROM) والاشتراك الذي ينتقل المستخدم له (اشتراك TO).

وأخيرا، حدد اسمي الاشتراكين TO و FROM (أرقام جزء SKU) ثم قم بتشغيل هذه الأوامر.

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
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
