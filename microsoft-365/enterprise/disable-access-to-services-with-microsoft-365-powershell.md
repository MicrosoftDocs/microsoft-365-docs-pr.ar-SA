---
title: تعطيل الوصول إلى Microsoft 365 PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- seo-marvel-apr2020
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell لتعطيل الوصول إلى Microsoft 365 للمستخدمين.
ms.openlocfilehash: bce02c40bf6ca99d74b8747fb0c5eb5c0b485888
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572836"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>تعطيل الوصول إلى Microsoft 365 PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

عندما يتم Microsoft 365 ترخيص من خطة ترخيص، Microsoft 365 الخدمات المتوفرة للمستخدم من هذا الترخيص. ومع ذلك، يمكنك التحكم في Microsoft 365 التي يمكن للمستخدم الوصول إليها. على سبيل المثال، على الرغم من أن الترخيص يسمح بالوصول إلى SharePoint عبر الإنترنت، إلا أنه يمكنك تعطيل الوصول إليها. يمكنك استخدام PowerShell لتعطيل الوصول إلى أي عدد من الخدمات لخطة ترخيص معينة من أجل:

- حساب فردي.
- مجموعة من الحسابات.
- كل الحسابات في مؤسستك.

>[!Note]
>هناك Microsoft 365 تبعيات الخدمة التي قد تمنعك من تعطيل خدمة معينة عندما تعتمد عليها خدمات أخرى.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

بعد ذلك، استخدم هذا الأمر لعرض خطط الترخيص المتوفرة، المعروفة أيضا ب AccountSkuIds:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع **Msol** في اسمها. لمواصلة استخدام هذه cmdlets، يجب تشغيلها من Windows PowerShell.
>

لمزيد من المعلومات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
لعرض نتائج الإجراءات في هذا الموضوع قبل الإجراءات وما بعدها، راجع عرض تفاصيل ترخيص الحساب والخدمة [باستخدام PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
يتوفر برنامج PowerShell النصي الذي يأتمتة الإجراءات الموضحة في هذا الموضوع. وبشكل خاص، يتيح لك البرنامج النصي عرض الخدمات وتعطيلها في Microsoft 365، بما في ذلك Sway. لمزيد من المعلومات، راجع [تعطيل الوصول إلى Sway باستخدام PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>تعطيل خدمات Microsoft 365 معينة لمستخدمين محددين لخطة ترخيص معينة
  
لتعطيل مجموعة معينة من Microsoft 365 للمستخدمين لخطة ترخيص معينة، قم بتنفيذ الخطوات التالية:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>الخطوة 1: تحديد الخدمات غير المشتتة في خطة الترخيص باستخدام بناء الجملة التالي:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

ينشئ المثال التالي كائن **LicenseOptions** الذي يقوم بتعطيل Office و SharePoint Online `litwareinc:ENTERPRISEPACK` في خطة الترخيص المسماة (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>الخطوة 2: استخدم الكائن **LicenseOptions** من الخطوة 1 على مستخدم واحد أو أكثر.
    
لإنشاء حساب جديد تم تعطيل الخدمات فيه، استخدم بناء الجملة التالي:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

ينشئ المثال التالي حسابا جديدا ل Allie Bellew يعين الترخيص ويعطل الخدمات الموضحة في الخطوة 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

لمزيد من المعلومات حول إنشاء حسابات المستخدمين في PowerShell Microsoft 365، راجع إنشاء حسابات [المستخدمين باستخدام PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
لتعطيل الخدمات لمستخدم مرخص موجود، استخدم بناء الجملة التالي:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

يقوم هذا المثال بتعطيل الخدمات الخاصة BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

لتعطيل الخدمات الموضحة في الخطوة 1 لجميع المستخدمين المرخصين، حدد اسم خطة Microsoft 365 من عرض أمر **cmdlet Get-MsolAccountSku** (مثل **litwareinc:ENTERPRISEPACK**)، ثم قم بتشغيل الأوامر التالية:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 إذا كنت تستخدم **الأمر Cmdlet Get-MsolUser** بدون استخدام المعلمة _All_ ، يتم إرجاع أول 500 حساب مستخدم فقط.

لتعطيل الخدمات لمجموعة من المستخدمين  الموجودين، استخدم أي من الأساليب التالية لتعريف المستخدمين:
    
**الطريقة 1. تصفية الحسابات استنادا إلى سمة حساب موجودة** 

للقيام بذلك، استخدم بناء الجملة التالي:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

يقوم المثال التالي بتعطيل الخدمات للمستخدمين في قسم المبيعات في الولايات المتحدة.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**الطريقة 2: استخدام قائمة حسابات معينة** 

للقيام بذلك، تنفيذ الخطوات التالية:
    
1. إنشاء ملف نصي يحتوي على حساب واحد على كل سطر على هذا النوع:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   في هذا المثال، الملف النصي هو C:\\مستنداتي\\Accounts.txt.
    
2. قم بتنفيذ الأمر التالي:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

إذا كنت تريد تعطيل الوصول إلى الخدمات لخطط ترخيص متعددة، كرر الإرشادات أعلاه لكل خطة ترخيص، مع ضمان ما يلي:

- تم تعيين خطة الترخيص إلى حسابات المستخدمين.
- تتوفر الخدمات التي يجب تعطيلها في خطة الترخيص.

لتعطيل Microsoft 365 للمستخدمين أثناء تعيينهم إلى خطة ترخيص، راجع تعطيل الوصول إلى الخدمات أثناء تعيين [تراخيص المستخدمين](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>تعيين كل الخدمات في خطة ترخيص إلى حساب مستخدم

بالنسبة إلى حسابات المستخدمين التي تم تعطيل خدماتها، يمكنك تمكين كل الخدمات لخطة ترخيص معينة باستخدام هذه الأوامر:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>موضوع ذو صلة

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
