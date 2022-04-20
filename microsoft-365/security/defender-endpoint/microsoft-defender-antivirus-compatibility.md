---
title: التوافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى
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
ms.date: 04/19/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 08f9f3e127246b361cd76000967ae22991335338
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943436"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>التوافق برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى

**ينطبق على:**

- برنامج الحماية من الفيروسات من Microsoft Defender
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

[!include[Prerelease information](../../includes/prerelease.md)]

يتم تثبيت برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا على نقاط النهاية التي تعمل بالإصدارات التالية من Windows:

- Windows 10 أو أحدث
- Windows Server 2022
- Windows Server 2019
- Windows Server أو الإصدار 1803 أو الأحدث
- Windows Server 2016‏

ماذا يحدث عند استخدام حل آخر غير برنامج الحماية من الفيروسات/البرامج الضارة من Microsoft؟ هل يمكنك تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتج آخر من برامج الحماية من الفيروسات؟ تعتمد الإجابات على عدة عوامل، مثل نظام التشغيل الخاص بك وما إذا كنت تستخدم [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) مع الحماية من الفيروسات.

تصف هذه المقالة ما يحدث مع برنامج الحماية من الفيروسات من Microsoft Defender وحل برنامج الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft، مع Defender for Endpoint وبدونه.

