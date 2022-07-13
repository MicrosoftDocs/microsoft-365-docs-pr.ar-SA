---
title: توافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى
description: تعرف على برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى وأنظمة التشغيل.
keywords: windows Defender، Defender لنقطة النهاية، الجيل التالي، برنامج الحماية من الفيروسات، التوافق، الوضع السلبي
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: mkaminska, pahuijbr
manager: dansimp
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 860c1cd36568705b2646cf14b6fea071af4a19a5
ms.sourcegitcommit: aa9e1bceb661df894f66d5dd5f4ab692c870fc71
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66756594"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>توافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى

**ينطبق على:**

- برنامج الحماية من الفيروسات من Microsoft Defender
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يتم تثبيت برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا على نقاط النهاية التي تعمل بالإصدارات التالية من Windows:

- Windows 10 أو أحدث
- Windows Server 2022
- Windows Server 2019
- Windows Server أو الإصدار 1803 أو الأحدث
- Windows Server 2016‏

ماذا يحدث عند استخدام حل آخر غير برنامج الحماية من الفيروسات/البرامج الضارة من Microsoft؟ هل يمكنك تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتج آخر من برامج الحماية من الفيروسات؟ تعتمد الإجابات على عدة عوامل، مثل نظام التشغيل الخاص بك وما إذا كنت تستخدم [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) مع الحماية من الفيروسات.

تصف هذه المقالة ما يحدث مع برنامج الحماية من الفيروسات من Microsoft Defender وحل برنامج الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft، مع Defender for Endpoint وبدونه.

> [!IMPORTANT]
> - يتوفر برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة التي تعمل Windows 10 و11 وWindows Server 2022 وWindows Server 2019 وWindows Server والإصدار 1803 أو الأحدث وWindows Server 2016. 
> - يتوفر برنامج الحماية من الفيروسات من Microsoft Defender أيضا على Windows Server 2012 R2 عند إلحاقه باستخدام [الحل الحديث والموحد](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - في Windows 8.1، يتم تقديم الحماية من الفيروسات لنقطة النهاية على مستوى [المؤسسة System Center Endpoint Protection،](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)) والتي تتم إدارتها من خلال Configuration Manager نقطة النهاية من Microsoft.
> - كما يتم تقديم Windows Defender [للأجهزة الاستهلاكية على Windows 8.1، على](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) الرغم من أن Windows Defender لا يوفر إدارة على مستوى المؤسسة.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>الحماية من الفيروسات بدون Defender لنقطة النهاية

يصف هذا القسم ما يحدث عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتجات الحماية من الفيروسات/الحماية من البرامج الضارة غير التابعة ل Microsoft على نقاط النهاية التي لم يتم إلحاقها ب Defender لنقطة النهاية. 

> [!NOTE]
> بشكل عام، لا يعمل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على الأجهزة التي لم يتم إلحاقها ب Defender لنقطة النهاية.

يلخص الجدول التالي ما يجب توقعه:

|إصدار Windows|حل الحماية من الفيروسات/الحماية من البرامج الضارة الأساسي|حالة برنامج الحماية من الفيروسات من Microsoft Defender|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|برنامج الحماية من الفيروسات من Microsoft Defender|الوضع النشط|
|Windows 10 <br/> Windows 11|حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft|وضع التعطيل (يحدث تلقائيا)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server أو الإصدار 1803 أو الأحدث <br/> Windows Server 2016‏ <br/> Windows Server 2012 R2 |برنامج الحماية من الفيروسات من Microsoft Defender|الوضع النشط|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server أو الإصدار 1803 أو الأحدث <br/> Windows Server 2016‏ |حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft|معطل (تعيين يدوي) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) على Windows Server، إذا كنت تقوم بتشغيل منتج الحماية من الفيروسات غير التابع ل Microsoft، يمكنك إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender لمنع التعارض. إذا تم إلحاق الجهاز Microsoft Defender لنقطة النهاية، يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي (انظر أدناه).

