---
title: إدارة SharePoint على الإنترنت باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/17/2019
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
description: في هذه المقالة، ابحث عن إجراءات لاستخدام PowerShell Microsoft 365 لإدارة SharePoint مواقع عبر الإنترنت.
ms.openlocfilehash: 393771fec5346b10d76bbe5af471ca3dd42ebf80
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681205"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>إدارة SharePoint على الإنترنت باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

على الرغم من أنه يمكنك استخدام مركز مسؤولي Microsoft 365، يمكنك أيضا استخدام PowerShell Microsoft 365 لإدارة مجموعات مواقع SharePoint عبر الإنترنت.

## <a name="before-you-begin"></a>قبل البدء

تتطلب الإجراءات في هذه المقالة الاتصال ب SharePoint Online. للحصول على الإرشادات، [راجع الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>عرض SharePoint عبر الإنترنت باستخدام PowerShell Microsoft 365

يحتوي SharePoint إدارة الإنترنت على بعض الأساليب السهلة الاستخدام لإدارة مجموعات المواقع. على سبيل المثال، افترض أنك تريد النظر إلى المجموعات وأعضاء المجموعة للموقع `https://litwareinc.sharepoint.com/sites/finance` . إليك ما يجب فعله:

1. من مركز SharePoint، حدد <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**المواقع**</a> النشطة، ثم حدد عنوان URL للموقع.
2. في صفحة الموقع <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**، حدد الإعدادات**</a> (الموجود في الزاوية العلوية اليسرى من الصفحة)، ثم حدد **أذونات الموقع**.

ثم كرر العملية للموقع التالي الذي تريد النظر فيه.

للحصول على قائمة بالمجموعات التي تتضمن PowerShell Microsoft 365، يمكنك استخدام الأوامر التالية:

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

هناك طريقتان لتشغيل مجموعة الأوامر هذه في موجه الأوامر SharePoint Online Management Shell:

- انسخ الأوامر إلى المفكرة (أو محرر نص آخر)، ثم قم بتعديل قيمة متغير **$siteURL**، وحدد الأوامر، ثم اللصق في موجه الأوامر SharePoint Online Management Shell. عند القيام بذلك، سيتوقف PowerShell عند المطالبة **>>** . اضغط على Enter لتنفيذ `foreach` الأمر.<br/>
- انسخ الأوامر إلى المفكرة (أو محرر نص آخر)، ثم قم بتعديل قيمة متغير **$siteURL**، ثم احفظ هذا الملف النصي باسم وملحق .ps1 في مجلد مناسب. بعد ذلك، قم بتشغيل البرنامج النصي من SharePoint الأوامر Online Management Shell بتحديد المسار واسم الملف الخاص به. فيما يلي مثال على الأمر:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

في كلتا الحالتين، يجب أن ترى شيئا مماثلا لهذا:

![SharePoint مجموعات المواقع على الإنترنت.](../media/SPO-site-groups.png)

هذه هي كل المجموعات التي تم `https://litwareinc.sharepoint.com/sites/finance`إنشاؤها للموقع ، وجميع المستخدمين المعينين إلى هذه المجموعات. تظهر أسماء المجموعات باللون الأصفر لمساعدتك على فصل أسماء المجموعات عن أعضائها.

على سبيل المثال، فيما يلي مجموعة أوامر تسرد المجموعات، وجميع عضويات المجموعة، لكل مواقع SharePoint Online.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```

## <a name="see-also"></a>راجع أيضًا

[الاتصال SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[إنشاء SharePoint عبر الإنترنت وإضافة مستخدمين باستخدام PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[إدارة SharePoint والمجموعات عبر الإنترنت باستخدام PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء العمل باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)
