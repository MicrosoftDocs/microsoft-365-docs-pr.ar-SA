---
title: إنشاء تطبيق للوصول إلى Microsoft Defender لنقطة النهاية بدون مستخدم
ms.reviewer: ''
description: تعرف على كيفية تصميم تطبيق ويب للحصول على وصول برمجي إلى Microsoft Defender لنقطة النهاية دون مستخدم.
keywords: واجهة برمجة التطبيقات، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، الفاعل، التنبيهات، الجهاز، المستخدم، المجال، ip، الملف، التتبع المتقدم، الاستعلام
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
ms.openlocfilehash: f8b620d519b0e27fd54313329040096f10c070f9
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172349"
---
# <a name="create-an-app-to-access-microsoft-defender-for-endpoint-without-a-user"></a>إنشاء تطبيق للوصول إلى Microsoft Defender لنقطة النهاية بدون مستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> لا يتم تضمين قدرات التتبع المتقدمة في Defender for Business. راجع [مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Defender لنقطة النهاية دون مستخدم. إذا كنت بحاجة إلى وصول برمجي إلى Defender لنقطة النهاية نيابة عن مستخدم، فراجع [الحصول على حق الوصول باستخدام سياق المستخدم](exposed-apis-create-app-nativeapp.md). إذا لم تكن متأكدا من الوصول الذي تحتاجه، فراجع ["بدء الاستخدام](apis-intro.md)".

