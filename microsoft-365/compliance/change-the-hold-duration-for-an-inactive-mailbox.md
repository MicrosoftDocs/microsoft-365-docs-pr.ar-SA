---
title: تغيير مدة الانتظار لعلبة بريد غير نشطة
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: 8/29/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: bdee24ed-b8cf-4dd0-92ae-b86ec4661e6b
ms.custom:
- seo-marvel-apr2020
description: بعد أن Office 365 علبة بريد غير نشطة، قم بتغيير مدة احتجاز أو Office 365 الاستبقاء المعين لعلبة البريد غير النشطة.
ms.openlocfilehash: bf1131aa0d14222bec7ab1c94983925cfe39e673
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63568547"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>تغيير مدة الانتظار لعلبة بريد غير نشطة

إن [علبة البريد غير النشطة](inactive-mailboxes-in-office-365.md) هي حالة علبة البريد التي يتم استخدامها للاحتفاظ بالبريد الإلكتروني الخاص بموظف سابق بعد مغادرته مؤسستك. تصبح علبة البريد غير نشطة عند تطبيق الاستمرار المطبق عليها قبل حذف Microsoft 365 المستخدم.  ستبدأ الأنواع التالية من عمليات الحذف بإنشاء علبة بريد غير نشطة عند حذف حساب المستخدم:

- [Microsoft 365 الاستبقاء والتسميات](retention.md) مع الاحتفاظ بإعدادات أو الاحتفاظ بها وحذفها

- عقد مقترن مع [حالة eDiscovery](ediscovery.md)

- [الاحتجاز القضائية](create-a-litigation-hold.md)

- قائمة موجودة In-Place الانتظار.

> [!IMPORTANT]
> على الرغم من أن أي من عمليات الاحتفاظ أعلاه ستجبر علبة البريد على أن تصبح غير نشطة عند حذف حساب مستخدم Microsoft 365، إلا أنه من المستحسن بشدة استخدام استبقاء Microsoft 365 عند التخطيط الاستباقي لاستخدام علب البريد غير النشطة.
>
> - إن مخصصات eDiscovery المخصصة ل الحالات المحددة والمحددة زمنيا ذات الصلة بالمهمة القانونية. في مرحلة ما، من المحتمل أن تنتهي حالة قانونية وستزال عمليات الإزالة المقترنة بالقضية وستغلق حالة eDiscovery (أو يتم حذفها). إذا كانت حالة الانتظار الموضوعة على علبة بريد غير نشطة مقترنة بقضية eDiscovery، وكان يتم إصدار جلسة الانتظار أو تم إغلاق حالة eDiscovery أو حذفها، سيتم حذف علبة البريد غير النشطة بشكل دائم.
>
> - In-Place تم الآن Exchange في مركز إدارة المؤسسة. حتى 1 يوليو 2020، تعذر إنشاء In-Place جديدة في Exchange Online. حتى 1 أكتوبر 2020، لم يعد من الممكن تغيير مدة الاحتفاظ في مكانها. يمكن حذف أي علبة بريد غير نشطة In-Place تم تطبيق "الاستمرار" عليها فقط عن طريق إزالة In-Place الانتظار. ستستمر علب البريد غير النشطة الموجودة In-Place الاحتفاظ بالحفظ حتى تتم إزالة الاستمرار. لمزيد من المعلومات حول In-Place حالات التقاعد، راجع تقاعد [أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md).
>
> - [يظل الاحتجاز](create-a-litigation-hold.md) بسبب الدعاوى القضائية معتمدا كطريقة بديلة للاحتفاظ بالمحتوى في علبة البريد وجعله غير نشط بعد حذف حساب مستخدم. ومع ذلك، فإننا ننصحك، كتقنية قديمة، Microsoft 365 الاستبقاء بدلا من ذلك.

بمجرد أن تصبح علبة البريد غير نشطة، يتم الاحتفاظ بمحتويات [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) علبة البريد بما في ذلك مجلد العناصر القابلة لاستردادها حتى لا يتم تطبيق فترة الانتظار التي تم وضعها على علبة البريد قبل أن تصبح غير نشطة.  

