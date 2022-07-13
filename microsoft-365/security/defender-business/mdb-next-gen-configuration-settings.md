---
title: فهم إعدادات تكوين الحماية من الجيل التالي في Microsoft Defender for Business
description: فهم إعدادات الحماية من الفيروسات والجيل التالي من الحماية في Defender for Business، وأمان نقطة النهاية للشركات الصغيرة والمتوسطة الحجم.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 69eea26df1f96b72ef66e53e46d679f40f0294b7
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772466"
---
# <a name="understand-next-generation-configuration-settings-in-microsoft-defender-for-business"></a>فهم إعدادات تكوين الجيل التالي في Microsoft Defender for Business

تتضمن حماية الجيل التالي في Defender for Business الحماية القوية من الفيروسات والحماية من البرامج الضارة. تم تصميم النهج الافتراضية لحماية أجهزتك والمستخدمين دون إعاقة الإنتاجية. يمكنك أيضا تخصيص النهج لتناسب احتياجات عملك. وإذا كنت تستخدم Microsoft Intune، يمكنك استخدام مركز إدارة Microsoft إدارة نقاط النهاية لإدارة نهج الأمان الخاصة بك.

**تصف هذه المقالة**:

- [إعدادات وخيارات الحماية من الجيل التالي](#next-generation-protection-settings-and-options)
- [إعدادات أخرى تم تكوينها مسبقا في Defender for Business](#other-preconfigured-settings-in-defender-for-business) 
- [الإعدادات الافتراضية ل Defender for Business Microsoft Intune](#defender-for-business-default-settings-and-microsoft-intune)

## <a name="next-generation-protection-settings-and-options"></a>إعدادات وخيارات الحماية من الجيل التالي

يسرد الجدول التالي الإعدادات والخيارات.

| اعداد | الوصف |
|:---|:---|
| **الحماية في الوقت الحقيقي**  |  |
| **تشغيل الحماية في الوقت الحقيقي** | تمكن الحماية في الوقت الحقيقي بشكل افتراضي من تحديد موقع البرامج الضارة وإيقاف تشغيلها على الأجهزة. *نوصي بالاحتفاظ بالحماية في الوقت الحقيقي قيد التشغيل.*<p>عند تشغيل الحماية في الوقت الحقيقي، فإنها تقوم بتكوين الإعدادات التالية:<ul><li>مراقبة السلوك قيد التشغيل ([AllowBehaviorMonitoring](/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)).</li><li>يتم مسح جميع الملفات والمرفقات التي تم تنزيلها ضوئيا ([AllowIOAVProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)).</li><li>يتم مسح البرامج النصية المستخدمة في مستعرضات Microsoft ضوئيا ([AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)).</li></ul>   |
| **حظر للوهلة الأولى** | تقوم الكتلة عند النظرة الأولى، التي تم تمكينها بشكل افتراضي، بحظر البرامج الضارة في غضون ثوان من الكشف، وزيادة الوقت (بالثوان) المسموح به لإرسال نماذج الملفات للتحليل، وتعيين مستوى الكشف إلى "عال". *نوصي بالاحتفاظ بالكتلة عند النظرة الأولى قيد التشغيل.*<p>عند تشغيل الحظر عند الوهلة الأولى، فإنه يقوم بتكوين الإعدادات التالية لبرنامج الحماية من الفيروسات من Microsoft Defender:<ul><li>يتم تعيين حظر الملفات المشبوهة وفحصها إلى مستوى الحظر العالي ([CloudBlockLevel](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)).</li><li>يتم تعيين عدد الثوان لملف ليتم حظره والتحقق منه إلى 50 ثانية ([CloudExtendedTimeout](/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout)).</li></ul> <p>**الهامه** إذا تم إيقاف تشغيل الحظر عند النظرة الأولى، فإنه يؤثر على `CloudBlockLevel` برنامج الحماية من الفيروسات من Microsoft Defender.`CloudExtendedTimeout`  |
| **تشغيل حماية الشبكة** | عند تشغيلها، تساعد حماية الشبكة على الحماية من رسائل التصيد الاحتيالي ومواقع استضافة الاستغلال والمحتوى الضار على الإنترنت. كما يمنع المستخدمين من إيقاف تشغيل حماية الشبكة.<p>يمكن تعيين حماية الشبكة إلى الأوضاع التالية:<ul><li>**وضع الحظر** هو الإعداد الافتراضي. يمنع المستخدمين من زيارة المواقع التي تعتبر غير آمنة. *نوصي بالاحتفاظ بحماية الشبكة معينة إلى وضع الحظر.*</li><li>يسمح **وضع التدقيق** للمستخدمين بزيارة المواقع التي قد تكون غير آمنة ويتعقب نشاط الشبكة من/إلى مثل هذه المواقع.</li><li>لا يمنع **الوضع المعطل** المستخدمين من زيارة المواقع التي قد تكون غير آمنة ولا يتعقب نشاط الشبكة من/إلى مثل هذه المواقع.</li></ul> |
| **الاصلاح**  |  |
| **إجراء اتخاذه على التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA)** | يمكن أن يتضمن PUA برامج إعلانية؛ تجميع البرامج التي تقدم لتثبيت برامج أخرى غير موقعة؛ وبرامج التجنب التي تحاول التطفل على ميزات الأمان. على الرغم من أن PUA ليس بالضرورة فيروسا أو برامج ضارة أو أي نوع آخر من التهديدات، فإنه يمكن أن يؤثر على أداء الجهاز.<p>تمنع حماية PUA العناصر التي تم اكتشافها ك PUA. يمكنك تعيين حماية PUA إلى ما يلي:<ul><li>**التمكين** هو الإعداد الافتراضي. يحظر العناصر التي تم اكتشافها ك PUA على الأجهزة. *نوصي بتمكين حماية PUA.*</li><li>لا يتخذ **وضع التدقيق** أي إجراء على العناصر التي تم اكتشافها ك PUA.</li><li>لا يكشف **المعطل** عن العناصر التي قد تكون PUA أو يتخذ إجراء بشأنها.</li></ul> |
| **المسح الضوئي**   |  |
| **نوع الفحص المجدول** | ضع في اعتبارك تشغيل فحص مكافحة الفيروسات الأسبوعي على أجهزتك. يمكنك الاختيار من بين خيارات نوع الفحص التالية:<ul><li>يتحقق **Quickscan** من المواقع، مثل مفاتيح التسجيل ومجلدات بدء التشغيل، حيث يمكن تسجيل البرامج الضارة للبدء مع الجهاز. *نوصي باستخدام خيار quickscan.*</li><li>**يتحقق Fullscan** من كافة الملفات والمجلدات على جهاز.</li><li>**يعني التعطيل** أنه لن يتم إجراء عمليات فحص مجدولة. لا يزال بإمكان المستخدمين تشغيل عمليات المسح الضوئي على أجهزتهم الخاصة. (بشكل عام، لا نوصي بتعطيل عمليات الفحص المجدولة.)</li></ul><p> [تعرف على المزيد حول أنواع الفحص](../defender-endpoint/schedule-antivirus-scans.md). |
| **يوم من الأسبوع لتشغيل فحص مجدول** | حدد يوما لتشغيل عمليات فحص مكافحة الفيروسات العادية والأسبوعية. |
| **وقت اليوم لتشغيل فحص مجدول** | حدد وقتا لتشغيل عمليات فحص مكافحة الفيروسات المجدولة بانتظام لتشغيلها. |
| **استخدام أداء منخفض** | هذا الإعداد متوقف عن التشغيل بشكل افتراضي. *نوصي بإيقاف تشغيل هذا الإعداد.* ومع ذلك، يمكنك تشغيل هذا الإعداد للحد من ذاكرة الجهاز والموارد المستخدمة أثناء عمليات الفحص المجدولة. <p>**الهامه** إذا قمت بتشغيل **"استخدام أداء منخفض**"، فإنه يقوم بتكوين الإعدادات التالية لبرنامج الحماية من الفيروسات من Microsoft Defender:<ul><li>لا يتم مسح ملفات الأرشيف ضوئيا ([AllowArchiveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)).</li><li>يتم تعيين أولوية CPU منخفضة للمسح الضوئي ([EnableLowCPUPriority](/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority)).</li><li>إذا لم يتم فحص برنامج الحماية من الفيروسات بالكامل، فلن يتم تشغيل أي فحص للمتابعة ([DisableCatchupFullScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupfullscan)).</li><li>إذا لم يتم فحص برنامج الحماية من الفيروسات بسرعة، فلن يتم تشغيل أي فحص للحاق بالركب ([DisableCatchupQuickScan](/windows/client-management/mdm/policy-csp-defender#defender-disablecatchupquickscan)).</li><li>يقلل من متوسط عامل تحميل CPU أثناء فحص مكافحة الفيروسات من 50 بالمائة إلى 20 بالمائة ([AvgCPULoadFactor](/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor)).</li></ul> |
| **تجربة المستخدم**   |  |
| **السماح للمستخدمين بالوصول إلى تطبيق أمن Windows** | قم بتشغيل هذا الإعداد لتمكين المستخدمين من فتح تطبيق أمن Windows على أجهزتهم. لن يتمكن المستخدمون من تجاوز الإعدادات التي تقوم بتكوينها في Defender for Business، لكنهم سيتمكنون من تشغيل فحص سريع أو عرض أي تهديدات تم اكتشافها. |
| **استثناءات برنامج الحماية من الفيروسات** | الاستثناءات هي العمليات أو الملفات أو المجلدات التي تم تخطيها بواسطة عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender. *بشكل عام، يجب ألا تحتاج إلى تحديد الاستثناءات.* يتضمن برنامج الحماية من الفيروسات من Microsoft Defender العديد من الاستثناءات التلقائية التي تستند إلى سلوك نظام التشغيل المعروف وملفات الإدارة النموذجية.<p>[تعرف على المزيد حول الاستثناءات](../defender-endpoint/configure-exclusions-microsoft-defender-antivirus.md). |
| **استثناءات العملية** | تمنع استثناءات العملية فحص الملفات التي يتم فتحها بواسطة عمليات معينة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <p>[تعرف على المزيد حول استثناءات العمليات](../defender-endpoint/configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). |
| **استثناءات ملحق الملف** | تمنع استثناءات ملحق الملف فحص الملفات ذات الملحقات المحددة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender.<p>[تعرف على المزيد حول استثناءات ملحق الملف](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md). |
| **استثناءات الملفات والمجلدات** | تمنع استثناءات الملفات والمجلدات فحص الملفات الموجودة في مجلدات معينة بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <p>[تعرف على المزيد حول استثناءات الملفات والمجلدات](../defender-endpoint/configure-extension-file-exclusions-microsoft-defender-antivirus.md). |

## <a name="other-preconfigured-settings-in-defender-for-business"></a>إعدادات أخرى تم تكوينها مسبقا في Defender for Business

تم تكوين إعدادات الأمان التالية مسبقا في Defender for Business:

- يتم تشغيل المسح الضوئي لمحركات الأقراص القابلة للإزالة ([AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)).
- لا تحتوي عمليات الفحص السريع اليومية على وقت محدد مسبقا ([ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)).
- يتم التحقق من تحديثات معلومات الأمان قبل تشغيل فحص مكافحة الفيروسات ([CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan)).
- تحدث عمليات التحقق من معلومات الأمان كل أربع ساعات ([SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)).

## <a name="defender-for-business-default-settings-and-microsoft-intune"></a>الإعدادات الافتراضية ل Defender for Business Microsoft Intune

يصف الجدول التالي الإعدادات التي تم تكوينها مسبقا ل Defender for Business وكيف تتوافق هذه الإعدادات مع ما قد تراه في Intune (تتم إدارته في مركز إدارة Microsoft إدارة نقاط النهاية). إذا كنت تستخدم [عملية التكوين المبسطة في Defender for Business](mdb-simplified-configuration.md)، فلن تحتاج إلى تحرير هذه الإعدادات.

| اعداد  | الوصف  |
|---------|---------|
| [حماية السحابة](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)     | في بعض الأحيان يشار إليها باسم الحماية المقدمة من السحابة أو خدمة الحماية المتقدمة من Microsoft (MAPS)، تعمل الحماية السحابية مع Microsoft Defender Antivirus وسحابة Microsoft لتحديد التهديدات الجديدة، وأحيانا حتى قبل تأثر جهاز واحد. بشكل افتراضي، يتم تشغيل [AllowCloudProtection](/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) . <p>[تعرف على المزيد حول حماية السحابة](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md).         |
| [مراقبة الملفات الواردة والصادرة](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)     | لمراقبة الملفات الواردة والصادرة، تم تعيين [RealTimeScanDirection](/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection) لمراقبة جميع الملفات.         |
| [فحص ملفات الشبكة](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) | بشكل افتراضي، لا يتم تمكين [AllowScanningNetworkFiles](/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) ، ولا يتم مسح ملفات الشبكة ضوئيا. |
| [مسح رسائل البريد الإلكتروني ضوئيا](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) | بشكل افتراضي، لا يتم تمكين [AllowEmailScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) ، ولا يتم مسح رسائل البريد الإلكتروني ضوئيا. |
| [عدد الأيام (0-90) للحفاظ على البرامج الضارة المعزولة](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) | بشكل افتراضي، يتم تعيين إعداد [DaysToRetainCleanedMalware](/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) إلى صفر (0) أيام. لا تتم إزالة البيانات الاصطناعية الموجودة في العزل تلقائيا.  |
| [إرسال موافقة العينات](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) | بشكل افتراضي، يتم تعيين [SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) لإرسال عينات آمنة تلقائيا. تتضمن `.bat`أمثلة العينات الآمنة والملفات `.dll``.scr`والملفات `.exe` التي لا تحتوي على معلومات تعريف شخصية (PII). إذا كان الملف يحتوي على PII، يتلقى المستخدم طلبا للسماح لنموذج الإرسال بالمتابعة.<p>[تعرف على المزيد حول حماية السحابة وعينة الإرسال](../defender-endpoint/cloud-protection-microsoft-antivirus-sample-submission.md). |
| [مسح محركات الأقراص القابلة للإزالة ضوئيا](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) | بشكل افتراضي، يتم تكوين [AllowFullScanRemovableDriveScanning](/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) لمسح محركات الأقراص القابلة للإزالة، مثل محركات أقراص USB الإبهام على الأجهزة.<p>[تعرف على المزيد حول إعدادات نهج مكافحة البرامج الضارة](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#list-of-antimalware-policy-settings).   |
| [تشغيل وقت الفحص السريع اليومي](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) | بشكل افتراضي، يتم تعيين [ScheduleQuickScanTime](/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) إلى 2:00 ص.<p>[تعرف على المزيد حول إعدادات الفحص](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).   |
| [التحقق من وجود تحديثات التوقيع قبل تشغيل الفحص](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) | بشكل افتراضي، يتم تكوين [CheckForSignaturesBeforeRunningScan](/windows/client-management/mdm/policy-csp-defender#defender-checkforsignaturesbeforerunningscan) للتحقق من تحديثات معلومات الأمان قبل تشغيل عمليات مسح الحماية من الفيروسات/الحماية من البرامج الضارة.<p>[تعرف على المزيد حول إعدادات الفحص](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [وتحديثات معلومات الأمان](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates).   |
| [كم مرة (0-24 ساعة) للتحقق من وجود تحديثات التحليل الذكي للأمان](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) | بشكل افتراضي، يتم تكوين [SignatureUpdateInterval](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) للتحقق من وجود تحديثات التحليل الذكي للأمان كل أربع ساعات.<p>[تعرف على المزيد حول إعدادات الفحص](/mem/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings) [وتحديثات معلومات الأمان](../defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus.md#security-intelligence-updates). |


## <a name="next-steps"></a>الخطوات التالية

- [عرض الحوادث وإدارتها في Defender for Business](mdb-view-manage-incidents.md)
- [الاستجابة للتهديدات وتخفيفها في Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)


## <a name="see-also"></a>راجع أيضًا

- [تفضّل بزيارة مدخل Microsoft 365 Defender](mdb-get-started.md)
- [إدارة إعدادات جدار الحماية في Defender for Business](mdb-custom-rules-firewall.md)
- [نهج موفر الخدمات المشتركة ( CSP ) - Defender](/windows/client-management/mdm/policy-csp-defender)