> [!TIP]
> في Windows Server 2016، قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>حلول الحماية من الفيروسات/البرامج الضارة من Microsoft Defender وحلول الحماية من الفيروسات/البرامج الضارة غير التابعة ل Microsoft

> [!NOTE]
> بشكل عام، يمكن تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي فقط على نقاط النهاية التي تم إلحاقها ب Defender لنقطة النهاية.

يعتمد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي أو تم تعطيله على عدة عوامل، مثل:

- أي إصدار من Windows مثبت على نقطة نهاية
- ما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender هو الحل الأساسي لمكافحة الفيروسات/البرامج الضارة على نقطة النهاية
- ما إذا كانت نقطة النهاية قد تم إلحاقها ب Defender لنقطة النهاية

يلخص الجدول التالي حالة برنامج الحماية من الفيروسات من Microsoft Defender في عدة سيناريوهات. 

| إصدار Windows   | حل مكافحة الفيروسات/الحماية من البرامج الضارة  | تم إلحاقه <br/> Defender لنقطة النهاية؟ | حالة برنامج الحماية من الفيروسات من Microsoft Defender     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| برنامج الحماية من الفيروسات من Microsoft Defender | نعم  | الوضع النشط | 
| Windows 10 <br/> Windows 11 | برنامج الحماية من الفيروسات من Microsoft Defender | لا   | الوضع النشط |
| Windows 10 <br/> Windows 11  | حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft | نعم  | الوضع السلبي (تلقائيا) |
| Windows 10 <br/> Windows 11  | حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft | لا   | وضع التعطيل (تلقائيا)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server، الإصدار 1803 أو الأحدث  | برنامج الحماية من الفيروسات من Microsoft Defender  | نعم |         الوضع النشط  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server، الإصدار 1803 أو الأحدث   | برنامج الحماية من الفيروسات من Microsoft Defender | لا  | الوضع النشط |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server، الإصدار 1803 أو الأحدث  | حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft | نعم  | يجب تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي (يدويا) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server، الإصدار 1803 أو الأحدث  | حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft | لا  | يجب تعطيل برنامج الحماية من الفيروسات من Microsoft Defender (يدويا) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016‏ <br/> Windows Server 2012 R2   | برنامج الحماية من الفيروسات من Microsoft Defender | نعم | الوضع النشط |
|Windows Server 2016‏ <br/> Windows Server 2012 R2  | برنامج الحماية من الفيروسات من Microsoft Defender | لا | الوضع النشط |
| Windows Server 2016‏ <br/> Windows Server 2012 R2  | حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft | نعم | يجب تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي (يدويا) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016‏ <br/> Windows Server 2012 R2  | حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft | لا | يجب تعطيل برنامج الحماية من الفيروسات من Microsoft Defender (يدويا) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) على Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الإصدار الأحدث أو Windows Server 2016 أو Windows Server 2012 R2، لا يدخل برنامج الحماية من الفيروسات من Microsoft Defender الوضع السلبي تلقائيا عند تثبيت منتج الحماية من الفيروسات غير التابع ل Microsoft. في هذه الحالات، قم بتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع الخامل لمنع المشاكل الناتجة عن تثبيت منتجات مكافحة الفيروسات المتعددة على الخادم. يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام مفتاح التسجيل كما يلي:
- مسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- الاسم: `ForceDefenderPassiveMode`
- نوع: `REG_DWORD`
- قيمه: `1`

