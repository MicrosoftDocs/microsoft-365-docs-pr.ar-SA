---
title: برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server
description: تعرف على كيفية تمكين برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها على Windows Server 2016 Windows Server 2019 Windows Server 2022.
keywords: windows defender، الخادم، scep، حماية نقطة نهاية مركز النظام، الخادم 2016، الفرع الحالي، الخادم 2012
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr, shwjha
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 01/26/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 4962537e86010fceeb2845fdd6408270c97742dc
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469746"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

برنامج الحماية من الفيروسات من Microsoft Defender في الإصدارات/الإصدارات التالية من Windows Server:

- Windows Server 2022
- Windows Server 2019
- Windows Server، الإصدار 1803 أو الإصدارات الأحدث
- Windows Server 2016‏
- Windows Server 2012 R2 (يتطلب Microsoft Defender لنقطة النهاية)

في بعض الحالات، برنامج الحماية من الفيروسات من Microsoft Defender يشار إلى Endpoint Protection، ولكن محرك الحماية هو نفسه. على الرغم من أن الوظائف والتكوين والإدارة هي نفسها إلى حد كبير [](microsoft-defender-antivirus-windows.md) برنامج الحماية من الفيروسات من Microsoft Defender على Windows 10 و Windows 11، هناك بعض الاختلافات الرئيسية في Windows Server:

- في Windows الخادم، [يتم](configure-server-exclusions-microsoft-defender-antivirus.md) تطبيق الاستثناءات التلقائية استنادا إلى دور الخادم المحدد.

- على Windows Server، إذا كنت تقوم بتشغيل حل برنامج الحماية من الفيروسات/مكافحة البرامج الضارة من Microsoft، برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي أو وضع المعطل تلقائيا. ومع ذلك، يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender وضع غير سلبي أو معطل يدويا.

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>إعداد برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server

تتضمن عملية إعداد وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender على النظام الأساسي للخادم عدة خطوات:

1. [تمكين الواجهة](#enable-the-user-interface-on-windows-server).
2. [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [تحقق برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل](#verify-microsoft-defender-antivirus-is-running).
4. [قم بتحديث معلومات أمان مكافحة البرامج الضارة](#update-antimalware-security-intelligence).
5. (حسب الحاجة) [إرسال عينات](#submit-samples).
6. (حسب الحاجة) [تكوين الاستثناءات التلقائية](#configure-automatic-exclusions).
7. (فقط إذا لزم الأمر) تعيين [Windows الخادم إلى الوضع السلبي](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>تمكين واجهة المستخدم على Windows Server

بشكل افتراضي برنامج الحماية من الفيروسات من Microsoft Defender يتم تثبيت Windows Server. في بعض الأحيان، يتم تثبيت واجهة المستخدم (GUI) بشكل افتراضي، ولكن واجهة المستخدم (GUI) غير مطلوبة. يمكنك استخدام PowerShell أو نهج المجموعة أو أساليب أخرى لإدارة برنامج الحماية من الفيروسات من Microsoft Defender.

إذا لم يكن GUI مثبتا على الخادم، وتريد تثبيته، إما معالج إضافة **أدوار** وميزات أو PowerShell cmdlets.

> [!NOTE]
> لا يتوفر هذا الخيار Windows Server 2012 R2. لمزيد من المعلومات، راجع [خيارات تثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

### <a name="turn-on-the-gui-using-the-add-roles-and-features-wizard"></a>تشغيل واجهة المستخدم (GUI) باستخدام معالج "إضافة أدوار وميزات"

1. راجع [تثبيت الأدوار وخدمات الدور](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) والميزات باستخدام معالج إضافة أدوار وميزات، واستخدام معالج إضافة **أدوار وميزات**.

2. عند الوصول إلى الخطوة **ميزات** من المعالج، ضمن Windows **ميزات Defender**، حدد **الخيار GUI Windows Defender**.

   في Windows Server 2016، يبدو معالج إضافة أدوار وميزات كما يلي:

   :::image type="content" source="images/server-add-gui.png" alt-text="يعرض معالج إضافة أدوار وميزات خيار GUI Windows Defender." lightbox="images/server-add-gui.png":::

   في Windows Server 2019 Windows Server 2022، يكون معالج إضافة **أدوار وميزات** مماثلا.

### <a name="turn-on-the-gui-using-powershell"></a>تشغيل واجهة المستخدم (GUI) باستخدام PowerShell

سيمكن PowerShell cmdlet التالي الواجهة:

```powershell
Install-WindowsFeature -Name Windows-Defender-GUI
```

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server

إذا كنت بحاجة إلى تثبيت أو إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server، يمكنك القيام بذلك باستخدام معالج إضافة **أدوار** وميزات أو PowerShell.

### <a name="use-the-add-roles-and-features-wizard-to-install-microsoft-defender-antivirus"></a>استخدم معالج إضافة أدوار وميزات لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender

1. راجع هذه [المقالة،](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) ثم استخدم معالج إضافة **أدوار وميزات**.

2. عند الوصول إلى الخطوة **ميزات** من المعالج، حدد خيار برنامج الحماية من الفيروسات من Microsoft Defender. حدد أيضا خيار **GUI Windows Defender**.

### <a name="use-powershell-to-install-microsoft-defender-antivirus"></a>استخدم PowerShell لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender

لاستخدام PowerShell لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender، قم بتشغيل cmdlet التالي:

```powershell
Install-WindowsFeature -Name Windows-Defender
```

يمكن العثور على رسائل الأحداث الخاصة بمحرك مكافحة البرامج الضارة المضمن برنامج الحماية من الفيروسات من Microsoft Defender في برنامج الحماية من الفيروسات من Microsoft Defender [الأحداث](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>التحقق برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل

بمجرد برنامج الحماية من الفيروسات من Microsoft Defender تثبيت التطبيق، تكون الخطوة التالية هي التحقق من أنه قيد التشغيل. على نقطة نهاية Windows الخادم، تشغيل الأمر cmdlet التالي في PowerShell:

```powershell
Get-Service -Name windefend
```

للتحقق من تشغيل حماية جدار الحماية، قم بتشغيل أمر cmdlet التالي في PowerShell:

```powershell
Get-Service -Name mpssvc
```

كبديل ل PowerShell، يمكنك استخدام موجه الأوامر للتحقق من أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل. للقيام بذلك، يمكنك تشغيل الأمر التالي من موجه الأوامر:

```console
sc query Windefend
```

يرجع `sc query` الأمر معلومات حول برنامج الحماية من الفيروسات من Microsoft Defender الخدمة. عند برنامج الحماية من الفيروسات من Microsoft Defender، يتم عرض `STATE` القيمة `RUNNING`.

لعرض كل الخدمات التي لا يتم تشغيلها، يمكنك تشغيل الأمر Cmdlet التالي في PowerShell:

```console
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>تحديث معلومات الأمان لمكافحة البرامج الضارة

للحصول على معلومات محدثة حول أمان مكافحة البرامج الضارة، يجب أن Windows Update الخدمة قيد التشغيل. إذا كنت تستخدم خدمة إدارة التحديثات، مثل خادم Windows Server Update Services (WSUS)، فتأكد من أنه تمت الموافقة على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender معلومات الأمان لأجهزة الكمبيوتر التي تديرها.

بشكل افتراضي، Windows Update تنزيل التحديثات وتثبيتها تلقائيا على Windows Server 2019 أو Windows Server 2022 أو Windows Server 2016. يمكنك تغيير هذا التكوين باستخدام أحد الأساليب التالية:

<br/><br/>

| الأسلوب | الوصف |
|---|---|
| **Windows Update** في لوحة التحكم | **يؤدي تثبيت التحديثات تلقائيا** إلى تثبيت كل التحديثات تلقائيا، بما في ذلك Windows معلومات أمان Defender. <br/><br/> **تنزيل التحديثات ولكن** اسم السماح لي باختيار ما إذا كنت تريد تثبيتها Windows Defender بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا، ولكن لا يتم تثبيت التحديثات الأخرى تلقائيا. |
| **نهج المجموعة** | يمكنك إعداد Windows Update باستخدام الإعدادات المتوفرة في نهج المجموعة، في المسار التالي: القوالب الإدارية **\Windows المكونات\Windows Update\** تكوين التحديثات التلقائية |
| مفتاح **تسجيل AUOptions** | تسمح القيمتان التاليتان Windows Update تنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا: <br/><br/> **4** -  **تثبيت التحديثات تلقائيا**. ينتج عن هذه القيمة تثبيت كل التحديثات تلقائيا، بما في ذلك Windows معلومات أمان Defender. <br/><br/> **3** -  **قم بتنزيل التحديثات ولكن اسماني باختيار ما إذا كنت تريد تثبيتها أم لا**. تسمح هذه Windows Defender بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا، ولكن لا يتم تثبيت التحديثات الأخرى تلقائيا. |

لضمان الحفاظ على الحماية من البرامج الضارة، نوصي بتمكين الخدمات التالية:

- إعداد تقرير بالأخطاء في Windows الخدمة
- Windows Update الخدمة

يسرد الجدول التالي خدمات برنامج الحماية من الفيروسات من Microsoft Defender والخدمات التابعة.

<br/><br/>


| اسم الخدمة | موقع الملف | الوصف |
|---|---|---|
| Windows Defender Service (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | هذه هي الخدمة برنامج الحماية من الفيروسات من Microsoft Defender التي يجب تشغيلها في كل الأوقات.|
| إعداد تقرير بالأخطاء في Windows الخدمة (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | ترسل هذه الخدمة تقارير الأخطاء مرة أخرى إلى Microsoft. |
| Windows Defender Firewall (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | نوصي بترك Windows جدار الحماية ل Defender ممكنة. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update الحاجة للحصول على تحديثات معلومات الأمان وتحديثات مشغلات البرامج الضارة |

## <a name="submit-samples"></a>إرسال عينات

تسمح عملية الإرسال العينة لشركة Microsoft بتجميع عينات من البرامج التي قد تكون ضارة. للمساعدة في توفير حماية مستمرة ومحدثة، يستخدم الباحثون في Microsoft هذه العينات لتحليل الأنشطة المريبة وإنتاج معلومات محدثة حول أمان البرامج الضارة. نجمع ملفات قابلة للتنفيذ للبرنامج، مثل .exe الملفات .dll الملفات. لا نجمع الملفات التي تحتوي على بيانات شخصية، مثل Microsoft Word وملفات PDF.

### <a name="submit-a-file"></a>إرسال ملف

1. راجع [دليل الإرسال](/windows/security/threat-protection/intelligence/submission-guide).
2. تفضل بزيارة [مدخل الإرسال النموذجي](https://www.microsoft.com/wdsi/filesubmission)، وأدخل الملف.

### <a name="enable-automatic-sample-submission"></a>تمكين الإرسال النموذجي التلقائي

لتمكين الإرسال النموذجي التلقائي، ابدأ تشغيل وحدة تحكم Windows PowerShell كمسؤول، ثم عين بيانات القيمة **SubmitSamplesConsent** وفقا لأحد الإعدادات التالية:

<br/><br/>

|الإعداد|الوصف|
|---|---|
| **0** -  **المطالبة دائما** | تطلب برنامج الحماية من الفيروسات من Microsoft Defender الخدمة تأكيد إرسال جميع الملفات المطلوبة. هذا هو الإعداد الافتراضي ل برنامج الحماية من الفيروسات من Microsoft Defender، ولكن لا يوصى بإجراء عمليات التثبيت على Windows Server 2016 أو 2019 أو Windows Server 2022 بدون واجهة GUI. |
| **1**  -  **إرسال عينات آمنة تلقائيا** | ترسل برنامج الحماية من الفيروسات من Microsoft Defender الخدمة كافة الملفات التي تم وضع علامة "آمن" عليها وتطالب ببقية الملفات. |
| **2** -  **عدم إرسال** | لا برنامج الحماية من الفيروسات من Microsoft Defender هذه الخدمة ولا ترسل أي ملفات. |
| **3** -  **إرسال كل العينات تلقائيا** | ترسل برنامج الحماية من الفيروسات من Microsoft Defender الخدمة كل الملفات دون مطالبة بتأكيدها. |

> [!NOTE]
> لا يتوفر هذا الخيار Windows Server 2012 R2. 


## <a name="configure-automatic-exclusions"></a>تكوين الاستثناءات التلقائية

للمساعدة على ضمان الأمان والأداء، تضاف بعض الاستثناءات تلقائيا استنادا إلى الأدوار والميزات التي تقوم بتثبيتها عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016 أو 2019 أو Windows Server 2022.

راجع [تكوين الاستثناءات في برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>الوضع السلبي Windows Server

إذا كنت تستخدم منتجا لا يستخدم برنامج الحماية من الفيروسات من Microsoft كحل أساسي لمكافحة الفيروسات على Windows Server، فيجب عليك تعيين برنامج الحماية من الفيروسات من Microsoft Defender وضع غير سلبي أو وضع معطل.

لمزيد من المعلومات، راجع [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server](microsoft-defender-antivirus-on-windows-server.md#install-microsoft-defender-antivirus-on-windows-server).


### <a name="set-microsoft-defender-antivirus-to-passive-mode-using-a-registry-key"></a>تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام مفتاح تسجيل

يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي عن طريق تعيين مفتاح التسجيل التالي:
- المسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- الاسم: `ForceDefenderPassiveMode`
- اكتب: `REG_DWORD`
- القيمة: `1`

### <a name="disable-microsoft-defender-antivirus-using-the-remove-roles-and-features-wizard"></a>تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام معالج إزالة الأدوار والميزات

1. راجع [تثبيت الأدوار](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) أو خدمات الدور أو الميزات أو إلغاء تثبيتها، واستخدام معالج إزالة **الأدوار والميزات**.

2. عند الوصول إلى خطوة **الميزات** من المعالج، أمسح Windows **ميزات Defender**.

    إذا قمت **Windows Defender** بنفسه ضمن المقطع ميزات **Windows Defender**، فسوف يتم مطالبتك بإزالة خيار واجهة **المستخدم (GUI) Windows Defender**.

    برنامج الحماية من الفيروسات من Microsoft Defender التشغيل العادي بدون واجهة المستخدم، ولكن لا يمكن تمكين واجهة المستخدم إذا **قمت بتعطيل Windows Defender** الأساسية.

### <a name="turn-off-the-microsoft-defender-antivirus-user-interface-using-powershell"></a>إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender المستخدم باستخدام PowerShell

إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender GUI، استخدم cmdlet التالي في PowerShell:

```powershell
Uninstall-WindowsFeature -Name Windows-Defender-GUI
```

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>هل تستخدم Windows Server 2012 R2 أو Windows Server 2016؟

يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على Windows Server 2012 R2 Windows Server 2016. لمزيد من المعلومات، راجع [خيارات تثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

<br/><br/>

| الإجراء | الوصف |
|---|---|
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة | في محرر نهج المجموعة المحلي > ، انتقل إلى القالب الإداري Windows **مكون** >  >  Endpoint Protection مكون **Endpoint Protection**، ثم حدد **EnabledOK** > . |
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام مفتاح تسجيل | لاستخدام مفتاح تسجيل [DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)`HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`، انتقل إلى ، ثم قم بتعيين أو إنشاء إدخال DWORD يسمى `DisableAntiSpyware`. قم بتعيين قيمته إلى `1` (الذي يحدد قيمة مفتاح التسجيل إلى *true*). |
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender PowerShell | استخدم cmdlet التالي في PowerShell: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender PowerShell | استخدم cmdlet التالي في PowerShell: `Uninstall-WindowsFeature -Name Windows-Defender` |


## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows](microsoft-defender-antivirus-windows.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender التوافق](microsoft-defender-antivirus-compatibility.md)