إذا لم يكن الاحتجاز المعمول به مستندا إلى الوقت، مثل احتجاز مقترن مع نهج استبقاء أو تسمية استبقاء خاصة ب Microsoft 365 فقط، أو حالة eDiscovery أو احتجاز بسبب الدعاوى القضائية (```LitigationHoldDuration```بدون تكوين)، سيتم الاحتفاظ بمحتوى علبة البريد إلى أجل غير مسمى حتى تتم إزالة الاحتجاز.  

ومع ذلك، إذا كانت فترة الانتظار مستندة إلى الوقت، سيتم الاحتفاظ بمحتوى علبة البريد حتى تنتهي مدة الانتظار، وعندها سيتم حذف أي عناصر في مجلد العناصر القابلة لاستردادها بشكل دائم (إزالة) من علبة البريد غير النشطة.

> [!NOTE]
> بالنسبة لعلب البريد غير النشطة، نوصي باستخدام إعداد استبقاء وحذف Microsoft 365 الاستبقاء أو التسميات.  إذا اخترت إعداد استبقاء فقط، سيحذف مجلد "العناصر القابلة لاستردادها" في نهاية مدة الانتظار، ولكن ستبقى أي عناصر أخرى غير محذوفة ضمن علبة البريد غير النشطة إلى أجل غير مسمى.

مع تطور اللوائح والسياسات، قد تحتاج في بعض الحالات إلى تغيير مدة فترة الانتظار المعينة إلى علبة البريد غير النشطة.  توضح الخطوات التالية كيفية القيام بذلك.

## <a name="connect-to-powershell"></a>الاتصال إلى PowerShell

كما ذكرنا من قبل، يمكن للعديد من الأنواع المختلفة من المواد أن تؤدي إلى إنشاء علبة بريد غير نشطة.  لهذا السبب، لتغيير مدة الانتظار المطبقة على علبة البريد غير النشطة، يجب أولا تحديد نوع فترات الانتظار التي تؤثر عليها.  للقيام بذلك، يجب استخدام Exchange Online PowerShell لتحديد أنواع احتجازات، وإذا كانت علبة البريد غير النشطة متأثرة ونهج استبقاء Microsoft 365 أو تسمياتها، فيجب عليك أيضا استخدام مركز الأمان والتوافق PowerShell لتحديد سياسات معينة.

