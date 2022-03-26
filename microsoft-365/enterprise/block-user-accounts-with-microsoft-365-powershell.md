---
title: حظر Microsoft 365 المستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: كيفية استخدام PowerShell لحظر الوصول إلى حسابات Microsoft 365 أو إلغاء حظره.
ms.openlocfilehash: 0ecfdfb8f99175ce5312769593c7637a7d1ae25b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569991"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a>حظر Microsoft 365 المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

عند حظر الوصول إلى حساب Microsoft 365، ستمنع أي شخص من استخدام الحساب في تسجيل الدخول والوصول إلى الخدمات والبيانات في Microsoft 365 مؤسستك. يمكنك استخدام PowerShell لحظر الوصول إلى حسابات المستخدمين الفردية أو حسابات المستخدمين المتعددة.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="block-access-to-individual-user-accounts"></a>حظر الوصول إلى حسابات المستخدمين الفردية

استخدم بناء الجملة التالي لحظر حساب مستخدم فردي:

```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> تقبل *المعلمة -ObjectID* في **الأمر cmdlet Set-AzureAD** إما اسم تسجيل الدخول للحساب، المعروف أيضا بالاسم الأساسي للمستخدم، أو بمعرف كائن الحساب.

يمنع هذا المثال الوصول إلى *حساب المستخدم fabricec@litwareinc.com*.

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

إلغاء حظر حساب المستخدم هذا، تشغيل الأمر التالي:

```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

لعرض UPN لحساب المستخدم استنادا إلى اسم العرض الخاص به، استخدم الأوامر التالية:

```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

يعرض هذا المثال حساب المستخدم UPN للمستخدم  *Caleb Sills*.

```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

لحظر حساب استنادا إلى اسم عرض المستخدم، استخدم الأوامر التالية:

```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

للتحقق من الحالة المحظورة لحساب مستخدم، استخدم الأمر التالي:

```powershell
Get-AzureADUser  -ObjectID <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-multiple-user-accounts"></a>حظر حسابات مستخدمين متعددة

لحظر الوصول لحسابات مستخدمين متعددة، أنشئ ملفا نصيا يحتوي على اسم تسجيل الدخول إلى حساب واحد على كل سطر مثل هذا:

  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

في الأوامر التالية، يكون المثال للملف النصي *C:\my Documents\Accounts.txt*. استبدل اسم الملف هذا بالمسار واسم الملف للملف النصي.

لحظر الوصول إلى الحسابات المدرجة في الملف النصي، يمكنك تشغيل الأمر التالي:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $false}
```

إلغاء حظر الحسابات المدرجة في الملف النصي، تشغيل الأمر التالي:

```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach {Set-AzureADUser -ObjectID $_ -AccountEnabled $true}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="block-individual-user-accounts"></a>حظر حسابات المستخدمين الفردية

استخدم بناء الجملة التالي لحظر الوصول إلى حساب مستخدم فردي:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets التي تتضمن *Msol* في اسمها. يجب تشغيل cmdlets هذه من Windows PowerShell.

يمنع هذا المثال الوصول إلى *حساب المستخدم fabricec litwareinc.com\@*.

```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

إلغاء حظر حساب المستخدم، تشغيل الأمر التالي:

```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

للتحقق من الحالة المحظورة لحساب مستخدم، قم بتشغيل الأمر التالي:

```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-for-multiple-user-accounts"></a>حظر الوصول إلى حسابات مستخدمين متعددة

أولا، أنشئ ملفا نصيا يحتوي على حساب واحد على كل سطر من هذا النوع:

```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

في الأوامر التالية، يكون المثال للملف النصي *C:\my Documents\Accounts.txt*. استبدل اسم الملف هذا بالمسار واسم الملف للملف النصي.

لحظر الوصول إلى الحسابات المدرجة في الملف النصي، يمكنك تشغيل الأمر التالي:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
إلغاء حظر الحسابات المدرجة في الملف النصي، تشغيل الأمر التالي:

  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
