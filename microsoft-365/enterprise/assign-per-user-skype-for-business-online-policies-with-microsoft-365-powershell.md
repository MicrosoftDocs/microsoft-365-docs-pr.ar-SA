---
title: تعيين كل مستخدم Skype for Business عبر الإنترنت باستخدام PowerShell Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'ملخص: استخدم PowerShell Microsoft 365 لتعيين إعدادات الاتصال لكل مستخدم باستخدام Skype for Business عبر الإنترنت.'
ms.openlocfilehash: c49d465ffe0a6f1379681be0ae4faaf9982b6ef0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572840"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>تعيين كل مستخدم Skype for Business عبر الإنترنت باستخدام PowerShell Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

استخدام PowerShell Microsoft 365 طريقة فعالة لتعيين إعدادات الاتصال لكل مستخدم باستخدام Skype for Business عبر الإنترنت.
  
## <a name="prepare-to-run-the-powershell-commands"></a>التحضير لتشغيل أوامر PowerShell

استخدم هذه الإرشادات لإعداد الأوامر (تخطي الخطوات التي أكملتها بالفعل):
  
  > [!Note]
   > Skype for Business Online Connector حاليا جزءا من أحدث Teams PowerShell. إذا كنت تستخدم أحدث إصدار Teams PowerShell العام، فلا تحتاج إلى تثبيت Skype for Business Online Connector.

1. قم بتثبيت [Teams PowerShell النمطية](/microsoftteams/teams-powershell-install).
    
2. افتح Windows PowerShell موجه الأوامر ثم ادير الأوامر التالية: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   عند المطالبة، أدخل اسم حساب Skype for Business Online وكلمة المرور.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>تحديث إعدادات الاتصالات الخارجية لحساب مستخدم

لنفترض أنك تريد تغيير إعدادات الاتصالات الخارجية على حساب مستخدم. على سبيل المثال، تريد السماح ل Alex بالتواصل مع المستخدمين المتحدة (EnableFederationAccess يساوي True) ولكن ليس مع مستخدمي Windows Live (EnablePublicCloudAccesss يساوي False). للقيام بذلك، تحتاج إلى القيام بما يلي:
  
1. ابحث عن نهج وصول خارجي يلبي معاييرنا.
    
2. قم بتعيين نهج الوصول الخارجي هذا إلى Alex.
    
كيف يمكنك تحديد نهج الوصول الخارجي الذي يجب تعيينه إلى Alex؟ يرجع الأمر التالي كل سياسات الوصول الخارجية حيث تم تعيين EnableFederationAccess إلى True و EnablePublicCloudAccess إلى False:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

إلا إذا قمت بإنشاء أي مثيلات مخصصة ل ExternalAccessPolicy، فإن هذا الأمر يرجع نهج واحد يلبي معاييرنا (FederationOnly). فيما يلي مثال على ذلك:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

الآن وقد تعرفت على النهج الذي يجب تعيينه إلى Alex، يمكننا تعيين هذا النهج باستخدام [أمر cmdlet Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) . فيما يلي مثال على ذلك:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

إن تعيين نهج بسيط جدا: ما عليك سوى تحديد هوية المستخدم واسم النهج الذي سيتم تعيينه. 
  
وعندما يتعلق الأمر النهج وواجبات النهج، لن تقتصر على استخدام حسابات المستخدمين مرة واحدة. على سبيل المثال، افترض أنك تحتاج إلى قائمة بجميع المستخدمين المسموح لهم بالتواصل مع الشركاء المتحدة ومع Windows المباشرين. نحن نعلم بالفعل أنه تم تعيين نهج وصول المستخدم الخارجي إلى FederationAndPICDefault لهؤلاء المستخدمين. لأننا نعلم ذلك، يمكنك عرض قائمة بكل هؤلاء المستخدمين عن طريق تشغيل أمر واحد بسيط. إليك الأمر:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

بعبارة أخرى، اعرض لنا جميع المستخدمين حيث تم تعيين الخاصية ExternalAccessPolicy إلى FederationAndPICDefault. (ولحد كمية المعلومات التي تظهر على الشاشة، استخدم أمر cmdlet Select-Object لعرض اسم العرض الخاص بكل مستخدم فقط.) 
  
لتكوين كل حسابات المستخدمين لاستخدام النهج نفسه، استخدم هذا الأمر:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

يستخدم هذا الأمر Get-CsOnlineUser لإرجاع مجموعة من جميع المستخدمين الذين تم تمكينهم ل Lync، ثم يرسل كل هذه المعلومات إلى Grant-CsExternalAccessPolicy، الذي يعين نهج FederationAndPICDefault لكل مستخدم في المجموعة.
  
كمثال إضافي، افترض أنك قمت مسبقا بتعيين نهج FederationAndPICDefault إلى Alex والآن غيرت رأيك وتود أن يدار بواسطة نهج الوصول الخارجي العام. لا يمكنك تعيين النهج العام لأي شخص بشكل صريح. بدلا من ذلك، يتم استخدام النهج العام لمستخدم معين إذا لم يتم تعيين نهج لكل مستخدم لهذا المستخدم. وبالتالي، إذا كنا نريد أن يدار Alex بواسطة النهج العام، ستحتاج إلى عدم تعيين  أي نهج لكل مستخدم تم تعيينه له مسبقا. فيما يلي مثال على الأمر:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

يعين هذا الأمر اسم نهج الوصول الخارجي المعين إلى Alex إلى قيمة خالية ($Null). تعني القيمة Null "لا شيء". بعبارة أخرى، لا يتم تعيين نهج وصول خارجي إلى Alex. عندما لا يتم تعيين نهج وصول خارجي إلى مستخدم، يتم إدارة هذا المستخدم بعد ذلك بواسطة النهج العام.

## <a name="managing-large-numbers-of-users"></a>إدارة أعداد كبيرة من المستخدمين

لإدارة أعداد كبيرة من المستخدمين (1000 أو أكثر)، ستحتاج إلى دفع الأوامر عبر كتلة برنامج نصي باستخدام [الأمر cmdlet ل Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) .  في الأمثلة السابقة، في كل مرة يتم فيها تنفيذ أمر cmdlet، يجب إعداد المكالمة ثم انتظار النتيجة قبل إرسالها مرة أخرى.  عند استخدام كتلة برنامج نصي، يسمح هذا الأمر بتنفيذ cmdlets عن بعد، وبمجرد إكمالها، قم بإرسال البيانات مرة أخرى.

```powershell
$s = Get-PSSession | Where-Object { ($.ComputerName -like '*.online.lync.com' -or $.Computername -eq 'api.interfaces.records.teams.microsoft.com') -and $.State -eq 'Opened' -and $.Availability -eq 'Available' }

$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

سيعثر هذا على 500 مستخدم في كل مرة ليس لديهم نهج عميل. سيمنحهم نهج العميل "ClientPolicyNoIMURL" ونمث الوصول الخارجي "FederationAndPicDefault". يتم إرسال النتائج في مجموعات من 50، ثم يتم إرسال كل دفعة من 50 إلى الجهاز البعيد.
  
## <a name="see-also"></a>راجع أيضًا

[إدارة Skype for Business عبر الإنترنت باستخدام PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
