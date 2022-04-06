---
title: تطبيق تحديثات الحماية من AV ل Microsoft Defender على نقاط النهاية غير المحدثة
description: تحديد وقت وكيفية تطبيق التحديثات لنقاط النهاية التي لم يتم تحديثها منذ فترة قصيرة.
keywords: التحديثات والحماية وغير المحدثة أو القديمة أو القديمة أو المتابعة
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
ms.openlocfilehash: a708bf6ef34767b338c40cf8004e4c497658fc36
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63583229"
---
# <a name="manage-microsoft-defender-antivirus-updates-and-scans-for-endpoints-that-are-out-of-date"></a>إدارة برنامج الحماية من الفيروسات من Microsoft Defender وفحص نقاط النهاية غير المحدثة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

برنامج الحماية من الفيروسات من Microsoft Defender تحديد المدة التي يمكن أن تتفادى فيها نقطة النهاية أي تحديث أو عدد عمليات الفحص التي قد تفوتها قبل أن تكون مطلوبة لتحديث نفسها وفحصها ضوئيا. هذا مفيد بشكل خاص في البيئات التي لا تكون فيها الأجهزة غالبا متصلة بشبكة شركة أو شبكة خارجية، أو الأجهزة التي لا يتم استخدامها بشكل يومي.

على سبيل المثال، الموظف الذي يستخدم كمبيوتر شخصي معين في وضع التوقف لمدة ثلاثة أيام ولا يسجل دخوله إلى جهاز الكمبيوتر الخاص به خلال هذه الفترة.

عندما يعود المستخدم إلى العمل ويسجل دخوله إلى الكمبيوتر الشخصي، برنامج الحماية من الفيروسات من Microsoft Defender على الفور التحقق من آخر تحديثات الحماية وتنزيلها، وتشغيل عملية فحص.

## <a name="set-up-catch-up-protection-updates-for-endpoints-that-havent-updated-for-a-while"></a>إعداد تحديثات الحماية للحاق بنقاط النهاية التي لم يتم تحديثها لفترة من الوقت

إذا برنامج الحماية من الفيروسات من Microsoft Defender تنزيل تحديثات الحماية لفترة محددة، يمكنك إعداده للتحقق من التحديث الأخير وتنزيلها تلقائيا في سجل الدخول التالي. هذا مفيد إذا قمت بتعطيل تنزيلات التحديث التلقائي بشكل عمومي [عند بدء التشغيل](manage-event-based-updates-microsoft-defender-antivirus.md).

### <a name="use-configuration-manager-to-configure-catch-up-protection-updates"></a>استخدام "إدارة التكوين" لتكوين تحديثات الحماية للحاق بك

1. على وحدة إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره ( \>  \> انقر فوق الأصول والتوافق في  جزء التنقل على اليمين، ثم قم بتوسيع الشجرة إلى نظرة عامة Endpoint Protection نهج مكافحة البرامج **الضارة**)

2. انتقل إلى **القسم تحديثات معلومات** الأمان وتكوين الإعدادات التالية:

    1. تعيين **فرض تحديث معلومات الأمان إذا كان الكمبيوتر العميل** غير متصل لأكثر من تحديثين متتاليين مجدولين إلى **نعم**.
    2. بالنسبة إلى  **"إدارة** التكوين" إذا تم استخدامها كمصدر لتحديثات معلومات الأمان...، حدد الساعات التي يجب أن تعتبر فيها تحديثات الحماية التي تم تسليمها بواسطة "إدارة التكوين" محدثة. سيتسبب هذا في استخدام موقع التحديث التالي، استنادا إلى ترتيب المصدر [الاحتياطي المحدد](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order).

3. انقر فوق **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-update-feature"></a>استخدام "نهج المجموعة" لتمكين ميزة تحديث المتابعة وتكوينها

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > التواقيع**.

