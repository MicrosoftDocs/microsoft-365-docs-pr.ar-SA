---
title: تكوين تكامل دعم Microsoft 365 مع Azure AD Auth Token
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
description: تثبيت التطبيق المعتمد على نطاق ودليل التكوين ل ServiceNow.
ms.openlocfilehash: d3991355779228cf1562e23ddd0e97cb37225a43
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093735"
---
# <a name="configure-microsoft-365-support-integration-with-azure-ad-auth-token"></a>تكوين تكامل دعم Microsoft 365 مع Azure AD Auth Token

## <a name="prerequisites-azure-ad-auth-token"></a>المتطلبات الأساسية (الرمز المميز لمصادقة Azure AD)

هذه المتطلبات الأساسية ضرورية لإعداد تكامل دعم Microsoft 365.

1. \[مسؤول\] AAD (دليل Azure النشط) إنشاء تطبيق Azure AD ل Outbound ضمن مستأجر Microsoft 365 الخاص بك.

    1. سجل الدخول إلى مدخل Microsoft Azure باستخدام بيانات اعتماد المستأجر Microsoft 365 وانتقل إلى [صفحة تسجيلات التطبيق](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) لإنشاء تطبيق جديد.

    2. حدد **الحسابات في دليل المؤسسة هذا فقط ({Microsoft-365-tenant-name} فقط – مستأجر واحد)** وحدد **"Register**".

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. انتقل إلى **المصادقة** وحدد **"إضافة نظام أساسي**". حدد خيار **ويب** وأدخل عنوان URL لإعادة التوجيه: `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. احصل على معرف عميل التطبيق وأنشئ سر العميل واحصل على هذه القيمة.

1. \[مسؤول\] AAD (دليل Azure النشط) إنشاء تطبيق Azure AD ل Rest API ضمن مستأجر Microsoft 365 الخاص بك.

    1. سجل الدخول إلى [مدخل Microsoft Azure](https://portal.azure.com/) باستخدام بيانات اعتماد المستأجر Microsoft 365 وانتقل إلى صفحة تسجيلات التطبيق لإنشاء تطبيق جديد.

    1. حدد **الحسابات في دليل المؤسسة هذا فقط {(Microsoft-365-tenant-name} فقط – مستأجر واحد).**

        :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image22.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image22.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. احصل على معرف عميل التطبيق وأنشئ سر العميل واحصل على هذه القيمة.

1. \[مسؤول\] AAD (دليل Azure النشط) إنشاء تطبيق Azure AD لمستخدم Rest ضمن مستأجر Microsoft 365 الخاص بك.

    1. سجل الدخول إلى [مدخل Microsoft Azure](https://portal.azure.com/) باستخدام بيانات اعتماد المستأجر Microsoft 365 وانتقل إلى صفحة تسجيلات التطبيق لإنشاء تطبيق جديد.

    1. حدد **الحسابات في دليل المؤسسة هذا فقط {(Microsoft-365-tenant-name} فقط – مستأجر واحد).**

        :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" lightbox="../../media/ServiceNow-guide/ServiceNow-guide-image23.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. احصل على معرف عميل التطبيق وأنشئ سر العميل واحصل على هذه القيمة.

1. \[إعداد ServiceNow Admin\] موفر OAuth الصادر في ServiceNow.

    إذا لم يتم تعيين النطاق إلى **Global**، فقم بذلك بالانتقال إلى **الإعدادات &gt; Developer &gt; Applications** والتبديل إلى **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="واجهة مستخدم رسومية أو نص أو تطبيق أو دردشة أو وصف رسالة نصية تم إنشاؤه تلقائيا":::

1. انتقل إلى **System OAuth &gt; Application Registry**.

1. إنشاء تطبيق جديد باستخدام **الاتصال إلى خيار موفر OAuth تابع لجهة خارجية** وإدخال هذه القيم:

    - معرف العميل: هذا هو معرف العميل للتطبيق الذي تم إنشاؤه في الخطوة \#1 من المتطلبات الأساسية (Azure AD Auth Token).

    - سر العميل: هذه هي قيمة سر العميل للتطبيق الذي تم إنشاؤه في الخطوة \#1 من المتطلبات الأساسية (Azure AD Auth Token).

    - نوع المنحة الافتراضية: بيانات اعتماد العميل

    - URL الرمز المميز: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - عنوان URL لإعادة التوجيه: `https://{service-now-instance-name``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="واجهة مستخدم رسومية، تم إنشاء وصف التطبيق تلقائيا":::

