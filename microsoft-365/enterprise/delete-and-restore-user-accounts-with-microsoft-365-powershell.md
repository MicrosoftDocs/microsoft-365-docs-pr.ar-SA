---
title: حذف Microsoft 365 المستخدمين باستخدام PowerShell
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
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: تعرف على كيفية استخدام وحدات نموذجية مختلفة في PowerShell لحذف Microsoft 365 المستخدمين.
ms.openlocfilehash: dc1e5c53f2d356f0585da5a0a5285b9af28dc8f0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568972"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>حذف Microsoft 365 المستخدمين باستخدام PowerShell

يمكنك استخدام PowerShell Microsoft 365 لحذف حسابات المستخدمين واستعادتها.

>[!Note]
>تعرف على [كيفية استعادة حساب مستخدم](../admin/add-users/restore-user.md) باستخدام مركز مسؤولي Microsoft 365.
>
>للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>   
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

بعد الاتصال، استخدم بناء الجملة التالي لإزالة حساب مستخدم فردي:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

يزيل هذا المثال نسيج حساب *المستخدم litwareinc.com\@*.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> تقبل المعلمة *-ObjectID* في الأمر **cmdlet Remove-AzureADUser** إما اسم تسجيل الدخول للحساب، المعروف أيضا بالاسم الأساسي للمستخدم أو بمعرف كائن الحساب.
  
لعرض اسم الحساب استنادا إلى اسم المستخدم، استخدم الأوامر التالية:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

يعرض هذا المثال اسم حساب المستخدم *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

لإزالة حساب استنادا إلى اسم عرض المستخدم، استخدم الأوامر التالية:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

عند حذف حساب مستخدم من خلال Microsoft Azure Active Directory النمطية Windows PowerShell، لن يتم حذف الحساب بشكل دائم. يمكنك استعادة حساب المستخدم المحذوف في غضون 30 يوما.

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

لحذف حساب مستخدم، استخدم بناء الجملة التالي:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. تشغيل cmdlets هذه من Windows PowerShell.
>

يحذف هذا المثال *حساب المستخدم BelindaN@litwareinc.com*.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

لاستعادة حساب مستخدم محذوف خلال فترة سماح 30 يوما، استخدم بناء الجملة التالي:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

يستعيد هذا المثال حساب *BelindaN\@ المحذوف* litwareinc.com.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

>[!Note]
> لرؤية قائمة المستخدمين المحذوفة التي يمكن استعادتها، يمكنك تشغيل الأمر التالي:
>    
> ```powershell
> Get-MsolUser -All -ReturnDeletedUsers
> ```
>
> إذا تم استخدام اسم المستخدم الأساسي الأصلي لحساب المستخدم بواسطة حساب آخر، فاستخدم المعلمة _NewUserPrincipalName_ بدلا من _UserPrincipalName_ لتحديد اسم مستخدم أساسي مختلف عند استعادة حساب المستخدم.


## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)