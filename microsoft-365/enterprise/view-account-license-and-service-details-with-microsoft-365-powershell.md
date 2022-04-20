---
title: عرض ترخيص حساب Microsoft 365 وتفاصيل الخدمة باستخدام PowerShell
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
description: يشرح كيفية استخدام PowerShell لتحديد خدمات Microsoft 365 التي تم تعيينها للمستخدمين.
ms.openlocfilehash: 7e5724acbff571825f1496db5d59e04e11ba3a67
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64915984"
---
# <a name="view-microsoft-365-account-license-and-service-details-with-powershell"></a>عرض ترخيص حساب Microsoft 365 وتفاصيل الخدمة باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

في Microsoft 365، تمنح التراخيص من خطط الترخيص (تسمى أيضا وحدات SKU أو خطط Microsoft 365) للمستخدمين إمكانية الوصول إلى خدمات Microsoft 365 المحددة لتلك الخطط. ومع ذلك، قد لا يكون لدى المستخدم حق الوصول إلى جميع الخدمات المتوفرة في ترخيص معين له حاليا. يمكنك استخدام PowerShell Microsoft 365 لعرض حالة الخدمات على حسابات المستخدمين.

لمزيد من المعلومات حول خطط الترخيص والترخيص والخدمات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

## <a name="use-the-microsoft-graph-powershell-sdk"></a>استخدام Microsoft Graph PowerShell SDK

أولا، [اتصل بمستأجر Microsoft 365](/graph/powershell/get-started#authentication).

تتطلب قراءة خصائص المستخدم بما في ذلك تفاصيل الترخيص نطاق أذونات User.Read.All أو أحد الأذونات الأخرى المدرجة في [الصفحة المرجعية "Get a user" Graph API](/graph/api/user-get).

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

بعد ذلك، قم بإدراج خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-MgSubscribedSku
```

استخدم هذه الأوامر لإدراج الخدمات المتوفرة في كل خطة ترخيص.

```powershell

$allSKUs = Get-MgSubscribedSku -Property SkuPartNumber, ServicePlans 
$allSKUs | ForEach-Object {
    Write-Host "Service Plan:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

استخدم هذه الأوامر لإدراج التراخيص المعينة لحساب مستخدم.

```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

على سبيل المثال:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

### <a name="to-view-services-for-a-user-account"></a>لعرض الخدمات لحساب مستخدم

لعرض جميع خدمات Microsoft 365 التي يمكن للمستخدم الوصول إليها، استخدم بناء الجملة التالي:
  
```powershell
(Get-MgUserLicenseDetail -UserId <user account UPN> -Property ServicePlans)[<LicenseIndexNumber>].ServicePlans
```

يوضح هذا المثال الخدمات التي يمكن للمستخدم BelindaN@litwareinc.com الوصول إليها. يعرض ذلك الخدمات المقترنة بكافة التراخيص التي تم تعيينها لحسابها.
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans).ServicePlans
```

يوضح هذا المثال الخدمات التي يمكن للمستخدم BelindaN@litwareinc.com الوصول إليها من الترخيص الأول المعين لحسابه (رقم الفهرس هو 0).
  
```powershell
(Get-MgUserLicenseDetail -UserId belindan@litwareinc.com -Property ServicePlans)[0].ServicePlans
```

لعرض كافة الخدمات لمستخدم تم تعيين *تراخيص متعددة* له، استخدم بناء الجملة التالي:

```powershell
$userUPN="<user account UPN>"
$allLicenses = Get-MgUserLicenseDetail -UserId $userUPN -Property SkuPartNumber, ServicePlans
$allLicenses | ForEach-Object {
    Write-Host "License:" $_.SkuPartNumber
    $_.ServicePlans | ForEach-Object {$_}
}

```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
بعد ذلك، قم بإدراج خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

استخدم هذه الأوامر لإدراج الخدمات المتوفرة في كل خطة ترخيص.

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

استخدم هذه الأوامر لإدراج التراخيص المعينة لحساب مستخدم.

```powershell
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

بعد ذلك، قم بتشغيل هذا الأمر لإدراج خطط الترخيص المتوفرة في مؤسستك. 

```powershell
Get-MsolAccountSku
```
>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

بعد ذلك، قم بتشغيل هذا الأمر لإدراج الخدمات المتوفرة في كل خطة ترخيص، والترتيب الذي يتم إدراجها به (رقم الفهرس).

```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```
  
استخدم هذا الأمر لإدراج التراخيص التي تم تعيينها لمستخدم، والترتيب الذي تم إدراجها به (رقم الفهرس).

```powershell
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
```

### <a name="to-view-services-for-a-user-account"></a>لعرض الخدمات لحساب مستخدم

لعرض جميع خدمات Microsoft 365 التي يمكن للمستخدم الوصول إليها، استخدم بناء الجملة التالي:
  
```powershell
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

يوضح هذا المثال الخدمات التي يمكن للمستخدم BelindaN@litwareinc.com الوصول إليها. يعرض ذلك الخدمات المقترنة بكافة التراخيص التي تم تعيينها لحسابها.
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

يوضح هذا المثال الخدمات التي يمكن للمستخدم BelindaN@litwareinc.com الوصول إليها من الترخيص الأول المعين لحسابه (رقم الفهرس هو 0).
  
```powershell
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

لعرض كافة الخدمات لمستخدم تم تعيين *تراخيص متعددة* له، استخدم بناء الجملة التالي:

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

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
