---
title: التبديل إلى Microsoft Defender لنقطة النهاية - إلحاق
description: قم بالتبديل إلى Microsoft Defender لنقطة النهاية. قم بإلحاق الأجهزة ثم قم بإلغاء تثبيت الحل غير التابع ل Microsoft.
keywords: الترحيل، Microsoft Defender لنقطة النهاية، edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-migratetomdatp
- m365solution-mcafeemigrate
- m365solution-symantecmigrate
ms.custom:
- migrationguides
- admindeeplinkDEFENDER
ms.topic: article
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: d927f1a5972e24c3bae0329bd866a4b56b0a5d95
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717239"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>التبديل إلى Microsoft Defender لنقطة النهاية - المرحلة 3: إلحاق

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![المرحلة 1: الإعداد3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[المرحلة 1: التحضير](switch-to-mde-phase-1.md) | [![المرحلة 2: إعداد](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[المرحلة 2: إعداد](switch-to-mde-phase-2.md) | ![المرحلة 3: التجهيز للاستخدام](images/phase-diagrams/onboard.png#lightbox)<br/>المرحلة 3: التجهيز للاستخدام |
|--|--|--|
|| |*أنت هنا!* |

**مرحبا بك في المرحلة 3 من [التبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)**. تتضمن مرحلة الترحيل هذه الخطوات التالية:

1. [إلحاق الأجهزة ب Defender لنقطة النهاية](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [تشغيل اختبار الكشف](#run-a-detection-test).
3. [تأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على نقاط النهاية.](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints)
4. [احصل على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).
5. [إلغاء تثبيت الحل غير التابع ل Microsoft](#uninstall-your-non-microsoft-solution).
6. [تأكد من أن Defender لنقطة النهاية يعمل بشكل صحيح](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>إلحاق الأجهزة Microsoft Defender لنقطة النهاية

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. اختر **إعدادات** \> **إلحاق نقاط** \> النهاية **(ضمن** **إدارة الجهاز**).

3. في **تحديد نظام التشغيل لبدء قائمة عمليات الإلحاق** ، حدد نظام تشغيل.

4. ضمن **أسلوب النشر**، حدد خيارا. اتبع الارتباطات والمطالبات لإلحاق أجهزة مؤسستك. هل تحتاج إلى مساعدة؟ راجع [أساليب الإلحاق](#onboarding-methods) (في هذه المقالة).

> [!NOTE]
> إذا حدث خطأ ما أثناء الإلحاق، فراجع [استكشاف أخطاء Microsoft Defender لنقطة النهاية الإلحاق وإصلاحها](troubleshoot-onboarding.md). تصف هذه المقالة كيفية حل مشاكل الإلحاق والأخطاء الشائعة على نقاط النهاية.

### <a name="onboarding-methods"></a>أساليب الإلحاق

> [!IMPORTANT]
> إذا كنت تستخدم Microsoft Defender for Cloud، فراجع [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

تختلف أساليب النشر، اعتمادا على نظام التشغيل والأساليب المفضلة. يسرد الجدول التالي الموارد لمساعدتك في إلحاق Defender لنقطة النهاية:

|أنظمة التشغيل  |اساليب  |
|---------|---------|
|Windows 10 أو أحدث<br/><br/>Windows Server 2019 أو إصدار أحدث<br/><br/>Windows Server، الإصدار 1803 أو أحدث<br/><br/>Windows Server 2012 R2 و2016<sup>[[1](#fn1)]<sup>  |   [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md)<br><br/>   [نهج المجموعة](configure-endpoints-gp.md)<br/><br/>[Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)<br/><br/>[Microsoft إدارة نقاط النهاية/ Mobile إدارة الجهاز (Intune)](configure-endpoints-mdm.md)<br>    [البرامج النصية ل VDI](configure-endpoints-vdi.md) <br><br> **ملاحظة**: البرنامج النصي المحلي مناسب لإثبات المفهوم ولكن لا ينبغي استخدامه لتوزيع الإنتاج. لنشر الإنتاج، نوصي باستخدام نهج المجموعة أو نقطة نهاية Microsoft Configuration Manager أو Intune. |
|Windows Server 2008 R2 SP1 | [عامل مراقبة Microsoft (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma)  أو [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **ملاحظة**: عامل مراقبة Microsoft هو الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة على عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  |
|Windows 8.1 Enterprise<br/><br/>Windows 8.1 Pro<br/><br/>Windows 7 SP1 Pro<br/><br/>Windows 7 SP1| [عامل مراقبة Microsoft (MMA)](onboard-downlevel.md) <br><br> **ملاحظة**: عامل مراقبة Microsoft هو الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة على عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
| macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md) | [البرنامج النصي المحلي](mac-install-manually.md)<br/><br/>[إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md)<br/><br/>[JAMF Pro](mac-install-with-jamf.md)<br/><br/>[إدارة الجهاز الجوال](mac-install-with-other-mdm.md)   |
| Linux (راجع [متطلبات النظام](microsoft-defender-endpoint-linux.md#system-requirements)) |  [البرنامج النصي المحلي](linux-install-manually.md) <br><br/> [دميه](linux-install-with-puppet.md) <br><br/> [Ansible](linux-install-with-ansible.md)|  
| دائره الرقابه الداخليه | [إدارة نقاط النهاية من Microsoft](ios-install.md)     |
|الروبوت  | [إدارة نقاط النهاية من Microsoft](android-intune.md)  | 

(<a id="fn1">1</a>) يجب أن يتم إلحاق Windows Server 2016 وWindows Server 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows الملحقة](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).

## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف

للتحقق من أن أجهزتك الملحقة متصلة بشكل صحيح ب Defender لنقطة النهاية، يمكنك تشغيل اختبار الكشف.

|نظام التشغيل|التوجيه|
|---|---|
|Windows 10 أو أحدث<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server، الإصدار 1803، أو أحدث<br/><br/>Windows Server 2016‏<br/><br/>Windows Server 2012 R2|راجع [تشغيل اختبار الكشف](run-detection-test.md).|
|macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md)|قم بتنزيل تطبيق DIY واستخدامه في <https://aka.ms/mdatpmacosdiy>. <br/><br/> لمزيد من المعلومات، راجع [Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md).|
|Linux (راجع [متطلبات النظام](microsoft-defender-endpoint-linux.md#system-requirements))|1. قم بتشغيل الأمر التالي، وابحث عن نتيجة **1**: `mdatp health --field real_time_protection_enabled`.<br/><br/>2. افتح نافذة Terminal، وقم بتشغيل الأمر التالي: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. قم بتشغيل الأمر التالي لإدراج أي تهديدات تم اكتشافها: `mdatp threat list`.<br/><br/>لمزيد من المعلومات، راجع [Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md).|

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>تأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على نقاط النهاية

الآن بعد أن تم إلحاق نقاط النهاية الخاصة بك إلى Defender لنقطة النهاية، فإن خطوتك التالية هي التأكد من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. يمكنك استخدام أحد الأساليب المتعددة، كما هو موضح في الجدول التالي:

|الاسلوب|ما يجب فعله|
|---|---|
|موجه الأوامر|1. على جهاز Windows، افتح موجه الأوامر.<br/><br/>2. اكتب `sc query windefend`، ثم اضغط على مفتاح الإدخال Enter.<br/><br/>3. راجع النتائج للتأكد من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي.|
|PowerShell|1. على جهاز Windows، افتح Windows PowerShell كمسؤول.<br/><br/>2. تشغيل التالي PowerShell cmdlet: `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. راجع النتائج. يجب أن تشاهد **الوضع السلبي**.|
|تطبيق أمن Windows|1. على جهاز Windows، افتح تطبيق أمن Windows.<br/><br/>2. حدد **الحماية من التهديدات & الفيروسات**.<br/><br/>3. ضمن **من يحميني؟** حدد **"إدارة الموفرين**".<br/><br/>4. في صفحة **موفري الأمان** ، ضمن **برنامج الحماية من الفيروسات**، **يتم تشغيل البحث عن برنامج الحماية من الفيروسات من Microsoft Defender**.|
|إدارة المهام|1. على جهاز Windows، افتح تطبيق Task Manager.<br/><br/>2. حدد علامة التبويب **"تفاصيل** ". ابحث عن **MsMpEng.exe** في القائمة.|

> [!NOTE]
> قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender* في بعض إصدارات Windows.
> لمعرفة المزيد حول الوضع السلبي ووضع النشاط، راجع [المزيد من التفاصيل حول حالات برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server إلى الوضع السلبي يدويا

لتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server أو الإصدار 1803 أو الأحدث أو Windows Server 2019 أو Windows Server 2022، اتبع الخطوات التالية:

1. افتح محرر السجل، ثم انتقل إلى `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. تحرير (أو إنشاء) إدخال DWORD يسمى **ForceDefenderPassiveMode**، وتحديد الإعدادات التالية:

   - تعيين قيمة DWORD إلى **1**.

   - ضمن **Base**، حدد **سداسي عشري**.

> [!NOTE]
> يمكنك استخدام أساليب أخرى لتعيين مفتاح التسجيل، مثل ما يلي:
>
> - [تفضيل نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [أداة كائن نهج المجموعة المحلي](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [حزمة في Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>بدء برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016

إذا كنت تستخدم Windows Server 2016، فقد تحتاج إلى بدء تشغيل برنامج الحماية من الفيروسات من Microsoft Defender يدويا. يمكنك تنفيذ هذه المهمة باستخدام PowerShell cmdlet `mpcmdrun.exe -wdenable` على الجهاز.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>الحصول على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender

يعد تحديث برنامج الحماية من الفيروسات من Microsoft Defender أمرا بالغ الأهمية لضمان حصول أجهزتك على أحدث التقنيات والميزات اللازمة للحماية من البرامج الضارة الجديدة وتقنيات الهجوم، حتى لو كان برنامج الحماية من الفيروسات من Microsoft Defender يعمل في الوضع السلبي. (راجع [توافق برنامج الحماية من الفيروسات ل Microsoft Defender](microsoft-defender-antivirus-compatibility.md).)

هناك نوعان من التحديثات المتعلقة بالحفاظ على تحديث برنامج الحماية من الفيروسات من Microsoft Defender:

- تحديثات التحليل الذكي لمخاطر الأمان

- تحديثات المنتجات

للحصول على التحديثات، اتبع الإرشادات الواردة في [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>إلغاء تثبيت الحل غير التابع ل Microsoft

إذا كان لديك في هذه المرحلة:

- إلحاق أجهزة مؤسستك ب Defender لنقطة النهاية، و

- تم تثبيت برنامج الحماية من الفيروسات من Microsoft Defender وتمكينه،

ثم خطوتك التالية هي إلغاء تثبيت حل الحماية من الفيروسات والحماية من البرامج الضارة ونقطة النهاية غير التابع ل Microsoft. عند إلغاء تثبيت الحل غير التابع ل Microsoft، يقوم برنامج الحماية من الفيروسات من Microsoft Defender بالتبديل من الوضع السلبي إلى الوضع النشط. في معظم الحالات، يحدث هذا تلقائيا. 

> [!IMPORTANT]
> إذا لم ينتقل برنامج الحماية من الفيروسات من Microsoft Defender، لسبب ما، إلى الوضع النشط بعد إلغاء تثبيت حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft، [فراجع برنامج الحماية من الفيروسات من Microsoft Defender يبدو أنه عالق في الوضع السلبي](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

للحصول على المساعدة في إلغاء تثبيت الحل غير التابع ل Microsoft، اتصل بفريق الدعم التقني.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>تأكد من أن Defender لنقطة النهاية يعمل بشكل صحيح

الآن بعد أن قمت بإلحاق Defender لنقطة النهاية، وقمت بإلغاء تثبيت الحل السابق غير التابع ل Microsoft، فإن خطوتك التالية هي التأكد من أن Defender لنقطة النهاية يعمل بشكل صحيح. 

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **مخزون أجهزة** **نقاط** >  النهاية. هناك، ستتمكن من رؤية حالة الحماية للأجهزة.

لمعرفة المزيد، راجع [مخزون الجهاز](machines-view-overview.md).

## <a name="next-steps"></a>الخطوات التالية

**تهانينا**! لقد أكملت [الترحيل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)!

- [تفضل بزيارة لوحة معلومات عمليات الأمان](security-operations-dashboard.md) في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)).

- [إدارة Defender لنقطة النهاية، بعد الترحيل](manage-mde-post-migration.md).
