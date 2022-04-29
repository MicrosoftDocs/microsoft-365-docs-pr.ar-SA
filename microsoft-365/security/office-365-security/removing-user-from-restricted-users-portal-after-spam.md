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
description: يمكن للمسؤولين معرفة كيفية إزالة المستخدمين من صفحة المستخدمين المقيدين في مدخل Microsoft 365 Defender. تتم إضافة المستخدمين إلى مدخل المستخدمين المقيدين لإرسال البريد العشوائي الصادر، عادة نتيجة اختراق الحساب.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 229dfbb7a0441f4a6cb6632432c0032f4ce4308e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130725"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>إزالة المستخدمين المحظورين من مدخل المستخدمين المقيدين في Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

إذا تجاوز المستخدم أحد حدود الإرسال الصادرة كما هو محدد في [حدود الخدمة](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) أو في [نهج البريد العشوائي الصادرة](configure-the-outbound-spam-policy.md)، يتم تقييد المستخدم من إرسال البريد الإلكتروني، ولكن لا يزال بإمكانه تلقي البريد الإلكتروني.

تتم إضافة المستخدم إلى صفحة **"المستخدمون المقيدون**" في مدخل Microsoft 365 Defender. عندما يحاولون إرسال بريد إلكتروني، يتم إرجاع الرسالة في تقرير بعدم التسليم (المعروف أيضا باسم NDR أو رسالة إعلام البريد المرتد) مع رمز الخطأ [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) والنص التالي:

> "تعذر تسليم رسالتك لأنه لم يتم التعرف عليك كمرسل صالح. السبب الأكثر شيوعا لذلك هو أن عنوان البريد الإلكتروني الخاص بك مشتبه في إرسال البريد العشوائي ولم يعد مسموحا له بإرسال البريد الإلكتروني.  اتصل بمسؤول البريد الإلكتروني للحصول على المساعدة. أرجع Remote Server '550 5.1.8 Access مرفوض، مرسل صادر غير صالح."

يمكن للمسؤولين إزالة المستخدمين من صفحة **"المستخدمون المقيدون**" في Microsoft 365 Defender أو في Exchange Online PowerShell.

## <a name="learn-more-on-restricted-entities"></a>معرفة المزيد حول الكيانات المقيدة

الكيان المقيد هو كيان تم حظره من إرسال البريد الإلكتروني إما لأنه قد تم اختراقه أو تجاوز حد الإرسال.

هناك نوعان من الكيانات المقيدة: 

- **المستخدم المقيد**: تعرف على سبب تقييد المستخدم وكيفية التعامل مع المستخدمين المقيدين (هذه المقالة).  

- **الموصل المقيد**: لمزيد من المعلومات حول سبب تقييد الموصل وكيفية التعامل مع الموصلات المقيدة، راجع [إزالة الموصلات المحظورة من مدخل الكيانات المقيدة](remove-blocked-connectors.md). 

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **"المستخدمون المقيدون** "، استخدم <https://security.microsoft.com/restrictedusers>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يجب تعيين أذونات لك في **Exchange Online** قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لإزالة المستخدمين من مدخل المستخدمين المقيدين، يجب أن تكون عضوا في مجموعات دور مسؤول **الأمان** أو **إدارة المؤسسة**.
  - للوصول للقراءة فقط إلى مدخل المستخدمين المقيدين، يجب أن تكون عضوا في مجموعات دور **القارئ العمومي** أو **قارئ الأمان** .

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات _والأذونات_ المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  >
  > - كما توفر مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) إمكانية الوصول للقراءة فقط إلى الميزة.