> [!IMPORTANT]
> - يتوفر برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة التي تعمل Windows 10 و11، Windows Server 2022، Windows Server 2019، Windows Server، الإصدار 1803 أو الأحدث، Windows Server 2016. 
> - يتوفر برنامج الحماية من الفيروسات من Microsoft Defender أيضا على Windows Server 2012 R2 عند إلحاقه باستخدام [الحل الحديث الموحد](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - في Windows 8.1، يتم توفير الحماية من الفيروسات على مستوى المؤسسة ك [System Center Endpoint Protection](/الإصدارات السابقة/system-center/system-center-2012-R2/hh508760(v=technet.10)، والتي تتم إدارتها من خلال Microsoft Endpoint Configuration Manager.
> - كما يتم تقديم Windows Defender [للأجهزة الاستهلاكية على Windows 8.1، على](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) الرغم من أن Windows Defender لا يوفر إدارة على مستوى المؤسسة.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>الحماية من الفيروسات بدون Defender لنقطة النهاية

يصف هذا القسم ما يحدث عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتجات الحماية من الفيروسات/الحماية من البرامج الضارة غير التابعة ل Microsoft على نقاط النهاية التي لم يتم إلحاقها ب Defender لنقطة النهاية. 

> [!NOTE]
> بشكل عام، لا يتم تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على الأجهزة التي لم يتم إلحاقها ب Defender لنقطة النهاية.

يلخص الجدول التالي ما يجب توقعه:

|إصدار Windows|حل الحماية من الفيروسات/الحماية من البرامج الضارة الأساسي|حالة برنامج الحماية من الفيروسات من Microsoft Defender|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|برنامج الحماية من الفيروسات من Microsoft Defender|الوضع النشط|
|Windows 10 <br/> Windows 11|حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft|وضع التعطيل (يحدث تلقائيا)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server أو الإصدار 1803 أو الأحدث <br/> Windows Server 2016‏ |برنامج الحماية من الفيروسات من Microsoft Defender|الوضع النشط|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server أو الإصدار 1803 أو الأحدث <br/> Windows Server 2016‏  |حل الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft|معطل (تعيين يدوي) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) على Windows Server، إذا كنت تقوم بتشغيل منتج الحماية من الفيروسات غير التابع ل Microsoft، يمكنك إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender لمنع التعارض. إذا تم إلحاق الجهاز Microsoft Defender لنقطة النهاية، يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل (انظر أدناه).

> [!TIP]
> في Windows Server 2016، قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>حلول مكافحة الفيروسات/البرامج الضارة برنامج الحماية من الفيروسات من Microsoft Defender وغير التابعة ل Microsoft

> [!NOTE]
> بشكل عام، يمكن تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع الخامل فقط على نقاط النهاية التي تم إلحاقها ب Defender لنقطة النهاية.

يعتمد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي أو تعطيله على عدة عوامل، مثل:

- أي إصدار من Windows مثبت على نقطة نهاية
- ما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender هو الحل الأساسي لمكافحة الفيروسات/الحماية من البرامج الضارة على نقطة النهاية
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

(<a id="fn2">2</a>) على Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الأحدث أو Windows Server 2016 أو Windows Server 2012 R2، لا يدخل برنامج الحماية من الفيروسات من Microsoft Defender الوضع السلبي تلقائيا عند تثبيت برنامج الحماية من الفيروسات من غير Microsoft المنتج. في هذه الحالات، قم بتعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع الخامل لمنع المشاكل الناتجة عن تثبيت منتجات مكافحة الفيروسات المتعددة على الخادم. يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام PowerShell أو نهج المجموعة أو مفتاح التسجيل. 

  يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي عن طريق تعيين مفتاح التسجيل التالي:
- مسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- الاسم: `ForceDefenderPassiveMode`
- نوع: `REG_DWORD`
- قيمه: `1`

 > [!NOTE]
 > لكي يعمل الوضع السلبي على نقاط النهاية التي تعمل Windows Server 2016 وserver Windows Server 2012 R2، يجب إلحاق نقاط النهاية هذه بالحل الحديث والموحد الموضح في [خوادم Windows الملحقة](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) على Windows Server 2016، Windows Server 2012 R2، Windows Server الإصدار 1803 أو الأحدث، Windows Server 2019، وserver Windows 2022، إذا كنت تستخدم منتج الحماية من الفيروسات غير التابع ل Microsoft على نقطة نهاية *لم* يتم إلحاقها Microsoft Defender لنقطة النهاية، قم بتعطيل/إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender يدويا لمنع المشاكل الناتجة عن تثبيت منتجات مكافحة الفيروسات المتعددة على الخادم.

> [!TIP]
> في Windows Server 2016، قد ترى *برنامج الحماية من الفيروسات لـ Windows Defender* بدلا من *برنامج الحماية من الفيروسات من Microsoft Defender*.

> [!IMPORTANT]
> يتوفر برنامج الحماية من الفيروسات من Microsoft Defender فقط على الأجهزة التي تعمل Windows 10 و11، Windows Server 2022، Windows Server 2019، Windows Server، الإصدار 1803 أو أحدث، Windows Server 2016، و Windows Server 2012 R2.
>
> في Windows 8.1، يتم تقديم الحماية من الفيروسات لنقطة النهاية على مستوى المؤسسة [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10))، والتي تتم إدارتها من خلال Microsoft Endpoint Configuration Manager.
>
> كما يتم تقديم Windows Defender [للأجهزة الاستهلاكية على Windows 8.1، على](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender) الرغم من أن Windows Defender لا يوفر إدارة على مستوى المؤسسة.

يتضمن Defender لنقطة النهاية قدرات تزيد من توسيع الحماية من الفيروسات المثبتة على نقطة النهاية. يمكنك الاستفادة من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب حل آخر لمكافحة الفيروسات.

على سبيل المثال، يوفر [الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر](edr-in-block-mode.md) حماية إضافية من البيانات الاصطناعية الضارة حتى إذا لم يكن برنامج الحماية من الفيروسات من Microsoft Defender هو منتج الحماية من الفيروسات الأساسي. تتطلب هذه الإمكانات تثبيت برنامج الحماية من الفيروسات من Microsoft Defender وتشغيلها في الوضع الخامل أو الوضع النشط.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي

لكي يتم تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، يجب أن تفي نقاط النهاية بالمتطلبات التالية:

- نظام التشغيل: Windows 10 أو أحدث؛ Windows Server 2022 أو Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الأحدث
- يجب تثبيت برنامج الحماية من الفيروسات من Microsoft Defender
- يجب تثبيت منتج آخر غير برنامج الحماية من الفيروسات/الحماية من البرامج الضارة من Microsoft واستخدامه كحل الحماية من الفيروسات الأساسي
- يجب إلحاق نقاط النهاية ب Defender لنقطة النهاية

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>كيفية تأثير برنامج الحماية من الفيروسات من Microsoft Defender على وظيفة Defender لنقطة النهاية

