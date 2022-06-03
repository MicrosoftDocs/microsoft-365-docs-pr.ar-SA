---
title: تشغيل محلل العميل على macOS أو Linux
description: تعرف على كيفية تشغيل Microsoft Defender لنقطة النهاية Client Analyzer على macOS أو Linux
keywords: محلل العميل، مستشعر استكشاف الأخطاء وإصلاحها، المحلل، mdeanalyzer، macos، linux، mdeanalyzer
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
ms.openlocfilehash: 9e3b52f5e16a2294cc504791928f10a96e5e54c7
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872753"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>تشغيل محلل العميل على macOS وLinux


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>تشغيل المحلل من خلال سيناريو واجهة المستخدم الرسومية

1. قم بتنزيل أداة [محلل عميل XMDE](https://aka.ms/XMDEClientAnalyzer) إلى جهاز macOS أو Linux الذي تحتاج إلى التحقيق فيه.

   > [!NOTE]
   > تجزئة SHA256 الحالية ل 'XMDEClientAnalyzer.zip' التي يتم تنزيلها من الارتباط أعلاه هي: 'A9BF065DE3F2608A309BC4F5295548BB9931F107BF2F01DC42A789C5527C1308'.

2. استخراج محتويات XMDEClientAnalyzer.zip على الجهاز.

3. افتح جلسة عمل طرفية، وغير الدليل إلى الموقع المستخرج، ثم قم بتشغيل:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > على Linux، إذا لم يكن لدى البرنامج النصي أذونات للتنفيذ، فستحتاج إلى التشغيل أولا:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>تشغيل المحلل باستخدام سيناريو محطة طرفية أو SSH

افتح محطة طرفية أو SSH في الجهاز ذي الصلة وقم بتشغيل الأوامر التالية:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. تشغيل كاستخدام غير جذر لتثبيت pip المطلوبة وlxml أي المكونات: `./mde_support_tool.sh`

4. لتجميع حزمة التشخيص الفعلية وإنشاء تشغيل ملف أرشيف النتائج مرة أخرى كجذر: `./mde_support_tool.sh -d`

> [!NOTE]
> - بالنسبة إلى Linux، يتطلب المحلل 'lxml' لإنتاج ناتج النتيجة. إذا لم يتم تثبيته، سيحاول المحلل إحضاره من المستودع الرسمي لحزم python أدناه: <https://pypi.org/search/?q=lxml>
> 
> - بالإضافة إلى ذلك، تتطلب الأداة حاليا تثبيت الإصدار 3 من Python أو إصدار أحدث.
>
> - إذا كنت تعمل على جهاز لا يمكنه استخدام Python 3 أو إحضار مكون lxml، يمكنك تنزيل إصدار ثنائي يستند إلى محلل لا يحتوي على أي من المتطلبات: [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - إذا كان جهازك خلف وكيل، يمكنك ببساطة تمرير الخادم الوكيل كمتغير بيئة إلى البرنامج النصي mde_support_tool.sh. على سبيل المثال: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

على سبيل المثال:

:::image type="content" source="images/4ca188f6c457e335abe3c9ad3eddda26.png" alt-text="مثال سطر الأوامر" lightbox="images/4ca188f6c457e335abe3c9ad3eddda26.png":::

تعليمات بناء الجملة الإضافية:

**-h** \# تعليمات<br>
\# إظهار رسالة التعليمات

**الاداء** \# الاداء<br>
\# يجمع التتبع الشامل لتحليل مشكلة الأداء التي يمكن إعادة إنتاجها عند الطلب. يستخدم `--length=<seconds>` لتحديد مدة المعيار.

**-o** \# الاخراج<br>
\# تحديد مسار الوجهة لملف النتيجة

**-nz** \# No-Zip<br>
\# إذا تم تعيينه، فسيتم إنشاء دليل بدلا من ملف أرشيف ناتج

**-f** \# القوه<br>
\# الكتابة فوق ما إذا كان الإخراج موجودا بالفعل في مسار الوجهة

## <a name="result-package-contents-on-macos-and-linux"></a>محتويات حزمة النتائج على macOS وLinux

- report.html

  الوصف: ملف إخراج HTML الرئيسي الذي سيحتوي على النتائج والإرشادات التي يمكن أن ينتجها البرنامج النصي للمحلل على الجهاز.

- mde_diagnostic.zip

  الوصف: نفس الإخراج التشخيصي الذي يتم إنشاؤه عند تشغيل *إنشاء تشخيص mdatp* على أي [من macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  او

  [ينكس](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  الوصف: إخراج XML الذي يتم إنشاؤه أثناء التشغيل ويستخدم لإنشاء ملف تقرير html.

- Processes_information.txt

  الوصف: يحتوي على تفاصيل تشغيل Microsoft Defender لنقطة النهاية العمليات ذات الصلة على النظام.

- Log.txt

  الوصف: يحتوي على نفس رسائل السجل المكتوبة على الشاشة أثناء جمع البيانات.

- Health.txt

  الوصف: نفس مخرجات الحماية الأساسية التي تظهر عند تشغيل أمر *حماية mdatp* .

- Events.xml

  الوصف: ملف XML إضافي يستخدمه المحلل عند إنشاء تقرير HTML.

- Audited_info.txt

  الوصف: تفاصيل حول الخدمة التي تم تدقيقها والمكونات ذات الصلة لنظام التشغيل [Linux](/microsoft-365/security/defender-endpoint/linux-resources)

- perf_benchmark.tar.gz

  الوصف: تقارير اختبار الأداء. لن ترى هذا إلا إذا كنت تستخدم معلمة الأداء.
