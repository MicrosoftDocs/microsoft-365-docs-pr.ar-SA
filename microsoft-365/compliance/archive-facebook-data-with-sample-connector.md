---
title: إعداد موصل لأرشفة بيانات Facebook
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
description: تعرف على كيفية إعداد & موصل في مركز التوافق في Microsoft 365 لاستيراد بيانات الأرشيف & من صفحات Facebook Business Microsoft 365.
ms.openlocfilehash: f7cbc2b5a0f1ed55379224fc18b1be905e8a4cf0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566303"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>إعداد موصل لأرشفة بيانات Facebook (معاينة)

استخدم موصلا في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من صفحات Facebook Business Microsoft 365. بعد إعداد الموصل وتكوينه، يتصل بصفحة Facebook Business (على أساس مجدول)، ويحول محتوى عناصر Facebook إلى تنسيق رسالة بريد إلكتروني، ثم يستورد هذه العناصر إلى علبة بريد في Microsoft 365.

بعد استيراد بيانات Facebook، يمكنك تطبيق ميزات توافق Microsoft 365 مثل الاحتجاز بسبب الدعاوى القضائية والبحث في المحتوى وأرشفة In-Place والتدقيق وتوافق الاتصالات ونهج استبقاء Microsoft 365 على بيانات Facebook. على سبيل المثال، عند وضع علبة بريد في وضع الاحتجاز بسبب الدعاوى القضائية أو تعيينها إلى نهج استبقاء، يتم الاحتفاظ بالبيانات في Facebook. يمكنك البحث عن بيانات جهة خارجية باستخدام "البحث في المحتوى" أو إقران علبة البريد حيث يتم تخزين بيانات Facebook مع شخص Advanced eDiscovery حالة. يمكن أن يساعد استخدام موصل لاستيراد بيانات Facebook وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقا مع سياسات الحكومة والسياسات التنظيمية.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>المتطلبات الأساسية لإعداد موصل لصفحات Facebook Business

أكمل المتطلبات الأساسية التالية قبل أن تتمكن من إعداد موصل وتكوينه في مركز التوافق في Microsoft 365 لاستيراد البيانات وأرشفتها من صفحات Facebook Business في مؤسستك. 

- أنت بحاجة إلى حساب Facebook لصفحات الأعمال في مؤسستك (تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إعداد الموصل). حاليا، يمكنك أرشفة البيانات فقط من صفحات Facebook Business؛ لا يمكنك أرشفة البيانات من ملفات تعريف Facebook الفردية.

