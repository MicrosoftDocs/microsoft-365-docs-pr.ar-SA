---
title: موارد ل Microsoft Defender لنقطة النهاية على Mac
description: موارد ل Microsoft Defender ل Endpoint على Mac، بما في ذلك كيفية إلغاء تثبيته، وكيفية تجميع سجلات التشخيص، وأوامر CLI، وا المشاكل المعروفة في المنتج.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: 5c8580e1bc0869f28da1b23a813bba9d2f3c612e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570665"
---
# <a name="resources-for-microsoft-defender-for-endpoint-on-macos"></a>موارد ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="collecting-diagnostic-information"></a>تجميع المعلومات التشخيصية

إذا كان بإمكانك إعادة إنتاج مشكلة، فالزيادة في مستوى التسجيل وتشغيل النظام لبعض الوقت واستعادة مستوى التسجيل إلى الإعداد الافتراضي.

1. زيادة مستوى التسجيل:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. إعادة إنتاج المشكلة

3. قم `sudo mdatp diagnostic create` بتشغيل للحصول على دعم لسجلات نقطة النهاية ل Microsoft Defender. سيتم تخزين الملفات داخل أرشيف .zip. سيطبع هذا الأمر أيضا مسار الملف إلى النسخة الاحتياطية بعد نجاح العملية.

   > [!TIP]
   > بشكل افتراضي، يتم حفظ سجلات التشخيص في `/Library/Application Support/Microsoft/Defender/wdavdiag/`. لتغيير الدليل حيث يتم حفظ السجلات التشخيصية `--path [directory]` ، مرر إلى الأمر أدناه `[directory]` ، مع استبدال الدليل المطلوب.

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

إذا حدث خطأ أثناء التثبيت، سيقر المثبت بفشل عام فقط.

سيتم حفظ السجل التفصيلي في `/Library/Logs/Microsoft/mdatp/install.log`. إذا واجهت مشاكل أثناء التثبيت، أرسل لنا هذا الملف حتى يمكننا مساعدتك في تشخيص السبب.

## <a name="uninstalling"></a>إلغاء تثبيت

هناك عدة طرق  إلغاء تثبيت Microsoft Defender ل Endpoint على macOS. لاحظ أنه على الرغم من توفر إلغاء التثبيت المدار مركزيا على JAMF، إلا أنه غير متوفر Microsoft Intune.

### <a name="interactive-uninstallation"></a>إزالة التثبيت التفاعلي

- افتح **"البحث" > التطبيقات**. انقر بيمين فوق **Microsoft Defender لنقطة النهاية > الانتقال إلى سلة المهملات**.

### <a name="supported-output-types"></a>أنواع الإخراج المعتمدة

يدعم الجدول وأنواع إخراجات تنسيق JSON. لكل أمر، يوجد سلوك إخراج افتراضي. يمكنك تعديل الإخراج بتنسيق الإخراج المفضل لديك باستخدام الأوامر التالية:

`-output json`

`-output table`

### <a name="from-the-command-line"></a>من سطر الأوامر

- `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`

## <a name="configuring-from-the-command-line"></a>تكوين من سطر الأوامر

يمكن تنفيذ المهام المهمة، مثل التحكم في إعدادات المنتج وتحريك عمليات الفحص عند الطلب، من سطر الأوامر:

|مجموعة|السيناريو|الأمر|
|---|---|---|
|تكوين|تشغيل/إيقاف تشغيل الحماية في الوقت الحقيقي|`mdatp config real-time-protection --value [enabled/disabled]`|
|تكوين|تشغيل/إيقاف تشغيل الحماية السحابية|`mdatp config cloud --value [enabled/disabled]`|
|تكوين|تشغيل/إيقاف تشغيل تشخيص المنتج|`mdatp config cloud-diagnostic --value [enabled/disabled]`|
|تكوين|تشغيل/إيقاف تشغيل إرسال العينة التلقائي|`mdatp config cloud-automatic-sample-submission --value [enabled/disabled]`|
|تكوين|إضافة اسم خطر إلى القائمة المسموح بها|`mdatp threat allowed add --name [threat-name]`|
|تكوين|إزالة اسم خطر من القائمة المسموح بها|`mdatp threat allowed remove --name [threat-name]`|
|تكوين|سرد جميع أسماء التهديدات المسموح بها|`mdatp threat allowed list`|
|تكوين|تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application -- action block`|
|تكوين|إيقاف تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application -- action off`|
|تكوين|تشغيل وضع التدقيق لحماية PUA|`mdatp threat policy set --type potentially_unwanted_application -- action audit`|
|تكوين|تشغيل/إيقاف تشغيل وضع الحماية من الفيروسات السلبي|`mdatp config passive-mode --value [enabled/disabled]`|
|تكوين|تكوين درجة التوازي لمسح عند الطلب|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|تكوين|تشغيل/إيقاف تشغيل عمليات الفحص بعد تحديثات معلومات الأمان|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|تكوين|تشغيل/إيقاف تشغيل مسح الأرشيف (عمليات المسح عند الطلب فقط)|`mdatp config scan-archives --value [enabled/disabled]`|
|التشخيصات|تغيير مستوى السجل|`mdatp log level set --level [error/warning/info/verbose]`|
|التشخيصات|إنشاء سجلات تشخيصية|`mdatp diagnostic create --path [directory]`|
|الصحة|التحقق من صحة المنتج|`mdatp health`|
|الصحة|التحقق من سمة منتج سفلي|`mdatp health --field [attribute: healthy/licensed/engine_version...]`|
|الحماية|مسح مسار ضوئيا|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|الحماية|إجراء فحص سريع|`mdatp scan quick`|
|الحماية|إجراء فحص كامل|`mdatp scan full`|
|الحماية|إلغاء فحص مستمر عند الطلب|`mdatp scan cancel`|
|الحماية|طلب تحديث معلومات الأمان|`mdatp definitions update`|
|الكشف التلقائي والاستجابة على النقط النهائية|علامة "تعيين/إزالة"، المجموعة المعتمدة فقط|`mdatp edr tag set --name GROUP --value [name]`|
|الكشف التلقائي والاستجابة على النقط النهائية|إزالة علامة المجموعة من الجهاز|`mdatp edr tag remove --tag-name [name]`|
|الكشف التلقائي والاستجابة على النقط النهائية|إضافة "معرّف المجموعة"|`mdatp edr group-ids --group-id [group]`|

### <a name="how-to-enable-autocompletion"></a>كيفية تمكين الإبهار التلقائي

لتمكين الإبعاد التلقائي في bash، قم بتشغيل الأمر التالي ثم أعد تشغيل جلسة عمل المحطة الطرفية:

```bash
echo "source /Applications/Microsoft\ Defender.app/Contents/Resources/Tools/mdatp_completion.bash" >> ~/.bash_profile
```

لتمكين الإبهار التلقائي بالتنسيق zsh:

- تحقق مما إذا كان الإبهار التلقائي ممكنا على جهازك:

   ```zsh
   cat ~/.zshrc | grep autoload
   ```

- إذا لم ينتج عن الأمر السابق أي إخراج، يمكنك تمكين الإبهار التلقائي باستخدام الأمر التالي:

   ```zsh
   echo "autoload -Uz compinit && compinit" >> ~/.zshrc
   ```

- قم بتشغيل الأوامر التالية لتمكين الإبعاد التلقائي ل Microsoft Defender ل Endpoint على macOS وإعادة تشغيل جلسة عمل المحطة الطرفية:

   ```zsh
   sudo mkdir -p /usr/local/share/zsh/site-functions

   sudo ln -svf "/Applications/Microsoft Defender.app/Contents/Resources/Tools/mdatp_completion.zsh" /usr/local/share/zsh/site-functions/_mdatp
   ```

## <a name="client-microsoft-defender-for-endpoint-quarantine-directory"></a>دليل الفحص الخاص ب Microsoft Defender for Endpoint

`/Library/Application Support/Microsoft/Defender/quarantine/` يحتوي على الملفات التي تم فحصها بواسطة `mdatp`. مسماة الملفات باسم "تعقب التهديدات". يتم عرض التعقب الحاليمعيارات التعقب مع `mdatp threat list`.

## <a name="microsoft-defender-for-endpoint-portal-information"></a>معلومات مدخل Microsoft Defender for Endpoint

[الكشف التلقائي والاستجابة على النقط النهائية قدرات macOS](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/edr-capabilities-for-macos-have-now-arrived/ba-p/1047801) الآن، على مدونة Microsoft Defender for Endpoint، توفر إرشادات مفصلة حول ما يجب توقعه في مركز أمان نقطة النهاية ل Microsoft Defender.
