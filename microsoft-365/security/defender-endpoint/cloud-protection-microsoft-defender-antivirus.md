---
title: الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender
description: تعرف على الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، تقنيات الجيل التالي، الجيل التالي من av، التعلم الآلي، الحماية من البرامج الضارة، الأمان، defender، السحابة، الحماية السحابية
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 013b189dca95fc63dc8d189d020fcf3f7727cf82
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/25/2021
ms.locfileid: "63578178"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

توفر تقنيات الجيل التالي برنامج الحماية من الفيروسات من Microsoft Defender حماية فورية وأتمتة من التهديدات الجديدة والناشئة. لتحديد التهديدات الجديدة ديناميكيا، تعمل تقنيات الجيل التالي مع مجموعات كبيرة من البيانات المتداخلة في أنظمة الأمان الذكي ل Microsoft Graph والذكاء الاصطناعي القوي (AI) التي تحركها نماذج التعلم الآلي المتقدمة. تعمل الحماية السحابية مع برنامج الحماية من الفيروسات من Microsoft Defender لتقديم حماية دقيقة وفي الوقت الحقيقي وذكية. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="رسم تخطيطي يعرض كيفية عمل الحماية السحابية مع برنامج الحماية من الفيروسات من Microsoft Defender":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> نوصي بإبقاء الحماية السحابية في وضع تشغيل. لمعرفة المزيد، [راجع لماذا يجب تمكين](why-cloud-protection-should-be-on-mdav.md) الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender. 

## <a name="how-cloud-protection-works"></a>كيفية عمل الحماية السحابية

برنامج الحماية من الفيروسات من Microsoft Defender العمل بسلاسة مع خدمات Microsoft السحابية. تعمل خدمات الحماية السحابية هذه، يشار إليها أيضا باسم خدمة الحماية المتقدمة من Microsoft (MAPS)، على تحسين الحماية القياسية في الوقت الحقيقي. باستخدام الحماية السحابية، توفر تقنيات الجيل التالي تعريفا سريعا للتهديدات الجديدة، في بعض الأحيان حتى قبل إصابة نقطة نهاية واحدة. 

توضح منشورات المدونة التالية كيفية عمل الحماية السحابية:

- [تعرف على التقنيات المتقدمة في قلب Microsoft Defender لحماية الجيل التالي من نقطة النهاية](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [لماذا برنامج الحماية من الفيروسات من Microsoft Defender هو الأكثر نشرا في المؤسسة](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [مراقبة السلوك جنبا إلى جنب مع التعلم الآلي تفسد حملة ضخمة لتعدين العملات](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [كيفية توقف الذكاء الاصطناعي عن حدوث فاشية "رموز اصطناعية"](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [محاولة محاولة محاولة سيئة: برنامج الحماية من الفيروسات من Microsoft Defender التعلم الآلي الطبقي](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [برنامج الحماية من الفيروسات من Microsoft Defender حماية السحابة: الدفاع المتقدم في الوقت الحقيقي ضد البرامج الضارة التي لم يسبق أن رأيتها مطلقا](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> إن برنامج الحماية من الفيروسات من Microsoft Defender السحابة هي آلية لتقديم حماية محدثة للشبكة ونقاط النهاية. كخدمة سحابية، فهي ليست مجرد حماية للملفات المخزنة في السحابة؛ بل هي أيضا حماية للملفات المخزنة في السحابة. بدلا من ذلك، تستخدم الخدمة السحابية الموارد الموزعة والتعلم الآلي لتقديم الحماية لنقاط النهاية بمعدل أسرع بكثير من تحديثات معلومات الأمان التقليدية.

## <a name="how-to-get-cloud-protection"></a>كيفية الحصول على الحماية السحابية 

يتم تمكين الحماية السحابية بشكل افتراضي. ومع ذلك، قد تحتاج إلى إعادة تمكينه إذا تم تعطيله كجزء من سياسات المؤسسة السابقة. لمعرفة المزيد، راجع [تشغيل الحماية السحابية](enable-cloud-protection-microsoft-defender-antivirus.md).

إذا كان اشتراكك Windows 10 E5، يمكنك الاستفادة من تحديثات المعلومات الديناميكية الطارئة، التي توفر حماية في الوقت الحقيقي تقريبا من التهديدات الناشئة. عند تشغيل الحماية السحابية، يمكن تسليم تصحيحات مشاكل البرامج الضارة عبر السحابة في غضون دقائق، بدلا من انتظار التحديث التالي. راجع تكوين برنامج الحماية من الفيروسات من Microsoft Defender لتلقي تحديثات الحماية الجديدة تلقائيا استنادا إلى [التقارير من الخدمة السحابية](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates).

## <a name="next-steps"></a>الخطوات التالية

الآن لديك نظرة عامة حول الحماية السحابية في برنامج الحماية من الفيروسات من Microsoft Defender، إليك بعض الخطوات التالية:

1. راجع [لماذا يجب تمكين الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender](why-cloud-protection-should-be-on-mdav.md).

2. المتابعة لتمكين [الحماية السحابية](enable-cloud-protection-microsoft-defender-antivirus.md)