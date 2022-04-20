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
description: بعد جعل علبة بريد Office 365 غير نشطة، قم بتغيير مدة الاحتجاز أو Office 365 نهج الاستبقاء المعين إلى علبة البريد غير النشطة.
ms.openlocfilehash: d959195731ee0bf4de9b533f85fa2e2356259c12
ms.sourcegitcommit: 1d972f15a45204e89e268c5ff257021aced5e775
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/18/2022
ms.locfileid: "64911357"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>تغيير مدة الانتظار لعلبة بريد غير نشطة

[علبة البريد غير النشطة](inactive-mailboxes-in-office-365.md) هي حالة علبة البريد المستخدمة للاحتفاظ بالبريد الإلكتروني لموظف سابق بعد مغادرة مؤسستك. تصبح علبة البريد غير نشطة عند تطبيق قائمة احتجاز قابلة للتطبيق عليها قبل حذف كائن المستخدم Microsoft 365.  ستبدأ أنواع عمليات الاحتجاز التالية في إنشاء علبة بريد غير نشطة عند حذف حساب المستخدم:

- [Microsoft 365 نهج الاستبقاء والتسميات](retention.md) مع الاحتفاظ بالإعدادات أو الاحتفاظ بها وحذفها

- قائمة احتجاز مقترنة بحالة [eDiscovery](ediscovery.md)

- [احتجاز التقاضي](create-a-litigation-hold.md)

- قائمة احتجاز In-Place موجودة.

> [!IMPORTANT]
> في حين أن أي من عمليات الاحتجاز أعلاه ستجبر علبة البريد على أن تصبح غير نشطة عند حذف حساب المستخدم Microsoft 365، فمن المستحسن بشدة استخدام استبقاء Microsoft 365 عند التخطيط بشكل استباقي لاستخدام علب البريد غير النشطة.
>
> - قوائم احتجاز eDiscovery مخصصة لحالات محددة ومحددة زمنيا تتعلق بمشكلة قانونية. في مرحلة ما، من المحتمل أن تنتهي الدعوى القانونية وستتم إزالة عمليات الاحتجاز المقترنة بالحالة وسيتم إغلاق حالة eDiscovery (أو حذفها). إذا كانت قائمة الاحتجاز الموضوعة على علبة بريد غير نشطة مقترنة بحالة eDiscovery، وتم إصدار قائمة الاحتجاز أو تم إغلاق حالة eDiscovery أو حذفها، فسيتم حذف علبة البريد غير النشطة بشكل دائم.
>
> - تم الآن إيقاف In-Place قوائم الاحتجاز في مركز إدارة Exchange. اعتبارا من 1 يوليو 2020، تعذر إنشاء In-Place عمليات احتجاز جديدة في Exchange Online. اعتبارا من 1 أكتوبر 2020، لم يعد من الممكن تغيير مدة الاحتجاز الموضعي. يمكن حذف أي علبة بريد غير نشطة تم تطبيق تعليق In-Place عليها فقط عن طريق إزالة In-Place Hold. سيستمر الاحتفاظ بعلب البريد غير النشطة الموجودة في In-Place قائمة الاحتجاز حتى تتم إزالة قائمة الاحتجاز. لمزيد من المعلومات حول In-Place الإيقاف، راجع [تقاعد أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md).
>
> - يظل [احتجاز التقاضي](create-a-litigation-hold.md) معتمدا كطريقة بديلة للاحتفاظ بالمحتوى في علبة بريد وجعله غير نشط بعد حذف حساب مستخدم. ومع ذلك، وكتقنية قديمة، نوصي باستخدام استبقاء Microsoft 365 بدلا من ذلك.

بمجرد جعل علبة البريد غير نشطة، يتم الاحتفاظ بمحتويات علبة البريد بما في ذلك [مجلد العناصر القابلة للاسترداد](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) حتى لا يتم تطبيق قائمة الاحتجاز التي تم وضعها على علبة البريد قبل أن تصبح غير نشطة.  

