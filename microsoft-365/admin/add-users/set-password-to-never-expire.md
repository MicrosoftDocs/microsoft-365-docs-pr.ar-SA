---
title: تعيين كلمة مرور مستخدم فردي حتى لا تنتهي صلاحيتها أبدا
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
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: سجل الدخول إلى حساب Microsoft 365 لتعيين بعض كلمات مرور المستخدم الفردية حتى لا تنتهي صلاحيتها أبدا باستخدام Windows PowerShell.
ms.openlocfilehash: f0eff70b2b95c7e318f8a7e52777d4b684dbd8bf
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63567084"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>تعيين كلمة مرور مستخدم فردي حتى لا تنتهي صلاحيتها أبدا

تشرح هذه المقالة كيفية تعيين كلمة مرور لمستخدم فردي لكي لا تنتهي صلاحيتها. يجب عليك إكمال هذه الخطوات باستخدام PowerShell.

## <a name="before-you-begin"></a>قبل البدء

هذه المقالة للأشخاص الذين يحددون نهج انتهاء صلاحية كلمة المرور للأعمال أو المدرسة أو المؤسسات غير الربحية. لإكمال هذه الخطوات، تحتاج إلى تسجيل الدخول باستخدام حساب المسؤول Microsoft 365 الخاص بك. راجع [نظرة عامة على مركز مسؤولي Microsoft 365](/microsoft-365/admin/admin-overview/admin-center-overview?view=o365-worldwide).

يجب أن تكون مسؤولا [عاما أو مسؤول كلمة مرور](about-admin-roles.md) لتنفيذ هذه الخطوات.

يمكن للمسؤول العام لخدمة سحابة Microsoft استخدام [Azure Active Directory PowerShell](/powershell/azure/active-directory/install-adv2) Graph لتعيين كلمات المرور التي لا تنتهي صلاحيتها لمستخدمين معينين. يمكنك أيضا استخدام [AzureAD](/powershell/module/Azuread) cmdlets لإزالة التكوين الذي لم تنتهي صلاحيته أبدا أو لمعرفة كلمات مرور المستخدمين التي تم تعيينها لكي لا تنتهي صلاحيتها أبدا.

ينطبق هذا الدليل على موفرين آخرين، مثل Intune Microsoft 365، التي تعتمد أيضا على Azure AD لخدمات الهوية والدليل. انتهاء صلاحية كلمة المرور هو الجزء الوحيد من النهج الذي يمكن تغييره.


## <a name="how-to-check-the-expiration-policy-for-a-password"></a>كيفية التحقق من نهج انتهاء الصلاحية لكلمة مرور

لمزيد من المعلومات حول Get-AzureADUser في وحدة AzureAD النمطية، راجع المقالة المرجعية [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

تشغيل أحد الأوامر التالية:

- لمعرفة ما إذا تم تعيين كلمة مرور مستخدم واحد على عدم انتهاء صلاحيتها مطلقا، قم بتشغيل الأمر cmdlet التالي باستخدام UPN (على سبيل المثال *، user@contoso.onmicrosoft.com*) أو اسم المستخدم للمستخدم الذي تريد التحقق من:

    ```powershell
    Get-AzureADUser -ObjectId <user id or UPN> | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

    على سبيل المثال:

    ```powershell
    Get-AzureADUser -ObjectId userUPN@contoso.com | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    }
    ```

- لرؤية إعداد **كلمة المرور لا تنتهي صلاحيته** لجميع المستخدمين، يمكنك تشغيل cmdlet التالي:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- للحصول على تقرير حول جميع المستخدمين الذين لديهم PasswordNeverExpires في Html على سطح المكتب الخاص بالمستخدم الحالي  **باستخدام اسمReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- للحصول على تقرير حول جميع المستخدمين الذين لديهم PasswordNeverExpires في CSV على سطح المكتب الخاص بالمستخدم الحالي **باستخدام اسمReportPasswordNeverExpires.csv**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Csv -NoTypeInformation | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.csv

## Set a password to never expire

Run one of the following commands:

- To set the password of one user to never expire, run the following cmdlet by using the UPN or the user ID of the user:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies DisablePasswordExpiration
    ```

- لتعيين كلمات مرور جميع المستخدمين في المؤسسة لكي لا تنتهي صلاحيتها أبدا، قم بتشغيل cmdlet التالي:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> حسابات المستخدمين التي تم تكوينها مع المعلمة `-PasswordPolicies DisablePasswordExpiration` التي لا تزال العمر استنادا إلى السمة `pwdLastSet` . استنادا إلى `pwdLastSet` `-PasswordPolicies None`السمة، إذا قمت بتغيير انتهاء الصلاحية إلى ، فإن كل كلمات المرور التي لها pwdLastSet الأقدم من 90 يوما تتطلب من المستخدم تغييرها في المرة التالية التي يقوم فيها تسجيل الدخول. يمكن أن يؤثر هذا التغيير على عدد كبير من المستخدمين.

### <a name="set-a-password-to-expire"></a>تعيين كلمة مرور لكي تنتهي صلاحيتها

تشغيل أحد الأوامر التالية:

- لتعيين كلمة المرور الخاصة بمستخدم واحد بحيث تنتهي صلاحية كلمة المرور، قم بتشغيل الأمر cmdlet التالي باستخدام UPN أو اسم المستخدم للمستخدم:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- لتعيين كلمات مرور جميع المستخدمين في المؤسسة بحيث تنتهي صلاحيتها، استخدم الأمر cmdlet التالي:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>المحتوى ذي الصلة

[السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم](../add-users/let-users-reset-passwords.md) (مقالة)\
[إعادة تعيين كلمات المرور](../add-users/reset-passwords.md) (مقالة)\
[تعيين نهج انتهاء صلاحية كلمة المرور لمنظمتك](../manage/set-password-expiration-policy.md) (مقالة)
