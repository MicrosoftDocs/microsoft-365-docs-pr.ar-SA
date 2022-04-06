---
title: استكشاف مشكلات الأداء وإصلاحها Microsoft Defender لنقطة النهاية على Linux
description: استكشاف مشكلات الأداء وإصلاحها في Microsoft Defender لنقطة النهاية على Linux.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، الأداء
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 369c6a198035418a5c16e2a72d84c8dcfc88be2f
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666427"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>استكشاف مشكلات الأداء وإصلاحها Microsoft Defender لنقطة النهاية على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يوفر هذا المستند تعليمات حول كيفية تضييق مشكلات الأداء المتعلقة ب Defender لنقطة النهاية على Linux باستخدام أدوات التشخيص المتاحة لتكون قادرة على فهم وتخفيف حالات النقص الحالية في الموارد والعمليات التي تجعل النظام في مثل هذه الحالات. تحدث مشاكل الأداء بشكل رئيسي بسبب الازدحام في نظام فرعي واحد أو أكثر من الأجهزة، اعتمادا على ملف تعريف استخدام الموارد على النظام. في بعض الأحيان تكون التطبيقات حساسة لموارد إدخال/إخراج القرص وقد تحتاج إلى سعة أكبر لوحدة المعالجة المركزية، وفي بعض الأحيان تكون بعض التكوينات غير مستدامة، وقد تؤدي إلى العديد من العمليات الجديدة، وتفتح العديد من واصفات الملفات.

اعتمادا على التطبيقات التي تقوم بتشغيلها وخصائص جهازك، قد تواجه أداء دون المستوى الأمثل عند تشغيل Defender لنقطة النهاية على Linux. على وجه الخصوص، يمكن للتطبيقات أو عمليات النظام التي تصل إلى العديد من الموارد مثل وحدة المعالجة المركزية والقرص والذاكرة على مدى فترة زمنية قصيرة أن تؤدي إلى مشكلات في الأداء في Defender لنقطة النهاية على Linux.

> [!WARNING]
> قبل البدء، **الرجاء التأكد من أن منتجات الأمان الأخرى لا تعمل حاليا على الجهاز**. قد تتعارض منتجات الأمان المتعددة وتؤثر على أداء المضيف.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>استكشاف مشكلات الأداء وإصلاحها باستخدام إحصائيات الحماية في الوقت الحقيقي

**ينطبق على:**
- مشكلات الأداء المتعلقة ب AV فقط

الحماية في الوقت الحقيقي (RTP) هي ميزة من ميزات Defender لنقطة النهاية على Linux التي تراقب وتحمي جهازك باستمرار من التهديدات. وهو يتكون من مراقبة الملفات والعمليات وغيرها من الأساليب الاستباقية.

يمكن استخدام الخطوات التالية لاستكشاف الأخطاء وإصلاحها والتخفيف من حدة هذه المشكلات:

1. تعطيل الحماية في الوقت الحقيقي باستخدام أحد الأساليب التالية ومراقبة ما إذا كان الأداء يتحسن. يساعد هذا النهج على تضييق نطاق ما إذا كان Defender لنقطة النهاية على Linux يساهم في مشكلات الأداء.

    إذا لم تكن مؤسستك تدير جهازك، يمكن تعطيل الحماية في الوقت الحقيقي من سطر الأوامر:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    إذا كانت مؤسستك تدير جهازك، يمكن تعطيل الحماية في الوقت الحقيقي من قبل المسؤول باستخدام الإرشادات الواردة في [تعيين تفضيلات Defender لنقطة النهاية على Linux](linux-preferences.md).

    > [!NOTE]
    > إذا استمرت مشكلة الأداء أثناء إيقاف تشغيل الحماية في الوقت الحقيقي، فقد يكون أصل المشكلة هو مكون الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). في هذه الحالة، الرجاء اتباع الخطوات الواردة من **استكشاف مشاكل الأداء وإصلاحها باستخدام قسم محلل العميل Microsoft Defender لنقطة النهاية** من هذه المقالة.

2. للعثور على التطبيقات التي تقوم بتشغيل معظم عمليات الفحص، يمكنك استخدام الإحصائيات في الوقت الحقيقي التي جمعها Defender لنقطة النهاية على Linux.

    > [!NOTE]
    > تتوفر هذه الميزة في الإصدار 100.90.70 أو أحدث.

    يتم تمكين هذه الميزة بشكل افتراضي على القنوات `Dogfood` والقنوات `InsiderFast` . إذا كنت تستخدم قناة تحديث مختلفة، يمكن تمكين هذه الميزة من سطر الأوامر:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    تتطلب هذه الميزة تمكين الحماية في الوقت الحقيقي. للتحقق من حالة الحماية في الوقت الحقيقي، قم بتشغيل الأمر التالي:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    تحقق من أن `real_time_protection_enabled` الإدخال هو `true`. وإلا، فشغل الأمر التالي لتمكينه:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    لجمع الإحصائيات الحالية، قم بتشغيل:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > يضمن استخدام ```--output json``` (لاحظ الشرطة المزدوجة) أن تنسيق الإخراج جاهز لتحليله.

    سيعرض إخراج هذا الأمر جميع العمليات ونشاط الفحص المقترن بها.

