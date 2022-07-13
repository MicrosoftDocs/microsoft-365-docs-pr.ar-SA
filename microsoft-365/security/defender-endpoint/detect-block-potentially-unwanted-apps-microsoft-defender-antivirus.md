---
title: حظر التطبيقات التي يحتمل أن تكون غير مرغوب فيها باستخدام برنامج الحماية من الفيروسات من Microsoft Defender
description: تمكين ميزة الحماية من الفيروسات (PUA) للتطبيق غير المرغوب فيه لحظر البرامج غير المرغوب فيها مثل البرامج الضارة.
keywords: pua, enable, unwanted software, unwanted apps, adware, browser toolbar, detect, block, Microsoft Defender Antivirus
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
ms.collection: m365-security-compliance
ms.openlocfilehash: 43cb2c4230bd48260ecd1cf4e4f6f92518a47b43
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747912"
---
# <a name="detect-and-block-potentially-unwanted-applications"></a>الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Edge](/microsoft-edge/deploy/microsoft-edge)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA) هي فئة من البرامج التي يمكن أن تتسبب في تشغيل جهازك ببطء، أو عرض إعلانات غير متوقعة، أو في أسوأ الأحوال، تثبيت برامج أخرى قد تكون غير متوقعة أو غير مرغوب فيها. لا يعتبر PUA فيروسا أو برنامجا ضارا أو نوعا آخر من التهديدات، ولكنه قد ينفذ إجراءات على نقاط النهاية التي تؤثر سلبا على أداء نقطة النهاية أو استخدامها. يمكن أن يشير مصطلح *PUA* أيضا إلى تطبيق له سمعة سيئة، كما تم تقييمه من قبل Microsoft Defender لنقطة النهاية، بسبب أنواع معينة من السلوك غير المرغوب فيه.

فيما يلي بعض الأمثلة:

- **البرامج الإعلانية** التي تعرض الإعلانات أو العروض الترويجية، بما في ذلك البرامج التي تدرج إعلانات إلى صفحات الويب.
- **تجميع البرامج** التي تقدم لتثبيت برامج أخرى لم يتم توقيعها رقميا من قبل نفس الكيان. أيضا، البرامج التي تقدم لتثبيت برامج أخرى مؤهلة ك PUA.
- **برنامج التجنب** الذي يحاول بنشاط الكشف عن طريق منتجات الأمان، بما في ذلك البرامج التي تتصرف بشكل مختلف في وجود منتجات الأمان.

> [!TIP]
> لمزيد من الأمثلة ومناقشة المعايير التي نستخدمها لتسمية التطبيقات بعناية خاصة من ميزات الأمان، راجع [كيفية تحديد Microsoft للبرامج الضارة والتطبيقات التي يحتمل أن تكون غير مرغوب فيها](/windows/security/threat-protection/intelligence/criteria).

يمكن للتطبيقات غير المرغوب فيها أن تزيد من خطر إصابة شبكتك بالبرامج الضارة الفعلية، أو تجعل من الصعب تحديد عدوى البرامج الضارة، أو تكلف فرق تكنولوجيا المعلومات والأمان الوقت والجهد لتنظيفها. يتم دعم حماية PUA على Windows 11 Windows 10 وWindows Server 2022 وWindows Server 2019 وWindows Server 2016. إذا كان اشتراك مؤسستك يتضمن [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md)، يحظر برنامج الحماية من الفيروسات من Microsoft Defender التطبيقات التي تعتبر PUA بشكل افتراضي على أجهزة Windows. 

