---
title: الاتصال إلى جميع خدمات Microsoft 365 في نافذة PowerShell واحدة
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/23/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'ملخص: الاتصال إلى جميع خدمات Microsoft 365 في نافذة PowerShell واحدة.'
ms.openlocfilehash: babb5c308310e1444a2ac20b6557f4f7a2050f79
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016889"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>الاتصال إلى جميع خدمات Microsoft 365 في نافذة PowerShell واحدة

عند استخدام PowerShell لإدارة Microsoft 365، يمكنك فتح جلسات عمل PowerShell متعددة في نفس الوقت. قد يكون لديك نوافذ PowerShell مختلفة لإدارة حسابات المستخدمين، SharePoint Online، Exchange Online، Microsoft Teams، ميزات Microsoft Defender لـ Office 365 (الأمان)، وميزات توافق Microsoft Purview.

هذا السيناريو ليس مثاليا لإدارة Microsoft 365، لأنه لا يمكنك تبادل البيانات بين تلك النوافذ لإدارة عبر الخدمات. تصف هذه المقالة كيفية استخدام مثيل واحد من PowerShell لإدارة حسابات Microsoft 365، Exchange Online، SharePoint Online، Microsoft Teams، والميزات في التوافق مع Microsoft Purview Defender لـ Office 365.

>[!Note]
>تحتوي هذه المقالة حاليا على الأوامر للاتصال بالسحابة العالمية (+سحابة القطاع الحكومي). توفر الملاحظات ارتباطات إلى مقالات حول الاتصال بسحابات Microsoft 365 الأخرى.

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إدارة جميع Microsoft 365 من مثيل واحد من PowerShell، ضع في اعتبارك المتطلبات الأساسية التالية:

- يجب أن يكون حساب العمل أو المؤسسة التعليمية Microsoft 365 الذي تستخدمه عضوا في دور مسؤول Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md). هذا متطلب ل PowerShell Microsoft 365، ولكن ليس بالضرورة لجميع خدمات Microsoft 365 الأخرى.

- يمكنك استخدام الإصدارات 64 بت التالية من Windows:
  - Windows 11
  - Windows 10
  - Windows 8.1 أو Windows 8
  - Windows Server 2019
  - Windows Server 2016‏
  - Windows Server 2012 R2 أو Windows Server 2012
  - Windows 7 حزمة خدمة 1 (SP1)*
  - Windows Server 2008 R2 SP1*

    \*تحتاج إلى تثبيت Microsoft .NET Framework 4.5.*x* ثم إطار عمل إدارة Windows 3.0 أو 4.0. لمزيد من المعلومات، راجع [إطار عمل إدارة Windows](/powershell/scripting/windows-powershell/wmf/overview).

- تحتاج إلى تثبيت الوحدات النمطية المطلوبة ل Azure Active Directory (Azure AD) Exchange Online Defender لـ Office 365 وتوافق Microsoft Purview SharePoint Online Teams:

  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Teams وحدة PowerShell](/microsoftteams/teams-powershell-overview)
  - [Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [نظرة عامة على Teams PowerShell](/microsoftteams/teams-powershell-overview)

- يجب تكوين PowerShell لتشغيل البرامج النصية الموقعة لتوافق Exchange Online Defender لـ Office 365 وMicrosoft Purview. قم بتشغيل الأمر التالي في جلسة عمل PowerShell غير مقيدة (جلسة عمل PowerShell التي تقوم **بتشغيلها كمسؤول**).

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>خطوات الاتصال عند استخدام كلمة مرور فقط

اتبع هذه الخطوات للاتصال بجميع الخدمات في نافذة PowerShell واحدة عند استخدام كلمة مرور فقط لتسجيل الدخول.

1. افتح Windows PowerShell.

2. قم بتشغيل هذا الأمر وأدخل بيانات اعتماد حساب العمل أو المؤسسة التعليمية Microsoft 365.

   ```powershell
   $credential = Get-Credential
   ```

3. قم بتشغيل هذا الأمر للاتصال Azure AD باستخدام Azure Active Directory PowerShell لوحدة Graph.

   ```powershell
   Connect-AzureAD -Credential $credential
   ```

   أو إذا كنت تستخدم الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell، فقم بتشغيل هذا الأمر.

   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!NOTE]
   > لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell و cmdlets مع *Msol* باسمها. يجب تشغيل أوامر cmdlets هذه من PowerShell.

