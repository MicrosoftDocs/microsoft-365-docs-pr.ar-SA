---
title: نشر مستند إلى Intune ل Microsoft Defender ل Endpoint على Mac
description: قم بتثبيت Microsoft Defender ل Endpoint على Mac، باستخدام Microsoft Intune.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4979ee5f3953ced1073779fdcabb7eb361d4911a
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63583159"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>النشر المستند إلى Intune ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md)
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يصف هذا الموضوع كيفية نشر Microsoft Defender ل Endpoint على macOS من خلال Intune. يتطلب النشر الناجح إكمال كل الخطوات التالية:

1. [تنزيل حزمة الboarding](#download-the-onboarding-package)
1. [إعداد جهاز العميل](#client-device-setup)
1. [الموافقة على ملحقات النظام](#approve-system-extensions)
1. [إنشاء ملفات تعريف تكوين النظام](#create-system-configuration-profiles)
1. [تطبيق النشر](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع صفحة [Microsoft Defender ل Endpoint الرئيسية على macOS](microsoft-defender-endpoint-mac.md) للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام الخاصة بالإصدار الحالي للبرنامج.

## <a name="overview"></a>نظرة عامة

يلخص الجدول التالي الخطوات التي ستحتاج إلى اتخاذها لنشر Microsoft Defender لنقطة النهاية وإدارتها على أجهزة Mac، عبر Intune. تتوفر خطوات أكثر تفصيلا أدناه.

<br>

****

|الخطوة|أسماء ملفات نموذجية|BundleIdentifier|
|---|---|---|
|[تنزيل حزمة الboarding](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[الموافقة على ملحق النظام ل Microsoft Defender لنقطة النهاية](#approve-system-extensions)|MDATP_SysExt.xml|N/A|
|[الموافقة على ملحق Kernel ل Microsoft Defender لنقطة النهاية](#download-the-onboarding-package)|MDATP_KExt.xml|N/A|
|[منح حق الوصول الكامل للقرص إلى Microsoft Defender لنقطة النهاية](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[نهج ملحق الشبكة](#network-filter)|MDATP_NetExt.xml|N/A|
|[تكوين Microsoft AutoUpdate (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[إعدادات تكوين Microsoft Defender لنقطة النهاية](mac-preferences.md#intune-full-profile) <p> **ملاحظة:** إذا كنت تخطط لتشغيل AV من جهة خارجية ل macOS، فقم بتعيين إلى `passiveMode` `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[تكوين إعلامات Microsoft Defender لنقطة النهاية وMS AutoUpdate (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 أو com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الboarding

قم بتنزيل حزم الboarding من مدخل Microsoft 365 Defender:

1. في Microsoft 365 Defender، **انتقل إلى الإعدادات** \> **إدارة** \> أجهزة نقاط **النهاية** \> **.**

2. قم بتعيين نظام التشغيل إلى **macOS وطريقة** النشر إلى **إدارة أجهزة المحمول / Microsoft Intune**.

    ![لقطة شاشة لإعدادات الضبط.](images/macos-install-with-intune.png)

3. حدد **تنزيل حزمة التكهيل**. احفظه _WindowsDefenderATPOnboardingPackage.zip_ إلى الدليل نفسه.

4. استخراج محتويات ملف .zip:

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    warning:  WindowsDefenderATPOnboardingPackage.zip appears to use backslashes as path separators
      inflating: intune/kext.xml
      inflating: intune/WindowsDefenderATPOnboarding.xml
      inflating: jamf/WindowsDefenderATPOnboarding.plist
    ```

## <a name="create-system-configuration-profiles"></a>إنشاء ملفات تعريف تكوين النظام

الخطوة التالية هي إنشاء ملفات تعريف تكوين النظام التي يحتاجها Microsoft Defender لنقطة النهاية.
في مركز [إدارة نقاط النهاية من Microsoft،](https://endpoint.microsoft.com/) افتح **ملفات تعريف تكوين** \> **الأجهزة**.

### <a name="onboarding-blob"></a>Blob للانصهار

يحتوي ملف التعريف هذا على معلومات ترخيص ل Microsoft Defender لنقطة النهاية. بدون ملف التعريف هذا، سيقرر Microsoft Defender ل Endpoint أنه غير مرخص.

1. حدد **إنشاء ملف تعريف** ضمن **ملفات تعريف التكوين**.
1. حدد **PlatformmacOS**=، **اكتب ملف** **التعريفTemplates**=. **اسم القالب**= **مخصص**. انقر **فوق إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![إنشاء ملف تعريف تكوين مخصص.](images/mdatp-6-systemconfigurationprofiles-1.png)

1. اختر اسما لملف التعريف، على سبيل المثال، "Defender for Cloud أو Endpoint onboarding for macOS". انقر فوق **التالي**.

    > [!div class="mx-imgBorder"]
    > ![ملف تعريف تكوين مخصص - الاسم.](images/mdatp-6-systemconfigurationprofiles-2.png)

1. اختر اسما لاسم ملف تعريف التكوين، على سبيل المثال، "Defender for Endpoint onboarding for macOS".
1. اختر [قناة نشر](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. حدد intune/WindowsDefenderATPOnboarding.xml التي قمت باستخراجها من حزمة التهيئة أعلاه كملف ملف تعريف التكوين.

    > [!div class="mx-imgBorder"]
    > ![استيراد تكوين من ملف لملف تعريف تكوين مخصص.](images/mdatp-6-systemconfigurationprofiles.png)

1. انقر فوق **التالي**.
1. تعيين الأجهزة على علامة **التبويب واجب** . انقر فوق **التالي**.

    > [!div class="mx-imgBorder"]
    > ![ملف تعريف تكوين مخصص - واجب.](images/mdatp-6-systemconfigurationprofiles-2.png)

1. مراجعة **وإنشاء.**
1. افتح **ملفات تعريف** \> **تكوين الأجهزة**، يمكنك رؤية ملف التعريف الذي تم إنشاؤه هناك.

    > [!div class="mx-imgBorder"]
    > ![ملف تعريف تكوين مخصص - تم.](images/mdatp-6-systemconfigurationprofiles-3.png)

### <a name="approve-system-extensions"></a>الموافقة على ملحقات النظام

ملف التعريف هذا مطلوب ل macOS 10.15 (Catalina) أو أحدث. سيتم تجاهله على macOS الأقدم.

1. حدد **إنشاء ملف تعريف** ضمن **ملفات تعريف التكوين**.
1. حدد **PlatformmacOS**=، **اكتب ملف** **التعريفTemplates**=. **اسم القالب**= **الملحقات**. انقر **فوق إنشاء**.
1. في علامة **التبويب أساسيات** ، امنح اسما لملف التعريف الجديد هذا.
1. في **علامة التبويب إعدادات** التكوين، قم بتوسيع **ملحقات** النظام بإضافة الإدخالات التالية في المقطع **ملحقات النظام المسموح** به:

    |معرف الحزمة|معرف الفريق|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > ![إعدادات ملحق النظام.](images/mac-system-extension-intune2.png)

1. في علامة **التبويب** الواجبات، قم بتعيين ملف التعريف هذا إلى جميع المستخدمين & **كافة الأجهزة**.
1. راجع ملف تعريف التكوين هذا وأنشئه.

### <a name="kernel-extensions"></a>ملحقات Kernel

ملف التعريف هذا مطلوب ل macOS 10.15 (Catalina) أو الإصدارات الأقدم. سيتم تجاهله على macOS أحدث.

> [!CAUTION]
> لا تدعم أجهزة Apple Silicon (M1) KEXT. سيفشل تثبيت ملف تعريف تكوين يتكون من سياسات KEXT على هذه الأجهزة.

1. حدد **إنشاء ملف تعريف** ضمن **ملفات تعريف التكوين**.
1. حدد **PlatformmacOS**=، **اكتب ملف** **التعريفTemplates**=. **اسم القالب**= **الملحقات**. انقر **فوق إنشاء**.
1. في علامة **التبويب أساسيات** ، امنح اسما لملف التعريف الجديد هذا.
1. في **علامة التبويب إعدادات التكوين** ، قم بتوسيع **ملحقات Kernel**.
1. قم **بتعيين معرف الفريق** إلى **UBF8T346G9** وانقر فوق **التالي**.

    > [!div class="mx-imgBorder"]
    > ![إعدادات ملحقات Kernel.](images/mac-kernel-extension-intune2.png)

1. في علامة **التبويب** الواجبات، قم بتعيين ملف التعريف هذا إلى جميع المستخدمين & **كافة الأجهزة**.
1. راجع ملف تعريف التكوين هذا وأنشئه.

### <a name="full-disk-access"></a>الوصول إلى القرص الكامل

   > [!CAUTION]
   > يحتوي macOS 10.15 (Catalina) على تحسينات جديدة على الأمان والخصوصية. بدءا من هذا الإصدار، بشكل افتراضي، لن تتمكن التطبيقات من الوصول إلى مواقع معينة على القرص (مثل المستندات أو التنزيلات أو سطح المكتب وغير ذلك) بدون موافقة صريحة. في حالة عدم وجود هذه الموافقة، لن يتمكن Microsoft Defender ل Endpoint من حماية جهازك بشكل كامل.
   >
   > يمنح ملف تعريف التكوين هذا إمكانية الوصول إلى القرص الكامل إلى Microsoft Defender لنقطة النهاية. إذا قمت مسبقا بتكوين Microsoft Defender ل Endpoint من خلال Intune، نوصي بتحديث النشر باستخدام ملف تعريف التكوين هذا.

قم [**بتنزيل fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) [من مستودع GitHub.](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles)

اتبع الإرشادات الخاصة [ب التهيئة](#onboarding-blob) من أعلى باستخدام "Defender for Endpoint Full Disk Access" لاسم ملف التعريف، وتنزيل **fulldisk.mobileconfig** باسم ملف تعريف التكوين.

### <a name="network-filter"></a>عامل تصفية الشبكة

كجزء من قدرات الكشف عن نقاط النهاية والاستجابة لها، يفحص Microsoft Defender ل Endpoint على نظام التشغيل macOS حركة مرور مآخذ التوصيل ويعيد Microsoft 365 Defender المدخل. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

قم [**بتنزيل netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) [من مستودع GitHub.](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles)

اتبع الإرشادات الخاصة [بتهيئة](#onboarding-blob) الشبكة من الأعلى، باستخدام "Defender for Endpoint Network Filter" لاسم ملف التعريف، و **netfilter.mobileconfig** الذي تم تنزيله باسم ملف تعريف التكوين.

### <a name="notifications"></a>الإعلامات

يتم استخدام ملف التعريف هذا للسماح ل Microsoft Defender ل Endpoint على macOS والتحديث التلقائي ل Microsoft بعرض الإعلامات في واجهة المستخدم على macOS 10.15 (Catalina) أو أحدث.

قم [**بتنزيل notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) من [مستودع GitHub.](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles)

اتبع الإرشادات الخاصة [بتهيئة](#onboarding-blob) البيانات من الأعلى، باستخدام "Defender for Endpoint Notifications" لاسم ملف التعريف، وتنزيل **notif.mobileconfig** باسم ملف تعريف التكوين.

### <a name="view-status"></a>عرض الحالة

بمجرد نشر تغييرات Intune على الأجهزة المسجلة، يمكنك عرضها مدرجة ضمن **حالة** \> **جهاز العرض**:

> [!div class="mx-imgBorder"]
> ![عرض حالة الجهاز في جهاز العرض.](images/mdatp-7-devicestatusblade.png)

## <a name="publish-application"></a>تطبيق النشر

تمكن هذه الخطوة نشر Microsoft Defender ل Endpoint على الأجهزة التي تم تسجيلها.

1. في مركز [إدارة نقاط النهاية من Microsoft،](https://endpoint.microsoft.com/) افتح **التطبيقات**.

    > [!div class="mx-imgBorder"]
    > ![جاهز لإنشاء تطبيق.](images/mdatp-8-app-before.png)

1. حدد حسب النظام الأساسي > macOS > إضافة.
1. اختر **تطبيق** **typemacOS**=، وانقر فوق **تحديد**.

    > [!div class="mx-imgBorder"]
    > ![حدد نوع التطبيق.](images/mdatp-9-app-type.png)

1. احتفظ بالقيم الافتراضية، وانقر فوق **التالي**.

    > [!div class="mx-imgBorder"]
    > ![خصائص التطبيق.](images/mdatp-10-properties.png)

1. أضف الواجبات، وانقر فوق **التالي**.

    > [!div class="mx-imgBorder"]
    > ![لقطة شاشة للمعلومات حول تعيينات Intune.](images/mdatp-11-assignments.png)

1. مراجعة **وإنشاء.**
1. يمكنك زيارة **التطبيقات** \> **حسب النظام الأساسي** \> **macOS** لمشاهدتها في قائمة جميع التطبيقات.

    > [!div class="mx-imgBorder"]
    > ![قائمة التطبيقات.](images/mdatp-12-applications.png)

لمزيد من المعلومات، راجع [إضافة Microsoft Defender ل Endpoint إلى أجهزة macOS باستخدام](/mem/intune/apps/apps-advanced-threat-protection-macos) Microsoft Intune.)

   > [!CAUTION]
   > يجب عليك إنشاء كل ملفات تعريف التكوين المطلوبة ودفعها إلى جميع الأجهزة، كما هو موضح أعلاه.

## <a name="client-device-setup"></a>إعداد جهاز العميل

لا تحتاج إلى أي توفير خاص لجهاز Mac يتجاوز مستوى Company Portal [التثبيت](/intune-user-help/enroll-your-device-in-intune-macos-cp).

1. تأكيد إدارة الأجهزة.

    > [!div class="mx-imgBorder"]
    > ![تأكيد لقطة شاشة لإدارة الأجهزة.](images/mdatp-3-confirmdevicemgmt.png)

    حدد **فتح تفضيلات النظام**، وحدد **موقع ملف تعريف الإدارة** في القائمة، وحدد **موافقة...**. سيتم عرض "ملف تعريف الإدارة" ك **"متحقق منه"**:

    ![لقطة شاشة لملف تعريف الإدارة.](images/mdatp-4-managementprofile.png)

2. حدد **متابعة** وأكمل عملية التسجيل.

   يمكنك الآن تسجيل المزيد من الأجهزة. يمكنك أيضا تسجيلها لاحقا، بعد الانتهاء من توفير تكوين النظام وحزم التطبيقات.

3. في Intune، افتح **إدارة الأجهزة** \> **كافة** \> **الأجهزة**. يمكنك هنا رؤية جهازك بين الأشخاص المدرجين:

   > [!div class="mx-imgBorder"]
   > ![لقطة شاشة لإضافة أجهزة.](images/mdatp-5-alldevices.png)

## <a name="verify-client-device-state"></a>التحقق من حالة جهاز العميل

1. بعد نشر ملفات تعريف التكوين على أجهزتك، افتح **ملفات تعريف تفضيلات** \> **النظام** على جهاز Mac.

    > [!div class="mx-imgBorder"]
    > ![لقطة شاشة لتفضيلات النظام.](images/mdatp-13-systempreferences.png)

    ![لقطة شاشة لملفات تعريف تفضيلات النظام.](images/mdatp-14-systempreferencesprofiles.png)

2. تحقق من أن ملفات تعريف التكوين التالية موجودة ومثبتة. يجب **أن يكون ملف تعريف** الإدارة هو ملف تعريف النظام Intune. _Wdav-config_ و _wdav-kext_ هي ملفات تعريف تكوين النظام التي تم إضافتها في Intune:

    ![لقطة شاشة لملفات التعريف.](images/mdatp-15-managementprofileconfig.png)

3. سترى أيضا أيقونة Microsoft Defender لنقطة النهاية في الزاوية العلوية اليسرى:

    > [!div class="mx-imgBorder"]
    > ![أيقونة Microsoft Defender لنقطة النهاية في لقطة شاشة ل شريط الحالة.](images/mdatp-icon-bar.png)

## <a name="troubleshooting"></a>استكشاف الأخطاء وإصلاحها

المشكلة: لم يتم العثور على أي ترخيص.

الحل: اتبع الخطوات المذكورة أعلاه لإنشاء ملف تعريف جهاز باستخدام WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>مشاكل تثبيت التسجيل

لمزيد من المعلومات حول كيفية البحث عن السجل الذي تم إنشاؤه تلقائيا الذي تم إنشاؤه بواسطة المثبت عند حدوث خطأ، راجع [تسجيل مشاكل التثبيت](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>إلغاء التثبيت

راجع [إلغاء تثبيت للحصول](mac-resources.md#uninstalling) على تفاصيل حول كيفية إزالة Microsoft Defender ل Endpoint على macOS من أجهزة العميل.