- يجب أن يكون لدى مؤسستك اشتراك Azure صالح. إذا لم يكن لديك اشتراك Azure موجود، يمكنك التسجيل للحصول على أحد الخيارات التالية:

    - [التسجيل للحصول على اشتراك Azure مجاني لمدة سنة واحدة](https://azure.microsoft.com/free)

    - [التسجيل للحصول على اشتراك Pay-As-You-Go Azure](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > لا [يدعم اشتراك Azure Active Directory](use-your-free-azure-ad-subscription-in-office-365.md) المجاني المضمن مع اشتراكك في Microsoft 365 الموصلات في مركز التوافق في Microsoft 365.

- يمكن لموصل صفحات Facebook Business استيراد ما مجموعه 200000 عنصر في يوم واحد. إذا كان هناك أكثر من 200000 عنصر في Facebook Business في يوم واحد، لن يتم استيراد أي من هذه العناصر إلى Microsoft 365.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم مركز التوافق في Microsoft 365 في الخطوة 5. هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات** البيانات في مركز التوافق في Microsoft 365. يضاف هذا الدور بشكل افتراضي إلى مجموعات دور متعددة. للحصول على قائمة لمجموعات الأدوار هذه، راجع القسم "الأدوار في مراكز الأمان والتوافق" في الأذونات [في مركز التوافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة دور مخصصة وتعيين دور مسؤول موصل البيانات ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة دور مخصص" في [الأذونات في مركز التوافق في Microsoft 365](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>الخطوة 1: إنشاء تطبيق في Azure Active Directory

الخطوة الأولى هي تسجيل تطبيق جديد في Azure Active Directory (AAD (دليل Azure النشط)). يتوافق هذا التطبيق مع مورد تطبيق الويب الذي تنفذه في الخطوة 4 والخطوة 5 لموصل Facebook. 

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء تطبيق في Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

أثناء إكمال هذه الخطوة (باستخدام الإرشادات السابقة خطوة بخطوة)، ستحفظ المعلومات التالية في ملف نصي. يتم استخدام هذه القيم في الخطوات اللاحقة في عملية النشر.

- AAD (دليل Azure النشط) التطبيق

- AAD (دليل Azure النشط) سرية للتطبيق

- "مستأجر"

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>الخطوة 2: نشر خدمة الويب للموصل من GitHub إلى حساب Azure

الخطوة التالية هي نشر التعليمات البرمجية المصدر لتطبيق موصل صفحات Facebook Business الذي سيستخدم API في Facebook للاتصال باستخدام حساب Facebook واستخراج البيانات حتى تتمكن من استيرادها إلى Microsoft 365. سيرفع موصل Facebook الذي تنشره لمنظمتك العناصر من صفحات Facebook Business إلى موقع تخزين Azure الذي تم إنشاؤه في هذه الخطوة. بعد إنشاء موصل صفحات عمل Facebook في مركز التوافق في Microsoft 365 (في الخطوة 5)، ستنسخ خدمة الاستيراد بيانات صفحات الأعمال في Facebook من موقع تخزين Azure إلى علبة بريد في Microsoft 365 مؤسستك. كما هو موضح سابقا في المقطع [المتطلبات](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) الأساسية، يجب أن يكون لديك اشتراك Azure صالح لإنشاء حساب تخزين Azure.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع نشر خدمة الويب للموصل [من GitHub إلى حساب Azure](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

في الإرشادات خطوة بخطوة لإكمال هذه الخطوة، ستزودك بالمعلومات التالية:

- APISecretKey: يمكنك إنشاء هذا السرية أثناء إكمال هذه الخطوة. يتم استخدامه في الخطوة 5.

- TenantId: هو مستأجر Microsoft 365 الذي نسخته بعد إنشاء تطبيق موصل Facebook في Azure Active Directory في الخطوة 1.

بعد إكمال هذه الخطوة، تأكد من نسخ عنوان URL لخدمة تطبيق Azure (على سبيل المثال، https://fbconnector.azurewebsites.net). يجب استخدام عنوان URL هذا لإكمال الخطوة 3 والخطوة 4 والخطوة 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>الخطوة 3: تسجيل تطبيق الويب على Facebook

الخطوة التالية هي إنشاء تطبيق جديد وتكوينه على Facebook. يستخدم موصل صفحات الأعمال في Facebook الذي تقوم بإنشاءه في الخطوة 5 تطبيق Facebook على الويب للتفاعل مع API في Facebook للحصول على بيانات من صفحات Facebook Business الخاصة بالم مؤسستك.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [تسجيل تطبيق Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، يمكنك حفظ المعلومات التالية في ملف نصي. يتم استخدام هذه القيم لتكوين تطبيق موصل Facebook في الخطوة 4.

- "معرّف تطبيق Facebook"

- سرية تطبيق Facebook

- يتحقق Facebook webhooks من الرمز المميز

## <a name="step-4-configure-the-facebook-connector-app"></a>الخطوة 4: تكوين تطبيق موصل Facebook

الخطوة التالية هي إضافة إعدادات التكوين إلى تطبيق موصل Facebook الذي قمت بتحميله عند إنشاء مورد تطبيق Azure على الويب في الخطوة 1. يمكنك القيام بذلك عن طريق الذهاب إلى الصفحة الرئيسية لتطبيق الموصل وتكوينه.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [تكوين تطبيق موصل Facebook](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، يمكنك توفير المعلومات التالية (التي نسختها إلى ملف نصي بعد إكمال الخطوات السابقة):

- "معرّف تطبيق Facebook" (تم الحصول عليه في الخطوة 3)

- سرية تطبيق Facebook (تم الحصول عليها في الخطوة 3)

- يتحقق Facebook webhooks من الرمز المميز (تم الحصول عليه في الخطوة 3)

- Azure Active Directory application ID (AAD (دليل Azure النشط) التطبيق الذي تم الحصول عليه في الخطوة 1)

- سرية تطبيق Azure Active Directory (AAD (دليل Azure النشط) سرية التطبيق التي تم الحصول عليها في الخطوة 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-microsoft-365-compliance-center"></a>الخطوة 5: إعداد موصل صفحات Facebook Business في مركز التوافق في Microsoft 365

الخطوة الأخيرة هي إعداد الموصل في مركز التوافق في Microsoft 365 الذي سيستورد البيانات من صفحات Facebook Business إلى علبة بريد محددة في Microsoft 365. بعد إكمال هذه الخطوة، Microsoft 365 استيراد البيانات من صفحات Facebook Business إلى Microsoft 365.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الخطوة 5: إعداد موصل Facebook في مركز التوافق في Microsoft 365](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center). 

أثناء إكمال هذه الخطوة (باتباع الإرشادات خطوة بخطوة)، يمكنك توفير المعلومات التالية (التي نسختها إلى ملف نصي بعد إكمال الخطوات).

- AAD (دليل Azure النشط) التطبيق (تم الحصول عليه في الخطوة 1)

- URL لخدمة تطبيق Azure (تم الحصول عليه في الخطوة 1؛ على سبيل المثال، https://fbconnector.azurewebsites.net)

- APISecretKey (الذي أنشأته في الخطوة 2)