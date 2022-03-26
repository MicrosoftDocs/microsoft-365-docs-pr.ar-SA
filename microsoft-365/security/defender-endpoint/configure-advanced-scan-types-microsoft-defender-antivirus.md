---
title: تكوين خيارات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك تكوين Microsoft Defender AV لمسح ملفات تخزين البريد الإلكتروني ضوئيا، والنقاط التي تم إجراء حفظي لها أو إعادة حسابها، وملفات الشبكة، والملفات المؤرشفة (مثل ملفات .zip).
keywords: عمليات الفحص المتقدمة، والمسح الضوئي، والبريد الإلكتروني، والأرشفة، والرمز المضغوط، والأرشفة، وفحص reparse
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.date: 12/03/2021
ms.collection: M365-security-compliance
ms.topic: how-to
ms.openlocfilehash: 2527a558d474fecaab813963dc38a9e76aa89d5c
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/06/2021
ms.locfileid: "63573882"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>تكوين خيارات برنامج الحماية من الفيروسات من Microsoft Defender ضوئية

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>استخدام Microsoft Intune لتكوين خيارات الفحص

لمزيد من المعلومات، راجع [](/intune/device-restrictions-configure) تكوين إعدادات تقييد الجهاز في Microsoft Intune برنامج الحماية من الفيروسات من Microsoft Defender إعدادات تقييد الجهاز Windows 10 [Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>استخدام إدارة نقاط النهاية من Microsoft لتكوين خيارات الفحص

للحصول على تفاصيل حول إدارة نقاط النهاية من Microsoft (الفرع الحالي)، راجع كيفية إنشاء سياسات مكافحة البرامج الضارة [ونشرها: إعدادات](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) الفحص.

## <a name="use-group-policy-to-configure-scanning-options"></a>استخدام "نهج المجموعة" لتكوين خيارات الفحص

> [!TIP]
> قم بتنزيل جدول بيانات مرجع نهج المجموعة، الذي يسرد إعدادات النهج لتكوينات الكمبيوتر والمستخدم المضمنة في ملفات القوالب الإدارية التي تم تسليمها Windows. يمكنك تكوين الرجوع إلى جدول البيانات عند تحرير كائنات نهج المجموعة. <br/><br/> فيما يلي أحدث الإصدارات:
> - [نهج المجموعة الإعدادات جدول البيانات المرجعي Windows 10 تحديث مايو 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [نهج المجموعة الإعدادات جدول البيانات المرجعي Windows 11 تحديث أكتوبر 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر ب الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه، ثم حدد **تحرير**.

3. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر** وانقر فوق **قوالب إدارية**.

4. قم بتوسيع الشجرة **Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender**\>، ثم حدد موقعا (راجع الإعدادات [والمواقع في](#settings-and-locations) هذه المقالة).

5. تحرير كائن النهج.

6. انقر **فوق موافق**، وكرر أي إعدادات أخرى.

### <a name="settings-and-locations"></a>الإعدادات والمواقع

|عنصر النهج وموقعه|الإعداد الافتراضي (إذا لم يتم تكوينه)|معلمة PowerShell `Set-MpPreference` أو خاصية WMI للفئة `MSFT_MpPreference`|
|---|---|---|
|مسح البريد الإلكتروني <p> **المسح الضوئي** \> **تشغيل مسح البريد الإلكتروني**<p>راجع [قيود مسح البريد الإلكتروني](#email-scanning-limitations) (في هذه المقالة)|معطل|`-DisableEmailScanning`|
| مسح البرنامج النصي | تم التمكين  | يسمح لك إعداد النهج هذا بتكوين مسح البرنامج النصي. إذا قمت بتمكين هذا الإعداد أو لم تقوم بتكوينه، سيتم تمكين مسح البرنامج النصي. <p>راجع [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|فحص [نقاط reparse](/windows/win32/fileio/reparse-points) <p> **المسح الضوئي** \> **تشغيل مسح نقاط reparse**|معطل|غير متوفر <p>راجع [إعادة افصل النقاط](/windows/win32/fileio/reparse-points)|
|مسح محركات أقراص الشبكة التي تم تعيينها <p> **المسح الضوئي** \> **تشغيل الفحص الكامل على محركات أقراص الشبكة التي تم تعيينها**|معطل|`-DisableScanningMappedNetworkDrivesForFullScan`|
|فحص ملفات الأرشيف (مثل ملفات .zip أو .rar). <p> **المسح الضوئي** \> **فحص ملفات الأرشيف**|تم التمكين|`-DisableArchiveScanning` <p>[ستأخذ قائمة استثناءات](configure-extension-file-exclusions-microsoft-defender-antivirus.md) الملحقات الأسبقية على هذا الإعداد.|
|فحص الملفات على الشبكة <p> **المسح الضوئي** \> **فحص ملفات الشبكة**|معطل|`-DisableScanningNetworkFiles`|
|مسح معبأة القابلة للتنفيذ <p> **المسح الضوئي** \> **مسح معبأة القابلة للتنفيذ**|تم التمكين|غير متوفر|
|فحص محركات الأقراص القابلة للإزالة أثناء الفحص الكامل فقط <p> **المسح الضوئي** \> **فحص محركات الأقراص القابلة للإزالة**|معطل|`-DisableRemovableDriveScanning`|
|تحديد مستوى المجلدات الفرعية ضمن مجلد أرشيف لفحصه <p>**المسح الضوئي** \> **تحديد الحد الأقصى للعمق لمسح ملفات الأرشيف ضوئيا**|0|غير متوفر|
|حدد الحد الأقصى لتحميل CPU (كنسبة مئوية) أثناء الفحص. <p> **المسح الضوئي** \> **تحديد الحد الأقصى للنسبة المئوية لاستخدام CPU أثناء الفحص**|50|`-ScanAvgCPULoadFactor` <p>**ملاحظة**: إن الحد الأقصى لتحميل CPU ليس حدا صعبا، ولكنه إرشاد لمحرك الفحص حتى لا يتجاوز الحد الأقصى في المتوسط. سيتجاهل تشغيل عمليات الفحص يدويا هذا الإعداد وسيبقى في وضع التشغيل دون أي قيود على وحدة المعالجة المركزية (CPU).|
|حدد الحد الأقصى لحجم ملفات الأرشيف التي يجب فحصها (بالكيلوبايت). <p> **المسح الضوئي** \> **تحديد الحد الأقصى لحجم ملفات الأرشيف المطلوب فحصها**|بلا حد|غير متوفر <p>لا تنطبق القيمة الافتراضية 0 على أي حد|
|تكوين أولوية منخفضة لوحدة المعالجة المركزية (CPU) لمسح ضوئي مجدول <p> **المسح الضوئي** \> **تكوين أولوية منخفضة لوحدة المعالجة المركزية (CPU) لمسح ضوئي مجدول**|معطل|غير متوفر|

> [!NOTE]
> إذا تم تشغيل الحماية في الوقت الحقيقي، يتم فحص الملفات قبل الوصول إليها وتنفيذها. يتضمن نطاق الفحص كل الملفات، بما في ذلك الملفات على الوسائط المثبتة القابلة للإزالة، مثل محركات أقراص USB. إذا كان الجهاز الذي يقوم بالفحص يتضمن حماية في الوقت الحقيقي أو تم تشغيل الحماية عند الوصول، سيتضمن الفحص أيضا أسهم الشبكة.

## <a name="use-powershell-to-configure-scanning-options"></a>استخدام PowerShell لتكوين خيارات الفحص

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع

- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender cmdlets](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>استخدام WMI لتكوين خيارات الفحص

راجع [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>قيود فحص البريد الإلكتروني

يمكن مسح البريد الإلكتروني فحص ملفات البريد الإلكتروني التي يستخدمها Outlook عملاء البريد الآخرين أثناء عمليات الفحص عند الطلب والم مجدولة. يتم أيضا فحص العناصر المضمنة في البريد الإلكتروني (مثل المرفقات والملفات المؤرشفة). يمكن فحص أنواع تنسيقات الملفات التالية و إصلاحها:

- DBX
- MBX
- MIME

يتم أيضا فحص ملفات PST التي يستخدمها Outlook 2003 أو الإصدارات الأقدم (حيث يتم تعيين نوع الأرشيف إلى غير unicode)، ولكن يتعذر على برنامج الحماية من الفيروسات من Microsoft Defender معالجة التهديدات التي يتم اكتشافها داخل ملفات PST.

إذا برنامج الحماية من الفيروسات من Microsoft Defender رسالة بريد إلكتروني عن وجود خطر داخل رسالة بريد إلكتروني، فستعرض لك المعلومات التالية لمساعدتك في تحديد البريد الإلكتروني الذي تم اختراقه، حتى تتمكن من معالجة هذا الخطر يدويا:

- موضوع البريد الإلكتروني
- اسم المرفق

## <a name="scanning-mapped-network-drives"></a>مسح محركات أقراص الشبكة التي تم تعيينها

على أي نظام تشغيل، يتم فحص محركات أقراص الشبكة التي تم تعيينها على مستوى النظام فقط. لا يتم فحص محركات أقراص الشبكة التي تم تعيينها على مستوى المستخدم. إن محركات أقراص الشبكة التي تم تعيينها على مستوى المستخدم هي تلك التي يقوم المستخدم بخرائطها في جلسة العمل يدويا واستخدام بيانات الاعتماد الخاصة به.

## <a name="see-also"></a>راجع أيضًا

- [تخصيص نتائج عمليات المسح برنامج الحماية من الفيروسات من Microsoft Defender والوساطة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب](run-scan-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender مجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
