---
title: حذف حسابات المستخدمين Microsoft 365 باستخدام PowerShell
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
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: تعرف على كيفية استخدام وحدات نمطية مختلفة في PowerShell لحذف حسابات المستخدمين Microsoft 365.
ms.openlocfilehash: b3d273e6f2274b43018848e5439f431281a54df8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093427"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>حذف حسابات المستخدمين Microsoft 365 باستخدام PowerShell

يمكنك استخدام PowerShell Microsoft 365 لحذف حسابات المستخدمين واستعادتها.

>[!Note]
>تعرف على كيفية [استعادة حساب مستخدم](../admin/add-users/restore-user.md) باستخدام مركز مسؤولي Microsoft 365.
>
>للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

بعد الاتصال، استخدم بناء الجملة التالي لإزالة حساب مستخدم فردي:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

يزيل هذا المثال *fabricec\@* حساب المستخدم litwareinc.com.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> تقبل المعلمة *-ObjectID* في **cmdlet Remove-AzureADUser** إما اسم تسجيل الدخول للحساب، والمعروف أيضا باسم المستخدم الأساسي أو معرف كائن الحساب.
  
لعرض اسم الحساب استنادا إلى اسم المستخدم، استخدم الأوامر التالية:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

يعرض هذا المثال اسم الحساب للمستخدم *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

لإزالة حساب استنادا إلى اسم العرض الخاص بالمستخدم، استخدم الأوامر التالية:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

عند حذف حساب مستخدم من خلال الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell، لا يتم حذف الحساب بشكل دائم. يمكنك استعادة حساب المستخدم المحذوفة في غضون 30 يوما.

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

لحذف حساب مستخدم، استخدم بناء الجملة التالي:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell و cmdlets مع *Msol* باسمها. تشغيل أوامر cmdlets هذه من Windows PowerShell.
>

يحذف هذا المثال *حساب المستخدم BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

لاستعادة حساب مستخدم محذوفة خلال فترة السماح التي تبلغ 30 يوما، استخدم بناء الجملة التالي:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

This example restores the deleted account *BelindaN\@litwareinc.com*.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

>[!Note]
> لمشاهدة قائمة المستخدمين المحذوفين التي يمكن استعادتها، قم بتشغيل الأمر التالي:
>    
> ```powershell
> Get-MsolUser -All -ReturnDeletedUsers
> ```
>
> إذا تم استخدام اسم المستخدم الأساسي الأصلي لحساب المستخدم من قبل حساب آخر، فاستخدم المعلمة _NewUserPrincipalName_ بدلا من _UserPrincipalName_ لتحديد اسم أساسي مختلف للمستخدم عند استعادة حساب المستخدم.


## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)