---
title: برنامج الحماية من الفيروسات من Microsoft Defender التوافق مع منتجات الأمان الأخرى
description: تعرف على برنامج الحماية من الفيروسات من Microsoft Defender مع منتجات الأمان الأخرى وأنظمت التشغيل.
keywords: windows defender، defender لنقطة النهاية، الجيل التالي، برنامج الحماية من الفيروسات، التوافق، الوضع السلبي
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
ms.date: 03/16/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: fd049930b7b5b922e30e49f5796a736d44038bf2
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63571614"
---
# <a name="microsoft-defender-antivirus-compatibility-with-other-security-products"></a>برنامج الحماية من الفيروسات من Microsoft Defender التوافق مع منتجات الأمان الأخرى

**ينطبق على:**

- برنامج الحماية من الفيروسات من Microsoft Defender
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا على نقاط النهاية التي تعمل بالإصدارات التالية من Windows:

- Windows 10 أو أحدث
- Windows Server 2022
- Windows Server 2019
- Windows Server أو الإصدار 1803 أو الأحدث
- Windows Server 2016‏

ماذا يحدث عند استخدام حل آخر غير Microsoft antivirus/antimalware؟ هل يمكنك تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتج آخر لمكافحة الفيروسات؟ تعتمد الإجابات على عدة عوامل، مثل نظام التشغيل لديك وما إذا كنت تستخدم [Microsoft Defender ل Endpoint](microsoft-defender-endpoint.md) مع الحماية من الفيروسات.

تصف هذه المقالة ما يحدث برنامج الحماية من الفيروسات من Microsoft Defender برنامج الحماية من الفيروسات/مكافحة البرامج الضارة من Microsoft، مع برنامج Defender for Endpoint وبدونه.

> [!IMPORTANT]
> - يتوفر برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة التي تعمل ب Windows 10 و11 و11 و1 Windows 1 و1022 و Windows Server 2019 و Windows Server والإصدار 1803 أو الأحدث و Windows Server 2016. 
> - برنامج الحماية من الفيروسات من Microsoft Defender أيضا على Windows Server 2012 R2 عند التوفر باستخدام الحل الحديث [الموحد](/microsoft-365/security/defender-endpoint/configure-server-endpoints).
> - في Windows 8.1، يتم توفير الحماية من الفيروسات على مستوى المؤسسة ك [System Center Endpoint Protection](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10)، الذي يتم إدارته من خلال Microsoft Endpoint Configuration Manager.
> - Windows Defender أيضا للأجهزة المستهلكة على [Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender)، على الرغم من أن Windows Defender لا يوفر إدارة على مستوى المؤسسة.

## <a name="antivirus-protection-without-defender-for-endpoint"></a>الحماية من الفيروسات بدون Defender for Endpoint

يصف هذا القسم ما يحدث عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتجات مكافحة الفيروسات/البرامج الضارة غير الخاصة ب Microsoft على نقاط النهاية التي لم يتم إعدادها في Defender for Endpoint. 

> [!NOTE]
> بشكل عام، برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي على الأجهزة غير المجهزة في Defender for Endpoint.

يلخص الجدول التالي ما يجب توقعه:

