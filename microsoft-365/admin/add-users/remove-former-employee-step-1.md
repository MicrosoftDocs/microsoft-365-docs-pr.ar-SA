---
title: الخطوة 1 - منع موظف سابق من تسجيل الدخول ومنع الوصول إلى خدمات Microsoft 365
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
description: يمكن للمسؤولين العموميين حظر موظف سابق من تسجيل الدخول ومنع وصولهم إلى خدمات Microsoft 365.
ms.openlocfilehash: eec436a182f5e065f445167dea38fe99390ca105
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436636"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>الخطوة 1 - منع موظف سابق من تسجيل الدخول ومنع الوصول إلى خدمات Microsoft 365

إذا كنت بحاجة إلى منع وصول المستخدم إلى تسجيل الدخول على الفور، فيجب عليك إعادة تعيين كلمة المرور الخاصة به. في هذه الخطوة، يجبر المستخدم على الخروج من Microsoft 365.

> [!NOTE]
> يجب أن تكون مسؤولا عاما لبدء تسجيل الخروج للمسؤولين الآخرين. بالنسبة للمستخدمين غير المسؤولين، يمكنك استخدام مسؤول مستخدم أو مستخدم مسؤول Helpdesk لتنفيذ هذا الإجراء. [تعرف على المزيد حول أدوار المسؤولين](about-admin-roles.md)

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>
2. حدد المربع الموجود بجانب اسم المستخدم، ثم حدد **إعادة تعيين كلمة المرور**.
3. أدخل كلمة مرور جديدة، ثم حدد **"إعادة تعيين**". (لا ترسلها إليهم.)
4. حدد اسم المستخدم للانتقال إلى جزء الخصائص الخاص به، ومن علامة التبويب **"حساب** "، حدد **"تسجيل الخروج من كافة جلسات العمل**".

في غضون ساعة - أو بعد مغادرة صفحة Microsoft 365 الحالية التي يستخدمونها - تتم مطالبته بتسجيل الدخول مرة أخرى. يعد رمز الوصول المميز جيدا لمدة ساعة، لذلك يعتمد المخطط الزمني على مقدار الوقت المتبقي على هذا الرمز المميز، وما إذا كان سيتنقل خارج صفحة الويب الحالية.
  
> [!IMPORTANT]
> إذا كان المستخدم في Outlook على ويب، فما عليك سوى النقر فوق علبة البريد الخاصة به، فقد لا يتم إخراجه على الفور. بمجرد تحديد لوحة مختلفة، مثل OneDrive، أو تحديث المستعرض الخاص بهم، يتم بدء تسجيل الخروج.
  
لاستخدام PowerShell لتسجيل الخروج من مستخدم على الفور، راجع [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) cmdlet.
  
لمزيد من المعلومات حول المدة التي يستغرقها إخراج شخص ما من البريد الإلكتروني، راجع [ما تحتاج إلى معرفته حول إنهاء جلسة عمل البريد الإلكتروني لأحد الموظفين](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>حظر وصول موظف سابق إلى خدمات Microsoft 365

> [!IMPORTANT]
 > قد يستغرق حظر الحساب ما يصل إلى 24 ساعة حتى يدخل حيز التنفيذ. إذا كنت بحاجة إلى منع وصول المستخدم إلى تسجيل الدخول على الفور، فاتبع الخطوات المذكورة أعلاه ثم أعد تعيين كلمة المرور الخاصة به.

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>
2. حدد اسم الموظف الذي تريد حظره، وضمن اسم المستخدم، حدد الرمز " **حظر هذا المستخدم**".
3. حدد **"حظر المستخدم" من تسجيل الدخول**، ثم حدد **"حفظ**".

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>حظر وصول موظف سابق إلى البريد الإلكتروني (Exchange Online)

إذا كان لديك بريد إلكتروني كجزء من اشتراكك في Microsoft 365، فسجل دخولك إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> واتبع هذه الخطوات لمنع الموظف السابق من الوصول إلى بريده الإلكتروني.
  
1. انتقل إلى مركز إدارة Exchange > <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">علب بريد</a> **المستلمين**\>.
1. حدد علبة بريد المستخدم من القائمة، ثم في *جزء التفاصيل* (على الجانب الأيمن)، حدد **إدارة إعدادات تطبيقات البريد الإلكتروني** ضمن **تطبيقات البريد الإلكتروني**. **إيقاف** تشغيل شريط التمرير لكافة الخيارات؛ **الأجهزة المحمولة (Exchange ActiveSync)** **Outlook على ويب** **وسطح المكتب Outlook (MAPI)** **وخدمات الويب Exchange** **وPOP3** **وIMAP**.
1. حدد **حفظ**.

## <a name="related-content"></a>المحتويات ذات الصلة

[مركز إدارة Exchange في Exchange Online](/exchange/exchange-admin-center) (مقالة)\

[استعادة مستخدم](restore-user.md) (مقال)
