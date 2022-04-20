---
title: كيفية تحديد قائمة الاحتجاز في علبة بريد Exchange Online
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6057daa8-6372-4e77-a636-7ea599a76128
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: تعرف على كيفية تحديد أنواع الاحتجاز المختلفة التي يمكن وضعها على علبة بريد Exchange Online في Microsoft 365.
ms.openlocfilehash: 2e62d8f6fd0dc6352b4bf6fc5766b9cd33f8ffb4
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64994161"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>كيفية تحديد نوع قائمة الاحتجاز الموضوعة على علبة بريد Exchange Online

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تشرح هذه المقالة كيفية تحديد قوائم الاحتجاز الموضوعة على علب بريد Exchange Online في Microsoft 365.

يوفر Microsoft 365 عدة طرق يمكن لمؤسستك من خلالها منع حذف محتوى علبة البريد بشكل دائم. يسمح هذا لمؤسستك بالاحتفاظ بالمحتوى لتلبية لوائح الامتثال أو أثناء التحقيقات القانونية وأنواع أخرى من التحقيقات. فيما يلي قائمة بميزات الاستبقاء (تسمى أيضا *قوائم الاحتجاز*) في Office 365:

- **[احتجاز التقاضي](create-a-litigation-hold.md):** عمليات الاحتجاز التي يتم تطبيقها على علب بريد المستخدمين في Exchange Online.

- **[قائمة احتجاز eDiscovery](create-ediscovery-holds.md):** عمليات الاحتجاز المقترنة بحالة Microsoft Purview eDiscovery (Standard) في مركز الأمان والتوافق. يمكن تطبيق قوائم احتجاز eDiscovery على علب بريد المستخدمين وعلى علبة البريد المقابلة مجموعات Microsoft 365 Microsoft Teams.