Microsoft Defender لنقطة النهاية يكشف الكثير من بياناته وإجراءاته من خلال مجموعة من واجهات برمجة التطبيقات البرمجية. ستساعدك واجهات برمجة التطبيقات هذه على أتمتة تدفقات العمل والابتكار استنادا إلى قدرات Defender لنقطة النهاية. يتطلب الوصول إلى واجهة برمجة التطبيقات مصادقة OAuth2.0. لمزيد من المعلومات، راجع [التعليمة البرمجية للتخويل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:
- إنشاء تطبيق Azure Active Directory (Azure AD).
- احصل على رمز مميز للوصول باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى Defender لواجهة برمجة تطبيقات نقطة النهاية.

تشرح هذه المقالة كيفية إنشاء تطبيق Azure AD، والحصول على رمز وصول مميز Microsoft Defender لنقطة النهاية، والتحقق من صحة الرمز المميز.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل الدخول إلى [Azure](https://portal.azure.com) باستخدام مستخدم لديه دور **المسؤول العام** .

2. انتقل إلى **تسجيلات** \> تطبيق **Azure Active Directory** \> **الجديدة**. 

    :::image type="content" source="images/atp-azure-new-app2.png" alt-text="جزء تسجيل التطبيق" lightbox="images/atp-azure-new-app2.png":::

3. في نموذج التسجيل، اختر اسما لتطبيقك، ثم حدد **"تسجيل**".

4. لتمكين تطبيقك من الوصول إلى Defender لنقطة النهاية وتعيين إذن **"قراءة جميع التنبيهات"** ، في صفحة التطبيق، حدد **API Permissions** \> **Add permission** \> **APIs التي تستخدمها مؤسستي** >، واكتب **WindowsDefenderATP**، ثم حدد **WindowsDefenderATP**.

   > [!NOTE]
   > لا يظهر *WindowsDefenderATP* في القائمة الأصلية. ابدأ بكتابة اسمه في مربع النص لكي يظهر.

   :::image type="content" source="images/add-permission.png" alt-text="جزء أذونات واجهة برمجة التطبيقات" lightbox="images/add-permission.png":::

   حدد **Alert.Read.All** **لأذونات** \> التطبيق، ثم حدد **"إضافة أذونات**".

   :::image type="content" source="images/application-permissions.png" alt-text="جزء معلومات أذونات التطبيق" lightbox="images/application-permissions.png":::

     تحتاج إلى تحديد الأذونات ذات الصلة. "قراءة كافة التنبيهات" هو مثال فقط. على سبيل المثال:

     - [لتشغيل الاستعلامات المتقدمة](run-advanced-query-api.md)، حدد إذن "تشغيل الاستعلامات المتقدمة".
     - [لعزل جهاز](isolate-machine.md)، حدد إذن "عزل الجهاز".
     - لتحديد الإذن الذي تحتاجه، انظر إلى قسم **الأذونات** في واجهة برمجة التطبيقات التي تريد الاتصال بها.

5. حدد **منح الموافقة**.

     > [!NOTE]
     > في كل مرة تضيف فيها إذنا، يجب تحديد **"منح الموافقة** " لكي يدخل الإذن الجديد حيز التنفيذ.

    :::image type="content" source="images/grant-consent.png" alt-text="صفحة أذونات المنح" lightbox="images/grant-consent.png":::

6. لإضافة سر إلى التطبيق، حدد **"Certificates & secrets**"، وأضف وصفا إلى السر، ثم حدد **"Add**".

    > [!NOTE]
    > بعد تحديد **"إضافة"**، حدد **نسخ قيمة البيانات السرية التي تم إنشاؤها**. لن تتمكن من استرداد هذه القيمة بعد المغادرة.

      :::image type="content" source="images/webapp-create-key2.png" alt-text="خيار إنشاء التطبيق" lightbox="images/webapp-create-key2.png":::

7. اكتب معرف التطبيق الخاص بك ومعرف المستأجر الخاص بك. في صفحة التطبيق، انتقل إلى **Overview** وانسخ ما يلي.

   :::image type="content" source="images/app-and-tenant-ids.png" alt-text="معرفات التطبيق والمستأجر التي تم إنشاؤها" lightbox="images/app-and-tenant-ids.png":::

8. **لشركاء Microsoft Defender لنقطة النهاية فقط**. قم بتعيين تطبيقك ليكون متعدد المستأجرين (متوفر في جميع المستأجرين بعد الموافقة). هذا **مطلوب** لتطبيقات الجهات الخارجية (على سبيل المثال، إذا قمت بإنشاء تطبيق مخصص للتشغيل في مستأجر عملاء متعددين). **هذا غير مطلوب** إذا قمت بإنشاء خدمة تريد تشغيلها في المستأجر الخاص بك فقط (على سبيل المثال، إذا قمت بإنشاء تطبيق لاستخدامك الخاص الذي سيتفاعل فقط مع بياناتك الخاصة). لتعيين تطبيقك ليكون متعدد المستأجرين:

    - انتقل إلى **المصادقة**، وأضف `https://portal.azure.com` ك **URI لإعادة التوجيه**.

    - في أسفل الصفحة، ضمن **أنواع الحسابات المدعومة**، حدد **الحسابات في أي موافقة تطبيق دليل تنظيمي** لتطبيقك متعدد المستأجرين.

    تحتاج إلى الموافقة على التطبيق الخاص بك في كل مستأجر حيث تنوي استخدامه. وذلك لأن تطبيقك يتفاعل مع Defender لنقطة النهاية نيابة عن عميلك.

    أنت (أو عميلك إذا كنت تكتب تطبيقا تابعا لجهة خارجية) تحتاج إلى تحديد ارتباط الموافقة والموافقة على تطبيقك. يجب أن تتم الموافقة مع مستخدم لديه امتيازات إدارية في Active Directory.

    يتم تشكيل ارتباط الموافقة كما يلي: 

    ```https
    https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
    ```

    حيث يتم استبدال 000000000-0000-0000-0000000000000 بمعرف التطبيق الخاص بك.


**القيام به!** لقد قمت بتسجيل تطبيق بنجاح! راجع الأمثلة أدناه للحصول على الرمز المميز والتحقق من صحته.

## <a name="get-an-access-token"></a>الحصول على رمز مميز للوصول

لمزيد من المعلومات حول الرموز المميزة Azure AD، راجع [البرنامج التعليمي Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

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

### <a name="use-c"></a>استخدام C#:

تم اختبار التعليمات البرمجية التالية باستخدام NuGet Microsoft.IdentityModel.Clients.ActiveDirectory 3.19.8.

1. إنشاء تطبيق وحدة تحكم جديد.
1. تثبيت NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).
1. أضف ما يلي:

    ```csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

1. انسخ التعليمات البرمجية التالية والصقها في تطبيقك (لا تنس تحديث المتغيرات الثلاثة: ```tenantId, appId, appSecret```):

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

### <a name="use-curl"></a>استخدام Curl

> [!NOTE]
> يفترض الإجراء التالي أن Curl for Windows مثبت بالفعل على الكمبيوتر.

1. افتح موجه الأوامر، وقم بتعيين CLIENT_ID إلى معرف تطبيق Azure.
1. تعيين CLIENT_SECRET إلى سر تطبيق Azure الخاص بك.
1. قم بتعيين TENANT_ID إلى معرف مستأجر Azure للعميل الذي يريد استخدام تطبيقك للوصول إلى Defender لنقطة النهاية.
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

1. انسخ والصق الرمز المميز الذي حصلت عليه في الخطوة السابقة في [JWT](https://jwt.ms) لفك ترميزه.

1. تحقق من حصولك على مطالبة "الأدوار" بالأذونات المطلوبة.

   في الصورة التالية، يمكنك مشاهدة رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق مع أذونات لجميع أدوار Microsoft Defender لنقطة النهاية:

   :::image type="content" source="images/webapp-decoded-token.png" alt-text="جزء تفاصيل الرمز المميز" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>استخدام الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية

1. اختر واجهة برمجة التطبيقات التي تريد استخدامها. لمزيد من المعلومات، راجع [واجهات برمجة تطبيقات Defender لنقطة النهاية المدعومة](exposed-apis-list.md).
1. قم بتعيين رأس التخويل في طلب http الذي ترسله إلى "Bearer {token}" (Bearer هو نظام التخويل).
1. وقت انتهاء صلاحية الرمز المميز هو ساعة واحدة. يمكنك إرسال أكثر من طلب واحد بنفس الرمز المميز.

فيما يلي مثال على إرسال طلب للحصول على قائمة بالتنبيهات **باستخدام C#**:

```csharp
var httpClient = new HttpClient();

var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

// Do something useful with the response
```

## <a name="see-also"></a>راجع أيضًا
- [واجهات Microsoft Defender لنقطة النهاية برمجة التطبيقات المعتمدة](exposed-apis-list.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية نيابة عن مستخدم](exposed-apis-create-app-nativeapp.md)
