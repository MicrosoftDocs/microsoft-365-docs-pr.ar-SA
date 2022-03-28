---
title: فهم إعدادات تكوين حماية الجيل التالي في Microsoft Defender for Business
description: فهم إعدادات التكوين لحماية الجيل التالي في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 263d6457c8e913bdd3d8224af71f201156e24b5a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575943"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>فهم إعدادات تكوين الجيل التالي في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

تتضمن حماية الجيل التالي في Defender for Business الحماية من الفيروسات والحماية من البرامج الضارة. تم تصميم سياساتك الافتراضية لحماية أجهزتك والمستخدمين دون إعاقة الإنتاجية؛ ومع ذلك، يمكنك أيضا تخصيص سياساتك لتتناسب مع احتياجات عملك. وإذا كنت تستخدم إدارة نقاط النهاية من Microsoft، يمكنك استخدام ذلك لإدارة سياسات الأمان.

**تصف هذه المقالة**:

- [إعدادات وخيارات حماية الجيل التالي](#next-generation-protection-settings-and-options)

- [إعدادات أخرى تم تكوينها مسبقا في Defender for Business](#other-preconfigured-settings-in-defender-for-business) 

- [الإعدادات الافتراضية ل Defender for Business إدارة نقاط النهاية من Microsoft](#defender-for-business-default-settings-and-microsoft-endpoint-manager)

## <a name="next-generation-protection-settings-and-options"></a>إعدادات وخيارات حماية الجيل التالي

يسرد الجدول التالي الإعدادات والخيارات:<br/><br/>

| الإعداد | الوصف |
|:---|:---|
| **الحماية في الوقت الحقيقي**  |  |
| **تشغيل الحماية في الوقت الحقيقي** | يتم تمكين الحماية في الوقت الحقيقي بشكل افتراضي لتحديد موقع البرامج الضارة وتوقف تشغيلها على الأجهزة. *نوصي بإبقاء الحماية في الوقت الحقيقي في وضع تشغيل.*<br/><br/>عند تشغيل الحماية في الوقت الحقيقي، يتم تكوين الإعدادات التالية:<br/>- يتم تشغيل مراقبة السلوك ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring))<br/>- يتم فحص جميع الملفات والمرفقات التي تم تنزيلها ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection))<br/>- يتم فحص البرامج النصية المستخدمة في مستعرضات Microsoft ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning))   |
| **الحظر من النظرة الأولى** | إذا تم تمكين هذا الخيار بشكل افتراضي، فحظر البرامج الضارة للنظرة الأولى في غضون ثوان من الكشف، وزيادة الوقت (بالثواني) المسموح بإرسال نماذج الملفات لتحليلها، بالإضافة إلى تعيين مستوى الكشف إلى عال. *نوصيك بإبقاء الحظر عند أول نظرة في وضع تشغيل.*<br/><br/>عند تشغيل الحظر من النظرة الأولى، فإنه يتم تكوين الإعدادات التالية برنامج الحماية من الفيروسات من Microsoft Defender: <br/>- يتم تعيين حظر الملفات المريبة وفحصها إلى مستوى الحظر العالي ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel))<br/>- يتم تعيين عدد الثواني للملف الذي سيتم حظره وفحصه إلى 50 ثانية ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)) <br/><br/>**هام**: إذا تم إيقاف تشغيل الحظر من النظرة الأولى، فإنه يؤثر `CloudBlockLevel` `CloudExtendedTimeout` على برنامج الحماية من الفيروسات من Microsoft Defender.  |
| **تشغيل حماية الشبكة** | عند تشغيلها، تساعد حماية الشبكة على الحماية من رسائل التصيد الاحتيالي ومواقع الاستضافة المستغلة والمحتوى الضار على الإنترنت. كما يمنع المستخدمين من إيقاف تشغيل حماية الشبكة.<br/><br/>يمكن تعيين حماية الشبكة إلى أحد الأوضاع التالية:<br/>- **وضع الحظر** (هذا الإعداد هو الإعداد الافتراضي)، الذي يمنع المستخدمين من زيارة المواقع التي تعتبر غير آمنة. *نوصي بإبقاء حماية الشبكة مع تعيينها إلى وضع الحظر.*<br/>- **وضع التدقيق**، الذي يسمح للمستخدمين بزيارة المواقع التي قد تكون غير آمنة ويتعقب نشاط الشبكة إلى/من هذه المواقع <br/>- **الوضع "معطل"**، الذي يمنع المستخدمين من زيارة المواقع التي قد تكون غير آمنة ولا يتعقب نشاط الشبكة إلى/من هذه المواقع |
| **المعالجة**  |  |
| **الإجراء المطلوب اتخاذه على التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA)** | يمكن أن تتضمن PUA برامج إعلانية وبرامج تجميع تعرض تثبيت برامج أخرى غير موقعة وبرامج التجنب التي تحاول التجنب من ميزات الأمان. على الرغم من أن PUA ليس بالضرورة فيروسا أو برامج ضارة أو أي نوع آخر من التهديدات، يمكن أن يؤثر PUA على أداء الجهاز.<br/><br/>تمنع الحماية PUA العناصر التي يتم الكشف عنها ك PUA. يمكنك تعيين حماية PUA إلى أحد الإعدادات التالية: <br/>- **ممكن** (هذا الإعداد هو الإعداد الافتراضي)، الذي يمنع العناصر التي تم الكشف عنها ك PUA على الأجهزة. *نوصي بإبقاء حماية PUA ممكنة.*<br/>- **وضع التدقيق**، الذي لا يتخذ أي إجراء على العناصر التي تم الكشف عنها ك PUA <br/>- **معطل**، لا يكشف عن العناصر التي قد تكون PUA أو يتخذ إجراء بشأنها |
| **المسح الضوئي**   |  |
| **نوع الفحص المجدول** | فكر في تشغيل فحص برنامج الحماية من الفيروسات أسبوعيا على أجهزتك. يمكنك الاختيار من بين خيارات نوع الفحص التالية: <br/>- **تحقق Quickscan** من المواقع، مثل مفاتيح التسجيل ومجلدات بدء التشغيل، حيث يمكن تسجيل البرامج الضارة للبدء بجهاز. *نوصي باستخدام خيار quickscan.* <br/>- **يتحقق Fullscan** من كل الملفات والمجلدات على جهاز <br/>- **معطل** يعني أنه لن يتم إجراء عمليات فحص مجدولة. لا يزال بإمكان المستخدمين تشغيل عمليات الفحص على أجهزتهم الخاصة. (بشكل عام، لا نوصي بتعطيل عمليات الفحص المجدولة.) <br/><br/> [تعرف على المزيد حول أنواع الفحص](../defender-endpoint/schedule-antivirus-scans.md). |
| **يوم من الأسبوع لتشغيل فحص مجدول** | حدد يوما لتشغيل عمليات فحص الفيروسات الأسبوعية العادية. |
| **وقت اليوم لتشغيل فحص مجدول** | حدد وقتا لتشغيل عمليات فحص برامج الحماية من الفيروسات المجدولة بانتظام لتشغيلها. |
| **استخدام أداء منخفض** | يتم إيقاف تشغيل هذا الإعداد بشكل افتراضي. *نوصي بإبقاء هذا الإعداد م إيقاف التشغيل.* ومع ذلك، يمكنك تشغيل هذا الإعداد للحد من ذاكرة الجهاز والموارد المستخدمة أثناء عمليات الفحص المجدولة. <br/><br/>**هام** إذا قمت ب **تشغيل استخدام الأداء** المنخفض، فإنه يتم تكوين الإعدادات التالية برنامج الحماية من الفيروسات من Microsoft Defender: <br/>- لا يتم فحص ملفات الأرشيف ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning))<br/>- يتم تعيين أولوية منخفضة لوحدة المعالجة المركزية ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)) <br/>- إذا فاتتك عملية فحص كاملة لمكافحة الفيروسات، لن يتم تشغيل أي فحص للحاق ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)) <br/>- إذا فاتتك عملية فحص سريعة لمكافحة الفيروسات، لن يتم تشغيل أي فحص للحاق ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)) <br/>- تقليل متوسط عامل تحميل CPU أثناء فحص برنامج الحماية من الفيروسات من 50٪ إلى 20٪ ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)) |
| **تجربة المستخدم**   |  |
| **السماح للمستخدمين بالوصول إلى أمن Windows التطبيق** | قم تشغيل هذا الإعداد لتمكين المستخدمين من فتح أمن Windows على أجهزتهم. لن يتمكن المستخدمون من تجاوز الإعدادات التي تقوم بتكوينها في Microsoft Defender for Business، ولكن سيكون بمقدورهم تشغيل فحص سريع إذا لزم الأمر، أو عرض أي تهديدات تم اكتشافها. |
| **استثناءات برنامج الحماية من الفيروسات** | الاستثناءات هي العمليات أو الملفات أو المجلدات التي يتم تخطيها برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. *بشكل عام، يجب ألا تحتاج إلى تعريف الاستثناءات.* برنامج الحماية من الفيروسات من Microsoft Defender العديد من الاستثناءات التلقائية التي تستند إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية.<br/><br/>[معرفة المزيد حول الاستثناءات](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md) |
| **استثناءات العملية** | تمنع استثناءات العمليات فحص الملفات التي يتم فتحها بواسطة عمليات معينة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <br/><br/>[معرفة المزيد حول استثناءات العملية](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md) |
| **استثناءات ملحقات الملفات** | تمنع استثناءات ملحقات الملفات فحص الملفات ذات الملحقات المعينة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.<br/><br/>[تعرف على المزيد حول استثناءات ملحقات الملفات](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |
| **استثناءات الملفات والمجلدات** | تمنع استثناءات الملفات والمجلدات فحص الملفات الموجودة في مجلدات معينة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <br/><br/>[معرفة المزيد حول استثناءات الملفات والمجلدات](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md) |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>إعدادات أخرى تم تكوينها مسبقا في Defender for Business

تم تكوين إعدادات الأمان التالية مسبقا في Defender for Business:

- يتم تشغيل المسح الضوئي لمحركات الأقراص القابلة للإزالة ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning))

