---
title: استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender أثناء عملية إعادة التهجر من حل جهة خارجية
description: استكشاف الأخطاء الشائعة وإصلاحها عند عملية برنامج الحماية من الفيروسات من Microsoft Defender
keywords: حدث، رمز الخطأ، التسجيل، استكشاف الأخطاء وإصلاحها، برنامج الحماية من الفيروسات ل microsoft defender، برنامج الحماية من الفيروسات ل windows defender، الترحيل
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: martyav
ms.author: v-maave
ms.custom: nextgen
ms.date: 10/19/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: c1b60b66977c4f93591bce20a5cf6ace0b7fc567
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573889"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender أثناء عملية إعادة التهجر من حل جهة خارجية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


يمكنك العثور على تعليمات هنا إذا كنت تواجه مشاكل أثناء عملية ا المركز عليه من حل أمان جهة خارجية برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="review-event-logs"></a>مراجعة سجلات الأحداث

1. افتح تطبيق عارض الأحداث عن طريق تحديد الأيقونة **بحث** في شريط المهام، والبحث عن *عارض الأحداث*.

    يمكن العثور على برنامج الحماية من الفيروسات من Microsoft Defender ضمن التطبيقات والخدمات **سجلات** \> **Microsoft Windows** \>  \> **Windows Defender**.

1. من هناك، حدد **فتح** أسفل **التشغيل**.

    سيعرض لك تحديد حدث من جزء التفاصيل المزيد من المعلومات حول حدث ما في الجزء السفلي، ضمن علامات التبويب عام **وتفاصيل**.

## <a name="microsoft-defender-antivirus-wont-start"></a>برنامج الحماية من الفيروسات من Microsoft Defender بدء تشغيل

يمكن أن تظهر هذه المشكلة في شكل العديد من الم IDs مختلفة للحدث، وكلها لها نفس السبب الأساسي.

### <a name="associated-event-ids"></a>"معرّف الأحداث المقترنة"

"معرّف الحدث"|اسم السجل|الوصف|المصدر
---|---|---|---
15|Application|تم Windows حالة Defender بنجاح SECURITY_PRODUCT_STATE_OFF.|مركز الأمان
5007|Microsoft-Windows-Windows Defender/التشغيلية|برنامج الحماية من الفيروسات لـ Windows Defender تغيير التكوين. إذا كان هذا الحدث غير متوقع، يجب مراجعة الإعدادات حيث قد يكون ذلك نتيجة للبرامج الضارة. <p> **القيمة القديمة:** Default\IsServiceRunning = 0x0 <p> **قيمة جديدة:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/التشغيلية|برنامج الحماية من الفيروسات لـ Windows Defender المسح الضوئي لبرامج التجسس والبرامج الأخرى التي من المحتمل أن تكون غير مرغوب فيها معطلة.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>كيفية معرفة ما إذا برنامج الحماية من الفيروسات من Microsoft Defender بدء التشغيل بسبب تثبيت برنامج الحماية من الفيروسات التابع جهة خارجية

على جهاز Windows 10 أو Windows 11، إذا كنت لا تستخدم Microsoft Defender ل Endpoint، وكان لديك برنامج مكافحة الفيروسات من جهة خارجية مثبتا، برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا. إذا كنت تستخدم Microsoft Defender ل Endpoint مع برنامج الحماية من الفيروسات المثبت بواسطة جهة خارجية، برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، مع وظائف أقل.

> [!TIP]
> ينطبق السيناريو الذي تم وصفه للتو على Windows 10 Windows 11. الإصدارات الأخرى من Windows [لديها](microsoft-defender-antivirus-compatibility.md) استجابات مختلفة برنامج الحماية من الفيروسات من Microsoft Defender يتم تشغيلها إلى جانب برنامج أمان جهة خارجية.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>استخدام تطبيق "الخدمات" للتحقق مما إذا برنامج الحماية من الفيروسات من Microsoft Defender تم إيقاف تشغيل التطبيق

لفتح تطبيق الخدمات، حدد الأيقونة **بحث** من شريط المهام وابحث عن *الخدمات*. يمكنك أيضا فتح التطبيق من سطر الأوامر عن طريق كتابة *services.msc*.

سيتم إدراج برنامج الحماية من الفيروسات من Microsoft Defender داخل تطبيق "الخدمات" ضمن Windows **Defender** \> **التشغيلية**. اسم خدمة الحماية من الفيروسات هو *برنامج الحماية من الفيروسات لـ Windows Defender الخدمة*.

أثناء التحقق من التطبيق، قد ترى أنه برنامج الحماية من الفيروسات لـ Windows Defender *تم* تعيين الخدمة يدويا، ولكن عندما تحاول بدء هذه الخدمة يدويا، ستحصل على تحذير يفيد بأن برنامج الحماية من الفيروسات لـ Windows Defender *خدمة الخدمة على الكمبيوتر المحلي بدأت ثم توقفت. تتوقف بعض الخدمات تلقائيا إذا لم تكن تستخدم بواسطة خدمات أو برامج أخرى.*

يشير ذلك إلى أنه برنامج الحماية من الفيروسات من Microsoft Defender إيقاف تشغيل البرنامج تلقائيا للحفاظ على التوافق مع برنامج مكافحة الفيروسات التابع جهة خارجية.

