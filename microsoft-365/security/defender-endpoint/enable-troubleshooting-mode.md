---
title: بدء استخدام وضع استكشاف الأخطاء وإصلاحها في Microsoft Defender لنقطة النهاية
description: قم بتشغيل وضع استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية لمعالجة مشكلات مكافحة الفيروسات المختلفة.
keywords: مكافحة الفيروسات، واستكشاف الأخطاء وإصلاحها، ووضع استكشاف الأخطاء وإصلاحها، والحماية من العبث، والتوافق
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: eee3e07825b2775b4eff1b5fb45a6e1f86fc3a1b
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857449"
---
# <a name="get-started-with-troubleshooting-mode-in-microsoft-defender-for-endpoint"></a>بدء استخدام وضع استكشاف الأخطاء وإصلاحها في Microsoft Defender لنقطة النهاية 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

يسمح لك وضع استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية باستكشاف أخطاء ميزات الحماية من الفيروسات المختلفة في Microsoft Defender وإصلاحها من خلال تمكينها من الجهاز واختبار سيناريوهات مختلفة، حتى لو كان يتم التحكم فيها بواسطة نهج المؤسسة. يتم تعطيل وضع استكشاف الأخطاء وإصلاحها بشكل افتراضي ويتطلب منك تشغيله لجهاز (و/أو مجموعة من الأجهزة) لفترة محدودة. لاحظ أن هذه ميزة خاصة بالمؤسسات فقط، وتتطلب الوصول Microsoft 365 Defender.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- استخدم وضع استكشاف الأخطاء وإصلاحها لتعطيل/تغيير إعداد الحماية من العبث لتنفيذ:

  - استكشاف الأخطاء وإصلاحها الوظيفية ل Microsoft Defender Antivirus /توافق التطبيق (كتل التطبيقات الإيجابية الخاطئة).
  - استكشاف أخطاء أداء برنامج الحماية من الفيروسات من Microsoft Defender وإصلاحها باستخدام وضع استكشاف الأخطاء وإصلاحها ومعالجة الحماية من العبث وإعدادات مكافحة الفيروسات الأخرى.

- إذا حدث العبث (على سبيل المثال، يتم تغيير اللقطة `MpPreference` أو حذفها)، فسينتهي وضع استكشاف الأخطاء وإصلاحها وسيتم تمكين الحماية من العبث على الجهاز.

- يمكن للمسؤولين المحليين، الذين لديهم الأذونات المناسبة، تغيير التكوينات على نقاط النهاية الفردية التي يتم تأمينها عادة بواسطة النهج. قد يكون وجود جهاز في وضع استكشاف الأخطاء وإصلاحها مفيدا عند تشخيص أداء Microsoft Defender Antivirus وسيناريوهات التوافق.

  - لن يتمكن المسؤولون المحليون من إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته.
  - سيتمكن المسؤولون المحليون من تكوين جميع إعدادات الأمان الأخرى في مجموعة الحماية من الفيروسات من Microsoft Defender (على سبيل المثال، حماية السحابة والحماية من العبث).

- سيكون للمسؤولين الذين لديهم أذونات "إدارة إعدادات الأمان" حق الوصول لتشغيل وضع استكشاف الأخطاء وإصلاحها.

