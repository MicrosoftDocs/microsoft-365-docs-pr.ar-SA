---
title: تطبيق برنامج الحماية من الفيروسات من Microsoft Defender التحديثات بعد أحداث معينة
description: إدارة كيفية برنامج الحماية من الفيروسات من Microsoft Defender تحديثات معلومات الأمان بعد بدء التشغيل أو تلقي تقارير الكشف التي يتم تسليمها من السحابة.
keywords: التحديثات والحماية، فرض التحديثات، الأحداث، بدء التشغيل، التحقق من وجود آخر، الإعلامات
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
ms.openlocfilehash: c99e4e085de32ac4e7ec77a2155182f1a930d432
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63575468"
---
# <a name="manage-event-based-forced-updates"></a>إدارة التحديثات التلقائية المستندة إلى الحدث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

برنامج الحماية من الفيروسات من Microsoft Defender تحديد ما إذا كان يجب (أو لا يجب) أن تحدث التحديثات بعد أحداث معينة، مثل عند بدء التشغيل أو بعد تلقي تقارير معينة من خدمة الحماية التي يتم تسليمها من السحابة.

## <a name="check-for-protection-updates-before-running-a-scan"></a>التحقق من تحديثات الحماية قبل تشغيل الفحص

يمكنك استخدام Microsoft Endpoint Configuration Manager ونهاية المجموعة و PowerShell cmdlets و WMI لجبر برنامج الحماية من الفيروسات من Microsoft Defender على التحقق من تحديثات الحماية وتنزيلها قبل تشغيل عملية فحص مجدولة.

### <a name="use-configuration-manager-to-check-for-protection-updates-before-running-a-scan"></a>استخدام "إدارة التكوين" للتحقق من وجود تحديثات الحماية قبل تشغيل الفحص

1. على وحدة إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره ( \>  \> انقر فوق الأصول والتوافق في  جزء التنقل على اليمين، ثم قم بتوسيع الشجرة إلى نظرة عامة Endpoint Protection نهج مكافحة البرامج **الضارة**)

2. انتقل إلى **المقطع عمليات الفحص المجدولة** وحدد التحقق من وجود آخر تحديثات معلومات الأمان **قبل تشغيل** عملية فحص إلى **نعم**.

3. انقر فوق **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-check-for-protection-updates-before-running-a-scan"></a>استخدام "نهج المجموعة" للتحقق من وجود تحديثات الحماية قبل تشغيل الفحص

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **المسح الضوئي**.

5. انقر نقرا **مزدوجا فوق التحقق من أحدث تعريفات** الفيروسات وبرامج التجسس قبل تشغيل فحص مجدول، ثم قم بتعيين الخيار إلى **تمكين**.

6. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-check-for-protection-updates-before-running-a-scan"></a>استخدام PowerShell cmdlets للتحقق من وجود تحديثات الحماية قبل تشغيل الفحص

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -CheckForSignaturesBeforeRunningScan
```

لمزيد من المعلومات، راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/index).

### <a name="use-windows-management-instruction-wmi-to-check-for-protection-updates-before-running-a-scan"></a>استخدام Windows إدارة البيانات (WMI) للتحقق من وجود تحديثات الحماية قبل تشغيل الفحص

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
CheckForSignaturesBeforeRunningScan
```

لمزيد من المعلومات، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="check-for-protection-updates-on-startup"></a>التحقق من تحديثات الحماية عند بدء التشغيل

يمكنك استخدام "نهج المجموعة" برنامج الحماية من الفيروسات من Microsoft Defender التحقق من تحديثات الحماية وتنزيلها عند بدء تشغيل الجهاز.

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **معلومات الأمان**.

5. انقر نقرا **مزدوجا فوق التحقق من أحدث تعريفات** الفيروسات وبرامج التجسس عند بدء التشغيل، ثم قم بتعيين الخيار **إلى تمكين**.

6. انقر فوق **موافق**.

يمكنك أيضا استخدام نهج المجموعة أو PowerShell أو WMI لتكوين برنامج الحماية من الفيروسات من Microsoft Defender للتحقق من وجود تحديثات عند بدء التشغيل حتى عندما لا يكون قيد التشغيل.

### <a name="use-group-policy-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>استخدام "نهج المجموعة" لتنزيل التحديثات برنامج الحماية من الفيروسات من Microsoft Defender تكون غير موجودة

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **معلومات الأمان**.

5. انقر نقرا **مزدوجا فوق بدء تحديث معلومات الأمان عند** بدء التشغيل، ثم قم بتعيين الخيار **إلى تمكين**.

6. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>استخدام PowerShell cmdlets لتنزيل التحديثات عندما برنامج الحماية من الفيروسات من Microsoft Defender تكون موجودة

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -SignatureDisableUpdateOnStartupWithoutEngine
```

لمزيد من المعلومات، راجع استخدام [powerShell cmdlets لإدارة برنامج الحماية من الفيروسات من Microsoft Defender cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) و Defender [Antivirus](/powershell/module/defender/index) للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-download-updates-when-microsoft-defender-antivirus-is-not-present"></a>استخدام Windows الإدارة (WMI) لتنزيل التحديثات عندما برنامج الحماية من الفيروسات من Microsoft Defender تكون غير موجودة

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureDisableUpdateOnStartupWithoutEngine
```

لمزيد من المعلومات، راجع Windows [واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

<a id="cloud-report-updates"></a>

## <a name="allow-ad-hoc-changes-to-protection-based-on-cloud-delivered-protection"></a>السماح بإجراء تغييرات مخصصة على الحماية استنادا إلى الحماية التي يتم تسليمها من السحابة

يمكن ل Microsoft Defender AV إجراء تغييرات على حمايته استنادا إلى الحماية التي يتم تسليمها من السحابة. قد تحدث مثل هذه التغييرات خارج تحديثات الحماية العادية أو المجدولة.

إذا قمت بتمكين الحماية التي يتم تسليمها عبر السحابة، سيرسل Microsoft Defender AV ملفات مريبة إلى Windows Defender. إذا كانت الخدمة السحابية تعلم بأن الملف ضار، والكشف عن الملف في تحديث حماية حديث، يمكنك استخدام "نهج المجموعة" لتكوين Microsoft Defender AV لتلقي تحديث الحماية هذا تلقائيا. يمكن أيضا تطبيق تحديثات الحماية الهامة الأخرى.

### <a name="use-group-policy-to-automatically-download-recent-updates-based-on-cloud-delivered-protection"></a>استخدام "نهج المجموعة" لتنزيل التحديثات الأخيرة تلقائيا استنادا إلى الحماية التي يتم تسليمها من السحابة

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **معلومات الأمان**.

5. انقر نقرا **مزدوجا فوق السماح بتحديثات** معلومات الأمان في الوقت الحقيقي استنادا إلى التقارير إلى Microsoft MAPS، ثم قم بتعيين الخيار **إلى تمكين**. ثم انقر فوق **موافق**.

6. **اسمح الإعلامات بتعطيل التقارير المستندة إلى التعريفات إلى Microsoft MAPS** ، ثم قم بتعيين الخيار **إلى تمكين**. ثم انقر فوق **موافق**.

> [!NOTE]
> **السماح الإعلامات بتعطيل التقارير المستندة** إلى التعريفات تمكن Microsoft MAPS من تعطيل تلك التعريفات المعروفة بالتسبب في تقارير إيجابية خاطئة. يجب تكوين الكمبيوتر للانضمام إلى Microsoft MAPS لكي تعمل هذه الدالة.

## <a name="see-also"></a>راجع أيضًا

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيقها](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
