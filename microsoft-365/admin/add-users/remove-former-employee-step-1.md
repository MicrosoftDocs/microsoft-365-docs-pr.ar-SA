---
title: الخطوة 1 - منع موظف سابق من تسجيل الدخول وحظر الوصول إلى Microsoft 365 الخدمات
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
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: حظر موظف سابق من تسجيل الدخول وحظر الوصول Microsoft 365 الخدمات.
ms.openlocfilehash: abd6a6f47952b5af190b08f1ecae337840eaa312
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63574292"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>الخطوة 1 - منع موظف سابق من تسجيل الدخول وحظر الوصول إلى Microsoft 365 الخدمات

إذا كنت بحاجة إلى منع وصول المستخدم إلى تسجيل الدخول مباشرة، يجب إعادة تعيين كلمة المرور الخاصة به. في هذه الخطوة، اجبر المستخدم على الخروج من Microsoft 365.

> [!NOTE]
> يجب أن تكون مسؤولا عاما لبدء تسجيل الخروج لمسؤولين آخرين. بالنسبة للمستخدمين غير المسؤولين، يمكنك استخدام مسؤول مستخدم أو مستخدم مسؤول تعليمات لتنفيذ هذا الإجراء. [تعرف على المزيد حول أدوار المسؤولين](about-admin-roles.md)

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .
2. حدد المربع بجانب اسم المستخدم، ثم حدد **إعادة تعيين كلمة المرور**.
3. أدخل كلمة مرور جديدة، ثم حدد **إعادة تعيين**. (لا ترسله إليهم.)
4. حدد اسم المستخدم للذهاب إلى جزء الخصائص الخاص به، وعلى علامة التبويب حساب، حدد **تسجيل الخروج من كل جلسات العمل**.

في غضون ساعة - أو بعد مغادرة الصفحة الحالية Microsoft 365 الموجودة عليها - سيطلب منه تسجيل الدخول مرة أخرى. رمز الوصول المميز جيد لمدة ساعة، لذلك يعتمد المخطط الزمني على الوقت المتبقى على هذا الرمز المميز، وما إذا كان سيتنقل خارج صفحة الويب الحالية الخاصة به.
  
> [!IMPORTANT]
> إذا كان المستخدم في Outlook على ويب، ما عليك سوى النقر فوق علبة البريد الخاصة به، فقد لا يتم تهييأ له على الفور. بمجرد تحديد لوحة مختلفة، مثل OneDrive أو تحديث المستعرض، يتم بدء تسجيل الخروج.
  
لاستخدام PowerShell لتوقيع اسم مستخدم على الفور، راجع [الأمر Cmdlet Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
للحصول على مزيد من المعلومات حول المدة التي تستغرقها عملية تخلص شخص ما من البريد الإلكتروني، راجع ما تحتاج إلى معرفته حول إنهاء جلسة عمل البريد الإلكتروني [لأحد الموظفين](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>حظر وصول موظف سابق إلى Microsoft 365 الخدمات

> [!IMPORTANT]
 > قد يستغرق حظر حساب ما يصل إلى 24 ساعة حتى يتم التنفيذ. إذا كنت بحاجة إلى منع وصول المستخدم إلى تسجيل الدخول مباشرة، فاتبع الخطوات المذكورة أعلاه ثم أعد تعيين كلمة المرور الخاصة به.

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .
2. حدد اسم الموظف الذي تريد حظره، وحدد رمز حظر **هذا المستخدم** ضمن اسم المستخدم.
3. حدد **حظر المستخدم من تسجيل الدخول**، ثم حدد **حفظ**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>حظر وصول موظف سابق إلى البريد الإلكتروني (Exchange Online)

إذا كان لديك بريد إلكتروني كجزء من اشتراكك في Microsoft 365، ف سجل دخولك إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a> مركز إدارة Exchange واتبع هذه الخطوات لمنع الموظف السابق من الوصول إلى بريده الإلكتروني.
  
1. انتقل إلى Exchange إدارة > **علب** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">بريد المستلمين</a>.
1. حدد علبة بريد المستخدم من القائمة، ثم في جزء *التفاصيل (على* الجانب الأيسر)، حدد إدارة إعدادات تطبيقات البريد **الإلكتروني ضمن** **تطبيقات البريد الإلكتروني**. إيقاف **تشغيل** شريط التمرير لكل الخيارات؛ **الأجهزة المحمولة (Exchange ActiveSync)** **Outlook على ويب** وسطح **المكتب Outlook (MAPI)** وخدمات Exchange الويب و **POP3** و **IMAP**. 
1. حدد **حفظ**.

## <a name="related-content"></a>المحتوى ذي الصلة

[Exchange مركز الإدارة في Exchange Online](/exchange/exchange-admin-center) (مقالة)\

[استعادة مستخدم](restore-user.md) (مقالة)
