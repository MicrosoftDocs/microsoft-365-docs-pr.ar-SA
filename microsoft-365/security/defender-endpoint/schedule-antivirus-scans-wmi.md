---
title: جدولة عمليات فحص مكافحة الفيروسات باستخدام Windows Management Instrumentation
description: جدولة عمليات فحص مكافحة الفيروسات باستخدام WMI
keywords: فحص سريع، فحص كامل، WMI، جدول، برنامج الحماية من الفيروسات
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: pauhijbr, ksarens
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 2b25876a43dea3b1598d4bdfa89cf4724c0fca14
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788909"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>جدولة عمليات فحص مكافحة الفيروسات باستخدام Windows Management Instrumentation (WMI)

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

تصف هذه المقالة كيفية تكوين عمليات الفحص المجدولة باستخدام WMI. لمعرفة المزيد حول جدولة عمليات الفحص وأنواع الفحص، راجع [تكوين عمليات الفحص السريعة أو الكاملة المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>استخدام Windows Management Instruction (WMI) لجدولة عمليات الفحص

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

لمزيد من المعلومات والمعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>WMI لجدولة عمليات الفحص عندما لا تكون نقطة النهاية قيد الاستخدام

استخدم [الأسلوب Set للفئة MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ScanOnlyIfIdleEnabled
```

لمزيد من المعلومات حول واجهات برمجة التطبيقات والمعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> عند جدولة عمليات الفحص لأوقات عدم استخدام نقاط النهاية، لا تحترم عمليات الفحص تكوين تقييد وحدة المعالجة المركزية وستستفيد استفادة كاملة من الموارد المتاحة لإكمال الفحص في أسرع وقت ممكن.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>WMI لجدولة عمليات الفحص لإكمال المعالجة

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

لمزيد من المعلومات والمعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>WMI لجدولة عمليات الفحص اليومية

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ScanScheduleQuickScanTime
```

لمزيد من المعلومات والمعلمات المسموح بها، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)