5. انقر نقرا **مزدوجا** فوق الإعداد تحديد عدد الأيام التي يكون فيها تحديث معلومات الأمان للحاق مطلوبا بعد ذلك، ثم قم بتعيين الخيار إلى **تمكين**. أدخل عدد الأيام التي تريد من Microsoft Defender AV بعدها التحقق من آخر تحديث للحماية وتنزيلها.

6. انقر فوق **موافق**.

### <a name="use-powershell-cmdlets-to-configure-catch-up-protection-updates"></a>استخدام PowerShell cmdlets لتكوين تحديثات الحماية للحاق

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -SignatureUpdateCatchupInterval
```

راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين الأمرين [cmdlets](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus وتشغيلها للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-protection-updates"></a>استخدام Windows إدارة المعلومات (WMI) لتكوين تحديثات الحماية للحاق بك

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
SignatureUpdateCatchupInterval
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="set-the-number-of-days-before-protection-is-reported-as-out-of-date"></a>تعيين عدد الأيام التي يتم فيها إعداد التقارير حول الحماية كعدد

يمكنك أيضا تحديد عدد الأيام التي برنامج الحماية من الفيروسات من Microsoft Defender بعدها الحماية القديمة أو القديمة. بعد عدد الأيام المحدد، سيعرض العميل نفسه على أنه غير مهيأ، وسيعرض خطأ إلى مستخدم الكمبيوتر الشخصي. وقد يؤدي ذلك أيضا برنامج الحماية من الفيروسات من Microsoft Defender محاولة تنزيل تحديث من مصادر أخرى (استنادا إلى ترتيب المصدر الاحتياطي المعرف)، مثل عند [](manage-protection-updates-microsoft-defender-antivirus.md#fallback-order)استخدام MMPC كمصدر ثانوي بعد تعيين WSUS أو Microsoft Update كمصدر أول.

### <a name="use-group-policy-to-specify-the-number-of-days-before-protection-is-considered-out-of-date"></a>استخدام "نهج المجموعة" لتحديد عدد الأيام قبل اعتبار الحماية غير م تاريخ

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق سياسات** ثم **قوالب إدارية**.

4. قم بتوسيع الشجرة **Windows مكونات > برنامج الحماية من الفيروسات من Microsoft Defender >** تحديثات التواقيع وتكوين الإعدادات التالية:

    1. انقر نقرا **مزدوجا** فوق تعريف عدد الأيام التي قبل اعتبار تعريفات برامج التجسس غير مكتشفة، ثم قم بتعيين الخيار إلى **ممكن**. أدخل عدد الأيام التي تريد أن يعتبر فيها Microsoft Defender AV معلومات أمان برامج التجسس مكتشفة.

    2. انقر فوق **موافق**.

    3. انقر نقرا **مزدوجا** فوق تعريف عدد الأيام التي قبل اعتبار تعريفات الفيروسات غير مكتشفة، ثم قم بتعيين الخيار إلى **ممكن**. أدخل عدد الأيام التي تريد أن يعتبر فيها Microsoft Defender AV معلومات أمان الفيروسات غير مكتشفة.

    4. انقر فوق **موافق**.

## <a name="set-up-catch-up-scans-for-endpoints-that-have-not-been-scanned-for-a-while"></a>إعداد عمليات المسح الضوئي للحاق بنقاط النهاية التي لم يتم فحصها منذ فترة من الوقت

يمكنك تعيين عدد عمليات الفحص المجدولة المتتالية التي يمكن أن تفوتك برنامج الحماية من الفيروسات من Microsoft Defender فرض الفحص.

عملية تمكين هذه الميزة هي:

1. إعداد فحص مجدول واحد على الأقل (راجع الموضوع [جدولة عمليات الفحص](scheduled-catch-up-scans-microsoft-defender-antivirus.md) ).
2. تمكين ميزة المسح الضوئي للحاق.
3. حدد عدد عمليات الفحص التي يمكن تخطيها قبل إجراء فحص التقاط.

يمكن تمكين هذه الميزة لكل من الفحص الكامل والسرعة.

### <a name="use-group-policy-to-enable-and-configure-the-catch-up-scan-feature"></a>استخدام "نهج المجموعة" لتمكين ميزة المسح الضوئي للحاق وتكوينها

1. تأكد من إعداد فحص مجدول واحد على الأقل.

2. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

3. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

4. انقر **فوق سياسات** ثم **قوالب إدارية**.

5. قم بتوسيع الشجرة **Windows مكونات > برنامج الحماية من الفيروسات من Microsoft Defender > ضوئيا** وتكوين الإعدادات التالية:

    1. إذا قمت بإعداد عمليات المسح السريع المجدولة، انقر نقرا مزدوجا  فوق إعداد تشغيل المسح السريع للحاق ثم قم بتعيين الخيار إلى **تمكين**.
    2. إذا قمت بإعداد عمليات فحص كاملة مجدولة، انقر نقرا مزدوجا  فوق إعداد تشغيل مسح كامل للحاق وحدد الخيار إلى **تمكين**. انقر فوق **موافق**.
    3. انقر نقرا مزدوجا فوق **تحديد عدد** الأيام التي يتم بعدها فرض إعداد مسح المتابعة ضوئيا، ثم قم بتعيين الخيار إلى **تمكين**.
    4. أدخل عدد عمليات الفحص التي يمكن تفويتها قبل تشغيل الفحص تلقائيا عند تسجيل المستخدم التالي الدخول إلى الكمبيوتر الشخصي. يتم تحديد نوع الفحص الذي يتم تشغيله من خلال تحديد نوع الفحص الذي يجب استخدامه لمسح مجدول **(راجع** الموضوع [جدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md) عمليات الفحص). انقر فوق **موافق**.

> [!NOTE]
> يشير عنوان إعداد نهج المجموعة إلى عدد الأيام. ومع ذلك، يتم تطبيق الإعداد على عدد عمليات الفحص (وليس الأيام) قبل تشغيل المسح الضوئي للحاق.

### <a name="use-powershell-cmdlets-to-configure-catch-up-scans"></a>استخدام PowerShell cmdlets لتكوين عمليات المسح الضوئي للحاق

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -DisableCatchupFullScan
Set-MpPreference -DisableCatchupQuickScan

```

