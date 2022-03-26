---
title: حذف علبة بريد غير نشطة
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: f5caf497-5e8d-4b7a-bfff-d02942f38150
ms.custom:
- seo-marvel-apr2020
description: عندما لا تحتاج إلى الاحتفاظ بمحتويات علبة بريد Microsoft 365 غير نشطة، يمكنك حذف علبة البريد غير النشطة بشكل دائم.
ms.openlocfilehash: 71223c0b5f53e03d51797e32f249f24146e96dee
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63567123"
---
# <a name="delete-an-inactive-mailbox"></a>حذف علبة بريد غير نشطة

يتم استخدام علبة بريد غير نشطة للحفاظ على البريد الإلكتروني الخاص بموظف سابق بعد مغادرته مؤسستك. عندما لا تحتاج إلى الاحتفاظ بمحتويات علبة البريد غير النشطة، يمكنك حذف علبة البريد غير النشطة نهائيا عن طريق إزالة فترة الانتظار. كما أنه من المحتمل أن يتم وضع العديد من عمليات التحمس على علبة بريد غير نشطة. على سبيل المثال، قد يتم وضع علبة بريد غير نشطة في "الاحتجاز بسبب الدعاوى القضائية" وعلى علبة بريد In-Place أخرى. بالإضافة إلى ذلك، قد يتم تطبيق نهج استبقاء (تم إنشاؤه في مركز الأمان والتوافق في Office 365 أو Microsoft 365) على علبة البريد غير النشطة. يجب إزالة كل ونهج الاستبقاء والاستبقاء من علبة بريد غير نشطة لحذفها. بعد إزالة سياسة الاحتفاظ والاستبقاء، يتم وضع علامة على علبة البريد غير النشطة للحذف، ثم يتم حذفها نهائيا بعد معالجتها.
  
> [!IMPORTANT]
> بينما نستمر في الاستثمار بطرق مختلفة للحفاظ على محتوى علبة البريد، نعلن عن In-Place في مركز إدارة Exchange الإلكتروني. وهذا يعني أنه يجب عليك استخدام "الاحتجازات القضائية" ونهج الاستبقاء لإنشاء علبة بريد غير نشطة. بدءا من 1 يوليو 2020، لن تتمكن من إنشاء In-Place جديدة في Exchange Online. ولكن سيبقى بإمكانك تغيير مدة الانتظار الخاصة ب In-Place قيد الانتظار في علبة بريد غير نشطة. ومع ذلك، بدءا من 1 أكتوبر 2020، لن تتمكن من تغيير مدة الانتظار. لن تتمكن من حذف علبة بريد غير نشطة إلا عن طريق إزالة In-Place الانتظار. ستحتفظ علب البريد غير النشطة الموجودة In-Place مع الاستمرار في الانتظار حتى تتم إزالة الاستمرار. لمزيد من المعلومات حول تقاعد In-Place، راجع تقاعد [أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md).
  
