---
title: إدارة الوصول المستند إلى الوردية للعاملين في الخطوط الأمامية في Teams
author: LanaChin
ms.author: v-lanachin
ms.reviewer: aaku
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: تعرف على كيفية إدارة الوصول المستند إلى الوردية في Teams للعاملين في الخطوط الأمامية في مؤسستك.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 0e8ed4d923375d8d839533b6c69a114c4c53aa28
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66858069"
---
# <a name="manage-shift-based-access-for-frontline-workers-in-teams"></a>إدارة الوصول المستند إلى الوردية للعاملين في الخطوط الأمامية في Teams

## <a name="overview"></a>نظرة عامة

[!INCLUDE [preview-feature](includes/preview-feature.md)]

يشير التواجد في Microsoft Teams إلى توفر المستخدم وحالته الحاليين للمستخدمين الآخرين. غالبا ما يكون وجود العاملين في الخطوط الأمامية أقل قابلية للتنبؤ من الموظفين الآخرين لأن ساعات عملهم عادة لا تكون هي نفسها كل يوم. بصفتك مسؤولا، يمكنك تكوين Teams لإظهار مجموعة من حالات التواجد المستندة إلى الوردية للعاملين في الخطوط الأمامية في مؤسستك للإشارة إلى وقت تشغيلهم وإطفاء الوردية.

تشير حالة&mdash;![الحضور المستندة إلى الوردية هذه إلى علامة اختيار خضراء خالصة، إلى "عند الوردية".](media/flw-presence-on-shift.png) **في الوردية**، ![تشير الدائرة الرمادية مع x إلى إيقاف الوردية.](media/flw-presence-off-shift.png) **خارج الوردية**، ![الدائرة الحمراء الصلبة، تشير **إلى أن مشغول**&mdash;](media/flw-presence-busy.png) منفصل عن [المجموعة الافتراضية لحالات الحضور](/microsoftteams/presence-admins) في Teams. باستخدام هاتين المجموعتين من حالات الحضور، يمكنك تكوين تجارب مختلفة للأشخاص في مؤسستك استنادا إلى دورهم.

باستخدام الوصول المستند إلى الوردية، يمكنك إدارة الوصول إلى Teams عندما يكون عمال الخطوط الأمامية خارج الوردية. على سبيل المثال، يمكنك تعيين Teams لعرض رسالة يجب أن يقر بها عمال الخطوط الأمامية قبل أن يتمكنوا من استخدام Teams عندما لا يكونون في وردية مجدولة.  

## <a name="scenario"></a>السيناريو

فيما يلي مثال على كيفية إدارة مؤسستك للوصول المستند إلى الوردية.

لديك عمال الخطوط الأمامية في مؤسستك الذين يجب أن تدفع لهم فقط مقابل ساعات العمل على وردية قام مديرهم بجدولتها والموافقة عليها. يجب ألا تدفع مقابل الوقت المستغرق في العمل خارج وردية مجدولة، والتي تتضمن استخدام تطبيق Teams. يمكنك إعداد رسالة مخصصة تقول "لن يتم حساب وقتك في Teams عند إيقاف الوردية في الساعات المستحقة الدفع"، والتي يتم عرضها عندما يحاول عمال الخطوط الأمامية الوصول إلى Teams عند إيقاف الوردية. إذا اختاروا استخدام Teams، فانقر فوق **"أوافق** " مع فهم أنهم لن يدفعوا مقابل هذا الوقت.

لديك أيضا عاملون في مجال المعلومات في مؤسستك رواتب ولا يعملون على الورديات. يمكنك تكوين العاملين في مجال المعلومات لاستخدام حالات الحضور الافتراضية في Teams مع منح العاملين في الخطوط الأمامية حالة حضور مستندة إلى الوردية.

## <a name="shift-based-presence-states"></a>حالات الحضور المستندة إلى Shift

فيما يلي حالات الحضور المستندة إلى الوردية.

|تم تكوين التطبيق |تم تكوين المستخدم  |معلومات إضافية  |
|---------|---------|---------|
|![علامة اختيار خضراء خالصة، تشير إلى "عند الوردية".](media/flw-presence-on-shift.png) عند الوردية     |         |تعيين تلقائي في بداية الوردية         |
|![دائرة رمادية مع x، تشير إلى إيقاف الوردية](media/flw-presence-off-shift.png) إيقاف الوردية     |         |تعيين تلقائي في نهاية الوردية         |
|![دائرة حمراء متصلة، تشير إلى مشغول.](media/flw-presence-busy.png) مشغول      | ![دائرة حمراء متصلة، تشير إلى مشغول](media/flw-presence-busy.png) مشغول         |تعيين تلقائي. يمكن أيضا تعيينه يدويا عندما يكون عامل الخط الأمامي في وردية.|

## <a name="off-shift-access-to-teams"></a>إيقاف تشغيل الوصول إلى Shift إلى Teams

تتيح لك هذه الميزة إدارة الوصول إلى Teams عند إيقاف تشغيل عمال الخطوط الأمامية. يمكنك تعيين Teams لعرض رسالة للعاملين في الخطوط الأمامية إذا كانوا يصلون إلى Teams عند إيقاف الوردية. يجب على عمال الخطوط الأمامية النقر فوق **"أوافق** " للإقرار بالرسالة قبل أن يتمكنوا من استخدام Teams.

يمكنك استخدام الرسالة الافتراضية، أو الاختيار من بين مجموعة من الرسائل المعرفة مسبقا، أو تخصيص الرسالة لعرض أي نص تريده. إليك الرسالة الافتراضية:

![لقطة شاشة للرسالة الافتراضية.](media/shifts-presence-message.png)

