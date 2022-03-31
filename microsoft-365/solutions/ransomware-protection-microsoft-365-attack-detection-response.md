---
title: الخطوة 2. نشر الكشف عن الهجمات والاستجابة لها
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، هامور، هجوم مهين، هجوم برامج الفدية الضارة، التشفير، علم الفيروسات المشفرة، الثقة الصفرية
description: استخدم Microsoft 365 Defender ومصادر إشارات الأمان الخاصة بها لحماية مواردك Microsoft 365 من هجمات برامج الفدية الضارة.
ms.openlocfilehash: bf365693505b658dc61ab349c86541cfb9543de9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578488"
---
# <a name="step-2-deploy-attack-detection-and-response"></a>الخطوة 2. نشر الكشف عن الهجمات والاستجابة لها

كخطوة أولية مستحسنة بشدة للكشف عن هجمات برامج الفدية الضارة والاستجابة لها في Microsoft 365 المستأجر الخاص بك[](/microsoft-365/security/defender/eval-overview)، قم بإعداد بيئة تجريبية لتقييم ميزات وإمكانيات برامج الفدية الضارة Microsoft 365 Defender.

لمزيد من المعلومات، راجع هذه الموارد.

| الميزة | الوصف | مكان البدء | كيفية استخدامها للكشف والاستجابة |
|:-------|:-----|:-------|:-------|
| [Microsoft 365 Defender](/microsoft-365/security/defender) | يجمع بين الإشارات وإمكانيات التكاتف في حل واحد. <br><br> تمكن محترفي الأمان من جمع إشارات الخطر معا وتحديد النطاق الكامل للتهديد وتأثيره. <br><br> أتمتة الإجراءات لمنع الهجوم أو إيقافه والتئام علب البريد ونقاط النهاية وهويات المستخدم المتأثرة ذاتيا. | [بدء العمل](/microsoft-365/security/defender/get-started) | [استجابة للحوادث](/microsoft-365/security/defender/incidents-overview) |
| [Microsoft Defender for Identity](/defender-for-identity/what-is) |  يقوم بتحديد التهديدات المتقدمة والهويات المتهكة والإجراءات الضارة ل insider الموجهة إلى مؤسستك من خلال واجهة أمان مستندة إلى السحابة، كما يستخدم إشارات خدمات مجال Active Directory (AD DS) المحلية. | [نظرة عامة](/defender-for-identity/what-is) | [العمل مع مدخل Microsoft Defender for Identity](/defender-for-identity/workspace-portal) |
| [Microsoft Defender Office 365](/microsoft-365/security/office-365-security) | يحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. <br><br> يحمي من البرامج الضارة والتصيد الاحتيالي والخادع وأنواع الهجمات الأخرى. | [نظرة عامة](/microsoft-365/security/office-365-security/overview) | [البحث عن تهديدات](/microsoft-365/security/office-365-security/threat-hunting-in-threat-explorer) |
| [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint) | تمكين الكشف عن التهديدات المتقدمة والاستجابة لها عبر نقاط النهاية (الأجهزة). | [نظرة عامة](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)  | [الكشف عن نقطة النهاية والاستجابة لها](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) |
| [حماية هوية Azure Active Directory (Azure AD)](/azure/active-directory/identity-protection/) | أتمتة عملية الكشف عن المخاطر المستندة إلى الهوية وتحري تلك المخاطر وتوضيتها. | [نظرة عامة](/azure/active-directory/identity-protection/overview-identity-protection) | [التحقق من المخاطر](/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk) |
| [Microsoft Defender لتطبيقات السحابة](/cloud-app-security) | وسيط أمان الوصول السحابي للاكتشاف، والتحري، والحوكمة عبر جميع خدمات السحابة الخاصة بك من Microsoft و الجهة الخارجية. | [نظرة عامة](/cloud-app-security/what-is-cloud-app-security) | [التحقق](/cloud-app-security/investigate) |

>[!Note]
>تتطلب كل هذه الخدمات Microsoft 365 E5 أو Microsoft 365 E3 مع الأمان في Microsoft 365 E5 الإضافية.
>

استخدم هذه الخدمات للكشف عن التهديدات الشائعة التالية والرد عليها من قبل مهاجمي برامج الفدية الضارة:

- سرقة بيانات الاعتماد

   - حماية هوية Azure AD
   - Defender for Identity
   - Defender for Office 365

- اختراق الجهاز

   - Defender لنقطة النهاية
   - Defender for Office 365

- تصاعد الامتياز

   - حماية هوية Azure AD
   - Defender for Cloud Apps

- سلوك التطبيق الضار

   - Defender for Cloud Apps

- مسح البيانات أو حذفها أو تحميلها

   - Defender for Office 365
   - Defender for Cloud Apps [مع سياسات الكشف عن الشذوذ](/cloud-app-security/anomaly-detection-policy#ransomware-activity)

تستخدم الخدمات التالية Microsoft 365 Defender مدخلها (https://security.microsoft.com)كنقطة تجميع وتحليل مشتركة للتهديدات:

- Defender for Identity
- Defender for Office 365
- Defender لنقطة النهاية
- Defender for Cloud Apps

Microsoft 365 Defender بين إشارات الخطر في التنبيهات والتنبيهات المتصلة في حادث ما بحيث يمكن لمحللو الأمان اكتشاف مراحل هجوم برامج الفدية الضارة بسرعة أكبر، وتحري هذه المراحل، وتحل محلها.

## <a name="resulting-configuration"></a>التكوين الناتج

إليك حماية برامج الفدية الضارة للمستأجر للحصول على خطوتين 1 و2.

![الحماية من برامج الفدية الضارة Microsoft 365 المستأجر بعد الخطوة 2](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step2.png)

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 3 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step3.png)](ransomware-protection-microsoft-365-identities.md)

تابع الخطوة [3](ransomware-protection-microsoft-365-identities.md) لحماية الهويات في Microsoft 365 المستأجر.
