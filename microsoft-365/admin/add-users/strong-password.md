---
title: إيقاف تشغيل متطلبات كلمات المرور القوية للمستخدمين
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
description: إذا كنت مسؤولا يدير نهج كلمة المرور للأعمال أو المؤسسة التعليمية أو المؤسسات غير الربحية، يمكنك تعيين متطلبات كلمة مرور قوية باستخدام Windows PowerShell.
ms.openlocfilehash: 20bea953207a85b589bf1ae821f988a3cfe8e22c
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436174"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>إيقاف تشغيل متطلبات كلمات المرور القوية للمستخدمين

تشرح هذه المقالة كيفية إيقاف تشغيل متطلبات كلمات المرور القوية للمستخدمين. يتم تشغيل متطلبات كلمة المرور القوية بشكل افتراضي في مؤسسة Microsoft 365 للأعمال. قد يكون لدى مؤسستك متطلبات لتعطيل كلمات المرور القوية. اتبع الخطوات أدناه لإيقاف تشغيل متطلبات كلمة المرور القوية. يجب عليك إكمال هذه الخطوات باستخدام PowerShell.

## <a name="before-you-begin"></a>قبل البدء

هذه المقالة مخصصة للأشخاص الذين يديرون نهج كلمة المرور للأعمال أو المؤسسة التعليمية أو المؤسسات غير الربحية. لإكمال هذه الخطوات، تحتاج إلى تسجيل الدخول باستخدام حساب مسؤول Microsoft 365. [ما هو حساب المسؤول؟] (نظرة عامة على مركز مسؤولي Microsoft 365](.. /نظرة عامة على المسؤول/admin-center-overview.md) يجب أن تكون [مسؤولا عموميا أو مسؤول كلمة مرور](about-admin-roles.md) لتنفيذ هذه الخطوات.

يجب عليك أيضا الاتصال Microsoft 365 باستخدام PowerShell.

## <a name="set-strong-passwords"></a>تعيين كلمات مرور قوية

1. [الاتصال إلى Microsoft 365 باستخدام PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. باستخدام PowerShell، يمكنك إيقاف تشغيل متطلبات كلمة المرور القوية لجميع المستخدمين باستخدام الأمر التالي:

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> يجب أن يكون userPrincipalName بتنسيق تسجيل الدخول بنمط إنترنت حيث يتبع اسم المستخدم علامة (@) واسم المجال. على سبيل المثال: user@contoso.com.

## <a name="related-content"></a>المحتويات ذات الصلة

[كيفية الاتصال Microsoft 365 باستخدام PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[مزيد من المعلومات حول أوامر PowerShell MsolUser](/powershell/azure/active-directory/install-adv2)

[مزيد من المعلومات حول نهج كلمة المرور](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
