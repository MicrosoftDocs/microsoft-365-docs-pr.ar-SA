---
title: إعداد موصل أرشفة بيانات Twitter
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: تعرف على كيفية إعداد المسؤولين واستخدام موصل أصلي لاستيراد بيانات Twitter إلى Microsoft 365.
ms.openlocfilehash: 95a6a3abd9bed908172ea41b33e4fd60376bea01
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64993502"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>إعداد موصل Microsoft أرشفة بيانات Twitter (معاينة)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

استخدم موصلا في مدخل توافق Microsoft Purview لاستيراد البيانات وأرشفتها من Twitter إلى Microsoft 365. بعد إعداد الموصل وتكوينه، يتصل بحساب Twitter الخاص بمؤسستك (على أساس مجدول)، ويحول محتوى عنصر إلى تنسيق رسالة بريد إلكتروني، ثم يستورد هذه العناصر إلى علبة بريد في Microsoft 365.

بعد استيراد بيانات Twitter، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي والبحث في المحتوى In-Place الأرشفة والتدقيق ونهج استبقاء Microsoft 365 على بيانات Twitter. على سبيل المثال، عند وضع علبة بريد في احتجاز التقاضي أو تعيينها إلى نهج استبقاء، يتم الاحتفاظ ببيانات Twitter. يمكنك البحث في بيانات الجهات الخارجية باستخدام البحث عن المحتوى أو إقران علبة البريد حيث يتم تخزين بيانات Twitter مع أمين في حالة Microsoft Purview eDiscovery (Premium). يمكن أن يساعد استخدام موصل لاستيراد بيانات Twitter وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

بعد استيراد بيانات Twitter، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي والبحث في المحتوى In-Place الأرشفة والتدقيق وتوافق الاتصالات ونهج استبقاء Microsoft 365 على البيانات المخزنة في علبة البريد. على سبيل المثال، يمكنك البحث في بيانات Twitter باستخدام البحث عن المحتوى أو إقران علبة البريد حيث يتم تخزين البيانات مع أمين في حالة eDiscovery (Premium). يمكن أن يساعد استخدام موصل لاستيراد بيانات Twitter وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

## <a name="before-you-set-up-a-connector"></a>قبل إعداد موصل

أكمل المتطلبات الأساسية التالية قبل أن تتمكن من إعداد موصل وتكوينه في مدخل التوافق لاستيراد البيانات وأرشفتها من حساب Twitter الخاص بمؤسستك.

- تحتاج إلى حساب Twitter لمؤسستك؛ تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إعداد الموصل.

