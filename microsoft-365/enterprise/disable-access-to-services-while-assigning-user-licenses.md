---
title: تعطيل الوصول إلى خدمات Microsoft 365 أثناء تعيين تراخيص المستخدمين
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/24/2020
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: تعرف على كيفية تعيين تراخيص لحسابات المستخدمين وتعطيل خطط خدمة معينة في الوقت نفسه باستخدام PowerShell Microsoft 365.
ms.openlocfilehash: 6c0c3a3860da8a1935152fcaefb29f2f355cfa49
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095719"
---
# <a name="disable-access-to-microsoft-365-services-while-assigning-user-licenses"></a>تعطيل الوصول إلى خدمات Microsoft 365 أثناء تعيين تراخيص المستخدمين

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

تأتي Microsoft 365 الاشتراكات مع خطط الخدمة للخدمات الفردية. غالبا ما يحتاج المسؤولون Microsoft 365 إلى تعطيل خطط معينة عند تعيين تراخيص للمستخدمين. باستخدام الإرشادات الواردة في هذه المقالة، يمكنك تعيين ترخيص Microsoft 365 أثناء تعطيل خطط خدمة معينة باستخدام PowerShell لحساب مستخدم فردي أو حسابات مستخدمين متعددة.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).


بعد ذلك، قم بإدراج خطط الترخيص للمستأجر باستخدام هذا الأمر.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

بعد ذلك، احصل على اسم تسجيل الدخول للحساب الذي تريد إضافة ترخيص إليه، والمعروف أيضا باسم المستخدم الأساسي (UPN).

بعد ذلك، قم بتجميع قائمة من الخدمات لتمكينها. للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات)، وخطط الخدمة المضمنة، وأسماءها المألوفة المقابلة، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

بالنسبة إلى كتلة الأوامر أدناه، املأ اسم المستخدم الأساسي لحساب المستخدم ورقم جزء SKU وقائمة خطط الخدمة لتمكين النص التوضيحي والأحرف \< and > وإزالتها. ثم قم بتشغيل الأوامر الناتجة في موجه الأوامر PowerShell.

```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

بعد ذلك، قم بتشغيل هذا الأمر لمشاهدة اشتراكاتك الحالية:

```powershell
Get-MsolAccountSku
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets مع **Msol** باسمها. لمتابعة استخدام أوامر cmdlets هذه، يجب تشغيلها من Windows PowerShell.
>

في عرض  `Get-MsolAccountSku` الأمر:

- **AccountSkuId** هو اشتراك لمؤسستك بتنسيق \<OrganizationName>:\<Subscription> القيمة \<OrganizationName> التي قدمتها عند التسجيل في Microsoft 365، وهي فريدة لمؤسستك. \<Subscription> القيمة هي لاشتراك معين. على سبيل المثال، بالنسبة إلى litwareinc:ENTERPRISEPACK، يكون اسم المؤسسة litwareinc، واسم الاشتراك هو ENTERPRISEPACK (Office 365 Enterprise E3).

- **ActiveUnits** هو عدد التراخيص التي اشتريتها للاشتراك.

- **WarningUnits** هو عدد التراخيص في اشتراك لم تقم بتجديده، وستنتهي صلاحيته بعد فترة السماح التي تبلغ 30 يوما.

- **«وحدات المستهلكة** » هي عدد التراخيص التي قمت بتعيينها للمستخدمين للاشتراك.

لاحظ AccountSkuId لاشتراكك Microsoft 365 الذي يحتوي على المستخدمين الذين تريد ترخيصهم. تأكد أيضا من وجود تراخيص كافية لتعيينها (طرح **وحدات استهلاكية** من **ActiveUnits**).

بعد ذلك، قم بتشغيل هذا الأمر للاطلاع على التفاصيل حول خطط خدمة Microsoft 365 المتوفرة في جميع اشتراكاتك:

```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

من عرض هذا الأمر، حدد خطط الخدمة التي تريد تعطيلها عند تعيين تراخيص للمستخدمين.

فيما يلي قائمة جزئية بخطط الخدمة وخدماتها Microsoft 365 المقابلة.

يعرض الجدول التالي خطط خدمة Microsoft 365 وأسماءها المألوفة للخدمات الأكثر شيوعا. قد تكون قائمة خطط الخدمة الخاصة بك مختلفة.

|**خطة الخدمة**|**الوصف**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 Apps for enterprise *(المسمى سابقا Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online الخطة 2  <br/> |

للحصول على قائمة كاملة بخطط الترخيص (المعروفة أيضا باسم أسماء المنتجات)، وخطط الخدمة المضمنة، وأسماءها المألوفة المقابلة، راجع [أسماء المنتجات ومعرفات خطة الخدمة للترخيص](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

الآن بعد أن أصبح لديك AccountSkuId وخطط الخدمة لتعطيلها، يمكنك تعيين تراخيص لمستخدم فردي أو لعدة مستخدمين.

### <a name="for-a-single-user"></a>لمستخدم واحد

بالنسبة لمستخدم واحد، قم بتعبئة اسم المستخدم الأساسي لحساب المستخدم و AccountSkuId وقائمة خطط الخدمة لتعطيل النص التوضيحي والأحرف \< and > وإزالتها. ثم قم بتشغيل الأوامر الناتجة في موجه الأوامر PowerShell.

```powershell
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

فيما يلي مثال على كتلة أوامر للحساب المسمى belindan@contoso.com، لترخيص contoso:ENTERPRISEPACK، وخطط الخدمة التي يجب تعطيلها هي RMS_S_ENTERPRISE وSWAY INTUNE_O365 YAMMER_ENTERPRISE:

```powershell
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
```

### <a name="for-multiple-users"></a>لمستخدمين متعددين

لتنفيذ مهمة الإدارة هذه لعدة مستخدمين، أنشئ ملفا نصيا مفصولا بفواصل (CSV) يحتوي على الحقلين UserPrincipalName وUserageLocation. فيما يلي مثال على ذلك:

```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

بعد ذلك، املأ موقع ملفات CSV للإدخال والإخراج، ومعرف SKU للحساب، وقائمة خطط الخدمة لتعطيلها، ثم قم بتشغيل الأوامر الناتجة في موجه أوامر PowerShell.

```powershell
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

كتلة أوامر PowerShell هذه:

- عرض اسم المستخدم الأساسي لكل مستخدم.

- تعيين تراخيص مخصصة لكل مستخدم.

- إنشاء ملف CSV مع جميع المستخدمين الذين تمت معالجتها ويعرض حالة الترخيص الخاصة بهم.

## <a name="see-also"></a>راجع أيضًا

[تعطيل الوصول إلى خدمات Microsoft 365 باستخدام PowerShell](disable-access-to-services-with-microsoft-365-powershell.md)

[تعطيل الوصول إلى Sway باستخدام PowerShell](disable-access-to-sway-with-microsoft-365-powershell.md)

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)