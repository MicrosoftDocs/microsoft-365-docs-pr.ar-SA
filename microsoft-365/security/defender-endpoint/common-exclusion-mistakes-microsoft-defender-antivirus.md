---
title: الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات
description: تجنب الأخطاء الشائعة عند تحديد الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي.
keywords: الاستثناءات والملفات والملحقات ونوع الملف واسم المجلد واسم الملف والفحص
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
ms.openlocfilehash: 73234fd929406da475455baf21fbbf463216c660
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/25/2021
ms.locfileid: "63570223"
---
# <a name="common-mistakes-to-avoid-when-defining-exclusions"></a>الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك تحديد قائمة استثناء للعناصر التي لا تريد برنامج الحماية من الفيروسات من Microsoft Defender مسحها ضوئيا. قد تحتوي هذه العناصر المستبعدة على تهديدات تجعل جهازك عرضة للتأثر. تصف هذه المقالة بعض الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات.

قبل تحديد قوائم الاستثناء، راجع التوصيات [تعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions).

## <a name="excluding-certain-trusted-items"></a>استبعاد عناصر موثوق بها معينة

يجب عدم استبعاد بعض الملفات أو أنواع الملفات أو المجلدات أو العمليات من المسح الضوئي على الرغم من أنك تثق بها على أنها غير ضارة.

لا تحدد الاستثناءات لمواقع المجلدات وملحقات الملفات والعمليات المدرجة في المقاطع التالية:
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

`C:\Users\<UserProfileName>\AppData\Local\Temp\`**لاحظ الاستثناء التالي ل SharePoint**: استثني `C:\Users\ServiceAccount\AppData\Local\Temp` عند استخدام [الحماية من](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9) الفيروسات على مستوى الملف في SharePoint.

`C:\Users\<UserProfileName>\AppData\LocalLow\Temp\`**لاحظ الاستثناء التالي ل SharePoint**: استثني `C:\Users\Default\AppData\Local\Temp` عند استخدام [الحماية من](https://support.microsoft.com/office/certain-folders-may-have-to-be-excluded-from-antivirus-scanning-when-you-use-file-level-antivirus-software-in-sharepoint-01cbc532-a24e-4bba-8d67-0b1ed733a3d9) الفيروسات على مستوى الملف في SharePoint.

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

#### <a name="linux-and-macos-platforms"></a>الأنظمة الأساسية ل Linux و macOS

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

#### <a name="linux-and-macos-platforms"></a>الأنظمة الأساسية ل Linux و macOS

`bash`

`sh`

`python` و `python3`

`java`

`zsh`

> [!NOTE]
> يمكنك اختيار `.gif`استبعاد أنواع الملفات، مثل ، `.jpg`أو ، `.jpeg`أو إذا `.png` كانت بيئتك لديها برنامج حديث ومحدث مع نهج تحديث صارم لمعالجة أي نقاط ضعف.

## <a name="using-just-the-file-name-in-the-exclusion-list"></a>استخدام اسم الملف فقط في قائمة الاستثناء

قد يكون للبرامج الضارة نفس اسم الملف الذي تثق به وتريد استبعاده من الفحص. لذلك، لتجنب استبعاد البرامج الضارة المحتملة من الفحص، استخدم مسارا مؤهلا بالكامل إلى الملف الذي تريد استبعاده بدلا من استخدام اسم الملف فقط. على سبيل المثال، إذا كنت تريد الاستبعاد `Filename.exe` من الفحص، فاستخدم المسار الكامل إلى الملف، مثل `C:\program files\contoso\Filename.exe`.

## <a name="using-a-single-exclusion-list-for-multiple-server-workloads"></a>استخدام قائمة استثناء واحدة لأحمال عمل خوادم متعددة

لا تستخدم قائمة استثناء واحدة لتعريف استثناءات لأحمال عمل خوادم متعددة. تقسيم الاستثناءات لأحمال العمل المختلفة للتطبيقات أو الخدمات إلى قوائم استثناءات متعددة. على سبيل المثال، يجب أن تختلف قائمة الاستثناء الخاصة بأحمال عمل خادم IIS عن قائمة الاستثناء الخاصة SQL Server العمل.

## <a name="using-incorrect-environment-variables-as-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists"></a>استخدام متغيرات البيئة غير الصحيحة ك أحرف بدل في اسم الملف ومسار المجلد أو قوائم استثناءات الملحقات

برنامج الحماية من الفيروسات من Microsoft Defender تشغيل الخدمة في سياق النظام باستخدام حساب LocalSystem، مما يعني أنها تحصل على معلومات من متغير بيئة النظام، وليس من متغير بيئة المستخدم. يقتصر استخدام متغيرات البيئة ك أحرف بدل في قوائم الاستثناء على متغيرات النظام وتلك المطبقة على العمليات التي يتم تشغيلها ك حساب NT AUTHORITY\SYSTEM. لذلك، لا تستخدم متغيرات بيئة المستخدمين ك أحرف بدل عند برنامج الحماية من الفيروسات من Microsoft Defender استثناءات المجلدات و العملية. راجع الجدول ضمن [متغيرات بيئة النظام](configure-extension-file-exclusions-microsoft-defender-antivirus.md#system-environment-variables) للحصول على قائمة كاملة من متغيرات بيئة النظام.

راجع [استخدام أحرف البدل](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists) في اسم الملف ومسار المجلد أو قوائم استثناءات الملحقات للحصول على معلومات حول كيفية استخدام أحرف البدل في قوائم الاستثناء.
