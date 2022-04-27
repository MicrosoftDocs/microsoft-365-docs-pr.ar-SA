---
title: جدولة تحديثات حماية برنامج الحماية من الفيروسات من Microsoft Defender
description: جدولة اليوم والوقت والفاصل الزمني لوقت تنزيل تحديثات الحماية
keywords: التحديثات، وخطوط الأمان الأساسية، وجدولة التحديثات
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
ms.openlocfilehash: 1624cec49b6c1e242be7fd1120ef87bdf05a5af7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091644"
---
# <a name="manage-the-schedule-for-when-protection-updates-should-be-downloaded-and-applied"></a>إدارة الجدول الزمني عندما يجب تنزيل تحديثات الحماية وتطبيقها

> [!IMPORTANT]
> قد يكون العملاء الذين طبقوا تحديث محرك Microsoft Defender مارس 2022 (**1.1.19100.5**) قد واجهوا استخداما عاليا للموارد (وحدة المعالجة المركزية و/أو الذاكرة). أصدرت Microsoft تحديثا (**1.1.19200.5**) يحل الأخطاء التي تم تقديمها في الإصدار السابق. يوصى للعملاء بالتحديث إلى هذا الإصدار الجديد من محرك الحماية من الفيروسات (**1.1.19200.5**). لضمان إصلاح أي مشكلات في الأداء بشكل كامل، يوصى بإعادة تشغيل الأجهزة بعد تطبيق التحديث. لمزيد من المعلومات، راجع [إصدارات النظام الأساسي والمحرك الشهرية](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يتيح لك برنامج الحماية من الفيروسات من Microsoft Defender تحديد الوقت الذي يجب أن يبحث فيه عن التحديثات وينزلها.

يمكنك جدولة التحديثات لنقاط النهاية عن طريق:

- تحديد يوم الأسبوع للتحقق من وجود تحديثات الحماية
- تحديد الفاصل الزمني للتحقق من تحديثات الحماية
- تحديد الوقت للتحقق من تحديثات الحماية

يمكنك أيضا إضفاء الطابع العشوائي على الأوقات التي تتحقق فيها كل نقطة نهاية من تحديثات الحماية وتنزلها. راجع موضوع [فحص الجدول](scheduled-catch-up-scans-microsoft-defender-antivirus.md) للحصول على مزيد من المعلومات.

## <a name="use-configuration-manager-to-schedule-protection-updates"></a>استخدام Configuration Manager لجدولة تحديثات الحماية

1. في وحدة التحكم إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره (انقر فوق **الأصول والتوافق** في جزء التنقل على اليسار، ثم قم بتوسيع الشجرة إلى **نظرة عامة** \> **Endpoint Protection** \> **نهج مكافحة البرامج الضارة**)

2. انتقل إلى قسم **تحديثات معلومات الأمان** .

3. للتحقق من التحديثات وتنزيلها في وقت معين:
      1. تعيين **Check for Endpoint Protection security intelligence updates at a specific interval...** to **0**.
      2. قم بتعيين **Check for Endpoint Protection security intelligence updates يوميا في...** إلى الوقت الذي يجب فيه التحقق من التحديثات.
      3
4. للتحقق من التحديثات وتنزيلها على فاصل زمني مستمر، قم بتعيين **التحقق من Endpoint Protection تحديثات التحليل الذكي للأمان في فاصل زمني معين...** إلى عدد الساعات التي يجب أن تحدث بين التحديثات.

5. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="use-group-policy-to-schedule-protection-updates"></a>استخدام نهج المجموعة لجدولة تحديثات الحماية

> [!IMPORTANT]
> بشكل افتراضي، يتم تعيين "SignatureScheduleDay" ك "8" ويتم تعيين "SignatureUpdateInterval" ك "0" لذلك لن يقوم برنامج الحماية من الفيروسات من Microsoft Defender بجدولة تحديثات الحماية.
سيؤدي تمكين هذه الإعدادات إلى تجاوز هذا الإعداد الافتراضي.

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تحديثات التحليل الذكي للتوقيع** وتكوين الإعدادات التالية:

    1. انقر نقرا مزدوجا فوق **"تحديد يوم الأسبوع" للتحقق من إعداد تحديثات معلومات الأمان** وتعيين الخيار "**ممكن".** أدخل يوم الأسبوع للتحقق من وجود تحديثات. انقر فوق **موافق**.
    2. انقر نقرا مزدوجا فوق **"تحديد الفاصل الزمني" للتحقق من إعداد تحديثات معلومات الأمان** وتعيين الخيار "**ممكن".** أدخل عدد الساعات بين التحديثات. انقر فوق **موافق**.
    3. انقر نقرا مزدوجا فوق **"تحديد الوقت" للتحقق من إعداد تحديثات معلومات الأمان** وتعيين الخيار "**ممكن".** أدخل الوقت الذي يجب فيه التحقق من التحديثات. يستند الوقت إلى الوقت المحلي لنقطة النهاية. انقر فوق **موافق**.

## <a name="use-powershell-cmdlets-to-schedule-protection-updates"></a>استخدام PowerShell cmdlets لجدولة تحديثات الحماية

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -SignatureScheduleDay
Set-MpPreference -SignatureScheduleTime
Set-MpPreference -SignatureUpdateInterval
```

راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets لبرنامج الحماية من الفيروسات](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="use-windows-management-instruction-wmi-to-schedule-protection-updates"></a>استخدام تعليمات إدارة Windows (WMI) لجدولة تحديثات الحماية

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureScheduleDay
SignatureScheduleTime
SignatureUpdateInterval
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

> [!TIP]
> إذا كنت’ تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
