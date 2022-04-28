---
title: تعيين أدوار لحسابات المستخدمين Microsoft 365 باستخدام PowerShell
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell بسرعة وسهولة Microsoft 365 لتعيين أدوار المسؤول لحسابات المستخدمين.
ms.openlocfilehash: 8ac98920dd3d2d0487905b001434d73274463f9a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097437"
---
# <a name="assign-admin-roles-to-microsoft-365-user-accounts-with-powershell"></a>تعيين أدوار المسؤول لحسابات المستخدمين Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك بسهولة تعيين أدوار لحسابات المستخدمين باستخدام PowerShell Microsoft 365.

>[!Note]
>تعرف على كيفية [تعيين أدوار المسؤول](../admin/add-users/assign-admin-roles.md) لحسابات المستخدمين باستخدام مركز مسؤولي Microsoft 365.
>
>للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، استخدم **مسؤول AZURE AD DC** أو **مسؤول تطبيق السحابة** أو حساب **المسؤول العمومي** [للاتصال بمستأجر Microsoft 365.](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
 
لمزيد من المعلومات، راجع [حول أدوار المسؤولين](/microsoft-365/admin/add-users/about-admin-roles?).

بعد ذلك، حدد اسم تسجيل الدخول لحساب المستخدم الذي تريد إضافته إلى دور (على سبيل المثال: fredsm\@ contoso.com). يعرف هذا أيضا باسم اسم المستخدم الأساسي (UPN).

بعد ذلك، حدد اسم الدور. راجع [الأدوار المضمنة في Azure AD](/azure/active-directory/roles/permissions-reference).

>[!Note]
>انتبه للملاحظات الواردة في هذه المقالة. تختلف بعض أسماء الأدوار ل Azure Active Directory (Azure AD) PowerShell. على سبيل المثال، دور *مسؤول SharePoint* في مركز مسؤولي Microsoft 365 هو *مسؤول خدمة SharePoint* في Azure AD PowerShell.
>

بعد ذلك، قم بتعبئة أسماء الأدوار وتسجيل الدخول وتشغيل هذه الأوامر:
  
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

فيما يلي مثال على مجموعة أوامر مكتملة تقوم بتعيين دور مسؤول الخدمة SharePoint إلى حساب *behakn\@ contoso.com*:
  
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، استخدم حساب مسؤول عام [للاتصال بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="for-a-single-role-change"></a>لتغيير دور واحد

الطرق الأكثر شيوعا لتحديد حساب المستخدم هي باستخدام اسم العرض أو اسم البريد الإلكتروني الخاص به، والذي يعرف أيضا باسم تسجيل الدخول أو اسم المستخدم الأساسي (UPN).

#### <a name="display-names-of-user-accounts"></a>عرض أسماء حسابات المستخدمين

إذا كنت معتادا على العمل مع أسماء عرض حسابات المستخدمين، فحدد المعلومات التالية:
  
- حساب المستخدم الذي تريد تكوينه
    
    لتحديد حساب المستخدم، يجب تحديد اسم العرض الخاص به. للحصول على قائمة كاملة بالحسابات، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    يسرد هذا الأمر "الاسم المعروض" لحسابات المستخدمين، التي تم فرزها حسب "اسم العرض"، شاشة واحدة في كل مرة. يمكنك تصفية القائمة إلى مجموعة أصغر باستخدام **Cmdlet Where** . راجع المثال التالي.

   >[!Note]
   >لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell و cmdlets مع *Msol* باسمها. تشغيل أوامر cmdlets هذه من Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    يسرد هذا الأمر فقط حسابات المستخدمين التي يبدأ اسم العرض بها ب "وليد".
    
- الدور الذي تريد تعيينه
    
    لعرض قائمة أدوار المسؤولين المتوفرة التي يمكنك تعيينها لحسابات المستخدمين، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

بعد تحديد اسم العرض للحساب واسم الدور، استخدم هذه الأوامر لتعيين الدور إلى الحساب:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The admin role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

الصق الأوامر في المفكرة. بالنسبة *للمتغيرات* *$dispName* $roleName، استبدل نص الوصف بقيمها. قم بإزالة الأحرف \< and > مع الاحتفاظ بعلامات الاقتباس. الصق الخطوط المعدلة في الوحدة النمطية Microsoft Azure Active Directory لنافذة Windows PowerShell لتشغيلها. بدلا من ذلك، يمكنك استخدام Windows PowerShell بيئة البرنامج النصي المتكامل (ISE).
  
فيما يلي مثال على مجموعة أوامر مكتملة:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>أسماء تسجيل الدخول لحسابات المستخدمين

إذا كنت معتادا على استخدام أسماء تسجيل الدخول أو UPN لحسابات المستخدمين، فحدد المعلومات التالية:
  
- UPN لحساب المستخدم
    
    إذا كنت لا تعرف UPN، فاستخدم هذا الأمر:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    يسرد هذا الأمر UPN لحسابات المستخدمين، التي تم فرزها حسب UPN، شاشة واحدة في كل مرة. يمكنك استخدام **Cmdlet** Where لتصفية القائمة. فيما يلي مثال على ذلك:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    يسرد هذا الأمر فقط حسابات المستخدمين التي يبدأ اسم العرض بها ب "وليد".
    
- الدور الذي تريد تعيينه
    
    لعرض قائمة الأدوار المتوفرة التي يمكنك تعيينها لحسابات المستخدمين، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

بعد أن يكون لديك UPN للحساب واسم الدور، استخدم هذه الأوامر لتعيين الدور إلى الحساب:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

انسخ الأوامر والصقها في المفكرة. للمتغيرات **$upnName** $roleName. استبدل نص الوصف بقيمه. قم بإزالة الأحرف \< and > مع الاحتفاظ بعلامات الاقتباس. الصق الأسطر المعدلة في وحدة نمطية Microsoft Azure Active Directory لنافذة Windows PowerShell لتشغيلها. بدلا من ذلك، يمكنك استخدام Windows PowerShell ISE.
  
فيما يلي مثال على مجموعة أوامر مكتملة:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>تغييرات دور متعددة

لتغييرات الأدوار المتعددة، حدد المعلومات التالية:
  
- حسابات المستخدمين التي تريد تكوينها. يمكنك استخدام الأساليب الموجودة في المقطع السابق لجمع مجموعة أسماء العرض أو UPNs.
    
- الأدوار التي تريد تعيينها لكل حساب مستخدم. لعرض قائمة الأدوار المتوفرة التي يمكنك تعيينها لحسابات المستخدمين، استخدم هذا الأمر:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

بعد ذلك، قم بإنشاء ملف نصي لقيمة مفصولة بفواصل (CSV) يحتوي على اسم العرض أو حقول اسم UPN واسم الدور. يمكنك القيام بذلك بسهولة في Microsoft Excel.

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

- [إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
- [إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
