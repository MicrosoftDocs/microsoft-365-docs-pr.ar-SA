---
title: مرحبًا بالعالم ل API Microsoft Defender لنقطة النهاية API
ms.reviewer: ''
description: قم بإنشاء مكالمة API نمط 'Hello world' إلى Microsoft Defender لنقطة النهاية API.
keywords: apis، apis المعتمدة، البحث المتقدم، الاستعلام، microsoft defender atp، microsoft defender لنقطة النهاية
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
ms.openlocfilehash: bd8f48e8396225fc03441cfc7c8ed69fa3f378bb
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475598"
---
# <a name="microsoft-defender-for-endpoint-api---hello-world"></a>Microsoft Defender لنقطة النهاية API - مرحبًا بالعالم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)


>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="get-alerts-using-a-simple-powershell-script"></a>الحصول على تنبيهات باستخدام برنامج PowerShell نصي بسيط

### <a name="how-long-it-takes-to-go-through-this-example"></a>ما المدة التي يستغرقها الانتقال إلى هذا المثال؟

يستغرق الأمر 5 دقائق فقط من خلال خطوتين:

- تسجيل التطبيق
- استخدام الأمثلة: يتطلب فقط نسخ/لصق برنامج نصي PowerShell قصير

### <a name="do-i-need-a-permission-to-connect"></a>هل أحتاج إلى إذن للاتصال؟

بالنسبة إلى مرحلة تسجيل التطبيق، يجب أن يكون مسؤول عمومي  في مستأجر Azure Active Directory (Azure AD).

### <a name="step-1---create-an-app-in-azure-active-directory"></a>الخطوة 1 - إنشاء تطبيق في Azure Active Directory

