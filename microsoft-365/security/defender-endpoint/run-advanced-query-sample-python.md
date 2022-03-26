---
title: دليل البحث المتقدم باستخدام Python API
ms.reviewer: ''
description: تعرف على كيفية الاستعلام باستخدام Microsoft Defender ل API لنقطة النهاية، باستخدام Python، مع الأمثلة.
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
ms.openlocfilehash: 73be2b3c2aa40bb88ac6ccff60eec5cb7f55338c
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573233"
---
# <a name="advanced-hunting-using-python"></a>"الصيد المتقدم" باستخدام "بايثون"

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تشغيل الاستعلامات المتقدمة باستخدام Python، راجع [API للصيد المتقدم](run-advanced-query-api.md).

في هذا القسم، نشارك نماذج Python لاسترداد رمز مميز واستخدامه لتشغيل استعلام.

> **المتطلبات** الأساسية: تحتاج أولا [إلى إنشاء تطبيق](apis-intro.md).

## <a name="get-token"></a>الحصول على رمز مميز

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

- tenantId: ID للمستأجر الذي تريد تشغيل الاستعلام بالنيابة عنه (أي، سيتم تشغيل الاستعلام على بيانات هذا المستأجر)
- appId: ID لتطبيق Azure AD (يجب أن يكون لدى التطبيق إذن 'تشغيل الاستعلامات المتقدمة' ل Microsoft Defender لنقطة النهاية)
- appSecret: سري لتطبيق Azure AD

## <a name="run-query"></a>تشغيل الاستعلام

 تشغيل الاستعلام التالي:

```python
query = 'RegistryEvents | limit 10' # Paste your own query here

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

إذا كنت تريد تشغيل استعلامات معقدة (أو استعلامات متعددة الخطوط)، فاحفظ الاستعلام في ملف، وبدلا من السطر الأول في العينة أعلاه، يمكنك تشغيل الأمر أدناه:

```python
queryFile = open("D:\\Temp\\myQuery.txt", 'r') # Replace with the path to your file
query = queryFile.read()
queryFile.close()
```

## <a name="work-with-query-results"></a>استخدام نتائج الاستعلام

يمكنك الآن استخدام نتائج الاستعلام.

للترتير عبر النتائج، يمكنك القيام ما يلي:

```python
for result in results:
    print(result) # Prints the whole result
    print(result["EventTime"]) # Prints only the property 'EventTime' from the result
```

إخراج نتائج الاستعلام بتنسيق CSV في ملف file1.csv ما يلي:

```python
import csv

outputFile = open("D:\\Temp\\file1.csv", 'w')
output = csv.writer(outputFile)
output.writerow(results[0].keys())
for result in results:
    output.writerow(result.values())

outputFile.close()
```

للحصول على نتائج الاستعلام بتنسيق JSON في file1.json، يمكنك القيام ما يلي:

```python
outputFile = open("D:\\Temp\\file1.json", 'w')
json.dump(results, outputFile)
outputFile.close()
```

## <a name="related-topic"></a>موضوع ذو صلة

- [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [API للصيد المتقدم](run-advanced-query-api.md)
- [الصيد المتقدم باستخدام PowerShell](run-advanced-query-sample-powershell.md)