1. \[ServiceNow Admin\] لتكوين موفر OIDC في ServiceNow، راجع [الوثائق عبر الإنترنت](https://docs.servicenow.com/bundle/quebec-platform-administration/page/administer/security/task/add-OIDC-entity.html).

    إذا لم يتم تعيين النطاق إلى **Global**، فانتقل إلى **الإعدادات &gt; Developer &gt; Applications** وقم بالتبديل إلى **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="واجهة مستخدم رسومية أو نص أو تطبيق أو دردشة أو وصف رسالة نصية تم إنشاؤه تلقائيا":::

1. انتقل إلى **System OAuth &gt; Application Registry**.

1. حدد **"جديد**"، ثم حدد **"Create open ID الاتصال Provider**".

1. في **تكوين موفر OAuth OIDC**، حدد **Search** وقم بإنشاء تكوين موفر OIDC جديد ضمن **oidcproviderconfiguration.list\_\_** مع هذه القيم:

    - موفر OIDC: **{TenantName\_} Azure** (مثال: Contoso Azure)

    - URL بيانات تعريف OIDC: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/.well-known/openid-configuration`

    - UserClaim: **appid**

    - UserField: **معرف المستخدم**

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image24.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image24.png" alt-text="واجهة المستخدم الرسومية، النص، وصف التطبيق التي تم إنشاؤها تلقائيا":::

1. إنشاء تطبيق جديد عن طريق تحديد **تكوين موفر OIDC للتحقق من الرموز المميزة للمعرف** باستخدام هذه القيم:

    - الاسم: **{TenantName\_}\_applicationinboundapi\_\_** (مثال: contosoapplicationinboundapi\_\_\_)

    - معرف العميل: معرف العميل للتطبيق الذي تم إنشاؤه في الخطوة \#3 من المتطلبات الأساسية (Azure AD Auth Token).

    - سر العميل: سر التطبيق للتطبيق الذي تم إنشاؤه في الخطوة \#3 من المتطلبات الأساسية (Azure AD Auth Token).

    - تكوين موفر OAuth OIDC: تم إنشاء موفر OIDC في الخطوة السابقة

    - عنوان URL لإعادة التوجيه: `https://{service-now-instance-name}.service-now.com/oauth\_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image25.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image25.png" alt-text="واجهة مستخدم رسومية، تم إنشاء وصف التطبيق تلقائيا":::

1. \[يقوم مسؤول\] ServiceNow بإنشاء مستخدمي التكامل.

    يجب تحديد مستخدم تكامل. إذا لم يكن لديك مستخدم تكامل موجود أو إذا كنت تريد إنشاء مستخدم خاص لهذا التكامل، فانتقل إلى **"مستخدمو المؤسسة&gt;**" لإنشاء مستخدم جديد. The value of the **User ID** is the application Client ID created in [Prerequisites (Azure AD Auth Token)](#prerequisites-azure-ad-auth-token).

    إذا كنت تقوم بإنشاء مستخدم تكامل جديد، فتحقق من خيار **الوصول إلى خدمة ويب فقط** . يجب عليك أيضا منح هذا المستخدم دور **incidentmanager\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image26.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image26.png" alt-text="واجهة مستخدم رسومية، تم إنشاء وصف التطبيق تلقائيا":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[اختياري\] السماح لعناوين IP للخدمة Microsoft 365 دعم التكامل

إذا كانت شركتك تحد من الوصول إلى الإنترنت من خلال نهجك الخاصة، فتمكن من الوصول إلى الشبكة لخدمة Microsoft 365 دعم التكامل من خلال السماح بعناوين IP أدناه للوصول إلى كل من واجهة برمجة التطبيقات الواردة والصادرة.

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> يسرد أمر المحطة الطرفية هذا كافة عناوين IP النشطة للخدمة Microsoft 365 تكامل الدعم:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>تكوين تطبيق تكامل دعم Microsoft 365

يمكن إعداد تطبيق تكامل دعم Microsoft 365 ضمن دعم Microsoft 365.

هذه الخطوات مطلوبة لإعداد التكامل بين مثيل ServiceNow ودعم Microsoft 365.

1. \[ServiceNow Admin\] Switch the scope to **Microsoft 365 support integration**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="واجهة مستخدم رسومية، تم إنشاء وصف الجدول تلقائيا":::

1. \[انتقل مسؤول\] ServiceNow إلى **إعداد دعم &gt; Microsoft 365** لفتح سير عمل التكامل.

    > [!NOTE]
    > إذا رأيت الخطأ "تم رفض عملية القراءة مقابل "oauthentity\_" من النطاق "xmiomsm365assis\_\_\_" بسبب نهج الوصول عبر النطاق للجدول،" فقد حدث ذلك بسبب نهج الوصول إلى الجدول. يجب التأكد من تحديد **كافة نطاقات التطبيق التي &gt; يمكن قراءتها** للكيان oauthentity\_ للجدول.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image27.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image27.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[ServiceNow Admin\] Select **Agree** to the consent prompt to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-1.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-1.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[يقوم مسؤول\] ServiceNow بتكوين البيئة ونوع الإعداد.
    إذا كان هذا التثبيت في بيئة اختبار، فحدد الخيار "هذه بيئة اختبار". ستتمكن من تعطيل هذا الخيار بسرعة بعد الإعداد وإكمال جميع الاختبارات في وقت لاحق.
    إذا كان المثيل الخاص بك يسمح بالمصادقة الأساسية للاتصالات الواردة، فحدد "نعم" وراجع [عملية إعداد Basic Auth](servicenow-basic-authentication.md). وإلا، فحدد **"لا** " وانقر فوق **"بدء الإعداد**". 
      :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-2.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-2.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[أدخل مسؤول\] ServiceNow مجال المستأجر Microsoft 365.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-3.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-3.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[ServiceNow Admin\] Configure Outbound OAuth provider.
    1. تكوين موفر OAuth الصادر.
    1. بعد إكمال الإرشادات في قسم المتطلبات الأساسية، انقر فوق "تم". وإلا، اتبع الإرشادات الموجودة في المعالج لإنشاء تسجيل التطبيق الضروري في AAD (دليل Azure النشط).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-4.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-4.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::
    1. تسجيل تطبيق ServiceNow OAuth.
    1. بعد إكمال الإرشادات في قسم المتطلبات الأساسية، حدد تسجيل تطبيق OAuth الذي تم إنشاؤه حديثا وانقر فوق "التالي". وإلا، فاتبع الإرشادات لإنشاء الكيان في ServiceNow ثم حدد تسجيل التطبيق الجديد.
     :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-5.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-5.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[يقوم مسؤول\] ServiceNow بتكوين الإعدادات الواردة.
    1. تكوين تطبيق AAD (دليل Azure النشط) الوارد.
    1. بعد إكمال الإرشادات في قسم المتطلبات الأساسية، انقر فوق "تم" للانتقال إلى الخطوة التالية. وإلا، اتبع الإرشادات لإنشاء تسجيل تطبيق AAD (دليل Azure النشط) للاتصال الوارد.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-6.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-6.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::
    1. تكوين موفر الاتصال ServiceNow External OpenID (موفر OIDC).
    1. بعد إكمال الإرشادات في قسم المتطلبات الأساسية، حدد الكيان الذي تم إنشاؤه حديثا وانقر فوق "تم". وإلا، فاتبع الإرشادات لإنشاء الكيان في ServiceNow ثم حدد تسجيل تطبيق موفر OIDC الخارجي الجديد.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-7.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-7.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::
    1. تكوين تسجيل تطبيق AAD (دليل Azure النشط) لمستخدم التكامل الوارد.
    1. بعد إكمال الإرشادات في قسم المتطلبات الأساسية، انقر فوق "تم" للانتقال إلى الخطوة التالية. وإلا، اتبع الإرشادات لإنشاء تسجيل تطبيق AAD (دليل Azure النشط) لمستخدم REST الوارد (مستخدم التكامل).
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-8.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-8.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::
    1. تكوين مستخدم التكامل.
    1. بعد إكمال الإرشادات في قسم المتطلبات الأساسية، حدد الكيان الذي تم إنشاؤه حديثا وانقر فوق "التالي". وإلا فاتبع الإرشادات لإنشاء مستخدم التكامل في ServiceNow ثم حدد الكيان.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-9.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-9.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[مسؤول مستأجر\] Microsoft 365 إكمال التكامل.

    تحقق من صحة المعلومات أدناه. لا تحدد **"التالي"** في هذا الوقت.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image40.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image40.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

    1. انتقل إلى **ملفات تعريف المؤسسة لإعدادات &gt; مسؤول Microsoft 365 Portal &gt; الإعدادات &gt; Org**.

    1. تكوين إعدادات تكامل الدعم:

    حدد علامة تبويب **المعلومات الأساسية** > **أداة** >  الدعم **الداخليServiceNow**، وأدخل قيمة **معرف التطبيق الصادر** في **معرف التطبيق لإصدار حقل رمز المصادقة المميز**. معرف التطبيق الصادر هذا في الخطوة 6 – أكمل التكامل، الذي تم إنشاؤه في [المتطلبات الأساسية (Azure AD Auth Token).](#prerequisites-azure-ad-auth-token)

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

    1. في علامة التبويب **"Repositories** "، حدد **"New repository"** وقم بتحديثه بالإعدادات التالية:

    - المستودع: قيمة **معرف المستودع** من "الخطوة 6 – إكمال التكامل".

    - نقطة النهاية: قيمة **نقطة النهاية** من "الخطوة 6 – إكمال التكامل".

    - نوع المصادقة: حدد **AAD (دليل Azure النشط) Auth**.

    - معرف العميل: قيمة **معرف العميل** من الخطوة 6 – إكمال التكامل.

    - سر العميل: سر موفر OAuth الوارد الذي تم إنشاؤه في الخطوة \#2 من المتطلبات الأساسية (Azure AD Auth Token).

    - اسم المستخدم المتبقي: قيمة **اسم المستخدم** من الخطوة 6 – إكمال التكامل، وهو **معرف العميل** للتطبيق الذي تم إنشاؤه في الخطوة \#3 من المتطلبات الأساسية (Azure AD Auth Token).

    - كلمة مرور المستخدم المتبقية: سر التطبيق للتطبيق الذي تم إنشاؤه في الخطوة \#3 من المتطلبات الأساسية (Azure AD Auth Token).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image31.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image31.png" alt-text="واجهة مستخدم رسومية، تم إنشاء وصف التطبيق تلقائيا":::

    1. ارجع إلى ServiceNow.

    1. حدد **"التالي** " لإكمال التكامل.

   :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-10.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-10.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::
    سيقوم تطبيق تكامل دعم Microsoft 365 بتنفيذ الاختبارات لضمان عمل التكامل. إذا كانت هناك مشكلة في التكوين، فستشرح رسالة الخطأ ما يجب إصلاحه. وإلا، فإن التطبيق جاهز.
    :::image type="content" source="../../media/ServiceNow-guide/snowaadoauth-11.png" lightbox="../../media/ServiceNow-guide/snowaadoauth-11.png" alt-text="واجهة المستخدم الرسومية، النص، التطبيق، وصف البريد الإلكتروني التي تم إنشاؤها تلقائيا":::

1. \[تمكين تكامل دعم Microsoft لمستخدم موجود من قبل مسؤول\] ServiceNow.

    يتم تمكين تكامل دعم Microsoft 365 للمستخدم باستخدام أحد الأدوار التالية:

    - xmiomsm365assis.insightsuser\_\_\_\_

    - xmiomsm365assis.administrator\_\_\_

1. \[اختياري\] \[المستخدم ذو الدور xmiomsm365assis.administrator\_\_\_ link\] link Microsoft 365 admin account.

    إذا كان لأي مستخدم دور xmiomsm365assis.administrator\_\_\_ ويستخدم حسابات Microsoft 365 مختلفة لإدارة حالة دعم Microsoft 365، فيجب عليه الانتقال إلى Microsoft 365 دعم &gt; حساب الارتباط لإعداد البريد الإلكتروني للمسؤول Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image21.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image21.png" alt-text="واجهة المستخدم الرسومية، النص، وصف التطبيق التي تم إنشاؤها تلقائيا":::
