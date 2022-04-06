---
title: تحضير وضع الأمان لحادثك الأول
description: قم بإعداد Microsoft 365 أمان المستأجر لأول مرة في Microsoft 365 Defender.
keywords: الأحداث والتنبيهات والتحري والارتباط والهجمة والأجهزة والأجهزة والمستخدمين والهويات والهوية علبة البريد والبريد الإلكتروني و365 و microsoft و m365
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
ms.openlocfilehash: 92b7efdad61a4738310d5fb469400033f78363a8
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570140"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>تحضير وضع الأمان لحادثك الأول

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يتضمن التحضير لمعالجة الحوادث إعداد حماية كافية لشبكة المؤسسة من أنواع مختلفة من أحداث الأمان. لتقليل مخاطر الحوادث الأمنية، يوصي "المؤسسة الوطنية للمعايير والتكنولوجيا" (NIST) بعدة ممارسات أمان بما في ذلك تقييمات المخاطر، وتقييد أمان المضيف، وتكوين الشبكات بأمان، ومنع البرامج الضارة. 

Microsoft 365 Defender المساعدة في معالجة جوانب متعددة من منع الحوادث: 

- تنفيذ إطار [عمل Confiança zero](/security/zero-trust/) جديد
- تحديد وضع الأمان من خلال تعيين درجة باستخدام [Microsoft Secure Score](microsoft-secure-score.md)
- منع التهديدات من خلال تقييمات الضعف في إدارة المخاطر [والضعف](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- فهم التهديدات الأمنية الأخيرة حتى تتمكن من التحضير لها باستخدام [تحليلات التهديدات](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>الخطوة 1. تنفيذ Confiança zero

[Confiança zero](/security/zero-trust/) هي إحدى فلسفات الأمان المتكاملة والاستراتيجية الشاملة التي تفكر في الطبيعة المعقدة لأي بيئة حديثة، بما في ذلك القوة العاملة المتنقلة والمستخدمين والأجهزة والتطبيقات والبيانات، أينما كانوا. من خلال توفير جزء واحد من الزجاج لإدارة كل عمليات الكشف بطريقة متناسقة، يمكن Microsoft 365 Defender أن يسهل على فريق عمليات الأمان تنفيذ المبادئ التوجيهية Confiança zero.[](/security/zero-trust/#guiding-principles-of-zero-trust) 

يمكن لمكونات Microsoft 365 Defender عرض انتهاكات القواعد التي تم تنفيذها لإنشاء سياسات الوصول الشرطي Confiança zero عن طريق دمج البيانات من Microsoft Defender لنقطة النهاية  أو موردو أمان الأجهزة المحمولة الآخرين كمصدر معلومات لنهج توافق الأجهزة وتنفيذ سياسات الوصول الشرطي المستندة إلى الجهاز. 

تؤثر مخاطر الجهاز بشكل مباشر على الموارد التي يمكن لمستخدم هذا الجهاز الوصول إليها. إن رفض الوصول إلى الموارد استنادا إلى معايير معينة هو النسق الرئيسي Confiança zero يوفر Microsoft 365 Defender المعلومات اللازمة لتحديد معايير مستوى الثقة. على سبيل المثال، Microsoft 365 Defender توفير مستوى إصدار البرنامج لجهاز من خلال صفحة إدارة المخاطر والهشاشة في حين تقيد سياسات الوصول الشرطي الأجهزة التي تحتوي على إصدارات قديمة أو ضعيفة.

التنفيذ التلقائي هو جزء أساسي من تنفيذ بيئة Confiança zero والحفاظ عليها مع تقليل عدد التنبيهات التي من المحتمل أن تؤدي إلى أحداث الاستجابة للحوادث (IR). يمكن أن يتم Microsoft 365 Defender عناصر الكمبيوتر التلقائية مثل إجراءات [المعالجة (المعروفة](m365d-autoir.md) بتحريات حادث في مدخل Microsoft 365 Defender) والإجراءات الإعلامية وحتى إنشاء تذاكر الدعم كما في [ServiceNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>الخطوة 2. تحديد الوضع الأمني لمنظمتك

بعد ذلك، يمكن أن تستخدم المؤسسات [Microsoft Secure Score](microsoft-secure-score.md) في Microsoft 365 Defender لتحديد وضع الأمان الحالي لديك ودرس التوصيات المتعلقة بكيفية تحسينه. كلما كانت النتيجة أعلى، زادت توصيات الأمان والإجراءات التي اتخذتها المؤسسة. يمكن الحصول على توصيات "نقاط آمنة" عبر منتجات مختلفة والسماح ل المؤسسات برفع نقاطها إلى مستوى أعلى. 

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="صفحة Microsoft Secure Score في مدخل Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::
 
## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>الخطوة 3. تقييم التعرض للضعف في مؤسستك

من الممكن أن يساعد منع الحوادث على تنظيم جهود عمليات الأمان للتركيز على أحداث الأمان الهامة والحرجة. غالبا ما تكون نقاط الضعف في البرامج نقطة إدخال يمكن منعها للهجمات التي يمكن أن تؤدي إلى سرقة البيانات أو فقدان البيانات أو تعطيل عمليات الأعمال. إذا لم تكن هناك أي هجمات مقبلة، فيجب أن تسعى عمليات الأمان لتحقيق مستوى مقبول من التعرض للضعف والحفاظ [عليه في](../defender-endpoint/tvm-exposure-score.md) مؤسساتها.

للتحقق من تقدم تصحيح البرامج، تفضل بزيارة صفحة [](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) إدارة المخاطر والثغرات الأمنية في Defender for Endpoint، والتي يمكنك الوصول إليها من Microsoft 365 Defender عبر علامة التبويب **موارد إضافية.**

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="صفحة التهديدات والضعف في مدخل Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png"::: 
 
## <a name="4-understand-emerging-threats"></a>4. فهم التهديدات الناشئة

استخدم [تحليلات التهديدات](threat-analytics.md) في Microsoft 365 Defender الإلكتروني لإبقاء الوضع الحالي للتهديدات الأمنية مواكبا للتهديدات الحالية. ينشئ الباحثون في مجال الأمان من Microsoft الخبراء تقارير تصف التهديدات الإلكترونية الأخيرة بالتفصيل حتى تتمكن من فهم كيفية تأثيرها على Microsoft 365 الخاص بك والأجهزة والمستخدمين. يمكن أن تتضمن هذه التقارير:

- الجهات النشطة التي تواجه تهديدات وحملاتها
- تقنيات هجوم شائعة وهجمة جديدة
- نقاط الضعف الحرجة
- أسطح الهجمات الشائعة
- البرامج الضارة الشائعة

كما تبحث تحليلات التهديدات في تكوينك وتنبيهاتك لتحديد مدى المخاطر التي تواجهك وما إذا كانت هناك تنبيهات نشطة قابلة للتطبيق على تقرير.

يمكنك تنفيذ توصيات خطر ناشئ لتعزيز وضعية الأمان وتقليل منطقة سطح الهجوم.

اصنع وقتا في جدولك الزمني للتحقق [](threat-analytics.md) بشكل منتظم من قسم تحليل التهديدات Microsoft 365 Defender المدخل. راجع مثال [عمليات الأمان Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender) للحصول على مزيد من المعلومات.

## <a name="next-step"></a>الخطوة التالية

تعرف على [كيفية فرز الأحداث وتحليلها](first-incident-analyze.md).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
