---
title: استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender أثناء عملية إعادة التهجر من حل جهة خارجية
description: استكشاف الأخطاء الشائعة وإصلاحها عند الترحيل إلى برنامج الحماية من الفيروسات من Microsoft Defender
keywords: الحدث، رمز الخطأ، التسجيل، استكشاف الأخطاء وإصلاحها، برنامج الحماية من الفيروسات من Microsoft Defender، برنامج الحماية من الفيروسات ل Windows Defender، الترحيل
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
ms.openlocfilehash: 74843a71131ae8f10628dac96086e68e25acb2b0
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788425"
---
# <a name="troubleshoot-microsoft-defender-antivirus-while-migrating-from-a-third-party-solution"></a>استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender أثناء عملية إعادة التهجر من حل جهة خارجية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

يمكنك العثور على المساعدة هنا إذا واجهت مشاكل أثناء الترحيل من حل أمان تابع لجهة خارجية إلى برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="review-event-logs"></a>مراجعة سجلات الأحداث

1. افتح تطبيق عارض الأحداث عن طريق تحديد أيقونة **"البحث"** في شريط المهام، والبحث عن *عارض الأحداث*.

    يمكن العثور على معلومات حول برنامج الحماية من الفيروسات من Microsoft Defender ضمن **سجلات التطبيقات والخدمات** \> **Microsoft** \> **Windows** \> **Windows Defender**.

1. من هناك، حدد **«Open** » تحت **«Operational**».

    سيؤدي تحديد حدث من جزء التفاصيل إلى إظهار المزيد من المعلومات حول حدث في الجزء السفلي، ضمن علامتي التبويب **"عام** " و" **تفاصيل** ".

## <a name="microsoft-defender-antivirus-wont-start"></a>لن يبدأ برنامج الحماية من الفيروسات من Microsoft Defender

يمكن أن تظهر هذه المشكلة في شكل عدة معرفات أحداث مختلفة، وكلها لها نفس السبب الأساسي.

### <a name="associated-event-ids"></a>معرفات الأحداث المقترنة

معرف الحدث|اسم السجل|الوصف|مصدر
---|---|---|---
15|Application|تم تحديث حالة Windows Defender بنجاح SECURITY_PRODUCT_STATE_OFF.|مركز الأمان
5007|Microsoft-Windows-Windows Defender/Operational|تم تغيير تكوين برنامج الحماية من الفيروسات لـ Windows Defender. إذا كان هذا حدثا غير متوقع، يجب عليك مراجعة الإعدادات لأن هذا قد يكون نتيجة للبرامج الضارة. <p> **القيمة القديمة:** Default\IsServiceRunning = 0x0 <p> **القيمة الجديدة:** HKLM\SOFTWARE\Microsoft\Windows Defender\IsServiceRunning = 0x1|Windows Defender
5010|Microsoft-Windows-Windows Defender/Operational|برنامج الحماية من الفيروسات لـ Windows Defender يتم تعطيل الفحص بحثا عن برامج التجسس والبرامج الأخرى التي يحتمل أن تكون غير مرغوب فيها.|Windows Defender

### <a name="how-to-tell-if-microsoft-defender-antivirus-wont-start-because-a-third-party-antivirus-is-installed"></a>كيفية معرفة ما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender لن يبدأ بسبب تثبيت برنامج الحماية من الفيروسات تابع لجهة خارجية

على جهاز Windows 10 أو Windows 11، إذا كنت لا تستخدم Microsoft Defender لنقطة النهاية، وكان لديك برنامج الحماية من الفيروسات تابع لجهة خارجية مثبتا، فسيتم تشغيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا قباله. إذا كنت تستخدم Microsoft Defender لنقطة النهاية مع تثبيت برنامج الحماية من الفيروسات تابع لجهة خارجية، فستبدأ برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، مع انخفاض الأداء الوظيفي.

> [!TIP]
> ينطبق السيناريو الموضح للتو على Windows 10 Windows 11 فقط. الإصدارات الأخرى من Windows لها [استجابات مختلفة](microsoft-defender-antivirus-compatibility.md) برنامج الحماية من الفيروسات من Microsoft Defender يتم تشغيلها جنبا إلى جنب مع برامج الأمان التابعة لجهة خارجية.

#### <a name="use-services-app-to-check-if-microsoft-defender-antivirus-is-turned-off"></a>استخدام تطبيق الخدمات للتحقق من إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender

لفتح تطبيق "الخدمات"، حدد أيقونة **"البحث"** من شريط المهام وابحث عن *الخدمات*. يمكنك أيضا فتح التطبيق من سطر الأوامر عن طريق كتابة *services.msc*.

سيتم إدراج معلومات حول برنامج الحماية من الفيروسات من Microsoft Defender داخل تطبيق الخدمات ضمن **Windows Defender** \> **Operational**. اسم خدمة الحماية من الفيروسات هو *برنامج الحماية من الفيروسات لـ Windows Defender Service*.

أثناء التحقق من التطبيق، قد ترى أنه تم تعيين *برنامج الحماية من الفيروسات لـ Windows Defender Service* يدويا، ولكن عندما تحاول بدء تشغيل هذه الخدمة يدويا، تتلقى تحذيرا يفيد بأن *برنامج الحماية من الفيروسات لـ Windows Defender  بدأت خدمة الخدمة على الكمبيوتر المحلي ثم توقفت. تتوقف بعض الخدمات تلقائيا إذا لم تكن قيد الاستخدام من قبل خدمات أو برامج أخرى.*

يشير هذا إلى أنه تم إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا للحفاظ على التوافق مع برنامج الحماية من الفيروسات تابع لجهة خارجية.

