---
title: منح المستخدمين حق الوصول إلى مركز & الأمان
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
ms.localizationpriority: medium
ms.collection: Strat_O365_IP
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: يجب تعيين أذونات للمستخدمين في Microsoft 365 الأمان & التوافق قبل أن يتمكنوا من إدارة أي من ميزات الأمان أو التوافق الخاصة به.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2dcab8a14df6266bea87b3ae876ed9bac8eea1d7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566925"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>منح المستخدمين حق الوصول إلى مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يجب تعيين أذونات للمستخدمين في مركز التوافق & الأمان قبل أن يتمكنوا من إدارة أي من ميزات الأمان أو التوافق الخاصة به. بصفتك مسؤول عام أو عضوا في مجموعة دور إدارة المؤسسة في مركز التوافق & الأمان، يمكنك منح هذه الأذونات للمستخدمين. لن يتمكن المستخدمون إلا من إدارة ميزات الأمان أو التوافق التي تمنحهم حق الوصول إليها.

لمزيد من المعلومات حول الأذونات المختلفة التي يمكنك منحها للمستخدمين في مركز التوافق & الأمان، راجع الأذونات في مركز التوافق & [الأمان](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يجب أن تكون مسؤول عام أو عضوا في مجموعة دور إدارة المؤسسة في مركز التوافق & الأمان، لإكمال الخطوات في هذه المقالة.

- قد يكون لمجموعات الدور & مركز التوافق أسماء مماثلة لمجموعات الدور في Exchange Online، ولكنها ليست نفسها.

- لا يتم مشاركة عضوية مجموعة الدور بين Exchange Online مركز التوافق & الأمان.

- لا يمكن لشركاء إذن الوصول المفوض (DAP) مع إدارة نيابة عن (AOBO) الوصول إلى مركز التوافق & الأمان.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>استخدام مركز & الأمان لإعطاء مستخدم آخر حق الوصول إلى مركز التوافق & الأمان

1. افتح مركز & الأمان في <https://protection.office.com> ، ثم انتقل إلى **الأذونات**. الانتقال مباشرة إلى علامة التبويب **أذونات** ، افتح <https://protection.office.com/permissions>.

2. من قائمة مجموعات الدور، اختر مجموعة الدور، ثم انقر فوق **تحرير أيقونة** ![تحرير.](../../media/O365-MDM-CreatePolicy-EditIcon.gif).

3. في صفحة خصائص مجموعة الدور ضمن **الأعضاء،** انقر فوق **أيقونة AddAdd**![.](../../media/ITPro-EAC-AddIcon.gif) وحدد اسم المستخدم (أو المستخدمين) الذي تريد إضافته.

4. عند تحديد جميع المستخدمين الذين تريد إضافتهم إلى مجموعة الدور، انقر فوق **إضافة\>** ثم **موافق**.

5. عند الانتهاء، انقر فوق **حفظ**.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>استخدام ميزة & مركز التوافق PowerShell لإعطاء مستخدم آخر حق الوصول إلى مركز التوافق & الأمان

1. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. استخدم بناء الجملة التالي:

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

للحصول على مشاكل مفصلة في بناء الجملة والمعلمات، راجع [Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>كيف يمكنك معرفة كيفية عمل ذلك؟

للتحقق من أنك منحت حق الوصول إلى مركز التوافق & الأمان، يمكنك تنفيذ أي من الخطوات التالية:

- في مركز & الأمان، انتقل إلى **أذونات** وحدد مجموعة الدور. في مجموعة التفاصيل التي يتم فتحها، تحقق من أعضاء مجموعة الدور.

- في Security & Compliance Center PowerShell \<RoleGroupName\> ، استبدل باسم مجموعة الدور، ثم ادير الأمر التالي:

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).