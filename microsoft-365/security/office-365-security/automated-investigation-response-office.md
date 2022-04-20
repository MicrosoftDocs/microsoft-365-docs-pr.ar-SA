---
title: كيفية عمل التحقيق والاستجابة الآليين في Microsoft Defender لـ Office 365
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
keywords: الاستجابة التلقائية للحوادث والتحقيق والمعالجة والحماية من التهديدات
ms.date: 01/29/2021
description: تعرف على كيفية عمل قدرات التحقيق والاستجابة التلقائية في Microsoft Defender لـ Office 365
ms.custom:
- air
- seo-marvel-mar2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78dc31c055f563f0f9f03bcf12642296459de491
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974224"
---
# <a name="how-automated-investigation-and-response-works-in-microsoft-defender-for-office-365"></a>كيفية عمل التحقيق والاستجابة الآليين في Microsoft Defender لـ Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

مع تشغيل تنبيهات الأمان، يعود الأمر إلى فريق عمليات الأمان لديك للنظر في هذه التنبيهات واتخاذ خطوات لحماية مؤسستك. في بعض الأحيان، يمكن أن تشعر فرق عمليات الأمان بالإرهاق بسبب حجم التنبيهات التي يتم تشغيلها. يمكن أن تساعد قدرات التحقيق والاستجابة التلقائية (AIR) في Microsoft Defender لـ Office 365.

يتيح AIR لفريق عمليات الأمان لديك العمل بفعالية وفعالية أكبر. تتضمن قدرات AIR عمليات التحقيق التلقائية استجابة للتهديدات المعروفة الموجودة اليوم. تنتظر إجراءات المعالجة المناسبة الموافقة، ما يتيح لفريق عمليات الأمان لديك الاستجابة للتهديدات المكتشفة.

تصف هذه المقالة كيفية عمل AIR من خلال عدة أمثلة. عندما تكون مستعدا لبدء استخدام AIR، راجع [التحقيق التلقائي في التهديدات والاستجابة لها](office-365-air.md).

