---
title: الاتصال بـ Microsoft 365 باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: الاتصال إلى مستأجر Microsoft 365 باستخدام PowerShell Microsoft 365 لتنفيذ مهام مركز الإدارة من سطر الأوامر.
ms.openlocfilehash: a69fa6885e254e0c15cd65833a4f8368ec239c4f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174827"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>الاتصال بـ Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك PowerShell ل Microsoft 365 من إدارة إعدادات Microsoft 365 من سطر الأوامر. للاتصال ب PowerShell، ما عليك سوى تثبيت البرنامج المطلوب ثم الاتصال بمؤسستك Microsoft 365.

هناك إصداران من الوحدة النمطية PowerShell يمكنك استخدامهما للاتصال Microsoft 365 وإدارة حسابات المستخدمين والمجموعات والتراخيص:

- Azure Active Directory PowerShell ل Graph، والتي تتضمن أوامر cmdlets الخاصة بها *AzureAD* باسمها
- Microsoft Azure Active Directory الوحدة النمطية Windows PowerShell، التي تتضمن أوامر cmdlets *Msol* باسمها

حاليا، لا تحل الوحدة النمطية Azure Active Directory PowerShell لوحدة Graph محل وظائف الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell لإدارة المستخدم والمجموعة والترخيص. في بعض الحالات، تحتاج إلى استخدام كلا الإصدارين. يمكنك تثبيت كلا الإصدارين بأمان على نفس الكمبيوتر.

