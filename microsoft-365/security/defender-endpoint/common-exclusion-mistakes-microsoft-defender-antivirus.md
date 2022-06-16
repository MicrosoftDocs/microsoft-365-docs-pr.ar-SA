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
ms.date: 06/16/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 99d59c2027d3b34ad5c9c19444a51dd08cc22276
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128647"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- الخطة 1 من Microsoft Defender لنقطة النهاية
- برنامج الحماية من الفيروسات من Microsoft Defender 

**الأنظمة الأساسية**

- بالنسبة لنظام التشغيل
- macOS
- ينكس

> [!IMPORTANT]
> **أضف الاستثناءات بحذر**. تقلل الاستثناءات الخاصة بمسح برنامج الحماية من الفيروسات من Microsoft Defender مستوى الحماية للأجهزة.

يمكنك تحديد قائمة استبعاد للعناصر التي لا تريد برنامج الحماية من الفيروسات من Microsoft Defender فحصها. ومع ذلك، يمكن أن تحتوي العناصر المستبعدة على تهديدات تجعل جهازك عرضة للخطر. تصف هذه المقالة بعض الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات.

قبل تحديد قوائم الاستبعاد، راجع [التوصيات لتعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>استبعاد بعض العناصر الموثوق بها

يجب عدم استبعاد بعض الملفات أو أنواع الملفات أو المجلدات أو العمليات من الفحص على الرغم من أنك تثق بها لتكون غير ضارة.

لا تحدد الاستثناءات لمواقع المجلدات وملحقات الملفات والعمليات المدرجة في الأقسام التالية:

- [مواقع المجلدات](#folder-locations)
- [ملحقات الملفات](#file-extensions)
- [العمليات](#processes)

### <a name="folder-locations"></a>مواقع المجلدات

> [!IMPORTANT]
> يجب عدم استبعاد بعض المجلدات من عمليات الفحص لأنها في نهاية المطاف مجلدات يمكن أن يتم إسقاط الملفات الضارة فيها.

بشكل عام، لا تحدد الاستثناءات لمواقع المجلدات التالية:

- `%systemdrive%`
- `C:`، `C:\`أو `C:\*`
- `%ProgramFiles%\Java` او `C:\Program Files\Java`
- `%ProgramFiles%\Contoso\`، `C:\Program Files\Contoso\`أو `%ProgramFiles(x86)%\Contoso\`، أو `C:\Program Files (x86)\Contoso\`
- `C:\Temp`، `C:\Temp\`أو `C:\Temp\*`
- `C:\Users\` او `C:\Users\*`
- `C:\Users\<UserProfileName>\AppData\Local\Temp\` أو `C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`. **لاحظ الاستثناءات الهامة التالية SharePoint**: **قم باستبعاد** `C:\Users\ServiceAccount\AppData\Local\Temp` أو `C:\Users\Default\AppData\Local\Temp` عند استخدام [الحماية من الفيروسات على مستوى الملف في SharePoint](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9).
- `%Windir%\Prefetch`، `C:\Windows\Prefetch`أو `C:\Windows\Prefetch\`، أو `C:\Windows\Prefetch\*`
- `%Windir%\System32\Spool` او `C:\Windows\System32\Spool`
- `C:\Windows\System32\CatRoot2`
- `%Windir%\Temp`، `C:\Windows\Temp`أو `C:\Windows\Temp\`، أو `C:\Windows\Temp\*`

#### <a name="linux-and-macos-platforms"></a>Linux وأنظمة macOS الأساسية

بشكل عام، لا تحدد الاستثناءات لمواقع المجلدات التالية:

- `/`
- `/bin` او `/sbin`
- `/usr/lib`

### <a name="file-extensions"></a>ملحقات الملفات

> [!IMPORTANT]
> يجب عدم استبعاد بعض ملحقات الملفات لأنها يمكن أن تكون أنواع ملفات تستخدم في هجوم.

بشكل عام، لا تحدد الاستثناءات لملحقات الملفات التالية:

- `.7z`
- `.bat`
- `.bin`
- `.cab`
- `.cmd`
- `.com`
- `.cpl`
- `.dll`
- `.exe`
- `.fla`
- `.gif`
- `.gz`
- `.hta`
- `.inf`
- `.java`
- `.jar`
- `.job`
- `.jpeg`
- `.jpg`
- `.js`
- `.ko` او `.ko.gz`
- `.msi`
- `.ocx`
- `.png`
- `.ps1`
- `.py`
- `.rar`
- `.reg`
- `.scr`
- `.sys`
- `.tar`
- `.tmp`
- `.url`
- `.vbe`
- `.vbs`
- `.wsf`
- `.zip`

### <a name="processes"></a>العمليات

> [!IMPORTANT]
> لا ينبغي استبعاد بعض العمليات لأنها تستخدم في أثناء الهجمات.

بشكل عام، لا تحدد الاستثناءات للعمليات التالية:

- `AcroRd32.exe`
- `addinprocess.exe`
- `addinprocess32.exe`
- `addinutil.exe`
- `bash.exe`
- `bginfo.exe`
- `bitsadmin.exe`
- `cdb.exe`
- `csi.exe`
- `dbghost.exe`
- `dbgsvc.exe`
- `dnx.exe`
- `dotnet.exe`
- `excel.exe`
- `fsi.exe`
- `fsiAnyCpu.exe`
- `iexplore.exe`
- `java.exe`
- `kd.exe`
- `lxssmanager.dll`
- `msbuild.exe`
- `mshta.exe`
- `ntkd.exe`
- `ntsd.exe`
- `outlook.exe`
- `psexec.exe`
- `powerpnt.exe`
- `powershell.exe`
- `rcsi.exe`
- `svchost.exe`
- `schtasks.exe`
- `system.management.automation.dll`
- `windbg.exe`
- `winword.exe`
- `wmic.exe`
- `wuauclt.exe`

> [!NOTE]
> يمكنك اختيار استبعاد أنواع الملفات، مثل `.gif`، `.jpg``.jpeg`أو `.png` إذا كانت بيئتك تحتوي على برنامج حديث ومحدث مع نهج تحديث صارم للتعامل مع أي ثغرات أمنية.

#### <a name="linux-and-macos-platforms"></a>Linux وأنظمة macOS الأساسية

بشكل عام، لا تحدد الاستثناءات للعمليات التالية:

- `bash`
- `java`
- `python` و `python3`
- `sh`
- `zsh`

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>استخدام اسم الملف فقط في قائمة الاستبعاد

قد يكون للبرامج الضارة نفس اسم الملف الذي تثق به وتريد استبعاده من الفحص. لذلك، لتجنب استبعاد البرامج الضارة المحتملة من الفحص، استخدم مسارا مؤهلا بالكامل إلى الملف الذي تريد استبعاده بدلا من استخدام اسم الملف فقط. على سبيل المثال، إذا كنت تريد الاستبعاد `Filename.exe` من الفحص، فاستخدم المسار الكامل إلى الملف، مثل `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>استخدام قائمة استبعاد واحدة لأحمال عمل خادم متعددة

لا تستخدم قائمة استبعاد واحدة لتعريف الاستثناءات لأحمال عمل الخادم المتعددة. تقسيم الاستثناءات لأحمال عمل التطبيقات أو الخدمات المختلفة إلى قوائم استثناء متعددة. على سبيل المثال، يجب أن تكون قائمة الاستبعاد لحمل عمل IIS Server مختلفة عن قائمة الاستبعاد لحمل العمل SQL Server.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>استخدام متغيرات البيئة غير الصحيحة كأحرف بدل في اسم الملف ومسار المجلد أو قوائم استبعاد الملحق

تعمل برنامج الحماية من الفيروسات من Microsoft Defender Service في سياق النظام باستخدام حساب LocalSystem، ما يعني أنها تحصل على معلومات من متغير بيئة النظام، وليس من متغير بيئة المستخدم. يقتصر استخدام متغيرات البيئة كحرف بدل في قوائم الاستبعاد على متغيرات النظام وتلك التي تنطبق على العمليات التي تعمل كحساب NT AUTHORITY\SYSTEM. لذلك، لا تستخدم متغيرات بيئة المستخدم كأحرف بدل عند إضافة استثناءات برنامج الحماية من الفيروسات من Microsoft Defender المجلد والعمليات. راجع الجدول ضمن [متغيرات بيئة النظام](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) للحصول على قائمة كاملة بمتغيرات بيئة النظام.

راجع [استخدام أحرف البدل في اسم الملف ومسار المجلد أو قوائم استثناء الملحق](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) للحصول على معلومات حول كيفية استخدام أحرف البدل في قوائم الاستبعاد.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
