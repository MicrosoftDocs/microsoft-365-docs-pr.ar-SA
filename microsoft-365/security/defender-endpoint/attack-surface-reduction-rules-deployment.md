---
title: متطلبات نشر قواعد ASR
description: يوفر نظرة عامة وإرشادات المتطلبات الأساسية حول نشر قواعد تقليل مساحة الهجوم (ASR).
keywords: نشر قواعد الحد من الهجمات على سطح الهجوم ونشر ASR وتمكين قواعد asr وتكوين ASR ونظام منع اقتحام المضيف وقواعد الحماية وقواعد مكافحة الهجمات وقواعد مكافحة استغلالها واستغلالها وقواعد منع Microsoft Defender لنقطة النهاية وتكوين قواعد ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 4703867449877a35d6621b76072b9420a0cdbdec
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520540"
---
# <a name="asr-rules-deployment-prerequisites"></a>متطلبات نشر قواعد ASR

## <a name="before-you-begin"></a>قبل البدء

أسطح الهجمات هي كل الأماكن التي تكون فيها مؤسستك عرضة للهجمات ولهجمات الإنترنت. تتضمن أسطح الهجمات في مؤسستك كل الأماكن التي يمكن أن يعرض فيها مهاجم أجهزة مؤسستك أو شبكاتها للخطر. يعني تقليل سطح الهجوم حماية أجهزة مؤسستك وشبكة الاتصال بها، مما يترك للمهاجمين طرقا أقل للهجوم. يمكن أن يساعد تكوين قواعد تقليل مستوى الهجوم (ASR) — واحدة من العديد من ميزات الأمان الموجودة في Microsoft Defender لنقطة النهاية —

تستهدف قواعد ASR سلوكيات برامج معينة، مثل:

- بدء تشغيل الملفات القابلة للتنفيذ والنصية التي تحاول تنزيل الملفات أو تشغيلها
- تشغيل البرامج النصية غير المريبة أو غير ذلك من البرامج النصية المريبة
- السلوكيات التي لا تحدث عادة في التطبيقات أثناء العمل العادي يوميا

من خلال تقليل أسطح الهجمات المختلفة، يمكنك المساعدة في منع وقوع الهجمات في المقام الأول.

أثناء التحضير الأولي، من المهم أن تفهم قدرات الأنظمة التي ستضعها في مكانها. سيساعدك فهم الإمكانات في تحديد قواعد ASR الأكثر أهمية لحماية مؤسستك. بالإضافة إلى ذلك، هناك العديد من المتطلبات الأساسية التي يجب عليك حضورها في التحضير لنشر ASR.

>[!IMPORTANT]
>يوفر هذا الدليل صورا وأمثلة لمساعدتك على تحديد كيفية تكوين قواعد ASR؛ قد لا تعكس هذه الصور والأمثلة أفضل خيارات التكوين  بيئتك.

