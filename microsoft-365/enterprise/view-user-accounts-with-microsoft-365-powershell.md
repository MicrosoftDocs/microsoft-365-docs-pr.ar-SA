---
title: عرض حسابات المستخدمين Microsoft 365 باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
- seo-marvel-apr2020
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: تعرف على كيفية عرض حسابات المستخدمين Microsoft 365 أو سردها أو عرضها بطرق مختلفة باستخدام PowerShell.
ms.openlocfilehash: cbbb188c50e4d163d5ef4226a83968c64e8a260c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090718"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>عرض حسابات المستخدمين Microsoft 365 باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يمكنك استخدام مركز مسؤولي Microsoft 365 لعرض حسابات مستأجر Microsoft 365. يتيح PowerShell ل Microsoft 365 هذا ولكنه يوفر أيضا وظائف إضافية.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام Azure Active Directory PowerShell للوحدة النمطية Graph

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>عرض كافة الحسابات

لعرض القائمة الكاملة لحسابات المستخدمين، قم بتشغيل هذا الأمر:
  
```powershell
Get-AzureADUser
```

يجب أن تحصل على معلومات مشابهة لهذا:
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>عرض حساب معين

لعرض حساب مستخدم معين، قم بتشغيل الأمر التالي. قم بتعبئة اسم حساب تسجيل الدخول لحساب المستخدم، والذي يعرف أيضا باسم اسم المستخدم الأساسي (UPN). قم بإزالة الأحرف "<" و">".
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

فيما يلي مثال على ذلك:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>عرض قيم خصائص إضافية لحساب معين

بشكل افتراضي، يعرض **Cmdlet Get-AzureADUser** خصائص *ObjectID* و *DisplayName* و *UserPrincipalName* للحسابات فقط.

لتكون أكثر انتقائية حول الخصائص المطلوب عرضها، استخدم **Select** cmdlet مع **Get-AzureADUser** cmdlet. لدمج أمري cmdlets، استخدم الحرف "pipe" ("|")، الذي يخبر Azure Active Directory PowerShell Graph لأخذ نتائج أمر واحد وإرساله إلى الأمر التالي. فيما يلي مثال على الأمر الذي يعرض *DisplayName* و *Department* و *UsageLocation* لكل حساب مستخدم:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات على حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).
    
1.  عرض اسم حساب المستخدم والقسم وموقع الاستخدام فقط (**حدد DisplayName و Department و UsageLocation**).
  
لمشاهدة جميع خصائص حساب مستخدم معين، استخدم **"تحديد** cmdlet" وحرف البدل (*). فيما يلي مثال على ذلك:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

كمثال آخر، قم بتشغيل الأمر التالي للتحقق من الحالة الممكنة لحساب مستخدم معين:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>عرض حالة مزامنة الحساب

حسابات المستخدمين لها مصدران: 

- Windows Server Active Directory (AD)، وهي حسابات تتم مزامنتها من AD المحلي إلى السحابة.

- حسابات Azure Active Directory (Azure AD)، التي يتم إنشاؤها مباشرة في السحابة.

يمكنك استخدام الأمر التالي للبحث عن الحسابات التي تتم مزامنتها من AD **المحلي** . يوجه PowerShell للحصول على جميع المستخدمين الذين لديهم تعيين *السمة DirSyncEnabled* إلى *True*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

يمكنك استخدام الأمر التالي للعثور على حسابات **السحابة فقط** . يوجه PowerShell للحصول على جميع المستخدمين الذين لديهم تعيين *السمة DirSyncEnabled* إلى *False* أو لم يتم تعيينها (*Null*).
يحتوي الحساب الذي لم تتم مزامنته من AD المحلي على *تعيين DirSyncEnabled* إلى *Null*. تم تعيين *DirSyncEnabled* إلى *False* لحساب تمت مزامنته في البداية من AD محلي ولكن لم يعد قيد المزامنة. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>عرض الحسابات استنادا إلى خاصية مشتركة

