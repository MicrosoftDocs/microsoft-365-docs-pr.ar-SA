---
title: إدارة SharePoint والمجموعات عبر الإنترنت باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: في هذه المقالة، تعرف على كيفية استخدام PowerShell Microsoft 365 لإدارة SharePoint والمجموعات والمواقع عبر الإنترنت.
ms.openlocfilehash: e2166753b1be56c19011a1fc7e20d1584a5d3004
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681183"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>إدارة SharePoint والمجموعات عبر الإنترنت باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

إذا كنت مسؤولا SharePoint Online تعمل مع قوائم كبيرة من حسابات المستخدمين أو المجموعات وتريد طريقة أسهل لإدارة هذه الحسابات، يمكنك استخدام PowerShell Microsoft 365.

قبل البدء، تتطلب الإجراءات في هذه المقالة الاتصال ب SharePoint Online. للحصول على الإرشادات، [راجع الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>الحصول على قائمة بالمواقع والمجموعات والمستخدمين

قبل أن نبدأ بإدارة المستخدمين والمجموعات، ستحتاج إلى الحصول على قوائم بالمواقع والمجموعات والمستخدمين. يمكنك بعد ذلك استخدام هذه المعلومات للعمل من خلال المثال الوارد في هذه المقالة.

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

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>إضافة مستخدم إلى المجموعة "مسؤولي مجموعة المواقع"

يمكنك استخدام `Set-SPOUser` الأمر cmdlet لإضافة مستخدم إلى قائمة مسؤولي مجموعة المواقع الموقعة في مجموعة مواقع ويب.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

لاستخدام هذه الأوامر، استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك < والأحرف >، بالأسماء الصحيحة.

على سبيل المثال، تضيف مجموعة الأوامر هذه Opal Castillo (opalc اسم المستخدم) إلى قائمة مسؤولي مجموعة المواقع المشتركة في مجموعة مواقع ContosoTest المشتركة في إيجار Contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

يمكنك نسخ هذه الأوامر ولصقها في المفكرة، وتغيير القيم المتغيرة ل $tenant و $site و $user إلى القيم الفعلية من بيئتك، ثم لصقها في نافذة SharePoint Online Management Shell لتشغيلها.

## <a name="add-a-user-to-other-site-collection-groups"></a>إضافة مستخدم إلى مجموعات مجموعات مواقع أخرى

في هذه المهمة، سنستخدم `Add-SPOUser` الأمر cmdlet لإضافة مستخدم إلى مجموعة SharePoint مجموعة مواقع ويب.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

على سبيل المثال، دعنا نضيف Glen Rife (اسم المستخدم glenr) إلى مجموعة المراجعين في مجموعة مواقع ContosoTest في إيجار contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>إنشاء مجموعة مجموعة مواقع ويب

يمكنك استخدام `New-SPOSiteGroup` الأمر cmdlet لإنشاء مجموعة SharePoint جديدة وإضافتها إلى مجموعة مواقع ويب.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

يمكن تحديث خصائص المجموعة، مثل مستويات الأذونات، لاحقا باستخدام `Set-SPOSiteGroup` cmdlet.

على سبيل المثال، دعنا نضيف مجموعة المراجعين مع أذونات عرض فقط إلى مجموعة مواقع contosotest في إيجار contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>إزالة مستخدمين من مجموعة

قد تحتاج في بعض الأحيان إلى إزالة مستخدم من موقع أو حتى من كل المواقع. ربما ينتقل الموظف من قسم إلى آخر أو يغادر الشركة. يمكنك القيام بذلك لموظف واحد بسهولة في واجهة المستخدم، ولكن لا يمكن القيام بذلك بسهولة عندما تحتاج إلى نقل قسمة كاملة من موقع إلى آخر.

ومع ذلك، باستخدام SharePoint Online Management Shell وملفات CSV، يكون هذا الأمر سريعا وسهلا. في هذه المهمة، ستستخدم Windows PowerShell لإزالة مستخدم من مجموعة أمان مجموعة مواقع ويب. بعد ذلك، سوف تستخدم ملف CSV وتزيل الكثير من المستخدمين من مواقع مختلفة.

سنستخدم الأمر cmdlet "Remove-SPOUser" لإزالة مستخدم Microsoft 365 واحد من مجموعة مجموعة مواقع ويب حتى يمكننا رؤية بناء جملة الأوامر. إليك كيفية مظهر بناء الجملة:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

على سبيل المثال، دعنا نزيل باسيف من مجموعة مدققي مجموعة المواقع في مجموعة مواقع contosotest في إيجار contoso:

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

لنفترض أننا نريد إزالة بازيلاء بازلاء من كل المجموعات التي يوجد فيها حاليا. إليك كيفية القيام بذلك:

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> هذا مجرد مثال. يجب ألا تقوم بتشغيل هذا الأمر إلا إذا كان عليك بالفعل إزالة مستخدم من كل مجموعة، على سبيل المثال إذا غادر المستخدم الشركة.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>الإدارة التلقائية للمجموعات والمستخدمين الكبيرين

لإضافة عدد كبير من الحسابات إلى SharePoint المواقع الأخرى وإعطائها الأذونات، يمكنك استخدام مركز مسؤولي Microsoft 365 أو أوامر PowerShell الفردية أو PowerShell وملف CSV. من بين هذه الخيارات، ملف CSV هو أسرع طريقة لأتمتة هذه المهمة.

العملية الأساسية هي إنشاء ملف CSV يحتوي على رؤوس (أعمدة) تتوافق مع المعلمات التي يحتاجها Windows PowerShell النصي. يمكنك بسهولة إنشاء مثل هذه القائمة في Excel ثم تصديرها كملف CSV. بعد ذلك، يمكنك استخدام Windows PowerShell نصي للتكرير عبر السجلات (الصفوف) في ملف CSV، مع إضافة المستخدمين إلى المجموعات والمجموعات إلى المواقع.

على سبيل المثال، لننشئ ملف CSV لتعريف مجموعة من مجموعات المواقع والمجموعات والأذونات. بعد ذلك، سنقوم بإنشاء ملف CSV  لملء المجموعات بالمستخدمين. وأخيرا، سنقوم بإنشاء برنامج نصي Windows PowerShell الذي ينشئ المجموعات وي ملءها.

سيضيف ملف CSV الأول مجموعة واحدة أو أكثر إلى مجموعة واحدة أو أكثر من مجموعات المواقع، كما سيضفي هذه البنية:

الرأس:

```powershell
Site,Group,PermissionLevels
```

العنصر:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

فيما يلي مثال لملف:

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

سيضيف ملف CSV الثاني مستخدما واحدا أو أكثر إلى مجموعة واحدة أو أكثر وسيستخدم هذه البنية:

الرأس:

```powershell
Group,LoginName,Site
```

العنصر:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

فيما يلي مثال لملف:

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

للخطوة التالية، يجب أن يكون لديك ملفي CSV محفوظين في محرك الأقراص. فيما يلي أمثلة على الأوامر التي تستخدم ملفات CSV وإضافة الأذونات وعضوية المجموعة:

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

يستورد البرنامج النصي محتويات ملف CSV ويستخدم القيم في الأعمدة لملء معلمات الأمرين **New-SPOSiteGroup** و **Add-SPOUser** . في مثالنا، نقوم بحفظ هذا الملف في مجلد O365Admin على محرك الأقراص C، ولكن يمكنك حفظه في أي مكان تريده.

والآن، دعنا نزيل مجموعة من الأشخاص لمجموعات متعددة في مواقع مختلفة باستخدام ملف CSV نفسه. إليك مثال على الأمر:

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>إنشاء تقارير المستخدمين

قد ترغب في الحصول على تقرير لبضعة مواقع وعرض المستخدمين لتلك المواقع ومستوى الأذونات وخصائص أخرى. هذه هي الطريقة التي يبدو بها بناء الجملة:

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

سيلتقط هذا بيانات هذه المواقع الثلاثة ويكتبها إلى ملف نصي على محرك الأقراص المحلي. المعلمة –سيضيف ال إلحاق محتوى جديدا إلى ملف موجود.

على سبيل المثال، لندير تقريرا على مواقع ContosoTest و TeamSite01 و Project01 لمستأجر Contoso1:

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

كان علينا تغيير المتغير **$site فقط.** يحتفظ **$tenant** المتغير بقيمته خلال عمليات التشغيل الثلاثة كلها من الأمر.

ومع ذلك، ماذا لو أردت القيام بذلك لكل موقع؟ يمكنك القيام بذلك دون الحاجة إلى كتابة كل مواقع الويب هذه باستخدام هذا الأمر:

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

هذا التقرير بسيط إلى حد ما، كما يمكنك إضافة المزيد من التعليمات البرمجية لإنشاء تقارير أو تقارير أكثر تحديدا تتضمن معلومات أكثر تفصيلا. ولكن من المفترض أن يعطيك هذا فكرة حول كيفية استخدام SharePoint Online Management Shell لإدارة المستخدمين في بيئة SharePoint Online.

## <a name="see-also"></a>راجع أيضًا

[الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[إدارة SharePoint عبر الإنترنت باستخدام PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
