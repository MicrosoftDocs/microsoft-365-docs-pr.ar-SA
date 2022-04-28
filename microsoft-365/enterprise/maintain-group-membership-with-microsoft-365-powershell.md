---
title: الحفاظ على عضوية مجموعة الأمان باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: تعرف على كيفية استخدام PowerShell للحفاظ على العضوية في مجموعات Microsoft 365.
ms.openlocfilehash: 48720d5f3922598feec5a64eaa2c2532e17248ad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095675"
---
# <a name="maintain-security-group-membership-with-powershell"></a>الحفاظ على عضوية مجموعة الأمان باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 كبديل مركز مسؤولي Microsoft 365 للحفاظ على عضوية مجموعة الأمان في Microsoft 365. 

>[!Note]
>[تعرف على كيفية الحفاظ على عضوية مجموعة Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md) باستخدام مركز مسؤولي Microsoft 365. للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph
أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>إضافة حسابات المستخدمين أو إزالتها كأعضاء في مجموعة

**لإضافة حساب مستخدم بواسطة UPN الخاص به**، قم بتعبئة اسم المستخدم الأساسي (UPN) لحساب المستخدم (على سبيل المثال: belindan@contoso.com) واسم عرض مجموعة الأمان، وإزالة الأحرف "<" و">"، وتشغيل هذه الأوامر في نافذة PowerShell أو بيئة البرنامج النصي المتكامل PowerShell (ISE).

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإضافة حساب مستخدم باسم العرض الخاص به**، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Beplay Newman) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإزالة حساب مستخدم بواسطة UPN الخاص به**، قم بتعبئة UPN لحساب المستخدم (على سبيل المثال: belindan@contoso.com) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإزالة حساب مستخدم باسم العرض الخاص به**، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Beplay Newman) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>إضافة مجموعات أو إزالتها كأعضاء في مجموعة

يمكن أن تحتوي مجموعات الأمان على مجموعات أخرى كأعضاء. ومع ذلك، لا يمكن Microsoft 365 المجموعات. يحتوي هذا المقطع على أوامر PowerShell لإضافة مجموعات لمجموعة أمان فقط أو إزالتها.

**لإضافة مجموعة حسب اسم العرض الخاص بها**، قم بتعبئة اسم العرض للمجموعة التي ستقوم بإضافتها واسم العرض للمجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإزالة مجموعة باسم العرض الخاص بها**، قم بتعبئة اسم عرض المجموعة التي ستقوم بإزالتها واسم العرض للمجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>إضافة حسابات المستخدمين أو إزالتها كأعضاء في مجموعة

**لإضافة حساب مستخدم بواسطة UPN الخاص به**، قم بتعبئة اسم المستخدم الأساسي (UPN) لحساب المستخدم (على سبيل المثال: belindan@contoso.com) واسم عرض المجموعة، وإزالة الأحرف "<" و">"، وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإضافة حساب مستخدم باسم العرض الخاص به**، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Beplay Newman) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإزالة حساب مستخدم بواسطة UPN الخاص به**، قم بتعبئة UPN لحساب المستخدم (على سبيل المثال: belindan@contoso.com) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**لإزالة حساب مستخدم باسم العرض الخاص به**، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Beplay Newman) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>إضافة مجموعات أو إزالتها كأعضاء في مجموعة

يمكن أن تحتوي مجموعات الأمان على مجموعات أخرى كأعضاء. ومع ذلك، لا يمكن Microsoft 365 المجموعات. يحتوي هذا المقطع على أوامر PowerShell لإضافة مجموعات لمجموعة أمان فقط أو إزالتها.

**لإضافة مجموعة حسب اسم العرض الخاص بها**، قم بتعبئة اسم العرض للمجموعة التي ستقوم بإضافتها واسم العرض للمجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**لإزالة مجموعة باسم العرض الخاص بها**، قم بتعبئة اسم عرض المجموعة التي ستقوم بإزالتها واسم العرض للمجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)