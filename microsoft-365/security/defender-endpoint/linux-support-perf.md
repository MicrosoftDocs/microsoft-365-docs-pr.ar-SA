---
title: استكشاف مشاكل الأداء وإصلاحها ل Microsoft Defender ل Endpoint على Linux
description: استكشاف مشاكل الأداء وإصلاحها في Microsoft Defender ل Endpoint على Linux.
keywords: microsoft، defender، Microsoft Defender for Endpoint، linux، الأداء
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
ms.openlocfilehash: 14424f0cdff908fc641d6de1c22d25546473cc13
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570624"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-linux"></a>استكشاف مشاكل الأداء وإصلاحها ل Microsoft Defender ل Endpoint على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يوفر هذا المستند إرشادات حول كيفية تضييق مشاكل الأداء المتعلقة ب Defender for Endpoint على Linux باستخدام أدوات التشخيص المتوفرة لكي تتمكن من فهم الحد من مشاكل الموارد الموجودة والعمليات التي تجعل النظام في مثل هذه الحالات. تحدث مشاكل الأداء بشكل أساسي بسبب المشاكل في نظام فرعي واحد أو أكثر من الأجهزة، استنادا إلى ملف تعريف استخدام الموارد على النظام. في بعض الأحيان تكون التطبيقات حساسة للموارد I/O للقرص وقد تحتاج إلى سعة أكبر لوحدة المعالجة المركزية (CPU) وفي بعض الأحيان تكون بعض التكوينات غير ممكنة الاستدامة، وقد تؤدي إلى تشغيل عدد كبير جدا من العمليات الجديدة وفتح عدد كبير جدا من واصفات الملفات.

استنادا إلى التطبيقات التي تقوم بتشغيلها وخصائص جهازك، قد تواجه أداء دون المستوى الأمثل عند تشغيل Defender for Endpoint على Linux. بشكل خاص، يمكن للتطبيقات أو عمليات النظام التي يمكنها الوصول إلى العديد من الموارد مثل CPU والقرص والذاكرة خلال فترة زمنية قصيرة أن تؤدي إلى مشاكل الأداء في Defender for Endpoint على Linux.

> [!WARNING]
> قبل البدء، **يرجى التأكد من أن منتجات** الأمان الأخرى لا تعمل حاليا على الجهاز. قد تتضارب منتجات الأمان المتعددة مع أداء المضيف وقد تؤثر عليه.

## <a name="troubleshoot-performance-issues-using-real-time-protection-statistics"></a>استكشاف مشاكل الأداء وإصلاحها باستخدام إحصائيات الحماية في الوقت الحقيقي

**ينطبق على:**
- مشاكل الأداء المرتبطة بال AV فقط

الحماية في الوقت الحقيقي (RTP) هي ميزة من ميزات Defender for Endpoint على Linux التي تراقب جهازك وتحميه بشكل مستمر من التهديدات. وهي تتكون من مراقبة الملفات وعملية وغيرها من الأسلوبات الاورستاتية.

يمكن استخدام الخطوات التالية في استكشاف الأخطاء وإصلاحها وتخفيف هذه المشاكل:

1. قم بتعطيل الحماية في الوقت الحقيقي باستخدام أحد الأساليب التالية ولاحظ ما إذا كان الأداء يتحسن أم لا. يساعد هذا النهج على تضييق ما إذا كان Defender for Endpoint على Linux يساهم في مشاكل الأداء.

    إذا لم تكن مؤسستك تدير جهازك، يمكن تعطيل الحماية في الوقت الحقيقي من سطر الأوامر:

    ```bash
    mdatp config real-time-protection --value disabled
    ```

    ```Output
    Configuration property updated
    ```

    إذا كانت مؤسستك تدير جهازك، يمكن للمسؤول تعطيل الحماية في الوقت الحقيقي باستخدام الإرشادات الواردة في تعيين تفضيلات [ل Defender for Endpoint على Linux](linux-preferences.md).

    > [!NOTE]
    > إذا استمرت مشكلة الأداء أثناء إيقاف تشغيل الحماية في الوقت الحقيقي، فمن الممكن أن يكون مصدر المشكلة هو مكون الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية). في هذه الحالة، يرجى اتباع الخطوات من القسم استكشاف مشاكل الأداء وإصلاحها باستخدام **Microsoft Defender for Endpoint Client Analyzer** من هذه المقالة.

