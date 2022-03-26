---
title: الاتصال جميع Microsoft 365 في نافذة PowerShell واحدة
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
description: 'ملخص: الاتصال كافة Microsoft 365 في نافذة PowerShell واحدة.'
ms.openlocfilehash: 4df9a16aba22587adbe289bca2d74e78a64db4ba
ms.sourcegitcommit: b51bfed24a9e3b7adf82d4918b76462cd40dffaf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63569599"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>الاتصال جميع Microsoft 365 في نافذة PowerShell واحدة

عند استخدام PowerShell لإدارة Microsoft 365، يمكنك فتح جلسات PowerShell متعددة في الوقت نفسه. قد يكون لديك نوافذ PowerShell مختلفة لإدارة حسابات المستخدمين، SharePoint عبر الإنترنت، Exchange Online، Skype for Business عبر الإنترنت، Microsoft Teams&amp;، ومركز توافق الأمان.
  
هذا السيناريو ليس الأمثل لإدارة Microsoft 365، لأنه لا يمكنك تبادل البيانات بين تلك النوافذ لإدارة الخدمات عبر الخدمات. تصف هذه المقالة كيفية استخدام مثيل واحد من PowerShell لإدارة حسابات Microsoft 365 و Skype for Business Online و Exchange Online و SharePoint Online و Microsoft Teams و مركز &amp; توافق الأمان.

>[!Note]
>تحتوي هذه المقالة حاليا على الأوامر للاتصال بالسحابة العالمية (+سحابة القطاع الحكومي). توفر الملاحظات ارتباطات إلى مقالات حول الاتصال بسحابة Microsoft 365 أخرى.

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إدارة كل Microsoft 365 من مثيل واحد من PowerShell، يجب عليك التفكير في المتطلبات الأساسية التالية:
  
- يجب Microsoft 365 حساب العمل أو المؤسسة الدراسية الذي تستخدمه عضوا في Microsoft 365 مسؤول. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md). هذا متطلب ل PowerShell Microsoft 365، ولكن ليس بالضرورة لجميع الخدمات Microsoft 365 الأخرى.
    
- يمكنك استخدام إصدارات 64 بت التالية من Windows:
    
  - Windows 10
    
  - Windows 8.1 أو Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016‏
    
  - Windows Server 2012 R2 أو Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*تحتاج إلى تثبيت Microsoft .NET Framework 4.5.*x* ثم إطار عمل إدارة Windows 3.0 أو 4.0. لمزيد من المعلومات[، راجع إطار عمل إدارة Windows](/powershell/scripting/windows-powershell/wmf/overview).
    
    تحتاج إلى استخدام إصدار 64 بت من Windows بسبب متطلبات الوحدة النمطية Skype for Business Online وأحد Microsoft 365 النمطية.
    
- تحتاج إلى تثبيت الوحدات النمطية المطلوبة ل Azure Active Directory (Azure AD) Exchange Online و SharePoint عبر الإنترنت Skype for Business عبر الإنترنت Teams:
    
  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Skype for Business Online، وحدة PowerShell النمطية](/microsoftteams/teams-powershell-overview)
  - [Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Teams نظرة عامة حول PowerShell](/microsoftteams/teams-powershell-overview)
    
-  يجب تكوين PowerShell لتشغيل البرامج النصية الموقعة Skype for Business عبر الإنترنت ومركز توافق &amp; الأمان. تشغيل الأمر التالي في جلسة PowerShell مرتفعة (جلسة PowerShell تقوم **بتشغيلها كمسؤول**).
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>خطوات الاتصال عند استخدام كلمة مرور فقط

اتبع هذه الخطوات للاتصال بكل الخدمات في نافذة PowerShell واحدة عندما تستخدم كلمة مرور فقط من أجل تسجيل الدخول.
  
1. افتح Windows PowerShell.
    
2. تشغيل هذا الأمر وأدخل بيانات Microsoft 365 بيانات اعتماد حساب العمل أو المدرسة.
    
   ```powershell
   $credential = Get-Credential
   ```

3. قم بتشغيل هذا الأمر للاتصال ب Azure AD باستخدام Azure Active Directory PowerShell Graph النمطية.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   أو إذا كنت تستخدم الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية، فدير هذا الأمر.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. يجب تشغيل cmdlets هذه من PowerShell.

4. قم بتشغيل هذه الأوامر للاتصال SharePoint Online. حدد اسم المؤسسة لمجالك. على سبيل المثال، بالنسبة إلى "litwareinc\. onmicrosoft.com"، تكون قيمة اسم المؤسسة "litwareinc".
    
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
   > للاتصال بسحابات Exchange Online ل Microsoft 365 أخرى غير جميع أنحاء العالم، راجع الاتصال إلى [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

6. قم بتشغيل هذه الأوامر للاتصال بمركز توافق &amp; الأمان.
    
   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!Note]
   > للاتصال بمركز التوافق الأمني &amp; لسحابات Microsoft 365 أخرى غير جميع أنحاء العالم، راجع الاتصال إلى مركز التوافق & [PowerShell](/powershell/exchange/connect-to-scc-powershell).

7. قم بتشغيل هذه الأوامر للاتصال Teams PowerShell (Skype for Business Online).
    
   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Skype for Business Online Connector حاليا جزءا من أحدث Teams PowerShell. إذا كنت تستخدم أحدث إصدار Teams PowerShell العام، فلا تحتاج إلى تثبيت Skype for Business Online Connector.
  
   > [!Note]
   > للاتصال بسحابات Microsoft Teams أخرى غير جميع *أنحاء العالم،* راجع الاتصال [MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).
  


### <a name="azure-active-directory-powershell-for-graph-module"></a>وحدة Azure Active Directory PowerShell Graph النمطية

فيما يلي أوامر جميع الخدمات في كتلة واحدة عند استخدام Azure Active Directory PowerShell Graph النمطية. حدد اسم مضيف المجال و UPN تسجيل الدخول و قم بتشغيلهما جميعا في الوقت نفسه.
  
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
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory الوحدة النمطية Windows PowerShell النمطية

فيما يلي أوامر لكل الخدمات في كتلة واحدة عند استخدام الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية. حدد اسم مضيف المجال و UPN تسجيل الدخول وتشغيلها كلها مرة واحدة.
  
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
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>خطوات الاتصال عند استخدام المصادقة متعددة العوامل

### <a name="azure-active-directory-powershell-for-graph-module"></a>وحدة Azure Active Directory PowerShell Graph النمطية

فيما يلي كل الأوامر في كتلة واحدة للاتصال Microsoft 365 متعددة عند استخدام مصادقة متعددة العوامل مع وحدة Azure Active Directory PowerShell Graph النمطية.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
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
### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory الوحدة النمطية Windows PowerShell النمطية

فيما يلي كل الأوامر في كتلة واحدة للاتصال Microsoft 365 متعددة عند استخدام مصادقة متعددة العوامل مع وحدة Microsoft Azure Active Directory النمطية Windows PowerShell النمطية.

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

لإغلاق نافذة PowerShell، قم بتشغيل هذا الأمر لإزالة جلسات العمل النشطة SharePoint عبر الإنترنت Teams:
  
```powershell
Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="see-also"></a>راجع أيضًا

- [الاتصال Microsoft 365 باستخدام PowerShell](connect-to-microsoft-365-powershell.md)
- [إدارة SharePoint عبر الإنترنت باستخدام PowerShell](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
