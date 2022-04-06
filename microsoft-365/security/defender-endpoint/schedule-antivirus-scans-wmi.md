---
title: جدولة عمليات فحص الحماية من الفيروسات Windows أدوات الإدارة
description: جدولة عمليات مسح الفيروسات باستخدام WMI
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
ms.openlocfilehash: be22e59f6d2be30ead354099f2cc168868959752
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63583309"
---
# <a name="schedule-antivirus-scans-using-windows-management-instrumentation-wmi"></a>جدولة عمليات فحص الفيروسات Windows إدارة الأجهزة (WMI)

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

تصف هذه المقالة كيفية تكوين عمليات الفحص المجدولة باستخدام WMI. لمعرفة المزيد حول عمليات الفحص المجدولة وأنواع الفحص، راجع تكوين عمليات المسح السريع أو [برنامج الحماية من الفيروسات من Microsoft Defender الكامل المجدولة](schedule-antivirus-scans.md). 

## <a name="use-windows-management-instruction-wmi-to-schedule-scans"></a>استخدام Windows إدارة البيانات (WMI) لجدولة عمليات الفحص

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ScanParameters
ScanScheduleDay
ScanScheduleTime
RandomizeScheduleTaskTimes
```

لمزيد من المعلومات والمعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="wmi-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>WMI لجدولة عمليات الفحص عند عدم استخدام نقطة نهاية

استخدم [الأسلوب Set للفئة MSFT_MpPreference للخصائص](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) التالية:

```WMI
ScanOnlyIfIdleEnabled
```

لمزيد من المعلومات حول واجهات برمجة التطبيقات والمعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

> [!NOTE]
> عند جدولة عمليات الفحص لأزمنة لا تكون فيها نقاط النهاية في وضع الاستخدام، فإن عمليات الفحص لا تشرف تكوين "وحدة المعالجة المركزية(CPU) وستستفيد بشكل كامل من الموارد المتوفرة لإكمال عملية الفحص بأسرع وقت ممكن.


## <a name="wmi-for-scheduling-scans-to-complete-remediation"></a>WMI لجدولة عمليات الفحص لإكمال المعالجة

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
RemediationScheduleDay
RemediationScheduleTime
```

لمزيد من المعلومات والمعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="wmi-for-scheduling-daily-scans"></a>WMI لجدولة عمليات الفحص اليومية

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
ScanScheduleQuickScanTime
```

لمزيد من المعلومات والمعلمات المسموح بها، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