- لا يوجد وقت محدد مسبقا للمسح السريع اليومي ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime))

- يتم التحقق من تحديثات معلومات الأمان قبل تشغيل فحص الحماية من الفيروسات ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan))

- يتم فحص معلومات الأمان كل أربع ساعات ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval))

## <a name="defender-for-business-default-settings-and-microsoft-endpoint-manager"></a>الإعدادات الافتراضية ل Defender for Business إدارة نقاط النهاية من Microsoft

يصف الجدول التالي الإعدادات التي تم تكوينها مسبقا ل Defender for Business وكيفية توافق هذه الإعدادات مع ما قد تراه في إدارة نقاط النهاية من Microsoft (أو Microsoft Intune). إذا كنت تستخدم عملية التكوين المبسطة في [Defender for Business](mdb-simplified-configuration.md) (معاينة)، فلا تحتاج إلى تحرير هذه الإعدادات.
<br/><br/>

| الإعداد  | الوصف  |
|---------|---------|
| [الحماية السحابية](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | تعمل الحماية السحابية التي يشار إليها أحيانا بالحماية التي يتم توفيرها من السحابة أو خدمة الحماية المتقدمة من Microsoft (MAPS) مع برنامج الحماية من الفيروسات من Microsoft Defender وسحابة Microsoft لتحديد التهديدات الجديدة، في بعض الأحيان حتى قبل تأثر جهاز واحد. بشكل افتراضي، [يتم تشغيل AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) . <br/><br/>[تعرف على المزيد حول الحماية السحابية](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [مراقبة الملفات الواردة وال الصادرة](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | لمراقبة الملفات الواردة وال الصادرة، [يتم تعيين RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) لمراقبة كل الملفات.         |
| [فحص ملفات الشبكة](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | بشكل افتراضي [، لا يتم تمكين AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) ، ولا يتم فحص ملفات الشبكة. |
| [مسح رسائل البريد الإلكتروني ضوئيا](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | بشكل افتراضي [، لا يتم تمكين AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) ، ولا يتم فحص رسائل البريد الإلكتروني. |
| [عدد الأيام (0-90) لإبقاء البرامج الضارة المعزولة](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | بشكل افتراضي، [يتم تعيين DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) هذا الإعداد إلى صفر (0) أيام. لا تتم إزالة التحف التي في الفحص تلقائيا.  |
| [الموافقة على إرسال عينات](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | بشكل افتراضي، [تكون SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) et لإرسال عينات آمنة تلقائيا. تتضمن أمثلة العينات الآمنة `.bat`ملفات و `.scr``.dll``.exe` لا تحتوي على معلومات تعريف شخصية (PII). إذا احتوى ملف على PII، يتلقى المستخدم طلبا للسماح لنموذج الإرسال بالمتابعة.<br/><br/>[تعرف على المزيد حول الحماية السحابية ونموذج الإرسال](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md) |
| [فحص محركات الأقراص القابلة للإزالة](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | بشكل افتراضي، [يتم تكوين AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) لمسح محركات الأقراص القابلة للإزالة، مثل محركات أقراص USB المصغرة على الأجهزة.<br/><br/>[تعرف على المزيد حول إعدادات نهج مكافحة البرامج الضارة](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings)   |
| [تشغيل وقت الفحص السريع اليومي](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | بشكل افتراضي، [يتم تعيين ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) إلى 2:00 صباحا.<br/><br/>[تعرف على المزيد حول إعدادات الفحص](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [التحقق من وجود تحديثات للتوقيع قبل تشغيل الفحص](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | بشكل افتراضي، يتم تكوين [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) للتحقق من وجود تحديثات لذكاء الأمان قبل تشغيل عمليات فحص برامج الحماية من الفيروسات/مكافحة البرامج الضارة.<br/><br/>[تعرف على المزيد حول إعدادات الفحص](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [وتحديثات معلومات الأمان](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [عدد المرات (من 0 إلى 24 ساعة) للتحقق من تحديثات معلومات الأمان](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | بشكل افتراضي، [يتم تكوين SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) للتحقق من وجود تحديثات لذكاء الأمان كل أربع ساعات.<br/><br/>[تعرف على المزيد حول إعدادات الفحص](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [وتحديثات معلومات الأمان](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>الخطوات التالية

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)


## <a name="see-also"></a>راجع أيضًا

- [زيارة مدخل Microsoft 365 Defender](mdb-get-started.md)

- [إدارة إعدادات جدار الحماية في Microsoft Defender for Business](mdb-custom-rules-firewall.md)

- [نهج CSP - Defender](/windows/client-management/mdm/policy-csp-defender)