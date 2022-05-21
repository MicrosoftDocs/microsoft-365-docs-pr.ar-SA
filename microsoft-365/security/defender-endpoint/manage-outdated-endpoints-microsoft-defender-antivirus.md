---
title: تطبيق تحديثات حماية برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية غير المحدثة
description: حدد متى وكيف يجب تطبيق التحديثات على نقاط النهاية التي لم يتم تحديثها منذ فترة.
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
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: fcf13258b8012bfd2a5875b52b8d844040aee73e
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623487"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>إدارة برنامج الحماية من الفيروسات من Microsoft Defender وفحص نقاط النهاية غير المحدثة

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**

- بالنسبة لنظام التشغيل

باستخدام برنامج الحماية من الفيروسات من Microsoft Defender، يمكن لفريق الأمان تحديد المدة التي يمكن أن تتجنب فيها نقطة النهاية التحديث أو عدد عمليات الفحص التي قد تفوتها قبل أن يطلب منها تلقي التحديث وتشغيل الفحص. هذه الإمكانية مفيدة بشكل خاص في البيئات التي لا تكون فيها الأجهزة غالبا متصلة بشركة أو شبكة خارجية، أو للأجهزة التي لا تستخدم على أساس يومي.

على سبيل المثال، الموظف الذي يستخدم كمبيوتر معين يأخذ ثلاثة أيام من العمل، ولا يقوم بتسجيل الدخول على الكمبيوتر الخاص به خلال ذلك الوقت. عندما يعود الموظف إلى العمل ويسجل دخوله إلى جهاز الكمبيوتر الخاص به، سيقوم برنامج الحماية من الفيروسات من Microsoft Defender على الفور بالتحقق من آخر تحديثات الحماية وتنزيلها، ثم إجراء فحص.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>إعداد تحديثات حماية اللحاق بالركب لنقاط النهاية التي لم يتم تحديثها لفترة من الوقت

إذا لم تقم برنامج الحماية من الفيروسات من Microsoft Defender بتنزيل تحديثات الحماية لفترة محددة، يمكنك إعدادها للتحقق من التحديث الأخير وتنزيله تلقائيا في المرة التالية التي يقوم فيها شخص ما بتسجيل الدخول إلى نقطة نهاية. يعد هذا التكوين مفيدا إذا قمت [بتعطيل تنزيلات التحديث التلقائية على مستوى العالم عند بدء التشغيل](manage-event-based-updates-microsoft-defender-antivirus.md).

يمكنك استخدام أحد الأساليب المتعددة لإعداد تحديثات حماية اللحاق بالركب:

- [إدارة التكوين](#use-configuration-manager-to-configure-catch-up-protection-updates)
- [نهج المجموعة](#use-group-policy-to-enable-and-configure-the-catch-up-update-feature)
- [PowerShell cmdlets](#use-powershell-cmdlets-to-configure-catch-up-protection-updates)
- [تعليمات إدارة Windows (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates)

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>استخدام Configuration Manager لتكوين تحديثات الحماية الإضافية

1. في وحدة التحكم إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره (حدد **الأصول والتوافق** في جزء التنقل على اليسار، ثم قم بتوسيع الشجرة إلى **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. انتقل إلى قسم **تحديثات معلومات الأمان** وقم بتكوين الإعدادات التالية:

    - قم بتعيين **فرض تحديث معلومات الأمان إذا كان كمبيوتر العميل غير متصل بأكثر من تحديثين مجدولين متتاليين** إلى **"نعم**".
    - بالنسبة **Configuration Manager If المستخدمة كمصدر لتحديثات معلومات الأمان...**، حدد الساعات التي يجب أن يتم فيها اعتبار تحديثات الحماية التي تم تسليمها بواسطة Configuration Manager قديمة. يؤدي هذا الإعداد إلى استخدام موقع التحديث التالي، استنادا إلى [ترتيب المصدر الاحتياطي](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) المحدد.

3. حدد **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>استخدام نهج المجموعة لتمكين ميزة تحديث اللحاق بالركب وتكوينها

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق عنصر نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. حدد **النهج** ثم **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > تحديثات التوقيع**.

5. انقر نقرا **مزدوجا فوق "تعريف عدد الأيام" التي بعدها يلزم إعداد تحديث معلومات الأمان وضبط** الخيار "**ممكن".** أدخل عدد الأيام التي تريد برنامج الحماية من الفيروسات من Microsoft Defender بعدها التحقق من وجود آخر تحديث حماية وتنزيله.

6. حدد **موافق**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>استخدام أوامر Cmdlets PowerShell لتكوين تحديثات الحماية الإضافية

استخدم cmdlet التالي:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

لمزيد من المعلومات حول استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع المقالات التالية:

- [استخدم أوامر cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [أوامر cmdlets الخاصة بالحماية من الفيروسات ل Defender](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>استخدام تعليمات إدارة Windows (WMI) لتكوين تحديثات الحماية الإضافية

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureUpdateCatchupInterval
```

راجع المقالة التالية لمزيد من المعلومات والمعلمات المسموح بها:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>تعيين عدد الأيام قبل الإبلاغ عن الحماية على أنها قديمة

يمكنك أيضا تحديد عدد الأيام التي تعتبر بعدها الحماية برنامج الحماية من الفيروسات من Microsoft Defender قديمة أو قديمة. بعد عدد الأيام المحدد، سيقوم العميل بالإبلاغ عن نفسه على أنه "قديم" وسيعرض خطأ لمستخدم نقطة النهاية. عند اعتبار نقطة نهاية قديمة، قد يحاول برنامج الحماية من الفيروسات من Microsoft Defender تنزيل تحديث من مصادر أخرى (استنادا إلى [ترتيب المصدر الاحتياطي](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order) المحدد).

يمكنك استخدام نهج المجموعة لتحديد عدد الأيام التي تعتبر بعدها حماية نقطة النهاية قديمة.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>استخدم نهج المجموعة لتحديد عدد الأيام قبل اعتبار الحماية قديمة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. حدد **النهج** ثم **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > تحديثات التوقيع** وتكوين الإعدادات التالية:

    1. انقر نقرا مزدوجا فوق **"تعريف عدد الأيام قبل اعتبار تعريفات برامج التجسس قديمة**" وقم بتعيين الخيار "**ممكن".** أدخل عدد الأيام التي تريد برنامج الحماية من الفيروسات من Microsoft Defender بعدها اعتبار معلومات أمان برامج التجسس قديمة.

    2. حدد **موافق**.

    3. انقر نقرا مزدوجا فوق **"تعريف عدد الأيام قبل اعتبار تعريفات الفيروسات قديمة**" وقم بتعيين الخيار "**ممكن".** أدخل عدد الأيام التي تريد برنامج الحماية من الفيروسات من Microsoft Defender بعدها اعتبار تحليل معلومات أمان الفيروسات قديما.

    4. حدد **موافق**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>إعداد عمليات فحص اللحاق بالركب لنقاط النهاية التي لم يتم مسحها ضوئيا لفترة من الوقت

يمكنك تعيين عدد عمليات الفحص المجدولة المتتالية التي يمكن تفويتها قبل أن برنامج الحماية من الفيروسات من Microsoft Defender فرض الفحص.

عملية تمكين هذه الميزة هي:

1. إعداد فحص مجدول واحد على الأقل (راجع مقالة [المسح الضوئي المجدول](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).

2. تمكين ميزة فحص اللحاق بالركب.

3. حدد عدد عمليات الفحص التي يمكن تخطيها قبل إجراء فحص اللحاق بالركب.

يمكن تمكين هذه الميزة لكل من عمليات الفحص الكاملة والسريعة. 

> [!TIP]
> نوصي باستخدام عمليات المسح السريع لمعظم الحالات. لمعرفة المزيد، راجع [الفحص السريع والمسح الضوئي الكامل والمسح الضوئي المخصص](schedule-antivirus-scans.md#quick-scan-full-scan-and-custom-scan). 

يمكنك استخدام إحدى الطرق المتعددة لإعداد عمليات الفحص الإلحاقية:

- [نهج المجموعة](#use-group-policy-to-enable-and-configure-the-catch-up-scan-feature)
- [استخدام أوامر Cmdlets PowerShell لتكوين عمليات الفحص الإلحاقية](#use-powershell-cmdlets-to-configure-catch-up-scans)
- [تعليمات إدارة Windows (WMI)](#use-windows-management-instruction-wmi-to-configure-catch-up-scans)
- [إدارة التكوين](#use-configuration-manager-to-configure-catch-up-scans)

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>استخدام نهج المجموعة لتمكين ميزة الفحص الإلحاقي وتكوينها

1. تأكد من إعداد فحص مجدول واحد على الأقل.

2. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

3. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

4. حدد **النهج** ثم **القوالب الإدارية**.

5. قم بتوسيع الشجرة إلى **مكونات Windows > برنامج الحماية من الفيروسات من Microsoft Defender > المسح الضوئي** وتكوين الإعدادات التالية:

    - إذا قمت بإعداد عمليات فحص سريعة مجدولة، فانقر نقرا مزدوجا **فوق إعداد "تشغيل الفحص السريع للمتابعة**" وقم بتعيين الخيار "**ممكن".**
    - إذا قمت بإعداد عمليات فحص كاملة مجدولة، فانقر نقرا مزدوجا **فوق إعداد "تشغيل الفحص الكامل للمتابعة**" وقم بتعيين الخيار "**ممكن".** حدد **موافق**.
    - انقر نقرا **مزدوجا فوق "تعريف عدد الأيام" التي يتم بعدها إعداد الفحص الإلحاقي وتعيين** الخيار "**ممكن".**
    - أدخل عدد عمليات الفحص التي يمكن تفويتها قبل تشغيل الفحص تلقائيا عندما يقوم المستخدم التالي بتسجيل الدخول على نقطة النهاية. يتم تحديد نوع الفحص الذي يتم تشغيله بواسطة **تحديد نوع الفحص لاستخدامه لإجراء فحص مجدول** (راجع [مقالة فحص الجدول](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ). حدد **موافق**.

> [!NOTE]
> يشير عنوان إعداد نهج المجموعة إلى عدد الأيام. ومع ذلك، يتم تطبيق الإعداد على عدد عمليات الفحص (وليس الأيام) قبل تشغيل الفحص اللحاق بالركب.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>استخدام أوامر Cmdlets PowerShell لتكوين عمليات الفحص الإلحاقية

استخدم أوامر cmdlet التالية:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

لمزيد من المعلومات حول استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع المقالات التالية:

- [استخدم PowerShell cmdlets لإدارة برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) 
- [أوامر cmdlets الخاصة بالحماية من الفيروسات ل Defender](/powershell/module/defender/)

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>استخدام Windows Management Instruction (WMI) لتكوين عمليات المسح الضوئي للحاق بالركب

استخدم [أسلوب **Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

راجع المقالة التالية لمزيد من المعلومات والمعلمات المسموح بها:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>استخدام Configuration Manager لتكوين عمليات فحص اللحاق بالركب

1. في وحدة التحكم إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره (حدد **الأصول والتوافق** في جزء التنقل على اليسار، ثم قم بتوسيع الشجرة إلى **Overview** \> **Endpoint Protection** \> **Antimalware Policies**)

2. انتقل إلى قسم **المسح الضوئي المجدول** وفرض **إجراء فحص لنوع الفحص المحدد إذا كان كمبيوتر العميل غير متصل...** إلى **"نعم**".

3. حدد **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
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
