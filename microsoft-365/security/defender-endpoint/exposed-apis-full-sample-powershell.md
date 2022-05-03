---
title: التتبع المتقدم باستخدام دليل واجهة برمجة تطبيقات PowerShell
ms.reviewer: ''
description: استخدم نماذج التعليمات البرمجية هذه، للاستعلام عن العديد من واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية.
keywords: واجهة برمجة التطبيقات، واجهة برمجة التطبيقات المدعومة، التتبع المتقدم، الاستعلام
search.product: eADQiWindows 10XVcnh
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
ms.date: 04/27/2022
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c23bf15a188527b2b4c24270fbc1312537da4154
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174888"
---
# <a name="microsoft-defender-for-endpoint-apis-using-powershell"></a>Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات باستخدام PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> لا يتم تضمين قدرات التتبع المتقدمة في Defender for Business. راجع [مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

سيناريو كامل باستخدام واجهات برمجة تطبيقات متعددة من Microsoft Defender لنقطة النهاية.

في هذا القسم، نشارك نماذج PowerShell إلى 
- استرداد رمز مميز 
- استخدم الرمز المميز لاسترداد أحدث التنبيهات في Microsoft Defender لنقطة النهاية
- لكل تنبيه، إذا كان التنبيه ذا أولوية متوسطة أو عالية ولا يزال قيد التقدم، فتحقق من عدد المرات التي اتصل فيها الجهاز ب URL مريب.

**المتطلبات الأساسية**: تحتاج أولا إلى [إنشاء تطبيق](apis-intro.md).

## <a name="preparation-instructions"></a>إرشادات التحضير

- افتح نافذة PowerShell.
- إذا لم يسمح لك نهجك بتشغيل أوامر PowerShell، يمكنك تشغيل الأمر أدناه:
  ```
  Set-ExecutionPolicy -ExecutionPolicy Bypass
  ```

لمزيد من المعلومات، راجع [وثائق PowerShell](/powershell/module/microsoft.powershell.security/set-executionpolicy)

## <a name="get-token"></a>الحصول على الرمز المميز

قم بتشغيل ما يلي:

- $tenantId: معرف المستأجر الذي تريد تشغيل الاستعلام بالنيابة عنه (على سبيل المثال، سيتم تشغيل الاستعلام على بيانات هذا المستأجر)
- $appId: معرف تطبيق AAD (دليل Azure النشط) (يجب أن يكون للتطبيق إذن "تشغيل الاستعلامات المتقدمة" إلى Defender لنقطة النهاية)
- $appSecret: سر تطبيق Azure AD

- $suspiciousUrl: عنوان URL


```
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://securitycenter.onmicrosoft.com/windowsatpservice'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token


#Get latest alert
$alertUrl = "https://api.securitycenter.microsoft.com/api/alerts?`$top=10"
$headers = @{ 
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken" 
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```


## <a name="see-also"></a>راجع أيضًا
- [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [التتبع المتقدم لواجهات برمجة التطبيقات](run-advanced-query-api.md)
- ["الصيد المتقدم" باستخدام Python](run-advanced-query-sample-python.md)
