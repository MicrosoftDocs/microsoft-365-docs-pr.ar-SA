---
title: كيفية التحكم في أجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Intune (Windows 10)
description: يمكنك تكوين إعدادات Intune لتقليل التهديدات من التخزين القابل للإزالة مثل أجهزة USB.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.author: dansimp
author: dansimp
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.technology: mde
ROBOTS: NOINDEX
ms.openlocfilehash: 6ad51065ca4e919fe51cc4a2d5f4b0d53bc474b1
ms.sourcegitcommit: 1ef30b82d97bd998149235dc69d3c0e450e95285
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 09/23/2021
ms.locfileid: "63575493"
---
# <a name="how-to-control-usb-devices-and-other-removable-media-using-microsoft-defender-for-endpoint"></a>كيفية التحكم في أجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية

**ينطبق على:** [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2069559)

توصي Microsoft بنهج [](https://aka.ms/devicecontrolblog)الطبقات لتأمين الوسائط القابلة للإزالة، ويوفر Microsoft Defender ل Endpoint ميزات مراقبة ومراقبة متعددة للمساعدة على منع التهديدات في الأجهزة الطرفية غير المصرح بها من التأثير على أجهزتك:

1. [اكتشف توصيل الأحداث المتصلة و تشغيلها للم طرفيات في Microsoft Defender لصيد متقدم لنقطة النهاية](#discover-plug-and-play-connected-events). التعرف على نشاط الاستخدام المريب أو التحقق منه.

2. تكوين للسماح ببعض الأجهزة القابلة للإزالة أو حظرها فقط ومنع التهديدات.
    1. [السماح بالأجهزة القابلة للإزالة](#allow-or-block-removable-devices) أو حظرها استنادا إلى التكوينات الخاصة برفض إمكانية الوصول للكتابة إلى الأقراص القابلة للإزالة والموافقة على الأجهزة أو رفضها باستخدام "الم IDS" الخاصة بجهاز USB. تعيين نهج مرن لإعدادات تثبيت الجهاز استنادا إلى مستخدم أو مجموعة من مستخدمي Azure Active Directory (Azure AD) والأجهزة.

    2. [منع التهديدات من التخزين القابل للإزالة الذي](#prevent-threats-from-removable-storage) يتم تقديمه بواسطة أجهزة التخزين القابلة للإزالة من خلال تمكين:
        - برنامج الحماية من الفيروسات من Microsoft Defender الحماية في الوقت الحقيقي (RTP) لمسح مساحة التخزين القابلة للإزالة ضوئيا للبرامج الضارة.
        - قاعدة USB الخاصة بخفض مستوى الهجوم (ASR) لحظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB.
        - إعدادات حماية الوصول المباشر إلى الذاكرة (DMA) للحد من هجمات DMA، بما في ذلك حماية Kernel DMA ل Thunderbolt وحظر DMA حتى يقوم المستخدم تسجيل الدخول.

3. [أنشئ تنبيهات مخصصة](#create-customized-alerts-and-response-actions) وأ إجراءات استجابة لمراقبة استخدام الأجهزة القابلة للإزالة استنادا إلى أحداث التوصيل واللعب هذه أو أي أحداث أخرى من Microsoft Defender لنقطة النهاية باستخدام قواعد [الكشف المخصصة](/microsoft-365/security/defender-endpoint/custom-detection-rules).

4. [الاستجابة للتهديدات من](#respond-to-threats) الأجهزة الطرفية في الوقت الحقيقي استنادا إلى الخصائص التي تم الاستناد إلى كل طرف منها.

> [!NOTE]
> تساعد إجراءات الحد من المخاطر هذه في منع البرامج الضارة من الدخول إلى بيئتك. لحماية بيانات المؤسسة من مغادرة بيئتك، يمكنك أيضا تكوين تدابير منع فقدان البيانات. على سبيل المثال، على أجهزة Windows 10، يمكنك تكوين [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview.md) و [Windows Information Protection](/windows/security/information-protection/create-wip-policy-using-intune-azure.md)، مما يعمل على تشفير بيانات الشركة حتى لو كانت مخزنة على جهاز شخصي، أو استخدام [Storage/RemovableDiskDenyWriteAccessS CSP](/windows/client-management/mdm/policy-csp-storage#storage-removablediskdenywriteaccess) لرفض إمكانية الوصول للكتابة إلى الأقراص القابلة للإزالة. بالإضافة إلى ذلك، يمكنك تصنيف الملفات [وحمايتها](/windows/security/threat-protection/windows-defender-atp/information-protection-in-windows-overview) على أجهزة Windows (بما في ذلك أجهزة USB المثبتة) باستخدام Microsoft Defender ل Endpoint و Azure Information Protection.

## <a name="discover-plug-and-play-connected-events"></a>اكتشاف توصيل الأحداث المتصلة واللعب بها

يمكنك عرض أحداث توصيل التوصيل واللعب في البحث المتقدم في Microsoft Defender لنقطة النهاية لتحديد نشاط استخدام مريب أو إجراء عمليات تحقيق داخلية.
للحصول على أمثلة حول استعلامات البحث المتقدمة ل Defender لنقطة النهاية، راجع استعلامات البحث عن نقطة النهاية ل [Microsoft Defender GitHub إعادة التعيين](https://github.com/Microsoft/WindowsDefenderATP-Hunting-Queries).

تتوفر قوالب تقارير Power BI العينة ل Microsoft Defender لنقطة النهاية التي يمكنك استخدامها لاستعلامات الصيد المتقدمة. باستخدام هذه القوالب العينة، بما في ذلك قالب للتحكم في الجهاز، يمكنك دمج قوة الصيد المتقدم في Power BI. راجع مستودع [GitHub قوالب Power BI](https://github.com/microsoft/MDATP-PowerBI-Templates) للحصول على مزيد من المعلومات. راجع [إنشاء تقارير مخصصة باستخدام Power BI](/microsoft-365/security/defender-endpoint/api-power-bi) لمعرفة المزيد حول تكامل Power BI.

## <a name="allow-or-block-removable-devices"></a>السماح بالأجهزة القابلة للإزالة أو حظرها
يصف الجدول التالي الطرق التي يمكن من خلالها ل Microsoft Defender لنقطة النهاية السماح بالأجهزة القابلة للإزالة أو حظرها استنادا إلى التكوين المفرد.

<br>

****

|عنصر التحكم|الوصف|
|---|---|
|[تقييد محركات أقراص USB والأجهزة الملحقة الأخرى](#restrict-usb-drives-and-other-peripherals)|يمكنك السماح/منع المستخدمين من تثبيت محركات أقراص USB والأجهزة الطرفية الأخرى المضمنة في قائمة الأجهزة أو أنواع الأجهزة المعتمدة/غير المصرح بها فقط.|
|[حظر تثبيت مساحة التخزين القابلة للإزالة واستخدامها](#block-installation-and-usage-of-removable-storage)|لا يمكنك تثبيت مساحة تخزين قابلة للإزالة أو استخدامها.|
|[السماح بتثبيت الأجهزة الطرفية المعتمدة بشكل خاص واستخدامها](#allow-installation-and-usage-of-specifically-approved-peripherals)|يمكنك فقط تثبيت الأجهزة الملحقة المعتمدة التي تقوم ب الإبلاغ عن خصائص معينة في برامجها الثابتة واستخدامها.|
|[منع تثبيت الأجهزة الملحقة المحظورة تحديدا](#prevent-installation-of-specifically-prohibited-peripherals)|لا يمكنك تثبيت أو استخدام الأجهزة الملحقة المحظورة التي تقوم ب الإبلاغ عن خصائص معينة في البرامج الثابتة الخاصة بها.|
|[السماح بتثبيت الأجهزة الطرفية المعتمدة بشكل خاص واستخدامها باستخدام المثيلات المطابقة لمثيلات الأجهزة](#allow-installation-and-usage-of-specifically-approved-peripherals-with-matching-device-instance-ids)|يمكنك فقط تثبيت الأجهزة الملحقة المعتمدة التي تتطابق مع أي من هذه المثيلات في الجهاز واستخدامها.|
|[منع تثبيت الأجهزة الطرفية المحظورة بشكل خاص واستخدامها باستخدام المثيلات المطابقة لمثيلات الأجهزة](#prevent-installation-and-usage-of-specifically-prohibited-peripherals-with-matching-device-instance-ids)|لا يمكنك تثبيت الأجهزة الملحقة المحظورة التي تتطابق مع أي من هذه المثيلات في الجهاز أو استخدامها.|
|[تقييد الخدمات التي تستخدم Bluetooth](#limit-services-that-use-bluetooth)|يمكنك تحديد الخدمات التي يمكنها استخدام Bluetooth.|
|

### <a name="restrict-usb-drives-and-other-peripherals"></a>تقييد محركات أقراص USB والأجهزة الملحقة الأخرى

لمنع انتشار البرامج الضارة أو فقدان البيانات، قد تقيد المؤسسة محركات أقراص USB والأجهزة الطرفية الأخرى. يصف الجدول التالي الطرق التي يمكن أن يساعد بها Microsoft Defender لنقطة النهاية على منع تثبيت محركات أقراص USB والأجهزة الطرفية الأخرى واستخدامها.

<br>

****

|عنصر التحكم|الوصف
|---|---|
|[السماح بتثبيت محركات أقراص USB والأجهزة الطرفية الأخرى واستخدامها](#allow-installation-and-usage-of-usb-drives-and-other-peripherals)|السماح للمستخدمين بتثبيت محركات أقراص USB والأجهزة الطرفية الأخرى المضمنة في قائمة الأجهزة أو أنواع الأجهزة المعتمدة فقط|
|[منع تثبيت محركات أقراص USB والأجهزة الطرفية الأخرى واستخدامها](#prevent-installation-and-usage-of-usb-drives-and-other-peripherals)|منع المستخدمين من تثبيت محركات أقراص USB والأجهزة الطرفية الأخرى المضمنة في قائمة من الأجهزة وأنواع الأجهزة غير المصرح بها|
|

يمكن تعيين كل عناصر التحكم أعلاه من خلال قوالب Intune [الإدارية](/intune/administrative-templates-windows). توجد السياسات ذات الصلة هنا في قوالب مسؤول Intune:

![لقطة شاشة لقائمة قوالب المسؤول.](images/admintemplates.png)

> [!NOTE]
> باستخدام Intune، يمكنك تطبيق سياسات تكوين الجهاز على مستخدم Azure AD و/أو مجموعات الأجهزة.
يمكن أيضا تعيين السياسات أعلاه من خلال إعدادات [CSP](/windows/client-management/mdm/policy-csp-deviceinstallation) تثبيت الجهاز و [GPOs تثبيت الجهاز](/previous-versions/dotnet/articles/bb530324(v=msdn.10)).
>
> اختبر هذه الإعدادات وتنقيحها دائما باستخدام مجموعة تجريبية من المستخدمين والأجهزة أولا قبل تطبيقها في الإنتاج.
لمزيد من المعلومات حول التحكم في أجهزة USB، راجع [مدونة Microsoft Defender for Endpoint](https://www.microsoft.com/security/blog/2018/12/19/windows-defender-atp-has-protections-for-usb-and-removable-devices/).

#### <a name="allow-installation-and-usage-of-usb-drives-and-other-peripherals"></a>السماح بتثبيت محركات أقراص USB والأجهزة الطرفية الأخرى واستخدامها

هناك طريقة تسمح لك بتركيب محركات أقراص USB والأجهزة الطرفية الأخرى واستخدامها وهي البدء بالسماح لكل شيء. بعد ذلك، يمكنك البدء في تقليل برامج تشغيل USB المسموح بها والأجهزة الملحقة الأخرى.

> [!NOTE]
> نظرا لأن جهاز USB الطرفي غير المصرح به يمكنه الحصول على برنامج ثابت ينتحل من خصائص USB الخاصة به، نوصي بالسماح فقط بوصلات USB الطرفية المعتمدة وتحديد المستخدمين الذين يمكنهم الوصول إليها.

1. تمكين **منع تثبيت الأجهزة التي لم يتم وصفها بواسطة إعدادات النهج الأخرى** لجميع المستخدمين.
2. تمكين **السماح بتثبيت الأجهزة باستخدام برامج التشغيل التي تتطابق** مع فئات إعداد الجهاز هذه لكل [فئات إعداد الجهاز](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors).

لفرض النهج للأجهزة المثبتة بالفعل، قم بتطبيق النهج التي لديها هذا الإعداد.

عند تكوين نهج السماح بتثبيت الجهاز، يجب السماح بكل السمات الأصل أيضا. يمكنك عرض والدي الجهاز عن طريق فتح إدارة الأجهزة وعرضها حسب الاتصال.

![الأجهزة حسب الاتصال.](images/devicesbyconnection.png)

في هذا المثال، يجب إضافة الفصول التالية: HID ولوحة المفاتيح و{36fc9e60-c465-11cf-8056-44455354000}. راجع [برامج تشغيل USB التي توفرها Microsoft](/windows-hardware/drivers/usbcon/supported-usb-classes) للحصول على مزيد من المعلومات.

![وحدة تحكم مضيف الجهاز.](images/devicehostcontroller.jpg)

إذا كنت تريد تقييد أجهزة معينة، فإزالة فئة إعداد الجهاز من الجهاز الملحق الذي تريد تقييده. بعد ذلك، أضف "معرّف الجهاز" الذي تريد إضافته. يستند "معرِّف الجهاز" إلى "معرِّف المورد" وقيم "معرِّف المنتج" لجهاز. للحصول على معلومات حول تنسيقات معرف الجهاز، راجع [معرفات USB القياسية](/windows-hardware/drivers/install/standard-usb-identifiers).

للبحث عن "هويات الجهاز"، راجع [البحث عن "المعرف" للجهاز](#look-up-device-id).

على سبيل المثال:

1. قم بإزالة USBDevice للصفوف من السماح **بتثبيت الأجهزة باستخدام برامج التشغيل التي تتطابق مع إعداد الجهاز هذا**.
2. أضف "معر ة الجهاز" للسماح في السماح **بتثبيت الجهاز الذي يطابق أي من هذه المضافات**.

#### <a name="prevent-installation-and-usage-of-usb-drives-and-other-peripherals"></a>منع تثبيت محركات أقراص USB والأجهزة الطرفية الأخرى واستخدامها

إذا كنت تريد منع تثبيت فئة جهاز أو أجهزة معينة، يمكنك استخدام سياسات منع تثبيت الجهاز:

1. تمكين **منع تثبيت الأجهزة التي تتطابق مع** أي من هذه الأجهزة وإضافة هذه الأجهزة إلى القائمة.
2. تمكين **منع تثبيت الأجهزة باستخدام برامج التشغيل التي تتطابق مع فئات إعداد الجهاز هذه**.

> [!NOTE]
> يكون لنهج منع تثبيت الجهاز الأسبقية على سياسات السماح بتثبيت الجهاز.

يسمح **لك** نهج منع تثبيت الأجهزة التي تتطابق مع أي من هذه الأجهزة بتحديد قائمة بالأجهزة التي Windows تثبيتها.

لمنع تثبيت الأجهزة التي تتطابق مع أي من هذه الم IDS:

1. [ابحث عن "معرّف](#look-up-device-id) الجهاز" للأجهزة التي تريد Windows منع تثبيتها.

   ![ابحث عن مورد أو معرّف منتج.](images/lookup-vendor-product-id.png)

2. تمكين **منع تثبيت الأجهزة التي تتطابق مع** أي من هذه المضافات وإضافة المورد أو المنتج إلى القائمة.

    ![إضافة "معرِّف المورد" لمنع القائمة.](images/add-vendor-id-to-prevent-list.png)

#### <a name="look-up-device-id"></a>البحث عن "معرّف الجهاز"

يمكنك استخدام "إدارة الأجهزة" للبحث عن "معرّف الجهاز".

1. افتح إدارة الأجهزة.
2. انقر **فوق عرض** وحدد **الأجهزة حسب الاتصال**.
3. من الشجرة، انقر بيمين فوق الجهاز وحدد **خصائص**.
4. في مربع الحوار للجهاز المحدد، انقر فوق **علامة التبويب** تفاصيل.
5. انقر فوق **القائمة** المنسدل الخاصية وحدد **"الأجهزة الملقطة".**
6. انقر بضغطة زر الماوس الأيمن فوق أعلى قيمة الم ID وحدد **نسخ**.

للحصول على معلومات حول تنسيقات معرف الجهاز، راجع [معرفات USB القياسية](/windows-hardware/drivers/install/standard-usb-identifiers).

للحصول على معلومات حول "معلومات" حول "المواد"، راجع [أعضاء USB](https://www.usb.org/members).

فيما يلي مثال للبحث عن "معرِّف مورد الجهاز" أو "معرِّف المنتج" (الذي هو جزء من "معرِّف الجهاز") باستخدام PowerShell:

```powershell
Get-WMIObject -Class Win32_DiskDrive | Select-Object -Property *
```

يسمح **لك نهج** منع تثبيت الأجهزة باستخدام برامج التشغيل التي تتطابق مع فئات إعداد الجهاز هذه بتحديد فئات إعداد الجهاز التي Windows تثبيتها.

لمنع تثبيت فئات معينة من الأجهزة:

1. ابحث عن GUID لفئة إعداد الجهاز من فئات إعداد الجهاز المعرفة [من قبل النظام المتوفرة للموردين](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors).

2. تمكين **منع تثبيت الأجهزة باستخدام برامج التشغيل التي تتطابق مع** فئات إعداد الجهاز هذه وإضافة GUID للفئة إلى القائمة.

    > [!div class="mx-imgBorder"]
    > ![إضافة فئة إعداد الجهاز لمنع القائمة.](images/Add-device-setup-class-to-prevent-list.png)

### <a name="block-installation-and-usage-of-removable-storage"></a>حظر تثبيت مساحة التخزين القابلة للإزالة واستخدامها

1. سجل الدخول إلى إدارة نقاط النهاية من Microsoft [الإدارة](https://endpoint.microsoft.com/).

2. انقر **فوق ملفات تعريف** \> **تكوين الأجهزة** \> **إنشاء ملف تعريف**.

    > [!div class="mx-imgBorder"]
    > ![إنشاء ملف تعريف تكوين الجهاز.](images/create-device-configuration-profile.png)

3. استخدم الإعدادات التالية:
   - الاسم: اكتب اسما لملف التعريف
   - الوصف: كتابة وصف
   - النظام الأساسي: Windows 10 واللاحقة
   - نوع ملف التعريف: قيود الجهاز

   > [!div class="mx-imgBorder"]
   > ![إنشاء ملف تعريف.](images/create-profile.png)

4. انقر **فوق تكوين** \> **عام**.

5. **للتخزين القابل للإزالة** **واتصال USB (الهاتف المحمول فقط)،** اختر **حظر**. **تتضمن السعة التخزينية** القابلة للإزالة محركات أقراص USB، في حين يستثني **اتصال USB (** الهاتف المحمول فقط) شحن USB ولكنه يتضمن اتصالات USB الأخرى على الأجهزة المحمولة فقط.

   ![الإعدادات العامة.](images/general-settings.png)

6. انقر **فوق موافق** **لإغلاق** الإعدادات العامة **وقيود الجهاز**.

7. انقر **فوق** إنشاء لحفظ ملف التعريف.

### <a name="allow-installation-and-usage-of-specifically-approved-peripherals"></a>السماح بتثبيت الأجهزة الطرفية المعتمدة بشكل خاص واستخدامها

يمكن تحديد الأجهزة الطرفية المسموح بتثبيتها بواسطة هوية [الأجهزة الخاصة بها](/windows-hardware/drivers/install/device-identification-strings). للحصول على قائمة ببنيات المعرف الشائعة، راجع [تنسيقات معرف الجهاز](/windows-hardware/drivers/install/device-identifier-formats). اختبر التكوين قبل طرحه للتأكد من أنه يمنع الأجهزة المتوقعة ويسمح بها. اختبار مثيلات مختلفة من الأجهزة بشكل مثالي. على سبيل المثال، اختبر عدة مفاتيح USB بدلا من مفتاح USB واحد فقط.

للحصول على مثال SyncML الذي يسمح بتثبيت محدد لمحددات الأجهزة، راجع [DeviceInstallation/AllowInstallationOfMatchingDeviceIDs CSP](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceids). للسماح بفئات أجهزة معينة، راجع [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses CSP](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses).
يتطلب السماح بتثبيت أجهزة معينة أيضا تمكين [DeviceInstallation/PreventInstallationOfDevicesNotDescribedByOtherPolicySettings](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofdevicesnotdescribedbyotherpolicysettings).

### <a name="prevent-installation-of-specifically-prohibited-peripherals"></a>منع تثبيت الأجهزة الملحقة المحظورة تحديدا

يحظر Microsoft Defender for Endpoint تثبيت الأجهزة الملحقة المحظورة واستخدامها باستخدام أي من هذين الخيارين:

- [يمكن أن تمنع القوالب](/intune/administrative-templates-windows) الإدارية أي جهاز بم ID أو فئة إعداد متطابقة للأجهزة.
- [إعدادات CSP الخاصة ب تثبيت الجهاز](/windows/client-management/mdm/policy-csp-deviceinstallation) مع ملف تعريف مخصص في Intune. يمكنك منع [تثبيت محددات الأجهزة أو](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) [منع فئات معينة من الأجهزة](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdevicesetupclasses).

### <a name="allow-installation-and-usage-of-specifically-approved-peripherals-with-matching-device-instance-ids"></a>السماح بتثبيت الأجهزة الطرفية المعتمدة بشكل خاص واستخدامها باستخدام المثيلات المطابقة لمثيلات الأجهزة

يمكن تحديد الأجهزة الطرفية المسموح بتثبيتها بمثيلات [الأجهزة الخاصة بها](/windows-hardware/drivers/install/device-instance-ids). اختبر التكوين قبل طرحه للتأكد من أنه يسمح للأجهزة المتوقعة. اختبار مثيلات مختلفة من الأجهزة بشكل مثالي. على سبيل المثال، اختبر عدة مفاتيح USB بدلا من مفتاح USB واحد فقط.

يمكنك السماح بتثبيت الأجهزة الملحقة المعتمدة واستخدامها باستخدام المثيلات المطابقة لمثيلات الأجهزة من خلال تكوين [إعداد نهج DeviceInstallation/AllowInstallationOfMatchingDeviceInstanceIDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdeviceinstanceids) .

### <a name="prevent-installation-and-usage-of-specifically-prohibited-peripherals-with-matching-device-instance-ids"></a>منع تثبيت الأجهزة الطرفية المحظورة بشكل خاص واستخدامها باستخدام المثيلات المطابقة لمثيلات الأجهزة

يمكن تحديد الأجهزة الطرفية المحظور تثبيتها بواسطة المثيلات الخاصة [بها.](/windows-hardware/drivers/install/device-instance-ids) اختبر التكوين قبل طرحه للتأكد من أنه يسمح للأجهزة المتوقعة. اختبار مثيلات مختلفة من الأجهزة بشكل مثالي. على سبيل المثال، اختبر عدة مفاتيح USB بدلا من مفتاح USB واحد فقط.

يمكنك منع تثبيت الأجهزة الملحقة المحظورة بمثيلات مطابقة لمثيلات الأجهزة من خلال تكوين [إعداد نهج DeviceInstallation/PreventInstallationOfMatchingDeviceInstanceIDs](/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceinstanceids) .

### <a name="limit-services-that-use-bluetooth"></a>تقييد الخدمات التي تستخدم Bluetooth

باستخدام Intune، يمكنك تحديد الخدمات التي يمكنها استخدام Bluetooth [من خلال "Bluetooth المسموح بها".](/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) تعني الحالة الافتراضية لإعدادات "Bluetooth المسموح بها" أن كل شيء مسموح به.  بمجرد إضافة خدمة، تصبح هذه هي القائمة المسموح بها. إذا أضف العميل قيم "لوحات المفاتيح" و"الماوس"، ولم يضيف "GUID" لنقل الملفات، يجب حظر نقل الملفات.

> [!div class="mx-imgBorder"]
> ![لقطة شاشة لصفحة Bluetooth الإعدادات.](images/bluetooth.png)

## <a name="prevent-threats-from-removable-storage"></a>منع التهديدات من التخزين القابل للإزالة

يمكن أن تقدم أجهزة التخزين القابلة للإزالة مخاطر أمان إضافية لمنظمتك. يمكن أن يساعد Microsoft Defender لنقطة النهاية في تحديد الملفات الضارة وحظرها على أجهزة التخزين القابلة للإزالة.

يمكن أن يمنع Microsoft Defender ل Endpoint أيضا أجهزة USB الطرفية من استخدامها على الأجهزة للمساعدة على منع التهديدات الخارجية. يقوم بذلك باستخدام الخصائص التي تم تقريرها بواسطة أجهزة USB الطرفية لتحديد ما إذا كان يمكن تثبيتها واستخدامها على الجهاز أم لا.

تجدر الإشارة إلى أنه إذا قمت بحظر أجهزة USB أو أي فئات أجهزة أخرى باستخدام سياسات تثبيت الجهاز، فإن الأجهزة المتصلة، مثل الهواتف، لا تزال يمكن شحنها.

> [!NOTE]
> اختبر هذه الإعدادات وتنقيحها دائما باستخدام مجموعة تجريبية من المستخدمين والأجهزة أولا قبل التوزيع على نطاق واسع إلى مؤسستك.

يصف الجدول التالي الطرق التي يمكن أن يساعد بها Microsoft Defender ل Endpoint على منع التهديدات من التخزين القابل للإزالة.

لمزيد من المعلومات حول التحكم في أجهزة USB، راجع [مدونة Microsoft Defender for Endpoint](https://aka.ms/devicecontrolblog).

<br>

****

|عنصر التحكم|الوصف|
|---|---|
|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender ضوئي](#enable-microsoft-defender-antivirus-scanning)|تمكين برنامج الحماية من الفيروسات من Microsoft Defender ضوئيا من أجل الحماية في الوقت الحقيقي أو عمليات الفحص المجدولة.|
|[حظر العمليات غير الملوثة وغير الموقعة على أجهزة USB الطرفية](#block-untrusted-and-unsigned-processes-on-usb-peripherals)|حظر ملفات USB غير الموقعة أو غير الملوثة.|
|[الحماية من هجمات الوصول المباشر إلى الذاكرة (DMA)](#protect-against-direct-memory-access-dma-attacks)|تكوين الإعدادات للحماية من هجمات DMA.|
|

> [!NOTE]
> نظرا لأن جهاز USB الطرفي غير المصرح به يمكنه الحصول على برنامج ثابت ينتحل من خصائص USB الخاصة به، نوصي بالسماح فقط بوصلات USB الطرفية المعتمدة وتحديد المستخدمين الذين يمكنهم الوصول إليها.

### <a name="enable-microsoft-defender-antivirus-scanning"></a>تمكين برنامج الحماية من الفيروسات من Microsoft Defender ضوئي

تتطلب حماية مساحة التخزين القابلة للإزالة برنامج الحماية من الفيروسات من Microsoft Defender تمكين الحماية في الوقت الحقيقي [](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) أو جدولة عمليات الفحص وتكوين محركات الأقراص القابلة للإزالة للفحص.

- إذا تم تمكين الحماية في الوقت الحقيقي، يتم فحص الملفات قبل الوصول إليها وتنفيذها. يتضمن نطاق الفحص كل الملفات، بما في ذلك تلك الموجودة على الأجهزة المثبتة القابلة للإزالة مثل محركات أقراص USB. يمكنك بشكل اختياري تشغيل برنامج [نصي من PowerShell](/samples/browse/?redirectedfrom=TechNet-Gallery) لإجراء مسح مخصص لمحرك أقراص USB بعد تثبيته، بحيث يبدأ برنامج الحماية من الفيروسات من Microsoft Defender فحص جميع الملفات على جهاز قابل للإزالة بمجرد إرفاق الجهاز القابل للإزالة. ومع ذلك، نوصي بتمكين الحماية في الوقت الحقيقي لتحسين أداء الفحص، خاصة للأجهزة التخزينية الكبيرة.

- إذا تم استخدام عمليات الفحص المجدولة، ستحتاج إلى تعطيل الإعداد DisableRemovableDriveScanning (الذي يتم تمكينه بشكل افتراضي) لمسح الجهاز القابل للإزالة أثناء الفحص الكامل. يتم فحص الأجهزة القابلة للإزالة أثناء عملية فحص سريعة أو مخصصة بغض النظر عن الإعداد DisableRemovableDriveScanning.

> [!NOTE]
> نوصي بتمكين مراقبة الوقت الحقيقي للمسح الضوئي. في Intune  \>، يمكنك تمكين مراقبة الوقت الحقيقي Windows 10 في قيود الجهاز **تكوين** \>  \> برنامج الحماية من الفيروسات من Microsoft Defender **مراقبة الوقت الحقيقي**.

<!-- Need to build out point in the preceding note.
-->

### <a name="block-untrusted-and-unsigned-processes-on-usb-peripherals"></a>حظر العمليات غير الملوثة وغير الموقعة على أجهزة USB الطرفية

قد يقوم المستخدمون النهائيون بتوصيل الأجهزة القابلة للإزالة والمصابة بالبرامج الضارة.
لمنع حدوث حالات نقل، يمكن لشركة حظر ملفات USB غير الموقعة أو غير الملوثة.
بدلا من ذلك، يمكن للشركات الاستفادة من ميزة التدقيق [](/microsoft-365/security/defender-endpoint/attack-surface-reduction) لقواعد الحد من سطح الهجوم لمراقبة نشاط العمليات غير المدققة وغير الموقعة التي تنفذ على جهاز USB طرفي.
يمكن إجراء ذلك من خلال تعيين العمليات غير المدققة وغير الموقعة التي يتم تشغيلها من **USB** إلى حظر  أو تدقيق **فقط**، على التوالي.
باستخدام هذه القاعدة، يمكن للمسؤولين منع تشغيل الملفات القابلة للتنفيذ غير الموقعة أو غير المدققة أو تدقيقها من محركات أقراص USB القابلة للإزالة، بما في ذلك بطاقات SD.
تتضمن أنواع الملفات المتأثرة الملفات القابلة للتنفيذ (مثل ملفات .exe أو .dll أو .scr) وملفات البرامج النصية مثل ملفات PowerShell (.ps) أو VisualBasic (.vbs) أو JavaScript (.js).

تتطلب هذه الإعدادات [تمكين الحماية في الوقت الحقيقي](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus).

1. سجل [الدخول إلى إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/).

2. انقر **فوق** \> **الأجهزة Windows** \> **"سياسات** \> التكوين **" إنشاء ملف تعريف**.

    ![إنشاء ملف تعريف تكوين الجهاز.](images/create-device-configuration-profile.png)

3. استخدم الإعدادات التالية:
   - النظام الأساسي: Windows 10 واللاحقة
   - نوع ملف التعريف: قيود الجهاز

   > [!div class="mx-imgBorder"]
   > ![إنشاء ملف تعريف حماية نقطة النهاية.](images/create-endpoint-protection-profile.png)

4. انقر **فوق إنشاء**.

5. بالنسبة **إلى العمليات غير الموقعة وغير الملوثة** التي يتم تشغيلها من USB، اختر **حظر**.

   ![حظر العمليات غير الملوثة.](images/block-untrusted-processes.png)

6. انقر **فوق** موافق لإغلاق الإعدادات **وقيود الجهاز**.

### <a name="protect-against-direct-memory-access-dma-attacks"></a>الحماية من هجمات الوصول المباشر إلى الذاكرة (DMA)

يمكن أن تؤدي هجمات DMA إلى الكشف عن معلومات حساسة مقيمة على كمبيوتر شخصي، أو حتى إلى ضخ البرامج الضارة التي تسمح للمهاجمين بتجاوز شاشة التأمين أو التحكم في أجهزة الكمبيوتر عن بعد. تساعد الإعدادات التالية على منع هجمات DMA:

1. بدءا من Windows 10 1803، قدمت Microsoft [Kernel DMA Protection ل Thunderbolt](/windows/security/information-protection/kernel-dma-protection-for-thunderbolt.md) لتوفير الحماية الأصلية من هجمات DMA عبر منافذ Thunderbolt. يتم تمكين Kernel DMA Protection ل Thunderbolt من قبل الشركات المصنعة للنظام ولا يمكن للمستخدمين تشغيلها أو إيقاف تشغيلها.

   بدءا من Windows 10 1809، يمكنك ضبط مستوى حماية Kernel DMA من خلال تكوين [DMA Guard CSP](/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy). هذا عنصر تحكم إضافي للم الملحقات التي لا تدعم عزل ذاكرة الجهاز (المعروف أيضا ب إعادة استخدام DMA). يتيح عزل الذاكرة ل OS الاستفادة من وحدة إدارة الذاكرة I/O (IOMMU) لجهاز لحظر الوصول إلى الذاكرة أو I/O غير مسموح به، من قبل الطرفية (الحماية من الذاكرة). بعبارة أخرى، يعين نظام التشغيل نطاق ذاكرة معينا إلى الملحق. إذا حاول الجهاز الطرفي القراءة/الكتابة للذاكرة خارج النطاق المعين، يمنعه نظام التشغيل.

   يمكن توصيل الأجهزة الطرفية التي تدعم عزل ذاكرة الجهاز دائما. الأجهزة الطرفية التي لا يمكن حظرها أو السماح بها أو السماح بها فقط بعد تسجيل المستخدم الدخول (افتراضي).

2. على Windows 10 التي لا تدعم حماية Kernel DMA، يمكنك:

   - [حظر DMA حتى يقوم المستخدم تسجيل الدخول](/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)
   - [حظر كافة الاتصالات عبر منافذ Thunderbolt (بما في ذلك أجهزة USB)](https://support.microsoft.com/help/2516445/blocking-the-sbp-2-driver-and-thunderbolt-controllers-to-reduce-1394-d)

## <a name="create-customized-alerts-and-response-actions"></a>إنشاء تنبيهات مخصصة والإجراءات الخاصة بالاستجابة

يمكنك إنشاء تنبيهات مخصصة أو إجراءات استجابة باستخدام موصل WDATP وقواعد الكشف المخصصة:

**إجراءات استجابة موصل Wdatp:**

**التحقق:** بدء التحقيق، وجمع حزمة التحقيق، وعزل جهاز.

**المسح الضوئي للتهديدات** على أجهزة USB.

**تقييد تنفيذ جميع التطبيقات** على الجهاز باستثناء مجموعة محددة مسبقا

موصل MDATP هو واحد من أكثر من 200 موصل معرف مسبقا بما في ذلك Outlook أو Teams أو Slack وغير ذلك. يمكن إنشاء موصلات مخصصة.

- [مزيد من المعلومات حول إجراءات استجابة موصل WDATP](/connectors/wdatp/)

**إجراء الاستجابة لقواعد الكشف المخصصة:**

يمكن تطبيق كل من إجراءات مستوى الجهاز والملف.

- [مزيد من المعلومات حول إجراءات الاستجابة لقواعد الكشف المخصصة](/microsoft-365/security/defender-endpoint/custom-detection-rules)

للحصول على معلومات حول أحداث الصيد المتقدمة ذات الصلة بالتحكم في الجهاز وأمثلة حول كيفية إنشاء تنبيهات مخصصة، راجع تحديثات الصيد المتقدمة [: أحداث USB](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/Advanced-hunting-updates-USB-events-machine-level-actions-and/ba-p/824152) والإجراءات على مستوى الجهاز والتغييرات في المخطط.

## <a name="respond-to-threats"></a>الاستجابة للتهديدات

يمكنك إنشاء تنبيهات مخصصة واستجابات تلقائية باستخدام [قواعد الكشف المخصص ل Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/custom-detection-rules). تغطي إجراءات الاستجابة ضمن الكشف المخصص كلا من إجراءات مستوى الجهاز والملف. يمكنك أيضا إنشاء تنبيهات أو إجراءات استجابة تلقائية باستخدام [تطبيقات Power Apps](https://powerapps.microsoft.com/) [Flow](https://flow.microsoft.com/) باستخدام [موصل Microsoft Defender ل Endpoint](/connectors/wdatp/). يدعم الموصل إجراءات التحقيق والمسح الضوئي للتهديدات وتقييد تشغيل التطبيقات. وهو واحد من أكثر من 200 موصل معرف مسبقا بما في ذلك Outlook Teams وS slack والمزيد. يمكن أيضا إنشاء موصلات مخصصة. راجع [الموصلات](/connectors/) لمعرفة المزيد حول الموصلات.

على سبيل المثال، باستخدام أي من الأسلوبين، يمكنك تشغيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا عند تثبيت جهاز USB على جهاز.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تكوين الحماية في الوقت الحقيقي برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus)
- [Defender/AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)
- [النهج/DeviceInstallation CSP](/windows/client-management/mdm/policy-csp-deviceinstallation)
- [إجراء فحص مخصص لجهاز قابل للإزالة](/samples/browse/?redirectedfrom=TechNet-Gallery)
- [قالب Power BI للتحكم في الجهاز لإعداد التقارير المخصصة](https://github.com/microsoft/MDATP-PowerBI-Templates)
- [BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview.md)
- [Windows حماية المعلومات](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure.md)
