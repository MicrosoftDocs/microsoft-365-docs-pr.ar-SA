---
title: تطبيق تحديثات حماية Microsoft Defender AV على نقاط النهاية قديمة
description: حدد متى وكيف يجب تطبيق التحديثات لنقاط النهاية التي لم يتم تحديثها منذ فترة.
keywords: التحديثات، الحماية، قديمة، قديمة، اللحاق بالركب
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: c6d8eeb23312f7e4775aacfcadc0d040fc3f0394
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415893"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>إدارة برنامج الحماية من الفيروسات من Microsoft Defender وفحص نقاط النهاية غير المحدثة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يتيح لك برنامج الحماية من الفيروسات من Microsoft Defender تحديد المدة التي يمكن أن تتجنب فيها نقطة النهاية إجراء تحديث أو عدد عمليات الفحص التي قد تفوتها قبل أن تكون مطلوبة لتحديث نفسها وفحصها. وهذا مفيد بشكل خاص في البيئات التي لا تكون فيها الأجهزة متصلة غالبا بشبكة شركة أو شبكة خارجية، أو الأجهزة التي لا تستخدم على أساس يومي.

على سبيل المثال، الموظف الذي يستخدم جهاز كمبيوتر شخصي معين في استراحة لمدة ثلاثة أيام ولا يسجل دخوله إلى جهاز الكمبيوتر الخاص به خلال ذلك الوقت.

عند عودة المستخدم إلى العمل وتسجيل الدخول إلى جهاز الكمبيوتر الخاص به، سيقوم برنامج الحماية من الفيروسات من Microsoft Defender على الفور بالتحقق من آخر تحديثات الحماية وتنزيلها، وتشغيل الفحص.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>إعداد تحديثات حماية اللحاق بالركب لنقاط النهاية التي لم يتم تحديثها لفترة من الوقت

