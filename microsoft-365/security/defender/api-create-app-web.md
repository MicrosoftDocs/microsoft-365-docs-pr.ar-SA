---
title: إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم
description: تعرف على كيفية إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم.
keywords: التطبيق، والوصول، وواجهة برمجة التطبيقات، وإنشاء
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
ms.openlocfilehash: 05450912d78e7da774de76e02dfe4d42a1569084
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102383"
---
# <a name="create-an-app-to-access-microsoft-365-defender-without-a-user"></a>إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Microsoft 365 Defender دون مستخدم محدد— على سبيل المثال، إذا كنت تقوم بإنشاء برنامج خفي أو خدمة خلفية.

إذا كنت بحاجة إلى وصول برمجي إلى Microsoft 365 Defender نيابة عن مستخدم واحد أو أكثر، فراجع [إنشاء تطبيق للوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender نيابة عن مستخدم](api-create-app-user-context.md) [وإنشاء تطبيق مع وصول الشريك إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-partner-access.md). إذا لم تكن متأكدا من نوع الوصول الذي تحتاجه، فراجع ["بدء الاستخدام](api-access.md)".

Microsoft 365 Defender يكشف الكثير من بياناته وإجراءاته من خلال مجموعة من واجهات برمجة التطبيقات البرمجية. تساعدك واجهات برمجة التطبيقات هذه على أتمتة مهام سير العمل والاستفادة من قدرات Microsoft 365 Defender. يتطلب الوصول إلى واجهة برمجة التطبيقات هذا مصادقة OAuth2.0. لمزيد من المعلومات، راجع [التعليمة البرمجية للتخويل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات هذه:

- إنشاء تطبيق Azure Active Directory (Azure AD).
- احصل على رمز مميز للوصول باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft 365 Defender.

تشرح هذه المقالة كيفية:

- إنشاء تطبيق Azure AD
- الحصول على رمز مميز للوصول إلى Microsoft 365 Defender
- التحقق من صحة الرمز المميز.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل الدخول إلى [Azure](https://portal.azure.com) كمستخدم باستخدام دور **المسؤول العام** .

2. انتقل إلى **تسجيلات** >  تطبيق **Azure Active Directory** > **الجديدة**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="علامة تبويب التسجيل الجديدة في مدخل Microsoft 365 Defender" lightbox="../../media/atp-azure-new-app2.png":::

3. في النموذج، اختر اسما للتطبيق الخاص بك، ثم حدد **"تسجيل**".

4. في صفحة التطبيق، حدد **API Permissions** > **Add permission** > **APIs التي تستخدمها مؤسستي** >، واكتب **Microsoft Threat Protection**، وحدد **Microsoft Threat Protection**. يمكن لتطبيقك الآن الوصول إلى Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* هو اسم سابق Microsoft 365 Defender، ولن يظهر في القائمة الأصلية. يجب أن تبدأ بكتابة اسمه في مربع النص لكي يظهر.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="علامة تبويب استخدام واجهات برمجة التطبيقات للمؤسسة في مدخل Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

5. حدد **أذونات التطبيق**. اختر الأذونات ذات الصلة للسيناريو (على سبيل المثال، **Incident.Read.All**)، ثم حدد **"إضافة أذونات**".

   :::image type="content" source="../../media/request-api-permissions.PNG" alt-text="جزء أذونات التطبيق في مدخل Microsoft 365 Defender" lightbox="../../media/request-api-permissions.PNG":::

    > [!NOTE]
    > تحتاج إلى تحديد الأذونات ذات الصلة للسيناريو الخاص بك. *قراءة جميع الحوادث* هي مجرد مثال. لتحديد الإذن الذي تحتاج إليه، يرجى مراجعة قسم **الأذونات** في واجهة برمجة التطبيقات التي تريد الاتصال بها.
    >
    > على سبيل المثال، [لتشغيل الاستعلامات المتقدمة](api-advanced-hunting.md)، حدد إذن "تشغيل الاستعلامات المتقدمة"؛ [لعزل جهاز](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine)، حدد إذن "عزل الجهاز".

6. حدد **منح موافقة المسؤول**. في كل مرة تضيف فيها إذنا، يجب تحديد **منح موافقة المسؤول** لكي يدخل حيز التنفيذ.

    :::image type="content" source="../../media/grant-consent.PNG" alt-text="الجزء المتعلق بمنح الموافقة في مدخل Microsoft 365 Defender" lightbox="../../media/grant-consent.PNG":::

7. لإضافة سر إلى التطبيق، حدد **"Certificates & secrets**"، وأضف وصفا إلى السر، ثم حدد **"Add**".

    > [!TIP]
    > بعد تحديد **"إضافة"**، حدد **نسخ قيمة البيانات السرية التي تم إنشاؤها**. لن تتمكن من استرداد القيمة السرية بعد المغادرة.

    :::image type="content" source="../../media/defender-endpoint/webapp-create-key2.png" alt-text="جزء إنشاء التطبيق في مدخل Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-create-key2.png":::

8. سجل معرف التطبيق الخاص بك ومعرف المستأجر الخاص بك في مكان آمن. يتم سردها ضمن **نظرة عامة** على صفحة التطبيق الخاص بك.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="جزء النظرة العامة في مدخل Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

9. **لشركاء Microsoft 365 Defender فقط**: [اتبع هذه الإرشادات](./api-partner-access.md) للوصول إلى الشركاء من خلال واجهات برمجة التطبيقات Microsoft 365 Defender، قم بتعيين تطبيقك ليكون متعدد المستأجرين، بحيث يمكن أن يكون متوفرا في جميع المستأجرين بمجرد حصولك على موافقة المسؤول. الوصول إلى الشريك **مطلوب** لتطبيقات الجهات الخارجية— على سبيل المثال، إذا قمت بإنشاء تطبيق مخصص للتشغيل في مستأجرين متعددين للعملاء. **ليس مطلوبا** إذا قمت بإنشاء خدمة تريد تشغيلها في المستأجر الخاص بك فقط، مثل تطبيق لاستخدامك الخاص الذي سيتفاعل فقط مع بياناتك الخاصة. لتعيين تطبيقك ليكون متعدد المستأجرين:

    - انتقل إلى **المصادقة**، وأضف https://portal.azure.com ك **URI لإعادة التوجيه**.

    - في أسفل الصفحة، ضمن **أنواع الحسابات المدعومة**، حدد **الحسابات في أي موافقة تطبيق دليل تنظيمي** لتطبيقك متعدد المستأجرين.

    نظرا إلى أن التطبيق الخاص بك يتفاعل مع Microsoft 365 Defender نيابة عن المستخدمين، فإنه يجب الموافقة عليه لكل مستأجر تنوي استخدامه عليه.

    يحتاج المسؤول العام ل Active Directory لكل مستأجر إلى تحديد ارتباط الموافقة والموافقة على تطبيقك.

    يحتوي ارتباط الموافقة على البنية التالية:

    ```http
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=<00000000-0000-0000-0000-000000000000>&response_type=code&sso_reload=true
    ```

    يجب استبدال الأرقام `00000000-0000-0000-0000-000000000000` بمعرف التطبيق الخاص بك.  

**القيام به!** لقد سجلت تطبيقا بنجاح! راجع الأمثلة أدناه للحصول على الرمز المميز والتحقق من صحته.

## <a name="get-an-access-token"></a>الحصول على رمز مميز للوصول

لمزيد من المعلومات حول الرموز المميزة ل Azure Active Directory، راجع [البرنامج التعليمي Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> على الرغم من أن الأمثلة في هذا القسم تشجعك على لصق القيم السرية لأغراض الاختبار، يجب **ألا تقوم أبدا بترميز البيانات السرية في** تطبيق يعمل في الإنتاج. يمكن لجهة خارجية استخدام بياناتك السرية للوصول إلى الموارد. يمكنك المساعدة في الحفاظ على أمان أسرار تطبيقك باستخدام [azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). للحصول على مثال عملي حول كيفية حماية تطبيقك، راجع [إدارة الأسرار في تطبيقات الخادم باستخدام Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

### <a name="get-an-access-token-using-powershell"></a>الحصول على رمز مميز للوصول باستخدام PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

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

### <a name="get-an-access-token-using-c"></a>الحصول على رمز مميز للوصول باستخدام C\#

> [!NOTE]
> تم اختبار التعليمات البرمجية التالية مع Nuget Microsoft.Identity.Client 3.19.8.

> [!IMPORTANT]
> تم إهمال حزمة [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) NuGet ومكتبة مصادقة Azure AD (ADAL). لم تتم إضافة أي ميزات جديدة منذ 30 يونيو 2020.   نحن نشجعك بشدة على الترقية، راجع [دليل الترحيل](/azure/active-directory/develop/msal-migration) للحصول على مزيد من التفاصيل.

1. إنشاء تطبيق وحدة تحكم جديد.

1. تثبيت NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/).

1. أضف السطر التالي:

    ```C#
    using Microsoft.Identity.Client;
    ```

1. انسخ التعليمات البرمجية التالية والصقها في تطبيقك (لا تنس تحديث المتغيرات الثلاثة: `tenantId`، ، `clientId``appSecret`:

    ```C#
    csharp
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place! 
    const string authority = https://login.microsoftonline.com;
    const string audience = https://api.securitycenter.microsoft.com;

    IConfidentialClientApplication myApp = ConfidentialClientApplicationBuilder.Create(appId).WithClientSecret(appSecret).WithAuthority($"{authority}/{tenantId}").Build();

    List<string> scopes = new List<string>() { $"{audience}/.default" };

    AuthenticationResult authResult = myApp.AcquireTokenForClient(scopes).ExecuteAsync().GetAwaiter().GetResult();

    string token = authResult.AccessToken;
    ```

### <a name="get-an-access-token-using-python"></a>الحصول على رمز مميز للوصول باستخدام Python

```Python
import json
import urllib.request
import urllib.parse

tenantId = '' # Paste your directory (tenant) ID here
clientId = '' # Paste your application (client) ID here
appSecret = '' # Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

url = "https://login.windows.net/%s/oauth2/token" % (tenantId)

resourceAppIdUri = 'https://api.security.microsoft.com'

body = {
    'resource' : resourceAppIdUri,
    'client_id' : clientId,
    'client_secret' : appSecret,
    'grant_type' : 'client_credentials'
}

data = urllib.parse.urlencode(body).encode("utf-8")

req = urllib.request.Request(url, data)
response = urllib.request.urlopen(req)
jsonResponse = json.loads(response.read())
aadToken = jsonResponse["access_token"]
```

### <a name="get-an-access-token-using-curl"></a>الحصول على رمز مميز للوصول باستخدام curl

> [!NOTE]
> تم تثبيت Curl مسبقا على Windows 10 والإصدارات 1803 والإصدارات الأحدث. بالنسبة للإصدارات الأخرى من Windows، قم بتنزيل الأداة وتثبيتها مباشرة من [موقع ويب curl الرسمي](https://curl.haxx.se/windows/).

1. افتح موجه الأوامر، وقم بتعيين CLIENT_ID إلى معرف تطبيق Azure.

1. تعيين CLIENT_SECRET إلى سر تطبيق Azure الخاص بك.

1. قم بتعيين TENANT_ID إلى معرف مستأجر Azure للعميل الذي يريد استخدام تطبيقك للوصول إلى Microsoft 365 Defender.

1. قم بتنفيذ الأمر التالي:

   ```bash
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.security.microsoft.com/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```

   ستبدو الاستجابة الناجحة كما يلي:

   ```bash
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

1. انسخ الرمز المميز والصقه في [موقع مدقق الرمز المميز على ويب JSON، JWT،](https://jwt.ms) لفك ترميزه.

1. تأكد من أن المطالبة *بالأدوار* داخل الرمز المميز الذي تم فك تشفيره يحتوي على الأذونات المطلوبة.

   في الصورة التالية، يمكنك مشاهدة رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق، باستخدام `Incidents.Read.All`، `Incidents.ReadWrite.All`وأذونات `AdvancedHunting.Read.All` :

   :::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="جزء الرمز المميز الذي تم فك ترميزه في مدخل Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>استخدم الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft 365 Defender

1. اختر واجهة برمجة التطبيقات التي تريد استخدامها (الحوادث أو التتبع المتقدم). لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات Microsoft 365 Defender المعتمدة](api-supported.md).

2. في طلب http الذي أنت على وشك إرساله، قم بتعيين رأس التخويل إلى `"Bearer" <token>`، *والحامل* هو نظام التخويل، *والرمز المميز* الذي تم التحقق من صحته.

3. ستنتهي صلاحية الرمز المميز في غضون ساعة واحدة. يمكنك إرسال أكثر من طلب واحد خلال هذا الوقت بنفس الرمز المميز.

يوضح المثال التالي كيفية إرسال طلب للحصول على قائمة بالحوادث **باستخدام C#**.

```C#
    var httpClient = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة على واجهات برمجة التطبيقات Microsoft 365 Defender](api-overview.md)
- [الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-access.md)
- [إنشاء تطبيق 'Hello world'](api-hello-world.md)
- [إنشاء تطبيق للوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender نيابة عن مستخدم](api-create-app-user-context.md)
- [إنشاء تطبيق مع وصول شريك متعدد المستأجرين إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-partner-access.md)
- [التعرف على حدود واجهة برمجة التطبيقات والترخيص](api-terms.md)
- [فهم رموز الأخطاء](api-error-codes.md)
- [إدارة البيانات السرية في تطبيقات الخادم باستخدام Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/)
- [تخويل OAuth 2.0 لتسجيل دخول المستخدم والوصول إلى واجهة برمجة التطبيقات](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
