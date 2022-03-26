---
title: إدارة كلمات المرور باستخدام PowerShell
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
description: تعرف على كيفية استخدام PowerShell لإدارة كلمات المرور.
ms.openlocfilehash: 64c46f774db2ae2153ea336b8afb1f1aa7536d94
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569083"
---
# <a name="manage-passwords-with-powershell"></a>إدارة كلمات المرور باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 كبديل مركز مسؤولي Microsoft 365 لإدارة كلمات المرور في Microsoft 365. 

عندما تتطلب كتلة أوامر في هذه المقالة تحديد قيم متغيرة، استخدم هذه الخطوات.

1. انسخ كتلة الأوامر إلى الحافظة واللصق في المفكرة بيئة البرنامج النصي المتكاملة في PowerShell (ISE).
2. قم بتعبئة القيم المتغيرة وإزالة الأحرف "<" و">".
3. تشغيل الأوامر في نافذة PowerShell أو POWERShell ISE.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

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

استخدم هذه الأوامر لتعيين كلمة مرور وإجبار المستخدم على تغيير كلمة المرور الجديدة في المرة التالية التي يقوم فيها تسجيل الدخول.

```powershell
$userUPN="<user account sign in name, such as belindan@contoso.com>"
$newPassword="<new password>"
$secPassword = ConvertTo-SecureString $newPassword -AsPlainText -Force
Set-AzureADUserPassword -ObjectId  $userUPN -Password $secPassword -ForceChangePasswordNextLogin $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="set-a-password"></a>تعيين كلمة مرور

استخدم هذه الأوامر لتحديد كلمة مرور لحساب مستخدم.

```powershell
$userUPN="<user account sign in name>"
$newPassword="<new password>"
Set-MsolUserPassword -UserPrincipalName $userUPN -NewPassword $newPassword
```

### <a name="force-a-user-to-change-their-password"></a>إجبار المستخدم على تغيير كلمة المرور الخاصة به

استخدم هذه الأوامر لجبر المستخدم على تغيير كلمة المرور الخاصة به.

```powershell
$userUPN="<user account sign in name>"
Set-MsolUserPassword -UserPrincipalName $userUPN -ForceChangePassword $true
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)

