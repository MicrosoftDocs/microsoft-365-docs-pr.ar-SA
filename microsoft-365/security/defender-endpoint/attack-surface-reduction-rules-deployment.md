---
title: متطلبات أساسية لنشر قواعد ASR
description: يوفر نظرة عامة وإرشادات المتطلبات الأساسية حول نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR).
keywords: نشر قواعد تقليل الأجزاء المعرضة للهجوم، ونشر ASR، وتمكين قواعد asr، وتكوين ASR، ونظام منع الاختراق المضيف، وقواعد الحماية، وقواعد مكافحة الاستغلال، وقواعد مكافحة الاستغلال، وقواعد الاستغلال، وقواعد منع العدوى، Microsoft Defender لنقطة النهاية، وتكوين قواعد ASR
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
ms.openlocfilehash: 0180bfcef9d478dcf8e334a180ea3df993585e00
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666405"
---
# <a name="asr-rules-deployment-prerequisites"></a>متطلبات أساسية لنشر قواعد ASR

## <a name="before-you-begin"></a>قبل البدء

الأسطح المعرضة للهجوم هي جميع الأماكن التي تكون فيها مؤسستك عرضة للتهديدات الإلكترونية والهجمات. تتضمن الأسطح الهجومية لمؤسستك جميع الأماكن التي يمكن للمهاجم فيها اختراق أجهزة مؤسستك أو شبكاتها. إن تقليل مساحة الهجوم يعني حماية أجهزة مؤسستك وشبكتها، ما يترك للمهاجمين طرقا أقل للهجوم. يمكن أن يساعد تكوين قواعد تقليل الأجزاء المعرضة للهجوم (ASR)، وهي واحدة من العديد من ميزات الأمان الموجودة في Microsoft Defender لنقطة النهاية.

تستهدف قواعد ASR بعض سلوكيات البرامج، مثل:

- تشغيل الملفات والبرامج النصية القابلة للتنفيذ التي تحاول تنزيل الملفات أو تشغيلها
- تشغيل البرامج النصية المشوشة أو المشبوهة
- السلوكيات التي لا تحدثها التطبيقات عادة أثناء العمل اليومي العادي

من خلال تقليل أسطح الهجوم المختلفة، يمكنك المساعدة في منع حدوث الهجمات في المقام الأول.

في أثناء إعدادك الأولي، من الضروري أن تفهم قدرات الأنظمة التي ستضعها. سيساعدك فهم القدرات على تحديد قواعد ASR الأكثر أهمية لحماية مؤسستك. بالإضافة إلى ذلك، هناك العديد من المتطلبات الأساسية التي يجب عليك حضورها تحضيرا لنشر ASR.

>[!IMPORTANT]
>يوفر هذا الدليل صورا وأمثلة لمساعدتك في تحديد كيفية تكوين قواعد ASR؛ قد لا تعكس هذه الصور والأمثلة أفضل خيارات التكوين للبيئة الخاصة بك.

