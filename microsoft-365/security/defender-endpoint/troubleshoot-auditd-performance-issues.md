---
title: استكشاف مشكلات أداء AuditD وإصلاحها باستخدام Microsoft Defender لنقطة النهاية على Linux
ms.reviewer: ''
description: يصف كيفية استكشاف مشكلات الأداء ذات الصلة AuditD وإصلاحها التي قد تواجهها مع Microsoft Defender ل Linux.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، استكشاف الأخطاء وإصلاحها، AuditD، XMDEClientAnalyzer، التثبيت، النشر، إزالة التثبيت
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
ms.openlocfilehash: 31aaf297fd3622eede2e1532ad60a20666d1bd07
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/19/2022
ms.locfileid: "66988230"
---
# <a name="troubleshoot-auditd-performance-issues-with-microsoft-defender-for-endpoint-on-linux"></a>استكشاف مشكلات أداء AuditD وإصلاحها باستخدام Microsoft Defender لنقطة النهاية على Linux 

توفر هذه المقالة إرشادات حول كيفية استكشاف مشكلات الأداء ذات الصلة AuditD وإصلاحها التي قد تواجهها مع Microsoft Defender لنقطة النهاية على Linux. 

**الخلفيه:** 

- يستخدم Microsoft Defender لنقطة النهاية على توزيعات نظام التشغيل Linux إطار عمل AuditD لجمع أنواع معينة من أحداث تتبع الاستخدام. 

- ستتم إضافة أحداث النظام التي تم تسجيلها بواسطة القواعد المضافة إلى `/etc/audit/rules.d/` audit.log (سجلات) وقد تؤثر على تدقيق المضيف ومجموعة المصدر.  

- سيتم وضع علامة على الأحداث التي تمت إضافتها بواسطة Microsoft Defender لنقطة النهاية على Linux باستخدام `mdatp` المفتاح. 

- إذا تم تكوين خدمة AuditD بشكل خاطئ أو دون اتصال، فقد تكون بعض الأحداث مفقودة. لاستكشاف مثل هذه المشكلة وإصلاحها، ارجع إلى: [استكشاف أخطاء الأحداث المفقودة أو التنبيهات وإصلاحها Microsoft Defender لنقطة النهاية على Linux.](linux-support-events.md)

في بعض أحمال عمل الخادم، قد تتم ملاحظة ملاحظتين: 

- **استهلاك كبير** لمورد CPU من **_عملية mdatp_audisp_plugin_** . 

- ***/var/log/audit/audit.log*** تصبح كبيرة أو تتناوب بشكل متكرر. 

قد تحدث هذه المشكلات على الخوادم التي تحتوي على العديد من الأحداث التي يتدفق فيها AuditD.  

يمكن أن يحدث هذا إذا كان هناك العديد من المستهلكين ل AuditD، أو العديد من القواعد مع الجمع بين Microsoft Defender لنقطة النهاية ومستهلكي الجهات الخارجية، أو حمل العمل العالي الذي يولد الكثير من الأحداث. 

لاستكشاف هذه المشكلات وإصلاحها، ابدأ [بجمع سجلات MDEClientAnalyzer](run-analyzer-macos-linux.md) على الخادم المتأثر النموذجي. 

> [!NOTE]
> وكأفضل ممارسة عامة، يوصى بتحديث [عامل Microsoft Defender لنقطة النهاية إلى أحدث إصدار متوفر](linux-whatsnew.md) وتأكيد استمرار المشكلة قبل إجراء مزيد من التحقيق.


## <a name="xmdeclientanalyzer"></a>XMDEClientAnalyzer 

عند استخدام XMDEClientAnalyzer، ستعرض الملفات التالية الإخراج الذي يوفر رؤى لمساعدتك على استكشاف المشكلات وإصلاحها.
- auditd_info.txt
- auditd_log_analysis.txt


### <a name="auditd_infotxt"></a>auditd_info.txt

يحتوي على تكوين AuditD عام وسيعرض:

- ما هي العمليات المسجلة كمستهلكي AuditD. 

