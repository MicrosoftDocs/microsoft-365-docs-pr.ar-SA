---
title: إعداد Scheduler Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: إعداد Scheduler Microsoft 365.
ms.openlocfilehash: 3315c362a6e6ae1eb4fa9bf54d388a89dd667136
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63583265"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>إعداد Scheduler Microsoft 365

يجب على المسؤولين المستأجرين إعداد علبة بريد مساعد الجدول والحصول على تراخيص Scheduler لمنظمي الاجتماع لتمكين "المجدول" Microsoft 365 الخدمة. 

## <a name="licensing"></a>الترخيص

تعرف على المزيد: [مجدول Microsoft 365 الترخيص](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!Note]
> لا يحتاج حاضرو الاجتماع إلى ترخيص مجدول أو Microsoft 365 جديد. <br>لا تتطلب علبة بريد مساعد الجدولة Microsoft 365 أو ترخيص Scheduler.

## <a name="prerequisites"></a>المتطلبات الأساسية

| المتطلبات الأساسية | الوصف |
|-------------------|-------------|
|علبة بريد مساعد "المجدول" للمستأجر |علبة Exchange موارد نوع المعدات التي تعمل كعميل بريد "المجدول" للمستأجر لإرسال رسائل البريد الإلكتروني وتلقيها من ونهاية Cortana. يتم الاحتفاظ بكل رسائل البريد الإلكتروني Cortana في علبة بريد المستأجر Cortana استنادا إلى نهج الاستبقاء. تسمى علبة بريد مساعد الجدولة عادة "Cortana" أو "Cortana Scheduler" نظرا لأنه سيتم توقيع كل رسائل البريد الإلكتروني من المساعد Cortana.<ul><li>إنشاء نوع المعدات Exchange بريد المورد</li><li>تسمية اسم عرض علبة البريد وعنوان SMTP الأساسي `Cortana <cortana@yourdomain.com>` أو `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul>**ملاحظة:** لا تتطلب علبة بريد مساعد الجدولة Microsoft 365 أو ترخيص Scheduler.|
|Exchange Online بريدك |يجب أن يكون لدى منظمي Exchange Online البريد والتقويم عادة كجزء من Microsoft 365 الخاص بهم. بالإضافة إلى ذلك، يجب أن يكون لدى منظمي الاجتماع ترخيص Scheduler. يمكن ترخيص "المجدول" مساعد "الجدول" من استخدام علبة بريد منظم الاجتماع وتقويمه لجدولة الاجتماعات لهم.<br/><br/> راجع جدولة Microsoft 365 للحصول على معلومات حول الترخيص والأسعار.  <br/><br/>**ملاحظة:** لا يحتاج حاضرو الاجتماع إلى ترخيص مجدول أو Microsoft 365 جديد. يمكن أن يكون حضور الاجتماع داخليا أو خارجيا للمستأجر. يحتاج حاضرو الاجتماع إلى الوصول إلى عنوان بريد إلكتروني فقط.|


## <a name="setting-up-the-scheduler-assistant-mailbox"></a>إعداد علبة بريد مساعد الجدول

إن علبة بريد مساعد الجدولة Exchange علبة بريد نوع المعدات التي لا تتطلب ترخيصا إضافيا Microsoft 365 Scheduler. يجب أن يحتوي اسم العرض وعنوان SMTP الأساسي لعلبة البريد على Cortana حيث سيتم توقيع كل رسائل البريد الإلكتروني من مساعد Scheduler Cortana ( `Cortana <cortana@yourdomain.com>` أي، أو `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). بعد إنشاء علبة بريد مساعد الجدول، يجب تعيين علبة البريد ك علبة بريد مساعد Scheduler. بعد تعيين علبة بريد مساعد الجدول، Cortana تكون متوفرة لجدولة الاجتماعات نيابة عن المستخدمين.

- استخدم مركز مسؤولي Microsoft 365 لإنشاء علبة بريد مستخدم. يوصى باستخدام نهج استبقاء لمدة 30 يوما. 
- استخدم الاسم Cortana عنوان SMTP الأساسي لعلبة البريد. أسماء مثل `Cortana@yourdomain.com`أو `CortanaScheduler@contoso.com`أو `Cortana.Scheduler@yourdomain.com` مستحسنة.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>تعيين علبة البريد كمساعد "المجدول"

