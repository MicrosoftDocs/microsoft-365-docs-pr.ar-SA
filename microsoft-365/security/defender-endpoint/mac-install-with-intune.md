---
title: النشر المستند إلى Intune Microsoft Defender لنقطة النهاية على Mac
description: ثبت Microsoft Defender لنقطة النهاية على Mac، باستخدام Microsoft Intune.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، التوزيع، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: 4c2c1f7c11c57ca45411b74023807077f73ba8bf
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66044095"
---
# <a name="intune-based-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>النشر المستند إلى Intune Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يصف هذا الموضوع كيفية نشر Microsoft Defender لنقطة النهاية على macOS من خلال Intune. يتطلب النشر الناجح إكمال جميع الخطوات التالية:

1. [تنزيل حزمة الإلحاق](#download-the-onboarding-package)
1. [إعداد جهاز العميل](#client-device-setup)
1. [الموافقة على ملحقات النظام](#approve-system-extensions)
1. [إنشاء ملفات تعريف تكوين النظام](#create-system-configuration-profiles)
1. [نشر التطبيق](#publish-application)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع [Microsoft Defender لنقطة النهاية الرئيسية على صفحة macOS للحصول على](microsoft-defender-endpoint-mac.md) وصف للمتطلبات الأساسية ومتطلبات النظام لإصدار البرنامج الحالي.

## <a name="overview"></a>نظرة عامة

يلخص الجدول التالي الخطوات التي ستحتاج إلى اتخاذها لنشر وإدارة Microsoft Defender لنقطة النهاية على أجهزة Mac، عبر Intune. تتوفر خطوات أكثر تفصيلا أدناه.

<br>

****

|خطوه|أسماء ملفات نموذجية|معرف المجموعة|
|---|---|---|
|[تنزيل حزمة الإلحاق](#download-the-onboarding-package)|WindowsDefenderATPOnboarding__MDATP_wdav.atp.xml|com.microsoft.wdav.atp|
|[الموافقة على ملحق النظام Microsoft Defender لنقطة النهاية](#approve-system-extensions)|MDATP_SysExt.xml|N/A|
|[الموافقة على ملحق Kernel Microsoft Defender لنقطة النهاية](#download-the-onboarding-package)|MDATP_KExt.xml|N/A|
|[منح حق الوصول الكامل للقرص إلى Microsoft Defender لنقطة النهاية](#full-disk-access)|MDATP_tcc_Catalina_or_newer.xml|com.microsoft.wdav.tcc|
|[نهج ملحق الشبكة](#network-filter)|MDATP_NetExt.xml|N/A|
|[تكوين التحديث التلقائي لبرامج Microsoft (MAU)](mac-updates.md#intune)|MDATP_Microsoft_AutoUpdate.xml|com.microsoft.autoupdate2|
|[إعدادات تكوين Microsoft Defender لنقطة النهاية](mac-preferences.md#intune-full-profile) <p> **ملاحظه:** إذا كنت تخطط لتشغيل AV تابع لجهة خارجية macOS، فقم بتعيينه `passiveMode` إلى `true`.|MDATP_WDAV_and_exclusion_settings_Preferences.xml|com.microsoft.wdav|
|[تكوين إعلامات Microsoft Defender لنقطة النهاية وMS AutoUpdate (MAU)](mac-updates.md)|MDATP_MDAV_Tray_and_AutoUpdate2.mobileconfig|com.microsoft.autoupdate2 أو com.microsoft.wdav.tray|
|

## <a name="download-the-onboarding-package"></a>تنزيل حزمة الإلحاق

قم بتنزيل حزم الإلحاق من مدخل Microsoft 365 Defender:

1. في مدخل Microsoft 365 Defender، انتقل إلى إعداد **إدارة** \> أجهزة نقاط **النهاية** \> **الإعدادات** \> **.**

2. تعيين نظام التشغيل إلى **macOS** وطريقة النشر إلى **إدارة الجهاز الجوال / Microsoft Intune**.

   :::image type="content" source="images/macos-install-with-intune.png" alt-text="صفحة إعدادات الإلحاق" lightbox="images/macos-install-with-intune.png":::

3. حدد **تنزيل حزمة الإلحاق**. احفظه _WindowsDefenderATPOnboardingPackage.zip_ إلى الدليل نفسه.

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
في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/)، افتح **ملفات تعريف تكوين** **الأجهزة**\>.

### <a name="onboarding-blob"></a>إلحاق الكائن الثنائي كبير الحجم

يحتوي ملف التعريف هذا على معلومات ترخيص Microsoft Defender لنقطة النهاية. بدون ملف التعريف هذا، سيبلغ Microsoft Defender لنقطة النهاية أنه غير مرخص.

1. حدد **"إنشاء ملف تعريف** " ضمن **"ملفات تعريف التكوين**".
1. حدد **النظام الأساسي**= **macOS**،**قوالب** **نوع**= ملف التعريف. **اسم**= القالب **مخصص**. انقر فوق **"إنشاء**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-1.png" alt-text="صفحة إنشاء ملف تعريف التكوين المخصص" lightbox="images/mdatp-6-systemconfigurationprofiles-1.png":::

1. اختر اسما لملف التعريف، على سبيل المثال، "Defender for Cloud أو Endpoint onboarding for macOS". انقر فوق **التالي**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="حقل اسم ملف تعريف التكوين المخصص" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. اختر اسما لاسم ملف تعريف التكوين، على سبيل المثال، "Defender for Endpoint onboarding for macOS".
1. اختر [قناة نشر](/mem/intune/fundamentals/whats-new#new-deployment-channel-setting-for-custom-device-configuration-profiles-on-macos-devices).
1. حدد intune/WindowsDefenderATPOnboarding.xml التي قمت باستخراجها من حزمة الإلحاق أعلاه كملف ملف تعريف التكوين.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles.png" alt-text="استيراد تكوين من ملف لملف تعريف التكوين المخصص" lightbox="images/mdatp-6-systemconfigurationprofiles.png":::

1. انقر فوق **التالي**.
1. تعيين الأجهزة على علامة التبويب **"واجب** ". انقر فوق **"التالي**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-2.png" alt-text="ملف تعريف التكوين المخصص - التعيين" lightbox="images/mdatp-6-systemconfigurationprofiles-2.png":::

1. المراجعة **والإنشاء**.
1. افتح **ملفات تعريف تكوين** **الأجهزة**\>، يمكنك رؤية ملف التعريف الذي تم إنشاؤه هناك.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-6-systemconfigurationprofiles-3.png" alt-text="اكتمال ملف تعريف التكوين المخصص" lightbox="images/mdatp-6-systemconfigurationprofiles-3.png":::

### <a name="approve-system-extensions"></a>الموافقة على ملحقات النظام

ملف التعريف هذا مطلوب macOS 10.15 (Catalina) أو أحدث. سيتم تجاهله في macOS الأقدم.

1. حدد **"إنشاء ملف تعريف** " ضمن **"ملفات تعريف التكوين**".
1. حدد **النظام الأساسي**= **macOS**،**قوالب** **نوع**= ملف التعريف. **اسم**= القالب **الملحقات**. انقر فوق **"إنشاء**".
1. في علامة التبويب **"Basics** "، أدخل اسما لملف التعريف الجديد هذا.
1. في علامة التبويب **إعدادات التكوين** ، قم بتوسيع **ملحقات النظام** بإضافة الإدخالات التالية في قسم **ملحقات النظام المسموح بها** :

    |معرف المجموعة|معرف الفريق|
    |---|---|
    |com.microsoft.wdav.epsext|UBF8T346G9|
    |com.microsoft.wdav.netext|UBF8T346G9|

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-system-extension-intune2.png" alt-text="إعدادات ملحق النظام" lightbox="images/mac-system-extension-intune2.png":::

1. في علامة التبويب **"الواجبات"** ، قم بتعيين ملف التعريف هذا إلى **كافة المستخدمين & كافة الأجهزة**.
1. مراجعة ملف تعريف التكوين هذا وإنشاءه.

### <a name="kernel-extensions"></a>ملحقات Kernel

ملف التعريف هذا مطلوب macOS 10.15 (Catalina) أو إصدار أقدم. سيتم تجاهله في macOS الأحدث.

> [!CAUTION]
> لا تدعم أجهزة Apple Silicon (M1) KEXT. سيفشل تثبيت ملف تعريف تكوين يتكون من نهج KEXT على هذه الأجهزة.

1. حدد **"إنشاء ملف تعريف** " ضمن **"ملفات تعريف التكوين**".
1. حدد **النظام الأساسي**= **macOS**،**قوالب** **نوع**= ملف التعريف. **اسم**= القالب **الملحقات**. انقر فوق **"إنشاء**".
1. في علامة التبويب **"Basics** "، أدخل اسما لملف التعريف الجديد هذا.
1. في علامة التبويب **إعدادات التكوين** ، قم بتوسيع **ملحقات Kernel**.
1. قم بتعيين **معرف الفريق** إلى **UBF8T346G9** وانقر فوق **"التالي**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mac-kernel-extension-intune2.png" alt-text="معرفات الفريق المسموح بها لملحقات Kernel." lightbox="images/mac-kernel-extension-intune2.png":::

1. في علامة التبويب **"الواجبات"** ، قم بتعيين ملف التعريف هذا إلى **كافة المستخدمين & كافة الأجهزة**.
1. مراجعة ملف تعريف التكوين هذا وإنشاءه.

### <a name="full-disk-access"></a>الوصول إلى القرص الكامل

   > [!CAUTION]
   > يحتوي macOS 10.15 (Catalina) على تحسينات أمان وخصوصية جديدة. بدءا من هذا الإصدار، بشكل افتراضي، لا يمكن للتطبيقات الوصول إلى مواقع معينة على القرص (مثل المستندات والتنزيلات وسطح المكتب وما إلى ذلك) دون موافقة صريحة. في حالة عدم وجود هذه الموافقة، لن يتمكن Microsoft Defender لنقطة النهاية من حماية جهازك بشكل كامل.
   >
   > يمنح ملف تعريف التكوين هذا الوصول إلى القرص الكامل إلى Microsoft Defender لنقطة النهاية. إذا قمت بتكوين Microsoft Defender لنقطة النهاية مسبقا من خلال Intune، نوصي بتحديث النشر باستخدام ملف تعريف التكوين هذا.

قم بتنزيل [**fulldisk.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) من [مستودع GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

اتبع الإرشادات الخاصة [بإلحاق الكائن الثنائي كبير الحجم](#onboarding-blob) من أعلى، باستخدام "Defender for Endpoint Full Disk Access" كاسم ملف التعريف، وقم بتنزيل **fulldisk.mobileconfig** كاسم ملف تعريف التكوين.

### <a name="network-filter"></a>عامل تصفية الشبكة

كجزء من قدرات الكشف عن نقطة النهاية والاستجابة لها، يقوم Microsoft Defender لنقطة النهاية على macOS بفحص حركة مرور مأخذ التوصيل ويبلغ عن هذه المعلومات إلى مدخل Microsoft 365 Defender. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

قم بتنزيل [**netfilter.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/netfilter.mobileconfig) من [مستودع GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

اتبع الإرشادات الخاصة [بإلحاق الكائن الثنائي كبير الحجم](#onboarding-blob) من أعلى، باستخدام "Defender for Endpoint Network Filter" كاسم ملف التعريف، وقم بتنزيل **netfilter.mobileconfig** كاسم ملف تعريف التكوين.

### <a name="notifications"></a>الاخطارات

يتم استخدام ملف التعريف هذا للسماح Microsoft Defender لنقطة النهاية على macOS وMicrosoft Auto Update لعرض الإعلامات في واجهة المستخدم على macOS 10.15 (Catalina) أو أحدث.

قم بتنزيل [**notif.mobileconfig**](https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/mobileconfig/profiles/notif.mobileconfig) من [مستودع GitHub](https://github.com/microsoft/mdatp-xplat/tree/master/macos/mobileconfig/profiles).

اتبع الإرشادات الخاصة [بإلحاق الكائن الثنائي كبير الحجم](#onboarding-blob) من أعلى، باستخدام "Defender لإشعارات نقطة النهاية" كاسم ملف التعريف، وقم بتنزيل **notif.mobileconfig** كاسم ملف تعريف التكوين.

### <a name="view-status"></a>عرض الحالة

بمجرد نشر تغييرات Intune على الأجهزة المسجلة، يمكنك رؤيتها مدرجة ضمن **حالة جهاز المراقبة**\>:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/mdatp-7-devicestatusblade.png" alt-text="طريقة عرض حالة الجهاز" lightbox="images/mdatp-7-devicestatusblade.png":::

## <a name="publish-application"></a>نشر التطبيق

تمكن هذه الخطوة نشر Microsoft Defender لنقطة النهاية إلى الأجهزة المسجلة.

1. في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/)، افتح **التطبيقات**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-8-app-before.png" alt-text="صفحة نظرة عامة على التطبيق" lightbox="images/mdatp-8-app-before.png":::

1. حدد حسب النظام الأساسي > macOS > Add.
1. اختر **نوع**= التطبيق **macOS**، انقر فوق **"تحديد**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-9-app-type.png" alt-text="نوع التطبيق المحدد" lightbox="images/mdatp-9-app-type.png":::

1. احتفظ بالقيم الافتراضية، وانقر فوق **"التالي**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-10-properties.png" alt-text="صفحة خصائص التطبيق" lightbox="images/mdatp-10-properties.png":::

1. إضافة تعيينات، انقر فوق **"التالي**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-11-assignments.png" alt-text="صفحة معلومات تعيينات Intune" lightbox="images/mdatp-11-assignments.png":::

1. المراجعة **والإنشاء**.
1. يمكنك زيارة **"التطبيقات** \> **حسب" macOS النظام الأساسي** \> لمشاهدتها في قائمة جميع التطبيقات.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-12-applications.png" alt-text="صفحة قوائم التطبيق" lightbox="images/mdatp-12-applications.png":::

لمزيد من المعلومات، راجع [إضافة Microsoft Defender لنقطة النهاية إلى أجهزة macOS باستخدام Microsoft Intune](/mem/intune/apps/apps-advanced-threat-protection-macos).)

   > [!CAUTION]
   > يجب عليك إنشاء جميع ملفات تعريف التكوين المطلوبة ودفعها إلى جميع الأجهزة، كما هو موضح أعلاه.

## <a name="client-device-setup"></a>إعداد جهاز العميل

لا تحتاج إلى أي توفير خاص لجهاز Mac يتجاوز [تثبيت Company Portal](/intune-user-help/enroll-your-device-in-intune-macos-cp) القياسي.

1. تأكيد إدارة الجهاز.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-3-confirmdevicemgmt.png" alt-text="صفحة تأكيد إدارة الجهاز" lightbox="images/mdatp-3-confirmdevicemgmt.png":::

    حدد **"فتح تفضيلات النظام**"، وحدد موقع **"ملف تعريف الإدارة** " في القائمة، وحدد **"موافقة"...**. سيتم عرض ملف تعريف الإدارة الخاص بك على أنه **تم التحقق منه**:

    :::image type="content" source="images/mdatp-4-managementprofile.png" alt-text="صفحة ملف تعريف الإدارة" lightbox="images/mdatp-4-managementprofile.png":::

2. حدد **متابعة** التسجيل وإكماله.

   يمكنك الآن تسجيل المزيد من الأجهزة. يمكنك أيضا تسجيلها لاحقا، بعد الانتهاء من توفير تكوين النظام وحزم التطبيقات.

3. في Intune، افتح **Manage** \> **Devices** \> **All devices**. يمكنك هنا رؤية جهازك من بين الأشخاص المدرجين:

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mdatp-5-alldevices.png" alt-text="صفحة كافة الأجهزة" lightbox="images/mdatp-5-alldevices.png":::

## <a name="verify-client-device-state"></a>التحقق من حالة جهاز العميل

1. بعد نشر ملفات تعريف التكوين على أجهزتك، افتح **"ملفات تعريف** **تفضيلات** \> النظام" على جهاز Mac.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-13-systempreferences.png" alt-text="صفحة تفضيلات النظام" lightbox="images/mdatp-13-systempreferences.png":::

   :::image type="content" source="images/mdatp-14-systempreferencesprofiles.png" alt-text="صفحة ملفات تعريف تفضيلات النظام" lightbox="images/mdatp-14-systempreferencesprofiles.png":::

2. تحقق من وجود ملفات تعريف التكوين التالية وتثبيتها. يجب أن يكون **ملف تعريف الإدارة** هو ملف تعريف نظام Intune. _Wdav-config_ _وwdav-kext_ هي ملفات تعريف تكوين النظام التي تمت إضافتها في Intune:

   :::image type="content" source="images/mdatp-15-managementprofileconfig.png" alt-text="صفحة ملفات التعريف" lightbox="images/mdatp-15-managementprofileconfig.png":::

3. يجب أن تشاهد أيضا أيقونة Microsoft Defender لنقطة النهاية في الزاوية العلوية اليسرى:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="أيقونة Microsoft Defender لنقطة النهاية في شريط المعلومات" lightbox="images/mdatp-icon-bar.png":::

## <a name="troubleshooting"></a>استكشاف الأخطاء وإصلاحها

المشكلة: لم يتم العثور على ترخيص.

الحل: اتبع الخطوات المذكورة أعلاه لإنشاء ملف تعريف الجهاز باستخدام WindowsDefenderATPOnboarding.xml.

## <a name="logging-installation-issues"></a>مشاكل تثبيت التسجيل

لمزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا بواسطة المثبت عند حدوث خطأ، راجع [مشاكل تثبيت التسجيل](mac-resources.md#logging-installation-issues).

## <a name="uninstallation"></a>الغاء التثبيت

راجع [إلغاء التثبيت](mac-resources.md#uninstalling) للحصول على تفاصيل حول كيفية إزالة Microsoft Defender لنقطة النهاية على macOS من أجهزة العميل.
