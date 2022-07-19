---
title: تعرف على كيفية التخفيف من ثغرة Log4Shell الأمنية في Microsoft Defender لنقطة النهاية - إدارة المخاطر والثغرات الأمنية
description: تعرف على كيفية التخفيف من ثغرة Log4Shell الأمنية في Microsoft Defender لنقطة النهاية
keywords: tvm, lo4j
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365-initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6e265490eb5afee275debcdd1eb073f11bb845e3
ms.sourcegitcommit: 8101c12df67cfd9c15507b0133c23ce4cca1c6ba
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66857558"
---
# <a name="learn-how-to-manage-the-log4shell-vulnerability-in-microsoft-defender-for-endpoint"></a>تعرف على كيفية إدارة ثغرة Log4Shell الأمنية في Microsoft Defender لنقطة النهاية

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [إدارة المخاطر والثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

ثغرة Log4Shell الأمنية هي ثغرة أمنية لتنفيذ التعليمات البرمجية عن بعد (RCE) موجودة في مكتبة تسجيل Apache Log4j 2. نظرا لأن Apache Log4j 2 يستخدم بشكل شائع من قبل العديد من تطبيقات البرامج serviços online، فإنه يمثل وضعا معقدا وعالي المخاطر للشركات في جميع أنحاء العالم. يشار إليه باسم "Log4Shell" ([CVE-2021-44228](https://cve.mitre.org/cgi-bin/cvename.cgi?name=2021-44228)، [CVE-2021-45046](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046) ) إنه يقدم متجه هجوم جديدا يمكن للمهاجمين استغلاله لاستخراج البيانات ونشر برامج الفدية الضارة في مؤسسة.

> [!NOTE]
> راجع إرشادات المدونات [لمنع الثغرة الأمنية Log4j 2 واكتشافها والتتبع بحثا](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) [عنها للحصول على](https://msrc-blog.microsoft.com/2021/12/11/microsofts-response-to-cve-2021-44228-apache-log4j2/) إرشادات ومعلومات تقنية حول الثغرة الأمنية وتوصيات التخفيف الخاصة بالمنتج لحماية مؤسستك.

## <a name="overview-of-discovery-monitoring-and-mitigation-capabilities"></a>نظرة عامة على قدرات الاكتشاف والمراقبة والتخفيف

توفر لك إدارة المخاطر والثغرات الأمنية الإمكانات التالية لمساعدتك في تحديد التعرض التنظيمي للثغرة الأمنية Log4Shell ومراقبته والتخفيف من حدته:

- **الاكتشاف**: يستند الكشف عن الأجهزة المكشوفة، سواء Microsoft Defender لنقطة النهاية الأجهزة الملحقة أو الأجهزة التي تم اكتشافها ولكن لم يتم إلحاقها بعد، إلى البرامج المعرضة للخطر والملفات المعرضة للخطر التي تم اكتشافها على القرص.
- **الوعي بالتهديدات:** طريقة عرض موحدة لتقييم تعرض المؤسسة. تظهر طريقة العرض هذه تعرضك على مستوى الجهاز والبرامج، وتوفر الوصول إلى تفاصيل حول الملفات المعرضة للخطر مثل، آخر مرة تمت مشاهدتها فيها، وآخر مرة تم تنفيذها فيها، وآخر مرة تم تنفيذها باستخدام منافذ مفتوحة. يمكنك استخدام هذه المعلومات لتحديد أولويات إجراءات المعالجة. قد يستغرق ظهور البيانات المتعلقة بالأجهزة المكشوفة على لوحة المعلومات ما يصل إلى 24 ساعة.
- **خيارات التخفيف من المخاطر:** تطبيق خيارات التخفيف للمساعدة في تقليل مخاطر التعرض.
- **التتبع المتقدم:** استخدم التتبع المتقدم لإرجاع تفاصيل ملفات log4j المعرضة للخطر المحددة على القرص.

> [!NOTE]
> يتم دعم هذه القدرات على Windows 10 & Windows 11 وWindows Server وLinux وmacOS.
>
> يتطلب الدعم على Linux Microsoft Defender لنقطة النهاية إصدار عميل Linux 101.52.57 (30.121092.15257.0) أو إصدار أحدث.
>
> يتطلب الدعم على macOS Microsoft Defender لنقطة النهاية إصدار عميل macOS 20.121111.15416.0 أو إصدار أحدث.
>
>لمزيد من المعلومات حول الإصدارات المدعومة، راجع [الأنظمة الأساسية والإمكانيات لأنظمة التشغيل المدعومة](tvm-supported-os.md).

## <a name="exposed-devices-discovery"></a>اكتشاف الأجهزة المكشوفة

ستساعدك قدرات إدارة المخاطر والثغرات الأمنية المضمنة، جنبا إلى جنب مع تمكين الكشف عن Log4j، في مدخل Microsoft 365 Defender، على اكتشاف الأجهزة المعرضة للثغرة الأمنية Log4Shell.

يتم تقييم الأجهزة المضمنة باستخدام قدرات إدارة المخاطر والثغرات الأمنية المضمنة الموجودة التي يمكنها اكتشاف البرامج والملفات المعرضة للخطر.

للكشف عن الأجهزة المكتشفة ولكن لم يتم إلحاقها بعد، يجب تمكين الكشف عن Log4j. سيؤدي ذلك إلى بدء الفحوصات بنفس الطريقة التي يفحص بها اكتشاف الجهاز شبكتك بشكل نشط. يتضمن ذلك التحقق من نقاط النهاية المتعددة المضمنة (أجهزة Windows 10+ وWindows Server 2019+ ) والتحقق فقط داخل الشبكات الفرعية، للكشف عن الأجهزة المعرضة للخطر والمعرضة عن بعد ل CVE-2021-44228.

لتمكين الكشف عن Log4:

1. الانتقال إلى **إعداد** **اكتشاف جهاز** >  **الإعدادات** > 
2. حدد **تمكين الكشف عن Log4j2 (CVE-2021-44228)**
3. حدد **"حفظ"**

:::image type="content" source="images/enable_log4j.png" alt-text="الإعداد لتمكين الكشف عن log4j2" lightbox="images/enable_log4j.png":::

سيؤدي تشغيل هذه الفحوصات إلى تشغيل تدفق Log4j القياسي دون التسبب في أي تأثير ضار على الجهاز الذي يتم فحصه أو جهاز الفحص. يتم فحص نفسها عن طريق إرسال طلبات HTTP متعددة إلى الأجهزة المكتشفة، واستهداف منافذ تطبيقات الويب الشائعة (على سبيل المثال - 80,8000,8080,443,8443) وعناوين URL. يحتوي الطلب على رؤوس HTTP مع حمولة JNDI التي تشغل طلب DNS من الجهاز الذي تم فحصه.

على سبيل المثال، User-Agent: ${jndi:dns://192.168.1.3:5353/MDEDiscoveryUser-Agent} حيث 192.168.1.3 هو IP لجهاز التحقق.

> [!NOTE]
> تمكين الكشف عن Log4j2 يعني أيضا أن الأجهزة الملحقة ستستخدم التحقق الذاتي للكشف عن الثغرات الأمنية المحلية.

## <a name="vulnerable-software-and-files-detection"></a>الكشف عن البرامج والملفات المعرضة للخطر

توفر إدارة المخاطر والثغرات الأمنية طبقات من الكشف لمساعدتك على اكتشاف:

- **البرامج المعرضة للخطر**: يستند الاكتشاف إلى تعدادات النظام الأساسي الشائع للتطبيقات المثبتة (CPE) المعروفة بأنها عرضة لتنفيذ التعليمات البرمجية عن بعد Log4j.
- **الملفات المعرضة للخطر:** يتم تقييم كل من الملفات في الذاكرة والملفات في نظام الملفات. يمكن أن تكون هذه الملفات ملفات jar Log4j-core مع الإصدار الضعيف المعروف أو Uber-JAR الذي يحتوي على فئة بحث jndi ضعيفة أو ملف log4j-core ضعيف. على وجه التحديد، فإنه:

  - يحدد ما إذا كان ملف JAR يحتوي على ملف Log4j ضعيف من خلال فحص ملفات JAR والبحث عن الملف التالي:   \\META-INF\\maven\\org.apache.logging.log4j\\log4j-core\\pom.properties - إذا كان هذا الملف موجودا، تتم قراءة إصدار Log4j واستخراجه.
  - البحث عن ملف JndiLookup.class داخل ملف JAR من خلال البحث عن المسارات التي تحتوي على السلسلة "/log4j/core/lookup/JndiLookup.class" - إذا كان ملف الفئة JndiLookup.class موجودا، إدارة المخاطر والثغرات الأمنية يحدد ما إذا كان JAR يحتوي على ملف Log4j مع الإصدار المحدد في pom.properties.
  - البحث عن أي ملفات JAR ل Log4j-core ضعيفة مضمنة داخل JAR متداخلة عن طريق البحث عن المسارات التي تحتوي على أي من هذه السلاسل:
    - lib/log4j-core-
    - WEB-INF/lib/log4j-core-
    - App-INF/lib/log4j-core-

يصف هذا الجدول قدرات البحث في الأنظمة الأساسية والإصدارات المدعومة:

|القدره|نوع الملف|Windows10+،<br>server2019+|Server 2012R2،<br>server2016|Server 2008R2|Linux + macOS|
|:---|:---|:---|:---|:---|:---|
|البحث في الذاكرة  | Log4j-core | نعم |نعم<sup>[1]| - | نعم |
| |Uber-JARs | نعم |نعم<sup>[1]| - | نعم |
| البحث في كافة الملفات على القرص  |Log4j-core | نعم |نعم<sup>[1]| نعم | - |
| | Uber-JARs|نعم |نعم<sup>[1]| - | -|

(1) تتوفر الإمكانات عند تثبيت [KB5005292](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-update-for-edr-sensor-f8f69773-f17f-420f-91f4-a8e5167284ac) على Windows Server 2012 R2 و2016.

## <a name="learn-about-your-log4shell-exposure-and-mitigation-options"></a>تعرف على خيارات التعرض والتخفيف ل Log4Shell

### <a name="threat-and-vulnerability-management-dashboard"></a>لوحة معلومات إدارة المخاطر والثغرات الأمنية

استخدم لوحة معلومات إدارة المخاطر والثغرات الأمنية لمشاهدة التعرض الحالي.

1. في مدخل Microsoft 365 Defender، انتقل إلى **الوعي بتهديدات** **لوحة معلومات** >  **إدارة** >  الثغرات الأمنية: 
:::image type="content" source="images/awareness_dashboard.png" alt-text="عنصر واجهة مستخدم الوعي بالتهديدات على لوحة معلومات إدارة الثغرات الأمنية" lightbox="images/awareness_dashboard.png":::
2. حدد **عرض تفاصيل الثغرات الأمنية** للاطلاع على طريقة العرض المدمجة لتعرض المؤسسة.
:::image type="content" source="images/view_vulnerability_details.png" alt-text="صفحة تفاصيل الثغرات الأمنية ل CVE-2021-44228 (Log4j)" lightbox="images/view_vulnerability_details.png":::
3. اختر علامة التبويب ذات الصلة لرؤية تعرضك مقسما حسب:
    - الأجهزة المكشوفة – الإلحاق
    - الأجهزة المكشوفة – غير المجهزة
    - الملفات المعرضة للخطر
    - البرامج المعرضة للخطر

### <a name="log4shell-vulnerability-mitigation"></a>تخفيف الثغرة الأمنية Log4Shell

يمكن تخفيف ثغرة log4Shell الأمنية عن طريق منع عمليات بحث JNDI على إصدارات Log4j 2.10 - 2.14.1 مع التكوينات الافتراضية. لإنشاء إجراء التخفيف هذا، من **لوحة معلومات الوعي بالتهديدات**:

1. تحديد **عرض تفاصيل الثغرات الأمنية**
2. تحديد **خيارات التخفيف**

يمكنك اختيار تطبيق التخفيف على جميع الأجهزة المكشوفة أو تحديد أجهزة معينة تم إلحاقها. لإكمال العملية وتطبيق التخفيف على الأجهزة، حدد **"Create mitigation action**".

:::image type="content" source="images/mitigation_options.png" alt-text="خيارات التخفيف من المخاطر ل CVE-2021-44228" lightbox="images/mitigation_options.png":::

### <a name="mitigation-status"></a>حالة التخفيف

تشير حالة التخفيف إلى ما إذا كان قد تم تطبيق التخفيف من المخاطر البديلة لتعطيل عمليات بحث JDNI على الجهاز. يمكنك عرض حالة التخفيف لكل جهاز متأثر في علامات تبويب الأجهزة المكشوفة. يمكن أن يساعد هذا في تحديد أولويات التخفيف و/أو تصحيح الأجهزة استنادا إلى حالة التخفيف الخاصة بها.

:::image type="content" source="images/mitigation_status.png" alt-text="حالات التخفيف المحتملة" lightbox="/mitigation_status.png":::

يسرد الجدول أدناه حالات التخفيف المحتملة:

| حالة التخفيف | الوصف |
|:---|:---|
| تم تطبيق الحل البديل | _Windows_: تمت ملاحظة متغير بيئة LOG4J_FORMAT_MSG_NO_LOOKUPS قبل إعادة تشغيل الجهاز الأخير. <br/><br/> _Linux + macOS_: جميع العمليات قيد التشغيل لها LOG4J_FORMAT_MSG_NO_LOOKUPS=true في متغيرات البيئة الخاصة بها. |
| الحل البديل لإعادة التشغيل المعلقة | تم تعيين متغير البيئة LOG4J_FORMAT_MSG_NO_LOOKUPS، ولكن لم يتم الكشف عن إعادة التشغيل التالية. |
| غير مطبق | _Windows_: لم يتم ملاحظة متغير البيئة LOG4J_FORMAT_MSG_NO_LOOKUPS. <br/><br/> _Linux + macOS_: ليس لكل العمليات قيد التشغيل LOG4J_FORMAT_MSG_NO_LOOKUPS=true في متغيرات البيئة الخاصة بها، ولم يتم تطبيق إجراء التخفيف على الجهاز. |
| تم تخفيفه جزئيا | _Linux + macOS_: على الرغم من تطبيق إجراء التخفيف على الجهاز، فإن جميع العمليات قيد التشغيل ليس لها LOG4J_FORMAT_MSG_NO_LOOKUPS=true في متغيرات البيئة الخاصة بها. |
|غير قابل للتطبيق | الأجهزة التي تحتوي على ملفات عرضة للخطر غير موجودة في نطاق إصدار التخفيف. |
|غير معروف | تعذر تحديد حالة التخفيف في هذا الوقت. |

> [!NOTE]
> قد يستغرق الأمر بضع ساعات حتى تنعكس حالة التخفيف المحدثة للجهاز.

### <a name="revert-mitigations-applied-for-the-log4shell-vulnerability"></a>إرجاع عمليات التخفيف المطبقة على ثغرة Log4Shell الأمنية

في الحالات التي تحتاج فيها إلى العودة إلى التخفيف، اتبع الخطوات التالية:

**_لنظام التشغيل Windows:_**

1. فتح نافذة PowerShell غير مقيدة
2. قم بتنفيذ الأمر التالي:

 ```Powershell
   [Environment]::SetEnvironmentVariable("LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS", $null,[EnvironmentVariableTarget]::Machine)
```

سيدخل التغيير حيز التنفيذ بعد إعادة تشغيل الجهاز.

**_بالنسبة إلى Linux:_**

1. افتح الملف /etc/environment واحذف السطر LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS=true
2. حذف الملف /etc/systemd/system.conf.d/log4j\_تعطيل\_jndi\_lookups.conf
3. حذف الملف /etc/systemd/user.conf.d/log4j\_تعطيل\_jndi\_lookups.conf

سيدخل التغيير حيز التنفيذ بعد إعادة تشغيل الجهاز.

**_لنظام التشغيل macOS:_**

إزالة ملف setenv. LOG4J\_FORMAT\_MSG\_NO\_LOOKUPS.plist من المجلدات التالية:

- */Library/LaunchDaemons/*
- */Library/LaunchAgents/*
- */Users/\[username\]/Library/LaunchAgents/ - لجميع المستخدمين*

سيدخل التغيير حيز التنفيذ بعد إعادة تشغيل الجهاز.

### <a name="apache-log4j-security-recommendations"></a>توصيات أمان Apache Log4j

لمشاهدة توصية الأمان النشطة المتعلقة ب Apache log4j، حدد علامة تبويب **توصيات الأمان** من صفحة تفاصيل الثغرات الأمنية. في هذا المثال، إذا حددت **تحديث Apache Log4j** ، فسترى قائمة منبثقة أخرى مع مزيد من المعلومات:

:::image type="content" source="images/update_apache_log4j.png" alt-text="تحديث توصية أمان apache log4j" lightbox="images/update_apache_log4j.png":::

حدد **طلب المعالجة** لإنشاء طلب معالجة.

## <a name="explore-the-vulnerability-in-the-microsoft-365-defender-portal"></a>استكشاف الثغرات الأمنية في مدخل Microsoft 365 Defender

بمجرد العثور على الأجهزة والملفات والبرامج المكشوفة، سيتم أيضا نقل المعلومات ذات الصلة من خلال التجارب التالية في مدخل Microsoft 365 Defender:

### <a name="security-recommendations"></a>توصيات الأمان

ابحث عن **CVE-2021-44228** للاطلاع على توصيات الأمان التي تعالج ثغرة Log4Shell الأمنية:

:::image type="content" source="images/security_recommendations_log4j.png" alt-text="ثغرة log4j الأمنية في صفحة توصيات الأمان" lightbox="images/security_recommendations_log4j.png":::

### <a name="software-inventory"></a>بيانات البرامج

 في صفحة مخزون البرامج، ابحث عن **CVE-2021-44228** للاطلاع على تفاصيل حول عمليات تثبيت برامج Log4j والتعرض لها:

:::image type="content" source="images/software_inventory_log4j.png" alt-text="ثغرة log4j الأمنية على صفحة مخزون البرامج" lightbox="images/software_inventory_log4j.png":::

### <a name="weaknesses"></a>الضعف

في صفحة نقاط الضعف، ابحث عن **CVE-2021-44228** للاطلاع على معلومات حول ثغرة Log4Shell الأمنية:

:::image type="content" source="images/weaknesses_log4j.png" alt-text="ثغرة log4j الأمنية في صفحة نقاط الضعف" lightbox="images/weaknesses_log4j.png":::

## <a name="use-advanced-hunting"></a>استخدام التتبع المتقدم

يمكنك استخدام استعلام التتبع المتقدم التالي لتحديد الثغرات الأمنية في البرامج المثبتة على الأجهزة:

 ```text
    DeviceTvmSoftwareVulnerabilities
    | where CveId in ("CVE-2021-44228", "CVE-2021-45046")
 ```

يمكنك استخدام استعلام التتبع المتقدم التالي لتحديد الثغرات الأمنية في البرامج المثبتة على الأجهزة لعرض النتائج على مستوى الملف من القرص:

 ```text
    DeviceTvmSoftwareEvidenceBeta
    | mv-expand DiskPaths
    | where DiskPaths contains "log4j"
    | project DeviceId, SoftwareName, SoftwareVendor, SoftwareVersion, DiskPaths
 ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة على إدارة المخاطر والثغرات الأمنية](http://next-gen-threat-and-vuln-mgt.md)
- [توصيات الأمان](tvm-security-recommendation.md)
