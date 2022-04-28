---
title: تعيين نهج Skype for Business Online لكل مستخدم باستخدام PowerShell ل Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: استخدم PowerShell Microsoft 365 لتعيين إعدادات الاتصال لكل مستخدم مع نهج Skype for Business Online.'
ms.openlocfilehash: 70120f6d296f958f44906a3526a7dcaa36b7eb04
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091380"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>تعيين نهج Skype for Business Online لكل مستخدم باستخدام PowerShell ل Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

يعد استخدام PowerShell Microsoft 365 طريقة فعالة لتعيين إعدادات الاتصال لكل مستخدم مع نهج Skype for Business Online.
  
## <a name="prepare-to-run-the-powershell-commands"></a>التحضير لتشغيل أوامر PowerShell

استخدم هذه الإرشادات لإعداد تشغيل الأوامر (تخطي الخطوات التي أكملتها بالفعل):
  
  > [!Note]
   > Skype for Business Online Connector هو حاليا جزء من أحدث وحدة Teams PowerShell. إذا كنت تستخدم أحدث إصدار عام Teams PowerShell، فلن تحتاج إلى تثبيت Skype for Business Online Connector.

1. تثبيت [الوحدة النمطية Teams PowerShell](/microsoftteams/teams-powershell-install).
    
2. افتح موجه أوامر Windows PowerShell وقم بتشغيل الأوامر التالية: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   عند مطالبتك، أدخل اسم حساب مسؤول Skype for Business عبر الإنترنت وكلمة المرور.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>تحديث إعدادات الاتصال الخارجية لحساب مستخدم

لنفترض أنك تريد تغيير إعدادات الاتصال الخارجي على حساب مستخدم. على سبيل المثال، تريد السماح ل Alex بالاتصال بالمستخدمين المتحدين (EnableFederationAccess يساوي True) ولكن ليس مع Windows Live users (EnablePublicCloudAccess يساوي False). للقيام بذلك، تحتاج إلى القيام بأمرين:
  
1. ابحث عن نهج وصول خارجي يلبي معاييرنا.
    
2. تعيين نهج الوصول الخارجي هذا إلى أليكس.
    
كيف يمكنك تحديد نهج الوصول الخارجي لتعيين أليكس؟ يرجع الأمر التالي كافة نهج الوصول الخارجية حيث تم تعيين EnableFederationAccess إلى True وتم تعيين EnablePublicCloudAccess إلى False:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

ما لم تكن قد أنشأت أي مثيلات مخصصة ل ExternalAccessPolicy، فإن هذا الأمر يرجع نهجا واحدا يفي بمعاييرنا (FederationOnly). فيما يلي مثال على ذلك:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

الآن بعد أن تعرفت على النهج الذي يجب تعيينه إلى أليكس، يمكننا تعيين هذا النهج باستخدام [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) cmdlet. فيما يلي مثال على ذلك:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

تعيين نهج بسيط جدا: يمكنك ببساطة تحديد هوية المستخدم واسم النهج الذي سيتم تعيينه. 
  
وعندما يتعلق الأمر بالنهج وتعيينات النهج، لا تقتصر على العمل مع حسابات المستخدمين مرة واحدة. على سبيل المثال، افترض أنك بحاجة إلى قائمة بجميع المستخدمين المسموح لهم بالاتصال بالشركاء الخارجيين ومع مستخدمي Windows Live. نحن نعلم بالفعل أنه تم تعيين نهج وصول المستخدم الخارجي إلى FederationAndPICDefault لهؤلاء المستخدمين. لأننا نعلم ذلك، يمكنك عرض قائمة بجميع هؤلاء المستخدمين عن طريق تشغيل أمر واحد بسيط. إليك الأمر:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

بمعنى آخر، أظهر لنا جميع المستخدمين حيث تم تعيين خاصية ExternalAccessPolicy إلى FederationAndPICDefault. (ولحد من كمية المعلومات التي تظهر على الشاشة، استخدم Select-Object cmdlet لعرض اسم العرض لكل مستخدم فقط.) 
  
لتكوين جميع حسابات المستخدمين لاستخدام نفس النهج، استخدم هذا الأمر:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

يستخدم هذا الأمر Get-CsOnlineUser لإرجاع مجموعة من جميع المستخدمين الذين تم تمكينهم ل Lync، ثم يرسل كل هذه المعلومات إلى Grant-CsExternalAccessPolicy، الذي يقوم بتعيين نهج FederationAndPICDefault لكل مستخدم في المجموعة.
  
كمثال إضافي، لنفترض أنك قمت بتعيين نهج FederationAndPICDefault مسبقا، والآن قمت بتغيير رأيك وترغب في إدارته من خلال نهج الوصول الخارجي العام. لا يمكنك تعيين النهج العمومي بشكل صريح إلى أي شخص. بدلا من ذلك، يتم استخدام النهج العمومي لمستخدم معين إذا لم يتم تعيين نهج لكل مستخدم لهذا المستخدم. لذلك، إذا أردنا أن تتم إدارة أليكس بواسطة النهج العالمي، فأنت بحاجة إلى  *إلغاء تعيين*  أي نهج لكل مستخدم تم تعيينه له مسبقا. فيما يلي مثال على الأمر:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

يعين هذا الأمر اسم نهج الوصول الخارجي المعين إلى أليكس إلى قيمة خالية ($Null). القيمة الخالية تعني "لا شيء". وبعبارة أخرى، لا يتم تعيين نهج وصول خارجي إلى أليكس. عندما لا يتم تعيين نهج وصول خارجي إلى مستخدم، تتم إدارة هذا المستخدم بواسطة النهج العمومي.

## <a name="managing-large-numbers-of-users"></a>إدارة أعداد كبيرة من المستخدمين

لإدارة أعداد كبيرة من المستخدمين (1000 أو أكثر)، تحتاج إلى دفع الأوامر عبر كتلة برنامج نصي باستخدام [استدعاء الأمر](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.  في الأمثلة السابقة، في كل مرة يتم فيها تنفيذ أمر cmdlet، يجب إعداد المكالمة ثم انتظار النتيجة قبل إرسالها مرة أخرى.  عند استخدام كتلة برنامج نصي، يسمح هذا الأمر بتنفيذ أوامر cmdlets عن بعد، وبمجرد الانتهاء، أرسل البيانات مرة أخرى.

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

سيؤدي ذلك إلى العثور على 500 مستخدم في كل مرة ليس لديهم نهج عميل. سيمنحهم نهج العميل "ClientPolicyNoIMURL" ونهج الوصول الخارجي "FederationAndPicDefault". يتم دفع النتائج في مجموعات من 50 ثم يتم إرسال كل دفعة من 50 إلى الجهاز البعيد.
  
## <a name="see-also"></a>راجع أيضًا

[إدارة Skype for Business Online باستخدام PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
