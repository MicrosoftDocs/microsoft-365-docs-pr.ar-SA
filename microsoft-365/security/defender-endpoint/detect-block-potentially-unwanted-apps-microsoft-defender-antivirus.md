---
title: حظر التطبيقات التي قد تكون غير مرغوب فيها باستخدام برنامج الحماية من الفيروسات من Microsoft Defender
description: تمكين ميزة الحماية من الفيروسات (PUA) للتطبيقات غير المرغوب فيها لحظر البرامج غير المرغوب فيها مثل البرامج الضارة.
keywords: pua، تمكين، البرامج غير المرغوب فيها، التطبيقات غير المرغوب فيها، البرامج الضارة، شريط أدوات المستعرض، الكشف، الحظر، برنامج الحماية من الفيروسات من Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: detect
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
audience: ITPro
ms.reviewer: mimilone, julih
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: m365-security-compliance
ms.openlocfilehash: b193279f9891badc78e639776a57a366a0fa8109
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63574258"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)

التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA) هي فئة من البرامج التي يمكن أن تتسبب في تشغيل جهازك ببطء، أو عرض إعلانات غير متوقعة، أو في أسوأ الأحوال، تثبيت برامج أخرى قد تكون غير متوقعة أو غير مرغوب فيها. لا يعتبر PUA فيروسا أو برامج ضارة أو أي نوع آخر من التهديدات، ولكنه قد ينفذ إجراءات على نقاط النهاية تؤثر سلبا على أداء نقطة النهاية أو استخدامها. يمكن أن يشير *مصطلح PUA* أيضا إلى تطبيق بسمعة سيئة، كما تم تقييمه بواسطة Microsoft Defender ل Endpoint، نظرا لأنواع معينة من السلوك غير المرغوب فيه.

فيما يلي بعض الأمثلة:

- **البرامج الإعلانية** التي تعرض الإعلانات أو العروض الترويجية، بما في ذلك البرامج التي تدرج إعلانات إلى صفحات الويب.
- **تجميع البرامج التي** تعرض تثبيت برامج أخرى لم يتم توقيعها رقميا من قبل الكيان نفسه. بالإضافة إلى ذلك، البرامج التي تعرض تثبيت برامج أخرى مؤهلة ك PUA.
- **برنامج التجنب الذي** يحاول جاهدا التجنب من الكشف بواسطة منتجات الأمان، بما في ذلك البرامج التي تعمل بشكل مختلف في حالة وجود منتجات الأمان.

> [!TIP]
> للحصول على مزيد من الأمثلة ومناقشة المعايير التي نستخدمها لتسمية التطبيقات لاهتمام خاص من ميزات الأمان، راجع كيفية تحديد Microsoft للبرامج الضارة والتطبيقات التي يحتمل أن تكون [غير مرغوب فيها](/windows/security/threat-protection/intelligence/criteria).

يمكن للتطبيقات غير المرغوب فيها أن تزيد من خطر إصابة شبكتك بالبرامج الضارة الفعلية، أو تجعل عملية إصابتك بالبرامج الضارة صعبة التعريف، أو تهدر موارد المعلومات في تنظيفها. يتم دعم حماية PUA على Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2022 و Windows Server 2016. في Windows 10 (الإصدار 2004 والإصدارات الأحدث)، برنامج الحماية من الفيروسات من Microsoft Defender التطبيقات التي تعتبر PUA للأجهزة الخاصة بالمؤسسة (E5) بشكل افتراضي.

## <a name="microsoft-edge"></a>Microsoft Edge

