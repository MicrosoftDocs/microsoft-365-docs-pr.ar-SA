---
title: الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات
description: تجنب الأخطاء الشائعة عند تحديد استثناءات عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: الاستثناءات، والملفات، والملحق، ونوع الملف، واسم المجلد، واسم الملف، والمسح الضوئي
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/19/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: b5dc8832839c86fee98e9f27264b70e6a63f380c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790691"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender 

**منصات**
- بالنسبة لنظام التشغيل
- ماك
- ينكس

يمكنك تحديد قائمة استبعاد للعناصر التي لا تريد برنامج الحماية من الفيروسات من Microsoft Defender فحصها. يمكن أن تحتوي هذه العناصر المستبعدة على تهديدات تجعل جهازك عرضة للخطر. تصف هذه المقالة بعض الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات.

قبل تحديد قوائم الاستبعاد، راجع [التوصيات لتعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>استبعاد بعض العناصر الموثوق بها

يجب عدم استبعاد بعض الملفات أو أنواع الملفات أو المجلدات أو العمليات من الفحص على الرغم من أنك تثق بها لتكون غير ضارة.

لا تقم بتعريف الاستثناءات لمواقع المجلدات وملحقات الملفات والعمليات المدرجة في الأقسام التالية:
- مواقع المجلدات
- ملحقات الملفات
- العمليات

### <a name="folder-locations"></a>مواقع المجلدات

بشكل عام، لا تحدد الاستثناءات لمواقع المجلدات التالية:

`%systemdrive%`

`C:`

`C:\`

`C:\*`

`%ProgramFiles%\Java`

`C:\Program Files\Java`

`%ProgramFiles%\Contoso\`

`C:\Program Files\Contoso\`

`%ProgramFiles(x86)%\Contoso\`

`C:\Program Files (x86)\Contoso\`

`C:\Temp`

`C:\Temp\`

`C:\Temp\*`

`C:\Users\`

`C:\Users\*`

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**لاحظ الاستثناء التالي SharePoint**: قم باستبعاد `C:\Users\ServiceAccount\AppData\Local\Temp` عند استخدام [الحماية من الفيروسات على مستوى الملف في SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**لاحظ الاستثناء التالي SharePoint**: قم باستبعاد `C:\Users\Default\AppData\Local\Temp` عند استخدام [الحماية من الفيروسات على مستوى الملف في SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).

`%Windir%\Prefetch`

`C:\Windows\Prefetch`

`C:\Windows\Prefetch\`

`C:\Windows\Prefetch\*`

`%Windir%\System32\Spool`

`C:\Windows\System32\Spool`

`C:\Windows\System32\CatRoot2`
`%Windir%\Temp`

`C:\Windows\Temp`

`C:\Windows\Temp\`

`C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>أنظمة Linux وmacOS الأساسية

`/`

`/bin`

`/sbin`

`/usr/lib`


### <a name="file-extensions"></a>ملحقات الملفات

بشكل عام، لا تحدد الاستثناءات لملحقات الملفات التالية:

`.7z`

`.bat`

`.bin`

`.cab`

`.cmd`

`.com`

`.cpl`

`.dll`

`.exe`

`.fla`

`.gif`

`.gz`

`.hta`

`.inf`

`.java`

`.jar`

`.job`

`.jpeg`

`.jpg`

`.js`

`.ko`

`.ko.gz`

`.msi`

`.ocx`

`.png`

`.ps1`

`.py`

`.rar`

`.reg`

`.scr`

`.sys`

`.tar`

`.tmp`

`.url`

`.vbe`

`.vbs`

`.wsf`

`.zip`

### <a name="processes"></a>العمليات

بشكل عام، لا تحدد الاستثناءات للعمليات التالية:

`AcroRd32.exe`

`bitsadmin.exe`

`excel.exe`

`iexplore.exe`

`java.exe`

`outlook.exe`

`psexec.exe`

`powerpnt.exe`

`powershell.exe`

`schtasks.exe`

`svchost.exe`

`wmic.exe`

`winword.exe`

`wuauclt.exe`

`addinprocess.exe`

`addinprocess32.exe`

`addinutil.exe`

`bash.exe`

`bginfo.exe`

`cdb.exe`

`csi.exe`

`dbghost.exe`

`dbgsvc.exe`

`dnx.exe`

`dotnet.exe`

`fsi.exe`

`fsiAnyCpu.exe`

`kd.exe`

`ntkd.exe`

`lxssmanager.dll`

`msbuild.exe`

`mshta.exe`

`ntsd.exe`

`rcsi.exe`

`system.management.automation.dll`

`windbg.exe`

#### <a name="linux-and-macos-platforms"></a>أنظمة Linux وmacOS الأساسية

`bash`

`sh`

`python` و `python3`

`java`

`zsh`

> [!NOTE]
> يمكنك اختيار استبعاد أنواع الملفات، مثل `.gif`، `.jpg``.jpeg`أو `.png` إذا كانت بيئتك تحتوي على برنامج حديث ومحدث مع نهج تحديث صارم للتعامل مع أي ثغرات أمنية.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>استخدام اسم الملف فقط في قائمة الاستبعاد

قد يكون للبرامج الضارة نفس اسم الملف الذي تثق به وتريد استبعاده من الفحص. لذلك، لتجنب استبعاد البرامج الضارة المحتملة من الفحص، استخدم مسارا مؤهلا بالكامل إلى الملف الذي تريد استبعاده بدلا من استخدام اسم الملف فقط. على سبيل المثال، إذا كنت تريد الاستبعاد `Filename.exe` من الفحص، فاستخدم المسار الكامل إلى الملف، مثل `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>استخدام قائمة استبعاد واحدة لأحمال عمل خادم متعددة

لا تستخدم قائمة استبعاد واحدة لتعريف الاستثناءات لأحمال عمل خادم متعددة. تقسيم الاستثناءات لأحمال عمل التطبيقات أو الخدمات المختلفة إلى قوائم استثناء متعددة. على سبيل المثال، يجب أن تكون قائمة الاستبعاد لحمل عمل IIS Server مختلفة عن قائمة الاستبعاد لحمل العمل SQL Server.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>استخدام متغيرات البيئة غير الصحيحة كأحرف بدل في اسم الملف ومسار المجلد أو قوائم استبعاد الملحق

تعمل برنامج الحماية من الفيروسات من Microsoft Defender Service في سياق النظام باستخدام حساب LocalSystem، ما يعني أنها تحصل على معلومات من متغير بيئة النظام، وليس من متغير بيئة المستخدم. يقتصر استخدام متغيرات البيئة كحرف بدل في قوائم الاستبعاد على متغيرات النظام وتلك التي تنطبق على العمليات التي تعمل كحساب NT AUTHORITY\SYSTEM. لذلك، لا تستخدم متغيرات بيئة المستخدم كأحرف بدل عند إضافة استثناءات برنامج الحماية من الفيروسات من Microsoft Defender المجلد والعمليات. راجع الجدول ضمن [متغيرات بيئة النظام](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) للحصول على قائمة كاملة بمتغيرات بيئة النظام.

راجع [استخدام أحرف البدل في اسم الملف ومسار المجلد أو قوائم استثناء الملحق](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) للحصول على معلومات حول كيفية استخدام أحرف البدل في قوائم الاستبعاد.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
