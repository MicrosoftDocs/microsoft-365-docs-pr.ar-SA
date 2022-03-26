---
title: مزامنة مستخدمي المجال Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: مزامنة المستخدمين الذين يتحكمون بالمجال مع Microsoft 365 للأعمال.
ms.openlocfilehash: e49a3095cff77692e58d1b70ca1169dc8fd4802a
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/25/2022
ms.locfileid: "63571995"
---
# <a name="synchronize-domain-users-to-microsoft-365"></a>مزامنة مستخدمي المجال Microsoft 365

## <a name="1-prepare-for-directory-synchronization"></a>1. التحضير لمزامنة الدليل 

قبل مزامنة المستخدمين وأجهزة الكمبيوتر من مجال Active Directory المحلي، راجع [التحضير لمزامنة](../../enterprise/prepare-for-directory-synchronization.md) الدليل Microsoft 365. بشكل خاص:

   - تأكد من عدم وجود تكرارات في الدليل الخاص بك للخصائص التالية: **البريد** و **proxyAddresses** و **userPrincipalName**. يجب أن تكون هذه القيم فريدة ويجب إزالة أي تكرارات.
   
   - نوصي بتكوين **السمة userPrincipalName** (UPN) لكل حساب مستخدم محلي لمطابقة عنوان البريد الإلكتروني الأساسي الذي يتطابق مع اسم المستخدم Microsoft 365 المرخص. على سبيل *المثال: mary.shelley@contoso.com* بدلا من *mary@contoso.local*
   
   - إذا انتهى مجال Active Directory ب لاحقة غير قابلة التوجيه مثل *.local* أو *.lan*، بدلا من لاحقة قابلة التوجيه عبر الإنترنت مثل *.com* أو *.org*، فاضبط لاحقة UPN الخاصة وحسابات المستخدمين المحلية أولا كما هو موضح في إعداد مجال غير قابل التوجيه لمزامنة [الدليل](../../enterprise/prepare-a-non-routable-domain-for-directory-synchronization.md). 

**سيتأكد أيضا تشغيل IdFix** في الخطوة الرابعة (4) أدناه من أن Active Directory المحلي جاهز لمزامنة الدليل.

## <a name="2-install-and-configure-azure-ad-connect"></a>2. تثبيت Azure AD وتكوينه الاتصال

لمزامنة المستخدمين والمجموعات وجهات الاتصال من Active Directory المحلي إلى Azure Active Directory، قم بتثبيت Azure Active Directory الاتصال إعداد مزامنة الدليل. 

 1. في مركز [الإدارة،](https://go.microsoft.com/fwlink/p/?linkid=2024339) حدد **إعداد** في التنقل الأيسر.

 2. ضمن **تسجيل الدخول والأمان**، حدد **إضافة مستخدمين أو مزامنتهم إلى حساب Microsoft الخاص بك**.

 3. في الصفحة **إضافة مستخدمين إلى حساب Microsoft** أو مزامنتهم، اختر **بدء العمل**.

 4. في الخطوة الأولى، قم بتشغيل أداة IdFix للتحضير لمزامنة الدليل.

 5. اتبع خطوات المعالج لتنزيل Azure AD الاتصال واستخدامه لمزامنة المستخدمين الذين يتم التحكم في مجالهم Microsoft 365.


راجع [إعداد مزامنة الدليل Microsoft 365](../../enterprise/set-up-directory-synchronization.md) لمعرفة المزيد.

أثناء تكوين خيارات Azure AD الاتصال، نوصي بتمكين مزامنة كلمة المرور، تسجيل الدخول المفرد السلس، وميزة كتابة كلمة المرور، والمدعمة أيضا في  Microsoft 365 للأعمال.

> [!NOTE]
> هناك بعض الخطوات الإضافية لكتابة كلمة المرور خارج خانة الاختيار في Azure AD الاتصال. لمزيد من المعلومات، راجع [كيفية: تكوين كتابة كلمة المرور](/azure/active-directory/authentication/howto-sspr-writeback). 

إذا كنت تريد أيضا إدارة أجهزة Windows 10 المنضمة إلى المجال، فا راجع تمكين [](manage-windows-devices.md) أجهزة Windows 10 المنضمة إلى المجال لكي تدار بواسطة Microsoft 365 Business Premium لإعداد Azure AD Join مختلط.