#### <a name="generate-a-detailed-report"></a>إنشاء تقرير مفصل

يمكنك إنشاء تقرير مفصل حول نهج المجموعة النشطة حاليا عن طريق فتح موجه أوامر في **وضع التشغيل كمسؤول** ، ثم إدخال الأمر التالي:

```console
GPresult.exe /h gpresult.html
```

سيؤدي ذلك إلى إنشاء تقرير موجود في *./gpresult.html*. افتح هذا الملف وقد ترى النتائج التالية، استنادا إلى كيفية إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender.

##### <a name="group-policy-results"></a>نتائج نهج المجموعة

##### <a name="if-security-settings-are-implemented-via-group-policy-gpo-at-the-domain-or-local-level-or-though-system-center-configuration-manager-sccm"></a>إذا تم تنفيذ إعدادات الأمان عبر نهج المجموعة (GPO) على المجال أو المستوى المحلي، أو على الرغم من مدير تكوين مركز النظام (SCCM)

ضمن تقرير GPResults، أسفل العنوان، *Windows Components/برنامج الحماية من الفيروسات لـ Windows Defender*، قد ترى شيئا مثل الإدخال التالي، مما يشير إلى إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender.

السياسات|اعداد|عنصر نهج المجموعة الفائز
---|---|---
إيقاف تشغيل برنامج الحماية من الفيروسات لـ Windows Defender|تمكين|Win10-Workstations

###### <a name="if-security-settings-are-implemented-via-group-policy-preference-gpp"></a>إذا تم تنفيذ إعدادات الأمان عبر تفضيل نهج المجموعة (GPP)

أسفل العنوان، *عنصر التسجيل (مسار المفتاح: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender، اسم القيمة: DisableAntiSpyware)،* قد ترى شيئا مثل الإدخال التالي، مما يشير إلى إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender.

DisableAntiSpyware|-
---|---
عنصر نهج المجموعة الفائز|Win10-Workstations
النتيجة: النجاح|
**عام**|
العمل|تحديث
**خصائص**|
خليه|HKEY_LOCAL_MACHINE
مسار المفتاح|SOFTWARE\Policies\Microsoft\Windows Defender
اسم القيمة|DisableAntiSpyware
نوع القيمة|REG_DWORD
بيانات القيمة|0x1 (1)

###### <a name="if-security-settings-are-implemented-via-registry-key"></a>إذا تم تنفيذ إعدادات الأمان عبر مفتاح التسجيل

قد يحتوي التقرير على النص التالي، مما يشير إلى إيقاف تشغيل برنامج الحماية من الفيروسات من Microsoft Defender:

> السجل (regedit.exe)
>
> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender DisableAntiSpyware (dword) 1 (سداسي)

###### <a name="if-security-settings-are-set-in-windows-or-your-windows-server-image"></a>إذا تم تعيين إعدادات الأمان في Windows أو صورة خادم Windows

ربما قام المسؤول التخيلي بتعيين نهج الأمان **[أو DisableAntiSpyware](/windows-hardware/customize/desktop/unattend/security-malware-windows-defender-disableantispyware)** أو محليا عبر *GPEdit.exe**أوLGPO.exe* أو عن طريق تعديل السجل في تسلسل المهام الخاص به. يمكنك [تكوين معرف صورة موثوق به](/windows-hardware/manufacture/desktop/configure-a-trusted-image-identifier-for-windows-defender) برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="turn-microsoft-defender-antivirus-back-on"></a>تشغيل برنامج الحماية من الفيروسات من Microsoft Defender مرة أخرى

سيتم تشغيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا إذا لم يكن هناك برنامج مكافحة فيروسات آخر نشط حاليا. ستحتاج إلى إيقاف تشغيل برنامج الحماية من الفيروسات التابع لجهة خارجية تماما لضمان تشغيل برنامج الحماية من الفيروسات من Microsoft Defender بوظائف كاملة.

> [!WARNING]
> الحلول التي تقترح تحرير قيم بدء *Windows Defender* ل *wdboot* *وwdfilter* *وwdnisdrv* *وwdnissvc* *والواجهة* في HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services غير معتمدة، وقد تفرض عليك إعادة تصوير النظام الخاص بك.

يتوفر الوضع السلبي إذا بدأت في استخدام Microsoft Defender لنقطة النهاية ومكافحة الفيروسات من جهة خارجية مع برنامج الحماية من الفيروسات من Microsoft Defender. يسمح الوضع السلبي برنامج الحماية من الفيروسات من Microsoft Defender بفحص الملفات وتحديث نفسها، ولكنه لن يعالج التهديدات. بالإضافة إلى ذلك، لا تتوفر مراقبة السلوك عبر [الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) في الوضع الخامل، ما لم يتم نشر [منع فقدان بيانات نقطة النهاية (DLP](/microsoft-365/security/defender-endpoint/information-protection-in-windows-overview) ).

تتوفر ميزة أخرى، تعرف باسم [الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md)، للمستخدمين النهائيين عند تعيين برنامج الحماية من الفيروسات من Microsoft Defender لإيقاف التشغيل تلقائيا. تسمح هذه الميزة برنامج الحماية من الفيروسات من Microsoft Defender بفحص الملفات بشكل دوري إلى جانب برنامج الحماية من الفيروسات التابع لجهة خارجية، باستخدام عدد محدود من عمليات الكشف.

> [!IMPORTANT]
> لا يوصى بالمسح الدوري المحدود في بيئات المؤسسة. يتم تقليل قدرات الكشف والإدارة وإعداد التقارير المتوفرة عند تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في هذا الوضع مقارنة بالمكان النشط.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)


### <a name="see-also"></a>راجع أيضًا

- [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md)
