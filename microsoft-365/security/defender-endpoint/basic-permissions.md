---
title: استخدام الأذونات الأساسية للوصول إلى مركز حماية Microsoft Defender
description: تعرف على كيفية استخدام الأذونات الأساسية للوصول إلى مدخل Microsoft Defender لنقطة النهاية.
keywords: تعيين أدوار المستخدمين وتعيين حق الوصول للقراءة والكتابة وتعيين الوصول للقراءة فقط والمستخدم وأدوار المستخدمين والأدوار
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 27c480a0d4c95e79619e10f8fa42efb2c268b18c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/25/2021
ms.locfileid: "63571435"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>استخدام الأذونات الأساسية للوصول إلى المدخل

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- Azure Active Directory
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-basicaccess-abovefoldlink)

راجع الإرشادات أدناه لاستخدام إدارة الأذونات الأساسية.

يمكنك استخدام أي من الحلول التالية:

- Azure PowerShell
- مدخل Azure

للتحكم في الأذونات، [قم بالتبديل إلى عنصر تحكم الوصول المستند إلى الدور](rbac.md).

## <a name="assign-user-access-using-azure-powershell"></a>تعيين وصول المستخدم باستخدام Azure PowerShell

يمكنك تعيين مستخدمين لديهم أحد مستويات الأذونات التالية:

- الوصول الكامل (قراءة وكتابة)
- الوصول للقراءة فقط

### <a name="before-you-begin"></a>قبل البدء

- تثبيت Azure PowerShell. لمزيد من المعلومات، [راجع كيفية تثبيت Azure PowerShell وتكوينه](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

  > [!NOTE]
  > تحتاج إلى تشغيل أوامر PowerShell cmdlets في سطر أوامر مرتفع.

- الاتصال إلى Azure Active Directory. لمزيد من المعلومات، راجع [الاتصال-MsolService](/powershell/module/msonline/connect-msolservice).

  - **الوصول الكامل**: يمكن للمستخدمين الذين لديهم حق الوصول الكامل تسجيل الدخول وعرض كل معلومات النظام وحل التنبيهات وإرسال الملفات للتحليل العميق وتنزيل حزمة التكامل. يتطلب تعيين حقوق الوصول الكامل إضافة المستخدمين إلى "مسؤول الأمان" أو "المسؤول العام" AAD (دليل Azure النشط) المضمنة.
  - **الوصول للقراءة فقط**: يمكن للمستخدمين الذين لديهم حق الوصول للقراءة فقط تسجيل الدخول وعرض كل التنبيهات والمعلومات ذات الصلة.

    ولن يتمكن من تغيير حالة التنبيه أو إرسال الملفات لتحليلها بعمق أو تنفيذ أي عمليات تغيير حالة.

    يتطلب تعيين حقوق الوصول للقراءة فقط إضافة المستخدمين إلى دور Azure AD المضمن في Azure AD.

استخدم الخطوات التالية لتعيين أدوار الأمان:

- للوصول **إلى القراءة والكتابة** ، قم بتعيين مستخدمين إلى دور مسؤول الأمان باستخدام الأمر التالي:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```

- للوصول **للقراءة فقط** ، قم بتعيين المستخدمين إلى دور قارئ الأمان باستخدام الأمر التالي:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

لمزيد من المعلومات، راجع [إضافة أعضاء المجموعة أو إزالتهم باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

## <a name="assign-user-access-using-the-azure-portal"></a>تعيين وصول المستخدم باستخدام مدخل Azure

لمزيد من المعلومات، راجع تعيين أدوار المسؤولين وغير المسؤولين [للمستخدمين الذين لديهم Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

## <a name="related-topic"></a>موضوع ذو صلة

- [إدارة الوصول إلى المدخل باستخدام RBAC](rbac.md)
