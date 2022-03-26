---
title: تكوين خصائص Microsoft 365 المستخدم باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
- admindeeplinkMAC
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: استخدم PowerShell Microsoft 365 لتكوين خصائص حسابات المستخدمين الفردية أو حسابات المستخدمين المتعددة في Microsoft 365 المستأجر.
ms.openlocfilehash: 01b17837e4babc31d385be66f9387129baf87da1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569560"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>تكوين خصائص Microsoft 365 المستخدم باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365 لتكوين خصائص</a> حسابات المستخدمين الخاصة Microsoft 365 المستأجر. في PowerShell، يمكنك أيضا القيام بذلك، بالإضافة إلى بعض الأمور الأخرى التي لا يمكنك القيام بها في مركز الإدارة.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

لتكوين خصائص حسابات المستخدمين في وحدة Azure Active Directory PowerShell النمطية ل Graph، استخدم الأمر [**cmdlet Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) وحدد الخصائص لتعيينها أو تغييرها.

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>تغيير خصائص حساب مستخدم معين

يمكنك تحديد الحساب باستخدام *المعلمة ObjectID* ، كما يمكنك تعيين خصائص معينة أو تغييرها باستخدام معلمات إضافية. فيما يلي قائمة بالمعلمات الأكثر شيوعا:
  
- -Department "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Surname "\<user last name>"

- -Mobile "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- -City "\<city name>"

- -State "\<state name>"

- -الرمز البريدي "\<postal code>"

- -Country "\<country name>"

- -TelephoneNumber "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    هذا هو رمز البلد أو المنطقة من حرفين ل ISO 3166-1 alpha-2 (A2).

للحصول على معلمات إضافية، راجع [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> قبل أن تتمكن من تعيين تراخيص لحساب مستخدم، يجب تعيين موقع استخدام.

لعرض اسم المستخدم الأساسي حسابات المستخدمين، اعرض الأمر التالي.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات في حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).

1. فرز قائمة أسماء المستخدمين الأساسية أبجديا (فرز **UserPrincipalName**) وإرسالها إلى الأمر التالي (**|**).

1. عرض الخاصية اسم المستخدم الأساسي فقط لكل حساب (**حدد UserPrincipalName**).

1. عرضها شاشة واحدة في كل مرة (**المزيد**).

لعرض اسم المستخدم الأساسي لحساب استنادا إلى اسم العرض الخاص به (الاسم الأول واسم العائلة)، تشغيل الأوامر التالية. قم *بتعبئة $userName* المتغير، وأزل الأحرف \< and > :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

يعرض هذا المثال اسم المستخدم الأساسي لحساب المستخدم الذي لديه اسم العرض *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

باستخدام متغير *$upn* ، يمكنك إجراء تغييرات على الحسابات الفردية استنادا إلى اسم العرض الخاص بها. فيما يلي مثال على تعيين موقع استخدام *Belinda Newman* إلى فرنسا. ولكنه يحدد اسم العرض الخاص بها بدلا من اسم المستخدم الأساسي الخاص بها:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>تغيير الخصائص لكل حسابات المستخدمين

لتغيير خصائص جميع المستخدمين، يمكنك استخدام مجموعة من **الأمرين Cmdlets Get-AzureADUser** و **Set-AzureADUser** . يغير المثال التالي موقع الاستخدام لكل المستخدمين في *فرنسا*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات في حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>تغيير خصائص مجموعة معينة من حسابات المستخدمين

لتغيير خصائص مجموعة معينة من حسابات المستخدمين، يمكنك استخدام مجموعة من **الأمرين Get-AzureADUser** و Where و **Set-AzureADUser** cmdlets.  يغير المثال التالي موقع الاستخدام لكل المستخدمين في قسم المحاسبة إلى *فرنسا*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات في حسابات المستخدمين (**Get-AzureADUser**)، وأرسلها إلى الأمر التالي (**|**).

