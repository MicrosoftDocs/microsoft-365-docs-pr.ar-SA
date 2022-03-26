---
title: أمثلة أوامر الاستجابة المباشرة
description: تعرف على كيفية تشغيل أوامر الاستجابة المباشرة الأساسية أو المتقدمة ل Microsoft Defender ل Endpoint، وشاهد أمثلة حول كيفية استخدامها.
keywords: مثال، أمر، cli، بعيد، shell، اتصال، live، استجابة، في الوقت الحقيقي، الأمر، البرنامج النصي، إعادة المعالجة، البحث، التصدير، السجل، إسقاط، تنزيل، ملف
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 325146ba7ed40e27c50eaca490c70d3988b1198f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570155"
---
# <a name="live-response-command-examples"></a>أمثلة أوامر الاستجابة المباشرة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

تعرف على الأوامر الشائعة المستخدمة في الاستجابة المباشرة وشاهد أمثلة حول كيفية استخدامها عادة.

استنادا إلى الدور الذي تقوم به، يمكنك تشغيل أوامر الاستجابة المباشرة الأساسية أو المتقدمة. لمزيد من المعلومات حول الأوامر الأساسية والمتقدمة، راجع [التحقق من الكيانات على الأجهزة باستخدام الاستجابة المباشرة](live-response.md).

## `analyze`

```console
# Analyze the file malware.txt
analyze file c:\Users\user\Desktop\malware.txt
```

```console
# Analyze the process by PID
analyze process 1234
```

## `connections`

```console
# List active connections in json format using parameter name
connections -output json
```

```console
# List active connections in json format without parameter name
connections json
```

## `dir`

```console
# List files and sub-folders in the current folder (by default it will show relative paths [-relative_path])
dir
```

```console
# List files and sub-folders in the current folder, with their full path
dir -full_path
```

```console
# List files and sub-folders in a specific folder
dir C:\Users\user\Desktop\
```

```console
# List files and subfolders in the current folder in json format
dir -output json
```

## `fileinfo`

```console
# Display information about a file
fileinfo C:\Windows\notepad.exe
```

## `findfile`

```console
# Find file by name
findfile test.txt
```

## `getfile`

```console
# Download a file from a machine
getfile c:\Users\user\Desktop\work.txt
```

```console
# Download a file from a machine, automatically run prerequisite commands
getfile c:\Users\user\Desktop\work.txt -auto
```

> [!NOTE]
>
> لا يمكن تنزيل *أنواع* الملفات التالية باستخدام هذا الأمر من داخل الاستجابة المباشرة:
>
> - [إعادة افصل ملفات النقاط](/windows/desktop/fileio/reparse-points/)
> - [ملفات متباعدة](/windows/desktop/fileio/sparse-files/)
> - إفراغ الملفات
> - الملفات الظاهرية أو الملفات غير الموجودة محليا بشكل كامل
>
> يتم دعم *أنواع الملفات* هذه بواسطة [PowerShell](/powershell/scripting/overview).
>
> استخدم PowerShell كبديل، إذا كنت تواجه مشاكل في استخدام هذا الأمر من داخل Live Response.

## `library`

```console
# List files in the library
library
```

```console
# Delete a file from the library
library delete script.ps1
```

## `processes`

```console
# Show all processes
processes
```

```console
# Get process by pid
processes 123
```

```console
# Get process by pid with argument name
processes -pid 123
```

```console
# Get process by name
processes -name notepad.exe
```

## `putfile`

```console
# Upload file from library
putfile get-process-by-name.ps1
```

```console
# Upload file from library, overwrite file if it exists
putfile get-process-by-name.ps1 -overwrite
```

```console
# Upload file from library, keep it on the machine after a restart
putfile get-process-by-name.ps1 -keep
```

## `registry`

```console
# Show information about the values in a registry key
registry HKEY_CURRENT_USER\Console
```

```console
# Show information about a specific registry value (the double backslash \\ indicates a registry value versus key)
registry HKEY_CURRENT_USER\Console\\ScreenBufferSize
```


## `remediate`

```console
# Remediate file in specific path
remediate file c:\Users\user\Desktop\malware.exe
```

```console
# Remediate process with specific PID
remediate process 7960
```

```console
# Remediate a registry value (the double backslash \\ indicates a registry value versus key)
remediate registry HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run\\SPStartup
```

```console
# See list of all remediated entities
remediate list
```

## `run`

```console
# Run PowerShell script from the library without arguments
run script.ps1
```

```console
# Run PowerShell script from the library with arguments
run get-process-by-name.ps1 -parameters "-processName Registry"
```

> [!NOTE]
>
> بالنسبة لأوامر التشغيل الطويلة مثل '**تشغيل**' أو '**getfile**'، قد تحتاج إلى استخدام الرمز '**&**' في نهاية الأمر لتنفيذ هذا الإجراء في الخلفية.
> سيتيح لك ذلك الاستمرار في التحقق من الجهاز والعودة إلى أمر الخلفية عند القيام باستخدام الأمر الأساسي '**fg**['](live-response.md#basic-commands).

## `scheduledtask`

```console
# Get all scheduled tasks
scheduledtasks
```

```console
# Get specific scheduled task by location and name
scheduledtasks Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Get specific scheduled task by location and name with spacing
scheduledtasks "Microsoft\Configuration Manager\Configuration Manager Health Evaluation"
```

## `undo`

```console
# Restore remediated registry
undo registry HKEY_CURRENT_USER\Console\ScreenBufferSize
```

```console
# Restore remediated scheduledtask
undo scheduledtask Microsoft\Windows\Subscription\LicenseAcquisition
```

```console
# Restore remediated file
undo file c:\Users\user\Desktop\malware.exe
```
