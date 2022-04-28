---
title: إزالة تراخيص Microsoft 365 من حسابات المستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/23/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: يشرح كيفية استخدام PowerShell لإزالة تراخيص Microsoft 365 التي تم تعيينها مسبقا للمستخدمين.
ms.openlocfilehash: b036f58686ac179fc93c1a0605ed2b585ea89c30
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096315"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>إزالة تراخيص Microsoft 365 من حسابات المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

>[!Note]
>[تعرف على كيفية إزالة التراخيص من حسابات المستخدمين](../admin/manage/remove-licenses-from-users.md) باستخدام مركز مسؤولي Microsoft 365. للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>استخدام Microsoft Graph PowerShell SDK

أولا، [اتصل بمستأجر Microsoft 365](/graph/powershell/get-started#authentication).

يتطلب تعيين تراخيص لمستخدم وإزالتها نطاق أذونات User.ReadWrite.All أو أحد الأذونات الأخرى المدرجة في [الصفحة المرجعية "تعيين ترخيص" Graph واجهة برمجة التطبيقات](/graph/api/user-assignlicense).

نطاق أذونات Organization.Read.All مطلوب لقراءة التراخيص المتوفرة في المستأجر.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

لعرض معلومات خطة الترخيص في مؤسستك، راجع المواضيع التالية:

- [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)

- [عرض تفاصيل ترخيص الحساب والخدمة باستخدام PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)

### <a name="removing-licenses-from-user-accounts"></a>إزالة التراخيص من حسابات المستخدمين

لإزالة التراخيص من حساب مستخدم موجود، استخدم بناء الجملة التالي:
  
```powershell
Set-MgUserLicense -UserId "<Account>" -RemoveLicenses @("<AccountSkuId1>") -AddLicenses @{}
```

يزيل هذا المثال خطة ترخيص **SPE_E5** (Microsoft 365 E5) من **BelindaN@litwareinc.com** المستخدم:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -RemoveLicenses @($e5Sku.SkuId) -AddLicenses @{}
```

لإزالة كافة التراخيص من مجموعة من المستخدمين المرخصين الحاليين، استخدم بناء الجملة التالي:

```powershell
$licensedUsers = Get-MgUser -Filter 'assignedLicenses/$count ne 0' `
    -ConsistencyLevel eventual -CountVariable licensedUserCount -All `
    -Select UserPrincipalName,DisplayName,AssignedLicenses

foreach($user in $licensedUsers)
{
    $licencesToRemove = $user.AssignedLicenses | Select -ExpandProperty SkuId
    $user = Set-MgUserLicense -UserId $user.UserPrincipalName -RemoveLicenses $licencesToRemove -AddLicenses @{} 
}
```

هناك طريقة أخرى لتحرير ترخيص وهي حذف حساب المستخدم. لمزيد من المعلومات، راجع [حذف حسابات المستخدمين واستعادتها باستخدام PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

>من المقرر إيقاف Set-AzureADUserLicense cmdlet. الرجاء ترحيل البرامج النصية الخاصة بك إلى أمر cmdlet Set-MgUserLicense SDK ل Microsoft Graph كما هو موضح أعلاه. لمزيد من المعلومات، راجع [ترحيل تطبيقاتك للوصول إلى واجهات برمجة تطبيقات إدارة التراخيص من Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

بعد ذلك، قم بإدراج خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، احصل على اسم تسجيل الدخول للحساب الذي تريد إزالة ترخيص له، والمعروف أيضا باسم المستخدم الأساسي (UPN).

وأخيرا، حدد أسماء خطة تسجيل الدخول والترخيص للمستخدم، وقم بإزالة الأحرف "<" و">"، ثم قم بتشغيل هذه الأوامر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

لإزالة كافة التراخيص لحساب مستخدم معين، حدد اسم تسجيل دخول المستخدم، وقم بإزالة الأحرف "<" و">"، ثم قم بتشغيل هذه الأوامر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userList = Get-AzureADUser -ObjectID $userUPN
$Skus = $userList | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
    if($Skus -is [array])
    {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        for ($i=0; $i -lt $Skus.Count; $i++) {
            $licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

>[!Note]
>من المقرر إيقاف أوامر cmdlets Set-MsolUserLicense New-MsolUser (-LicenseAssignment). الرجاء ترحيل البرامج النصية الخاصة بك إلى أمر cmdlet Set-MgUserLicense SDK ل Microsoft Graph كما هو موضح أعلاه. لمزيد من المعلومات، راجع [ترحيل تطبيقاتك للوصول إلى واجهات برمجة تطبيقات إدارة التراخيص من Microsoft Graph](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/migrate-your-apps-to-access-the-license-managements-apis-from/ba-p/2464366).
>

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
لعرض معلومات خطة الترخيص (**AccountSkuID**) في مؤسستك، راجع المواضيع التالية:
    
  - [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [عرض تفاصيل ترخيص الحساب والخدمة باستخدام PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
إذا كنت تستخدم **Get-MsolUser** cmdlet دون استخدام المعلمة _-All_ ، يتم إرجاع أول 500 حساب فقط.
    
### <a name="removing-licenses-from-user-accounts"></a>إزالة التراخيص من حسابات المستخدمين

لإزالة التراخيص من حساب مستخدم موجود، استخدم بناء الجملة التالي:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

يزيل هذا المثال ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) من حساب المستخدم BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>لا يمكنك استخدام `Set-MsolUserLicense` cmdlet لإلغاء تعيين المستخدمين من التراخيص *التي تم إلغاؤها* . يجب القيام بذلك بشكل فردي لكل حساب مستخدم في مركز مسؤولي Microsoft 365.
>

لإزالة كافة التراخيص من مجموعة من المستخدمين المرخصين الحاليين، استخدم أيا من الأساليب التالية:
  
- **تصفية الحسابات استنادا إلى سمة حساب موجودة** للقيام بذلك، استخدم بناء الجملة التالي:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

يزيل هذا المثال كافة التراخيص من جميع حسابات المستخدمين في قسم المبيعات في الولايات المتحدة.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **استخدام قائمة بحسابات معينة لترخيص معين** للقيام بذلك، نفذ الخطوات التالية:
    
1. إنشاء ملف نصي يحتوي على حساب واحد على كل سطر وحفظه كما يلي:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. استخدم بناء الجملة التالي:
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
يزيل هذا المثال ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) من حسابات المستخدمين المعرفة في الملف النصي C:\My Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

لإزالة كافة التراخيص من جميع حسابات المستخدمين الموجودة، استخدم بناء الجملة التالي:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

هناك طريقة أخرى لتحرير ترخيص وهي حذف حساب المستخدم. لمزيد من المعلومات، راجع [حذف حسابات المستخدمين واستعادتها باستخدام PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