- **[تعليق موضعي](/Exchange/security-and-compliance/create-or-remove-in-place-holds):** عمليات الاحتجاز التي يتم تطبيقها على علب بريد المستخدمين باستخدام أداة In-Place eDiscovery & Hold في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> في Exchange Online. 

   > [!NOTE]
   > In-Place تم إيقاف عمليات الاحتجاز ولم يعد بإمكانك إنشاء In-Place عمليات الاحتجاز أو تطبيقها على علب البريد. ومع ذلك، قد يستمر تطبيق In-Place عمليات الاحتجاز على علب البريد في مؤسستك، ولهذا السبب يتم تضمينها في هذه المقالة. لمزيد من المعلومات، راجع [تقاعد أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[نهج الاستبقاء Microsoft 365](retention.md):** يمكن تكوينها للاحتفاظ بالمحتوى (أو الاحتفاظ به ثم حذفه) في علب بريد المستخدمين في Exchange Online وفي علبة البريد المقابلة مجموعات Microsoft 365 Microsoft Teams. يمكنك أيضا إنشاء نهج استبقاء للاحتفاظ Skype for Business المحادثات المخزنة في علب بريد المستخدمين.

  هناك نوعان من نهج الاستبقاء Microsoft 365 التي يمكن تعيينها إلى علب البريد.

    - **نهج معينة للاحتفاظ بالموقع:** هذه هي النهج التي تم تعيينها إلى مواقع المحتوى الخاصة بمستخدمين معينين. يمكنك استخدام **cmdlet Get-Mailbox** في Exchange Online PowerShell للحصول على معلومات حول نهج الاستبقاء المعينة لعلب بريد معينة. لمزيد من المعلومات حول هذا النوع من نهج الاستبقاء، راجع القسم [A policy مع تضمينات أو استثناءات محددة](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) من وثائق نهج الاستبقاء.

    - **نهج الاستبقاء على مستوى المؤسسة:** هذه هي النهج التي تم تعيينها إلى كافة مواقع المحتويات في مؤسستك. يمكنك استخدام **Get-OrganizationConfig** cmdlet في Exchange Online PowerShell للحصول على معلومات حول نهج الاستبقاء على مستوى المؤسسة. لمزيد من المعلومات حول هذا النوع من نهج الاستبقاء، راجع القسم [A policy الذي ينطبق على مواقع بأكملها](retention-settings.md#a-policy-that-applies-to-entire-locations) من وثائق نهج الاستبقاء.

- **[Microsoft 365 تسميات الاستبقاء](retention.md):** إذا قام مستخدم بتطبيق تسمية استبقاء Microsoft 365 (تسمية تم تكوينها للاحتفاظ بالمحتوى أو الاحتفاظ بالمحتوى ثم حذفه) على *أي* مجلد أو عنصر في علبة البريد الخاصة به، يتم وضع قائمة احتجاز على علبة البريد كما لو كانت علبة البريد موضوعة في احتجاز التقاضي أو تم تعيينها إلى نهج استبقاء Microsoft 365. لمزيد من المعلومات، راجع [تحديد علب البريد الموجودة قيد الاحتجاز لأنه تم تطبيق تسمية استبقاء على مجلد أو مقطع عنصر](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) في هذه المقالة.

لإدارة علب البريد قيد الاحتجاز، قد تحتاج إلى تحديد نوع الاحتجاز الموضوع على علبة البريد بحيث يمكنك تنفيذ مهام مثل تغيير مدة الاحتجاز، أو إزالة قائمة الاحتجاز مؤقتا أو بشكل دائم، أو استبعاد علبة بريد من نهج استبقاء Microsoft 365. في هذه الحالات، تتمثل الخطوة الأولى في تحديد نوع الاحتجاز الموضوع على علبة البريد. ونظرا لأنه يمكن وضع قوائم احتجاز متعددة (وأنواع مختلفة من قوائم الاحتجاز) على علبة بريد واحدة، يجب عليك تحديد كافة قوائم الاحتجاز الموضوعة على علبة البريد إذا كنت تريد إزالة قائمة احتجاز أو تغييرها.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>الخطوة 1: الحصول على المعرف الفريد العمومي (GUID) لقيم الاحتجاز الموضوعة على علبة بريد

يمكنك تشغيل أمري cmdlets التاليين في Exchange Online PowerShell للحصول على المعرف الفريد العمومي (GUID) لأحمال الاحتجاز التي يتم وضعها على علبة بريد. بعد الحصول على GUID، يمكنك استخدامه لتحديد قائمة الاحتجاز المحددة في الخطوة 2. لا يتم تحديد احتجاز التقاضي بواسطة GUID. يتم تمكين احتجاز التقاضي أو تعطيله لعل بريد.

- **الحصول على علبة البريد:** استخدم أمر cmdlet هذا لتحديد ما إذا كان تم تمكين احتجاز التقاضي لعل بريد والحصول على معرفات المستخدم الرسومية (GUIDs) للاحتفاظ ب eDiscovery In-Place ونهج الاستبقاء Microsoft 365 التي تم تعيينها بشكل خاص إلى علبة بريد. سيشير إخراج أمر cmdlet هذا أيضا إلى ما إذا تم استبعاد علبة بريد بشكل صريح من نهج استبقاء على مستوى المؤسسة.

- **Get-OrganizationConfig:** استخدم أمر cmdlet هذا للحصول على GUIDs لنهج الاستبقاء على مستوى المؤسسة.

للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

قم بتشغيل الأمر التالي للحصول على معلومات حول قوائم الاحتجاز ونهج الاستبقاء Microsoft 365 المطبقة على علبة بريد.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> إذا كان هناك عدد كبير جدا من القيم في الخاصية InPlaceHolds ولم يتم عرضها كلها، يمكنك تشغيل `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` الأمر لعرض كل GUID على سطر منفصل.

يصف الجدول التالي كيفية تحديد أنواع مختلفة من قوائم الاحتجاز استنادا إلى القيم الموجودة في *الخاصية InPlaceHolds* عند تشغيل **الأمر "الحصول على علبة البريد** " cmdlet.

| نوع قائمة الاحتجاز                                                          | قيمة المثال                                                                                  | كيفية تحديد قائمة الاحتجاز                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| احتجاز التقاضي                                                    | `True`                                                                                         | يتم تمكين احتجاز التقاضي لعل بريد عند تعيين `True`الخاصية *«التقاضي_ إلى* ».                                                                                                                                                                                                                                         |
| قائمة احتجاز eDiscovery                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | تحتوي *الخاصية InPlaceHolds* على GUID لأي احتجاز مقترن بحالة eDiscovery في مركز الأمان والتوافق. يمكنك معرفة أن هذا هو تعليق eDiscovery لأن GUID يبدأ بالبادئة `UniH` (التي تشير إلى احتجاز موحد).                                                                                   |
| احتجاز In-Place                                                      | `c0ba3ce811b6432a8751430937152491` <br/> او <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | تحتوي *الخاصية InPlaceHolds* على المعرف الفريد العمومي (GUID) In-Place Hold الذي تم وضعه على علبة البريد. يمكنك معرفة أن هذا In-Place قائمة احتجاز لأن GUID إما لا يبدأ ببادئة أو يبدأ بالبادئة `cld` .                                                                                                               |
| نهج استبقاء Microsoft 365 مطبق بشكل خاص على علبة البريد | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> او <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | تحتوي الخاصية InPlaceHolds على معرفات GUID لأي نهج استبقاء موقع معين يتم تطبيقه على علبة البريد. يمكنك تحديد نهج الاستبقاء لأن GUID يبدأ بالبادئة `mbx` `skp` أو. تشير البادئة `skp` إلى تطبيق نهج الاستبقاء على المحادثات Skype for Business في علبة بريد المستخدم. |
| مستثناة من نهج استبقاء Microsoft 365 على مستوى المؤسسة  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | إذا تم استبعاد علبة بريد من نهج استبقاء Microsoft 365 على مستوى المؤسسة، يتم عرض GUID لنهج الاستبقاء الذي تم استبعاد علبة البريد منه في الخاصية InPlaceHolds ويتم تعريفه بواسطة البادئة`-mbx`.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
إذا كانت *الخاصية InPlaceHolds فارغة* عند تشغيل **الأمر cmdlet الخاص ب Get-Mailbox**، فقد يكون هناك نهج استبقاء واحد أو أكثر على مستوى المؤسسة Microsoft 365 مطبق على علبة البريد. قم بتشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على قائمة ب GUIDs لنهج استبقاء Microsoft 365 على مستوى المؤسسة.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> إذا كان هناك عدد كبير جدا من القيم في الخاصية InPlaceHolds ولم يتم عرضها كلها، يمكنك تشغيل `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` الأمر لعرض كل GUID على سطر منفصل.

يصف الجدول التالي الأنواع المختلفة لقوائم الاحتجاز على مستوى المؤسسة وكيفية تحديد كل نوع استنادا إلى معرفات المستخدم الرسومية المضمنة في خاصية *InPlaceHolds* عند تشغيل **الأمر Cmdlet Get-OrganizationConfig** .

| نوع قائمة الاحتجاز                                                                                                | قيمة المثال                           | الوصف                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft 365 نهج الاستبقاء المطبقة على علب البريد Exchange والمجلدات العامة Exchange والدردشات Teams | `mbx7cfb30345d454ac0a989ab3041051209:2` | يتم تعريف نهج الاستبقاء على مستوى المؤسسة المطبقة على علب البريد Exchange والمجلدات العامة Exchange ودردشات 1xN في Microsoft Teams بواسطة معرفات GUID التي تبدأ بالبادئة`mbx`. يتم تخزين دردشات 1xN الملاحظة في علبة بريد المشاركين في الدردشة الفردية.  |
| نهج الاستبقاء Microsoft 365 المطبق على رسائل القناة مجموعات Microsoft 365 ورسائل القناة Teams                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | يتم تحديد نهج الاستبقاء على مستوى المؤسسة المطبقة على مجموعات Microsoft 365 ورسائل القناة في Microsoft Teams بواسطة معرفات GUID التي تبدأ بالبادئة`grp`. يتم تخزين رسائل قناة الملاحظات في علبة بريد المجموعة المقترنة ب Microsoft Team. |

لمزيد من المعلومات حول نهج الاستبقاء المطبقة على Microsoft Teams، راجع [التعرف على نهج الاستبقاء Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>فهم تنسيق قيمة InPlaceHolds لنهج الاستبقاء

بالإضافة إلى البادئة (mbx أو skp أو grp) التي تعرف عنصرا في الخاصية InPlaceHolds كنهج استبقاء Microsoft 365، تحتوي القيمة أيضا على لاحقة تحدد نوع إجراء الاستبقاء الذي تم تكوينه للنهج. على سبيل المثال، يتم تمييز لاحقة الإجراء بالنوع الغامق في الأمثلة التالية:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

يحدد الجدول التالي إجراءات الاستبقاء المحتملة الثلاثة:

| قيمه | الوصف                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | يشير إلى تكوين نهج الاستبقاء لحذف العناصر. لا يحتفظ النهج بالعناصر.                                  |
| **2** | يشير إلى تكوين نهج الاستبقاء للاحتفاظ بالعناصر. لا يحذف النهج العناصر بعد انتهاء فترة الاستبقاء. |
| **3** | يشير إلى أنه تم تكوين نهج الاستبقاء للاحتفاظ بالعناصر ثم حذفها بعد انتهاء فترة الاستبقاء.             |

لمزيد من المعلومات حول إجراءات الاستبقاء، راجع [محتوى الاحتفاظ لفترة زمنية معينة](retention-settings.md#retaining-content-for-a-specific-period-of-time) .
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>الخطوة 2: استخدام GUID لتحديد قائمة الاحتجاز

بعد الحصول على GUID للاحتفاظ الذي يتم تطبيقه على علبة بريد، تتمثل الخطوة التالية في استخدام GUID هذا لتعريف قائمة الاحتجاز. توضح الأقسام التالية كيفية تحديد اسم قائمة الاحتجاز (ومعلومات أخرى) باستخدام GUID قائمة الاحتجاز.

### <a name="ediscovery-holds"></a>قوائم احتجاز eDiscovery

قم بتشغيل الأوامر التالية في Security & Compliance Center PowerShell لتحديد قائمة احتجاز eDiscovery التي تم تطبيقها على علبة البريد. استخدم GUID (دون تضمين بادئة UniH) للاحتفاظ eDiscovery الذي حددته في الخطوة 1. 

للاتصال ب PowerShell ل Security & Compliance Center، راجع [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

ينشئ الأمر الأول متغيرا يحتوي على معلومات حول قائمة الاحتجاز. يتم استخدام هذا المتغير في الأوامر الأخرى. يعرض الأمر الثاني اسم حالة eDiscovery المقترنة بها. يعرض الأمر الثالث اسم قائمة الاحتجاز وقائمة بعلب البريد التي تنطبق عليها قائمة الاحتجاز.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>قوائم احتجاز In-Place

قم بتشغيل الأمر التالي في Exchange Online PowerShell لتحديد In-Place Hold المطبق على علبة البريد. استخدم GUID للاحتفاظ In-Place الذي حددته في الخطوة 1. يعرض الأمر اسم قائمة الاحتجاز وقائمة بعلب البريد التي تنطبق عليها قائمة الاحتجاز.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

إذا بدأ المعرف الفريد العمومي (GUID) In-Place Hold بالبادئة `cld` ، فتأكد من تضمين البادئة عند تشغيل الأمر السابق.

> [!IMPORTANT]
> بينما نواصل الاستثمار بطرق مختلفة للحفاظ على محتوى علبة البريد، فإننا نعلن عن توقف In-Place عمليات الاحتجاز في مركز إدارة Exchange (EAC). بدءا من 1 يوليو 2020، لن تتمكن من إنشاء In-Place جديد في Exchange Online. ولكن سيظل بإمكانك إدارة In-Place قوائم الاحتجاز في EAC أو باستخدام **Set-MailboxSearch** cmdlet في Exchange Online PowerShell. ومع ذلك، بدءا من 1 أكتوبر 2020، لن تتمكن من إدارة In-Place عمليات الاحتجاز. سيتم إزالتها فقط في EAC أو باستخدام **Cmdlet Remove-MailboxSearch** . لمزيد من المعلومات حول توقف In-Place Holds، راجع [تقاعد أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>نهج الاستبقاء Microsoft 365

[الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) وقم بتشغيل الأمر التالي لتحديد نهج استبقاء Microsoft 365 (على مستوى المؤسسة أو الموقع المحدد) المطبق على علبة البريد. استخدم GUID (لا يتضمن بادئة mbx أو skp أو grp أو لاحقة الإجراء) التي حددتها في الخطوة 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>تحديد علب البريد قيد الاحتجاز بسبب تطبيق تسمية استبقاء على مجلد أو عنصر

كلما قام مستخدم بتطبيق تسمية استبقاء تم تكوينها *للاحتفاظ* بالمحتوى أو *الاحتفاظ به ثم حذفه* إلى أي مجلد أو عنصر في علبة البريد الخاصة به، يتم تعيين خاصية علبة البريد *ComplianceTagHoldApplied* إلى **True**. عند حدوث ذلك، يتم التعامل مع علبة البريد بطريقة مماثلة لما إذا تم وضعها قيد الاحتجاز، مثل عند تعيينها إلى نهج استبقاء Microsoft 365 أو وضعها في احتجاز التقاضي، ولكن مع بعض التحذيرات. عند تعيين الخاصية *ComplianceTagHoldApplied* إلى **True**، تحدث الأشياء التالية:

- إذا تم حذف علبة البريد أو حساب Microsoft 365 الخاص بالمستخدم، فستصبح علبة البريد [علبة بريد غير نشطة](inactive-mailboxes-in-office-365.md).
- لا يمكنك تعطيل علبة البريد (إما علبة البريد الأساسية أو علبة بريد الأرشيف، إذا تم تمكينها).
- ستتبع العناصر التي تم حذفها من علبة البريد أحد المسارين استنادا إلى ما إذا كانت مسماة أم لا:
    - ستتبع **العناصر غير المسماة** المسار نفسه الذي تتخذه العناصر المحذوفة عند عدم تطبيق أي عمليات احتجاز على علبة البريد.  يتم تحديد الوقت الذي يستغرقه حذف هذه العناصر نهائيا بواسطة تكوين [استبقاء العنصر المحذوق](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) وما إذا كان قد تم تمكين [استرداد عنصر واحد](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) لعل البريد أم لا.
    - سيتم الاحتفاظ **بالعناصر المسماة** داخل [مجلد العناصر القابلة للاسترداد](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) بنفس الطريقة التي سيتم بها إذا تم تطبيق نهج استبقاء Microsoft 365، ولكن على مستوى العنصر الفردي.  إذا كانت هناك تسميات مختلفة لعناصر متعددة تم تكوينها *للاحتفاظ* بالمحتوى أو *الاحتفاظ به ثم حذفه* في فواصل زمنية مختلفة، فسيتم الاحتفاظ بكل عنصر استنادا إلى تكوين التسمية المطبقة.
- يمكن أن تؤدي عمليات الاحتجاز الأخرى، مثل نهج الاستبقاء Microsoft 365 أو احتجاز eDiscovery أو احتجاز التقاضي إلى تمديد مدة الاحتفاظ بالعناصر المسماة استنادا إلى [مبادئ الاستبقاء](retention.md#the-principles-of-retention-or-what-takes-precedence).

لعرض قيمة الخاصية *ComplianceTagHoldApplied* لعلب بريد واحد، قم بتشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

لمزيد من المعلومات حول تسميات الاستبقاء، راجع [تسميات الاستبقاء](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>إدارة علب البريد عند تعليق التأخير

بعد إزالة أي نوع من الاحتجاز من علبة بريد، يتم تطبيق *احتجاز تأخير* . وهذا يعني أن الإزالة الفعلية للاحتفاظ بالملفات متأخرة لمدة 30 يوما لمنع حذف البيانات بشكل دائم (إزالتها) من علبة البريد. وهذا يعطي المسؤولين فرصة للبحث عن عناصر علبة البريد التي سيتم إزالتها بعد إزالة قائمة الاحتجاز أو استردادها. يتم وضع تعليق تأخير على علبة بريد في المرة التالية التي يعالج فيها مساعد المجلد المدار علبة البريد ويكتشف أنه تمت إزالة قائمة احتجاز. على وجه التحديد، يتم تطبيق احتجاز تأخير على علبة بريد عندما يقوم مساعد المجلد المدار بتعيين إحدى خصائص علبة البريد التالية إلى **True**:

- **DelayHoldApplied:** تنطبق هذه الخاصية على المحتوى المرتبط بالبريد الإلكتروني (الذي يتم إنشاؤه بواسطة أشخاص يستخدمون Outlook Outlook على ويب) المخزن في علبة بريد المستخدم.

- **DelayReleaseHoldApplied:** تنطبق هذه الخاصية على المحتوى المستند إلى السحابة (الذي تم إنشاؤه بواسطة تطبيقات غير Outlook مثل Microsoft Teams Microsoft Forms وMicrosoft Yammer) المخزن في علبة بريد المستخدم. عادة ما يتم تخزين بيانات السحابة التي تم إنشاؤها بواسطة تطبيق Microsoft في مجلد مخفي في علبة بريد المستخدم.

عند وضع تعليق تأخير على علبة البريد (عند تعيين أي من الخصائص السابقة إلى **True**)، تظل علبة البريد قيد الاحتجاز لمدة احتجاز غير محدودة، كما لو كانت علبة البريد قيد الاحتجاز بسبب التقاضي. بعد 30 يوما، تنتهي صلاحية احتجاز التأخير، وسيحاول Microsoft 365 تلقائيا إزالة تعليق التأخير (عن طريق تعيين الخاصية DelayHoldApplied أو DelayReleaseHoldApplied إلى **False**) بحيث تتم إزالة قائمة الاحتجاز. بعد تعيين أي من هاتين الخاصيتين إلى **False**، تتم إزالة العناصر المقابلة التي تم وضع علامة إزالتها عليها في المرة التالية التي تتم فيها معالجة علبة البريد بواسطة مساعد المجلد المدار.

لعرض قيم الخاصيتين DelayHoldApplied و DelayReleaseHoldApplied لعلبة بريد، قم بتشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

لإزالة تعليق التأخير قبل انتهاء صلاحيته، يمكنك تشغيل أمر واحد (أو كليهما) في Exchange Online PowerShell، استنادا إلى الخاصية التي تريد تغييرها:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

او

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

يجب تعيين دور الاحتجاز القانوني في Exchange Online لاستخدام المعلمات *RemoveDelayHoldApplied* أو *RemoveDelayReleaseHoldApplied*. 

لإزالة تعليق التأخير على علبة بريد غير نشطة، قم بتشغيل أحد الأوامر التالية في Exchange Online PowerShell:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

او

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> أفضل طريقة لتحديد علبة بريد غير نشطة في الأمر السابق هي استخدام الاسم المميز أو قيمة GUID Exchange. يساعد استخدام إحدى هذه القيم على منع تحديد علبة البريد الخطأ عن طريق الخطأ. 

لمزيد من المعلومات حول استخدام هذه المعلمات لإدارة عمليات احتجاز التأخير، راجع [Set-Mailbox](/powershell/module/exchange/set-mailbox).

ضع الأمور التالية في الاعتبار عند إدارة علبة بريد عند تعليق التأخير:

- إذا تم تعيين الخاصية DelayHoldApplied أو DelayReleaseHoldApplied إلى **True** وتم حذف علبة بريد (أو حساب المستخدم المقابل)، تصبح علبة البريد علبة بريد غير نشطة. وذلك لأن علبة البريد تعتبر قيد الاحتجاز إذا تم تعيين أي خاصية إلى **True**، ويؤدي حذف علبة بريد قيد الاحتجاز إلى وجود علبة بريد غير نشطة. لحذف علبة بريد وعدم جعلها علبة بريد غير نشطة، يجب تعيين الخاصيتين إلى **False**.

- كما ذكر سابقا، تعتبر علبة البريد قيد الاحتجاز لمدة احتجاز غير محدودة إذا تم تعيين الخاصية DelayHoldApplied أو DelayReleaseHoldApplied إلى **True**. ومع ذلك، لا يعني هذا أنه يتم الاحتفاظ *بكافة* المحتويات في علبة البريد. يعتمد ذلك على القيمة التي تم تعيينها إلى كل خاصية. على سبيل المثال، لنفترض أن كلتا الخاصيتين تم تعيينهما إلى **True** لأنه تتم إزالة قوائم الاحتجاز من علبة البريد. ثم يمكنك إزالة قائمة احتجاز التأخير التي يتم تطبيقها على البيانات السحابية غير Outlook فقط (باستخدام المعلمة *RemoveDelayReleaseHoldApplied*). في المرة التالية التي يعالج فيها مساعد المجلد المدار علبة البريد، تتم إزالة العناصر غير Outlook التي تم وضع علامة إزالتها عليها. لن تتم إزالة أي عناصر Outlook تم وضع علامة إزالتها لأن الخاصية DelayHoldApplied لا تزال معينة إلى **True**. سيكون العكس صحيحا أيضا: إذا تم تعيين DelayHoldApplied إلى **False** وتم تعيين DelayReleaseHoldApplied إلى **True**، فسيتم إزالة العناصر التي تم وضع علامة إزالتها Outlook فقط.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>كيفية تأكيد تطبيق نهج استبقاء على مستوى المؤسسة على علبة بريد

عند تطبيق نهج استبقاء على مستوى المؤسسة أو إزالته إلى علبة بريد، يمكن أن يساعدك تصدير سجلات تشخيص علبة البريد على التأكد من أن Exchange Online قد قام بالفعل بتطبيق نهج الاستبقاء أو إزالته إلى علبة البريد. لعرض هذه المعلومات، تحتاج أولا إلى التحقق من صحة بعض الأشياء باستخدام [Exchange Online Powershell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>الحصول على معرفات المستخدم الرسومية لأي نهج استبقاء مطبقة بشكل صريح على علبة بريد

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>الحصول على معرفات المستخدم الرسومية (GUID) لأي نهج استبقاء على مستوى المؤسسة مطبقة على علب البريد

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>الحصول على تشخيص علبة البريد ل HoldTracking

تحتفظ سجلات تشخيص علبة بريد تعقب الاحتجاز بمحفوظات عمليات الاحتجاز المطبقة على علبة بريد المستخدم.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>مراجعة نتائج سجلات تشخيصات علبة البريد

إذا قمت بجمع البيانات من الخطوة السابقة، فقد تبدو البيانات الناتجة شيئا مثل هذا:

> **اد**`  : 0001-01-01T00:00:00.0000000`
>  **اختبا**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **Ht**`  : 4`
>  **Lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **Osd**` : 2020-03-23T18:24:37.1884606Z`

استخدم الجدول التالي لمساعدتك على فهم كل قيمة من القيم السابقة المدرجة في سجل التشخيصات.

| قيمه   | الوصف |
|:------- |:----------- |
| **اد**  | يشير إلى تاريخ الانتهاء، وهو تاريخ تعطيل نهج الاستبقاء. تعني MinValue أن النهج لا يزال معينا إلى علبة البريد. |
| **اختبا** | يشير إلى GUID لنهج الاستبقاء. ستربط هذه القيمة ب GUIDs التي قمت بتجميعها لنهج الاستبقاء الصريحة أو على مستوى المؤسسة المعينة إلى علبة البريد.|
| **Lsd** | يشير إلى تاريخ البدء الأخير، وهو التاريخ الذي تم فيه تعيين نهج الاستبقاء إلى علبة البريد.|
| **Osd** | يشير إلى تاريخ البدء الأصلي، وهو التاريخ الذي Exchange أول معلومات مسجلة حول نهج الاستبقاء. |
|||

عندما لا يتم تطبيق نهج استبقاء على علبة بريد، سنضع تعليق تأخير مؤقت على المستخدم لمنع إزالة المحتوى. يمكن تعطيل تعليق التأخير عن طريق تشغيل `Set-Mailbox -RemoveDelayHoldApplied` الأمر.

## <a name="next-steps"></a>الخطوات التالية

بعد تحديد قوائم الاحتجاز التي يتم تطبيقها على علبة بريد، يمكنك تنفيذ مهام مثل تغيير مدة الاحتجاز أو إزالة قائمة الاحتجاز مؤقتا أو بشكل دائم أو استبعاد علبة بريد غير نشطة من نهج استبقاء Microsoft 365. لمزيد من المعلومات حول تنفيذ المهام المتعلقة بعمليات الاحتجاز، راجع أحد المواضيع التالية:

- قم بتشغيل الأمر [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) في [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) لاستبعاد علبة بريد من نهج استبقاء Microsoft 365 على مستوى المؤسسة. يمكن استخدام هذا الأمر فقط لنهج الاستبقاء حيث تساوي `All`قيمة خاصية *ExchangeLocation*.

- [تغيير مدة الانتظار لعلبة بريد غير نشطة](change-the-hold-duration-for-an-inactive-mailbox.md)

- [حذف علبة بريد غير نشطة](delete-an-inactive-mailbox.md)

- [حذف العناصر في مجلد "العناصر القابلة للاسترداد" في علب البريد المستندة إلى السحابة عند الاحتجاز](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
