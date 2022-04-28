---
title: تعطيل الوصول إلى خدمات Microsoft 365 باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell لتعطيل الوصول إلى خدمات Microsoft 365 للمستخدمين.
ms.openlocfilehash: 0acd174fce25e0332aa8f927595657e4d0a464b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097701"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>تعطيل الوصول إلى خدمات Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

عند تعيين ترخيص من خطة ترخيص لحساب Microsoft 365، يتم توفير خدمات Microsoft 365 للمستخدم من هذا الترخيص. ومع ذلك، يمكنك التحكم في خدمات Microsoft 365 التي يمكن للمستخدم الوصول إليها. على سبيل المثال، على الرغم من أن الترخيص يسمح بالوصول إلى خدمة SharePoint Online، يمكنك تعطيل الوصول إليها. يمكنك استخدام PowerShell لتعطيل الوصول إلى أي عدد من الخدمات لخطة ترخيص معينة من أجل:

- حساب فردي.
- مجموعة من الحسابات.
- جميع الحسابات في مؤسستك.

>[!Note]
>هناك Microsoft 365 تبعيات الخدمة التي يمكن أن تمنعك من تعطيل خدمة معينة عندما تعتمد الخدمات الأخرى عليها.
>

## <a name="use-the-microsoft-graph-powershell-sdk"></a>استخدام Microsoft Graph PowerShell SDK

أولا، [اتصل بمستأجر Microsoft 365](/graph/powershell/get-started#authentication).

يتطلب تعيين تراخيص لمستخدم وإزالتها نطاق أذونات User.ReadWrite.All أو أحد الأذونات الأخرى المدرجة في [الصفحة المرجعية "تعيين ترخيص" Graph واجهة برمجة التطبيقات](/graph/api/user-assignlicense).

نطاق أذونات Organization.Read.All مطلوب لقراءة التراخيص المتوفرة في المستأجر.

```powershell
Connect-Graph -Scopes User.ReadWrite.All, Organization.Read.All
```

بعد ذلك، استخدم هذا الأمر لعرض خطط الترخيص المتوفرة، والمعروفة أيضا باسم SkuPartNumber:

```powershell
Get-MgSubscribedSku | Select SkuId, SkuPartNumber, ServicePlans | Sort SkuPartNumber
```

لمزيد من المعلومات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).

للاطلاع على النتائج السابقة والسابقة للإجراءات الواردة في هذا الموضوع، راجع [عرض ترخيص الحساب وتفاصيل الخدمة باستخدام PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).

### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>تعطيل خدمات Microsoft 365 معينة لمستخدمين محددين لخطة ترخيص معينة
  
لتعطيل مجموعة معينة من خدمات Microsoft 365 للمستخدمين لخطة ترخيص معينة، نفذ الخطوات التالية:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>الخطوة 1: تحديد الخدمات غير المرغوب فيها في خطة الترخيص باستخدام بناء الجملة التالي:

قم أولا بإدراج خطط الترخيص المتوفرة في المستأجر باستخدام الأمر التالي.

```powershell
Get-MgSubscribedSku | Select SkuPartNumber

SkuPartNumber
-------------
EMSPREMIUM
SPE_E5
RIGHTSMANAGEMENT_ADHOC

```

بعد ذلك، استخدم SkuPartNumber من الأمر أعلاه، وسرد خطط الخدمة المتوفرة لخطة ترخيص معينة (Sku).

يسرد المثال التالي جميع خطط الخدمة المتوفرة **SPE_E5** (Microsoft 365 E5).

```powershell
Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5' |  select -ExpandProperty ServicePlans
```

