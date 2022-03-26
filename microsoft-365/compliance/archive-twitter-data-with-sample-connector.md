---
title: إعداد موصل لأرشفة بيانات Twitter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: تعرف على كيفية إعداد المسؤولين لموصل أصلي واستخدامه لاستيراد بيانات Twitter إلى Microsoft 365.
ms.openlocfilehash: 959cdd49d229334f3129eb21505c4489d23ded4f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63565898"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>إعداد موصل Microsoft لأرشفة بيانات Twitter (معاينة)

استخدم موصلا في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من Twitter Microsoft 365. بعد إعداد الموصل وتكوينه، يتم توصيله إلى حساب Twitter الخاص بالمنظمة (على أساس مجدول)، وتحويل محتوى عنصر إلى تنسيق رسالة بريد إلكتروني، ثم استيراد هذه العناصر إلى علبة بريد في Microsoft 365.

بعد استيراد بيانات Twitter، يمكنك تطبيق Microsoft 365 التوافق مثل الاحتجاز بسبب الدعاوى القضائية والبحث في المحتوى In-Place والأرشفة والتدقيق Microsoft 365 على بيانات Twitter. على سبيل المثال، عند وضع علبة بريد في وضع الاحتجاز بسبب الدعاوى القضائية أو تعيينها إلى نهج استبقاء، يتم الاحتفاظ بالبيانات على Twitter. يمكنك البحث عن بيانات جهة خارجية باستخدام "البحث في المحتوى" أو إقران علبة البريد حيث يتم تخزين بيانات Twitter مع شخص Advanced eDiscovery حالة. يمكن أن يساعد استخدام موصل لاستيراد بيانات Twitter وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

بعد استيراد بيانات Twitter، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية والبحث في المحتوى وأرشفة In-Place والتدقيق وتوافق الاتصالات ونهج استبقاء Microsoft 365 على البيانات المخزنة في علبة البريد. على سبيل المثال، يمكنك البحث في بيانات Twitter باستخدام "البحث في المحتوى" أو إقران علبة البريد حيث يتم تخزين البيانات مع شخص منضم في Advanced eDiscovery أخرى. يمكن أن يساعد استخدام موصل لاستيراد بيانات Twitter وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

أكمل المتطلبات الأساسية التالية قبل أن تتمكن من إعداد موصل وتكوينه في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من حساب Twitter الخاص بمنظمتك.

- أنت بحاجة إلى حساب Twitter لمنظمتك؛ ستحتاج إلى تسجيل الدخول إلى هذا الحساب عند إعداد الموصل.

