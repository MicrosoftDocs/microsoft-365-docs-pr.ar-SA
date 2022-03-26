---
title: تكوين تكامل الدعم باستخدام ServiceNow - المصادقة الأساسية
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
ms.openlocfilehash: 23fab410b17cea9635c63b0ed0e4225d158dfdc8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570866"
---
# <a name="configure-support-integration-with-servicenow---basic-authentication"></a>تكوين تكامل الدعم باستخدام ServiceNow - المصادقة الأساسية

## <a name="prerequisites-basic-authentication"></a>المتطلبات الأساسية (المصادقة الأساسية)

هذه المتطلبات الأساسية ضرورية لإعداد Microsoft 365 **الدعم.**

1. \[AAD (دليل Azure النشط) المسؤول\] إنشاء تطبيق Azure AD ضمن Microsoft 365 المستأجر.

    1. سجل دخولك إلى مدخل Azure باستخدام Microsoft 365 بيانات اعتماد المستأجر واذهب إلى صفحة تسجيلات التطبيق لإنشاء [](https://portal.azure.com/?Microsoft_AAD_RegisteredApps=true#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade) تطبيق جديد.

    1. حدد **الحسابات في دليل المؤسسة هذا فقط ({Microsoft-365-tenant-name} فقط – مستأجر واحد)** وحدد **تسجيل**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image3.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image3.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. انتقل إلى **المصادقة** وحدد **إضافة نظام أساسي**. حدد خيار **ويب** وأدخل عنوان URL لإعادة التوجيه: `https://{your-servicenow-instance``}.service-now.com/oauth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image4.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image4.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. احصل على "معر ة عميل التطبيق" وأنشئ سريا للعميل واحصل على تلك القيمة.

1. \[ServiceNow Admin قم\] بإعداد موفر OAuth الصادر في ServiceNow.

    إذا لم يتم تعيين النطاق إلى **عام**، **فاذهب &gt; إلى الإعدادات المطور &gt;** والتبديل إلى **عام**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="واجهة مستخدم رسومية أو نص أو تطبيق أو دردشة أو رسالة نصية يتم إنشاء الوصف تلقائيا":::

1. انتقل إلى **System OAuth &gt; Application Registry**.

1. أنشئ تطبيقا جديدا باستخدام الخيار الاتصال **موفر OAuth** جهة خارجية وأدخل هذه القيم:

    - "معرّف العميل": هذا هو "المليود العميل" للتطبيق الذي تم إنشاؤه في الخطوة \#1.

    - سرية العميل: هذه هي القيمة "سرية العميل" للتطبيق الذي تم إنشاؤه في الخطوة \#1.

    - نوع المنحة الافتراضية: بيانات اعتماد العميل

    - عنوان URL الرمز المميز: `https://login.microsoftonline.com/{microsoft-365-tenant-name}/oauth2/token`

    - عنوان URL إعادة التوجيه: `https://{service-now-instance-name``}.service-now.com/auth_redirect.do`

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image6.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image6.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

1. \[ServiceNow Admin قم\] بإعداد موفر OAuth الوارد.

    إذا لم يتم تعيين النطاق إلى **عام**، **ففعل ذلك عن &gt; طريق الانتقال إلى الإعدادات المطور &gt;** والتبديل إلى **Global**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image5.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image5.png" alt-text="واجهة مستخدم رسومية أو نص أو تطبيق أو دردشة أو رسالة نصية يتم إنشاء الوصف تلقائيا":::

1. انتقل إلى **System OAuth &gt; Application Registry**.

1. قم بإنشاء تطبيق جديد باستخدام **الخيار إنشاء نقطة نهاية OAuth API للعملاء الخارجيين** . يمكنك تسمية موفر OAuth الوارد وترك كافة الحقول الأخرى مع قيمها الافتراضية.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image7.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image7.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

1. \[ServiceNow Admin\] قم بإنشاء مستخدم تكامل.

    يجب تحديد مستخدم تكامل. إذا لم يكن **&gt;** لديك مستخدم تكامل موجود أو إذا كنت تريد إنشاء مستخدم خاص بهذا التكامل، فاذهب إلى مستخدمو المؤسسة لإنشاء مستخدم جديد.

    إذا كنت تقوم بإنشاء مستخدم تكامل جديد، فتحقق من خيار الوصول إلى **خدمة ويب** فقط. يجب أيضا منح هذا المستخدم دور **incidentmanager\_**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image8.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image8.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

## <a name="optional-allow-the-services-ip-addresses-to-microsoft-365-support-integration"></a>\[اختياري\] السماح لتكامل دعم عناوين IP Microsoft 365 الخدمة

إذا كانت شركتك تعمل على تقييد الوصول إلى الإنترنت باستخدام سياساتك الخاصة، فمكن الوصول إلى الشبكة لخدمة تكامل دعم Microsoft 365 من خلال السماح عناوين IP أدناه بالوصول إلى كل من API الوارد والداخل:

- 52.149.152.32

- 40.83.232.243

- 40.83.114.39

- 13.76.138.31

- 13.79.229.170

- 20.105.151.142

> [!NOTE]
> يسرد أمر المحطة الطرفية هذا جميع IPs النشطة للخدمة Microsoft 365 تكامل الدعم:`nslookup`` connector.rave.microsoft.com`

## <a name="configure-the-microsoft-365-support-integration-application"></a>تكوين تطبيق Microsoft 365 التكامل للدعم

يمكن Microsoft 365 تطبيق تكامل الدعم ضمن Microsoft 365 الدعم.

هذه الخطوات مطلوبة لإعداد التكامل بين مثيل ServiceNow Microsoft 365 الدعم.

1. \[ServiceNow Admin\] قم **بتبديل النطاق Microsoft 365 تكامل الدعم**.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image9.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image9.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف الجدول تلقائيا":::

1. \[ServiceNow Admin\] انتقل إلى Microsoft 365 **إعداد &gt; الدعم** لفتح سير عمل التكامل.

    > [!NOTE]
    > إذا رأيت رسالة الخطأ "تم رفض عملية القراءة مقابل 'oauthentity\_' من النطاق 'xmiomsm365\_\_\_،' بسبب نهج الوصول عبر النطاقات في الجدول،" فقد حدث ذلك بسبب نهج الوصول إلى الجدول. يجب التأكد من **تحديد كافة نطاقات التطبيقات التي &gt;** يمكن قراءتها ل oauthentity\_ في الجدول.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image10.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image10.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin Select\] **Agree** to continue.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-1.png" lightbox="../../media/ServiceNow-guide/snowbasic-1.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] تكوين البيئة ونوع الإعداد.

    إذا كان هذا التثبيت في بيئة اختبار، فحدد الخيار هذه بيئة اختبار. وستتمكن من تعطيل هذا الخيار بسرعة بعد الإعداد وستكتمل جميع الاختبارات في وقت لاحق.
    إذا كان المثيل يسمح بالمصادقة الأساسية للاتصالات الواردة، فحدد نعم، وإلا فالرجاء الرجوع إلى الإعداد المتقدم [مع](servicenow-aad-oauth-token.md) AAD (دليل Azure النشط). :::image type="content" source="../../media/ServiceNow-guide/snowbasic-2.png" lightbox="../../media/ServiceNow-guide/snowbasic-2.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] أدخل مجال المستأجر Microsoft 365 المستأجر الخاص بك.

    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-3.png" lightbox="../../media/ServiceNow-guide/snowbasic-3.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] تكوين الإعدادات الصادرة.
    1. سجل تطبيق Azure Active Directory (AAD (دليل Azure النشط)).
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، انقر فوق **تم**. وبخلاف ذلك، اتبع الإرشادات الموجودة في المعالج لإنشاء تسجيل التطبيق الضروري في AAD (دليل Azure النشط).
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-4.png" lightbox="../../media/ServiceNow-guide/snowbasic-4.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

    1. قم بتسجيل تطبيق ServiceNow OAuth.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، حدد تسجيل تطبيق OAuth الذي تم إنشاؤه حديثا وانقر فوق التالي. وإلا، اتبع الإرشادات لإنشاء الكيان في ServiceNow ثم حدد تسجيل التطبيق الجديد.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-5.png" lightbox="../../media/ServiceNow-guide/snowbasic-5.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[ServiceNow Admin\] تكوين الإعدادات الواردة.
    1. تكوين نقطة نهاية OAuth API الواردة.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، حدد تسجيل تطبيق OAuth الذي تم إنشاؤه حديثا وانقر فوق تم. وإلا، اتبع الإرشادات لإنشاء الكيان في ثم حدد تسجيل نقطة نهاية REST الجديد.
     
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-6.png" lightbox="../../media/ServiceNow-guide/snowbasic-6.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

    1. تكوين مستخدم التكامل.
    1. بعد إكمال الإرشادات في مقطع المتطلبات الأساسية، حدد مستخدم التكامل الذي تم إنشاؤه حديثا وانقر فوق التالي. وإلا، اتبع الإرشادات لإنشاء الكيان في ServiceNow ثم حدد مستخدم التكامل الجديد.
    
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-7.png" lightbox="../../media/ServiceNow-guide/snowbasic-7.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::


