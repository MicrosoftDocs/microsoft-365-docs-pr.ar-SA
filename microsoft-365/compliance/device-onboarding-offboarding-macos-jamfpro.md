---
title: إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام JAMF Pro
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: تعرف على كيفية إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام JAMF Pro
ms.openlocfilehash: bf15868b865afa80146df2b16199caf360a55ce2
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953416"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام JAMF Pro

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكنك استخدام PRO JAMF لإلحاق أجهزة macOS في حلول Microsoft Purview مثل منع فقدان بيانات نقطة النهاية.

> [!IMPORTANT]
> استخدم هذا الإجراء إذا ***لم يكن*** لديك Microsoft Defender لنقطة النهاية (MDE) منشورة على أجهزة macOS

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

## <a name="before-you-begin"></a>قبل البدء

- تأكد من [إدارة أجهزة macOS من خلال JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) ومقترنة بهوية (انضم Azure AD إلى UPN) من خلال JAMF الاتصال أو Intune.
- تثبيت مستعرض v95+ Edge على أجهزة macOS

## <a name="onboard-devices-into-microsoft-purview-solutions-using-jamf-pro"></a>إلحاق الأجهزة في حلول Microsoft Purview باستخدام JAMF Pro

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل|مصدر|
|---|---|
|حزمة الإلحاق|تم التنزيل من **حزمة الإلحاق** لمدخل التوافق، اسم الملف *DeviceComplianceOnboarding.plist*|
|امكانيه الوصول|[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص|[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|عامل تصفية الشبكة| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|ملحقات النظام|[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|تفضيل MDE|[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|تفضيل MAU|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|حزمة التثبيت|تم التنزيل من **حزمة تثبيت** مدخل التوافق، اسم *\*الملف wdav.pkg*\*|

> [!TIP]
> يمكنك تنزيل ملفات *.mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
>
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>إذا تم تحديث أي من هذه الملفات الفردية، فستحتاج إلى تنزيل إما الملف المدمج مرة أخرى أو الملف المحدث الفردي بشكل فردي.

إعداد جهاز macOS في حلول التوافق هو عملية متعددة الأطوار.

### <a name="get-the-device-onboarding-package"></a>الحصول على حزمة إلحاق الجهاز

1. في **مركز التوافق**، افتح **الإعدادات** >  **الحاق** بالمتلحق واختر **"إلحاق".**

1. **لتحديد نظام التشغيل لبدء عملية الإلحاق**، اختر **macOS**

1. **لأسلوب النشر**، اختر **إدارة الجهاز/Microsoft Intune الجوال**

1. اختيار **تنزيل حزمة الإلحاق**

1. استخراج محتويات حزمة إلحاق الجهاز. في مجلد JAMF، يجب أن تشاهد ملف *DeviceComplainceOnboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>إنشاء ملف تعريف تكوين Pro JAMF لحزمة الإلحاق

1. إنشاء ملف تعريف تكوين جديد في PRO JAMF. راجع [دليل مسؤولي PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP onboarding for macOS`
    - وصف: `MDATP EDR onboarding for macOS`
    - الفئه: `none`
    - طريقة التوزيع: `install automatically`
    - مستوي: `computer level`

2. في وحدة تحكم PRO JAMF > **التطبيق & إعدادات مخصصة**، اختر **تحميل** ثم **إضافة**. استخدم هذه القيمة:
    - مجال التفضيل: `com.microsoft.wdav.atp`

3. اختر **التحميل** وحدد ملف الإلحاق **DeviceComplianceOnboarding.plist**.

4. اختر علامة تبويب **النطاق** .

5. اختر أجهزة الكمبيوتر الهدف.

6. اختر **"حفظ**".

7. اختر **"تم**".

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>تكوين مجال التفضيل باستخدام وحدة تحكم JAMF PRO

> [!IMPORTANT]
> يجب استخدام ***com.microsoft.wdav** _ كقيمة مجال التفضيل. يستخدم Microsoft Defender لنقطة النهاية هذا الاسم و_ *_com.microsoft.wdav.ext_** لتحميل إعداداته المدارة.

1. إنشاء ملف تعريف تكوين جديد في PRO JAMF. راجع [دليل مسؤولي PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP MDAV configuration settings`
    - الوصف: اترك هذا فارغا
    - الفئه: `none`
    - طريقة التوزيع: `install automatically`
    - مستوي: `computer level`

1. في علامة التبويب **"تطبيق & Custom الإعدادات**"، اختر **"تطبيقات خارجية**"، واختر **"إضافة**" واختر **"مخطط مخصص**" لمجال التفضيل. استخدم هذه القيمة:
    - مجال التفضيل: `com.microsoft.wdav`

1. اختر **"إضافة مخطط"** **و"Upload**" لتحميل ملف *schema.json*.

1. اختر **"حفظ**".

1. ضمن **"خصائص مجال التفضيل"** اختر هذه الإعدادات
    - ميزات
        - استخدام ملحقات النظام: `enabled` - مطلوب لملحقات الشبكة على Catalina
        - استخدام منع فقدان البيانات: `enabled`
    - محرك الحماية من الفيروسات > الوضع السلبي: `true|false`. يستخدم `true`في حالة نشر DLP فقط. استخدام `false` قيمة أو عدم تعيينها في حالة نشر DLP و Microsoft Defender لنقطة النهاية (MDE).

1. اختر علامة التبويب **"نطاق** ".

1. اختر المجموعات التي تريد نشر ملف تعريف التكوين هذا إليها.

1. اختر **"حفظ**".

### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>إنشاء ملف تعريف تكوين ونشره ل Microsoft AutoUpdate (MAU)

1. إنشاء ملف تكوين PRO JAMF باستخدام **com.microsoft.autoupdate2.plist**. راجع [دليل مسؤولي PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP MDAV MAU settings`
    - وصف: `Microsoft AutoUPdate settings for MDATP for macOS`
    - الفئه: `none`
    - طريقة التوزيع: `install automatically`
    - مستوي: `computer level`

1. في **تطبيق & الإعدادات المخصصة** اختر **Upload** **وإضافة**.

1. في **مجال التفضيلات**، أدخل `com.microsoft.autoupdate2` ثم اختر **Upload**.

1. اختر ملف **com.microsoft.autoupdate2.plist** .

1. اختر **"حفظ**".

1. اختر علامة التبويب **"نطاق** ".

1. اختر أجهزة الكمبيوتر الهدف.

1. اختر **"حفظ**".

1. اختر **"تم**".

### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>إنشاء ملف تعريف تكوين وتوزيعه لمنح حق الوصول الكامل إلى القرص

1. استخدم ملف **fulldisk.mobileconfig** .

1. Upload ملف **fulldisk.mobileconfig** إلى JAMF. راجع [نشر ملفات تعريف التكوين المخصصة باستخدام PRO JAMF](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>إنشاء ملف تعريف تكوين ونشره لملحقات النظام

1. إنشاء ملف تكوين Pro JAMF باستخدام الإجراءات في [دليل مسؤولي PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP MDAV System Extensions`
    - وصف: `MDATP system extensions`
    - الفئه: `none`
    - طريقة التوزيع: `install automatically`
    - مستوي: `computer level`

1. في ملف تعريف **ملحقات النظام** ، أدخل هذه القيم:
    - اسم العرض: `Microsoft Corp. System Extensions`
    - أنواع ملحقات النظام: `Allowed System Extensions`
    - معرف الفريق: `UBF8T346G9`
    - ملحقات النظام المسموح بها: `com.microsoft.wdav.epsext`و `com.microsoft.wdav.netext`

1. اختر علامة التبويب **"نطاق** ".

1. اختر أجهزة الكمبيوتر الهدف.

1. اختر **"حفظ**".

1. اختر **"تم**".

### <a name="configure-network-extension"></a>تكوين ملحق الشبكة

1. استخدم ملف **netfilter.mobileconfig** الذي قمت بتنزيله من GitHub.

2. Upload إلى JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصصة باستخدام Pro Jamf](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>منح إمكانية وصول ذوي الاحتياجات الخاصة إلى DLP

1. استخدم ملف **accessibility.mobileconfig** الذي قمت بتنزيله من GitHub.

2. Upload إلى JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصصة باستخدام Pro Jamf](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>الحصول على حزمة التثبيت

1. في **مركز التوافق**، افتح **الإعدادات** >  **الحاق** بالمتلحق واختر **"إلحاق".**

1. **لتحديد نظام التشغيل لبدء عملية الإلحاق**، اختر **macOS**

1. **لأسلوب النشر**، اختر **إدارة الجهاز/Microsoft Intune الجوال**

1. اختر **تنزيل حزمة التثبيت**. سيمنحك هذا ملف *wdav.pkg* .

### <a name="deploy-the-installation-package"></a>نشر حزمة التثبيت

1. انتقل إلى المكان الذي حفظت الملف فيه `wdav.pkg` .

1. افتح لوحة معلومات PRO JAMF.

1. حدد الكمبيوتر وانقر فوق الترس في الأعلى، ثم اختر **إدارة الكمبيوتر**.

1. في **الحزم** ، اختر **+New**. أدخل هذه التفاصيل:
    - اسم العرض: اتركه فارغا لأنه ستتم إعادة تعيينه عند اختيار ملف .pkg.
    - الفئة: بلا (افتراضي)
    - اسم الملف: اختر ملفا، في هذه الحالة `wdav.pkg` الملف.

1. اختر **"فتح**". تعيين:
    - **اسم العرض**: `Microsoft Endpoint Technology`
    - **ملف البيان**: غير مطلوب
    - **علامة التبويب "خيارات"**: اترك القيم الافتراضية
    - **علامة التبويب "قيود"**: اترك القيم الافتراضية

1. اختر **"حفظ**". يؤدي ذلك إلى تحميل الحزمة إلى PRO JAMF.

1. افتح صفحة **النهج** .

1. اختر **+جديد** لإنشاء نهج جديد.

1. أدخل هذه القيم
    - **اسم العرض**: `MDATP Onboarding200329 v100.86.92 or later`

1. اختر **"إيداع متكرر**".

1. اختر **"حفظ**".

1. اختر **PackagesConfigure** > .

1. اختر **"إضافة**".

1. اختر **"حفظ**".

1. اختر علامة التبويب **"نطاق** ".

1. حدد أجهزة الكمبيوتر الهدف.

1. اختر **"إضافة**".

1. اختر **الخدمة الذاتية**.

1. اختر **"تم**".

### <a name="check-the-macos-device"></a>التحقق من جهاز macOS

1. أعد تشغيل جهاز macOS.

1. افتح **System** **PreferencesProfiles** > .

1. يجب أن ترى:
    - إمكانية الوصول
    - الوصول إلى القرص الكامل
    - ماو
    - إلحاق MDATP
    - تفضيلات MDE
    - ملف تعريف الإدارة
    - عامل تصفية الشبكة
    - ملف تعريف ملحق النظام

## <a name="offboard-macos-devices-using-jamf-pro"></a>إيقاف تشغيل أجهزة macOS باستخدام JAMF Pro

1. إلغاء تثبيت التطبيق (إذا لم يكن يستخدم MDE)
    1. راجع JAMF Pro Docs - نشر الحزمة - [دليل مسؤول PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) لJamf Pro دليل المسؤول

1. إعادة تشغيل جهاز macOS - قد تفقد بعض التطبيقات وظائف الطباعة حتى تتم إعادة تشغيلها

> [!IMPORTANT]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى 6 أشهر.
