---
title: التبديل إلى Microsoft Defender لنقطة النهاية - Onboard
description: قم بالتبديل إلى Microsoft Defender لنقطة النهاية. الأجهزة المجهزة، ثم قم ب إلغاء تثبيت الحل غير الخاص بك من Microsoft.
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
ms.date: 03/28/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 1397c34e8e4a7f1fcb20df192409bd57bc50f40b
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507110"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-3-onboard"></a>التبديل إلى Microsoft Defender لنقطة النهاية - المرحلة 3: Onboard

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

| [![المرحلة 1: التحضير3.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[المرحلة 1: التحضير](switch-to-mde-phase-1.md) | [![المرحلة الثانية: إعداد](images/phase-diagrams/setup.png#lightbox)](switch-to-mde-phase-2.md)<br/>[المرحلة الثانية: إعداد](switch-to-mde-phase-2.md) | ![المرحلة 3: Onboard](images/phase-diagrams/onboard.png#lightbox)<br/>المرحلة 3: Onboard |
|--|--|--|
|| |*أنت هنا!* |

**مرحبا بك في المرحلة 3 [من التبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)**. تتضمن مرحلة الترحيل هذه الخطوات التالية:

1. [الأجهزة المجهزة ل Defender لنقطة النهاية](#onboard-devices-to-microsoft-defender-for-endpoint).
2. [تشغيل اختبار الكشف](#run-a-detection-test).
3. [تأكد من برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على نقاط النهاية](#confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints).
4. [احصل على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender](#get-updates-for-microsoft-defender-antivirus).
5. [إلغاء تثبيت الحل غير الخاص بك من Microsoft](#uninstall-your-non-microsoft-solution).
6. [تأكد من أن Defender for Endpoint يعمل بشكل صحيح](#make-sure-defender-for-endpoint-is-working-correctly).

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>الأجهزة المجهزة Microsoft Defender لنقطة النهاية

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. اختر **الإعدادات** \> **نقاط** \> النهاية (ضمن **إدارة الأجهزة**).

3. في القائمة **تحديد نظام التشغيل لبدء عملية الضم** ، حدد نظام تشغيل.

4. ضمن **أسلوب النشر**، حدد خيارا. اتبع الارتباطات والمطالبات ل علي أجهزة مؤسستك. هل تحتاج إلى مساعدة؟ راجع [أساليب الboarding](#onboarding-methods) (في هذه المقالة).

> [!NOTE]
> إذا حدث خطأ ما أثناء التكهين، فشاهد استكشاف الأخطاء وإصلاحها Microsoft Defender لنقطة النهاية [التكعيب](troubleshoot-onboarding.md). تصف هذه المقالة كيفية حل مشاكل التكوين والأخطاء الشائعة في نقاط النهاية.

### <a name="onboarding-methods"></a>أساليب ال متنبها

> [!IMPORTANT]
> إذا كنت تستخدم Microsoft Defender for Cloud، فشاهد [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud).

تختلف أساليب النشر استنادا إلى نظام التشغيل والأساليب المفضلة. يسرد الجدول التالي الموارد لمساعدتك على ال متن الطائرة إلى Defender لنقطة النهاية:

|أنظمة التشغيل  |الأساليب  |
|---------|---------|
|Windows 10 أو أي وقت لاحق<br/><br/>Windows Server 2019 أو أي وقت لاحق<br/><br/>Windows Server، الإصدار 1803 أو الإصدارات الأحدث<br/><br/>Windows Server 2012 R2 و2016<sup>[[1](#fn1)]<sup>  |   [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md)<br><br/>   [نهج المجموعة](configure-endpoints-gp.md)<br/><br/>[Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)<br/><br/>[إدارة نقاط النهاية من Microsoft/ Mobile إدارة الجهاز (Intune)](configure-endpoints-mdm.md)<br>    [برامج VDI النصية](configure-endpoints-vdi.md) <br><br> **ملاحظة**: البرنامج النصي المحلي مناسب لإثبات المبدأ ولكن لا يجب استخدامه لنشر الإنتاج. لنشر الإنتاج، نوصي باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو Intune. |
|Windows Server 2008 R2 SP1 | [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma)  أو [Microsoft Defender for Cloud](/azure/security-center/security-center-wdatp) <br><br> **ملاحظة**: أصبح Microsoft Monitoring Agent الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة حول عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  |
|Windows 8.1 Enterprise<br/><br/>Windows 8.1 Pro<br/><br/>Windows 7 SP1 Pro<br/><br/>Windows 7 SP1| [Microsoft Monitoring Agent (MMA)](onboard-downlevel.md) <br><br> **ملاحظة**: أصبح Microsoft Monitoring Agent الآن عامل Azure Log Analytics. لمعرفة المزيد، راجع [نظرة عامة حول عامل Log Analytics](/azure/azure-monitor/platform/log-analytics-agent).  
| macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md) | [برنامج نصي محلي](mac-install-manually.md)<br/><br/>[إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md)<br/><br/>[JAMF Pro](mac-install-with-jamf.md)<br/><br/>[الأجهزة إدارة الجهاز](mac-install-with-other-mdm.md)   |
| Linux (راجع [متطلبات النظام](microsoft-defender-endpoint-linux.md#system-requirements)) |  [برنامج نصي محلي](linux-install-manually.md) <br><br/> [مهى](linux-install-with-puppet.md) <br><br/> [غير قابل للطي](linux-install-with-ansible.md)|  
| iOS | [إدارة نقاط النهاية من Microsoft](ios-install.md)     |
|Android  | [إدارة نقاط النهاية من Microsoft](android-intune.md)  | 


(<a id="fn1">1</a>) Windows Server 2016 و Windows Server 2012 R2 إلى ال متنها باستخدام الإرشادات الموجودة في [خوادم Windows على اللوحة](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016).


## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف

للتحقق من اتصال أجهزتك المجهزة بشكل صحيح ب Defender for Endpoint، يمكنك تشغيل اختبار الكشف.

<br/><br/>

|نظام التشغيل|إرشادات|
|---|---|
|Windows 10 أو أي وقت لاحق<br/><br/>Windows Server 2022<br/><br/>Windows Server 2019<br/><br/>Windows Server أو الإصدار 1803 أو الإصدارات الأحدث<br/><br/>Windows Server 2016‏<br/><br/>Windows Server 2012 R2|راجع [تشغيل اختبار الكشف](run-detection-test.md).<br/><br/>تفضل بزيارة موقع سيناريوهات العرض التوضيحي ل Defender for Endpoint (<https://demo.wd.microsoft.com>) وجرب واحدا أو أكثر من السيناريوهات. على سبيل المثال، جرب سيناريو العرض التوضيحي للحماية **التي** تم تسليمها من السحابة.|
|macOS (راجع [متطلبات النظام](microsoft-defender-endpoint-mac.md)|قم بتنزيل تطبيق DIY واستخدامه في <https://aka.ms/mdatpmacosdiy>. <br/><br/> لمزيد من المعلومات، راجع [Defender for Endpoint على macOS](microsoft-defender-endpoint-mac.md).|
|Linux (راجع [متطلبات النظام](microsoft-defender-endpoint-linux.md#system-requirements))|1. تشغيل الأمر التالي، وابحث عن نتيجة **1**: `mdatp health --field real_time_protection_enabled`.<br/><br/>2. افتح نافذة المحطة الطرفية، ثم ادير الأمر التالي: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.<br/><br/>3. تشغيل الأمر التالي لقائمة أي تهديدات تم الكشف عنها: `mdatp threat list`.<br/><br/>لمزيد من المعلومات، راجع [Defender for Endpoint على Linux](microsoft-defender-endpoint-linux.md).|

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

## <a name="confirm-that-microsoft-defender-antivirus-is-in-passive-mode-on-your-endpoints"></a>تأكد من برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على نقاط النهاية

الآن وقد تم تشغيل نقاط النهاية إلى Defender for Endpoint، فإن الخطوة التالية هي التأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي. يمكنك استخدام أحد الأساليب العديدة، كما هو موضح في الجدول التالي:

<br/><br/>

|الأسلوب|ما يجب فعله|
|---|---|
|موجه الأوامر|1. على جهاز Windows، افتح موجه الأوامر.<br/><br/>2. اكتب `sc query windefend`، ثم اضغط على Enter.<br/><br/>3. راجع النتائج للتأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي.|
|PowerShell|1. على جهاز Windows، افتح Windows PowerShell كمسؤول.<br/><br/>2. تشغيل الأمر cmdlet التالي في PowerShell: `Get-MpComputerStatus|select AMRunningMode`. <br/><br/>3. راجع النتائج. يجب أن ترى **الوضع السلبي**.|
|أمن Windows التطبيق|1. على جهاز Windows، افتح أمن Windows التطبيق.<br/><br/>2. حدد **الحماية من & الفيروسات**.<br/><br/>3. **ضمن روبوت Who أنت تحميني؟** حدد **إدارة الموفرين**.<br/><br/>4. على صفحة **موفري** الأمان، ضمن **برنامج** الحماية من الفيروسات، ابحث عن برنامج الحماية من الفيروسات من Microsoft Defender **قيد العمل**.|
|إدارة المهام|1. على جهاز Windows، افتح تطبيق إدارة المهام.<br/><br/>2. حدد **علامة التبويب** تفاصيل. ابحث عن **MsMpEng.exe** في القائمة.|

> [!NOTE]
> قد *ترى برنامج الحماية من الفيروسات لـ Windows Defender بدلا* *من برنامج الحماية من الفيروسات من Microsoft Defender* في بعض إصدارات Windows.
> لمعرفة المزيد حول الوضع السلبي ووضع النشاط، راجع مزيد من التفاصيل حول برنامج الحماية من الفيروسات من Microsoft Defender [غير النشطة](microsoft-defender-antivirus-compatibility.md#more-details-about-microsoft-defender-antivirus-states).

### <a name="set-microsoft-defender-antivirus-on-windows-server-to-passive-mode-manually"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server إلى الوضع السلبي يدويا

لتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server أو الإصدار 1803 أو الأحدث أو Windows Server 2019 أو Windows Server 2022، اتبع الخطوات التالية:

1. افتح محرر السجل، ثم انتقل إلى:

   `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. قم بتحرير (أو إنشاء) إدخال DWORD يسمى **ForceDefenderPassiveMode**، وحدد الإعدادات التالية:
   - تعيين قيمة DWORD إلى **1**.
   - ضمن **الأساس**، حدد **ست عشري**.

> [!NOTE]
> يمكنك استخدام أساليب أخرى لتعيين مفتاح التسجيل، على النحو التالي:
>
> - [نهج المجموعة التفضيل](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922(v=ws.11))
> - [أداة نهج المجموعة كائن محلي](/windows/security/threat-protection/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
> - [حزمة في Configuration Manager](/mem/configmgr/apps/deploy-use/packages-and-programs)

### <a name="start-microsoft-defender-antivirus-on-windows-server-2016"></a>بدء برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016

إذا كنت تستخدم Windows Server 2016، فقد تحتاج إلى بدء برنامج الحماية من الفيروسات من Microsoft Defender يدويا. يمكنك تنفيذ هذه المهمة باستخدام الأمر cmdlet `mpcmdrun.exe -wdenable` PowerShell على الجهاز.

## <a name="get-updates-for-microsoft-defender-antivirus"></a>الحصول على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender

إن برنامج الحماية من الفيروسات من Microsoft Defender التحديث أمر بالغ الأهمية لضمان أن أجهزتك تملك أحدث التقنيات والميزات اللازمة للحماية من البرامج الضارة وتقنيات الهجوم الجديدة، حتى لو كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي. ([راجع برنامج الحماية من الفيروسات من Microsoft Defender التوافق](microsoft-defender-antivirus-compatibility.md).)

هناك نوعان من التحديثات المتعلقة بإبقاء برنامج الحماية من الفيروسات من Microsoft Defender محدثة:

- تحديثات معلومات الأمان
- تحديثات المنتج

للحصول على التحديثات، اتبع الإرشادات في إدارة برنامج الحماية من الفيروسات من Microsoft Defender [الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="uninstall-your-non-microsoft-solution"></a>إلغاء تثبيت الحل غير الخاص بك من Microsoft

إذا كان لديك في هذه المرحلة:

- تم تعيين أجهزة مؤسستك إلى Defender for Endpoint، و
- برنامج الحماية من الفيروسات من Microsoft Defender تم تثبيته وتمكينه،

بعد ذلك، الخطوة التالية هي إلغاء تثبيت حل الحماية من الفيروسات والحماية من البرامج الضارة ونقطة النهاية غير من Microsoft. عند إلغاء تثبيت الحل غير الخاص ب Microsoft، برنامج الحماية من الفيروسات من Microsoft Defender التبديل من الوضع السلبي إلى الوضع النشط. في معظم الحالات، يحدث هذا تلقائيا. 

> [!IMPORTANT]
> إذا لم برنامج الحماية من الفيروسات من Microsoft Defender، لسبب ما، إلى الوضع النشط بعد إلغاء تثبيت حل الحماية من الفيروسات/مكافحة البرامج الضارة من Microsoft، فشاهد برنامج الحماية من الفيروسات من Microsoft Defender يبدو عالقا في الوضع غير [النشط](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

للحصول على تعليمات حول إلغاء تثبيت الحل غير الخاص ب Microsoft، اتصل بفريق الدعم التقني.

## <a name="make-sure-defender-for-endpoint-is-working-correctly"></a>تأكد من أن Defender for Endpoint يعمل بشكل صحيح

الآن بعد أن قمت بالتكوين في Defender for Endpoint، ثم قمت ب إلغاء تثبيت الحل السابق غير الخاص ب Microsoft، فإن الخطوة التالية هي التأكد من أن Defender for Endpoint يعمل بشكل صحيح. وتتمثل إحدى الطرق الجيدة لتنفيذ هذه المهمة في زيارة موقع سيناريوهات العرض التوضيحي ل Defender for Endpoint ([https://demo.wd.microsoft.com](https://demo.wd.microsoft.com)). جرب سيناريو عرض توضيحي واحدا أو أكثر على تلك الصفحة، بما في ذلك ما يلي على الأقل:

- الحماية التي يتم تسليمها من السحابة
- التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA)
- حماية الشبكة (NP)

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

## <a name="next-steps"></a>الخطوات التالية

**تهانينا**! لقد أكملت عملية [الترحيل إلى Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [تفضل بزيارة لوحة معلومات عمليات الأمان](security-operations-dashboard.md) في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)).
- [إدارة Defender لنقطة النهاية، نشر الترحيل](manage-mde-post-migration.md).