4. قم بتشغيل هذه الأوامر للاتصال ب SharePoint Online. حدد اسم المؤسسة لمجالك. على سبيل المثال، بالنسبة إلى "litwareinc\.onmicrosoft.com"، تكون قيمة اسم المؤسسة "litwareinc".

   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. قم بتشغيل هذه الأوامر للاتصال Exchange Online.

   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -ShowProgress $true
   ```

   > [!Note]
   > للاتصال Exchange Online للسحب Microsoft 365 غير جميع أنحاء العالم، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. قم بتشغيل هذه الأوامر للاتصال ب Security & Compliance PowerShell.

   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!NOTE]
   > للاتصال ب Security & Compliance PowerShell للسحابات Microsoft 365 غير حول العالم، راجع [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

7. قم بتشغيل هذه الأوامر للاتصال Teams PowerShell.

   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```

   > [!NOTE]
   > Skype for Business Online Connector هو حاليا جزء من أحدث وحدة Teams PowerShell. إذا كنت تستخدم أحدث إصدار عام Teams PowerShell، فلن تحتاج إلى تثبيت Skype for Business Online Connector.
   >
   > للاتصال بسحابات Microsoft Teams غير *"جميع أنحاء العالم*"، راجع [الاتصال-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).

### <a name="azure-active-directory-powershell-for-graph-module-when-using-just-a-password"></a>Azure Active Directory PowerShell لوحدة Graph عند استخدام كلمة مرور فقط

فيما يلي الأوامر لكافة الخدمات في كتلة واحدة عند استخدام Azure Active Directory PowerShell للوحدة النمطية Graph. حدد اسم مضيف المجال و UPN لتسجيل الدخول وقم بتشغيلها جميعا في نفس الوقت.

```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-AzureAD -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-just-a-password"></a>Microsoft Azure Active Directory الوحدة النمطية للوحدة النمطية Windows PowerShell عند استخدام كلمة مرور فقط

فيما يلي الأوامر لكافة الخدمات في كتلة واحدة عند استخدام الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell. حدد اسم مضيف المجال و UPN لتسجيل الدخول وقم بتشغيلها جميعا في وقت واحد.

```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-MsolService -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>خطوات الاتصال عند استخدام المصادقة متعددة العوامل

### <a name="azure-active-directory-powershell-for-graph-module-when-using-mfa"></a>Azure Active Directory PowerShell لوحدة Graph عند استخدام MFA

فيما يلي جميع الأوامر في كتلة واحدة للاتصال بخدمات Microsoft 365 متعددة عند استخدام المصادقة متعددة العوامل مع Azure Active Directory PowerShell للوحدة النمطية Graph.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module-when-using-mfa"></a>Microsoft Azure Active Directory الوحدة النمطية للوحدة النمطية Windows PowerShell عند استخدام المصادقة متعددة العوامل

فيما يلي جميع الأوامر في كتلة واحدة للاتصال بخدمات Microsoft 365 متعددة عند استخدام المصادقة متعددة العوامل مع الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

## <a name="close-the-powershell-window"></a>إغلاق نافذة PowerShell

لإغلاق نافذة PowerShell، قم بتشغيل هذا الأمر لإزالة جلسات العمل النشطة إلى توافق SharePoint Online و Teams Defender لـ Office 365 وMicrosoft Purview:

```powershell
Disconnect-SPOService; Disconnect-MicrosoftTeams; Disconnect-ExchangeOnline
```

## <a name="see-also"></a>راجع أيضًا

- [الاتصال بـ Microsoft 365 باستخدام PowerShell](connect-to-microsoft-365-powershell.md)
- [إدارة SharePoint Online باستخدام PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
