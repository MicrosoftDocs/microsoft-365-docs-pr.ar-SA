---
title: تكوين خصائص حساب المستخدم Microsoft 365 باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: استخدم PowerShell Microsoft 365 لتكوين خصائص حسابات المستخدمين الفردية أو المتعددة في مستأجر Microsoft 365.
ms.openlocfilehash: 3a1aa77a6af3995d7cd4d072b6b6c6047bf89942
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091336"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>تكوين خصائص حساب المستخدم Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> لتكوين خصائص لحسابات المستخدمين لمستأجر Microsoft 365 الخاص بك. في PowerShell، يمكنك أيضا القيام بذلك، بالإضافة إلى بعض الأشياء الأخرى التي لا يمكنك القيام بها في مركز الإدارة.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

لتكوين خصائص لحسابات المستخدمين في Azure Active Directory PowerShell للوحدة النمطية Graph، استخدم [**Set-AzureADUser**](/powershell/module/azuread/set-azureaduser) cmdlet وحدد الخصائص لتعيينها أو تغييرها.

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="change-properties-for-a-specific-user-account"></a>تغيير خصائص حساب مستخدم معين

يمكنك تحديد الحساب باستخدام المعلمة *-ObjectID* وتعيين خصائص معينة أو تغييرها باستخدام معلمات إضافية. فيما يلي قائمة بالمعلمات الأكثر شيوعا:
  
- -القسم "\<department name>"

- -DisplayName "\<full user name>"

- -FacsimilieTelephoneNumber "\<fax number>"

- -GivenName "\<user first name>"

- -Surname "\<user last name>"

- -Mobile "\<mobile phone number>"

- -JobTitle "\<job title>"

- -PreferredLanguage "\<language>"

- -StreetAddress "\<street address>"

- -المدينة "\<city name>"

- -State "\<state name>"

- -الرمز البريدي "\<postal code>"

- -البلد "\<country name>"

- -رقم الهاتف "\<office phone number>"

- -UsageLocation "\<2-character country or region code>"

    هذا هو رمز البلد أو المنطقة ISO 3166-1 alpha-2 (A2) المكون من حرفين.

للحصول على معلمات إضافية، راجع [Set-AzureADUser](/powershell/module/azuread/set-azureaduser).

> [!NOTE]
> قبل أن تتمكن من تعيين تراخيص لحساب مستخدم، يجب تعيين موقع استخدام.

لعرض اسم المستخدم الأساسي لحسابات المستخدمين، قم بتشغيل الأمر التالي.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات على حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).

1. فرز قائمة أسماء المستخدمين الأساسيين أبجديا (**فرز UserPrincipalName**) وإرسالها إلى الأمر التالي (**|**).

1. عرض خاصية اسم المستخدم الأساسي فقط لكل حساب (**حدد UserPrincipalName**).

1. اعرضها على شاشة واحدة في كل مرة (**المزيد**).

لعرض اسم المستخدم الأساسي لحساب استنادا إلى اسم العرض الخاص به (الاسم الأول واسم العائلة)، قم بتشغيل الأوامر التالية. املأ المتغير *$userName* ، وأزل الأحرف \< and > :
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

يعرض هذا المثال اسم المستخدم الأساسي لحساب المستخدم الذي يحتوي على اسم العرض *Caleb Sills*.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

باستخدام متغير *$upn* ، يمكنك إجراء تغييرات على الحسابات الفردية استنادا إلى اسم العرض الخاص بها. فيما يلي مثال يعين موقع استخدام *بيبيها نيومان* إلى فرنسا. ولكنه يحدد اسم العرض بدلا من اسم المستخدم الأساسي الخاص بها:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>تغيير الخصائص لكافة حسابات المستخدمين

لتغيير الخصائص لجميع المستخدمين، يمكنك استخدام مزيج من **Get-AzureADUser** و **Set-AzureADUser** cmdlets. يغير المثال التالي موقع الاستخدام لكافة المستخدمين إلى *فرنسا*:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات على حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-AzureADUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>تغيير الخصائص لمجموعة معينة من حسابات المستخدمين

لتغيير خصائص مجموعة معينة من حسابات المستخدمين، يمكنك استخدام مزيج من **Get-AzureADUser** و **Where** و **Set-AzureADUser** cmdlets. يغير المثال التالي موقع الاستخدام لكافة المستخدمين في قسم المحاسبة إلى *فرنسا*:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات على حسابات المستخدمين (**Get-AzureADUser**)، وأرسلها إلى الأمر التالي (**|**).

