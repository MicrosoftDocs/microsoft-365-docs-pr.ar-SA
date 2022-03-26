---
title: كيفية تحديد نوع الانتظار الموضوع على علبة بريد Exchange Online البريد
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
description: تعرف على كيفية تحديد أنواع الانتظار المختلفة التي يمكن وضعها على علبة بريد Exchange Online في Microsoft 365.
ms.openlocfilehash: 0ad2a1a4479c2de667b23ee29ee321912e7d18e9
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/03/2022
ms.locfileid: "63566507"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>كيفية تحديد نوع الانتظار الموضوع على علبة بريد Exchange Online البريد

تشرح هذه المقالة كيفية تحديد عدد Exchange Online علب البريد في Microsoft 365.

Microsoft 365 العديد من الطرق التي يمكن لمنظمتك من خلالها منع حذف محتوى علبة البريد بشكل دائم. يسمح هذا لمنظمتك بالاحتفاظ بالمحتوى لاحتفاظها بأنواع التوافق أو أثناء عمليات التحقيق القانونية وأنواع أخرى من التحقيقات. فيما يلي قائمة بميزات الاستبقاء (تسمى أيضا *احتجاز) في* Office 365:

- **[الاحتجاز القضائية](create-a-litigation-hold.md):** يتم تطبيق هذا الأمر على علب بريد المستخدمين في Exchange Online.

- **[eDiscovery hold](create-ediscovery-holds.md):** وهي تحمل مقترنة ب حالة eDiscovery الأساسية في مركز الأمان والتوافق. يمكن تطبيق معاينات eDiscovery على علب بريد المستخدمين وعلى علبة البريد المطابقة Microsoft 365 المجموعات Microsoft Teams.

