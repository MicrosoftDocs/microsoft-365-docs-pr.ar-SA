---
title: حماية مجموعة c-suite الخاصة بك باستخدام حماية الحساب ذات الأولوية في Microsoft Defender لـ Office 365 الخطة 2
description: خطوات حماية مجموعة c-suite الخاصة بك مع حماية الحساب ذات الأولوية. سيؤدي وضع علامة على حساب كحساب أولوية إلى تمكين الحماية الإضافية التي تم ضبطها لأنماط تدفق البريد التي تستهدف المديرين التنفيذيين للشركة، بالإضافة إلى رؤية إضافية في التقارير والتنبيهات والتحقيقات.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 3670d4c1c55cbaaab739a8de2df359f06b53ae80
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842351"
---
# <a name="protect-your-c-suite-with-priority-account-protection"></a>حماية مجموعة c-suite الخاصة بك مع حماية الحساب ذات الأولوية

تساعد حماية الحساب ذات الأولوية فرق تكنولوجيا المعلومات والأمان على ضمان جودة عالية للخدمة والحماية للأشخاص المهمين داخل مؤسستك. سيؤدي وضع علامة على حساب كحساب ذي أولوية إلى تمكين الحماية الإضافية التي تم ضبطها لأنماط تدفق البريد التي تستهدف المديرين التنفيذيين للشركة، بالإضافة إلى رؤية إضافية في التقارير والتنبيهات والتحقيقات.

## <a name="what-youll-need"></a>ما ستحتاج إليه
- Microsoft Defender لـ Office 365 الخطة 2 (المضمنة كجزء من خطط E5)
- أذونات كافية (دور مسؤول الأمان)
- 5 دقائق لتنفيذ الخطوات أدناه.

## <a name="tag-priority-users"></a>وضع علامة على مستخدمي الأولوية
1. حدد المستخدمين أو المجموعات أو المجالات التي تريد وضع علامة عليها كحسابات ذات أولوية.
1. سجل الدخول إلى [مدخل أمان Microsoft](https://security.microsoft.com/) وانتقل إلى الإعدادات على شريط التنقل الأيمن.
1. حدد التعاون & البريد الإلكتروني على الصفحة التي يتم تحميلها ثم انقر فوق علامات المستخدم
1. في صفحة علامات المستخدم، حدد علامة حساب الأولوية واضغط على علامة التحرير
1. في القائمة المنبثقة التي تظهر، حدد "إضافة أعضاء"
1. ابحث عن المستخدمين الذين ترغب في وضع علامة عليهم، وحدد مستخدما واحدا أو أكثر واضغط على "إضافة"
1. راجع الأعضاء الذين حددتهم واضغط على "التالي"
1. اضغط على "إرسال" لتأكيد التغييرات

لمعرفة علامات الحساب ذات الأولوية، راجع [إدارة الحسابات ذات الأولوية ومراقبتها - Microsoft 365 المسؤول | Microsoft Docs](../../../admin/setup/priority-accounts.md).

## <a name="next-steps"></a>الخطوات التالية
[راجع الحماية المميزة للمستخدمين الذين تم وضع علامة عليهم كحسابات ذات أولوية](../../office-365-security/configure-review-priority-account.md).

## <a name="powershell-configuration"></a>تكوين PowerShell
إذا كنت ترغب في تحقيق هذه الخطوات عبر PowerShell، يمكنك القيام بذلك باستخدام أوامر cmdlets التالية:
1. عرض قائمة بحسابات الأولوية: **Get-User -IsVIP | تحديد Identity**
1. إضافة مستخدم إلى قائمة الحسابات ذات الأولوية: **Set-User -VIP:$true -Identity \<Identity\>**
1. إزالة المستخدم من قائمة حسابات الأولوية: **Set-User -VIP:$false -Identity \<Identity\>**
