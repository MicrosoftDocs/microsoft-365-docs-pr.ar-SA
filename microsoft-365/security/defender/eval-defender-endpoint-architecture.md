---
title: مراجعة متطلبات البنية Microsoft Defender لنقطة النهاية والمفاهيم الرئيسية
description: سيساعدك الرسم التخطيطي التقني Microsoft Defender لنقطة النهاية في Microsoft 365 Defender على فهم الهوية في Microsoft 365 قبل إنشاء المختبر التجريبي أو بيئة الإصدار التجريبي.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 5197acd8ceb3a2dea7c03b0ef076bca5dc9138dd
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749122"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>مراجعة متطلبات البنية Microsoft Defender لنقطة النهاية والمفاهيم الرئيسية

**ينطبق على:** Microsoft 365 Defender

ستوجهك هذه المقالة في عملية إعداد التقييم لبيئة Microsoft Defender لنقطة النهاية.

لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-endpoint-overview.md).

قبل تمكين Microsoft Defender لنقطة النهاية، تأكد من فهمك للبنية ويمكن أن تفي بالمتطلبات.

## <a name="understand-the-architecture"></a>فهم البنية

يوضح الرسم التخطيطي التالي Microsoft Defender لنقطة النهاية البنية والتكاملات. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="خطوات إضافة Microsoft Defender ل Office إلى بيئة تقييم Defender" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

يصف الجدول التالي الرسم التوضيحي.

الاتصال | الوصف
:---|:---|
1 | يتم إلحاق الأجهزة من خلال إحدى أدوات الإدارة المدعومة. 
2 | توفر الأجهزة الموجودة على متن الطائرة بيانات إشارة Microsoft Defender لنقطة النهاية وتستجيب لها.
3 | يتم ربط الأجهزة المدارة و/أو تسجيلها في Azure Active Directory.
4 | تتم مزامنة أجهزة Windows المتصلة بالمجال مع Azure Active Directory باستخدام Azure Active Directory Connect.
5 | تتم إدارة Microsoft Defender لنقطة النهاية التنبيهات والتحقيقات والاستجابات في Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>فهم المفاهيم الرئيسية

حدد الجدول التالي المفاهيم الرئيسية التي من المهم فهمها عند تقييم Microsoft Defender لنقطة النهاية وتكوينها ونشرها: 

مفهوم | الوصف | معلومات إضافية
:---|:---|:---|
مدخل الإدارة | Microsoft 365 Defender المدخل لمراقبة التنبيهات المتعلقة بنشاط التهديد المستمر المتقدم المحتمل أو انتهاكات البيانات والمساعدة في الاستجابة لها. | [نظرة عامة على مدخل Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/portal-overview)
تقليل الأجزاء المعرضة للهجوم | ساعد في تقليل أسطح الهجوم الخاصة بك عن طريق تقليل الأماكن التي تكون فيها مؤسستك عرضة للتهديدات الإلكترونية والهجمات. | [نظرة عامة على تقليل الأجزاء المعرضة للهجوم](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
الكشف عن نقطة النهاية والاستجابة لها | توفر قدرات الكشف عن نقطة النهاية والاستجابة عمليات الكشف المتقدمة عن الهجمات التي تقترب من الوقت الحقيقي وقابلة للتنفيذ. | [نظرة عامة على قدرات الكشف عن نقاط النهاية والاستجابة لها](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
الحظر السلوكي والاحتواء | يمكن أن تساعد قدرات الحظر السلوكي والاحتواء في تحديد التهديدات وإيقافها، استنادا إلى سلوكياتها ومعالجة الأشجار حتى عندما يبدأ تنفيذ التهديد. | [الحظر السلوكي والاحتواء](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
التحقيق التلقائي والاستجابة | يستخدم التحقيق التلقائي خوارزميات فحص مختلفة استنادا إلى العمليات التي يستخدمها محللو الأمان ومصممة لفحص التنبيهات واتخاذ إجراءات فورية لحل الخروقات. | [استخدام التحقيقات التلقائية للتحقيق في التهديدات ومعالجتها](/microsoft-365/security/defender-endpoint/automated-investigations)
التتبع المتقدم | التتبع المتقدم هو أداة تتبع التهديدات المستندة إلى الاستعلام تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الأولية بحيث يمكنك فحص الأحداث في شبكتك بشكل استباقي لتحديد موقع مؤشرات التهديد والكيانات. | [نظرة عامة على التتبع المتقدم](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
تحليلات التهديدات | تحليلات التهديدات هي مجموعة من التقارير من باحثين خبراء في أمان Microsoft تغطي التهديدات الأكثر صلة. | [تتبع التهديدات الناشئة والرد عليها](/microsoft-365/security/defender-endpoint/threat-analytics)


لمزيد من المعلومات التفصيلية حول القدرات المضمنة في Microsoft Defender لنقطة النهاية، راجع [ما هو Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>تكامل إدارة معلومات الأمان والأحداث

يمكنك دمج Microsoft Defender لنقطة النهاية مع Microsoft Sentinel لتحليل أحداث الأمان بشكل أكثر شمولا عبر مؤسستك وإنشاء أدلة مبادئ للاستجابة الفعالة والفورية. 

يمكن أيضا دمج Microsoft Defender لنقطة النهاية في حلول أخرى لإدارة معلومات الأمان والأحداث (SIEM). لمزيد من المعلومات، راجع [تمكين تكامل SIEM في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>الخطوات التالية
[تمكين التقييم](eval-defender-endpoint-enable-eval.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
