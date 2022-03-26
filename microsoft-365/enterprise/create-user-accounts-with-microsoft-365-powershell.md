---
title: إنشاء Microsoft 365 المستخدمين باستخدام PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: كيفية استخدام PowerShell لإنشاء حسابات المستخدمين الفردية أو Microsoft 365 متعددة.
ms.openlocfilehash: 7396e98e597491910b639e5a0d0c57b8f685bc02
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569367"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>إنشاء Microsoft 365 المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 لإنشاء حسابات المستخدمين بكفاءة، بما في ذلك حسابات متعددة.

عند إنشاء حسابات المستخدمين في PowerShell، تكون بعض خصائص الحساب مطلوبة دائما. الخصائص الأخرى غير مطلوبة ولكنها مهمة. راجع الجدول التالي.
  
|**اسم الخاصية**|**مطلوب؟**|**الوصف**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |نعم  <br/> |هذا هو اسم العرض المستخدم في Microsoft 365 الخدمات. على سبيل المثال *، Caleb Sills*. <br/> |
|**UserPrincipalName** <br/> |نعم  <br/> |هذا هو اسم الحساب المستخدم في تسجيل الدخول Microsoft 365 الخدمات. على سبيل المثال *، CalebS\@ contoso.onmicrosoft.com*.  <br/> |
|**FirstName** <br/> |لا  <br/> ||
|**LastName** <br/> |لا  <br/> ||
|**LicenseAssignment** <br/> |لا  <br/> |هذه هي خطة الترخيص (المعروفة أيضا باسم خطة الترخيص أو SKU) التي يتم تعيين ترخيص متوفر منها إلى حساب المستخدم. يعرف الترخيص Microsoft 365 المتوفرة للحساب. لست بحاجة إلى تعيين ترخيص لمستخدم عند إنشاء الحساب، ولكن يجب أن يكون الحساب لديه ترخيص للوصول إلى Microsoft 365 الخدمات. لديك 30 يوما لترخيص حساب المستخدم بعد إنشائه. |
|**كلمة المرور** <br/> |لا  <br/> | إذا لم تحدد كلمة مرور، يتم تعيين كلمة مرور عشوائية لحساب المستخدم، وكلمة المرور مرئية في نتائج الأمر. إذا قمت بتحديد كلمة مرور، يجب أن تكون من 8 إلى 16 أحرف ASCII النصية من الأنواع التالية: الأحرف صغيرة والأحرف الكبيرة و الأرقام والرموز.<br/> |
|**UsageLocation** <br/> |لا  <br/> |هذا رمز بلد ISO 3166-1 صالح. على سبيل المثال *، الولايات* المتحدة الأمريكية و *FR* لفرنسا. من المهم توفير هذه القيمة، لأن بعض Microsoft 365 الخدمات غير متوفرة في بلدان معينة. لا يمكنك تعيين ترخيص لحساب مستخدم ما لم يتم تكوين هذه القيمة للحساب. لمزيد من المعلومات، راجع [حول قيود الترخيص](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |

>[!Note]
>[تعرف على كيفية إنشاء حسابات المستخدمين](../admin/add-users/add-users.md) باستخدام مركز مسؤولي Microsoft 365.
> 
> للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

بعد الاتصال، استخدم بناء الجملة التالي لإنشاء حساب فردي:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

ينشئ هذا المثال حسابا للمستخدم الأميركي *Caleb Sills*:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>إنشاء حساب مستخدم فردي

لإنشاء حساب فردي، استخدم بناء الجملة التالي:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets التي تتضمن *Msol* في اسمها. تشغيل cmdlets هذه من Windows PowerShell.
>

لتضمين أسماء خطط الترخيص المتوفرة، استخدم هذا الأمر:

````powershell
Get-MsolAccountSku
````

ينشئ هذا المثال حسابا للمستخدم الأميركي *Caleb Sills*`contoso:ENTERPRISEPACK`، ويعين ترخيصا من خطة ترخيص (Office 365 Enterprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>إنشاء حسابات مستخدمين متعددة

1. إنشاء ملف قيم مفصولة بفصول (CSV) يحتوي على معلومات حساب المستخدم المطلوبة. على سبيل المثال:

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >تكون أسماء الأعمدة ترتيبها في الصف الأول من ملف CSV عشوائيا. ولكن تأكد من أن ترتيب البيانات في باقي الملف يتطابق مع ترتيب أسماء الأعمدة. استخدم أسماء الأعمدة لقيم المعلمات في الأمر PowerShell Microsoft 365.
    
2. استخدم بناء الجملة التالي:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   ينشئ هذا المثال حسابات المستخدمين من الملف *C:\my Documents\NewAccounts.csv* ويسجل النتائج في ملف *باسم C:\My Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. راجع ملف الإخراج لرؤية النتائج. لم نحدد كلمات المرور، لذلك تكون كلمات المرور العشوائية Microsoft 365 التي تم إنشاؤها مرئية في ملف الإخراج.
    
## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)