---
title: الاحتفاظ بعضوية مجموعة الأمان باستخدام PowerShell
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
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: تعرف على كيفية استخدام PowerShell للحفاظ على العضوية في Microsoft 365 المجموعات.
ms.openlocfilehash: 3637fb7d2e68091c43e624e9b6780d032c1930bc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575331"
---
# <a name="maintain-security-group-membership-with-powershell"></a>الاحتفاظ بعضوية مجموعة الأمان باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 كبديل مركز مسؤولي Microsoft 365 للحفاظ على عضوية مجموعة الأمان في Microsoft 365. 

>[!Note]
>[تعرف على كيفية المحافظة على Microsoft 365 عضوية المجموعة](../admin/create-groups/add-or-remove-members-from-groups.md) مع مركز مسؤولي Microsoft 365. للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية
أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>إضافة حسابات المستخدمين أو إزالتها كأعضاء في مجموعة

لإضافة حساب مستخدم بواسطة **UPN**، قم بتعبئة حساب المستخدم اسم المستخدم الأساسي (UPN) (على سبيل المثال: belindan@contoso.com) واسم عرض مجموعة الأمان، مع إزالة حرفي "<" و">"، ثم قم بتشغيل هذه الأوامر في نافذة PowerShell أو بيئة البرنامج النصي المتكاملة (ISE) في PowerShell.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإضافة حساب مستخدم حسب اسم العرض الخاص به، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Belinda Newman) واسم عرض المجموعة و شغل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإزالة حساب مستخدم بواسطة **UPN**، قم بتعبئة حساب المستخدم UPN (على سبيل المثال: belindan@contoso.com) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإزالة حساب مستخدم حسب اسم العرض الخاص به، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Belinda Newman) واسم عرض المجموعة و شغل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>إضافة مجموعات أو إزالتها كأعضاء في مجموعة

يمكن أن تحتوي مجموعات الأمان على مجموعات أخرى كأعضاء. Microsoft 365 المجموعات الأخرى. يحتوي هذا القسم على أوامر PowerShell لإضافة مجموعات أو إزالتها لمجموعة أمان فقط.

لإضافة مجموعة حسب اسم العرض الخاص بها، قم بتعبئة اسم عرض المجموعة التي تريد إضافتها واسم عرض المجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإزالة مجموعة حسب اسم العرض الخاص بها، قم بتعبئة اسم عرض المجموعة التي تريد إزالتها واسم عرض المجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>إضافة حسابات المستخدمين أو إزالتها كأعضاء في مجموعة

لإضافة حساب مستخدم بواسطة **UPN**، قم بتعبئة حساب المستخدم اسم المستخدم الأساسي (UPN) (على سبيل المثال: belindan@contoso.com) واسم عرض المجموعة، مع إزالة حرفي "<" و">"، ثم قم بتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإضافة حساب مستخدم حسب اسم العرض الخاص به، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Belinda Newman) واسم عرض المجموعة و شغل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإزالة حساب مستخدم بواسطة **UPN**، قم بتعبئة حساب المستخدم UPN (على سبيل المثال: belindan@contoso.com) واسم عرض المجموعة وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

لإزالة حساب مستخدم حسب اسم العرض الخاص به، قم بتعبئة اسم عرض حساب المستخدم (على سبيل المثال: Belinda Newman) واسم عرض المجموعة و شغل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>إضافة مجموعات أو إزالتها كأعضاء في مجموعة

يمكن أن تحتوي مجموعات الأمان على مجموعات أخرى كأعضاء. Microsoft 365 المجموعات الأخرى. يحتوي هذا القسم على أوامر PowerShell لإضافة مجموعات أو إزالتها لمجموعة أمان فقط.

لإضافة مجموعة حسب اسم العرض الخاص بها، قم بتعبئة اسم عرض المجموعة التي تريد إضافتها واسم عرض المجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

لإزالة مجموعة حسب اسم العرض الخاص بها، قم بتعبئة اسم عرض المجموعة التي تريد إزالتها واسم عرض المجموعة التي ستحتوي على مجموعة الأعضاء وتشغيل هذه الأوامر في نافذة PowerShell أو PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)