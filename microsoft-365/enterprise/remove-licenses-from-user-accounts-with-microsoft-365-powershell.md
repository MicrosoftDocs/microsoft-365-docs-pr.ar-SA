---
title: إزالة Microsoft 365 من حسابات المستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: يشرح كيفية استخدام PowerShell لإزالة Microsoft 365 التي تم تعيينها مسبقا للمستخدمين.
ms.openlocfilehash: 4aa40b4405dda07eea34151bd2fddcde0030e8b8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569572"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a>إزالة Microsoft 365 من حسابات المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

>[!Note]
>[تعرف على كيفية إزالة التراخيص من حسابات المستخدمين](../admin/manage/remove-licenses-from-users.md) باستخدام مركز مسؤولي Microsoft 365. للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

بعد ذلك، سرد خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، احصل على اسم تسجيل الدخول للحساب الذي تريد إزالة ترخيص له، المعروف أيضا بالاسم الرئيسي للمستخدم (UPN).

وأخيرا، حدد أسماء خطط تسجيل الدخول والترخيص للمستخدم، وأزل <" و">" ثم قم بتشغيل هذه الأوامر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

لإزالة كل التراخيص لحساب مستخدم معين، حدد اسم تسجيل الدخول للمستخدم، وأزل حرفي "<" و">" ثم قم بتشغيل هذه الأوامر.

```powershell
$userUPN="<user sign-in name (UPN)>"
$userList = Get-AzureADUser -ObjectID $userUPN
$Skus = $userList | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
    if($Skus -is [array])
    {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        for ($i=0; $i -lt $Skus.Count; $i++) {
            $Licenses.RemoveLicenses +=  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus[$i].SkuId -EQ).SkuID   
        }
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    } else {
        $licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
        $Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $Skus.SkuId -EQ).SkuID
        Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
    }
}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
لعرض معلومات خطة الترخيص (**AccountSkuID**) في مؤسستك، راجع المواضيع التالية:
    
  - [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md)
    
  - [عرض تفاصيل ترخيص الحساب والخدمة باستخدام PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md)
    
إذا كنت تستخدم **الأمر Cmdlet Get-MsolUser** بدون استخدام _المعلمة -All_ ، يتم إرجاع أول 500 حساب فقط.
    
### <a name="removing-licenses-from-user-accounts"></a>إزالة التراخيص من حسابات المستخدمين

لإزالة التراخيص من حساب مستخدم موجود، استخدم بناء الجملة التالي:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

يزيل هذا المثال **ترخيص litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) من حساب المستخدم BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>لا يمكنك استخدام `Set-MsolUserLicense` الأمر cmdlet لإلغاء تعيين المستخدمين من *التراخيص الملغاة* . يجب القيام بذلك بشكل فردي لكل حساب مستخدم في مركز مسؤولي Microsoft 365.
>

لإزالة كل التراخيص من مجموعة من المستخدمين المرخصين، استخدم أحد الأساليب التالية:
  
- **تصفية الحسابات استنادا إلى سمة حساب موجودة** للقيام بذلك، استخدم بناء الجملة التالي:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

يزيل هذا المثال كل التراخيص من كل حسابات المستخدمين في قسم المبيعات في الولايات المتحدة.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **استخدام قائمة حسابات معينة لترخيص معين** للقيام بذلك، تنفيذ الخطوات التالية:
    
1. إنشاء ملف نصي يحتوي على حساب واحد على كل سطر على هذا السطر وحفظه:
    
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
يزيل هذا المثال ترخيص **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) من حسابات المستخدمين المعرفة في الملف النصي C:\my Documents\Accounts.txt.
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

لإزالة كل التراخيص من كل حسابات المستخدمين الموجودة، استخدم بناء الجملة التالي:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

هناك طريقة أخرى لتحرير ترخيص وهي حذف حساب المستخدم. لمزيد من المعلومات، راجع [حذف حسابات المستخدمين واستعادتها باستخدام PowerShell](delete-and-restore-user-accounts-with-microsoft-365-powershell.md).
  
## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)