إذا لم يقم برنامج الحماية من الفيروسات من Microsoft Defender بتنزيل تحديثات الحماية لفترة محددة، يمكنك إعداده للتحقق تلقائيا من التحديث الأخير وتنزيله في السجل التالي. يعد هذا الأمر مفيدا إذا قمت [بتعطيل تنزيلات التحديث التلقائية على مستوى العالم عند بدء التشغيل](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>استخدام Configuration Manager لتكوين تحديثات الحماية الإضافية

1. في وحدة التحكم إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره (انقر فوق **الأصول والتوافق** في جزء التنقل على اليسار، ثم قم بتوسيع الشجرة إلى **نظرة عامة** \> **Endpoint Protection** \> **نهج مكافحة البرامج الضارة**)

2. انتقل إلى قسم **تحديثات معلومات الأمان** وقم بتكوين الإعدادات التالية:

    1. قم بتعيين **فرض تحديث معلومات الأمان إذا كان كمبيوتر العميل غير متصل بأكثر من تحديثين مجدولين متتاليين** إلى **"نعم**".
    2. بالنسبة **إلى استخدام Configuration Manager If كمصدر لتحديثات التحليل الذكي للأمان...**، حدد الساعات التي يجب أن تعتبر فيها تحديثات الحماية التي تم تسليمها بواسطة Configuration Manager قديمة. سيؤدي ذلك إلى استخدام موقع التحديث التالي، استنادا إلى [ترتيب المصدر الاحتياطي](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) المحدد.

3. انقر فوق **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>استخدام نهج المجموعة لتمكين ميزة تحديث اللحاق بالركب وتكوينها

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > تحديثات التوقيع**.

5. انقر نقرا **مزدوجا فوق "تعريف عدد الأيام" التي بعدها يلزم إعداد تحديث معلومات الأمان وضبط** الخيار "**ممكن".** أدخل عدد الأيام التي تريد بعدها من Microsoft Defender AV التحقق من وجود آخر تحديث حماية وتنزيله.

6. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>استخدام أوامر Cmdlets PowerShell لتكوين تحديثات الحماية الإضافية

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets لبرنامج الحماية من الفيروسات](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>استخدام تعليمات إدارة Windows (WMI) لتكوين تحديثات الحماية الإضافية

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureUpdateCatchupInterval
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>تعيين عدد الأيام قبل الإبلاغ عن الحماية على أنها قديمة

يمكنك أيضا تحديد عدد الأيام التي تعتبر بعدها الحماية برنامج الحماية من الفيروسات من Microsoft Defender قديمة أو قديمة. بعد عدد الأيام المحدد، سيقوم العميل بالإبلاغ عن نفسه كقيمة قديمة، وإظهار خطأ لمستخدم الكمبيوتر الشخصي. قد يؤدي أيضا برنامج الحماية من الفيروسات من Microsoft Defender إلى محاولة تنزيل تحديث من مصادر أخرى (استنادا إلى [ترتيب المصدر الاحتياطي](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) المحدد)، مثل عند استخدام MMPC كمصدر ثانوي بعد تعيين WSUS أو Microsoft Update كمصدر أول.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>استخدم نهج المجموعة لتحديد عدد الأيام قبل اعتبار الحماية قديمة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

4. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > تحديثات التوقيع** وتكوين الإعدادات التالية:

    1. انقر نقرا مزدوجا فوق **"تعريف عدد الأيام قبل اعتبار تعريفات برامج التجسس قديمة**" وقم بتعيين الخيار "**ممكن".** أدخل عدد الأيام التي تريد بعدها أن يعتبر Microsoft Defender AV معلومات أمان برامج التجسس قديمة.

    2. انقر فوق **موافق**.

    3. انقر نقرا مزدوجا فوق **"تعريف عدد الأيام قبل اعتبار تعريفات الفيروسات قديمة**" وقم بتعيين الخيار "**ممكن".** أدخل عدد الأيام التي تريد أن يعتبر فيها Microsoft Defender AV تحليلا ذكيا لأمان الفيروسات قديما.

    4. انقر فوق **موافق**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>إعداد عمليات فحص اللحاق بالركب لنقاط النهاية التي لم يتم مسحها ضوئيا لفترة من الوقت

يمكنك تعيين عدد عمليات الفحص المجدولة المتتالية التي يمكن تفويتها قبل أن برنامج الحماية من الفيروسات من Microsoft Defender فرض الفحص.

عملية تمكين هذه الميزة هي:

1. إعداد فحص مجدول واحد على الأقل (راجع موضوع [المسح الضوئي للجدول](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).
2. تمكين ميزة فحص اللحاق بالركب.
3. حدد عدد عمليات الفحص التي يمكن تخطيها قبل إجراء فحص اللحاق بالركب.

يمكن تمكين هذه الميزة لكل من عمليات الفحص الكاملة والسريعة.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>استخدام نهج المجموعة لتمكين ميزة الفحص الإلحاقي وتكوينها

1. تأكد من إعداد فحص مجدول واحد على الأقل.

2. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

3. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

4. انقر فوق **"النهج****" ثم "القوالب الإدارية**".

5. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > المسح الضوئي** وتكوين الإعدادات التالية:

    1. إذا قمت بإعداد عمليات فحص سريعة مجدولة، فانقر نقرا مزدوجا **فوق إعداد "تشغيل الفحص السريع للمتابعة**" وقم بتعيين الخيار "**ممكن".**
    2. إذا قمت بإعداد عمليات فحص كاملة مجدولة، فانقر نقرا مزدوجا **فوق إعداد "تشغيل الفحص الكامل للمتابعة**" وقم بتعيين الخيار "**ممكن".** انقر فوق **موافق**.
    3. انقر نقرا **مزدوجا فوق "تعريف عدد الأيام" التي يتم بعدها إعداد الفحص الإلحاقي وتعيين** الخيار "**ممكن".**
    4. أدخل عدد عمليات الفحص التي يمكن تفويتها قبل تشغيل الفحص تلقائيا عندما يسجل المستخدم التالي الدخول إلى الكمبيوتر. يتم تحديد نوع الفحص الذي يتم تشغيله بواسطة **تحديد نوع الفحص لاستخدامه لإجراء فحص مجدول** (راجع موضوع [فحص الجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). انقر فوق **موافق**.

> [!NOTE]
> يشير عنوان إعداد نهج المجموعة إلى عدد الأيام. ومع ذلك، يتم تطبيق الإعداد على عدد عمليات الفحص (وليس الأيام) قبل تشغيل الفحص اللحاق بالركب.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>استخدام أوامر Cmdlets PowerShell لتكوين عمليات الفحص الإلحاقية

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

راجع [استخدام PowerShell cmdlets لإدارة أوامر cmdlets برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) و [Defender Antivirus](/powershell/module/defender/) لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>استخدام Windows Management Instruction (WMI) لتكوين عمليات المسح الضوئي للحاق بالركب

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>استخدام Configuration Manager لتكوين عمليات فحص اللحاق بالركب

1. في وحدة التحكم إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره (انقر فوق **الأصول والتوافق** في جزء التنقل على اليسار، ثم قم بتوسيع الشجرة إلى **نظرة عامة** \> **Endpoint Protection** \> **نهج مكافحة البرامج الضارة**)

2. انتقل إلى قسم **المسح الضوئي المجدول** وفرض **إجراء فحص لنوع الفحص المحدد إذا كان كمبيوتر العميل غير متصل...** إلى **"نعم**".

3. انقر فوق **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
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
- [إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
