---
title: الخطوة 1. التخطيط لجاهزية Microsoft 365 Defender العمليات
description: أساسيات التخطيط لعمليات Microsoft 365 Defender عند Microsoft 365 Defender في عمليات الأمان.
keywords: الأحداث والتنبيهات والتحري والارتباط والهجمة والأجهزة والمستخدمين والهويات والهوية علبة البريد والبريد الإلكتروني و365 و microsoft و m365 والاستجابة للحوادث والهجمة الإلكترونية والمناظير وعمليات الأمان وcc
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
ms.openlocfilehash: 45abe5dfa77e9ed224f2d55e15986eba732f2aff
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575620"
---
# <a name="step-1-plan-for-microsoft-365-defender-operations-readiness"></a>الخطوة 1. التخطيط لجاهزية Microsoft 365 Defender العمليات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

مهما كان الاستحقاق الحالي لعمليات الأمان، فمن المهم أن تتماشى مع مركز عمليات الأمان (SOC). على الرغم من عدم وجود نموذج واحد يلائم كل مؤسسة، هناك جوانب معينة أكثر شيوعا من غيرها. 

تصف الأقسام التالية الدالات الأساسية ل SOC.

## <a name="provide-situational-awareness-of-modern-threats"></a>توفير الوعي الوضعي للتهديدات الحديثة

يعمل فريق SOC على التحضير للتهديدات الجديدة وال واردة وتعقبها حتى يمكنهم العمل مع المؤسسة لإنشاء التدابير والاستجابات. يجب أن يكون لدى فريق SOC موظفون مدربون بدرجة عالية على أساليب وتقنيات الهجمات الحديثة ويفهمون الجهات التي تواجه التهديدات. يمكن أن تعمل المعلومات وأطر العمل المشتركة [](https://www.microsoft.com/security/blog/2016/11/28/disrupting-the-kill-chain/) حول التهديدات مثل سلسلة مكافحة التهديدات عبر الإنترنت أو [MITRE ATT&CK](https://attack.mitre.org/) على تمكين فريق العمل من محللي التهديدات ومائدي التهديدات.

## <a name="provide-first-second-and-potentially-third-level-responses-to-cyber-incidents-and-events"></a>توفير استجابات من المستوى الأول والثاني ومن المحتمل أن تكون ثالثة المستوى لحوادث الإنترنت والأحداث

إن SOC هو خط الدفاع الأمامي للأحداث والحوادث الأمنية. عندما يقوم حدث أو خطر أو هجوم أو انتهاك نهج أو عملية تدقيق بتشغيل تنبيه أو استدعاء إلى إجراء، يقوم فريق SOC بعمل تقييم للفرز واحتوائه أو تصعيده من أجل التحقيق. وبالتالي، يجب أن يكون لدى المجيبين في السطر الأول من SOC معرفة تقنية واسعة النطاق بالأحداث والمؤشرات الأمنية.

## <a name="centralize-monitoring-and-logging-of-your-organizations-security-sources"></a>مركزة مراقبة مصادر الأمان في مؤسستك وتسجيلها 

عادة ما تكون الوظيفة الأساسية لفريق SOC هي التأكد من أن جميع أجهزة الأمان مثل جدران الحماية، أنظمة منع التسلل، أنظمة منع فقدان البيانات، أنظمة إدارة المخاطر والثغرات الأمنية، أنظمة الهوية تعمل بشكل صحيح، كما يتم مراقبتها. ستعمل فرق SOC مع عمليات الشبكة الأوسع مثل الهوية وD devOps والسحابة والتطبيق وعلم البيانات وفرق الأعمال الأخرى لضمان مركزية وأمان تحليل معلومات الأمان. بالإضافة إلى ذلك، فإن فريق SOC مسؤول عن الاحتفاظ بسجلات البيانات بتنسيقات قابلة للاستخدام ويمكن قراءتها، والتي قد تتضمن تحليلا وتطبيع تنسيقات مختلفة.

## <a name="establish-red-blue-and-purple-team-operational-readiness"></a>إنشاء الجهوزية التشغيلية للفريق باللون الأحمر والأزرق والأرجواني

يجب على كل فريق SOC اختبار استعداده للاستجابة لحادث عبر الإنترنت. يمكن إجراء الاختبار من خلال التمارين التدريبية، مثل تشغيل قمم الجدول والتدريب مع أفراد مختلفين في مجال المعلومات والأمان وعلى مستوى الأعمال. يتم إنشاء فرق التمارين التدريبية الفردية بالاستناد إلى أدوار تمثيلية، وهي إما تقوم بدور أحد المدافعين (فريق أزرق) أو مهاجم (فريق أحمر)، أو كمراقبين يسعون لتحسين أساليب وتقنيات كل من الفرق الزرقاء والأحمر من خلال نقاط القوة والضعف التي يتم الكشف عنها أثناء التمرين (فريق أرجواني).

## <a name="next-step"></a>الخطوة التالية

[الخطوة 2. إجراء تقييم لجاهزية تكامل SOC باستخدام "إطار الثقة الصفري"](integrate-microsoft-365-defender-secops-readiness.md)
