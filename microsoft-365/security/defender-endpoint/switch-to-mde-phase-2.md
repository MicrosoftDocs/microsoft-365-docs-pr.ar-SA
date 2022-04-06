---
title: التبديل إلى Microsoft Defender لنقطة النهاية - الإعداد
description: قم بالتبديل إلى Defender لنقطة النهاية. راجع عملية الإعداد، التي تتضمن تثبيت برنامج الحماية من الفيروسات من Microsoft Defender.
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
ms.date: 04/01/2022
ms.reviewer: jesquive, chventou, jonix, chriggs, owtho
ms.openlocfilehash: 5dd5c78c366a708104b4662be86d71056d6a726a
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632700"
---
# <a name="switch-to-microsoft-defender-for-endpoint---phase-2-setup"></a>التبديل إلى Microsoft Defender لنقطة النهاية - المرحلة 2: الإعداد

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

|[![المرحلة 1: التحضير.](images/phase-diagrams/prepare.png#lightbox)](switch-to-mde-phase-1.md)<br/>[المرحلة 1: التحضير](switch-to-mde-phase-1.md)|![المرحلة 2: إعداد.](images/phase-diagrams/setup.png#lightbox)<br/>المرحلة 2: إعداد|[![المرحلة 3: Onboard3.](images/phase-diagrams/onboard.png#lightbox)](switch-to-mde-phase-3.md)<br/>[المرحلة 3: التجهيز للاستخدام](switch-to-mde-phase-3.md)|
|---|---|---|
||*أنت هنا!*||

**مرحبا بك في مرحلة الإعداد [للتبديل إلى Defender لنقطة النهاية](switch-to-mde-overview.md#the-migration-process)**. تتضمن هذه المرحلة الخطوات التالية:

1. [إعادة تثبيت/تمكين برنامج الحماية من الفيروسات من Microsoft Defender نقاط النهاية](#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).
2. [تكوين Defender لنقطة النهاية](#configure-defender-for-endpoint).
3. [أضف Defender for Endpoint إلى قائمة الاستثناء الخاصة بالحل الموجود](#add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).
4. [أضف الحل الموجود إلى قائمة الاستثناء برنامج الحماية من الفيروسات من Microsoft Defender](#add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus).
5. [قم بإعداد مجموعات الأجهزة ومجموعات الأجهزة ووحدات المؤسسة](#set-up-your-device-groups-device-collections-and-organizational-units).

## <a name="reinstallenable-microsoft-defender-antivirus-on-your-endpoints"></a>إعادة تثبيت/تمكين برنامج الحماية من الفيروسات من Microsoft Defender نقاط النهاية

في إصدارات معينة من Windows، برنامج الحماية من الفيروسات من Microsoft Defender إلغاء تثبيته أو تعطيله عند تثبيت حل مكافحة الفيروسات/مكافحة البرامج الضارة غير التابع ل Microsoft. عندما يتم Windows نقاط النهاية قيد التشغيل إلى Defender for Endpoint، برنامج الحماية من الفيروسات من Microsoft Defender تشغيلها في الوضع السلبي إلى جانب حل برنامج الحماية من الفيروسات غير Microsoft. لمعرفة المزيد، راجع [الحماية من الفيروسات باستخدام Defender ل Endpoint](microsoft-defender-antivirus-compatibility.md#antivirus-protection-without-defender-for-endpoint).

بينما تقوم بالتبديل إلى Defender for Endpoint، قد تحتاج إلى اتخاذ خطوات معينة لإعادة تثبيت أو تمكين برنامج الحماية من الفيروسات من Microsoft Defender. يصف الجدول التالي ما يجب فعله على العملاء Windows الخوادم.

|نوع نقطة النهاية|ما يجب فعله|
|---|---|
|Windows العملاء (مثل نقاط النهاية التي يتم تشغيلها Windows 10 Windows 11)|بشكل عام، لا تحتاج إلى اتخاذ أي إجراء للعملاء Windows (ما لم برنامج الحماية من الفيروسات من Microsoft Defender تثبيت). بشكل عام برنامج الحماية من الفيروسات من Microsoft Defender يجب أن يكون مثبتا، ولكن من المرجح أن يكون معطلا في هذه المرحلة من عملية الترحيل. <br/><br/> عند تثبيت حل مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft ولم يتم بعد إعادة تشغيل العملاء في Defender for Endpoint، يتم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا. في وقت لاحق، عندما يتم تشغيل نقاط نهاية العميل في Defender for Endpoint، إذا كانت نقاط النهاية هذه تقوم بتشغيل حل برنامج الحماية من الفيروسات غير Microsoft، برنامج الحماية من الفيروسات من Microsoft Defender وضع غير سلبي. <br/><br/> إذا تم إلغاء تثبيت حل الحماية من الفيروسات غير التابع ل Microsoft، برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط تلقائيا.|
|Windows الخادمة|على Windows Server، ستحتاج إلى إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender، ثم تعيينه إلى الوضع السلبي يدويا. على Windows، عند تثبيت برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft، برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب حل مكافحة الفيروسات غير Microsoft. في هذه الحالات، يتم برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته يدويا. <br/><br/> لإعادة تثبيت أو تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows الخادم، يمكنك تنفيذ المهام التالية: <br/>- [إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016](#re-enable-microsoft-defender-antivirus-on-windows-server-2016)<br/>- [إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server أو الإصدار 1803 أو إصدار أحدث](#re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later)<br/>- [تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server](#set-microsoft-defender-antivirus-to-passive-mode-on-windows-server) <br/><br/>إذا كنت تواجه مشاكل في إعادة تثبيت أو إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server، فشاهد استكشاف الأخطاء وإصلاحها: برنامج الحماية من الفيروسات من Microsoft Defender يتم إلغاء [تثبيتها Windows Server](switch-to-mde-troubleshooting.md#microsoft-defender-antivirus-is-getting-uninstalled-on-windows-server).|

> [!TIP]
> لمعرفة المزيد حول برنامج الحماية من الفيروسات من Microsoft Defender التي لا تستخدم الحماية من الفيروسات من Microsoft، [راجع برنامج الحماية من الفيروسات من Microsoft Defender التوافق](microsoft-defender-antivirus-compatibility.md).

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-2016"></a>إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016

يمكنك استخدام الأداة المساعدة Command-Line [الحماية](command-line-arguments-microsoft-defender-antivirus.md) من البرامج الضارة لإعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016.

1. كمسؤول محلي على الخادم، افتح موجه الأوامر.

2. تشغيل الأمر التالي: `MpCmdRun.exe -wdenable`

3. أعد تشغيل الجهاز.

### <a name="re-enable-microsoft-defender-antivirus-on-windows-server-version-1803-or-later"></a>إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server أو الإصدار 1803 أو الإصدارات الأحدث

> [!IMPORTANT]
> ينطبق الإجراء التالي فقط على نقاط النهاية أو الأجهزة التي تعمل بالإصدارات التالية من Windows:
> - Windows Server 2022
> - Windows Server 2019
> - Windows Server، الإصدار 1803 (الوضع الأساسي فقط)

1. كمسؤول محلي على الخادم، افتح Windows PowerShell.

2. تشغيل cmdlets التالية في PowerShell:

   ```powershell
   # For Windows Server 2016
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   Dism /online /Enable-Feature /FeatureName:Windows-Defender-Gui
   # For Windows Server 2019 and Windows Server 2022
   Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

   عند استخدام الأمر DISM ضمن تسلسل مهام يتم تشغيله في PowerShell، يكون المسار التالي cmd.exe مطلوبا.
   على سبيل المثال:

   ```powershell
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender-Features
   c:\windows\sysnative\cmd.exe /c Dism /online /Enable-Feature /FeatureName:Windows-Defender
   ```

3. أعد تشغيل الجهاز.

### <a name="set-microsoft-defender-antivirus-to-passive-mode-on-windows-server"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي على Windows Server

> [!TIP]
> يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط على Windows Server 2012 R2 و2016. لمزيد من المعلومات، راجع [خيارات تثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

1. افتح محرر السجل، ثم انتقل إلى `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.

2. قم بتحرير (أو إنشاء) إدخال DWORD يسمى **ForceDefenderPassiveMode**، وحدد الإعدادات التالية:

   - تعيين قيمة DWORD إلى **1**.

   - ضمن **الأساس**، حدد **ست عشري**.

> [!NOTE]
> بعد الboarding إلى Defender for Endpoint، قد تحتاج إلى تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى وضع غير Windows Server. للتحقق من تعيين الوضع السلبي هذا كما هو متوقع، ابحث عن الحدث *5007* في سجل تشغيل **Defender ل Microsoft-Windows-Windows** (`C:\Windows\System32\winevt\Logs`الموجود في )، وتأكد من تعيين مفتاحي التسجيل **ForceDefenderPassiveMode** أو **PassiveMode** بواسطة **0x1.**

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>هل تستخدم Windows Server 2012 R2 أو Windows Server 2016؟

يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على Windows Server 2012 R2 و2016 باستخدام الأسلوب أعلاه. لمزيد من المعلومات، راجع [خيارات تثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

## <a name="configure-defender-for-endpoint"></a>تكوين Defender لنقطة النهاية

تتضمن هذه الخطوة من عملية الترحيل تكوين برنامج الحماية من الفيروسات من Microsoft Defender نقاط النهاية. نوصي باستخدام Intune؛ ومع ذلك، يمكنك استخدام أي من الأساليب المدرجة في الجدول التالي:

|الأسلوب|ما يجب فعله|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **ملاحظة**: أصبح Intune الآن جزءا من إدارة نقاط النهاية من Microsoft.|1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft [ثم](https://go.microsoft.com/fwlink/?linkid=2109431) سجل الدخول.<br/><br/>2. حدد **ملفات تعريف** \> **تكوين الأجهزة**، ثم حدد نوع ملف التعريف الذي تريد تكوينه. إذا لم تكن قد أنشأت بعد نوع ملف تعريف  قيود الجهاز، أو إذا كنت تريد إنشاء ملف تعريف جديد، فشاهد تكوين إعدادات تقييد الجهاز في [Microsoft Intune.](/intune/device-restrictions-configure)<br/><br/>3. حدد **خصائص**، ثم حدد **إعدادات التكوين: تحرير**<br/><br/>4. **قم برنامج الحماية من الفيروسات من Microsoft Defender**.<br/><br/>5. تمكين **الحماية التي يتم تسليمها من السحابة**.<br/><br/>6. في المنسدلة **مطالبة المستخدمين قبل إرسال** العينة، حدد **إرسال كل العينات تلقائيا**.<br/><br/>7. في كشف **التطبيقات التي** يحتمل أن تكون غير مرغوب فيها، حدد **تمكين** أو **تدقيق**.<br/><br/>8. حدد **مراجعة + حفظ**، ثم اختر **حفظ**. <br/><br/> **تلميح**: لمزيد من المعلومات حول ملفات تعريف أجهزة Intune، بما في ذلك كيفية إنشاء إعداداتها وتكوينها، راجع ما [هي Microsoft Intune ملفات تعريف الأجهزة؟](/intune/device-profiles).|
|Microsoft Endpoint Configuration Manager|راجع [إنشاء سياسات مكافحة البرامج الضارة ونشرها Endpoint Protection في Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies). <br/><br/> عند إنشاء سياسات الحماية من البرامج الضارة وتكوينها، تأكد من مراجعة إعدادات الحماية في الوقت الحقيقي [](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) وتمكين الحظر [من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md).
|لوحة التحكم في Windows|اتبع الإرشادات هنا: [قم برنامج الحماية من الفيروسات من Microsoft Defender](/mem/intune/user-help/turn-on-defender-windows). (*قد ترى برنامج الحماية من الفيروسات لـ Windows Defender* بدلا *من برنامج الحماية من الفيروسات من Microsoft Defender في* بعض إصدارات Windows.)|
|[إدارة نهج المجموعة المتقدمة](/microsoft-desktop-optimization-pack/agpm/) <br/><br/> أو <br/><br/> [نهج المجموعة التحكم في الإدارة](/windows/security/threat-protection/microsoft-defender-antivirus/use-group-policy-microsoft-defender-antivirus)|1. انتقل إلى **قوالب تكوين** \>  \> الكمبيوتر الإدارية Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \> **.**<br/><br/>2. ابحث عن نهج يسمى **إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender**.<br/><br/>3. اختر **تحرير إعداد النهج**، وتأكد من تعطيل النهج. يمكن هذا الإجراء برنامج الحماية من الفيروسات من Microsoft Defender. <br/>(*قد ترى برنامج الحماية من الفيروسات لـ Windows Defender* بدلا *من برنامج الحماية من الفيروسات من Microsoft Defender في* بعض إصدارات Windows.)|

> [!TIP]
> يمكنك نشر هذه السياسات قبل أن يتم اجهزتك في الحافظة.

## <a name="add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution"></a>إضافة Microsoft Defender لنقطة النهاية إلى قائمة الاستثناء الخاصة بالحل الحالي

تتضمن هذه الخطوة من عملية الإعداد إضافة Defender for Endpoint إلى القائمة الخاصة باستثناء حل حماية نقطة النهاية الحالي وأي منتجات أمان أخرى تستخدمها مؤسستك.

> [!TIP]
> للحصول على المساعدة في تكوين الاستثناءات، راجع وثائق موفر الحل.

تعتمد الاستثناءات المعينة التي يجب تكوينها على إصدار Windows نقاط النهاية أو الأجهزة التي يتم تشغيلها، والمسرودة في الجدول التالي.
<br/><br/>

| نظام التشغيل |الاستثناءات |
|:--|:--|
|Windows 11 <br/><br/>Windows 10 الإصدار [1803](/windows/release-health/status-windows-10-1803) أو الإصدارات [الأحدث (راجع Windows 10 الإصدار)](/windows/release-health/release-information)<br/><br/>Windows 10، الإصدار 1703 أو 1709 مع [تثبيت KB4493441](https://support.microsoft.com/help/4493441) <br/><br/> Windows Server 2022<br/><br/>[Windows Server 2019](/windows/release-health/status-windows-10-1809-and-windows-server-2019) <br/><br/>[Windows Server 2016](/windows/release-health/status-windows-10-1607-and-windows-server-2016)<br/><br/>[Windows Server 2012 R2](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows Server، الإصدار 1803](/windows-server/get-started/whats-new-in-windows-server-1803) | `C:\Program Files\Windows Defender Advanced Threat Protection\MsSense.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCncProxy.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseSampleUploader.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseIR.exe`<br/><br/>`C:\Program Files\Windows Defender Advanced Threat Protection\SenseCM.exe`<br/><br/>بالإضافة إلى ذلك، في Windows Server 2012 R2 و2016 الذي يقوم بتشغيل الحل الحديث الموحد، يجب إجراء الاستثناءات التالية بعد تحديث مكون Sense الكشف التلقائي والاستجابة على النقط النهائية باستخدام [KB5005292](https://support.microsoft.com/en-us/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac):<br/> <br/> `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\MsSense.exe` <br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCnCProxy.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseIR.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCE.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseSampleUploader.exe`<br/><br/>`C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Platform\*\SenseCM.exe` |
|[Windows 8.1](/windows/release-health/status-windows-8.1-and-windows-server-2012-r2)<br/><br/>[Windows 7](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1)<br/><br/>[Windows Server 2008 R2 SP1](/windows/release-health/status-windows-7-and-windows-server-2008-r2-sp1) |`C:\Program Files\Microsoft Monitoring Agent\Agent\Health Service State\Monitoring Host Temporary Files 6\45\MsSenseS.exe`<br/><br/>**ملاحظة**: يمكن أن تكون مراقبة "الملفات المؤقتة للمضيف" 6\45 مجموعات فرعية ذات أرقام مختلفة.<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\AgentControlPanel.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HealthService.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\HSLockdown.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MOMPerfSnapshotHelper.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\MonitoringHost.exe`<br/><br/>`C:\Program Files\Microsoft Monitoring Agent\Agent\TestCloudConnection.exe` |

## <a name="add-your-existing-solution-to-the-exclusion-list-for-microsoft-defender-antivirus"></a>إضافة الحل الموجود إلى قائمة استثناءات برنامج الحماية من الفيروسات من Microsoft Defender

أثناء هذه الخطوة من عملية الإعداد، يمكنك إضافة الحل الموجود إلى برنامج الحماية من الفيروسات من Microsoft Defender الاستثناء. يمكنك الاختيار من بين عدة أساليب لإضافة الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender، كما هو مذكور في الجدول التالي: 

|الأسلوب|ما يجب فعله|
|---|---|
|[Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager) <br/><br/> **ملاحظة**: أصبح Intune الآن جزءا من إدارة نقاط النهاية من Microsoft.|1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft [ثم](https://go.microsoft.com/fwlink/?linkid=2109431) سجل الدخول.<br/><br/>2. حدد **ملفات تعريف** \> تكوين **الأجهزة**، ثم حدد ملف التعريف الذي تريد تكوينه.<br/><br/>3. ضمن **إدارة،** حدد **خصائص**.<br/><br/>4. حدد **إعدادات التكوين: تحرير**.<br/><br/>5. **قم برنامج الحماية من الفيروسات من Microsoft Defender**، ثم قم **برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات**.<br/><br/>6. حدد الملفات والمجلدات والملحقات والعمليات التي يجب استبعادها من برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. للحصول على مرجع، [راجع برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions).<br/><br/>7. اختر **مراجعة + حفظ**، ثم اختر **حفظ**.|
|[Microsoft Endpoint Configuration Manager](/mem/configmgr/)|1. باستخدام وحدة Configuration Manager [،](/mem/configmgr/core/servers/manage/admin-console) \> انتقل إلى الأصول **والتوافق** \> Endpoint Protection **نهج** مكافحة البرامج الضارة، ثم حدد النهج الذي تريد تعديله.<br/><br/>2. حدد إعدادات الاستثناء للملفات والمجلدات والملحقات والعمليات التي يجب استبعادها من برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي.|
|[نهج المجموعة كائن](/previous-versions/windows/desktop/Policy/group-policy-objects)|1. على الكمبيوتر نهج المجموعة، افتح وحدة التحكم في الإدارة نهج المجموعة، وانقر بيمين فوق نهج المجموعة الذي تريد تكوينه، ثم حدد **تحرير**.[](https://technet.microsoft.com/library/cc731212.aspx)<br/><br/>2. **في نهج المجموعة إدارة،** انتقل إلى **تكوين الكمبيوتر** وحدد **قوالب إدارية**.<br/><br/>3. قم بتوسيع الشجرة Windows **المكونات برنامج الحماية من الفيروسات من Microsoft Defender \> \> الاستثناءات**. (*قد ترى برنامج الحماية من الفيروسات لـ Windows Defender* بدلا *من برنامج الحماية من الفيروسات من Microsoft Defender في* بعض إصدارات Windows.)<br/><br/>4. انقر نقرا مزدوجا فوق **الإعداد استثناءات** المسار وأضف الاستثناءات.<br/><br/>5. تعيين الخيار إلى **تمكين**.<br/><br/>6. ضمن المقطع **خيارات** ، حدد **إظهار...**.<br/><br/>7. حدد كل مجلد على السطر الخاص به ضمن **العمود اسم** القيمة. إذا قمت بتحديد ملف، فتأكد من إدخال مسار مؤهل بالكامل إلى الملف، بما في ذلك حرف محرك الأقراص ومسار المجلد و اسم الملف والملحق. أدخل **0** في **عمود القيمة** .<br/><br/>8. حدد **موافق**.<br/><br/>9. انقر نقرا مزدوجا فوق **الإعداد استثناءات** الملحقات وأضف الاستثناءات.<br/><br/>10. تعيين الخيار إلى **تمكين**.<br/><br/>11. ضمن المقطع **خيارات** ، حدد **إظهار...**.<br/><br/>12. أدخل كل ملحق ملف على السطر الخاص به ضمن **العمود اسم** القيمة. أدخل **0** في **عمود القيمة** .<br/><br/>13. حدد **موافق**.|
|كائن نهج المجموعة المحلية|1. على نقطة النهاية أو الجهاز، افتح محرر نهج المجموعة المحلي.<br/><br/>2. انتقل إلى **قوالب تكوين** \>  \> الكمبيوتر **الإدارية Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **استثناءات**. (*قد ترى برنامج الحماية من الفيروسات لـ Windows Defender* بدلا *من برنامج الحماية من الفيروسات من Microsoft Defender في* بعض إصدارات Windows.)<br/><br/>3. حدد استثناءات المسار و العملية.|
|مفتاح التسجيل|1. تصدير مفتاح التسجيل التالي: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\exclusions`.<br/><br/>2. استيراد مفتاح التسجيل. فيما يلي مثالان:<br/>- المسار المحلي: `regedit.exe /s c:\temp\ MDAV_Exclusion.reg`<br/>- مشاركة الشبكة: `regedit.exe /s \\FileServer\ShareName\MDAV_Exclusion.reg`|

### <a name="keep-the-following-points-about-exclusions-in-mind"></a>ضع النقاط التالية حول الاستثناءات في الاعتبار

عند إضافة [استثناءات برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) عمليات الفحص، يجب إضافة استثناءات المسار و العملية.

ضع النقاط التالية في الاعتبار:

- *تستثني استثناءات المسارات* ملفات معينة وأي ملفات يمكن الوصول إليها.

- *تستثني استثناءات* العملية أي عملية تلامسها، ولكنها لا تستبعد العملية نفسها.

- سرد استثناءات العملية باستخدام مسارها الكامل وليس باسمها فقط. (أسلوب الاسم فقط أقل أمانا.)

- إذا قمت سرد كل عملية قابلة للتنفيذ (.exe) ك استثناء مسار واستبعاد عملية، يتم استبعاد العملية وأي شيء تلمسه.

## <a name="set-up-your-device-groups-device-collections-and-organizational-units"></a>إعداد مجموعات الأجهزة ومجموعات الأجهزة ووحدات المؤسسة

تمكن مجموعات الأجهزة ومجموعات الأجهزة ووحدات المؤسسة فريق الأمان من إدارة سياسات الأمان وتعيينها بكفاءة وفعالية. يصف الجدول التالي كل مجموعة من هذه المجموعات وكيفية تكوينها. قد لا تستخدم مؤسستك أنواع المجموعات الثلاثة كلها.

|نوع المجموعة|ما يجب فعله|
|---|---|
|[تمكن مجموعات](/microsoft-365/security/defender-endpoint/machine-groups) الأجهزة (التي كانت تسمى سابقا مجموعات *الأجهزة) فريق* عمليات الأمان من تكوين قدرات الأمان، مثل إجراء عمليات التحقيق التلقائية والتمكين من المعالجة. <br/><br/> كما أن مجموعات الأجهزة مفيدة أيضا لتعيين الوصول إلى هذه الأجهزة بحيث يمكن لفريق عمليات الأمان اتخاذ إجراءات المعالجة إذا لزم الأمر. <br/><br/> يتم إنشاء مجموعات الأجهزة في أثناء الكشف عن الهجوم وتوقفه، تم تشغيل التنبيهات، مثل "تنبيه الوصول الأولي"، وظهرت في مدخل Microsoft 365 Defender[.](/microsoft-365/security/defender/microsoft-365-defender)|1. انتقل إلى مدخل Microsoft 365 Defender (<https://security.microsoft.com>).<br/><br/>2. في جزء التنقل على اليمين **، اختر الإعدادات** \> **مجموعات** \>  \> أجهزة أذونات **نقاط النهاية**.<br/><br/>3. اختر **+ إضافة مجموعة أجهزة**.<br/><br/>4. حدد اسما ووصفا لمجموعة الأجهزة.<br/><br/>5. في القائمة **مستوى التنفيذ** التلقائي، حدد خيارا. (نوصي **بالتكامل - معالجة التهديدات تلقائيا**.) لمعرفة المزيد حول مستويات التنفيذ التلقائي المختلفة، راجع [كيفية معالجة التهديدات](/microsoft-365/security/defender-endpoint/automated-investigations#how-threats-are-remediated).<br/><br/>6. حدد شروط قاعدة مطابقة لتحديد الأجهزة التي تنتمي إلى مجموعة الأجهزة. على سبيل المثال، يمكنك اختيار مجال أو إصدارات نظام التشغيل أو حتى استخدام [علامات الجهاز](/microsoft-365/security/defender-endpoint/machine-tags).<br/><br/>7. في علامة **التبويب وصول المستخدم** ، حدد الأدوار التي يجب أن يكون لها حق الوصول إلى الأجهزة المضمنة في مجموعة الأجهزة.<br/><br/>8. اختر **تم**.|
|[تمكن مجموعات الأجهزة](/mem/configmgr/core/clients/manage/collections/introduction-to-collections) فريق عمليات الأمان من إدارة التطبيقات أو نشر إعدادات التوافق أو تثبيت تحديثات البرامج على الأجهزة في مؤسستك. <br/><br/> يتم إنشاء مجموعات الأجهزة [باستخدام Configuration Manager.](/mem/configmgr/)|اتبع الخطوات في [إنشاء مجموعة](/mem/configmgr/core/clients/manage/collections/create-collections#bkmk_create).|
|[تمكنك الوحدات](/azure/active-directory-domain-services/create-ou) التنظيمية من تجميع العناصر منطقيا مثل حسابات المستخدمين أو حسابات الخدمات أو حسابات الكمبيوتر. <br/><br/> يمكنك بعد ذلك تعيين المسؤولين إلى وحدات تنظيمية معينة، وتطبيق نهج المجموعة لفرض إعدادات التكوين المستهدف. <br/><br/> يتم تعريف الوحدات التنظيمية في [Azure خدمات مجال Active Directory](/azure/active-directory-domain-services).|اتبع الخطوات في [إنشاء وحدة تنظيمية في مجال Azure خدمات مجال Active Directory مدار](/azure/active-directory-domain-services/create-ou).|

## <a name="next-step"></a>الخطوة التالية

**تهانينا**! لقد أكملت مرحلة الإعداد [للتبديل إلى Defender for Endpoint](switch-to-mde-overview.md#the-migration-process)!

- [المتابعة إلى المرحلة 3: ال onboard إلى Defender لنقطة النهاية](switch-to-mde-phase-3.md)
