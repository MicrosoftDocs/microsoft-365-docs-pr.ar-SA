---
title: إعداد Scheduler ل Microsoft 365.
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
ms.localizationpriority: medium
description: إعداد Scheduler ل Microsoft 365.
ms.openlocfilehash: ef377393134e4d8028ab0e6e40ddcc3647f60695
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953837"
---
# <a name="setting-up-scheduler-for-microsoft-365"></a>إعداد مجدول Microsoft 365

يحتاج مسؤولو المستأجرين إلى إعداد علبة بريد مساعد Scheduler والحصول على تراخيص Scheduler لمنظمي الاجتماع لتمكين Scheduler لخدمة Microsoft 365. 

## <a name="licensing"></a>الترخيص

تعرف على المزيد: [مجدول لترخيص Microsoft 365](https://www.microsoft.com/microsoft-365/meeting-scheduler-pricing)

> [!NOTE]
> لا يحتاج حاضرو الاجتماع إلى ترخيص مجدول أو Microsoft 365.
>
> لا تتطلب علبة بريد مساعد Scheduler ترخيص Microsoft 365 أو Scheduler.

## <a name="prerequisites"></a>المتطلبات الأساسية

|شرط|الوصف|
|---|---|
|علبة بريد مساعد Scheduler للمستأجر |علبة بريد مورد نوع المعدات Exchange تعمل كعلبة بريد مساعد Scheduler للمستأجر لإرسال رسائل البريد الإلكتروني وتلقيها من Cortana وإليكها. يتم الاحتفاظ بكافة رسائل البريد الإلكتروني المرسلة إلى Cortana في علبة بريد المستأجر Cortana استنادا إلى نهج الاستبقاء. عادة ما تسمى علبة بريد مساعد Scheduler "Cortana" أو "Cortana Scheduler" حيث سيتم توقيع كل رسائل البريد الإلكتروني من المساعد Cortana. <ul><li>إنشاء نوع جهاز Exchange علبة بريد المورد</li><li>قم بتسمية اسم عرض علبة البريد وعنوان `Cortana <cortana@yourdomain.com>` SMTP الأساسي أو `Cortana Scheduler <cortana.scheduler@yourdomain.com>`.</li></ul> <br/> **ملاحظه:** لا تتطلب علبة بريد مساعد Scheduler ترخيص Microsoft 365 أو Scheduler.|
|علبة بريد Exchange Online |يجب أن يكون لدى منظمي الاجتماع علبة بريد وتقويم Exchange Online كجزء من ترخيص Microsoft 365 الخاص بهم. بالإضافة إلى ذلك، يجب أن يكون لدى منظمي الاجتماع ترخيص Scheduler. يمكن ترخيص Scheduler مساعد Scheduler من استخدام علبة بريد منظم الاجتماع وتقويمه لجدولة الاجتماعات له. <br/><br/> راجع Scheduler للحصول على Microsoft 365 للحصول على معلومات الترخيص والتسعير. <br/><br/> **ملاحظه:** لا يحتاج حاضرو الاجتماع إلى ترخيص مجدول أو Microsoft 365. يمكن أن يكون حضور الاجتماع داخليا أو خارجيا للمستأجر. يحتاج حاضرو الاجتماع فقط إلى الوصول إلى عنوان بريد إلكتروني.|

## <a name="setting-up-the-scheduler-assistant-mailbox"></a>إعداد علبة بريد مساعد Scheduler

علبة بريد مساعد المجدول هي علبة بريد نوع معدات Exchange لا تتطلب ترخيصا إضافيا Microsoft 365 أو Scheduler. يجب أن يحتوي اسم العرض وعنوان SMTP الأساسي لعل البريد على Cortana حيث سيتم توقيع جميع رسائل البريد الإلكتروني من مساعد Scheduler Cortana (أي، `Cortana <cortana@yourdomain.com>` أو `Cortana Scheduler <cortana.scheduler@yourdomain.com>`). بعد إنشاء علبة بريد مساعد Scheduler، يجب تعيين علبة البريد كعلبة بريد مساعد Scheduler. بعد تعيين علبة بريد مساعد Scheduler، سيكون Cortana متوفرا لجدولة الاجتماعات نيابة عن المستخدمين.

- استخدم مركز مسؤولي Microsoft 365 لإنشاء علبة بريد مستخدم. يوصى بنهج استبقاء لمدة 30 يوما. 
- استخدم الاسم Cortana في عنوان SMTP الأساسي لعل بريدك. أسماء مثل `Cortana@yourdomain.com`، `CortanaScheduler@contoso.com`أو ، أو `Cortana.Scheduler@yourdomain.com` مستحسنة.

## <a name="designate-the-mailbox-as-the-scheduler-assistant"></a>تعيين علبة البريد كمساعد المجدول

بعد إنشاء علبة بريد فريدة Cortana Scheduler، يجب تعيين علبة البريد Microsoft 365 رسميا. بعد تعيين علبة بريد Cortana Scheduler، ستتوفر لجدولة الاجتماعات نيابة عن المستخدمين.

### <a name="connect-to-powershell"></a>الاتصال إلى PowerShell

استخدم مركز مسؤولي Microsoft 365 لإنشاء علبة بريد مستخدم. يوصى بنهج استبقاء لمدة 30 يوما.
استخدم الاسم Cortana في عنوان SMTP الأساسي لعل بريدك. أسماء مثل `Cortana@yourdomain.com`، `CortanaScheduler@contoso.com`أو ، أو `Cortana.Scheduler@yourdomain.com` مستحسنة.

```PowerShell
$domain="yourdomain.com"
$tenantAdmin="<tenantadmin>@$domain"
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $tenantAdmin
```

### <a name="create-the-scheduler-assistant-mailbox"></a>إنشاء علبة بريد مساعد المجدول

```PowerShell
New-Mailbox -Name Cortana -Organization $domain -DisplayName "Cortana Scheduler" -Equipment 
Set-CalendarProcessing Cortana@$domain -DeleteNonCalendarItems $false 
```

### <a name="designate-the-scheduler-assistant-mailbox"></a>تعيين علبة بريد مساعد المجدول

```PowerShell
Set-mailbox cortana@$domain -SchedulerAssistant:$true
```

بعد تشغيل الأمر "set" هذا على علبة بريد مساعد "scheduler" Cortana، يتم تعيين "PersistedCapability" جديد على علبة البريد لتلاحظ أن علبة البريد هذه هي "SchedulerAssistant".

> [!NOTE]
> لمعرفة كيفية توصيل مؤسستك ب PowerShell، راجع: [الاتصال Microsoft 365 باستخدام PowerShell](/microsoft-365/enterprise/connect-to-microsoft-365-powershell)

### <a name="verifying-the-scheduler-assistant-mailbox"></a>التحقق من علبة بريد مساعد Scheduler

للتحقق من إنشاء علبة بريد مساعد Scheduler

```PowerShell
Get-CalendarProcessing cortana@$domain | fl DeleteNonCalendarItems
```

يجب أن تكون النتيجة "خطأ".

```PowerShell
Get-Mailbox -Identity cortana@$domain | fl *type*
```

يجب أن تكون النتيجة

- ResourceType: المعدات
- Remote RecipientType: None
- RecipientType: UserMailbox
- RecipientTypeDetails: EquipmentMailbox

### <a name="to-discover-which-mailbox-is-the-scheduler-assistant-mailbox"></a>لاكتشاف علبة البريد التي هي علبة بريد مساعد Scheduler

```PowerShell
Get-Mailbox -ResultSize Unlimited | where {$_.PersistedCapabilities -Match "SchedulerAssistant"}
```

> [!IMPORTANT]
> قد تستغرق علبة بريد مساعد Scheduler عدة ساعات لإكمال التوفير الكامل لتعيين إمكانية SchedulerAssistant.

## <a name="exchange-online-mailbox"></a>علبة بريد Exchange Online

ترخيص Scheduler هو وظيفة إضافية Microsoft 365، والتي تمكن منظم الاجتماع من تفويض مهام جدولة الاجتماعات إلى مساعد Scheduler الخاص به. بالإضافة إلى تعيين علبة بريد كعلبة بريد مساعد Scheduler، سيحتاج منظمو الاجتماع أيضا إلى ترخيص Scheduler وعلبة بريد Exchange Online والتقويم، عادة من خلال ترخيص Microsoft 365 لكي يعمل Scheduler. لا يحتاج حاضرو الاجتماع إلى ترخيص Scheduler أو ترخيص Microsoft 365.

لشراء الوظيفة الإضافية Scheduler، تحتاج إلى أحد التراخيص التالية:

- Microsoft 365 E3، A3، E5، A5
- Business Basic و Business و Business Standard و Business Premium
- Office 365 E1، A1، E3، A3، E5، A5
- Business Essentials, Business Premium
- Exchange Online ترخيص الخطة 1 أو الخطة 2.

> [!NOTE]
> يتوفر مجدول Microsoft 365 في بيئات متعددة المستأجرين في جميع أنحاء العالم باللغة الإنجليزية فقط. **مجدول Microsoft 365** غير متوفر لمستخدمي:
>
> - Microsoft 365 المشغلة بواسطة 21Vianet في الصين
> - Microsoft 365 مع السحابة الألمانية التي تستخدم وصي البيانات German Telekom
> - سحابة حكومية بما في ذلك سحابة القطاع الحكومي أو المستهلك أو سحابة القطاع الحكومي High أو DoD
>
> يدعم Scheduler المستخدمين في ألمانيا الذين لا يكون موقع بياناتهم هو مركز البيانات الألماني.