إذا لم يكن الاحتجاز المعمول به مستندا إلى الوقت، مثل احتجاز مقترن بنهج استبقاء غير محدد Microsoft 365 فقط أو تسمية أو حالة eDiscovery أو احتجاز التقاضي (بدون ```LitigationHoldDuration``` تكوين)، فسيتم الاحتفاظ بمحتوى علبة البريد إلى أجل غير مسمى حتى تتم إزالة الاحتجاز.  

ومع ذلك، إذا كانت قائمة الاحتجاز تستند إلى الوقت، فسيتم الاحتفاظ بمحتوى علبة البريد حتى تنتهي مدة الاحتجاز، وعند هذه النقطة سيتم حذف أي عناصر في مجلد "العناصر القابلة للاسترداد" بشكل دائم (إزالتها) من علبة البريد غير النشطة.

> [!NOTE]
> بالنسبة إلى علب البريد غير النشطة، نوصي باستخدام إعداد الاحتفاظ والحذف لنهج استبقاء Microsoft 365 أو التسميات.  إذا اخترت إعداد استبقاء فقط، فسيتم إزالة مجلد العناصر القابلة للاسترداد في نهاية مدة الاحتجاز، ولكن ستبقى أي عناصر أخرى غير محذوفة ضمن علبة البريد غير النشطة إلى أجل غير مسمى.

مع تطور اللوائح والسياسات، قد تكون هناك بعض الحالات التي تحتاج فيها إلى تغيير مدة الاحتجاز المعينة إلى علبة البريد غير النشطة.  توضح الخطوات التالية كيفية القيام بذلك.

## <a name="connect-to-powershell"></a>الاتصال إلى PowerShell

كما ذكرنا من قبل، يمكن أن تؤدي العديد من أنواع الاحتجاز المختلفة إلى إنشاء علبة بريد غير نشطة.  لهذا السبب، لتغيير مدة الاحتجاز المطبقة على علبة البريد غير النشطة، يجب أولا تحديد نوع قوائم الاحتجاز التي تؤثر عليها.  للقيام بذلك، يجب استخدام Exchange Online PowerShell لتحديد أنواع قوائم الاحتجاز، وإذا تأثرت علبة البريد غير النشطة بنهج استبقاء Microsoft 365 أو التسميات، فيجب أيضا استخدام Security and Compliance Center PowerShell لتحديد النهج المحددة.

