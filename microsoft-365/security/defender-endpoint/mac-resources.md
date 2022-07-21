---
title: موارد Microsoft Defender لنقطة النهاية على Mac
description: موارد Microsoft Defender لنقطة النهاية على Mac، بما في ذلك كيفية إلغاء تثبيته، وكيفية جمع سجلات التشخيص، وأوامر CLI، والمشاكل المعروفة في المنتج.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، التوزيع، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d7f01e3336fef9382ae6556180deaf14155b6d44
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66943607"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>موارد Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>تجميع المعلومات التشخيصية

إذا كان بإمكانك إعادة إنشاء مشكلة، فزيد مستوى التسجيل، وقم بتشغيل النظام لبعض الوقت، واستعادة مستوى التسجيل إلى المستوى الافتراضي.

1. زيادة مستوى التسجيل:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. إعادة إنتاج المشكلة

3. قم بتشغيل `sudo mdatp diagnostic create` النسخ الاحتياطي لسجلات Microsoft Defender لنقطة النهاية. سيتم تخزين الملفات داخل أرشيف .zip. سيقوم هذا الأمر أيضا بطباعة مسار الملف إلى النسخة الاحتياطية بعد نجاح العملية.

   > [!TIP]
   > بشكل افتراضي، يتم حفظ سجلات التشخيص إلى `/Library/Application Support/Microsoft/Defender/wdavdiag/`. لتغيير الدليل حيث يتم حفظ سجلات التشخيص، قم بالتمرير `--path [directory]` إلى الأمر أدناه، واستبداله `[directory]` بالدليل المطلوب.

   ```bash
   sudo mdatp diagnostic create
   ```

   ```console
   Diagnostic file created: "/Library/Application Support/Microsoft/Defender/wdavdiag/932e68a8-8f2e-4ad0-a7f2-65eb97c0de01.zip"
   ```

4. استعادة مستوى التسجيل:

   ```bash
   mdatp log level set --level info
   ```

   ```console
   Log level configured successfully
   ```

## <a name="logging-installation-issues"></a>مشاكل تثبيت التسجيل

إذا حدث خطأ أثناء التثبيت، فسيبلغ المثبت عن فشل عام فقط.

سيتم حفظ السجل التفصيلي في `/Library/Logs/Microsoft/mdatp/install.log`. إذا واجهت مشاكل أثناء التثبيت، فأرسل لنا هذا الملف حتى نتمكن من المساعدة في تشخيص السبب.

## <a name="uninstalling"></a>الغاء تثبيت

هناك عدة طرق لإلغاء تثبيت Microsoft Defender لنقطة النهاية على macOS. لاحظ أنه على الرغم من توفر إلغاء التثبيت المدار مركزيا على JAMF، إلا أنه غير متوفر حتى الآن Microsoft Intune.

### <a name="interactive-uninstallation"></a>إزالة تثبيت تفاعلي

- افتح **تطبيقات > الباحث**. انقر بزر الماوس الأيمن فوق **Microsoft Defender لنقطة النهاية > نقل إلى سلة المهملات**.

### <a name="supported-output-types"></a>أنواع الإخراج المعتمدة

يدعم أنواع إخراج تنسيقات الجدول وJSON. لكل أمر، هناك سلوك إخراج افتراضي. يمكنك تعديل الإخراج بتنسيق الإخراج المفضل لديك باستخدام الأوامر التالية:

`-output json`

`-output table`

### <a name="from-the-command-line"></a>من سطر الأوامر

- `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`

## <a name="configuring-from-the-command-line"></a>التكوين من سطر الأوامر

يمكن تنفيذ المهام الهامة، مثل التحكم في إعدادات المنتج وتشغيل عمليات الفحص عند الطلب، من سطر الأوامر:

|مجموعة|السيناريو|الامر|
|---|---|---|
|التكوين|تشغيل/إيقاف تشغيل الحماية في الوقت الحقيقي|`mdatp config real-time-protection --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل حماية السحابة|`mdatp config cloud --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل تشخيصات المنتجات|`mdatp config cloud-diagnostic --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل الإرسال التلقائي للعينة|`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`|
|التكوين|إضافة اسم تهديد إلى القائمة المسموح بها|`mdatp threat allowed add --name [threat-name]`|
|التكوين|إزالة اسم تهديد من القائمة المسموح بها|`mdatp threat allowed remove --name [threat-name]`|
|التكوين|سرد كافة أسماء التهديدات المسموح بها|`mdatp threat allowed list`|
|التكوين|تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application -- action block`|
|التكوين|إيقاف تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application -- action off`|
|التكوين|تشغيل وضع التدقيق لحماية PUA|`mdatp threat policy set --type potentially_unwanted_application -- action audit`|
|التكوين|تشغيل/إيقاف تشغيل الوضع السلبي لمكافحة الفيروسات|`mdatp config passive-mode --value [enabled/disabled]`|
|التكوين|تكوين درجة التوازي لإجراء عمليات الفحص عند الطلب|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|التكوين|تشغيل/إيقاف تشغيل عمليات الفحص بعد تحديثات معلومات الأمان|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل فحص الأرشيف (عمليات المسح حسب الطلب فقط)|`mdatp config scan-archives --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل حساب تجزئة الملف|`mdatp config enable-file-hash-computation --value [enabled/disabled]`|
|تشخيص|تغيير مستوى السجل|`mdatp log level set --level [error/warning/info/verbose]`|
|تشخيص|إنشاء سجلات تشخيصية|`mdatp diagnostic create --path [directory]`|
|الحماية|التحقق من صحة المنتج|`mdatp health`|
|الحماية|التحقق من سمة منتج spefic|`mdatp health --field [attribute: healthy/licensed/engine_version...]`|
|حمايه|مسح مسار ضوئيا|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|حمايه|إجراء فحص سريع|`mdatp scan quick`|
|حمايه|إجراء فحص كامل|`mdatp scan full`|
|حمايه|إلغاء فحص مستمر عند الطلب|`mdatp scan cancel`|
|حمايه|طلب تحديث معلومات الأمان|`mdatp definitions update`|
|يدر|تعيين/إزالة العلامة، المجموعة المعتمدة فقط|`mdatp edr tag set --name GROUP --value [name]`|
|يدر|إزالة علامة المجموعة من الجهاز|`mdatp edr tag remove --tag-name [name]`|
|يدر|إضافة معرف المجموعة|`mdatp edr group-ids --group-id [group]`|

### <a name="how-to-enable-autocompletion"></a>كيفية تمكين الإكمال التلقائي

لتمكين الإكمال التلقائي في bash، قم بتشغيل الأمر التالي وأعد تشغيل جلسة عمل Terminal:

```bash
echo "source /Applications/Microsoft\ Defender.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

لتمكين الإكمال التلقائي في zsh:

- تحقق مما إذا كان الإكمال التلقائي ممكنا على جهازك:

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- إذا لم ينتج عن الأمر السابق أي إخراج، يمكنك تمكين الإكمال التلقائي باستخدام الأمر التالي:

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- تشغيل الأوامر التالية لتمكين الإكمال التلقائي Microsoft Defender لنقطة النهاية على macOS وإعادة تشغيل جلسة عمل المحطة الطرفية:

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions

   sudo ln -svf "/Applications/Microsoft Defender.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>دليل عزل Microsoft Defender لنقطة النهاية العميل

`/Library/Application Support/Microsoft/Defender/quarantine/` يحتوي على الملفات التي تم عزلها بواسطة `mdatp`. تتم تسمية الملفات بعد معرف تتبع المخاطر. تظهر معرفات التعقب الحالية مع `mdatp threat list`.

## <a name="microsoft-defender-for-endpoint-portal-information"></a>معلومات مدخل Microsoft Defender لنقطة النهاية

[لقد وصلت الآن إمكانات EDR لنظام التشغيل macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801)، في مدونة Microsoft Defender لنقطة النهاية، وتوفر إرشادات مفصلة حول ما يجب توقعه في مركز الأمان Microsoft Defender لنقطة النهاية.
