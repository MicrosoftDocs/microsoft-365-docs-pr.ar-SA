---
title: مراجعة متطلبات بنية نقطة النهاية والمفاهيم الأساسية ل Microsoft Defender
description: سيساعدك الرسم التخطيطي التقني ل Microsoft Defender لنقطة النهاية Microsoft 365 Defender على فهم الهوية في Microsoft 365 قبل إنشاء المعمل التجريبي أو بيئة الإصدار التجريبي.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: b1381e7c2be2224818c72fb8e269ad65ffcacfc8
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755029"
---
# <a name="review-microsoft-defender-for-endpoint-architecture-requirements-and-key-concepts"></a>مراجعة متطلبات بنية نقطة النهاية والمفاهيم الأساسية ل Microsoft Defender

**ينطبق على: Microsoft 365 Defender**

سترشدك هذه المقالة في عملية إعداد التقييم لبيئة Microsoft Defender لنقطة النهاية.

لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-endpoint-overview.md).

قبل تمكين Microsoft Defender لنقطة النهاية، تأكد من فهم البنية ويمكنها تلبية المتطلبات.

## <a name="understand-the-architecture"></a>فهم البنية

يوضح الرسم التخطيطي التالي بنية Microsoft Defender لنقطة النهاية والتكاملات. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-architecture.png" alt-text="خطوات إضافة Microsoft Defender Office إلى بيئة تقييم Defender" lightbox="../../media/defender/m365-defender-endpoint-architecture.png":::

يصف الجدول التالي الرسم التوضيحي.

الاستدعاء | الوصف
:---|:---|
1 | يتم استخدام الأجهزة على متن إحدى أدوات الإدارة المعتمدة. 
2 | توفر الأجهزة المجهزة بيانات إشارة Microsoft Defender لنقطة النهاية وتستجيب لها.
3 | يتم ضم الأجهزة المدارة و/أو تسجيلها في Azure Active Directory.
4 | يتم مزامنة Windows المنضمة إلى المجال إلى Azure Active Directory باستخدام Azure Active Directory الاتصال.
5 | يتم إدارة تنبيهات Microsoft Defender لنقطة النهاية، والتباحثات، والاستجابات في Microsoft 365 Defender.

## <a name="understand-key-concepts"></a>فهم المفاهيم الأساسية

حدد الجدول التالي المفاهيم الأساسية التي من المهم فهمها عند تقييم Microsoft Defender لنقطة النهاية وتكوينه ونشره: 

المفهوم | الوصف | معلومات إضافية
:---|:---|:---|
مدخل الإدارة | Microsoft 365 Defender المدخل لمراقبة التنبيهات المتعلقة بنشاط متقدم متقدم أو خرق للبيانات والمساعدة في الاستجابة لها. | [نظرة عامة حول مدخل نقطة النهاية ل Microsoft Defender](/microsoft-365/security/defender-endpoint/portal-overview)
تقليل مساحة الهجوم | ساعد على تقليل أسطح الهجمات عن طريق تصغير الأماكن التي تكون فيها مؤسستك عرضة للهجمات ولهجمات الإنترنت. | [نظرة عامة حول الحد من سطح الهجوم](/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
الكشف عن نقطة النهاية والاستجابة لها | توفر قدرات الكشف عن نقاط النهاية والاستجابة لها الكشف المتقدم عن الهجمات التي تقترب من الوقت الحقيقي و قابلة للتنفيذ. | [نظرة عامة الكشف عن تهديدات نقاط النهاية والرد عليها التقنية](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
الحظر السلوكي والاحتواء | يمكن أن تساعد قدرات الحظر والاحتواء السلوكية على تحديد التهديدات والتوقف عنها، استنادا إلى سلوكياتها وأشجار المعالجة حتى عندما يبدأ التهديد التنفيذ. | [الحظر السلوكي والاحتواء](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment)
إجراء التحقيق والاستجابة بشكل تلقائي | يستخدم التحقيق التلقائي خوارزميات الفحص المختلفة استنادا إلى العمليات التي يستخدمها محللو الأمان والمصممة لفحص التنبيهات واتخاذ إجراء فوري لحل الخروقات. | [استخدام الاستقصاءات التلقائية للتحقق من التهديدات و إصلاحها](/microsoft-365/security/defender-endpoint/automated-investigations)
الصيد المتقدم | الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الخام بحيث يمكنك فحص الأحداث في شبكتك بشكل استباقي لتحديد مواقع مؤشرات التهديدات والكيانات. | [نظرة عامة حول الصيد المتقدم](/microsoft-365/security/defender-endpoint/advanced-hunting-overview)
Threat Analytics | تحليلات التهديدات عبارة عن مجموعة من التقارير من الباحثين الخبراء في مجال الأمان في Microsoft تغطي التهديدات الأكثر صلة. | [تعقب التهديدات الناشئة والاستجابة لها](/microsoft-365/security/defender-endpoint/threat-analytics)


للحصول على مزيد من المعلومات المفصلة حول الإمكانات المضمنة في Microsoft Defender ل Endpoint، راجع [ما هو Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="siem-integration"></a>تكامل SIEM

يمكنك دمج Microsoft Defender ل Endpoint مع Microsoft Sentinel لتحليل أحداث الأمان عبر مؤسستك بشكل أكثر شمولية، فضلا عن إنشاء دفاتر تشغيل للاستجابة الفورية والفعالة. 

يمكن أيضا دمج Microsoft Defender ل Endpoint في حلول أخرى لإدارة أحداث ومعلومات الأمان (SIEM). لمزيد من المعلومات، راجع [تمكين تكامل SIEM في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/enable-siem-integration).


## <a name="next-steps"></a>الخطوات التالية
[تمكين التقييم](eval-defender-endpoint-enable-eval.md)

العودة إلى نظرة عامة حول [تقييم Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
