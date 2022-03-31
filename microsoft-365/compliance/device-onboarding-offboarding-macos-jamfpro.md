---
title: أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro (معاينة)
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
description: تعرف على كيفية تشغيل أجهزة macOS وإبقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro (معاينة)
ms.openlocfilehash: e66c9ba88e7c829af3695675a72e264da17e7dc4
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63578535"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview"></a>أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro (معاينة)

يمكنك استخدام JAMF Pro أجهزة macOS المجهزة في Microsoft 365 التوافق مثل منع فقدان بيانات نقطة النهاية.

> [!IMPORTANT]
> استخدم هذا الإجراء ***إذا لم يتم*** نشر Microsoft Defender لنقطة النهاية (MDE) على أجهزة macOS

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>قبل البدء

- تأكد من إدارة أجهزة [macOS من خلال JAMF pro](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/) ومقترنة بهوية (Azure AD انضم إلى UPN) من خلال JAMF الاتصال Intune.
- تثبيت مستعرض v95+ Edge على أجهزة macOS 

## <a name="onboard-devices-into-microsoft-365-compliance-solutions-using-jamf-pro"></a>الأجهزة المجهزة في Microsoft 365 التوافق باستخدام JAMF Pro

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |المصدر |
|---------|---------|
|حزمة التكهين    |تم التنزيل من حزمة **"االتعبئة" في مدخل التوافق**، اسم الملف *DeviceComplianceOnboarding.plist* |
|إمكانية وصول ذوي الاحتياجات الخاصة |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|عامل تصفية الشبكة| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)
|ملحقات النظام |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|تفضيل MDE     |[schema.json](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/schema.json)|
|تفضيل MAU|[com.microsoft.autoupdate2.plist](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.plist)|
|حزمة التثبيت     |تم التنزيل من حزمة تثبيت مدخل **التوافق**، اسم *\*الملف wdav.pkg*\* |

> [!TIP]
> يمكنك تنزيل *ملفات .mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - sysext.mobileconfig
>
>إذا تم تحديث أي من هذه الملفات الفردية، ستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث المفرد كل على حدة.

إن عملية تكميل جهاز macOS في حلول التوافق هي عملية متعددة ال وقت.

### <a name="get-the-device-onboarding-package"></a>الحصول على حزمة تشغيل الجهاز

1. في **مركز التوافق**، **افتح** >  الإعدادات **التدليف** ثم اختر **"التكليف**".
 
1. لتحديد **نظام التشغيل لبدء عملية التوسيع،** اختر **macOS**
 
