---
title: إدارة Skype for Business عبر الإنترنت باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: استخدم PowerShell Microsoft 365 لإدارة Skype for Business الإنترنت ونهج كل مستخدم وإعدادات الاجتماعات.
ms.openlocfilehash: cb546a7e4130509d7acd0021b3cb78df23c1819f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474461"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>إدارة Skype for Business عبر الإنترنت باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

Skype for Business المسؤولين عبر الإنترنت عن إدارة السياسات. على الرغم من أنه يمكنك تنفيذ بعض هذه المهام في مركز مسؤولي Microsoft 365 المهام الأخرى في PowerShell.

## <a name="before-you-start"></a>قبل البدء

> [!NOTE]
> Skype for Business Online Connector حاليا جزءا من أحدث Teams PowerShell. إذا كنت تستخدم أحدث إصدار Teams **PowerShell** العام، فلا تحتاج إلى تثبيت Skype for Business Online Connector.

> [!NOTE]
> Skype for Business يمكن للمسؤولين عبر الإنترنت **إدارة Teams** ونهج **Skype for Business عبر** الإنترنت من خلال PowerShell.

قم بتثبيت [Teams PowerShell النمطية](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>الاتصال استخدام بيانات اعتماد المسؤول

1. افتح نافذة Windows PowerShell موجه الأوامر ثم ادير الأوامر التالية:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. في مربع **Windows PowerShell طلب** بيانات الاعتماد، اكتب اسم حساب المسؤول وكلمة المرور، ثم حدد **موافق**.

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>الاتصال استخدام حساب مسؤول مع مصادقة متعددة العوامل

1. افتح نافذة Windows PowerShell موجه الأوامر، ثم ادير الأوامر التالية:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. عند مطالبتك بإدخال اسم حساب Skype for Business Online.

3. في مربع **الحوار تسجيل الدخول** إلى حسابك، اكتب كلمة مرور Skype for Business عبر الإنترنت وحدد **تسجيل الدخول**.

4. في مربع **الحوار تسجيل الدخول** إلى حسابك، اتبع الإرشادات لإضافة معلومات المصادقة، مثل رمز التحقق، ثم حدد **التحقق**.

لمزيد من المعلومات، اطلع على:

- [إدارة Skype for Business عبر الإنترنت باستخدام PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [تعيين كل مستخدم Skype for Business Online باستخدام PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype for Business PowerShell cmdlet](/powershell/module/skype/)
