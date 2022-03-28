---
title: إنشاء حزمة
description: كيفية إنشاء الحزمة
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 02/28/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 277c185b633263a12687eec5a8eb9a1a34e1dbed
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/17/2022
ms.locfileid: "63574763"
---
# <a name="build-a-package"></a>إنشاء حزمة
الحزمة هي ملف .zip يحتوي على برامج نصية ثنائية واختبارية للتطبيق، وهو الشرط الأساسي لاستخدام Test Base. سيرشدك هذا "العرض السريع" إلى إنشاء الحزمة الأولى، التي يمكنك من خلالها إجراء اختبار "خارج الصندوق" على التطبيق. 
  
*    *يقوم اختبار "خارج المربع" **(OOB)** بإجراء تثبيت التطبيق الخاص بك، ثم تشغيله، أو إغلاقه، أو إلغاء تثبيته. بعد التثبيت، يتم تكرار روتين إغلاق التشغيل 30 مرة قبل تشغيل إلغاء تثبيت واحد. يوفر لك اختبار OOB بيانات قياس بيانات قياسية على الحزمة لمقارنتها عبر Windows البيانات.*  
    
بشكل اختياري، يمكنك تنزيل [الحزمة العينة](https://aka.ms/testbase-sample-package) الخاصة بالإشارة إليها والبدء بها. 

## <a name="create-a-folder-structure"></a>إنشاء بنية مجلد 

في الكمبيوتر المحلي، أنشئ بنية مجلد كما يلي:<br> 
![بنية المجلد المستخدمة لإنشاء حزمة](Media/buildpackage1.png)

يتم استخدام هذه المجلدات:
* **App\bin**: احفظ التطبيق والتبعية الثنائيات.<br> 
* **التطبيقات\البرامج النصية**: احفظ البرامج النصية لتثبيت تطبيقك أو بدء تشغيله أو إغلاقه أو إلغاء تثبيته.<br> 
* **App\logs**: يجب أن تقوم البرامج النصية إخراج سجلات إلى هذا المجلد، ثم يمكنك تنزيل السجلات وتحليلها بعد الانتهاء من الاختبار.<br> 

## <a name="copy-binary-files"></a>نسخ ملف (ملفات) ثنائي
انسخ ملفات تثبيت التطبيق إلى **App\bin**. إذا كان التطبيق الخاص بك به تبعيات، يجب تثبيتها أولا. أيضا، انسخ ملفات تثبيت التبعية إلى **App\bin**.<br> 
![موقع ملف (ملفات) التطبيق في المجلد](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>إضافة برامج PowerShell النصية
لتنفيذ اختبار OOB، ستحتاج إلى إضافة برامج PowerShell النصية لتثبيت تطبيقك، ثم بدء تشغيله أو إغلاقه أو إلغاء تثبيته.
> [!NOTE]  
> *في اختبار OOB،* يلزم تثبيت البرامج النصية أو تشغيلها أو إغلاقها، بينما يكون إلغاء تثبيت البرنامج النصي اختياريا.
    
يجب إضافة البرنامج النصي إلى المجلد كما يلي:  
![موقع ملفات البرامج النصية في powershell في المجلد](Media/buildpackage3.png)

يتضمن البرنامج النصي عادة السلوكيات التالية:<br> 
-   **قم بتشغيل الأوامر لتثبيت/تشغيل/إغلاق/إلغاء تثبيت التطبيق**. على سبيل المثال، إذا كان تطبيقك ملف MSI، ف [قم بتشغيل msiexec](/windows-server/administration/windows-commands/msiexec) لتثبيته. <br> 
-   **تحقق من نتيجة عملية التثبيت/التشغيل/الإغلاق/** إلغاء التثبيت، وإرجاع رمز الخروج الصفري إذا كانت النتيجة متوقعة. ستكتب Test Base علامة على البرنامج النصي الذي يتم تشغيله كفشل إذا كان يرجع رمز الخروج غير الصفري.<br> 
-   **احفظ ما يكفي من السجلات**، واحفظ السجلات الصحيحة لاستخدامها في المستقبل.<br> 

الرجاء الرجوع إلى الأمثلة التالية. يمكنك ببساطة نسخها إلى ملفاتك وإدائها وفقا لذلك. <br>

**مثال لتثبيت البرنامج النصي (App\scripts\install\job.ps1)**
```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"


        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Installing TestBaseM365 Digital Clock")
        push-location "..\..\bin"
        if ([Environment]::Is64BitProcess) {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        else {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        $arguments = "/i "+$installer_name+" /quiet /L*v "+"$log_dir"+"\atp-client-installation.log"

        $installer = Start-Process msiexec.exe $arguments -wait -passthru
        pop-location

        if ($installer.exitcode -eq 0) {
            log("Installation succesful as $($installer.exitcode)")
        }
        else {
            log("Error: Installation failed as $($installer.exitcode)")
            $exit_code = $installer.exitcode
        }

        log("Installation script finished as $exit_code")
        pop-location
        exit $exit_code
```

**مثال على تشغيل البرنامج النصي (App\scripts\launch\job.ps1)**
```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"

        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Launch TestBaseM365 Digital Clock")

        $PROCESS_NAME = "DigitalClock"
        $exePath = "C:\Program Files\Test Base M365\DigitalClock\DigitalClock.exe"

        Start-Process -FilePath $exePath

         if (Get-Process -Name $PROCESS_NAME) {
                log("Launch successfully $PROCESS_NAME...") 
                $exit_code = 0
         }
         else {
            log("Not launched $PROCESS_NAME...") 
            $exit_code = 1
         }

        log("Launch script finished as $exit_code")
        pop-location
        exit $exit_code 
```

## <a name="compress-to-zip-file"></a>ضغط إلى ملف zip
بعد إعداد البرامج النصية وال الثنائيات، يمكنك المتابعة لضغط المجلد إلى ملف zip. انقر بضغطة زر الماوس الأيمن فوق مجلد التطبيق، وحدد **ضغط إلى ملف ZIP**.<br>
![ضغط إلى ملف zip](Media/buildpackage4.png)


## <a name="verify-your-package-locally-optional"></a>التحقق من الحزمة محليا (اختياري)
بعد إنشاء الحزمة البريدية، يمكنك تحميلها إلى حساب Test Base الخاص بك. <br>
ومع ذلك، من أفضل الممارسات تشغيل الاختبار محليا لضمان عمل البرامج النصية بشكل صحيح قبل التحميل. يمكن للاختبار المحلي تحديد المشاكل بسرعة وتسريع عملية التحميل. للتحقق محليا، اتبع الخطوات أدناه:<br>
1.  إعداد VM (جهاز ظاهري)<br>
    نوصي باستخدام جهاز ظاهري لهذا الاختبار المحلي نظرا لأن بيئة Windows مطلوبة حاليا لكل اختبار. من السهل إنشاء Windows VM على Azure (تشغيل سريع [: Windows](/azure/virtual-machines/windows/quick-create-portal) جهاز ظاهري)، يمكنك تحديد إصدار Windows (صورة) مناسب للاختبار، على سبيل المثال، Windows 10 Pro، الإصدار *21H2.*<br>

2.  نسخ الحزمة إلى VM<br>
    هناك العديد من الطرق لنسخ ملف الحزمة إلى VM. إذا كنت تستخدم Azure VM، يمكنك اختيار:
     -  انسخ الملف مباشرة في اتصال سطح المكتب البعيد. <br>
     -  استخدام مشاركة ملف Azure ([Quickstart: إنشاء ملف Azure وإدارته](/azure/storage/files/storage-files-quick-create-use-windows))
    
    يمكنك إنشاء مجلد معين لهذا الاختبار ونسخ ملف الحزمة ضمن هذا المجلد. على سبيل المثال *، C:\TestBase*.<br>
3.  اختبار الحزمة<br>
    افتح Windows PowerShell، والتبديل إلى الدليل الذي يحتوي على الحزمة، على سبيل المثال، قرص C:\TestBase، وابدأ بتشغيل الاختبارات على الحزمة:<br>
    أ.  استخراج ملف الحزمة.
     -  *Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase*<br>
    
    ب.  تشغيل البرنامج النصي لتثبيت.  
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    c.  أعد تشغيل VM إذا لزم الأمر.<br>
    
    د.  تشغيل البرنامج النصي للتشغيل.
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    e.  تشغيل إغلاق البرنامج النصي.
     -  *C:\TestBase\App\scripts\close\job.ps1*<br>
    
    f.  تشغيل إلغاء تثبيت البرنامج النصي (إذا كان لديك برنامج نصي).
     -  *C:\TestBase\App\scripts\uninstall\job.ps1*<br>
    
    بعد كل خطوة، يمكنك التحقق مما إذا كانت هناك أي مشاكل في البرنامج النصي. إذا كانت كل البرامج النصية تعمل كما هو متوقع، فإن حزمتك جاهزة للتحميل إلى حساب Test Base الخاص بك.


## <a name="next-steps"></a>الخطوات التالية
[Upload حزمة](uploadApplication.md)
 
 
