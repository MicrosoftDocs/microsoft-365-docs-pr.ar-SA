---
title: إعداد المكون الإضافي لـ Moodle وتكوينه لـ Open LMS
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: استعد لدمج One LMS وMicrosoft Teams من خلال إعداد المكون الإضافي Moodle وتكوينه.
ms.openlocfilehash: e59d9298d61060f4d898e773cc5800d32e86bebf
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66857398"
---
# <a name="set-up-and-configure-the-moodle-plugin"></a>إعداد المكون الإضافي لـ Moodle وتكوينه

في هذه المقالة، ستتعلم كيفية تثبيت المكون الإضافي Moodle وتكوينه لدمج Microsoft Teams مع تجربة Open LMS.

## <a name="prerequisites"></a>المتطلبات الأساسية

فيما يلي المتطلبات الأساسية لتثبيت المكون الإضافي Moodle:

* بيانات اعتماد مسؤول Moodle.
* بيانات اعتماد المسؤول Microsoft Azure Active Directory (Azure AD).
* اشتراك Azure حيث يمكنك إنشاء موارد جديدة.

## <a name="1-install-the-microsoft-365-moodle-plugin"></a>1. تثبيت المكون الإضافي Microsoft 365 Moodle

يتم تشغيل تكامل LMS المفتوح في Microsoft Teams بواسطة Open Source [مجموعة مكونات Microsoft 365 Moodle الإضافية](https://moodle.org/plugins/browse.php?list=set&id=72).

### <a name="requisite-applications-and-plugins"></a>التطبيقات والمكونات الإضافية المطلوبة

قم بتثبيت العناصر التالية وتنزيلها قبل المتابعة مع تثبيت المكون الإضافي Microsoft 365 Moodle:

1. [إصدار مستقر حالي من Moodle](https://download.moodle.org/releases/latest/).
1. قم بتنزيل ميزة Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) والمكونات الإضافية [ل Microsoft 365 Integration](https://moodle.org/plugins/local_o365) وحفظها على الكمبيوتر المحلي.

    > [!NOTE]
    > يلزم تثبيت المكونين الإضافيين OpenID Connect وMicrosoft 365 Integration من أجل تكامل Teams.
    >
    > يوصى باستخدام المكون الإضافي [لنسق Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) .

### <a name="microsoft-365-moodle-plugins"></a>مكونات Microsoft 365 Moodle الإضافية

#### <a name="install-plugins"></a>تثبيت المكونات الإضافية

1. قم بتنزيل المكونات الإضافية واستخراجها وتحميلها إلى مجلداتها المقابلة. على سبيل المثال، قم باستخراج المكون الإضافي OpenID Connect (auth_oidc) إلى مجلد يسمى **oidc**، ثم قم بتحميله إلى مجلد **المصادقة** الخاص بجذر مستند Moodle.
2. سجل الدخول إلى موقع Moodle كمسؤول وحدد **إدارة الموقع**.
3. عند الكشف عن المكونات الإضافية الجديدة التي سيتم تثبيتها، يجب على Moodle إعادة توجيهك إلى صفحة تثبيت المكونات الإضافية الجديدة. إذا لم يحدث ذلك، في صفحة **إدارة الموقع** ، حدد **الإعلامات** في علامة التبويب **"عام** " حيث يجب أن يؤدي ذلك إلى تثبيت المكونات الإضافية.

    > [!IMPORTANT]
    >
    > * احتفظ بصفحة تكوين مكونات Microsoft 365 Moodle الإضافية مفتوحة في علامة تبويب مستعرض منفصلة حيث تحتاج إلى العودة إلى هذه المجموعة من الصفحات طوال العملية.  
    >
    > * إذا لم يكن لديك موقع موديل موجود، فانتقل إلى [Moodle على مستودع Azure](https://github.com/azure/moodle) ، وانشر مثيل Moodle بسرعة وقم بتخصيصه وفقا لاحتياجاتك.

#### <a name="enable-the-openid-connect-authentication-plugin"></a>تمكين المكون الإضافي لمصادقة OpenID Connect

1. انتقل إلى **مصادقة** **المكونات الإضافية** >  **لإدارة** >  الموقع ثم حدد **"إدارة المصادقة**".
1. ابحث عن المكون الإضافي لمصادقة **OpenID Connect** وحدد *أيقونة العين* لتمكينه.
1. حدد **إعدادات** المكون الإضافي للتحقق من نقاط نهاية **التخويل** **والرمز المميز** .
    1. يجب أن تكون القيم الافتراضية:
        1. نقطة نهاية التخويل: ``https://login.microsoftonline.com/common/oauth2/authorize``.
        1. نقطة نهاية الرمز المميز: ``https://login.microsoftonline.com/common/oauth2/token``.
1. سجل **URI إعادة التوجيه** لاستخدامه لاحقا.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. تكوين الاتصال بين مكونات Microsoft 365 الإضافية Azure AD

يجب تكوين الاتصال بين مكونات Microsoft 365 الإضافية Azure AD.

### <a name="requisites"></a>لوازم

سجل Moodle كتطبيق في Azure AD، باستخدام البرنامج النصي PowerShell. البرنامج النصي توفير العناصر التالية:

* تطبيق Azure AD جديد لمستأجر Microsoft 365، والذي يستخدمه Microsoft 365 Moodle Plugins.
* يقوم التطبيق لمستأجر Microsoft 365 بإعداد عناوين URL للرد المطلوبة والأذونات للتطبيق الذي تم توفيره وإرجاع `AppID` `Key`و.

استخدم صفحة إعداد مكونات Microsoft 365 Moodle الإضافية التي تم `AppID` `Key` إنشاؤها وفيها لتكوين موقع خادم Moodle باستخدام Azure AD.

> [!IMPORTANT]
> لمزيد من المعلومات حول تسجيل مثيل Moodle يدويا، راجع [تسجيل مثيل Moodle الخاص بك كتطبيق](https://docs.moodle.org/400/en/Microsoft_365#Azure_App_Creation_and_Configuration).

### <a name="teams-for-open-lms-setup-process"></a>عملية إعداد Teams for Open LMS

1. من صفحة مكونات Microsoft 365 Integration الإضافية، حدد علامة التبويب **"إعداد** ".

1. حدد الزر **"تنزيل البرنامج النصي PowerShell** " واحفظه كمجلد ZIP على الكمبيوتر المحلي.

1. قم بإعداد البرنامج النصي PowerShell من ملف ZIP كما يلي:

    1. قم بتنزيل الملف واستخراجه `Moodle-AzureAD-Powershell.zip` .
    1. افتح المجلد المستخرج.
    1. انقر بزر الماوس الأيمن فوق `Moodle-AzureAD-Script.ps1` الملف وحدد **"Properties**".
    1. ضمن علامة التبويب **"عام**" في okno Vlastnosti، حدد خانة `Unblock` الاختيار الموجودة بجانب سمة **الأمان** الموجودة في أسفل النافذة.
    1. حدد **موافق**.
    1. انسخ مسار الدليل إلى المجلد المستخرج.

1. تشغيل PowerShell كمسؤول:

    1. حدد "ابدأ".
    1. اكتب PowerShell.
    1. انقر بزر الماوس الأيمن فوق **Windows PowerShell**.
    1. حدد **"تشغيل كمسؤول**".

1. انتقل إلى الدليل غير المضغوط عن طريق كتابة `cd .../.../Moodle-AzureAD-Powershell` مكان `.../...` المسار إلى الدليل.

1. تنفيذ البرنامج النصي PowerShell:

    1. أدخل `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. أدخل `./Moodle-AzureAD-Script.ps1`.
    1. سجل الدخول إلى حساب مسؤول Microsoft 365 في النافذة المنبثقة.
    1. أدخل اسم تطبيق Azure AD، على سبيل المثال، الوظائف الإضافية Moodle أو Moodle.
    1. أدخل عنوان URL لخادم Moodle.
    1. انسخ **معرف التطبيق (`AppID`)** **ومفتاح التطبيق (`Key`)** الذي تم إنشاؤه بواسطة البرنامج النصي واحفظهما.

1. ارجع إلى صفحة إدارة المكونات الإضافية،**مصادقة** > **OpenID Connect** الخاصة **بإدارة** >  >  **الموقع**.

1. الصق `AppID` القيمة في مربع **"معرف التطبيق"** والقيمة `Key` في مربع **المفتاح** ، ثم حدد **"حفظ التغييرات**".

1. انتقل إلى **المكونات الإضافية** >  المحلية **لإدارة** >  الموقع وحدد **تكامل Microsoft 365**.

1. في **أسلوب "اختيار الاتصال**"، حدد **"الوصول إلى التطبيق**"، ثم حدد **"حفظ التغييرات"** مرة أخرى.

1. بعد تحديث الصفحة، يمكنك الاطلاع على قسم جديد آخر **مسؤول الموافقة & معلومات إضافية**.
    1. حدد **"توفير مسؤول ارتباط الموافقة**"، أدخل بيانات اعتماد المسؤول العام ل Microsoft 365، ثم **اقبل** لمنح الأذونات.
    1. إلى جانب حقل **المستأجر Azure AD**، حدد الزر **"كشف".**
    1. إلى جانب **عنوان URL OneDrive for Business**، حدد الزر **"كشف**".
    1. بعد ملء الحقول، حدد الزر **"حفظ التغييرات"** مرة أخرى.

1. حدد الزر **"تحديث** " للتحقق من التثبيت، ثم حدد **"حفظ التغييرات**".

1. مزامنة المستخدمين بين خادم Moodle Azure AD. اعتمادا على بيئتك، يمكنك تحديد خيارات مختلفة خلال هذه المرحلة. لبدء الاستخدام:
    1. التبديل إلى **علامة التبويب "إعدادات المزامنة**".

    1. في قسم "**مزامنة المستخدمين" مع Azure AD**، حدد خانات الاختيار التي تنطبق على بيئتك. يجب تحديد الخيارات التالية:  

        ✔ إنشاء حسابات في Open LMS للمستخدمين في Azure AD.

        ✔ تحديث كافة الحسابات في Open LMS للمستخدمين في Azure AD.

    1. في المقطع **"تقييد إنشاء المستخدم**"، يمكنك إعداد عامل تصفية للحد من Azure AD المستخدمين الذين تمت مزامنتهم إلى Open LMS.
    1. في قسم " **مزامنة الدورة التدريبية** "، يمكنك تحديد خيار **تخصيص مزامنة الدورة التدريبية** لتمكين الإنشاء التلقائي للمجموعات وTeams لبعض الدورات التدريبية الحالية في Open LMS أو كلها.

1. للتحقق من صحة مهام [cron](https://docs.moodle.org/400/en/Cron) وتشغيلها يدويا للمرة الأولى، انتقل إلى **المهام المجدولة** **لمهام** > **خادم** >  **إدارة** >  الموقع.

    1. قم بالتمرير لأسفل وابحث عن المهمة "**مزامنة المستخدمين" باستخدام Azure AD** وحدد **"تشغيل الآن**".
        1. ستقوم هذه العملية بمزامنة مستخدم Azure AD إلى موقع Open LMS.
    1. بعد ذلك، ابحث عن **دورات Sync Moodle التدريبية لمهمة Microsoft Teams** وحدد **تشغيل الآن**.
        1. ستنشئ هذه المهمة مجموعات وTeams إذا تم العثور على مالك.
        1. إذا كان المستخدم لديه `local/o365:teamowner` القدرة في سياق الدورة التدريبية، فإن المستخدم هو مالك الفريق. إذا كان المستخدم لديه `local/o365:teammember` القدرة في سياق الدورة التدريبية، يكون المستخدم عضوا في الفريق.  
        1. دور *المعلم* الافتراضي لديه `local/o365:teamowner` القدرة، ودور *الطالب* الافتراضي لديه `local/o365:teammember` القدرة.

    > [!NOTE]
    > يتم تشغيل Moodle [Cron](https://docs.moodle.org/400/en/Scheduled_tasks) وفقا لجدول المهام. يكون الجدول الافتراضي مرة واحدة في اليوم في الساعة 1:00 ص في المنطقة الزمنية المحلية للخادم. ومع ذلك، يجب تشغيل cron بشكل متكرر للحفاظ على كل شيء متزامنا.

1. انتقل إلى المكونات **الإضافية** >  > **المحلية** ل **"** > إدارة الموقع" في علامة التبويب "**إعدادات فرق** **التكامل** > " في Microsoft 365.

1. حدد زر **"Check Moodle settings"** الذي سيقوم بتحديث كافة التكوينات المطلوبة لكي يعمل تكامل Teams.

بعد تثبيت المكونات الإضافية وتكوينها، يمكنك:

* [توزيع Moodle Assistant Bot إلى Azure](/microsoftteams/install-moodle-integration#step-3-deploy-the-moodle-assistant-bot-to-azure).
* [أضف علامات تبويب Moodle إلى فصول Teams](/microsoftteams/install-moodle-integration#step-4-deploy-your-microsoft-teams-app).
* [إضافة فصول واجتماعات Teams إلى Open LMS](open-lms-teams-classes-and-meetings.md).

## <a name="extra-moodle-plugin-documentation"></a>وثائق المكون الإضافي Extra Moodle

إذا كنت ترغب في مراجعة إرشادات تكامل Microsoft 365 الخاصة ب Open LMS وملاحظات الإصدار، فراجع هذه الموارد:

* [وثائق تكامل Microsoft 365 على مستندات Moodle](https://docs.moodle.org/400/en/Microsoft_365).
