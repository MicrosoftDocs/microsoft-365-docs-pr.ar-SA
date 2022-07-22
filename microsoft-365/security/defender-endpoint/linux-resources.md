---
title: Microsoft Defender لنقطة النهاية على موارد Linux
ms.reviewer: ''
description: يصف موارد Microsoft Defender لنقطة النهاية على Linux، بما في ذلك كيفية إلغاء تثبيته، وكيفية جمع سجلات التشخيص، وأوامر CLI، والمشاكل المعروفة مع المنتج.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، التثبيت، التوزيع، إلغاء التثبيت، الدمى، ansible، linux، redhat، ubuntu، debian، sles، suse، centos
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
ms.openlocfilehash: 0971933f1099192b1cb8b7a844793f264ef2aa15
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949470"
---
# <a name="resources"></a>الموارد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>تجميع المعلومات التشخيصية

إذا كان بإمكانك إعادة إنتاج مشكلة، فبادر أولا بزيادة مستوى التسجيل، وقم بتشغيل النظام لبعض الوقت، ثم قم باستعادة مستوى التسجيل إلى المستوى الافتراضي.

1. زيادة مستوى التسجيل:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. إعادة إنشاء المشكلة.

3. قم بتشغيل الأمر التالي لإجراء نسخ احتياطي لسجلات Defender لنقطة النهاية. سيتم تخزين الملفات داخل أرشيف .zip.

   ```bash
   sudo mdatp diagnostic create
   ```

    سيقوم هذا الأمر أيضا بطباعة مسار الملف إلى النسخة الاحتياطية بعد نجاح العملية:

   ```Output
   Diagnostic file created: <path to file>
   ```

4. استعادة مستوى التسجيل:

   ```bash
   mdatp log level set --level info
   ```

   ```Output
   Log level configured successfully
   ```

## <a name="log-installation-issues"></a>مشاكل تثبيت السجل

إذا حدث خطأ أثناء التثبيت، فسيبلغ المثبت عن فشل عام فقط.

سيتم حفظ السجل التفصيلي في `/var/log/microsoft/mdatp/install.log`.
إذا واجهت مشاكل أثناء التثبيت، فأرسل لنا هذا الملف حتى نتمكن من المساعدة في تشخيص السبب.

## <a name="uninstall"></a>الغاء تثبيت

هناك عدة طرق لإلغاء تثبيت Defender لنقطة النهاية على Linux. إذا كنت تستخدم أداة تكوين مثل Puppet، فاتبع إرشادات إلغاء تثبيت الحزمة لأداة التكوين.

### <a name="manual-uninstallation"></a>إلغاء التثبيت يدويا

- `sudo yum remove mdatp` ل RHEL والمتغيرات (CentOS وOracle Linux).
- `sudo zypper remove mdatp` ل SLES والمتغيرات.
- `sudo apt-get purge mdatp` لأنظمة Ubuntu و Debian.

## <a name="configure-from-the-command-line"></a>التكوين من سطر الأوامر

يمكن تنفيذ المهام الهامة، مثل التحكم في إعدادات المنتج وتشغيل عمليات الفحص عند الطلب، من سطر الأوامر.

### <a name="global-options"></a>خيارات عمومية

بشكل افتراضي، تقوم أداة سطر الأوامر بإخراج النتيجة بتنسيق يمكن للإنسان قراءته. بالإضافة إلى ذلك، تدعم الأداة أيضا إخراج النتيجة ك JSON، وهو أمر مفيد لسيناريوهات التشغيل التلقائي. لتغيير الإخراج إلى JSON، مرر `--output json` إلى أي من الأوامر أدناه.

### <a name="supported-commands"></a>الأوامر المدعومة

يسرد الجدول التالي الأوامر لبعض السيناريوهات الأكثر شيوعا. تشغيل `mdatp help` من المحطة الطرفية لعرض القائمة الكاملة للأوامر المدعومة.

<br>

****

