---
title: تكوين المعالجة برنامج الحماية من الفيروسات من Microsoft Defender الكشف
description: تكوين ما برنامج الحماية من الفيروسات من Microsoft Defender القيام به عند الكشف عن وجود خطر، ومدى الوقت الذي يجب الاحتفاظ بالملفات المعزولة في مجلد الفحص
keywords: المعالجة، الإصلاح، الإزالة، التهديدات، الفحص، الفحص، الاستعادة
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
ms.openlocfilehash: 182e0b39c1a9c7795fbdd716fc2e260d06d5c451
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63571611"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>تكوين المعالجة برنامج الحماية من الفيروسات من Microsoft Defender الكشف


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

عندما برنامج الحماية من الفيروسات من Microsoft Defender عملية فحص، فإنه يحاول معالجة التهديدات التي تم الكشف عنها أو إزالتها. يمكنك تكوين كيفية برنامج الحماية من الفيروسات من Microsoft Defender معالجة بعض التهديدات، وما إذا كان يجب إنشاء نقطة استعادة قبل المعالجة، ومتى يجب إزالة التهديدات.

تصف هذه المقالة كيفية تكوين هذه الإعدادات باستخدام "نهج المجموعة"، ولكن يمكنك أيضا استخدام [Microsoft Endpoint Configuration Manager Microsoft Intune.](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) [](/intune/device-restrictions-configure)

يمكنك أيضا استخدام [فئة`Set-MpPreference` PowerShell cmdlet](/powershell/module/defender/set-mppreference) أو [`MSFT_MpPreference` WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) لتكوين هذه الإعدادات.

## <a name="configure-remediation-options"></a>تكوين خيارات المعالجة

1. على كمبيوتر إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \> **.**

4. باستخدام الجدول أدناه، حدد موقع، ثم قم بتحرير النهج كما هو مطلوب.

5. حدد **موافق**.

<br/><br/>

|الموقع|الإعداد|الوصف|الإعداد الافتراضي (إذا لم يتم تكوينه)|
|---|---|---|---|
|المسح الضوئي|إنشاء نقطة استعادة النظام|سيتم إنشاء نقطة استعادة النظام كل يوم قبل محاولة التنظيف أو الفحص|معطل|
|المسح الضوئي|تشغيل إزالة العناصر من مجلد محفوظات الفحص|تحديد عدد الأيام التي يجب الاحتفاظ فيها بالعناصر في محفوظات الفحص|30 يوماً|
|الجذر|إيقاف تشغيل المعالجة الروتينية|يمكنك تحديد ما إذا برنامج الحماية من الفيروسات من Microsoft Defender معالجة التهديدات تلقائيا، أو إذا كان يجب أن تسأل مستخدم نقطة النهاية عما يجب فعله.|معطل (يتم معالجة التهديدات تلقائيا)|
|الفحص|تكوين إزالة العناصر من مجلد "الفحص"|تحديد عدد الأيام التي يجب فيها الاحتفاظ بالعناصر في الفحص قبل إزالتها|90 يوما|
|التهديدات|تحديد مستويات تنبيهات التهديدات التي يجب عدم اتخاذ إجراء افتراضي عند الكشف عنها|يتم تعيين كل خطر يتم اكتشافه بواسطة برنامج الحماية من الفيروسات من Microsoft Defender إلى مستوى خطر (منخفض أو متوسط أو عال أو شديد). يمكنك استخدام هذا الإعداد لتعريف كيفية معالجة جميع التهديدات لكل مستوى من مستويات التهديدات (معزولة أو إزالتها أو تجاهلها)|غير قابل للتطبيق|
|التهديدات|تحديد التهديدات التي يجب عدم اتخاذ إجراء افتراضي عليها عند الكشف عنها|حدد كيفية معالجة تهديدات معينة (باستخدام "معرّف التهديدات" الخاص بها). يمكنك تحديد ما إذا كان يجب فحص الخطر المحدد أو إزالته أو تجاهله|غير قابل للتطبيق|

> [!IMPORTANT]
> برنامج الحماية من الفيروسات من Microsoft Defender عن الملفات التي تستند إلى العديد من العوامل وتتوسطها. في بعض الأحيان، يتطلب إكمال المعالجة إعادة تمهيد. حتى لو تم تحديد عملية الكشف لاحقا على أنها إيجابية خاطئة، يجب إكمال عملية إعادة التشغيل لضمان اكتمال كل خطوات الإصلاح الإضافية.
>
> إذا كنت واثقا برنامج الحماية من الفيروسات من Microsoft Defender ملف تم فحصه استنادا إلى إيجابية خاطئة، يمكنك استعادة الملف من الفحص بعد إعادة تشغيل الجهاز. راجع [استعادة الملفات المعزولة في برنامج الحماية من الفيروسات من Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md).
>
> لتجنب هذه المشكلة في المستقبل، يمكنك استبعاد الملفات من عمليات الفحص. راجع [تكوين الاستثناءات والتحقق من صحتها برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md).

راجع [أيضا تكوين عمليات](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) المسح الكامل المجدولة برنامج الحماية من الفيروسات من Microsoft Defender المعالجة المطلوبة للحصول على مزيد من الإعدادات ذات الصلة بالتعديلات.

## <a name="see-also"></a>راجع أيضًا

- [تكوين خيارات برنامج الحماية من الفيروسات من Microsoft Defender ضوئية](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender مجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب](run-scan-microsoft-defender-antivirus.md)
- [تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
- [تكوين تفاعل المستخدم برنامج الحماية من الفيروسات من Microsoft Defender المستخدم](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [تخصيص نتائج عمليات المسح برنامج الحماية من الفيروسات من Microsoft Defender والوساطة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