- يجب أن يكون لدى مؤسستك اشتراك Azure صالح. إذا لم يكن لديك اشتراك Azure موجود، يمكنك التسجيل للحصول على أحد الخيارات التالية:

    - [التسجيل للحصول على اشتراك Azure مجاني لمدة سنة واحدة](https://azure.microsoft.com/free) 

    - [التسجيل للحصول على اشتراك Pay-As-You-Go Azure](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > لا يدعم [اشتراك Azure Active Directory المجاني](use-your-free-azure-ad-subscription-in-office-365.md) المضمن في اشتراكك في Microsoft 365 الموصلات في مدخل التوافق.

- يمكن لموصل Twitter استيراد ما مجموعه 200000 عنصر في يوم واحد. إذا كان هناك أكثر من 200000 عنصر Twitter في يوم واحد، فلن يتم استيراد أي من هذه العناصر إلى Microsoft 365.

- يجب تعيين دور مسؤول موصل البيانات للمستخدم الذي يقوم بإعداد موصل Twitter في مدخل التوافق (في الخطوة 5). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور مسؤول موصل البيانات، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع قسم "إنشاء مجموعة أدوار مخصصة" في [الأذونات في مدخل توافق Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>الخطوة 1: إنشاء تطبيق في Azure Active Directory

الخطوة الأولى هي تسجيل تطبيق جديد في Azure Active Directory (AAD (دليل Azure النشط)). يتوافق هذا التطبيق مع مورد تطبيق الويب الذي تنفذه في الخطوة 2 لموصل Twitter.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء تطبيق في Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، ستحفظ المعلومات التالية في ملف نصي. سيتم استخدام هذه القيم في خطوات لاحقة في عملية النشر.

- معرف تطبيق AAD (دليل Azure النشط)

- AAD (دليل Azure النشط) سر التطبيق

- معرف المستأجر

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>الخطوة 2: نشر خدمة الويب للموصل من مستودع GitHub إلى حساب Azure الخاص بك

الخطوة التالية هي نشر التعليمات البرمجية المصدر لتطبيق موصل Twitter الذي سيستخدم واجهة برمجة تطبيقات Twitter للاتصال بحساب Twitter واستخراج البيانات حتى تتمكن من استيرادها إلى Microsoft 365. سيقوم موصل Twitter الذي تنشره لمؤسستك بتحميل العناصر من حساب Twitter الخاص بمؤسستك إلى موقع Azure Storage الذي تم إنشاؤه في هذه الخطوة. بعد إنشاء موصل Twitter في مدخل التوافق (في الخطوة 5)، ستقوم خدمة استيراد Microsoft 365 بنسخ بيانات Twitter من موقع تخزين Azure إلى علبة بريد في Microsoft 365. كما هو موضح سابقا في قسم ["قبل إعداد الموصل](#before-you-set-up-a-connector) "، يجب أن يكون لديك اشتراك Azure صالح لإنشاء حساب Azure Storage.

لنشر التعليمات البرمجية المصدر لتطبيق موصل Twitter:

1. انتقل إلى [موقع GitHub هذا](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. انقر فوق **"Deploy to Azure**".

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [نشر خدمة الويب للموصل من GitHub إلى حساب Azure الخاص بك](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

أثناء اتباع الإرشادات المفصلة خطوة بخطوة لإكمال هذه الخطوة، يمكنك توفير المعلومات التالية

- APISecretKey: يمكنك إنشاء هذا السر أثناء إكمال هذه الخطوة. يتم استخدامه في الخطوة 5.

- tenantId: معرف المستأجر لمؤسستك Microsoft 365 التي نسختها بعد إنشاء تطبيق Twitter في Azure Active Directory في الخطوة 1.

بعد إكمال هذه الخطوة، تأكد من نسخ عنوان URL الخاص بخدمة التطبيق (على سبيل المثال، `https://twitterconnector.azurewebsites.net`). تحتاج إلى استخدام عنوان URL هذا لإكمال الخطوة 3 والخطوة 4 والخطوة 5).

## <a name="step-3-create-developer-app-on-twitter"></a>الخطوة 3: إنشاء تطبيق مطور على Twitter

الخطوة التالية هي إنشاء وتكوين تطبيق مطور على Twitter. يستخدم الموصل المخصص الذي تقوم بإنشائه في الخطوة 7 تطبيق Twitter للتفاعل مع واجهة برمجة تطبيقات Twitter للحصول على بيانات من حساب Twitter الخاص بمؤسستك.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء تطبيق Twitter](deploy-twitter-connector.md#step-3-create-the-twitter-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، يمكنك حفظ المعلومات التالية في ملف نصي. سيتم استخدام هذه القيم لتكوين تطبيق موصل Twitter في الخطوة 4.

- مفتاح واجهة برمجة تطبيقات Twitter

- المفتاح السري لواجهة برمجة تطبيقات Twitter

- الرمز المميز للوصول إلى Twitter

- سر الرمز المميز ل Twitter Access

## <a name="step-4-configure-the-twitter-connector-app"></a>الخطوة 4: تكوين تطبيق موصل Twitter

الخطوة التالية هي إضافة إعدادات التكوينات إلى تطبيق موصل Twitter الذي قمت بنشره في الخطوة 2. يمكنك القيام بذلك عن طريق الانتقال إلى الصفحة الرئيسية لتطبيق الموصل وتكوينه.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [تكوين تطبيق ويب الموصل](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، ستوفر المعلومات التالية (التي قمت بنسخها إلى ملف نصي بعد إكمال الخطوات السابقة):

- مفتاح واجهة برمجة تطبيقات Twitter (تم الحصول عليه في الخطوة 3)

- المفتاح السري لواجهة برمجة تطبيقات Twitter (تم الحصول عليه في الخطوة 3)

- الرمز المميز للوصول إلى Twitter (تم الحصول عليه في الخطوة 3)

- Twitter Access Token Secret (تم الحصول عليه في الخطوة 3)

- معرف تطبيق Azure Active Directory (معرف تطبيق AAD (دليل Azure النشط) الذي تم الحصول عليه في الخطوة 1)

- سر تطبيق Azure Active Directory (سر تطبيق AAD (دليل Azure النشط) الذي تم الحصول عليه في الخطوة 1)

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>الخطوة 5: إعداد موصل Twitter في مدخل التوافق

الخطوة الأخيرة هي إعداد موصل Twitter في مدخل التوافق الذي سيستورد البيانات من حساب Twitter الخاص بمؤسستك إلى علبة بريد محددة في Microsoft 365. بعد إكمال هذه الخطوة، ستبدأ خدمة استيراد Microsoft 365 باستيراد البيانات من حساب Twitter الخاص بمؤسستك إلى Microsoft 365.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إعداد موصل Twitter في مدخل توافق Microsoft Purview](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-compliance-portal).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، ستوفر المعلومات التالية (التي قمت بنسخها إلى ملف نصي بعد إكمال الخطوات).

- URL خدمة تطبيق Azure (تم الحصول عليه في الخطوة 2؛ على سبيل المثال، `https://twitterconnector.azurewebsites.net`)

- APISecretKey (التي قمت بإنشائها في الخطوة 2)