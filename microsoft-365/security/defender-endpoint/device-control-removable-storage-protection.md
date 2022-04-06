---
title: Microsoft Defender لنقطة النهاية Device Control Removable Storage Protection
description: فهم 'القدرات التي تساعد على منع المستخدم أو الجهاز أو كليهما من استخدام وسائط التخزين القابلة للإزالة غير المصرح بها
keywords: وسائط التخزين القابلة للإزالة
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
ms.openlocfilehash: 3d679cfa4f09b06e2c7923ee1fe6e47247d90f76
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665063"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender لنقطة النهاية Device Control Removable Storage Protection


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

تمنع حماية التخزين القابلة للإزالة للتحكم في الجهاز في Microsoft Defender لنقطة النهاية المستخدمين أو نقاط النهاية أو كليهما من استخدام وسائط تخزين غير مصرح بها قابلة للإزالة.

## <a name="protection-policies"></a>نهج الحماية

### <a name="removable-storage-access-control"></a>التحكم في الوصول إلى التخزين القابل للإزالة

**قدرات**

- *مراجعه الحسابات* الوصول للقراءة أو الكتابة أو التنفيذ إلى التخزين القابل للإزالة استنادا إلى خصائص الجهاز المختلفة، مع استثناء أو بدونه.
- *منع* الوصول للقراءة أو الكتابة أو التنفيذ مع استثناء أو بدونه - السماح بجهاز معين استنادا إلى خصائص الجهاز المختلفة.

**تفاصيل دعم Windows 10 والدعم Windows 11**:

