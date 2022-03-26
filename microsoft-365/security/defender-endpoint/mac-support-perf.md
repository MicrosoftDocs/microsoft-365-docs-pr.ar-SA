---
title: استكشاف مشاكل الأداء وإصلاحها ل Microsoft Defender ل Endpoint على macOS
description: استكشاف مشاكل الأداء وإصلاحها في Microsoft Defender ل Endpoint على macOS.
keywords: microsoft، defender، Microsoft Defender for Endpoint، mac، الأداء
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
ms.openlocfilehash: 1d39bd46afae270fc7ac2a9fab8b5f4a2b4aaeb2
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63573265"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشاكل الأداء وإصلاحها ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md)
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يوفر هذا الموضوع بعض الخطوات العامة التي يمكن استخدامها لتضييق نطاق مشاكل الأداء المتعلقة ب Microsoft Defender ل Endpoint على macOS.

الحماية في الوقت الحقيقي (RTP) هي ميزة من ميزات Microsoft Defender ل Endpoint على macOS تقوم بمراقبة جهازك وحمايته بشكل مستمر من التهديدات. وهي تتكون من مراقبة الملفات وعملية وغيرها من الأسلوبات الاورستاتية.

استنادا إلى التطبيقات التي تقوم بتشغيلها وخصائص جهازك، قد تواجه أداء دون المستوى الأمثل عند تشغيل Microsoft Defender ل Endpoint على macOS. بشكل خاص، يمكن للتطبيقات أو عمليات النظام التي يمكنها الوصول إلى العديد من الموارد خلال فترة زمنية قصيرة أن تؤدي إلى مشاكل في الأداء في Microsoft Defender ل Endpoint على macOS.

يمكن استخدام الخطوات التالية في استكشاف الأخطاء وإصلاحها وتخفيف هذه المشاكل:

1. قم بتعطيل الحماية في الوقت الحقيقي باستخدام أحد الأساليب التالية ولاحظ ما إذا كان الأداء يتحسن أم لا. يساعد هذا النهج على تضييق ما إذا كان Microsoft Defender ل Endpoint على macOS يساهم في مشاكل الأداء.

      إذا لم تكن مؤسستك تدير جهازك، يمكن تعطيل الحماية في الوقت الحقيقي باستخدام أحد الخيارات التالية:

    - من واجهة المستخدم. افتح Microsoft Defender ل Endpoint على macOS وانتقل إلى **إدارة الإعدادات**.

      ![إدارة لقطة شاشة للحماية في الوقت الحقيقي.](images/mdatp-36-rtp.png)

    - من المحطة الطرفية. لأغراض الأمان، تتطلب هذه العملية رفعا.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      إذا كانت مؤسستك تدير جهازك، يمكن للمسؤول تعطيل الحماية في الوقت الحقيقي باستخدام الإرشادات الواردة في [تعيين تفضيلات ل Microsoft Defender ل Endpoint على macOS](mac-preferences.md).

      إذا استمرت مشكلة الأداء أثناء إيقاف تشغيل الحماية في الوقت الحقيقي، فمن الممكن أن يكون مصدر المشكلة هو الكشف عن تهديدات نقاط النهاية والرد عليها الأساسي. في هذه الحالة، يرجى الاتصال بدعم العملاء للحصول على مزيد من الإرشادات وتخفيف الأثر.

2. افتح "البحث" وانتقل إلى **أدوات مساعدة** \> **التطبيقات**. افتح **مراقب النشاط** وتحلل التطبيقات التي تستخدم الموارد على النظام. تتضمن الأمثلة النموذجية برامج تحديث البرامج وبرامج التحويل البرمجي.

3. للعثور على التطبيقات التي تقوم بتشغيل معظم عمليات الفحص، يمكنك استخدام إحصائيات الوقت الحقيقي التي يجمعها Defender for Endpoint على Mac.

      > [!NOTE]
      > تتوفر هذه الميزة في الإصدار 100.90.70 أو الإصدارات الأحدث.
      يتم تمكين هذه الميزة بشكل افتراضي على **قنوات Dogfood** و **InsiderFast** . إذا كنت تستخدم قناة تحديث مختلفة، يمكن تمكين هذه الميزة من سطر الأوامر:

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      تتطلب هذه الميزة تمكين الحماية في الوقت الحقيقي. للتحقق من حالة الحماية في الوقت الحقيقي، قم بتشغيل الأمر التالي:

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    تحقق من صحة **real_time_protection_enabled** الإدخال. بخلاف ذلك، يمكنك تشغيل الأمر التالي لتمكينه:

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      لجمع الإحصائيات الحالية، تشغيل:

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > يضمن **استخدام --output json** (ملاحظة الشرطة المزدوجة) أن تنسيق الإخراج جاهز للتقيس.
      سيعرض إخراج هذا الأمر جميع العمليات ونشاط الفحص المقترن بها.

4. على نظام Mac، قم بتنزيل عينة تحليل Python high_cpu_parser.py باستخدام الأمر:

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    يجب أن يكون إخراج هذا الأمر مماثلا للمخرجات التالية:

    ```Output
    --2020-11-14 11:27:27-- https://raw.githubusercontent.com/microsoft.
    mdatp-xplat/master/linus/diagnostic/high_cpu_parser.py
    Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.xxx.xxx
    Connecting to raw.githubusercontent.com (raw.githubusercontent.com)| 151.101.xxx.xxx| :443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 1020 [text/plain]
    Saving to: 'high_cpu_parser.py'
    100%[===========================================>] 1,020    --.-K/s   in
    0s
    ```

5. بعد ذلك، اكتب الأوامر التالية:

      ```bash
        chmod +x high_cpu_parser.py
      ```

      ```bash
        cat real_time_protection.json | python high_cpu_parser.py  > real_time_protection.log
      ```

      إخراج ما سبق هو قائمة من أهم المساهمين في مشاكل الأداء. العمود الأول هو معرف العملية (PID)، العمود الثاني هو اسم عملية te، العمود الأخير هو عدد الملفات الممسوحة ضوئيا، التي تم فرزها حسب التأثير.

      على سبيل المثال، سيكون إخراج الأمر مثل ما يلي:

      ```output
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

      لتحسين أداء Defender for Endpoint على Mac، حدد موقع الرقم الأعلى ضمن الصف إجمالي الملفات الممسوحة ضوئيا وأضف استثناء له. لمزيد من المعلومات، راجع تكوين الاستثناءات ل [Defender for Endpoint على Linux والتحقق من صحتها](linux-exclusions.md).

      > [!NOTE]
      > يخزن التطبيق الإحصائيات في الذاكرة ويتعقب نشاط الملف فقط منذ بدء العمل عليه وتمكين الحماية في الوقت الحقيقي. لا يتم حساب العمليات التي تم تشغيلها قبل فترات إيقاف تشغيل الحماية في الوقت الحقيقي أو أثناءها. بالإضافة إلى ذلك، يتم حساب الأحداث التي تم تشغيل عمليات الفحص فيها فقط.
      >
6. قم بتكوين Microsoft Defender ل Endpoint على macOS مع استثناءات للعمليات أو مواقع الأقراص التي تساهم في مشاكل الأداء وتتمكن من إعادة تمكين الحماية في الوقت الحقيقي.

     راجع [تكوين الاستثناءات ل Microsoft Defender ل Endpoint على macOS](mac-exclusions.md) والتحقق من صحتها للحصول على التفاصيل.
