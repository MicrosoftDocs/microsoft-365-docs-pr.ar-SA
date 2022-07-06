---
title: إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام Microsoft Intune
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
description: تعرف على كيفية إلحاق أجهزة macOS وإلحاقها بحلول Microsoft Purview باستخدام Microsoft Intune
ms.openlocfilehash: e5cc3ff25895f3eb7557566eb8a38722a1aee35f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632343"
---
# <a name="onboard-and-offboard-macos-devices-into-microsoft-purview-solutions-using-intune"></a>إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام Intune

يمكنك استخدام Intune لإلحاق أجهزة macOS في حلول Microsoft Purview.

> [!IMPORTANT]
> استخدم هذا الإجراء إذا ***لم يكن*** لديك Microsoft Defender لنقطة النهاية (MDE) منشورة على أجهزة macOS

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

## <a name="before-you-begin"></a>قبل البدء

- تأكد من [إلحاق أجهزة macOS في Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) وتسجيلها في [تطبيق Company Portal](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- تأكد من أن لديك حق الوصول إلى [مركز إدارة نقاط النهاية Microsoft](https://endpoint.microsoft.com/#home).
- هذا يدعم إصدار macOS Catalina 10.15 والإصدارات الأحدث.
- إنشاء مجموعات المستخدمين التي ستقوم بتعيين تحديثات التكوين إليها.
- تثبيت مستعرض v95+ Edge على أجهزة macOS 


## <a name="onboard-macos-devices-into-microsoft-purview-solutions-using-microsoft-intune"></a>إلحاق أجهزة macOS في حلول Microsoft Purview باستخدام Microsoft Intune

إعداد جهاز macOS في حلول التوافق هو عملية ست مراحل.

1. [إنشاء ملفات تعريف تكوين النظام](#create-system-configuration-profiles)
1. [الحصول على حزمة إلحاق الجهاز](#get-the-device-onboarding-package)
1. [نشر حزمة الإلحاق](#deploy-the-onboarding-package)
1. [تمكين ملحق النظام](#enable-system-extension)
1. [الحصول على حزمة التثبيت](#get-the-installation-package)
1. [نشر حزمة التثبيت](#deploy-the-microsoft-dlp-installation-package)

### <a name="create-system-configuration-profiles"></a>إنشاء ملفات تعريف تكوين النظام

1. ستحتاج إلى هذه الملفات لهذا الإجراء.

|الملف المطلوب ل |مصدر |
|---------|---------|
|حزمة الإلحاق    |تم التنزيل من **حزمة** إلحاق مدخل التوافق واسم الملف *DeviceComplianceOnboarding.xml* |
|امكانيه الوصول |[accessibility.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/accessibility.mobileconfig)|
الوصول الكامل إلى القرص     |[fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig)|
|ملف الشبكة| [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig)]
|ملحقات النظام |[sysext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/sysext.mobileconfig)
|تفضيل MDE     |[com.microsoft.wdav.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/data_loss_prevention/com.microsoft.wdav.mobileconfig)|
|تفضيل MAU|[com.microsoft.autoupdate2.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/settings/microsoft_auto_update/com.microsoft.autoupdate2.mobileconfig)|
|حزمة التثبيت     |تم التنزيل من **حزمة تثبيت** مدخل التوافق، اسم *\*الملف wdav.pkg*\* |

> [!TIP]
> يمكنك تنزيل ملفات *.mobileconfig* بشكل فردي أو في [ملف واحد مدمج](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/combined/mdatp-nokext.mobileconfig) يحتوي على:
> - accessibility.mobileconfig
> - fulldisk.mobileconfig
> - netfilter.mobileconfig
> - ملحقات النظام
>
>إذا تم تحديث أي من هذه الملفات الفردية، فستحتاج إلى تنزيل الملف المدمج مرة أخرى أو الملف المحدث الفردي بشكل فردي.

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

2. افتح **ملفات تعريف تكوين** **الأجهزة** >  لمركز  > **Microsoft إدارة نقاط النهاية**.

1. اختر: **إنشاء ملف تعريف** 

1. اختيار:
    1. **النظام الأساسي = macOS**
    1. **نوع ملف التعريف = قوالب**
    1. **اسم القالب = مخصص**

1. اختر **"إنشاء"**

1. اختر اسما لملف التعريف، مثل *AccessibilityformacOS* في هذا المثال. اختر **"التالي**".

1. اختر ملف **accessibility.mobileconfig** الذي قمت بتنزيله في الخطوة 1 كملف ملف تعريف التكوين.

1. اختر **"التالي"**

1. في علامة التبويب **"الواجبات"** ، أضف المجموعة التي تريد توزيع هذه التكوينات إليها واختر **"التالي**".

1. راجع الإعدادات واختر **"إنشاء** " لنشر التكوين.

1. كرر الخطوات من 3 إلى 11 لإنشاء ملفات تعريف ل:
    1. **ملف fulldisk.mobileconfig**
    1. **ملفcom.microsoft.autoupdate2.xml**
    1. تفضيلات MDE **com.microsoft.wdav.xml** الملف
        1. تعيين محرك `passive mode` = `true` الحماية من الفيروسات أو .`false` يستخدم `true`في حالة نشر DLP فقط. استخدام `false` قيمة أو عدم تعيينها في حالة نشر DLP و Microsoft Defender لنقطة النهاية (MDE).
    1. **netfilter.mobileconfig**
 
1. افتح **ملفات تعريف تكوين** **الأجهزة** > ، يجب أن تشاهد ملفات التعريف التي تم إنشاؤها هناك.

1. في صفحة **ملفات تعريف التكوين** ، اختر ملف التعريف الذي أنشأته للتو، في هذا المثال *AccessibilityformacOS* واختر **حالة الجهاز** لعرض قائمة بالأجهزة وحالة نشر ملف تعريف التكوين.

### <a name="get-the-device-onboarding-package"></a>الحصول على حزمة إلحاق الجهاز

1. في **مركز التوافق**، افتح **إعدادات** > **إعداد الجهاز** واختر **"إلحاق".**
 
1. **لتحديد نظام التشغيل لبدء عملية الإلحاق**، اختر **macOS**.
 
1. بالنسبة **لأسلوب النشر**، اختر **إدارة الجهاز/Microsoft Intune الجوال**.
 
1. اختر **تنزيل حزمة الإلحاق**. يحتوي هذا على التعليمات البرمجية الإلحاقية في ملف *DeviceComplianceOnboarding.xml* .

### <a name="deploy-the-onboarding-package"></a>نشر حزمة الإلحاق

1. افتح **ملفات تعريف تكوين** **الأجهزة** >  لمركز  > **Microsoft إدارة نقاط النهاية**.

1. اختر: **إنشاء ملف تعريف**. 

1. اختيار:
    1. **النظام الأساسي = macOS**
    1. **نوع ملف التعريف = قوالب**
    1. **اسم القالب = مخصص**

1. اختر **"إنشاء"**

1. اختر اسما لملف التعريف، مثل *OnboardingPackage* في هذا المثال. اختر **"التالي**".

1. اختر ملف *DeviceComplianceOnboarding.xml* كملف ملف تعريف التكوين.

1. اختر **"التالي"**

1. في علامة التبويب **"الواجبات"** ، أضف المجموعة التي تريد توزيع هذه التكوينات إليها واختر **"التالي**".

1. راجع الإعدادات واختر **"إنشاء** " لنشر التكوين.

### <a name="enable-system-extension"></a>تمكين ملحق النظام

1. في **مركز إدارة نقاط النهاية Microsoft**، حدد **"إنشاء ملف تعريف**" ضمن **"ملفات تعريف التكوين"**

1. اختيار:
    1. **النظام الأساسي = macOS**
    1. **نوع ملف التعريف = قوالب**
    1. **اسم القالب = ملحقات**

1. اختر **"إنشاء"**

1. في علامة التبويب **"Basics** "، قم بتسمية ملف التعريف الجديد هذا.

1. في علامة تبويب **إعدادات التكوين** ، قم بتوسيع **ملحقات النظام**.

1. ضمن **معرف المجموعة** **ومعرف الفريق**، قم بتعيين هذه القيم

|معرف المجموعة  |معرف الفريق  |
|---------|---------|
|**com.microsoft.wdav.epsext**|**UBF8T346G9**|
|**com.microsoft.wdav.netext**|**UBF8T346G9**|


1. في علامة التبويب **"الواجبات"** ، أضف المجموعة التي تريد توزيع هذه التكوينات إليها واختر **"التالي**".

1. اختر **"التالي** " لنشر التكوين.

### <a name="get-the-installation-package"></a>الحصول على حزمة التثبيت

1. في **مركز التوافق**، افتح **إعدادات** > **إعداد الجهاز** واختر **"إلحاق".**
 
1. **لتحديد نظام التشغيل لبدء عملية الإلحاق**، اختر **macOS**
 
1. **لأسلوب النشر**، اختر **إدارة الجهاز/Microsoft Intune الجوال**
 
1. اختر **تنزيل حزمة التثبيت**. سيمنحك هذا ملف *wdav.pkg* .

> [!IMPORTANT]
> قبل أن تتمكن من نشر *wdav.pkg.* الحزمة عبر Intune، يجب إعادة تنسيقها باستخدام *أدوات التفاف تطبيق Intune ل Mac* إلى تنسيق *wdav.pkg.intunemac* .
 

### <a name="deploy-the-microsoft-dlp-installation-package"></a>نشر حزمة تثبيت Microsoft DLP

1. اتبع الإجراءات في [كيفية إضافة تطبيقات خط العمل macOS (LOB) إلى Microsoft Intune](/mem/intune/apps/lob-apps-macos) لتحويل ملف *wdav.pkg* إلى التنسيق المناسب ونشره من خلال Intune.

## <a name="offboard-macos-devices-using-intune"></a>إيقاف تشغيل أجهزة macOS باستخدام Intune

> [!NOTE]
> يؤدي إلغاء الإلحاق إلى توقف الجهاز عن إرسال بيانات جهاز الاستشعار إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات كان قد تم الاحتفاظ بها لمدة تصل إلى ستة أشهر.

2. في **مركز microsoft إدارة نقاط النهاية**، افتح **ملفات تعريف تكوين** **الأجهزة** > ، يجب أن تشاهد ملفات التعريف التي تم إنشاؤها هناك.

1. في صفحة **ملفات تعريف التكوين** ، اختر ملف تعريف *wdav.pkg.intunemac* .

1. اختر **حالة الجهاز** للاطلاع على قائمة بالأجهزة وحالة نشر ملف تعريف التكوين

1. فتح **الخصائص** **والتعيينات**

1. إزالة المجموعة من التعيين. سيؤدي ذلك إلى إلغاء تثبيت حزمة *wdav.pkg.intunemac* وإلغاء تشغيل جهاز macOS من حلول التوافق.
