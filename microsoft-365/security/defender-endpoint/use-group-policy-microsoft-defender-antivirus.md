---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة
description: تعرف على كيفية استخدام نهج المجموعة لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية في Microsoft Defender لنقطة النهاية.
keywords: نهج المجموعة، عنصر نهج المجموعة، التكوين، الإعدادات
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/04/2022
ms.reviewer: ksarens, jtoole, pahuijbr
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 53b24f0566b9b9d43ad725a832bb1e0fa8013923
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416365"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدام إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يمكنك استخدام [نهج المجموعة](/windows/win32/srvnodes/group-policy) لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender على نقاط النهاية.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة

بشكل عام، يمكنك استخدام الإجراء التالي لتكوين إعدادات نهج المجموعة برنامج الحماية من الفيروسات من Microsoft Defender أو تغييرها:

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))، وانقر بزر الماوس الأيمن فوق عنصر نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **"تحرير**".

2. باستخدام **محرر إدارة نهج المجموعة** انتقل إلى **تكوين الكمبيوتر**.

3. انقر فوق **القوالب الإدارية**.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender**.

5. قم بتوسيع المقطع (يشار إليه باسم **الموقع** في الجدول في هذا الموضوع) الذي يحتوي على الإعداد الذي تريد تكوينه، وانقر نقرا مزدوجا فوق الإعداد لفتحه، وأدخل تغييرات على التكوين.