- **[في وضع](/Exchange/security-and-compliance/create-or-remove-in-place-holds) الانتظار:** يتم الاحتفاظات التي يتم تطبيقها على علب بريد المستخدمين باستخدام أداة In-Place eDiscovery & Hold في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز</a> إدارة Exchange في Exchange Online. 

   > [!NOTE]
   > In-Place تم إعفائها ولم يعد بإمكانك إنشاء "In-Place" أو تطبيقها على علب البريد. ومع ذلكIn-Place يمكن تطبيق "In-Place" على علب البريد في مؤسستك، ولهذا السبب يتم تضمينها في هذه المقالة. لمزيد من المعلومات، راجع تقاعد [أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Microsoft 365](retention.md)** الاستبقاء: يمكن تكوينه للاحتفاظ بالمحتوى (أو الاحتفاظ به ثم حذفه) في علب بريد المستخدمين في Exchange Online وفي علبة البريد المطابقة ل Microsoft 365 ومجموعات Microsoft Teams. يمكنك أيضا إنشاء نهج استبقاء للاحتفاظ Skype for Business المحادثات المخزنة في علب بريد المستخدمين.

  هناك نوعان من Microsoft 365 الاستبقاء التي يمكن تعيينها إلى علب البريد.

    - **سياسات استبقاء مواقع معينة:** هذه هي السياسات التي تم تعيينها إلى مواقع المحتوى الخاصة بمستخدمين معينين. يمكنك استخدام **الأمر cmdlet Get-Mailbox** Exchange Online PowerShell للحصول على معلومات حول سياسات الاستبقاء المعينة لعلب بريد معينة. لمزيد من المعلومات حول هذا النوع من نهج الاستبقاء، راجع المقطع [نهج](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) مع تضمينات أو استثناءات معينة من وثائق نهج الاستبقاء.

    - **سياسات الاستبقاء على مستوى المؤسسة:** هذه هي السياسات التي تم تعيينها إلى كل مواقع المحتوى في مؤسستك. يمكنك استخدام **الأمر Get-OrganizationConfig** cmdlet Exchange Online PowerShell للحصول على معلومات حول سياسات الاستبقاء على مستوى المؤسسة. لمزيد من المعلومات حول هذا النوع من نهج الاستبقاء، راجع المقطع [نهج](retention-settings.md#a-policy-that-applies-to-entire-locations) ينطبق على مواقع كاملة من وثائق نهج الاستبقاء.

- **[Microsoft 365 تسميات الاستبقاء](retention.md):** إذا قام مستخدم بتطبيق تسمية استبقاء Microsoft 365 (تم تكوينها للاحتفاظ بالمحتوى أو الاحتفاظ بالمحتوى ثم حذفه) لأي مجلد أو عنصر في  علبة بريده، يتم وضع علامة احتجاز على علبة البريد كما لو تم وضع علبة البريد في وضع الاحتجاز بسبب الدعاوى القضائية أو تعيينها إلى نهج استبقاء Microsoft 365. لمزيد من المعلومات، راجع [المقطع تحديد](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) علب البريد الموقوقة بسبب تطبيق تسمية استبقاء على مجلد أو عنصر في هذه المقالة.

لإدارة علب البريد قيد الانتظار، قد تحتاج إلى تحديد نوع الانتظار الذي يتم وضعه على علبة بريد بحيث يمكنك تنفيذ مهام مثل تغيير مدة الانتظار أو إزالة فترة الانتظار مؤقتا أو بشكل دائم أو استبعاد علبة بريد من نهج استبقاء Microsoft 365. في هذه الحالات، تكون الخطوة الأولى هي تحديد نوع الانتظار الموضوع على علبة البريد. ولأنه يمكن وضع العديد من عمليات الاحتفاظ (وأنواع مختلفة من عمليات الانتظار) على علبة بريد واحدة، يجب تحديد كل عمليات الاحتفاظ الموضوعة على علبة بريد إذا كنت تريد إزالة أو تغيير قيد الانتظار.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>الخطوة 1: الحصول على GUID ل "المواضع الموقوتة" على علبة بريد

يمكنك تشغيل الأمرين cmdlets التاليين في Exchange Online PowerShell للحصول على GUID الخاص باحتجز التي يتم وضعها على علبة بريد. بعد الحصول على GUID، يمكنك استخدامه لتعريف فترة الانتظار المحددة في الخطوة 2. لا يتم تعريف الاحتجاز بسبب الدعاوى القضائية بواسطة GUID. يتم تمكين "الاحتجاز بسبب الدعاوى القضائية" أو تعطيلها لعلبة بريد.

- **Get-Mailbox:** استخدم أمر cmdlet هذا لتحديد ما إذا كان يتم تمكين "الاحتجاز بسبب الدعاوى القضائية" لعلبة بريد والحصول على GUIDs للاحتفاظ ب eDiscovery، ونهج احتجاز In-Place، ونهج استبقاء Microsoft 365 التي تم تعيينها بشكل خاص إلى علبة بريد. سيشير إخراج الأمر cmdlet هذا أيضا إلى ما إذا تم استبعاد علبة بريد بشكل صريح من نهج استبقاء على مستوى المؤسسة.

- **Get-OrganizationConfig:** استخدم الأمر cmdlet هذا للحصول على GUIDs لنهج الاستبقاء على مستوى المؤسسة.

للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

تشغيل الأمر التالي للحصول على معلومات حول Microsoft 365 الاستبقاء المطبقة على علبة بريد.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> إذا كان هناك عدد كبير جدا من القيم في الخاصية InPlaceHolds `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` ولم يتم عرضها كلها، يمكنك تشغيل الأمر لعرض كل GUID على سطر منفصل.

يصف الجدول التالي كيفية تحديد أنواع مختلفة من المواصفات استنادا إلى القيم في الخاصية *InPlaceHolds* عند تشغيل **الأمر cmdlet الخاص ب Get-Mailbox** .

| نوع الانتظار                                                          | قيمة المثال                                                                                  | كيفية تحديد الانتظار                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| الاحتجاز القضائية                                                    | `True`                                                                                         | يتم تمكين الاحتجاز بسبب الدعاوى القضائية لعلبة بريد عند تعيين الخاصية *LitigationHoldEnabled* إلى `True`.                                                                                                                                                                                                                                         |
| الاستمرار في eDiscovery                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | تحتوي *الخاصية InPlaceHolds* على GUID لأي مع الاستمرار المقترن ب eDiscovery case في مركز الأمان والتوافق. يمكنك معرفة أن هذا هو وضع eDiscovery لأن GUID `UniH` يبدأ بالبادرة (التي تشير إلى الاحتجاز الموحد).                                                                                   |
| In-Place الانتظار                                                      | `c0ba3ce811b6432a8751430937152491` <br/> أو <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | تحتوي *الخاصية InPlaceHolds* على GUID الخاص In-Place الموضع على علبة البريد. يمكنك معرفة أن هذه In-Place لأن GUID `cld` إما لا يبدأ ببادرة أو يبدأ بالبادرة.                                                                                                               |
| Microsoft 365 الاستبقاء المطبق تحديدا على علبة البريد | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> أو <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | تحتوي الخاصية InPlaceHolds على GUID لأي نهج استبقاء موقع معين تم تطبيقه على علبة البريد. يمكنك تحديد سياسات الاستبقاء لأن GUID يبدأ بالبادرة `mbx` `skp` أو. تشير `skp` البادأه إلى أنه يتم تطبيق نهج الاستبقاء Skype for Business المحادثات في علبة بريد المستخدم. |
| مستبعد من نهج استبقاء Microsoft 365 المؤسسة  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | إذا تم استبعاد علبة بريد من نهج استبقاء على مستوى المؤسسة Microsoft 365، فيعرض المعرف GUID لن نهج الاستبقاء الذي تم استبعاد علبة البريد منه في الخاصية InPlaceHolds `-mbx` ومحددة بواسطة البادئه.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
إذا كانت *الخاصية InPlaceHolds* فارغة عند تشغيل أمر cmdlet الخاص ب **Get-Mailbox**، فقد لا يزال هناك واحد أو أكثر من Microsoft 365 الاستبقاء المطبقة على علبة البريد. تشغيل الأمر التالي في Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للحصول على قائمة ب GUIDs ونهج الاستبقاء Microsoft 365 المؤسسة.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> إذا كان هناك عدد كبير جدا من القيم في الخاصية InPlaceHolds `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` ولم يتم عرضها كلها، يمكنك تشغيل الأمر لعرض كل GUID على سطر منفصل.

يصف الجدول التالي الأنواع المختلفة من المواصفة على مستوى المؤسسة وكيفية تحديد كل نوع استنادا إلى GUIDs المضمنة في الخاصية *InPlaceHolds* عند تشغيل **الأمر Cmdlet Get-OrganizationConfig** .

| نوع الانتظار                                                                                                | قيمة المثال                           | الوصف                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft 365 الاستبقاء المطبقة Exchange علب البريد Exchange المجلدات العمومية Teams الدردشات | `mbx7cfb30345d454ac0a989ab3041051209:2` | يتم تعريف سياسات الاستبقاء على مستوى المؤسسة المطبقة على علب بريد Exchange و Exchange المجلدات العامة و دردشات 1xN في Microsoft Teams بواسطة معرفاتGUID التي `mbx` تبدأ بالبادئه. ملاحظة يتم تخزين دردشات 1xN في علبة بريد المشاركين الفرديين في الدردشة.  |
| Microsoft 365 الاستبقاء المطبق على Microsoft 365 المجموعات Teams القنوات                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | يتم تعريف سياسات الاستبقاء على مستوى المؤسسة المطبقة على Microsoft 365 ورسائل القناة في Microsoft Teams بواسطة معرفات واجهة المستخدم (GUI) التي تبدأ بالبادرة`grp`. ملاحظة يتم تخزين رسائل القناة في علبة بريد المجموعة المقترنة بفريق Microsoft. |

لمزيد من المعلومات حول سياسات الاستبقاء المطبقة على Microsoft Teams، راجع التعرف على سياسات الاستبقاء [Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>فهم تنسيق القيمة InPlaceHolds لنهج الاستبقاء

بالإضافة إلى البادئه (mbx أو skp أو grp) التي تعرف عنصر ما في الخاصية InPlaceHolds ك نهج استبقاء Microsoft 365، تحتوي القيمة أيضا على لاحقة تحدد نوع إجراء الاستبقاء الذي تم تكوينه النهج. على سبيل المثال، يتم تمييز لاحقة الإجراء بخط غامق في الأمثلة التالية:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

يعرف الجدول التالي إجراءات الاستبقاء الثلاثة المحتملة:

| القيمة | الوصف                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | تشير إلى أنه تم تكوين نهج الاستبقاء لحذف العناصر. لا يحتفظ النهج بالعناصر.                                  |
| **2** | تشير إلى أنه تم تكوين نهج الاستبقاء للاحتفاظ بالعناصر. لا يحذف النهج العناصر بعد انتهاء فترة الاستبقاء. |
| **3** | تشير إلى أنه تم تكوين نهج الاستبقاء للاحتفاظ بالعناصر ثم حذفها بعد انتهاء فترة الاستبقاء.             |

لمزيد من المعلومات حول إجراءات الاستبقاء، راجع القسم الاحتفاظ بالمحتوى [لفترة زمنية](retention-settings.md#retaining-content-for-a-specific-period-of-time) معينة.
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>الخطوة 2: استخدام GUID لتحديد وضع الانتظار

بعد الحصول على GUID للحصول على الاستمرار الذي يتم تطبيقه على علبة بريد، فإن الخطوة التالية هي استخدام GUID لتحديد فترة الانتظار. تظهر الأقسام التالية كيفية تحديد اسم الانتظار (ومعلومات أخرى) باستخدام المستعرض المستعرض المستعرض المستعرض.

### <a name="ediscovery-holds"></a>يتولى eDiscovery

قم بتشغيل الأوامر التالية في & مركز التوافق PowerShell لتحديد مع الاستمرار eDiscovery الذي تم تطبيقه على علبة البريد. استخدم GUID (لا يشمل ذلك البادئية UniH) مع الاحتفاظ ب eDiscovery الذي حددته في الخطوة 1. 

للاتصال بمركز التوافق & PowerShell، راجع الاتصال [إلى مركز التوافق & PowerShell](/powershell/exchange/connect-to-scc-powershell).

ينشئ الأمر الأول متغيرا يحتوي على معلومات حول وضع الانتظار. يتم استخدام هذا المتغير في الأوامر الأخرى. يعرض الأمر الثاني اسم حالة eDiscovery المقترنة به. يعرض الأمر الثالث اسم الاستمرار وقائمة علب البريد التي ينطبق عليها الأمر المحتفظ به.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>In-Place "In-Place"

قم بتشغيل الأمر التالي في Exchange Online PowerShell لتحديد In-Place مع الاستمرار المطبق على علبة البريد. استخدم GUID In-Place الذي حددته في الخطوة 1. يعرض الأمر اسم الاستمرار وقائمة علب البريد التي ينطبق عليها الأمر.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

إذا بدأ GUID In-Place Hold `cld` بالبادرة، فتأكد من تضمين البادرة عند تشغيل الأمر السابق.

> [!IMPORTANT]
> بينما نستمر في الاستثمار بطرق مختلفة للمحافظة على محتوى علبة البريد، سنعلن عن In-Place في مركز إدارة Exchange (EAC). بدءا من 1 يوليو 2020، لن تتمكن من إنشاء In-Place جديدة في Exchange Online. ولكن سيبقى بإمكانك إدارة عمليات In-Place في EAC أو باستخدام الأمر cmdlet **Set-MailboxSearch** في Exchange Online PowerShell. على الرغم من ذلك، بدءا من 1 أكتوبر 2020، لن تتمكن من إدارة In-Place انتظار. سيتم إزالتها فقط في EAC أو باستخدام الأمر **cmdlet Remove-MailboxSearch** . لمزيد من المعلومات حول تقاعد In-Place، راجع تقاعد [أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Microsoft 365 الاستبقاء

[الاتصال إلى مركز التوافق & PowerShell](/powershell/exchange/connect-to-scc-powershell) وتشغيل الأمر التالي ل تحديد نهج استبقاء Microsoft 365 (على مستوى المؤسسة أو موقع محدد) المطبق على علبة البريد. استخدم GUID (لا يشمل ذلك البادرة mbx أو skp أو grp أو لاحقة الإجراء) التي حددتها في الخطوة 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>تحديد علب البريد مع الانتظار بسبب تطبيق تسمية استبقاء على مجلد أو عنصر

كلما قام مستخدم بتطبيق تسمية استبقاء تم تكوينها للاحتفاظ بالمحتوى  أو الاحتفاظ  به ثم حذفه إلى أي مجلد أو عنصر في علبة بريده، يتم تعيين خاصية *علبة بريد ComplianceTagHoldApplied* إلى **True**. عند حدوث ذلك، يتم التعامل مع علبة البريد بطريقة مماثلة إذا تم وضعها قيد الانتظار، مثل عند تعيينها إلى نهج استبقاء Microsoft 365 أو وضعها في الاحتجاز بسبب الدعاوى القضائية، ولكن مع بعض التحذيرات. عند تعيين *الخاصية ComplianceTagHoldApplied* إلى **True**، تحدث الأمور التالية:

- إذا تم حذف علبة البريد أو Microsoft 365 المستخدم، تصبح علبة البريد علبة بريد [غير نشطة](inactive-mailboxes-in-office-365.md).
- لا يمكنك تعطيل علبة البريد (إما علبة البريد الأساسية أو علبة بريد الأرشيف، إذا تم تمكينها).
- ستتبع العناصر التي تم حذفها من علبة البريد أحد المسارين استنادا إلى ما إذا تم تسميتها أم لا:
    - **ستتبع العناصر غير** المصنوفة المسار نفسه الذي تتخذه العناصر المحذوفة عند عدم تطبيق أي معيقات على علبة البريد.  يتم تحديد الوقت الذي يستغرقه حذف هذه العناصر بشكل دائم من خلال تكوين استبقاء العنصر المحذوف وما إذا تم تمكين استرداد [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) عنصر واحد لعلبة البريد أم لا.[](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention)
    - **سيتم الاحتفاظ بالعناصر** ذات التسمية داخل مجلد العناصر [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) القابلة لاستردادها بالطريقة نفسها التي يتم بها الاحتفاظ بها في حالة Microsoft 365 الاستبقاء، ولكن على مستوى العنصر الفردي.  إذا كان لعدة عناصر تسميات مختلفة تم تكوينها للاحتفاظ بالمحتوى أو  الاحتفاظ به ثم حذفه في فواصل زمنية مختلفة، سيتم الاحتفاظ بكل عنصر استنادا إلى تكوين التسمية المطبقة.
- يمكن أن تمتد فترة الاحتجاز الأخرى، مثل Microsoft 365 الاستبقاء أو الاحتجاز في eDiscovery أو الاحتجاز بسبب الدعاوى القضائية إلى المدة التي يتم فيها الاحتفاظ بالعناصر الملصقات استنادا إلى مبادئ [الاستبقاء](retention.md#the-principles-of-retention-or-what-takes-precedence).

لعرض قيمة الخاصية *ComplianceTagHoldApplied* لعلبة بريد واحدة، يمكنك تشغيل الأمر التالي [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

لمزيد من المعلومات حول تسميات الاستبقاء، راجع [تسميات الاستبقاء](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>إدارة علب البريد عند الانتظار

بعد إزالة أي نوع من أنواع الانتظار من علبة البريد، يتم *تطبيق* فترة تأخير. وهذا يعني أن الإزالة الفعلية ل لفترة الانتظار يتم تأخيرها لمدة 30 يوما لمنع حذف البيانات نهائيا (إزالتها) من علبة البريد. يوفر ذلك للمسؤولين فرصة للبحث عن عناصر علبة البريد التي سيتم إزالتها أو استردادها بعد إزالة جلسة الانتظار. يتم وضع فترة الانتظار الخاصة بالتأخير على علبة بريد في المرة التالية التي يتولى فيها "مساعد المجلد المدار" بمعالجة علبة البريد والكشف عن إزالة قيد الانتظار. بشكل خاص، يتم تطبيق الاستمرار في التأخير على علبة بريد عندما يحدد مساعد المجلد المدار إحدى خصائص علبة البريد التالية إلى **True**:

- **DelayHoldApplied:** تنطبق هذه الخاصية على المحتوى المرتبط بالبريد الإلكتروني (الذي يتم إنشاؤه بواسطة الأشخاص الذين يستخدمون Outlook Outlook على ويب) المخزن في علبة بريد المستخدم.

- **DelayReleaseHoldApplied:** تنطبق هذه الخاصية على المحتوى المستند إلى السحابة (الذي يتم إنشاؤه بواسطة تطبيقات غير Outlook مثل Microsoft Teams و Microsoft Forms و Microsoft Yammer) المخزن في علبة بريد المستخدم. يتم عادة تخزين البيانات السحابية التي يتم إنشاؤها بواسطة تطبيق Microsoft في مجلد مخفي في علبة بريد المستخدم.

عند وضع فترة الانتظار لفترة تأخير على علبة البريد (عندما يتم تعيين أي من الخصائص السابقة إلى **True**)، لا تزال علبة البريد قيد الانتظار لمدة غير محدودة، كما لو كانت علبة البريد قيد الاحتجاز بسبب الدعاوى القضائية. بعد 30 يوما، تنتهي صلاحية فترة الانتظار للتأخير، وسيحاول Microsoft 365 تلقائيا إزالة فترة الانتظار للتأخير (من خلال تعيين الخاصية DelayHoldApplied أو DelayReleaseHoldApplied إلى **False**) بحيث تتم إزالة فترة الانتظار. بعد تعيين أي من هاتين الخاصتين إلى **False**، تتم إزالة العناصر المقابلة التي تم وضع علامة عليها للإزالة في المرة التالية التي تتم فيها معالجة علبة البريد بواسطة مساعد المجلد المدار.

لعرض قيم الخاصتين DelayHoldApplied و DelayReleaseHoldApplied لعلبة بريد، يمكنك تشغيل الأمر التالي [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

لإزالة فترة الانتظار قبل انتهاء صلاحيتها، يمكنك تشغيل أمر واحد (أو كليهما) في Exchange Online PowerShell، استنادا إلى الخاصية التي تريد تغييرها:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

أو

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

يجب أن يتم تعيين دور "الانتظار القانوني" في Exchange Online لاستخدام المعلمات *RemoveDelayHoldApplied* أو *RemoveDelayReleaseHoldApplied*. 

لإزالة الاستمرار في التأخير في علبة بريد غير نشطة، قم بتشغيل أحد الأوامر التالية في Exchange Online PowerShell:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

أو

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> أفضل طريقة لتحديد علبة بريد غير نشطة في الأمر السابق هي استخدام الاسم المميز أو Exchange GUID. يساعد استخدام إحدى هذه القيم على منع تحديد علبة البريد الخطأ عن طريق الخطأ. 

لمزيد من المعلومات حول استخدام هذه المعلمات لإدارة تأخيرات التأخير، راجع [تعيين علبة البريد](/powershell/module/exchange/set-mailbox).

ضع الأمور التالية في الاعتبار عند إدارة علبة بريد عند الانتظار بشكل تأخير:

- إذا تم تعيين الخاصية DelayHoldApplied أو DelayReleaseHoldApplied إلى **True** ، وحذفت علبة بريد (أو حساب المستخدم المناظر)، تصبح علبة البريد علبة بريد غير نشطة. وذلك لأن علبة البريد تعتبر في وضع الانتظار إذا تم تعيين أي خاصية إلى **True**، وي ينتج عن حذف علبة بريد عند الانتظار علبة بريد غير نشطة. لحذف علبة بريد وليس جعلها علبة بريد غير نشطة، يجب تعيين الخاصية إلى **False**.

- كما ذكر سابقا، تعتبر علبة البريد معطلة لمدة غير محدودة إذا تم تعيين الخاصية DelayHoldApplied أو DelayReleaseHoldApplied إلى **True**. ومع ذلك، لا يعني *ذلك أنه يتم* الاحتفاظ بكل المحتوى في علبة البريد. يعتمد ذلك على القيمة التي تم تعيينها إلى كل خاصية. على سبيل المثال، لن لنقل أنه تم تعيين الخاصية إلى **True** لأنه تتم إزالة حاملات من علبة البريد. بعد ذلك، يمكنك إزالة فقط الاستمرار في التأخير الذي يتم تطبيقه على البيانات غير Outlook السحابية (باستخدام *المعلمة RemoveDelayReleaseHoldApplied*). في المرة التالية التي يتولى فيها مساعد المجلد المدار عملية إدارة علبة البريد، Outlook العناصر التي تم وضع علامة عليها للإزالة. لن Outlook إزالة أي عناصر تم وضع علامة عليها للإزالة لأن الخاصية DelayHoldApplied لا تزال تعيين إلى **True**. سيكون العكس صحيحا أيضا: إذا تم تعيين DelayHoldApplied إلى **False** و DelayReleaseHoldApplied تم تعيينه إلى **True**، سيتم إزالة Outlook العناصر التي تم وضع علامة عليها للإزالة فقط.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>كيفية تأكيد تطبيق نهج استبقاء على مستوى المؤسسة على علبة بريد

عند تطبيق نهج استبقاء على مستوى المؤسسة أو إزالته إلى علبة بريد، قد يساعدك تصدير سجلات تشخيص علب البريد على أن تكون على يقين من أن Exchange Online قد طبق بالفعل نهج الاستبقاء أو أزاله إلى علبة البريد. لعرض هذه المعلومات، ستحتاج أولا إلى التحقق من بعض الأمور [باستخدام Exchange Online Powershell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>الحصول على GUIDs لأية سياسات استبقاء تم تطبيقها بشكل صريح على علبة بريد

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>الحصول على GUIDs لأي من سياسات الاستبقاء على مستوى المؤسسة المطبقة على علب البريد

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>الحصول على تشخيص علبة البريد ل HoldTracking

تحتفظ سجلات تشخيصات علبة البريد الخاصة بتعقب الانتظار بمحفوظات عمليات الاستمرار المطبقة على علبة بريد المستخدم.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>مراجعة نتائج سجلات تشخيص علب البريد

إذا قمت بجمع بيانات من الخطوة السابقة، فقد تبدو البيانات الناتجة على شكل ما يلي:

> **ed**`  : 0001-01-01T00:00:00.0000000`
>  **مخفي**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **ht**`  : 4`
>  **lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **osd**` : 2020-03-23T18:24:37.1884606Z`

استخدم الجدول التالي لمساعدتك على فهم كل قيمة من القيم السابقة المدرجة في سجل التشخيصات.

| القيمة   | الوصف |
|:------- |:----------- |
| **ed**  | تشير إلى تاريخ الانتهاء، وهو تاريخ تعطيل نهج الاستبقاء. تعني MinValue أنه لا يزال يتم تعيين النهج إلى علبة البريد. |
| **مخفي** | تشير إلى GUID لن نهج الاستبقاء. ترتبط هذه القيمة بGUIDs التي قمت بتجميعها لنهج الاستبقاء الصريحة أو على مستوى المؤسسة المعينة إلى علبة البريد.|
| **lsd** | تشير إلى تاريخ البدء الأخير، وهو تاريخ تعيين نهج الاستبقاء لعلبة البريد.|
| **osd** | تشير إلى تاريخ البدء الأصلي، وهو التاريخ الذي Exchange المعلومات المسجلة لأول مرة حول نهج الاستبقاء. |
|||

عندما لا يتم تطبيق نهج استبقاء على علبة بريد، سنطبق فترة انتظار مؤقتة على المستخدم لمنع إزالة المحتوى. يمكن تعطيل الاستمرار في التأخير عن طريق تشغيل `Set-Mailbox -RemoveDelayHoldApplied` الأمر.

## <a name="next-steps"></a>الخطوات التالية

بعد تحديد عمليات احتجاز تم تطبيقها على علبة بريد، يمكنك تنفيذ مهام مثل تغيير مدة الانتظار، أو إزالة فترة الانتظار مؤقتا أو بشكل دائم، أو استبعاد علبة بريد غير نشطة من نهج استبقاء Microsoft 365. للحصول على مزيد من المعلومات حول تنفيذ المهام ذات الصلة بالمهام المواثية، راجع أحد المواضيع التالية:

- قم بتشغيل الأمر [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) في مركز التوافق [في & PowerShell](/powershell/exchange/connect-to-scc-powershell) لاستبعاد علبة بريد من نهج استبقاء على مستوى Microsoft 365 المؤسسة. يمكن استخدام هذا الأمر فقط لنهج الاستبقاء حيث تساوي قيمة الخاصية *ExchangeLocation* `All`.

- [تغيير مدة الانتظار لعلبة بريد غير نشطة](change-the-hold-duration-for-an-inactive-mailbox.md)

- [حذف علبة بريد غير نشطة](delete-an-inactive-mailbox.md)

- [حذف العناصر في مجلد "العناصر القابلة لاستردادها" لعلب البريد المستندة إلى السحابة في الانتظار](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
