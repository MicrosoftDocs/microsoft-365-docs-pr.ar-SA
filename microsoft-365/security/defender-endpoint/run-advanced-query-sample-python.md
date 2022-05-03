---
title: التتبع المتقدم مع دليل واجهة برمجة تطبيقات Python
ms.reviewer: ''
description: تعرف على كيفية الاستعلام باستخدام واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية، باستخدام Python، مع أمثلة.
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
ms.openlocfilehash: 99fc848088725f7b28d91eebc78327c688059de8
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174779"
---
# <a name="advanced-hunting-using-python"></a>"الصيد المتقدم" باستخدام Python

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تشغيل الاستعلامات المتقدمة باستخدام Python، راجع [Advanced Hunting API](run-advanced-query-api.md).

في هذا القسم، نشارك نماذج Python لاسترداد رمز مميز واستخدامه لتشغيل استعلام.

> **المتطلبات الأساسية**: تحتاج أولا إلى [إنشاء تطبيق](apis-intro.md).

## <a name="get-token"></a>الحصول على الرمز المميز

- قم بتنفيذ الأوامر التالية:

```python
import json
import urllib.request
import urllib.parse

tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here

url = "https://login.microsoftonline.com/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.securitycenter.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : appId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

حيث

- tenantId: معرف المستأجر الذي تريد تشغيل الاستعلام بالنيابة عنه (أي، سيتم تشغيل الاستعلام على بيانات هذا المستأجر)
- appId: معرف تطبيق Azure AD (يجب أن يكون للتطبيق إذن "تشغيل الاستعلامات المتقدمة" Microsoft Defender لنقطة النهاية)
- appSecret: سر تطبيق Azure AD

## <a name="run-query"></a>تشغيل الاستعلام

 تشغيل الاستعلام التالي:

```python
query = 'DeviceRegistryEvents | limit 10' # Paste your own query here

url = "https://api.securitycenter.microsoft.com/api/advancedqueries/run"
headers = { 
    'Content-Type' : 'application/json',
    'Accept' : 'application/json',
    'Authorization' : "Bearer " + aadToken
}

data = json.dumps({ 'Query' : query }).encode("utf-8")

req = urllib.request.Request(url, data, headers)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
schema = jsonResponse["Schema"]
results = jsonResponse["Results"]
```

- يحتوي المخطط على مخطط نتائج الاستعلام
- تحتوي النتائج على نتائج الاستعلام

### <a name="complex-queries"></a>الاستعلامات المعقدة

إذا كنت تريد تشغيل استعلامات معقدة (أو استعلامات متعددة الأسطر)، فاحفظ الاستعلام في ملف، وبدلا من السطر الأول في النموذج أعلاه، قم بتشغيل الأمر أدناه:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>استخدام نتائج الاستعلام

يمكنك الآن استخدام نتائج الاستعلام.

للتكرار عبر النتائج، قم بما يلي:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

لإخراج نتائج الاستعلام بتنسيق CSV في ملف file1.csv قم بما يلي:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

لإخراج نتائج الاستعلام بتنسيق JSON في file1.json قم بما يلي:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>الموضوع ذو الصلة

- [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [التتبع المتقدم لواجهات برمجة التطبيقات](run-advanced-query-api.md)
- [الصيد المتقدم باستخدام PowerShell](run-advanced-query-sample-powershell.md)
