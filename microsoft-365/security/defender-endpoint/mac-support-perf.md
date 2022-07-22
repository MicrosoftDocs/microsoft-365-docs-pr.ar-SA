---
title: استكشاف مشكلات الأداء وإصلاحها Microsoft Defender لنقطة النهاية على macOS
description: استكشاف مشكلات الأداء وإصلاحها في Microsoft Defender لنقطة النهاية على macOS.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، الأداء
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
ms.openlocfilehash: 7c60a61ca1a0a1179abd27c0f6d59970a0c09866
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969520"
---
# <a name="troubleshoot-performance-issues-for-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشكلات الأداء وإصلاحها Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يوفر هذا الموضوع بعض الخطوات العامة التي يمكن استخدامها لتضييق مشكلات الأداء المتعلقة Microsoft Defender لنقطة النهاية على macOS.

الحماية في الوقت الحقيقي (RTP) هي ميزة من ميزات Microsoft Defender لنقطة النهاية على macOS الذي يراقب ويحمي جهازك باستمرار من التهديدات. وهو يتكون من مراقبة الملفات والعمليات وغيرها من الأساليب الاستباقية.

اعتمادا على التطبيقات التي تقوم بتشغيلها وخصائص جهازك، قد تواجه أداء دون المستوى الأمثل عند تشغيل Microsoft Defender لنقطة النهاية على macOS. على وجه الخصوص، يمكن للتطبيقات أو عمليات النظام التي تصل إلى العديد من الموارد على مدى فترة زمنية قصيرة أن تؤدي إلى مشكلات في الأداء في Microsoft Defender لنقطة النهاية على macOS.

يمكن استخدام الخطوات التالية لاستكشاف الأخطاء وإصلاحها والتخفيف من حدة هذه المشكلات:

1. تعطيل الحماية في الوقت الحقيقي باستخدام أحد الأساليب التالية ومراقبة ما إذا كان الأداء يتحسن. يساعد هذا النهج على تضييق نطاق ما إذا كان Microsoft Defender لنقطة النهاية على macOS يساهم في مشكلات الأداء.

      إذا لم تكن مؤسستك تدير جهازك، يمكن تعطيل الحماية في الوقت الحقيقي باستخدام أحد الخيارات التالية:

    - من واجهة المستخدم. افتح Microsoft Defender لنقطة النهاية على macOS وانتقل إلى **"إدارة الإعدادات**".

      :::image type="content" source="images/mdatp-36-rtp.png" alt-text=" صفحة إدارة الحماية في الوقت الحقيقي" lightbox="images/mdatp-36-rtp.png":::
      

    - من المحطة الطرفية. لأغراض أمنية، تتطلب هذه العملية رفع المستوى.

      ```bash
      mdatp config real-time-protection --value disabled
      ```

      إذا كانت مؤسستك تدير جهازك، يمكن تعطيل الحماية في الوقت الحقيقي من قبل المسؤول باستخدام الإرشادات الواردة في [تعيين التفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md).

      إذا استمرت مشكلة الأداء أثناء إيقاف تشغيل الحماية في الوقت الحقيقي، فقد يكون أصل المشكلة هو مكون الكشف عن نقطة النهاية والاستجابة. في هذه الحالة، يرجى الاتصال بدعم العملاء للحصول على مزيد من الإرشادات والتخفيف من المخاطر.

2. افتح "الباحث" وانتقل إلى **"أدوات مساعدة التطبيقات**\>". افتح **Activity Monitor** وحلل التطبيقات التي تستخدم الموارد على النظام الخاص بك. تتضمن الأمثلة النموذجية برامج تحديث البرامج والمحولات البرمجية.

3. للعثور على التطبيقات التي تقوم بتشغيل معظم عمليات الفحص، يمكنك استخدام الإحصائيات في الوقت الحقيقي التي جمعها Defender لنقطة النهاية على Mac.

      > [!NOTE]
      > تتوفر هذه الميزة في الإصدار 100.90.70 أو أحدث.
      يتم تمكين هذه الميزة بشكل افتراضي على قناتين **Dogfood** و **InsiderFast** . إذا كنت تستخدم قناة تحديث مختلفة، يمكن تمكين هذه الميزة من سطر الأوامر:

      ```bash
      mdatp config real-time-protection-statistics  --value enabled
      ```

      تتطلب هذه الميزة تمكين الحماية في الوقت الحقيقي. للتحقق من حالة الحماية في الوقت الحقيقي، قم بتشغيل الأمر التالي:

      ```bash
      mdatp health --field real_time_protection_enabled
      ```

    تحقق من صحة إدخال **real_time_protection_enabled** . وإلا، فشغل الأمر التالي لتمكينه:

      ```bash
      mdatp config real-time-protection --value enabled
      ```

      ```output
      Configuration property updated
      ```

      لجمع الإحصائيات الحالية، قم بتشغيل:

      ```bash
      mdatp diagnostic real-time-protection-statistics --output json > real_time_protection.json
      ```

      > [!NOTE]
      > يضمن استخدام **--output json** (لاحظ الشرطة المزدوجة) أن تنسيق الإخراج جاهز لتحليله.
      سيعرض إخراج هذا الأمر جميع العمليات ونشاط الفحص المقترن بها.

4. على نظام Mac، قم بتنزيل نموذج محلل Python high_cpu_parser.py باستخدام الأمر:

    ```bash
    curl -O https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/linux/diagnostic/high_cpu_parser.py
    ```

    يجب أن يكون إخراج هذا الأمر مشابها لما يلي:

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

      إخراج ما سبق هو قائمة بأفضل المساهمين في مشكلات الأداء. العمود الأول هو معرف العملية (PID)، والعمود الثاني هو اسم العملية te، والعمود الأخير هو عدد الملفات الممسوحة ضوئيا، والتي تم فرزها حسب التأثير.

      على سبيل المثال، سيكون إخراج الأمر شيئا مثل ما يلي:

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

      لتحسين أداء Defender لنقطة النهاية على Mac، حدد موقع الملف الذي يحتوي على أعلى رقم ضمن صف إجمالي الملفات الممسوحة ضوئيا وأضف استثناء له. لمزيد من المعلومات، راجع [تكوين الاستثناءات والتحقق من صحتها ل Defender لنقطة النهاية على macOS](mac-exclusions.md).

      > [!NOTE]
      > يخزن التطبيق الإحصائيات في الذاكرة ويتعقب نشاط الملف فقط منذ بدئه وتم تمكين الحماية في الوقت الحقيقي. لا يتم حساب العمليات التي تم تشغيلها قبل أو خلال الفترات التي كانت فيها الحماية في الوقت الحقيقي متوقفة عن التشغيل. بالإضافة إلى ذلك، يتم حساب الأحداث التي قامت بتشغيل عمليات الفحص فقط.
      >
6. تكوين Microsoft Defender لنقطة النهاية على macOS مع استثناءات للعمليات أو مواقع القرص التي تساهم في مشكلات الأداء وإعادة تمكين الحماية في الوقت الحقيقي.

     راجع [تكوين الاستثناءات والتحقق من صحتها Microsoft Defender لنقطة النهاية على macOS للحصول على](mac-exclusions.md) التفاصيل.
