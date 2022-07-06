---
title: تحديث ملف جدول مصدر المعلومات الحساسة لتطابق البيانات الدقيقة
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
description: تحديث ملف جدول مصدر المعلومات الحساسة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 310663caae55bb9b5e0d07cb38ba9fa4b45e8a73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621656"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>تحديث ملف جدول مصدر المعلومات الحساسة لتطابق البيانات الدقيقة 

يمكنك تحديث قاعدة بيانات المعلومات الحساسة حتى 5 مرات كل 24 ساعة. سيتعين عليك إعادة تشغيل جدول مصدر المعلومات الحساسة وتحميله.

1. أعد تصدير البيانات الحساسة إلى تطبيق، مثل Microsoft Excel، واحفظ الملف بتنسيق .csv أو تنسيق .tsv أو توجيه (|) المحدد. احتفظ بنفس اسم الملف والموقع الذي استخدمته عند تجزئة الملف وتحميله مسبقا. راجع [، تصدير البيانات المصدر لمطابقة البيانات الدقيقة استنادا إلى نوع المعلومات الحساسة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) للحصول على تفاصيل حول تصدير البيانات الحساسة والحصول عليها في التنسيق الصحيح.

      > [!NOTE]
      > إذا لم تكن هناك أي تغييرات على البنية (أسماء الحقول) لملف جدول مصدر المعلومات الحساسة، فلن تحتاج إلى إجراء أي تغييرات على ملف مخطط قاعدة البيانات عند تحديث البيانات. ولكن إذا كان عليك إجراء تغييرات، فتأكد من تحرير مخطط قاعدة البيانات وحزمة القواعد وفقا لذلك. راجع [، إدارة مخطط مطابقة البيانات الدقيقة](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) للخطوات لتحرير مخطط أو إزالته. انظر، [قم بإنشاء بيانات مطابقة دقيقة لنوع/حزمة قاعدة المعلومات الحساسة](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) للخطوات لتحرير حزمة EDM SIT/rule أو إزالتها.

2. استخدم الإجراءات في [التجزئة وقم بتحميل جدول مصدر المعلومات الحساسة لتطابق أنواع المعلومات الحساسة بدقة مع البيانات](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) لتحميل ملف مصدر جدول المعلومات الحساسة.

3. يمكنك استخدام ["جدول المهام"](/windows/desktop/TaskSchd/task-scheduler-start-page) لأتمتة [التجزئة وتحميل جدول مصدر المعلومات الحساسة لإجراء أنواع المعلومات الحساسة المطابقة تماما للبيانات](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) . يمكنك جدولة المهام باستخدام عدة أساليب:

   |الاسلوب|ما يجب فعله|
   |---|---|
   |PowerShell|راجع وثائق [ScheduledTasks](/powershell/module/scheduledtasks/) [ومثال البرنامج النصي PowerShell](#example-powershell-script-for-task-scheduler) في هذه المقالة|
   |واجهة برمجة تطبيقات مجدول المهام|راجع وثائق ["جدولة المهام"](/windows/desktop/TaskSchd/using-the-task-scheduler)|
   |واجهة مستخدم Windows|في Windows، انقر فوق **"بدء**" واكتب "جدولة المهام". بعد ذلك، في قائمة النتائج، انقر بزر الماوس الأيمن فوق **"جدولة المهام"**، واختر **"تشغيل" كمسؤول**.|

## <a name="example-powershell-script-for-task-scheduler"></a>مثال على برنامج PowerShell النصي لمجدول المهام

يتضمن هذا القسم مثالا على برنامج PowerShell النصي الذي يمكنك استخدامه لجدولة مهامك لتجزئة البيانات وتحميل البيانات المقسمة:

### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>جدولة التجزئة وتحميلها في خطوة مجمعة

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

### <a name="schedule-hashing-and-upload-as-separate-steps"></a>جدولة التجزئة وتحميلها كخطوات منفصلة

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
