---
title: استخدم سطر الأوامر لإدارة برنامج الحماية من الفيروسات من Microsoft Defender
description: قم بتشغيل عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender وتكوين حماية الجيل التالي باستخدام أداة مساعدة مخصصة لسطر الأوامر.
keywords: تشغيل فحص windows Defender، وتشغيل فحص مكافحة الفيروسات من سطر الأوامر، وتشغيل فحص windows Defender من سطر الأوامر، mpcmdrun، Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.date: 05/24/2021
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.openlocfilehash: 97f818469f9da2616ca5ca2839ddf29ea227b85f
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789723"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>تكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها باستخدام أداة سطر الأوامر mpcmdrun.exe

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender 

**منصات**
- بالنسبة لنظام التشغيل

يمكنك تنفيذ وظائف مختلفة في برنامج الحماية من الفيروسات من Microsoft Defender باستخدام أداة سطر الأوامر المخصصة **mpcmdrun.exe**. هذه الأداة المساعدة مفيدة عندما تريد أتمتة المهام برنامج الحماية من الفيروسات من Microsoft Defender. يمكنك العثور على الأداة المساعدة في `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. قم بتشغيله من موجه الأوامر.

> [!TIP]
> قد تحتاج إلى فتح إصدار على مستوى المسؤول لمطالبة الأوامر. عند البحث عن **موجه الأوامر** على قائمة البدء، اختر **"تشغيل كمسؤول**". إذا كنت تقوم بتشغيل إصدار نظام أساسي محدث من Microsoft Defender لمكافحة البرامج الضارة، فقم بتشغيله `MpCmdRun` من الموقع التالي: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. لمزيد من المعلومات حول النظام الأساسي لمكافحة البرامج الضارة، راجع [برنامج الحماية من الفيروسات من Microsoft Defender التحديثات والأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).

تستخدم الأداة المساعدة MpCmdRun بناء الجملة التالي:

```console
MpCmdRun.exe [command] [-options]
```

فيما يلي مثال على ذلك:

```console
MpCmdRun.exe -Scan -ScanType 2
```

في مثالنا، تبدأ الأداة المساعدة MpCmdRun عملية فحص مكافحة الفيروسات الكاملة على الجهاز.

## <a name="commands"></a>الاوامر

|الامر|الوصف|
|---|---|
|`-?`**او** `-h`|عرض كافة الخيارات المتوفرة لأداة MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|عمليات الفحص بحثا عن برامج ضارة. قيم **ScanType** هي:<p>**0** افتراضي، وفقا للتكوين الخاص بك<p>**فحص سريع 1**<p>**فحص كامل 2**<p>**3** فحص مخصص لملفات ودلائل.<p>يتم تشغيل CpuThrottling وفقا لتكوينات النهج|
|`-Trace [-Grouping #] [-Level #]`|بدء التتبع التشخيصي|
|`-GetFiles [-SupportLogLocation <path>]`|يجمع معلومات الدعم. راجع "[تجميع البيانات التشخيصية](collect-diagnostic-data.md)"|
|`-GetFilesDiagTrack`|مثل `-GetFiles`، ولكن المخرجات إلى مجلد DiagTrack المؤقت|
|`-RemoveDefinitions [-All]`|استعادة معلومات الأمان المثبتة إلى نسخة احتياطية سابقة أو إلى المجموعة الافتراضية الأصلية|
|`-RemoveDefinitions [-DynamicSignatures]`|إزالة معلومات الأمان التي تم تنزيلها ديناميكيا فقط|
|`-RemoveDefinitions [-Engine]`|استعادة المحرك المثبت السابق|
|`-SignatureUpdate [-UNC \|-MMPC]`|التحقق من وجود تحديثات جديدة لذكاء الأمان|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|استعادة العنصر (العناصر) المعزولة أو سردها|
|`-AddDynamicSignature [-Path]`|تحميل التحليل الذكي للأمان الديناميكي|
|`-ListAllDynamicSignatures`|سرد التحليل الذكي للأمان الديناميكي الذي تم تحميله|
|`-RemoveDynamicSignature [-SignatureSetID]`|إزالة التحليل الذكي للأمان الديناميكي|
|`-CheckExclusion -path <path>`|التحقق من استبعاد مسار|
|`-ValidateMapsConnection`|يتحقق من إمكانية اتصال شبكتك بخدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender. سيعمل هذا الأمر على Windows 10 أو الإصدار 1703 أو الإصدارات الأحدث فقط.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>الأخطاء الشائعة في تشغيل الأوامر عبر mpcmdrun.exe

يسرد الجدول التالي الأخطاء الشائعة التي يمكن أن تحدث أثناء استخدام أداة MpCmdRun.

|رسالة خطأ|السبب المحتمل|
|---|---|
|**فشل ValidateMapsConnection (800106BA)** أو **0x800106BA**|تم تعطيل خدمة برنامج الحماية من الفيروسات من Microsoft Defender. تمكين الخدمة والمحاولة مرة أخرى. إذا كنت بحاجة إلى مساعدة في إعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender، فراجع [إعادة تثبيت/تمكين برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **تلميح**: في Windows 10 1909 أو إصدار أقدم، Windows Server 2019 أو إصدار أقدم، كانت الخدمة تسمى سابقا *برنامج الحماية من الفيروسات لـ Windows Defender*.|
|**0x80070667**|تقوم بتشغيل `-ValidateMapsConnection` الأمر من كمبيوتر Windows 10 الإصدار 1607 أو إصدار أقدم، أو Windows Server 2016 أو إصدار أقدم. قم بتشغيل الأمر من جهاز Windows 10 الإصدار 1703 أو أحدث أو Windows Server 2019 أو أحدث.|
|**لا يتم التعرف على MpCmdRun كأوامر داخلية أو خارجية أو برنامج قابل للتشغيل أو ملف دفعي.**|يجب تشغيل الأداة من أي `%ProgramFiles%\Windows Defender` منهما أو `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` (حيث `2012.4-0` قد تختلف لأن تحديثات النظام الأساسي شهرية باستثناء مارس)|
|**فشل ValidateMapsConnection في تأسيس اتصال بالخرائط (hr=80070005 httpcode=450)**|تمت محاولة الأمر باستخدام امتيازات غير كافية. استخدم موجه الأوامر (cmd.exe) كمسؤول.|
|**فشل ValidateMapsConnection في تأسيس اتصال بالخرائط (hr=80070006 httpcode=451)**|جدار الحماية يمنع الاتصال أو يجري فحص SSL.|
|**فشل ValidateMapsConnection في تأسيس اتصال بالخرائط (hr=80004005 httpcode=450)**|المشاكل المحتملة المتعلقة بالشبكة، مثل مشاكل تحليل الاسم|
|**فشل ValidateMapsConnection في تأسيس اتصال بالخرائط (hr=0x80508015**|جدار الحماية يمنع الاتصال أو يجري فحص SSL.|
|**فشل ValidateMapsConnection في إنشاء اتصال بالخرائط (hr=800722F0D**|جدار الحماية يمنع الاتصال أو يجري فحص SSL.|
|**فشل ValidateMapsConnection في تأسيس اتصال بالخرائط (hr=80072EE7 httpcode=451)**|جدار الحماية يمنع الاتصال أو يجري فحص SSL.|

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

- [تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
- [تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md)
- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