- [مثال 1: رسالة تصيد احتيالي أبلغ عنها المستخدم تطلق دليل مبادئ التحقيق](#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- [مثال 2: يقوم مسؤول الأمان بتشغيل تحقيق من مستكشف التهديدات](#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)
- [مثال 3: يدمج فريق عمليات الأمان AIR مع SIEM الخاص بهم باستخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365](#example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api)

## <a name="example-a-user-reported-phish-message-launches-an-investigation-playbook"></a>مثال: رسالة تصيد احتيالي تم الإبلاغ عنها من قبل المستخدم تطلق دليل مبادئ التحقيق

لنفترض أن المستخدم في مؤسستك يتلقى رسالة بريد إلكتروني يعتقد أنها محاولة تصيد احتيالي. يستخدم المستخدم، المدرب على الإبلاغ عن مثل هذه الرسائل، [الوظيفة الإضافية "رسالة التقرير](enable-the-report-message-add-in.md) " أو [الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي](enable-the-report-phish-add-in.md) " لإرسالها إلى Microsoft للتحليل. يتم أيضا إرسال عمليات الإرسال إلى النظام الخاص بك وتكون مرئية في "المستكشف" في طريقة عرض **"عمليات الإرسال** " (يشار إليها سابقا بطريقة العرض **التي تم الإبلاغ عنها من قبل المستخدم** ). بالإضافة إلى ذلك، تؤدي الرسالة التي أبلغ عنها المستخدم الآن إلى تشغيل تنبيه إعلامي يستند إلى النظام، والذي يقوم تلقائيا بتشغيل دليل مبادئ التحقيق.

في أثناء مرحلة التحقيق الجذر، يتم تقييم جوانب مختلفة من البريد الإلكتروني. وتشمل هذه الجوانب ما يلي:

- تحديد نوع التهديد الذي قد يكون عليه؛
- روبوت Who إرساله؛
- المكان الذي تم إرسال البريد الإلكتروني منه (إرسال البنية الأساسية)؛
- ما إذا تم تسليم مثيلات أخرى للبريد الإلكتروني أو حظرها؛
- تقييم من محللينا؛
- ما إذا كان البريد الإلكتروني مقترنا بأي حملات معروفة؛
- والمزيد.

بعد اكتمال التحقيق الجذر، يوفر دليل المبادئ قائمة بالإجراءات الموصى بها لاتخاذها على البريد الإلكتروني الأصلي والكيانات المقترنة به.

بعد ذلك، يتم تنفيذ العديد من خطوات التحقيق في التهديدات والتتبع:

- يتم تعريف رسائل البريد الإلكتروني المماثلة عبر عمليات البحث في مجموعة البريد الإلكتروني.
- تتم مشاركة الإشارة مع أنظمة أساسية أخرى، مثل [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection).
- يتم تحديد ما إذا كان أي مستخدم قد نقر عبر أي ارتباطات ضارة في رسائل البريد الإلكتروني المشبوهة.
- يتم إجراء فحص عبر Exchange Online Protection ([EOP](exchange-online-protection-overview.md) و([Microsoft Defender لـ Office 365](defender-for-office-365.md) لمعرفة ما إذا كان هناك أي رسائل أخرى مماثلة أبلغ عنها المستخدمون.
- يتم إجراء فحص لمعرفة ما إذا كان قد تم اختراق مستخدم. يستفيد هذا الفحص من الإشارات عبر Office 365 [Microsoft Defender for Cloud Apps](/cloud-app-security) [وAzure Active Directory](/azure/active-directory)، ما يرتبط بأي حالات غير طبيعية متعلقة بنشاط المستخدم.

في أثناء مرحلة التتبع، يتم تعيين المخاطر والتهديدات إلى خطوات التتبع المختلفة.

المعالجة هي المرحلة النهائية من دليل المبادئ. خلال هذه المرحلة، يتم اتخاذ خطوات المعالجة، استنادا إلى مرحلتي التحقيق والتتبع.

## <a name="example-a-security-administrator-triggers-an-investigation-from-threat-explorer"></a>مثال: يقوم مسؤول الأمان بتشغيل تحقيق من مستكشف التهديدات

بالإضافة إلى التحقيقات التلقائية التي يتم تشغيلها بواسطة تنبيه، يمكن لفريق عمليات الأمان في مؤسستك تشغيل تحقيق تلقائي من طريقة عرض في [مستكشف التهديدات](threat-explorer.md). ينشئ هذا التحقيق أيضا تنبيها، لذلك Microsoft 365 Defender الحوادث وأدوات SIEM الخارجية يمكن أن ترى أنه تم تشغيل هذا التحقيق.

على سبيل المثال، افترض أنك تستخدم طريقة عرض **البرامج الضارة** في Explorer. باستخدام علامات التبويب أسفل المخطط، يمكنك تحديد علامة التبويب **"بريد إلكتروني** ". إذا قمت بتحديد عنصر واحد أو أكثر في القائمة، يتم تنشيط الزر **+Actions** .

:::image type="content" source="../../media/Explorer-Malware-Email-ActionsInvestigate.png" alt-text="المستكشف مع الرسائل المحددة" lightbox="../../media/Explorer-Malware-Email-ActionsInvestigate.png":::

باستخدام قائمة **الإجراءات** ، يمكنك تحديد **«Trigger investigation»**.

:::image type="content" source="../../media/explorer-malwareview-selectedemails-actions.jpg" alt-text="القائمة &quot;إجراءات&quot; للرسائل المحددة" lightbox="../../media/explorer-malwareview-selectedemails-actions.jpg":::

على غرار أدلة المبادئ التي يتم تشغيلها بواسطة تنبيه، تتضمن التحقيقات التلقائية التي يتم تشغيلها من طريقة عرض في Explorer تحقيق جذر، وخطوات لتحديد التهديدات وربطها، والإجراءات الموصى بها للتخفيف من تلك التهديدات.

## <a name="example-a-security-operations-team-integrates-air-with-their-siem-using-the-office-365-management-activity-api"></a>مثال: يدمج فريق عمليات الأمان AIR مع SIEM الخاص بهم باستخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365

تتضمن قدرات AIR في Microsoft Defender لـ Office 365 [تقارير & التفاصيل](air-view-investigation-results.md) التي يمكن لفرق عمليات الأمان استخدامها لمراقبة التهديدات ومعالجتها. ولكن يمكنك أيضا دمج قدرات AIR مع حلول أخرى. تتضمن الأمثلة نظام إدارة معلومات الأمان والأحداث (SIEM) أو نظام إدارة الحالة أو حل إعداد التقارير المخصص. يمكن إجراء هذه الأنواع من عمليات التكامل باستخدام [واجهة برمجة تطبيقات نشاط الإدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

على سبيل المثال، قامت مؤسسة مؤخرا بإعداد طريقة لفريق عمليات الأمان لعرض تنبيهات التصيد الاحتيالي التي أبلغ عنها المستخدم والتي تمت معالجتها بالفعل بواسطة AIR. يدمج حلهم التنبيهات ذات الصلة مع خادم SIEM الخاص بالمؤسسة ونظام إدارة الحالة الخاص بهم. يقلل الحل إلى حد كبير من عدد الإيجابيات الخاطئة بحيث يمكن لفريق عمليات الأمان تركيز وقتهم وجهدهم على التهديدات الحقيقية. لمعرفة المزيد حول هذا الحل المخصص، راجع [مدونة المجتمع التقني: تحسين فعالية SOC باستخدام Microsoft Defender لـ Office 365 وواجهة برمجة تطبيقات إدارة O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).

## <a name="next-steps"></a>الخطوات التالية

- [بدء استخدام AIR](office-365-air.md)
- [عرض إجراءات المعالجة المعلقة أو المكتملة](air-review-approve-pending-completed-actions.md)
