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
ms.openlocfilehash: e32f05792b4658c7d7b42f78e88d989dfb134a78
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583180"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>إنشاء تطبيق للوصول إلى Microsoft Defender لنقطة النهاية بدون مستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Defender لنقطة النهاية بدون مستخدم. إذا كنت بحاجة إلى الوصول برمجيا إلى Defender for Endpoint نيابة عن المستخدم، فشاهد [الوصول باستخدام سياق المستخدم](exposed-apis-create-app-nativeapp.md). إذا لم تكن متأكدا من الوصول الذي تحتاج إليه، فشاهد [بدء العمل](apis-intro.md).

يعرض Microsoft Defender ل Endpoint الكثير من بياناته والإجراءات الخاصة به من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. ستساعدك واجهات برمجة التطبيقات هذه على أتمتة تدفقات العمل وابتعازها استنادا إلى قدرات Defender لنقطة النهاية. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:
- إنشاء تطبيق Azure Active Directory (Azure AD).
- احصل على رمز وصول مميز باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى Defender ل API لنقطة النهاية.

تشرح هذه المقالة كيفية إنشاء تطبيق Azure AD والحصول على رمز وصول مميز إلى Microsoft Defender ل Endpoint والتحقق من صحة الرمز المميز.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل دخولك إلى [Azure](https://portal.azure.com) مع مستخدم لديه **دور المسؤول** العام.

2. انتقل إلى **تسجيلات تطبيق Azure Active Directory** \>  \> **تسجيل جديد**. 

    :::image type="content" alt-text="صورة Microsoft Azure والتنقل إلى تسجيل التطبيق." source="images/atp-azure-new-app2.png" lightbox="images/atp-azure-new-app2.png":::

3. في نموذج التسجيل، اختر اسما للتطبيق، ثم حدد **تسجيل**.

4. لتمكين تطبيقك من الوصول إلى Defender for Endpoint وتعيين **إذن "** قراءة كل التنبيهات"، على صفحة التطبيق، حدد أذونات **API** \>  \> إضافة أذونات واجهات برمجة التطبيقات التي تستخدمها **مؤسستك >،** وا اكتب **WindowsDefenderATP**، ثم حدد **WindowsDefenderATP**.

   > [!NOTE]
   > *لا يظهر WindowsDefenderATP* في القائمة الأصلية. ابدأ بكتابة اسمه في مربع النص لكي يظهر.

   :::image type="content" alt-text="إضافة إذن." source="images/add-permission.png" lightbox="images/add-permission.png":::

   حدد **أذونات التطبيق** \> **Alert.Read.All**، ثم حدد **إضافة أذونات**.

   :::image type="content" alt-text="إذن التطبيق." source="images/application-permissions.png" lightbox="images/application-permissions.png":::

     يجب تحديد الأذونات ذات الصلة. "قراءة كل التنبيهات" مثال فقط. على سبيل المثال:

     - لتشغيل [الاستعلامات المتقدمة](run-advanced-query-api.md)، حدد الإذن 'تشغيل الاستعلامات المتقدمة'.
     - [لعزل جهاز،](isolate-machine.md) حدد الإذن 'عزل الجهاز'.
     - لتحديد الإذن الذي تحتاج إليه، **انظر إلى مقطع** الأذونات في API التي تريد الاتصال بها.

5. حدد **منح الموافقة**.

     > [!NOTE]
     > في كل مرة تضيف فيها إذنا، يجب تحديد **منح الموافقة** لكي يكون الإذن الجديد حيز التنفيذ.

    ![منح الأذونات.](images/grant-consent.png)

6. لإضافة سر إلى التطبيق، حدد الشهادات **&،** وأضف وصفا للسر، ثم حدد **إضافة**.

    > [!NOTE]
    > بعد تحديد **إضافة،** حدد **نسخ القيمة السرية التي تم إنشاؤها**. لن تتمكن من استرداد هذه القيمة بعد المغادرة.

    ![صورة لمفتاح إنشاء تطبيق.](images/webapp-create-key2.png)

7. اكتب "معرّف التطبيق" وم ID المستأجر. على صفحة التطبيق، انتقل إلى **نظرة عامة** ونسخ ما يلي.

   :::image type="content" alt-text="صورة لم id التطبيق الذي تم إنشاؤه." source="images/app-and-tenant-ids.png" lightbox="images/app-and-tenant-ids.png":::

8. **ل Microsoft Defender لشركاء نقطة النهاية فقط**. قم بتعيين تطبيقك إلى مستأجر متعدد (متوفر في جميع المستأجرين بعد الموافقة). هذا مطلوب **لتطبيقات** الأطراف الخارجية (على سبيل المثال، إذا قمت بإنشاء تطبيق مخصص للتشغيل في مستأجر عملاء متعددين). هذا غير **مطلوب** إذا قمت بإنشاء خدمة تريد تشغيلها في المستأجر فقط (على سبيل المثال، إذا قمت بإنشاء تطبيق لاستخدامك الخاص يتفاعل فقط مع بياناتك الخاصة). لتعيين تطبيقك إلى مستأجر متعدد:

    - انتقل إلى **المصادقة**، وأضف كمعر `https://portal.azure.com` **URI إعادة التوجيه**.

    - في أسفل الصفحة، ضمن أنواع الحسابات المعتمدة، حدد موافقة الحسابات في  أي تطبيق دليل هيكلي لتطبيقك متعدد المستأجرين.

    تحتاج إلى الموافقة على تطبيقك في كل مستأجر تنوي استخدامه فيه. وذلك لأن تطبيقك يتفاعل مع Defender for Endpoint نيابة عن العميل.

    تحتاج أنت (أو العميل إذا كنت تكتب تطبيقا من جهة خارجية) إلى تحديد ارتباط الموافقة والموافقة على تطبيقك. يجب أن تتم الموافقة مع مستخدم لديه امتيازات إدارية في Active Directory.

    يتم تكوين ارتباط الموافقة كما يلي: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    حيث يتم استبدال 00000000-0000-0000-0000000000000 بم ID التطبيق.


**تم!** لقد سجلت تطبيقا بنجاح! راجع الأمثلة أدناه للحصول على الرمز المميز والتحقق من الصحة.

## <a name="get-an-access-token"></a>الحصول على رمز وصول مميز

لمزيد من المعلومات حول رموز Azure AD المميزة، راجع البرنامج التعليمي [Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="use-powershell"></a>استخدام PowerShell

```powershell
# This script acquires the App Context Token and stores it in the variable $token for later use in the script.
# Paste your Tenant ID, App ID, and App Secret (App key) into the indicated quotes below.

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
```

### <a name="use-c"></a>استخدم C#:

تم اختبار التعليمة البرمجية التالية باستخدام NuGet Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. إنشاء تطبيق وحدة تحكم جديد.
1. تثبيت NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. أضف ما يلي:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. انسخ التعليمة البرمجية التالية واللصق فيها (لا تنس تحديث المتغيرات الثلاثة: ```tenantId, appId, appSecret```):

    ```csharp
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


### <a name="use-python"></a>استخدام Python

راجع [الحصول على الرمز المميز باستخدام Python](run-advanced-query-sample-python.md#get-token).

### <a name="use-curl"></a>استخدام المجعد

> [!NOTE]
> يفترض الإجراء التالي أن مؤشر Windows مثبت بالفعل على الكمبيوتر.

1. افتح موجه أوامر، وعين CLIENT_ID إلى "معرّف تطبيق Azure".
1. قم CLIENT_SECRET إلى سرية تطبيق Azure.
1. قم TENANT_ID إلى "مستأجر Azure" الخاص للعميل الذي يريد استخدام تطبيقك للوصول إلى Defender for Endpoint.
1. قم بتنفيذ الأمر التالي:

    ```console
    curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
    ```
    
    ستحصل على إجابة في النموذج التالي:
    
    ```console
    {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
    ```
    
## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

تأكد من حصولك على الرمز المميز الصحيح:

1. انسخ الرمز المميز الذي حصلت عليه في الخطوة السابقة والصقه في [JWT](https://jwt.ms) من أجل فك ترميزه.

1. تحقق من صحة الحصول على مطالبة "أدوار" بالأذونات المطلوبة.

   في الصورة التالية، يمكنك رؤية رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق مع أذونات لكل أدوار Microsoft Defender ل Endpoint:

   :::image type="content" alt-text="صورة التحقق من صحة الرمز المميز." source="images/webapp-decoded-token.png" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>استخدام الرمز المميز للوصول إلى Microsoft Defender ل API لنقطة النهاية

1. اختر API الذي تريد استخدامه. لمزيد من المعلومات، راجع [دعم Defender ل واجهات برمجة التطبيقات لنقطة النهاية](exposed-apis-list.md).
1. قم بتعيين رأس التفويض في طلب http الذي ترسله إلى "حامل {token}" (إن Bearer هو نظام التخويل).
1. وقت انتهاء صلاحية الرمز المميز هو ساعة واحدة. يمكنك إرسال أكثر من طلب واحد بنفس الرمز المميز.

فيما يلي مثال لإرسال طلب للحصول على قائمة بالتنبيهات **باستخدام C#**:

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
