---
title: استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: تعرف على كيفية تصميم تطبيق Windows أصلي للوصول البرمجي إلى Microsoft Defender لنقطة النهاية بدون مستخدم.
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
ms.openlocfilehash: aec4c7bdc0da76a6a52a8b8f19d89b8b54f3df9f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173480"
---
# <a name="use-microsoft-defender-for-endpoint-apis"></a>استخدام واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> لا يتم تضمين قدرات التتبع المتقدمة في Defender for Business. راجع [مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تصف هذه الصفحة كيفية إنشاء تطبيق للحصول على وصول برمجي إلى Defender لنقطة النهاية نيابة عن مستخدم.

إذا كنت بحاجة إلى الوصول البرمجي Microsoft Defender لنقطة النهاية بدون مستخدم، فراجع [Access Microsoft Defender لنقطة النهاية مع سياق التطبيق](exposed-apis-create-app-webapp.md).

إذا لم تكن متأكدا من الوصول الذي تحتاجه، فاقرأ [صفحة "مقدمة](apis-intro.md)".

Microsoft Defender لنقطة النهاية يكشف الكثير من بياناته وإجراءاته من خلال مجموعة من واجهات برمجة التطبيقات البرمجية. ستمكنك واجهات برمجة التطبيقات هذه من أتمتة تدفقات العمل والابتكار استنادا إلى قدرات Microsoft Defender لنقطة النهاية. يتطلب الوصول إلى واجهة برمجة التطبيقات مصادقة OAuth2.0. لمزيد من المعلومات، راجع [التعليمة البرمجية للتخويل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء تطبيق AAD (دليل Azure النشط)
- الحصول على رمز مميز للوصول باستخدام هذا التطبيق
- استخدام الرمز المميز للوصول إلى Defender لواجهة برمجة تطبيقات نقطة النهاية

تشرح هذه الصفحة كيفية إنشاء تطبيق AAD (دليل Azure النشط)، والحصول على رمز وصول مميز Microsoft Defender لنقطة النهاية والتحقق من صحة الرمز المميز.

> [!NOTE]
> عند الوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية نيابة عن مستخدم، ستحتاج إلى إذن التطبيق الصحيح وإذن المستخدم.
> إذا لم تكن على دراية بأذونات المستخدم على Microsoft Defender لنقطة النهاية، فراجع [إدارة الوصول إلى المدخل باستخدام التحكم في الوصول المستند إلى الدور](rbac.md).

> [!TIP]
> إذا كان لديك الإذن لتنفيذ إجراء في المدخل، فلديك الإذن لتنفيذ الإجراء في واجهة برمجة التطبيقات.

## <a name="create-an-app"></a>إنشاء تطبيق

1. سجل الدخول إلى [Azure](https://portal.azure.com) باستخدام حساب مستخدم له دور **المسؤول العام** .

2. انتقل إلى **تسجيلات** \> تطبيق **Azure Active Directory** \> **الجديدة**.

   :::image type="content" source="images/atp-azure-new-app2.png" alt-text="صفحة تسجيلات التطبيق في مدخل Microsoft Azure" lightbox="images/atp-azure-new-app2.png":::

3. عند ظهور صفحة **تسجيل تطبيق** ، أدخل معلومات تسجيل التطبيق الخاص بك:
   - **الاسم** - أدخل اسم تطبيق ذا معنى سيتم عرضه لمستخدمي التطبيق.
   - **أنواع الحسابات المدعومة** - حدد الحسابات التي تريد أن يدعمها تطبيقك.

     <br>

     |أنواع الحسابات المعتمدة|الوصف|
     |---|---|
     |**الحسابات في هذا الدليل التنظيمي فقط**|حدد هذا الخيار إذا كنت تقوم بإنشاء تطبيق خط العمل (LOB). لا يتوفر هذا الخيار إذا كنت لا تسجل التطبيق في دليل. <p> يعين هذا الخيار إلى Azure AD مستأجر واحد فقط. <p> هذا هو الخيار الافتراضي إلا إذا كنت تقوم بتسجيل التطبيق خارج الدليل. في الحالات التي يتم فيها تسجيل التطبيق خارج الدليل، يكون الإعداد الافتراضي Azure AD حسابات Microsoft الشخصية ومتعددة المستأجرين.|
     |**الحسابات في أي دليل تنظيمي**|حدد هذا الخيار إذا كنت ترغب في استهداف جميع عملاء الأعمال والتعليم. <p> يعين هذا الخيار إلى Azure AD متعدد المستأجرين فقط. <p> إذا قمت بتسجيل التطبيق Azure AD مستأجر واحد فقط، يمكنك تحديثه ليكون Azure AD متعدد المستأجرين والعودة إلى مستأجر واحد من خلال **شفرة المصادقة**.|
     |**الحسابات في أي دليل تنظيمي وحسابات Microsoft الشخصية**|حدد هذا الخيار لاستهداف أوسع مجموعة من العملاء. <p> يتم تعيين هذا الخيار Azure AD حسابات Microsoft الشخصية ومتعددة المستأجرين. <p> إذا قمت بتسجيل التطبيق Azure AD حسابات Microsoft الشخصية ومتعددة المستأجرين، فلا يمكنك تغيير هذا في واجهة المستخدم. بدلا من ذلك، يجب استخدام محرر بيان التطبيق لتغيير أنواع الحسابات المعتمدة.|

   - **إعادة توجيه URI (اختياري)** - حدد نوع التطبيق الذي تقوم ببنائك أو **عميل ويب** أو **عميل عام (mobile & desktop)**، ثم أدخل عنوان URL لإعادة التوجيه (أو عنوان URL للرد) للتطبيق الخاص بك.

     - بالنسبة لتطبيقات الويب، قم بتوفير عنوان URL الأساسي لتطبيقك. على سبيل المثال، `http://localhost:31544` قد يكون عنوان URL لتطبيق ويب يعمل على جهازك المحلي. سيستخدم المستخدمون عنوان URL هذا لتسجيل الدخول إلى تطبيق عميل ويب.

     - بالنسبة لتطبيقات العميل العامة، قم بتوفير URI المستخدم من قبل Azure AD لإرجاع استجابات الرمز المميز. أدخل قيمة خاصة بتطبيقك، مثل `myapp://auth`.

     للاطلاع على أمثلة محددة لتطبيقات الويب أو التطبيقات الأصلية، تحقق من [قوالب التشغيل السريع](/azure/active-directory/develop/#quickstarts) الخاصة بنا.

     عند الانتهاء، حدد **"تسجيل**".

4. السماح للتطبيق بالوصول إلى Microsoft Defender لنقطة النهاية وتعيين إذن "قراءة التنبيهات":

   - في صفحة التطبيق، حدد **API Permissions** \> **Add permission** \> **APIs التي تستخدمها مؤسستي** > نوع **WindowsDefenderATP** وحدد على **WindowsDefenderATP**.

     > [!NOTE]
     > لا يظهر *WindowsDefenderATP* في القائمة الأصلية. ابدأ بكتابة اسمه في مربع النص لكي يظهر.

     :::image type="content" alt-text="إضافة إذن." source="images/add-permission.png" lightbox="images/add-permission.png":::

   - اختر **Alert.Read** **للأذونات المفوضة** \> > حدد **"إضافة أذونات**".

      :::image type="content" source="images/application-permissions-public-client.png" alt-text="أجزاء نوع التطبيق والأذونات" lightbox="images/application-permissions-public-client.png":::

   > [!IMPORTANT]
   > حدد الأذونات ذات الصلة. تعد قراءة التنبيهات مثالا فقط.

     على سبيل المثال:

     - [لتشغيل الاستعلامات المتقدمة](run-advanced-query-api.md)، حدد إذن **تشغيل الاستعلامات المتقدمة**.
     - [لعزل جهاز](isolate-machine.md)، حدد **"عزل إذن الجهاز**".
     - لتحديد الإذن الذي تحتاجه، اعرض قسم **الأذونات** في واجهة برمجة التطبيقات التي تريد الاتصال بها.

   - حدد **منح الموافقة**.

      > [!NOTE]
      > في كل مرة تضيف فيها إذنا، يجب تحديد منح **الموافقة** لكي يدخل الإذن الجديد حيز التنفيذ.

      :::image type="content" source="images/grant-consent.png" alt-text="خيار موافقة المسؤول الكبير" lightbox="images/grant-consent.png":::

5. اكتب معرف التطبيق الخاص بك ومعرف المستأجر الخاص بك.

    في صفحة التطبيق، انتقل إلى **Overview** وانسخ المعلومات التالية:

    :::image type="content" source="images/app-and-tenant-ids.png" alt-text="معرف التطبيق الذي تم إنشاؤه"  lightbox="images/app-and-tenant-ids.png":::

## <a name="get-an-access-token"></a>الحصول على رمز مميز للوصول

لمزيد من المعلومات حول الرموز المميزة AAD (دليل Azure النشط)، راجع [البرنامج التعليمي Azure AD](/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### <a name="using-c"></a>استخدام C\#

- نسخ/لصق الفئة أدناه في التطبيق الخاص بك.
- استخدم أسلوب **AcquireUserTokenAsync** مع معرف التطبيق ومعرف المستأجر واسم المستخدم وكلمة المرور للحصول على رمز مميز.

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

تحقق للتأكد من حصولك على رمز مميز صحيح:

- نسخ/لصق في [JWT](https://jwt.ms) الرمز المميز الذي حصلت عليه في الخطوة السابقة من أجل فك ترميزه.
- تحقق من صحة حصولك على مطالبة 'scp' باستخدام أذونات التطبيق المطلوبة.
- في لقطة الشاشة أدناه يمكنك مشاهدة رمز مميز تم فك تشفيره تم الحصول عليه من التطبيق في البرنامج التعليمي:

  :::image type="content" source="images/nativeapp-decoded-token.png" alt-text="صفحة التحقق من صحة الرمز المميز" lightbox="images/nativeapp-decoded-token.png":::

## <a name="use-the-token-to-access-microsoft-defender-for-endpoint-api"></a>استخدام الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية

- اختر واجهة برمجة التطبيقات التي تريد استخدامها - [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية المدعومة](exposed-apis-list.md).
- قم بتعيين رأس التخويل في طلب HTTP الذي ترسله إلى "Bearer {token}" (Bearer هو نظام التخويل).
- وقت انتهاء صلاحية الرمز المميز هو ساعة واحدة (يمكنك إرسال أكثر من طلب واحد بنفس الرمز المميز).

- مثال على إرسال طلب للحصول على قائمة بالتنبيهات **باستخدام C#**:

    ```csharp
    var httpClient = new HttpClient();

    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.securitycenter.microsoft.com/api/alerts");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
    ```

## <a name="see-also"></a>راجع أيضًا

- [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](exposed-apis-list.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية مع سياق التطبيق](exposed-apis-create-app-webapp.md)