|مجموعة|السيناريو|الامر|
|---|---|---|
|التكوين|تشغيل/إيقاف تشغيل الحماية في الوقت الحقيقي|`mdatp config real-time-protection --value [enabled\|disabled]`|
|التكوين|تشغيل/إيقاف تشغيل مراقبة السلوك|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|التكوين|تشغيل/إيقاف تشغيل حماية السحابة|`mdatp config cloud --value [enabled\|disabled]`|
|التكوين|تشغيل/إيقاف تشغيل تشخيصات المنتجات|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|التكوين|تشغيل/إيقاف تشغيل الإرسال التلقائي للعينة|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|التكوين|تشغيل/إيقاف تشغيل وضع AV الخامل|`mdatp config passive-mode --value [enabled\|disabled]`|
|التكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لملحق ملف|`mdatp exclusion extension [add\|remove] --name [extension]`|
|التكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لملف|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|التكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لدليل|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|التكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لعملية|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|التكوين|سرد جميع استثناءات برنامج الحماية من الفيروسات|`mdatp exclusion list`|
|التكوين|إضافة اسم تهديد إلى القائمة المسموح بها|`mdatp threat allowed add --name [threat-name]`|
|التكوين|إزالة اسم تهديد من القائمة المسموح بها|`mdatp threat allowed remove --name [threat-name]`|
|التكوين|سرد كافة أسماء التهديدات المسموح بها|`mdatp threat allowed list`|
|التكوين|تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|التكوين|إيقاف تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|التكوين|تشغيل وضع التدقيق لحماية PUA|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|التكوين|تكوين درجة التوازي لإجراء عمليات الفحص عند الطلب|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|التكوين|تشغيل/إيقاف تشغيل عمليات الفحص بعد تحديثات معلومات الأمان|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل فحص الأرشيف (عمليات المسح حسب الطلب فقط)|`mdatp config scan-archives --value [enabled/disabled]`|
|التكوين|تشغيل/إيقاف تشغيل حساب تجزئة الملف|`mdatp config enable-file-hash-computation --value [enabled/disabled]`|
|تشخيص|تغيير مستوى السجل|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|تشخيص|إنشاء سجلات تشخيصية|`mdatp diagnostic create --path [directory]`|
|الحماية|التحقق من صحة المنتج|`mdatp health`|
|حمايه|مسح مسار ضوئيا|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|حمايه|إجراء فحص سريع|`mdatp scan quick`|
|حمايه|إجراء فحص كامل|`mdatp scan full`|
|حمايه|إلغاء فحص مستمر عند الطلب|`mdatp scan cancel`|
|حمايه|طلب تحديث معلومات الأمان|`mdatp definitions update`|
|محفوظات الحماية|طباعة محفوظات الحماية الكاملة|`mdatp threat list`|
|محفوظات الحماية|الحصول على تفاصيل التهديد|`mdatp threat get --id [threat-id]`|
|إدارة العزل|سرد كافة الملفات المعزولة|`mdatp threat quarantine list`|
|إدارة العزل|إزالة كافة الملفات من العزل|`mdatp threat quarantine remove-all`|
|إدارة العزل|إضافة ملف تم اكتشافه كتهديد إلى العزل|`mdatp threat quarantine add --id [threat-id]`|
|إدارة العزل|إزالة ملف تم اكتشافه كتهديد من العزل|`mdatp threat quarantine remove --id [threat-id]`|
|إدارة العزل|استعادة ملف من العزل|`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`|
|الكشف عن نقطة النهاية والاستجابة لها|تعيين المعاينة المبكرة (غير مستخدمة)|`mdatp edr early-preview [enable|disable]`|
|الكشف عن نقطة النهاية والاستجابة لها|تعيين معرف المجموعة|`mdatp edr group-ids --group-id [group-id]`|
|الكشف عن نقطة النهاية والاستجابة لها|تعيين / إزالة العلامة، معتمدة فقط `GROUP`|`mdatp edr tag set --name GROUP --value [tag]`|
|الكشف عن نقطة النهاية والاستجابة لها|استثناءات القائمة (الجذر)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
