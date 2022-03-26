---
title: وصول الشريك عبر Microsoft 365 Defender واجهات برمجة التطبيقات
description: تعرف على كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Microsoft 365 Defender نيابة عن المستخدمين.
keywords: شريك، وصول، api، مستأجر متعدد، موافقة، رمز وصول مميز، تطبيق
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
ms.openlocfilehash: 8a80245f4e94ee6f5f413154cf9b6d2ea318f5e4
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63570613"
---
# <a name="create-an-app-with-partner-access-to-microsoft-365-defender-apis"></a>إنشاء تطبيق مع وصول الشريك Microsoft 365 Defender واجهات برمجة التطبيقات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

تصف هذه الصفحة كيفية إنشاء تطبيق Azure Active Directory الذي يحتوي على وصول برمجي إلى Microsoft 365 Defender، نيابة عن المستخدمين عبر مستأجرين متعددين. إن التطبيقات متعددة المستأجرين مفيدة لخدمة مجموعات كبيرة من المستخدمين.

إذا كنت بحاجة إلى الوصول Microsoft 365 Defender نيابة عن مستخدم واحد، فشاهد إنشاء تطبيق للوصول إلى Microsoft 365 Defender [واجهات](api-create-app-user-context.md) برمجة التطبيقات بالنيابة عن مستخدم. إذا كنت بحاجة إلى الوصول بدون مستخدم معرف بوضوح (على سبيل المثال، إذا كنت تكتب تطبيق خلفية أو daemon)، فشاهد إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون [مستخدم](api-create-app-web.md). إذا لم تكن متأكدا من نوع الوصول الذي تحتاج إليه، فشاهد [بدء العمل](api-access.md).

Microsoft 365 Defender البيانات والإجراءات من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. تساعدك واجهات برمجة التطبيقات هذه على أتمتة مهام سير العمل واستخدام Microsoft 365 Defender الخاصة بها. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات التالية:

- إنشاء تطبيق Azure Active Directory (Azure AD).
- احصل على رمز وصول مميز باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى Microsoft 365 Defender API.

بما أن هذا التطبيق متعدد المستأجرين، ستحتاج أيضا إلى موافقة [المسؤول من كل](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) مستأجر نيابة عن المستخدمين.

تشرح هذه المقالة كيفية:

- إنشاء **تطبيق** Azure AD متعدد المستأجرين
- احصل على موافقة م مخولا من مسؤول المستخدم لتطبيقك للوصول إلى Microsoft 365 Defender الموارد التي يحتاج إليها.
- احصل على رمز وصول مميز Microsoft 365 Defender
- التحقق من صحة الرمز المميز

Microsoft 365 Defender البيانات والإجراءات من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. ستساعدك واجهات برمجة التطبيقات هذه على أتمتة تدفقات العمل وابتعازها استنادا إلى Microsoft 365 Defender جديدة. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء **تطبيق** Azure AD متعدد المستأجرين.
- احصل على الإذن (الموافقة) من قبل مسؤول المستخدم لتطبيقك للوصول إلى Microsoft 365 Defender التي يحتاج إليها.
- احصل على رمز وصول مميز باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى Microsoft 365 Defender API.

ترشدك الخطوات التالية التي ترشدك إلى كيفية إنشاء تطبيق Azure AD متعدد المستأجرين، والحصول على رمز وصول مميز Microsoft 365 Defender التحقق من صحة الرمز المميز.

## <a name="create-the-multi-tenant-app"></a>إنشاء تطبيق متعدد المستأجرين

