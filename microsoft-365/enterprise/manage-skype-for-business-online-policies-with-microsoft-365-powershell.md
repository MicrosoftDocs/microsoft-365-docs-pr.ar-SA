---
title: إدارة Skype for Business عبر الإنترنت باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'ملخص: استخدم PowerShell لإدارة Skype for Business حساب المستخدم عبر الإنترنت باستخدام النهج.'
ms.openlocfilehash: 674ea6daba498279537f7c302f4bf4d791ee00f5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575329"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>إدارة Skype for Business عبر الإنترنت باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

لإدارة العديد من خصائص حساب المستخدم Skype for Business Online، يجب تحديدها كعقارات لنهج باستخدام PowerShell Microsoft 365.
  
## <a name="before-you-begin"></a>قبل البدء

استخدم هذه الإرشادات لإعداد الأوامر (تخطي الخطوات التي أكملتها بالفعل):

  > [!Note]
  > Skype for Business Online Connector حاليا جزءا من أحدث Teams PowerShell. إذا كنت تستخدم أحدث إصدار Teams PowerShell العام، فلا تحتاج إلى تثبيت Skype for Business Online Connector.

1. قم بتثبيت [Teams PowerShell النمطية](/microsoftteams/teams-powershell-install).
    
2. افتح Windows PowerShell موجه الأوامر ثم ادير الأوامر التالية: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   عند المطالبة، أدخل اسم حساب Skype for Business Online وكلمة المرور.
    
## <a name="manage-user-account-policies"></a>إدارة سياسات حساب المستخدم

يتم Skype for Business خصائص حساب المستخدم عبر الإنترنت باستخدام السياسات. إن السياسات عبارة عن مجموعات من الإعدادات التي يمكن تطبيقها على مستخدم واحد أو أكثر. لنظرة على كيفية تكوين النهج، يمكنك تشغيل أمر المثال هذا لن نهج FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

بدورك، يجب أن تستعيد شيئا مماثلا لهذا:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

في هذا المثال، تحدد القيم الموجودة في هذا النهج ما يمكن أو لا يمكن أن يقوم به الاستخدام عندما يتعلق الأمر بالتواصل مع المستخدمين المتحدة. على سبيل المثال، يجب تعيين الخاصية EnableOutsideAccess إلى True لكي يتمكن المستخدم من التواصل مع أشخاص من خارج المؤسسة. لاحظ أن هذه الخاصية لا تظهر في مركز مسؤولي Microsoft 365. بدلا من ذلك، يتم تعيين الخاصية تلقائيا إلى True أو False استنادا إلى التحديدات الأخرى التي تقوم بها. الخصائص الأخرى التي تهمك هي:
  
- **EnableFederationAccess يشير** إلى ما إذا كان يمكن للمستخدم التواصل مع أشخاص من مجالات متكاتف.
    
- **يشير EnablePublicCloudAccess إلى** ما إذا كان يمكن للمستخدم التواصل مع المستخدمين Windows المباشرين.
    
وبالتالي، لا تغير بشكل مباشر الخصائص ذات الصلة بالاتحاد في حسابات المستخدمين (على سبيل المثال **، Set-CsUser -EnableFederationAccess $True**). بدلا من ذلك، يمكنك تعيين نهج وصول خارجي إلى حساب تم تكوين قيم الخاصية المطلوبة مسبقا. إذا كنا نريد أن يتمكن المستخدم من التواصل مع المستخدمين المتحدة ومع Windows المباشرين، فيجب تعيين نهج يسمح لهذه الأنواع من الاتصالات باستخدام حساب المستخدم هذا.
  
إذا كنت تريد معرفة ما إذا كان بإمكان شخص ما التواصل مع مستخدمين من خارج المؤسسة أم لا، يجب عليك القيام بما يلي:
  
- تحديد نهج الوصول الخارجي الذي تم تعيينه لهذا المستخدم.
    
- حدد القدرات المسموح بها أو غير المسموح بها في هذا النهج.
    
على سبيل المثال، يمكنك القيام بذلك باستخدام هذا الأمر:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

يعثر هذا الأمر على النهج المعين للمستخدم، ثم يعثر على الإمكانات التي تم تمكينها أو تعطيلها ضمن هذا النهج.
  
لإدارة Skype for Business عبر الإنترنت باستخدام PowerShell، راجع cmdlets ل:

- [نهج العميل](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [نهج المؤتمرات](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [نهج الأجهزة المحمولة](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [نهج البريد الصوتي عبر الإنترنت](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [نهج توجيه الصوت](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> إن Skype for Business الطلب عبر الإنترنت هو نهج من جميع الأوجه باستثناء الاسم. تم اختيار الاسم "خطة الطلب" بدلا من ، على سبيل المثال، "نهج الطلب" من أجل توفير التوافق مع الإصدارات Office Communications Server ومع Exchange. 
  
على سبيل المثال، لنظرة إلى كل سياسات الصوت المتوفرة لاستخدامك، يمكنك تشغيل هذا الأمر:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> يرجع ذلك قائمة بكل سياسات الصوت المتوفرة لك. ومع ذلك، تذكر أنه لا يمكن تعيين كل السياسات لجميع المستخدمين. يعود سبب ذلك إلى القيود المتنوعة التي تتضمن الترخيص والموقع الجغرافي. (ما يسمى "[موقع الاستخدام](/previous-versions/azure/dn194136(v=azure.100))".) إذا كنت تريد معرفة سياسات الوصول الخارجي ونهج المؤتمرات التي يمكن تعيينها إلى مستخدم معين، فاستخدم أوامر مماثلة لتلك: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

تحدد المعلمة ApplicableTo البيانات التي يتم إرجاعها إلى النهج التي يمكن تعيينها إلى المستخدم المحدد (على سبيل المثال، Alex Darrow). استنادا إلى قيود موقع الاستخدام والترخيص، التي قد تمثل مجموعة فرعية من كل السياسات المتوفرة. 
  
في بعض الحالات، لا يتم استخدام خصائص السياسات مع Microsoft 365، بينما يمكن إدارة الآخرين بواسطة موظفي دعم Microsoft فقط. 
  
باستخدام Skype for Business Online، يجب إدارة المستخدمين بواسطة نهج من نوع ما. إذا كانت الخاصية الصالحة ذات الصلة ب النهج فارغة، فهذا يعني أنه يتم إدارة المستخدم المعني بواسطة نهج عام، وهو نهج يتم تطبيقه تلقائيا على المستخدم ما لم يتم تعيين نهج لكل مستخدم على وجه التحديد. نظرا لعدم تمكننا من رؤية نهج عميل مدرج لحساب مستخدم، فإنه مدار بواسطة النهج العام. يمكنك تحديد نهج العميل العام باستخدام هذا الأمر:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>راجع أيضًا

[إدارة Skype for Business عبر الإنترنت باستخدام PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)