راجع [استخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md) لإدارة برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets](/powershell/module/defender/) الخاصة ب PowerShell و Defender Antivirus للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-configure-catch-up-scans"></a>استخدام Windows إدارة المعلومات (WMI) لتكوين عمليات فحص المتابعة

استخدم [**الأسلوب Set** للفئة **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) للخصائص التالية:

```WMI
DisableCatchupFullScan
DisableCatchupQuickScan
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-configuration-manager-to-configure-catch-up-scans"></a>استخدام "إدارة التكوين" لتكوين عمليات المسح الضوئي للحاق

1. على وحدة إدارة نقاط النهاية من Microsoft، افتح نهج مكافحة البرامج الضارة الذي تريد تغييره ( \>  \> انقر فوق الأصول والتوافق في  جزء التنقل على اليمين، ثم قم بتوسيع الشجرة إلى نظرة عامة Endpoint Protection نهج مكافحة البرامج **الضارة**)

2. انتقل إلى **المقطع عمليات الفحص المجدولة** وأجبر على إجراء مسح ضوئي لنوع الفحص المحدد إذا كان **الكمبيوتر العميل غير متصل...** إلى **نعم**.

3. انقر فوق **موافق**.

4. [نشر النهج المحدث كالمعتاد](/sccm/protect/deploy-use/endpoint-antimalware-policies#deploy-an-antimalware-policy-to-client-computers).

## <a name="related-articles"></a>المقالات ذات الصلة

- [نشر برنامج الحماية من الفيروسات من Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيقها](manage-updates-baselines-microsoft-defender-antivirus.md)
- [إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)
- [إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)
- [إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
