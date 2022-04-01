---
title: تصدير نماذج فهم المستندات واستيرادها باستخدام PowerShell
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
description: تعرف على كيفية تصدير نماذج فهم المستندات واستيرادها باستخدام PowerShell SharePoint Syntex.
ms.openlocfilehash: dc35d298ebd79752684c91ce944333277fcef621
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63579210"
---
# <a name="export-and-import-document-understanding-models-with-powershell"></a>تصدير نماذج فهم المستندات واستيرادها باستخدام PowerShell

> [!IMPORTANT]
> إن SharePoint Syntex PowerShell cmdlets وجميع مكونات PnP الأخرى هي أدوات مفتوحة المصدر يدعمها مجتمع نشط يوفر الدعم لها. لا يوجد دعم SLA لأداة المصدر المفتوح من قنوات دعم Microsoft الرسمية.

SharePoint Syntex تصدير النماذج كقالب PnP، مما يمكن إعادة الاستخدام عبر مراكز المحتوى أو المستأجرين.

## <a name="export-all-models-in-a-content-center"></a>تصدير كل النماذج في مركز محتوى

لتصدير كل النماذج في مركز محتوى إلى قالب PnP واحد، استخدم [cmdlets PnP PowerShell](https://pnp.github.io/powershell/) التالية:

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Handlers SyntexModels
```

## <a name="export-specific-models"></a>تصدير نماذج معينة

لتصدير نماذج معينة من مركز محتوى إلى قالب PnP، استخدم [cmdlets التالية ل PnP PowerShell](https://pnp.github.io/powershell/) :

```powershell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Get-PnPSiteTemplate -Out MyModels.pnp -Configuration .\extract.json
```

يحدد extract.json النماذج التي تريد تصديرها، مما يسمح بتحديد النموذج حسب الاسم أو المعرف والتكوين اختياريا حتى لا تستخرج بيانات التدريب.

### <a name="example---specify-model-by-name"></a>مثال - تحديد نموذج حسب الاسم

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "name": "Sample - benefits change notice.classifier"
            }
        ]
    }
}
```

### <a name="example---specify-model-by-id"></a>مثال - تحديد نموذج حسب الم ID

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/pnp/provisioning/202102/extract-configuration.schema.json",
    "persistAssetFiles": true,
    "handlers": [        
        "SyntexModels"
    ],
    "syntexModels": {
        "models": [
            {
                "id": 3,
                "excludeTrainingData": true
            }
        ]
    }
}
```

إذا لم تتضمن الخاصية "includeTrainingData"، فإن السلوك الافتراضي هو تضمين.

> [!NOTE]
> بيانات التدريب مطلوبة لكي يكون النموذج قابلا للتحرير عند استيراده إلى مركز محتوى الوجهة.

## <a name="import-models-to-a-content-center"></a>استيراد نماذج إلى مركز محتوى
يمكن استيراد نماذج فهم المستندات التي تم تصديرها إلى قوالب PnP إلى مركز محتوى على أي مستأجر. إذا تضمنت عملية التصدير بيانات التدريب، سيكون النموذج قابلا للتحرير بمجرد استيراده.

لاستيراد نموذج، استخدم الأوامر التالية:

```PowerShell
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/yourContentCenter"

Invoke-PnPSiteTemplate -Path .\sampleModel.pnp
```