2. للعثور على التطبيقات التي تقوم بتشغيل معظم عمليات الفحص، يمكنك استخدام إحصائيات الوقت الحقيقي التي يجمعها Defender for Endpoint على Linux.

    > [!NOTE]
    > تتوفر هذه الميزة في الإصدار 100.90.70 أو الإصدارات الأحدث.

    يتم تمكين هذه الميزة بشكل افتراضي على `Dogfood` القنوات و `InsiderFast` . إذا كنت تستخدم قناة تحديث مختلفة، يمكن تمكين هذه الميزة من سطر الأوامر:

    ```bash
    mdatp config real-time-protection-statistics --value enabled
    ```

    تتطلب هذه الميزة تمكين الحماية في الوقت الحقيقي. للتحقق من حالة الحماية في الوقت الحقيقي، قم بتشغيل الأمر التالي:

    ```bash
    mdatp health --field real_time_protection_enabled
    ```

    تحقق من أن `real_time_protection_enabled` الإدخال هو `true`. بخلاف ذلك، يمكنك تشغيل الأمر التالي لتمكينه:

    ```bash
    mdatp config real-time-protection --value enabled
    ```

    ```Output
    Configuration property updated
    ```

    لجمع الإحصائيات الحالية، تشغيل:

    ```bash
    mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
    ```

    > [!NOTE]
    > يضمن ```--output json``` استخدام (ملاحظة الشرطة المزدوجة) أن تنسيق الإخراج جاهز للتقشير.

    سيعرض إخراج هذا الأمر جميع العمليات ونشاط الفحص المقترن بها.

