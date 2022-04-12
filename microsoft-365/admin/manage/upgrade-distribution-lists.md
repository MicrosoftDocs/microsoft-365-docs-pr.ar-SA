---
title: ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook
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
description: تعرف على كيفية ترقية قائمة توزيع واحدة أو أكثر مجموعات Microsoft 365 في Outlook، وكيفية استخدام PowerShell لترقية العديد من قوائم التوزيع في وقت واحد.
ms.openlocfilehash: 832d65854a6a18ad28e3d9fca6d1d11c17146c80
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782248"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook

يمكنك ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook. هذه طريقة رائعة لمنح قوائم التوزيع الخاصة بمؤسستك جميع ميزات ووظائف مجموعات Microsoft 365. [لماذا يجب عليك ترقية قوائم التوزيع إلى مجموعات في Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

يمكنك ترقية DLs كل على حدة، أو عدة في نفس الوقت.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>ترقية مجموعة واحدة أو أكثر من مجموعات قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook

يجب أن تكون مسؤولا عاما أو مسؤول Exchange لترقية مجموعة قائمة توزيع. للترقية إلى مجموعات Microsoft 365، يجب أن يكون لدى مجموعة قائمة التوزيع مالك لديه علبة بريد.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>استخدم EAC الجديد لترقية مجموعة واحدة أو أكثر من مجموعات قوائم التوزيع مجموعات Microsoft 365 في Outlook

1. انتقل إلى مركز إدارة Exchange الجديد > **مجموعات المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

2. حدد مجموعة قائمة التوزيع (تسمى أيضا **مجموعة توزيع**) التي تريد ترقيتها إلى مجموعة Microsoft 365 من صفحة **المجموعات**.

3. حدد **مجموعة توزيع الترقية** من شريط الأدوات.

4. في مربع الحوار " **هل أنت جاهز للترقية؟**"، انقر فوق **"ترقية**". تبدأ العملية على الفور. استنادا إلى حجم مجموعات قوائم التوزيع التي تقوم بترقيةها وعددها، قد تستغرق العملية دقائق أو ساعات.

> [!NOTE]
> يشير شعار في الأعلى إلى الترقية، على سبيل المثال، *تم ترقية مجموعة (مجموعات) التوزيع. سيستغرق الأمر 5 دقائق لعكس التغييرات. قم بالتصفية حسب مجموعات Microsoft 365 لمشاهدة مجموعات (مجموعات) التوزيع التي تمت ترقيتها*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>استخدم EAC الكلاسيكي لترقية مجموعة واحدة أو أكثر من مجموعات قوائم التوزيع مجموعات Microsoft 365 في Outlook

1. انتقل إلى مركز إدارة Exchange > **مجموعات المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>سترى إشعارا يشير إلى أن لديك قوائم توزيع (تسمى أيضا **مجموعات التوزيع**) مؤهلة للترقية إلى مجموعات Microsoft 365.<br/> ![حدد الزر "بدء الاستخدام".](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. حدد قائمة توزيع واحدة أو أكثر (تسمى أيضا **مجموعة توزيع**) من صفحة **المجموعات** .<br/>![حدد مجموعة توزيع.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. حدد أيقونة الترقية.<br/>![الترقية إلى أيقونة مجموعات Microsoft 365.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. في مربع حوار المعلومات، حدد **"نعم** " لتأكيد الترقية. تبدأ العملية على الفور. اعتمادا على حجم وعدد DLs التي تقوم بترقيةها، يمكن أن تستغرق العملية دقائق أو ساعات.<br/>إذا تعذرت ترقية قائمة التوزيع، فسيظهر مربع حوار يقول ذلك. هل تعرف على [قوائم التوزيع التي لا يمكن ترقيتها؟](#which-distribution-lists-cant-be-upgraded).

1. إذا كنت تقوم بترقية قوائم توزيع متعددة، فاستخدم القائمة المنسدلة لتصفية قوائم التوزيع التي تمت ترقيتها. إذا لم تكتمل القائمة، فانتظر لفترة أطول ثم حدد **"تحديث** " لمعرفة ما تمت ترقيته بنجاح.<br/>لا يوجد إشعار يخبرك عند اكتمال عملية الترقية لكافة DLs التي حددتها. يمكنك معرفة ذلك من خلال الاطلاع على ما هو مدرج ضمن **"متوفر" للترقية** أو **عناوين DLs التي تمت ترقيتها**.

1. إذا قمت بتحديد DL للترقية، ولكنه لا يزال يظهر على الصفحة على أنه متوفر للترقية، فقد فشل في الترقية. اطلع [على ما يجب فعله إذا لم تعمل الترقية](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> إذا كنت تقوم بتضمين رسائل البريد الإلكتروني الخاصة بالمجموعات، فقد تلاحظ في الأسفل أنه سيعرض عليك أحيانا ترقية أي قوائم توزيع مؤهلة تكون مالكها. راجع [إجراء محادثة جماعية في Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) للحصول على مزيد من المعلومات حول ملخص رسائل البريد الإلكتروني.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>ما يجب فعله إذا لم تعمل الترقية

تظل قوائم التوزيع التي تفشل في الترقية دون تغيير.

إذا فشلت ترقية قائمة توزيع **مؤهلة** واحدة أو أكثر، 

1. استخدم [هذا البرنامج النصي](https://aka.ms/DLToM365Group) للبحث عن المشاكل المحتملة التي يمكن أن تمنع ترقية قائمة التوزيع إلى مجموعة Microsoft 365 وإصلاح أي مشاكل تم الإبلاغ عنها بواسطة البرنامج النصي ومحاولة ترقية قائمة التوزيع مرة أخرى. 

2. إذا لم يساعد البرنامج النصي أعلاه أو إذا استمرت المشكلة، فافتح [تذكرة دعم](../../business-video/get-help-support.md). يجب تصعيد المشكلة إلى فريق هندسة المجموعات لمعرفة المشكلة.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>كيفية استخدام PowerShell لترقية العديد من قوائم التوزيع في الوقت نفسه

إذا كنت من ذوي الخبرة في استخدام PowerShell، فقد تحتاج إلى الانتقال إلى هذا المسار بدلا من استخدام واجهة المستخدم. لدينا مجموعة من أوامر cmdlets التي ستساعدك على ترقية قوائم التوزيع. انظر أدناه.

### <a name="upgrade-a-single-dl"></a>ترقية DL واحد

لترقية DL واحد، قم بتشغيل الأمر التالي:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

على سبيل المثال، إذا كنت تريد ترقية DL باستخدام عنوان SMTP dl1@contoso.com، فشغل الأمر التالي:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> يمكنك أيضا ترقية قائمة توزيع واحدة إلى مجموعة Microsoft 365 باستخدام [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) PowerShell cmdlet

### <a name="upgrade-multiple-dls-in-a-batch"></a>ترقية عدة DLs في دفعة

يمكنك أيضا تمرير عدة DLs كدفعة وترقيتها معا:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

على سبيل المثال، إذا كنت تريد ترقية خمسة DLs مع عنوان `dl1@contoso.com` SMTP، `dl3@contoso.com`و`dl2@contoso.com`، `dl4@contoso.com` وتشغيل `dl5@contoso.com`الأمر التالي:

```powershell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com
```

### <a name="upgrade-all-eligible-dls"></a>ترقية كافة DLs المؤهلة

هناك طريقتان يمكنك من خلالهما ترقية كافة DLs المؤهلة.

> [!NOTE]
> لا يتلقى Upgrade-DistributionGroup cmdlet البيانات من البنية الأساسية لبرنامج ربط العمليات التجارية، لهذا السبب يلزم استخدام عامل التشغيل "foreach-object{}" للتشغيل بنجاح.

1. الحصول على DLs المؤهلة في المستأجر وترقيتها باستخدام أمر الترقية:

   ```PowerShell
   Get-EligibleDistributionGroupForMigration | Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

2. الحصول على قائمة بكافة DLs وترقية DLs المؤهلة فقط:

   ```PowerShell
   Get-DistributionGroup| Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>الأسئلة المتداولة حول ترقية قوائم التوزيع إلى مجموعات Microsoft 365 في Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>ما هي قوائم التوزيع التي لا يمكن ترقيتها؟

يمكنك فقط ترقية قوائم التوزيع المدارة على السحابة والبسيطة وغير المتداخلة. يسرد الجدول أدناه قوائم التوزيع التي **لا** يمكن ترقيتها.

|الخاصيه|المؤهله؟|
|---|---|
|قائمة التوزيع المدارة المحلية.|لا|
|قوائم التوزيع المتداخلة. تحتوي قائمة التوزيع على مجموعات تابعة أو عضو في مجموعة أخرى.|لا|
|قوائم التوزيع التي تحتوي **على أعضاء RecipientTypeDetails** غير **UserMailbox** **وSharedMailbox** **و TeamMailbox** **وMailUser**|لا|
|قائمة التوزيع التي تحتوي على أكثر من 100 مالك|لا|
|قائمة التوزيع التي تحتوي على أعضاء فقط ولكن بدون مالك|لا|
|قائمة التوزيع التي تحتوي على اسم مستعار يحتوي على أحرف خاصة|لا|
|إذا تم تكوين قائمة التوزيع لتكون عنوان إعادة توجيه لعلبة البريد المشتركة|لا|
|إذا كان DL جزءا من **تقييد المرسل** في DL آخر.|لا|
|مجموعات الأمان|لا|
|قوائم التوزيع الديناميكي|لا|
|قوائم التوزيع التي تم تحويلها إلى **قوائم القاعات**|لا|

### <a name="check-which-dls-are-eligible-for-upgrade"></a>التحقق من عناوين DLs المؤهلة للترقية

إذا كنت تريد التحقق مما إذا كان DL مؤهلا أم لا، يمكنك تشغيل الأمر أدناه:

```PowerShell
Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration
```

إذا كنت تريد التحقق من عناوين DLs المؤهلة للترقية، فما عليك سوى تشغيل الأمر التالي:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>روبوت Who يمكن تشغيل البرامج النصية للترقية؟

الأشخاص الذين يعانون من حقوق المسؤول العام أو Exchange المسؤول.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>لماذا لا تزال بطاقة جهة الاتصال تعرض قائمة توزيع؟ ما الذي يجب فعله لمنع ظهور قائمة توزيع تمت ترقيتها في قائمة الاقتراح التلقائي؟

- على سبيل Outlook: عندما يحاول شخص ما إرسال بريد إلكتروني في Outlook بكتابة اسم مجموعة Microsoft 365 بعد الترحيل، سيتم حل المستلم كقوائم توزيع بدلا من المجموعة. ستكون بطاقة جهة الاتصال الخاصة بالمستلم هي بطاقة جهة اتصال قوائم التوزيع. وذلك بسبب ذاكرة التخزين المؤقت للمستلم أو ذاكرة التخزين المؤقت لاسم Outlook. سيتم إرسال البريد الإلكتروني بنجاح إلى المجموعة، ولكنه قد يسبب ارتباكا للمرسل.<br/>يمكنك تنفيذ الخطوات الواردة في هذه المقالة، [معلومات حول Outlook قائمة الإكمال التلقائي](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) لإعادة تعيين ذاكرة التخزين المؤقت، مما سيؤدي إلى إصلاح هذه المشكلة.

- بالنسبة Outlook على ويب: في حالة Outlook على ويب، سيظل مستلم قائمة التوزيع في ذاكرة التخزين المؤقت. يمكنك اتباع الخطوات الواردة في [إزالة الاسم المقترح أو عنوان البريد الإلكتروني المقترح من قائمة الإكمال التلقائي](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) لتحديث ذاكرة التخزين المؤقت لرؤية بطاقة جهة اتصال المجموعة.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>هل يحصل أعضاء المجموعة الجدد على بريد إلكتروني ترحيبي في علبة الوارد الخاصة بهم؟

لا. يتم تعيين الإعداد لتمكين رسائل الترحيب إلى خطأ بشكل افتراضي. يؤثر هذا الإعداد على كل من أعضاء المجموعة الحاليين والجديدين الذين قد ينضمون بعد اكتمال الترحيل. إذا سمح مالك المجموعة لاحقا للمستخدمين الضيوف، فلن يتلقى المستخدمون الضيوف بريدا إلكترونيا ترحيبيا في علبة الوارد الخاصة بهم. يمكن للأعضاء الضيوف متابعة العمل مع المجموعة.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>ماذا لو لم تتم ترقية واحد أو بعض DLs؟

هناك بعض الحالات التي تكون فيها DL مؤهلة ولكن تعذرت ترقيتها. لا يتم ترقية DL ويبقى ك DL.

- عندما يطبق المسؤول **نهج عنوان البريد الإلكتروني للمجموعات** في مؤسسة ويحاول ترقية DLs التي لا تفي بالمعايير، لا تتم ترقية DL

- تعذرت ترقية DLs مع **تعيين MemberJoinRestriction** أو **MemberDepartRestriction** إلى **مغلقة**

- يسمح بإنشاء مجموعة Microsoft 365 لعدد قليل من المستخدمين فقط، باستخدام الخطوات الواردة في [هذه المقالة](/microsoft-365/solutions/manage-creation-of-groups). في هذا السيناريو، إذا لم يسمح لمالك قائمة التوزيع بإنشاء مجموعة Microsoft 365، فلن تتم ترقية قائمة التوزيع إلى مجموعة Microsoft 365.
الحل البديل: استخدم أحد الحلول البديلة التالية للسيناريو أعلاه:

1. تأكد من السماح لكافة المستخدمين المذكورين كمالكين ل DL بإنشاء مجموعة M365، أي أنهم أعضاء في مجموعة الأمان المسموح بها لمجموعة M365.

   او

2. بشكل مؤقت، استبدل مالك DL غير المسموح له بإنشاء مجموعة M365 بالمستخدم المسموح له بإنشاء مجموعة M365.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>ماذا يحدث ل DL إذا فشلت الترقية من EAC؟

لن تحدث الترقية إلا عند إرسال المكالمة إلى الخادم. إذا فشلت الترقية، فستكون DLs بدون تغيير. سيعملون كما كانوا يعملون.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>ماذا يحدث لإعدادات الموافقة على الرسائل (الإشراف) على مجموعات التوزيع بعد الترقية؟

يتم الاحتفاظ بإعدادات الموافقة على الرسالة (الإشراف) والاستمرار في العمل بشكل جيد بعد ترقية مجموعة التوزيع إلى مجموعة Microsoft 365.

## <a name="related-content"></a>محتوى ذي صلة

[مقارنة المجموعات](../create-groups/compare-groups.md) (مقالة)\
[شرح مجموعات Microsoft 365 للمستخدمين](../create-groups/explain-groups-knowledge-worker.md) (مقالة)\
[إضافة أعضاء أو إزالتهم من مجموعات Microsoft 365 باستخدام مركز الإدارة](../create-groups/add-or-remove-members-from-groups.md)
