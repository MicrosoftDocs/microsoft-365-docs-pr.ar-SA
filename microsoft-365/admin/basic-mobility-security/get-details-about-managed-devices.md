---
title: الحصول على تفاصيل حول الأجهزة المدارة الأساسية للتنقل والأمان
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: استخدم Azure AD PowerShell للحصول على تفاصيل حول الأجهزة الأساسية للتنقل والأمان في مؤسستك.
ms.openlocfilehash: 816d397f29d6e1726448d92e641856f2a5a31a73
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66007185"
---
# <a name="get-details-about-basic-mobility-and-security-managed-devices"></a>الحصول على تفاصيل حول الأجهزة المدارة الأساسية للتنقل والأمان

توضح لك هذه المقالة كيفية استخدام Azure AD PowerShell للحصول على تفاصيل حول الأجهزة في مؤسستك التي قمت بإعدادها ل Basic Mobility and Security.

فيما يلي تصنيف تفصيلي لتفاصيل الجهاز المتوفرة لك.

|التفاصيل|ما الذي يجب البحث عنه في PowerShell|
|---|---|
|يتم تسجيل الجهاز في Basic Mobility and Security. لمزيد من المعلومات، راجع [تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md)|قيمة المعلمة *isManaged* هي:<br/>**تم تسجيل صواب**= جهاز.<br/>**الجهاز False**= غير مسجل.|
|الجهاز متوافق مع نهج أمان جهازك. لمزيد من المعلومات، راجع [إنشاء نهج أمان الجهاز](create-device-security-policies.md)|قيمة المعلمة *isCompliant* هي:<br/>**True** = الجهاز متوافق مع النهج.<br/>**False** = الجهاز غير متوافق مع النهج.|

:::image type="content" source="../../media/basic-mobility-security/bms-7-powershell-parameters.png" alt-text="معلمات PowerShell الأساسية للتنقل والأمان.":::

> [!NOTE]
> تقوم الأوامر والبرامج النصية في هذه المقالة أيضا بإرجاع تفاصيل حول أي أجهزة تديرها [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).

## <a name="before-you-begin"></a>قبل البدء

هناك بعض الأشياء التي تحتاج إلى إعدادها لتشغيل الأوامر والبرامج النصية الموضحة في هذه المقالة.

### <a name="step-1-download-and-install-the-azure-active-directory-module-for-windows-powershell"></a>الخطوة 1: تنزيل وتثبيت وحدة Azure Active Directory النمطية Windows PowerShell

لمزيد من المعلومات حول هذه الخطوات، راجع [الاتصال Microsoft 365 باستخدام PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell).

1. انتقل إلى [Microsoft Online Services Sign-In Assistant لمحترفي تكنولوجيا المعلومات RTWl](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi) وحدد **"تنزيل لمساعد تسجيل الدخول إلى Microsoft Online Services**".

2. تثبيت الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell باستخدام الخطوات التالية:

    1. افتح موجه أوامر PowerShell على مستوى المسؤول.

    2. `Install-Module MSOnline` تشغيل الأمر.

    3. إذا تمت مطالبتك بتثبيت موفر NuGet، فاكتب Y واضغط على ENTER.

    4. إذا تمت مطالبتك بتثبيت الوحدة النمطية من PSGallery، فاكتب Y واضغط على ENTER.

    5. بعد التثبيت، أغلق نافذة أمر PowerShell.

### <a name="step-2-connect-to-your-microsoft-365-subscription"></a>الخطوة 2: الاتصال إلى اشتراكك في Microsoft 365

1. في Windows Azure Active Directory Module for Windows PowerShell، قم بتشغيل الأمر التالي.

   ```powershell
   $UserCredential = Get-Credential
   ```

2. في مربع الحوار "طلب بيانات الاعتماد" Windows PowerShell، اكتب اسم المستخدم وكلمة المرور لحساب المسؤول العمومي Microsoft 365، ثم حدد **"موافق**".

3. قم بتشغيل الأمر التالي.

   ```powershell
   Connect-MsolService -Credential $UserCredential
   ```

### <a name="step-3-make-sure-youre-able-to-run-powershell-scripts"></a>الخطوة 3: تأكد من قدرتك على تشغيل البرامج النصية PowerShell

> [!NOTE]
> يمكنك تخطي هذه الخطوة إذا كنت قد أعددت بالفعل لتشغيل البرامج النصية PowerShell.

لتشغيل البرنامج النصي Get-MsolUserDeviceComplianceStatus.ps1، تحتاج إلى تمكين تشغيل البرامج النصية PowerShell.

1. من Windows Desktop، حدد **"ابدأ**"، ثم اكتب Windows PowerShell. انقر بزر الماوس الأيمن فوق Windows PowerShell، ثم حدد **"تشغيل كمسؤول**".

2. قم بتشغيل الأمر التالي.

   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

3. عند المطالبة، اكتب Y ثم اضغط على مفتاح الإدخال Enter.

#### <a name="run-the-get-msoldevice-cmdlet-to-display-details-for-all-devices-in-your-organization"></a>تشغيل Get-MsolDevice cmdlet لعرض تفاصيل جميع الأجهزة في مؤسستك

1. افتح الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell.

2. قم بتشغيل الأمر التالي.

   ```powershell
   Get-MsolDevice -All -ReturnRegisteredOwners | Where-Object {$_.RegisteredOwners.Count -gt 0}
   ```

لمزيد من الأمثلة، راجع [Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939).

