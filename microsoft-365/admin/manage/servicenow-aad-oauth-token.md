---
title: تكوين تكامل Microsoft 365 مع رمز Azure AD Auth المميز
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: دليل تكوين وتثبيت تطبيق معتمد النطاق ل ServiceNow.
ms.openlocfilehash: 9f9985e07989f168f9b27dde1c1d574813c3f349
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575112"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>تكوين تكامل Microsoft 365 مع رمز Azure AD Auth المميز

## <a name="prerequisites-azure-ad-auth-token"></a>المتطلبات الأساسية (رمز Azure AD Auth المميز)

هذه المتطلبات الأساسية ضرورية لإعداد Microsoft 365 الدعم.

1. \[AAD (دليل Azure النشط) المسؤول\] إنشاء تطبيق Azure AD للداخل ضمن Microsoft 365 المستأجر.

    1. سجل دخولك إلى مدخل Azure باستخدام Microsoft 365 بيانات اعتماد المستأجر واذهب إلى صفحة تسجيلات التطبيق لإنشاء [](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) تطبيق جديد.

    2. حدد **الحسابات في دليل المؤسسة هذا فقط ({Microsoft-365-tenant-name} فقط – مستأجر واحد)** وحدد **تسجيل**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. انتقل إلى **المصادقة** وحدد **إضافة نظام أساسي**. حدد خيار **ويب** وأدخل عنوان URL لإعادة التوجيه: `https://{your-servicenow-instance``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. احصل على "معر ة عميل التطبيق" وأنشئ سريا للعميل واحصل على تلك القيمة.

1. \[AAD (دليل Azure النشط) المسؤول\] قم بإنشاء تطبيق Azure AD ل API Rest ضمن Microsoft 365 المستأجر.

    1. سجل دخولك إلى [مدخل Azure](https://portal.azure.com/) باستخدام بيانات Microsoft 365 المستأجر واذهب إلى صفحة تسجيلات التطبيق لإنشاء تطبيق جديد.

    1. حدد **الحسابات في دليل المؤسسة هذا فقط {(Microsoft-365-tenant-name} فقط – مستأجر واحد)**.

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. احصل على "معر ة عميل التطبيق" وأنشئ سريا للعميل واحصل على تلك القيمة.

1. \[AAD (دليل Azure النشط) المسؤول\] إنشاء تطبيق Azure AD لمستخدم Rest User ضمن Microsoft 365 المستأجر.

    1. سجل دخولك إلى [مدخل Azure](https://portal.azure.com/) باستخدام بيانات Microsoft 365 المستأجر واذهب إلى صفحة تسجيلات التطبيق لإنشاء تطبيق جديد.

    1. حدد **الحسابات في دليل المؤسسة هذا فقط {(Microsoft-365-tenant-name} فقط – مستأجر واحد)**.

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. احصل على "معر ة عميل التطبيق" وأنشئ سريا للعميل واحصل على تلك القيمة.

1. \[ServiceNow Admin قم\] بإعداد موفر OAuth الصادر في ServiceNow.

    إذا لم يتم تعيين النطاق إلى **عام****&gt;، ففعل ذلك عن طريق الانتقال إلى الإعدادات المطور &gt;** والتبديل إلى **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="واجهة مستخدم رسومية أو نص أو تطبيق أو دردشة أو رسالة نصية يتم إنشاء الوصف تلقائيا":::

1. انتقل إلى **System OAuth &gt; Application Registry**.

1. أنشئ تطبيقا جديدا باستخدام الاتصال **إلى موفر OAuth** جهة خارجية وأدخل هذه القيم:

    - "معرّف العميل": هذا هو "المليكن العميل" للتطبيق الذي تم إنشاؤه في الخطوة 1 من المتطلبات الأساسية (رمز Azure AD Auth المميز \#).

    - سرية العميل: هذه هي القيمة "سرية العميل" للتطبيق الذي تم إنشاؤه في الخطوة 1 من المتطلبات الأساسية (رمز Azure AD Auth المميز \#).

    - نوع المنحة الافتراضية: بيانات اعتماد العميل

    - عنوان URL الرمز المميز: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - عنوان URL إعادة التوجيه: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

1. \[ServiceNow Admin\] لتكوين موفر OIDC في ServiceNow، راجع [الوثائق عبر الإنترنت](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    إذا لم يتم تعيين النطاق إلى **عام**، **فاذهب &gt; إلى الإعدادات المطور &gt;** والتبديل إلى **عام**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="واجهة مستخدم رسومية أو نص أو تطبيق أو دردشة أو رسالة نصية يتم إنشاء الوصف تلقائيا":::

1. انتقل إلى **System OAuth &gt; Application Registry**.

1. حدد **جديد**، ثم حدد **إنشاء "فتح الموفر**" الاتصال جديد.

1. في **تكوين موفر OAuth OIDC**، حدد **البحث وإنشاء تكوين** موفر OIDC جديد ضمن **oidcproviderconfiguration.list\_\_** باستخدام هذه القيم:

    - موفر OIDC: **{TenantName\_} Azure** (مثال: Contoso Azure)

    - URL بيانات تعريف OIDC: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **User ID**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="واجهة مستخدم رسومية، نص، وصف تطبيق يتم إنشاؤه تلقائيا":::

1. قم بإنشاء تطبيق جديد عن طريق تحديد **تكوين موفر OIDC** للتحقق من الرموز المميزة للم ID باستخدام هذه القيم:

    - الاسم: **{TenantName\_}\_applicationinboundapi\_\_** (مثال: contosoapplicationinboundapi\_\_\_)

    - "معرّف العميل": هو "معرّف العميل" للتطبيق الذي تم إنشاؤه في الخطوة 2 من المتطلبات الأساسية (رمز Azure AD Auth المميز \#).

    - سرية العميل: سرية التطبيق للتطبيق الذي تم إنشاؤه في الخطوة 2 من المتطلبات الأساسية (رمز Azure AD Auth المميز \#).

    - تكوين موفر OAuth OIDC: موفر OIDC الذي تم إنشاؤه في الخطوة السابقة

    - عنوان URL إعادة التوجيه: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

1. \[ServiceNow Admin Create\] Integration Users.

    يجب تحديد مستخدم تكامل. إذا لم يكن **&gt;** لديك مستخدم تكامل موجود أو إذا كنت تريد إنشاء مستخدم خاص بهذا التكامل، فاذهب إلى مستخدمو المؤسسة لإنشاء مستخدم جديد. إن قيمة " **تعريف** المستخدم" هي التطبيق "تعريف العميل" الذي تم إنشاؤه في المتطلبات الأساسية [(رمز Azure AD Auth المميز)](#prerequisites-azure-ad-auth-token).

    إذا كنت تقوم بإنشاء مستخدم تكامل جديد، فتحقق من خيار الوصول **إلى خدمة ويب** فقط. يجب أيضا منح هذا المستخدم دور **incidentmanager\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[اختياري\] السماح لتكامل دعم عناوين IP Microsoft 365 الخدمة

إذا كانت شركتك تعمل على تقييد الوصول إلى الإنترنت باستخدام سياساتك الخاصة، فمكن الوصول إلى الشبكة لخدمة تكامل دعم Microsoft 365 من خلال السماح عناوين IP أدناه بالوصول إلى كل من API الواردة والداخلة.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> يسرد أمر المحطة الطرفية هذا جميع IPs النشطة للخدمة Microsoft 365 تكامل الدعم:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>تكوين تطبيق Microsoft 365 تكامل الدعم

يمكن Microsoft 365 تطبيق تكامل الدعم ضمن Microsoft 365 الدعم.

هذه الخطوات مطلوبة لإعداد التكامل بين مثيل ServiceNow Microsoft 365 الدعم.

1. \[ServiceNow Admin\] قم **بتبديل النطاق Microsoft 365 تكامل الدعم**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف الجدول تلقائيا":::

1. \[ServiceNow Admin\] انتقل إلى Microsoft 365 **إعداد &gt; الدعم** لفتح سير عمل التكامل.

    > [!NOTE]
    > إذا رأيت رسالة الخطأ "تم رفض عملية القراءة مقابل 'oauthentity\_' من النطاق 'xmiomsm365\_\_\_،' بسبب نهج الوصول عبر النطاقات في الجدول،" فقد حدث ذلك بسبب نهج الوصول إلى الجدول. يجب التأكد من **تحديد كافة نطاقات التطبيقات التي &gt;** يمكن قراءتها ل oauthentity\_ في الجدول.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin Select\] **أوافق** على مطالبة الموافقة للمتابعة.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] تكوين البيئة ونوع الإعداد.
    إذا كان هذا التثبيت في بيئة اختبار، فحدد الخيار هذه بيئة اختبار. وستتمكن من تعطيل هذا الخيار بسرعة بعد الإعداد وستكتمل جميع الاختبارات في وقت لاحق.
    إذا كان المثيل يسمح بالمصادقة الأساسية للاتصالات الواردة، فحدد نعم وحدد عملية إعداد [المصادقة الأساسية](servicenow-basic-authentication.md). بخلاف ذلك، حدد **لا** وانقر **فوق بدء الإعداد**. 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] أدخل مجال المستأجر Microsoft 365 المستأجر الخاص بك.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] تكوين موفر OAuth الصادر.
    1. تكوين موفر OAuth الصادر.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، انقر فوق تم. وبخلاف ذلك، اتبع الإرشادات الموجودة في المعالج لإنشاء تسجيل التطبيق الضروري في AAD (دليل Azure النشط).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::
    1. قم بتسجيل تطبيق ServiceNow OAuth.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، حدد تسجيل تطبيق OAuth الذي تم إنشاؤه حديثا وانقر فوق التالي. وإلا، اتبع الإرشادات لإنشاء الكيان في ServiceNow ثم حدد تسجيل التطبيق الجديد.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] تكوين الإعدادات الواردة.
    1. تكوين تطبيق AAD (دليل Azure النشط) الوارد.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، انقر فوق تم الانتقال إلى الخطوة التالية. وبخلاف ذلك، اتبع الإرشادات لإنشاء AAD (دليل Azure النشط) تسجيل التطبيق للاتصال الوارد.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::
    1. تكوين ServiceNow External OpenID الاتصال موفر (موفر OIDC).
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، حدد الكيان الذي تم إنشاؤه حديثا وانقر فوق تم. وإلا، اتبع الإرشادات لإنشاء الكيان في ServiceNow ثم حدد تسجيل تطبيق موفر OIDC الخارجي الجديد.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::
    1. قم بتكوين AAD (دليل Azure النشط) تسجيل التطبيق لمستخدم التكامل الوارد.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، انقر فوق تم الانتقال إلى الخطوة التالية. وبخلاف ذلك، اتبع الإرشادات لإنشاء AAD (دليل Azure النشط) تسجيل التطبيق لمستخدم REST الوارد (مستخدم التكامل).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::
    1. تكوين مستخدم التكامل.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، حدد الكيان الذي تم إنشاؤه حديثا وانقر فوق التالي. بخلاف ذلك، اتبع الإرشادات لإنشاء مستخدم التكامل في ServiceNow ثم حدد الكيان.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[Microsoft 365 المستأجر\] أكمل عملية التكامل.

    تحقق من صحة المعلومات أدناه. لا تحدد **التالي** في هذا الوقت.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

    1. انتقل إلى **مسؤول Microsoft 365 Portal &gt; الإعدادات &gt; إعدادات &gt; المؤسسة لملفات تعريف المؤسسة**.

    1. تكوين إعدادات تكامل الدعم:

    حدد علامة **التبويب** معلومات أساسية > **أداة** >  الدعم **الداخليServiceNow**، وأدخل القيمة **"** معرفة التطبيق الصادر" في "المكتشف التطبيق" **من أجل إصدار حقل الرمز المميز ل Auth**. يتم تشغيل هذا الم ID App الصادر في الخطوة 6 – إكمال التكامل، الذي تم إنشاؤه في المتطلبات الأساسية [(رمز Azure AD Auth المميز)](#prerequisites-azure-ad-auth-token).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

    1. على علامة **التبويب مستودعات** ، حدد مستودع **جديد** وتحديثه باستخدام الإعدادات التالية:

    - المستودع: قيمة **"الملهم" من** "الخطوة 6 – إكمال التكامل".

    - نقطة النهاية: قيمة **نقطة النهاية** من "الخطوة 6 – إكمال التكامل".

    - نوع المصادقة: **حدد AAD (دليل Azure النشط) Auth**.

    - "معرّف العميل": قيمة **"معرّف العميل** " من الخطوة 6 – إكمال التكامل.

    - سرية العميل: سر موفر OAuth الوارد الذي تم إنشاؤه في الخطوة 2 من المتطلبات الأساسية (رمز Azure AD Auth المميز \#).

    - اسم المستخدم الباقي: قيمة **اسم** المستخدم من الخطوة 6 – إكمال التكامل، وهو "اسم العميل"  للتطبيق الذي تم إنشاؤه في "المتطلبات الأساسية" (رمز Azure AD Auth المميز) الخطوة \#3.

    - كلمة مرور باقي المستخدم: سرية التطبيق للتطبيق الذي تم إنشاؤه في الخطوة 3 من المتطلبات الأساسية (رمز Azure AD Auth المميز \#).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

    1. العودة إلى ServiceNow.

    1. حدد **التالي** لإكمال التكامل.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::
    سينفذ Microsoft 365 تكامل الدعم اختبارات لضمان عمل التكامل. إذا كانت هناك مشكلة في التكوين، ستشرح رسالة الخطأ ما يجب إصلاحه. وبخلاف ذلك، يكون التطبيق جاهزا.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[مسؤول ServiceNow\] تمكين تكامل دعم Microsoft لمستخدم موجود.

    Microsoft 365 تمكين تكامل الدعم للمستخدم الذي له أحد هذه الأدوار:

    - xmiomsm365\_\_\_، insightsuser\_

    - xmiomsm365همs.administrator\_\_\_

1. \[اختياري\] \[يقوم المستخدم الذي له دور xmiomsm365\_\_\_،\] بربط ارتباط Microsoft 365 المسؤول.

    إذا كان أي مستخدم لديه الدور xmiomsm365\_\_\_، وكان يستخدم حسابات Microsoft 365 مختلفة لإدارة حالة دعم Microsoft 365، فيجب الانتقال إلى حساب ارتباط دعم Microsoft 365 &gt; لإعداد البريد الإلكتروني لمسؤول Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="واجهة مستخدم رسومية، نص، وصف تطبيق يتم إنشاؤه تلقائيا":::