```text
AppliesTo ProvisioningStatus ServicePlanId                        ServicePlanName
--------- ------------------ -------------                        ---------------
User      Success            b21a6b06-1988-436e-a07b-51ec6d9f52ad PROJECT_O365_P3
User      Success            64bfac92-2b17-4482-b5e5-a0304429de3e MICROSOFTENDPOINTDLP
User      Success            199a5c09-e0ca-4e37-8f7c-b05d533e1ea2 MICROSOFTBOOKINGS
User      Success            6db1f1db-2b46-403f-be40-e39395f08dbb CUSTOMER_KEY
User      Success            4a51bca5-1eff-43f5-878c-177680f191af WHITEBOARD_PLAN3
User      Success            07699545-9485-468e-95b6-2fca3738be01 FLOW_O365_P3
User      Success            9c0dab89-a30c-4117-86e7-97bda240acd2 POWERAPPS_O365_P3
User      Success            e212cbc7-0961-4c40-9825-01117710dcb1 FORMS_PLAN_E5
User      Success            57ff2da0-773e-42df-b2af-ffb7a2317929 TEAMS1
User      Success            21b439ba-a0ca-424f-a6cc-52f954a5b111 WIN10_PRO_ENT_SUB
User      Success            eec0eb4f-6444-4f95-aba0-50c24d67f998 AAD_PREMIUM_P2
User      Success            c1ec4a95-1f05-45b3-a911-aa3fa01094f5 INTUNE_A
User      Success            7547a3fe-08ee-4ccb-b430-5077c5041653 YAMMER_ENTERPRISE
User      Success            a23b959c-7ce8-4e57-9140-b90eb88a9e97 SWAY
User      Success            e95bec33-7c88-4a70-8e19-b10bd9d0c014 SHAREPOINTWAC
User      Success            5dbe027f-2339-4123-9542-606e4d348a72 SHAREPOINTENTERPRISE
User      Success            b737dad2-2f6c-4c65-90e3-ca563267e8b9 PROJECTWORKMANAGEMENT
User      Success            43de0ff5-c92c-492b-9116-175376d08c38 OFFICESUBSCRIPTION
User      Success            0feaeb32-d00e-4d66-bd5a-43b5b83db82c MCOSTANDARD
User      Success            9f431833-0334-42de-a7dc-70aa40db46db LOCKBOX_ENTERPRISE
User      Success            efb87545-963c-4e0d-99df-69c6916d9eb0 EXCHANGE_S_ENTERPRISE
```

للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات)، وخطط الخدمة المضمنة، وأسماءها المألوفة المقابلة، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference). (ابحث باستخدام ServicePlanId للبحث عن الاسم المألوف المقابل لخطة الخدمة).

يعين المثال التالي **SPE_E5** (Microsoft 365 E5) مع إيقاف تشغيل خدمات **MICROSOFTBOOKINGS** (Microsoft Bookings **) LOCKBOX_ENTERPRISE (** مربع تأمين العميل):
  
```powershell
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") | `
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

ستؤدي الخاصية DisabledPlans للمعلمة AddLicenses في Set-MgUserLicense إلى الكتابة فوق قيمة DisabledPlans الموجودة للمستخدم. للمحافظة على حالة خطط الخدمة الموجودة، يجب دمج حالة خطط الخدمة الحالية للمستخدم مع الخطط الجديدة التي سيتم تعطيلها.

سيؤدي فشل تضمين DisabledPlans الموجودة إلى تمكين خطة المستخدم المعطلة مسبقا.

يقوم المثال التالي بتحديث مستخدم **باستخدام SPE_E5** (Microsoft 365 E5) وإيقاف تشغيل خطط خدمة Sway و Forms مع ترك الخطط المعطلة الموجودة للمستخدم في حالته الحالية:
  
```powershell
## Get the services that have already been disabled for the user.
$userLicense = Get-MgUserLicenseDetail -UserId "belinda@fdoau.onmicrosoft.com"
$userDisabledPlans = $userLicense.ServicePlans | `
    Where ProvisioningStatus -eq "Disabled" | `
    Select -ExpandProperty ServicePlanId

## Get the new service plans that are going to be disabled
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$newDisabledPlans = $e5Sku.ServicePlans | `
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") | `
    Select -ExpandProperty ServicePlanId

## Merge the new plans that are to be disabled with the user's current state of disabled plans
$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)
## Update user's license
Set-MgUserLicense -UserId "belinda@litwareinc.onmicrosoft.com" -AddLicenses $addLicenses -RemoveLicenses @()
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

بعد ذلك، استخدم هذا الأمر لعرض خطط الترخيص المتوفرة، والمعروفة أيضا باسم AccountSkuIds:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

لمزيد من المعلومات، راجع [عرض التراخيص والخدمات باستخدام PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md).
    
للاطلاع على النتائج السابقة والسابقة للإجراءات الواردة في هذا الموضوع، راجع [عرض ترخيص الحساب وتفاصيل الخدمة باستخدام PowerShell](view-account-license-and-service-details-with-microsoft-365-powershell.md).
    
