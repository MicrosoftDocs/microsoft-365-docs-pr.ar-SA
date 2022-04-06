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
ms.reviewer: pahuijbr
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 04/01/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 412033e274cce22b9350292c612b91ef6e34e209
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634834"
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

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>إعداد برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server

تتضمن عملية إعداد وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender على Windows الخادم الخطوات التالية:

1. [تمكين الواجهة](#enable-the-user-interface-on-windows-server).
2. [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [تحقق برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل](#verify-microsoft-defender-antivirus-is-running).
4. [قم بتحديث معلومات أمان مكافحة البرامج الضارة](#update-antimalware-security-intelligence).
5. (حسب الحاجة) [إرسال عينات](#submit-samples).
6. (حسب الحاجة) [تكوين الاستثناءات التلقائية](#configure-automatic-exclusions).
7. (فقط إذا لزم الأمر) تعيين [Windows الخادم إلى الوضع السلبي](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>تمكين واجهة المستخدم على Windows Server

> [!IMPORTANT]
> إذا كنت تستخدم Windows Server 2012 R2، فشاهد خيارات [لتثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

بشكل افتراضي برنامج الحماية من الفيروسات من Microsoft Defender يتم تثبيت Windows Server. في بعض الأحيان، يتم تثبيت واجهة المستخدم (GUI) بشكل افتراضي. واجهة المستخدم (GUI) غير مطلوبة؛ يمكنك استخدام PowerShell أو نهج المجموعة أو أساليب أخرى لإدارة برنامج الحماية من الفيروسات من Microsoft Defender. ومع ذلك، يفضل عدد كبير من المؤسسات استخدام واجهة المستخدم (GUI) برنامج الحماية من الفيروسات من Microsoft Defender. لتثبيت GUI، استخدم أحد الإجراءات في الجدول التالي:

| الإجراء | ما يجب فعله |
|:---|:---|
| تشغيل واجهة المستخدم (GUI) باستخدام معالج "إضافة أدوار وميزات" | 1. راجع [تثبيت الأدوار وخدمات الدور](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) والميزات باستخدام معالج إضافة أدوار وميزات، واستخدام معالج إضافة **أدوار وميزات**. <br/><br/>2. عند الوصول إلى الخطوة ميزات من  المعالج، ضمن Windows **ميزات** Defender، حدد **خيار GUI Windows Defender**. |
| تشغيل واجهة المستخدم (GUI) باستخدام PowerShell | 1. على الخادم Windows، افتح Windows PowerShell كمسؤول. <br/><br/>2. تشغيل الأمر Cmdlet التالي في PowerShell: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server

إذا كنت بحاجة إلى تثبيت أو إعادة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على Windows الخادم، فاستخدم أحد الإجراءات في الجدول التالي:

| الإجراء | ما يجب فعله |
|:---|:---|
| استخدم معالج إضافة أدوار وميزات لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender | 1. راجع [تثبيت](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) الأدوار أو خدمات الدور أو الميزات أو إلغاء تثبيتها، واستخدام معالج إضافة **أدوار وميزات**. <br/><br/>2. عند الوصول إلى الخطوة **ميزات** من المعالج، حدد خيار برنامج الحماية من الفيروسات من Microsoft Defender. حدد أيضا خيار **GUI Windows Defender**. |
| استخدم PowerShell لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender | 1. على الخادم Windows، افتح Windows PowerShell كمسؤول. <br/><br/>2. تشغيل الأمر Cmdlet التالي في PowerShell: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> يمكن العثور على رسائل الأحداث الخاصة بمحرك مكافحة البرامج الضارة المضمن برنامج الحماية من الفيروسات من Microsoft Defender في برنامج الحماية من الفيروسات من Microsoft Defender [الأحداث](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>التحقق برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل

بعد تثبيت (أو إعادة تثبيته) برنامج الحماية من الفيروسات من Microsoft Defender، تكون الخطوة التالية هي التحقق من أنه قيد التشغيل. استخدم cmdlets PowerShell في الجدول التالي:

| الإجراء | PowerShell cmdlet |
|:---|:---|
| التحقق من برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل | `Get-Service -Name windefend` |
| التحقق من تشغيل حماية جدار الحماية | `Get-Service -Name mpssvc` |

كبديل ل PowerShell، يمكنك استخدام موجه الأوامر للتحقق من أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل. للقيام بذلك، يمكنك تشغيل الأمر التالي من موجه الأوامر:

```cmd
sc query Windefend
```

يرجع `sc query` الأمر معلومات حول برنامج الحماية من الفيروسات من Microsoft Defender الخدمة. عند برنامج الحماية من الفيروسات من Microsoft Defender، يتم عرض `STATE` القيمة `RUNNING`.

لعرض كل الخدمات التي لا يتم تشغيلها، يمكنك تشغيل الأمر Cmdlet التالي في PowerShell:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>تحديث معلومات الأمان لمكافحة البرامج الضارة

للحصول على تحديثات معلومات الأمان العادية، Windows Update الخدمة قيد التشغيل. إذا كنت تستخدم خدمة إدارة التحديثات، مثل خادم Windows Server Update Services (WSUS)، فتأكد من أنه تمت الموافقة على تحديثات برنامج الحماية من الفيروسات من Microsoft Defender معلومات الأمان لأجهزة الكمبيوتر التي تديرها.

بشكل افتراضي، Windows Update تنزيل التحديثات وتثبيتها تلقائيا على Windows Server 2019 أو Windows Server 2022 أو Windows Server 2016. يمكنك تغيير هذا التكوين باستخدام أحد الأساليب التالية:

| الأسلوب | الوصف |
|---|---|
| **Windows Update** في لوحة التحكم | **يؤدي تثبيت التحديثات تلقائيا** إلى تثبيت كل التحديثات تلقائيا، بما في ذلك Windows معلومات أمان Defender. <br/><br/> **تنزيل التحديثات ولكن** اسم السماح لي باختيار ما إذا كنت تريد تثبيتها Windows Defender بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا، ولكن لا يتم تثبيت التحديثات الأخرى تلقائيا. |
| **نهج المجموعة** | يمكنك إعداد Windows Update باستخدام الإعدادات المتوفرة في نهج المجموعة، في المسار التالي: القوالب الإدارية **\Windows المكونات\Windows Update\** تكوين التحديثات التلقائية |
| مفتاح **تسجيل AUOptions** | تسمح القيمتان التاليتان Windows Update تنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا: <br/><br/> **4** -  **تثبيت التحديثات تلقائيا**. ينتج عن هذه القيمة تثبيت كل التحديثات تلقائيا، بما في ذلك Windows معلومات أمان Defender. <br/><br/> **3** -  **قم بتنزيل التحديثات ولكن اسماني باختيار ما إذا كنت تريد تثبيتها أم لا**. تسمح هذه Windows Defender بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا، ولكن لا يتم تثبيت التحديثات الأخرى تلقائيا. |

لضمان الحفاظ على الحماية من البرامج الضارة، يمكنك تمكين الخدمات التالية:

- إعداد تقرير بالأخطاء في Windows الخدمة
- Windows Update الخدمة

يسرد الجدول التالي خدمات برنامج الحماية من الفيروسات من Microsoft Defender والخدمات التابعة.

| اسم الخدمة | موقع الملف | الوصف |
|---|---|---|
| Windows Defender Service (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | هذه هي الخدمة برنامج الحماية من الفيروسات من Microsoft Defender التي يجب تشغيلها دائما.|
| إعداد تقرير بالأخطاء في Windows الخدمة (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | ترسل هذه الخدمة تقارير الأخطاء مرة أخرى إلى Microsoft. |
| Windows Defender Firewall (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | نوصي بالإبقاء على Windows جدار الحماية ل Defender. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| Windows Update الحاجة للحصول على تحديثات معلومات الأمان وتحديثات مشغلات البرامج الضارة |

## <a name="submit-samples"></a>إرسال عينات

تسمح عملية الإرسال العينة لشركة Microsoft بتجميع عينات من البرامج التي قد تكون ضارة. للمساعدة في توفير حماية مستمرة ومحدثة، يستخدم الباحثون في Microsoft هذه العينات لتحليل الأنشطة المريبة وإنتاج معلومات محدثة حول أمان البرامج الضارة. نجمع ملفات قابلة للتنفيذ للبرنامج، مثل .exe الملفات .dll الملفات. لا نجمع الملفات التي تحتوي على بيانات شخصية، مثل Microsoft Word وملفات PDF.

### <a name="submit-a-file"></a>إرسال ملف

1. راجع [دليل الإرسال](/windows/security/threat-protection/intelligence/submission-guide).

2. تفضل بزيارة [مدخل الإرسال النموذجي](https://www.microsoft.com/wdsi/filesubmission)، وأدخل الملف.

### <a name="enable-automatic-sample-submission"></a>تمكين الإرسال النموذجي التلقائي

لتمكين الإرسال النموذجي التلقائي، ابدأ تشغيل وحدة تحكم Windows PowerShell كمسؤول، ثم عين بيانات القيمة **SubmitSamplesConsent** وفقا لأحد الإعدادات التالية:

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

إذا كنت تستخدم منتجا لا يستخدم برنامج الحماية من الفيروسات من Microsoft كحل أساسي لمكافحة الفيروسات على Windows Server، فيجب عليك تعيين برنامج الحماية من الفيروسات من Microsoft Defender وضع غير سلبي أو وضع معطل. إذا تم Windows نهاية الخادم Microsoft Defender لنقطة النهاية، يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي. إذا كنت لا تستخدم Microsoft Defender لنقطة النهاية، فحدد برنامج الحماية من الفيروسات من Microsoft Defender وضع المعطل. 

> [!TIP]
> راجع [برنامج الحماية من الفيروسات من Microsoft Defender التوافق مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md).

يصف الجدول التالي أساليب لتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى وضع غير برنامج الحماية من الفيروسات من Microsoft Defender، ثم إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender:

| الإجراء | الوصف |
|---|---|
| تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام مفتاح تسجيل | تعيين مفتاح التسجيل ForceDefenderPassiveMode كما يلي: <br/>- المسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- الاسم: `ForceDefenderPassiveMode` <br/>- النوع: `REG_DWORD` <br/>- القيمة: `1` |
| إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender المستخدم باستخدام PowerShell | افتح Windows PowerShell كمسؤول، ثم ادير cmdlet التالي في PowerShell:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender PowerShell | استخدم cmdlet التالي في PowerShell: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام معالج إزالة الأدوار والميزات | راجع [تثبيت الأدوار](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard) أو خدمات الدور أو الميزات أو إلغاء تثبيتها، واستخدام معالج إزالة **الأدوار والميزات**. <br/><br/>عند الوصول إلى خطوة **الميزات** من المعالج، أمسح Windows **ميزات Defender**. <br/><br/> إذا قمت **Windows Defender** بنفسه ضمن المقطع ميزات **Windows Defender**، فسوف يتم مطالبتك بإزالة خيار واجهة **المستخدم (GUI) Windows Defender**.<br/><br/>برنامج الحماية من الفيروسات من Microsoft Defender التشغيل العادي بدون واجهة المستخدم، ولكن لا يمكن تمكين واجهة المستخدم إذا **قمت بتعطيل Windows Defender** الأساسية. |
| إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender PowerShell | استخدم cmdlet التالي في PowerShell: `Uninstall-WindowsFeature -Name Windows-Defender` |
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة | في محرر نهج المجموعة المحلي > ، انتقل إلى القالب الإداري Windows **مكون** >  >  Endpoint Protection مكون **Endpoint Protection**، ثم حدد **EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>هل تستخدم Windows Server 2012 R2 أو Windows Server 2016؟

إذا كان Windows Server Microsoft Defender لنقطة النهاية، يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط على Windows Server 2012 R2 Windows Server 2016. راجع المقالات التالية:

- [خيارات لتثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [برنامج الحماية من الفيروسات من Microsoft Defender التوافق مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows](microsoft-defender-antivirus-windows.md)

