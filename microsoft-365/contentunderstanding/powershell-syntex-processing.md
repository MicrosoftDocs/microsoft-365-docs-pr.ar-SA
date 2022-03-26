---
title: استخدام PowerShell لطلب المعالجة بواسطة نموذج فهم المستندات
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
description: تعرف على كيفية استخدام PowerShell لطلب المعالجة بواسطة نموذج SharePoint Syntex المستند.
ms.openlocfilehash: 8f66a0cc5e59ad2ccb6b92d98cfaee8ce84470f2
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63570930"
---
# <a name="use-powershell-to-request-processing-by-a-document-understanding-model"></a>استخدام PowerShell لطلب المعالجة بواسطة نموذج فهم المستندات

> [!IMPORTANT]
> إن SharePoint Syntex PowerShell cmdlets وجميع مكونات PnP الأخرى هي أدوات مفتوحة المصدر يدعمها مجتمع نشط يوفر الدعم لها. لا يوجد دعم SLA لأداة المصدر المفتوح من قنوات دعم Microsoft الرسمية.

سوف تقوم نماذج فهم المستندات لمعالجة الملفات التي تم تحميلها حديثا إلى مكتبة. من الممكن أيضا طلب المعالجة يدويا في واجهة المستخدم. ومع ذلك، قد تكون هناك سيناريوهات حيث يكون تشغيل المعالجة من خلال PowerShell أكثر فعالية.

## <a name="request-processing-of-all-items-that-have-not-been-previously-classified"></a>طلب معالجة جميع العناصر التي لم يتم تصنيفها مسبقا

يمكنك طلب المعالجة لكل العناصر الموجودة في المكتبة التي لم يتم تصنيفها مسبقا باستخدام هذا الأمر:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents"
```

بالنسبة ل المعالجة ذات الأولوية المنخفضة، قد تفكر أيضا في استخدام المعلمة -OffPeak، التي سيتم وضع الملفات في قائمة الانتظار لمجراها خارج ساعات العمل حيث يوجد المستأجر. راجع [Request-PnPSyntexClassifyAndExtract للحصول](https://pnp.github.io/powershell/cmdlets/Request-PnPSyntexClassifyAndExtract.html) على مزيد من التفاصيل.

## <a name="request-processing-of-all-items-in-a-library"></a>طلب معالجة كل العناصر في مكتبة

يمكنك طلب معالجة جميع الملفات في المكتبة، حتى لو تم تصنيفها مسبقا. قد يكون هذا الأمر مفيدا إذا قمت بتحديث نموذج أو إضافة نموذج آخر إلى المكتبة.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -List "Documents" -Force
```

> [!NOTE]
> يؤدي استخدام الخيار -Force مع أكثر من 5000 عنصر إلى تمكين إيقاف تشغيل معالجة الذروة تلقائيا.

## <a name="request-processing-of-all-items-based-on-a-property"></a>طلب معالجة جميع العناصر استنادا إلى خاصية

إذا كنت تريد حصر المعالجة في مجموعة فرعية معينة من العناصر في مكتبة، يمكنك استخدام برنامج نصي لتحديد مجموعة معينة من الملفات. في المثال التالي، يسمح البرنامج النصي بتحديد حقل وقيمة حقل للتصفية حسبها. يمكن إكمال الاستعلامات الأكثر تعقيدا باستخدام [Get-PnPListItem](https://pnp.github.io/powershell/cmdlets/Get-PnPListItem.html).

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"
$list = Get-PnPList -Identity "Documents"
# Set the field name to filter items by
$fieldName = "Vendor"
# Set the field value to filter by
$fieldFilter = "Fabrikam"

$listItems = (Get-PnPListItem -List $list -fields $fieldName).fieldValues
$targetItems = $listItems | Where-Object -Property Provider -EQ -Value $fieldFilter

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
foreach ($listItem in $targetItems) {
    Request-PnPSyntexClassifyAndExtract -FileUrl $listItem.FileRef -Batch $classifyBatch
}

# Execute batch
Invoke-PnPBatch -Batch $batch
```

## <a name="request-processing-of-specific-files"></a>طلب معالجة ملفات معينة

يمكن أيضا طلب المعالجة لملفات معينة.

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx"
```

يدعم الملف حسب نموذج الملف أيضا الدفع على دفعات:

```PowerShell
#Note: you're connecting here to the site that holds the document library you want to process
Connect-PnPOnline -Url "https://contoso.sharepoint.com/sites/finance"

# Create a new batch
$batch = New-PnPBatch

# Add files to classify to the batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/contoso contract.docx" -Batch $batch
Request-PnPSyntexClassifyAndExtract -FileUrl "/sites/finance/documents/relecloud contract.docx" -Batch $batch

# Execute batch
Invoke-PnPBatch -Batch $batch
```
