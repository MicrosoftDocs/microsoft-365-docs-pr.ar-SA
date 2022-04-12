---
title: جدولة عمليات فحص مكافحة الفيروسات باستخدام PowerShell
description: جدولة عمليات فحص مكافحة الفيروسات باستخدام PowerShell
keywords: المسح الضوئي السريع، الفحص الكامل، مكافحة الفيروسات، الجدول الزمني، PowerShell
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
ms.openlocfilehash: 8961428acee5d166b0cdad4982aa5f9ed48020af
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788821"
---
# <a name="schedule-antivirus-scans-using-powershell"></a>جدولة عمليات فحص مكافحة الفيروسات باستخدام PowerShell

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

تصف هذه المقالة كيفية تكوين عمليات الفحص المجدولة باستخدام PowerShell cmdlets. لمعرفة المزيد حول جدولة عمليات الفحص وأنواع الفحص، راجع [تكوين عمليات الفحص السريعة أو الكاملة المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](schedule-antivirus-scans.md). 

## <a name="use-powershell-cmdlets-to-schedule-scans"></a>استخدام PowerShell cmdlets لجدولة عمليات الفحص

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -ScanParameters
Set-MpPreference -ScanScheduleDay
Set-MpPreference -ScanScheduleTime
Set-MpPreference -RandomizeScheduleTaskTimes

```

لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus](/powershell/module/defender/) لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-scans-when-an-endpoint-is-not-in-use"></a>PowerShell cmdlets لجدولة عمليات الفحص عندما لا تكون نقطة النهاية قيد الاستخدام

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -ScanOnlyIfIdleEnabled
```

لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) [وSmdlets لبرنامج الحماية من الفيروسات من Defender](/powershell/module/defender/).

> [!NOTE]
> عند جدولة عمليات الفحص لأوقات عدم استخدام نقاط النهاية، لا تحترم عمليات الفحص تكوين تقييد وحدة المعالجة المركزية وستستفيد استفادة كاملة من الموارد المتاحة لإكمال الفحص في أسرع وقت ممكن.

## <a name="powershell-cmdlets-for-scheduling-scans-to-complete-remediation"></a>PowerShell cmdlets لجدولة عمليات الفحص لإكمال المعالجة

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -RemediationScheduleDay
Set-MpPreference -RemediationScheduleTime
```

راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets لبرنامج الحماية من الفيروسات](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="powershell-cmdlets-for-scheduling-daily-scans"></a>PowerShell cmdlets لجدولة عمليات الفحص اليومية

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -ScanScheduleQuickScanTime
```

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع [استخدام PowerShell cmdlets لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus](/powershell/module/defender/).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)