يؤثر Defender لنقطة النهاية على ما إذا كان يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل. يمكن أن تؤثر برنامج الحماية من الفيروسات من Microsoft Defender على قدرات معينة في Defender لنقطة النهاية أيضا. على سبيل المثال، تعمل الحماية في الوقت الحقيقي عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في وضع نشط أو سلبي، ولكن ليس عند تعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته.

يلخص الجدول في هذا القسم الميزات والقدرات التي تعمل بشكل نشط أو لا، وفقا لما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي أو معطل/غير مثبت.

> [!IMPORTANT]
> تم تصميم الجدول التالي ليكون إعلاميا فقط. **لا توقف تشغيل القدرات**، مثل الحماية في الوقت الحقيقي أو الحماية المقدمة من السحابة أو الفحص الدوري المحدود إذا كنت تستخدم برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، أو إذا كنت تستخدم [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md) ، التي تعمل في الخلفية للكشف عن ومعالجة البيانات الاصطناعية الضارة التي تم الكشف عنها بعد الاختراق.

| حمايه | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*الوضع النشط*) | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*الوضع السلبي*) | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*معطل أو غير مثبت*) | [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md) | 
|:---|:---|:---|:---|:---| 
| [الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) | نعم | راجع <sup>[الملاحظة [4](#fn4)]</sup> | لا | لا | 
| [الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) | نعم | لا  | لا | لا | 
| [حماية الشبكة](network-protection.md)  | نعم | لا | لا | لا | 
| [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)  | نعم | لا | لا  | لا | 
| [توفر الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md) | لا | لا | نعم | لا | 
| [معلومات مسح الملفات والكشف عنها](review-scan-results-microsoft-defender-antivirus.md) | نعم | نعم<sup>[[5](#fn5)]</sup> | لا | نعم | 
| [معالجة المخاطر](configure-remediation-microsoft-defender-antivirus.md) | نعم | راجع <sup>[الملاحظة [6](#fn6)]</sup> | لا | نعم | 
| [تحديثات التحليل الذكي لمخاطر الأمان](manage-updates-baselines-microsoft-defender-antivirus.md) | نعم | نعم <sup>[[7](#fn7)]</sup> | لا | نعم <sup>[[7](#fn7)]</sup> | 
| [منع فقدان البيانات](../../compliance/endpoint-dlp-learn-about.md) | نعم | نعم | لا | لا |
| [الوصول إلى المجلدات الخاضعة للتحكم](controlled-folders.md) | نعم |لا | لا | لا |
| [تصفية محتوى ويب](web-content-filtering.md) | نعم | راجع <sup>[الملاحظة [8](#fn8)]</sup> | لا | لا |
| [عنصر تحكم الجهاز](device-control-report.md) | نعم | نعم | لا | لا |
| [حماية PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) | نعم | لا | لا | لا |

(<a id="fn4">4</a>) بشكل عام، عندما تكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، لا توفر الحماية في الوقت الحقيقي أي حظر أو فرض، على الرغم من تمكينها وفي الوضع السلبي.

(<a id="fn5">5</a>) عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، لا تتم جدولة عمليات الفحص.

(<a id="fn6">6</a>) عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، فإنه لا يعالج التهديدات. ومع ذلك، يمكن معالجة التهديدات من خلال [الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر](edr-in-block-mode.md). في هذه الحالة، قد ترى تنبيهات تظهر برنامج الحماية من الفيروسات من Microsoft Defender كمصدر، حتى عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل.

(<a id="fn7">7</a>) يتم التحكم في إيقاع تحديث معلومات الأمان بواسطة إعدادات Windows Update فقط. تعمل مجدولات التحديث الخاصة ب Defender (يوميا/أسبوعيا في وقت محدد، تستند إلى الفاصل الزمني) فقط عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط. يتم تجاهلها في الوضع السلبي.

(<a id="fn8">8</a>) عندما تكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، تعمل تصفية محتوى الويب فقط مع مستعرض Microsoft Edge. 

> [!NOTE]
> تستمر الحماية [من فقدان بيانات نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about) في العمل بشكل طبيعي عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الخامل.

## <a name="important-notes"></a>ملاحظات هامة

- لا تقم بتعطيل أي من الخدمات المقترنة التي تستخدمها برنامج الحماية من الفيروسات من Microsoft Defender أو Defender for Endpoint أو تطبيق أمن Windows أو إيقافها أو تعديلها. تتضمن هذه التوصية خدمات وعمليات *wscsvc* أو *SecurityHealthService* أو *MsSense* أو *Sense* أو *WinDefend* أو *MsMpEng* . يمكن أن يؤدي تعديل هذه الخدمات يدويا إلى عدم استقرار شديد على أجهزتك ويمكن أن يجعل شبكتك عرضة للخطر. يمكن أن يؤدي تعطيل هذه الخدمات أو إيقافها أو تعديلها أيضا إلى حدوث مشاكل عند استخدام حلول الحماية من الفيروسات غير الخاصة ب Microsoft وكيفية عرض معلوماتها في [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).

- في Defender لنقطة النهاية، قم بتشغيل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، حتى لو لم يكن برنامج الحماية من الفيروسات من Microsoft Defender هو حل الحماية من الفيروسات الأساسي. الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر الكشف عن العناصر الضارة الموجودة على الجهاز (ما بعد الاختراق) ومعالجتها. لمعرفة المزيد، راجع [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>كيفية تأكيد حالة برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك استخدام إحدى الطرق المتعددة لتأكيد حالة برنامج الحماية من الفيروسات من Microsoft Defender، كما هو موضح في الجدول التالي:

 | الاسلوب | الاجراء | 
 |:---|:---| 
 | تطبيق أمن Windows |  1. على جهاز Windows، افتح تطبيق أمن Windows.<br/>2. حدد **الحماية من التهديدات & الفيروسات**.<br/>3. ضمن **حماية روبوت Who لي؟** حدد **"إدارة الموفرين**".<br/>4. في صفحة **موفري الأمان**، ضمن **برنامج الحماية من الفيروسات**، يجب أن ترى **برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل**. | 
 | إدارة المهام |  1. على جهاز Windows، افتح تطبيق Task Manager.<br/>2. حدد علامة التبويب **"تفاصيل** ".<br/>3. ابحث عن **MsMpEng.exe** في القائمة. | 
 | Windows PowerShell <br/> (لتأكيد تشغيل برنامج الحماية من الفيروسات من Microsoft Defender) |  1. على جهاز Windows، افتح Windows PowerShell. <br/>2. قم بتشغيل PowerShell cmdlet التالية: `Get-Process`.<br/>3. راجع النتائج. يجب أن تشاهد **MsMpEng.exe** إذا تم تمكين برنامج الحماية من الفيروسات من Microsoft Defender. | 
 | Windows PowerShell <br/>(للتأكد من وجود حماية من الفيروسات) |  يمكنك استخدام [Get-MpComputerStatus PowerShell cmdlet](/powershell/module/defender/get-mpcomputerstatus).<br/>1. على جهاز Windows، افتح Windows PowerShell.<br/>2. تشغيل أوامر PowerShell cmdlet التالية:<br/> \|Get-MpComputerStatus حدد AMRunningMode <br/>3. راجع النتائج. يجب أن تشاهد وضع الحظر **العادي** أو **الخامل** أو **الكشف التلقائي والاستجابة على النقط النهائية** إذا تم تمكين برنامج الحماية من الفيروسات من Microsoft Defender على نقطة النهاية.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>مزيد من التفاصيل حول حالات برنامج الحماية من الفيروسات من Microsoft Defender

يصف الجدول في هذا القسم الحالات المختلفة التي قد تراها مع برنامج الحماية من الفيروسات من Microsoft Defender.

 |  الدوله  |  ما يحدث  | 
 |:---|:---| 
 |  الوضع النشط  |  في الوضع النشط، يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات على الجهاز. سيتم تطبيق الإعدادات التي تم تكوينها باستخدام Configuration Manager أو نهج المجموعة أو Microsoft Intune أو منتجات إدارة أخرى. يتم مسح الملفات ضوئيا، ومعالجة التهديدات، ويتم الإبلاغ عن معلومات الكشف في أداة التكوين (مثل Configuration Manager أو تطبيق برنامج الحماية من الفيروسات من Microsoft Defender على نقطة النهاية نفسها).  | 
 |  الوضع السلبي <br/><br/> او <br/><br/> وضع حظر الكشف التلقائي والاستجابة على النقط النهائية |  في الوضع السلبي، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق مكافحة الفيروسات، *ولا* تتم معالجة التهديدات بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <br/><br/>يمكن معالجة التهديدات من خلال [الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر](edr-in-block-mode.md) عند التشغيل في وضع الحظر الكشف التلقائي والاستجابة على النقط النهائية، ومع ذلك. <br/><br/> يتم مسح الملفات ضوئيا بواسطة الكشف التلقائي والاستجابة على النقط النهائية، ويتم توفير التقارير للكشف عن التهديدات التي تتم مشاركتها مع خدمة Defender لنقطة النهاية. قد ترى تنبيهات تظهر برنامج الحماية من الفيروسات من Microsoft Defender كمصدر، حتى عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل. <br/><br/> عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل، لا يزال بإمكانك [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)؛ ومع ذلك، لا يمكنك النقل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط إذا كان لدى أجهزتك منتج الحماية من الفيروسات غير Microsoft الذي يوفر الحماية في الوقت الحقيقي من البرامج الضارة. <br/><br/> للحصول على أفضل كفاءة في الدفاع والكشف في طبقات الأمان، تأكد من الحصول على تحديثات برنامج الحماية من الفيروسات ومكافحة البرامج الضارة، حتى إذا كان برنامج الحماية من الفيروسات من Microsoft Defender يعمل في الوضع السلبي. راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> لاحظ أن الوضع الخامل معتمد فقط على Windows Server 2012 R2 & 2016 عندما يتم إلحاق الجهاز باستخدام [الحل الحديث الموحد](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  ذوي الاحتياجات الخاصه <br/><br/> او <br/><br/> الغاء تثبيت  |  عند تعطيله أو إلغاء تثبيته، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات. لا يتم مسح الملفات ضوئيا ولا تتم معالجة التهديدات. <br/><br/> لا يوصى بتعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيتها بشكل عام؛ إذا أمكن، فاحتفظ برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل إذا كنت تستخدم حل مكافحة البرامج الضارة/الحماية من الفيروسات غير التابع ل Microsoft. <br/><br/> في الحالات التي يتم فيها تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا، يمكن إعادة تمكينه تلقائيا إذا انتهت صلاحية منتج الحماية من الفيروسات/الحماية من البرامج الضارة غير التابع ل Microsoft أو توقف عن توفير الحماية في الوقت الحقيقي من الفيروسات أو البرامج الضارة أو التهديدات الأخرى. تساعد إعادة التمكين التلقائي برنامج الحماية من الفيروسات من Microsoft Defender على ضمان الحفاظ على الحماية من الفيروسات على نقاط النهاية الخاصة بك. <br/><br/> يمكنك أيضا استخدام [فحص دوري محدود](limited-periodic-scanning-microsoft-defender-antivirus.md)، والذي يعمل مع محرك برنامج الحماية من الفيروسات من Microsoft Defender للتحقق بشكل دوري من التهديدات إذا كنت تستخدم تطبيق الحماية من الفيروسات غير Microsoft.  | 

> [!TIP]
> إذا كنت’ تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender على عملاء Windows](microsoft-defender-antivirus-in-windows-10.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender على خادم Windows](microsoft-defender-antivirus-on-windows-server.md)
- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)
- [التعرّف على تفادي فقدان بيانات نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about)
