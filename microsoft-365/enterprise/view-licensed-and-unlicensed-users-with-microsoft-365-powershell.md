---
title: عرض مستخدمي Microsoft 365 المرخصين وغير المرخصين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/21/2020
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: تشرح هذه المقالة كيفية استخدام PowerShell لعرض حسابات المستخدمين Microsoft 365 المرخصة وغير المرخصة.
ms.openlocfilehash: 1be54b20d3b50985fea8eb665a1b6098a26aa703
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823620"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>عرض مستخدمي Microsoft 365 المرخصين وغير المرخصين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

قد تحتوي حسابات المستخدمين في مؤسستك Microsoft 365 على بعض التراخيص المتوفرة المعينة إليها من خطط الترخيص المتوفرة في مؤسستك أو كلها أو لا تحتوي على أي منها. يمكنك استخدام PowerShell Microsoft 365 للعثور بسرعة على المستخدمين المرخصين وغير المرخصين في مؤسستك.

## <a name="use-the-microsoft-graph-powershell-sdk"></a>استخدام Microsoft Graph PowerShell SDK

أولا، [اتصل بمستأجر Microsoft 365](/graph/powershell/get-started#authentication).

تتطلب قراءة خصائص المستخدم بما في ذلك تفاصيل الترخيص نطاق أذونات User.Read.All أو أحد الأذونات الأخرى المدرجة في [الصفحة المرجعية "Get a user" Graph API](/graph/api/user-get).

نطاق أذونات Organization.Read.All مطلوب لقراءة التراخيص المتوفرة في المستأجر.

```powershell
Connect-Graph -Scopes User.Read.All, Organization.Read.All
```

لعرض تفاصيل الترخيص لحساب مستخدم معين، قم بتشغيل الأمر التالي:
  
```powershell
Get-MgUserLicenseDetail -UserId "<user sign-in name (UPN)>"
```

على سبيل المثال:

```powershell
Get-MgUserLicenseDetail -UserId "belindan@litwareinc.com"
```

لعرض قائمة بجميع حسابات المستخدمين في مؤسستك التي لم يتم تعيين أي خطة ترخيص لها (مستخدمين غير مرخصين)، قم بتشغيل الأمر التالي:
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users."
```

لعرض قائمة بجميع حسابات المستخدمين الأعضاء (باستثناء الضيوف) في مؤسستك التي لم يتم تعيين أي من خطط الترخيص الخاصة بك (المستخدمين غير المرخصين)، قم بتشغيل الأمر التالي:
  
```powershell
Get-MgUser -Filter "assignedLicenses/`$count eq 0 and userType eq 'Member'" -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All

Write-Host "Found $unlicensedUserCount unlicensed users (excluding guests)."
```

لعرض قائمة بجميع حسابات المستخدمين في مؤسستك التي تم تعيينها لأي من خطط الترخيص (المستخدمين المرخصين)، قم بتشغيل الأمر التالي:
  
```powershell
Get-MgUser -Filter 'assignedLicenses/$count ne 0' -ConsistencyLevel eventual -CountVariable licensedUserCount -All -Select UserPrincipalName,DisplayName,AssignedLicenses | Format-Table -Property UserPrincipalName,DisplayName,AssignedLicenses

Write-Host "Found $licensedUserCount licensed users."
```

لعرض قائمة بكل حسابات المستخدمين في مؤسستك التي تم تعيين ترخيص E5 لها، قم بتشغيل الأمر التالي:

```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

Get-MgUser -Filter "assignedLicenses/any(x:x/skuId eq $($e5sku.SkuId) )" -ConsistencyLevel eventual -CountVariable e5licensedUserCount -All

Write-Host "Found $e5licensedUserCount E5 licensed users."
```

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
لعرض قائمة بجميع حسابات المستخدمين في مؤسستك التي لم يتم تعيين أي خطة ترخيص لها (مستخدمين غير مرخصين)، قم بتشغيل الأمر التالي:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

لعرض قائمة بجميع حسابات المستخدمين في مؤسستك التي تم تعيينها لأي من خطط الترخيص (المستخدمين المرخصين)، قم بتشغيل الأمر التالي:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>لإدراج جميع المستخدمين في اشتراكك، استخدم `Get-AzureAdUser -All $true` الأمر.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

لعرض قائمة بجميع حسابات المستخدمين وحالة الترخيص الخاصة بهم في مؤسستك، قم بتشغيل الأمر التالي في PowerShell:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

لعرض قائمة بكل حسابات المستخدمين غير المرخصين في مؤسستك، قم بتشغيل الأمر التالي:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

لعرض قائمة بكل حسابات المستخدمين المرخص لهم في مؤسستك، قم بتشغيل الأمر التالي:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
