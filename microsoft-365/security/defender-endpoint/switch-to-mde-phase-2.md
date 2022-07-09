---
title: التبديل إلى Microsoft Defender لنقطة النهاية - الإعداد
description: قم بالتبديل إلى Defender لنقطة النهاية. راجع عملية الإعداد، والتي تتضمن تثبيت برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: الترحيل، Microsoft Defender لنقطة النهاية، برنامج الحماية من الفيروسات، الوضع السلبي، عملية الإعداد
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
ms.topic: article
ms.custom: migrationguides
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 7f22d5d1162e01afe737e6e3f25450cc22e25c76
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/09/2022
ms.locfileid: "66695715"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>التبديل إلى Microsoft Defender لنقطة النهاية - المرحلة 2: الإعداد

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![المرحلة 1: التحضير.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[المرحلة 1: التحضير](switch-to-mde-phase-1.md)|![المرحلة الثانية: الإعداد.](images/phase-diagrams/setup.png#lightbox)<br/>المرحلة 2: إعداد|[![المرحلة 3: Onboard3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[المرحلة 3: التجهيز للاستخدام](switch-to-mde-phase-3.md)|
|---|---|---|
||*أنت هنا!*||

**مرحبا بك في مرحلة الإعداد [للتبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)**. تتضمن هذه المرحلة الخطوات التالية:

1. [أعد تثبيت/تمكين برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [تكوين Defender لنقطة النهاية](#configure-defender-for-endpoint).
3. [أضف Defender لنقطة النهاية إلى قائمة الاستبعاد لحلك الحالي](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [أضف الحل الحالي إلى قائمة الاستبعاد لبرنامج الحماية من الفيروسات من Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [قم بإعداد مجموعات الأجهزة ومجموعات الأجهزة والوحدات التنظيمية](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>إعادة تثبيت/تمكين برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية

في إصدارات معينة من Windows، من المحتمل أن يكون برنامج الحماية من الفيروسات من Microsoft Defender قد تم إلغاء تثبيته أو تعطيله عند تثبيت حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft. عند إلحاق نقاط النهاية التي تعمل بنظام التشغيل Windows ب Defender لنقطة النهاية، يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي إلى جانب حل الحماية من الفيروسات غير التابع ل Microsoft. لمعرفة المزيد، راجع [الحماية من الفيروسات باستخدام Defender لنقطة النهاية](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

أثناء إجراء التبديل إلى Defender لنقطة النهاية، قد تحتاج إلى اتخاذ خطوات معينة لإعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender أو تمكينه. يصف الجدول التالي ما يجب فعله على عملاء Windows وخوادمه.

|نوع نقطة النهاية|ما يجب فعله|
|---|---|
|عملاء Windows (مثل نقاط النهاية التي تعمل Windows 10 Windows 11)|بشكل عام، لا تحتاج إلى اتخاذ أي إجراء لعملاء Windows (ما لم يتم إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender). بشكل عام، يجب أن يظل برنامج الحماية من الفيروسات من Microsoft Defender مثبتا، ولكن من المحتمل أن يكون معطلا في هذه المرحلة من عملية الترحيل. <br/><br/> عند تثبيت حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft ولم يتم إلحاق العملاء بعد ب Defender لنقطة النهاية، يتم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا. في وقت لاحق، عندما يتم إلحاق نقاط نهاية العميل ب Defender لنقطة النهاية، إذا كانت نقاط النهاية هذه تقوم بتشغيل حل الحماية من الفيروسات غير التابع ل Microsoft، فإن برنامج الحماية من الفيروسات من Microsoft Defender ينتقل إلى الوضع السلبي. <br/><br/> إذا تم إلغاء تثبيت حل الحماية من الفيروسات غير التابع ل Microsoft، ينتقل برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط تلقائيا.|
|خوادم Windows|على Windows Server، ستحتاج إلى إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender، وتعيينه إلى الوضع السلبي يدويا. على خوادم Windows، عند تثبيت برنامج الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft، لا يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب حل الحماية من الفيروسات غير التابع ل Microsoft. في هذه الحالات، يتم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته يدويا. <br/><br/> لإعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender أو تمكينه على Windows Server، قم بتنفيذ المهام التالية: <br/>- [إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server، الإصدار 1803 أو الإصدارات الأحدث](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>إذا واجهت مشاكل في إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender أو إعادة تمكينه على Windows Server، فراجع [استكشاف الأخطاء وإصلاحها: يتم إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> لمعرفة المزيد حول حالات برنامج الحماية من الفيروسات من Microsoft Defender مع الحماية من الفيروسات من غير Microsoft، راجع [التوافق مع برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016

يمكنك استخدام [الأداة المساعدة Command-Line للحماية من البرامج الضارة](command-line-arguments-microsoft-defender-antivirus.md) لإعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016.

1. كمسؤول محلي على الخادم، افتح موجه الأوامر.

2. تشغيل الأمر التالي: `MpCmdRun.exe -wdenable`

3. أعد تشغيل الجهاز.

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server، الإصدار 1803 أو الإصدارات الأحدث

> [!IMPORTANT]
> ينطبق الإجراء التالي فقط على نقاط النهاية أو الأجهزة التي تقوم بتشغيل الإصدارات التالية من Windows:
> - Windows Server 2022
> - Windows Server 2019
> - Windows Server، الإصدار 1803 (وضع الذاكرة الأساسية فقط)

1. كمسؤول محلي على الخادم، افتح Windows PowerShell.

2. تشغيل أوامر PowerShell cmdlets التالية:

   ```powershell
   # For Windows Server 2016
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Gui
   
   # For Windows Server 2019 and Windows Server 2022
   Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```

   عند استخدام الأمر DISM ضمن تسلسل مهمة يقوم بتشغيل PowerShell، المسار التالي إلى cmd.exe مطلوب.
   على سبيل المثال:

   ```powershell
   C:\Windows\System32\cmd.exe /c Dism /Online /Enable-Feature /FeatureName:Windows-Defender-Features
   C:\Windows\System32\cmd.exe /c Dism /Online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. أعد تشغيل الجهاز.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server

> [!TIP]
> يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على Windows Server 2012 R2 و2016. لمزيد من المعلومات، راجع ["خيارات" لتثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. افتح محرر السجل، ثم انتقل إلى `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. تحرير (أو إنشاء) إدخال DWORD يسمى **ForceDefenderPassiveMode**، وتحديد الإعدادات التالية:

   - تعيين قيمة DWORD إلى **1**.

   - ضمن **Base**، حدد **سداسي عشري**.

> [!NOTE]
> بعد الإلحاق ب Defender لنقطة النهاية، قد تحتاج إلى تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server. للتحقق من تعيين الوضع الخامل كما هو متوقع، ابحث عن **الحدث 5007** في السجل **التشغيلي ل Microsoft-Windows-Windows Defender** (الموجود في `C:\Windows\System32\winevt\Logs`)، وتأكد من تعيين إما مفاتيح تسجيل **ForceDefenderPassiveMode** أو **PassiveMode** إلى **0x1**.

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>هل تستخدم Windows Server 2012 R2 أو Windows Server 2016؟

يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على Windows Server 2012 R2 و2016 باستخدام الأسلوب أعلاه. لمزيد من المعلومات، راجع ["خيارات" لتثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>تكوين Defender لنقطة النهاية

تتضمن هذه الخطوة من عملية الترحيل تكوين برنامج الحماية من الفيروسات من Microsoft Defender لنقاط النهاية الخاصة بك. نوصي باستخدام Intune؛ ومع ذلك، يمكنك استخدام أي من الأساليب المدرجة في الجدول التالي:

|الاسلوب|ما يجب فعله|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **ملاحظة**: أصبح Intune الآن جزءا من Microsoft إدارة نقاط النهاية.|1. انتقل إلى [مركز إدارة Microsoft إدارة نقاط النهاية](https://go.microsoft.com/fwlink/?linkid=2109431) وسجل الدخول.<br/><br/>2. حدد **ملفات تعريف تكوين** **الأجهزة**\>، ثم حدد نوع ملف التعريف الذي تريد تكوينه. إذا لم تكن قد أنشأت بعد نوع ملف تعريف **قيود الجهاز**، أو إذا كنت تريد إنشاء ملف تعريف جديد، فراجع [تكوين إعدادات تقييد الجهاز في Microsoft Intune](/intune/device-restrictions-configure).<br/><br/>3. حدد **الخصائص**، ثم حدد **إعدادات التكوين: تحرير**<br/><br/>4. توسيع **برنامج الحماية من الفيروسات من Microsoft Defender**.<br/><br/>5. تمكين **الحماية المقدمة من السحابة**.<br/><br/>6. في **"المطالبة بالمستخدمين" قبل القائمة المنسدلة "إرسال العينة** "، حدد **"إرسال كافة العينات" تلقائيا**.<br/><br/>7. في القائمة المنسدلة **"الكشف عن التطبيقات غير المرغوب فيها"** ، حدد **"تمكين** " أو **"تدقيق**".<br/><br/>8. حدد **"مراجعة + حفظ**"، ثم اختر **"حفظ**". <br/><br/> **تلميح**: لمزيد من المعلومات حول ملفات تعريف أجهزة Intune، بما في ذلك كيفية إنشاء إعداداتها وتكوينها، راجع [ما هي ملفات تعريف الأجهزة Microsoft Intune؟](/intune/device-profiles).|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr)|راجع [إنشاء نهج مكافحة البرامج الضارة ونشرها لحماية نقطة النهاية في Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> عند إنشاء نهج مكافحة البرامج الضارة وتكوينها، تأكد من مراجعة [إعدادات الحماية في الوقت الحقيقي](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) [وتمكين الكتلة من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|لوحة التحكم في Windows|اتبع الإرشادات هنا: [قم بتشغيل برنامج الحماية من الفيروسات من Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). (قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender* في بعض إصدارات Windows.)|
|[إدارة نهج المجموعة المتقدمة](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> او <br/><br/> [وحدة تحكم إدارة نهج المجموعة](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. انتقل إلى **قوالب إدارة** **تكوين** \> الكمبيوتر مكونات \> **Windows** \> **Microsoft Defender Antivirus**.<br/><br/>2. ابحث عن نهج يسمى **إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender**.<br/><br/>3. اختر **إعداد تحرير النهج**، وتأكد من تعطيل النهج. يتيح هذا الإجراء برنامج الحماية من الفيروسات من Microsoft Defender. <br/>(قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender* في بعض إصدارات Windows.)|

> [!TIP]
> يمكنك نشر النهج قبل إلحاق أجهزة مؤسستك.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>إضافة Microsoft Defender لنقطة النهاية إلى قائمة الاستبعاد للحل الحالي

تتضمن هذه الخطوة من عملية الإعداد إضافة Defender لنقطة النهاية إلى قائمة الاستبعاد لحل حماية نقطة النهاية الحالي وأي منتجات أمان أخرى تستخدمها مؤسستك.

> [!TIP]
> للحصول على المساعدة في تكوين الاستثناءات، راجع وثائق موفر الحلول.

ستعتمد الاستثناءات المحددة التي سيتم تكوينها على إصدار Windows الذي تعمل فيه نقاط النهاية أو الأجهزة، ويتم إدراجها في الجدول التالي.

| OS |الاستثناءات |
|:--|:--|
|[Windows 11](/windows/whats-new/windows-11-overview) <br/><br/>Windows 10 أو [الإصدار 1803](/lifecycle/announcements/windows-server-1803-end-of-servicing) أو الإصدارات الأحدث (راجع [معلومات إصدار Windows 10](/windows/release-health/release-information))<br/><br/>Windows 10 أو الإصدار 1703 أو 1709 مع تثبيت [KB4493441](https://support.microsoft.com/help/4493441) <br/><br/> [Windows Server 2022](/windows/release-health/status-windows-server-2022)<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server، الإصدار 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\DataCollection`<br/><br/> بالإضافة إلى ذلك، في Windows Server 2012 R2 و2016 الذي يقوم بتشغيل الحل الحديث الموحد، تكون الاستثناءات التالية مطلوبة بعد تحديث مكون Sense EDR باستخدام [KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac):<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe`|
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**ملاحظة**: يمكن أن تكون مراقبة الملفات المؤقتة للمضيف 6\45 مجلدات فرعية ذات تعداد رقمي مختلفة.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>إضافة الحل الموجود إلى قائمة الاستبعاد لبرنامج الحماية من الفيروسات من Microsoft Defender

أثناء هذه الخطوة من عملية الإعداد، يمكنك إضافة الحل الحالي إلى قائمة استبعاد برنامج الحماية من الفيروسات من Microsoft Defender. يمكنك الاختيار من بين عدة طرق لإضافة استثناءاتك إلى برنامج الحماية من الفيروسات من Microsoft Defender، كما هو مذكور في الجدول التالي: 

|الاسلوب|ما يجب فعله|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **ملاحظة**: أصبح Intune الآن جزءا من Microsoft إدارة نقاط النهاية.|1. انتقل إلى [مركز إدارة Microsoft إدارة نقاط النهاية](https://go.microsoft.com/fwlink/?linkid=2109431) وسجل الدخول.<br/><br/>2. حدد **ملفات تعريف تكوين** **الأجهزة**\>، ثم حدد ملف التعريف الذي تريد تكوينه.<br/><br/>3. ضمن **"إدارة**"، حدد **"خصائص**".<br/><br/>4. حدد **إعدادات التكوين: تحرير**.<br/><br/>5. قم بتوسيع **برنامج الحماية من الفيروسات من Microsoft Defender**، ثم قم بتوسيع **استثناءات برنامج الحماية من الفيروسات من Microsoft Defender**.<br/><br/>6. حدد الملفات والمجلدات والملحقات والعمليات التي يجب استبعادها من عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender. للرجوع إليها، راجع [استثناءات برنامج الحماية من الفيروسات من Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. اختر **"مراجعة + حفظ**"، ثم اختر **"حفظ**".|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. باستخدام [وحدة التحكم Configuration Manager](/mem/configmgr/core/servers/manage/admin-console)، انتقل إلى نهج **الحماية**\> من البرامج الضارة في **نقطة النهاية** للأصول **والامتثال**\>، ثم حدد النهج الذي تريد تعديله.<br/><br/>2. حدد إعدادات الاستثناء للملفات والمجلدات والملحقات والعمليات التي يجب استبعادها من عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender.|
|[كائن نهج المجموعة](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](https://technet.microsoft.com/library/cc731212.aspx)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه ثم حدد **"تحرير**".<br/><br/>2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.<br/><br/>3. قم بتوسيع الشجرة إلى **مكونات \> Windows استثناءات برنامج الحماية من الفيروسات \> من Microsoft Defender**. (قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender* في بعض إصدارات Windows.)<br/><br/>4. انقر نقرا مزدوجا فوق إعداد **"استثناءات المسار"** وأضف الاستثناءات.<br/><br/>5. تعيين الخيار إلى **ممكن**.<br/><br/>6. ضمن المقطع **"خيارات** "، حدد **"إظهار...**".<br/><br/>7. حدد كل مجلد على السطر الخاص به ضمن عمود **اسم القيمة** . إذا قمت بتحديد ملف، فتأكد من إدخال مسار مؤهل بالكامل إلى الملف، بما في ذلك حرف محرك الأقراص ومسار المجلد واسم الملف والملحق. أدخل **0** في عمود **"القيمة** ".<br/><br/>8. حدد **"موافق**".<br/><br/>9. انقر نقرا مزدوجا فوق إعداد " **استثناءات** الملحق" وأضف الاستثناءات.<br/><br/>10. تعيين الخيار إلى **ممكن**.<br/><br/>11. ضمن المقطع **"خيارات** "، حدد **"إظهار...**".<br/><br/>12. أدخل كل ملحق ملف على السطر الخاص به ضمن عمود **اسم القيمة** . أدخل **0** في عمود **"القيمة** ".<br/><br/>13. حدد **"موافق**".|
|كائن نهج المجموعة المحلية|1. على نقطة النهاية أو الجهاز، افتح محرر نهج المجموعة المحلي.<br/><br/>2. انتقل إلى **قوالب** \> إدارة **تكوين** \> الكمبيوتر Windows **Components** \> **Microsoft Defender Antivirus** \> **Exclusions**. (قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender* في بعض إصدارات Windows.)<br/><br/>3. حدد المسار واستثناءات العملية.|
|مفتاح التسجيل|1. تصدير مفتاح التسجيل التالي: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. استيراد مفتاح التسجيل. فيما يلي مثالان:<br/>- المسار المحلي: `regedit.exe /s c:\temp\MDAV_Exclusion.reg`<br/>- مشاركة الشبكة: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>ضع النقاط التالية حول الاستثناءات في الاعتبار

عند إضافة [استثناءات إلى عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus)، يجب إضافة استثناءات المسار والعمليات.

ضع النقاط التالية في الاعتبار:

- تستبعد *استثناءات المسار* ملفات معينة وأي ملفات يمكن الوصول إليها.
- تستبعد *استثناءات العملية* أي شيء تلامسه العملية، ولكنها لا تستبعد العملية نفسها.
- سرد استثناءات العملية باستخدام مسارها الكامل وليس باسمها فقط. (أسلوب الاسم فقط أقل أمانا.)
- إذا قمت بإدراج كل قابل للتنفيذ (.exe) كاستبعاد مسار واستبعاد عملية، يتم استبعاد العملية وأي شيء يتم لمسه.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>إعداد مجموعات الأجهزة ومجموعات الأجهزة والوحدات التنظيمية

تمكن مجموعات الأجهزة ومجموعات الأجهزة والوحدات التنظيمية فريق الأمان لديك من إدارة نهج الأمان وتعيينها بكفاءة وفعالية. يصف الجدول التالي كل مجموعة من هذه المجموعات وكيفية تكوينها. قد لا تستخدم مؤسستك كافة أنواع المجموعات الثلاثة.

|نوع المجموعة|ما يجب فعله|
|---|---|
|تمكن [مجموعات الأجهزة](/microsoft-365/security/defender-endpoint/machine-groups) (التي كانت تسمى سابقا *مجموعات الأجهزة*) فريق عمليات الأمان من تكوين قدرات الأمان، مثل التحقيق التلقائي والمعالجة. <br/><br/> مجموعات الأجهزة مفيدة أيضا لتعيين الوصول إلى تلك الأجهزة بحيث يمكن لفريق عمليات الأمان اتخاذ إجراءات المعالجة إذا لزم الأمر. <br/><br/> يتم إنشاء مجموعات الأجهزة في أثناء الكشف عن الهجوم وتوقفه، تم تشغيل التنبيهات، مثل "تنبيه الوصول الأولي"، وظهرت في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).|1. انتقل إلى مدخل Microsoft 365 Defender (<https://security.microsoft.com>).<br/><br/>2. في جزء التنقل على اليسار، اختر **مجموعات** **أجهزة أذونات** **نقاط النهاية** **للإعدادات** \> \> \>.<br/><br/>3. اختر **+ إضافة مجموعة أجهزة**.<br/><br/>4. حدد اسما ووصفا لمجموعة الأجهزة.<br/><br/>5. في قائمة **مستوى التنفيذ التلقائي** ، حدد خيارا. (نوصي **بالمعالجة الكاملة - معالجة التهديدات تلقائيا**.) لمعرفة المزيد حول مستويات الأتمتة المختلفة، راجع [كيفية معالجة التهديدات](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. حدد شروط قاعدة مطابقة لتحديد الأجهزة التي تنتمي إلى مجموعة الأجهزة. على سبيل المثال، يمكنك اختيار مجال أو إصدارات نظام التشغيل أو حتى استخدام [علامات الجهاز](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. في علامة التبويب **"وصول المستخدم** "، حدد الأدوار التي يجب أن يكون لها حق الوصول إلى الأجهزة المضمنة في مجموعة الأجهزة.<br/><br/>8. اختر **"تم**".|
|تمكن [مجموعات الأجهزة](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) فريق عمليات الأمان من إدارة التطبيقات أو نشر إعدادات التوافق أو تثبيت تحديثات البرامج على الأجهزة في مؤسستك. <br/><br/> يتم إنشاء مجموعات الأجهزة باستخدام [Configuration Manager](/mem/configmgr/).|اتبع الخطوات [الواردة في إنشاء مجموعة](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|تمكنك [الوحدات التنظيمية](/azure/active-directory-domain-services/create-ou) من تجميع العناصر منطقيا مثل حسابات المستخدمين أو حسابات الخدمة أو حسابات الكمبيوتر. <br/><br/> يمكنك بعد ذلك تعيين المسؤولين إلى وحدات تنظيمية معينة، وتطبيق نهج المجموعة لفرض إعدادات التكوين المستهدفة. <br/><br/> يتم تعريف الوحدات التنظيمية في [Azure خدمات مجال Active Directory](/azure/active-directory-domain-services).|اتبع الخطوات في [إنشاء وحدة تنظيمية في مجال مدار خدمات مجال Active Directory Azure](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>الخطوة التالية

**تهانينا**! لقد أكملت مرحلة الإعداد [للتبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)!

- [المتابعة إلى المرحلة 3: إلحاق Defender بنقطة النهاية](switch-to-mde-phase-3.md)