## <a name="run-a-script-to-get-device-details"></a>تشغيل برنامج نصي للحصول على تفاصيل الجهاز

أولا، احفظ البرنامج النصي على الكمبيوتر الخاص بك.

1. انسخ النص التالي والصقه في المفكرة.

   ```powershell
   param (
   [PSObject[]]$users = @(),
   [Switch]$export,
   [String]$exportFileName = "UserDeviceComplianceStatus_" + (Get-Date -Format "yyMMdd_HHMMss") + ".csv",
   [String]$exportPath = [Environment]::GetFolderPath("Desktop")
   )
   [System.Collections.IDictionary]$script:schema = @{
   DeviceId = ''
   DeviceOSType = ''
   DeviceOSVersion = ''
   DeviceTrustLevel = ''
   DisplayName = ''
   IsCompliant = ''
   IsManaged = ''
   ApproximateLastLogonTimestamp = ''
   DeviceObjectId = ''
   RegisteredOwnerUpn = ''
   RegisteredOwnerObjectId = ''
   RegisteredOwnerDisplayName = ''
   }
   function createResultObject
   {
   [PSObject]$resultObject = New-Object -TypeName PSObject -Property $script:schema
   return $resultObject
   }
   If ($users.Count -eq 0)
   {
   $users = Get-MsolUser
   }
   [PSObject[]]$result = foreach ($u in $users)
   {
   [PSObject]$devices = get-msoldevice -RegisteredOwnerUpn $u.UserPrincipalName
   foreach ($d in $devices)
   {
   [PSObject]$deviceResult = createResultObject
   $deviceResult.DeviceId = $d.DeviceId
   $deviceResult.DeviceOSType = $d.DeviceOSType
   $deviceResult.DeviceOSVersion = $d.DeviceOSVersion
   $deviceResult.DeviceTrustLevel = $d.DeviceTrustLevel
   $deviceResult.DisplayName = $d.DisplayName
   $deviceResult.IsCompliant = $d.GraphDeviceObject.IsCompliant
   $deviceResult.IsManaged = $d.GraphDeviceObject.IsManaged
   $deviceResult.DeviceObjectId = $d.ObjectId
   $deviceResult.RegisteredOwnerUpn = $u.UserPrincipalName
   $deviceResult.RegisteredOwnerObjectId = $u.ObjectId
   $deviceResult.RegisteredOwnerDisplayName = $u.DisplayName
   $deviceResult.ApproximateLastLogonTimestamp = $d.ApproximateLastLogonTimestamp
   $deviceResult
   }
   }
   If ($export)
   {
   $result | Export-Csv -path ($exportPath + "\" + $exportFileName) -NoTypeInformation
   }
   Else
   {
   $result
   }
   ```

2. احفظه كملف برنامج نصي Windows PowerShell باستخدام .ps1 ملحق الملف؛ على سبيل المثال، Get-MsolUserDeviceComplianceStatus.ps1.

## <a name="run-the-script-to-get-device-information-for-a-single-user-account"></a>تشغيل البرنامج النصي للحصول على معلومات الجهاز لحساب مستخدم واحد

1. افتح الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell.

2. انتقل إلى المجلد حيث حفظت البرنامج النصي. على سبيل المثال، إذا قمت بحفظه في C:\PS-Scripts، فشغل الأمر التالي.

   ```powershell
   cd C:\PS-Scripts
   ```

3. قم بتشغيل الأمر التالي لتحديد المستخدم الذي تريد الحصول على تفاصيل الجهاز له. يحصل هذا المثال على تفاصيل bar@example.com.

   ```powershell
   $u = Get-MsolUser -UserPrincipalName bar@example.com
   ```

4. تشغيل الأمر التالي لبدء البرنامج النصي.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

يتم تصدير المعلومات إلى سطح المكتب Windows كملف CSV. يمكنك استخدام معلمات إضافية لتحديد اسم الملف ومسار CSV.

## <a name="run-the-script-to-get-device-information-for-a-group-of-users"></a>تشغيل البرنامج النصي للحصول على معلومات الجهاز لمجموعة من المستخدمين

1. افتح الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell.

2. انتقل إلى المجلد حيث حفظت البرنامج النصي. على سبيل المثال، إذا قمت بحفظه في C:\PS-Scripts، فشغل الأمر التالي.

   ```powershell
   cd C:\PS-Scripts
   ```

3. قم بتشغيل الأمر التالي لتحديد المجموعة التي تريد الحصول على تفاصيل الجهاز لها. يحصل هذا المثال على تفاصيل للمستخدمين في مجموعة FinanceStaff.

   ```powershell
   $u = Get-MsolGroupMember -SearchString "FinanceStaff" | % { Get-MsolUser -ObjectId $_.ObjectId }
   ```

4. تشغيل الأمر التالي لبدء البرنامج النصي.

   ```powershell
   .\Get-MsolUserDeviceComplianceStatus.ps1 -User $u -Export
   ```

يتم تصدير المعلومات إلى سطح المكتب Windows كملف CSV. يمكنك استخدام معلمات إضافية لتحديد اسم الملف ومسار CSV.

## <a name="related-topics"></a>المواضيع ذات الصلة

[تم إيقاف Microsoft الاتصال](/collaborate/connect-redirect)

[نظرة عامة على التنقل والأمان الأساسيين](overview.md)

[Get-MsolDevice](https://go.microsoft.com/fwlink/?linkid=2157939)
