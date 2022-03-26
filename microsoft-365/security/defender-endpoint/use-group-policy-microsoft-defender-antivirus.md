---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام نهج المجموعة
description: تعرف على كيفية استخدام نهج المجموعة لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender نقاط النهاية في Microsoft Defender لنقطة النهاية.
keywords: نهج المجموعة، GPO، التكوين، الإعدادات
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
ms.openlocfilehash: 3659f0f532b14babd256f3310c4e7da8dde67e3c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63575474"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدم إعدادات نهج المجموعة لتكوين برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

يمكنك استخدام ["نهج المجموعة](/windows/win32/srvnodes/group-policy)" لتكوين برنامج الحماية من الفيروسات من Microsoft Defender نقاط النهاية وإدارتها.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام "نهج المجموعة"

بشكل عام، يمكنك استخدام الإجراء التالي لتكوين إعدادات نهج برنامج الحماية من الفيروسات من Microsoft Defender المجموعة أو تغييرها:

1. على جهاز إدارة نهج المجموعة، افتح وحدة التحكم [في](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) إدارة نهج المجموعة، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

2. باستخدام **محرر إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**.

3. انقر **فوق قوالب إدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \> **.**

5. قم بتوسيع المقطع (المشار إليه باسم الموقع  في الجدول في هذا الموضوع) الذي يحتوي على الإعداد الذي تريد تكوينه، وانقر نقرا مزدوجا فوق الإعداد لفتحه، ثم قم بإجراء تغييرات على التكوين.

6. [نشر "مجموعة عناصر المجموعة" المحدثة كما تفعل عادة](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>إعدادات نهج المجموعة وموارده

يسرد الجدول التالي إعدادات نهج المجموعة الشائع استخدامها والمتوفرة في Windows 10.

> [!TIP]
> قم بتنزيل جدول بيانات مرجع نهج المجموعة، الذي يسرد إعدادات النهج لتكوينات الكمبيوتر والمستخدم المضمنة في ملفات القوالب الإدارية التي تم تسليمها Windows. يمكنك تكوين الرجوع إلى جدول البيانات عند تحرير كائنات نهج المجموعة. <br/><br/> فيما يلي أحدث الإصدارات:
> - [نهج المجموعة الإعدادات جدول البيانات المرجعي Windows 10 تحديث مايو 2020 (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [نهج المجموعة الإعدادات جدول البيانات المرجعي Windows 11 تحديث أكتوبر 2021 (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|الموقع|الإعداد|مقالة|
|---|---|---|
|واجهة العميل|تمكين وضع واجهة المستخدم بدون رأس|[منع المستخدمين من رؤية واجهة مستخدم برنامج الحماية من الفيروسات من Microsoft Defender أو التفاعل معها](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|واجهة العميل|عرض نص إضافي للعملاء عند الحاجة إلى تنفيذ إجراء|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)|
|واجهة العميل|منع كل الإعلامات|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)|
|واجهة العميل|منع إعادة تشغيل الإعلامات|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)|
|الاستثناءات|استثناءات الملحقات|[تكوين الاستثناءات والتحقق من صحتها في برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)|
|الاستثناءات|استثناءات المسار|[تكوين الاستثناءات والتحقق من صحتها في برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)|
|الاستثناءات|استثناءات العملية|[تكوين الاستثناءات والتحقق من صحتها في برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)|
|الاستثناءات|إيقاف تشغيل الاستثناءات التلقائية|[تكوين الاستثناءات والتحقق من صحتها في برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)|
|الخرائط|تكوين ميزة "الحظر عند النظرة الأولى"|[تمكين الكتلة من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|الخرائط|الانضمام إلى Microsoft MAPS|[تمكين الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)|
|الخرائط|إرسال نماذج الملفات عند الحاجة إلى إجراء المزيد من التحليلات|[تمكين الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)|
|الخرائط|تكوين تجاوز الإعدادات المحلية لإعداد التقارير إلى Microsoft MAPS|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|تكوين التحقق من السحابة الموسعة|[تكوين الفترة الزمنية لحظر السحابة](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|تحديد مستوى الحماية السحابية|[تحديد مستوى الحماية التي يتم تسليمها من السحابة](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|نظام فحص الشبكة|تحديد مجموعات تعريف إضافية لفحص حركة مرور الشبكة| غير مستخدم (مهمل) |
|نظام فحص الشبكة|تشغيل إيقاف التعريف| غير مستخدم (مهمل)|
|نظام فحص الشبكة|تشغيل التعرف على البروتوكول| غير مستخدم (مهمل)|
|الفحص|تكوين تجاوز الإعداد المحلي لإزالة العناصر من مجلد "الفحص"|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الفحص|تكوين إزالة العناصر من مجلد "الفحص"|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعدادات المحلية لمراقبة نشاط الملف والبرنامج على الكمبيوتر|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمراقبة نشاط الملفات الواردة وال الصادرة|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي لمسح كل الملفات والمرفقات التي تم تنزيلها|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي من أجل تشغيل مراقبة السلوك|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين تجاوز الإعداد المحلي ل تشغيل الحماية في الوقت الحقيقي|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تحديد الحد الأقصى لحجم الملفات والمرفقات التي تم تنزيلها للفحص|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|مراقبة نشاط الملف والبرنامج على الكمبيوتر|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|فحص جميع الملفات والمرفقات التي تم تنزيلها|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|إيقاف تشغيل الحماية في الوقت الحقيقي|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تشغيل مراقبة السلوك|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تشغيل مسح العملية كلما تم تمكين الحماية في الوقت الحقيقي|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تشغيل إعلامات الكتابة بالحجم الخام|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|الحماية في الوقت الحقيقي|تكوين المراقبة للملفات الواردة وال الصادرة ونشاط البرنامج|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|المعالجة|تكوين تجاوز الإعداد المحلي في وقت اليوم لتشغيل فحص كامل مجدول لإكمال المعالجة|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المعالجة|تحديد يوم الأسبوع لتشغيل فحص كامل مجدول لإكمال المعالجة|[تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender مجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المعالجة|تحديد وقت اليوم لتشغيل فحص كامل مجدول لإكمال المعالجة|[تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender مجدولة](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|إعداد التقارير|إيقاف تشغيل الإعلامات المحسنة|[تكوين الإعلامات التي تظهر على نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md)
|الجذر|إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender|غير مستخدم. إذا كنت تستخدم منتج برنامج الحماية من الفيروسات من Microsoft [أو تخطط لاستخدامه، فشاهد برنامج الحماية من الفيروسات من Microsoft Defender التوافق مع منتجات الأمان الأخرى](microsoft-defender-antivirus-compatibility.md).|
|الجذر|تعريف العناوين لتجاوز الخادم الوكيل|[تكوين إعدادات اتصال الإنترنت ووكيل الجهاز](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|الجذر|تعريف autoconfig الوكيل (pac.) للاتصال بالشبكة|[تكوين إعدادات اتصال الإنترنت ووكيل الجهاز](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|الجذر|تعريف الخادم الوكيل للاتصال بالشبكة|[تكوين إعدادات اتصال الإنترنت ووكيل الجهاز](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|الجذر|تكوين سلوك دمج المسؤول المحلي في القوائم|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|الجذر|السماح لخدمة مكافحة البرامج الضارة ببدء الأولوية العادية|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|الجذر|السماح لخدمة مكافحة البرامج الضارة بتبقى قيد التشغيل دائما|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|الجذر|إيقاف تشغيل المعالجة الروتينية|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|الجذر|عشوائيا أوقات المهام المجدولة|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|السماح للمستخدمين بإيقاف الفحص مؤقتا|[منع المستخدمين من رؤية واجهة مستخدم](prevent-end-user-interaction-microsoft-defender-antivirus.md) برنامج الحماية من الفيروسات من Microsoft Defender المستخدم (غير معتمدة على Windows 10)|
|المسح الضوئي|التحقق من أحدث تعريفات الفيروسات وبرامج التجسس قبل تشغيل فحص مجدول|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد عدد الأيام التي يتم بعدها فرض إجراء مسح التقاط|[إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل متابعة الفحص الكامل|[إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل متابعة الفحص السريع|[إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي للحصول على النسبة المئوية القصوى لاستخدام CPU|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي لجدولة يوم الفحص|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي في وقت الفحص السريع المجدول|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي للوقت المجدول للفحص|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|تكوين تجاوز الإعداد المحلي لنوع الفحص لاستخدامه في عملية فحص مجدولة|[منع المستخدمين من تعديل إعدادات النهج محليا أو السماح لهم بذلك](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|المسح الضوئي|إنشاء نقطة استعادة النظام|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل إزالة العناصر من مجلد محفوظات الفحص|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل الإحصاء|[تمكين برنامج الحماية من الفيروسات من Microsoft Defender الحماية والمراقبة دائما](configure-real-time-protection-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل مسح البريد الإلكتروني|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل مسح نقاط reparse|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تشغيل الفحص الكامل على محركات أقراص الشبكة التي تم تعيينها|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|فحص ملفات الأرشيف|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|فحص ملفات الشبكة|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|مسح معبأة القابلة للتنفيذ|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| المسح الضوئي | مسح البرامج النصية | [تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>راجع أيضا [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|المسح الضوئي|فحص محركات الأقراص القابلة للإزالة|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الحد الأقصى للعمق لمسح ملفات الأرشيف ضوئيا|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الحد الأقصى للنسبة المئوية لاستخدام CPU أثناء الفحص|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الحد الأقصى لحجم ملفات الأرشيف المطلوب فحصها|[تكوين خيارات الفحص في برنامج الحماية من الفيروسات من Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد يوم الأسبوع لتشغيل فحص مجدول|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد الفاصل الزمني لتشغيل عمليات الفحص السريعة كل يوم|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد نوع الفحص الذي يجب استخدامه لمسح ضوئي مجدول|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد وقت الفحص السريع اليومي|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|تحديد وقت اليوم لتشغيل فحص مجدول|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|المسح الضوئي|بدء الفحص المجدول فقط عند تشغيل الكمبيوتر وليس عند استخدامه|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|السماح بتحديثات معلومات الأمان من Microsoft Update|[إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|السماح بتحديثات معلومات الأمان عند التشغيل على طاقة البطارية|[إدارة التحديثات للأجهزة المحمولة والأجهزة الظاهرية (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|السماح والإعلامات بتعطيل التقارير المستندة إلى التعريفات إلى Microsoft MAPS|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|السماح بتحديثات معلومات الأمان في الوقت الحقيقي استنادا إلى التقارير إلى Microsoft MAPS|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|التحقق من أحدث تعريفات الفيروسات وبرامج التجسس عند بدء التشغيل|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تعريف أسهم الملفات لتنزيل تحديثات معلومات الأمان|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender وتحديثات الأمان والحماية](manage-protection-updates-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تحديد عدد الأيام التي يكون فيها تحديث معلومات الأمان مطلوبا بعده|[إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تعريف عدد الأيام قبل اعتبار تعريفات برامج التجسس غير م تاريخ|[إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تعريف عدد الأيام قبل اعتبار تعريفات الفيروسات غير م تاريخ|[إدارة التحديثات لنقاط النهاية غير المحدثة](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تعريف ترتيب المصادر لتنزيل تحديثات معلومات الأمان|[إدارة برنامج الحماية من الفيروسات من Microsoft Defender وتحديثات الأمان والحماية](manage-protection-updates-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|بدء تحديث معلومات الأمان عند بدء التشغيل|[إدارة التحديثات التلقائية المستندة إلى الحدث](manage-event-based-updates-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تحديد يوم من أيام الأسبوع للتحقق من تحديثات معلومات الأمان|[إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تحديد الفاصل الزمني للتحقق من تحديثات معلومات الأمان|[إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تحديد وقت التحقق من تحديثات معلومات الأمان|[إدارة وقت تنزيل تحديثات الحماية وتطبيقها](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|تحديثات معلومات الأمان|تشغيل الفحص بعد تحديث معلومات الأمان|[تكوين عمليات الفحص المجدولة برنامج الحماية من الفيروسات من Microsoft Defender](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|التهديدات|تحديد مستويات تنبيهات التهديدات التي يجب عدم اتخاذ إجراء افتراضي عند الكشف عنها|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|
|التهديدات|تحديد التهديدات التي يجب عدم اتخاذ إجراء افتراضي عليها عند الكشف عنها|[تكوين المعالجة لمسح برنامج الحماية من الفيروسات من Microsoft Defender المحتوى](configure-remediation-microsoft-defender-antivirus.md)|


## <a name="see-also"></a>راجع أيضًا

- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
