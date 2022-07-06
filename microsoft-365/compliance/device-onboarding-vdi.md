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
description: نشر حزمة التكوين على جهاز البنية الأساسية لسطح المكتب الظاهري (VDI) بحيث يتم إلحاقها بخدمة منع فقدان بيانات نقطة النهاية.
ms.openlocfilehash: 8a54d4ce3cfb4b3ba6571f2aee63cd60c2a6d71f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636128"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>إلحاق أجهزة البنية الأساسية لسطح المكتب الظاهري غير الثابتة

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

- أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI)

> [!WARNING]
> يدعم دعم منع فقدان بيانات نقطة النهاية ل Windows Virtual Desktop سيناريوهات جلسة عمل واحدة. سيناريوهات جلسات متعددة على Windows Virtual Desktop غير معتمدة حاليا.

## <a name="onboard-vdi-devices"></a>إلحاق أجهزة VDI

يدعم Microsoft 365 إعداد جلسة عمل البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة.

> [!NOTE]
> لإلحاق جلسات VDI غير الثابتة، يجب أن تكون أجهزة VDI في Windows 10 1809 أو أعلى.

قد تكون هناك تحديات مرتبطة عند إلحاق VDIs. فيما يلي تحديات نموذجية لهذا السيناريو:

- الإلحاق المبكر الفوري بجلسات قصيرة الأمد، والتي يجب إلحاقها ب Microsoft 365 قبل التوفير الفعلي.
- عادة ما يعاد استخدام اسم الجهاز لجلسات عمل جديدة.

يمكن أن تظهر أجهزة VDI في مدخل التوافق في Microsoft Purview كما يلي:

- إدخال واحد لكل جهاز.
لاحظ أنه في هذه الحالة، يجب تكوين *نفس* اسم الجهاز عند إنشاء جلسة العمل، على سبيل المثال باستخدام ملف إجابات غير المراقب.
- إدخالات متعددة لكل جهاز - واحد لكل جلسة عمل.

ستوجهك الخطوات التالية خلال إلحاق أجهزة VDI وستسلط الضوء على خطوات الإدخالات الفردية والمضاعفة.

> [!WARNING]
> بالنسبة للبيئات التي توجد فيها تكوينات موارد منخفضة، قد يؤدي إجراء تمهيد VDI إلى إبطاء عملية إلحاق الجهاز.

1. احصل على ملف .zip حزمة تكوين VDI (*DeviceCompliancePackage.zip*) من [مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com).

2. في جزء التنقل، حدد **"إعدادات** >  الجهاز" في **الإلحاق** > .

3. في حقل **أسلوب النشر** ، حدد **البرامج النصية لإلحاق VDI لنقاط النهاية غير الثابتة**.

4. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.

5. انسخ الملفات من مجلد DeviceCompliancePackage المستخرج من ملف .zip إلى `golden` الصورة أسفل المسار `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. إذا كنت لا تنفذ إدخالا واحدا لكل جهاز، فنسسخ DeviceComplianceOnboardingScript.cmd.

7. إذا كنت تقوم بتنفيذ إدخال واحد لكل جهاز، فانسخ كل من Onboard-NonPersistentMachine.ps1 وDeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > إذا لم تتمكن من `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` رؤية المجلد، فقد يكون مخفيا. ستحتاج إلى اختيار الخيار **"إظهار الملفات والمجلدات المخفية**" من مستكشف الملفات.

8. افتح نافذة محرر نهج المجموعة المحلي وانتقل إلى **بدء تشغيل** **البرامج النصية** > **لإعدادات** >  Windows **لتكوين** >  الكمبيوتر.

   > [!NOTE]
   > يمكن أيضا استخدام نهج المجموعة المجال لإلحاق أجهزة VDI غير الثابتة.

9. استنادا إلى الأسلوب الذي تريد تنفيذه، اتبع الخطوات المناسبة:

   **لإدخال واحد لكل جهاز**

   حدد علامة التبويب **PowerShell Scripts** ، ثم انقر فوق **"إضافة** " (سيتم فتح مستكشف Windows مباشرة في المسار حيث قمت بنسخ البرنامج النصي للإلحاق سابقا). انتقل إلى إعداد البرنامج النصي `Onboard-NonPersistentMachine.ps1`PowerShell.

   **للإدخالات المتعددة لكل جهاز**:

   حدد علامة التبويب **"البرامج النصية** "، ثم انقر فوق **"إضافة** " (سيتم فتح مستكشف Windows مباشرة في المسار حيث قمت بنسخ البرنامج النصي للإلحاق سابقا). انتقل إلى البرنامج النصي `DeviceComplianceOnboardingScript.cmd`bash الإلحاق.

10. اختبار الحل الخاص بك:
    1. إنشاء تجمع مع جهاز واحد.
    1. تسجيل الدخول إلى الجهاز.
    1. تسجيل الخروج من الجهاز.
    1. تسجيل الدخول إلى الجهاز مع مستخدم آخر.
    1. **لإدخال واحد لكل جهاز**: تحقق من إدخال واحد فقط في مركز حماية Microsoft Defender.
       **للحصول على إدخالات متعددة لكل جهاز**: تحقق من إدخالات متعددة في مركز حماية Microsoft Defender.

11. انقر فوق **قائمة الأجهزة** في جزء التنقل.

12. استخدم دالة البحث عن طريق إدخال اسم الجهاز وحدد **الجهاز** كنوع بحث.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>تحديث صور البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة

كأفضل ممارسة، نوصي باستخدام أدوات الخدمة دون اتصال لتصحيح الصور الذهبية.

على سبيل المثال، يمكنك استخدام الأوامر أدناه لتثبيت تحديث بينما تظل الصورة غير متصلة:

```DOS
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

لمزيد من المعلومات حول أوامر DISM والخدمة دون اتصال، يرجى الرجوع إلى المقالات أدناه:

- [تعديل صورة Windows باستخدام DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [خيارات Command-Line إدارة صور DISM](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [تصغير حجم مخزن المكونات في صورة Windows غير متصلة](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

إذا لم تكن الخدمة دون اتصال خيارا قابلا للتطبيق لبيئة VDI غير الثابتة، يجب اتخاذ الخطوات التالية لضمان التناسق وحماية جهاز الاستشعار:

1. بعد تشغيل الصورة الذهبية لخدمة عبر الإنترنت أو تصحيحها، قم بتشغيل برنامج نصي لإيقاف تشغيل مستشعر مراقبة جهاز Microsoft 365. لمزيد من المعلومات، راجع [أجهزة Offboard باستخدام برنامج نصي محلي](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. تأكد من إيقاف جهاز الاستشعار عن طريق تشغيل الأمر أدناه في نافذة CMD:

   ```DOS
   sc query sense
   ```

3. خدمة الصورة حسب الحاجة.

4. قم بتشغيل الأوامر أدناه باستخدام PsExec.exe (التي يمكن تنزيلها من https://download.sysinternals.com/files/PSTools.zip) أجل تنظيف محتويات المجلد الإلكتروني التي قد يكون جهاز الاستشعار قد تراكم منذ التشغيل:

    ```DOS
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. أعد إغلاق الصورة الذهبية كما تفعل عادة.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام نهج المجموعة](device-onboarding-gp.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager نقطة نهاية Microsoft](device-onboarding-sccm.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام أدوات إدارة الأجهزة المحمولة](device-onboarding-mdm.md)
- [إلحاق أجهزة Windows 10 وأجهزة Windows 11 باستخدام برنامج نصي محلي](device-onboarding-script.md)
- [استكشاف أخطاء الحماية المتقدمة من التهديدات في Microsoft Defender وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
