---
title: إنشاء تطبيق للوصول إلى Microsoft Defender لنقطة النهاية بدون مستخدم
ms.reviewer: ''
description: تعرف على كيفية تصميم تطبيق ويب للحصول على وصول برمجي إلى Microsoft Defender ل Endpoint بدون مستخدم.
keywords: apis، واجهة برمجة التطبيق الرسومية، apis المعتمدة، الممثل، التنبيهات، الجهاز، المستخدم، المجال، ip، ملف، البحث المتقدم، الاستعلام
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
ms.openlocfilehash: 2705eb4e3010a06c707ad071a907da90dc0ec1fc
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575793"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>وصول الشريك عبر Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تصف هذه الصفحة كيفية إنشاء تطبيق Azure Active Directory (Azure AD) للحصول على وصول برمجي إلى Microsoft Defender لنقطة النهاية نيابة عن العملاء.

يعرض Microsoft Defender ل Endpoint الكثير من بياناته والإجراءات الخاصة به من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. ستساعدك واجهات برمجة التطبيقات هذه على أتمتة تدفقات العمل، كما ستساعدك على الابتكار استنادا إلى قدرات نقطة النهاية ل Microsoft Defender. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء **تطبيق** Azure AD متعدد المستأجرين.
- احصل على الإذن (الموافقة) من قبل مسؤول العملاء لتطبيقك للوصول إلى موارد Defender لنقطة النهاية التي يحتاج إليها.
- احصل على رمز وصول مميز باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى Microsoft Defender ل API لنقطة النهاية.

سترشدك الخطوات التالية إلى كيفية إنشاء تطبيق Azure AD والحصول على رمز وصول مميز إلى Microsoft Defender ل Endpoint والتحقق من صحة الرمز المميز.

## <a name="create-the-multi-tenant-app"></a>إنشاء تطبيق متعدد المستأجرين

