---
title: إدارة مجموعات مواقع SharePoint Online باستخدام PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: في هذه المقالة، ابحث عن إجراءات لاستخدام PowerShell Microsoft 365 لإدارة مجموعات المواقع SharePoint Online.
ms.openlocfilehash: 411ab477668b7956a63843d0b58b8d6d9bfc9059
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096425"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>إدارة مجموعات مواقع SharePoint Online باستخدام PowerShell

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

على الرغم من أنه يمكنك استخدام مركز مسؤولي Microsoft 365، يمكنك أيضا استخدام PowerShell Microsoft 365 لإدارة مجموعات المواقع SharePoint Online.

## <a name="before-you-begin"></a>قبل البدء

تتطلب منك الإجراءات الواردة في هذه المقالة الاتصال ب SharePoint Online. للحصول على الإرشادات، راجع [الاتصال إلى SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>عرض SharePoint Online باستخدام PowerShell ل Microsoft 365

يحتوي مركز إدارة SharePoint Online على بعض الأساليب السهلة الاستخدام لإدارة مجموعات المواقع. على سبيل المثال، افترض أنك تريد إلقاء نظرة على المجموعات وأعضاء المجموعة للموقع `https://litwareinc.sharepoint.com/sites/finance` . إليك ما يجب عليك فعله:

1. من مركز إدارة SharePoint، حدد <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**المواقع النشطة**</a>، ثم حدد عنوان URL للموقع.
2. في صفحة الموقع، حدد <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**الإعدادات**</a> (الموجود في الزاوية العلوية اليسرى من الصفحة)، ثم حدد **أذونات الموقع**.

ثم كرر العملية للموقع التالي الذي تريد النظر إليه.

للحصول على قائمة بالمجموعات باستخدام PowerShell Microsoft 365، يمكنك استخدام الأوامر التالية:

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

- انسخ الأوامر إلى المفكرة (أو محرر نص آخر)، وعدل قيمة متغير **$siteURL**، وحدد الأوامر، ثم الصقها في موجه أوامر SharePoint Online Management Shell. عند القيام بذلك، سيتوقف PowerShell عند مطالبة **>>** . اضغط على مفتاح الإدخال Enter لتنفيذ `foreach` الأمر.<br/>
- انسخ الأوامر إلى المفكرة (أو محرر نص آخر)، وقم بتعديل قيمة المتغير **$siteURL**، ثم احفظ هذا الملف النصي باسم وملحق .ps1 في مجلد مناسب. بعد ذلك، قم بتشغيل البرنامج النصي من موجه أوامر SharePoint Online Management Shell عن طريق تحديد مساره واسم الملف. فيما يلي مثال على الأمر:

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

في كلتا الحالتين، يجب أن ترى شيئا مشابها لهذا:

![SharePoint مجموعات المواقع عبر الإنترنت.](../media/SPO-site-groups.png)

هذه هي كافة المجموعات التي تم إنشاؤها للموقع `https://litwareinc.sharepoint.com/sites/finance`، وجميع المستخدمين المعينين لتلك المجموعات. أسماء المجموعات باللون الأصفر لمساعدتك على فصل أسماء المجموعات عن أعضاءها.

كمثال آخر، إليك مجموعة أوامر تسرد المجموعات وجميع عضويات المجموعة لكافة مواقع SharePoint Online.

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

[الاتصال إلى SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[إنشاء مواقع SharePoint Online وإضافة مستخدمين باستخدام PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[إدارة SharePoint عبر الإنترنت من المستخدمين والمجموعات باستخدام PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[إدارة Microsoft 365 باستخدام PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)