1.  ابحث عن جميع حسابات المستخدمين التي تم تعيين خاصية *القسم* الخاصة بها إلى "المحاسبة" (**حيث {$_. القسم -eq "Accounting"}**)، وإرسال المعلومات الناتجة إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-AzureADUser -UsageLocation "FR"**).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

لتكوين خصائص لحسابات المستخدمين باستخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell، استخدم **Set-MsolUser** cmdlet وحدد الخصائص لتعيينها أو تغييرها.

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
> [!NOTE]
> لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell و cmdlets مع *Msol* باسمها. تشغيل أوامر cmdlets هذه من Windows PowerShell.

### <a name="change-properties-for-a-specific-user-account"></a>تغيير خصائص حساب مستخدم معين

لتكوين خصائص لحساب مستخدم معين، استخدم [**Set-MsolUser**](/previous-versions/azure/dn194136(v=azure.100)) cmdlet وحدد الخصائص لتعيينها أو تغييرها. 

يمكنك تحديد الحساب باستخدام المعلمة *-UserPrincipalName* وتعيين خصائص معينة أو تغييرها باستخدام معلمات إضافية. فيما يلي قائمة بالمعلمات الأكثر شيوعا.
  
- -المدينة "\<city name>"

- -البلد "\<country name>"

- -القسم "\<department name>"

- -DisplayName "\<full user name>"

- -فاكس "\<fax number>"

- -FirstName "\<user first name>"

- -LastName "\<user last name>"

- -MobilePhone "\<mobile phone number>"

- -Office "\<office location>"

- -رقم الهاتف "\<office phone number>"

- -الرمز البريدي "\<postal code>"

- -PreferredLanguage "\<language>"

- -State "\<state name>"

- -StreetAddress "\<street address>"

- -العنوان "\<title name>"

- -UsageLocation "\<2-character country or region code>"

    هذا هو رمز البلد أو المنطقة ISO 3166-1 alpha-2 (A2) المكون من حرفين.

للحصول على معلمات إضافية، راجع [Set-MsolUser](/previous-versions/azure/dn194136(v=azure.100)).

للاطلاع على أسماء المستخدمين الأساسيين لجميع المستخدمين، قم بتشغيل الأمر التالي:
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات لحسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).

1. فرز قائمة أسماء المستخدمين الأساسيين أبجديا (**فرز UserPrincipalName**) وإرسالها إلى الأمر التالي (**|**).

1. عرض خاصية اسم المستخدم الأساسي فقط لكل حساب (**حدد UserPrincipalName**).

1. اعرضها على شاشة واحدة في كل مرة (**المزيد**).

لعرض اسم المستخدم الأساسي لحساب استنادا إلى اسم العرض الخاص به (الاسم الأول واسم العائلة)، قم بتشغيل الأوامر التالية. املأ المتغير *$userName* ، وقم بإزالة الأحرف \< and > .
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

يعرض هذا المثال اسم المستخدم الأساسي للمستخدم المسمى Caleb Sills:
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

باستخدام متغير *$upn* ، يمكنك إجراء تغييرات على الحسابات الفردية استنادا إلى اسم العرض الخاص بها. فيما يلي مثال يعين موقع استخدام *Beplay Newman* إلى *فرنسا*، ولكنه يحدد اسم العرض الخاص بها بدلا من اسم المستخدم الأساسي الخاص بها:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>تغيير الخصائص لكافة حسابات المستخدمين

لتغيير الخصائص لجميع المستخدمين، استخدم مزيجا من **Get-MsolUser** و **Set-MsolUser** cmdlets. يغير المثال التالي موقع الاستخدام لكافة المستخدمين إلى *فرنسا*:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات لحسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-MsolUser -UsageLocation "FR"**).

### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>تغيير الخصائص لمجموعة معينة من حسابات المستخدمين

لتغيير خصائص مجموعة معينة من حسابات المستخدمين، يمكنك استخدام مجموعة من أوامر cmdlets **Get-MsolUser** و **Where** و **Set-MsolUser** . يغير المثال التالي موقع الاستخدام لكافة المستخدمين في قسم المحاسبة إلى *فرنسا*:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات لحسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).

1. ابحث عن كافة حسابات المستخدمين التي تم تعيين خاصية *القسم* الخاصة بها إلى "المحاسبة" (**حيث {$_. Department -eq "Accounting"}**) وإرسال المعلومات الناتجة إلى الأمر التالي (**|**).

1. تعيين موقع المستخدم إلى فرنسا (**Set-MsolUser -UsageLocation "FR"**).

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