1. سجل دخولك إلى [Azure](https://portal.azure.com) **باستخدام** مسؤول عمومي المستخدم.

2. انتقل إلى **تسجيلات تطبيق Azure Active Directory** \>  \> **تسجيل جديد**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="الخيار &quot;تسجيلات التطبيق&quot; ضمن الجزء &quot;إدارة&quot; في مدخل Azure Active Directory"  lightbox="images/atp-azure-new-app2.png":::

3. في نموذج التسجيل، اختر اسما للتطبيق ثم انقر فوق **تسجيل**.

4. السماح لتطبيقك بالوصول إلى Defender لنقطة النهاية وتعيين **إذن "قراءة كل** التنبيهات":

   - على صفحة التطبيق، انقر فوق أذونات **API** \>  \> إضافة واجهات برمجة **تطبيقات الأذونات** التي تستخدمها > **نوع WindowsDefenderATP** وانقر فوق **WindowsDefenderATP**.

     > [!NOTE]
     > لا يظهر WindowsDefenderATP في القائمة الأصلية. ستحتاج إلى بدء كتابة اسمه في مربع النص لكي يظهر.

     :::image type="content" source="images/add-permission.png" alt-text="الخيار &quot;أذونات API&quot; ضمن الجزء &quot;إدارة&quot; في مدخل Azure Active Directory" lightbox="images/add-permission.png":::

   - اختر **أذونات التطبيق** \> **Alert.Read.all >** انقر فوق **إضافة أذونات**.

     :::image type="content" source="images/application-permissions.png" alt-text="نوع الإذن و جزء الإعدادات في صفحة طلب أذونات API" lightbox="images/application-permissions.png":::

     > [!IMPORTANT]
     > يجب تحديد الأذونات ذات الصلة. "قراءة كل التنبيهات" هو مثال فقط!

     على سبيل المثال:

     - لتشغيل [الاستعلامات المتقدمة،](run-advanced-query-api.md) حدد إذن 'تشغيل الاستعلامات المتقدمة'.
     - [لعزل جهاز،](isolate-machine.md) حدد إذن 'عزل الجهاز'.
     - لتحديد الإذن الذي تحتاج إليه، يرجى الاطلاع على قسم الأذونات في API التي تريد الاتصال بها.

5. انقر **فوق منح الموافقة**.

   > [!NOTE]
   > في كل مرة تضيف فيها إذنا، يجب النقر فوق **منح الموافقة** على الإذن الجديد لكي يتم التنفيذ.

   :::image type="content" source="images/grant-consent.png" alt-text="خيار الموافقة على منح الإذن في مدخل Azure Active Directory" lightbox="images/grant-consent.png":::

6. أضف سرية إلى التطبيق.

    انقر **فوق &، وأضف** وصفا للسر، ثم انقر فوق **إضافة**.

    > [!IMPORTANT]
    > بعد النقر فوق إضافة، **انسخ القيمة السرية التي تم إنشاؤها**. لن تتمكن من استرداده بعد المغادرة!

    :::image type="content" source="images/webapp-create-key2.png" alt-text="عنصر القائمة & &quot;&&quot; في الجزء &quot;إدارة&quot; في مدخل Azure Active Directory" lightbox="images/webapp-create-key2.png":::

7. اكتب "معرّف التطبيق" وم ID المستأجر.

   على صفحة التطبيق، انتقل إلى **نظرة عامة** ونسخ ما يلي:

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="جزء تفاصيل التطبيق ضمن عنصر القائمة نظرة عامة في مدخل Azure Active Directory" lightbox="images/app-and-tenant-ids.png":::

تم! لقد سجلت تطبيقا بنجاح!

### <a name="step-2---get-a-token-using-the-app-and-use-this-token-to-access-the-api"></a>الخطوة 2 - الحصول على رمز مميز باستخدام التطبيق واستخدام هذا الرمز المميز للوصول إلى API.

- انسخ البرنامج النصي أدناه إلى PowerShell ISE أو إلى محرر نص، واحفظه **Get-Token.ps1.**
- يؤدي تشغيل هذا البرنامج النصي إلى إنشاء رمز مميز وحفظه في مجلد العمل تحت **اسم** Latest-token.txt.

   ```powershell
   # That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
   # Paste below your Tenant ID, App ID and App Secret (App key).

   $tenantId = '' ### Paste your tenant ID here
   $appId = '' ### Paste your Application ID here
   $appSecret = '' ### Paste your Application secret here

   $resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
   $oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
   $authBody = [Ordered] @{
       resource = "$resourceAppIdUri"
       client_id = "$appId"
       client_secret = "$appSecret"
       grant_type = 'client_credentials'
   }
   $authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
   $token = $authResponse.access_token
   Out-File -FilePath "./Latest-token.txt" -InputObject $token
   return $token
   ```

- التحقق من الصحة:
  - تشغيل البرنامج النصي.
  - في المستعرض، انتقل إلى: <https://jwt.ms/>.
  - انسخ الرمز المميز (محتوى ملف Latest-token.txt).
  - اللصق في المربع العلوي.
  - ابحث عن مقطع "الأدوار". ابحث عن _الدور Alert.Read.All_ .

  :::image type="content" source="images/api-jwt-ms.png" alt-text="جزء الرمز المميز المفكك jwt.ms" lightbox="images/api-jwt-ms.png":::

### <a name="lets-get-the-alerts"></a>يتيح الحصول على التنبيهات!

- سيستخدم البرنامج النصي **أدناه** Get-Token.ps1للوصول إلى API وسيحصل على تنبيهات ال 48 ساعة الماضية.
- احفظ هذا البرنامج النصي في المجلد نفسه الذي حفظت فيه البرنامج النصي **Get-Token.ps1**.
- ينشئ البرنامج النصي ملفين (json و csv) مع البيانات الموجودة في المجلد نفسه الذي يحتوي على البرامج النصية.

  ```powershell
  # Returns Alerts created in the past 48 hours.

  $token = ./Get-Token.ps1       #run the script Get-Token.ps1  - make sure you are running this script from the same folder of Get-Token.ps1

  # Get Alert from the last 48 hours. Make sure you have alerts in that time frame.
  $dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

  # The URL contains the type of query and the time filter we create above
  # Read more about other query options and filters at   Https://TBD- add the documentation link
  $url = "https://api.securitycenter.microsoft.com/api/alerts?`$filter=alertCreationTime ge $dateTime"

  # Set the WebRequest headers
  $headers = @{
      'Content-Type' = 'application/json'
      Accept = 'application/json'
      Authorization = "Bearer $token"
  }

  # Send the webrequest and get the results.
  $response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

  # Extract the alerts from the results.
  $alerts =  ($response | ConvertFrom-Json).value | ConvertTo-Json

  # Get string with the execution time. We concatenate that string to the output file to avoid overwrite the file
  $dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

  # Save the result as json and as csv
  $outputJsonPath = "./Latest Alerts $dateTimeForFileName.json"
  $outputCsvPath = "./Latest Alerts $dateTimeForFileName.csv"

  Out-File -FilePath $outputJsonPath -InputObject $alerts
  ($alerts | ConvertFrom-Json) | Export-CSV $outputCsvPath -NoTypeInformation
  ```

لقد انتهيت جميعا! لقد نجحت للتو:

- تم إنشاؤه وتسجيله وتطبيقه
- تم منح الإذن لهذا التطبيق لقراءة التنبيهات
- توصيل API
- استخدام برنامج PowerShell النصي لإرجاع التنبيهات التي تم إنشاؤها في ال 48 ساعة الماضية

## <a name="related-topic"></a>موضوع ذو صلة

- [Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات](exposed-apis-list.md)
- [الوصول Microsoft Defender لنقطة النهاية مع سياق التطبيق](exposed-apis-create-app-webapp.md)
- [الوصول Microsoft Defender لنقطة النهاية مع سياق المستخدم](exposed-apis-create-app-nativeapp.md)