قبل البدء، راجع [نظرة عامة حول تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md)، [وتجميل قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) للحصول على معلومات أساسية. لفهم مجالات التغطية والتأثير المحتمل، تعرف على المجموعة الحالية من قواعد ASR؛ راجع [مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md).  بينما تتعرف على مجموعة قواعد ASR، لاحظ تعيينات GUID لكل قاعدة؛ راجع: [قواعد ASR ومصفوفة GUIDs](attack-surface-reduction-rules-reference.md#asr-rules-and-guids-matrix).

قواعد ASR هي قدرة واحدة فقط من قدرات تقليل الأجزاء المعرضة للهجوم داخل Microsoft Defender لنقطة النهاية. سيدخل هذا المستند في مزيد من التفاصيل حول نشر قواعد ASR بشكل فعال لإيقاف التهديدات المتقدمة مثل برامج الفدية الضارة التي يديرها الإنسان والتهديدات الأخرى.  

### <a name="rules-by-category"></a>القواعد حسب الفئة

كما هو موضح في [استخدام قواعد تقليل الأجزاء المعرضة للهجوم لمنع عدوى البرامج الضارة](attack-surface-reduction.md)، هناك العديد من قواعد تقليل الأجزاء المعرضة للهجوم داخل MDE التي يمكنك تمكينها لحماية مؤسستك. فيما يلي القواعد التي تم تقسيمها حسب الفئة:

<br/>

| تهديدات متعددة الأشكال | الحركة الجانبية & سرقة بيانات الاعتماد | قواعد تطبيقات الإنتاجية |  قواعد البريد الإلكتروني | قواعد البرنامج النصي | قواعد متباعدة |
|:---|:---|:---|:---|:---|:---|
| حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تفي بمعايير الانتشار (1000 جهاز) أو العمر (24 ساعة) أو معايير القائمة الموثوق بها | حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI | حظر تطبيقات Office من إنشاء محتوى قابل للتنفيذ | حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني | حظر التعليمات البرمجية JS/VBS/PS/الماكرو المشوشة | حظر إساءة استخدام برامج التشغيل <sup>الموقعة المعرضة للهجوم [[1](#fn1)]<sup></sup>  |
| حظر العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB | حظر سرقة بيانات الاعتماد من النظام الفرعي لسلطة الأمان المحلية Windows (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | حظر تطبيقات Office من إنشاء عمليات تابعة |  حظر تطبيقات الاتصال Office فقط من إنشاء عمليات تابعة | حظر JS/VBS من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله | |
| استخدام الحماية المتقدمة من برامج الفدية الضارة | حظر الثبات من خلال اشتراك حدث WMI | حظر تطبيقات Office من إدخال التعليمات البرمجية في عمليات أخرى | حظر تطبيقات الاتصال Office من إنشاء عمليات تابعة | | |
| | | حظر Adobe Reader من إنشاء عمليات تابعة | | | |

(<a id="fn1">1</a>) _حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للخطر المعرضة_ للخطر غير متوفرة حاليا في أمان نقطة نهاية MEM. يمكنك تكوين هذه القاعدة باستخدام [MEM OMA-URI](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) تولد بعض قواعد ASR ضوضاء كبيرة، ولكنها لن تمنع الوظائف. على سبيل المثال، إذا كنت تقوم بتحديث Chrome؛ سوف يصل Chrome إلى lsass.exe؛ يتم تخزين كلمات المرور في lsass على الجهاز. ومع ذلك، يجب ألا يصل Chrome إلى lsass.exe الجهاز المحلي. إذا قمت بتمكين القاعدة لحظر الوصول إلى lsass، فإنه سيتم إنشاء الكثير من الأحداث. هذه الأحداث هي أحداث جيدة لأن عملية تحديث البرامج يجب ألا تصل إلى lsass.exe. سيؤدي تمكين هذه القاعدة إلى منع تحديثات Chrome من الوصول إلى lsass، ولكن لن يمنع Chrome من التحديث؛ ينطبق هذا أيضا على التطبيقات الأخرى التي تجري استدعاءات غير ضرورية إلى lsass.exe. سيحظر _وصول الكتلة إلى قاعدة lsass_ الاستدعاءات غير الضرورية إلى lsass، ولكنه لن يمنع التطبيق من التشغيل.

### <a name="infrastructure-requirements"></a>متطلبات البنية الأساسية

على الرغم من إمكانية استخدام أساليب متعددة لتنفيذ قواعد ASR، يستند هذا الدليل إلى بنية أساسية تتكون من:

- Azure Active Directory
- إدارة نقاط النهاية من Microsoft (MEM)
- أجهزة Windows 10 وأجهزة Windows 11
- Microsoft Defender لنقطة النهاية تراخيص E5 أو Windows E5

للاستفادة الكاملة من قواعد ASR وإعداد التقارير، نوصي باستخدام ترخيص Microsoft 365 Defender E5 أو Windows E5 و A5. تعرف على المزيد: [الحد الأدنى من متطلبات Microsoft Defender لنقطة النهاية](minimum-requirements.md).

>[!Note]
>هناك أساليب متعددة لتكوين قواعد ASR. يمكن تكوين قواعد ASR باستخدام: إدارة نقاط النهاية من Microsoft (MEM) وPowerShell نهج المجموعة وMicrosoft System Center Configuration Manager (SCCM) وMEM OMA-URI.
>إذا كنت تستخدم تكوين بنية أساسية مختلف عما هو مدرج _لمتطلبات البنية الأساسية_ (أعلاه)، يمكنك معرفة المزيد حول نشر قواعد تقليل الأجزاء المعرضة للهجوم باستخدام تكوينات أخرى هنا: [تمكين قواعد تقليل الأجزاء المعرضة للهجوم](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>تبعيات قواعد ASR

يجب تمكين برنامج الحماية من الفيروسات من Microsoft Defender وتكوينه كحل أساسي لمكافحة الفيروسات، ويجب أن يكون في الوضع التالي:

- حل الحماية من الفيروسات/الحماية من البرامج الضارة الأساسي  
- الحالة: الوضع النشط

يجب ألا يكون برنامج الحماية من الفيروسات من Microsoft Defender في أي من الأوضاع التالية:

- السلبي
- الوضع السلبي مع الكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر
- المسح الدوري المحدود (LPS)
- قباله

راجع: [الحماية المقدمة من السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>يجب تمكين Cloud Protection (MAPS)

تعمل برنامج الحماية من الفيروسات من Microsoft Defender بسلاسة مع خدمات Microsoft السحابية. تعزز خدمات الحماية السحابية هذه، التي يشار إليها أيضا باسم خدمة الحماية المتقدمة من Microsoft (MAPS)، الحماية القياسية في الوقت الحقيقي، ويمكن القول إنها توفر أفضل دفاع عن الحماية من الفيروسات. تعد حماية السحابة أمرا بالغ الأهمية لمنع الخروقات من البرامج الضارة ومكون مهم من قواعد ASR.
[تشغيل الحماية التي توفرها السحابة في برنامج الحماية من الفيروسات من Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>يجب أن تكون مكونات برنامج الحماية من الفيروسات من Microsoft Defender هي الإصدارات الحالية

يجب ألا يزيد إصدار مكون برنامج الحماية من الفيروسات من Microsoft Defender التالي عن إصدارين أقدم من الإصدار الأكثر توفرا حاليا:

- **إصدار تحديث النظام الأساسي برنامج الحماية من الفيروسات من Microsoft Defender** - يتم تحديث النظام الأساسي برنامج الحماية من الفيروسات من Microsoft Defender شهريا.
- **إصدار محرك برنامج الحماية من الفيروسات من Microsoft Defender** - يتم تحديث محرك برنامج الحماية من الفيروسات من Microsoft Defender شهريا.
- **برنامج الحماية من الفيروسات من Microsoft Defender التحليل الذكي للأمان** - تحدث Microsoft باستمرار معلومات الأمان في Microsoft Defender (المعروفة أيضا بالتعريف والتوقيع) لمعالجة أحدث التهديدات، وتحسين منطق الكشف.

يساعد الاحتفاظ بالإصدارات برنامج الحماية من الفيروسات من Microsoft Defender الحالية على تقليل النتائج الإيجابية الخاطئة لقواعد ASR وتحسين قدرات الكشف برنامج الحماية من الفيروسات من Microsoft Defender. لمزيد من التفاصيل حول الإصدارات الحالية وكيفية تحديث مكونات برنامج الحماية من الفيروسات من Microsoft Defender المختلفة، تفضل بزيارة [دعم النظام الأساسي برنامج الحماية من الفيروسات من Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>التحذير

لا تعمل بعض القواعد بشكل جيد إذا كانت التطبيقات والبرامج النصية غير الموقعة والمطورة داخليا عالية الاستخدام. من الصعب نشر قواعد ASR إذا لم يتم فرض توقيع التعليمات البرمجية.

## <a name="asr-rules-deployment-steps"></a>خطوات نشر قواعد ASR

كما هو الحال مع أي تنفيذ جديد واسع النطاق قد يؤثر على عمليات خط عملك، من المهم أن تكون منهجية في تخطيطك وتنفيذك. نظرا للقدرات القوية لقواعد ASR في منع البرامج الضارة، من الضروري التخطيط الدقيق لهذه القواعد ونشرها لضمان عملها بشكل أفضل لسير عمل العملاء الفريد. للعمل في بيئتك، تحتاج إلى تخطيط قواعد ASR واختبارها وتنفيذها وتشغيلها بعناية.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="مراحل نشر قواعد ASR" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>بالنسبة للعملاء الذين يستخدمون HIPS غير التابعة ل Microsoft وينتقلون إلى قواعد تقليل الأجزاء المعرضة للهجوم Microsoft Defender لنقطة النهاية: تنصح Microsoft العملاء بتشغيل حل HIPS الخاص بهم جنبا إلى جنب مع نشر قواعد ASR الخاصة بهم حتى اللحظة التي تنتقل فيها من وضع التدقيق إلى وضع الحظر. ضع في اعتبارك أنه يجب عليك التواصل مع مورد الحماية من الفيروسات الخاص بك من الجهات الخارجية للحصول على توصيات الاستبعاد.  

## <a name="additional-topics-in-this-deployment-collection"></a>مواضيع إضافية في مجموعة النشر هذه

[المرحلة 1: الخطة](attack-surface-reduction-rules-deployment-plan.md)

[المرحلة الثانية: اختبار](attack-surface-reduction-rules-deployment-test.md)

[المرحلة 3: التنفيذ](attack-surface-reduction-rules-deployment-implement.md)

[المرحلة 4: التشغيل](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="reference"></a>المرجع

### <a name="blogs"></a>بلوق

[إزالة الغموض عن قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[إزالة الغموض عن قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[إزالة الغموض عن قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[إزالة الغموض عن قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>مجموعة ASR

[نظرة عامة على تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md)

[استخدام قواعد تقليل الأجزاء المعرضة للهجوم لمنع إصابة البرامج الضارة](attack-surface-reduction.md)

[تمكين قواعد تقليل الأجزاء المعرضة للهجوم](enable-attack-surface-reduction.md)

[مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md)

[الأسئلة المتداولة حول قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)

[الحماية المقدمة من السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[تشغيل الحماية التي توفرها السحابة في برنامج الحماية من الفيروسات من Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

[تكوين الاستثناءات والتحقق من صحتها استنادا إلى الملحق أو الاسم أو الموقع](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[دعم النظام الأساسي برنامج الحماية من الفيروسات من Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)

[نظرة عامة على المخزون في مركز إدارة Microsoft 365 Apps](/deployoffice/admincenter/inventory)

[إنشاء خطة نشر Windows](/windows/deployment/update/create-deployment-plan)

[استخدام التحكم في الوصول استنادا إلى الدور (RBAC) وعلامات النطاق ل تكنولوجيا المعلومات الموزعة في Intune](/mem/intune/fundamentals/scope-tags)

[تعيين ملفات تعريف الأجهزة في Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>مواقع الإدارة

[مركز إدارة إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/#home)

[قواعد تقليل الأجزاء المعرضة للهجوم](https://security.microsoft.com/asr?viewid=detections)

[تكوينات قواعد ASR](https://security.microsoft.com/asr?viewid=configuration)

[استثناءات قواعد ASR](https://security.microsoft.com/asr?viewid=exclusions)
