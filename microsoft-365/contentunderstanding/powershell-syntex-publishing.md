---
title: نشر نماذج فهم المستندات باستخدام PowerShell
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: تعرف على كيفية نشر نموذج SharePoint Syntex مستند باستخدام PowerShell.
ms.openlocfilehash: 5169e5ea5839cd5c341baa2477fd82281f5e5d76
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63579208"
---
# <a name="publish-document-understanding-models-with-powershell"></a>نشر نماذج فهم المستندات باستخدام PowerShell

> [!IMPORTANT]
> إن SharePoint Syntex PowerShell cmdlets وجميع مكونات PnP الأخرى هي أدوات مفتوحة المصدر يدعمها مجتمع نشط يوفر الدعم لها. لا يوجد دعم SLA لأداة المصدر المفتوح من قنوات دعم Microsoft الرسمية.

SharePoint Syntex يتم عادة نشر النماذج في مكتبات المستندات عبر المستأجر. يمكن القيام بذلك باستخدام موقع مركز المحتويات، ولكن يمكن القيام بذلك أيضا باستخدام [PnP PowerShell](https://pnp.github.io/powershell/) كما هو موضح في هذه المقالة.

## <a name="listing-the-available-models-in-a-content-center"></a>سرد النماذج المتوفرة في مركز محتوى

للحصول على نظرة عامة حول النماذج المضافة إلى موقع مركز SharePoint Syntex الحالي، استخدم [cmdlet Get-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModel.html):

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModel
```

## <a name="apply-a-model-to-a-library"></a>تطبيق نموذج على مكتبة

لتطبيق نموذج على مكتبة، استخدم [cmdlet Publish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Publish-PnPSyntexModel.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Publish-PnPSyntexModel -Model "Contract Notice" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="understanding-where-a-model-is-used"></a>فهم مكان استخدام نموذج

بعد نشر نموذج للعديد من المكتبات، قد تحتاج إلى مراجعة قائمة المكتبات باستخدام النموذج. يمكن القيام بذلك باستخدام [الأمر cmdlet Get-PnPSyntexModelPublication](https://pnp.github.io/powershell/cmdlets/Get-PnPSyntexModelPublication.html) :

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"
Get-PnPSyntexModelPublication -Identity "Contract Notice"
```

## <a name="removing-a-model-from-a-library"></a>إزالة نموذج من مكتبة

تتبع إزالة نموذج من مكتبة النمط نفسه الذي يتم تطبيقه ويمكن القيام به باستخدام [الأمر cmdlet Unpublish-PnPSyntexModel](https://pnp.github.io/powershell/cmdlets/Unpublish-PnPSyntexModel.html) إما بشكل تفاعلي أو دفعة من إجراءات متعددة.

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourSite"
Unpublish-PnPSyntexModel -Model "Invoice model" -ListWebUrl "https://contoso.sharepoint.com/sites/finance" -List "Documents"
```

## <a name="apply-models-in-bulk"></a>تطبيق النماذج بشكل مجمع

إذا كنت تريد نشر نماذج متعددة لمكتبات متعددة، فنشئ ملف إدخال CSV سرد النماذج والمواقع الهدف:

```CSV
ModelName,TargetSiteUrl,TargetWebServerRelativeUrl,TargetLibraryServerRelativeUrl
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/shared%20documents
Contract Notice,https://contoso.sharepoint.com/sites/Site1,/sites/Site1,/sites/site1/other
Trade Confirmation,https://contoso.sharepoint.com/sites/Site2,/sites/Site2,/sites/site2/shared%20documents
```

يمكن عندئذ استخدام ملف CSV هذا كمدخل في برنامج نصي سينشر النماذج المدرجة إلى المكتبات المناسبة. في المثال التالي، يتم استخدام الدفع على دفعات لزيادة فعالية الطلبات.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourSite"
$targetsCSV = "./Publish-SyntexModelBulk.csv"

Connect-PnPOnline -url $contentCenterURL

$targetLibraries = Import-Csv -Path $targetsCSV

$batch = New-PnPBatch

foreach ($target in $targetLibraries) {
    Publish-PnPSyntexModel -Model $target.ModelName -TargetSiteUrl $target.TargetSiteUrl -TargetWebServerRelativeUrl $target.TargetWebServerRelativeUrl -TargetLibraryServerRelativeUrl $target.TargetLibraryServerRelativeUrl -Batch $batch
}

Invoke-PnPBatch -Batch $batch
```
