---
title: تمكين علب بريد الأرشيف Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 268a109e-7843-405b-bb3d-b9393b2342ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
description: تعرف على كيفية تمكين علب بريد الأرشيف أو تعطيلها لدعم متطلبات الاحتفاظ بالرسائل وeDiscovery والاحتفاظ بالمؤسسة.
ms.openlocfilehash: f95da36b48389bba2bd640825071dbff5c6ddb3d
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772413"
---
# <a name="enable-archive-mailboxes-in-the-microsoft-purview-compliance-portal"></a>تمكين علب بريد الأرشيف في مدخل التوافق في Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

توفر الأرشفة في Microsoft 365 (تسمى أيضا *الأرشفة الموضعية*) للمستخدمين مساحة تخزين إضافية على علبة البريد. لمزيد من المعلومات، راجع ["التعرف على علب بريد الأرشيف](archive-mailboxes.md)".

استخدم المعلومات الواردة في هذه المقالة لتمكين علبة بريد أرشيف أو تعطيلها في مدخل التوافق في Microsoft Purview، أو باستخدام PowerShell. تعرف أيضا على كيفية تشغيل فحص تشخيصي تلقائي على علبة بريد الأرشيف الخاصة بالمستخدم لتحديد أي مشاكل وحلول مقترحة.

## <a name="get-the-necessary-permissions"></a>الحصول على الأذونات اللازمة

يجب تعيين دور مستلمي البريد في Exchange Online لتمكين علب بريد الأرشيف أو تعطيلها. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور إدارة المستلمين وإدارة المؤسسة في صفحة **الأذونات** في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. 

إذا لم تتمكن من رؤية صفحة **الأرشيف** في مدخل التوافق في Microsoft Purview، فاطلب من المسؤول تعيين الأذونات اللازمة لك.

## <a name="enable-an-archive-mailbox"></a>تمكين علبة بريد الأرشيف

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a> وسجل الدخول.

2. في الجزء الأيمن من مدخل التوافق، حدد **أرشيف** إدارة  > **دورة حياة البيانات**.

   في صفحة **الأرشيف** ، يحدد عمود  **علبة بريد الأرشيف** ما إذا كان قد تم تمكين علبة بريد الأرشيف أو تعطيلها لكل مستخدم.

   > [!NOTE]
   > تعرض صفحة **الأرشيف** 500 مستخدم كحد أقصى. استخدم مربع البحث إذا لم تتمكن من رؤية اسم المستخدم الذي تريده على الفور.

3. في قائمة علب البريد، حدد المستخدم لتمكين علبة البريد الخاصة به للأرشفة، ثم حدد خيار **تمكين الأرشيف** :
    
   ![تمكين خيار الأرشفة لمستخدم محدد.](../media/enable-archive-option.png)
    
   يتم عرض تحذير يفيد بأنه إذا قمت بتمكين علبة بريد الأرشيف، فسيتم نقل العناصر الموجودة في علبة بريد المستخدم الأقدم من نهج الأرشفة المعين لعلبة البريد إلى علبة بريد الأرشيف الجديدة. ينقل نهج الأرشيف الافتراضي الذي يعد جزءا من نهج الاستبقاء المعين إلى علب بريد Exchange Online العناصر إلى علبة بريد الأرشيف بعد عامين من تاريخ تسليم العنصر إلى علبة البريد أو إنشاؤه من قبل المستخدم. لمزيد من المعلومات، راجع ["التعرف على علب بريد الأرشيف](archive-mailboxes.md)".

5. حدد **"تمكين** " للتأكيد.

   قد يستغرق إنشاء علبة بريد الأرشيف بضع دقائق. عند إنشائه، يتم عرض **"ممكن"** في عمود **علبة بريد الأرشيف** للمستخدم المحدد، على الرغم من أنك قد تحتاج إلى تحديث الصفحة لرؤية تغيير الحالة.

## <a name="disable-an-archive-mailbox"></a>تعطيل علبة بريد الأرشيف

بطريقة مماثلة لكيفية تمكين علبة بريد الأرشيف، يمكنك استخدام صفحة **الأرشيف** في مدخل التوافق في Microsoft Purview لتعطيل علبة بريد الأرشيف الخاصة بالمستخدم. هذه المرة، حدد خيار **تعطيل الأرشيف** بعد تحديد المستخدم.

بعد تعطيل علبة بريد الأرشيف، يمكنك إعادة توصيلها بعلبة البريد الأساسية للمستخدم في غضون 30 يوما من تعطيلها. في هذه الحالة، تتم استعادة المحتويات الأصلية لعل بريد الأرشيف. بعد 30 يوما، يتم حذف محتويات علبة بريد الأرشيف الأصلية بشكل دائم ولا يمكن استردادها. لذلك إذا قمت بإعادة تمكين الأرشيف بعد أكثر من 30 يوما من تعطيله، يتم إنشاء علبة بريد أرشيف جديدة.

ينقل نهج الأرشيف الافتراضي المعين إلى علب بريد المستخدمين العناصر إلى علبة بريد الأرشيف بعد عامين من تاريخ تسليم العنصر. إذا قمت بتعطيل علبة بريد الأرشيف الخاصة بالمستخدم، فلن يتم اتخاذ أي إجراء على عناصر علبة البريد وستبقى في علبة البريد الأساسية للمستخدم.

## <a name="use-exchange-online-powershell-to-enable-or-disable-archive-mailboxes"></a>استخدام Exchange Online PowerShell لتمكين علب بريد الأرشيف أو تعطيلها

يمكنك أيضا استخدام Exchange Online PowerShell لتمكين علب بريد الأرشيف. السبب الأساسي لاستخدام PowerShell هو أنه يمكنك تمكين علبة بريد الأرشيف بسرعة لجميع المستخدمين في مؤسستك.

الخطوة الأولى هي الاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

بعد الاتصال Exchange Online، يمكنك تشغيل الأوامر في المقاطع التالية لتمكين علب بريد الأرشيف أو تعطيلها.

### <a name="enable-archive-mailboxes"></a>تمكين علب بريد الأرشيف

قم بتشغيل الأمر التالي لتمكين علبة بريد الأرشيف لمستخدم واحد.

```powershell
Enable-Mailbox -Identity <username> -Archive
```

قم بتشغيل الأمر التالي لتمكين علبة بريد الأرشيف لكافة المستخدمين في مؤسستك (علبة بريد الأرشيف الخاصة بهم غير ممكنة حاليا).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Eq "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Enable-Mailbox -Archive
```

### <a name="disable-archive-mailboxes"></a>تعطيل علب بريد الأرشيف

قم بتشغيل الأمر التالي لتعطيل علبة بريد الأرشيف لمستخدم واحد.

```powershell
Disable-Mailbox -Identity <username> -Archive
```

قم بتشغيل الأمر التالي لتعطيل علبة بريد الأرشيف لكافة المستخدمين في مؤسستك (علبة بريد الأرشيف الخاصة بهم ممكنة حاليا).

```powershell
Get-Mailbox -Filter {ArchiveGuid -Ne "00000000-0000-0000-0000-000000000000" -AND RecipientTypeDetails -Eq "UserMailbox"} | Disable-Mailbox -Archive
```

## <a name="run-diagnostics-on-archive-mailboxes"></a>تشغيل التشخيصات على علب بريد الأرشيف

يمكنك تشغيل فحص تشخيصي تلقائي على علبة بريد الأرشيف الخاصة بالمستخدم لتحديد أي مشاكل وحلول مقترحة.

لتشغيل الفحص التشخيصي، انقر فوق الزر أدناه. 

> [!div class="nextstepaction"]
> [تشغيل الاختبارات: علبة بريد الأرشيف](https://aka.ms/PillarArchiveMailbox)

![تشغيل التشخيصات على علبة بريد الأرشيف.](../media/ArchiveMailboxDiagnostics.png)

يتم فتح صفحة منبثقة في مركز مسؤولي Microsoft 365. أدخل عنوان البريد الإلكتروني لعل البريد الذي تريد التحقق منه وانقر فوق **"تشغيل الاختبارات**".

> [!NOTE]
> يجب أن تكون مسؤولا عموميا Microsoft 365 لاستخدام التحقق التشخيصي لعلبة بريد الأرشيف. كما أن هذه الميزة غير متوفرة في Microsoft 365 السحب الحكومية، Microsoft 365 تشغلها 21Vianet أو Microsoft 365 ألمانيا.

## <a name="instructions-for-end-users"></a>إرشادات للمستخدمين النهائيين

شرح كيفية عمل علبة بريد الأرشيف للمستخدمين، وكيفية تفاعلهم معها في Outlook على Windows macOS والويب. سيتم تخصيص الوثائق الأكثر فعالية لمؤسستك. ولكن للحصول على الإرشادات الأساسية، راجع [إدارة تخزين البريد الإلكتروني باستخدام علب بريد الأرشيف عبر الإنترنت](https://prod.support.services.microsoft.com/en-us/office/manage-email-storage-with-online-archive-mailboxes-1cae7d17-7813-4fe8-8ca2-9a5494e9a721).

## <a name="next-steps"></a>الخطوات التالية

ضع في اعتبارك تمكين [الأرشفة ذات التوسع التلقائي](autoexpanding-archiving.md) لمساحة تخزين إضافية. للحصول على الإرشادات، راجع [تمكين الأرشفة ذات التوسيع التلقائي](enable-autoexpanding-archiving.md).
