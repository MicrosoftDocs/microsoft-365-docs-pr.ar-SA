---
title: التخطيط لمشروع Microsoft 365 Defender التجريبي
description: خطط لمشروعك التجريبي Microsoft 365 Defender مع المساهمين لإدارة التوقعات وضمان نتائج ناجحة.
keywords: Microsoft 365 Defender التجريبي، تخطيط مشروع تجريبي Microsoft 365 Defender، تقييم Microsoft 365 Defender الإنتاج، Microsoft 365 Defender  مشروع تجريبي، أمان عبر الإنترنت، تهديدات ثابتة متقدمة، أمان المؤسسة، الأجهزة، الجهاز، الهوية، المستخدمون، البيانات، التطبيقات، الحوادث، التحقيق التلقائي وا الإصلاح، الصيد المتقدم
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6a52df8035ce6f84770a2d06c3b8c127e426622e
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63572303"
---
# <a name="planning-your-pilot-microsoft-365-defender-project"></a>التخطيط لمشروع Microsoft 365 Defender التجريبي 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

|![التخطيط](../../media/phase-diagrams/1-planning.png)<br/>التخطيط|[![التحضير](../../media/phase-diagrams/2-prepare.png)](prepare-m365d-eval.md)<br/>[التحضير](prepare-m365d-eval.md) | [![محاكاة هجوم](../../media/phase-diagrams/3-simluate.png)](m365d-pilot-simulate.md)<br/>[محاكاة هجوم](m365d-pilot-simulate.md) | [![إغلاق وتلخيص](../../media/phase-diagrams/4-summary.png)](m365d-pilot-close.md)<br/>[إغلاق وتلخيص](m365d-pilot-close.md)|
|--|--|--|--|
|*أنت هنا!*| | | |

أنت حاليا في مرحلة التخطيط.

لضمان نجاح مشروعك التجريبي، من الضروري التخطيط جيدا والحصول على الموافقات من المساهمين في البداية. تتضمن عناصر التخطيط تحديد النطاق، حالات الاستخدام، والمتطلبات، ومعايير النجاح.

يرشدك هذا الدليل إلى كيفية التخطيط لمشروعك التجريبي. 

>[!IMPORTANT]
>للحصول على أفضل النتائج، اتبع إرشادات التجربة قدر الإمكان.


## <a name="scope"></a>النطاق

سيحدد نطاق التجربة مدى توسيع الاختبار، استنادا إلى بيئتك وأساليب الاختبار المقبولة. فيما يلي بعض أمثلة النطاقات التي يجب التفكير فيها:

- بيئة التطوير أو الاختبار التي تتضمن نقاط النهاية، الخوادم، وحدات التحكم بالمجال.
- بيئة الإنتاج مع Microsoft 365 و Azure وخدمات Active Directory ونقاط النهاية و الخوادم

>[!NOTE]
>إذا لم يكن لديك التراخيص الكاملة بعد، يمكنك الحصول على تراخيص تجريبية لتقييم [Microsoft 365 Defender – تخطيط](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) مشروع الإصدار التجريبي وإعداده وإعداده وتكوينه وتشغيله. سيلعب المساهمين دورا كبيرا في المساعدة على تسهيل العملية من البداية إلى النهاية.

يجب أيضا تعريف أنواع أنظمة التشغيل التي يجب تقييمها استنادا إلى التركيبة التنظيمية. قد يتضمن ذلك ما يلي: [نقاط نهاية Mac](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements) و Linux [Servers](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements) [Windows 10 نقاط](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions) النهاية و [Windows Server 2016](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions).

## <a name="use-cases"></a>استخدام الحالات

تمثل حالات الاستخدام عبارات حول كيفية استخدام الأداة التي يتم اختبارها من قبل المستخدمين المقصودين. يمكن استخدام هذه القصص ك قصص مستخدم من وجهة نظر شخص معين، مثل محلل SOC. على سبيل المثال:

- كمحلل SOC، أحتاج إلى عرض التنبيهات والأحداث وربطها وتقييمها وإدارتها عبر الأجهزة والمستخدمين علب البريد في شبكتي. [إدارة الحوادث]
- كمحلل SOC، يجب أن يكون لدي الأداة وا العملية للتحقق تلقائيا من الأحداث الضارة في شبكتي والاستجابة لها. [IR التلقائي]
- كمحلل SOC، يجب البحث في البيانات من بيئتي للعثور على التهديدات المعروفة والمحتملة والأنشطة المريبة. [متقدمة للصيد]

ضع في اعتبارك أنه يجب إنشاء حالات الاستخدام هذه ضمن معلمات النطاق المحدد. إذا كان نطاق الاختبار، على سبيل المثال، لا يتضمن تقييما لأدوات مثل Microsoft Cloud App Security، فينبغي عدم إنشاء الحالات التي تعتمد على ذلك كمصدر بيانات.

