---
title: منح المستخدمين حق الوصول إلى مركز توافق & الأمان
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.PermissionsHelp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: يجب تعيين أذونات للمستخدمين في Microsoft 365 Security & Compliance Center قبل أن يتمكنوا من إدارة أي من ميزات الأمان أو التوافق الخاصة به.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4e0ca3874f03d9f0c386a84c9e8b56ea58bbfe72
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017997"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>منح المستخدمين حق الوصول إلى مركز توافق & الأمان

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يجب تعيين أذونات للمستخدمين في مركز توافق & الأمان قبل أن يتمكنوا من إدارة أي من ميزات الأمان أو التوافق الخاصة به. بصفتك مسؤولا عاما أو عضوا في مجموعة دور OrganizationManagement في مركز توافق & الأمان، يمكنك منح هذه الأذونات للمستخدمين. سيتمكن المستخدمون فقط من إدارة ميزات الأمان أو التوافق التي تمنحهم حق الوصول إليها.

لمزيد من المعلومات حول الأذونات المختلفة التي يمكنك منحها للمستخدمين في مركز التوافق & الأمان، راجع [الأذونات في مركز التوافق & الأمان](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يجب أن تكون مسؤولا عاما، أو عضوا في مجموعة دور OrganizationManagement في مركز التوافق & الأمان، لإكمال الخطوات الواردة في هذه المقالة.

- قد يكون لمجموعات الأدوار لمركز التوافق & الأمان أسماء مشابهة لمجموعات الأدوار في Exchange Online، ولكنها ليست متشابهة.

- لا تتم مشاركة عضويات مجموعة الأدوار بين Exchange Online ومركز توافق & الأمان.

- لا يمكن لشركاء إذن الوصول المفوض (DAP) الذين لديهم أذونات الإدارة نيابة عن (AOBO) الوصول إلى مركز توافق & الأمان.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>استخدام Security & Compliance Center لمنح مستخدم آخر حق الوصول إلى مركز توافق & الأمان

1. افتح مركز التوافق & الأمان في <https://protection.office.com> ثم انتقل إلى **الأذونات**. للانتقال مباشرة إلى علامة التبويب **"أذونات** "، افتح <https://protection.office.com/permissions>.

2. من قائمة مجموعات الأدوار، اختر مجموعة الأدوار، ثم انقر فوق أيقونة **"تحرير**![".](../../media/O365-MDM-CreatePolicy-EditIcon.gif)

3. في صفحة خصائص مجموعة الأدوار ضمن **"الأعضاء**"، انقر فوق **"إضافة**![أيقونة".](../../media/ITPro-EAC-AddIcon.gif) وحدد اسم المستخدم (أو المستخدمين) الذي تريد إضافته.

4. عند تحديد كافة المستخدمين الذين تريد إضافتهم إلى مجموعة الأدوار، انقر فوق **"إضافة"،\>** ثم **"موافق**".

5. عند الانتهاء، انقر فوق **حفظ**.

## <a name="use-security--compliance-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>استخدام Security & Compliance PowerShell لمنح مستخدم آخر حق الوصول إلى Security & Compliance Center

1. [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. استخدم بناء الجملة التالي:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

للحصول على مشاكل مفصلة في بناء الجملة والمعلمة، راجع [Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>كيف تعرف أن هذا يعمل؟

للتحقق من أنك منحت حق الوصول بنجاح إلى مركز توافق & الأمان، قم بأي من الخطوات التالية:

- في مركز التوافق & الأمان، انتقل إلى **الأذونات** وحدد مجموعة الأدوار. في القائمة المنبثقة للتفاصيل التي تفتح، تحقق من أعضاء مجموعة الأدوار.

- في Security & Compliance PowerShell، استبدل \<RoleGroupName\> باسم مجموعة الأدوار، وقم بتشغيل الأمر التالي:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).
