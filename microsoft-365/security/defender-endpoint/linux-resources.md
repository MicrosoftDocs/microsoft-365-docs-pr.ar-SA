---
title: Microsoft Defender ل Endpoint على موارد Linux
ms.reviewer: ''
description: يصف موارد Microsoft Defender ل Endpoint على Linux، بما في ذلك كيفية إلغاء تثبيته، وكيفية تجميع سجلات التشخيص، وأوامر CLI، وا المشاكل المعروفة في المنتج.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، التثبيت، النشر، إزالة التثبيت، المهى، قابل للأكل، linux، redhat، ubuntu، debian، sles، suse، centos
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
ms.openlocfilehash: a32c8c91350218da619de18e0b1b398a93bf7fda
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583134"
---
# <a name="resources"></a>الموارد

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="collect-diagnostic-information"></a>تجميع المعلومات التشخيصية

إذا كان بإمكانك إعادة إنتاج مشكلة، فالزيادة في مستوى التسجيل أولا وتشغيل النظام لبعض الوقت، ثم استعادة مستوى التسجيل إلى الإعداد الافتراضي.

1. زيادة مستوى التسجيل:

   ```bash
   mdatp log level set --level debug
   ```

   ```Output
   Log level configured successfully
   ```

2. إعادة إنتاج المشكلة.

3. قم بتشغيل الأمر التالي لنسوخ سجلات Defender ل Endpoint. سيتم تخزين الملفات داخل أرشيف .zip.

   ```bash
   sudo mdatp diagnostic create
   ```

    سيطبع هذا الأمر أيضا مسار الملف إلى النسخة الاحتياطية بعد نجاح العملية:

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

إذا حدث خطأ أثناء التثبيت، سيقر المثبت بفشل عام فقط.

سيتم حفظ السجل التفصيلي في `/var/log/microsoft/mdatp/install.log`.
إذا واجهت مشاكل أثناء التثبيت، أرسل لنا هذا الملف حتى يمكننا مساعدتك في تشخيص السبب.

## <a name="uninstall"></a>إلغاء التثبيت

هناك عدة طرق  إلغاء تثبيت Defender ل Endpoint على Linux. إذا كنت تستخدم أداة تكوين مثل "مهى"، فاتبع إرشادات إزالة تثبيت الحزمة لأداة التكوين.

### <a name="manual-uninstallation"></a>إزالة التثبيت اليدوي

- `sudo yum remove mdatp` ل RHEL والمتغيرات(CentOS و Oracle Linux).
- `sudo zypper remove mdatp` ل SLES والمتغيرات.
- `sudo apt-get purge mdatp` لنظامي Ubuntu و Debian.

## <a name="configure-from-the-command-line"></a>تكوين من سطر الأوامر

يمكن تنفيذ المهام المهمة، مثل التحكم في إعدادات المنتج وتحريك عمليات الفحص عند الطلب، من سطر الأوامر.

### <a name="global-options"></a>الخيارات "عام"

بشكل افتراضي، ينتج عن أداة سطر الأوامر النتيجة بتنسيق قابل للقراءة بواسطة الإنسان. بالإضافة إلى ذلك، تدعم الأداة أيضا إخراج النتيجة ك JSON، وهو أمر مفيد لسيناريوهات التنفيذ التلقائي. لتغيير الإخراج إلى JSON، مرر `--output json` إلى أي من الأوامر أدناه.

### <a name="supported-commands"></a>الأوامر المعتمدة

يسرد الجدول التالي الأوامر لبعض السيناريوهات الأكثر شيوعا. تشغيل `mdatp help` من المحطة الطرفية لعرض القائمة الكاملة بالأوامر المعتمدة.

<br>

****

