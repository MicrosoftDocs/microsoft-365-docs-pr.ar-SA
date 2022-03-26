---
title: كيفية عمل الاستجابات والتحري التلقائي في Microsoft Defender Office 365
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
keywords: الاستجابة التلقائية للحوادث، التحقيق، المعالجة، الحماية من المخاطر
ms.date: 01/29/2021
description: تعرف على كيفية عمل قدرات الاستجابة والتحري التلقائي في Microsoft Defender Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ee046815f681b327fbcceaedf9033af9bfa5e109
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566939"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>كيفية عمل الاستجابات والتحري التلقائي في Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

عند تشغيل تنبيهات الأمان، الأمر متروك لفريق عمليات الأمان للنظر في هذه التنبيهات واتخاذ خطوات لحماية مؤسستك. في بعض الأحيان، قد تشعر فرق عمليات الأمان بالارتباك بسبب حجم التنبيهات التي يتم تشغيلها. يمكن أن تساعدك قدرات الاستجابة (AIR) والتحري التلقائي في Microsoft Defender Office 365.

تمكن AIR فريق عمليات الأمان من العمل بفعالية وفعالية أكبر. تتضمن قدرات AIR عمليات التحقيق التلقائية استجابة للتهديدات المعروفة الموجودة اليوم. تنتظر إجراءات المعالجة المناسبة الموافقة، مما يمكن فريق عمليات الأمان من الاستجابة للتهديدات التي تم الكشف عنها.

تصف هذه المقالة كيفية عمل AIR من خلال أمثلة متعددة. عندما تكون جاهزا للبدء باستخدام AIR، راجع التحقق تلقائيا من التهديدات [والرد عليها](office-365-air.md).