3. على نظام Linux الخاص بك، قم بتنزيل عينة محلل Python **high_cpu_parser.py** باستخدام الأمر:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    يجب أن يكون إخراج هذا الأمر مشابها لما يلي:


    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in 0s
    ```

4. بعد ذلك، اكتب الأوامر التالية:

    ```bash
    chmod +x high_cpu_parser.py
    ```

    ```bash
    cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
    ```

      إخراج ما سبق هو قائمة بأفضل المساهمين في مشكلات الأداء. العمود الأول هو معرف العملية (PID)، والعمود الثاني هو اسم العملية، والعمود الأخير هو عدد الملفات الممسوحة ضوئيا، والتي تم فرزها حسب التأثير.
    على سبيل المثال، سيكون إخراج الأمر شيئا مثل ما يلي: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool    1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd     407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    لتحسين أداء Defender لنقطة النهاية على Linux، حدد موقع الشخص الذي يحتوي على أعلى رقم تحت `Total files scanned` الصف وأضف استثناء له. لمزيد من المعلومات، راجع [تكوين الاستثناءات والتحقق من صحتها ل Defender لنقطة النهاية على Linux](linux-exclusions.md).

    > [!NOTE]
    > يخزن التطبيق الإحصائيات في الذاكرة ويتعقب نشاط الملف فقط منذ بدئه وتم تمكين الحماية في الوقت الحقيقي. لا يتم حساب العمليات التي تم تشغيلها قبل أو خلال الفترات التي كانت فيها الحماية في الوقت الحقيقي متوقفة عن التشغيل. بالإضافة إلى ذلك، يتم حساب الأحداث التي قامت بتشغيل عمليات الفحص فقط.

5. تكوين Microsoft Defender لنقطة النهاية على Linux مع استثناءات للعمليات أو مواقع الأقراص التي تساهم في مشكلات الأداء وإعادة تمكين الحماية في الوقت الحقيقي.

    للمزيد من المعلومات، راجع [تكوين الاستثناءات والتحقق من صحتها في Microsoft Defender لنقطة النهاية على Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>استكشاف مشكلات الأداء وإصلاحها باستخدام Microsoft Defender لنقطة النهاية Client Analyzer

**ينطبق على:**
- مشكلات الأداء لكافة مكونات Defender لنقطة النهاية المتوفرة مثل AV و الكشف التلقائي والاستجابة على النقط النهائية  

يمكن لمحلل العميل Microsoft Defender لنقطة النهاية (MDECA) جمع التتبعات والسجلات ومعلومات التشخيص من أجل استكشاف مشكلات الأداء [وإصلاحها على الأجهزة الملحقة على](/microsoft-365/security/defender-endpoint/onboard-configure) Linux.

> [!NOTE]
> يتم استخدام أداة محلل العميل Microsoft Defender لنقطة النهاية بانتظام من قبل خدمات دعم العملاء من Microsoft (CSS) لجمع معلومات مثل (على سبيل المثال لا الحصر) عناوين IP وأسماء أجهزة الكمبيوتر التي ستساعد على استكشاف المشكلات التي قد تواجهها مع Microsoft Defender لنقطة النهاية وإصلاحها. لمزيد من المعلومات حول بيان الخصوصية، راجع [بيان خصوصية Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>الاحتياجات

- يمكن تشغيل محلل العميل على توزيعات مدعومة من [Linux](microsoft-defender-endpoint-linux.md#system-requirements) إما قبل أو بعد الإلحاق Microsoft Defender لنقطة النهاية.
- قم بتنزيل محلل العميل ل Linux من أحدث إصدار معاينة متوفر للتنزيل هنا: <https://aka.ms/XMDEClientAnalyzer>
- إذا كان جهازك خلف وكيل، يمكنك ببساطة تمرير الخادم الوكيل كمتغير بيئة إلى البرنامج النصي mde_support_tool.sh. على سبيل المثال: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>تشغيل محلل العميل على Linux

افتح محطة طرفية أو SSH في الجهاز ذي الصلة وقم بتشغيل الأوامر التالية:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. تشغيل كاستخدام غير جذر لتثبيت pip المطلوبة وlxml أي المكونات: `./mde_support_tool.sh`
6. لتجميع حزمة التشخيص الفعلية وإنشاء ملف أرشيف النتائج مرة أخرى كجذر: `./mde_support_tool.sh -d` مثال:

   ![صورة لمثال سطر الأوامر.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - يتطلب المحلل 'lxml' لإنتاج إخراج النتيجة. إذا لم يتم تثبيته، سيحاول المحلل إحضاره من المستودع الرسمي لحزم python أدناه: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - بالإضافة إلى ذلك، تتطلب الأداة حاليا تثبيت الإصدار 3 من Python أو إصدار أحدث.
>
> - إذا كنت تعمل على جهاز لا يمكنه استخدام Python 3 أو إحضار مكون lxml، يمكنك تنزيل إصدار ثنائي يستند إلى محلل لا يحتوي على أي من المتطلبات: [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>تعليمات بناء الجملة الإضافية:

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

### <a name="result-package-contents"></a>محتويات حزمة النتائج

- report.html

  الوصف: ملف إخراج HTML الرئيسي الذي سيحتوي على النتائج والإرشادات التي يمكن أن ينتجها البرنامج النصي للمحلل على الجهاز.

- mde_diagnostic.zip

  الوصف: نفس الإخراج التشخيصي الذي يتم إنشاؤه عند تشغيل *إنشاء تشخيص mdatp* على [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

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

- Auditd_info.txt

  الوصف: تفاصيل حول الخدمة التي تم تدقيقها والمكونات ذات الصلة لنظام التشغيل [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events)

- perf_benchmark.tar.gz

  الوصف: تقارير اختبار الأداء. لن ترى هذا إلا إذا كنت تستخدم معلمة الأداء.

> [!NOTE]
> في حالة استمرار مشكلة الأداء بعد اتباع الخطوات المذكورة أعلاه، يرجى الاتصال بدعم العملاء للحصول على مزيد من الإرشادات والتخفيف من المخاطر.



## <a name="see-also"></a>راجع أيضًا

- [التحقق من مشاكل صحة الوكيل](health-status.md)
