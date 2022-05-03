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
ms.openlocfilehash: fde2cc894fb989628f9e2e0d9d7297bdb3c9e9da
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172409"
---
# <a name="partner-access-through-microsoft-defender-for-endpoint-apis"></a>وصول الشريك من خلال واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> لا يتم تضمين قدرات التتبع المتقدمة في Defender for Business. راجع [مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تصف هذه الصفحة كيفية إنشاء تطبيق Azure Active Directory (Azure AD) للحصول على وصول برمجي إلى Microsoft Defender لنقطة النهاية نيابة عن عملائك.

Microsoft Defender لنقطة النهاية يكشف الكثير من بياناته وإجراءاته من خلال مجموعة من واجهات برمجة التطبيقات البرمجية. ستساعدك واجهات برمجة التطبيقات هذه على أتمتة تدفقات العمل والابتكار استنادا إلى قدرات Microsoft Defender لنقطة النهاية. يتطلب الوصول إلى واجهة برمجة التطبيقات مصادقة OAuth2.0. لمزيد من المعلومات، راجع [التعليمة البرمجية للتخويل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء تطبيق Azure AD **متعدد المستأجرين**.
- احصل على إذن (موافقة) من مسؤول العميل لتطبيقك للوصول إلى موارد Defender لنقطة النهاية التي يحتاجها.
- احصل على رمز مميز للوصول باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية.

سترشدك الخطوات التالية إلى كيفية إنشاء تطبيق Azure AD والحصول على رمز وصول مميز Microsoft Defender لنقطة النهاية والتحقق من صحة الرمز المميز.

## <a name="create-the-multi-tenant-app"></a>إنشاء تطبيق متعدد المستأجرين

1. سجل الدخول إلى [مستأجر Azure](https://portal.azure.com) باستخدام المستخدم الذي لديه دور **المسؤول العام** .

2. انتقل إلى **تسجيلات** \> تطبيق **Azure Active Directory** \> **الجديدة**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="جزء التنقل إلى تسجيل التطبيق" lightbox="images/atp-azure-new-app2.png":::

3. في نموذج التسجيل:

   - اختر اسما للتطبيق الخاص بك.

   - أنواع الحسابات المدعومة - الحسابات في أي دليل تنظيمي.

   - إعادة توجيه URI - النوع: ويب، URI: https://portal.azure.com

     :::image type="content" source="images/atp-api-new-app-partner.png" alt-text="صفحة تسجيل تطبيق شريك Microsoft Azure" lightbox="images/atp-api-new-app-partner.png":::

4. السماح للتطبيق بالوصول إلى Microsoft Defender لنقطة النهاية وتعيينه بأقل مجموعة من الأذونات المطلوبة لإكمال التكامل.

   - في صفحة التطبيق، حدد **API Permissions** \> **Add permission** \> **APIs التي تستخدمها مؤسستي** > نوع **WindowsDefenderATP** وحدد على **WindowsDefenderATP**.

   - **ملاحظة**: لا يظهر *WindowsDefenderATP* في القائمة الأصلية. ابدأ بكتابة اسمه في مربع النص لكي يظهر.

     :::image type="content" source="images/add-permission.png" alt-text="الخيار &quot;إضافة إذن&quot;" lightbox="images/add-permission.png":::

### <a name="request-api-permissions"></a>طلب أذونات واجهة برمجة التطبيقات

لتحديد الإذن الذي تحتاجه، راجع قسم **الأذونات** في واجهة برمجة التطبيقات التي تريد الاتصال بها. على سبيل المثال:

- [لتشغيل الاستعلامات المتقدمة](run-advanced-query-api.md)، حدد إذن "تشغيل الاستعلامات المتقدمة"
- [لعزل جهاز](isolate-machine.md)، حدد إذن "عزل الجهاز"

في المثال التالي، سنستخدم إذن **"قراءة جميع التنبيهات"** :

1. اختر **Alert.Read.All** **لأذونات** \> التطبيق > تحديد **"إضافة أذونات"**

   :::image type="content" source="images/application-permissions.png" alt-text="الخيار الذي يسمح بإضافة إذن" lightbox="images/application-permissions.png":::

2. تحديد **منح الموافقة**

   - **ملاحظة**: في كل مرة تضيف فيها الإذن، يجب تحديد منح **الموافقة** لكي يدخل الإذن الجديد حيز التنفيذ.

   :::image type="content" source="images/grant-consent.png" alt-text="الخيار الذي يسمح بمنح الموافقة" lightbox="images/grant-consent.png":::

3. إضافة سر إلى التطبيق.

   - حدد **"Certificates & secrets**"، وأضف وصفا إلى السر وحدد **"Add**".

    **هام**: بعد النقر فوق "إضافة"، **انسخ القيمة السرية التي تم إنشاؤها**. لن تتمكن من استرداده بعد المغادرة!

     :::image type="content" source="images/webapp-create-key2.png" alt-text="مفتاح إنشاء التطبيق" lightbox="images/webapp-create-key2.png":::

4. اكتب معرف التطبيق الخاص بك:

   - في صفحة التطبيق، انتقل إلى **Overview** وانسخ المعلومات التالية:

     :::image type="content" source="images/app-id.png" alt-text="معرف تطبيق الإنشاء" lightbox="images/app-id.png":::

5. أضف التطبيق إلى مستأجر العميل.

   تحتاج إلى الموافقة على التطبيق الخاص بك في كل مستأجر عميل حيث تنوي استخدامه. وذلك لأن تطبيقك يتفاعل مع تطبيق Microsoft Defender لنقطة النهاية نيابة عن العميل.

   يحتاج مستخدم يمتلك **"المسؤول العام** " من مستأجر العميل إلى تحديد ارتباط الموافقة والموافقة على طلبك.

   ارتباط الموافقة هو من النموذج:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```

   حيث يجب استبدال 000000000-0000-0000-0000000000000 بمعرف التطبيق الخاص بك

   بعد النقر فوق ارتباط الموافقة، قم بتسجيل الدخول باستخدام المسؤول العام لمستأجر العميل والموافقة على التطبيق.

   :::image type="content" source="images/app-consent-partner.png" alt-text="الزر &quot;قبول&quot;" lightbox="images/app-consent-partner.png":::

   بالإضافة إلى ذلك، ستحتاج إلى طلب معرف المستأجر الخاص بالعميل وحفظه للاستخدام في المستقبل عند الحصول على الرمز المميز.

6. **القيام به!** لقد قمت بتسجيل تطبيق بنجاح! راجع الأمثلة أدناه للحصول على الرمز المميز والتحقق من صحته.

## <a name="get-an-access-token-example"></a>الحصول على مثال على رمز مميز للوصول

**ملاحظه:** للحصول على رمز الوصول نيابة عن العميل الخاص بك، استخدم معرف المستأجر الخاص بالعميل على عمليات الاستحواذ على الرمز المميز التالي.

لمزيد من المعلومات حول الرمز المميز AAD (دليل Azure النشط)، راجع [AAD (دليل Azure النشط) البرنامج التعليمي](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds)

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

> تم اختبار التعليمات البرمجية أدناه باستخدام Nuget Microsoft.IdentityModel.Clients.ActiveDirectory

- إنشاء تطبيق وحدة تحكم جديد
- تثبيت NuGet [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/)
- إضافة ما يلي باستخدام

    ```console
    using Microsoft.IdentityModel.Clients.ActiveDirectory;
    ```

- نسخ/لصق التعليمات البرمجية أدناه في التطبيق الخاص بك (لا تنس تحديث المتغيرات الثلاثة: `tenantId`، `appId`و `appSecret`)

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

### <a name="using-curl"></a>استخدام Curl

> [!NOTE]
> الإجراء أدناه المفترض أن Curl ل Windows مثبت بالفعل على الكمبيوتر

- فتح نافذة أوامر
- تعيين CLIENT_ID إلى معرف تطبيق Azure
- تعيين CLIENT_SECRET إلى سر تطبيق Azure
- تعيين TENANT_ID إلى معرف مستأجر Azure للعميل الذي يريد استخدام تطبيقك للوصول إلى تطبيق Microsoft Defender لنقطة النهاية
- تشغيل الأمر أدناه:

```curl
curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://securitycenter.onmicrosoft.com/windowsatpservice/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
```

ستحصل على إجابة النموذج:

```console
{"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
```

## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

التحقق من السلامة للتأكد من أن لديك رمزا مميزا صحيحا:

- نسخ/لصق في [JWT](https://jwt.ms) الرمز المميز الذي تحصل عليه في الخطوة السابقة من أجل فك ترميزه
- التحقق من صحة حصولك على مطالبة "الأدوار" بالأذونات المطلوبة
- في لقطة الشاشة أدناه، يمكنك مشاهدة رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق مع أذونات متعددة Microsoft Defender لنقطة النهاية:
- المطالبة "tid" هي معرف المستأجر الذي ينتمي إليه الرمز المميز.

:::image type="content" source="images/webapp-decoded-token.png" alt-text="صفحة التحقق من صحة الرمز المميز" lightbox="images/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>استخدام الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية

- اختر واجهة برمجة التطبيقات التي تريد استخدامها، لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية المعتمدة](exposed-apis-list.md)
- تعيين رأس التخويل في طلب Http الذي ترسله إلى "Bearer {token}" (Bearer هو نظام التخويل)
- وقت انتهاء صلاحية الرمز المميز هو ساعة واحدة (يمكنك إرسال أكثر من طلب واحد بنفس الرمز المميز)

- مثال على إرسال طلب للحصول على قائمة بالتنبيهات **باستخدام C#**

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
