---
title: عرض المستخدمين المرخصين وغير المرخصين Microsoft 365 مع PowerShell
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
description: تشرح هذه المقالة كيفية استخدام PowerShell لعرض حسابات المستخدمين المرخصة وغير المرخصة Microsoft 365 المستخدمين.
ms.openlocfilehash: 015cb63fd692131d77799fe30fc94c6214bb01d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575297"
---
# <a name="view-licensed-and-unlicensed-microsoft-365-users-with-powershell"></a>عرض المستخدمين المرخصين وغير المرخصين Microsoft 365 مع PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

قد يكون لدى حسابات المستخدمين في مؤسستك Microsoft 365 بعض التراخيص المتوفرة المعينة لها أو كلها أو لا يتم تعيينها لها من خطط الترخيص المتوفرة في مؤسستك. يمكنك استخدام PowerShell Microsoft 365 للعثور بسرعة على المستخدمين المرخصين وغير المرخصين في مؤسستك.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
لعرض قائمة بكل حسابات المستخدمين في مؤسستك التي لم يتم تعيين أي خطط ترخيص لها (المستخدمون غير المرخصين)، قم بتشغيل الأمر التالي:
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

لعرض قائمة بكل حسابات المستخدمين في مؤسستك التي تم تعيينها لأي من خطط الترخيص (المستخدمون المرخصون)، قم بتشغيل الأمر التالي:
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
>لتضمين جميع المستخدمين في اشتراكك، استخدم `Get-AzureAdUser -All $true` الأمر.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

لعرض قائمة بكل حسابات المستخدمين ووضع الترخيص الخاص بهم في مؤسستك، يمكنك تشغيل الأمر التالي في PowerShell:
  
```powershell
Get-MsolUser -All
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

لعرض قائمة بكل حسابات المستخدمين غير مرخصين في مؤسستك، يمكنك تشغيل الأمر التالي:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

لعرض قائمة بكل حسابات المستخدمين المرخص لهم في مؤسستك، يمكنك تشغيل الأمر التالي:
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
