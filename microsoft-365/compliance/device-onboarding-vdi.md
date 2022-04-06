---
title: أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: نشر حزمة التكوين على جهاز البنية الأساسية لسطح المكتب الظاهري (VDI) بحيث يتم Microsoft 365 خدمة منع فقدان البيانات في نقطة النهاية.
ms.openlocfilehash: 00804c93022f21715e3604eeb45c22caa4745f91
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682141"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>أجهزة البنية الأساسية لسطح المكتب الظاهري غير الثابتة

**ينطبق على:**

- [Microsoft 365 فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

- أجهزة البنية الأساسية لسطح المكتب الظاهرية (VDI)

> [!WARNING]
> Microsoft 365 دعم منع فقدان بيانات نقطة النهاية Windows الظاهري لسطح المكتب الافتراضي على سيناريوهات جلسة عمل واحدة. سيناريوهات جلسات العمل المتعددة Windows سطح المكتب الظاهري غير معتمدة حاليا.

## <a name="onboard-vdi-devices"></a>أجهزة VDI المجهزة

Microsoft 365 تشغيل جلسة عمل البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة.

> [!NOTE]
> لتكديس جلسات VDI غير الثابتة، يجب أن تكون أجهزة VDI على Windows 10 1809 أو أعلى.

قد تكون هناك تحديات مقترنة عند تكديس VDIs. فيما يلي تحديات نموذجية لهذا السيناريو:

- التكهين المبكر الفوري لجلسات العمل القصيرة، والتي يجب أن يتم Microsoft 365 قبل توفيرها الفعلي.
- تتم إعادة استخدام اسم الجهاز عادة لجلسات العمل الجديدة.

يمكن أن تظهر أجهزة VDI في Microsoft 365 التوافق كما يلي:

- إدخال واحد لكل جهاز.
تجدر الإشارة إلى أنه في هذه الحالة، يجب تكوين اسم الجهاز نفسه عند إنشاء جلسة العمل، على سبيل المثال باستخدام ملف إجابة غير ملاحظ.
- إدخالات متعددة لكل جهاز - إدخال لكل جلسة عمل.

سترشدك الخطوات التالية عبر أجهزة VDI التي تقوم ب التكديس، كما ستسلط الضوء على خطوات الإدخالات الفردية والمتعددة.

> [!WARNING]
> بالنسبة إلى البيئات التي تكون فيها تكوينات الموارد منخفضة، قد يبطئ إجراء تشغيل VDI عملية إعداد الجهاز.

1. احصل على حزمة تكوين VDI .zip ملف (*DeviceCompliancePackage.zip*) من [مركز التوافق من Microsoft](https://compliance.microsoft.com).

2. في جزء التنقل **، حدد الإعدادات** >  **التأليف onboardingOnboarding** > .

3. في الحقل **أسلوب النشر** ، حدد **برامج VDI النصية لتكديس** نقاط النهاية غير الثابتة.

4. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

5. انسخ الملفات من مجلد DeviceCompliancePackage الذي تم استخراجه من ملف .zip إلى `golden` الصورة ضمن المسار `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. إذا كنت لا تنفذ إدخالا واحدا لكل جهاز، انسخ DeviceComplianceOnboardingScript.cmd.

7. إذا كنت تقوم بتنفيذ إدخال واحد لكل جهاز، انسخ كل من Onboard-NonPersistentMachine.ps1 و DeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > إذا لم تشاهد المجلد، `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` فقد يكون مخفيا. ستحتاج إلى اختيار الخيار **إظهار الملفات والمجلدات** المخفية من مستكشف الملفات.

8. افتح نافذة محرر نهج المجموعة المحلية وانتقل إلى **تكوين** >  **الكمبيوتر** >  Windows الإعدادات **ScriptsStartup** > .

   > [!NOTE]
   > يمكن أيضا استخدام نهج مجموعة المجالات لتكديس أجهزة VDI غير الثابتة.

9. استنادا إلى الأسلوب الذي تريد تنفيذه، اتبع الخطوات المناسبة:

   **إدخال واحد لكل جهاز**

   حدد علامة **التبويب البرامج النصية في PowerShell**، ثم انقر فوق **إضافة (Windows** سيفتح المستكشف مباشرة في المسار حيث نسخت البرنامج النصي لالإضافة سابقا). انتقل إلى البرنامج النصي ل PowerShell الذي تم إعادة ا `Onboard-NonPersistentMachine.ps1`متنه.

   **بالنسبة إلى إدخالات متعددة لكل جهاز**:

   حدد علامة **التبويب** البرامج النصية، ثم **انقر فوق إضافة** (Windows سيفتح المستكشف مباشرة في المسار الذي نسخت فيه البرنامج النصي لالإضافة سابقا). انتقل إلى البرنامج النصي ل bash الخاص باللوح `DeviceComplianceOnboardingScript.cmd`.

10. اختبر الحل الخاص بك:
    1. إنشاء تجمع باستخدام جهاز واحد.
    1. سجل دخولك إلى الجهاز.
    1. سجل خروجك من الجهاز.
    1. سجل دخولك إلى جهاز مع مستخدم آخر.
    1. **للحصول على إدخال واحد لكل جهاز**: تحقق من إدخال واحد فقط في مركز حماية Microsoft Defender.
       **للحصول على إدخالات متعددة لكل جهاز**: تحقق من إدخالات متعددة في مركز حماية Microsoft Defender.

11. انقر **فوق قائمة الأجهزة** في جزء التنقل.

12. استخدم وظيفة البحث بإدخال اسم الجهاز وحدد **الجهاز** كنوع بحث.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>تحديث صور البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة

من أفضل الممارسات، نوصي باستخدام أدوات توفير الخدمة دون اتصال لتصحيح الصور الذهبية.

على سبيل المثال، يمكنك استخدام الأوامر أدناه لتثبيت تحديث بينما تظل الصورة دون اتصال:

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

لمزيد من المعلومات حول أوامر DISM والخدمة دون اتصال، الرجاء الرجوع إلى المقالات أدناه:

- [تعديل صورة Windows باستخدام DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [خيارات إدارة الصور Command-Line DISM](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [تصغر حجم 'متجر المكونات' في صورة غير متصلة Windows](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

إذا لم تكن الخدمة دون اتصال خيارا قابلا للتطبيق لبيئة VDI غير الثابتة، يجب اتخاذ الخطوات التالية لضمان التناسق وصحة المستشعر:

1. بعد تشغيل الصورة الذهبية لخدمتها أو تصحيحها عبر الإنترنت، قم بتشغيل برنامج نصي خارج التشغيل Microsoft 365 مستشعر مراقبة الجهاز. لمزيد من المعلومات، راجع [أجهزة Offboard باستخدام برنامج نصي محلي](device-onboarding-script.md#offboard-devices-using-a-local-script).

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
    REG DELETE “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. إعادة ختم الصورة الذهبية كما لو كنت تقوم بذلك عادة.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [أجهزة Windows 10 Windows 11 باستخدام "نهج المجموعة"](device-onboarding-gp.md)
- [أجهزة Windows 10 وأجهزة Windows 11 باستخدام Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [أجهزة Windows 10 Windows 11 الأجهزة باستخدام أدوات إدارة أجهزة المحمول](device-onboarding-mdm.md)
- [أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [استكشاف مشاكل توفير الحماية المتقدمة من المخاطر ل Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
