---
title: الخطوة 1. فرز أول حادث وتحليله
description: كيفية الفرز والبدء في تحليل أول حادث في Microsoft 365 Defender.
keywords: الأحداث، التنبيهات، التحقق، الارتباط، الهجوم، الأجهزة، الأجهزة، المستخدمون، الهويات، الهوية، علبة البريد، البريد الإلكتروني، 365، microsoft، m365، الاستجابة للحوادث، هجوم عبر الإنترنت
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 299cb7847e19e625bbae3122e16c56bb54e05c89
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499012"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>الخطوة 1. فرز أول حادث وتحليله

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

بينما تقضي بعض الوقت في إنشاء تدابير الأمان وتطبيقها والمحافظة عليها وفقا لمعايير المؤسسة، يمكنك إعداد حلول الأمان لمساعدتك على تحديد المخاطر والمخاطر الأمنية بسرعة. Microsoft 365 Defender إمكانية الكشف عن الأحداث وفرزها التحقيق فيها من خلال تجربتها في جزء واحد من الزجاج حيث يمكنك العثور على المعلومات التي تحتاج إليها لاتخاذ قرارات في الوقت المناسب.

بمجرد اكتشاف حادث أمان، Microsoft 365 Defender تفاصيل ستحتاج إليها لفرز حادث أو أحداث أو تحديد أولويتها على غيرها. بعد تحديد تحديد الأولويات، يمكن للمحللين بعد ذلك تركيز تركيزهم على التحقق من الحالات المعينة لهم.

## <a name="detection-by-microsoft-365-defender"></a>الكشف حسب Microsoft 365 Defender

Microsoft 365 Defender تلقي التنبيهات والأحداث من أنظمة أمان Microsoft الأساسية المتعددة كمصادر الكشف لإنشاء صورة غير مهيأ سياق لنشاط ضار. مصادر الكشف المحتملة هي:

- [Microsoft Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md) هو حل الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية) يستخدم برنامج الحماية من الفيروسات من Microsoft Defender والحماية المتقدمة من المخاطر الممكنة من السحابة استخدام Microsoft Security Graph. Defender for Endpoint هو نظام أساسي موحد للحماية الوقائية، والكشف بعد الخرق، والتحري التلقائي، والاستجابة. فهو يحمي نقاط النهاية من الهجمات الإلكترونية، ويكشف عن الهجمات المتقدمة وخرقات البيانات، ويأتمتة أحداث الأمان، ويحسن الوضع الأمني.
- [Microsoft Defender for Identity](/defender-for-identity/what-is) هو حل أمان مستند إلى السحابة يستخدم إشارات خدمات مجال Active Directory محلي (AD DS) لتحديد التهديدات المتقدمة والهويات المهينة والإجراءات الضارة ل insider الموجهة إلى مؤسستك والكشف عنها والتحقق من وجودها.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) بمثابة وسيط للوصول في الوقت الحقيقي بين مستخدمي المؤسسة وموارد السحابة التي يستخدمونها، أينما كان موقع المستخدمين وبصرف النظر عن الجهاز الذي يستخدمونه.
- [Microsoft Defender لـ Office 365](../office-365-security/overview.md) مؤسستك من التهديدات الضارة في رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون.
- [إن Azure Security Center](/azure/security-center/security-center-introduction) هو نظام موحد لإدارة أمان البنية الأساسية يقوي الوضع الأمني لمراكز البيانات ويوفر حماية متقدمة من المخاطر عبر أحمال العمل المختلطة في السحابة وعلى المستوى الداخلي.


في Microsoft 365 Defender[، يتم](incidents-overview.md) تحديد الأحداث من خلال ربط التنبيهات من مصادر الكشف المختلفة هذه. بدلا من إنفاق الموارد في سلسلة معا أو تمييز تنبيهات متعددة في الأحداث الخاصة بها، يمكنك البدء بقائمة انتظار الأحداث في Microsoft 365 Defender مباشرة. يسمح لك هذا النهج بفرز الأحداث بطريقة فعالة عبر نقاط النهاية والهويات والبريد الإلكتروني والتطبيقات، وتقليل الأضرار الناجمة عن هجوم.

## <a name="triage-your-incidents"></a>فرز الأحداث

يبدأ الرد على Microsoft 365 Defender عند فرز قائمة الأحداث باستخدام أسلوب تحديد الأولويات الموصى به في مؤسستك. يعني الفرز تعيين مستوى من الأهمية أو الإلحاح للحوادث، مما يحدد الترتيب الذي سيتم به التحقيق فيها.