بعد إنشاء علبة بريد فريدة Cortana Scheduler، يجب تعيين علبة البريد Microsoft 365 بشكل رسمي. بعد تعيين علبة البريد Cortana Scheduler، ستكون متوفرة لجدولة الاجتماعات نيابة عن المستخدمين.

#### <a name="connect-to-powershell"></a>الاتصال إلى PowerShell

استخدم مركز مسؤولي Microsoft 365 لإنشاء علبة بريد مستخدم. يوصى باستخدام نهج استبقاء لمدة 30 يوما.
استخدم الاسم Cortana عنوان SMTP الأساسي لعلبة البريد. أسماء مثل `Cortana@yourdomain.com`أو `CortanaScheduler@contoso.com`أو `Cortana.Scheduler@yourdomain.com` مستحسنة.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

#### <a name="create-the-scheduler-assistant-mailbox"></a>إنشاء علبة بريد مساعد الجدولة

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```
    
#### <a name="designate-the-scheduler-assistant-mailbox"></a>تعيين علبة بريد مساعد الجدولة

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

بعد تشغيل الأمر "set" هذا على علبة بريد مساعد Cortana Scheduler، يتم تعيين "PersistedCapability" جديد على علبة البريد لتلاحظ أن علبة البريد هذه هي "SchedulerAssistant".

> [!Note]
> للتعرف على كيفية توصيل مؤسستك ب PowerShell، راجع: الاتصال [Microsoft 365 PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>التحقق من علبة بريد مساعد المجدول

للتحقق من إنشاء علبة بريد مساعد الجدول

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

يجب أن تكون النتيجة "false".

<br>

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

يجب أن تكون النتيجة
- ResourceType: المعدات
- RecipientType البعيد: بلا
- RecipientType: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

<br/>

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>لاكتشاف علبة البريد التي هي علبة بريد مساعد الجدول

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!Important]
> قد يستغرق الأمر عدة ساعات حتى تكتمل علبة بريد مساعد Scheduler عملية توفير كاملة لتعيين الإمكانية SchedulerAssistant.


## <a name="exchange-online-mailbox"></a>Exchange Online بريدك

ترخيص Scheduler هو أحد الوظائف الإضافية Microsoft 365، مما يمكن منظم الاجتماع من تفويض مهام جدولة الاجتماع إلى مساعد "الجدول". بالإضافة إلى تعيين علبة بريد كع البريد مساعد الجدول، سيحتاج منظمو الاجتماع أيضا إلى ترخيص Scheduler Exchange Online علبة بريد وتقويم، عادة من خلال Microsoft 365 ل Scheduler للعمل. لا يحتاج حاضرو الاجتماع إلى ترخيص Scheduler أو Microsoft 365 جديد.

لشراء الوظائف الإضافية Scheduler، تحتاج إلى أحد التراخيص التالية:

- Microsoft 365 E3، A3، E5، A5
- Business Basic, Business, Business Standard, Business Premium
- Office 365 E1، A1، E3، A3، E5، A5
- Business Essentials, Business Premium
- Exchange Online الخطة 1 أو الخطة 2. 

> [!Note]
> يتوفر المجدول Microsoft 365 في بيئات متعددة المستأجرين حول العالم باللغة الإنجليزية فقط. **لا يتوفر Microsoft 365** الجدولة لمستخدمي:
> 
> - Microsoft 365 التي يتم تشغيلها بواسطة 21Vianet في الصين
> - Microsoft 365 مع السحابة الألمانية التي تستخدم البيانات الموثوق بها German Telekom
> - سحابة الحكومة بما في ذلك سحابة القطاع الحكومي أو المستهلك أو سحابة القطاع الحكومي High أو DoD
> 
> يدعم Scheduler المستخدمين في ألمانيا الذين لا يكون موقع بياناتهم مركز البيانات الألماني.