1. \[Microsoft 365 المستأجر\] أكمل التكامل في مسؤول Microsoft 365 المدخل.

    تحقق من صحة المعلومات أدناه. لا تحدد **التالي** في هذا الوقت.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image17.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image17.png" alt-text="واجهة مستخدم رسومية، نص، وصف تطبيق يتم إنشاؤه تلقائيا":::

1. انتقل إلى **مسؤول Microsoft 365 Portal &gt; الإعدادات &gt; إعدادات &gt; المؤسسة لملفات تعريف المؤسسة**.

1. تكوين إعدادات تكامل الدعم:

    حدد علامة **التبويب** معلومات أساسية > **أداة** >  الدعم **الداخليServiceNow**، وأدخل القيمة **"** معرفة التطبيق الصادر" في "المكتشف التطبيق" **من أجل إصدار حقل الرمز المميز ل Auth**. يوجد هذا المكتشف الصادر للتطبيق في الخطوة 6 – إكمال التكامل، الذي تم إنشاؤه في الخطوة [1 من المتطلبات الأساسية (المصادقة الأساسية\#](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image18.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image18.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. على علامة **التبويب مستودعات** ، حدد مستودع **جديد** وتحديثه باستخدام الإعدادات التالية:

    - المستودع: قيمة **"معرّف المستودع** " من الخطوة 6 – إكمال التكامل.

    - نقطة النهاية: قيمة **نقطة النهاية** من الخطوة 6 – إكمال التكامل.

    - نوع المصادقة: حدد **المصادقة الأساسية**.

    - "معرّف العميل": قيمة **"معرّف العميل** " من الخطوة 6 – إكمال التكامل.

    - سرية العميل: سر موفر OAuth الوارد الذي تم إنشاؤه في الخطوة 3 المتطلبات الأساسية ( \#المصادقة الأساسية).

    - انتهاء صلاحية رمز التحديث المميز: 864000

    - اسم المستخدم الباقي: قيمة **اسم المستخدم** من الخطوة 6 – إكمال التكامل.

    - كلمة مرور المستخدم الباقية: كلمة مرور مستخدم التكامل الذي تم إنشاؤه في الخطوة [4 من المتطلبات الأساسية (المصادقة الأساسية\#](#prerequisites-basic-authentication)).

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image19.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image19.png" alt-text="واجهة مستخدم رسومية، يتم إنشاء وصف التطبيق تلقائيا":::

1. العودة إلى ServiceNow.

1. حدد **التالي** لإكمال التكامل.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-guide-image20.png" lightbox="../../media/ServiceNow-guide/servicenow-guide-image20.png" alt-text="واجهة مستخدم رسومية، تطبيق، وصف موقع ويب يتم إنشاؤه تلقائيا":::

1. \[ServiceNow Admin Test\] the connection after completing the previous step, click **Test connection**.
    :::image type="content" source="../../media/ServiceNow-guide/snowbasic-8.png" lightbox="../../media/ServiceNow-guide/snowbasic-8.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::
    سينفذ Microsoft 365 تكامل الدعم اختبارات لضمان عمل التكامل. إذا كانت هناك مشكلة في التكوين، ستشرح رسالة الخطأ ما يجب إصلاحه. وبخلاف ذلك، يكون التطبيق جاهزا.
     :::image type="content" source="../../media/ServiceNow-guide/snowbasic-9.png" lightbox="../../media/ServiceNow-guide/snowbasic-9.png" alt-text="إنشاء واجهة مستخدم رسومية أو نص أو تطبيق أو وصف بريد إلكتروني تلقائيا":::

1. \[مسؤول ServiceNow\] تمكين تكامل دعم Microsoft لمستخدم موجود.

    Microsoft 365 تمكين تكامل الدعم للمستخدم الذي له أحد هذه الأدوار:

    - xmiomsm365\_\_\_، insightsuser\_

    - xmiomsm365همs.administrator\_\_\_

1. \[اختياري\] [المستخدم الذي x_mioms_m365_assis.مسؤول) ارتباط مسؤول Microsoft 365 الحساب.

    إذا كان أي مستخدم لديه الدور x_mioms_m365_assis.مسؤول ويستخدم حسابات Microsoft 365 مختلفة لإدارة حالة دعم Microsoft 365، فيجب الانتقال إلى دعم Microsoft 365 > ارتباط الحساب لإعداد البريد الإلكتروني لمسؤول Microsoft 365.
    
    :::image type="content" source="../../media/ServiceNow-guide/ServiceNow-guide-image21.png" alt-text="واجهة مستخدم رسومية، نص، وصف تطبيق يتم إنشاؤه تلقائيا":::