- للاتصال ب Exchange Online PowerShell أو & مركز التوافق PowerShell، راجع أحد المواضيع التالية:

  - [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>الخطوة 1: تحديد المواد الموقوتة في علبة بريد غير نشطة

نظرا لأنه قد يتم وضع أنواع مختلفة من Microsoft 365 أو أكثر من سياسات الاستبقاء على علبة بريد غير نشطة، فإن الخطوة الأولى هي تحديد احتجازات علبة بريد غير نشطة.
  
تشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات الانتظار لعلبة بريد معينة غير نشطة في مؤسستك.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

إذا كنت بحاجة إلى تحديد نوع الانتظار لعلب البريد غير النشطة المتعددة وكان لمنظمتك عدد كبير منها، فقد يصبح من غير الممكن إدارة العرض باستخدام PowerShell. في هذه الحالة، يمكنك تصدير كل المعلومات القابلة للتطبيق إلى ملف CSV ```Path``` باستخدام الأمر التالي وتعديل كما هو مطلوب لبيئة:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

لأغراض هذا المثال، يعرض ما يلي نتائج لست علب بريد غير نشطة ذات أنواع مختلفة محتملة من الانتظار.

> [!NOTE]
> يمكن تطبيق العديد من عمليات التحمس بما في ذلك أنواع متعددة من عمليات التحكم على علبة بريد واحدة غير نشطة.
  
```text
DisplayName              : Ann Beebe
Name                     : annb
DistinguishedName        : CN=annb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 664ef44e-c1a0-47b0-9553-2ecdfc6ef840
IsInactiveMailbox        : True
LitigationHoldEnabled    : True
LitigationHoldDuration   : 365.00:00:00
LitigationHoldDate       : 10/25/2021 6:54:57 PM
LitigationHoldOwner      : admin@contoso.com
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Carol Olson
Name                     : carolo
DistinguishedName        : CN=carolo,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : e646a369-00bf-43d3-837a-8eae8b301d44
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbxcdbbb86ce60342489bff371876e7f224:3}
ComplianceTagHoldApplied : False
...
DisplayName              : Megan Bowen
Name                     : meganb
DistinguishedName        : CN=meganb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 36ec77cb-c524-468a-a8e8-bfb75e01a176
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbx6fe063689d404a5bb9940eed0f0bf5d2:1}
ComplianceTagHoldApplied : True
...
DisplayName              : Mario Necaise
Name                     : marion
DistinguishedName        : CN=marion,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 0579e039-a695-40d5-8f0a-0dc04f4b4c8f
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Abraham McMahon
Name                     : abrahamm
DistinguishedName        : CN=abrahamm,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 55ad8905-4e68-4c8d-940d-e068ec6b51fc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
ComplianceTagHoldApplied : False
...
DisplayName              : Pilar Pinilla
Name                     : pilarp
DistinguishedName        : CN=pilarp,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 8d7867d6-bb6d-4cd8-a51f-09d208f97fcc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {c0ba3ce811b6432a8751430937152491}
ComplianceTagHoldApplied : False
```

يحدد الجدول التالي أنواع الانتظار الستة المختلفة التي تم استخدامها لجعل كل علبة بريد غير نشطة من المثال أعلاه.
  
|**علبة البريد غير النشطة**|**نوع الانتظار**|**كيفية تحديد حالة الانتظار على علبة البريد غير النشطة**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |الاحتجاز القضائية  <br/> | تم  `LitigationHoldEnabled`  تعيين الخاصية إلى  `True` الإشارة إلى أن علبة البريد في وضع الاحتجاز بسبب الدعاوى القضائية. <br/><br/> بالإضافة إلى ذلك `LitigationHoldDuration` ، يتم تعيين للإشارة `365.00:00:00` إلى أن عناصر علبة البريد لن تخضع بعد الآن للدعاوى القضائية لمدة 365 يوما بعد تاريخ إنشائها (المرسل/المستلم).  <br/><br/> يشير `LitigationHoldDate` إلى تاريخ تمكين "التقاضي" `LitigationHoldOwner` ويحدد الشخص الذي بدأ الاحتجاز القضائية. <br/> |
|مهى  <br/> |Microsoft 365 الاستبقاء من مركز التوافق في Microsoft 365 الذي يتم تطبيقه على علب بريد معينة  <br/> |تحتوي `InPlaceHolds` الخاصية على GUID الخاص Microsoft 365 الاستبقاء المطبق على علبة البريد غير النشطة. يمكنك معرفة أن هذا نهج استبقاء تم تطبيقه على علب بريد معينة لأن GUID `mbx` يبدأ بالبادئ وينتهي ب أو `:2` `:3`. <br/><br/> لمزيد من المعلومات، راجع [فهم تنسيق القيمة InPlaceHolds لنهج الاستبقاء](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|ميغان بوين <br/> | Microsoft 365 تسمية استبقاء مع إجراء استبقاء أو الاحتفاظ به وحذفه على عنصر واحد على الأقل في علبة البريد  <br/> |تشير `ComplianceTagHoldApplied` الخاصية `True` إلى أنه قد تم تسمية عنصر مع تسمية الاحتفاظ أو الاحتفاظ بها وحذفها.  <br/><br/> بالإضافة إلى ذلك، تحتوي `InPlaceHolds` الخاصية على GUID الخاص Microsoft 365 تسمية الاستبقاء المطبق على علبة البريد غير النشطة.  <br/><br/> لمزيد من المعلومات، راجع تحديد علب البريد [الموقوقة بسبب تطبيق تسمية استبقاء على مجلد أو عنصر](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|مهى نكيسي  <br/> |نهج استبقاء Microsoft 365 المؤسسة من مركز التوافق في Microsoft 365  <br/> |الخاصية `InPlaceHolds` فارغة، `LitigationHoldEnabled` وهي `False` و`ComplianceTagHoldApplied`.`False` يشير ذلك إلى أنه تم تطبيق Exchange أو أكثر من Microsoft 365 الاستبقاء على المؤسسة التي ترثها علبة البريد غير النشطة. <br/><br/> لمزيد من المعلومات، [راجع كيفية تأكيد تطبيق نهج](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) استبقاء على مستوى المؤسسة على علبة بريد <br/> |
|نهاد ماكماهون  <br/> |eDiscovery case hold في مركز التوافق في Microsoft 365  <br/> |تحتوي  `InPlaceHolds`  الخاصية على GUID الخاص باحتواء حالة eDiscovery التي تم وضعها على علبة البريد غير النشطة. يمكنك معرفة أن هذه حالة eDiscovery لأن GUID يبدأ بالبادرة  `UniH` .  <br/><br/> لمزيد من المعلومات، راجع [يحتجز eDiscovery](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |In-Place الانتظار  <br/> |تحتوي  `InPlaceHolds`  الخاصية على GUID الخاص In-Place الموضع على علبة البريد غير النشطة. يمكنك معرفة أن هذه In-Place الانتظار لأن GUID لا يبدأ ببادرة.  <br/><br/> **ملاحظة**: حتى 1 أكتوبر 2020، لم يعد من الممكن تغيير مدة الاحتفاظ في مكانها. يمكنك فقط إزالة In-Place مع الاستمرار مما يؤدي إلى حذف علبة البريد غير النشطة. <br/><br/> لمزيد من المعلومات، راجع تقاعد [أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>الخطوة 2: تغيير مدة الانتظار لعلبة بريد غير نشطة

بعد تحديد نوع فترة الانتظار التي يتم وضعها على علبة البريد غير النشطة (وما إذا كان هناك العديد من عمليات الانتظار)، فإن الخطوة التالية هي تغيير مدة فترة الانتظار.  تختلف العملية استنادا إلى نوع الانتظار المطبق.

- [تغيير مدة نهج استبقاء Microsoft 365 البيانات](#change-the-duration-for-a-microsoft-365-retention-policy)

- [تغيير مدة تسمية Microsoft 365 الاستبقاء](#change-the-duration-for-a-microsoft-365-retention-label)

- [تغيير مدة الاحتفاظ ب eDiscovery](#change-the-duration-for-an-ediscovery-hold)

- [تغيير مدة الاحتجاز أمام الدعاوى القضائية](#change-the-duration-for-a-litigation-hold)

- [تغيير مدة مدة In-Place الانتظار](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>تغيير مدة نهج استبقاء Microsoft 365 البيانات

لتعديل مدة احتجاز نهج استبقاء Microsoft 365 `Get-RetentionCompliancePolicy` `InPlaceHolds`، يجب أولا تحديد النهج الذي يؤثر على علبة البريد غير النشطة من خلال تشغيل GUID المقترن من الخاصية على علبة البريد في مركز الأمان والتوافق PowerShell.

تأكد من إزالة البادرة وال لاحقة من GUID عند تشغيل هذا الأمر.  على سبيل المثال، باستخدام المعلومات العينة `InPlaceHolds` `:3` `mbxcdbbb86ce60342489bff371876e7f224:3` `mbx` الواردة من الأعلى، يمكنك أخذ قيمة ثم إزالتها مما يؤدي إلى نهج GUID ل .`cdbbb86ce60342489bff371876e7f224`  في هذا المثال، قد ترغب في تشغيل:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

بمجرد معرفة اسم النهج، يمكنك ببساطة تعديل نهج الاستبقاء في Microsoft 365 التوافق.  يجب أن تدرك أنه يتم عادة تطبيق نهج الاستبقاء على أكثر من موقع واحد، وبالتالي فإن تعديل النهج سيؤثر على كل المواقع المطبقة - غير النشطة والنشطة، والتي قد تتضمن أيضا مواقع أخرى غير Exchange.  لمزيد من المعلومات، راجع [إنشاء سياسات استبقاء وتكوينها](create-retention-policies.md).  

> [!IMPORTANT]
> يمكن [أن يتم تمديد](retention-preservation-lock.md) فترة الاستبقاء لنهج الاستبقاء مع تمكين تأمين الاحتفاظ، ولكن لا يمكن تقليلها أو إزالتها.

إذا كان الهدف من ذلك تعديل فترة الاستبقاء لعلب البريد غير النشطة فقط، أو علب بريد معينة غير نشطة فقط، فقد تفكر في نشر نطاقات النهج التكييفية، التي يمكن استخدامها لاستهداف علب بريد معينة بشكل فردي - أو أنواع علب بريد، مثل علب البريد غير النشطة - باستخدام سمات Azure AD وخصائص Exchange.[](retention.md#adaptive-or-static-policy-scopes-for-retention)

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>تغيير مدة تسمية Microsoft 365 الاستبقاء

كما هو الأمر مع نهج الاستبقاء، عند تعديل `Get-RetentionCompliancePolicy` `InPlaceHolds` مدة احتجاز تسمية استبقاء Microsoft 365، يجب أولا تحديد النهج الذي ينشر التسمية التي تؤثر على المحتوى داخل علبة البريد غير النشطة عن طريق تشغيل GUID المقترن من الخاصية على علبة البريد في مركز الأمان والتوافق PowerShell.

تأكد من إزالة البادرة وال لاحقة من GUID عند تشغيل هذا الأمر.  على سبيل المثال، باستخدام المعلومات العينة `InPlaceHolds` `:1` `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` `mbx` الواردة من الأعلى، يمكنك أخذ قيمة ثم إزالتها مما يؤدي إلى نهج GUID ل .`6fe063689d404a5bb9940eed0f0bf5d2`  في هذا المثال، قد ترغب في تشغيل:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

بعد تحديد النهج، ستعرف التسميات التي تم نشرها وإعداداتها.  نظرا لتطبيق التسميات على العناصر الفردية، استنادا إلى عدد التسميات المنشورة مع النهج والإعدادات الخاصة بها، فقد لا تتمكن من تحديد التسمية التي تؤثر على المحتوى مباشرة.  

إحدى الطرق التي يمكنك استخدامها لتعريف المحتوى الذي تنطبق عليه كل تسمية هي استخدام ["البحث في المحتوى](content-search.md)".  على سبيل المثال، باستخدام المعلومات العينة الواردة أعلاه، افترض أن النهج ينشر عدة تسميات، واحدة منها تسمى "HR-Content".  باستخدام الأذونات الصحيحة، يمكن تشغيل "البحث في المحتوى" باستخدام الأمر [New-ComplianceSearch PowerShell](/powershell/module/exchange/new-compliancesearch)، مع تحديد عنوان SMTP الأساسي لعلبة البريد غير النشطة، المكتتب مسبقا بجزرة (`.`)، `-AllowNotFoundExchangeLocationsEnabled $true` والمعلمة لتخطي التحقق من الصحة:[](microsoft-365-compliance-center-permissions.md)

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

بمجرد إنشاء البحث، ستبدأ عملية البحث باستخدام الأمر التالي:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

باستخدام هذا الأسلوب، يمكنك بعد ذلك تحديد التسميات من نهج التسمية المعرف التي تنطبق على المحتوى داخل علبة البريد غير النشطة بحيث يمكنك تعديل فترات الاستبقاء الخاصة بها. يجب أن تدرك أن تسميات الاستبقاء يتم تطبيقها عادة على أكثر من موقع واحد، وبالتالي فإن تعديل التسمية سيؤثر على كل المواقع المطبقة والمحتوى المسمى، والذي قد يتضمن أيضا مواقع ومحتوى غير Exchange. لمزيد من المعلومات، راجع [إنشاء تسميات استبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md).

> [!NOTE]
> لا يمكن تعديل كل أنواع تسميات الاستبقاء.  بالنسبة لبعض التسميات، قد تتمكن فقط من زيادة وقت الاستبقاء، وبالنسبة للآخرين، قد لا تتمكن من تعديل فترة الاستبقاء على الإطلاق.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>تغيير مدة الاحتفاظ ب eDiscovery

إن الاحتجازات المقترنة ب حالات eDiscovery هي عمليات الاحتجاز غير المتحملة، مما يعني أنه لا يمكن تغيير مدة الاحتجاز. يتم الاحتفاظ بالعناصر بشكل دائم أو حتى تتم إزالة حالة [الانتظار أو إغلاق](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) الحالة.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>تغيير مدة الاحتجاز أمام الدعاوى القضائية

يجب عليك استخدام Exchange Online PowerShell لتغيير مدة الاحتجاز بسبب الدعاوى القضائية الموضوعة على علبة بريد غير نشطة. لا يمكنك استخدام EAC. تشغيل الأمر التالي لتغيير مدة الانتظار. في هذا المثال، يتم تغيير مدة الانتظار إلى فترة زمنية غير محدودة:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

والنتيجة هي الاحتفاظ بالعناصر الموجودة في علبة البريد غير النشطة إلى أجل غير مسمى أو حتى تتم إزالة فترة الانتظار أو تغيير مدة الانتظار إلى قيمة مختلفة.
  
> [!TIP]
> أفضل طريقة لتحديد علبة بريد غير نشطة هي باستخدام الاسم المميز أو Exchange **GUID**. يساعد استخدام إحدى هذه القيم على منع تحديد علبة البريد الخطأ عن طريق الخطأ.

### <a name="change-the-duration-for-an-in-place-hold"></a>تغيير مدة مدة In-Place الانتظار

In-Place تم ازالته ولا يمكن تعديله. إذا كانت علبة البريد غير النشطة In-Place اضغط عليها، لا يمكنك تغيير مدة الانتظار. يمكنك فقط إزالة In-Place مع الاستمرار، مما يؤدي إلى حذف علبة البريد غير النشطة. لمزيد من المعلومات، راجع [حذف علبة بريد غير نشطة](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>معلومات إضافية

- **كيف يتم حساب مدة الانتظار الخاصة بعنصر في علبة بريد غير نشطة؟** يتم حساب المدة من التاريخ الأصلي الذي تم فيه استلام عنصر علبة بريد أو إنشائه.
    
- **ماذا يحدث عند انتهاء مدة الانتظار؟** عند انتهاء مدة الانتظار الخاصة بعنصر علبة بريد في مجلد العناصر القابلة للاسترداد، يتم حذف العنصر بشكل دائم (إزالة) من علبة البريد غير النشطة. إذا لم يتم تحديد أي مدة لفترة الانتظار الموضوعة على علبة البريد غير النشطة، فلا يتم أبدا إزالة العناصر الموجودة في مجلد العناصر القابلة لاستردادها (ما لم يتم تغيير مدة الانتظار لعلبة البريد غير النشطة). 
    
- **هل لا يزال Exchange MRM تتم معالجته على علب البريد غير النشطة؟**  إذا تم تطبيق نهج استبقاء MRM على علبة بريد قبل أن تكون غير نشطة، فإن أي نهج حذف (علامات استبقاء MRM تم تكوينها بواسطة إجراء **Delete** ) ستستمر في المعالجة على علبة البريد غير النشطة. وهذا يعني أنه سيتم نقل العناصر التي تم وضع علامة عليها باستخدام نهج حذف MRM إلى مجلد العناصر القابلة لاستردادها عند انتهاء فترة الاستبقاء. يتم إزالة هذه العناصر من علبة البريد غير النشطة عند انتهاء مدة الانتظار. إذا لم يتم تحديد مدة الانتظار لعلبة البريد غير النشطة، سيتم الاحتفاظ بالعناصر الموجودة في مجلد استرداد العناصر إلى أجل غير مسمى.

    وعلى العكس من ذلك، يتم تجاهل أي نهج أرشفة (علامات استبقاء MRM تم تكوينها مع إجراء **MoveToArchive** ) المضمنة في نهج استبقاء MRM المعين إلى علبة بريد غير نشطة. وهذا يعني أن العناصر الموجودة في علبة بريد غير نشطة تم وضع علامة عليها باستخدام نهج أرشيف تبقى في علبة البريد الأساسية عند انتهاء فترة الاستبقاء. ولا يتم نقلها إلى علبة بريد الأرشيف أو إلى مجلد العناصر القابلة لاستردادها في علبة بريد الأرشيف. سيتم الاحتفاظ بها إلى أجل غير مسمى.
    > [!NOTE]
    > لا ينشئ Exchange الاستبقاء (إدارة سجلات المراسلة أو MRM في Exchange Online) علبة بريد غير نشطة عند حذف حساب المستخدم.

- **وكما هو الأمر مع علب البريد العادية، يتولى مساعد المجلد المدار (MFA) أيضا عمليات علب البريد غير النشطة.** في Exchange Online، فإن MFA بمعالجة علب البريد مرة واحدة كل سبعة أيام تقريبا. بعد تغيير مدة الانتظار لعلبة بريد غير نشطة، يمكنك استخدام الأمر **cmdlet Start-ManagedFolderAssistant** لبدء معالجة مدة الانتظار الجديدة لعلبة البريد غير النشطة على الفور. قم بتشغيل الأمر التالي. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **إذا تم `InPlaceHolds` وضع العديد من العناصر على علبة بريد غير نشطة، لن يتم عرض كل GUIDs الموضعية.** يمكنك تشغيل الأمر التالي لعرض GUIDs `InPlaceHolds` لكل ما يتم وضعه على علبة بريد غير نشطة.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