[وتحظر Microsoft Edge](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea) الجديدة المستندة إلى Chromium تنزيلات التطبيقات غير المرغوب فيها أو عناوين URL للموارد المقترنة بها. يتم توفير هذه [الميزة عبر Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>تمكين حماية PUA في Chromium المستندة إلى Microsoft Edge

على الرغم من أن الحماية غير المرغوب فيها للتطبيقات في Microsoft Edge (المستندة إلى Chromium، يتم إيقاف تشغيل الإصدار 80.0.361.50) بشكل افتراضي، إلا أنه يمكن تشغيله بسهولة من داخل المستعرض.

1. في مستعرض Edge، حدد البقصاصات، **ثم اختر الإعدادات**.

2. حدد **الخصوصية والبحث والخدمات**.

3. ضمن قسم **الأمان** ، قم تشغيل **حظر التطبيقات التي قد تكون غير مرغوب فيها**.

> [!TIP]
> إذا كنت تقوم بتشغيل Microsoft Edge (Chromium مستندة إلى)، يمكنك استكشاف ميزة حظر URL لحماية PUA بأمان عن طريق اختبارها على إحدى صفحات العرض [Microsoft Defender SmartScreen التوضيحية](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>حظر عناوين URL مع Microsoft Defender SmartScreen

في Chromium Edge المستندة إلى PUA مع تشغيل الحماية Microsoft Defender SmartScreen تحميك من عناوين URL المقترنة ب PUA.

يمكن [لمسؤولي الأمان تكوين](/DeployEdge/configure-microsoft-edge) Microsoft Edge Microsoft Defender SmartScreen العمل معا لحماية مجموعات المستخدمين من عناوين URL المقترنة ب PUA. هناك العديد من [إعدادات نهج](/DeployEdge/microsoft-edge-policies#smartscreen-settings) المجموعة بشكل صريح Microsoft Defender SmartScreen المتوفرة، بما في ذلك [أحدها لحظر PUA](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). بالإضافة إلى ذلك، يمكن للمسؤولين [Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) بشكل عام، باستخدام إعدادات نهج المجموعة Microsoft Defender SmartScreen أو إيقاف تشغيلها.

على الرغم من أن Microsoft Defender ل Endpoint لديه قائمة حظر خاصة به استنادا إلى مجموعة بيانات مدارة بواسطة Microsoft، إلا أنه يمكنك تخصيص هذه القائمة استنادا إلى معلومات المخاطر الخاصة بك. إذا قمت [بإنشاء مؤشرات](manage-indicators.md) وإدارتها في مدخل Microsoft Defender لنقطة النهاية، Microsoft Defender SmartScreen الإعدادات الجديدة.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>برنامج الحماية من الفيروسات من Microsoft Defender الحماية من البقاع و PUA

يمكن لميزاة حماية التطبيق (PUA) غير المرغوب فيها برنامج الحماية من الفيروسات من Microsoft Defender الكشف عن PUA وحظرها على نقاط النهاية في شبكتك.

> [!NOTE]
> تتوفر هذه الميزة في Windows 10 و Windows 11 و Windows Server 2019 و Windows Server 2022 و Windows Server 2016.

برنامج الحماية من الفيروسات من Microsoft Defender تم الكشف عن ملفات PUA وأي محاولات لتنزيلها أو نقلها أو تشغيلها أو تثبيتها. بعد ذلك، يتم نقل ملفات PUA المحظورة إلى الفحص. عند اكتشاف ملف PUA في نقطة نهاية، يرسل برنامج الحماية من الفيروسات من Microsoft Defender إعلاما إلى [المستخدم (ما](configure-notifications-microsoft-defender-antivirus.md) لم يتم تعطيل الإعلامات بنفس التنسيق الذي تم به الكشف عن المخاطر الأخرى. يتم تقديم الإعلام للإشارة `PUA:` إلى محتواه.

يظهر الإعلام في قائمة الفحص [العادية داخل أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>تكوين حماية PUA في برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك تمكين حماية PUA باستخدام [Microsoft Intune أو](/mem/intune/protect/device-protect) [Microsoft Endpoint Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection) أو نهج المجموعة أو عبر [PowerShell cmdlets](/powershell/module/defender/?preserve-view=true&view=win10-ps). [](/azure/active-directory-domain-services/manage-group-policy)

يمكنك أيضا استخدام حماية PUA في وضع التدقيق للكشف عن التطبيقات التي قد تكون غير مرغوب فيها دون حظرها. يتم تسجيل الاكتشافات في Windows الأحداث.

> [!TIP]
> تفضل بزيارة موقع العرض التوضيحي ل Microsoft Defender ل Endpoint [على](https://demo.wd.microsoft.com/Page/UrlRep) demo.wd.microsoft.com للتأكد من أن الميزة تعمل، وشاهدها في وضع العمل.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

تكون حماية PUA في وضع التدقيق مفيدة إذا كانت شركتك تجري فحصا داخليا لتوافق أمان البرامج وتود تجنب أي نتائج إيجابية خاطئة.

### <a name="use-intune-to-configure-pua-protection"></a>استخدام Intune لتكوين حماية PUA

راجع [تكوين إعدادات تقييد](/intune/device-restrictions-configure) الجهاز في Microsoft Intune برنامج الحماية من الفيروسات من Microsoft Defender إعدادات تقييد الجهاز Windows 10 [Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) للحصول على مزيد من التفاصيل.

### <a name="use-configuration-manager-to-configure-pua-protection"></a>استخدام "إدارة التكوين" لتكوين حماية PUA

يتم تمكين حماية PUA بشكل افتراضي في إدارة نقاط النهاية من Microsoft (الفرع الحالي).

راجع [كيفية إنشاء سياسات](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) مكافحة البرامج الضارة ونشرها: إعدادات الفحص المجدول للحصول على تفاصيل حول إدارة نقاط النهاية من Microsoft (الفرع الحالي).

للحصول System Center 2012 التكوين، راجع كيفية نشر نهج حماية التطبيقات غير المرغوب فيه Endpoint Protection [إدارة التكوين](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> يتم برنامج الحماية من الفيروسات من Microsoft Defender أحداث PUA التي تم حظرها بواسطة Windows "عارض الأحداث" وليس في Microsoft Endpoint Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>استخدام "نهج المجموعة" لتكوين حماية PUA

1. تنزيل القوالب [الإدارية (admx.) وتثبيتها Windows 10 تحديث أكتوبر 2020 (20H2)](https://www.microsoft.com/download/details.aspx?id=102157)

2. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. حدد كائن نهج المجموعة الذي تريد تكوينه، ثم اختر **تحرير**.

4. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

5. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \> **.**

6. انقر نقرا **مزدوجا فوق تكوين الكشف للتطبيقات التي قد تكون غير مرغوب فيها**.

7. حدد **تمكين** لتمكين حماية PUA.

8. في **خيارات**، حدد **حظر** لحظر التطبيقات التي يحتمل أن تكون غير مرغوب فيها، أو حدد وضع **التدقيق** لاختبار كيفية عمل الإعداد في بيئتك. حدد **موافق**.

9. نشر كائن "نهج المجموعة" كما تفعل عادة.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>استخدام PowerShell cmdlets لتكوين حماية PUA

#### <a name="to-enable-pua-protection"></a>لتمكين حماية PUA

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

تعيين قيمة الأمر cmdlet هذا `Enabled` لكي يتم تشغيل الميزة إذا تم تعطيلها.

#### <a name="to-set-pua-protection-to-audit-mode"></a>لتعيين حماية PUA إلى وضع التدقيق

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

يكشف `AuditMode` الإعداد عن PUAs دون حظرها.

#### <a name="to-disable-pua-protection"></a>لتعطيل حماية PUA

نوصي بإبقاء حماية PUA في وضع تشغيل. ومع ذلك، يمكنك إيقاف تشغيله باستخدام الأمر cmdlet التالي:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

تعيين قيمة الأمر cmdlet هذا `Disabled` ل إيقاف تشغيل الميزة إذا تم تمكينها.

لمزيد من المعلومات، راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets و Defender Antivirus وتشغيلها](/powershell/module/defender/index).

## <a name="view-pua-events-using-powershell"></a>عرض أحداث PUA باستخدام PowerShell

يتم التقارير عن أحداث PUA في Windows الحدث، ولكن ليس في إدارة نقاط النهاية من Microsoft أو Intune. يمكنك أيضا استخدام `Get-MpThreat` أمر cmdlet لعرض التهديدات التي برنامج الحماية من الفيروسات من Microsoft Defender بها. فيما يلي مثال على ذلك:

```console
CategoryID       : 27
DidThreatExecute : False
IsActive         : False
Resources        : {webfile:_q:\Builds\Dalton_Download_Manager_3223905758.exe|http://d18yzm5yb8map8.cloudfront.net/
                    fo4yue@kxqdw/Dalton_Download_Manager.exe|pid:14196,ProcessStart:132378130057195714}
RollupStatus     : 33
SchemaVersion    : 1.0.0.0
SeverityID       : 1
ThreatID         : 213927
ThreatName       : PUA:Win32/InstallCore
TypeID           : 0
PSComputerName   :
```

## <a name="get-email-notifications-about-pua-detections"></a>الحصول على إعلامات بالبريد الإلكتروني حول اكتشافات PUA

يمكنك تشغيل إعلامات البريد الإلكتروني لتلقي البريد حول اكتشافات PUA.

راجع [استكشاف مشاكل أحداثك وإصلاحها](troubleshoot-microsoft-defender-antivirus.md) للحصول على تفاصيل حول عرض برنامج الحماية من الفيروسات من Microsoft Defender الأحداث. يتم تسجيل أحداث PUA ضمن "الم ID **الحدث 1160**".

## <a name="view-pua-events-using-advanced-hunting"></a>عرض أحداث PUA باستخدام الصيد المتقدم

إذا كنت تستخدم [Microsoft Defender لنقطة](microsoft-defender-endpoint.md) النهاية، يمكنك استخدام استعلام بحث متقدم لعرض أحداث PUA. فيما يلي استعلام مثال:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

لمعرفة المزيد حول الصيد المتقدم، راجع البحث بشكل استباقي عن [التهديدات بالصيد المتقدم](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>استبعاد الملفات من حماية PUA

في بعض الأحيان يتم حظر الملف بشكل غير صحيح بواسطة حماية PUA، أو تكون ميزة PUA مطلوبة لإكمال مهمة. في هذه الحالات، يمكن إضافة ملف إلى قائمة استثناء.

لمزيد من المعلومات، راجع تكوين الاستثناءات والتحقق من [صحتها استنادا إلى ملحق الملف وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

## <a name="see-also"></a>راجع أيضًا

- [حماية الجيل التالي](microsoft-defender-antivirus-in-windows-10.md)
- [تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md)
