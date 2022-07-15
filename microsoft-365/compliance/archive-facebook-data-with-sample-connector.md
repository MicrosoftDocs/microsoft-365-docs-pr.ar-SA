---
title: إعداد موصل أرشفة بيانات Facebook
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 07/15/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: تعرف على كيفية إعداد & استخدام موصل في مدخل التوافق في Microsoft Purview لاستيراد بيانات أرشفة & من صفحات Facebook Business إلى Microsoft 365.
ms.openlocfilehash: 79238bbbdcea71cf83342894d3b61e8047f5897a
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822868"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>إعداد موصل أرشفة بيانات Facebook (معاينة)

استخدم موصلا في مدخل التوافق في Microsoft Purview لاستيراد البيانات وأرشفتها من صفحات Facebook Business إلى Microsoft 365. بعد إعداد الموصل وتكوينه، يتصل بصفحة Facebook Business (على أساس مجدول)، ويحول محتوى عناصر Facebook إلى تنسيق رسالة بريد إلكتروني، ثم يستورد هذه العناصر إلى علبة بريد في Microsoft 365.

بعد استيراد بيانات Facebook، يمكنك تطبيق ميزات Microsoft Purview مثل احتجاز التقاضي والبحث في المحتوى In-Place الأرشفة والتدقيق وتوافق الاتصالات ونهج استبقاء Microsoft 365 على بيانات Facebook. على سبيل المثال، عند وضع علبة بريد في احتجاز التقاضي أو تعيينها إلى نهج استبقاء، يتم الاحتفاظ ببيانات Facebook. يمكنك البحث في بيانات الجهات الخارجية باستخدام "البحث عن المحتوى" أو إقران علبة البريد حيث يتم تخزين بيانات Facebook مع أمين في حالة Microsoft Purview eDiscovery (Premium). يمكن أن يساعد استخدام موصل لاستيراد بيانات Facebook وأرشفتها في Microsoft 365 مؤسستك على البقاء متوافقة مع السياسات الحكومية والتنظيمية.

إذا كنت ترغب في المشاركة في المعاينة، فالرجاء التواصل مع الفريق في dcfeedback@microsoft.com.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>المتطلبات الأساسية لإعداد موصل لصفحات Facebook Business

أكمل المتطلبات الأساسية التالية قبل أن تتمكن من إعداد موصل وتكوينه في مدخل التوافق لاستيراد البيانات وأرشفتها من صفحات Facebook Business الخاصة بمؤسستك. 

- تحتاج إلى حساب Facebook لصفحات عمل مؤسستك (تحتاج إلى تسجيل الدخول إلى هذا الحساب عند إعداد الموصل). حاليا، يمكنك أرشفة البيانات فقط من صفحات Facebook Business؛ لا يمكنك أرشفة البيانات من ملفات تعريف Facebook الفردية.

