---
title: استخدم سطر الأوامر لإدارة برنامج الحماية من الفيروسات من Microsoft Defender
description: قم برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي وتكوين حماية الجيل التالي باستخدام أداة مساعدة مخصصة لخط الأوامر.
keywords: تشغيل فحص windows defender، تشغيل مسح الحماية من الفيروسات من سطر الأوامر، تشغيل فحص windows defender من سطر الأوامر، mpcmdrun، defender
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
ms.openlocfilehash: f7ae9c9d0986463b6d6368edd0dac050600e3373
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63573883"
---
# <a name="configure-and-manage-microsoft-defender-antivirus-with-the-mpcmdrunexe-command-line-tool"></a>تكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام mpcmdrun.exe سطر الأوامر

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك تنفيذ دالات متنوعة في برنامج الحماية من الفيروسات من Microsoft Defender باستخدام أداة **سطر الأوامر المخصصة** mpcmdrun.exe. تكون هذه الأداة المساعدة مفيدة عندما تريد أتمتة برنامج الحماية من الفيروسات من Microsoft Defender المهام. يمكنك العثور على الأداة المساعدة في `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. تشغيله من موجه أوامر.

> [!TIP]
> قد تحتاج إلى فتح إصدار على مستوى المسؤول من موجه الأوامر. عند البحث عن **موجه الأوامر** على قائمة البدء، اختر **تشغيل كمسؤول**. إذا كنت تقوم بتشغيل إصدار نظام أساسي محدث من Microsoft Defender لمكافحة البرامج الضارة، فتابع `MpCmdRun` التشغيل من الموقع التالي: `C:\ProgramData\Microsoft\Windows Defender\Platform\<antimalware platform version>`. لمزيد من المعلومات حول النظام الأساسي لمكافحة البرامج الضارة، راجع برنامج الحماية من الفيروسات من Microsoft Defender [الأساسية والتحديثات](manage-updates-baselines-microsoft-defender-antivirus.md).

تستخدم الأداة المساعدة MpCmdRun بناء الجملة التالي:

```console
MpCmdRun.exe [command] [-options]
```

فيما يلي مثال على ذلك:

```console
MpCmdRun.exe -Scan -ScanType 2
```

في مثالنا، تبدأ الأداة المساعدة MpCmdRun فحصا كاملا لمكافحة الفيروسات على الجهاز.

## <a name="commands"></a>الأوامر

|الأمر|الوصف|
|---|---|
|`-?`**أو** `-h`|عرض جميع الخيارات المتوفرة لأداة MpCmdRun|
|`-Scan [-ScanType [<value>]] [-File <path> [-DisableRemediation] [-BootSectorScan] [-CpuThrottling]] [-Timeout <days>] [-Cancel]`|فحص البرامج الضارة. قيم **ل ScanType** هي:<p>**0** افتراضي، وفقا لتكوينك<p>**1** فحص سريع<p>**2** فحص كامل<p>**3** ملف وفحص مخصص للد الدليل.<p>يتم تشغيل وحدة المعالجة المركزية وفقا لتكوينات النهج|
|`-Trace [-Grouping #] [-Level #]`|بدء تتبع التشخيص|
|`-GetFiles [-SupportLogLocation <path>]`|تجمع معلومات الدعم. راجع "[تجميع البيانات التشخيصية](collect-diagnostic-data.md)"|
|`-GetFilesDiagTrack`|تماما مثل `-GetFiles`، ولكن الإخراجات إلى مجلد DiagTrack المؤقت|
|`-RemoveDefinitions [-All]`|استعادة معلومات الأمان المثبتة إلى نسخة احتياطية سابقة أو إلى المجموعة الافتراضية الأصلية|
|`-RemoveDefinitions [-DynamicSignatures]`|إزالة معلومات الأمان التي تم تنزيلها ديناميكيا فقط|
|`-RemoveDefinitions [-Engine]`|استعادة المحرك المثبت السابق|
|`-SignatureUpdate [-UNC \|-MMPC]`|التحقق من وجود تحديثات جديدة لذكاء الأمان|
|`-Restore  [-ListAll \|[[-Name <name>] [-All] \|[-FilePath <filePath>]] [-Path <path>]]`|استعادة عنصر (عناصر) معزولة أو قوائم بها|
|`-AddDynamicSignature [-Path]`|تحميل معلومات الأمان الديناميكية|
|`-ListAllDynamicSignatures`|تسرد معلومات الأمان الديناميكية التي تم تحميلها|
|`-RemoveDynamicSignature [-SignatureSetID]`|إزالة معلومات الأمان الديناميكية|
|`-CheckExclusion -path <path>`|التحقق مما إذا كان المسار مستبعدا أم لا|
|`-ValidateMapsConnection`|تتحقق من أن شبكتك يمكنها التواصل مع برنامج الحماية من الفيروسات من Microsoft Defender السحابية. لن يعمل هذا الأمر إلا على Windows 10 الإصدار 1703 أو الإصدارات الأحدث.|

## <a name="common-errors-in-running-commands-via-mpcmdrunexe"></a>الأخطاء الشائعة في تشغيل الأوامر عبر mpcmdrun.exe

يسرد الجدول التالي الأخطاء الشائعة التي يمكن أن تحدث أثناء استخدام أداة MpCmdRun.

|رسالة خطأ|السبب المحتمل|
|---|---|
|**فشل التحقق من صحةMapsConnection (800106BA)** **أو 0x800106BA**|تم برنامج الحماية من الفيروسات من Microsoft Defender الخدمة. تمكين الخدمة والمحاولة مرة أخرى. إذا كنت بحاجة إلى مساعدة لإعادة تمكين برنامج الحماية من الفيروسات من Microsoft Defender، فشاهد إعادة [تثبيت/تمكين برنامج الحماية من الفيروسات من Microsoft Defender نقاط النهاية](switch-to-mde-phase-2.md#reinstallenable-microsoft-defender-antivirus-on-your-endpoints).<p> **تلميح**: في Windows 10 1909 أو أكثر، Windows Server 2019 أو الإصدارات الأقدم، كانت الخدمة تسمى *برنامج الحماية من الفيروسات لـ Windows Defender*.|
|**0x80070667**|تقوم بتشغيل الأمر من `-ValidateMapsConnection` كمبيوتر يعمل Windows 10 1607 أو إصدار أقدم، أو Windows Server 2016 أو إصدار أقدم. تشغيل الأمر من جهاز Windows 10 1703 أو إصدار أحدث، أو Windows Server 2019 أو أحدث.|
|**لا يتم التعرف على MpCmdRun على أنه أمر داخلي أو خارجي أو برنامج يمكن تشغيله أو ملف دفعة.**|يجب تشغيل الأداة إما من `%ProgramFiles%\Windows Defender` `C:\ProgramData\Microsoft\Windows Defender\Platform\4.18.2012.4-0` أو (حيث `2012.4-0` قد تختلف نظرا لأن تحديثات النظام الأساسي شهرية باستثناء مارس)|
|**فشل التحقق من صحةMapsConnection في إنشاء اتصال ب MAPS (hr=80070005 httpcode=450)**|تم محاولة الأمر باستخدام امتيازات غير كافية. استخدم موجه الأوامر (cmd.exe) كمسؤول.|
|**فشل التحقق من صحةMapsConnection في إنشاء اتصال ب MAPS (hr=80070006 httpcode=451)**|يقوم جدار الحماية بحظر الاتصال أو إجراء فحص SSL.|
|**فشل التحقق من صحةMapsConnection في إنشاء اتصال ب MAPS (hr=80004005 httpcode=450)**|المشاكل المحتملة المتعلقة بالشبكة، مثل مشاكل حل الاسم|
|**فشل التحقق من صحةMapsConnection في إنشاء اتصال ب MAPS (hr=0x80508015**|يقوم جدار الحماية بحظر الاتصال أو إجراء فحص SSL.|
|**فشل التحقق من صحةMapsConnection في إنشاء اتصال ب MAPS (hr=800722F0D**|يقوم جدار الحماية بحظر الاتصال أو إجراء فحص SSL.|
|**فشل التحقق من صحةMapsConnection في إنشاء اتصال ب MAPS (hr=80072EE7 httpcode=451)**|يقوم جدار الحماية بحظر الاتصال أو إجراء فحص SSL.|

## <a name="see-also"></a>راجع أيضًا

- [تكوين ميزات برنامج الحماية من الفيروسات من Microsoft Defender](configure-microsoft-defender-antivirus-features.md)
- [تكوين اتصالات الشبكة برنامج الحماية من الفيروسات من Microsoft Defender والتحقق من صحتها](configure-network-connections-microsoft-defender-antivirus.md)
- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
