---
title: الخطوة 1. فرز الحادث الأول وتحليله
description: كيفية فرز الحدث الأول وبدء تحليله في Microsoft 365 Defender.
keywords: الحوادث، والتنبيهات، والتحقيق، والارتباط، والهجمات، والآلات، والأجهزة، والمستخدمين، والهويات، والهوية، وعلبة البريد، والبريد الإلكتروني، و365، وmicrosoft، وm365، والاستجابة للحوادث، والهجمات الإلكترونية
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
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 596966c7c1975ebb8f20b306be5e4ab0a34bd99e
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893628"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>الخطوة 1. فرز الحادث الأول وتحليله

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

بينما تقضي بعض الوقت في إنشاء وتنفيذ وصيانة إجراءات الأمان وفقا لمعايير المؤسسة، يمكنك إعداد حلول أمان لمساعدتك على تحديد المخاطر والتهديدات الأمنية بسرعة. يسمح لك Microsoft 365 Defender بالكشف عن الحوادث وفرزها والتحقيق فيها من خلال تجربتها ذات الجزء الواحد من الزجاج حيث يمكنك العثور على المعلومات التي تحتاجها لاتخاذ القرارات في الوقت المناسب.

بمجرد الكشف عن حادث أمني، يقدم Microsoft 365 Defender تفاصيل ستحتاجها لفرز حادث أو حوادث أو تحديد أولوياتها على الآخرين. بعد تحديد ترتيب الأولويات، يمكن للمحللين بعد ذلك تركيز طاقاتهم على التحقيق في الحالات المعينة لهم.

## <a name="detection-by-microsoft-365-defender"></a>الكشف عن طريق Microsoft 365 Defender

يتلقى Microsoft 365 Defender التنبيهات والأحداث من أنظمة أمان Microsoft الأساسية المتعددة كمصادر للكشف لإنشاء صورة شاملة وسياق للنشاط الضار. مصادر الكشف المحتملة هي:

- [Microsoft Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md) هو حل الكشف عن نقطة النهاية والاستجابة (EDR) الذي يستخدم برنامج الحماية من الفيروسات من Microsoft Defender والحماية المتقدمة من التهديدات الممكنة على السحابة باستخدام Microsoft Security Graph. Defender لنقطة النهاية هو نظام أساسي موحد للحماية الوقائية، والكشف بعد الاختراق، والتحقيق التلقائي، والاستجابة. فهو يحمي نقاط النهاية من التهديدات الإلكترونية، ويكشف عن الهجمات المتقدمة وخروقات البيانات، ويأتمتة الحوادث الأمنية، ويحسن الوضع الأمني.
- [Microsoft Defender for Identity](/defender-for-identity/what-is) هو حل أمان مستند إلى السحابة يستخدم إشارات خدمات المجال Active Directory محلي (AD DS) لتحديد التهديدات المتقدمة والهويات المخترقة والإجراءات الداخلية الضارة الموجهة إلى مؤسستك واكتشافها والتحقيق فيها.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) بمثابة أداة بوابة للتوسط في الوصول في الوقت الحقيقي بين مستخدمي المؤسسة وموارد السحابة التي يستخدمونها، أينما كان المستخدمون بغض النظر عن الجهاز الذي يستخدمونه.
- [Microsoft Defender لـ Office 365](../office-365-security/overview.md) تحمي مؤسستك من التهديدات الضارة في رسائل البريد الإلكتروني والارتباطات (عناوين URL) وأدوات التعاون.
- [مركز أمان Azure](/azure/security-center/security-center-introduction) هو نظام موحد لإدارة أمان البنية الأساسية يعزز الوضع الأمني لمراكز البيانات الخاصة بك ويوفر حماية متقدمة من التهديدات عبر أحمال العمل المختلطة الخاصة بك في السحابة وفي أماكن العمل.


في Microsoft 365 Defender، يتم تحديد [الحوادث](incidents-overview.md) عن طريق ربط التنبيهات من مصادر الكشف المختلفة هذه. بدلا من إنفاق موارد السلاسل معا أو تمييز تنبيهات متعددة في الحوادث الخاصة بها، يمكنك البدء مع قائمة انتظار الحوادث في Microsoft 365 Defender على الفور. يسمح لك هذا النهج بفرز الحوادث بطريقة فعالة عبر نقاط النهاية والهويات والبريد الإلكتروني والتطبيقات، وتقليل الضرر الناتج عن الهجوم.

## <a name="triage-your-incidents"></a>فرز الحوادث الخاصة بك