1. **لطريقة النشر**، اختر **إدارة/** Microsoft Intune
 
1. اختر **تنزيل حزمة التكهيل**
 
1. استخراج محتويات حزمة اضمان الجهاز. في مجلد JAMF، يجب أن ترى *ملف DeviceComplainceOnboarding.plist* .

### <a name="create-a-jamf-pro-configuration-profile-for-the-onboarding-package"></a>إنشاء ملف تعريف Pro JAMF لحزمة التهيئة

1. إنشاء ملف تعريف تكوين جديد في JAMF Pro. راجع دليل [PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP onboarding for macOS`
    - الوصف: `MDATP EDR onboarding for macOS`
    - الفئة: `none`
    - طريقة التوزيع: `install automatically`
    - المستوى: `computer level`

2. في ملف التحكم JAMF Pro التحكم > **التطبيق & إعدادات** مخصصة، اختر **تحميل** ثم **أضف**. استخدم هذه القيمة:
    - مجال التفضيل: `com.microsoft.wdav.atp`

3. اختر **تحميل** وحدد ملف الالتحميل **DeviceComplianceOnboarding.plist**.

4. اختر **علامة تبويب** النطاق.

5. اختر أجهزة الكمبيوتر الهدف.

6. اختر **حفظ**.

7. اختر **تم**.

### <a name="configure-preference-domain-using-the-jamf-pro-console"></a>تكوين مجال التفضيل باستخدام وحدة تحكم JAMF PRO

> [!IMPORTANT]
> يجب استخدام ***com.microsoft.wdav** _ كقيمة مجال التفضيل. يستخدم Microsoft Defender ل Endpoint هذا الاسم و_ *_com.microsoft.wdav.ext_** لتحميل إعداداته المدارة.

1. إنشاء ملف تعريف تكوين جديد في JAMF Pro. راجع دليل [PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP MDAV configuration settings`
    - الوصف: اترك هذا فارغا
    - الفئة: `none`
    - طريقة التوزيع: `install automatically`
    - المستوى: `computer level`

1. في علامة **التبويب & تطبيق الإعدادات**، اختر تطبيقات خارجية، واختر **إضافة واختر** مخطط **مخصص لمجال** التفضيل. استخدم هذه القيمة:
    - مجال التفضيل: `com.microsoft.wdav`

1. اختر **إضافة مخطط** **Upload** لتحميل *ملف schema.json*.

1. اختر **حفظ**.

1. ضمن **خصائص مجال التفضيل** ، اختر هذه الإعدادات
    - الميزات 
        - استخدام ملحقات النظام: `enabled` - مطلوب لملحقات الشبكة على كاتالينا
        - استخدام منع فقدان البيانات: `enabled`
    - محرك الحماية من الفيروسات > السلبي: `true|false`. استخدم `true`في حالة نشر DLP فقط. استخدم `false` قيمة أو لا تقوم بتعيينها في حالة نشر DLP و Microsoft Defender لنقطة النهاية (MDE).

1. اختر علامة **التبويب** نطاق.

1. اختر المجموعات لنشر ملف تعريف التكوين هذا لها.

1. اختر **حفظ**. 


### <a name="create-and-deploy-a-configuration-profile-for-microsoft-autoupdate-mau"></a>إنشاء ملف تعريف تكوين ل Microsoft AutoUpdate (MAU) ونشره

1. أنشئ ملف تكوين PRO JAMF باستخدام **com.microsoft.autoupdate2.plist**. راجع دليل [PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP MDAV MAU settings`
    - الوصف: `Microsoft AutoUPdate settings for MDATP for macOS`
    - الفئة: `none`
    - طريقة التوزيع: `install automatically`
    - المستوى: `computer level`

1. في **تطبيق & مخصص الإعدادات** **اختر Upload** **وإضافة**.

1. في **التفضيلات أدخل المجال** `com.microsoft.autoupdate2` **ثم اختر Upload**.

1. اختر **الملف com.microsoft.autoupdate2.plist** .

1. اختر **حفظ**.

1. اختر علامة **التبويب** نطاق.

1. اختر أجهزة الكمبيوتر الهدف.

1. اختر **حفظ**.

1. اختر **تم**.


### <a name="create-and-deploy-a-configuration-profile-for-grant-full-disk-access"></a>إنشاء ملف تعريف تكوين ونشره لمنح الوصول الكامل إلى القرص

1. استخدم **ملف fulldisk.mobileconfig** .

1. Upload **ملف fulldisk.mobileconfig** إلى JAMF. راجع نشر [ملفات تعريف التكوين المخصصة باستخدام JAMF Pro](https://docs.jamf.com/technical-articles/Deploying_Custom_Configuration_Profiles_Using_Jamf_Pro.html).

### <a name="create-and-deploy-a-configuration-profile-for-system-extensions"></a>إنشاء ملف تعريف تكوين لملحقات النظام ونشره

1. قم بإنشاء ملف Pro JAMF باستخدام الإجراءات في [دليل مسؤولي PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/). استخدم هذه القيم:
    - الاسم: `MDATP MDAV System Extensions`
    - الوصف: `MDATP system extensions`
    - الفئة: `none`
    - طريقة التوزيع: `install automatically`
    - المستوى: `computer level`

1. في **ملف تعريف ملحقات** النظام، أدخل هذه القيم:
    - اسم العرض: `Microsoft Corp. System Extensions`
    - أنواع ملحقات النظام: `Allowed System Extensions`
    - معرف الفريق: `UBF8T346G9`
    - ملحقات النظام المسموح بها: `com.microsoft.wdav.epsext`و و `com.microsoft.wdav.netext`

1. اختر علامة **التبويب** نطاق.

1. اختر أجهزة الكمبيوتر الهدف.

1. اختر **حفظ**.

1. اختر **تم**.

### <a name="configure-network-extension"></a>تكوين ملحق الشبكة

1.  استخدم **ملف netfilter.mobileconfig** الذي قمت بتنزيلها من GitHub.

2.  Upload إلى JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصص باستخدام Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="grant-accessibility-access-to-dlp"></a>منح إمكانية وصول ذوي الاحتياجات الخاصة إلى DLP

1. استخدم **ملف accessibility.mobileconfig** الذي قمت بتنزيلها من GitHub.

2.  Upload إلى JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصص باستخدام Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

### <a name="get-the-installation-package"></a>الحصول على حزمة التثبيت

1. في **مركز التوافق**، **افتح** >  الإعدادات **التدليف** ثم اختر **"التكليف**".
 
1. لتحديد **نظام التشغيل لبدء عملية التوسيع،** اختر **macOS**
 
1. **لطريقة النشر**، اختر **إدارة/** Microsoft Intune
 
1. اختر **تنزيل حزمة التثبيت**. سيمنحك ذلك *ملف wdav.pkg* .


### <a name="deploy-the-installation-package"></a>نشر حزمة التثبيت

1. انتقل إلى المكان حيث حفظت `wdav.pkg` الملف.

1. افتح لوحة معلومات PRO JAMF.

1. حدد الكمبيوتر وانقر فوق الترس في الأعلى، ثم اختر **إدارة الكمبيوتر**.

1. في **الحزم،** اختر **+جديد**. أدخل هذه التفاصيل:
    - اسم العرض: اتركه فارغا لأنه سيعاد تعيينه عند اختيار ملف pkg.
    - الفئة: بلا (افتراضي)
    - اسم الملف: اختر ملفا، وفي هذه الحالة `wdav.pkg` الملف.

1. اختر **فتح**. تعيين:
    - **اسم العرض**: `Microsoft Endpoint Technology`
    - **ملف بيان**: غير مطلوب
    - **علامة التبويب "خيارات"**: ترك القيم الافتراضية
    - **علامة التبويب "قيود"**: ترك القيم الافتراضية

1. اختر **حفظ**. يتم من خلال ذلك تحميل الحزمة إلى JAMF Pro.

1. افتح **صفحة "السياسات** ".

1. اختر **+جديد** لإنشاء نهج جديد.

1. أدخل هذه القيم
    - **اسم العرض**: `MDATP Onboarding200329 v100.86.92 or later`

1. اختر **تسجيل الدخول المتكرر**.

1. اختر **حفظ**.

1. اختر **PackagesConfigure** > .

1. اختر **إضافة**.

1. اختر **حفظ**. 

1. اختر علامة **التبويب** نطاق.

1. حدد أجهزة الكمبيوتر الهدف.

1. اختر **إضافة**.

1. اختر **الخدمة الذاتية**.

1. اختر **تم**.

### <a name="check-the-macos-device"></a>التحقق من جهاز macOS 

1. أعد تشغيل جهاز macOS.

1. افتح **تفضيلات** **النظامProfiles** > .

1. من المفترض أن ترى:
    - Accessiblity
    - الوصول إلى القرص الكامل
    - MAU
    - MDATP Onboarding
    - تفضيلات MDE
    - ملف تعريف الإدارة
    - عامل تصفية الشبكة
    - ملف تعريف ملحق النظام

## <a name="offboard-macos-devices-using-jamf-pro"></a>إيقاف تشغيل أجهزة macOS باستخدام JAMF Pro

1. إلغاء تثبيت التطبيق (إذا لم يكن يستخدم MDE)
    1. راجع JAMF Pro Docs - نشر الحزمة - [دليل PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) دليل مسؤول Pro دليل المسؤول

1. إعادة تشغيل جهاز macOS - قد تفقد بعض التطبيقات وظائف الطباعة حتى تتم إعادة تشغيلها

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.
