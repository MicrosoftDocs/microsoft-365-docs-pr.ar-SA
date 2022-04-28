---
title: إدارة نهج Skype for Business Online باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'ملخص: استخدم PowerShell لإدارة خصائص حساب المستخدم Skype for Business Online باستخدام النهج.'
ms.openlocfilehash: 71ced77947efda0f587fe7a20af85a73dea73f6c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094339"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>إدارة نهج Skype for Business Online باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

لإدارة العديد من خصائص حساب المستخدم ل Skype for Business Online، يجب تحديدها كخصائص للنهج باستخدام PowerShell Microsoft 365.
  
## <a name="before-you-begin"></a>قبل البدء

استخدم هذه الإرشادات لإعداد تشغيل الأوامر (تخطي الخطوات التي أكملتها بالفعل):

  > [!Note]
  > Skype for Business Online Connector هو حاليا جزء من أحدث وحدة Teams PowerShell. إذا كنت تستخدم أحدث إصدار عام Teams PowerShell، فلن تحتاج إلى تثبيت Skype for Business Online Connector.

1. تثبيت [الوحدة النمطية Teams PowerShell](/microsoftteams/teams-powershell-install).
    
2. افتح موجه أوامر Windows PowerShell وقم بتشغيل الأوامر التالية: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   عند مطالبتك، أدخل اسم حساب مسؤول Skype for Business عبر الإنترنت وكلمة المرور.
    
## <a name="manage-user-account-policies"></a>إدارة نهج حساب المستخدم

يتم تكوين العديد من خصائص حساب المستخدم عبر الإنترنت Skype for Business باستخدام النهج. النهج هي ببساطة مجموعات من الإعدادات التي يمكن تطبيقها على مستخدم واحد أو أكثر. لإلقاء نظرة على كيفية تكوين النهج، يمكنك تشغيل هذا الأمر المثال لنهج FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

في المقابل، يجب أن تحصل على شيء مشابه لهذا:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

في هذا المثال، تحدد القيم داخل هذا النهج ما يمكن أو لا يمكن أن يفعله الاستخدام عندما يتعلق الأمر بالتواصل مع المستخدمين الخارجيين. على سبيل المثال، يجب تعيين الخاصية EnableOutsideAccess إلى True لكي يتمكن المستخدم من التواصل مع أشخاص من خارج المؤسسة. لاحظ أن هذه الخاصية لا تظهر في مركز مسؤولي Microsoft 365. بدلا من ذلك، يتم تعيين الخاصية تلقائيا إلى True أو False استنادا إلى التحديدات الأخرى التي تقوم بها. الخاصيتان الأخريان للفائدة هما:
  
- يشير **EnableFederationAccess** إلى ما إذا كان يمكن للمستخدم التواصل مع أشخاص من المجالات المتحدة.
    
- يشير **EnablePublicCloudAccess** إلى ما إذا كان يمكن للمستخدم التواصل مع Windows المستخدمين المباشرين.
    
لذلك، لا تقم بتغيير الخصائص المتعلقة الاتحاد مباشرة على حسابات المستخدمين (على سبيل المثال، **Set-CsUser -EnableFederationAccess $True**). بدلا من ذلك، يمكنك تعيين حساب نهج وصول خارجي يحتوي على قيم الخصائص المطلوبة التي تم تكوينها مسبقا. إذا أردنا أن يتمكن المستخدم من التواصل مع المستخدمين الخارجيين ومع المستخدمين Windows Live، يجب تعيين نهج يسمح بهذه الأنواع من الاتصالات لحساب المستخدم هذا.
  
إذا كنت تريد معرفة ما إذا كان يمكن لشخص ما التواصل مع مستخدمين من خارج المؤسسة أم لا، يجب عليك:
  
- تحديد نهج الوصول الخارجي الذي تم تعيينه لهذا المستخدم.
    
- تحديد القدرات المسموح بها أو غير المسموح بها من قبل هذا النهج.
    
على سبيل المثال، يمكنك القيام بذلك باستخدام هذا الأمر:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

يبحث هذا الأمر عن النهج المعين للمستخدم، ثم يبحث عن الإمكانات الممكنة أو المعطلة ضمن هذا النهج.
  
لإدارة نهج Skype for Business Online باستخدام PowerShell، راجع أوامر cmdlets ل:

- [نهج العميل](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [نهج المؤتمرات](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [نهج الهاتف المحمول](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [نهج البريد الصوتي عبر الإنترنت](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [نهج التوجيه الصوتي](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> خطة طلب Skype for Business Online هي نهج من كل النواحي باستثناء الاسم. تم اختيار اسم "خطة الطلب" بدلا من "نهج الطلب" على سبيل المثال لتوفير التوافق مع الإصدارات السابقة مع Office Communications Server ومع Exchange. 
  
على سبيل المثال، لإلقاء نظرة على جميع النهج الصوتية المتوفرة لاستخدامك، قم بتشغيل هذا الأمر:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> هذا يرجع قائمة بجميع النهج الصوتية المتوفرة لك. ومع ذلك، ضع في اعتبارك أنه لا يمكن تعيين كافة النهج لجميع المستخدمين. ويرجع ذلك إلى القيود المختلفة التي تتضمن الترخيص والموقع الجغرافي. (ما يسمى "[موقع الاستخدام](/previous-versions/azure/dn194136(v=azure.100))".) إذا كنت تريد معرفة نهج الوصول الخارجية ونهج المؤتمرات التي يمكن تعيينها لمستخدم معين، فاستخدم أوامر مشابهة لتلك: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

تحدد المعلمة ApplicableTo البيانات التي تم إرجاعها إلى النهج التي يمكن تعيينها للمستخدم المحدد (على سبيل المثال، أليكس دارو). اعتمادا على قيود موقع الترخيص والاستخدام، التي قد تمثل مجموعة فرعية من جميع النهج المتاحة. 
  
في بعض الحالات، لا يتم استخدام خصائص النهج مع Microsoft 365، بينما لا يمكن إدارة الخصائص الأخرى إلا من قبل موظفي دعم Microsoft. 
  
مع Skype for Business Online، يجب أن تتم إدارة المستخدمين بواسطة نهج من نوع ما. إذا كانت خاصية صالحة متعلقة بالنهج فارغة، فهذا يعني أن المستخدم المعني تتم إدارته بواسطة نهج عمومي، وهو نهج يتم تطبيقه تلقائيا على مستخدم ما لم يتم تعيين نهج لكل مستخدم على وجه التحديد. نظرا لأننا لا نرى نهج العميل مدرجا لحساب مستخدم، فإنه تتم إدارته بواسطة النهج العمومي. يمكنك تحديد نهج العميل العمومي باستخدام هذا الأمر:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Skype for Business Online باستخدام PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)