- [مثال 1: تقوم رسالة التصيد الاحتيالي التي تم تسجيلها من قبل المستخدم بتحري مصنف تشغيل التحقيق](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [المثال 2: يقوم مسؤول الأمان بتشغيل تحقيق من "مستكشف التهديدات"](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [المثال 3: يدمج فريق عمليات الأمان AIR مع SIEM باستخدام Office 365 API لنشاط الإدارة](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>مثال: تقوم رسالة التصيد الاحتيالي التي تم إعلام المستخدم بها بإطلاق مصنف تشغيل التحقيق

لنفترض أن أحد المستخدمين في مؤسستك يتلقى رسالة بريد إلكتروني يعتقد أنها محاولة تصيد احتيالي. يستخدم المستخدم، الذي تم تدريبه على الإبلاغ عن مثل هذه الرسائل، الوظائف الإضافية ["](enable-the-report-message-add-in.md)رسالة التقرير[](enable-the-report-phish-add-in.md)" أو "الإبلاغ عن التصيد الاحتيالي" لإرسالها إلى Microsoft لتحليلها. يتم أيضا إرسال الإرسال إلى النظام الخاص بك، كما يكون مرئيا في المستكشف  في طريقة عرض الواجبات المرسلة (يشار إليها سابقا باسم طريقة العرض **التي** تم إعلام المستخدم بها). بالإضافة إلى ذلك، تقوم الرسالة التي تم إعلام المستخدم بها الآن بتشغيل تنبيه إعلامي يستند إلى النظام، والذي يقوم بتشغيل دفتر تشغيل التحقيق تلقائيا.

أثناء مرحلة التحقيق الجذر، يتم تقييم جوانب مختلفة من البريد الإلكتروني. تتضمن هذه الجوانب:

- تحديد نوع الخطر الذي قد يشكله؛
- روبوت Who إرساله؛
- المكان الذي تم إرسال البريد الإلكتروني منه (إرسال البنية الأساسية)؛
- ما إذا كان قد تم تسليم مثيلات أخرى من البريد الإلكتروني أو حظره؛
- تقييم من المحللين لدينا؛
- ما إذا كان البريد الإلكتروني مقترن بأي حملات معروفة؛
- والمزيد.

بعد اكتمال عملية البحث الجذر، يوفر دفتر التشغيل قائمة بالأفعال الموصى بها التي يجب اتخاذها على البريد الإلكتروني الأصلي والكيانات المقترنة به.

بعد ذلك، يتم تنفيذ عدة خطوات للتحري عن المخاطر والصيد:

- يتم تحديد رسائل بريد إلكتروني مماثلة عبر عمليات البحث عن مجموعات البريد الإلكتروني.
- يتم مشاركة الإشارة مع الأنظمة الأساسية الأخرى، [مثل Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- يتم تحديد ما إذا كان أي مستخدم قد قام بالنقر عبر أي ارتباطات ضارة في رسائل البريد الإلكتروني المريبة.
- يتم إجراء فحص عبر Exchange Online Protection ([EOP](exchange-online-protection-overview.md) و([Microsoft Defender for Office 365](defender-for-office-365.md) لمعرفة ما إذا كانت هناك أي رسائل مماثلة أخرى تم تسجيلها من قبل المستخدمين.
- يتم إجراء فحص لمعرفة ما إذا تم اختراق مستخدم. تستفيد عملية الاختيار هذه من الإشارات عبر Office 365 [و Microsoft Defender لتطبيقات](/cloud-app-security) السحابة و [Azure Active Directory](/azure/active-directory)، مما يرتبط بأي تشوهات متعلقة بنشاط المستخدم.

أثناء مرحلة الصيد، يتم تعيين المخاطر والمخاطر إلى خطوات مختلفة للصيد.

المعالجة هي المرحلة الأخيرة من المصنف. خلال هذه المرحلة، يتم اتخاذ خطوات المعالجة، استنادا إلى مراحل البحث والصيد.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>مثال: يقوم مسؤول الأمان بتشغيل تحقيق من "مستكشف التهديدات"

بالإضافة إلى عمليات التحقيق التلقائية التي يتم تشغيلها بواسطة تنبيه، يمكن لفريق عمليات الأمان في مؤسستك تشغيل تحقيق تلقائي من طريقة عرض في "مستكشف [التهديدات](threat-explorer.md)".  ينشئ هذا التحقيق أيضا تنبيها، بحيث Microsoft 365 Defender الأحداث وأدوات SIEM الخارجية أن هذا التحقيق قد تم.

على سبيل المثال، افترض أنك تستخدم طريقة عرض **البرامج الضارة في** المستكشف. باستخدام علامات التبويب الموجودة أسفل المخطط، حدد علامة **التبويب البريد** الإلكتروني. إذا قمت بتحديد عنصر واحد أو أكثر في القائمة، يتم تنشيط **الزر +** إجراءات.

![مستكشف مع رسائل محددة.](../../media/Explorer-Malware-Email-ActionsInvestigate.png)

باستخدام القائمة **إجراءات** ، يمكنك تحديد **تشغيل التحقيق**.

![قائمة الإجراءات للرسائل المحددة.](../../media/explorer-malwareview-selectedemails-actions.jpg)

على غرار دفاتر التشغيل التي يتم تشغيلها بواسطة تنبيه، تتضمن عمليات التحقيق التلقائية التي يتم تشغيلها من طريقة عرض في "المستكشف" إجراء تحقيق جذري، والخطوات اللازمة لتحديد التهديدات وربطها، والإجراءات الموصى بها للحد من هذه التهديدات.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>مثال: يدمج فريق عمليات الأمان AIR مع SIEM باستخدام Office 365 API لنشاط الإدارة

تتضمن قدرات AIR في Microsoft Defender Office 365 تقارير & يمكن لفرق عمليات الأمان استخدامها لمراقبة التهديدات ومعالجتها.[](air-view-investigation-results.md) ولكن يمكنك أيضا دمج قدرات AIR مع الحلول الأخرى. تتضمن الأمثلة نظام معلومات الأمان وإدارة الأحداث (SIEM) أو نظام إدارة الحالات أو حل إعداد التقارير المخصص. يمكن القيام بهذه الأنواع من عمليات التكامل [باستخدام Office 365 API لنشاط الإدارة](/office/office-365-management-api/office-365-management-activity-api-reference).

على سبيل المثال، مؤخرا، تقوم مؤسسة بإعداد طريقة لفريق عمليات الأمان لعرض تنبيهات التصيد الاحتيالي التي تم إعدادها من قبل المستخدم التي تمت معالجتها بواسطة AIR. يتكامل حلها مع التنبيهات ذات الصلة مع خادم SIEM الخاص بالم المؤسسة ونظام إدارة حالاتها. يقلل الحل إلى حد كبير من عدد الإيجابيات الخاطئة بحيث يمكن لفريق عمليات الأمان تركيز وقته وجهده على التهديدات الحقيقية. لمعرفة المزيد حول هذا الحل المخصص، راجع مدونة المجتمع التقني: تحسين فعالية [SOC باستخدام Microsoft Defender Office 365 و API لإدارة O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>الخطوات التالية

- [بدء استخدام AIR](office-365-air.md)
- [عرض إجراءات المعالجة المعلقة أو المكتملة](air-review-approve-pending-completed-actions.md)