قبل البدء، راجع نظرة [عامة](overview-attack-surface-reduction.md) حول الحد من سطح الهجوم، و إلغاء غموض قواعد الحد من سطح الهجوم [- الجزء 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) للحصول على معلومات تأسيسية. لفهم مجالات التغطية والتأثير المحتمل، تعرف على مجموعة قواعد ASR الحالية؛ راجع [مرجع قواعد تقليل مساحة الهجوم](attack-surface-reduction-rules-reference.md).  أثناء التعرف على مجموعة قواعد ASR، دون تعيينات GUID لكل قاعدة؛ راجع: [قواعد ASR ومصفوفة GUIDs](attack-surface-reduction-rules-reference.md#asr-rules-and-guids-matrix).

قواعد ASR هي قدرة واحدة فقط لإمكانيات الحد من سطح الهجوم ضمن Microsoft Defender لنقطة النهاية. سيدخل هذا المستند في مزيد من التفاصيل حول نشر قواعد ASR بفعالية لإيقاف التهديدات المتقدمة مثل برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان وغيرها من التهديدات.  

### <a name="rules-by-category"></a>القواعد حسب الفئة

كما هو موضح في [استخدام](attack-surface-reduction.md) قواعد الحد من سطح الهجوم لمنع إصابة البرامج الضارة، هناك قواعد متعددة للحد من سطح الهجوم ضمن MDE يمكنك تمكينها لحماية مؤسستك. فيما يلي القواعد التي تم تقسيمها حسب الفئة:

<br/>

| تهديدات متعددة الأشكال | حركة & سرقة بيانات الاعتماد | قواعد تطبيقات الإنتاجية |  قواعد البريد الإلكتروني | قواعد البرنامج النصي | قواعد Misc |
|:---|:---|:---|:---|:---|:---|
| حظر تشغيل الملفات القابلة للتنفيذ ما لم تكن تلبي معايير قائمة موثوق بها (1000 أجهزة) أو عمر (24 ساعة) أو قائمة موثوق بها | إنشاءات عملية الحظر التي تنشأ من أوامر PSExec و WMI | منع Office من إنشاء محتوى قابل للتنفيذ | حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني | حظر التعليمات البرمجية ل JS/VBS/PS/الماكرو | حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال <sup>[[1](#fn1)]<sup></sup>  |
| حظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB | حظر سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | منع Office من إنشاء عمليات الطفل |  حظر تطبيقات Office فقط من إنشاء عمليات الأطفال | حظر JS/VBS من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله | |
| استخدام الحماية المتقدمة من برامج الفدية الضارة | حظر الثبات عبر اشتراك حدث WMI | حظر Office من إدخال التعليمات البرمجية في عمليات أخرى | منع Office الاتصالات من إنشاء عمليات الطفل | | |
| | | منع Adobe Reader من إنشاء عمليات الأطفال | | | |

(<a id="fn1">1</a>) _لا يتوفر حظر إساءة استخدام برامج التشغيل الموقعة_ الضعيفة والمستغلة حاليا في أمان نقطة نهاية MEM. يمكنك تكوين هذه القاعدة باستخدام [MEM OMA-URI](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) تنشئ بعض قواعد ASR الكثير من الضوضاء، ولكنها لن تمنع الوظائف. على سبيل المثال، إذا كنت تقوم بتحديث Chrome؛ سيالوصول إلى Chrome lsass.exe؛ يتم تخزين كلمات المرور في lsass على الجهاز. ومع ذلك، يجب ألا يعمل Chrome على الوصول إلى الأجهزة المحلية lsass.exe. إذا قمت بتمكين القاعدة لحظر الوصول إلى lsass، ستولد الكثير من الأحداث. هذه الأحداث هي أحداث جيدة لأن عملية تحديث البرنامج يجب ألا lsass.exe. يؤدي تمكين هذه القاعدة إلى منع تحديثات Chrome من الوصول إلى lsass، ولكنه لن يمنع Chrome من التحديث؛ ينطبق ذلك أيضا على التطبيقات الأخرى التي تقوم ب إجراء مكالمات غير ضرورية lsass.exe. _ستحظر قاعدة حظر الوصول إلى lsass_ المكالمات غير الضرورية إلى lsass، ولكنها لن تمنع تشغيل التطبيق.

### <a name="infrastructure-requirements"></a>متطلبات البنية الأساسية

على الرغم من إمكانية استخدام أساليب متعددة لتنفيذ قواعد ASR، يستند هذا الدليل إلى بنية أساسية مكونة من:

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- Windows 10 Windows 11 الأجهزة
- Microsoft Defender لنقطة النهاية E5 أو Windows E5

للاستفادة بشكل كامل من قواعد ASR وإعداد التقارير، نوصي باستخدام Microsoft 365 Defender E5 أو Windows E5 و A5. تعرف على المزيد: [الحد الأدنى لمتطلبات Microsoft Defender لنقطة النهاية](minimum-requirements.md).

>[!Note]
>هناك أساليب متعددة لتكوين قواعد ASR. يمكن تكوين قواعد ASR باستخدام: إدارة نقاط النهاية من Microsoft (MEM) و PowerShell و نهج المجموعة و Microsoft System Center Configuration Manager (SCCM) و MEM OMA-URI.
>إذا كنت تستخدم تكوين بنية أساسية مختلفا عما هو مدرج لمتطلبات البنية _الأساسية (أعلاه_ )، يمكنك معرفة المزيد حول نشر قواعد الحد من سطح الهجوم باستخدام تكوينات أخرى هنا: تمكين قواعد الحد من سطح [الهجوم](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>تبعيات قواعد ASR

برنامج الحماية من الفيروسات من Microsoft Defender تمكين البرنامج وتكوينه كحل أساسي لمكافحة الفيروسات، ويجب أن يكون في الوضع التالي:

- حل الحماية من الفيروسات/البرامج الضارة الأساسية  
- الحالة: الوضع النشط

برنامج الحماية من الفيروسات من Microsoft Defender أن تكون في أي من الأوضاع التالية:

- غير سلبي
- الوضع السلبي مع الكشف عن نقطة النهاية والاستجابة (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر
- فحص دوري محدود (LPS)
- إيقاف التشغيل

راجع: [الحماية والحماية التي يتم توفيرها في السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>يجب تمكين الحماية السحابية (الخرائط)

برنامج الحماية من الفيروسات من Microsoft Defender العمل بسلاسة مع خدمات Microsoft السحابية. تعمل خدمات الحماية السحابية هذه، يشار إليها أيضا باسم خدمة الحماية المتقدمة من Microsoft (MAPS)، على تحسين الحماية القياسية في الوقت الحقيقي، مما يوفر أفضل برنامج حماية من الفيروسات. حماية السحابة أمر بالغ الأهمية لمنع الخروقات من البرامج الضارة ومكون هام لقواعد ASR.
[تشغيل الحماية التي يتم تسليمها من السحابة في برنامج الحماية من الفيروسات من Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>برنامج الحماية من الفيروسات من Microsoft Defender أن تكون مكونات الإصدارات الحالية

يجب ألا برنامج الحماية من الفيروسات من Microsoft Defender الإصدارات المكونة لأكثر من إصدارين أقدم من الإصدار الأكثر توفرا حاليا:

- **برنامج الحماية من الفيروسات من Microsoft Defender تحديث النظام الأساسي -** برنامج الحماية من الفيروسات من Microsoft Defender تحديث النظام الأساسي شهريا.
- **برنامج الحماية من الفيروسات من Microsoft Defender محرك -** برنامج الحماية من الفيروسات من Microsoft Defender تحديث المحرك شهريا.
- **برنامج الحماية من الفيروسات من Microsoft Defender** الأمان - تعمل Microsoft باستمرار على تحديث معلومات أمان Microsoft Defender (المعروفة أيضا بالتعريف والتوقيع) لمعالجة التهديدات الأخيرة وتنقيح منطق الكشف.

يساعد برنامج الحماية من الفيروسات من Microsoft Defender الإصدارات الحالية على تقليل نتائج قواعد ASR الإيجابية الخاطئة ويحسن برنامج الحماية من الفيروسات من Microsoft Defender الكشف عن البيانات. لمزيد من التفاصيل حول الإصدارات الحالية وكيفية تحديث المكونات المختلفة برنامج الحماية من الفيروسات من Microsoft Defender، يرجى زيارة برنامج الحماية من الفيروسات من Microsoft Defender [الأساسي](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>تحذير

لا تعمل بعض القواعد بشكل جيد إذا كانت البرامج النصية والتطبيقات غير الموقعة والمطورة داخليا ذات استخدام عال. من الصعب نشر قواعد ASR إذا لم يتم فرض توقيع التعليمات البرمجية.

## <a name="asr-rules-deployment-steps"></a>خطوات نشر قواعد ASR

وكما هو حال أي تنفيذ جديد على نطاق واسع قد يؤثر على عمليات خط العمل، من المهم أن تكون أسلوبيا في التخطيط والتنفيذ. نظرا للإمكانات القوية لقواعد ASR في منع البرامج الضارة، من الضروري التخطيط الدقيق لهذه القواعد ونشرها لضمان عملها بشكل أفضل لمسيرات عمل العملاء الفريدة. للعمل في بيئتك، تحتاج إلى تخطيط قواعد ASR واختبارها وتطبيقها وتشغيلها بعناية.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="مراحل نشر قواعد ASR" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>للعملاء الذين يستخدمون HIPS غير Microsoft ويتحولون إلى قواعد الحد من سطح الهجوم في Microsoft Defender لنقطة النهاية: تنصح Microsoft العملاء بتشغيل حل HIPS جنبا إلى جنب مع نشر قواعد ASR الخاصة بهم حتى اللحظة التي تقوم فيها بالتحويل من التدقيق إلى وضع الحظر. ضع في اعتبارك أنه يجب عليك التواصل مع مورد الحماية من الفيروسات التابع لأي جهة خارجية للحصول على توصيات الاستثناء.  

## <a name="additional-topics-in-this-deployment-collection"></a>مواضيع إضافية في مجموعة النشر هذه

[المرحلة 1: الخطة](attack-surface-reduction-rules-deployment-plan.md)

[المرحلة 2: الاختبار](attack-surface-reduction-rules-deployment-test.md)

[المرحلة 3: تنفيذ](attack-surface-reduction-rules-deployment-implement.md)

[المرحلة 4: التشغيل](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="reference"></a>المرجع

### <a name="blogs"></a>المدونات

[إزالة الغموض عن قواعد الحد من سطح الهجوم - الجزء 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[إزالة الغموض عن قواعد الحد من سطح الهجوم - الجزء 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[إزالة الغموض عن قواعد الحد من سطح الهجوم - الجزء 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[إزالة الغموض عن قواعد الحد من سطح الهجوم - الجزء 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>مجموعة ASR

[نظرة عامة حول الحد من سطح الهجوم](overview-attack-surface-reduction.md)

[استخدام قواعد الحد من سطح الهجوم لمنع إصابة البرامج الضارة](attack-surface-reduction.md)

[تمكين قواعد الحد من سطح الهجوم](enable-attack-surface-reduction.md)

[مرجع قواعد الحد من سطح الهجوم](attack-surface-reduction-rules-reference.md)

[الأسئلة الشائعة حول الحد من سطح الهجوم](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)

[الحماية والحماية التي يتم توفيرها في السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[تشغيل الحماية التي يتم تسليمها عبر السحابة في برنامج الحماية من الفيروسات من Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

[تكوين الاستثناءات والتحقق من صحتها استنادا إلى الملحق أو الاسم أو الموقع](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[برنامج الحماية من الفيروسات من Microsoft Defender دعم النظام الأساسي](manage-updates-baselines-microsoft-defender-antivirus.md)

[نظرة عامة حول المخزون في مركز إدارة Microsoft 365 Apps](/deployoffice/admincenter/inventory)

[إنشاء خطة نشر Windows](/windows/deployment/update/create-deployment-plan)

[استخدام التحكم بالوصول المستند إلى الدور (RBAC) والعلامات الخاصة بنطاق الوصول الموزعة في Intune](/mem/intune/fundamentals/scope-tags)

[تعيين ملفات تعريف الجهاز في Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>مواقع الإدارة

[إدارة نقاط النهاية من Microsoft إدارة](https://endpoint.microsoft.com/#home)

[الحد من سطح الهجوم](https://security.microsoft.com/asr?viewid=detections)

[تكوينات قواعد ASR](https://security.microsoft.com/asr?viewid=configuration)

[استثناءات قواعد ASR](https://security.microsoft.com/asr?viewid=exclusions)
