---
title: جدولة برنامج الحماية من الفيروسات من Microsoft Defender تحديثات الحماية
description: جدولة اليوم والوقت والوقت الفاصل الزمني للوقت الذي يجب فيه تنزيل تحديثات الحماية
keywords: التحديثات، خطوط الأمان الأساسية، تحديثات الجدولة
ms.prod: m365-security
search.appverid: met150
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: fa67ff12ecfc2fb97bbc50642a5d7db99df91819
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575467"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>إدارة الجدول الزمني عندما يجب تنزيل تحديثات الحماية وتطبيقها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

برنامج الحماية من الفيروسات من Microsoft Defender تحديد وقت البحث عن التحديثات وتنزيلها.

يمكنك جدولة التحديثات لنقاط النهاية عن طريق:

- تحديد يوم الأسبوع للتحقق من تحديثات الحماية
- تحديد الفاصل الزمني للتحقق من تحديثات الحماية
- تحديد الوقت للتحقق من تحديثات الحماية

يمكنك أيضا عشوائيا الأوقات التي تقوم فيها كل نقطة نهاية بالتحقق من تحديثات الحماية وتنزيلها. لمزيد من المعلومات، راجع [الموضوع جدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) عمليات الفحص.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>استخدام "إدارة التكوين" لجدولة تحديثات الحماية

1. على وحدة إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره ( \>  \> انقر فوق الأصول والتوافق في  جزء التنقل على اليمين، ثم قم بتوسيع الشجرة إلى نظرة عامة Endpoint Protection نهج مكافحة البرامج **الضارة**)

2. انتقل إلى **القسم تحديثات معلومات الأمان** .

3. للتحقق من التحديثات وتنزيلها في وقت معين:
      1. تعيين **التحقق من Endpoint Protection معلومات الأمان في فاصل زمني معين...** إلى **0**.
      2. تعيين **التحقق من Endpoint Protection معلومات الأمان يوميا في...** إلى الوقت الذي يجب أن يتم فيه التحقق من التحديثات.
      3
4. للتحقق من التحديثات وتنزيلها على فاصل زمني مستمر، قم بتعيين Endpoint Protection تحديثات معلومات الأمان في فاصل زمني معين **...** إلى عدد الساعات التي يجب أن تحدث بين التحديثات.

5. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>استخدام "نهج المجموعة" لجدولة تحديثات الحماية

> [!IMPORTANT]
> بشكل افتراضي، برنامج الحماية من الفيروسات من Microsoft Defender التحقق من وجود تحديث قبل 15 دقيقة من وقت أي عمليات فحص مجدولة. يؤدي تمكين هذه الإعدادات إلى تجاوز هذا الإعداد الافتراضي.

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة **Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **"** تحديثات معلومات التواقيع" وتكوين الإعدادات التالية:

    1. انقر نقرا مزدوجا فوق الإعداد تحديد يوم **من الأسبوع للتحقق من وجود تحديثات لذكاء** الأمان، ثم قم بتعيين الخيار إلى **تمكين**. أدخل يوم الأسبوع للتحقق من وجود تحديثات. انقر فوق **موافق**.
    2. انقر نقرا مزدوجا فوق **الإعداد تحديد الفاصل الزمني للتحقق** من تحديثات معلومات الأمان، ثم قم بتعيين الخيار **إلى تمكين**. أدخل عدد الساعات بين التحديثات. انقر فوق **موافق**.
    3. انقر نقرا مزدوجا **فوق الإعداد تحديد الوقت للتحقق من** تحديثات معلومات الأمان، ثم قم بتعيين الخيار **إلى تمكين**. أدخل الوقت الذي يجب أن يتم فيه التحقق من التحديثات. يستند الوقت إلى الوقت المحلي لنقطة النهاية. انقر فوق **موافق**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>استخدام PowerShell cmdlets لجدولة تحديثات الحماية

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين الأمرين [cmdlets](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus وتشغيلها للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>استخدام Windows الإدارة (WMI) لجدولة تحديثات الحماية

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="related-articles"></a>المقالات ذات الصلة

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيقها](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