يمكن تلخيص نموذج إرشادي مفيد لتحديد الحادث الذي يجب تحديد Microsoft 365 Defender حسب الصيغة: *الخطورة + التأثير = الأولوية*.

- **الخطورة** هي المستوى المعين بواسطة Microsoft 365 Defender ومكونات الأمان المتكاملة الخاصة بها.
- **يتم** تحديد التأثير بواسطة المؤسسة ويتضمن بشكل عام، على وجه المثال لا يقتصر على، عدد العتبات للمستخدمين المتأثرين والأجهزة والخدمات المتأثرة (أو مجموعة منها)، وحتى نوع التنبيه.

بعد ذلك، يقوم المحللون ببدء التحقيق استنادا **إلى معايير الأولوية** التي تحددها المؤسسة.

قد تختلف أولوية الأحداث استنادا إلى المؤسسة. توصي NIST أيضا بالنظر في التأثير الوظيفي والمعلوماتي للحادث وإمكانية استرداده.

تم وصف أحد النهج المتبعة للفرز أدناه:

1. انتقل إلى [صفحة الأحداث](incidents-overview.md) لبدء الفرز. يمكنك هنا رؤية قائمة بالحوادث التي تؤثر على مؤسستك. بشكل افتراضي، يتم ترتيبها من آخر حادث إلى أقدم حادث. من هنا، يمكنك أيضا رؤية أعمدة مختلفة لكل حادث تظهر خطورتها وفئة تنبيهاتها وعدد التنبيهات النشطة والكيانات ذات التأثير، من بين أعمدة أخرى. يمكنك تخصيص مجموعة الأعمدة وفرز قائمة انتظار الأحداث حسب بعض هذه الأعمدة عن طريق تحديد اسم العمود. يمكنك أيضا تصفية قائمة انتظار الأحداث وفقا لاحتياجاتك. للحصول على قائمة كاملة ب عوامل التصفية المتوفرة، راجع [تحديد أولوية الأحداث](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="الأحداث في مدخل Microsoft 365 الأمان" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    أحد الأمثلة على كيفية إجراء الفرز لهذه المجموعة من الأحداث هو إعطاء الأولوية للحوادث التي تؤثر على عدد أكبر من المستخدمين والأجهزة. في هذا المثال، قد تحدد أولوية الم ID 6769 للحادث لأنه يؤثر على أكبر عدد من الوحدات: سبعة أجهزة وستة مستخدمين و علب بريد. علاوة على ذلك، يبدو أن الحادث يحتوي على تنبيهات من Microsoft Defender for Identity تشير إلى تنبيه مستند إلى الهوية وسرقة بيانات الاعتماد المحتملة.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="تعرض صفحة &quot;الأحداث** مثال لحادث كبير التأثير في مدخل Microsoft 365 الأمان" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. حدد الدائرة المجاورة لاسم الحادث لمراجعة التفاصيل. سيظهر جزء جانبي على الجانب الأيسر، يحتوي على معلومات إضافية يمكن أن تساعد في إجراء الفرز بشكل أكبر.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="تعرض صفحة &quot;الأحداث&quot; مثالا عن جزء جانب الحادث في مدخل Microsoft 365 الأمان" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   على سبيل المثال، بالنظر إلى الأساليب التي يستخدمها [مهاجم&CK ل MITRE ATT&](https://attack.mitre.org/) استنادا إلى فئات الحادث، يمكنك تحديد أولوية هذا الحادث لأن المتطفل استخدم بيانات الاعتماد التي تمت سرقتها، وأنشأ الأمر والتحكم، وأ قام بإجراء حركة متلاحقة، وسحب بعض البيانات. تشير هذه الإجراءات إلى أن المهاجم قد تعمق بالفعل في الشبكة وربما سرق معلومات سرية.

   بالإضافة إلى ذلك، إذا نفذت مؤسستك ثقة معدومة العمل، يمكنك اعتبار الوصول إلى بيانات الاعتماد كانتهاك أمان هام يستحق تحديد أولوياته.

   عند التمرير لأسفل الجزء الجانبي، سترى الكيانات المحددة التي تم التأثير عليها مثل المستخدمين والأجهزة علب البريد. يمكنك التحقق من مستوى التعرض لكل جهاز وماالكي علب البريد المتأثرة.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="تفاصيل جزء جانب الحادث" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. في الجزء الجانبي، يمكنك العثور على التنبيهات المقترنة. Microsoft 365 Defender بالفعل ارتباط التنبيهات في حادث واحد، مما يوفر عليك الوقت والموارد التي تنفقها بشكل أفضل في معالجة الهجوم. التنبيهات مريبة، وبالتالي من المحتمل أن تكون أحداث النظام الضارة التي تشير إلى وجود مهاجم على شبكة.

   في هذا المثال، تم تحديد 87 تنبيها فرديا كجزء من حادث أمان واحد. يمكنك عرض كل التنبيهات للحصول على طريقة عرض سريعة حول كيفية تنفيذ الهجوم.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="التنبيهات في جزء جانب الحادث في مدخل Microsoft 365 الأمان" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>تحليل أول حادث

لا يقل عن ذلك أهمية فهم السياق الذي يحيط بالتنبيهات. غالبا ما لا يكون التنبيه حدثا مستقلا واحدا. هناك سلسلة من العمليات التي تم إنشاؤها والأوامر والإجراءات التي ربما لم تحدث في الوقت نفسه. وبالتالي، يجب على المحلل البحث عن الأنشطة الأولى والأخيرة للكيان المريب في المخططات الزمنية للجهاز لفهم سياق التنبيهات.

هناك طرق متعددة لقراءة البيانات وتحليلها باستخدام Microsoft 365 Defender ولكن الهدف النهائي للمحللين هو الاستجابة للحوادث بأسرع وقت ممكن. على Microsoft 365 Defender تقليل "وقت المعالجة[" (MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) بشكل ملحوظ من خلال ميزة الاستجابة والتحري التلقائي الرائدة في المجال، [](m365d-autoir.md) إلا أن هناك دائما حالات تتطلب تحليلا يدويا.

فيما يلي مثال على ذلك:

1. بعد تحديد أولوية الفرز، يبدأ المحلل تحليلا مفصلا عن طريق تحديد اسم الحادث. تعرض هذه الصفحة ملخص **الأحداث حيث يتم** عرض البيانات في علامات تبويب للمساعدة في التحليل. ضمن علامة **التبويب** تنبيهات، يتم عرض أنواع التنبيهات. يمكن للمحللين النقر فوق كل تنبيه للتنقيب لأسفل في مصدر الكشف الخاص به.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="علامة التبويب &quot;ملخص&quot; لحادث" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    للحصول على دليل سريع حول المجال الذي يغطيه كل مصدر للكشف، [راجع القسم كشف](#detection-by-microsoft-365-defender) من هذه المقالة.

2. من علامة **التبويب** تنبيهات، يمكنك المحور إلى مصدر الكشف لإجراء تحقيق وتحليل أكثر عمقا. على سبيل المثال، إن تحديد الكشف عن البرامج الضارة باستخدام Microsoft Defender for Cloud Apps كمصدر الكشف يأخذ المحلل إلى صفحة التنبيه المقابلة الخاصة به.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="صفحة &quot;الأحداث&quot; التي تعرض مثالا عن تحديد تنبيه لحادث." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="صفحة مقابلة في Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. للتحقق من مثالنا بشكل أكبر، قم بالتمرير إلى أسفل الصفحة لعرض **المستخدمين المتأثرين.** لمشاهدة النشاط والسياقات المحيطة بالكشف عن البرامج الضارة، حدد صفحة مستخدم Annette Hill.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="صفحة مستخدم" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. تسرد صفحة المستخدم الأحداث بشكل زمني، بدءا من تسجيل الدخول إلى المخاطر من *تنبيه عنوان IP لشبكة TOR* . على الرغم من أن ريبة النشاط تعتمد على طبيعة كيفية إدارة المؤسسة لنشاطها، في معظم الحالات، قد يعتبر استخدام "موجه البصل" (TOR)، وهو شبكة تسمح للمستخدمين باستعراض الويب بشكل مجهول، في بيئة المؤسسة غير محتمل للغاية وغير ضروري للعمليات العادية عبر الإنترنت.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="القائمة الزمنية للأحداث الخاصة بالمستخدم" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. يمكن تحديد كل تنبيه للحصول على مزيد من المعلومات حول النشاط. على سبيل المثال، يؤدي تحديد **النشاط من تنبيه عنوان IP ل Tor** إلى الوصول إلى الصفحة الخاصة بهذا التنبيه. Annette هي مسؤول Office 365 تشير إلى امتيازات مرتفعة وأن الحادث المصدر قد أدى إلى الوصول إلى معلومات سرية.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="تفاصيل التنبيهات الخاصة Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. من خلال تحديد تنبيهات أخرى، يمكنك الحصول على صورة كاملة للهجوم.

## <a name="next-step"></a>الخطوة التالية

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="الخيار &quot;إعادة المعالجة&quot; في الصفحة &quot;الاستجابة للحادث الأول&quot;" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

تعرف على [كيفية معالجة الأحداث](first-incident-remediate.md).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