يمكنك عرض حالة الحماية في PowerShell باستخدام الأمر [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus). تحقق من قيمة `AMRunningMode`. يجب أن تشاهد وضع كتلة **Normal** أو **Passive** أو **EDR** إذا تم تمكين برنامج الحماية من الفيروسات من Microsoft Defender على نقطة النهاية. 

 > [!NOTE]
 > لكي يعمل الوضع السلبي على نقاط النهاية التي تعمل بنظامي التشغيل Windows Server 2016 وWindows Server 2012 R2، يجب إلحاق نقاط النهاية هذه بالحل الحديث والموحد الموضح في [خوادم Windows المحلية](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) على Windows Server 2016 وWindows Server 2012 R2 وإصدار Windows Server 1803 أو أحدث وWindows Server 2019 وWindows Server 2022، إذا كنت تستخدم منتج الحماية من الفيروسات غير التابع ل Microsoft على نقطة نهاية *لم* يتم إلحاقها Microsoft Defender لنقطة النهاية ، قم بتعطيل/إزالة تثبيت برنامج الحماية من الفيروسات من Microsoft Defender يدويا لمنع حدوث مشاكل بسبب تثبيت منتجات مكافحة فيروسات متعددة على خادم.

> [!TIP]
> في Windows Server 2016، قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender*.

يتضمن Defender لنقطة النهاية قدرات تزيد من توسيع الحماية من الفيروسات المثبتة على نقطة النهاية. يمكنك الاستفادة من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب حل آخر لمكافحة الفيروسات.

على سبيل المثال، يوفر [الكشف عن نقطة النهاية والاستجابة لها (EDR) في وضع الحظر](edr-in-block-mode.md) حماية إضافية من البيانات الاصطناعية الضارة حتى إذا لم يكن برنامج الحماية من الفيروسات من Microsoft Defender هو منتج الحماية من الفيروسات الأساسي. تتطلب هذه الإمكانات تثبيت برنامج الحماية من الفيروسات من Microsoft Defender وتشغيله في الوضع الخامل أو الوضع النشط.

## <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي

لكي يعمل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، يجب أن تفي نقاط النهاية بالمتطلبات التالية:

- نظام التشغيل: Windows 10 أو أحدث؛ Windows Server 2022 أو Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الأحدث
- يجب تثبيت برنامج الحماية من الفيروسات من Microsoft Defender
- يجب تثبيت منتج آخر غير برنامج الحماية من الفيروسات/الحماية من البرامج الضارة من Microsoft واستخدامه كحل الحماية من الفيروسات الأساسي
- يجب إلحاق نقاط النهاية ب Defender لنقطة النهاية

> [!IMPORTANT]
> - يتوفر برنامج الحماية من الفيروسات من Microsoft Defender فقط على الأجهزة التي تعمل Windows 10 و11 وWindows Server 2022 وWindows Server 2019 وWindows Server والإصدار 1803 أو الأحدث وWindows Server 2016 وWindows Server 2012 R2.
> - في Windows 8.1، يتم تقديم الحماية من الفيروسات لنقطة النهاية على مستوى المؤسسة [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10))، والتي تتم إدارتها من خلال Configuration Manager نقطة النهاية من Microsoft.
> - كما يتم تقديم Windows Defender [للأجهزة الاستهلاكية على Windows 8.1، على](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) الرغم من أن Windows Defender لا يوفر إدارة على مستوى المؤسسة.

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>كيف يؤثر برنامج الحماية من الفيروسات من Microsoft Defender على وظيفة Defender لنقطة النهاية

يؤثر Defender لنقطة النهاية على إمكانية تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. ويمكن أن تؤثر حالة برنامج الحماية من الفيروسات من Microsoft Defender على قدرات معينة في Defender لنقطة النهاية. على سبيل المثال، تعمل الحماية في الوقت الحقيقي عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في وضع نشط أو سلبي، ولكن ليس عند تعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته.

> [!IMPORTANT]
> - يلخص الجدول في هذا القسم الميزات والقدرات التي تعمل بشكل نشط أو لا، وفقا لما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي أو معطل/غير مثبت. تم تصميم هذا الجدول ليكون إعلاميا فقط.   
> - **لا توقف تشغيل القدرات**، مثل الحماية في الوقت الحقيقي أو الحماية المقدمة من السحابة أو الفحص الدوري المحدود إذا كنت تستخدم برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، أو إذا كنت تستخدم [EDR في وضع الحظر](edr-in-block-mode.md)، والذي يعمل خلف الكواليس للكشف عن البيانات الاصطناعية الضارة التي تم الكشف عنها بعد الاختراق ومعالجتها.

