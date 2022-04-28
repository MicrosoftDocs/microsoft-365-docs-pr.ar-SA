---
title: إنشاء مواقع SharePoint Online وإضافة مستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: استخدم PowerShell لإنشاء مواقع SharePoint Online جديدة ثم أضف مستخدمين ومجموعات إلى تلك المواقع.'
ms.openlocfilehash: 9d99f98825d88e2d2e63f106a7b5704c773c8be1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101326"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>إنشاء مواقع SharePoint Online وإضافة مستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

عند استخدام PowerShell Microsoft 365 لإنشاء مواقع SharePoint عبر الإنترنت وإضافة مستخدمين، يمكنك تنفيذ المهام بسرعة وتكرارا بشكل أسرع بكثير مما يمكنك القيام به في مركز مسؤولي Microsoft 365. يمكنك أيضا تنفيذ المهام التي لا يمكن تنفيذها في مركز مسؤولي Microsoft 365.

## <a name="connect-to-sharepoint-online"></a>الاتصال إلى SharePoint Online

تتطلب منك الإجراءات الواردة في هذا الموضوع الاتصال ب SharePoint Online. للحصول على الإرشادات، راجع [الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>الخطوة 1: إنشاء مجموعات مواقع مشتركة جديدة باستخدام PowerShell

إنشاء مواقع متعددة باستخدام PowerShell وملف .csv تقوم بإنشائه باستخدام التعليمات البرمجية النموذجية المتوفرة المفكرة. بالنسبة إلى هذا الإجراء، ستقوم باستبدال معلومات العنصر النائب المعروضة بين قوسين بمعلومات خاصة بالموقع والمستأجر. تتيح لك هذه العملية إنشاء ملف واحد وتشغيل أمر PowerShell واحد يستخدم هذا الملف. وهذا يجعل الإجراءات المتخذة قابلة للتكرار وقابلة للنقل ويزيل العديد من الأخطاء، إن لم يكن كلها، التي يمكن أن تأتي من كتابة أوامر طويلة في SharePoint Online Management Shell. هناك جزأان لهذا الإجراء. أولا ستقوم بإنشاء ملف .csv، ثم ستقوم بالإشارة إلى ملف .csv باستخدام PowerShell، الذي سيستخدم محتوياته لإنشاء المواقع.

يستورد PowerShell cmdlet ملف .csv ويرسله إلى حلقة داخل الأقواس المتعرجة التي تقرأ السطر الأول من الملف كرؤوس أعمدة. ثم يكرر PowerShell cmdlet السجلات المتبقية، وينشئ مجموعة مواقع مشتركة جديدة لكل سجل، ويعين خصائص مجموعة المواقع المشتركة وفقا لرؤوس الأعمدة.

### <a name="create-a-csv-file"></a>إنشاء ملف .csv

> [!NOTE]
> تعمل معلمة الحصة النسبية للمورد على المواقع الكلاسيكية فقط. إذا كنت تستخدم هذه المعلمة على موقع حديث، فقد تتلقى رسالة تحذير تفيد بإهمالها.

1. افتح المفكرة، والصق كتلة النص التالية فيه:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   حيث يكون *المستأجر* هو اسم المستأجر الخاص بك، *والمالك* هو اسم المستخدم الخاص بالمستأجر الذي تريد منحه دور مسؤول مجموعة المواقع المشتركة الأساسي.

   (يمكنك الضغط على Ctrl+H عند استخدام المفكرة للاستبدال المجمع بشكل أسرع.)

2. احفظ الملف على سطح المكتب ك **SiteCollections.csv**.

> [!TIP]
> قبل استخدام هذا أو أي ملف برنامج نصي .csv أو Windows PowerShell آخر، من الممارسات الجيدة التأكد من عدم وجود أحرف غريبة أو غير مطبوعة. افتح الملف في Word، وفي الشريط، انقر فوق أيقونة الفقرة لإظهار الأحرف غير المطبوعة. يجب ألا تكون هناك أحرف غير طباعة غريبة. على سبيل المثال، يجب ألا تكون هناك أي علامات فقرات تتجاوز علامات الفقرة الأخيرة في نهاية الملف.

### <a name="run-the-windows-powershell-command"></a>تشغيل الأمر Windows PowerShell

1. في موجه Windows PowerShell، اكتب الأمر التالي أو انسخه والصقه، ثم اضغط على مفتاح الإدخال Enter:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   حيث *يساوي MyAlias* الاسم المستعار للمستخدم.

2. انتظر ظهور المطالبة Windows PowerShell مرة أخرى. قد يستغرق الأمر دقيقة أو دقيقتين.

3. في موجه Windows PowerShell، اكتب أمر cmdlet التالي أو انسخه والصقه، واضغط على مفتاح الإدخال Enter:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. لاحظ مجموعات المواقع المشتركة الجديدة في القائمة. باستخدام ملف CSV المثال، سترى مجموعات المواقع المشتركة التالية: **TeamSite01** و **Blog01** **وProject01** و **Community01**

هذا هو. لقد قمت بإنشاء مجموعات مواقع مشتركة متعددة باستخدام ملف .csv الذي أنشأته والأمر Windows PowerShell واحد. أنت الآن جاهز لإنشاء المستخدمين وتعيينهم إلى هذه المواقع.

## <a name="step-2-add-users-and-groups"></a>الخطوة 2: إضافة مستخدمين ومجموعات

الآن ستقوم بإنشاء مستخدمين وإضافتهم إلى مجموعة مواقع مشتركة. ثم ستستخدم ملف .csv لتحميل مجموعات ومستخدمين جدد بشكل مجمع.

تستمر الإجراءات التالية في استخدام المواقع المثال TeamSite01 و Blog01 وProject01 و Community01.

### <a name="create-csv-and-ps1-files"></a>إنشاء ملفات .csv .ps1

1. افتح المفكرة، والصق كتلة النص التالية فيه:

   ```powershell
   Site,Group,PermissionLevels
   https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
   https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
   https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
   https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
   ```

   حيث يساوي *المستأجر* اسم المستأجر الخاص بك.

2. احفظ الملف على سطح المكتب ك **GroupsAndPermissions.csv**.

3. افتح مثيلا جديدا من المفكرة، والصق كتلة النص التالية فيه:

   ```powershell
   Group,LoginName,Site
   Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
   ```

   حيث يساوي *المستأجر* اسم المستأجر الخاص بك، واسم *المستخدم* يساوي اسم المستخدم لمستخدم موجود.

4. احفظ الملف على سطح المكتب ك **Users.csv**.

5. افتح مثيلا جديدا من المفكرة، والصق كتلة النص التالية فيه:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   حيث يساوي MyAlias اسم المستخدم للمستخدم الذي تم تسجيل دخوله حاليا.

6. احفظ الملف على سطح المكتب ك **UsersAndGroups.ps1**. هذا برنامج نصي بسيط Windows PowerShell.

أنت الآن جاهز لتشغيل البرنامج النصي UsersAndGroup.ps1 لإضافة مستخدمين ومجموعات إلى مجموعات مواقع مشتركة متعددة.

### <a name="run-usersandgroupsps1-script"></a>تشغيل البرنامج النصي UsersAndGroups.ps1

1. ارجع إلى SharePoint Online Management Shell.

2. في المطالبة Windows PowerShell، اكتب السطر التالي أو انسخه والصقه، ثم اضغط على مفتاح الإدخال Enter:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. في موجه التأكيد، اضغط **على Y**.

4. في المطالبة Windows PowerShell، اكتب ما يلي أو انسخه والصقه، واضغط على مفتاح الإدخال Enter:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   حيث *يساوي MyAlias* اسم المستخدم الخاص بك.

5. انتظر حتى تعود المطالبة قبل الانتقال. سترى أولا ظهور المجموعات عند إنشائها. بعد ذلك، سترى قائمة المجموعات مكررة عند إضافة المستخدمين.

## <a name="see-also"></a>راجع أيضًا

[الاتصال إلى SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[إدارة مجموعات مواقع SharePoint Online باستخدام PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
