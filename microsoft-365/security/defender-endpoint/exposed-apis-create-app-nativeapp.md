---
title: استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية
ms.reviewer: ''
description: تعرف على كيفية تصميم تطبيق Windows الأصلي للحصول على وصول برمجي إلى Microsoft Defender لنقطة النهاية بدون مستخدم.
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
ms.openlocfilehash: f6cc0ea9cac46fa2e6ad2b5fe56422683d4a3e28
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63573345"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Defender for Endpoint نيابة عن المستخدم.

إذا كنت بحاجة إلى الوصول برمجيا إلى Microsoft Defender لنقطة النهاية بدون مستخدم، فحدد [الوصول إلى Microsoft Defender ل Endpoint باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md).

إذا لم تكن متأكدا من الوصول الذي تحتاج إليه، فاقرأ [صفحة المقدمة](apis-intro.md).

يعرض Microsoft Defender ل Endpoint الكثير من بياناته والإجراءات الخاصة به من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. ستمكنك واجهات برمجة التطبيقات هذه من أتمتة تدفقات العمل وابتعازها استنادا إلى قدرات نقطة النهاية ل Microsoft Defender. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء AAD (دليل Azure النشط) جديد
- الحصول على رمز وصول مميز باستخدام هذا التطبيق
- استخدام الرمز المميز للوصول إلى Defender for Endpoint API

تشرح هذه الصفحة كيفية إنشاء تطبيق AAD (دليل Azure النشط)، والحصول على رمز وصول مميز إلى Microsoft Defender ل Endpoint والتحقق من صحة الرمز المميز.

> [!NOTE]
> عند الوصول إلى Microsoft Defender ل API لنقطة النهاية نيابة عن المستخدم، ستحتاج إلى إذن التطبيق الصحيح وإذن المستخدم.
> إذا لم تكن ملما باستخدام أذونات المستخدم على Microsoft Defender لنقطة النهاية، فاطلع على [إدارة الوصول إلى المدخل باستخدام التحكم بالوصول المستند إلى الدور](rbac.md).