## <a name="requirements"></a>المتطلبات

من قائمة حالات الاستخدام، يمكنك البدء في إنشاء متطلبات. تتضمن المتطلبات الميزات التي يجب أن تحتوي عليها الأداة لتلبية حالات الاستخدام. يمكن تقسيم هذه المتطلبات إلى فئات مثل التكوين والصيانة ودعم عمليات التكامل والمتطلبات الخاصة بالميزات مثل القدرة على الصيد والقدرة على إنشاء تنبيهات مخصصة.

## <a name="test-plan"></a>خطة الاختبار

استنادا إلى المتطلبات، قد تكون أساليب الاختبار المختلفة مناسبة. على سبيل المثال، إذا كان المتطلب هو تقييم فعالية المعالجة التلقائية، يجب أن تتضمن خطة الاختبار خطوات لإنشاء السلوك (السلوك) الذي يؤدي إلى تشغيل إجراء المعالجة التلقائية ضمن Microsoft 365 Defender. إذا كان المتطلب هو الكشف عن سلوك معين أو هجوم معين، فقد يتضمن الاختبار خطوات إضافية. الهدف هو وضع خطة لاختبارها بدقة مقابل متطلباتك.

## <a name="success-criteria"></a>معايير النجاح

معايير النجاح هي في النهاية الشريط الذي تم تعيينه لقياس مقابل ما تقوم باختباره. سواء كنت تقوم Microsoft 365 Defender (أو أي تقنية أخرى في هذه المسألة) مقابل أدوات أخرى أو بحد ذاتها، يجب أن تكون هناك بعض المعايير القابلة للقياس لتحديد القيمة التي تقدمها الأداة. استنادا إلى النطاق والمتطلبات خطة الاختبار، ستحدد معايير النجاح كيفية تسجيل الاختبار. يجب أن يكون هذا أقل من تمريرة أو فشل والمزيد من نقاط المرجحة استنادا إلى احتياجاتك. على سبيل المثال، لكي تكون الأداة ناجحة، قد تحتاج إلى تسجيل نقاط أعلى من 80٪ في بعض المناطق الهامة التي تحددها.

## <a name="scorecard"></a>بطاقة الأداء

يمكن أن تكون إحدى الطرق التي يمكن من خلالها جمع كل عناصر خطتك معا هي إنشاء بطاقة الأداء. راجع نموذج بطاقة الأداء أدناه:

| حالة الاستخدام | المتطلبات | متطلبات التكوين | خطة الاختبار | النتيجة المتوقعة | حالة الاختبار | النتيجة | ملاحظات |
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|إدارة الحوادث|- Microsoft 365 Defender </br></br>- Microsoft Defender for Identity </br></br>- Microsoft Defender لنقطة النهاية </br></br>- Microsoft Cloud App Security (اختياري)|راجع [المتطلبات الأساسية](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) لإعداد الإعداد والإعداد والتكوين للحصول على التفاصيل |[محاكاة هجوم](m365d-pilot-simulate.md) <br></br>[التحقق من الحادث](./m365d-pilot-simulate.md#investigate-an-incident) |يمكن للمشتبهين فهم نطاق الحادث وتأثيره وإدارة الحادث||||
|AutoIR|- Microsoft 365 Defender </br></br>- Microsoft Defender for Identity </br></br>- Microsoft Defender لنقطة النهاية |راجع [المتطلبات الأساسية](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) لإعداد الإعداد والإعداد والتكوين للحصول على التفاصيل <br>تمكين AutoIR  |[محاكاة هجوم](m365d-pilot-simulate.md) <br></br>[التحقيق التلقائي](m365d-pilot-simulate.md#automated-investigation-and-remediation) |يتم تلقائيا معالجة التنبيهات والحوادث بواسطة Microsoft 365 Defender||||
|الصيد المتقدم|- Microsoft 365 Defender </br></br>- Microsoft Defender لنقطة النهاية </br></br>-Microsoft Defender Office 365 |راجع [المتطلبات الأساسية](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) لإعداد الإعداد والإعداد والتكوين للحصول على التفاصيل|[سيناريو الصيد المتقدم](./m365d-pilot-simulate.md#advanced-hunting-scenario) |يمكن للمشتبهين العثور على البيانات من خلال البحث المتقدم، وال محور الكيانات المعنية، وإنشاء اكتشافات مخصصة||||

## <a name="next-step"></a>الخطوة التالية

|![مرحلة الإعداد](../../media/mtp/prep.png) <br>[مرحلة الإعداد](prepare-m365d-eval.md) | تحضير بيئة Microsoft 365 Defender التجريبية
|:-------|:-----|
