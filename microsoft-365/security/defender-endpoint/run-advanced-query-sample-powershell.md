---
title: البحث المتقدم باستخدام أساسيات API في PowerShell
ms.reviewer: ''
description: تعرف على أساسيات الاستعلام في Microsoft Defender ل API لنقطة النهاية، باستخدام PowerShell.
keywords: apis، apis المعتمدة، البحث المتقدم، الاستعلام
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 5de8778f1da44f8a9453616dc1e3b6f2af948397
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583047"
---
# <a name="advanced-hunting-using-powershell"></a>الصيد المتقدم باستخدام PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تشغيل الاستعلامات المتقدمة باستخدام PowerShell، راجع [API للصيد المتقدم](run-advanced-query-api.md).

في هذا القسم، نشارك نماذج PowerShell لاسترداد رمز مميز واستخدامه لتشغيل استعلام.

## <a name="before-you-begin"></a>قبل البدء
ستحتاج أولا [إلى إنشاء تطبيق](apis-intro.md).

## <a name="preparation-instructions"></a>إرشادات التحضير

- افتح نافذة PowerShell.

- إذا لم يسمح لك النهج بتشغيل أوامر PowerShell، يمكنك تشغيل الأمر التالي:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

لمزيد من المعلومات، راجع [وثائق PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>الحصول على رمز مميز

- تشغيل ما يلي:

```powershell
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$body = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$response = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $body -ErrorAction Stop
$aadToken = $response.access_token
```

حيث
- $tenantId: هوية المستأجر الذي تريد تشغيل الاستعلام بالنيابة عنه (أي، سيتم تشغيل الاستعلام على بيانات هذا المستأجر)
- $appId: هويات تطبيق Azure AD (يجب أن يكون لدى التطبيق إذن 'تشغيل الاستعلامات المتقدمة' ل Defender لنقطة النهاية)
- $appSecret: سرية تطبيق Azure AD

## <a name="run-query"></a>تشغيل الاستعلام

تشغيل الاستعلام التالي:

```powershell
$query = 'RegistryEvents | limit 10' # Paste your own query here

$url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$body = ConvertTo-Json -InputObject @{ 'Query' = $query }
$webResponse = Invoke-WebRequest -Method Post -Uri $url -Headers $headers -Body $body -ErrorAction Stop
$response =  $webResponse | ConvertFrom-Json
$results = $response.Results
$schema = $response.Schema
```

- $results على نتائج الاستعلام
- $schema يحتوي على مخطط نتائج الاستعلام

### <a name="complex-queries"></a>الاستعلامات المعقدة

إذا كنت تريد تشغيل استعلامات معقدة (أو استعلامات متعددة الخطوط)، فاحفظ الاستعلام في ملف، وبدلا من السطر الأول في العينة أعلاه، يمكنك تشغيل الأمر التالي:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>استخدام نتائج الاستعلام

يمكنك الآن استخدام نتائج الاستعلام.

إخراج نتائج الاستعلام بتنسيق CSV في ملف file1.csv، ادير الأمر التالي:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

إخراج نتائج الاستعلام بتنسيق JSON في file1.json، تشغيل الأمر التالي:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>موضوع ذو صلة
- [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [API للصيد المتقدم](run-advanced-query-api.md)
- ["الصيد المتقدم" باستخدام "بايثون"](run-advanced-query-sample-python.md)