> [!TIP]
> إذا كان لديك الإذن لتنفيذ إجراء في المدخل، لديك الإذن لتنفيذ الإجراء في API.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل دخولك إلى [Azure](https://portal.azure.com) باستخدام حساب مستخدم له **دور المسؤول** العام.

2. انتقل إلى **تسجيلات تطبيق Azure Active Directory** \>  \> **تسجيل جديد**.

   :::image type="content" alt-text="صورة Microsoft Azure والتنقل إلى تسجيل التطبيق." source="images/atp-azure-new-app2.png" lightbox="images/atp-azure-new-app2.png":::

3. عندما تظهر **صفحة تسجيل** تطبيق، أدخل معلومات تسجيل التطبيق:
   - **الاسم** - أدخل اسم تطبيق ذا معنى سيتم عرضه لمستخدمي التطبيق.
   - **أنواع الحسابات المعتمدة** - حدد الحسابات التي تريد أن يدعمها التطبيق.

     <br>

     |أنواع الحسابات المعتمدة|الوصف|
     |---|---|
     |**الحسابات في دليل المؤسسة هذا فقط**|حدد هذا الخيار إذا كنت تقوم ببناء تطبيق خط العمل (LOB). لا يتوفر هذا الخيار إذا كنت لا تقوم بتسجيل التطبيق في دليل. <p> يتم تحديد هذا الخيار إلى Azure AD فقط لمستأجر واحد. <p> هذا هو الخيار الافتراضي إلا إذا كنت تقوم بتسجيل التطبيق خارج الدليل. في الحالات التي يكون فيها التطبيق مسجلا خارج الدليل، يكون الإعداد الافتراضي هو Azure AD متعدد المستأجرين وحسابات Microsoft الشخصية.|
     |**الحسابات في أي دليل هيكلي**|حدد هذا الخيار إذا كنت تريد استهداف جميع عملاء الأعمال والتعليم. <p> يتم تحديد هذا الخيار لمستأجر Azure AD متعدد المستأجرين فقط. <p> إذا قمت بتسجيل التطبيق كمستأجر واحد فقط من Azure AD، يمكنك تحديثه لكي يكون Azure AD متعدد المستأجرين ثم العودة إلى مستأجر واحد من خلال ريشة **المصادقة** .|
     |**الحسابات في أي دليل هيكلي وحسابات Microsoft الشخصية**|حدد هذا الخيار لاستهداف أوسع مجموعة من العملاء. <p> يتم تحديد هذا الخيار إلى حسابات Azure AD متعددة المستأجرين والحسابات الشخصية في Microsoft. <p> إذا قمت بتسجيل التطبيق ك Azure AD متعدد المستأجرين وحسابات Microsoft الشخصية، فلا يمكنك تغيير ذلك في واجهة المستخدم. بدلا من ذلك، يجب استخدام محرر بيان التطبيق لتغيير أنواع الحسابات المعتمدة.|

   - **إعادة توجيه URI (** اختياري) - حدد نوع التطبيق الذي تقوم ببناءه  أو عميل ويب أو عام **(سطح مكتب & mobile)** ، ثم أدخل عنوان URL إعادة التوجيه (أو عنوان URL للرد) للتطبيق.

     - بالنسبة لتطبيقات الويب، يمكنك توفير عنوان URL الأساسي لتطبيقك. على سبيل المثال `http://localhost:31544` ، قد يكون عنوان URL لتطبيق ويب يعمل على جهازك المحلي. سيستخدم المستخدمون عنوان URL هذا في تسجيل الدخول إلى تطبيق عميل ويب.

     - بالنسبة إلى تطبيقات العميل العامة، يجب توفير URI المستخدم بواسطة Azure AD لإرجاع استجابات الرموز المميزة. أدخل قيمة خاصة بتطبيقك، مثل `myapp://auth`.

     لرؤية أمثلة محددة حول تطبيقات الويب أو التطبيقات الأصلية، اطلع على [تطبيقاتنا السريعة](/azure/active-directory/develop/#quickstarts).

     عند الانتهاء، حدد **تسجيل**.

4. السماح لتطبيقك بالوصول إلى Microsoft Defender لنقطة النهاية وتعيين إذن "قراءة التنبيهات":

   - في صفحة التطبيق، حدد أذونات **API** \>  \> إضافة أذونات واجهات برمجة التطبيقات التي تستخدمها > **نوع WindowsDefenderATP** وحدد على **WindowsDefenderATP**.

     > [!NOTE]
     > *لا يظهر WindowsDefenderATP* في القائمة الأصلية. ابدأ بكتابة اسمه في مربع النص لكي يظهر.

     :::image type="content" alt-text="إضافة إذن." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - اختر **الأذونات المفوضة** \> **تنبيه.اقرأ >** حدد **إضافة أذونات**.

      :::image type="content" alt-text="أذونات التطبيق." source="images/application-permissions-public-client.png" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > حدد الأذونات ذات الصلة. تنبيهات القراءة مثال فقط.

     على سبيل المثال:

     - لتشغيل [الاستعلامات المتقدمة،](run-advanced-query-api.md) حدد **تشغيل إذن الاستعلامات** المتقدمة.
     - [لعزل جهاز،](isolate-machine.md) حدد **عزل إذن** الجهاز.
     - لتحديد الإذن الذي تحتاج إليه **، اشاهد** مقطع الأذونات في API الذي تريد الاتصال به.

   - حدد **منح الموافقة**.

      > [!NOTE]
      > في كل مرة تضيف فيها إذنا، يجب أن تحدد عند **منح الموافقة** على الإذن الجديد لكي يتم التنفيذ.

      ![صورة لمنح الأذونات.](images/grant-consent.png)

5. اكتب "معرّف التطبيق" وم ID المستأجر.

    على صفحة التطبيق، انتقل إلى **نظرة عامة** ونسخ المعلومات التالية:

    :::image type="content" alt-text="صورة لم id التطبيق الذي تم إنشاؤه." source="images/app-and-tenant-ids.png" lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>الحصول على رمز وصول مميز

لمزيد من المعلومات حول AAD (دليل Azure النشط) المميزة، راجع [البرنامج التعليمي Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>استخدام C\#

- نسخ/لصق الفئة أدناه في التطبيق.
- استخدم **أسلوب AcquireUserTokenAsync** مع "معرّف التطبيق" و"مستأجر" و"اسم المستخدم" وكلمة المرور للحصول على رمز مميز.

    ```csharp
    namespace WindowsDefenderATP
    {
        using System.Net.Http;
        using System.Text;
        using System.Threading.Tasks;
        using Newtonsoft.Json.Linq;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            private const string WdatpResourceId = "https://api.securitycenter.microsoft.com";

            public static async Task<string> AcquireUserTokenAsync(string username, string password, string appId, string tenantId)
            {
                using (var httpClient = new HttpClient())
                {
                    var urlEncodedBody = $"resource={WdatpResourceId}&client_id={appId}&grant_type=password&username={username}&password={password}";

                    var stringContent = new StringContent(urlEncodedBody, Encoding.UTF8, "application/x-www-form-urlencoded");

                    using (var response = await httpClient.PostAsync($"{Authority}/{tenantId}/oauth2/token", stringContent).ConfigureAwait(false))
                    {
                        response.EnsureSuccessStatusCode();

                        var json = await response.Content.ReadAsStringAsync().ConfigureAwait(false);

                        var jObject = JObject.Parse(json);

                        return jObject["access_token"].Value<string>();
                    }
                }
            }
        }
    }
    ```

## <a name="validate-the-token"></a>التحقق من صحة الرمز المميز

تحقق للتأكد من أنك حصلت على رمز مميز صحيح:

- انسخ/الصق الرمز المميز الذي حصلت عليه في الخطوة السابقة في [JWT](https://jwt.ms) لكي تتمكن من فك ترميزه.
- تحقق من صحة الحصول على مطالبة 'scp' مع أذونات التطبيق المطلوبة.
- في لقطة الشاشة أدناه، يمكنك رؤية رمز مميز تم فك تشفيره تم الحصول عليه من التطبيق في البرنامج التعليمي:

  :::image type="content" alt-text="صورة التحقق من صحة الرمز المميز." source="images/nativeapp-decoded-token.png" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>استخدام الرمز المميز للوصول إلى Microsoft Defender ل API لنقطة النهاية

- اختر واجهات برمجة التطبيقات التي تريد استخدامها - [واجهات برمجة التطبيقات المعتمدة ل Microsoft Defender لنقطة النهاية](exposed-apis-list.md).
- قم بتعيين رأس التخويل في طلب HTTP الذي ترسله إلى "حامل {token}" (إن Bearer هو نظام التخويل).
- وقت انتهاء صلاحية الرمز المميز هو ساعة واحدة (يمكنك إرسال أكثر من طلب واحد بنفس الرمز المميز).

- مثال لإرسال طلب للحصول على قائمة تنبيهات **باستخدام C#**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>راجع أيضًا

- [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](exposed-apis-list.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md)
