---
title: تجريبي ل Microsoft Defender for Identity
description: قم بإعداد تجريبي ل Microsoft Defender for Identity، وحدد معايير، واتخذ برامج تعليمية حول الاستطلاع، وبيانات الاعتماد التي تم اختراقها، والحركة اللاحقة، وتنبيهات السيطرة على المجال، والملء، وغيرها.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: 3801fdb4a7aeda5e75c4e36f622f7e76604d96a6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575594"
---
# <a name="pilot-microsoft-defender-for-identity"></a>تجريبي ل Microsoft Defender for Identity


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 3 من 3](eval-defender-identity-overview.md) في عملية إعداد بيئة التقييم ل Microsoft Defender for Identity. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

استخدم الخطوات التالية لإعداد التجربة وتكوينها ل Microsoft Defender للهوية. تجدر الإشارة إلى أن التوصيات لا تتضمن إعداد مجموعة تجريبية. أفضل ممارسة هي المضي قدما وتثبيت المستشعر على كل الخوادم التي تقوم بتشغيل خدمات مجال Active Directory (AD DS) والخدمات المتحدة ل Active Directory (AD FS).

![خطوات لإضافة Microsoft Defender for Identity إلى بيئة تقييم Defender.](../../media/defender/m365-defender-identity-pilot-steps.png)

يصف الجدول التالي الخطوات في الرسم التوضيحي.

- [الخطوة 1: تكوين توصيات معايير بيئة هويتك](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [الخطوة 2: تجربة الإمكانات — تعرف على البرامج التعليمية للتعرف على أنواع الهجمات المختلفة وتداركها ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>الخطوة 1. تكوين توصيات المعايير لبيئة هويتك

توفر Microsoft توصيات معايير الأمان للعملاء الذين يستخدمون خدمات Microsoft Cloud. يوفر [Azure Security Benchmark](/security/benchmark/azure/overview) (ASB) أفضل الممارسات والتوصيات الإرشادية للمساعدة في تحسين أمان أحمال العمل والبيانات والخدمات في Azure.

تتضمن توصيات المعايير هذه [أساس أمان Azure ل Microsoft Defender for Identity](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). قد يستغرق تنفيذ هذه التوصيات بعض الوقت من أجل التخطيط لها وتطبيقها. على الرغم من أن هذه ستزيد إلى حد كبير من أمان بيئة هويتك، يجب ألا تمنعك من الاستمرار في تقييم Microsoft Defender for Identity وتطبيقه. يتم توفير هذه المعلومات هنا لوعيك.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>الخطوة 2. جرب الإمكانات — تعرف على البرامج التعليمية للتعرف على أنواع الهجمات المختلفة وتداركها

تتضمن وثائق Microsoft Defender for Identity سلسلة من البرامج التعليمية التي تتعرف على مختلف أنواع الهجمات وتداركها.

جرب البرامج التعليمية ل Defender for Identity:
- [تنبيهات الاستطلاع](/defender-for-identity/reconnaissance-alerts)
- [تنبيهات بيانات الاعتماد التي تم اختراقها](/defender-for-identity/compromised-credentials-alerts)
- [تنبيهات الحركة اللاحقة](/defender-for-identity/lateral-movement-alerts)
- [تنبيهات المجال](/defender-for-identity/domain-dominance-alerts)
- [تنبيهات الملء](/defender-for-identity/exfiltration-alerts)
- [التحقق من مستخدم](/defender-for-identity/investigate-a-user)
- [التحقق من جهاز كمبيوتر](/defender-for-identity/investigate-a-computer)
- [التحقق من مسارات الحركة اللاحقة](/defender-for-identity/investigate-lateral-movement-path)
- [التحقق من الكيانات](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>الخطوات التالية

[تقييم Microsoft Defender Office 365](eval-defender-office-365-overview.md)

العودة إلى نظرة عامة حول [تقييم Microsoft Defender Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)