[تعرف على المزيد حول اشتراكات Windows Enterprise](https://www.microsoft.com/microsoft-365/windows/windows-11-enterprise).

## <a name="microsoft-edge"></a>Microsoft Edge

يحظر [Microsoft Edge الجديد](https://support.microsoft.com/microsoft-edge/get-to-know-microsoft-edge-3f4bb0ff-58de-2188-55c0-f560b7e20bea)، المستند إلى Chromium، تنزيلات التطبيقات التي يحتمل أن تكون غير مرغوب فيها وعناوين URL للموارد المرتبطة بها. يتم توفير هذه الميزة عبر [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview).

### <a name="enable-pua-protection-in-chromium-based-microsoft-edge"></a>تمكين حماية PUA في Microsoft Edge المستند إلى Chromium

على الرغم من إيقاف تشغيل حماية التطبيقات غير المرغوب فيها في Microsoft Edge (المستندة إلى Chromium، الإصدار 80.0.361.50) بشكل افتراضي، إلا أنه يمكن تشغيلها بسهولة من داخل المستعرض.

1. في مستعرض Edge، حدد علامات الحذف، ثم اختر **"إعدادات**".

2. حدد **الخصوصية والبحث والخدمات**.

3. ضمن قسم **"الأمان** "، قم بتشغيل **"حظر التطبيقات التي يحتمل أن تكون غير مرغوب فيها**".

> [!TIP]
> إذا كنت تقوم بتشغيل Microsoft Edge (المستند إلى Chromium)، يمكنك استكشاف ميزة حظر عنوان URL لحماية PUA بأمان عن طريق اختبارها على إحدى [صفحات العرض التوضيحي ل Microsoft Defender SmartScreen](https://demo.smartscreen.msft.net/).

### <a name="block-urls-with-microsoft-defender-smartscreen"></a>حظر عناوين URL باستخدام Microsoft Defender SmartScreen

في Edge المستند إلى Chromium مع تشغيل حماية PUA، يحميك Microsoft Defender SmartScreen من عناوين URL المقترنة ب PUA.

يمكن لمسؤولي الأمان [تكوين](/DeployEdge/configure-microsoft-edge) كيفية عمل Microsoft Edge وMicrosoft Defender SmartScreen معا لحماية مجموعات المستخدمين من عناوين URL المقترنة ب PUA. تتوفر العديد من [إعدادات نهج المجموعة](/DeployEdge/microsoft-edge-policies#smartscreen-settings) بشكل صريح ل Microsoft Defender SmartScreen، بما في ذلك [إعدادات لحظر PUA](/DeployEdge/microsoft-edge-policies#smartscreenpuaenabled). بالإضافة إلى ذلك، يمكن للمسؤولين [تكوين Microsoft Defender SmartScreen](/microsoft-edge/deploy/available-policies?source=docs#configure-windows-defender-smartscreen) ككل، باستخدام إعدادات نهج المجموعة لتشغيل Microsoft Defender SmartScreen أو إيقاف تشغيله.

على الرغم من أن Microsoft Defender لنقطة النهاية لديه قائمة حظر خاصة به استنادا إلى مجموعة بيانات تديرها Microsoft، يمكنك تخصيص هذه القائمة استنادا إلى التحليل الذكي للمخاطر الخاصة بك. إذا قمت [بإنشاء المؤشرات وإدارتها](manage-indicators.md) في مدخل Microsoft Defender لنقطة النهاية، فإن Microsoft Defender SmartScreen تحترم الإعدادات الجديدة.

## <a name="microsoft-defender-antivirus-and-pua-protection"></a>حماية Microsoft Defender Antivirus و PUA

يمكن لميزة حماية التطبيق (PUA) غير المرغوب فيها في برنامج الحماية من الفيروسات من Microsoft Defender الكشف عن PUA ومنعه على نقاط النهاية في شبكتك.

> [!NOTE]
> تتوفر هذه الميزة في Windows 11 Windows 10 وWindows Server 2022 وWindows Server 2019 وWindows Server 2016.

اكتشفت كتل برنامج الحماية من الفيروسات من Microsoft Defender ملفات PUA وأي محاولات لتنزيلها أو نقلها أو تشغيلها أو تثبيتها. ثم يتم نقل ملفات PUA المحظورة إلى العزل. عند اكتشاف ملف PUA على نقطة نهاية، يرسل برنامج الحماية من الفيروسات من Microsoft Defender إعلاما إلى المستخدم ([ما لم يتم تعطيل الإعلامات](configure-notifications-microsoft-defender-antivirus.md) بنفس تنسيق عمليات الكشف عن التهديدات الأخرى. يتم تمهيد `PUA:` الإعلام للإشارة إلى محتواه.

يظهر الإعلام في [قائمة العزل المعتادة داخل تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).

## <a name="configure-pua-protection-in-microsoft-defender-antivirus"></a>تكوين حماية PUA في برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك تمكين حماية PUA باستخدام [Microsoft Intune](/mem/intune/protect/device-protect) [أو نقطة نهاية Microsoft Configuration Manager](/mem/configmgr/protect/deploy-use/endpoint-protection) [أو نهج المجموعة](/azure/active-directory-domain-services/manage-group-policy) أو عبر [PowerShell cmdlets](/powershell/module/defender/?preserve-view=true&view=win10-ps).

يمكنك أيضا استخدام حماية PUA في وضع التدقيق للكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها دون حظرها. يتم تسجيل عمليات الكشف في سجل أحداث Windows. تعد حماية PUA في وضع التدقيق مفيدة إذا كانت شركتك تجري فحصا داخليا لتوافق أمان البرامج وكنت ترغب في تجنب أي إيجابيات خاطئة.

### <a name="use-intune-to-configure-pua-protection"></a>استخدام Intune لتكوين حماية PUA

راجع [تكوين إعدادات تقييد الجهاز في إعدادات](/intune/device-restrictions-configure) [تقييد جهاز Microsoft Intune وMicrosoft Defender Antivirus Windows 10 في Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) للحصول على مزيد من التفاصيل.

### <a name="use-configuration-manager-to-configure-pua-protection"></a>استخدام Configuration Manager لتكوين حماية PUA

يتم تمكين حماية PUA بشكل افتراضي في Microsoft إدارة نقاط النهاية (الفرع الحالي).

راجع [كيفية إنشاء نهج مكافحة البرامج الضارة ونشرها: إعدادات الفحص المجدول](/configmgr/protect/deploy-use/endpoint-antimalware-policies#real-time-protection-settings) للحصول على تفاصيل حول تكوين Microsoft إدارة نقاط النهاية (الفرع الحالي).

للحصول على Configuration Manager System Center 2012، راجع [كيفية نشر نهج حماية التطبيقات غير المرغوب فيه لحماية نقطة النهاية في Configuration Manager](/previous-versions/system-center/system-center-2012-R2/hh508770(v=technet.10)#BKMK_PUA).

> [!NOTE]
> يتم الإبلاغ عن أحداث PUA المحظورة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender في عارض الأحداث Windows وليس في نقطة نهاية Microsoft Configuration Manager.

### <a name="use-group-policy-to-configure-pua-protection"></a>استخدام نهج المجموعة لتكوين حماية PUA

1. تنزيل [القوالب الإدارية (.admx) وتثبيتها لتحديث Windows 11 أكتوبر 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103507)

2. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

3. حدد نهج المجموعة الكائن الذي تريد تكوينه، ثم اختر **"تحرير**".

4. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

5. قم بتوسيع الشجرة إلى **Windows Components** \> **Microsoft Defender Antivirus**.

6. انقر نقرا **مزدوجا فوق تكوين الكشف للتطبيقات التي يحتمل أن تكون غير مرغوب فيها**.

7. حدد **Enabled** لتمكين حماية PUA.

8. في **"خيارات"**، حدد **"حظر"** لحظر التطبيقات التي يحتمل أن تكون غير مرغوب فيها، أو حدد **"وضع التدقيق"** لاختبار كيفية عمل الإعداد في بيئتك. حدد **موافق**.

9. نشر كائن نهج المجموعة كما تفعل عادة.

### <a name="use-powershell-cmdlets-to-configure-pua-protection"></a>استخدام PowerShell cmdlets لتكوين حماية PUA

#### <a name="to-enable-pua-protection"></a>لتمكين حماية PUA

```PowerShell
Set-MpPreference -PUAProtection Enabled
```

تعيين قيمة أمر cmdlet هذا لتشغيل `Enabled` الميزة إذا تم تعطيلها.

#### <a name="to-set-pua-protection-to-audit-mode"></a>لتعيين حماية PUA إلى وضع التدقيق

```PowerShell
Set-MpPreference -PUAProtection AuditMode
```

يكشف الإعداد `AuditMode` عن PUAs دون حظرها.

#### <a name="to-disable-pua-protection"></a>لتعطيل حماية PUA

نوصي بالاحتفاظ بحماية PUA قيد التشغيل. ومع ذلك، يمكنك إيقاف تشغيله باستخدام cmdlet التالي:

```PowerShell
Set-MpPreference -PUAProtection Disabled
```

تعيين قيمة أمر cmdlet هذا لإيقاف `Disabled` تشغيل الميزة إذا تم تمكينها.

لمزيد من المعلومات، راجع [استخدام أوامر Cmdlets PowerShell لتكوين أوامر cmdlets لبرنامج الحماية من الفيروسات والحماية من الفيروسات من Microsoft Defender وتشغيلها](use-powershell-cmdlets-microsoft-defender-antivirus.md).[](/powershell/module/defender/index)

## <a name="view-pua-events-using-powershell"></a>عرض أحداث PUA باستخدام PowerShell

يتم الإبلاغ عن أحداث PUA في عارض الأحداث Windows، ولكن ليس في Microsoft إدارة نقاط النهاية أو Intune. يمكنك أيضا استخدام `Get-MpThreat` cmdlet لعرض التهديدات التي عالجها برنامج الحماية من الفيروسات من Microsoft Defender. فيما يلي مثال على ذلك:

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

راجع [استكشاف أخطاء معرفات الأحداث وإصلاحها](troubleshoot-microsoft-defender-antivirus.md) للحصول على تفاصيل حول عرض أحداث برنامج الحماية من الفيروسات من Microsoft Defender. يتم تسجيل أحداث PUA ضمن معرف الحدث **1160**.

## <a name="view-pua-events-using-advanced-hunting"></a>عرض أحداث PUA باستخدام التتبع المتقدم

إذا كنت تستخدم [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md)، يمكنك استخدام استعلام تتبع متقدم لعرض أحداث PUA. فيما يلي مثال للاستعلام:

```console
DeviceEvents
| where ActionType == "AntivirusDetection"
| extend x = parse_json(AdditionalFields)
| project Timestamp, DeviceName, FolderPath, FileName, SHA256, ThreatName = tostring(x.ThreatName), WasExecutingWhileDetected = tostring(x.WasExecutingWhileDetected), WasRemediated = tostring(x.WasRemediated)
| where ThreatName startswith_cs 'PUA:'
```

لمعرفة المزيد حول التتبع المتقدم، راجع [البحث الاستباقي عن التهديدات باستخدام التتبع المتقدم](advanced-hunting-overview.md).

## <a name="exclude-files-from-pua-protection"></a>استبعاد الملفات من حماية PUA

في بعض الأحيان يتم حظر الملف بشكل خاطئ بواسطة حماية PUA، أو يلزم وجود ميزة PUA لإكمال مهمة. في هذه الحالات، يمكن إضافة ملف إلى قائمة استبعاد.

لمزيد من المعلومات، راجع [تكوين الاستثناءات والتحقق من صحتها استنادا إلى ملحق الملف وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [حماية الجيل التالي](microsoft-defender-antivirus-in-windows-10.md)
- [تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي](configure-protection-features-microsoft-defender-antivirus.md)
