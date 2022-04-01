---
title: حماية التخزين القابلة للإزالة من Microsoft Defender للتحكم في جهاز نقطة النهاية
description: فهم 'الإمكانات التي تساعد على منع المستخدم أو الجهاز أو كليهما من استخدام وسائط تخزين غير مصرح بها قابلة للإزالة
keywords: وسائط تخزين قابلة للإزالة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: cc1c2a5fc05b795c0fc69ebc8a3b50dbf556960b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63579595"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>حماية التخزين القابلة للإزالة من Microsoft Defender للتحكم في جهاز نقطة النهاية


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

يمنع التحكم في الجهاز حماية التخزين القابلة للإزالة في Microsoft Defender ل Endpoint المستخدمين أو نقاط النهاية أو كليهما من استخدام وسائط تخزين غير مصرح بها.

## <a name="protection-policies"></a>سياسات الحماية

### <a name="removable-storage-access-control"></a>التحكم بالوصول إلى التخزين القابل للإزالة

**الإمكانات**

- *التدقيق* القراءة أو الكتابة أو تنفيذ الوصول إلى مساحة تخزين قابلة للإزالة استنادا إلى خصائص الجهاز المختلفة، مع استثناء أو بدونه.
- *منع* القراءة أو الكتابة أو تنفيذ الوصول مع استثناء أو بدونه - السماح بجهاز معين استنادا إلى خصائص الجهاز المختلفة.

**Windows 10 Windows 11 تفاصيل الدعم**:

