---
title: جدولة عمليات مسح الفيروسات باستخدام PowerShell
description: جدولة عمليات مسح الفيروسات باستخدام PowerShell
keywords: فحص سريع، فحص كامل، برنامج الحماية من الفيروسات، جدول، PowerShell
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
ms.openlocfilehash: e1cbdd156306d7cc2ee41fd85baadb1fa51cf1ac
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63578263"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>جدولة عمليات مسح الفيروسات باستخدام PowerShell

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

تصف هذه المقالة كيفية تكوين عمليات الفحص المجدولة باستخدام Cmdlets في PowerShell. لمعرفة المزيد حول عمليات الفحص المجدولة وأنواع الفحص، راجع تكوين عمليات المسح السريع أو [برنامج الحماية من الفيروسات من Microsoft Defender الكامل المجدولة](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>استخدام PowerShell cmdlets لجدولة عمليات الفحص

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

لمزيد من المعلومات، راجع [استخدام PowerShell cmdlets لتكوين برنامج الحماية من الفيروسات من Microsoft Defender cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) وتشغيلها للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.[](/powershell/module/defender/)

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>PowerShell cmdlets لجدولة عمليات الفحص عند عدم استخدام نقطة نهاية

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

لمزيد من المعلومات، راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/).

> [!NOTE]
> عند جدولة عمليات الفحص لأزمنة لا تكون فيها نقاط النهاية في وضع الاستخدام، فإن عمليات الفحص لا تشرف تكوين "وحدة المعالجة المركزية(CPU) وستستفيد بشكل كامل من الموارد المتوفرة لإكمال عملية الفحص بأسرع وقت ممكن.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>PowerShell cmdlets لجدولة عمليات الفحص لإكمال المعالجة

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين الأمرين [cmdlets](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus وتشغيلها للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>PowerShell cmdlets لجدولة عمليات الفحص اليومية

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع استخدام [الأمرين cmdlets في PowerShell لتكوين](use-powershell-cmdlets-microsoft-defender-antivirus.md) برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/).
