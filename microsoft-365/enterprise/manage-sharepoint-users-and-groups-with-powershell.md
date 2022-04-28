---
title: إدارة SharePoint عبر الإنترنت من المستخدمين والمجموعات باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell Microsoft 365 لإدارة SharePoint المستخدمين والمجموعات والمواقع عبر الإنترنت.
ms.openlocfilehash: 78c829e476c63e435d9543b3a4175cdbbccb76e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100666"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>إدارة SharePoint عبر الإنترنت من المستخدمين والمجموعات باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

إذا كنت مسؤولا SharePoint Online يعمل مع قوائم كبيرة من حسابات المستخدمين أو المجموعات وتريد طريقة أسهل لإدارتها، يمكنك استخدام PowerShell Microsoft 365.

قبل البدء، تتطلب منك الإجراءات الواردة في هذه المقالة الاتصال ب SharePoint Online. للحصول على الإرشادات، راجع [الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>الحصول على قائمة بالمواقع والمجموعات والمستخدمين

قبل أن نبدأ في إدارة المستخدمين والمجموعات، تحتاج إلى الحصول على قوائم بالمواقع والمجموعات والمستخدمين. يمكنك بعد ذلك استخدام هذه المعلومات للعمل على المثال الوارد في هذه المقالة.

احصل على قائمة بالمواقع في المستأجر باستخدام هذا الأمر:

```powershell
Get-SPOSite
```

احصل على قائمة بالمجموعات في المستأجر باستخدام هذا الأمر:

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

احصل على قائمة بالمستخدمين في المستأجر باستخدام هذا الأمر:

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>إضافة مستخدم إلى مجموعة مسؤولي مجموعة المواقع المشتركة

يمكنك استخدام `Set-SPOUser` cmdlet لإضافة مستخدم إلى قائمة مسؤولي مجموعة المواقع المشتركة على مجموعة مواقع مشتركة.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

لاستخدام هذه الأوامر، استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف < والأحرف >، بالأسماء الصحيحة.

على سبيل المثال، تضيف هذه المجموعة من الأوامر Opal Castnam (اسم المستخدم opalc) إلى قائمة مسؤولي مجموعة المواقع المشتركة على مجموعة المواقع المشتركة ContosoTest في إيجار Contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

يمكنك نسخ هذه الأوامر ولصقها في المفكرة، وتغيير القيم المتغيرة $tenant، $site، $user إلى قيم فعلية من بيئتك، ثم لصقها في نافذة SharePoint Online Management Shell لتشغيلها.

## <a name="add-a-user-to-other-site-collection-groups"></a>إضافة مستخدم إلى مجموعات مواقع مشتركة أخرى

في هذه المهمة، سنستخدم `Add-SPOUser` cmdlet لإضافة مستخدم إلى مجموعة SharePoint على مجموعة مواقع مشتركة.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

على سبيل المثال، دعنا نضيف Tahoma Rife (اسم المستخدم) إلى مجموعة المراجعين على مجموعة المواقع المشتركة ContosoTest في إيجار contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>إنشاء مجموعة مواقع مشتركة

يمكنك استخدام `New-SPOSiteGroup` cmdlet لإنشاء مجموعة SharePoint جديدة وإضافتها إلى مجموعة مواقع مشتركة.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

يمكن تحديث خصائص المجموعة، مثل مستويات الأذونات، لاحقا باستخدام `Set-SPOSiteGroup` cmdlet.

على سبيل المثال، دعنا نضيف مجموعة المراجعين مع عرض الأذونات فقط إلى مجموعة المواقع المشتركة contosotest في إيجار contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>إزالة مستخدمين من مجموعة

في بعض الأحيان، يتعين عليك إزالة مستخدم من موقع أو حتى جميع المواقع. ربما ينتقل الموظف من قسم إلى آخر أو يترك الشركة. يمكنك القيام بذلك لموظف واحد بسهولة في واجهة المستخدم، ولكن لا يتم ذلك بسهولة عندما يتعين عليك نقل قسم كامل من موقع إلى آخر.

ومع ذلك باستخدام SharePoint Online Management Shell وملفات CSV، فإن هذا الأمر سريع وسهل. في هذه المهمة، ستستخدم Windows PowerShell لإزالة مستخدم من مجموعة أمان مجموعة مواقع مشتركة. ثم ستستخدم ملف CSV وتزيل الكثير من المستخدمين من مواقع مختلفة.

سنستخدم الأمر cmdlet "Remove-SPOUser" لإزالة مستخدم واحد Microsoft 365 من مجموعة مجموعة مواقع مشتركة حتى نتمكن من رؤية بناء جملة الأمر. إليك كيفية مظهر بناء الجملة:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

على سبيل المثال، دعنا نزيل "باه" من مجموعة "مدققي" مجموعة المواقع المشتركة في مجموعة المواقع المشتركة contosotest في إيجار contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

لنفترض أننا أردنا إزالة "باه" من جميع المجموعات التي يوجد بها حاليا. إليك كيفية القيام بذلك:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> هذا مجرد مثال. يجب عدم تشغيل هذا الأمر إلا إذا كان عليك بالفعل إزالة مستخدم من كل مجموعة، على سبيل المثال إذا ترك المستخدم الشركة.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>أتمتة إدارة قوائم كبيرة من المستخدمين والمجموعات

لإضافة عدد كبير من الحسابات إلى مواقع SharePoint ومنحها أذونات، يمكنك استخدام مركز مسؤولي Microsoft 365 أو أوامر PowerShell الفردية أو PowerShell وملف CSV. من بين هذه الخيارات، ملف CSV هو أسرع طريقة لأتمتة هذه المهمة.

العملية الأساسية هي إنشاء ملف CSV يحتوي على رؤوس (أعمدة) تتوافق مع المعلمات التي يحتاجها البرنامج النصي Windows PowerShell. يمكنك بسهولة إنشاء مثل هذه القائمة في Excel ثم تصديرها كملف CSV. بعد ذلك، يمكنك استخدام برنامج نصي Windows PowerShell للتكرار عبر السجلات (الصفوف) في ملف CSV، وإضافة المستخدمين إلى المجموعات والمجموعات إلى المواقع.

على سبيل المثال، لننشئ ملف CSV لتعريف مجموعة من مجموعات المواقع المشتركة والمجموعات والأذونات. بعد ذلك، سنقوم بإنشاء ملف CSV لملء المجموعات بالمستخدمين. وأخيرا، سنقوم بإنشاء وتشغيل برنامج نصي Windows PowerShell الذي ينشئ المجموعات ويملأها.

سيقوم ملف CSV الأول بإضافة مجموعة واحدة أو أكثر إلى مجموعة مواقع مشتركة واحدة أو أكثر وسيحتوي على هذه البنية:

راس:

```powershell
Site,Group,PermissionLevels
```

البند:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

فيما يلي مثال على الملف:

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

سيضيف ملف CSV الثاني مستخدما واحدا أو أكثر إلى مجموعة واحدة أو أكثر وسيحتوي على هذه البنية:

راس:

```powershell
Group,LoginName,Site
```

البند:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

فيما يلي مثال على الملف:

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

للخطوة التالية، يجب حفظ ملفي CSV في محرك الأقراص. فيما يلي أمثلة على الأوامر التي تستخدم كل من ملفات CSV وإضافة الأذونات وعضوية المجموعة:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

يستورد البرنامج النصي محتويات ملف CSV ويستخدم القيم في الأعمدة لتعبئة معلمات **New-SPOSiteGroup** وأوامر **Add-SPOUser** . في مثالنا، نقوم بحفظ هذا الملف إلى مجلد O365Admin على محرك الأقراص C، ولكن يمكنك حفظه أينما أردت.

الآن، دعونا نزيل مجموعة من الأشخاص لعدة مجموعات في مواقع مختلفة باستخدام نفس ملف CSV. فيما يلي مثال على الأمر:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>إنشاء تقارير المستخدم

قد تحتاج إلى الحصول على تقرير لبعض المواقع وعرض المستخدمين لهذه المواقع ومستوى الأذونات والخصائص الأخرى. هذه هي الطريقة التي يبدو بها بناء الجملة:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

سيؤدي ذلك إلى الحصول على البيانات الخاصة بهذه المواقع الثلاثة وكتابتها إلى ملف نصي على محرك الأقراص المحلي. ستقوم المعلمة –Append بإضافة محتوى جديد إلى ملف موجود.

على سبيل المثال، لنقم بتشغيل تقرير على مواقع ContosoTest و TeamSite01 وProject01 لمستأجر Contoso1:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

كان علينا تغيير المتغير **$site** فقط. يحتفظ متغير **$tenant** بقيمته من خلال جميع التشغيلات الثلاثة للأمر.

ومع ذلك، ماذا لو أردت القيام بذلك لكل موقع؟ يمكنك القيام بذلك دون الحاجة إلى كتابة كافة مواقع الويب هذه باستخدام هذا الأمر:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

هذا التقرير بسيط إلى حد ما، ويمكنك إضافة المزيد من التعليمات البرمجية لإنشاء تقارير أو تقارير أكثر تحديدا تتضمن معلومات أكثر تفصيلا. ولكن يجب أن يمنحك هذا فكرة عن كيفية استخدام SharePoint Online Management Shell لإدارة المستخدمين في بيئة SharePoint Online.

## <a name="see-also"></a>راجع أيضًا

[الاتصال إلى SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[إدارة SharePoint Online باستخدام PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
