---
title: برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows
description: تعرف على كيفية تمكين برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها على Windows Server 2016 Windows Server 2019 وserver Windows 2022.
keywords: windows defender, server, scep, system center endpoint protection, server 2016, current branch, server 2012
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
ms.openlocfilehash: b93595375982e3ed61d1ac94ae410575b0d72307
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666977"
---
# <a name="microsoft-defender-antivirus-on-windows-server"></a>برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يتوفر برنامج الحماية من الفيروسات من Microsoft Defender في الإصدارات/الإصدارات التالية من Windows Server:

- Windows Server 2022
- Windows Server 2019
- Windows Server، الإصدار 1803 أو أحدث
- Windows Server 2016‏
- Windows Server 2012 R2 (يتطلب Microsoft Defender لنقطة النهاية)

## <a name="setting-up-microsoft-defender-antivirus-on-windows-server"></a>إعداد برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows

تتضمن عملية إعداد برنامج الحماية من الفيروسات من Microsoft Defender وتشغيلها على Windows Server الخطوات التالية:

1. [تمكين الواجهة](#enable-the-user-interface-on-windows-server).
2. [تثبيت برنامج الحماية من الفيروسات من Microsoft Defender](#install-microsoft-defender-antivirus-on-windows-server).
3. [تحقق من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender](#verify-microsoft-defender-antivirus-is-running).
4. [تحديث التحليل الذكي لأمان مكافحة البرامج الضارة.](#update-antimalware-security-intelligence)
5. (حسب الحاجة) [إرسال عينات](#submit-samples).
6. (حسب الحاجة) [تكوين الاستثناءات التلقائية](#configure-automatic-exclusions).
7. (فقط إذا لزم الأمر) تعيين [Windows Server إلى الوضع السلبي](#passive-mode-and-windows-server).

## <a name="enable-the-user-interface-on-windows-server"></a>تمكين واجهة المستخدم على خادم Windows

> [!IMPORTANT]
> إذا كنت تستخدم Windows Server 2012 R2، فراجع ["خيارات" لتثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages).

بشكل افتراضي، يتم تثبيت برنامج الحماية من الفيروسات من Microsoft Defender وتشغيله على Windows Server. في بعض الأحيان، يتم تثبيت واجهة المستخدم (GUI) بشكل افتراضي. واجهة المستخدم الرسومية غير مطلوبة؛ يمكنك استخدام PowerShell أو نهج المجموعة أو أساليب أخرى لإدارة برنامج الحماية من الفيروسات من Microsoft Defender. ومع ذلك، تفضل العديد من المؤسسات استخدام واجهة المستخدم الرسومية برنامج الحماية من الفيروسات من Microsoft Defender. لتثبيت واجهة المستخدم الرسومية، استخدم أحد الإجراءات في الجدول التالي:

| الاجراء | ما يجب فعله |
|:---|:---|
| تشغيل واجهة المستخدم الرسومية باستخدام معالج إضافة أدوار وميزات | 1. راجع [تثبيت الأدوار وخدمات الأدوار والميزات باستخدام معالج إضافة أدوار وميزات](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard)، واستخدام **معالج إضافة أدوار وميزات**. <br/><br/>2. عند الوصول إلى خطوة **الميزات** الخاصة بالمعالج، ضمن **Windows Defender Features**، حدد الخيار **GUI ل Windows Defender**. |
| تشغيل واجهة المستخدم الرسومية باستخدام PowerShell | 1. على خادم Windows، افتح Windows PowerShell كمسؤول. <br/><br/>2. قم بتشغيل PowerShell cmdlet التالية: `Install-WindowsFeature -Name Windows-Defender-GUI` |

## <a name="install-microsoft-defender-antivirus-on-windows-server"></a>تثبيت برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows

إذا كنت بحاجة إلى تثبيت برنامج الحماية من الفيروسات من Microsoft Defender أو إعادة تثبيتها على Windows Server، فاستخدم أحد الإجراءات الواردة في الجدول التالي:

| الاجراء | ما يجب فعله |
|:---|:---|
| استخدم معالج إضافة أدوار وميزات لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender | 1. راجع [تثبيت الأدوار أو خدمات الأدوار أو الميزات أو إلغاء تثبيتها](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard) واستخدام **معالج إضافة أدوار وميزات**. <br/><br/>2. عند الوصول إلى خطوة **الميزات** في المعالج، حدد الخيار برنامج الحماية من الفيروسات من Microsoft Defender. حدد أيضا **GUI للخيار Windows Defender**. |
| استخدام PowerShell لتثبيت برنامج الحماية من الفيروسات من Microsoft Defender | 1. على خادم Windows، افتح Windows PowerShell كمسؤول. <br/><br/>2. قم بتشغيل PowerShell cmdlet التالية: `Install-WindowsFeature -Name Windows-Defender` |

> [!NOTE]
> يمكن العثور على رسائل الأحداث لمحرك مكافحة البرامج الضارة المضمنة مع برنامج الحماية من الفيروسات من Microsoft Defender في [برنامج الحماية من الفيروسات من Microsoft Defender Events](troubleshoot-microsoft-defender-antivirus.md).

## <a name="verify-microsoft-defender-antivirus-is-running"></a>التحقق من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender

بعد تثبيت (أو إعادة تثبيت) برنامج الحماية من الفيروسات من Microsoft Defender، تكون خطوتك التالية هي التحقق من أنه قيد التشغيل. استخدم أوامر PowerShell cmdlets في الجدول التالي:

| الاجراء | PowerShell cmdlet |
|:---|:---|
| التحقق من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender | `Get-Service -Name windefend` |
| التحقق من تشغيل حماية جدار الحماية | `Get-Service -Name mpssvc` |

كبديل ل PowerShell، يمكنك استخدام موجه الأوامر للتحقق من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender. للقيام بذلك، قم بتشغيل الأمر التالي من موجه الأوامر:

```cmd
sc query Windefend
```

يقوم `sc query` الأمر بإرجاع معلومات حول خدمة برنامج الحماية من الفيروسات من Microsoft Defender. عند تشغيل برنامج الحماية من الفيروسات من Microsoft Defender، `STATE` يتم عرض `RUNNING`القيمة.

لعرض جميع الخدمات التي لا تعمل، قم بتشغيل PowerShell cmdlet التالية:

```cmd
sc query state= all
```

## <a name="update-antimalware-security-intelligence"></a>تحديث التحليل الذكي لأمان مكافحة البرامج الضارة

للحصول على تحديثات التحليل الذكي للأمان العادية، يجب تشغيل خدمة Windows Update. إذا كنت تستخدم خدمة إدارة التحديثات، مثل خادم Windows Server Update Services (WSUS)، فتأكد من الموافقة على تحديثات تحليل معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender لأجهزة الكمبيوتر التي تديرها.

بشكل افتراضي، لا يقوم Windows Update بتنزيل التحديثات وتثبيتها تلقائيا على Windows Server 2019 أو Windows Server 2022 أو Windows Server 2016. يمكنك تغيير هذا التكوين باستخدام إحدى الطرق التالية:

| الاسلوب | الوصف |
|---|---|
| **Windows Update** في لوحة التحكم | يؤدي **تثبيت التحديثات تلقائيا** إلى تثبيت كافة التحديثات تلقائيا، بما في ذلك تحديثات التحليل الذكي Windows Defender Security. <br/><br/> **قم بتنزيل التحديثات ولكن اسمح لي باختيار ما إذا كان تثبيتها** يسمح Windows Defender بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا، ولكن لا يتم تثبيت التحديثات الأخرى تلقائيا. |
| **نهج المجموعة** | يمكنك إعداد Windows Update وإدارتها باستخدام الإعدادات المتوفرة في نهج المجموعة، في المسار التالي: **القوالب الإدارية\Windows Components\Windows Update\Configure Automatic Updates** |
| مفتاح تسجيل **AUOptions** | تسمح القيمتان التاليتان Windows Update بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا: <br/><br/> **4** -  **تثبيت التحديثات تلقائيا**. ينتج عن هذه القيمة تثبيت كافة التحديثات تلقائيا، بما في ذلك تحديثات التحليل الذكي Windows Defender Security. <br/><br/> **3** -  **قم بتنزيل التحديثات ولكن اسمح لي باختيار ما إذا كنت تريد تثبيتها أم لا**. تسمح هذه القيمة Windows Defender بتنزيل تحديثات معلومات الأمان وتثبيتها تلقائيا، ولكن لا يتم تثبيت التحديثات الأخرى تلقائيا. |

لضمان الحفاظ على الحماية من البرامج الضارة، قم بتمكين الخدمات التالية:

- خدمة إعداد تقرير بالأخطاء في Windows
- خدمة Windows Update

يسرد الجدول التالي خدمات برنامج الحماية من الفيروسات من Microsoft Defender والخدمات التابعة.

| اسم الخدمة | موقع الملف | الوصف |
|---|---|---|
| Windows Defender Service (WinDefend) | `C:\Program Files\Windows Defender\MsMpEng.exe` | هذه هي خدمة برنامج الحماية من الفيروسات من Microsoft Defender الرئيسية التي يجب تشغيلها دائما.|
| إعداد تقرير بالأخطاء في Windows Service (Wersvc) | `C:\WINDOWS\System32\svchost.exe -k WerSvcGroup` | ترسل هذه الخدمة تقارير الأخطاء مرة أخرى إلى Microsoft. |
| Windows Defender Firewall (MpsSvc) | `C:\WINDOWS\system32\svchost.exe -k LocalServiceNoNetwork` | نوصي بتمكين خدمة Windows Defender Firewall. |
| Windows Update (Wuauserv) | `C:\WINDOWS\system32\svchost.exe -k netsvcs`| هناك حاجة Windows Update للحصول على تحديثات معلومات الأمان وتحديثات محرك مكافحة البرامج الضارة |

## <a name="submit-samples"></a>إرسال عينات

يسمح نموذج الإرسال لشركة Microsoft بجمع عينات من البرامج التي يحتمل أن تكون ضارة. للمساعدة في توفير حماية مستمرة ومحدثة، يستخدم باحثو Microsoft هذه العينات لتحليل الأنشطة المشبوهة وإنتاج معلومات أمنية محدثة لمكافحة البرامج الضارة. نقوم بتجميع الملفات القابلة للتنفيذ للبرنامج، مثل ملفات .exe وملفات .dll. لا نجمع الملفات التي تحتوي على بيانات شخصية، مثل Microsoft Word المستندات وملفات PDF.

### <a name="submit-a-file"></a>إرسال ملف

1. راجع [دليل الإرسال](/windows/security/threat-protection/intelligence/submission-guide).

2. تفضل بزيارة [مدخل إرسال العينة](https://www.microsoft.com/wdsi/filesubmission)، وأرسل الملف.

### <a name="enable-automatic-sample-submission"></a>تمكين الإرسال التلقائي للعينة

لتمكين الإرسال التلقائي للعينة، ابدأ تشغيل وحدة تحكم Windows PowerShell كمسؤول، وعين بيانات قيمة **SubmitSamplesConsent** وفقا لأحد الإعدادات التالية:

|اعداد|الوصف|
|---|---|
| **0** -  **المطالبة دوما** | تطالبك خدمة برنامج الحماية من الفيروسات من Microsoft Defender بتأكيد إرسال كافة الملفات المطلوبة. هذا هو الإعداد الافتراضي برنامج الحماية من الفيروسات من Microsoft Defender، ولكن غير مستحسن للتثبيتات على Windows Server 2016 أو 2019، أو Windows Server 2022 بدون واجهة المستخدم الرسومية. |
| **1**  -  **إرسال عينات آمنة تلقائيا** | ترسل خدمة برنامج الحماية من الفيروسات من Microsoft Defender كافة الملفات التي تم وضع علامة "آمنة" عليها وتطالب بباقي الملفات. |
| **2** -  **عدم الإرسال أبدا** | لا تطالب خدمة برنامج الحماية من الفيروسات من Microsoft Defender بأي ملفات ولا ترسلها. |
| **3** -  **إرسال جميع العينات تلقائيا** | ترسل خدمة برنامج الحماية من الفيروسات من Microsoft Defender كافة الملفات دون مطالبة للتأكيد. |

> [!NOTE]
> هذا الخيار غير متوفر ل Windows Server 2012 R2. 

## <a name="configure-automatic-exclusions"></a>تكوين الاستثناءات التلقائية

للمساعدة في ضمان الأمان والأداء، تتم إضافة بعض الاستثناءات تلقائيا استنادا إلى الأدوار والميزات التي تقوم بتثبيتها عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016 أو 2019 أو Windows Server 2022.

راجع [تكوين الاستثناءات في برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server](configure-server-exclusions-microsoft-defender-antivirus.md).

## <a name="passive-mode-and-windows-server"></a>الوضع السلبي وخادم Windows

إذا كنت تستخدم منتج الحماية من الفيروسات غير التابع ل Microsoft كحل الحماية من الفيروسات الأساسي على Windows Server، فيجب تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي أو وضع التعطيل. إذا تم إلحاق نقطة نهاية خادم Windows إلى Microsoft Defender لنقطة النهاية، يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع الخامل. إذا كنت لا تستخدم Microsoft Defender لنقطة النهاية، فقم بتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى وضع التعطيل. 

> [!TIP]
> راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md).

يصف الجدول التالي أساليب تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع الخامل وتعطيل برنامج الحماية من الفيروسات من Microsoft Defender وإلغاء التثبيت برنامج الحماية من الفيروسات من Microsoft Defender:

| الاجراء | الوصف |
|---|---|
| تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام مفتاح التسجيل | تعيين مفتاح التسجيل ForceDefenderPassiveMode كما يلي: <br/>- المسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <br/>- الاسم: `ForceDefenderPassiveMode` <br/>- النوع: `REG_DWORD` <br/>- القيمة: `1` |
| إيقاف تشغيل واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell | افتح Windows PowerShell كمسؤول، وقم بتشغيل أمر Cmdlet PowerShell التالي:`Uninstall-WindowsFeature -Name Windows-Defender-GUI`
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell | استخدم أمر Cmdlet PowerShell التالي: `Set-MpPreference -DisableRealtimeMonitoring $true` |
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام معالج إزالة الأدوار والميزات | راجع [تثبيت الأدوار أو خدمات الأدوار أو الميزات أو إلغاء تثبيتها](/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#remove-roles-role-services-and-features-by-using-the-remove-roles-and-features-wizard)، واستخدم **معالج إزالة الأدوار والميزات**. <br/><br/>عند الوصول إلى خطوة **الميزات** الخاصة بالمعالج، قم بإلغاء تحديد الخيار **Windows Defender Features**. <br/><br/> إذا قمت **بمسح Windows Defender** بنفسه ضمن قسم **"ميزات Windows Defender**"، فستتم مطالبتك بإزالة واجهة **المستخدم الرسومية** الخاصة بخيار الواجهة ل Windows Defender.<br/><br/>سيستمر تشغيل برنامج الحماية من الفيروسات من Microsoft Defender بشكل طبيعي دون واجهة المستخدم، ولكن لا يمكن تمكين واجهة المستخدم إذا قمت بتعطيل ميزة **Windows Defender** الأساسية. |
| إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender باستخدام PowerShell | استخدم أمر Cmdlet PowerShell التالي: `Uninstall-WindowsFeature -Name Windows-Defender` |
| تعطيل برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة | في محرر نهج المجموعة المحلي، انتقل إلى **القالب** >  الإداري **Windows المكون** >  **Endpoint Protection** >  **مكون قابل للتعدي Endpoint Protection**، ثم حدد **EnabledOK** > . |

### <a name="are-you-using-windows-server-2012-r2-or-windows-server-2016"></a>هل تستخدم Windows Server 2012 R2 أو Windows Server 2016؟

إذا تم إلحاق خادم Windows الخاص بك Microsoft Defender لنقطة النهاية، يمكنك الآن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل على Windows Server 2012 R2 وserver Windows 2016. راجع المقالات التالية:

- [خيارات تثبيت Microsoft Defender لنقطة النهاية](configure-server-endpoints.md#options-to-install-the-microsoft-defender-for-endpoint-packages)

- [التوافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md)

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows](microsoft-defender-antivirus-windows.md)