- يجب أن يكون لدى مؤسستك اشتراك Azure صالح. إذا لم يكن لديك اشتراك Azure موجود، يمكنك التسجيل للحصول على أحد الخيارات التالية:

    - [التسجيل للحصول على اشتراك Azure مجاني لمدة سنة واحدة](https://azure.microsoft.com/free) 

    - [التسجيل للحصول على اشتراك Pay-As-You-Go Azure](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > لا [يدعم اشتراك Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) المجاني المضمن مع اشتراكك في Microsoft 365 الموصلات في مركز التوافق في Microsoft 365.

- يمكن لموصل Twitter استيراد ما مجموعه 200000 عنصر في يوم واحد. إذا كان هناك أكثر من 200000 عنصر Twitter في اليوم، لن يتم استيراد أي من هذه العناصر إلى Microsoft 365.

- يجب تعيين دور مسؤول موصل البيانات إلى المستخدم الذي يقوم مركز التوافق في Microsoft 365 Twitter في القائمة (في الخطوة 5). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>الخطوة 1: إنشاء تطبيق في Azure Active Directory

الخطوة الأولى هي تسجيل تطبيق جديد في Azure Active Directory (AAD (دليل Azure النشط)). يتوافق هذا التطبيق مع مورد تطبيق الويب الذي تنفذه في الخطوة 2 لموصل Twitter.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء تطبيق في Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، ستحفظ المعلومات التالية في ملف نصي. سيتم استخدام هذه القيم في الخطوات اللاحقة في عملية النشر.

- AAD (دليل Azure النشط) التطبيق

- AAD (دليل Azure النشط) سرية للتطبيق

- "مستأجر"

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>الخطوة 2: نشر خدمة ويب للموصل من GitHub إلى حساب Azure

الخطوة التالية هي نشر التعليمات البرمجية المصدر لتطبيق Twitter connector الذي سيستخدم Twitter API للاتصال باستخدام حساب Twitter واستخراج البيانات حتى تتمكن من استيرادها Microsoft 365. سيرفع موصل Twitter الذي تنشره لمنظمتك العناصر من حساب Twitter الخاص بمنظمتك إلى موقع تخزين Azure الذي تم إنشاؤه في هذه الخطوة. بعد إنشاء موصل Twitter في مركز التوافق في Microsoft 365 (في الخطوة 5)، ستنسخ خدمة استيراد Microsoft 365 بيانات Twitter من موقع تخزين Azure إلى علبة بريد في Microsoft 365. كما هو موضح سابقا في المقطع [قبل](#before-you-set-up-a-connector) إعداد موصل، يجب أن يكون لديك اشتراك Azure صالح لإنشاء حساب تخزين Azure.

لنشر التعليمة البرمجية المصدر لتطبيق Twitter connector:

1. انتقل إلى [موقع GitHub هذا](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. انقر **فوق نشر إلى Azure**.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع نشر خدمة الويب للموصل [من GitHub إلى حساب Azure](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

أثناء اتباع الإرشادات خطوة بخطوة لإكمال هذه الخطوة، يمكنك توفير المعلومات التالية

- APISecretKey: يمكنك إنشاء هذا السرية أثناء إكمال هذه الخطوة. يتم استخدامه في الخطوة 5.

- tenantId: هو "Microsoft 365 المستأجر" الخاص Microsoft 365 الذي نسخته بعد إنشاء تطبيق Twitter في Azure Active Directory في الخطوة 1.

بعد إكمال هذه الخطوة، تأكد من نسخ عنوان URL لخدمة التطبيق (على سبيل المثال، `https://twitterconnector.azurewebsites.net`). يجب استخدام عنوان URL هذا لإكمال الخطوة 3 والخطوة 4 والخطوة 5).

## <a name="step-3-create-developer-app-on-twitter"></a>الخطوة 3: إنشاء تطبيق مطور على Twitter

الخطوة التالية هي إنشاء تطبيق مطور وتكوينه على Twitter. يستخدم الموصل المخصص الذي تقوم بإنشاءه في الخطوة 7 تطبيق Twitter للتفاعل مع API على Twitter للحصول على بيانات من حساب Twitter الخاص بالمنظمة.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء تطبيق Twitter](deploy-twitter-connector.md#step-3-create-the-twitter-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، يمكنك حفظ المعلومات التالية في ملف نصي. سيتم استخدام هذه القيم لتكوين تطبيق موصل Twitter في الخطوة 4.

- مفتاح API ل Twitter

- مفتاح سري ل API في Twitter

- رمز Twitter Access المميز

- سرية رمز Twitter Access المميز

## <a name="step-4-configure-the-twitter-connector-app"></a>الخطوة 4: تكوين تطبيق موصل Twitter

الخطوة التالية هي إضافة إعدادات التكوين إلى تطبيق Twitter connector الذي قمت بنشره في الخطوة 2. يمكنك القيام بذلك عن طريق الذهاب إلى الصفحة الرئيسية لتطبيق الموصل وتكوينه.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [تكوين تطبيق ويب الموصل](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، ستزودك بالمعلومات التالية (التي نسختها إلى ملف نصي بعد إكمال الخطوات السابقة):

- مفتاح API ل Twitter (تم الحصول عليه في الخطوة 3)

- مفتاح سري ل API في Twitter (تم الحصول عليه في الخطوة 3)

- Twitter Access Token (تم الحصول عليه في الخطوة 3)

- سرية رمز Twitter Access المميز (تم الحصول عليه في الخطوة 3)

- Azure Active Directory application ID (AAD (دليل Azure النشط) التطبيق الذي تم الحصول عليه في الخطوة 1)

- سرية تطبيق Azure Active Directory (AAD (دليل Azure النشط) سرية التطبيق التي تم الحصول عليها في الخطوة 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>الخطوة 5: إعداد موصل Twitter في مركز التوافق في Microsoft 365

الخطوة الأخيرة هي إعداد موصل Twitter في مركز التوافق في Microsoft 365 الذي سيستورد البيانات من حساب Twitter الخاص بالم مؤسستك إلى علبة بريد محددة في Microsoft 365. بعد إكمال هذه الخطوة، Microsoft 365 استيراد البيانات من حساب Twitter الخاص Microsoft 365.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إعداد موصل Twitter في مركز التوافق في Microsoft 365](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center). 

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، ستزودك بالمعلومات التالية (التي نسختها إلى ملف نصي بعد إكمال الخطوات).

- URL لخدمة تطبيق Azure (تم الحصول عليه في الخطوة 2؛ على سبيل المثال، `https://twitterconnector.azurewebsites.net`)

- APISecretKey (الذي أنشأته في الخطوة 2)