1. سجل الدخول إلى [مستأجر Azure](https://portal.azure.com) باستخدام مستخدم له **دور المسؤول** العام.

2. انتقل إلى **تسجيلات تطبيق Azure Active Directory** \>  \> **تسجيل جديد**.

   ![صورة Microsoft Azure والتنقل إلى تسجيل التطبيق.](images/atp-azure-new-app2.png)

3. في نموذج التسجيل:

   - اختر اسما للتطبيق.

   - أنواع الحسابات المعتمدة - الحسابات في أي دليل هيكلي.

   - إعادة توجيه URI - اكتب: ويب، URI: https://portal.azure.com

   ![صورة لتسجيل تطبيق شريك Microsoft Azure.](images/atp-api-new-app-partner.png)

4. اسمح لتطبيقك بالوصول إلى Microsoft Defender لنقطة النهاية وتعيينه بأقل مجموعة من الأذونات المطلوبة لإكمال التكامل.

   - في صفحة التطبيق، حدد أذونات **API** \>  \> إضافة أذونات واجهات برمجة التطبيقات التي تستخدمها > **نوع WindowsDefenderATP** وحدد على **WindowsDefenderATP**.

   - **ملاحظة**: *لا يظهر WindowsDefenderATP* في القائمة الأصلية. ابدأ بكتابة اسمه في مربع النص لكي يظهر.

     ![إضافة إذن.](images/add-permission.png)

### <a name="request-api-permissions"></a>طلب أذونات API

لتحديد الإذن الذي تحتاج إليه، راجع مقطع **الأذونات** في API التي تريد الاتصال بها. على سبيل المثال:

- لتشغيل [الاستعلامات المتقدمة](run-advanced-query-api.md)، حدد الإذن "تشغيل الاستعلامات المتقدمة"
- [لعزل جهاز،](isolate-machine.md) حدد الإذن "عزل الجهاز"

في المثال التالي، سنستخدم **إذن "قراءة كل التنبيهات** ":

1. اختر **تنبيه أذونات** \> **التطبيق.Read.all** > تحديد **على إضافة أذونات**

   ![أذونات التطبيق.](images/application-permissions.png)

2. حدد **منح الموافقة**

   - **ملاحظة**: في كل مرة تقوم فيها بإضافة إذن، يجب أن تحدد عند منح **الموافقة** على الإذن الجديد لكي يتم التنفيذ.

   ![صورة لمنح الأذونات.](images/grant-consent.png)

3. أضف سرية إلى التطبيق.

   - حدد **الشهادات & أسرار،** وأضف وصفا للسر وحدد **إضافة**.

    **هام**: بعد النقر فوق إضافة، **انسخ القيمة السرية التي تم إنشاؤها**. لن تتمكن من استرداده بعد المغادرة!

    ![صورة لمفتاح إنشاء تطبيق.](images/webapp-create-key2.png)

4. اكتب "معرّف التطبيق":

   - على صفحة التطبيق، انتقل إلى **نظرة عامة** ونسخ المعلومات التالية:

   ![صورة لم id التطبيق الذي تم إنشاؤه.](images/app-id.png)

5. أضف التطبيق إلى مستأجر العميل.

   تحتاج إلى الموافقة على تطبيقك في كل مستأجر عميل تنوي استخدامه فيه. وذلك لأن تطبيقك يتفاعل مع تطبيق Microsoft Defender for Endpoint نيابة عن العميل.

   يحتاج مستخدم مع **مسؤول** عام من مستأجر العميل إلى تحديد ارتباط الموافقة والموافقة على طلبك.

   يكون ارتباط الموافقة من النموذج:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   حيث يجب استبدال 00000000-0000-0000-0000000000000 بم ID التطبيق

   بعد النقر فوق ارتباط الموافقة، سجل الدخول مع المسؤول العام لمستأجر العميل ووافق على التطبيق.

   ![صورة الموافقة.](images/app-consent-partner.png)

   بالإضافة إلى ذلك، ستحتاج إلى أن تطلب من العميل الخاص بك الحصول على هويات المستأجر الخاصة به وحفظه لاستخدامه في المستقبل عند الحصول على الرمز المميز.

6. **تم!** لقد سجلت تطبيقا بنجاح! راجع الأمثلة أدناه للحصول على الرمز المميز والتحقق من الصحة.

## <a name="get-an-access-token-example"></a>الحصول على مثال رمز مميز للوصول

**ملاحظة:** للحصول على رمز الوصول المميز نيابة عن العميل، استخدم "معر ة مستأجر العميل" على عمليات الحصول على الرموز المميزة التالية.

لمزيد من المعلومات حول AAD (دليل Azure النشط) المميز، راجع AAD (دليل Azure النشط) [التعليمي](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

### <a name="using-powershell"></a>استخدام PowerShell

```powershell
# That code gets the App Context Token and save it to a file named "Latest-token.txt" under the current directory
# Paste below your Tenant ID, App ID and App Secret (App key).

$tenantId = '' ### Paste your tenant ID here
$appId = '' ### Paste your Application ID here
$appSecret = '' ### Paste your Application key here

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

### <a name="using-c"></a>استخدام C #

> تم اختبار التعليمة البرمجية أدناه مع Nuget Microsoft.IdentityModel.Clients.ActiveDirectory

- إنشاء تطبيق وحدة تحكم جديد
- تثبيت NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- إضافة ما يلي باستخدام

    ```console
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- انسخ/اللصق التعليمة البرمجية أدناه في التطبيق (لا تنس تحديث المتغيرات الثلاثة: `tenantId`و `appId`و `appSecret`)

    ```console
    string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
    string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
    string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place!

    const string authority = "https://login.microsoftonline.com";
    const string wdatpResourceId = "https://api.securitycenter.microsoft.com";

    AuthenticationContext auth = new AuthenticationContext($"{authority}/{tenantId}/");
    ClientCredential clientCredential = new ClientCredential(appId, appSecret);
    AuthenticationResult authenticationResult = auth.AcquireTokenAsync(wdatpResourceId, clientCredential).GetAwaiter().GetResult();
    string token = authenticationResult.AccessToken;
    ```

### <a name="using-python"></a>استخدام Python

الرجوع إلى [الحصول على الرمز المميز باستخدام Python](run-advanced-query-sample-python.md#get-token)

### <a name="using-curl"></a>استخدام المجعد

> [!NOTE]
> الإجراء أدناه المفترض أن يكون Windows مثبتا بالفعل على الكمبيوتر

- فتح نافذة أوامر
- تعيين CLIENT_ID إلى "معرّف تطبيق Azure"
- تعيين CLIENT_SECRET إلى سرية تطبيق Azure
- تعيين TENANT_ID إلى "مستأجر Azure" الخاص للعميل الذي يريد استخدام التطبيق للوصول إلى تطبيق Microsoft Defender for Endpoint
- تشغيل الأمر أدناه:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

ستحصل على إجابة النموذج:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

التحقق من الصحة للتأكد من أنك حصلت على رمز مميز صحيح:

- نسخ/لصق الرمز المميز الذي تحصل عليه في الخطوة السابقة في [JWT](https://jwt.ms) من أجل فك ترميزه
- التحقق من صحة الحصول على مطالبة "أدوار" باستخدام الأذونات المطلوبة
- في لقطة الشاشة أدناه، يمكنك رؤية رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق مع أذونات متعددة ل Microsoft Defender لنقطة النهاية:
- المطالبة "tid" هي "مستأجر" الم ID الذي ينتمي إليه الرمز المميز.

![صورة التحقق من صحة الرمز المميز.](images/webapp-decoded-token.png)

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>استخدام الرمز المميز للوصول إلى Microsoft Defender ل API لنقطة النهاية

- اختر واجهات برمجة التطبيقات التي تريد استخدامها، لمزيد من المعلومات، راجع [واجهات برمجة تطبيقات نقطة النهاية المعتمدة من Microsoft Defender](exposed-apis-list.md)
- تعيين رأس التخويل في طلب Http الذي ترسله إلى "حامل {token}" (حامل هو نظام التخويل)
- وقت انتهاء صلاحية الرمز المميز هو ساعة واحدة (يمكنك إرسال أكثر من طلب واحد بنفس الرمز المميز)

- مثال لإرسال طلب للحصول على قائمة تنبيهات **باستخدام C#**

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>راجع أيضًا

- [واجهات برمجة تطبيقات نقطة النهاية المدعومة من Microsoft Defender](exposed-apis-list.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية نيابة عن مستخدم](exposed-apis-create-app-nativeapp.md)
