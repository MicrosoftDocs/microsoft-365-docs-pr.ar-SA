---
title: تكوين خيارات الفحص برنامج الحماية من الفيروسات من Microsoft Defender
description: يمكنك تكوين Microsoft Defender AV لمسح ملفات تخزين البريد الإلكتروني، والنسخ الاحتياطي أو إعادة توزيع النقاط، وملفات الشبكة، والملفات المؤرشفة (مثل ملفات .zip).
keywords: المسح المتقدم، والمسح الضوئي، والبريد الإلكتروني، والأرشيف، والرمز، والهرع، والأرشفة، وإعادة توزيع المسح
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
ms.openlocfilehash: a2eaeb2de0a7caf502130bef788c17e515657d7a
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788953"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>قم بتكوين خيارات فحص Microsoft Defender Antivirus

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل 

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>استخدام Microsoft Intune لتكوين خيارات الفحص

لمزيد من المعلومات، راجع [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure) [وإعدادات تقييد الجهاز برنامج الحماية من الفيروسات من Microsoft Defender Windows 10 في Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>استخدام إدارة نقاط النهاية من Microsoft لتكوين خيارات الفحص

للحصول على تفاصيل حول تكوين إدارة نقاط النهاية من Microsoft (الفرع الحالي)، راجع [كيفية إنشاء نهج مكافحة البرامج الضارة ونشرها: إعدادات الفحص](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>استخدام نهج المجموعة لتكوين خيارات الفحص

> [!TIP]
> قم بتنزيل جدول بيانات مرجعي نهج المجموعة، الذي يسرد إعدادات النهج لتكوينات الكمبيوتر والمستخدم المضمنة في ملفات القالب الإداري التي تم تسليمها مع Windows. يمكنك تكوين الإشارة إلى جدول البيانات عند تحرير نهج المجموعة العناصر. <br/><br/> فيما يلي أحدث الإصدارات:
> - [جدول بيانات مرجعي نهج المجموعة الإعدادات لتحديث Windows 10 مايو 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [جدول بيانات مرجعي نهج المجموعة الإعدادات لتحديث Windows 11 أكتوبر 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

3. في **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر** وانقر فوق **القوالب الإدارية**.

4. قم بتوسيع الشجرة Windows **المكونات** \> **برنامج الحماية من الفيروسات من Microsoft Defender**، ثم حدد موقعا (راجع [الإعدادات والمواقع](#settings-and-locations) في هذه المقالة).

5. تحرير كائن النهج.

6. انقر فوق **"موافق**"، ثم كرر أي إعدادات أخرى.

### <a name="settings-and-locations"></a>الإعدادات والمواقع

|عنصر النهج وموقعه|الإعداد الافتراضي (إذا لم يتم تكوينه)|معلمة PowerShell `Set-MpPreference` أو خاصية WMI للفئة `MSFT_MpPreference`|
|---|---|---|
|مسح البريد الإلكتروني <p> **المسح الضوئي** \> **تشغيل فحص البريد الإلكتروني**<p>راجع [قيود مسح البريد الإلكتروني](#email-scanning-limitations) (في هذه المقالة)|ذوي الاحتياجات الخاصه|`-DisableEmailScanning`|
| فحص البرنامج النصي | تمكين  | يسمح لك إعداد النهج هذا بتكوين فحص البرنامج النصي. إذا قمت بتمكين هذا الإعداد أو لم تقم بتكوينه، فسيتم تمكين فحص البرنامج النصي. <p>راجع [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|مسح [نقاط إعادة توزيع](/windows/win32/fileio/reparse-points) <p> **المسح الضوئي** \> **تشغيل المسح الضوئي لنقطة إعادة الفرز**|ذوي الاحتياجات الخاصه|غير متوفر <p>راجع [إعادة توزيع النقاط](/windows/win32/fileio/reparse-points)|
|مسح محركات أقراص الشبكة المعينة <p> **المسح الضوئي** \> **تشغيل الفحص الكامل على محركات أقراص الشبكة المعينة**|ذوي الاحتياجات الخاصه|`-DisableScanningMappedNetworkDrivesForFullScan`|
|فحص ملفات الأرشيف (مثل ملفات .zip أو .rar). <p> **المسح الضوئي** \> **فحص ملفات الأرشيف**|تمكين|`-DisableArchiveScanning` <p>ستكون [لقائمة استبعاد الملحقات](configure-extension-file-exclusions-microsoft-defender-antivirus.md) الأسبقية على هذا الإعداد.|
|مسح الملفات ضوئيا على الشبكة <p> **المسح الضوئي** \> **فحص ملفات الشبكة**|ذوي الاحتياجات الخاصه|`-DisableScanningNetworkFiles`|
|مسح الملفات التنفيذية المحزمة <p> **المسح الضوئي** \> **مسح الملفات التنفيذية المحزمة**|تمكين|غير متوفر|
|مسح محركات الأقراص القابلة للإزالة ضوئيا أثناء عمليات الفحص الكاملة فقط <p> **المسح الضوئي** \> **مسح محركات الأقراص القابلة للإزالة ضوئيا**|ذوي الاحتياجات الخاصه|`-DisableRemovableDriveScanning`|
|تحديد مستوى المجلدات الفرعية داخل مجلد أرشيف للمسح الضوئي <p>**المسح الضوئي** \> **تحديد الحد الأقصى للعمق لمسح ملفات الأرشيف**|0|غير متوفر|
|حدد الحد الأقصى لتحميل وحدة المعالجة المركزية (كنسبة مئوية) أثناء الفحص. <p> **المسح الضوئي** \> **تحديد النسبة المئوية القصوى لاستخدام وحدة المعالجة المركزية أثناء الفحص**|50|`-ScanAvgCPULoadFactor` <p>**ملاحظة**: الحد الأقصى لتحميل وحدة المعالجة المركزية ليس حدا صعبا، ولكنه إرشادات لمحرك الفحص بحيث لا يتجاوز الحد الأقصى في المتوسط. سيتجاهل تشغيل عمليات الفحص يدويا هذا الإعداد ويتم تشغيله دون أي حدود لوحدة المعالجة المركزية.|
|حدد الحجم الأقصى (بالكيلو بايت) لملفات الأرشيف التي يجب مسحها ضوئيا. <p> **المسح الضوئي** \> **تحديد الحد الأقصى لحجم ملفات الأرشيف التي سيتم مسحها ضوئيا**|لا يوجد حد|غير متوفر <p>لا تنطبق القيمة الافتراضية 0 على أي حد|
|تكوين أولوية وحدة المعالجة المركزية المنخفضة لإجراء عمليات الفحص المجدولة <p> **المسح الضوئي** \> **تكوين أولوية وحدة المعالجة المركزية المنخفضة لإجراء عمليات الفحص المجدولة**|ذوي الاحتياجات الخاصه|غير متوفر|

> [!NOTE]
> إذا تم تشغيل الحماية في الوقت الحقيقي، يتم مسح الملفات ضوئيا قبل الوصول إليها وتنفيذها. يتضمن نطاق الفحص كافة الملفات، بما في ذلك الملفات الموجودة على الوسائط القابلة للإزالة المثبتة، مثل محركات أقراص USB. إذا كان الجهاز الذي يقوم بالمسح الضوئي لديه حماية في الوقت الحقيقي أو حماية عند الوصول قيد التشغيل، فإن الفحص سيتضمن أيضا مشاركات الشبكة.

## <a name="use-powershell-to-configure-scanning-options"></a>استخدام PowerShell لتكوين خيارات الفحص

لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender، راجع

- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell cmdlets](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender cmdlets](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>استخدام WMI لتكوين خيارات الفحص

راجع [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>قيود مسح البريد الإلكتروني

يتيح مسح البريد الإلكتروني مسح ملفات البريد الإلكتروني المستخدمة من قبل Outlook وعملاء البريد الآخرين أثناء عمليات الفحص حسب الطلب والمجدولة. كما يتم فحص الكائنات المضمنة داخل البريد الإلكتروني (مثل المرفقات والملفات المؤرشفة). يمكن مسح أنواع تنسيقات الملفات التالية ضوئيا ومعالجتها:

- DBX
- MBX
- MIME

يتم أيضا فحص ملفات PST المستخدمة من قبل Outlook 2003 أو إصدار أقدم (حيث تم تعيين نوع الأرشيف إلى غير unicode)، ولكن برنامج الحماية من الفيروسات من Microsoft Defender لا يمكن معالجة التهديدات التي تم اكتشافها داخل ملفات PST.

إذا كشف برنامج الحماية من الفيروسات من Microsoft Defender عن تهديد داخل رسالة بريد إلكتروني، فسيعرض لك المعلومات التالية لمساعدتك في تحديد البريد الإلكتروني الذي تم اختراقه، حتى تتمكن من معالجة التهديد يدويا:

- موضوع البريد الإلكتروني
- اسم المرفق

## <a name="scanning-mapped-network-drives"></a>مسح محركات أقراص الشبكة المعينة ضوئيا

على أي نظام تشغيل، يتم مسح محركات أقراص الشبكة التي تم تعيينها على مستوى النظام فقط. لا يتم مسح محركات أقراص الشبكة المعينة على مستوى المستخدم ضوئيا. محركات أقراص الشبكة المعينة على مستوى المستخدم هي تلك التي يقوم المستخدم بتعيينها في جلسة العمل الخاصة به يدويا واستخدام بيانات الاعتماد الخاصة به.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [تخصيص نتائج عمليات الفحص والمعالجة برنامج الحماية من الفيروسات من Microsoft Defender وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص عند برنامج الحماية من الفيروسات من Microsoft Defender عند الطلب](run-scan-microsoft-defender-antivirus.md)
- [تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
