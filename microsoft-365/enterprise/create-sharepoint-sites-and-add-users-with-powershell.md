---
title: إنشاء SharePoint عبر الإنترنت وإضافة مستخدمين باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: hub-page
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
description: 'ملخص: استخدم PowerShell لإنشاء مواقع SharePoint عبر الإنترنت ثم أضف المستخدمين والمجموعات إلى تلك المواقع.'
ms.openlocfilehash: 76411621c0c313a31e4c92417b4472d6fd34ddac
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569350"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>إنشاء SharePoint عبر الإنترنت وإضافة مستخدمين باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

عند استخدام PowerShell Microsoft 365 لإنشاء مواقع SharePoint عبر الإنترنت وإضافة مستخدمين، يمكنك تنفيذ المهام بسرعة وتكرار أسرع بكثير مما يمكنك في مركز مسؤولي Microsoft 365. يمكنك أيضا تنفيذ مهام لا يمكن تنفيذها في مركز مسؤولي Microsoft 365.

## <a name="connect-to-sharepoint-online"></a>الاتصال إلى SharePoint Online

تتطلب الإجراءات في هذا الموضوع الاتصال ب SharePoint Online. للحصول على الإرشادات، [راجع الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>الخطوة 1: إنشاء مجموعات مواقع موقعية جديدة باستخدام PowerShell

أنشئ مواقع متعددة باستخدام PowerShell وملف .csv تقوم بإنشاءه باستخدام التعليمات البرمجية المتوفرة والمثال المفكرة. بالنسبة لهذا الإجراء، سيتم استبدال معلومات العنصر النائب المعروضة بين قوسين بمعلومات خاصة بالموقع والمستأجر. تسمح لك هذه العملية بإنشاء ملف واحد وتشغيل أمر PowerShell واحد يستخدم هذا الملف. يجعل هذا الإجراءات التي تم اتخاذها قابلة للتكرار والمحمولة على حد سواء ويزيل العديد من الأخطاء، إن لم يكن كلها، التي يمكن أن تأتي من كتابة أوامر طويلة في SharePoint Online Management Shell. يوجد جزءان لهذا الإجراء. أولا، ستنشئ ملف .csv، ثم .csv الملف باستخدام PowerShell، الذي سيستخدم محتوياته لإنشاء المواقع.

يستورد PowerShell cmdlet ملف .csv ويرسله إلى حلقة داخل الأقواس المقوسة التي تقرأ السطر الأول من الملف كرقام أعمدة. يتم بعد ذلك تكرير الأمر cmdlet في PowerShell عبر السجلات المتبقية، وينشئ مجموعة مواقع ويب جديدة لكل سجل، ويعين خصائص مجموعة المواقع الموقعة وفقا لر رؤوس الأعمدة.

### <a name="create-a-csv-file"></a>إنشاء ملف .csv

> [!NOTE]
> تعمل معلمة الحصة النسبية للموارد على المواقع الكلاسيكية فقط. إذا كنت تستخدم هذه المعلمة على موقع حديث، فقد تتلقى رسالة تحذير بأنه تم إهمالها.

1. افتح المفكرة ولصق كتلة النص التالية فيها:

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   حيث *المستأجر* هو اسم المستأجر، ومالك هو اسم  المستخدم للمستخدم على المستأجر الذي تريد منحه دور مسؤول مجموعة المواقع الرئيسية.

   (يمكنك الضغط على Ctrl+H عند استخدام المفكرة للاستبدال المجمع بشكل أسرع.)

2. احفظ الملف على سطح **المكتبSiteCollections.csv.**

> [!TIP]
> قبل استخدام هذا الملف أو أي ملف نصي .csv آخر أو Windows PowerShell، من الجيد التأكد من عدم وجود أحرف دفينة أو غير مطبوعة. افتح الملف في Word، وفي الشريط، انقر فوق أيقونة الفقرة لإظهار الأحرف غير المطبوعة. يجب ألا تكون هناك أحرف دفينة غير مطبوعة. على سبيل المثال، يجب ألا تكون هناك أي علامات فقرات تتجاوز الأخيرة في نهاية الملف.

### <a name="run-the-windows-powershell-command"></a>تشغيل الأمر Windows PowerShell

1. في Windows PowerShell، اكتب الأمر التالي أو انسخه واللصق فيه، ثم اضغط على Enter:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   حيث *يساوي MyAlias* الاسم المستعار للمستخدم.

2. انتظر حتى تظهر Windows PowerShell المطالبة مرة أخرى. قد يستغرق الأمر دقيقة أو دقيقتين.

3. في Windows PowerShell، اكتب الأمر cmdlet التالي أو انسخه واللصق فيه، ثم اضغط على Enter:

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. لاحظ مجموعات المواقع الجديدة في القائمة. باستخدام ملف CSV المثال، سترى مجموعات المواقع التالية: **TeamSite01** و **Blog01** و **Project01** و **Community01**

هذا هو. لقد قمت بإنشاء مجموعات مواقع موقعية متعددة باستخدام .csv الذي أنشأته Windows PowerShell واحد. أنت الآن جاهز لإنشاء مستخدمين وتعيينهم إلى هذه المواقع.

## <a name="step-2-add-users-and-groups"></a>الخطوة 2: إضافة مستخدمين ومجموعات

الآن أنت ستعمل على إنشاء مستخدمين وإضافتهم إلى مجموعة مجموعة مواقع ويب. بعد ذلك، يمكنك استخدام ملف .csv لتحميل مجموعات ومستخدمين جدد مجمعين.

تستمر الإجراءات التالية في استخدام مواقع TeamSite01 و Blog01 و Project01 و Community01.

### <a name="create-csv-and-ps1-files"></a>إنشاء .csv .ps1 الملفات

1. افتح المفكرة ولصق كتلة النص التالية فيها:

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

   حيث *يساوي* المستأجر اسم المستأجر الخاص بك.

2. احفظ الملف على سطح **المكتبGroupsAndPermissions.csv.**

3. افتح مثيلا جديدا المفكرة ولصق كتلة النص التالية فيه:

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

   حيث *يساوي* المستأجر اسم المستأجر، واسم *المستخدم* يساوي اسم المستخدم لمستخدم موجود.

4. احفظ الملف على سطح **المكتبUsers.csv.**

5. افتح مثيلا جديدا المفكرة ولصق كتلة النص التالية فيه:

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   حيث يساوي MyAlias اسم المستخدم للمستخدم الذي تم تسجيل دخوله حاليا.

6. احفظ الملف على سطح **المكتبUsersAndGroups.ps1.** هذا برنامج نصي Windows PowerShell بسيط.

أنت الآن جاهز لتشغيل البرنامج النصي UsersAndGroup.ps1 لإضافة مستخدمين ومجموعات إلى مجموعات مواقع متعددة.

### <a name="run-usersandgroupsps1-script"></a>تشغيل UsersAndGroups.ps1 نصي

1. العودة إلى SharePoint Online Management Shell.

2. في Windows PowerShell، اكتب السطر التالي أو انسخه واللصق فيه، ثم اضغط على Enter:

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. عند طلب التأكيد، اضغط **على Y**.

4. في Windows PowerShell، اكتب ما يلي أو انسخه واللصق فيه، ثم اضغط على Enter:

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   حيث *يساوي MyAlias* اسم المستخدم الخاص بك.

5. انتظر حتى يتم إرجاع المطالبة قبل الانتقال. سترى أولا المجموعات تظهر عند إنشائها. بعد ذلك، سترى قائمة المجموعة مكررة عند إضافة مستخدمين.

## <a name="see-also"></a>راجع أيضًا

[الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[إدارة SharePoint على الإنترنت باستخدام PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
