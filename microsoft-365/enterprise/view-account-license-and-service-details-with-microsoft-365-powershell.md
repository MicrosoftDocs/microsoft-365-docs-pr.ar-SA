---
title: عرض Microsoft 365 تفاصيل الخدمة وترخيص الحساب باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
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
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: يشرح كيفية استخدام PowerShell لتحديد Microsoft 365 التي تم تعيينها للمستخدمين.
ms.openlocfilehash: c02d3ffe2fff330f46adfc6b6dd49e553f69ad86
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570029"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>عرض Microsoft 365 تفاصيل الخدمة وترخيص الحساب باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

في Microsoft 365، تمنح التراخيص من خطط الترخيص (تسمى أيضا خطط Microsoft 365 أو SKUs) المستخدمين حق الوصول إلى خدمات Microsoft 365 المحددة لتلك الخطط. ومع ذلك، قد لا يكون لدى المستخدم حق الوصول إلى كل الخدمات المتوفرة في ترخيص تم تعيينه له حاليا. يمكنك استخدام PowerShell Microsoft 365 لعرض حالة الخدمات على حسابات المستخدمين. 

لمزيد من المعلومات حول خطط الترخيص والترخيص والخدمات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
بعد ذلك، سرد خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

استخدم هذه الأوامر لتضمين الخدمات المتوفرة في كل خطة ترخيص.

```powershell
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
```

استخدم هذه الأوامر لقائمة التراخيص المعينة إلى حساب مستخدم.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

بعد ذلك، تشغيل هذا الأمر لقائمة خطط الترخيص المتوفرة في مؤسستك. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

بعد ذلك، يمكنك تشغيل هذا الأمر لقائمة الخدمات المتوفرة في كل خطة ترخيص، بالترتيب الذي يتم به إدراجها (رقم الفهرس).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
استخدم هذا الأمر لقائمة التراخيص التي تم تعيينها إلى مستخدم، بالترتيب الذي يتم به إدراجها (رقم الفهرس).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>لعرض الخدمات لحساب مستخدم

لعرض كل Microsoft 365 التي يمكن للمستخدم الوصول إليها، استخدم بناء الجملة التالي:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

يوضح هذا المثال الخدمات التي يمكن للمستخدم BelindaN@litwareinc.com الوصول إليها. يظهر هذا الخدمات المقترنة بكل التراخيص المعينة إلى حسابها.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

يوضح هذا المثال الخدمات التي BelindaN@litwareinc.com المستخدم حق الوصول إليها من الترخيص الأول الذي تم تعيينه إلى حسابها (رقم الفهرس هو 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

لعرض كل الخدمات لمستخدم تم تعيين تراخيص متعددة له، استخدم بناء الجملة التالي:

```powershell
$userUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```
 
## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