3. على نظام Linux، قم بتنزيل عينة تحليل Python **high_cpu_parser.py** باستخدام الأمر:

    ```bash
    wget -c https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    يجب أن يكون إخراج هذا الأمر مماثلا للمخرجات التالية:


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

      إخراج ما سبق هو قائمة من أهم المساهمين في مشاكل الأداء. العمود الأول هو معرف العملية (PID)، العمود الثاني هو اسم العملية، العمود الأخير هو عدد الملفات الممسوحة ضوئيا، التي تم فرزها حسب التأثير.
    على سبيل المثال، سيكون إخراج الأمر مثل ما يلي: 

    ```Output
    ... > python ~/repo/mdatp-xplat/linux/diagnostic/high_cpu_parser.py <~Downloads/output.json | head -n 10
    27432 None 76703
    73467 actool     1249
    73914 xcodebuild 1081
    73873 bash 1050
    27475 None 836
    1    launchd    407
    73468 ibtool     344
    549  telemetryd_v1   325
    4764 None 228
    125  CrashPlanService 164
    ```

    لتحسين أداء Defender for Endpoint على Linux `Total files scanned` ، حدد موقع الرقم الذي به أعلى رقم أسفل الصف وأضف استثناء له. لمزيد من المعلومات، راجع تكوين الاستثناءات ل [Defender for Endpoint على Linux والتحقق من صحتها](linux-exclusions.md).

    > [!NOTE]
    > يخزن التطبيق الإحصائيات في الذاكرة ويتعقب نشاط الملف فقط منذ بدء العمل عليه وتمكين الحماية في الوقت الحقيقي. لا يتم حساب العمليات التي تم تشغيلها قبل فترات إيقاف تشغيل الحماية في الوقت الحقيقي أو أثناءها. بالإضافة إلى ذلك، يتم حساب الأحداث التي تم تشغيل عمليات الفحص فيها فقط.

5. قم بتكوين Microsoft Defender ل Endpoint على Linux مع استثناءات للعمليات أو مواقع الأقراص التي تساهم في مشاكل الأداء وتتمكن من إعادة تمكين الحماية في الوقت الحقيقي.

    للمزيد من المعلومات، راجع [تكوين الاستثناءات والتحقق من صحتها في Microsoft Defender لنقطة النهاية على Linux](linux-exclusions.md).

## <a name="troubleshoot-performance-issues-using-microsoft-defender-for-endpoint-client-analyzer"></a>استكشاف مشاكل الأداء وإصلاحها باستخدام Microsoft Defender ل "محلل عميل نقطة النهاية"

**ينطبق على:**
- مشاكل الأداء لكل مكونات Defender لنقطة النهاية المتوفرة مثل AV الكشف التلقائي والاستجابة على النقط النهائية  

يمكن لمحلل عميل Microsoft Defender لنقطة النهاية (MDECA) تجميع التتبعات والسجلات والمعلومات التشخيصية من أجل استكشاف مشاكل الأداء وإصلاحها على الأجهزة المجهزة على Linux.[](/microsoft-365/security/defender-endpoint/onboard-configure)

> [!NOTE]
> يتم استخدام أداة محلل عميل Microsoft Defender for Endpoint بشكل منتظم بواسطة Microsoft Customer Support Services (CSS) لجمع معلومات مثل (على سبيل المثال لا يقتصر على) عناوين IP وأسماء الكمبيوتر الشخصي التي ستساعدك على استكشاف المشاكل التي قد تواجهها مع Microsoft Defender ل Endpoint وإصلاحها. لمزيد من المعلومات حول بيان الخصوصية، راجع [بيان خصوصية Microsoft](https://privacy.microsoft.com/privacystatement).

### <a name="requirements"></a>المتطلبات

- يمكن أن يتم تشغيل محلل العميل على الدواوين المدعمة ل [Linux](microsoft-defender-endpoint-linux.md#system-requirements) إما قبل أو بعد التكديس في Microsoft Defender ل Endpoint.
- قم بتنزيل محلل العملاء ل Linux من إصدار المعاينة الأخير المتوفر للتنزيل هنا: <https://aka.ms/XMDEClientAnalyzer>
- إذا كان جهازك خلف وكيل، يمكنك ببساطة تمرير الخادم الوكيل كمتغير بيئة إلى البرنامج النصي mde_support_tool.sh. على سبيل المثال: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

### <a name="run-the-client-analyzer-on-linux"></a>تشغيل محلل العملاء على Linux

افتح محطة أو SSH في الجهاز ذي الصلة وتولى تشغيل الأوامر التالية:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`
2. `unzip -q XMDEClientAnalyzer.zip`
3. `cd XMDEClientAnalyzer`
4. `chmod +x mde_support_tool.sh`
5. قم بتشغيلها ك الاستخدام غير الجذر لتثبيت المكونين pip و lxml المطلوبين: `./mde_support_tool.sh`
6. لتجميع الحزمة التشخيصية الفعلية وإنشاء ملف أرشيف النتائج مرة أخرى كحزمة الجذر: مثال: `./mde_support_tool.sh -d`

   ![صورة لمثال سطر الأوامر.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

> [!NOTE]
> - يتطلب المحلل 'lxml' للحصول على إخراج النتيجة. إذا لم يكن مثبتا، سيحاول المحلل إحضاره من المستودع الرسمي لحزم python أدناه: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - بالإضافة إلى ذلك، تتطلب الأداة حاليا تثبيت إصدار Python 3 أو إصدار أحدث.
>
> - إذا كنت تعمل على جهاز لا يمكنه استخدام Python 3 أو إحضار مكون lxml، يمكنك تنزيل إصدار ثنائي يستند إلى محلل لا يحتاج إلى أي من المتطلبات: [XMDE Client Analyzer Binary](https://aka.ms/XMDEClientAnalyzerBinary)

### <a name="additional-syntax-help"></a>تعليمات بناء الجملة الإضافية:

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

### <a name="result-package-contents"></a>محتويات حزمة النتائج

- report.html

  الوصف: ملف إخراج HTML الرئيسي الذي سيحتوي على النتائج والإرشادات التي يمكن أن ينتجها البرنامج النصي للمحلل على الجهاز.

- mde_diagnostic.zip

  الوصف: نفس الإخراج التشخيصي الذي يتم إنشاؤه عند تشغيل *إنشاء تشخيص mdatp* على [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  الوصف: إخراج XML الذي يتم إنشاؤه أثناء التشغيل ويستخدم لإنشاء ملف تقرير html.

- Processes_information.txt

  الوصف: يحتوي على تفاصيل تشغيل عمليات Microsoft Defender لنقطة النهاية ذات الصلة على النظام.

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

> [!NOTE]
> في حالة استمرار مشكلة الأداء بعد اتباع الخطوات المذكورة أعلاه، يرجى الاتصال ب دعم العملاء للحصول على مزيد من الإرشادات وتخفيف المخاطر.



## <a name="see-also"></a>راجع أيضًا

- [التحقق من مشاكل صحة الوكيل](health-status.md)