#### <a name="generate-a-detailed-report"></a>إنشاء تقرير مفصل

يمكنك إنشاء تقرير مفصل حول سياسات المجموعة النشطة حاليا عن طريق فتح موجه أوامر في وضع "التشغيل  كمسؤول"، ثم إدخال الأمر التالي:

```console
GPresult.exe /h gpresult.html
```

يؤدي ذلك إلى إنشاء تقرير موجود في *./gpresult.html*. افتح هذا الملف وقد ترى النتائج التالية، استنادا إلى برنامج الحماية من الفيروسات من Microsoft Defender تم إيقاف تشغيله.

##### <a name="group-policy-results"></a>نتائج نهج المجموعة

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>إذا تم تنفيذ إعدادات الأمان عبر نهج المجموعة (GPO) على المستوى المحلي أو المجال، أو عبر إدارة تكوين مركز النظام (SCCM)

ضمن تقرير GPResults، أسفل العنوان *، Windows مكونات/برنامج الحماية من الفيروسات لـ Windows Defender*، قد ترى شيئا مثل الإدخال التالي، مما يشير إلى أنه تم إيقاف برنامج الحماية من الفيروسات من Microsoft Defender.

النهج|الإعداد|الفوز ب GPO
---|---|---
إيقاف تشغيل برنامج الحماية من الفيروسات لـ Windows Defender|تم التمكين|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>إذا تم تنفيذ إعدادات الأمان عبر تفضيلات نهج المجموعة (GPP)

أسفل العنوان، عنصر السجل (مسار المفتاح: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender، اسم القيمة *: DisableAntiSpyware)،* قد ترى شيئا مثل الإدخال التالي، مما يشير إلى أنه تم إيقاف برنامج الحماية من الفيروسات من Microsoft Defender.

DisableAntiSpyware|-
---|---
الفوز ب GPO|Win10-Workstations
النتيجة: نجاح|
**عام**|
الإجراء|تحديث
**الخصائص**|
الخلية|HKEY_LOCAL_MACHINE
مسار المفتاح|SOFTWARE\Policies\Microsoft\Windows Defender
اسم القيمة|DisableAntiSpyware
نوع القيمة|REG_DWORD
بيانات القيمة|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>إذا تم تنفيذ إعدادات الأمان عبر مفتاح التسجيل

قد يحتوي التقرير على النص التالي، الذي يشير إلى برنامج الحماية من الفيروسات من Microsoft Defender تم إيقاف تشغيله:

> السجل (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (hex)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>إذا تم تعيين إعدادات الأمان في Windows أو صورة Windows الخادم

من المحتمل أن يكون المسؤول التخيلي قد حدد نهج الأمان **[DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)**، محليا عبر *GPEdit.exe* أو *LGPO.exe* أو عن طريق تعديل السجل في تسلسل المهام. يمكنك [تكوين معرف صورة](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) موثوق به برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>تشغيل برنامج الحماية من الفيروسات من Microsoft Defender مرة أخرى

برنامج الحماية من الفيروسات من Microsoft Defender تشغيل برنامج الحماية من الفيروسات تلقائيا إذا لم يكن هناك أي برنامج آخر من برامج الحماية من الفيروسات نشط حاليا. ستحتاج إلى إيقاف تشغيل برنامج الحماية من الفيروسات التابع جهة خارجية بشكل كامل لضمان برنامج الحماية من الفيروسات من Microsoft Defender تشغيل البرنامج مع الوظائف الكاملة.

> [!WARNING]
> الحلول التي تقترح تحرير قيم بدء *Windows Defender* ل *wdboot* و *wdfilter* و *wdnisdrv* و *wdnissvc* و *windefend* في HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services غير معتمدة، وقد تجبرك على إعادة صورة النظام.

يتوفر الوضع السلبي إذا بدأت باستخدام Microsoft Defender ل Endpoint و برنامج الحماية من الفيروسات التابع جهة خارجية مع برنامج الحماية من الفيروسات من Microsoft Defender. يسمح الوضع برنامج الحماية من الفيروسات من Microsoft Defender بمسح الملفات وتحديث نفسها، ولكنه لن يقوم بتمكين التهديدات. بالإضافة إلى ذلك، لا تتوفر مراقبة السلوك عبر [الحماية](configure-real-time-protection-microsoft-defender-antivirus.md) في الوقت الحقيقي في الوضع السلبي، ما لم يتم نشر منع فقدان بيانات نقطة النهاية [(DLP](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) ).

تتوفر ميزة أخرى، [تعرف بالمسح](limited-periodic-scanning-microsoft-defender-antivirus.md) الدوري المحدود، للمستخدمين النهائيين عند برنامج الحماية من الفيروسات من Microsoft Defender إلى إيقاف التشغيل تلقائيا. تسمح هذه الميزة برنامج الحماية من الفيروسات من Microsoft Defender فحص الملفات بشكل دوري إلى جانب برنامج الحماية من الفيروسات التابع جهة خارجية، باستخدام عدد محدود من عمليات الكشف.

> [!IMPORTANT]
> لا يوصى بإجراء فحص دوري محدود في بيئات المؤسسة. يتم تقليل قدرات الكشف والإدارة وإعداد التقارير المتوفرة عند تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في هذا الوضع مقارنة بالواسطة النشطة.

### <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender التوافق](microsoft-defender-antivirus-compatibility.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md)