تبدأ الاستجابة للحوادث في Microsoft 365 Defender بمجرد فرز قائمة الحوادث باستخدام الأسلوب الموصى به لمؤسستك لتحديد الأولويات. إن الفرز يعني تعيين مستوى من الأهمية أو الضرورة العاجلة للحوادث، والتي تحدد بعد ذلك الترتيب الذي سيتم التحقيق فيه.

دليل نموذج مفيد لتحديد الحادث الذي يجب تحديد أولوياته في Microsoft 365 Defender يمكن تلخيصه بواسطة *الصيغة: Severity + Impact = Priority*.

- **الخطورة** هي المستوى المعين من قبل Microsoft 365 Defender ومكونات الأمان المتكاملة الخاصة به.
- يتم تحديد **التأثير** من قبل المؤسسة ويتضمن بشكل عام، على سبيل المثال لا الحصر، حدا لعدد المستخدمين المتأثرين والأجهزة والخدمات المتأثرة (أو مزيج منها)، وحتى نوع التنبيه.

ثم يبدأ المحللون التحقيقات بناء على معايير **الأولوية** التي تحددها المؤسسة.

قد يختلف ترتيب أولويات الحوادث وفقا للمؤسسة. توصي NIST أيضا بالنظر في التأثير الوظيفي والمعلوماتي للحادث، وقابلية الاسترداد.

يتم وصف نهج واحد للفرز أدناه:

1. انتقل إلى صفحة [الأحداث لبدء الفرز](incidents-overview.md) . يمكنك هنا الاطلاع على قائمة بالحوادث التي تؤثر على مؤسستك. بشكل افتراضي، يتم ترتيبها من الحدث الأحدث إلى الحدث الأقدم. من هنا، يمكنك أيضا رؤية أعمدة مختلفة لكل حادث تظهر خطورتها، وفئة، وعدد التنبيهات النشطة، والكيانات المتأثرة، من بين أمور أخرى. يمكنك تخصيص مجموعة الأعمدة وفرز قائمة انتظار الأحداث حسب بعض هذه الأعمدة عن طريق تحديد اسم العمود. يمكنك أيضا تصفية قائمة انتظار الحوادث وفقا لاحتياجاتك. للحصول على قائمة كاملة بعوامل التصفية المتوفرة، راجع [تحديد أولويات الحوادث](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="الحوادث في مدخل أمان Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    أحد الأمثلة على كيفية إجراء الفرز لهذه المجموعة من الحوادث هو تحديد أولويات الحوادث التي أثرت على المزيد من المستخدمين والأجهزة. في هذا المثال، قد تعطي الأولوية لمعرف الحدث 6769 لأنه أثر على أكبر عدد من الكيانات: سبعة أجهزة وستة مستخدمين وعلبتي بريد. وعلاوة على ذلك، يبدو أن الحادث يحتوي على تنبيهات من Microsoft Defender for Identity، والتي تشير إلى تنبيه قائم على الهوية وسرقة محتملة لبيانات الاعتماد.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="صفحة Incidents** تعرض مثالا لحادث شديد التأثير في مدخل أمان Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. حدد الدائرة الموجودة بجانب اسم الحدث لمراجعة التفاصيل. سيظهر جزء جانبي على الجانب الأيسر، والذي يحتوي على معلومات إضافية يمكن أن تساعد في الفرز بشكل أكبر.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="صفحة الحوادث تعرض مثالا لجزء جانب الحادث في مدخل أمان Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   على سبيل المثال، بالنظر إلى تكتيكات [MITRE ATT&CK](https://attack.mitre.org/) التي استخدمها المهاجم استنادا إلى فئات الحادث، قد تعطي الأولوية لهذا الحدث لأن المهاجم استخدم بيانات الاعتماد المسروقة، وثبت الأمر والتحكم، ونفذ حركة جانبية، وصادر بعض البيانات. تشير هذه الإجراءات إلى أن المهاجم قد تعمق بالفعل في الشبكة وربما قام بسرقة معلومات سرية.

   بالإضافة إلى ذلك، إذا نفذت مؤسستك إطار عمل ثقة معدومة، فستعتبر الوصول إلى بيانات الاعتماد خرقا أمنيا مهما يستحق تحديد أولوياته.

   بالتمرير لأسفل الجزء الجانبي، سترى الكيانات المحددة المتأثرة مثل المستخدمين والأجهزة وعلب البريد. يمكنك التحقق من مستوى التعرض لكل جهاز ومالكي علب البريد المتأثرة.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="تفاصيل جزء الحادث الجانبي" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. في الجزء الجانبي، يمكنك العثور على التنبيهات المقترنة. Microsoft 365 Defender قد نفذت بالفعل ارتباط التنبيهات المذكورة في حادث واحد، ما يوفر لك الوقت والموارد التي تقضيها بشكل أفضل في معالجة الهجوم. التنبيهات مريبة ومن ثم قد تكون أحداث نظام ضارة تشير إلى وجود مهاجم على شبكة.

   في هذا المثال، تم تحديد 87 تنبيها فرديا كجزء من حادث أمني واحد. يمكنك عرض جميع التنبيهات للحصول على عرض سريع لكيفية تشغيل الهجوم.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="التنبيهات في جزء جانب الحادث في مدخل أمان Microsoft 365" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>تحليل الحدث الأول

يعد فهم السياق الذي يحيط بالتنبيهات بنفس القدر من الأهمية. غالبا ما لا يكون التنبيه حدثا مستقلا واحدا. هناك سلسلة من العمليات التي تم إنشاؤها والأوامر والإجراءات التي ربما لم تحدث في نفس الوقت. لذلك، يجب على المحلل البحث عن الأنشطة الأولى والأخيرة للكيان المشبوه في الجداول الزمنية للجهاز لفهم سياق التنبيهات.

هناك طرق متعددة لقراءة البيانات وتحليلها باستخدام Microsoft 365 Defender ولكن الهدف النهائي للمحللين هو الاستجابة للحوادث في أسرع وقت ممكن. في حين أن Microsoft 365 Defender يمكن أن يقلل بشكل كبير [من متوسط الوقت للمعالجة (MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) من خلال ميزة [التحقيق والاستجابة التلقائية](m365d-autoir.md) الرائدة في الصناعة، هناك دائما حالات تتطلب تحليلا يدويا.

فيما يلي مثال على ذلك:

1. بمجرد تحديد أولوية الفرز، يبدأ المحلل تحليلا متعمقا عن طريق تحديد اسم الحدث. تعرض هذه الصفحة **"ملخص الحادث** " حيث يتم عرض البيانات في علامات التبويب للمساعدة في التحليل. ضمن علامة التبويب **«Alerts** »، يتم عرض أنواع التنبيهات. يمكن للمحللين النقر فوق كل تنبيه للتنقل لأسفل في مصدر الكشف المعني.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="علامة التبويب &quot;ملخص&quot; لحادث" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    للحصول على دليل سريع حول المجال الذي يغطيه كل مصدر اكتشاف، راجع قسم [الكشف](#detection-by-microsoft-365-defender) في هذه المقالة.

2. من علامة التبويب **«Alerts** »، يمكنك الانتقال إلى مصدر الكشف لإجراء تحقيق وتحليل أكثر تعمقا. على سبيل المثال، اختيار الكشف عن البرامج الضارة مع Microsoft Defender for Cloud Apps كمصدر الكشف يأخذ المحلل إلى صفحة التنبيه المقابلة له.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="صفحة الحوادث التي تعرض مثالا لتحديد تنبيه لحادث." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="صفحة مقابلة في Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. لمزيد من التحقيق في مثالنا، قم بالتمرير إلى أسفل الصفحة لعرض **المستخدمين المتأثرين**. لمشاهدة النشاط والسياق المحيطين بالكشف عن البرامج الضارة، حدد صفحة مستخدم Annette التل.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="صفحة مستخدم" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. تسرد صفحة المستخدم الأحداث ترتيبا زمنيا، بدءا من *تسجيل الدخول المحفوفة بالمخاطر من تنبيه عنوان IP لشبكة TOR* . في حين أن ريبة النشاط تعتمد على طبيعة كيفية إدارة المؤسسة لأعمالها، في معظم الحالات، قد يعتبر استخدام جهاز توجيه Onion (TOR)، وهو شبكة تسمح للمستخدمين باستعراض الويب مجهول الهوية، في بيئة المؤسسة أمرا غير محتمل للغاية وغير ضروري للعمليات العادية عبر الإنترنت.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="قائمة الأحداث الزمنية لمستخدم" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. يمكن تحديد كل تنبيه للحصول على مزيد من المعلومات حول النشاط. على سبيل المثال، يؤدي تحديد **النشاط من تنبيه عنوان IP Tor** إلى الصفحة الخاصة بهذا التنبيه. Annette هي مسؤول Office 365، والتي تشير إلى امتيازات مرتفعة وأن الحادث المصدر قد أدى إلى الوصول إلى معلومات سرية.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="تفاصيل التنبيهات الخاصة Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. من خلال تحديد تنبيهات أخرى، يمكنك الحصول على صورة كاملة للهجوم.

## <a name="next-step"></a>الخطوة التالية

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="خيار المعالجة في صفحة الاستجابة للحدث الأول" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

تعرف على كيفية [معالجة الحوادث](first-incident-remediate.md).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
