---
title: حظر حسابات المستخدمين Microsoft 365 باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/16/2020
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
- Ent_Office_Other
- PowerShell
- seo-marvel-apr2020
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: كيفية استخدام PowerShell لحظر الوصول إلى حسابات Microsoft 365 وإلغاء حظره.
ms.openlocfilehash: ffeac03f9f48e6531443a8f90a3d5fd3506172fe
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091600"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>حظر حسابات المستخدمين Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

عند حظر الوصول إلى حساب Microsoft 365، فإنك تمنع أي شخص من استخدام الحساب لتسجيل الدخول والوصول إلى الخدمات والبيانات في مؤسستك Microsoft 365. يمكنك استخدام PowerShell لحظر الوصول إلى حسابات المستخدمين الفردية أو المتعددة.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>حظر الوصول إلى حسابات المستخدمين الفردية

استخدم بناء الجملة التالي لحظر حساب مستخدم فردي:

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> تقبل المعلمة *-ObjectID* في **Cmdlet Set-AzureAD** إما اسم تسجيل الدخول إلى الحساب، المعروف أيضا باسم المستخدم الأساسي، أو معرف كائن الحساب.

يمنع هذا المثال الوصول إلى *حساب المستخدم fabricec@litwareinc.com*.

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

لإلغاء حظر حساب المستخدم هذا، قم بتشغيل الأمر التالي:

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

لعرض UPN لحساب المستخدم استنادا إلى اسم العرض الخاص بالمستخدم، استخدم الأوامر التالية:

```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

يعرض هذا المثال UPN لحساب المستخدم ل  *Caleb Sills* للمستخدم.

```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

لحظر حساب استنادا إلى اسم العرض الخاص بالمستخدم، استخدم الأوامر التالية:

```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

للتحقق من الحالة المحظورة لحساب مستخدم، استخدم الأمر التالي:

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>حظر حسابات مستخدمين متعددة

لحظر الوصول لحسابات مستخدمين متعددة، قم بإنشاء ملف نصي يحتوي على اسم تسجيل دخول حساب واحد على كل سطر مثل هذا:

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

في الأوامر التالية، الملف النصي المثال هو *C:\My Documents\Accounts.txt*. استبدل اسم الملف هذا بالمسار واسم الملف الخاص بالملف النصي.

لحظر الوصول إلى الحسابات المدرجة في الملف النصي، قم بتشغيل الأمر التالي:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

لإلغاء حظر الحسابات المدرجة في الملف النصي، قم بتشغيل الأمر التالي:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>حظر حسابات المستخدمين الفردية

استخدم بناء الجملة التالي لحظر الوصول لحساب مستخدم فردي:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets التي تحتوي على *Msol* باسمها. يجب عليك تشغيل أوامر cmdlets هذه من Windows PowerShell.

يمنع هذا المثال الوصول إلى *fabricec\@* لحساب المستخدم litwareinc.com.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

لإلغاء حظر حساب المستخدم، قم بتشغيل الأمر التالي:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

للتحقق من الحالة المحظورة لحساب مستخدم، قم بتشغيل الأمر التالي:

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>حظر الوصول لحسابات مستخدمين متعددة

أولا، إنشاء ملف نصي يحتوي على حساب واحد على كل سطر مثل هذا:

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

في الأوامر التالية، الملف النصي المثال هو *C:\My Documents\Accounts.txt*. استبدل اسم الملف هذا بالمسار واسم الملف الخاص بالملف النصي.

لحظر الوصول إلى الحسابات المدرجة في الملف النصي، قم بتشغيل الأمر التالي:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
لإلغاء حظر الحسابات المدرجة في الملف النصي، قم بتشغيل الأمر التالي:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
