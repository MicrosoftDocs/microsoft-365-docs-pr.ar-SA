---
title: Microsoft Defender for Identity الإصدار التجريبي
description: Microsoft Defender for Identity التجريبية، وتعيين المعايير، وأخذ البرامج التعليمية حول الاستطلاع، وبيانات الاعتماد المخترقة، والحركة الجانبية، وإهمال المجال، وتنبيهات النقل غير المصرح به، من بين أمور أخرى.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4805c97d79d36879a7b5081c347bd81c655c58c4
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747890"
---
# <a name="pilot-microsoft-defender-for-identity"></a>Microsoft Defender for Identity الإصدار التجريبي


**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 3 من 3](eval-defender-identity-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Identity. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

استخدم الخطوات التالية لإعداد وتكوين الإصدار التجريبي ل Microsoft Defender للهوية. لاحظ أن التوصيات لا تتضمن إعداد مجموعة تجريبية. أفضل الممارسات هي المضي قدما وتثبيت جهاز الاستشعار على جميع خوادمك التي تعمل خدمات مجال Active Directory (AD DS) وخدمات Active Directory المتحدة (AD FS).

:::image type="content" source="../../media/defender/m365-defender-identity-pilot-steps.png" alt-text="خطوات تجربة Microsoft Defender for Identity في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-identity-pilot-steps.png":::

يصف الجدول التالي الخطوات الواردة في الرسم التوضيحي.

- [الخطوة 1: تكوين توصيات المعيار لبيئة هويتك](#step-1-configure-benchmark-recommendations-for-your-identity-environment)
- [الخطوة 2: تجربة القدرات - الاطلاع على البرامج التعليمية لتحديد ومعالجة أنواع الهجمات المختلفة ](#step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types)

## <a name="step-1-configure-benchmark-recommendations-for-your-identity-environment"></a>الخطوة 1. تكوين توصيات المعيار لبيئة هويتك

توفر Microsoft توصيات معيار الأمان للعملاء الذين يستخدمون خدمات Microsoft Cloud. يوفر [معيار أمان Azure](/security/benchmark/azure/overview) (ASB) أفضل الممارسات والتوصيات الإرشادية للمساعدة في تحسين أمان أحمال العمل والبيانات والخدمات على Azure.

تتضمن توصيات المعيار هذه [أساس أمان Azure Microsoft Defender for Identity](/security/benchmark/azure/baselines/defender-for-identity-security-baseline). قد يستغرق تنفيذ هذه التوصيات بعض الوقت للتخطيط والتنفيذ. في حين أن هذه سوف تزيد إلى حد كبير من أمان بيئة الهوية الخاصة بك، فإنها لا ينبغي أن تمنعك من الاستمرار في تقييم وتنفيذ Microsoft Defender for Identity. يتم توفير هذه هنا لوعيك.

## <a name="step-2-try-out-capabilities--walk-through-tutorials-for-identifying-and-remediating-different-attack-types"></a>الخطوة 2. جرب القدرات — اطلع على البرامج التعليمية لتحديد أنواع الهجمات المختلفة ومعالجتها

تتضمن وثائق Microsoft Defender for Identity سلسلة من البرامج التعليمية التي تستعرض عملية تحديد ومعالجة أنواع الهجمات المختلفة.

جرب البرامج التعليمية ل Defender for Identity:
- [تنبيهات الاستطلاع](/defender-for-identity/reconnaissance-alerts)
- [تنبيهات بيانات الاعتماد المخترقة](/defender-for-identity/compromised-credentials-alerts)
- [تنبيهات الحركة الجانبية](/defender-for-identity/lateral-movement-alerts)
- [تنبيهات إهمال المجال](/defender-for-identity/domain-dominance-alerts)
- [تنبيهات النقل غير المصرح به](/defender-for-identity/exfiltration-alerts)
- [التحقيق مع مستخدم](/defender-for-identity/investigate-a-user)
- [التحقيق في جهاز كمبيوتر](/defender-for-identity/investigate-a-computer)
- [التحقيق في مسارات الحركة الجانبية](/defender-for-identity/investigate-lateral-movement-path)
- [التحقيق في الكيانات](/defender-for-identity/investigate-entity)

## <a name="next-steps"></a>الخطوات التالية

[تقييم Microsoft Defender لـ Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender لـ Office 365](eval-defender-office-365-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)