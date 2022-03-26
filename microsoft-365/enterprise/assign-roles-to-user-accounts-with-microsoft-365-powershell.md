---
title: تعيين أدوار إلى Microsoft 365 المستخدمين باستخدام PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: في هذه المقالة، تعرف على مدى سرعة وسهولة استخدام PowerShell Microsoft 365 لتعيين أدوار المسؤولين إلى حسابات المستخدمين.
ms.openlocfilehash: 0b0fc0a5da1a6b84d4f13f95ace4846e367ae111
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572823"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>تعيين أدوار المسؤولين إلى Microsoft 365 المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك بسهولة تعيين أدوار إلى حسابات المستخدمين باستخدام PowerShell Microsoft 365.

>[!Note]
>تعرف على [كيفية تعيين أدوار المسؤولين](../admin/add-users/assign-admin-roles.md) إلى حسابات المستخدمين باستخدام مركز مسؤولي Microsoft 365.
>
>للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، استخدم مسؤول **Azure AD DC** أو **مسؤول تطبيق السحابة** أو حساب  المسؤول العام للاتصال Microsoft 365 [المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
لمزيد من المعلومات، راجع [حول أدوار المسؤولين](/microsoft-365/admin/add-users/about-admin-roles?).

بعد ذلك، حدد اسم تسجيل الدخول لحساب المستخدم الذي تريد إضافته إلى دور (على سبيل المثال: fredsm\@ contoso.com). يعرف هذا أيضا بالاسم الرئيسي للمستخدم (UPN).

بعد ذلك، حدد اسم الدور. راجع [أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference).

>[!Note]
>انتبه إلى الملاحظات في هذه المقالة. تختلف بعض أسماء الدور ل Azure Active Directory (Azure AD) PowerShell. على سبيل المثال *SharePoint دور مسؤول* مركز مسؤولي Microsoft 365 في SharePoint في Azure AD PowerShell.
>

بعد ذلك، قم بتعبئة اسمي تسجيل الدخول و الدور وتشغيل هذه الأوامر:
  
```powershell
$userName="<sign-in name of the account>"
$roleName="<admin role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

فيما يلي مثال على مجموعة أوامر مكتملة تقوم بتعيين SharePoint مسؤول الخدمة إلى *حساب belindan\@ contoso.com* التالي:
  
```powershell
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

لعرض قائمة بأسماء المستخدمين لدور مسؤول معين، استخدم هذه الأوامر.

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، استخدم حساب مسؤول عام [للاتصال Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>لتغيير دور واحد

الطرق الأكثر شيوعا لتحديد حساب المستخدم هي باستخدام اسم العرض أو اسم البريد الإلكتروني الخاص به، والذي يعرف أيضا باسم تسجيل الدخول أو اسم المستخدم الأساسي (UPN).

#### <a name="display-names-of-user-accounts"></a>عرض أسماء حسابات المستخدمين

إذا كنت معتادا على استخدام أسماء عرض حسابات المستخدمين، فحدد المعلومات التالية:
  
- حساب المستخدم الذي تريد تكوينه
    
    لتحديد حساب المستخدم، يجب تحديد اسم العرض الخاص به. للحصول على قائمة كاملة من الحسابات، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    يسرد هذا الأمر اسم العرض الخاص وحسابات المستخدمين، التي تم فرزها حسب اسم العرض، شاشة واحدة في كل مرة. يمكنك تصفية القائمة إلى مجموعة أصغر باستخدام **الأمر Where** cmdlet. راجع المثال التالي.

   >[!Note]
   >لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. تشغيل cmdlets هذه من Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    يسرد هذا الأمر فقط حسابات المستخدمين التي يبدأ "اسم العرض" بها ب "John".
    
- الدور الذي تريد تعيينه
    
    لعرض قائمة أدوار المسؤولين المتوفرة التي يمكنك تعيينها إلى حسابات المستخدمين، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

بعد تحديد اسم العرض للحساب واسم الدور، استخدم هذه الأوامر لتعيين الدور إلى الحساب:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

لصق الأوامر في المفكرة. بالنسبة إلى *$dispName* *$roleName،* استبدل نص الوصف بقيمها. قم بإزالة \< and > الأحرف مع الاحتفاظ علامات الاقتباس. ألصق الخطوط المعدلة في Microsoft Azure Active Directory النمطية Windows PowerShell لتشغيلها. بدلا من ذلك، يمكنك استخدام Windows PowerShell البرامج النصية المتكاملة (ISE).
  
فيما يلي مثال على مجموعة أوامر مكتملة:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>أسماء تسجيل الدخول إلى حسابات المستخدمين

إذا كنت معتادا على استخدام أسماء تسجيل الدخول أو UPN في حسابات المستخدمين، فحدد المعلومات التالية:
  
- UPN لحساب المستخدم
    
    إذا لم تكن تعرف UPN، فاستخدم هذا الأمر:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    يسرد هذا الأمر UPN حسابات المستخدمين، التي تم فرزها حسب UPN، كل شاشة على الأخرى. يمكنك استخدام **الأمر Where** cmdlet لتصفية القائمة. فيما يلي مثال على ذلك:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    يسرد هذا الأمر فقط حسابات المستخدمين التي يبدأ "اسم العرض" بها ب "John".
    
- الدور الذي تريد تعيينه
    
    لعرض قائمة الأدوار المتوفرة التي يمكنك تعيينها إلى حسابات المستخدمين، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

بعد الحصول على UPN للحساب واسم الدور، استخدم هذه الأوامر لتعيين الدور إلى الحساب:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

انسخ الأوامر واللصق في المفكرة. بالنسبة **$upnName** **ومتغيرات $roleName** . استبدل نص الوصف بقيمه. قم بإزالة \< and > الأحرف مع الاحتفاظ علامات الاقتباس. لصق الخطوط المعدلة في Microsoft Azure Active Directory النمطية Windows PowerShell النافذة لتشغيلها. بدلا من ذلك، يمكنك استخدام Windows PowerShell ISE.
  
فيما يلي مثال على مجموعة أوامر مكتملة:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>تغييرات الدور المتعددة

للحصول على تغييرات الدور المتعددة، حدد المعلومات التالية:
  
- حسابات المستخدمين التي تريد تكوينها. يمكنك استخدام الأساليب في المقطع السابق لجمع مجموعة أسماء العرض أو أسماء UPN.
    
- الأدوار التي تريد تعيينها لكل حساب مستخدم. لعرض قائمة الأدوار المتوفرة التي يمكنك تعيينها إلى حسابات المستخدمين، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

بعد ذلك، قم بإنشاء ملف نصي لقيمة مفصولة ب فاصلة (CSV) يحتوي على حقلي اسم العرض أو UPN واسم الدور. يمكنك القيام بذلك بسهولة في Microsoft Excel.

فيما يلي مثال لأسماء العرض:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

بعد ذلك، قم بتعبئة موقع ملف CSV وتشغيل الأوامر الناتجة في موجه الأوامر PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

فيما يلي مثال على UPNs:
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

بعد ذلك، قم بتعبئة موقع ملف CSV وتشغيل الأوامر الناتجة في موجه الأوامر PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>راجع أيضًا

- [إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