|مجموعة|السيناريو|الأمر|
|---|---|---|
|تكوين|تشغيل/إيقاف تشغيل الحماية في الوقت الحقيقي|`mdatp config real-time-protection --value [enabled\|disabled]`|
|تكوين|تشغيل/إيقاف تشغيل مراقبة السلوك|`mdatp config behavior-monitoring --value [enabled\|disabled]`
|تكوين|تشغيل/إيقاف تشغيل الحماية السحابية|`mdatp config cloud --value [enabled\|disabled]`|
|تكوين|تشغيل/إيقاف تشغيل تشخيص المنتج|`mdatp config cloud-diagnostic --value [enabled\|disabled]`|
|تكوين|تشغيل/إيقاف تشغيل إرسال العينة التلقائي|`mdatp config cloud-automatic-sample-submission [enabled\|disabled]`|
|تكوين|تشغيل/إيقاف تشغيل وضع AV السلبي|`mdatp config passive-mode --value [enabled\|disabled]`|
|تكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لملحق ملف|`mdatp exclusion extension [add\|remove] --name [extension]`|
|تكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لملف|`mdatp exclusion file [add\|remove] --path [path-to-file]`|
|تكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات للدالة|`mdatp exclusion folder [add\|remove] --path [path-to-directory]`|
|تكوين|إضافة/إزالة استثناء برنامج الحماية من الفيروسات لعملية|`mdatp exclusion process [add\|remove] --path [path-to-process]` <p> `mdatp exclusion process [add\|remove] --name [process-name]`|
|تكوين|سرد جميع استثناءات برامج الحماية من الفيروسات|`mdatp exclusion list`|
|تكوين|إضافة اسم خطر إلى القائمة المسموح بها|`mdatp threat allowed add --name [threat-name]`|
|تكوين|إزالة اسم خطر من القائمة المسموح بها|`mdatp threat allowed remove --name [threat-name]`|
|تكوين|سرد جميع أسماء التهديدات المسموح بها|`mdatp threat allowed list`|
|تكوين|تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application --action block`|
|تكوين|إيقاف تشغيل حماية PUA|`mdatp threat policy set --type potentially_unwanted_application --action off`|
|تكوين|تشغيل وضع التدقيق لحماية PUA|`mdatp threat policy set --type potentially_unwanted_application --action audit`|
|تكوين|تكوين درجة التوازي لمسح عند الطلب|`mdatp config maximum-on-demand-scan-threads --value [numerical-value-between-1-and-64]`|
|تكوين|تشغيل/إيقاف تشغيل عمليات الفحص بعد تحديثات معلومات الأمان|`mdatp config scan-after-definition-update --value [enabled/disabled]`|
|تكوين|تشغيل/إيقاف تشغيل مسح الأرشيف (عمليات المسح عند الطلب فقط)|`mdatp config scan-archives --value [enabled/disabled]`|
|التشخيصات|تغيير مستوى السجل|`mdatp log level set --level verbose [error|warning|info|verbose]`|
|التشخيصات|إنشاء سجلات تشخيصية|`mdatp diagnostic create --path [directory]`|
|الصحة|التحقق من صحة المنتج|`mdatp health`|
|الحماية|مسح مسار ضوئيا|`mdatp scan custom --path [path] [--ignore-exclusions]`|
|الحماية|إجراء فحص سريع|`mdatp scan quick`|
|الحماية|إجراء فحص كامل|`mdatp scan full`|
|الحماية|إلغاء فحص مستمر عند الطلب|`mdatp scan cancel`|
|الحماية|طلب تحديث معلومات الأمان|`mdatp definitions update`|
|محفوظات الحماية|طباعة محفوظات الحماية الكاملة|`mdatp threat list`|
|محفوظات الحماية|الحصول على تفاصيل التهديدات|`mdatp threat get --id [threat-id]`|
|إدارة الفحص|سرد جميع الملفات المعزولة|`mdatp threat quarantine list`|
|إدارة الفحص|إزالة كل الملفات من الفحص|`mdatp threat quarantine remove-all`|
|إدارة الفحص|إضافة ملف تم اكتشافه كخطر على الفحص|`mdatp threat quarantine add --id [threat-id]`|
|إدارة الفحص|إزالة ملف تم اكتشافه كخطر من الفحص|`mdatp threat quarantine remove --id [threat-id]`|
|إدارة الفحص|استعادة ملف من الفحص|`mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`|
|الكشف عن نقطة النهاية والاستجابة لها|تعيين المعاينة المبكرة (غير المموزة)|`mdatp edr early-preview [enable|disable]`|
|الكشف عن نقطة النهاية والاستجابة لها|تعيين "مجموعة-id"|`mdatp edr group-ids --group-id [group-id]`|
|الكشف عن نقطة النهاية والاستجابة لها|تعيين / إزالة العلامة، معتمد `GROUP` فقط|`mdatp edr tag set --name GROUP --value [tag]`|
|الكشف عن نقطة النهاية والاستجابة لها|استثناءات القائمة (الجذر)|`mdatp edr exclusion list [processes|paths|extensions|all]`|
|
