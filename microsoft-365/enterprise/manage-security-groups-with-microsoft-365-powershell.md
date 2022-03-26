---
title: إدارة مجموعات الأمان باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية استخدام PowerShell لإدارة مجموعات الأمان.
ms.openlocfilehash: d07296b88e626e854c57152a079cc96e1e23e8d3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569084"
---
# <a name="manage-security-groups-with-powershell"></a>إدارة مجموعات الأمان باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 كبديل مركز مسؤولي Microsoft 365 لإدارة مجموعات الأمان. 

تصف هذه المقالة سرد مجموعات الأمان وإنشاءها وتغييرها وإزالة مجموعات الأمان. 

عندما تتطلب كتلة أوامر في هذه المقالة تحديد قيم متغيرة، استخدم هذه الخطوات.

1. انسخ كتلة الأوامر إلى الحافظة واللصق في المفكرة بيئة البرنامج النصي المتكاملة في PowerShell (ISE).
2. قم بتعبئة القيم المتغيرة وإزالة الأحرف "<" و">".
3. تشغيل الأوامر في نافذة PowerShell أو POWERShell ISE.

راجع [الاحتفاظ بعضوية مجموعة الأمان](maintain-group-membership-with-microsoft-365-powershell.md) لإدارة عضوية المجموعة باستخدام PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="list-your-groups"></a>سرد المجموعات

استخدم هذا الأمر لتضمين كل المجموعات.

```powershell
Get-AzureADGroup
```
استخدم هذه الأوامر لعرض إعدادات مجموعة معينة حسب اسم العرض الخاص بها.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>إنشاء مجموعة جديدة

استخدم هذا الأمر لإنشاء مجموعة أمان جديدة.

```powershell
New-AzureADGroup -Description "<group purpose>" -DisplayName "<name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "<email name>"
```

### <a name="change-the-settings-on-a-group"></a>تغيير الإعدادات في مجموعة

عرض إعدادات المجموعة باستخدام هذه الأوامر.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

بعد ذلك، استخدم المقالة [Set-AzureADGroup](/powershell/module/azuread/set-azureadgroup) لتحديد كيفية تغيير إعداد.

### <a name="remove-a-security-group"></a>إزالة مجموعة أمان

استخدم هذه الأوامر لإزالة مجموعة أمان.

```powershell
$groupName="<display name of the group>"
Remove-AzureADGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

### <a name="manage-the-owners-of-a-security-group"></a>إدارة مالكي مجموعة أمان

استخدم هذه الأوامر لعرض المالكين الحاليين لمجموعة أمان.

```powershell
$groupName="<display name of the group>"
Get-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```
استخدم هذه الأوامر لإضافة حساب مستخدم حسب اسم المستخدم الأساسي **(UPN)** إلى المالكين الحاليين لمجموعة أمان.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```
استخدم هذه الأوامر لإضافة حساب مستخدم حسب اسم العرض الخاص به  إلى المالكين الحاليين لمجموعة أمان.

```powershell
$userName="<Display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```
استخدم هذه الأوامر لإزالة حساب مستخدم بواسطة **UPN** الخاص به إلى المالكين الحاليين لمجموعة أمان.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectId
```

استخدم هذه الأوامر لإزالة حساب مستخدم باسم العرض الخاص به إلى  المالكين الحاليين لمجموعة أمان.

```powershell
$userName="<Display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupOwner -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId -OwnerId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectId
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="list-your-groups"></a>سرد المجموعات

استخدم هذا الأمر لتضمين كل المجموعات.

```powershell
Get-MsolGroup
```
استخدم هذه الأوامر لعرض إعدادات مجموعة معينة حسب اسم العرض الخاص بها.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName }
```

### <a name="create-a-new-group"></a>إنشاء مجموعة جديدة

استخدم هذا الأمر لإنشاء مجموعة أمان جديدة.

```powershell
New-MsolGroup -Description "<group purpose>" -DisplayName "<name>"
```

### <a name="change-the-settings-on-a-group"></a>تغيير الإعدادات في مجموعة

عرض إعدادات المجموعة باستخدام هذه الأوامر.

```powershell
$groupName="<display name of the group>"
Get-MsolGroup | Where { $_.DisplayName -eq $groupName } | Select *
```

بعد ذلك، استخدم المقالة [Set-MsolGroup](/powershell/module/msonline/set-msolgroup) لتحديد كيفية تغيير إعداد.

### <a name="remove-a-security-group"></a>إزالة مجموعة أمان

استخدم هذه الأوامر لإزالة مجموعة أمان.

```powershell
$groupName="<display name of the group>"
Remove-MsolGroup -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectId
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)