---
title: أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Microsoft Intune (معاينة)
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
description: تعرف على كيفية تشغيل أجهزة macOS أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Microsoft Intune (معاينة)
ms.openlocfilehash: 5f8dd27490992e15d53dfc10311ce7b23b99683a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575126"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview"></a>أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Intune (معاينة)

يمكنك استخدام Intune لتكميل أجهزة macOS Microsoft 365 حلول التوافق.

> [!IMPORTANT]
> استخدم هذا الإجراء ***إذا لم يتم*** نشر Microsoft Defender لنقطة النهاية (MDE) على أجهزة macOS

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>قبل البدء

- تأكد من أن [أجهزة macOS مجهزه في Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) ومسجلة في [Company Portal التطبيق](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- تأكد من إمكانية الوصول إلى إدارة نقاط النهاية من Microsoft[.](https://endpoint.microsoft.com/#home)
- هذا يدعم إصدار macOS Catalina 10.15 والإصدارات الأحدث.
- قم بإنشاء مجموعات المستخدمين التي سيتم تعيين تحديثات التكوين لها.
- تثبيت مستعرض v95+ Edge على أجهزة macOS 


## <a name="onboard-macos-devices-into-microsoft-365-compliance-solutions-using-microsoft-intune"></a>أجهزة macOS المجهزة Microsoft 365 التوافق باستخدام Microsoft Intune

إن عملية احالة جهاز macOS إلى حلول التوافق هي عملية ست مراحل.

1. [إنشاء ملفات تعريف تكوين النظام](#create-system-configuration-profiles)
1. [الحصول على حزمة تشغيل الجهاز](#get-the-device-onboarding-package)
1. [نشر حزمة التكهين](#deploy-the-onboarding-package)
1. [تمكين ملحق النظام](#enable-system-extension)
1. [الحصول على حزمة التثبيت](#get-the-installation-package)
1. [نشر حزمة التثبيت](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>إنشاء ملفات تعريف تكوين النظام

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |المصدر |
|---------|---------|
|حزمة التكهين    |التي تم تنزيلها من حزمة **"التكهين" لمدخل التوافق**، اسم *الملف* DeviceComplianceOnboarding.xml |
|إمكانية وصول ذوي الاحتياجات الخاصة |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|ملف الشبكة| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|ملحقات النظام |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|تفضيل MDE     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|تفضيل MAU|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|حزمة التثبيت     |تم التنزيل من حزمة تثبيت مدخل **التوافق**، اسم *\*الملف wdav.pkg*\* |

> [!TIP]
> يمكنك تنزيل *ملفات .mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - ملحقات النظام
>
>إذا تم تحديث أي من هذه الملفات الفردية، ستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث المفرد كل على حدة.

<!--2. Copy this code and save it in a file named `com.microsoft.autoupdate2.xml`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
            <key>PayloadUUID</key>
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```
-->

2. افتح إدارة نقاط النهاية من Microsoft النملفات تعريف تكوين **في** **الوسط** >  > .

1. اختر: **إنشاء ملف تعريف** 

1. اختر:
    1. **Platform = macOS**
    1. **نوع ملف التعريف = القوالب**
    1. **اسم القالب = مخصص**

1. اختر **إنشاء**

1. اختر اسما لملف التعريف، مثل *AccessibilityformacOS* في هذا المثال. اختر **التالي**.

1. اختر **ملف accessibility.mobileconfig** الذي قمت بتنزيلها في الخطوة 1 كملف ملف تعريف التكوين.

1. اختر **التالي**

1. على علامة **التبويب** الواجبات، أضف المجموعة التي تريد نشر هذه التكوينات لها واختر **التالي**.

1. راجع الإعدادات **واختر إنشاء** لنشر التكوين.

1. كرر الخطوات من 3 إلى 11 لإنشاء ملفات تعريف ل:
    1. **fulldisk.mobileconfig** file
    1. **com.microsoft.autoupdate2.xml** الملف
    1. تفضيلات MDE **com.microsoft.wdav.xml** ملف
        1. تعيين مشغل برنامج الحماية من الفيروسات `passive mode` = `true` أو .`false` استخدم `true`في حالة نشر DLP فقط. استخدم `false` قيمة أو لا تقوم بتعيينها في حالة نشر DLP و Microsoft Defender لنقطة النهاية (MDE).
    1. **netfilter.mobileconfig**
 
1. افتح **ملفات تعريف تكوين** >  **الأجهزة**، يجب أن ترى ملفات التعريف التي تم إنشاؤها هناك.

1. في الصفحة **ملفات تعريف** التكوين، اختر ملف التعريف الذي أنشأته للتو، في هذا المثال *AccessibilityformacOS* واختر حالة الجهاز  لرؤية قائمة الأجهزة حالة نشر ملف تعريف التكوين.

### <a name="get-the-device-onboarding-package"></a>الحصول على حزمة تشغيل الجهاز

1. في **مركز التوافق**، **افتح** >  الإعدادات **التدليف** ثم اختر **"التكليف**".
 
1. لتحديد **نظام التشغيل لبدء عملية التكميل،** اختر **macOS**.
 
1. **لطريقة النشر**، اختر **إدارة/** Microsoft Intune.
 
1. اختر **تنزيل حزمة الboarding**. يحتوي هذا على التعليمات البرمجية لتك جديدة في *DeviceComplianceOnboarding.xml* .

### <a name="deploy-the-onboarding-package"></a>نشر حزمة التكهين

1. افتح إدارة نقاط النهاية من Microsoft النملفات تعريف تكوين **في** **الوسط** >  > .

1. اختر: **إنشاء ملف تعريف**. 

1. اختر:
    1. **Platform = macOS**
    1. **نوع ملف التعريف = القوالب**
    1. **اسم القالب = مخصص**

1. اختر **إنشاء**

1. اختر اسما لملف التعريف، مثل *OnboardingPackage* في هذا المثال. اختر **التالي**.

1. اختر *DeviceComplianceOnboarding.xmlالملف* كملف ملف تعريف التكوين.

1. اختر **التالي**

1. على علامة **التبويب** الواجبات، أضف المجموعة التي تريد نشر هذه التكوينات لها واختر **التالي**.

1. راجع الإعدادات **واختر إنشاء** لنشر التكوين.

### <a name="enable-system-extension"></a>تمكين ملحق النظام

1. في إدارة نقاط النهاية من Microsoft **،** حدد **إنشاء ملف تعريف** ضمن **ملفات تعريف التكوين**

1. اختر:
    1. **Platform = macOS**
    1. **نوع ملف التعريف = القوالب**
    1. **اسم القالب = الملحقات**

1. اختر **إنشاء**

1. في علامة **التبويب أساسيات** ، امنح ملف التعريف الجديد هذا اسما.

1. في علامة **التبويب إعدادات** التكوين، قم بتوسيع **ملحقات النظام**.

1. ضمن **معرف الحزمة** **ومعرف الفريق**، قم بتعيين هذه القيم

|معرف الحزمة  |معرف الفريق  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. على علامة **التبويب** الواجبات، أضف المجموعة التي تريد نشر هذه التكوينات لها واختر **التالي**.

1. اختر **التالي** لنشر التكوين.

### <a name="get-the-installation-package"></a>الحصول على حزمة التثبيت

1. في **مركز التوافق**، **افتح** >  الإعدادات **التدليف** ثم اختر **"التكليف**".
 
1. لتحديد **نظام التشغيل لبدء عملية التوسيع،** اختر **macOS**
 
1. **لطريقة النشر**، اختر **إدارة/** Microsoft Intune
 
1. اختر **تنزيل حزمة التثبيت**. سيمنحك ذلك *ملف wdav.pkg* .

> [!IMPORTANT]
> قبل أن تتمكن من نشر *wdav.pkg.* حزمة عبر Intune، يجب إعادة تنسيقها باستخدام أدوات التفاف تطبيق *Intune for Mac* بتنسيق *wdav.pkg.intunemac* .
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>نشر حزمة تثبيت Microsoft DLP

1. اتبع الإجراءات في كيفية إضافة تطبيقات [خط عمل macOS (LOB) إلى Microsoft Intune](/mem/intune/apps/lob-apps-macos) لتحويل ملف *wdav.pkg* إلى التنسيق المناسب ونشره من خلال Intune.

## <a name="offboard-macos-devices-using-intune"></a>إيقاف تشغيل أجهزة macOS باستخدام Intune

> [!NOTE]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى ستة أشهر.

2. في **إدارة نقاط النهاية من Microsoft،** افتح **ملفات تعريف تكوين** >  **الأجهزة**، يجب أن ترى ملفات التعريف التي تم إنشاؤها هناك.

1. في الصفحة **ملفات تعريف التكوين** ، اختر *ملف تعريف wdav.pkg.intunemac* .

1. اختر **حالة الجهاز** لرؤية قائمة الأجهزة حالة نشر ملف تعريف التكوين

1. فتح **الخصائص** **والواجبات**

1. إزالة المجموعة من الواجب. سيتم إلغاء تثبيت حزمة *wdav.pkg.intunemac* وإبدال جهاز macOS من حلول التوافق.