1. سجل الدخول إلى [Azure](https://portal.azure.com) كمستخدم باستخدام **دور المسؤول** العام.

2. انتقل إلى **تسجيلات Azure Active DirectoryApp** >  >  **التسجيل الجديد**.

   ![صورة Microsoft Azure والتنقل إلى تسجيل التطبيق.](../../media/atp-azure-new-app2.png)

3. في نموذج التسجيل:

   - اختر اسما للتطبيق.
   - من **أنواع الحسابات المعتمدة**، حدد **الحسابات في أي دليل هيكلي (أي دليل Azure AD) - متعدد.**
   - قم **بتعبئة المقطع إعادة توجيه URI** . حدد نوع **ويب** وامنح URI إعادة التوجيه ك **https://portal.azure.com**.

   بعد أن تملأ النموذج، حدد **تسجيل**.

   ![صورة ل نموذج تسجيل أحد التطبيقات.](../..//media/atp-api-new-app-partner.png)

4. في صفحة التطبيق الخاصة بك، حدد أذونات **APIAdd** >  **permissionAPIs** >  **تستخدم >**، وا اكتب الحماية من المخاطر من **Microsoft**، وحدد **الحماية من المخاطر من Microsoft**. يمكن لتطبيقك الآن الوصول إلى Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* هو اسم سابق Microsoft 365 Defender، ولن يظهر في القائمة الأصلية. ستحتاج إلى بدء كتابة اسمه في مربع النص لكي يظهر.

   ![صورة تحديد أذونات API.](../../media/apis-in-my-org-tab.PNG)

5. حدد **أذونات التطبيق**. اختر الأذونات ذات الصلة في السيناريو (على سبيل المثال **، Incident.Read.All**)، ثم حدد **إضافة أذونات**.

   ![صورة الوصول إلى API واختيار API.](../../media/request-api-permissions.PNG)

    > [!NOTE]
    > أنت بحاجة إلى تحديد الأذونات ذات الصلة في السيناريو الخاص بك. *ما عليك سوى قراءة كل* الأحداث كمثال. لتحديد الإذن الذي تحتاج إليه، يرجى الاطلاع على قسم **الأذونات** في API الذي تريد الاتصال به.
    >
    > على سبيل المثال، لتشغيل [استعلامات متقدمة](api-advanced-hunting.md)، حدد الإذن "تشغيل الاستعلامات المتقدمة"؛ [لعزل جهاز،](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine) حدد الإذن 'عزل الجهاز'.

6. حدد **منح موافقة المسؤول**. في كل مرة تضيف فيها إذنا، يجب تحديد **منح موافقة** المسؤول لكي يتم هذا الأمر.

    ![صورة لمنح الأذونات.](../../media/grant-consent.PNG)

7. لإضافة سر إلى التطبيق، حدد الشهادات **&،** وأضف وصفا للسر، ثم حدد **إضافة**.

    > [!TIP]
    > بعد تحديد **إضافة،** حدد **نسخ القيمة السرية التي تم إنشاؤها**. لن تتمكن من استرداد القيمة السرية بعد المغادرة.

    ![صورة لمفتاح إنشاء تطبيق.](../../media/webapp-create-key2.png)

8. سجل "رقم التطبيق" وم ID المستأجر الخاص بك في مكان آمن. يتم سردها ضمن **نظرة عامة** على صفحة التطبيق.

   ![صورة لم id التطبيق الذي تم إنشاؤه.](../../media/app-and-tenant-ids.png)

9. أضف التطبيق إلى مستأجر المستخدم.

   بما أن تطبيقك يتفاعل مع Microsoft 365 Defender نيابة عن المستخدمين، يجب اعتماده لكل مستأجر تنوي استخدامه عليه.

   يحتاج **المسؤول العام** من مستأجر المستخدم إلى عرض ارتباط الموافقة والموافقة على طلبك.

   يكون ارتباط الموافقة من النموذج:

   ```HTTP
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   يجب استبدال الأرقام `00000000-0000-0000-0000-000000000000` بم ID التطبيق الخاص بك.

   بعد النقر فوق ارتباط الموافقة، سجل الدخول مع المسؤول العام لمستأجر المستخدم ووافق على التطبيق.

   ![صورة الموافقة.](../../media/app-consent-partner.png)

   ستحتاج أيضا إلى طلب من المستخدم الخاص بك لمعرف المستأجر الخاص به. معرف المستأجر هو أحد المعرفين المستخدمين للحصول على رموز الوصول المميزة.

- **تم!** لقد سجلت تطبيقا بنجاح!
- راجع الأمثلة أدناه للحصول على الرمز المميز والتحقق من الصحة.

## <a name="get-an-access-token"></a>الحصول على رمز وصول مميز

لمزيد من المعلومات حول رموز Azure AD المميزة، راجع البرنامج التعليمي [Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

> [!IMPORTANT]
> على الرغم من أن الأمثلة في هذا القسم تشجعك على لصق القيم السرية لأغراض الاختبار، إلا أنه لا يجب عليك  أبدا إدخال أسرار الترميز الثابت في تطبيق قيد الإنتاج. يمكن أن تستخدم جهة خارجية سرك للوصول إلى الموارد. يمكنك المساعدة في الحفاظ على أمان أسرار تطبيقك باستخدام [Azure Key Vault](/azure/key-vault/general/about-keys-secrets-certificates). للحصول على مثال عملي حول كيفية حماية تطبيقك، راجع إدارة أسرار تطبيقات الخادم [باستخدام Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/).

> [!TIP]
> في الأمثلة التالية، استخدم "اسم المستأجر" الخاص ب المستخدم لاختبار أن البرنامج النصي يعمل.

### <a name="get-an-access-token-using-powershell"></a>الحصول على رمز وصول مميز باستخدام PowerShell

```PowerShell
# This code gets the application context token and saves it to a file named "Latest-token.txt" under the current directory.

$tenantId = '' # Paste your directory (tenant) ID here
$clientId = '' # Paste your application (client) ID here
$appSecret = '' # Paste your own app secret here to test, then store it in a safe place!

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

### <a name="get-an-access-token-using-c"></a>الحصول على رمز وصول مميز باستخدام C\#

> [!NOTE]
> تم اختبار التعليمة البرمجية التالية مع Nuget Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. إنشاء تطبيق وحدة تحكم جديد.
1. تثبيت NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. أضف السطر التالي:

    ```C#
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. انسخ التعليمة البرمجية التالية واللصق بها في تطبيقك (لا تنس تحديث المتغيرات الثلاثة: `tenantId`، ، `clientId`، : `appSecret`

    ```C#
    string tenantId = ""; // Paste your directory (tenant) ID here
    string clientId = ""; // Paste your application (client) ID here
    string appSecret = ""; // Paste your own app secret here to test, then store it in a safe place, such as the Azure Key Vault!

    const string authority = "https://login.windows.net";
    const string wdatpResourceId = "https://api.security.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(clientId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```

### <a name="get-an-access-token-using-python"></a>الحصول على رمز وصول مميز باستخدام بايثون

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

### <a name="get-an-access-token-using-curl"></a>الحصول على رمز وصول مميز باستخدام حليق

> [!NOTE]
> تم تثبيت Curl مسبقا على Windows 10 والإصدارات 1803 والإصدارات الأحدث. بالنسبة للإصدارات الأخرى من Windows، قم بتنزيل الأداة وتثبيتها مباشرة من [موقع ويب المجعد الرسمي](https://curl.haxx.se/windows/).

1. افتح موجه أوامر، وعين CLIENT_ID إلى "معرّف تطبيق Azure".
1. قم CLIENT_SECRET إلى سرية تطبيق Azure.
1. قم TENANT_ID إلى "مستأجر Azure" للمستخدم الذي يريد استخدام تطبيقك للوصول إلى Microsoft 365 Defender.
1. قم بتنفيذ الأمر التالي:

```bash
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

ستبدو الاستجابة الناجحة كما يلي:

```bash
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

1. انسخ الرمز المميز والصقه في موقع [ويب للتحقق من صحة رمز JSON المميز على الويب، JWT](https://jwt.ms) ، لفك ترميزه.
1. تأكد من أن *ادعاء الأدوار* ضمن الرمز المميز الذي تم فك فك تشفيره يحتوي على الأذونات المطلوبة.

في الصورة التالية، يمكنك رؤية رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق، باستخدام ```Incidents.Read.All```، ```Incidents.ReadWrite.All```و، وأذونات ```AdvancedHunting.Read.All``` :

![صورة التحقق من صحة الرمز المميز.](../../media/webapp-decoded-token.png)

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>استخدام الرمز المميز للوصول إلى Microsoft 365 Defender API

1. اختر API الذي تريد استخدامه (الأحداث أو الصيد المتقدم). لمزيد من المعلومات، راجع [واجهات Microsoft 365 Defender برمجة التطبيقات المعتمدة](api-supported.md).
2. في طلب http الذي أنت `"Bearer" <token>`على وشك إرساله، قم بتعيين رأس التخويل إلى ، *يكون Bearer* هو نظام التخويل، والرمز *المميز هو الرمز* المميز الذي تم التحقق من صحته.
3. ستنتهي صلاحية الرمز المميز في غضون ساعة واحدة. يمكنك إرسال أكثر من طلب واحد خلال هذه الفترة بنفس الرمز المميز.

يوضح المثال التالي كيفية إرسال طلب للحصول على قائمة بالحوادث **باستخدام C#**.

```C#
   var httpClient = new HttpClient();
   var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

   request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

   var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [Microsoft 365 Defender نظرة عامة على واجهات برمجة التطبيقات](api-overview.md)
- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [إنشاء تطبيق 'Hello world'](api-hello-world.md)
- [إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم](api-create-app-web.md)
- [إنشاء تطبيق للوصول Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم](api-create-app-user-context.md)
- [التعرف على حدود API والترخيص](api-terms.md)
- [فهم رموز الخطأ](api-error-codes.md)
- [إدارة أسرار تطبيقات الخادم باستخدام مخزن مفاتيح Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [تخويل OAuth 2.0 تسجيل دخول المستخدم والوصول إلى API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
