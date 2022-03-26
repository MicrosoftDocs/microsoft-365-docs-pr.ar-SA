---
title: الاتصال Microsoft 365 باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: الاتصال إلى Microsoft 365 المستأجر باستخدام PowerShell Microsoft 365 مهام مركز الإدارة من سطر الأوامر.
ms.openlocfilehash: 67c3a596d1b0d7acec2925f39c2f6bd8025d7d4a
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/03/2022
ms.locfileid: "63568776"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>الاتصال Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك PowerShell for Microsoft 365 من إدارة إعدادات Microsoft 365 من سطر الأوامر. للاتصال ب PowerShell، ما عليك سوى تثبيت البرنامج المطلوب ثم الاتصال Microsoft 365 مؤسستك.

هناك إصداران من وحدة PowerShell النمطية التي يمكنك استخدامها للاتصال Microsoft 365 حسابات المستخدمين والمجموعات والتراخيص وإدارتها:

- Azure Active Directory PowerShell for Graph، الذي تتضمن cmdlets *فيه AzureAD* في اسمه
- Microsoft Azure Active Directory النمطية Windows PowerShell، التي تتضمن cmdlets *Msol* في اسمها

في الوقت الحالي، لا تستبدل وحدة Azure Active Directory PowerShell ل Graph النمطية بالكامل وظائف وحدة Microsoft Azure Active Directory النمطية ل Windows PowerShell لإدارة المستخدم والمجموعة والترخيص. في بعض الحالات، تحتاج إلى استخدام الإصدارين. يمكنك تثبيت الإصدارين بأمان على الكمبيوتر نفسه.

