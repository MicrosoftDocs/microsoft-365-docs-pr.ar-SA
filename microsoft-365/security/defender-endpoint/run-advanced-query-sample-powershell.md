---
title: التتبع المتقدم مع أساسيات واجهة برمجة تطبيقات PowerShell
ms.reviewer: ''
description: تعرف على أساسيات الاستعلام عن واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية، باستخدام PowerShell.
keywords: واجهة برمجة التطبيقات، واجهة برمجة التطبيقات المدعومة، التتبع المتقدم، الاستعلام
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
ms.openlocfilehash: fc0cae0ff8c45f4c32213130773e3c118d779ed6
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243129"
---
# <a name="advanced-hunting-using-powershell"></a>الصيد المتقدم باستخدام PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تشغيل الاستعلامات المتقدمة باستخدام PowerShell، راجع [Advanced Hunting API](run-advanced-query-api.md).

في هذا القسم، نشارك نماذج PowerShell لاسترداد رمز مميز واستخدامه لتشغيل استعلام.

## <a name="before-you-begin"></a>قبل البدء
تحتاج أولا إلى [إنشاء تطبيق](apis-intro.md).

## <a name="preparation-instructions"></a>إرشادات التحضير

- افتح نافذة PowerShell.

- إذا لم يسمح لك نهجك بتشغيل أوامر PowerShell، يمكنك تشغيل الأمر التالي:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

لمزيد من المعلومات، راجع [وثائق PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>الحصول على الرمز المميز

- قم بتشغيل ما يلي:

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
- $tenantId: معرف المستأجر الذي تريد تشغيل الاستعلام بالنيابة عنه (أي، سيتم تشغيل الاستعلام على بيانات هذا المستأجر)
- $appId: معرف تطبيق Azure AD (يجب أن يكون للتطبيق إذن "تشغيل الاستعلامات المتقدمة" إلى Defender لنقطة النهاية)
- $appSecret: سر تطبيق Azure AD

## <a name="run-query"></a>تشغيل الاستعلام

تشغيل الاستعلام التالي:

```powershell
$query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

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

- $results تحتوي على نتائج الاستعلام
- يحتوي $schema على مخطط نتائج الاستعلام

### <a name="complex-queries"></a>الاستعلامات المعقدة

إذا كنت تريد تشغيل استعلامات معقدة (أو استعلامات متعددة الأسطر)، فاحفظ الاستعلام في ملف، وبدلا من السطر الأول في النموذج أعلاه، قم بتشغيل الأمر التالي:

```powershell
$query = [IO.File]::ReadAllText("C:\myQuery.txt"); # Replace with the path to your file
```

## <a name="work-with-query-results"></a>استخدام نتائج الاستعلام

يمكنك الآن استخدام نتائج الاستعلام.

لإخراج نتائج الاستعلام بتنسيق CSV في file1.csv الملف، قم بتشغيل الأمر التالي:

```powershell
$results | ConvertTo-Csv -NoTypeInformation | Set-Content file1.csv
```

لإخراج نتائج الاستعلام بتنسيق JSON في file1.json، قم بتشغيل الأمر التالي:

```powershell
$results | ConvertTo-Json | Set-Content file1.json
```


## <a name="related-topic"></a>الموضوع ذو الصلة
- [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [التتبع المتقدم لواجهات برمجة التطبيقات](run-advanced-query-api.md)
- ["الصيد المتقدم" باستخدام Python](run-advanced-query-sample-python.md)
