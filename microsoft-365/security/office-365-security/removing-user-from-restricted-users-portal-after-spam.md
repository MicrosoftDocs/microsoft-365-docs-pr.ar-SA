---
title: إزالة المستخدمين المحظورين من مدخل المستخدمين المقيدين
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.exch.eac.ActionCenter.Restricted.Users.RestrictedUsers
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين التعرف على كيفية إزالة المستخدمين من صفحة المستخدمين المقيدين في Microsoft 365 Defender المدخل. تتم إضافة المستخدمين إلى مدخل المستخدمين المقيدين لإرسال البريد العشوائي الصادر، عادة نتيجة اختراق الحساب.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c375d77c3aa64d996a8d8d2f8dce538829eaa3b2
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568303"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>إزالة المستخدمين المحظورين من مدخل المستخدمين المقيدين في Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

إذا تجاوز المستخدم أحد حدود الإرسال الصادر كما هو محدد في حدود الخدمة أو في سياسات البريد [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) العشوائي الصادر، فيبقى المستخدم [](configure-the-outbound-spam-policy.md)مقيدا من إرسال البريد الإلكتروني، ولكن لا يزال يمكنه تلقي البريد الإلكتروني.

يضاف المستخدم إلى صفحة **المستخدمون** المقيدون في مدخل Microsoft 365 Defender. عندما يحاول إرسال بريد إلكتروني، يتم إرجاع الرسالة في تقرير بعدم التسليم (يعرف أيضا ب NDR أو رسالة البريد المرتد) مع رمز الخطأ [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) والنص التالي:

> "لم يتم تسليم رسالتك لأنه لم يتم التعرف عليك كمرسل صالح. السبب الأكثر شيوعا لذلك هو أن عنوان بريدك الإلكتروني مشتبه في إرسال بريد عشوائي ولم يعد مسموحا له بإرسال البريد الإلكتروني.  اتصل بمسؤول البريد الإلكتروني للحصول على المساعدة. أرجع الخادم البعيد '550 5.1.8 رفض الوصول، مرسل الصادر السيئ"."

يمكن للمسؤولين إزالة المستخدمين من  صفحة المستخدمين المقيدين في Microsoft 365 Defender أو في Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة **المستخدمون المقيدون** ، استخدم <https://security.microsoft.com/restrictedusers>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يجب تعيين أذونات لك في Exchange Online قبل أن تتمكن  من تنفيذ الإجراءات في هذه المقالة:
  - لإزالة مستخدمين من مدخل المستخدمين المقيدين، يجب أن تكون عضوا في مجموعات دور مسؤول إدارة **المؤسسة** **أو مسؤول** الأمان.
  - للوصول للقراءة فقط إلى مدخل المستخدمين المقيدين، يجب أن تكون عضوا في مجموعات دور القارئ العام  أو قارئ الأمان.

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات والأذونات المطلوبة للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  >
  > - توفر **أيضا مجموعة دور "** إدارة [المؤسسات Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) طريقة العرض فقط" إمكانية الوصول للقراءة فقط إلى الميزة.

- إن المرسل الذي يتجاوز حدود البريد الإلكتروني الصادر هو مؤشر على حساب معرر للخطر. قبل إزالة المستخدم من مدخل المستخدمين المقيدين، تأكد من اتباع الخطوات المطلوبة لاستعادة التحكم في حسابه. لمزيد من المعلومات، راجع [الرد على حساب بريد إلكتروني م اختراق في](responding-to-a-compromised-email-account.md) Office 365.

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>استخدام Microsoft 365 Defender لإزالة مستخدم من قائمة المستخدمين المقيدين

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **البريد الإلكتروني** & **مراجعة** \> \> **المستخدمين المقيدين**. الانتقال مباشرة إلى صفحة **المستخدمون المقيدون** ، استخدم <https://security.microsoft.com/restrictedusers>.

2. في صفحة **المستخدمون** المقيدون، ابحث عن المستخدم الذي تريد إلغاء حظره وحدده بالنقر فوق المستخدم.

3. انقر فوق **الإجراء إلغاء الحظر** الذي يظهر.

