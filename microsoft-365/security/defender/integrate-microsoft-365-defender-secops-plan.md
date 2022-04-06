---
title: الخطوة 1. التخطيط لجاهزية عمليات Microsoft 365 Defender
description: أساسيات التخطيط لجاهزية العمليات Microsoft 365 Defender عند دمج Microsoft 365 Defender في عمليات الأمان الخاصة بك.
keywords: الحوادث، والتنبيهات، والتحقيق، والارتباط، والهجمات، والأجهزة، والمستخدمين، والهويات، والهوية، وعلبة البريد، والبريد الإلكتروني، و365، وmicrosoft، وm365، والاستجابة للحوادث، والهجمات الإلكترونية، وال secops، وعمليات الأمان، وsoc
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
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 8c69e92390e6ed6515be6f399703124ece99cc39
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664007"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>الخطوة 1. التخطيط لجاهزية عمليات Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

مهما كان النضج الحالي لعمليات الأمان الخاصة بك، فمن المهم أن تتماشى مع مركز عمليات الأمان (SOC). على الرغم من عدم وجود نموذج واحد يناسب كل مؤسسة، هناك جوانب معينة أكثر شيوعا من غيرها.

تصف الأقسام التالية الوظائف الأساسية ل SOC.

## <a name="provide-situational-awareness-of-modern-threats"></a>توفير الوعي الموقفي بالتهديدات الحديثة

يستعد فريق SOC للتهديدات الجديدة والواردة ويتتبعها حتى يتمكنوا من العمل مع المؤسسة لوضع التدابير والاستجابات المعاكسة. يجب أن يكون لدى فريق SOC الخاص بك موظفين مدربون تدريبا عاليا على أساليب وتقنيات الهجوم الحديثة وفهم الجهات الفاعلة في التهديد. يمكن للذكاء الذكي المشترك للمخاطر وأطر العمل مثل [سلسلة القتل السيبراني](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) أو [إطار عمل MITRE ATT&CK](https://attack.mitre.org/) تمكين موظفيك من محللي التهديدات ومتتبعي التهديدات.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>توفير استجابات من المستوى الأول والثاني وربما الثالث للحوادث والأحداث الإلكترونية

SOC هو خط الدفاع الأمامي للأحداث والحوادث الأمنية. عندما يؤدي حدث أو تهديد أو هجوم أو انتهاك للنهج أو العثور على تدقيق إلى تشغيل تنبيه أو استدعاء لاتخاذ إجراء، يقوم فريق SOC بإجراء تقييم لفرزه واحتواءه أو تصعيده للتحقيق فيه. لذلك، يجب أن يكون لدى مستجيبي الخط الأول SOC معرفة تقنية واسعة بالأحداث والمؤشرات الأمنية.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>مركزية مراقبة مصادر الأمان الخاصة بمؤسستك وتسجيلها

عادة ما تكون الوظيفة الأساسية لفريق SOC هي التأكد من أن جميع أجهزة الأمان مثل جدران الحماية وأنظمة منع الاختراق وأنظمة منع فقدان البيانات وأنظمة إدارة المخاطر والثغرات الأمنية وأنظمة الهوية تعمل بشكل صحيح وتتم مراقبتها. ستعمل فرق SOC مع عمليات الشبكة الأوسع مثل الهوية وDevOps والسحابة والتطبيق وعلوم البيانات وفرق الأعمال الأخرى لضمان مركزية تحليل معلومات الأمان وتأمينها. بالإضافة إلى ذلك، يكون فريق SOC مسؤولا عن الاحتفاظ بسجلات البيانات بتنسيقات قابلة للاستخدام وقابلة للقراءة، والتي يمكن أن تتضمن تحليل التنسيقات المتباينة وتطبيعها.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>إنشاء الاستعداد التشغيلي للفريق الأحمر والأزرق والأرجواني

يجب على كل فريق SOC اختبار استعداده للاستجابة لحادث إلكتروني. يمكن إجراء الاختبار من خلال تمارين التدريب، مثل الجداول والممارسات التي يتم تشغيلها مع مختلف الأفراد في تكنولوجيا المعلومات والأمان وعلى مستوى الأعمال. يتم إنشاء فرق تمرين تدريب فردية استنادا إلى أدوار تمثيلية، وهي تلعب دور أحد المهاجمين (الفريق الأزرق) أو المهاجم (الفريق الأحمر) أو كمراقبين يسعون إلى تحسين أساليب وتقنيات كل من الفرق الزرقاء والأحمرة من خلال نقاط القوة والضعف التي يتم الكشف عنها أثناء التمرين (الفريق الأرجواني).

## <a name="next-step"></a>الخطوة التالية

[الخطوة 2. إجراء تقييم جاهزية تكامل SOC باستخدام ثقة معدومة Framework](integrate-microsoft-365-defender-secops-readiness.md)