|Windows الإصدار|حل الحماية من الفيروسات/البرامج الضارة الأساسية|برنامج الحماية من الفيروسات من Microsoft Defender الحالة|
|:---|:---|:---|
|Windows 10 <br/> Windows 11|برنامج الحماية من الفيروسات من Microsoft Defender|الوضع النشط|
|Windows 10 <br/> Windows 11|حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft|الوضع المعطل (يحدث تلقائيا)|
|Windows Server 2022 <br/> Windows Server 2019<br/> Windows Server أو الإصدار 1803 أو الأحدث <br/> Windows Server 2016‏ |برنامج الحماية من الفيروسات من Microsoft Defender|الوضع النشط|
|Windows Server 2022<br/>Windows Server 2019<br/>Windows Server أو الإصدار 1803 أو الأحدث <br/> Windows Server 2016‏  |حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft|معطل (تعيين يدويا) <sup>[[1](#fn1)]</sup>|

(<a id="fn1">1</a>) على Windows الخادم، إذا كنت تقوم بتشغيل منتج برنامج الحماية من الفيروسات غير Microsoft، يمكنك إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender لمنع حدوث تعارض. إذا كان الجهاز مفعلا في Microsoft Defender لنقطة النهاية، يمكنك استخدام برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي (انظر أدناه).

> [!TIP]
> على Windows Server 2016، *قد ترى برنامج الحماية من الفيروسات لـ Windows Defender* *بدلا من برنامج الحماية من الفيروسات من Microsoft Defender*.

## <a name="microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions"></a>برنامج الحماية من الفيروسات من Microsoft Defender برامج الحماية من الفيروسات/البرامج الضارة غير الخاصة ب Microsoft

> [!NOTE]
> بشكل عام، برنامج الحماية من الفيروسات من Microsoft Defender تعيين النقاط إلى الوضع السلبي فقط على نقاط النهاية التي تم إعدادها في Defender for Endpoint.

يعتمد برنامج الحماية من الفيروسات من Microsoft Defender تشغيل الكمبيوتر في الوضع النشط أو الوضع السلبي أو تم تعطيله على عدة عوامل، مثل:

- أي إصدار Windows مثبت على نقطة نهاية
- ما إذا برنامج الحماية من الفيروسات من Microsoft Defender هو الحل الأساسي لمكافحة الفيروسات/مكافحة البرامج الضارة في نقطة النهاية
- ما إذا كانت نقطة النهاية في وضع "الحافظة" لنقطة النهاية

يلخص الجدول التالي حالة برنامج الحماية من الفيروسات من Microsoft Defender في عدة سيناريوهات. 

| Windows الإصدار   | حل برنامج الحماية من الفيروسات/مكافحة البرامج الضارة  | تم ال متنبها إلى <br/> Defender ل Endpoint؟ | برنامج الحماية من الفيروسات من Microsoft Defender الحالة     |
|:------|:------|:-------|:-------|
| Windows 10 <br/> Windows 11| برنامج الحماية من الفيروسات من Microsoft Defender | نعم  | الوضع النشط | 
| Windows 10 <br/> Windows 11 | برنامج الحماية من الفيروسات من Microsoft Defender | لا   | الوضع النشط |
| Windows 10 <br/> Windows 11  | حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft | نعم  | الوضع السلبي (تلقائيا) |
| Windows 10 <br/> Windows 11  | حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft | لا   | الوضع المعطل (تلقائيا)    |
| Windows Server 2022 <br/> Windows Server 2019 <br/>Windows Server أو الإصدار 1803 أو الأحدث  | برنامج الحماية من الفيروسات من Microsoft Defender  | نعم |         الوضع النشط  |
| Windows Server 2022 <br/> Windows Server 2019 <br/> Windows Server أو الإصدار 1803 أو الأحدث   | برنامج الحماية من الفيروسات من Microsoft Defender | لا  | الوضع النشط |
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server أو الإصدار 1803 أو الأحدث  | حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft | نعم  | برنامج الحماية من الفيروسات من Microsoft Defender تعيين الإعدادات إلى الوضع السلبي (يدويا) <sup>[[2](#fn2)]<sup>  | 
| Windows Server 2022 <br/> Windows Server 2019 <p> Windows Server أو الإصدار 1803 أو الأحدث  | حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft | لا  | برنامج الحماية من الفيروسات من Microsoft Defender يجب تعطيلها (يدويا) <sup>[[3](#fn3)]<sup></sup>  |
| Windows Server 2016‏ <br/> Windows Server 2012 R2   | برنامج الحماية من الفيروسات من Microsoft Defender | نعم | الوضع النشط |
|Windows Server 2016‏ <br/> Windows Server 2012 R2  | برنامج الحماية من الفيروسات من Microsoft Defender | لا | الوضع النشط |
| Windows Server 2016‏ <br/> Windows Server 2012 R2  | حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft | نعم | برنامج الحماية من الفيروسات من Microsoft Defender تعيين الإعدادات إلى الوضع السلبي (يدويا) <sup>[[2](#fn2)]<sup> |
|Windows Server 2016‏ <br/> Windows Server 2012 R2  | حل برنامج مكافحة الفيروسات/مكافحة البرامج الضارة من Microsoft | لا | برنامج الحماية من الفيروسات من Microsoft Defender يجب تعطيلها (يدويا) <sup>[[3](#fn3)]<sup> |

(<a id="fn2">2</a>) في Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الأحدث أو Windows Server 2016 أو Windows Server 2012 R2، لا يدخل برنامج الحماية من الفيروسات من Microsoft Defender الوضع السلبي تلقائيا عند تثبيت برنامج مكافحة الفيروسات من دون Microsoft المنتج. في هذه الحالات، برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي لمنع المشاكل التي تسببها تثبيت منتجات الحماية من الفيروسات المتعددة على الخادم. يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي باستخدام PowerShell أو نهج المجموعة أو مفتاح التسجيل. 

  يمكنك تعيين برنامج الحماية من الفيروسات من Microsoft Defender إلى الوضع السلبي عن طريق تعيين مفتاح التسجيل التالي:
- المسار: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
- الاسم: `ForceDefenderPassiveMode`
- اكتب: `REG_DWORD`
- القيمة: `1`

 > [!NOTE]
 > لكي يعمل الوضع السلبي على نقاط النهاية التي تعمل Windows Server 2016 و Windows Server 2012 R2، يجب أن يتم تشغيل نقاط النهاية هذه مع الحل الموحد الحديث الموضح في خوادم [Windows على اللوحة](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016). 

(<a id="fn3">3</a>) في Windows Server 2016 أو Windows Server 2012 R2، إذا كنت تستخدم منتجا من برامج الحماية من الفيروسات من غير Microsoft ولم يتم تشغيل نقطة النهاية هذه في Microsoft Defender لنقطة النهاية، فعطل/قم ب إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender  يدويا لمنع حدوث مشاكل بسبب تثبيت العديد من منتجات الحماية من الفيروسات على خادم.

> [!TIP]
> على Windows Server 2016، *قد ترى برنامج الحماية من الفيروسات لـ Windows Defender* *بدلا من برنامج الحماية من الفيروسات من Microsoft Defender*.

> [!IMPORTANT]
> يتوفر برنامج الحماية من الفيروسات من Microsoft Defender فقط على الأجهزة التي تعمل ب Windows 10 و11 و11 و Windows Server 2022 و Windows Server 2019 و Windows Server و الإصدار 1803 أو الأحدث و Windows Server 2016 و Windows Server 2012 R2.
>
> في Windows 8.1، يتم توفير الحماية من الفيروسات على مستوى المؤسسة كعناوين System Center Endpoint Protection[](/previous-versions/system-center/system-center-2012-R2/hh508760(v=technet.10))، والتي تدار من خلال Microsoft Endpoint Configuration Manager.
>
> Windows Defender أيضا للأجهزة المستهلكة على [Windows 8.1](/previous-versions/windows/it-pro/windows-8.1-and-8/dn344918(v=ws.11)#BKMK_WindowsDefender)، على الرغم من أن Windows Defender لا يوفر إدارة على مستوى المؤسسة.

يتضمن Defender لنقطة النهاية القدرات التي توسع الحماية من الفيروسات المثبتة على نقطة النهاية. يمكنك الاستفادة من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب حل آخر لمكافحة الفيروسات.

على سبيل المثال، يوفر الكشف عن نقطة النهاية [والاستجابة (الكشف التلقائي والاستجابة على النقط النهائية)](edr-in-block-mode.md) في وضع الحظر حماية إضافية من الأعمال الضارة حتى لو لم يكن برنامج الحماية من الفيروسات من Microsoft Defender منتج الحماية من الفيروسات الأساسي. تتطلب هذه الإمكانات برنامج الحماية من الفيروسات من Microsoft Defender تثبيتها وتشغيلها في الوضع السلبي أو الوضع النشط.

### <a name="requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode"></a>متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط

لكي يتم برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، يجب أن تلبي نقاط النهاية المتطلبات التالية:

- نظام التشغيل: Windows 10 أو أحدث؛ Windows Server 2022 أو Windows Server 2019 أو Windows Server أو الإصدار 1803 أو الأحدث
- برنامج الحماية من الفيروسات من Microsoft Defender تثبيت
- يجب تثبيت منتج آخر من برامج الحماية من الفيروسات/مكافحة البرامج الضارة من Microsoft، كما يجب استخدامه كحل أساسي لمكافحة الفيروسات
- يجب أن يتم تعيين نقاط النهاية إلى Defender لنقطة النهاية

## <a name="how-microsoft-defender-antivirus-affects-defender-for-endpoint-functionality"></a>كيفية برنامج الحماية من الفيروسات من Microsoft Defender على وظيفة Defender for Endpoint

يؤثر Defender لنقطة النهاية على برنامج الحماية من الفيروسات من Microsoft Defender يمكن تشغيلها في الوضع غير النشط. برنامج الحماية من الفيروسات من Microsoft Defender تؤثر على بعض الإمكانات في Defender for Endpoint أيضا. على سبيل المثال، تعمل الحماية في الوقت الحقيقي عندما برنامج الحماية من الفيروسات من Microsoft Defender في وضع نشط أو غير نشط، ولكن ليس عند برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته.

يلخص الجدول في هذا القسم الميزات والإمكانات التي تعمل بشكل نشط أو لا، وفقا لما إذا كان برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي أو معطل/غير م تثبيت.

> [!IMPORTANT]
> تم تصميم الجدول التالي بحيث يكون معلوماتيا فقط. **لا تقوم ب** إيقاف تشغيل الإمكانات، مثل الحماية في الوقت الحقيقي أو الحماية التي يتم تسليمها بواسطة السحابة أو المسح الدوري المحدود إذا كنت تستخدم برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، أو إذا كنت تستخدم الكشف التلقائي والاستجابة على النقط النهائية في وضع [](edr-in-block-mode.md) الحظر ، الذي يعمل في الكواليس للكشف عن التحف الضارة التي تم الكشف عنها بعد الخرق وتوسطها.

 | الحماية | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*الوضع النشط*) | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*الوضع السلبي*) | برنامج الحماية من الفيروسات من Microsoft Defender <br/>(*معطل أو غير مثبتة*) | [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md) | 
 |:---|:---|:---|:---|:---| 
 | [الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) | نعم | راجع الملاحظة <sup>[[4](#fn4)]</sup> | لا | لا | 
 | [الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) | نعم | لا  | لا | لا | 
 | [حماية الشبكة](network-protection.md)  | نعم | لا | لا | لا | 
 | [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)  | نعم | لا | لا  | لا | 
 | [توفر الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md) | لا | لا | نعم | لا | 
 | [معلومات الكشف والمسح الضوئي للملفات](review-scan-results-microsoft-defender-antivirus.md) | نعم | نعم<sup>[[5](#fn5)]</sup> | لا | نعم | 
 | [معالجة المخاطر](configure-remediation-microsoft-defender-antivirus.md) | نعم | راجع <sup>الملاحظة [[6](#fn6)]</sup> | لا | نعم | 
 | [تحديثات معلومات الأمان](manage-updates-baselines-microsoft-defender-antivirus.md) | نعم | نعم | لا | نعم | 

(<a id="fn4">4</a>) بشكل عام، عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، لا توفر الحماية في الوقت الحقيقي أي حظر أو تنفيذ، على الرغم من تمكينها وفي الوضع السلبي.

(<a id="fn5">5</a>) عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، لا يتم جدولة عمليات الفحص.

(<a id="fn6">6</a>) عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، فإنه لا يعمل على معالجة التهديدات. ومع ذلك، يمكن معالجة التهديدات من خلال الكشف عن نقطة النهاية والاستجابة [لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر](edr-in-block-mode.md). في هذه الحالة، قد ترى تنبيهات تظهر برنامج الحماية من الفيروسات من Microsoft Defender المصدر، حتى عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي.

> [!NOTE]
> [Microsoft 365](/microsoft-365/compliance/endpoint-dlp-learn-about) حماية فقدان البيانات في نقطة النهاية في العمل بشكل طبيعي عندما برنامج الحماية من الفيروسات من Microsoft Defender في وضع نشط أو غير نشط.

## <a name="important-notes"></a>ملاحظات مهمة

- لا تقوم بتعطيل أو إيقاف أو تعديل أي من الخدمات المقترنة التي يستخدمها برنامج الحماية من الفيروسات من Microsoft Defender أو Defender for Endpoint أو أمن Windows التطبيق. تتضمن هذه التوصية *الخدمات والعمليات wscsvc* أو *SecurityHealthService* أو *MsSense* أو *Sense* أو *WinDefend* أو *MsMpEng* . قد يؤدي تعديل هذه الخدمات يدويا إلى عدم استقرار شديد على أجهزتك وقد يجعل شبكتك عرضة للخطر. قد يؤدي تعطيل هذه الخدمات أو إيقافها أو تعديلها إلى حدوث مشاكل عند استخدام حلول الحماية من الفيروسات غير الخاصة ب Microsoft [وكيفية عرض معلوماتها](microsoft-defender-security-center-antivirus.md) في تطبيق أمن Windows.

- في Defender for Endpoint، قم الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، حتى لو لم برنامج الحماية من الفيروسات من Microsoft Defender برنامج الحماية من الفيروسات الأساسي. الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر عن العناصر الضارة التي يتم العثور عليها على الجهاز (اختراق ما بعد) وتمنعها. لمعرفة المزيد، راجع الكشف التلقائي والاستجابة على النقط النهائية [وضع الحظر](edr-in-block-mode.md).

## <a name="how-to-confirm-the-state-of-microsoft-defender-antivirus"></a>كيفية تأكيد حالة برنامج الحماية من الفيروسات من Microsoft Defender

يمكنك استخدام أحد الأساليب العديدة لتأكيد حالة برنامج الحماية من الفيروسات من Microsoft Defender، كما هو موضح في الجدول التالي:

 | الأسلوب | الإجراء | 
 |:---|:---| 
 | أمن Windows التطبيق |  1. على جهاز Windows، افتح أمن Windows التطبيق.<br/>2. حدد **الحماية من & الفيروسات**.<br/>3. **ضمن روبوت Who أنت تحميني؟** حدد **إدارة الموفرين**.<br/>4. على صفحة **موفري** الأمان، ضمن **برنامج** الحماية من الفيروسات، **برنامج الحماية من الفيروسات من Microsoft Defender قيد تشغيل.** | 
 | إدارة المهام |  1. على جهاز Windows، افتح تطبيق إدارة المهام.<br/>2. حدد **علامة التبويب** تفاصيل.<br/>3. **ابحث عنMsMpEng.exe** في القائمة. | 
 | Windows PowerShell <br/> (لتأكيد أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل) |  1. على جهاز Windows، افتح Windows PowerShell. <br/>2. تشغيل الأمر cmdlet التالي في PowerShell: `Get-Process`.<br/>3. راجع النتائج. يجب أن ترى **MsMpEng.exe** إذا برنامج الحماية من الفيروسات من Microsoft Defender تم تمكينه. | 
 | Windows PowerShell <br/>(للتأكد من أن الحماية من الفيروسات في مكانها الصحيح) |  يمكنك استخدام [الأمر Get-MpComputerStatus PowerShell cmdlet](/powershell/module/defender/get-mpcomputerstatus).<br/>1. على جهاز Windows، افتح Windows PowerShell.<br/>2. تشغيل الأمر cmdlet التالي في PowerShell:<br/> \|Get-MpComputerStatus AMRunningMode <br/>3. راجع النتائج. يجب أن ترى **"عادي**"  أو "غير برنامج الحماية من الفيروسات من Microsoft Defender" إذا تم تمكين "برنامج الحماية من الفيروسات من Microsoft Defender" في نقطة النهاية.  | 
 | موجه الأوامر |  1. على جهاز Windows، افتح موجه الأوامر.<br/>2. اكتب `sc query windefend`، ثم اضغط على Enter.<br/>3. راجع النتائج للتأكد من أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي.  | 

## <a name="more-details-about-microsoft-defender-antivirus-states"></a>مزيد من التفاصيل حول برنامج الحماية من الفيروسات من Microsoft Defender الحالات

يصف الجدول في هذا القسم الحالات المختلفة التي قد تراها مع برنامج الحماية من الفيروسات من Microsoft Defender.

 |  الولاية  |  ماذا يحدث  | 
 |:---|:---| 
 |  الوضع النشط  |  في الوضع النشط برنامج الحماية من الفيروسات من Microsoft Defender يتم استخدام تطبيق الحماية من الفيروسات على الجهاز. الإعدادات التي يتم تكوينها باستخدام إدارة التكوين أو نهج المجموعة أو Microsoft Intune أو منتجات الإدارة الأخرى. يتم مسح الملفات ضوئيا، كما يتم معالجة التهديدات، كما يتم إعداد التقارير حول معلومات الكشف في أداة التكوين (مثل إدارة التكوين أو تطبيق برنامج الحماية من الفيروسات من Microsoft Defender على نقطة النهاية نفسها).  | 
 |  الوضع السلبي  |  في الوضع السلبي، برنامج الحماية من الفيروسات من Microsoft Defender يتم استخدام التطبيق ك تطبيق الحماية من الفيروسات، ولا يتم معالجة التهديدات عن  طريق برنامج الحماية من الفيروسات من Microsoft Defender. ومع ذلك، يمكن معالجة التهديدات من خلال الكشف عن نقطة النهاية والاستجابة [لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع](edr-in-block-mode.md) الحظر. <br/><br/> يتم فحص الملفات الكشف التلقائي والاستجابة على النقط النهائية، كما يتم توفير التقارير للكشف عن المخاطر التي تمت مشاركتها مع خدمة Defender for Endpoint. قد تظهر التنبيهات برنامج الحماية من الفيروسات من Microsoft Defender كمصدر، حتى عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي. <br/><br/> عندما برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي، لا يزال بإمكانك إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender؛ [](manage-updates-baselines-microsoft-defender-antivirus.md)ومع ذلك، لا يمكنك التنقل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط إذا كان لدى أجهزتك منتج برنامج الحماية من الفيروسات غير Microsoft يوفر الحماية في الوقت الحقيقي من البرامج الضارة. <br/><br/> للحصول على أفضل مستويات أمان الدفاع والكشف، تأكد من الحصول على تحديثات الحماية من الفيروسات وفيروسات الحماية من البرامج الضارة، حتى لو كان برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع السلبي. راجع [إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md). <br/><br/> تجدر الإشارة إلى أن الوضع السلبي مدعوم فقط على Windows Server 2012 R2 & 2016 عند تشغيل الجهاز باستخدام الحل الحديث [الموحد](/microsoft-365/security/defender-endpoint/configure-server-endpoints).  | 
 |  معطل <br/><br/> أو <br/><br/> إلغاء تثبيت  |  عند تعطيله أو إلغاء تثبيته، برنامج الحماية من الفيروسات من Microsoft Defender يتم استخدامه ك تطبيق الحماية من الفيروسات. لا يتم مسح الملفات ضوئيا ولا يتم معالجة التهديدات. <br/><br/> لا يوصى بتعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيته بشكل عام؛ إذا أمكن، فاحتفظ ب برنامج الحماية من الفيروسات من Microsoft Defender في الوضع غير النشط إذا كنت تستخدم حل مكافحة البرامج الضارة/برنامج الحماية من الفيروسات من Microsoft. <br/><br/> في الحالات التي يتم فيها تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا، يمكن إعادة تمكينه تلقائيا إذا تنتهي صلاحية منتج مكافحة الفيروسات/مكافحة البرامج الضارة غير التابع ل Microsoft أو توقف عن توفير الحماية في الوقت الحقيقي من الفيروسات أو البرامج الضارة أو التهديدات الأخرى. تساعد إعادة التمكين التلقائي برنامج الحماية من الفيروسات من Microsoft Defender على ضمان الحفاظ على الحماية من الفيروسات في نقاط النهاية. <br/><br/> يمكنك [أيضا استخدام الفحص](limited-periodic-scanning-microsoft-defender-antivirus.md) الدوري المحدود، الذي يعمل مع محرك برنامج الحماية من الفيروسات من Microsoft Defender للتحقق بشكل دوري من التهديدات إذا كنت تستخدم تطبيقا غير من تطبيقات مكافحة الفيروسات من Microsoft.  | 


## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender على Windows العملاء](microsoft-defender-antivirus-in-windows-10.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server](microsoft-defender-antivirus-on-windows-server.md)
- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)
- [التعرف على Microsoft 365 فقدان بيانات نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about)