- يتم تطبيقه على مستوى الجهاز ومستوى المستخدم. أو كليهما. السماح فقط للأشخاص المحددين بإجراء القراءة/الكتابة/تنفيذ الوصول إلى مساحة تخزين محددة قابلة للإزالة على جهاز معين.
- دعم MEM OMA-URI و GPO.
- "[خصائص الجهاز"](#device-properties) المعتمدة كما هو مدرج.
- للحصول على ميزة في Windows، راجع [التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md).

**النظام الأساسي المعتمد** - Windows 10 Windows 11

**تفاصيل دعم macOS**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله.
- للحصول على معلومات خاصة ب macOS، راجع [التحكم في الجهاز ل macOS](mac-device-control-overview.md).

**النظام الأساسي المعتمد** - macOS Catalina 10.15.4+ (مع تمكين ملحقات النظام)


### <a name="device-installation"></a>تثبيت الجهاز

**الإمكانات** - منع التثبيت مع أو بدون استثناء استنادا إلى خصائص الجهاز المختلفة.

**Windows 10 Windows 11 تفاصيل الدعم**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله.
- يدعم إدارة نقاط النهاية من Microsoft نهج المجموعة.
- "[خصائص الجهاز"](#device-properties) المعتمدة كما هو مدرج.
- لمزيد من المعلومات حول Windows، راجع كيفية التحكم في أجهزة USB وغيرها من الوسائط القابلة [للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md).

**النظام الأساسي المعتمد** - Windows 10 Windows 11

**تفاصيل دعم macOS**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله
- للحصول على معلومات خاصة ب macOS، راجع [التحكم في الجهاز ل macOS](mac-device-control-overview.md).

**النظام الأساسي المعتمد** - macOS Catalina 10.15.4+ (مع تمكين ملحقات النظام) أو أي وقت لاحق

### <a name="endpoint-dlp-removable-storage"></a>مساحة تخزين DLP القابلة للإزالة في نقطة النهاية

**الإمكانات** - تدقيق المستخدم أو تحذيره أو منعه من نسخ عنصر أو معلومات إلى وسائط قابلة للإزالة أو جهاز USB.

**الوصف** - لمزيد من المعلومات حول Windows، راجع [التعرف على Microsoft 365 فقدان البيانات في نقطة النهاية](../../compliance/endpoint-dlp-learn-about.md).

**النظام الأساسي المعتمد** - Windows 10 Windows 11

### <a name="bitlocker"></a>BitLocker

**الإمكانات**:

- حظر البيانات لكي تتم كتابتها على محركات الأقراص القابلة للإزالة غير المحمية من BitLocker.
- حظر الوصول إلى محركات الأقراص القابلة للإزالة ما لم يتم تشفيرها على كمبيوتر تملكه مؤسستك

**الوصف** - لمزيد من المعلومات حول Windows، راجع [BitLocker - محرك أقراص الإعدادات](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**النظام الأساسي المعتمد** - Windows 10 Windows 11

## <a name="device-properties"></a>خصائص الجهاز

يسمح لك Microsoft Defender لمراقبة جهاز Endpoint Storage Protection القابل للإزالة بتقييد الوصول إلى مساحة التخزين القابلة للإزالة استنادا إلى الخصائص الموضحة في الجدول أدناه:

<br/><br/>

|اسم الخاصية|السياسات المطبقة|ينطبق على أنظمة التشغيل|الوصف|
|---|---|---|---|
|فئة الجهاز|[كيفية التحكم في أجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md)|بالنسبة لنظام التشغيل|للحصول على معلومات حول تنسيقات "معرفة الجهاز"، راجع [فئة إعداد الجهاز](/windows-hardware/drivers/install/overview-of-device-setup-classes). يوفر الارتباطان التاليان القائمة الكاملة لفئات إعداد الجهاز. تشير فئات "استخدام النظام" في معظمها إلى الأجهزة التي تأتي مع كمبيوتر/جهاز من المصنع، في حين تشير فئات "المورد" في الغالب إلى الأجهزة التي يمكن توصيلها بجهاز كمبيوتر/جهاز موجود: فئات إعداد الجهاز المعرفة من قبل النظام المتوفرة للموردين - برامج تشغيل [Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) وفئات إعداد الجهاز المعرفة من قبل النظام محجوزة لاستخدام النظام [- Windows برامج التشغيل](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **ملاحظة**: يمكن تطبيق تثبيت الجهاز على أي أجهزة، وليس فقط على مساحة التخزين القابلة للإزالة.|
|الم ID الأساسي|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل|يتضمن الم ID الأساسي سعة تخزينية قابلة للإزالة ومخزن الأقراص المضغوطة/أقراص DVD Windows Portable Device/WPD.|
|"معرّف الجهاز"|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)؛ <p> [كيفية التحكم في أجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md)|بالنسبة لنظام التشغيل|للحصول على معلومات حول تنسيقات معرف الجهاز، راجع [معرفات USB](/windows-hardware/drivers/install/standard-usb-identifiers) القياسية، على سبيل المثال، USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|"معرّف الأجهزة"|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md) <p> [كيفية التحكم في أجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md)|بالنسبة لنظام التشغيل|تعرفت سلسلة على الجهاز في النظام، على سبيل المثال، USBSTOR\DiskGeneric_Flash_Disk___8.07؛ **ملاحظة**: إن "معرّف الأجهزة" ليس فريدا؛ قد تشارك أجهزة مختلفة القيمة نفسها.|
|"المثيل"|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md) <p> تثبيت الجهاز|بالنسبة لنظام التشغيل|تعرف السلسلة الجهاز في النظام بشكل فريد، على سبيل المثال، USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|اسم ودود|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل|سلسلة مرفقة بجهاز، على سبيل المثال، جهاز USB Generic Flash Disk|
|"مورد" / "معرّف المنتج"|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل <p> macOS|إن "رقم المورد" هو رمز المورد المكون من أربعة أرقام الذي تم تعيينه إلى المورد من قبل لجنة USB. إن "رقم المنتج" هو رمز المنتج المكون من أربعة أرقام الذي يعينه المورد إلى الجهاز؛ دعم أحرف البدل.|
|الرقم التسلسلي|[التحكم بالوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل <p> macOS |على سبيل المثال <SerialNumberId>، 002324B534BCB431B000058A</SerialNumberId>|