- **إخراج Auditctl -s** مع **enabled=2**  

    - الاقتراحات التي تم تدقيقها في وضع غير قابل للتغيير (يتطلب إعادة التشغيل حتى يدخل أي تغييرات تكوين حيز التنفيذ). 

- **إخراج Auditctl -l**  

    - سوف تظهر القواعد التي يتم تحميلها حاليا في النواة (والتي قد تختلف عن ما هو موجود على القرص في "/etc/auditd/rules.d/mdatp.rules"). 
    
    - سوف تظهر القواعد ذات الصلة Microsoft Defender لنقطة النهاية. 
    
### <a name="auditd_log_analysistxt"></a>auditd_log_analysis.txt

يحتوي على معلومات مجمعة مهمة مفيدة عند التحقق من مشكلات أداء AuditD.  

- أي مكون يمتلك الأحداث الأكثر الإبلاغ عنها (سيتم وضع علامة على الأحداث Microsoft Defender لنقطة النهاية).`key=mdatp` 

- أهم البادئين لإعداد التقارير. 

- استدعاءات النظام الأكثر شيوعا (أحداث الشبكة أو نظام الملفات وغيرها). 

- ما هي مسارات نظام الملفات الأكثر سخونة. 

**للتخفيف من معظم مشكلات أداء AuditD، يمكنك تنفيذ استبعاد AuditD. **

> [!NOTE]
> وينبغي إجراء الاستثناءات فقط للبادئات أو المسارات ذات التهديد المنخفض والضوضاء العالية. على سبيل المثال، لا تستثني /bin/bash التي تخاطر بإنشاء نقطة مخفية كبيرة.
> [الأخطاء الشائعة التي يجب تجنبها عند تحديد الاستثناءات](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus).



## <a name="exclusion-types"></a>أنواع الاستبعاد 

تحتوي أداة دعم XMDEClientAnalyzer على بناء الجملة الذي يمكن استخدامه لإضافة قواعد تكوين استبعاد AuditD: 

استبعاد AuditD – تعليمات بناء جملة أداة الدعم:

:::image type="content" source="images/auditd-exclusion-support-tool-syntax-help.png" alt-text="بناء الجملة الذي يمكن استخدامه لإضافة قواعد تكوين استبعاد AuditD" lightbox="images/auditd-exclusion-support-tool-syntax-help.png":::

**بواسطة البادئ** 

- **-e/ -exe** full binary path > إزالة كافة الأحداث بواسطة هذا البادئ 

**حسب المسار** 

- **-d / -dir** المسار الكامل إلى دليل > إزالة أحداث نظام الملفات التي تستهدف هذا الدليل 

امثله: 

إذا كانت "`/opt/app/bin/app`" تكتب إلى "`/opt/app/cfg/logs/1234.log`"، يمكنك استخدام أداة الدعم لاستبعاد خيارات مختلفة: 

`-e /opt/app/bin/app`

`-d /opt/app/cfg`

`-x /usr/bin/python /etc/usercfg` 

`-d /usr/app/bin/`

أمثلة إضافية: 

`./mde_support_tool.sh exclude -p <process id>`

`./mde_support_tool.sh exclude -e <process name>`

لاستبعاد أكثر من عنصر واحد - قم بسلسلة الاستثناءات في سطر واحد: 

`./mde_support_tool.sh exclude -e <process name> -e <process name 2> -e <process name3>`
 
يتم استخدام علامة -x لاستبعاد الوصول إلى الدلائل الفرعية من قبل بادئين محددين على سبيل المثال: 

`./mde_support_tool.sh exclude -x /usr/sbin/mv /tmp`

سوف يستبعد ما سبق مراقبة المجلد الفرعي /tmp، عند الوصول إليها بواسطة عملية mv. 

 
> [!NOTE]
> يرجى الاتصال بدعم Microsoft إذا كنت بحاجة إلى مساعدة في تحليل مشكلات الأداء ذات الصلة بتدقيق التدقيق والتخفيف منها، أو مع نشر استثناءات AuditD على نطاق واسع. 