لتكون أكثر انتقائية حول قائمة الحسابات التي سيتم عرضها، يمكنك استخدام **Cmdlet Where** مع **Get-AzureADUser** cmdlet. لدمج أمري cmdlets، استخدم الحرف "pipe" ("|")، الذي يخبر Azure Active Directory PowerShell Graph لأخذ نتائج أمر واحد وإرساله إلى الأمر التالي. فيما يلي مثال على الأمر الذي يعرض فقط حسابات المستخدمين التي لها موقع استخدام غير محدد:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

يرشد هذا الأمر Azure Active Directory PowerShell Graph إلى:
  
1. احصل على جميع المعلومات على حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. ابحث عن جميع حسابات المستخدمين التي لها موقع استخدام غير محدد (**حيث {$\_. UsageLocation -eq $Null}**). داخل الأقواس، يرشد الأمر PowerShell للعثور فقط على مجموعة الحسابات التي لها خاصية حساب مستخدم UsageLocation (**$\_. لم يتم تحديد UsageLocation**) (**-eq $Null**).
    
**الخاصية UsageLocation** هي واحدة فقط من العديد من الخصائص المقترنة بحساب مستخدم. لعرض كافة خصائص حساب مستخدم معين، استخدم **"تحديد** cmdlet" وحرف البدل (*). فيما يلي مثال على ذلك:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