يمكنك أيضا تعيين التكرار عند عرض الرسالة وتعيين فترة سماح بين وقت بدء الوردية الأولى أو انتهاء الوردية الأخيرة ووقت تقييد الوصول إلى Teams.

## <a name="manage-shift-based-access"></a>إدارة الوصول المستند إلى الوردية

بصفتك مسؤولا، يمكنك استخدام النهج للتحكم في حالة الحضور المستندة إلى الوردية للعاملين في الخطوط الأمامية في مؤسستك. يمكنك إدارة هذه النهج باستخدام أوامر PowerShell cmdlets التالية:

- [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy)
- [Get-CsTeamsShiftsPolicy](/powershell/module/teams/get-csteamsshiftspolicy)
- [Set-CsTeamsShiftsPolicy](/powershell/module/teams/set-csteamsshiftspolicy)
- [Grant-CsTeamsShiftsPolicy](/powershell/module/teams/grant-csteamsshiftspolicy)
- [Remove-CsTeamsShiftsPolicy](/powershell/module/teams/remove-csteamsshiftspolicy)

استخدم New-CsTeamsShiftsPolicy cmdlet لإنشاء نهج جديد، وتعيين إعدادات النهج التي تريدها، ثم استخدم Grant-CsTeamsShiftsPolicy cmdlet لتعيين النهج للمستخدمين.

إليك بعض الأمثلة. للحصول على معلومات مفصلة حول كل إعداد نهج ومعلمة، بما في ذلك قائمة رسائل الوردية المعرفة مسبقا التي يمكنك الاختيار من بينها، راجع [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-1"></a>مثال 1

في هذا المثال، نقوم بإنشاء نهج جديد يسمى Off Shift Teams Access Default Message. في هذا النهج، يتم تشغيل حالة الحضور المستندة إلى الوردية ويتم عرض الرسالة الافتراضية في كل مرة يصل فيها مستخدم معين لهذا النهج إلى Teams عند إيقاف الوردية. يمكن للمستخدم استخدام Teams عند إيقاف الوردية إذا قبل الرسالة، وفترة السماح بين تاريخ بدء الوردية الأولى أو انتهاء الوردية الأخيرة ووقت تقييد الوصول هي 10 دقائق.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Default Message" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType DefaultMessage -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 10
```

> [!NOTE]
> استخدم المعلمة **ShiftNoticeMessageType** لتعيين الرسالة التي تريد عرضها. للاطلاع على قائمة بالرسائل المعرفة مسبقا التي يمكنك الاختيار من بينها لهذه المعلمة، راجع [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-2"></a>مثال 2 

في هذا المثال، نقوم بإنشاء نهج جديد يسمى Off Shift Teams Access Custom Message. في هذا النهج، يتم تشغيل حالة الحضور المستندة إلى الوردية ويتم عرض رسالة مخصصة في كل مرة يصل فيها مستخدم معين لهذا النهج إلى Teams عند إيقاف الوردية. يمكن للمستخدم استخدام Teams عند إيقاف الوردية إذا قبل الرسالة، وفترة السماح بين تاريخ بدء الوردية الأولى أو انتهاء الوردية الأخيرة ووقت تقييد الوصول هي 15 دقيقة.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Custom Message" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType CustomMessage -ShiftNoticeMessageCustom "Your time on Teams when on off shift won't count toward payable hours" -AccessType UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 15
```

> [!NOTE]
> استخدم المعلمة **ShiftNoticeMessageType** لتعيين الرسالة التي تريد عرضها. لمعرفة المزيد، راجع [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-3"></a>مثال 3

في هذا المثال، نقوم بإنشاء نهج جديد يسمى Off Shift Teams Access Message1. في هذا النهج، يتم تشغيل حالة الحضور المستندة إلى الوردية ويتم عرض الرسالة التالية المعرفة مسبقا في كل مرة يصل فيها مستخدم معين لهذا النهج إلى Teams عند إيقاف الوردية.

  "لا يصرح صاحب العمل أو يوافق على استخدام شبكته أو تطبيقاته أو أنظمته أو أدواته من قبل الموظفين غير المعفيين أو كل ساعة خلال ساعات العمل الخاصة بهم. من خلال القبول، فإنك تقر بأن استخدامك ل Teams أثناء إيقاف الوردية غير مخول ولن يتم تعويضك." 

يمكن للمستخدم استخدام Teams عند إيقاف الوردية إذا قبل الرسالة، وفترة السماح بين تاريخ بدء الوردية الأولى أو انتهاء الوردية الأخيرة ووقت تقييد الوصول هي ثلاث دقائق.  

```powershell
New-CsTeamsShiftsPolicy -Identity "Off Shift Teams Access Message1" -EnableShiftPresence $true -ShiftNoticeFrequency always -ShiftNoticeMessageType Message1 -AccessType  UnrestrictedAccess_TeamsApp -AccessGracePeriodMinutes 3
```

> [!NOTE]
> استخدم المعلمة **ShiftNoticeMessageType** لتعيين الرسالة التي تريد عرضها. للاطلاع على قائمة بالرسائل المعرفة مسبقا التي يمكنك الاختيار من بينها لهذه المعلمة، راجع [New-CsTeamsShiftsPolicy](/powershell/module/teams/new-csteamsshiftspolicy).

### <a name="example-4"></a>مثال 4

في هذا المثال، نقوم بتعيين نهج يسمى Off Shift Teams Access Custom Message إلى مستخدم يسمى remy@contoso.com.

```powershell
Grant-CsTeamsShiftsPolicy -Identity remy@contoso.com -PolicyName "Off Shift Teams Access Custom Message"
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة تطبيق الورديات لمؤسستك في Teams](/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)
- [نظرة عامة على Teams PowerShell](/microsoftteams/teams-powershell-overview)