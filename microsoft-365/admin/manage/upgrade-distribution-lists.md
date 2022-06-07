---
title: ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Exchange Online
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: تعرف على كيفية ترقية قائمة توزيع واحدة أو أكثر إلى مجموعات Microsoft 365 في Exchange Online، وكيفية استخدام PowerShell لترقية العديد من قوائم التوزيع في وقت واحد.
ms.openlocfilehash: 6f27c4a7df345a25f4b5ca7d2a9f2979a97e7c6a
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922164"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-exchange-online"></a>ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Exchange Online

تعد ترقية قائمة توزيع إلى مجموعة Microsoft 365 طريقة رائعة لتحسين ميزات المجموعات وقدراتها في مؤسستك. لمزيد من المعلومات، راجع [لماذا يجب ترقية قوائم التوزيع إلى مجموعات في Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

يمكنك ترقية قوائم التوزيع كل على حدة، أو عدة قوائم في الوقت نفسه. يمكنك استخدام مركز إدارة Exchange (EAC) أو Exchange Online PowerShell.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups"></a>ترقية مجموعة واحدة أو أكثر من مجموعات قوائم التوزيع إلى مجموعات Microsoft 365

يجب أن تكون مسؤولا عموميا أو مسؤول Exchange لترقية قائمة توزيع. للترقية إلى مجموعات Microsoft 365، يجب أن يكون لقائمة التوزيع مالك معين، ويجب أن يكون هذا المالك علبة بريد.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>استخدام EAC الكلاسيكي لترقية مجموعة واحدة أو أكثر من مجموعات قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook

> [!NOTE]
> الإجراءات الواردة في هذا القسم غير متوفرة في EAC الجديد.

1. انتقل إلى مركز إدارة Exchange > <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**مجموعات**</a> **المستلمين**\>.

   سترى إشعارا يشير إلى أن لديك قوائم توزيع (تسمى أيضا **مجموعات التوزيع**) مؤهلة للترقية إلى مجموعات Microsoft 365.
   
   ![حدد الزر "بدء الاستخدام".](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. حدد قائمة توزيع واحدة أو أكثر (تسمى أيضا **مجموعات التوزيع**) من صفحة **المجموعات** .

   ![حدد مجموعة توزيع.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. حدد أيقونة الترقية.

   ![الترقية إلى أيقونة مجموعات Microsoft 365.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. في مربع حوار المعلومات، حدد **"نعم** " لتأكيد الترقية. تبدأ العملية على الفور. اعتمادا على حجم وعدد مضاءات التوزيع التي تقوم بترقيةها، يمكن أن تستغرق العملية دقائق أو ساعات.

   إذا تعذرت ترقية قائمة التوزيع، فسيظهر مربع حوار يقول ذلك. هل تعرف على [قوائم التوزيع التي لا يمكن ترقيتها؟](#which-distribution-lists-cant-be-upgraded).

1. إذا كنت تقوم بترقية قوائم توزيع متعددة، فاستخدم القائمة المنسدلة لتصفية قوائم التوزيع التي تمت ترقيتها. إذا لم تكتمل القائمة، فانتظر لفترة أطول ثم حدد **"تحديث** " لمعرفة ما تمت ترقيته بنجاح.

**الملاحظات**:

- لن تتلقى إعلاما عند اكتمال الترقيات. بدلا من ذلك، راجع ما هو مدرج ضمن **"متوفر" للترقية** أو **قوائم DLs التي تمت ترقيتها**.

- إذا قمت بتحديد قائمة توزيع للترقية، ولكنها لا تزال تظهر على الصفحة على أنها **متوفرة للترقية**، فقد فشلت الترقية. اطلع [على ما يجب فعله إذا لم تعمل الترقية](#what-to-do-if-the-upgrade-doesnt-work).

- قد يعرض البريد الإلكتروني الملخص لمجموعة ما السماح لك بترقية أي قوائم توزيع مؤهلة تكون مالكها. لمزيد من المعلومات حول ملخص البريد الإلكتروني، راجع [إجراء محادثة جماعية في Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22).

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>ما يجب فعله إذا لم تعمل الترقية

تظل قوائم التوزيع التي تفشل في الترقية دون تغيير.

إذا فشلت ترقية قائمة توزيع **مؤهلة** واحدة أو أكثر، فقم بالخطوات التالية:

1. استخدم [هذا البرنامج النصي](https://aka.ms/DLToM365Group) للبحث عن المشكلات المحتملة. قم بإصلاح أي مشاكل تم الإبلاغ عنها بواسطة البرنامج النصي وحاول ترقية قائمة التوزيع مرة أخرى. 

2. إذا لم يساعدك البرنامج النصي، فافتح [تذكرة دعم](../../business-video/get-help-support.md). يجب تصعيد المشكلة إلى فريق هندسة المجموعات.

## <a name="how-to-use-exchange-online-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>كيفية استخدام Exchange Online PowerShell لترقية العديد من قوائم التوزيع في الوقت نفسه

للاتصال ب Exchange Online PowerShell، راجع [Connect to Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="upgrade-a-single-distribution-list"></a>ترقية قائمة توزيع واحدة

لترقية قائمة توزيع واحدة، استخدم بناء الجملة التالي:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress>
```

هذا المثال ترقية قائمة التوزيع marketing@contoso.com:

```PowerShell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

> [!NOTE]
> يمكنك أيضا ترقية قائمة توزيع واحدة إلى مجموعة Microsoft 365 باستخدام [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) cmdlet.

### <a name="upgrade-multiple-distribution-lists-at-the-same-time"></a>ترقية قوائم توزيع متعددة في الوقت نفسه

لترقية قوائم توزيع متعددة في الوقت نفسه، استخدم بناء الجملة التالي:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress1>,<EmailAddress2>,...
```

يقوم هذا المثال بترقية قوائم التوزيع المحددة إلى مجموعات Microsoft 365.

```powershell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com,finanace@contoso.com,hr@contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

### <a name="upgrade-all-eligible-distribution-lists"></a>ترقية كافة قوائم التوزيع المؤهلة

استخدم أيا من الأسلوبين التاليين لترقية كافة قوائم التوزيع المؤهلة إلى مجموعات Microsoft 365:

- ترقية كافة قوائم التوزيع المؤهلة:

   ```PowerShell
   $All = Get-EligibleDistributionGroupForMigration -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

- حاول ترقية جميع قوائم التوزيع سواء كانت مؤهلة أم لا:

   ```PowerShell
   $All Get-DistributionGroup -RecipientTypeDetails MailUniversalDistributionGroup -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>الأسئلة المتداولة حول ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>ما هي قوائم التوزيع التي لا يمكن ترقيتها؟

يمكنك فقط ترقية قوائم التوزيع المدارة على السحابة والبسيطة وغير المتداخلة. يسرد الجدول أدناه قوائم التوزيع التي **لا** يمكن ترقيتها.

|الخاصيه|المؤهله؟|
|---|:---:|
|قائمة التوزيع المدارة المحلية.|لا|
|قوائم التوزيع المتداخلة. تحتوي قائمة التوزيع على مجموعات تابعة أو عضو في مجموعة أخرى.|لا|
|قوائم التوزيع التي يكون فيها عضو واحد أو أكثر شيئا آخر غير علبة بريد المستخدم أو علبة البريد المشتركة أو علبة بريد الفريق أو مستخدم البريد. بمعنى آخر، قيمة **RecipientTypeDetails** لأي عضو في قائمة التوزيع ليست **UserMailbox** أو **SharedMailbox** أو **TeamMailbox** أو **MailUser**.|لا|
|قائمة التوزيع التي تحتوي على أكثر من 100 مالك.|لا|
|قائمة التوزيع التي تحتوي على أعضاء فقط ولكن ليس لها مالك.|لا|
|قائمة التوزيع التي تحتوي على اسم مستعار يحتوي على أحرف خاصة.|لا|
|تم تكوين قائمة التوزيع لتكون عنوان إعادة توجيه لعلب بريد مشترك.|لا|
|تعد قائمة التوزيع جزءا من **تقييد المرسل** في قائمة توزيع أخرى.|لا|
|مجموعات الأمان الممكنة للبريد.|لا|
|مجموعات التوزيع الديناميكية.|لا|
|قوائم التوزيع التي تم تحويلها إلى **قوائم القاعات**.|لا|

### <a name="check-which-distribution-lists-are-eligible-for-upgrade"></a>التحقق من قوائم التوزيع المؤهلة للترقية

للتحقق مما إذا كانت قائمة توزيع معينة مؤهلة للترقية، قم بتشغيل الأمر التالي:

```PowerShell
Get-DistributionGroup <EmailAddress> | Get-EligibleDistributionGroupForMigration
```

لمشاهدة كافة مجموعات التوزيع المؤهلة للترقية، قم بتشغيل الأمر التالي:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>من يمكنه تشغيل البرامج النصية للترقية؟

الأشخاص الذين معهم حقوق مسؤول عمومي أو مسؤول Exchange.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>لماذا لا تزال بطاقة جهة الاتصال تعرض قائمة توزيع؟ ما الذي يجب فعله لمنع ظهور قائمة توزيع تمت ترقيتها في قائمة الاقتراح التلقائي؟

- **Outlook**: بعد ترقية قائمة ditribution إلى مجموعة Microsoft 365، لا تكون ذاكرة التخزين المؤقت للمستلم المحلي للمستخدم (المعروفة أيضا باسم ذاكرة التخزين المؤقت لاسم الحذف) على علم بالتغيير. نفذ الخطوات الواردة في المقالة التالية لإعادة تعيين ذاكرة التخزين المؤقت للمستلم المحلي للمستخدم: [معلومات حول قائمة الإكمال التلقائي في Outlook](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list). 

  إذا لم تقم بتحديث ذاكرة التخزين المؤقت للمستلمين، فسيتم تسليم أي بريد إلكتروني تم إرساله إلى مجموعة Microsoft 365 بنجاح، ولكن ستظل المشاكل التالية:
  
  - سيتم حل مستلم المجموعة كقوائم توزيع بدلا من مجموعة Microsoft 365.
  - ستكون بطاقة جهة الاتصال جهة اتصال قائمة التوزيع بدلا من مجموعة Microsoft 365.

- **Outlook على الويب**: مثل Outlook، ستبقى قائمة التوزيع في ذاكرة التخزين المؤقت للمستلمين. اتبع الخطوات الواردة في هذه المقالة لتحديث ذاكرة التخزين المؤقت للاطلاع على بطاقة جهة اتصال المجموعة: [قم بإزالة الاسم المقترح أو عنوان البريد الإلكتروني المقترح من قائمة الإكمال التلقائي](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58).

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>هل يحصل أعضاء المجموعة الجدد على بريد إلكتروني ترحيبي في علبة الوارد الخاصة بهم؟

لا. يتم تعيين الإعداد لتمكين رسائل الترحيب إلى خطأ بشكل افتراضي. يؤثر هذا الإعداد على كل من أعضاء المجموعة الحاليين والجديدين الذين قد ينضمون بعد اكتمال الترحيل. إذا سمح مالك المجموعة لاحقا للمستخدمين الضيوف، فلن يتلقى المستخدمون الضيوف بريدا إلكترونيا ترحيبيا في علبة الوارد الخاصة بهم. يمكن للأعضاء الضيوف متابعة العمل مع المجموعة.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>ماذا لو لم تتم ترقية واحد أو بعض DLs؟

هناك بعض الحالات التي لا يمكن فيها ترقية قوائم التوزيع المؤهلة. على سبيل المثال:

- قام مسؤول بتطبيق **نهج عنوان البريد الإلكتروني للمجموعة**، ولا تفي قائمة التوزيع بمتطلبات النهج.

- تحتوي قائمة التوزيع على **MemberJoinRestriction** أو **MemberDepartRestriction** معينة إلى القيمة **مغلقة**.

- إن إنشاء مجموعة Microsoft 365 محدود كما هو موضح في هذه المقالة: [هذه المقالة](/microsoft-365/solutions/manage-creation-of-groups).

  استخدم أحد الحلول البديلة التالية لهذه المشكلة المحددة:

  - تأكد من السماح لكافة مالكي قائمة التوزيع بإنشاء مجموعات Microsoft 365 (أي أن المالكين هم أعضاء في مجموعة الأمان المسموح لها بإنشاء مجموعات Microsoft 365).

  - استبدل مالك قائمة التوزيع مؤقتا بمستخدم يسمح له بإنشاء مجموعات Microsoft 365.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>ماذا يحدث ل DL إذا فشلت الترقية من EAC؟

لن تحدث الترقية إلا عند إرسال المكالمة إلى الخادم. إذا فشلت الترقية، فستبقى قوائم التوزيع الخاصة بك وتعمل كما كانت.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>ماذا يحدث لإعدادات الموافقة على الرسائل (الإشراف) على مجموعات التوزيع بعد الترقية؟

يتم الاحتفاظ بإعدادات الموافقة على الرسائل (الإشراف) والاستمرار في العمل بشكل جيد بعد ترقية مجموعة التوزيع إلى مجموعة Microsoft 365.

## <a name="related-content"></a>المحتويات ذات الصلة

[مقارنة المجموعات](../create-groups/compare-groups.md) (مقالة)\
[شرح مجموعات Microsoft 365 للمستخدمين](../create-groups/explain-groups-knowledge-worker.md) (المقالة)\
[إضافة أعضاء أو إزالتهم من مجموعات Microsoft 365 باستخدام مركز الإدارة](../create-groups/add-or-remove-members-from-groups.md)