6. [نشر عنصر نهج المجموعة المحدث كما تفعل عادة](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>نهج المجموعة الإعدادات والموارد

يسرد الجدول التالي إعدادات نهج المجموعة شائعة الاستخدام المتوفرة في Windows 10.

> [!TIP]
> قم بتنزيل جدول بيانات مرجعي نهج المجموعة، الذي يسرد إعدادات النهج لتكوينات الكمبيوتر والمستخدم المضمنة في ملفات القالب الإداري التي تم تسليمها مع Windows. يمكنك تكوين الإشارة إلى جدول البيانات عند تحرير نهج المجموعة العناصر. <br/><br/> فيما يلي أحدث الإصدارات:
> - [جدول بيانات مرجعي نهج المجموعة الإعدادات لتحديث Windows 10 مايو 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [جدول بيانات مرجعي نهج المجموعة الإعدادات لتحديث Windows 11 أكتوبر 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|موقع|اعداد|مقالة|
|---|---|---|
|واجهة العميل|تمكين وضع واجهة المستخدم بلا رأس|[منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|واجهة العميل|عرض نص إضافي للعملاء عندما يحتاجون إلى تنفيذ إجراء|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)|
|واجهة العميل|منع كافة الإعلامات|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)|
|واجهة العميل|منع إعلامات إعادة التشغيل|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)|
|الاستثناءات|استثناءات الامتداد|[تكوين الاستثناءات والتحقق من صحتها في عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|الاستثناءات|استثناءات المسار|[تكوين الاستثناءات والتحقق من صحتها في عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|الاستثناءات|استثناءات العملية|[تكوين الاستثناءات والتحقق من صحتها في عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|الاستثناءات|إيقاف تشغيل الاستثناءات التلقائية|[تكوين الاستثناءات والتحقق من صحتها في عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)|
|خرائط|تكوين ميزة "الحظر عند النظرة الأولى"|[تمكين الكتلة من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|خرائط|الانضمام إلى Microsoft MAPS|[تمكين الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)|
|خرائط|إرسال نماذج الملفات عند الحاجة إلى مزيد من التحليل|[تمكين الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)|
|خرائط|تكوين تجاوز الإعداد المحلي لإعداد التقارير إلى Microsoft MAPS|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|تكوين فحص سحابي موسع|[تكوين الفترة الزمنية لحظر السحابة](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|تحديد مستوى حماية السحابة|[تحديد مستوى الحماية المقدمة من السحابة](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|نظام فحص الشبكة|تحديد مجموعات تعريف إضافية لفحص نسبة استخدام الشبكة| غير مستخدم (مهمل) |
|نظام فحص الشبكة|تشغيل إيقاف التعريف| غير مستخدم (مهمل)|
|نظام فحص الشبكة|تشغيل التعرف على البروتوكول| غير مستخدم (مهمل)|
|العزل|تكوين تجاوز الإعداد المحلي لإزالة العناصر من مجلد العزل|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|العزل|تكوين إزالة العناصر من مجلد العزل|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمراقبة نشاط الملفات والبرامج على الكمبيوتر|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمراقبة نشاط الملفات الواردة والصادرة|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمسح كافة الملفات والمرفقات التي تم تنزيلها|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لتشغيل مراقبة السلوك|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعدادات المحلية لتشغيل الحماية في الوقت الحقيقي|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تحديد الحد الأقصى لحجم الملفات والمرفقات التي تم تنزيلها ليتم مسحها ضوئيا|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|مراقبة نشاط الملفات والبرامج على الكمبيوتر|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|فحص كافة الملفات والمرفقات التي تم تنزيلها|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|إيقاف تشغيل الحماية في الوقت الحقيقي|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تشغيل مراقبة السلوك|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تشغيل فحص العمليات كلما تم تمكين الحماية في الوقت الحقيقي|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تشغيل إعلامات الكتابة المجمعة البسيطة|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين المراقبة للملفات الواردة والصادرة ونشاط البرنامج|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الاصلاح|تكوين تجاوز الإعداد المحلي لوقت اليوم لتشغيل فحص كامل مجدول لإكمال المعالجة|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الاصلاح|حدد يوم الأسبوع لتشغيل فحص كامل مجدول لإكمال المعالجة|[تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|الاصلاح|تحديد وقت اليوم لتشغيل فحص كامل مجدول لإكمال المعالجة|[تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender المجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|إعداد التقارير|إيقاف تشغيل الإعلامات المحسنة|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
|الجذر|إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender|غير مستخدم. إذا كنت تستخدم منتج الحماية من الفيروسات غير التابع ل Microsoft أو تخطط لاستخدامه، فراجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md).|
|الجذر|تعريف العناوين لتجاوز الخادم الوكيل|[تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|الجذر|تعريف التكوين التلقائي للوكيل (.pac) للاتصال بالشبكة|[تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|الجذر|تعريف الخادم الوكيل للاتصال بالشبكة|[تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|الجذر|تكوين سلوك دمج المسؤول المحلي للقوائم|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الجذر|السماح لخدمة مكافحة البرامج الضارة بالبدء بالأولوية العادية|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|الجذر|السماح ببقاء خدمة مكافحة البرامج الضارة قيد التشغيل دائما|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|الجذر|إيقاف تشغيل المعالجة الروتينية|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|الجذر|تحديد أوقات المهام المجدولة عشوائيا|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|السماح للمستخدمين بإيقاف الفحص مؤقتا|[منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md) (غير معتمدة في Windows 10)|
|المسح الضوئي|التحقق من أحدث تعريفات الفيروسات وبرامج التجسس قبل تشغيل فحص مجدول|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد عدد الأيام التي يتم بعدها فرض الفحص الإلحاقي|[إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل اللحاق بالمسح الضوئي الكامل|[إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل اللحاق بالمسح الضوئي السريع|[إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي للحد الأقصى للنسبة المئوية لاستخدام وحدة المعالجة المركزية|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي ليوم فحص الجدول|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي لوقت الفحص السريع المجدول|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي لوقت الفحص المجدول|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي لنوع الفحص لاستخدامه لإجراء فحص مجدول|[منع المستخدمين أو السماح لهم بتعديل إعدادات النهج محليا](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|إنشاء نقطة استعادة النظام|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل إزالة العناصر من مجلد محفوظات الفحص|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل الأساليب الاستعلاماتية|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة الدائمة وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل فحص البريد الإلكتروني|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل المسح الضوئي لنقطة إعادة الفرز|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل الفحص الكامل على محركات أقراص الشبكة المعينة|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|فحص ملفات الأرشيف|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|فحص ملفات الشبكة|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|مسح الملفات التنفيذية المحزمة|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| المسح الضوئي | مسح البرامج النصية | [تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>راجع أيضا [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|المسح الضوئي|مسح محركات الأقراص القابلة للإزالة ضوئيا|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الحد الأقصى للعمق لمسح ملفات الأرشيف|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد النسبة المئوية القصوى لاستخدام وحدة المعالجة المركزية أثناء الفحص|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الحد الأقصى لحجم ملفات الأرشيف التي سيتم مسحها ضوئيا|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد يوم الأسبوع لتشغيل فحص مجدول|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الفاصل الزمني لتشغيل عمليات الفحص السريعة في اليوم|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد نوع الفحص لاستخدامه لإجراء فحص مجدول|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد وقت الفحص السريع اليومي|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد وقت اليوم لتشغيل فحص مجدول|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|بدء الفحص المجدول فقط عندما يكون الكمبيوتر قيد التشغيل ولكن ليس قيد الاستخدام|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|السماح بتحديثات التحليل الذكي للأمان من Microsoft Update|[إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|السماح بتحديثات التحليل الذكي للأمان عند التشغيل على طاقة البطارية|[إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|السماح للإعلامات بتعطيل التقارير المستندة إلى التعريفات إلى Microsoft MAPS|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|السماح بتحديثات التحليل الذكي للأمان في الوقت الحقيقي استنادا إلى التقارير إلى Microsoft MAPS|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|التحقق من أحدث تعريفات الفيروسات وبرامج التجسس عند بدء التشغيل|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد مشاركات الملفات لتنزيل تحديثات معلومات الأمان|[إدارة تحديثات معلومات الأمان وحماية برنامج الحماية من الفيروسات من Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد عدد الأيام التي بعدها يلزم تحديث معلومات الأمان|[إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد عدد الأيام قبل اعتبار تعريفات برامج التجسس قديمة|[إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد عدد الأيام قبل اعتبار تعريفات الفيروسات قديمة|[إدارة تحديثات نقاط النهاية غير](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد ترتيب المصادر لتنزيل تحديثات معلومات الأمان|[إدارة تحديثات معلومات الأمان وحماية برنامج الحماية من الفيروسات من Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|بدء تحديث معلومات الأمان عند بدء التشغيل|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد يوم الأسبوع للتحقق من وجود تحديثات التحليل الذكي للأمان|[إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد الفاصل الزمني للتحقق من تحديثات معلومات الأمان|[إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تحديد الوقت للتحقق من تحديثات معلومات الأمان|[إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|تحديثات التحليل الذكي لمخاطر الأمان|تشغيل الفحص بعد تحديث معلومات الأمان|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|التهديدات|تحديد مستويات التنبيه للمخاطر التي لا يجب اتخاذ إجراء افتراضي عند الكشف عنها|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|
|التهديدات|تحديد التهديدات التي لا ينبغي اتخاذ إجراء افتراضي عليها عند الكشف عنها|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender](configure-remediation-microsoft-defender-antivirus.md)|

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
