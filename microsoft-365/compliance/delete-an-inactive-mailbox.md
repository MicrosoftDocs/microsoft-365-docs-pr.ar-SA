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
description: عندما لا تعود بحاجة إلى الاحتفاظ بمحتويات علبة بريد غير نشطة Microsoft 365، يمكنك حذف علبة البريد غير النشطة بشكل دائم.
ms.openlocfilehash: 640a118a2fc277b05edc181e19008836027dc468
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772369"
---
# <a name="delete-an-inactive-mailbox"></a>حذف علبة بريد غير نشطة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يتم استخدام علبة بريد غير نشطة للاحتفاظ بالبريد الإلكتروني لموظف سابق بعد مغادرة مؤسستك. عندما لا تعود بحاجة إلى الاحتفاظ بمحتويات علبة بريد غير نشطة، يمكنك حذف علبة البريد غير النشطة بشكل دائم عن طريق إزالة قائمة الاحتجاز. ومن المحتمل أيضا أن يتم وضع عدة قوائم احتجاز على علبة بريد غير نشطة. على سبيل المثال، قد يتم وضع علبة بريد غير نشطة في احتجاز التقاضي وعلى In-Place احتجاز واحد أو أكثر. بالإضافة إلى ذلك، قد يتم تطبيق استبقاء Microsoft 365 على علبة البريد غير النشطة. يجب إزالة كافة نهج الاحتجاز والاستبقاء من علبة بريد غير نشطة لحذفها. بعد إزالة نهج الاحتجاز والاستبقاء، يتم وضع علامة على علبة البريد غير النشطة للحذف ويتم حذفها نهائيا بعد معالجتها.
  
> [!IMPORTANT]
> مع استمرار الاستثمار بطرق مختلفة للحفاظ على محتوى علبة البريد، فإننا نعلن عن توقف In-Place عمليات الاحتجاز في مركز إدارة Exchange. وهذا يعني أنه يجب عليك استخدام نهج احتجاز التقاضي والاستبقاء لإنشاء علبة بريد غير نشطة. بدءا من 1 يوليو 2020، لن تتمكن من إنشاء In-Place جديد في Exchange Online. ولكن سيظل بإمكانك تغيير مدة احتجاز In-Place تم وضعه على علبة بريد غير نشطة. ومع ذلك، بدءا من 1 أكتوبر 2020، لن تتمكن من تغيير مدة الاحتجاز. ستتمكن فقط من حذف علبة بريد غير نشطة عن طريق إزالة In-Place Hold. ستظل علب البريد غير النشطة الموجودة على In-Place قائمة الاحتجاز محفوظة حتى تتم إزالة قائمة الاحتجاز. لمزيد من المعلومات حول توقف In-Place Holds، راجع [تقاعد أدوات eDiscovery القديمة](legacy-ediscovery-retirement.md).
  
