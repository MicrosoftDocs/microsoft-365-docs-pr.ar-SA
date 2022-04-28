---
title: إدارة Skype for Business Online باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: استخدم PowerShell Microsoft 365 لإدارة نهج Skype for Business Online ونهج كل مستخدم وإعدادات الاجتماع.
ms.openlocfilehash: 1c3a3e06d3fa607765382176a8c291fab2c69636
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097657"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>إدارة Skype for Business Online باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

مسؤولو Skype for Business Online مسؤولون عن إدارة النهج. على الرغم من أنه يمكنك القيام ببعض هذه المهام في مركز مسؤولي Microsoft 365، فإن البعض الآخر أسهل في PowerShell.

## <a name="before-you-start"></a>قبل البدء

> [!NOTE]
> Skype for Business Online Connector هو حاليا جزء من أحدث وحدة Teams PowerShell. إذا كنت تستخدم أحدث **إصدار عام Teams PowerShell**، فلن تحتاج إلى تثبيت Skype for Business Online Connector.

> [!NOTE]
> Skype for Business يمكن للمسؤولين عبر الإنترنت إدارة **كل من Teams** ونهج تطبيق **Skype for Business Online** من خلال PowerShell.

تثبيت [الوحدة النمطية Teams PowerShell](/microsoftteams/teams-powershell-install).

## <a name="connect-using-admin-credentials"></a>الاتصال باستخدام بيانات اعتماد المسؤول

1. افتح نافذة موجه الأوامر Windows PowerShell وقم بتشغيل الأوامر التالية:

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. في **مربع الحوار "طلب بيانات الاعتماد" Windows PowerShell**، اكتب اسم حساب المسؤول وكلمة المرور، ثم حدد **"موافق**".

## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>الاتصال باستخدام حساب مسؤول مع مصادقة متعددة العوامل

1. افتح نافذة موجه الأوامر Windows PowerShell، ثم قم بتشغيل الأوامر التالية:

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. عند مطالبتك بإدخال اسم حساب مسؤول Skype for Business Online.

3. في مربع الحوار **"تسجيل الدخول إلى حسابك**"، اكتب كلمة مرور مسؤول Skype for Business Online وحدد **"تسجيل الدخول**".

4. في مربع الحوار **"تسجيل الدخول إلى حسابك**"، اتبع الإرشادات لإضافة معلومات المصادقة، مثل رمز التحقق، ثم حدد **"التحقق".**

لمزيد من المعلومات، اطلع على:

- [إدارة نهج Skype for Business Online باستخدام PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)

- [تعيين نهج Skype for Business Online لكل مستخدم باستخدام PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Skype for Business مراجع PowerShell cmdlet](/powershell/module/skype/)