>[!Note]
>يمكنك أيضا الاتصال ب [Azure Cloud Shell](#connect-with-the-azure-cloud-shell) من مركز مسؤولي Microsoft 365.
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟


**نظام التشغيل**

يجب استخدام إصدار 64 بت من Windows. انتهى دعم الإصدار 32 بت من الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell في عام 2014.

يمكنك استخدام الإصدارات التالية من Windows:
    
  - Windows 10 أو Windows 8.1 أو Windows 8 أو Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019 أو Windows Server 2016 أو Windows Server 2012 R2 أو Windows Server 2012 أو Windows Server 2008 R2 SP1

>[!Note]
>بالنسبة إلى Windows 8.1، Windows 8، Windows 7 حزمة خدمة 1 (SP1)، Windows Server 2012 R2، Windows Server 2012، Windows Server 2008 R2 SP1، قم بتنزيل [إطار عمل إدارة Windows 5.1](https://www.microsoft.com/download/details.aspx?id=54616) وتثبيته.

**PowerShell**

- بالنسبة إلى Azure Active Directory PowerShell للوحدة النمطية Graph، يجب استخدام PowerShell الإصدار 5.1.

- بالنسبة للوحدة Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell، يجب استخدام الإصدار 5.1 من PowerShell أو إصدار أحدث، حتى إصدار PowerShell 6. لا يمكنك استخدام الإصدار 7 من PowerShell.
       
>[!Note]
>هذه الإجراءات مخصصة للمستخدمين الأعضاء في دور مسؤول Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>الاتصال مع الوحدة النمطية Azure Active Directory PowerShell Graph

تحتوي الأوامر في Azure Active Directory PowerShell لوحدة Graph على *AzureAD* باسم cmdlet الخاص بها. يمكنك تثبيت [Azure Active Directory PowerShell لوحدة Graph](/powershell/azure/active-directory/install-adv2) أو [Azure PowerShell](/powershell/azure/install-az-ps).

للإجراءات التي تتطلب أوامر cmdlets الجديدة في Azure Active Directory PowerShell للوحدة النمطية Graph، اتبع هذه الخطوات لتثبيت الوحدة النمطية والاتصال باشتراكك في Microsoft 365.

> [!Note]
> للحصول على معلومات حول دعم الإصدارات المختلفة من Windows، راجع [Azure Active Directory PowerShell للوحدة النمطية Graph](/powershell/azure/active-directory/install-adv2).

### <a name="step-1-install-the-required-software"></a>الخطوة 1: تثبيت البرنامج المطلوب

هذه الخطوات مطلوبة مرة واحدة فقط على الكمبيوتر. ولكن من المحتمل أن تحتاج إلى تحديث البرنامج بشكل دوري.
  
1. افتح نافذة موجه الأوامر Windows PowerShell غير مقيدة (قم بتشغيل Windows PowerShell كمسؤول).
    
2. تشغيل هذا الأمر:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  بشكل افتراضي، لا يتم تكوين معرض PowerShell (PSGallery) كمستودع موثوق به ل **PowerShellGet**. في المرة الأولى التي تستخدم فيها PSGallery، سترى الرسالة التالية:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

أجب ب **"نعم** " أو **"نعم للكل** " لمتابعة التثبيت.

3.  تشغيل هذا الأمر لاستيراد الوحدة النمطية:
    
    ```powershell
    Import-Module  AzureAD
    ```
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>الخطوة 2: الاتصال Azure AD لاشتراكك في Microsoft 365

للاتصال ب Azure Active Directory (Azure AD) لاشتراكك Microsoft 365 باسم حساب وكلمة مرور أو باستخدام مصادقة متعددة العوامل، قم بتشغيل أحد هذه الأوامر من موجه أوامر Windows PowerShell. (لا يجب أن يكون مرتفعا.)

| سحابة Office 365 | الامر |
|:-------|:-----|
| Office 365 حول العالم (+سحابة القطاع الحكومي) | `Connect-AzureAD` |
| Office 365 المشغل بواسطة 21 Vianet | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 ألمانيا | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365 سحابة القطاع الحكومي حكومة الولايات المتحدة Office 365 حكومة الولايات المتحدة | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

في مربع الحوار **"تسجيل الدخول إلى حسابك**"، اكتب Microsoft 365 اسم مستخدم حساب العمل أو المؤسسة التعليمية وكلمة المرور، ثم حدد **"موافق**".

إذا كنت تستخدم مصادقة متعددة العوامل، فاتبع الإرشادات لتوفير معلومات مصادقة إضافية، مثل رمز التحقق.

بعد الاتصال، يمكنك استخدام cmdlets لوحدة [Azure Active Directory PowerShell للوحدة النمطية Graph](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>الاتصال مع الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

>[!Note]
>تحتوي أوامر Cmdlets في الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell على *Msol* باسمها.

لا يدعم الإصدار 7 من PowerShell والإصدارات الأحدث الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع *Msol* باسمها. للإصدار 7 من PowerShell والإصدارات الأحدث، يجب استخدام Microsoft Graph PowerShell SDK.

لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell و cmdlets مع *Msol* باسمها. تشغيل أوامر cmdlets هذه من Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>الخطوة 1: تثبيت البرنامج المطلوب

هذه الخطوات مطلوبة مرة واحدة فقط على الكمبيوتر. ولكن من المحتمل أن تحتاج إلى تحديث البرنامج بشكل دوري.
  
1.  إذا كنت لا تقوم بتشغيل Windows 10، فقم بتثبيت الإصدار 32 بت من مساعد تسجيل الدخول إلى Microsoft Online Services: [مساعد تسجيل الدخول إلى Microsoft Online Services لمحترفي تكنولوجيا المعلومات RTW](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi).
    
2. اتبع هذه الخطوات لتثبيت الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell:
    
   1. افتح موجه أوامر Windows PowerShell غير مقيد (قم بتشغيل Windows PowerShell كمسؤول).
   1.  تشغيل الأمر **Install-Module MSOnline** .
   1. إذا تمت مطالبتك بتثبيت موفر NuGet، فاكتب **Y** واضغط على مفتاح الإدخال Enter.
   1. إذا تمت مطالبتك بتثبيت الوحدة النمطية من PSGallery، فاكتب **Y** واضغط على مفتاح الإدخال Enter.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>الخطوة 2: الاتصال Azure AD لاشتراكك في Microsoft 365

للاتصال Azure AD لاشتراكك في Microsoft 365 باسم حساب وكلمة مرور أو باستخدام مصادقة متعددة العوامل، قم بتشغيل أحد هذه الأوامر من موجه أوامر Windows PowerShell. (لا يجب أن يكون مرتفعا.)

| سحابة Office 365 | الامر |
|:-------|:-----|
| Office 365 حول العالم (+سحابة القطاع الحكومي) | `Connect-MsolService` |
| Office 365 المشغل بواسطة 21 Vianet | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 ألمانيا | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365 سحابة القطاع الحكومي حكومة الولايات المتحدة Office 365 حكومة الولايات المتحدة | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

في مربع الحوار **"تسجيل الدخول إلى حسابك**"، اكتب Microsoft 365 اسم مستخدم حساب العمل أو المؤسسة التعليمية وكلمة المرور، ثم حدد **"موافق**".

إذا كنت تستخدم مصادقة متعددة العوامل، فاتبع الإرشادات لتوفير معلومات مصادقة إضافية، مثل رمز التحقق.

### <a name="how-do-you-know-it-worked"></a>كيف تعرف أنه يعمل؟

إذا لم تحصل على رسالة خطأ، فيمكنك الاتصال بنجاح. للاختبار السريع، قم بتشغيل Microsoft 365 cmdlet، مثل **Get-MsolUser**، وشاهد النتائج.
  
إذا تلقيت رسالة خطأ، فتحقق من المشاكل التالية:
  
- **المشكلة الشائعة هي كلمة مرور غير صحيحة**. قم بتشغيل [الخطوة 2](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) مرة أخرى، وولي اهتماما كبيرا لاسم المستخدم وكلمة المرور التي تقوم بإدخالها.
    
- **تتطلب Microsoft Azure Active Directory Module for Windows PowerShell أن Microsoft .NET Framework 3.5.* x* ممكن على الكمبيوتر**. من المحتمل أن يكون لديك إصدار أحدث مثبت على الكمبيوتر (على سبيل المثال، 4 أو 4.5.* x*). ولكن يمكن تمكين التوافق مع الإصدارات السابقة من .NET Framework أو تعطيله. لمزيد من المعلومات، راجع المقالات التالية:
    
  - للحصول على Windows Server 2012 أو Windows Server 2012 R2، راجع [تمكين .NET Framework 3.5 باستخدام معالج إضافة أدوار وميزات](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)).
    
  - للحصول على Windows 7 أو Windows Server 2008 R2، راجع [أنه لا يمكنك فتح وحدة Azure Active Directory النمطية Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - للحصول على Windows 10 و Windows 8.1 و Windows 8، راجع [تثبيت .NET Framework 3.5 على Windows 10، Windows 8.1، Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **قد يكون إصدار الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell قديما.** للتحقق، قم بتشغيل الأمر التالي في PowerShell Microsoft 365 أو الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    إذا كان رقم الإصدار الذي تم إرجاعه أقل من *1.0.8070.2*، فقم بإلغاء تثبيت الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell والتثبيت من [الخطوة 1](#step-1-install-the-required-software) أعلاه.

- **إذا تلقيت رسالة خطأ اتصال**، فراجع [الخطأ "الاتصال-MsolService: تم طرح استثناء من النوع".](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception)
    
- **إذا تلقيت رسالة الخطأ "Get-Item: Cannot find path"**، فشغل هذا الأمر:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>الاتصال مع Azure Cloud Shell

للاتصال باستخدام Azure Cloud Shell واستخدامه من مركز مسؤولي Microsoft 365، حدد أيقونة نافذة PowerShell من الزاوية العلوية اليسرى من شريط المهام. في جزء **Welcome to Azure Cloud Shell** ، حدد **PowerShell**.

ستحتاج إلى اشتراك Azure نشط لمؤسستك مرتبط باشتراكك في Microsoft 365. إذا لم يكن لديك واحد بالفعل، يمكنك إنشاء واحد. بمجرد أن يكون لديك اشتراك Azure، يتم فتح نافذة PowerShell التي يمكنك من خلالها تشغيل أوامر PowerShell والبرامج النصية.

لمزيد من المعلومات، راجع [Azure Cloud Shell](/azure/cloud-shell/overview).


## <a name="get-started-with-the-microsoft-graph-powershell-sdk"></a>بدء استخدام Microsoft Graph PowerShell SDK

يمكنك استخدام Microsoft Graph PowerShell SDK للوصول إلى جميع واجهات برمجة تطبيقات Microsoft Graph.

لمزيد من المعلومات، راجع [بدء استخدام Microsoft Graph PowerShell SDK](/powershell/microsoftgraph/get-started?view=graph-powershell-beta)

## <a name="see-also"></a>راجع أيضًا

- [إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
- [بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [الاتصال بكافة خدمات Microsoft 365 في نافذة Windows PowerShell واحدة](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
