---
title: الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender
description: التعرف على حماية السحابة برنامج الحماية من الفيروسات من Microsoft Defender
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، الجيل التالي من التقنيات، الجيل التالي من av، التعلم الآلي، مكافحة البرامج الضارة، الأمان، Defender، السحابة، حماية السحابة
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
ms.openlocfilehash: 0cba725ed27d652366e681adccdec8dbefa68ecd
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788073"
---
# <a name="cloud-protection-and-microsoft-defender-antivirus"></a>الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

توفر تقنيات الجيل التالي في برنامج الحماية من الفيروسات من Microsoft Defender حماية تلقائية شبه فورية ضد التهديدات الجديدة والناشئة. لتحديد التهديدات الجديدة ديناميكيا، تعمل تقنيات الجيل التالي مع مجموعات كبيرة من البيانات المترابطة في Graph الأمان الذكي من Microsoft وأنظمة الذكاء الاصطناعي القوية (الذكاء الاصطناعي) مدفوعة بنماذج التعلم الآلي المتقدمة. تعمل حماية السحابة مع برنامج الحماية من الفيروسات من Microsoft Defender لتوفير حماية دقيقة وفي الوقت الحقيقي وذكية. 

[:::image type="content" source="images/mde-cloud-protection.png" alt-text="رسم تخطيطي يوضح كيفية عمل الحماية السحابية مع برنامج الحماية من الفيروسات من Microsoft Defender" lightbox="images/mde-cloud-protection.png":::](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> نوصي بالاحتفاظ بالحماية السحابية قيد التشغيل. لمعرفة المزيد، راجع [لماذا يجب تمكين حماية السحابة برنامج الحماية من الفيروسات من Microsoft Defender](why-cloud-protection-should-be-on-mdav.md). 

## <a name="how-cloud-protection-works"></a>كيفية عمل حماية السحابة

تعمل برنامج الحماية من الفيروسات من Microsoft Defender بسلاسة مع خدمات Microsoft السحابية. تعمل خدمات الحماية السحابية هذه، التي يشار إليها أيضا باسم خدمة الحماية المتقدمة من Microsoft (MAPS)، على تحسين الحماية القياسية في الوقت الحقيقي. مع حماية السحابة، توفر تقنيات الجيل التالي تعريفا سريعا للتهديدات الجديدة، حتى قبل إصابة نقطة نهاية واحدة في بعض الأحيان. 

توضح منشورات المدونة التالية كيفية عمل حماية السحابة:

- [التعرف على التقنيات المتقدمة في جوهر حماية الجيل التالي Microsoft Defender لنقطة النهاية](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/)

- [لماذا برنامج الحماية من الفيروسات من Microsoft Defender هو الأكثر توزيعا في المؤسسة](https://www.microsoft.com/security/blog/2018/03/22/why-windows-defender-antivirus-is-the-most-deployed-in-the-enterprise) 

- [مراقبة السلوك جنبا إلى جنب مع التعلم الآلي يفسد حملة ضخمة للتنقيب عن العملات المعدنية](https://www.microsoft.com/security/blog/2018/03/07/behavior-monitoring-combined-with-machine-learning-spoils-a-massive-dofoil-coin-mining-campaign)

- [كيف أوقف الذكاء الاصطناعي انتشار "Emotet"](https://www.microsoft.com/security/blog/2018/02/14/how-artificial-intelligence-stopped-an-emotet-outbreak)

- [معالجة الأرنب السيئ: دفاعات التعلم الآلي برنامج الحماية من الفيروسات من Microsoft Defender والطبقات](https://www.microsoft.com/security/blog/2017/12/11/detonating-a-bad-rabbit-windows-defender-antivirus-and-layered-machine-learning-defenses)

- [برنامج الحماية من الفيروسات من Microsoft Defender خدمة حماية السحابة: دفاع متقدم في الوقت الحقيقي ضد البرامج الضارة التي لم يسبق مشاهدتها](https://www.microsoft.com/security/blog/2017/07/18/windows-defender-antivirus-cloud-protection-service-advanced-real-time-defense-against-never-before-seen-malware) 


> [!NOTE]
> خدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender هي آلية لتقديم حماية محدثة إلى شبكتك ونقاط النهاية. كخدمة سحابية، فهي ليست مجرد حماية للملفات المخزنة في السحابة؛ بدلا من ذلك، تستخدم خدمة السحابة الموارد الموزعة والتعلم الآلي لتوفير الحماية لنقاط النهاية بمعدل أسرع بكثير من تحديثات المعلومات الذكية الأمنية التقليدية.

## <a name="how-to-get-cloud-protection"></a>كيفية الحصول على حماية السحابة 

يتم تمكين حماية السحابة بشكل افتراضي. ومع ذلك، قد تحتاج إلى إعادة تمكينه إذا تم تعطيله كجزء من نهج المؤسسة السابقة. لمعرفة المزيد، راجع [تشغيل حماية السحابة](enable-cloud-protection-microsoft-defender-antivirus.md).

إذا كان اشتراكك يتضمن Windows 10 E5، يمكنك الاستفادة من تحديثات التحليل الذكي الديناميكي في حالات الطوارئ، والتي توفر حماية شبه آنية من التهديدات الناشئة. عند تشغيل الحماية السحابية، يمكن تسليم إصلاحات مشكلات البرامج الضارة عبر السحابة في غضون دقائق، بدلا من انتظار التحديث التالي. راجع [تكوين برنامج الحماية من الفيروسات من Microsoft Defender لتلقي تحديثات الحماية الجديدة تلقائيا استنادا إلى التقارير من الخدمة السحابية.](manage-event-based-updates-microsoft-defender-antivirus.md#cloud-report-updates)

## <a name="next-steps"></a>الخطوات التالية

الآن بعد أن أصبح لديك نظرة عامة على حماية السحابة في برنامج الحماية من الفيروسات من Microsoft Defender، إليك بعض الخطوات التالية:

1. راجع [سبب تمكين الحماية السحابية برنامج الحماية من الفيروسات من Microsoft Defender](why-cloud-protection-should-be-on-mdav.md).

2. المتابعة لتمكين [حماية السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)