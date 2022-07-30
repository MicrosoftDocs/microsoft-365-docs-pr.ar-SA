---
title: تعيين كلمة مرور مستخدم فردية على ألا تنتهي صلاحيتها أبدا
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
- VSBFY23
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: f493e3af-e1d8-4668-9211-230c245a0466
description: سجل الدخول إلى حساب مسؤول Microsoft 365 لتعيين بعض كلمات مرور المستخدمين الفردية لكي لا تنتهي صلاحيتها أبدا باستخدام Azure AD PowerShell.
ms.openlocfilehash: bd9960e0da7491b5f2db14618daa17b917310450
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084598"
---
# <a name="set-an-individual-users-password-to-never-expire"></a>تعيين كلمة مرور مستخدم فردية على ألا تنتهي صلاحيتها أبدا

تشرح هذه المقالة كيفية تعيين كلمة مرور لمستخدم فردي حتى لا تنتهي صلاحيتها. يجب عليك إكمال هذه الخطوات باستخدام PowerShell.

## <a name="before-you-begin"></a>قبل البدء

هذه المقالة مخصصة للأشخاص الذين يقومون بتعيين نهج انتهاء صلاحية كلمة المرور للأعمال أو المؤسسة التعليمية أو المؤسسات غير الربحية. لإكمال هذه الخطوات، تحتاج إلى تسجيل الدخول باستخدام حساب مسؤول Microsoft 365. راجع [نظرة عامة على مركز مسؤولي Microsoft 365](/microsoft-365/admin/admin-overview/admin-center-overview).

يجب أن تكون [مسؤولا عموميا أو مسؤول كلمة مرور](about-admin-roles.md) لتنفيذ هذه الخطوات.

يمكن للمسؤول العام لخدمة سحابة Microsoft استخدام [Azure Active Directory PowerShell ل Graph](/powershell/azure/active-directory/install-adv2) لتعيين كلمات المرور التي لا تنتهي صلاحيتها لمستخدمين محددين. يمكنك أيضا استخدام [أوامر cmdlets AzureAD](/powershell/module/Azuread) لإزالة التكوين الذي لا تنتهي صلاحيته أبدا أو لمعرفة كلمات مرور المستخدم التي تم تعيينها على عدم انتهاء صلاحيتها أبدا.

ينطبق هذا الدليل على موفرين آخرين، مثل Intune وMicrosoft 365، الذين يعتمدون أيضا على Azure AD لخدمات الهوية والدليل. انتهاء صلاحية كلمة المرور هو الجزء الوحيد من النهج الذي يمكن تغييره.

## <a name="how-to-check-the-expiration-policy-for-a-password"></a>كيفية التحقق من نهج انتهاء الصلاحية لكلمة مرور

لمزيد من المعلومات حول الأمر Get-AzureADUser في الوحدة النمطية AzureAD، راجع المقالة المرجعية [Get-AzureADUser](/powershell/module/Azuread/Get-AzureADUser).

تشغيل أحد الأوامر التالية:

- لمعرفة ما إذا تم تعيين كلمة مرور مستخدم واحد إلى عدم انتهاء صلاحيتها، قم بتشغيل cmdlet التالي باستخدام UPN (على سبيل المثال، *user@contoso.onmicrosoft.com*) أو معرف المستخدم للمستخدم الذي تريد التحقق منه:

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

- لمشاهدة إعداد **كلمة المرور التي لا تنتهي صلاحيتها لجميع** المستخدمين، قم بتشغيل cmdlet التالي:

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
     }
    ```

- للحصول على تقرير لكافة المستخدمين الذين لديهم PasswordNeverExpires في Html على سطح المكتب للمستخدم الحالي الذي يحمل الاسم  **ReportPasswordNeverExpires.html**

    ```powershell
    Get-AzureADUser -All $true | Select-Object UserprincipalName,@{
        N="PasswordNeverExpires";E={$_.PasswordPolicies -contains "DisablePasswordExpiration"}
    } | ConvertTo-Html | Out-File $env:userprofile\Desktop\ReportPasswordNeverExpires.html
    ```

- للحصول على تقرير لكافة المستخدمين الذين لديهم PasswordNeverExpires في CSV على سطح المكتب للمستخدم الحالي الذي يحمل الاسم **ReportPasswordNeverExpires.csv**

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

- لتعيين كلمات المرور لجميع المستخدمين في المؤسسة على ألا تنتهي صلاحيتها أبدا، قم بتشغيل cmdlet التالي:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies DisablePasswordExpiration
    ```

> [!WARNING]
> لا تزال حسابات المستخدمين التي تم تكوينها مع المعلمة `-PasswordPolicies DisablePasswordExpiration` في العمر استنادا إلى السمة `pwdLastSet` . استنادا إلى السمة `pwdLastSet` ، إذا قمت بتغيير انتهاء الصلاحية إلى `-PasswordPolicies None`، تتطلب جميع كلمات المرور التي تحتوي على pwdLastSet أقدم من 90 يوما من المستخدم تغييرها في المرة التالية التي يسجل فيها الدخول. يمكن أن يؤثر هذا التغيير على عدد كبير من المستخدمين.

### <a name="set-a-password-to-expire"></a>تعيين كلمة مرور لتنتهي صلاحيتها

تشغيل أحد الأوامر التالية:

- لتعيين كلمة مرور مستخدم واحد بحيث تنتهي صلاحية كلمة المرور، قم بتشغيل cmdlet التالي باستخدام UPN أو معرف المستخدم للمستخدم:

    ```powershell
    Set-AzureADUser -ObjectId <user ID> -PasswordPolicies None
    ```

- لتعيين كلمات المرور لكافة المستخدمين في المؤسسة بحيث تنتهي صلاحيتها، استخدم cmdlet التالي:

    ```powershell
    Get-AzureADUser -All $true | Set-AzureADUser -PasswordPolicies None
    ```

## <a name="related-content"></a>المحتويات ذات الصلة

[السماح للمستخدمين بإعادة تعيين كلمات المرور الخاصة بهم](../add-users/let-users-reset-passwords.md) (المقالة)\
[إعادة تعيين كلمات المرور](../add-users/reset-passwords.md) (مقالة)\
[تعيين نهج انتهاء صلاحية كلمة المرور لمؤسستك](../manage/set-password-expiration-policy.md) (مقالة)
