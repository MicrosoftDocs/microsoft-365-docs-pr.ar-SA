---
title: تحديث ملف جدول مصدر معلومات متطابق تماما مع البيانات الحساسة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تحديث ملف جدول مصدر المعلومات الحساس.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 347ff88391a19cb3d8688b1142e524a163159b6f
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575917"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>تحديث البيانات بدقة تتطابق مع ملف جدول مصدر المعلومات الحساس 

يمكنك تحديث قاعدة بيانات المعلومات الحساسة حتى 5 مرات كل 24 ساعة. يجب إعادة البحث عن جدول مصدر المعلومات الحساس وتحميله.

1. يمكنك إعادة تصدير البيانات الحساسة إلى تطبيق، مثل Microsoft Excel، وحفظ الملف بتنسيق .csv بتنسيق .tsv أو تنسيق توجيه (|) المحدد. احتفظ بنفس اسم الملف والموقع الذي استخدمته عندما قمت مسبقا بتفيش الملف وتحميله. راجع تصدير [بيانات المصدر](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) للحصول على معلومات دقيقة تتطابق مع نوع المعلومات الحساسة المستندة إلى البيانات للحصول على تفاصيل حول تصدير البيانات الحساسة والحصول عليها في التنسيق الصحيح.

      > [!NOTE]
      > إذا لم تكن هناك أي تغييرات على البنية (أسماء الحقول) لملف جدول مصدر المعلومات الحساس، فلن تحتاج إلى إجراء أي تغييرات على ملف مخطط قاعدة البيانات عند تحديث البيانات. ولكن إذا كان عليك إجراء تغييرات، فتأكد من تحرير مخطط قاعدة البيانات وحزمة القواعد وفقا لذلك. راجع، [إدارة مخطط مطابقة البيانات الدقيقة](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) لخطوات تحرير مخطط أو إزالته. راجع، [إنشاء بيانات دقيقة تتطابق مع نوع/حزمة](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) قاعدة المعلومات الحساسة لخطوات تحرير حزمة قاعدة/قاعدة/قاعدة EDM أو تحريرها.

2. استخدم الإجراءات الواردة في ["](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) هاش" وحمّل جدول مصدر المعلومات الحساس لكي تتطابق البيانات بدقة مع أنواع المعلومات الحساسة لتحميل ملف مصدر جدول المعلومات الحساس.

2. يمكنك استخدام ["جدول المهام](/windows/desktop/TaskSchd/task-scheduler-start-page) " لأتمتة "هاش" وتحميل جدول مصدر المعلومات الحساس لكي تتطابق البيانات [بدقة مع إجراء أنواع المعلومات الحساسة](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . يمكنك جدولة المهام باستخدام عدة أساليب:

   |الأسلوب|ما يجب فعله|
   |---|---|
   |Windows PowerShell|راجع [وثائق ScheduledTasks](/powershell/module/scheduledtasks/) [ومثال برنامج PowerShell النصي](#example-powershell-script-for-task-scheduler) في هذه المقالة|
   |API لجدولة المهام|راجع [وثائق "جدول المهام](/windows/desktop/TaskSchd/using-the-task-scheduler) "|
   |Windows المستخدم|في Windows، انقر فوق **بدء**، ثم اكتب جدول المهام. بعد ذلك، في قائمة النتائج، انقر ب زر الماوس الأيمن فوق **جدول المهام**، **واختر تشغيل كمسؤول**.|

### <a name="example-powershell-script-for-task-scheduler"></a>مثال برنامج PowerShell النصي لجدول المهام 

يتضمن هذا القسم مثالا عن برنامج PowerShell النصي الذي يمكنك استخدامه لجدولة مهامك لتقحم البيانات وتحميل البيانات المقسمة:

#### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>جدولة عملية التهشح والتحميل في خطوة مدمجة

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

#### <a name="schedule-hashing-and-upload-as-separate-steps"></a>جدولة التهشح وتحميله كلخطوات المنفصلة

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
