---
title: إيقاف تشغيل متطلبات كلمة المرور القوية للمستخدمين
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
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية تعيين متطلبات كلمة مرور قوية للمستخدمين باستخدام Windows PowerShell.
ms.openlocfilehash: 5932f01c2f17a72f4f6a20a6457d263bed7dd85e
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63572959"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>إيقاف تشغيل متطلبات كلمة المرور القوية للمستخدمين

تشرح هذه المقالة كيفية إيقاف تشغيل متطلبات كلمة المرور القوية للمستخدمين. يتم تشغيل متطلبات كلمة المرور القوية بشكل افتراضي في Microsoft 365 للأعمال. قد تحتاج مؤسستك إلى متطلبات لتعطيل كلمات مرور قوية. اتبع الخطوات أدناه ل إيقاف تشغيل متطلبات كلمة المرور القوية. يجب عليك إكمال هذه الخطوات باستخدام PowerShell.

## <a name="before-you-begin"></a>قبل البدء

هذه المقالة للأشخاص الذين يديرون نهج كلمة المرور الخاصة بأعمال أو مؤسسة تعليمية أو مؤسسة غير ربحية. لإكمال هذه الخطوات، تحتاج إلى تسجيل الدخول باستخدام حساب المسؤول Microsoft 365 الخاص بك. [ما هو حساب المسؤول؟] (نظرة عامة على مركز مسؤولي Microsoft 365](.. /admin-overview/admin-center-overview.md) يجب أن تكون مسؤولا عاما أو مسؤول كلمة [مرور](about-admin-roles.md) لتنفيذ هذه الخطوات.

يجب أيضا الاتصال Microsoft 365 PowerShell.

## <a name="set-strong-passwords"></a>تعيين كلمات مرور قوية

1. [الاتصال Microsoft 365 باستخدام PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. باستخدام PowerShell، يمكنك إيقاف تشغيل متطلبات كلمة المرور القوية لجميع المستخدمين الذين لديهم الأمر التالي:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> يجب أن يكون userPrincipalName بتنسيق تسجيل الدخول على نمط الإنترنت حيث يكون اسم المستخدم متبوع ب العلامة (@) واسم المجال. على سبيل المثال: user@contoso.com.

## <a name="related-content"></a>المحتوى ذي الصلة

[كيفية الاتصال ب Microsoft 365 PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[مزيد من المعلومات حول أوامر PowerShell MsolUser](/powershell/azure/active-directory/install-adv2)

[مزيد من المعلومات حول نهج كلمة المرور](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