1.  ابحث عن كل حسابات المستخدمين التي تم تعيين خاصية *"القسم* " الخاصة بها إلى "المحاسبة" (**حيث {$_. القسم -eq "Accounting"}**)، وأرسل المعلومات الناتجة إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

لتكوين خصائص حسابات المستخدمين باستخدام وحدة Microsoft Azure Active Directory النمطية Windows PowerShell، استخدم الأمر **cmdlet Set-MsolUser** وحدد الخصائص لتعيينها أو تغييرها.

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. تشغيل cmdlets هذه من Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>تغيير خصائص حساب مستخدم معين

لتكوين خصائص لحساب مستخدم معين، استخدم [**الأمر Cmdlet Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) وحدد الخصائص التي تريد تعيينها أو تغييرها. 

يمكنك تحديد الحساب باستخدام *المعلمة -UserPrincipalName* وتحديد خصائص معينة أو تغييرها باستخدام معلمات إضافية. إليك قائمة بالمعلمات الأكثر شيوعا.
  
- -City "\<city name>"

- -Country "\<country name>"

- -Department "\<department name>"

- -DisplayName "\<full user name>"

- -فاكس "\<fax number>"

- -FirstName "\<user first name>"

- -LastName "\<user last name>"

- -MobilePhone "\<mobile phone number>"

- -Office "\<office location>"

- -PhoneNumber "\<office phone number>"

- -الرمز البريدي "\<postal code>"

- -PreferredLanguage "\<language>"

- -State "\<state name>"

- -StreetAddress "\<street address>"

- -Title "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    هذا هو رمز البلد أو المنطقة من حرفين ل ISO 3166-1 alpha-2 (A2).

للحصول على معلمات إضافية، راجع [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

لرؤية أسماء المستخدمين الأساسية لجميع المستخدمين، تشغيل الأمر التالي:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات الخاصة وحسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).

1. فرز قائمة أسماء المستخدمين الأساسية أبجديا (فرز **UserPrincipalName**) وإرسالها إلى الأمر التالي (**|**).

1. عرض الخاصية اسم المستخدم الأساسي فقط لكل حساب (**حدد UserPrincipalName**).

1. عرضها شاشة واحدة في كل مرة (**المزيد**).

لعرض اسم المستخدم الأساسي لحساب استنادا إلى اسم العرض الخاص به (الاسم الأول واسم العائلة)، تشغيل الأوامر التالية. قم *بتعبئة $userName* المتغير، وأزل الأحرف \< and > .
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

يعرض هذا المثال اسم المستخدم الأساسي للمستخدم المسمى Caleb Sills:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

باستخدام متغير *$upn* ، يمكنك إجراء تغييرات على الحسابات الفردية استنادا إلى اسم العرض الخاص بها. فيما يلي مثال يقوم بتعيين موقع استخدام *Belinda Newman* إلى *فرنسا*، ولكنه يحدد اسم العرض الخاص بها بدلا من اسم المستخدم الأساسي الخاص بها:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>تغيير الخصائص لكل حسابات المستخدمين

لتغيير خصائص جميع المستخدمين، استخدم تركيبة من **الأمرين Cmdlets Get-MsolUser** و **Set-MsolUser** . يغير المثال التالي موقع الاستخدام لكل المستخدمين في *فرنسا*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات الخاصة وحسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>تغيير خصائص مجموعة معينة من حسابات المستخدمين

لتغيير خصائص مجموعة معينة من حسابات المستخدمين، يمكنك استخدام مجموعة من **الأمرين Cmdlets Get-MsolUser** و Where و **Set-MsolUser**.  يغير المثال التالي موقع الاستخدام لكل المستخدمين في قسم المحاسبة إلى *فرنسا*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات الخاصة وحسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).

1. ابحث عن كل حسابات المستخدمين التي تم تعيين خاصية *"القسم* " الخاصة بها إلى "المحاسبة" (**حيث {$_. القسم -eq "Accounting"}**) وأرسل المعلومات الناتجة إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
