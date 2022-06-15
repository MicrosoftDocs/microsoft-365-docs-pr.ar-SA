---
title: إنشاء تطبيق للوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender نيابة عن مستخدم
description: تعرف على كيفية الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender نيابة عن مستخدم.
keywords: الوصول، نيابة عن المستخدم، واجهة برمجة التطبيقات، التطبيق، المستخدم، الرمز المميز للوصول، الرمز المميز،
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
ms.openlocfilehash: 41f2763d73bbb9ed0b7ae32dce431cb2c1a4d71f
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102581"
---
# <a name="create-an-app-to-access-microsoft-365-defender-apis-on-behalf-of-a-user"></a>إنشاء تطبيق للوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender نيابة عن مستخدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Microsoft 365 Defender نيابة عن مستخدم واحد.

إذا كنت بحاجة إلى وصول برمجي إلى Microsoft 365 Defender بدون مستخدم محدد (على سبيل المثال، إذا كنت تكتب تطبيق خلفية أو برنامج خفي)، فراجع [إنشاء تطبيق للوصول إلى Microsoft 365 Defender دون مستخدم](api-create-app-web.md). إذا كنت بحاجة إلى توفير الوصول لمستأجرين متعددين، على سبيل المثال، إذا كنت تخدم مؤسسة كبيرة أو مجموعة من العملاء، فراجع [إنشاء تطبيق مع وصول الشريك إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-partner-access.md). إذا لم تكن متأكدا من نوع الوصول الذي تحتاجه، فراجع ["بدء الاستخدام](api-access.md)".

Microsoft 365 Defender يكشف الكثير من بياناته وإجراءاته من خلال مجموعة من واجهات برمجة التطبيقات البرمجية. تساعدك واجهات برمجة التطبيقات هذه على أتمتة مهام سير العمل والاستفادة من قدرات Microsoft 365 Defender. يتطلب الوصول إلى واجهة برمجة التطبيقات هذا مصادقة OAuth2.0. لمزيد من المعلومات، راجع [التعليمة البرمجية للتخويل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات هذه:

- إنشاء تطبيق Azure Active Directory (Azure AD).
- احصل على رمز مميز للوصول باستخدام هذا التطبيق.
- استخدم الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft 365 Defender.

تشرح هذه المقالة كيفية:

- إنشاء تطبيق Azure AD
- الحصول على رمز مميز للوصول إلى Microsoft 365 Defender
- التحقق من صحة الرمز المميز

> [!NOTE]
> عند الوصول إلى واجهة برمجة تطبيقات Microsoft 365 Defender نيابة عن مستخدم، ستحتاج إلى أذونات التطبيق وأذونات المستخدم الصحيحة.

> [!TIP]
> إذا كان لديك الإذن لتنفيذ إجراء في المدخل، فلديك الإذن لتنفيذ الإجراء في واجهة برمجة التطبيقات.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل الدخول إلى [Azure](https://portal.azure.com) كمستخدم باستخدام دور **المسؤول العام** .

2. انتقل إلى **تسجيلات** >  تطبيق **Azure Active Directory** > **الجديدة**.

   :::image type="content" source="../../media/atp-azure-new-app2.png" alt-text="خيار التسجيل الجديد في الجزء &quot;إدارة&quot; في مدخل Azure" lightbox="../../media/atp-azure-new-app2.png":::

3. في النموذج، اختر اسما للتطبيق الخاص بك وأدخل المعلومات التالية ل URI إعادة التوجيه، ثم حدد **"تسجيل**".

   :::image type="content" source="../../media/nativeapp-create2.PNG" alt-text="جزء تسجيل التطبيق في مدخل Azure" lightbox="../../media/nativeapp-create2.PNG":::
   

   - **نوع التطبيق:** العميل العام
   - **إعادة توجيه URI:** https://portal.azure.com

4. في صفحة التطبيق، حدد **API Permissions** > **Add permission** > **APIs التي تستخدمها مؤسستي** >، واكتب **Microsoft Threat Protection**، وحدد **Microsoft Threat Protection**. يمكن لتطبيقك الآن الوصول إلى Microsoft 365 Defender.

   > [!TIP]
   > *Microsoft Threat Protection* هو اسم سابق Microsoft 365 Defender، ولن يظهر في القائمة الأصلية. يجب أن تبدأ بكتابة اسمه في مربع النص لكي يظهر.

   :::image type="content" source="../../media/apis-in-my-org-tab.PNG" alt-text="جزء واجهات برمجة التطبيقات لمؤسستك في مدخل Microsoft 365 Defender" lightbox="../../media/apis-in-my-org-tab.PNG":::

   - اختر **الأذونات المفوضة**. اختر الأذونات ذات الصلة للسيناريو (على سبيل المثال **Incident.Read**)، ثم حدد **"Add permissions**".

     :::image type="content" source="../../media/request-api-permissions-delegated.PNG" alt-text="جزء الأذونات المفوضة في مدخل Microsoft 365 Defender" lightbox="../../media/request-api-permissions-delegated.PNG":::

    > [!NOTE]
    > تحتاج إلى تحديد الأذونات ذات الصلة للسيناريو الخاص بك. *قراءة جميع الحوادث* هي مجرد مثال. لتحديد الإذن الذي تحتاج إليه، يرجى مراجعة قسم **الأذونات** في واجهة برمجة التطبيقات التي تريد الاتصال بها.
    >
    > على سبيل المثال، [لتشغيل الاستعلامات المتقدمة](api-advanced-hunting.md)، حدد إذن "تشغيل الاستعلامات المتقدمة"؛ [لعزل جهاز](/windows/security/threat-protection/microsoft-defender-atp/isolate-machine)، حدد إذن "عزل الجهاز".

5. حدد **منح موافقة المسؤول**. في كل مرة تضيف فيها إذنا، يجب تحديد **منح موافقة المسؤول** لكي يدخل حيز التنفيذ.

   :::image type="content" source="../../media/grant-consent-delegated.PNG" alt-text="جزء منح موافقة المسؤول في مدخل Microsoft 365 Defender" lightbox="../../media/grant-consent-delegated.PNG":::

6. سجل معرف التطبيق الخاص بك ومعرف المستأجر الخاص بك في مكان آمن. يتم سردها ضمن **نظرة عامة** على صفحة التطبيق الخاص بك.

   :::image type="content" source="../../media/app-and-tenant-ids.png" alt-text="جزء النظرة العامة في مدخل Microsoft 365 Defender" lightbox="../../media/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>الحصول على رمز مميز للوصول

لمزيد من المعلومات حول الرموز المميزة ل Azure Active Directory، راجع [البرنامج التعليمي Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="get-an-access-token-on-behalf-of-a-user-using-powershell"></a>الحصول على رمز مميز للوصول نيابة عن مستخدم يستخدم PowerShell

استخدم مكتبة MSAL.PS للحصول على رموز الوصول المميزة ذات الأذونات المفوضة. قم بتشغيل الأوامر التالية للحصول على رمز الوصول المميز نيابة عن مستخدم:

```PowerShell
Install-Module -Name MSAL.PS # Install the MSAL.PS module from PowerShell Gallery

$TenantId = " " # Paste your directory (tenant) ID here.
$AppClientId="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" # Paste your application (client) ID here.

$MsalParams = @{
   ClientId = $AppClientId
   TenantId = $TenantId
   Scopes   = 'https://graph.microsoft.com/User.Read.All','https://graph.microsoft.com/Files.ReadWrite'
}

$MsalResponse = Get-MsalToken @MsalParams
$AccessToken  = $MsalResponse.AccessToken
 
$AccessToken # Display the token in PS console
```
## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

1. انسخ الرمز المميز والصقه في [JWT](https://jwt.ms) لفك ترميزه.
2. تأكد من أن المطالبة *بالأدوار* داخل الرمز المميز الذي تم فك تشفيره يحتوي على الأذونات المطلوبة.

في الصورة التالية، يمكنك مشاهدة رمز مميز تم فك تشفيره تم الحصول عليه من تطبيق، باستخدام ```Incidents.Read.All```، ```Incidents.ReadWrite.All```وأذونات ```AdvancedHunting.Read.All``` :

:::image type="content" source="../../media/defender-endpoint/webapp-decoded-token.png" alt-text="قسم الأذونات في جزء الرمز المميز الذي تم فك ترميزه في مدخل Microsoft 365 Defender" lightbox="../../media/defender-endpoint/webapp-decoded-token.png":::

## <a name="use-the-token-to-access-the-microsoft-365-defender-api"></a>استخدم الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft 365 Defender

1. اختر واجهة برمجة التطبيقات التي تريد استخدامها (الحوادث أو التتبع المتقدم). لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات Microsoft 365 Defender المعتمدة](api-supported.md).
2. في طلب http الذي أنت على وشك إرساله، قم بتعيين رأس التخويل إلى `"Bearer" <token>`، و *Bearer* هو نظام التخويل ، *والرمز المميز* الذي تم التحقق من صحته.
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
- [إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم](api-create-app-web.md)
- [إنشاء تطبيق مع وصول شريك متعدد المستأجرين إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-partner-access.md)
- [التعرف على حدود واجهة برمجة التطبيقات والترخيص](api-terms.md)
- [فهم رموز الأخطاء](api-error-codes.md)
- [تخويل OAuth 2.0 لتسجيل دخول المستخدم والوصول إلى واجهة برمجة التطبيقات](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