- يعد المرسل الذي يتجاوز حدود البريد الإلكتروني الصادر مؤشرا لحساب تم اختراقه. قبل إزالة المستخدم من مدخل المستخدمين المقيدين، تأكد من اتباع الخطوات المطلوبة لاستعادة التحكم في حسابه. لمزيد من المعلومات، راجع [الاستجابة إلى حساب بريد إلكتروني تم اختراقه في Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>استخدام مدخل Microsoft 365 Defender لإزالة مستخدم من قائمة المستخدمين المقيدين

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **تعاون** \> البريد الإلكتروني & **مراجعة** \> **المستخدمين المقيدين**. للانتقال مباشرة إلى صفحة **"المستخدمون المقيدون** "، استخدم <https://security.microsoft.com/restrictedusers>.

2. في صفحة **"المستخدمون المقيدون** "، ابحث عن المستخدم الذي تريد إلغاء حظره وحدده بالنقر فوق المستخدم.

3. انقر فوق الإجراء **"إلغاء الحظر"** الذي يظهر.

4. في القائمة المنبثقة **"إلغاء حظر المستخدم** " التي تظهر، اقرأ التفاصيل حول الحساب المقيد. يجب عليك الاطلاع على التوصيات للتأكد من أنك تتخذ الإجراءات المناسبة في حالة اختراق الحساب.

   عند الانتهاء، انقر فوق **"التالي**".

5. تحتوي الشاشة التالية على توصيات للمساعدة في منع الاختراق في المستقبل. تمكين المصادقة متعددة العوامل (MFA) وإعادة تعيين كلمة المرور هي دفاع جيد.

   عند الانتهاء، انقر فوق **"إرسال**".

6. انقر فوق **"نعم** " لتأكيد التغيير.

   > [!NOTE]
   > قد يستغرق الأمر ما يصل إلى ساعة واحدة لإزالة جميع القيود من المستخدم.

## <a name="verify-the-alert-settings-for-restricted-users"></a>التحقق من إعدادات التنبيه للمستخدمين المقيدين

سيعلم نهج التنبيه الافتراضي **المسمى المستخدم المقيد من إرسال البريد الإلكتروني** المسؤولين تلقائيا عند حظر المستخدمين من إرسال البريد الصادر. يمكنك التحقق من هذه الإعدادات وإضافة مستخدمين إضافيين لإعلامهم. لمزيد من المعلومات حول نهج التنبيه، راجع [نهج التنبيه في Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> لكي تعمل التنبيهات، يجب تشغيل البحث في سجل التدقيق. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **& نهج** \> **التنبيه**. للانتقال مباشرة إلى صفحة **نهج التنبيه** ، استخدم <https://security.microsoft.com/alertpolicies>.

2. في صفحة **نهج التنبيه** ، ابحث عن التنبيه المسمى **User مقيدا من إرسال البريد الإلكتروني وحدده**. يمكنك فرز النهج حسب الاسم، أو استخدام مربع **البحث** للعثور على النهج.

3. في **المستخدم المقيد من إرسال القائمة المنبثقة للبريد الإلكتروني** التي تظهر، تحقق من الإعدادات التالية أو قم بتكوينها:
   - **الحالة**: تحقق من تشغيل ![تشغيل التنبيه.](../../media/scc-toggle-on.png)
   - **مستلمو البريد الإلكتروني**: انقر فوق **"تحرير"** وتحقق من الإعدادات التالية أو قم بتكوينها في القائمة المنبثقة **"تحرير المستلمين** " التي تظهر:
     - **إرسال إعلامات بالبريد الإلكتروني**: تحقق من تحديد هذا الخيار (**تشغيل**).
     - **مستلمو البريد الإلكتروني**: القيمة الافتراضية هي **TenantAdmins** (بمعنى، أعضاء **المسؤول العمومي** ). لإضافة المزيد من المستلمين، انقر في منطقة فارغة من المربع. ستظهر قائمة بالمستلمين، ويمكنك البدء بكتابة اسم لتصفية المستلم وتحديده. يمكنك إزالة مستلم موجود من المربع بالنقر فوق أيقونة " ![إزالة".](../../media/m365-cc-sc-remove-selection-icon.png) بجوار أسمائهم.
     - **حد الإعلامات اليومية**: القيمة الافتراضية **ليست حدا** ولكن يمكنك تحديد حد أقصى لعدد الإعلامات في اليوم.

     عند الانتهاء، انقر فوق **حفظ**.

4. مرة أخرى على **المستخدم المقيد من إرسال القائمة المنبثقة للبريد الإلكتروني** ، انقر فوق **"إغلاق**".

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>استخدام Exchange Online PowerShell لعرض المستخدمين وإزالتها من قائمة المستخدمين المقيدين

لعرض قائمة المستخدمين المحظورين من إرسال البريد الإلكتروني، قم بتشغيل الأمر التالي:

```powershell
Get-BlockedSenderAddress
```

لعرض تفاصيل حول مستخدم معين، استبدله \<emailaddress\> بعنوان بريده الإلكتروني وقم بتشغيل الأمر التالي:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

لإزالة مستخدم من قائمة المستخدمين المقيدين، استبدله \<emailaddress\> بعنوان بريده الإلكتروني ثم قم بتشغيل الأمر التالي:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