- يجب أن يكون لدى مؤسستك اشتراك Azure صالح. إذا لم يكن لديك اشتراك Azure موجود، يمكنك التسجيل للحصول على أحد الخيارات التالية:

    - [التسجيل للحصول على اشتراك Azure مجاني لمدة سنة واحدة](https://azure.microsoft.com/free)

    - [التسجيل للحصول على اشتراك Pay-As-You-Go Azure](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > لا يدعم [اشتراك Azure Active Directory المجاني](use-your-free-azure-ad-subscription-in-office-365.md) المضمن مع اشتراكك في Microsoft 365 الموصلات في مدخل التوافق.

- يمكن لموصل صفحات Facebook Business استيراد إجمالي 200000 عنصر في يوم واحد. إذا كان هناك أكثر من 200000 عنصر في Facebook Business في يوم واحد، فلن يتم استيراد أي من هذه العناصر إلى Microsoft 365.

- يجب تعيين دور موصل البيانات مسؤول للمستخدم الذي يقوم بإعداد الموصل المخصص في مدخل التوافق (في الخطوة 5). هذا الدور مطلوب لإضافة موصلات على صفحة **موصلات البيانات** في مدخل التوافق. تتم إضافة هذا الدور بشكل افتراضي إلى مجموعات أدوار متعددة. للحصول على قائمة بمجموعات الأدوار هذه، راجع قسم "الأدوار في مراكز الأمان والتوافق" في ["الأذونات" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). بدلا من ذلك، يمكن للمسؤول في مؤسستك إنشاء مجموعة أدوار مخصصة، وتعيين دور موصل البيانات مسؤول، ثم إضافة المستخدمين المناسبين كأعضاء. للحصول على الإرشادات، راجع المقطع "إنشاء مجموعة أدوار مخصصة" في ["الأذونات" في مدخل التوافق في Microsoft Purview](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-create-an-app-in-azure-active-directory"></a>الخطوة 1: إنشاء تطبيق في Azure Active Directory

الخطوة الأولى هي تسجيل تطبيق جديد في Azure Active Directory (AAD). يتوافق هذا التطبيق مع مورد تطبيق الويب الذي تنفذه في الخطوة 4 والخطوة 5 لموصل Facebook.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إنشاء تطبيق في Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

أثناء إكمال هذه الخطوة (باستخدام الإرشادات خطوة بخطوة السابقة)، ستحفظ المعلومات التالية في ملف نصي. يتم استخدام هذه القيم في خطوات لاحقة في عملية النشر.

- معرف تطبيق AAD

- سر تطبيق AAD

- معرف المستأجر

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>الخطوة 2: نشر خدمة الويب للموصل من GitHub إلى حساب Azure الخاص بك

الخطوة التالية هي نشر التعليمات البرمجية المصدر لتطبيق موصل صفحات Facebook Business الذي سيستخدم واجهة برمجة تطبيقات Facebook للاتصال بحساب Facebook واستخراج البيانات حتى تتمكن من استيرادها إلى Microsoft 365. سيقوم موصل Facebook الذي تنشره لمؤسستك بتحميل العناصر من صفحات Facebook Business إلى موقع تخزين Azure الذي تم إنشاؤه في هذه الخطوة. بعد إنشاء موصل صفحات عمل Facebook في مدخل التوافق (في الخطوة 5)، ستقوم خدمة الاستيراد بنسخ بيانات صفحات أعمال Facebook من موقع تخزين Azure إلى علبة بريد في مؤسسة Microsoft 365. كما هو موضح سابقا في قسم [المتطلبات الأساسية](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) ، يجب أن يكون لديك اشتراك Azure صالح لإنشاء حساب Azure Storage.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [نشر خدمة الويب للموصل من GitHub إلى حساب Azure الخاص بك](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

في الإرشادات المفصلة خطوة بخطوة لإكمال هذه الخطوة، ستوفر المعلومات التالية:

- APISecretKey: يمكنك إنشاء هذا السر أثناء إكمال هذه الخطوة. يتم استخدامه في الخطوة 5.

- TenantId: معرف المستأجر لمؤسسة Microsoft 365 التي نسختها بعد إنشاء تطبيق موصل Facebook في Azure Active Directory في الخطوة 1.

بعد إكمال هذه الخطوة، تأكد من نسخ عنوان URL لخدمة تطبيق Azure (على سبيل المثال، https://fbconnector.azurewebsites.net). تحتاج إلى استخدام عنوان URL هذا لإكمال الخطوة 3 والخطوة 4 والخطوة 5).

## <a name="step-3-register-the-web-app-on-facebook"></a>الخطوة 3: تسجيل تطبيق الويب على Facebook

الخطوة التالية هي إنشاء تطبيق جديد وتكوينه على Facebook. يستخدم موصل صفحات الأعمال في Facebook الذي تقوم بإنشائه في الخطوة 5 تطبيق Facebook على الويب للتفاعل مع واجهة برمجة تطبيقات Facebook للحصول على بيانات من صفحات Facebook Business الخاصة بمؤسستك.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [تسجيل تطبيق Facebook](deploy-facebook-connector.md#step-3-register-the-facebook-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، يمكنك حفظ المعلومات التالية في ملف نصي. يتم استخدام هذه القيم لتكوين تطبيق موصل Facebook في الخطوة 4.

- معرف تطبيق Facebook

- سر تطبيق Facebook

- التحقق من الرمز المميز لخطافات ويب Facebook

## <a name="step-4-configure-the-facebook-connector-app"></a>الخطوة 4: تكوين تطبيق موصل Facebook

الخطوة التالية هي إضافة إعدادات التكوين إلى تطبيق موصل Facebook الذي قمت بتحميله عند إنشاء مورد تطبيق ويب Azure في الخطوة 1. يمكنك القيام بذلك عن طريق الانتقال إلى الصفحة الرئيسية لتطبيق الموصل وتكوينه.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [تكوين تطبيق موصل Facebook](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، يمكنك توفير المعلومات التالية (التي قمت بنسخها إلى ملف نصي بعد إكمال الخطوات السابقة):

- معرف تطبيق Facebook (تم الحصول عليه في الخطوة 3)

- سر تطبيق Facebook (تم الحصول عليه في الخطوة 3)

- الرمز المميز للتحقق من خطافات ويب Facebook (تم الحصول عليه في الخطوة 3)

- معرف تطبيق Azure Active Directory (معرف تطبيق AAD الذي تم الحصول عليه في الخطوة 1)

- سر تطبيق Azure Active Directory (سر تطبيق AAD الذي تم الحصول عليه في الخطوة 1)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>الخطوة 5: إعداد موصل صفحات Facebook Business في مدخل التوافق

الخطوة الأخيرة هي إعداد الموصل في مدخل التوافق الذي سيستورد البيانات من صفحات Facebook Business إلى علبة بريد محددة في Microsoft 365. بعد إكمال هذه الخطوة، ستبدأ خدمة استيراد Microsoft 365 في استيراد البيانات من صفحات Facebook Business إلى Microsoft 365.

للحصول على إرشادات مفصلة خطوة بخطوة، راجع [الخطوة 5: إعداد موصل Facebook في مدخل التوافق](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

أثناء إكمال هذه الخطوة (باتباع الإرشادات المفصلة خطوة بخطوة)، يمكنك توفير المعلومات التالية (التي قمت بنسخها إلى ملف نصي بعد إكمال الخطوات).

- معرف تطبيق AAD (تم الحصول عليه في الخطوة 1)

- URL خدمة تطبيق Azure (تم الحصول عليه في الخطوة 1؛ على سبيل المثال، https://fbconnector.azurewebsites.net)

- APISecretKey (التي قمت بإنشائها في الخطوة 2)
