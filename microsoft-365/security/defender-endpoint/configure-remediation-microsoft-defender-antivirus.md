---
title: تكوين المعالجة برنامج الحماية من الفيروسات من Microsoft Defender الكشف
description: تكوين ما يجب أن تفعله برنامج الحماية من الفيروسات من Microsoft Defender عند الكشف عن تهديد، ومدة الاحتفاظ بالملفات المعزولة في مجلد العزل
keywords: المعالجة، الإصلاح، الإزالة، التهديدات، العزل، الفحص، الاستعادة
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f07e62edd43098a493c80ca7f3155c148793578e
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419165"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>تكوين المعالجة برنامج الحماية من الفيروسات من Microsoft Defender الكشف


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

عندما يقوم برنامج الحماية من الفيروسات من Microsoft Defender بتشغيل عملية فحص، فإنه يحاول معالجة التهديدات التي تم اكتشافها أو إزالتها. يمكنك تكوين كيفية معالجة برنامج الحماية من الفيروسات من Microsoft Defender لتهديدات معينة، وما إذا كان يجب إنشاء نقطة استعادة قبل المعالجة، ومتى يجب إزالة التهديدات.

تصف هذه المقالة كيفية تكوين هذه الإعدادات باستخدام نهج المجموعة، ولكن يمكنك أيضا استخدام [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) [Microsoft Intune](/intune/device-restrictions-configure).

يمكنك أيضا استخدام [`Set-MpPreference` فئة PowerShell cmdlet](/powershell/module/defender/set-mppreference) أو [`MSFT_MpPreference` WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) لتكوين هذه الإعدادات.

## <a name="configure-remediation-options"></a>تكوين خيارات المعالجة

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في **نهج المجموعة انتقل محرر الإدارة** إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender**.

4. باستخدام الجدول أدناه، حدد موقعا، ثم قم بتحرير النهج حسب الحاجة.

5. حدد **موافق**.

<br/><br/>

|موقع|اعداد|الوصف|الإعداد الافتراضي (إذا لم يتم تكوينه)|
|---|---|---|---|
|المسح الضوئي|إنشاء نقطة استعادة النظام|سيتم إنشاء نقطة استعادة النظام كل يوم قبل محاولة التنظيف أو الفحص|ذوي الاحتياجات الخاصه|
|المسح الضوئي|تشغيل إزالة العناصر من مجلد محفوظات الفحص|تحديد عدد الأيام التي يجب الاحتفاظ بها في محفوظات الفحص|30 يوماً|
|الجذر|إيقاف تشغيل المعالجة الروتينية|يمكنك تحديد ما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender معالجة التهديدات تلقائيا، أو ما إذا كان يجب أن يطلب من مستخدم نقطة النهاية ما يجب فعله.|معطل (تتم معالجة التهديدات تلقائيا)|
|العزل|تكوين إزالة العناصر من مجلد العزل|تحديد عدد الأيام التي يجب الاحتفاظ بها في العزل قبل إزالتها|90 يوما|
|التهديدات|تحديد مستويات التنبيه للمخاطر التي لا يجب اتخاذ إجراء افتراضي عند الكشف عنها|يتم تعيين مستوى التهديد لكل تهديد يتم اكتشافه بواسطة برنامج الحماية من الفيروسات من Microsoft Defender (منخفض أو متوسط أو مرتفع أو شديد). يمكنك استخدام هذا الإعداد لتحديد كيفية معالجة جميع التهديدات لكل مستوى من مستويات التهديد (عزلها أو إزالتها أو تجاهلها)|غير قابل للتطبيق|
|التهديدات|تحديد التهديدات التي لا ينبغي اتخاذ إجراء افتراضي عليها عند الكشف عنها|حدد كيفية معالجة التهديدات المحددة (باستخدام معرف التهديد الخاص بها). يمكنك تحديد ما إذا كان يجب عزل التهديد المحدد أو إزالته أو تجاهله|غير قابل للتطبيق|

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender الكشف عن الملفات ومعالجتها استنادا إلى العديد من العوامل. في بعض الأحيان، يتطلب إكمال المعالجة إعادة التشغيل. حتى إذا تم تحديد الكشف لاحقا على أنه إيجابي زائف، يجب إكمال إعادة التشغيل لضمان اكتمال جميع خطوات المعالجة الإضافية.
>
> إذا كنت متأكدا من برنامج الحماية من الفيروسات من Microsoft Defender عزل ملف استنادا إلى إيجابية خاطئة، يمكنك استعادة الملف من العزل بعد إعادة تشغيل الجهاز. راجع [استعادة الملفات المعزولة في برنامج الحماية من الفيروسات من Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> لتجنب هذه المشكلة في المستقبل، يمكنك استبعاد الملفات من عمليات الفحص. راجع [تكوين الاستثناءات والتحقق من صحتها لإجراء عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

راجع أيضا [تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender الكاملة المجدولة المطلوبة](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) للمعالجة للحصول على المزيد من الإعدادات المتعلقة بالمعالجة.

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

- [قم بتكوين خيارات فحص Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب](run-scan-microsoft-defender-antivirus.md)
- [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
- [تكوين تفاعل برنامج الحماية من الفيروسات من Microsoft Defender للمستخدم النهائي](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [تخصيص نتائج عمليات الفحص والمعالجة برنامج الحماية من الفيروسات من Microsoft Defender وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