- يتم تطبيقه على مستوى الجهاز، على مستوى المستخدم. أو كليهما. السماح فقط لأشخاص معينين يقومون بإجراء الوصول للقراءة/الكتابة/التنفيذ إلى تخزين معين قابل للإزالة على جهاز معين.
- دعم MEM OMA-URI وGPO.
- '[خصائص الجهاز](#device-properties)' المدعومة كما هو مدرج.
- للحصول على ميزة في Windows، راجع التحكم في [الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

**تفاصيل دعم macOS**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله.
- للحصول على معلومات محددة حول macOS، راجع [عنصر تحكم الجهاز لنظام التشغيل macOS](mac-device-control-overview.md).

**النظام الأساسي المدعوم** - macOS Catalina 10.15.4+ (مع تمكين ملحقات النظام)


### <a name="device-installation"></a>تثبيت الجهاز

**الإمكانات** - منع التثبيت مع أو بدون استثناء استنادا إلى خصائص الجهاز المختلفة.

**تفاصيل دعم Windows 10 والدعم Windows 11**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله.
- يدعم إدارة نقاط النهاية من Microsoft وكائنات نهج المجموعة.
- '[خصائص الجهاز](#device-properties)' المدعومة كما هو مدرج.
- لمزيد من المعلومات حول Windows، راجع [كيفية التحكم في أجهزة USB والوسائط الأخرى القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

**تفاصيل دعم macOS**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله
- للحصول على معلومات محددة حول macOS، راجع [عنصر تحكم الجهاز لنظام التشغيل macOS](mac-device-control-overview.md).

**النظام الأساسي المدعوم** - macOS Catalina 10.15.4+ (مع تمكين ملحقات النظام) أو أحدث

### <a name="endpoint-dlp-removable-storage"></a>تخزين DLP القابل للإزالة لنقطة النهاية

**الإمكانات** - تدقيق المستخدم أو تحذيره أو منعه من نسخ عنصر أو معلومات إلى وسائط قابلة للإزالة أو جهاز USB.

**الوصف** - لمزيد من المعلومات حول Windows، راجع [التعرف على Microsoft 365 منع فقدان بيانات نقطة النهاية](../../compliance/endpoint-dlp-learn-about.md).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

### <a name="bitlocker"></a>Bitlocker

**القدرات**:

- حظر البيانات المطلوب كتابتها إلى محركات الأقراص القابلة للإزالة غير المحمية ب BitLocker.
- حظر الوصول إلى محركات الأقراص القابلة للإزالة ما لم تكن مشفرة على كمبيوتر تملكه مؤسستك

**الوصف** - لمزيد من المعلومات حول Windows، راجع [BitLocker - محرك الأقراص القابل للإزالة الإعدادات](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

## <a name="device-properties"></a>خصائص الجهاز

تسمح لك Microsoft Defender لنقطة النهاية Device Control Removable Storage Protection بتقييد الوصول إلى التخزين القابل للإزالة استنادا إلى الخصائص الموضحة في الجدول أدناه:

<br/><br/>

|اسم الخاصية|النهج المعمول بها|ينطبق على أنظمة التشغيل|الوصف|
|---|---|---|---|
|فئة الجهاز|[كيفية التحكم في أجهزة USB والوسائط الأخرى القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md)|بالنسبة لنظام التشغيل|للحصول على معلومات حول تنسيقات معرف الجهاز، راجع [فئة إعداد الجهاز](/windows-hardware/drivers/install/overview-of-device-setup-classes). يوفر الارتباطان التاليان القائمة الكاملة لفئات إعداد الجهاز. تشير فئات "استخدام النظام" في الغالب إلى الأجهزة التي تأتي مع كمبيوتر/جهاز من المصنع، بينما تشير فئات "المورد" في الغالب إلى الأجهزة التي يمكن توصيلها بجهاز كمبيوتر/جهاز موجود: [فئات إعداد الجهاز المعرفة من قبل النظام المتوفرة للموردين - برامج تشغيل Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) [وفئات إعداد الأجهزة المعرفة من قبل النظام المحجوزة لاستخدام النظام - برامج تشغيل Windows](/windows-hardware/drivers/install/system-defined-device-setup-classes-reserved-for-system-use). **ملاحظة**: يمكن تطبيق تثبيت الجهاز على أي أجهزة، وليس فقط على التخزين القابل للإزالة.|
|المعرف الأساسي|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل|يتضمن المعرف الأساسي التخزين القابل للإزالة والقرص المضغوط/DVD Windows Portable Device/WPD.|
|معرف الجهاز|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)؛ <p> [كيفية التحكم في أجهزة USB والوسائط الأخرى القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md)|بالنسبة لنظام التشغيل|للحصول على معلومات حول تنسيقات معرف الجهاز، راجع [معرفات USB القياسية](/windows-hardware/drivers/install/standard-usb-identifiers)، على سبيل المثال، USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07|
|معرف الجهاز|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md) <p> [كيفية التحكم في أجهزة USB والوسائط الأخرى القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md)|بالنسبة لنظام التشغيل|حددت سلسلة الجهاز في النظام، على سبيل المثال، USBSTOR\DiskGeneric_Flash_Disk___8.07; **ملاحظة**: معرف الجهاز ليس فريدا؛ قد تشترك الأجهزة المختلفة في نفس القيمة.|
|معرف المثيل|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md) <p> تثبيت الجهاز|بالنسبة لنظام التشغيل|تعرف السلسلة الجهاز في النظام بشكل فريد، على سبيل المثال، USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0|
|اسم مألوف|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل|سلسلة متصلة بالجهاز، على سبيل المثال، جهاز USB عام على قرص محمول|
|معرف المورد / معرف المنتج|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل <p> ماك|معرف المورد هو رمز المورد المكون من أربعة أرقام الذي تعينه لجنة USB للمورد. معرف المنتج هو رمز المنتج المكون من أربعة أرقام الذي يقوم المورد بتعيينه إلى الجهاز؛ دعم حرف البدل.|
|معرف الرقم التسلسلي|[التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md)|بالنسبة لنظام التشغيل <p> ماك |على سبيل المثال `<SerialNumberId>002324B534BCB431B000058A</SerialNumberId>`|
