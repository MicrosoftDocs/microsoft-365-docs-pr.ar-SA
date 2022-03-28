---
title: Hello World for Microsoft 365 Defender REST API
description: تعرف على كيفية إنشاء تطبيق واستخدام رمز مميز للوصول إلى واجهات Microsoft 365 Defender برمجة التطبيقات
keywords: التطبيق، الرمز المميز، الوصول، aad، التطبيق، تسجيل التطبيق، powershell، البرنامج النصي، المسؤول العام، إذن، microsoft 365 defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 3a8696a14b85374d4bcb0a8704c14b82fdd845b5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754607"
---
# <a name="hello-world-for-microsoft-365-defender-rest-api"></a>Hello World for Microsoft 365 Defender REST API

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

## <a name="get-incidents-using-a-simple-powershell-script"></a>الحصول على أحداث باستخدام برنامج PowerShell نصي بسيط

من المفترض أن يستغرق إكمال هذا المشروع من 5 إلى 10 دقائق. يتضمن تقدير الوقت هذا تسجيل التطبيق وتطبيق التعليمات البرمجية من البرنامج النصي النموذجي ل PowerShell.

### <a name="register-an-app-in-azure-active-directory"></a>تسجيل تطبيق في Azure Active Directory

1. سجل الدخول إلى [Azure](https://portal.azure.com) كمستخدم باستخدام **دور المسؤول** العام.

2. انتقل إلى **تسجيلات Azure Active DirectoryApp** >  >  **التسجيل الجديد**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="مقطع التسجيل الجديد في مدخل Microsoft 365 Defender" lightbox="../../media/atp-azure-new-app2.png":::

3. في نموذج التسجيل، اختر اسما للتطبيق، ثم حدد **تسجيل**. إن تحديد URI إعادة توجيه اختياري. لن تحتاج إلى مثال لإكمال هذا المثال.

4. في صفحة التطبيق الخاصة بك، حدد أذونات **APIAdd** >  **permissionAPIs** >  **تستخدم >**، وا اكتب الحماية من المخاطر من **Microsoft**، وحدد **الحماية من المخاطر من Microsoft**. يمكن لتطبيقك الآن الوصول إلى Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* هو اسم سابق Microsoft 365 Defender، ولن يظهر في القائمة الأصلية. ستحتاج إلى بدء كتابة اسمه في مربع النص لكي يظهر.
   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="مقطع استخدام واجهات برمجة التطبيقات في مدخل Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - اختر **أذونات** **التطبيقIncident.Read.All** >  وحدد **إضافة أذونات**.

     :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="جزء أذونات التطبيق في مدخل Microsoft 365 Defender" lightbox="../../media/request-api-permissions.PNG":::

5. حدد **منح موافقة المسؤول**. في كل مرة تضيف فيها إذنا، يجب تحديد **منح موافقة** المسؤول لكي يتم هذا الأمر.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="القسم &quot;منح موافقة المسؤول&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/grant-consent.PNG":::

6. أضف سرية إلى التطبيق. حدد **الشهادات &،** وأضف وصفا للسر، ثم حدد **إضافة**.

    > [!TIP]
    > بعد تحديد **إضافة،** حدد **نسخ القيمة السرية التي تم إنشاؤها**. لن تتمكن من استرداد القيمة السرية بعد المغادرة.

    :::image type="content" source="../../media/webapp-create-key2.png" alt-text="القسم &quot;إضافة سري&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/webapp-create-key2.png":::
    

7. سجل "رقم التطبيق" وم ID المستأجر الخاص بك في مكان آمن. يتم سردها ضمن **نظرة عامة** على صفحة التطبيق.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="القسم &quot;نظرة عامة&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

### <a name="get-a-token-using-the-app-and-use-the-token-to-access-the-api"></a>الحصول على رمز مميز باستخدام التطبيق واستخدام الرمز المميز للوصول إلى API

لمزيد من المعلومات حول رموز Azure Active Directory المميزة، راجع البرنامج التعليمي [Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> على الرغم من أن المثال في تطبيق العرض التوضيحي هذا يشجعك على لصق القيمة السرية لأغراض الاختبار، إلا أنه لا يجب  عليك أبدا إدخال أسرار الترميز الثابت في تطبيق قيد الإنتاج. يمكن أن تستخدم جهة خارجية سرك للوصول إلى الموارد. يمكنك المساعدة في الحفاظ على أمان أسرار تطبيقك باستخدام [Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). للحصول على مثال عملي حول كيفية حماية تطبيقك، راجع إدارة أسرار تطبيقات الخادم [باستخدام Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

1. انسخ البرنامج النصي أدناه واللصق في محرر النص المفضل لديك. احفظ **Get-Token.ps1**. يمكنك أيضا تشغيل التعليمة البرمجية كما هي في PowerShell ISE، ولكن يجب حفظها، لأننا نحتاج إلى تشغيلها مرة أخرى عند استخدام البرنامج النصي لإحضار الأحداث في المقطع التالي.

    سيولد هذا البرنامج النصي رمزا مميزا ويحفظه في مجلد العمل تحت الاسم *،Latest-token.txt*.

    ```PowerShell
    # This script gets the app context token and saves it to a file named "Latest-token.txt" under the current directory.
    # Paste in your tenant ID, client ID and app secret (App key).

    $tenantId = '' # Paste your directory (tenant) ID here
    $clientId = '' # Paste your application (client) ID here
    $appSecret = '' # # Paste your own app secret here to test, then store it in a safe place!

    $resourceAppIdUri = 'https://api.security.microsoft.com'
    $oAuthUri = "https://login.windows.net/$tenantId/oauth2/token"
    $authBody = [Ordered] @{
      resource = $resourceAppIdUri
      client_id = $clientId
      client_secret = $appSecret
      grant_type = 'client_credentials'
    }
    $authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
    $token = $authResponse.access_token
    Out-File -FilePath "./Latest-token.txt" -InputObject $token
    return $token
    ```

#### <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

1. انسخ الرمز المميز الذي تلقيته في [JWT](https://jwt.ms) والصقه لفك ترميزه.
1. *يرمز JWT* إلى *رمز JSON Web Token*. سيحتوي الرمز المميز الذي تم فك تشفيره على عدد من العناصر أو المطالبات التي تم تنسيقها بتنسيق JSON. تأكد من أن *ادعاء الأدوار* ضمن الرمز المميز الذي تم فك فك تشفيره يحتوي على الأذونات المطلوبة.

    في الصورة التالية، يمكنك رؤية رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق، باستخدام ```Incidents.Read.All```، ```Incidents.ReadWrite.All```و، وأذونات ```AdvancedHunting.Read.All``` :

    :::image type="content" source="../../media/api-jwt-ms.png" alt-text="مقطع الرمز المميز المفكك في مدخل Microsoft 365 Defender" lightbox="../../media/api-jwt-ms.png":::

### <a name="get-a-list-of-recent-incidents"></a>الحصول على قائمة بالحوادث الأخيرة

سيستخدم البرنامج النصي **أدناه** Get-Token.ps1للوصول إلى API. بعد ذلك، يسترد قائمة بالحوادث التي تم تحديثها آخر مرة خلال ال 48 ساعة الماضية، ويحفظ القائمة كملف JSON.

> [!IMPORTANT]
> احفظ هذا البرنامج النصي في المجلد نفسه **الذي حفظته** Get-Token.ps1.

```PowerShell
# This script returns incidents last updated within the past 48 hours.

$token = ./Get-Token.ps1

# Get incidents from the past 48 hours.
# The script may appear to fail if you don't have any incidents in that time frame.
$dateTime = (Get-Date).ToUniversalTime().AddHours(-48).ToString("o")

# This URL contains the type of query and the time filter we created above.
# Note that `$filter` does not refer to a local variable in our script --
# it's actually an OData operator and part of the API's syntax.
$url = "https://api.security.microsoft.com/api/incidents?$filter=lastUpdateTime+ge+$dateTime"

# Set the webrequest headers
$headers = @{
    'Content-Type' = 'application/json'
    'Accept' = 'application/json'
    'Authorization' = "Bearer $token"
}

# Send the request and get the results.
$response = Invoke-WebRequest -Method Get -Uri $url -Headers $headers -ErrorAction Stop

# Extract the incidents from the results.
$incidents =  ($response | ConvertFrom-Json).value | ConvertTo-Json -Depth 99

# Get a string containing the execution time. We concatenate that string to the name 
# of the output file to avoid overwriting the file on consecutive runs of the script.
$dateTimeForFileName = Get-Date -Format o | foreach {$_ -replace ":", "."}

# Save the result as json
$outputJsonPath = "./Latest Incidents $dateTimeForFileName.json"

Out-File -FilePath $outputJsonPath -InputObject $incidents
```

لقد انتهيت جميعا! لقد نجحت في:

- إنشاء تطبيق وتسجيله.
- تم منح الإذن لهذا التطبيق لقراءة التنبيهات.
- متصل ب API.
- استخدم برنامج PowerShell النصي لإرجاع الأحداث التي تم تحديثها خلال ال 48 ساعة الماضية.

## <a name="related-articles"></a>المقالات ذات الصلة

- [Microsoft 365 Defender نظرة عامة على واجهات برمجة التطبيقات](api-overview.md)
- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم](api-create-app-web.md)
- [إنشاء تطبيق للوصول Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم](api-create-app-user-context.md)
- [إنشاء تطبيق مع وصول شريك متعدد المستأجرين إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-partner-access.md)
- [إدارة أسرار تطبيقات الخادم باستخدام مخزن مفاتيح Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [OAuth 2.0 تخويل تسجيل دخول المستخدم والوصول إلى واجهة برمجة المستخدم](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)