---
title: إنشاء حسابات مستخدمين Microsoft 365 باستخدام PowerShell
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: كيفية استخدام PowerShell لإنشاء حسابات مستخدمين فردية أو متعددة Microsoft 365.
ms.openlocfilehash: 2b0ef749dc0a0d38d84d1086dee50ce416d93e9b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101040"
---
# <a name="create-microsoft-365-user-accounts-with-powershell"></a>إنشاء حسابات مستخدمين Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك استخدام PowerShell Microsoft 365 لإنشاء حسابات المستخدمين بكفاءة، بما في ذلك حسابات متعددة.

عند إنشاء حسابات مستخدمين في PowerShell، تكون بعض خصائص الحساب مطلوبة دائما. الخصائص الأخرى غير مطلوبة ولكنها مهمة. راجع الجدول التالي.
  
|**اسم الخاصية**|**مطلوب؟**|**الوصف**|
|:-----|:-----|:-----|
|**العرض** <br/> |نعم  <br/> |هذا هو اسم العرض المستخدم في خدمات Microsoft 365. على سبيل المثال، *Caleb Sills*. <br/> |
|**UserPrincipalName** <br/> |نعم  <br/> |هذا هو اسم الحساب المستخدم لتسجيل الدخول إلى خدمات Microsoft 365. على سبيل المثال، *Calebs\@ contoso.onmicrosoft.com*.  <br/> |
|**Firstname** <br/> |لا  <br/> ||
|**Lastname** <br/> |لا  <br/> ||
|**LicenseAssignment** <br/> |لا  <br/> |هذه هي خطة الترخيص (المعروفة أيضا بخطة الترخيص أو SKU) التي يتم من خلالها تعيين ترخيص متوفر لحساب المستخدم. يحدد الترخيص خدمات Microsoft 365 المتوفرة للحساب. لا يتعين عليك تعيين ترخيص لمستخدم عند إنشاء الحساب، ولكن يجب أن يكون للحساب ترخيص للوصول إلى خدمات Microsoft 365. لديك 30 يوما لترخيص حساب المستخدم بعد إنشائه. |
|**كلمه المرور** <br/> |لا  <br/> | إذا لم تحدد كلمة مرور، يتم تعيين كلمة مرور عشوائية لحساب المستخدم، وتكون كلمة المرور مرئية في نتائج الأمر. إذا حددت كلمة مرور، فيجب أن تكون من 8 إلى 16 حرفا نصيا من ASCII من الأنواع التالية: أحرف صغيرة وأحرف كبيرة وأرقام ورموز.<br/> |
|**تحديد الاستخدام** <br/> |لا  <br/> |هذا رمز بلد ISO 3166-1 alpha-2 صالح. على سبيل المثال، *الولايات* المتحدة للولايات المتحدة، *وFR* ل فرنسا. من المهم توفير هذه القيمة، لأن بعض خدمات Microsoft 365 غير متوفرة في بعض البلدان. لا يمكنك تعيين ترخيص لحساب مستخدم ما لم يتم تكوين هذه القيمة للحساب. لمزيد من المعلومات، راجع ["حول قيود الترخيص](https://go.microsoft.com/fwlink/p/?LinkId=691730)".<br/> |

>[!Note]
>[تعرف على كيفية إنشاء حسابات المستخدمين](../admin/add-users/add-users.md) باستخدام مركز مسؤولي Microsoft 365.
> 
> للحصول على قائمة بالموارد الإضافية، راجع [إدارة المستخدمين والمجموعات](/admin).
>   

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

بعد الاتصال، استخدم بناء الجملة التالي لإنشاء حساب فردي:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName "<display name>" -GivenName "<first name>" -SurName "<last name>" -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

ينشئ هذا المثال حسابا للمستخدم الأمريكي *Caleb Sills*:
  
```powershell
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="create-an-individual-user-account"></a>إنشاء حساب مستخدم فردي

لإنشاء حساب فردي، استخدم بناء الجملة التالي:
  
```powershell
New-MsolUser -DisplayName <display name> -FirstName <first name> -LastName <last name> -UserPrincipalName <sign-in name> -UsageLocation <ISO 3166-1 alpha-2 country code> -LicenseAssignment <licensing plan name> [-Password <Password>]
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets التي تحتوي على *Msol* باسمها. تشغيل أوامر cmdlets هذه من Windows PowerShell.
>

لإدراج أسماء خطط الترخيص المتوفرة، استخدم هذا الأمر:

````powershell
Get-MsolAccountSku
````

ينشئ هذا المثال حسابا للمستخدم الأمريكي *Caleb Sills*، ويعين ترخيصا من `contoso:ENTERPRISEPACK` خطة ترخيص (Office 365 Enterprise E3).
  
```powershell
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

### <a name="create-multiple-user-accounts"></a>إنشاء حسابات مستخدمين متعددة

1. إنشاء ملف قيمة مفصولة بفواصل (CSV) يحتوي على معلومات حساب المستخدم المطلوبة. على سبيل المثال:

     ```powershell
     UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
     ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
     LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
     ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
     ```

   >[!NOTE]
   >أسماء الأعمدة وترتيبها في الصف الأول من ملف CSV عشوائية. ولكن تأكد من أن ترتيب البيانات في بقية الملف يطابق ترتيب أسماء الأعمدة. واستخدم أسماء الأعمدة لقيم المعلمات في PowerShell للأمر Microsoft 365.
    
2. استخدم بناء الجملة التالي:
    
    ```powershell
     Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
    ```

   ينشئ هذا المثال حسابات مستخدمين من الملف *C:\my Documents\NewAccounts.csv* ويسجل النتائج في ملف يسمى *C:\My Documents\NewAccountResults.csv*.
    
    ```powershell
    Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
    ```

3. راجع ملف الإخراج للاطلاع على النتائج. لم نحدد كلمات المرور، لذلك تكون كلمات المرور العشوائية التي Microsoft 365 إنشاؤها مرئية في ملف الإخراج.
    
## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)