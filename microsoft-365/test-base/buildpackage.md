---
title: إنشاء حزمة
description: كيفية إنشاء الحزمة الخاصة بك
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
ms.openlocfilehash: db09d1b182965c0a21945b025601c21d5100212b
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952897"
---
# <a name="build-a-package"></a>إنشاء حزمة

الحزمة هي ملف .zip يحتوي على البرامج النصية الثنائية واختبار التطبيق الخاص بك، وهو المتطلبات الأساسية لاستخدام قاعدة الاختبار. سيرشدك هذا التشغيل السريع إلى إنشاء الحزمة الأولى، والتي يمكنك من خلالها إجراء اختبار خارج الصندوق على التطبيق الخاص بك.

- *يقوم اختبار **خارج الصندوق (OOB)** بإجراء تثبيت للتطبيق الخاص بك وتشغيله وإغلاقه وإلغاء تثبيته. بعد التثبيت، يتكرر روتين إغلاق التشغيل 30 مرة قبل تشغيل إزالة تثبيت واحد. يوفر لك اختبار OOB بيانات تتبع الاستخدام القياسية على الحزمة الخاصة بك للمقارنة عبر إصدارات Windows.*

اختياريا، يمكنك تنزيل [حزمة العينة](https://aka.ms/testbase-sample-package) للرجوع إليها والبدء بها.

## <a name="create-a-folder-structure"></a>إنشاء بنية مجلد

في الكمبيوتر المحلي، قم بإنشاء بنية مجلد كما يلي:

![بنية المجلد المستخدمة لإنشاء حزمة](Media/buildpackage1.png)

يتم استخدام هذه المجلدات:

- **App\bin**: احفظ ثنائيات التطبيق والتبعية.
- **التطبيقات\البرامج النصية**: حفظ البرامج النصية لتثبيت التطبيق الخاص بك وتشغيله وإغلاقه وإلغاء تثبيته.
- **App\logs**: يجب أن تقوم البرامج النصية لإخراج سجلات إلى هذا المجلد، ثم يمكنك تنزيل السجلات وتحليلها بعد الانتهاء من الاختبار.

## <a name="copy-binary-files"></a>نسخ ملف ثنائي (ملفات) ثنائية

انسخ ملفات تثبيت التطبيق إلى **App\bin**. إذا كان التطبيق الخاص بك يحتوي على تبعيات، فيجب تثبيتها أولا. أيضا، انسخ ملفات تثبيت التبعية إلى **App\bin**.

![موقع ملف (ملفات) التطبيق في المجلد](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>إضافة برامج نصية PowerShell

لإجراء اختبار OOB، ستحتاج إلى إضافة برامج PowerShell النصية لتثبيت التطبيق الخاص بك وتشغيله وإغلاقه وإلغاء تثبيته.

> [!NOTE]
> *في اختبار OOB، يلزم تثبيت البرامج النصية وتشغيلها وإغلاقها، بينما يكون إلغاء تثبيت البرنامج النصي اختياريا*.

يجب إضافة البرنامج النصي إلى المجلد كما يلي:

![موقع ملفات البرامج النصية powershell في المجلد](Media/buildpackage3.png)

يتضمن البرنامج النصي عادة السلوكيات التالية:

- **قم بتشغيل الأوامر لتثبيت/تشغيل/إغلاق/إلغاء تثبيت التطبيق**. على سبيل المثال، إذا كان التطبيق الخاص بك هو ملف MSI، فشغل [msiexec](/windows-server/administration/windows-commands/msiexec) لتثبيته.
- **تحقق من نتيجة عملية التثبيت/التشغيل/الإغلاق/إلغاء التثبيت**، وارجع صفر رمز الخروج إذا كانت النتيجة متوقعة. ستميز قاعدة الاختبار تشغيل البرنامج النصي كفشل إذا كانت ترجع رمز خروج غير صفري.
- **احفظ ما يكفي من السجلات**، واحفظ السجلات المناسبة لاستخدامها في المستقبل.

الرجاء الرجوع إلى الأمثلة التالية. يمكنك ببساطة نسخها إلى ملفاتك وإجراء التغييرات وفقا لذلك.

**مثال على تثبيت البرنامج النصي (App\scripts\install\job.ps1):**

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

**مثال على تشغيل البرنامج النصي (App\scripts\launch\job.ps1)**:

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

## <a name="compress-to-zip-file"></a>ضغط إلى ملف مضغوط

بعد إعداد البرامج النصية والثنائيات، يمكنك المتابعة لضغط المجلد إلى ملف مضغوط. انقر بزر الماوس الأيمن فوق مجلد "التطبيق"، وحدد **"ضغط إلى ملف ZIP**".

![ضغط إلى ملف مضغوط](Media/buildpackage4.png)

## <a name="verify-your-package-locally-optional"></a>التحقق من الحزمة محليا (اختياري)

بعد إنشاء الحزمة المضغوطة، يمكنك تحميلها إلى حساب قاعدة الاختبار.

ومع ذلك، من أفضل الممارسات تشغيل الاختبار محليا لضمان عمل البرامج النصية بشكل صحيح قبل التحميل. يمكن للاختبار المحلي تحديد المشكلات بسرعة وتسريع عملية التحميل. للتحقق محليا اتبع الخطوات أدناه:

1. إعداد جهاز ظاهري (جهاز ظاهري)

   نوصي باستخدام جهاز ظاهري لهذا الاختبار المحلي نظرا لحاجة بيئة Windows نظيفة حاليا لكل اختبار. من السهل إنشاء جهاز ظاهري Windows على Azure ([التشغيل السريع: Windows الجهاز الظاهري](/azure/virtual-machines/windows/quick-create-portal))، يمكنك تحديد إصدار Windows مناسب (صورة) للاختبار الخاص بك، على سبيل المثال، *Windows 10 Pro، الإصدار 21H2.*<br>

2. نسخ الحزمة إلى الجهاز الظاهري

   هناك العديد من الطرق لنسخ ملف الحزمة إلى الجهاز الظاهري. إذا كنت تستخدم جهازا ظاهريا من Azure، يمكنك اختيار:

     - انسخ الملف مباشرة في اتصال سطح المكتب البعيد.
     - استخدام مشاركة ملف Azure ([التشغيل السريع: إنشاء ملف Azure وإدارته](/azure/storage/files/storage-files-quick-create-use-windows))

   يمكنك إنشاء مجلد معين لهذا الاختبار ونسخ ملف الحزمة ضمن هذا المجلد. على سبيل المثال، *C:\TestBase*.

3. اختبار الحزمة

   افتح Windows PowerShell، وقم بالتبديل إلى الدليل الذي يحتوي على الحزمة، على سبيل المثال، `cd C:\TestBase`وابدأ في تشغيل الاختبارات على الحزمة:

   1. استخراج ملف الحزمة.

      ```powershell
      Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase
      ```

   2. تشغيل البرنامج النصي للتثبيت.

      ```powershell
      C:\TestBase\App\scripts\install\job.ps1
      ```

   3. أعد تشغيل الجهاز الظاهري إذا لزم الأمر.

   4. تشغيل البرنامج النصي لبدء التشغيل.

      ```powershell
      C:\TestBase\App\scripts\install\job.ps1
      ```

   5. تشغيل البرنامج النصي إغلاق.

      ```powershell
      C:\TestBase\App\scripts\close\job.ps1
      ```

   6. تشغيل البرنامج النصي لإلغاء التثبيت (إذا كان لديك برنامج نصي).

      ```powershell
      C:\TestBase\App\scripts\uninstall\job.ps1
      ```

بعد كل خطوة، يمكنك التحقق مما إذا كانت هناك أي مشكلات في البرنامج النصي الخاص بك. إذا كانت جميع البرامج النصية تعمل كما هو متوقع، فإن حزمتك جاهزة لتحميلها إلى حساب قاعدة الاختبار.

## <a name="next-steps"></a>الخطوات التالية

[Upload حزمة](uploadApplication.md)
