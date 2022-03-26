---
title: عرض Microsoft 365 المستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: 5c434825da95fd7d90594b2424cab287305f7d26
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/02/2021
ms.locfileid: "63569647"
---
# <a name="view-microsoft-365-user-accounts-with-powershell"></a>عرض Microsoft 365 المستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

يمكنك استخدام مركز مسؤولي Microsoft 365 لعرض حسابات المستأجر Microsoft 365 المستأجر. يمكن PowerShell for Microsoft 365 هذا ولكنه يوفر أيضا وظائف إضافية.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>استخدام وحدة Azure Active Directory PowerShell Graph النمطية

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>عرض كل الحسابات

لعرض القائمة الكاملة من حسابات المستخدمين، اعرض هذا الأمر:
  
```powershell
Get-AzureADUser
```

يجب أن تحصل على معلومات مماثلة لهذه:
  
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

لعرض حساب مستخدم معين، تشغيل الأمر التالي. قم بتعبئة اسم حساب تسجيل الدخول لحساب المستخدم، والذي يعرف أيضا بالاسم الرئيسي للمستخدم (UPN). إزالة الأحرف "<" و">" .
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

فيما يلي مثال على ذلك:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>عرض قيم خاصية إضافية لحساب معين

بشكل افتراضي، يعرض **الأمر Cmdlet Get-AzureADUser** الخصائص *ObjectID* و *DisplayName* و *UserPrincipalName* للحسابات فقط.

لكي تكون أكثر اختيارا حول الخصائص التي تريد عرضها، استخدم **الأمر تحديد** cmdlet مع **الأمر Cmdlet Get-AzureADUser** . لدمج أمري cmdlets، استخدم الحرف "pipe" ("|")، الذي يخبر Azure Active Directory PowerShell ل Graph أخذ نتائج أمر واحد وإرساله إلى الأمر التالي. فيما يلي مثال على الأمر الذي يعرض *DisplayName و Department* و *UsageLocation* لكل حساب مستخدم:
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات في حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).
    
1.  عرض اسم حساب المستخدم والقسم وموقع الاستخدام فقط (**حدد اسم العرض والقسم وموقع الاستخدام**).
  
لرؤية كل الخصائص لحساب مستخدم معين، استخدم **تحديد** cmdlet و حرف البدل (*). فيما يلي مثال على ذلك:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

على سبيل المثال، قم بتشغيل الأمر التالي للتحقق من الحالة التي تم تمكينها لحساب مستخدم معين:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-account-synchronization-status"></a>عرض حالة مزامنة الحساب

حسابات المستخدمين لها مصدرين: 

- Windows Server Active Directory (AD)، وهي حسابات تتم مزامنتها من AD المحلي إلى السحابة.

- حسابات Azure Active Directory (Azure AD) التي يتم إنشاؤها مباشرة في السحابة.

