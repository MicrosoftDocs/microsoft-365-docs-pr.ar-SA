---
title: تشغيل محلل العميل على macOS أو Linux
description: تعرف على كيفية تشغيل "محلل Microsoft Defender لنقطة النهاية" على macOS أو Linux
keywords: محلل العميل، استكشاف الأخطاء وإصلاحها، محلل، mdeanalyzer، macos، linux، mdeanalyzer
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: d56cbb48697c4804aa493d945ff81c52e12f86c5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470076"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>تشغيل محلل العملاء على macOS و Linux


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>تشغيل المحلل عبر سيناريو واجهة المستخدم (GUI)

1. قم [بتنزيل أداة محلل عميل XMDE](https://aka.ms/XMDEClientAnalyzer) إلى جهاز macOS أو Linux الذي تحتاج إلى التحقق منه.

   > [!NOTE]
   > إن علامة تفرع SHA256 الحالية ل "XMDEClientAnalyzer.zip" التي يتم تنزيلها من الارتباط أعلاه هي: 'A9BF065DE3F2608A309BC4F5295548BB9931F107BF2F01DC42A789C5527C1308'.

2. استخراج محتويات XMDEClientAnalyzer.zip على الجهاز.

3. افتح جلسة عمل المحطة الطرفية، غير الدليل إلى الموقع الذي تم استخراجه ثم تشغيل:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > في Linux، إذا لم يكن البرنامج النصي لديه أذونات لتنفيذه، فسوف تحتاج إلى التشغيل أولا:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>تشغيل المحلل باستخدام سيناريو SSH أو محطة طرفية

افتح محطة أو SSH في الجهاز ذي الصلة وتولى تشغيل الأوامر التالية:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. قم بتشغيلها ك الاستخدام غير الجذر لتثبيت المكونين pip و lxml المطلوبين: `./mde_support_tool.sh`

4. لتجميع الحزمة التشخيصية الفعلية وإنشاء ملف أرشيف النتائج مرة أخرى كتجذر: `./mde_support_tool.sh -d`

> [!NOTE]
> - بالنسبة إلى Linux، يحتاج المحلل إلى 'lxml' للحصول على النتيجة. إذا لم يكن مثبتا، سيحاول المحلل إحضاره من المستودع الرسمي لحزم python أدناه: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - بالإضافة إلى ذلك، تتطلب الأداة حاليا تثبيت إصدار Python 3 أو إصدار أحدث.
>
> - إذا كنت تعمل على جهاز لا يمكنه استخدام Python 3 أو إحضار مكون lxml، يمكنك تنزيل إصدار ثنائي يستند إلى محلل لا يحتاج إلى أي من المتطلبات: [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - إذا كان جهازك خلف وكيل، يمكنك ببساطة تمرير الخادم الوكيل كمتغير بيئة إلى البرنامج النصي mde_support_tool.sh. على سبيل المثال: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

على سبيل المثال:

:::image type="content" source="images/4ca188f6c457e335abe3c9ad3eddda26.png" alt-text="مثال سطر الأوامر" lightbox="images/4ca188f6c457e335abe3c9ad3eddda26.png":::

تعليمات بناء الجملة الإضافية:

**-h** \# تعليمات<br>
\# إظهار رسالة تعليمات

**الأداء** \# الأداء<br>
\# يجمع التتبع الموسع لتحليل مشكلة الأداء التي يمكن إعادة إنتاجها عند الطلب. يستخدم `--length=<seconds>` لتحديد مدة المعيار.

**-o** \# الإخراج<br>
\# تحديد مسار الوجهة لملف النتيجة

**-nz** \# No-Zip<br>
\# إذا تم تعيينه، سيتم إنشاء دليل بدلا من ملف أرشيف ناتج

**-f** \# فرض<br>
\# الكتابة فوق ما إذا كان الإخراج موجودا بالفعل في مسار الوجهة

## <a name="result-package-contents-on-macos-and-linux"></a>محتويات حزمة النتائج على macOS و Linux

- report.html

  الوصف: ملف إخراج HTML الرئيسي الذي سيحتوي على النتائج والإرشادات التي يمكن أن ينتجها البرنامج النصي للمحلل على الجهاز.

- mde_diagnostic.zip

  الوصف: نفس الإخراج التشخيصي الذي يتم إنشاؤه عند تشغيل *إنشاء تشخيص mdatp* على [أي من macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  أو

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  الوصف: إخراج XML الذي يتم إنشاؤه أثناء التشغيل ويستخدم لإنشاء ملف تقرير html.

- Processes_information.txt

  الوصف: يحتوي على تفاصيل Microsoft Defender لنقطة النهاية العمليات ذات الصلة على النظام.

- Log.txt

  الوصف: يحتوي على نفس رسائل السجل المكتوبة على الشاشة أثناء تجميع البيانات.

- Health.txt

  الوصف: ناتج الصحة الأساسي نفسه الذي يظهر عند تشغيل *الأمر "صحة mdatp* ".

- Events.xml

  الوصف: ملف XML إضافي يستخدمه المحلل عند إنشاء تقرير HTML.

- Auditd_info.txt

  الوصف: تفاصيل حول الخدمة التي تم تدقيقها والمكونات ذات الصلة ل [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events) OS

- perf_benchmark.tar.gz

  الوصف: تقارير اختبار الأداء. لن ترى هذا إلا إذا كنت تستخدم معلمة الأداء.