يتوفر برنامج نصي PowerShell يقوم بأتمتة الإجراءات الموضحة في هذا الموضوع. على وجه التحديد، يتيح لك البرنامج النصي عرض الخدمات وتعطيلها في مؤسستك Microsoft 365، بما في ذلك Sway. لمزيد من المعلومات، راجع [تعطيل الوصول إلى Sway باستخدام PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>تعطيل خدمات Microsoft 365 معينة لمستخدمين محددين لخطة ترخيص معينة
  
لتعطيل مجموعة معينة من خدمات Microsoft 365 للمستخدمين لخطة ترخيص معينة، نفذ الخطوات التالية:
  
#### <a name="step-1-identify-the-undesired-services-in-the-licensing-plan-by-using-the-following-syntax"></a>الخطوة 1: تحديد الخدمات غير المرغوب فيها في خطة الترخيص باستخدام بناء الجملة التالي:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesiredService1>", "<UndesiredService2>"...
```

ينشئ المثال التالي كائن **LicenseOptions** الذي يعطل Office والخدمات SharePoint Online في خطة الترخيص المسماة `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>الخطوة 2: استخدم كائن **LicenseOptions** من الخطوة 1 على مستخدم واحد أو أكثر.
    
لإنشاء حساب جديد تم تعطيل الخدمات فيه، استخدم بناء الجملة التالي:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

ينشئ المثال التالي حسابا جديدا ل "ألي بيلو" الذي يعين الترخيص ويعطل الخدمات الموضحة في الخطوة 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

لمزيد من المعلومات حول إنشاء حسابات المستخدمين في PowerShell Microsoft 365، راجع [إنشاء حسابات المستخدمين باستخدام PowerShell](create-user-accounts-with-microsoft-365-powershell.md).
    
لتعطيل الخدمات لمستخدم مرخص موجود، استخدم بناء الجملة التالي:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

يقوم هذا المثال بتعطيل خدمات المستخدم BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

لتعطيل الخدمات الموضحة في الخطوة 1 لجميع المستخدمين المرخصين الحاليين، حدد اسم خطة Microsoft 365 من عرض **Get-MsolAccountSku** cmdlet (مثل **litwareinc:ENTERPRISEPACK**)، ثم قم بتشغيل الأوامر التالية:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 إذا كنت تستخدم **Get-MsolUser** cmdlet دون استخدام المعلمة _All_ ، يتم إرجاع أول 500 حساب مستخدم فقط.

لتعطيل الخدمات لمجموعة من المستخدمين الموجودين، استخدم أيا من الأساليب التالية لتحديد المستخدمين:
    
**الأسلوب 1. تصفية الحسابات استنادا إلى سمة حساب موجودة** 

للقيام بذلك، استخدم بناء الجملة التالي:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

المثال التالي يعطل الخدمات للمستخدمين في قسم المبيعات في الولايات المتحدة.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**الطريقة 2: استخدام قائمة بحسابات معينة** 

للقيام بذلك، نفذ الخطوات التالية:
    
1. إنشاء ملف نصي يحتوي على حساب واحد على كل سطر على النحو التالي:
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   في هذا المثال، الملف النصي هو C:\\My Documents\\Accounts.txt.
    
2. قم بتنفيذ الأمر التالي:
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

إذا كنت تريد تعطيل الوصول إلى الخدمات لخطط ترخيص متعددة، فكرر الإرشادات أعلاه لكل خطة ترخيص، مع ضمان ما يلي:

- تم تعيين خطة الترخيص لحسابات المستخدمين.
- تتوفر الخدمات التي يجب تعطيلها في خطة الترخيص.

لتعطيل خدمات Microsoft 365 للمستخدمين أثناء تعيينهم لخطة ترخيص، راجع [تعطيل الوصول إلى الخدمات أثناء تعيين تراخيص المستخدمين](disable-access-to-services-while-assigning-user-licenses.md).

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a>تعيين كافة الخدمات في خطة ترخيص إلى حساب مستخدم

بالنسبة لحسابات المستخدمين التي لديها خدمات معطلة، يمكنك تمكين جميع الخدمات لخطة ترخيص معينة باستخدام هذه الأوامر:

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="related-topic"></a>الموضوع ذو الصلة

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