على سبيل المثال، **المدينة** هي اسم خاصية حساب مستخدم. يمكنك استخدام الأمر التالي لإدراج جميع حسابات المستخدمين الذين يعيشون في لندن:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> بناء الجملة ل cmdlet **Where** في هذه الأمثلة هو **Where {$\_.** [اسم خاصية حساب المستخدم] [عامل المقارنة] [value] **}**.> [عامل المقارنة] هو **-eq** للتساوي، **-ne** for not equals، **-lt** لأقل من، **-gt** لزيادة من، وغيرها.  [value] عادة ما تكون سلسلة (تسلسل من الأحرف والأرقام والأحرف الأخرى) أو قيمة رقمية أو **$Null** غير محددة. لمزيد من المعلومات، راجع ["أين](/powershell/module/microsoft.powershell.core/where-object)".

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدام الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell

أولا، [اتصل بمستأجر Microsoft 365](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>عرض كافة الحسابات

لعرض القائمة الكاملة لحسابات المستخدمين، قم بتشغيل هذا الأمر:
  
```powershell
Get-MsolUser
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory للوحدة النمطية Windows PowerShell و cmdlets مع *Msol* باسمها. تشغيل أوامر cmdlets هذه من Windows PowerShell.
>

يجب أن تحصل على معلومات مشابهة لهذا:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

يحتوي **Get-MsolUser** cmdlet أيضا على مجموعة من المعلمات لتصفية مجموعة حسابات المستخدمين المعروضة. على سبيل المثال، بالنسبة لقائمة المستخدمين غير المرخصين (المستخدمين الذين تمت إضافتهم إلى Microsoft 365 ولكن لم يتم ترخيصهم بعد لاستخدام أي من الخدمات)، قم بتشغيل هذا الأمر:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

يجب أن تحصل على معلومات مشابهة لهذا:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

للحصول على معلومات حول معلمات إضافية لتصفية مجموعة حسابات المستخدمين المعروضة، راجع [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>عرض حساب معين

لعرض حساب مستخدم معين، قم بتشغيل الأمر التالي. املأ اسم تسجيل الدخول لحساب المستخدم، والذي يعرف أيضا باسم المستخدم الأساسي (UPN). قم بإزالة الأحرف "<" و">".
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>عرض الحسابات استنادا إلى خاصية مشتركة

لتكون أكثر انتقائية حول قائمة الحسابات التي سيتم عرضها، يمكنك استخدام **Where** cmdlet مع **Get-MsolUser** cmdlet. لدمج أمري cmdlets، استخدم الحرف "pipe" ("|")، الذي يخبر PowerShell بأخذ نتائج أمر واحد وإرساله إلى الأمر التالي. فيما يلي مثال يعرض فقط حسابات المستخدمين التي لها موقع استخدام غير محدد:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات على حسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. ابحث عن كافة حسابات المستخدمين التي لها موقع استخدام غير محدد (**حيث {$\_. UsageLocation -eq $Null}**). داخل الأقواس، يرشد الأمر PowerShell للعثور فقط على مجموعة الحسابات التي لها خاصية حساب مستخدم UsageLocation (**$\_. لم يتم تحديد UsageLocation**) (**-eq $Null**).
    
يجب أن تحصل على معلومات مشابهة لهذا:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

*الخاصية UsageLocation* هي واحدة فقط من العديد من الخصائص المقترنة بحساب مستخدم. للاطلاع على جميع خصائص حسابات المستخدمين، استخدم **"تحديد** cmdlet" وحرف البدل (*) لعرضها جميعا لحساب مستخدم معين. فيما يلي مثال على ذلك:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

على سبيل المثال، *المدينة* هي اسم خاصية حساب مستخدم. يمكنك استخدام الأمر التالي لإدراج جميع حسابات المستخدمين للمستخدمين الذين يعيشون في لندن:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> بناء الجملة ل cmdlet **Where** في هذه الأمثلة هو **Where {$\_.** [اسم خاصية حساب المستخدم] [عامل المقارنة] [value] **}**.  [عامل المقارنة] هو **-eq** للتساوي، **-ne** for not equals، **-lt** لأقل من، **-gt** لزيادة عن، وغيرها.  [value] عادة ما تكون سلسلة (تسلسل من الأحرف والأرقام والأحرف الأخرى) أو قيمة رقمية أو **$Null** غير محددة. لمزيد من المعلومات، راجع ["أين](/powershell/module/microsoft.powershell.core/where-object)".
  
للتحقق من الحالة المحظورة لحساب مستخدم، استخدم الأمر التالي:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>عرض قيم خصائص إضافية للحسابات

بشكل افتراضي، يعرض **Get-MsolUser** cmdlet هذه الخصائص الثلاث لحسابات المستخدمين:
  
- UserPrincipalName

- العرض

- isLicensed

إذا كنت بحاجة إلى خصائص إضافية، مثل القسم الذي يعمل فيه المستخدم والبلد/المنطقة التي يستخدم فيها خدمات Microsoft 365، يمكنك تشغيل **Get-MsolUser** مع **Select** cmdlet لتحديد قائمة خصائص حساب المستخدم. فيما يلي مثال على ذلك:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات حول حسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. عرض اسم حساب المستخدم والقسم وموقع الاستخدام فقط (**حدد DisplayName و Department و UsageLocation**).
    
يجب أن تحصل على معلومات مشابهة لهذا:
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

يتيح لك **تحديد** cmdlet اختيار الخصائص التي تريد عرضها. لعرض كافة الخصائص لحساب مستخدم معين، استخدم حرف البدل (*). فيما يلي مثال على ذلك:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

لتكون أكثر انتقائية حول قائمة الحسابات التي سيتم عرضها، يمكنك أيضا استخدام **Cmdlet Where** . فيما يلي مثال على الأمر الذي يعرض فقط حسابات المستخدمين التي لها موقع استخدام غير محدد:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على جميع المعلومات حول حسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. ابحث عن كافة حسابات المستخدمين التي لها موقع استخدام غير محدد (**حيث {$\_. UsageLocation -eq $Null}**)، وإرسال المعلومات الناتجة إلى الأمر التالي (**|**). داخل الأقواس، يرشد الأمر PowerShell للعثور فقط على مجموعة الحسابات التي لها خاصية حساب مستخدم UsageLocation (**$\_. لم يتم تحديد UsageLocation**) (**-eq $Null**).
    
1. عرض اسم حساب المستخدم والقسم وموقع الاستخدام فقط (**حدد DisplayName و Department و UsageLocation**).
    
يجب أن تحصل على معلومات مشابهة لهذا:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

إذا كنت تستخدم مزامنة الدليل لإنشاء المستخدمين Microsoft 365 وإدارتهم، يمكنك عرض الحساب المحلي الذي تم عرض مستخدم Microsoft 365 منه. يفترض المثال التالي ما يلي:

- تم تكوين الاتصال Azure AD لاستخدام ارتساء المصدر الافتراضي ل ObjectGUID. (لمزيد من المعلومات حول تكوين ارتساء مصدر، راجع [الاتصال Azure AD: مفاهيم التصميم](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- تم تثبيت الوحدة النمطية خدمات مجال Active Directory ل PowerShell (راجع [أدوات RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>راجع أيضًا

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
