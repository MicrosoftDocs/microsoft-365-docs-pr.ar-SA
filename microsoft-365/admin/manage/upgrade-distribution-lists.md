---
title: ترقية قوائم التوزيع Microsoft 365 المجموعات في Outlook
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
description: تعرف على كيفية ترقية قائمة توزيع واحدة أو أكثر Microsoft 365 المجموعات في Outlook، وكيفية استخدام PowerShell لترقية عدة قوائم توزيع في الوقت نفسه.
ms.openlocfilehash: 5394ce52f865d0b9a0383619cb11b9ebf3a94fc8
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63568359"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>ترقية قوائم التوزيع Microsoft 365 المجموعات في Outlook

يمكنك ترقية قوائم التوزيع Microsoft 365 المجموعات في Outlook. هذه طريقة رائعة لإعطاء قوائم التوزيع في مؤسستك كل الميزات والوظائف في Microsoft 365 المجموعات. [لماذا يجب ترقية قوائم التوزيع إلى مجموعات في Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

يمكنك ترقية DLs مرة واحدة في كل مرة، أو عدة عناوين في الوقت نفسه.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>ترقية مجموعة واحدة أو أكثر من مجموعات قائمة التوزيع Microsoft 365 المجموعات في Outlook

يجب أن تكون المسؤول العام أو المسؤول Exchange لترقية مجموعة قائمة توزيع. للترقية إلى Microsoft 365 المجموعات، يجب أن يكون لمجموعة قائمة التوزيع مالك مع علبة بريد.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>استخدم EAC الجديد لترقية مجموعة واحدة أو أكثر من مجموعات قائمة التوزيع Microsoft 365 مجموعات في Outlook

1. انتقل إلى مركز إدارة Exchange الجديد > **المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

2. حدد مجموعة قائمة التوزيع (تسمى أيضا مجموعة **توزيع) التي** تريد ترقيتها Microsoft 365 من **صفحة** المجموعات.

3. حدد مجموعة **توزيع الترقية** من شريط الأدوات.

4. في مربع الحوار **هل أنت جاهز للترقية؟**، انقر فوق **ترقية**. تبدأ العملية على الفور. استنادا إلى حجم مجموعات قائمة التوزيع التي تقوم بترقية عددها وعددها، قد تستغرق العملية دقائق أو ساعات.

> [!NOTE]
> يشير الشعار في الأعلى إلى الترقية، على سبيل المثال، تمت ترقية مجموعة *(مجموعة) توزيع. سيستغرق الأمر 5 دقائق لعكس التغييرات. قم بالتصفية Microsoft 365 المجموعات لرؤية مجموعات (مجموعات) التوزيع التي تمت ترقيتها*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>استخدم EAC الكلاسيكية لترقية مجموعة واحدة أو أكثر من مجموعات قائمة التوزيع Microsoft 365 المجموعات في Outlook

1. انتقل إلى Exchange إدارة > **المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>سترى إشعارا يشير إلى أن لديك قوائم توزيع (تسمى أيضا مجموعات **التوزيع) مؤهلة** للترقية إلى Microsoft 365 المجموعات.<br/> ![حدد الزر بدء التشغيل.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. حدد قائمة توزيع واحدة أو أكثر (تسمى أيضا **مجموعة توزيع**) من **صفحة** المجموعات.<br/>![حدد مجموعة توزيع.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. حدد أيقونة الترقية.<br/>![الترقية إلى Microsoft 365 المجموعات.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. في مربع حوار المعلومات، حدد **نعم** لتأكيد الترقية. تبدأ العملية على الفور. استنادا إلى حجم عدد عناوين DLs التي تقوم بترقيةها، قد تستغرق العملية دقائق أو ساعات.<br/>إذا لم يكن من الممكن ترقية قائمة التوزيع، يظهر مربع حوار يقول ذلك. راجع [ما هي قوائم التوزيع التي لا يمكن ترقيتها؟](#which-distribution-lists-cant-be-upgraded).

1. إذا كنت تقوم بترقية قوائم توزيع متعددة، فاستخدم القائمة المنسدل لتصفية قوائم التوزيع التي تمت ترقيتها. إذا لم تكتمل القائمة، فانتظر قليلا ثم حدد **تحديث** لرؤية ما تمت ترقيته بنجاح.<br/>لا يوجد إشعار يخبرك عند اكتمال عملية الترقية لكل عناوين DLs التي حددتها. يمكنك معرفة ذلك من خلال الاطلاع على ما هو مدرج ضمن **متوفر للترقية** أو **عناوين DLs التي تمت ترقيتها**.

1. إذا قمت بتحديد DL للترقية، ولكن لا يزال يظهر على الصفحة ك متوفر للترقية، فقد فشل الترقية. راجع [ما يجب فعله إذا لم تعمل الترقية](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> إذا كنت تحصل على رسائل البريد الإلكتروني الخاصة بالمجموعات، فقد تلاحظ في الأسفل أنه قد يعرض في بعض الأحيان السماح لك بترقية أي قوائم توزيع مؤهلة أنت مالكها. راجع [إجراء محادثة مجموعة في Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) للحصول على مزيد من المعلومات حول رسائل البريد الإلكتروني الخاصة بالهضم.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>ما يجب فعله إذا لم تعمل الترقية

تظل قوائم التوزيع التي تفشل في الترقية دون تغيير.

إذا فشلت ترقية واحدة  أو أكثر من قوائم التوزيع المؤهلة، 

1. استخدم [هذا](https://aka.ms/DLToM365Group) البرنامج النصي لمسح المشاكل المحتملة التي قد تمنع ترقية قائمة التوزيع إلى مجموعة Microsoft 365، وإصلاح أي مشاكل تم إعلامها بواسطة البرنامج النصي وحاول ترقية قائمة التوزيع مرة أخرى. 

2. إذا لم يساعدك البرنامج النصي أعلاه أو إذا استمرت المشكلة، فافتح [تذكرة دعم](../../business-video/get-help-support.md). يجب تصعيد المشكلة إلى فريق هندسة المجموعات ليكتشفوا المشكلة.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>كيفية استخدام PowerShell لترقية عدة قوائم توزيع في الوقت نفسه

إذا كنت من ذوي الخبرة في استخدام PowerShell، فقد تحتاج إلى الانتقال إلى هذا المسار بدلا من استخدام واجهة المستخدم. لدينا مجموعة من cmdlets التي ستساعدك على ترقية قوائم التوزيع. انظر أدناه.

### <a name="upgrade-a-single-dl"></a>ترقية DL واحد

لترقية DL واحد، قم بتشغيل الأمر التالي:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

على سبيل المثال، إذا كنت تريد ترقية DL باستخدام عنوان SMTP dl1@contoso.com، ف قم بتشغيل الأمر التالي:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> يمكنك أيضا ترقية قائمة توزيع واحدة إلى مجموعة Microsoft 365 [باستخدام cmdlet New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) PowerShell

### <a name="upgrade-multiple-dls-in-a-batch"></a>ترقية عدة عناوين DLs في دفعة

يمكنك أيضا تمرير عدة عناوين DLs دفعة واحدة وترقية كل منها معا:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

على سبيل المثال، إذا كنت تريد ترقية خمسة عناوين DLs باستخدام عنوان SMTP `dl2@contoso.com``dl1@contoso.com` و و `dl4@contoso.com` `dl3@contoso.com`و `dl5@contoso.com`، قم بتشغيل الأمر التالي:

`Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com`

### <a name="upgrade-all-eligible-dls"></a>ترقية كل عناوين DLs المؤهلة

هناك طريقتان يمكنك من خلالها ترقية كل عناوين DLs المؤهلة.

> [!NOTE]
> لا يتلقى Upgrade-DistributionGroup cmdlet بيانات من خط الانابيب، ولهذا السبب، من المطلوب استخدام عامل التشغيل "foreach-object{}" للتشغيل بنجاح.

1. احصل على عناوين DLs المؤهلة في المستأجر وترقية هؤلاء الأشخاص باستخدام أمر الترقية:

```PowerShell
Get-EligibleDistributionGroupForMigration | Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

2. احصل على قائمة بكل عناوين DLs وترقية عناوين DLs المؤهلة فقط:

```PowerShell
Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>الأسئلة الشائعة حول ترقية قوائم التوزيع Microsoft 365 المجموعات في Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>ما هي قوائم التوزيع التي لا يمكن ترقيتها؟

يمكنك فقط ترقية قوائم التوزيع البسيطة وغير المتداخلة المدارة عبر السحابة. يسرد الجدول أدناه قوائم التوزيع التي **لا يمكن** ترقيتها.

|**الخاصية**|**هل هو مؤهل؟**|
|:-----|:-----|
|قائمة توزيع مدارة في الموقع.  <br/> |لا  <br/> |
|قوائم التوزيع المتداخلة. تتضمن قائمة التوزيع مجموعات أطفال أو عضوا في مجموعة أخرى.  <br/> |لا  <br/> |
|قوائم التوزيع مع **RecipientTypeDetails العضو** غير **UserMailbox** و **SharedMailbox** و **TeamMailbox** و **MailUser**  <br/> |لا  <br/> |
|قائمة التوزيع التي تضم أكثر من 100 مالك  <br/> |لا  <br/> |
|قائمة التوزيع التي تضم أعضاء فقط ولكن بدون مالك  <br/> |لا  <br/> |
|قائمة توزيع تحتوي على اسم مستعار يحتوي على أحرف خاصة  <br/> |لا  <br/> |
|إذا تم تكوين قائمة التوزيع لتكون عنوان إعادة توجيه لعلبة البريد المشتركة  <br/> |لا  <br/> |
|إذا كانت DL جزءا من **تقييد المرسل** في DL آخر.  <br/> |لا  <br/> |
|مجموعات الأمان  <br/> |لا  <br/> |
|قوائم التوزيع الديناميكية  <br/> |لا  <br/> |
|قوائم التوزيع التي تم تحويلها إلى **RoomLists**  <br/> |لا  <br/> |

### <a name="check-which-dls-are-eligible-for-upgrade"></a>التحقق من عناوين DLs المؤهلة للترقية

إذا كنت تريد التحقق مما إذا كان DL مؤهلا أم لا، يمكنك تشغيل الأمر أدناه:

`Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration`

إذا كنت تريد التحقق من عناوين DLs المؤهلة للترقية ما عليك سوى تشغيل الأمر التالي:

`Get-EligibleDistributionGroupForMigration`

### <a name="who-can-run-the-upgrade-scripts"></a>روبوت Who تشغيل البرامج النصية للترقية؟

الأشخاص الذين Exchange أو المسؤول العام.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>لماذا لا تزال بطاقة جهة الاتصال تعرض قائمة توزيع؟ ماذا يجب أن أفعل لمنع ظهور قائمة توزيع تمت ترقيتها في قائمة اقتراحي التلقائي؟

- على Outlook: عندما يحاول أحد الأشخاص إرسال رسالة بريد إلكتروني في Outlook عن طريق كتابة اسم مجموعة Microsoft 365 بعد الترحيل، سيتم حل المستلم ك قائمة توزيع بدلا من المجموعة. ستكون بطاقة جهة الاتصال الخاصة بالمستلم هي بطاقة جهة اتصال قوائم التوزيع. وذلك بسبب ذاكرة التخزين المؤقت للمستلم أو ذاكرة التخزين المؤقت لاسم نيات في Outlook. سيتم إرسال البريد الإلكتروني بنجاح إلى المجموعة، ولكن قد يسبب إرباكا للمرسل.<br/>يمكنك تنفيذ الخطوات الواردة في هذه المقالة، [معلومات](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) Outlook الإبعاد التلقائي لإعادة تعيين ذاكرة التخزين المؤقت، مما يؤدي إلى إصلاح هذه المشكلة.

- بالنسبة Outlook على ويب: في حالة Outlook على ويب، سيظل مستلم قائمة التوزيع في ذاكرة التخزين المؤقت. يمكنك اتباع الخطوات الواردة في [إزالة](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) الاسم أو عنوان البريد الإلكتروني المقترح من قائمة الإكمال التلقائي لتحديث ذاكرة التخزين المؤقت لرؤية بطاقة جهة اتصال المجموعة.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>هل يحصل أعضاء المجموعة الجدد على بريد إلكتروني ترحيبي في علبة الوارد الخاصة بهم؟

لا. يتم تعيين الإعداد لتمكين رسائل الترحيب إلى خطأ بشكل افتراضي. يؤثر هذا الإعداد على أعضاء المجموعة الجدد والموجودين الذين قد ينضمون بعد اكتمال عملية الترحيل. إذا كان مالك المجموعة يسمح لاحقا للمستخدمين الضيوف، فلن يتلقى المستخدمون الضيوف رسالة بريد إلكتروني ترحيبية في علبة الوارد الخاصة بهم. يمكن للأعضاء الضيوف متابعة العمل مع المجموعة.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>ماذا يحدث إذا لم تتم ترقية واحدة أو بعض عناوين DLs؟

هناك بعض الحالات التي يكون فيها DL مؤهلا ولكن لا يمكن ترقيته. لا تتم ترقية DL وتبقى ك DL.

- حيث يقوم المسؤول بتطبيق "نهج عنوان **البريد** الإلكتروني للمجموعة" للمجموعات في مؤسسة ويحاول ترقية عناوين DLs التي لا تفي بالمعايير، لا تتم ترقية DL

- لا يمكن ترقية **عناوين DLs مع MemberJoinRestriction** أو **MemberDepartRestriction** إلى **"** مغلقة"

- يسمح Microsoft 365 المجموعة فقط لمستخدمين قليلين، باستخدام الخطوات من [هذه المقالة](/microsoft-365/solutions/manage-creation-of-groups). في هذا السيناريو، إذا لم يسمح لمالك قائمة التوزيع بإنشاء مجموعة Microsoft 365، لن تتم ترقية قائمة التوزيع إلى Microsoft 365 المجموعة. الحل البديل: استخدم أحد الحل البديل التالي للسيناريوهات أعلاه:
1)  تأكد من أن جميع المستخدمين المذكورين كملاك ل DL مسموح لهم بإنشاء مجموعة M365، أي هم أعضاء في مجموعة الأمان المسموح بها لمجموعة M365.
OR
2)  بشكل مؤقت، استبدل مالك DL غير المسموح له بإنشاء مجموعة M365 بمستخدم مسموح له بإنشاء مجموعة M365

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>ماذا يحدث ل DL إذا فشلت الترقية من EAC؟

لن تحدث الترقية إلا عند إرسال المكالمة إلى الخادم. إذا فشلت الترقية، ستكون عناوين DLs بدون تغيير. ستعمل كما كانت تعمل.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>ماذا يحدث لإعدادات الموافقة على الرسائل (الإشراف) على مجموعات التوزيع بعد الترقية؟

يتم الاحتفاظ بإعدادات الموافقة على الرسالة (الإشراف) وستستمر في العمل بشكل جيد بعد ترقية مجموعة التوزيع إلى مجموعة Microsoft 365 المجموعة.

## <a name="related-content"></a>المحتوى ذي الصلة

[مقارنة المجموعات](../create-groups/compare-groups.md) (مقالة)\
[شرح Microsoft 365 المجموعات للمستخدمين](../create-groups/explain-groups-knowledge-worker.md) (مقالة)\
[إضافة أعضاء أو إزالتهم من Microsoft 365 باستخدام مركز الإدارة](../create-groups/add-or-remove-members-from-groups.md)