- يجمع Microsoft Defender لنقطة النهاية السجلات وبيانات التحقيق طوال عملية استكشاف الأخطاء وإصلاحها.

  - `MpPreference` سيتم أخذ لقطة قبل بدء وضع استكشاف الأخطاء وإصلاحها.
  - سيتم أخذ اللقطة الثانية قبل انتهاء صلاحية وضع استكشاف الأخطاء وإصلاحها.
  - كما سيتم جمع السجلات التشغيلية من أثناء وضع استكشاف الأخطاء وإصلاحها.

  - سيتم جمع جميع السجلات واللقطات أعلاه وستتوفر للمسؤول لجمعها باستخدام ميزة [حزمة التحقيق "تجميع](respond-machine-alerts.md#collect-investigation-package-from-devices) " على صفحة الجهاز. لاحظ أن Microsoft لن تزيل هذه البيانات من الجهاز حتى يقوم المسؤول بتجميعها.

- يمكن للمسؤولين أيضا مراجعة التغييرات في الإعدادات التي تحدث أثناء وضع استكشاف الأخطاء وإصلاحها في **عارض الأحداث** على صفحة الجهاز.

- يتم إيقاف تشغيل وضع استكشاف الأخطاء وإصلاحها تلقائيا بعد الوصول إلى وقت انتهاء الصلاحية (يستمر لمدة 3 ساعات). بعد انتهاء الصلاحية، ستصبح جميع التكوينات المدارة بواسطة النهج للقراءة فقط مرة أخرى وستعود إلى ما كانت عليه قبل تشغيل وضع استكشاف الأخطاء وإصلاحها.

- قد يستغرق الأمر ما يصل إلى 15 دقيقة من وقت إرسال الأمر من Microsoft 365 Defender إلى وقت تنشيطه على الجهاز.

- سيتم إرسال الإعلام إلى المستخدم النهائي عند بدء وضع استكشاف الأخطاء وإصلاحها وعند انتهاء وضع استكشاف الأخطاء وإصلاحها. سيتم أيضا إرسال تحذير لإعلامه بأنه سينتهي قريبا.

- سيتم تحديد بداية وضع استكشاف الأخطاء وإصلاحها ونهايتك في **المخطط الزمني للجهاز** على صفحة الجهاز.

- يمكنك الاستعلام عن جميع أحداث وضع استكشاف الأخطاء وإصلاحها في التتبع المتقدم.

> [!NOTE]
> سيتم تطبيق تغييرات إدارة النهج على الجهاز عندما يكون نشطا في وضع استكشاف الأخطاء وإصلاحها. ومع ذلك، لن تصبح التغييرات سارية المفعول حتى تنتهي صلاحية وضع استكشاف الأخطاء وإصلاحها. بالإضافة إلى ذلك، لن يتم تطبيق تحديثات Microsoft Defender Antivirus Platform أثناء وضع استكشاف الأخطاء وإصلاحها. سيتم تطبيق تحديثات النظام الأساسي بمجرد انتهاء وضع استكشاف الأخطاء وإصلاحها بتحديث Windows.

## <a name="prerequisites"></a>المتطلبات الأساسية

- جهاز يعمل Windows 10 (الإصدار 19044.1618 أو أحدث) أو Windows 11 أو Windows Server 2019 أو Windows Server 2022.

  فصل دراسي/حجر أحمر|إصدار نظام التشغيل|Release
  :---|:---|:---
  21H2/SV1|>=22000.593|[KB5011563: كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011563)
  20H1/20H2/21H1|>=19042.1620<br/> >=19041.1620<br/> >=19043.1620|[KB5011543: كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011543)
  Windows Server 2022|>=20348.617|[KB5011558: كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011558)
  Windows Server 2019 (RS5)|>=17763.2746|[KB5011551: كتالوج تحديث Microsoft](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5011551)

- لتطبيق وضع استكشاف الأخطاء وإصلاحها، يجب أن يكون Microsoft Defender لنقطة النهاية مسجلا من قبل المستأجر ونشطا على الجهاز.

- يجب أن يعمل الجهاز بنشاط على برنامج الحماية من الفيروسات من Microsoft Defender، الإصدار 4.18.2203 أو الإصدارات الأحدث.

## <a name="enable-the-troubleshooting-mode"></a>تمكين وضع استكشاف الأخطاء وإصلاحها

1. انتقل إلى مدخل Microsoft 365 Defender (<https://security.microsoft.com>)، وسجل الدخول.

2. انتقل إلى صفحة الجهاز/صفحة الجهاز للجهاز الذي ترغب في تشغيله في وضع استكشاف الأخطاء وإصلاحها. حدد **تشغيل وضع استكشاف الأخطاء وإصلاحها**. لاحظ أن هذا يتطلب أذونات "إدارة إعدادات الأمان في مركز الأمان" Microsoft Defender لنقطة النهاية.

   :::image type="content" source="../../media/ts-mode-menu.png" alt-text="تشغيل وضع استكشاف الأخطاء وإصلاحها" lightbox="../../media/ts-mode-menu.png":::

3. تأكد من رغبتك في تشغيل وضع استكشاف الأخطاء وإصلاحها للجهاز.

   :::image type="content" source="../../media/ts-mode-conf-flyout.png" alt-text="القائمة المنبثقة للتكوين" lightbox="../../media/ts-mode-conf-flyout.png":::

4. تظهر صفحة الجهاز أن الجهاز الآن في وضع استكشاف الأخطاء وإصلاحها.

   :::image type="content" source="../../media/ts-mode-option-greyed-out.png" alt-text="الجهاز الآن في وضع استكشاف الأخطاء وإصلاحها" lightbox="../../media/ts-mode-option-greyed-out.png":::

## <a name="advanced-hunting-queries"></a>استعلامات التتبع المتقدمة

فيما يلي بعض استعلامات التتبع المتقدمة التي تم إنشاؤها مسبقا لإعطائك رؤية لأحداث استكشاف الأخطاء وإصلاحها التي تحدث في بيئتك. يمكنك أيضا استخدام هذه الاستعلامات [لإنشاء قواعد الكشف](/defender/custom-detection-rules.md#create-a-custom-detection-rule) التي تنبهك عندما تكون الأجهزة في وضع استكشاف الأخطاء وإصلاحها.

### <a name="get-troubleshooting-events-for-a-particular-device"></a>الحصول على أحداث استكشاف الأخطاء وإصلاحها لجهاز معين
ابحث حسب deviceId أو deviceName عن طريق التعليق على الأسطر المعنية.  
```kusto
//let deviceName = "<deviceName>";   // update with device name
let deviceId = "<deviceID>";   // update with device id
DeviceEvents
| where DeviceId == deviceId
//| where DeviceName  == deviceName
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| project Timestamp,DeviceId, DeviceName, _tsmodeproperties,
 _tsmodeproperties.TroubleshootingState, _tsmodeproperties.TroubleshootingPreviousState, _tsmodeproperties.TroubleshootingStartTime,
 _tsmodeproperties.TroubleshootingStateExpiry, _tsmodeproperties.TroubleshootingStateRemainingMinutes,
 _tsmodeproperties.TroubleshootingStateChangeReason, _tsmodeproperties.TroubleshootingStateChangeSource
```

### <a name="devices-currently-in-troubleshooting-mode"></a>الأجهزة الموجودة حاليا في وضع استكشاف الأخطاء وإصلاحها  

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
|summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| order by Timestamp desc
```

### <a name="count-of-troubleshooting-mode-instances-by-device"></a>عدد مثيلات وضع استكشاف الأخطاء وإصلاحها حسب الجهاز

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where Timestamp > ago(30d)  // choose the date range you want
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| sort by count_
```

### <a name="total-count"></a>العدد الإجمالي

```kusto
DeviceEvents
| where ActionType == "AntivirusTroubleshootModeEvent"
| extend _tsmodeproperties = parse_json(AdditionalFields)
| where Timestamp > ago(2d) //beginning of time range
| where Timestamp < ago(1d) //end of time range
| where _tsmodeproperties.TroubleshootingStateChangeReason contains "started"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count()
| where count_ > 5          // choose your max # of TS mode instances for your time range
```

## <a name="related-topic"></a>الموضوع ذو الصلة

- [سيناريوهات وضع استكشاف الأخطاء وإصلاحها](troubleshooting-mode-scenarios.md)
- [حماية إعدادات الأمان باستخدام الحماية من العبث](prevent-changes-to-security-settings-with-tamper-protection.md)