- للاتصال Exchange Online PowerShell أو Security & Compliance Center PowerShell، راجع أحد المواضيع التالية:

  - [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

  - [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>الخطوة 1: تحديد قوائم الاحتجاز على علبة بريد غير نشطة

نظرا لأنه قد يتم وضع أنواع مختلفة من قوائم الاحتجاز أو نهج استبقاء Microsoft 365 واحد أو أكثر على علبة بريد غير نشطة، فإن الخطوة الأولى هي تحديد قوائم الاحتجاز على علبة بريد غير نشطة.
  
قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض معلومات الاحتجاز لعلبة بريد غير نشطة معينة في مؤسستك.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

إذا كنت بحاجة إلى تحديد نوع الاحتجاز لعدة علب بريد غير نشطة وكان لدى مؤسستك عدد كبير منها، فقد يصبح من غير القابل لإدارة العرض باستخدام PowerShell. في هذه الحالة، يمكنك تصدير كافة المعلومات القابلة للتطبيق إلى ملف CSV باستخدام الأمر التالي وتعديلها ```Path``` حسب الحاجة للبيئة الخاصة بك:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

لأغراض هذا المثال، يعرض ما يلي نتائج لستة علب بريد غير نشطة مع أنواع احتجاز محتملة مختلفة.

> [!NOTE]
> يمكن تطبيق قوائم احتجاز متعددة بما في ذلك أنواع متعددة من قوائم الاحتجاز على علبة بريد غير نشطة واحدة.
  
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

يحدد الجدول التالي أنواع الاحتجاز الستة المختلفة التي تم استخدامها لجعل كل علبة بريد غير نشطة من المثال أعلاه.
  
|**علبة بريد غير نشطة**|**نوع قائمة الاحتجاز**|**كيفية تحديد قائمة الاحتجاز على علبة البريد غير النشطة**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |احتجاز التقاضي  <br/> | `LitigationHoldEnabled` تم تعيين الخاصية للإشارة إلى `True` أن علبة البريد موجودة في "احتجاز التقاضي". <br/><br/> بالإضافة إلى ذلك، `LitigationHoldDuration` تم تعيين الإشارة إلى `365.00:00:00` أن عناصر علبة البريد لن تخضع لفترة احتجاز التقاضي بعد 365 يوما من تاريخ إنشائها (تم إرسالها/تلقيها).  <br/><br/> `LitigationHoldDate` يشير إلى تاريخ تمكين "التقاضي" ويحدد `LitigationHoldOwner` الشخص الذي بدأ احتجاز التقاضي. <br/> |
|نايلة أولسون  <br/> |نهج استبقاء Microsoft 365 من مركز التوافق في Microsoft 365 التي يتم تطبيقها على علب بريد معينة  <br/> |`InPlaceHolds` تحتوي الخاصية على المعرف الفريد العمومي (GUID) لنهج الاستبقاء Microsoft 365 المطبق على علبة البريد غير النشطة. يمكنك معرفة أن هذا نهج استبقاء يتم تطبيقه على علب بريد معينة لأن GUID يبدأ بالبادئة `mbx` وينتهي ب a `:2` أو `:3`. <br/><br/> لمزيد من المعلومات، راجع [فهم تنسيق قيمة InPlaceHolds لنهج الاستبقاء](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|ميغان باين <br/> | يتم تطبيق تسمية استبقاء Microsoft 365 مع إجراء الاستبقاء أو الاستبقاء والحذف على عنصر واحد على الأقل في علبة البريد  <br/> |`ComplianceTagHoldApplied` تشير الخاصية `True` إلى أنه تم تسمية عنصر بتسمية الاحتفاظ أو الاحتفاظ بها وحذفها.  <br/><br/> بالإضافة إلى ذلك، `InPlaceHolds` تحتوي الخاصية على المعرف الفريد العمومي (GUID) لنهج تسمية استبقاء Microsoft 365 المطبق على علبة البريد غير النشطة.  <br/><br/> لمزيد من المعلومات، راجع [تحديد علب البريد قيد الاحتجاز بسبب تطبيق تسمية استبقاء على مجلد أو عنصر](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|نيكايس النيكاسية النيكاسية  <br/> |نهج استبقاء Microsoft 365 على مستوى المؤسسة من مركز التوافق في Microsoft 365  <br/> |الخاصية `InPlaceHolds` فارغة، `LitigationHoldEnabled` وهي`False`.`ComplianceTagHoldApplied` `False` يشير هذا إلى أن موقعا واحدا أو أكثر بالكامل (Exchange) Microsoft 365 نهج الاستبقاء المطبقة على المؤسسة التي ترثها علبة البريد غير النشطة. <br/><br/> لمزيد من المعلومات، راجع [كيفية تأكيد تطبيق نهج استبقاء على مستوى المؤسسة على علبة بريد](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|أبراهام ماكماهون  <br/> |احتجاز حالة eDiscovery في مركز التوافق في Microsoft 365  <br/> |`InPlaceHolds` تحتوي الخاصية على GUID للاحتفاظ بحالة eDiscovery الموضوعة على علبة البريد غير النشطة. يمكنك معرفة أن هذه حالة احتجاز eDiscovery لأن GUID يبدأ بالبادئة  `UniH` .  <br/><br/> لمزيد من المعلومات، راجع [قوائم احتجاز eDiscovery](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |احتجاز In-Place  <br/> |`InPlaceHolds` تحتوي الخاصية على المعرف الفريد العمومي (GUID) In-Place Hold الذي تم وضعه على علبة البريد غير النشطة. يمكنك معرفة أن هذا In-Place قائمة احتجاز لأن GUID لا يبدأ بالبادئة.  <br/><br/> **ملاحظة**: اعتبارا من 1 أكتوبر 2020، لم يعد من الممكن تغيير مدة الاحتجاز الموضعي. يمكنك إزالة In-Place قائمة احتجاز فقط مما سيؤدي إلى حذف علبة البريد غير النشطة. <br/><br/> لمزيد من المعلومات، راجع [تقاعد أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>الخطوة 2: تغيير مدة احتجاز علبة بريد غير نشطة

بعد تحديد نوع الاحتجاز الذي يتم وضعه على علبة البريد غير النشطة (وما إذا كان هناك عدة قوائم احتجاز)، فإن الخطوة التالية هي تغيير مدة الاحتجاز.  تختلف العملية حسب نوع الاحتجاز المطبق.

- [تغيير مدة نهج استبقاء Microsoft 365](#change-the-duration-for-a-microsoft-365-retention-policy)

- [تغيير مدة تسمية استبقاء Microsoft 365](#change-the-duration-for-a-microsoft-365-retention-label)

- [تغيير مدة احتجاز eDiscovery](#change-the-duration-for-an-ediscovery-hold)

- [تغيير مدة احتجاز التقاضي](#change-the-duration-for-a-litigation-hold)

- [تغيير مدة احتجاز In-Place](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>تغيير مدة نهج استبقاء Microsoft 365

لتعديل مدة الاحتجاز لنهج استبقاء Microsoft 365، يجب أولا تحديد النهج الذي يؤثر على علبة البريد غير النشطة عن طريق تشغيل `Get-RetentionCompliancePolicy` GUID المقترن من `InPlaceHolds` الخاصية على علبة البريد في مركز الأمان والتوافق PowerShell.

تأكد من إزالة البادئة واللاحقة من GUID عند تشغيل هذا الأمر.  على سبيل المثال، باستخدام عينة المعلومات الواردة أعلاه، يمكنك أخذ `InPlaceHolds` قيمة `mbxcdbbb86ce60342489bff371876e7f224:3` ثم إزالتها `mbx` والناتج `:3` عن المعرف الفريد العمومي (GUID) للنهج.`cdbbb86ce60342489bff371876e7f224`  في هذا المثال، تريد تشغيل:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

بمجرد معرفة اسم النهج، يمكنك ببساطة تعديل نهج الاستبقاء في مركز التوافق Microsoft 365.  كن على علم بأن نهج الاستبقاء تطبق عادة على أكثر من موقع واحد، لذلك سيؤثر تعديل النهج على جميع المواقع المطبقة - سواء كانت غير نشطة أو نشطة، والتي قد تتضمن أيضا مواقع أخرى غير Exchange.  لمزيد من المعلومات، راجع [إنشاء نهج الاستبقاء وتكوينها](create-retention-policies.md).  

> [!IMPORTANT]
> يمكن أن تم تمديد فترة الاستبقاء لنهج [الاستبقاء مع تمكين تأمين الاحتفاظ](retention-preservation-lock.md) ، ولكن لا يتم تقليلها أو إزالتها.

إذا كان الهدف هو تعديل فترة الاستبقاء لعلب البريد غير النشطة فقط، أو علب البريد غير النشطة المحددة فقط، فقد تفكر في نشر [نطاقات النهج التكيفية](retention.md#adaptive-or-static-policy-scopes-for-retention)، والتي يمكن استخدامها لاستهداف علب بريد معينة بشكل فردي - أو أنواع علب البريد، مثل علب البريد غير النشطة - باستخدام Azure AD وسمات وخصائص Exchange.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>تغيير مدة تسمية استبقاء Microsoft 365

كما هو الحال مع نهج الاستبقاء، عند تعديل مدة احتجاز تسمية استبقاء Microsoft 365، يجب أولا تحديد النهج الذي ينشر التسمية التي تؤثر على المحتوى داخل علبة البريد غير النشطة عن طريق تشغيل `Get-RetentionCompliancePolicy` GUID المقترن من `InPlaceHolds` الخاصية على علبة البريد في مركز الأمان والتوافق PowerShell.

تأكد من إزالة البادئة واللاحقة من GUID عند تشغيل هذا الأمر.  على سبيل المثال، باستخدام عينة المعلومات الواردة أعلاه، يمكنك أخذ `InPlaceHolds` قيمة `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` ثم إزالتها `mbx` والناتج `:1` عن المعرف الفريد العمومي (GUID) للنهج.`6fe063689d404a5bb9940eed0f0bf5d2`  في هذا المثال، تريد تشغيل:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

بمجرد تحديد النهج، ستعرف التسميات التي تم نشرها وإعداداتها.  نظرا لتطبيق التسميات على العناصر الفردية، استنادا إلى عدد التسميات المنشورة مع النهج وإعداداتها، قد لا تتمكن من تحديد التسمية التي تؤثر على المحتوى مباشرة.  

أحد الأساليب التي يمكنك استخدامها لتعريف المحتوى الذي تنطبق عليه كل تسمية هو استخدام ["البحث في المحتوى](content-search.md)".  على سبيل المثال، باستخدام عينة المعلومات الواردة أعلاه، افترض أن النهج ينشر العديد من التسميات، واحدة منها تسمى "HR-Content".  باستخدام [الأذونات الصحيحة](microsoft-365-compliance-center-permissions.md)، يمكن تشغيل البحث عن المحتوى باستخدام [الأمر New-ComplianceSearch PowerShell](/powershell/module/exchange/new-compliancesearch)، مع تحديد عنوان SMTP الأساسي لعلبة البريد غير النشطة، وقلم مسبقا بنقطة (`.`)، والمعلمة `-AllowNotFoundExchangeLocationsEnabled $true` لتخطي التحقق من الصحة:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

بمجرد إنشاء البحث، ستبدأ البحث باستخدام الأمر التالي:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

باستخدام هذا الأسلوب، يمكنك بعد ذلك تحديد التسميات من نهج التسميات المحددة التي تنطبق على المحتوى داخل علبة البريد غير النشطة بحيث يمكنك تعديل فترات الاستبقاء الخاصة بها. تجدر الإشارة إلى أنه يتم عادة تطبيق تسميات الاستبقاء على أكثر من موقع واحد، لذلك سيؤثر تعديل التسمية على جميع المواقع المطبقة والمحتوى المسمى، والذي قد يتضمن أيضا مواقع ومحتوى آخر غير Exchange. لمزيد من المعلومات، راجع [نشر تسميات الاستبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md).

> [!NOTE]
> لا يمكن تعديل كافة أنواع تسميات الاستبقاء.  بالنسبة لبعض التسميات، قد تتمكن فقط من زيادة وقت الاستبقاء، وبالنسبة إلى البعض الآخر، قد لا تتمكن من تعديل فترة الاستبقاء على الإطلاق.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>تغيير مدة احتجاز eDiscovery

تعد عمليات الاحتجاز المقترنة بحالات eDiscovery احتجازا غير محدد، ما يعني أنه لا توجد مدة احتجاز يمكن تغييرها. يتم الاحتفاظ بالعناصر إلى الأبد أو حتى [تتم إزالة الاحتجاز](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) أو إغلاق الحالة.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>تغيير مدة احتجاز التقاضي

يجب استخدام Exchange Online PowerShell لتغيير مدة الاحتجاز ل "احتجاز التقاضي" الذي يتم وضعه على علبة بريد غير نشطة. لا يمكنك استخدام EAC. قم بتشغيل الأمر التالي لتغيير مدة الاحتجاز. في هذا المثال، يتم تغيير مدة الاحتجاز إلى فترة زمنية غير محدودة:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

والنتيجة هي الاحتفاظ بالعناصر الموجودة في علبة البريد غير النشطة إلى أجل غير مسمى أو حتى تتم إزالة قائمة الاحتجاز أو تغيير مدة الاحتجاز إلى قيمة مختلفة.
  
> [!TIP]
> أفضل طريقة لتعريف علبة بريد غير نشطة هي باستخدام **الاسم المميز** أو **قيمة GUID Exchange**. يساعد استخدام إحدى هذه القيم على منع تحديد علبة البريد الخطأ عن طريق الخطأ.

### <a name="change-the-duration-for-an-in-place-hold"></a>تغيير مدة احتجاز In-Place

In-Place تم إيقاف عمليات الاحتجاز ولم يعد من الممكن تعديلها. إذا تم تطبيق تعليق In-Place على علبة بريد غير نشطة، فلا يمكنك تغيير مدة الاحتجاز. يمكنك إزالة In-Place قائمة الاحتجاز فقط، مما سيؤدي إلى حذف علبة البريد غير النشطة. لمزيد من المعلومات، راجع [حذف علبة بريد غير نشطة](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>معلومات إضافية

- **كيف يتم حساب مدة الاحتجاز لعنصر في علبة بريد غير نشطة؟** يتم حساب المدة من التاريخ الأصلي الذي تم فيه تلقي عنصر علبة بريد أو إنشائه.
    
- **ماذا يحدث عند انتهاء مدة الاحتجاز؟** عند انتهاء مدة الاحتجاز لعنصر علبة بريد في مجلد "العناصر القابلة للاسترداد"، يتم حذف العنصر نهائيا (تتم إزالته) من علبة البريد غير النشطة. إذا لم تكن هناك مدة محددة للاحتفاظ بعلبة البريد غير النشطة، فلن تتم إزالة العناصر الموجودة في مجلد "العناصر القابلة للاسترداد" (إلا إذا تم تغيير مدة احتجاز علبة البريد غير النشطة). 
    
- **هل لا يزال نهج EXCHANGE MRM قيد المعالجة على علب البريد غير النشطة؟**  إذا تم تطبيق نهج استبقاء MRM على علبة بريد قبل أن تصبح غير نشطة، فستستمر معالجة أي نهج حذف (علامات استبقاء MRM تم تكوينها بواسطة إجراء **حذف** ) على علبة البريد غير النشطة. وهذا يعني أنه سيتم نقل العناصر التي تم وضع علامة عليها باستخدام نهج حذف MRM إلى مجلد العناصر القابلة للاسترداد عند انتهاء فترة الاستبقاء. تتم إزالة هذه العناصر من علبة البريد غير النشطة عند انتهاء مدة الاحتجاز. إذا لم يتم تحديد مدة احتجاز لعلدة البريد غير النشطة، فسيتم الاحتفاظ بالعناصر الموجودة في مجلد "استرداد العناصر" إلى أجل غير مسمى.

    وعلى العكس من ذلك، يتم تجاهل أي نهج أرشيف (علامات استبقاء MRM تم تكوينها باستخدام إجراء **MoveToArchive** ) المضمنة في نهج استبقاء MRM المعين إلى علبة بريد غير نشطة. وهذا يعني أن العناصر الموجودة في علبة بريد غير نشطة والتي تم وضع علامة عليها باستخدام نهج أرشيف تبقى في علبة البريد الأساسية عند انتهاء فترة الاستبقاء. ولا يتم نقلها إلى علبة بريد الأرشيف أو إلى مجلد العناصر القابلة للاسترداد في علبة بريد الأرشيف. سيتم الاحتفاظ بها إلى أجل غير مسمى.
    > [!NOTE]
    > لا يؤدي تطبيق نهج استبقاء Exchange (إدارة سجلات المراسلة أو ميزة MRM في Exchange Online) إلى إنشاء علبة بريد غير نشطة عند حذف حساب المستخدم.

- **كما هو الحال مع علب البريد العادية، يعالج مساعد المجلد المدار (MFA) أيضا علب البريد غير النشطة.** في Exchange Online، تعالج المصادقة متعددة العوامل علب البريد مرة واحدة تقريبا كل سبعة أيام. بعد تغيير مدة احتجاز علبة بريد غير نشطة، يمكنك استخدام الأمر cmdlet **Start-ManagedFolderAssistant** لبدء معالجة مدة الاحتجاز الجديدة لعلدة البريد غير النشطة على الفور. قم بتشغيل الأمر التالي. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **إذا تم وضع العديد منها `InPlaceHolds` على علبة بريد غير نشطة، فلن يتم عرض كافة معرفات واجهة المستخدم الرسومية للاحتفاظ بها.** يمكنك تشغيل الأمر التالي لعرض معرفات المستخدم الرسومية لكل `InPlaceHolds` ما يتم وضعه على علبة بريد غير نشطة.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