راجع القسم [مزيد من المعلومات](#more-information) للحصول على وصف لما يحدث بعد إزالة التعليقات من علبة بريد غير نشطة.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>قبل حذف علبة بريد غير نشطة

- يجب عليك استخدام Exchange Online PowerShell لإزالة "الاحتجاز بسبب الدعاوى القضائية" من علبة بريد غير نشطة. لا يمكنك استخدام مركز إدارة Exchange (EAC). للحصول على إرشادات مفصلة خطوة بخطوة، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يمكنك نسخ محتويات علبة بريد غير نشطة إلى علبة بريد أخرى قبل إزالة الانتظار وحذف علبة بريد غير نشطة. للحصول على التفاصيل، راجع [استعادة علبة بريد غير نشطة في](restore-an-inactive-mailbox.md) Office 365.

- إذا قمت بإزالة نهج الاحتفاظ أو الاستبقاء من علبة بريد غير نشطة وانتهاء فترة استبقاء علبة البريد المحذوفة بشكل تلقائي، سيتم حذف علبة البريد نهائيا بعد انتهاء فترة استبقاء علبة البريد المحذوفة بشكل تلقائي والمنتهية لمدة 183 يوما. لمزيد من المعلومات حول فترة استبقاء علبة البريد المحذوفة بشكل تلقائي، راجع القسم [مزيد](#more-information) من المعلومات في هذه المقالة. بعد حذف علبة البريد غير النشطة نهائيا، لا يمكن استردادها. قبل إزالة فترة الانتظار، تأكد من أنك لم تعد بحاجة إلى المحتويات في علبة البريد. إذا كنت تريد إعادة تنشيط علبة بريد غير نشطة، يمكنك استردادها. للحصول على التفاصيل، راجع [استرداد علبة بريد غير نشطة في](recover-an-inactive-mailbox.md) Office 365.

- لمزيد من المعلومات حول علب البريد غير النشطة، راجع [التعرف على علب البريد غير النشطة](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>الخطوة 1: تحديد المواد الموقوتة في علبة بريد غير نشطة

كما ذكر سابقا، قد يتم وضع نهج الاحتجاز In-Place أو الاحتجاز أو الاستبقاء على علبة بريد غير نشطة. الخطوة الأولى هي تحديد المواد الموقوتة في علبة بريد غير نشطة.
  
تشغيل الأمر التالي لعرض معلومات الانتظار لكل علب البريد غير النشطة في مؤسستك.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

تشير قيمة **True** للممتلكات **LitigationHoldEnabled** إلى أن علبة البريد غير النشطة في الاحتجاز بسبب الدعاوى القضائية. إذا تم In-Place قيد الانتظار على علبة بريد غير نشطة، يتم عرض GUID الخاص بالموضع الموضعي كقيمة للممتلكات **InPlaceHolds** . على سبيل المثال، تظهر النتائج التالية لعلب بريد غير نشطة أنه تم وضع "احتجاز بسبب الدعاوى القضائية" على "آن بيبي" وأن In-Place "الاحتجاز والاستبقاء" موضوع على Pilar Pinilla.
  
```text
DisplayName           : Ann Beebe
Name                  : annb
IsInactiveMailbox     : True
LitigationHoldEnabled : True
InPlaceHolds          : {}
...
DisplayName           : Pilar Pinilla
Name                  : pilarp
IsInactiveMailbox     : True
LitigationHoldEnabled : False
InPlaceHolds          : {c0ba3ce811b6432a8751430937152491, mbxba6f4ba25b62490aaaa253eea27426ab}
```

> [!TIP]
> إذا تم وضع In-Place الاحتفاظ أو الاستبقاء في علبة بريد غير نشطة، لن يتم عرض In-Place مع الاستمرار في GUIDs. يمكنك تشغيل الأمر التالي لعرض كل GUIDs في الخاصية InPlaceHolds:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
لمزيد من المعلومات حول تحديد المواضع المحتفظ بها، راجع كيفية تحديد نوع الانتظار [الموضوع على علبة بريد](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>الخطوة 2: إزالة الانتظار من علبة بريد غير نشطة

بعد تحديد نوع فترة الانتظار التي يتم وضعها على علبة البريد غير النشطة (وما إذا كان هناك العديد من عمليات الانتظار)، فإن الخطوة التالية هي إزالة عمليات الانتظار على علبة البريد. كما ذكر سابقا، يجب إزالة كل المواخير لحذف علبة بريد غير نشطة بشكل دائم.
  
### <a name="remove-a-litigation-hold"></a>إزالة الاحتجاز في الدعاوى القضائية

كما ذكر سابقا، يجب استخدام Windows PowerShell لإزالة "الاحتجاز بسبب الدعاوى القضائية" من علبة بريد غير نشطة. لا يمكنك استخدام EAC. قم بتشغيل الأمر التالي لإزالة الاحتجاز بسبب الدعاوى القضائية.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> إن أفضل طريقة لتحديد علبة بريد غير نشطة هي باستخدام الاسم المميز أو Exchange GUID. يساعد استخدام إحدى هذه القيم على منع تحديد علبة البريد الخطأ عن طريق الخطأ. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>إزالة علبة بريد غير نشطة من نهج استبقاء

يعتمد الإجراء الخاص بإزالة علبة بريد غير نشطة من نهج استبقاء Microsoft 365 على ما إذا كان نهج الاستبقاء المعين لعلبة البريد غير النشطة على مستوى المؤسسة أو صريحا. على نوع نهج الاستبقاء المعين إلى علبة البريد غير النشطة.

- تم تعيين سياسات استبقاء على مستوى المؤسسة لكل علب البريد في المؤسسة. استخدم **الأمر Get-OrganizationConfig** cmdlet Exchange Online PowerShell للحصول على معلومات حول سياسات الاستبقاء على مستوى المؤسسة.

- تم تعيين سياسات استبقاء مواقع معينة لعلب بريد معينة. هذه هي السياسات التي تم تعيينها إلى مواقع المحتوى الخاصة بمستخدمين معينين. استخدم **الأمر cmdlet Get-Mailbox -IncludeInactiveMailbox** في Exchange Online PowerShell للحصول على معلومات حول سياسات الاستبقاء المعينة لعلب بريد معينة غير نشطة.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>إزالة علبة بريد غير نشطة من نهج استبقاء على مستوى المؤسسة

تشغيل الأمر التالي في Exchange Online PowerShell لاستبعاد علبة بريد غير نشطة من نهج استبقاء على مستوى المؤسسة.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

لمزيد من المعلومات حول تحديد نهج الاستبقاء على مستوى المؤسسة المطبقة على علبة بريد غير نشطة والحصول على GUID لنهج استبقاء، راجع القسم "Get-OrganizationConfig" في كيفية تحديد نوع الانتظار الموضوع على علبة [بريد.](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig)

بدلا من ذلك، يمكنك تشغيل الأمر التالي لإزالة علبة البريد غير النشطة من كل السياسات على مستوى المؤسسة:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>إزالة علبة بريد غير نشطة من نهج استبقاء موقع معين

قم بتشغيل الأمر التالي في [& مركز التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell) لإزالة علبة بريد غير نشطة من نهج استبقاء صريح.

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -AddExchangeLocationException <identity of inactive mailbox>
```

لمزيد من المعلومات حول تحديد نهج استبقاء الموقع المحددة المطبقة على علبة بريد غير نشطة والحصول على GUID لنهج استبقاء، راجع القسم "الحصول على علبة البريد" في كيفية تحديد نوع الانتظار الموضوع على علبة [بريد](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox).

### <a name="remove-in-place-holds"></a>إزالة In-Place الموازل

 هناك طريقتان لإزالة In-Place مع الاستمرار من علبة بريد غير نشطة:
  
- **احذف In-Place مع الاستمرار**. إذا كانت علبة البريد غير النشطة التي تريد حذفها بشكل دائم هي علبة البريد المصدر الوحيدة In-Place Hold، يمكنك فقط حذف In-Place Hold. 

    > [!NOTE]
    > يجب تعطيل الاستمرار قبل أن تتمكن من حذف In-Place Hold. إذا حاولت حذف In-Place مع الاستمرار تم تمكينه، ستتلقى رسالة خطأ. 
  
- **قم بإزالة علبة البريد غير النشطة كعلبة بريد مصدر In-Place الانتظار**. إذا كنت تريد الاحتفاظ لعلب بريد المصدر الأخرى In-Place Hold، يمكنك إزالة علبة البريد غير النشطة من قائمة علب البريد المصدر والاحتفاظ In-Place Hold.

#### <a name="delete-an-in-place-hold"></a>حذف In-Place مع الاستمرار

1. أنشئ متغيرا يحتوي على خصائص In-Place الذي تريد حذفه. استخدم In-Place مع الاستمرار في GUID التي حصلت عليها في الخطوة 1: تحديد عدد الانتظار [في علبة بريد غير نشطة](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. قم بتعطيل الانتظار على In-Place الانتظار.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. احذف In-Place الانتظار.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>إزالة علبة بريد غير نشطة من In-Place الانتظار

إذا احتوى In-Place Hold على عدد كبير من علب البريد المصدر، فمن المحتمل ألا تكون علبة البريد غير النشطة مدرجة في صفحة المصادر في EAC. يتم عرض ما يصل إلى 3000 علبة بريد على صفحة المصادر عند  تحرير In-Place الانتظار. إذا لم تكن علبة البريد غير النشطة مدرجة في صفحة المصادر،  يمكنك استخدام Exchange Online PowerShell لإزالتها من In-Place الانتظار. 
  
1. أنشئ متغيرا يحتوي على خصائص In-Place قيد الانتظار الموضوعة على علبة البريد غير النشطة. استخدم In-Place مع الاستمرار في GUID التي حصلت عليها في الخطوة 1: تحديد عدد الانتظار [في علبة بريد غير نشطة](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. تحقق من أن علبة البريد غير النشطة مدرجة كعلبة بريد مصدر In-Place الانتظار. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > تحدد *الخاصية Sources* الخاصة In-Place Hold علب البريد المصدر من خلال خصائص *LegacyExchangeDN* الخاصة بها. نظرا لأن هذه الخاصية تعرف علب البريد غير النشطة بشكل فريد، فإن  استخدام الخاصية مصادر من In-Place Hold يساعد على منع إزالة علبة البريد الخطأ. يساعد ذلك أيضا على تجنب المشاكل إذا كان لعلبة بريد نفس الاسم المستعار أو عنوان SMTP. 

3. قم بإزالة علبة البريد غير النشطة من قائمة علب البريد المصدر في المتغير. تأكد من استخدام **LegacyExchangeDN** لعلبة البريد غير النشطة التي تم إرجاعها بواسطة الأمر في الخطوة السابقة. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    على سبيل المثال، يزيل الأمر التالي علبة البريد غير النشطة ل Pilar Pinilla.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. تحقق من إزالة علبة البريد غير النشطة من قائمة علب البريد المصدر في المتغير.

   ```powershell
   $InPlaceHold.Sources
   ```

5. قم بتعديل In-Place مع قائمة علب البريد المصدر المحدثة، التي لا تتضمن علبة البريد غير النشطة.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. تحقق من إزالة علبة البريد غير النشطة من قائمة علب البريد المصدر In-Place الانتظار.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>معلومات إضافية

- **إن علبة البريد غير النشطة هي نوع من علب البريد المحذوفة بشكل تلقائي.** في Exchange Online، تكون علبة البريد المحذوفة بشكل تلقائي علبة بريد تم حذفها ولكن يمكن استردادها خلال فترة استبقاء معينة. بالنسبة إلى علب البريد المحذوفة بشكل تلقائي غير الموقوفة، يمكن استرداد علبة البريد في غضون 30 يوما. ستبقى علبة البريد غير النشطة (علبة البريد في وضع الانتظار قبل حذفها) في حالة الحذف الناعم مع حالة الانتظار حتى تتم إزالة الاستمرار. بعد إزالة فترة الانتظار من علبة بريد غير نشطة، لن تكون علبة البريد في حالة غير نشطة. بدلا من ذلك، سيتم حذفه تلقائيا وسيظل في Exchange Online لمدة 183 يوما من اليوم الذي تمت فيه إزالة فترة الانتظار واستردادها خلال هذه الفترة. بعد مرور 183 يوما، يتم وضع علامة على علبة بريد محذوفة بشكل تلقائي للحذف الدائم ولا يمكن استردادها.

- **ماذا يحدث بعد إزالة الاستمرار في علبة بريد غير نشطة؟** يتم التعامل مع علبة البريد مثل علب البريد الأخرى المحذوفة بشكل تلقائي، كما يتم وضع علامة عليها للحذف الدائم بعد انتهاء فترة استبقاء علبة البريد المحذوفة بشكل تلقائي لمدة 183 يوما. تبدأ فترة الاستبقاء هذه في تاريخ إزالة فترة الانتظار من علبة البريد غير النشطة. يتم تعيين الخاصية *InactiveMailboxRetireTime* عندما يتم نقل علبة البريد من وضع غير نشط (تم حذفه بشكل تلقائي مع الاستمرار) إلى لم يعد غير نشط (محذوف بشكل تلقائي بدون أي عمليات توقف). في هذه المرحلة، يتم تعيين الخاصية *InactiveMailboxRetireTime* إلى التاريخ الحالي عند حدوث الانتقال. هناك مساعد يتم تشغيله (يسمى مساعد *MailboxLifeCycle* ) الذي تبحث عن علب البريد التي تم تعيين الخاصية *InactiveMailboxRetireTime* لها. إذا كانت "InactiveMailboxRetireTime + 183 يوما" أقل من التاريخ الحالي، فقم ب إزالة علبة البريد.

- **هل يتم حذف علبة بريد غير نشطة بشكل دائم مباشرة بعد إزالة فترة الانتظار؟** ستتوفر علبة بريد غير نشطة سابقا في حالة الحذف الناعم لمدة 183 يوما. بعد مرور 183 يوما، سيتم وضع علامة على علبة البريد للحذف الدائم.

- **كيف تعرض معلومات حول علبة بريد غير نشطة بعد إزالة فترة الانتظار؟** بعد إزالة فترة الانتظار وعودة علبة البريد غير النشطة إلى علبة بريد محذوفة بشكل تلقائي، لن يتم إرجاعها باستخدام المعلمة  *InactiveMailboxOnly*  مع أمر cmdlet **Get-Mailbox** . ولكن يمكنك عرض معلومات حول علبة البريد باستخدام الأمر **Get-Mailbox -SoftDeletedMailbox** . على سبيل المثال:

  ```text
  Get-Mailbox -SoftDeletedMailbox -Identity pilarp | FL Name,Identity,LitigationHoldEnabled,In
  Placeholds,WhenSoftDeleted,IsInactiveMailbox,WasInactiveMailbox,InactiveMailboxRetireTime
  Name                   : pilarp
  Identity               : Soft Deleted Objects\pilarp
  LitigationHoldEnabled  : False
  InPlaceHolds           : {}
  WhenSoftDeleted        : 6/16/2020 1:19:04 AM
  IsInactiveMailbox      : False
  WasInactiveMailbox     : True
  InactiveMailboxRetireTime : 9/30/2020 11:16:23 PM
  ```

  في المثال أعلاه، تحدد الخاصية *WhenSoftDeleted* تاريخ الحذف الناعم، وهو في هذا المثال 16 يونيو 2020. يتم *سرد الخاصية WasInactiveMailbox* على أنها `True` كانت في السابق علبة بريد غير نشطة. سيتم حذف علبة البريد نهائيا بعد 183 يوما من 30 سبتمبر 2020.