راجع المقطع ["مزيد من المعلومات](#more-information) " للحصول على وصف لما يحدث بعد إزالة قوائم الاحتجاز من علبة بريد غير نشطة.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>قبل حذف علبة بريد غير نشطة

- يجب استخدام Exchange Online PowerShell لإزالة قوائم الاحتجاز من علبة بريد غير نشطة. لا يمكنك استخدام مركز إدارة Exchange (EAC) أو مدخل التوافق في Microsoft Purview لهذه الإجراءات. للحصول على إرشادات مفصلة خطوة بخطوة لاستخدام Exchange Online PowerShell، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يمكنك نسخ محتويات علبة بريد غير نشطة إلى علبة بريد أخرى قبل إزالة قائمة الاحتجاز وحذف علبة بريد غير نشطة. للحصول على التفاصيل، راجع [استعادة علبة بريد غير نشطة في Office 365](restore-an-inactive-mailbox.md).

- إذا قمت بإزالة نهج الاحتجاز أو الاستبقاء من علبة بريد غير نشطة وانتهت فترة الاحتفاظ بعلبة البريد المحذوفة مبدئيا لعل البريد، فسيتم حذف علبة البريد نهائيا بعد انتهاء فترة الاحتفاظ بعلب البريد المحذوفة مبدئيا لمدة 183 يوما. للحصول على مزيد من المعلومات حول فترة الاحتفاظ بعلب البريد المحذوفة مبدئيا، راجع القسم ["مزيد من المعلومات](#more-information) " في هذه المقالة. بعد حذف علبة البريد غير النشطة بشكل دائم، لا يمكن استردادها. قبل إزالة قائمة الاحتجاز، تأكد من أنك لم تعد بحاجة إلى المحتويات في علبة البريد. إذا كنت تريد إعادة تنشيط علبة بريد غير نشطة، يمكنك استردادها. للحصول على التفاصيل، راجع [استرداد علبة بريد غير نشطة في Office 365](recover-an-inactive-mailbox.md).

- لمزيد من المعلومات حول علب البريد غير النشطة، راجع ["تعرف على علب البريد غير النشطة](inactive-mailboxes-in-office-365.md)".

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>الخطوة 1: تحديد قوائم الاحتجاز على علبة بريد غير نشطة

كما ذكر سابقا، قد يتم وضع احتجاز التقاضي أو In-Place الاحتجاز أو نهج الاستبقاء على علبة بريد غير نشطة. الخطوة الأولى هي تحديد قوائم الاحتجاز على علبة بريد غير نشطة.
  
[الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)ثم قم بتشغيل الأمر التالي لعرض معلومات الاحتجاز لكافة علب البريد غير النشطة في مؤسستك.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

تشير قيمة **True** لخاصية **"التقاضي_ غير النشط** " إلى أن علبة البريد غير النشطة موجودة في "احتجاز التقاضي". إذا تم وضع تعليق In-Place على علبة بريد غير نشطة، يتم عرض GUID للاحتفاظ كقيمة **للخاصية InPlaceHolds** . على سبيل المثال، تظهر النتائج التالية لعلبة بريد غير نشطة أنه تم وضع احتجاز التقاضي على Ann Beebe وأنه يتم وضع نهج احتجاز واستبقاء In-Place على Pilar Pinilla.
  
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
> إذا تم وضع الكثير من In-Place نهج الاحتجاز أو الاستبقاء على علبة بريد غير نشطة، فلن يتم عرض كافة In-Place "معرفات المستخدم الرسومية للاحتفاظ". يمكنك تشغيل الأمر التالي لعرض كافة GUIDs في الخاصية InPlaceHolds:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
لمزيد من المعلومات حول تحديد قوائم الاحتجاز، راجع [كيفية تحديد نوع قائمة الاحتجاز الموضوعة على علبة البريد](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>الخطوة 2: إزالة قائمة احتجاز من علبة بريد غير نشطة

بعد تحديد نوع الاحتجاز الذي يتم وضعه على علبة البريد غير النشطة (وما إذا كان هناك عدة قوائم احتجاز)، فإن الخطوة التالية هي إزالة قوائم الاحتجاز على علبة البريد. كما ذكر سابقا، يجب إزالة كافة قوائم الاحتجاز لحذف علبة بريد غير نشطة بشكل دائم.
  
### <a name="remove-a-litigation-hold"></a>إزالة احتجاز التقاضي

قم بتشغيل أمر PowerShell التالي لإزالة احتجاز التقاضي.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> أفضل طريقة لتعريف علبة بريد غير نشطة هي باستخدام الاسم المميز أو قيمة GUID Exchange. يساعد استخدام إحدى هذه القيم على منع تحديد علبة البريد الخطأ عن طريق الخطأ. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>إزالة علبة بريد غير نشطة من نهج استبقاء

يعتمد إجراء إزالة علبة بريد غير نشطة من نهج استبقاء Microsoft 365 على ما إذا كان نهج الاستبقاء المعين إلى علبة البريد غير النشطة على مستوى المؤسسة أم صريحا:

- نهج الاستبقاء على مستوى المؤسسة المعينة لكافة علب البريد في المؤسسة. استخدم **get-OrganizationConfig** cmdlet في Exchange Online PowerShell للحصول على معلومات حول نهج الاستبقاء على مستوى المؤسسة.

- نهج معينة لاستبقاء الموقع معينة إلى علب بريد معينة. هذه هي النهج التي تم تعيينها إلى مواقع المحتوى الخاصة بمستخدمين معينين. استخدم **Get-Mailbox -IncludeInactiveMailbox** cmdlet في Exchange Online PowerShell للحصول على معلومات حول نهج الاستبقاء المعينة إلى علب بريد غير نشطة معينة.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>إزالة علبة بريد غير نشطة من نهج استبقاء على مستوى المؤسسة

قم بتشغيل أمر PowerShell التالي لاستبعاد علبة بريد غير نشطة من نهج استبقاء على مستوى المؤسسة.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

لمزيد من المعلومات حول تحديد نهج الاستبقاء على مستوى المؤسسة المطبقة على علبة بريد غير نشطة والحصول على GUID لنهج الاستبقاء، راجع القسم "Get-OrganizationConfig" في [كيفية تحديد نوع الاحتجاز الموضوع على علبة البريد](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig).

بدلا من ذلك، يمكنك تشغيل أمر PowerShell التالي لإزالة علبة البريد غير النشطة من كافة النهج على مستوى المؤسسة:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>إزالة علبة بريد غير نشطة من نهج استبقاء موقع معين

استخدم [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) لإزالة علبة بريد غير نشطة من نهج استبقاء صريح:

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -RemoveExchangeLocation <identity of inactive mailbox>
```

لمزيد من المعلومات حول تحديد نهج استبقاء موقع معينة يتم تطبيقها على علبة بريد غير نشطة، والحصول على المعرف الفريد العمومي (GUID) لنهج الاستبقاء، راجع القسم "الحصول على علبة البريد" في [كيفية تحديد نوع الاحتجاز الموضوع على علبة البريد](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox).

### <a name="remove-in-place-holds"></a>إزالة In-Place قوائم الاحتجاز

 هناك طريقتان لإزالة In-Place قائمة احتجاز من علبة بريد غير نشطة:
  
- **حذف كائن احتجاز In-Place**. إذا كانت علبة البريد غير النشطة التي تريد حذفها بشكل دائم هي علبة البريد المصدر الوحيدة ل "In-Place Hold"، فيمكنك حذف كائن "In-Place Hold". 

    > [!NOTE]
    > يجب تعطيل قائمة الاحتجاز قبل أن تتمكن من حذف كائن In-Place قائمة احتجاز. إذا حاولت حذف كائن In-Place قائمة احتجاز تم تمكين قائمة الاحتجاز فيه، فستتلقى رسالة خطأ. 
  
- **إزالة علبة البريد غير النشطة كعلبة بريد مصدر In-Place قائمة احتجاز**. إذا كنت تريد الاحتفاظ بعلب البريد المصدر الأخرى للاحتفاظ In-Place، يمكنك إزالة علبة البريد غير النشطة من قائمة علب البريد المصدر والاحتفاظ بكائن In-Place احتجاز.

#### <a name="delete-an-in-place-hold"></a>حذف قائمة احتجاز In-Place

1. أنشئ متغيرا يحتوي على خصائص In-Place قائمة الاحتجاز التي تريد حذفها. استخدم معرف GUID In-Place الذي حصلت عليه في [الخطوة 1: تحديد قوائم الاحتجاز على علبة بريد غير نشطة](#step-1-identify-the-holds-on-an-inactive-mailbox).

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. قم بتعطيل قائمة الاحتجاز على In-Place Hold.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. حذف قائمة احتجاز In-Place.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>إزالة علبة بريد غير نشطة من قائمة احتجاز In-Place

إذا احتوت In-Place قائمة الاحتجاز على عدد كبير من علب البريد المصدر، فمن المحتمل ألا تكون علبة البريد غير النشطة مدرجة في صفحة **"المصادر** " في EAC. يتم عرض ما يصل إلى 3000 علبة بريد على صفحة **"المصادر** " عند تحرير In-Place قائمة احتجاز. إذا لم تكن علبة بريد غير نشطة مدرجة في صفحة **"المصادر**"، فيمكنك استخدام Exchange Online PowerShell لإزالتها من قائمة الاحتجاز In-Place. 
  
1. إنشاء متغير يحتوي على خصائص In-Place تم وضع قائمة الاحتجاز على علبة البريد غير النشطة. استخدم معرف GUID In-Place الذي حصلت عليه في [الخطوة 1: تحديد قوائم الاحتجاز على علبة بريد غير نشطة](#step-1-identify-the-holds-on-an-inactive-mailbox).

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. تحقق من إدراج علبة البريد غير النشطة كعلبة بريد مصدر ل "In-Place Hold". 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > تحدد *الخاصية "مصادر* " ل "قائمة احتجاز In-Place" علب البريد المصدر حسب خصائص *LegacyExchangeDN* الخاصة بها. نظرا لأن هذه الخاصية تعرف علب البريد غير النشطة بشكل فريد، فإن استخدام *الخاصية "مصادر* " من In-Place"، يساعد على منع إزالة علبة البريد الخطأ. يساعد هذا أيضا على تجنب المشاكل إذا كانت علبة بريد لها نفس الاسم المستعار أو عنوان SMTP. 

3. إزالة علبة البريد غير النشطة من قائمة علب البريد المصدر في المتغير. تأكد من استخدام **LegacyExchangeDN** الخاص بعلبة البريد غير النشطة التي تم إرجاعها بواسطة الأمر في الخطوة السابقة. 

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

5. تعديل In-Place قائمة الاحتجاز مع القائمة المحدثة لعلب البريد المصدر، والتي لا تتضمن علبة البريد غير النشطة.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. تحقق من إزالة علبة البريد غير النشطة من قائمة علب البريد المصدر ل "In-Place Hold".

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>معلومات إضافية

- **علبة البريد غير النشطة هي نوع من علبة البريد المحذوفة مبدئيا.** في Exchange Online، علبة البريد المحذوفة مبدئيا هي علبة بريد تم حذفها ولكن يمكن استردادها خلال فترة استبقاء معينة. بالنسبة إلى علب البريد المحذوفة مبدئيا غير الموجودة قيد الاحتجاز، تكون علبة البريد قابلة للاسترداد في غضون 30 يوما. ستبقى علبة البريد غير النشطة (علبة بريد قيد الاحتجاز قبل حذفها) في حالة احتجاز مبدئية حتى تتم إزالة قائمة الاحتجاز. بعد إزالة قائمة الاحتجاز من علبة بريد غير نشطة، لن تكون علبة البريد في حالة غير نشطة. بدلا من ذلك، سيتم حذفه مبدئيا وسيظل في Exchange Online لمدة 183 يوما من اليوم الذي تمت فيه إزالة قائمة الاحتجاز وقابلة للاسترداد خلال ذلك الوقت. بعد 183 يوما، يتم وضع علامة على علبة بريد محذومة مبدئيا للحذف الدائم ولا يمكن استردادها.

- **ماذا يحدث بعد إزالة التعليق على علبة بريد غير نشطة؟** يتم التعامل مع علبة البريد مثل علب البريد الأخرى المحذوفة مبدئيا ويتم وضع علامة عليها للحذف الدائم بعد انتهاء فترة الاحتفاظ بعلب البريد المحذوفة مبدئيا لمدة 183 يوما. تبدأ فترة الاستبقاء هذه في تاريخ إزالة قائمة الاحتجاز من علبة البريد غير النشطة. يتم تعيين الخاصية *"غير نشطMailboxRetireTime* " عندما تنتقل علبة البريد من كونها غير نشطة (تم حذفها مبدئيا عند الاحتجاز) إلى عدم كونها غير نشطة (تم حذفها مبدئيا بدون قوائم احتجاز). عند هذه النقطة، يتم تعيين الخاصية *"غير نشطMailboxRetireTime"* إلى التاريخ الحالي عند حدوث الانتقال. هناك مساعد يتم تشغيله (يسمى *مساعد MailboxLifeCycle*) الذي يبحث عن علب البريد التي تم تعيين الخاصية *"غير نشطMailboxRetireTime".* إذا كان "غير نشطMailboxRetireTime + 183 days" أقل من التاريخ الحالي، فسيؤدي ذلك إلى إزالة علبة البريد.

- **هل يتم حذف علبة بريد غير نشطة بشكل دائم بعد إزالة قائمة الاحتجاز مباشرة؟** ستتوفر علبة بريد غير نشطة سابقا في الحالة المحذوفة مبدئيا لمدة 183 يوما. بعد 183 يوما، سيتم وضع علامة على علبة البريد للحذف الدائم.

- **كيف يمكنك عرض معلومات حول علبة بريد غير نشطة بعد إزالة قائمة الاحتجاز؟** بعد إزالة قائمة احتجاز وإعادة علبة البريد غير النشطة إلى علبة بريد تم حذفها مبدئيا، لن يتم إرجاعها باستخدام المعلمة  *ActiveMailboxOnly*  مع **الأمر Cmdlet "Get-Mailbox** ". ولكن يمكنك عرض معلومات حول علبة البريد باستخدام الأمر **Get-Mailbox -SoftDeletedMailbox** . على سبيل المثال:

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

  في المثال أعلاه، تحدد الخاصية *WhenSoftDeleted* التاريخ الذي تم حذفه مبدئيا، وهو في هذا المثال 16 يونيو 2020. تم سرد *الخاصية WasInactiveMailbox* لأنها `True` كانت في السابق علبة بريد غير نشطة. سيتم حذف علبة البريد نهائيا بعد 183 يوما من 30 سبتمبر 2020.