| حمايه | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*الوضع النشط*) | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*الوضع السلبي*) | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*معطل أو غير مثبت*) | [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) | نعم | راجع <sup>[الملاحظة [4](#fn4)]</sup> | لا | لا | 
| [الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) | نعم | لا  | لا | لا | 
| [حماية الشبكة](network-protection.md)  | نعم | لا | لا | لا | 
| [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)  | نعم | لا | لا  | لا | 
| [توفر الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md) | لا | لا | نعم | لا | 
| [معلومات مسح الملفات والكشف عنها](review-scan-results-microsoft-defender-antivirus.md) | نعم | نعم <sup>[[5](#fn5)]</sup> | لا | نعم | 
| [معالجة المخاطر](configure-remediation-microsoft-defender-antivirus.md) | نعم | راجع <sup>[الملاحظة [6](#fn6)]</sup> | لا | نعم | 
| [تحديثات التحليل الذكي لمخاطر الأمان](manage-updates-baselines-microsoft-defender-antivirus.md) | نعم | نعم <sup>[[7](#fn7)]</sup> | لا | نعم <sup>[[7](#fn7)]</sup> | 
| [منع فقدان البيانات](../../compliance/endpoint-dlp-learn-about.md) | نعم | نعم | لا | لا |
| [الوصول إلى المجلدات الخاضعة للتحكم](controlled-folders.md) | نعم |لا | لا | لا |
| [تصفية محتوى ويب](web-content-filtering.md) | نعم | راجع <sup>[الملاحظة [8](#fn8)]</sup> | لا | لا |
| [عنصر تحكم الجهاز](device-control-report.md) | نعم | نعم | لا | لا |
| [حماية PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | نعم | لا | لا | لا |

(<a id="fn4">4</a>) بشكل عام، عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، لا توفر الحماية في الوقت الحقيقي أي حظر أو فرض، على الرغم من تمكينها وفي الوضع السلبي.

(<a id="fn5">5</a>) عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، لا تتم جدولة عمليات الفحص.

(<a id="fn6">6</a>) عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، فإنه لا يعالج التهديدات. ومع ذلك، يمكن معالجة التهديدات عن طريق [الكشف عن نقطة النهاية والاستجابة لها (EDR) في وضع الحظر](edr-in-block-mode.md). في هذه الحالة، قد ترى تنبيهات تظهر برنامج الحماية من الفيروسات من Microsoft Defender كمصدر، حتى عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي.

(<a id="fn7">7</a>) يتم التحكم في إيقاع تحديث معلومات الأمان بواسطة إعدادات Windows Update فقط. تعمل مجدولات التحديث الخاصة ب Defender (يوميا/أسبوعيا في وقت محدد، تستند إلى الفاصل الزمني) فقط عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط. يتم تجاهلها في الوضع السلبي.

(<a id="fn8">8</a>) عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، فإن تصفية محتوى الويب تعمل فقط مع مستعرض Microsoft Edge. 

> [!IMPORTANT]
> - تستمر الحماية [من فقدان بيانات نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about) في العمل بشكل طبيعي عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في وضع نشط أو سلبي.
>
> - لا تقم بتعطيل أو إيقاف أو تعديل أي من الخدمات المقترنة التي يتم استخدامها بواسطة برنامج الحماية من الفيروسات من Microsoft Defender أو Defender لنقطة النهاية أو تطبيق أمن Windows. تتضمن هذه التوصية خدمات وعمليات *wscsvc* أو *SecurityHealthService* أو *MsSense* أو *Sense* أو *WinDefend* أو *MsMpEng* . يمكن أن يؤدي تعديل هذه الخدمات يدويا إلى عدم استقرار شديد على أجهزتك ويمكن أن يجعل شبكتك عرضة للخطر. يمكن أن يؤدي تعطيل هذه الخدمات أو إيقافها أو تعديلها أيضا إلى حدوث مشاكل عند استخدام حلول الحماية من الفيروسات غير الخاصة ب Microsoft وكيفية عرض معلوماتها في [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).
>
> - في Defender لنقطة النهاية، يمكنك تشغيل EDR في وضع الحظر، حتى إذا لم يكن برنامج الحماية من الفيروسات من Microsoft Defender هو حل الحماية من الفيروسات الأساسي. يكشف EDR في وضع الحظر عن العناصر الضارة الموجودة على الجهاز (ما بعد الاختراق) ويعالجها. لمعرفة المزيد، راجع [EDR في وضع الحظر](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>كيفية تأكيد حالة برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك استخدام إحدى الطرق المتعددة لتأكيد حالة برنامج الحماية من الفيروسات من Microsoft Defender. يمكنك:

- [استخدم تطبيق أمن Windows لتحديد تطبيق الحماية من الفيروسات](#use-the-windows-security-app-to-identify-your-antivirus-app).
- [استخدم إدارة المهام لتأكيد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender](#use-task-manager-to-confirm-that-microsoft-defender-antivirus-is-running).
- [استخدم Windows PowerShell لتأكيد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender](#use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running).
- [استخدم Windows PowerShell لتأكيد تشغيل الحماية من الفيروسات](#use-windows-powershell-to-confirm-that-antivirus-protection-is-running).

### <a name="use-the-windows-security-app-to-identify-your-antivirus-app"></a>استخدام تطبيق أمن Windows لتحديد تطبيق الحماية من الفيروسات

1. على جهاز Windows، افتح تطبيق أمن Windows.

2. حدد **الحماية من الفيروسات والمخاطر**.

3. ضمن **من يحميني؟** حدد **"إدارة الموفرين**".

4. في صفحة **موفري الأمان** ، ضمن **برنامج الحماية من الفيروسات**، يجب أن ترى **أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل**.

### <a name="use-task-manager-to-confirm-that-microsoft-defender-antivirus-is-running"></a>استخدام إدارة المهام لتأكيد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender

1. على جهاز Windows، افتح تطبيق Task Manager.

2. حدد علامة التبويب **"تفاصيل** ".

3. ابحث عن **MsMpEng.exe** في القائمة.

### <a name="use-windows-powershell-to-confirm-that-microsoft-defender-antivirus-is-running"></a>استخدم Windows PowerShell لتأكيد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender

> [!NOTE]
> استخدم هذا الإجراء فقط لتأكيد ما إذا كان Microsoft Defender Antirivus قيد التشغيل على نقطة نهاية.

1. على جهاز Windows، افتح Windows PowerShell. 

2. تشغيل أمر Cmdlet PowerShell التالي: `Get-Process`.

3. راجع النتائج. يجب أن تشاهد **MsMpEng.exe** إذا تم تمكين برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-powershell-to-confirm-that-antivirus-protection-is-running"></a>استخدام Windows PowerShell لتأكيد تشغيل الحماية من الفيروسات

> [!NOTE]
> استخدم هذا الإجراء فقط لتأكيد تمكين الحماية من الفيروسات على نقطة نهاية.

1. على جهاز Windows، افتح Windows PowerShell.

2. تشغيل cmdlet PowerShell التالي: `Get-MpComputerStatus | select AMRunningMode`.

3. راجع النتائج. يجب أن تشاهد **الوضع العادي** أو **السلبي** أو **وضع حظر EDR** إذا تم تمكين الحماية من الفيروسات على نقطة النهاية. 

> [!NOTE]
> لاحظ أن هذا الإجراء هو فقط لتأكيد ما إذا كانت الحماية من الفيروسات ممكنة على نقطة نهاية.

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>مزيد من التفاصيل حول حالات برنامج الحماية من الفيروسات من Microsoft Defender

تصف الأقسام التالية ما يجب توقعه عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender:

- [في الوضع النشط](#active-mode)
- [في الوضع السلبي، أو عند تشغيل EDR في وضع الحظر](#passive-mode-or-edr-block-mode)
- [معطل أو غير مثبت](#disabled-or-uninstalled)

### <a name="active-mode"></a>الوضع النشط

في الوضع النشط، يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات على الجهاز. سيتم تطبيق الإعدادات التي تم تكوينها باستخدام Configuration Manager أو نهج المجموعة أو Microsoft Intune أو منتجات إدارة أخرى. يتم مسح الملفات ضوئيا، ومعالجة التهديدات، ويتم الإبلاغ عن معلومات الكشف في أداة التكوين (كما هو الحال في مركز إدارة Microsoft إدارة نقاط النهاية أو تطبيق Microsoft Defender Antivirus على نقطة النهاية).  

### <a name="passive-mode-or-edr-block-mode"></a>الوضع السلبي أو وضع حظر EDR

في الوضع السلبي، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق مكافحة الفيروسات، *ولا* تتم معالجة التهديدات بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. ومع ذلك، يمكن معالجة التهديدات عن طريق [الكشف عن نقطة النهاية والاستجابة لها (EDR) في وضع الحظر](edr-in-block-mode.md). يتم مسح الملفات ضوئيا بواسطة EDR، ويتم توفير التقارير للكشف عن التهديدات التي تتم مشاركتها مع خدمة Defender for Endpoint. قد ترى تنبيهات تظهر برنامج الحماية من الفيروسات من Microsoft Defender كمصدر، حتى عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. 

عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، لا يزال بإمكانك [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)؛ ومع ذلك، لا يمكنك نقل برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع النشط إذا كان لدى أجهزتك منتج الحماية من الفيروسات غير التابع ل Microsoft الذي يوفر الحماية في الوقت الحقيقي من البرامج الضارة.

**تأكد من الحصول على تحديثات برنامج الحماية من الفيروسات والحماية من البرامج الضارة، حتى إذا كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي**. راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).<br/><br/>لاحظ أن الوضع السلبي مدعوم فقط على Windows Server 2012 R2 & 2016 عندما يتم إلحاق الجهاز باستخدام [الحل الحديث الموحد](/microsoft-365/security/defender-endpoint/configure-server-endpoints). 

### <a name="disabled-or-uninstalled"></a>معطل أو غير مثبت

عند التعطيل أو إلغاء التثبيت، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات. لا يتم مسح الملفات ضوئيا ولا تتم معالجة التهديدات. لا يوصى بتعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته بشكل عام؛ إذا كان ذلك ممكنا، فاحتفظ ب Microsoft Defender Antivirus في الوضع السلبي إذا كنت تستخدم حل مكافحة البرامج الضارة/الحماية من الفيروسات من غير Microsoft.

في الحالات التي يتم فيها تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا، يمكن إعادة تمكينه تلقائيا إذا انتهت صلاحية منتج الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft أو إذا كان غير مثبت أو يتوقف عن توفير الحماية في الوقت الحقيقي من الفيروسات أو البرامج الضارة أو التهديدات الأخرى. تساعد إعادة التمكين التلقائي لبرامج الحماية من الفيروسات من Microsoft Defender على ضمان الحفاظ على الحماية من الفيروسات على نقاط النهاية.

قد تستخدم أيضا [فحصا دوريا محدودا](limited-periodic-scanning-microsoft-defender-antivirus.md)، والذي يعمل مع محرك الحماية من الفيروسات من Microsoft Defender للتحقق بشكل دوري من التهديدات إذا كنت تستخدم تطبيق الحماية من الفيروسات غير التابع ل Microsoft.  | 

## <a name="what-about-non-windows-devices"></a>ماذا عن الأجهزة غير التي تعمل بنظام Windows؟

 إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:

- [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
- [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
- [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
- [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
- [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender على عملاء Windows](microsoft-defender-antivirus-in-windows-10.md)
- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)
- [التعرّف على تفادي فقدان بيانات نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about)
