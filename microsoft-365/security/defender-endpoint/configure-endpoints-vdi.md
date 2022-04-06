---
title: أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة
description: نشر حزمة التكوين على جهاز البنية الأساسية لسطح المكتب الظاهري (VDI) بحيث يتم تشغيلها في خدمة Microsoft Defender for Endpoint.
keywords: تكوين جهاز البنية الأساسية لسطح المكتب الظاهري (VDI)، vdi، إدارة الأجهزة، تكوين Microsoft Defender لنقطة النهاية، نقاط النهاية
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 02/14/2022
ms.technology: mde
ms.openlocfilehash: 7342f368063c2c9024c4942c33a2e41f28eebd36
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63583181"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- أجهزة البنية الأساسية لسطح المكتب الظاهرية (VDI)
- Windows 10، Windows 11، Windows Server 2019، Windows Server 2022، Windows Server 2008R2/2012R2/2016

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **VDI الثابتة** -  [يتم التعامل مع](configure-endpoints.md) تشغيل تشغيل جهاز VDI ثابت في Microsoft Defender لنقطة النهاية بالطريقة نفسها التي يتم بها تشغيل جهاز فعلي، مثل كمبيوتر سطح المكتب أو الكمبيوتر المحمول. يمكن استخدام نهج إدارة نقاط النهاية من Microsoft والأساليب الأخرى ل متن جهاز ثابت. في Microsoft 365 Defender، (https://security.microsoft.com)ضمن التكهين، حدد أسلوب التكهين المفضل لديك، واتبع الإرشادات الخاصة بهذا النوع. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>تشغيل أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة

يدعم Defender ل Endpoint التكديس غير الدائم لجلسة VDI.

قد تكون هناك تحديات مقترنة عند تكديس VDIs. فيما يلي تحديات نموذجية لهذا السيناريو:

- التكوين المبكر لجلسة قصيرة، يجب أن يتم ا متنها إلى Defender لنقطة النهاية قبل توفيرها الفعلي.
- تتم إعادة استخدام اسم الجهاز عادة لجلسات العمل الجديدة.

يمكن أن تظهر أجهزة VDI في مدخل Defender for Endpoint كما يلي:

- إدخال واحد لكل جهاز.

  > [!NOTE]
  > في هذه الحالة *، يجب تكوين* اسم الجهاز نفسه عند إنشاء جلسة العمل، على سبيل المثال باستخدام ملف إجابة غير معتين.

- إدخالات متعددة لكل جهاز - إدخال لكل جلسة عمل.

سترشدك الخطوات التالية عبر أجهزة VDI التي تقوم ب التكديس، كما ستسلط الضوء على خطوات الإدخالات الفردية والمتعددة.

> [!WARNING]
> بالنسبة إلى البيئات التي تكون فيها تكوينات الموارد منخفضة، قد يبطئ إجراء تشغيل VDI تشغيل مستشعر Defender لنقطة النهاية.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>بالنسبة Windows 10 أو Windows 11 أو Windows Server 2012 R2 واللاحقة

> [!NOTE]
> Windows يجب إعداد Windows Server 2012 R2 من خلال تطبيق حزمة التثبيت أولا باستخدام الإرشادات الموجودة في خوادم [Onboard Windows](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) لكي تعمل هذه الميزة.

1.  افتح حزمة تكوين VDI .zip ملف (*WindowsDefenderATPOnboardingPackage.zip*) الذي قمت بتنزيلها من معالج إعداد الخدمة. يمكنك أيضا الحصول على الحزمة من مدخل Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">:</a>

    1. في جزء التنقل **، حدد الإعدادات** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. حدد نظام التشغيل.

    1.  في الحقل **أسلوب النشر** ، حدد **برامج VDI النصية لتكديس** نقاط النهاية غير الثابتة.

    1. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

2. انسخ الملفات من مجلد WindowsDefenderATPOnboardingPackage المستخرج من ملف .zip إلى الصورة الذهبية/الرئيسية أسفل المسار `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. إذا كنت تقوم بتنفيذ إدخالات متعددة لكل جهاز - واحد لكل جلسة عمل، انسخ WindowsDefenderATPOnboardingScript.cmd.
    2. إذا كنت تقوم بتنفيذ إدخال واحد لكل جهاز، انسخ كل من Onboard-NonPersistentMachine.ps1 و WindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > إذا لم تشاهد المجلد، `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` فقد يكون مخفيا. ستحتاج إلى اختيار الخيار **إظهار الملفات والمجلدات** المخفية من مستكشف الملفات.

3. افتح نافذة محرر نهج المجموعة المحلية وانتقل إلى **تكوين** \>  \> الكمبيوتر Windows الإعدادات **بدء تشغيل** \> **البرامج النصية**.

   > [!NOTE]
   > يمكن أيضا استخدام نهج مجموعة المجالات لتكديس أجهزة VDI غير الثابتة.

4. استنادا إلى الأسلوب الذي تريد تنفيذه، اتبع الخطوات المناسبة:
    - للحصول على إدخال واحد لكل جهاز:

         حدد علامة **التبويب البرامج النصية في PowerShell**، ثم انقر فوق **إضافة (Windows** سيفتح المستكشف مباشرة في المسار حيث نسخت البرنامج النصي لالإضافة سابقا). انتقل إلى البرنامج النصي ل PowerShell الذي تم إعادة ا `Onboard-NonPersistentMachine.ps1`متنه. لا حاجة إلى تحديد الملف الآخر، حيث سيتم تشغيله تلقائيا.

    - بالنسبة إلى إدخالات متعددة لكل جهاز:

         حدد علامة **التبويب** البرامج النصية، ثم **انقر فوق إضافة** (Windows سيفتح المستكشف مباشرة في المسار الذي نسخت فيه البرنامج النصي لالإضافة سابقا). انتقل إلى البرنامج النصي ل bash الخاص باللوح `WindowsDefenderATPOnboardingScript.cmd`.

5. اختبر الحل الخاص بك:
   1. إنشاء تجمع باستخدام جهاز واحد.
   2. سجل دخولك إلى الجهاز.
   3. سجل خروجك من الجهاز.
   4. سجل دخولك إلى جهاز مع مستخدم آخر.
   5. استنادا إلى الأسلوب الذي تريد تنفيذه، اتبع الخطوات المناسبة:
      - للحصول على إدخال واحد لكل جهاز: تحقق من إدخال واحد فقط Microsoft 365 Defender المدخل.
      - للحصول على إدخالات متعددة لكل جهاز: تحقق من إدخالات متعددة Microsoft 365 Defender المدخل.

6. انقر **فوق قائمة الأجهزة** في جزء التنقل.

7. استخدم وظيفة البحث بإدخال اسم الجهاز وحدد **الجهاز** كنوع بحث.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>بالنسبة إلى SKUs على المستوى Windows Server 2008 R2)

> [!NOTE]
> تنطبق هذه الإرشادات لإصدارات خوادم Windows الأخرى أيضا إذا كنت تقوم بتشغيل Microsoft Defender السابق لنقطة النهاية ل Windows Server 2016 و Windows Server 2012 R2 الذي يتطلب MMA. توجد إرشادات الترحيل إلى الحل الموحد الجديد في سيناريوهات [ترحيل الخادم في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> يكون السجل التالي ذا صلة فقط عندما يكون الهدف هو تحقيق 'إدخال واحد لكل جهاز'.

1. تعيين قيمة السجل إلى:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    أو استخدام سطر الأوامر:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. اتبع عملية [التكهين للخادم](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>تحديث صور البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة

من أفضل الممارسات، نوصي باستخدام أدوات توفير الخدمة دون اتصال للصق الصور الذهبية/الرئيسية.

على سبيل المثال، يمكنك استخدام الأوامر أدناه لتثبيت تحديث بينما تظل الصورة دون اتصال:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

لمزيد من المعلومات حول أوامر DISM والخدمة دون اتصال، راجع المقالات أدناه:

- [تعديل صورة Windows باستخدام DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [خيارات إدارة الصور Command-Line DISM](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [تصغر حجم 'متجر المكونات' في صورة غير متصلة Windows](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

إذا لم تكن الخدمة دون اتصال خيارا قابلا للتطبيق لبيئة VDI غير الثابتة، يجب اتخاذ الخطوات التالية لضمان التناسق وصحة المستشعر:

1. بعد تشغيل الصورة الرئيسية لخدمتها أو تصحيحها عبر الإنترنت، قم بتشغيل برنامج نصي خارج التشغيل لتشغيل مستشعر Defender for Endpoint. لمزيد من المعلومات، راجع [أجهزة Offboard باستخدام برنامج نصي محلي](configure-endpoints-script.md#offboard-devices-using-a-local-script).

2. تأكد من إيقاف المستشعر عن طريق تشغيل الأمر أدناه في نافذة CMD:

   ```console
   sc query sense
   ```

3. خدمة الصورة حسب الحاجة.

4. شغل الأوامر أدناه باستخدام PsExec.exe ( https://download.sysinternals.com/files/PSTools.zip) التي يمكن تنزيلها من لتنظيف محتويات مجلد الإنترنت التي قد تكون المستشعر قد تراكمت منذ التشغيل:

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. يمكنك إعادة ازاله الصورة الذهبية/الرئيسية كما تريد عادة.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows باستخدام "نهج المجموعة"](configure-endpoints-gp.md)
- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows الأجهزة باستخدام أدوات إدارة أجهزة المحمول](configure-endpoints-mdm.md)
- [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](troubleshoot-onboarding.md)
