---
title: إدارة كلمات المرور باستخدام PowerShell
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
description: تعرف على كيفية استخدام PowerShell لإدارة كلمات المرور.
ms.openlocfilehash: e980e9c4c2511ea1f84df870c790a61a047c3a90
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091556"
---
# <a name="manage-passwords-with-powershell"></a>إدارة كلمات المرور باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 كبديل مركز مسؤولي Microsoft 365 لإدارة كلمات المرور في Microsoft 365. 

عندما تتطلب كتلة الأوامر في هذه المقالة تحديد قيم متغيرة، استخدم هذه الخطوات.

1. انسخ كتلة الأوامر إلى الحافظة والصقها في المفكرة أو بيئة البرنامج النصي المتكامل PowerShell (ISE).
2. املأ القيم المتغيرة وقم بإزالة الأحرف "<" و">".
3. تشغيل الأوامر في نافذة PowerShell أو PowerShell ISE.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="set-a-password"></a>تعيين كلمة مرور

استخدم هذه الأوامر لتحديد كلمة مرور لحساب مستخدم.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword
```
### <a name="force-a-user-to-change-their-password"></a>إجبار المستخدم على تغيير كلمة المرور الخاصة به

استخدم هذه الأوامر لتعيين كلمة مرور وإجبار المستخدم على تغيير كلمة المرور الجديدة.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -EnforceChangePasswordPolicy $true
```

استخدم هذه الأوامر لتعيين كلمة مرور وإجبار المستخدم على تغيير كلمة المرور الجديدة في المرة التالية التي يسجل فيها الدخول.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -ForceChangePasswordNextLogin $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="set-a-password"></a>تعيين كلمة مرور

استخدم هذه الأوامر لتحديد كلمة مرور لحساب مستخدم.

```powershell
$userUPN="<user account sign in name>"
$newPassword="<new password>"
Set-MsolUserPassword -UserPrincipalName $userUPN -NewPassword $newPassword
```

### <a name="force-a-user-to-change-their-password"></a>إجبار المستخدم على تغيير كلمة المرور الخاصة به

استخدم هذه الأوامر لإجبار المستخدم على تغيير كلمة المرور الخاصة به.

```powershell
$userUPN="<user account sign in name>"
Set-MsolUserPassword -UserPrincipalName $userUPN -ForceChangePassword $true
```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)