4. في الأمر **إلغاء حظر المستخدم** الذي يظهر، اقرأ التفاصيل حول الحساب المقيد. يجب عليك الانتقال إلى التوصيات للتأكد من أنك تقوم باتخاذ الإجراءات المناسبة في حالة اختراق الحساب.

   عند الانتهاء، انقر فوق **التالي**.

5. تعرض الشاشة التالية توصيات للمساعدة في منع حدوث اختراق في المستقبل. إن تمكين المصادقة متعددة العوامل (MFA) وإعادة تعيين كلمة المرور هو أمر جيد.

   عند الانتهاء، انقر فوق **إرسال**.

6. انقر **فوق نعم** لتأكيد التغيير.

   > [!NOTE]
   > قد يستغرق الأمر ما يصل إلى ساعة واحدة لإزالة كل القيود من المستخدم.

## <a name="verify-the-alert-settings-for-restricted-users"></a>التحقق من إعدادات التنبيه للمستخدمين المقيدين

يقوم نهج التنبيه الافتراضي المسمى **المستخدم المحظور** من إرسال البريد الإلكتروني بإعلام المسؤولين تلقائيا عندما يتم حظر المستخدمين من إرسال البريد الصادر. يمكنك التحقق من هذه الإعدادات وإضافة مستخدمين إضافيين لإعلامهم. لمزيد من المعلومات حول سياسات التنبيه، راجع [تنبيهات في Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> لكي تعمل التنبيهات، يجب تشغيل البحث في سجل التدقيق. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى البريد الإلكتروني & **نهج التعاون &** \>  \> **نهج التنبيه**. الانتقال مباشرة إلى صفحة **نهج التنبيه** ، استخدم <https://security.microsoft.com/alertpolicies>.

2. في صفحة **نهج التنبيه** ، ابحث عن التنبيه المسمى المستخدم المحظور **من إرسال البريد الإلكتروني وحدده**. يمكنك فرز النهج حسب الاسم، أو استخدام **مربع البحث للعثور** على النهج.

3. في المستخدم **المحظور من إرسال** قائمة البريد الإلكتروني المستعرضة التي تظهر، تحقق من الإعدادات التالية أو قم بتكوينها:
   - **الحالة**: تحقق من تشغيل التنبيه ![إلى تشغيل تشغيل.](../../media/scc-toggle-on.png).
   - **مستلمو البريد** الإلكتروني: انقر فوق **تحرير** الإعدادات التالية أو التحقق منها أو تكوينها في قائمة **تحرير** المستلمين التي تظهر:
     - **إرسال إعلامات بالبريد** الإلكتروني: تحقق من تحديد هذا الأمر (**تشغيل**).
     - **مستلمو البريد** الإلكتروني: القيمة الافتراضية هي **TenantAdmins** (أي أعضاء **المسؤول** العام). لإضافة المزيد من المستلمين، انقر في منطقة فارغة من المربع. ستظهر قائمة بالمستلمين، ويمكن بدء كتابة اسم لتصفية مستلم وتحديده. يمكنك إزالة مستلم موجود من المربع بالنقر فوق أيقونة ![إزالة.](../../media/m365-cc-sc-remove-selection-icon.png) بجانب اسمه.
     - **حد الإعلامات اليومية**: القيمة الافتراضية هي **بلا حد** ولكن يمكنك تحديد حد الحد الأقصى لعدد الإعلامات في اليوم.

     عند الانتهاء، انقر فوق **حفظ**.

4. مرة أخرى على **المستخدم المقيد من إرسال قائمة البريد الإلكتروني** ، انقر فوق **إغلاق**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>استخدام Exchange Online PowerShell لعرض المستخدمين وإزالهم من قائمة المستخدمين المقيدين

لعرض قائمة المستخدمين هذه المحظورين من إرسال البريد الإلكتروني، يمكنك تشغيل الأمر التالي:

```powershell
Get-BlockedSenderAddress
```

لعرض تفاصيل حول مستخدم معين، \<emailaddress\> استبدل عنوان بريده الإلكتروني وبدل الأمر التالي:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-BlockedSenderAddress.](/powershell/module/exchange/get-blockedsenderaddress)

لإزالة مستخدم من قائمة المستخدمين المقيدين، \<emailaddress\> استبدل عنوان بريده الإلكتروني و قم بتشغيل الأمر التالي:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-BlockedSenderAddress.](/powershell/module/exchange/remove-blockedsenderaddress)
