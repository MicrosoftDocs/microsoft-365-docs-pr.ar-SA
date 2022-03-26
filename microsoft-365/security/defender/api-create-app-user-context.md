---
title: إنشاء تطبيق للوصول Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم
description: تعرف على كيفية الوصول Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم.
keywords: الوصول، نيابة عن المستخدم، واجهة برمجة التطبيقات، التطبيق، المستخدم، رمز الوصول المميز، الرمز المميز،
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
ms.openlocfilehash: 88b1bc6c46296e3694ef53ae733955a1491b21c7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63570193"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>إنشاء تطبيق للوصول Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Microsoft 365 Defender نيابة عن مستخدم واحد.

إذا كنت بحاجة إلى الوصول Microsoft 365 Defender بدون مستخدم محدد (على سبيل المثال، إذا كنت تكتب تطبيق خلفية أو daemon)، فشاهد إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون [مستخدم](api-create-app-web.md). إذا كنت بحاجة إلى توفير الوصول لمستأجرين متعددين — على سبيل المثال، إذا كنت تعمل في مؤسسة كبيرة أو مجموعة من العملاء — فشاهد إنشاء تطبيق مع وصول الشريك [إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-partner-access.md). إذا لم تكن متأكدا من نوع الوصول الذي تحتاج إليه، فشاهد [بدء العمل](api-access.md).

Microsoft 365 Defender البيانات والإجراءات من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. تساعدك واجهات برمجة التطبيقات هذه على أتمتة مهام سير العمل واستخدام Microsoft 365 Defender الخاصة بها. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات التالية:

- إنشاء تطبيق Azure Active Directory (Azure AD).
- احصل على رمز وصول مميز باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى Microsoft 365 Defender API.

تشرح هذه المقالة كيفية:

- إنشاء تطبيق Azure AD
- احصل على رمز وصول مميز Microsoft 365 Defender
- التحقق من صحة الرمز المميز

> [!NOTE]
> عند الوصول إلى Microsoft 365 Defender API نيابة عن المستخدم، ستحتاج إلى أذونات التطبيق وأذونات المستخدم الصحيحة.

> [!TIP]
> إذا كان لديك الإذن لتنفيذ إجراء في المدخل، لديك الإذن لتنفيذ الإجراء في API.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل الدخول إلى [Azure](https://portal.azure.com) كمستخدم باستخدام **دور المسؤول** العام.

2. انتقل إلى **تسجيلات Azure Active DirectoryApp** >  >  **التسجيل الجديد**.

   ![صورة Microsoft Azure والتنقل إلى تسجيل التطبيق.](../../media/atp-azure-new-app2.png)

3. في النموذج، اختر اسما للتطبيق وأدخل المعلومات التالية لمعاينة إعادة التوجيه، ثم حدد **تسجيل**.

   ![صورة نافذة إنشاء تطبيق.](../../media/nativeapp-create2.PNG)

   - **نوع التطبيق:** عميل عام
   - **إعادة توجيه URI:** https://portal.azure.com

4. في صفحة التطبيق الخاصة بك، حدد أذونات **APIAdd** >  **permissionAPIs** >  **تستخدم >**، وا اكتب الحماية من المخاطر من **Microsoft**، وحدد **الحماية من المخاطر من Microsoft**. يمكن لتطبيقك الآن الوصول إلى Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* هو اسم سابق Microsoft 365 Defender، ولن يظهر في القائمة الأصلية. ستحتاج إلى بدء كتابة اسمه في مربع النص لكي يظهر.

   ![صورة تحديد أذونات API.](../../media/apis-in-my-org-tab.PNG)

   - اختر **الأذونات المفوضة**. اختر الأذونات ذات الصلة في السيناريو (على سبيل المثال **Incident.Read**)، ثم حدد **إضافة أذونات**.

   ![صورة الوصول إلى API واختيار API.](../../media/request-api-permissions-delegated.PNG)

    > [!NOTE]
    > أنت بحاجة إلى تحديد الأذونات ذات الصلة في السيناريو الخاص بك. *ما عليك سوى قراءة كل* الأحداث كمثال. لتحديد الإذن الذي تحتاج إليه، يرجى الاطلاع على قسم **الأذونات** في API الذي تريد الاتصال به.
    >
    > على سبيل المثال، لتشغيل [استعلامات متقدمة](api-advanced-hunting.md)، حدد الإذن "تشغيل الاستعلامات المتقدمة"؛ [لعزل جهاز،](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine) حدد الإذن 'عزل الجهاز'.

5. حدد **منح موافقة المسؤول**. في كل مرة تضيف فيها إذنا، يجب تحديد **منح موافقة** المسؤول لكي يتم هذا الأمر.

   ![صورة لمنح الأذونات.](../../media/grant-consent-delegated.PNG)

6. سجل "رقم التطبيق" وم ID المستأجر الخاص بك في مكان آمن. يتم سردها ضمن **نظرة عامة** على صفحة التطبيق.

   ![صورة لم id التطبيق الذي تم إنشاؤه.](../../media/app-and-tenant-ids.png)

## <a name="get-an-access-token"></a>الحصول على رمز وصول مميز

لمزيد من المعلومات حول رموز Azure Active Directory المميزة، راجع البرنامج التعليمي [Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-using-powershell"></a>الحصول على رمز وصول مميز باستخدام PowerShell

```PowerShell
if(!(Get-Package adal.ps)) { Install-Package -Name adal.ps } # Install the ADAL.PS package in case it's not already present

$tenantId = '' # Paste your directory (tenant) ID here.
$clientId = '' # Paste your application (client) ID here.
$redirectUri = '' # Paste your app's redirection URI

$authority = "https://login.windows.net/$tenantId"
$resourceUrl = 'https://api.security.microsoft.com'

$response = Get-ADALToken -Resource $resourceUrl -ClientId $clientId -RedirectUri $redirectUri -Authority $authority -PromptBehavior:Always
$response.AccessToken | clip

$response.AccessToken
```

## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

1. انسخ الرمز المميز والصقه في [JWT](https://jwt.ms) لفك ترميزه.
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
- [إنشاء تطبيق مع وصول شريك متعدد المستأجرين إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-partner-access.md)
- [التعرف على حدود API والترخيص](api-terms.md)
- [فهم رموز الخطأ](api-error-codes.md)
- [تخويل OAuth 2.0 تسجيل دخول المستخدم والوصول إلى API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
