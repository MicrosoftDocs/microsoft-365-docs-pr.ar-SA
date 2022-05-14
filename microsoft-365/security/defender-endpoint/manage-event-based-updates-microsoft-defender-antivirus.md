---
title: تطبيق تحديثات برنامج الحماية من الفيروسات من Microsoft Defender بعد أحداث معينة
description: إدارة كيفية تطبيق برنامج الحماية من الفيروسات من Microsoft Defender تحديثات التحليل الذكي للأمان بعد بدء تشغيل تقارير الكشف التي يتم تسليمها من السحابة أو تلقيها.
keywords: التحديثات والحماية وفرض التحديثات والأحداث والبدء والتحقق من الأحدث والإعلامات
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/17/2018
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 813dfe410a3e6cf198d6d4a36afd6d2987f6d376
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415585"
---
# <a name="manage-event-based-forced-updates"></a>إدارة التحديثات التلقائية المستندة إلى الحدث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يسمح لك برنامج الحماية من الفيروسات من Microsoft Defender بتحديد ما إذا كان يجب (أو لا) إجراء التحديثات بعد أحداث معينة، مثل عند بدء التشغيل أو بعد تلقي تقارير محددة من خدمة الحماية المقدمة من السحابة.

## <a name="check-for-protection-updates-before-running-a-scan"></a>التحقق من تحديثات الحماية قبل تشغيل الفحص

يمكنك استخدام Microsoft Endpoint Configuration Manager نهج المجموعة وPowerShell cmdlets وWMI لإجبار برنامج الحماية من الفيروسات من Microsoft Defender على التحقق من تحديثات الحماية وتنزيلها قبل تشغيل فحص مجدول.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>استخدام Configuration Manager للتحقق من تحديثات الحماية قبل تشغيل الفحص

1. في وحدة التحكم إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره (انقر فوق **الأصول والتوافق** في جزء التنقل على اليسار، ثم قم بتوسيع الشجرة إلى **نظرة عامة** \> **Endpoint Protection** \> **نهج مكافحة البرامج الضارة**)

2. انتقل إلى قسم **"المسح الضوئي المجدول** " وقم بتعيين **"Check for the latest security intelligence updates" قبل تشغيل الفحص** إلى **"Yes**".

3. انقر فوق **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>استخدام نهج المجموعة للتحقق من تحديثات الحماية قبل تشغيل الفحص

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **المسح الضوئي**.

5. انقر نقرا **مزدوجا فوق "التحقق من أحدث تعريفات الفيروسات وبرامج التجسس" قبل تشغيل فحص مجدول** وتعيين الخيار "**ممكن".**

6. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>استخدام PowerShell cmdlets للتحقق من تحديثات الحماية قبل تشغيل الفحص

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) [وSmdlets لبرنامج الحماية من الفيروسات من Defender](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>استخدام Windows Management Instruction (WMI) للتحقق من وجود تحديثات الحماية قبل تشغيل الفحص

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
CheckForSignaturesBeforeRunningScan
```

لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>التحقق من تحديثات الحماية عند بدء التشغيل

يمكنك استخدام نهج المجموعة لإجبار برنامج الحماية من الفيروسات من Microsoft Defender على التحقق من تحديثات الحماية وتنزيلها عند بدء تشغيل الجهاز.

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تحديثات معلومات الأمان**.

5. انقر نقرا مزدوجا فوق **"التحقق من وجود أحدث تعريفات الفيروسات وبرامج التجسس عند بدء التشغيل** " وحدد الخيار " **ممكن**".

6. انقر فوق **موافق**.

يمكنك أيضا استخدام نهج المجموعة أو PowerShell أو WMI لتكوين برنامج الحماية من الفيروسات من Microsoft Defender للتحقق من وجود تحديثات عند بدء التشغيل حتى عندما لا يكون قيد التشغيل.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>استخدام نهج المجموعة لتنزيل التحديثات عندما لا يكون برنامج الحماية من الفيروسات من Microsoft Defender موجودا

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تحديثات معلومات الأمان**.

5. انقر نقرا مزدوجا فوق **بدء تحديث معلومات الأمان عند بدء التشغيل** وتعيين الخيار إلى **ممكن**.

6. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>استخدام PowerShell cmdlets لتنزيل التحديثات عندما لا يكون برنامج الحماية من الفيروسات من Microsoft Defender موجودا

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

لمزيد من المعلومات، راجع [استخدام PowerShell cmdlets لإدارة أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus](/powershell/module/defender/index) لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>استخدام تعليمات إدارة Windows (WMI) لتنزيل التحديثات عندما لا يكون برنامج الحماية من الفيروسات من Microsoft Defender موجودا

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>السماح بإجراء تغييرات مخصصة على الحماية استنادا إلى الحماية المقدمة من السحابة

يمكن ل Microsoft Defender AV إجراء تغييرات على حمايته استنادا إلى الحماية المقدمة من السحابة. يمكن أن تحدث مثل هذه التغييرات خارج تحديثات الحماية العادية أو المجدولة.

إذا قمت بتمكين الحماية المقدمة من السحابة، فسيرسل Microsoft Defender AV ملفات مريبة حولها إلى سحابة Windows Defender. إذا كانت خدمة السحابة تشير إلى أن الملف ضار، وتم الكشف عن الملف في تحديث حماية حديث، يمكنك استخدام نهج المجموعة لتكوين Microsoft Defender AV لتلقي تحديث الحماية هذا تلقائيا. يمكن أيضا تطبيق تحديثات حماية مهمة أخرى.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>استخدم نهج المجموعة لتنزيل التحديثات الأخيرة تلقائيا استنادا إلى الحماية المقدمة من السحابة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **تحديثات معلومات الأمان**.

5. انقر نقرا مزدوجا فوق **السماح بتحديثات التحليل الذكي للأمان في الوقت الحقيقي استنادا إلى التقارير إلى Microsoft MAPS** وتعيين الخيار "**ممكن".** ثم انقر فوق **"موافق**".

6. **السماح للإعلامات بتعطيل التقارير المستندة إلى التعريفات إلى Microsoft MAPS** وتعيين الخيار إلى **ممكن**. ثم انقر فوق **"موافق**".

> [!NOTE]
> **يتيح السماح للإعلامات بتعطيل التقارير المستندة إلى التعريفات** ل Microsoft MAPS تعطيل تلك التعريفات المعروفة بتسببها في تقارير إيجابية خاطئة. يجب تكوين الكمبيوتر للانضمام إلى Microsoft MAPS لكي تعمل هذه الدالة.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