>[!Note]
>يمكنك أيضا الاتصال ب [Azure Cloud Shell](#connect-with-the-azure-cloud-shell) من مركز مسؤولي Microsoft 365.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟


**نظام التشغيل**

يجب استخدام إصدار 64 بت من Windows. انتهى دعم الإصدار 32 بت من Microsoft Azure Active Directory النمطية Windows PowerShell 2014.

يمكنك استخدام الإصدارات التالية من Windows:
    
  - Windows 10 أو Windows 8.1 أو Windows 8 أو Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019 أو Windows Server 2016 أو Windows Server 2012 R2 أو Windows Server 2012 أو Windows Server 2008 R2 SP1

>[!Note]
>بالنسبة إلى Windows 8.1 و Windows 8 و Windows 7 Service Pack 1 (SP1) و Windows Server 2012 R2 و Windows Server 2012 و Windows Server 2008 R2 SP1، قم [بتنزيل إطار عمل إدارة Windows 5.1 وتثبيته](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- بالنسبة إلى وحدة Azure Active Directory PowerShell النمطية Graph، يجب استخدام الإصدار 5.1 من PowerShell.

- بالنسبة Microsoft Azure Active Directory الوحدة النمطية Windows PowerShell النمطية، يجب استخدام الإصدار 5.1 من PowerShell أو الإصدارات الأحدث، حتى الإصدار 6 من PowerShell. لا يمكنك استخدام الإصدار 7 من PowerShell.
       
>[!Note]
>هذه الإجراءات مخصصة للمستخدمين الأعضاء في Microsoft 365 المسؤول. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>الاتصال باستخدام وحدة Azure Active Directory PowerShell Graph النمطية

تتضمن الأوامر في وحدة Azure Active Directory PowerShell Graph النمطية *AzureAD* في اسم أمر cmdlet الخاص بها. يمكنك تثبيت [Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2) النمطية أو [Azure PowerShell](/powershell/azure/install-az-ps).

بالنسبة للإجراءات التي تتطلب cmdlets الجديدة في وحدة Azure Active Directory PowerShell النمطية ل Graph، اتبع هذه الخطوات لتثبيت الوحدة النمطية والاتصال باشتراكك في Microsoft 365.

> [!Note]
> للحصول على معلومات حول دعم الإصدارات المختلفة من Windows، راجع [Azure Active Directory PowerShell Graph النمطية .](/powershell/azure/active-directory/install-adv2)

### <a name="step-1-install-the-required-software"></a>الخطوة 1: تثبيت البرنامج المطلوب

هذه الخطوات مطلوبة مرة واحدة فقط على الكمبيوتر. ولكن من المرجح أنك ستحتاج إلى تحديث البرنامج بشكل دوري.
  
1. افتح نافذة موجه أوامر Windows PowerShell مرتفعة (Windows PowerShell كمسؤول).
    
2. تشغيل هذا الأمر:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  بشكل افتراضي، لا يتم تكوين معرض PowerShell (PSGallery) كمستودع موثوق به **ل PowerShellGet**. في المرة الأولى التي تستخدم فيها PSGallery، سترى الرسالة التالية:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

**أجب نعم** **أو نعم على الكل** للمتابعة مع التثبيت.

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>الخطوة 2: الاتصال Azure AD لاشتراكك Microsoft 365

للاتصال ب Azure Active Directory (Azure AD) لاشتراك Microsoft 365 باستخدام اسم حساب وكلمة مرور أو باستخدام مصادقة متعددة العوامل، قم بتشغيل أحد هذه الأوامر من موجه Windows PowerShell الأوامر. (لا يجب أن تكون مرتفعة.)

| Office 365 السحابة | الأمر |
|:-------|:-----|
| Office 365 حول العالم (+سحابة القطاع الحكومي) | `Connect-AzureAD` |
| Office 365 التي يتم تشغيلها بواسطة 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 ألمانيا | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 الحكومة الأمريكية Office 365 الحكومة الأمريكية سحابة القطاع الحكومي عالية | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

في مربع **الحوار** تسجيل الدخول إلى حسابك، اكتب Microsoft 365 المستخدم وكلمة المرور لحساب العمل أو المدرسة، ثم حدد **موافق**.

إذا كنت تستخدم مصادقة متعددة العوامل، فاتبع الإرشادات لتوفير معلومات مصادقة إضافية، مثل رمز التحقق.

بعد الاتصال، يمكنك استخدام cmdlets ل [Azure Active Directory PowerShell Graph النمطية](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>الاتصال الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell

>[!Note]
>تتضمن cmdlets في Microsoft Azure Active Directory النمطية Windows PowerShell *Msol* في اسمها.

لا يدعم الإصدار 7 من PowerShell والإصدارات الأحدث وحدة Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. بالنسبة للإصدار 7 من PowerShell والإصدارات الأحدث، يجب استخدام Microsoft Graph PowerShell SDK.

لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. تشغيل cmdlets هذه من Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>الخطوة 1: تثبيت البرنامج المطلوب

هذه الخطوات مطلوبة مرة واحدة فقط على الكمبيوتر. ولكن من المرجح أنك ستحتاج إلى تحديث البرنامج بشكل دوري.
  
1.  إذا كنت لا تقوم بتشغيل Windows 10، فثبت الإصدار 32 بت من مساعد تسجيل الدخول إلى Microsoft Online Services: مساعد تسجيل الدخول إلى [Microsoft Online Services](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi) لمحترفي تكنولوجيا المعلومات RTW.
    
2. اتبع هذه الخطوات لتثبيت الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell:
    
   1. افتح موجه أوامر Windows PowerShell (Windows PowerShell كمسؤول).
   1.  قم بتشغيل **الأمر تثبيت وحدة نمطية MSOnline** .
   1. إذا تم مطالبتك بتثبيت موفر NuGet، فاضغط **على Y** واضغط على Enter.
   1. إذا تم مطالبتك بتثبيت الوحدة النمطية من PSGallery، فاضغط على **Y** واضغط على Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>الخطوة 2: الاتصال Azure AD لاشتراكك Microsoft 365

للاتصال ب Azure AD لاشتراكك في Microsoft 365 باستخدام اسم حساب وكلمة مرور أو باستخدام مصادقة متعددة العوامل، قم بتشغيل أحد هذه الأوامر من موجه Windows PowerShell الأوامر. (لا يجب أن تكون مرتفعة.)

| Office 365 السحابة | الأمر |
|:-------|:-----|
| Office 365 حول العالم (+سحابة القطاع الحكومي) | `Connect-MsolService` |
| Office 365 التي يتم تشغيلها بواسطة 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 ألمانيا | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 الحكومة الأمريكية Office 365 الحكومة الأمريكية سحابة القطاع الحكومي عالية | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

في مربع **الحوار** تسجيل الدخول إلى حسابك، اكتب Microsoft 365 المستخدم وكلمة المرور لحساب العمل أو المدرسة، ثم حدد **موافق**.

إذا كنت تستخدم مصادقة متعددة العوامل، فاتبع الإرشادات لتوفير معلومات مصادقة إضافية، مثل رمز التحقق.

### <a name="how-do-you-know-it-worked"></a>كيف يمكنك معرفة كيفية عمل ذلك؟

إذا لم تحصل على رسالة خطأ، يمكنك الاتصال بنجاح. للاختبار السريع، يمكنك تشغيل Microsoft 365 cmdlet، مثل **Get-MsolUser**، وشاهد النتائج.
  
إذا حصلت على رسالة خطأ، فتحقق من المشاكل التالية:
  
- **المشكلة الشائعة هي كلمة مرور غير صحيحة**. تشغيل [الخطوة 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) مرة أخرى، وانتبه إلى اسم المستخدم وكلمة المرور التي تدخلها.
    
- **تتطلب Microsoft Azure Active Directory الوحدة النمطية Windows PowerShell Microsoft .NET Framework 3.5.* x* تم تمكينه على الكمبيوتر**. من المرجح أن* يكون الكمبيوتر مثبتا عليه إصدار أحدث (على سبيل المثال، 4 أو 4.5. x*). ولكن يمكن تمكين التوافق مع الإصدارات القديمة من .NET Framework أو تعطيله. لمزيد من المعلومات، راجع المقالات التالية:
    
  - بالنسبة Windows Server 2012 أو Windows Server 2012 R2، راجع [تمكين .NET Framework 3.5](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)) باستخدام معالج إضافة أدوار وميزات.
    
  - بالنسبة Windows 7 أو Windows Server 2008 R2، راجع لا يمكنك فتح [وحدة Azure Active Directory النمطية Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - للحصول Windows 10 و Windows 8.1 و Windows 8، راجع تثبيت [.NET Framework 3.5 على Windows 10 و Windows 8.1 و Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **قد يكون إصدار Microsoft Azure Active Directory النمطية Windows PowerShell غير محدث.** للتحقق، قم بتشغيل الأمر التالي في PowerShell Microsoft 365 أو Microsoft Azure Active Directory النمطية Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    إذا كان رقم الإصدار الذي تم إرجاعه أقل من *1.0.8070.2*، فقم ب إلغاء تثبيت وحدة Microsoft Azure Active Directory النمطية Windows PowerShell وتثبيتها من الخطوة [1](#step-1-install-the-required-software)، أعلاه.

- **إذا حصلت على رسالة خطأ اتصال**، [فشاهد رسالة الخطأ "الاتصال-MsolService: تم طرح استثناء من النوع](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception)".
    
- **إذا حصلت على رسالة الخطأ "Get-Item: لا يمكن العثور على مسار"**، ف تشغيل هذا الأمر:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>الاتصال باستخدام Azure Cloud Shell

للاتصال ب Azure Cloud Shell واستخدامه من مركز مسؤولي Microsoft 365، حدد أيقونة نافذة PowerShell من الزاوية العلوية اليسرى من شريط المهام. في الجزء **مرحبا بك في Azure Cloud Shell** ، حدد **PowerShell**.

ستحتاج إلى اشتراك Azure نشط لمنظمتك يرتبط باشتراكك Microsoft 365 اشتراكك. إذا لم يكن لديك حساب بالفعل، يمكنك إنشاء واحد. بمجرد الحصول على اشتراك Azure، يتم فتح نافذة PowerShell التي يمكنك تشغيل أوامر PowerShell والنصية منها.

لمزيد من المعلومات، راجع [Azure Cloud Shell](/azure/cloud-shell/overview).

## <a name="see-also"></a>راجع أيضًا

- [إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [الاتصال كافة Microsoft 365 في نافذة Windows PowerShell واحدة](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