يمكنك استخدام الأمر التالي للعثور على الحسابات التي يتم مزامنتها من AD في **الموقع** . إنه يطلب من PowerShell تعيين كل المستخدمين الذين لديهم السمة *DirSyncEnabled* إلى *True*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -eq $true}
```

يمكنك استخدام الأمر التالي للعثور على **حسابات السحابة** فقط. وهي ترشد PowerShell إلى تعيين السمة *DirSyncEnabled* إلى *False* أو عدم تعيينها (*Null*).
تم تعيين *DirSyncEnabled* لحساب لم تتم مزامنته من AD في الموقع إلى *Null*. تم تعيين *DirSyncEnabled* للحساب الذي تم مزامنته مبدئيا من AD في الموقع ولكن لم يعد تتم مزامنته إلى *False*. 

```powershell
Get-AzureADUser | Where {$_.DirSyncEnabled -ne $true}
```

### <a name="view-accounts-based-on-a-common-property"></a>عرض الحسابات استنادا إلى خاصية شائعة

لتكون أكثر اختيارا حول قائمة الحسابات التي سيتم عرضها، يمكنك استخدام الأمر **Where** cmdlet مع **الأمر cmdlet Get-AzureADUser** . لدمج أمري cmdlets، استخدم الحرف "pipe" ("|")، الذي يخبر Azure Active Directory PowerShell ل Graph أخذ نتائج أمر واحد وإرساله إلى الأمر التالي. فيما يلي أمر مثال يعرض فقط حسابات المستخدمين التي لها موقع استخدام غير محدد:
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

يوجه هذا الأمر Azure Active Directory PowerShell Graph:
  
1. احصل على كل المعلومات في حسابات المستخدمين (**Get-AzureADUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. ابحث عن كل حسابات المستخدمين التي لها موقع استخدام غير محدد (**أين {$\_. UsageLocation -eq $Null}**). داخل الرموش، يقوم الأمر بإرشاد PowerShell للعثور فقط على مجموعة الحسابات التي لها خاصية حساب مستخدم UsageLocation (**$\_. UsageLocation**) غير محدد (**-eq $Null**).
    
خاصية **UsageLocation** هي واحدة فقط من العديد من الخصائص المقترنة باستخدام حساب مستخدم. لعرض كل الخصائص لحساب مستخدم معين، استخدم **تحديد** cmdlet و حرف البدل (*). فيما يلي مثال على ذلك:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

على سبيل المثال **، المدينة** هي اسم خاصية حساب مستخدم. يمكنك استخدام الأمر التالي لقائمة جميع حسابات المستخدمين الذين يعيشون في لندن:
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
> بناء جملة الأمر **Where** cmdlet في هذه الأمثلة هو **أين {$\_.** [اسم خاصية حساب المستخدم] [عامل المقارنة] [value] **}**.> [عامل المقارنة] هو **-eq** ل يساوي، **-ne** ل لا يساوي، **-lt** لأقل من، **-gt** للكميات الأكبر من، وغيرها.  [value] عادة ما تكون سلسلة (سلسلة من الأحرف و الأرقام والأحرف الأخرى) أو قيمة **رقمية** أو $Null غير محددة. لمزيد من المعلومات، راجع [أين](/powershell/module/microsoft.powershell.core/where-object).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>استخدم الوحدة Microsoft Azure Active Directory النمطية Windows PowerShell

أولا، [اتصل Microsoft 365 المستأجر](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>عرض كل الحسابات

لعرض القائمة الكاملة من حسابات المستخدمين، اعرض هذا الأمر:
  
```powershell
Get-MsolUser
```

>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets مع *Msol* في اسمها. تشغيل cmdlets هذه من Windows PowerShell.
>

يجب أن تحصل على معلومات مماثلة لهذه:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

كما **أن الأمر Cmdlet Get-MsolUser** به مجموعة من المعلمات لتصفية مجموعة حسابات المستخدمين المعروضة. على سبيل المثال، بالنسبة لقائمة المستخدمين غير المرخصين (المستخدمون الذين تم إضافتهم إلى Microsoft 365 ولكن لم يتم ترخيصهم بعد لاستخدام أي من الخدمات)، يمكنك تشغيل هذا الأمر:
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

يجب أن تحصل على معلومات مماثلة لهذه:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

للحصول على معلومات حول معلمات إضافية لتصفية مجموعة حسابات المستخدمين التي يتم عرضها، راجع [Get-MsolUser](/previous-versions/azure/dn194133(v=azure.100)).
  
### <a name="view-a-specific-account"></a>عرض حساب معين

لعرض حساب مستخدم معين، تشغيل الأمر التالي. قم بتعبئة اسم تسجيل الدخول لحساب المستخدم، والذي يعرف أيضا بالاسم الرئيسي للمستخدم (UPN). إزالة الأحرف "<" و">" .
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-accounts-based-on-a-common-property"></a>عرض الحسابات استنادا إلى خاصية شائعة

لكي تكون أكثر اختيارا حول قائمة الحسابات التي سيتم عرضها، يمكنك استخدام الأمر **Where** cmdlet مع **الأمر Cmdlet Get-MsolUser** . لدمج أمري cmdlets، استخدم الحرف "pipe" ("|")، الذي يخبر PowerShell بأن يأخذ نتائج أمر واحد ويرسله إلى الأمر التالي. فيما يلي مثال يعرض حسابات المستخدمين التي لها موقع استخدام غير محدد فقط:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات في حسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. ابحث عن كل حسابات المستخدمين التي لها موقع استخدام غير محدد (**أين {$\_. UsageLocation -eq $Null}**). داخل الرموش، يقوم الأمر بإرشاد PowerShell للعثور على مجموعة الحسابات التي لها خاصية حساب مستخدم UsageLocation فقط (**$\_. UsageLocation**) غير محدد (**-eq $Null**).
    
يجب أن تحصل على معلومات مماثلة لهذه:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

خاصية *UsageLocation* هي واحدة فقط من العديد من الخصائص المقترنة باستخدام حساب مستخدم. لعرض كل الخصائص لحسابات المستخدمين، استخدم **الأمر تحديد** cmdlet و حرف البدل (*) لعرضها كلها لحساب مستخدم معين. فيما يلي مثال على ذلك:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

على سبيل المثال *، المدينة* هي اسم خاصية حساب مستخدم. يمكنك استخدام الأمر التالي لقائمة كل حسابات المستخدمين للمستخدمين الذين يعيشون في لندن:
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
> بناء جملة الأمر **Where** cmdlet في هذه الأمثلة هو **أين {$\_.** [اسم خاصية حساب المستخدم] [عامل المقارنة] [value] **}**.  [عامل المقارنة] **هو -eq** ل يساوي، **-ne** ل لا يساوي، **-lt** لأقل من، **-gt** للكميات الأكبر من، وغيرها.  [value] عادة ما تكون سلسلة (سلسلة من الأحرف و الأرقام والأحرف الأخرى) أو قيمة **رقمية** أو $Null غير محددة. لمزيد من المعلومات، راجع [أين](/powershell/module/microsoft.powershell.core/where-object).
  
للتحقق من الحالة المحظورة لحساب مستخدم، استخدم الأمر التالي:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>عرض قيم خاصية إضافية للحسابات

بشكل افتراضي، يعرض **Cmdlet Get-MsolUser** الخصائص الثلاثة هذه الخاصة وحسابات المستخدمين:
  
- UserPrincipalName

- DisplayName

- isLicensed

إذا كنت بحاجة إلى خصائص إضافية، مثل القسم الذي يعمل فيه المستخدم والمنطقة/البلد حيث يستخدم خدمات Microsoft 365، يمكنك تشغيل **Get-MsolUser** مع الأمر **تحديد** cmdlet لتحديد قائمة خصائص حساب المستخدم. فيما يلي مثال على ذلك:
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات حول حسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. عرض اسم حساب المستخدم والقسم وموقع الاستخدام فقط (**حدد اسم العرض والقسم وموقع الاستخدام**).
    
يجب أن تحصل على معلومات مماثلة لهذه:
  
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

يتيح **لك الأمر تحديد** cmdlet اختيار الخصائص التي تريد عرضها. لعرض كل الخصائص لحساب مستخدم معين، استخدم حرف البدل (*). فيما يلي مثال على ذلك:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

لتكون أكثر انتقائية حول قائمة الحسابات التي تريد عرضها، يمكنك أيضا استخدام **الأمر أين** cmdlet. فيما يلي أمر مثال يعرض فقط حسابات المستخدمين التي لها موقع استخدام غير محدد:
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

يوجه هذا الأمر PowerShell إلى:
  
1. احصل على كل المعلومات حول حسابات المستخدمين (**Get-MsolUser**) وأرسلها إلى الأمر التالي (**|**).
    
1. ابحث عن كل حسابات المستخدمين التي لها موقع استخدام غير محدد (**أين {$\_. UsageLocation -eq $Null}**)، وأرسل المعلومات الناتجة إلى الأمر التالي (**|**). داخل الرموش، يقوم الأمر بإرشاد PowerShell للعثور فقط على مجموعة الحسابات التي لها خاصية حساب مستخدم UsageLocation (**$\_. UsageLocation**) غير محدد (**-eq $Null**).
    
1. عرض اسم حساب المستخدم والقسم وموقع الاستخدام فقط (**حدد اسم العرض والقسم وموقع الاستخدام**).
    
يجب أن تحصل على معلومات مماثلة لهذه:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

إذا كنت تستخدم مزامنة الدليل لإنشاء مستخدمي Microsoft 365 وإدارتهم، يمكنك عرض الحساب المحلي الذي تم عرض Microsoft 365 مستخدم آخر منه. يفترض المثال التالي ما يلي:

- تم تكوين الاتصال Azure AD لاستخدام نقطة الارتساء المصدر الافتراضية ل ObjectGUID. (لمزيد من المعلومات حول تكوين نقطة ارتساء المصدر، راجع [Azure AD الاتصال: مفاهيم التصميم](/azure/active-directory/hybrid/plan-connect-design-concepts)).
- تم تثبيت الوحدة النمطية لخدمات مجال Active Directory ل PowerShell (راجع [أدوات RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)).

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
